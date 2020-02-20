---
title: DotNet paketi komutu
description: DotNet Pack komutu, .NET Core projeniz için NuGet paketleri oluşturur.
ms.date: 02/14/2020
ms.openlocfilehash: 865262f1eb314f9b7e8ee713c573a965e89ded93
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503651"
---
# <a name="dotnet-pack"></a>dotnet pack

**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2. x SDK ve sonraki sürümleri

## <a name="name"></a>Adı

`dotnet pack`-kodu bir NuGet paketine paketler.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet pack [<PROJECT>|<SOLUTION>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--interactive]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo] [-o|--output] [--runtime] [-s|--serviceable]
    [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

## <a name="description"></a>Açıklama

`dotnet pack` komutu projeyi oluşturur ve NuGet paketleri oluşturur. Bu komutun sonucu bir NuGet paketidir (yani, bir *. nupkg* dosyası).

Hata ayıklama sembollerini içeren bir paket oluşturmak istiyorsanız iki seçeneğiniz vardır:

- `--include-symbols`-bu, semboller paketini oluşturur.
- `--include-source`-kaynak dosyaları içeren içindeki bir `src` klasörüyle birlikte semboller paketini oluşturur.

Paketlenmiş projenin NuGet bağımlılıkları *. nuspec* dosyasına eklenir, bu nedenle paket yüklenirken düzgün şekilde çözülür. Projeden projeye başvurular proje içinde paketlenmemiş. Şu anda, projeden projeye bağımlılıklar varsa proje başına bir pakete sahip olmanız gerekir.

Varsayılan olarak, `dotnet pack` önce projeyi oluşturur. Bu davranışı önlemek istiyorsanız `--no-build` seçeneğini geçirin. Bu seçenek genellikle kodun daha önce oluşturulduğunu bildiğiniz sürekli tümleştirme (CI) derleme senaryolarında yararlıdır.

Paketleme işlemi için `dotnet pack` komutuna MSBuild özellikleri sağlayabilirsiniz. Daha fazla bilgi için bkz. [NuGet meta veri özellikleri](csproj.md#nuget-metadata-properties) ve [MSBuild komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference). [Örnekler](#examples) bölümü, MSBuild-p anahtarının birkaç farklı senaryo için nasıl kullanılacağını gösterir.

Web projeleri varsayılan olarak packable değildir. Varsayılan davranışı geçersiz kılmak için, *. csproj* dosyanıza aşağıdaki özelliği ekleyin:

```xml
<PropertyGroup>
   <IsPackable>true</IsPackable>
</PropertyGroup>
```

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a>Bağımsız Değişkenler

`PROJECT | SOLUTION`

  Paket için proje veya çözüm. Bu, bir [csproj dosyası](csproj.md), çözüm dosyası veya bir dizin yoludur. Belirtilmemişse, komut geçerli dizinde bir proje veya çözüm dosyası arar.

## <a name="options"></a>Seçenekler

- **`-c|--configuration <CONFIGURATION>`**

  Yapı yapılandırmasını tanımlar. Çoğu proje için varsayılan değer `Debug`, ancak projenizde derleme yapılandırma ayarlarını geçersiz kılabilirsiniz.

- **`--force`**

  Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar. Bu bayrağın belirtilmesi, *Project. varlıklar. JSON* dosyasını silme ile aynıdır.

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`--include-source`**

  Çıkış dizinindeki normal NuGet paketlerine ek olarak hata ayıklama sembolleri NuGet paketlerini içerir. Kaynak dosyaları, semboller paketinin içindeki `src` klasörüne eklenir.

- **`--include-symbols`**

  Çıkış dizinindeki normal NuGet paketlerine ek olarak hata ayıklama sembolleri NuGet paketlerini içerir.

- **`--interactive`**

  Komutun, Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir (örneğin, kimlik doğrulamasını tamamlamaya yönelik). .NET Core 3,0 SDK 'dan beri kullanılabilir.

- **`--no-build`**

  Paketleme öncesinde projeyi oluşturmaz. Ayrıca `--no-restore` bayrağını örtülü olarak ayarlar.

- **`--no-dependencies`**

  Projeden projeye başvuruları yoksayar ve yalnızca kök projeyi geri yükler.

- **`--no-restore`**

  Komutu çalıştırılırken örtük geri yükleme yürütülmez.

- **`--nologo`**

  Başlangıç başlığını veya telif hakkı iletisini görüntülemez. .NET Core 3,0 SDK 'dan beri kullanılabilir.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Oluşturulan paketleri belirtilen dizine koyar.

- **`--runtime <RUNTIME_IDENTIFIER>`**

  Paketlerinin geri yükleneceği hedef çalışma zamanını belirtir. Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md).

- **`-s|--serviceable`**

  Paketteki hizmet verebilir bayrağını ayarlar. Daha fazla bilgi için bkz. [.net blogu: .NET 4.5.1, .net NuGet kitaplıkları Için Microsoft güvenlik güncelleştirmelerini destekler](https://aka.ms/nupkgservicing).

- **`--version-suffix <VERSION_SUFFIX>`**

  Projedeki `$(VersionSuffix)` MSBuild özelliğinin değerini tanımlar.

- **`-v|--verbosity <LEVEL>`**

  Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.

## <a name="examples"></a>Örnekler

- Projeyi geçerli dizinde paketleme:

  ```dotnetcli
  dotnet pack
  ```

- `app1` projeyi paketleme:

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj
  ```

- Projeyi geçerli dizinde paketedin ve elde edilen paketleri `nupkgs` klasöre yerleştirin:

  ```dotnetcli
  dotnet pack --output nupkgs
  ```

- Geçerli dizindeki projeyi `nupkgs` klasöre paketlayın ve derleme adımını atlayın:

  ```dotnetcli
  dotnet pack --no-build --output nupkgs
  ```

- Projenin sürüm soneki *. csproj* dosyasında `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` olarak yapılandırıldığında, geçerli projeyi paketleyin ve elde edilen paket sürümünü verilen sonek ile güncelleştirin:

  ```dotnetcli
  dotnet pack --version-suffix "ci-1234"
  ```

- Paket sürümünü `PackageVersion` MSBuild özelliği ile `2.1.0` olarak ayarlayın:

  ```dotnetcli
  dotnet pack -p:PackageVersion=2.1.0
  ```

- Projeyi belirli bir [hedef çerçeve](../../standard/frameworks.md)için paketleme:

  ```dotnetcli
  dotnet pack -p:TargetFrameworks=net45
  ```

- Projeyi paketleme ve geri yükleme işlemi için belirli bir çalışma zamanı (Windows 10) kullanın:

  ```dotnetcli
  dotnet pack --runtime win10-x64
  ```

- Bir [. nuspec dosyası](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec)kullanarak projeyi paketleme:

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj -p:NuspecFile=~/projects/app1/project.nuspec -p:NuspecBasePath=~/projects/app1/nuget
  ```
