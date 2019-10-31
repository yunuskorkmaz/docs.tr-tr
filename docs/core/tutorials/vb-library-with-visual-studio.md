---
title: Visual Studio 2017 'de Visual Basic .NET Standard sınıf kitaplığı oluşturma
description: Visual Studio 2017 kullanarak Visual Basic yazılmış .NET Standard sınıf kitaplığı oluşturmayı öğrenin
ms.date: 08/07/2017
dev_langs:
- vb
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 1daab377abe3b6b89f73ed48eafadeae4d7eee77
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73100862"
---
# <a name="build-a-net-standard-library-with-visual-basic-and-the-net-core-sdk-in-visual-studio-2017"></a><span data-ttu-id="2d0f7-103">Visual Studio 2017 ' de Visual Basic ve .NET Core SDK ile .NET Standard kitaplığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="2d0f7-103">Build a .NET Standard library with Visual Basic and the .NET Core SDK in Visual Studio 2017</span></span>

<span data-ttu-id="2d0f7-104">Bir *sınıf kitaplığı* , bir uygulama tarafından çağrılan türleri ve yöntemleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-104">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="2d0f7-105">.NET Standard 2,0 ' i hedefleyen bir sınıf kitaplığı, kitaplığınızın bu .NET Standard sürümünü destekleyen tüm .NET uygulamaları tarafından çağrılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-105">A class library that targets the .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of the .NET Standard.</span></span> <span data-ttu-id="2d0f7-106">Sınıf kitaplığınızı bitirdiğinizde, bunu üçüncü taraf bir bileşen olarak dağıtmak mı yoksa bir veya daha fazla uygulamayla paketlenmiş bir bileşen olarak eklemek mi istediğinize karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-106">When you finish your class library, you can decide whether you want to distribute it as a third-party component or whether you want to include it as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="2d0f7-107">.NET Standard sürümlerinin ve destekledikleri platformların bir listesi için bkz. [.NET Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="2d0f7-107">For a list of the .NET Standard versions and the platforms they support, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="2d0f7-108">Bu konu başlığında, tek bir dize işleme yöntemi içeren basit bir yardımcı program kitaplığı oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-108">In this topic, you'll create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="2d0f7-109">Bunu, <xref:System.String> sınıfının bir üyesi gibi çağırabilmeniz için bir [genişletme yöntemi](../../visual-basic/programming-guide/language-features/procedures/extension-methods.md) olarak uygulayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-109">You'll implement it as an [extension method](../../visual-basic/programming-guide/language-features/procedures/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

## <a name="creating-a-class-library-solution"></a><span data-ttu-id="2d0f7-110">Sınıf kitaplığı çözümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="2d0f7-110">Creating a class library solution</span></span>

<span data-ttu-id="2d0f7-111">Sınıf kitaplığı projeniz ve ilgili projeler için bir çözüm oluşturarak başlayın.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-111">Start by creating a solution for your class library project and its related projects.</span></span> <span data-ttu-id="2d0f7-112">Bir Visual Studio çözümü yalnızca bir veya daha fazla proje için kapsayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-112">A Visual Studio Solution just serves as a container for one or more projects.</span></span> <span data-ttu-id="2d0f7-113">Çözümü oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="2d0f7-113">To create the solution:</span></span>

1. <span data-ttu-id="2d0f7-114">Visual Studio menü çubuğunda **dosya** > **Yeni** > **Proje**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-114">On the Visual Studio menu bar, choose **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="2d0f7-115">**Yeni proje** Iletişim kutusunda **diğer proje türleri** düğümünü genişletin ve **Visual Studio çözümleri**' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-115">In the **New Project** dialog, expand the **Other Project Types** node, and select **Visual Studio Solutions**.</span></span> <span data-ttu-id="2d0f7-116">"ClassLibraryProjects" çözümünü adlandırın ve **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-116">Name the solution "ClassLibraryProjects" and select the **OK** button.</span></span>

   ![Visual Studio yeni test projesi oluştur iletişim kutusu](./media/library-with-visual-studio/new-project-dialog.png)

## <a name="creating-the-class-library-project"></a><span data-ttu-id="2d0f7-118">Sınıf kitaplığı projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="2d0f7-118">Creating the class library project</span></span>

<span data-ttu-id="2d0f7-119">Sınıf kitaplığı projenizi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="2d0f7-119">Create your class library project:</span></span>

1. <span data-ttu-id="2d0f7-120">**Çözüm Gezgini**, **classlibraryprojects** çözüm dosyasına sağ tıklayın ve bağlam menüsünden **Yeni proje** > **Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-120">In **Solution Explorer**, right-click on the **ClassLibraryProjects** solution file and from the context menu, select **Add** > **New Project**.</span></span>

1. <span data-ttu-id="2d0f7-121">**Yeni Proje Ekle** iletişim kutusunda **Visual Basic** düğümünü genişletin ve ardından **.NET Standard** düğümünü ve ardından **sınıf kitaplığı (.NET Standard)** proje şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-121">In the **Add New Project** dialog, expand the **Visual Basic** node, then select the **.NET Standard** node followed by the **Class Library (.NET Standard)** project template.</span></span> <span data-ttu-id="2d0f7-122">**Ad** metin kutusuna projenin adı olarak "StringLibrary" yazın.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-122">In the **Name** text box, enter "StringLibrary" as the name of the project.</span></span> <span data-ttu-id="2d0f7-123">Sınıf Kitaplığı projesini oluşturmak için **Tamam ' ı** seçin.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-123">Select **OK** to create the class library project.</span></span>

   ![Visual Studio yeni kitaplık projesi Ekle iletişim kutusu](./media/vb-library-with-visual-studio/create-new-library-project.png)

   <span data-ttu-id="2d0f7-125">Kod penceresi daha sonra Visual Studio geliştirme ortamında açılır.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-125">The code window then opens in the Visual Studio development environment.</span></span> 
 
   ![Varsayılan sınıf kitaplığı şablon kodunu gösteren Visual Studio uygulama penceresi](./media/vb-library-with-visual-studio/visual-studio-library.png)

1. <span data-ttu-id="2d0f7-127">Kitaplığın .NET Standard doğru sürümünü hedeflediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-127">Check to make sure that the library targets the correct version of the .NET Standard.</span></span> <span data-ttu-id="2d0f7-128">**Çözüm Gezgini** penceresinde kitaplık projesine sağ tıklayın ve ardından **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-128">Right-click on the library project in the **Solution Explorer** windows, then select **Properties**.</span></span> <span data-ttu-id="2d0f7-129">**Hedef Framework** metin kutusunda 2,0 .NET Standard hedeflendiğimiz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-129">The **Target Framework** text box shows that we're targeting .NET Standard 2.0.</span></span>

   ![Sınıf kitaplığı için proje özellikleri](./media/library-with-visual-studio/library-project-properties.png)

1. <span data-ttu-id="2d0f7-131">Ayrıca **Özellikler** iletişim kutusunda, **kök ad alanı** metin kutusundaki metni temizleyin.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-131">Also in the **Properties** dialog, clear the text in the **Root namespace** text box.</span></span> <span data-ttu-id="2d0f7-132">Her proje için, Visual Basic otomatik olarak proje adına karşılık gelen bir ad alanı oluşturur ve kaynak kod dosyalarında tanımlanan ad alanları bu ad alanının üstlerdir.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-132">For each project, Visual Basic automatically creates a namespace that corresponds to the project name, and any namespaces defined in source code files are parents of that namespace.</span></span> <span data-ttu-id="2d0f7-133">[`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) anahtar sözcüğünü kullanarak en üst düzey bir ad alanı tanımlamak istiyoruz.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-133">We want to define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword.</span></span>
  
1. <span data-ttu-id="2d0f7-134">Kod penceresindeki kodu aşağıdaki kodla değiştirin ve dosyayı kaydedin:</span><span class="sxs-lookup"><span data-stu-id="2d0f7-134">Replace the code in the code window with the following code and save the file:</span></span>

  [!CODE-vb[ClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   <span data-ttu-id="2d0f7-135">`UtilityLibraries.StringLibrary`sınıf kitaplığı, geçerli dize örneğinin büyük bir karakterle başlayıp başlamadığını belirten bir <xref:System.Boolean> değeri döndüren `StartsWithUpper`adlı bir yöntemi içerir.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-135">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`, which returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="2d0f7-136">Unicode standart, büyük harfli karakterleri küçük harfli karakterlerden ayırır.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-136">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="2d0f7-137"><xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> yöntemi, bir karakter büyük harfle `true` döndürür.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-137">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="2d0f7-138">Menü çubuğunda **derleme** > **Build Solution**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-138">On the menu bar, select **Build** > **Build Solution**.</span></span> <span data-ttu-id="2d0f7-139">Projenin hatasız derlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-139">The project should compile without error.</span></span>

   ![Yapılandırmanın başarılı olduğunu gösteren çıkış bölmesi](./media/library-with-visual-studio/output-pane-successful-build.png)

## <a name="next-step"></a><span data-ttu-id="2d0f7-141">Sonraki adım</span><span class="sxs-lookup"><span data-stu-id="2d0f7-141">Next step</span></span>

<span data-ttu-id="2d0f7-142">Kitaplığı başarıyla derlediniz.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-142">You've successfully built the library.</span></span> <span data-ttu-id="2d0f7-143">Yöntemlerinden herhangi birini çağırmadığınız için, beklendiği gibi çalışıp çalışmadığını bilemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-143">Because you haven't called any of its methods, you don't know whether it works as expected.</span></span> <span data-ttu-id="2d0f7-144">Kitaplığınızı geliştirmedeki bir sonraki adım, bir [birim testi projesi](testing-library-with-visual-studio.md)kullanarak test kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-144">The next step in developing your library is to test it by using a [Unit Test Project](testing-library-with-visual-studio.md).</span></span>
