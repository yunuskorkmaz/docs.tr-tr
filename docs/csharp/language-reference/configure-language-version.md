---
title: C#dil sürümü oluşturma C# -kılavuz
description: C# Dil sürümünün projenize göre nasıl belirlendiği hakkında bilgi edinin ve bunu el ile ayarlayabileceğiniz farklı değerler.
ms.date: 07/10/2019
ms.openlocfilehash: 744cec0aac21f743648cccbdc93cf2977c32d644
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796535"
---
# <a name="c-language-versioning"></a><span data-ttu-id="aba8e-103">C#dil sürümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="aba8e-103">C# language versioning</span></span>

<span data-ttu-id="aba8e-104">Derleyici C# , projenizin hedef çerçevesine veya çerçevelerine göre varsayılan dil sürümünü belirler.</span><span class="sxs-lookup"><span data-stu-id="aba8e-104">The C# compiler determines a default language version based on your project's target framework or frameworks.</span></span> <span data-ttu-id="aba8e-105">Bunun nedeni, C# dilin her .NET uygulamasında kullanılamayan türleri veya çalışma zamanı bileşenlerini kullanan özelliklere sahip olması olabilir.</span><span class="sxs-lookup"><span data-stu-id="aba8e-105">This is because the C# language may have features that rely on types or runtime components that are not available in every .NET implementation.</span></span> <span data-ttu-id="aba8e-106">Bu Ayrıca, projenizin her türlü hedefi için varsayılan olarak en yüksek uyumlu dil sürümünü almanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="aba8e-106">This also ensures that for whatever target your project is built against, you get the highest compatible language version by default.</span></span>

## <a name="defaults"></a><span data-ttu-id="aba8e-107">Varsayılanları</span><span class="sxs-lookup"><span data-stu-id="aba8e-107">Defaults</span></span>

<span data-ttu-id="aba8e-108">Derleyici, bu kurallara göre bir varsayılan değer belirler:</span><span class="sxs-lookup"><span data-stu-id="aba8e-108">The compiler determines a default based on these rules:</span></span>

|<span data-ttu-id="aba8e-109">Hedef çerçeve</span><span class="sxs-lookup"><span data-stu-id="aba8e-109">Target framework</span></span>|<span data-ttu-id="aba8e-110">sürüm</span><span class="sxs-lookup"><span data-stu-id="aba8e-110">version</span></span>|<span data-ttu-id="aba8e-111">C#dil sürümü varsayılanı</span><span class="sxs-lookup"><span data-stu-id="aba8e-111">C# language version default</span></span>|
|----------------|-------|---------------------------|
|<span data-ttu-id="aba8e-112">.NET Core</span><span class="sxs-lookup"><span data-stu-id="aba8e-112">.NET Core</span></span>|<span data-ttu-id="aba8e-113">3.x</span><span class="sxs-lookup"><span data-stu-id="aba8e-113">3.x</span></span>|<span data-ttu-id="aba8e-114">C#8,0</span><span class="sxs-lookup"><span data-stu-id="aba8e-114">C# 8.0</span></span>|
|<span data-ttu-id="aba8e-115">.NET Core</span><span class="sxs-lookup"><span data-stu-id="aba8e-115">.NET Core</span></span>|<span data-ttu-id="aba8e-116">2.x</span><span class="sxs-lookup"><span data-stu-id="aba8e-116">2.x</span></span>|<span data-ttu-id="aba8e-117">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="aba8e-117">C# 7.3</span></span>|
|<span data-ttu-id="aba8e-118">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="aba8e-118">.NET Standard</span></span>|<span data-ttu-id="aba8e-119">tüm</span><span class="sxs-lookup"><span data-stu-id="aba8e-119">all</span></span>|<span data-ttu-id="aba8e-120">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="aba8e-120">C# 7.3</span></span>|
|<span data-ttu-id="aba8e-121">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="aba8e-121">.NET Framework</span></span>|<span data-ttu-id="aba8e-122">tüm</span><span class="sxs-lookup"><span data-stu-id="aba8e-122">all</span></span>|<span data-ttu-id="aba8e-123">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="aba8e-123">C# 7.3</span></span>|

## <a name="default-for-previews"></a><span data-ttu-id="aba8e-124">Önizlemeler için varsayılan</span><span class="sxs-lookup"><span data-stu-id="aba8e-124">Default for previews</span></span>

<span data-ttu-id="aba8e-125">Projeniz karşılık gelen önizleme dili sürümüne sahip bir önizleme çerçevesini hedefliyorsa, kullanılan dil sürümü önizleme dili sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="aba8e-125">When your project targets a preview framework that has a corresponding preview language version, the language version used is the preview language version.</span></span> <span data-ttu-id="aba8e-126">Bu, yayımlanmış bir .NET Core sürümünü hedefleyen projelerinizi etkilemeden, herhangi bir ortamda bu önizleme ile çalışmak için garanti edilen en son özellikleri kullanmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="aba8e-126">This ensures that you can use the latest features that are guaranteed to work with that preview in any environment without affecting your projects that target a released .NET Core version.</span></span>

