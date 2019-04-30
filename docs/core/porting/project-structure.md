---
title: .NET Framework ve .NET Core için proje düzenleme
description: .NET Framework ve .NET Core yan yana karşı çözüm derlemek istediğiniz proje sahipleri için yardımcı olur.
author: conniey
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: ab484ccc2c5b51b2ee1dca57df51669d288f3e6b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663211"
---
# <a name="organize-your-project-to-support-both-net-framework-and-net-core"></a><span data-ttu-id="9459c-103">Hem .NET Framework ve .NET Core desteklemek için proje düzenleme</span><span class="sxs-lookup"><span data-stu-id="9459c-103">Organize your project to support both .NET Framework and .NET Core</span></span>

<span data-ttu-id="9459c-104">Hem .NET Framework ve .NET Core yan yana için derleyen bir çözüm oluşturmayı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="9459c-104">Learn how to create a solution that compiles for both .NET Framework and .NET Core side-by-side.</span></span> <span data-ttu-id="9459c-105">Bu amaca ulaşmak amacıyla projelerini düzenlemek için çeşitli seçenekler bakın.</span><span class="sxs-lookup"><span data-stu-id="9459c-105">See several options to organize projects to help you achieve this goal.</span></span> <span data-ttu-id="9459c-106">Ne zaman .NET Core projesi düzeninizi nasıl karar dikkate alınması gereken bazı tipik senaryolar aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9459c-106">Here are some typical scenarios to consider when you're deciding how to setup your project layout with .NET Core.</span></span> <span data-ttu-id="9459c-107">Listeden istediğiniz her şeyi kapsamayabilir; projenizin ihtiyaçlarına göre öncelik verin.</span><span class="sxs-lookup"><span data-stu-id="9459c-107">The list may not cover everything you want; prioritize based on your project's needs.</span></span>

