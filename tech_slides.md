https://dev.to/andyhaskell/write-your-tech-talk-slides-rapidly-with-marp-2c7g

Я занимаюсь публичными выступлениями в сфере технологий с 2015 года, когда я представил свой самый первый молниеносный доклад на Boston Go, и с тех пор я выступал с докладами на встречах, на работе и на нескольких конференциях.

Но хотя мне нравится выступать на мероприятиях, чтобы преподавать технические концепции, которые я изучил, могут возникнуть некоторые трудности при передаче идей из моего мозга в слайды, при продумывании макета слайдов и доработке слайдов, чтобы мое выступление плавно переходило от слайда к слайду.

Что мне в последнее время помогло в написании слайдов, так это инструмент под названием Marp, который позволяет мне писать макет слайда, просто печатая в текстовом редакторе **Markdown** . Что для меня означает:

-   🏎️ Поскольку в Marp есть разумные встроенные макеты, мне не нужно думать о таких вещах, как размер шрифта, пока у меня нет на то причины; Я могу просто набрать текст, как если бы это было сообщение в блоге, и слайд будет выглядеть достаточно хорошо, и я смогу сразу попрактиковаться с ним, а позже настроить его макет!
-   👀 Поскольку я пишу слайды в своем редакторе, если я хочу переключиться на эксперименты с кодом, о котором рассказывается в моем докладе, для меня это гораздо меньшее переключение контекста, чем переход между инструментом перетаскивания слайдов и инструментом Текстовый редактор.
    -   Говоря о предотвращении переключения контекста, есть также [плагин Marp для VSCode](https://marketplace.visualstudio.com/items?itemName=marp-team.marp-vscode) , который вы можете использовать, чтобы видеть свои слайды рядом с текстом, который вы пишете, в режиме реального времени!
-   🦕 Поскольку мои слайды состоят из текста, это позволяет легко создавать разные версии моего выступления **в Git** , поэтому, экспериментируя с различным расположением слайдов, я могу переключать версии так быстро, как вы можете сказать. `git checkout`!
-   🎨 Вы можете настроить макет отдельных слайдов или всех слайдов с помощью CSS!

И я могу сказать, что Marp готов к конференции, поскольку именно его я использовал для написания и повторения своей презентации на GopherCon в этом году!

Поэтому в этом уроке я хотел бы показать вам, как использовать Marp для написания трех типов слайдов: титульный слайд с привлекательным изображением, слайд «обо мне» с изображением слева и текстом справа, и слайд с фрагментом кода. Я также покажу вам, как добавлять заметки докладчика, которые может видеть только докладчик во время презентации, и как использовать CSS, чтобы придать макету слайда больше возможностей настройки.

## [](https://dev.to/andyhaskell/write-your-tech-talk-slides-rapidly-with-marp-2c7g#installing-marp)Установка Марпа

Чтобы получить Marp, вы устанавливаете его интерфейс командной строки с помощью менеджера пакетов, такого как Homebrew, Scoop или Yarn.  

Установив Marp, давайте напишем нашу презентацию слайдов!

## [](https://dev.to/andyhaskell/write-your-tech-talk-slides-rapidly-with-marp-2c7g#writing-our-first-title-slide)Пишем наш первый титульный слайд

Во-первых, давайте дадим нашему выступлению титульный слайд. Вставьте этот Markdown в файл с именем `talk.md`.  

```
<span>---</span>
<span>marp</span><span>:</span> <span>true</span>
<span>theme</span><span>:</span> <span>uncover</span>
<span>paginate</span><span>:</span> <span>true</span>
<span>---</span>

<span># What is io.Reader in Go?</span>

YOUR NAME - @YOUR_SOCIAL_MEDIA
```

Сейчас у нас написаны две части синтаксиса Marp: вверху раздел, полный опций внутри тройного тире, называется frontmatter [и](https://marpit.marp.app/directives?id=front-matter) содержит конфигурацию вашей презентации в целом.

Правила нашего фронтмена таковы:

-   `marp: true`, что указывает на то, что это презентация Marp
-   `theme: uncover`, который устанавливает тему ваших слайдов Uncover, одну из [встроенных тем](https://github.com/marp-team/marp-core/blob/main/themes/README.md) Marp.
-   `paginate: true`, что приводит к тому, что ваши слайды включают номер страницы.

Есть и другие правила, которые вы можете добавить в заголовок, например: `style`для дополнительного пользовательского стиля CSS или `backgroundImage`если вы хотите, чтобы все ваши слайды имели фоновое изображение по умолчанию, например узорчатый фон, чтобы ваши слайды выглядели более яркими.

Ниже заголовка у нас есть первый слайд, написанный в Markdown.  

```
<span># What is io.Reader in Go?</span>

<span>**YOUR NAME - @YOUR_SOCIAL_MEDIA**</span>
```

Как и в стандартной уценке, текст представляет собой заголовок названия вашего выступления, а обычный текст, выделенный жирным шрифтом, — ваше имя и учетную запись в социальной сети.

Чтобы увидеть, как на самом деле выглядит этот слайд в презентации, запустите только что установленный интерфейс командной строки Marp:  

Затем вы получите приглашение перейти к URI локального хоста. Перейдите туда в своем браузере, и вы  
посмотрите свою презентацию. На данный момент титульный слайд выглядит так:

[![Начальный слайд с заголовком, выделенным жирным шрифтом.  Маркер страницы указывает, что мы находимся на первом слайде.](%D0%91%D1%8B%D1%81%D1%82%D1%80%D0%BE%20%D0%BD%D0%B0%D0%BF%D0%B8%D1%88%D0%B8%D1%82%D0%B5%20%D1%81%D0%BB%D0%B0%D0%B9%D0%B4%D1%8B%20%D1%82%D0%B5%D1%85%D0%BD%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%BE%D0%B3%D0%BE%20%D0%B4%D0%BE%D0%BA%D0%BB%D0%B0%D0%B4%D0%B0%20%D1%81%20%D0%BF%D0%BE%D0%BC%D0%BE%D1%89%D1%8C%D1%8E%20Marp%20-%20%D0%A1%D0%BE%D0%BE%D0%B1%D1%89%D0%B5%D1%81%D1%82%D0%B2%D0%BE%20DEV/lx0ugtuqs09uzp0x5gib.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--YnWLFYJy--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/lx0ugtuqs09uzp0x5gib.png)

У нас есть заголовок и имя. Это хороший чистый макет для титульного слайда, но что, если нам нужно классное изображение, с которого можно начать разговор? Вы можете добавить это с помощью Markdown для изображения.

### [](https://dev.to/andyhaskell/write-your-tech-talk-slides-rapidly-with-marp-2c7g#adding-an-image)Добавление изображения

Как и в стандартном Markdown, в Marp вы используете `![alt text](image URL)`формат для рендеринга изображений. Чтобы опробовать это, мы воспользуемся фотографией ярко-голубой воды, сделанной мной в прекрасный день на пляже.  

```
<span>![</span><span>Picture of the view at the beach; rocks are in the foreground and the water that day was bright blue</span><span>](</span><span>https://url/to/beach/image</span><span>)</span>

<span># What is io.Reader in Go?</span>

YOUR NAME - @YOUR_SOCIAL_MEDIA
<span>
---
</span>
```

Теперь посмотрите на talk.html и

[![Первый слайд теперь с фотографией с пляжа, но изображение настолько высокое, что выталкивает текст за пределы экрана.](%D0%91%D1%8B%D1%81%D1%82%D1%80%D0%BE%20%D0%BD%D0%B0%D0%BF%D0%B8%D1%88%D0%B8%D1%82%D0%B5%20%D1%81%D0%BB%D0%B0%D0%B9%D0%B4%D1%8B%20%D1%82%D0%B5%D1%85%D0%BD%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%BE%D0%B3%D0%BE%20%D0%B4%D0%BE%D0%BA%D0%BB%D0%B0%D0%B4%D0%B0%20%D1%81%20%D0%BF%D0%BE%D0%BC%D0%BE%D1%89%D1%8C%D1%8E%20Marp%20-%20%D0%A1%D0%BE%D0%BE%D0%B1%D1%89%D0%B5%D1%81%D1%82%D0%B2%D0%BE%20DEV/vgk5jylhvutepjgrvuay.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--n4S9M7Vh--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/vgk5jylhvutepjgrvuay.png)

Ого, какое высокое изображение! Если мы хотим, чтобы это изображение поместилось на слайде, нам нужно будет изменить его размер, и мы сделаем это, добавив директиву к замещающему тексту, а также уменьшив текст заголовка, преобразовав его из заголовка h1 в заголовок h3.  

```
<span>![</span><span>w:800 h:480 Picture of the view at the beach; rocks are in the foreground and the water that day was aqua</span><span>](</span><span>https://url/to/beach/image</span><span>)</span>

<span>### What is io.Reader in Go?</span>
```

С помощью директив `w:800 h:480`, мы просим Марпа установить ширину и высоту изображения на 800 пикселей и 480 пикселей соответственно, что аккуратно вписывается в слайд.

[![Первый слайд с размером изображения, измененным таким образом, чтобы изображение и текст вписывались в высоту слайда.](%D0%91%D1%8B%D1%81%D1%82%D1%80%D0%BE%20%D0%BD%D0%B0%D0%BF%D0%B8%D1%88%D0%B8%D1%82%D0%B5%20%D1%81%D0%BB%D0%B0%D0%B9%D0%B4%D1%8B%20%D1%82%D0%B5%D1%85%D0%BD%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%BE%D0%B3%D0%BE%20%D0%B4%D0%BE%D0%BA%D0%BB%D0%B0%D0%B4%D0%B0%20%D1%81%20%D0%BF%D0%BE%D0%BC%D0%BE%D1%89%D1%8C%D1%8E%20Marp%20-%20%D0%A1%D0%BE%D0%BE%D0%B1%D1%89%D0%B5%D1%81%D1%82%D0%B2%D0%BE%20DEV/d2aqyl9c99epobovxx1c.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--f1zFovSz--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/d2aqyl9c99epobovxx1c.png)

Или, если вы действительно хотите быть ярким и создать изображение, занимающее весь фон, вы можете использовать `bg`директива!

`![bg Picture of the view at the beach; rocks are in the foreground and the water that day was aqua](https://url/to/beach/image)`

[![Первый слайд, теперь изображение используется в качестве фона слайда, текст слайда выделен черным цветом.  В некоторых местах на изображении камни и вода темнее, из-за чего некоторые буквы труднее читать.](%D0%91%D1%8B%D1%81%D1%82%D1%80%D0%BE%20%D0%BD%D0%B0%D0%BF%D0%B8%D1%88%D0%B8%D1%82%D0%B5%20%D1%81%D0%BB%D0%B0%D0%B9%D0%B4%D1%8B%20%D1%82%D0%B5%D1%85%D0%BD%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%BE%D0%B3%D0%BE%20%D0%B4%D0%BE%D0%BA%D0%BB%D0%B0%D0%B4%D0%B0%20%D1%81%20%D0%BF%D0%BE%D0%BC%D0%BE%D1%89%D1%8C%D1%8E%20Marp%20-%20%D0%A1%D0%BE%D0%BE%D0%B1%D1%89%D0%B5%D1%81%D1%82%D0%B2%D0%BE%20DEV/wthr2e1a6wqh0g56fcay.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--w1MycH6a--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/wthr2e1a6wqh0g56fcay.png)

Но вам нужно убедиться, что текст контрастирует с цветами изображения, с которыми он может перекрываться. Мы рассмотрим один из способов сделать это с помощью текста с тенью в разделе CSS.

## [](https://dev.to/andyhaskell/write-your-tech-talk-slides-rapidly-with-marp-2c7g#adding-an-about-me-slide)Добавляем слайд «обо мне»

Чтобы написать новый слайд, вы отделяете каждый слайд в Marp, добавляя строку, содержащую три тире, например:  

```
<span>![</span><span>w:700 h:500 Picture of the view at the beach; rocks are in the foreground and the water that day was bright blue</span><span>](</span><span>https://url/to/beach/image</span><span>)</span>

<span># What is io.Reader in Go?</span>

YOUR NAME - @YOUR_SOCIAL_MEDIA
<span>
---
</span>
Everything from here down to
the next --- line will be
will be part of the Markdown of
the second slide of your talk,
and then you add another --- to
give your talk a third slide
```

Мы заменим текстовый блок-заполнитель слайдом «обо мне», который соответствует обычному макету слайдов: изображение занимает левую часть слайда, а текст — правую.

И мы будем делать это, используя параметр изображения `bg`директива, которую мы видели ранее, которая делает `bg`изображение должно быть только в левой части слайда: `bg left`. В качестве примера давайте попросим мою собаку Лолу выступить с докладом.  

```
<span>---
</span>
<span>![</span><span>bg left 70% My dog Lola, an adorable black and white Havanese dog who looks like a tiny floofy panda, on the couch looking at the camera doing a blep</span><span>](</span><span>https://url/to/lola/image</span><span>)</span>

<span># About me</span>
<span>
-</span> <span>**Name:**</span> Lola the Micropanda
<span>-</span> <span>**Job:**</span> CFO at Micropanda Accelerator
<span>-</span> <span>**IG:**</span> @lolamicropanda
```

Откройте слайд-шоу Marp, и вы увидите:

[![Слайд «обо мне».  В левой части слайда находится изображение Лолы, отображенное в виде вертикальной полосы посередине левой части слайда.  Справа от слайда — биография Лолы «обо мне».](%D0%91%D1%8B%D1%81%D1%82%D1%80%D0%BE%20%D0%BD%D0%B0%D0%BF%D0%B8%D1%88%D0%B8%D1%82%D0%B5%20%D1%81%D0%BB%D0%B0%D0%B9%D0%B4%D1%8B%20%D1%82%D0%B5%D1%85%D0%BD%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%BE%D0%B3%D0%BE%20%D0%B4%D0%BE%D0%BA%D0%BB%D0%B0%D0%B4%D0%B0%20%D1%81%20%D0%BF%D0%BE%D0%BC%D0%BE%D1%89%D1%8C%D1%8E%20Marp%20-%20%D0%A1%D0%BE%D0%BE%D0%B1%D1%89%D0%B5%D1%81%D1%82%D0%B2%D0%BE%20DEV/yinuhb7f7wv7fc5fn118.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--Vaa19S5C--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/yinuhb7f7wv7fc5fn118.png)

Слайд Лолы «обо мне»! Обратите внимание, что в дополнение к `left`параметр на `bg`директиву, я также решил добавить `70%`параметр. В результате изображение занимает средние 70 % левой части слайда, а не всю левую часть слайда, в результате чего изображение «обо мне» отображается в виде полосы в левой части слайда.

Кстати, вы знаете технику представления маркированного списка, в котором пункты списка отображаются один за другим по мере представления? Например: «Немного обо мне \[показать маркер\], я Микропанда Лола, \[показать еще один пункт\], я главный специалист по работе с Micropanda Accelerator \[показать еще один пункт\], и вы можете подписаться на меня в Instagram». в @lolamicropanda"?

Марп тоже это поддерживает! Если вы измените пункты списка с тире на звездочки, вот так  

```
<span>*</span> <span>**Name:**</span> Lola the Micropanda
<span>*</span> <span>**Job:**</span> CFO at Micropanda Accelerator
<span>*</span> <span>**IG:**</span> @lolamicropanda
```

Вы получаете [фрагментированный список](https://marpit.marp.app/fragmented-list) ; пролистайте слайд «обо мне» `talk.html`и теперь, когда вы представляете, ваши пункты списка появляются один за другим!

## [](https://dev.to/andyhaskell/write-your-tech-talk-slides-rapidly-with-marp-2c7g#code-snippets-and-speaker-notes)Фрагменты кода и заметки докладчика

Точно так же, как Marp поддерживает изображения, заголовки, обычный текст и списки, в Marp также можно создавать слайды, содержащие фрагменты кода. Как и в стандартном Markdown, вы создаете фрагмент кода с тройными обратными кавычками (заменяется сообщением в скобках для фрагментов кода впереди, потому что у меня возникли проблемы с отображением тройных обратных кавычек внутри фрагмента кода).  

```
<span>## io.Reader in Go: small interface with tons of power</span>

[replace this box with triple backticks in your code]
type Reader interface {
    Read(p []byte) (n int, err error)
}
[replace this box with triple backticks in your code]
<span>
---
</span>
```

Если вы посмотрите на этот слайд в своем `talk.html`, вот увидишь:

[![Слайд, показывающий код интерфейса Go io.Reader](%D0%91%D1%8B%D1%81%D1%82%D1%80%D0%BE%20%D0%BD%D0%B0%D0%BF%D0%B8%D1%88%D0%B8%D1%82%D0%B5%20%D1%81%D0%BB%D0%B0%D0%B9%D0%B4%D1%8B%20%D1%82%D0%B5%D1%85%D0%BD%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%BE%D0%B3%D0%BE%20%D0%B4%D0%BE%D0%BA%D0%BB%D0%B0%D0%B4%D0%B0%20%D1%81%20%D0%BF%D0%BE%D0%BC%D0%BE%D1%89%D1%8C%D1%8E%20Marp%20-%20%D0%A1%D0%BE%D0%BE%D0%B1%D1%89%D0%B5%D1%81%D1%82%D0%B2%D0%BE%20DEV/mfdchu5eg5tjnja2rgru.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--FO52Q3q1--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/mfdchu5eg5tjnja2rgru.png)

Ваш код на слайде, отформатированный в моноширинном формате! Хотя вам может потребоваться подсветка синтаксиса на ваших слайдах, и если вы это сделаете, вы можете сделать простую настройку: перед ведущими обратными кавычками введите язык программирования, на котором написан ваш код. Мой код написан на Go, поэтому я начинаю с `go`в конце тройных обратных кавычек.  

```
<span>- [replace this box with triple backticks in your code]
</span><span>+ [replace this box with triple backticks in your code]go
</span>  type Reader interface {
      Read(p []byte) (n int, err error)
  }
```

Теперь на вашем слайде будет подсветка синтаксиса.

[![Слайд-отображение кода, теперь с подсветкой синтаксиса Go](%D0%91%D1%8B%D1%81%D1%82%D1%80%D0%BE%20%D0%BD%D0%B0%D0%BF%D0%B8%D1%88%D0%B8%D1%82%D0%B5%20%D1%81%D0%BB%D0%B0%D0%B9%D0%B4%D1%8B%20%D1%82%D0%B5%D1%85%D0%BD%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%BE%D0%B3%D0%BE%20%D0%B4%D0%BE%D0%BA%D0%BB%D0%B0%D0%B4%D0%B0%20%D1%81%20%D0%BF%D0%BE%D0%BC%D0%BE%D1%89%D1%8C%D1%8E%20Marp%20-%20%D0%A1%D0%BE%D0%BE%D0%B1%D1%89%D0%B5%D1%81%D1%82%D0%B2%D0%BE%20DEV/74e97ue7dfy32d5scjds.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--uVSxiR1I--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/74e97ue7dfy32d5scjds.png)

И если бы я выступал с этим докладом по-настоящему, на этом слайде заметки докладчика действительно пригодились бы, поскольку есть несколько вещей, которые я хотел бы отметить в Go. `io.Reader`интерфейс.

Не каждый докладчик использует заметки, но если вы используете заметки докладчика или хотите их попробовать, Marp позволяет вам добавить к любому из ваших слайдов примечания, которые увидите только вы, когда будете представлять их в стиле HTML. `<!-- -->`Комментарии. Лично я считаю их полезными для моего выступления, поскольку они напоминают мне о концепциях, которые я хочу затронуть, или служат временными подсказками, например, для перехода к следующему слайду в середине предложения. Вот пример  

```
&lt;!--
The io.Reader interface is a type you'll see all over the Go interface, with just one method. Let's look at that method's signature.
<span>
*</span> In the return value n is the number of bytes read to the buffer
<span>*</span> err can include EOF for reaching the end of the input
<span>*</span> The part I found surprising was we don't return the bytes we read, we copy them to a buffer we pass in. And the reason why is-[CHANGE SLIDE]
--&gt;
<span>
---
</span>
```

Чтобы использовать заметки докладчика, откройте talk.html, наведите указатель мыши на слайды и щелкните значок кафедры в правой части открывшегося меню. Теперь вы находитесь в **режиме докладчика** , как в инструментах перетаскивания. Таким образом, у вас будет одно окно рабочего стола, показывающее текущий слайд, которым вы делитесь с аудиторией, а другое — ваши заметки докладчика, текущий слайд и эскиз следующего слайда.

[![Режим докладчика: текущий слайд, заметки докладчика и следующий слайд.](%D0%91%D1%8B%D1%81%D1%82%D1%80%D0%BE%20%D0%BD%D0%B0%D0%BF%D0%B8%D1%88%D0%B8%D1%82%D0%B5%20%D1%81%D0%BB%D0%B0%D0%B9%D0%B4%D1%8B%20%D1%82%D0%B5%D1%85%D0%BD%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%BE%D0%B3%D0%BE%20%D0%B4%D0%BE%D0%BA%D0%BB%D0%B0%D0%B4%D0%B0%20%D1%81%20%D0%BF%D0%BE%D0%BC%D0%BE%D1%89%D1%8C%D1%8E%20Marp%20-%20%D0%A1%D0%BE%D0%BE%D0%B1%D1%89%D0%B5%D1%81%D1%82%D0%B2%D0%BE%20DEV/cfblob2kj48lxde0z1qu.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--S9vhk25c--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/cfblob2kj48lxde0z1qu.png)

## [](https://dev.to/andyhaskell/write-your-tech-talk-slides-rapidly-with-marp-2c7g#using-css-in-your-slides)Использование CSS в ваших слайдах

Макет слайдов Marp имеет разумные настройки по умолчанию, но вы можете настроить макет слайда, используя всю мощь CSS, вставив `<style scoped>`HTML-тег в один слайд или `<style>`HTML-тег для добавления правил CSS, применимых ко всем слайдам.

Прежде всего, на нашем слайде показан код Go. `io.Reader`интерфейс, хотя мне нравится иметь небольшой объем информации на каждом слайде, чтобы уменьшить когнитивную нагрузку, поскольку на слайде так мало кода, код мог бы использовать шрифт большего размера, чтобы занять большую часть экрана. Вот как мы это сделаем:  

```
<span>---</span>

<span>&lt;style scoped&gt;</span>
<span>code {</span>
  <span>font-size</span><span>:</span> <span>40px;</span>
<span>}</span>
<span>&lt;/style&gt;</span>

<span>## io.Reader in Go: small interface with tons of power</span>

<span>[</span><span>replace this line with triple backticks in your code</span><span>]</span><span>go</span>
<span>type Reader interface {</span>
    <span>Read(p []byte) (n int, err error)</span>
<span>}</span>
<span>[</span><span>replace this line with triple backticks in your code</span><span>]</span>

<span>---</span>
```

Посмотрите на этот слайд `talk.html`, и вы увидите, что код теперь занимает большую часть экрана.

[![Слайд с кодом, теперь код занимает большую часть экрана](%D0%91%D1%8B%D1%81%D1%82%D1%80%D0%BE%20%D0%BD%D0%B0%D0%BF%D0%B8%D1%88%D0%B8%D1%82%D0%B5%20%D1%81%D0%BB%D0%B0%D0%B9%D0%B4%D1%8B%20%D1%82%D0%B5%D1%85%D0%BD%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%BE%D0%B3%D0%BE%20%D0%B4%D0%BE%D0%BA%D0%BB%D0%B0%D0%B4%D0%B0%20%D1%81%20%D0%BF%D0%BE%D0%BC%D0%BE%D1%89%D1%8C%D1%8E%20Marp%20-%20%D0%A1%D0%BE%D0%BE%D0%B1%D1%89%D0%B5%D1%81%D1%82%D0%B2%D0%BE%20DEV/ptknpcwowjsepznzplji.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--z2jeSRUV--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ptknpcwowjsepznzplji.png)

Далее, помните, как я упоминал, что наш титульный слайд может быть фоновым изображением с текстом на нем, используя `bg`директива, но мы хотели бы использовать CSS, чтобы обеспечить разборчивость нашего текста?

Вот CSS, который мы бы добавили для титульного слайда. Обратите внимание, что мы также меняем заголовок обратно на h1, поскольку изображение теперь является фоновым, поэтому нам не нужно экономить место с помощью заголовка h3.  

```
<span>&lt;style </span><span>scoped</span><span>&gt;</span>
<span>h1</span><span>,</span> <span>p</span> <span>{</span>
  <span>color</span><span>:</span> <span>#FFFFFF</span><span>;</span>
  <span>font-weight</span><span>:</span> <span>bold</span><span>;</span>
  <span>text-shadow</span><span>:</span>
    <span>5px</span> <span>5px</span> <span>3px</span> <span>#000000</span><span>;</span>
<span>}</span>
<span>&lt;/style&gt;</span>

![bg Picture of the rocks on Singing Beach; rocks are in the foreground and the water that day was bright blue](https://url/to/beach/image)

# What is the io.Reader interface in Go?

YOUR NAME - @YOUR-SOCIAL-MEDIA

---
```

Правила делают весь текст на этом слайде («заголовок 1» и абзац или `h1`и `p`в CSS и HTML) белый, полужирный, с черной тенью текста вниз и вправо. Вот как это выглядит `talk.html`

[![Слайд с фоновым изображением;  текст отображается белым и жирным шрифтом, с тенью, поэтому текст контрастирует с окружением](%D0%91%D1%8B%D1%81%D1%82%D1%80%D0%BE%20%D0%BD%D0%B0%D0%BF%D0%B8%D1%88%D0%B8%D1%82%D0%B5%20%D1%81%D0%BB%D0%B0%D0%B9%D0%B4%D1%8B%20%D1%82%D0%B5%D1%85%D0%BD%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%BE%D0%B3%D0%BE%20%D0%B4%D0%BE%D0%BA%D0%BB%D0%B0%D0%B4%D0%B0%20%D1%81%20%D0%BF%D0%BE%D0%BC%D0%BE%D1%89%D1%8C%D1%8E%20Marp%20-%20%D0%A1%D0%BE%D0%BE%D0%B1%D1%89%D0%B5%D1%81%D1%82%D0%B2%D0%BE%20DEV/445wr2c769xjpeqxng8r.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--xfkQbi5y--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/445wr2c769xjpeqxng8r.png)

Потрясающий! И последнее, на что следует обратить внимание: скажем, мы хотим, чтобы содержимое ваших слайдов не попадало в нижние 20% слайда. Это сценарий, который вы можете увидеть, если на конференции есть живые субтитры и вы хотите разместить живые субтитры в нижних 20% экрана, что и сделал GopherCon.

Когда я это узнал, я смог быстро добавить `<style scoped>`теги, чтобы все мои слайды занимали 80% экрана, но что можно было бы сделать быстрее, так это если бы я вместо этого использовал `<style>`тег без `scoped`применить 20% отступов к нижней части всех слайдов!  

```
<span>&lt;style&gt;</span>
section {
  padding-bottom: 20%;
}
<span>&lt;/style&gt;</span>
```

Это работает, поскольку в HTML-коде, создаваемом инструментом «Марп», отдельный слайд представляет собой `<section>`HTML-элемент.

Тем не менее, это увеличивает содержание всех существующих слайдов на 20%, поэтому, если вы примените это к макету слайдов после того, как уже написали несколько слайдов, вам все равно захочется просмотреть существующие слайды и убедиться, что вы не Мне не нужно дополнительно настраивать макеты отдельных слайдов.

Еще одна вещь: если на вашей странице слишком много контента или слишком большое изображение, слайд все равно может выйти за пределы высоты, поэтому я научился одному трюку на репетиции GopherCon (не могу вспомнить, кто мне это сказал). но кто бы это ни был, спасибо!) заключался в том, чтобы временно изменить фоновое изображение моих слайдов на сетку 5 x 5 с красной горизонтальной линией на высоте 80%.

Вы можете применить это фоновое изображение ко всем слайдам (кроме слайдов с собственным фоновым изображением, например, к нашему недавно обновленному титульному слайду), используя `backgroundImage`в авангарде.  

```
---
marp: true
theme: uncover
paginate: true
backgroundImage: url('https://url/to/cutoff/image.png')
---
```

Вот как выглядит слайд с этим фоновым изображением: значительно выше отметки 80 %!

[![слайд с кодом, линия обрезки отображается на 80 % ниже верхнего края](%D0%91%D1%8B%D1%81%D1%82%D1%80%D0%BE%20%D0%BD%D0%B0%D0%BF%D0%B8%D1%88%D0%B8%D1%82%D0%B5%20%D1%81%D0%BB%D0%B0%D0%B9%D0%B4%D1%8B%20%D1%82%D0%B5%D1%85%D0%BD%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%BE%D0%B3%D0%BE%20%D0%B4%D0%BE%D0%BA%D0%BB%D0%B0%D0%B4%D0%B0%20%D1%81%20%D0%BF%D0%BE%D0%BC%D0%BE%D1%89%D1%8C%D1%8E%20Marp%20-%20%D0%A1%D0%BE%D0%BE%D0%B1%D1%89%D0%B5%D1%81%D1%82%D0%B2%D0%BE%20DEV/gamw3z0q7edry8k5pzek.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--kXfbGUoL--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/gamw3z0q7edry8k5pzek.png)

Если вас интересовал Marp, надеюсь, это поможет вам начать писать слайды в Marp! Мне также было бы интересно узнать о том, какие еще инструменты вы использовали, чтобы сделать процесс написания технического доклада более эргономичным, поэтому, если вы использовали какие-либо другие инструменты, я буду рад услышать о них в комментариях!