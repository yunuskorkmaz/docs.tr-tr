---
title: DotNet paket Ekle komutu
description: "' DotNet Add Package ' komutu, bir projeye NuGet paket başvurusu eklemek için uygun bir seçenek sağlar."
ms.date: 02/14/2020
ms.openlocfilehash: bc79fe8adf5f775ddce62f3877a8de945c6a18ab
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83840903"
---
# <a name="dotnet-add-package"></a><span data-ttu-id="f7139-103">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="f7139-103">dotnet add package</span></span>

<span data-ttu-id="f7139-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2. x SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="f7139-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="f7139-105">Name</span><span class="sxs-lookup"><span data-stu-id="f7139-105">Name</span></span>

<span data-ttu-id="f7139-106">`dotnet add package`-Proje dosyasına bir paket başvurusu ekler.</span><span class="sxs-lookup"><span data-stu-id="f7139-106">`dotnet add package` - Adds a package reference to a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f7139-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="f7139-107">Synopsis</span></span>

```dotnetcli
dotnet add [<PROJECT>] package <PACKAGE_NAME>
    [-f|--framework <FRAMEWORK>] [--interactive]
    [-n|--no-restore] [--package-directory <PACKAGE_DIRECTORY>]
    [-s|--source <SOURCE>] [-v|--version <VERSION>]

dotnet add package -h|--help
```

## <a name="description"></a><span data-ttu-id="f7139-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f7139-108">Description</span></span>

<span data-ttu-id="f7139-109">`dotnet add package`Komut, bir proje dosyasına paket başvurusu eklemek için uygun bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="f7139-109">The `dotnet add package` command provides a convenient option to add a package reference to a project file.</span></span> <span data-ttu-id="f7139-110">Komutu çalıştırdıktan sonra, paketin projedeki çerçeveler ile uyumlu olduğundan emin olmak için bir uyumluluk denetimi vardır.</span><span class="sxs-lookup"><span data-stu-id="f7139-110">After running the command, there's a compatibility check to ensure the package is compatible with the frameworks in the project.</span></span> <span data-ttu-id="f7139-111">Denetim başarılı olursa, `<PackageReference>` proje dosyasına bir öğe eklenir ve [DotNet restore](dotnet-restore.md) çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="f7139-111">If the check passes, a `<PackageReference>` element is added to the project file and [dotnet restore](dotnet-restore.md) is run.</span></span>

<span data-ttu-id="f7139-112">Örneğin, `Newtonsoft.Json` *Todo. csproj* öğesine eklemek aşağıdaki örneğe benzer bir çıktı üretir:</span><span class="sxs-lookup"><span data-stu-id="f7139-112">For example, adding `Newtonsoft.Json` to *ToDo.csproj* produces output similar to the following example:</span></span>

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

