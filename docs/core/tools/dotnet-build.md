---
title: DotNet oluşturma komutu
description: Dotnet bir projeyi ve tüm bağımlılıklarını komut derlemeleri oluşturun.
ms.date: 04/24/2019
ms.openlocfilehash: 6564aacbe520797b47095929cfe72c6b180b99a7
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632128"
---
# <a name="dotnet-build"></a>DotNet derleme

**Bu makale için geçerlidir: ✓** .NET Core SDK'sı 1.x ve sonraki sürümler

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Ad

`dotnet build` -Bir proje ve tüm bağımlılıklarını oluşturur.

## <a name="synopsis"></a>Synopsis

```
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--force] [--interactive] [--no-dependencies]
    [--no-incremental] [--nologo] [--no-restore] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```

## <a name="description"></a>Açıklama

`dotnet build` Komut projesi ve bağımlılıklarını ikili dosyaları kümesine oluşturur. Proje kodunuzun Ara dil (IL) dosyaları ile ikili dosyaları dahil bir *.dll* ile hata ayıklama için kullanılan uzantı ve sembol dosyalarını bir *.pdb* uzantısı. Bağımlılıkları JSON dosyası (*\*. deps.json*) üretilir, uygulama ile ilgili bağımlılıklar listelenmiştir. A  *\*. runtimeconfig.json* dosyası oluşturulur, paylaşılan çalışma zamanı ve uygulamanın sürümünü belirtir.

Proje, NuGet kitaplıklarından gibi üçüncü taraf bağımlılıkları varsa, NuGet önbellekten çözümlenen ve projenin çıkışı ile kullanılamaz. Unutmayın, ürün, ile `dotnet build` çalıştırmak için başka bir makineye aktarılmak hazır değil. Bu .NET Framework'ün aksine hangi binada bir yürütülebilir proje (uygulama), herhangi bir makinede çalıştırılabilir bir çıktı üretir. .NET Framework yüklendiği davranışıdır. .NET Core ile benzer bir deneyim sağlamak için kullanmanız gerekir [dotnet yayımlama](dotnet-publish.md) komutu. Daha fazla bilgi için [.NET Core uygulaması dağıtımını](../deploying/index.md).

Yapı gerektirir *project.assets.json* dosyasını uygulamanızın bağımlılıklar listelenmiştir. Bir dosya oluşturulur [ `dotnet restore` ](dotnet-restore.md) yürütülür. Varlıklar dosyayı yerinde araç hataları sonuçlanır başvuru derlemelerini çözümlenemiyor. .NET Core 1.x SDK'sı, gerekli açıkça çalıştırılacak `dotnet restore` çalıştırmadan önce `dotnet build`. .NET Core 2.0 SDK ile başlayarak `dotnet restore` çalıştırdığınızda örtülü olarak çalışan `dotnet build`. Oluşturma komutu çalıştırırken örtük geri yükleme devre dışı bırakmak isterseniz, geçirebilirsiniz `--no-restore` seçeneği.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

Projenin yürütülebilir olup olmamasına göre belirlenen `<OutputType>` proje dosyasındaki özellik. Aşağıdaki örnek, yürütülebilir kod üreten bir proje gösterir:

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

Bir kitaplığı üretmek için atla `<OutputType>` özelliği. Çıkışı ana fark, bir kitaplık için IL DLL giriş noktalarını içermiyor ve yürütülemez ' dir.

### <a name="msbuild"></a>MSBuild

`dotnet build` Projeyi derlemek için MSBuild kullanır, hem paralel hem de artımlı destekler şekilde oluşturur. Daha fazla bilgi için [artımlı derlemeler](/visualstudio/msbuild/incremental-builds).

Kendi seçenekleri yanı sıra `dotnet build` komutu kabul MSBUILD seçenekleri gibi `-p` özelliklerini ayarlamak için veya `-l` bir Günlükçü tanımlamak için. Bu seçenekler hakkında daha fazla bilgi için bkz. [MSBuild komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference). Ya da ayrıca [dotnet msbuild](dotnet-msbuild.md) komutu.

