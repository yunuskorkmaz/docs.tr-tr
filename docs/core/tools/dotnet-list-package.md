---
title: DotNet List paket komutu
description: "' DotNet List Package ' komutu bir proje veya çözümün paket başvurularını listelemek için uygun bir seçenek sağlar."
ms.date: 06/26/2019
ms.openlocfilehash: fe95f3898c5bd85956f4312eb4d20259227e9ff0
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117732"
---
# <a name="dotnet-list-package"></a><span data-ttu-id="1d8d3-103">dotnet list package</span><span class="sxs-lookup"><span data-stu-id="1d8d3-103">dotnet list package</span></span>

[!INCLUDE [topic-appliesto-net-core-22plus](../../../includes/topic-appliesto-net-core-22plus.md)]

## <a name="name"></a><span data-ttu-id="1d8d3-104">Ad</span><span class="sxs-lookup"><span data-stu-id="1d8d3-104">Name</span></span>

<span data-ttu-id="1d8d3-105">`dotnet list package`-Bir proje veya çözüm için paket başvurularını listeler.</span><span class="sxs-lookup"><span data-stu-id="1d8d3-105">`dotnet list package` - Lists the package references for a project or solution.</span></span>

## <a name="synopsis"></a><span data-ttu-id="1d8d3-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="1d8d3-106">Synopsis</span></span>

```dotnetcli
dotnet list [<PROJECT>|<SOLUTION>] package [--config] [--framework] [--highest-minor] [--highest-patch] 
   [--include-prerelease] [--include-transitive] [--interactive] [--outdated] [--source]
dotnet list package [-h|--help]
```

## <a name="description"></a><span data-ttu-id="1d8d3-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1d8d3-107">Description</span></span>

<span data-ttu-id="1d8d3-108">`dotnet list package` Komut belirli bir proje veya çözüm için tüm NuGet paket başvurularını listelemek için uygun bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="1d8d3-108">The `dotnet list package` command provides a convenient option to list all NuGet package references for a specific project or a solution.</span></span> <span data-ttu-id="1d8d3-109">Bu komutun işlemesi için gereken varlıkların olması için öncelikle projeyi derlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1d8d3-109">You first need to build the project in order to have the assets needed for this command to process.</span></span> <span data-ttu-id="1d8d3-110">Aşağıdaki örnek, `dotnet list package` [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) projesi için komutunun çıkışını gösterir:</span><span class="sxs-lookup"><span data-stu-id="1d8d3-110">The following example shows the output of the `dotnet list package` command for the [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) project:</span></span>

```output
Project 'SentimentAnalysis' has the following package references
   [netcoreapp2.1]:
   Top-level Package               Requested   Resolved
   > Microsoft.ML                  0.11.0      0.11.0
   > Microsoft.NETCore.App   (A)   [2.1.0, )   2.1.0

(A) : Auto-referenced package.
```

