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
# <a name="dotnet-add-package"></a><span data-ttu-id="9aab7-103">DotNet paket ekleme</span><span class="sxs-lookup"><span data-stu-id="9aab7-103">dotnet add package</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="9aab7-104">Ad</span><span class="sxs-lookup"><span data-stu-id="9aab7-104">Name</span></span>

<span data-ttu-id="9aab7-105">`dotnet add package` -Bir proje dosyası için bir paket başvuru ekler.</span><span class="sxs-lookup"><span data-stu-id="9aab7-105">`dotnet add package` - Adds a package reference to a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9aab7-106">Özet</span><span class="sxs-lookup"><span data-stu-id="9aab7-106">Synopsis</span></span>

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-h|--help] [-v|--version] [-f|--framework] [-n|--no-restore] [-s|--source] [--package-directory]`

## <a name="description"></a><span data-ttu-id="9aab7-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9aab7-107">Description</span></span>

<span data-ttu-id="9aab7-108">`dotnet add package` Komutu bir proje dosyası paketi başvuru eklemek için uygun bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="9aab7-108">The `dotnet add package` command provides a convenient option to add a package reference to a project file.</span></span> <span data-ttu-id="9aab7-109">Komutu çalıştırdıktan sonra paketi projesinde çerçeveleri ile uyumlu olduğundan emin olmak için bir uyumluluk denetimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="9aab7-109">After running the command, there's a compatibility check to ensure the package is compatible with the frameworks in the project.</span></span> <span data-ttu-id="9aab7-110">Onay başarılı olursa, bir `<PackageReference>` öğesi proje dosyasına eklenir ve [dotnet geri yükleme](dotnet-restore.md) çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="9aab7-110">If the check passes, a `<PackageReference>` element is added to the project file and [dotnet restore](dotnet-restore.md) is run.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="9aab7-111">Örneğin, ekleme `Newtonsoft.Json` için *ToDo.csproj* aşağıdaki örneğe benzer bir çıktı üretir:</span><span class="sxs-lookup"><span data-stu-id="9aab7-111">For example, adding `Newtonsoft.Json` to *ToDo.csproj* produces output similar to the following example:</span></span>

```
  Writing C:\Users\mairaw\AppData\Local\Temp\tmp95A8.tmp
info : Adding PackageReference for package 'Newtonsoft.Json' into project 'C:\projects\ToDo\ToDo.csproj'.
log  : Restoring packages for C:\projects\ToDo\ToDo.csproj...
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json 235ms
info : Package 'Newtonsoft.Json' is compatible with all the specified frameworks in project 'C:\projects\ToDo\ToDo.csproj'.
info : PackageReference for package 'Newtonsoft.Json' version '10.0.3' added to file 'C:\projects\ToDo\ToDo.csproj'.
```

<span data-ttu-id="9aab7-112">*ToDo.csproj* dosyayı şimdi içeren bir [ `<PackageReference>` ](/nuget/consume-packages/package-references-in-project-files) başvurulan paketi öğesi.</span><span class="sxs-lookup"><span data-stu-id="9aab7-112">The *ToDo.csproj* file now contains a [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) element for the referenced package.</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```

## <a name="arguments"></a><span data-ttu-id="9aab7-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="9aab7-113">Arguments</span></span>

`PROJECT`

<span data-ttu-id="9aab7-114">Proje dosyası belirtir.</span><span class="sxs-lookup"><span data-stu-id="9aab7-114">Specifies the project file.</span></span> <span data-ttu-id="9aab7-115">Belirtilmezse, komut için geçerli dizin arar.</span><span class="sxs-lookup"><span data-stu-id="9aab7-115">If not specified, the command searches the current directory for one.</span></span>

`PACKAGE_NAME`

<span data-ttu-id="9aab7-116">Eklenecek paket başvuru.</span><span class="sxs-lookup"><span data-stu-id="9aab7-116">The package reference to add.</span></span>

## <a name="options"></a><span data-ttu-id="9aab7-117">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="9aab7-117">Options</span></span>

`-h|--help`

<span data-ttu-id="9aab7-118">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="9aab7-118">Prints out a short help for the command.</span></span>

`-v|--version <VERSION>`

<span data-ttu-id="9aab7-119">Paketin sürümü.</span><span class="sxs-lookup"><span data-stu-id="9aab7-119">Version of the package.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="9aab7-120">Yalnızca belirli bir hedeflerken bir paket başvuru ekler [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="9aab7-120">Adds a package reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

`-n|--no-restore`

<span data-ttu-id="9aab7-121">Bir geri yükleme Önizleme ve uyumluluk denetimi yapmadan paket başvuru ekler.</span><span class="sxs-lookup"><span data-stu-id="9aab7-121">Adds a package reference without performing a restore preview and compatibility check.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="9aab7-122">Geri yükleme işlemi sırasında belirli bir NuGet paketi kaynak kullanır.</span><span class="sxs-lookup"><span data-stu-id="9aab7-122">Uses a specific NuGet package source during the restore operation.</span></span>

`--package-directory <PACKAGE_DIRECTORY>`

<span data-ttu-id="9aab7-123">Paket için belirtilen dizin geri yükler.</span><span class="sxs-lookup"><span data-stu-id="9aab7-123">Restores the package to the specified directory.</span></span>

## <a name="examples"></a><span data-ttu-id="9aab7-124">Örnekler</span><span class="sxs-lookup"><span data-stu-id="9aab7-124">Examples</span></span>

<span data-ttu-id="9aab7-125">Ekleme `Newtonsoft.Json` NuGet paketini projeye:</span><span class="sxs-lookup"><span data-stu-id="9aab7-125">Add `Newtonsoft.Json` NuGet package to a project:</span></span>

`dotnet add package Newtonsoft.Json`

<span data-ttu-id="9aab7-126">Belirli bir paket sürümü için bir proje ekleyin:</span><span class="sxs-lookup"><span data-stu-id="9aab7-126">Add a specific version of a package to a project:</span></span>

`dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0`

<span data-ttu-id="9aab7-127">Belirli bir NuGet kaynağı kullanarak bir paket ekleyin:</span><span class="sxs-lookup"><span data-stu-id="9aab7-127">Add a package using a specific NuGet source:</span></span>

`dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json`
