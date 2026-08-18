# Security Policy

*The English text is authoritative. Русская версия — ниже.*

## Never put credentials in a public issue

A FunPay session key (`golden_key`, `PHPSESSID`, CSRF tokens) is **not** a scoped API token.
It is your whole account: whoever holds it can read your private chats, see your orders and
act as you.

Do not paste into a public issue, discussion, pull request or gist:

- session keys and cookies of any kind,
- raw HTML captured from a signed-in page,
- unredacted logs, tracebacks or diagnostic exports,
- private chat contents — yours or a buyer's.

GitHub's secret scanning does not know the format of a FunPay session key. Nothing will stop
you, and nothing will warn you.

## If you have already leaked a key

Assume it is compromised the moment it is submitted. Public issues are delivered to the
GitHub events API within seconds and are mirrored by third parties. Deleting the comment
does not undo this.

1. Change your FunPay account password immediately — this invalidates existing sessions.
2. Sign in again and verify no unfamiliar activity on your orders and chats.
3. Only then edit or delete the issue.

Do not open a public issue to report your own leak. Use the private channel below.

## Reporting a vulnerability

Report privately through GitHub Security Advisories:

**https://github.com/Funora-Develop/Funora/security/advisories/new**

Please include: affected repository and version, what an attacker gains, reproduction steps,
and a **redacted** diagnostic. Do not include a working session key — describe the shape of
the problem instead.

We will acknowledge within a few days. This project is currently maintained by one person,
so please allow reasonable time before public disclosure.

## What is in scope

- Leakage of session keys or private chat contents through any output channel of the
  framework: logs, exception text, `repr`/`toString`, telemetry hooks, diagnostic exports,
  fixtures, persisted state.
- A write operation that can be replayed or duplicated, causing a seller to lose goods or
  money.
- Anything that lets one account's data or credentials reach another account inside the same
  process.
- Supply-chain issues: release workflows, code generation, package publishing.

## What is not in scope

- The behaviour of FunPay itself. We do not control it and cannot fix it. Report site
  problems to FunPay.
- Requests to add CAPTCHA bypass, anti-detection, proxy rotation for evasion, or rate-limit
  circumvention. These are explicit non-goals and will be closed.
- Account suspensions resulting from how you used the software.

## Third-party plugins

An in-process plugin runs with the permissions of your process and can read your session.
This cannot be honestly sandboxed. Any plugin permission manifest the project may add later
is a declaration of intent, **not** an enforced boundary. Run only plugins you would trust
with your account.

---

# Политика безопасности

*Английский текст является основным; русский приведён для удобства.*

## Никогда не публикуйте учётные данные в открытых issue

Сессионный ключ FunPay (`golden_key`, `PHPSESSID`, CSRF-токены) — это **не** токен с
ограниченными правами. Это доступ ко всему аккаунту: кто им владеет, тот читает вашу
переписку, видит заказы и действует от вашего имени.

Не вставляйте в публичные issue, обсуждения, pull request и gist:

- сессионные ключи и любые cookie,
- сырой HTML, снятый со страницы под авторизацией,
- неотредактированные логи, трейсбеки и диагностические выгрузки,
- содержимое личной переписки — вашей или покупателя.

Secret scanning GitHub не знает формата сессионного ключа FunPay. Вас никто не остановит и
не предупредит.

## Если ключ уже утёк

Считайте его скомпрометированным с момента отправки. Публичные issue попадают в events API
GitHub за секунды и зеркалируются третьими лицами. Удаление комментария этого не отменяет.

1. Немедленно смените пароль аккаунта FunPay — это обнулит существующие сессии.
2. Войдите заново и проверьте заказы и чаты на незнакомую активность.
3. Только после этого редактируйте или удаляйте issue.

Не заводите публичный issue, чтобы сообщить о собственной утечке. Используйте приватный
канал ниже.

## Как сообщить об уязвимости

Приватно, через GitHub Security Advisories:

**https://github.com/Funora-Develop/Funora/security/advisories/new**

Укажите: репозиторий и версию, что получает атакующий, шаги воспроизведения и
**отредактированную** диагностику. Не прикладывайте рабочий сессионный ключ — опишите
характер проблемы.

Ответим в течение нескольких дней. Проект сейчас ведёт один человек, поэтому дайте разумное
время до публичного раскрытия.

## Что входит в область

- Утечка сессионных ключей или содержимого переписки через любой выходной канал framework:
  логи, текст исключений, `repr`/`toString`, telemetry-хуки, диагностические выгрузки,
  fixtures, сохранённое состояние.
- Write-операция, которую можно повторить или продублировать так, что продавец теряет товар
  или деньги.
- Всё, что позволяет данным или учётным данным одного аккаунта попасть в другой в пределах
  одного процесса.
- Цепочка поставки: release-workflow, кодогенерация, публикация пакетов.

## Что не входит

- Поведение самой FunPay. Мы его не контролируем и починить не можем.
- Просьбы добавить обход CAPTCHA, антидетект, ротацию прокси для обхода ограничений или
  обход rate limit. Это явные не-цели, такие issue закрываются.
- Блокировки аккаунта, наступившие из-за того, как вы использовали программу.

## Сторонние плагины

Плагин, работающий внутри процесса, имеет права этого процесса и может прочитать вашу
сессию. Честно изолировать его нельзя. Любой манифест разрешений, который проект добавит
позже, — это декларация намерений, **а не** принудительная граница. Запускайте только те
плагины, которым доверили бы свой аккаунт.
