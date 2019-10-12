---
title: DotNet derleme komutu
description: DotNet derleme komutu bir projeyi ve tüm bağımlılıklarını oluşturur.
ms.date: 10/07/2019
ms.openlocfilehash: db353feebab920dc8f63b9854d14f050adeb0b79
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250187"
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

@No__t-0 komutu, projeyi ve onun bağımlılıklarını bir ikili dosya kümesine oluşturur. İkililer, bir. *pdb* uzantısıyla hata ayıklama için kullanılan bir *. dll* uzantısına ve sembol dosyalarına sahip olan ara dil (IL) dosyalarındaki projenin kodunu içerir. Uygulamanın bağımlılıklarını listeleyen bir bağımlılıklar JSON dosyası ( *. Deps. JSON*) oluşturulur. Bir *. runtimeconfig. JSON* dosyası oluşturulur, bu, paylaşılan çalışma zamanını ve uygulamanın sürümünü belirtir.

Projenin NuGet kitaplığı gibi üçüncü taraf bağımlılıkları varsa, bunlar NuGet önbelleğinden çözülür ve projenin oluşturulan çıkışıyla birlikte kullanılamaz. Bu şekilde `dotnet build` ürünü, çalıştırmak için başka bir makineye aktarılmaya hazırlanmıyor. Bu, yürütülebilir bir proje (bir uygulama) oluşturmanın, .NET Framework yüklendiği herhangi bir makinede çalıştırılabilir bir çıktı oluşturduğu .NET Framework davranışına karşılık gelir. .NET Core ile benzer bir deneyim sunmak için [DotNet Publish](dotnet-publish.md) komutunu kullanmanız gerekir. Daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md).

Oluşturma, uygulamanızın bağımlılıklarını listeleyen *Project. varlıklar. JSON* dosyasını gerektirir. [@No__t-1](dotnet-restore.md) yürütüldüğünde dosya oluşturulur. Varlıklar dosyası olmadan, Araçlar başvuru derlemelerini çözemez, bu da hatalara neden olur. .NET Core 1. x SDK ile, `dotnet build` ' i çalıştırmadan önce `dotnet restore` ' ı açık olarak çalıştırmanız gerekir. @No__t-1 ' i çalıştırdığınızda `dotnet restore`, .NET Core 2,0 SDK ile başlayarak örtülü olarak çalışır. Build komutunu çalıştırırken örtük geri yüklemeyi devre dışı bırakmak istiyorsanız, `--no-restore` seçeneğini geçirebilirsiniz.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

Projenin yürütülebilir olup olmadığı veya proje dosyasındaki `<OutputType>` özelliği tarafından belirlenmediği. Aşağıdaki örnekte yürütülebilir kod üreten bir proje gösterilmektedir:

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

Bir kitaplık oluşturmak için `<OutputType>` özelliğini atlayın. Oluşturulan çıktıda ana fark, bir kitaplık için Il DLL 'sinin giriş noktaları içermemesi ve yürütülemeyecek.

### <a name="msbuild"></a>MSBuild

`dotnet build`, projeyi derlemek için MSBuild kullanır, bu nedenle hem paralel hem de artımlı yapıları destekler. Daha fazla bilgi için bkz. [Artımlı derlemeler](/visualstudio/msbuild/incremental-builds).

@No__t-0 komutu, seçeneklerini ayarlamak için `-p` veya bir günlükçü tanımlamak için `-l` gibi MSBuild seçeneklerini kabul eder. Bu seçenekler hakkında daha fazla bilgi için bkz. [MSBuild komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference). Ayrıca [DotNet MSBuild](dotnet-msbuild.md) komutunu da kullanabilirsiniz.

@No__t-0 ' ın çalıştırılması `dotnet msbuild -restore -target:Build` ' e eşdeğerdir.

## <a name="arguments"></a>Arguments

`PROJECT | SOLUTION`

