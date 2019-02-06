---
title: .NET Framework ve .NET Core için proje düzenleme
description: .NET Framework ve .NET Core yan yana karşı çözüm derlemek istediğiniz proje sahipleri için yardımcı olur.
author: conniey
ms.date: 04/06/2017
ms.custom: seodec18
ms.openlocfilehash: 4f3469c7f5c8c95cb5bf2ce522c8732c90744755
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2019
ms.locfileid: "55759671"
---
# <a name="organize-your-project-to-support-both-net-framework-and-net-core"></a><span data-ttu-id="9d53e-103">Hem .NET Framework ve .NET Core desteklemek için proje düzenleme</span><span class="sxs-lookup"><span data-stu-id="9d53e-103">Organize your project to support both .NET Framework and .NET Core</span></span>

<span data-ttu-id="9d53e-104">Hem .NET Framework ve .NET Core yan yana için derleyen bir çözüm oluşturmayı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="9d53e-104">Learn how to create a solution that compiles for both .NET Framework and .NET Core side-by-side.</span></span> <span data-ttu-id="9d53e-105">Bu amaca ulaşmak amacıyla projelerini düzenlemek için çeşitli seçenekler bakın.</span><span class="sxs-lookup"><span data-stu-id="9d53e-105">See several options to organize projects to help you achieve this goal.</span></span> <span data-ttu-id="9d53e-106">Ne zaman .NET Core projesi düzeninizi nasıl karar dikkate alınması gereken bazı tipik senaryolar aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9d53e-106">Here are some typical scenarios to consider when you're deciding how to setup your project layout with .NET Core.</span></span> <span data-ttu-id="9d53e-107">Listeden istediğiniz her şeyi kapsamayabilir; projenizin ihtiyaçlarına göre öncelik verin.</span><span class="sxs-lookup"><span data-stu-id="9d53e-107">The list may not cover everything you want; prioritize based on your project's needs.</span></span>

* <span data-ttu-id="9d53e-108">[**Var olan projeleri ve .NET Core projeleri tek projelere birleştirin**][option-csproj]</span><span class="sxs-lookup"><span data-stu-id="9d53e-108">[**Combine existing projects and .NET Core projects into single projects**][option-csproj]</span></span>

  <span data-ttu-id="9d53e-109">*Ne bu için uygundur:*</span><span class="sxs-lookup"><span data-stu-id="9d53e-109">*What this is good for:*</span></span>
  * <span data-ttu-id="9d53e-110">Yapı işleminizin, tek bir proje derlenirken yerine her platform veya farklı bir .NET Framework sürümünü hedefleyen birden çok proje derleme basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="9d53e-110">Simplifying your build process by compiling a single project rather than compiling multiple projects, each targeting a different .NET Framework version or platform.</span></span>
  * <span data-ttu-id="9d53e-111">Tek bir proje dosyası yönetmeniz gerektiğinden çoklu hedefleyen projeler için kaynak dosya yönetimi basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="9d53e-111">Simplifying source file management for multi-targeted projects because you must manage a single project file.</span></span> <span data-ttu-id="9d53e-112">Kaynak dosyaları ekleme/kaldırma, alternatifleri diğer projeleriniz ile el ile eşitleme yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9d53e-112">When adding/removing source files, the alternatives require you to manually sync these with your other projects.</span></span>
  * <span data-ttu-id="9d53e-113">Kolayca tüketim için bir NuGet paketi oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="9d53e-113">Easily generating a NuGet package for consumption.</span></span>
  * <span data-ttu-id="9d53e-114">Derleyici yönergeleri kullanarak kitaplıklarınızdaki belirli bir .NET Framework sürümü için kod yazmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="9d53e-114">Allows you to write code for a specific .NET Framework version in your libraries through the use of compiler directives.</span></span>

  <span data-ttu-id="9d53e-115">*Desteklenmeyen senaryolar:*</span><span class="sxs-lookup"><span data-stu-id="9d53e-115">*Unsupported scenarios:*</span></span>
  * <span data-ttu-id="9d53e-116">Var olan projeleri açmak için Visual Studio 2017 geliştiriciler gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9d53e-116">Requires developers to use Visual Studio 2017 to open existing projects.</span></span> <span data-ttu-id="9d53e-117">Visual Studio'nun eski sürümlerini desteklemek üzere [farklı klasörlerde bulunan proje dosyalarınızı tutma](#support-vs) daha iyi bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="9d53e-117">To support older versions of Visual Studio, [keeping your project files in different folders](#support-vs) is a better option.</span></span>

