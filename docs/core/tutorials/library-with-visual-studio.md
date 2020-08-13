---
title: Visual Studio 'Yu kullanarak .NET Standard sınıf kitaplığı oluşturma
description: Visual Studio kullanarak .NET Standard sınıf kitaplığı oluşturmayı öğrenin.
ms.date: 08/07/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet,contperfq1
ms.openlocfilehash: 595e93d8d8d22478c6770ddd4f70a0214653f5b9
ms.sourcegitcommit: d337df55f83325918cbbd095eb573400bea49064
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2020
ms.locfileid: "88187949"
---
# <a name="tutorial-create-a-net-standard-library-using-visual-studio"></a><span data-ttu-id="5b327-103">Öğretici: Visual Studio kullanarak .NET Standard kitaplığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="5b327-103">Tutorial: Create a .NET Standard library using Visual Studio</span></span>

<span data-ttu-id="5b327-104">Bu öğreticide, tek bir dize işleme yöntemi içeren basit bir sınıf kitaplığı oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="5b327-104">In this tutorial, you create a simple class library that contains a single string-handling method.</span></span>

<span data-ttu-id="5b327-105">Bir *sınıf kitaplığı* , bir uygulama tarafından çağrılan türleri ve yöntemleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5b327-105">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="5b327-106">.NET Standard 2,0 ' i hedefleyen bir sınıf kitaplığı, kitaplığınızın bu .NET Standard sürümünü destekleyen herhangi bir .NET uygulamasının çağrılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="5b327-106">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span>

<span data-ttu-id="5b327-107">Sınıf kitaplığınızı bitirdiğinizde, bir NuGet paketi veya onu kullanan uygulamayla paketlenmiş bir bileşen olarak dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b327-107">When you finish your class library, you can distribute it as a NuGet package or as a component bundled with the application that uses it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5b327-108">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="5b327-108">Prerequisites</span></span>

