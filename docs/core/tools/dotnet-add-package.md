---
title: DotNet Paketi komutu - .NET Core CLI ekleme
description: "'Dotnet add paket' komutunu bir NuGet paketi başvuru bir proje eklemek için uygun bir seçenek sağlar."
author: mairaw
ms.author: mairaw
ms.date: 08/11/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 3a8752ff83e069d21ebbda346efef34b17360e3b
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-add-package"></a>DotNet paket ekleme

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet add package` -Bir proje dosyası için bir paket başvuru ekler.

## <a name="synopsis"></a>Özet

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-h|--help] [-v|--version] [-f|--framework] [-n|--no-restore] [-s|--source] [--package-directory]`

## <a name="description"></a>Açıklama

`dotnet add package` Komutu bir proje dosyası paketi başvuru eklemek için uygun bir seçenek sağlar. Komutu çalıştırdıktan sonra paketi projesinde çerçeveleri ile uyumlu olduğundan emin olmak için bir uyumluluk denetimi yoktur. Onay başarılı olursa, bir `<PackageReference>` öğesi proje dosyasına eklenir ve [dotnet geri yükleme](dotnet-restore.md) çalıştırılır.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Örneğin, ekleme `Newtonsoft.Json` için *ToDo.csproj* aşağıdaki örneğe benzer bir çıktı üretir:

```
  Writing C:\Users\mairaw\AppData\Local\Temp\tmp95A8.tmp
info : Adding PackageReference for package 'Newtonsoft.Json' into project 'C:\projects\ToDo\ToDo.csproj'.
log  : Restoring packages for C:\projects\ToDo\ToDo.csproj...
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json 235ms
info : Package 'Newtonsoft.Json' is compatible with all the specified frameworks in project 'C:\projects\ToDo\ToDo.csproj'.
info : PackageReference for package 'Newtonsoft.Json' version '10.0.3' added to file 'C:\projects\ToDo\ToDo.csproj'.
```

*ToDo.csproj* dosyayı şimdi içeren bir [ `<PackageReference>` ](/nuget/consume-packages/package-references-in-project-files) başvurulan paketi öğesi.

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```

## <a name="arguments"></a>Arguments

`PROJECT`

Proje dosyası belirtir. Belirtilmezse, komut için geçerli dizin arar.

`PACKAGE_NAME`

Eklenecek paket başvuru.

## <a name="options"></a>Seçenekler

`-h|--help`

Komutu için kısa bir Yardım yazdırır.

`-v|--version <VERSION>`

Paketin sürümü.

`-f|--framework <FRAMEWORK>`

Yalnızca belirli bir hedeflerken bir paket başvuru ekler [framework](../../standard/frameworks.md).

`-n|--no-restore`

Bir geri yükleme Önizleme ve uyumluluk denetimi yapmadan paket başvuru ekler.

`-s|--source <SOURCE>`

Geri yükleme işlemi sırasında belirli bir NuGet paketi kaynak kullanır.

`--package-directory <PACKAGE_DIRECTORY>`

Paket için belirtilen dizin geri yükler.

## <a name="examples"></a>Örnekler

Ekleme `Newtonsoft.Json` NuGet paketini projeye:

`dotnet add package Newtonsoft.Json`

Belirli bir paket sürümü için bir proje ekleyin:

`dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0`

Belirli bir NuGet kaynağı kullanarak bir paket ekleyin:

`dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json`
