---
title: DotNet Paketi komutu Kaldır
description: Dotnet remove paket komutu bir proje için NuGet paket başvuruyu kaldırmak için kullanışlı bir seçenek sağlar.
ms.date: 05/29/2018
ms.openlocfilehash: cbdeacff78ef20c9a73010e10a771a724b23792e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632430"
---
# <a name="dotnet-remove-package"></a><span data-ttu-id="be35f-103">DotNet Kaldır paket</span><span class="sxs-lookup"><span data-stu-id="be35f-103">dotnet remove package</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="be35f-104">Ad</span><span class="sxs-lookup"><span data-stu-id="be35f-104">Name</span></span>

<span data-ttu-id="be35f-105">`dotnet remove package` -Paket başvurusu proje dosyasından kaldırır.</span><span class="sxs-lookup"><span data-stu-id="be35f-105">`dotnet remove package` - Removes package reference from a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="be35f-106">Synopsis</span><span class="sxs-lookup"><span data-stu-id="be35f-106">Synopsis</span></span>

`dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]`

## <a name="description"></a><span data-ttu-id="be35f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="be35f-107">Description</span></span>

<span data-ttu-id="be35f-108">`dotnet remove package` Komutu bir projeden NuGet paketi başvuruyu kaldırmak için kullanışlı bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="be35f-108">The `dotnet remove package` command provides a convenient option to remove a NuGet package reference from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="be35f-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="be35f-109">Arguments</span></span>

`PROJECT`

<span data-ttu-id="be35f-110">Proje dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="be35f-110">Specifies the project file.</span></span> <span data-ttu-id="be35f-111">Belirtilmezse, komut için geçerli dizinde arar.</span><span class="sxs-lookup"><span data-stu-id="be35f-111">If not specified, the command searches the current directory for one.</span></span>

`PACKAGE_NAME`

<span data-ttu-id="be35f-112">Kaldırmak için paket başvurusu.</span><span class="sxs-lookup"><span data-stu-id="be35f-112">The package reference to remove.</span></span>

## <a name="options"></a><span data-ttu-id="be35f-113">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="be35f-113">Options</span></span>

`-h|--help`

<span data-ttu-id="be35f-114">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="be35f-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="be35f-115">Örnekler</span><span class="sxs-lookup"><span data-stu-id="be35f-115">Examples</span></span>

<span data-ttu-id="be35f-116">Kaldırır `Newtonsoft.Json` geçerli dizindeki bir projeden NuGet paketi:</span><span class="sxs-lookup"><span data-stu-id="be35f-116">Removes `Newtonsoft.Json` NuGet package from a project in the current directory:</span></span>

`dotnet remove package Newtonsoft.Json`
