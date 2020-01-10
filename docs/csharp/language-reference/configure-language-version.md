---
title: C#dil sürümü oluşturma C# -kılavuz
description: C# Dil sürümünün projenize göre nasıl belirlendiği hakkında bilgi edinin ve bunu el ile ayarlayabileceğiniz farklı değerler.
ms.date: 07/10/2019
ms.openlocfilehash: 90624816a68de694cacd0017c6d3162f6a89431c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713870"
---
# <a name="c-language-versioning"></a><span data-ttu-id="26e01-103">C#dil sürümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="26e01-103">C# language versioning</span></span>

<span data-ttu-id="26e01-104">En son C# derleyici, projenizin hedef çerçevesine veya çerçevelerine göre varsayılan dil sürümünü belirler.</span><span class="sxs-lookup"><span data-stu-id="26e01-104">The latest C# compiler determines a default language version based on your project's target framework or frameworks.</span></span> <span data-ttu-id="26e01-105">Bunun nedeni, C# dilin her .NET uygulamasında kullanılamayan türleri veya çalışma zamanı bileşenlerini kullanan özelliklere sahip olması olabilir.</span><span class="sxs-lookup"><span data-stu-id="26e01-105">This is because the C# language may have features that rely on types or runtime components that are not available in every .NET implementation.</span></span> <span data-ttu-id="26e01-106">Bu Ayrıca, projenizin her türlü hedefi için varsayılan olarak en yüksek uyumlu dil sürümünü almanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="26e01-106">This also ensures that for whatever target your project is built against, you get the highest compatible language version by default.</span></span>

<span data-ttu-id="26e01-107">Bu makaledeki kurallar, Visual Studio 2019 veya .NET Core 3,0 SDK ile sunulan derleyici için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="26e01-107">The rules in this article apply to the compiler delivered with Visual Studio 2019, or the .NET Core 3.0 SDK.</span></span> <span data-ttu-id="26e01-108">Visual C# Studio 2017 yüklemesinin parçası olan derleyiciler veya daha önceki .NET Core SDK sürümleri, varsayılan olarak C# 7,0 ' dir.</span><span class="sxs-lookup"><span data-stu-id="26e01-108">The C# compilers that are part of the Visual Studio 2017 installation or earlier .NET Core SDK versions target C# 7.0 by default.</span></span> 

## <a name="defaults"></a><span data-ttu-id="26e01-109">Varsayılanları</span><span class="sxs-lookup"><span data-stu-id="26e01-109">Defaults</span></span>

<span data-ttu-id="26e01-110">Derleyici, bu kurallara göre bir varsayılan değer belirler:</span><span class="sxs-lookup"><span data-stu-id="26e01-110">The compiler determines a default based on these rules:</span></span>