- <span data-ttu-id="5b327-109">**.NET Core platformlar arası geliştirme** iş yükünün yüklü olduğu [Visual Studio 2019 sürüm 16,6 veya sonraki bir sürüm](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) .</span><span class="sxs-lookup"><span data-stu-id="5b327-109">[Visual Studio 2019 version 16.6 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="5b327-110">.NET Core 3,1 SDK, bu iş yükünü seçtiğinizde otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="5b327-110">.NET Core 3.1 SDK is automatically installed when you select this workload.</span></span>

## <a name="create-a-solution"></a><span data-ttu-id="5b327-111">Çözüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="5b327-111">Create a solution</span></span>

<span data-ttu-id="5b327-112">' De Sınıf Kitaplığı projesini yerleştirmek için boş bir çözüm oluşturarak başlayın.</span><span class="sxs-lookup"><span data-stu-id="5b327-112">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="5b327-113">Visual Studio çözümü bir veya daha fazla proje için kapsayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="5b327-113">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="5b327-114">Aynı çözüme ek ve ilgili projeler ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="5b327-114">You'll add additional, related projects to the same solution.</span></span>

<span data-ttu-id="5b327-115">Boş çözümü oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="5b327-115">To create the blank solution:</span></span>

1. <span data-ttu-id="5b327-116">Visual Studio’yu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5b327-116">Start Visual Studio.</span></span>

2. <span data-ttu-id="5b327-117">Başlangıç penceresinde **Yeni proje oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="5b327-117">On the start window, choose **Create a new project**.</span></span>

3. <span data-ttu-id="5b327-118">**Yeni proje oluştur** sayfasında, arama kutusuna **çözüm** girin.</span><span class="sxs-lookup"><span data-stu-id="5b327-118">On the **Create a new project** page, enter **solution** in the search box.</span></span> <span data-ttu-id="5b327-119">**Boş çözüm** şablonunu seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="5b327-119">Choose the **Blank Solution** template, and then choose **Next**.</span></span>

   ![Visual Studio 'da boş çözüm şablonu](media/library-with-visual-studio/blank-solution.png)

4. <span data-ttu-id="5b327-121">**Yeni projenizi yapılandırın** sayfasında, **Proje adı** kutusuna **classlibraryprojects** ' i girin.</span><span class="sxs-lookup"><span data-stu-id="5b327-121">On the **Configure your new project** page, enter **ClassLibraryProjects** in the **Project name** box.</span></span> <span data-ttu-id="5b327-122">Ardından **Oluştur**’u seçin.</span><span class="sxs-lookup"><span data-stu-id="5b327-122">Then choose **Create**.</span></span>

## <a name="create-a-class-library-project"></a><span data-ttu-id="5b327-123">Sınıf kitaplığı projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="5b327-123">Create a class library project</span></span>

1. <span data-ttu-id="5b327-124">Çözüme "StringLibrary" adlı yeni bir .NET Standard sınıf kitaplığı projesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5b327-124">Add a new .NET Standard class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="5b327-125">**Çözüm Gezgini** çözüme sağ tıklayın ve **Add**  >  **Yeni proje**Ekle ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="5b327-125">Right-click on the solution in **Solution Explorer** and select **Add** > **New Project**.</span></span>

   1. <span data-ttu-id="5b327-126">**Yeni Proje Ekle** sayfasında, arama kutusuna **kitaplık** yazın.</span><span class="sxs-lookup"><span data-stu-id="5b327-126">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="5b327-127">Dil listesinden **C#** veya **Visual Basic** seçin ve ardından platform listesinden **tüm platformlar** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="5b327-127">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="5b327-128">**Sınıf kitaplığı (.NET Standard)** şablonunu seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="5b327-128">Choose the **Class Library (.NET Standard)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="5b327-129">**Yeni projenizi yapılandırın** sayfasında, **Proje adı** kutusuna **StringLibrary** yazın.</span><span class="sxs-lookup"><span data-stu-id="5b327-129">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box.</span></span> <span data-ttu-id="5b327-130">Ardından **Oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="5b327-130">Then, choose **Create**.</span></span>

1. <span data-ttu-id="5b327-131">Kitaplığın doğru .NET Standard sürümünü hedeflediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="5b327-131">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="5b327-132">**Çözüm Gezgini**kitaplık projesine sağ tıklayın ve ardından **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="5b327-132">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="5b327-133">**Hedef Framework** metin kutusu, projenin .NET Standard 2,0 ' i hedeflediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5b327-133">The **Target Framework** text box shows that the project targets .NET Standard 2.0.</span></span>

   ![Sınıf kitaplığı için proje özellikleri](./media/library-with-visual-studio/library-project-properties.png)

1. <span data-ttu-id="5b327-135">Visual Basic kullanıyorsanız, **kök ad alanı** metin kutusundaki metni temizleyin.</span><span class="sxs-lookup"><span data-stu-id="5b327-135">If you're using Visual Basic, clear the text in the **Root namespace** text box.</span></span>

   ![Sınıf kitaplığı için proje özellikleri](./media/library-with-visual-studio/vb/library-project-properties.png)

   <span data-ttu-id="5b327-137">Her proje için, Visual Basic otomatik olarak proje adına karşılık gelen bir ad alanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5b327-137">For each project, Visual Basic automatically creates a namespace that corresponds to the project name.</span></span> <span data-ttu-id="5b327-138">Bu öğreticide, kod dosyasındaki anahtar sözcüğünü kullanarak üst düzey bir ad alanı tanımlarsınız [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="5b327-138">In this tutorial, you define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword in the code file.</span></span>

1. <span data-ttu-id="5b327-139">*Class1.cs* veya *Class1. vb* için kod penceresindeki kodu aşağıdaki kodla değiştirin ve dosyayı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="5b327-139">Replace the code in the code window for *Class1.cs*  or *Class1.vb* with the following code, and save the file.</span></span> <span data-ttu-id="5b327-140">Kullanmak istediğiniz dil gösterilmiyorsa sayfanın en üstündeki dil seçicisini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="5b327-140">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/StringLibrary/Class1.vb":::

   <span data-ttu-id="5b327-141">Sınıf kitaplığı, `UtilityLibraries.StringLibrary` adlı bir yöntemi içerir `StartsWithUpper` .</span><span class="sxs-lookup"><span data-stu-id="5b327-141">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="5b327-142">Bu yöntem <xref:System.Boolean> , geçerli dize örneğinin büyük harfli bir karakterle başlayıp başlamadığını belirten bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="5b327-142">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="5b327-143">Unicode standart, büyük harfli karakterleri küçük harfli karakterlerden ayırır.</span><span class="sxs-lookup"><span data-stu-id="5b327-143">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="5b327-144"><xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> `true` Bir karakter büyük harfli ise, yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="5b327-144">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

   <span data-ttu-id="5b327-145">`StartsWithUpper` , sınıfının bir üyesi gibi çağırabilmeniz için bir [genişletme yöntemi](../../csharp/programming-guide/classes-and-structs/extension-methods.md) olarak uygulanır <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="5b327-145">`StartsWithUpper` is implemented as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

1. <span data-ttu-id="5b327-146">**Build**  >  Projenin hatasız derlendiğinden emin olmak için menü çubuğunda, derleme**çözümü** oluştur ' u seçin.</span><span class="sxs-lookup"><span data-stu-id="5b327-146">On the menu bar, select **Build** > **Build Solution** to verify that the project compiles without error.</span></span>

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="5b327-147">Çözüme bir konsol uygulaması ekleme</span><span class="sxs-lookup"><span data-stu-id="5b327-147">Add a console app to the solution</span></span>

<span data-ttu-id="5b327-148">Sınıf kitaplığını kullanan bir konsol uygulaması ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5b327-148">Add a console application that uses the class library.</span></span> <span data-ttu-id="5b327-149">Uygulama kullanıcıdan bir dize girmesini ister ve dizenin büyük harfli bir karakterle başlayıp başlamamadığını rapor eder.</span><span class="sxs-lookup"><span data-stu-id="5b327-149">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="5b327-150">Çözüme "gösterimi" adlı yeni bir .NET Core konsol uygulaması ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5b327-150">Add a new .NET Core console application named "ShowCase" to the solution.</span></span>

   1. <span data-ttu-id="5b327-151">**Çözüm Gezgini** çözüme sağ tıklayın ve **Add**  >  **Yeni proje**Ekle ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="5b327-151">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="5b327-152">**Yeni Proje Ekle** sayfasında, arama kutusuna **konsol** girin.</span><span class="sxs-lookup"><span data-stu-id="5b327-152">On the **Add a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="5b327-153">Dil listesinden **C#** veya **Visual Basic** seçin ve ardından platform listesinden **tüm platformlar** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="5b327-153">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span>

   1. <span data-ttu-id="5b327-154">**Konsol uygulaması (.NET Core)** şablonunu seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="5b327-154">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="5b327-155">**Yeni projenizi yapılandırın** sayfasında, **Proje adı** kutusuna **gösterimi** girin.</span><span class="sxs-lookup"><span data-stu-id="5b327-155">On the **Configure your new project** page, enter **ShowCase** in the **Project name** box.</span></span> <span data-ttu-id="5b327-156">Ardından **Oluştur**’u seçin.</span><span class="sxs-lookup"><span data-stu-id="5b327-156">Then choose **Create**.</span></span>

1. <span data-ttu-id="5b327-157">*Program.cs* veya *program. vb* dosyasının kod penceresinde, tüm kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="5b327-157">In the code window for the *Program.cs* or *Program.vb* file, replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/ShowCase/Program.vb":::

   <span data-ttu-id="5b327-158">Kod, `row` konsol penceresine yazılan veri satırlarının sayısını korumak için değişkenini kullanır.</span><span class="sxs-lookup"><span data-stu-id="5b327-158">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="5b327-159">25 ' e eşit veya daha büyük olduğunda, kod konsol penceresini temizler ve kullanıcıya bir ileti görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5b327-159">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="5b327-160">Program kullanıcıdan bir dize girmesini ister.</span><span class="sxs-lookup"><span data-stu-id="5b327-160">The program prompts the user to enter a string.</span></span> <span data-ttu-id="5b327-161">Dizenin büyük harfle başlatılıp başlatılmayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5b327-161">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="5b327-162">Kullanıcı bir dize girmeden <kbd>ENTER</kbd> tuşuna basarsa, uygulama sonlanır ve konsol penceresi kapanır.</span><span class="sxs-lookup"><span data-stu-id="5b327-162">If the user presses the <kbd>Enter</kbd> key without entering a string, the application ends, and the console window closes.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="5b327-163">Proje başvurusu Ekle</span><span class="sxs-lookup"><span data-stu-id="5b327-163">Add a project reference</span></span>

<span data-ttu-id="5b327-164">Başlangıçta, yeni konsol uygulaması projesi sınıf kitaplığına erişemez.</span><span class="sxs-lookup"><span data-stu-id="5b327-164">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="5b327-165">Sınıf kitaplığındaki yöntemleri çağırmasına izin vermek için, sınıf kitaplığı projesine bir proje başvurusu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5b327-165">To allow it to call methods in the class library, create a project reference to the class library project.</span></span>

1. <span data-ttu-id="5b327-166">**Çözüm Gezgini**, `ShowCase` projenin **Bağımlılıklar** düğümüne sağ tıklayın ve **proje başvurusu Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="5b327-166">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node, and select **Add Project Reference**.</span></span>

   ![Visual Studio 'da başvuru bağlam menüsü Ekle](media/library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="5b327-168">**Başvuru Yöneticisi** Iletişim kutusunda **StringLibrary** projesini seçin ve **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="5b327-168">In the **Reference Manager** dialog, select the **StringLibrary** project, and select **OK**.</span></span>

   ![StringLibrary seçiliyken başvuru Yöneticisi iletişim kutusu](media/library-with-visual-studio/manage-project-references.png)

## <a name="run-the-app"></a><span data-ttu-id="5b327-170">Uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="5b327-170">Run the app</span></span>

1. <span data-ttu-id="5b327-171">**Çözüm Gezgini** **, Gösterim projesine sağ** tıklayın ve bağlam menüsünde **Başlangıç projesi olarak ayarla** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="5b327-171">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span>

   ![Başlangıç projesini ayarlamak için Visual Studio proje bağlam menüsü](media/library-with-visual-studio/set-startup-project-context-menu.png)

1. <span data-ttu-id="5b327-173"><kbd>Ctrl</kbd> + Hata ayıklama olmadan programı derlemek ve çalıştırmak için CTRL<kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="5b327-173">Press <kbd>Ctrl</kbd>+<kbd>F5</kbd> to compile and run the program without debugging.</span></span>

   ![Hata ayıklama düğmesini gösteren Visual Studio proje araç çubuğu](media/library-with-visual-studio/visual-studio-project-toolbar.png)

1. <span data-ttu-id="5b327-175">Dizeleri girerek ve <kbd>ENTER</kbd>'a basarak programı deneyin ve çıkmak için <kbd>ENTER</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="5b327-175">Try out the program by entering strings and pressing <kbd>Enter</kbd>, then press <kbd>Enter</kbd> to exit.</span></span>

   :::image type="content" source="media/library-with-visual-studio/run-showcase.png" alt-text="Gösterimi çalışan konsol penceresi":::

## <a name="additional-resources"></a><span data-ttu-id="5b327-177">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="5b327-177">Additional resources</span></span>

* [<span data-ttu-id="5b327-178">.NET Core CLI ile Kitaplıklar geliştirin</span><span class="sxs-lookup"><span data-stu-id="5b327-178">Develop libraries with the .NET Core CLI</span></span>](libraries.md)
* <span data-ttu-id="5b327-179">[.NET Standard sürümleri ve destekledikleri platformlar](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="5b327-179">[.NET Standard versions and the platforms they support](../../standard/net-standard.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="5b327-180">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="5b327-180">Next steps</span></span>

<span data-ttu-id="5b327-181">Bu öğreticide, bir sınıf kitaplığı oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="5b327-181">In this tutorial, you created a class library.</span></span> <span data-ttu-id="5b327-182">Sonraki öğreticide, sınıf kitaplığını birim testi ile öğrenin.</span><span class="sxs-lookup"><span data-stu-id="5b327-182">In the next tutorial, you learn how to unit test the class library.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5b327-183">Visual Studio 'Yu kullanarak .NET Standard kitaplığı ile birim testi</span><span class="sxs-lookup"><span data-stu-id="5b327-183">Unit test a .NET Standard library using Visual Studio</span></span>](testing-library-with-visual-studio.md)

<span data-ttu-id="5b327-184">Ya da otomatik birim testlerini atlayabilir ve bir NuGet paketi oluşturarak kitaplığı nasıl paylaşacağınızı öğrenebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5b327-184">Or you can skip automated unit testing and learn how to share the library by creating a NuGet package:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5b327-185">Visual Studio kullanarak paket oluşturma ve yayımlama</span><span class="sxs-lookup"><span data-stu-id="5b327-185">Create and publish a package using Visual Studio</span></span>](/nuget/quickstart/create-and-publish-a-package-using-visual-studio)

<span data-ttu-id="5b327-186">Ya da bir konsol uygulamasını yayımlamayı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="5b327-186">Or learn how to publish a console app.</span></span> <span data-ttu-id="5b327-187">Konsol uygulamasını, bu öğreticide oluşturduğunuz çözümden yayımlarsanız, sınıf kitaplığı bir *. dll* dosyası olarak onunla birlikte görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5b327-187">If you publish the console app from the solution you created in this tutorial, the class library goes with it as a *.dll* file.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5b327-188">Visual Studio kullanarak bir .NET Core konsol uygulaması yayımlama</span><span class="sxs-lookup"><span data-stu-id="5b327-188">Publish a .NET Core console application using Visual Studio</span></span>](publishing-with-visual-studio.md)
