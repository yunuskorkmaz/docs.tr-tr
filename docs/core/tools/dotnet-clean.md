---
title: DotNet temizleme komutu
description: Dotnet temiz komut geçerli dizinde temizler.
ms.date: 06/26/2019
ms.openlocfilehash: 36630c046ff8f1ad8d513b4e64cfb74a8625776b
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67422013"
---
# <a name="dotnet-clean"></a><span data-ttu-id="00ae0-103">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="00ae0-103">dotnet clean</span></span>

<span data-ttu-id="00ae0-104">**Bu konu için geçerlidir: ✓** .NET Core SDK'sı 1.x ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="00ae0-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="00ae0-105">Ad</span><span class="sxs-lookup"><span data-stu-id="00ae0-105">Name</span></span>

<span data-ttu-id="00ae0-106">`dotnet clean` -Bir projenin çıkışı temizler.</span><span class="sxs-lookup"><span data-stu-id="00ae0-106">`dotnet clean` - Cleans the output of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="00ae0-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="00ae0-107">Synopsis</span></span>

```
dotnet clean [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--interactive] 
    [--nologo] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```

## <a name="description"></a><span data-ttu-id="00ae0-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="00ae0-108">Description</span></span>

<span data-ttu-id="00ae0-109">`dotnet clean` Komut önceki yapı çıkışını temizler.</span><span class="sxs-lookup"><span data-stu-id="00ae0-109">The `dotnet clean` command cleans the output of the previous build.</span></span> <span data-ttu-id="00ae0-110">Olarak uygulanan bir [MSBuild hedefi](/visualstudio/msbuild/msbuild-targets), projenin komut çalıştırıldığında değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="00ae0-110">It's implemented as an [MSBuild target](/visualstudio/msbuild/msbuild-targets), so the project is evaluated when the command is run.</span></span> <span data-ttu-id="00ae0-111">Yalnızca derleme sırasında oluşturulan çıkışları temizlenir.</span><span class="sxs-lookup"><span data-stu-id="00ae0-111">Only the outputs created during the build are cleaned.</span></span> <span data-ttu-id="00ae0-112">Her iki Orta (*obj*) ve son çıktı (*bin*) klasörler temizlendi.</span><span class="sxs-lookup"><span data-stu-id="00ae0-112">Both intermediate (*obj*) and final output (*bin*) folders are cleaned.</span></span>

## <a name="arguments"></a><span data-ttu-id="00ae0-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="00ae0-113">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="00ae0-114">MSBuild proje veya çözüm temizlenemedi.</span><span class="sxs-lookup"><span data-stu-id="00ae0-114">The MSBuild project or solution to clean.</span></span> <span data-ttu-id="00ae0-115">Bir proje veya çözüm dosyası belirtilmezse, MSBuild ile biten bir dosya uzantısına sahip bir dosya için geçerli çalışma dizini arar *proj* veya *sln*ve bu dosyayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="00ae0-115">If a project or solution file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* or *sln*, and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="00ae0-116">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="00ae0-116">Options</span></span>

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="00ae0-117">Derleme yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="00ae0-117">Defines the build configuration.</span></span> <span data-ttu-id="00ae0-118">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="00ae0-118">The default value is `Debug`.</span></span> <span data-ttu-id="00ae0-119">Bu seçeneği yalnızca olan derleme zamanında belirtilmişse temizlenirken gerekli.</span><span class="sxs-lookup"><span data-stu-id="00ae0-119">This option is only required when cleaning if you specified it during build time.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="00ae0-120">[Framework](../../standard/frameworks.md) oluşturma zamanında belirtildi.</span><span class="sxs-lookup"><span data-stu-id="00ae0-120">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="00ae0-121">Framework tanımlanmalıdır [proje dosyası](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="00ae0-121">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="00ae0-122">Oluşturma zamanında framework belirtilmişse framework temizlenirken belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="00ae0-122">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

* **`-h|--help`**

  <span data-ttu-id="00ae0-123">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="00ae0-123">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="00ae0-124">Durdurmak ve kullanıcı girişi ya da eylem için beklemek için komutu sağlar.</span><span class="sxs-lookup"><span data-stu-id="00ae0-124">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="00ae0-125">Örneğin, kimlik doğrulamasını tamamlamak için.</span><span class="sxs-lookup"><span data-stu-id="00ae0-125">For example, to complete authentication.</span></span> <span data-ttu-id="00ae0-126">.NET Core SDK 3.0 bu yana kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="00ae0-126">Available since .NET Core 3.0 SDK.</span></span>

* **`--nologo`**

  <span data-ttu-id="00ae0-127">Başlangıç başlığını veya telif hakkı iletisini görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="00ae0-127">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="00ae0-128">.NET Core SDK 3.0 bu yana kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="00ae0-128">Available since .NET Core 3.0 SDK.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="00ae0-129">Temizlemek için derleme yapıtları içeren dizin.</span><span class="sxs-lookup"><span data-stu-id="00ae0-129">The directory that contains the build artifacts to clean.</span></span> <span data-ttu-id="00ae0-130">Belirtin `-f|--framework <FRAMEWORK>` çerçeve proje oluşturulduğunda belirttiyseniz çıkış dizini anahtarıyla geçin.</span><span class="sxs-lookup"><span data-stu-id="00ae0-130">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="00ae0-131">Belirtilen çalışma zamanı çıktı klasörünü siler.</span><span class="sxs-lookup"><span data-stu-id="00ae0-131">Cleans the output folder of the specified runtime.</span></span> <span data-ttu-id="00ae0-132">Bu, bir [müstakil dağıtım](../deploying/index.md#self-contained-deployments-scd) oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="00ae0-132">This is used when a [self-contained deployment](../deploying/index.md#self-contained-deployments-scd) was created.</span></span> <span data-ttu-id="00ae0-133">Seçeneği, .NET Core 2.0 SDK'sını itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="00ae0-133">Option available since .NET Core 2.0 SDK.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="00ae0-134">MSBuild ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="00ae0-134">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="00ae0-135">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="00ae0-135">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="00ae0-136">Varsayılan, `normal` değeridir.</span><span class="sxs-lookup"><span data-stu-id="00ae0-136">The default is `normal`.</span></span>

## <a name="examples"></a><span data-ttu-id="00ae0-137">Örnekler</span><span class="sxs-lookup"><span data-stu-id="00ae0-137">Examples</span></span>

* <span data-ttu-id="00ae0-138">Projenin varsayılan derlemeyi temizleme:</span><span class="sxs-lookup"><span data-stu-id="00ae0-138">Clean a default build of the project:</span></span>

  ```console
  dotnet clean
  ```

* <span data-ttu-id="00ae0-139">Yayın Yapılandırması kullanılarak oluşturulan bir projeyi Temizle:</span><span class="sxs-lookup"><span data-stu-id="00ae0-139">Clean a project built using the Release configuration:</span></span>

  ```console
  dotnet clean --configuration Release
  ```
