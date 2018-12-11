---
title: DotNet-başvuru komut ekleme
description: Dotnet ekleyin başvuru komut projeden projeye başvurular eklemek için uygun bir seçenek sağlar.
ms.date: 12/04/2018
ms.openlocfilehash: 8df9fa3c9469f74b27a9cb8120936f03532b016c
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169777"
---
# <a name="dotnet-add-reference"></a><span data-ttu-id="dd013-103">DotNet-Başvuru Ekle</span><span class="sxs-lookup"><span data-stu-id="dd013-103">dotnet-add reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="dd013-104">Ad</span><span class="sxs-lookup"><span data-stu-id="dd013-104">Name</span></span>

<span data-ttu-id="dd013-105">`dotnet add reference` -Projeler (P2P) başvuruları ekler.</span><span class="sxs-lookup"><span data-stu-id="dd013-105">`dotnet add reference` - Adds project-to-project (P2P) references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="dd013-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="dd013-106">Synopsis</span></span>

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a><span data-ttu-id="dd013-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dd013-107">Description</span></span>

<span data-ttu-id="dd013-108">`dotnet add reference` Komutu, bir proje proje başvurular eklemek için uygun bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="dd013-108">The `dotnet add reference` command provides a convenient option to add project references to a project.</span></span> <span data-ttu-id="dd013-109">Komutu çalıştırdıktan sonra [ `<ProjectReference>` ](/visualstudio/msbuild/common-msbuild-project-items) öğeleri, proje dosyasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="dd013-109">After running the command, the [`<ProjectReference>`](/visualstudio/msbuild/common-msbuild-project-items) elements are added to the project file.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a><span data-ttu-id="dd013-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="dd013-110">Arguments</span></span>

* **`PROJECT`**

  <span data-ttu-id="dd013-111">Proje dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="dd013-111">Specifies the project file.</span></span> <span data-ttu-id="dd013-112">Belirtilmezse, komut için geçerli dizinde arar.</span><span class="sxs-lookup"><span data-stu-id="dd013-112">If not specified, the command searches the current directory for one.</span></span>

* **`PROJECT_REFERENCES`**

  <span data-ttu-id="dd013-113">Eklenecek proje proje (P2P) başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="dd013-113">Project-to-project (P2P) references to add.</span></span> <span data-ttu-id="dd013-114">Bir veya daha fazla proje belirtin.</span><span class="sxs-lookup"><span data-stu-id="dd013-114">Specify one or more projects.</span></span> <span data-ttu-id="dd013-115">[Glob desenleri](https://en.wikipedia.org/wiki/Glob_(programming)) UNIX/Linux tabanlı sistemlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="dd013-115">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux-based systems.</span></span>

## <a name="options"></a><span data-ttu-id="dd013-116">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="dd013-116">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="dd013-117">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="dd013-117">Prints out a short help for the command.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="dd013-118">Yalnızca belirli bir hedeflenirken proje başvuruları ekler [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="dd013-118">Adds project references only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="dd013-119">Örnekler</span><span class="sxs-lookup"><span data-stu-id="dd013-119">Examples</span></span>

* <span data-ttu-id="dd013-120">Bir proje başvurusu Ekle:</span><span class="sxs-lookup"><span data-stu-id="dd013-120">Add a project reference:</span></span>

  ```console
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

* <span data-ttu-id="dd013-121">Geçerli dizinde birden çok proje başvuruları projeye ekleyin:</span><span class="sxs-lookup"><span data-stu-id="dd013-121">Add multiple project references to the project in the current directory:</span></span>

  ```console
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

* <span data-ttu-id="dd013-122">Linux/UNIX Glob deseni kullanılarak birden çok proje başvurularını ekleyin:</span><span class="sxs-lookup"><span data-stu-id="dd013-122">Add multiple project references using a globbing pattern on Linux/Unix:</span></span>

  ```console
  dotnet add app/app.csproj reference **/*.csproj
  ```