---
title: DotNet depolama komutu
description: "'Dotnet depo' komutu çalışma zamanı paketi deposunda belirtilen derlemelerini depolar."
author: bleroy
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: fcf1eeba0709e05cff124bc3ae7bb93f4ca57128
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-store"></a><span data-ttu-id="d3f16-103">DotNet deposu</span><span class="sxs-lookup"><span data-stu-id="d3f16-103">dotnet store</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a><span data-ttu-id="d3f16-104">Ad</span><span class="sxs-lookup"><span data-stu-id="d3f16-104">Name</span></span>

<span data-ttu-id="d3f16-105">`dotnet store`-Belirtilen derlemelerde depolar [çalışma zamanı Paket Deposu](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="d3f16-105">`dotnet store` - Stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span>

## <a name="synopsis"></a><span data-ttu-id="d3f16-106">Özet</span><span class="sxs-lookup"><span data-stu-id="d3f16-106">Synopsis</span></span>

`dotnet store -m|--manifest -f|--framework -r|--runtime  [--framework-version] [-h|--help] [--output] [--skip-optimization] [--skip-symbols] [-v|--verbosity] [--working-dir]`

## <a name="description"></a><span data-ttu-id="d3f16-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3f16-107">Description</span></span>

<span data-ttu-id="d3f16-108">`dotnet store`Belirtilen derlemelerde depolar [çalışma zamanı Paket Deposu](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="d3f16-108">`dotnet store` stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span> <span data-ttu-id="d3f16-109">Varsayılan olarak, derlemeleri hedef çalışma zamanı ve framework için getirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d3f16-109">By default, assemblies are optimized for the target runtime and framework.</span></span> <span data-ttu-id="d3f16-110">Daha fazla bilgi için bkz: [çalışma zamanı Paket Deposu](../deploying/runtime-store.md) konu.</span><span class="sxs-lookup"><span data-stu-id="d3f16-110">For more information, see the [runtime package store](../deploying/runtime-store.md) topic.</span></span>

## <a name="required-options"></a><span data-ttu-id="d3f16-111">Gerekli seçenekler</span><span class="sxs-lookup"><span data-stu-id="d3f16-111">Required options</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="d3f16-112">Belirtir [hedef framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="d3f16-112">Specifies the [target framework](../../standard/frameworks.md).</span></span>

`-m|--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="d3f16-113">*Paket Deposu bildirim dosyası* depolamak için paketlerin listesini içeren bir XML dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="d3f16-113">The *package store manifest file* is an XML file that contains the list of packages to store.</span></span> <span data-ttu-id="d3f16-114">Bildirim dosyasının biçimi ile uyumlu *csproj* biçimi.</span><span class="sxs-lookup"><span data-stu-id="d3f16-114">The format of the manifest file is compatible with the *csproj* format.</span></span> <span data-ttu-id="d3f16-115">Bu nedenle, bir *csproj* istediğiniz paketleri başvuran proje dosyası ile kullanılabilir `-m|--manifest` derlemeleri çalışma zamanı paketi deposunda depolamak için seçeneği.</span><span class="sxs-lookup"><span data-stu-id="d3f16-115">So, a *csproj* project file that references the desired packages can be used with the `-m|--manifest` option to store assemblies in the runtime package store.</span></span> <span data-ttu-id="d3f16-116">Birden çok bildirim dosyası belirtmek için her dosya için yolu ve seçeneği yineleyin: `--manifest packages1.csproj --manifest packages2.csproj`.</span><span class="sxs-lookup"><span data-stu-id="d3f16-116">To specify multiple manifest files, repeat the option and path for each file: `--manifest packages1.csproj --manifest packages2.csproj`.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="d3f16-117">Hedef çalışma zamanı tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="d3f16-117">The runtime identifier to target.</span></span>

## <a name="optional-options"></a><span data-ttu-id="d3f16-118">İsteğe bağlı seçenekleri</span><span class="sxs-lookup"><span data-stu-id="d3f16-118">Optional options</span></span>

`--framework-version <FRAMEWORK_VERSION>`

<span data-ttu-id="d3f16-119">.NET Core SDK sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="d3f16-119">Specifies the .NET Core SDK version.</span></span> <span data-ttu-id="d3f16-120">Bu seçeneği tarafından belirtilen framework ötesinde belirli framework sürümünü seçmenize olanak sağlar `-f|--framework` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="d3f16-120">This option enables you to select a specific framework version beyond the framework specified by the `-f|--framework` option.</span></span>

`-h|--help`

<span data-ttu-id="d3f16-121">Yardım bilgisi gösterir.</span><span class="sxs-lookup"><span data-stu-id="d3f16-121">Shows help information.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="d3f16-122">Çalışma zamanı paketi deposunun yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d3f16-122">Specifies the path to the runtime package store.</span></span> <span data-ttu-id="d3f16-123">Belirtilmezse, varsayılan olarak *depolamak* kullanıcı profili .NET Core yükleme dizininin alt.</span><span class="sxs-lookup"><span data-stu-id="d3f16-123">If not specified, it defaults to the *store* subdirectory of the user profile .NET Core installation directory.</span></span>

`--skip-optimization`

<span data-ttu-id="d3f16-124">İyileştirme aşamasından atlar.</span><span class="sxs-lookup"><span data-stu-id="d3f16-124">Skips the optimization phase.</span></span>

`--skip-symbols`

<span data-ttu-id="d3f16-125">Atlar nesil simge.</span><span class="sxs-lookup"><span data-stu-id="d3f16-125">Skips symbol generation.</span></span> <span data-ttu-id="d3f16-126">Şu anda yalnızca Windows ve Linux üzerindeki simgelerin oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="d3f16-126">Currently, you can only generate symbols on Windows and Linux.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="d3f16-127">Komutun ayrıntı düzeyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d3f16-127">Sets the verbosity level of the command.</span></span> <span data-ttu-id="d3f16-128">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="d3f16-128">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`-w|--working-dir <INTERMEDIATE_WORKING_DIRECTORY>`

<span data-ttu-id="d3f16-129">Komutu tarafından kullanılan çalışma dizini.</span><span class="sxs-lookup"><span data-stu-id="d3f16-129">The working directory used by the command.</span></span> <span data-ttu-id="d3f16-130">Belirtilmezse, kullanan *obj* geçerli dizinin alt dizini.</span><span class="sxs-lookup"><span data-stu-id="d3f16-130">If not specified, it uses the *obj* subdirectory of the current directory.</span></span>

## <a name="examples"></a><span data-ttu-id="d3f16-131">Örnekler</span><span class="sxs-lookup"><span data-stu-id="d3f16-131">Examples</span></span>

<span data-ttu-id="d3f16-132">Belirtilen paketleri depolamak *packages.csproj* .NET Core 2.0.0 için proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="d3f16-132">Store the packages specified in the *packages.csproj* project file for .NET Core 2.0.0:</span></span>

`dotnet store --manifest packages.csproj --framework-version 2.0.0`

<span data-ttu-id="d3f16-133">Belirtilen paketleri depolamak *packages.csproj* en iyi duruma getirme olmadan:</span><span class="sxs-lookup"><span data-stu-id="d3f16-133">Store the packages specified in the *packages.csproj* without optimization:</span></span>

`dotnet store --manifest packages.csproj --skip-optimization`

## <a name="see-also"></a><span data-ttu-id="d3f16-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3f16-134">See also</span></span>

[<span data-ttu-id="d3f16-135">Çalışma zamanı Paket Deposu</span><span class="sxs-lookup"><span data-stu-id="d3f16-135">Runtime package store</span></span>](../deploying/runtime-store.md)   
