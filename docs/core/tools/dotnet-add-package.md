---
title: DotNet paket Ekle komutu
description: "' DotNet Add Package ' komutu, bir projeye NuGet paket başvurusu eklemek için uygun bir seçenek sağlar."
ms.date: 06/26/2019
ms.openlocfilehash: 210dcf0efe06672264ebfa297589bdb387591a42
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733322"
---
# <a name="dotnet-add-package"></a>dotnet add package

**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 1. x SDK ve sonraki sürümleri

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Ad

`dotnet add package`-proje dosyasına bir paket başvurusu ekler.

## <a name="synopsis"></a>Özeti

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-h|--help] [-f|--framework] [--interactive] [-n|--no-restore] [--package-directory] [-s|--source] [-v|--version]`

## <a name="description"></a>Açıklama

`dotnet add package` komutu bir proje dosyasına paket başvurusu eklemek için uygun bir seçenek sağlar. Komutu çalıştırdıktan sonra, paketin projedeki çerçeveler ile uyumlu olduğundan emin olmak için bir uyumluluk denetimi vardır. Denetim başarılı olursa, proje dosyasına bir `<PackageReference>` öğesi eklenir ve [DotNet restore](dotnet-restore.md) çalıştırılır.

[!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

Örneğin, *Todo. csproj* öğesine `Newtonsoft.Json` eklemek, aşağıdaki örneğe benzer bir çıktı üretir:

```console
  Writing C:\Users\mairaw\AppData\Local\Temp\tmp95A8.tmp
info : Adding PackageReference for package 'Newtonsoft.Json' into project 'C:\projects\ToDo\ToDo.csproj'.
log  : Restoring packages for C:\Temp\projects\consoleproj\consoleproj.csproj...
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json 79ms
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/12.0.1/newtonsoft.json.12.0.1.nupkg
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/12.0.1/newtonsoft.json.12.0.1.nupkg 232ms
log  : Installing Newtonsoft.Json 12.0.1.
info : Package 'Newtonsoft.Json' is compatible with all the specified frameworks in project 'C:\projects\ToDo\ToDo.csproj'.
info : PackageReference for package 'Newtonsoft.Json' version '12.0.1' added to file 'C:\projects\ToDo\ToDo.csproj'.
```

*Todo. csproj* dosyası artık başvurulan paket için bir [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) öğesi içeriyor.

```xml
<PackageReference Include="Newtonsoft.Json" Version="12.0.1" />
```

## <a name="arguments"></a>Arguments

- **`PROJECT`**

  Proje dosyasını belirtir. Belirtilmemişse, komut geçerli dizinde bir arama yapar.

- **`PACKAGE_NAME`**

  Eklenecek paket başvurusu.

## <a name="options"></a>Seçenekler

- **`-f|--framework <FRAMEWORK>`**

  Yalnızca belirli bir [çerçeveyi](../../standard/frameworks.md)hedeflerken bir paket başvurusu ekler.

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`--interactive`**

  Komutun, Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir (örneğin, kimlik doğrulamasını tamamlamaya yönelik). .NET Core 2,1 SDK, sürüm 2.1.400 veya sonrası ile kullanılabilir.

- **`-n|--no-restore`**

  Geri yükleme önizlemesi ve uyumluluk denetimi yapılmadan bir paket başvurusu ekler.

- **`--package-directory <PACKAGE_DIRECTORY>`**

  Paketlerin geri yükleneceği dizin. Varsayılan paket geri yükleme konumu Windows üzerinde `%userprofile%\.nuget\packages` ve macOS ve Linux üzerinde `~/.nuget/packages`. Daha fazla bilgi için bkz. [NuGet 'de Genel paketleri, önbelleği ve temp klasörlerini yönetme](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders).

- **`-s|--source <SOURCE>`**

  Geri yükleme işlemi sırasında kullanılacak NuGet paketi kaynağı.

- **`-v|--version <VERSION>`**

  Paketin sürümü. Bkz. [NuGet paketi sürümü oluşturma](https://docs.microsoft.com/nuget/reference/package-versioning).

## <a name="examples"></a>Örnekler

- Bir projeye `Newtonsoft.Json` NuGet paketi Ekle:

  ```dotnetcli
  dotnet add package Newtonsoft.Json
  ```

- Bir projeye paketin belirli bir sürümünü ekleyin:

  ```dotnetcli
  dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0
  ```

- Belirli bir NuGet kaynağını kullanarak bir paket ekleyin:

  ```dotnetcli
  dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json
  ```

## <a name="see-also"></a>Ayrıca bkz.

- [NuGet 'de Genel paketleri, önbelleği ve temp klasörlerini yönetme](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders)
- [NuGet paketi sürümü oluşturma](https://docs.microsoft.com/nuget/reference/package-versioning)
