---
title: dotnet restore komutu
description: Dotnet restore komutuyla bağımlılıkları ve projeye özel araçları nasıl geri yükleyeceğinizi öğrenin.
ms.date: 02/27/2020
ms.openlocfilehash: e74027ba70ddf6905a12f9691caeb0a406428ad6
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157030"
---
# <a name="dotnet-restore"></a>dotnet restore

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri

## <a name="name"></a>Adı

`dotnet restore`-bir projenin bağımlılıklarını ve araçlarını geri yükler.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet restore [<ROOT>] [--configfile] [--disable-parallel]
    [--force] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime]
    [-s|--source] [-v|--verbosity] [--interactive]

dotnet restore [-h|--help]
```

## <a name="description"></a>Açıklama

`dotnet restore` komutu,, bağımlılıkları geri yüklemek için NuGet kullanır ve proje dosyasında belirtilen projeye özgü araçlardır. Varsayılan olarak, bağımlılıklar ve araçların geri yüklenmesi paralel olarak yürütülür.

Bağımlılıkları geri yüklemek için, NuGet paketlerin bulunduğu akışlara ihtiyaç duyuyor. Akışlar genellikle *NuGet. config* yapılandırma dosyası aracılığıyla sağlanır. .NET Core SDK yüklendiğinde varsayılan bir yapılandırma dosyası sağlanır. Proje dizininde kendi *NuGet. config* dosyanızı oluşturarak ek akışlar belirlersiniz. *NuGet. config* akışlarını-`-s` seçeneğiyle geçersiz kılabilirsiniz.

Bağımlılıklar için, geri yükleme işlemi sırasında `--packages` bağımsız değişkenini kullanarak geri yüklenen paketlerin nereye yerleştirileceğini belirtirsiniz. Belirtilmezse, varsayılan NuGet paketi önbelleği kullanılır ve bu, kullanıcının tüm işletim sistemlerindeki giriş dizinindeki `.nuget/packages` dizininde bulunur. Örneğin, Linux üzerinde */home/user1* veya Windows üzerinde *c:\Users\User1* .

Projeye özgü araçlar için `dotnet restore` önce aracın paketlenmesi gereken paketi geri yükler, sonra da araç bağımlılıklarını proje dosyasında belirtilen şekilde geri yüklemeye devam eder.

### <a name="nugetconfig-differences"></a>NuGet. config farklılıkları

`dotnet restore` komutunun davranışı, varsa *NuGet. config* dosyasındaki ayarlardan etkilenir. Örneğin, *NuGet. config* dosyasındaki `globalPackagesFolder` ayarlamak, geri yüklenen NuGet paketlerini belirtilen klasöre koyar. Bu, `dotnet restore` komutunda `--packages` seçeneğinin belirtilmesine alternatiftir. Daha fazla bilgi için bkz. [NuGet. config başvurusu](/nuget/schema/nuget-config-file).

`dotnet restore` göz ardı eden üç özel ayar vardır:

- [Bindingyönlendirmeler](/nuget/schema/nuget-config-file#bindingredirects-section)

  Bağlama yeniden yönlendirmeleri `<PackageReference>` öğeleriyle çalışmaz ve .NET Core yalnızca NuGet paketleri için `<PackageReference>` öğelerini destekler.

- [çözümden](/nuget/schema/nuget-config-file#solution-section)

  Bu ayar Visual Studio 'ya özeldir ve .NET Core için uygulanmaz. .NET Core bir `packages.config` dosyası kullanmaz ve bunun yerine NuGet paketleri için `<PackageReference>` öğeleri kullanır.

- [trustedSigners](/nuget/schema/nuget-config-file#trustedsigners-section)

  NuGet, güvenilen paketlerin [platformlar arası doğrulanmasını henüz desteklemediğinden](https://github.com/NuGet/Home/issues/7939) , bu ayar geçerli değildir.

## <a name="implicit-restore"></a>Örtük geri yükleme

Aşağıdaki komutları çalıştırdığınızda, gerekirse `dotnet restore` komutu örtülü olarak çalıştırılır:

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

Çoğu durumda, `dotnet restore` komutunu açıkça kullanmanız gerekmez.

Bazen `dotnet restore`, örtük olarak çalıştırmak kullanışlı olabilir. Örneğin, derleme sistemleri gibi bazı otomatikleştirilmiş sistemlerin, ağ kullanımını denetleyebilmeleri için geri yükleme işleminin ne zaman gerçekleşeceğini denetlemek üzere `dotnet restore` çağrısı yapması gerekir. `dotnet restore` örtük olarak çalışmasını engellemek için, örtük geri yüklemeyi devre dışı bırakmak üzere bu komutlardan herhangi biriyle `--no-restore` bayrağını kullanabilirsiniz.

## <a name="arguments"></a>Bağımsız Değişkenler

- **`ROOT`**

  Geri yüklenecek proje dosyasının isteğe bağlı yolu.

## <a name="options"></a>Seçenekler

- **`--configfile <FILE>`**

  Geri yükleme işlemi için kullanılacak NuGet yapılandırma dosyası (*NuGet. config*).

- **`--disable-parallel`**

  Paralel olarak birden çok projenin geri yüklenmesini devre dışı bırakır.

- **`--force`**

  Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar. Bu bayrağın belirtilmesi, *Project. varlıklar. JSON* dosyasını silme ile aynıdır.

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`--ignore-failed-sources`**

  Yalnızca sürüm gereksinimini karşılayan paketler varsa başarısız kaynaklar hakkında uyar.

- **`--no-cache`**

  Paketlerin ve HTTP isteklerinin önbelleğe alınamadı belirtir.

- **`--no-dependencies`**

  Projeden projeye (P2P) başvuruları olan bir projeyi geri yüklerken, başvuruları değil kök projeyi geri yükler.

- **`--packages <PACKAGES_DIRECTORY>`**

  Geri yüklenen paketlerin dizinini belirtir.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Paket geri yüklemesi için bir çalışma zamanı belirtir. Bu, *. csproj* dosyasındaki `<RuntimeIdentifiers>` etiketinde açıkça listelenmeyen çalışma zamanları paketlerini geri yüklemek için kullanılır. Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md). Bu seçeneği birden çok kez belirterek birden çok grup belirtin.

- **`-s|--source <SOURCE>`**

  Geri yükleme işlemi sırasında kullanılacak bir NuGet paket kaynağını belirtir. Bu ayar *NuGet. config* dosyalarında belirtilen tüm kaynakları geçersiz kılar. Bu seçenek birden çok kez belirtilerek birden çok kaynak sağlanarak sağlayabilirsiniz.

- **`--verbosity <LEVEL>`**

  Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`. Varsayılan değer `minimal`.

- **`--interactive`**

  Komutun Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir (örneğin, kimlik doğrulamasını tamamlamaya). .NET Core 2.1.400 'dan beri.

## <a name="examples"></a>Örnekler

- Geçerli dizindeki proje için bağımlılıkları ve araçları geri yükle:

  ```dotnetcli
  dotnet restore
  ```

- Verilen yolda bulunan `app1` projesi için bağımlılıkları ve araçları geri yükleyin:

  ```dotnetcli
  dotnet restore ~/projects/app1/app1.csproj
  ```

- Kaynak olarak belirtilen dosya yolunu kullanarak geçerli dizindeki proje için bağımlılıkları ve araçları geri yükleyin:

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages
  ```

- Kaynak olarak girilen iki dosya yolunu kullanarak geçerli dizindeki proje için bağımlılıkları ve araçları geri yükleyin:

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages
  ```

- Geçerli dizindeki proje için bağımlılıkları ve araçları ayrıntılı çıktıyı gösteren geri yükleyin:

  ```dotnetcli
  dotnet restore --verbosity detailed
  ```
