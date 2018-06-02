---
title: DotNet Kaldır başvuru command - .NET Core CLI
description: Dotnet Kaldır başvuru komutu proje için proje başvuruları kaldırmak için uygun bir seçenek sağlar.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: b281b255be7f49a99a6b4928c340cd4fb085f085
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696237"
---
# <a name="dotnet-remove-reference"></a><span data-ttu-id="cb971-103">DotNet Kaldır başvurusu</span><span class="sxs-lookup"><span data-stu-id="cb971-103">dotnet remove reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="cb971-104">Ad</span><span class="sxs-lookup"><span data-stu-id="cb971-104">Name</span></span>

<span data-ttu-id="cb971-105">`dotnet remove reference` -Proje Proje başvuruları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="cb971-105">`dotnet remove reference` - Removes project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="cb971-106">Özet</span><span class="sxs-lookup"><span data-stu-id="cb971-106">Synopsis</span></span>

`dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a><span data-ttu-id="cb971-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb971-107">Description</span></span>

<span data-ttu-id="cb971-108">`dotnet remove reference` Komutu proje başvuruları bir projeden kaldırmak için uygun bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="cb971-108">The `dotnet remove reference` command provides a convenient option to remove project references from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="cb971-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="cb971-109">Arguments</span></span>

`PROJECT`

<span data-ttu-id="cb971-110">Hedef proje dosyası.</span><span class="sxs-lookup"><span data-stu-id="cb971-110">Target project file.</span></span> <span data-ttu-id="cb971-111">Belirtilmezse, komut için geçerli dizin arar.</span><span class="sxs-lookup"><span data-stu-id="cb971-111">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="cb971-112">Kaldırmak için proje proje (P2P) başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="cb971-112">Project-to-project (P2P) references to remove.</span></span> <span data-ttu-id="cb971-113">Bir veya birden çok proje belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cb971-113">You can specify one or multiple projects.</span></span> <span data-ttu-id="cb971-114">[Glob desenleri](https://en.wikipedia.org/wiki/Glob_(programming)) UNIX/Linux tabanlı Terminal üzerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="cb971-114">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

## <a name="options"></a><span data-ttu-id="cb971-115">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="cb971-115">Options</span></span>

`-h|--help`

<span data-ttu-id="cb971-116">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="cb971-116">Prints out a short help for the command.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="cb971-117">Yalnızca belirli bir hedeflerken başvuru kaldırır [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="cb971-117">Removes the reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="cb971-118">Örnekler</span><span class="sxs-lookup"><span data-stu-id="cb971-118">Examples</span></span>

<span data-ttu-id="cb971-119">Proje başvurusu belirtilen projeden kaldırın:</span><span class="sxs-lookup"><span data-stu-id="cb971-119">Remove a project reference from the specified project:</span></span>

`dotnet remove app/app.csproj reference lib/lib.csproj`

<span data-ttu-id="cb971-120">Geçerli dizin projede birden çok proje başvuruları kaldırın:</span><span class="sxs-lookup"><span data-stu-id="cb971-120">Remove multiple project references from the project in the current directory:</span></span>

`dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj`

<span data-ttu-id="cb971-121">UNIX/Linux üzerinde glob desenini kullanarak birden çok proje başvuruları kaldırın:</span><span class="sxs-lookup"><span data-stu-id="cb971-121">Remove multiple project references using a glob pattern on Unix/Linux:</span></span>

`dotnet remove app/app.csproj reference **/*.csproj`
