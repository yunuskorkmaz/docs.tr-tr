---
title: DotNet List paket komutu
description: "' DotNet List Package ' komutu bir proje veya çözümün paket başvurularını listelemek için uygun bir seçenek sağlar."
ms.date: 02/14/2020
ms.openlocfilehash: 7157e56860936d10aa322854a589ae89e2bc0826
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164760"
---
# <a name="dotnet-list-package"></a><span data-ttu-id="f2142-103">dotnet list package</span><span class="sxs-lookup"><span data-stu-id="f2142-103">dotnet list package</span></span>

<span data-ttu-id="f2142-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,2 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="f2142-104">**This article applies to:** ✔️ .NET Core 2.2 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="f2142-105">Ad</span><span class="sxs-lookup"><span data-stu-id="f2142-105">Name</span></span>

<span data-ttu-id="f2142-106">`dotnet list package`-Bir proje veya çözüm için paket başvurularını listeler.</span><span class="sxs-lookup"><span data-stu-id="f2142-106">`dotnet list package` - Lists the package references for a project or solution.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f2142-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="f2142-107">Synopsis</span></span>

```dotnetcli
dotnet list [<PROJECT>|<SOLUTION>] package [--config <SOURCE>]
    [--deprecated]
    [--framework <FRAMEWORK>] [--highest-minor] [--highest-patch]
    [--include-prerelease] [--include-transitive] [--interactive]
    [--outdated] [--source <SOURCE>]

dotnet list package -h|--help
```

## <a name="description"></a><span data-ttu-id="f2142-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2142-108">Description</span></span>

<span data-ttu-id="f2142-109">`dotnet list package`Komut belirli bir proje veya çözüm için tüm NuGet paket başvurularını listelemek için uygun bir seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="f2142-109">The `dotnet list package` command provides a convenient option to list all NuGet package references for a specific project or a solution.</span></span> <span data-ttu-id="f2142-110">Bu komutun işlemesi için gereken varlıkların olması için öncelikle projeyi derlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f2142-110">You first need to build the project in order to have the assets needed for this command to process.</span></span> <span data-ttu-id="f2142-111">Aşağıdaki örnek, `dotnet list package` [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) projesi için komutunun çıkışını gösterir:</span><span class="sxs-lookup"><span data-stu-id="f2142-111">The following example shows the output of the `dotnet list package` command for the [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) project:</span></span>

```output
Project 'SentimentAnalysis' has the following package references
   [netcoreapp2.1]:
   Top-level Package               Requested   Resolved
   > Microsoft.ML                  1.4.0       1.4.0
   > Microsoft.NETCore.App   (A)   [2.1.0, )   2.1.0

(A) : Auto-referenced package.
```

