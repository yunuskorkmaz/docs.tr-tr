---
title: DotNet derleme komutu
description: DotNet derleme komutu bir projeyi ve tüm bağımlılıklarını oluşturur.
ms.date: 10/14/2019
ms.openlocfilehash: fe2135c150be46997699f756f7f0c9bc18bbb529
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846820"
---
# <a name="dotnet-build"></a>dotnet build

**Bu makale şu şekilde geçerlidir: ✓** .NET Core 1. x SDK ve sonraki sürümleri

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Name

`dotnet build`-bir projeyi ve tüm bağımlılıklarını oluşturur.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--force] [--interactive] [--no-dependencies]
    [--no-incremental] [--no-restore] [--nologo] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```

## <a name="description"></a>Açıklama

`dotnet build` komutu projeyi ve onun bağımlılıklarını bir ikili dosya kümesine oluşturur. İkili dosyalar, projenin kodunu *. dll* uzantılı ara DIL (IL) dosyalarına dahil eder.  Proje türü ve ayarlarına bağlı olarak, şu gibi diğer dosyalar dahil edilebilir:

- Proje türü, .NET Core 3,0 veya üstünü hedefleyen bir yürütülebilir dosya ise, uygulamayı çalıştırmak için kullanılabilecek bir çalıştırılabilir dosya.
- Bir *. pdb* uzantısıyla hata ayıklama için kullanılan sembol dosyaları.
- Uygulamanın veya kitaplığın bağımlılıklarını listeleyen *. Deps. JSON* dosyası.
- Paylaşılan çalışma zamanını ve bir uygulamanın sürümünü belirten *. runtimeconfig. JSON* dosyası.
- Projenin bağımlı olduğu diğer kitaplıklar (proje başvuruları veya NuGet paket başvuruları aracılığıyla).

.NET Core 3,0 ' den önceki sürümleri hedefleyen yürütülebilir projeler için, NuGet 'deki kitaplık bağımlılıkları genellikle çıkış klasörüne kopyalanmaz.  Bunlar, çalışma zamanında NuGet genel paketler klasöründen çözümlenirler. Bu şekilde `dotnet build` ürünü, çalıştırmak için başka bir makineye aktarılmaya hazırlanmıyor. Uygulamasının dağıtılabilecek bir sürümünü oluşturmak için (örneğin, [DotNet Publish](dotnet-publish.md) komutuyla) yayımlamanız gerekir. Daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md).

.NET Core 3,0 ve üstünü hedefleyen yürütülebilir projelerde, kitaplık bağımlılıkları çıkış klasörüne kopyalanır. Bu, başka bir yayınla özel mantık (örneğin, Web projeleri) yoksa, yapı çıkışının dağıtılabilir olması anlamına gelir.

Oluşturma, uygulamanızın bağımlılıklarını listeleyen *Project. varlıklar. JSON* dosyasını gerektirir. [`dotnet restore`](dotnet-restore.md) yürütüldüğünde dosya oluşturulur. Varlıklar dosyası olmadan, Araçlar başvuru derlemelerini çözemez, bu da hatalara neden olur. .NET Core 1. x SDK ile, `dotnet build` ' i çalıştırmadan önce `dotnet restore` ' ı açık olarak çalıştırmanız gerekir. .NET Core 2,0 SDK ile başlayarak, `dotnet build` çalıştırdığınızda `dotnet restore` örtülü olarak çalışır. Build komutunu çalıştırırken örtük geri yüklemeyi devre dışı bırakmak istiyorsanız, `--no-restore` seçeneğini geçirebilirsiniz.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

Projenin yürütülebilir olup olmadığı veya proje dosyasındaki `<OutputType>` özelliği tarafından belirlenmediği. Aşağıdaki örnekte yürütülebilir kod üreten bir proje gösterilmektedir:

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

Bir kitaplık oluşturmak için `<OutputType>` özelliğini atlayın veya değerini `Library`olarak değiştirin. Bir kitaplığın Il DLL 'SI giriş noktaları içermiyor ve yürütülemiyor.

### <a name="msbuild"></a>MSBuild

`dotnet build`, projeyi derlemek için MSBuild kullanır, bu nedenle hem paralel hem de artımlı yapıları destekler. Daha fazla bilgi için bkz. [Artımlı derlemeler](/visualstudio/msbuild/incremental-builds).

`dotnet build` komutu, seçeneklerine ek olarak, özellikleri ayarlamak için `-p` veya bir günlükçü tanımlamak için `-l` gibi MSBuild seçeneklerini kabul eder. Bu seçenekler hakkında daha fazla bilgi için bkz. [MSBuild komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference). Ayrıca [DotNet MSBuild](dotnet-msbuild.md) komutunu da kullanabilirsiniz.

Çalışan `dotnet build`, çalışan `dotnet msbuild -restore`eşdeğerdir; Ancak, çıktının varsayılan ayrıntı düzeyi farklıdır.

## <a name="arguments"></a>Arguments

`PROJECT | SOLUTION`

Derlenecek proje veya çözüm dosyası. Bir proje veya çözüm dosyası belirtilmemişse, MSBuild, *proj* veya *sln* 'de biten bir dosya uzantısına sahip bir dosya için geçerli çalışma dizinini arar ve bu dosyayı kullanır.

## <a name="options"></a>Seçenekler

- **`-c|--configuration {Debug|Release}`**

  Yapı yapılandırmasını tanımlar. Çoğu proje için varsayılan değer `Debug` ' dır, ancak projenizde derleme yapılandırma ayarlarını geçersiz kılabilirsiniz.

- **`-f|--framework <FRAMEWORK>`**

  Belirli bir [çerçeve](../../standard/frameworks.md)için derlenir. Çerçeve [Proje dosyasında](csproj.md)tanımlanmalıdır.

- **`--force`**

  Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar. Bu bayrağın belirtilmesi, *Project. varlıklar. JSON* dosyasını silme ile aynıdır. .NET Core 2,0 SDK 'dan beri kullanılabilir.

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`--interactive`**

  Komutun Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir. Örneğin, kimlik doğrulamasını tamamlamaya yönelik. .NET Core 3,0 SDK 'dan beri kullanılabilir.

- **`--no-dependencies`**

  Projeden projeye (P2P) başvurularını yoksayar ve yalnızca belirtilen kök projeyi oluşturur.

- **`--no-incremental`**

  Derlemeyi Artımlı derleme için güvenli değil olarak işaretler. Bu bayrak, artımlı derlemeyi kapatır ve projenin bağımlılık grafiğinin temiz bir yeniden oluşturulmasına zorlar.

- **`--no-restore`**

  Derleme sırasında örtük geri yükleme yürütmez. .NET Core 2,0 SDK 'dan beri kullanılabilir.

- **`--nologo`**

  Başlangıç başlığını veya telif hakkı iletisini görüntülemez. .NET Core 3,0 SDK 'dan beri kullanılabilir.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Oluşturulan ikililerin yerleştirileceği dizin. Belirtilmemişse, varsayılan yol `./bin/<configuration>/<framework>/` ' dır.  Birden çok hedef çerçevesi olan projeler için (`TargetFrameworks` özelliği aracılığıyla), bu seçeneği belirttiğinizde de `--framework` tanımlamanız gerekir.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Hedef çalışma zamanını belirtir. Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md).

- **`-v|--verbosity <LEVEL>`**

  MSBuild ayrıntı düzeyi düzeyini ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`. Varsayılan, `minimal` değeridir.

