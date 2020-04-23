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
# <a name="dotnet-add-package"></a><span data-ttu-id="afb16-103">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="afb16-103">dotnet add package</span></span>

<span data-ttu-id="afb16-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.x SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="afb16-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="afb16-105">Adı</span><span class="sxs-lookup"><span data-stu-id="afb16-105">Name</span></span>

<span data-ttu-id="afb16-106">`dotnet add package`- Proje dosyasına paket başvurusu ekler.</span><span class="sxs-lookup"><span data-stu-id="afb16-106">`dotnet add package` - Adds a package reference to a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="afb16-107">Özet</span><span class="sxs-lookup"><span data-stu-id="afb16-107">Synopsis</span></span>

```dotnetcli
dotnet add [<PROJECT>] package <PACKAGE_NAME>
    [-f|--framework <FRAMEWORK>] [--interactive]
    [-n|--no-restore] [--package-directory <PACKAGE_DIRECTORY>]
    [-s|--source <SOURCE>] [-v|--version <VERSION>]

dotnet add package -h|--help
```

## <a name="description"></a><span data-ttu-id="afb16-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="afb16-108">Description</span></span>

<span data-ttu-id="afb16-109">Komut, `dotnet add package` proje dosyasına paket başvurusu eklemek için kullanışlı bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="afb16-109">The `dotnet add package` command provides a convenient option to add a package reference to a project file.</span></span> <span data-ttu-id="afb16-110">Komutu çalıştırdıktan sonra, paketin projedeki çerçevelerle uyumlu olduğundan emin olmak için bir uyumluluk denetimi vardır.</span><span class="sxs-lookup"><span data-stu-id="afb16-110">After running the command, there's a compatibility check to ensure the package is compatible with the frameworks in the project.</span></span> <span data-ttu-id="afb16-111">Denetim geçerse, proje `<PackageReference>` dosyasına bir öğe eklenir ve [dotnet geri yükleme](dotnet-restore.md) çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="afb16-111">If the check passes, a `<PackageReference>` element is added to the project file and [dotnet restore](dotnet-restore.md) is run.</span></span>

<span data-ttu-id="afb16-112">Örneğin, `Newtonsoft.Json` *ToDo.csproj'a* ekleme aşağıdaki örneğe benzer çıktı üretir:</span><span class="sxs-lookup"><span data-stu-id="afb16-112">For example, adding `Newtonsoft.Json` to *ToDo.csproj* produces output similar to the following example:</span></span>

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

