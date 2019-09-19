---
title: DotNet araç listesi komutu
description: DotNet araç listesi komutu, makinenizden belirtilen .NET Core küresel aracını listeler.
ms.date: 05/29/2018
ms.openlocfilehash: 6d35b1dce0c6d57edb0c6dd5f9711f093bc804aa
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117556"
---
# <a name="dotnet-tool-list"></a><span data-ttu-id="a9e57-103">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="a9e57-103">dotnet tool list</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="a9e57-104">Ad</span><span class="sxs-lookup"><span data-stu-id="a9e57-104">Name</span></span>

<span data-ttu-id="a9e57-105">`dotnet tool list`-Makinenizde varsayılan dizinde veya belirtilen yolda yüklü olan tüm [.NET Core genel araçlarını](global-tools.md) listeler.</span><span class="sxs-lookup"><span data-stu-id="a9e57-105">`dotnet tool list` - Lists all [.NET Core Global Tools](global-tools.md) currently installed in the default directory on your machine or in the specified path.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a9e57-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="a9e57-106">Synopsis</span></span>

```dotnetcli
dotnet tool list <-g|--global>
dotnet tool list <--tool-path>
dotnet tool list <-h|--help>
```

## <a name="description"></a><span data-ttu-id="a9e57-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a9e57-107">Description</span></span>

<span data-ttu-id="a9e57-108">Komut `dotnet tool list` , Kullanıcı genelinde yüklü olan tüm .NET Core genel araçlarını makinenizde (geçerli kullanıcı profili) veya belirtilen yolda listeetmeniz için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="a9e57-108">The `dotnet tool list` command provides a way for you to list all .NET Core Global Tools installed user-wide on your machine (current user profile) or in the specified path.</span></span> <span data-ttu-id="a9e57-109">Komut, paket adını, yüklü sürümü ve genel araç komutunu listeler.</span><span class="sxs-lookup"><span data-stu-id="a9e57-109">The command lists the package name, version installed, and the Global Tool command.</span></span> <span data-ttu-id="a9e57-110">List komutunu kullanmak için, `--global` seçeneğini kullanarak tüm Kullanıcı genelindeki araçları görmek istediğinizi veya `--tool-path` seçeneğini kullanarak özel bir yol belirtmeyi belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a9e57-110">To use the list command, you either have to specify that you want to see all user-wide tools using the `--global` option or specify a custom path using the `--tool-path` option.</span></span>

## <a name="options"></a><span data-ttu-id="a9e57-111">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="a9e57-111">Options</span></span>

`-g|--global`

<span data-ttu-id="a9e57-112">Kullanıcı genelindeki genel araçları listeler.</span><span class="sxs-lookup"><span data-stu-id="a9e57-112">Lists user-wide Global Tools.</span></span> <span data-ttu-id="a9e57-113">`--tool-path` Seçeneğiyle birleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="a9e57-113">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="a9e57-114">Bu seçeneği belirtmezseniz, `--tool-path` seçeneğini belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a9e57-114">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="a9e57-115">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="a9e57-115">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="a9e57-116">Genel araçların bulunacağı bir özel konum belirtir.</span><span class="sxs-lookup"><span data-stu-id="a9e57-116">Specifies a custom location where to find Global Tools.</span></span> <span data-ttu-id="a9e57-117">YOL mutlak veya göreli olabilir.</span><span class="sxs-lookup"><span data-stu-id="a9e57-117">PATH can be absolute or relative.</span></span> <span data-ttu-id="a9e57-118">`--global` Seçeneğiyle birleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="a9e57-118">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="a9e57-119">Bu seçeneği belirtmezseniz, `--global` seçeneğini belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a9e57-119">If you don't specify this option, you must specify the `--global` option.</span></span>

## <a name="examples"></a><span data-ttu-id="a9e57-120">Örnekler</span><span class="sxs-lookup"><span data-stu-id="a9e57-120">Examples</span></span>

<span data-ttu-id="a9e57-121">Makinenizde Kullanıcı genelinde yüklenen tüm genel araçları listeler (geçerli kullanıcı profili):</span><span class="sxs-lookup"><span data-stu-id="a9e57-121">Lists all Global Tools installed user-wide on your machine (current user profile):</span></span>

`dotnet tool list -g`

<span data-ttu-id="a9e57-122">Belirli bir Windows klasöründen genel araçları listeler:</span><span class="sxs-lookup"><span data-stu-id="a9e57-122">Lists the Global Tools from a specific Windows folder:</span></span>

`dotnet tool list --tool-path c:\global-tools`

<span data-ttu-id="a9e57-123">Belirli bir Linux/macOS klasöründen genel araçları listeler:</span><span class="sxs-lookup"><span data-stu-id="a9e57-123">Lists the Global Tools from a specific Linux/macOS folder:</span></span>

`dotnet tool list --tool-path ~/bin`

## <a name="see-also"></a><span data-ttu-id="a9e57-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9e57-124">See also</span></span>

- [<span data-ttu-id="a9e57-125">.NET Core küresel araçları</span><span class="sxs-lookup"><span data-stu-id="a9e57-125">.NET Core Global Tools</span></span>](global-tools.md)
