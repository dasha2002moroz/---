## **КАК ЗАПУСТИТЬ КОД?**

1. npm i (npm install)
2. npm start

## **ОСНОВНЫЕ ЗАДАЧИ**

1. Развернуть React-приложение с использованием **create-react-app**.
2. Следуя правилам компонентного подхода, разбить Канбан-доску на смысловые блоки, сверстать интерфейс.
3. Реализовать функционал, описанный ниже (см. раздел Функциональные требования ↓).

## МАКЕТ FIGMA

https://www.figma.com/file/gmwg0Me1T6szwVqd7KSYL6/Kanban?type=design&node-id=0-1&mode=design&t=mJA4zoU3SWW8olOd-0

## **ФУНКЦИОНАЛЬНЫЕ ТРЕБОВАНИЯ**

### **Исходное состояние**

Исходная Канбан-доска должна иметь 4 блока с задачами:

- **Backlog** (задачи, которые требуют уточнения перед тем, как брать их в работу);
- **Ready** (задачи, которые могут быть взяты в работу);
- **In progress** (задачи, которые уже в работе);
- **Finished** (законченные задачи).

## **ДОЛЖЕН БЫТЬ РЕАЛИЗОВАН СЛЕДУЮЩИЙ ФУНКЦИОНАЛ:**

### **1. Добавление новой задачи**

Первоначально каждая задача всегда размещается в бэклоге — для анализа. При клике на кнопку *+ Add card* в карточке *Backlog* должно появляться поле ввода в конце списка, между последней задачей и кнопкой. При этом кнопка *+ Add card* должна меняться на *Submit.*

**Алгоритм добавления задачи:**

Нажали кнопку *+ Add card* → появилось поле для редактирования → ввели название → нажали кнопку *Submit* — задача появилась в бэклоге (при условии, что название введено).

Нельзя добавить в список задачу с отсутствующим названием. Если при нажатии *Submit* поле с названием пустое, в список ничего не добавляется.

### **2. Перемещение задач между списками**

Задачи для списка *Ready* берутся из *Backlog.* При клике на *+ Add card* в карточке *Ready,* в конце списка появляется дропдаун с задачами из списка *Backlog.* После клика на задачу из дропдауна она должна появиться в списке *Ready* последней, при этом эта задача должна быть удалена из *Backlog.*

Если *Backlog* пустой (в списке нет задач), то кнопка *+ Add card* в списке *Ready* должна быть неактивна, то есть при клике на неё ничего не происходит. Неактивной кнопке нужно назначить атрибут `disabled`. Активная и неактивная кнопки должны отличаться визуально: например, цветом и отсутствием `cursor: pointer`.

Остальные списки (*In progress* и *Finished*) работают по тому же принципу. Задачи для списка *In progress* берутся из *Ready,* а задачи для списка *Finished* — из *In progress.*

### **3. Сохранение внесённых изменений**

Любые изменения, внесенные в приложение (добавление новых задач, перемещение задач между списками, изменение описания задачи), должны сохраняться в **localStorage.**

При загрузке приложения должны отображаться задачи, записанные в *localStorage* (или пустые списки, если в *localStorage* ничего нет). Если внести изменения и обновить страницу, то изменения должны сохраниться.

### **4. Детальная страница задачи**

Добавьте возможность перехода на отдельную страницу какой-либо задачи в списке при клике на её заголовок.

Страница с задачей должна иметь URL, отличный от того, который используется для главной страницы. URL должен содержать id задачи. Пример: `localhost:3000/tasks/12345` откроет страницу задачи с `id 12345`.

О том, как именно реализовать такой переход, написано подробнее в разделе «Требования к React».

На детальной странице задачи должны быть выведены название задачи и её описание. Если описания нет, вывести вместо него фразу `"This task has no description"`.

Поле с описанием должно быть редактируемым. Реализовать эту функцию можете как угодно. Например, добавить возможность редактирования при клике на текст или сделать специальную кнопку, которая позволит отредактировать описание.

При клике на крестик в правом верхнем углу осуществляется переход обратно на главную страницу.

### **5. Вывод количества задач в футер**

