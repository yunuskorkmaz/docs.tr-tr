---
title: DotNet .NET Core CLI command - derleme
description: Dotnet bir proje ve tüm bağımlılıkları komutu derlemeleri oluşturun.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 6b0b7bc11b560d8632b38f1dfa4e7eb3ce6c54d2
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34697137"
---
# <a name="dotnet-build"></a>DotNet derleme

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet build` -Bir proje ve tüm bağımlılıkları oluşturur.

## <a name="synopsis"></a>Özet

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)
```
dotnet build [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--no-dependencies] [--no-incremental]
    [--no-restore] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]
dotnet build [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)
```
dotnet build [<PROJECT>] [-c|--configuration] [-f|--framework] [--no-dependencies] [--no-incremental] [-o|--output]
    [-r|--runtime] [-v|--verbosity] [--version-suffix]
dotnet build [-h|--help]
```
---

## <a name="description"></a>Açıklama

`dotnet build` Komut, ikili dosyalar kümesine proje ve bağımlılıklarını oluşturur. İkili dosyaları ara dile (IL) dosyalarıyla projenin kod dahil bir *.dll* ile hata ayıklama için kullanılan uzantı ve sembol dosyalarını bir *.pdb* uzantısı. Bağımlılıklar JSON dosyası (*\*. deps.json*) üretilir, uygulama bağımlılıkları listeler. A  *\*. runtimeconfig.json* dosyası oluşturulur, paylaşılan çalışma zamanı ve uygulama için sürümünü belirtir.

Proje NuGet kitaplıklarından gibi üçüncü taraf bağımlılıkları varsa, NuGet önbellekten çözülmüş ve projenin yerleşik çıktı ile kullanılamaz. Unutmayın, ürün alanıyla `dotnet build` çalıştırmak için başka bir makineye aktarılması hazır değil. Bu .NET Framework'ün aksine hangi binada yürütülebilir bir proje (uygulama) herhangi bir makinede runnable bir çıktı üretir, .NET Framework yüklü olduğu davranıştır. .NET Core benzer bir deneyim sağlamak için kullanmanız gereken [dotnet yayımlama](dotnet-publish.md) komutu. Daha fazla bilgi için bkz: [.NET Core uygulama dağıtımı](../deploying/index.md).

Yapı gerektirir *project.assets.json* uygulamanızın bağımlılıkları listeler dosya. Dosyanın ne zaman oluşturulur [ `dotnet restore` ](dotnet-restore.md) yürütülür. Varlıklar dosyayı yerinde hangi hatalar sonuçları başvuru derlemeleri araç çözümlenemiyor. .NET Core ile 1.x SDK, gerekli açıkça çalıştırmak `dotnet restore` çalıştırmadan önce `dotnet build`. .NET Core 2.0 SDK ile başlayan `dotnet restore` çalıştırdığınızda örtük olarak çalışır `dotnet build`. Yapı komutu çalıştırırken örtük geri yükleme devre dışı bırakmak istiyorsanız, geçirebilirsiniz `--no-restore` seçeneği.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

`dotnet build` MSBuild Projesi derlemek için kullanır, paralel ve artımlı destekler şekilde oluşturur. Daha fazla bilgi için bkz: [artımlı derlemeler](/visualstudio/msbuild/incremental-builds).

Kendi seçenekleri yanı sıra `dotnet build` komutu kabul MSBuild seçenekleri gibi `/p` özelliklerini ayarlamak için veya `/l` Günlükçü tanımlamak için. Bu seçenekler hakkında daha fazla bilgi için bkz: [MSBuild komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference).

Proje yürütülebilir olup olmamasına göre belirlenir. `<OutputType>` proje dosyası bir özellik. Aşağıdaki örnek yürütülebilir kod üreten bir proje gösterilmiştir:

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

Bir kitaplık üretmek için atlayın `<OutputType>` özelliği. Ana yerleşik çıktıda bir kitaplık için IL DLL giriş noktaları içermiyor ve yürütülemez farktır.

