    // MOTOR GENERADOR CONFIGURADO PARA DEEPSEEK API
    async function generateSessionsWithAI() {
      const apiKey = localStorage.getItem(STORAGE_KEYS.GEMINI_KEY);
      if (!apiKey) return alert("⚠️ Configura primero tu API Key de DeepSeek en el Panel Maestro.");

      const btn = document.getElementById("btnGenerateAI");
      const output = document.getElementById("planOutputContainer");
      const modeloKey = document.getElementById("selModelo").value;
      const meta = {
        docente: document.getElementById("inpDocente").value,
        escuela: document.getElementById("inpEscuela").value,
        cct: document.getElementById("inpCCT").value,
        grupo: document.getElementById("inpGrupo").value,
        director: document.getElementById("inpDirector").value,
        modalidad: document.getElementById("selModalidad").value,
        entorno: document.getElementById("selEntornoSesion").options[document.getElementById("selEntornoSesionselectedIndex") || 0].text,
        fase: document.getElementById("selFase").options[document.getElementById("selFase").selectedIndex].text,
        contenido: document.getElementById("selContenido").options[document.getElementById("selContenido").selectedIndex].text,
        pda: document.getElementById("pdaDisplayBox").textContent,
        modeloBase: METHODOLOGY_CASCADE[modeloKey].nombre,
        modeloSec: document.getElementById("selModeloSecundario").value,
        dominioCAI: document.getElementById("selDominioCAI").value,
        conflicto: document.getElementById("selConflicto").value,
        eje: document.getElementById("selEje").value,
        instrumento: document.getElementById("selInstrumento").value,
        problematica: document.getElementById("inpProblematica").value
      };
      const dates = computeSchoolDates(selectedPackageSessions);

      btn.disabled = true;
      btn.textContent = `⏳ DISEÑANDO ${selectedPackageSessions} SESIONES CON DEEPSEEK...`;
      output.innerHTML = `<div class="card-box p-6 text-center font-bold text-sm">Construyendo ${selectedPackageSessions} sesiones bajo ${meta.modeloBase} con DeepSeek...</div>`;

      const systemPrompt = "Eres un Doctor en Cultura Física, experto en Praxiología Motriz (Parlebas/Lavega) y NEM 2026-2027. Devuelve EXCLUSIVAMENTE un arreglo JSON válido, sin texto adicional ni bloques markdown.";
      
      const userPrompt = `Diseña exactamente ${selectedPackageSessions} sesiones de Educación Física TOTALMENTE DIFERENTES Y PROGRESIVAS (PROHIBIDO repetir juegos entre sesiones).
Parámetros fijos:
- Estructura: ${meta.modalidad} | Entorno: ${meta.entorno}
- Nivel: ${meta.fase} (${meta.grupo}) | Contenido: ${meta.contenido}
- PDA: ${meta.pda}
- Metodología: ${meta.modeloBase} ${meta.modeloSec}
- Dominio [CAI]: ${meta.dominioCAI} | Conflicto: ${meta.conflicto}
- Contexto: ${meta.problematica}

Estructura estricta del JSON requerido (debe ser un arreglo con ${selectedPackageSessions} objetos):
[
  {
    "numero": 1,
    "titulo_tactico": "...",
    "inicial": "Juego inédito + reglas y biomecánica (mín 50 palabras)",
    "medular": "Situación motriz + lógica interna detallada (espacio, tiempo, móvil, roles, subroles y variante táctica, mín 90 palabras)",
    "cierre": "Vuelta a la calma + pregunta mayéutica (mín 40 palabras)",
    "adecuacion_bap": "Ajuste DUA",
    "indicador_evaluacion": "Indicador observable"
  }
];`;

      try {
        const res = await fetch("https://api.deepseek.com/chat/completions", {
          method: "POST",
          headers: {
            "Content-Type": "application/json",
            "Authorization": `Bearer ${apiKey}`
          },
          body: JSON.stringify({
            model: "deepseek-chat",
            messages: [
              { role: "system", content: systemPrompt },
              { role: "user", content: userPrompt }
            ],
            response_format: { type: "json_object" },
            temperature: 0.78
          })
        });

        const data = await res.json();
        const raw = data?.choices?.[0]?.message?.content;
        if (!raw) throw new Error("No se obtuvo respuesta de DeepSeek.");
        
        // Limpieza de JSON por si el modelo incluye marcas de texto
        let cleanJson = raw.trim();
        if (cleanJson.startsWith("```json")) cleanJson = cleanJson.replace(/^```json/, "").replace(/```$/, "").trim();
        else if (cleanJson.startsWith("```")) cleanJson = cleanJson.replace(/^```/, "").replace(/```$/, "").trim();

        const parsed = JSON.parse(cleanJson);
        // Soporta tanto si devuelve un objeto contenedor como un arreglo directo
        currentGeneratedSessions = Array.isArray(parsed) ? parsed : (parsed.sesiones || parsed.sessions || Object.values(parsed)[0]);
        
        renderSessionsHTML(currentGeneratedSessions, dates, meta);
      } catch (e) {
        output.innerHTML = `<div class="card-box p-4 bg-rose-50 text-rose-900 text-xs font-bold">❌ Error DeepSeek API: ${e.message}</div>`;
      } finally {
        btn.disabled = false;
        btn.textContent = `⚡ 1. DISEÑAR SESIONES IRREPETIBLES CON API`;
      }
    }