<span data-ttu-id="f2142-112">**İstenen** sütun, proje dosyasında belirtilen paket sürümünü ifade eder ve bir Aralık olabilir.</span><span class="sxs-lookup"><span data-stu-id="f2142-112">The **Requested** column refers to the package version specified in the project file and can be a range.</span></span> <span data-ttu-id="f2142-113">**Çözümlenen** sütun, projenin şu anda kullandığı sürümü listeler ve her zaman tek bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="f2142-113">The **Resolved** column lists the version that the project is currently using and is always a single value.</span></span> <span data-ttu-id="f2142-114">Adlarının yanında bir doğru görüntülenen paketler, `(A)` Proje ayarlarından ( [implicit package references](csproj.md#implicit-package-references) `Sdk` tür `<TargetFramework>` veya `<TargetFrameworks>` özellik, vb.) çıkarılan örtük paket başvurularını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f2142-114">The packages displaying an `(A)` right next to their names represent [implicit package references](csproj.md#implicit-package-references) that are inferred from your project settings (`Sdk` type, `<TargetFramework>` or `<TargetFrameworks>` property, etc.)</span></span>

<span data-ttu-id="f2142-115">`--outdated`Projelerinizde kullanmakta olduğunuz paketlerin yeni sürümlerinin olup olmadığını öğrenmek için seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f2142-115">Use the `--outdated` option to find out if there are newer versions available of the packages you're using in your projects.</span></span> <span data-ttu-id="f2142-116">Varsayılan olarak, `--outdated` Çözümlenmiş sürüm aynı zamanda bir ön sürüm sürümü olmadığı takdirde en son kararlı paketleri listeler.</span><span class="sxs-lookup"><span data-stu-id="f2142-116">By default, `--outdated` lists the latest stable packages unless the resolved version is also a prerelease version.</span></span> <span data-ttu-id="f2142-117">Yeni sürümler listelenirken ön sürüm sürümlerini dahil etmek için seçeneği de belirtin `--include-prerelease` .</span><span class="sxs-lookup"><span data-stu-id="f2142-117">To include prerelease versions when listing newer versions, also specify the `--include-prerelease` option.</span></span> <span data-ttu-id="f2142-118">Aşağıdaki örneklerde, `dotnet list package --outdated --include-prerelease` önceki örnekle aynı proje için komutun çıktısı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="f2142-118">The following examples shows the output of the `dotnet list package --outdated --include-prerelease` command for the same project as the previous example:</span></span>

```output
The following sources were used:
   https://api.nuget.org/v3/index.json
   C:\Program Files (x86)\Microsoft SDKs\NuGetPackages\

Project `SentimentAnalysis` has the following updates to its packages
   [netcoreapp2.1]:
   Top-level Package      Requested   Resolved   Latest
   > Microsoft.ML         1.4.0       1.4.0      1.5.0-preview
```

<span data-ttu-id="f2142-119">Projenizin geçişli bağımlılıklara sahip olup olmadığını bulmanız gerekiyorsa, `--include-transitive` seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f2142-119">If you need to find out whether your project has transitive dependencies, use the `--include-transitive` option.</span></span> <span data-ttu-id="f2142-120">Daha sonra başka bir pakete bağımlı olan bir paketi projenize eklediğinizde geçişli bağımlılıklar oluşur.</span><span class="sxs-lookup"><span data-stu-id="f2142-120">Transitive dependencies occur when you add a package to your project that in turn relies on another package.</span></span> <span data-ttu-id="f2142-121">Aşağıdaki örnek, `dotnet list package --include-transitive` üst düzey paketleri ve bağımlı oldukları paketleri görüntüleyen [helloplugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) projesi için komutu çalıştırmanın çıkışını gösterir:</span><span class="sxs-lookup"><span data-stu-id="f2142-121">The following example shows the output from running the `dotnet list package --include-transitive` command for the [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) project, which displays top-level packages and the packages they depend on:</span></span>

```output
Project 'HelloPlugin' has the following package references
   [netcoreapp3.0]:
   Transitive Package      Resolved
   > PluginBase            1.0.0
```

## <a name="arguments"></a><span data-ttu-id="f2142-122">Arguments</span><span class="sxs-lookup"><span data-stu-id="f2142-122">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="f2142-123">Üzerinde çalışılacak proje veya çözüm dosyası.</span><span class="sxs-lookup"><span data-stu-id="f2142-123">The project or solution file to operate on.</span></span> <span data-ttu-id="f2142-124">Belirtilmemişse, komut geçerli dizinde bir arama yapar.</span><span class="sxs-lookup"><span data-stu-id="f2142-124">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="f2142-125">Birden fazla çözüm veya proje bulunursa bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="f2142-125">If more than one solution or project is found, an error is thrown.</span></span>

## <a name="options"></a><span data-ttu-id="f2142-126">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="f2142-126">Options</span></span>

- **`--config <SOURCE>`**

  <span data-ttu-id="f2142-127">Yeni paketler aranırken kullanılacak NuGet kaynakları.</span><span class="sxs-lookup"><span data-stu-id="f2142-127">The NuGet sources to use when searching for newer packages.</span></span> <span data-ttu-id="f2142-128">Seçeneğini gerektirir `--outdated` .</span><span class="sxs-lookup"><span data-stu-id="f2142-128">Requires the `--outdated` option.</span></span>

- **`--deprecated`**

  <span data-ttu-id="f2142-129">Kullanım dışı bırakılan paketleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f2142-129">Displays packages that have been deprecated.</span></span>

- **`--framework <FRAMEWORK>`**

  <span data-ttu-id="f2142-130">Yalnızca belirtilen [hedef çerçeve](../../standard/frameworks.md)için geçerli olan paketleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f2142-130">Displays only the packages applicable for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="f2142-131">Birden çok çerçeve belirtmek için seçeneğini birden çok kez tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="f2142-131">To specify multiple frameworks, repeat the option multiple times.</span></span> <span data-ttu-id="f2142-132">Örneğin: `--framework netcoreapp2.2 --framework netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="f2142-132">For example: `--framework netcoreapp2.2 --framework netstandard2.0`.</span></span>

- **`-h|--help`**

  <span data-ttu-id="f2142-133">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="f2142-133">Prints out a short help for the command.</span></span>

- **`--highest-minor`**

  <span data-ttu-id="f2142-134">Daha yeni paketler aranırken yalnızca eşleşen bir ana sürüm numarası olan paketleri dikkate alır.</span><span class="sxs-lookup"><span data-stu-id="f2142-134">Considers only the packages with a matching major version number when searching for newer packages.</span></span> <span data-ttu-id="f2142-135">`--outdated`Veya seçeneğini gerektirir `--deprecated` .</span><span class="sxs-lookup"><span data-stu-id="f2142-135">Requires the `--outdated` or `--deprecated` option.</span></span>

- **`--highest-patch`**

  <span data-ttu-id="f2142-136">Yeni paketleri ararken yalnızca eşleşen büyük ve küçük sürüm numaralarına sahip paketleri dikkate alır.</span><span class="sxs-lookup"><span data-stu-id="f2142-136">Considers only the packages with a matching major and minor version numbers when searching for newer packages.</span></span> <span data-ttu-id="f2142-137">`--outdated`Veya seçeneğini gerektirir `--deprecated` .</span><span class="sxs-lookup"><span data-stu-id="f2142-137">Requires the `--outdated` or `--deprecated` option.</span></span>

- **`--include-prerelease`**

  <span data-ttu-id="f2142-138">Yeni paketleri ararken paketleri ön sürüm sürümlerini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="f2142-138">Considers packages with prerelease versions when searching for newer packages.</span></span> <span data-ttu-id="f2142-139">`--outdated`Veya seçeneğini gerektirir `--deprecated` .</span><span class="sxs-lookup"><span data-stu-id="f2142-139">Requires the `--outdated` or `--deprecated` option.</span></span>

- **`--include-transitive`**

  <span data-ttu-id="f2142-140">Üst düzey paketlerin yanı sıra geçişli paketleri listeler.</span><span class="sxs-lookup"><span data-stu-id="f2142-140">Lists transitive packages, in addition to the top-level packages.</span></span> <span data-ttu-id="f2142-141">Bu seçeneği belirtirken, üst düzey paketlerin bağımlı olduğu paketlerin bir listesini alırsınız.</span><span class="sxs-lookup"><span data-stu-id="f2142-141">When specifying this option, you get a list of packages that the top-level packages depend on.</span></span>

- **`--interactive`**

  <span data-ttu-id="f2142-142">Komutun Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="f2142-142">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="f2142-143">Örneğin, kimlik doğrulamasını tamamlamaya yönelik.</span><span class="sxs-lookup"><span data-stu-id="f2142-143">For example, to complete authentication.</span></span> <span data-ttu-id="f2142-144">.NET Core 3,0 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f2142-144">Available since .NET Core 3.0 SDK.</span></span>

- **`--outdated`**

  <span data-ttu-id="f2142-145">Daha yeni sürümleri bulunan paketleri listeler.</span><span class="sxs-lookup"><span data-stu-id="f2142-145">Lists packages that have newer versions available.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="f2142-146">Yeni paketler aranırken kullanılacak NuGet kaynakları.</span><span class="sxs-lookup"><span data-stu-id="f2142-146">The NuGet sources to use when searching for newer packages.</span></span> <span data-ttu-id="f2142-147">`--outdated`Veya seçeneğini gerektirir `--deprecated` .</span><span class="sxs-lookup"><span data-stu-id="f2142-147">Requires the `--outdated` or `--deprecated` option.</span></span>

## <a name="examples"></a><span data-ttu-id="f2142-148">Örnekler</span><span class="sxs-lookup"><span data-stu-id="f2142-148">Examples</span></span>

- <span data-ttu-id="f2142-149">Belirli bir projenin paket başvurularını listeleyin:</span><span class="sxs-lookup"><span data-stu-id="f2142-149">List package references of a specific project:</span></span>

  ```dotnetcli
  dotnet list SentimentAnalysis.csproj package
  ```

- <span data-ttu-id="f2142-150">Ön sürüm sürümleri dahil olmak üzere daha yeni sürümlere sahip paket başvurularını listeleyin:</span><span class="sxs-lookup"><span data-stu-id="f2142-150">List package references that have newer versions available, including prerelease versions:</span></span>

  ```dotnetcli
  dotnet list package --outdated --include-prerelease
  ```

- <span data-ttu-id="f2142-151">Belirli bir hedef çerçeve için paket başvurularını listeleyin:</span><span class="sxs-lookup"><span data-stu-id="f2142-151">List package references for a specific target framework:</span></span>

  ```dotnetcli
  dotnet list package --framework netcoreapp3.0
  ```
