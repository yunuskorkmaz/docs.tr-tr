---
title: C# dil sürümünü - C# Kılavuzu seçin
description: Belirli derleyici sürümü kullanılarak sözdizimi doğrulama gerçekleştirmek için derleyici yapılandırma
ms.date: 05/24/2018
ms.openlocfilehash: 9b91e62168ced0f373e1a55def8b279dc64833d8
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208415"
---
# <a name="select-the-c-language-version"></a><span data-ttu-id="9a22a-103">C# dil sürümünü seçin</span><span class="sxs-lookup"><span data-stu-id="9a22a-103">Select the C# language version</span></span>

<span data-ttu-id="9a22a-104">C# Derleyici yayımlandı dil ana en son sürümü varsayılan olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="9a22a-104">The C# compiler defaults to the latest major version of the language that has been released.</span></span> <span data-ttu-id="9a22a-105">Yeni noktası bir dil sürümünü kullanarak Projeyi derlemek tercih edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a22a-105">You may choose to compile any project using a new point release of the language.</span></span> <span data-ttu-id="9a22a-106">Dili, yeni bir sürümünü seçerek sağlar yapmak projenizin en son dil özelliklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9a22a-106">Choosing a newer version of the language enables your project to make use of the latest language features.</span></span> <span data-ttu-id="9a22a-107">Diğer senaryolarda bir proje dili daha eski bir sürümünü kullanırken düzgün bir şekilde derler doğrulamanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="9a22a-107">In other scenarios, you may need to validate that a project compiles cleanly when using an older version of the language.</span></span>

<span data-ttu-id="9a22a-108">Bu özelliği geliştirme ortamınızı bir projede yeni dil özellikleri içerecek şekilde karar den yeni sürümlerini SDK'yı ve araçları yüklemek için karar ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="9a22a-108">This capability decouples the decision to install new versions of the SDK and tools in your development environment from the decision to incorporate new language features in a project.</span></span> <span data-ttu-id="9a22a-109">En son SDK'yı ve araçları, yapı makinenizde yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a22a-109">You can install the latest SDK and tools on your build machine.</span></span> <span data-ttu-id="9a22a-110">Her proje, derleme için belirli bir dil sürümünü kullanacak şekilde yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="9a22a-110">Each project can be configured to use a specific version of the language for its build.</span></span>

<span data-ttu-id="9a22a-111">Dil sürümünü ayarlamak için birkaç yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="9a22a-111">There are several ways to set the language version:</span></span>

