---
title: DotNet araç Listele komutu - .NET Core CLI
description: Dotnet araç Listele komutu belirtilen .NET Core genel aracı makinenizden listeler.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 5f4793cd37c3a8df06eb6930ad9f381ac70d4e67
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696731"
---
# <a name="dotnet-tool-list"></a><span data-ttu-id="7f0de-103">DotNet araç listesi</span><span class="sxs-lookup"><span data-stu-id="7f0de-103">dotnet tool list</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="7f0de-104">Ad</span><span class="sxs-lookup"><span data-stu-id="7f0de-104">Name</span></span>

<span data-ttu-id="7f0de-105">`dotnet tool list` -Tüm listeler [.NET Core genel Araçları](global-tools.md) makinenizde varsayılan dizin veya belirtilen yol şu anda yüklü.</span><span class="sxs-lookup"><span data-stu-id="7f0de-105">`dotnet tool list` - Lists all [.NET Core Global Tools](global-tools.md) currently installed in the default directory on your machine or in the specified path.</span></span>

## <a name="synopsis"></a><span data-ttu-id="7f0de-106">Özet</span><span class="sxs-lookup"><span data-stu-id="7f0de-106">Synopsis</span></span>

```
dotnet tool list <-g|--global>
dotnet tool list <--tool-path>
dotnet tool list <-h|--help>
```

## <a name="description"></a><span data-ttu-id="7f0de-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7f0de-107">Description</span></span>

<span data-ttu-id="7f0de-108">`dotnet tool list` Komutu makinenizde (geçerli kullanıcı profili) veya belirtilen yoldaki tüm .NET Core genel araçları listelemek bir yol yüklü kullanıcı genelinde sağlar.</span><span class="sxs-lookup"><span data-stu-id="7f0de-108">The `dotnet tool list` command provides a way for you to list all .NET Core Global Tools installed user-wide on your machine (current user profile) or in the specified path.</span></span> <span data-ttu-id="7f0de-109">Komut, paket adı, yüklü sürümü ve genel aracı komut listeler.</span><span class="sxs-lookup"><span data-stu-id="7f0de-109">The command lists the package name, version installed, and the Global Tool command.</span></span> <span data-ttu-id="7f0de-110">List komutunu kullanmak için ya da tüm kullanıcı genelinde araçları kullanarak görmek istediğiniz belirtmek zorunda `--global` seçeneği veya bir özel yolu kullanarak belirtin `--tool-path` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="7f0de-110">To use the list command, you either have to specify that you want to see all user-wide tools using the `--global` option or specify a custom path using the `--tool-path` option.</span></span>

## <a name="options"></a><span data-ttu-id="7f0de-111">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="7f0de-111">Options</span></span>

`-g|--global`

<span data-ttu-id="7f0de-112">Kullanıcı genelinde genel araçları listeler.</span><span class="sxs-lookup"><span data-stu-id="7f0de-112">Lists user-wide Global Tools.</span></span> <span data-ttu-id="7f0de-113">Birleştirilemez `--tool-path` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="7f0de-113">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="7f0de-114">Bu seçeneği belirtmezseniz, belirtmeniz gerekir `--tool-path` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="7f0de-114">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="7f0de-115">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="7f0de-115">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="7f0de-116">Özel bir konuma genel araçları nerede bulabileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7f0de-116">Specifies a custom location where to find Global Tools.</span></span> <span data-ttu-id="7f0de-117">YOL, mutlak veya göreli olabilir.</span><span class="sxs-lookup"><span data-stu-id="7f0de-117">PATH can be absolute or relative.</span></span> <span data-ttu-id="7f0de-118">Birleştirilemez `--global` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="7f0de-118">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="7f0de-119">Bu seçeneği belirtmezseniz, belirtmeniz gerekir `--global` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="7f0de-119">If you don't specify this option, you must specify the `--global` option.</span></span>

## <a name="examples"></a><span data-ttu-id="7f0de-120">Örnekler</span><span class="sxs-lookup"><span data-stu-id="7f0de-120">Examples</span></span>

<span data-ttu-id="7f0de-121">Tüm makinenizde (geçerli kullanıcı profili) genel araçlarının yüklü kullanıcı genelinde listeler:</span><span class="sxs-lookup"><span data-stu-id="7f0de-121">Lists all Global Tools installed user-wide on your machine (current user profile):</span></span>

`dotnet tool list -g`

<span data-ttu-id="7f0de-122">Belirli bir Windows klasörden genel araçları listeler:</span><span class="sxs-lookup"><span data-stu-id="7f0de-122">Lists the Global Tools from a specific Windows folder:</span></span>

`dotnet tool list --tool-path c:\global-tools`

<span data-ttu-id="7f0de-123">Belirli bir Linux/macOS klasörden genel araçları listeler:</span><span class="sxs-lookup"><span data-stu-id="7f0de-123">Lists the Global Tools from a specific Linux/macOS folder:</span></span>

`dotnet tool list --tool-path ~/bin`

## <a name="see-also"></a><span data-ttu-id="7f0de-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f0de-124">See also</span></span>

[<span data-ttu-id="7f0de-125">.NET core genel araçları</span><span class="sxs-lookup"><span data-stu-id="7f0de-125">.NET Core Global Tools</span></span>](global-tools.md)