- **`--version-suffix <VERSION_SUFFIX>`**

  Projeyi oluştururken kullanılacak `$(VersionSuffix)` özelliğinin değerini ayarlar. Bu yalnızca `$(Version)` özelliği ayarlanmamışsa işe yarar. Daha sonra, `$(Version)`, bir çizgiyle ayırarak `$(VersionSuffix)` ile Birleşik `$(VersionPrefix)` ayarlanır.

## <a name="examples"></a>Örnekler

- Bir proje ve bağımlılıklarını oluşturun:

  ```dotnetcli
  dotnet build
  ```

- Yayın yapılandırması kullanarak bir proje ve bağımlılıklarını oluşturun:

  ```dotnetcli
  dotnet build --configuration Release
  ```

- Belirli bir çalışma zamanı için bir proje ve bağımlılıklarını oluşturun (Bu örnekte Ubuntu 18,04):

  ```dotnetcli
  dotnet build --runtime ubuntu.18.04-x64
  ```

- Projeyi derleyin ve geri yükleme işlemi sırasında belirtilen NuGet paket kaynağını kullanın (.NET Core 2,0 SDK ve sonraki sürümleri):

  ```dotnetcli
  dotnet build --source c:\packages\mypackages
  ```

- Projeyi derleyin ve `-p` [MSBuild seçeneğini](#msbuild)kullanarak bir yapı parametresi olarak 1.2.3.4 öğesini ayarlayın:

  ```dotnetcli
  dotnet build -p:Version=1.2.3.4
  ```
