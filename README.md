# Smart Proxy AI

Android-приложение: отдельный DNS для ИИ, трафик ИИ идёт напрямую мимо VPN-сервера, остальное — через VPN.

## Что здесь есть
- `tools/inject_ai_dns.py` — **проверено**: добавляет DNS и маршрут для ИИ в любой Xray JSON-профиль.
- `app/.../core/ConfigInjector.kt` — та же логика на Kotlin (не компилировалась).
- `app/.../ui/` — интерфейс на Jetpack Compose (не компилировался).
- `.github/workflows/build.yml` — сборка debug-APK на GitHub.

## Чего нет
VPN-движка (`core/Engine.kt`, пока заглушка). Нужны VpnService + Xray-ядро + tun2socks.
Эту часть надо брать из v2rayNG (GPL-3.0): сделайте Fork 2dust/v2rayNG и перенесите оттуда.

## Быстрая проверка идеи без приложения
1. Возьмите JSON-профиль из своей подписки (в v2rayNG: профиль → «Экспорт полной конфигурации»).
2. `python3 tools/inject_ai_dns.py profile.json > profile_ai.json`
3. Импортируйте результат в v2rayNG как кастомный конфиг и проверьте ИИ и YouTube одновременно.
