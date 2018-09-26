---
title: Yeni komut dotnet - .NET Core CLI
description: Belirtilen şablonu temel alan yeni .NET Core projeleri dotnet yeni bir komut oluşturur.
author: mairaw
ms.author: mairaw
ms.date: 07/31/2018
ms.openlocfilehash: 396c4ddf09854fa4582226bdb1422f8c929e459b
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47083059"
---
# <a name="dotnet-new"></a>DotNet yeni

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet new` -Yeni Proje, yapılandırma dosyası veya belirtilen şablonu temel alan bir çözüm oluşturur.

## <a name="synopsis"></a>Özeti

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output]
    [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

```console
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a>Açıklama

`dotnet new` Komutu geçerli bir .NET Core projesi başlatmak için kolay bir yol sağlar.

Komut çağrıları [şablon altyapısı](https://github.com/dotnet/templating) yapıları belirtilen şablonu ve seçenekleri bağlı disk oluşturmak için.

## <a name="arguments"></a>Arguments

`TEMPLATE`

Komut çağrıldığında örneği oluşturmak için şablon. Her şablon geçirebilirsiniz belirli seçenekler olabilir. Daha fazla bilgi için [şablon seçeneklerini](#template-options).

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

Komutu, şablonları, varsayılan listesini içerir. Kullanım `dotnet new -l` kullanılabilir şablonların listesini alamadı. Aşağıdaki tablo, .NET Core SDK 2.1.300 önceden yüklenmiş olarak gelen şablonları gösterir. Şablonunuz için varsayılan dili köşeli ayraçlar içinde gösterilmiştir.

|Şablon açıklaması                          | Şablon adı   | Diller     |
|----------------------------------------------|-----------------|---------------|
| Konsol uygulaması                          | `console`       | [C#], F#, VB  |
| Sınıf kitaplığı                                | `classlib`      | [C#], F#, VB  |
| Birim testi projesi                            | `mstest`        | [C#], F#, VB  |
| xUnit test projesi                           | `xunit`         | [C#], F#, VB  |
| Razor sayfası                                   | `page`          | [C#]          |
| MVC ViewImports                              | `viewimports`   | [C#]          |
| MVC ViewStart                                | `viewstart`     | [C#]          |
| ASP.NET Core boş                           | `web`           | [C#] F #      |
| ASP.NET Core Web uygulaması (Model-View-Controller) | `mvc`           | [C#] F #      |
| ASP.NET Core Web uygulaması                         | `razor`         | [C#]          |
| Angular ile ASP.NET Core                    | `angular`       | [C#]          |
| React.js ile ASP.NET Core                   | `react`         | [C#]          |
| ASP.NET Core React.js ve Redux         | `reactredux`    | [C#]          |
| ASP.NET Core Web API'si                         | `webapi`        | [C#] F #      |
| Razor sınıf kitaplığı                          | `razorclasslib` | [C#]          |
| Global.JSON dosyasını                             | `globaljson`    |               |
| NuGet yapılandırma                                 | `nugetconfig`   |               |
| Web yapılandırması                                   | `webconfig`     |               |
| Çözüm dosyası                                | `sln`           |               |

# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)

Komutu, şablonları, varsayılan listesini içerir. Kullanım `dotnet new -l` kullanılabilir şablonların listesini alamadı. Aşağıdaki tablo, .NET Core SDK 2.0 ile önceden yüklenmiş olarak gelen şablonları gösterir. Şablonunuz için varsayılan dili köşeli ayraçlar içinde gösterilmiştir.

|Şablon açıklaması                          | Şablon adı | Diller     |
|----------------------------------------------|---------------|---------------|
| Konsol uygulaması                          | `console`     | [C#], F#, VB  |
| Sınıf kitaplığı                                | `classlib`    | [C#], F#, VB  |
| Birim testi projesi                            | `mstest`      | [C#], F#, VB  |
| xUnit test projesi                           | `xunit`       | [C#], F#, VB  |
| ASP.NET Core boş                           | `web`         | [C#] F #      |
| ASP.NET Core Web uygulaması (Model-View-Controller) | `mvc`         | [C#] F #      |
| ASP.NET Core Web uygulaması                         | `razor`       | [C#]          |
| Angular ile ASP.NET Core                    | `angular`     | [C#]          |
| React.js ile ASP.NET Core                   | `react`       | [C#]          |
| ASP.NET Core React.js ve Redux         | `reactredux`  | [C#]          |
| ASP.NET Core Web API'si                         | `webapi`      | [C#] F #      |
| Global.JSON dosyasını                             | `globaljson`  |               |
| NuGet yapılandırma                                 | `nugetconfig` |               |
| Web yapılandırması                                   | `webconfig`   |               |
| Çözüm dosyası                                | `sln`         |               |
| Razor sayfası                                   | `page`        |               |
| MVC ViewImports                              | `viewimports` |               |
| MVC ViewStart                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

Komutu, şablonları, varsayılan listesini içerir. Kullanım `dotnet new -all` kullanılabilir şablonların listesini alamadı. .NET Core SDK'sı ile önceden yüklenmiş olarak gelen şablonları aşağıdaki tabloda gösterilmektedir 1.x. Şablonunuz için varsayılan dili köşeli ayraçlar içinde gösterilmiştir.

|Şablon açıklaması  | Şablon adı | Diller |
|----------------------|---------------|-----------|
| Konsol uygulaması  | `console`     | [C#] F #  |
| Sınıf kitaplığı        | `classlib`    | [C#] F #  |
| Birim testi projesi    | `mstest`      | [C#] F #  |
| xUnit test projesi   | `xunit`       | [C#] F #  |
| ASP.NET Core boş   | `web`         | [C#]      |
| ASP.NET Core Web uygulaması | `mvc`         | [C#] F #  |
| ASP.NET Core Web API'si | `webapi`      | [C#]      |
| NuGet yapılandırma         | `nugetconfig` |           |
| Web yapılandırması           | `webconfig`   |           |
| Çözüm dosyası        | `sln`         |           |

---

## <a name="options"></a>Seçenekler

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

`--force`

Mevcut dosyaları değiştirmek olsa bile oluşturulması gereken içeriği zorlar. Bir proje çıkış dizinine içerdiğinde, bu gereklidir.

`-h|--help`

Komut için Yardım yazdırır. İçin çağrılabilir `dotnet new` kendisini komutu veya herhangi bir şablon gibi `dotnet new mvc --help`.

`-i|--install <PATH|NUGET_ID>`

Bir kaynak veya şablon paketinden yükler `PATH` veya `NUGET_ID` sağlanan. Bir şablon Paketi yayım öncesi bir sürümü yüklemek istediğiniz sürümü biçiminde belirtmek gerekirse `<package-name>::<package-version>`. Varsayılan olarak, `dotnet new` geçirir \* sürümünü temsil eden en son kararlı Paket sürümü. Bir örneğe bakın [örnekler](#examples) bölümü.

Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz. [yeni dotnet için özel şablonları](custom-templates.md).

`-l|--list`

Belirtilen ad içeren şablonlar listelenmektedir. İçin çağırdıysanız `dotnet new` komut, belirtilen dizinde kullanılabilir olası şablonları listeler. Örnek dizin zaten bir proje içeriyorsa, tüm proje şablonları listesinde değil.

`-lang|--language {C#|F#|VB}`

Oluşturmak için şablon dili. Dil kabul şablon tarafından farklılık gösterir (varsayılan ayarlarında bkz [bağımsız değişkenleri](#arguments) bölümü). Bazı şablonlar için geçerli değil.

> [!NOTE]
> Bazı Kabukları yorumlama `#` olarak bir özel karakter. Bu gibi durumlarda, dil parametre değeri, aşağıdaki gibi alın gerek `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

Oluşturulan çıktı adı. Hiçbir ad belirtilmediği takdirde, geçerli dizin adı kullanılır.

`--nuget-source`

Yükleme sırasında kullanılacak bir NuGet kaynağı belirtir.

`-o|--output <OUTPUT_DIRECTORY>`

Oluşturulan çıktı yerleştirileceği konumu. Geçerli dizin varsayılandır.

`--type`

Şablonları kullanılabilir türlerine göre filtreler. Önceden tanımlanmış değerler şunlardır: "proje", "Item" veya "diğer".

`-u|--uninstall <PATH|NUGET_ID>`

Bir kaynak veya şablon paketini kaldırır `PATH` veya `NUGET_ID` sağlanan.

> [!NOTE]
> Bir şablon kullanarak kaldırmak için bir `PATH`, yol tam olarak nitelemek gerekir. Örneğin, *C:/Users/\<kullanıcı > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak *./GarciaSoftware.ConsoleTemplate.CSharp* içeren gelen Klasör erişemez.
> Ayrıca, şablonu yoldaki son Sonlandırıcı directory eğik çizgi içermez.

# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)

`--force`

Mevcut dosyaları değiştirmek olsa bile oluşturulması gereken içeriği zorlar. Bir proje çıkış dizinine içerdiğinde, bu gereklidir.

`-h|--help`

Komut için Yardım yazdırır. İçin çağrılabilir `dotnet new` kendisini komutu veya herhangi bir şablon gibi `dotnet new mvc --help`.

`-i|--install <PATH|NUGET_ID>`

Bir kaynak veya şablon paketinden yükler `PATH` veya `NUGET_ID` sağlanan. Bir şablon Paketi yayım öncesi bir sürümü yüklemek istediğiniz sürümü biçiminde belirtmek gerekirse `<package-name>::<package-version>`. Varsayılan olarak, `dotnet new` geçirir \* sürümünü temsil eden en son kararlı Paket sürümü. Bir örneğe bakın [örnekler](#examples) bölümü.

Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz. [yeni dotnet için özel şablonları](custom-templates.md).

`-l|--list`

Belirtilen ad içeren şablonlar listelenmektedir. İçin çağırdıysanız `dotnet new` komut, belirtilen dizinde kullanılabilir olası şablonları listeler. Örnek dizin zaten bir proje içeriyorsa, tüm proje şablonları listesinde değil.

`-lang|--language {C#|F#|VB}`

Oluşturmak için şablon dili. Dil kabul şablon tarafından farklılık gösterir (varsayılan ayarlarında bkz [bağımsız değişkenleri](#arguments) bölümü). Bazı şablonlar için geçerli değil.

> [!NOTE]
> Bazı Kabukları yorumlama `#` olarak bir özel karakter. Bu gibi durumlarda, dil parametre değeri, aşağıdaki gibi alın gerek `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

Oluşturulan çıktı adı. Hiçbir ad belirtilmediği takdirde, geçerli dizin adı kullanılır.

`-o|--output <OUTPUT_DIRECTORY>`

Oluşturulan çıktı yerleştirileceği konumu. Geçerli dizin varsayılandır.

`--type`

Şablonları kullanılabilir türlerine göre filtreler. Önceden tanımlanmış değerler şunlardır: "proje", "Item" veya "diğer".

`-u|--uninstall <PATH|NUGET_ID>`

Bir kaynak veya şablon paketini kaldırır `PATH` veya `NUGET_ID` sağlanan.

> [!NOTE]
> Bir kaynağı kullanan bir şablonu kaldırmak için `PATH`, yol tam olarak nitelemek gerekir. Örneğin, *C:/Users/\<kullanıcı > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak *./GarciaSoftware.ConsoleTemplate.CSharp* içeren gelen Klasör erişemez. Ayrıca, şablonu yoldaki son Sonlandırıcı directory eğik çizgi içermez.
> 
> Belirlemek erişemiyorsanız `PATH` veya `NUGET_ID` çalıştıran, bir şablonu kaldırmak için gerekli bağımsız değişken `dotnet new --uninstall` bağımsız değişken yüklü tüm şablonları ve bunları kaldırmak için gerekli bağımsız değişken listesi olmayan.

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

`-all|--show-all`

Belirli türde bir proje için tüm şablonları'nı bağlamında çalıştırılırken gösterir `dotnet new` tek başına komutu. Belirli bir şablon bağlamında gibi çalıştırırken `dotnet new web -all`, `-all` zorla oluşturma bayrak olarak yorumlanır. Bir proje çıkış dizinine içerdiğinde, bu gereklidir.

`-h|--help`

Komut için Yardım yazdırır. İçin çağrılabilir `dotnet new` kendisini komutu veya herhangi bir şablon gibi `dotnet new mvc --help`.

`-l|--list`

Belirtilen ad içeren şablonlar listelenmektedir. İçin çağırdıysanız `dotnet new` komut, belirtilen dizinde kullanılabilir olası şablonları listeler. Örnek dizin zaten bir proje içeriyorsa, tüm proje şablonları listesinde değil.

`-lang|--language {C#|F#}`

Oluşturmak için şablon dili. Dil kabul şablon tarafından farklılık gösterir (varsayılan ayarlarında bkz [bağımsız değişkenleri](#arguments) bölümü). Bazı şablonlar için geçerli değil.

> [!NOTE]
> Bazı Kabukları yorumlama `#` olarak bir özel karakter. Bu gibi durumlarda, dil parametre değeri, aşağıdaki gibi alın gerek `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

Oluşturulan çıktı adı. Hiçbir ad belirtilmediği takdirde, geçerli dizin adı kullanılır.

`-o|--output <OUTPUT_DIRECTORY>`

Oluşturulan çıktı yerleştirileceği konumu. Geçerli dizin varsayılandır.

---

## <a name="template-options"></a>Şablon seçenekleri

Her proje şablonu, ek seçenekler kullanılabilir olabilir. Çekirdek şablonları aşağıdaki ek seçeneklere sahip olursunuz:

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

**konsolunda, angular, react, açarken kilitlenmesi, razorclasslib**

  `--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.

**ClassLib**

`-f|--framework <FRAMEWORK>` -Belirtir [framework](../../standard/frameworks.md) hedef. Değerler: `netcoreapp2.0` bir .NET Core sınıf kitaplığı oluşturmak için veya `netstandard2.0` .NET standart sınıf kitaplığı oluşturmak için. Varsayılan değer `netstandard2.0` şeklindedir.

`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.

**MSTest, xunit**

`-p|--enable-pack` -Etkinleştirir kullanarak projeyi için paketleme [dotnet paketi](dotnet-pack.md).

`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.

**globaljson**

`--sdk-version <VERSION_NUMBER>` -Kullanmak için .NET Core SDK'sı sürümünü belirtir *global.json* dosya.

**Web**

`--exclude-launch-settings` -Hariç *launchSettings.json* oluşturulan şablonundan.

`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.

`--no-https` -Proje HTTPS'yi gerektirmez. Bu seçenek yalnızca geçerlidir `IndividualAuth` veya `OrganizationalAuth` kullanılmayan.

**webapı**

`-au|--auth <AUTHENTICATION_TYPE>` -Kullanılacak kimlik doğrulaması türü. Olası değerler şunlardır:

- `None` -Kimlik doğrulama yok (varsayılan).
- `IndividualB2C` -Azure AD B2C ile kimlik doğrulaması tek tek.
- `SingleOrg` -Kuruluş kimlik doğrulaması için tek bir kiracı.
- `Windows` -Windows kimlik doğrulaması.

`--aad-b2c-instance <INSTANCE>` -Bağlanmak için Azure Active Directory B2C örnek. İle kullanma `IndividualB2C` kimlik doğrulaması. Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.

`-ssp|--susi-policy-id <ID>` -Bu proje için oturum açma ve kaydolma ilke kimliği. İle kullanma `IndividualB2C` kimlik doğrulaması.

`--aad-instance <INSTANCE>` -Bağlanmak için Azure Active Directory örneği. İle kullanma `SingleOrg` kimlik doğrulaması. Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.

`--client-id <ID>` -Bu proje için istemci kimliği. İle kullanma `IndividualB2C` veya `SingleOrg` kimlik doğrulaması. Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.

`--domain <DOMAIN>` -Dizin kiracısı için etki alanı. İle kullanma `SingleOrg` veya `IndividualB2C` kimlik doğrulaması. Varsayılan değer `qualified.domain.name` şeklindedir.

`--tenant-id <ID>` -Tenantıd bağlanmak için kimliği dizini. İle kullanma `SingleOrg` kimlik doğrulaması. Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.

`-r|--org-read-access` -Bu uygulamanın dizine okuma erişimi sağlar. Yalnızca uygulandığı `SingleOrg` veya `MultiOrg` kimlik doğrulaması.

`--exclude-launch-settings` -Hariç *launchSettings.json* oluşturulan şablonundan.

`-uld|--use-local-db` -LocalDB yerine SQLite kullanılması gerektiğini belirtir. Yalnızca uygulandığı `Individual` veya `IndividualB2C` kimlik doğrulaması.

`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.

`--no-https` -Proje HTTPS'yi gerektirmez. `app.UseHsts` ve `app.UseHttpsRedirection` için eklenmez `Startup.Configure`. Bu seçenek yalnızca geçerlidir `Individual`, `IndividualB2C`, `SingleOrg`, veya `MultiOrg` kullanılmayan.

**MVC, razor**

`-au|--auth <AUTHENTICATION_TYPE>` -Kullanılacak kimlik doğrulaması türü. Olası değerler şunlardır:

- `None` -Kimlik doğrulama yok (varsayılan).
- `Individual` -Tek tek kimlik doğrulaması.
- `IndividualB2C` -Azure AD B2C ile kimlik doğrulaması tek tek.
- `SingleOrg` -Kuruluş kimlik doğrulaması için tek bir kiracı.
- `MultiOrg` -Birden fazla Kiracı için Kurumsal kimlik doğrulaması.
- `Windows` -Windows kimlik doğrulaması.

`--aad-b2c-instance <INSTANCE>` -Bağlanmak için Azure Active Directory B2C örnek. İle kullanma `IndividualB2C` kimlik doğrulaması. Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.

`-ssp|--susi-policy-id <ID>` -Bu proje için oturum açma ve kaydolma ilke kimliği. İle kullanma `IndividualB2C` kimlik doğrulaması.

`-rp|--reset-password-policy-id <ID>` -Bu proje için reset parola ilkesi kimliği. İle kullanma `IndividualB2C` kimlik doğrulaması.

`-ep|--edit-profile-policy-id <ID>` -Bu proje için düzenleme profili ilke kimliği. İle kullanma `IndividualB2C` kimlik doğrulaması.

`--aad-instance <INSTANCE>` -Bağlanmak için Azure Active Directory örneği. İle kullanma `SingleOrg` veya `MultiOrg` kimlik doğrulaması. Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.

`--client-id <ID>` -Bu proje için istemci kimliği. İle kullanma `IndividualB2C`, `SingleOrg`, veya `MultiOrg` kimlik doğrulaması. Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.

`--domain <DOMAIN>` -Dizin kiracısı için etki alanı. İle kullanma `SingleOrg` veya `IndividualB2C` kimlik doğrulaması. Varsayılan değer `qualified.domain.name` şeklindedir.

`--tenant-id <ID>` -Tenantıd bağlanmak için kimliği dizini. İle kullanma `SingleOrg` kimlik doğrulaması. Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.

`--callback-path <PATH>` -Yeniden yönlendirme URI'si uygulamanın taban yolu içindeki istek yolu. İle kullanma `SingleOrg` veya `IndividualB2C` kimlik doğrulaması. Varsayılan değer `/signin-oidc` şeklindedir.

`-r|--org-read-access` -Bu uygulamanın dizine okuma erişimi sağlar. Yalnızca uygulandığı `SingleOrg` veya `MultiOrg` kimlik doğrulaması.

`--exclude-launch-settings` -Hariç *launchSettings.json* oluşturulan şablonundan.

`--use-browserlink` -BrowserLink projede içerir.

`-uld|--use-local-db` -LocalDB yerine SQLite kullanılması gerektiğini belirtir. Yalnızca uygulandığı `Individual` veya `IndividualB2C` kimlik doğrulaması.

`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.

`--no-https` -Proje HTTPS'yi gerektirmez. `app.UseHsts` ve `app.UseHttpsRedirection` için eklenmez `Startup.Configure`. Bu seçenek yalnızca geçerlidir `Individual`, `IndividualB2C`, `SingleOrg`, veya `MultiOrg` kullanılmayan.

**Sayfa**

`-na|--namespace <NAMESPACE_NAME>`-Namespace üretilen kod için. Varsayılan değer `MyApp.Namespace` şeklindedir.

`-np|--no-pagemodel` -Bir PageModel olmadan sayfası oluşturur.

**viewimports**

`-na|--namespace <NAMESPACE_NAME>`-Namespace üretilen kod için. Varsayılan değer `MyApp.Namespace` şeklindedir.

# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)

**konsolunda, angular, react, açarken kilitlenmesi**

  `--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.

**ClassLib**

`-f|--framework <FRAMEWORK>` -Belirtir [framework](../../standard/frameworks.md) hedef. Değerler: `netcoreapp2.0` bir .NET Core sınıf kitaplığı oluşturmak için veya `netstandard2.0` .NET standart sınıf kitaplığı oluşturmak için. Varsayılan değer `netstandard2.0` şeklindedir.

`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.

**MSTest, xunit**

`-p|--enable-pack` -Etkinleştirir kullanarak projeyi için paketleme [dotnet paketi](dotnet-pack.md).

`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.

**globaljson**

`--sdk-version <VERSION_NUMBER>` -Kullanmak için .NET Core SDK'sı sürümünü belirtir *global.json* dosya.

**Web**

`--use-launch-settings` -İçeren *launchSettings.json* oluşturulan şablon çıktı.

`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.

**webapı**

`-au|--auth <AUTHENTICATION_TYPE>` -Kullanılacak kimlik doğrulaması türü. Olası değerler şunlardır:

- `None` -Kimlik doğrulama yok (varsayılan).
- `IndividualB2C` -Azure AD B2C ile kimlik doğrulaması tek tek.
- `SingleOrg` -Kuruluş kimlik doğrulaması için tek bir kiracı.
- `Windows` -Windows kimlik doğrulaması.

`--aad-b2c-instance <INSTANCE>` -Bağlanmak için Azure Active Directory B2C örnek. İle kullanma `IndividualB2C` kimlik doğrulaması. Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.

`-ssp|--susi-policy-id <ID>` -Bu proje için oturum açma ve kaydolma ilke kimliği. İle kullanma `IndividualB2C` kimlik doğrulaması.

`--aad-instance <INSTANCE>` -Bağlanmak için Azure Active Directory örneği. İle kullanma `SingleOrg` kimlik doğrulaması. Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.

`--client-id <ID>` -Bu proje için istemci kimliği. İle kullanma `IndividualB2C` veya `SingleOrg` kimlik doğrulaması. Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.

`--domain <DOMAIN>` -Dizin kiracısı için etki alanı. İle kullanma `SingleOrg` veya `IndividualB2C` kimlik doğrulaması. Varsayılan değer `qualified.domain.name` şeklindedir.

`--tenant-id <ID>` -Tenantıd bağlanmak için kimliği dizini. İle kullanma `SingleOrg` kimlik doğrulaması. Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.

`-r|--org-read-access` -Bu uygulamanın dizine okuma erişimi sağlar. Yalnızca uygulandığı `SingleOrg` veya `MultiOrg` kimlik doğrulaması.

`--use-launch-settings` -İçeren *launchSettings.json* oluşturulan şablon çıktı.

`-uld|--use-local-db` -LocalDB yerine SQLite kullanılması gerektiğini belirtir. Yalnızca uygulandığı `Individual` veya `IndividualB2C` kimlik doğrulaması.

`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.

**MVC, razor**

`-au|--auth <AUTHENTICATION_TYPE>` -Kullanılacak kimlik doğrulaması türü. Olası değerler şunlardır:

- `None` -Kimlik doğrulama yok (varsayılan).
- `Individual` -Tek tek kimlik doğrulaması.
- `IndividualB2C` -Azure AD B2C ile kimlik doğrulaması tek tek.
- `SingleOrg` -Kuruluş kimlik doğrulaması için tek bir kiracı.
- `MultiOrg` -Birden fazla Kiracı için Kurumsal kimlik doğrulaması.
- `Windows` -Windows kimlik doğrulaması.

`--aad-b2c-instance <INSTANCE>` -Bağlanmak için Azure Active Directory B2C örnek. İle kullanma `IndividualB2C` kimlik doğrulaması. Varsayılan değer `https://login.microsoftonline.com/tfp/` şeklindedir.

`-ssp|--susi-policy-id <ID>` -Bu proje için oturum açma ve kaydolma ilke kimliği. İle kullanma `IndividualB2C` kimlik doğrulaması.

`-rp|--reset-password-policy-id <ID>` -Bu proje için reset parola ilkesi kimliği. İle kullanma `IndividualB2C` kimlik doğrulaması.

`-ep|--edit-profile-policy-id <ID>` -Bu proje için düzenleme profili ilke kimliği. İle kullanma `IndividualB2C` kimlik doğrulaması.

`--aad-instance <INSTANCE>` -Bağlanmak için Azure Active Directory örneği. İle kullanma `SingleOrg` veya `MultiOrg` kimlik doğrulaması. Varsayılan değer `https://login.microsoftonline.com/` şeklindedir.

`--client-id <ID>` -Bu proje için istemci kimliği. İle kullanma `IndividualB2C`, `SingleOrg`, veya `MultiOrg` kimlik doğrulaması. Varsayılan değer `11111111-1111-1111-11111111111111111` şeklindedir.

`--domain <DOMAIN>` -Dizin kiracısı için etki alanı. İle kullanma `SingleOrg` veya `IndividualB2C` kimlik doğrulaması. Varsayılan değer `qualified.domain.name` şeklindedir.

`--tenant-id <ID>` -Tenantıd bağlanmak için kimliği dizini. İle kullanma `SingleOrg` kimlik doğrulaması. Varsayılan değer `22222222-2222-2222-2222-222222222222` şeklindedir.

`--callback-path <PATH>` -Yeniden yönlendirme URI'si uygulamanın taban yolu içindeki istek yolu. İle kullanma `SingleOrg` veya `IndividualB2C` kimlik doğrulaması. Varsayılan değer `/signin-oidc` şeklindedir.

`-r|--org-read-access` -Bu uygulamanın dizine okuma erişimi sağlar. Yalnızca uygulandığı `SingleOrg` veya `MultiOrg` kimlik doğrulaması.

`--use-launch-settings` -İçeren *launchSettings.json* oluşturulan şablon çıktı.

`--use-browserlink` -BrowserLink projede içerir.

`-uld|--use-local-db` -LocalDB yerine SQLite kullanılması gerektiğini belirtir. Yalnızca uygulandığı `Individual` veya `IndividualB2C` kimlik doğrulaması.

`--no-restore` -Örtük bir geri yükleme proje oluşturma sırasında yürütme değil.

**Sayfa**

`-na|--namespace <NAMESPACE_NAME>`-Namespace üretilen kod için. Varsayılan değer `MyApp.Namespace` şeklindedir.

`-np|--no-pagemodel` -Bir PageModel olmadan sayfası oluşturur.

**viewimports**

`-na|--namespace <NAMESPACE_NAME>`-Namespace üretilen kod için. Varsayılan değer `MyApp.Namespace` şeklindedir.

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

**Konsolu, xunit, mstest, web, webapı**

`-f|--framework` -Belirtir [framework](../../standard/frameworks.md) hedef. Değerler: `netcoreapp1.0` veya `netcoreapp1.1`. Varsayılan değer `netcoreapp1.0` şeklindedir.

**ClassLib**

`-f|--framework` -Belirtir [framework](../../standard/frameworks.md) hedef. Değerler: `netcoreapp1.0`, `netcoreapp1.1`, veya `netstandard1.0` için `netstandard1.6`. Varsayılan değer `netstandard1.4` şeklindedir.

**mvc**

`-f|--framework` -Belirtir [framework](../../standard/frameworks.md) hedef. Değerler: `netcoreapp1.0` veya `netcoreapp1.1`. Varsayılan değer `netcoreapp1.0` şeklindedir.

`-au|--auth` -Kullanılacak kimlik doğrulaması türü. Değerler: `None` veya `Individual`. Varsayılan değer `None` şeklindedir.

`-uld|--use-local-db` -LocalDB yerine SQLite kullanılıp kullanılmayacağını belirtir. Değerler: `true` veya `false`. Varsayılan değer `false` şeklindedir.

---

## <a name="examples"></a>Örnekler

Geçerli dizinde bir F # konsol uygulaması projesi oluşturun:

`dotnet new console -lang F#`

Belirtilen dizin (yalnızca .NET Core SDK 2.0 veya sonraki sürümler ile kullanılabilir) bir .NET Standard sınıf kitaplığı projesi oluşturun:

`dotnet new classlib -lang VB -o MyLibrary`

Kimlik doğrulaması olmayan geçerli dizinde yeni bir ASP.NET Core C# MVC uygulaması projesi oluşturun:

`dotnet new mvc -au None`

Yeni bir xUnit uygulama oluşturun:

`dotnet new xunit`

MVC için tüm şablonları listeler:

`dotnet new mvc -l`

ASP.NET Core (komut seçeneği kullanılabilir .NET Core SDK 1.1 ve yalnızca sonraki sürümleri için) için tek sayfalı uygulama şablonları 2.0 sürümünü yükleyin:

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

Oluşturma bir *global.json* SDK'sı sürüm 2.0.0 (yalnızca .NET Core SDK 2.0 veya sonraki sürümler ile kullanılabilir) ayarı geçerli dizin:

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a>Ayrıca bkz.

* [Yeni dotnet için özel şablonlar](custom-templates.md)  
* [Dotnet new için özel şablon oluşturma](~/docs/core/tutorials/create-custom-template.md)  
* [DotNet/dotnet-şablonu-örnekleri GitHub deposu](https://github.com/dotnet/dotnet-template-samples)  
* [Yeni dotnet şablonları](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
