---
title: Projeniz .NET Framework ve .NET Core desteklemek için düzenleme
description: .NET Framework ve .NET Core yan yana karşı kendi çözümünü derlemek için isteyen proje sahipleri için yardımcı olur.
keywords: .NET, .NET core, .NET Framework, proje düzeni, birden çok çerçeveyi
author: conniey
ms.author: mairaw
ms.date: 04/06/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 3af62252-1dfa-4336-8d2f-5cfdb57d7724
ms.workload:
- dotnetcore
ms.openlocfilehash: 2392c6e477138e21dc98055fe7ecca84789f07af
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="organizing-your-project-to-support-net-framework-and-net-core"></a><span data-ttu-id="82327-104">Projeniz .NET Framework ve .NET Core desteklemek için düzenleme</span><span class="sxs-lookup"><span data-stu-id="82327-104">Organizing your project to support .NET Framework and .NET Core</span></span>

<span data-ttu-id="82327-105">Bu makalede, .NET Framework ve .NET Core yan yana karşı kendi çözümünü derlemek için isteyen proje sahipleri yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="82327-105">This article helps project owners who want to compile their solution against .NET Framework and .NET Core side-by-side.</span></span> <span data-ttu-id="82327-106">Bu hedefe ulaşmak geliştiricilere yardımcı olmak için projeleri düzenlemek için çeşitli seçenekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="82327-106">It provides several options to organize projects to help developers achieve this goal.</span></span> <span data-ttu-id="82327-107">Aşağıdaki listede, ne zaman, proje düzeni .NET Core ile Kurulum nasıl karar dikkate alınması gereken bazı tipik senaryolar verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="82327-107">The following list provides some typical scenarios to consider when you're deciding how to setup your project layout with .NET Core.</span></span> <span data-ttu-id="82327-108">Listenin istediğiniz her şeyi kapsayan değil; projenizin ihtiyaçlara göre öncelik verin.</span><span class="sxs-lookup"><span data-stu-id="82327-108">The list may not cover everything you want; prioritize based on your project's needs.</span></span>

* <span data-ttu-id="82327-109">[**Var olan projeleri ve .NET Core projeler tek projelere birleştirin**][option-csproj]</span><span class="sxs-lookup"><span data-stu-id="82327-109">[**Combine existing projects and .NET Core projects into single projects**][option-csproj]</span></span>

  <span data-ttu-id="82327-110">*Bu için iyi nedir:*</span><span class="sxs-lookup"><span data-stu-id="82327-110">*What this is good for:*</span></span>
  * <span data-ttu-id="82327-111">Yapı işleminizin tek bir proje derleme yerine her farklı bir .NET Framework sürümünü veya platformu hedefleme birden çok proje derleme basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="82327-111">Simplifying your build process by compiling a single project rather than compiling multiple projects, each targeting a different .NET Framework version or platform.</span></span>
  * <span data-ttu-id="82327-112">Bir tek proje dosyası yönetmeniz gerekir çünkü çoklu hedefleyen projeler için kaynak dosyası yönetimini basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="82327-112">Simplifying source file management for multi-targeted projects because you must manage a single project file.</span></span> <span data-ttu-id="82327-113">Kaynak dosyaları ekleme/kaldırma, alternatifleri diğer projelerinizi bunlarla el ile eşitleme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="82327-113">When adding/removing source files, the alternatives require you to manually sync these with your other projects.</span></span>
  * <span data-ttu-id="82327-114">Kolayca tüketimi için NuGet paketi oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="82327-114">Easily generating a NuGet package for consumption.</span></span>
  * <span data-ttu-id="82327-115">Derleyici yönergeleri kullanarak, kitaplıklarınızdaki belirli bir .NET Framework sürümü için kod yazmayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="82327-115">Allows you to write code for a specific .NET Framework version in your libraries through the use of compiler directives.</span></span>

  <span data-ttu-id="82327-116">*Desteklenmeyen senaryolar:*</span><span class="sxs-lookup"><span data-stu-id="82327-116">*Unsupported scenarios:*</span></span>
  * <span data-ttu-id="82327-117">Geliştiriciler mevcut projeleri açmak için Visual Studio 2017 kullanmayı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="82327-117">Requires developers to use Visual Studio 2017 to open existing projects.</span></span> <span data-ttu-id="82327-118">Visual Studio'nun daha eski sürümleri desteklemek için [proje dosyalarınızı farklı klasörlerde tutma](#support-vs) daha iyi bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="82327-118">To support older versions of Visual Studio, [keeping your project files in different folders](#support-vs) is a better option.</span></span>

