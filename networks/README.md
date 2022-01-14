# Запуск Celestia Devnet
> Примечание: Это руководство актуально только для текущей сети разработчиков. По мере приближения к тестнету будет новый гайд.

- [Запуск Celestia Devnet](#run-celestia-devnet)
  - [Celestia 101(обзор)](#celestia-101overview)
    - [Celestia Full Node](#celestia-full-node)
    - [Celestia Light Client](#celestia-light-client)
  - [Руководство по установке](#installation-guide)
  - [Устранение неполадок](#troubleshoot)

## Селестия 101(Обзор)
<i>Концептуально</i> у нас есть 2 основных компонента в сети: 
1. `Celestia Full Node`.
2. `Celestia Light Client`.

> Примечание: Когда вы видите отформатированный текст двух вышеприведенных («Celestia Full Node», «Celestia Light Client»), помните, что мы имеем в виду <i>концептуальный вид</i>. Стандартный форматированный текст имеет технический вид.
### Celestia Full Node
Когда мы говорим о Celestia Full Node, мы имеем в виду комбинацию из двух компонентов:

- Приложение Celestia (находится в репозитории [celestia-app](https://github.com/celestiaorg/celestia-app))
- Celestia Full Node (находится в репозитории [celestia-node](https://github.com/celestiaorg/celestia-node))

<i>Концептуально</i>, одно не может жить без другого, так как нам нужно, чтобы каждый новый блок был "erasure coded", чтобы делать выборку доступности данных из `Celestia Light Clients`.

Технически Celestia Application и Celestia Full Node работают в разных процессах <b>одной инстанции</b> (например, сервера). Давайте разберем, что делает каждая из сторон.

Celestia Application(CA) заботится о следующих моментах: 
- Consensus (Консенсус)
- State Interaction (Взаимодействие Состояний)
- Block Production (Произвдство блоков)
- Связь только между инстанциями приложения Celestia!

Celestia Full Node(CFN) заботится о следующих моментах: 
- Синхронизация блоков из приложения Celestia
- Стирание кодов блоков (Erasure Codes)
- Обслуживать headers/shares для Celestia Light Clients
- Взаимодействие Celestia Full Nodes и Celestia Light Clients

Связь процессов CA и CFN происходит через RPC.

### Celestia Light Client
Celestia Light Client(CLC) существует только в [celestia-node](https://github.com/celestiaorg/celestia-node) репозитории. Что CLC делает: 
1. Соединяется с `Celestia Full Node`.
2. Синхронизирует headers.
3. Выполняет выборку доступности данных (DAS).

> Примечание: `Celestia Light Clients` не общаются друг с другом, а общаются только между `Celestia Full Nodes`



## Инструкция по установке
> Предупреждение: убедитесь, что у вас есть не менее 50+ ГБ свободного места, чтобы безопасно продолжить работу с этой инструкцией.

Вам нужно установить celestia-app, celestia-node, чтобы двигаться дальше.
> Примечание: <b>намного проще запустить non-validator celestia app</b> + celestia full node, чем переходить туда и обратно, чтобы быть включенным в активный сэт валидаторов.
- [Celestia Application Installation](./xyz.md)
- [Celestia Node Installation](./celestia-node.md)

## Устранение неполадок
Пожалуйста, перейдите по [этой ссылке](./troubleshoot.md) что бы найти больше информации.

