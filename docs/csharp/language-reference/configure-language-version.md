---
title: C# dil sürümü oluşturma-C# Kılavuzu
description: C# dil sürümünün projenize göre nasıl belirlendiği ve bu seçimin arkasındaki nedenler hakkında bilgi edinin. Varsayılanı el ile nasıl geçersiz kılacağınızı öğrenin.
ms.custom: updateeachrelease
ms.date: 08/11/2020
ms.openlocfilehash: 327a98da37b97830ac7f752a3621a92d8cb161e0
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89495466"
---
# <a name="c-language-versioning"></a><span data-ttu-id="e240a-104">C# dil sürümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="e240a-104">C# language versioning</span></span>

<span data-ttu-id="e240a-105">En son C# derleyicisi, projenizin hedef çerçevesine veya çerçevelerine göre varsayılan dil sürümünü belirler.</span><span class="sxs-lookup"><span data-stu-id="e240a-105">The latest C# compiler determines a default language version based on your project's target framework or frameworks.</span></span> <span data-ttu-id="e240a-106">Visual Studio, değeri değiştirmek için bir kullanıcı arabirimi sağlamaz, ancak *csproj* dosyasını düzenleyerek bunu değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e240a-106">Visual Studio doesn't provide a UI to change the value, but you can change it by editing the *csproj* file.</span></span> <span data-ttu-id="e240a-107">Varsayılan seçenek, hedef çerçeveinizle uyumlu en son dil sürümünü kullanmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="e240a-107">The choice of default ensures that you use the latest language version compatible with your target framework.</span></span> <span data-ttu-id="e240a-108">Projenizin hedefi ile uyumlu olan en son dil özelliklerine erişim avantajına sahip olursunuz.</span><span class="sxs-lookup"><span data-stu-id="e240a-108">You benefit from access to the latest language features compatible with your project's target.</span></span> <span data-ttu-id="e240a-109">Bu varsayılan seçenek ayrıca, hedef çerçeveinizden kullanılabilir olmayan türler veya çalışma zamanı davranışı gerektiren bir dil kullanmanıza da sağlar.</span><span class="sxs-lookup"><span data-stu-id="e240a-109">This default choice also ensures you don't use a language that requires types or runtime behavior not available in your target framework.</span></span> <span data-ttu-id="e240a-110">Varsayılandan daha yeni bir dil sürümü seçmek, derleme zamanı ve çalışma zamanı hatalarının tanılanmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="e240a-110">Choosing a language version newer than the default can cause hard to diagnose compile-time and runtime errors.</span></span>

<span data-ttu-id="e240a-111">Bu makaledeki kurallar, Visual Studio 2019 veya .NET SDK ile sunulan derleyici için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e240a-111">The rules in this article apply to the compiler delivered with Visual Studio 2019 or the .NET SDK.</span></span> <span data-ttu-id="e240a-112">Visual Studio 2017 yüklemesinin veya önceki bir sürümünün parçası olan C# derleyicileri .NET Core SDK, varsayılan olarak c# 7,0 ' dir.</span><span class="sxs-lookup"><span data-stu-id="e240a-112">The C# compilers that are part of the Visual Studio 2017 installation or earlier .NET Core SDK versions target C# 7.0 by default.</span></span>

<span data-ttu-id="e240a-113">C# 8,0 yalnızca .NET Core 3. x ve daha yeni sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e240a-113">C# 8.0 is supported only on .NET Core 3.x and newer versions.</span></span> <span data-ttu-id="e240a-114">En yeni özelliklerin birçoğu .NET Core 3. x içinde tanıtılan kitaplık ve çalışma zamanı özellikleri gerektirir:</span><span class="sxs-lookup"><span data-stu-id="e240a-114">Many of the newest features require library and runtime features introduced in .NET Core 3.x:</span></span>