<span data-ttu-id="1d8d3-111">**İstenen** sütun, proje dosyasında belirtilen paket sürümünü ifade eder ve bir Aralık olabilir.</span><span class="sxs-lookup"><span data-stu-id="1d8d3-111">The **Requested** column refers to the package version specified in the project file and can be a range.</span></span> <span data-ttu-id="1d8d3-112">**Çözümlenen** sütun, projenin şu anda kullandığı sürümü listeler ve her zaman tek bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="1d8d3-112">The **Resolved** column lists the version that the project is currently using and is always a single value.</span></span> <span data-ttu-id="1d8d3-113">Adlarının yanında `(A)` bir doğru görüntülenen paketler, proje `<TargetFramework>` ayarlarından (`Sdk` tür veya `<TargetFrameworks>` özellik, vb.) çıkarılan [örtük paket başvurularını](csproj.md#implicit-package-references) temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1d8d3-113">The packages displaying an `(A)` right next to their names represent [implicit package references](csproj.md#implicit-package-references) that are inferred from your project settings (`Sdk` type, `<TargetFramework>` or `<TargetFrameworks>` property, etc.)</span></span>

<span data-ttu-id="1d8d3-114">Projelerinizde kullanmakta olduğunuz paketlerin yeni sürümlerinin olup olmadığını öğrenmek için seçeneğinikullanın.`--outdated`</span><span class="sxs-lookup"><span data-stu-id="1d8d3-114">Use the `--outdated` option to find out if there are newer versions available of the packages you're using in your projects.</span></span> <span data-ttu-id="1d8d3-115">Varsayılan olarak, `--outdated` çözümlenmiş sürüm aynı zamanda bir ön sürüm sürümü olmadığı takdirde en son kararlı paketleri listeler.</span><span class="sxs-lookup"><span data-stu-id="1d8d3-115">By default, `--outdated` lists the latest stable packages unless the resolved version is also a prerelease version.</span></span> <span data-ttu-id="1d8d3-116">Yeni sürümler listelenirken ön sürüm sürümlerini dahil etmek için `--include-prerelease` seçeneği de belirtin.</span><span class="sxs-lookup"><span data-stu-id="1d8d3-116">To include prerelease versions when listing newer versions, also specify the `--include-prerelease` option.</span></span> <span data-ttu-id="1d8d3-117">Aşağıdaki örneklerde, önceki örnekle aynı proje için `dotnet list package --outdated --include-prerelease` komutun çıktısı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="1d8d3-117">The following examples shows the output of the `dotnet list package --outdated --include-prerelease` command for the same project as the previous example:</span></span>

```output
The following sources were used:
   https://api.nuget.org/v3/index.json

Project `SentimentAnalysis` has the following updates to its packages
   [netcoreapp2.1]:
   Top-level Package      Requested   Resolved   Latest
   > Microsoft.ML         0.11.0      0.11.0     1.0.0-preview
```

<span data-ttu-id="1d8d3-118">Projenizin geçişli bağımlılıklara sahip olup olmadığını bulmanız gerekiyorsa, `--include-transitive` seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="1d8d3-118">If you need to find out whether your project has transitive dependencies, use the `--include-transitive` option.</span></span> <span data-ttu-id="1d8d3-119">Daha sonra başka bir pakete bağımlı olan bir paketi projenize eklediğinizde geçişli bağımlılıklar oluşur.</span><span class="sxs-lookup"><span data-stu-id="1d8d3-119">Transitive dependencies occur when you add a package to your project that in turn relies on another package.</span></span> <span data-ttu-id="1d8d3-120">Aşağıdaki örnek, üst düzey paketleri ve bağımlı oldukları `dotnet list package --include-transitive` paketleri görüntüleyen [helloplugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) projesi için komutu çalıştırmanın çıkışını gösterir:</span><span class="sxs-lookup"><span data-stu-id="1d8d3-120">The following example shows the output from running the `dotnet list package --include-transitive` command for the [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) project, which displays top-level packages and the packages they depend on:</span></span>

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

## <a name="arguments"></a><span data-ttu-id="1d8d3-121">Arguments</span><span class="sxs-lookup"><span data-stu-id="1d8d3-121">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="1d8d3-122">Üzerinde çalışılacak proje veya çözüm dosyası.</span><span class="sxs-lookup"><span data-stu-id="1d8d3-122">The project or solution file to operate on.</span></span> <span data-ttu-id="1d8d3-123">Belirtilmemişse, komut geçerli dizinde bir arama yapar.</span><span class="sxs-lookup"><span data-stu-id="1d8d3-123">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="1d8d3-124">Birden fazla çözüm veya proje bulunursa bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="1d8d3-124">If more than one solution or project is found, an error is thrown.</span></span>

## <a name="options"></a><span data-ttu-id="1d8d3-125">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="1d8d3-125">Options</span></span>

* **`--config <SOURCE>`**

  <span data-ttu-id="1d8d3-126">Yeni paketler aranırken kullanılacak NuGet kaynakları.</span><span class="sxs-lookup"><span data-stu-id="1d8d3-126">The NuGet sources to use when searching for newer packages.</span></span> <span data-ttu-id="1d8d3-127">`--outdated` Seçeneğini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1d8d3-127">Requires the `--outdated` option.</span></span>

* **`--framework <FRAMEWORK>`**

  <span data-ttu-id="1d8d3-128">Yalnızca belirtilen [hedef çerçeve](../../standard/frameworks.md)için geçerli olan paketleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1d8d3-128">Displays only the packages applicable for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="1d8d3-129">Birden çok çerçeve belirtmek için seçeneğini birden çok kez tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="1d8d3-129">To specify multiple frameworks, repeat the option multiple times.</span></span> <span data-ttu-id="1d8d3-130">Örneğin: bağlanmak için yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="1d8d3-130">For example: `--framework netcoreapp2.2 --framework netstandard2.0`.</span></span>

* **`-h|--help`**

  <span data-ttu-id="1d8d3-131">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="1d8d3-131">Prints out a short help for the command.</span></span>

* **`--highest-minor`**

  <span data-ttu-id="1d8d3-132">Daha yeni paketler aranırken yalnızca eşleşen bir ana sürüm numarası olan paketleri dikkate alır.</span><span class="sxs-lookup"><span data-stu-id="1d8d3-132">Considers only the packages with a matching major version number when searching for newer packages.</span></span> <span data-ttu-id="1d8d3-133">`--outdated` Seçeneğini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1d8d3-133">Requires the `--outdated` option.</span></span>

* **`--highest-patch`**

  <span data-ttu-id="1d8d3-134">Yeni paketleri ararken yalnızca eşleşen büyük ve küçük sürüm numaralarına sahip paketleri dikkate alır.</span><span class="sxs-lookup"><span data-stu-id="1d8d3-134">Considers only the packages with a matching major and minor version numbers when searching for newer packages.</span></span> <span data-ttu-id="1d8d3-135">`--outdated` Seçeneğini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1d8d3-135">Requires the `--outdated` option.</span></span>

* **`--include-prerelease`**

  <span data-ttu-id="1d8d3-136">Yeni paketleri ararken paketleri ön sürüm sürümlerini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="1d8d3-136">Considers packages with prerelease versions when searching for newer packages.</span></span> <span data-ttu-id="1d8d3-137">`--outdated` Seçeneğini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1d8d3-137">Requires the `--outdated` option.</span></span>

* **`--include-transitive`**

  <span data-ttu-id="1d8d3-138">Üst düzey paketlerin yanı sıra geçişli paketleri listeler.</span><span class="sxs-lookup"><span data-stu-id="1d8d3-138">Lists transitive packages, in addition to the top-level packages.</span></span> <span data-ttu-id="1d8d3-139">Bu seçeneği belirtirken, üst düzey paketlerin bağımlı olduğu paketlerin bir listesini alırsınız.</span><span class="sxs-lookup"><span data-stu-id="1d8d3-139">When specifying this option, you get a list of packages that the top-level packages depend on.</span></span>

* **`--interactive`**

  <span data-ttu-id="1d8d3-140">Komutun Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="1d8d3-140">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="1d8d3-141">Örneğin, kimlik doğrulamasını tamamlamaya yönelik.</span><span class="sxs-lookup"><span data-stu-id="1d8d3-141">For example, to complete authentication.</span></span> <span data-ttu-id="1d8d3-142">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1d8d3-142">Available since .NET Core 3.0 SDK.</span></span>

* **`--outdated`**

  <span data-ttu-id="1d8d3-143">Daha yeni sürümleri bulunan paketleri listeler.</span><span class="sxs-lookup"><span data-stu-id="1d8d3-143">Lists packages that have newer versions available.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="1d8d3-144">Yeni paketler aranırken kullanılacak NuGet kaynakları.</span><span class="sxs-lookup"><span data-stu-id="1d8d3-144">The NuGet sources to use when searching for newer packages.</span></span> <span data-ttu-id="1d8d3-145">`--outdated` Seçeneğini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1d8d3-145">Requires the `--outdated` option.</span></span>

## <a name="examples"></a><span data-ttu-id="1d8d3-146">Örnekler</span><span class="sxs-lookup"><span data-stu-id="1d8d3-146">Examples</span></span>

* <span data-ttu-id="1d8d3-147">Belirli bir projenin paket başvurularını listeleyin:</span><span class="sxs-lookup"><span data-stu-id="1d8d3-147">List package references of a specific project:</span></span>

  ```dotnetcli
  dotnet list SentimentAnalysis.csproj package
  ```

* <span data-ttu-id="1d8d3-148">Ön sürüm sürümleri dahil olmak üzere daha yeni sürümlere sahip paket başvurularını listeleyin:</span><span class="sxs-lookup"><span data-stu-id="1d8d3-148">List package references that have newer versions available, including prerelease versions:</span></span>

  ```dotnetcli
  dotnet list package --outdated --include-prerelease
  ```

* <span data-ttu-id="1d8d3-149">Belirli bir hedef çerçeve için paket başvurularını listeleyin:</span><span class="sxs-lookup"><span data-stu-id="1d8d3-149">List package references for a specific target framework:</span></span>

  ```dotnetcli
  dotnet list package --framework netcoreapp3.0
  ```
