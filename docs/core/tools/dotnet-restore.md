---
title: dotnet geri yükleme komutu
description: Dotnet geri yükleme komutuyla bağımlılıkları ve projeye özgü araçları nasıl geri yükleyebileceğinizi öğrenin.
ms.date: 02/27/2020
ms.openlocfilehash: 3b336e1aa097f83280de6faeef51793345520530
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389655"
---
# <a name="dotnet-restore"></a>dotnet restore

**Bu makale şu şekilde dir:** ✔️ .NET Core 2.1 SDK ve sonraki sürümler

## <a name="name"></a>Adı

`dotnet restore`- Projenin bağımlılıklarını ve araçlarını geri yükler.

## <a name="synopsis"></a>Özet

```dotnetcli
dotnet restore [<ROOT>] [--configfile] [--disable-parallel]
    [-f|--force] [--force-evaluate] [--ignore-failed-sources]
    [--interactive] [--lock-file-path] [--locked-mode]
    [--no-cache] [--no-dependencies] [--packages] [-r|--runtime]
    [-s|--source] [--use-lockfile] [-v|--verbosity]

dotnet restore [-h|--help]
```

## <a name="description"></a>Açıklama

Komut, `dotnet restore` proje dosyasında belirtilen projeye özgü araçların yanı sıra bağımlılıkları geri yüklemek için NuGet'i kullanır. Varsayılan olarak, bağımlılıkların ve araçların geri yükleme paralel olarak yürütülür.

Bağımlılıkları geri yüklemek için NuGet'in paketlerin bulunduğu akışlara ihtiyacı vardır. Özet akışları genellikle *nuget.config* yapılandırma dosyası üzerinden sağlanır. .NET Core SDK yüklendiğinde varsayılan yapılandırma dosyası sağlanır. Proje dizininde kendi *nuget.config* dosyanızı oluşturarak ek akışlar belirtirsiniz. *Nuget.config* beslemelerini - `-s` seçeneği ile geçersiz kılabilirsiniz.

Bağımlılıklar için, bağımsız değişkeni kullanarak geri yükleme işlemi `--packages` sırasında geri yüklenen paketlerin nereye yerleştirildiğini belirtirsiniz. Belirtilmemişse, varsayılan NuGet paket önbelleği kullanılır `.nuget/packages` ve bu da tüm işletim sistemlerinde kullanıcının ev dizininde bulunan dizinde bulunur. Örneğin, *Linux'ta /home/user1* veya Windows'da *C:\Users\user1.*

Projeye özgü takımlama `dotnet restore` için, önce aracın paketlendiği paketi geri yükler, sonra da proje dosyasında belirtildiği şekilde aracın bağımlılıklarını geri yüklemeye devam eder.

### <a name="nugetconfig-differences"></a>nuget.config farklar

`dotnet restore` Komutun davranışı *nuget.config* dosyasındaki ayarlardan etkilenir, varsa. Örneğin, `globalPackagesFolder` *nuget.config'de* ayarla, geri yüklenen NuGet paketlerini belirtilen klasöre yerleştirir. Bu, komuttaki `--packages` seçeneği belirtmeye `dotnet restore` alternatiftir. Daha fazla bilgi için [nuget.config referansına](/nuget/schema/nuget-config-file)bakın.

Yoksayan `dotnet restore` üç özel ayar vardır:

