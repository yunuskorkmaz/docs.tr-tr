---
title: Visual Basic dil sürümünü seçin
description: Derleyiciyi belirli bir derleyici sürümünü kullanarak sözdizimi doğrulaması gerçekleştirecek şekilde yapılandırın.
ms.date: 05/24/2018
ms.openlocfilehash: 09503db726f9d993bc986860c57aa98652b696d1
ms.sourcegitcommit: 65af0f0ad316858882845391d60ef7e303b756e8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/05/2021
ms.locfileid: "99585461"
---
# <a name="select-the-visual-basic-language-version"></a><span data-ttu-id="4ba3a-103">Visual Basic dil sürümünü seçin</span><span class="sxs-lookup"><span data-stu-id="4ba3a-103">Select the Visual Basic language version</span></span>

<span data-ttu-id="4ba3a-104">Visual Basic derleyici varsayılan olarak yayınlanan dilin en son ana sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="4ba3a-104">The Visual Basic compiler defaults to the latest major version of the language that has been released.</span></span> <span data-ttu-id="4ba3a-105">Dilin yeni bir noktası sürümünü kullanarak herhangi bir projeyi derlemeyi seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ba3a-105">You may choose to compile any project using a new point release of the language.</span></span> <span data-ttu-id="4ba3a-106">Dilin daha yeni bir sürümünü seçmek, projenizin en son dil özelliklerini kullanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="4ba3a-106">Choosing a newer version of the language enables your project to make use of the latest language features.</span></span> <span data-ttu-id="4ba3a-107">Diğer senaryolarda, dilin eski bir sürümünü kullanırken bir projenin düzgün şekilde derlendiğini doğrulamanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="4ba3a-107">In other scenarios, you may need to validate that a project compiles cleanly when using an older version of the language.</span></span>

<span data-ttu-id="4ba3a-108">Bu özellik, bir projedeki yeni dil özelliklerini birleştirme kararı vermeden geliştirme ortamınızda SDK ve araçların yeni sürümlerini yüklemeye yönelik kararı ayırır.</span><span class="sxs-lookup"><span data-stu-id="4ba3a-108">This capability decouples the decision to install new versions of the SDK and tools in your development environment from the decision to incorporate new language features in a project.</span></span> <span data-ttu-id="4ba3a-109">Yapı makinenize en son SDK ve araçları yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ba3a-109">You can install the latest SDK and tools on your build machine.</span></span> <span data-ttu-id="4ba3a-110">Her proje, derlemesi için dilin belirli bir sürümünü kullanacak şekilde yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="4ba3a-110">Each project can be configured to use a specific version of the language for its build.</span></span>

<span data-ttu-id="4ba3a-111">Dil sürümünü ayarlamak için üç yol vardır:</span><span class="sxs-lookup"><span data-stu-id="4ba3a-111">There are three ways to set the language version:</span></span>

