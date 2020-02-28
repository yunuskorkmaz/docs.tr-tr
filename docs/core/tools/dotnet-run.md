---
title: DotNet Run komutu
description: DotNet Run komutu, uygulamanızı kaynak koddan çalıştırmak için uygun bir seçenek sağlar.
ms.date: 02/19/2020
ms.openlocfilehash: e442ed56d676ffd189ef6d394d840cea671c2dc6
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157082"
---
# <a name="dotnet-run"></a>dotnet run

**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2. x SDK ve sonraki sürümleri

## <a name="name"></a>Adı

`dotnet run`-herhangi bir açık derleme veya başlatma komutu olmadan kaynak kodu çalıştırır.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--interactive] [--launch-profile]
    [--no-build] [--no-dependencies] [--no-launch-profile] [--no-restore] [-p|--project]
    [-r|--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```

## <a name="description"></a>Açıklama

`dotnet run` komutu, uygulamanızı kaynak koddan tek bir komutla çalıştırmak için uygun bir seçenek sağlar. Komut satırından hızlı yinelemeli geliştirme için faydalıdır. Komut, kodu derlemek için [`dotnet build`](dotnet-build.md) komutuna bağımlıdır. Projenin önce geri yüklenmesi gerektiği gibi, derleme için tüm gereksinimler, `dotnet run` için de geçerlidir.

Çıktı dosyaları varsayılan konuma yazılır, bu `bin/<configuration>/<target>`. Örneğin, bir `netcoreapp2.1` uygulamanız varsa ve `dotnet run`çalıştırırsanız, çıktı `bin/Debug/netcoreapp2.1`yerleştirilir. Dosyalar gerektiği gibi üzerine yazılır. Geçici dosyalar `obj` dizinine yerleştirilir.

Proje birden çok çerçeve belirtiyorsa, Framework 'ü belirtmek için `-f|--framework <FRAMEWORK>` seçeneği kullanılmadığı müddetçe `dotnet run` yürütülerek hata oluşur.

`dotnet run` komutu, oluşturulan derlemeler değil, proje bağlamında kullanılır. Bunun yerine Framework 'e bağımlı bir uygulama DLL 'sini çalıştırmaya çalışıyorsanız, bir komut olmadan [DotNet](dotnet.md) kullanmanız gerekir. Örneğin, `myapp.dll`çalıştırmak için şunu kullanın:

```dotnetcli
dotnet myapp.dll
```

`dotnet` sürücüsü hakkında daha fazla bilgi için bkz. [.NET Core komut satırı araçları (CLI)](index.md) konusu.

Uygulamayı çalıştırmak için `dotnet run` komutu, paylaşılan çalışma zamanının dışındaki uygulamanın tüm bağımlılıklarını NuGet önbelleğinden çözer. Önbelleğe alınmış bağımlılıkları kullandığından, üretimde uygulamaları çalıştırmak için `dotnet run` kullanılması önerilmez. Bunun yerine, [`dotnet publish`](dotnet-publish.md) komutunu kullanarak [bir dağıtım oluşturun](../deploying/index.md) ve yayımlanan çıktıyı dağıtın.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a>Seçenekler

- **`--`**

  Çalıştırılmakta olan uygulamanın bağımsız değişkenlerinden `dotnet run` için bağımsız değişkenleri ayırır. Bu sınırlayıcıdan sonraki tüm bağımsız değişkenler uygulama çalıştırmasına geçirilir.

- **`-c|--configuration <CONFIGURATION>`**

  Yapı yapılandırmasını tanımlar. Çoğu proje için varsayılan değer `Debug`, ancak projenizde derleme yapılandırma ayarlarını geçersiz kılabilirsiniz.

- **`-f|--framework <FRAMEWORK>`**

  Belirtilen [Framework 'ü](../../standard/frameworks.md)kullanarak uygulamayı oluşturur ve çalıştırır. Çerçeve proje dosyasında belirtilmelidir.

- **`--force`**

  Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar. Bu bayrağın belirtilmesi, *Project. varlıklar. JSON* dosyasını silme ile aynıdır.

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`--interactive`**

  Komutun, Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir (örneğin, kimlik doğrulamasını tamamlamaya yönelik). .NET Core 3,0 SDK 'dan beri kullanılabilir.

- **`--launch-profile <NAME>`**

  Uygulamayı başlatırken kullanılacak başlatma profilinin adı (varsa). Başlatma profilleri, *Launchsettings. JSON* dosyasında tanımlanır ve genellikle `Development`, `Staging`ve `Production`olarak adlandırılır. Daha fazla bilgi için bkz. [birden çok ortamla çalışma](/aspnet/core/fundamentals/environments).

- **`--no-build`**

  Çalıştırmadan önce projeyi oluşturmaz. Ayrıca `--no-restore` bayrağını örtülü olarak ayarlar.

- **`--no-dependencies`**

  Projeden projeye (P2P) başvuruları olan bir projeyi geri yüklerken, başvuruları değil kök projeyi geri yükler.

- **`--no-launch-profile`**

  Uygulamayı yapılandırmak için *Launchsettings. JSON* kullanmaya çalışmayın.

- **`--no-restore`**

  Komutu çalıştırılırken örtük geri yükleme yürütülmez.

- **`-p|--project <PATH>`**

  Çalıştırılacak proje dosyasının yolunu belirtir (klasör adı veya tam yol). Belirtilmezse, varsayılan olarak geçerli dizini alır.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Paketlerinin geri yükleneceği hedef çalışma zamanını belirtir. Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md). `-r` Short seçeneği .NET Core 3,0 SDK 'dan beri kullanılabilir.

- **`-v|--verbosity <LEVEL>`**

  Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`. Varsayılan değer: `m`. .NET Core 2,1 SDK 'dan beri kullanılabilir.

## <a name="examples"></a>Örnekler

- Projeyi geçerli dizinde Çalıştır:

  ```dotnetcli
  dotnet run
  ```

- Belirtilen projeyi Çalıştır:

  ```dotnetcli
  dotnet run --project ./projects/proj1/proj1.csproj
  ```

- Projeyi geçerli dizinde çalıştırın (boş `--` seçeneği kullanıldığından bu örnekteki `--help` bağımsız değişkeni uygulamaya geçirilir):

  ```dotnetcli
  dotnet run --configuration Release -- --help
  ```

- Geçerli dizindeki proje için bağımlılıkları ve araçları geri yükleme yalnızca minimum çıktıyı gösterir ve ardından projeyi (.NET Core SDK 2,0 ve sonraki sürümleri) çalıştırır:

  ```dotnetcli
  dotnet run --verbosity m
  ```
