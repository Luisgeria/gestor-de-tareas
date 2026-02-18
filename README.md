# ⚡ TaskFlow Pro — Guía de Setup

## Credenciales por defecto

| Rol | Usuario | Contraseña |
|-----|---------|------------|
| **Admin** | `admin` | `11223344` |
| Usuario demo | `user1` | `1234` |

---

## Funcionalidades

### Para todos los usuarios
- ✅ Crear, editar y completar tareas
- 📋 Vista Kanban (Pendiente / En progreso / Completada / Cancelada)
- 📃 Vista Lista con tabla completa
- 📅 Calendario: Día / Semana / Mes / Año
- 🎤 Entrada de texto por voz (español)
- 🔥 Niveles de prioridad: Alta / Media / Baja
- ⏱ Tiempo estimado (min / horas / días)
- 🏷 Etiquetas personalizadas
- 📁 Categorías
- 🔍 Búsqueda y filtros

### Solo Admin
- 👥 Gestión de usuarios (crear, editar, eliminar)
- 👁 Ver TODAS las tareas de todos los usuarios
- 📋 Asignar tareas a usuarios específicos
- 📥 Exportar datos en JSON
- ⚙ Panel de administración completo

---

## Configurar Firebase (opcional)

Sin Firebase, los datos se guardan en `localStorage` del navegador.
Con Firebase, los datos se sincronizan en tiempo real entre dispositivos.

### Pasos

1. Ve a [console.firebase.google.com](https://console.firebase.google.com)
2. Crear proyecto → Agregar app Web
3. Copiar `firebaseConfig`
4. En `index.html`, busca el bloque `const firebaseConfig = {` y reemplaza los valores `REPLACE_...` con los tuyos
5. En Firestore, crear base de datos en **modo de prueba**

### Reglas Firestore recomendadas
```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read, write: if true; // Solo para pruebas
    }
  }
}
```

---

## Instalación PWA

- **Android / Chrome**: Menú ⋮ → "Añadir a pantalla de inicio"
- **iOS / Safari**: Compartir → "Añadir a pantalla de inicio"
- **Desktop Chrome/Edge**: Icono de instalación en la barra de URL

---

## Despliegue

### Opción A — Netlify (más fácil)
Arrastra la carpeta en [app.netlify.com/drop](https://app.netlify.com/drop)

### Opción B — Firebase Hosting
```bash
npm install -g firebase-tools
firebase login
firebase init hosting  # carpeta: . o dist
firebase deploy
```

### Opción C — Vercel
```bash
npm i -g vercel
vercel --prod
```

---

## Atajos de teclado

| Tecla | Acción |
|-------|--------|
| `N` | Nueva tarea |
| `Esc` | Cerrar modal |
| `Ctrl+F` | Buscar |