В футере должно быть выведено количество активных и завершенных задач.

- **Active tasks** — отображает количество задач в списке *Backlog.*
- **Finished tasks** — отображает количество задач в списке *Finished.*

### **6. Выпадающее меню пользователя**

Реализуйте выпадающий список, который будет появляться при клике на блок в правом верхнем углу страницы — аватар пользователя со стрелкой.

Стрелочка рядом с аватаром должна смотреть вверх, когда меню открыто, и вниз, когда меню закрыто.

При клике на пункты меню ничего не происходит, но нужно добавить выделение пунктов при наведении курсора (например, поменять цвет текста или добавить подчеркивание).

## **ТРЕБОВАНИЯ К REACT**

1. Интерфейс должен быть поделён на компоненты. Перед началом работы хорошенько обдумайте, какие компоненты вы будете использовать. Деление на компоненты должно быть логичным и оправданным.
2. После того как определитесь с делением на компоненты, подумайте о том, как верно организовать файловую структуру.
3. Следуйте принципам модульности (используйте *export, import*).
4. Используйте *Typescript* для описания типов данных.
5. Используйте [Synthetic events](https://ru.reactjs.org/docs/handling-events.html) для работы с событиями.
6. Для вывода разного состояния элементов в зависимости от действий пользователя (пример: раскрытое/свернутое меню пользователя) используйте [условный рендеринг](https://learn-reactjs.ru/basics/conditional-rendering).
7. Для реализации отдельных страниц для каждой задачи и перехода между страницами используйте библиотеку [react-router](https://habr.com/ru/post/329996/).
8. Для ключевых *React*компонентов необходимо добавить тесты.
9. При написании кода старайтесь следовать принципам **KISS** (Keep It Short and Simple — не усложняй) и **DRY** (Don’t Repeat Yourself — не повторяйся).

## **ТРЕБОВАНИЯ К ВЁРСТКЕ И CSS**

1. Вёрстка должна соответствовать макету. Добиваться *Pixel Perfect* соответствия не обязательно, но основные моменты должны быть соблюдены: цветовая гамма, шрифты, размеры, отступы.
2. Приложение должно корректно отображаться и на мобильных устройствах. Дизайн для мобильной версии вы можете найти в макете.
3. Соблюдайте семантическую вёрстку. В приложении должны присутствовать разделы `<header>`, `<main>` и `<footer>`. Кнопки должна быть реализованы элементом `<button>`, элементы дропдауна — списком `<select>` и так далее.
4. При наведении курсора на любые кликабельные элементы должен появляться `cursor: pointer`.
5. Учитывайте состояния кнопки *+ Add card* — активная и неактивная.
    - Если кнопка **активна,** её внешний вид должен соответствовать макету. При наведении она должна подсвечиваться (менять цвет), а курсор должен меняться на `pointer`.
    - Если кнопка **неактивна** (назначен атрибут `disabled`), её цвет должен отличаться от активного состояния, кнопка не должна реагировать на наведение курсора (цвет остаётся таким же, не появляется курсор `pointer`).
6. Можете использовать любой вариант подключения стилей на ваше усмотрение: общий файл стилей проекта, CSS-модули или специальные React-библиотеки для стилизации компонентов (например, [Styled Components](https://styled-components.com/)).
7. Использовать селекторы по тегу и `id` для задания стилей **нельзя.** Используйте классы.

## **ПРОЧИЕ ТРЕБОВАНИЯ**

1. Пишите код аккуратно, с соблюдением форматирования и отступов.
2. Старайтесь давать компонентам, переменным и функциям осмысленные имена.
3. Старайтесь использовать современный ES6 синтаксис: стрелочные функции, декомпозицию, *spread* и т.д.
4. При размещении проекта на GitHub не забывайте добавить папку *node_modules* в файл *.gitignore,* чтобы она не попала в ваш репозиторий. О том, как настроить *.gitignore* и почему папки *node_modules* не должно быть в репозитории, можете прочитать [в этой статье](https://cpab.ru/chto-takoe-fajl-gitignore-i-kak-ego-nastroit-cloudsavvy-it/).