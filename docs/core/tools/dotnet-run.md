---
title: dotnet çalıştır komutu
description: Dotnet çalıştır komutu, uygulamanızı kaynak kodundan çalıştırmak için kullanışlı bir seçenek sağlar.
ms.date: 02/19/2020
ms.openlocfilehash: e442ed56d676ffd189ef6d394d840cea671c2dc6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157082"
---
# <a name="dotnet-run"></a>dotnet run

**Bu makale şu şekilde dir:** ✔️ .NET Core 2.x SDK ve sonraki sürümler

## <a name="name"></a>Adı

`dotnet run`- Kaynak kodunu açık bir derleme veya başlatma komutları olmadan çalıştırın.

## <a name="synopsis"></a>Özet

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--interactive] [--launch-profile]
    [--no-build] [--no-dependencies] [--no-launch-profile] [--no-restore] [-p|--project]
    [-r|--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```

## <a name="description"></a>Açıklama

Komut, `dotnet run` uygulamanızı kaynak koddan tek bir komutla çalıştırmak için kullanışlı bir seçenek sağlar. Komut satırından hızlı yinelemeli geliştirme için yararlıdır. Komut, kodu oluşturmak [`dotnet build`](dotnet-build.md) için komuta bağlıdır. Yapı için, projenin önce geri yükedilmesi gibi tüm gereksinimler `dotnet run` de geçerlidir.

Çıktı dosyaları varsayılan konuma yazılır, `bin/<configuration>/<target>`yani. Örneğin bir `netcoreapp2.1` uygulamanız varsa ve `dotnet run`çalıştırın, çıktı `bin/Debug/netcoreapp2.1`. Dosyalar gerektiği gibi üzerine yazılır. Geçici dosyalar dizine `obj` yerleştirilir.

Proje birden çok çerçeve belirtirse, `dotnet run` çerçeveyi belirtmek `-f|--framework <FRAMEWORK>` için seçenek kullanılmadığı sürece bir hatayla sonuçlanır.

Komut, `dotnet run` derlemeler değil, projeler bağlamında kullanılır. Bunun yerine çerçeveye bağımlı bir uygulama olan DLL'yi çalıştırmaya çalışıyorsanız, komut olmadan [dotnet](dotnet.md) kullanmanız gerekir. Örneğin, çalıştırmak `myapp.dll`için, kullanmak:

```dotnetcli
dotnet myapp.dll
```

Sürücü hakkında daha `dotnet` fazla bilgi için [.NET Core Komut Satırı Araçları (CLI)](index.md) konusuna bakın.

Uygulamayı çalıştırmak için `dotnet run` komut, NuGet önbelleğinden paylaşılan çalışma süresinin dışında olan uygulamanın bağımlılıklarını giderir. Önbelleğe alınmış bağımlılıklar kullandığından, üretimdeki `dotnet run` uygulamaları çalıştırmak için kullanılması önerilmez. Bunun [create a deployment](../deploying/index.md) yerine, komutu [`dotnet publish`](dotnet-publish.md) kullanarak bir dağıtım oluşturun ve yayımlanmış çıktıyı dağıtın.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a>Seçenekler

- **`--`**

  Çalıştırılmakta `dotnet run` olan uygulama için bağımsız değişkenleri sınırlandırın. Bu delimiter sonra tüm bağımsız değişkenler uygulama çalışmasına geçirilir.

- **`-c|--configuration <CONFIGURATION>`**

  Yapı yapılandırmasını tanımlar. Çoğu proje için `Debug`varsayılan değer, ancak projenizdeki yapı yapılandırma ayarlarını geçersiz kılabilirsiniz.

- **`-f|--framework <FRAMEWORK>`**

  Belirtilen [çerçeveyi](../../standard/frameworks.md)kullanarak uygulamayı oluşturur ve çalıştırın. Çerçeve proje dosyasında belirtilmelidir.

- **`--force`**

  Son geri yükleme başarılı olsa bile tüm bağımlılıkları çözüme kavuşturmaya zorlar. Bu bayrağı *belirtmek, project.assets.json* dosyasını silmekle aynıdır.

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`--interactive`**

  Komutun durmasına ve kullanıcı girişinin veya eylemini beklemesine (örneğin, kimlik doğrulamasını tamamlamak için) izin verir. .NET Core 3.0 SDK'dan beri mevcuttur.

- **`--launch-profile <NAME>`**

  Uygulamayı başlatırken kullanılacak başlatma profilinin adı (varsa). Başlatma profilleri *launchSettings.json* dosyasında tanımlanır ve genellikle `Development` `Staging`, `Production`, ve . Daha fazla bilgi için bkz: [Birden çok ortamla çalışma.](/aspnet/core/fundamentals/environments)

- **`--no-build`**

  Çalıştırmadan önce projeyi oluşturmaz. Ayrıca örtük `--no-restore` bayrağı ayarlar.

- **`--no-dependencies`**

  Projeden projeye (P2P) başvurularla projeyi geri yüklediğinizde, başvuruları değil, kök projeyi geri yükler.

- **`--no-launch-profile`**

  Uygulamayı yapılandırmak için *launchSettings.json* kullanmaya çalışmaz.

- **`--no-restore`**

  Komutu çalıştırırken örtük bir geri yükleme yürütmez.

- **`-p|--project <PATH>`**

  Proje dosyasının çalışma yolunu (klasör adı veya tam yol) belirtir. Belirtilmemişse, varsayılan olarak geçerli dizine göre olur.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Paketleri geri yüklemek için hedef çalışma süresini belirtir. Runtime Tanımlayıcıları (RID'ler) listesi için RID [kataloğuna](../rid-catalog.md)bakın. `-r`.NET Core 3.0 SDK'dan beri kısa seçenek mevcuttur.

- **`-v|--verbosity <LEVEL>`**

  Komutun ayrıntılı düzeyini ayarlar. İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve . Varsayılan değer: `m`. .NET Core 2.1 SDK'dan beri mevcuttur.

## <a name="examples"></a>Örnekler

- Projeyi geçerli dizinde çalıştırın:

  ```dotnetcli
  dotnet run
  ```

- Belirtilen projeyi çalıştırın:

  ```dotnetcli
  dotnet run --project ./projects/proj1/proj1.csproj
  ```

- Projeyi geçerli dizinde çalıştırın `--help` (boş `--` seçenek kullanıldığından, bu örnekteki bağımsız değişken uygulamaya geçirilir):

  ```dotnetcli
  dotnet run --configuration Release -- --help
  ```

- Geçerli dizinde proje için bağımlılıkları ve araçları yalnızca en az çıktıyı gösteren geri yüklenir ve projeyi çalıştırın: (.NET Core SDK 2.0 ve sonraki sürümler):

  ```dotnetcli
  dotnet run --verbosity m
  ```