* <a name="support-vs"></a><span data-ttu-id="9d53e-118">[**Var olan projeleri ve yeni .NET Core projeleri ayrı tut**][option-csproj-folder]</span><span class="sxs-lookup"><span data-stu-id="9d53e-118">[**Keep existing projects and new .NET Core projects separate**][option-csproj-folder]</span></span>

  <span data-ttu-id="9d53e-119">*Ne bu için uygundur:*</span><span class="sxs-lookup"><span data-stu-id="9d53e-119">*What this is good for:*</span></span>
  * <span data-ttu-id="9d53e-120">Geliştiriciler/Visual Studio 2017 sahip olmayan katkıda bulunanlar için yükseltmek zorunda kalmadan mevcut projelerde geliştirme desteklemeye devam ediliyor.</span><span class="sxs-lookup"><span data-stu-id="9d53e-120">Continuing to support development on existing projects without having to upgrade for developers/contributors who may not have Visual Studio 2017.</span></span>
  * <span data-ttu-id="9d53e-121">Bu projelerde hiçbir kod karmaşası olması gerektiğinden yeni hatalar var olan projeleri oluşturma olasılığını kısaltır.</span><span class="sxs-lookup"><span data-stu-id="9d53e-121">Decreasing the possibility of creating new bugs in existing projects because no code churn is required in those projects.</span></span>

## <a name="example"></a><span data-ttu-id="9d53e-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="9d53e-122">Example</span></span>

<span data-ttu-id="9d53e-123">Aşağıdaki depoya göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="9d53e-123">Consider the repository below:</span></span>

<span data-ttu-id="9d53e-124">![Mevcut proje][example-initial-project]</span><span class="sxs-lookup"><span data-stu-id="9d53e-124">![Existing project][example-initial-project]</span></span>

<span data-ttu-id="9d53e-125">[**Kaynak kodu**][example-initial-project-code]</span><span class="sxs-lookup"><span data-stu-id="9d53e-125">[**Source Code**][example-initial-project-code]</span></span>

<span data-ttu-id="9d53e-126">Aşağıdaki kısıtlamalar ve mevcut projeleri karmaşıklığına bağlı olarak bu depo için .NET Core desteği eklemek için çeşitli yollar açıklar.</span><span class="sxs-lookup"><span data-stu-id="9d53e-126">The following describes several ways to add support for .NET Core for this repository depending on the constraints and complexity of the existing projects.</span></span>

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a><span data-ttu-id="9d53e-127">Var olan projeleri birden çok hedefli bir .NET Core projesi ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="9d53e-127">Replace existing projects with a multi-targeted .NET Core project</span></span>

<span data-ttu-id="9d53e-128">Herhangi bir mevcut depoyu reorganıze  *\*.csproj* dosyalar kaldırılır ve tek  *\*.csproj* dosyası birden çok çerçeveyi hedefleyen oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9d53e-128">Reorganize the repository so that any existing *\*.csproj* files are removed and a single *\*.csproj* file is created that targets multiple frameworks.</span></span> <span data-ttu-id="9d53e-129">Tek bir proje için farklı çerçeveler derleyemezsiniz olduğu için bu harika bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="9d53e-129">This is a great option because a single project is able to compile for different frameworks.</span></span> <span data-ttu-id="9d53e-130">Ayrıca, farklı bir derleme seçenekleri ve bağımlılıkları hedeflenen çerçeve başına işleme gücüne sahiptir.</span><span class="sxs-lookup"><span data-stu-id="9d53e-130">It also has the power to handle different compilation options and dependencies per targeted framework.</span></span>

<span data-ttu-id="9d53e-131">![Birden çok çerçeveyi hedefleyen bir csproj oluşturma][example-csproj]</span><span class="sxs-lookup"><span data-stu-id="9d53e-131">![Create an csproj that targets multiple frameworks][example-csproj]</span></span>