* <a name="support-vs"></a><span data-ttu-id="82327-119">[**Var olan projeleri ve yeni .NET Core projeler ayrı tut**][option-csproj-folder]</span><span class="sxs-lookup"><span data-stu-id="82327-119">[**Keep existing projects and new .NET Core projects separate**][option-csproj-folder]</span></span>

  <span data-ttu-id="82327-120">*Bu için iyi nedir:*</span><span class="sxs-lookup"><span data-stu-id="82327-120">*What this is good for:*</span></span>
  * <span data-ttu-id="82327-121">Geliştiriciler/Visual Studio 2017 sahip olmaması katkıda bulunanlar için yükseltme yapmak zorunda kalmadan mevcut projelerde geliştirme desteklemeye devam.</span><span class="sxs-lookup"><span data-stu-id="82327-121">Continuing to support development on existing projects without having to upgrade for developers/contributors who may not have Visual Studio 2017.</span></span>
  * <span data-ttu-id="82327-122">Kod karmaşası bu projelerde gerektirdiğinden yeni hatalar mevcut projelerinde oluşturma olasılığını azaltmak.</span><span class="sxs-lookup"><span data-stu-id="82327-122">Decreasing the possibility of creating new bugs in existing projects because no code churn is required in those projects.</span></span>

## <a name="example"></a><span data-ttu-id="82327-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="82327-123">Example</span></span>

<span data-ttu-id="82327-124">Depo göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="82327-124">Consider the repository below:</span></span>

<span data-ttu-id="82327-125">![Mevcut proje][example-initial-project]</span><span class="sxs-lookup"><span data-stu-id="82327-125">![Existing project][example-initial-project]</span></span>

<span data-ttu-id="82327-126">[**Kaynak kodu**][example-initial-project-code]</span><span class="sxs-lookup"><span data-stu-id="82327-126">[**Source Code**][example-initial-project-code]</span></span>

<span data-ttu-id="82327-127">Aşağıdaki kısıtlamalar ve mevcut projeleri karmaşıklığına bağlı olarak bu depo için .NET Core desteği eklemek için çeşitli yollar açıklar.</span><span class="sxs-lookup"><span data-stu-id="82327-127">The following describes several ways to add support for .NET Core for this repository depending on the constraints and complexity of the existing projects.</span></span>

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a><span data-ttu-id="82327-128">Mevcut projeleri çoklu hedeflenen .NET Core projesi ile değiştir</span><span class="sxs-lookup"><span data-stu-id="82327-128">Replace existing projects with a multi-targeted .NET Core project</span></span>

<span data-ttu-id="82327-129">Herhangi bir varolan deposu reorganıze  *\*.csproj* dosyaları kaldırılır ve tek  *\*.csproj* dosyası birden çok çerçeveyi hedefleyen oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="82327-129">Reorganize the repository so that any existing *\*.csproj* files are removed and a single *\*.csproj* file is created that targets multiple frameworks.</span></span> <span data-ttu-id="82327-130">Tek bir proje için farklı çerçeveleri derleme mümkün olduğundan bu harika bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="82327-130">This is a great option because a single project is able to compile for different frameworks.</span></span> <span data-ttu-id="82327-131">Ayrıca, farklı derleme seçenekleri ve bağımlılıkları hedef çerçeveyi başına işlemek için güç sahiptir.</span><span class="sxs-lookup"><span data-stu-id="82327-131">It also has the power to handle different compilation options and dependencies per targeted framework.</span></span>

