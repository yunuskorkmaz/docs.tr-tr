---
title: DotNet araç listesi komutu
description: DotNet araç listesi komutu, makinenizde yüklü olan .NET araçlarını listeler.
ms.date: 02/14/2020
ms.openlocfilehash: d884f2c41834dd9704de3a8ca15417ba368fde4b
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634291"
---
# <a name="dotnet-tool-list"></a><span data-ttu-id="484c6-103">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="484c6-103">dotnet tool list</span></span>

<span data-ttu-id="484c6-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="484c6-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="484c6-105">Name</span><span class="sxs-lookup"><span data-stu-id="484c6-105">Name</span></span>

<span data-ttu-id="484c6-106">`dotnet tool list` -Makinenizde yüklü olan belirtilen türdeki tüm [.net araçlarını](global-tools.md) listeler.</span><span class="sxs-lookup"><span data-stu-id="484c6-106">`dotnet tool list` - Lists all [.NET tools](global-tools.md) of the specified type currently installed on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="484c6-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="484c6-107">Synopsis</span></span>

```dotnetcli
dotnet tool list -g|--global

dotnet tool list --tool-path <PATH>

dotnet tool list --local

dotnet tool list

dotnet tool list -h|--help
```

## <a name="description"></a><span data-ttu-id="484c6-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="484c6-108">Description</span></span>

<span data-ttu-id="484c6-109">Bu `dotnet tool list` komut, makinenizde yüklü olan tüm .NET genel, araç yolu veya yerel araçları listelemek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="484c6-109">The `dotnet tool list` command provides a way for you to list all .NET global, tool-path, or local tools installed on your machine.</span></span> <span data-ttu-id="484c6-110">Komut, paket adını, yüklü sürümü ve araç komutunu listeler.</span><span class="sxs-lookup"><span data-stu-id="484c6-110">The command lists the package name, version installed, and the tool command.</span></span>  <span data-ttu-id="484c6-111">Komutunu kullanmak için aşağıdakilerden birini belirtin:</span><span class="sxs-lookup"><span data-stu-id="484c6-111">To use the command, you specify one of the following:</span></span>

* <span data-ttu-id="484c6-112">Varsayılan konumda yüklü olan küresel araçları listelemek için, `--global` seçeneğini kullanın</span><span class="sxs-lookup"><span data-stu-id="484c6-112">To list global tools installed in the default location, use the `--global` option</span></span>
* <span data-ttu-id="484c6-113">Özel bir konumda yüklü olan küresel araçları listelemek için `--tool-path` seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="484c6-113">To list global tools installed in a custom location, use the `--tool-path` option.</span></span>
* <span data-ttu-id="484c6-114">Yerel araçları listelemek için `--local` seçeneğini kullanın veya `--global` , `--tool-path` ve seçeneklerini atlayın `--local` .</span><span class="sxs-lookup"><span data-stu-id="484c6-114">To list local tools, use the `--local` option or omit the `--global`, `--tool-path`, and `--local` options.</span></span>

<span data-ttu-id="484c6-115">**Yerel araçlar .NET Core SDK 3,0 ' den başlayarak kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="484c6-115">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="options"></a><span data-ttu-id="484c6-116">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="484c6-116">Options</span></span>

- **`-g|--global`**

  <span data-ttu-id="484c6-117">Kullanıcı genelindeki genel araçları listeler.</span><span class="sxs-lookup"><span data-stu-id="484c6-117">Lists user-wide global tools.</span></span> <span data-ttu-id="484c6-118">`--tool-path`Seçeneğiyle birleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="484c6-118">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="484c6-119">Her ikisini de atlama `--global` ve `--tool-path` yerel araçları listeler.</span><span class="sxs-lookup"><span data-stu-id="484c6-119">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

- **`-h|--help`**

  <span data-ttu-id="484c6-120">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="484c6-120">Prints out a short help for the command.</span></span>

- **`--local`**

  <span data-ttu-id="484c6-121">Geçerli dizin için yerel araçları listeler.</span><span class="sxs-lookup"><span data-stu-id="484c6-121">Lists local tools for the current directory.</span></span> <span data-ttu-id="484c6-122">`--global`Veya `--tool-path` seçenekleriyle birleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="484c6-122">Can't be combined with the `--global` or `--tool-path` options.</span></span> <span data-ttu-id="484c6-123">Belirtilmemiş olsa bile, her ikisini de atlama `--global` ve `--tool-path` yerel araçları listeler `--local` .</span><span class="sxs-lookup"><span data-stu-id="484c6-123">Omitting both `--global` and `--tool-path` lists local tools even if `--local` is not specified.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="484c6-124">Genel araçların bulunacağı bir özel konum belirtir.</span><span class="sxs-lookup"><span data-stu-id="484c6-124">Specifies a custom location where to find global tools.</span></span> <span data-ttu-id="484c6-125">YOL mutlak veya göreli olabilir.</span><span class="sxs-lookup"><span data-stu-id="484c6-125">PATH can be absolute or relative.</span></span> <span data-ttu-id="484c6-126">`--global`Seçeneğiyle birleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="484c6-126">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="484c6-127">Her ikisini de atlama `--global` ve `--tool-path` yerel araçları listeler.</span><span class="sxs-lookup"><span data-stu-id="484c6-127">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

## <a name="examples"></a><span data-ttu-id="484c6-128">Örnekler</span><span class="sxs-lookup"><span data-stu-id="484c6-128">Examples</span></span>

- **`dotnet tool list -g`**

  <span data-ttu-id="484c6-129">Makinenizde Kullanıcı genelinde yüklenen tüm genel araçları listeler (geçerli kullanıcı profili).</span><span class="sxs-lookup"><span data-stu-id="484c6-129">Lists all global tools installed user-wide on your machine (current user profile).</span></span>

- **`dotnet tool list --tool-path c:\global-tools`**

  <span data-ttu-id="484c6-130">Belirli bir Windows dizininden küresel araçları listeler.</span><span class="sxs-lookup"><span data-stu-id="484c6-130">Lists the global tools from a specific Windows directory.</span></span>

- **`dotnet tool list --tool-path ~/bin`**

  <span data-ttu-id="484c6-131">Belirli bir Linux/macOS dizininden küresel araçları listeler.</span><span class="sxs-lookup"><span data-stu-id="484c6-131">Lists the global tools from a specific Linux/macOS directory.</span></span>

- <span data-ttu-id="484c6-132">**`dotnet tool list`** veya **`dotnet tool list --local`**</span><span class="sxs-lookup"><span data-stu-id="484c6-132">**`dotnet tool list`** or **`dotnet tool list --local`**</span></span>

  <span data-ttu-id="484c6-133">Geçerli dizinde bulunan tüm yerel araçları listeler.</span><span class="sxs-lookup"><span data-stu-id="484c6-133">Lists all local tools available in the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="484c6-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="484c6-134">See also</span></span>

- [<span data-ttu-id="484c6-135">.NET araçları</span><span class="sxs-lookup"><span data-stu-id="484c6-135">.NET tools</span></span>](global-tools.md)
- [<span data-ttu-id="484c6-136">Öğretici: .NET CLı kullanarak .NET genel aracını yükleyip kullanma</span><span class="sxs-lookup"><span data-stu-id="484c6-136">Tutorial: Install and use a .NET global tool using the .NET CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="484c6-137">Öğretici: .NET CLı kullanarak .NET yerel aracını yükleyip kullanma</span><span class="sxs-lookup"><span data-stu-id="484c6-137">Tutorial: Install and use a .NET local tool using the .NET CLI</span></span>](local-tools-how-to-use.md)
