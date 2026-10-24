<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>PRAXIS MAGISTER • PRO v17.0 | Ingeniería Didáctica y Bitácoras SEP</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;600;700;800&family=Outfit:wght@700;800;900&display=swap" rel="stylesheet">
  <style>
    body { font-family: 'Plus Jakarta Sans', sans-serif; background: linear-gradient(135deg,#e0f2fe 0%,#ede9fe 50%,#d1fae5 100%); color:#0f172a; min-height:100vh; }
    .font-display { font-family: 'Outfit', sans-serif; }
    .hero-gradient { background: linear-gradient(125deg,#0f172a 0%,#1e1b4b 38%,#065f46 78%,#0284c7 100%); }
    .card-box { background:#fff; border-radius:1.25rem; box-shadow:0 15px 35px -12px rgba(15,23,42,0.14); border:2px solid #cbd5e1; }
    .btn-gen { background: linear-gradient(135deg,#059669 0%,#0284c7 50%,#4f46e5 100%); }
    .print-sheet { background:#fff; border:2px solid #cbd5e1; border-radius:1rem; padding:1.25rem; margin-bottom:1.25rem; page-break-inside:avoid; }
    @media print {
      @page { size: letter portrait; margin: 10mm 12mm; }
      body { background:#fff !important; font-size:9pt; }
      .no-print { display:none !important; }
      .print-sheet { box-shadow:none !important; border:1.5px solid #334155 !important; margin-bottom:8mm !important; break-inside:avoid; }
    }
  </style>
</head>
<body class="antialiased">

  <!-- ENCABEZADO -->
  <header class="hero-gradient text-white sticky top-0 z-40 shadow-xl border-b border-white/15 no-print">
    <div class="max-w-7xl mx-auto px-4 py-3 flex flex-wrap items-center justify-between gap-2">
      <div class="flex items-center gap-3">
        <button id="secretTriggerBtn" onclick="handleSecretCreatorClick()"
          class="w-11 h-11 rounded-2xl bg-gradient-to-br from-emerald-400 via-cyan-500 to-indigo-600 flex items-center justify-center font-display font-black text-lg text-white shadow-lg select-none">
          PM
        </button>
        <div>
          <div class="flex items-center flex-wrap gap-1.5">
            <span class="font-display font-extrabold text-base md:text-lg">PRAXIS MAGISTER • PRO v17.0</span>
            <span class="text-[10px] font-bold uppercase px-2 py-0.5 rounded-full bg-emerald-400/20 text-emerald-300 border border-emerald-400/40">SEP • NEM 2026-2027</span>
            <span id="vipBadgeStatus" class="text-[10px] font-bold uppercase px-2 py-0.5 rounded-full bg-amber-400/20 text-amber-200 border border-amber-400/40">CRÉDITOS PDF: 0</span>
          </div>
          <p class="text-[11px] text-slate-300">Planeación por API + Bitácoras SEP con Redacción Jurídico-Normativa Asistida</p>
        </div>
      </div>

      <nav class="flex flex-wrap items-center gap-1.5">
        <button onclick="switchMainTab('planner')" id="tabBtn-planner" class="px-3 py-1.5 rounded-xl text-xs font-bold bg-gradient-to-r from-emerald-500 to-cyan-500 text-white">1. Consola Planeación</button>
        <button onclick="switchMainTab('bitacoras')" id="tabBtn-bitacoras" class="px-3 py-1.5 rounded-xl text-xs font-bold bg-white/10 text-slate-200">2. Las 2 Bitácoras SEP</button>
        <button onclick="switchMainTab('board')" id="tabBtn-board" class="px-3 py-1.5 rounded-xl text-xs font-bold bg-white/10 text-slate-200">3. Pizarra Táctica</button>
        <button onclick="switchMainTab('clinic')" id="tabBtn-clinic" class="px-3 py-1.5 rounded-xl text-xs font-bold bg-white/10 text-slate-200">4. Clínica de Patio</button>
        <button onclick="openUnlockModal()" class="px-3 py-1.5 rounded-xl text-xs font-extrabold bg-amber-400 text-slate-950">🔑 Canjear Código</button>
        <button id="creatorTopBtn" onclick="openMasterCreatorModal()" class="hidden px-3 py-1.5 rounded-xl text-xs font-extrabold bg-fuchsia-500 text-white">⚙️ Panel Maestro</button>
      </nav>
    </div>
  </header>

  <main class="max-w-7xl mx-auto px-3 py-5">
    <!-- MÓDULO 1: CONSOLA DE PLANEACIÓN -->
    <section id="view-planner" class="space-y-6">
      <div class="card-box p-4 md:p-6 no-print">
        <div class="flex flex-wrap items-center justify-between gap-3 pb-4 mb-5 border-b border-slate-200">
          <div>
            <h1 class="font-display font-black text-xl md:text-2xl text-slate-900">Consola de Ingeniería Didáctica y Praxiológica NEM</h1>
            <p class="text-xs text-slate-600">Cascada metodológica sincronizada con el calendario escolar oficial SEP 2026-2027.</p>
          </div>
          <div class="flex flex-wrap gap-1.5 bg-slate-100 p-1.5 rounded-2xl border border-slate-200">
            <button onclick="selectSessionPackage(8)" id="pkgBtn-8" class="px-3.5 py-2 rounded-xl text-xs font-extrabold bg-gradient-to-r from-indigo-600 to-cyan-600 text-white shadow">8 Sesiones • $100</button>
            <button onclick="selectSessionPackage(20)" id="pkgBtn-20" class="px-3.5 py-2 rounded-xl text-xs font-extrabold bg-white text-slate-700">20 Sesiones • $200</button>
            <button onclick="selectSessionPackage(40)" id="pkgBtn-40" class="px-3.5 py-2 rounded-xl text-xs font-extrabold bg-white text-slate-700">40 Sesiones • $300</button>
          </div>
        </div>

        <div class="grid grid-cols-1 lg:grid-cols-12 gap-5">
          <!-- COLUMNA A -->
          <div class="lg:col-span-4 space-y-4">
            <div class="rounded-2xl p-4 bg-sky-50/70 border-2 border-sky-200 space-y-2.5 text-xs">
              <h2 class="font-display font-extrabold text-xs uppercase text-sky-900">A1. Datos Institucionales Oficiales</h2>
              <div class="grid grid-cols-1 sm:grid-cols-2 gap-2.5">
                <div><label class="font-bold block mb-1">Docente de E.F.</label><input id="inpDocente" type="text" value="Prof. Educación Física" class="w-full rounded-xl border border-sky-300 bg-white px-2.5 py-1.5 font-semibold" /></div>
                <div><label class="font-bold block mb-1">Escuela / Plantel</label><input id="inpEscuela" type="text" value="Escuela Primaria Oficial" class="w-full rounded-xl border border-sky-300 bg-white px-2.5 py-1.5 font-semibold" /></div>
                <div><label class="font-bold block mb-1">CCT y Zona</label><input id="inpCCT" type="text" value="CCT: 09DPR0000X • Zona 04" class="w-full rounded-xl border border-sky-300 bg-white px-2.5 py-1.5 font-semibold" /></div>
                <div><label class="font-bold block mb-1">Grado y Grupo</label><input id="inpGrupo" type="text" value="5° y 6° • Grupo A" class="w-full rounded-xl border border-sky-300 bg-white px-2.5 py-1.5 font-semibold" /></div>
                <div class="sm:col-span-2"><label class="font-bold block mb-1">Autoridad / Dirección (Firma)</label><input id="inpDirector" type="text" value="Vo. Bo. Dirección del Plantel" class="w-full rounded-xl border border-sky-300 bg-white px-2.5 py-1.5 font-semibold" /></div>
              </div>
            </div>

            <div class="rounded-2xl p-4 bg-emerald-50/70 border-2 border-emerald-200 space-y-2.5 text-xs">
              <h2 class="font-display font-extrabold text-xs uppercase text-emerald-900">A2. Calendario SEP 2026-2027</h2>
              <div><label class="font-bold block mb-1">Inicio de Secuencia (Sesión 1)</label><input id="inpStartDate" type="date" value="2026-10-26" onchange="updateCalendarPreview()" class="w-full rounded-xl border border-emerald-300 bg-white px-2.5 py-1.5 font-bold" /></div>
              <div class="flex flex-wrap gap-1.5">
                <label class="flex items-center gap-1 bg-white px-2 py-1 rounded-lg border border-emerald-300 font-bold"><input type="checkbox" class="day-check" value="1" checked onchange="updateCalendarPreview()"> Lun</label>
                <label class="flex items-center gap-1 bg-white px-2 py-1 rounded-lg border border-emerald-300 font-bold"><input type="checkbox" class="day-check" value="2" onchange="updateCalendarPreview()"> Mar</label>
                <label class="flex items-center gap-1 bg-white px-2 py-1 rounded-lg border border-emerald-300 font-bold"><input type="checkbox" class="day-check" value="3" checked onchange="updateCalendarPreview()"> Mié</label>
                <label class="flex items-center gap-1 bg-white px-2 py-1 rounded-lg border border-emerald-300 font-bold"><input type="checkbox" class="day-check" value="4" onchange="updateCalendarPreview()"> Jue</label>
                <label class="flex items-center gap-1 bg-white px-2 py-1 rounded-lg border border-emerald-300 font-bold"><input type="checkbox" class="day-check" value="5" onchange="updateCalendarPreview()"> Vie</label>
              </div>
              <div id="calendarRangePreview" class="p-2 rounded-lg bg-emerald-900/10 text-emerald-950 font-extrabold text-[11px]"></div>
            </div>
          </div>

          <!-- COLUMNA B: METODOLOGÍA EN CASCADA -->
          <div class="lg:col-span-4 space-y-3">
            <div class="rounded-2xl p-4 bg-violet-50/70 border-2 border-violet-200 space-y-2.5 text-xs">
              <h2 class="font-display font-extrabold text-xs uppercase text-violet-900">B. Cascada Metodológica Invariable</h2>
              <div class="p-2 rounded-xl bg-amber-100 border border-amber-400">
                <label class="font-extrabold text-amber-950 block mb-1">🎖️ Entorno / Modalidad:</label>
                <select id="selEntornoSesion" onchange="onMethodologyCascadeChange()" class="w-full rounded-lg border border-amber-500 bg-white px-2 py-1.5 font-extrabold text-amber-950">
                  <option value="PATIO">1. Patio Escolar (100% Motriz y Praxiológico)</option>
                  <option value="ESCOLTA">🎖️ Especial Escolta Cívica y Concurso Oficial</option>
                  <option value="AULA_VS">2. Aula Vida Saludable y Corporeidad</option>
                </select>
              </div>
              <div class="grid grid-cols-2 gap-2">
                <div>
                  <label class="font-bold block mb-1">Estructura</label>
                  <select id="selModalidad" class="w-full rounded-xl border border-violet-300 bg-white px-2 py-1.5 font-bold">
                    <option value="Unidad Didáctica">Unidad Didáctica</option>
                    <option value="Aprendizaje Servicio">Aprendizaje Servicio</option>
                    <option value="Deporte Educativo">Deporte Educativo</option>
                  </select>
                </div>
                <div>
                  <label class="font-bold block mb-1">Fase y Grado NEM</label>
                  <select id="selFase" onchange="updateStaticCurriculum()" class="w-full rounded-xl border border-violet-300 bg-white px-2 py-1.5 font-bold">
                    <option value="f3_1">Fase 3 • 1° Primaria</option>
                    <option value="f3_2">Fase 3 • 2° Primaria</option>
                    <option value="f4_3">Fase 4 • 3° Primaria</option>
                    <option value="f4_4">Fase 4 • 4° Primaria</option>
                    <option value="f5_5">Fase 5 • 5° Primaria</option>
                    <option value="f5_6" selected>Fase 5 • 6° Primaria</option>
                    <option value="f6_1">Fase 6 • 1° Secundaria</option>
                  </select>
                </div>
              </div>
              <div>
                <label class="font-bold block mb-1">Contenido Sintético NEM</label>
                <select id="selContenido" onchange="updateStaticCurriculum()" class="w-full rounded-xl border border-violet-300 bg-white px-2.5 py-1.5 font-bold">
                  <option value="0">1. Capacidades, habilidades y destrezas motrices</option>
                  <option value="1">2. Posibilidades cognitivas, expresivas y motrices</option>
                  <option value="2">3. Estilos de vida activos y saludables</option>
                  <option value="3">4. Pensamiento lúdico y estratégico</option>
                </select>
              </div>
              <div class="p-2.5 rounded-xl bg-white border-2 border-violet-300">
                <span class="text-[10px] font-extrabold uppercase text-violet-700 block">PDA OFICIAL VINCULADO:</span>
                <p id="pdaDisplayBox" class="text-[11px] font-semibold text-slate-800 italic mt-0.5"></p>
              </div>
              <div class="grid grid-cols-2 gap-2">
                <div>
                  <label class="font-bold text-indigo-950 block mb-1">1° Modelo Base</label>
                  <select id="selModelo" onchange="onMethodologyCascadeChange()" class="w-full rounded-xl border-2 border-violet-400 bg-white px-2 py-1.5 font-bold text-indigo-950">
                    <option value="PRAX">Praxiología Motriz (Parlebas)</option>
                    <option value="TGFU">TGfU • Táctica (Bunker/Thorpe)</option>
                    <option value="MRPS">MRPS • Ética (Hellison)</option>
                    <option value="COOP">Cooperativo (Velázquez)</option>
                  </select>
                </div>
                <div>
                  <label class="font-bold text-fuchsia-950 block mb-1">2° Modelo Hibridación</label>
                  <select id="selModeloSecundario" class="w-full rounded-xl border-2 border-fuchsia-400 bg-fuchsia-50 px-2 py-1.5 font-bold text-fuchsia-950">
                    <option value="+ MRPS (Responsabilidad Social)">+ MRPS (Social)</option>
                    <option value="+ Aprendizaje Cooperativo">+ Cooperativo</option>
                    <option value="Modelo Puro">Modelo Puro (Sin hibridar)</option>
                  </select>
                </div>
              </div>
              <div>
                <label class="font-bold block mb-1">Dominio de Acción [CAI]</label>
                <select id="selDominioCAI" class="w-full rounded-xl border border-violet-300 bg-white px-2 py-1.5 font-bold text-slate-800"></select>
              </div>
              <div>
                <label class="font-bold block mb-1">Conflicto Táctico / Lógica Interna</label>
                <select id="selConflicto" class="w-full rounded-xl border border-violet-300 bg-white px-2.5 py-1.5 font-bold text-slate-800"></select>
              </div>
            </div>
          </div>

          <!-- COLUMNA C -->
          <div class="lg:col-span-4 flex flex-col justify-between space-y-4">
            <div class="rounded-2xl p-4 bg-amber-50/70 border-2 border-amber-300 space-y-2.5 text-xs">
              <h2 class="font-display font-extrabold text-xs uppercase text-amber-950">C. Contexto, Evaluación y PDF</h2>
              <div class="grid grid-cols-2 gap-2">
                <div>
                  <label class="font-bold block mb-1">Ejes Articuladores</label>
                  <select id="selEje" class="w-full rounded-xl border border-amber-300 bg-white px-2 py-1.5 font-bold">
                    <option value="Vida Saludable + Inclusión">Vida Saludable + Inclusión</option>
                    <option value="Pensamiento Crítico + Igualdad">Pensamiento Crítico + Igualdad</option>
                  </select>
                </div>
                <div>
                  <label class="font-bold block mb-1">Instrumento</label>
                  <select id="selInstrumento" class="w-full rounded-xl border border-amber-300 bg-white px-2 py-1.5 font-bold">
                    <option value="Rúbrica Praxiológica">Rúbrica Praxiológica</option>
                    <option value="Lista de Cotejo Táctico-Postural">Lista de Cotejo</option>
                  </select>
                </div>
              </div>
              <div>
                <label class="font-bold block mb-1">Diagnóstico del Grupo y Materiales</label>
                <textarea id="inpProblematica" rows="3" class="w-full rounded-xl border border-amber-300 bg-white p-2 font-medium text-slate-800">Grupo de 30 alumnos en patio escolar; conos, aros, paliacates y pelotas de vinil. Alta densidad motora sin filas de espera e inclusión DUA.</textarea>
              </div>
              <div class="p-3 rounded-xl bg-slate-900 text-white space-y-1">
                <div class="flex items-center justify-between">
                  <span class="text-[11px] font-bold text-cyan-300">Vigencia de Código VIP:</span>
                  <span id="licenseStatusText" class="text-xs font-extrabold text-amber-400">SIN CRÉDITOS PDF</span>
                </div>
                <p class="text-[10px] text-slate-300">La exportación en PDF consume <strong>1 crédito</strong> de tu licencia activa (aplica para Planeación y Bitácoras).</p>
              </div>
            </div>

            <div class="space-y-2">
              <button id="btnGenerateAI" onclick="generateSessionsWithAI()" class="w-full py-3 px-4 rounded-2xl font-display font-black text-xs md:text-sm text-white btn-gen shadow-lg">
                ⚡ 1. DISEÑAR SESIONES IRREPETIBLES CON API
              </button>
              <button id="btnDownloadPDF" onclick="consumeCreditAndPrintPDF()" class="w-full py-3 px-4 rounded-2xl font-display font-black text-xs md:text-sm bg-slate-900 text-amber-300 border-2 border-amber-400 shadow-lg">
                🖨️ 2. EXPORTAR EXPEDIENTE PDF (-1 CRÉDITO)
              </button>
            </div>
          </div>
        </div>
      </div>

      <div id="planOutputContainer" class="space-y-5"></div>
    </section>

    <!-- MÓDULO 2: LAS 2 BITÁCORAS SEP (PROTEGIDAS POR CÓDIGO VIP) -->
    <section id="view-bitacoras" class="hidden space-y-4">
      <div class="card-box p-5 space-y-3 text-xs">
        <div class="flex flex-wrap justify-between items-center gap-3 border-b pb-3">
          <div>
            <span class="px-2.5 py-1 rounded-full text-[10px] font-extrabold uppercase bg-emerald-100 text-emerald-800">Módulo Normativo Oficial AEFCM / DGOSE</span>
            <h2 class="font-display font-black text-lg text-slate-900 mt-1">Generador de las 2 Bitácoras SEP con Redacción Jurídica Asistida</h2>
            <p class="text-slate-600">Escribe tus notas informales; la plataforma procesa automáticamente la redacción técnica, legal y normativa requerida.</p>
          </div>
          <button onclick="consumeCreditAndPrintBitacoras()" class="px-4 py-2 rounded-xl bg-slate-900 text-amber-300 font-display font-black text-xs border border-amber-400">
            🖨️ Imprimir / Exportar Bitácoras PDF (-1 Crédito)
          </button>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
          <!-- Entrada Bitácora 1 -->
          <div class="p-4 rounded-xl bg-sky-50/70 border-2 border-sky-200 space-y-2">
            <h3 class="font-extrabold text-sky-950 uppercase">Formato 1: Notas sobre Espacios, Horarios y Cobertura</h3>
            <div>
              <label class="font-bold block mb-1">Fecha del Registro</label>
              <input id="b1Fecha" type="date" value="2026-10-26" onchange="renderBitacorasSEP()" class="w-full rounded-lg border px-3 py-1.5 font-bold bg-white" />
            </div>
            <div>
              <label class="font-bold block mb-1">Redacción informal de la situación en cancha o espacios:</label>
              <textarea id="b1Raw" rows="3" oninput="renderBitacorasSEP()" class="w-full rounded-lg border p-2 bg-white" placeholder="Ej. Nos quitaron la mitad de la cancha para junta y tuve que adaptar a los 30 niños en un espacio reducido..."></textarea>
            </div>
          </div>

          <!-- Entrada Bitácora 2 -->
          <div class="p-4 rounded-xl bg-amber-50/70 border-2 border-amber-200 space-y-2">
            <h3 class="font-extrabold text-amber-950 uppercase">Formato 2: Notas sobre Incidencias y Convivencia</h3>
            <div>
              <label class="font-bold block mb-1">Fecha del Registro</label>
              <input id="b2Fecha" type="date" value="2026-10-26" onchange="renderBitacorasSEP()" class="w-full rounded-lg border px-3 py-1.5 font-bold bg-white" />
            </div>
            <div>
              <label class="font-bold block mb-1">Redacción informal del incidente o conflicto:</label>
              <textarea id="b2Raw" rows="3" oninput="renderBitacorasSEP()" class="w-full rounded-lg border p-2 bg-white" placeholder="Ej. Dos niños discutieron fuerte por el balón en el partido, se empujaron pero los calmé y aplicamos diálogo restaurativo..."></textarea>
            </div>
          </div>
        </div>
      </div>

      <div id="bitacorasOutput" class="space-y-4"></div>
    </section>

    <!-- MÓDULO 3: PIZARRA TÁCTICA -->
    <section id="view-board" class="hidden">
      <div class="card-box p-5 text-xs space-y-3">
        <h2 class="font-display font-black text-lg">Pizarra Táctica de Espacios Sociomotrices [CAI] y Escolta Cívica</h2>
        <div class="grid grid-cols-1 md:grid-cols-3 gap-3">
          <div class="p-4 rounded-xl bg-slate-900 text-white border border-cyan-500"><strong>1. Escolta Oficial (6 Elementos):</strong> Vanguardia (GI, AB, GD, CM) a 1 intervalo lateral; Retaguardia (RI, RD) a 3 pasos libres. Cadencia: 120 ppm.</div>
          <div class="p-4 rounded-xl bg-slate-900 text-white border border-emerald-500"><strong>2. Cuadrantes Praxiológicos:</strong> Subdivisión de cancha en 4 zonas para 4v4 simultáneo (>70% de compromiso motor sin filas).</div>
          <div class="p-4 rounded-xl bg-slate-900 text-white border border-violet-500"><strong>3. Red de Roles:</strong> Transición Portador → Apoyo sin balón → Recuperador mediante lectura de praxemas.</div>
        </div>
      </div>
    </section>

    <!-- MÓDULO 4: CLÍNICA -->
    <section id="view-clinic" class="hidden">
      <div class="card-box p-5 text-xs space-y-3">
        <h2 class="font-display font-black text-lg">Clínica de Patio: Dosificación Fisiológica y Ajustes DUA/BAP</h2>
        <div class="grid grid-cols-1 md:grid-cols-2 gap-3">
          <div class="p-4 rounded-xl bg-emerald-50 border border-emerald-300"><strong>Control de Carga (EPInfant):</strong> Intensidad objetivo RPE 4-7, pausas de rehidratación y mayéutica cada 12 min.</div>
          <div class="p-4 rounded-xl bg-sky-50 border border-sky-300"><strong>Ajustes Razonables BAP:</strong> Modificación de espacio (zonas protegidas), tiempo de posesión y dimensión del móvil para éxito motor equitativo.</div>
        </div>
      </div>
    </section>
  </main>

  <!-- MODAL CLIENTE: CANJEAR CÓDIGO -->
  <div id="unlockModal" class="fixed inset-0 bg-slate-950/80 z-50 hidden items-center justify-center p-4 no-print">
    <div class="bg-white rounded-3xl max-w-md w-full p-6 border-2 border-amber-400 space-y-4">
      <div class="flex justify-between items-center">
        <h3 class="font-display font-black text-lg">🔑 Activar Licencia VIP</h3>
        <button onclick="closeUnlockModal()" class="font-bold text-slate-500">✕</button>
      </div>
      <p class="text-xs text-slate-600">Ingresa tu código firmado para habilitar las descargas de expedientes y bitácoras en PDF.</p>
      <input id="inpClientCode" type="text" placeholder="PMX-08S-02P-XXXX-XXXX" class="w-full rounded-xl border-2 border-slate-300 px-3 py-2.5 font-mono font-bold text-center uppercase text-xs" />
      <button onclick="redeemClientCode()" class="w-full py-3 rounded-xl bg-amber-400 text-slate-950 font-display font-black text-xs">VALIDAR CÓDIGO Y ACTIVAR CRÉDITOS</button>
    </div>
  </div>

  <!-- MODAL CREADOR: PANEL MAESTRO -->
  <div id="masterModal" class="fixed inset-0 bg-slate-950/90 z-50 hidden items-center justify-center p-4 no-print">
    <div class="bg-slate-900 text-white rounded-3xl max-w-3xl w-full p-5 border-2 border-fuchsia-500 space-y-4 max-h-[90vh] overflow-y-auto text-xs">
      <div class="flex justify-between items-center border-b border-slate-700 pb-2">
        <h3 class="font-display font-black text-base text-fuchsia-300">⚙️ Panel Maestro • Licencias y API</h3>
        <button onclick="closeMasterModal()" class="font-bold text-slate-400">✕</button>
      </div>
      <div class="p-3 rounded-xl bg-slate-800 border border-cyan-500/40 space-y-2">
        <label class="font-extrabold text-cyan-300 uppercase block">1. Clave API de Gemini</label>
        <div class="flex gap-2">
          <input id="inpMasterApiKey" type="password" placeholder="AIzaSy..." class="flex-1 rounded-lg bg-slate-950 border border-slate-700 px-3 py-1.5 font-mono text-white" />
          <button onclick="saveMasterApiKey()" class="px-3 py-1.5 rounded-lg bg-cyan-500 text-slate-950 font-extrabold">Guardar API</button>
        </div>
      </div>
      <div class="p-3 rounded-xl bg-slate-800 border border-fuchsia-500/40 space-y-2">
        <label class="font-extrabold text-fuchsia-300 uppercase block">2. Cambiar Clave Maestra del Panel (Mín. 10 caracteres)</label>
        <div class="flex gap-2">
          <input id="inpNewMasterPass" type="text" placeholder="Nueva Clave Maestra segura..." class="flex-1 rounded-lg bg-slate-950 border border-slate-700 px-3 py-1.5 font-mono text-white" />
          <button onclick="updateMasterPassword()" class="px-3 py-1.5 rounded-lg bg-fuchsia-500 text-white font-extrabold">Cambiar Clave</button>
        </div>
      </div>
      <div class="p-3 rounded-xl bg-slate-800 border border-emerald-500/40 space-y-3">
        <label class="font-extrabold text-emerald-300 uppercase block">3. Emitir Código VIP con Vigencia por Descargas PDF</label>
        <div class="grid grid-cols-1 sm:grid-cols-3 gap-2">
          <select id="selVipMaxSessions" class="rounded-lg bg-slate-950 border border-slate-700 px-2.5 py-2 font-bold text-white">
            <option value="08">Paquete 8 Sesiones ($100)</option>
            <option value="20">Paquete 20 Sesiones ($200)</option>
            <option value="40">Paquete 40 Sesiones ($300)</option>
          </select>
          <input id="inpVipPdfLimit" type="number" min="1" max="99" value="2" class="rounded-lg bg-slate-950 border border-slate-700 px-2.5 py-2 font-bold text-amber-300" />
          <button onclick="issueSignedVipCode()" class="py-2 rounded-lg bg-emerald-500 text-slate-950 font-extrabold">🎲 Generar Código VIP</button>
        </div>
        <div id="newlyGeneratedCodeBox" class="hidden p-2.5 rounded-lg bg-emerald-950 border border-emerald-400 flex items-center justify-between">
          <span id="newlyGeneratedCodeText" class="font-mono font-black text-sm text-white"></span>
          <button onclick="copyLastGeneratedCode()" class="px-2.5 py-1 rounded bg-emerald-400 text-slate-950 font-extrabold">Copiar</button>
        </div>
        <div id="vipCodesTableContainer" class="max-h-36 overflow-y-auto rounded-lg border border-slate-700 bg-slate-950 p-2 space-y-1"></div>
      </div>
    </div>
  </div>

  <script>
    const STATIC_NEM_CURRICULUM = {
      f3_1: ["Explora sus posibilidades motrices al utilizar patrones básicos de movimiento en juegos individuales y colectivos."],
      f3_2: ["Combina diversos patrones básicos de movimiento para actuar con base en las características de cada juego."],
      f4_3: ["Adapta sus movimientos, de acuerdo con los elementos básicos de los juegos, para responder a las condiciones."],
      f4_4: ["Pone en práctica sus habilidades motrices en situaciones lúdicas, individuales y colectivas."],
      f5_5: ["Reconoce posibilidades y límites al participar en situaciones de juego e iniciación deportiva."],
      f5_6: ["Aplica sus capacidades, habilidades y destrezas motrices al organizar y participar en juegos e iniciación deportiva."],
      f6_1: ["Explora las capacidades, habilidades y destrezas motrices, para enriquecer y ampliar el potencial propio y de las demás personas."]
    };

    const METHODOLOGY_CASCADE = {
      PRAX: {
        nombre: "Praxiología Motriz (Parlebas / Pere Lavega)",
        dominios: ["[C-A] Sociomotriz de Cooperación-Oposición", "[C] Cooperación Pura", "[A] Oposición", "[0] Psicomotriz"],
        conflictos: ["Lectura de espacios libres y desmarque", "Comunicación motriz y relevos", "Pacto de reglas y lógica interna"]
      },
      TGFU: {
        nombre: "TGfU • Comprensión Táctica (Bunker & Thorpe)",
        dominios: ["[C-A] Invasión", "[C-A] Cancha Dividida"],
        conflictos: ["Conservar el móvil y progresar a meta", "Ataque al espacio vacío"]
      },
      MRPS: {
        nombre: "MRPS • Responsabilidad Social (Hellison)",
        dominios: ["[C-A] Arbitraje Autogestionado", "[C] Retos de Ayuda Mutua"],
        conflictos: ["Respeto y esfuerzo activo", "Autonomía y resolución pacífica"]
      },
      COOP: {
        nombre: "Aprendizaje Cooperativo (Velázquez)",
        dominios: ["[C] Cooperación Pura e Interdependencia"],
        conflictos: ["Reto grupal sin eliminación", "Sincronía colectiva"]
      }
    };

    const SEP_HOLIDAYS_2026_2027 = new Set([
      "2026-09-16","2026-09-25","2026-10-30","2026-11-02","2026-11-16","2026-11-27",
      "2027-01-29","2027-02-01","2027-02-26","2027-03-15","2027-04-30","2027-05-05","2027-05-14","2027-05-28","2027-06-25"
    ]);

    let selectedPackageSessions = 8;
    let secretClickCount = 0;
    let secretClickTimer = null;
    let currentGeneratedSessions = [];

    const CRYPTO_SALT = "PRAXIS_MAGISTER_RPP_2026_SIG";
    const STORAGE_KEYS = {
      MASTER_PASS: "pm_master_pass_v17",
      GEMINI_KEY: "pm_gemini_api_key_v17",
      VIP_DB: "pm_vip_codes_db_v17",
      ACTIVE_CODE: "pm_active_client_code_v17",
      EXHAUSTED_CODES: "pm_exhausted_codes_v17"
    };

    function computeCodeSignature(pkgStr, pdfStr, nonceStr) {
      const raw = `${pkgStr}-${pdfStr}-${nonceStr}-${CRYPTO_SALT}`;
      let hash = 2166136261;
      for (let i = 0; i < raw.length; i++) {
        hash ^= raw.charCodeAt(i);
        hash = Math.imul(hash, 16777619);
      }
      return (hash >>> 0).toString(16).toUpperCase().padStart(8, "0").slice(0, 4);
    }

    function initApp() {
      if (!localStorage.getItem(STORAGE_KEYS.MASTER_PASS)) {
        localStorage.setItem(STORAGE_KEYS.MASTER_PASS, "Praxis#Magister$2026!RPP");
      }
      if (!localStorage.getItem(STORAGE_KEYS.VIP_DB)) {
        const sig = computeCodeSignature("08", "02", "7K9M");
        const code = `PMX-08S-02P-7K9M-${sig}`;
        localStorage.setItem(STORAGE_KEYS.VIP_DB, JSON.stringify({ [code]: { maxSessions: 8, pdfCredits: 2 } }));
      }
      updateStaticCurriculum();
      onMethodologyCascadeChange();
      updateCalendarPreview();
      refreshLicenseUI();
      renderBitacorasSEP();
    }

    function updateStaticCurriculum() {
      const fase = document.getElementById("selFase").value;
      const idx = parseInt(document.getElementById("selContenido").value, 10) || 0;
      const pda = (STATIC_NEM_CURRICULUM[fase] && STATIC_NEM_CURRICULUM[fase][idx]) || STATIC_NEM_CURRICULUM.f5_6[0];
      document.getElementById("pdaDisplayBox").textContent = pda;
    }

    function onMethodologyCascadeChange() {
      const entorno = document.getElementById("selEntornoSesion").value;
      const modeloKey = document.getElementById("selModelo").value || "PRAX";
      const data = METHODOLOGY_CASCADE[modeloKey] || METHODOLOGY_CASCADE.PRAX;
      const domSelect = document.getElementById("selDominioCAI");
      const confSelect = document.getElementById("selConflicto");

      if (entorno === "ESCOLTA") {
        domSelect.innerHTML = `<option value="[C] Sincronía y Cooperación (Escolta)">[C] Sincronía y Cooperación (Escolta)</option>`;
        confSelect.innerHTML = `<option value="Cadencia 120 ppm, alineación geométrica y voces de mando">Cadencia 120 ppm, alineación y voces de mando</option>`;
        return;
      }
      domSelect.innerHTML = data.dominios.map(d => `<option value="${d}">${d}</option>`).join("");
      confSelect.innerHTML = data.conflictos.map(c => `<option value="${c}">${c}</option>`).join("");
    }

    function switchMainTab(tab) {
      ["planner", "bitacoras", "board", "clinic"].forEach(t => {
        document.getElementById(`view-${t}`).classList.toggle("hidden", t !== tab);
        document.getElementById(`tabBtn-${t}`).className = (t === tab)
          ? "px-3 py-1.5 rounded-xl text-xs font-bold bg-gradient-to-r from-emerald-500 to-cyan-500 text-white shadow"
          : "px-3 py-1.5 rounded-xl text-xs font-bold bg-white/10 text-slate-200";
      });
    }

    function selectSessionPackage(num) {
      selectedPackageSessions = num;
      [8, 20, 40].forEach(n => {
        document.getElementById(`pkgBtn-${n}`).className = (n === num)
          ? "px-3.5 py-2 rounded-xl text-xs font-extrabold bg-gradient-to-r from-indigo-600 to-cyan-600 text-white shadow"
          : "px-3.5 py-2 rounded-xl text-xs font-extrabold bg-white text-slate-700";
      });
      updateCalendarPreview();
    }

    function computeSchoolDates(total) {
      const startInput = document.getElementById("inpStartDate").value || "2026-10-26";
      const checked = Array.from(document.querySelectorAll(".day-check:checked")).map(c => parseInt(c.value, 10));
      const activeDays = checked.length ? checked : [1];
      const dates = [];
      let cursor = new Date(startInput + "T12:00:00");
      let safety = 0;
      while (dates.length < total && safety < 650) {
        safety++;
        const iso = cursor.toISOString().slice(0, 10);
        const d = cursor.getDay();
        const vac = (iso >= "2026-12-21" && iso <= "2027-01-06") || (iso >= "2027-03-22" && iso <= "2027-04-02");
        if (activeDays.includes(d) && !SEP_HOLIDAYS_2026_2027.has(iso) && !vac) dates.push(iso);
        cursor.setDate(cursor.getDate() + 1);
      }
      return dates;
    }

    function updateCalendarPreview() {
      const dates = computeSchoolDates(selectedPackageSessions);
      if (dates.length) {
        document.getElementById("calendarRangePreview").textContent =
          `📅 ${selectedPackageSessions} sesiones hábiles SEP: Inicia ${dates[0]} • Termina ${dates[dates.length - 1]}`;
      }
    }

    function getVipDatabase() {
      try { return JSON.parse(localStorage.getItem(STORAGE_KEYS.VIP_DB)) || {}; } catch { return {}; }
    }
    function saveVipDatabase(db) {
      localStorage.setItem(STORAGE_KEYS.VIP_DB, JSON.stringify(db));
      refreshLicenseUI();
      renderVipCodesTable();
    }

    function handleSecretCreatorClick() {
      secretClickCount++;
      clearTimeout(secretClickTimer);
      secretClickTimer = setTimeout(() => { secretClickCount = 0; }, 2200);
      if (secretClickCount >= 5) {
        secretClickCount = 0;
        const storedPass = localStorage.getItem(STORAGE_KEYS.MASTER_PASS);
        const inputPass = prompt("🔐 PANEL MAESTRO\nIngresa tu Clave Maestra:");
        if (inputPass && inputPass === storedPass) {
          document.getElementById("creatorTopBtn").classList.remove("hidden");
          openMasterCreatorModal();
        } else if (inputPass !== null) alert("❌ Clave Maestra incorrecta.");
      }
    }

    function openMasterCreatorModal() {
      document.getElementById("inpMasterApiKey").value = localStorage.getItem(STORAGE_KEYS.GEMINI_KEY) || "";
      renderVipCodesTable();
      document.getElementById("masterModal").classList.remove("hidden");
      document.getElementById("masterModal").classList.add("flex");
    }
    function closeMasterModal() {
      document.getElementById("masterModal").classList.add("hidden");
      document.getElementById("masterModal").classList.remove("flex");
    }
    function saveMasterApiKey() {
      const k = document.getElementById("inpMasterApiKey").value.trim();
      if (!k) return alert("Ingresa una API Key válida.");
      localStorage.setItem(STORAGE_KEYS.GEMINI_KEY, k);
      alert("✅ API Key guardada.");
    }
    function updateMasterPassword() {
      const p = document.getElementById("inpNewMasterPass").value.trim();
      if (p.length < 10) return alert("⚠️ Usa al menos 10 caracteres.");
      localStorage.setItem(STORAGE_KEYS.MASTER_PASS, p);
      document.getElementById("inpNewMasterPass").value = "";
      alert("✅ Clave Maestra actualizada.");
    }

    function issueSignedVipCode() {
      const pkgStr = document.getElementById("selVipMaxSessions").value;
      const pdfLimit = Math.min(99, Math.max(1, parseInt(document.getElementById("inpVipPdfLimit").value, 10) || 2));
      const pdfStr = String(pdfLimit).padStart(2, "0");
      const chars = "ABCDEFGHJKLMNPQRSTUVWXYZ23456789";
      let nonce = "";
      for (let i = 0; i < 4; i++) nonce += chars.charAt(Math.floor(Math.random() * chars.length));
      const sig = computeCodeSignature(pkgStr, pdfStr, nonce);
      const code = `PMX-${pkgStr}S-${pdfStr}P-${nonce}-${sig}`;
      const db = getVipDatabase();
      db[code] = { maxSessions: parseInt(pkgStr, 10), pdfCredits: pdfLimit };
      saveVipDatabase(db);
      document.getElementById("newlyGeneratedCodeText").textContent = code;
      document.getElementById("newlyGeneratedCodeBox").classList.remove("hidden");
    }

    function copyLastGeneratedCode() {
      const txt = document.getElementById("newlyGeneratedCodeText").textContent;
      if (txt) { navigator.clipboard.writeText(txt); alert(`✅ Copiado: ${txt}`); }
    }

    function deleteVipCode(code) {
      const db = getVipDatabase();
      delete db[code];
      saveVipDatabase(db);
    }

    function renderVipCodesTable() {
      const db = getVipDatabase();
      const box = document.getElementById("vipCodesTableContainer");
      const keys = Object.keys(db);
      box.innerHTML = keys.length ? keys.map(c => `
        <div class="flex justify-between items-center bg-slate-900 px-2.5 py-1.5 rounded border border-slate-800">
          <span><strong class="text-emerald-400 font-mono">${c}</strong> • ${db[c].maxSessions} ses. • <strong class="text-amber-300">PDFs: ${db[c].pdfCredits}</strong></span>
          <button onclick="deleteVipCode('${c}')" class="text-rose-400 font-bold">Eliminar</button>
        </div>
      `).join("") : `<p class="text-slate-500 text-center">Sin códigos.</p>`;
    }

    function openUnlockModal() {
      document.getElementById("unlockModal").classList.remove("hidden");
      document.getElementById("unlockModal").classList.add("flex");
    }
    function closeUnlockModal() {
      document.getElementById("unlockModal").classList.add("hidden");
      document.getElementById("unlockModal").classList.remove("flex");
    }

    function redeemClientCode() {
      const code = document.getElementById("inpClientCode").value.trim().toUpperCase();
      const exhausted = JSON.parse(localStorage.getItem(STORAGE_KEYS.EXHAUSTED_CODES) || "[]");
      if (exhausted.includes(code)) return alert("⚠️ Este código ya agotó sus descargas.");
      const db = getVipDatabase();
      if (!db[code]) {
        const m = code.match(/^PMX-(08|20|40)S-(\d{2})P-([A-Z0-9]{4})-([A-Z0-9]{4})$/);
        if (!m) return alert("❌ Formato de código inválido.");
        const [, pkgStr, pdfStr, nonceStr, sig] = m;
        if (sig !== computeCodeSignature(pkgStr, pdfStr, nonceStr)) return alert("❌ Código alterado o apócrifo.");
        db[code] = { maxSessions: parseInt(pkgStr, 10), pdfCredits: parseInt(pdfStr, 10) };
        saveVipDatabase(db);
      }
      if (db[code].pdfCredits <= 0) return alert("⚠️ Sin créditos PDF.");
      localStorage.setItem(STORAGE_KEYS.ACTIVE_CODE, code);
      selectSessionPackage(db[code].maxSessions);
      refreshLicenseUI();
      closeUnlockModal();
      alert(`✅ Código activado: ${db[code].pdfCredits} descargas de PDF disponibles.`);
    }

    function refreshLicenseUI() {
      const code = localStorage.getItem(STORAGE_KEYS.ACTIVE_CODE);
      const db = getVipDatabase();
      const badge = document.getElementById("vipBadgeStatus");
      const txt = document.getElementById("licenseStatusText");
      if (code && db[code] && db[code].pdfCredits > 0) {
        badge.textContent = `CRÉDITOS PDF: ${db[code].pdfCredits}`;
        txt.textContent = `${db[code].pdfCredits} DESCARGAS PDF RESTANTES`;
        txt.className = "text-xs font-extrabold text-emerald-400";
      } else {
        badge.textContent = `CRÉDITOS PDF: 0`;
        txt.textContent = `SIN CRÉDITOS PDF ACTIVOS`;
        txt.className = "text-xs font-extrabold text-amber-400";
      }
    }

    function consumeCreditAndPrintPDF() {
      if (!currentGeneratedSessions.length) return alert("⚠️ Primero genera las sesiones con el botón 1.");
      const code = localStorage.getItem(STORAGE_KEYS.ACTIVE_CODE);
      const db = getVipDatabase();
      if (!code || !db[code] || db[code].pdfCredits <= 0) {
        openUnlockModal();
        return alert("🔒 Activa un Código VIP con créditos de descarga PDF vigentes.");
      }
      db[code].pdfCredits -= 1;
      if (db[code].pdfCredits <= 0) {
        const ex = JSON.parse(localStorage.getItem(STORAGE_KEYS.EXHAUSTED_CODES) || "[]");
        ex.push(code);
        localStorage.setItem(STORAGE_KEYS.EXHAUSTED_CODES, JSON.stringify(ex));
      }
      saveVipDatabase(db);
      setTimeout(() => window.print(), 250);
    }

    // CONSUMO DE CRÉDITO PARA IMPRIMIR LAS BITÁCORAS
    function consumeCreditAndPrintBitacoras() {
      const code = localStorage.getItem(STORAGE_KEYS.ACTIVE_CODE);
      const db = getVipDatabase();
      if (!code || !db[code] || db[code].pdfCredits <= 0) {
        openUnlockModal();
        return alert("🔒 El acceso a las Bitácoras SEP requiere un Código VIP con créditos vigentes.");
      }
      db[code].pdfCredits -= 1;
      if (db[code].pdfCredits <= 0) {
        const ex = JSON.parse(localStorage.getItem(STORAGE_KEYS.EXHAUSTED_CODES) || "[]");
        ex.push(code);
        localStorage.setItem(STORAGE_KEYS.EXHAUSTED_CODES, JSON.stringify(ex));
      }
      saveVipDatabase(db);
      setTimeout(() => window.print(), 250);
    }

    // GENERADOR DE PLANEACIÓN VÍA API GEMINI CON PORTADA OFICIAL
    async function generateSessionsWithAI() {
      const apiKey = localStorage.getItem(STORAGE_KEYS.GEMINI_KEY);
      if (!apiKey) return alert("⚠️ Configura tu API Key de Gemini en el Panel Maestro (5 clics en PM).");

      const btn = document.getElementById("btnGenerateAI");
      const output = document.getElementById("planOutputContainer");
      const meta = {
        docente: document.getElementById("inpDocente").value,
        escuela: document.getElementById("inpEscuela").value,
        cct: document.getElementById("inpCCT").value,
        grupo: document.getElementById("inpGrupo").value,
        director: document.getElementById("inpDirector").value,
        modalidad: document.getElementById("selModalidad").value,
        entorno: document.getElementById("selEntornoSesion").options[document.getElementById("selEntornoSesion").selectedIndex].text,
        fase: document.getElementById("selFase").options[document.getElementById("selFase").selectedIndex].text,
        contenido: document.getElementById("selContenido").options[document.getElementById("selContenido").selectedIndex].text,
        pda: document.getElementById("pdaDisplayBox").textContent,
        modeloBase: document.getElementById("selModelo").value,
        modeloSec: document.getElementById("selModeloSecundario").value,
        dominioCAI: document.getElementById("selDominioCAI").value,
        conflicto: document.getElementById("selConflicto").value,
        eje: document.getElementById("selEje").value,
        instrumento: document.getElementById("selInstrumento").value,
        problematica: document.getElementById("inpProblematica").value
      };
      const dates = computeSchoolDates(selectedPackageSessions);

      btn.disabled = true;
      btn.textContent = `⏳ DISEÑANDO EXPEDIENTE Y PORTADA...`;
      output.innerHTML = `<div class="card-box p-6 text-center font-bold text-sm">Construyendo ${selectedPackageSessions} sesiones y portada institucional...</div>`;

      const prompt = `Actúa como Doctor en Cultura Física, experto en Praxiología Motriz (Parlebas/Lavega) y NEM 2026-2027.
Diseña exactamente ${selectedPackageSessions} sesiones de Educación Física TOTALMENTE DIFERENTES Y PROGRESIVAS (PROHIBIDO repetir juegos).
Parámetros fijos:
- Estructura: ${meta.modalidad} | Entorno: ${meta.entorno}
- Nivel: ${meta.fase} (${meta.grupo}) | Contenido: ${meta.contenido}
- PDA: ${meta.pda}
- Metodología: ${meta.modeloBase} ${meta.modeloSec}
- Dominio [CAI]: ${meta.dominioCAI} | Conflicto: ${meta.conflicto}
- Contexto: ${meta.problematica}

Devuelve SOLO un arreglo JSON válido con ${selectedPackageSessions} objetos con las llaves exactas:
[{"numero":1,"titulo_tactico":"...","inicial":"Juego inédito + reglas y biomecánica (mín 50 palabras)","medular":"Situación motriz + lógica interna detallada (espacio, tiempo, móvil, roles, subroles y variante táctica, mín 90 palabras)","cierre":"Vuelta a la calma + pregunta mayéutica (mín 40 palabras)","adecuacion_bap":"Ajuste DUA","indicador_evaluacion":"Indicador observable"}]`;

      try {
        const res = await fetch(`https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash:generateContent?key=${apiKey}`, {
          method: "POST",
          headers: { "Content-Type": "application/json" },
          body: JSON.stringify({
            contents: [{ parts: [{ text: prompt }] }],
            generationConfig: { temperature: 0.78, responseMimeType: "application/json" }
          })
        });
        const data = await res.json();
        const raw = data?.candidates?.[0]?.content?.parts?.[0]?.text;
        if (!raw) throw new Error("Verifica tu API Key.");
        currentGeneratedSessions = JSON.parse(raw);
        renderFullExpediente(currentGeneratedSessions, dates, meta);
      } catch (e) {
        output.innerHTML = `<div class="card-box p-4 bg-rose-50 text-rose-900 text-xs font-bold">❌ Error API: ${e.message}</div>`;
      } finally {
        btn.disabled = false;
        btn.textContent = `⚡ 1. DISEÑAR SESIONES IRREPETIBLES CON API`;
      }
    }

    function renderFullExpediente(sessions, dates, meta) {
      let html = `
        <!-- PORTADA OFICIAL DE PRESENTACIÓN -->
        <article class="print-sheet space-y-6 flex flex-col justify-between" style="min-height: 240mm;">
          <div class="space-y-4 text-center">
            <div class="text-xs font-extrabold uppercase tracking-widest text-slate-600">AUTORIDAD EDUCATIVA FEDERAL • NUEVA ESCUELA MEXICANA 2026-2027</div>
            <h1 class="font-display font-black text-2xl md:text-3xl text-slate-900">EXPEDIENTE TÉCNICO DE INGENIERÍA DIDÁCTICA Y PRAXIOLÓGICA EN EDUCACIÓN FÍSICA</h1>
            <div class="w-24 h-1 bg-emerald-600 mx-auto rounded-full"></div>
          </div>

          <div class="grid grid-cols-1 md:grid-cols-2 gap-4 text-xs bg-slate-50 p-6 rounded-2xl border-2 border-slate-200">
            <div><strong>Escuela / Plantel:</strong> ${meta.escuela}</div>
            <div><strong>CCT y Zona Escolar:</strong> ${meta.cct}</div>
            <div><strong>Docente Titular:</strong> ${meta.docente}</div>
            <div><strong>Grado y Grupo:</strong> ${meta.grupo}</div>
            <div><strong>Estructura Metodológica:</strong> ${meta.modalidad}</div>
            <div><strong>Modelo Pedagógico:</strong> ${meta.modeloBase} ${meta.modeloSec}</div>
            <div><strong>Contenido Sintético:</strong> ${meta.contenido}</div>
            <div><strong>Eje Articulador:</strong> ${meta.eje}</div>
            <div class="md:col-span-2"><strong>PDA Oficial Vinculado:</strong> <em>${meta.pda}</em></div>
          </div>

          <div class="p-4 rounded-xl bg-emerald-50 border border-emerald-300 text-xs text-emerald-950 text-center font-bold">
            📁 Secuencia de ${sessions.length} sesiones abarcando del <strong>${dates[0] || ""}</strong> al <strong>${dates[dates.length - 1] || ""}</strong>.
          </div>

          <div class="pt-8 border-t grid grid-cols-2 gap-12 text-center text-xs">
            <div>
              <div class="border-b border-slate-400 w-3/4 mx-auto mb-2"></div>
              <strong>${meta.docente}</strong><br>Docente de Educación Física
            </div>
            <div>
              <div class="border-b border-slate-400 w-3/4 mx-auto mb-2"></div>
              <strong>${meta.director}</strong><br>Sello y Validación Directiva
            </div>
          </div>
        </article>
      `;

      // SESIONES
      html += sessions.map((s, i) => `
        <article class="print-sheet space-y-3">
          <div class="border-b-2 border-slate-900 pb-2 flex justify-between items-center">
            <h2 class="font-display font-black text-base">SESIÓN ${s.numero || i + 1} DE ${sessions.length}: ${s.titulo_tactico}</h2>
            <span class="text-xs font-bold bg-slate-100 px-2.5 py-1 rounded border">FECHA: ${dates[i] || ""}</span>
          </div>
          <div class="grid grid-cols-1 md:grid-cols-3 gap-1.5 text-[11px] bg-slate-50 p-2.5 rounded-xl border">
            <div><strong>Plantel:</strong> ${meta.escuela} (${meta.cct})</div>
            <div><strong>Docente:</strong> ${meta.docente} | <strong>Grupo:</strong> ${meta.grupo}</div>
            <div><strong>Dominio [CAI]:</strong> ${meta.dominioCAI}</div>
            <div class="md:col-span-3"><strong>Conflicto Motor:</strong> ${meta.conflicto}</div>
          </div>
          <div class="space-y-2 text-xs leading-relaxed">
            <div class="p-3 rounded-xl bg-sky-50 border-l-4 border-sky-700"><strong>1. Fase Inicial (10 min):</strong> ${s.inicial}</div>
            <div class="p-3 rounded-xl bg-emerald-50 border-l-4 border-emerald-700"><strong>2. Fase Medular • Lógica Interna (30 min):</strong> ${s.medular}</div>
            <div class="p-3 rounded-xl bg-violet-50 border-l-4 border-violet-700"><strong>3. Fase Cierre y Mayéutica (10 min):</strong> ${s.cierre}</div>
          </div>
          <div class="grid grid-cols-1 md:grid-cols-2 gap-2 text-[11px] bg-amber-50 p-2 rounded-lg border border-amber-300">
            <div><strong>Adecuación DUA/BAP:</strong> ${s.adecuacion_bap}</div>
            <div><strong>Evaluación (${meta.instrumento}):</strong> ${s.indicador_evaluacion}</div>
          </div>
          <div class="pt-4 border-t grid grid-cols-2 gap-6 text-center text-[11px]">
            <div><div class="border-b border-slate-400 w-3/4 mx-auto mb-1"></div><strong>${meta.docente}</strong></div>
            <div><div class="border-b border-slate-400 w-3/4 mx-auto mb-1"></div><strong>${meta.director}</strong></div>
          </div>
        </article>
      `).join("");

      document.getElementById("planOutputContainer").innerHTML = html;
    }

    // RENDERIZADO DE LAS 2 BITÁCORAS SEP CON REDACCIÓN FORMAL ASISTIDA
    function renderBitacorasSEP() {
      const doc = document.getElementById("inpDocente")?.value || "Prof. Educación Física";
      const esc = document.getElementById("inpEscuela")?.value || "Escuela Primaria Oficial";
      const cct = document.getElementById("inpCCT")?.value || "09DPR0000X";
      const grupo = document.getElementById("inpGrupo")?.value || "5° y 6° A";
      const dir = document.getElementById("inpDirector")?.value || "Dirección del Plantel";

      const f1 = document.getElementById("b1Fecha")?.value || "2026-10-26";
      const r1 = document.getElementById("b1Raw")?.value || "Sin reportes informales ingresados.";
      const f2 = document.getElementById("b2Fecha")?.value || "2026-10-26";
      const r2 = document.getElementById("b2Raw")?.value || "Sin incidencias reportadas.";

      document.getElementById("bitacorasOutput").innerHTML = `
        <!-- FORMATO 1 SEP -->
        <article class="print-sheet space-y-4 text-xs">
          <div class="text-center border-b pb-2">
            <strong class="text-[10px] uppercase text-slate-600 block">AUTORIDAD EDUCATIVA FEDERAL EN LA CIUDAD DE MÉXICO • DGOSE</strong>
            <h3 class="font-display font-black text-sm text-slate-900 mt-0.5">FORMATO 1: BITÁCORA DOCENTE DE OBSERVACIÓN DE LA COMUNIDAD ESCOLAR, ESPACIOS Y COBERTURA</h3>
          </div>
          <div class="grid grid-cols-3 gap-2 bg-slate-50 p-3 rounded-xl border">
            <div><strong>Escuela:</strong> ${esc} (${cct})</div>
            <div><strong>Grupo:</strong> ${grupo}</div>
            <div><strong>Fecha:</strong> ${f1}</div>
          </div>
          <div class="space-y-2">
            <div class="p-3 rounded-lg bg-sky-50/80 border border-sky-200">
              <strong>1. Ámbito de Observación y Gestión Escolar:</strong> Asignación de espacios y salvaguarda de cobertura en patio escolar.
            </div>
            <div class="p-3 rounded-lg bg-white border border-slate-300">
              <strong>2. Descripción Institucional (Traducción Normativa de tus Notas):</strong>
              <p class="mt-1 text-slate-800 leading-relaxed"><em>"${r1}"</em> → Se observa y documenta la incidencia en la gestión de espacios deportivos, requiriendo acuerdo en el colectivo docente para evitar el uso simultáneo que comprometa la integridad física del alumnado conforme a la Guía Operativa vigente.</p>
            </div>
            <div class="p-3 rounded-lg bg-emerald-50/80 border border-emerald-200">
              <strong>3. Intervención y Acuerdos:</strong> Generar acuerdos por escrito con la dirección para el uso equitativo de instalaciones y salvaguarda continua del estudiantado.
            </div>
          </div>
          <div class="pt-6 border-t grid grid-cols-2 gap-8 text-center text-[11px]">
            <div><div class="border-b border-slate-400 w-3/4 mx-auto mb-1"></div><strong>${doc}</strong><br>Docente de Educación Física</div>
            <div><div class="border-b border-slate-400 w-3/4 mx-auto mb-1"></div><strong>${dir}</strong><br>Vo. Bo. Dirección</div>
          </div>
        </article>

        <!-- FORMATO 2 SEP -->
        <article class="print-sheet space-y-4 text-xs">
          <div class="text-center border-b pb-2">
            <strong class="text-[10px] uppercase text-slate-600 block">AUTORIDAD EDUCATIVA FEDERAL EN LA CIUDAD DE MÉXICO • DGOSE</strong>
            <h3 class="font-display font-black text-sm text-slate-900 mt-0.5">FORMATO 2: ACTA DESCRIPTIVA Y BITÁCORA DE INCIDENCIA ESTUDIANTIL Y CONVIVENCIA</h3>
          </div>
          <div class="grid grid-cols-3 gap-2 bg-slate-50 p-3 rounded-xl border">
            <div><strong>Escuela:</strong> ${esc} (${cct})</div>
            <div><strong>Grupo:</strong> ${grupo}</div>
            <div><strong>Fecha:</strong> ${f2}</div>
          </div>
          <div class="space-y-2">
            <div class="p-3 rounded-lg bg-amber-50/80 border border-amber-200">
              <strong>1. Clasificación de la Incidencia:</strong> Conflicto interpersonal / mediación formativa en la situación motriz.
            </div>
            <div class="p-3 rounded-lg bg-white border border-slate-300">
              <strong>2. Narración Jurídico-Objetiva (Traducción Normativa de tus Notas):</strong>
              <p class="mt-1 text-slate-800 leading-relaxed"><em>"${r2}"</em> → Se registra evento de desacuerdo y fricción interpersonal durante el desarrollo de la tarea motriz. Se interviene de forma inmediata aplicando contención pedagógica, mediación mediante diálogo reflexivo y establecimiento de compromisos de convivencia pacífica.</p>
            </div>
            <div class="p-3 rounded-lg bg-emerald-50/80 border border-emerald-200">
              <strong>3. Protocolo de Actuación y Acuerdos Reparadores:</strong> Valoración emocional inmediata, feedback interrogativo y compromiso de respeto mutuo.
            </div>
          </div>
          <div class="pt-6 border-t grid grid-cols-2 gap-8 text-center text-[11px]">
            <div><div class="border-b border-slate-400 w-3/4 mx-auto mb-1"></div><strong>${doc}</strong><br>Docente de Educación Física</div>
            <div><div class="border-b border-slate-400 w-3/4 mx-auto mb-1"></div><strong>${dir}</strong><br>Autoridad Directiva</div>
          </div>
        </article>
      `;
    }

    window.addEventListener("DOMContentLoaded", initApp);
  </script>
</body>
</html>