---
title: .NET Framework ve .NET Core için projeler düzenleyin
description: Çözümlerini .NET Framework ve .NET Core'a karşı yan yana derlemek isteyen proje sahiplerine yardımcı olun.
author: conniey
ms.date: 12/07/2018
ms.openlocfilehash: d71cc3102846c08f4e35831921b8cc4ca82f9e1b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75777328"
---
# <a name="organize-your-project-to-support-both-net-framework-and-net-core"></a><span data-ttu-id="b7496-103">Projenizi hem .NET Framework hem de .NET Core'u destekleyecek şekilde düzenleyin</span><span class="sxs-lookup"><span data-stu-id="b7496-103">Organize your project to support both .NET Framework and .NET Core</span></span>

<span data-ttu-id="b7496-104">Hem .NET Framework hem de .NET Core için yan yana derleyen bir çözüm oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7496-104">You can create a solution that compiles for both .NET Framework and .NET Core side-by-side.</span></span> <span data-ttu-id="b7496-105">Bu makalede, bu hedefe ulaşmanıza yardımcı olmak için çeşitli proje organizasyonu seçenekleri kapsar.</span><span class="sxs-lookup"><span data-stu-id="b7496-105">This article covers several project-organization options to help you achieve this goal.</span></span> <span data-ttu-id="b7496-106">Proje düzeninizi .NET Core ile nasıl ayarladığınıza karar verirken göz önünde bulundurmanız gereken bazı tipik senaryolar aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b7496-106">Here are some typical scenarios to consider when you're deciding how to set up your project layout with .NET Core.</span></span> <span data-ttu-id="b7496-107">Liste istediğiniz her şeyi kapsamayabilir; projenizin ihtiyaçlarına göre öncelik belirleyin.</span><span class="sxs-lookup"><span data-stu-id="b7496-107">The list may not cover everything you want; prioritize based on your project's needs.</span></span>

