---
title: DotNet depolama komutu
description: "'Dotnet deposu' komutunu belirtilen derlemeleri çalışma zamanı Paket Deposu."
author: bleroy
ms.date: 05/29/2018
ms.custom: seodec18
ms.openlocfilehash: 58889039d117a2231cda693e4aca7790f018d1b5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54606757"
---
# <a name="dotnet-store"></a><span data-ttu-id="0d31f-103">DotNet deposu</span><span class="sxs-lookup"><span data-stu-id="0d31f-103">dotnet store</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a><span data-ttu-id="0d31f-104">Ad</span><span class="sxs-lookup"><span data-stu-id="0d31f-104">Name</span></span>

<span data-ttu-id="0d31f-105">`dotnet store` -Belirli derlemelerde depolar [çalışma zamanı Paket Deposu](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="0d31f-105">`dotnet store` - Stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span>

## <a name="synopsis"></a><span data-ttu-id="0d31f-106">Synopsis</span><span class="sxs-lookup"><span data-stu-id="0d31f-106">Synopsis</span></span>

`dotnet store -m|--manifest -f|--framework -r|--runtime  [--framework-version] [-h|--help] [--output] [--skip-optimization] [--skip-symbols] [-v|--verbosity] [--working-dir]`

## <a name="description"></a><span data-ttu-id="0d31f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0d31f-107">Description</span></span>

<span data-ttu-id="0d31f-108">`dotnet store` Belirtilen derlemede depolar [çalışma zamanı Paket Deposu](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="0d31f-108">`dotnet store` stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span> <span data-ttu-id="0d31f-109">Varsayılan olarak, derlemeleri çerçevesi ve hedef çalışma zamanı için iyileştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0d31f-109">By default, assemblies are optimized for the target runtime and framework.</span></span> <span data-ttu-id="0d31f-110">Daha fazla bilgi için [çalışma zamanı Paket Deposu](../deploying/runtime-store.md) konu.</span><span class="sxs-lookup"><span data-stu-id="0d31f-110">For more information, see the [runtime package store](../deploying/runtime-store.md) topic.</span></span>

## <a name="required-options"></a><span data-ttu-id="0d31f-111">Gerekli seçenekleri</span><span class="sxs-lookup"><span data-stu-id="0d31f-111">Required options</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="0d31f-112">Belirtir [hedef Framework'ü](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="0d31f-112">Specifies the [target framework](../../standard/frameworks.md).</span></span>

`-m|--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="0d31f-113">*Paket Deposu bildirim dosyası* depolamak için paketler listesini içeren bir XML dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="0d31f-113">The *package store manifest file* is an XML file that contains the list of packages to store.</span></span> <span data-ttu-id="0d31f-114">Bildirim dosyasının biçimi SDK stilinde proje biçimi ile uyumludur.</span><span class="sxs-lookup"><span data-stu-id="0d31f-114">The format of the manifest file is compatible with the SDK-style project format.</span></span> <span data-ttu-id="0d31f-115">Bu nedenle, istediğiniz paketleri başvuran bir proje dosyası ile birlikte kullanılabilir `-m|--manifest` derlemeler çalışma zamanı paketi deposuna seçeneği.</span><span class="sxs-lookup"><span data-stu-id="0d31f-115">So, a project file that references the desired packages can be used with the `-m|--manifest` option to store assemblies in the runtime package store.</span></span> <span data-ttu-id="0d31f-116">Birden çok bildirim dosyaları belirtmek için her dosya için yolu ve seçeneği yineleyin.</span><span class="sxs-lookup"><span data-stu-id="0d31f-116">To specify multiple manifest files, repeat the option and path for each file.</span></span> <span data-ttu-id="0d31f-117">Örneğin: `--manifest packages1.csproj --manifest packages2.csproj`</span><span class="sxs-lookup"><span data-stu-id="0d31f-117">For example: `--manifest packages1.csproj --manifest packages2.csproj`.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="0d31f-118">[Çalışma zamanı tanımlayıcısı](../rid-catalog.md) hedef.</span><span class="sxs-lookup"><span data-stu-id="0d31f-118">The [runtime identifier](../rid-catalog.md) to target.</span></span>

## <a name="optional-options"></a><span data-ttu-id="0d31f-119">İsteğe bağlı Seçenekler</span><span class="sxs-lookup"><span data-stu-id="0d31f-119">Optional options</span></span>

`--framework-version <FRAMEWORK_VERSION>`

<span data-ttu-id="0d31f-120">.NET Core SDK'sı sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="0d31f-120">Specifies the .NET Core SDK version.</span></span> <span data-ttu-id="0d31f-121">Bu seçeneği tarafından belirtilen framework ötesinde bir özel framework sürümünü seçmenize olanak sağlayan `-f|--framework` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="0d31f-121">This option enables you to select a specific framework version beyond the framework specified by the `-f|--framework` option.</span></span>

`-h|--help`

<span data-ttu-id="0d31f-122">Yardım bilgisi gösterir.</span><span class="sxs-lookup"><span data-stu-id="0d31f-122">Shows help information.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="0d31f-123">Çalışma zamanı Paket Deposu yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="0d31f-123">Specifies the path to the runtime package store.</span></span> <span data-ttu-id="0d31f-124">Belirtilmezse, varsayılan *depolamak* kullanıcı profili .NET Core yükleme dizininin alt.</span><span class="sxs-lookup"><span data-stu-id="0d31f-124">If not specified, it defaults to the *store* subdirectory of the user profile .NET Core installation directory.</span></span>

`--skip-optimization`

<span data-ttu-id="0d31f-125">İyileştirme aşamasından atlar.</span><span class="sxs-lookup"><span data-stu-id="0d31f-125">Skips the optimization phase.</span></span>

`--skip-symbols`

<span data-ttu-id="0d31f-126">Atlamalar nesil simge.</span><span class="sxs-lookup"><span data-stu-id="0d31f-126">Skips symbol generation.</span></span> <span data-ttu-id="0d31f-127">Şu anda yalnızca Windows ve Linux üzerinde sembolleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d31f-127">Currently, you can only generate symbols on Windows and Linux.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="0d31f-128">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0d31f-128">Sets the verbosity level of the command.</span></span> <span data-ttu-id="0d31f-129">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="0d31f-129">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`-w|--working-dir <INTERMEDIATE_WORKING_DIRECTORY>`

<span data-ttu-id="0d31f-130">Komut tarafından kullanılan çalışma dizini.</span><span class="sxs-lookup"><span data-stu-id="0d31f-130">The working directory used by the command.</span></span> <span data-ttu-id="0d31f-131">Belirtilmezse, kullandığı *obj* geçerli dizininin alt.</span><span class="sxs-lookup"><span data-stu-id="0d31f-131">If not specified, it uses the *obj* subdirectory of the current directory.</span></span>

## <a name="examples"></a><span data-ttu-id="0d31f-132">Örnekler</span><span class="sxs-lookup"><span data-stu-id="0d31f-132">Examples</span></span>

<span data-ttu-id="0d31f-133">Belirtilen paket Store *packages.csproj* .NET Core 2.0.0 için proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="0d31f-133">Store the packages specified in the *packages.csproj* project file for .NET Core 2.0.0:</span></span>

`dotnet store --manifest packages.csproj --framework-version 2.0.0`

<span data-ttu-id="0d31f-134">Belirtilen paket Store *packages.csproj* iyileştirme olmadan:</span><span class="sxs-lookup"><span data-stu-id="0d31f-134">Store the packages specified in the *packages.csproj* without optimization:</span></span>

`dotnet store --manifest packages.csproj --skip-optimization`

## <a name="see-also"></a><span data-ttu-id="0d31f-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d31f-135">See also</span></span>

- [<span data-ttu-id="0d31f-136">Çalışma zamanı paket deposu</span><span class="sxs-lookup"><span data-stu-id="0d31f-136">Runtime package store</span></span>](../deploying/runtime-store.md)
