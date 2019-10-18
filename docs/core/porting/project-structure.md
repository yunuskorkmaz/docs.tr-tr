---
title: .NET Framework ve .NET Core için projeleri düzenleme
description: Çözümlerini .NET Framework ve .NET Core ile yan yana derlemek isteyen proje sahipleri için yardım.
author: conniey
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: 701aa64be8d6c712ef635411ad6c226a3c3ab8ed
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522976"
---
# <a name="organize-your-project-to-support-both-net-framework-and-net-core"></a><span data-ttu-id="6bc9d-103">Projenizi hem .NET Framework hem de .NET Core 'ı destekleyecek şekilde düzenleyin</span><span class="sxs-lookup"><span data-stu-id="6bc9d-103">Organize your project to support both .NET Framework and .NET Core</span></span>

<span data-ttu-id="6bc9d-104">Hem .NET Framework hem de .NET Core yan yana için derlenen bir çözüm oluşturmayı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="6bc9d-104">Learn how to create a solution that compiles for both .NET Framework and .NET Core side-by-side.</span></span> <span data-ttu-id="6bc9d-105">Bu amaca ulaşmanıza yardımcı olmak için projeleri düzenlemek için çeşitli seçeneklere bakın.</span><span class="sxs-lookup"><span data-stu-id="6bc9d-105">See several options to organize projects to help you achieve this goal.</span></span> <span data-ttu-id="6bc9d-106">İşte, proje düzeninizi .NET Core ile ayarlama konusunda karar verirken göz önünde bulundurmanız gereken bazı tipik senaryolar aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6bc9d-106">Here are some typical scenarios to consider when you're deciding how to setup your project layout with .NET Core.</span></span> <span data-ttu-id="6bc9d-107">Liste istediğiniz her şeyi kapsamayabilir; projenizin ihtiyaçlarına göre öncelik verir.</span><span class="sxs-lookup"><span data-stu-id="6bc9d-107">The list may not cover everything you want; prioritize based on your project's needs.</span></span>

