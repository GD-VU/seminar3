# **Инструкция по работе с Git**

![git logo](git_logo.png)

**Git** - сисема контроля версий. Изначально *разработана в 2005 году* **Линусом Торвальдсом** - создателем ядра операционной системы *Linux*.

## Общая инструкция по Git

Далее представлены **основные команды** для Git, необходимые каждому, кто решил встать на путь программиста.

## Создание нового репозитория

Чтобы создать (инициализировать) новый репозиторий в текущей папке необходимо в терминале выполнить команду:

    git init

## Проверка состояния репозитория

Чтобы проверить состояние файлов в рабочей директории необходимо выполнить команду:

    git status

## Добавление изменений к индексу

Чтобы добавить внесенные в файл изменения с последующим созданием коммита необходимо выполнить команду:

    git add <filename>

## Фиксация изменений

Для создания коммита (фиксации изменений), к которой в дальнейшем можно будет вернуться, необходимо выполнить команду:

    git commit

**Внимание!**

*Помни про принцип атомарности коммита, который гласит: **"Один коммит - одно изменение"** , которое означает: в одном коммите не может быть сообщения о двух разных изменениях, должно быть одно сообщение на каждое изменение.*

### Дополнительные опции для Git commit

- Для создания текстовой пометки в коммите, с описанием выполненного изменения, необходимо выполнить команду:

        git commit -m "message"

    где:

    -m - непосредственно опция 'message' для Git commit.

    "message" - понятное описание изменения, задается пользователем.

- Для добавления изменений к индексу по всем файлам репозитория можно использовать команду:

        git commit -a

    где:

    -a - опция 'Add' для 'Git commit', действие которой аналогично команде 'Git add <filename>', но распространяется на все файлы в репозитории.

- Для добавления изменений к индексу по всем файлам рапозитория с одновременным добавлением коммита необходимо использовать команду:

        git commit -am "message"
    
    где:

    -a - опция 'Add' для всех файлов в репозитории

    -m - опция 'message' для создания сообщения с описанием изменений

    "message" - сообщение пользователя с описанием внесенных изменений.

## Просмотр журнала изменений

Журнал изменений представляет набор коммитов в той последовательности и с теми сообщениями, как мы их домавляли, поэтому так важно писать максимально понятные сообщения.

Для просмотра журнала изменений в репозитории необходимо выполнить команду:

    git log

### Дополнительные опции для Git log

- Для сокращения журнала в одну строчку использовать команду:

        git log --oneline
    
    где:

    --oneline - опция которая указывает, что журнал следует выводить одной строкой в виде структуры: **hash + message**

    Знак '**--**' сообщает, что это опция глобальная

- В тех случаях, когда вы находитесь в более "ранних" версиях файла и надо посмотреть журнал не только до момента на котором находитесь, но и все последующие изменения, применять команду:

        git log --all
    
    где:

    --all - опция которая позволяет просмотреть **все** изменения.

    Обратите внимание, все коммиты будут выведены, и будут иметь полную информацию. Эта опция глобальная.

- В тех случаях, когда надо показать весь журнал в максимально сжатом виде, нужно использовать команду:

        git log --all --oneline

    где:

    --all - опция, отвечающая за отображение всего журнала, вне зависимости от того, в каком месте "временной шкалы" для этого файла бы находимся

    --oneline - опция для максимального сокращения информации о коммитах.

    *Эти две опции глобальны, каждая задается по отдельности к одной команде.*

- В тех слечаях, когда имеется ветвление в структуре коммитов, чтобы иметь четкое представление об изменениях, можно использовать графическую визуализацию веток. Для этого нужно испольковать команду:

        git log --graph
    
    где:

    --graph - опция, добавляющая графического отображения ветвей в логе коммитов.

- При испольховании опции "--graph", для получения максимально сжатой, но при этом и максимально понятной информации, лучше использовать команду с несколькими, ранее изученными опциями:

        git log --all --oneline --graph

## Просмотр выполненных изменений

Бывает так, что ты отвлекся, или просто забыл, какое изменение сделал, и, чтобы сделать верный коммит, нужно сравнить файл "до" и "после" изменений.

Для просмотра выполненных изменений использовать команду:

    git diff

### Дополнительные опции Git diff

- Для сравнения изменений двух коммитов (не последнего и предпоследнего, а, например, первого и третьего, или пятого и десятого) нужно использовать команду:

        git diff <hash1> <hash2>
    
    где:

        <hash1> - первые 7 цифр номера первого, более раннего коммита

        <hash2> - первые 7 цифр номера второго, более позднего коммита
    
    **Обрати внимание!**

    Принципиальной разницы нет, какой коммит с каким сравнивать (более ранний с более поздним или наоборот) **но**, если сравнивать более ранний с более поздним, тогда, при выполнении команды сравнения *добавление* нового текста будет соответствовать *добавлению* в изменениях.

    В случае, если сравниваются более поздний коммит с более ранним, тогда *добавление* нового текста будет соответсвовать *удалению* этого фрагмента, так как в более ранней версии его нет.

## Перемещение между коммитами

- Для перемещения в интересующую нас версию, необходимо использовать номер коммита.

    Использовать команду:

        git checkout <hash>

    где:

        <hash> - первые семь цифр номера коммита, который нас интересует

- Для перемещения в последнюю "головную" версию файла нужно использовать команду:

        git checkout master

    где:

    master - последний актуальный коммит


## Ветвеления

Ветвления в Git нужны для того, чтобы программисты могли вести совместную работу над проектом и не мешать друг другу при этом.

### Просмотр существующих веток

Для того чтобы просмотреть существующие ветки нужно выполнить команду:

    git branch


Для того чтобы создать новую ветку нужно выполнить команду:

    git branch <branchname>

где:

"<branchname>" - имя ветки, задаваемое пользователем

Для того чтобы удалить ветку необходимо выполнить команду:

    git branch -d <branchname>

где:

-d - опция удаления ветки

Для форсированного удаления ветки используется команда:

    git branch -D <branchname>

где:

-D - опция удаления ветки, которая состоит из двух опций:

* -d - удаление

* -f (--force) - cбрасывает <branchname> в <startpoint>, даже если <branchname> уже существует. Без опции -f ветка git отказывается изменять существующую ветку.

## Слияние веток

Для слияния другой ветки с текущей, необходимо использовать команду:

    git merge <branchname>

где: 

"<branchname>" - имя ветки, которую необходимо слить текущей веткой

**!Внимание!**

При слиянии существует вероятность получения конфликта! Это нормальная ситуация и пугаться этого не стоит. Так происходит во время слияния веток, где на одной строчке находится разная информация, и на текущий момент Git не может понять, что нужно оставить - что верно, и что следует удалить.

В этом случае программисту самому придется определить, что оставлять, а что следует убрать.

После решения конфликта - обязательно закоммитить процесс.

## Удаленные репозитории

Удаленные репозитории нужны для...

1. связываение локального и удаленного репозитория
1. git push
1. git pull
1. git clone
1. fork
1. pull-request