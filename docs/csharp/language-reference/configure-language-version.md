---
title: C#dil sürümü oluşturma C# -kılavuz
description: C# Dil sürümünün projenize göre nasıl belirlendiği hakkında bilgi edinin ve bunu el ile ayarlayabileceğiniz farklı değerler.
ms.date: 07/10/2019
ms.openlocfilehash: aa4f16d91b38fec7f5d4cd0b2632e62552b64eb7
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698800"
---
# <a name="c-language-versioning"></a><span data-ttu-id="90428-103">C#dil sürümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="90428-103">C# language versioning</span></span>

<span data-ttu-id="90428-104">En son C# derleyici, projenizin hedef çerçevesine veya çerçevelerine göre varsayılan dil sürümünü belirler.</span><span class="sxs-lookup"><span data-stu-id="90428-104">The latest C# compiler determines a default language version based on your project's target framework or frameworks.</span></span> <span data-ttu-id="90428-105">Bunun nedeni, C# dilin her .NET uygulamasında kullanılamayan türleri veya çalışma zamanı bileşenlerini kullanan özelliklere sahip olması olabilir.</span><span class="sxs-lookup"><span data-stu-id="90428-105">This is because the C# language may have features that rely on types or runtime components that are not available in every .NET implementation.</span></span> <span data-ttu-id="90428-106">Bu Ayrıca, projenizin her türlü hedefi için varsayılan olarak en yüksek uyumlu dil sürümünü almanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="90428-106">This also ensures that for whatever target your project is built against, you get the highest compatible language version by default.</span></span>

<span data-ttu-id="90428-107">Bu makaledeki kurallar, Visual Studio 2019 veya .NET Core 3,0 SDK ile sunulan derleyici için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="90428-107">The rules in this article apply to the compiler delivered with Visual Studio 2019, or the .NET Core 3.0 SDK.</span></span> <span data-ttu-id="90428-108">Visual C# Studio 2017 yüklemesinin parçası olan derleyiciler veya daha önceki .NET Core SDK sürümleri, varsayılan olarak C# 7,0 ' dir.</span><span class="sxs-lookup"><span data-stu-id="90428-108">The C# compilers that are part of the Visual Studio 2017 installation or earlier .NET Core SDK versions target C# 7.0 by default.</span></span> 

## <a name="defaults"></a><span data-ttu-id="90428-109">Varsayılanları</span><span class="sxs-lookup"><span data-stu-id="90428-109">Defaults</span></span>

<span data-ttu-id="90428-110">Derleyici, bu kurallara göre bir varsayılan değer belirler:</span><span class="sxs-lookup"><span data-stu-id="90428-110">The compiler determines a default based on these rules:</span></span>

