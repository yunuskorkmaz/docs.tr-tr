---
title: DotNet List paket komutu
description: "' DotNet List Package ' komutu bir proje veya çözümün paket başvurularını listelemek için uygun bir seçenek sağlar."
ms.date: 02/14/2020
ms.openlocfilehash: bd275c308c3a213661d5cc6c7e60817620f076a5
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503738"
---
# <a name="dotnet-list-package"></a><span data-ttu-id="2926a-103">dotnet list package</span><span class="sxs-lookup"><span data-stu-id="2926a-103">dotnet list package</span></span>

<span data-ttu-id="2926a-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,2 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="2926a-104">**This article applies to:** ✔️ .NET Core 2.2 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="2926a-105">Adı</span><span class="sxs-lookup"><span data-stu-id="2926a-105">Name</span></span>

<span data-ttu-id="2926a-106">`dotnet list package`-bir proje veya çözüm için paket başvurularını listeler.</span><span class="sxs-lookup"><span data-stu-id="2926a-106">`dotnet list package` - Lists the package references for a project or solution.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2926a-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="2926a-107">Synopsis</span></span>

```dotnetcli
dotnet list [<PROJECT>|<SOLUTION>] package [--config] [--framework] [--highest-minor] [--highest-patch] 
   [--include-prerelease] [--include-transitive] [--interactive] [--outdated] [--source]
dotnet list package [-h|--help]
```

## <a name="description"></a><span data-ttu-id="2926a-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2926a-108">Description</span></span>

<span data-ttu-id="2926a-109">`dotnet list package` komutu, belirli bir proje veya çözüm için tüm NuGet paket başvurularını listelemek için uygun bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="2926a-109">The `dotnet list package` command provides a convenient option to list all NuGet package references for a specific project or a solution.</span></span> <span data-ttu-id="2926a-110">Bu komutun işlemesi için gereken varlıkların olması için öncelikle projeyi derlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2926a-110">You first need to build the project in order to have the assets needed for this command to process.</span></span> <span data-ttu-id="2926a-111">Aşağıdaki örnek, [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) projesi için `dotnet list package` komutunun çıkışını gösterir:</span><span class="sxs-lookup"><span data-stu-id="2926a-111">The following example shows the output of the `dotnet list package` command for the [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) project:</span></span>

```output
Project 'SentimentAnalysis' has the following package references
   [netcoreapp2.1]:
   Top-level Package               Requested   Resolved
   > Microsoft.ML                  1.4.0       1.4.0
   > Microsoft.NETCore.App   (A)   [2.1.0, )   2.1.0

(A) : Auto-referenced package.
```

