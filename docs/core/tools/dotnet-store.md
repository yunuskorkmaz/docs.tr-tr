---
title: DotNet depolama komutu
description: "'Dotnet depo' komutu çalışma zamanı paketi deposunda belirtilen derlemelerini depolar."
author: bleroy
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 54654522207157f7d49bb86223b7986acccf51ee
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696331"
---
# <a name="dotnet-store"></a><span data-ttu-id="071e1-103">DotNet deposu</span><span class="sxs-lookup"><span data-stu-id="071e1-103">dotnet store</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a><span data-ttu-id="071e1-104">Ad</span><span class="sxs-lookup"><span data-stu-id="071e1-104">Name</span></span>

<span data-ttu-id="071e1-105">`dotnet store` -Belirtilen derlemelerde depolar [çalışma zamanı Paket Deposu](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="071e1-105">`dotnet store` - Stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span>

## <a name="synopsis"></a><span data-ttu-id="071e1-106">Özet</span><span class="sxs-lookup"><span data-stu-id="071e1-106">Synopsis</span></span>

`dotnet store -m|--manifest -f|--framework -r|--runtime  [--framework-version] [-h|--help] [--output] [--skip-optimization] [--skip-symbols] [-v|--verbosity] [--working-dir]`

## <a name="description"></a><span data-ttu-id="071e1-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="071e1-107">Description</span></span>

<span data-ttu-id="071e1-108">`dotnet store` Belirtilen derlemelerde depolar [çalışma zamanı Paket Deposu](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="071e1-108">`dotnet store` stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span> <span data-ttu-id="071e1-109">Varsayılan olarak, derlemeleri hedef çalışma zamanı ve framework için getirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="071e1-109">By default, assemblies are optimized for the target runtime and framework.</span></span> <span data-ttu-id="071e1-110">Daha fazla bilgi için bkz: [çalışma zamanı Paket Deposu](../deploying/runtime-store.md) konu.</span><span class="sxs-lookup"><span data-stu-id="071e1-110">For more information, see the [runtime package store](../deploying/runtime-store.md) topic.</span></span>

## <a name="required-options"></a><span data-ttu-id="071e1-111">Gerekli seçenekler</span><span class="sxs-lookup"><span data-stu-id="071e1-111">Required options</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="071e1-112">Belirtir [hedef framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="071e1-112">Specifies the [target framework](../../standard/frameworks.md).</span></span>

`-m|--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="071e1-113">*Paket Deposu bildirim dosyası* depolamak için paketlerin listesini içeren bir XML dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="071e1-113">The *package store manifest file* is an XML file that contains the list of packages to store.</span></span> <span data-ttu-id="071e1-114">Bildirim dosyasının biçimi SDK stili project biçimiyle uyumlu.</span><span class="sxs-lookup"><span data-stu-id="071e1-114">The format of the manifest file is compatible with the SDK-style project format.</span></span> <span data-ttu-id="071e1-115">Bu nedenle, istediğiniz paketleri başvuruda bulunan bir proje dosyası ile birlikte kullanılabilir `-m|--manifest` derlemeleri çalışma zamanı paketi deposunda depolamak için seçeneği.</span><span class="sxs-lookup"><span data-stu-id="071e1-115">So, a project file that references the desired packages can be used with the `-m|--manifest` option to store assemblies in the runtime package store.</span></span> <span data-ttu-id="071e1-116">Birden çok bildirim dosyası belirtmek için yolu ve seçeneği her dosya için yineleyin.</span><span class="sxs-lookup"><span data-stu-id="071e1-116">To specify multiple manifest files, repeat the option and path for each file.</span></span> <span data-ttu-id="071e1-117">Örneğin: `--manifest packages1.csproj --manifest packages2.csproj`.</span><span class="sxs-lookup"><span data-stu-id="071e1-117">For example: `--manifest packages1.csproj --manifest packages2.csproj`.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="071e1-118">[Çalışma zamanı tanımlayıcı](../rid-catalog.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="071e1-118">The [runtime identifier](../rid-catalog.md) to target.</span></span>

## <a name="optional-options"></a><span data-ttu-id="071e1-119">İsteğe bağlı seçenekleri</span><span class="sxs-lookup"><span data-stu-id="071e1-119">Optional options</span></span>

`--framework-version <FRAMEWORK_VERSION>`

<span data-ttu-id="071e1-120">.NET Core SDK sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="071e1-120">Specifies the .NET Core SDK version.</span></span> <span data-ttu-id="071e1-121">Bu seçeneği tarafından belirtilen framework ötesinde belirli framework sürümünü seçmenize olanak sağlar `-f|--framework` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="071e1-121">This option enables you to select a specific framework version beyond the framework specified by the `-f|--framework` option.</span></span>

`-h|--help`

<span data-ttu-id="071e1-122">Yardım bilgisi gösterir.</span><span class="sxs-lookup"><span data-stu-id="071e1-122">Shows help information.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="071e1-123">Çalışma zamanı paketi deposunun yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="071e1-123">Specifies the path to the runtime package store.</span></span> <span data-ttu-id="071e1-124">Belirtilmezse, varsayılan olarak *depolamak* kullanıcı profili .NET Core yükleme dizininin alt.</span><span class="sxs-lookup"><span data-stu-id="071e1-124">If not specified, it defaults to the *store* subdirectory of the user profile .NET Core installation directory.</span></span>

`--skip-optimization`

<span data-ttu-id="071e1-125">İyileştirme aşamasından atlar.</span><span class="sxs-lookup"><span data-stu-id="071e1-125">Skips the optimization phase.</span></span>

`--skip-symbols`

<span data-ttu-id="071e1-126">Atlar nesil simge.</span><span class="sxs-lookup"><span data-stu-id="071e1-126">Skips symbol generation.</span></span> <span data-ttu-id="071e1-127">Şu anda yalnızca Windows ve Linux üzerindeki simgelerin oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="071e1-127">Currently, you can only generate symbols on Windows and Linux.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="071e1-128">Komutun ayrıntı düzeyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="071e1-128">Sets the verbosity level of the command.</span></span> <span data-ttu-id="071e1-129">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="071e1-129">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`-w|--working-dir <INTERMEDIATE_WORKING_DIRECTORY>`

<span data-ttu-id="071e1-130">Komutu tarafından kullanılan çalışma dizini.</span><span class="sxs-lookup"><span data-stu-id="071e1-130">The working directory used by the command.</span></span> <span data-ttu-id="071e1-131">Belirtilmezse, kullanan *obj* geçerli dizinin alt dizini.</span><span class="sxs-lookup"><span data-stu-id="071e1-131">If not specified, it uses the *obj* subdirectory of the current directory.</span></span>

## <a name="examples"></a><span data-ttu-id="071e1-132">Örnekler</span><span class="sxs-lookup"><span data-stu-id="071e1-132">Examples</span></span>

<span data-ttu-id="071e1-133">Belirtilen paketleri depolamak *packages.csproj* .NET Core 2.0.0 için proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="071e1-133">Store the packages specified in the *packages.csproj* project file for .NET Core 2.0.0:</span></span>

`dotnet store --manifest packages.csproj --framework-version 2.0.0`

<span data-ttu-id="071e1-134">Belirtilen paketleri depolamak *packages.csproj* en iyi duruma getirme olmadan:</span><span class="sxs-lookup"><span data-stu-id="071e1-134">Store the packages specified in the *packages.csproj* without optimization:</span></span>

`dotnet store --manifest packages.csproj --skip-optimization`

## <a name="see-also"></a><span data-ttu-id="071e1-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="071e1-135">See also</span></span>

[<span data-ttu-id="071e1-136">Çalışma zamanı paket deposu</span><span class="sxs-lookup"><span data-stu-id="071e1-136">Runtime package store</span></span>](../deploying/runtime-store.md)