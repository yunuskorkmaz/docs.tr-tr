---
title: Visual Basic dil sürümünü seçin
description: Belirli bir derleyici sürümü kullanarak söz dizimi doğrulama gerçekleştirmek için derleyicinin yapılandırın.
ms.date: 05/24/2018
ms.openlocfilehash: 3b6d8055dbf64f2a5c38f46b6d66794fc48a1cea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797039"
---
# <a name="select-the-visual-basic-language-version"></a><span data-ttu-id="4b820-103">Visual Basic dil sürümünü seçin</span><span class="sxs-lookup"><span data-stu-id="4b820-103">Select the Visual Basic language version</span></span>

<span data-ttu-id="4b820-104">Visual Basic derleyici varsayılan olarak en son ana sürüm dilinin kullanıma sundu.</span><span class="sxs-lookup"><span data-stu-id="4b820-104">The Visual Basic compiler defaults to the latest major version of the language that has been released.</span></span> <span data-ttu-id="4b820-105">Yeni noktası bir dil sürümünü kullanarak herhangi bir projeyi derlemek tercih edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4b820-105">You may choose to compile any project using a new point release of the language.</span></span> <span data-ttu-id="4b820-106">Daha yeni bir dil sürümü seçme sağlayan sağlamak için projenizi en son dil özelliklerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4b820-106">Choosing a newer version of the language enables your project to make use of the latest language features.</span></span> <span data-ttu-id="4b820-107">Diğer senaryolarda, bir proje dili daha eski bir sürümünü kullanırken düzgün bir şekilde derlendiğinden doğrulamanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="4b820-107">In other scenarios, you may need to validate that a project compiles cleanly when using an older version of the language.</span></span>

<span data-ttu-id="4b820-108">Bu özellik, bir projede yeni dil özellikleri eklemelerine kararı geliştirme ortamınızdan araçları ve SDK'sı yeni sürümlerini yüklemek için karar ayırır.</span><span class="sxs-lookup"><span data-stu-id="4b820-108">This capability decouples the decision to install new versions of the SDK and tools in your development environment from the decision to incorporate new language features in a project.</span></span> <span data-ttu-id="4b820-109">En son SDK'sı ve araçları, yapı makinesinde yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4b820-109">You can install the latest SDK and tools on your build machine.</span></span> <span data-ttu-id="4b820-110">Her proje, derleme için belirli bir dil sürümünü kullanmak için yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="4b820-110">Each project can be configured to use a specific version of the language for its build.</span></span>

<span data-ttu-id="4b820-111">Dil sürümünü ayarlamak için üç yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="4b820-111">There are three ways to set the language version:</span></span>

