<p align="center">
  <a href="https://github.com/Dathinel/rodaje"><img src="https://raw.githubusercontent.com/Dathinel/rodaje/main/assets/marca/rodaje.svg" alt="Logotipo de Rodaje" width="104"></a>
</p>

<h1 align="center">modulo-voz</h1>

<p align="center">
  Módulo de IA opcional para <a href="https://github.com/Dathinel/rodaje">Rodaje</a>: convierte texto en voz con Kokoro-82M en la CPU: español, portugués de Brasil e inglés, con 34 voces. Todo corre en tu equipo, sin conexión.
</p>

<p align="center">
  <a href="#licencia"><img src="https://img.shields.io/badge/c%C3%B3digo-GPLv3-E8833A?style=flat-square&labelColor=1D1D1D" alt="Código GPLv3"></a>
  <a href="https://github.com/Dathinel/modulo-voz/releases/latest"><img src="https://img.shields.io/github/v/release/Dathinel/modulo-voz?style=flat-square&labelColor=1D1D1D&color=E8833A&label=versi%C3%B3n" alt="Última versión"></a>
  <img src="https://img.shields.io/badge/formato-.paquete-E8833A?style=flat-square&labelColor=1D1D1D" alt="Formato .paquete">
  <a href="https://github.com/Dathinel/rodaje"><img src="https://img.shields.io/badge/para-Rodaje-E8833A?style=flat-square&labelColor=1D1D1D" alt="Para Rodaje"></a>
</p>

| Función | Qué hace |
|---|---|
| `voces` | Idiomas y voces instaladas |
| `voz` | Convertir texto en voz |
| `entregar` | Copiar un audio ya generado |

Corre en: CPU. Motor: ONNX Runtime 1.30.0 (MIT). Rodaje lo abre como un proceso aparte y le habla por una tubería con nombre ([protocolo de módulos](https://github.com/Dathinel/rodaje/blob/main/docs/protocolo-modulos.md)); lo que devuelve es una propuesta que se aplica como un paso del historial (Ctrl+Z la deshace).

## Modelos (198 MB)

El `.paquete` no trae los modelos: Rodaje los baja después de instalar el módulo, comprueba su SHA-256 y los deja en `modelos\` dentro de la carpeta del módulo. Si la descarga se corta, sigue desde donde quedó.

| Id | Tamaño | Licencia | De dónde sale |
|---|---|---|---|
| `kokoro-82m-v1.0-uint8` | 169 MB | Apache-2.0 | Hugging Face `onnx-community/Kokoro-82M-v1.0-ONNX` @ `1939ad2a` |
| `misaki-us-gold` | 3 MB | Apache-2.0 | esta release |
| `misaki-us-silver` | 3 MB | Apache-2.0 | esta release |
| `misaki-gb-gold` | 3 MB | Apache-2.0 | esta release |
| `misaki-gb-silver` | 3 MB | Apache-2.0 | esta release |
| 34 voces `kokoro-voz-*` | 34 × 510 KB | Apache-2.0 | Hugging Face `onnx-community/Kokoro-82M-v1.0-ONNX` @ `1939ad2a` |

## Instalar en Rodaje

En Rodaje, Complementos → Instalar lo baja, comprueba la firma del catálogo y el hash, lo instala y baja sus modelos. A mano: descarga `modulo-voz-1.0.0.paquete` de las [releases](https://github.com/Dathinel/modulo-voz/releases) y usa «Instalar desde archivo…» en Complementos; después, «Bajar modelos».

## Código

El código fuente está en el repositorio de Rodaje, en [`modules/Rodaje.Module.Voice`](https://github.com/Dathinel/rodaje/tree/main/modules/Rodaje.Module.Voice), junto con la biblioteca del protocolo ([`src/Rodaje.Modules.Protocol`](https://github.com/Dathinel/rodaje/tree/main/src/Rodaje.Modules.Protocol)). Cada release adjunta además el código exacto con el que se compiló (`codigo-fuente-*.zip`). Se arma con:

```
powershell -NoProfile -ExecutionPolicy Bypass -File build\empaquetar-modulo.ps1 -Modulo modulo-voz
```

| Archivo | Qué es |
|---|---|
| `paquete.json` | El manifiesto del módulo: funciones, VRAM y cada modelo con su URL, tamaño y SHA-256 |
| `LICENCIAS.md` | Licencias de las bibliotecas y los modelos |
| `licencias/` | Textos de licencia de los modelos que se publican en esta release |
| `LICENSE` | GPLv3 con los términos adicionales de Rodaje |

## Licencia

El código es GPL-3.0-only con los términos adicionales de Rodaje (atribución y permiso para complementos), ver `LICENSE`. Los modelos y las bibliotecas conservan la suya: ver `LICENCIAS.md` y `licencias/`, que también viajan dentro del `.paquete`. El logotipo de Rodaje es marca de su autor ([TRADEMARK.md](https://github.com/Dathinel/rodaje/blob/main/TRADEMARK.md)).
