---
title: DotNet depo komutu
description: "' DotNet Store ' komutu, belirtilen derlemeleri çalışma zamanı paket deposunda depolar."
author: bleroy
ms.date: 05/29/2018
ms.openlocfilehash: 3a81e06f36ffbed68b7cc35de47aa5dca32bab6e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714194"
---
# <a name="dotnet-store"></a><span data-ttu-id="a7654-103">dotnet store</span><span class="sxs-lookup"><span data-stu-id="a7654-103">dotnet store</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a><span data-ttu-id="a7654-104">Name</span><span class="sxs-lookup"><span data-stu-id="a7654-104">Name</span></span>

<span data-ttu-id="a7654-105">`dotnet store`-belirtilen derlemeleri [çalışma zamanı paket deposunda](../deploying/runtime-store.md)depolar.</span><span class="sxs-lookup"><span data-stu-id="a7654-105">`dotnet store` - Stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span>

## <a name="synopsis"></a><span data-ttu-id="a7654-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="a7654-106">Synopsis</span></span>

`dotnet store -m|--manifest -f|--framework -r|--runtime  [--framework-version] [-h|--help] [--output] [--skip-optimization] [--skip-symbols] [-v|--verbosity] [--working-dir]`

## <a name="description"></a><span data-ttu-id="a7654-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7654-107">Description</span></span>

<span data-ttu-id="a7654-108">`dotnet store`, belirtilen derlemeleri [çalışma zamanı paket deposunda](../deploying/runtime-store.md)depolar.</span><span class="sxs-lookup"><span data-stu-id="a7654-108">`dotnet store` stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span> <span data-ttu-id="a7654-109">Varsayılan olarak, derlemeler hedef çalışma zamanına ve çerçeveye en iyi duruma getirilir.</span><span class="sxs-lookup"><span data-stu-id="a7654-109">By default, assemblies are optimized for the target runtime and framework.</span></span> <span data-ttu-id="a7654-110">Daha fazla bilgi için bkz. [çalışma zamanı paket deposu](../deploying/runtime-store.md) konusu.</span><span class="sxs-lookup"><span data-stu-id="a7654-110">For more information, see the [runtime package store](../deploying/runtime-store.md) topic.</span></span>

## <a name="required-options"></a><span data-ttu-id="a7654-111">Gerekli seçenekler</span><span class="sxs-lookup"><span data-stu-id="a7654-111">Required options</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="a7654-112">[Hedef çerçeveyi](../../standard/frameworks.md)belirtir.</span><span class="sxs-lookup"><span data-stu-id="a7654-112">Specifies the [target framework](../../standard/frameworks.md).</span></span>