- [<span data-ttu-id="b7496-108">**Mevcut projeleri ve .NET Core projelerini tek projelerde birleştirin**</span><span class="sxs-lookup"><span data-stu-id="b7496-108">**Combine existing projects and .NET Core projects into single projects**</span></span>](#replace-existing-projects-with-a-multi-targeted-net-core-project)

  <span data-ttu-id="b7496-109">*Bu ne için iyidir:*</span><span class="sxs-lookup"><span data-stu-id="b7496-109">*What this is good for:*</span></span>
  - <span data-ttu-id="b7496-110">Her biri farklı bir .NET Framework sürümünü veya platformunu hedefleyen birden çok proje yerine tek bir proje derleyerek yapı işleminizi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="b7496-110">Simplifies your build process by compiling a single project rather than multiple projects that each target a different .NET Framework version or platform.</span></span>
  - <span data-ttu-id="b7496-111">Tek bir proje dosyalarını yönetmeniz gerektiğinden, çok hedefli projeler için kaynak dosya yönetimini basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="b7496-111">Simplifies source file management for multi-targeted projects because you must manage a single project file.</span></span> <span data-ttu-id="b7496-112">Kaynak dosyaları eklerken veya kaldırırken, alternatifler bunları diğer projelerinizle el ile eşitlemenizi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b7496-112">When adding or removing source files, the alternatives require you to manually sync these with your other projects.</span></span>
  - <span data-ttu-id="b7496-113">Kolayca tüketim için bir NuGet paketi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b7496-113">Easily generate a NuGet package for consumption.</span></span>
  - <span data-ttu-id="b7496-114">Derleyici yönergeleri ni kullanarak kitaplıklarınızda belirli bir .NET Framework sürümü için kod yazmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b7496-114">Allows you to write code for a specific .NET Framework version in your libraries through the use of compiler directives.</span></span>

  <span data-ttu-id="b7496-115">*Desteklenmeyen senaryolar:*</span><span class="sxs-lookup"><span data-stu-id="b7496-115">*Unsupported scenarios:*</span></span>
  - <span data-ttu-id="b7496-116">Geliştiricilerin mevcut projeleri açmak için Visual Studio 2017 veya sonraki bir sürümü kullanmalarını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b7496-116">Requires developers to use Visual Studio 2017 or a later version to open existing projects.</span></span> <span data-ttu-id="b7496-117">Visual Studio'nun eski sürümlerini desteklemek için [proje dosyalarınızı farklı klasörlerde tutmak](#support-vs) daha iyi bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="b7496-117">To support older versions of Visual Studio, [keeping your project files in different folders](#support-vs) is a better option.</span></span>

- <a name="support-vs"></a><span data-ttu-id="b7496-118">[**Mevcut projeleri ve yeni .NET Core projelerini ayrı tutun**](#keep-existing-projects-and-create-a-net-core-project)</span><span class="sxs-lookup"><span data-stu-id="b7496-118">[**Keep existing projects and new .NET Core projects separate**](#keep-existing-projects-and-create-a-net-core-project)</span></span>

  <span data-ttu-id="b7496-119">*Bu ne için iyidir:*</span><span class="sxs-lookup"><span data-stu-id="b7496-119">*What this is good for:*</span></span>
  - <span data-ttu-id="b7496-120">Visual Studio 2017 veya daha sonraki sürümü olmayan geliştiriciler ve katkıda bulunanlar için mevcut projelerin geliştirilmesini destekler.</span><span class="sxs-lookup"><span data-stu-id="b7496-120">Supports development on existing projects for developers and contributors who may not have Visual Studio 2017 or a later version.</span></span>
  - <span data-ttu-id="b7496-121">Bu projelerde kod karmaşası gerekmediği için varolan projelerde yeni hata oluşturma olasılığını azaltır.</span><span class="sxs-lookup"><span data-stu-id="b7496-121">Decreases the possibility of creating new bugs in existing projects because no code churn is required in those projects.</span></span>

## <a name="example"></a><span data-ttu-id="b7496-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="b7496-122">Example</span></span>

<span data-ttu-id="b7496-123">Aşağıdaki depoyu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="b7496-123">Consider the repository below:</span></span>

![Mevcut proje](./media/project-structure/existing-project-structure.png)

[<span data-ttu-id="b7496-125">**Kaynak Kodu**</span><span class="sxs-lookup"><span data-stu-id="b7496-125">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/)

<span data-ttu-id="b7496-126">Aşağıdaki, varolan projelerin kısıtlamalarına ve karmaşıklığına bağlı olarak bu depo için .NET Core için destek eklemenin çeşitli yollarını açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="b7496-126">The following describes several ways to add support for .NET Core for this repository depending on the constraints and complexity of the existing projects.</span></span>

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a><span data-ttu-id="b7496-127">Varolan projeleri çok hedefli bir .NET Core projesiyle değiştirme</span><span class="sxs-lookup"><span data-stu-id="b7496-127">Replace existing projects with a multi-targeted .NET Core project</span></span>

<span data-ttu-id="b7496-128">Depoyu, varolan \* \*.csproj\* dosyalarının kaldırılacak şekilde yeniden düzenleyin ve birden çok çerçeveyi hedefleyen tek \* \*bir .csproj\* dosyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b7496-128">Reorganize the repository so that any existing *\*.csproj* files are removed and a single *\*.csproj* file is created that targets multiple frameworks.</span></span> <span data-ttu-id="b7496-129">Tek bir proje farklı çerçeveler için derlemek mümkün olduğundan, bu harika bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="b7496-129">This is a great option, because a single project is able to compile for different frameworks.</span></span> <span data-ttu-id="b7496-130">Ayrıca, hedeflenen çerçeve başına farklı derleme seçeneklerini ve bağımlılıkları işleme gücüne de sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b7496-130">It also has the power to handle different compilation options and dependencies per targeted framework.</span></span>

![Birden çok çerçeveyi hedefleyen bir csproj oluşturma](./media/project-structure/multi-targeted-project.png)

[<span data-ttu-id="b7496-132">**Kaynak Kodu**</span><span class="sxs-lookup"><span data-stu-id="b7496-132">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/)

<span data-ttu-id="b7496-133">Not değişiklikleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b7496-133">Changes to note are:</span></span>

- <span data-ttu-id="b7496-134">*Packages.config* ve \* \*.csproj'un\* yeni bir [.NET Core \* \*.csproj\*](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj)ile değiştirilmesi.</span><span class="sxs-lookup"><span data-stu-id="b7496-134">Replacement of *packages.config* and *\*.csproj* with a new [.NET Core *\*.csproj*](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj).</span></span> <span data-ttu-id="b7496-135">NuGet paketleri ile `<PackageReference> ItemGroup`belirtilir.</span><span class="sxs-lookup"><span data-stu-id="b7496-135">NuGet packages are specified with `<PackageReference> ItemGroup`.</span></span>

## <a name="keep-existing-projects-and-create-a-net-core-project"></a><span data-ttu-id="b7496-136">Varolan projeleri koruyun ve bir .NET Core projesi oluşturun</span><span class="sxs-lookup"><span data-stu-id="b7496-136">Keep existing projects and create a .NET Core project</span></span>

<span data-ttu-id="b7496-137">Eski çerçeveleri hedefleyen varolan projeler varsa, bu projeleri el değmemiş olarak bırakmak ve gelecekteki çerçeveleri hedeflemek için bir .NET Core projesi kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7496-137">If there are existing projects that target older frameworks, you may want to leave these projects untouched and use a .NET Core project to target future frameworks.</span></span>

![.NET Core projesi farklı klasörde mevcut proje ile](./media/project-structure/separate-projects-same-source.png)

[<span data-ttu-id="b7496-139">**Kaynak Kodu**</span><span class="sxs-lookup"><span data-stu-id="b7496-139">**Source Code**</span></span>](https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/)

<span data-ttu-id="b7496-140">.NET Core ve varolan projeler ayrı klasörlerde tutulur.</span><span class="sxs-lookup"><span data-stu-id="b7496-140">The .NET Core and existing projects are kept in separate folders.</span></span> <span data-ttu-id="b7496-141">Projeleri ayrı klasörlerde tutmak, Visual Studio 2017 veya sonraki sürümlerine sahip olmaya zorlamanızı önler.</span><span class="sxs-lookup"><span data-stu-id="b7496-141">Keeping projects in separate folders avoids forcing you to have Visual Studio 2017 or later versions.</span></span> <span data-ttu-id="b7496-142">Yalnızca eski projeleri açan ayrı bir çözüm oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7496-142">You can create a separate solution that only opens the old projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="b7496-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7496-143">See also</span></span>

- [<span data-ttu-id="b7496-144">.NET Çekirdek taşıma belgeleri</span><span class="sxs-lookup"><span data-stu-id="b7496-144">.NET Core porting documentation</span></span>](index.md)
