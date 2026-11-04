# LEDERG PANZER

**LEDERG PANZER v0.2.0 — бесплатный Windows x64 набор для разрешённого аудита и локальной защиты.**

Telegram: [канал @lederg_panzer](https://t.me/lederg_panzer) · [чат @lederg_panzer_chat](https://t.me/lederg_panzer_chat)

## Основные возможности

- Новый чёрно-красный интерфейс, панель окна LEDERG PANZER, аватар и боковая навигация.
- Веб-аудит: DNS A/AAAA/MX/NS/TXT/CAA, SPF, DMARC, HTTPS, TLS-сертификат, HTTP Security Headers, CORS и cookie-флаги.
- Полный TCP connect scan одного домена/IP по диапазону **1–65535**, с ограниченной параллельностью, прогрессом и остановкой.
- OSINT: RDAP по IP/домену и пассивный поиск имён из Certificate Transparency через crt.sh.
- Поиск CVE по продукту/поставщику через публичный NVD API.
- Локальная инвентаризация Windows: сетевые интерфейсы, слушающие TCP-порты, состояние Windows Firewall и Microsoft Defender.
- Быстрая проверка штатным Microsoft Defender; добавление явного входящего правила Windows Firewall для указанного IP (нужны права администратора).
- Утилиты: SHA-256/SHA-1/MD5 файлов локально, криптографический генератор паролей, ping и traceroute.
- Локальная история SQLite; экспорт отчётов HTML/JSON.

## Сборка из исходников

Требуется Windows 10/11 x64 и Python 3.12.

```powershell
py -3.12 -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install -r requirements-dev.txt
python -m unittest discover -s tests -v
python app.py
```

Для сборки EXE:

```powershell
pyinstaller --noconfirm --clean --onefile --windowed --name LEDERG-PANZER --collect-all dns --collect-all psutil app.py
```

## Область и безопасность

- Запускайте тестирование только на системах, которыми владеете, или на цели с явным разрешением.
- Один запуск работает с одним доменом или одним IP; CIDR, wildcard, списки целей и автоматическое сканирование обнаруженных поддоменов не выполняются.
- Полный сканер выполняет TCP connect-проверки. Он не является SYN/stealth-сканером и не выполняет UDP-сканирование. Закрытый порт и порт, отфильтрованный firewall, не всегда можно отличить одним connect-методом.
- OSINT использует публичные источники; найденные записи не означают наличие уязвимости.
- Поиск CVE по ключевым словам не подтверждает уязвимость конкретной установленной версии.
- Block IP создаёт входящее правило Windows Firewall только на локальном устройстве. Требуются права администратора и подтверждение пользователя.
- Ответные атаки, DDoS, эксплуатация чужих систем, подбор паролей, скрытность, persistence и извлечение чужих данных не реализованы.
- Автоматические предупреждения требуют ручной валидации.

## Рекомендованные открытые инструменты

- [Nmap](https://nmap.org/) — сетевая инвентаризация и TCP connect scan.
- [OWASP ZAP](https://www.zaproxy.org/) — аудит веб-приложений; активные проверки применяйте только по согласованной программе.
- [Wireshark](https://www.wireshark.org/) — анализ сетевого трафика.
- [YARA](https://yara.readthedocs.io/) — поиск и классификация файлов по правилам.
- [Microsoft Sysinternals](https://learn.microsoft.com/sysinternals/) — диагностика процессов и Windows.
- [OWASP Web Security Testing Guide](https://owasp.org/www-project-web-security-testing-guide/) — методология веб-тестирования.

## Репозиторий и релизы

- Source: https://github.com/lederg001/lederg-panzer
- Releases: https://github.com/lederg001/lederg-panzer/releases
- Maintainer: [@LEDERG_ru](https://t.me/LEDERG_ru)

Лицензия MIT — см. [LICENSE](LICENSE).