Çalışan `dotnet build` eşdeğerdir `dotnet msbuild -restore -target:Build`.

## <a name="arguments"></a>Arguments

`PROJECT | SOLUTION`

Derleme için proje veya çözüm dosyası. Bir proje veya çözüm dosyası belirtilmezse, MSBuild içinde biten bir dosya uzantısına sahip bir dosya için geçerli çalışma dizini arar *proj* veya *sln* ve bu dosyayı kullanır.

## <a name="options"></a>Seçenekler

* **`-c|--configuration {Debug|Release}`**

  Derleme yapılandırmasını tanımlar. Varsayılan değer `Debug` şeklindedir.

* **`-f|--framework <FRAMEWORK>`**

  Özel bir derleme [framework](../../standard/frameworks.md). Framework tanımlanmalıdır [proje dosyası](csproj.md).

* **`--force`**

  Son geri yükleme başarılı olduysa bile çözülmesi için tüm bağımlılıkların zorlar. Bu bayrak belirten aynıdır silme *project.assets.json* dosya. .NET Core 2.0 SDK'sı bu yana kullanılabilir.

* **`-h|--help`**

  Komut için kısa bir Yardım yazdırır.

* **`--interactive`**

  Durdurmak ve kullanıcı girişi ya da eylem için beklemek için komutu sağlar. Örneğin, kimlik doğrulamasını tamamlamak için. .NET Core SDK 3.0 bu yana kullanılabilir.

* **`--no-dependencies`**

  Projeden projeye (P2P) başvurularını yoksayar ve yalnızca belirtilen kök projeyi oluşturur.

* **`--no-incremental`**

  Derleme Artımlı derleme için güvensiz olarak işaretler. Bu bayrak, Artımlı derlemeyi devre dışı bırakır ve temiz bir projenin bağımlılık grafiği yeniden zorlar.

* **`--no-logo`**

  Başlangıç başlığını veya telif hakkı iletisini görüntülemez. .NET Core SDK 3.0 bu yana kullanılabilir.

* **`--no-restore`**

  Örtük bir geri yükleme derleme sırasında yürütülmez. .NET Core 2.0 SDK'sı bu yana kullanılabilir.

* **`-o|--output <OUTPUT_DIRECTORY>`**

  Yerleşik ikili dosyaların yerleştirileceği dizin. Tanımlamanız gereken `--framework` bu seçeneği belirttiğinizde. Belirtilmezse, varsayılan yoldur `./bin/<configuration>/<framework>/`.

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Hedef çalışma zamanı belirtir. Çalışma zamanı tanımlayıcılarının (RID'ler) bir listesi için bkz. [RID Kataloğu](../rid-catalog.md).

* **`-v|--verbosity <LEVEL>`**

  MSBuild ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`. Varsayılan, `minimal` değeridir.

* **`--version-suffix <VERSION_SUFFIX>`**

  Ayarlar `$(VersionSuffix)` proje derlenirken kullanılacak özellik. Bu, yalnızca çalışır `$(Version)` özelliği ayarlanmamış. Ardından, `$(Version)` ayarlanır `$(VersionPrefix)` birlikte `$(VersionSuffix)`kısa çizgiyle ayrılmış.

## <a name="examples"></a>Örnekler

* Bir proje ve bağımlılıkları derleme:

  ```console
  dotnet build
  ```

* Bir proje ve bağımlılıkları sürüm yapılandırmasını oluşturun:

  ```console
  dotnet build --configuration Release
  ```

* Bir proje ve bağımlılıkları (Bu örnekte, Ubuntu 18.04) belirli bir çalışma zamanı için derleme:

  ```console
  dotnet build --runtime ubuntu.18.04-x64
  ```

* Projeyi oluşturmak ve geri yükleme işlemi sırasında (.NET Core 2.0 SDK'sını ve sonraki sürümler) belirtilen NuGet paket kaynağı kullanın:

  ```console
  dotnet build --source c:\packages\mypackages
  ```

* Projeyi oluşturmak ve ayarlamak 1.2.3.4 derleme parametre olarak sürüm:

  ```console
  dotnet build -p:Version=1.2.3.4
  ```
