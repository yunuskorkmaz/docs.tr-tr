---
title: C#Dil sürümü oluşturma - C# Kılavuzu
description: Hakkında nasıl bilgi C# dil sürümü, projenizi temel alarak belirlenir ve farklı değerler, el ile şekilde ayarlayabilirsiniz.
ms.date: 07/10/2019
ms.openlocfilehash: e35fdf2bcdb1a31b752c760f3f6df59232e498a4
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68236090"
---
# <a name="c-language-versioning"></a><span data-ttu-id="d7985-103">C#Dil sürümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="d7985-103">C# language versioning</span></span>

<span data-ttu-id="d7985-104">C# Derleyici, proje hedef Framework'ü veya çerçeveleri göre varsayılan dil sürümü belirler.</span><span class="sxs-lookup"><span data-stu-id="d7985-104">The C# compiler determines a default language version based on your project's target framework or frameworks.</span></span> <span data-ttu-id="d7985-105">Bunun nedeni, C# dil türleri veya her bir .NET uygulamasında kullanılabilir olmayan bir çalışma zamanı bileşenlerini kullanan özellikler olabilir.</span><span class="sxs-lookup"><span data-stu-id="d7985-105">This is because the C# language may have features that rely on types or runtime components that are not available in every .NET implementation.</span></span> <span data-ttu-id="d7985-106">Bu ayrıca, projenizin karşı yerleşik her hedef için en yüksek uyumlu dil sürümünü varsayılan olarak almasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="d7985-106">This also ensures that for whatever target your project is built against, you get the highest compatible language version by default.</span></span>

## <a name="defaults"></a><span data-ttu-id="d7985-107">Varsayılanları</span><span class="sxs-lookup"><span data-stu-id="d7985-107">Defaults</span></span>

<span data-ttu-id="d7985-108">Derleyici, bu kurallara dayalı bir varsayılan belirler:</span><span class="sxs-lookup"><span data-stu-id="d7985-108">The compiler determines a default based on these rules:</span></span>

|<span data-ttu-id="d7985-109">Hedef Çerçeve</span><span class="sxs-lookup"><span data-stu-id="d7985-109">Target framework</span></span>|<span data-ttu-id="d7985-110">sürüm</span><span class="sxs-lookup"><span data-stu-id="d7985-110">version</span></span>|<span data-ttu-id="d7985-111">C#Dil sürümü varsayılan</span><span class="sxs-lookup"><span data-stu-id="d7985-111">C# language version default</span></span>|
|----------------|-------|---------------------------|
|<span data-ttu-id="d7985-112">.NET Core</span><span class="sxs-lookup"><span data-stu-id="d7985-112">.NET Core</span></span>|<span data-ttu-id="d7985-113">3.x</span><span class="sxs-lookup"><span data-stu-id="d7985-113">3.x</span></span>|<span data-ttu-id="d7985-114">C#8.0</span><span class="sxs-lookup"><span data-stu-id="d7985-114">C# 8.0</span></span>|
|<span data-ttu-id="d7985-115">.NET Core</span><span class="sxs-lookup"><span data-stu-id="d7985-115">.NET Core</span></span>|<span data-ttu-id="d7985-116">2.x</span><span class="sxs-lookup"><span data-stu-id="d7985-116">2.x</span></span>|<span data-ttu-id="d7985-117">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="d7985-117">C# 7.3</span></span>|
|<span data-ttu-id="d7985-118">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="d7985-118">.NET Standard</span></span>|<span data-ttu-id="d7985-119">tüm</span><span class="sxs-lookup"><span data-stu-id="d7985-119">all</span></span>|<span data-ttu-id="d7985-120">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="d7985-120">C# 7.3</span></span>|
|<span data-ttu-id="d7985-121">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="d7985-121">.NET Framework</span></span>|<span data-ttu-id="d7985-122">tüm</span><span class="sxs-lookup"><span data-stu-id="d7985-122">all</span></span>|<span data-ttu-id="d7985-123">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="d7985-123">C# 7.3</span></span>|

