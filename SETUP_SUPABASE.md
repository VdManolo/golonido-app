# Configuración de Supabase para GoloNido

## Campo faltante en la tabla `nidos`

Para que el sistema de reportes funcione correctamente, debes añadir una columna a la tabla `nidos` en Supabase:

### Nuevo campo a agregar:
- **Nombre**: `reports_count`
- **Tipo**: `integer`
- **Default**: `0`
- **Nullable**: No

### Pasos en Supabase:
1. Ve a tu proyecto en supabase.co
2. Abre la tabla `nidos`
3. Haz clic en "+" para añadir una columna
4. Configura:
   - Column name: `reports_count`
   - Type: `int8` (integer)
   - Default value: `0`
5. Guarda los cambios

---

## Funcionalidades implementadas:

### 1. **Panel de Administración**
   - Acceso con botón "⚙️ Admin" en la esquina inferior derecha
   - Atajo de teclado: `Ctrl + Shift + A`
   - Requiere acceso al navegador (sin autenticación por ahora)

### 2. **Tres pestañas principales:**

#### a) **Nidos** - Gestión completa
   - Tabla con todos los nidos
   - Muestra: ID, tipo, ubicación, usuario, fecha, reportes
   - Botones:
     - **Ver**: Para ver detalles
     - **Eliminar**: Para eliminar nidos (con confirmación)

#### b) **Estadísticas** - Análisis de datos
   - Total de nidos
   - Conteo de nidos de golondrina
   - Conteo de otros nidos
   - Número de usuarios activos
   - Lista detallada de nidos por usuario (ordenada por cantidad)

#### c) **Reportes** - Moderación
   - Muestra solo nidos con reportes (reports_count > 0)
   - Ordena por cantidad de reportes (descendente)
   - Muestra foto del nido
   - Botón para eliminar nido directamente

### 3. **Sistema de reportes en usuarios**
   - Cada nido tiene un botón "Reportar" en su popup
   - Los usuarios pueden reportar nidos inapropiados
   - Los reportes se cuentan en `reports_count`
   - Los admin pueden ver y actuar sobre nidos reportados

---

## Cómo usar:

1. **Para abrir el panel admin:**
   - Haz clic en el botón "⚙️ Admin" en la esquina inferior derecha
   - O presiona `Ctrl + Shift + A`

2. **Para ver nidos:**
   - Ve a la pestaña "Nidos"
   - Aquí puedes ver todos los nidos y eliminar cualquiera

3. **Para ver estadísticas:**
   - Ve a la pestaña "Estadísticas"
   - Verás gráficas simples y resumen de datos

4. **Para moderar nidos reportados:**
   - Ve a la pestaña "Reportes"
   - Verás solo nidos que han sido reportados
   - Puedes eliminarlos directamente

---

## Notas de seguridad:

⚠️ **Importante**: Actualmente el panel admin no tiene protección por contraseña. 
Esto significa que cualquiera puede acceder al panel si abre el navegador.

### Opciones futuras de seguridad:
1. Agregar contraseña simple
2. Usar autenticación con Supabase Auth
3. Crear tabla de "admins" con usuarios autorizados
4. Usar tokens JWT para validar admin

---

## Archivos modificados:
- `index.html` - Agregados estilos CSS y funciones JavaScript para el panel
