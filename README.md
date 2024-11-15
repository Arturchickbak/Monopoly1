# Monopoly1
Программа состоит из следующих основных классов:

Box - представляет коробку, содержащую свойства, такие как размеры (Width, Height, Depth), срок годности (ExpirationDate) и другие. Pallet - представляет паллету, на которой могут находиться коробки. Этот класс содержит свойства для хранения коробок и расчетные свойства, такие как Weight и Volume. WarehouseService - сервисный класс, который управляет логикой взаимодействия с базой данных, загрузкой данных в объекты Box и Pallet, а также выполняет группировку и сортировку паллет по указанным критериям. Program - основной класс программы, который вызывает методы WarehouseService для выполнения логики и вывода данных в консоль.

Класс Box Класс Box описывает коробку и ее свойства: Размеры: ширина, высота и глубина. Срок годности (ExpirationDate) и дата производства (ProductionDate). Если указана только дата производства, срок годности вычисляется автоматически как дата производства плюс 100 дней. Объем (Volume) - вычисляется как произведение ширины, высоты и глубины коробки.

Класс Pallet Класс Pallet описывает паллету, которая может содержать несколько коробок. Основные свойства и методы: Список коробок (Boxes), которые находятся на паллете. Срок годности паллеты (ExpirationDate) - определяется минимальным сроком годности среди всех коробок на паллете. Если хотя бы одна коробка на паллете имеет срок годности, то срок годности паллеты равен самому ближайшему сроку годности среди коробок. Вес паллеты (Weight) - сумма весов всех коробок на паллете, вес коробки равен ее объему. Объем паллеты (Volume) - сумма объемов всех коробок плюс объем самой паллеты.

Класс WarehouseService Этот класс выполняет основную работу с базой данных и обрабатывает данные, чтобы предоставить информацию для отображения: LoadBoxesForPallets: Этот метод загружает коробки из базы данных и связывает их с соответствующими паллетами на основе идентификатора PalletId. GetPalletsGroupedByExpirationAndWeight: Этот метод выполняет группировку паллет по сроку годности и сортирует паллеты внутри каждой группы по весу. Он использует метод GetPalletsGroupedByExpiration, который возвращает паллеты, отсортированные по сроку годности. GetPalletsGroupedByExpiration: Возвращает паллеты, отсортированные по возрастанию срока годности. Метод загружает паллеты из базы данных и связывает их с коробками, а затем фильтрует и сортирует паллеты по сроку годности. GetTopPalletsByBoxExpiration: Этот метод выбирает топ-3 паллеты с наибольшим сроком годности коробок, отсортированные по возрастанию объема. Сначала метод сортирует паллеты по убыванию срока годности, затем по возрастанию объема и берет первые три паллеты для отображения.
Класс Program Класс Program является точкой входа в программу и выполняет следующие действия: Создает экземпляр WarehouseService, передавая строку подключения к базе данных. Вызывает метод GetPalletsGroupedByExpirationAndWeight для получения всех паллет, сгруппированных по сроку годности и отсортированных по весу, и выводит их в консоль. Вызывает метод GetTopPalletsByBoxExpiration для получения топ-3 паллет с наибольшим сроком годности коробок, отсортированных по объему, и выводит их в консоль.

!! Скачать SQL скрипт. Изменить строку подключения в программе. Класс Program.cs 9 строка: var connectionString = @"Data Source=...;Initial Catalog=monopoly;Integrated Security=True"; !!
