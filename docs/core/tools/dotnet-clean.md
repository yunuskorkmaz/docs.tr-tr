---
title: DotNet command - .NET Core CLI Temizle
description: Dotnet Temizle komutu, geçerli dizin temizler.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 9e68781fe00590f3c8d429631a3f72d525d29fa9
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34697037"
---
# <a name="dotnet-clean"></a><span data-ttu-id="c340c-103">DotNet Temizle</span><span class="sxs-lookup"><span data-stu-id="c340c-103">dotnet-clean</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="c340c-104">Ad</span><span class="sxs-lookup"><span data-stu-id="c340c-104">Name</span></span>

<span data-ttu-id="c340c-105">`dotnet clean` -Proje çıktı temizler.</span><span class="sxs-lookup"><span data-stu-id="c340c-105">`dotnet clean` - Cleans the output of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c340c-106">Özet</span><span class="sxs-lookup"><span data-stu-id="c340c-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="c340c-107">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="c340c-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c340c-108">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="c340c-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-v|--verbosity]
dotnet clean [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="c340c-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c340c-109">Description</span></span>

<span data-ttu-id="c340c-110">`dotnet clean` Komutu önceki yapı çıktı temizler.</span><span class="sxs-lookup"><span data-stu-id="c340c-110">The `dotnet clean` command cleans the output of the previous build.</span></span> <span data-ttu-id="c340c-111">Olarak uygulanan bir [MSBuild hedef](/visualstudio/msbuild/msbuild-targets), bu komutu çalıştırdığınızda proje değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="c340c-111">It's implemented as an [MSBuild target](/visualstudio/msbuild/msbuild-targets), so the project is evaluated when the command is run.</span></span> <span data-ttu-id="c340c-112">Yalnızca derleme sırasında oluşturulan çıkışları temizlenir.</span><span class="sxs-lookup"><span data-stu-id="c340c-112">Only the outputs created during the build are cleaned.</span></span> <span data-ttu-id="c340c-113">Her iki ara (*obj*) ve son çıktı (*bin*) klasörleri temizlendi.</span><span class="sxs-lookup"><span data-stu-id="c340c-113">Both intermediate (*obj*) and final output (*bin*) folders are cleaned.</span></span>

## <a name="arguments"></a><span data-ttu-id="c340c-114">Arguments</span><span class="sxs-lookup"><span data-stu-id="c340c-114">Arguments</span></span>

`PROJECT`

<span data-ttu-id="c340c-115">Temizlemek için MSBuild proje.</span><span class="sxs-lookup"><span data-stu-id="c340c-115">The MSBuild project to clean.</span></span> <span data-ttu-id="c340c-116">MSBuild proje dosyası belirtilmezse, geçerli çalışma dizini ile biten bir dosya uzantısına sahip bir dosya için arar *proj* ve bu dosyayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="c340c-116">If a project file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="c340c-117">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="c340c-117">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="c340c-118">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="c340c-118">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="c340c-119">Derleme yapılandırması tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c340c-119">Defines the build configuration.</span></span> <span data-ttu-id="c340c-120">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="c340c-120">The default value is `Debug`.</span></span> <span data-ttu-id="c340c-121">Bu seçeneği yalnızca olan yapı süre boyunca belirtilmişse temizlenirken gerekli.</span><span class="sxs-lookup"><span data-stu-id="c340c-121">This option is only required when cleaning if you specified it during build time.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="c340c-122">[Framework](../../standard/frameworks.md) derleme zamanında belirtildi.</span><span class="sxs-lookup"><span data-stu-id="c340c-122">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="c340c-123">Framework tanımlanmalıdır [proje dosyası](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="c340c-123">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="c340c-124">Framework'te derleme zamanında belirtilmişse framework temizlenirken belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c340c-124">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

`-h|--help`

<span data-ttu-id="c340c-125">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="c340c-125">Prints out a short help for the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="c340c-126">Dizin oluşturma çıkışları yer alır.</span><span class="sxs-lookup"><span data-stu-id="c340c-126">Directory in which the build outputs are placed.</span></span> <span data-ttu-id="c340c-127">Belirtin `-f|--framework <FRAMEWORK>` geçiş çıktı dizini ile proje yapılandırıldığında framework belirtilmişse.</span><span class="sxs-lookup"><span data-stu-id="c340c-127">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="c340c-128">Belirtilen çalışma zamanının çıkış klasörü siler.</span><span class="sxs-lookup"><span data-stu-id="c340c-128">Cleans the output folder of the specified runtime.</span></span> <span data-ttu-id="c340c-129">Bu kullanılır olduğunda bir [müstakil dağıtım](../deploying/index.md#self-contained-deployments-scd) oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="c340c-129">This is used when a [self-contained deployment](../deploying/index.md#self-contained-deployments-scd) was created.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="c340c-130">Komutun ayrıntı düzeyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c340c-130">Sets the verbosity level of the command.</span></span> <span data-ttu-id="c340c-131">İzin verilen düzeyleri q [uiet], [en az sıfır] m, n [ormal], [kincil] d ve tanı [nostic] ' dir.</span><span class="sxs-lookup"><span data-stu-id="c340c-131">Allowed levels are q[uiet], m[inimal], n[ormal], d[etailed], and diag[nostic].</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c340c-132">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="c340c-132">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="c340c-133">Derleme yapılandırması tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c340c-133">Defines the build configuration.</span></span> <span data-ttu-id="c340c-134">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="c340c-134">The default value is `Debug`.</span></span> <span data-ttu-id="c340c-135">Bu seçeneği yalnızca olan yapı süre boyunca belirtilmişse temizlenirken gerekli.</span><span class="sxs-lookup"><span data-stu-id="c340c-135">This option is only required when cleaning if you specified it during build time.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="c340c-136">[Framework](../../standard/frameworks.md) derleme zamanında belirtildi.</span><span class="sxs-lookup"><span data-stu-id="c340c-136">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="c340c-137">Framework tanımlanmalıdır [proje dosyası](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="c340c-137">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="c340c-138">Framework'te derleme zamanında belirtilmişse framework temizlenirken belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c340c-138">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

`-h|--help`

<span data-ttu-id="c340c-139">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="c340c-139">Prints out a short help for the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="c340c-140">Dizin oluşturma çıkışları yer alır.</span><span class="sxs-lookup"><span data-stu-id="c340c-140">Directory in which the build outputs are placed.</span></span> <span data-ttu-id="c340c-141">Belirtin `-f|--framework <FRAMEWORK>` geçiş çıktı dizini ile proje yapılandırıldığında framework belirtilmişse.</span><span class="sxs-lookup"><span data-stu-id="c340c-141">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="c340c-142">Komutun ayrıntı düzeyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c340c-142">Sets the verbosity level of the command.</span></span> <span data-ttu-id="c340c-143">İzin verilen düzeyleri q [uiet], [en az sıfır] m, n [ormal], [kincil] d ve tanı [nostic] ' dir.</span><span class="sxs-lookup"><span data-stu-id="c340c-143">Allowed levels are q[uiet], m[inimal], n[ormal], d[etailed], and diag[nostic].</span></span>

---

## <a name="examples"></a><span data-ttu-id="c340c-144">Örnekler</span><span class="sxs-lookup"><span data-stu-id="c340c-144">Examples</span></span>

<span data-ttu-id="c340c-145">Projenin varsayılan derlemeyi temizleme:</span><span class="sxs-lookup"><span data-stu-id="c340c-145">Clean a default build of the project:</span></span>

`dotnet clean`

<span data-ttu-id="c340c-146">Yayın yapılandırma kullanılarak oluşturulmuştur bir projeyi temizleyin:</span><span class="sxs-lookup"><span data-stu-id="c340c-146">Clean a project built using the Release configuration:</span></span>

`dotnet clean --configuration Release`
