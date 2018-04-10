---
title: DotNet depolama komutu
description: "'Dotnet depo' komutu çalışma zamanı paketi deposunda belirtilen derlemelerini depolar."
author: bleroy
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 80ea40dfbedba3dca0e767b66e14f5de22374d4f
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="dotnet-store"></a><span data-ttu-id="2e5ac-103">DotNet deposu</span><span class="sxs-lookup"><span data-stu-id="2e5ac-103">dotnet store</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a><span data-ttu-id="2e5ac-104">Ad</span><span class="sxs-lookup"><span data-stu-id="2e5ac-104">Name</span></span>

<span data-ttu-id="2e5ac-105">`dotnet store` -Belirtilen derlemelerde depolar [çalışma zamanı Paket Deposu](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="2e5ac-105">`dotnet store` - Stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span>

## <a name="synopsis"></a><span data-ttu-id="2e5ac-106">Özet</span><span class="sxs-lookup"><span data-stu-id="2e5ac-106">Synopsis</span></span>

`dotnet store -m|--manifest -f|--framework -r|--runtime  [--framework-version] [-h|--help] [--output] [--skip-optimization] [--skip-symbols] [-v|--verbosity] [--working-dir]`

## <a name="description"></a><span data-ttu-id="2e5ac-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2e5ac-107">Description</span></span>

<span data-ttu-id="2e5ac-108">`dotnet store` Belirtilen derlemelerde depolar [çalışma zamanı Paket Deposu](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="2e5ac-108">`dotnet store` stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span> <span data-ttu-id="2e5ac-109">Varsayılan olarak, derlemeleri hedef çalışma zamanı ve framework için getirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2e5ac-109">By default, assemblies are optimized for the target runtime and framework.</span></span> <span data-ttu-id="2e5ac-110">Daha fazla bilgi için bkz: [çalışma zamanı Paket Deposu](../deploying/runtime-store.md) konu.</span><span class="sxs-lookup"><span data-stu-id="2e5ac-110">For more information, see the [runtime package store](../deploying/runtime-store.md) topic.</span></span>

## <a name="required-options"></a><span data-ttu-id="2e5ac-111">Gerekli seçenekler</span><span class="sxs-lookup"><span data-stu-id="2e5ac-111">Required options</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="2e5ac-112">Belirtir [hedef framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="2e5ac-112">Specifies the [target framework](../../standard/frameworks.md).</span></span>

`-m|--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="2e5ac-113">*Paket Deposu bildirim dosyası* depolamak için paketlerin listesini içeren bir XML dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="2e5ac-113">The *package store manifest file* is an XML file that contains the list of packages to store.</span></span> <span data-ttu-id="2e5ac-114">Bildirim dosyasının biçimi ile uyumlu *csproj* biçimi.</span><span class="sxs-lookup"><span data-stu-id="2e5ac-114">The format of the manifest file is compatible with the *csproj* format.</span></span> <span data-ttu-id="2e5ac-115">Bu nedenle, bir *csproj* istediğiniz paketleri başvuran proje dosyası ile kullanılabilir `-m|--manifest` derlemeleri çalışma zamanı paketi deposunda depolamak için seçeneği.</span><span class="sxs-lookup"><span data-stu-id="2e5ac-115">So, a *csproj* project file that references the desired packages can be used with the `-m|--manifest` option to store assemblies in the runtime package store.</span></span> <span data-ttu-id="2e5ac-116">Birden çok bildirim dosyası belirtmek için her dosya için yolu ve seçeneği yineleyin: `--manifest packages1.csproj --manifest packages2.csproj`.</span><span class="sxs-lookup"><span data-stu-id="2e5ac-116">To specify multiple manifest files, repeat the option and path for each file: `--manifest packages1.csproj --manifest packages2.csproj`.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="2e5ac-117">[Çalışma zamanı tanımlayıcı](../rid-catalog.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="2e5ac-117">The [runtime identifier](../rid-catalog.md) to target.</span></span>

## <a name="optional-options"></a><span data-ttu-id="2e5ac-118">İsteğe bağlı seçenekleri</span><span class="sxs-lookup"><span data-stu-id="2e5ac-118">Optional options</span></span>

`--framework-version <FRAMEWORK_VERSION>`

<span data-ttu-id="2e5ac-119">.NET Core SDK sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="2e5ac-119">Specifies the .NET Core SDK version.</span></span> <span data-ttu-id="2e5ac-120">Bu seçeneği tarafından belirtilen framework ötesinde belirli framework sürümünü seçmenize olanak sağlar `-f|--framework` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="2e5ac-120">This option enables you to select a specific framework version beyond the framework specified by the `-f|--framework` option.</span></span>

`-h|--help`

<span data-ttu-id="2e5ac-121">Yardım bilgisi gösterir.</span><span class="sxs-lookup"><span data-stu-id="2e5ac-121">Shows help information.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="2e5ac-122">Çalışma zamanı paketi deposunun yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2e5ac-122">Specifies the path to the runtime package store.</span></span> <span data-ttu-id="2e5ac-123">Belirtilmezse, varsayılan olarak *depolamak* kullanıcı profili .NET Core yükleme dizininin alt.</span><span class="sxs-lookup"><span data-stu-id="2e5ac-123">If not specified, it defaults to the *store* subdirectory of the user profile .NET Core installation directory.</span></span>

`--skip-optimization`

<span data-ttu-id="2e5ac-124">İyileştirme aşamasından atlar.</span><span class="sxs-lookup"><span data-stu-id="2e5ac-124">Skips the optimization phase.</span></span>

`--skip-symbols`

<span data-ttu-id="2e5ac-125">Atlar nesil simge.</span><span class="sxs-lookup"><span data-stu-id="2e5ac-125">Skips symbol generation.</span></span> <span data-ttu-id="2e5ac-126">Şu anda yalnızca Windows ve Linux üzerindeki simgelerin oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="2e5ac-126">Currently, you can only generate symbols on Windows and Linux.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="2e5ac-127">Komutun ayrıntı düzeyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2e5ac-127">Sets the verbosity level of the command.</span></span> <span data-ttu-id="2e5ac-128">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="2e5ac-128">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`-w|--working-dir <INTERMEDIATE_WORKING_DIRECTORY>`

<span data-ttu-id="2e5ac-129">Komutu tarafından kullanılan çalışma dizini.</span><span class="sxs-lookup"><span data-stu-id="2e5ac-129">The working directory used by the command.</span></span> <span data-ttu-id="2e5ac-130">Belirtilmezse, kullanan *obj* geçerli dizinin alt dizini.</span><span class="sxs-lookup"><span data-stu-id="2e5ac-130">If not specified, it uses the *obj* subdirectory of the current directory.</span></span>

## <a name="examples"></a><span data-ttu-id="2e5ac-131">Örnekler</span><span class="sxs-lookup"><span data-stu-id="2e5ac-131">Examples</span></span>

<span data-ttu-id="2e5ac-132">Belirtilen paketleri depolamak *packages.csproj* .NET Core 2.0.0 için proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="2e5ac-132">Store the packages specified in the *packages.csproj* project file for .NET Core 2.0.0:</span></span>

`dotnet store --manifest packages.csproj --framework-version 2.0.0`

<span data-ttu-id="2e5ac-133">Belirtilen paketleri depolamak *packages.csproj* en iyi duruma getirme olmadan:</span><span class="sxs-lookup"><span data-stu-id="2e5ac-133">Store the packages specified in the *packages.csproj* without optimization:</span></span>

`dotnet store --manifest packages.csproj --skip-optimization`

## <a name="see-also"></a><span data-ttu-id="2e5ac-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e5ac-134">See also</span></span>

[<span data-ttu-id="2e5ac-135">Çalışma zamanı paket deposu</span><span class="sxs-lookup"><span data-stu-id="2e5ac-135">Runtime package store</span></span>](../deploying/runtime-store.md)   
