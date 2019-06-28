---
title: DotNet paketi komut ekleme
description: "'Dotnet, paket Ekle' komutunu bir projeye bir NuGet paketi başvuru eklemek için uygun bir seçenek sağlar."
ms.date: 06/26/2019
ms.openlocfilehash: f387d32cbf706e1711439e393c1a7811bc8f47bd
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67422057"
---
# <a name="dotnet-add-package"></a>dotnet add package

**Bu makale için geçerlidir: ✓** .NET Core SDK'sı 1.x ve sonraki sürümler

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Ad

`dotnet add package` -Bir proje dosyası için bir paket başvurusu ekler.

## <a name="synopsis"></a>Synopsis

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-h|--help] [-f|--framework] [--interactive] [-n|--no-restore] [--package-directory] [-s|--source] [-v|--version]`

## <a name="description"></a>Açıklama

`dotnet add package` Komutu bir proje dosyası için bir paket başvurusu eklemek için uygun bir seçenek sağlar. Komutu çalıştırdıktan sonra paket projedeki çerçevelerle uyumlu olduğundan emin olmak için bir uyumluluk denetimi yoktur. Onay başarılı olursa bir `<PackageReference>` öğesi, proje dosyasına eklenir ve [dotnet restore](dotnet-restore.md) çalıştırılır.

[!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

Örneğin, ekleme `Newtonsoft.Json` için *ToDo.csproj* aşağıdaki örneğe benzer bir çıktı üretir:

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

*ToDo.csproj* artık dosya içeren bir [ `<PackageReference>` ](/nuget/consume-packages/package-references-in-project-files) başvurulan paketi için öğesi.

```xml
<PackageReference Include="Newtonsoft.Json" Version="12.0.1" />
```

## <a name="arguments"></a>Arguments

* **`PROJECT`**

  Proje dosyasını belirtir. Belirtilmezse, komut için geçerli dizinde arar.

* **`PACKAGE_NAME`**

  Eklenecek paket başvurusu.

## <a name="options"></a>Seçenekler

* **`-f|--framework <FRAMEWORK>`**

  Yalnızca belirli bir hedeflenirken paket başvurusu ekler [framework](../../standard/frameworks.md).

* **`-h|--help`**

  Komut için kısa bir Yardım yazdırır.

* **`--interactive`**

  Durdurmak ve kullanıcı girişi veya eylem (örneğin, kimlik doğrulamasını tamamlamak için) için beklemek için komutu sağlar. .NET Core 2.1 SDK, sürüm 2.1.400 sürümünden itibaren kullanılabilir veya üzeri.

* **`-n|--no-restore`**

  Geri yükleme Önizleme ve uyumluluk denetimi gerçekleştirmeden bir paket başvurusu ekler.

* **`--package-directory <PACKAGE_DIRECTORY>`**

  Dizin paketleri geri yükleneceği yeri. Varsayılan paket geri yükleme konumu `%userprofile%\.nuget\packages` Windows üzerinde ve `~/.nuget/packages` macOS ve Linux'ta. Daha fazla bilgi için [genel paketleri, önbellek ve NuGet geçici klasörlere yönetme](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders).

* **`-s|--source <SOURCE>`**

  Geri yükleme işlemi sırasında kullanmak için NuGet paket kaynağı.

* **`-v|--version <VERSION>`**

  Paket sürümü. Bkz: [NuGet Paket sürümü oluşturma](https://docs.microsoft.com/nuget/reference/package-versioning).

## <a name="examples"></a>Örnekler

* Ekleme `Newtonsoft.Json` NuGet paketini projeye:

  ```console
  dotnet add package Newtonsoft.Json
  ```

* Bir paketin belirli bir sürümünü bir projeye ekleyin:

  ```console
  dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0
  ```

* Belirli bir NuGet kaynağını kullanarak paket ekleyin:

  ```console
  dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json
  ```

## <a name="see-also"></a>Ayrıca bkz.

- [Genel paketleri, önbellek ve NuGet geçici klasörlere yönetme](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders)
- [NuGet Paket sürümü oluşturma](https://docs.microsoft.com/nuget/reference/package-versioning)