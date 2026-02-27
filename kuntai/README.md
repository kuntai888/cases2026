# Kuntai Business Awake

Sitio web estático con CMS Jamstack. Powered by Decap CMS + Netlify Identity.

---

## 📁 Estructura de archivos

```
kuntai/
├── index.html                          ← Sitio público (visitantes)
├── netlify.toml                        ← Configuración de despliegue
├── admin/
│   ├── index.html                      ← Panel del editor (subir contenido)
│   └── config.yml                      ← Esquema del CMS
├── content/
│   ├── posts/
│   │   ├── index.json                  ← Índice de artículos (leído por el frontend)
│   │   └── *.md                        ← Artículos en Markdown
│   └── settings/
│       ├── social.json                 ← Redes sociales
│       ├── stats.json                  ← Estadísticas del hero
│       └── ticker.json                 ← Frases del ticker
└── public/
    └── uploads/                        ← Imágenes y audios subidos desde el CMS
```

---

## 🚀 Despliegue en Netlify

### 1. Subir a GitHub
```bash
git init
git add .
git commit -m "initial commit"
git branch -M main
git remote add origin https://github.com/TU_USUARIO/kuntai.git
git push -u origin main
```

### 2. Conectar con Netlify
1. Ir a [netlify.com](https://netlify.com) → **Add new site** → **Import from Git**
2. Seleccionar el repositorio
3. Build command: *(dejar vacío)*
4. Publish directory: `.`
5. Click **Deploy site**

### 3. Activar Netlify Identity
1. **Site settings** → **Identity** → **Enable Identity**
2. En **Registration** → seleccionar **Invite only**
3. Bajar hasta **Git Gateway** → **Enable Git Gateway**

### 4. Invitar editores
1. **Identity** → **Invite users**
2. Ingresar el correo del editor
3. El editor recibirá un email para crear su contraseña

### 5. Primer acceso al CMS
- Visitar `https://tu-sitio.netlify.app/admin/`
- Click en **Login with Netlify Identity**
- Aceptar la invitación del email

---

## ✍️ Crear un artículo

1. Entrar a `/admin/`
2. Click en **Artículos / Articles** → **New Artículo / Article**
3. Completar los campos:
   - **Slug**: URL del artículo (solo letras, números y guiones)
   - **Estado**: Borrador → Publicado
   - **Categoría**: elegir de la lista
   - **Título (ES)** y **Resumen (ES)**: obligatorios
   - **Audio / Video**: opcionales (aparecen badges en la tarjeta)
4. Click **Save** (guarda como borrador) o **Publish** (publica directo)

### Flujo editorial
```
Borrador → En revisión → Publicado
```

---

## 🔄 Actualizar index.json

Cada vez que publiques un artículo desde el CMS, **debes actualizar** el archivo `content/posts/index.json` para que aparezca en el frontend. 

Agrega un objeto al array `posts` con los campos:
```json
{
  "slug": "slug-del-articulo",
  "date": "2026-01-01",
  "status": "published",
  "category": "strategy",
  "read_time": 8,
  "author": "Kuntai",
  "title_es": "Título en español",
  "excerpt_es": "Resumen breve...",
  "title_en": "Title in English",
  "excerpt_en": "Brief summary...",
  "cover_image": "/uploads/mi-imagen.jpg",
  "audio_url": "/uploads/mi-audio.mp3",
  "youtube_url": "https://www.youtube.com/watch?v=XXXXXXXXX"
}
```

> Los campos `cover_image`, `audio_url` y `youtube_url` son opcionales. 
> Dejarlos como `""` para omitirlos.

---

## 🌐 Idiomas

El sitio soporta **Español (ES)** e **Inglés (EN)**.

- El idioma se guarda en `localStorage` entre visitas
- El toggle ES/EN está en la barra de navegación
- Cada artículo puede tener campos en ambos idiomas

---

## 🔗 Links importantes

| Descripción | URL |
|---|---|
| Sitio público | `https://tu-sitio.netlify.app/` |
| Panel CMS | `https://tu-sitio.netlify.app/admin/` |
| Grupo LinkedIn | https://www.linkedin.com/groups/17528001/ |
| LinkedIn empresa | https://www.linkedin.com/company/kuntai |
| Instagram | https://www.instagram.com/kuntai.negocios.conscientes |
| Codex | https://orgcodex.netlify.app/ |