|<span data-ttu-id="90428-111">hedef çerçeve</span><span class="sxs-lookup"><span data-stu-id="90428-111">Target framework</span></span>|<span data-ttu-id="90428-112">sürüm</span><span class="sxs-lookup"><span data-stu-id="90428-112">version</span></span>|<span data-ttu-id="90428-113">C#dil sürümü varsayılanı</span><span class="sxs-lookup"><span data-stu-id="90428-113">C# language version default</span></span>|
|----------------|-------|---------------------------|
|<span data-ttu-id="90428-114">.NET Core</span><span class="sxs-lookup"><span data-stu-id="90428-114">.NET Core</span></span>|<span data-ttu-id="90428-115">3.x</span><span class="sxs-lookup"><span data-stu-id="90428-115">3.x</span></span>|<span data-ttu-id="90428-116">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="90428-116">C# 8.0</span></span>|
|<span data-ttu-id="90428-117">.NET Core</span><span class="sxs-lookup"><span data-stu-id="90428-117">.NET Core</span></span>|<span data-ttu-id="90428-118">2.x</span><span class="sxs-lookup"><span data-stu-id="90428-118">2.x</span></span>|<span data-ttu-id="90428-119">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="90428-119">C# 7.3</span></span>|
|<span data-ttu-id="90428-120">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="90428-120">.NET Standard</span></span>|<span data-ttu-id="90428-121">2,1</span><span class="sxs-lookup"><span data-stu-id="90428-121">2.1</span></span>|<span data-ttu-id="90428-122">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="90428-122">C# 8.0</span></span>|
|<span data-ttu-id="90428-123">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="90428-123">.NET Standard</span></span>|<span data-ttu-id="90428-124">2,0</span><span class="sxs-lookup"><span data-stu-id="90428-124">2.0</span></span>|<span data-ttu-id="90428-125">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="90428-125">C# 7.3</span></span>|
|<span data-ttu-id="90428-126">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="90428-126">.NET Standard</span></span>|<span data-ttu-id="90428-127">'in</span><span class="sxs-lookup"><span data-stu-id="90428-127">1.x</span></span>|<span data-ttu-id="90428-128">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="90428-128">C# 7.3</span></span>|
|<span data-ttu-id="90428-129">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="90428-129">.NET Framework</span></span>|<span data-ttu-id="90428-130">tüm</span><span class="sxs-lookup"><span data-stu-id="90428-130">all</span></span>|<span data-ttu-id="90428-131">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="90428-131">C# 7.3</span></span>|

## <a name="default-for-previews"></a><span data-ttu-id="90428-132">Önizlemeler için varsayılan</span><span class="sxs-lookup"><span data-stu-id="90428-132">Default for previews</span></span>

<span data-ttu-id="90428-133">Projeniz karşılık gelen önizleme dili sürümüne sahip bir önizleme çerçevesini hedefliyorsa, kullanılan dil sürümü önizleme dili sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="90428-133">When your project targets a preview framework that has a corresponding preview language version, the language version used is the preview language version.</span></span> <span data-ttu-id="90428-134">Bu, yayımlanmış bir .NET Core sürümünü hedefleyen projelerinizi etkilemeden, herhangi bir ortamda bu önizleme ile çalışmak için garanti edilen en son özellikleri kullanmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="90428-134">This ensures that you can use the latest features that are guaranteed to work with that preview in any environment without affecting your projects that target a released .NET Core version.</span></span>

## <a name="override-a-default"></a><span data-ttu-id="90428-135">Varsayılanı geçersiz kıl</span><span class="sxs-lookup"><span data-stu-id="90428-135">Override a default</span></span>

<span data-ttu-id="90428-136">C# Sürümünüzü açıkça belirtmeniz gerekiyorsa, bunu birkaç şekilde yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="90428-136">If you must specify your C# version explicitly, you can do so in several ways:</span></span>

