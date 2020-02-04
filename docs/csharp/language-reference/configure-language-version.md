---
title: C#dil sürümü oluşturma C# -kılavuz
description: C# Dil sürümünün projenize göre nasıl belirlendiği hakkında bilgi edinin ve bunu el ile ayarlayabileceğiniz farklı değerler.
ms.date: 07/10/2019
ms.openlocfilehash: 3c1035d983660ea0a945e4d4b7b72c69736c90cb
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980138"
---
# <a name="c-language-versioning"></a><span data-ttu-id="a2528-103">C#dil sürümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="a2528-103">C# language versioning</span></span>

<span data-ttu-id="a2528-104">En son C# derleyici, projenizin hedef çerçevesine veya çerçevelerine göre varsayılan dil sürümünü belirler.</span><span class="sxs-lookup"><span data-stu-id="a2528-104">The latest C# compiler determines a default language version based on your project's target framework or frameworks.</span></span> <span data-ttu-id="a2528-105">Bunun nedeni, C# dilin her .NET uygulamasında kullanılamayan türleri veya çalışma zamanı bileşenlerini kullanan özelliklere sahip olması olabilir.</span><span class="sxs-lookup"><span data-stu-id="a2528-105">This is because the C# language may have features that rely on types or runtime components that are not available in every .NET implementation.</span></span> <span data-ttu-id="a2528-106">Bu Ayrıca, projenizin her türlü hedefi için varsayılan olarak en yüksek uyumlu dil sürümünü almanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2528-106">This also ensures that for whatever target your project is built against, you get the highest compatible language version by default.</span></span>

<span data-ttu-id="a2528-107">Bu makaledeki kurallar, Visual Studio 2019 veya .NET Core 3,0 SDK ile sunulan derleyici için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a2528-107">The rules in this article apply to the compiler delivered with Visual Studio 2019 or the .NET Core 3.0 SDK.</span></span> <span data-ttu-id="a2528-108">Visual C# Studio 2017 yüklemesinin parçası olan derleyiciler veya daha önceki .NET Core SDK sürümleri, varsayılan olarak C# 7,0 ' dir.</span><span class="sxs-lookup"><span data-stu-id="a2528-108">The C# compilers that are part of the Visual Studio 2017 installation or earlier .NET Core SDK versions target C# 7.0 by default.</span></span> 

## <a name="defaults"></a><span data-ttu-id="a2528-109">Varsayılanları</span><span class="sxs-lookup"><span data-stu-id="a2528-109">Defaults</span></span>

<span data-ttu-id="a2528-110">Derleyici, bu kurallara göre bir varsayılan değer belirler:</span><span class="sxs-lookup"><span data-stu-id="a2528-110">The compiler determines a default based on these rules:</span></span>