- <span data-ttu-id="4ba3a-112">[ **. Vbproj** dosyanızı el ile düzenleme](#edit-the-vbproj-file)</span><span class="sxs-lookup"><span data-stu-id="4ba3a-112">Manually edit your [**.vbproj** file](#edit-the-vbproj-file)</span></span>
- <span data-ttu-id="4ba3a-113">[Alt dizindeki birden çok proje için](#configure-multiple-projects) dil sürümünü ayarlama</span><span class="sxs-lookup"><span data-stu-id="4ba3a-113">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects)</span></span>
- <span data-ttu-id="4ba3a-114">[ `-langversion` Derleyici seçeneğini](#set-the-langversion-compiler-option) yapılandırma</span><span class="sxs-lookup"><span data-stu-id="4ba3a-114">Configure the [`-langversion` compiler option](#set-the-langversion-compiler-option)</span></span>

## <a name="edit-the-vbproj-file"></a><span data-ttu-id="4ba3a-115">Vbproj dosyasını düzenleme</span><span class="sxs-lookup"><span data-stu-id="4ba3a-115">Edit the vbproj file</span></span>

<span data-ttu-id="4ba3a-116">**. Vbproj** dosyanızdaki dil sürümünü ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ba3a-116">You can set the language version in your **.vbproj** file.</span></span> <span data-ttu-id="4ba3a-117">Şu öğeyi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="4ba3a-117">Add the following element:</span></span>

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="4ba3a-118">Değer `latest` Visual Basic dilinin en son ikincil sürümünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="4ba3a-118">The value `latest` uses the latest minor version of the Visual Basic language.</span></span> <span data-ttu-id="4ba3a-119">Geçerli değerler:</span><span class="sxs-lookup"><span data-stu-id="4ba3a-119">Valid values are:</span></span>

|<span data-ttu-id="4ba3a-120">Değer</span><span class="sxs-lookup"><span data-stu-id="4ba3a-120">Value</span></span>|<span data-ttu-id="4ba3a-121">Anlamı</span><span class="sxs-lookup"><span data-stu-id="4ba3a-121">Meaning</span></span>|
|------------|-------------|
|<span data-ttu-id="4ba3a-122">default</span><span class="sxs-lookup"><span data-stu-id="4ba3a-122">default</span></span>|<span data-ttu-id="4ba3a-123">Derleyici, destekleyebileceği en son ana sürümden tüm geçerli dil sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="4ba3a-123">The compiler accepts all valid language syntax from the latest major version that it can support.</span></span>|
|<span data-ttu-id="4ba3a-124">9</span><span class="sxs-lookup"><span data-stu-id="4ba3a-124">9</span></span>|<span data-ttu-id="4ba3a-125">Derleyici yalnızca Visual Basic 9,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="4ba3a-125">The compiler accepts only syntax that is included in Visual Basic 9.0 or lower.</span></span>|
|<span data-ttu-id="4ba3a-126">10</span><span class="sxs-lookup"><span data-stu-id="4ba3a-126">10</span></span>|<span data-ttu-id="4ba3a-127">Derleyici yalnızca Visual Basic 10,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="4ba3a-127">The compiler accepts only syntax that is included in Visual Basic 10.0 or lower.</span></span>|
|<span data-ttu-id="4ba3a-128">11</span><span class="sxs-lookup"><span data-stu-id="4ba3a-128">11</span></span>|<span data-ttu-id="4ba3a-129">Derleyici yalnızca Visual Basic 11,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="4ba3a-129">The compiler accepts only syntax that is included in Visual Basic 11.0 or lower.</span></span>|
|<span data-ttu-id="4ba3a-130">12</span><span class="sxs-lookup"><span data-stu-id="4ba3a-130">12</span></span>|<span data-ttu-id="4ba3a-131">Derleyici yalnızca Visual Basic 12,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="4ba3a-131">The compiler accepts only syntax that is included in Visual Basic 12.0 or lower.</span></span>|
|<span data-ttu-id="4ba3a-132">14</span><span class="sxs-lookup"><span data-stu-id="4ba3a-132">14</span></span>|<span data-ttu-id="4ba3a-133">Derleyici yalnızca Visual Basic 14,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="4ba3a-133">The compiler accepts only syntax that is included in Visual Basic 14.0 or lower.</span></span>|
|<span data-ttu-id="4ba3a-134">15</span><span class="sxs-lookup"><span data-stu-id="4ba3a-134">15</span></span>|<span data-ttu-id="4ba3a-135">Derleyici yalnızca Visual Basic 15,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="4ba3a-135">The compiler accepts only syntax that is included in Visual Basic 15.0 or lower.</span></span>|
|<span data-ttu-id="4ba3a-136">15.3</span><span class="sxs-lookup"><span data-stu-id="4ba3a-136">15.3</span></span>|<span data-ttu-id="4ba3a-137">Derleyici yalnızca Visual Basic 15,3 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="4ba3a-137">The compiler accepts only syntax that is included in Visual Basic 15.3 or lower.</span></span>|
|<span data-ttu-id="4ba3a-138">15.5</span><span class="sxs-lookup"><span data-stu-id="4ba3a-138">15.5</span></span>|<span data-ttu-id="4ba3a-139">Derleyici yalnızca Visual Basic 15,5 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="4ba3a-139">The compiler accepts only syntax that is included in Visual Basic 15.5 or lower.</span></span>|
|<span data-ttu-id="4ba3a-140">16</span><span class="sxs-lookup"><span data-stu-id="4ba3a-140">16</span></span>|<span data-ttu-id="4ba3a-141">Derleyici yalnızca Visual Basic 16 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="4ba3a-141">The compiler accepts only syntax that is included in Visual Basic 16 or lower.</span></span>|
|<span data-ttu-id="4ba3a-142">16.9</span><span class="sxs-lookup"><span data-stu-id="4ba3a-142">16.9</span></span>|<span data-ttu-id="4ba3a-143">Derleyici yalnızca Visual Basic 16,9 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="4ba3a-143">The compiler accepts only syntax that is included in Visual Basic 16.9 or lower.</span></span>|
|<span data-ttu-id="4ba3a-144">en son</span><span class="sxs-lookup"><span data-stu-id="4ba3a-144">latest</span></span>|<span data-ttu-id="4ba3a-145">Derleyici, destekleyebileceği tüm geçerli dil sözdizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="4ba3a-145">The compiler accepts all valid language syntax that it can support.</span></span>|

<span data-ttu-id="4ba3a-146">Özel dizeler, `default` `latest` sırasıyla derleme makinesinde yüklü en son büyük ve küçük dil sürümlerine çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="4ba3a-146">The special strings `default` and `latest` resolve to the latest major and minor language versions installed on the build machine, respectively.</span></span>

## <a name="configure-multiple-projects"></a><span data-ttu-id="4ba3a-147">Birden çok proje yapılandırma</span><span class="sxs-lookup"><span data-stu-id="4ba3a-147">Configure multiple projects</span></span>

<span data-ttu-id="4ba3a-148">Birden çok dizini yapılandırmak için öğesini içeren bir **Dizin. Build. props** dosyası oluşturabilirsiniz `<LangVersion>` .</span><span class="sxs-lookup"><span data-stu-id="4ba3a-148">You can create a **Directory.build.props** file that contains the `<LangVersion>` element to configure multiple directories.</span></span> <span data-ttu-id="4ba3a-149">Bunu genellikle çözüm dizininizde yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ba3a-149">You typically do that in your solution directory.</span></span> <span data-ttu-id="4ba3a-150">Aşağıdakileri çözüm dizininizde bir **Dizin. Build. props** dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="4ba3a-150">Add the following to a **Directory.build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>15.5</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="4ba3a-151">Şimdi, bu dosyayı içeren dizinin her alt dizinindeki derlemeler Visual Basic sürüm 15,5 sözdizimini kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="4ba3a-151">Now, builds in every subdirectory of the directory containing that file will use Visual Basic version 15.5 syntax.</span></span> <span data-ttu-id="4ba3a-152">Daha fazla bilgi için, [yapınızı özelleştirme](/visualstudio/msbuild/customize-your-build)başlıklı makaleye bakın.</span><span class="sxs-lookup"><span data-stu-id="4ba3a-152">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="set-the-langversion-compiler-option"></a><span data-ttu-id="4ba3a-153">Langversion derleyici seçeneğini ayarlayın</span><span class="sxs-lookup"><span data-stu-id="4ba3a-153">Set the langversion compiler option</span></span>

<span data-ttu-id="4ba3a-154">`-langversion`Komut satırı seçeneğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ba3a-154">You can use the `-langversion` command-line option.</span></span> <span data-ttu-id="4ba3a-155">Daha fazla bilgi için, [-langversion](../reference/command-line-compiler/langversion.md) derleyici seçeneğinde makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="4ba3a-155">For more information, see the article on the [-langversion](../reference/command-line-compiler/langversion.md) compiler option.</span></span> <span data-ttu-id="4ba3a-156">Yazarak geçerli değerlerin bir listesini görebilirsiniz  `vbc -langversion:?` .</span><span class="sxs-lookup"><span data-stu-id="4ba3a-156">You can see a list of the valid values by typing  `vbc -langversion:?` .</span></span>