- <span data-ttu-id="90428-137">[Proje dosyanızı](#edit-the-project-file)el ile düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="90428-137">Manually edit your [project file](#edit-the-project-file).</span></span>
- <span data-ttu-id="90428-138">[Bir alt dizinde birden çok proje için](#configure-multiple-projects)dil sürümünü ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="90428-138">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects).</span></span>
- <span data-ttu-id="90428-139">[@No__t-1 derleyici seçeneğini](compiler-options/langversion-compiler-option.md) yapılandırma</span><span class="sxs-lookup"><span data-stu-id="90428-139">Configure the [`-langversion` compiler option](compiler-options/langversion-compiler-option.md)</span></span>

### <a name="edit-the-project-file"></a><span data-ttu-id="90428-140">Proje dosyasını düzenleme</span><span class="sxs-lookup"><span data-stu-id="90428-140">Edit the project file</span></span>

<span data-ttu-id="90428-141">Proje dosyanızdaki dil sürümünü ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="90428-141">You can set the language version in your project file.</span></span> <span data-ttu-id="90428-142">Örneğin, önizleme özelliklerine açıkça erişim istiyorsanız, şöyle bir öğe ekleyin:</span><span class="sxs-lookup"><span data-stu-id="90428-142">For example, if you explicitly want access to preview features, add an element like this:</span></span>

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="90428-143">@No__t-0 değeri, derleyicinizin desteklediği en son C# önizleme dili sürümünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="90428-143">The value `preview` uses the latest available preview C# language version that your compiler supports.</span></span>

### <a name="configure-multiple-projects"></a><span data-ttu-id="90428-144">Birden çok proje yapılandırma</span><span class="sxs-lookup"><span data-stu-id="90428-144">Configure multiple projects</span></span>

<span data-ttu-id="90428-145">Birden çok dizini yapılandırmak için `<LangVersion>` öğesini içeren bir **Dizin. Build. props** dosyası oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="90428-145">You can create a **Directory.Build.props** file that contains the `<LangVersion>` element to configure multiple directories.</span></span> <span data-ttu-id="90428-146">Bunu genellikle çözüm dizininizde yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="90428-146">You typically do that in your solution directory.</span></span> <span data-ttu-id="90428-147">Aşağıdakileri çözüm dizininizde bir **Dizin. Build. props** dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="90428-147">Add the following to a **Directory.Build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="90428-148">Şimdi, bu dosyayı içeren dizinin her alt dizinindeki derlemeler Önizleme C# sürümünü kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="90428-148">Now, builds in every subdirectory of the directory containing that file will use the preview C# version.</span></span> <span data-ttu-id="90428-149">Daha fazla bilgi için, [yapınızı özelleştirme](/visualstudio/msbuild/customize-your-build)başlıklı makaleye bakın.</span><span class="sxs-lookup"><span data-stu-id="90428-149">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="c-language-version-reference"></a><span data-ttu-id="90428-150">C#dil sürümü başvurusu</span><span class="sxs-lookup"><span data-stu-id="90428-150">C# language version reference</span></span>

<span data-ttu-id="90428-151">Aşağıdaki tabloda tüm geçerli C# dil sürümleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="90428-151">The following table shows all current C# language versions.</span></span> <span data-ttu-id="90428-152">Daha eskiyse, derleyicisinin her değeri anlayamayabilir.</span><span class="sxs-lookup"><span data-stu-id="90428-152">Your compiler may not necessarily understand every value if it is older.</span></span> <span data-ttu-id="90428-153">.NET Core 3,0 ' i yüklerseniz, listelenen her şeye erişim sahibi olursunuz.</span><span class="sxs-lookup"><span data-stu-id="90428-153">If you install .NET Core 3.0, then you will have access to everything listed.</span></span>

|<span data-ttu-id="90428-154">Değer</span><span class="sxs-lookup"><span data-stu-id="90428-154">Value</span></span>|<span data-ttu-id="90428-155">Açıklama</span><span class="sxs-lookup"><span data-stu-id="90428-155">Meaning</span></span>|
|------------|-------------|
|<span data-ttu-id="90428-156">Önizleme</span><span class="sxs-lookup"><span data-stu-id="90428-156">preview</span></span>|<span data-ttu-id="90428-157">Derleyici, en son önizleme sürümündeki tüm geçerli dil sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="90428-157">The compiler accepts all valid language syntax from the latest preview version.</span></span>|
|<span data-ttu-id="90428-158">sürümü</span><span class="sxs-lookup"><span data-stu-id="90428-158">latest</span></span>|<span data-ttu-id="90428-159">Derleyici derleyicinin en son yayınlanan sürümünden (ikincil sürüm dahil) söz dizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="90428-159">The compiler accepts syntax from the latest released version of the compiler (including minor version).</span></span>|
|<span data-ttu-id="90428-160">Latestana</span><span class="sxs-lookup"><span data-stu-id="90428-160">latestMajor</span></span>|<span data-ttu-id="90428-161">Derleyici derleyicinin en son yayınlanan ana sürümünden söz dizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="90428-161">The compiler accepts syntax from the latest released major version of the compiler.</span></span>|
|<span data-ttu-id="90428-162">8.0</span><span class="sxs-lookup"><span data-stu-id="90428-162">8.0</span></span>|<span data-ttu-id="90428-163">Derleyici yalnızca C# 8,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="90428-163">The compiler accepts only syntax that is included in C# 8.0 or lower.</span></span>|
|<span data-ttu-id="90428-164">7,3</span><span class="sxs-lookup"><span data-stu-id="90428-164">7.3</span></span>|<span data-ttu-id="90428-165">Derleyici yalnızca C# 7,3 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="90428-165">The compiler accepts only syntax that is included in C# 7.3 or lower.</span></span>|
|<span data-ttu-id="90428-166">7,2</span><span class="sxs-lookup"><span data-stu-id="90428-166">7.2</span></span>|<span data-ttu-id="90428-167">Derleyici yalnızca C# 7,2 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="90428-167">The compiler accepts only syntax that is included in C# 7.2 or lower.</span></span>|
|<span data-ttu-id="90428-168">7,1</span><span class="sxs-lookup"><span data-stu-id="90428-168">7.1</span></span>|<span data-ttu-id="90428-169">Derleyici yalnızca C# 7,1 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="90428-169">The compiler accepts only syntax that is included in C# 7.1 or lower.</span></span>|
|<span data-ttu-id="90428-170">7</span><span class="sxs-lookup"><span data-stu-id="90428-170">7</span></span>|<span data-ttu-id="90428-171">Derleyici yalnızca C# 7,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="90428-171">The compiler accepts only syntax that is included in C# 7.0 or lower.</span></span>|
|<span data-ttu-id="90428-172">6</span><span class="sxs-lookup"><span data-stu-id="90428-172">6</span></span>|<span data-ttu-id="90428-173">Derleyici yalnızca C# 6,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="90428-173">The compiler accepts only syntax that is included in C# 6.0 or lower.</span></span>|
|<span data-ttu-id="90428-174">5</span><span class="sxs-lookup"><span data-stu-id="90428-174">5</span></span>|<span data-ttu-id="90428-175">Derleyici yalnızca C# 5,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="90428-175">The compiler accepts only syntax that is included in C# 5.0 or lower.</span></span>|
|<span data-ttu-id="90428-176">4</span><span class="sxs-lookup"><span data-stu-id="90428-176">4</span></span>|<span data-ttu-id="90428-177">Derleyici yalnızca C# 4,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="90428-177">The compiler accepts only syntax that is included in C# 4.0 or lower.</span></span>|
|<span data-ttu-id="90428-178">3</span><span class="sxs-lookup"><span data-stu-id="90428-178">3</span></span>|<span data-ttu-id="90428-179">Derleyici yalnızca C# 3,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="90428-179">The compiler accepts only syntax that is included in C# 3.0 or lower.</span></span>|
|<span data-ttu-id="90428-180">ISO-2</span><span class="sxs-lookup"><span data-stu-id="90428-180">ISO-2</span></span>|<span data-ttu-id="90428-181">Derleyici yalnızca ISO/ıEC 23270:2006 C# (2,0) içinde bulunan söz dizimini kabul eder</span><span class="sxs-lookup"><span data-stu-id="90428-181">The compiler accepts only syntax that is included in ISO/IEC 23270:2006 C# (2.0)</span></span> |
|<span data-ttu-id="90428-182">ISO-1</span><span class="sxs-lookup"><span data-stu-id="90428-182">ISO-1</span></span>|<span data-ttu-id="90428-183">Derleyici yalnızca ISO/ıEC 23270:2003 C# (1.0/1.2) içinde bulunan söz dizimini kabul eder</span><span class="sxs-lookup"><span data-stu-id="90428-183">The compiler accepts only syntax that is included in ISO/IEC 23270:2003 C# (1.0/1.2)</span></span> |
