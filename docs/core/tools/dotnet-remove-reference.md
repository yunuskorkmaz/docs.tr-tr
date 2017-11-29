---
title: "DotNet Kaldır başvuru command - .NET Core CLI"
description: "Dotnet Kaldır başvuru komutu proje için proje başvuruları kaldırmak için uygun bir seçenek sağlar."
keywords: "DotNet Kaldır, CLI, CLI komutu, .NET Core"
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 7cb84c2dc7fc4d16b00bd6459132390ab80131f3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-remove-reference"></a><span data-ttu-id="67c19-104">DotNet Kaldır başvurusu</span><span class="sxs-lookup"><span data-stu-id="67c19-104">dotnet remove reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="67c19-105">Ad</span><span class="sxs-lookup"><span data-stu-id="67c19-105">Name</span></span>

<span data-ttu-id="67c19-106">`dotnet remove reference`-Proje Proje başvuruları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="67c19-106">`dotnet remove reference` - Removes project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="67c19-107">Özet</span><span class="sxs-lookup"><span data-stu-id="67c19-107">Synopsis</span></span>

`dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a><span data-ttu-id="67c19-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="67c19-108">Description</span></span>

<span data-ttu-id="67c19-109">`dotnet remove reference` Komutu proje başvuruları bir projeden kaldırmak için uygun bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="67c19-109">The `dotnet remove reference` command provides a convenient option to remove project references from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="67c19-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="67c19-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="67c19-111">Hedef proje dosyası.</span><span class="sxs-lookup"><span data-stu-id="67c19-111">Target project file.</span></span> <span data-ttu-id="67c19-112">Belirtilmezse, komut için geçerli dizin arar.</span><span class="sxs-lookup"><span data-stu-id="67c19-112">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="67c19-113">Proje projesine (kaldırmak için P2P başvuruları.</span><span class="sxs-lookup"><span data-stu-id="67c19-113">Project to project (P2P references to remove.</span></span> <span data-ttu-id="67c19-114">Bir veya birden çok proje belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67c19-114">You can specify one or multiple projects.</span></span> <span data-ttu-id="67c19-115">[Glob desenleri](https://en.wikipedia.org/wiki/Glob_(programming)) UNIX/Linux tabanlı Terminal üzerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="67c19-115">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

## <a name="options"></a><span data-ttu-id="67c19-116">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="67c19-116">Options</span></span>

`-h|--help`

<span data-ttu-id="67c19-117">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="67c19-117">Prints out a short help for the command.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="67c19-118">Yalnızca belirli bir hedeflerken başvuru kaldırır [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="67c19-118">Removes the reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="67c19-119">Örnekler</span><span class="sxs-lookup"><span data-stu-id="67c19-119">Examples</span></span>

<span data-ttu-id="67c19-120">Proje başvurusu belirtilen projeden kaldırın:</span><span class="sxs-lookup"><span data-stu-id="67c19-120">Remove a project reference from the specified project:</span></span>

`dotnet remove app/app.csproj reference lib/lib.csproj`

<span data-ttu-id="67c19-121">Geçerli dizin projede birden çok proje başvuruları kaldırın:</span><span class="sxs-lookup"><span data-stu-id="67c19-121">Remove multiple project references from the project in the current directory:</span></span>

`dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj`

<span data-ttu-id="67c19-122">UNIX/Linux üzerinde glob desenini kullanarak birden çok proje başvuruları kaldırın:</span><span class="sxs-lookup"><span data-stu-id="67c19-122">Remove multiple project references using a glob pattern on Unix/Linux:</span></span>

`dotnet remove app/app.csproj reference **/*.csproj`
