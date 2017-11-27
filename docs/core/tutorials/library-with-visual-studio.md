---
title: "C# ve Visual Studio 2017 .NET çekirdek ile .NET standart bir sınıf kitaplığı oluşturma"
description: "Visual Studio 2017 kullanarak C# içinde yazılmış .NET standart bir sınıf kitaplığı oluşturmayı öğrenin."
keywords: ".NET core, Visual Studio 2017 .NET standart sınıf kitaplığı"
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: c849ca26-6a25-4d35-9544-f343af88e0e7
ms.openlocfilehash: 5806e3e71eabbc1d65ecffed72108ba548b57806
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="building-a-class-library-with-c-and-net-core-in-visual-studio-2017"></a><span data-ttu-id="ef8aa-104">C# ve Visual Studio 2017 .NET çekirdek sınıf kitaplığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="ef8aa-104">Building a class library with C# and .NET Core in Visual Studio 2017</span></span>

<span data-ttu-id="ef8aa-105">A *sınıf kitaplığı* türleri ve bir uygulama tarafından çağrılan yöntemleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ef8aa-105">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="ef8aa-106">.NET standart 2.0 hedefleyen bir sınıf kitaplığı .NET standart bu sürümünü destekleyen herhangi bir .NET uygulaması tarafından çağrılması için kitaplığınızın sağlar.</span><span class="sxs-lookup"><span data-stu-id="ef8aa-106">A class library that targets the .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of the .NET Standard.</span></span> <span data-ttu-id="ef8aa-107">Sınıf kitaplığı bitirdikten sonra bir üçüncü taraf bileşeni veya bir veya daha fazla uygulama ile birlikte gelen bir bileşeni olarak dahil etmek isteyip istemediğinizi olarak dağıtmak isteyip istemediğinize karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef8aa-107">When you finish your class library, you can decide whether you want to distribute it as a third-party component or whether you want to include it as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="ef8aa-108">.NET standart sürümleri ve desteklenen platformlar listesi için bkz: [.NET standart](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="ef8aa-108">For a list of the .NET Standard versions and the platforms they support, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="ef8aa-109">Bu konuda, tek bir dize işleme yöntemi içeren basit yardımcı programı kitaplığı oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="ef8aa-109">In this topic, you'll create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="ef8aa-110">Olarak uygulamanız bir [genişletme yöntemi](../../csharp/programming-guide/classes-and-structs/extension-methods.md) üyesi değilmiş gibi çağırabilirsiniz böylece <xref:System.String> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ef8aa-110">You'll implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

## <a name="creating-a-class-library-solution"></a><span data-ttu-id="ef8aa-111">Bir sınıf kitaplığı çözümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="ef8aa-111">Creating a class library solution</span></span>

<span data-ttu-id="ef8aa-112">Sınıf kitaplığı projenizin ve ilgili projeleri için bir çözüm oluşturmaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="ef8aa-112">Start by creating a solution for your class library project and its related projects.</span></span> <span data-ttu-id="ef8aa-113">Visual Studio çözümü, yalnızca bir veya daha fazla projeleri için bir kapsayıcı olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="ef8aa-113">A Visual Studio Solution just serves as a container for one or more projects.</span></span> <span data-ttu-id="ef8aa-114">Çözüm oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="ef8aa-114">To create the solution:</span></span>

1. <span data-ttu-id="ef8aa-115">Visual Studio menü çubuğunda seçin **dosya** > **yeni** > **proje**.</span><span class="sxs-lookup"><span data-stu-id="ef8aa-115">On the Visual Studio menu bar, choose **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="ef8aa-116">İçinde **yeni proje** iletişim kutusunda, genişletin **diğer proje türleri** düğümü ve select **Visual Studio çözümleri**.</span><span class="sxs-lookup"><span data-stu-id="ef8aa-116">In the **New Project** dialog, expand the **Other Project Types** node, and select **Visual Studio Solutions**.</span></span> <span data-ttu-id="ef8aa-117">"ClassLibraryProjects" Çözüm adı ve seçin **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="ef8aa-117">Name the solution "ClassLibraryProjects" and select the **OK** button.</span></span>

   ![Yeni Proje iletişim kutusu](./media/library-with-visual-studio/newproject.png)

## <a name="creating-the-class-library-project"></a><span data-ttu-id="ef8aa-119">Sınıf kitaplığı projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="ef8aa-119">Creating the class library project</span></span>

<span data-ttu-id="ef8aa-120">Sınıf kitaplığı projenizin oluşturun:</span><span class="sxs-lookup"><span data-stu-id="ef8aa-120">Create your class library project:</span></span>

1. <span data-ttu-id="ef8aa-121">İçinde **Çözüm Gezgini**, sağ tıklayın **ClassLibraryProjects** çözüm dosya ve bağlam menüsünden seçin **Ekle** > **yeni Proje**.</span><span class="sxs-lookup"><span data-stu-id="ef8aa-121">In **Solution Explorer**, right-click on the **ClassLibraryProjects** solution file and from the context menu, select **Add** > **New Project**.</span></span>

1. <span data-ttu-id="ef8aa-122">İçinde **Yeni Proje Ekle** iletişim kutusunda, genişletin **Visual C#** düğümünü, ardından **.NET standart** düğümünü ve ardından **(.NET standart)sınıfkitaplığı** proje şablonu.</span><span class="sxs-lookup"><span data-stu-id="ef8aa-122">In the **Add New Project** dialog, expand the **Visual C#** node, then select the **.NET Standard** node followed by the **Class Library (.NET Standard)** project template.</span></span> <span data-ttu-id="ef8aa-123">İçinde **adı** metin kutusunda, "StringLibrary" projesinin adı girin.</span><span class="sxs-lookup"><span data-stu-id="ef8aa-123">In the **Name** text box, enter "StringLibrary" as the name of the project.</span></span> <span data-ttu-id="ef8aa-124">Seçin **Tamam** sınıf kitaplığı proje oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="ef8aa-124">Select **OK** to create the class library project.</span></span>

   ![Yeni Proje iletişim kutusu ekleme](./media/library-with-visual-studio/libproject.png)

   <span data-ttu-id="ef8aa-126">Kod penceresi ardından Visual Studio geliştirme ortamında açar.</span><span class="sxs-lookup"><span data-stu-id="ef8aa-126">The code window then opens in the Visual Studio development environment.</span></span>

   ![Visual Studio uygulama penceresi varsayılan sınıf kitaplığı şablonu kodu gösterme](./media/library-with-visual-studio/stringlibrary.png)

1. <span data-ttu-id="ef8aa-128">Bizim kitaplığı .NET standart doğru sürümü hedefleyen emin olmak için kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="ef8aa-128">Check to make sure that our library targets the correct version of the .NET Standard.</span></span> <span data-ttu-id="ef8aa-129">Kitaplık projeye sağ tıklayın **Çözüm Gezgini** windows, ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="ef8aa-129">Right-click on the library project in the **Solution Explorer** windows, then select **Properties**.</span></span> <span data-ttu-id="ef8aa-130">**Hedef Framework** metin kutusu gösterir biz .NET standart 2.0 hedefleme.</span><span class="sxs-lookup"><span data-stu-id="ef8aa-130">The **Target Framework** text box shows that we're targeting .NET Standard 2.0.</span></span>

   ![Sınıf kitaplığı proje özellikleri](./media/library-with-visual-studio/properties.png)

1. <span data-ttu-id="ef8aa-132">Kod penceresinde kodu aşağıdaki kodla değiştirin ve dosyayı kaydedin:</span><span class="sxs-lookup"><span data-stu-id="ef8aa-132">Replace the code in the code window with the following code and save the file:</span></span>

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]

   <span data-ttu-id="ef8aa-133">Sınıf Kitaplığı `UtilityLibraries.StringLibrary`, adlandırılmış bir yöntem içerir `StartsWithUpper`, döndüren bir <xref:System.Boolean> geçerli dize örneği bir büyük harf karakter ile başlayan olup olmadığını belirten değer.</span><span class="sxs-lookup"><span data-stu-id="ef8aa-133">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`, which returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="ef8aa-134">Unicode standart büyük harfli karakterler, küçük harfli karakterlerden ayırır.</span><span class="sxs-lookup"><span data-stu-id="ef8aa-134">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="ef8aa-135"><xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> Yöntemi döndürür `true` bir karakter büyük harf ise.</span><span class="sxs-lookup"><span data-stu-id="ef8aa-135">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="ef8aa-136">Menü çubuğunda seçin **yapı** > **yapı çözümü**.</span><span class="sxs-lookup"><span data-stu-id="ef8aa-136">On the menu bar, select **Build** > **Build Solution**.</span></span> <span data-ttu-id="ef8aa-137">Proje derleme hatası.</span><span class="sxs-lookup"><span data-stu-id="ef8aa-137">The project should compile without error.</span></span>

   ![Yapı başarılı olduğunu gösteren çıkış bölmesi](./media/library-with-visual-studio/buildsucceeds.png)

## <a name="next-step"></a><span data-ttu-id="ef8aa-139">Sonraki adım</span><span class="sxs-lookup"><span data-stu-id="ef8aa-139">Next step</span></span>

<span data-ttu-id="ef8aa-140">Kitaplık başarıyla temel aldık.</span><span class="sxs-lookup"><span data-stu-id="ef8aa-140">You've successfully built the library.</span></span> <span data-ttu-id="ef8aa-141">Yöntemlerinden herhangi biri adlı henüz olduğundan, beklendiği gibi çalışıp çalışmadığını bilinmiyor.</span><span class="sxs-lookup"><span data-stu-id="ef8aa-141">Because you haven't called any of its methods, you don't know whether it works as expected.</span></span> <span data-ttu-id="ef8aa-142">Kitaplığınızı geliştirme sonraki adım kullanarak test etmektir bir [birim testi projesi](testing-library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="ef8aa-142">The next step in developing your library is to test it by using a [Unit Test Project](testing-library-with-visual-studio.md).</span></span>