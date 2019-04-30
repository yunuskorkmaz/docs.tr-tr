---
title: DotNet temizleme komutu
description: Dotnet temiz komut geçerli dizinde temizler.
ms.date: 12/04/2018
ms.openlocfilehash: a25b7930794795e3dff5051a8ca1dd1b9c261dfd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665221"
---
# <a name="dotnet-clean"></a><span data-ttu-id="f7b02-103">DotNet Temizle</span><span class="sxs-lookup"><span data-stu-id="f7b02-103">dotnet clean</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="f7b02-104">Ad</span><span class="sxs-lookup"><span data-stu-id="f7b02-104">Name</span></span>

<span data-ttu-id="f7b02-105">`dotnet clean` -Bir projenin çıkışı temizler.</span><span class="sxs-lookup"><span data-stu-id="f7b02-105">`dotnet clean` - Cleans the output of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f7b02-106">Synopsis</span><span class="sxs-lookup"><span data-stu-id="f7b02-106">Synopsis</span></span>

```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```

## <a name="description"></a><span data-ttu-id="f7b02-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f7b02-107">Description</span></span>

<span data-ttu-id="f7b02-108">`dotnet clean` Komut önceki yapı çıkışını temizler.</span><span class="sxs-lookup"><span data-stu-id="f7b02-108">The `dotnet clean` command cleans the output of the previous build.</span></span> <span data-ttu-id="f7b02-109">Olarak uygulanan bir [MSBuild hedefi](/visualstudio/msbuild/msbuild-targets), projenin komut çalıştırıldığında değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="f7b02-109">It's implemented as an [MSBuild target](/visualstudio/msbuild/msbuild-targets), so the project is evaluated when the command is run.</span></span> <span data-ttu-id="f7b02-110">Yalnızca derleme sırasında oluşturulan çıkışları temizlenir.</span><span class="sxs-lookup"><span data-stu-id="f7b02-110">Only the outputs created during the build are cleaned.</span></span> <span data-ttu-id="f7b02-111">Her iki Orta (*obj*) ve son çıktı (*bin*) klasörler temizlendi.</span><span class="sxs-lookup"><span data-stu-id="f7b02-111">Both intermediate (*obj*) and final output (*bin*) folders are cleaned.</span></span>

## <a name="arguments"></a><span data-ttu-id="f7b02-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="f7b02-112">Arguments</span></span>

`PROJECT`

<span data-ttu-id="f7b02-113">Temizlemek için MSBuild proje.</span><span class="sxs-lookup"><span data-stu-id="f7b02-113">The MSBuild project to clean.</span></span> <span data-ttu-id="f7b02-114">Bir proje dosyası belirtilmezse, MSBuild ile biten bir dosya uzantısına sahip bir dosya için geçerli çalışma dizini arar *proj* ve bu dosyayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="f7b02-114">If a project file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="f7b02-115">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="f7b02-115">Options</span></span>

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="f7b02-116">Derleme yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f7b02-116">Defines the build configuration.</span></span> <span data-ttu-id="f7b02-117">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="f7b02-117">The default value is `Debug`.</span></span> <span data-ttu-id="f7b02-118">Bu seçeneği yalnızca olan derleme zamanında belirtilmişse temizlenirken gerekli.</span><span class="sxs-lookup"><span data-stu-id="f7b02-118">This option is only required when cleaning if you specified it during build time.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f7b02-119">[Framework](../../standard/frameworks.md) oluşturma zamanında belirtildi.</span><span class="sxs-lookup"><span data-stu-id="f7b02-119">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="f7b02-120">Framework tanımlanmalıdır [proje dosyası](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="f7b02-120">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="f7b02-121">Oluşturma zamanında framework belirtilmişse framework temizlenirken belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7b02-121">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

* **`-h|--help`**

  <span data-ttu-id="f7b02-122">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="f7b02-122">Prints out a short help for the command.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="f7b02-123">Dizini, derleme çıktılarını yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f7b02-123">Directory in which the build outputs are placed.</span></span> <span data-ttu-id="f7b02-124">Belirtin `-f|--framework <FRAMEWORK>` çerçeve proje oluşturulduğunda belirttiyseniz çıkış dizini anahtarıyla geçin.</span><span class="sxs-lookup"><span data-stu-id="f7b02-124">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="f7b02-125">Belirtilen çalışma zamanı çıktı klasörünü siler.</span><span class="sxs-lookup"><span data-stu-id="f7b02-125">Cleans the output folder of the specified runtime.</span></span> <span data-ttu-id="f7b02-126">Bu, bir [müstakil dağıtım](../deploying/index.md#self-contained-deployments-scd) oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="f7b02-126">This is used when a [self-contained deployment](../deploying/index.md#self-contained-deployments-scd) was created.</span></span> <span data-ttu-id="f7b02-127">Seçeneği, .NET Core 2.0 SDK'sını itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f7b02-127">Option available since .NET Core 2.0 SDK.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="f7b02-128">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f7b02-128">Sets the verbosity level of the command.</span></span> <span data-ttu-id="f7b02-129">İzin verilen düzeyleri q [uiet], m [en az sıfır], [ormal] n, d [ayrıntılı] ve tanı [tanısı] ' dir.</span><span class="sxs-lookup"><span data-stu-id="f7b02-129">Allowed levels are q[uiet], m[inimal], n[ormal], d[etailed], and diag[nostic].</span></span>

## <a name="examples"></a><span data-ttu-id="f7b02-130">Örnekler</span><span class="sxs-lookup"><span data-stu-id="f7b02-130">Examples</span></span>

* <span data-ttu-id="f7b02-131">Projenin varsayılan derlemeyi temizleme:</span><span class="sxs-lookup"><span data-stu-id="f7b02-131">Clean a default build of the project:</span></span>

  ```console
  dotnet clean
  ```

* <span data-ttu-id="f7b02-132">Yayın Yapılandırması kullanılarak oluşturulan bir projeyi Temizle:</span><span class="sxs-lookup"><span data-stu-id="f7b02-132">Clean a project built using the Release configuration:</span></span>

  ```console
  dotnet clean --configuration Release
  ```