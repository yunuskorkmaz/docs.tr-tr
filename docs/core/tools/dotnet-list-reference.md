---
title: "DotNet listesi başvuru command - .NET Core CLI"
description: "Dotnet listesi başvuru komutu listesi proje için proje başvuruları için uygun bir seçenek sağlar."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: a4ceadb6d070d7997e75b472624bbe2c1650396d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="22caa-103">DotNet listesi başvurusu</span><span class="sxs-lookup"><span data-stu-id="22caa-103">dotnet list reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="22caa-104">Ad</span><span class="sxs-lookup"><span data-stu-id="22caa-104">Name</span></span>

<span data-ttu-id="22caa-105">`dotnet list reference`-Projeyi project başvurular listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="22caa-105">`dotnet list reference` - Lists project to project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="22caa-106">Özet</span><span class="sxs-lookup"><span data-stu-id="22caa-106">Synopsis</span></span>

`dotnet list [<PROJECT>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="22caa-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="22caa-107">Description</span></span>

<span data-ttu-id="22caa-108">`dotnet list reference` Komutu belirli bir projenin için liste proje başvuruları için uygun bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="22caa-108">The `dotnet list reference` command provides a convenient option to list project references for a given project.</span></span>

## <a name="arguments"></a><span data-ttu-id="22caa-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="22caa-109">Arguments</span></span>

`PROJECT`

<span data-ttu-id="22caa-110">Başvuruları listelemek için kullanılacak proje dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="22caa-110">Specifies the project file to use for listing references.</span></span> <span data-ttu-id="22caa-111">Belirtilmezse, komut bir proje dosyası için geçerli dizini arayın.</span><span class="sxs-lookup"><span data-stu-id="22caa-111">If not specified, the command will search the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="22caa-112">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="22caa-112">Options</span></span>

`-h|--help`

<span data-ttu-id="22caa-113">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="22caa-113">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="22caa-114">Örnekler</span><span class="sxs-lookup"><span data-stu-id="22caa-114">Examples</span></span>

<span data-ttu-id="22caa-115">Belirtilen proje için proje başvuruları listesi:</span><span class="sxs-lookup"><span data-stu-id="22caa-115">List the project references for the specified project:</span></span>

`dotnet list app/app.csproj reference`

<span data-ttu-id="22caa-116">Geçerli dizindeki proje için proje başvuruları listesi:</span><span class="sxs-lookup"><span data-stu-id="22caa-116">List the project references for the project in the current directory:</span></span>

`dotnet list reference`
