---
title: DotNet paketi command - .NET Core CLI Ekle
description: "'Dotnet, paket Ekle' komutunu bir projeye bir NuGet paketi başvuru eklemek için uygun bir seçenek sağlar."
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 31dda9dbb101238b3a33d8b0d9a17765744480e0
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/25/2018
ms.locfileid: "39244399"
---
# <a name="dotnet-add-package"></a>DotNet paketi ekleme

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet add package` -Bir proje dosyası için bir paket başvurusu ekler.

## <a name="synopsis"></a>Özeti

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-h|--help] [-f|--framework] [-n|--no-restore] [--package-directory] [-s|--source] [-v|--version]`

## <a name="description"></a>Açıklama

`dotnet add package` Komutu bir proje dosyası için bir paket başvurusu eklemek için uygun bir seçenek sağlar. Komutu çalıştırdıktan sonra paket projedeki çerçevelerle uyumlu olduğundan emin olmak için bir uyumluluk denetimi yoktur. Onay başarılı olursa bir `<PackageReference>` öğesi, proje dosyasına eklenir ve [dotnet restore](dotnet-restore.md) çalıştırılır.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Örneğin, ekleme `Newtonsoft.Json` için *ToDo.csproj* aşağıdaki örneğe benzer bir çıktı üretir:

```console
  Writing C:\Users\mairaw\AppData\Local\Temp\tmp95A8.tmp
info : Adding PackageReference for package 'Newtonsoft.Json' into project 'C:\projects\ToDo\ToDo.csproj'.
log  : Restoring packages for C:\projects\ToDo\ToDo.csproj...
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json 235ms
info : Package 'Newtonsoft.Json' is compatible with all the specified frameworks in project 'C:\projects\ToDo\ToDo.csproj'.
info : PackageReference for package 'Newtonsoft.Json' version '10.0.3' added to file 'C:\projects\ToDo\ToDo.csproj'.
```

*ToDo.csproj* artık dosya içeren bir [ `<PackageReference>` ](/nuget/consume-packages/package-references-in-project-files) başvurulan paketi için öğesi.

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```

## <a name="arguments"></a>Arguments

`PROJECT`

Proje dosyasını belirtir. Belirtilmezse, komut için geçerli dizinde arar.

`PACKAGE_NAME`

Eklenecek paket başvurusu.

## <a name="options"></a>Seçenekler

`-h|--help`

Komut için kısa bir Yardım yazdırır.

`-f|--framework <FRAMEWORK>`

Yalnızca belirli bir hedeflenirken paket başvurusu ekler [framework](../../standard/frameworks.md).

`-n|--no-restore`

Geri yükleme Önizleme ve uyumluluk denetimi gerçekleştirmeden bir paket başvurusu ekler.

`--package-directory <PACKAGE_DIRECTORY>`

Pakette belirtilen dizine geri yükler.

`-s|--source <SOURCE>`

Geri yükleme işlemi sırasında belirli bir NuGet paket kaynağı kullanır.

`-v|--version <VERSION>`

Paket sürümü.

## <a name="examples"></a>Örnekler

Ekleme `Newtonsoft.Json` NuGet paketini projeye:

`dotnet add package Newtonsoft.Json`

Bir paketin belirli bir sürümünü bir projeye ekleyin:

`dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0`

Belirli bir NuGet kaynağını kullanarak paket ekleyin:

`dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json`