<span data-ttu-id="82327-132">![Birden çok çerçeveyi hedefleyen bir csproj oluşturma][example-csproj]</span><span class="sxs-lookup"><span data-stu-id="82327-132">![Create an csproj that targets multiple frameworks][example-csproj]</span></span>

<span data-ttu-id="82327-133">[**Kaynak kodu**][example-csproj-code]</span><span class="sxs-lookup"><span data-stu-id="82327-133">[**Source Code**][example-csproj-code]</span></span>

<span data-ttu-id="82327-134">Not değişiklik şunlardır:</span><span class="sxs-lookup"><span data-stu-id="82327-134">Changes to note are:</span></span>
* <span data-ttu-id="82327-135">Değiştirilmesini *packages.config* ve  *\*.csproj* yeni bir [.NET Core  *\*.csproj* ] [ example-csproj-netcore].</span><span class="sxs-lookup"><span data-stu-id="82327-135">Replacement of *packages.config* and *\*.csproj* with a new [.NET Core *\*.csproj*][example-csproj-netcore].</span></span> <span data-ttu-id="82327-136">NuGet paketleri ile belirtilir `<PackageReference> ItemGroup`.</span><span class="sxs-lookup"><span data-stu-id="82327-136">NuGet packages are specified with `<PackageReference> ItemGroup`.</span></span>

## <a name="keep-existing-projects-and-create-a-net-core-project"></a><span data-ttu-id="82327-137">Mevcut projeleri tutmak ve .NET Core projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="82327-137">Keep existing projects and create a .NET Core project</span></span>

<span data-ttu-id="82327-138">Eski çerçeveleri hedef mevcut projeleri varsa, bu projeler dokunulmadan bırakın ve gelecekteki çerçeveleri hedeflemek için bir .NET Core proje kullanın isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82327-138">If there are existing projects that target older frameworks, you may want to leave these projects untouched and use a .NET Core project to target future frameworks.</span></span>

<span data-ttu-id="82327-139">![.NET core projeyle farklı klasörde mevcut proje][example-csproj-different-folder]</span><span class="sxs-lookup"><span data-stu-id="82327-139">![.NET Core project with existing project in different folder][example-csproj-different-folder]</span></span>

<span data-ttu-id="82327-140">[**Kaynak kodu**][example-csproj-different-code]</span><span class="sxs-lookup"><span data-stu-id="82327-140">[**Source Code**][example-csproj-different-code]</span></span>

<span data-ttu-id="82327-141">Not değişiklik şunlardır:</span><span class="sxs-lookup"><span data-stu-id="82327-141">Changes to note are:</span></span>
* <span data-ttu-id="82327-142">.NET Core ve mevcut projeleri ayrı klasörlerde tutulur.</span><span class="sxs-lookup"><span data-stu-id="82327-142">The .NET Core and existing projects are kept in separate folders.</span></span>
    * <span data-ttu-id="82327-143">Projeleri ayrı klasörlerde tutma Visual Studio 2017 olmasını zorlama önler.</span><span class="sxs-lookup"><span data-stu-id="82327-143">Keeping projects in separate folders avoids forcing you to have Visual Studio 2017.</span></span> <span data-ttu-id="82327-144">Yalnızca eski projeleri açar ayrı bir çözüm oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82327-144">You can create a separate solution that only opens the old projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="82327-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="82327-145">See Also</span></span>

<span data-ttu-id="82327-146">Lütfen bakın [.NET Core belgeleri taşıma] [ porting-doc] .NET Core geçirme hakkında daha fazla yönlendirme için.</span><span class="sxs-lookup"><span data-stu-id="82327-146">Please see the [.NET Core porting documentation][porting-doc] for more guidance on migrating to .NET Core.</span></span>

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
