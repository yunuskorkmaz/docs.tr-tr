---
title: DotNet araç listesi komutu
description: DotNet araç listesi komutu, makinenizde yüklü olan .NET Core araçlarını listeler.
ms.date: 02/14/2020
ms.openlocfilehash: f231dcfe64a925f75f948d508e7a2d83befd9a00
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156991"
---
# <a name="dotnet-tool-list"></a><span data-ttu-id="c5e85-103">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="c5e85-103">dotnet tool list</span></span>

<span data-ttu-id="c5e85-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="c5e85-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="c5e85-105">Adı</span><span class="sxs-lookup"><span data-stu-id="c5e85-105">Name</span></span>

<span data-ttu-id="c5e85-106">`dotnet tool list`-makinenizde yüklü olan belirtilen türdeki tüm [.NET Core araçları](global-tools.md) listelenir.</span><span class="sxs-lookup"><span data-stu-id="c5e85-106">`dotnet tool list` - Lists all [.NET Core tools](global-tools.md) of the specified type currently installed on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c5e85-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="c5e85-107">Synopsis</span></span>

```dotnetcli
dotnet tool list <-g|--global>
dotnet tool list <--tool-path>
dotnet tool list
dotnet tool list <-h|--help>
```

## <a name="description"></a><span data-ttu-id="c5e85-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5e85-108">Description</span></span>

<span data-ttu-id="c5e85-109">`dotnet tool list` komutu, makinenizde yüklü olan tüm .NET Core genel, araç yolu veya yerel araçlarını listeetmeniz için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5e85-109">The `dotnet tool list` command provides a way for you to list all .NET Core global, tool-path, or local Tools installed on your machine.</span></span> <span data-ttu-id="c5e85-110">Komut, paket adını, yüklü sürümü ve araç komutunu listeler.</span><span class="sxs-lookup"><span data-stu-id="c5e85-110">The command lists the package name, version installed, and the tool command.</span></span>  <span data-ttu-id="c5e85-111">Komutunu kullanmak için aşağıdakilerden birini belirtin:</span><span class="sxs-lookup"><span data-stu-id="c5e85-111">To use the command, you specify one of the following:</span></span>

* <span data-ttu-id="c5e85-112">Varsayılan konumda yüklü olan küresel bir araç.</span><span class="sxs-lookup"><span data-stu-id="c5e85-112">A global tool installed in the default location.</span></span> <span data-ttu-id="c5e85-113">`--global` seçeneğini kullanın</span><span class="sxs-lookup"><span data-stu-id="c5e85-113">Use the `--global` option</span></span>
* <span data-ttu-id="c5e85-114">Özel bir konumda yüklü olan küresel bir araç.</span><span class="sxs-lookup"><span data-stu-id="c5e85-114">A global tool installed in a custom location.</span></span> <span data-ttu-id="c5e85-115">`--tool-path` seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c5e85-115">Use the `--tool-path` option.</span></span>
* <span data-ttu-id="c5e85-116">Yerel bir araç.</span><span class="sxs-lookup"><span data-stu-id="c5e85-116">A local tool.</span></span> <span data-ttu-id="c5e85-117">`--global` ve `--tool-path` seçeneklerini atlayın.</span><span class="sxs-lookup"><span data-stu-id="c5e85-117">Omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="c5e85-118">**Yerel araçlar .NET Core SDK 3,0 ' den başlayarak kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="c5e85-118">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="options"></a><span data-ttu-id="c5e85-119">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="c5e85-119">Options</span></span>

- **`-g|--global`**

  <span data-ttu-id="c5e85-120">Kullanıcı genelindeki genel araçları listeler.</span><span class="sxs-lookup"><span data-stu-id="c5e85-120">Lists user-wide global tools.</span></span> <span data-ttu-id="c5e85-121">`--tool-path` seçeneği ile birleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="c5e85-121">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="c5e85-122">Hem `--global` hem de `--tool-path`, yerel araçları listeler.</span><span class="sxs-lookup"><span data-stu-id="c5e85-122">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

- **`-h|--help`**

  <span data-ttu-id="c5e85-123">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="c5e85-123">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="c5e85-124">Genel araçların bulunacağı bir özel konum belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5e85-124">Specifies a custom location where to find global tools.</span></span> <span data-ttu-id="c5e85-125">YOL mutlak veya göreli olabilir.</span><span class="sxs-lookup"><span data-stu-id="c5e85-125">PATH can be absolute or relative.</span></span> <span data-ttu-id="c5e85-126">`--global` seçeneği ile birleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="c5e85-126">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="c5e85-127">Hem `--global` hem de `--tool-path`, yerel araçları listeler.</span><span class="sxs-lookup"><span data-stu-id="c5e85-127">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

## <a name="examples"></a><span data-ttu-id="c5e85-128">Örnekler</span><span class="sxs-lookup"><span data-stu-id="c5e85-128">Examples</span></span>

- **`dotnet tool list -g`**

  <span data-ttu-id="c5e85-129">Makinenizde Kullanıcı genelinde yüklenen tüm genel araçları listeler (geçerli kullanıcı profili).</span><span class="sxs-lookup"><span data-stu-id="c5e85-129">Lists all global tools installed user-wide on your machine (current user profile).</span></span>

- **`dotnet tool list --tool-path c:\global-tools`**

  <span data-ttu-id="c5e85-130">Belirli bir Windows dizininden küresel araçları listeler.</span><span class="sxs-lookup"><span data-stu-id="c5e85-130">Lists the global tools from a specific Windows directory.</span></span>

- **`dotnet tool list --tool-path ~/bin`**

  <span data-ttu-id="c5e85-131">Belirli bir Linux/macOS dizininden küresel araçları listeler.</span><span class="sxs-lookup"><span data-stu-id="c5e85-131">Lists the global tools from a specific Linux/macOS directory.</span></span>

- **`dotnet tool list`**

  <span data-ttu-id="c5e85-132">Geçerli dizinde bulunan tüm yerel araçları listeler.</span><span class="sxs-lookup"><span data-stu-id="c5e85-132">Lists all local tools available in the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="c5e85-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5e85-133">See also</span></span>

- [<span data-ttu-id="c5e85-134">.NET Core araçları</span><span class="sxs-lookup"><span data-stu-id="c5e85-134">.NET Core tools</span></span>](global-tools.md)
