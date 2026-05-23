# NutriTrack v2.0 🥗💪

**PWA de nutrición deportiva · Diseño premium · Offline-first · Chile-ready**

## Despliegue en GitHub Pages

### 1. Preparar repositorio
```bash
git init
git add .
git commit -m "feat: NutriTrack v2.0"
git remote add origin https://github.com/TU_USUARIO/nutritrack.git
git push -u origin main
```

### 2. Activar GitHub Pages
Settings → Pages → Source: **main branch** → `/` (root) → Save

Tu app estará disponible en:
`https://TU_USUARIO.github.io/nutritrack/`

---

## Instalar como PWA en iPhone

1. Abre la URL en **Safari** (no Chrome ni otro browser)
2. Toca el botón **Compartir** (ícono de caja con flecha ↑)
3. Selecciona **"Añadir a pantalla de inicio"**
4. Ponle nombre y toca **Agregar**

✅ La app funciona **completamente offline** una vez instalada.

---

## Arquitectura

```
nutritrack/
├── index.html      ← App completa (shell + lógica + datos)
├── sw.js           ← Service Worker (offline + cache)
├── manifest.json   ← PWA manifest
├── icons/          ← Iconos para PWA
│   ├── icon-192.png
│   └── icon-512.png
└── README.md
```

### Stack técnico
| Capa | Tecnología |
|------|-----------|
| UI | HTML5 + CSS3 (variables, animations) |
| Lógica | Vanilla JavaScript ES2022 |
| Almacenamiento | localStorage (JSON) |
| Fuentes | Syne (Syne display) + DM Sans (body) |
| Escaneo | BarcodeDetector API + fallback manual |
| API externa | Open Food Facts (gratis, Chile) |
| Offline | Service Worker + Cache API |

---

## API de códigos de barras

**Open Food Facts** fue elegida por:
- ✅ Gratuita y sin límite de peticiones
- ✅ Cobertura real de productos Chile (supermercados Jumbo, Lider, SMU)
- ✅ Endpoint REST simple: `world.openfoodfacts.org/api/v0/product/{barcode}.json`
- ✅ Datos de macros en formato estándar por 100g
- ✅ Funciona offline con fallback a entrada manual

Alternativas consideradas: USDA FoodData (sin Chile), Nutritionix (pago), Edamam (pago)

---

## Metas nutricionales configuradas

| Nutriente | Meta/día |
|-----------|---------|
| Calorías | 1780 kcal |
| Carbohidratos | 180 g |
| Proteínas | 130 g |
| Grasas | 60 g |
| Agua | 3.0 L |

Para cambiar las metas, edita `const GOALS` en `index.html`.

---

## Base de datos incluida

**60+ alimentos** categorizados para Chile:
- 🥩 Proteínas (10): pollo, vacuno, salmón, atún, huevos, cerdo, whey...
- 🥛 Lácteos (6): yogurt griego Colun, quesillo Soprole, leche descremada...
- 🍚 Carbohidratos (10): arroz, avena Quaker, pan hallulla, pasta Carozzi...
- 🍎 Frutas (8): plátano, manzana, palta, frutilla, melón tuna...
- 🥦 Verduras (7): brócoli, espinaca, zanahoria, choclo...
- 🫘 Legumbres (4): lentejas, porotos negros, garbanzos...
- 🌰 Snacks (7): almendras, nueces, maní, mantequilla de maní...
- 🧃 Bebidas (6): café, té verde, jugo natural, bebida light...
- 🫒 Grasas (3): aceite de oliva, palta, mantequilla Soprole

---

## Roadmap futuro

- [ ] Sincronización con iCloud / Google Drive
- [ ] Gráficos de tendencias semanales (Chart.js)
- [ ] Notificaciones push de recordatorio
- [ ] Escáner mejorado con ZXing-js (mayor compatibilidad)
- [ ] Recetas y platos compuestos
- [ ] Integración con Apple Health / Google Fit
- [ ] Backend con Supabase para sync multi-dispositivo