- <span data-ttu-id="4b820-112">El ile düzenlemeniz, [ **.vbproj** dosyası](#edit-the-vbproj-file)</span><span class="sxs-lookup"><span data-stu-id="4b820-112">Manually edit your [**.vbproj** file](#edit-the-vbproj-file)</span></span>
- <span data-ttu-id="4b820-113">Dil sürümünü ayarlama [bir alt dizinde birden çok proje için](#configure-multiple-projects)</span><span class="sxs-lookup"><span data-stu-id="4b820-113">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects)</span></span>
- <span data-ttu-id="4b820-114">Yapılandırma [ `-langversion` derleyici seçeneği](#set-the-langversion-compiler-option)</span><span class="sxs-lookup"><span data-stu-id="4b820-114">Configure the [`-langversion` compiler option](#set-the-langversion-compiler-option)</span></span>

## <a name="edit-the-vbproj-file"></a><span data-ttu-id="4b820-115">Vbproj dosyayı Düzenle</span><span class="sxs-lookup"><span data-stu-id="4b820-115">Edit the vbproj file</span></span>

<span data-ttu-id="4b820-116">Dil sürümü ayarlayabilirsiniz, **.vbproj** dosya.</span><span class="sxs-lookup"><span data-stu-id="4b820-116">You can set the language version in your **.vbproj** file.</span></span> <span data-ttu-id="4b820-117">Aşağıdaki öğeyi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="4b820-117">Add the following element:</span></span>

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="4b820-118">Değer `latest` Visual Basic dili küçük en son sürümünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="4b820-118">The value `latest` uses the latest minor version of the Visual Basic language.</span></span> <span data-ttu-id="4b820-119">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="4b820-119">Valid values are:</span></span>

|<span data-ttu-id="4b820-120">Değer</span><span class="sxs-lookup"><span data-stu-id="4b820-120">Value</span></span>|<span data-ttu-id="4b820-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b820-121">Meaning</span></span>|
|------------|-------------|
|<span data-ttu-id="4b820-122">default</span><span class="sxs-lookup"><span data-stu-id="4b820-122">default</span></span>|<span data-ttu-id="4b820-123">Derleyici, tüm geçerli dil sözdiziminden destekleyebileceği en son ana sürüm, kabul eder.</span><span class="sxs-lookup"><span data-stu-id="4b820-123">The compiler accepts all valid language syntax from the latest major version that it can support.</span></span>|
|<span data-ttu-id="4b820-124">9</span><span class="sxs-lookup"><span data-stu-id="4b820-124">9</span></span>|<span data-ttu-id="4b820-125">Derleyici, Visual Basic 9.0 dahil veya daha düşük olan söz dizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="4b820-125">The compiler accepts only syntax that is included in Visual Basic 9.0 or lower.</span></span>|
|<span data-ttu-id="4b820-126">10</span><span class="sxs-lookup"><span data-stu-id="4b820-126">10</span></span>|<span data-ttu-id="4b820-127">Derleyici, Visual Basic 10.0 dahil veya daha düşük olan söz dizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="4b820-127">The compiler accepts only syntax that is included in Visual Basic 10.0 or lower.</span></span>|
|<span data-ttu-id="4b820-128">11</span><span class="sxs-lookup"><span data-stu-id="4b820-128">11</span></span>|<span data-ttu-id="4b820-129">Derleyici dahil Visual Basic 11.0 veya daha düşük olan söz dizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="4b820-129">The compiler accepts only syntax that is included in Visual Basic 11.0 or lower.</span></span>|
|<span data-ttu-id="4b820-130">12</span><span class="sxs-lookup"><span data-stu-id="4b820-130">12</span></span>|<span data-ttu-id="4b820-131">Derleyici dahil Visual Basic 12.0 veya daha düşük olan söz dizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="4b820-131">The compiler accepts only syntax that is included in Visual Basic 12.0 or lower.</span></span>|
|<span data-ttu-id="4b820-132">14</span><span class="sxs-lookup"><span data-stu-id="4b820-132">14</span></span>|<span data-ttu-id="4b820-133">Derleyici, Visual Basic 14.0 dahil veya daha düşük olan söz dizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="4b820-133">The compiler accepts only syntax that is included in Visual Basic 14.0 or lower.</span></span>|
|<span data-ttu-id="4b820-134">15</span><span class="sxs-lookup"><span data-stu-id="4b820-134">15</span></span>|<span data-ttu-id="4b820-135">Derleyici, Visual Basic 15.0 dahil veya daha düşük olan söz dizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="4b820-135">The compiler accepts only syntax that is included in Visual Basic 15.0 or lower.</span></span>|
|<span data-ttu-id="4b820-136">15.3</span><span class="sxs-lookup"><span data-stu-id="4b820-136">15.3</span></span>|<span data-ttu-id="4b820-137">Derleyici, Visual Basic 15.3 dahil veya daha düşük olan söz dizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="4b820-137">The compiler accepts only syntax that is included in Visual Basic 15.3 or lower.</span></span>|
|<span data-ttu-id="4b820-138">15.5</span><span class="sxs-lookup"><span data-stu-id="4b820-138">15.5</span></span>|<span data-ttu-id="4b820-139">Derleyici, Visual Basic 15.5 dahil veya daha düşük olan söz dizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="4b820-139">The compiler accepts only syntax that is included in Visual Basic 15.5 or lower.</span></span>|
|<span data-ttu-id="4b820-140">en son</span><span class="sxs-lookup"><span data-stu-id="4b820-140">latest</span></span>|<span data-ttu-id="4b820-141">Derleyici bunu destekleyen tüm geçerli dili söz dizimini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="4b820-141">The compiler accepts all valid language syntax that it can support.</span></span>|

<span data-ttu-id="4b820-142">Özel dizeler `default` ve `latest` sırasıyla yapı makinesinde yüklü en son büyük ve küçük dil sürümleri.</span><span class="sxs-lookup"><span data-stu-id="4b820-142">The special strings `default` and `latest` resolve to the latest major and minor language versions installed on the build machine, respectively.</span></span>

## <a name="configure-multiple-projects"></a><span data-ttu-id="4b820-143">Birden çok proje yapılandırma</span><span class="sxs-lookup"><span data-stu-id="4b820-143">Configure multiple projects</span></span>

<span data-ttu-id="4b820-144">Oluşturabileceğiniz bir **Directory.build.props** içeren dosya `<LangVersion>` birden çok dizini yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="4b820-144">You can create a **Directory.build.props** file that contains the `<LangVersion>` element to configure multiple directories.</span></span> <span data-ttu-id="4b820-145">Genellikle, çözüm dizininizde yaparsınız.</span><span class="sxs-lookup"><span data-stu-id="4b820-145">You typically do that in your solution directory.</span></span> <span data-ttu-id="4b820-146">Ekleyin bir **Directory.build.props** çözüm dizininizde dosya:</span><span class="sxs-lookup"><span data-stu-id="4b820-146">Add the following to a **Directory.build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>15.5</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="4b820-147">Artık, her alt bu dosyayı içeren dizine yapılarında Visual Basic sürüm 15.5 sözdizimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="4b820-147">Now, builds in every subdirectory of the directory containing that file will use Visual Basic version 15.5 syntax.</span></span> <span data-ttu-id="4b820-148">Daha fazla bilgi için makaleye bakın [derlemenizi özelleştirme](/visualstudio/msbuild/customize-your-build).</span><span class="sxs-lookup"><span data-stu-id="4b820-148">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="set-the-langversion-compiler-option"></a><span data-ttu-id="4b820-149">Langversion derleyici seçeneği ayarlama</span><span class="sxs-lookup"><span data-stu-id="4b820-149">Set the langversion compiler option</span></span>

<span data-ttu-id="4b820-150">Kullanabileceğiniz `-langversion` komut satırı seçeneği.</span><span class="sxs-lookup"><span data-stu-id="4b820-150">You can use the `-langversion` command-line option.</span></span> <span data-ttu-id="4b820-151">Daha fazla bilgi için makaleye bakın [- langversion](../reference/command-line-compiler/langversion.md) derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="4b820-151">For more information, see the article on the [-langversion](../reference/command-line-compiler/langversion.md) compiler option.</span></span> <span data-ttu-id="4b820-152">Yazarak geçerli değerlerin bir listesini görebilirsiniz `vbc -langversion:?` .</span><span class="sxs-lookup"><span data-stu-id="4b820-152">You can see a list of the valid values by typing  `vbc -langversion:?` .</span></span>