- <span data-ttu-id="e240a-115">[Varsayılan arabirim uygulamasına](../whats-new/csharp-8.md#default-interface-methods) .net Core 3,0 clr 'de yeni özellikler gerekir.</span><span class="sxs-lookup"><span data-stu-id="e240a-115">[Default interface implementation](../whats-new/csharp-8.md#default-interface-methods) requires new features in the .NET Core 3.0 CLR.</span></span>
- <span data-ttu-id="e240a-116">[Zaman uyumsuz akışlar](../whats-new/csharp-8.md#asynchronous-streams) , ve gibi yeni türler gerektirir <xref:System.IAsyncDisposable?displayProperty=nameWithType> <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType> <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e240a-116">[Async streams](../whats-new/csharp-8.md#asynchronous-streams) require the new types <xref:System.IAsyncDisposable?displayProperty=nameWithType>, <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType>, and <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType>.</span></span>
- <span data-ttu-id="e240a-117">[Dizinler ve aralıklar](../whats-new/csharp-8.md#indices-and-ranges) yeni türler ve gerektirir <xref:System.Index?displayProperty=nameWithType> <xref:System.Range?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e240a-117">[Indices and ranges](../whats-new/csharp-8.md#indices-and-ranges) require the new types <xref:System.Index?displayProperty=nameWithType> and <xref:System.Range?displayProperty=nameWithType>.</span></span>
- <span data-ttu-id="e240a-118">[Null yapılabilir başvuru türleri](../whats-new/csharp-8.md#nullable-reference-types) , daha iyi uyarılar sağlamak için birkaç [özniteliği](attributes/nullable-analysis.md) kullanır.</span><span class="sxs-lookup"><span data-stu-id="e240a-118">[Nullable reference types](../whats-new/csharp-8.md#nullable-reference-types) make use of several [attributes](attributes/nullable-analysis.md) to provide better warnings.</span></span> <span data-ttu-id="e240a-119">Bu öznitelikler .NET Core 3,0 ' ye eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="e240a-119">Those attributes were added in .NET Core 3.0.</span></span> <span data-ttu-id="e240a-120">Diğer hedef çerçeveler bu özniteliklerin hiçbirinde açıklanmamış.</span><span class="sxs-lookup"><span data-stu-id="e240a-120">Other target frameworks haven't been annotated with any of these attributes.</span></span> <span data-ttu-id="e240a-121">Bu, null yapılabilir uyarıların olası sorunları doğru şekilde yansıtmayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e240a-121">That means nullable warnings may not accurately reflect potential issues.</span></span>

<span data-ttu-id="e240a-122">C# 9,0 yalnızca .NET 5 ve daha yeni sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e240a-122">C# 9.0 is supported only on .NET 5 and newer versions.</span></span>

## <a name="defaults"></a><span data-ttu-id="e240a-123">Varsayılanları</span><span class="sxs-lookup"><span data-stu-id="e240a-123">Defaults</span></span>

<span data-ttu-id="e240a-124">Derleyici, bu kurallara göre bir varsayılan değer belirler:</span><span class="sxs-lookup"><span data-stu-id="e240a-124">The compiler determines a default based on these rules:</span></span>

| <span data-ttu-id="e240a-125">Hedef çerçeve</span><span class="sxs-lookup"><span data-stu-id="e240a-125">Target framework</span></span> | <span data-ttu-id="e240a-126">sürüm</span><span class="sxs-lookup"><span data-stu-id="e240a-126">version</span></span> | <span data-ttu-id="e240a-127">C# dil sürümü varsayılanı</span><span class="sxs-lookup"><span data-stu-id="e240a-127">C# language version default</span></span> |
|------------------|---------|-----------------------------|
| <span data-ttu-id="e240a-128">.NET</span><span class="sxs-lookup"><span data-stu-id="e240a-128">.NET</span></span>             | <span data-ttu-id="e240a-129">sürümünün</span><span class="sxs-lookup"><span data-stu-id="e240a-129">5.x</span></span>     | <span data-ttu-id="e240a-130">C# 9,0</span><span class="sxs-lookup"><span data-stu-id="e240a-130">C# 9.0</span></span>                      |
| <span data-ttu-id="e240a-131">.NET Core</span><span class="sxs-lookup"><span data-stu-id="e240a-131">.NET Core</span></span>        | <span data-ttu-id="e240a-132">3.x</span><span class="sxs-lookup"><span data-stu-id="e240a-132">3.x</span></span>     | <span data-ttu-id="e240a-133">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="e240a-133">C# 8.0</span></span>                      |
| <span data-ttu-id="e240a-134">.NET Core</span><span class="sxs-lookup"><span data-stu-id="e240a-134">.NET Core</span></span>        | <span data-ttu-id="e240a-135">2.x</span><span class="sxs-lookup"><span data-stu-id="e240a-135">2.x</span></span>     | <span data-ttu-id="e240a-136">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="e240a-136">C# 7.3</span></span>                      |
| <span data-ttu-id="e240a-137">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="e240a-137">.NET Standard</span></span>    | <span data-ttu-id="e240a-138">2.1</span><span class="sxs-lookup"><span data-stu-id="e240a-138">2.1</span></span>     | <span data-ttu-id="e240a-139">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="e240a-139">C# 8.0</span></span>                      |
| <span data-ttu-id="e240a-140">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="e240a-140">.NET Standard</span></span>    | <span data-ttu-id="e240a-141">2.0</span><span class="sxs-lookup"><span data-stu-id="e240a-141">2.0</span></span>     | <span data-ttu-id="e240a-142">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="e240a-142">C# 7.3</span></span>                      |
| <span data-ttu-id="e240a-143">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="e240a-143">.NET Standard</span></span>    | <span data-ttu-id="e240a-144">'in</span><span class="sxs-lookup"><span data-stu-id="e240a-144">1.x</span></span>     | <span data-ttu-id="e240a-145">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="e240a-145">C# 7.3</span></span>                      |
| <span data-ttu-id="e240a-146">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="e240a-146">.NET Framework</span></span>   | <span data-ttu-id="e240a-147">tümü</span><span class="sxs-lookup"><span data-stu-id="e240a-147">all</span></span>     | <span data-ttu-id="e240a-148">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="e240a-148">C# 7.3</span></span>                      |

<span data-ttu-id="e240a-149">Projeniz karşılık gelen önizleme dili sürümüne sahip bir önizleme çerçevesini hedefliyorsa, kullanılan dil sürümü önizleme dili sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="e240a-149">When your project targets a preview framework that has a corresponding preview language version, the language version used is the preview language version.</span></span> <span data-ttu-id="e240a-150">Yayınlanan bir .NET Core sürümünü hedefleyen projeleri etkilemeden, bu Önizlemedeki en son özellikleri herhangi bir ortamda kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="e240a-150">You use the latest features with that preview in any environment, without affecting projects that target a released .NET Core version.</span></span>

> [!TIP]
> <span data-ttu-id="e240a-151">Kullanmakta olduğunuz dil sürümünü görmek için `#error version` kodunuzda (büyük/küçük harfe duyarlı) koyun.</span><span class="sxs-lookup"><span data-stu-id="e240a-151">To know what language version you're currently using, put `#error version` (case sensitive) in your code.</span></span> <span data-ttu-id="e240a-152">Bu, derleyicinin, kullanılmakta olan derleyici sürümünü ve geçerli seçili dil sürümünü içeren bir ileti içeren bir tanılama, CS8304 oluşturmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e240a-152">This makes the compiler produce a diagnostic, CS8304, with a message containing the compiler version being used and the current selected language version.</span></span>

## <a name="override-a-default"></a><span data-ttu-id="e240a-153">Varsayılanı geçersiz kıl</span><span class="sxs-lookup"><span data-stu-id="e240a-153">Override a default</span></span>

<span data-ttu-id="e240a-154">C# sürümünüzü açık bir şekilde belirtmeniz gerekiyorsa, bunu birkaç şekilde yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e240a-154">If you must specify your C# version explicitly, you can do so in several ways:</span></span>

- <span data-ttu-id="e240a-155">[Proje dosyanızı](#edit-the-project-file)el ile düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="e240a-155">Manually edit your [project file](#edit-the-project-file).</span></span>
- <span data-ttu-id="e240a-156">[Bir alt dizinde birden çok proje için](#configure-multiple-projects)dil sürümünü ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e240a-156">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects).</span></span>
- <span data-ttu-id="e240a-157">[ `-langversion` Derleyici seçeneğini](compiler-options/langversion-compiler-option.md)yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="e240a-157">Configure the [`-langversion` compiler option](compiler-options/langversion-compiler-option.md).</span></span>

### <a name="edit-the-project-file"></a><span data-ttu-id="e240a-158">Proje dosyasını düzenleme</span><span class="sxs-lookup"><span data-stu-id="e240a-158">Edit the project file</span></span>

<span data-ttu-id="e240a-159">Proje dosyanızdaki dil sürümünü ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e240a-159">You can set the language version in your project file.</span></span> <span data-ttu-id="e240a-160">Örneğin, önizleme özelliklerine açıkça erişim istiyorsanız, şöyle bir öğe ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e240a-160">For example, if you explicitly want access to preview features, add an element like this:</span></span>

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="e240a-161">Bu değer, `preview` derleyicinizin desteklediği en son Preview C# dil sürümünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="e240a-161">The value `preview` uses the latest available preview C# language version that your compiler supports.</span></span>

### <a name="configure-multiple-projects"></a><span data-ttu-id="e240a-162">Birden çok proje yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e240a-162">Configure multiple projects</span></span>

<span data-ttu-id="e240a-163">Birden çok proje yapılandırmak için, öğesini içeren bir **Dizin. Build. props** dosyası oluşturabilirsiniz `<LangVersion>` .</span><span class="sxs-lookup"><span data-stu-id="e240a-163">To configure multiple projects, you can create a **Directory.Build.props** file that contains the `<LangVersion>` element.</span></span> <span data-ttu-id="e240a-164">Bunu genellikle çözüm dizininizde yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e240a-164">You typically do that in your solution directory.</span></span> <span data-ttu-id="e240a-165">Aşağıdakileri çözüm dizininizde bir **Dizin. Build. props** dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e240a-165">Add the following to a **Directory.Build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="e240a-166">Bu dosyayı içeren dizinin tüm alt dizinlerindeki derlemeler, Preview C# sürümünü kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="e240a-166">Builds in all subdirectories of the directory containing that file will use the preview C# version.</span></span> <span data-ttu-id="e240a-167">Daha fazla bilgi için, [yapınızı özelleştirme](/visualstudio/msbuild/customize-your-build)başlıklı makaleye bakın.</span><span class="sxs-lookup"><span data-stu-id="e240a-167">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="c-language-version-reference"></a><span data-ttu-id="e240a-168">C# dil sürümü başvurusu</span><span class="sxs-lookup"><span data-stu-id="e240a-168">C# language version reference</span></span>

<span data-ttu-id="e240a-169">Aşağıdaki tabloda tüm geçerli C# dil sürümleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e240a-169">The following table shows all current C# language versions.</span></span> <span data-ttu-id="e240a-170">Daha eski bir değer varsa, derleyicinizi her değeri anlayamayabilir.</span><span class="sxs-lookup"><span data-stu-id="e240a-170">Your compiler may not necessarily understand every value if it's older.</span></span> <span data-ttu-id="e240a-171">.NET Core 3,0 veya sonraki bir sürümünü yüklerseniz, listelenen her şeye erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e240a-171">If you install .NET Core 3.0 or later, then you have access to everything listed.</span></span>

[!INCLUDE [langversion-table](includes/langversion-table.md)]

> [!TIP]
> <span data-ttu-id="e240a-172">[Visual Studio için geliştirici komut istemi](../../framework/tools/developer-command-prompt-for-vs.md)açın ve makinenizde kullanılabilen dil sürümlerinin listesini görmek için aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e240a-172">Open the [Developer Command Prompt for Visual Studio](../../framework/tools/developer-command-prompt-for-vs.md), and run the following command to see the listing of language versions available on your machine.</span></span>
>
> ```CMD
> csc -langversion:?
> ```
>
> <span data-ttu-id="e240a-173">Bunun gibi [-langversion](compiler-options/langversion-compiler-option.md) derleme seçeneğini Sorga benzemekle, aşağıdakine benzer bir şey yazdıracaktır:</span><span class="sxs-lookup"><span data-stu-id="e240a-173">Questioning the [-langversion](compiler-options/langversion-compiler-option.md) compile option like this, will print something similar to the following:</span></span>
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
