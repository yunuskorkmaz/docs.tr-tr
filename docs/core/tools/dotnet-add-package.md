---
title: dotnet ekle paket komutu
description: "'dotnet paketi ekle' komutu, projeye NuGet paketi başvurusu eklemek için kullanışlı bir seçenek sunar."
ms.date: 02/14/2020
ms.openlocfilehash: 8121539a50d2ac2837693ccc35581f7fde1d1fc1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146612"
---
# <a name="dotnet-add-package"></a><span data-ttu-id="3f4ba-103">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="3f4ba-103">dotnet add package</span></span>

<span data-ttu-id="3f4ba-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.x SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="3f4ba-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="3f4ba-105">Adı</span><span class="sxs-lookup"><span data-stu-id="3f4ba-105">Name</span></span>

<span data-ttu-id="3f4ba-106">`dotnet add package`- Proje dosyasına paket başvurusu ekler.</span><span class="sxs-lookup"><span data-stu-id="3f4ba-106">`dotnet add package` - Adds a package reference to a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="3f4ba-107">Özet</span><span class="sxs-lookup"><span data-stu-id="3f4ba-107">Synopsis</span></span>

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-h|--help] [-f|--framework] [--interactive] [-n|--no-restore] [--package-directory] [-s|--source] [-v|--version]`

## <a name="description"></a><span data-ttu-id="3f4ba-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3f4ba-108">Description</span></span>

<span data-ttu-id="3f4ba-109">Komut, `dotnet add package` proje dosyasına paket başvurusu eklemek için kullanışlı bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="3f4ba-109">The `dotnet add package` command provides a convenient option to add a package reference to a project file.</span></span> <span data-ttu-id="3f4ba-110">Komutu çalıştırdıktan sonra, paketin projedeki çerçevelerle uyumlu olduğundan emin olmak için bir uyumluluk denetimi vardır.</span><span class="sxs-lookup"><span data-stu-id="3f4ba-110">After running the command, there's a compatibility check to ensure the package is compatible with the frameworks in the project.</span></span> <span data-ttu-id="3f4ba-111">Denetim geçerse, proje `<PackageReference>` dosyasına bir öğe eklenir ve [dotnet geri yükleme](dotnet-restore.md) çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="3f4ba-111">If the check passes, a `<PackageReference>` element is added to the project file and [dotnet restore](dotnet-restore.md) is run.</span></span>

[!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

<span data-ttu-id="3f4ba-112">Örneğin, `Newtonsoft.Json` *ToDo.csproj'a* ekleme aşağıdaki örneğe benzer çıktı üretir:</span><span class="sxs-lookup"><span data-stu-id="3f4ba-112">For example, adding `Newtonsoft.Json` to *ToDo.csproj* produces output similar to the following example:</span></span>

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

<span data-ttu-id="3f4ba-113">*ToDo.csproj* dosyası artık [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) başvurulan paket için bir öğe içerir.</span><span class="sxs-lookup"><span data-stu-id="3f4ba-113">The *ToDo.csproj* file now contains a [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) element for the referenced package.</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="12.0.1" />
```

## <a name="arguments"></a><span data-ttu-id="3f4ba-114">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="3f4ba-114">Arguments</span></span>

- **`PROJECT`**

  <span data-ttu-id="3f4ba-115">Proje dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3f4ba-115">Specifies the project file.</span></span> <span data-ttu-id="3f4ba-116">Belirtilmemişse, komut geçerli dizini arar.</span><span class="sxs-lookup"><span data-stu-id="3f4ba-116">If not specified, the command searches the current directory for one.</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="3f4ba-117">Eklenecek paket başvurusu.</span><span class="sxs-lookup"><span data-stu-id="3f4ba-117">The package reference to add.</span></span>

## <a name="options"></a><span data-ttu-id="3f4ba-118">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="3f4ba-118">Options</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="3f4ba-119">Yalnızca belirli bir [çerçeveyi](../../standard/frameworks.md)hedefalırken paket başvurusu ekler.</span><span class="sxs-lookup"><span data-stu-id="3f4ba-119">Adds a package reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="3f4ba-120">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="3f4ba-120">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="3f4ba-121">Komutun durmasına ve kullanıcı girişinin veya eylemini beklemesine (örneğin, kimlik doğrulamasını tamamlamak için) izin verir.</span><span class="sxs-lookup"><span data-stu-id="3f4ba-121">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="3f4ba-122">.NET Core 2.1 SDK, sürüm 2.1.400 veya daha sonra kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3f4ba-122">Available since .NET Core 2.1 SDK, version 2.1.400 or later.</span></span>

