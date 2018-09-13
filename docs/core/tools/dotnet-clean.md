---
title: DotNet command - .NET Core CLI Temizle
description: Dotnet temiz komut geçerli dizinde temizler.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 5553e4b4423a2d824c05caf7114c47b5f1c20477
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44710148"
---
# <a name="dotnet-clean"></a><span data-ttu-id="fef74-103">DotNet Temizle</span><span class="sxs-lookup"><span data-stu-id="fef74-103">dotnet clean</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="fef74-104">Ad</span><span class="sxs-lookup"><span data-stu-id="fef74-104">Name</span></span>

<span data-ttu-id="fef74-105">`dotnet clean` -Bir projenin çıkışı temizler.</span><span class="sxs-lookup"><span data-stu-id="fef74-105">`dotnet clean` - Cleans the output of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="fef74-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="fef74-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="fef74-107">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="fef74-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="fef74-108">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="fef74-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-v|--verbosity]
dotnet clean [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="fef74-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fef74-109">Description</span></span>

<span data-ttu-id="fef74-110">`dotnet clean` Komut önceki yapı çıkışını temizler.</span><span class="sxs-lookup"><span data-stu-id="fef74-110">The `dotnet clean` command cleans the output of the previous build.</span></span> <span data-ttu-id="fef74-111">Olarak uygulanan bir [MSBuild hedefi](/visualstudio/msbuild/msbuild-targets), projenin komut çalıştırıldığında değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="fef74-111">It's implemented as an [MSBuild target](/visualstudio/msbuild/msbuild-targets), so the project is evaluated when the command is run.</span></span> <span data-ttu-id="fef74-112">Yalnızca derleme sırasında oluşturulan çıkışları temizlenir.</span><span class="sxs-lookup"><span data-stu-id="fef74-112">Only the outputs created during the build are cleaned.</span></span> <span data-ttu-id="fef74-113">Her iki Orta (*obj*) ve son çıktı (*bin*) klasörler temizlendi.</span><span class="sxs-lookup"><span data-stu-id="fef74-113">Both intermediate (*obj*) and final output (*bin*) folders are cleaned.</span></span>

## <a name="arguments"></a><span data-ttu-id="fef74-114">Arguments</span><span class="sxs-lookup"><span data-stu-id="fef74-114">Arguments</span></span>

`PROJECT`

<span data-ttu-id="fef74-115">Temizlemek için MSBuild proje.</span><span class="sxs-lookup"><span data-stu-id="fef74-115">The MSBuild project to clean.</span></span> <span data-ttu-id="fef74-116">Bir proje dosyası belirtilmezse, MSBuild ile biten bir dosya uzantısına sahip bir dosya için geçerli çalışma dizini arar *proj* ve bu dosyayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="fef74-116">If a project file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="fef74-117">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="fef74-117">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="fef74-118">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="fef74-118">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="fef74-119">Derleme yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fef74-119">Defines the build configuration.</span></span> <span data-ttu-id="fef74-120">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="fef74-120">The default value is `Debug`.</span></span> <span data-ttu-id="fef74-121">Bu seçeneği yalnızca olan derleme zamanında belirtilmişse temizlenirken gerekli.</span><span class="sxs-lookup"><span data-stu-id="fef74-121">This option is only required when cleaning if you specified it during build time.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="fef74-122">[Framework](../../standard/frameworks.md) oluşturma zamanında belirtildi.</span><span class="sxs-lookup"><span data-stu-id="fef74-122">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="fef74-123">Framework tanımlanmalıdır [proje dosyası](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="fef74-123">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="fef74-124">Oluşturma zamanında framework belirtilmişse framework temizlenirken belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fef74-124">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

`-h|--help`

<span data-ttu-id="fef74-125">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="fef74-125">Prints out a short help for the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="fef74-126">Dizini, derleme çıktılarını yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="fef74-126">Directory in which the build outputs are placed.</span></span> <span data-ttu-id="fef74-127">Belirtin `-f|--framework <FRAMEWORK>` çerçeve proje oluşturulduğunda belirttiyseniz çıkış dizini anahtarıyla geçin.</span><span class="sxs-lookup"><span data-stu-id="fef74-127">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="fef74-128">Belirtilen çalışma zamanı çıktı klasörünü siler.</span><span class="sxs-lookup"><span data-stu-id="fef74-128">Cleans the output folder of the specified runtime.</span></span> <span data-ttu-id="fef74-129">Bu, bir [müstakil dağıtım](../deploying/index.md#self-contained-deployments-scd) oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="fef74-129">This is used when a [self-contained deployment](../deploying/index.md#self-contained-deployments-scd) was created.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="fef74-130">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="fef74-130">Sets the verbosity level of the command.</span></span> <span data-ttu-id="fef74-131">İzin verilen düzeyleri q [uiet], m [en az sıfır], [ormal] n, d [ayrıntılı] ve tanı [tanısı] ' dir.</span><span class="sxs-lookup"><span data-stu-id="fef74-131">Allowed levels are q[uiet], m[inimal], n[ormal], d[etailed], and diag[nostic].</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="fef74-132">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="fef74-132">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="fef74-133">Derleme yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fef74-133">Defines the build configuration.</span></span> <span data-ttu-id="fef74-134">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="fef74-134">The default value is `Debug`.</span></span> <span data-ttu-id="fef74-135">Bu seçeneği yalnızca olan derleme zamanında belirtilmişse temizlenirken gerekli.</span><span class="sxs-lookup"><span data-stu-id="fef74-135">This option is only required when cleaning if you specified it during build time.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="fef74-136">[Framework](../../standard/frameworks.md) oluşturma zamanında belirtildi.</span><span class="sxs-lookup"><span data-stu-id="fef74-136">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="fef74-137">Framework tanımlanmalıdır [proje dosyası](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="fef74-137">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="fef74-138">Oluşturma zamanında framework belirtilmişse framework temizlenirken belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fef74-138">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

`-h|--help`

<span data-ttu-id="fef74-139">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="fef74-139">Prints out a short help for the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="fef74-140">Dizini, derleme çıktılarını yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="fef74-140">Directory in which the build outputs are placed.</span></span> <span data-ttu-id="fef74-141">Belirtin `-f|--framework <FRAMEWORK>` çerçeve proje oluşturulduğunda belirttiyseniz çıkış dizini anahtarıyla geçin.</span><span class="sxs-lookup"><span data-stu-id="fef74-141">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="fef74-142">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="fef74-142">Sets the verbosity level of the command.</span></span> <span data-ttu-id="fef74-143">İzin verilen düzeyleri q [uiet], m [en az sıfır], [ormal] n, d [ayrıntılı] ve tanı [tanısı] ' dir.</span><span class="sxs-lookup"><span data-stu-id="fef74-143">Allowed levels are q[uiet], m[inimal], n[ormal], d[etailed], and diag[nostic].</span></span>

---

## <a name="examples"></a><span data-ttu-id="fef74-144">Örnekler</span><span class="sxs-lookup"><span data-stu-id="fef74-144">Examples</span></span>

<span data-ttu-id="fef74-145">Projenin varsayılan derlemeyi temizleme:</span><span class="sxs-lookup"><span data-stu-id="fef74-145">Clean a default build of the project:</span></span>

`dotnet clean`

<span data-ttu-id="fef74-146">Yayın Yapılandırması kullanılarak oluşturulan bir projeyi Temizle:</span><span class="sxs-lookup"><span data-stu-id="fef74-146">Clean a project built using the Release configuration:</span></span>

`dotnet clean --configuration Release`
