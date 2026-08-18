# Funora

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

| Repository | What it is | Status |
|---|---|---|
| [Funora-spec](https://github.com/Funora-Develop/Funora-spec) | Canonical models, events, errors, capabilities | in design |
| [Funora-codegen](https://github.com/Funora-Develop/Funora-codegen) | Generates models, enums and error codes from the spec | in design |
| [Funora-conformance](https://github.com/Funora-Develop/Funora-conformance) | Language-independent test vectors | in design |
| [Funora-python](https://github.com/Funora-Develop/Funora-python) | Python SDK - reference implementation | in design |
| [Funora-javascript](https://github.com/Funora-Develop/Funora-javascript) | TypeScript source, JavaScript + type declarations | planned |
| [Funora-java](https://github.com/Funora-Develop/Funora-java) | Java SDK | planned |
| [Funora-dotnet](https://github.com/Funora-Develop/Funora-dotnet) | .NET SDK | planned |
| [Funora-cpp](https://github.com/Funora-Develop/Funora-cpp) | C++ SDK | planned |
| [Funora-c](https://github.com/Funora-Develop/Funora-c) | C SDK | planned |
| [Funora-docs](https://github.com/Funora-Develop/Funora-docs) | Documentation | in design |
| [Funora-examples](https://github.com/Funora-Develop/Funora-examples) | End-to-end examples | planned |

## Before you use this

Automated access to a marketplace you do not own carries real risk. The account that can be
suspended is **yours**, and the money in it is yours. Read this part.

### What the published rules actually say

We quote FunPay's own rules so you can verify every claim yourself rather than take ours.

Source: **[funpay.com/trade/info](https://funpay.com/trade/info)** (RU) ·
**[funpay.com/en/trade/info](https://funpay.com/en/trade/info)** (EN)

- **1.9** - *"Advertising, spamming, mass mailing to users."* Sanction: temporary or
  permanent suspension of the account. This is why Funora deliberately has no
  `broadcast_to_all_buyers()` and never will.
- **2.2.9** - *"Продажа товаров и услуг, связанных со спамом и массовой рассылкой сообщений."*
  (Selling goods and services related to spam and mass messaging.)
- **2.1.8** - *"The 'Automatic delivery' function must not be used for products that require
  communication or additional services."* If you build auto-delivery on Funora, this limit is
  yours to respect - the framework cannot know what your product requires.
- **3.4.3** - *"Account suspension due to poor-quality services (for example, due to the
  seller using bots or other software prohibited by the game publisher)."* Note what this
  clause is actually about: software prohibited **by the game publisher**, not automation of
  FunPay itself.

**We did not find any published clause that either permits or forbids automating FunPay
itself.** We are not going to claim otherwise in either direction. Part of FunPay's
documentation is only reachable by signed-in users, and we have not reviewed it. Read the
rules and the agreement that apply to your own account and decide for yourself.

### What this means in practice

- Using this software may lead to your account being suspended and your funds frozen. That
  risk is yours, and no disclaimer moves it elsewhere.
- Funora does not implement, and will not accept contributions implementing, CAPTCHA
  bypass, anti-detection, proxy rotation for evasion, or any circumvention of rate limits.
- Your session key is your whole account. Treat it accordingly - see
  [SECURITY.md](https://github.com/Funora-Develop/.github/blob/main/SECURITY.md).

## License

Apache-2.0. See [LICENSE](https://github.com/Funora-Develop/Funora/blob/main/LICENSE).

---

# Funora - по-русски

**Неофициальный мульти-языковой framework для площадки FunPay, разрабатываемый сообществом.**

Проект **не аффилирован с FunPay**, не одобрен ею и никак с ней не связан. Он работает с
приватным веб-интерфейсом, который может измениться в любой момент без предупреждения.

> ### Статус: проектирование
> Ни один SDK не выпущен. Имена в реестрах заняты, чтобы их не забрал кто-то другой, но
> устанавливать пока нечего. Сначала спецификация и эталонная реализация на Python,
> остальные языки - после стабилизации контракта.

### Прежде чем пользоваться

Автоматизация чужой площадки несёт реальный риск. Заблокировать могут **ваш** аккаунт, и
деньги в нём - ваши.

Правила: **[funpay.com/trade/info](https://funpay.com/trade/info)**

- **1.9** - «Реклама, спам, массовая рассылка пользователям.» Санкция: временная или
  постоянная блокировка аккаунта. Поэтому в Funora нет и не будет массовых рассылок.
- **2.2.9** - «Продажа товаров и услуг, связанных со спамом и массовой рассылкой сообщений.»
- **2.1.8** - «Функцию "Автоматическая выдача" запрещается использовать для товаров, при
  продаже которых требуется общение или предоставление дополнительных услуг.» Если строите
  автовыдачу на Funora - соблюдение этого ограничения на вас: framework не знает, что
  требует ваш товар.
- **3.4.3** - «Блокировка аккаунта из-за некачественно оказываемой услуги (например, из-за
  использования продавцом бота или другого запрещённого издателем игры ПО).» Обратите
  внимание, о чём пункт: о ПО, запрещённом **издателем игры**, а не об автоматизации FunPay.

**Пункта, который прямо разрешал или прямо запрещал бы автоматизацию самой FunPay, в
опубликованных правилах мы не нашли.** Утверждать обратное - ни в ту, ни в другую сторону -
не будем. Часть документов площадки доступна только авторизованным пользователям, и мы их не
видели. Читайте правила и соглашение, применимые к вашему аккаунту.

Использование может привести к блокировке аккаунта и заморозке средств. Этот риск несёте вы.
В случае расхождения версий английский текст является основным.
