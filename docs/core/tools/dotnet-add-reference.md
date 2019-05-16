---
title: DotNet-başvuru komut ekleme
description: Dotnet ekleyin başvuru komut projeden projeye başvurular eklemek için uygun bir seçenek sağlar.
ms.date: 04/24/2019
ms.openlocfilehash: e90f95527d4f14c7851ccd8d30201daaaaefa2ae
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65631935"
---
# <a name="dotnet-add-reference"></a><span data-ttu-id="49465-103">DotNet-Başvuru Ekle</span><span class="sxs-lookup"><span data-stu-id="49465-103">dotnet-add reference</span></span>

<span data-ttu-id="49465-104">**Bu makale için geçerlidir: ✓** .NET Core SDK'sı 1.x ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="49465-104">**This article applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="49465-105">Ad</span><span class="sxs-lookup"><span data-stu-id="49465-105">Name</span></span>

<span data-ttu-id="49465-106">`dotnet add reference` -Projeler (P2P) başvuruları ekler.</span><span class="sxs-lookup"><span data-stu-id="49465-106">`dotnet add reference` - Adds project-to-project (P2P) references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="49465-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="49465-107">Synopsis</span></span>

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a><span data-ttu-id="49465-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="49465-108">Description</span></span>

<span data-ttu-id="49465-109">`dotnet add reference` Komutu, bir proje proje başvurular eklemek için uygun bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="49465-109">The `dotnet add reference` command provides a convenient option to add project references to a project.</span></span> <span data-ttu-id="49465-110">Komutu çalıştırdıktan sonra [ `<ProjectReference>` ](/visualstudio/msbuild/common-msbuild-project-items) öğeleri, proje dosyasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="49465-110">After running the command, the [`<ProjectReference>`](/visualstudio/msbuild/common-msbuild-project-items) elements are added to the project file.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a><span data-ttu-id="49465-111">Arguments</span><span class="sxs-lookup"><span data-stu-id="49465-111">Arguments</span></span>

* **`PROJECT`**

  <span data-ttu-id="49465-112">Proje dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="49465-112">Specifies the project file.</span></span> <span data-ttu-id="49465-113">Belirtilmezse, komut için geçerli dizinde arar.</span><span class="sxs-lookup"><span data-stu-id="49465-113">If not specified, the command searches the current directory for one.</span></span>

* **`PROJECT_REFERENCES`**

  <span data-ttu-id="49465-114">Eklenecek proje proje (P2P) başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="49465-114">Project-to-project (P2P) references to add.</span></span> <span data-ttu-id="49465-115">Bir veya daha fazla proje belirtin.</span><span class="sxs-lookup"><span data-stu-id="49465-115">Specify one or more projects.</span></span> <span data-ttu-id="49465-116">[Glob desenleri](https://en.wikipedia.org/wiki/Glob_(programming)) UNIX/Linux tabanlı sistemlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="49465-116">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux-based systems.</span></span>

## <a name="options"></a><span data-ttu-id="49465-117">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="49465-117">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="49465-118">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="49465-118">Prints out a short help for the command.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="49465-119">Yalnızca belirli bir hedeflenirken proje başvuruları ekler [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="49465-119">Adds project references only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="49465-120">Örnekler</span><span class="sxs-lookup"><span data-stu-id="49465-120">Examples</span></span>

* <span data-ttu-id="49465-121">Bir proje başvurusu Ekle:</span><span class="sxs-lookup"><span data-stu-id="49465-121">Add a project reference:</span></span>

  ```console
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

* <span data-ttu-id="49465-122">Geçerli dizinde birden çok proje başvuruları projeye ekleyin:</span><span class="sxs-lookup"><span data-stu-id="49465-122">Add multiple project references to the project in the current directory:</span></span>

  ```console
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

* <span data-ttu-id="49465-123">Linux/UNIX Glob deseni kullanılarak birden çok proje başvurularını ekleyin:</span><span class="sxs-lookup"><span data-stu-id="49465-123">Add multiple project references using a globbing pattern on Linux/Unix:</span></span>

  ```console
  dotnet add app/app.csproj reference **/*.csproj
  ```
