---
title: DotNet derleme komutu
description: DotNet derleme komutu bir projeyi ve tüm bağımlılıklarını oluşturur.
ms.date: 02/14/2020
ms.openlocfilehash: 6f33b449301f40949ff5dfe4077564344a9de8ec
ms.sourcegitcommit: c8c3e1c63a00b7d27f76f5e50ee6469e6bdc8987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87251172"
---
# <a name="dotnet-build"></a>dotnet build

**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2. x SDK ve sonraki sürümleri

## <a name="name"></a>Ad

`dotnet build`-Bir projeyi ve tüm bağımlılıklarını oluşturur.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [-f|--framework <FRAMEWORK>] [--force] [--interactive] [--no-dependencies]
    [--no-incremental] [--no-restore] [--nologo] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [--source <SOURCE>]
    [-v|--verbosity <LEVEL>] [--version-suffix <VERSION_SUFFIX>]

dotnet build -h|--help
```

## <a name="description"></a>Açıklama

`dotnet build`Komutu projeyi ve onun bağımlılıklarını bir ikili dosya kümesine oluşturur. İkili dosyalar, projenin kodunu *. dll* uzantılı ara DIL (IL) dosyalarına dahil eder.  Proje türü ve ayarlarına bağlı olarak, şu gibi diğer dosyalar dahil edilebilir:

- Proje türü, .NET Core 3,0 veya üstünü hedefleyen bir yürütülebilir dosya ise, uygulamayı çalıştırmak için kullanılabilecek bir çalıştırılabilir dosya.
- Bir *. pdb* uzantısıyla hata ayıklama için kullanılan sembol dosyaları.
- Uygulamanın veya kitaplığın bağımlılıklarını listeleyen bir *.deps.js* dosyası.
- Paylaşılan çalışma zamanını ve bir uygulamanın sürümünü belirten dosya *.runtimeconfig.js* .
- Projenin bağımlı olduğu diğer kitaplıklar (proje başvuruları veya NuGet paket başvuruları aracılığıyla).

.NET Core 3,0 ' den önceki sürümleri hedefleyen yürütülebilir projeler için, NuGet 'deki kitaplık bağımlılıkları genellikle çıkış klasörüne kopyalanmaz.  Bunlar, çalışma zamanında NuGet genel paketler klasöründen çözümlenirler. Göz önünde bulundurularak, ürünü `dotnet build` çalıştırmak için başka bir makineye aktarılmaya hazırlanın. Uygulamasının dağıtılabilecek bir sürümünü oluşturmak için (örneğin, [DotNet Publish](dotnet-publish.md) komutuyla) yayımlamanız gerekir. Daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md).

.NET Core 3,0 ve üstünü hedefleyen yürütülebilir projelerde, kitaplık bağımlılıkları çıkış klasörüne kopyalanır. Bu, başka bir yayınla özel mantık (örneğin, Web projeleri) yoksa, yapı çıkışının dağıtılabilir olması anlamına gelir.

### <a name="implicit-restore"></a>Örtük geri yükleme

Oluşturma, uygulamanızın bağımlılıklarını listeleyen dosyada *project.assets.js* gerektirir. Dosya [`dotnet restore`](dotnet-restore.md) yürütüldüğünde oluşturulur. Varlıklar dosyası olmadan, Araçlar başvuru derlemelerini çözemez, bu da hatalara neden olur.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

### <a name="executable-or-library-output"></a>Yürütülebilir veya kitaplık çıkışı

Projenin yürütülebilir olup olmadığı veya proje dosyasındaki özelliği tarafından belirlenmediği `<OutputType>` . Aşağıdaki örnekte yürütülebilir kod üreten bir proje gösterilmektedir:

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

Bir kitaplık oluşturmak için, özelliği atlayın `<OutputType>` veya değerini olarak değiştirin `Library` . Bir kitaplığın Il DLL 'SI giriş noktaları içermiyor ve yürütülemiyor.

### <a name="msbuild"></a>MSBuild

`dotnet build`, projeyi derlemek için MSBuild kullanır, bu nedenle hem paralel hem de artımlı yapıları destekler. Daha fazla bilgi için bkz. [Artımlı derlemeler](/visualstudio/msbuild/incremental-builds).

Seçeneklerine ek olarak `dotnet build` komut, `-p` özellikleri ayarlama veya bir günlükçü tanımlama gibi MSBuild seçeneklerini kabul eder `-l` . Bu seçenekler hakkında daha fazla bilgi için bkz. [MSBuild komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference). Ayrıca [DotNet MSBuild](dotnet-msbuild.md) komutunu da kullanabilirsiniz.

Çalışıyor, `dotnet build` çalıştırmaya eşdeğerdir `dotnet msbuild -restore` ; ancak, çıktının varsayılan ayrıntı düzeyi farklıdır.

## <a name="arguments"></a>Arguments

`PROJECT | SOLUTION`

Derlenecek proje veya çözüm dosyası. Bir proje veya çözüm dosyası belirtilmemişse, MSBuild, *proj* veya *sln* 'de biten bir dosya uzantısına sahip bir dosya için geçerli çalışma dizinini arar ve bu dosyayı kullanır.

## <a name="options"></a>Seçenekler

- **`-c|--configuration <CONFIGURATION>`**

  Yapı yapılandırmasını tanımlar. Çoğu proje için varsayılandır `Debug` , ancak projenizde derleme yapılandırma ayarlarını geçersiz kılabilirsiniz.

- **`-f|--framework <FRAMEWORK>`**

  Belirli bir [çerçeve](../../standard/frameworks.md)için derlenir. Çerçeve [Proje dosyasında](csproj.md)tanımlanmalıdır.

- **`--force`**

  Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar. Bu bayrağın belirtilmesi, dosyadaki *project.assets.js* silme ile aynıdır.

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`--interactive`**

  Komutun Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir. Örneğin, kimlik doğrulamasını tamamlamaya yönelik. .NET Core 3,0 SDK 'dan beri kullanılabilir.

- **`--no-dependencies`**

  Projeden projeye (P2P) başvurularını yoksayar ve yalnızca belirtilen kök projeyi oluşturur.

- **`--no-incremental`**

  Derlemeyi Artımlı derleme için güvenli değil olarak işaretler. Bu bayrak, artımlı derlemeyi kapatır ve projenin bağımlılık grafiğinin temiz bir yeniden oluşturulmasına zorlar.

- **`--no-restore`**

  Derleme sırasında örtük geri yükleme yürütmez.

- **`--nologo`**

  Başlangıç başlığını veya telif hakkı iletisini görüntülemez. .NET Core 3,0 SDK 'dan beri kullanılabilir.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Oluşturulan ikililerin yerleştirileceği dizin. Belirtilmemişse, varsayılan yol olur `./bin/<configuration>/<framework>/` .  Birden çok hedef çerçevesi olan projeler için ( `TargetFrameworks` özelliği aracılığıyla), `--framework` Bu seçeneği ne zaman belirttiğinizde de tanımlamanız gerekir.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Hedef çalışma zamanını belirtir. Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md).

- **`--source <SOURCE>`**

  Geri yükleme işlemi sırasında kullanılacak NuGet paket kaynağının URI 'SI.

- **`-v|--verbosity <LEVEL>`**

  MSBuild ayrıntı düzeyi düzeyini ayarlar. İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` . Varsayılan değer: `minimal`.

- **`--version-suffix <VERSION_SUFFIX>`**

  `$(VersionSuffix)`Proje oluşturulurken kullanılacak özelliğin değerini ayarlar. Bu yalnızca `$(Version)` özellik ayarlanmamışsa işe yarar. Daha sonra, `$(Version)` `$(VersionPrefix)` ile birleştirilmiş olarak ayarlanır `$(VersionSuffix)` , tireyle ayrılır.

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

- `-p` [MSBuild seçeneğini](#msbuild)kullanarak projeyi derleyin ve derleme parametresi olarak 1.2.3.4 olarak ayarlayın:

  ```dotnetcli
  dotnet build -p:Version=1.2.3.4
  ```
