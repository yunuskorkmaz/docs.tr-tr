---
title: DotNet Kaldır başvuru komutu
description: Dotnet remove başvuru komutu, projeden projeye başvuruları kaldırmak için kullanışlı bir seçenek sağlar.
ms.date: 05/29/2018
ms.openlocfilehash: bfac4721743babcf48fd8e86a50c8df136e1bfce
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170619"
---
# <a name="dotnet-remove-reference"></a><span data-ttu-id="b4e79-103">DotNet başvuru Kaldır</span><span class="sxs-lookup"><span data-stu-id="b4e79-103">dotnet remove reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="b4e79-104">Ad</span><span class="sxs-lookup"><span data-stu-id="b4e79-104">Name</span></span>

<span data-ttu-id="b4e79-105">`dotnet remove reference` -Projeden projeye başvurular kaldırır.</span><span class="sxs-lookup"><span data-stu-id="b4e79-105">`dotnet remove reference` - Removes project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b4e79-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="b4e79-106">Synopsis</span></span>

`dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a><span data-ttu-id="b4e79-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b4e79-107">Description</span></span>

<span data-ttu-id="b4e79-108">`dotnet remove reference` Komutu bir projeden projeye başvuruları kaldırmak için kullanışlı bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="b4e79-108">The `dotnet remove reference` command provides a convenient option to remove project references from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="b4e79-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="b4e79-109">Arguments</span></span>

`PROJECT`

<span data-ttu-id="b4e79-110">Hedef proje dosyası.</span><span class="sxs-lookup"><span data-stu-id="b4e79-110">Target project file.</span></span> <span data-ttu-id="b4e79-111">Belirtilmezse, komut için geçerli dizinde arar.</span><span class="sxs-lookup"><span data-stu-id="b4e79-111">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="b4e79-112">Projeden projeye (P2P) kaldırmak için başvurur.</span><span class="sxs-lookup"><span data-stu-id="b4e79-112">Project-to-project (P2P) references to remove.</span></span> <span data-ttu-id="b4e79-113">Bir veya birden çok proje belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b4e79-113">You can specify one or multiple projects.</span></span> <span data-ttu-id="b4e79-114">[Glob desenleri](https://en.wikipedia.org/wiki/Glob_(programming)) UNIX/Linux tabanlı terminaller üzerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="b4e79-114">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

## <a name="options"></a><span data-ttu-id="b4e79-115">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="b4e79-115">Options</span></span>

`-h|--help`

<span data-ttu-id="b4e79-116">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="b4e79-116">Prints out a short help for the command.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="b4e79-117">Yalnızca belirli bir hedeflenirken başvuruyu kaldırır [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="b4e79-117">Removes the reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="b4e79-118">Örnekler</span><span class="sxs-lookup"><span data-stu-id="b4e79-118">Examples</span></span>

<span data-ttu-id="b4e79-119">Bir proje başvurusu belirtilen projeden kaldır:</span><span class="sxs-lookup"><span data-stu-id="b4e79-119">Remove a project reference from the specified project:</span></span>

`dotnet remove app/app.csproj reference lib/lib.csproj`

<span data-ttu-id="b4e79-120">Geçerli dizindeki bir projeden birden çok proje başvuruları kaldırın:</span><span class="sxs-lookup"><span data-stu-id="b4e79-120">Remove multiple project references from the project in the current directory:</span></span>

`dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj`

<span data-ttu-id="b4e79-121">UNIX/Linux üzerinde bir glob deseni kullanılarak birden çok proje başvuruları kaldırın:</span><span class="sxs-lookup"><span data-stu-id="b4e79-121">Remove multiple project references using a glob pattern on Unix/Linux:</span></span>

`dotnet remove app/app.csproj reference **/*.csproj`