<span data-ttu-id="2926a-112">**İstenen** sütun, proje dosyasında belirtilen paket sürümünü ifade eder ve bir Aralık olabilir.</span><span class="sxs-lookup"><span data-stu-id="2926a-112">The **Requested** column refers to the package version specified in the project file and can be a range.</span></span> <span data-ttu-id="2926a-113">**Çözümlenen** sütun, projenin şu anda kullandığı sürümü listeler ve her zaman tek bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="2926a-113">The **Resolved** column lists the version that the project is currently using and is always a single value.</span></span> <span data-ttu-id="2926a-114">Adlarının hemen yanında bir `(A)` görüntüleyen paketler, proje ayarlarından (`Sdk` türü, `<TargetFramework>` veya `<TargetFrameworks>` özelliği vb.) çıkarılan [örtük paket başvurularını](csproj.md#implicit-package-references) temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2926a-114">The packages displaying an `(A)` right next to their names represent [implicit package references](csproj.md#implicit-package-references) that are inferred from your project settings (`Sdk` type, `<TargetFramework>` or `<TargetFrameworks>` property, etc.)</span></span>

<span data-ttu-id="2926a-115">Projelerinizde kullanmakta olduğunuz paketlerin yeni sürümlerinin olup olmadığını öğrenmek için `--outdated` seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2926a-115">Use the `--outdated` option to find out if there are newer versions available of the packages you're using in your projects.</span></span> <span data-ttu-id="2926a-116">Varsayılan olarak, çözümlenmiş sürüm aynı zamanda bir ön sürüm sürümü olmadığı takdirde, `--outdated` en son kararlı paketleri listeler.</span><span class="sxs-lookup"><span data-stu-id="2926a-116">By default, `--outdated` lists the latest stable packages unless the resolved version is also a prerelease version.</span></span> <span data-ttu-id="2926a-117">Yeni sürümler listelenirken ön sürüm sürümlerini dahil etmek için `--include-prerelease` seçeneğini de belirtin.</span><span class="sxs-lookup"><span data-stu-id="2926a-117">To include prerelease versions when listing newer versions, also specify the `--include-prerelease` option.</span></span> <span data-ttu-id="2926a-118">Aşağıdaki örneklerde, önceki örnekle aynı proje için `dotnet list package --outdated --include-prerelease` komutunun çıktısı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="2926a-118">The following examples shows the output of the `dotnet list package --outdated --include-prerelease` command for the same project as the previous example:</span></span>

```output
The following sources were used:
   https://api.nuget.org/v3/index.json
   C:\Program Files (x86)\Microsoft SDKs\NuGetPackages\

Project `SentimentAnalysis` has the following updates to its packages
   [netcoreapp2.1]:
   Top-level Package      Requested   Resolved   Latest
   > Microsoft.ML         1.4.0       1.4.0      1.5.0-preview
```

<span data-ttu-id="2926a-119">Projenizin geçişli bağımlılıklara sahip olup olmadığını bulmanız gerekiyorsa `--include-transitive` seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2926a-119">If you need to find out whether your project has transitive dependencies, use the `--include-transitive` option.</span></span> <span data-ttu-id="2926a-120">Daha sonra başka bir pakete bağımlı olan bir paketi projenize eklediğinizde geçişli bağımlılıklar oluşur.</span><span class="sxs-lookup"><span data-stu-id="2926a-120">Transitive dependencies occur when you add a package to your project that in turn relies on another package.</span></span> <span data-ttu-id="2926a-121">Aşağıdaki örnek, üst düzey paketleri ve bağımlı oldukları paketleri görüntüleyen [Helloplugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) projesi için `dotnet list package --include-transitive` komutunu çalıştırmanın çıkışını gösterir:</span><span class="sxs-lookup"><span data-stu-id="2926a-121">The following example shows the output from running the `dotnet list package --include-transitive` command for the [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) project, which displays top-level packages and the packages they depend on:</span></span>

```output
Project 'HelloPlugin' has the following package references
   [netcoreapp3.0]:
   Transitive Package      Resolved
   > PluginBase            1.0.0
```

## <a name="arguments"></a><span data-ttu-id="2926a-122">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="2926a-122">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="2926a-123">Üzerinde çalışılacak proje veya çözüm dosyası.</span><span class="sxs-lookup"><span data-stu-id="2926a-123">The project or solution file to operate on.</span></span> <span data-ttu-id="2926a-124">Belirtilmemişse, komut geçerli dizinde bir arama yapar.</span><span class="sxs-lookup"><span data-stu-id="2926a-124">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="2926a-125">Birden fazla çözüm veya proje bulunursa bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="2926a-125">If more than one solution or project is found, an error is thrown.</span></span>

## <a name="options"></a><span data-ttu-id="2926a-126">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="2926a-126">Options</span></span>

- **`--config <SOURCE>`**

  <span data-ttu-id="2926a-127">Yeni paketler aranırken kullanılacak NuGet kaynakları.</span><span class="sxs-lookup"><span data-stu-id="2926a-127">The NuGet sources to use when searching for newer packages.</span></span> <span data-ttu-id="2926a-128">`--outdated` seçeneğini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="2926a-128">Requires the `--outdated` option.</span></span>

- **`--framework <FRAMEWORK>`**

  <span data-ttu-id="2926a-129">Yalnızca belirtilen [hedef çerçeve](../../standard/frameworks.md)için geçerli olan paketleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2926a-129">Displays only the packages applicable for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="2926a-130">Birden çok çerçeve belirtmek için seçeneğini birden çok kez tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="2926a-130">To specify multiple frameworks, repeat the option multiple times.</span></span> <span data-ttu-id="2926a-131">Örneğin: `--framework netcoreapp2.2 --framework netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="2926a-131">For example: `--framework netcoreapp2.2 --framework netstandard2.0`.</span></span>

- **`-h|--help`**

  <span data-ttu-id="2926a-132">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="2926a-132">Prints out a short help for the command.</span></span>

- **`--highest-minor`**

  <span data-ttu-id="2926a-133">Daha yeni paketler aranırken yalnızca eşleşen bir ana sürüm numarası olan paketleri dikkate alır.</span><span class="sxs-lookup"><span data-stu-id="2926a-133">Considers only the packages with a matching major version number when searching for newer packages.</span></span> <span data-ttu-id="2926a-134">`--outdated` seçeneğini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="2926a-134">Requires the `--outdated` option.</span></span>

- **`--highest-patch`**

  <span data-ttu-id="2926a-135">Yeni paketleri ararken yalnızca eşleşen büyük ve küçük sürüm numaralarına sahip paketleri dikkate alır.</span><span class="sxs-lookup"><span data-stu-id="2926a-135">Considers only the packages with a matching major and minor version numbers when searching for newer packages.</span></span> <span data-ttu-id="2926a-136">`--outdated` seçeneğini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="2926a-136">Requires the `--outdated` option.</span></span>

- **`--include-prerelease`**

  <span data-ttu-id="2926a-137">Yeni paketleri ararken paketleri ön sürüm sürümlerini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="2926a-137">Considers packages with prerelease versions when searching for newer packages.</span></span> <span data-ttu-id="2926a-138">`--outdated` seçeneğini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="2926a-138">Requires the `--outdated` option.</span></span>

- **`--include-transitive`**

  <span data-ttu-id="2926a-139">Üst düzey paketlerin yanı sıra geçişli paketleri listeler.</span><span class="sxs-lookup"><span data-stu-id="2926a-139">Lists transitive packages, in addition to the top-level packages.</span></span> <span data-ttu-id="2926a-140">Bu seçeneği belirtirken, üst düzey paketlerin bağımlı olduğu paketlerin bir listesini alırsınız.</span><span class="sxs-lookup"><span data-stu-id="2926a-140">When specifying this option, you get a list of packages that the top-level packages depend on.</span></span>

- **`--interactive`**

  <span data-ttu-id="2926a-141">Komutun Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="2926a-141">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="2926a-142">Örneğin, kimlik doğrulamasını tamamlamaya yönelik.</span><span class="sxs-lookup"><span data-stu-id="2926a-142">For example, to complete authentication.</span></span> <span data-ttu-id="2926a-143">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2926a-143">Available since .NET Core 3.0 SDK.</span></span>

- **`--outdated`**

  <span data-ttu-id="2926a-144">Daha yeni sürümleri bulunan paketleri listeler.</span><span class="sxs-lookup"><span data-stu-id="2926a-144">Lists packages that have newer versions available.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="2926a-145">Yeni paketler aranırken kullanılacak NuGet kaynakları.</span><span class="sxs-lookup"><span data-stu-id="2926a-145">The NuGet sources to use when searching for newer packages.</span></span> <span data-ttu-id="2926a-146">`--outdated` seçeneğini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="2926a-146">Requires the `--outdated` option.</span></span>

## <a name="examples"></a><span data-ttu-id="2926a-147">Örnekler</span><span class="sxs-lookup"><span data-stu-id="2926a-147">Examples</span></span>

- <span data-ttu-id="2926a-148">Belirli bir projenin paket başvurularını listeleyin:</span><span class="sxs-lookup"><span data-stu-id="2926a-148">List package references of a specific project:</span></span>

  ```dotnetcli
  dotnet list SentimentAnalysis.csproj package
  ```

- <span data-ttu-id="2926a-149">Ön sürüm sürümleri dahil olmak üzere daha yeni sürümlere sahip paket başvurularını listeleyin:</span><span class="sxs-lookup"><span data-stu-id="2926a-149">List package references that have newer versions available, including prerelease versions:</span></span>

  ```dotnetcli
  dotnet list package --outdated --include-prerelease
  ```

- <span data-ttu-id="2926a-150">Belirli bir hedef çerçeve için paket başvurularını listeleyin:</span><span class="sxs-lookup"><span data-stu-id="2926a-150">List package references for a specific target framework:</span></span>

  ```dotnetcli
  dotnet list package --framework netcoreapp3.0
  ```
