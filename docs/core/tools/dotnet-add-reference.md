---
title: DotNet-başvuru komut - .NET Core CLI ekleme
description: Dotnet ekleyin başvuru komutu proje için proje başvuruları eklemek için uygun bir seçenek sağlar.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 3398d4dc7bf70eaadcdd92269dbd3b784079c22d
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696968"
---
# <a name="dotnet-add-reference"></a><span data-ttu-id="57a42-103">DotNet-Başvuru Ekle</span><span class="sxs-lookup"><span data-stu-id="57a42-103">dotnet-add reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="57a42-104">Ad</span><span class="sxs-lookup"><span data-stu-id="57a42-104">Name</span></span>

<span data-ttu-id="57a42-105">`dotnet add reference` -Proje Proje (P2P) başvuruları ekler.</span><span class="sxs-lookup"><span data-stu-id="57a42-105">`dotnet add reference` - Adds project-to-project (P2P) references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="57a42-106">Özet</span><span class="sxs-lookup"><span data-stu-id="57a42-106">Synopsis</span></span>

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a><span data-ttu-id="57a42-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57a42-107">Description</span></span>

<span data-ttu-id="57a42-108">`dotnet add reference` Komutu proje başvuruları bir proje eklemek için uygun bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="57a42-108">The `dotnet add reference` command provides a convenient option to add project references to a project.</span></span> <span data-ttu-id="57a42-109">Komutu çalıştırdıktan sonra [ `<ProjectReference>` ](/visualstudio/msbuild/common-msbuild-project-items) öğeleri proje dosyasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="57a42-109">After running the command, the [`<ProjectReference>`](/visualstudio/msbuild/common-msbuild-project-items) elements are added to the project file.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a><span data-ttu-id="57a42-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="57a42-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="57a42-111">Proje dosyası belirtir.</span><span class="sxs-lookup"><span data-stu-id="57a42-111">Specifies the project file.</span></span> <span data-ttu-id="57a42-112">Belirtilmezse, komut için geçerli dizin arar.</span><span class="sxs-lookup"><span data-stu-id="57a42-112">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="57a42-113">Eklemek için proje proje (P2P) başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="57a42-113">Project-to-project (P2P) references to add.</span></span> <span data-ttu-id="57a42-114">Bir veya daha fazla projeleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="57a42-114">Specify one or more projects.</span></span> <span data-ttu-id="57a42-115">[Glob desenleri](https://en.wikipedia.org/wiki/Glob_(programming)) UNIX/Linux tabanlı sistemlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="57a42-115">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux-based systems.</span></span>

## <a name="options"></a><span data-ttu-id="57a42-116">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="57a42-116">Options</span></span>

`-h|--help`

<span data-ttu-id="57a42-117">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="57a42-117">Prints out a short help for the command.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="57a42-118">Proje başvuruları yalnızca belirli bir hedeflerken ekler [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="57a42-118">Adds project references only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="57a42-119">Örnekler</span><span class="sxs-lookup"><span data-stu-id="57a42-119">Examples</span></span>

<span data-ttu-id="57a42-120">Proje başvurusu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="57a42-120">Add a project reference:</span></span>

`dotnet add app/app.csproj reference lib/lib.csproj`

<span data-ttu-id="57a42-121">Birden çok proje başvuruları projeye geçerli dizinde ekleyin:</span><span class="sxs-lookup"><span data-stu-id="57a42-121">Add multiple project references to the project in the current directory:</span></span>

`dotnet add reference lib1/lib1.csproj lib2/lib2.csproj`

<span data-ttu-id="57a42-122">Linux/Unix üzerinde genelleme desenini kullanarak birden çok proje başvurularını ekleyin:</span><span class="sxs-lookup"><span data-stu-id="57a42-122">Add multiple project references using a globbing pattern on Linux/Unix:</span></span>

`dotnet add app/app.csproj reference **/*.csproj`
