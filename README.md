#Heroes of might and magic
The goal of this project is to create a simplified console version of the combat mode of the famous Heroes Of Might and Magic. The full list of requirements is as follows:

#Описание:

Целта е да направим опростена версия на частта от HOM включваща битките. Основните компоненти тук ще бъдат: играчите, различните видове единици и менюто на играта. В играта ще има двама играчи всеки ще изпълнява ходовете си последователно като играта приключва когато армията на някой играч бъде избита.

#Менюта:

Когато се стартира играта се случват следните неща:
Първия играч трябва да въведе името си
От файл се зарежда информацията за първия играч
Втория играч трябва да въведе името си
От файл се зарежда информацията за втория играч
Първият играч трябва да избере расата с която ще играе
Вторият играч трябва да избере расата с която ще играе
Първият играч си купува единици
Вторият играч си купува единици
Първият играч си избира какъв тип е героят му
Вторият играч си избира какъв тип е героят му
За всяка стъпка да се извеждат адекватни съобщения обясняващи какво трябва да направи играчът. Когато играч си купува чудовища златото му се отнема моментно, само в рамките на тази игра.

##Армия:

В армията си играчите могат да имат различни чудовища. Като всички чудовища от един тип са на едно и също поле, движат се заедно и атакуват заедно. Всички чудовища могат да атакуват и да се движат по картата. Раси и единици: Имаме 2 раси Heaven, Inferno. Всяка от тях има по 3 типа единици всеки от който може да се upgrade-ва. Всички единици си имат обхват (на атаката), жизнени точки, броня, атакуващи точки и stamina (колко полета от картата могат да изминат за един ход)

###Heaven

Peasent може да нанася щета на една група чудовища на разстояние едно поле по стена или ръб от него. Upgrade – Brute когато атакува чудовище нанася щета на всички съседни на атакуваното (по стена или ръб) равна на 25% от нанесената на атакуваното.
Archer може да атакува от разстояние. Upgrade – Crossbowman избира се поле и се атакуват всички единици на него и на съседните му (по поле или по ръб)
Angel ако бъдат убити чудовища от тази група на случаен принцип се избира колко от тях се възраждат. Archnagel – ако бъдат убити чудовища от тази група на случаен принцип се избира колко от тях се възраждат и след като атакува чудовище нанася щета на всички зад него равна на 50% от нанесената.

###Inferno

Imp – може да нанася щета на една група чудовища на разстояние едно поле по стена или ръб от него. Upgrade – Vermin когато атакува чудовище в следващите 2 хода то получава щета равна на 25% от първоначалната.
Horned demon – нанася щета от разстояние. Upgrade – Horned Grunt – нанася щета от разстояние и има 50% шанс да удари 2 пъти.
Devil – нанася щета само на съседни противници, когато умре нанася щета на всички съседни противници. Upgrade – Arch Demon запазва способностите на Devil, но при движение може да си размени местата с някое чудовище.

##Герои Героите са два класа Mage и Warrior. Те имат и допълнителни полета: mana, crit,experience, nextLvlExperience, level и могат да правят различни магии.

Mana – маната която има има героя. Всяка магия изисква определено количество. На всеки ход се възстановят по 10%.
crit – допълнителна щета в % от базовата на героя
Еxperience – текущ опит на героя
nextLvlExperience – колко опит е нужен на героя, за да качи ниво
level – ниво на героя

###Мage Атакува от разстояние и може даправи следните магии.

Fire Ball – нанася щета на даден противник
Ice ball – замразява противник и той не може да се движи един ход, но може да атакува

###Warrior

Атакува от разстояние едно поле и може да прави следните магии:
Stun – атакува чудовище и то не може да се движи или атакува един ход
Shield – дава щит на чудовище и то не може да бъде атакувано
След края на битката победителя печели 500 злато загубилия 200. Героите получават опит равен на броя на убитите противникови чудовища. Ако герой вдигне ниво може да избере дали да качи точка на crit или на mana. Всяка точка на crit увеличава бонус щетата с 0.05, всяка точка вдига mana-та с 10 (примерно). И NextLvlExperience се умножава по 1.5.

##Файлове За всеки играч трябва да има един файл с името на играча. Във файла се пазят златото на героя, нивото на героя, текущия му опит, опита нужен за следващо ниво, точките mana и точките crit, в какъвто си формат Ви е най – удобно.

##Команди Купуването, придвижването и атакуването ще се извършват чрез командите описани долу:

Buy (amount) (creature) където amount е количеството на чудовищата от тип creature, които искате да закупите, ако златото на играча не достига да се изведе съобщение. 

Пример: Buy 10 Peasent
Move (fromX) (fromY) To (toX) (toY) придвижва чудовище. На от позиция (fromX,fromY) на позиция (toX,toY). Ако входа е невалиден да се изведе съобщение и да се даде възможност на играча да повтори хода си. Входа е невалиден ако няма такива полета, ако няма чудовище на играча на позиция (fromX,fromY), ако на позиция (toX,toY) има чудовище (изключение прави ArchDeamon, който в този случай си разменя мястото със съответното чудовище), или ако (toX,toY) е извън обхвата на чудовището (не му достига stamina, за да стигне до там). Придвижва се цялата група чудовища.

Пример: Move 2 4 To 4 6
Attack (fromX) (fromY) At (atX) (atY) кара чудовището на позиция (fromX,fromY) да атакува чудовището на позиция (toX,toY). При невалиден вход да се изведе съобщение за грешка и да се даде възможност на играча да повтори хода си. Входа е невалиден ако няма чудовища на входните позиции, ако на (fromX,fromY) има противниково чудовище, (toX,toY) има чудовище, но не е противниково. Или ако (toX,toY) е извън обхвата на чудовището. Атакуването става групово. Събират се точките щета на атакуващата група от тях се вади сбора на точките защита на нападната група, ако числото е отрицателно атакуващата група губи толкова жизнени точки колкото е разликата и се преизчислява числеността на групата. Ако е по – голямо от нула от общите жизнени точки на нападнатата група се вади разликата и се преизчислява броя на групата.

Пример:Attack 2 3 At 4 3
Cast (spell) At (atX) (atY) кара геройят да направи магията spell. При невалиден вход да се изведе съобщение и да се даде възможност на играча да направи ход отново. 

Пример: Cast Fireball At 3 4
За цените на чудовищата, жизнените точки, защитата, обхвата на удряне и предвижване си измислете някакви числа те не са от голяма важност.
