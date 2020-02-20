---
title: DotNet temizleme komutu
description: DotNet Clean komutu geçerli dizini temizler.
ms.date: 02/14/2020
ms.openlocfilehash: 186f1ea07718a8e178f88c3d079cf6e2f1f8660b
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503747"
---
# <a name="dotnet-clean"></a><span data-ttu-id="9650a-103">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="9650a-103">dotnet clean</span></span>

<span data-ttu-id="9650a-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2. x SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="9650a-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="9650a-105">Adı</span><span class="sxs-lookup"><span data-stu-id="9650a-105">Name</span></span>

<span data-ttu-id="9650a-106">`dotnet clean`-bir projenin çıkışını temizler.</span><span class="sxs-lookup"><span data-stu-id="9650a-106">`dotnet clean` - Cleans the output of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9650a-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="9650a-107">Synopsis</span></span>

```dotnetcli
dotnet clean [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--interactive]
    [--nologo] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```

## <a name="description"></a><span data-ttu-id="9650a-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9650a-108">Description</span></span>

<span data-ttu-id="9650a-109">`dotnet clean` komutu, önceki derleme çıkışını temizler.</span><span class="sxs-lookup"><span data-stu-id="9650a-109">The `dotnet clean` command cleans the output of the previous build.</span></span> <span data-ttu-id="9650a-110">Bir [MSBuild hedefi](/visualstudio/msbuild/msbuild-targets)olarak uygulanır, bu nedenle, komut çalıştırıldığında proje değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="9650a-110">It's implemented as an [MSBuild target](/visualstudio/msbuild/msbuild-targets), so the project is evaluated when the command is run.</span></span> <span data-ttu-id="9650a-111">Yalnızca derleme sırasında oluşturulan çıktılar temizlenir.</span><span class="sxs-lookup"><span data-stu-id="9650a-111">Only the outputs created during the build are cleaned.</span></span> <span data-ttu-id="9650a-112">Ara (*obj*) ve nihai çıkış (*bin*) klasörleri temizlenir.</span><span class="sxs-lookup"><span data-stu-id="9650a-112">Both intermediate (*obj*) and final output (*bin*) folders are cleaned.</span></span>

## <a name="arguments"></a><span data-ttu-id="9650a-113">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="9650a-113">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="9650a-114">Temizleyen MSBuild projesi veya çözümü.</span><span class="sxs-lookup"><span data-stu-id="9650a-114">The MSBuild project or solution to clean.</span></span> <span data-ttu-id="9650a-115">Bir proje veya çözüm dosyası belirtilmemişse, MSBuild, *proj* veya *sln*ile biten bir dosya uzantısına sahip bir dosya için geçerli çalışma dizinini arar ve bu dosyayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="9650a-115">If a project or solution file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* or *sln*, and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="9650a-116">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="9650a-116">Options</span></span>

* **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="9650a-117">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9650a-117">Defines the build configuration.</span></span> <span data-ttu-id="9650a-118">Çoğu proje için varsayılan değer `Debug`, ancak projenizde derleme yapılandırma ayarlarını geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9650a-118">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span> <span data-ttu-id="9650a-119">Bu seçenek yalnızca derleme zamanı sırasında belirtilmişse temizlik sırasında gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9650a-119">This option is only required when cleaning if you specified it during build time.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="9650a-120">Derleme zamanında belirtilen [çerçeve](../../standard/frameworks.md) .</span><span class="sxs-lookup"><span data-stu-id="9650a-120">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="9650a-121">Çerçeve [Proje dosyasında](csproj.md)tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9650a-121">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="9650a-122">Yapı zamanında Framework belirttiyseniz, temizleme sırasında çerçeveyi belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9650a-122">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

* **`-h|--help`**

  <span data-ttu-id="9650a-123">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="9650a-123">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="9650a-124">Komutun Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="9650a-124">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="9650a-125">Örneğin, kimlik doğrulamasını tamamlamaya yönelik.</span><span class="sxs-lookup"><span data-stu-id="9650a-125">For example, to complete authentication.</span></span> <span data-ttu-id="9650a-126">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9650a-126">Available since .NET Core 3.0 SDK.</span></span>

* **`--nologo`**

  <span data-ttu-id="9650a-127">Başlangıç başlığını veya telif hakkı iletisini görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="9650a-127">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="9650a-128">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9650a-128">Available since .NET Core 3.0 SDK.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="9650a-129">Temizleyen derleme yapıtlarını içeren dizin.</span><span class="sxs-lookup"><span data-stu-id="9650a-129">The directory that contains the build artifacts to clean.</span></span> <span data-ttu-id="9650a-130">Projenin oluşturulduğu zaman çerçevesini belirttiyseniz, çıkış dizini anahtarıyla `-f|--framework <FRAMEWORK>` anahtarı belirtin.</span><span class="sxs-lookup"><span data-stu-id="9650a-130">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="9650a-131">Belirtilen çalışma zamanının çıkış klasörünü temizler.</span><span class="sxs-lookup"><span data-stu-id="9650a-131">Cleans the output folder of the specified runtime.</span></span> <span data-ttu-id="9650a-132">Bu, [kendinden bağımsız bir dağıtım](../deploying/index.md#publish-self-contained) oluşturulduğu zaman kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9650a-132">This is used when a [self-contained deployment](../deploying/index.md#publish-self-contained) was created.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="9650a-133">MSBuild ayrıntı düzeyi düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9650a-133">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="9650a-134">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="9650a-134">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="9650a-135">Varsayılan değer: `normal`.</span><span class="sxs-lookup"><span data-stu-id="9650a-135">The default is `normal`.</span></span>

## <a name="examples"></a><span data-ttu-id="9650a-136">Örnekler</span><span class="sxs-lookup"><span data-stu-id="9650a-136">Examples</span></span>

* <span data-ttu-id="9650a-137">Projenin varsayılan derlemesini temizle:</span><span class="sxs-lookup"><span data-stu-id="9650a-137">Clean a default build of the project:</span></span>

  ```dotnetcli
  dotnet clean
  ```

* <span data-ttu-id="9650a-138">Yayın yapılandırması kullanılarak oluşturulan bir projeyi Temizleme:</span><span class="sxs-lookup"><span data-stu-id="9650a-138">Clean a project built using the Release configuration:</span></span>

  ```dotnetcli
  dotnet clean --configuration Release
  ```
