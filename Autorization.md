### Терминология
- **`Идентификация`** - это заявление о том, кем вы являетесь. В зависимости от ситуации, это может быть имя, адрес электронной почты, номер учетной записи, итд.;
- **`Аутентификация`** -  предоставление доказательств, что вы на самом деле есть тот, кем идентифицировались (от слова “authentic” — истинный, подлинный).;
- **`Авторизация`** - -   проверка, что вам разрешен доступ к запрашиваемому ресурсу.



---
|     **Способ**|**Основное применение**|**Протоколы**|
|----------------|-------------------------------|-----------------------------|
|**По паролю**| Аутентификация пользователей |  HTTP, Forms|
|**По сертификатам**|Аутентификация пользователей в безопасных приложениях; аутентификация сервисов| SSL/TLS|
|**По одноразовым паролям**|Дополнительная аутентификация пользователей (для достижения two-factor authentication)|Forms|
|**По ключам доступа**|Аутентификация сервисов и приложений|-|
|**По токенам**|Делегированная аутентификация пользователей; делегированная авторизация приложений|SAML, WS-Federation, OAuth, OpenID Connect|
---



## Basic
Наиболее простая схема, при которой `username` и `password` пользователя передаются в заголовке `Authorization` в незашифрованном виде (**base64-encoded**). Однако при использовании HTTPS (HTTP over SSL) протокола, является относительно безопасной.

![Basic](./img/AUTH_basic.png)

---
 **JSON Web Token (JWT)** — содержит три блока, разделенных точками: заголовок, набор полей (claims) и подпись. Первые два блока представлены в JSON-формате и дополнительно закодированы в формат base64. Набор полей содержит произвольные пары имя/значения, притом стандарт JWT определяет несколько зарезервированных имен (iss, aud, exp и другие). Подпись может генерироваться при помощи и симметричных алгоритмов шифрования, и асимметричных. Кроме того, существует отдельный стандарт, отписывающий формат зашифрованного JWT-токена.  
  
_Пример подписанного JWT токена (после декодирования 1 и 2 блоков)._  