|<span data-ttu-id="26e01-111">Hedef çerçeve</span><span class="sxs-lookup"><span data-stu-id="26e01-111">Target framework</span></span>|<span data-ttu-id="26e01-112">sürümü</span><span class="sxs-lookup"><span data-stu-id="26e01-112">version</span></span>|<span data-ttu-id="26e01-113">C#dil sürümü varsayılanı</span><span class="sxs-lookup"><span data-stu-id="26e01-113">C# language version default</span></span>|
|----------------|-------|---------------------------|
|<span data-ttu-id="26e01-114">.NET Core</span><span class="sxs-lookup"><span data-stu-id="26e01-114">.NET Core</span></span>|<span data-ttu-id="26e01-115">3.x</span><span class="sxs-lookup"><span data-stu-id="26e01-115">3.x</span></span>|<span data-ttu-id="26e01-116">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="26e01-116">C# 8.0</span></span>|
|<span data-ttu-id="26e01-117">.NET Core</span><span class="sxs-lookup"><span data-stu-id="26e01-117">.NET Core</span></span>|<span data-ttu-id="26e01-118">2.x</span><span class="sxs-lookup"><span data-stu-id="26e01-118">2.x</span></span>|<span data-ttu-id="26e01-119">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="26e01-119">C# 7.3</span></span>|
|<span data-ttu-id="26e01-120">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="26e01-120">.NET Standard</span></span>|<span data-ttu-id="26e01-121">2.1</span><span class="sxs-lookup"><span data-stu-id="26e01-121">2.1</span></span>|<span data-ttu-id="26e01-122">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="26e01-122">C# 8.0</span></span>|
|<span data-ttu-id="26e01-123">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="26e01-123">.NET Standard</span></span>|<span data-ttu-id="26e01-124">2,0</span><span class="sxs-lookup"><span data-stu-id="26e01-124">2.0</span></span>|<span data-ttu-id="26e01-125">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="26e01-125">C# 7.3</span></span>|
|<span data-ttu-id="26e01-126">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="26e01-126">.NET Standard</span></span>|<span data-ttu-id="26e01-127">'in</span><span class="sxs-lookup"><span data-stu-id="26e01-127">1.x</span></span>|<span data-ttu-id="26e01-128">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="26e01-128">C# 7.3</span></span>|
|<span data-ttu-id="26e01-129">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="26e01-129">.NET Framework</span></span>|<span data-ttu-id="26e01-130">tüm</span><span class="sxs-lookup"><span data-stu-id="26e01-130">all</span></span>|<span data-ttu-id="26e01-131">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="26e01-131">C# 7.3</span></span>|

## <a name="default-for-previews"></a><span data-ttu-id="26e01-132">Önizlemeler için varsayılan</span><span class="sxs-lookup"><span data-stu-id="26e01-132">Default for previews</span></span>

<span data-ttu-id="26e01-133">Projeniz karşılık gelen önizleme dili sürümüne sahip bir önizleme çerçevesini hedefliyorsa, kullanılan dil sürümü önizleme dili sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="26e01-133">When your project targets a preview framework that has a corresponding preview language version, the language version used is the preview language version.</span></span> <span data-ttu-id="26e01-134">Bu, yayımlanmış bir .NET Core sürümünü hedefleyen projelerinizi etkilemeden, herhangi bir ortamda bu önizleme ile çalışmak için garanti edilen en son özellikleri kullanmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="26e01-134">This ensures that you can use the latest features that are guaranteed to work with that preview in any environment without affecting your projects that target a released .NET Core version.</span></span>

## <a name="override-a-default"></a><span data-ttu-id="26e01-135">Varsayılanı geçersiz kıl</span><span class="sxs-lookup"><span data-stu-id="26e01-135">Override a default</span></span>

<span data-ttu-id="26e01-136">C# Sürümünüzü açıkça belirtmeniz gerekiyorsa, bunu birkaç şekilde yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="26e01-136">If you must specify your C# version explicitly, you can do so in several ways:</span></span>

