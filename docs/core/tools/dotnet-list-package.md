---
title: dotnet liste paket komutu
description: "'Dotnet list package' komutu, bir proje veya çözüm için paket başvurularını listelemek için kullanışlı bir seçenek sağlar."
ms.date: 02/14/2020
ms.openlocfilehash: 1cb52b8de10b2eef2ef7465f04316e9446318763
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157238"
---
# <a name="dotnet-list-package"></a><span data-ttu-id="ea6c0-103">dotnet list package</span><span class="sxs-lookup"><span data-stu-id="ea6c0-103">dotnet list package</span></span>

<span data-ttu-id="ea6c0-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.2 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="ea6c0-104">**This article applies to:** ✔️ .NET Core 2.2 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="ea6c0-105">Adı</span><span class="sxs-lookup"><span data-stu-id="ea6c0-105">Name</span></span>

<span data-ttu-id="ea6c0-106">`dotnet list package`- Proje veya çözüm için paket referanslarını listeler.</span><span class="sxs-lookup"><span data-stu-id="ea6c0-106">`dotnet list package` - Lists the package references for a project or solution.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ea6c0-107">Özet</span><span class="sxs-lookup"><span data-stu-id="ea6c0-107">Synopsis</span></span>

```dotnetcli
dotnet list [<PROJECT>|<SOLUTION>] package [--config] [--framework] [--highest-minor] [--highest-patch]
   [--include-prerelease] [--include-transitive] [--interactive] [--outdated] [--source]
dotnet list package [-h|--help]
```

## <a name="description"></a><span data-ttu-id="ea6c0-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea6c0-108">Description</span></span>

<span data-ttu-id="ea6c0-109">Komut, `dotnet list package` belirli bir proje veya çözüm için tüm NuGet paket başvurularını listelemek için kullanışlı bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="ea6c0-109">The `dotnet list package` command provides a convenient option to list all NuGet package references for a specific project or a solution.</span></span> <span data-ttu-id="ea6c0-110">Öncelikle bu komutun işlemesi için gereken varlıklara sahip olmak için projeyi oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ea6c0-110">You first need to build the project in order to have the assets needed for this command to process.</span></span> <span data-ttu-id="ea6c0-111">Aşağıdaki örnek, [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) `dotnet list package` projesi için komutçıktısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="ea6c0-111">The following example shows the output of the `dotnet list package` command for the [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) project:</span></span>

```output
Project 'SentimentAnalysis' has the following package references
   [netcoreapp2.1]:
   Top-level Package               Requested   Resolved
   > Microsoft.ML                  1.4.0       1.4.0
   > Microsoft.NETCore.App   (A)   [2.1.0, )   2.1.0

(A) : Auto-referenced package.
```

