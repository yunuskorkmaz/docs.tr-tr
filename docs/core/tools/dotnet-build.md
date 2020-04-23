---
title: dotnet yapı komutu
description: Dotnet build komutu bir proje ve tüm bağımlılıklarını oluşturur.
ms.date: 02/14/2020
ms.openlocfilehash: 1022df059493c7e045f81d4be93dff2fdab77eb1
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102846"
---
# <a name="dotnet-build"></a>dotnet build

**Bu makale şu şekilde dir:** ✔️ .NET Core 2.x SDK ve sonraki sürümler

## <a name="name"></a>Adı

`dotnet build`- Bir proje ve tüm bağımlılıkları oluşturur.

## <a name="synopsis"></a>Özet

```dotnetcli
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [-f|--framework <FRAMEWORK>] [--force] [--interactive] [--no-dependencies]
    [--no-incremental] [--no-restore] [--nologo] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [-v|--verbosity <LEVEL>]
    [--version-suffix <VERSION_SUFFIX>]

dotnet build -h|--help
```

## <a name="description"></a>Açıklama

Komut, `dotnet build` projeyi ve bağımlılıklarını bir dizi ikili ye dönüştürür. İkili dosyalar, projenin kodlarını *.dll* uzantılı Orta Dil (IL) dosyalarında içerir.  Proje türüne ve ayarlarına bağlı olarak, aşağıdakiler gibi başka dosyalar da eklenebilir:

- Proje türü yürütülebilir bir hedefleme .NET Core 3.0 veya daha sonra ise, uygulamayı çalıştırmak için kullanılabilecek bir yürütülebilir.
- *.pdb* uzantılı hata ayıklama için kullanılan simge dosyaları.
- Uygulamanın veya kitaplığın bağımlılıklarını listeleyen bir *.deps.json* dosyası.
- Bir uygulama için paylaşılan çalışma süresini ve sürümünü belirten bir *.runtimeconfig.json* dosyası.
- Projenin bağlı olduğu diğer kitaplıklar (proje referansları veya NuGet paket başvuruları yoluyla).

.NET Core 3.0'dan önceki sürümleri hedefleyen çalıştırılabilir projeler için, NuGet'in kitaplık bağımlılıkları genellikle çıktı klasörüne kopyalanmaz.  Bunlar, çalışma zamanında NuGet global paketler klasöründen çözülür. Bunu göz önünde bulundurarak, ürün `dotnet build` çalıştırmak için başka bir makineye transfer için hazır değildir. Uygulamanın dağıtılabilen bir sürümünü oluşturmak için, uygulamayı yayımlamanız gerekir (örneğin, [dotnet yayımlama](dotnet-publish.md) komutuyla). Daha fazla bilgi için [bkz.](../deploying/index.md)

.NET Core 3.0 ve sonrası hedeflemesi yapılan yürütülebilir projeler için kitaplık bağımlılıkları çıktı klasörüne kopyalanır. Bu, yayımlamaya özgü başka bir mantık yoksa (Web projeleri gibi), yapı çıktısının dağıtılabilir olması gerektiği anlamına gelir.

### <a name="implicit-restore"></a>Örtük geri yükleme

Bina, uygulamanızın bağımlılıklarını listeleyen *project.assets.json* dosyasını gerektirir. Dosya yürütüldüğünde [`dotnet restore`](dotnet-restore.md) oluşturulur. Varlıklar dosyası yerinde olmadan, takım başvuru derlemelerini çözemez ve bu da hatalara neden olabilir.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

### <a name="executable-or-library-output"></a>Çalıştırılabilir veya kitaplık çıktısı

Projenin yürütülüp yürütülemeyeceği proje `<OutputType>` dosyasındaki özellik tarafından belirlenir. Aşağıdaki örnek, yürütülebilir kod üreten bir projeyi gösterir:

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

Kitaplık oluşturmak için, özelliği `<OutputType>` atlaveya değerini `Library`' ye değdirin. Kitaplık için IL DLL giriş noktaları içermez ve yürütülemez.

### <a name="msbuild"></a>MSBuild

`dotnet build`projeyi oluşturmak için MSBuild'i kullanır, böylece hem paralel hem de artımlı yapıyı destekler. Daha fazla bilgi için [Bkz. Artımlı Yapılar.](/visualstudio/msbuild/incremental-builds)

