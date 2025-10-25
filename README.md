# 💰 Calculadora de Ahorro e Inversión

Aplicación web para registrar y calcular ahorros con interés compuesto del 11% anual.

## 📋 Características

- ✅ Registro de ahorros con nombre, fecha y monto
- 📊 Cálculo automático de interés compuesto diario
- 👥 Sistema compartido para múltiples usuarios
- 📈 Calculadora de proyecciones futuras
- 💾 Sincronización en tiempo real con Firebase

---

## 🚀 Opción 1: Desplegar en Netlify (MÁS FÁCIL)

### Paso 1: Crear proyecto en Firebase

1. Ve a [Firebase Console](https://console.firebase.google.com/)
2. Haz clic en "Agregar proyecto"
3. Dale un nombre (ej: "ahorro-familiar")
4. Desactiva Google Analytics (no es necesario)
5. Crea el proyecto

### Paso 2: Configurar Realtime Database

1. En el menú lateral, ve a **"Realtime Database"**
2. Haz clic en **"Crear base de datos"**
3. Selecciona ubicación: **"United States (us-central1)"**
4. Modo: **"Empezar en modo de prueba"** (por ahora)
5. Haz clic en **"Reglas"** y pega esto:

```json
{
  "rules": {
    "savings": {
      ".read": true,
      ".write": true
    }
  }
}
```

6. Publica las reglas

### Paso 3: Obtener configuración de Firebase

1. En Firebase Console, haz clic en el ícono de engranaje ⚙️ → **"Configuración del proyecto"**
2. Baja hasta **"Tus apps"**
3. Haz clic en el ícono **</> (Web)**
4. Dale un nombre (ej: "app-ahorro")
5. **NO marques** "Firebase Hosting"
6. Registra la app
7. Copia la configuración que se ve así:

```javascript
const firebaseConfig = {
  apiKey: "AIzaSy...",
  authDomain: "tu-proyecto.firebaseapp.com",
  databaseURL: "https://tu-proyecto-default-rtdb.firebaseio.com",
  projectId: "tu-proyecto",
  storageBucket: "tu-proyecto.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:abc123"
};
```

### Paso 4: Modificar el archivo index.html

1. Abre el archivo `index.html`
2. Busca esta sección (línea ~380):

```javascript
const firebaseConfig = {
    apiKey: "TU_API_KEY_AQUI",
    authDomain: "TU_AUTH_DOMAIN_AQUI",
    // ...
};
```

3. **Reemplaza** con los valores de tu Firebase (del paso anterior)

### Paso 5: Subir a GitHub

1. Crea una cuenta en [GitHub](https://github.com) si no tienes
2. Crea un nuevo repositorio:
   - Nombre: `ahorro-inversion`
   - Público o Privado (tu elección)
   - NO inicialices con README
3. En tu computadora, abre la terminal/CMD en la carpeta donde guardaste `index.html`
4. Ejecuta estos comandos:

```bash
git init
git add index.html
git commit -m "Aplicación de ahorro e inversión"
git branch -M main
git remote add origin https://github.com/TU_USUARIO/ahorro-inversion.git
git push -u origin main
```

### Paso 6: Desplegar en Netlify

1. Ve a [Netlify](https://www.netlify.com/) y crea una cuenta (gratis)
2. Haz clic en **"Add new site"** → **"Import an existing project"**
3. Selecciona **"GitHub"** y autoriza
4. Selecciona tu repositorio `ahorro-inversion`
5. Configuración:
   - Build command: *dejar vacío*
   - Publish directory: *dejar vacío*
6. Haz clic en **"Deploy"**
7. ¡Listo! Te dará una URL como: `https://tu-app-123.netlify.app`

### Paso 7: Personalizar dominio (OPCIONAL)

En Netlify:
1. Ve a **"Site settings"** → **"Change site name"**
2. Ponle un nombre personalizado: `ahorro-familiar-perez`
3. Tu URL será: `https://ahorro-familiar-perez.netlify.app`

---

## 🚀 Opción 2: Desplegar en Firebase Hosting

Si prefieres usar solo Firebase:

### Después del Paso 4 anterior:

```bash
# Instalar Firebase CLI
npm install -g firebase-tools

# Iniciar sesión
firebase login

# Inicializar proyecto
firebase init

# Selecciona:
# - Hosting
# - Use an existing project (selecciona el tuyo)
# - Public directory: . (punto)
# - Single-page app: No

# Desplegar
firebase deploy
```

Tu app estará en: `https://tu-proyecto.web.app`

---

## 🔒 Mejorar Seguridad (IMPORTANTE)

Una vez funcionando, mejora las reglas de Firebase:

```json
{
  "rules": {
    "savings": {
      ".read": true,
      ".write": true,
      ".validate": "newData.hasChildren(['id', 'name', 'date', 'amount'])"
    }
  }
}
```

Para seguridad avanzada, considera agregar Firebase Authentication.

---

## 📱 Uso de la aplicación

### Para ti y tu esposa:

1. Ambos abren la misma URL
2. Registran ahorros con sus nombres
3. Los cambios se sincronizan automáticamente en tiempo real
4. Los datos persisten indefinidamente

### Ejemplo:

**María registra:**
- Nombre: María
- Fecha: 15/10/2024
- Monto: $2,000

**Juan ve el ahorro de María inmediatamente** y puede agregar el suyo.

---

## ❓ Solución de Problemas

### Error: "Permission denied"
- Verifica las reglas de Firebase Realtime Database
- Asegúrate de que `.read` y `.write` estén en `true`

### No se sincronizan los datos
- Verifica que `databaseURL` esté correcto en firebaseConfig
- Abre la consola del navegador (F12) y busca errores

### Los datos no persisten
- Verifica que Firebase Realtime Database esté activo
- Revisa que la configuración de Firebase esté correcta

---

## 💡 Características Técnicas

- **Interés Compuesto:** 11% anual calculado diariamente
- **Fórmula:** `Valor = Monto × (1 + tasa_diaria)^días`
- **Sincronización:** Tiempo real con Firebase
- **Almacenamiento:** Ilimitado en plan gratuito de Firebase

---

## 📞 Soporte

Si tienes problemas:
1. Revisa la consola del navegador (F12)
2. Verifica la configuración de Firebase
3. Asegúrate de que las reglas permitan lectura/escritura

---

## 🎯 Próximas Mejoras Sugeridas

- [ ] Exportar datos a Excel
- [ ] Gráficos de crecimiento
- [ ] Notificaciones de metas alcanzadas
- [ ] Historial de cambios
- [ ] Categorías de ahorro

---

**¡Feliz ahorro! 💰**
