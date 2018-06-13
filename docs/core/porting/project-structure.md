---
title: Projeniz .NET Framework ve .NET Core desteklemek için düzenleme
description: .NET Framework ve .NET Core yan yana karşı kendi çözümünü derlemek için isteyen proje sahipleri için yardımcı olur.
author: conniey
ms.author: mairaw
ms.date: 04/06/2017
ms.openlocfilehash: e6cd9c6d66996d9fd24fe71d48091723143e5849
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33211445"
---
# <a name="organizing-your-project-to-support-net-framework-and-net-core"></a><span data-ttu-id="1d009-103">Projeniz .NET Framework ve .NET Core desteklemek için düzenleme</span><span class="sxs-lookup"><span data-stu-id="1d009-103">Organizing your project to support .NET Framework and .NET Core</span></span>

<span data-ttu-id="1d009-104">Bu makalede, .NET Framework ve .NET Core yan yana karşı kendi çözümünü derlemek için isteyen proje sahipleri yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="1d009-104">This article helps project owners who want to compile their solution against .NET Framework and .NET Core side-by-side.</span></span> <span data-ttu-id="1d009-105">Bu hedefe ulaşmak geliştiricilere yardımcı olmak için projeleri düzenlemek için çeşitli seçenekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="1d009-105">It provides several options to organize projects to help developers achieve this goal.</span></span> <span data-ttu-id="1d009-106">Aşağıdaki listede, ne zaman, proje düzeni .NET Core ile Kurulum nasıl karar dikkate alınması gereken bazı tipik senaryolar verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1d009-106">The following list provides some typical scenarios to consider when you're deciding how to setup your project layout with .NET Core.</span></span> <span data-ttu-id="1d009-107">Listenin istediğiniz her şeyi kapsayan değil; projenizin ihtiyaçlara göre öncelik verin.</span><span class="sxs-lookup"><span data-stu-id="1d009-107">The list may not cover everything you want; prioritize based on your project's needs.</span></span>

* <span data-ttu-id="1d009-108">[**Var olan projeleri ve .NET Core projeler tek projelere birleştirin**][option-csproj]</span><span class="sxs-lookup"><span data-stu-id="1d009-108">[**Combine existing projects and .NET Core projects into single projects**][option-csproj]</span></span>

  <span data-ttu-id="1d009-109">*Bu için iyi nedir:*</span><span class="sxs-lookup"><span data-stu-id="1d009-109">*What this is good for:*</span></span>
  * <span data-ttu-id="1d009-110">Yapı işleminizin tek bir proje derleme yerine her farklı bir .NET Framework sürümünü veya platformu hedefleme birden çok proje derleme basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="1d009-110">Simplifying your build process by compiling a single project rather than compiling multiple projects, each targeting a different .NET Framework version or platform.</span></span>
  * <span data-ttu-id="1d009-111">Bir tek proje dosyası yönetmeniz gerekir çünkü çoklu hedefleyen projeler için kaynak dosyası yönetimini basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="1d009-111">Simplifying source file management for multi-targeted projects because you must manage a single project file.</span></span> <span data-ttu-id="1d009-112">Kaynak dosyaları ekleme/kaldırma, alternatifleri diğer projelerinizi bunlarla el ile eşitleme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1d009-112">When adding/removing source files, the alternatives require you to manually sync these with your other projects.</span></span>
  * <span data-ttu-id="1d009-113">Kolayca tüketimi için NuGet paketi oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="1d009-113">Easily generating a NuGet package for consumption.</span></span>
  * <span data-ttu-id="1d009-114">Derleyici yönergeleri kullanarak, kitaplıklarınızdaki belirli bir .NET Framework sürümü için kod yazmayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="1d009-114">Allows you to write code for a specific .NET Framework version in your libraries through the use of compiler directives.</span></span>

  <span data-ttu-id="1d009-115">*Desteklenmeyen senaryolar:*</span><span class="sxs-lookup"><span data-stu-id="1d009-115">*Unsupported scenarios:*</span></span>
  * <span data-ttu-id="1d009-116">Geliştiriciler mevcut projeleri açmak için Visual Studio 2017 kullanmayı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1d009-116">Requires developers to use Visual Studio 2017 to open existing projects.</span></span> <span data-ttu-id="1d009-117">Visual Studio'nun daha eski sürümleri desteklemek için [proje dosyalarınızı farklı klasörlerde tutma](#support-vs) daha iyi bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="1d009-117">To support older versions of Visual Studio, [keeping your project files in different folders](#support-vs) is a better option.</span></span>

