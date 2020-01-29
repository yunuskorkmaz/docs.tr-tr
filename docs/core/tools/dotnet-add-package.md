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
# <a name="dotnet-add-package"></a><span data-ttu-id="1ab64-103">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="1ab64-103">dotnet add package</span></span>

<span data-ttu-id="1ab64-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 1. x SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="1ab64-104">**This article applies to:** ✔️ .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="1ab64-105">Name</span><span class="sxs-lookup"><span data-stu-id="1ab64-105">Name</span></span>

<span data-ttu-id="1ab64-106">`dotnet add package`-proje dosyasına bir paket başvurusu ekler.</span><span class="sxs-lookup"><span data-stu-id="1ab64-106">`dotnet add package` - Adds a package reference to a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="1ab64-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="1ab64-107">Synopsis</span></span>

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-h|--help] [-f|--framework] [--interactive] [-n|--no-restore] [--package-directory] [-s|--source] [-v|--version]`

## <a name="description"></a><span data-ttu-id="1ab64-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1ab64-108">Description</span></span>

<span data-ttu-id="1ab64-109">`dotnet add package` komutu bir proje dosyasına paket başvurusu eklemek için uygun bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="1ab64-109">The `dotnet add package` command provides a convenient option to add a package reference to a project file.</span></span> <span data-ttu-id="1ab64-110">Komutu çalıştırdıktan sonra, paketin projedeki çerçeveler ile uyumlu olduğundan emin olmak için bir uyumluluk denetimi vardır.</span><span class="sxs-lookup"><span data-stu-id="1ab64-110">After running the command, there's a compatibility check to ensure the package is compatible with the frameworks in the project.</span></span> <span data-ttu-id="1ab64-111">Denetim başarılı olursa, proje dosyasına bir `<PackageReference>` öğesi eklenir ve [DotNet restore](dotnet-restore.md) çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="1ab64-111">If the check passes, a `<PackageReference>` element is added to the project file and [dotnet restore](dotnet-restore.md) is run.</span></span>

[!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

<span data-ttu-id="1ab64-112">Örneğin, *Todo. csproj* öğesine `Newtonsoft.Json` eklemek, aşağıdaki örneğe benzer bir çıktı üretir:</span><span class="sxs-lookup"><span data-stu-id="1ab64-112">For example, adding `Newtonsoft.Json` to *ToDo.csproj* produces output similar to the following example:</span></span>

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

<span data-ttu-id="1ab64-113">*Todo. csproj* dosyası artık başvurulan paket için bir [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) öğesi içeriyor.</span><span class="sxs-lookup"><span data-stu-id="1ab64-113">The *ToDo.csproj* file now contains a [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) element for the referenced package.</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="12.0.1" />
```

## <a name="arguments"></a><span data-ttu-id="1ab64-114">Arguments</span><span class="sxs-lookup"><span data-stu-id="1ab64-114">Arguments</span></span>

- **`PROJECT`**

  <span data-ttu-id="1ab64-115">Proje dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1ab64-115">Specifies the project file.</span></span> <span data-ttu-id="1ab64-116">Belirtilmemişse, komut geçerli dizinde bir arama yapar.</span><span class="sxs-lookup"><span data-stu-id="1ab64-116">If not specified, the command searches the current directory for one.</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="1ab64-117">Eklenecek paket başvurusu.</span><span class="sxs-lookup"><span data-stu-id="1ab64-117">The package reference to add.</span></span>

## <a name="options"></a><span data-ttu-id="1ab64-118">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="1ab64-118">Options</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="1ab64-119">Yalnızca belirli bir [çerçeveyi](../../standard/frameworks.md)hedeflerken bir paket başvurusu ekler.</span><span class="sxs-lookup"><span data-stu-id="1ab64-119">Adds a package reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="1ab64-120">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="1ab64-120">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="1ab64-121">Komutun, Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir (örneğin, kimlik doğrulamasını tamamlamaya yönelik).</span><span class="sxs-lookup"><span data-stu-id="1ab64-121">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="1ab64-122">.NET Core 2,1 SDK, sürüm 2.1.400 veya sonrası ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1ab64-122">Available since .NET Core 2.1 SDK, version 2.1.400 or later.</span></span>