|<span data-ttu-id="a2528-111">Hedef çerçeve</span><span class="sxs-lookup"><span data-stu-id="a2528-111">Target framework</span></span>|<span data-ttu-id="a2528-112">sürümü</span><span class="sxs-lookup"><span data-stu-id="a2528-112">version</span></span>|<span data-ttu-id="a2528-113">C#dil sürümü varsayılanı</span><span class="sxs-lookup"><span data-stu-id="a2528-113">C# language version default</span></span>|
|----------------|-------|---------------------------|
|<span data-ttu-id="a2528-114">.NET Core</span><span class="sxs-lookup"><span data-stu-id="a2528-114">.NET Core</span></span>|<span data-ttu-id="a2528-115">3.x</span><span class="sxs-lookup"><span data-stu-id="a2528-115">3.x</span></span>|<span data-ttu-id="a2528-116">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="a2528-116">C# 8.0</span></span>|
|<span data-ttu-id="a2528-117">.NET Core</span><span class="sxs-lookup"><span data-stu-id="a2528-117">.NET Core</span></span>|<span data-ttu-id="a2528-118">2.x</span><span class="sxs-lookup"><span data-stu-id="a2528-118">2.x</span></span>|<span data-ttu-id="a2528-119">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="a2528-119">C# 7.3</span></span>|
|<span data-ttu-id="a2528-120">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="a2528-120">.NET Standard</span></span>|<span data-ttu-id="a2528-121">2.1</span><span class="sxs-lookup"><span data-stu-id="a2528-121">2.1</span></span>|<span data-ttu-id="a2528-122">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="a2528-122">C# 8.0</span></span>|
|<span data-ttu-id="a2528-123">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="a2528-123">.NET Standard</span></span>|<span data-ttu-id="a2528-124">2,0</span><span class="sxs-lookup"><span data-stu-id="a2528-124">2.0</span></span>|<span data-ttu-id="a2528-125">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="a2528-125">C# 7.3</span></span>|
|<span data-ttu-id="a2528-126">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="a2528-126">.NET Standard</span></span>|<span data-ttu-id="a2528-127">'in</span><span class="sxs-lookup"><span data-stu-id="a2528-127">1.x</span></span>|<span data-ttu-id="a2528-128">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="a2528-128">C# 7.3</span></span>|
|<span data-ttu-id="a2528-129">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="a2528-129">.NET Framework</span></span>|<span data-ttu-id="a2528-130">tüm</span><span class="sxs-lookup"><span data-stu-id="a2528-130">all</span></span>|<span data-ttu-id="a2528-131">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="a2528-131">C# 7.3</span></span>|

## <a name="default-for-previews"></a><span data-ttu-id="a2528-132">Önizlemeler için varsayılan</span><span class="sxs-lookup"><span data-stu-id="a2528-132">Default for previews</span></span>

<span data-ttu-id="a2528-133">Projeniz karşılık gelen önizleme dili sürümüne sahip bir önizleme çerçevesini hedefliyorsa, kullanılan dil sürümü önizleme dili sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="a2528-133">When your project targets a preview framework that has a corresponding preview language version, the language version used is the preview language version.</span></span> <span data-ttu-id="a2528-134">Bu, yayımlanmış bir .NET Core sürümünü hedefleyen projelerinizi etkilemeden, herhangi bir ortamda bu önizleme ile çalışmak için garanti edilen en son özellikleri kullanmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2528-134">This ensures that you can use the latest features that are guaranteed to work with that preview in any environment without affecting your projects that target a released .NET Core version.</span></span>

## <a name="override-a-default"></a><span data-ttu-id="a2528-135">Varsayılanı geçersiz kıl</span><span class="sxs-lookup"><span data-stu-id="a2528-135">Override a default</span></span>

<span data-ttu-id="a2528-136">C# Sürümünüzü açıkça belirtmeniz gerekiyorsa, bunu birkaç şekilde yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a2528-136">If you must specify your C# version explicitly, you can do so in several ways:</span></span>

