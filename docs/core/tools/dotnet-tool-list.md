---
title: DotNet araç listesi komutu
description: DotNet araç listesi komutu, makinenizde yüklü olan .NET Core araçlarını listeler.
ms.date: 02/14/2020
ms.openlocfilehash: 4035c5be233232e53c6d7150485f737108c1e18d
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925468"
---
# <a name="dotnet-tool-list"></a><span data-ttu-id="c514b-103">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="c514b-103">dotnet tool list</span></span>

<span data-ttu-id="c514b-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="c514b-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="c514b-105">Ad</span><span class="sxs-lookup"><span data-stu-id="c514b-105">Name</span></span>

<span data-ttu-id="c514b-106">`dotnet tool list`-Makinenizde yüklü olan belirtilen türdeki tüm [.NET Core araçlarını](global-tools.md) listeler.</span><span class="sxs-lookup"><span data-stu-id="c514b-106">`dotnet tool list` - Lists all [.NET Core tools](global-tools.md) of the specified type currently installed on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c514b-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="c514b-107">Synopsis</span></span>

```dotnetcli
dotnet tool list -g|--global

dotnet tool list --tool-path <PATH>

dotnet tool list --local

dotnet tool list

dotnet tool list -h|--help
```

## <a name="description"></a><span data-ttu-id="c514b-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c514b-108">Description</span></span>

<span data-ttu-id="c514b-109">Bu `dotnet tool list` komut, makinenizde yüklü olan tüm .NET Core genel, araç yolu veya yerel araçlarını listeetmeniz için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="c514b-109">The `dotnet tool list` command provides a way for you to list all .NET Core global, tool-path, or local tools installed on your machine.</span></span> <span data-ttu-id="c514b-110">Komut, paket adını, yüklü sürümü ve araç komutunu listeler.</span><span class="sxs-lookup"><span data-stu-id="c514b-110">The command lists the package name, version installed, and the tool command.</span></span>  <span data-ttu-id="c514b-111">Komutunu kullanmak için aşağıdakilerden birini belirtin:</span><span class="sxs-lookup"><span data-stu-id="c514b-111">To use the command, you specify one of the following:</span></span>

* <span data-ttu-id="c514b-112">Varsayılan konumda yüklü olan küresel araçları listelemek için, `--global` seçeneğini kullanın</span><span class="sxs-lookup"><span data-stu-id="c514b-112">To list global tools installed in the default location, use the `--global` option</span></span>
* <span data-ttu-id="c514b-113">Özel bir konumda yüklü olan küresel araçları listelemek için `--tool-path` seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c514b-113">To list global tools installed in a custom location, use the `--tool-path` option.</span></span>
* <span data-ttu-id="c514b-114">Yerel araçları listelemek için `--local` seçeneğini kullanın veya `--global` , `--tool-path` ve seçeneklerini atlayın `--local` .</span><span class="sxs-lookup"><span data-stu-id="c514b-114">To list local tools, use the `--local` option or omit the `--global`, `--tool-path`, and `--local` options.</span></span>

<span data-ttu-id="c514b-115">**Yerel araçlar .NET Core SDK 3,0 ' den başlayarak kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="c514b-115">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="options"></a><span data-ttu-id="c514b-116">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="c514b-116">Options</span></span>

- **`-g|--global`**

  <span data-ttu-id="c514b-117">Kullanıcı genelindeki genel araçları listeler.</span><span class="sxs-lookup"><span data-stu-id="c514b-117">Lists user-wide global tools.</span></span> <span data-ttu-id="c514b-118">`--tool-path`Seçeneğiyle birleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="c514b-118">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="c514b-119">Her ikisini de atlama `--global` ve `--tool-path` yerel araçları listeler.</span><span class="sxs-lookup"><span data-stu-id="c514b-119">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

- **`-h|--help`**

  <span data-ttu-id="c514b-120">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="c514b-120">Prints out a short help for the command.</span></span>

- **`--local`**

  <span data-ttu-id="c514b-121">Geçerli dizin için yerel araçları listeler.</span><span class="sxs-lookup"><span data-stu-id="c514b-121">Lists local tools for the current directory.</span></span> <span data-ttu-id="c514b-122">`--global`Veya `--tool-path` seçenekleriyle birleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="c514b-122">Can't be combined with the `--global` or `--tool-path` options.</span></span> <span data-ttu-id="c514b-123">Belirtilmemiş olsa bile, her ikisini de atlama `--global` ve `--tool-path` yerel araçları listeler `--local` .</span><span class="sxs-lookup"><span data-stu-id="c514b-123">Omitting both `--global` and `--tool-path` lists local tools even if `--local` is not specified.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="c514b-124">Genel araçların bulunacağı bir özel konum belirtir.</span><span class="sxs-lookup"><span data-stu-id="c514b-124">Specifies a custom location where to find global tools.</span></span> <span data-ttu-id="c514b-125">YOL mutlak veya göreli olabilir.</span><span class="sxs-lookup"><span data-stu-id="c514b-125">PATH can be absolute or relative.</span></span> <span data-ttu-id="c514b-126">`--global`Seçeneğiyle birleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="c514b-126">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="c514b-127">Her ikisini de atlama `--global` ve `--tool-path` yerel araçları listeler.</span><span class="sxs-lookup"><span data-stu-id="c514b-127">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

## <a name="examples"></a><span data-ttu-id="c514b-128">Örnekler</span><span class="sxs-lookup"><span data-stu-id="c514b-128">Examples</span></span>

- **`dotnet tool list -g`**

  <span data-ttu-id="c514b-129">Makinenizde Kullanıcı genelinde yüklenen tüm genel araçları listeler (geçerli kullanıcı profili).</span><span class="sxs-lookup"><span data-stu-id="c514b-129">Lists all global tools installed user-wide on your machine (current user profile).</span></span>

- **`dotnet tool list --tool-path c:\global-tools`**

  <span data-ttu-id="c514b-130">Belirli bir Windows dizininden küresel araçları listeler.</span><span class="sxs-lookup"><span data-stu-id="c514b-130">Lists the global tools from a specific Windows directory.</span></span>

- **`dotnet tool list --tool-path ~/bin`**

  <span data-ttu-id="c514b-131">Belirli bir Linux/macOS dizininden küresel araçları listeler.</span><span class="sxs-lookup"><span data-stu-id="c514b-131">Lists the global tools from a specific Linux/macOS directory.</span></span>

- <span data-ttu-id="c514b-132">**`dotnet tool list`** veya**`dotnet tool list --local`**</span><span class="sxs-lookup"><span data-stu-id="c514b-132">**`dotnet tool list`** or **`dotnet tool list --local`**</span></span>

  <span data-ttu-id="c514b-133">Geçerli dizinde bulunan tüm yerel araçları listeler.</span><span class="sxs-lookup"><span data-stu-id="c514b-133">Lists all local tools available in the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="c514b-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c514b-134">See also</span></span>

- [<span data-ttu-id="c514b-135">.NET Core araçları</span><span class="sxs-lookup"><span data-stu-id="c514b-135">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="c514b-136">Öğretici: .NET Core CLI kullanarak .NET Core küresel aracı 'nı yükleyip kullanın</span><span class="sxs-lookup"><span data-stu-id="c514b-136">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="c514b-137">Öğretici: .NET Core CLI kullanarak bir .NET Core yerel aracı yükleyip kullanın</span><span class="sxs-lookup"><span data-stu-id="c514b-137">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
