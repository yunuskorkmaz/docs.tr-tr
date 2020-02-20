---
title: DotNet temizleme komutu
description: DotNet Clean komutu geçerli dizini temizler.
ms.date: 06/26/2019
ms.openlocfilehash: 715a33a8a1aa13a2a76f9d4522413dcc72e4b4aa
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451362"
---
# <a name="dotnet-clean"></a><span data-ttu-id="30a56-103">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="30a56-103">dotnet clean</span></span>

<span data-ttu-id="30a56-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 1. x SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="30a56-104">**This article applies to:** ✔️ .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="30a56-105">Name</span><span class="sxs-lookup"><span data-stu-id="30a56-105">Name</span></span>

<span data-ttu-id="30a56-106">`dotnet clean`-bir projenin çıkışını temizler.</span><span class="sxs-lookup"><span data-stu-id="30a56-106">`dotnet clean` - Cleans the output of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="30a56-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="30a56-107">Synopsis</span></span>

```dotnetcli
dotnet clean [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--interactive]
    [--nologo] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```

## <a name="description"></a><span data-ttu-id="30a56-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="30a56-108">Description</span></span>

<span data-ttu-id="30a56-109">`dotnet clean` komutu, önceki derleme çıkışını temizler.</span><span class="sxs-lookup"><span data-stu-id="30a56-109">The `dotnet clean` command cleans the output of the previous build.</span></span> <span data-ttu-id="30a56-110">Bir [MSBuild hedefi](/visualstudio/msbuild/msbuild-targets)olarak uygulanır, bu nedenle, komut çalıştırıldığında proje değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="30a56-110">It's implemented as an [MSBuild target](/visualstudio/msbuild/msbuild-targets), so the project is evaluated when the command is run.</span></span> <span data-ttu-id="30a56-111">Yalnızca derleme sırasında oluşturulan çıktılar temizlenir.</span><span class="sxs-lookup"><span data-stu-id="30a56-111">Only the outputs created during the build are cleaned.</span></span> <span data-ttu-id="30a56-112">Ara (*obj*) ve nihai çıkış (*bin*) klasörleri temizlenir.</span><span class="sxs-lookup"><span data-stu-id="30a56-112">Both intermediate (*obj*) and final output (*bin*) folders are cleaned.</span></span>

## <a name="arguments"></a><span data-ttu-id="30a56-113">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="30a56-113">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="30a56-114">Temizleyen MSBuild projesi veya çözümü.</span><span class="sxs-lookup"><span data-stu-id="30a56-114">The MSBuild project or solution to clean.</span></span> <span data-ttu-id="30a56-115">Bir proje veya çözüm dosyası belirtilmemişse, MSBuild, *proj* veya *sln*ile biten bir dosya uzantısına sahip bir dosya için geçerli çalışma dizinini arar ve bu dosyayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="30a56-115">If a project or solution file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* or *sln*, and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="30a56-116">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="30a56-116">Options</span></span>

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="30a56-117">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="30a56-117">Defines the build configuration.</span></span> <span data-ttu-id="30a56-118">Varsayılan değer `Debug` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="30a56-118">The default value is `Debug`.</span></span> <span data-ttu-id="30a56-119">Bu seçenek yalnızca derleme zamanı sırasında belirtilmişse temizlik sırasında gereklidir.</span><span class="sxs-lookup"><span data-stu-id="30a56-119">This option is only required when cleaning if you specified it during build time.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="30a56-120">Derleme zamanında belirtilen [çerçeve](../../standard/frameworks.md) .</span><span class="sxs-lookup"><span data-stu-id="30a56-120">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="30a56-121">Çerçeve [Proje dosyasında](csproj.md)tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="30a56-121">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="30a56-122">Yapı zamanında Framework belirttiyseniz, temizleme sırasında çerçeveyi belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="30a56-122">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

* **`-h|--help`**

  <span data-ttu-id="30a56-123">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="30a56-123">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="30a56-124">Komutun Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="30a56-124">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="30a56-125">Örneğin, kimlik doğrulamasını tamamlamaya yönelik.</span><span class="sxs-lookup"><span data-stu-id="30a56-125">For example, to complete authentication.</span></span> <span data-ttu-id="30a56-126">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="30a56-126">Available since .NET Core 3.0 SDK.</span></span>

* **`--nologo`**

  <span data-ttu-id="30a56-127">Başlangıç başlığını veya telif hakkı iletisini görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="30a56-127">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="30a56-128">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="30a56-128">Available since .NET Core 3.0 SDK.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="30a56-129">Temizleyen derleme yapıtlarını içeren dizin.</span><span class="sxs-lookup"><span data-stu-id="30a56-129">The directory that contains the build artifacts to clean.</span></span> <span data-ttu-id="30a56-130">Projenin oluşturulduğu zaman çerçevesini belirttiyseniz, çıkış dizini anahtarıyla `-f|--framework <FRAMEWORK>` anahtarı belirtin.</span><span class="sxs-lookup"><span data-stu-id="30a56-130">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="30a56-131">Belirtilen çalışma zamanının çıkış klasörünü temizler.</span><span class="sxs-lookup"><span data-stu-id="30a56-131">Cleans the output folder of the specified runtime.</span></span> <span data-ttu-id="30a56-132">Bu, [kendinden bağımsız bir dağıtım](../deploying/index.md#publish-self-contained) oluşturulduğu zaman kullanılır.</span><span class="sxs-lookup"><span data-stu-id="30a56-132">This is used when a [self-contained deployment](../deploying/index.md#publish-self-contained) was created.</span></span> <span data-ttu-id="30a56-133">.NET Core 2,0 SDK 'dan beri kullanılabilir seçeneği.</span><span class="sxs-lookup"><span data-stu-id="30a56-133">Option available since .NET Core 2.0 SDK.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="30a56-134">MSBuild ayrıntı düzeyi düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="30a56-134">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="30a56-135">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="30a56-135">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="30a56-136">Varsayılan, `normal` değeridir.</span><span class="sxs-lookup"><span data-stu-id="30a56-136">The default is `normal`.</span></span>

## <a name="examples"></a><span data-ttu-id="30a56-137">Örnekler</span><span class="sxs-lookup"><span data-stu-id="30a56-137">Examples</span></span>

* <span data-ttu-id="30a56-138">Projenin varsayılan derlemesini temizle:</span><span class="sxs-lookup"><span data-stu-id="30a56-138">Clean a default build of the project:</span></span>

  ```dotnetcli
  dotnet clean
  ```

* <span data-ttu-id="30a56-139">Yayın yapılandırması kullanılarak oluşturulan bir projeyi Temizleme:</span><span class="sxs-lookup"><span data-stu-id="30a56-139">Clean a project built using the Release configuration:</span></span>

  ```dotnetcli
  dotnet clean --configuration Release
  ```
