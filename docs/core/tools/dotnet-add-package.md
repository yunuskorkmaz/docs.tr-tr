---
title: DotNet paketi komut ekleme
description: "'Dotnet, paket Ekle' komutunu bir projeye bir NuGet paketi başvuru eklemek için uygun bir seçenek sağlar."
ms.date: 12/04/2018
ms.openlocfilehash: 159b208feafb82e267629ea47dcef02d6b575055
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170008"
---
# <a name="dotnet-add-package"></a><span data-ttu-id="db150-103">DotNet paketi ekleme</span><span class="sxs-lookup"><span data-stu-id="db150-103">dotnet add package</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="db150-104">Ad</span><span class="sxs-lookup"><span data-stu-id="db150-104">Name</span></span>

<span data-ttu-id="db150-105">`dotnet add package` -Bir proje dosyası için bir paket başvurusu ekler.</span><span class="sxs-lookup"><span data-stu-id="db150-105">`dotnet add package` - Adds a package reference to a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="db150-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="db150-106">Synopsis</span></span>

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-h|--help] [-f|--framework] [--interactive] [-n|--no-restore] [--package-directory] [-s|--source] [-v|--version]`

## <a name="description"></a><span data-ttu-id="db150-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="db150-107">Description</span></span>

<span data-ttu-id="db150-108">`dotnet add package` Komutu bir proje dosyası için bir paket başvurusu eklemek için uygun bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="db150-108">The `dotnet add package` command provides a convenient option to add a package reference to a project file.</span></span> <span data-ttu-id="db150-109">Komutu çalıştırdıktan sonra paket projedeki çerçevelerle uyumlu olduğundan emin olmak için bir uyumluluk denetimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="db150-109">After running the command, there's a compatibility check to ensure the package is compatible with the frameworks in the project.</span></span> <span data-ttu-id="db150-110">Onay başarılı olursa bir `<PackageReference>` öğesi, proje dosyasına eklenir ve [dotnet restore](dotnet-restore.md) çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="db150-110">If the check passes, a `<PackageReference>` element is added to the project file and [dotnet restore](dotnet-restore.md) is run.</span></span>

[!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

<span data-ttu-id="db150-111">Örneğin, ekleme `Newtonsoft.Json` için *ToDo.csproj* aşağıdaki örneğe benzer bir çıktı üretir:</span><span class="sxs-lookup"><span data-stu-id="db150-111">For example, adding `Newtonsoft.Json` to *ToDo.csproj* produces output similar to the following example:</span></span>

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

<span data-ttu-id="db150-112">*ToDo.csproj* artık dosya içeren bir [ `<PackageReference>` ](/nuget/consume-packages/package-references-in-project-files) başvurulan paketi için öğesi.</span><span class="sxs-lookup"><span data-stu-id="db150-112">The *ToDo.csproj* file now contains a [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) element for the referenced package.</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="12.0.1" />
```

## <a name="arguments"></a><span data-ttu-id="db150-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="db150-113">Arguments</span></span>

* **`PROJECT`**

  <span data-ttu-id="db150-114">Proje dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="db150-114">Specifies the project file.</span></span> <span data-ttu-id="db150-115">Belirtilmezse, komut için geçerli dizinde arar.</span><span class="sxs-lookup"><span data-stu-id="db150-115">If not specified, the command searches the current directory for one.</span></span>

* **`PACKAGE_NAME`**

  <span data-ttu-id="db150-116">Eklenecek paket başvurusu.</span><span class="sxs-lookup"><span data-stu-id="db150-116">The package reference to add.</span></span>

## <a name="options"></a><span data-ttu-id="db150-117">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="db150-117">Options</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="db150-118">Yalnızca belirli bir hedeflenirken paket başvurusu ekler [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="db150-118">Adds a package reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

* **`-h|--help`**

  <span data-ttu-id="db150-119">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="db150-119">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="db150-120">Durdurmak ve kullanıcı girişi veya eylem (örneğin kimlik doğrulamasını tamamlamak için) için beklemek için komutu sağlar.</span><span class="sxs-lookup"><span data-stu-id="db150-120">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span> <span data-ttu-id="db150-121">.NET Core 2.1 SDK, sürüm 2.1.400 sürümünden itibaren kullanılabilir veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="db150-121">Available since .NET Core 2.1 SDK, version 2.1.400 or later.</span></span>

* **`-n|--no-restore`**

  <span data-ttu-id="db150-122">Geri yükleme Önizleme ve uyumluluk denetimi gerçekleştirmeden bir paket başvurusu ekler.</span><span class="sxs-lookup"><span data-stu-id="db150-122">Adds a package reference without performing a restore preview and compatibility check.</span></span>

* **`--package-directory <PACKAGE_DIRECTORY>`**

  <span data-ttu-id="db150-123">Pakette belirtilen dizine geri yükler.</span><span class="sxs-lookup"><span data-stu-id="db150-123">Restores the package to the specified directory.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="db150-124">Geri yükleme işlemi sırasında belirli bir NuGet paket kaynağı kullanır.</span><span class="sxs-lookup"><span data-stu-id="db150-124">Uses a specific NuGet package source during the restore operation.</span></span>

* **`-v|--version <VERSION>`**

  <span data-ttu-id="db150-125">Paket sürümü.</span><span class="sxs-lookup"><span data-stu-id="db150-125">Version of the package.</span></span>

## <a name="examples"></a><span data-ttu-id="db150-126">Örnekler</span><span class="sxs-lookup"><span data-stu-id="db150-126">Examples</span></span>

* <span data-ttu-id="db150-127">Ekleme `Newtonsoft.Json` NuGet paketini projeye:</span><span class="sxs-lookup"><span data-stu-id="db150-127">Add `Newtonsoft.Json` NuGet package to a project:</span></span>

  ```console
  dotnet add package Newtonsoft.Json
  ```

* <span data-ttu-id="db150-128">Bir paketin belirli bir sürümünü bir projeye ekleyin:</span><span class="sxs-lookup"><span data-stu-id="db150-128">Add a specific version of a package to a project:</span></span>

  ```console
  dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0
  ```

* <span data-ttu-id="db150-129">Belirli bir NuGet kaynağını kullanarak paket ekleyin:</span><span class="sxs-lookup"><span data-stu-id="db150-129">Add a package using a specific NuGet source:</span></span>

  ```console
  dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json
  ```