- **`-n|--no-restore`**

  <span data-ttu-id="1ab64-123">Geri yükleme önizlemesi ve uyumluluk denetimi yapılmadan bir paket başvurusu ekler.</span><span class="sxs-lookup"><span data-stu-id="1ab64-123">Adds a package reference without performing a restore preview and compatibility check.</span></span>

- **`--package-directory <PACKAGE_DIRECTORY>`**

  <span data-ttu-id="1ab64-124">Paketlerin geri yükleneceği dizin.</span><span class="sxs-lookup"><span data-stu-id="1ab64-124">The directory where to restore the packages.</span></span> <span data-ttu-id="1ab64-125">Varsayılan paket geri yükleme konumu Windows üzerinde `%userprofile%\.nuget\packages` ve macOS ve Linux üzerinde `~/.nuget/packages`.</span><span class="sxs-lookup"><span data-stu-id="1ab64-125">The default package restore location is `%userprofile%\.nuget\packages` on Windows and `~/.nuget/packages` on macOS and Linux.</span></span> <span data-ttu-id="1ab64-126">Daha fazla bilgi için bkz. [NuGet 'de Genel paketleri, önbelleği ve temp klasörlerini yönetme](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders).</span><span class="sxs-lookup"><span data-stu-id="1ab64-126">For more information, see [Managing the global packages, cache, and temp folders in NuGet](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders).</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="1ab64-127">Geri yükleme işlemi sırasında kullanılacak NuGet paketi kaynağı.</span><span class="sxs-lookup"><span data-stu-id="1ab64-127">The NuGet package source to use during the restore operation.</span></span>

- **`-v|--version <VERSION>`**

  <span data-ttu-id="1ab64-128">Paketin sürümü.</span><span class="sxs-lookup"><span data-stu-id="1ab64-128">Version of the package.</span></span> <span data-ttu-id="1ab64-129">Bkz. [NuGet paketi sürümü oluşturma](https://docs.microsoft.com/nuget/reference/package-versioning).</span><span class="sxs-lookup"><span data-stu-id="1ab64-129">See [NuGet package versioning](https://docs.microsoft.com/nuget/reference/package-versioning).</span></span>

## <a name="examples"></a><span data-ttu-id="1ab64-130">Örnekler</span><span class="sxs-lookup"><span data-stu-id="1ab64-130">Examples</span></span>

- <span data-ttu-id="1ab64-131">Bir projeye `Newtonsoft.Json` NuGet paketi Ekle:</span><span class="sxs-lookup"><span data-stu-id="1ab64-131">Add `Newtonsoft.Json` NuGet package to a project:</span></span>

  ```dotnetcli
  dotnet add package Newtonsoft.Json
  ```

- <span data-ttu-id="1ab64-132">Bir projeye paketin belirli bir sürümünü ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1ab64-132">Add a specific version of a package to a project:</span></span>

  ```dotnetcli
  dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0
  ```

- <span data-ttu-id="1ab64-133">Belirli bir NuGet kaynağını kullanarak bir paket ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1ab64-133">Add a package using a specific NuGet source:</span></span>

  ```dotnetcli
  dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json
  ```

## <a name="see-also"></a><span data-ttu-id="1ab64-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ab64-134">See also</span></span>

- [<span data-ttu-id="1ab64-135">NuGet 'de Genel paketleri, önbelleği ve temp klasörlerini yönetme</span><span class="sxs-lookup"><span data-stu-id="1ab64-135">Managing the global packages, cache, and temp folders in NuGet</span></span>](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders)
- [<span data-ttu-id="1ab64-136">NuGet paketi sürümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="1ab64-136">NuGet package versioning</span></span>](https://docs.microsoft.com/nuget/reference/package-versioning)
