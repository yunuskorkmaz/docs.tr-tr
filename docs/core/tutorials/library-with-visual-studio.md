---
title: Visual Studio 'da .NET Standard sınıf kitaplığı oluşturma
description: Visual Studio kullanarak .NET Standard sınıf kitaplığı oluşturmayı öğrenin.
ms.date: 05/21/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 2afe11ad75fc36a67efed48d56dbafb11bceaf2a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005297"
---
# <a name="tutorial-create-a-net-standard-library-in-visual-studio"></a><span data-ttu-id="9a6bb-103">Öğretici: Visual Studio 'da .NET Standard kitaplığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="9a6bb-103">Tutorial: Create a .NET Standard library in Visual Studio</span></span>

<span data-ttu-id="9a6bb-104">Bir *sınıf kitaplığı* , bir uygulama tarafından çağrılan türleri ve yöntemleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-104">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="9a6bb-105">.NET Standard 2,0 ' i hedefleyen bir sınıf kitaplığı, kitaplığınızın bu .NET Standard sürümünü destekleyen herhangi bir .NET uygulamasının çağrılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-105">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span> <span data-ttu-id="9a6bb-106">Sınıf kitaplığınızı bitirdiğinizde, bunu üçüncü taraf bir bileşen olarak dağıtmak mı yoksa bir veya daha fazla uygulamayla paketlenmiş bir bileşen olarak eklemek mi istediğinize karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-106">When you finish your class library, you can decide whether you want to distribute it as a third-party component or whether you want to include it as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="9a6bb-107">.NET Standard sürümlerinin ve destekledikleri platformların listesi için bkz. [.NET Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="9a6bb-107">For a list of .NET Standard versions and the platforms they support, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="9a6bb-108">Bu öğreticide, tek bir dize işleme yöntemi içeren basit bir yardımcı program kitaplığı oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-108">In this tutorial, you create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="9a6bb-109">Bunu, sınıfının bir üyesi gibi çağırabilmeniz için bir [genişletme yöntemi](../../csharp/programming-guide/classes-and-structs/extension-methods.md) olarak uygulamalısınız <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="9a6bb-109">You implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9a6bb-110">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="9a6bb-110">Prerequisites</span></span>

