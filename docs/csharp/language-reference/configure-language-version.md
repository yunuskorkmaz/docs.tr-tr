---
title: Seçin C# dil sürümü - C# Kılavuzu
description: Belirli bir derleyici sürümü kullanarak söz dizimi doğrulama gerçekleştirmek için derleyici yapılandırma
ms.date: 02/28/2019
ms.openlocfilehash: 6d31a757171bd2eecdcc1fbd3da765dcb3fe45c0
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57212033"
---
# <a name="select-the-c-language-version"></a><span data-ttu-id="649b6-103">Seçin C# dil sürümü</span><span class="sxs-lookup"><span data-stu-id="649b6-103">Select the C# language version</span></span>

<span data-ttu-id="649b6-104">C# Derleyici, proje hedef Framework'ü veya çerçeveleri göre varsayılan dil sürümü belirler.</span><span class="sxs-lookup"><span data-stu-id="649b6-104">The C# compiler determines a default language version based on your project's target framework or frameworks.</span></span> <span data-ttu-id="649b6-105">Projenize karşılık gelen bir önizleme dil sürümü olan bir önizleme framework hedeflediğinde, kullanılan dil sürümü Önizleme dil sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="649b6-105">When your project targets a preview framework that has a corresponding preview language version, the language version used is the preview language version.</span></span> <span data-ttu-id="649b6-106">Bir önizleme çerçeve proje hedeflemiyor, kullanılan dil son alt sürüm sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="649b6-106">When your project doesn't target a preview framework, the language version used is the latest minor version.</span></span>

<span data-ttu-id="649b6-107">Örneğin, .NET Core 3.0 Önizleme dönemi boyunca herhangi hedefleyen bir proje `netcoreapp3.0` veya `netstandard2.1` (hem de Önizleme) kullanacağı C# 8.0 Dil (Ayrıca önizlemede).</span><span class="sxs-lookup"><span data-stu-id="649b6-107">For example, during the preview period for .NET Core 3.0, any project that targets `netcoreapp3.0` or `netstandard2.1` (both in preview) will use the C# 8.0 language (also in preview).</span></span> <span data-ttu-id="649b6-108">Herhangi bir kullanıma sunulan sürümünü hedefleyen projelerin kullanacağı C# 7.3 (son yayımlanan sürümü).</span><span class="sxs-lookup"><span data-stu-id="649b6-108">Projects targeting any released version will use C# 7.3 (the latest released version).</span></span> <span data-ttu-id="649b6-109">Bu davranışı, .NET Framework'ü hedefleyen herhangi bir projenin son kullanacağı anlamına gelir (C# 7.3).</span><span class="sxs-lookup"><span data-stu-id="649b6-109">This behavior means that any project targeting .NET Framework will use latest (C# 7.3).</span></span> 

<span data-ttu-id="649b6-110">Bu özellik, bir projede yeni dil özellikleri eklemelerine kararı geliştirme ortamınızdan araçları ve SDK'sı yeni sürümlerini yüklemek için karar ayırır.</span><span class="sxs-lookup"><span data-stu-id="649b6-110">This capability decouples the decision to install new versions of the SDK and tools in your development environment from the decision to incorporate new language features in a project.</span></span> <span data-ttu-id="649b6-111">En son SDK'sı ve araçları, yapı makinesinde yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="649b6-111">You can install the latest SDK and tools on your build machine.</span></span> <span data-ttu-id="649b6-112">Her proje, derleme için belirli bir dil sürümünü kullanmak için yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="649b6-112">Each project can be configured to use a specific version of the language for its build.</span></span> <span data-ttu-id="649b6-113">Varsayılan davranış, yalnızca projeleri bu çerçeveleri hedeflediğinizde yeni türleri veya yeni bir CLR davranış dayalı tüm dil özelliklerinin etkin olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="649b6-113">The default behavior means that any language features that rely on new types or new CLR behavior are enabled only when projects target those frameworks.</span></span>

<span data-ttu-id="649b6-114">Bir dil sürümü belirterek varsayılan davranışı geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="649b6-114">You can override the default behavior by specifying a language version.</span></span> <span data-ttu-id="649b6-115">Dil sürümünü ayarlamak için birkaç yol vardır:</span><span class="sxs-lookup"><span data-stu-id="649b6-115">There are several ways to set the language version:</span></span>

