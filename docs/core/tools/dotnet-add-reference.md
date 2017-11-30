---
title: "DotNet-başvuru komut - .NET Core CLI ekleme"
description: "Dotnet ekleyin başvuru komutu proje için proje başvuruları eklemek için uygun bir seçenek sağlar."
author: mairaw
ms.author: mairaw
ms.date: 09/19/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 9c6b0f434a9d6b1431e375ec6a437497aaddfc61
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-add-reference"></a><span data-ttu-id="07b1f-103">DotNet-Başvuru Ekle</span><span class="sxs-lookup"><span data-stu-id="07b1f-103">dotnet-add reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="07b1f-104">Ad</span><span class="sxs-lookup"><span data-stu-id="07b1f-104">Name</span></span>

<span data-ttu-id="07b1f-105">`dotnet add reference`-Proje Proje (P2P) başvuruları ekler.</span><span class="sxs-lookup"><span data-stu-id="07b1f-105">`dotnet add reference` - Adds project-to-project (P2P) references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="07b1f-106">Özet</span><span class="sxs-lookup"><span data-stu-id="07b1f-106">Synopsis</span></span>

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a><span data-ttu-id="07b1f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="07b1f-107">Description</span></span>

<span data-ttu-id="07b1f-108">`dotnet add reference` Komutu proje başvuruları bir proje eklemek için uygun bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="07b1f-108">The `dotnet add reference` command provides a convenient option to add project references to a project.</span></span> <span data-ttu-id="07b1f-109">Komutu çalıştırdıktan sonra [ `<ProjectReference>` ](/visualstudio/msbuild/common-msbuild-project-items) öğeleri proje dosyasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="07b1f-109">After running the command, the [`<ProjectReference>`](/visualstudio/msbuild/common-msbuild-project-items) elements are added to the project file.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a><span data-ttu-id="07b1f-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="07b1f-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="07b1f-111">Proje dosyası belirtir.</span><span class="sxs-lookup"><span data-stu-id="07b1f-111">Specifies the project file.</span></span> <span data-ttu-id="07b1f-112">Belirtilmezse, komut için geçerli dizin arar.</span><span class="sxs-lookup"><span data-stu-id="07b1f-112">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="07b1f-113">Eklemek için proje proje (P2P) başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="07b1f-113">Project-to-project (P2P) references to add.</span></span> <span data-ttu-id="07b1f-114">Bir veya daha fazla projeleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="07b1f-114">Specify one or more projects.</span></span> <span data-ttu-id="07b1f-115">[Glob desenleri](https://en.wikipedia.org/wiki/Glob_(programming)) UNIX/Linux tabanlı sistemlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="07b1f-115">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux-based systems.</span></span>

## <a name="options"></a><span data-ttu-id="07b1f-116">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="07b1f-116">Options</span></span>

`-h|--help`

<span data-ttu-id="07b1f-117">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="07b1f-117">Prints out a short help for the command.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="07b1f-118">Proje başvuruları yalnızca belirli bir hedeflerken ekler [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="07b1f-118">Adds project references only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="07b1f-119">Örnekler</span><span class="sxs-lookup"><span data-stu-id="07b1f-119">Examples</span></span>

<span data-ttu-id="07b1f-120">Proje başvurusu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="07b1f-120">Add a project reference:</span></span>

`dotnet add app/app.csproj reference lib/lib.csproj`

<span data-ttu-id="07b1f-121">Birden çok proje başvuruları projeye geçerli dizinde ekleyin:</span><span class="sxs-lookup"><span data-stu-id="07b1f-121">Add multiple project references to the project in the current directory:</span></span>

`dotnet add reference lib1/lib1.csproj lib2/lib2.csproj`

<span data-ttu-id="07b1f-122">Linux/Unix üzerinde genelleme desenini kullanarak birden çok proje başvurularını ekleyin:</span><span class="sxs-lookup"><span data-stu-id="07b1f-122">Add multiple project references using a globbing pattern on Linux/Unix:</span></span>

`dotnet add app/app.csproj reference **/*.csproj`
