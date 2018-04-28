---
title: DotNet Kaldır başvuru command - .NET Core CLI
description: Dotnet Kaldır başvuru komutu proje için proje başvuruları kaldırmak için uygun bir seçenek sağlar.
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 0b7fb2788ccc04b54bf02f0387141d501612c16d
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-remove-reference"></a><span data-ttu-id="4b1fc-103">DotNet Kaldır başvurusu</span><span class="sxs-lookup"><span data-stu-id="4b1fc-103">dotnet remove reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="4b1fc-104">Ad</span><span class="sxs-lookup"><span data-stu-id="4b1fc-104">Name</span></span>

<span data-ttu-id="4b1fc-105">`dotnet remove reference` -Proje Proje başvuruları kaldırır.</span><span class="sxs-lookup"><span data-stu-id="4b1fc-105">`dotnet remove reference` - Removes project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="4b1fc-106">Özet</span><span class="sxs-lookup"><span data-stu-id="4b1fc-106">Synopsis</span></span>

`dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a><span data-ttu-id="4b1fc-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b1fc-107">Description</span></span>

<span data-ttu-id="4b1fc-108">`dotnet remove reference` Komutu proje başvuruları bir projeden kaldırmak için uygun bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="4b1fc-108">The `dotnet remove reference` command provides a convenient option to remove project references from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="4b1fc-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="4b1fc-109">Arguments</span></span>

`PROJECT`

<span data-ttu-id="4b1fc-110">Hedef proje dosyası.</span><span class="sxs-lookup"><span data-stu-id="4b1fc-110">Target project file.</span></span> <span data-ttu-id="4b1fc-111">Belirtilmezse, komut için geçerli dizin arar.</span><span class="sxs-lookup"><span data-stu-id="4b1fc-111">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="4b1fc-112">Proje projesine (kaldırmak için P2P başvuruları.</span><span class="sxs-lookup"><span data-stu-id="4b1fc-112">Project to project (P2P references to remove.</span></span> <span data-ttu-id="4b1fc-113">Bir veya birden çok proje belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4b1fc-113">You can specify one or multiple projects.</span></span> <span data-ttu-id="4b1fc-114">[Glob desenleri](https://en.wikipedia.org/wiki/Glob_(programming)) UNIX/Linux tabanlı Terminal üzerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="4b1fc-114">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

## <a name="options"></a><span data-ttu-id="4b1fc-115">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="4b1fc-115">Options</span></span>

`-h|--help`

<span data-ttu-id="4b1fc-116">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="4b1fc-116">Prints out a short help for the command.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="4b1fc-117">Yalnızca belirli bir hedeflerken başvuru kaldırır [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="4b1fc-117">Removes the reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="4b1fc-118">Örnekler</span><span class="sxs-lookup"><span data-stu-id="4b1fc-118">Examples</span></span>

<span data-ttu-id="4b1fc-119">Proje başvurusu belirtilen projeden kaldırın:</span><span class="sxs-lookup"><span data-stu-id="4b1fc-119">Remove a project reference from the specified project:</span></span>

`dotnet remove app/app.csproj reference lib/lib.csproj`

<span data-ttu-id="4b1fc-120">Geçerli dizin projede birden çok proje başvuruları kaldırın:</span><span class="sxs-lookup"><span data-stu-id="4b1fc-120">Remove multiple project references from the project in the current directory:</span></span>

`dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj`

<span data-ttu-id="4b1fc-121">UNIX/Linux üzerinde glob desenini kullanarak birden çok proje başvuruları kaldırın:</span><span class="sxs-lookup"><span data-stu-id="4b1fc-121">Remove multiple project references using a glob pattern on Unix/Linux:</span></span>

`dotnet remove app/app.csproj reference **/*.csproj`