- <span data-ttu-id="a2528-137">[Proje dosyanızı](#edit-the-project-file)el ile düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="a2528-137">Manually edit your [project file](#edit-the-project-file).</span></span>
- <span data-ttu-id="a2528-138">[Bir alt dizinde birden çok proje için](#configure-multiple-projects)dil sürümünü ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a2528-138">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects).</span></span>
- <span data-ttu-id="a2528-139">[`-langversion` derleyici seçeneğini](compiler-options/langversion-compiler-option.md)yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="a2528-139">Configure the [`-langversion` compiler option](compiler-options/langversion-compiler-option.md).</span></span>

### <a name="edit-the-project-file"></a><span data-ttu-id="a2528-140">Proje dosyasını düzenleme</span><span class="sxs-lookup"><span data-stu-id="a2528-140">Edit the project file</span></span>

<span data-ttu-id="a2528-141">Proje dosyanızdaki dil sürümünü ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2528-141">You can set the language version in your project file.</span></span> <span data-ttu-id="a2528-142">Örneğin, önizleme özelliklerine açıkça erişim istiyorsanız, şöyle bir öğe ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a2528-142">For example, if you explicitly want access to preview features, add an element like this:</span></span>

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="a2528-143">Değer `preview`, derleyicinizin desteklediği en son C# önizleme dili sürümünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="a2528-143">The value `preview` uses the latest available preview C# language version that your compiler supports.</span></span>

### <a name="configure-multiple-projects"></a><span data-ttu-id="a2528-144">Birden çok proje yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a2528-144">Configure multiple projects</span></span>

<span data-ttu-id="a2528-145">Birden çok projeyi yapılandırmak için, `<LangVersion>` öğesini içeren bir **Dizin. Build. props** dosyası oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2528-145">To configure multiple projects, you can create a **Directory.Build.props** file that contains the `<LangVersion>` element.</span></span> <span data-ttu-id="a2528-146">Bunu genellikle çözüm dizininizde yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2528-146">You typically do that in your solution directory.</span></span> <span data-ttu-id="a2528-147">Aşağıdakileri çözüm dizininizde bir **Dizin. Build. props** dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a2528-147">Add the following to a **Directory.Build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="a2528-148">Şimdi, bu dosyayı içeren dizinin her alt dizinindeki derlemeler Önizleme C# sürümünü kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="a2528-148">Now, builds in every subdirectory of the directory containing that file will use the preview C# version.</span></span> <span data-ttu-id="a2528-149">Daha fazla bilgi için, [yapınızı özelleştirme](/visualstudio/msbuild/customize-your-build)başlıklı makaleye bakın.</span><span class="sxs-lookup"><span data-stu-id="a2528-149">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="c-language-version-reference"></a><span data-ttu-id="a2528-150">C#dil sürümü başvurusu</span><span class="sxs-lookup"><span data-stu-id="a2528-150">C# language version reference</span></span>

<span data-ttu-id="a2528-151">Aşağıdaki tabloda tüm geçerli C# dil sürümleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a2528-151">The following table shows all current C# language versions.</span></span> <span data-ttu-id="a2528-152">Daha eskiyse, derleyicisinin her değeri anlayamayabilir.</span><span class="sxs-lookup"><span data-stu-id="a2528-152">Your compiler may not necessarily understand every value if it is older.</span></span> <span data-ttu-id="a2528-153">.NET Core 3,0 ' i yüklerseniz, listelenen her şeye erişim sahibi olursunuz.</span><span class="sxs-lookup"><span data-stu-id="a2528-153">If you install .NET Core 3.0, then you will have access to everything listed.</span></span>

|<span data-ttu-id="a2528-154">Değer</span><span class="sxs-lookup"><span data-stu-id="a2528-154">Value</span></span>|<span data-ttu-id="a2528-155">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a2528-155">Meaning</span></span>|
|------------|-------------|
|<span data-ttu-id="a2528-156">önizleme</span><span class="sxs-lookup"><span data-stu-id="a2528-156">preview</span></span>|<span data-ttu-id="a2528-157">Derleyici, en son önizleme sürümündeki tüm geçerli dil sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="a2528-157">The compiler accepts all valid language syntax from the latest preview version.</span></span>|
|<span data-ttu-id="a2528-158">latest</span><span class="sxs-lookup"><span data-stu-id="a2528-158">latest</span></span>|<span data-ttu-id="a2528-159">Derleyici derleyicinin en son yayınlanan sürümünden (ikincil sürüm dahil) söz dizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="a2528-159">The compiler accepts syntax from the latest released version of the compiler (including minor version).</span></span>|
|<span data-ttu-id="a2528-160">Latestana</span><span class="sxs-lookup"><span data-stu-id="a2528-160">latestMajor</span></span>|<span data-ttu-id="a2528-161">Derleyici derleyicinin en son yayınlanan ana sürümünden söz dizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="a2528-161">The compiler accepts syntax from the latest released major version of the compiler.</span></span>|
|<span data-ttu-id="a2528-162">8.0</span><span class="sxs-lookup"><span data-stu-id="a2528-162">8.0</span></span>|<span data-ttu-id="a2528-163">Derleyici yalnızca C# 8,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="a2528-163">The compiler accepts only syntax that is included in C# 8.0 or lower.</span></span>|
|<span data-ttu-id="a2528-164">7.3</span><span class="sxs-lookup"><span data-stu-id="a2528-164">7.3</span></span>|<span data-ttu-id="a2528-165">Derleyici yalnızca C# 7,3 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="a2528-165">The compiler accepts only syntax that is included in C# 7.3 or lower.</span></span>|
|<span data-ttu-id="a2528-166">7.2</span><span class="sxs-lookup"><span data-stu-id="a2528-166">7.2</span></span>|<span data-ttu-id="a2528-167">Derleyici yalnızca C# 7,2 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="a2528-167">The compiler accepts only syntax that is included in C# 7.2 or lower.</span></span>|
|<span data-ttu-id="a2528-168">7.1</span><span class="sxs-lookup"><span data-stu-id="a2528-168">7.1</span></span>|<span data-ttu-id="a2528-169">Derleyici yalnızca C# 7,1 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="a2528-169">The compiler accepts only syntax that is included in C# 7.1 or lower.</span></span>|
|<span data-ttu-id="a2528-170">7</span><span class="sxs-lookup"><span data-stu-id="a2528-170">7</span></span>|<span data-ttu-id="a2528-171">Derleyici yalnızca C# 7,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="a2528-171">The compiler accepts only syntax that is included in C# 7.0 or lower.</span></span>|
|<span data-ttu-id="a2528-172">6</span><span class="sxs-lookup"><span data-stu-id="a2528-172">6</span></span>|<span data-ttu-id="a2528-173">Derleyici yalnızca C# 6,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="a2528-173">The compiler accepts only syntax that is included in C# 6.0 or lower.</span></span>|
|<span data-ttu-id="a2528-174">5</span><span class="sxs-lookup"><span data-stu-id="a2528-174">5</span></span>|<span data-ttu-id="a2528-175">Derleyici yalnızca C# 5,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="a2528-175">The compiler accepts only syntax that is included in C# 5.0 or lower.</span></span>|
|<span data-ttu-id="a2528-176">4</span><span class="sxs-lookup"><span data-stu-id="a2528-176">4</span></span>|<span data-ttu-id="a2528-177">Derleyici yalnızca C# 4,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="a2528-177">The compiler accepts only syntax that is included in C# 4.0 or lower.</span></span>|
|<span data-ttu-id="a2528-178">3</span><span class="sxs-lookup"><span data-stu-id="a2528-178">3</span></span>|<span data-ttu-id="a2528-179">Derleyici yalnızca C# 3,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="a2528-179">The compiler accepts only syntax that is included in C# 3.0 or lower.</span></span>|
|<span data-ttu-id="a2528-180">ISO-2</span><span class="sxs-lookup"><span data-stu-id="a2528-180">ISO-2</span></span>|<span data-ttu-id="a2528-181">Derleyici yalnızca ISO/ıEC 23270:2006 C# (2,0) içinde bulunan söz dizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="a2528-181">The compiler accepts only syntax that is included in ISO/IEC 23270:2006 C# (2.0).</span></span> |
|<span data-ttu-id="a2528-182">ISO-1</span><span class="sxs-lookup"><span data-stu-id="a2528-182">ISO-1</span></span>|<span data-ttu-id="a2528-183">Derleyici yalnızca ISO/ıEC 23270:2003 C# (1.0/1.2) içinde bulunan söz dizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="a2528-183">The compiler accepts only syntax that is included in ISO/IEC 23270:2003 C# (1.0/1.2).</span></span> |