## <a name="default-for-previews"></a><span data-ttu-id="d7985-124">Preview sürümleri için varsayılan</span><span class="sxs-lookup"><span data-stu-id="d7985-124">Default for previews</span></span>

<span data-ttu-id="d7985-125">Projenize karşılık gelen bir önizleme dil sürümü olan bir önizleme framework hedeflediğinde, kullanılan dil sürümü Önizleme dil sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="d7985-125">When your project targets a preview framework that has a corresponding preview language version, the language version used is the preview language version.</span></span> <span data-ttu-id="d7985-126">Bu, her türlü ortamda bu Önizleme ile projelerinizi etkilemeden yayımlanmış bir .NET Core sürümünü hedefleyen çalışacağı garanti en son özellikleri kullanabileceğiniz sağlar.</span><span class="sxs-lookup"><span data-stu-id="d7985-126">This ensures that you can use the latest features that are guaranteed to work with that preview in any environment without affecting your projects that target a released .NET Core version.</span></span>

## <a name="overriding-a-default"></a><span data-ttu-id="d7985-127">Varsayılan bir geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="d7985-127">Overriding a default</span></span>

<span data-ttu-id="d7985-128">Belirtmeniz gerekiyorsa, C# sürüm açıkça çeşitli yollarla bunu yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d7985-128">If you must specify your C# version explicitly, you can do so in several ways:</span></span>

