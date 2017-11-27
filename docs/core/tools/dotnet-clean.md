---
title: DotNet command - .NET Core CLI Temizle
description: "Dotnet Temizle komutu, geçerli dizin temizler."
author: mairaw
ms.author: mairaw
ms.date: 08/13/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 4836f07ec1a8b59c343b4d0181587e602f61d45e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-clean"></a><span data-ttu-id="9aae9-103">DotNet Temizle</span><span class="sxs-lookup"><span data-stu-id="9aae9-103">dotnet-clean</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="9aae9-104">Ad</span><span class="sxs-lookup"><span data-stu-id="9aae9-104">Name</span></span>

<span data-ttu-id="9aae9-105">`dotnet clean`-Proje çıktı temizler.</span><span class="sxs-lookup"><span data-stu-id="9aae9-105">`dotnet clean` - Cleans the output of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9aae9-106">Özet</span><span class="sxs-lookup"><span data-stu-id="9aae9-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="9aae9-107">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="9aae9-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="9aae9-108">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="9aae9-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-v|--verbosity]
dotnet clean [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="9aae9-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9aae9-109">Description</span></span>

<span data-ttu-id="9aae9-110">`dotnet clean` Komutu önceki yapı çıktı temizler.</span><span class="sxs-lookup"><span data-stu-id="9aae9-110">The `dotnet clean` command cleans the output of the previous build.</span></span> <span data-ttu-id="9aae9-111">Olarak uygulanan bir [MSBuild hedef](/visualstudio/msbuild/msbuild-targets), bu komutu çalıştırdığınızda proje değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="9aae9-111">It's implemented as an [MSBuild target](/visualstudio/msbuild/msbuild-targets), so the project is evaluated when the command is run.</span></span> <span data-ttu-id="9aae9-112">Yalnızca derleme sırasında oluşturulan çıkışları temizlenir.</span><span class="sxs-lookup"><span data-stu-id="9aae9-112">Only the outputs created during the build are cleaned.</span></span> <span data-ttu-id="9aae9-113">Her iki ara (*obj*) ve son çıktı (*bin*) klasörleri temizlendi.</span><span class="sxs-lookup"><span data-stu-id="9aae9-113">Both intermediate (*obj*) and final output (*bin*) folders are cleaned.</span></span>

## <a name="arguments"></a><span data-ttu-id="9aae9-114">Arguments</span><span class="sxs-lookup"><span data-stu-id="9aae9-114">Arguments</span></span>

`PROJECT`

<span data-ttu-id="9aae9-115">Temizlemek için MSBuild proje.</span><span class="sxs-lookup"><span data-stu-id="9aae9-115">The MSBuild project to clean.</span></span> <span data-ttu-id="9aae9-116">MSBuild proje dosyası belirtilmezse, geçerli çalışma dizini ile biten bir dosya uzantısına sahip bir dosya için arar *proj* ve bu dosyayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="9aae9-116">If a project file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="9aae9-117">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="9aae9-117">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="9aae9-118">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="9aae9-118">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="9aae9-119">Derleme yapılandırması tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9aae9-119">Defines the build configuration.</span></span> <span data-ttu-id="9aae9-120">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="9aae9-120">The default value is `Debug`.</span></span> <span data-ttu-id="9aae9-121">Bu seçeneği yalnızca olan yapı süre boyunca belirtilmişse temizlenirken gerekli.</span><span class="sxs-lookup"><span data-stu-id="9aae9-121">This option is only required when cleaning if you specified it during build time.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="9aae9-122">[Framework](../../standard/frameworks.md) derleme zamanında belirtildi.</span><span class="sxs-lookup"><span data-stu-id="9aae9-122">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="9aae9-123">Framework tanımlanmalıdır [proje dosyası](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="9aae9-123">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="9aae9-124">Framework'te derleme zamanında belirtilmişse framework temizlenirken belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9aae9-124">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

`-h|--help`

<span data-ttu-id="9aae9-125">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="9aae9-125">Prints out a short help for the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="9aae9-126">Dizin oluşturma çıkışları yer alır.</span><span class="sxs-lookup"><span data-stu-id="9aae9-126">Directory in which the build outputs are placed.</span></span> <span data-ttu-id="9aae9-127">Belirtin `-f|--framework <FRAMEWORK>` geçiş çıktı dizini ile proje yapılandırıldığında framework belirtilmişse.</span><span class="sxs-lookup"><span data-stu-id="9aae9-127">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="9aae9-128">Belirtilen çalışma zamanının çıkış klasörü siler.</span><span class="sxs-lookup"><span data-stu-id="9aae9-128">Cleans the output folder of the specified runtime.</span></span> <span data-ttu-id="9aae9-129">Bu kullanılır olduğunda bir [müstakil dağıtım](../deploying/index.md#self-contained-deployments-scd) oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="9aae9-129">This is used when a [self-contained deployment](../deploying/index.md#self-contained-deployments-scd) was created.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="9aae9-130">Komutun ayrıntı düzeyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9aae9-130">Sets the verbosity level of the command.</span></span> <span data-ttu-id="9aae9-131">İzin verilen düzeyleri q [uiet], [en az sıfır] m, n [ormal], [kincil] d ve tanı [nostic] ' dir.</span><span class="sxs-lookup"><span data-stu-id="9aae9-131">Allowed levels are q[uiet], m[inimal], n[ormal], d[etailed], and diag[nostic].</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="9aae9-132">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="9aae9-132">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="9aae9-133">Derleme yapılandırması tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9aae9-133">Defines the build configuration.</span></span> <span data-ttu-id="9aae9-134">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="9aae9-134">The default value is `Debug`.</span></span> <span data-ttu-id="9aae9-135">Bu seçeneği yalnızca olan yapı süre boyunca belirtilmişse temizlenirken gerekli.</span><span class="sxs-lookup"><span data-stu-id="9aae9-135">This option is only required when cleaning if you specified it during build time.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="9aae9-136">[Framework](../../standard/frameworks.md) derleme zamanında belirtildi.</span><span class="sxs-lookup"><span data-stu-id="9aae9-136">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="9aae9-137">Framework tanımlanmalıdır [proje dosyası](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="9aae9-137">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="9aae9-138">Framework'te derleme zamanında belirtilmişse framework temizlenirken belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9aae9-138">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

`-h|--help`

<span data-ttu-id="9aae9-139">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="9aae9-139">Prints out a short help for the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="9aae9-140">Dizin oluşturma çıkışları yer alır.</span><span class="sxs-lookup"><span data-stu-id="9aae9-140">Directory in which the build outputs are placed.</span></span> <span data-ttu-id="9aae9-141">Belirtin `-f|--framework <FRAMEWORK>` geçiş çıktı dizini ile proje yapılandırıldığında framework belirtilmişse.</span><span class="sxs-lookup"><span data-stu-id="9aae9-141">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="9aae9-142">Komutun ayrıntı düzeyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9aae9-142">Sets the verbosity level of the command.</span></span> <span data-ttu-id="9aae9-143">İzin verilen düzeyleri q [uiet], [en az sıfır] m, n [ormal], [kincil] d ve tanı [nostic] ' dir.</span><span class="sxs-lookup"><span data-stu-id="9aae9-143">Allowed levels are q[uiet], m[inimal], n[ormal], d[etailed], and diag[nostic].</span></span>

---

## <a name="examples"></a><span data-ttu-id="9aae9-144">Örnekler</span><span class="sxs-lookup"><span data-stu-id="9aae9-144">Examples</span></span>

<span data-ttu-id="9aae9-145">Projenin varsayılan derlemeyi temizleme:</span><span class="sxs-lookup"><span data-stu-id="9aae9-145">Clean a default build of the project:</span></span>

`dotnet clean`

<span data-ttu-id="9aae9-146">Yayın yapılandırma kullanılarak oluşturulmuştur bir projeyi temizleyin:</span><span class="sxs-lookup"><span data-stu-id="9aae9-146">Clean a project built using the Release configuration:</span></span>

`dotnet clean --configuration Release`