* [<span data-ttu-id="9459c-108">**Var olan projeleri ve .NET Core projeleri tek projelere birleştirin**</span><span class="sxs-lookup"><span data-stu-id="9459c-108">**Combine existing projects and .NET Core projects into single projects**</span></span>](#replace-existing-projects-with-a-multi-targeted-net-core-project)

  <span data-ttu-id="9459c-109">*Ne bu için uygundur:*</span><span class="sxs-lookup"><span data-stu-id="9459c-109">*What this is good for:*</span></span>
  * <span data-ttu-id="9459c-110">Yapı işleminizin, tek bir proje derlenirken yerine her platform veya farklı bir .NET Framework sürümünü hedefleyen birden çok proje derleme basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="9459c-110">Simplifying your build process by compiling a single project rather than compiling multiple projects, each targeting a different .NET Framework version or platform.</span></span>
  * <span data-ttu-id="9459c-111">Tek bir proje dosyası yönetmeniz gerektiğinden çoklu hedefleyen projeler için kaynak dosya yönetimi basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="9459c-111">Simplifying source file management for multi-targeted projects because you must manage a single project file.</span></span> <span data-ttu-id="9459c-112">Kaynak dosyaları ekleme/kaldırma, alternatifleri diğer projeleriniz ile el ile eşitleme yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9459c-112">When adding/removing source files, the alternatives require you to manually sync these with your other projects.</span></span>
  * <span data-ttu-id="9459c-113">Kolayca tüketim için bir NuGet paketi oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="9459c-113">Easily generating a NuGet package for consumption.</span></span>
  * <span data-ttu-id="9459c-114">Derleyici yönergeleri kullanarak kitaplıklarınızdaki belirli bir .NET Framework sürümü için kod yazmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="9459c-114">Allows you to write code for a specific .NET Framework version in your libraries through the use of compiler directives.</span></span>

  <span data-ttu-id="9459c-115">*Desteklenmeyen senaryolar:*</span><span class="sxs-lookup"><span data-stu-id="9459c-115">*Unsupported scenarios:*</span></span>
  * <span data-ttu-id="9459c-116">Var olan projeleri açmak için Visual Studio 2017 geliştiriciler gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9459c-116">Requires developers to use Visual Studio 2017 to open existing projects.</span></span> <span data-ttu-id="9459c-117">Visual Studio'nun eski sürümlerini desteklemek üzere [farklı klasörlerde bulunan proje dosyalarınızı tutma](#support-vs) daha iyi bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="9459c-117">To support older versions of Visual Studio, [keeping your project files in different folders](#support-vs) is a better option.</span></span>

* <a name="support-vs"></a><span data-ttu-id="9459c-118">[**Var olan projeleri ve yeni .NET Core projeleri ayrı tut**](#keep-existing-projects-and-create-a-net-core-project)</span><span class="sxs-lookup"><span data-stu-id="9459c-118">[**Keep existing projects and new .NET Core projects separate**](#keep-existing-projects-and-create-a-net-core-project)</span></span>

  <span data-ttu-id="9459c-119">*Ne bu için uygundur:*</span><span class="sxs-lookup"><span data-stu-id="9459c-119">*What this is good for:*</span></span>
  * <span data-ttu-id="9459c-120">Geliştiriciler/Visual Studio 2017 sahip olmayan katkıda bulunanlar için yükseltmek zorunda kalmadan mevcut projelerde geliştirme desteklemeye devam ediliyor.</span><span class="sxs-lookup"><span data-stu-id="9459c-120">Continuing to support development on existing projects without having to upgrade for developers/contributors who may not have Visual Studio 2017.</span></span>
  * <span data-ttu-id="9459c-121">Bu projelerde hiçbir kod karmaşası olması gerektiğinden yeni hatalar var olan projeleri oluşturma olasılığını kısaltır.</span><span class="sxs-lookup"><span data-stu-id="9459c-121">Decreasing the possibility of creating new bugs in existing projects because no code churn is required in those projects.</span></span>

## <a name="example"></a><span data-ttu-id="9459c-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="9459c-122">Example</span></span>

<span data-ttu-id="9459c-123">Aşağıdaki depoya göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="9459c-123">Consider the repository below:</span></span>

![Mevcut proje](./media/project-structure/existing-project-structure.png)

[<span data-ttu-id="9459c-125">**Kaynak kodu**</span><span class="sxs-lookup"><span data-stu-id="9459c-125">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/)

<span data-ttu-id="9459c-126">Aşağıdaki kısıtlamalar ve mevcut projeleri karmaşıklığına bağlı olarak bu depo için .NET Core desteği eklemek için çeşitli yollar açıklar.</span><span class="sxs-lookup"><span data-stu-id="9459c-126">The following describes several ways to add support for .NET Core for this repository depending on the constraints and complexity of the existing projects.</span></span>

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a><span data-ttu-id="9459c-127">Var olan projeleri birden çok hedefli bir .NET Core projesi ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="9459c-127">Replace existing projects with a multi-targeted .NET Core project</span></span>

<span data-ttu-id="9459c-128">Herhangi bir mevcut depoyu reorganıze  *\*.csproj* dosyalar kaldırılır ve tek  *\*.csproj* dosyası birden çok çerçeveyi hedefleyen oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9459c-128">Reorganize the repository so that any existing *\*.csproj* files are removed and a single *\*.csproj* file is created that targets multiple frameworks.</span></span> <span data-ttu-id="9459c-129">Tek bir proje için farklı çerçeveler derleyemezsiniz olduğu için bu harika bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="9459c-129">This is a great option because a single project is able to compile for different frameworks.</span></span> <span data-ttu-id="9459c-130">Ayrıca, farklı bir derleme seçenekleri ve bağımlılıkları hedeflenen çerçeve başına işleme gücüne sahiptir.</span><span class="sxs-lookup"><span data-stu-id="9459c-130">It also has the power to handle different compilation options and dependencies per targeted framework.</span></span>

![Birden çok çerçeveyi hedefleyen bir csproj oluşturma](./media/project-structure/multi-targeted-project.png)

[<span data-ttu-id="9459c-132">**Kaynak kodu**</span><span class="sxs-lookup"><span data-stu-id="9459c-132">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/)

<span data-ttu-id="9459c-133">Dikkat edilecek değişiklikler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="9459c-133">Changes to note are:</span></span>

* <span data-ttu-id="9459c-134">Değiştirme *packages.config* ve  *\*.csproj* yeni bir [.NET Core  *\*.csproj*](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj).</span><span class="sxs-lookup"><span data-stu-id="9459c-134">Replacement of *packages.config* and *\*.csproj* with a new [.NET Core *\*.csproj*](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj).</span></span> <span data-ttu-id="9459c-135">NuGet paketleri ile belirtilen `<PackageReference> ItemGroup`.</span><span class="sxs-lookup"><span data-stu-id="9459c-135">NuGet packages are specified with `<PackageReference> ItemGroup`.</span></span>

## <a name="keep-existing-projects-and-create-a-net-core-project"></a><span data-ttu-id="9459c-136">Var olan projeleri korumak ve bir .NET Core projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="9459c-136">Keep existing projects and create a .NET Core project</span></span>

<span data-ttu-id="9459c-137">Eski çerçeveleri hedefleyen var olan projeler varsa, bu projelerin dokunmayın ve gelecekteki çerçeveleri hedeflemek için bir .NET Core projesinden kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9459c-137">If there are existing projects that target older frameworks, you may want to leave these projects untouched and use a .NET Core project to target future frameworks.</span></span>

![Varolan projede, farklı bir klasör ile .NET core projesi](./media/project-structure/separate-projects-same-source.png)

[<span data-ttu-id="9459c-139">**Kaynak kodu**</span><span class="sxs-lookup"><span data-stu-id="9459c-139">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/)

<span data-ttu-id="9459c-140">Dikkat edilecek değişiklikler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="9459c-140">Changes to note are:</span></span>

* <span data-ttu-id="9459c-141">.NET Core ve mevcut projeleri ayrı klasörlerde tutulur.</span><span class="sxs-lookup"><span data-stu-id="9459c-141">The .NET Core and existing projects are kept in separate folders.</span></span>
  * <span data-ttu-id="9459c-142">Projeleri ayrı klasörlerde tutmak için Visual Studio 2017 için zorlama önler.</span><span class="sxs-lookup"><span data-stu-id="9459c-142">Keeping projects in separate folders avoids forcing you to have Visual Studio 2017.</span></span> <span data-ttu-id="9459c-143">Yalnızca eski projelerdeki açılır ayrı bir çözüm oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9459c-143">You can create a separate solution that only opens the old projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="9459c-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9459c-144">See also</span></span>

<span data-ttu-id="9459c-145">Lütfen [.NET Core belgeleri taşıma](index.md) .NET Core ile geçirme hakkında daha fazla yardım almak için.</span><span class="sxs-lookup"><span data-stu-id="9459c-145">Please see the [.NET Core porting documentation](index.md) for more guidance on migrating to .NET Core.</span></span>
