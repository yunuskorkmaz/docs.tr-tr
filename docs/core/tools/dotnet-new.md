---
title: DotNet yeni komutu - .NET Core CLI
description: "Dotnet yeni komut belirtilen şablona dayalı yeni .NET Core projelerini oluşturur."
keywords: dotnet-new, CLI, CLI command, .NET Core
author: mairaw
ms.author: mairaw
ms.date: 08/13/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: fcc3ed2e-9265-4d50-b59e-dc2e5c190b34
ms.workload: dotnetcore
ms.openlocfilehash: cf65dc80f135badcb1580726a12a9ae9d94ae3d7
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/20/2018
---
# <a name="dotnet-new"></a>DotNet yeni

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet new`-Yeni Proje, yapılandırma dosyası veya belirtilen şablona dayalı çözüm oluşturur.

## <a name="synopsis"></a>Özet

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a>Açıklama

`dotnet new` Komutu geçerli bir .NET Core projeyi başlatmak için kolay bir yol sağlar. 

Komut çağrıları [şablon motoru](https://github.com/dotnet/templating) yapıları belirtilen şablonu ve seçenekleri bağlı disk oluşturmak için.

## <a name="arguments"></a>Arguments

`TEMPLATE`

Komutu çağrıldığında örneği oluşturmak için şablon. Her bir şablon geçirebilirsiniz belirli seçenekleri olabilir. Daha fazla bilgi için bkz: [şablon seçenekleri](#template-options).

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

Komut şablonlarının varsayılan listesini içerir. Kullanım `dotnet new -l` kullanılabilir şablonların listesini elde edilir. Aşağıdaki tabloda .NET Core 2.0 SDK ile birlikte önceden yüklenmiş olarak gelen şablonları gösterir. Şablon için varsayılan dili köşeli ayraçlar içinde gösterilmiştir.

|Şablon açıklaması                          | Şablon adı | Diller     |
|----------------------------------------------|---------------|---------------|
| Konsol uygulaması                          | `console`     | [C#], F#, VB  |
| Sınıf kitaplığı                                | `classlib`    | [C#], F#, VB  |
| Birim testi projesi                            | `mstest`      | [C#], F#, VB  |
| xUnit test project                           | `xunit`       | [C#], F#, VB  |
| ASP.NET Core boş                           | `web`         | [C#], F#      |
| ASP.NET Core Web uygulaması (Model-View-Controller) | `mvc`         | [C#], F#      |
| ASP.NET Core Web uygulaması                         | `razor`       | [C#]          |
| ASP.NET Core Açısal ile                    | `angular`     | [C#]          |
| ASP.NET Core React.js ile                   | `react`       | [C#]          |
| ASP.NET Core React.js ve Redux         | `reactredux`  | [C#]          |
| ASP.NET Core Web API                         | `webapi`      | [C#], F#      |
| global.json file                             | `globaljson`  |               |
| Nuget yapılandırma                                 | `nugetconfig` |               |
| Web yapılandırma                                   | `webconfig`   |               |
| Çözüm dosyası                                | `sln`         |               |
| Razor sayfası                                   | `page`        |               |
| MVC/ViewImports                              | `viewimports` |               |
| MVC ViewStart                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

Komut şablonlarının varsayılan listesini içerir. Kullanım `dotnet new -all` kullanılabilir şablonların listesini elde edilir. .NET Core ile önceden yüklenmiş olarak gelen şablonları aşağıdaki tabloda gösterilmektedir 1.x SDK. Şablon için varsayılan dili köşeli ayraçlar içinde gösterilmiştir.

|Şablon açıklaması  | Şablon adı | Diller |
|----------------------|---------------|-----------|
| Konsol uygulaması  | `console`     | [C#], F#  |
| Sınıf kitaplığı        | `classlib`    | [C#], F#  |
| Birim testi projesi    | `mstest`      | [C#], F#  |
| xUnit test project   | `xunit`       | [C#], F#  |
| ASP.NET Core boş   | `web`         | [C#]      |
| ASP.NET Core Web uygulaması | `mvc`         | [C#], F#  |
| ASP.NET Core Web API | `webapi`      | [C#]      |
| Nuget yapılandırma         | `nugetconfig` |           |
| Web yapılandırma           | `webconfig`   |           |
| Çözüm dosyası        | `sln`         |           |

---

## <a name="options"></a>Seçenekler

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

`--force`

Var olan dosyaları değişeceğinden olsa bile oluşturulacak içeriği zorlar. Çıktı dizini bir proje zaten içeriyor, bu gereklidir.

`-h|--help`

Komut için Yardım yazdırır. İçin çağrılabilir `dotnet new` kendisini komut veya herhangi bir şablonu gibi `dotnet new mvc --help`.

`-i|--install <PATH|NUGET_ID>`

Bir kaynak veya şablon paketinden yükler `PATH` veya `NUGET_ID` sağlanan. Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz: [yeni dotnet için özel şablonlar](custom-templates.md).

`-l|--list`

Belirtilen ad içeren şablonlarını listeler. İçin başlatılırsa `dotnet new` komutu için belirtilen dizin kullanılabilir olası şablonları listeler. Örneğin dizini zaten bir proje içeriyorsa, tüm proje şablonları listesinde değil.

`-lang|--language {C#|F#|VB}`

Oluşturmak için şablon dili. Dil kabul değişir şablon tarafından (varsayılan ayarlarında bkz [bağımsız değişkenleri](#arguments) bölümü). Bazı şablonlar için geçerli değil.

`-n|--name <OUTPUT_NAME>`

Oluşturulan çıktı adı. Ad belirtilmezse, geçerli dizin adı kullanılır.

`-o|--output <OUTPUT_DIRECTORY>`

Oluşturulan çıktı yerleştirileceği konum. Geçerli dizin varsayılandır.

`--type`

Şablonlar kullanılabilir türlerine göre filtreler. Önceden tanımlanmış değerler "proje", "öğesi" veya "diğer" olabilir.

`-u|--uninstall <PATH|NUGET_ID>`

Bir kaynak veya şablon paketini kaldırır `PATH` veya `NUGET_ID` sağlanan.

> [!NOTE]
> Bir şablon kullanarak kaldırmak için bir `PATH`, yolun tam olarak nitelemek gerekir. Örneğin, *C:/Users/\<kullanıcı > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak *./GarciaSoftware.ConsoleTemplate.CSharp* içeren gelen Klasör almayacak.
> Ayrıca, şablonu yoldaki son sonlandırma dizin eğik çizgi eklemeyin.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`-all|--show-all`

Belirli bir proje türü için tüm şablonları bağlamında çalışırken gösterir `dotnet new` tek başına komutu. Belirli bir şablon bağlamda gibi çalıştırırken `dotnet new web -all`, `-all` zorla oluşturma bayrak olarak yorumlanır. Çıktı dizini bir proje zaten içeriyor, bu gereklidir.

`-h|--help`

Komut için Yardım yazdırır. İçin çağrılabilir `dotnet new` kendisini komut veya herhangi bir şablonu gibi `dotnet new mvc --help`.

`-l|--list`

Belirtilen ad içeren şablonlarını listeler. İçin başlatılırsa `dotnet new` komutu için belirtilen dizin kullanılabilir olası şablonları listeler. Örneğin dizini zaten bir proje içeriyorsa, tüm proje şablonları listesinde değil.

`-lang|--language {C#|F#}`

Oluşturmak için şablon dili. Dil kabul değişir şablon tarafından (varsayılan ayarlarında bkz [bağımsız değişkenleri](#arguments) bölümü). Bazı şablonlar için geçerli değil.

`-n|--name <OUTPUT_NAME>`

Oluşturulan çıktı adı. Ad belirtilmezse, geçerli dizin adı kullanılır.

`-o|--output <OUTPUT_DIRECTORY>`

Oluşturulan çıktı yerleştirileceği konum. Geçerli dizin varsayılandır.

---

## <a name="template-options"></a>Şablon seçenekleri

Her proje şablonu ek seçenekleri olabilir. Çekirdek şablonları aşağıdaki ek seçeneklere sahip olursunuz:

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

**konsolunda, Açısal, tepki, reactredux**

`--no-restore`-Proje oluşturma sırasında örtük bir geri yükleme yapın değil.

**classlib**

`-f|--framework <FRAMEWORK>`-Belirtir [framework](../../standard/frameworks.md) hedef. Değerler: `netcoreapp2.0` .NET çekirdek sınıf kitaplığı oluşturmak için veya `netstandard2.0` .NET standart sınıf kitaplığı oluşturmak için. Varsayılan değer `netstandard2.0` şeklindedir.

`--no-restore`-Proje oluşturma sırasında örtük bir geri yükleme yapın değil.

**mstest, xunit**

`-p|--enable-pack`-Proje kullanma paketleme sağlar [dotnet paketi](dotnet-pack.md).

`--no-restore`-Proje oluşturma sırasında örtük bir geri yükleme yapın değil.

**globaljson**

`--sdk-version <VERSION_NUMBER>`-Kullanmak için .NET Core SDK sürümünü belirtir *global.json* dosya.

**web**

`--use-launch-settings`-İçeren *launchSettings.json* oluşturulan şablon çıkışı.

`--no-restore`-Proje oluşturma sırasında örtük bir geri yükleme yapın değil.

**webapi**

`-au|--auth <AUTHENTICATION_TYPE>`-Kullanılacak kimlik doğrulama türü. Olası değerler şunlardır:

- `None`-Kimlik doğrulama yok (varsayılan).
- `IndividualB2C`-Azure AD B2C ile tek tek kimlik doğrulaması.
- `SingleOrg`-Tek bir kiracı için kuruluş kimlik doğrulaması.
- `Windows`-Windows kimlik doğrulaması.

`--aad-b2c-instance <INSTANCE>`-Bağlanmak için Azure Active Directory B2C örnek. İle kullandığınız `IndividualB2C` kimlik doğrulaması. Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.

`-ssp|--susi-policy-id <ID>`-Bu proje için oturum açma ve kaydolma ilke kimliği. İle kullandığınız `IndividualB2C` kimlik doğrulaması.

`--aad-instance <INSTANCE>`-Bağlanmak için Azure Active Directory örneği. İle kullandığınız `SingleOrg` kimlik doğrulaması. Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.

`--client-id <ID>`-Bu proje için istemci kimliği. İle kullandığınız `IndividualB2C` veya `SingleOrg` kimlik doğrulaması. Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.

`--domain <DOMAIN>`-Etki alanı için dizin Kiracı. İle kullandığınız `SingleOrg` veya `IndividualB2C` kimlik doğrulaması. Varsayılan değer `qualified.domain.name` şeklindedir.

`--tenant-id <ID>`-Tenantıd bağlanmak için kimliği dizini. İle kullandığınız `SingleOrg` kimlik doğrulaması. Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.

`-r|--org-read-access`-Bu uygulamanın dizine okuma erişimi sağlar. Yalnızca uygular `SingleOrg` veya `MultiOrg` kimlik doğrulaması.

`--use-launch-settings`-İçeren *launchSettings.json* oluşturulan şablon çıkışı.

`-uld|--use-local-db`-Yerel veritabanı yerine SQLite kullanılması gerektiğini belirtir. Yalnızca uygular `Individual` veya `IndividualB2C` kimlik doğrulaması.

`--no-restore`-Proje oluşturma sırasında örtük bir geri yükleme yapın değil.

**mvc, razor**

`-au|--auth <AUTHENTICATION_TYPE>`-Kullanılacak kimlik doğrulama türü. Olası değerler şunlardır:

- `None`-Kimlik doğrulama yok (varsayılan).
- `Individual`-Tek tek kimlik doğrulaması.
- `IndividualB2C`-Azure AD B2C ile tek tek kimlik doğrulaması.
- `SingleOrg`-Tek bir kiracı için kuruluş kimlik doğrulaması.
- `MultiOrg`-Birden çok Kiracı için kuruluş kimlik doğrulaması.
- `Windows`-Windows kimlik doğrulaması.

`--aad-b2c-instance <INSTANCE>`-Bağlanmak için Azure Active Directory B2C örnek. İle kullandığınız `IndividualB2C` kimlik doğrulaması. Varsayılan değer `https://login.microsoftonline.com/tfp/` .

`-ssp|--susi-policy-id <ID>`-Bu proje için oturum açma ve kaydolma ilke kimliği. İle kullandığınız `IndividualB2C` kimlik doğrulaması.

`-rp|--reset-password-policy-id <ID>`-Bu proje için reset parola ilkesi kimliği. İle kullandığınız `IndividualB2C` kimlik doğrulaması.

`-ep|--edit-profile-policy-id <ID>`-Bu proje için Düzenle profili ilke kimliği. İle kullandığınız `IndividualB2C` kimlik doğrulaması.

`--aad-instance <INSTANCE>`-Bağlanmak için Azure Active Directory örneği. İle kullandığınız `SingleOrg` veya `MultiOrg` kimlik doğrulaması. Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.

`--client-id <ID>`-Bu proje için istemci kimliği. İle kullandığınız `IndividualB2C`, `SingleOrg`, veya `MultiOrg` kimlik doğrulaması. Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.

`--domain <DOMAIN>`-Etki alanı için dizin Kiracı. İle kullandığınız `SingleOrg` veya `IndividualB2C` kimlik doğrulaması... Varsayılan değer `qualified.domain.name` şeklindedir.

`--tenant-id <ID>`-Tenantıd bağlanmak için kimliği dizini. İle kullandığınız `SingleOrg` kimlik doğrulaması... Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.

`--callback-path <PATH>`-Yeniden yönlendirme URI'si, uygulamanın taban yolu içindeki istek yolu. İle kullandığınız `SingleOrg` veya `IndividualB2C` kimlik doğrulaması... Varsayılan değer `/signin-oidc` şeklindedir.

`-r|--org-read-access`-Bu uygulamanın dizine okuma erişimi sağlar. Yalnızca uygular `SingleOrg` veya `MultiOrg` kimlik doğrulaması.

`--use-launch-settings`-İçeren *launchSettings.json* oluşturulan şablon çıkışı.

`--use-browserlink`-BrowserLink projede içerir.

`-uld|--use-local-db`-Yerel veritabanı yerine SQLite kullanılması gerektiğini belirtir. Yalnızca uygular `Individual` veya `IndividualB2C` kimlik doğrulaması.

`--no-restore`-Proje oluşturma sırasında örtük bir geri yükleme yapın değil.

**Sayfa**

`-na|--namespace <NAMESPACE_NAME>`-Namespace üretilen kod için. Varsayılan değer `MyApp.Namespace` şeklindedir.

`-np|--no-pagemodel`-Bir PageModel olmadan sayfası oluşturur.

**viewimports**

`-na|--namespace <NAMESPACE_NAME>`-Namespace üretilen kod için. Varsayılan değer `MyApp.Namespace` şeklindedir.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**Konsolu, xunit, mstest'i, web, webapı**

`-f|--framework`-Belirtir [framework](../../standard/frameworks.md) hedef. Değerler: `netcoreapp1.0` veya `netcoreapp1.1`. Varsayılan değer `netcoreapp1.0` şeklindedir.

**classlib**

`-f|--framework`-Belirtir [framework](../../standard/frameworks.md) hedef. Değerler: `netcoreapp1.0`, `netcoreapp1.1`, veya `netstandard1.0` için `netstandard1.6`. Varsayılan değer `netstandard1.4` şeklindedir.

**mvc**

`-f|--framework`-Belirtir [framework](../../standard/frameworks.md) hedef. Değerler: `netcoreapp1.0` veya `netcoreapp1.1`. Varsayılan değer `netcoreapp1.0` şeklindedir.

`-au|--auth`-Kullanılacak kimlik doğrulama türü. Değerler: `None` veya `Individual`. Varsayılan değer `None` şeklindedir.

`-uld|--use-local-db`-Yerel veritabanı yerine SQLite kullanılıp kullanılmayacağını belirtir. Değerler: `true` veya `false`. Varsayılan değer `false` şeklindedir.

---

## <a name="examples"></a>Örnekler

Geçerli dizinde bir F # konsol uygulama projesi oluşturun:

`dotnet new console -lang f#`

(Yalnızca .NET çekirdeği 2.0 SDK veya sonraki sürümleriyle kullanılabilir) belirtilen dizindeki .NET standart bir sınıf kitaplığı projesi oluşturun:

`dotnet new classlib -lang VB -o MyLibrary`

Yeni bir ASP.NET Core C# MVC uygulama projesi geçerli dizinde kimlik doğrulamasız .NET Core 2.0 hedefleme oluşturun:

`dotnet new mvc -au None -f netcoreapp2.0`

.NET Core 2.0 hedefleme yeni bir xUnit uygulaması oluşturun:

`dotnet new xunit --framework netcoreapp2.0`

MVC için kullanılabilir tüm şablonları listeler:

`dotnet new mvc -l`

## <a name="see-also"></a>Ayrıca bkz.

[Yeni dotnet için özel şablonlar](custom-templates.md)  
[Dotnet new için özel şablon oluşturma](~/docs/core/tutorials/create-custom-template.md)  
[DotNet/dotnet-şablonu-samples GitHub depo](https://github.com/dotnet/dotnet-template-samples)  
[Yeni dotnet için kullanılabilir şablonlar](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
