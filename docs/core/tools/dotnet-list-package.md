---
title: DotNet Listele paket komutu
description: "'Dotnet paket listeleme' komutu, bir proje veya çözüm için paket referanslarını listelemek için uygun bir seçenek sağlar."
ms.date: 04/09/2019
ms.openlocfilehash: bc38b94201f85ed4b22e11722ef5cabcb6fbf040
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59481600"
---
# <a name="dotnet-list-package"></a><span data-ttu-id="e07b3-103">DotNet paket listeleme</span><span class="sxs-lookup"><span data-stu-id="e07b3-103">dotnet list package</span></span>

[!INCLUDE [topic-appliesto-net-core-22plus](../../../includes/topic-appliesto-net-core-22plus.md)]

## <a name="name"></a><span data-ttu-id="e07b3-104">Ad</span><span class="sxs-lookup"><span data-stu-id="e07b3-104">Name</span></span>

<span data-ttu-id="e07b3-105">`dotnet list package` -Bir proje veya çözüm için paket başvuruları listeler.</span><span class="sxs-lookup"><span data-stu-id="e07b3-105">`dotnet list package` - Lists the package references for a project or solution.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e07b3-106">Synopsis</span><span class="sxs-lookup"><span data-stu-id="e07b3-106">Synopsis</span></span>

```
dotnet list [<PROJECT | SOLUTION>] package [--config] [--framework] [--highest-minor] [--highest-patch] 
   [--include-prerelease] [--include-transitive] [--outdated] [--source]
dotnet list package [-h|--help]
```

## <a name="description"></a><span data-ttu-id="e07b3-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e07b3-107">Description</span></span>

<span data-ttu-id="e07b3-108">`dotnet list package` Komut belirli bir proje veya çözüm için NuGet paket başvuruları tüm listelemek için uygun bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="e07b3-108">The `dotnet list package` command provides a convenient option to list all NuGet package references for a specific project or a solution.</span></span> <span data-ttu-id="e07b3-109">Önce bu komutu işlemek gerekli varlıkları için projeyi derlemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="e07b3-109">You first need to build the project in order to have the assets needed for this command to process.</span></span> <span data-ttu-id="e07b3-110">Aşağıdaki örnek, çıktısını gösterir `dotnet list package` komutunu [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) proje:</span><span class="sxs-lookup"><span data-stu-id="e07b3-110">The following example shows the output of the `dotnet list package` command for the [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) project:</span></span>

```output
Project 'SentimentAnalysis' has the following package references
   [netcoreapp2.1]:
   Top-level Package               Requested   Resolved
   > Microsoft.ML                  0.11.0      0.11.0
   > Microsoft.NETCore.App   (A)   [2.1.0, )   2.1.0

(A) : Auto-referenced package.
```

