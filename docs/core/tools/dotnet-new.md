---
title: DotNet yeni komut
description: DotNet New komutu, belirtilen şablona göre yeni .NET Core projeleri oluşturur.
ms.date: 05/06/2019
ms.openlocfilehash: c9e960bab0e28e88b0cc8d431dad3b9f3f00c9c0
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69660548"
---
# <a name="dotnet-new"></a>dotnet new

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet new`-Belirtilen şablonu temel alan yeni bir proje, yapılandırma dosyası veya çözüm oluşturur.

## <a name="synopsis"></a>Özeti

# <a name="net-core-22tabnetcore22"></a>[.NET Core 2,2](#tab/netcore22)

```console
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2,0](#tab/netcore20)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1. x](#tab/netcore1x)

```console
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a>Açıklama

Komut `dotnet new` , geçerli bir .NET Core projesi başlatmak için kullanışlı bir yol sağlar.

Komutu, belirtilen şablon ve seçeneklere göre diskteki yapıtları oluşturmak için [şablon altyapısını](https://github.com/dotnet/templating) çağırır.

## <a name="arguments"></a>Arguments

`TEMPLATE`

Komut çağrıldığında örnek oluşturulacak şablon. Her şablonun geçirebilmeniz için özel seçenekleri olabilir. Daha fazla bilgi için bkz. [şablon seçenekleri](#template-options).

Değer, şablonlar veya **kısa ad** sütunundaki metin üzerinde tam eşleşme değilse, bu iki sütunda bir alt dize eşleşmesi gerçekleştirilir. `TEMPLATE`

# <a name="net-core-22tabnetcore22"></a>[.NET Core 2,2](#tab/netcore22)

Komut, şablonların varsayılan bir listesini içerir. Kullanılabilir `dotnet new -l` şablonların bir listesini almak için kullanın. Aşağıdaki tabloda, .NET Core SDK 2.2.100 ile önceden yüklenmiş olarak gelen şablonlar gösterilmektedir. Şablon için varsayılan dil, köşeli ayraçlar içinde gösterilir.

| Şablonlar                                    | Kısa Ad        | Dil     | Etiketler                                  |
|----------------------------------------------|-------------------|--------------|---------------------------------------|
| Konsol Uygulaması                          | `console`         | [C#], F#, VB | Ortak/konsol                        |
| Sınıf kitaplığı                                | `classlib`        | [C#], F#, VB | Ortak/Kitaplık                        |
| Birim testi projesi                            | `mstest`          | [C#], F#, VB | Test/MSTest                           |
| NUnit 3 test projesi                         | `nunit`           | [C#], F#, VB | Test/NUnit                            |
| NUnit 3 test öğesi                            | `nunit-test`      | [C#], F#, VB | Test/NUnit                            |
| xUnit test projesi                           | `xunit`           | [C#], F#, VB | Test/xUnit                            |
| Razor sayfası                                   | `page`            | [C#]         | Web/ASP. NET                           |
| MVC Viewıtemts                              | `viewimports`     | [C#]         | Web/ASP. NET                           |
| MVC ViewStart                                | `viewstart`       | [C#]         | Web/ASP. NET                           |
| ASP.NET Core boş                           | `web`             | [C#],F#     | Web/boş                             |
| ASP.NET Core Web uygulaması (Model-View-Controller) | `mvc`             | [C#],F#     | Web/MVC                               |
| ASP.NET Core Web uygulaması                         | `webapp`, `razor` | [C#]         | Web/MVC/Razor Pages                   |
| Angular ile ASP.NET Core                    | `angular`         | [C#]         | MVC/Web/SPA                           |
| Tepki verme. js ile ASP.NET Core                   | `react`           | [C#]         | MVC/Web/SPA                           |
| Yanıt verir. js ve Redux ile ASP.NET Core         | `reactredux`      | [C#]         | MVC/Web/SPA                           |
| Razor sınıf kitaplığı                          | `razorclasslib`   | [C#]         | Web/Razor/kitaplık/Razor sınıfı kitaplığı |
| ASP.NET Core Web API 'SI                         | `webapi`          | [C#],F#     | Web/WebAPI                            |
| Global. JSON dosyası                             | `globaljson`      |              | Config                                |
| NuGet yapılandırması                                 | `nugetconfig`     |              | Config                                |
| Web yapılandırması                                   | `webconfig`       |              | Config                                |
| Çözüm dosyası                                | `sln`             |              | Çözüm                              |

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

Komut, şablonların varsayılan bir listesini içerir. Kullanılabilir `dotnet new -l` şablonların bir listesini almak için kullanın. Aşağıdaki tabloda, .NET Core SDK 2.1.300 ile önceden yüklenmiş olarak gelen şablonlar gösterilmektedir. Şablon için varsayılan dil, köşeli ayraçlar içinde gösterilir.

| Şablonlar                                    | Kısa Ad      | Dil     | Etiketler                                  |
|----------------------------------------------|-----------------|--------------|---------------------------------------|
| Konsol Uygulaması                          | `console`       | [C#], F#, VB | Ortak/konsol                        |
| Sınıf kitaplığı                                | `classlib`      | [C#], F#, VB | Ortak/Kitaplık                        |
| Birim testi projesi                            | `mstest`        | [C#], F#, VB | Test/MSTest                           |
| xUnit test projesi                           | `xunit`         | [C#], F#, VB | Test/xUnit                            |
| Razor sayfası                                   | `page`          | [C#]         | Web/ASP. NET                           |
| MVC Viewıtemts                              | `viewimports`   | [C#]         | Web/ASP. NET                           |
| MVC ViewStart                                | `viewstart`     | [C#]         | Web/ASP. NET                           |
| ASP.NET Core boş                           | `web`           | [C#],F#     | Web/boş                             |
| ASP.NET Core Web uygulaması (Model-View-Controller) | `mvc`           | [C#],F#     | Web/MVC                               |
| ASP.NET Core Web uygulaması                         | `razor`         | [C#]         | Web/MVC/Razor Pages                   |
| Angular ile ASP.NET Core                    | `angular`       | [C#]         | MVC/Web/SPA                           |
| Tepki verme. js ile ASP.NET Core                   | `react`         | [C#]         | MVC/Web/SPA                           |
| Yanıt verir. js ve Redux ile ASP.NET Core         | `reactredux`    | [C#]         | MVC/Web/SPA                           | 
| Razor sınıf kitaplığı                          | `razorclasslib` | [C#]         | Web/Razor/kitaplık/Razor sınıfı kitaplığı |
| ASP.NET Core Web API 'SI                         | `webapi`        | [C#],F#     | Web/WebAPI                            |
| Global. JSON dosyası                             | `globaljson`    |              | Config                                |
| NuGet yapılandırması                                 | `nugetconfig`   |              | Config                                |
| Web yapılandırması                                   | `webconfig`     |              | Config                                |
| Çözüm dosyası                                | `sln`           |              | Çözüm                              |

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2,0](#tab/netcore20)

Komut, şablonların varsayılan bir listesini içerir. Kullanılabilir `dotnet new -l` şablonların bir listesini almak için kullanın. Aşağıdaki tabloda, .NET Core SDK 2.0.0 ile önceden yüklenmiş olarak gelen şablonlar gösterilmektedir. Şablon için varsayılan dil, köşeli ayraçlar içinde gösterilir.

| Şablonlar                                    | Kısa Ad    | Dil     | Etiketler                |
|----------------------------------------------|---------------|--------------|---------------------|
| Konsol Uygulaması                          | `console`     | [C#], F#, VB | Ortak/konsol      |
| Sınıf kitaplığı                                | `classlib`    | [C#], F#, VB | Ortak/Kitaplık      |
| Birim testi projesi                            | `mstest`      | [C#], F#, VB | Test/MSTest         |
| xUnit test projesi                           | `xunit`       | [C#], F#, VB | Test/xUnit          |
| ASP.NET Core boş                           | `web`         | [C#],F#     | Web/boş           |
| ASP.NET Core Web uygulaması (Model-View-Controller) | `mvc`         | [C#],F#     | Web/MVC             |
| ASP.NET Core Web uygulaması                         | `razor`       | [C#]         | Web/MVC/Razor Pages |
| Angular ile ASP.NET Core                    | `angular`     | [C#]         | MVC/Web/SPA         |
| Tepki verme. js ile ASP.NET Core                   | `react`       | [C#]         | MVC/Web/SPA         |
| Yanıt verir. js ve Redux ile ASP.NET Core         | `reactredux`  | [C#]         | MVC/Web/SPA         |
| ASP.NET Core Web API 'SI                         | `webapi`      | [C#],F#     | Web/WebAPI          |
| Global. JSON dosyası                             | `globaljson`  |              | Config              |
| NuGet yapılandırması                                 | `nugetconfig` |              | Config              |
| Web yapılandırması                                   | `webconfig`   |              | Config              |
| Çözüm dosyası                                | `sln`         |              | Çözüm            |
| Razor sayfası                                   | `page`        |              | Web/ASP. NET         |
| MVC Viewıtemts                              | `viewimports` |              | Web/ASP. NET         |
| MVC ViewStart                                | `viewstart`   |              | Web/ASP. NET         |

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1. x](#tab/netcore1x)

Komut, şablonların varsayılan bir listesini içerir. Kullanılabilir `dotnet new -all` şablonların bir listesini almak için kullanın. Aşağıdaki tabloda, .NET Core SDK 1.0.1 ile önceden yüklenmiş olarak gelen şablonlar gösterilmektedir. Şablon için varsayılan dil, köşeli ayraçlar içinde gösterilir.

| Şablonlar            | Kısa Ad    | Dil | Etiketler           |
|----------------------|---------------|----------|----------------|
| Konsol Uygulaması  | `console`     | [C#],F# | Ortak/konsol |
| Sınıf kitaplığı        | `classlib`    | [C#],F# | Ortak/Kitaplık |
| Birim testi projesi    | `mstest`      | [C#],F# | Test/MSTest    |
| xUnit test projesi   | `xunit`       | [C#],F# | Test/xUnit     |
| ASP.NET Core boş   | `web`         | [C#]     | Web/boş      |
| ASP.NET Core Web uygulaması | `mvc`         | [C#],F# | Web/MVC        |
| ASP.NET Core Web API 'SI | `webapi`      | [C#]     | Web/WebAPI     |
| NuGet yapılandırması         | `nugetconfig` |          | Config         |
| Web yapılandırması           | `webconfig`   |          | Config         |
| Çözüm dosyası        | `sln`         |          | Çözüm       |

---

## <a name="options"></a>Seçenekler

# <a name="net-core-22tabnetcore22"></a>[.NET Core 2,2](#tab/netcore22)

`--dry-run`

Bir şablon oluşturulmasına neden olacaksa, verilen komutun çalıştırılması durumunda ne olacağını gösteren bir Özet görüntüler.

`--force`

Var olan dosyaları değiştirebilse bile içeriğin oluşturulmasını zorlar. Çıkış dizini zaten bir proje içerdiğinde bu gereklidir.

`-h|--help`

Komut için yardım yazdırır. `dotnet new` Komutun kendisi veya gibi herhangi bir şablon `dotnet new mvc --help`için çağrılabilir.

`-i|--install <PATH|NUGET_ID>`

`PATH` Veya`NUGET_ID` tarafından sağlanmış bir kaynak veya şablon paketi kurar. Şablon paketinin bir ön sürümü sürümünü yüklemek istiyorsanız, sürümü biçiminde `<package-name>::<package-version>`belirtmeniz gerekir. Varsayılan olarak, `dotnet new` en \* son kararlı paket sürümünü temsil eden sürüm için geçirir. [Örnekler](#examples) bölümündeki bir örneğe bakın.

Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz. [DotNet New Için özel şablonlar](custom-templates.md).

`-l|--list`

Belirtilen adı içeren şablonları listeler. `dotnet new` Komut için çağrılırsa, belirtilen dizin için kullanılabilir olabilecek şablonları listeler. Örneğin, dizin zaten bir proje içeriyorsa, tüm proje şablonlarını listeetmez.

`-lang|--language {C#|F#|VB}`

Oluşturulacak şablonun dili. Kabul edilen dil şablona göre değişir (bkz. [arguments](#arguments) bölümünde Varsayılanlar). Bazı şablonlar için geçerli değildir.

> [!NOTE]
> Bazı kabuklar `#` özel bir karakter olarak yorumlanır. Bu durumlarda, gibi dil parametre değerini `dotnet new console -lang "F#"`almalısınız.

`-n|--name <OUTPUT_NAME>`

Oluşturulan çıkışın adı. Ad belirtilmemişse, geçerli dizinin adı kullanılır.

`--nuget-source`

Yüklemesi sırasında kullanılacak bir NuGet kaynağını belirtir.

`-o|--output <OUTPUT_DIRECTORY>`

Oluşturulan çıkışın yerleştirileceği konum. Geçerli dizin varsayılandır.

`--type`

Şablonları kullanılabilir türlerine göre filtreler. Önceden tanımlanmış değerler şunlardır "proje", "öğe" veya "diğer".

`-u|--uninstall <PATH|NUGET_ID>`

`PATH` Veya`NUGET_ID` belirtilen bir kaynak veya şablon paketini kaldırır. `<PATH|NUGET_ID>` Değer hariç tutularak, yüklü olan tüm şablon paketleri ve bunlarla ilişkili şablonlar görüntülenir.

> [!NOTE]
> Bir `PATH`şablonu kullanarak kaldırmak için, yolu tam olarak nitelemeniz gerekir. Örneğin, *C:/kullanıcıları/\<Kullanıcı >/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak içeren klasörden *./GarciaSoftware.ConsoleTemplate.CSharp* olmayacaktır.
> Ayrıca, şablon yolunuza son Sonlandırıcı Dizin eğik çizgi eklemeyin.

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

`--force`

Var olan dosyaları değiştirebilse bile içeriğin oluşturulmasını zorlar. Çıkış dizini zaten bir proje içerdiğinde bu gereklidir.

`-h|--help`

Komut için yardım yazdırır. `dotnet new` Komutun kendisi veya gibi herhangi bir şablon `dotnet new mvc --help`için çağrılabilir.

`-i|--install <PATH|NUGET_ID>`

`PATH` Veya`NUGET_ID` tarafından sağlanmış bir kaynak veya şablon paketi kurar. Şablon paketinin bir ön sürümü sürümünü yüklemek istiyorsanız, sürümü biçiminde `<package-name>::<package-version>`belirtmeniz gerekir. Varsayılan olarak, `dotnet new` en \* son kararlı paket sürümünü temsil eden sürüm için geçirir. [Örnekler](#examples) bölümündeki bir örneğe bakın.

Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz. [DotNet New Için özel şablonlar](custom-templates.md).

`-l|--list`

Belirtilen adı içeren şablonları listeler. `dotnet new` Komut için çağrılırsa, belirtilen dizin için kullanılabilir olabilecek şablonları listeler. Örneğin, dizin zaten bir proje içeriyorsa, tüm proje şablonlarını listeetmez.

`-lang|--language {C#|F#|VB}`

Oluşturulacak şablonun dili. Kabul edilen dil şablona göre değişir (bkz. [arguments](#arguments) bölümünde Varsayılanlar). Bazı şablonlar için geçerli değildir.

> [!NOTE]
> Bazı kabuklar `#` özel bir karakter olarak yorumlanır. Bu durumlarda, gibi dil parametre değerini `dotnet new console -lang "F#"`almalısınız.

`-n|--name <OUTPUT_NAME>`

Oluşturulan çıkışın adı. Ad belirtilmemişse, geçerli dizinin adı kullanılır.

`--nuget-source`

Yüklemesi sırasında kullanılacak bir NuGet kaynağını belirtir.

`-o|--output <OUTPUT_DIRECTORY>`

Oluşturulan çıkışın yerleştirileceği konum. Geçerli dizin varsayılandır.

`--type`

Şablonları kullanılabilir türlerine göre filtreler. Önceden tanımlanmış değerler şunlardır "proje", "öğe" veya "diğer".

`-u|--uninstall <PATH|NUGET_ID>`

`PATH` Veya`NUGET_ID` belirtilen bir kaynak veya şablon paketini kaldırır.

> [!NOTE]
> Bir `PATH`şablonu kullanarak kaldırmak için, yolu tam olarak nitelemeniz gerekir. Örneğin, *C:/kullanıcıları/\<Kullanıcı >/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak içeren klasörden *./GarciaSoftware.ConsoleTemplate.CSharp* olmayacaktır.
> Ayrıca, şablon yolunuza son Sonlandırıcı Dizin eğik çizgi eklemeyin.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2,0](#tab/netcore20)

`--force`

Var olan dosyaları değiştirebilse bile içeriğin oluşturulmasını zorlar. Çıkış dizini zaten bir proje içerdiğinde bu gereklidir.

`-h|--help`

Komut için yardım yazdırır. `dotnet new` Komutun kendisi veya gibi herhangi bir şablon `dotnet new mvc --help`için çağrılabilir.

`-i|--install <PATH|NUGET_ID>`

`PATH` Veya`NUGET_ID` tarafından sağlanmış bir kaynak veya şablon paketi kurar. Şablon paketinin bir ön sürümü sürümünü yüklemek istiyorsanız, sürümü biçiminde `<package-name>::<package-version>`belirtmeniz gerekir. Varsayılan olarak, `dotnet new` en \* son kararlı paket sürümünü temsil eden sürüm için geçirir. [Örnekler](#examples) bölümündeki bir örneğe bakın.

Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz. [DotNet New Için özel şablonlar](custom-templates.md).

`-l|--list`

Belirtilen adı içeren şablonları listeler. `dotnet new` Komut için çağrılırsa, belirtilen dizin için kullanılabilir olabilecek şablonları listeler. Örneğin, dizin zaten bir proje içeriyorsa, tüm proje şablonlarını listeetmez.

`-lang|--language {C#|F#|VB}`

Oluşturulacak şablonun dili. Kabul edilen dil şablona göre değişir (bkz. [arguments](#arguments) bölümünde Varsayılanlar). Bazı şablonlar için geçerli değildir.

> [!NOTE]
> Bazı kabuklar `#` özel bir karakter olarak yorumlanır. Bu durumlarda, gibi dil parametre değerini `dotnet new console -lang "F#"`almalısınız.

`-n|--name <OUTPUT_NAME>`

Oluşturulan çıkışın adı. Ad belirtilmemişse, geçerli dizinin adı kullanılır.

`-o|--output <OUTPUT_DIRECTORY>`

Oluşturulan çıkışın yerleştirileceği konum. Geçerli dizin varsayılandır.

`--type`

Şablonları kullanılabilir türlerine göre filtreler. Önceden tanımlanmış değerler şunlardır "proje", "öğe" veya "diğer".

`-u|--uninstall <PATH|NUGET_ID>`

`PATH` Veya`NUGET_ID` belirtilen bir kaynak veya şablon paketini kaldırır.

> [!NOTE]
> Bir kaynağı `PATH`kullanarak bir şablonu kaldırmak için yolu tam olarak nitelemeniz gerekir. Örneğin, *C:/kullanıcıları/\<Kullanıcı >/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak içeren klasörden *./GarciaSoftware.ConsoleTemplate.CSharp* olmayacaktır. Ayrıca, şablon yolunuza son Sonlandırıcı Dizin eğik çizgi eklemeyin.
> 
> Bir şablonu kaldırmak için gereken `PATH` veya `NUGET_ID` bağımsız değişkeni belirleyemıyorsanız, bağımsız değişken olmadan çalıştırıldığında `dotnet new --uninstall` , tüm yüklü şablonlar ve bunları kaldırmak için gereken bağımsız değişken listelenir.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1. x](#tab/netcore1x)

`-all|--show-all`

Yalnızca `dotnet new` komutun bağlamında çalışırken belirli bir proje türü için tüm şablonları gösterir. Gibi belirli bir şablon `dotnet new web -all`bağlamında çalıştırılırken, `-all` zorla oluşturma bayrağı olarak yorumlanır. Çıkış dizini zaten bir proje içerdiğinde bu gereklidir.

`-h|--help`

Komut için yardım yazdırır. `dotnet new` Komutun kendisi veya gibi herhangi bir şablon `dotnet new mvc --help`için çağrılabilir.

`-l|--list`

Belirtilen adı içeren şablonları listeler. `dotnet new` Komut için çağrılırsa, belirtilen dizin için kullanılabilir olabilecek şablonları listeler. Örneğin, dizin zaten bir proje içeriyorsa, tüm proje şablonlarını listeetmez.

`-lang|--language {C#|F#}`

Oluşturulacak şablonun dili. Kabul edilen dil şablona göre değişir (bkz. [arguments](#arguments) bölümünde Varsayılanlar). Bazı şablonlar için geçerli değildir.

> [!NOTE]
> Bazı kabuklar `#` özel bir karakter olarak yorumlanır. Bu durumlarda, gibi dil parametre değerini `dotnet new console -lang "F#"`almalısınız.

`-n|--name <OUTPUT_NAME>`

Oluşturulan çıkışın adı. Ad belirtilmemişse, geçerli dizinin adı kullanılır.

`-o|--output <OUTPUT_DIRECTORY>`

Oluşturulan çıkışın yerleştirileceği konum. Geçerli dizin varsayılandır.

---

## <a name="template-options"></a>Şablon seçenekleri

Her proje şablonunda ek seçenekler bulunabilir. Çekirdek şablonlar aşağıdaki ek seçeneklere sahiptir:

# <a name="net-core-22tabnetcore22"></a>[.NET Core 2,2](#tab/netcore22)

**konsola**

`--langVersion <VERSION_NUMBER>`-Oluşturulan proje `LangVersion` dosyasındaki özelliği ayarlar. Örneğin, 7,3 kullanmak `--langVersion 7.3` C# için kullanın. İçin F#desteklenmez.

`--no-restore`-Proje oluşturma sırasında örtük geri yükleme yürütülmez.

**Angular, tepki, reactredux**

`--exclude-launch-settings`- *Launchsettings. JSON* öğesini oluşturulan şablondan hariç tutun.

`--no-restore`-Proje oluşturma sırasında örtük geri yükleme yürütülmez.

`--no-https`-Proje HTTPS gerektirmez. Bu seçenek yalnızca `IndividualAuth` veya `OrganizationalAuth` kullanılmıyorsa geçerlidir.

**razorclasslib**

`--no-restore`-Proje oluşturma sırasında örtük geri yükleme yürütülmez.

**projesinin**

`-f|--framework <FRAMEWORK>`-Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir. Değerler: `netcoreapp2.2` bir .NET Core sınıf kitaplığı oluşturmak veya `netstandard2.0` bir .NET Standard sınıf kitaplığı oluşturmak için. Varsayılan değer `netstandard2.0` şeklindedir.

`--langVersion <VERSION_NUMBER>`-Oluşturulan proje `LangVersion` dosyasındaki özelliği ayarlar. Örneğin, 7,3 kullanmak `--langVersion 7.3` C# için kullanın. İçin F#desteklenmez.

`--no-restore`-Proje oluşturma sırasında örtük geri yükleme yürütülmez.

**MSTest, xUnit**

`-p|--enable-pack`- [DotNet Pack](dotnet-pack.md)kullanarak proje için paketlemeyi etkinleştirilir.

`--no-restore`-Proje oluşturma sırasında örtük geri yükleme yürütülmez.

**NUnit**

`-f|--framework <FRAMEWORK>`-Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir. Varsayılan değer `netcoreapp2.1` şeklindedir.

`-p|--enable-pack`- [DotNet Pack](dotnet-pack.md)kullanarak proje için paketlemeyi etkinleştirilir.

`--no-restore`-Proje oluşturma sırasında örtük geri yükleme yürütülmez.

**sayfasında**

`-na|--namespace <NAMESPACE_NAME>`-Oluşturulan kod için ad alanı. Varsayılan değer `MyApp.Namespace` şeklindedir.

`-np|--no-pagemodel`-Sayfayı PageModel olmadan oluşturur.

**viewıtems 'lar**

`-na|--namespace <NAMESPACE_NAME>`-Oluşturulan kod için ad alanı. Varsayılan değer `MyApp.Namespace` şeklindedir.

**Web**

`--exclude-launch-settings`- *Launchsettings. JSON* öğesini oluşturulan şablondan hariç tutun.

`--no-restore`-Proje oluşturma sırasında örtük geri yükleme yürütülmez.

`--no-https`-Proje HTTPS gerektirmez. Bu seçenek yalnızca `IndividualAuth` veya `OrganizationalAuth` kullanılmıyorsa geçerlidir.

**MVC, WebApp**

`-au|--auth <AUTHENTICATION_TYPE>`-Kullanılacak kimlik doğrulaması türü. Olası değerler şunlardır:

- `None`-Kimlik doğrulaması yok (varsayılan).
- `Individual`-Bireysel kimlik doğrulama.
- `IndividualB2C`-Azure AD B2C ile bireysel kimlik doğrulama.
- `SingleOrg`-Tek bir kiracı için kuruluş kimlik doğrulaması.
- `MultiOrg`-Birden çok kiracı için kuruluş kimlik doğrulaması.
- `Windows`-Windows kimlik doğrulaması.

`--aad-b2c-instance <INSTANCE>`-Bağlanılacak Azure Active Directory B2C örneği. `IndividualB2C` Kimlik doğrulamasıyla kullanın. Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.

`-ssp|--susi-policy-id <ID>`-Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI. `IndividualB2C` Kimlik doğrulamasıyla kullanın.

`-rp|--reset-password-policy-id <ID>`-Bu proje için parola sıfırlama ilkesi KIMLIĞI. `IndividualB2C` Kimlik doğrulamasıyla kullanın.

`-ep|--edit-profile-policy-id <ID>`-Bu proje için profil ilkesi KIMLIĞINI Düzenle. `IndividualB2C` Kimlik doğrulamasıyla kullanın.

`--aad-instance <INSTANCE>`-Bağlanılacak Azure Active Directory örneği. `SingleOrg` Veya`MultiOrg` kimlik doğrulamasıyla kullanın. Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.

`--client-id <ID>`-Bu projenin Istemci KIMLIĞI. `IndividualB2C`, Veyakimlik`MultiOrg`doğrulamasıylakullanın. `SingleOrg` Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.

`--domain <DOMAIN>`-Dizin kiracının etki alanı. `SingleOrg` Veya`IndividualB2C` kimlik doğrulamasıyla kullanın. Varsayılan değer `qualified.domain.name` şeklindedir.

`--tenant-id <ID>`-Bağlanılacak dizinin Tenantıd KIMLIĞI. `SingleOrg` Kimlik doğrulamasıyla kullanın. Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.

`--callback-path <PATH>`-Uygulamanın yeniden yönlendirme URI 'sinin temel yolu içindeki istek yolu. `SingleOrg` Veya`IndividualB2C` kimlik doğrulamasıyla kullanın. Varsayılan değer `/signin-oidc` şeklindedir.

`-r|--org-read-access`-Bu uygulamanın dizine okuma erişimi sağlar. Yalnızca veya `SingleOrg` `MultiOrg` kimlik doğrulaması için geçerlidir.

`--exclude-launch-settings`- *Launchsettings. JSON* öğesini oluşturulan şablondan hariç tutun.

`--no-https`-Proje HTTPS gerektirmez. `app.UseHsts`ve `app.UseHttpsRedirection` öğesine`Startup.Configure`eklenmez. Bu `Individual`seçenek yalnızca `IndividualB2C` `MultiOrg` , ,,veyakullanılmıyorsageçerlidir.`SingleOrg`

`-uld|--use-local-db`-SQLite yerine LocalDB kullanılması gerektiğini belirtir. Yalnızca veya `Individual` `IndividualB2C` kimlik doğrulaması için geçerlidir.

`--no-restore`-Proje oluşturma sırasında örtük geri yükleme yürütülmez.

**WebApi**

`-au|--auth <AUTHENTICATION_TYPE>`-Kullanılacak kimlik doğrulaması türü. Olası değerler şunlardır:

- `None`-Kimlik doğrulaması yok (varsayılan).
- `IndividualB2C`-Azure AD B2C ile bireysel kimlik doğrulama.
- `SingleOrg`-Tek bir kiracı için kuruluş kimlik doğrulaması.
- `Windows`-Windows kimlik doğrulaması.

`--aad-b2c-instance <INSTANCE>`-Bağlanılacak Azure Active Directory B2C örneği. `IndividualB2C` Kimlik doğrulamasıyla kullanın. Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.

`-ssp|--susi-policy-id <ID>`-Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI. `IndividualB2C` Kimlik doğrulamasıyla kullanın.

`--aad-instance <INSTANCE>`-Bağlanılacak Azure Active Directory örneği. `SingleOrg` Kimlik doğrulamasıyla kullanın. Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.

`--client-id <ID>`-Bu projenin Istemci KIMLIĞI. `IndividualB2C` Veya`SingleOrg` kimlik doğrulamasıyla kullanın. Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.

`--domain <DOMAIN>`-Dizin kiracının etki alanı. `SingleOrg` Veya`IndividualB2C` kimlik doğrulamasıyla kullanın. Varsayılan değer `qualified.domain.name` şeklindedir.

`--tenant-id <ID>`-Bağlanılacak dizinin Tenantıd KIMLIĞI. `SingleOrg` Kimlik doğrulamasıyla kullanın. Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.

`-r|--org-read-access`-Bu uygulamanın dizine okuma erişimi sağlar. Yalnızca veya `SingleOrg` `MultiOrg` kimlik doğrulaması için geçerlidir.

`--exclude-launch-settings`- *Launchsettings. JSON* öğesini oluşturulan şablondan hariç tutun.

`--no-https`-Proje HTTPS gerektirmez. `app.UseHsts`ve `app.UseHttpsRedirection` öğesine`Startup.Configure`eklenmez. Bu `Individual`seçenek yalnızca `IndividualB2C` `MultiOrg` , ,,veyakullanılmıyorsageçerlidir.`SingleOrg`

`-uld|--use-local-db`-SQLite yerine LocalDB kullanılması gerektiğini belirtir. Yalnızca veya `Individual` `IndividualB2C` kimlik doğrulaması için geçerlidir.

`--no-restore`-Proje oluşturma sırasında örtük geri yükleme yürütülmez.

**globaljson**

`--sdk-version <VERSION_NUMBER>`- *Global. JSON* dosyasında kullanılacak .NET Core SDK sürümünü belirtir.

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

**konsol, angular, tepki, reactredux, razorclasslib**

`--no-restore`-Proje oluşturma sırasında örtük geri yükleme yürütülmez.

**projesinin**

`-f|--framework <FRAMEWORK>`-Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir. Değerler: `netcoreapp2.1` bir .NET Core sınıf kitaplığı oluşturmak veya `netstandard2.0` bir .NET Standard sınıf kitaplığı oluşturmak için. Varsayılan değer `netstandard2.0` şeklindedir.

`--no-restore`-Proje oluşturma sırasında örtük geri yükleme yürütülmez.

**MSTest, xUnit**

`-p|--enable-pack`- [DotNet Pack](dotnet-pack.md)kullanarak proje için paketlemeyi etkinleştirilir.

`--no-restore`-Proje oluşturma sırasında örtük geri yükleme yürütülmez.

**globaljson**

`--sdk-version <VERSION_NUMBER>`- *Global. JSON* dosyasında kullanılacak .NET Core SDK sürümünü belirtir.

**Web**

`--exclude-launch-settings`- *Launchsettings. JSON* öğesini oluşturulan şablondan hariç tutun.

`--no-restore`-Proje oluşturma sırasında örtük geri yükleme yürütülmez.

`--no-https`-Proje HTTPS gerektirmez. Bu seçenek yalnızca `IndividualAuth` veya `OrganizationalAuth` kullanılmıyorsa geçerlidir.

**WebApi**

`-au|--auth <AUTHENTICATION_TYPE>`-Kullanılacak kimlik doğrulaması türü. Olası değerler şunlardır:

- `None`-Kimlik doğrulaması yok (varsayılan).
- `IndividualB2C`-Azure AD B2C ile bireysel kimlik doğrulama.
- `SingleOrg`-Tek bir kiracı için kuruluş kimlik doğrulaması.
- `Windows`-Windows kimlik doğrulaması.

`--aad-b2c-instance <INSTANCE>`-Bağlanılacak Azure Active Directory B2C örneği. `IndividualB2C` Kimlik doğrulamasıyla kullanın. Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.

`-ssp|--susi-policy-id <ID>`-Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI. `IndividualB2C` Kimlik doğrulamasıyla kullanın.

`--aad-instance <INSTANCE>`-Bağlanılacak Azure Active Directory örneği. `SingleOrg` Kimlik doğrulamasıyla kullanın. Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.

`--client-id <ID>`-Bu projenin Istemci KIMLIĞI. `IndividualB2C` Veya`SingleOrg` kimlik doğrulamasıyla kullanın. Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.

`--domain <DOMAIN>`-Dizin kiracının etki alanı. `SingleOrg` Veya`IndividualB2C` kimlik doğrulamasıyla kullanın. Varsayılan değer `qualified.domain.name` şeklindedir.

`--tenant-id <ID>`-Bağlanılacak dizinin Tenantıd KIMLIĞI. `SingleOrg` Kimlik doğrulamasıyla kullanın. Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.

`-r|--org-read-access`-Bu uygulamanın dizine okuma erişimi sağlar. Yalnızca veya `SingleOrg` `MultiOrg` kimlik doğrulaması için geçerlidir.

`--exclude-launch-settings`- *Launchsettings. JSON* öğesini oluşturulan şablondan hariç tutun.

`-uld|--use-local-db`-SQLite yerine LocalDB kullanılması gerektiğini belirtir. Yalnızca veya `Individual` `IndividualB2C` kimlik doğrulaması için geçerlidir.

`--no-restore`-Proje oluşturma sırasında örtük geri yükleme yürütülmez.

`--no-https`-Proje HTTPS gerektirmez. `app.UseHsts`ve `app.UseHttpsRedirection` öğesine`Startup.Configure`eklenmez. Bu `Individual`seçenek yalnızca `IndividualB2C` `MultiOrg` , ,,veyakullanılmıyorsageçerlidir.`SingleOrg`

**MVC, Razor**

`-au|--auth <AUTHENTICATION_TYPE>`-Kullanılacak kimlik doğrulaması türü. Olası değerler şunlardır:

- `None`-Kimlik doğrulaması yok (varsayılan).
- `Individual`-Bireysel kimlik doğrulama.
- `IndividualB2C`-Azure AD B2C ile bireysel kimlik doğrulama.
- `SingleOrg`-Tek bir kiracı için kuruluş kimlik doğrulaması.
- `MultiOrg`-Birden çok kiracı için kuruluş kimlik doğrulaması.
- `Windows`-Windows kimlik doğrulaması.

`--aad-b2c-instance <INSTANCE>`-Bağlanılacak Azure Active Directory B2C örneği. `IndividualB2C` Kimlik doğrulamasıyla kullanın. Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.

`-ssp|--susi-policy-id <ID>`-Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI. `IndividualB2C` Kimlik doğrulamasıyla kullanın.

`-rp|--reset-password-policy-id <ID>`-Bu proje için parola sıfırlama ilkesi KIMLIĞI. `IndividualB2C` Kimlik doğrulamasıyla kullanın.

`-ep|--edit-profile-policy-id <ID>`-Bu proje için profil ilkesi KIMLIĞINI Düzenle. `IndividualB2C` Kimlik doğrulamasıyla kullanın.

`--aad-instance <INSTANCE>`-Bağlanılacak Azure Active Directory örneği. `SingleOrg` Veya`MultiOrg` kimlik doğrulamasıyla kullanın. Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.

`--client-id <ID>`-Bu projenin Istemci KIMLIĞI. `IndividualB2C`, Veyakimlik`MultiOrg`doğrulamasıylakullanın. `SingleOrg` Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.

`--domain <DOMAIN>`-Dizin kiracının etki alanı. `SingleOrg` Veya`IndividualB2C` kimlik doğrulamasıyla kullanın. Varsayılan değer `qualified.domain.name` şeklindedir.

`--tenant-id <ID>`-Bağlanılacak dizinin Tenantıd KIMLIĞI. `SingleOrg` Kimlik doğrulamasıyla kullanın. Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.

`--callback-path <PATH>`-Uygulamanın yeniden yönlendirme URI 'sinin temel yolu içindeki istek yolu. `SingleOrg` Veya`IndividualB2C` kimlik doğrulamasıyla kullanın. Varsayılan değer `/signin-oidc` şeklindedir.

`-r|--org-read-access`-Bu uygulamanın dizine okuma erişimi sağlar. Yalnızca veya `SingleOrg` `MultiOrg` kimlik doğrulaması için geçerlidir.

`--exclude-launch-settings`- *Launchsettings. JSON* öğesini oluşturulan şablondan hariç tutun.

`--use-browserlink`-Projedeki BrowserLink öğesini içerir.

`-uld|--use-local-db`-SQLite yerine LocalDB kullanılması gerektiğini belirtir. Yalnızca veya `Individual` `IndividualB2C` kimlik doğrulaması için geçerlidir.

`--no-restore`-Proje oluşturma sırasında örtük geri yükleme yürütülmez.

`--no-https`-Proje HTTPS gerektirmez. `app.UseHsts`ve `app.UseHttpsRedirection` öğesine`Startup.Configure`eklenmez. Bu `Individual`seçenek yalnızca `IndividualB2C` `MultiOrg` , ,,veyakullanılmıyorsageçerlidir.`SingleOrg`

**sayfasında**

`-na|--namespace <NAMESPACE_NAME>`-Oluşturulan kod için ad alanı. Varsayılan değer `MyApp.Namespace` şeklindedir.

`-np|--no-pagemodel`-Sayfayı PageModel olmadan oluşturur.

**viewıtems 'lar**

`-na|--namespace <NAMESPACE_NAME>`-Oluşturulan kod için ad alanı. Varsayılan değer `MyApp.Namespace` şeklindedir.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2,0](#tab/netcore20)

**konsol, angular, tepki, reactredux**

`--no-restore`-Proje oluşturma sırasında örtük geri yükleme yürütülmez.

**projesinin**

`-f|--framework <FRAMEWORK>`-Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir. Değerler: `netcoreapp2.0` bir .NET Core sınıf kitaplığı oluşturmak veya `netstandard2.0` bir .NET Standard sınıf kitaplığı oluşturmak için. Varsayılan değer `netstandard2.0` şeklindedir.

`--no-restore`-Proje oluşturma sırasında örtük geri yükleme yürütülmez.

**MSTest, xUnit**

`-p|--enable-pack`- [DotNet Pack](dotnet-pack.md)kullanarak proje için paketlemeyi etkinleştirilir.

`--no-restore`-Proje oluşturma sırasında örtük geri yükleme yürütülmez.

**globaljson**

`--sdk-version <VERSION_NUMBER>`- *Global. JSON* dosyasında kullanılacak .NET Core SDK sürümünü belirtir.

**Web**

`--use-launch-settings`-Oluşturulan şablon çıkışında *Launchsettings. JSON* öğesini içerir.

`--no-restore`-Proje oluşturma sırasında örtük geri yükleme yürütülmez.

**WebApi**

`-au|--auth <AUTHENTICATION_TYPE>`-Kullanılacak kimlik doğrulaması türü. Olası değerler şunlardır:

- `None`-Kimlik doğrulaması yok (varsayılan).
- `IndividualB2C`-Azure AD B2C ile bireysel kimlik doğrulama.
- `SingleOrg`-Tek bir kiracı için kuruluş kimlik doğrulaması.
- `Windows`-Windows kimlik doğrulaması.

`--aad-b2c-instance <INSTANCE>`-Bağlanılacak Azure Active Directory B2C örneği. `IndividualB2C` Kimlik doğrulamasıyla kullanın. Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.

`-ssp|--susi-policy-id <ID>`-Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI. `IndividualB2C` Kimlik doğrulamasıyla kullanın.

`--aad-instance <INSTANCE>`-Bağlanılacak Azure Active Directory örneği. `SingleOrg` Kimlik doğrulamasıyla kullanın. Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.

`--client-id <ID>`-Bu projenin Istemci KIMLIĞI. `IndividualB2C` Veya`SingleOrg` kimlik doğrulamasıyla kullanın. Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.

`--domain <DOMAIN>`-Dizin kiracının etki alanı. `SingleOrg` Veya`IndividualB2C` kimlik doğrulamasıyla kullanın. Varsayılan değer `qualified.domain.name` şeklindedir.

`--tenant-id <ID>`-Bağlanılacak dizinin Tenantıd KIMLIĞI. `SingleOrg` Kimlik doğrulamasıyla kullanın. Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.

`-r|--org-read-access`-Bu uygulamanın dizine okuma erişimi sağlar. Yalnızca veya `SingleOrg` `MultiOrg` kimlik doğrulaması için geçerlidir.

`--use-launch-settings`-Oluşturulan şablon çıkışında *Launchsettings. JSON* öğesini içerir.

`-uld|--use-local-db`-SQLite yerine LocalDB kullanılması gerektiğini belirtir. Yalnızca veya `Individual` `IndividualB2C` kimlik doğrulaması için geçerlidir.

`--no-restore`-Proje oluşturma sırasında örtük geri yükleme yürütülmez.

**MVC, Razor**

`-au|--auth <AUTHENTICATION_TYPE>`-Kullanılacak kimlik doğrulaması türü. Olası değerler şunlardır:

- `None`-Kimlik doğrulaması yok (varsayılan).
- `Individual`-Bireysel kimlik doğrulama.
- `IndividualB2C`-Azure AD B2C ile bireysel kimlik doğrulama.
- `SingleOrg`-Tek bir kiracı için kuruluş kimlik doğrulaması.
- `MultiOrg`-Birden çok kiracı için kuruluş kimlik doğrulaması.
- `Windows`-Windows kimlik doğrulaması.

`--aad-b2c-instance <INSTANCE>`-Bağlanılacak Azure Active Directory B2C örneği. `IndividualB2C` Kimlik doğrulamasıyla kullanın. Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.

`-ssp|--susi-policy-id <ID>`-Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI. `IndividualB2C` Kimlik doğrulamasıyla kullanın.

`-rp|--reset-password-policy-id <ID>`-Bu proje için parola sıfırlama ilkesi KIMLIĞI. `IndividualB2C` Kimlik doğrulamasıyla kullanın.

`-ep|--edit-profile-policy-id <ID>`-Bu proje için profil ilkesi KIMLIĞINI Düzenle. `IndividualB2C` Kimlik doğrulamasıyla kullanın.

`--aad-instance <INSTANCE>`-Bağlanılacak Azure Active Directory örneği. `SingleOrg` Veya`MultiOrg` kimlik doğrulamasıyla kullanın. Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.

`--client-id <ID>`-Bu projenin Istemci KIMLIĞI. `IndividualB2C`, Veyakimlik`MultiOrg`doğrulamasıylakullanın. `SingleOrg` Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.

`--domain <DOMAIN>`-Dizin kiracının etki alanı. `SingleOrg` Veya`IndividualB2C` kimlik doğrulamasıyla kullanın. Varsayılan değer `qualified.domain.name` şeklindedir.

`--tenant-id <ID>`-Bağlanılacak dizinin Tenantıd KIMLIĞI. `SingleOrg` Kimlik doğrulamasıyla kullanın. Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.

`--callback-path <PATH>`-Uygulamanın yeniden yönlendirme URI 'sinin temel yolu içindeki istek yolu. `SingleOrg` Veya`IndividualB2C` kimlik doğrulamasıyla kullanın. Varsayılan değer `/signin-oidc` şeklindedir.

`-r|--org-read-access`-Bu uygulamanın dizine okuma erişimi sağlar. Yalnızca veya `SingleOrg` `MultiOrg` kimlik doğrulaması için geçerlidir.

`--use-launch-settings`-Oluşturulan şablon çıkışında *Launchsettings. JSON* öğesini içerir.

`--use-browserlink`-Projedeki BrowserLink öğesini içerir.

`-uld|--use-local-db`-SQLite yerine LocalDB kullanılması gerektiğini belirtir. Yalnızca veya `Individual` `IndividualB2C` kimlik doğrulaması için geçerlidir.

`--no-restore`-Proje oluşturma sırasında örtük geri yükleme yürütülmez.

**sayfasında**

`-na|--namespace <NAMESPACE_NAME>`-Oluşturulan kod için ad alanı. Varsayılan değer `MyApp.Namespace` şeklindedir.

`-np|--no-pagemodel`-Sayfayı PageModel olmadan oluşturur.

**viewıtems 'lar**

`-na|--namespace <NAMESPACE_NAME>`-Oluşturulan kod için ad alanı. Varsayılan değer `MyApp.Namespace` şeklindedir.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1. x](#tab/netcore1x)

**konsol, xUnit, MSTest, Web, WebApi**

`-f|--framework <FRAMEWORK>`-Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir. Değerler: `netcoreapp1.0` veya `netcoreapp1.1`. Varsayılan değer `netcoreapp1.0` şeklindedir.

**projesinin**

`-f|--framework <FRAMEWORK>`-Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir. Değerler: `netcoreapp1.0`, `netcoreapp1.1`, veya `netstandard1.0` .`netstandard1.6` Varsayılan değer `netstandard1.4` şeklindedir.

**mvc**

`-f|--framework <FRAMEWORK>`-Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir. Değerler: `netcoreapp1.0` veya `netcoreapp1.1`. Varsayılan değer `netcoreapp1.0` şeklindedir.

`-au|--auth <AUTHENTICATION_TYPE>`-Kullanılacak kimlik doğrulaması türü. Değerler: `None` veya `Individual`. Varsayılan değer `None` şeklindedir.

`-uld|--use-local-db`-SQLite yerine LocalDB kullanılıp kullanılmayacağını belirtir. Değerler: `true` veya `false`. Varsayılan değer `false` şeklindedir.

---

## <a name="examples"></a>Örnekler

Şablon adını C# belirterek bir konsol uygulaması projesi oluşturun:

`dotnet new "Console Application"`

Geçerli dizinde F# bir konsol uygulaması projesi oluşturun:

`dotnet new console -lang F#`

Belirtilen dizinde bir .NET Standard sınıf kitaplığı projesi oluşturun (yalnızca .NET Core SDK 2,0 veya sonraki sürümlerle kullanılabilir):

`dotnet new classlib -lang VB -o MyLibrary`

Geçerli dizinde kimlik doğrulaması C# olmadan yeni bir ASP.NET Core MVC projesi oluşturun:

`dotnet new mvc -au None`

Yeni bir xUnit projesi oluştur:

`dotnet new xunit`

MVC için kullanılabilen tüm şablonları listeleyin:

`dotnet new mvc -l`

*We* alt dizeniz ile eşleşen tüm şablonları listeleyin. Tam eşleşme bulunamadı, bu nedenle alt dize eşleştirmesi hem kısa ad hem de ad sütunlarında çalışır.

`dotnet new we -l`

Şablonla eşleşen şablonu çağırma girişimi. Tek bir eşleşme belirlenemiyorsa kısmi eşleşen şablonları listeleyin.

`dotnet new ng`

ASP.NET Core için tek sayfalı uygulama şablonlarının 2,0 sürümünü (yalnızca .NET Core SDK 1,1 ve sonraki sürümler için kullanılabilir) (komut seçeneği) yükler:

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

SDK sürümü 2.0.0 (yalnızca .NET Core SDK 2,0 veya üzeri sürümlerle kullanılabilir) ayarı geçerli dizinde *Global. JSON* oluşturun:

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a>Ayrıca bkz.

- [DotNet New için özel şablonlar](custom-templates.md)
- [Dotnet new için özel şablon oluşturma](../tutorials/create-custom-template.md)
- [DotNet/DotNet-şablon-örnek GitHub deposu](https://github.com/dotnet/dotnet-template-samples)
- [DotNet New için kullanılabilir şablonlar](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
