---
title: C# dil sürümü oluşturma-C# Kılavuzu
description: C# dil sürümünün projenize göre nasıl belirlendiği ve bu seçimin arkasındaki nedenler hakkında bilgi edinin. Varsayılanı el ile nasıl geçersiz kılacağınızı öğrenin.
ms.date: 05/20/2020
ms.openlocfilehash: bbe5b12e378cf47b7c9b2c8576088e949e526a9a
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803003"
---
# <a name="c-language-versioning"></a><span data-ttu-id="fa63b-104">C# dil sürümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="fa63b-104">C# language versioning</span></span>

<span data-ttu-id="fa63b-105">En son C# derleyicisi, projenizin hedef çerçevesine veya çerçevelerine göre varsayılan dil sürümünü belirler.</span><span class="sxs-lookup"><span data-stu-id="fa63b-105">The latest C# compiler determines a default language version based on your project's target framework or frameworks.</span></span> <span data-ttu-id="fa63b-106">Visual Studio, değeri değiştirmek için bir kullanıcı arabirimi sağlamaz, ancak *csproj* dosyasını düzenleyerek bunu değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa63b-106">Visual Studio doesn't provide a UI to change the value, but you can change it by editing the *csproj* file.</span></span> <span data-ttu-id="fa63b-107">Varsayılan seçenek, hedef çerçeveinizle uyumlu en son dil sürümünü kullanmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="fa63b-107">The choice of default ensures that you use the latest language version compatible with your target framework.</span></span> <span data-ttu-id="fa63b-108">Projenizin hedefi ile uyumlu olan en son dil özelliklerine erişim avantajına sahip olursunuz.</span><span class="sxs-lookup"><span data-stu-id="fa63b-108">You benefit from access to the latest language features compatible with your project's target.</span></span> <span data-ttu-id="fa63b-109">Bu varsayılan seçenek ayrıca, hedef çerçeveinizden kullanılabilir olmayan türler veya çalışma zamanı davranışı gerektiren bir dil kullanmanıza da sağlar.</span><span class="sxs-lookup"><span data-stu-id="fa63b-109">This default choice also ensures you don't use a language that requires types or runtime behavior not available in your target framework.</span></span> <span data-ttu-id="fa63b-110">Varsayılandan daha yeni bir dil sürümü seçmek, derleme zamanı ve çalışma zamanı hatalarının tanılanmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="fa63b-110">Choosing a language version newer than the default can cause hard to diagnose compile-time and runtime errors.</span></span>

<span data-ttu-id="fa63b-111">Bu makaledeki kurallar, Visual Studio 2019 veya .NET Core 3,0 SDK ile sunulan derleyici için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="fa63b-111">The rules in this article apply to the compiler delivered with Visual Studio 2019 or the .NET Core 3.0 SDK.</span></span> <span data-ttu-id="fa63b-112">Visual Studio 2017 yüklemesinin veya önceki bir sürümünün parçası olan C# derleyicileri .NET Core SDK, varsayılan olarak c# 7,0 ' dir.</span><span class="sxs-lookup"><span data-stu-id="fa63b-112">The C# compilers that are part of the Visual Studio 2017 installation or earlier .NET Core SDK versions target C# 7.0 by default.</span></span>

<span data-ttu-id="fa63b-113">C# 8,0 (ve üzeri) yalnızca .NET Core 3. x ve daha yeni sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="fa63b-113">C# 8.0 (and higher) is supported only on .NET Core 3.x and newer versions.</span></span> <span data-ttu-id="fa63b-114">En yeni özelliklerin birçoğu .NET Core 3. x içinde tanıtılan kitaplık ve çalışma zamanı özellikleri gerektirir:</span><span class="sxs-lookup"><span data-stu-id="fa63b-114">Many of the newest features require library and runtime features introduced in .NET Core 3.x:</span></span>