<span data-ttu-id="e07b3-111">**İstenen** sütun proje dosyasında belirtilen Paket sürümü ifade eder ve bir aralık olabilir.</span><span class="sxs-lookup"><span data-stu-id="e07b3-111">The **Requested** column refers to the package version specified in the project file and can be a range.</span></span> <span data-ttu-id="e07b3-112">**Çözümlenmiş** proje şu anda kullanıyor ve her zaman tek bir değer olan sürüm sütununda listelenir.</span><span class="sxs-lookup"><span data-stu-id="e07b3-112">The **Resolved** column lists the version that the project is currently using and is always a single value.</span></span> <span data-ttu-id="e07b3-113">Görüntüleme paketleri bir `(A)` sağ adlarının yanındaki temsil [örtük paket başvuruları](csproj.md#implicit-package-references) proje ayarlarınızdan çıkarılan (`Sdk` türü `<TargetFramework>` veya `<TargetFrameworks>` özelliği, vb..)</span><span class="sxs-lookup"><span data-stu-id="e07b3-113">The packages displaying an `(A)` right next to their names represent [implicit package references](csproj.md#implicit-package-references) that are inferred from your project settings (`Sdk` type, `<TargetFramework>` or `<TargetFrameworks>` property, etc.)</span></span>

<span data-ttu-id="e07b3-114">Kullanım `--outdated` projelerinizde kullandığınız paketlerin daha yeni sürümlerin olup olmadığını öğrenmek için seçeneği.</span><span class="sxs-lookup"><span data-stu-id="e07b3-114">Use the `--outdated` option to find out if there are newer versions available of the packages you're using in your projects.</span></span> <span data-ttu-id="e07b3-115">Varsayılan olarak, `--outdated` çözümlenen sürümünü bir ön sürümünü de olmadığı sürece, en son kararlı paketler listeler.</span><span class="sxs-lookup"><span data-stu-id="e07b3-115">By default, `--outdated` lists the latest stable packages unless the resolved version is also a prerelease version.</span></span> <span data-ttu-id="e07b3-116">Daha yeni sürümlerin listelenmesi zaman ön sürümleri dahil etmek için de belirtmeniz `--include-prerelease` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="e07b3-116">To include prerelease versions when listing newer versions, also specify the `--include-prerelease` option.</span></span> <span data-ttu-id="e07b3-117">Aşağıdaki örnekler çıktısını gösterir `dotnet list package --outdated --include-prerelease` komut önceki örnekteki gibi aynı proje için:</span><span class="sxs-lookup"><span data-stu-id="e07b3-117">The following examples shows the output of the `dotnet list package --outdated --include-prerelease` command for the same project as the previous example:</span></span>

```output
The following sources were used:
   https://api.nuget.org/v3/index.json

Project `SentimentAnalysis` has the following updates to its packages
   [netcoreapp2.1]:
   Top-level Package      Requested   Resolved   Latest
   > Microsoft.ML         0.11.0      0.11.0     1.0.0-preview
```

<span data-ttu-id="e07b3-118">Projenizi geçişli bağımlılıkları, kullanım olup olmadığını bulmak gereken `--include-transitive` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="e07b3-118">If you need to find out whether your project has transitive dependencies, use the `--include-transitive` option.</span></span> <span data-ttu-id="e07b3-119">Sırayla başka bir pakete bağlıdır. projenize bir paket eklerken, geçişli bağımlılıkları oluşur.</span><span class="sxs-lookup"><span data-stu-id="e07b3-119">Transitive dependencies occur when you add a package to your project that in turn relies on another package.</span></span> <span data-ttu-id="e07b3-120">Aşağıdaki örnek çalışan çıktısında `dotnet list package --include-transitive` komutunu [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) en üst düzey paketleri ve bunların bağlı olduğu paketler görüntüleyen proje:</span><span class="sxs-lookup"><span data-stu-id="e07b3-120">The following example shows the output from running the `dotnet list package --include-transitive` command for the [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) project, which displays top-level packages and the packages they depend on:</span></span>

```output
Project 'HelloPlugin' has the following package references
   [netcoreapp3.0]:
   Top-level Package                      Requested                    Resolved
   > Microsoft.NETCore.Platforms    (A)   [3.0.0-preview3.19128.7, )   3.0.0-preview3.19128.7
   > Microsoft.WindowsDesktop.App   (A)   [3.0.0-preview3-27504-2, )   3.0.0-preview3-27504-2

   Transitive Package               Resolved
   > Microsoft.NETCore.Targets      2.0.0
   > PluginBase                     1.0.0

(A) : Auto-referenced package.
```

## <a name="arguments"></a><span data-ttu-id="e07b3-121">Arguments</span><span class="sxs-lookup"><span data-stu-id="e07b3-121">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="e07b3-122">Üzerinde çalışılacak proje veya çözüm dosyası.</span><span class="sxs-lookup"><span data-stu-id="e07b3-122">The project or solution file to operate on.</span></span> <span data-ttu-id="e07b3-123">Belirtilmezse, komut için geçerli dizinde arar.</span><span class="sxs-lookup"><span data-stu-id="e07b3-123">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="e07b3-124">Birden fazla çözüm ya da proje bulunursa, bir hata oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e07b3-124">If more than one solution or project is found, an error is thrown.</span></span>

## <a name="options"></a><span data-ttu-id="e07b3-125">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="e07b3-125">Options</span></span>

* **`--config <SOURCE>`**

  <span data-ttu-id="e07b3-126">Yeni paketleri aramak için kullanılan NuGet kaynakları.</span><span class="sxs-lookup"><span data-stu-id="e07b3-126">The NuGet sources to use when searching for newer packages.</span></span> <span data-ttu-id="e07b3-127">Gerektirir `--outdated` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="e07b3-127">Requires the `--outdated` option.</span></span>

* **`--framework <FRAMEWORK>`**

  <span data-ttu-id="e07b3-128">Yalnızca belirtilen geçerli paketleri görüntüler [hedef Framework'ü](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="e07b3-128">Displays only the packages applicable for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="e07b3-129">Birden çok çerçeveyi belirtmek için bu seçeneği birden çok kez yineleyin.</span><span class="sxs-lookup"><span data-stu-id="e07b3-129">To specify multiple frameworks, repeat the option multiple times.</span></span> <span data-ttu-id="e07b3-130">Örneğin: `--framework netcoreapp2.2 --framework netstandard2.0`</span><span class="sxs-lookup"><span data-stu-id="e07b3-130">For example: `--framework netcoreapp2.2 --framework netstandard2.0`.</span></span>

* **`-h|--help`**

  <span data-ttu-id="e07b3-131">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="e07b3-131">Prints out a short help for the command.</span></span>

* **`--highest-minor`**

  <span data-ttu-id="e07b3-132">Paketler yalnızca eşleşen bir ana sürüm numarası ile yeni paketler için arama yaparken göz önünde bulundurur.</span><span class="sxs-lookup"><span data-stu-id="e07b3-132">Considers only the packages with a matching major version number when searching for newer packages.</span></span> <span data-ttu-id="e07b3-133">Gerektirir `--outdated` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="e07b3-133">Requires the `--outdated` option.</span></span>

* **`--highest-patch`**

  <span data-ttu-id="e07b3-134">Yalnızca eşleşen paketleri büyük ve küçük sürüm numaraları için yeni paketler arama yaparken göz önünde bulundurur.</span><span class="sxs-lookup"><span data-stu-id="e07b3-134">Considers only the packages with a matching major and minor version numbers when searching for newer packages.</span></span> <span data-ttu-id="e07b3-135">Gerektirir `--outdated` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="e07b3-135">Requires the `--outdated` option.</span></span>

* **`--include-prerelease`**

  <span data-ttu-id="e07b3-136">Yayın öncesi sürümler paketlerle yeni paketler için arama yaparken göz önünde bulundurur.</span><span class="sxs-lookup"><span data-stu-id="e07b3-136">Considers packages with prerelease versions when searching for newer packages.</span></span> <span data-ttu-id="e07b3-137">Gerektirir `--outdated` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="e07b3-137">Requires the `--outdated` option.</span></span>

* **`--include-transitive`**

  <span data-ttu-id="e07b3-138">Üst düzey paketlerinin yanı sıra geçişli paketleri listeler.</span><span class="sxs-lookup"><span data-stu-id="e07b3-138">Lists transitive packages, in addition to the top-level packages.</span></span> <span data-ttu-id="e07b3-139">Bu seçeneği belirtmek, üst düzey paketleri bağımlı paketlerin listesini alın.</span><span class="sxs-lookup"><span data-stu-id="e07b3-139">When specifying this option, you get a list of packages that the top-level packages depend on.</span></span>

* **`--outdated`**

  <span data-ttu-id="e07b3-140">Yeni sürümler kullanılabilir olan paketleri listeler.</span><span class="sxs-lookup"><span data-stu-id="e07b3-140">Lists packages that have newer versions available.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="e07b3-141">Yeni paketleri aramak için kullanılan NuGet kaynakları.</span><span class="sxs-lookup"><span data-stu-id="e07b3-141">The NuGet sources to use when searching for newer packages.</span></span> <span data-ttu-id="e07b3-142">Gerektirir `--outdated` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="e07b3-142">Requires the `--outdated` option.</span></span>

## <a name="examples"></a><span data-ttu-id="e07b3-143">Örnekler</span><span class="sxs-lookup"><span data-stu-id="e07b3-143">Examples</span></span>

* <span data-ttu-id="e07b3-144">Belirli bir projenin paket başvuruları listesi:</span><span class="sxs-lookup"><span data-stu-id="e07b3-144">List package references of a specific project:</span></span>

  ```console
  dotnet list SentimentAnalysis.csproj package
  ```

* <span data-ttu-id="e07b3-145">Ön sürümleri dahil olmak üzere, kullanılabilir yeni sürümlere sahip paket başvuruları listesi:</span><span class="sxs-lookup"><span data-stu-id="e07b3-145">List package references that have newer versions available, including prerelease versions:</span></span>

  ```console
  dotnet list package --outdated --include-prerelease
  ```

* <span data-ttu-id="e07b3-146">Belirli hedef çerçeve için paket başvuruları listeleyin:</span><span class="sxs-lookup"><span data-stu-id="e07b3-146">List package references for a specific target framework:</span></span>

  ```console
  dotnet list package --framework netcoreapp3.0
  ```