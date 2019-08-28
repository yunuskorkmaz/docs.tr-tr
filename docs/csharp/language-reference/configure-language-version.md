---
title: C#dil sürümü oluşturma C# -kılavuz
description: C# Dil sürümünün projenize göre nasıl belirlendiği hakkında bilgi edinin ve bunu el ile ayarlayabileceğiniz farklı değerler.
ms.date: 07/10/2019
ms.openlocfilehash: fae36f5305e23fbfa1c55c5881e37391670f93ab
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040345"
---
# <a name="c-language-versioning"></a><span data-ttu-id="6f740-103">C#dil sürümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="6f740-103">C# language versioning</span></span>

<span data-ttu-id="6f740-104">En son C# derleyici, projenizin hedef çerçevesine veya çerçevelerine göre varsayılan dil sürümünü belirler.</span><span class="sxs-lookup"><span data-stu-id="6f740-104">The latest C# compiler determines a default language version based on your project's target framework or frameworks.</span></span> <span data-ttu-id="6f740-105">Bunun nedeni, C# dilin her .NET uygulamasında kullanılamayan türleri veya çalışma zamanı bileşenlerini kullanan özelliklere sahip olması olabilir.</span><span class="sxs-lookup"><span data-stu-id="6f740-105">This is because the C# language may have features that rely on types or runtime components that are not available in every .NET implementation.</span></span> <span data-ttu-id="6f740-106">Bu Ayrıca, projenizin her türlü hedefi için varsayılan olarak en yüksek uyumlu dil sürümünü almanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f740-106">This also ensures that for whatever target your project is built against, you get the highest compatible language version by default.</span></span>

<span data-ttu-id="6f740-107">Bu makaledeki kurallar, Visual Studio 2019 veya .NET Core 3,0 SDK ile sunulan derleyici için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6f740-107">The rules in this article apply to the compiler delivered with Visual Studio 2019, or the .NET Core 3.0 SDK.</span></span> <span data-ttu-id="6f740-108">Visual C# Studio 2017 yüklemesinin parçası olan derleyiciler veya daha önceki .NET Core SDK sürümleri, varsayılan olarak C# 7,0 ' dir.</span><span class="sxs-lookup"><span data-stu-id="6f740-108">The C# compilers that are part of the Visual Studio 2017 installation or earlier .NET Core SDK versions target C# 7.0 by default.</span></span> 

## <a name="defaults"></a><span data-ttu-id="6f740-109">Varsayılanları</span><span class="sxs-lookup"><span data-stu-id="6f740-109">Defaults</span></span>

<span data-ttu-id="6f740-110">Derleyici, bu kurallara göre bir varsayılan değer belirler:</span><span class="sxs-lookup"><span data-stu-id="6f740-110">The compiler determines a default based on these rules:</span></span>

|<span data-ttu-id="6f740-111">Hedef çerçeve</span><span class="sxs-lookup"><span data-stu-id="6f740-111">Target framework</span></span>|<span data-ttu-id="6f740-112">sürüm</span><span class="sxs-lookup"><span data-stu-id="6f740-112">version</span></span>|<span data-ttu-id="6f740-113">C#dil sürümü varsayılanı</span><span class="sxs-lookup"><span data-stu-id="6f740-113">C# language version default</span></span>|
|----------------|-------|---------------------------|
|<span data-ttu-id="6f740-114">.NET Core</span><span class="sxs-lookup"><span data-stu-id="6f740-114">.NET Core</span></span>|<span data-ttu-id="6f740-115">3.x</span><span class="sxs-lookup"><span data-stu-id="6f740-115">3.x</span></span>|<span data-ttu-id="6f740-116">C#8,0</span><span class="sxs-lookup"><span data-stu-id="6f740-116">C# 8.0</span></span>|
|<span data-ttu-id="6f740-117">.NET Core</span><span class="sxs-lookup"><span data-stu-id="6f740-117">.NET Core</span></span>|<span data-ttu-id="6f740-118">2.x</span><span class="sxs-lookup"><span data-stu-id="6f740-118">2.x</span></span>|<span data-ttu-id="6f740-119">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="6f740-119">C# 7.3</span></span>|
|<span data-ttu-id="6f740-120">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="6f740-120">.NET Standard</span></span>|<span data-ttu-id="6f740-121">tüm</span><span class="sxs-lookup"><span data-stu-id="6f740-121">all</span></span>|<span data-ttu-id="6f740-122">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="6f740-122">C# 7.3</span></span>|
|<span data-ttu-id="6f740-123">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="6f740-123">.NET Framework</span></span>|<span data-ttu-id="6f740-124">tüm</span><span class="sxs-lookup"><span data-stu-id="6f740-124">all</span></span>|<span data-ttu-id="6f740-125">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="6f740-125">C# 7.3</span></span>|

## <a name="default-for-previews"></a><span data-ttu-id="6f740-126">Önizlemeler için varsayılan</span><span class="sxs-lookup"><span data-stu-id="6f740-126">Default for previews</span></span>

