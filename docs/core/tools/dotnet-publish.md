---
title: dotnet yayımlama komutu
description: Dotnet yayımlama komutu bir .NET Core projesi veya çözüm bir dizine yayımlar.
ms.date: 02/24/2020
ms.openlocfilehash: 7e57a7b3cfe72653cc64c90055735795e4616260
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523764"
---
# <a name="dotnet-publish"></a>dotnet publish

**Bu makale şu şekilde dir:** ✔️ .NET Core 2.1 SDK ve sonraki sürümler

## <a name="name"></a>Adı

`dotnet publish`- Uygulama ve bağımlılıklarını barındırma sistemine dağıtım için bir klasöre yayımlar.

## <a name="synopsis"></a>Özet

```dotnetcli
dotnet publish [<PROJECT>|<SOLUTION>] [-c|--configuration]
    [-f|--framework] [--force] [--interactive] [--manifest]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo]
    [-o|--output] [-r|--runtime] [--self-contained]
    [--no-self-contained] [-v|--verbosity] [--version-suffix]

dotnet publish [-h|--help]
```

## <a name="description"></a>Açıklama

`dotnet publish`uygulamayı derler, proje dosyasında belirtilen bağımlılıkları okur ve ortaya çıkan dosya kümesini bir dizine yayınlar. Çıktı aşağıdaki varlıkları içerir:

- *Dll* uzantılı bir derlemede Ara Dil (IL) kodu.
- Projenin tüm bağımlılıklarını içeren bir *.deps.json* dosyası.
- Uygulamanın beklediği paylaşılan çalışma süresini ve çalışma zamanı için diğer yapılandırma seçeneklerini (örneğin, çöp toplama türü) belirten bir *.runtimeconfig.json* dosyası.
- NuGet önbelleğinden çıktı klasörüne kopyalanan uygulamabağımlılıkları.

Komutun `dotnet publish` çıktısı yürütme için bir barındırma sistemine (örneğin, bir sunucu, PC, Mac, dizüstü bilgisayar) dağıtım için hazırdır. Uygulamayı dağıtıma hazırlamak için resmi olarak desteklenen tek yol bu. Projenin belirttiği dağıtım türüne bağlı olarak, barındırma sistemi .NET Core paylaşılan çalışma zamanı yüklü olabilir veya olmayabilir.

## <a name="arguments"></a>Bağımsız Değişkenler

