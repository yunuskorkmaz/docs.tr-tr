---
title: DotNet temizleme komutu
description: Dotnet temiz komut geçerli dizinde temizler.
ms.date: 12/04/2018
ms.openlocfilehash: a25b7930794795e3dff5051a8ca1dd1b9c261dfd
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169865"
---
# <a name="dotnet-clean"></a><span data-ttu-id="c9037-103">DotNet Temizle</span><span class="sxs-lookup"><span data-stu-id="c9037-103">dotnet clean</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="c9037-104">Ad</span><span class="sxs-lookup"><span data-stu-id="c9037-104">Name</span></span>

<span data-ttu-id="c9037-105">`dotnet clean` -Bir projenin çıkışı temizler.</span><span class="sxs-lookup"><span data-stu-id="c9037-105">`dotnet clean` - Cleans the output of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c9037-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="c9037-106">Synopsis</span></span>

```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```

## <a name="description"></a><span data-ttu-id="c9037-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9037-107">Description</span></span>

<span data-ttu-id="c9037-108">`dotnet clean` Komut önceki yapı çıkışını temizler.</span><span class="sxs-lookup"><span data-stu-id="c9037-108">The `dotnet clean` command cleans the output of the previous build.</span></span> <span data-ttu-id="c9037-109">Olarak uygulanan bir [MSBuild hedefi](/visualstudio/msbuild/msbuild-targets), projenin komut çalıştırıldığında değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="c9037-109">It's implemented as an [MSBuild target](/visualstudio/msbuild/msbuild-targets), so the project is evaluated when the command is run.</span></span> <span data-ttu-id="c9037-110">Yalnızca derleme sırasında oluşturulan çıkışları temizlenir.</span><span class="sxs-lookup"><span data-stu-id="c9037-110">Only the outputs created during the build are cleaned.</span></span> <span data-ttu-id="c9037-111">Her iki Orta (*obj*) ve son çıktı (*bin*) klasörler temizlendi.</span><span class="sxs-lookup"><span data-stu-id="c9037-111">Both intermediate (*obj*) and final output (*bin*) folders are cleaned.</span></span>

## <a name="arguments"></a><span data-ttu-id="c9037-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="c9037-112">Arguments</span></span>

`PROJECT`

<span data-ttu-id="c9037-113">Temizlemek için MSBuild proje.</span><span class="sxs-lookup"><span data-stu-id="c9037-113">The MSBuild project to clean.</span></span> <span data-ttu-id="c9037-114">Bir proje dosyası belirtilmezse, MSBuild ile biten bir dosya uzantısına sahip bir dosya için geçerli çalışma dizini arar *proj* ve bu dosyayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="c9037-114">If a project file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="c9037-115">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="c9037-115">Options</span></span>

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="c9037-116">Derleme yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c9037-116">Defines the build configuration.</span></span> <span data-ttu-id="c9037-117">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="c9037-117">The default value is `Debug`.</span></span> <span data-ttu-id="c9037-118">Bu seçeneği yalnızca olan derleme zamanında belirtilmişse temizlenirken gerekli.</span><span class="sxs-lookup"><span data-stu-id="c9037-118">This option is only required when cleaning if you specified it during build time.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c9037-119">[Framework](../../standard/frameworks.md) oluşturma zamanında belirtildi.</span><span class="sxs-lookup"><span data-stu-id="c9037-119">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="c9037-120">Framework tanımlanmalıdır [proje dosyası](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="c9037-120">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="c9037-121">Oluşturma zamanında framework belirtilmişse framework temizlenirken belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c9037-121">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

* **`-h|--help`**

  <span data-ttu-id="c9037-122">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="c9037-122">Prints out a short help for the command.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="c9037-123">Dizini, derleme çıktılarını yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c9037-123">Directory in which the build outputs are placed.</span></span> <span data-ttu-id="c9037-124">Belirtin `-f|--framework <FRAMEWORK>` çerçeve proje oluşturulduğunda belirttiyseniz çıkış dizini anahtarıyla geçin.</span><span class="sxs-lookup"><span data-stu-id="c9037-124">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="c9037-125">Belirtilen çalışma zamanı çıktı klasörünü siler.</span><span class="sxs-lookup"><span data-stu-id="c9037-125">Cleans the output folder of the specified runtime.</span></span> <span data-ttu-id="c9037-126">Bu, bir [müstakil dağıtım](../deploying/index.md#self-contained-deployments-scd) oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="c9037-126">This is used when a [self-contained deployment](../deploying/index.md#self-contained-deployments-scd) was created.</span></span> <span data-ttu-id="c9037-127">Seçeneği, .NET Core 2.0 SDK'sını itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c9037-127">Option available since .NET Core 2.0 SDK.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="c9037-128">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c9037-128">Sets the verbosity level of the command.</span></span> <span data-ttu-id="c9037-129">İzin verilen düzeyleri q [uiet], m [en az sıfır], [ormal] n, d [ayrıntılı] ve tanı [tanısı] ' dir.</span><span class="sxs-lookup"><span data-stu-id="c9037-129">Allowed levels are q[uiet], m[inimal], n[ormal], d[etailed], and diag[nostic].</span></span>

## <a name="examples"></a><span data-ttu-id="c9037-130">Örnekler</span><span class="sxs-lookup"><span data-stu-id="c9037-130">Examples</span></span>

* <span data-ttu-id="c9037-131">Projenin varsayılan derlemeyi temizleme:</span><span class="sxs-lookup"><span data-stu-id="c9037-131">Clean a default build of the project:</span></span>

  ```console
  dotnet clean
  ```

* <span data-ttu-id="c9037-132">Yayın Yapılandırması kullanılarak oluşturulan bir projeyi Temizle:</span><span class="sxs-lookup"><span data-stu-id="c9037-132">Clean a project built using the Release configuration:</span></span>

  ```console
  dotnet clean --configuration Release
  ```