- <span data-ttu-id="649b6-116">Dayanan bir [Visual Studio hızlı eylem](#visual-studio-quick-action).</span><span class="sxs-lookup"><span data-stu-id="649b6-116">Rely on a [Visual Studio quick action](#visual-studio-quick-action).</span></span>
- <span data-ttu-id="649b6-117">Dil sürümü ayarlama [Visual Studio UI](#set-the-language-version-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="649b6-117">Set the language version in the [Visual Studio UI](#set-the-language-version-in-visual-studio).</span></span>
- <span data-ttu-id="649b6-118">El ile düzenlemeniz, [ **.csproj** dosya](#edit-the-csproj-file).</span><span class="sxs-lookup"><span data-stu-id="649b6-118">Manually edit your [**.csproj** file](#edit-the-csproj-file).</span></span>
- <span data-ttu-id="649b6-119">Dil sürümünü ayarlama [bir alt dizinde birden çok proje için](#configure-multiple-projects).</span><span class="sxs-lookup"><span data-stu-id="649b6-119">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects).</span></span>
- <span data-ttu-id="649b6-120">Yapılandırma [ `-langversion` derleyici seçeneği](#set-the-langversion-compiler-option).</span><span class="sxs-lookup"><span data-stu-id="649b6-120">Configure the [`-langversion` compiler option](#set-the-langversion-compiler-option).</span></span>

## <a name="visual-studio-quick-action"></a><span data-ttu-id="649b6-121">Visual Studio hızlı eylem</span><span class="sxs-lookup"><span data-stu-id="649b6-121">Visual Studio quick action</span></span>

<span data-ttu-id="649b6-122">Visual Studio ihtiyacınız olan dil sürümü belirlemenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="649b6-122">Visual Studio helps you determine the language version you need.</span></span> <span data-ttu-id="649b6-123">Şu anda yapılandırılmış sürümü için kullanılabilir olmayan bir dil özelliğini kullanırsanız, Visual Studio projesi için dil sürümünü güncelleştirmek için bir olası düzeltme gösterir.</span><span class="sxs-lookup"><span data-stu-id="649b6-123">If you use a language feature that is not available for the currently configured version, Visual Studio shows a potential fix to update the language version for the project.</span></span>

## <a name="set-the-language-version-in-visual-studio"></a><span data-ttu-id="649b6-124">Visual Studio'da dil sürümünü ayarlama</span><span class="sxs-lookup"><span data-stu-id="649b6-124">Set the language version in Visual Studio</span></span>

<span data-ttu-id="649b6-125">Visual Studio'da sürüm ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="649b6-125">You can set the version in Visual Studio.</span></span> <span data-ttu-id="649b6-126">Çözüm Gezgini'nde proje düğümüne sağ tıklayıp **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="649b6-126">Right-click on the project node in Solution Explorer and select **Properties**.</span></span> <span data-ttu-id="649b6-127">Seçin **derleme** sekmenize **Gelişmiş** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="649b6-127">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="649b6-128">Açılır menüden sürümü seçin.</span><span class="sxs-lookup"><span data-stu-id="649b6-128">In the dropdown, select the version.</span></span> <span data-ttu-id="649b6-129">Aşağıdaki görüntüde "son" ayarı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="649b6-129">The following image shows the "latest" setting:</span></span>

![Dil sürümü belirleyebileceğiniz Gelişmiş derleme ayarları görüntüsü](./media/configure-language-version/advanced-build-settings.png)

> [!NOTE]
> <span data-ttu-id="649b6-131">Csproj dosyalarınızı güncelleştirmek için Visual Studio IDE kullanırsanız, IDE her derleme yapılandırması için ayrı bir düğüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="649b6-131">If you use the Visual Studio IDE to update your csproj files, the IDE creates separate nodes for each build configuration.</span></span> <span data-ttu-id="649b6-132">Genellikle aynı tüm derleme yapılandırmalarında ayarlamanız, ancak her derleme yapılandırması için açık olarak veya bu ayarı değiştirdiğinizde "Tüm yapılandırmaları" gerekir.</span><span class="sxs-lookup"><span data-stu-id="649b6-132">You'll typically set the value the same in all build configurations, but you need to set it explicitly for each build configuration, or select "All Configurations" when you modify this setting.</span></span> <span data-ttu-id="649b6-133">Csproj dosyanıza aşağıdaki görüntüyle karşılaşırsınız:</span><span class="sxs-lookup"><span data-stu-id="649b6-133">You'll see the following in your csproj file:</span></span>
>
>```xml
> <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|AnyCPU'">
>  <LangVersion>latest</LangVersion>
></PropertyGroup>
>
> <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|AnyCPU'">
>  <LangVersion>latest</LangVersion>
> </PropertyGroup>
> ```
>

## <a name="edit-the-csproj-file"></a><span data-ttu-id="649b6-134">Csproj dosyasını düzenleyin</span><span class="sxs-lookup"><span data-stu-id="649b6-134">Edit the csproj file</span></span>

<span data-ttu-id="649b6-135">Dil sürümü ayarlayabilirsiniz, **.csproj** dosya.</span><span class="sxs-lookup"><span data-stu-id="649b6-135">You can set the language version in your **.csproj** file.</span></span> <span data-ttu-id="649b6-136">Aşağıdaki gibi bir öğe ekleyin:</span><span class="sxs-lookup"><span data-stu-id="649b6-136">Add an element like the following:</span></span>

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="649b6-137">Değer `latest` en son sürümü kullanan C# dili.</span><span class="sxs-lookup"><span data-stu-id="649b6-137">The value `latest` uses the latest minor version of the C# language.</span></span> <span data-ttu-id="649b6-138">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="649b6-138">Valid values are:</span></span>

|<span data-ttu-id="649b6-139">Değer</span><span class="sxs-lookup"><span data-stu-id="649b6-139">Value</span></span>|<span data-ttu-id="649b6-140">Açıklama</span><span class="sxs-lookup"><span data-stu-id="649b6-140">Meaning</span></span>|
|------------|-------------|
|<span data-ttu-id="649b6-141">önizleme</span><span class="sxs-lookup"><span data-stu-id="649b6-141">preview</span></span>|<span data-ttu-id="649b6-142">Derleyici, en son Önizleme sürümünden tüm geçerli dili söz dizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="649b6-142">The compiler accepts all valid language syntax from the latest preview version.</span></span>|
|<span data-ttu-id="649b6-143">en son</span><span class="sxs-lookup"><span data-stu-id="649b6-143">latest</span></span>|<span data-ttu-id="649b6-144">Bir derleyici sürümünden en son yayımlanan (alt sürümü dahil) derleyici sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="649b6-144">The compiler accepts syntax from the latest released version of the compiler (including minor version).</span></span>|
|<span data-ttu-id="649b6-145">latestMajor</span><span class="sxs-lookup"><span data-stu-id="649b6-145">latestMajor</span></span>|<span data-ttu-id="649b6-146">Bir derleyici sürümünden en son yayımlanan önemli derleyici sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="649b6-146">The compiler accepts syntax from the latest released major version of the compiler.</span></span>|
|<span data-ttu-id="649b6-147">8.0</span><span class="sxs-lookup"><span data-stu-id="649b6-147">8.0</span></span>|<span data-ttu-id="649b6-148">Dahil edilen sözdizimi derleyici kabul C# 8.0 veya daha düşük.</span><span class="sxs-lookup"><span data-stu-id="649b6-148">The compiler accepts only syntax that is included in C# 8.0 or lower.</span></span>|
|<span data-ttu-id="649b6-149">7.3</span><span class="sxs-lookup"><span data-stu-id="649b6-149">7.3</span></span>|<span data-ttu-id="649b6-150">Dahil edilen sözdizimi derleyici kabul C# 7.3 ya da daha düşük.</span><span class="sxs-lookup"><span data-stu-id="649b6-150">The compiler accepts only syntax that is included in C# 7.3 or lower.</span></span>|
|<span data-ttu-id="649b6-151">7.2</span><span class="sxs-lookup"><span data-stu-id="649b6-151">7.2</span></span>|<span data-ttu-id="649b6-152">Dahil edilen sözdizimi derleyici kabul C# 7.2 veya daha düşük.</span><span class="sxs-lookup"><span data-stu-id="649b6-152">The compiler accepts only syntax that is included in C# 7.2 or lower.</span></span>|
|<span data-ttu-id="649b6-153">7.1</span><span class="sxs-lookup"><span data-stu-id="649b6-153">7.1</span></span>|<span data-ttu-id="649b6-154">Dahil edilen sözdizimi derleyici kabul C# 7.1 veya daha düşük.</span><span class="sxs-lookup"><span data-stu-id="649b6-154">The compiler accepts only syntax that is included in C# 7.1 or lower.</span></span>|
|<span data-ttu-id="649b6-155">7</span><span class="sxs-lookup"><span data-stu-id="649b6-155">7</span></span>|<span data-ttu-id="649b6-156">Dahil edilen sözdizimi derleyici kabul C# 7.0 ya da daha düşük.</span><span class="sxs-lookup"><span data-stu-id="649b6-156">The compiler accepts only syntax that is included in C# 7.0 or lower.</span></span>|
|<span data-ttu-id="649b6-157">6</span><span class="sxs-lookup"><span data-stu-id="649b6-157">6</span></span>|<span data-ttu-id="649b6-158">Dahil edilen sözdizimi derleyici kabul C# 6.0 veya daha düşük.</span><span class="sxs-lookup"><span data-stu-id="649b6-158">The compiler accepts only syntax that is included in C# 6.0 or lower.</span></span>|
|<span data-ttu-id="649b6-159">5</span><span class="sxs-lookup"><span data-stu-id="649b6-159">5</span></span>|<span data-ttu-id="649b6-160">Dahil edilen sözdizimi derleyici kabul C# 5.0 veya daha düşük.</span><span class="sxs-lookup"><span data-stu-id="649b6-160">The compiler accepts only syntax that is included in C# 5.0 or lower.</span></span>|
|<span data-ttu-id="649b6-161">4</span><span class="sxs-lookup"><span data-stu-id="649b6-161">4</span></span>|<span data-ttu-id="649b6-162">Dahil edilen sözdizimi derleyici kabul C# 4.0 veya daha düşük.</span><span class="sxs-lookup"><span data-stu-id="649b6-162">The compiler accepts only syntax that is included in C# 4.0 or lower.</span></span>|
|<span data-ttu-id="649b6-163">3</span><span class="sxs-lookup"><span data-stu-id="649b6-163">3</span></span>|<span data-ttu-id="649b6-164">Dahil edilen sözdizimi derleyici kabul C# 3.0 veya daha düşük.</span><span class="sxs-lookup"><span data-stu-id="649b6-164">The compiler accepts only syntax that is included in C# 3.0 or lower.</span></span>|
|<span data-ttu-id="649b6-165">ISO-2</span><span class="sxs-lookup"><span data-stu-id="649b6-165">ISO-2</span></span>|<span data-ttu-id="649b6-166">Derleyici ISO/IEC 23270:2006 dahil edilen sözdizimi kabul eden C# (2.0)</span><span class="sxs-lookup"><span data-stu-id="649b6-166">The compiler accepts only syntax that is included in ISO/IEC 23270:2006 C# (2.0)</span></span> |
|<span data-ttu-id="649b6-167">ISO-1</span><span class="sxs-lookup"><span data-stu-id="649b6-167">ISO-1</span></span>|<span data-ttu-id="649b6-168">Derleyici ISO/IEC 23270:2003 dahil edilen sözdizimi kabul eden C# (1.0/1.2)</span><span class="sxs-lookup"><span data-stu-id="649b6-168">The compiler accepts only syntax that is included in ISO/IEC 23270:2003 C# (1.0/1.2)</span></span> |

## <a name="configure-multiple-projects"></a><span data-ttu-id="649b6-169">Birden çok proje yapılandırma</span><span class="sxs-lookup"><span data-stu-id="649b6-169">Configure multiple projects</span></span>

<span data-ttu-id="649b6-170">Oluşturabileceğiniz bir **Directory.build.props** içeren dosya `<LangVersion>` birden çok dizini yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="649b6-170">You can create a **Directory.build.props** file that contains the `<LangVersion>` element to configure multiple directories.</span></span> <span data-ttu-id="649b6-171">Genellikle, çözüm dizininizde yaparsınız.</span><span class="sxs-lookup"><span data-stu-id="649b6-171">You typically do that in your solution directory.</span></span> <span data-ttu-id="649b6-172">Ekleyin bir **Directory.build.props** çözüm dizininizde dosya:</span><span class="sxs-lookup"><span data-stu-id="649b6-172">Add the following to a **Directory.build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>7.3</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="649b6-173">Artık, her alt bu dosyayı içeren dizine yapılarında kullanacak C# sürüm 7.3 söz dizimi.</span><span class="sxs-lookup"><span data-stu-id="649b6-173">Now, builds in every subdirectory of the directory containing that file will use C# version 7.3 syntax.</span></span> <span data-ttu-id="649b6-174">Daha fazla bilgi için makaleye bakın [derlemenizi özelleştirme](/visualstudio/msbuild/customize-your-build).</span><span class="sxs-lookup"><span data-stu-id="649b6-174">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="set-the-langversion-compiler-option"></a><span data-ttu-id="649b6-175">Langversion derleyici seçeneği ayarlama</span><span class="sxs-lookup"><span data-stu-id="649b6-175">Set the langversion compiler option</span></span>

<span data-ttu-id="649b6-176">Kullanabileceğiniz `-langversion` komut satırı seçeneği.</span><span class="sxs-lookup"><span data-stu-id="649b6-176">You can use the `-langversion` command-line option.</span></span> <span data-ttu-id="649b6-177">Daha fazla bilgi için makaleye bakın [- langversion](../language-reference/compiler-options/langversion-compiler-option.md) derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="649b6-177">For more information, see the article on the [-langversion](../language-reference/compiler-options/langversion-compiler-option.md) compiler option.</span></span> <span data-ttu-id="649b6-178">Yazarak geçerli değerlerin bir listesini görebilirsiniz `csc -langversion:?`.</span><span class="sxs-lookup"><span data-stu-id="649b6-178">You can see a list of the valid values by typing  `csc -langversion:?`.</span></span>
