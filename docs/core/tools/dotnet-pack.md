---
title: dotnet paketi komutu
description: Dotnet paketi komutu,.NET Core projeniz için NuGet paketleri oluşturur.
ms.date: 02/14/2020
ms.openlocfilehash: 2df096a088a177b77256b5d717f31e185507b249
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102820"
---
# <a name="dotnet-pack"></a>dotnet pack

**Bu makale şu şekilde dir:** ✔️ .NET Core 2.x SDK ve sonraki sürümler

## <a name="name"></a>Adı

`dotnet pack`- Kodu NuGet paketine paketler.

## <a name="synopsis"></a>Özet

```dotnetcli
dotnet pack [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [--force] [--include-source] [--include-symbols] [--interactive]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo]
    [-o|--output <OUTPUT_DIRECTORY>] [--runtime <RUNTIME_IDENTIFIER>]
    [-s|--serviceable] [-v|--verbosity <LEVEL>]
    [--version-suffix <VERSION_SUFFIX>]

dotnet pack -h|--help
```

## <a name="description"></a>Açıklama

Komut `dotnet pack` projeyi oluşturur ve NuGet paketleri oluşturur. Bu komutun sonucu bir NuGet paketidir *(yani.nupkg* dosyası).

Hata ayıklama sembollerini içeren bir paket oluşturmak istiyorsanız, iki seçeneğiniz vardır:

- `--include-symbols`- semboller paketini oluşturur.
- `--include-source`- kaynak dosyaları içeren bir `src` klasör ile semboller paketi oluşturur.

Paketlenmiş projenin NuGet bağımlılıkları *.nuspec* dosyasına eklenir, böylece paket yüklendiğinde düzgün bir şekilde çözülürler. Projeden projeye başvurular proje içinde paketlenmemiştir. Şu anda, projeden projeye bağımlılıklarınız varsa, proje başına bir paketiniz olmalıdır.

Varsayılan olarak, `dotnet pack` önce projeyi oluşturur. Bu davranıştan kaçınmak istiyorsanız, `--no-build` seçeneği geçirin. Bu seçenek genellikle, kodun daha önce üretildiği senaryoları sürekli tümleştirme (CI) oluşturmada yararlıdır.

> [!NOTE]
> Bazı durumlarda, örtülü yapı gerçekleştirilemez. Bu, yapı `GeneratePackageOnBuild` ve paket hedefleri arasında döngüsel bağımlılıktan kaçınmak için ayarlandığında oluşabilir. Kilitli bir dosya veya başka bir sorun varsa yapı da başarısız olabilir.

