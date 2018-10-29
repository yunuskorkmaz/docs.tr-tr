---
title: DotNet - command .NET Core CLI oluşturun
description: Dotnet bir projeyi ve tüm bağımlılıklarını komut derlemeleri oluşturun.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: c9d1478e3d3e298b01e707242cc7ad5cd924a9b3
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50200563"
---
# <a name="dotnet-build"></a>DotNet derleme

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet build` -Bir proje ve tüm bağımlılıklarını oluşturur.

## <a name="synopsis"></a>Özeti

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)
```
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--force] [--no-dependencies] [--no-incremental]
    [--no-restore] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)
```
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--no-dependencies] [--no-incremental] [-o|--output]
    [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```
---

## <a name="description"></a>Açıklama

`dotnet build` Komut projesi ve bağımlılıklarını ikili dosyaları kümesine oluşturur. Proje kodunuzun Ara dil (IL) dosyaları ile ikili dosyaları dahil bir *.dll* ile hata ayıklama için kullanılan uzantı ve sembol dosyalarını bir *.pdb* uzantısı. Bağımlılıkları JSON dosyası (*\*. deps.json*) üretilir, uygulama ile ilgili bağımlılıklar listelenmiştir. A  *\*. runtimeconfig.json* dosyası oluşturulur, paylaşılan çalışma zamanı ve uygulamanın sürümünü belirtir.

Proje, NuGet kitaplıklarından gibi üçüncü taraf bağımlılıkları varsa, NuGet önbellekten çözümlenen ve projenin çıkışı ile kullanılamaz. Unutmayın, ürün, ile `dotnet build` çalıştırmak için başka bir makineye aktarılmak hazır değil. Bu .NET Framework'ün aksine hangi binada bir yürütülebilir proje (uygulama), herhangi bir makinede çalıştırılabilir bir çıktı üretir. .NET Framework yüklendiği davranışıdır. .NET Core ile benzer bir deneyim sağlamak için kullanmanız gerekir [dotnet yayımlama](dotnet-publish.md) komutu. Daha fazla bilgi için [.NET Core uygulaması dağıtımını](../deploying/index.md).

Yapı gerektirir *project.assets.json* dosyasını uygulamanızın bağımlılıklar listelenmiştir. Bir dosya oluşturulur [ `dotnet restore` ](dotnet-restore.md) yürütülür. Varlıklar dosyayı yerinde araç hataları sonuçlanır başvuru derlemelerini çözümlenemiyor. .NET Core 1.x SDK'sı, gerekli açıkça çalıştırılacak `dotnet restore` çalıştırmadan önce `dotnet build`. .NET Core 2.0 SDK ile başlayarak `dotnet restore` çalıştırdığınızda örtülü olarak çalışan `dotnet build`. Oluşturma komutu çalıştırırken örtük geri yükleme devre dışı bırakmak isterseniz, geçirebilirsiniz `--no-restore` seçeneği.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

`dotnet build` Projeyi derlemek için MSBuild kullanır, hem paralel hem de artımlı destekler şekilde oluşturur. Daha fazla bilgi için [artımlı derlemeler](/visualstudio/msbuild/incremental-builds).

Kendi seçenekleri yanı sıra `dotnet build` komutu kabul MSBUILD seçenekleri gibi `-p` özelliklerini ayarlamak için veya `-l` bir Günlükçü tanımlamak için. Bu seçenekler hakkında daha fazla bilgi için bkz. [MSBuild komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference).

Projenin yürütülebilir olup olmamasına göre belirlenen `<OutputType>` proje dosyasındaki özellik. Aşağıdaki örnek, yürütülebilir kod üreten bir proje gösterir:

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

Bir kitaplığı üretmek için atla `<OutputType>` özelliği. Çıkışı ana fark, bir kitaplık için IL DLL giriş noktalarını içermiyor ve yürütülemez ' dir.

## <a name="arguments"></a>Arguments

`PROJECT | SOLUTION`