- [<span data-ttu-id="6bc9d-108">**Mevcut projeleri ve .NET Core projelerini tek projeler halinde birleştirin**</span><span class="sxs-lookup"><span data-stu-id="6bc9d-108">**Combine existing projects and .NET Core projects into single projects**</span></span>](#replace-existing-projects-with-a-multi-targeted-net-core-project)

  <span data-ttu-id="6bc9d-109">*Bunun için uygun olan şey:*</span><span class="sxs-lookup"><span data-stu-id="6bc9d-109">*What this is good for:*</span></span>
  - <span data-ttu-id="6bc9d-110">Her biri farklı bir .NET Framework sürümü veya platformu hedefleyen birden çok proje derlemek yerine, tek bir projeyi derleyerek yapı işleminizi basitleştirin.</span><span class="sxs-lookup"><span data-stu-id="6bc9d-110">Simplifying your build process by compiling a single project rather than compiling multiple projects, each targeting a different .NET Framework version or platform.</span></span>
  - <span data-ttu-id="6bc9d-111">Tek bir proje dosyasını yönetmeniz gerektiğinden, çok hedefli projeler için kaynak dosya yönetimini basitleştirecek.</span><span class="sxs-lookup"><span data-stu-id="6bc9d-111">Simplifying source file management for multi-targeted projects because you must manage a single project file.</span></span> <span data-ttu-id="6bc9d-112">Kaynak dosyaları eklendiğinde/kaldırırken, alternatifler bunları diğer projelerinizle el ile eşitlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6bc9d-112">When adding/removing source files, the alternatives require you to manually sync these with your other projects.</span></span>
  - <span data-ttu-id="6bc9d-113">Tüketim için kolayca bir NuGet paketi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="6bc9d-113">Easily generating a NuGet package for consumption.</span></span>
  - <span data-ttu-id="6bc9d-114">Derleyici yönergelerinin kullanımı aracılığıyla kitaplıklarınızdaki belirli bir .NET Framework sürümü için kod yazmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="6bc9d-114">Allows you to write code for a specific .NET Framework version in your libraries through the use of compiler directives.</span></span>

  <span data-ttu-id="6bc9d-115">*Desteklenmeyen senaryolar:*</span><span class="sxs-lookup"><span data-stu-id="6bc9d-115">*Unsupported scenarios:*</span></span>
  - <span data-ttu-id="6bc9d-116">Geliştiricilerin mevcut projeleri açmak için Visual Studio 2017 kullanmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="6bc9d-116">Requires developers to use Visual Studio 2017 to open existing projects.</span></span> <span data-ttu-id="6bc9d-117">Visual Studio 'nun eski sürümlerini desteklemek için, [Proje dosyalarınızın farklı klasörlerde tutulması](#support-vs) daha iyi bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="6bc9d-117">To support older versions of Visual Studio, [keeping your project files in different folders](#support-vs) is a better option.</span></span>

- <a name="support-vs"></a><span data-ttu-id="6bc9d-118">[**Mevcut projeleri ve yeni .NET Core projelerini ayrı tutun**](#keep-existing-projects-and-create-a-net-core-project)</span><span class="sxs-lookup"><span data-stu-id="6bc9d-118">[**Keep existing projects and new .NET Core projects separate**](#keep-existing-projects-and-create-a-net-core-project)</span></span>

  <span data-ttu-id="6bc9d-119">*Bunun için uygun olan şey:*</span><span class="sxs-lookup"><span data-stu-id="6bc9d-119">*What this is good for:*</span></span>
  - <span data-ttu-id="6bc9d-120">Visual Studio 2017 olmayan geliştiriciler/katkıda bulunanlar için yükseltme yapmak zorunda kalmadan mevcut projelerde geliştirmeyi desteklemeye devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6bc9d-120">Continuing to support development on existing projects without having to upgrade for developers/contributors who may not have Visual Studio 2017.</span></span>
  - <span data-ttu-id="6bc9d-121">Mevcut projelerde yeni hatalar oluşturma olasılığını azaltmak, çünkü bu projelerde hiçbir kod karmaşıklığı gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="6bc9d-121">Decreasing the possibility of creating new bugs in existing projects because no code churn is required in those projects.</span></span>

## <a name="example"></a><span data-ttu-id="6bc9d-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="6bc9d-122">Example</span></span>

<span data-ttu-id="6bc9d-123">Aşağıdaki depoyu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="6bc9d-123">Consider the repository below:</span></span>

![Mevcut proje](./media/project-structure/existing-project-structure.png)

[<span data-ttu-id="6bc9d-125">**Kaynak kodu**</span><span class="sxs-lookup"><span data-stu-id="6bc9d-125">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/)

<span data-ttu-id="6bc9d-126">Aşağıda, mevcut projelerin kısıtlamalarına ve karmaşıklığına bağlı olarak bu depoya yönelik .NET Core desteği eklemenin çeşitli yolları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6bc9d-126">The following describes several ways to add support for .NET Core for this repository depending on the constraints and complexity of the existing projects.</span></span>

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a><span data-ttu-id="6bc9d-127">Mevcut projeleri çok hedefli bir .NET Core projesiyle değiştirme</span><span class="sxs-lookup"><span data-stu-id="6bc9d-127">Replace existing projects with a multi-targeted .NET Core project</span></span>

<span data-ttu-id="6bc9d-128">Mevcut *\*. csproj* dosyalarının kaldırılması ve birden çok çerçeveyi hedefleyen tek bir *\*. csproj* dosyası oluşturulması için depoyu yeniden düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="6bc9d-128">Reorganize the repository so that any existing *\*.csproj* files are removed and a single *\*.csproj* file is created that targets multiple frameworks.</span></span> <span data-ttu-id="6bc9d-129">Tek bir proje farklı çerçeveler için derleyebildiğinden bu harika bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="6bc9d-129">This is a great option because a single project is able to compile for different frameworks.</span></span> <span data-ttu-id="6bc9d-130">Ayrıca hedeflenen çerçeveye göre farklı derleme seçeneklerini ve bağımlılıklarını işlemek için de güç vardır.</span><span class="sxs-lookup"><span data-stu-id="6bc9d-130">It also has the power to handle different compilation options and dependencies per targeted framework.</span></span>

![Birden çok çerçeveyi hedefleyen bir csproj oluşturma](./media/project-structure/multi-targeted-project.png)

[<span data-ttu-id="6bc9d-132">**Kaynak kodu**</span><span class="sxs-lookup"><span data-stu-id="6bc9d-132">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/)

<span data-ttu-id="6bc9d-133">Notda yapılan değişiklikler:</span><span class="sxs-lookup"><span data-stu-id="6bc9d-133">Changes to note are:</span></span>

- <span data-ttu-id="6bc9d-134">*Packages. config* ve *\*. csproj* sürümlerini yeni bir [.NET Core *\*. csproj*](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj)ile değiştirme.</span><span class="sxs-lookup"><span data-stu-id="6bc9d-134">Replacement of *packages.config* and *\*.csproj* with a new [.NET Core *\*.csproj*](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj).</span></span> <span data-ttu-id="6bc9d-135">NuGet paketleri `<PackageReference> ItemGroup` ile belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6bc9d-135">NuGet packages are specified with `<PackageReference> ItemGroup`.</span></span>

## <a name="keep-existing-projects-and-create-a-net-core-project"></a><span data-ttu-id="6bc9d-136">Mevcut projeleri tut ve bir .NET Core projesi oluştur</span><span class="sxs-lookup"><span data-stu-id="6bc9d-136">Keep existing projects and create a .NET Core project</span></span>

<span data-ttu-id="6bc9d-137">Eski çerçeveleri hedefleyen mevcut projeler varsa, bu projeleri dokunmadan bırakmak ve gelecekteki çerçeveleri hedeflemek için bir .NET Core projesi kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6bc9d-137">If there are existing projects that target older frameworks, you may want to leave these projects untouched and use a .NET Core project to target future frameworks.</span></span>

![Farklı klasördeki mevcut projeyi içeren .NET Core projesi](./media/project-structure/separate-projects-same-source.png)

[<span data-ttu-id="6bc9d-139">**Kaynak kodu**</span><span class="sxs-lookup"><span data-stu-id="6bc9d-139">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/)

<span data-ttu-id="6bc9d-140">Notda yapılan değişiklikler:</span><span class="sxs-lookup"><span data-stu-id="6bc9d-140">Changes to note are:</span></span>

- <span data-ttu-id="6bc9d-141">.NET Core ve var olan projeler ayrı klasörlerde tutulur.</span><span class="sxs-lookup"><span data-stu-id="6bc9d-141">The .NET Core and existing projects are kept in separate folders.</span></span>
  - <span data-ttu-id="6bc9d-142">Projelerin ayrı klasörlerde tutulması, Visual Studio 2017 veya sonraki sürümlerini yapmanızı zorunlu tutar.</span><span class="sxs-lookup"><span data-stu-id="6bc9d-142">Keeping projects in separate folders avoids forcing you to have Visual Studio 2017 or later versions.</span></span> <span data-ttu-id="6bc9d-143">Yalnızca eski projeleri açan ayrı bir çözüm oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6bc9d-143">You can create a separate solution that only opens the old projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="6bc9d-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6bc9d-144">See also</span></span>

- [<span data-ttu-id="6bc9d-145">.NET Core taşıma belgeleri</span><span class="sxs-lookup"><span data-stu-id="6bc9d-145">.NET Core porting documentation</span></span>](index.md)