Paketleme işlemi için `dotnet pack` komuta MSBuild özellikleri sağlayabilirsiniz. Daha fazla bilgi için [NuGet meta veri özellikleri](csproj.md#nuget-metadata-properties) ve [MSBuild Komut Satırı Başvurusu'na](/visualstudio/msbuild/msbuild-command-line-reference)bakın. [Örnekler](#examples) bölümünde, birkaç farklı senaryo için MSBuild -p anahtarının nasıl kullanılacağı gösterilmektedir.

Web projeleri varsayılan olarak paketlenebilir değildir. Varsayılan davranışı geçersiz kılmak için *.csproj* dosyanıza aşağıdaki özelliği ekleyin:

```xml
<PropertyGroup>
   <IsPackable>true</IsPackable>
</PropertyGroup>
```

### <a name="implicit-restore"></a>Örtük geri yükleme

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a>Bağımsız Değişkenler

`PROJECT | SOLUTION`

  Proje veya çözüm paketi. Ya bir [csproj dosyasına,](csproj.md)bir çözüm dosyasına veya bir dizine giden bir yoldur. Belirtilmemişse, komut bir proje veya çözüm dosyası için geçerli dizini arar.

## <a name="options"></a>Seçenekler

- **`-c|--configuration <CONFIGURATION>`**

  Yapı yapılandırmasını tanımlar. Çoğu proje için `Debug`varsayılan değer, ancak projenizdeki yapı yapılandırma ayarlarını geçersiz kılabilirsiniz.

- **`--force`**

  Son geri yükleme başarılı olsa bile tüm bağımlılıkları çözüme kavuşturmaya zorlar. Bu bayrağı *belirtmek, project.assets.json* dosyasını silmekle aynıdır.

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`--include-source`**

  Çıkış dizinindeki normal NuGet paketlerine ek olarak hata ayıklama sembollerini NuGet paketlerini içerir. Kaynak dosyaları semboller paketinin `src` içindeki klasöre dahildir.

- **`--include-symbols`**

  Çıkış dizinindeki normal NuGet paketlerine ek olarak hata ayıklama sembollerini NuGet paketlerini içerir.

- **`--interactive`**

  Komutun durmasına ve kullanıcı girişinin veya eylemini beklemesine (örneğin, kimlik doğrulamasını tamamlamak için) izin verir. .NET Core 3.0 SDK'dan beri mevcuttur.

- **`--no-build`**

  Paketlemeden önce projeyi inşa etmez. Ayrıca bayrağı da `--no-restore` örtülü olarak ayarlar.

- **`--no-dependencies`**

  Projeden projeye başvuruları yoksa ve yalnızca kök projeyi geri yükler.

- **`--no-restore`**

  Komutu çalıştırırken örtük bir geri yükleme yürütmez.

- **`--nologo`**

  Başlangıç bayrağını veya telif hakkı iletisini görüntülemez. .NET Core 3.0 SDK'dan beri mevcuttur.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Yapılı paketleri belirtilen dizine yerleştirir.

- **`--runtime <RUNTIME_IDENTIFIER>`**

  Paketleri geri yüklemek için hedef çalışma süresini belirtir. Runtime Tanımlayıcıları (RID'ler) listesi için RID [kataloğuna](../rid-catalog.md)bakın.

- **`-s|--serviceable`**

  Paketteki servis edilebilir bayrağı ayarlar. Daha fazla bilgi için [.NET Blog: .NET 4.5.1 .NET NuGet Kitaplıkları için Microsoft Güvenlik Güncelleştirmelerini Destekler.](https://aka.ms/nupkgservicing)

- **`--version-suffix <VERSION_SUFFIX>`**

  Projedeki MSBuild `$(VersionSuffix)` özelliğinin değerini tanımlar.

- **`-v|--verbosity <LEVEL>`**

  Komutun ayrıntılı düzeyini ayarlar. İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve .

## <a name="examples"></a>Örnekler

- Projeyi geçerli dizinde paketle:

  ```dotnetcli
  dotnet pack
  ```

- Projeyi `app1` paketle:

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj
  ```

- Projeyi geçerli dizine yerleştirin ve ortaya çıkan `nupkgs` paketleri klasöre yerleştirin:

  ```dotnetcli
  dotnet pack --output nupkgs
  ```

- Projeyi geçerli dizindeki `nupkgs` klasöre paketleyin ve yapı adımını atlayın:

  ```dotnetcli
  dotnet pack --no-build --output nupkgs
  ```

- *.csproj* dosyasında olduğu gibi `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` yapılandırılan projenin sürümüyle, geçerli projeyi paketleyin ve elde edilen paket sürümünü verilen sonekle güncelleyin:

  ```dotnetcli
  dotnet pack --version-suffix "ci-1234"
  ```

- Paket sürümünü MSBuild `2.1.0` `PackageVersion` özelliğine göre ayarlayın:

  ```dotnetcli
  dotnet pack -p:PackageVersion=2.1.0
  ```

- Belirli bir hedef [çerçevesi](../../standard/frameworks.md)için proje paketi:

  ```dotnetcli
  dotnet pack -p:TargetFrameworks=net45
  ```

- Projeyi paketleyin ve geri yükleme işlemi için belirli bir çalışma süresi (Windows 10) kullanın:

  ```dotnetcli
  dotnet pack --runtime win10-x64
  ```

- [.nuspec dosyasını](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec)kullanarak projeyi paketle:

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj -p:NuspecFile=~/projects/app1/project.nuspec -p:NuspecBasePath=~/projects/app1/nuget
  ```