- <span data-ttu-id="9a6bb-111">**.NET Core platformlar arası geliştirme** iş yükünün yüklü olduğu [Visual Studio 2019 sürüm 16,6 veya sonraki bir sürüm](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) .</span><span class="sxs-lookup"><span data-stu-id="9a6bb-111">[Visual Studio 2019 version 16.6 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="9a6bb-112">.NET Core 3,1 SDK, bu iş yükünü seçtiğinizde otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-112">.NET Core 3.1 SDK is automatically installed when you select this workload.</span></span>

  <span data-ttu-id="9a6bb-113">Daha fazla bilgi için, [.NET Core SDK](../install/sdk.md?pivots=os-windows) makalesine [Visual Studio ile install](../install/sdk.md?pivots=os-windows#install-with-visual-studio) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-113">For more information, see the [Install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) section on the [Install the .NET Core SDK](../install/sdk.md?pivots=os-windows) article.</span></span>

## <a name="create-a-visual-studio-solution"></a><span data-ttu-id="9a6bb-114">Visual Studio çözümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="9a6bb-114">Create a Visual Studio solution</span></span>

<span data-ttu-id="9a6bb-115">' De Sınıf Kitaplığı projesini yerleştirmek için boş bir çözüm oluşturarak başlayın.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-115">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="9a6bb-116">Visual Studio çözümü bir veya daha fazla proje için kapsayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-116">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="9a6bb-117">Aynı çözüme ek ve ilgili projeler ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-117">You'll add additional, related projects to the same solution.</span></span>

<span data-ttu-id="9a6bb-118">Boş çözümü oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="9a6bb-118">To create the blank solution:</span></span>

1. <span data-ttu-id="9a6bb-119">Visual Studio'yu açın.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-119">Open Visual Studio.</span></span>

2. <span data-ttu-id="9a6bb-120">Başlangıç penceresinde **Yeni proje oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-120">On the start window, choose **Create a new project**.</span></span>

3. <span data-ttu-id="9a6bb-121">**Yeni proje oluştur** sayfasında, arama kutusuna **çözüm** girin.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-121">On the **Create a new project** page, enter **solution** in the search box.</span></span> <span data-ttu-id="9a6bb-122">**Boş çözüm** şablonunu seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-122">Choose the **Blank Solution** template, and then choose **Next**.</span></span>

   ![Visual Studio 'da boş çözüm şablonu](media/library-with-visual-studio/blank-solution.png)

4. <span data-ttu-id="9a6bb-124">**Yeni projenizi yapılandırın** sayfasında, **Proje adı** kutusuna **classlibraryprojects** ' i girin.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-124">On the **Configure your new project** page, enter **ClassLibraryProjects** in the **Project name** box.</span></span> <span data-ttu-id="9a6bb-125">Ardından **Oluştur**’u seçin.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-125">Then choose **Create**.</span></span>

## <a name="create-a-class-library-project"></a><span data-ttu-id="9a6bb-126">Sınıf kitaplığı projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="9a6bb-126">Create a class library project</span></span>

1. <span data-ttu-id="9a6bb-127">Çözüme "StringLibrary" adlı yeni bir .NET Standard sınıf kitaplığı projesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-127">Add a new .NET Standard class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="9a6bb-128">**Çözüm Gezgini** çözüme sağ tıklayın ve **Add**  >  **Yeni proje**Ekle ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-128">Right-click on the solution in **Solution Explorer** and select **Add** > **New Project**.</span></span>

   1. <span data-ttu-id="9a6bb-129">**Yeni Proje Ekle** sayfasında, arama kutusuna **kitaplık** yazın.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-129">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="9a6bb-130">Dil listesinden **C#** veya **Visual Basic** seçin ve ardından platform listesinden **tüm platformlar** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-130">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="9a6bb-131">**Sınıf kitaplığı (.NET Standard)** şablonunu seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-131">Choose the **Class Library (.NET Standard)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="9a6bb-132">**Yeni projenizi yapılandırın** sayfasında, **Proje adı** kutusuna **StringLibrary** yazın.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-132">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box.</span></span> <span data-ttu-id="9a6bb-133">Ardından **Oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-133">Then, choose **Create**.</span></span>

1. <span data-ttu-id="9a6bb-134">Kitaplığın doğru .NET Standard sürümünü hedeflediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-134">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="9a6bb-135">**Çözüm Gezgini**kitaplık projesine sağ tıklayın ve ardından **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-135">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="9a6bb-136">**Hedef Framework** metin kutusu, projenin .NET Standard 2,0 ' i hedeflediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-136">The **Target Framework** text box shows that the project targets .NET Standard 2.0.</span></span>

   ![Sınıf kitaplığı için proje özellikleri](./media/library-with-visual-studio/library-project-properties.png)

1. <span data-ttu-id="9a6bb-138">Visual Basic kullanıyorsanız, **kök ad alanı** metin kutusundaki metni temizleyin.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-138">If you're using Visual Basic, clear the text in the **Root namespace** text box.</span></span>

   ![Sınıf kitaplığı için proje özellikleri](./media/library-with-visual-studio/vb/library-project-properties.png)

   <span data-ttu-id="9a6bb-140">Her proje için, Visual Basic otomatik olarak proje adına karşılık gelen bir ad alanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-140">For each project, Visual Basic automatically creates a namespace that corresponds to the project name.</span></span> <span data-ttu-id="9a6bb-141">Bu öğreticide, kod dosyasındaki anahtar sözcüğünü kullanarak üst düzey bir ad alanı tanımlarsınız [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="9a6bb-141">In this tutorial, you define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword in the code file.</span></span>

1. <span data-ttu-id="9a6bb-142">*Class1.cs* veya *Class1. vb* için kod penceresindeki kodu aşağıdaki kodla değiştirin ve dosyayı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-142">Replace the code in the code window for *Class1.cs*  or *Class1.vb* with the following code, and save the file.</span></span> <span data-ttu-id="9a6bb-143">Kullanmak istediğiniz dil gösterilmiyorsa sayfanın en üstündeki dil seçicisini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-143">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

   [!code-csharp[](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]
   [!code-vb[](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   <span data-ttu-id="9a6bb-144">Sınıf kitaplığı, `UtilityLibraries.StringLibrary` adlı bir yöntemi içerir `StartsWithUpper` .</span><span class="sxs-lookup"><span data-stu-id="9a6bb-144">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="9a6bb-145">Bu yöntem <xref:System.Boolean> , geçerli dize örneğinin büyük harfli bir karakterle başlayıp başlamadığını belirten bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-145">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="9a6bb-146">Unicode standart, büyük harfli karakterleri küçük harfli karakterlerden ayırır.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-146">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="9a6bb-147"><xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> `true` Bir karakter büyük harfli ise, yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-147">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="9a6bb-148">**Build**  >  Projenin hatasız derlendiğinden emin olmak için menü çubuğunda, derleme**çözümü** oluştur ' u seçin.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-148">On the menu bar, select **Build** > **Build Solution** to verify that the project compiles without error.</span></span>

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="9a6bb-149">Çözüme bir konsol uygulaması ekleme</span><span class="sxs-lookup"><span data-stu-id="9a6bb-149">Add a console app to the solution</span></span>

<span data-ttu-id="9a6bb-150">Bir konsol uygulamasında sınıf kitaplığını kullanarak, dizenin büyük harfli bir karakterle başlayıp başlamamadığını bir dize ve rapor girmesini ister.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-150">Use the class library in a console application that prompts the user to enter a string and reports whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="9a6bb-151">Çözüme "gösterimi" adlı yeni bir .NET Core konsol uygulaması ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-151">Add a new .NET Core console application named "ShowCase" to the solution.</span></span>

   1. <span data-ttu-id="9a6bb-152">**Çözüm Gezgini** çözüme sağ tıklayın ve **Add**  >  **Yeni proje**Ekle ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-152">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="9a6bb-153">**Yeni Proje Ekle** sayfasında, arama kutusuna **konsol** girin.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-153">On the **Add a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="9a6bb-154">Dil listesinden **C#** veya **Visual Basic** seçin ve ardından platform listesinden **tüm platformlar** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-154">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span>

   1. <span data-ttu-id="9a6bb-155">**Konsol uygulaması (.NET Core)** şablonunu seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-155">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="9a6bb-156">**Yeni projenizi yapılandırın** sayfasında, **Proje adı** kutusuna **gösterimi** girin.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-156">On the **Configure your new project** page, enter **ShowCase** in the **Project name** box.</span></span> <span data-ttu-id="9a6bb-157">Ardından **Oluştur**’u seçin.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-157">Then choose **Create**.</span></span>

1. <span data-ttu-id="9a6bb-158">**Çözüm Gezgini** **, Gösterim projesine sağ** tıklayın ve bağlam menüsünde **Başlangıç projesi olarak ayarla** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-158">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span>

   ![Başlangıç projesini ayarlamak için Visual Studio proje bağlam menüsü](media/library-with-visual-studio/set-startup-project-context-menu.png)

1. <span data-ttu-id="9a6bb-160">Başlangıçta, yeni konsol uygulaması projesi sınıf kitaplığına erişemez.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-160">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="9a6bb-161">Sınıf kitaplığındaki yöntemleri çağırmasına izin vermek için, sınıf kitaplığı projesine bir proje başvurusu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-161">To allow it to call methods in the class library, create a project reference to the class library project.</span></span> <span data-ttu-id="9a6bb-162">**Çözüm Gezgini**, `ShowCase` projenin **Bağımlılıklar** düğümüne sağ tıklayın ve **proje başvurusu Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-162">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node, and select **Add Project Reference**.</span></span>

   ![Visual Studio 'da başvuru bağlam menüsü Ekle](media/library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="9a6bb-164">**Başvuru Yöneticisi** Iletişim kutusunda **StringLibrary** projesini seçin ve **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-164">In the **Reference Manager** dialog, select the **StringLibrary** project, and select **OK**.</span></span>

   ![StringLibrary seçiliyken başvuru Yöneticisi iletişim kutusu](media/library-with-visual-studio/manage-project-references.png)

1. <span data-ttu-id="9a6bb-166">*Program.cs* veya *program. vb* dosyasının kod penceresinde, tüm kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-166">In the code window for the *Program.cs* or *Program.vb* file, replace all of the code with the following code.</span></span>

   [!code-csharp[UsingClassLib#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]
   [!code-vb[UsingClassLib#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   <span data-ttu-id="9a6bb-167">Kod, `row` konsol penceresine yazılan veri satırlarının sayısını korumak için değişkenini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-167">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="9a6bb-168">25 ' e eşit veya daha büyük olduğunda, kod konsol penceresini temizler ve kullanıcıya bir ileti görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-168">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="9a6bb-169">Program kullanıcıdan bir dize girmesini ister.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-169">The program prompts the user to enter a string.</span></span> <span data-ttu-id="9a6bb-170">Dizenin büyük harfle başlatılıp başlatılmayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-170">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="9a6bb-171">Kullanıcı bir dize girmeden ENTER tuşuna basarsa, uygulama sonlanır ve konsol penceresi kapanır.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-171">If the user presses the Enter key without entering a string, the application ends, and the console window closes.</span></span>

1. <span data-ttu-id="9a6bb-172">Gerekirse, projenin **hata ayıklama** sürümünü derlemek için araç çubuğunu değiştirin `ShowCase` .</span><span class="sxs-lookup"><span data-stu-id="9a6bb-172">If necessary, change the toolbar to compile the **Debug** release of the `ShowCase` project.</span></span> <span data-ttu-id="9a6bb-173">**Gösterimi** düğmesindeki yeşil oku seçerek programı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-173">Compile and run the program by selecting the green arrow on the **ShowCase** button.</span></span>

   ![Hata ayıklama düğmesini gösteren Visual Studio proje araç çubuğu](media/library-with-visual-studio/visual-studio-project-toolbar.png)

1. <span data-ttu-id="9a6bb-175">Dizeleri girerek ve **ENTER**'a basarak programı deneyin ve çıkmak için **ENTER** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-175">Try out the program by entering strings and pressing **Enter**, then press **Enter** to exit.</span></span>

   :::image type="content" source="media/library-with-visual-studio/run-showcase.png" alt-text="Gösterimi çalışan konsol penceresi":::

## <a name="next-steps"></a><span data-ttu-id="9a6bb-177">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="9a6bb-177">Next steps</span></span>

<span data-ttu-id="9a6bb-178">Bu öğreticide, bir çözüm oluşturdunuz, bir kitaplık projesi eklediniz ve kitaplığı kullanan bir konsol uygulaması projesi ekledik.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-178">In this tutorial, you created a solution, added a library project, and added a console app project that uses the library.</span></span> <span data-ttu-id="9a6bb-179">Sonraki öğreticide, çözüme bir birim testi projesi eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="9a6bb-179">In the next tutorial, you add a unit test project to the solution.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9a6bb-180">Visual Studio 'da .NET Core ile .NET Standard kitaplığı test etme</span><span class="sxs-lookup"><span data-stu-id="9a6bb-180">Test a .NET Standard library with .NET Core in Visual Studio</span></span>](testing-library-with-visual-studio.md)