Komut, seçeneklerine ek `dotnet build` olarak, özellikleri ayarlama veya `-p` `-l` logger tanımlama gibi MSBuild seçeneklerini de kabul eder. Bu seçenekler hakkında daha fazla bilgi için [MSBuild Komut Satırı Başvurusu'na](/visualstudio/msbuild/msbuild-command-line-reference)bakın. Veya [dotnet msbuild](dotnet-msbuild.md) komutunu da kullanabilirsiniz.

Koşmak `dotnet build` koşmaya `dotnet msbuild -restore`eşdeğerdir; ancak, çıktının varsayılan ayrıntılılığı farklıdır.

## <a name="arguments"></a>Bağımsız Değişkenler

`PROJECT | SOLUTION`

Oluşturmak için proje veya çözüm dosyası. Bir proje veya çözüm dosyası belirtilmemişse, MSBuild *proj* veya *sln* ile biten ve bu dosyayı kullanan bir dosya uzantısı olan bir dosya için geçerli çalışma dizinini arar.

## <a name="options"></a>Seçenekler

- **`-c|--configuration <CONFIGURATION>`**

  Yapı yapılandırmasını tanımlar. Çoğu proje için `Debug`varsayılan değer, ancak projenizdeki yapı yapılandırma ayarlarını geçersiz kılabilirsiniz.

- **`-f|--framework <FRAMEWORK>`**

  Belirli bir [çerçeve](../../standard/frameworks.md)için derler. Çerçeve [proje dosyasında](csproj.md)tanımlanmalıdır.

- **`--force`**

  Son geri yükleme başarılı olsa bile tüm bağımlılıkları çözüme kavuşturmaya zorlar. Bu bayrağı *belirtmek, project.assets.json* dosyasını silmekle aynıdır.

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`--interactive`**

  Komutun durmasını ve kullanıcı girişi veya eylemini beklemesini sağlar. Örneğin, kimlik doğrulamasını tamamlamak için. .NET Core 3.0 SDK'dan beri mevcuttur.

- **`--no-dependencies`**

  Projeden projeye (P2P) başvurularını yoksa ve yalnızca belirtilen kök projeyi oluşturur.

- **`--no-incremental`**

  Artımlı yapı için yapıyı güvenli olmayan olarak işaretler. Bu bayrak artımlı derlemeyi kapatır ve projenin bağımlılık grafiğini temiz bir yeniden oluşturmaya zorlar.

- **`--no-restore`**

  Yapı sırasında örtük bir geri yükleme yürütmez.

- **`--nologo`**

  Başlangıç bayrağını veya telif hakkı iletisini görüntülemez. .NET Core 3.0 SDK'dan beri mevcuttur.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Yapılı ikililerin yerleştirilen dizin. Belirtilmemişse, varsayılan `./bin/<configuration>/<framework>/`yol .  Birden çok hedef çerçevesi olan `TargetFrameworks` projelerde (özellik üzerinden), bu seçeneği belirttiğinizi de tanımlamanız `--framework` gerekir.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Hedef çalışma süresini belirtir. Runtime Tanımlayıcıları (RID'ler) listesi için RID [kataloğuna](../rid-catalog.md)bakın.

- **`-v|--verbosity <LEVEL>`**

  MSBuild ayrıntılı düzeyini ayarlar. İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve . Varsayılan değer: `minimal`.

- **`--version-suffix <VERSION_SUFFIX>`**

  Projeyi `$(VersionSuffix)` yaparken kullanılacak özelliğin değerini ayarlar. Bu yalnızca `$(Version)` özellik ayarlı değilse çalışır. Daha `$(Version)` sonra, bir `$(VersionPrefix)` çizgi `$(VersionSuffix)`ile ayrılmış ile birleştirilir.

## <a name="examples"></a>Örnekler

- Bir proje ve bağımlılıkları oluşturun:

  ```dotnetcli
  dotnet build
  ```

- Sürüm yapılandırmasını kullanarak bir proje ve bağımlılıkları oluşturun:

  ```dotnetcli
  dotnet build --configuration Release
  ```

- Belirli bir çalışma zamanı için proje ve bağımlılıkları oluşturun (bu örnekte, Ubuntu 18.04):

  ```dotnetcli
  dotnet build --runtime ubuntu.18.04-x64
  ```

- Projeyi oluşturun ve geri yükleme işlemi sırasında belirtilen NuGet paket kaynağını kullanın (.NET Core 2.0 SDK ve sonraki sürümler):

  ```dotnetcli
  dotnet build --source c:\packages\mypackages
  ```

- PROJEYI oluşturun ve `-p` [MSBuild seçeneğini](#msbuild)kullanarak sürüm 1.2.3.4'u yapı parametresi olarak ayarlayın:

  ```dotnetcli
  dotnet build -p:Version=1.2.3.4
  ```
