<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Checklist Diario de Obra - Frente 1</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">
    <style>
        :root {
            --primary: #1e293b;
            --accent: #3b82f6;
            --success: #22c55e;
            --danger: #ef4444;
            --warning: #f59e0b;
            --bg: #f8fafc;
        }

        body { font-family: 'Inter', system-ui, sans-serif; background: var(--bg); margin: 0; padding: 20px; color: var(--primary); }
        .container { max-width: 1400px; margin: 0 auto; background: white; padding: 25px; border-radius: 12px; box-shadow: 0 4px 20px rgba(0,0,0,0.08); }
        
        header { display: flex; justify-content: space-between; align-items: flex-start; border-bottom: 2px solid #e2e8f0; padding-bottom: 20px; margin-bottom: 20px; }
        .project-info h1 { margin: 0; font-size: 20px; color: var(--primary); }
        .project-info p { margin: 5px 0; color: #64748b; font-size: 14px; }

        .tabs { display: flex; gap: 8px; margin-bottom: 20px; overflow-x: auto; padding-bottom: 5px; }
        .tab-btn { padding: 10px 15px; border: none; background: #e2e8f0; border-radius: 8px; cursor: pointer; font-weight: 600; white-space: nowrap; transition: 0.2s; font-size: 13px; }
        .tab-btn.active { background: var(--accent); color: white; }

        table { width: 100%; border-collapse: collapse; margin-top: 10px; font-size: 13px; }
        th { background: #f1f5f9; padding: 10px; text-align: left; border-bottom: 2px solid #e2e8f0; white-space: nowrap; }
        td { padding: 10px; border-bottom: 1px solid #e2e8f0; vertical-align: middle; }

        .check-cell { width: 35px; text-align: center; }
        input[type="checkbox"] { width: 18px; height: 18px; cursor: pointer; }

        tr.done { background-color: #f0fdf4; color: #166534; }
        tr.done td:nth-child(2) { text-decoration: line-through; opacity: 0.6; }

        .status-pill { padding: 4px 8px; border-radius: 6px; font-size: 11px; font-weight: bold; }
        .pill-pending { background: #fee2e2; color: #991b1b; }
        .pill-done { background: #dcfce7; color: #166534; }

        .change-request-section { margin-top: 40px; border-top: 3px solid var(--warning); padding-top: 20px; }
        .summary-section { margin-top: 40px; border-top: 3px solid var(--success); padding-top: 20px; display: none; background: #f0fdf4; padding: 20px; border-radius: 8px; }
        
        .btn-add { background: var(--warning); color: white; border: none; padding: 8px 16px; border-radius: 6px; cursor: pointer; font-weight: bold; }
        .btn-pdf { background: var(--accent); color: white; border: none; padding: 10px 20px; border-radius: 6px; cursor: pointer; font-weight: bold; }
        
        .change-row { background-color: #fffbeb; }
        .change-row input, .change-row select { 
            width: 100%; padding: 6px; border: 1px solid #ddd; border-radius: 4px; font-size: 12px;
        }

        .item-code { font-weight: bold; color: #475569; background: #f1f5f9; padding: 2px 5px; border-radius: 4px; margin-right: 5px; }

        @media print { 
            .no-print { display: none; } 
            .container { box-shadow: none; border: none; max-width: 100%; padding: 0; } 
            .summary-section { display: block !important; }
            body { background: white; padding: 0; }
        }
    </style>
</head>
<body>

<div class="container">
    <header>
        <div class="project-info">
            <p><strong>PROYECTO:</strong> BELEMPAMPA - CUSCO (GORE CUSCO)</p>
            <h1>PROGRAMACIÓN SEMANAL COMPLETA - FRENTE 1</h1>
            <p><i class="fa-regular fa-calendar"></i> Semana del 23 al 28 de Marzo (Rev. 00)</p>
        </div>
        <button class="no-print btn-pdf" onclick="window.print()"><i class="fa-solid fa-file-pdf"></i> Generar Reporte PDF</button>
    </header>

    <div class="tabs no-print">
        <button id="btn-Lunes" class="tab-btn active" onclick="showDay('Lunes', this)">Lun 23</button>
        <button id="btn-Martes" class="tab-btn" onclick="showDay('Martes', this)">Mar 24</button>
        <button id="btn-Miercoles" class="tab-btn" onclick="showDay('Miercoles', this)">Mié 25</button>
        <button id="btn-Jueves" class="tab-btn" onclick="showDay('Jueves', this)">Jue 26</button>
        <button id="btn-Viernes" class="tab-btn" onclick="showDay('Viernes', this)">Vie 27</button>
        <button id="btn-Sabado" class="tab-btn" onclick="showDay('Sabado', this)" style="background: #cbd5e1;">Sáb 28 (Cierre)</button>
    </div>

    <h2 id="current-day-title" style="color: var(--accent);">Lunes 23 de Marzo</h2>
    
    <table id="main-table">
        <thead>
            <tr>
                <th class="check-cell">Ok</th>
                <th>Actividad Programada (Descripción)</th>
                <th>Responsable</th>
                <th>Cuadrilla / Metrado</th>
                <th>Estado</th>
            </tr>
        </thead>
        <tbody id="checklist-body">
            <!-- ÍTEMS ESTRUCTURAS -->
            <tr data-days="Lunes,Martes,Miercoles,Jueves,Viernes,Sabado">
                <td class="check-cell"><input type="checkbox" onchange="toggleRow(this)"></td>
                <td><span class="item-code">01.01.01</span> Compactación (Bloque 2 - Sótano)</td>
                <td>Ing. Michelle</td>
                <td>OP-OF-PE | 10.00 m3</td>
                <td><span class="status-pill pill-pending">Pendiente</span></td>
            </tr>
            <tr data-days="Lunes,Martes,Miercoles,Jueves,Viernes,Sabado">
                <td class="check-cell"><input type="checkbox" onchange="toggleRow(this)"></td>
                <td><span class="item-code">06.01.207</span> Montaje de Estructura Metálica</td>
                <td>Ing. Jean Carlos</td>
                <td>450 KG/día | 1350 KG Total</td>
                <td><span class="status-pill pill-pending">Pendiente</span></td>
            </tr>
            <tr data-days="Jueves,Viernes,Sabado">
                <td class="check-cell"><input type="checkbox" onchange="toggleRow(this)"></td>
                <td><span class="item-code">06.01.207</span> Pintura y Acabado Final (Estructuras)</td>
                <td>Ing. Jean Carlos</td>
                <td>400 m2 | Cuadrilla Esp.</td>
                <td><span class="status-pill pill-pending">Pendiente</span></td>
            </tr>

            <!-- ÍTEMS ARQUITECTURA -->
            <tr data-days="Lunes,Martes,Miercoles,Jueves,Viernes,Sabado">
                <td class="check-cell"><input type="checkbox" onchange="toggleRow(this)"></td>
                <td><span class="item-code">05.01.01</span> Tarrajeo de superficies (Vert. / Horiz.)</td>
                <td>Arq. Nilam</td>
                <td>Cuadrilla Arq.</td>
                <td><span class="status-pill pill-pending">Pendiente</span></td>
            </tr>
            <tr data-days="Lunes,Martes,Miercoles,Jueves,Viernes,Sabado">
                <td class="check-cell"><input type="checkbox" onchange="toggleRow(this)"></td>
                <td><span class="item-code">06.02.02</span> Trabajos en Techo</td>
                <td>Arq. Nilam</td>
                <td>Cuadrilla Techos</td>
                <td><span class="status-pill pill-pending">Pendiente</span></td>
            </tr>
            <tr data-days="Lunes,Martes,Miercoles,Jueves,Viernes,Sabado">
                <td class="check-cell"><input type="checkbox" onchange="toggleRow(this)"></td>
                <td><span class="item-code">4.1.2.1</span> Enchapados (C2-Enchapados)</td>
                <td>Arq. Cantero / Alexandria</td>
                <td>10 Personas | Bloque 2</td>
                <td><span class="status-pill pill-pending">Pendiente</span></td>
            </tr>

            <!-- ÍTEMS INSTALACIONES -->
            <tr data-days="Lunes,Martes,Miercoles">
                <td class="check-cell"><input type="checkbox" onchange="toggleRow(this)"></td>
                <td><span class="item-code">IS</span> Excavación de zanjas (Redes Sanitarias)</td>
                <td>Ing. Cesar</td>
                <td>Exc. Manual</td>
                <td><span class="status-pill pill-pending">Pendiente</span></td>
            </tr>
            <tr data-days="Lunes,Martes,Miercoles,Jueves,Viernes,Sabado">
                <td class="check-cell"><input type="checkbox" onchange="toggleRow(this)"></td>
                <td><span class="item-code">C4-GASF</span> Instalaciones de Gasfitería</td>
                <td>Ing. Cesar</td>
                <td>Cuadrilla Gasf.</td>
                <td><span class="status-pill pill-pending">Pendiente</span></td>
            </tr>
            <tr data-days="Lunes,Martes,Miercoles,Jueves,Viernes,Sabado">
                <td class="check-cell"><input type="checkbox" onchange="toggleRow(this)"></td>
                <td><span class="item-code">IE</span> Instalaciones Eléctricas (Bloque 2 Sótano)</td>
                <td>Ing. Cesar</td>
                <td>Cuadrilla Elec.</td>
                <td><span class="status-pill pill-pending">Pendiente</span></td>
            </tr>
            <tr data-days="Lunes,Martes,Miercoles,Jueves,Viernes,Sabado">
                <td class="check-cell"><input type="checkbox" onchange="toggleRow(this)"></td>
                <td><span class="item-code">12</span> Instalación de Canaletas y Cobertura Tejandina</td>
                <td>Ing. Cesar / Jean C.</td>
                <td>100 ml / 20.00 m2</td>
                <td><span class="status-pill pill-pending">Pendiente</span></td>
            </tr>

            <!-- CIERRE SEMANAL -->
            <tr data-days="Sabado">
                <td class="check-cell"><input type="checkbox" onchange="toggleRow(this)"></td>
                <td><span class="item-code">CIERRE</span> Limpieza, Orden y Seguridad del Frente 1</td>
                <td>Ing. Michelle</td>
                <td>Todo el Personal</td>
                <td><span class="status-pill pill-pending">Pendiente</span></td>
            </tr>
        </tbody>
    </table>

    <!-- REGISTRO DE CAMBIOS -->
    <div class="change-request-section">
        <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 15px;">
            <h3 style="margin: 0; color: var(--warning);"><i class="fa-solid fa-triangle-exclamation"></i> Registro de Cambios y Adicionales (Fecha Dinámica)</h3>
            <button class="no-print btn-add" onclick="addChangeRow()"><i class="fa-solid fa-plus"></i> Registrar Nuevo Cambio</button>
        </div>
        <div style="overflow-x: auto;">
            <table id="change-table">
                <thead>
                    <tr>
                        <th class="check-cell">Ok</th>
                        <th>Fecha</th>
                        <th>Bloque</th>
                        <th>Nivel</th>
                        <th>Actividad No Programada</th>
                        <th>Sustento / Motivo</th>
                        <th>Responsable</th>
                        <th>Impacto</th>
                    </tr>
                </thead>
                <tbody id="change-body"></tbody>
            </table>
        </div>
    </div>

    <!-- INFORME DE CIERRE -->
    <div id="summary-area" class="summary-section">
        <h3 style="margin-top:0;"><i class="fa-solid fa-chart-line"></i> Informe de Cierre de Semana - Frente 1</h3>
        <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 20px;">
            <div>
                <label><strong>% Avance Real</strong></label><br>
                <input type="text" placeholder="Ej: 98%" style="width:100%; padding:8px; margin-top:5px; border:1px solid #ccc; border-radius:4px;">
            </div>
            <div>
                <label><strong>Observaciones / Restricciones</strong></label><br>
                <textarea rows="3" style="width:100%; padding:8px; margin-top:5px; border:1px solid #ccc; border-radius:4px;" placeholder="Detalles de supervisión..."></textarea>
            </div>
        </div>
    </div>
</div>

<script>
    const datesMap = { 
        'Lunes': '2025-03-23', 
        'Martes': '2025-03-24', 
        'Miercoles': '2025-03-25', 
        'Jueves': '2025-03-26', 
        'Viernes': '2025-03-27', 
        'Sabado': '2025-03-28' 
    };

    function toggleRow(checkbox) {
        const row = checkbox.closest('tr');
        const pill = row.querySelector('.status-pill');
        if (checkbox.checked) {
            row.classList.add('done');
            if(pill) {
                pill.textContent = 'Completado';
                pill.className = 'status-pill pill-done';
            }
        } else {
            row.classList.remove('done');
            if(pill) {
                pill.textContent = 'Pendiente';
                pill.className = 'status-pill pill-pending';
            }
        }
    }

    function showDay(day, btn) {
        document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
        const activeBtn = btn || document.getElementById('btn-' + day);
        if (activeBtn) activeBtn.classList.add('active');
        
        const dayNum = datesMap[day].split('-')[2];
        document.getElementById('current-day-title').textContent = `${day} ${dayNum} de Marzo`;

        const summaryArea = document.getElementById('summary-area');
        if(summaryArea) summaryArea.style.display = (day === 'Sabado') ? 'block' : 'none';

        // Filtro de programación
        const rows = document.querySelectorAll('#checklist-body tr');
        rows.forEach(row => {
            const daysAllowed = row.getAttribute('data-days');
            if (daysAllowed) {
                row.style.display = daysAllowed.includes(day) ? '' : 'none';
            }
        });

        // Sincronización automática de fechas en la tabla de cambios
        const currentSelectedDate = datesMap[day];
        const changeRows = document.querySelectorAll('#change-body tr');
        changeRows.forEach(row => {
            const dateInput = row.querySelector('input[type="date"]');
            if(dateInput) dateInput.value = currentSelectedDate;
        });
    }

    function addChangeRow() {
        const body = document.getElementById('change-body');
        const newRow = document.createElement('tr');
        newRow.className = 'change-row';
        
        const activeTab = document.querySelector('.tab-btn.active');
        const dayKey = activeTab ? activeTab.id.replace('btn-', '') : 'Lunes';
        const initialDate = datesMap[dayKey];

        newRow.innerHTML = `
            <td class="check-cell"><input type="checkbox" onchange="toggleRow(this)"></td>
            <td><input type="date" value="${initialDate}"></td>
            <td><select><option>Bloque 1</option><option>Bloque 2</option><option>Bloque 3</option><option>Exteriores</option></select></td>
            <td><select><option>Sótano</option><option>Piso 1</option><option>Piso 2</option><option>Piso 3</option><option>Azotea</option></select></td>
            <td><input type="text" placeholder="Actividad..."></td>
            <td><input type="text" placeholder="Motivo..."></td>
            <td><select><option>Ing. Michelle</option><option>Ing. Cesar</option><option>Ing. Jean Carlos</option><option>Arq. Nilam</option><option>Arq. Cantero</option></select></td>
            <td><select><option>Bajo</option><option>Medio</option><option>Alto</option></select></td>
        `;
        body.appendChild(newRow);
    }

    window.addEventListener('load', () => {
        showDay('Lunes');
    });
</script>

</body>
</html>