- **`PROJECT|SOLUTION`**

  Yayımlanmak için proje veya çözüm.
  
  * `PROJECT`[C#](csproj.md), F#veya Visual Basic proje dosyasının yolu ve dosya adı veya C#, F#veya Visual Basic proje dosyası içeren bir dizine giden yoldur. Dizin belirtilmemişse, geçerli dizine varsayılan olarak.

  * `SOLUTION`çözüm dosyasının *(.sln* uzantısı) veya çözüm dosyası içeren bir dizine giden yol ve dosya adıdır. Dizin belirtilmemişse, geçerli dizine varsayılan olarak. .NET Core 3.0 SDK'dan beri mevcuttur.

## <a name="options"></a>Seçenekler

- **`-c|--configuration <CONFIGURATION>`**

  Yapı yapılandırmasını tanımlar. Çoğu proje için `Debug`varsayılan değer, ancak projenizdeki yapı yapılandırma ayarlarını geçersiz kılabilirsiniz.

- **`-f|--framework <FRAMEWORK>`**

  Belirtilen [hedef çerçeve](../../standard/frameworks.md)için uygulama yayımlar. Proje dosyasındaki hedef çerçeveyi belirtmeniz gerekir.

- **`--force`**

  Son geri yükleme başarılı olsa bile tüm bağımlılıkları çözüme kavuşturmaya zorlar. Bu bayrağı *belirtmek, project.assets.json* dosyasını silmekle aynıdır.

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`--interactive`**

  Komutun durmasını ve kullanıcı girişi veya eylemini beklemesini sağlar. Örneğin, kimlik doğrulamasını tamamlamak için. .NET Core 3.0 SDK'dan beri mevcuttur.

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  Uygulamayla birlikte yayınlanan paket kümesini kırpmak için kullanılacak bir veya birkaç [hedef bildirimi](../deploying/runtime-store.md) belirtir. Bildirim dosyası [ `dotnet store` komutun](dotnet-store.md)çıktısının bir parçasıdır. Birden çok bildirim belirtmek `--manifest` için, her bildirim için bir seçenek ekleyin.

- **`--no-build`**

  Yayımlamadan önce projeyi oluşturmaz. Ayrıca bayrağı da `--no-restore` örtülü olarak ayarlar.

- **`--no-dependencies`**

  Projeden projeye başvuruları yoksa ve yalnızca kök projeyi geri yükler.

- **`--nologo`**

  Başlangıç bayrağını veya telif hakkı iletisini görüntülemez. .NET Core 3.0 SDK'dan beri mevcuttur.

- **`--no-restore`**

  Komutu çalıştırırken örtük bir geri yükleme yürütmez.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Çıktı dizininin yolunu belirtir.
  
  Belirtilmemişse, çalışma süresine bağlı yürütülebilir ve platform lar arası ikili ler için *[project_file_folder]./bin/[configuration]/[framework]/publish/* olarak varsayılan olarak geçer. Kendi kendine yeten bir yürütülebilir için *[project_file_folder]/bin/[configuration]/[framework]/[runtime]/publish/* olarak varsayılan olarak

  - .NET Core 3.x SDK ve sonrası
  
    Proje yayımlanırken göreceli bir yol belirtilirse, oluşturulan çıktı dizini proje dosyası konumuna değil, geçerli çalışma dizinine göredir.

    Çözüm yayımlanırken göreceli bir yol belirtilirse, tüm projelerin tüm çıktıları geçerli çalışma dizinine göre belirtilen klasöre gider. Yayımlama çıktısının her proje için ayrı klasörlere gitmesini sağlamak için, seçenek yerine msbuild `PublishDir` özelliğini kullanarak göreli bir yol belirtin. `--output` Örneğin, `dotnet publish -p:PublishDir=.\publish` her proje için yayımçıktısını proje dosyasını içeren klasörün altındaki klasöre `publish` gönderir.

  - .NET Çekirdek 2.x SDK
  
    Proje yayımlanırken göreceli bir yol belirtilirse, oluşturulan çıktı dizini geçerli çalışma dizinine değil, proje dosyası konumuna göredir.

    Çözüm yayımlanırken göreli bir yol belirtilirse, her projenin çıktısı proje dosyası konumuna göre ayrı bir klasöre gider. Bir çözüm yayımlanırken mutlak bir yol belirtilirse, tüm projeler için çıktı yayımlamak belirtilen klasöre gider.

- **`--self-contained [true|false]`**

  .NET Core çalışma zamanını uygulamanızla birlikte yayınlar, böylece çalışma süresinin hedef makineye yüklenmesi gerekmez. Varsayılan, `true` çalışma zamanı tanımlayıcısı belirtilmişse. Daha fazla bilgi için [.NET Core uygulama yayımlama](../deploying/index.md) ve [.NET Core CLI ile .NET Core uygulamaları yayımlama](../deploying/deploy-with-cli.md)'ya bakın.

- **`--no-self-contained`**

  `--self-contained false`Eşdeğeri . .NET Core 3.0 SDK'dan beri mevcuttur.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Belirli bir çalışma zamanı için uygulamayı yayımlar. Runtime Tanımlayıcıları (RID'ler) listesi için RID [kataloğuna](../rid-catalog.md)bakın. Daha fazla bilgi için [.NET Core uygulama yayımlama](../deploying/index.md) ve [.NET Core CLI ile .NET Core uygulamaları yayımlama](../deploying/deploy-with-cli.md)'ya bakın.

- **`-v|--verbosity <LEVEL>`**

  Komutun ayrıntılı düzeyini ayarlar. İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve . Varsayılan değer. `minimal`

- **`--version-suffix <VERSION_SUFFIX>`**

  Proje dosyasının sürüm alanında yıldız işaretini`*`( ) değiştirmek için sürüm soneki tanımlar.

## <a name="examples"></a>Örnekler

- Geçerli dizinde proje için [çalışma süresine bağımlı çapraz platform ikilisi](../deploying/index.md#produce-a-cross-platform-binary) oluşturun:

  ```dotnetcli
  dotnet publish
  ```

  .NET Core 3.0 SDK ile başlayarak, bu örnek aynı zamanda geçerli platform için [çalıştırılabilir bir çalışma zamanı bağımlı](../deploying/index.md#publish-runtime-dependent) oluşturur.

- Belirli bir çalışma süresi için geçerli dizindeki proje için bağımsız bir [yürütülebilir](../deploying/index.md#publish-self-contained) oluşturun:

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  RID proje dosyasında olmalıdır.

- Belirli bir platform için geçerli dizindeki proje için [çalışma süresine bağlı yürütülebilir bir çalıştırılmaz](../deploying/index.md#publish-runtime-dependent) oluşturun:

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  RID proje dosyasında olmalıdır. Bu örnek .NET Core 3.0 SDK ve sonraki sürümler için geçerlidir.

- Belirli bir çalışma zamanı ve hedef çerçeve için projeyi geçerli dizinde yayımlayın:

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- Belirtilen proje dosyasını yayımlayın:

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- Geçerli uygulamayı yayımlayın, ancak projeden projeye (P2P) başvurularını, yalnızca geri yükleme işlemi sırasındaki kök projeyi geri yüklemeyin:

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core uygulama yayıncılığı genel bakış](../deploying/index.md)
- [.NET Core CLI ile .NET Core uygulamalarını yayımla](../deploying/deploy-with-cli.md)
- [Hedef çerçeveler](../../standard/frameworks.md)
- [Çalışma Zamanı Tanımlayıcı (RID) kataloğu](../rid-catalog.md)
- [macOS Catalina Noterizasyonu ile çalışma](../install/macos-notarization-issues.md)
- [Yayınlanan bir uygulamanın dizin yapısı](/aspnet/core/hosting/directory-structure)
