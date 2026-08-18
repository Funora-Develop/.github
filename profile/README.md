# Funora

**Неофициальный мульти-языковой framework для площадки FunPay, разрабатываемый сообществом.**

Проект **не аффилирован с FunPay**, не одобрен ею, не спонсируется и никак с ней не связан.
Он работает с приватным веб-интерфейсом, который может измениться в любой момент без
предупреждения.

> ### Статус: проектирование
> Ни один SDK не выпущен. Имена в реестрах заняты, чтобы их не забрал кто-то другой, но
> устанавливать пока нечего. Сначала спецификация и эталонная реализация на Python,
> остальные языки - после стабилизации контракта.

## Замысел

Один контракт, один набор тестовых векторов, нативный SDK на каждый язык. Меняется язык,
но не ментальная модель: `Client`, сервисы, события, роутер, фильтры, middleware и
таксономия ошибок означают одно и то же везде.

| Репозиторий | Что это | Статус |
|---|---|---|
| [Funora-spec](https://github.com/Funora-Develop/Funora-spec) | Канонический контракт: модели, события, ошибки, возможности | в разработке |
| [Funora-codegen](https://github.com/Funora-Develop/Funora-codegen) | Генерирует модели, перечисления и коды ошибок из спецификации | проектируется |
| [Funora-conformance](https://github.com/Funora-Develop/Funora-conformance) | Языконезависимые тестовые векторы | проектируется |
| [Funora-python](https://github.com/Funora-Develop/Funora-python) | Python SDK - эталонная реализация | в разработке |
| [Funora-javascript](https://github.com/Funora-Develop/Funora-javascript) | Исходник на TypeScript, на выходе JavaScript и типы | запланирован |
| [Funora-java](https://github.com/Funora-Develop/Funora-java) | Java SDK | запланирован |
| [Funora-dotnet](https://github.com/Funora-Develop/Funora-dotnet) | .NET SDK | запланирован |
| [Funora-cpp](https://github.com/Funora-Develop/Funora-cpp) | C++ SDK | запланирован |
| [Funora-c](https://github.com/Funora-Develop/Funora-c) | C SDK | запланирован |
| [Funora-docs](https://github.com/Funora-Develop/Funora-docs) | Документация | проектируется |
| [Funora-examples](https://github.com/Funora-Develop/Funora-examples) | Сквозные примеры | запланирован |

## Прежде чем пользоваться

Автоматизация чужой площадки несёт реальный риск. Заблокировать могут **ваш** аккаунт, и
деньги в нём тоже ваши. Этот раздел стоит прочитать.

### Что на самом деле сказано в опубликованных правилах

Цитируем правила FunPay, чтобы вы могли проверить каждое утверждение, а не верить нам на
слово.

Источник: **[funpay.com/trade/info](https://funpay.com/trade/info)** ·
**[funpay.com/en/trade/info](https://funpay.com/en/trade/info)**

- **1.9** - «Реклама, спам, массовая рассылка пользователям.» Санкция: временная или
  постоянная блокировка аккаунта. Поэтому в Funora нет метода массовой рассылки и не будет.
- **2.2.9** - «Продажа товаров и услуг, связанных со спамом и массовой рассылкой сообщений.»
- **2.1.8** - «Функцию "Автоматическая выдача" запрещается использовать для товаров, при
  продаже которых требуется общение или предоставление дополнительных услуг.» Если строите
  автовыдачу на Funora, соблюдение этого ограничения на вас: framework не знает, что
  требует ваш товар.
- **3.4.3** - «Блокировка аккаунта из-за некачественно оказываемой услуги (например, из-за
  использования продавцом бота или другого запрещённого издателем игры ПО).» Обратите
  внимание, о чём пункт: о ПО, запрещённом **издателем игры**, а не об автоматизации самой
  FunPay.

**Пункта, который прямо разрешал или прямо запрещал бы автоматизацию самой FunPay, в
опубликованных правилах мы не нашли.** Утверждать обратное - ни в ту, ни в другую сторону -
не будем. Часть документации площадки доступна только авторизованным пользователям, и мы её
не просматривали. Прочитайте правила и соглашение, применимые к вашему аккаунту, и решите
сами.

### Что это значит на практике

- Использование может привести к блокировке аккаунта и заморозке средств. Этот риск ваш, и
  никакой отказ от ответственности не переносит его на кого-то другого.
- Funora не реализует и не примет в качестве вклада обход CAPTCHA, антидетект, ротацию
  прокси для обхода ограничений и любое обход rate limit.
- Сессионный ключ - это доступ ко всему вашему аккаунту. См.
  [SECURITY.md](https://github.com/Funora-Develop/.github/blob/main/SECURITY.md).

## Лицензия

Apache-2.0. См. [LICENSE](https://github.com/Funora-Develop/Funora/blob/main/LICENSE).

---

# Funora - in English

**An unofficial, community-built multi-language framework for the FunPay marketplace.**

Funora is **not affiliated with, endorsed by, sponsored by, or connected to FunPay** in any
way. It works against a private web interface that can change at any time without notice.

> ### Status: design
> No SDK has been released yet. Package names are reserved so they cannot be taken by
> someone else, but there is nothing to install. The specification and a Python reference
> implementation come first; the other languages follow once the contract is stable.

## The idea

One contract, one set of test vectors, native SDKs per language. You change the language,
not the mental model: `Client`, services, events, router, filters, middleware and the error
taxonomy mean the same thing everywhere.

The repository list above links to every component; descriptions are in Russian, which is
the project's primary language.

## Before you use this

Automated access to a marketplace you do not own carries real risk. The account that can be
suspended is **yours**, and the money in it is yours.

We quote FunPay's own published rules so you can verify every claim rather than take ours.
Source: **[funpay.com/en/trade/info](https://funpay.com/en/trade/info)**

- **1.9** - *"Advertising, spamming, mass mailing to users."* Sanction: temporary or
  permanent suspension. This is why Funora has no broadcast feature and will not accept one.
- **2.1.8** - *"The 'Automatic delivery' function must not be used for products that require
  communication or additional services."* If you build auto-delivery on Funora, respecting
  this limit is your responsibility.
- **3.4.3** - *"Account suspension due to poor-quality services (for example, due to the
  seller using bots or other software prohibited by the game publisher)."* Note what this
  clause is actually about: software prohibited **by the game publisher**, not automation of
  FunPay itself.

**We did not find any published clause that either permits or forbids automating FunPay
itself**, and we will not claim otherwise in either direction. Part of FunPay's
documentation is only reachable by signed-in users and we have not reviewed it. Read the
rules and the agreement that apply to your own account.

Funora does not implement, and will not accept contributions implementing, CAPTCHA bypass,
anti-detection, proxy rotation for evasion, or any circumvention of rate limits.

## License

Apache-2.0.