- <span data-ttu-id="fa63b-115">[Varsayılan arabirim uygulamasına](../whats-new/csharp-8.md#default-interface-methods) .net Core 3,0 clr 'de yeni özellikler gerekir.</span><span class="sxs-lookup"><span data-stu-id="fa63b-115">[Default interface implementation](../whats-new/csharp-8.md#default-interface-methods) requires new features in the .NET Core 3.0 CLR.</span></span>
- <span data-ttu-id="fa63b-116">[Zaman uyumsuz akışlar](../whats-new/csharp-8.md#asynchronous-streams) , ve gibi yeni türler gerektirir <xref:System.IAsyncDisposable?displayProperty=nameWithType> <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType> <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fa63b-116">[Async streams](../whats-new/csharp-8.md#asynchronous-streams) require the new types <xref:System.IAsyncDisposable?displayProperty=nameWithType>, <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType>, and <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType>.</span></span>
- <span data-ttu-id="fa63b-117">[Dizinler ve aralıklar](../whats-new/csharp-8.md#indices-and-ranges) yeni türler ve gerektirir <xref:System.Index?displayProperty=nameWithType> <xref:System.Range?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fa63b-117">[Indices and ranges](../whats-new/csharp-8.md#indices-and-ranges) require the new types <xref:System.Index?displayProperty=nameWithType> and <xref:System.Range?displayProperty=nameWithType>.</span></span>
- <span data-ttu-id="fa63b-118">[Null yapılabilir başvuru türleri](../whats-new/csharp-8.md#nullable-reference-types) , daha iyi uyarılar sağlamak için birkaç [özniteliği](attributes/nullable-analysis.md) kullanır.</span><span class="sxs-lookup"><span data-stu-id="fa63b-118">[Nullable reference types](../whats-new/csharp-8.md#nullable-reference-types) make use of several [attributes](attributes/nullable-analysis.md) to provide better warnings.</span></span> <span data-ttu-id="fa63b-119">Bu öznitelikler .NET Core 3,0 ' ye eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="fa63b-119">Those attributes were added in .NET Core 3.0.</span></span> <span data-ttu-id="fa63b-120">Diğer hedef çerçeveler bu özniteliklerin hiçbirinde açıklanmamış.</span><span class="sxs-lookup"><span data-stu-id="fa63b-120">Other target frameworks haven't been annotated with any of these attributes.</span></span> <span data-ttu-id="fa63b-121">Bu, null yapılabilir uyarıların olası sorunları doğru şekilde yansıtmayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="fa63b-121">That means nullable warnings may not accurately reflect potential issues.</span></span>

## <a name="defaults"></a><span data-ttu-id="fa63b-122">Varsayılanları</span><span class="sxs-lookup"><span data-stu-id="fa63b-122">Defaults</span></span>

<span data-ttu-id="fa63b-123">Derleyici, bu kurallara göre bir varsayılan değer belirler:</span><span class="sxs-lookup"><span data-stu-id="fa63b-123">The compiler determines a default based on these rules:</span></span>

| <span data-ttu-id="fa63b-124">Hedef çerçeve</span><span class="sxs-lookup"><span data-stu-id="fa63b-124">Target framework</span></span> | <span data-ttu-id="fa63b-125">sürüm</span><span class="sxs-lookup"><span data-stu-id="fa63b-125">version</span></span> | <span data-ttu-id="fa63b-126">C# dil sürümü varsayılanı</span><span class="sxs-lookup"><span data-stu-id="fa63b-126">C# language version default</span></span> |
|------------------|---------|-----------------------------|
| <span data-ttu-id="fa63b-127">.NET Core</span><span class="sxs-lookup"><span data-stu-id="fa63b-127">.NET Core</span></span>        | <span data-ttu-id="fa63b-128">3.x</span><span class="sxs-lookup"><span data-stu-id="fa63b-128">3.x</span></span>     | <span data-ttu-id="fa63b-129">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="fa63b-129">C# 8.0</span></span>                      |
| <span data-ttu-id="fa63b-130">.NET Core</span><span class="sxs-lookup"><span data-stu-id="fa63b-130">.NET Core</span></span>        | <span data-ttu-id="fa63b-131">2.x</span><span class="sxs-lookup"><span data-stu-id="fa63b-131">2.x</span></span>     | <span data-ttu-id="fa63b-132">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="fa63b-132">C# 7.3</span></span>                      |
| <span data-ttu-id="fa63b-133">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="fa63b-133">.NET Standard</span></span>    | <span data-ttu-id="fa63b-134">2.1</span><span class="sxs-lookup"><span data-stu-id="fa63b-134">2.1</span></span>     | <span data-ttu-id="fa63b-135">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="fa63b-135">C# 8.0</span></span>                      |
| <span data-ttu-id="fa63b-136">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="fa63b-136">.NET Standard</span></span>    | <span data-ttu-id="fa63b-137">2.0</span><span class="sxs-lookup"><span data-stu-id="fa63b-137">2.0</span></span>     | <span data-ttu-id="fa63b-138">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="fa63b-138">C# 7.3</span></span>                      |
| <span data-ttu-id="fa63b-139">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="fa63b-139">.NET Standard</span></span>    | <span data-ttu-id="fa63b-140">'in</span><span class="sxs-lookup"><span data-stu-id="fa63b-140">1.x</span></span>     | <span data-ttu-id="fa63b-141">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="fa63b-141">C# 7.3</span></span>                      |
| <span data-ttu-id="fa63b-142">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="fa63b-142">.NET Framework</span></span>   | <span data-ttu-id="fa63b-143">tümü</span><span class="sxs-lookup"><span data-stu-id="fa63b-143">all</span></span>     | <span data-ttu-id="fa63b-144">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="fa63b-144">C# 7.3</span></span>                      |

<span data-ttu-id="fa63b-145">Projeniz karşılık gelen önizleme dili sürümüne sahip bir önizleme çerçevesini hedefliyorsa, kullanılan dil sürümü önizleme dili sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="fa63b-145">When your project targets a preview framework that has a corresponding preview language version, the language version used is the preview language version.</span></span> <span data-ttu-id="fa63b-146">Yayınlanan bir .NET Core sürümünü hedefleyen projeleri etkilemeden, bu Önizlemedeki en son özellikleri herhangi bir ortamda kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="fa63b-146">You use the latest features with that preview in any environment, without affecting projects that target a released .NET Core version.</span></span>

## <a name="override-a-default"></a><span data-ttu-id="fa63b-147">Varsayılanı geçersiz kıl</span><span class="sxs-lookup"><span data-stu-id="fa63b-147">Override a default</span></span>

<span data-ttu-id="fa63b-148">C# sürümünüzü açık bir şekilde belirtmeniz gerekiyorsa, bunu birkaç şekilde yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fa63b-148">If you must specify your C# version explicitly, you can do so in several ways:</span></span>

- <span data-ttu-id="fa63b-149">[Proje dosyanızı](#edit-the-project-file)el ile düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="fa63b-149">Manually edit your [project file](#edit-the-project-file).</span></span>
- <span data-ttu-id="fa63b-150">[Bir alt dizinde birden çok proje için](#configure-multiple-projects)dil sürümünü ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="fa63b-150">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects).</span></span>
- <span data-ttu-id="fa63b-151">[ `-langversion` Derleyici seçeneğini](compiler-options/langversion-compiler-option.md)yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="fa63b-151">Configure the [`-langversion` compiler option](compiler-options/langversion-compiler-option.md).</span></span>

### <a name="edit-the-project-file"></a><span data-ttu-id="fa63b-152">Proje dosyasını düzenleme</span><span class="sxs-lookup"><span data-stu-id="fa63b-152">Edit the project file</span></span>

<span data-ttu-id="fa63b-153">Proje dosyanızdaki dil sürümünü ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa63b-153">You can set the language version in your project file.</span></span> <span data-ttu-id="fa63b-154">Örneğin, önizleme özelliklerine açıkça erişim istiyorsanız, şöyle bir öğe ekleyin:</span><span class="sxs-lookup"><span data-stu-id="fa63b-154">For example, if you explicitly want access to preview features, add an element like this:</span></span>

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="fa63b-155">Bu değer, `preview` derleyicinizin desteklediği en son Preview C# dil sürümünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="fa63b-155">The value `preview` uses the latest available preview C# language version that your compiler supports.</span></span>

### <a name="configure-multiple-projects"></a><span data-ttu-id="fa63b-156">Birden çok proje yapılandırma</span><span class="sxs-lookup"><span data-stu-id="fa63b-156">Configure multiple projects</span></span>

<span data-ttu-id="fa63b-157">Birden çok proje yapılandırmak için, öğesini içeren bir **Dizin. Build. props** dosyası oluşturabilirsiniz `<LangVersion>` .</span><span class="sxs-lookup"><span data-stu-id="fa63b-157">To configure multiple projects, you can create a **Directory.Build.props** file that contains the `<LangVersion>` element.</span></span> <span data-ttu-id="fa63b-158">Bunu genellikle çözüm dizininizde yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa63b-158">You typically do that in your solution directory.</span></span> <span data-ttu-id="fa63b-159">Aşağıdakileri çözüm dizininizde bir **Dizin. Build. props** dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="fa63b-159">Add the following to a **Directory.Build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="fa63b-160">Bu dosyayı içeren dizinin tüm alt dizinlerindeki derlemeler, Preview C# sürümünü kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="fa63b-160">Builds in all subdirectories of the directory containing that file will use the preview C# version.</span></span> <span data-ttu-id="fa63b-161">Daha fazla bilgi için, [yapınızı özelleştirme](/visualstudio/msbuild/customize-your-build)başlıklı makaleye bakın.</span><span class="sxs-lookup"><span data-stu-id="fa63b-161">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="c-language-version-reference"></a><span data-ttu-id="fa63b-162">C# dil sürümü başvurusu</span><span class="sxs-lookup"><span data-stu-id="fa63b-162">C# language version reference</span></span>

<span data-ttu-id="fa63b-163">Aşağıdaki tabloda tüm geçerli C# dil sürümleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fa63b-163">The following table shows all current C# language versions.</span></span> <span data-ttu-id="fa63b-164">Daha eski bir değer varsa, derleyicinizi her değeri anlayamayabilir.</span><span class="sxs-lookup"><span data-stu-id="fa63b-164">Your compiler may not necessarily understand every value if it's older.</span></span> <span data-ttu-id="fa63b-165">.NET Core 3,0 veya sonraki bir sürümünü yüklerseniz, listelenen her şeye erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa63b-165">If you install .NET Core 3.0 or later, then you have access to everything listed.</span></span>

[!INCLUDE [langversion-table](includes/langversion-table.md)]

> [!TIP]
> <span data-ttu-id="fa63b-166">[Visual Studio için geliştirici komut istemi](../../framework/tools/developer-command-prompt-for-vs.md)açın ve makinenizde kullanılabilen dil sürümlerinin listesini görmek için aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="fa63b-166">Open the [Developer Command Prompt for Visual Studio](../../framework/tools/developer-command-prompt-for-vs.md), and run the following command to see the listing of language versions available on your machine.</span></span>
>
> ```CMD
> csc -langversion:?
> ```
>
> <span data-ttu-id="fa63b-167">Bunun gibi [-langversion](compiler-options/langversion-compiler-option.md) derleme seçeneğini Sorga benzemekle, aşağıdakine benzer bir şey yazdıracaktır:</span><span class="sxs-lookup"><span data-stu-id="fa63b-167">Questioning the [-langversion](compiler-options/langversion-compiler-option.md) compile option like this, will print something similar to the following:</span></span>
>
> ```CMD
> Supported language versions:
> default
> 1
> 2
> 3
> 4
> 5
> 6
> 7.0
> 7.1
> 7.2
> 7.3
> 8.0 (default)
> latestmajor
> preview
> latest
> ```