- [bindingYönlendirmeler](/nuget/schema/nuget-config-file#bindingredirects-section)

  Bağlama yönlendirmeleri öğelerle `<PackageReference>` çalışmaz ve .NET `<PackageReference>` Core yalnızca NuGet paketleri için öğeleri destekler.

- [Çözüm](/nuget/schema/nuget-config-file#solution-section)

  Bu ayar Visual Studio'ya özgüdür ve .NET Core için geçerli değildir. .NET Core bir `packages.config` dosya kullanmaz `<PackageReference>` ve bunun yerine NuGet paketleri için öğeleri kullanır.

- [güvenilir Signers](/nuget/schema/nuget-config-file#trustedsigners-section)

  NuGet henüz güvenilir paketlerin [platformlar arası doğrulanmasını desteklemediği](https://github.com/NuGet/Home/issues/7939) için bu ayar geçerli değildir.

## <a name="implicit-restore"></a>Örtük geri yükleme

Aşağıdaki `dotnet restore` komutları çalıştırdığınızda gerekirse komut örtülü olarak çalıştırılır:

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

Çoğu durumda, komutu `dotnet restore` açıkça kullanmanız gerekmez.

Bazen, dolaylı olarak çalıştırmak `dotnet restore` rahatsız edici olabilir. Örneğin, yapı sistemleri gibi bazı otomatik sistemlerin, `dotnet restore` ağ kullanımını denetleyebilmeleri için geri yüklemenin ne zaman gerçekleşebileceğini denetlemek için açıkça aramaları gerekir. Örtülü `dotnet restore` olarak çalışmasını önlemek için, `--no-restore` örtük geri yüklemeyi devre dışı bırakmada bu komutlardan herhangi biriyle bayrağı kullanabilirsiniz.

## <a name="arguments"></a>Bağımsız Değişkenler

- **`ROOT`**

  Geri yükleme için proje dosyasına isteğe bağlı yol.

## <a name="options"></a>Seçenekler

- **`--configfile <FILE>`**

  NuGet yapılandırma dosyası (*nuget.config*) geri yükleme işlemi için kullanılacak.

- **`--disable-parallel`**

  Birden çok projeyi paralel olarak geri devre dışı kılabilir.

- **`--force`**

  Son geri yükleme başarılı olsa bile tüm bağımlılıkları çözüme kavuşturmaya zorlar. Bu bayrağı *belirtmek, project.assets.json* dosyasını silmekle aynıdır.

- **`--force-evaluate`**

  Bir kilit dosyası zaten olsa bile tüm bağımlılıkları yeniden değerlendirmek için geri yükleme zorlar.

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`--ignore-failed-sources`**

  Yalnızca sürüm gereksinimini karşılayan paketler varsa, başarısız kaynaklar hakkında uyarıda bulunabilir.

- **`--interactive`**

  Komutun durmasına ve kullanıcı girişinin veya eylemini beklemesine izin verir (örneğin kimlik doğrulamasını tamamlamak için). .NET Core 2.1.400'den beri.

- **`--lock-file-path <LOCK_FILE_PATH>`**

  Proje kilidi dosyasının yazıldığı çıktı konumu. Varsayılan olarak, bu *PROJECT_ROOT\packages.lock.json*olduğunu.

- **`--locked-mode`**

  Proje kilidi dosyasının güncelleştirilmesine izin verme.

- **`--no-cache`**

  Önbellek paketleri ve HTTP isteklerini belirtim.

- **`--no-dependencies`**

  Projeden projeye (P2P) başvurularla projeyi geri yüklediğinizde, başvuruları değil, kök projeyi geri yükler.

- **`--packages <PACKAGES_DIRECTORY>`**

  Geri yüklenen paketler için dizini belirtir.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Paket geri yüklemesi için bir çalışma zamanı belirtir. Bu, `<RuntimeIdentifiers>` *.csproj* dosyasındaki etikette açıkça belirtilmeyen çalışma süreleri için paketleri geri yüklemek için kullanılır. Runtime Tanımlayıcıları (RID'ler) listesi için RID [kataloğuna](../rid-catalog.md)bakın. Bu seçeneği birden çok kez belirterek birden çok RID sağlayın.

- **`-s|--source <SOURCE>`**

  Geri yükleme işlemi sırasında kullanılacak bir NuGet paket kaynağını belirtir. Bu ayar *nuget.config* dosyalarında belirtilen tüm kaynakları geçersiz kılar. Bu seçeneği birden çok kez belirterek birden çok kaynak sağlanabilir.

- **`--use-lockfile`**

  Proje kilit dosyasının oluşturulmasını ve geri yükleme ile kullanılmasını sağlar.

- **`-v|--verbosity <LEVEL>`**

  Komutun ayrıntılı düzeyini ayarlar. İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve . Varsayılan değer. `minimal`

## <a name="examples"></a>Örnekler

- Geçerli dizindeki proje için bağımlılıkları ve araçları geri yükleyin:

  ```dotnetcli
  dotnet restore
  ```

- Verilen yolda bulunan `app1` proje için bağımlılıkları ve araçları geri yükleyin:

  ```dotnetcli
  dotnet restore ~/projects/app1/app1.csproj
  ```

- Kaynak olarak sağlanan dosya yolunu kullanarak geçerli dizindeki projeye ilişkin bağımlılıkları ve araçları geri yükleyin:

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages
  ```

- Kaynak olarak sağlanan iki dosya yolunu kullanarak geçerli dizindeki proje ye bağımlılıkları ve araçları geri yükleyin:

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages
  ```

- Ayrıntılı çıktıyı gösteren geçerli dizinde proje için bağımlılıkları ve araçları geri yükleyin:

  ```dotnetcli
  dotnet restore --verbosity detailed
  ```
