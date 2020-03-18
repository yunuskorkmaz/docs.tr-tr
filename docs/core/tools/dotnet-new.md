---
title: dotnet yeni komut
description: Dotnet yeni komutu, belirtilen şablonu temel alan yeni .NET Core projeleri oluşturur.
ms.date: 02/13/2020
ms.openlocfilehash: d3c609419596b123f5bfb3ca85cf292a61154a70
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399128"
---
# <a name="dotnet-new"></a>dotnet new

**Bu makale şu şekilde dir:** ✔️ .NET Core 2.0 SDK ve sonraki sürümler

## <a name="name"></a>Adı

`dotnet new`- Belirtilen şablonu temel alan yeni bir proje, yapılandırma dosyası veya çözüm oluşturur.

## <a name="synopsis"></a>Özet

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name]
    [--nuget-source] [-o|--output] [-u|--uninstall] [--update-apply] [--update-check] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

## <a name="description"></a>Açıklama

Komut, `dotnet new` şablona dayalı bir .NET Core projesi veya diğer yapılar oluşturur.

Komut, belirtilen şablon ve seçenekleri temel alan disküzerinde yapıları oluşturmak için [şablon altyapısını](https://github.com/dotnet/templating) çağırır.

## <a name="arguments"></a>Bağımsız Değişkenler

- **`TEMPLATE`**

  Komut çağrıldığında anında başlatılabilmek için şablon. Her şablonun geçirebileceğiniz belirli seçenekleri olabilir. Daha fazla bilgi için [Şablon seçeneklerine](#template-options)bakın.

  Yüklenen tüm `dotnet new --list` şablonların listesini görmek için çalıştırabilirsiniz. Döndürülen `TEMPLATE` tablodaki **Şablonlar** veya **Kısa Ad** sütunundaki metindeki değer tam eşleşme değilse, bu iki sütunda bir alt dize eşleşmesi gerçekleştirilir.

  .NET Core 3.0 SDK ile başlayarak, cli aşağıdaki koşullarda `dotnet new` komutu çağırdığınızda NuGet.org şablonları arar:

  - CLI, çağrıştırırken bir şablon eşleşmesi `dotnet new`bulamazsa, kısmi bile değildir.
  - Şablonun daha yeni bir sürümü varsa. Bu durumda, proje veya yapı oluşturulur, ancak CLI şablonun güncelleştirilmiş bir sürümü hakkında sizi uyarır.

  Komut varsayılan şablonlar listesini içerir. Kullanılabilir `dotnet new -l` şablonların listesini almak için kullanın. Aşağıdaki tabloda .NET Core SDK ile önceden yüklenmiş gelen şablonlar gösterilmektedir. Şabloniçin varsayılan dil parantez içinde gösterilir. Belirli şablon seçeneklerini görmek için kısa ad bağlantısını tıklatın.

| Şablonlar                                    | Kısa ad                      | Dil     | Etiketler                                  | Tanıttı |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| Konsol Uygulaması                          | [Konsol](#console)             | [C#], F#, VB | Ortak/Konsol                        | 1.0        |
| Sınıf kitaplığı                                | [classlib](#classlib)           | [C#], F#, VB | Ortak / Kütüphane                        | 1.0        |
| WPF Uygulaması                              | [Wpf](#wpf)                     | [C#]         | Ortak/WPF                            | 3,0        |
| WPF Sınıf kitaplığı                            | [wpflib](#wpf)                  | [C#]         | Ortak/WPF                            | 3,0        |
| WPF Özel Denetim Kitaplığı                   | [wpfcustomcontrollib](#wpf)     | [C#]         | Ortak/WPF                            | 3,0        |
| WPF Kullanıcı Kontrol Kütüphanesi                     | [wpfusercontrollib](#wpf)       | [C#]         | Ortak/WPF                            | 3,0        |
| Windows Formları (WinForms) Uygulaması         | [Winforms](#winforms)           | [C#]         | Ortak/WinForm'lar                       | 3,0        |
| Windows Formları (WinForms) Sınıf kitaplığı       | [winformslib](#winforms)        | [C#]         | Ortak/WinForm'lar                       | 3,0        |
| İşçi Hizmeti                               | [Işçi](#web-others)           | [C#]         | Ortak/Çalışan/Web                     | 3,0        |
| Ünite Test Projesi                            | [Mstest](#test)                 | [C#], F#, VB | Test /MSTest                           | 1.0        |
| NUnit 3 Test Projesi                         | [nunit](#nunit)                  | [C#], F#, VB | Test /NUnit                            | 2.1.400    |
| NUnit 3 Test Öğesi                            | `nunit-test`                    | [C#], F#, VB | Test /NUnit                            | 2,2        |
| xUnit Test Projesi                           | [xunit](#test)                  | [C#], F#, VB | Test/xUnit                            | 1.0        |
| Jilet Bileşeni                              | `razorcomponent`                | [C#]         | Web/ASP.NET                           | 3,0        |
| Jilet Sayfası                                   | [Sayfası](#page)                   | [C#]         | Web/ASP.NET                           | 2,0        |
| MVC Görünümİthalat                              | [içe görme](#namespace)       | [C#]         | Web/ASP.NET                           | 2,0        |
| MVC Görünüm Başlat                                | `viewstart`                     | [C#]         | Web/ASP.NET                           | 2,0        |
| Blazor Server Uygulaması                            | [blazorserver](#blazorserver)   | [C#]         | Web/Blazor                            | 3,0        |
| ASP.NET Çekirdek Boş                           | [Web](#web)                     | [C#], F #     | Web/Boş                             | 1.0        |
| ASP.NET Çekirdek Web Uygulaması (Model-View-Controller) | [Mvc](#web-options)             | [C#], F #     | Web/MVC                               | 1.0        |
| ASP.NET Çekirdek Web Uygulaması                         | [webapp, jilet](#web-options)   | [C#]         | Web/MVC/Razor Sayfaları                   | 2.2, 2.0   |
| ASP.NET Çekirdek li Açısal                    | [Açısal](#spa)                 | [C#]         | Web/MVC/SPA                           | 2,0        |
| React.js ile ASP.NET Çekirdek                   | [Tepki](#spa)                   | [C#]         | Web/MVC/SPA                           | 2,0        |
| React.js ve Redux ile ASP.NET Çekirdek         | [reactredux](#reactredux)       | [C#]         | Web/MVC/SPA                           | 2,0        |
| Razor Sınıf Kütüphanesi                          | [razorclasslib](#razorclasslib) | [C#]         | Web/Razor/Kütüphane/Razor Sınıf Kütüphanesi | 2.1        |
| ASP.NET Core Web API'si                         | [webapi](#webapi)               | [C#], F #     | Web/WebAPI                            | 1.0        |
| ASP.NET Çekirdek gRPC Hizmeti                    | [grpc](#web-others)             | [C#]         | Web/gRPC                              | 3,0        |
| Protokol Arabellek Dosyası                         | [Proto](#namespace)             |              | Web/gRPC                              | 3,0        |
| dotnet gitignore dosyası                        | `gitignore`                     |              | Config                                | 3,0        |
| global.json dosyası                             | [globaljson](#globaljson)       |              | Config                                | 2,0        |
| NuGet Config                                 | `nugetconfig`                   |              | Config                                | 1.0        |
| dotnet yerel araç bildirimi dosyası              | `tool-manifest`                 |              | Config                                | 3,0        |
| Web Config                                   | `webconfig`                     |              | Config                                | 1.0        |
| Çözüm Dosyası                                | `sln`                           |              | Çözüm                              | 1.0        |

## <a name="options"></a>Seçenekler

- **`--dry-run`**

  Verilen komut çalıştırılırsa ne olacağının bir özetini görüntüler. .NET Core 2.2 SDK'dan beri mevcuttur.

- **`--force`**

  Varolan dosyaları değiştirse bile içeriği oluşturulmaya zorlar. Bu, seçilen şablon çıktı dizinindeki varolan dosyaları geçersiz kılacaksa gereklidir.

- **`-h|--help`**

  Komut için yardım yazdırır. Komutun `dotnet new` kendisi veya herhangi bir şablon için çağrılabilir. Örneğin, `dotnet new mvc --help`.

- **`-i|--install <PATH|NUGET_ID>`**

  Bir şablon paketi yükler `PATH` `NUGET_ID` veya sağlanan. Bir şablon paketinin ön sürüm sürümünü yüklemek istiyorsanız, sürümü ' nin `<package-name>::<package-version>`biçiminde belirtmeniz gerekir. Varsayılan `dotnet new` olarak, \* en son kararlı paket sürümünü temsil eden sürüm için geçer. [Örnekler](#examples) bölümündeki bir örneğe bakın.
  
  Bu komutu çalıştırdığınızda şablonun bir sürümü zaten yüklenmişse, sürüm belirtilmemişse şablon belirtilen sürüme veya en son kararlı sürüme güncelleştirilir.

  Özel şablonlar oluşturma hakkında bilgi [için, nokta yeni için Özel şablonlara](custom-templates.md)bakın.

- **`-l|--list`**

  Belirtilen adı içeren şablonları listeler. Ad belirtilmemişse, tüm şablonları listeler.

- **`-lang|--language {C#|F#|VB}`**

  Oluşturulacak şablonun dili. Kabul edilen dil şablona göre değişir [(bağımsız değişkenler](#arguments) bölümündeki varsayılanlara bakın). Bazı şablonlar için geçerli değildir.

  > [!NOTE]
  > Bazı kabuklar `#` özel bir karakter olarak yorumlanır. Bu gibi durumlarda, dil parametre değerini tırnak içinde içine atl.. Örneğin, `dotnet new console -lang "F#"`.

- **`-n|--name <OUTPUT_NAME>`**

  Oluşturulan çıktının adı. Ad belirtilmemişse, geçerli dizinin adı kullanılır.

- **`--nuget-source`**

  Yükleme sırasında kullanılacak bir NuGet kaynağı belirtir. .NET Core 2.1 SDK'dan beri mevcuttur.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Oluşturulan çıktıyı yerleştirmek için yer. Geçerli dizin varsayılandır.

- **`--type`**

  Kullanılabilir türleri temel alan şablonları filtreler. Önceden tanımlanmış değerler "proje", "öğe" veya "diğer" olarak tanımlanır.

- **`-u|--uninstall [PATH|NUGET_ID]`**

  Bir şablon paketini `PATH` kaldırın `NUGET_ID` veya sağlanan. `<PATH|NUGET_ID>` Değer belirtilmediği zaman, şu anda yüklü olan tüm şablon paketleri ve ilişkili şablonları görüntülenir. `NUGET_ID`Belirtirken, sürüm numarasını eklemeyin.

  Bu seçenek için bir parametre belirtmezseniz, komut yüklenen şablonları ve bunlarla ilgili ayrıntıları listeler.

  > [!NOTE]
  > Bir şablonu kaldırmak `PATH`için , yolu tam olarak nitelemeniz gerekir. Örneğin, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak içeren klasörden *./GarciaSoftware.ConsoleTemplate.CSharp* çalışmaz.
  > Şablon yolunuza sonlandırma dizini kesimieklemeyi eklemeyin.

- **`--update-apply`**

  Şu anda yüklü olan ve bunları yükleyen şablon paketleri için güncelleştirmeolup olmadığını denetler. .NET Core 3.0 SDK'dan beri mevcuttur.

- **`--update-check`**

  Şu anda yüklü olan şablon paketleri için güncelleştirme olup olmadığını denetler. .NET Core 3.0 SDK'dan beri mevcuttur.

## <a name="template-options"></a>Şablon seçenekleri

Her proje şablonunda ek seçenekler olabilir. Çekirdek şablonları aşağıdaki ek seçeneklere sahiptir:

### <a name="console"></a>console

- **`-f|--framework <FRAMEWORK>`**

  Hedef için [çerçeve](../../standard/frameworks.md) belirtir. .NET Core 3.0 SDK'dan beri mevcuttur.

  Aşağıdaki tablo, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerleri listeler:

  | SDK sürümü | Varsayılan değer   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3,0         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  Oluşturulan `LangVersion` proje dosyasındaki özelliği ayarlar. Örneğin, C# 7.3'u kullanmak için kullanın. `--langVersion 7.3` F# için desteklenmez. .NET Core 2.2 SDK'dan beri mevcuttur.

  Varsayılan C# sürümlerinin listesi için [Varsayılanlar'a](../../csharp/language-reference/configure-language-version.md#defaults)bakın.

- **`--no-restore`**

  Belirtilirse, proje oluşturma sırasında örtülü bir geri yükleme yürütmez. .NET Core 2.2 SDK'dan beri mevcuttur.

***

### <a name="classlib"></a>classlib

- **`-f|--framework <FRAMEWORK>`**

  Hedef için [çerçeve](../../standard/frameworks.md) belirtir. Değerler: `netcoreapp<version>` .NET Çekirdek Sınıf Kitaplığı oluşturmak veya `netstandard<version>` .NET Standart Sınıf Kitaplığı oluşturmak için. Varsayılan değer: `netstandard2.0`.

- **`--langVersion <VERSION_NUMBER>`**

  Oluşturulan `LangVersion` proje dosyasındaki özelliği ayarlar. Örneğin, C# 7.3'u kullanmak için kullanın. `--langVersion 7.3` F# için desteklenmez. .NET Core 2.2 SDK'dan beri mevcuttur.

  Varsayılan C# sürümlerinin listesi için [Varsayılanlar'a](../../csharp/language-reference/configure-language-version.md#defaults)bakın.

- **`--no-restore`**

  Proje oluşturma sırasında örtülü bir geri yükleme yürütmez.

***

### <a name="wpf"></a>wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib

- **`-f|--framework <FRAMEWORK>`**

  Hedef için [çerçeve](../../standard/frameworks.md) belirtir. Varsayılan değer: `netcoreapp3.1`. .NET Core 3.1 SDK'dan beri mevcuttur.

- **`--langVersion <VERSION_NUMBER>`**

  Oluşturulan `LangVersion` proje dosyasındaki özelliği ayarlar. Örneğin, C# 7.3'u kullanmak için kullanın. `--langVersion 7.3`

  Varsayılan C# sürümlerinin listesi için [Varsayılanlar'a](../../csharp/language-reference/configure-language-version.md#defaults)bakın.

- **`--no-restore`**

  Proje oluşturma sırasında örtülü bir geri yükleme yürütmez.

***

### <a name="winforms"></a>winforms, winformslib

- **`--langVersion <VERSION_NUMBER>`**

  Oluşturulan `LangVersion` proje dosyasındaki özelliği ayarlar. Örneğin, C# 7.3'u kullanmak için kullanın. `--langVersion 7.3`

  Varsayılan C# sürümlerinin listesi için [Varsayılanlar'a](../../csharp/language-reference/configure-language-version.md#defaults)bakın.

- **`--no-restore`**

  Proje oluşturma sırasında örtülü bir geri yükleme yürütmez.

***

### <a name="web-others"></a>işçi, grpc

- **`-f|--framework <FRAMEWORK>`**

  Hedef için [çerçeve](../../standard/frameworks.md) belirtir. Varsayılan değer: `netcoreapp3.1`. .NET Core 3.1 SDK'dan beri mevcuttur.

- **`--exclude-launch-settings`**

  oluşturulan şablondan *launchSettings.json* hariç tutar.

- **`--no-restore`**

  Proje oluşturma sırasında örtülü bir geri yükleme yürütmez.

***

### <a name="test"></a>mstest, xunit

- **`-f|--framework <FRAMEWORK>`**

  Hedef için [çerçeve](../../standard/frameworks.md) belirtir. Seçenek .NET Core 3.0 SDK beri kullanılabilir.

  Aşağıdaki tablo, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerleri listeler:

  | SDK sürümü | Varsayılan değer   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3,0         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  [Dotnet paketi](dotnet-pack.md)kullanarak proje için paketleme sağlar.

- **`--no-restore`**

  Proje oluşturma sırasında örtülü bir geri yükleme yürütmez.

***

### <a name="nunit"></a>nunit

- **`-f|--framework <FRAMEWORK>`**

  Hedef için [çerçeve](../../standard/frameworks.md) belirtir.

  Aşağıdaki tablo, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerleri listeler:

  | SDK sürümü | Varsayılan değer   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3,0         | `netcoreapp3.0` |
  | 2,2         | `netcoreapp2.2` |
  | 2.1         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  [Dotnet paketi](dotnet-pack.md)kullanarak proje için paketleme sağlar.

- **`--no-restore`**

  Proje oluşturma sırasında örtülü bir geri yükleme yürütmez.

***

### <a name="page"></a>Sayfası

- **`-na|--namespace <NAMESPACE_NAME>`**

  Oluşturulan kod için ad alanı. Varsayılan değer: `MyApp.Namespace`.

- **`-np|--no-pagemodel`**

  Sayfayı PageModel olmadan oluşturur.

***

### <a name="namespace"></a>viewimports, proto

- **`-na|--namespace <NAMESPACE_NAME>`**

  Oluşturulan kod için ad alanı. Varsayılan değer: `MyApp.Namespace`.

***

### <a name="blazorserver"></a>blazorserver

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  Kullanılacak kimlik doğrulama türü. Olası değerler şunlardır:

  - `None`- Kimlik doğrulaması yok (Varsayılan).
  - `Individual`- Bireysel kimlik doğrulama.
  - `IndividualB2C`- Azure AD B2C ile bireysel kimlik doğrulaması.
  - `SingleOrg`- Tek bir kiracı için kuruluş kimlik doğrulaması.
  - `MultiOrg`- Birden çok kiracı için kuruluş kimlik doğrulaması.
  - `Windows`- Windows kimlik doğrulaması.

- **`--aad-b2c-instance <INSTANCE>`**

  Bağlanmak için Azure Active Directory B2C örneği. Kimlik `IndividualB2C` doğrulaması ile kullanın. Varsayılan değer: `https://login.microsoftonline.com/tfp/`.

- **`-ssp|--susi-policy-id <ID>`**

  Bu proje için oturum açma ve kaydolma ilkesi kimliği. Kimlik `IndividualB2C` doğrulaması ile kullanın.

- **`-rp|--reset-password-policy-id <ID>`**

  Bu proje için sıfırlama parola ilkesi kimliği. Kimlik `IndividualB2C` doğrulaması ile kullanın.

- **`-ep|--edit-profile-policy-id <ID>`**

  Bu projenin profil ilke kimliğini edin. Kimlik `IndividualB2C` doğrulaması ile kullanın.

- **`--aad-instance <INSTANCE>`**

  Bağlanmak için Azure Etkin Dizin örneği. Kimlik `SingleOrg` doğrulaması ile kullanın. `MultiOrg` Varsayılan değer: `https://login.microsoftonline.com/`.

- **`--client-id <ID>`**

  Bu projenin Istemci Kimliği. "Kimlik `IndividualB2C` `SingleOrg`doğrulama" `MultiOrg` ile kullanın. Varsayılan değer: `11111111-1111-1111-11111111111111111`.

- **`--domain <DOMAIN>`**

  Dizin kiracı için etki alanı. Kimlik `SingleOrg` doğrulaması ile kullanın. `IndividualB2C` Varsayılan değer: `qualified.domain.name`.

- **`--tenant-id <ID>`**

  Bağlanacak dizinin Kiracı Kimliği. Kimlik `SingleOrg` doğrulaması ile kullanın. Varsayılan değer: `22222222-2222-2222-2222-222222222222`.

- **`--callback-path <PATH>`**

  Yeniden yönlendirme URI uygulamanın temel yolu içinde istek yolu. Kimlik `SingleOrg` doğrulaması ile kullanın. `IndividualB2C` Varsayılan değer: `/signin-oidc`.

- **`-r|--org-read-access`**

  Bu uygulamanın dizine okuma erişimine izin verir. Yalnızca kimlik `SingleOrg` doğrulama `MultiOrg` veya kimlik doğrulama için geçerlidir.

- **`--exclude-launch-settings`**

  oluşturulan şablondan *launchSettings.json* hariç tutar.

- **`--no-https`**

  HTTPS'yi kapatır. Bu seçenek yalnızca `Individual`, `IndividualB2C` `SingleOrg`, `MultiOrg` , , `--auth`için kullanılıyorsa veya kullanılmazsa geçerlidir.

- **`-uld|--use-local-db`**

  SQLite yerine LocalDB'nin kullanılması gerektiğini belirtir. Yalnızca kimlik `Individual` doğrulama `IndividualB2C` veya kimlik doğrulama için geçerlidir.

- **`--no-restore`**

  Proje oluşturma sırasında örtülü bir geri yükleme yürütmez.

***

### <a name="web"></a>web

- **`--exclude-launch-settings`**

  oluşturulan şablondan *launchSettings.json* hariç tutar.

- **`-f|--framework <FRAMEWORK>`**

  Hedef için [çerçeve](../../standard/frameworks.md) belirtir. Seçenek .NET Core 2.2 SDK'da kullanılamaz.

  Aşağıdaki tablo, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerleri listeler:

  | SDK sürümü | Varsayılan değer   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3,0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.1` |

- **`--no-restore`**

  Proje oluşturma sırasında örtülü bir geri yükleme yürütmez.

- **`--no-https`**

  HTTPS'yi kapatır.

***

### <a name="web-options"></a>mvc, webapp

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  Kullanılacak kimlik doğrulama türü. Olası değerler şunlardır:

  - `None`- Kimlik doğrulaması yok (Varsayılan).
  - `Individual`- Bireysel kimlik doğrulama.
  - `IndividualB2C`- Azure AD B2C ile bireysel kimlik doğrulaması.
  - `SingleOrg`- Tek bir kiracı için kuruluş kimlik doğrulaması.
  - `MultiOrg`- Birden çok kiracı için kuruluş kimlik doğrulaması.
  - `Windows`- Windows kimlik doğrulaması.

- **`--aad-b2c-instance <INSTANCE>`**

  Bağlanmak için Azure Active Directory B2C örneği. Kimlik `IndividualB2C` doğrulaması ile kullanın. Varsayılan değer: `https://login.microsoftonline.com/tfp/`.

- **`-ssp|--susi-policy-id <ID>`**

  Bu proje için oturum açma ve kaydolma ilkesi kimliği. Kimlik `IndividualB2C` doğrulaması ile kullanın.

- **`-rp|--reset-password-policy-id <ID>`**

  Bu proje için sıfırlama parola ilkesi kimliği. Kimlik `IndividualB2C` doğrulaması ile kullanın.

- **`-ep|--edit-profile-policy-id <ID>`**

  Bu projenin profil ilke kimliğini edin. Kimlik `IndividualB2C` doğrulaması ile kullanın.

- **`--aad-instance <INSTANCE>`**

  Bağlanmak için Azure Etkin Dizin örneği. Kimlik `SingleOrg` doğrulaması ile kullanın. `MultiOrg` Varsayılan değer: `https://login.microsoftonline.com/`.

- **`--client-id <ID>`**

  Bu projenin Istemci Kimliği. "Kimlik `IndividualB2C` `SingleOrg`doğrulama" `MultiOrg` ile kullanın. Varsayılan değer: `11111111-1111-1111-11111111111111111`.

- **`--domain <DOMAIN>`**

  Dizin kiracı için etki alanı. Kimlik `SingleOrg` doğrulaması ile kullanın. `IndividualB2C` Varsayılan değer: `qualified.domain.name`.

- **`--tenant-id <ID>`**

  Bağlanacak dizinin Kiracı Kimliği. Kimlik `SingleOrg` doğrulaması ile kullanın. Varsayılan değer: `22222222-2222-2222-2222-222222222222`.

- **`--callback-path <PATH>`**

  Yeniden yönlendirme URI uygulamanın temel yolu içinde istek yolu. Kimlik `SingleOrg` doğrulaması ile kullanın. `IndividualB2C` Varsayılan değer: `/signin-oidc`.

- **`-r|--org-read-access`**

  Bu uygulamanın dizine okuma erişimine izin verir. Yalnızca kimlik `SingleOrg` doğrulama `MultiOrg` veya kimlik doğrulama için geçerlidir.

- **`--exclude-launch-settings`**

  oluşturulan şablondan *launchSettings.json* hariç tutar.

- **`--no-https`**

  HTTPS'yi kapatır. Bu seçenek yalnızca `Individual`, `IndividualB2C` `SingleOrg`, `MultiOrg` , , , veya kullanılmazsa geçerlidir.

- **`-uld|--use-local-db`**

  SQLite yerine LocalDB'nin kullanılması gerektiğini belirtir. Yalnızca kimlik `Individual` doğrulama `IndividualB2C` veya kimlik doğrulama için geçerlidir.

- **`-f|--framework <FRAMEWORK>`**

  Hedef için [çerçeve](../../standard/frameworks.md) belirtir. Seçenek .NET Core 3.0 SDK beri kullanılabilir.

  Aşağıdaki tablo, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerleri listeler:

  | SDK sürümü | Varsayılan değer   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3,0         | `netcoreapp3.0` |

- **`--no-restore`**

  Proje oluşturma sırasında örtülü bir geri yükleme yürütmez.

- **`--use-browserlink`**

  Projeye BrowserLink'i içerir. Seçenek .NET Core 2.2 ve 3.1 SDK'da kullanılamaz.

***

### <a name="spa"></a>açısal, tepki

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  Kullanılacak kimlik doğrulama türü. .NET Core 3.0 SDK'dan beri mevcuttur.
  
  Olası değerler şunlardır:

  - `None`- Kimlik doğrulaması yok (Varsayılan).
  - `Individual`- Bireysel kimlik doğrulama.

- **`--exclude-launch-settings`**

  oluşturulan şablondan *launchSettings.json* hariç tutar.

- **`--no-restore`**

  Proje oluşturma sırasında örtülü bir geri yükleme yürütmez.

- **`--no-https`**

  HTTPS'yi kapatır. Bu seçenek yalnızca kimlik `None`doğrulaması.

- **`-uld|--use-local-db`**

  SQLite yerine LocalDB'nin kullanılması gerektiğini belirtir. Yalnızca kimlik `Individual` doğrulama `IndividualB2C` veya kimlik doğrulama için geçerlidir. .NET Core 3.0 SDK'dan beri mevcuttur.

- **`-f|--framework <FRAMEWORK>`**

  Hedef için [çerçeve](../../standard/frameworks.md) belirtir. Seçenek .NET Core 2.2 SDK'da kullanılamaz.

  Aşağıdaki tablo, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerleri listeler:

  | SDK sürümü | Varsayılan değer   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3,0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.0` |

***

### <a name="reactredux"></a>reactredux

- **`--exclude-launch-settings`**

  oluşturulan şablondan *launchSettings.json* hariç tutar.

- **`-f|--framework <FRAMEWORK>`**

  Hedef için [çerçeve](../../standard/frameworks.md) belirtir. Seçenek .NET Core 2.2 SDK'da kullanılamaz.

  Aşağıdaki tablo, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerleri listeler:

  | SDK sürümü | Varsayılan değer   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3,0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.0` |

- **`--no-restore`**

  Proje oluşturma sırasında örtülü bir geri yükleme yürütmez.

- **`--no-https`**

  HTTPS'yi kapatır.

***

### <a name="razorclasslib"></a>razorclasslib

- **`--no-restore`**

  Proje oluşturma sırasında örtülü bir geri yükleme yürütmez.

- **`-s|--support-pages-and-views`**

  Bu kitaplığa bileşenlere ek olarak geleneksel Razor sayfaları ve Görünümler eklemeyi destekler. .NET Core 3.0 SDK'dan beri mevcuttur.

***
  
### <a name="webapi"></a>webapi

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  Kullanılacak kimlik doğrulama türü. Olası değerler şunlardır:

  - `None`- Kimlik doğrulaması yok (Varsayılan).
  - `IndividualB2C`- Azure AD B2C ile bireysel kimlik doğrulaması.
  - `SingleOrg`- Tek bir kiracı için kuruluş kimlik doğrulaması.
  - `Windows`- Windows kimlik doğrulaması.

- **`--aad-b2c-instance <INSTANCE>`**

  Bağlanmak için Azure Active Directory B2C örneği. Kimlik `IndividualB2C` doğrulaması ile kullanın. Varsayılan değer: `https://login.microsoftonline.com/tfp/`.

- **`-ssp|--susi-policy-id <ID>`**

  Bu proje için oturum açma ve kaydolma ilkesi kimliği. Kimlik `IndividualB2C` doğrulaması ile kullanın.

- **`--aad-instance <INSTANCE>`**

  Bağlanmak için Azure Etkin Dizin örneği. Kimlik `SingleOrg` doğrulaması ile kullanın. Varsayılan değer: `https://login.microsoftonline.com/`.

- **`--client-id <ID>`**

  Bu projenin Istemci Kimliği. Kimlik `IndividualB2C` doğrulaması ile kullanın. `SingleOrg` Varsayılan değer: `11111111-1111-1111-11111111111111111`.

- **`--domain <DOMAIN>`**

  Dizin kiracı için etki alanı. Kimlik `IndividualB2C` doğrulaması ile kullanın. `SingleOrg` Varsayılan değer: `qualified.domain.name`.

- **`--tenant-id <ID>`**

  Bağlanacak dizinin Kiracı Kimliği. Kimlik `SingleOrg` doğrulaması ile kullanın. Varsayılan değer: `22222222-2222-2222-2222-222222222222`.

- **`-r|--org-read-access`**

  Bu uygulamanın dizine okuma erişimine izin verir. Yalnızca kimlik `SingleOrg` doğrulama için geçerlidir.

- **`--exclude-launch-settings`**

  oluşturulan şablondan *launchSettings.json* hariç tutar.

- **`--no-https`**

  HTTPS'yi kapatır. `app.UseHsts`ve `app.UseHttpsRedirection` `Startup.Configure`eklenmez. Bu seçenek yalnızca `IndividualB2C` kimlik `SingleOrg` doğrulaması için kullanılıyorsa veya kullanılmamışsa geçerlidir.

- **`-uld|--use-local-db`**

  SQLite yerine LocalDB'nin kullanılması gerektiğini belirtir. Yalnızca kimlik `IndividualB2C` doğrulama için geçerlidir.

- **`-f|--framework <FRAMEWORK>`**

  Hedef için [çerçeve](../../standard/frameworks.md) belirtir. Seçenek .NET Core 2.2 SDK'da kullanılamaz.

  Aşağıdaki tablo, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerleri listeler:

  | SDK sürümü | Varsayılan değer   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3,0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.1` |

- **`--no-restore`**

  Proje oluşturma sırasında örtülü bir geri yükleme yürütmez.

***

### <a name="globaljson"></a>globaljson

- **`--sdk-version <VERSION_NUMBER>`**

  .NET Core SDK sürümünü *global.json* dosyasında kullanmak üzere belirtir.

***

## <a name="examples"></a>Örnekler

- Şablon adını belirterek c# konsolu uygulama projesi oluşturun:

  ```dotnetcli
  dotnet new "Console Application"
  ```

- Geçerli dizinde bir F# konsolu uygulama projesi oluşturun:

  ```dotnetcli
  dotnet new console -lang F#
  ```

- Belirtilen dizinde bir .NET Standart sınıf kitaplığı projesi oluşturun:

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- Geçerli dizinde kimlik doğrulaması olmadan yeni bir ASP.NET Core C# MVC projesi oluşturun:

  ```dotnetcli
  dotnet new mvc -au None
  ```

- Yeni bir xUnit projesi oluşturun:

  ```dotnetcli
  dotnet new xunit
  ```

- Tek Sayfa Uygulaması (SPA) şablonları için kullanılabilen tüm şablonları listeleyin:

  ```dotnetcli
  dotnet new spa -l
  ```

- *Biz* alt dize ile eşleşen tüm şablonları listeleyin. Tam eşleşme bulunamadı, bu nedenle alt dize eşleştirme hem kısa ad hem de ad sütunlarına karşı çalışır.

  ```dotnetcli
  dotnet new we -l
  ```

- Ng eşleşen şablonu çağırmak için girişimi *.* Tek bir eşleşme belirlenemezse, kısmi eşleşmeolan şablonları listeleyin.

  ```dotnetcli
  dotnet new ng
  ```

- ASP.NET Core için SPA şablonlarının 2.0 sürümünü yükleyin:

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- Yüklenen şablonları ve bunlarla ilgili ayrıntıları ve bunları nasıl kaldırılabildiğini listeleyin:

  ```dotnetcli
  dotnet new -u
  ```

- Geçerli dizinde SDK sürümünü 3.1.101 olarak ayarlayarak *global.json* oluşturun:

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a>Ayrıca bkz.

- [Dotnet yeni için özel şablonlar](custom-templates.md)
- [Dotnet new için özel şablon oluşturma](../tutorials/cli-templates-create-item-template.md)
- [dotnet/dotnet-şablon-örnekleri GitHub repo](https://github.com/dotnet/dotnet-template-samples)
- [dotnet yeni için kullanılabilir şablonlar](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
