---
title: dotnet araç listesi komutu
description: Dotnet araç listesi komutu, makinenize yüklenen .NET Core araçlarını listeler.
ms.date: 02/14/2020
ms.openlocfilehash: 28f9155407d1238f8b0960b69b34ea329ca0e8e6
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463355"
---
# <a name="dotnet-tool-list"></a><span data-ttu-id="c4fad-103">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="c4fad-103">dotnet tool list</span></span>

<span data-ttu-id="c4fad-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.1 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="c4fad-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="c4fad-105">Adı</span><span class="sxs-lookup"><span data-stu-id="c4fad-105">Name</span></span>

<span data-ttu-id="c4fad-106">`dotnet tool list`- Şu anda makinenizde yüklü olan belirtilen türdeki tüm [.NET Core araçlarını](global-tools.md) listeler.</span><span class="sxs-lookup"><span data-stu-id="c4fad-106">`dotnet tool list` - Lists all [.NET Core tools](global-tools.md) of the specified type currently installed on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c4fad-107">Özet</span><span class="sxs-lookup"><span data-stu-id="c4fad-107">Synopsis</span></span>

```dotnetcli
dotnet tool list -g|--global

dotnet tool list --tool-path <PATH>

dotnet tool list

dotnet tool list -h|--help
```

## <a name="description"></a><span data-ttu-id="c4fad-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c4fad-108">Description</span></span>

<span data-ttu-id="c4fad-109">Komut, `dotnet tool list` makinenizde yüklü olan tüm .NET Core global, araç yolu veya yerel Araçları listele etmeniz için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="c4fad-109">The `dotnet tool list` command provides a way for you to list all .NET Core global, tool-path, or local Tools installed on your machine.</span></span> <span data-ttu-id="c4fad-110">Komut, paket adını, yüklenen sürümü ve araç komutunu listeler.</span><span class="sxs-lookup"><span data-stu-id="c4fad-110">The command lists the package name, version installed, and the tool command.</span></span>  <span data-ttu-id="c4fad-111">Komutu kullanmak için aşağıdakilerden birini belirtin:</span><span class="sxs-lookup"><span data-stu-id="c4fad-111">To use the command, you specify one of the following:</span></span>

* <span data-ttu-id="c4fad-112">Varsayılan konuma yüklenen genel bir araç.</span><span class="sxs-lookup"><span data-stu-id="c4fad-112">A global tool installed in the default location.</span></span> <span data-ttu-id="c4fad-113">`--global` Seçeneği kullanma</span><span class="sxs-lookup"><span data-stu-id="c4fad-113">Use the `--global` option</span></span>
* <span data-ttu-id="c4fad-114">Özel bir konuma yüklenen genel bir araç.</span><span class="sxs-lookup"><span data-stu-id="c4fad-114">A global tool installed in a custom location.</span></span> <span data-ttu-id="c4fad-115">`--tool-path` Seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="c4fad-115">Use the `--tool-path` option.</span></span>
* <span data-ttu-id="c4fad-116">Yerel bir araç.</span><span class="sxs-lookup"><span data-stu-id="c4fad-116">A local tool.</span></span> <span data-ttu-id="c4fad-117">Ve `--tool-path` seçenekleri `--global` atla.</span><span class="sxs-lookup"><span data-stu-id="c4fad-117">Omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="c4fad-118">**Yerel araçlar .NET Core SDK 3.0 ile başlayarak kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="c4fad-118">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="options"></a><span data-ttu-id="c4fad-119">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="c4fad-119">Options</span></span>

- **`-g|--global`**

  <span data-ttu-id="c4fad-120">Kullanıcı çapında genel araçları listeler.</span><span class="sxs-lookup"><span data-stu-id="c4fad-120">Lists user-wide global tools.</span></span> <span data-ttu-id="c4fad-121">`--tool-path` Seçenekle birleştirilemeyiz.</span><span class="sxs-lookup"><span data-stu-id="c4fad-121">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="c4fad-122">Her ikisini `--global` de `--tool-path` atlayarak yerel araçları listeler.</span><span class="sxs-lookup"><span data-stu-id="c4fad-122">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

- **`-h|--help`**

  <span data-ttu-id="c4fad-123">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="c4fad-123">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="c4fad-124">Genel araçları bulabileceğiniz özel bir konum belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4fad-124">Specifies a custom location where to find global tools.</span></span> <span data-ttu-id="c4fad-125">PATH mutlak veya göreceli olabilir.</span><span class="sxs-lookup"><span data-stu-id="c4fad-125">PATH can be absolute or relative.</span></span> <span data-ttu-id="c4fad-126">`--global` Seçenekle birleştirilemeyiz.</span><span class="sxs-lookup"><span data-stu-id="c4fad-126">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="c4fad-127">Her ikisini `--global` de `--tool-path` atlayarak yerel araçları listeler.</span><span class="sxs-lookup"><span data-stu-id="c4fad-127">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

## <a name="examples"></a><span data-ttu-id="c4fad-128">Örnekler</span><span class="sxs-lookup"><span data-stu-id="c4fad-128">Examples</span></span>

- **`dotnet tool list -g`**

  <span data-ttu-id="c4fad-129">Makinenizde kullanıcı çapında yüklenen tüm genel araçları listeler (geçerli kullanıcı profili).</span><span class="sxs-lookup"><span data-stu-id="c4fad-129">Lists all global tools installed user-wide on your machine (current user profile).</span></span>

- **`dotnet tool list --tool-path c:\global-tools`**

  <span data-ttu-id="c4fad-130">Belirli bir Windows dizinindeki genel araçları listeler.</span><span class="sxs-lookup"><span data-stu-id="c4fad-130">Lists the global tools from a specific Windows directory.</span></span>

- **`dotnet tool list --tool-path ~/bin`**

  <span data-ttu-id="c4fad-131">Belirli bir Linux/macOS dizinindeki genel araçları listeler.</span><span class="sxs-lookup"><span data-stu-id="c4fad-131">Lists the global tools from a specific Linux/macOS directory.</span></span>

- **`dotnet tool list`**

  <span data-ttu-id="c4fad-132">Geçerli dizinde bulunan tüm yerel araçları listeler.</span><span class="sxs-lookup"><span data-stu-id="c4fad-132">Lists all local tools available in the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="c4fad-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4fad-133">See also</span></span>

- [<span data-ttu-id="c4fad-134">.NET Çekirdek araçları</span><span class="sxs-lookup"><span data-stu-id="c4fad-134">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="c4fad-135">Öğretici: .NET Core CLI'yi kullanarak bir .NET Core global aracı yükleyin ve kullanın</span><span class="sxs-lookup"><span data-stu-id="c4fad-135">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="c4fad-136">Öğretici: .NET Core CLI'yi kullanarak bir .NET Core yerel aracı nı yükleyin ve kullanın</span><span class="sxs-lookup"><span data-stu-id="c4fad-136">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
