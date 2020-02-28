---
title: DotNet yeni komut
description: DotNet New komutu, belirtilen şablona göre yeni .NET Core projeleri oluşturur.
ms.date: 02/13/2020
ms.openlocfilehash: d3c609419596b123f5bfb3ca85cf292a61154a70
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157225"
---
# <a name="dotnet-new"></a>dotnet new

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,0 SDK ve sonraki sürümleri

## <a name="name"></a>Adı

`dotnet new`-belirtilen şablona göre yeni bir proje, yapılandırma dosyası veya çözüm oluşturur.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name]
    [--nuget-source] [-o|--output] [-u|--uninstall] [--update-apply] [--update-check] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

## <a name="description"></a>Açıklama

`dotnet new` komutu bir şablonu temel alan bir .NET Core projesi veya diğer yapılar oluşturur.

Komutu, belirtilen şablon ve seçeneklere göre diskteki yapıtları oluşturmak için [şablon altyapısını](https://github.com/dotnet/templating) çağırır.

## <a name="arguments"></a>Bağımsız Değişkenler

- **`TEMPLATE`**

  Komut çağrıldığında örnek oluşturulacak şablon. Her şablonun geçirebilmeniz için özel seçenekleri olabilir. Daha fazla bilgi için bkz. [şablon seçenekleri](#template-options).

  Tüm yüklü şablonların listesini görmek için `dotnet new --list` çalıştırabilirsiniz. `TEMPLATE` değeri, döndürülen tablodaki **Şablonlar** veya **kısa ad** sütunundaki metinde tam eşleşme değilse, bu iki sütunda bir alt dize eşleşmesi gerçekleştirilir.

  .NET Core 3,0 SDK ile başlayarak, CLı, aşağıdaki koşullarda `dotnet new` komutunu çağırdığınızda NuGet.org içindeki şablonları arar:

  - CLı, `dotnet new`çağrılırken bir şablon eşleşmesi bulamazsa, bu da kısmi değildir.
  - Şablonun daha yeni bir sürümü kullanılabilir. Bu durumda, proje veya yapıt oluşturulur ancak CLı, şablonun güncelleştirilmiş bir sürümü hakkında sizi uyarır.

  Komut, şablonların varsayılan bir listesini içerir. Kullanılabilir şablonların bir listesini almak için `dotnet new -l` kullanın. Aşağıdaki tabloda, .NET Core SDK ile önceden yüklenmiş olan şablonlar gösterilmektedir. Şablon için varsayılan dil, köşeli ayraçlar içinde gösterilir. Özel şablon seçeneklerini görmek için kısa ad bağlantısına tıklayın.

| Şablonlar                                    | Kısa ad                      | Dil     | Etiketler                                  | Dağıtıla |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| Konsol Uygulaması                          | [konsola](#console)             | [C#], F#, VB | Ortak/konsol                        | 1.0        |
| Sınıf kitaplığı                                | [projesinin](#classlib)           | [C#], F#, VB | Ortak/Kitaplık                        | 1.0        |
| WPF Uygulaması                              | [WPF](#wpf)                     | [C#]         | Ortak/WPF                            | 3.0        |
| WPF sınıf kitaplığı                            | [wpflib](#wpf)                  | [C#]         | Ortak/WPF                            | 3.0        |
| WPF Özel Denetim Kitaplığı                   | [wpfcustomcontrollib](#wpf)     | [C#]         | Ortak/WPF                            | 3.0        |
| WPF Kullanıcı Denetimi Kütüphanesi                     | [wpfusercontrollib](#wpf)       | [C#]         | Ortak/WPF                            | 3.0        |
| Windows Forms (WinForms) uygulaması         | [WinForms](#winforms)           | [C#]         | Ortak/WinForms                       | 3.0        |
| Windows Forms (WinForms) sınıf kitaplığı       | [winformslib](#winforms)        | [C#]         | Ortak/WinForms                       | 3.0        |
| Çalışan hizmeti                               | [ından](#web-others)           | [C#]         | Ortak/çalışan/Web                     | 3.0        |
| Birim testi projesi                            | ['i](#test)                 | [C#], F#, VB | Test/MSTest                           | 1.0        |
| NUnit 3 test projesi                         | [NUnit](#nunit)                  | [C#], F#, VB | Test/NUnit                            | 2.1.400    |
| NUnit 3 test öğesi                            | `nunit-test`                    | [C#], F#, VB | Test/NUnit                            | 2.2        |
| xUnit test projesi                           | [xUnit](#test)                  | [C#], F#, VB | Test/xUnit                            | 1.0        |
| Razor bileşeni                              | `razorcomponent`                | [C#]         | Web/ASP. NET                           | 3.0        |
| Razor sayfası                                   | [sayfasında](#page)                   | [C#]         | Web/ASP. NET                           | 2,0        |
| MVC Viewıtemts                              | [viewıtems 'lar](#namespace)       | [C#]         | Web/ASP. NET                           | 2,0        |
| MVC ViewStart                                | `viewstart`                     | [C#]         | Web/ASP. NET                           | 2,0        |
| Blazor sunucusu uygulaması                            | [blazorserver](#blazorserver)   | [C#]         | Web/Blazor                            | 3.0        |
| ASP.NET Core boş                           | [Web](#web)                     | [C#],F#     | Web/boş                             | 1.0        |
| ASP.NET Core Web uygulaması (Model-View-Controller) | [MVC](#web-options)             | [C#],F#     | Web/MVC                               | 1.0        |
| ASP.NET Core Web uygulaması                         | [WEBAPP, Razor](#web-options)   | [C#]         | Web/MVC/Razor Pages                   | 2,2, 2,0   |
| Angular ile ASP.NET Core                    | [Angular](#spa)                 | [C#]         | MVC/Web/SPA                           | 2,0        |
| Tepki verme. js ile ASP.NET Core                   | [tıkla](#spa)                   | [C#]         | MVC/Web/SPA                           | 2,0        |
| Yanıt verir. js ve Redux ile ASP.NET Core         | [reactredux](#reactredux)       | [C#]         | MVC/Web/SPA                           | 2,0        |
| Razor sınıf kitaplığı                          | [razorclasslib](#razorclasslib) | [C#]         | Web/Razor/kitaplık/Razor sınıfı kitaplığı | 2.1        |
| ASP.NET Core Web API'si                         | [WebApi](#webapi)               | [C#],F#     | Web/WebAPI                            | 1.0        |
| ASP.NET Core gRPC hizmeti                    | [GRPC](#web-others)             | [C#]         | Web/gRPC                              | 3.0        |
| Protokol arabelleği dosyası                         | [Proto](#namespace)             |              | Web/gRPC                              | 3.0        |
| DotNet gitignore dosyası                        | `gitignore`                     |              | Config                                | 3.0        |
| Global. JSON dosyası                             | [globaljson](#globaljson)       |              | Config                                | 2,0        |
| NuGet yapılandırması                                 | `nugetconfig`                   |              | Config                                | 1.0        |
| DotNet yerel araç bildirim dosyası              | `tool-manifest`                 |              | Config                                | 3.0        |
| Web yapılandırması                                   | `webconfig`                     |              | Config                                | 1.0        |
| Çözüm dosyası                                | `sln`                           |              | Çözüm                              | 1.0        |

## <a name="options"></a>Seçenekler

- **`--dry-run`**

  Verilen komutun çalıştırılmasından sonra ne olacağını gösteren bir Özet görüntüler. .NET Core 2,2 SDK 'dan beri kullanılabilir.

- **`--force`**

  Var olan dosyaları değiştirebilse bile içeriğin oluşturulmasını zorlar. Seçilen şablon çıkış dizinindeki mevcut dosyaları geçersiz kılacağından bu gereklidir.

- **`-h|--help`**

  Komut için yardım yazdırır. `dotnet new` komutun kendisi veya herhangi bir şablon için çağrılabilir. Örneğin, `dotnet new mvc --help`.

- **`-i|--install <PATH|NUGET_ID>`**

  `PATH` veya sağlanmış `NUGET_ID` bir şablon paketi kurar. Şablon paketinin bir ön sürümünü yüklemek istiyorsanız, `<package-name>::<package-version>`biçiminde sürümü belirtmeniz gerekir. Varsayılan olarak, `dotnet new` en son kararlı paket sürümünü temsil eden sürüm için \* geçirir. [Örnekler](#examples) bölümündeki bir örneğe bakın.
  
  Bu komutu çalıştırdığınızda şablonun bir sürümü zaten yüklüyse, şablon belirtilen sürüme veya sürüm belirtilmemişse en son kararlı sürüme güncelleştirilir.

  Özel şablonlar oluşturma hakkında daha fazla bilgi için bkz. [DotNet New Için özel şablonlar](custom-templates.md).

- **`-l|--list`**

  Belirtilen adı içeren şablonları listeler. Ad belirtilmemişse, tüm şablonları listeler.

- **`-lang|--language {C#|F#|VB}`**

  Oluşturulacak şablonun dili. Kabul edilen dil şablona göre değişir (bkz. [arguments](#arguments) bölümünde Varsayılanlar). Bazı şablonlar için geçerli değildir.

  > [!NOTE]
  > Bazı kabuklar, `#` özel bir karakter olarak yorumlar. Bu durumlarda, dil parametre değerini tırnak içine alın. Örneğin, `dotnet new console -lang "F#"`.

- **`-n|--name <OUTPUT_NAME>`**

  Oluşturulan çıkışın adı. Ad belirtilmemişse, geçerli dizinin adı kullanılır.

- **`--nuget-source`**

  Yüklemesi sırasında kullanılacak bir NuGet kaynağını belirtir. .NET Core 2,1 SDK 'dan beri kullanılabilir.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Oluşturulan çıkışın yerleştirileceği konum. Geçerli dizin varsayılandır.

- **`--type`**

  Şablonları kullanılabilir türlerine göre filtreler. Önceden tanımlanmış değerler şunlardır "proje", "öğe" veya "diğer".

- **`-u|--uninstall [PATH|NUGET_ID]`**

  `PATH` veya sağlanmış `NUGET_ID` bir şablon paketini kaldırır. `<PATH|NUGET_ID>` değeri belirtilmediğinde, yüklü olan tüm şablon paketleri ve bunlarla ilişkili şablonlar görüntülenir. `NUGET_ID`belirtirken sürüm numarasını eklemeyin.

  Bu seçeneğe bir parametre belirtmezseniz, komut, yüklü şablonları ve bunlarla ilgili ayrıntıları listeler.

  > [!NOTE]
  > Bir `PATH`kullanarak bir şablonu kaldırmak için, yolu tam olarak nitelemeniz gerekir. Örneğin, *C:/kullanıcılar/\<USER >/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak içeren klasörden *./GarciaSoftware.ConsoleTemplate.CSharp* olmayacaktır.
  > Şablon yolunuzda son Sonlandırıcı Dizin eğik çizgisi eklemeyin.

- **`--update-apply`**

  Şu anda yüklü olan şablon paketleri için kullanılabilir güncelleştirmelerin olup olmadığını denetler ve bunları kurar. .NET Core 3,0 SDK 'dan beri kullanılabilir.

- **`--update-check`**

  Şu anda yüklü olan şablon paketleri için kullanılabilir güncelleştirmeler olup olmadığını denetler. .NET Core 3,0 SDK 'dan beri kullanılabilir.

## <a name="template-options"></a>Şablon seçenekleri

Her proje şablonunda ek seçenekler bulunabilir. Çekirdek şablonlar aşağıdaki ek seçeneklere sahiptir:

### <a name="console"></a>console

- **`-f|--framework <FRAMEWORK>`**

  Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir. .NET Core 3,0 SDK 'dan beri kullanılabilir.

  Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:

  | SDK sürümü | Varsayılan değer   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  Oluşturulan proje dosyasındaki `LangVersion` özelliğini ayarlar. Örneğin, 7,3 kullanmak C# için `--langVersion 7.3` kullanın. İçin F#desteklenmez. .NET Core 2,2 SDK 'dan beri kullanılabilir.

  Varsayılan C# sürümlerin bir listesi için bkz. [Varsayılanlar](../../csharp/language-reference/configure-language-version.md#defaults).

- **`--no-restore`**

  Belirtilmişse, proje oluşturma sırasında örtük geri yükleme yürütmez. .NET Core 2,2 SDK 'dan beri kullanılabilir.

***

### <a name="classlib"></a>projesinin

- **`-f|--framework <FRAMEWORK>`**

  Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir. Değerler: bir .NET Standard sınıf kitaplığı oluşturmak için bir .NET Core sınıf kitaplığı veya `netstandard<version>` oluşturmak `netcoreapp<version>`. Varsayılan değer: `netstandard2.0`.

- **`--langVersion <VERSION_NUMBER>`**

  Oluşturulan proje dosyasındaki `LangVersion` özelliğini ayarlar. Örneğin, 7,3 kullanmak C# için `--langVersion 7.3` kullanın. İçin F#desteklenmez. .NET Core 2,2 SDK 'dan beri kullanılabilir.

  Varsayılan C# sürümlerin bir listesi için bkz. [Varsayılanlar](../../csharp/language-reference/configure-language-version.md#defaults).

- **`--no-restore`**

  Proje oluşturma sırasında örtük geri yükleme yürütülmez.

***

### <a name="wpf"></a>WPF, wpflib, wpfcustomcontrollib, wpfusercontrollib

- **`-f|--framework <FRAMEWORK>`**

  Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir. Varsayılan değer: `netcoreapp3.1`. .NET Core 3,1 SDK 'dan beri kullanılabilir.

- **`--langVersion <VERSION_NUMBER>`**

  Oluşturulan proje dosyasındaki `LangVersion` özelliğini ayarlar. Örneğin, 7,3 kullanmak C# için `--langVersion 7.3` kullanın.

  Varsayılan C# sürümlerin bir listesi için bkz. [Varsayılanlar](../../csharp/language-reference/configure-language-version.md#defaults).

- **`--no-restore`**

  Proje oluşturma sırasında örtük geri yükleme yürütülmez.

***

### <a name="winforms"></a>WinForms, winformslib

- **`--langVersion <VERSION_NUMBER>`**

  Oluşturulan proje dosyasındaki `LangVersion` özelliğini ayarlar. Örneğin, 7,3 kullanmak C# için `--langVersion 7.3` kullanın.

  Varsayılan C# sürümlerin bir listesi için bkz. [Varsayılanlar](../../csharp/language-reference/configure-language-version.md#defaults).

- **`--no-restore`**

  Proje oluşturma sırasında örtük geri yükleme yürütülmez.

***

### <a name="web-others"></a>çalışan, GRPC

- **`-f|--framework <FRAMEWORK>`**

  Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir. Varsayılan değer: `netcoreapp3.1`. .NET Core 3,1 SDK 'dan beri kullanılabilir.

- **`--exclude-launch-settings`**

  Oluşturulan şablondan *Launchsettings. JSON* öğesini dışlar.

- **`--no-restore`**

  Proje oluşturma sırasında örtük geri yükleme yürütülmez.

***

### <a name="test"></a>MSTest, xUnit

- **`-f|--framework <FRAMEWORK>`**

  Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir. .NET Core 3,0 SDK 'dan beri kullanılabilir seçeneği.

  Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:

  | SDK sürümü | Varsayılan değer   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  [DotNet Pack](dotnet-pack.md)kullanarak proje için paketleme imkanı sunar.

- **`--no-restore`**

  Proje oluşturma sırasında örtük geri yükleme yürütülmez.

***

### <a name="nunit"></a>NUnit

- **`-f|--framework <FRAMEWORK>`**

  Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir.

  Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:

  | SDK sürümü | Varsayılan değer   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.2         | `netcoreapp2.2` |
  | 2.1         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  [DotNet Pack](dotnet-pack.md)kullanarak proje için paketleme imkanı sunar.

- **`--no-restore`**

  Proje oluşturma sırasında örtük geri yükleme yürütülmez.

***

### <a name="page"></a>sayfa

- **`-na|--namespace <NAMESPACE_NAME>`**

  Oluşturulan kod için ad alanı. Varsayılan değer: `MyApp.Namespace`.

- **`-np|--no-pagemodel`**

  PageModel olmadan sayfayı oluşturur.

***

### <a name="namespace"></a>viewıtemler, Proto

- **`-na|--namespace <NAMESPACE_NAME>`**

  Oluşturulan kod için ad alanı. Varsayılan değer: `MyApp.Namespace`.

***

### <a name="blazorserver"></a>blazorserver

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  Kullanılacak kimlik doğrulaması türü. Olası değerler şunlardır:

  - `None`-kimlik doğrulaması yok (varsayılan).
  - `Individual` bireysel kimlik doğrulaması.
  - `IndividualB2C` bireysel kimlik doğrulama Azure AD B2C.
  - tek bir kiracı için `SingleOrg` kurumsal kimlik doğrulaması.
  - `MultiOrg`-birden çok kiracı için kuruluş kimlik doğrulaması.
  - `Windows`-Windows kimlik doğrulaması.

- **`--aad-b2c-instance <INSTANCE>`**

  Bağlanılacak Azure Active Directory B2C örneği. `IndividualB2C` kimlik doğrulamasıyla kullanın. Varsayılan değer: `https://login.microsoftonline.com/tfp/`.

- **`-ssp|--susi-policy-id <ID>`**

  Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI. `IndividualB2C` kimlik doğrulamasıyla kullanın.

- **`-rp|--reset-password-policy-id <ID>`**

  Bu proje için parola sıfırlama ilkesi KIMLIĞI. `IndividualB2C` kimlik doğrulamasıyla kullanın.

- **`-ep|--edit-profile-policy-id <ID>`**

  Bu proje için profil ilke KIMLIĞINI Düzenle. `IndividualB2C` kimlik doğrulamasıyla kullanın.

- **`--aad-instance <INSTANCE>`**

  Bağlanılacak Azure Active Directory örneği. `SingleOrg` veya `MultiOrg` kimlik doğrulamasıyla kullanın. Varsayılan değer: `https://login.microsoftonline.com/`.

- **`--client-id <ID>`**

  Bu projenin Istemci KIMLIĞI. `IndividualB2C`, `SingleOrg`veya `MultiOrg` kimlik doğrulamasıyla kullanın. Varsayılan değer: `11111111-1111-1111-11111111111111111`.

- **`--domain <DOMAIN>`**

  Dizin kiracının etki alanı. `SingleOrg` veya `IndividualB2C` kimlik doğrulamasıyla kullanın. Varsayılan değer: `qualified.domain.name`.

- **`--tenant-id <ID>`**

  Bağlanılacak dizinin Tenantıd KIMLIĞI. `SingleOrg` kimlik doğrulamasıyla kullanın. Varsayılan değer: `22222222-2222-2222-2222-222222222222`.

- **`--callback-path <PATH>`**

  Uygulamanın yeniden yönlendirme URI 'sinin temel yolundaki istek yolu. `SingleOrg` veya `IndividualB2C` kimlik doğrulamasıyla kullanın. Varsayılan değer: `/signin-oidc`.

- **`-r|--org-read-access`**

  Bu uygulamanın dizine okuma erişimini sağlar. Yalnızca `SingleOrg` veya `MultiOrg` kimlik doğrulaması için geçerlidir.

- **`--exclude-launch-settings`**

  Oluşturulan şablondan *Launchsettings. JSON* öğesini dışlar.

- **`--no-https`**

  HTTPS 'yi kapatır. Bu seçenek yalnızca `Individual`, `IndividualB2C`, `SingleOrg`veya `MultiOrg` `--auth`için kullanılmıyorsa geçerlidir.

- **`-uld|--use-local-db`**

  SQLite yerine LocalDB kullanılması gerektiğini belirtir. Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.

- **`--no-restore`**

  Proje oluşturma sırasında örtük geri yükleme yürütülmez.

***

### <a name="web"></a>web

- **`--exclude-launch-settings`**

  Oluşturulan şablondan *Launchsettings. JSON* öğesini dışlar.

- **`-f|--framework <FRAMEWORK>`**

  Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir. Seçenek .NET Core 2,2 SDK sürümünde kullanılamaz.

  Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:

  | SDK sürümü | Varsayılan değer   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.1` |

- **`--no-restore`**

  Proje oluşturma sırasında örtük geri yükleme yürütülmez.

- **`--no-https`**

  HTTPS 'yi kapatır.

***

### <a name="web-options"></a>MVC, WebApp

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  Kullanılacak kimlik doğrulaması türü. Olası değerler şunlardır:

  - `None`-kimlik doğrulaması yok (varsayılan).
  - `Individual` bireysel kimlik doğrulaması.
  - `IndividualB2C` bireysel kimlik doğrulama Azure AD B2C.
  - tek bir kiracı için `SingleOrg` kurumsal kimlik doğrulaması.
  - `MultiOrg`-birden çok kiracı için kuruluş kimlik doğrulaması.
  - `Windows`-Windows kimlik doğrulaması.

- **`--aad-b2c-instance <INSTANCE>`**

  Bağlanılacak Azure Active Directory B2C örneği. `IndividualB2C` kimlik doğrulamasıyla kullanın. Varsayılan değer: `https://login.microsoftonline.com/tfp/`.

- **`-ssp|--susi-policy-id <ID>`**

  Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI. `IndividualB2C` kimlik doğrulamasıyla kullanın.

- **`-rp|--reset-password-policy-id <ID>`**

  Bu proje için parola sıfırlama ilkesi KIMLIĞI. `IndividualB2C` kimlik doğrulamasıyla kullanın.

- **`-ep|--edit-profile-policy-id <ID>`**

  Bu proje için profil ilke KIMLIĞINI Düzenle. `IndividualB2C` kimlik doğrulamasıyla kullanın.

- **`--aad-instance <INSTANCE>`**

  Bağlanılacak Azure Active Directory örneği. `SingleOrg` veya `MultiOrg` kimlik doğrulamasıyla kullanın. Varsayılan değer: `https://login.microsoftonline.com/`.

- **`--client-id <ID>`**

  Bu projenin Istemci KIMLIĞI. `IndividualB2C`, `SingleOrg`veya `MultiOrg` kimlik doğrulamasıyla kullanın. Varsayılan değer: `11111111-1111-1111-11111111111111111`.

- **`--domain <DOMAIN>`**

  Dizin kiracının etki alanı. `SingleOrg` veya `IndividualB2C` kimlik doğrulamasıyla kullanın. Varsayılan değer: `qualified.domain.name`.

- **`--tenant-id <ID>`**

  Bağlanılacak dizinin Tenantıd KIMLIĞI. `SingleOrg` kimlik doğrulamasıyla kullanın. Varsayılan değer: `22222222-2222-2222-2222-222222222222`.

- **`--callback-path <PATH>`**

  Uygulamanın yeniden yönlendirme URI 'sinin temel yolundaki istek yolu. `SingleOrg` veya `IndividualB2C` kimlik doğrulamasıyla kullanın. Varsayılan değer: `/signin-oidc`.

- **`-r|--org-read-access`**

  Bu uygulamanın dizine okuma erişimini sağlar. Yalnızca `SingleOrg` veya `MultiOrg` kimlik doğrulaması için geçerlidir.

- **`--exclude-launch-settings`**

  Oluşturulan şablondan *Launchsettings. JSON* öğesini dışlar.

- **`--no-https`**

  HTTPS 'yi kapatır. Bu seçenek yalnızca `Individual`, `IndividualB2C`, `SingleOrg`veya `MultiOrg` kullanılmıyorsa geçerlidir.

- **`-uld|--use-local-db`**

  SQLite yerine LocalDB kullanılması gerektiğini belirtir. Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir.

- **`-f|--framework <FRAMEWORK>`**

  Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir. .NET Core 3,0 SDK 'dan beri kullanılabilir seçeneği.

  Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:

  | SDK sürümü | Varsayılan değer   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |

- **`--no-restore`**

  Proje oluşturma sırasında örtük geri yükleme yürütülmez.

- **`--use-browserlink`**

  Projedeki BrowserLink öğesini içerir. Seçenek .NET Core 2,2 ve 3,1 SDK sürümünde kullanılamaz.

***

### <a name="spa"></a>Angular, tepki verme

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  Kullanılacak kimlik doğrulaması türü. .NET Core 3,0 SDK 'dan beri kullanılabilir.
  
  Olası değerler şunlardır:

  - `None`-kimlik doğrulaması yok (varsayılan).
  - `Individual` bireysel kimlik doğrulaması.

- **`--exclude-launch-settings`**

  Oluşturulan şablondan *Launchsettings. JSON* öğesini dışlar.

- **`--no-restore`**

  Proje oluşturma sırasında örtük geri yükleme yürütülmez.

- **`--no-https`**

  HTTPS 'yi kapatır. Bu seçenek yalnızca kimlik doğrulama `None`geçerlidir.

- **`-uld|--use-local-db`**

  SQLite yerine LocalDB kullanılması gerektiğini belirtir. Yalnızca `Individual` veya `IndividualB2C` kimlik doğrulaması için geçerlidir. .NET Core 3,0 SDK 'dan beri kullanılabilir.

- **`-f|--framework <FRAMEWORK>`**

  Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir. Seçenek .NET Core 2,2 SDK sürümünde kullanılamaz.

  Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:

  | SDK sürümü | Varsayılan değer   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.0` |

***

### <a name="reactredux"></a>açarken kilitlenmesi

- **`--exclude-launch-settings`**

  Oluşturulan şablondan *Launchsettings. JSON* öğesini dışlar.

- **`-f|--framework <FRAMEWORK>`**

  Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir. Seçenek .NET Core 2,2 SDK sürümünde kullanılamaz.

  Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:

  | SDK sürümü | Varsayılan değer   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.0` |

- **`--no-restore`**

  Proje oluşturma sırasında örtük geri yükleme yürütülmez.

- **`--no-https`**

  HTTPS 'yi kapatır.

***

### <a name="razorclasslib"></a>razorclasslib

- **`--no-restore`**

  Proje oluşturma sırasında örtük geri yükleme yürütülmez.

- **`-s|--support-pages-and-views`**

  , Bu kitaplığa bileşenlere ek olarak geleneksel Razor sayfaları ve görünümleri eklenmesini destekler. .NET Core 3,0 SDK 'dan beri kullanılabilir.

***
  
### <a name="webapi"></a>WebApi

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  Kullanılacak kimlik doğrulaması türü. Olası değerler şunlardır:

  - `None`-kimlik doğrulaması yok (varsayılan).
  - `IndividualB2C` bireysel kimlik doğrulama Azure AD B2C.
  - tek bir kiracı için `SingleOrg` kurumsal kimlik doğrulaması.
  - `Windows`-Windows kimlik doğrulaması.

- **`--aad-b2c-instance <INSTANCE>`**

  Bağlanılacak Azure Active Directory B2C örneği. `IndividualB2C` kimlik doğrulamasıyla kullanın. Varsayılan değer: `https://login.microsoftonline.com/tfp/`.

- **`-ssp|--susi-policy-id <ID>`**

  Bu proje için oturum açma ve kaydolma ilkesi KIMLIĞI. `IndividualB2C` kimlik doğrulamasıyla kullanın.

- **`--aad-instance <INSTANCE>`**

  Bağlanılacak Azure Active Directory örneği. `SingleOrg` kimlik doğrulamasıyla kullanın. Varsayılan değer: `https://login.microsoftonline.com/`.

- **`--client-id <ID>`**

  Bu projenin Istemci KIMLIĞI. `IndividualB2C` veya `SingleOrg` kimlik doğrulamasıyla kullanın. Varsayılan değer: `11111111-1111-1111-11111111111111111`.

- **`--domain <DOMAIN>`**

  Dizin kiracının etki alanı. `IndividualB2C` veya `SingleOrg` kimlik doğrulamasıyla kullanın. Varsayılan değer: `qualified.domain.name`.

- **`--tenant-id <ID>`**

  Bağlanılacak dizinin Tenantıd KIMLIĞI. `SingleOrg` kimlik doğrulamasıyla kullanın. Varsayılan değer: `22222222-2222-2222-2222-222222222222`.

- **`-r|--org-read-access`**

  Bu uygulamanın dizine okuma erişimini sağlar. Yalnızca `SingleOrg` kimlik doğrulaması için geçerlidir.

- **`--exclude-launch-settings`**

  Oluşturulan şablondan *Launchsettings. JSON* öğesini dışlar.

- **`--no-https`**

  HTTPS 'yi kapatır. `app.UseHsts` ve `app.UseHttpsRedirection` `Startup.Configure`eklenmez. Bu seçenek yalnızca `IndividualB2C` veya `SingleOrg` kimlik doğrulaması için kullanılmıyorsa geçerlidir.

- **`-uld|--use-local-db`**

  SQLite yerine LocalDB kullanılması gerektiğini belirtir. Yalnızca `IndividualB2C` kimlik doğrulaması için geçerlidir.

- **`-f|--framework <FRAMEWORK>`**

  Hedeflenecek [çerçeveyi](../../standard/frameworks.md) belirtir. Seçenek .NET Core 2,2 SDK sürümünde kullanılamaz.

  Aşağıdaki tabloda, kullanmakta olduğunuz SDK sürüm numarasına göre varsayılan değerler listelenmektedir:

  | SDK sürümü | Varsayılan değer   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.1` |

- **`--no-restore`**

  Proje oluşturma sırasında örtük geri yükleme yürütülmez.

***

### <a name="globaljson"></a>globaljson

- **`--sdk-version <VERSION_NUMBER>`**

  *Global. JSON* dosyasında kullanılacak .NET Core SDK sürümünü belirtir.

***

## <a name="examples"></a>Örnekler

- Şablon adını C# belirterek bir konsol uygulaması projesi oluşturun:

  ```dotnetcli
  dotnet new "Console Application"
  ```

- Geçerli dizinde F# bir konsol uygulaması projesi oluşturun:

  ```dotnetcli
  dotnet new console -lang F#
  ```

- Belirtilen dizinde bir .NET Standard sınıf kitaplığı projesi oluşturun:

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- Geçerli dizinde kimlik doğrulaması C# olmadan yeni bir ASP.NET Core MVC projesi oluşturun:

  ```dotnetcli
  dotnet new mvc -au None
  ```

- Yeni bir xUnit projesi oluştur:

  ```dotnetcli
  dotnet new xunit
  ```

- Tek sayfalı uygulama (SPA) şablonları için kullanılabilen tüm şablonları listeleyin:

  ```dotnetcli
  dotnet new spa -l
  ```

- *We* alt dizeniz ile eşleşen tüm şablonları listeleyin. Tam eşleşme bulunamadı, bu nedenle alt dize eşleştirmesi hem kısa ad hem de ad sütunlarında çalışır.

  ```dotnetcli
  dotnet new we -l
  ```

- Şablonla *eşleşen şablonu*çağırma girişimi. Tek bir eşleşme belirlenemiyorsa kısmi eşleşen şablonları listeleyin.

  ```dotnetcli
  dotnet new ng
  ```

- ASP.NET Core için SPA şablonlarının 2,0 sürümünü yükler:

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- Yüklü şablonları ve bunlarla ilgili ayrıntıları, bunları kaldırma dahil olmak üzere listeleyin:

  ```dotnetcli
  dotnet new -u
  ```

- SDK sürümünü 3.1.101 olarak ayarlamak için geçerli dizinde *Global. JSON* oluşturun:

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a>Ayrıca bkz.

- [DotNet New için özel şablonlar](custom-templates.md)
- [Dotnet new için özel şablon oluşturma](../tutorials/cli-templates-create-item-template.md)
- [DotNet/DotNet-şablon-örnek GitHub deposu](https://github.com/dotnet/dotnet-template-samples)
- [DotNet New için kullanılabilir şablonlar](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
