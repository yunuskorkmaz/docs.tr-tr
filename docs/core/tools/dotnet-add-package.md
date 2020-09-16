---
title: DotNet paket Ekle komutu
description: "' DotNet Add Package ' komutu, bir projeye NuGet paket başvurusu eklemek için uygun bir seçenek sağlar."
ms.date: 02/14/2020
ms.openlocfilehash: 1bdda241c1301b926ba2fd322f969407038b7b62
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538074"
---
# <a name="dotnet-add-package"></a>dotnet add package

**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2. x SDK ve sonraki sürümleri

## <a name="name"></a>Name

`dotnet add package` -Proje dosyasına bir paket başvurusu ekler.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet add [<PROJECT>] package <PACKAGE_NAME>
    [-f|--framework <FRAMEWORK>] [--interactive]
    [-n|--no-restore] [--package-directory <PACKAGE_DIRECTORY>]
    [-s|--source <SOURCE>] [-v|--version <VERSION>]

dotnet add package -h|--help
```

## <a name="description"></a>Description

`dotnet add package`Komut, bir proje dosyasına paket başvurusu eklemek için uygun bir seçenek sağlar. Komutu çalıştırdıktan sonra, paketin projedeki çerçeveler ile uyumlu olduğundan emin olmak için bir uyumluluk denetimi vardır. Denetim başarılı olursa, `<PackageReference>` proje dosyasına bir öğe eklenir ve [DotNet restore](dotnet-restore.md) çalıştırılır.

Örneğin, `Newtonsoft.Json` *Todo. csproj* öğesine eklemek aşağıdaki örneğe benzer bir çıktı üretir:

```console
Writing C:\Users\me\AppData\Local\Temp\tmp95A8.tmp
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

*Todo. csproj* dosyası artık [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) başvurulan paket için bir öğe içeriyor.

```xml
<PackageReference Include="Newtonsoft.Json" Version="12.0.1" />
```

### <a name="implicit-restore"></a>Örtük geri yükleme

[!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

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

  Paketlerin geri yükleneceği dizin. Varsayılan paket geri yükleme konumu `%userprofile%\.nuget\packages` Windows ve `~/.nuget/packages` MacOS ve Linux üzerinde bulunur. Daha fazla bilgi için bkz. [NuGet 'de Genel paketleri, önbelleği ve temp klasörlerini yönetme](/nuget/consume-packages/managing-the-global-packages-and-cache-folders).

- **`-s|--source <SOURCE>`**

  Geri yükleme işlemi sırasında kullanılacak NuGet paket kaynağının URI 'SI.

- **`-v|--version <VERSION>`**

  Paketin sürümü. Bkz. [NuGet paketi sürümü oluşturma](/nuget/reference/package-versioning).

## <a name="examples"></a>Örnekler

- `Newtonsoft.Json`Bir projeye NuGet paketi Ekle:

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

- [NuGet 'de Genel paketleri, önbelleği ve temp klasörlerini yönetme](/nuget/consume-packages/managing-the-global-packages-and-cache-folders)
- [NuGet paketi sürümü oluşturma](/nuget/reference/package-versioning)
