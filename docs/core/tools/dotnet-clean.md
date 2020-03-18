---
title: dotnet temiz komutu
description: Dotnet temiz komutu geçerli dizini temizler.
ms.date: 02/14/2020
ms.openlocfilehash: 186f1ea07718a8e178f88c3d079cf6e2f1f8660b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503747"
---
# <a name="dotnet-clean"></a><span data-ttu-id="db6dd-103">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="db6dd-103">dotnet clean</span></span>

<span data-ttu-id="db6dd-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.x SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="db6dd-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="db6dd-105">Adı</span><span class="sxs-lookup"><span data-stu-id="db6dd-105">Name</span></span>

<span data-ttu-id="db6dd-106">`dotnet clean`- Projenin çıktısını temizler.</span><span class="sxs-lookup"><span data-stu-id="db6dd-106">`dotnet clean` - Cleans the output of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="db6dd-107">Özet</span><span class="sxs-lookup"><span data-stu-id="db6dd-107">Synopsis</span></span>

```dotnetcli
dotnet clean [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--interactive]
    [--nologo] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```

## <a name="description"></a><span data-ttu-id="db6dd-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="db6dd-108">Description</span></span>

<span data-ttu-id="db6dd-109">Komut, `dotnet clean` önceki yapının çıktısını temizler.</span><span class="sxs-lookup"><span data-stu-id="db6dd-109">The `dotnet clean` command cleans the output of the previous build.</span></span> <span data-ttu-id="db6dd-110">MSBuild [hedefi](/visualstudio/msbuild/msbuild-targets)olarak uygulandığından, komut çalıştırıldığında proje değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="db6dd-110">It's implemented as an [MSBuild target](/visualstudio/msbuild/msbuild-targets), so the project is evaluated when the command is run.</span></span> <span data-ttu-id="db6dd-111">Yalnızca yapı sırasında oluşturulan çıktılar temizlenir.</span><span class="sxs-lookup"><span data-stu-id="db6dd-111">Only the outputs created during the build are cleaned.</span></span> <span data-ttu-id="db6dd-112">Hem ara *(obj)* hem de son çıktı *(bin)* klasörleri temizlenir.</span><span class="sxs-lookup"><span data-stu-id="db6dd-112">Both intermediate (*obj*) and final output (*bin*) folders are cleaned.</span></span>

## <a name="arguments"></a><span data-ttu-id="db6dd-113">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="db6dd-113">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="db6dd-114">MSBuild projesi veya çözüm temizlemek için.</span><span class="sxs-lookup"><span data-stu-id="db6dd-114">The MSBuild project or solution to clean.</span></span> <span data-ttu-id="db6dd-115">Bir proje veya çözüm dosyası belirtilmemişse, MSBuild *proj* veya *sln*ile biten ve bu dosyayı kullanan bir dosya uzantısı olan bir dosya için geçerli çalışma dizinini arar.</span><span class="sxs-lookup"><span data-stu-id="db6dd-115">If a project or solution file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* or *sln*, and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="db6dd-116">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="db6dd-116">Options</span></span>

* **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="db6dd-117">Yapı yapılandırmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="db6dd-117">Defines the build configuration.</span></span> <span data-ttu-id="db6dd-118">Çoğu proje için `Debug`varsayılan değer, ancak projenizdeki yapı yapılandırma ayarlarını geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db6dd-118">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span> <span data-ttu-id="db6dd-119">Bu seçenek yalnızca yapı süresi içinde belirttiğiniz zaman temizlik yaparken gereklidir.</span><span class="sxs-lookup"><span data-stu-id="db6dd-119">This option is only required when cleaning if you specified it during build time.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="db6dd-120">Oluşturma zamanında belirtilen [çerçeve.](../../standard/frameworks.md)</span><span class="sxs-lookup"><span data-stu-id="db6dd-120">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="db6dd-121">Çerçeve [proje dosyasında](csproj.md)tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="db6dd-121">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="db6dd-122">Çerçeveyi oluşturma zamanında belirttiyseniz, temizleme sırasında çerçeveyi belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="db6dd-122">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

* **`-h|--help`**

  <span data-ttu-id="db6dd-123">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="db6dd-123">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="db6dd-124">Komutun durmasını ve kullanıcı girişi veya eylemini beklemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="db6dd-124">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="db6dd-125">Örneğin, kimlik doğrulamasını tamamlamak için.</span><span class="sxs-lookup"><span data-stu-id="db6dd-125">For example, to complete authentication.</span></span> <span data-ttu-id="db6dd-126">.NET Core 3.0 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="db6dd-126">Available since .NET Core 3.0 SDK.</span></span>

* **`--nologo`**

  <span data-ttu-id="db6dd-127">Başlangıç bayrağını veya telif hakkı iletisini görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="db6dd-127">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="db6dd-128">.NET Core 3.0 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="db6dd-128">Available since .NET Core 3.0 SDK.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="db6dd-129">Temizlemek için yapı yapıları içeren dizin.</span><span class="sxs-lookup"><span data-stu-id="db6dd-129">The directory that contains the build artifacts to clean.</span></span> <span data-ttu-id="db6dd-130">Proje `-f|--framework <FRAMEWORK>` oluşturulurken çerçeveyi belirttiyseniz, çıkış dizin anahtarıyla anahtarı belirtin.</span><span class="sxs-lookup"><span data-stu-id="db6dd-130">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="db6dd-131">Belirtilen çalışma zamanının çıktı klasörünü temizler.</span><span class="sxs-lookup"><span data-stu-id="db6dd-131">Cleans the output folder of the specified runtime.</span></span> <span data-ttu-id="db6dd-132">Bu, bağımsız bir [dağıtım](../deploying/index.md#publish-self-contained) oluşturulduğunda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="db6dd-132">This is used when a [self-contained deployment](../deploying/index.md#publish-self-contained) was created.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="db6dd-133">MSBuild ayrıntılı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="db6dd-133">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="db6dd-134">İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve .</span><span class="sxs-lookup"><span data-stu-id="db6dd-134">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="db6dd-135">Varsayılan değer: `normal`.</span><span class="sxs-lookup"><span data-stu-id="db6dd-135">The default is `normal`.</span></span>

## <a name="examples"></a><span data-ttu-id="db6dd-136">Örnekler</span><span class="sxs-lookup"><span data-stu-id="db6dd-136">Examples</span></span>

* <span data-ttu-id="db6dd-137">Projenin varsayılan yapısını temizleyin:</span><span class="sxs-lookup"><span data-stu-id="db6dd-137">Clean a default build of the project:</span></span>

  ```dotnetcli
  dotnet clean
  ```

* <span data-ttu-id="db6dd-138">Sürüm yapılandırması kullanılarak oluşturulmuş bir projeyi temizleme:</span><span class="sxs-lookup"><span data-stu-id="db6dd-138">Clean a project built using the Release configuration:</span></span>

  ```dotnetcli
  dotnet clean --configuration Release
  ```
