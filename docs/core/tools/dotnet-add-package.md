---
title: dotnet ekle paket komutu
description: "'dotnet paketi ekle' komutu, projeye NuGet paketi başvurusu eklemek için kullanışlı bir seçenek sunar."
ms.date: 02/14/2020
ms.openlocfilehash: 1d57aed59ccd45417c88f9b6a2f9dd768fda9b58
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102859"
---
# <a name="dotnet-add-package"></a>dotnet add package

**Bu makale şu şekilde dir:** ✔️ .NET Core 2.x SDK ve sonraki sürümler

## <a name="name"></a>Adı

`dotnet add package`- Proje dosyasına paket başvurusu ekler.

## <a name="synopsis"></a>Özet

```dotnetcli
dotnet add [<PROJECT>] package <PACKAGE_NAME>
    [-f|--framework <FRAMEWORK>] [--interactive]
    [-n|--no-restore] [--package-directory <PACKAGE_DIRECTORY>]
    [-s|--source <SOURCE>] [-v|--version <VERSION>]

dotnet add package -h|--help
```

## <a name="description"></a>Açıklama

Komut, `dotnet add package` proje dosyasına paket başvurusu eklemek için kullanışlı bir seçenek sağlar. Komutu çalıştırdıktan sonra, paketin projedeki çerçevelerle uyumlu olduğundan emin olmak için bir uyumluluk denetimi vardır. Denetim geçerse, proje `<PackageReference>` dosyasına bir öğe eklenir ve [dotnet geri yükleme](dotnet-restore.md) çalıştırılır.

Örneğin, `Newtonsoft.Json` *ToDo.csproj'a* ekleme aşağıdaki örneğe benzer çıktı üretir:

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

*ToDo.csproj* dosyası artık [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) başvurulan paket için bir öğe içerir.

```xml
<PackageReference Include="Newtonsoft.Json" Version="12.0.1" />
```

### <a name="implicit-restore"></a>Örtük geri yükleme

[!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

## <a name="arguments"></a>Bağımsız Değişkenler

- **`PROJECT`**

  Proje dosyasını belirtir. Belirtilmemişse, komut geçerli dizini arar.

- **`PACKAGE_NAME`**

  Eklenecek paket başvurusu.

## <a name="options"></a>Seçenekler

- **`-f|--framework <FRAMEWORK>`**

  Yalnızca belirli bir [çerçeveyi](../../standard/frameworks.md)hedefalırken paket başvurusu ekler.

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`--interactive`**

  Komutun durmasına ve kullanıcı girişinin veya eylemini beklemesine (örneğin, kimlik doğrulamasını tamamlamak için) izin verir. .NET Core 2.1 SDK, sürüm 2.1.400 veya daha sonra kullanılabilir.

- **`-n|--no-restore`**

  Geri yükleme önizleme ve uyumluluk denetimi gerçekleştirmeden bir paket başvurusu ekler.

- **`--package-directory <PACKAGE_DIRECTORY>`**

  Paketleri geri yüklemek için dizin. Varsayılan paket geri `%userprofile%\.nuget\packages` yükleme konumu `~/.nuget/packages` Windows'ta, macOS ve Linux'tadır. Daha fazla bilgi için bkz. [NuGet'deki genel paketleri, önbellekleri ve geçici klasörleri yönetme.](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders)

- **`-s|--source <SOURCE>`**

  Geri yükleme işlemi sırasında kullanılacak NuGet paket kaynağı.

- **`-v|--version <VERSION>`**

  Paketin sürümü. Bkz. [NuGet paket sürümü.](https://docs.microsoft.com/nuget/reference/package-versioning)

## <a name="examples"></a>Örnekler

- Projeye `Newtonsoft.Json` NuGet paketi ekleyin:

  ```dotnetcli
  dotnet add package Newtonsoft.Json
  ```

- Projeye paketin belirli bir sürümünü ekleyin:

  ```dotnetcli
  dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0
  ```

- Belirli bir NuGet kaynağını kullanarak paket ekleyin:

  ```dotnetcli
  dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json
  ```

## <a name="see-also"></a>Ayrıca bkz.

- [NuGet'de genel paketleri, önbelleği ve geçici klasörleri yönetme](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders)
- [NuGet paketi sürümü](https://docs.microsoft.com/nuget/reference/package-versioning)