<span data-ttu-id="6f740-127">Projeniz karşılık gelen önizleme dili sürümüne sahip bir önizleme çerçevesini hedefliyorsa, kullanılan dil sürümü önizleme dili sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="6f740-127">When your project targets a preview framework that has a corresponding preview language version, the language version used is the preview language version.</span></span> <span data-ttu-id="6f740-128">Bu, yayımlanmış bir .NET Core sürümünü hedefleyen projelerinizi etkilemeden, herhangi bir ortamda bu önizleme ile çalışmak için garanti edilen en son özellikleri kullanmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f740-128">This ensures that you can use the latest features that are guaranteed to work with that preview in any environment without affecting your projects that target a released .NET Core version.</span></span>

## <a name="override-a-default"></a><span data-ttu-id="6f740-129">Varsayılanı geçersiz kıl</span><span class="sxs-lookup"><span data-stu-id="6f740-129">Override a default</span></span>

<span data-ttu-id="6f740-130">C# Sürümünüzü açıkça belirtmeniz gerekiyorsa, bunu birkaç şekilde yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6f740-130">If you must specify your C# version explicitly, you can do so in several ways:</span></span>

- <span data-ttu-id="6f740-131">[Proje dosyanızı](#edit-the-project-file)el ile düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="6f740-131">Manually edit your [project file](#edit-the-project-file).</span></span>
- <span data-ttu-id="6f740-132">[Bir alt dizinde birden çok proje için](#configure-multiple-projects)dil sürümünü ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6f740-132">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects).</span></span>
- <span data-ttu-id="6f740-133">Derleyici seçeneğini [ `-langversion` yapılandırma](compiler-options/langversion-compiler-option.md)</span><span class="sxs-lookup"><span data-stu-id="6f740-133">Configure the [`-langversion` compiler option](compiler-options/langversion-compiler-option.md)</span></span>

### <a name="edit-the-project-file"></a><span data-ttu-id="6f740-134">Proje dosyasını düzenleme</span><span class="sxs-lookup"><span data-stu-id="6f740-134">Edit the project file</span></span>

<span data-ttu-id="6f740-135">Proje dosyanızdaki dil sürümünü ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f740-135">You can set the language version in your project file.</span></span> <span data-ttu-id="6f740-136">Örneğin, önizleme özelliklerine açıkça erişim istiyorsanız, şöyle bir öğe ekleyin:</span><span class="sxs-lookup"><span data-stu-id="6f740-136">For example, if you explicitly want access to preview features, add an element like this:</span></span>

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="6f740-137">Değer `preview` , derleyicinizin desteklediği en son C# önizleme dili sürümünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="6f740-137">The value `preview` uses the latest available preview C# language version that your compiler supports.</span></span>

### <a name="configure-multiple-projects"></a><span data-ttu-id="6f740-138">Birden çok proje yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6f740-138">Configure multiple projects</span></span>

<span data-ttu-id="6f740-139">Birden çok dizini yapılandırmak için `<LangVersion>` öğesini içeren bir **Dizin. Build. props** dosyası oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f740-139">You can create a **Directory.Build.props** file that contains the `<LangVersion>` element to configure multiple directories.</span></span> <span data-ttu-id="6f740-140">Bunu genellikle çözüm dizininizde yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f740-140">You typically do that in your solution directory.</span></span> <span data-ttu-id="6f740-141">Aşağıdakileri çözüm dizininizde bir **Dizin. Build. props** dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="6f740-141">Add the following to a **Directory.Build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="6f740-142">Şimdi, bu dosyayı içeren dizinin her alt dizinindeki derlemeler Önizleme C# sürümünü kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="6f740-142">Now, builds in every subdirectory of the directory containing that file will use the preview C# version.</span></span> <span data-ttu-id="6f740-143">Daha fazla bilgi için, [yapınızı özelleştirme](/visualstudio/msbuild/customize-your-build)başlıklı makaleye bakın.</span><span class="sxs-lookup"><span data-stu-id="6f740-143">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="c-language-version-reference"></a><span data-ttu-id="6f740-144">C#dil sürümü başvurusu</span><span class="sxs-lookup"><span data-stu-id="6f740-144">C# language version reference</span></span>

<span data-ttu-id="6f740-145">Aşağıdaki tabloda tüm geçerli C# dil sürümleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6f740-145">The following table shows all current C# language versions.</span></span> <span data-ttu-id="6f740-146">Daha eskiyse, derleyicisinin her değeri anlayamayabilir.</span><span class="sxs-lookup"><span data-stu-id="6f740-146">Your compiler may not necessarily understand every value if it is older.</span></span> <span data-ttu-id="6f740-147">.NET Core 3,0 ' i yüklerseniz, listelenen her şeye erişim sahibi olursunuz.</span><span class="sxs-lookup"><span data-stu-id="6f740-147">If you install .NET Core 3.0, then you will have access to everything listed.</span></span>

|<span data-ttu-id="6f740-148">Değer</span><span class="sxs-lookup"><span data-stu-id="6f740-148">Value</span></span>|<span data-ttu-id="6f740-149">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6f740-149">Meaning</span></span>|
|------------|-------------|
|<span data-ttu-id="6f740-150">önizleme</span><span class="sxs-lookup"><span data-stu-id="6f740-150">preview</span></span>|<span data-ttu-id="6f740-151">Derleyici, en son önizleme sürümündeki tüm geçerli dil sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="6f740-151">The compiler accepts all valid language syntax from the latest preview version.</span></span>|
|<span data-ttu-id="6f740-152">latest</span><span class="sxs-lookup"><span data-stu-id="6f740-152">latest</span></span>|<span data-ttu-id="6f740-153">Derleyici derleyicinin en son yayınlanan sürümünden (ikincil sürüm dahil) söz dizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="6f740-153">The compiler accepts syntax from the latest released version of the compiler (including minor version).</span></span>|
|<span data-ttu-id="6f740-154">Latestana</span><span class="sxs-lookup"><span data-stu-id="6f740-154">latestMajor</span></span>|<span data-ttu-id="6f740-155">Derleyici derleyicinin en son yayınlanan ana sürümünden söz dizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="6f740-155">The compiler accepts syntax from the latest released major version of the compiler.</span></span>|
|<span data-ttu-id="6f740-156">8.0</span><span class="sxs-lookup"><span data-stu-id="6f740-156">8.0</span></span>|<span data-ttu-id="6f740-157">Derleyici yalnızca C# 8,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="6f740-157">The compiler accepts only syntax that is included in C# 8.0 or lower.</span></span>|
|<span data-ttu-id="6f740-158">7.3</span><span class="sxs-lookup"><span data-stu-id="6f740-158">7.3</span></span>|<span data-ttu-id="6f740-159">Derleyici yalnızca C# 7,3 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="6f740-159">The compiler accepts only syntax that is included in C# 7.3 or lower.</span></span>|
|<span data-ttu-id="6f740-160">7.2</span><span class="sxs-lookup"><span data-stu-id="6f740-160">7.2</span></span>|<span data-ttu-id="6f740-161">Derleyici yalnızca C# 7,2 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="6f740-161">The compiler accepts only syntax that is included in C# 7.2 or lower.</span></span>|
|<span data-ttu-id="6f740-162">7.1</span><span class="sxs-lookup"><span data-stu-id="6f740-162">7.1</span></span>|<span data-ttu-id="6f740-163">Derleyici yalnızca C# 7,1 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="6f740-163">The compiler accepts only syntax that is included in C# 7.1 or lower.</span></span>|
|<span data-ttu-id="6f740-164">7</span><span class="sxs-lookup"><span data-stu-id="6f740-164">7</span></span>|<span data-ttu-id="6f740-165">Derleyici yalnızca C# 7,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="6f740-165">The compiler accepts only syntax that is included in C# 7.0 or lower.</span></span>|
|<span data-ttu-id="6f740-166">6</span><span class="sxs-lookup"><span data-stu-id="6f740-166">6</span></span>|<span data-ttu-id="6f740-167">Derleyici yalnızca C# 6,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="6f740-167">The compiler accepts only syntax that is included in C# 6.0 or lower.</span></span>|
|<span data-ttu-id="6f740-168">5</span><span class="sxs-lookup"><span data-stu-id="6f740-168">5</span></span>|<span data-ttu-id="6f740-169">Derleyici yalnızca C# 5,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="6f740-169">The compiler accepts only syntax that is included in C# 5.0 or lower.</span></span>|
|<span data-ttu-id="6f740-170">4</span><span class="sxs-lookup"><span data-stu-id="6f740-170">4</span></span>|<span data-ttu-id="6f740-171">Derleyici yalnızca C# 4,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="6f740-171">The compiler accepts only syntax that is included in C# 4.0 or lower.</span></span>|
|<span data-ttu-id="6f740-172">3</span><span class="sxs-lookup"><span data-stu-id="6f740-172">3</span></span>|<span data-ttu-id="6f740-173">Derleyici yalnızca C# 3,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="6f740-173">The compiler accepts only syntax that is included in C# 3.0 or lower.</span></span>|
|<span data-ttu-id="6f740-174">ISO-2</span><span class="sxs-lookup"><span data-stu-id="6f740-174">ISO-2</span></span>|<span data-ttu-id="6f740-175">Derleyici yalnızca ISO/ıEC 23270:2006 C# (2,0) içinde bulunan söz dizimini kabul eder</span><span class="sxs-lookup"><span data-stu-id="6f740-175">The compiler accepts only syntax that is included in ISO/IEC 23270:2006 C# (2.0)</span></span> |
|<span data-ttu-id="6f740-176">ISO-1</span><span class="sxs-lookup"><span data-stu-id="6f740-176">ISO-1</span></span>|<span data-ttu-id="6f740-177">Derleyici yalnızca ISO/ıEC 23270:2003 C# (1.0/1.2) içinde bulunan söz dizimini kabul eder</span><span class="sxs-lookup"><span data-stu-id="6f740-177">The compiler accepts only syntax that is included in ISO/IEC 23270:2003 C# (1.0/1.2)</span></span> |