> { «alg»: «HS256», «typ»: «JWT» }.  
> { «iss»: «[auth.myservice.com](http://auth.myservice.com/)», «aud»: «[myservice.com](http://myservice.com/)», «exp»: «1435937883», «userName»: «John Smith», «userRole»: «Admin» }.  
> S9Zs/8/uEGGTVVtLggFTizCsMtwOJnRhjaQ2BMUQhcY

## Войти через..

* Провайдерами аутентификации могут выступать организации, проверившие пользователя!
* Конечно, информация может быть передана только с согласия самого клиента

Для этого как раз существует экран согласия, который вы иногда видите, используя “вход через
какой-либо сервис.
![sber](./img/AUTH_sbr.png)


OPENid - это слой учетных данных поверх OAuth 2.0 (делегированная авторизация),  здесь появляется `id-token` и информация о пользователе.

**`id-token`** содержит информацию о пользователе.

**`access-token`**  - ключ позволяющий получить доступ к удаленным ресурсам. Имеет ограниченное время жизни. Хранится в `LocalStorage`.

**`refresh=token`** - живет более долго (30 дней например), необходим для обновления access-токена. Хранится в куках.

OAuth 2.0
![oauth](./img/AUTH_OAuth2.png)

>OAuth используется для:
> - Предоставления доступа к API;
> - Получения данных пользователя в других системах.

OpenID
![openID](./img/AUTH_OpenID.png)
> OpenID используется для аутентификации пользователя.

Сайт, получив токен доступа для пользователя, может выполнить с ним запрос к Authorization Server (**OIDS**) для получения информации о пользователе (_доступную, разрешенную информацию_).
* Доступ к информации управляется через Sсореs
* Sсореs вшиты в токен доступа, и выдаются OIDS

> **`Sсоре`** — некое мнемоническое имя, имеющее значение в определенных контекстах

Примеры:
* profile,
* email


Сайту по сути не нужен ассеss Tокеn, если он не обращается к внешним сервисам от лица клиента, но он нужен для получения дополнительной информации от сервера авторизации о пользователе.



**Роль фронта** - хранение токена, отправка токена, обновление токена.

---

https://habr.com/ru/companies/dataart/articles/262817/

https://deworker.pro/edu/series/http-basics/authentication-headers

https://www.youtube.com/watch?v=fN25fMQZ2v0&ab_channel=UlbiTV

https://www.youtube.com/watch?v=kHL-zwEuSQo&ab_channel=SergeiCalabonga

https://www.youtube.com/watch?v=i7vuFHH0nxY&ab_channel=DotNetRu



# Files

StackEdit stores your files in your browser, which means all your files are automatically saved locally and are accessible **offline!**

## Create files and folders

The file explorer is accessible using the button in left corner of the navigation bar. You can create a new file by clicking the **New file** button in the file explorer. You can also create folders by clicking the **New folder** button.

## Switch to another file

All your files and folders are presented as a tree in the file explorer. You can switch from one to another by clicking a file in the tree.

## Rename a file

You can rename the current file by clicking the file name in the navigation bar or by clicking the **Rename** button in the file explorer.

## Delete a file

You can delete the current file by clicking the **Remove** button in the file explorer. The file will be moved into the **Trash** folder and automatically deleted after 7 days of inactivity.

## Export a file

You can export the current file by clicking **Export to disk** in the menu. You can choose to export the file as plain Markdown, as HTML using a Handlebars template or as a PDF.


# Synchronization

Synchronization is one of the biggest features of StackEdit. It enables you to synchronize any file in your workspace with other files stored in your **Google Drive**, your **Dropbox** and your **GitHub** accounts. This allows you to keep writing on other devices, collaborate with people you share the file with, integrate easily into your workflow... The synchronization mechanism takes place every minute in the background, downloading, merging, and uploading file modifications.

There are two types of synchronization and they can complement each other:

- The workspace synchronization will sync all your files, folders and settings automatically. This will allow you to fetch your workspace on any other device.
	> To start syncing your workspace, just sign in with Google in the menu.

- The file synchronization will keep one file of the workspace synced with one or multiple files in **Google Drive**, **Dropbox** or **GitHub**.
	> Before starting to sync files, you must link an account in the **Synchronize** sub-menu.

## Open a file

You can open a file from **Google Drive**, **Dropbox** or **GitHub** by opening the **Synchronize** sub-menu and clicking **Open from**. Once opened in the workspace, any modification in the file will be automatically synced.

## Save a file

You can save any file of the workspace to **Google Drive**, **Dropbox** or **GitHub** by opening the **Synchronize** sub-menu and clicking **Save on**. Even if a file in the workspace is already synced, you can save it to another location. StackEdit can sync one file with multiple locations and accounts.

## Synchronize a file

Once your file is linked to a synchronized location, StackEdit will periodically synchronize it by downloading/uploading any modification. A merge will be performed if necessary and conflicts will be resolved.

If you just have modified your file and you want to force syncing, click the **Synchronize now** button in the navigation bar.

> **Note:** The **Synchronize now** button is disabled if you have no file to synchronize.

## Manage file synchronization

Since one file can be synced with multiple locations, you can list and manage synchronized locations by clicking **File synchronization** in the **Synchronize** sub-menu. This allows you to list and remove synchronized locations that are linked to your file.


# Publication

Publishing in StackEdit makes it simple for you to publish online your files. Once you're happy with a file, you can publish it to different hosting platforms like **Blogger**, **Dropbox**, **Gist**, **GitHub**, **Google Drive**, **WordPress** and **Zendesk**. With [Handlebars templates](http://handlebarsjs.com/), you have full control over what you export.

> Before starting to publish, you must link an account in the **Publish** sub-menu.

## Publish a File

You can publish your file by opening the **Publish** sub-menu and by clicking **Publish to**. For some locations, you can choose between the following formats:

- Markdown: publish the Markdown text on a website that can interpret it (**GitHub** for instance),
- HTML: publish the file converted to HTML via a Handlebars template (on a blog for example).

## Update a publication

After publishing, StackEdit keeps your file linked to that publication which makes it easy for you to re-publish it. Once you have modified your file and you want to update your publication, click on the **Publish now** button in the navigation bar.

> **Note:** The **Publish now** button is disabled if your file has not been published yet.

## Manage file publication

Since one file can be published to multiple locations, you can list and manage publish locations by clicking **File publication** in the **Publish** sub-menu. This allows you to list and remove publication locations that are linked to your file.


# Markdown extensions

StackEdit extends the standard Markdown syntax by adding extra **Markdown extensions**, providing you with some nice features.

> **ProTip:** You can disable any **Markdown extension** in the **File properties** dialog.


## SmartyPants

SmartyPants converts ASCII punctuation characters into "smart" typographic punctuation HTML entities. For example:

|                |ASCII                          |HTML                         |
|----------------|-------------------------------|-----------------------------|
|Single backticks|`'Isn't this fun?'`            |'Isn't this fun?'            |
|Quotes          |`"Isn't this fun?"`            |"Isn't this fun?"            |
|Dashes          |`-- is en-dash, --- is em-dash`|-- is en-dash, --- is em-dash|


## KaTeX

You can render LaTeX mathematical expressions using [KaTeX](https://khan.github.io/KaTeX/):

The *Gamma function* satisfying $\Gamma(n) = (n-1)!\quad\forall n\in\mathbb N$ is via the Euler integral

$$
\Gamma(z) = \int_0^\infty t^{z-1}e^{-t}dt\,.
$$

> You can find more information about **LaTeX** mathematical expressions [here](http://meta.math.stackexchange.com/questions/5020/mathjax-basic-tutorial-and-quick-reference).


## UML diagrams

You can render UML diagrams using [Mermaid](https://mermaidjs.github.io/). For example, this will produce a sequence diagram:

```mermaid
sequenceDiagram
Alice ->> Bob: Hello Bob, how are you?
Bob-->>John: How about you John?
Bob--x Alice: I am good thanks!
Bob-x John: I am good thanks!
Note right of John: Bob thinks a long<br/>long time, so long<br/>that the text does<br/>not fit on a row.

Bob-->Alice: Checking with John...
Alice->John: Yes... John, how are you?
```

And this will produce a flow chart:

```mermaid
graph LR
A[Square Rect] -- Link text --> B((Circle))
A --> C(Round Rect)
B --> D{Rhombus}
C --> D
```