* <a name="support-vs"></a><span data-ttu-id="1d009-118">[**Var olan projeleri ve yeni .NET Core projeler ayrı tut**][option-csproj-folder]</span><span class="sxs-lookup"><span data-stu-id="1d009-118">[**Keep existing projects and new .NET Core projects separate**][option-csproj-folder]</span></span>

  <span data-ttu-id="1d009-119">*Bu için iyi nedir:*</span><span class="sxs-lookup"><span data-stu-id="1d009-119">*What this is good for:*</span></span>
  * <span data-ttu-id="1d009-120">Geliştiriciler/Visual Studio 2017 sahip olmaması katkıda bulunanlar için yükseltme yapmak zorunda kalmadan mevcut projelerde geliştirme desteklemeye devam.</span><span class="sxs-lookup"><span data-stu-id="1d009-120">Continuing to support development on existing projects without having to upgrade for developers/contributors who may not have Visual Studio 2017.</span></span>
  * <span data-ttu-id="1d009-121">Kod karmaşası bu projelerde gerektirdiğinden yeni hatalar mevcut projelerinde oluşturma olasılığını azaltmak.</span><span class="sxs-lookup"><span data-stu-id="1d009-121">Decreasing the possibility of creating new bugs in existing projects because no code churn is required in those projects.</span></span>

## <a name="example"></a><span data-ttu-id="1d009-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="1d009-122">Example</span></span>

<span data-ttu-id="1d009-123">Depo göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="1d009-123">Consider the repository below:</span></span>

<span data-ttu-id="1d009-124">![Mevcut proje][example-initial-project]</span><span class="sxs-lookup"><span data-stu-id="1d009-124">![Existing project][example-initial-project]</span></span>

<span data-ttu-id="1d009-125">[**Kaynak kodu**][example-initial-project-code]</span><span class="sxs-lookup"><span data-stu-id="1d009-125">[**Source Code**][example-initial-project-code]</span></span>

<span data-ttu-id="1d009-126">Aşağıdaki kısıtlamalar ve mevcut projeleri karmaşıklığına bağlı olarak bu depo için .NET Core desteği eklemek için çeşitli yollar açıklar.</span><span class="sxs-lookup"><span data-stu-id="1d009-126">The following describes several ways to add support for .NET Core for this repository depending on the constraints and complexity of the existing projects.</span></span>

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a><span data-ttu-id="1d009-127">Mevcut projeleri çoklu hedeflenen .NET Core projesi ile değiştir</span><span class="sxs-lookup"><span data-stu-id="1d009-127">Replace existing projects with a multi-targeted .NET Core project</span></span>

<span data-ttu-id="1d009-128">Herhangi bir varolan deposu reorganıze  *\*.csproj* dosyaları kaldırılır ve tek  *\*.csproj* dosyası birden çok çerçeveyi hedefleyen oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1d009-128">Reorganize the repository so that any existing *\*.csproj* files are removed and a single *\*.csproj* file is created that targets multiple frameworks.</span></span> <span data-ttu-id="1d009-129">Tek bir proje için farklı çerçeveleri derleme mümkün olduğundan bu harika bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="1d009-129">This is a great option because a single project is able to compile for different frameworks.</span></span> <span data-ttu-id="1d009-130">Ayrıca, farklı derleme seçenekleri ve bağımlılıkları hedef çerçeveyi başına işlemek için güç sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1d009-130">It also has the power to handle different compilation options and dependencies per targeted framework.</span></span>

<span data-ttu-id="1d009-131">![Birden çok çerçeveyi hedefleyen bir csproj oluşturma][example-csproj]</span><span class="sxs-lookup"><span data-stu-id="1d009-131">![Create an csproj that targets multiple frameworks][example-csproj]</span></span>