<span data-ttu-id="ea6c0-112">**İstenen** sütun, proje dosyasında belirtilen paket sürümüne başvurur ve bir aralık olabilir.</span><span class="sxs-lookup"><span data-stu-id="ea6c0-112">The **Requested** column refers to the package version specified in the project file and can be a range.</span></span> <span data-ttu-id="ea6c0-113">**Çözümlenen** sütun, projenin şu anda kullanmakta olduğu sürümü listeler ve her zaman tek bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="ea6c0-113">The **Resolved** column lists the version that the project is currently using and is always a single value.</span></span> <span data-ttu-id="ea6c0-114">Adlarının yanında `(A)` bir hakkı görüntüleyen paketler, proje ayarlarınızdan (tür `<TargetFramework>` `<TargetFrameworks>` veya`Sdk` özellik, vb.) çıkarılan [örtük paket başvurularını](csproj.md#implicit-package-references) temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ea6c0-114">The packages displaying an `(A)` right next to their names represent [implicit package references](csproj.md#implicit-package-references) that are inferred from your project settings (`Sdk` type, `<TargetFramework>` or `<TargetFrameworks>` property, etc.)</span></span>

<span data-ttu-id="ea6c0-115">Projelerinizde `--outdated` kullanmakta olduğunuz paketlerin daha yeni sürümlerinin olup olmadığını öğrenmek için seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="ea6c0-115">Use the `--outdated` option to find out if there are newer versions available of the packages you're using in your projects.</span></span> <span data-ttu-id="ea6c0-116">Varsayılan olarak, `--outdated` çözülen sürüm de bir ön sürüm olmadığı sürece en son kararlı paketleri listeler.</span><span class="sxs-lookup"><span data-stu-id="ea6c0-116">By default, `--outdated` lists the latest stable packages unless the resolved version is also a prerelease version.</span></span> <span data-ttu-id="ea6c0-117">Yeni sürümleri listelerken yayın öncesi sürümleri eklemek `--include-prerelease` için de seçeneği belirtin.</span><span class="sxs-lookup"><span data-stu-id="ea6c0-117">To include prerelease versions when listing newer versions, also specify the `--include-prerelease` option.</span></span> <span data-ttu-id="ea6c0-118">Aşağıdaki örnekler, önceki örnekle aynı proje için `dotnet list package --outdated --include-prerelease` komutun çıktısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="ea6c0-118">The following examples shows the output of the `dotnet list package --outdated --include-prerelease` command for the same project as the previous example:</span></span>

```output
The following sources were used:
   https://api.nuget.org/v3/index.json
   C:\Program Files (x86)\Microsoft SDKs\NuGetPackages\

Project `SentimentAnalysis` has the following updates to its packages
   [netcoreapp2.1]:
   Top-level Package      Requested   Resolved   Latest
   > Microsoft.ML         1.4.0       1.4.0      1.5.0-preview
```

<span data-ttu-id="ea6c0-119">Projenizin geçişli bağımlılıkları olup olmadığını öğrenmeniz gerekiyorsa, `--include-transitive` seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="ea6c0-119">If you need to find out whether your project has transitive dependencies, use the `--include-transitive` option.</span></span> <span data-ttu-id="ea6c0-120">Geçişli bağımlılıklar, projenize başka bir pakete dayanan bir paket eklediğinizde oluşur.</span><span class="sxs-lookup"><span data-stu-id="ea6c0-120">Transitive dependencies occur when you add a package to your project that in turn relies on another package.</span></span> <span data-ttu-id="ea6c0-121">Aşağıdaki örnek, üst düzey `dotnet list package --include-transitive` paketleri ve bağlı oldukları paketleri görüntüleyen [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) projesi nin komutunu çalıştıran çıktıyı gösterir:</span><span class="sxs-lookup"><span data-stu-id="ea6c0-121">The following example shows the output from running the `dotnet list package --include-transitive` command for the [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) project, which displays top-level packages and the packages they depend on:</span></span>

```output
Project 'HelloPlugin' has the following package references
   [netcoreapp3.0]:
   Transitive Package      Resolved
   > PluginBase            1.0.0
```

## <a name="arguments"></a><span data-ttu-id="ea6c0-122">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="ea6c0-122">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="ea6c0-123">İşletilmesi gereken proje veya çözüm dosyası.</span><span class="sxs-lookup"><span data-stu-id="ea6c0-123">The project or solution file to operate on.</span></span> <span data-ttu-id="ea6c0-124">Belirtilmemişse, komut geçerli dizini arar.</span><span class="sxs-lookup"><span data-stu-id="ea6c0-124">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="ea6c0-125">Birden fazla çözüm veya proje bulunursa, bir hata atılır.</span><span class="sxs-lookup"><span data-stu-id="ea6c0-125">If more than one solution or project is found, an error is thrown.</span></span>

## <a name="options"></a><span data-ttu-id="ea6c0-126">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="ea6c0-126">Options</span></span>

- **`--config <SOURCE>`**

  <span data-ttu-id="ea6c0-127">NuGet kaynakları yeni paketler ararken kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="ea6c0-127">The NuGet sources to use when searching for newer packages.</span></span> <span data-ttu-id="ea6c0-128">`--outdated` Seçeneği gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ea6c0-128">Requires the `--outdated` option.</span></span>

- **`--framework <FRAMEWORK>`**

  <span data-ttu-id="ea6c0-129">Yalnızca belirtilen [hedef çerçeve](../../standard/frameworks.md)için geçerli paketleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ea6c0-129">Displays only the packages applicable for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="ea6c0-130">Birden çok çerçeve belirtmek için seçeneği birden çok kez yineleyin.</span><span class="sxs-lookup"><span data-stu-id="ea6c0-130">To specify multiple frameworks, repeat the option multiple times.</span></span> <span data-ttu-id="ea6c0-131">Örneğin: `--framework netcoreapp2.2 --framework netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="ea6c0-131">For example: `--framework netcoreapp2.2 --framework netstandard2.0`.</span></span>

- **`-h|--help`**

  <span data-ttu-id="ea6c0-132">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="ea6c0-132">Prints out a short help for the command.</span></span>

- **`--highest-minor`**

  <span data-ttu-id="ea6c0-133">Yeni paketleri ararken yalnızca eşleşen bir ana sürüm numarasına sahip paketleri dikkate alır.</span><span class="sxs-lookup"><span data-stu-id="ea6c0-133">Considers only the packages with a matching major version number when searching for newer packages.</span></span> <span data-ttu-id="ea6c0-134">`--outdated` Seçeneği gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ea6c0-134">Requires the `--outdated` option.</span></span>

- **`--highest-patch`**

  <span data-ttu-id="ea6c0-135">Yeni paketleri ararken yalnızca eşleşen büyük ve küçük sürüm numaralarına sahip paketleri dikkate alır.</span><span class="sxs-lookup"><span data-stu-id="ea6c0-135">Considers only the packages with a matching major and minor version numbers when searching for newer packages.</span></span> <span data-ttu-id="ea6c0-136">`--outdated` Seçeneği gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ea6c0-136">Requires the `--outdated` option.</span></span>

- **`--include-prerelease`**

  <span data-ttu-id="ea6c0-137">Yeni paketler ararken yayın öncesi sürümsürümlerine sahip paketleri dikkate alır.</span><span class="sxs-lookup"><span data-stu-id="ea6c0-137">Considers packages with prerelease versions when searching for newer packages.</span></span> <span data-ttu-id="ea6c0-138">`--outdated` Seçeneği gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ea6c0-138">Requires the `--outdated` option.</span></span>

- **`--include-transitive`**

  <span data-ttu-id="ea6c0-139">Üst düzey paketlere ek olarak geçişli paketleri listeler.</span><span class="sxs-lookup"><span data-stu-id="ea6c0-139">Lists transitive packages, in addition to the top-level packages.</span></span> <span data-ttu-id="ea6c0-140">Bu seçeneği belirtirken, üst düzey paketlerin bağlı olduğu paketlerin bir listesini alırsınız.</span><span class="sxs-lookup"><span data-stu-id="ea6c0-140">When specifying this option, you get a list of packages that the top-level packages depend on.</span></span>

- **`--interactive`**

  <span data-ttu-id="ea6c0-141">Komutun durmasını ve kullanıcı girişi veya eylemini beklemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ea6c0-141">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="ea6c0-142">Örneğin, kimlik doğrulamasını tamamlamak için.</span><span class="sxs-lookup"><span data-stu-id="ea6c0-142">For example, to complete authentication.</span></span> <span data-ttu-id="ea6c0-143">.NET Core 3.0 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="ea6c0-143">Available since .NET Core 3.0 SDK.</span></span>

- **`--outdated`**

  <span data-ttu-id="ea6c0-144">Yeni sürümleri olan paketleri listeler.</span><span class="sxs-lookup"><span data-stu-id="ea6c0-144">Lists packages that have newer versions available.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="ea6c0-145">NuGet kaynakları yeni paketler ararken kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="ea6c0-145">The NuGet sources to use when searching for newer packages.</span></span> <span data-ttu-id="ea6c0-146">`--outdated` Seçeneği gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ea6c0-146">Requires the `--outdated` option.</span></span>

## <a name="examples"></a><span data-ttu-id="ea6c0-147">Örnekler</span><span class="sxs-lookup"><span data-stu-id="ea6c0-147">Examples</span></span>

- <span data-ttu-id="ea6c0-148">Belirli bir projenin paket başvurularını listele:</span><span class="sxs-lookup"><span data-stu-id="ea6c0-148">List package references of a specific project:</span></span>

  ```dotnetcli
  dotnet list SentimentAnalysis.csproj package
  ```

- <span data-ttu-id="ea6c0-149">Sürüm öncesi sürümler de dahil olmak üzere daha yeni sürümleri olan paket başvurularını listele:</span><span class="sxs-lookup"><span data-stu-id="ea6c0-149">List package references that have newer versions available, including prerelease versions:</span></span>

  ```dotnetcli
  dotnet list package --outdated --include-prerelease
  ```

- <span data-ttu-id="ea6c0-150">Belirli bir hedef çerçeve için paket başvurularını listele:</span><span class="sxs-lookup"><span data-stu-id="ea6c0-150">List package references for a specific target framework:</span></span>

  ```dotnetcli
  dotnet list package --framework netcoreapp3.0
  ```