- <span data-ttu-id="26e01-137">[Proje dosyanızı](#edit-the-project-file)el ile düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="26e01-137">Manually edit your [project file](#edit-the-project-file).</span></span>
- <span data-ttu-id="26e01-138">[Bir alt dizinde birden çok proje için](#configure-multiple-projects)dil sürümünü ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="26e01-138">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects).</span></span>
- <span data-ttu-id="26e01-139">[`-langversion` derleyici seçeneğini](compiler-options/langversion-compiler-option.md)yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="26e01-139">Configure the [`-langversion` compiler option](compiler-options/langversion-compiler-option.md).</span></span>

### <a name="edit-the-project-file"></a><span data-ttu-id="26e01-140">Proje dosyasını düzenleme</span><span class="sxs-lookup"><span data-stu-id="26e01-140">Edit the project file</span></span>

<span data-ttu-id="26e01-141">Proje dosyanızdaki dil sürümünü ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26e01-141">You can set the language version in your project file.</span></span> <span data-ttu-id="26e01-142">Örneğin, önizleme özelliklerine açıkça erişim istiyorsanız, şöyle bir öğe ekleyin:</span><span class="sxs-lookup"><span data-stu-id="26e01-142">For example, if you explicitly want access to preview features, add an element like this:</span></span>

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="26e01-143">Değer `preview`, derleyicinizin desteklediği en son C# önizleme dili sürümünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="26e01-143">The value `preview` uses the latest available preview C# language version that your compiler supports.</span></span>

### <a name="configure-multiple-projects"></a><span data-ttu-id="26e01-144">Birden çok proje yapılandırma</span><span class="sxs-lookup"><span data-stu-id="26e01-144">Configure multiple projects</span></span>

<span data-ttu-id="26e01-145">Birden çok dizini yapılandırmak için `<LangVersion>` öğesini içeren bir **Dizin. Build. props** dosyası oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26e01-145">You can create a **Directory.Build.props** file that contains the `<LangVersion>` element to configure multiple directories.</span></span> <span data-ttu-id="26e01-146">Bunu genellikle çözüm dizininizde yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26e01-146">You typically do that in your solution directory.</span></span> <span data-ttu-id="26e01-147">Aşağıdakileri çözüm dizininizde bir **Dizin. Build. props** dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="26e01-147">Add the following to a **Directory.Build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="26e01-148">Şimdi, bu dosyayı içeren dizinin her alt dizinindeki derlemeler Önizleme C# sürümünü kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="26e01-148">Now, builds in every subdirectory of the directory containing that file will use the preview C# version.</span></span> <span data-ttu-id="26e01-149">Daha fazla bilgi için, [yapınızı özelleştirme](/visualstudio/msbuild/customize-your-build)başlıklı makaleye bakın.</span><span class="sxs-lookup"><span data-stu-id="26e01-149">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="c-language-version-reference"></a><span data-ttu-id="26e01-150">C#dil sürümü başvurusu</span><span class="sxs-lookup"><span data-stu-id="26e01-150">C# language version reference</span></span>

<span data-ttu-id="26e01-151">Aşağıdaki tabloda tüm geçerli C# dil sürümleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="26e01-151">The following table shows all current C# language versions.</span></span> <span data-ttu-id="26e01-152">Daha eskiyse, derleyicisinin her değeri anlayamayabilir.</span><span class="sxs-lookup"><span data-stu-id="26e01-152">Your compiler may not necessarily understand every value if it is older.</span></span> <span data-ttu-id="26e01-153">.NET Core 3,0 ' i yüklerseniz, listelenen her şeye erişim sahibi olursunuz.</span><span class="sxs-lookup"><span data-stu-id="26e01-153">If you install .NET Core 3.0, then you will have access to everything listed.</span></span>

|<span data-ttu-id="26e01-154">Değer</span><span class="sxs-lookup"><span data-stu-id="26e01-154">Value</span></span>|<span data-ttu-id="26e01-155">Açıklama</span><span class="sxs-lookup"><span data-stu-id="26e01-155">Meaning</span></span>|
|------------|-------------|
|<span data-ttu-id="26e01-156">önizleme</span><span class="sxs-lookup"><span data-stu-id="26e01-156">preview</span></span>|<span data-ttu-id="26e01-157">Derleyici, en son önizleme sürümündeki tüm geçerli dil sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="26e01-157">The compiler accepts all valid language syntax from the latest preview version.</span></span>|
|<span data-ttu-id="26e01-158">latest</span><span class="sxs-lookup"><span data-stu-id="26e01-158">latest</span></span>|<span data-ttu-id="26e01-159">Derleyici derleyicinin en son yayınlanan sürümünden (ikincil sürüm dahil) söz dizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="26e01-159">The compiler accepts syntax from the latest released version of the compiler (including minor version).</span></span>|
|<span data-ttu-id="26e01-160">Latestana</span><span class="sxs-lookup"><span data-stu-id="26e01-160">latestMajor</span></span>|<span data-ttu-id="26e01-161">Derleyici derleyicinin en son yayınlanan ana sürümünden söz dizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="26e01-161">The compiler accepts syntax from the latest released major version of the compiler.</span></span>|
|<span data-ttu-id="26e01-162">8.0</span><span class="sxs-lookup"><span data-stu-id="26e01-162">8.0</span></span>|<span data-ttu-id="26e01-163">Derleyici yalnızca C# 8,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="26e01-163">The compiler accepts only syntax that is included in C# 8.0 or lower.</span></span>|
|<span data-ttu-id="26e01-164">7.3</span><span class="sxs-lookup"><span data-stu-id="26e01-164">7.3</span></span>|<span data-ttu-id="26e01-165">Derleyici yalnızca C# 7,3 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="26e01-165">The compiler accepts only syntax that is included in C# 7.3 or lower.</span></span>|
|<span data-ttu-id="26e01-166">7.2</span><span class="sxs-lookup"><span data-stu-id="26e01-166">7.2</span></span>|<span data-ttu-id="26e01-167">Derleyici yalnızca C# 7,2 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="26e01-167">The compiler accepts only syntax that is included in C# 7.2 or lower.</span></span>|
|<span data-ttu-id="26e01-168">7.1</span><span class="sxs-lookup"><span data-stu-id="26e01-168">7.1</span></span>|<span data-ttu-id="26e01-169">Derleyici yalnızca C# 7,1 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="26e01-169">The compiler accepts only syntax that is included in C# 7.1 or lower.</span></span>|
|<span data-ttu-id="26e01-170">7</span><span class="sxs-lookup"><span data-stu-id="26e01-170">7</span></span>|<span data-ttu-id="26e01-171">Derleyici yalnızca C# 7,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="26e01-171">The compiler accepts only syntax that is included in C# 7.0 or lower.</span></span>|
|<span data-ttu-id="26e01-172">6</span><span class="sxs-lookup"><span data-stu-id="26e01-172">6</span></span>|<span data-ttu-id="26e01-173">Derleyici yalnızca C# 6,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="26e01-173">The compiler accepts only syntax that is included in C# 6.0 or lower.</span></span>|
|<span data-ttu-id="26e01-174">5</span><span class="sxs-lookup"><span data-stu-id="26e01-174">5</span></span>|<span data-ttu-id="26e01-175">Derleyici yalnızca C# 5,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="26e01-175">The compiler accepts only syntax that is included in C# 5.0 or lower.</span></span>|
|<span data-ttu-id="26e01-176">4</span><span class="sxs-lookup"><span data-stu-id="26e01-176">4</span></span>|<span data-ttu-id="26e01-177">Derleyici yalnızca C# 4,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="26e01-177">The compiler accepts only syntax that is included in C# 4.0 or lower.</span></span>|
|<span data-ttu-id="26e01-178">3</span><span class="sxs-lookup"><span data-stu-id="26e01-178">3</span></span>|<span data-ttu-id="26e01-179">Derleyici yalnızca C# 3,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="26e01-179">The compiler accepts only syntax that is included in C# 3.0 or lower.</span></span>|
|<span data-ttu-id="26e01-180">ISO-2</span><span class="sxs-lookup"><span data-stu-id="26e01-180">ISO-2</span></span>|<span data-ttu-id="26e01-181">Derleyici yalnızca ISO/ıEC 23270:2006 C# (2,0) içinde bulunan söz dizimini kabul eder</span><span class="sxs-lookup"><span data-stu-id="26e01-181">The compiler accepts only syntax that is included in ISO/IEC 23270:2006 C# (2.0)</span></span> |
|<span data-ttu-id="26e01-182">ISO-1</span><span class="sxs-lookup"><span data-stu-id="26e01-182">ISO-1</span></span>|<span data-ttu-id="26e01-183">Derleyici yalnızca ISO/ıEC 23270:2003 C# (1.0/1.2) içinde bulunan söz dizimini kabul eder</span><span class="sxs-lookup"><span data-stu-id="26e01-183">The compiler accepts only syntax that is included in ISO/IEC 23270:2003 C# (1.0/1.2)</span></span> |