Derlenecek proje veya çözüm dosyası. Bir proje veya çözüm dosyası belirtilmemişse, MSBuild, *proj* veya *sln* 'de biten bir dosya uzantısına sahip bir dosya için geçerli çalışma dizinini arar ve bu dosyayı kullanır.

## <a name="options"></a>Seçenekler

* **`-c|--configuration {CONFIGURATION}`**

  Yapı yapılandırmasını tanımlar. Çoğu proje için varsayılan değer `Debug` ' dır, ancak projenizde derleme yapılandırma ayarlarını geçersiz kılabilirsiniz.

* **`-f|--framework <FRAMEWORK>`**

  Belirli bir [çerçeve](../../standard/frameworks.md)için derlenir. Çerçeve [Proje dosyasında](csproj.md)tanımlanmalıdır.

* **`--force`**

  Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar. Bu bayrağın belirtilmesi, *Project. varlıklar. JSON* dosyasını silme ile aynıdır. .NET Core 2,0 SDK 'dan beri kullanılabilir.

* **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

* **`--interactive`**

  Komutun Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir. Örneğin, kimlik doğrulamasını tamamlamaya yönelik. .NET Core 3,0 SDK 'dan beri kullanılabilir.

* **`--no-dependencies`**

  Projeden projeye (P2P) başvurularını yoksayar ve yalnızca belirtilen kök projeyi oluşturur.

* **`--no-incremental`**

  Derlemeyi Artımlı derleme için güvenli değil olarak işaretler. Bu bayrak, artımlı derlemeyi kapatır ve projenin bağımlılık grafiğinin temiz bir yeniden oluşturulmasına zorlar.

* **`--no-restore`**

  Derleme sırasında örtük geri yükleme yürütmez. .NET Core 2,0 SDK 'dan beri kullanılabilir.

* **`--nologo`**

  Başlangıç başlığını veya telif hakkı iletisini görüntülemez. .NET Core 3,0 SDK 'dan beri kullanılabilir.

* **`-o|--output <OUTPUT_DIRECTORY>`**

  Oluşturulan ikililerin yerleştirileceği dizin. Ayrıca, bu seçeneği belirttiğinizde `--framework` tanımlamanız gerekir. Belirtilmemişse, varsayılan yol `./bin/<configuration>/<framework>/` ' dır.

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Hedef çalışma zamanını belirtir. Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md).

* **`-v|--verbosity <LEVEL>`**

  MSBuild ayrıntı düzeyi düzeyini ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` ve `diag[nostic]` ' dir. Varsayılan, `minimal` değeridir.

* **`--version-suffix <VERSION_SUFFIX>`**

  Projeyi oluştururken kullanılacak `$(VersionSuffix)` özelliğinin değerini ayarlar. Bu yalnızca `$(Version)` özelliği ayarlanmamışsa işe yarar. Sonra, `$(Version)`, `$(VersionSuffix)` ile Birleşik @no__t bir çizgiyle ayrılmış şekilde ayarlanır.

## <a name="examples"></a>Örnekler

* Bir proje ve bağımlılıklarını oluşturun:

  ```dotnetcli
  dotnet build
  ```

* Yayın yapılandırması kullanarak bir proje ve bağımlılıklarını oluşturun:

  ```dotnetcli
  dotnet build --configuration Release
  ```

* Belirli bir çalışma zamanı için bir proje ve bağımlılıklarını oluşturun (Bu örnekte Ubuntu 18,04):

  ```dotnetcli
  dotnet build --runtime ubuntu.18.04-x64
  ```

* Projeyi derleyin ve geri yükleme işlemi sırasında belirtilen NuGet paket kaynağını kullanın (.NET Core 2,0 SDK ve sonraki sürümleri):

  ```dotnetcli
  dotnet build --source c:\packages\mypackages
  ```

* Projeyi derleyin ve `-p` [MSBuild seçeneğini](#msbuild)kullanarak bir yapı parametresi olarak 1.2.3.4 öğesini ayarlayın:

  ```dotnetcli
  dotnet build -p:Version=1.2.3.4
  ```
