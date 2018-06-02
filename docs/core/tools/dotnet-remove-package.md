---
title: DotNet Paketi komutu - .NET Core CLI Kaldır
description: Dotnet Kaldır Paketi komutu NuGet paketi başvurusu projeye kaldırmak için uygun bir seçeneği sağlar.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: ed6086bfdfadaa06494c857fc74687f1273af971
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696864"
---
# <a name="dotnet-remove-package"></a><span data-ttu-id="970f3-103">DotNet Kaldır paketi</span><span class="sxs-lookup"><span data-stu-id="970f3-103">dotnet remove package</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="970f3-104">Ad</span><span class="sxs-lookup"><span data-stu-id="970f3-104">Name</span></span>

<span data-ttu-id="970f3-105">`dotnet remove package` -Paket başvuru proje dosyasından kaldırır.</span><span class="sxs-lookup"><span data-stu-id="970f3-105">`dotnet remove package` - Removes package reference from a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="970f3-106">Özet</span><span class="sxs-lookup"><span data-stu-id="970f3-106">Synopsis</span></span>

`dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]`

## <a name="description"></a><span data-ttu-id="970f3-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="970f3-107">Description</span></span>

<span data-ttu-id="970f3-108">`dotnet remove package` Komutu bir NuGet paketi başvurusu projeden kaldırmak için uygun bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="970f3-108">The `dotnet remove package` command provides a convenient option to remove a NuGet package reference from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="970f3-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="970f3-109">Arguments</span></span>

`PROJECT`

<span data-ttu-id="970f3-110">Proje dosyası belirtir.</span><span class="sxs-lookup"><span data-stu-id="970f3-110">Specifies the project file.</span></span> <span data-ttu-id="970f3-111">Belirtilmezse, komut için geçerli dizin arar.</span><span class="sxs-lookup"><span data-stu-id="970f3-111">If not specified, the command searches the current directory for one.</span></span>

`PACKAGE_NAME`

<span data-ttu-id="970f3-112">Kaldırılacak paket başvuru.</span><span class="sxs-lookup"><span data-stu-id="970f3-112">The package reference to remove.</span></span>

## <a name="options"></a><span data-ttu-id="970f3-113">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="970f3-113">Options</span></span>

`-h|--help`

<span data-ttu-id="970f3-114">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="970f3-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="970f3-115">Örnekler</span><span class="sxs-lookup"><span data-stu-id="970f3-115">Examples</span></span>

<span data-ttu-id="970f3-116">Kaldırır `Newtonsoft.Json` geçerli dizinde bir projeden NuGet paketi:</span><span class="sxs-lookup"><span data-stu-id="970f3-116">Removes `Newtonsoft.Json` NuGet package from a project in the current directory:</span></span>

`dotnet remove package Newtonsoft.Json`