<span data-ttu-id="f7139-113">*Todo. csproj* dosyası artık [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) başvurulan paket için bir öğe içeriyor.</span><span class="sxs-lookup"><span data-stu-id="f7139-113">The *ToDo.csproj* file now contains a [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) element for the referenced package.</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="12.0.1" />
```

### <a name="implicit-restore"></a><span data-ttu-id="f7139-114">Örtük geri yükleme</span><span class="sxs-lookup"><span data-stu-id="f7139-114">Implicit restore</span></span>

[!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="f7139-115">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="f7139-115">Arguments</span></span>

- **`PROJECT`**

  <span data-ttu-id="f7139-116">Proje dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f7139-116">Specifies the project file.</span></span> <span data-ttu-id="f7139-117">Belirtilmemişse, komut geçerli dizinde bir arama yapar.</span><span class="sxs-lookup"><span data-stu-id="f7139-117">If not specified, the command searches the current directory for one.</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="f7139-118">Eklenecek paket başvurusu.</span><span class="sxs-lookup"><span data-stu-id="f7139-118">The package reference to add.</span></span>

## <a name="options"></a><span data-ttu-id="f7139-119">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="f7139-119">Options</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f7139-120">Yalnızca belirli bir [çerçeveyi](../../standard/frameworks.md)hedeflerken bir paket başvurusu ekler.</span><span class="sxs-lookup"><span data-stu-id="f7139-120">Adds a package reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="f7139-121">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="f7139-121">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="f7139-122">Komutun, Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir (örneğin, kimlik doğrulamasını tamamlamaya yönelik).</span><span class="sxs-lookup"><span data-stu-id="f7139-122">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="f7139-123">.NET Core 2,1 SDK, sürüm 2.1.400 veya sonrası ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f7139-123">Available since .NET Core 2.1 SDK, version 2.1.400 or later.</span></span>

- **`-n|--no-restore`**

  <span data-ttu-id="f7139-124">Geri yükleme önizlemesi ve uyumluluk denetimi yapılmadan bir paket başvurusu ekler.</span><span class="sxs-lookup"><span data-stu-id="f7139-124">Adds a package reference without performing a restore preview and compatibility check.</span></span>

- **`--package-directory <PACKAGE_DIRECTORY>`**

  <span data-ttu-id="f7139-125">Paketlerin geri yükleneceği dizin.</span><span class="sxs-lookup"><span data-stu-id="f7139-125">The directory where to restore the packages.</span></span> <span data-ttu-id="f7139-126">Varsayılan paket geri yükleme konumu `%userprofile%\.nuget\packages` Windows ve `~/.nuget/packages` MacOS ve Linux üzerinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="f7139-126">The default package restore location is `%userprofile%\.nuget\packages` on Windows and `~/.nuget/packages` on macOS and Linux.</span></span> <span data-ttu-id="f7139-127">Daha fazla bilgi için bkz. [NuGet 'de Genel paketleri, önbelleği ve temp klasörlerini yönetme](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders).</span><span class="sxs-lookup"><span data-stu-id="f7139-127">For more information, see [Managing the global packages, cache, and temp folders in NuGet](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders).</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="f7139-128">Geri yükleme işlemi sırasında kullanılacak NuGet paket kaynağının URI 'SI.</span><span class="sxs-lookup"><span data-stu-id="f7139-128">The URI of the NuGet package source to use during the restore operation.</span></span>

- **`-v|--version <VERSION>`**

  <span data-ttu-id="f7139-129">Paketin sürümü.</span><span class="sxs-lookup"><span data-stu-id="f7139-129">Version of the package.</span></span> <span data-ttu-id="f7139-130">Bkz. [NuGet paketi sürümü oluşturma](https://docs.microsoft.com/nuget/reference/package-versioning).</span><span class="sxs-lookup"><span data-stu-id="f7139-130">See [NuGet package versioning](https://docs.microsoft.com/nuget/reference/package-versioning).</span></span>

## <a name="examples"></a><span data-ttu-id="f7139-131">Örnekler</span><span class="sxs-lookup"><span data-stu-id="f7139-131">Examples</span></span>

- <span data-ttu-id="f7139-132">`Newtonsoft.Json`Bir projeye NuGet paketi Ekle:</span><span class="sxs-lookup"><span data-stu-id="f7139-132">Add `Newtonsoft.Json` NuGet package to a project:</span></span>

  ```dotnetcli
  dotnet add package Newtonsoft.Json
  ```

- <span data-ttu-id="f7139-133">Bir projeye paketin belirli bir sürümünü ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f7139-133">Add a specific version of a package to a project:</span></span>

  ```dotnetcli
  dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0
  ```

- <span data-ttu-id="f7139-134">Belirli bir NuGet kaynağını kullanarak bir paket ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f7139-134">Add a package using a specific NuGet source:</span></span>

  ```dotnetcli
  dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json
  ```

## <a name="see-also"></a><span data-ttu-id="f7139-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7139-135">See also</span></span>

- [<span data-ttu-id="f7139-136">NuGet 'de Genel paketleri, önbelleği ve temp klasörlerini yönetme</span><span class="sxs-lookup"><span data-stu-id="f7139-136">Managing the global packages, cache, and temp folders in NuGet</span></span>](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders)
- [<span data-ttu-id="f7139-137">NuGet paketi sürümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="f7139-137">NuGet package versioning</span></span>](https://docs.microsoft.com/nuget/reference/package-versioning)
