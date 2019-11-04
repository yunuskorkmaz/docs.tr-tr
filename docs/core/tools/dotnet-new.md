---
title: DotNet yeni komut
description: DotNet New komutu, belirtilen şablona göre yeni .NET Core projeleri oluşturur.
ms.date: 05/06/2019
ms.openlocfilehash: c9529e135f48c80f445c91038294a3e7266486f1
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73420472"
---
# <a name="dotnet-new"></a>dotnet new

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Name

`dotnet new`-belirtilen şablona göre yeni bir proje, yapılandırma dosyası veya çözüm oluşturur.

## <a name="synopsis"></a>Özeti

<!-- markdownlint-disable MD025 -->

# <a name="net-core-22tabnetcore22"></a>[.NET Core 2,2](#tab/netcore22)

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

```dotnetcli
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2,0](#tab/netcore20)

```dotnetcli
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1. x](#tab/netcore1x)

```dotnetcli
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a>Açıklama

`dotnet new` komutu, geçerli bir .NET Core projesi başlatmak için kullanışlı bir yol sağlar.

Komutu, belirtilen şablon ve seçeneklere göre diskteki yapıtları oluşturmak için [şablon altyapısını](https://github.com/dotnet/templating) çağırır.

## <a name="arguments"></a>Arguments

`TEMPLATE`

Komut çağrıldığında örnek oluşturulacak şablon. Her şablonun geçirebilmeniz için özel seçenekleri olabilir. Daha fazla bilgi için bkz. [şablon seçenekleri](#template-options).

`TEMPLATE` değeri **Şablonlar** veya **kısa ad** sütunundaki metin üzerinde tam eşleşme değilse, bu iki sütunda bir alt dize eşleşmesi gerçekleştirilir.

# <a name="net-core-22tabnetcore22"></a>[.NET Core 2,2](#tab/netcore22)

Komut, şablonların varsayılan bir listesini içerir. Kullanılabilir şablonların bir listesini almak için `dotnet new -l` kullanın. Aşağıdaki tabloda, .NET Core SDK 2.2.100 ile önceden yüklenmiş olarak gelen şablonlar gösterilmektedir. Şablon için varsayılan dil, köşeli ayraçlar içinde gösterilir.

| Şablonlar                                    | Kısa Ad        | Dil     | Etiketler                                  |
|----------------------------------------------|-------------------|--------------|---------------------------------------|
| Konsol Uygulaması                          | `console`         | [C#], F#Vb. | Ortak/konsol                        |
| Sınıf kitaplığı                                | `classlib`        | [C#], F#Vb. | Ortak/Kitaplık                        |
| Birim testi projesi                            | `mstest`          | [C#], F#Vb. | Test/MSTest                           |
| NUnit 3 test projesi                         | `nunit`           | [C#], F#Vb. | Test/NUnit                            |
| NUnit 3 test öğesi                            | `nunit-test`      | [C#], F#Vb. | Test/NUnit                            |
| xUnit test projesi                           | `xunit`           | [C#], F#Vb. | Test/xUnit                            |
| Razor sayfası                                   | `page`            | [C#]         | Web/ASP. NET                           |
| MVC Viewıtemts                              | `viewimports`     | [C#]         | Web/ASP. NET                           |
| MVC ViewStart                                | `viewstart`       | [C#]         | Web/ASP. NET                           |
| ASP.NET Core boş                           | `web`             | [C#],F#     | Web/boş                             |
| ASP.NET Core Web uygulaması (Model-View-Controller) | `mvc`             | [C#],F#     | Web/MVC                               |
| ASP.NET Core Web uygulaması                         | `webapp`, `razor` | [C#]         | Web/MVC/Razor Pages                   |
| Angular ile ASP.NET Core                    | `angular`         | [C#]         | Web/MVC/SPA                           |
| Tepki verme. js ile ASP.NET Core                   | `react`           | [C#]         | Web/MVC/SPA                           |
| Yanıt verir. js ve Redux ile ASP.NET Core         | `reactredux`      | [C#]         | Web/MVC/SPA                           |
| Razor sınıf kitaplığı                          | `razorclasslib`   | [C#]         | Web/Razor/kitaplık/Razor sınıfı kitaplığı |
| ASP.NET Core Web API 'SI                         | `webapi`          | [C#],F#     | Web/WebAPI                            |
| Global. JSON dosyası                             | `globaljson`      |              | Config                                |
| NuGet yapılandırması                                 | `nugetconfig`     |              | Config                                |
| Web yapılandırması                                   | `webconfig`       |              | Config                                |
| Çözüm dosyası                                | `sln`             |              | Çözüm                              |

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

Komut, şablonların varsayılan bir listesini içerir. Kullanılabilir şablonların bir listesini almak için `dotnet new -l` kullanın. Aşağıdaki tabloda, .NET Core SDK 2.1.300 ile önceden yüklenmiş olarak gelen şablonlar gösterilmektedir. Şablon için varsayılan dil, köşeli ayraçlar içinde gösterilir.

| Şablonlar                                    | Kısa Ad      | Dil     | Etiketler                                  |
|----------------------------------------------|-----------------|--------------|---------------------------------------|
| Konsol Uygulaması                          | `console`       | [C#], F#Vb. | Ortak/konsol                        |
| Sınıf kitaplığı                                | `classlib`      | [C#], F#Vb. | Ortak/Kitaplık                        |
| Birim testi projesi                            | `mstest`        | [C#], F#Vb. | Test/MSTest                           |
| xUnit test projesi                           | `xunit`         | [C#], F#Vb. | Test/xUnit                            |
| Razor sayfası                                   | `page`          | [C#]         | Web/ASP. NET                           |
| MVC Viewıtemts                              | `viewimports`   | [C#]         | Web/ASP. NET                           |
| MVC ViewStart                                | `viewstart`     | [C#]         | Web/ASP. NET                           |
| ASP.NET Core boş                           | `web`           | [C#],F#     | Web/boş                             |
| ASP.NET Core Web uygulaması (Model-View-Controller) | `mvc`           | [C#],F#     | Web/MVC                               |
| ASP.NET Core Web uygulaması                         | `razor`         | [C#]         | Web/MVC/Razor Pages                   |
| Angular ile ASP.NET Core                    | `angular`       | [C#]         | Web/MVC/SPA                           |
| Tepki verme. js ile ASP.NET Core                   | `react`         | [C#]         | Web/MVC/SPA                           |
| Yanıt verir. js ve Redux ile ASP.NET Core         | `reactredux`    | [C#]         | Web/MVC/SPA                           | 
| Razor sınıf kitaplığı                          | `razorclasslib` | [C#]         | Web/Razor/kitaplık/Razor sınıfı kitaplığı |
| ASP.NET Core Web API 'SI                         | `webapi`        | [C#],F#     | Web/WebAPI                            |
| Global. JSON dosyası                             | `globaljson`    |              | Config                                |
| NuGet yapılandırması                                 | `nugetconfig`   |              | Config                                |
| Web yapılandırması                                   | `webconfig`     |              | Config                                |
| Çözüm dosyası                                | `sln`           |              | Çözüm                              |

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2,0](#tab/netcore20)

Komut, şablonların varsayılan bir listesini içerir. Kullanılabilir şablonların bir listesini almak için `dotnet new -l` kullanın. Aşağıdaki tabloda, .NET Core SDK 2.0.0 ile önceden yüklenmiş olarak gelen şablonlar gösterilmektedir. Şablon için varsayılan dil, köşeli ayraçlar içinde gösterilir.

| Şablonlar                                    | Kısa Ad    | Dil     | Etiketler                |
|----------------------------------------------|---------------|--------------|---------------------|
| Konsol Uygulaması                          | `console`     | [C#], F#Vb. | Ortak/konsol      |
| Sınıf kitaplığı                                | `classlib`    | [C#], F#Vb. | Ortak/Kitaplık      |
| Birim testi projesi                            | `mstest`      | [C#], F#Vb. | Test/MSTest         |
| xUnit test projesi                           | `xunit`       | [C#], F#Vb. | Test/xUnit          |
| ASP.NET Core boş                           | `web`         | [C#],F#     | Web/boş           |
| ASP.NET Core Web uygulaması (Model-View-Controller) | `mvc`         | [C#],F#     | Web/MVC             |
| ASP.NET Core Web uygulaması                         | `razor`       | [C#]         | Web/MVC/Razor Pages |
| Angular ile ASP.NET Core                    | `angular`     | [C#]         | Web/MVC/SPA         |
| Tepki verme. js ile ASP.NET Core                   | `react`       | [C#]         | Web/MVC/SPA         |
| Yanıt verir. js ve Redux ile ASP.NET Core         | `reactredux`  | [C#]         | Web/MVC/SPA         |
| ASP.NET Core Web API 'SI                         | `webapi`      | [C#],F#     | Web/WebAPI          |
| Global. JSON dosyası                             | `globaljson`  |              | Config              |
| NuGet yapılandırması                                 | `nugetconfig` |              | Config              |
| Web yapılandırması                                   | `webconfig`   |              | Config              |
| Çözüm dosyası                                | `sln`         |              | Çözüm            |
| Razor sayfası                                   | `page`        |              | Web/ASP. NET         |
| MVC Viewıtemts                              | `viewimports` |              | Web/ASP. NET         |
| MVC ViewStart                                | `viewstart`   |              | Web/ASP. NET         |

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1. x](#tab/netcore1x)

Komut, şablonların varsayılan bir listesini içerir. Kullanılabilir şablonların bir listesini almak için `dotnet new -all` kullanın. Aşağıdaki tabloda, .NET Core SDK 1.0.1 ile önceden yüklenmiş olarak gelen şablonlar gösterilmektedir. Şablon için varsayılan dil, köşeli ayraçlar içinde gösterilir.

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

Komut için yardım yazdırır. `dotnet new` komutun kendisi veya `dotnet new mvc --help`gibi herhangi bir şablon için çağrılabilir.

`-i|--install <PATH|NUGET_ID>`

`PATH` veya `NUGET_ID` belirtilen bir kaynak veya şablon paketini kurar. Şablon paketinin bir ön sürümünü yüklemek istiyorsanız, `<package-name>::<package-version>`biçiminde sürümü belirtmeniz gerekir. Varsayılan olarak, `dotnet new` en son kararlı paket sürümünü temsil eden sürüm için \* geçirir. [Örnekler](#examples) bölümündeki bir örneğe bakın.

Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz. [DotNet New Için özel şablonlar](custom-templates.md).

`-l|--list`

Belirtilen adı içeren şablonları listeler. `dotnet new` komutu için çağrılırsa, belirtilen dizin için kullanılabilir olabilecek şablonları listeler. Örneğin, dizin zaten bir proje içeriyorsa, tüm proje şablonlarını listeetmez.

`-lang|--language {C#|F#|VB}`

Oluşturulacak şablonun dili. Kabul edilen dil şablona göre değişir (bkz. [arguments](#arguments) bölümünde Varsayılanlar). Bazı şablonlar için geçerli değildir.

> [!NOTE]
> Bazı kabuklar, `#` özel bir karakter olarak yorumlar. Bu durumlarda, `dotnet new console -lang "F#"`gibi dil parametre değerini almanız gerekir.

`-n|--name <OUTPUT_NAME>`

Oluşturulan çıkışın adı. Ad belirtilmemişse, geçerli dizinin adı kullanılır.

`--nuget-source`

Yüklemesi sırasında kullanılacak bir NuGet kaynağını belirtir.

`-o|--output <OUTPUT_DIRECTORY>`

Oluşturulan çıkışın yerleştirileceği konum. Geçerli dizin varsayılandır.

`--type`

Şablonları kullanılabilir türlerine göre filtreler. Önceden tanımlanmış değerler şunlardır "proje", "öğe" veya "diğer".

`-u|--uninstall <PATH|NUGET_ID>`

`PATH` veya `NUGET_ID` sağlanmış bir kaynak veya şablon paketini kaldırır. `<PATH|NUGET_ID>` değeri hariç tutularak, yüklü olan tüm şablon paketleri ve bunlarla ilişkili şablonlar görüntülenir.

> [!NOTE]
> Bir `PATH`kullanarak bir şablonu kaldırmak için, yolu tam olarak nitelemeniz gerekir. Örneğin, *C:/kullanıcılar/\<USER >/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak içeren klasörden *./GarciaSoftware.ConsoleTemplate.CSharp* olmayacaktır.
> Ayrıca, şablon yolunuza son Sonlandırıcı Dizin eğik çizgi eklemeyin.

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

`--force`

Var olan dosyaları değiştirebilse bile içeriğin oluşturulmasını zorlar. Çıkış dizini zaten bir proje içerdiğinde bu gereklidir.

`-h|--help`

Komut için yardım yazdırır. `dotnet new` komutun kendisi veya `dotnet new mvc --help`gibi herhangi bir şablon için çağrılabilir.

`-i|--install <PATH|NUGET_ID>`

`PATH` veya `NUGET_ID` belirtilen bir kaynak veya şablon paketini kurar. Şablon paketinin bir ön sürümünü yüklemek istiyorsanız, `<package-name>::<package-version>`biçiminde sürümü belirtmeniz gerekir. Varsayılan olarak, `dotnet new` en son kararlı paket sürümünü temsil eden sürüm için \* geçirir. [Örnekler](#examples) bölümündeki bir örneğe bakın.

Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz. [DotNet New Için özel şablonlar](custom-templates.md).

`-l|--list`

Belirtilen adı içeren şablonları listeler. `dotnet new` komutu için çağrılırsa, belirtilen dizin için kullanılabilir olabilecek şablonları listeler. Örneğin, dizin zaten bir proje içeriyorsa, tüm proje şablonlarını listeetmez.

`-lang|--language {C#|F#|VB}`

Oluşturulacak şablonun dili. Kabul edilen dil şablona göre değişir (bkz. [arguments](#arguments) bölümünde Varsayılanlar). Bazı şablonlar için geçerli değildir.

> [!NOTE]
> Bazı kabuklar, `#` özel bir karakter olarak yorumlar. Bu durumlarda, `dotnet new console -lang "F#"`gibi dil parametre değerini almanız gerekir.

`-n|--name <OUTPUT_NAME>`

Oluşturulan çıkışın adı. Ad belirtilmemişse, geçerli dizinin adı kullanılır.

`--nuget-source`

Yüklemesi sırasında kullanılacak bir NuGet kaynağını belirtir.

`-o|--output <OUTPUT_DIRECTORY>`

Oluşturulan çıkışın yerleştirileceği konum. Geçerli dizin varsayılandır.

`--type`

Şablonları kullanılabilir türlerine göre filtreler. Önceden tanımlanmış değerler şunlardır "proje", "öğe" veya "diğer".

`-u|--uninstall <PATH|NUGET_ID>`

`PATH` veya `NUGET_ID` sağlanmış bir kaynak veya şablon paketini kaldırır.

> [!NOTE]
> Bir `PATH`kullanarak bir şablonu kaldırmak için, yolu tam olarak nitelemeniz gerekir. Örneğin, *C:/kullanıcılar/\<USER >/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak içeren klasörden *./GarciaSoftware.ConsoleTemplate.CSharp* olmayacaktır.
> Ayrıca, şablon yolunuza son Sonlandırıcı Dizin eğik çizgi eklemeyin.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2,0](#tab/netcore20)

`--force`

Var olan dosyaları değiştirebilse bile içeriğin oluşturulmasını zorlar. Çıkış dizini zaten bir proje içerdiğinde bu gereklidir.

`-h|--help`

Komut için yardım yazdırır. `dotnet new` komutun kendisi veya `dotnet new mvc --help`gibi herhangi bir şablon için çağrılabilir.

`-i|--install <PATH|NUGET_ID>`

`PATH` veya `NUGET_ID` belirtilen bir kaynak veya şablon paketini kurar. Şablon paketinin bir ön sürümünü yüklemek istiyorsanız, `<package-name>::<package-version>`biçiminde sürümü belirtmeniz gerekir. Varsayılan olarak, `dotnet new` en son kararlı paket sürümünü temsil eden sürüm için \* geçirir. [Örnekler](#examples) bölümündeki bir örneğe bakın.

Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz. [DotNet New Için özel şablonlar](custom-templates.md).

`-l|--list`

Belirtilen adı içeren şablonları listeler. `dotnet new` komutu için çağrılırsa, belirtilen dizin için kullanılabilir olabilecek şablonları listeler. Örneğin, dizin zaten bir proje içeriyorsa, tüm proje şablonlarını listeetmez.

`-lang|--language {C#|F#|VB}`

Oluşturulacak şablonun dili. Kabul edilen dil şablona göre değişir (bkz. [arguments](#arguments) bölümünde Varsayılanlar). Bazı şablonlar için geçerli değildir.

> [!NOTE]
> Bazı kabuklar, `#` özel bir karakter olarak yorumlar. Bu durumlarda, `dotnet new console -lang "F#"`gibi dil parametre değerini almanız gerekir.

`-n|--name <OUTPUT_NAME>`

Oluşturulan çıkışın adı. Ad belirtilmemişse, geçerli dizinin adı kullanılır.

`-o|--output <OUTPUT_DIRECTORY>`

Oluşturulan çıkışın yerleştirileceği konum. Geçerli dizin varsayılandır.

`--type`

Şablonları kullanılabilir türlerine göre filtreler. Önceden tanımlanmış değerler şunlardır "proje", "öğe" veya "diğer".

`-u|--uninstall <PATH|NUGET_ID>`

`PATH` veya `NUGET_ID` sağlanmış bir kaynak veya şablon paketini kaldırır.

> [!NOTE]
> Kaynak `PATH`kullanarak bir şablonu kaldırmak için, yolu tam olarak nitelemeniz gerekir. Örneğin, *C:/kullanıcılar/\<USER >/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak içeren klasörden *./GarciaSoftware.ConsoleTemplate.CSharp* olmayacaktır. Ayrıca, şablon yolunuza son Sonlandırıcı Dizin eğik çizgi eklemeyin.
> 
> Bir şablonu kaldırmak için gereken `PATH` veya `NUGET_ID` bağımsız değişkenini belirleyemıyorsanız, bir bağımsız değişken olmadan `dotnet new --uninstall` çalıştırmak, tüm yüklü şablonları ve bunları kaldırmak için gereken bağımsız değişkeni listeler.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1. x](#tab/netcore1x)

`-all|--show-all`

Yalnızca `dotnet new` komutu bağlamında çalışırken belirli bir proje türü için tüm şablonları gösterir. `dotnet new web -all`gibi belirli bir şablon bağlamında çalıştırılırken, `-all` bir zorla oluşturma bayrağı olarak yorumlanır. Çıkış dizini zaten bir proje içerdiğinde bu gereklidir.

`-h|--help`

Komut için yardım yazdırır. `dotnet new` komutun kendisi veya `dotnet new mvc --help`gibi herhangi bir şablon için çağrılabilir.

`-l|--list`

Belirtilen adı içeren şablonları listeler. `dotnet new` komutu için çağrılırsa, belirtilen dizin için kullanılabilir olabilecek şablonları listeler. Örneğin, dizin zaten bir proje içeriyorsa, tüm proje şablonlarını listeetmez.

`-lang|--language {C#|F#}`

Oluşturulacak şablonun dili. Kabul edilen dil şablona göre değişir (bkz. [arguments](#arguments) bölümünde Varsayılanlar). Bazı şablonlar için geçerli değildir.

> [!NOTE]
> Bazı kabuklar, `#` özel bir karakter olarak yorumlar. Bu durumlarda, `dotnet new console -lang "F#"`gibi dil parametre değerini almanız gerekir.

`-n|--name <OUTPUT_NAME>`

Oluşturulan çıkışın adı. Ad belirtilmemişse, geçerli dizinin adı kullanılır.

`-o|--output <OUTPUT_DIRECTORY>`

Oluşturulan çıkışın yerleştirileceği konum. Geçerli dizin varsayılandır.

---

## <a name="template-options"></a>Şablon seçenekleri

Her proje şablonunda ek seçenekler bulunabilir. Çekirdek şablonlar aşağıdaki ek seçeneklere sahiptir:

# <a name="net-core-22tabnetcore22"></a>[.NET Core 2,2](#tab/netcore22)

**konsola**

`--langVersion <VERSION_NUMBER>`-oluşturulan proje dosyasındaki `LangVersion` özelliğini ayarlar. Örneğin, 7,3 kullanmak C# için `--langVersion 7.3` kullanın. İçin F#desteklenmez.

`--no-restore`-proje oluşturma sırasında örtük geri yükleme yürütmez.

**Angular, tepki, reactredux**

`--exclude-launch-settings`-oluşturulan şablondan *Launchsettings. JSON* öğesini hariç tutun.

`--no-restore`-proje oluşturma sırasında örtük geri yükleme yürütmez.

`--no-https`-proje HTTPS gerektirmez. Bu seçenek yalnızca `IndividualAuth` veya `OrganizationalAuth` kullanılmıyorsa geçerlidir.

**razorclasslib**

`--no-restore`-proje oluşturma sırasında örtük geri yükleme yürütmez.

**projesinin**

`-f|--framework <FRAMEWORK>`-hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir. Değerler: bir .NET Standard sınıf kitaplığı oluşturmak için bir .NET Core sınıf kitaplığı veya `netstandard2.0` oluşturmak `netcoreapp2.2`. Varsayılan değer `netstandard2.0` şeklindedir.

`--langVersion <VERSION_NUMBER>`-oluşturulan proje dosyasındaki `LangVersion` özelliğini ayarlar. Örneğin, 7,3 kullanmak C# için `--langVersion 7.3` kullanın. İçin F#desteklenmez.

`--no-restore`-proje oluşturma sırasında örtük geri yükleme yürütmez.

**MSTest, xUnit**

`-p|--enable-pack`- [DotNet Pack](dotnet-pack.md)kullanarak proje için paketlemeyi etkinleştirilir.

`--no-restore`-proje oluşturma sırasında örtük geri yükleme yürütmez.

**NUnit**

`-f|--framework <FRAMEWORK>`-hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir. Varsayılan değer `netcoreapp2.1` şeklindedir.

`-p|--enable-pack`- [DotNet Pack](dotnet-pack.md)kullanarak proje için paketlemeyi etkinleştirilir.

`--no-restore`-proje oluşturma sırasında örtük geri yükleme yürütmez.

**sayfasında**

`-na|--namespace <NAMESPACE_NAME>`-oluşturulan kod için ad alanı. Varsayılan değer `MyApp.Namespace` şeklindedir.

`-np|--no-pagemodel`-sayfayı PageModel olmadan oluşturur.

**viewıtems 'lar**

`-na|--namespace <NAMESPACE_NAME>`-oluşturulan kod için ad alanı. Varsayılan değer `MyApp.Namespace` şeklindedir.

**Web**

`--exclude-launch-settings`-oluşturulan şablondan *Launchsettings. JSON* öğesini hariç tutun.

`--no-restore`-proje oluşturma sırasında örtük geri yükleme yürütmez.

`--no-https`-proje HTTPS gerektirmez. Bu seçenek yalnızca `IndividualAuth` veya `OrganizationalAuth` kullanılmıyorsa geçerlidir.

**MVC, WebApp**

`-au|--auth <AUTHENTICATION_TYPE>`-kullanılacak kimlik doğrulaması türü. Olası değerler şunlardır:

- `None`-kimlik doğrulaması yok (varsayılan).
- `Individual` bireysel kimlik doğrulaması.
- `IndividualB2C` bireysel kimlik doğrulama Azure AD B2C.
- tek bir kiracı için `SingleOrg` kurumsal kimlik doğrulaması.
- `MultiOrg`-birden çok kiracı için kuruluş kimlik doğrulaması.
- `Windows`-Windows kimlik doğrulaması.

`--aad-b2c-instance <INSTANCE>`-Bağlanılacak Azure Active Directory B2C örneği. `IndividualB2C` kimlik doğrulamasıyla kullanın. Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.

`-ssp|--susi-policy-id <ID>`-bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI. `IndividualB2C` kimlik doğrulamasıyla kullanın.

`-rp|--reset-password-policy-id <ID>`-bu proje için parola sıfırlama ilkesi KIMLIĞI. `IndividualB2C` kimlik doğrulamasıyla kullanın.

`-ep|--edit-profile-policy-id <ID>`-bu proje için profil ilke KIMLIĞINI Düzenle. `IndividualB2C` kimlik doğrulamasıyla kullanın.

`--aad-instance <INSTANCE>`-Bağlanılacak Azure Active Directory örneği. `SingleOrg` veya `MultiOrg` kimlik doğrulamasıyla kullanın. Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.

`--client-id <ID>`-bu projenin Istemci KIMLIĞI. `IndividualB2C`, `SingleOrg`veya `MultiOrg` kimlik doğrulamasıyla kullanın. Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.

`--domain <DOMAIN>`-Dizin kiracının etki alanı. `SingleOrg` veya `IndividualB2C` kimlik doğrulamasıyla kullanın. Varsayılan değer `qualified.domain.name` şeklindedir.

`--tenant-id <ID>`-Bağlanılacak dizinin Tenantıd KIMLIĞI. `SingleOrg` kimlik doğrulamasıyla kullanın. Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.

`--callback-path <PATH>`-uygulamanın yeniden yönlendirme URI 'sinin temel yolu içindeki istek yolu. `SingleOrg` veya `IndividualB2C` kimlik doğrulamasıyla kullanın. Varsayılan değer `/signin-oidc` şeklindedir.

`-r|--org-read-access`-bu uygulamanın dizine okuma erişimini sağlar. Yalnızca `SingleOrg` veya `MultiOrg` kimlik doğrulaması için geçerlidir.

`--exclude-launch-settings`-oluşturulan şablondan *Launchsettings. JSON* öğesini hariç tutun.

`--no-https`-proje HTTPS gerektirmez. `app.UseHsts` ve `app.UseHttpsRedirection` `Startup.Configure`eklenmez. Bu seçenek yalnızca `Individual`, `IndividualB2C`, `SingleOrg`veya `MultiOrg` kullanılmıyorsa geçerlidir.

`-uld|--use-local-db`-bir LocalDB 'nin SQLite yerine kullanılması gerektiğini belirtir. Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.

`--no-restore`-proje oluşturma sırasında örtük geri yükleme yürütmez.

**WebApi**

`-au|--auth <AUTHENTICATION_TYPE>`-kullanılacak kimlik doğrulaması türü. Olası değerler şunlardır:

- `None`-kimlik doğrulaması yok (varsayılan).
- `IndividualB2C` bireysel kimlik doğrulama Azure AD B2C.
- tek bir kiracı için `SingleOrg` kurumsal kimlik doğrulaması.
- `Windows`-Windows kimlik doğrulaması.

`--aad-b2c-instance <INSTANCE>`-Bağlanılacak Azure Active Directory B2C örneği. `IndividualB2C` kimlik doğrulamasıyla kullanın. Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.

`-ssp|--susi-policy-id <ID>`-bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI. `IndividualB2C` kimlik doğrulamasıyla kullanın.

`--aad-instance <INSTANCE>`-Bağlanılacak Azure Active Directory örneği. `SingleOrg` kimlik doğrulamasıyla kullanın. Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.

`--client-id <ID>`-bu projenin Istemci KIMLIĞI. `IndividualB2C` veya `SingleOrg` kimlik doğrulamasıyla kullanın. Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.

`--domain <DOMAIN>`-Dizin kiracının etki alanı. `SingleOrg` veya `IndividualB2C` kimlik doğrulamasıyla kullanın. Varsayılan değer `qualified.domain.name` şeklindedir.

`--tenant-id <ID>`-Bağlanılacak dizinin Tenantıd KIMLIĞI. `SingleOrg` kimlik doğrulamasıyla kullanın. Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.

`-r|--org-read-access`-bu uygulamanın dizine okuma erişimini sağlar. Yalnızca `SingleOrg` veya `MultiOrg` kimlik doğrulaması için geçerlidir.

`--exclude-launch-settings`-oluşturulan şablondan *Launchsettings. JSON* öğesini hariç tutun.

`--no-https`-proje HTTPS gerektirmez. `app.UseHsts` ve `app.UseHttpsRedirection` `Startup.Configure`eklenmez. Bu seçenek yalnızca `Individual`, `IndividualB2C`, `SingleOrg`veya `MultiOrg` kullanılmıyorsa geçerlidir.

`-uld|--use-local-db`-bir LocalDB 'nin SQLite yerine kullanılması gerektiğini belirtir. Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.

`--no-restore`-proje oluşturma sırasında örtük geri yükleme yürütmez.

**globaljson**

`--sdk-version <VERSION_NUMBER>`- *Global. JSON* dosyasında kullanılacak .NET Core SDK sürümünü belirtir.

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

**konsol, angular, tepki, reactredux, razorclasslib**

`--no-restore`-proje oluşturma sırasında örtük geri yükleme yürütmez.

**projesinin**

`-f|--framework <FRAMEWORK>`-hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir. Değerler: bir .NET Standard sınıf kitaplığı oluşturmak için bir .NET Core sınıf kitaplığı veya `netstandard2.0` oluşturmak `netcoreapp2.1`. Varsayılan değer `netstandard2.0` şeklindedir.

`--no-restore`-proje oluşturma sırasında örtük geri yükleme yürütmez.

**MSTest, xUnit**

`-p|--enable-pack`- [DotNet Pack](dotnet-pack.md)kullanarak proje için paketlemeyi etkinleştirilir.

`--no-restore`-proje oluşturma sırasında örtük geri yükleme yürütmez.

**globaljson**

`--sdk-version <VERSION_NUMBER>`- *Global. JSON* dosyasında kullanılacak .NET Core SDK sürümünü belirtir.

**Web**

`--exclude-launch-settings`-oluşturulan şablondan *Launchsettings. JSON* öğesini hariç tutun.

`--no-restore`-proje oluşturma sırasında örtük geri yükleme yürütmez.

`--no-https`-proje HTTPS gerektirmez. Bu seçenek yalnızca `IndividualAuth` veya `OrganizationalAuth` kullanılmıyorsa geçerlidir.

**WebApi**

`-au|--auth <AUTHENTICATION_TYPE>`-kullanılacak kimlik doğrulaması türü. Olası değerler şunlardır:

- `None`-kimlik doğrulaması yok (varsayılan).
- `IndividualB2C` bireysel kimlik doğrulama Azure AD B2C.
- tek bir kiracı için `SingleOrg` kurumsal kimlik doğrulaması.
- `Windows`-Windows kimlik doğrulaması.

`--aad-b2c-instance <INSTANCE>`-Bağlanılacak Azure Active Directory B2C örneği. `IndividualB2C` kimlik doğrulamasıyla kullanın. Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.

`-ssp|--susi-policy-id <ID>`-bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI. `IndividualB2C` kimlik doğrulamasıyla kullanın.

`--aad-instance <INSTANCE>`-Bağlanılacak Azure Active Directory örneği. `SingleOrg` kimlik doğrulamasıyla kullanın. Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.

`--client-id <ID>`-bu projenin Istemci KIMLIĞI. `IndividualB2C` veya `SingleOrg` kimlik doğrulamasıyla kullanın. Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.

`--domain <DOMAIN>`-Dizin kiracının etki alanı. `SingleOrg` veya `IndividualB2C` kimlik doğrulamasıyla kullanın. Varsayılan değer `qualified.domain.name` şeklindedir.

`--tenant-id <ID>`-Bağlanılacak dizinin Tenantıd KIMLIĞI. `SingleOrg` kimlik doğrulamasıyla kullanın. Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.

`-r|--org-read-access`-bu uygulamanın dizine okuma erişimini sağlar. Yalnızca `SingleOrg` veya `MultiOrg` kimlik doğrulaması için geçerlidir.

`--exclude-launch-settings`-oluşturulan şablondan *Launchsettings. JSON* öğesini hariç tutun.

`-uld|--use-local-db`-bir LocalDB 'nin SQLite yerine kullanılması gerektiğini belirtir. Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.

`--no-restore`-proje oluşturma sırasında örtük geri yükleme yürütmez.

`--no-https`-proje HTTPS gerektirmez. `app.UseHsts` ve `app.UseHttpsRedirection` `Startup.Configure`eklenmez. Bu seçenek yalnızca `Individual`, `IndividualB2C`, `SingleOrg`veya `MultiOrg` kullanılmıyorsa geçerlidir.

**MVC, Razor**

`-au|--auth <AUTHENTICATION_TYPE>`-kullanılacak kimlik doğrulaması türü. Olası değerler şunlardır:

- `None`-kimlik doğrulaması yok (varsayılan).
- `Individual` bireysel kimlik doğrulaması.
- `IndividualB2C` bireysel kimlik doğrulama Azure AD B2C.
- tek bir kiracı için `SingleOrg` kurumsal kimlik doğrulaması.
- `MultiOrg`-birden çok kiracı için kuruluş kimlik doğrulaması.
- `Windows`-Windows kimlik doğrulaması.

`--aad-b2c-instance <INSTANCE>`-Bağlanılacak Azure Active Directory B2C örneği. `IndividualB2C` kimlik doğrulamasıyla kullanın. Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.

`-ssp|--susi-policy-id <ID>`-bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI. `IndividualB2C` kimlik doğrulamasıyla kullanın.

`-rp|--reset-password-policy-id <ID>`-bu proje için parola sıfırlama ilkesi KIMLIĞI. `IndividualB2C` kimlik doğrulamasıyla kullanın.

`-ep|--edit-profile-policy-id <ID>`-bu proje için profil ilke KIMLIĞINI Düzenle. `IndividualB2C` kimlik doğrulamasıyla kullanın.

`--aad-instance <INSTANCE>`-Bağlanılacak Azure Active Directory örneği. `SingleOrg` veya `MultiOrg` kimlik doğrulamasıyla kullanın. Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.

`--client-id <ID>`-bu projenin Istemci KIMLIĞI. `IndividualB2C`, `SingleOrg`veya `MultiOrg` kimlik doğrulamasıyla kullanın. Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.

`--domain <DOMAIN>`-Dizin kiracının etki alanı. `SingleOrg` veya `IndividualB2C` kimlik doğrulamasıyla kullanın. Varsayılan değer `qualified.domain.name` şeklindedir.

`--tenant-id <ID>`-Bağlanılacak dizinin Tenantıd KIMLIĞI. `SingleOrg` kimlik doğrulamasıyla kullanın. Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.

`--callback-path <PATH>`-uygulamanın yeniden yönlendirme URI 'sinin temel yolu içindeki istek yolu. `SingleOrg` veya `IndividualB2C` kimlik doğrulamasıyla kullanın. Varsayılan değer `/signin-oidc` şeklindedir.

`-r|--org-read-access`-bu uygulamanın dizine okuma erişimini sağlar. Yalnızca `SingleOrg` veya `MultiOrg` kimlik doğrulaması için geçerlidir.

`--exclude-launch-settings`-oluşturulan şablondan *Launchsettings. JSON* öğesini hariç tutun.

`--use-browserlink`-projede BrowserLink 'i Içerir.

`-uld|--use-local-db`-bir LocalDB 'nin SQLite yerine kullanılması gerektiğini belirtir. Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.

`--no-restore`-proje oluşturma sırasında örtük geri yükleme yürütmez.

`--no-https`-proje HTTPS gerektirmez. `app.UseHsts` ve `app.UseHttpsRedirection` `Startup.Configure`eklenmez. Bu seçenek yalnızca `Individual`, `IndividualB2C`, `SingleOrg`veya `MultiOrg` kullanılmıyorsa geçerlidir.

**sayfasında**

`-na|--namespace <NAMESPACE_NAME>`-oluşturulan kod için ad alanı. Varsayılan değer `MyApp.Namespace` şeklindedir.

`-np|--no-pagemodel`-sayfayı PageModel olmadan oluşturur.

**viewıtems 'lar**

`-na|--namespace <NAMESPACE_NAME>`-oluşturulan kod için ad alanı. Varsayılan değer `MyApp.Namespace` şeklindedir.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2,0](#tab/netcore20)

**konsol, angular, tepki, reactredux**

`--no-restore`-proje oluşturma sırasında örtük geri yükleme yürütmez.

**projesinin**

`-f|--framework <FRAMEWORK>`-hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir. Değerler: bir .NET Standard sınıf kitaplığı oluşturmak için bir .NET Core sınıf kitaplığı veya `netstandard2.0` oluşturmak `netcoreapp2.0`. Varsayılan değer `netstandard2.0` şeklindedir.

`--no-restore`-proje oluşturma sırasında örtük geri yükleme yürütmez.

**MSTest, xUnit**

`-p|--enable-pack`- [DotNet Pack](dotnet-pack.md)kullanarak proje için paketlemeyi etkinleştirilir.

`--no-restore`-proje oluşturma sırasında örtük geri yükleme yürütmez.

**globaljson**

`--sdk-version <VERSION_NUMBER>`- *Global. JSON* dosyasında kullanılacak .NET Core SDK sürümünü belirtir.

**Web**

`--use-launch-settings`-oluşturulan şablon çıkışında *Launchsettings. JSON* öğesini içerir.

`--no-restore`-proje oluşturma sırasında örtük geri yükleme yürütmez.

**WebApi**

`-au|--auth <AUTHENTICATION_TYPE>`-kullanılacak kimlik doğrulaması türü. Olası değerler şunlardır:

- `None`-kimlik doğrulaması yok (varsayılan).
- `IndividualB2C` bireysel kimlik doğrulama Azure AD B2C.
- tek bir kiracı için `SingleOrg` kurumsal kimlik doğrulaması.
- `Windows`-Windows kimlik doğrulaması.

`--aad-b2c-instance <INSTANCE>`-Bağlanılacak Azure Active Directory B2C örneği. `IndividualB2C` kimlik doğrulamasıyla kullanın. Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.

`-ssp|--susi-policy-id <ID>`-bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI. `IndividualB2C` kimlik doğrulamasıyla kullanın.

`--aad-instance <INSTANCE>`-Bağlanılacak Azure Active Directory örneği. `SingleOrg` kimlik doğrulamasıyla kullanın. Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.

`--client-id <ID>`-bu projenin Istemci KIMLIĞI. `IndividualB2C` veya `SingleOrg` kimlik doğrulamasıyla kullanın. Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.

`--domain <DOMAIN>`-Dizin kiracının etki alanı. `SingleOrg` veya `IndividualB2C` kimlik doğrulamasıyla kullanın. Varsayılan değer `qualified.domain.name` şeklindedir.

`--tenant-id <ID>`-Bağlanılacak dizinin Tenantıd KIMLIĞI. `SingleOrg` kimlik doğrulamasıyla kullanın. Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.

`-r|--org-read-access`-bu uygulamanın dizine okuma erişimini sağlar. Yalnızca `SingleOrg` veya `MultiOrg` kimlik doğrulaması için geçerlidir.

`--use-launch-settings`-oluşturulan şablon çıkışında *Launchsettings. JSON* öğesini içerir.

`-uld|--use-local-db`-bir LocalDB 'nin SQLite yerine kullanılması gerektiğini belirtir. Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.

`--no-restore`-proje oluşturma sırasında örtük geri yükleme yürütmez.

**MVC, Razor**

`-au|--auth <AUTHENTICATION_TYPE>`-kullanılacak kimlik doğrulaması türü. Olası değerler şunlardır:

- `None`-kimlik doğrulaması yok (varsayılan).
- `Individual` bireysel kimlik doğrulaması.
- `IndividualB2C` bireysel kimlik doğrulama Azure AD B2C.
- tek bir kiracı için `SingleOrg` kurumsal kimlik doğrulaması.
- `MultiOrg`-birden çok kiracı için kuruluş kimlik doğrulaması.
- `Windows`-Windows kimlik doğrulaması.

`--aad-b2c-instance <INSTANCE>`-Bağlanılacak Azure Active Directory B2C örneği. `IndividualB2C` kimlik doğrulamasıyla kullanın. Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.

`-ssp|--susi-policy-id <ID>`-bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI. `IndividualB2C` kimlik doğrulamasıyla kullanın.

`-rp|--reset-password-policy-id <ID>`-bu proje için parola sıfırlama ilkesi KIMLIĞI. `IndividualB2C` kimlik doğrulamasıyla kullanın.

`-ep|--edit-profile-policy-id <ID>`-bu proje için profil ilke KIMLIĞINI Düzenle. `IndividualB2C` kimlik doğrulamasıyla kullanın.

`--aad-instance <INSTANCE>`-Bağlanılacak Azure Active Directory örneği. `SingleOrg` veya `MultiOrg` kimlik doğrulamasıyla kullanın. Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.

`--client-id <ID>`-bu projenin Istemci KIMLIĞI. `IndividualB2C`, `SingleOrg`veya `MultiOrg` kimlik doğrulamasıyla kullanın. Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.

`--domain <DOMAIN>`-Dizin kiracının etki alanı. `SingleOrg` veya `IndividualB2C` kimlik doğrulamasıyla kullanın. Varsayılan değer `qualified.domain.name` şeklindedir.

`--tenant-id <ID>`-Bağlanılacak dizinin Tenantıd KIMLIĞI. `SingleOrg` kimlik doğrulamasıyla kullanın. Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.

`--callback-path <PATH>`-uygulamanın yeniden yönlendirme URI 'sinin temel yolu içindeki istek yolu. `SingleOrg` veya `IndividualB2C` kimlik doğrulamasıyla kullanın. Varsayılan değer `/signin-oidc` şeklindedir.

`-r|--org-read-access`-bu uygulamanın dizine okuma erişimini sağlar. Yalnızca `SingleOrg` veya `MultiOrg` kimlik doğrulaması için geçerlidir.

`--use-launch-settings`-oluşturulan şablon çıkışında *Launchsettings. JSON* öğesini içerir.

`--use-browserlink`-projede BrowserLink 'i Içerir.

`-uld|--use-local-db`-bir LocalDB 'nin SQLite yerine kullanılması gerektiğini belirtir. Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.

`--no-restore`-proje oluşturma sırasında örtük geri yükleme yürütmez.

**sayfasında**

`-na|--namespace <NAMESPACE_NAME>`-oluşturulan kod için ad alanı. Varsayılan değer `MyApp.Namespace` şeklindedir.

`-np|--no-pagemodel`-sayfayı PageModel olmadan oluşturur.

**viewıtems 'lar**

`-na|--namespace <NAMESPACE_NAME>`-oluşturulan kod için ad alanı. Varsayılan değer `MyApp.Namespace` şeklindedir.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1. x](#tab/netcore1x)

**konsol, xUnit, MSTest, Web, WebApi**

`-f|--framework <FRAMEWORK>`-hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir. Değerler: `netcoreapp1.0` veya `netcoreapp1.1`. Varsayılan değer `netcoreapp1.0` şeklindedir.

**projesinin**

`-f|--framework <FRAMEWORK>`-hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir. Değerler: `netstandard1.6`için `netcoreapp1.0`, `netcoreapp1.1`veya `netstandard1.0`. Varsayılan değer `netstandard1.4` şeklindedir.

**MVC**

`-f|--framework <FRAMEWORK>`-hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir. Değerler: `netcoreapp1.0` veya `netcoreapp1.1`. Varsayılan değer `netcoreapp1.0` şeklindedir.

`-au|--auth <AUTHENTICATION_TYPE>`-kullanılacak kimlik doğrulaması türü. Değerler: `None` veya `Individual`. Varsayılan değer `None` şeklindedir.

`-uld|--use-local-db`-, SQLite yerine LocalDB kullanılıp kullanılmayacağını belirtir. Değerler: `true` veya `false`. Varsayılan değer `false` şeklindedir.

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

Şablonla *eşleşen şablonu*çağırma girişimi. Tek bir eşleşme belirlenemiyorsa kısmi eşleşen şablonları listeleyin.

`dotnet new ng`

ASP.NET Core için tek sayfalı uygulama şablonlarının 2,0 sürümünü (yalnızca .NET Core SDK 1,1 ve sonraki sürümler için kullanılabilir) (komut seçeneği) yükler:

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

SDK sürümü 2.0.0 (yalnızca .NET Core SDK 2,0 veya üzeri sürümlerle kullanılabilir) ayarı geçerli dizinde *Global. JSON* oluşturun:

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a>Ayrıca bkz.

- [DotNet New için özel şablonlar](custom-templates.md)
- [Dotnet new için özel şablon oluşturma](../tutorials/cli-templates-create-item-template.md)
- [DotNet/DotNet-şablon-örnek GitHub deposu](https://github.com/dotnet/dotnet-template-samples)
- [DotNet New için kullanılabilir şablonlar](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