<span data-ttu-id="9d53e-132">[**Kaynak kodu**][example-csproj-code]</span><span class="sxs-lookup"><span data-stu-id="9d53e-132">[**Source Code**][example-csproj-code]</span></span>

<span data-ttu-id="9d53e-133">Dikkat edilecek değişiklikler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="9d53e-133">Changes to note are:</span></span>

* <span data-ttu-id="9d53e-134">Değiştirme *packages.config* ve  *\*.csproj* yeni bir [.NET Core  *\*.csproj* ] [ example-csproj-netcore].</span><span class="sxs-lookup"><span data-stu-id="9d53e-134">Replacement of *packages.config* and *\*.csproj* with a new [.NET Core *\*.csproj*][example-csproj-netcore].</span></span> <span data-ttu-id="9d53e-135">NuGet paketleri ile belirtilen `<PackageReference> ItemGroup`.</span><span class="sxs-lookup"><span data-stu-id="9d53e-135">NuGet packages are specified with `<PackageReference> ItemGroup`.</span></span>

## <a name="keep-existing-projects-and-create-a-net-core-project"></a><span data-ttu-id="9d53e-136">Var olan projeleri korumak ve bir .NET Core projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="9d53e-136">Keep existing projects and create a .NET Core project</span></span>

<span data-ttu-id="9d53e-137">Eski çerçeveleri hedefleyen var olan projeler varsa, bu projelerin dokunmayın ve gelecekteki çerçeveleri hedeflemek için bir .NET Core projesinden kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d53e-137">If there are existing projects that target older frameworks, you may want to leave these projects untouched and use a .NET Core project to target future frameworks.</span></span>

<span data-ttu-id="9d53e-138">![Varolan projede, farklı bir klasör ile .NET core projesi][example-csproj-different-folder]</span><span class="sxs-lookup"><span data-stu-id="9d53e-138">![.NET Core project with existing project in different folder][example-csproj-different-folder]</span></span>

<span data-ttu-id="9d53e-139">[**Kaynak kodu**][example-csproj-different-code]</span><span class="sxs-lookup"><span data-stu-id="9d53e-139">[**Source Code**][example-csproj-different-code]</span></span>

<span data-ttu-id="9d53e-140">Dikkat edilecek değişiklikler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="9d53e-140">Changes to note are:</span></span>

* <span data-ttu-id="9d53e-141">.NET Core ve mevcut projeleri ayrı klasörlerde tutulur.</span><span class="sxs-lookup"><span data-stu-id="9d53e-141">The .NET Core and existing projects are kept in separate folders.</span></span>
  * <span data-ttu-id="9d53e-142">Projeleri ayrı klasörlerde tutmak için Visual Studio 2017 için zorlama önler.</span><span class="sxs-lookup"><span data-stu-id="9d53e-142">Keeping projects in separate folders avoids forcing you to have Visual Studio 2017.</span></span> <span data-ttu-id="9d53e-143">Yalnızca eski projelerdeki açılır ayrı bir çözüm oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d53e-143">You can create a separate solution that only opens the old projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="9d53e-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d53e-144">See also</span></span>

<span data-ttu-id="9d53e-145">Lütfen [.NET Core belgeleri taşıma] [ porting-doc] .NET Core ile geçirme hakkında daha fazla yardım almak için.</span><span class="sxs-lookup"><span data-stu-id="9d53e-145">Please see the [.NET Core porting documentation][porting-doc] for more guidance on migrating to .NET Core.</span></span>

[porting-doc]: index.md
[example-initial-project]: media/project-structure/project.png "Mevcut proje"
[example-initial-project-code]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/

[example-csproj]: media/project-structure/project.csproj.png "Birden çok çerçeveyi hedefleyen bir csproj oluşturma"
[example-csproj-code]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/
[example-csproj-netcore]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj

[example-csproj-different-folder]: media/project-structure/project.csproj.different.png "Var olan farklı bir klasöre PCL'de ile .NET core projesi"
[example-csproj-different-code]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/

[option-csproj]: #replace-existing-projects-with-a-multi-targeted-net-core-project
[option-csproj-folder]: #keep-existing-projects-and-create-a-net-core-project
