# 📦 Instrucciones de deployment - Landing Aislación Celulosa

## Estructura de archivos para GitHub

```
tu-repo/
├── index.html                           (renombrar index_mejorada_esferainfo.html)
├── 01-camper-celulosa-proyectada.png
├── 02-estudio-grabacion-acustica.png
├── 03-wood-frame-construccion.png
├── 04-container-exterior.png
├── 05-steel-frame-proyeccion.png
├── 06-oficina-ecofine-blanca.png
├── 07-operario-aplicacion.png
├── 08-techo-detalle-textura.png
└── 09-restaurante-terminado.png
```

## Pasos para subir a GitHub

### 1. Renombrar el HTML principal
```bash
mv index_mejorada_esferainfo.html index.html
```

### 2. Subir todo a la raíz del repositorio
```bash
git add index.html
git add *.png
git commit -m "Landing con EsferaInfo y galería de trabajos reales"
git push origin main
```

### 3. Configurar GitHub Pages (si usás Pages)
1. Ve a Settings → Pages
2. Source: Deploy from a branch
3. Branch: `main` / `root`
4. Save

Tu landing estará en: `https://tu-usuario.github.io/tu-repo/`

## Alternativa: Usar una carpeta `/images`

Si preferís organizarlo mejor:

```
tu-repo/
├── index.html
└── images/
    ├── 01-camper-celulosa-proyectada.png
    ├── 02-estudio-grabacion-acustica.png
    ├── 03-wood-frame-construccion.png
    ├── 04-container-exterior.png
    ├── 05-steel-frame-proyeccion.png
    ├── 06-oficina-ecofine-blanca.png
    ├── 07-operario-aplicacion.png
    ├── 08-techo-detalle-textura.png
    └── 09-restaurante-terminado.png
```

Entonces en el HTML cambiar las rutas:
```html
<img src="images/01-camper-celulosa-proyectada.png" ...>
```

## Optimización de imágenes (opcional pero recomendado)

Las imágenes actuales pesan ~1.8MB total. Para mejor performance:

```bash
# Instalar ImageMagick
brew install imagemagick  # macOS
sudo apt install imagemagick  # Linux

# Optimizar todas las imágenes
for img in *.png; do
  convert "$img" -resize 1200x1200\> -quality 85 "optimized-$img"
done
```

Esto reduce el peso total a ~600-800KB sin pérdida visible de calidad.

## SEO: Alt texts incluidos

Todas las imágenes ya tienen alt texts optimizados para SEO:
- ✅ "Aislación térmica y acústica de camper con celulosa proyectada"
- ✅ "Estudio de grabación profesional con aislación acústica de celulosa"
- ✅ "Técnico especializado aplicando celulosa proyectada con equipos profesionales"

Esto mejora el ranking en Google Images para búsquedas como:
- "aislación celulosa proyectada"
- "aislación térmica restaurante"
- "celulosa steel frame"

## Performance web

El HTML tiene:
- ✅ `loading="lazy"` en todas las imágenes (carga diferida)
- ✅ CSS inline (no hay requests adicionales)
- ✅ Sin dependencias externas (no jQuery, no Bootstrap)

**PageSpeed esperado:** 90+ en mobile, 95+ en desktop

## ¿Necesitás un dominio personalizado?

Si comprás un dominio tipo `aislacioncelulosa.com.ar`:

1. Agregá un archivo `CNAME` en la raíz con el dominio:
   ```
   aislacioncelulosa.com.ar
   ```

2. En tu proveedor de DNS (GoDaddy, Namecheap, etc):
   ```
   CNAME www 185.199.108.153
   A @ 185.199.108.153
   A @ 185.199.109.153
   A @ 185.199.110.153
   A @ 185.199.111.153
   ```

## Contacto y formularios

El HTML tiene un placeholder para formulario de Tally.so. 

Para activarlo:
1. Crear formulario en https://tally.so
2. Obtener código de embed
3. Reemplazar línea 986-1001 del HTML con el iframe de Tally

---

**¿Algún problema?** Avisame y lo resolvemos.
