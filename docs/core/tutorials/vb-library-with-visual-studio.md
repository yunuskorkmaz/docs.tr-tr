---
title: "Visual Basic ve Visual Studio 2017 .NET çekirdek ile bir sınıf kitaplığı oluşturma"
description: "Visual Studio 2017 kullanarak Visual Basic'te yazılmış bir sınıf kitaplığı oluşturmayı öğrenin"
keywords: ".NET core, .NET standart kitaplığı, Visual Studio 2017, Visual Basic sınıfı"
author: rpetrusha
ms.author: ronpet
ms.date: 08/07/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-vb
dev_langs:
- vb
ms.workload:
- dotnetcore
ms.openlocfilehash: b8d87e3a97e2ffeb8e8712bfa5d178bb855f402d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="building-a-class-library-with-visual-basic-and-net-core-in-visual-studio-2017"></a><span data-ttu-id="d0a3c-104">Visual Basic ve Visual Studio 2017 .NET çekirdek ile bir sınıf kitaplığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="d0a3c-104">Building a class library with Visual Basic and .NET Core in Visual Studio 2017</span></span>

<span data-ttu-id="d0a3c-105">A *sınıf kitaplığı* türleri ve bir uygulama tarafından çağrılan yöntemleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d0a3c-105">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="d0a3c-106">.NET standart 2.0 hedefleyen bir sınıf kitaplığı .NET standart bu sürümünü destekleyen herhangi bir .NET uygulaması tarafından çağrılması için kitaplığınızın sağlar.</span><span class="sxs-lookup"><span data-stu-id="d0a3c-106">A class library that targets the .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of the .NET Standard.</span></span> <span data-ttu-id="d0a3c-107">Sınıf kitaplığı bitirdikten sonra bir üçüncü taraf bileşeni veya bir veya daha fazla uygulama ile birlikte gelen bir bileşeni olarak dahil etmek isteyip istemediğinizi olarak dağıtmak isteyip istemediğinize karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0a3c-107">When you finish your class library, you can decide whether you want to distribute it as a third-party component or whether you want to include it as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="d0a3c-108">.NET standart sürümleri ve desteklenen platformlar listesi için bkz: [.NET standart](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="d0a3c-108">For a list of the .NET Standard versions and the platforms they support, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="d0a3c-109">Bu konuda, tek bir dize işleme yöntemi içeren basit yardımcı programı kitaplığı oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="d0a3c-109">In this topic, you'll create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="d0a3c-110">Olarak uygulamanız bir [genişletme yöntemi](../../visual-basic/programming-guide/language-features/procedures/extension-methods.md) üyesi değilmiş gibi çağırabilirsiniz böylece <xref:System.String> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d0a3c-110">You'll implement it as an [extension method](../../visual-basic/programming-guide/language-features/procedures/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

## <a name="creating-a-class-library-solution"></a><span data-ttu-id="d0a3c-111">Bir sınıf kitaplığı çözümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="d0a3c-111">Creating a class library solution</span></span>

<span data-ttu-id="d0a3c-112">Sınıf kitaplığı projenizin ve ilgili projeleri için bir çözüm oluşturmaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="d0a3c-112">Start by creating a solution for your class library project and its related projects.</span></span> <span data-ttu-id="d0a3c-113">Visual Studio çözümü, yalnızca bir veya daha fazla projeleri için bir kapsayıcı olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="d0a3c-113">A Visual Studio Solution just serves as a container for one or more projects.</span></span> <span data-ttu-id="d0a3c-114">Çözüm oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="d0a3c-114">To create the solution:</span></span>

1. <span data-ttu-id="d0a3c-115">Visual Studio menü çubuğunda seçin **dosya** > **yeni** > **proje**.</span><span class="sxs-lookup"><span data-stu-id="d0a3c-115">On the Visual Studio menu bar, choose **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="d0a3c-116">İçinde **yeni proje** iletişim kutusunda, genişletin **diğer proje türleri** düğümü ve select **Visual Studio çözümleri**.</span><span class="sxs-lookup"><span data-stu-id="d0a3c-116">In the **New Project** dialog, expand the **Other Project Types** node, and select **Visual Studio Solutions**.</span></span> <span data-ttu-id="d0a3c-117">"ClassLibraryProjects" Çözüm adı ve seçin **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="d0a3c-117">Name the solution "ClassLibraryProjects" and select the **OK** button.</span></span>

   ![Yeni Proje iletişim kutusu](./media/library-with-visual-studio/newproject.png)

## <a name="creating-the-class-library-project"></a><span data-ttu-id="d0a3c-119">Sınıf kitaplığı projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="d0a3c-119">Creating the class library project</span></span>

<span data-ttu-id="d0a3c-120">Sınıf kitaplığı projenizin oluşturun:</span><span class="sxs-lookup"><span data-stu-id="d0a3c-120">Create your class library project:</span></span>

1. <span data-ttu-id="d0a3c-121">İçinde **Çözüm Gezgini**, sağ tıklayın **ClassLibraryProjects** çözüm dosya ve bağlam menüsünden seçin **Ekle** > **yeni Proje**.</span><span class="sxs-lookup"><span data-stu-id="d0a3c-121">In **Solution Explorer**, right-click on the **ClassLibraryProjects** solution file and from the context menu, select **Add** > **New Project**.</span></span>

1. <span data-ttu-id="d0a3c-122">İçinde **Yeni Proje Ekle** iletişim kutusunda, genişletin **Visual Basic** düğümünü, ardından **.NET standart** düğümünü ve ardından **sınıf kitaplığı (.NET standart)**  proje şablonu.</span><span class="sxs-lookup"><span data-stu-id="d0a3c-122">In the **Add New Project** dialog, expand the **Visual Basic** node, then select the **.NET Standard** node followed by the **Class Library (.NET Standard)** project template.</span></span> <span data-ttu-id="d0a3c-123">İçinde **adı** metin kutusunda, "StringLibrary" projesinin adı girin.</span><span class="sxs-lookup"><span data-stu-id="d0a3c-123">In the **Name** text box, enter "StringLibrary" as the name of the project.</span></span> <span data-ttu-id="d0a3c-124">Seçin **Tamam** sınıf kitaplığı proje oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="d0a3c-124">Select **OK** to create the class library project.</span></span>

   ![Yeni Proje iletişim kutusu ekleme](./media/vb-library-with-visual-studio/libproject.png)

   <span data-ttu-id="d0a3c-126">Kod penceresi ardından Visual Studio geliştirme ortamında açar.</span><span class="sxs-lookup"><span data-stu-id="d0a3c-126">The code window then opens in the Visual Studio development environment.</span></span> 
 
   ![Visual Studio uygulama penceresi varsayılan sınıf kitaplığı şablonu kodu gösterme](./media/vb-library-with-visual-studio/stringlibrary.png)

1. <span data-ttu-id="d0a3c-128">Kitaplığı .NET standart doğru sürümü hedefleyen emin olmak için kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="d0a3c-128">Check to make sure that the library targets the correct version of the .NET Standard.</span></span> <span data-ttu-id="d0a3c-129">Kitaplık projeye sağ tıklayın **Çözüm Gezgini** windows, ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="d0a3c-129">Right-click on the library project in the **Solution Explorer** windows, then select **Properties**.</span></span> <span data-ttu-id="d0a3c-130">**Hedef Framework** metin kutusu gösterir biz .NET standart 2.0 hedefleme.</span><span class="sxs-lookup"><span data-stu-id="d0a3c-130">The **Target Framework** text box shows that we're targeting .NET Standard 2.0.</span></span>

   ![Sınıf kitaplığı proje özellikleri](./media/library-with-visual-studio/properties.png)

1. <span data-ttu-id="d0a3c-132">De **özellikleri** iletişim kutusunda, metin temizleyin **kök ad alanı** metin kutusu.</span><span class="sxs-lookup"><span data-stu-id="d0a3c-132">Also in the **Properties** dialog, clear the text in the **Root namespace** text box.</span></span> <span data-ttu-id="d0a3c-133">Her proje için Visual Basic proje adına karşılık gelen bir ad alanı otomatik olarak oluşturur ve bu ad alanının üst kaynak kodu dosyaları içinde tanımlanan tüm ad alanlarını şunlardır.</span><span class="sxs-lookup"><span data-stu-id="d0a3c-133">For each project, Visual Basic automatically creates a namespace that corresponds to the project name, and any namespaces defined in source code files are parents of that namespace.</span></span> <span data-ttu-id="d0a3c-134">En üst düzey bir ad kullanarak tanımlamak istiyoruz [ `namespace` ](../../visual-basic/language-reference/statements/namespace-statement.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="d0a3c-134">We want to define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword.</span></span>
  
1. <span data-ttu-id="d0a3c-135">Kod penceresinde kodu aşağıdaki kodla değiştirin ve dosyayı kaydedin:</span><span class="sxs-lookup"><span data-stu-id="d0a3c-135">Replace the code in the code window with the following code and save the file:</span></span>

  [!CODE-vb[ClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   <span data-ttu-id="d0a3c-136">Sınıf Kitaplığı `UtilityLibraries.StringLibrary`, adlandırılmış bir yöntem içerir `StartsWithUpper`, döndüren bir <xref:System.Boolean> geçerli dize örneği bir büyük harf karakter ile başlayan olup olmadığını belirten değer.</span><span class="sxs-lookup"><span data-stu-id="d0a3c-136">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`, which returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="d0a3c-137">Unicode standart büyük harfli karakterler, küçük harfli karakterlerden ayırır.</span><span class="sxs-lookup"><span data-stu-id="d0a3c-137">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="d0a3c-138"><xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> Yöntemi döndürür `true` bir karakter büyük harf ise.</span><span class="sxs-lookup"><span data-stu-id="d0a3c-138">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="d0a3c-139">Menü çubuğunda seçin **yapı** > **yapı çözümü**.</span><span class="sxs-lookup"><span data-stu-id="d0a3c-139">On the menu bar, select **Build** > **Build Solution**.</span></span> <span data-ttu-id="d0a3c-140">Proje derleme hatası.</span><span class="sxs-lookup"><span data-stu-id="d0a3c-140">The project should compile without error.</span></span>

   ![Yapı başarılı olduğunu gösteren çıkış bölmesi](./media/library-with-visual-studio/buildsucceeds.png)



## <a name="next-step"></a><span data-ttu-id="d0a3c-142">Sonraki adım</span><span class="sxs-lookup"><span data-stu-id="d0a3c-142">Next step</span></span>

<span data-ttu-id="d0a3c-143">Kitaplık başarıyla temel aldık.</span><span class="sxs-lookup"><span data-stu-id="d0a3c-143">You've successfully built the library.</span></span> <span data-ttu-id="d0a3c-144">Yöntemlerinden herhangi biri adlı henüz olduğundan, beklendiği gibi çalışıp çalışmadığını bilinmiyor.</span><span class="sxs-lookup"><span data-stu-id="d0a3c-144">Because you haven't called any of its methods, you don't know whether it works as expected.</span></span> <span data-ttu-id="d0a3c-145">Kitaplığınızı geliştirme sonraki adım kullanarak test etmektir bir [birim testi projesi](testing-library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="d0a3c-145">The next step in developing your library is to test it by using a [Unit Test Project](testing-library-with-visual-studio.md).</span></span>
