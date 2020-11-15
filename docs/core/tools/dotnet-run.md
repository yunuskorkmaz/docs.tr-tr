---
title: DotNet Run komutu
description: DotNet Run komutu, uygulamanızı kaynak koddan çalıştırmak için uygun bir seçenek sağlar.
ms.date: 02/19/2020
ms.openlocfilehash: c80f290c75e3bac65ae73fe8edada53db4ce86f8
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634422"
---
# <a name="dotnet-run"></a>dotnet run

**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2. x SDK ve sonraki sürümleri

## <a name="name"></a>Name

`dotnet run` -Açık derleme veya başlatma komutları olmadan kaynak kodu çalıştırır.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet run [-c|--configuration <CONFIGURATION>] [-f|--framework <FRAMEWORK>]
    [--force] [--interactive] [--launch-profile <NAME>] [--no-build]
    [--no-dependencies] [--no-launch-profile] [--no-restore]
    [-p|--project <PATH>] [-r|--runtime <RUNTIME_IDENTIFIER>]
    [-v|--verbosity <LEVEL>] [[--] [application arguments]]

dotnet run -h|--help
```

## <a name="description"></a>Açıklama

`dotnet run`Komut, uygulamanızı kaynak koddan tek bir komutla çalıştırmak için uygun bir seçenek sunar. Komut satırından hızlı yinelemeli geliştirme için faydalıdır. Komut, [`dotnet build`](dotnet-build.md) kodu oluşturmak için komutuna bağımlıdır. Projenin önce geri yüklenmesi gerektiği gibi, derleme için tüm gereksinimler, için `dotnet run` de geçerlidir.

Çıktı dosyaları varsayılan konuma yazılır, yani `bin/<configuration>/<target>` . Örneğin `netcoreapp2.1` , bir uygulamanız varsa ve çalıştırırsanız çıkış ' a `dotnet run` yerleştirilir `bin/Debug/netcoreapp2.1` . Dosyalar gerektiği gibi üzerine yazılır. Geçici dosyalar `obj` dizine yerleştirilir.

Proje birden çok çerçeve belirtiyorsa, `dotnet run` `-f|--framework <FRAMEWORK>` çerçeveyi belirtmek için seçeneği kullanılmadığı müddetçe sonuçları bir hata halinde yürütüyordur.

`dotnet run`Komut, oluşturulan derlemeler değil, proje bağlamında kullanılır. Bunun yerine Framework 'e bağımlı bir uygulama DLL 'sini çalıştırmaya çalışıyorsanız, bir komut olmadan [DotNet](dotnet.md) kullanmanız gerekir. Örneğin, çalıştırmak için `myapp.dll` şunu kullanın:

```dotnetcli
dotnet myapp.dll
```

Sürücü hakkında daha fazla bilgi için `dotnet` bkz. [.NET komut satırı araçları (CLI)](index.md) konusu.

Uygulamayı çalıştırmak için `dotnet run` komut, paylaşılan çalışma zamanının dışındaki uygulamanın tüm bağımlılıklarını NuGet önbelleğinden çözer. Önbelleğe alınmış bağımlılıkları kullandığından, `dotnet run` Üretim ortamında uygulamaları çalıştırmak için kullanılması önerilmez. Bunun yerine, komutunu kullanarak [bir dağıtım oluşturun](../deploying/index.md) [`dotnet publish`](dotnet-publish.md) ve yayımlanan çıktıyı dağıtın.

### <a name="implicit-restore"></a>Örtük geri yükleme

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a>Seçenekler

- **`--`**

  `dotnet run`Çalıştırılmakta olan uygulama için bağımsız değişkenlerin bağımsız değişkenlerini sınırlandırın. Bu sınırlayıcıdan sonraki tüm bağımsız değişkenler uygulama çalıştırmasına geçirilir.

- **`-c|--configuration <CONFIGURATION>`**

  Yapı yapılandırmasını tanımlar. Çoğu proje için varsayılandır `Debug` , ancak projenizde derleme yapılandırma ayarlarını geçersiz kılabilirsiniz.

- **`-f|--framework <FRAMEWORK>`**

  Belirtilen [Framework 'ü](../../standard/frameworks.md)kullanarak uygulamayı oluşturur ve çalıştırır. Çerçeve proje dosyasında belirtilmelidir.

- **`--force`**

  Son geri yükleme başarılı olsa bile tüm bağımlılıkların çözülmesini zorlar. Bu bayrağın belirtilmesi, dosyadaki *project.assets.js* silme ile aynıdır.

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`--interactive`**

  Komutun, Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir (örneğin, kimlik doğrulamasını tamamlamaya yönelik). .NET Core 3,0 SDK 'dan beri kullanılabilir.

- **`--launch-profile <NAME>`**

  Uygulamayı başlatırken kullanılacak başlatma profilinin adı (varsa). Başlatma profilleri dosyasında *launchSettings.js* tanımlanmıştır ve genellikle `Development` , ve olarak adlandırılır `Staging` `Production` . Daha fazla bilgi için bkz. [birden çok ortamla çalışma](/aspnet/core/fundamentals/environments).

- **`--no-build`**

  Çalıştırmadan önce projeyi oluşturmaz. Bayrak de örtülü olarak ayarlanır `--no-restore` .

- **`--no-dependencies`**

  Projeden projeye (P2P) başvuruları olan bir projeyi geri yüklerken, başvuruları değil kök projeyi geri yükler.

- **`--no-launch-profile`**

  , Uygulamayı yapılandırmak için *üzerindelaunchSettings.js* kullanmaya çalışmayın.

- **`--no-restore`**

  Komutu çalıştırılırken örtük geri yükleme yürütülmez.

- **`-p|--project <PATH>`**

  Çalıştırılacak proje dosyasının yolunu belirtir (klasör adı veya tam yol). Belirtilmezse, varsayılan olarak geçerli dizini alır.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Paketlerinin geri yükleneceği hedef çalışma zamanını belirtir. Çalışma zamanı tanımlayıcıları (RID 'Ler) listesi için bkz. [RID kataloğu](../rid-catalog.md). `-r` .NET Core 3,0 SDK 'dan bu yana sunulan kısa seçenek.

- **`-v|--verbosity <LEVEL>`**

  Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` . `m` varsayılan değerdir. .NET Core 2,1 SDK 'dan beri kullanılabilir.

## <a name="examples"></a>Örnekler

- Projeyi geçerli dizinde Çalıştır:

  ```dotnetcli
  dotnet run
  ```

- Belirtilen projeyi Çalıştır:

  ```dotnetcli
  dotnet run --project ./projects/proj1/proj1.csproj
  ```

- Projeyi geçerli dizinde çalıştırın ( `--help` boş seçenek kullanıldığından bu örnekteki bağımsız değişken uygulamaya geçirilir `--` ):

  ```dotnetcli
  dotnet run --configuration Release -- --help
  ```

- Geçerli dizindeki proje için bağımlılıkları ve araçları geri yükleme yalnızca minimum çıktıyı gösterir ve ardından projeyi çalıştırır:

  ```dotnetcli
  dotnet run --verbosity m
  ```