- <span data-ttu-id="d7985-129">El ile düzenlemeniz, [proje dosyası](#edit-the-project-file).</span><span class="sxs-lookup"><span data-stu-id="d7985-129">Manually edit your [project file](#edit-the-project-file).</span></span>
- <span data-ttu-id="d7985-130">Dil sürümünü ayarlama [bir alt dizinde birden çok proje için](#configure-multiple-projects).</span><span class="sxs-lookup"><span data-stu-id="d7985-130">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects).</span></span>
- <span data-ttu-id="d7985-131">Yapılandırma [ `-langversion` derleyici seçeneği](compiler-options/langversion-compiler-option.md)</span><span class="sxs-lookup"><span data-stu-id="d7985-131">Configure the [`-langversion` compiler option](compiler-options/langversion-compiler-option.md)</span></span>

### <a name="edit-the-project-file"></a><span data-ttu-id="d7985-132">Proje dosyası Düzenle</span><span class="sxs-lookup"><span data-stu-id="d7985-132">Edit the project file</span></span>

<span data-ttu-id="d7985-133">Dil sürümü, proje dosyasında ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d7985-133">You can set the language version in your project file.</span></span> <span data-ttu-id="d7985-134">Açıkça özelliklerin önizlemesini sağlamak erişim istediyseniz, örneğin, şunun gibi bir öğe ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d7985-134">For example, if you explicitly wanted access to preview features, you could do add an element like this:</span></span>

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="d7985-135">Değer `preview` kullanılabilir en son Önizleme kullanan C# derleyicinizin destekleyen dili.</span><span class="sxs-lookup"><span data-stu-id="d7985-135">The value `preview` uses the latest available preview C# language that your compiler supports.</span></span>

### <a name="configure-multiple-projects"></a><span data-ttu-id="d7985-136">Birden çok proje yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d7985-136">Configure multiple projects</span></span>

<span data-ttu-id="d7985-137">Oluşturabileceğiniz bir **Directory.Build.props** içeren dosya `<LangVersion>` birden çok dizini yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="d7985-137">You can create a **Directory.Build.props** file that contains the `<LangVersion>` element to configure multiple directories.</span></span> <span data-ttu-id="d7985-138">Genellikle, çözüm dizininizde yaparsınız.</span><span class="sxs-lookup"><span data-stu-id="d7985-138">You typically do that in your solution directory.</span></span> <span data-ttu-id="d7985-139">Ekleyin bir **Directory.Build.props** çözüm dizininizde dosya:</span><span class="sxs-lookup"><span data-stu-id="d7985-139">Add the following to a **Directory.Build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="d7985-140">Bu dosyayı içeren dizine her alt yapılarında Önizleme artık, kullanacak C# sürümü.</span><span class="sxs-lookup"><span data-stu-id="d7985-140">Now, builds in every subdirectory of the directory containing that file will use the preview C# version.</span></span> <span data-ttu-id="d7985-141">Daha fazla bilgi için makaleye bakın [derlemenizi özelleştirme](/visualstudio/msbuild/customize-your-build).</span><span class="sxs-lookup"><span data-stu-id="d7985-141">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="c-language-version-reference"></a><span data-ttu-id="d7985-142">C#Dil sürümü başvurusu</span><span class="sxs-lookup"><span data-stu-id="d7985-142">C# language version reference</span></span>

<span data-ttu-id="d7985-143">Aşağıdaki tablo geçerli tüm gösterir C# dil sürümleri.</span><span class="sxs-lookup"><span data-stu-id="d7985-143">The following table shows all current C# language versions.</span></span> <span data-ttu-id="d7985-144">Eski ise, derleyici her değer mutlaka anlamayabilir.</span><span class="sxs-lookup"><span data-stu-id="d7985-144">Your compiler may not necessarily understand every value if it is older.</span></span> <span data-ttu-id="d7985-145">.NET Core 3.0 yüklerseniz, listelenen her şeye erişimi gerekir.</span><span class="sxs-lookup"><span data-stu-id="d7985-145">If you install .NET Core 3.0, then you will have access to everything listed.</span></span>

|<span data-ttu-id="d7985-146">Değer</span><span class="sxs-lookup"><span data-stu-id="d7985-146">Value</span></span>|<span data-ttu-id="d7985-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d7985-147">Meaning</span></span>|
|------------|-------------|
|<span data-ttu-id="d7985-148">önizleme</span><span class="sxs-lookup"><span data-stu-id="d7985-148">preview</span></span>|<span data-ttu-id="d7985-149">Derleyici, en son Önizleme sürümünden tüm geçerli dili söz dizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="d7985-149">The compiler accepts all valid language syntax from the latest preview version.</span></span>|
|<span data-ttu-id="d7985-150">latest</span><span class="sxs-lookup"><span data-stu-id="d7985-150">latest</span></span>|<span data-ttu-id="d7985-151">Bir derleyici sürümünden en son yayımlanan (alt sürümü dahil) derleyici sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="d7985-151">The compiler accepts syntax from the latest released version of the compiler (including minor version).</span></span>|
|<span data-ttu-id="d7985-152">latestMajor</span><span class="sxs-lookup"><span data-stu-id="d7985-152">latestMajor</span></span>|<span data-ttu-id="d7985-153">Bir derleyici sürümünden en son yayımlanan önemli derleyici sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="d7985-153">The compiler accepts syntax from the latest released major version of the compiler.</span></span>|
|<span data-ttu-id="d7985-154">8.0</span><span class="sxs-lookup"><span data-stu-id="d7985-154">8.0</span></span>|<span data-ttu-id="d7985-155">Dahil edilen sözdizimi derleyici kabul C# 8.0 veya daha düşük.</span><span class="sxs-lookup"><span data-stu-id="d7985-155">The compiler accepts only syntax that is included in C# 8.0 or lower.</span></span>|
|<span data-ttu-id="d7985-156">7.3</span><span class="sxs-lookup"><span data-stu-id="d7985-156">7.3</span></span>|<span data-ttu-id="d7985-157">Dahil edilen sözdizimi derleyici kabul C# 7.3 ya da daha düşük.</span><span class="sxs-lookup"><span data-stu-id="d7985-157">The compiler accepts only syntax that is included in C# 7.3 or lower.</span></span>|
|<span data-ttu-id="d7985-158">7.2</span><span class="sxs-lookup"><span data-stu-id="d7985-158">7.2</span></span>|<span data-ttu-id="d7985-159">Dahil edilen sözdizimi derleyici kabul C# 7.2 veya daha düşük.</span><span class="sxs-lookup"><span data-stu-id="d7985-159">The compiler accepts only syntax that is included in C# 7.2 or lower.</span></span>|
|<span data-ttu-id="d7985-160">7.1</span><span class="sxs-lookup"><span data-stu-id="d7985-160">7.1</span></span>|<span data-ttu-id="d7985-161">Dahil edilen sözdizimi derleyici kabul C# 7.1 veya daha düşük.</span><span class="sxs-lookup"><span data-stu-id="d7985-161">The compiler accepts only syntax that is included in C# 7.1 or lower.</span></span>|
|<span data-ttu-id="d7985-162">7</span><span class="sxs-lookup"><span data-stu-id="d7985-162">7</span></span>|<span data-ttu-id="d7985-163">Dahil edilen sözdizimi derleyici kabul C# 7.0 ya da daha düşük.</span><span class="sxs-lookup"><span data-stu-id="d7985-163">The compiler accepts only syntax that is included in C# 7.0 or lower.</span></span>|
|<span data-ttu-id="d7985-164">6</span><span class="sxs-lookup"><span data-stu-id="d7985-164">6</span></span>|<span data-ttu-id="d7985-165">Dahil edilen sözdizimi derleyici kabul C# 6.0 veya daha düşük.</span><span class="sxs-lookup"><span data-stu-id="d7985-165">The compiler accepts only syntax that is included in C# 6.0 or lower.</span></span>|
|<span data-ttu-id="d7985-166">5</span><span class="sxs-lookup"><span data-stu-id="d7985-166">5</span></span>|<span data-ttu-id="d7985-167">Dahil edilen sözdizimi derleyici kabul C# 5.0 veya daha düşük.</span><span class="sxs-lookup"><span data-stu-id="d7985-167">The compiler accepts only syntax that is included in C# 5.0 or lower.</span></span>|
|<span data-ttu-id="d7985-168">4</span><span class="sxs-lookup"><span data-stu-id="d7985-168">4</span></span>|<span data-ttu-id="d7985-169">Dahil edilen sözdizimi derleyici kabul C# 4.0 veya daha düşük.</span><span class="sxs-lookup"><span data-stu-id="d7985-169">The compiler accepts only syntax that is included in C# 4.0 or lower.</span></span>|
|<span data-ttu-id="d7985-170">3</span><span class="sxs-lookup"><span data-stu-id="d7985-170">3</span></span>|<span data-ttu-id="d7985-171">Dahil edilen sözdizimi derleyici kabul C# 3.0 veya daha düşük.</span><span class="sxs-lookup"><span data-stu-id="d7985-171">The compiler accepts only syntax that is included in C# 3.0 or lower.</span></span>|
|<span data-ttu-id="d7985-172">ISO-2</span><span class="sxs-lookup"><span data-stu-id="d7985-172">ISO-2</span></span>|<span data-ttu-id="d7985-173">Derleyici ISO/IEC 23270:2006 dahil edilen sözdizimi kabul eden C# (2.0)</span><span class="sxs-lookup"><span data-stu-id="d7985-173">The compiler accepts only syntax that is included in ISO/IEC 23270:2006 C# (2.0)</span></span> |
|<span data-ttu-id="d7985-174">ISO-1</span><span class="sxs-lookup"><span data-stu-id="d7985-174">ISO-1</span></span>|<span data-ttu-id="d7985-175">Derleyici ISO/IEC 23270:2003 dahil edilen sözdizimi kabul eden C# (1.0/1.2)</span><span class="sxs-lookup"><span data-stu-id="d7985-175">The compiler accepts only syntax that is included in ISO/IEC 23270:2003 C# (1.0/1.2)</span></span> |
