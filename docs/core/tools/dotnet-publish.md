---
title: dotnet publish komutu
description: Dotnet publish komutu bir dizine .NET Core projesi veya çözümü yayımlar.
ms.date: 02/24/2020
ms.openlocfilehash: cf41ee09244faad03feb8ccda19135b8c7780106
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157006"
---
# <a name="dotnet-publish"></a>dotnet publish

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri

## <a name="name"></a>Adı

`dotnet publish`-uygulamayı ve bağımlılıklarını barındırma sistemine dağıtım için bir klasöre yayımlar.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet publish [<PROJECT>|<SOLUTION>] [-c|--configuration] 
    [-f|--framework] [--force] [--interactive] [--manifest]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo]
    [-o|--output] [-r|--runtime] [--self-contained]
    [--no-self-contained] [-v|--verbosity] [--version-suffix]

dotnet publish [-h|--help]
```

## <a name="description"></a>Açıklama

`dotnet publish` uygulamayı derler, proje dosyasında belirtilen bağımlılıklarını okur ve elde edilen dosya kümesini bir dizine yayınlar. Çıktı aşağıdaki varlıkları içerir:

- *DLL* uzantılı bir derlemede ara DIL (IL) kodu.
- Projenin tüm bağımlılıklarını içeren bir *. Deps. JSON* dosyası.
- Uygulamanın beklediği paylaşılan çalışma zamanını belirten *. runtimeconfig. JSON* dosyası ve çalışma zamanına yönelik diğer yapılandırma seçenekleri (örneğin, çöp toplama türü).
- NuGet önbelleğinden çıkış klasörüne kopyalanmış olan uygulamanın bağımlılıkları.

`dotnet publish` komutun çıktısı, yürütme için bir barındırma sistemine (örneğin, bir sunucu, PC, Mac, dizüstü bilgisayar) dağıtıma yöneliktir. Uygulamayı dağıtıma hazırlamak için tek resmi olarak desteklenen bir yoldur. Projenin belirttiği dağıtımın türüne bağlı olarak, barındırma sisteminde .NET Core paylaşılan çalışma zamanı yüklü olabilir veya olmayabilir.

## <a name="arguments"></a>Bağımsız Değişkenler

- **`PROJECT|SOLUTION`**

  Yayımlanacak proje veya çözüm.
  
  * `PROJECT`, veya Visual Basic proje dosyasının yolu ve [C#](csproj.md)dosya F#adıdır ya da C#, F#veya Visual Basic proje dosyası içeren bir dizinin yoludur. Dizin belirtilmemişse, varsayılan olarak geçerli dizine ayarlanır.

  * `SOLUTION`, bir çözüm dosyasının ( *. sln* uzantısının) yolu ve dosya adıdır veya çözüm dosyası içeren bir dizinin yoludur. Dizin belirtilmemişse, varsayılan olarak geçerli dizine ayarlanır. **.NET Core 3,0 SDK ile başlayarak kullanılabilir.** 

## <a name="options"></a>Seçenekler

- **`-c|--configuration <CONFIGURATION>`**

  Yapı yapılandırmasını tanımlar. Çoğu proje için varsayılan değer `Debug`, ancak projenizde derleme yapılandırma ayarlarını geçersiz kılabilirsiniz.

- **`-f|--framework <FRAMEWORK>`**

  Belirtilen [hedef çerçeve](../../standard/frameworks.md)için uygulamayı yayımlar. Hedef çerçeveyi proje dosyasında belirtmeniz gerekir.

- **`--force`**

  Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar. Bu bayrağın belirtilmesi, *Project. varlıklar. JSON* dosyasını silme ile aynıdır.

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`--interactive`** **.NET Core 3,0 SDK ile başlayarak kullanılabilir.**

  Komutun Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir. Örneğin, kimlik doğrulamasını tamamlamaya yönelik. 

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  Uygulamayla yayımlanmış paket kümesini kırpmak için kullanılacak bir veya birkaç [hedef bildirimi](../deploying/runtime-store.md) belirtir. Bildirim dosyası [`dotnet store` komutunun](dotnet-store.md)çıktısının bir parçasıdır. Birden çok bildirim belirtmek için her bildirim için bir `--manifest` seçeneği ekleyin.

- **`--no-build`**

  Yayımlamadan önce projeyi oluşturmaz. Ayrıca `--no-restore` bayrağını örtülü olarak ayarlar.

- **`--no-dependencies`**

  Projeden projeye başvuruları yoksayar ve yalnızca kök projeyi geri yükler.

- **`--nologo`** **.NET Core 3,0 SDK ile başlayarak kullanılabilir.**

  Başlangıç başlığını veya telif hakkı iletisini görüntülemez. 

- **`--no-restore`**

  Komutu çalıştırılırken örtük geri yükleme yürütülmez.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Çıkış dizini için yolu belirtir. Belirtilmemişse, çalışma zamanına bağlı bir yürütülebilir dosya ve platformlar arası ikili dosyalar için *./bin/[Configuration]/[Framework]/Publish/* varsayılan değeri. Otomatik olarak içerilen bir yürütülebilir dosya için *./bin/[Configuration]/[Framework]/[Runtime]/Publish/* varsayılan olarak.

  Yol göreli ise, oluşturulan çıkış dizini geçerli çalışma dizinine değil, proje dosyası konumuna göre belirlenir.

- **`--self-contained [true|false]`**

  .NET Core çalışma zamanını uygulamanızla yayımlar, böylece çalışma zamanının hedef makinede yüklü olması gerekmez. Bir çalışma zamanı tanımlayıcısı belirtilmişse varsayılan `true`. Daha fazla bilgi için bkz. [.NET Core uygulaması yayımlama](../deploying/index.md) ve [.NET Core CLI .NET Core uygulamaları](../deploying/deploy-with-cli.md)yayımlama.

- **`--no-self-contained`** **.NET Core 3,0 SDK ile başlayarak kullanılabilir.**

  `--self-contained false`eşdeğerdir.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Uygulamayı belirli bir çalışma zamanı için yayımlar. Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md). Daha fazla bilgi için bkz. [.NET Core uygulaması yayımlama](../deploying/index.md) ve [.NET Core CLI .NET Core uygulamaları](../deploying/deploy-with-cli.md)yayımlama.

- **`-v|--verbosity <LEVEL>`**

  Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.

- **`--version-suffix <VERSION_SUFFIX>`**

  Proje dosyasının sürüm alanındaki yıldız işaretini (`*`) değiştirecek sürüm sonekini tanımlar.

## <a name="examples"></a>Örnekler

- Geçerli dizindeki proje için [çalışma zamanına bağımlı platformlar arası ikili](../deploying/index.md#produce-a-cross-platform-binary) oluşturun:

  ```dotnetcli
  dotnet publish
  ```

  .NET Core 3,0 SDK ile başlayarak bu örnek ayrıca geçerli platform için [çalışma zamanına bağlı bir yürütülebilir dosya](../deploying/index.md#publish-runtime-dependent) oluşturur.

- Belirli bir çalışma zamanı için geçerli dizindeki proje için [kendi kendine içerilen bir yürütülebilir dosya](../deploying/index.md#publish-self-contained) oluşturun:

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  RID proje dosyasında olmalıdır.

- Belirli bir platform için geçerli dizindeki proje için [çalışma zamanına bağımlı bir yürütülebilir dosya](../deploying/index.md#publish-runtime-dependent) oluşturun:

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  RID proje dosyasında olmalıdır. Bu örnek .NET Core 3,0 SDK ve sonraki sürümleri için geçerlidir.

- Projeyi, belirli bir çalışma zamanı ve hedef çerçeve için geçerli dizinde yayımlayın:

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- Belirtilen proje dosyasını Yayımla:

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- Geçerli uygulamayı yayımlayın ancak projeden projeye (P2P) başvurularını geri yüklemeyin, ancak geri yükleme işlemi sırasında yalnızca kök proje:

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core uygulama yayımlamaya genel bakış](../deploying/index.md)
- [.NET Core CLI .NET Core uygulamaları yayımlayın](../deploying/deploy-with-cli.md)
- [Hedef çerçeveler](../../standard/frameworks.md)
- [Çalışma zamanı tanımlayıcı (RID) kataloğu](../rid-catalog.md)
- [MacOS Catalina notarle çalışma](../install/macos-notarization-issues.md) Daha fazla bilgi için aşağıdaki kaynaklara bakın:
- [Yayımlanan bir uygulamanın dizin yapısı](/aspnet/core/hosting/directory-structure)