`-m|--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="a7654-113">*Paket deposu bildirim dosyası* , depolanacak paketlerin listesini IÇEREN bir XML dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="a7654-113">The *package store manifest file* is an XML file that contains the list of packages to store.</span></span> <span data-ttu-id="a7654-114">Bildirim dosyasının biçimi, SDK stili proje biçimiyle uyumludur.</span><span class="sxs-lookup"><span data-stu-id="a7654-114">The format of the manifest file is compatible with the SDK-style project format.</span></span> <span data-ttu-id="a7654-115">Bu nedenle, istenen paketlere başvuran bir proje dosyası, derlemeleri çalışma zamanı paket deposunda depolamak için `-m|--manifest` seçeneği ile birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a7654-115">So, a project file that references the desired packages can be used with the `-m|--manifest` option to store assemblies in the runtime package store.</span></span> <span data-ttu-id="a7654-116">Birden çok bildirim dosyası belirtmek için, her bir dosyanın seçeneğini ve yolunu tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="a7654-116">To specify multiple manifest files, repeat the option and path for each file.</span></span> <span data-ttu-id="a7654-117">Örneğin: `--manifest packages1.csproj --manifest packages2.csproj`.</span><span class="sxs-lookup"><span data-stu-id="a7654-117">For example: `--manifest packages1.csproj --manifest packages2.csproj`.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="a7654-118">Hedeflenecek [çalışma zamanı tanımlayıcısı](../rid-catalog.md) .</span><span class="sxs-lookup"><span data-stu-id="a7654-118">The [runtime identifier](../rid-catalog.md) to target.</span></span>

## <a name="optional-options"></a><span data-ttu-id="a7654-119">İsteğe bağlı seçenekler</span><span class="sxs-lookup"><span data-stu-id="a7654-119">Optional options</span></span>

`--framework-version <FRAMEWORK_VERSION>`

<span data-ttu-id="a7654-120">.NET Core SDK sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="a7654-120">Specifies the .NET Core SDK version.</span></span> <span data-ttu-id="a7654-121">Bu seçenek, `-f|--framework` seçeneği tarafından belirtilen çerçevenin ötesinde belirli bir çerçeve sürümü seçmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a7654-121">This option enables you to select a specific framework version beyond the framework specified by the `-f|--framework` option.</span></span>

`-h|--help`

<span data-ttu-id="a7654-122">Yardım bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a7654-122">Shows help information.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="a7654-123">Çalışma zamanı paket deposunun yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="a7654-123">Specifies the path to the runtime package store.</span></span> <span data-ttu-id="a7654-124">Belirtilmemişse, varsayılan olarak Kullanıcı profili .NET Core yükleme dizininin *Depo* alt dizini olur.</span><span class="sxs-lookup"><span data-stu-id="a7654-124">If not specified, it defaults to the *store* subdirectory of the user profile .NET Core installation directory.</span></span>

`--skip-optimization`

<span data-ttu-id="a7654-125">İyileştirme aşamasını atlar.</span><span class="sxs-lookup"><span data-stu-id="a7654-125">Skips the optimization phase.</span></span>

`--skip-symbols`

<span data-ttu-id="a7654-126">Sembol oluşturmayı atlar.</span><span class="sxs-lookup"><span data-stu-id="a7654-126">Skips symbol generation.</span></span> <span data-ttu-id="a7654-127">Şu anda yalnızca Windows ve Linux üzerinde semboller oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7654-127">Currently, you can only generate symbols on Windows and Linux.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="a7654-128">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a7654-128">Sets the verbosity level of the command.</span></span> <span data-ttu-id="a7654-129">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="a7654-129">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`-w|--working-dir <INTERMEDIATE_WORKING_DIRECTORY>`

<span data-ttu-id="a7654-130">Komut tarafından kullanılan çalışma dizini.</span><span class="sxs-lookup"><span data-stu-id="a7654-130">The working directory used by the command.</span></span> <span data-ttu-id="a7654-131">Belirtilmemişse, geçerli dizinin *obj* alt dizinini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a7654-131">If not specified, it uses the *obj* subdirectory of the current directory.</span></span>

## <a name="examples"></a><span data-ttu-id="a7654-132">Örnekler</span><span class="sxs-lookup"><span data-stu-id="a7654-132">Examples</span></span>

<span data-ttu-id="a7654-133">.NET Core 2.0.0 için *Packages. csproj* proje dosyasında belirtilen paketleri depolayın:</span><span class="sxs-lookup"><span data-stu-id="a7654-133">Store the packages specified in the *packages.csproj* project file for .NET Core 2.0.0:</span></span>

`dotnet store --manifest packages.csproj --framework-version 2.0.0`

<span data-ttu-id="a7654-134">*Packages. csproj* içinde belirtilen paketleri iyileştirme olmadan depola:</span><span class="sxs-lookup"><span data-stu-id="a7654-134">Store the packages specified in the *packages.csproj* without optimization:</span></span>

`dotnet store --manifest packages.csproj --skip-optimization`

## <a name="see-also"></a><span data-ttu-id="a7654-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7654-135">See also</span></span>

- [<span data-ttu-id="a7654-136">Çalışma zamanı paket deposu</span><span class="sxs-lookup"><span data-stu-id="a7654-136">Runtime package store</span></span>](../deploying/runtime-store.md)
