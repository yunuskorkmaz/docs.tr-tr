---
title: DotNet paketi komutu
description: DotNet Pack komutu, .NET Core projeniz için NuGet paketleri oluşturur.
ms.date: 08/08/2019
ms.openlocfilehash: ba5a438d58963222c3fa55d2c585ef503dcd49db
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990418"
---
# <a name="dotnet-pack"></a>dotnet pack

**Bu konu şu şekilde geçerlidir: ✓** .NET Core 1. x SDK ve sonraki sürümleri

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Ad

`dotnet pack`-Kodu bir NuGet paketine paketler.

## <a name="synopsis"></a>Özeti

```console
dotnet pack [<PROJECT>|<SOLUTION>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--interactive] 
    [--no-build] [--no-dependencies] [--no-restore] [--nologo] [-o|--output] [--runtime] [-s|--serviceable] 
    [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

## <a name="description"></a>Açıklama

`dotnet pack` Komut projeyi oluşturur ve NuGet paketleri oluşturur. Bu komutun sonucu bir NuGet paketidir (yani, bir *. nupkg* dosyası). 

Hata ayıklama sembollerini içeren bir paket oluşturmak istiyorsanız iki seçeneğiniz vardır:

- `--include-symbols`-Bu, semboller paketini oluşturur.
- `--include-source`-Bu, kaynak dosyaları içeren içindeki bir `src` klasörü içeren semboller paketini oluşturur.

Paketlenmiş projenin NuGet bağımlılıkları *. nuspec* dosyasına eklenir, bu nedenle paket yüklenirken düzgün şekilde çözülür. Projeden projeye başvurular proje içinde paketlenmemiş. Şu anda, projeden projeye bağımlılıklar varsa proje başına bir pakete sahip olmanız gerekir.

Varsayılan olarak, `dotnet pack` önce projeyi oluşturur. Bu davranışı önlemek istiyorsanız, `--no-build` seçeneğini geçirin. Bu seçenek genellikle kodun daha önce oluşturulduğunu bildiğiniz sürekli tümleştirme (CI) derleme senaryolarında yararlıdır.

Paketleme işlemi için `dotnet pack` komutuna MSBuild özellikleri sağlayabilirsiniz. Daha fazla bilgi için bkz. [NuGet meta veri özellikleri](csproj.md#nuget-metadata-properties) ve [MSBuild komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference). [Örnekler](#examples) bölümü, MSBuild-p anahtarının birkaç farklı senaryo için nasıl kullanılacağını gösterir.

Web projeleri varsayılan olarak packable değildir. Varsayılan davranışı geçersiz kılmak için, *. csproj* dosyanıza aşağıdaki özelliği ekleyin:

```xml
<PropertyGroup>
   <IsPackable>true</IsPackable>
</PropertyGroup>
```

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a>Arguments

`PROJECT | SOLUTION`

  Paket için proje veya çözüm. Bu, bir [csproj dosyası](csproj.md), çözüm dosyası veya bir dizin yoludur. Belirtilmemişse, komut geçerli dizinde bir proje veya çözüm dosyası arar.

## <a name="options"></a>Seçenekler

* **`-c|--configuration {Debug|Release}`**

  Yapı yapılandırmasını tanımlar. Varsayılan değer `Debug` şeklindedir.

* **`--force`**

  Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar. Bu bayrağın belirtilmesi, *Project. varlıklar. JSON* dosyasını silme ile aynıdır. .NET Core 2,0 SDK 'dan beri kullanılabilir seçeneği.

* **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

* **`--include-source`**

  Çıkış dizinindeki normal NuGet paketlerine ek olarak hata ayıklama sembolleri NuGet paketlerini içerir. Kaynak dosyaları, semboller paketinin içindeki `src` klasörüne dahil edilmiştir.

* **`--include-symbols`**

  Çıkış dizinindeki normal NuGet paketlerine ek olarak hata ayıklama sembolleri NuGet paketlerini içerir.

* **`--interactive`**

  Komutun, Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir (örneğin, kimlik doğrulamasını tamamlamaya yönelik). .NET Core 3,0 SDK 'dan beri kullanılabilir.

* **`--no-build`**

  Paketleme öncesinde projeyi oluşturmaz. Ayrıca `--no-restore` bayrağı örtülü olarak ayarlar.

* **`--no-dependencies`**

  Projeden projeye başvuruları yoksayar ve yalnızca kök projeyi geri yükler. .NET Core 2,0 SDK 'dan beri kullanılabilir seçeneği.

* **`--no-restore`**

  Komutu çalıştırılırken örtük geri yükleme yürütülmez. .NET Core 2,0 SDK 'dan beri kullanılabilir seçeneği.

* **`--nologo`**

  Başlangıç başlığını veya telif hakkı iletisini görüntülemez. .NET Core 3,0 SDK 'dan beri kullanılabilir.

* **`-o|--output <OUTPUT_DIRECTORY>`**

  Oluşturulan paketleri belirtilen dizine koyar.

* **`--runtime <RUNTIME_IDENTIFIER>`**

  Paketlerinin geri yükleneceği hedef çalışma zamanını belirtir. Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md). .NET Core 2,0 SDK 'dan beri kullanılabilir seçeneği.

* **`-s|--serviceable`**

  Paketteki hizmet verebilir bayrağını ayarlar. Daha fazla bilgi için bkz. [.net blogu: .NET 4.5.1, .net NuGet kitaplıkları Için Microsoft güvenlik güncelleştirmelerini destekler](https://aka.ms/nupkgservicing).

* **`--version-suffix <VERSION_SUFFIX>`**

  Projedeki `$(VersionSuffix)` MSBuild özelliğinin değerini tanımlar.

* **`-v|--verbosity <LEVEL>`**

  Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]` `m[inimal]` ,`n[ormal]`,, ve .`diag[nostic]` `d[etailed]`

## <a name="examples"></a>Örnekler

* Projeyi geçerli dizinde paketleme:

  ```console
  dotnet pack
  ```

* `app1` Projeyi paketleme:

  ```console
  dotnet pack ~/projects/app1/project.csproj
  ```

* Projeyi geçerli dizinde paketedin ve elde edilen paketleri `nupkgs` klasörüne yerleştirin:

  ```console
  dotnet pack --output nupkgs
  ```

* Geçerli dizindeki `nupkgs` projeyi klasöre paketlayın ve derleme adımını atlayın:

  ```console
  dotnet pack --no-build --output nupkgs
  ```

* Projenin sürüm soneki `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` *. csproj* dosyasında olarak yapılandırıldığında, geçerli projeyi paketleyin ve elde edilen paket sürümünü verilen sonek ile güncelleştirin:

  ```console
  dotnet pack --version-suffix "ci-1234"
  ```

* Paket sürümünü `PackageVersion` MSBuild özelliği ile `2.1.0` olarak ayarlayın:

  ```console
  dotnet pack -p:PackageVersion=2.1.0
  ```

* Projeyi belirli bir [hedef çerçeve](../../standard/frameworks.md)için paketleme:

  ```console
  dotnet pack -p:TargetFrameworks=net45
  ```

* Projeyi paketleme ve geri yükleme işlemi için belirli bir çalışma zamanı (Windows 10) kullanın (.NET Core SDK 2,0 ve sonraki sürümler):

  ```console
  dotnet pack --runtime win10-x64
  ```

* Bir [. nuspec dosyası](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec)kullanarak projeyi paketleme:

  ```console
  dotnet pack ~/projects/app1/project.csproj -p:NuspecFile=~/projects/app1/project.nuspec -p:NuspecBasePath=~/projects/app1/nuget
  ```