<span data-ttu-id="1d009-132">[**Kaynak kodu**][example-csproj-code]</span><span class="sxs-lookup"><span data-stu-id="1d009-132">[**Source Code**][example-csproj-code]</span></span>

<span data-ttu-id="1d009-133">Not değişiklik şunlardır:</span><span class="sxs-lookup"><span data-stu-id="1d009-133">Changes to note are:</span></span>
* <span data-ttu-id="1d009-134">Değiştirilmesini *packages.config* ve  *\*.csproj* yeni bir [.NET Core  *\*.csproj* ] [ example-csproj-netcore].</span><span class="sxs-lookup"><span data-stu-id="1d009-134">Replacement of *packages.config* and *\*.csproj* with a new [.NET Core *\*.csproj*][example-csproj-netcore].</span></span> <span data-ttu-id="1d009-135">NuGet paketleri ile belirtilir `<PackageReference> ItemGroup`.</span><span class="sxs-lookup"><span data-stu-id="1d009-135">NuGet packages are specified with `<PackageReference> ItemGroup`.</span></span>

## <a name="keep-existing-projects-and-create-a-net-core-project"></a><span data-ttu-id="1d009-136">Mevcut projeleri tutmak ve .NET Core projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="1d009-136">Keep existing projects and create a .NET Core project</span></span>

<span data-ttu-id="1d009-137">Eski çerçeveleri hedef mevcut projeleri varsa, bu projeler dokunulmadan bırakın ve gelecekteki çerçeveleri hedeflemek için bir .NET Core proje kullanın isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d009-137">If there are existing projects that target older frameworks, you may want to leave these projects untouched and use a .NET Core project to target future frameworks.</span></span>

<span data-ttu-id="1d009-138">![.NET core projeyle farklı klasörde mevcut proje][example-csproj-different-folder]</span><span class="sxs-lookup"><span data-stu-id="1d009-138">![.NET Core project with existing project in different folder][example-csproj-different-folder]</span></span>

<span data-ttu-id="1d009-139">[**Kaynak kodu**][example-csproj-different-code]</span><span class="sxs-lookup"><span data-stu-id="1d009-139">[**Source Code**][example-csproj-different-code]</span></span>

<span data-ttu-id="1d009-140">Not değişiklik şunlardır:</span><span class="sxs-lookup"><span data-stu-id="1d009-140">Changes to note are:</span></span>
* <span data-ttu-id="1d009-141">.NET Core ve mevcut projeleri ayrı klasörlerde tutulur.</span><span class="sxs-lookup"><span data-stu-id="1d009-141">The .NET Core and existing projects are kept in separate folders.</span></span>
    * <span data-ttu-id="1d009-142">Projeleri ayrı klasörlerde tutma Visual Studio 2017 olmasını zorlama önler.</span><span class="sxs-lookup"><span data-stu-id="1d009-142">Keeping projects in separate folders avoids forcing you to have Visual Studio 2017.</span></span> <span data-ttu-id="1d009-143">Yalnızca eski projeleri açar ayrı bir çözüm oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d009-143">You can create a separate solution that only opens the old projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="1d009-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1d009-144">See Also</span></span>

<span data-ttu-id="1d009-145">Lütfen bakın [.NET Core belgeleri taşıma] [ porting-doc] .NET Core geçirme hakkında daha fazla yönlendirme için.</span><span class="sxs-lookup"><span data-stu-id="1d009-145">Please see the [.NET Core porting documentation][porting-doc] for more guidance on migrating to .NET Core.</span></span>

[porting-doc]: index.md
[example-initial-project]: media/project-structure/project.png "Mevcut proje"
[example-initial-project-code]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/

[example-csproj]: media/project-structure/project.csproj.png "Birden çok çerçeveyi hedefleyen bir csproj oluşturma"
[example-csproj-code]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/
[example-csproj-netcore]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj

[example-csproj-different-folder]: media/project-structure/project.csproj.different.png "Farklı bir klasör içinde varolan PCL .NET core projeyle"
[example-csproj-different-code]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/

[option-csproj]: #replace-existing-projects-with-a-multi-targeted-net-core-project
[option-csproj-folder]: #keep-existing-projects-and-create-a-net-core-project