## <a name="arguments"></a>Arguments

`PROJECT`

Derleme projesi dosyası. MSBuild proje dosyası belirtilmezse, geçerli çalışma dizini ile biten bir dosya uzantısına sahip bir dosya için arar *proj* ve bu dosyayı kullanır.

## <a name="options"></a>Seçenekler

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

Derleme yapılandırması tanımlar. Varsayılan değer `Debug` şeklindedir.

`-f|--framework <FRAMEWORK>`

Özel bir derler [framework](../../standard/frameworks.md). Framework tanımlanmalıdır [proje dosyası](csproj.md).

`--force`

Son geri yükleme başarılı olsa bile çözümlenmesi için tüm bağımlılıkları zorlar. Bu bayrak belirten aynıdır silme *project.assets.json* dosya.

`-h|--help`

Komutu için kısa bir Yardım yazdırır.

`--no-dependencies`

Proje Proje (P2P) başvuruları yoksayar ve yalnızca belirtilen kök proje oluşturur.

`--no-incremental`

Yapı Artımlı derleme için güvensiz olarak işaretler. Bu bayrak Artımlı derlemeyi devre dışı bırakır ve temiz bir yeniden oluşturma, projenin bağımlılık grafiğinin zorlar.

`--no-restore`

Derleme sırasında örtük bir geri yükleme yürütmez.

`-o|--output <OUTPUT_DIRECTORY>`

Dizin oluşturulmuş ikili dosyalarının yerleştirileceği. Tanımlamanız gereken `--framework` bu seçeneği belirlediğinizde.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Hedef çalışma zamanı belirtir. Çalışma zamanı tanımlayıcıları (RID) bir listesi için bkz: [RID katalog](../rid-catalog.md).

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyi ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.

`--version-suffix <VERSION_SUFFIX>`

Sürüm soneki için bir yıldız işareti tanımlar (`*`) proje dosyasının sürüm alanında. NuGet sürümü yönergeleri biçimdedir.

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

Derleme yapılandırması tanımlar. Varsayılan değer `Debug` şeklindedir.

`-f|--framework <FRAMEWORK>`

Özel bir derler [framework](../../standard/frameworks.md). Framework tanımlanmalıdır [proje dosyası](csproj.md).

`-h|--help`

Komutu için kısa bir Yardım yazdırır.

`--no-dependencies`

Proje Proje (P2P) başvuruları yoksayar ve yalnızca belirtilen kök proje oluşturur.

`--no-incremental`

Yapı Artımlı derleme için güvensiz olarak işaretler. Bu bayrak Artımlı derlemeyi devre dışı bırakır ve temiz bir yeniden oluşturma, projenin bağımlılık grafiğinin zorlar.

`-o|--output <OUTPUT_DIRECTORY>`

Dizin oluşturulmuş ikili dosyalarının yerleştirileceği. Tanımlamanız gereken `--framework` bu seçeneği belirlediğinizde.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Hedef çalışma zamanı belirtir. Çalışma zamanı tanımlayıcıları (RID) bir listesi için bkz: [RID katalog](../rid-catalog.md).

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyi ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.

`--version-suffix <VERSION_SUFFIX>`

Sürüm soneki için bir yıldız işareti tanımlar (`*`) proje dosyasının sürüm alanında. NuGet sürümü yönergeleri biçimdedir.

---

## <a name="examples"></a>Örnekler

Proje ve bağımlılıklarını oluşturun:

`dotnet build`

Proje ve bağımlılıklarını yayın Yapılandırması'nı kullanarak oluşturun:

`dotnet build --configuration Release`

Proje ve bağımlılıklarını belirli bir çalışma zamanı (Bu örnekte, Ubuntu 16.04) için yapı:

`dotnet build --runtime ubuntu.16.04-x64`

Projeyi derlemek ve geri yükleme işlemi sırasında (.NET Core SDK 2.0 ve sonraki sürümler) belirtilen NuGet paket kaynağı kullanın:

`dotnet build --source c:\packages\mypackages`