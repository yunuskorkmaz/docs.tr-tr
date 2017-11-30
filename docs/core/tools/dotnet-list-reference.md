---
title: "DotNet listesi başvuru command - .NET Core CLI"
description: "Dotnet listesi başvuru komutu listesi proje için proje başvuruları için uygun bir seçenek sağlar."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: b3e903c15a7486faa279d47ad5e2e00c090b19af
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="d940a-103">DotNet listesi başvurusu</span><span class="sxs-lookup"><span data-stu-id="d940a-103">dotnet list reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="d940a-104">Ad</span><span class="sxs-lookup"><span data-stu-id="d940a-104">Name</span></span>

<span data-ttu-id="d940a-105">`dotnet list reference`-Projeyi project başvurular listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="d940a-105">`dotnet list reference` - Lists project to project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d940a-106">Özet</span><span class="sxs-lookup"><span data-stu-id="d940a-106">Synopsis</span></span>

`dotnet list [<PROJECT>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="d940a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d940a-107">Description</span></span>

<span data-ttu-id="d940a-108">`dotnet list reference` Komutu belirli bir projenin için liste proje başvuruları için uygun bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="d940a-108">The `dotnet list reference` command provides a convenient option to list project references for a given project.</span></span>

## <a name="arguments"></a><span data-ttu-id="d940a-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="d940a-109">Arguments</span></span>

`PROJECT`

<span data-ttu-id="d940a-110">Başvuruları listelemek için kullanılacak proje dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d940a-110">Specifies the project file to use for listing references.</span></span> <span data-ttu-id="d940a-111">Belirtilmezse, komut bir proje dosyası için geçerli dizini arayın.</span><span class="sxs-lookup"><span data-stu-id="d940a-111">If not specified, the command will search the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="d940a-112">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="d940a-112">Options</span></span>

`-h|--help`

<span data-ttu-id="d940a-113">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="d940a-113">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="d940a-114">Örnekler</span><span class="sxs-lookup"><span data-stu-id="d940a-114">Examples</span></span>

<span data-ttu-id="d940a-115">Belirtilen proje için proje başvuruları listesi:</span><span class="sxs-lookup"><span data-stu-id="d940a-115">List the project references for the specified project:</span></span>

`dotnet list app/app.csproj reference`

<span data-ttu-id="d940a-116">Geçerli dizindeki proje için proje başvuruları listesi:</span><span class="sxs-lookup"><span data-stu-id="d940a-116">List the project references for the project in the current directory:</span></span>

`dotnet list reference`