Derleme için proje veya çözüm dosyası. Bir proje veya çözüm dosyası belirtilmezse, MSBuild içinde biten bir dosya uzantısına sahip bir dosya için geçerli çalışma dizini arar *proj* veya *sln* ve bu dosyayı kullanır.

## <a name="options"></a>Seçenekler

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

Derleme yapılandırmasını tanımlar. Varsayılan değer `Debug` şeklindedir.

`-f|--framework <FRAMEWORK>`

Özel bir derleme [framework](../../standard/frameworks.md). Framework tanımlanmalıdır [proje dosyası](csproj.md).

`--force`

Son geri yükleme başarılı olduysa bile çözülmesi için tüm bağımlılıkların zorlar. Bu bayrak belirten aynıdır silme *project.assets.json* dosya.

`-h|--help`

Komut için kısa bir Yardım yazdırır.

`--no-dependencies`

Projeden projeye (P2P) başvurularını yoksayar ve yalnızca belirtilen kök projeyi oluşturur.

`--no-incremental`

Derleme Artımlı derleme için güvensiz olarak işaretler. Bu bayrak, Artımlı derlemeyi devre dışı bırakır ve temiz bir projenin bağımlılık grafiği yeniden zorlar.

`--no-restore`

Örtük bir geri yükleme derleme sırasında yürütülmez.

`-o|--output <OUTPUT_DIRECTORY>`

Yerleşik ikili dosyaların yerleştirileceği dizin. Tanımlamanız gereken `--framework` bu seçeneği belirttiğinizde.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Hedef çalışma zamanı belirtir. Çalışma zamanı tanımlayıcılarının (RID'ler) bir listesi için bkz. [RID Kataloğu](../rid-catalog.md).

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.

`--version-suffix <VERSION_SUFFIX>`

Sürüm soneki için bir yıldız işareti tanımlar (`*`) proje dosyasının sürümü alanında. NuGet'ın sürümü yönergeleri biçimdedir.

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

Derleme yapılandırmasını tanımlar. Varsayılan değer `Debug` şeklindedir.

`-f|--framework <FRAMEWORK>`

Özel bir derleme [framework](../../standard/frameworks.md). Framework tanımlanmalıdır [proje dosyası](csproj.md).

`-h|--help`

Komut için kısa bir Yardım yazdırır.

`--no-dependencies`

Projeden projeye (P2P) başvurularını yoksayar ve yalnızca belirtilen kök projeyi oluşturur.

`--no-incremental`

Derleme Artımlı derleme için güvensiz olarak işaretler. Bu bayrak, Artımlı derlemeyi devre dışı bırakır ve temiz bir projenin bağımlılık grafiği yeniden zorlar.

`-o|--output <OUTPUT_DIRECTORY>`

Yerleşik ikili dosyaların yerleştirileceği dizin. Tanımlamanız gereken `--framework` bu seçeneği belirttiğinizde.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Hedef çalışma zamanı belirtir. Çalışma zamanı tanımlayıcılarının (RID'ler) bir listesi için bkz. [RID Kataloğu](../rid-catalog.md).

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.

`--version-suffix <VERSION_SUFFIX>`

Sürüm soneki için bir yıldız işareti tanımlar (`*`) proje dosyasının sürümü alanında. NuGet'ın sürümü yönergeleri biçimdedir.

---

## <a name="examples"></a>Örnekler

Bir proje ve bağımlılıkları derleme:

`dotnet build`

Bir proje ve bağımlılıkları sürüm yapılandırmasını oluşturun:

`dotnet build --configuration Release`

Bir proje ve bağımlılıkları (Bu örnekte, Ubuntu 16.04) belirli bir çalışma zamanı için derleme:

`dotnet build --runtime ubuntu.16.04-x64`

Projeyi oluşturmak ve geri yükleme işlemi sırasında (.NET Core SDK 2.0 ve sonraki sürümler) belirtilen NuGet paket kaynağı kullanın:

`dotnet build --source c:\packages\mypackages`