<span data-ttu-id="afb16-113">*ToDo.csproj* dosyası artık [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) başvurulan paket için bir öğe içerir.</span><span class="sxs-lookup"><span data-stu-id="afb16-113">The *ToDo.csproj* file now contains a [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) element for the referenced package.</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="12.0.1" />
```

### <a name="implicit-restore"></a><span data-ttu-id="afb16-114">Örtük geri yükleme</span><span class="sxs-lookup"><span data-stu-id="afb16-114">Implicit restore</span></span>

[!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="afb16-115">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="afb16-115">Arguments</span></span>

- **`PROJECT`**

  <span data-ttu-id="afb16-116">Proje dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="afb16-116">Specifies the project file.</span></span> <span data-ttu-id="afb16-117">Belirtilmemişse, komut geçerli dizini arar.</span><span class="sxs-lookup"><span data-stu-id="afb16-117">If not specified, the command searches the current directory for one.</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="afb16-118">Eklenecek paket başvurusu.</span><span class="sxs-lookup"><span data-stu-id="afb16-118">The package reference to add.</span></span>

## <a name="options"></a><span data-ttu-id="afb16-119">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="afb16-119">Options</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="afb16-120">Yalnızca belirli bir [çerçeveyi](../../standard/frameworks.md)hedefalırken paket başvurusu ekler.</span><span class="sxs-lookup"><span data-stu-id="afb16-120">Adds a package reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="afb16-121">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="afb16-121">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="afb16-122">Komutun durmasına ve kullanıcı girişinin veya eylemini beklemesine (örneğin, kimlik doğrulamasını tamamlamak için) izin verir.</span><span class="sxs-lookup"><span data-stu-id="afb16-122">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="afb16-123">.NET Core 2.1 SDK, sürüm 2.1.400 veya daha sonra kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="afb16-123">Available since .NET Core 2.1 SDK, version 2.1.400 or later.</span></span>

- **`-n|--no-restore`**

  <span data-ttu-id="afb16-124">Geri yükleme önizleme ve uyumluluk denetimi gerçekleştirmeden bir paket başvurusu ekler.</span><span class="sxs-lookup"><span data-stu-id="afb16-124">Adds a package reference without performing a restore preview and compatibility check.</span></span>

- **`--package-directory <PACKAGE_DIRECTORY>`**

  <span data-ttu-id="afb16-125">Paketleri geri yüklemek için dizin.</span><span class="sxs-lookup"><span data-stu-id="afb16-125">The directory where to restore the packages.</span></span> <span data-ttu-id="afb16-126">Varsayılan paket geri `%userprofile%\.nuget\packages` yükleme konumu `~/.nuget/packages` Windows'ta, macOS ve Linux'tadır.</span><span class="sxs-lookup"><span data-stu-id="afb16-126">The default package restore location is `%userprofile%\.nuget\packages` on Windows and `~/.nuget/packages` on macOS and Linux.</span></span> <span data-ttu-id="afb16-127">Daha fazla bilgi için bkz. [NuGet'deki genel paketleri, önbellekleri ve geçici klasörleri yönetme.](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders)</span><span class="sxs-lookup"><span data-stu-id="afb16-127">For more information, see [Managing the global packages, cache, and temp folders in NuGet](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders).</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="afb16-128">Geri yükleme işlemi sırasında kullanılacak NuGet paket kaynağı.</span><span class="sxs-lookup"><span data-stu-id="afb16-128">The NuGet package source to use during the restore operation.</span></span>

- **`-v|--version <VERSION>`**

  <span data-ttu-id="afb16-129">Paketin sürümü.</span><span class="sxs-lookup"><span data-stu-id="afb16-129">Version of the package.</span></span> <span data-ttu-id="afb16-130">Bkz. [NuGet paket sürümü.](https://docs.microsoft.com/nuget/reference/package-versioning)</span><span class="sxs-lookup"><span data-stu-id="afb16-130">See [NuGet package versioning](https://docs.microsoft.com/nuget/reference/package-versioning).</span></span>

## <a name="examples"></a><span data-ttu-id="afb16-131">Örnekler</span><span class="sxs-lookup"><span data-stu-id="afb16-131">Examples</span></span>

- <span data-ttu-id="afb16-132">Projeye `Newtonsoft.Json` NuGet paketi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="afb16-132">Add `Newtonsoft.Json` NuGet package to a project:</span></span>

  ```dotnetcli
  dotnet add package Newtonsoft.Json
  ```

- <span data-ttu-id="afb16-133">Projeye paketin belirli bir sürümünü ekleyin:</span><span class="sxs-lookup"><span data-stu-id="afb16-133">Add a specific version of a package to a project:</span></span>

  ```dotnetcli
  dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0
  ```

- <span data-ttu-id="afb16-134">Belirli bir NuGet kaynağını kullanarak paket ekleyin:</span><span class="sxs-lookup"><span data-stu-id="afb16-134">Add a package using a specific NuGet source:</span></span>

  ```dotnetcli
  dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json
  ```

## <a name="see-also"></a><span data-ttu-id="afb16-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="afb16-135">See also</span></span>

- [<span data-ttu-id="afb16-136">NuGet'de genel paketleri, önbelleği ve geçici klasörleri yönetme</span><span class="sxs-lookup"><span data-stu-id="afb16-136">Managing the global packages, cache, and temp folders in NuGet</span></span>](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders)
- [<span data-ttu-id="afb16-137">NuGet paketi sürümü</span><span class="sxs-lookup"><span data-stu-id="afb16-137">NuGet package versioning</span></span>](https://docs.microsoft.com/nuget/reference/package-versioning)