## <a name="override-a-default"></a><span data-ttu-id="aba8e-127">Varsayılanı geçersiz kıl</span><span class="sxs-lookup"><span data-stu-id="aba8e-127">Override a default</span></span>

<span data-ttu-id="aba8e-128">C# Sürümünüzü açıkça belirtmeniz gerekiyorsa, bunu birkaç şekilde yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="aba8e-128">If you must specify your C# version explicitly, you can do so in several ways:</span></span>

- <span data-ttu-id="aba8e-129">[Proje dosyanızı](#edit-the-project-file)el ile düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="aba8e-129">Manually edit your [project file](#edit-the-project-file).</span></span>
- <span data-ttu-id="aba8e-130">[Bir alt dizinde birden çok proje için](#configure-multiple-projects)dil sürümünü ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="aba8e-130">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects).</span></span>
- <span data-ttu-id="aba8e-131">Derleyici seçeneğini [ `-langversion` yapılandırma](compiler-options/langversion-compiler-option.md)</span><span class="sxs-lookup"><span data-stu-id="aba8e-131">Configure the [`-langversion` compiler option](compiler-options/langversion-compiler-option.md)</span></span>

### <a name="edit-the-project-file"></a><span data-ttu-id="aba8e-132">Proje dosyasını düzenleme</span><span class="sxs-lookup"><span data-stu-id="aba8e-132">Edit the project file</span></span>

<span data-ttu-id="aba8e-133">Proje dosyanızdaki dil sürümünü ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aba8e-133">You can set the language version in your project file.</span></span> <span data-ttu-id="aba8e-134">Örneğin, önizleme özelliklerine açıkça erişim istiyorsanız, şöyle bir öğe ekleyin:</span><span class="sxs-lookup"><span data-stu-id="aba8e-134">For example, if you explicitly want access to preview features, add an element like this:</span></span>

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="aba8e-135">Değer `preview` , derleyicinizin desteklediği en son C# önizleme dili sürümünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="aba8e-135">The value `preview` uses the latest available preview C# language version that your compiler supports.</span></span>

### <a name="configure-multiple-projects"></a><span data-ttu-id="aba8e-136">Birden çok proje yapılandırma</span><span class="sxs-lookup"><span data-stu-id="aba8e-136">Configure multiple projects</span></span>

<span data-ttu-id="aba8e-137">Birden çok dizini yapılandırmak için `<LangVersion>` öğesini içeren bir **Dizin. Build. props** dosyası oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aba8e-137">You can create a **Directory.Build.props** file that contains the `<LangVersion>` element to configure multiple directories.</span></span> <span data-ttu-id="aba8e-138">Bunu genellikle çözüm dizininizde yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aba8e-138">You typically do that in your solution directory.</span></span> <span data-ttu-id="aba8e-139">Aşağıdakileri çözüm dizininizde bir **Dizin. Build. props** dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="aba8e-139">Add the following to a **Directory.Build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="aba8e-140">Şimdi, bu dosyayı içeren dizinin her alt dizinindeki derlemeler Önizleme C# sürümünü kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="aba8e-140">Now, builds in every subdirectory of the directory containing that file will use the preview C# version.</span></span> <span data-ttu-id="aba8e-141">Daha fazla bilgi için, [yapınızı özelleştirme](/visualstudio/msbuild/customize-your-build)başlıklı makaleye bakın.</span><span class="sxs-lookup"><span data-stu-id="aba8e-141">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="c-language-version-reference"></a><span data-ttu-id="aba8e-142">C#dil sürümü başvurusu</span><span class="sxs-lookup"><span data-stu-id="aba8e-142">C# language version reference</span></span>

<span data-ttu-id="aba8e-143">Aşağıdaki tabloda tüm geçerli C# dil sürümleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="aba8e-143">The following table shows all current C# language versions.</span></span> <span data-ttu-id="aba8e-144">Daha eskiyse, derleyicisinin her değeri anlayamayabilir.</span><span class="sxs-lookup"><span data-stu-id="aba8e-144">Your compiler may not necessarily understand every value if it is older.</span></span> <span data-ttu-id="aba8e-145">.NET Core 3,0 ' i yüklerseniz, listelenen her şeye erişim sahibi olursunuz.</span><span class="sxs-lookup"><span data-stu-id="aba8e-145">If you install .NET Core 3.0, then you will have access to everything listed.</span></span>

|<span data-ttu-id="aba8e-146">Değer</span><span class="sxs-lookup"><span data-stu-id="aba8e-146">Value</span></span>|<span data-ttu-id="aba8e-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aba8e-147">Meaning</span></span>|
|------------|-------------|
|<span data-ttu-id="aba8e-148">önizleme</span><span class="sxs-lookup"><span data-stu-id="aba8e-148">preview</span></span>|<span data-ttu-id="aba8e-149">Derleyici, en son önizleme sürümündeki tüm geçerli dil sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="aba8e-149">The compiler accepts all valid language syntax from the latest preview version.</span></span>|
|<span data-ttu-id="aba8e-150">latest</span><span class="sxs-lookup"><span data-stu-id="aba8e-150">latest</span></span>|<span data-ttu-id="aba8e-151">Derleyici derleyicinin en son yayınlanan sürümünden (ikincil sürüm dahil) söz dizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="aba8e-151">The compiler accepts syntax from the latest released version of the compiler (including minor version).</span></span>|
|<span data-ttu-id="aba8e-152">Latestana</span><span class="sxs-lookup"><span data-stu-id="aba8e-152">latestMajor</span></span>|<span data-ttu-id="aba8e-153">Derleyici derleyicinin en son yayınlanan ana sürümünden söz dizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="aba8e-153">The compiler accepts syntax from the latest released major version of the compiler.</span></span>|
|<span data-ttu-id="aba8e-154">8.0</span><span class="sxs-lookup"><span data-stu-id="aba8e-154">8.0</span></span>|<span data-ttu-id="aba8e-155">Derleyici yalnızca C# 8,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="aba8e-155">The compiler accepts only syntax that is included in C# 8.0 or lower.</span></span>|
|<span data-ttu-id="aba8e-156">7.3</span><span class="sxs-lookup"><span data-stu-id="aba8e-156">7.3</span></span>|<span data-ttu-id="aba8e-157">Derleyici yalnızca C# 7,3 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="aba8e-157">The compiler accepts only syntax that is included in C# 7.3 or lower.</span></span>|
|<span data-ttu-id="aba8e-158">7.2</span><span class="sxs-lookup"><span data-stu-id="aba8e-158">7.2</span></span>|<span data-ttu-id="aba8e-159">Derleyici yalnızca C# 7,2 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="aba8e-159">The compiler accepts only syntax that is included in C# 7.2 or lower.</span></span>|
|<span data-ttu-id="aba8e-160">7.1</span><span class="sxs-lookup"><span data-stu-id="aba8e-160">7.1</span></span>|<span data-ttu-id="aba8e-161">Derleyici yalnızca C# 7,1 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="aba8e-161">The compiler accepts only syntax that is included in C# 7.1 or lower.</span></span>|
|<span data-ttu-id="aba8e-162">7</span><span class="sxs-lookup"><span data-stu-id="aba8e-162">7</span></span>|<span data-ttu-id="aba8e-163">Derleyici yalnızca C# 7,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="aba8e-163">The compiler accepts only syntax that is included in C# 7.0 or lower.</span></span>|
|<span data-ttu-id="aba8e-164">6</span><span class="sxs-lookup"><span data-stu-id="aba8e-164">6</span></span>|<span data-ttu-id="aba8e-165">Derleyici yalnızca C# 6,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="aba8e-165">The compiler accepts only syntax that is included in C# 6.0 or lower.</span></span>|
|<span data-ttu-id="aba8e-166">5</span><span class="sxs-lookup"><span data-stu-id="aba8e-166">5</span></span>|<span data-ttu-id="aba8e-167">Derleyici yalnızca C# 5,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="aba8e-167">The compiler accepts only syntax that is included in C# 5.0 or lower.</span></span>|
|<span data-ttu-id="aba8e-168">4</span><span class="sxs-lookup"><span data-stu-id="aba8e-168">4</span></span>|<span data-ttu-id="aba8e-169">Derleyici yalnızca C# 4,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="aba8e-169">The compiler accepts only syntax that is included in C# 4.0 or lower.</span></span>|
|<span data-ttu-id="aba8e-170">3</span><span class="sxs-lookup"><span data-stu-id="aba8e-170">3</span></span>|<span data-ttu-id="aba8e-171">Derleyici yalnızca C# 3,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="aba8e-171">The compiler accepts only syntax that is included in C# 3.0 or lower.</span></span>|
|<span data-ttu-id="aba8e-172">ISO-2</span><span class="sxs-lookup"><span data-stu-id="aba8e-172">ISO-2</span></span>|<span data-ttu-id="aba8e-173">Derleyici yalnızca ISO/ıEC 23270:2006 C# (2,0) içinde bulunan söz dizimini kabul eder</span><span class="sxs-lookup"><span data-stu-id="aba8e-173">The compiler accepts only syntax that is included in ISO/IEC 23270:2006 C# (2.0)</span></span> |
|<span data-ttu-id="aba8e-174">ISO-1</span><span class="sxs-lookup"><span data-stu-id="aba8e-174">ISO-1</span></span>|<span data-ttu-id="aba8e-175">Derleyici yalnızca ISO/ıEC 23270:2003 C# (1.0/1.2) içinde bulunan söz dizimini kabul eder</span><span class="sxs-lookup"><span data-stu-id="aba8e-175">The compiler accepts only syntax that is included in ISO/IEC 23270:2003 C# (1.0/1.2)</span></span> |
