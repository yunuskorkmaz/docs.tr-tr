---
title: DotNet araç Listele komutu
description: Belirtilen .NET Core genel aracı makinenizden dotnet araç Listele komutu listelenmektedir.
ms.date: 05/29/2018
ms.openlocfilehash: 0c17534beb80ed87a8f260342b0f82882a9e17b6
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169774"
---
# <a name="dotnet-tool-list"></a><span data-ttu-id="cf227-103">DotNet araç listesi</span><span class="sxs-lookup"><span data-stu-id="cf227-103">dotnet tool list</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="cf227-104">Ad</span><span class="sxs-lookup"><span data-stu-id="cf227-104">Name</span></span>

<span data-ttu-id="cf227-105">`dotnet tool list` -Tüm listeler [.NET Core Araçları Genel](global-tools.md) makinenizde varsayılan dizinde veya belirtilen yolun şu anda yüklü.</span><span class="sxs-lookup"><span data-stu-id="cf227-105">`dotnet tool list` - Lists all [.NET Core Global Tools](global-tools.md) currently installed in the default directory on your machine or in the specified path.</span></span>

## <a name="synopsis"></a><span data-ttu-id="cf227-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="cf227-106">Synopsis</span></span>

```console
dotnet tool list <-g|--global>
dotnet tool list <--tool-path>
dotnet tool list <-h|--help>
```

## <a name="description"></a><span data-ttu-id="cf227-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cf227-107">Description</span></span>

<span data-ttu-id="cf227-108">`dotnet tool list` Komut makinenizde (geçerli kullanıcı profili) veya belirtilen yolda yüklü kullanıcı genelinde tüm .NET Core genel araçları listelemek bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf227-108">The `dotnet tool list` command provides a way for you to list all .NET Core Global Tools installed user-wide on your machine (current user profile) or in the specified path.</span></span> <span data-ttu-id="cf227-109">Komut, paket adı, sürümü ve genel aracı komut listeler.</span><span class="sxs-lookup"><span data-stu-id="cf227-109">The command lists the package name, version installed, and the Global Tool command.</span></span> <span data-ttu-id="cf227-110">LIST komutu kullanmak için ya da tüm kullanıcı genelinde araçları kullanarak görmek istediğinizi belirtmek olması `--global` kullanarak bir özel yol belirtin veya seçeneği `--tool-path` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="cf227-110">To use the list command, you either have to specify that you want to see all user-wide tools using the `--global` option or specify a custom path using the `--tool-path` option.</span></span>

## <a name="options"></a><span data-ttu-id="cf227-111">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="cf227-111">Options</span></span>

`-g|--global`

<span data-ttu-id="cf227-112">Kullanıcı genelinde genel araçları listeler.</span><span class="sxs-lookup"><span data-stu-id="cf227-112">Lists user-wide Global Tools.</span></span> <span data-ttu-id="cf227-113">İle birleştirilemez `--tool-path` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="cf227-113">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="cf227-114">Bu seçeneği belirtmezseniz, belirtmeniz gerekir `--tool-path` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="cf227-114">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="cf227-115">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="cf227-115">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="cf227-116">Özel bir konuma genel Araçlar nerede bulacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="cf227-116">Specifies a custom location where to find Global Tools.</span></span> <span data-ttu-id="cf227-117">YOL mutlak veya göreli olabilir.</span><span class="sxs-lookup"><span data-stu-id="cf227-117">PATH can be absolute or relative.</span></span> <span data-ttu-id="cf227-118">İle birleştirilemez `--global` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="cf227-118">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="cf227-119">Bu seçeneği belirtmezseniz, belirtmeniz gerekir `--global` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="cf227-119">If you don't specify this option, you must specify the `--global` option.</span></span>

## <a name="examples"></a><span data-ttu-id="cf227-120">Örnekler</span><span class="sxs-lookup"><span data-stu-id="cf227-120">Examples</span></span>

<span data-ttu-id="cf227-121">Tüm makinenizde (geçerli kullanıcı profili) genel araçları yüklü kullanıcı genelinde listeler:</span><span class="sxs-lookup"><span data-stu-id="cf227-121">Lists all Global Tools installed user-wide on your machine (current user profile):</span></span>

`dotnet tool list -g`

<span data-ttu-id="cf227-122">Belirli bir Windows klasörü genel araçları listeler:</span><span class="sxs-lookup"><span data-stu-id="cf227-122">Lists the Global Tools from a specific Windows folder:</span></span>

`dotnet tool list --tool-path c:\global-tools`

<span data-ttu-id="cf227-123">Belirli Linux/macOS klasöründe bulunan genel araçlarını listeler:</span><span class="sxs-lookup"><span data-stu-id="cf227-123">Lists the Global Tools from a specific Linux/macOS folder:</span></span>

`dotnet tool list --tool-path ~/bin`

## <a name="see-also"></a><span data-ttu-id="cf227-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf227-124">See also</span></span>

* [<span data-ttu-id="cf227-125">.NET core Araçları Genel</span><span class="sxs-lookup"><span data-stu-id="cf227-125">.NET Core Global Tools</span></span>](global-tools.md)