- **`-n|--no-restore`**

  <span data-ttu-id="3f4ba-123">Geri yükleme önizleme ve uyumluluk denetimi gerçekleştirmeden bir paket başvurusu ekler.</span><span class="sxs-lookup"><span data-stu-id="3f4ba-123">Adds a package reference without performing a restore preview and compatibility check.</span></span>

- **`--package-directory <PACKAGE_DIRECTORY>`**

  <span data-ttu-id="3f4ba-124">Paketleri geri yüklemek için dizin.</span><span class="sxs-lookup"><span data-stu-id="3f4ba-124">The directory where to restore the packages.</span></span> <span data-ttu-id="3f4ba-125">Varsayılan paket geri `%userprofile%\.nuget\packages` yükleme konumu `~/.nuget/packages` Windows'ta, macOS ve Linux'tadır.</span><span class="sxs-lookup"><span data-stu-id="3f4ba-125">The default package restore location is `%userprofile%\.nuget\packages` on Windows and `~/.nuget/packages` on macOS and Linux.</span></span> <span data-ttu-id="3f4ba-126">Daha fazla bilgi için bkz. [NuGet'deki genel paketleri, önbellekleri ve geçici klasörleri yönetme.](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders)</span><span class="sxs-lookup"><span data-stu-id="3f4ba-126">For more information, see [Managing the global packages, cache, and temp folders in NuGet](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders).</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="3f4ba-127">Geri yükleme işlemi sırasında kullanılacak NuGet paket kaynağı.</span><span class="sxs-lookup"><span data-stu-id="3f4ba-127">The NuGet package source to use during the restore operation.</span></span>

- **`-v|--version <VERSION>`**

  <span data-ttu-id="3f4ba-128">Paketin sürümü.</span><span class="sxs-lookup"><span data-stu-id="3f4ba-128">Version of the package.</span></span> <span data-ttu-id="3f4ba-129">Bkz. [NuGet paket sürümü.](https://docs.microsoft.com/nuget/reference/package-versioning)</span><span class="sxs-lookup"><span data-stu-id="3f4ba-129">See [NuGet package versioning](https://docs.microsoft.com/nuget/reference/package-versioning).</span></span>

## <a name="examples"></a><span data-ttu-id="3f4ba-130">Örnekler</span><span class="sxs-lookup"><span data-stu-id="3f4ba-130">Examples</span></span>

- <span data-ttu-id="3f4ba-131">Projeye `Newtonsoft.Json` NuGet paketi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="3f4ba-131">Add `Newtonsoft.Json` NuGet package to a project:</span></span>

  ```dotnetcli
  dotnet add package Newtonsoft.Json
  ```

- <span data-ttu-id="3f4ba-132">Projeye paketin belirli bir sürümünü ekleyin:</span><span class="sxs-lookup"><span data-stu-id="3f4ba-132">Add a specific version of a package to a project:</span></span>

  ```dotnetcli
  dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0
  ```

- <span data-ttu-id="3f4ba-133">Belirli bir NuGet kaynağını kullanarak paket ekleyin:</span><span class="sxs-lookup"><span data-stu-id="3f4ba-133">Add a package using a specific NuGet source:</span></span>

  ```dotnetcli
  dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json
  ```

## <a name="see-also"></a><span data-ttu-id="3f4ba-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f4ba-134">See also</span></span>

- [<span data-ttu-id="3f4ba-135">NuGet'de genel paketleri, önbelleği ve geçici klasörleri yönetme</span><span class="sxs-lookup"><span data-stu-id="3f4ba-135">Managing the global packages, cache, and temp folders in NuGet</span></span>](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders)
- [<span data-ttu-id="3f4ba-136">NuGet paketi sürümü</span><span class="sxs-lookup"><span data-stu-id="3f4ba-136">NuGet package versioning</span></span>](https://docs.microsoft.com/nuget/reference/package-versioning)