- <span data-ttu-id="9a22a-112">Bağlı bir [Visual Studio hızlı eylem](#visual-studio-quick-action).</span><span class="sxs-lookup"><span data-stu-id="9a22a-112">Rely on a [Visual Studio quick action](#visual-studio-quick-action).</span></span>
- <span data-ttu-id="9a22a-113">Dil sürümü kümesinde [Visual Studio kullanıcı Arabirimi](#set-the-language-version-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="9a22a-113">Set the language version in the [Visual Studio UI](#set-the-language-version-in-visual-studio).</span></span>
- <span data-ttu-id="9a22a-114">El ile düzenleme, [ **.csproj** dosya](#edit-the-csproj-file).</span><span class="sxs-lookup"><span data-stu-id="9a22a-114">Manually edit your [**.csproj** file](#edit-the-csproj-file).</span></span>
- <span data-ttu-id="9a22a-115">Dil sürümü [alt dizindeki birden çok proje için](#configure-multiple-projects).</span><span class="sxs-lookup"><span data-stu-id="9a22a-115">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects).</span></span>
- <span data-ttu-id="9a22a-116">Yapılandırma [ `-langversion` derleyici seçeneği](#set-the-langversion-compiler-option).</span><span class="sxs-lookup"><span data-stu-id="9a22a-116">Configure the [`-langversion` compiler option](#set-the-langversion-compiler-option).</span></span>

## <a name="visual-studio-quick-action"></a><span data-ttu-id="9a22a-117">Visual Studio hızlı eylemi</span><span class="sxs-lookup"><span data-stu-id="9a22a-117">Visual Studio quick action</span></span>

<span data-ttu-id="9a22a-118">Visual Studio, ihtiyacınız olan dil sürümü belirlemenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="9a22a-118">Visual Studio helps you determine the language version you need.</span></span> <span data-ttu-id="9a22a-119">Şu anda yapılandırılmış sürümü için kullanılabilir olmayan bir dil özelliğini kullanırsanız, Visual Studio projesi için dil sürümünü güncelleştirmek için olası bir düzeltme gösterir.</span><span class="sxs-lookup"><span data-stu-id="9a22a-119">If you use a language feature that is not available for the currently configured version, Visual Studio shows a potential fix to update the language version for the project.</span></span>

## <a name="set-the-language-version-in-visual-studio"></a><span data-ttu-id="9a22a-120">Visual Studio'da dil sürümünü ayarlayın</span><span class="sxs-lookup"><span data-stu-id="9a22a-120">Set the language version in Visual Studio</span></span>

<span data-ttu-id="9a22a-121">Visual Studio'daki sürüm ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a22a-121">You can set the version in Visual Studio.</span></span> <span data-ttu-id="9a22a-122">Çözüm Gezgini'nde proje düğümüne sağ tıklayın ve **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="9a22a-122">Right-click on the project node in Solution Explorer and select **Properties**.</span></span> <span data-ttu-id="9a22a-123">Seçin **yapı** sekmesinde ve seçin **Gelişmiş** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="9a22a-123">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="9a22a-124">Açılır listede sürümü seçin.</span><span class="sxs-lookup"><span data-stu-id="9a22a-124">In the dropdown, select the version.</span></span> <span data-ttu-id="9a22a-125">Aşağıdaki resimde "en son" ayarı gösterir:</span><span class="sxs-lookup"><span data-stu-id="9a22a-125">The following image shows the "latest" setting:</span></span>

![Gelişmiş derleme ayarları dil sürümü belirtebileceğiniz ekran görüntüsü](./media/configure-language-version/advanced-build-settings.png)

> [!NOTE]
> <span data-ttu-id="9a22a-127">Csproj dosyalarınızı güncelleştirmek için Visual Studio IDE kullanırsanız, IDE her yapı yapılandırması için ayrı düğüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9a22a-127">If you use the Visual Studio IDE to update your csproj files, the IDE creates separate nodes for each build configuration.</span></span> <span data-ttu-id="9a22a-128">Genellikle değerini aynı tüm yapı yapılandırmalarında ayarlamanız, ancak her yapı yapılandırması için açıkça ayarlamak veya bu ayarı değiştirdikten sonra "Tüm yapılandırmaları" seçmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="9a22a-128">You'll typically set the value the same in all build configurations, but you need to set it explicitly for each build configuration, or select "All Configurations" when you modify this setting.</span></span> <span data-ttu-id="9a22a-129">Aşağıdaki csproj dosyanızda görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="9a22a-129">You'll see the following in your csproj file:</span></span>
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

## <a name="edit-the-csproj-file"></a><span data-ttu-id="9a22a-130">Csproj dosyayı düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="9a22a-130">Edit the csproj file</span></span>

<span data-ttu-id="9a22a-131">Dil sürümü ayarlayabileceğiniz, **.csproj** dosya.</span><span class="sxs-lookup"><span data-stu-id="9a22a-131">You can set the language version in your **.csproj** file.</span></span> <span data-ttu-id="9a22a-132">Aşağıdaki gibi bir öğe ekleyin:</span><span class="sxs-lookup"><span data-stu-id="9a22a-132">Add an element like the following:</span></span>

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="9a22a-133">Değer `latest` C# dili son alt sürümü kullanır.</span><span class="sxs-lookup"><span data-stu-id="9a22a-133">The value `latest` uses the latest minor version of the C# language.</span></span> <span data-ttu-id="9a22a-134">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="9a22a-134">Valid values are:</span></span>

|<span data-ttu-id="9a22a-135">Değer</span><span class="sxs-lookup"><span data-stu-id="9a22a-135">Value</span></span>|<span data-ttu-id="9a22a-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9a22a-136">Meaning</span></span>|
|------------|-------------|
|<span data-ttu-id="9a22a-137">default</span><span class="sxs-lookup"><span data-stu-id="9a22a-137">default</span></span>|<span data-ttu-id="9a22a-138">Derleyici destekleyebileceği en son sürümle gelen tüm geçerli dil sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="9a22a-138">The compiler accepts all valid language syntax from the latest major version that it can support.</span></span>|
|<span data-ttu-id="9a22a-139">ISO-1</span><span class="sxs-lookup"><span data-stu-id="9a22a-139">ISO-1</span></span>|<span data-ttu-id="9a22a-140">Derleyici ISO/IEC 23270:2003 C# (1.0/1.2) dahil söz dizimini kabul eder</span><span class="sxs-lookup"><span data-stu-id="9a22a-140">The compiler accepts only syntax that is included in ISO/IEC 23270:2003 C# (1.0/1.2)</span></span> |
|<span data-ttu-id="9a22a-141">ISO-2</span><span class="sxs-lookup"><span data-stu-id="9a22a-141">ISO-2</span></span>|<span data-ttu-id="9a22a-142">Derleyici ISO/IEC 23270:2006 C# (2.0) dahil söz dizimini kabul eder</span><span class="sxs-lookup"><span data-stu-id="9a22a-142">The compiler accepts only syntax that is included in ISO/IEC 23270:2006 C# (2.0)</span></span> |
|<span data-ttu-id="9a22a-143">3</span><span class="sxs-lookup"><span data-stu-id="9a22a-143">3</span></span>|<span data-ttu-id="9a22a-144">Derleyici dahil C# 3.0 veya daha düşük olan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="9a22a-144">The compiler accepts only syntax that is included in C# 3.0 or lower.</span></span>|
|<span data-ttu-id="9a22a-145">4</span><span class="sxs-lookup"><span data-stu-id="9a22a-145">4</span></span>|<span data-ttu-id="9a22a-146">Derleyici dahil C# 4.0 veya daha düşük olan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="9a22a-146">The compiler accepts only syntax that is included in C# 4.0 or lower.</span></span>|
|<span data-ttu-id="9a22a-147">5</span><span class="sxs-lookup"><span data-stu-id="9a22a-147">5</span></span>|<span data-ttu-id="9a22a-148">Derleyici dahil C# 5.0 veya daha düşük olan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="9a22a-148">The compiler accepts only syntax that is included in C# 5.0 or lower.</span></span>|
|<span data-ttu-id="9a22a-149">6</span><span class="sxs-lookup"><span data-stu-id="9a22a-149">6</span></span>|<span data-ttu-id="9a22a-150">Derleyici dahil C# 6. 0 veya daha düşük olan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="9a22a-150">The compiler accepts only syntax that is included in C# 6.0 or lower.</span></span>|
|<span data-ttu-id="9a22a-151">7</span><span class="sxs-lookup"><span data-stu-id="9a22a-151">7</span></span>|<span data-ttu-id="9a22a-152">Derleyici dahil C# 7. 0 veya daha düşük olan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="9a22a-152">The compiler accepts only syntax that is included in C# 7.0 or lower.</span></span>|
|<span data-ttu-id="9a22a-153">7.1</span><span class="sxs-lookup"><span data-stu-id="9a22a-153">7.1</span></span>|<span data-ttu-id="9a22a-154">Derleyici C# 7.1 dahil ya da daha düşük olan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="9a22a-154">The compiler accepts only syntax that is included in C# 7.1 or lower.</span></span>|
|<span data-ttu-id="9a22a-155">7.2</span><span class="sxs-lookup"><span data-stu-id="9a22a-155">7.2</span></span>|<span data-ttu-id="9a22a-156">Derleyici C# 7.2 dahil ya da daha düşük olan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="9a22a-156">The compiler accepts only syntax that is included in C# 7.2 or lower.</span></span>|
|<span data-ttu-id="9a22a-157">7.3</span><span class="sxs-lookup"><span data-stu-id="9a22a-157">7.3</span></span>|<span data-ttu-id="9a22a-158">Derleyici C# 7.3 dahil ya da daha düşük olan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="9a22a-158">The compiler accepts only syntax that is included in C# 7.3 or lower.</span></span>|
|<span data-ttu-id="9a22a-159">en son</span><span class="sxs-lookup"><span data-stu-id="9a22a-159">latest</span></span>|<span data-ttu-id="9a22a-160">Derleyici destekleyebileceği tüm geçerli dil söz dizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="9a22a-160">The compiler accepts all valid language syntax that it can support.</span></span>|

<span data-ttu-id="9a22a-161">Özel dizeler `default` ve `latest` son ana (C# 7.0) ve ikincil (C# 7.3) dil sürümleri yapı makinesinde sırasıyla yüklü çözme.</span><span class="sxs-lookup"><span data-stu-id="9a22a-161">The special strings `default` and `latest` resolve to the latest major (C# 7.0) and minor (C# 7.3) language versions installed on the build machine, respectively.</span></span>

## <a name="configure-multiple-projects"></a><span data-ttu-id="9a22a-162">Birden çok proje yapılandırın</span><span class="sxs-lookup"><span data-stu-id="9a22a-162">Configure multiple projects</span></span>

<span data-ttu-id="9a22a-163">Oluşturabileceğiniz bir **Directory.build.props** içeren dosya `<LangVersion>` öğesi birden fazla dizine yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="9a22a-163">You can create a **Directory.build.props** file that contains the `<LangVersion>` element to configure multiple directories.</span></span> <span data-ttu-id="9a22a-164">Genellikle, çözüm dizininizde yaptığınız.</span><span class="sxs-lookup"><span data-stu-id="9a22a-164">You typically do that in your solution directory.</span></span> <span data-ttu-id="9a22a-165">Aşağıdakileri ekleyin bir **Directory.build.props** çözüm dizininize dosyasında:</span><span class="sxs-lookup"><span data-stu-id="9a22a-165">Add the following to a **Directory.build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>7.3</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="9a22a-166">Şimdi, bu dosyayı içeren dizinin her alt derlemelerde C# sürüm 7.3 sözdizimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9a22a-166">Now, builds in every subdirectory of the directory containing that file will use C# version 7.3 syntax.</span></span> <span data-ttu-id="9a22a-167">Daha fazla bilgi için üzerinde makalesine bakın. [yapınızın özelleştirme](/visualstudio/msbuild/customize-your-build).</span><span class="sxs-lookup"><span data-stu-id="9a22a-167">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="set-the-langversion-compiler-option"></a><span data-ttu-id="9a22a-168">Langversion derleyici seçeneği ayarlama</span><span class="sxs-lookup"><span data-stu-id="9a22a-168">Set the langversion compiler option</span></span>

<span data-ttu-id="9a22a-169">Kullanabileceğiniz `-langversion` komut satırı seçeneği.</span><span class="sxs-lookup"><span data-stu-id="9a22a-169">You can use the `-langversion` command-line option.</span></span> <span data-ttu-id="9a22a-170">Daha fazla bilgi için üzerinde makalesine bakın. [- langversion](../language-reference/compiler-options/langversion-compiler-option.md) derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="9a22a-170">For more information, see the article on the [-langversion](../language-reference/compiler-options/langversion-compiler-option.md) compiler option.</span></span> <span data-ttu-id="9a22a-171">Geçerli değerler listesi yazarak görebilirsiniz `csc -langversion:?`.</span><span class="sxs-lookup"><span data-stu-id="9a22a-171">You can see a list of the valid values by typing  `csc -langversion:?`.</span></span>
