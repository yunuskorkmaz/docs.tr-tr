---
title: Visual Studio 'Yu kullanarak .NET Standard sınıf kitaplığı oluşturma
description: Visual Studio kullanarak .NET Standard sınıf kitaplığı oluşturmayı öğrenin.
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: ef9c62b0378e1064d8cfd90a8c59aed74ea312b2
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2020
ms.locfileid: "84701571"
---
# <a name="tutorial-create-a-net-standard-library-using-visual-studio"></a><span data-ttu-id="afdb8-103">Öğretici: Visual Studio kullanarak .NET Standard kitaplığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="afdb8-103">Tutorial: Create a .NET Standard library using Visual Studio</span></span>

<span data-ttu-id="afdb8-104">Bu öğreticide, tek bir dize işleme yöntemi içeren basit bir yardımcı program kitaplığı oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="afdb8-104">In this tutorial, you create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="afdb8-105">Bunu, sınıfının bir üyesi gibi çağırabilmeniz için bir [genişletme yöntemi](../../csharp/programming-guide/classes-and-structs/extension-methods.md) olarak uygulamalısınız <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="afdb8-105">You implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

<span data-ttu-id="afdb8-106">Bir *sınıf kitaplığı* , bir uygulama tarafından çağrılan türleri ve yöntemleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="afdb8-106">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="afdb8-107">.NET Standard 2,0 ' i hedefleyen bir sınıf kitaplığı, kitaplığınızın bu .NET Standard sürümünü destekleyen herhangi bir .NET uygulamasının çağrılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="afdb8-107">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span> <span data-ttu-id="afdb8-108">Sınıf kitaplığınızı bitirdiğinizde, bir üçüncü taraf bileşen olarak veya bir veya daha fazla uygulamayla paketlenmiş bileşen olarak dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="afdb8-108">When you finish your class library, you can distribute it as a third-party component or as a bundled component with one or more applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="afdb8-109">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="afdb8-109">Prerequisites</span></span>

- <span data-ttu-id="afdb8-110">**.NET Core platformlar arası geliştirme** iş yükünün yüklü olduğu [Visual Studio 2019 sürüm 16,6 veya sonraki bir sürüm](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) .</span><span class="sxs-lookup"><span data-stu-id="afdb8-110">[Visual Studio 2019 version 16.6 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="afdb8-111">.NET Core 3,1 SDK, bu iş yükünü seçtiğinizde otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="afdb8-111">.NET Core 3.1 SDK is automatically installed when you select this workload.</span></span>

  <span data-ttu-id="afdb8-112">Daha fazla bilgi için, [.NET Core SDK](../install/sdk.md?pivots=os-windows) makalesine [Visual Studio ile install](../install/sdk.md?pivots=os-windows#install-with-visual-studio) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="afdb8-112">For more information, see the [Install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) section on the [Install the .NET Core SDK](../install/sdk.md?pivots=os-windows) article.</span></span>

## <a name="create-a-solution"></a><span data-ttu-id="afdb8-113">Çözüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="afdb8-113">Create a solution</span></span>

<span data-ttu-id="afdb8-114">' De Sınıf Kitaplığı projesini yerleştirmek için boş bir çözüm oluşturarak başlayın.</span><span class="sxs-lookup"><span data-stu-id="afdb8-114">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="afdb8-115">Visual Studio çözümü bir veya daha fazla proje için kapsayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="afdb8-115">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="afdb8-116">Aynı çözüme ek ve ilgili projeler ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="afdb8-116">You'll add additional, related projects to the same solution.</span></span>

<span data-ttu-id="afdb8-117">Boş çözümü oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="afdb8-117">To create the blank solution:</span></span>

1. <span data-ttu-id="afdb8-118">Visual Studio’yu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="afdb8-118">Start Visual Studio.</span></span>

2. <span data-ttu-id="afdb8-119">Başlangıç penceresinde **Yeni proje oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="afdb8-119">On the start window, choose **Create a new project**.</span></span>

3. <span data-ttu-id="afdb8-120">**Yeni proje oluştur** sayfasında, arama kutusuna **çözüm** girin.</span><span class="sxs-lookup"><span data-stu-id="afdb8-120">On the **Create a new project** page, enter **solution** in the search box.</span></span> <span data-ttu-id="afdb8-121">**Boş çözüm** şablonunu seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="afdb8-121">Choose the **Blank Solution** template, and then choose **Next**.</span></span>

   ![Visual Studio 'da boş çözüm şablonu](media/library-with-visual-studio/blank-solution.png)

4. <span data-ttu-id="afdb8-123">**Yeni projenizi yapılandırın** sayfasında, **Proje adı** kutusuna **classlibraryprojects** ' i girin.</span><span class="sxs-lookup"><span data-stu-id="afdb8-123">On the **Configure your new project** page, enter **ClassLibraryProjects** in the **Project name** box.</span></span> <span data-ttu-id="afdb8-124">Ardından **Oluştur**’u seçin.</span><span class="sxs-lookup"><span data-stu-id="afdb8-124">Then choose **Create**.</span></span>

## <a name="create-a-class-library-project"></a><span data-ttu-id="afdb8-125">Sınıf kitaplığı projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="afdb8-125">Create a class library project</span></span>

1. <span data-ttu-id="afdb8-126">Çözüme "StringLibrary" adlı yeni bir .NET Standard sınıf kitaplığı projesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="afdb8-126">Add a new .NET Standard class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="afdb8-127">**Çözüm Gezgini** çözüme sağ tıklayın ve **Add**  >  **Yeni proje**Ekle ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="afdb8-127">Right-click on the solution in **Solution Explorer** and select **Add** > **New Project**.</span></span>

   1. <span data-ttu-id="afdb8-128">**Yeni Proje Ekle** sayfasında, arama kutusuna **kitaplık** yazın.</span><span class="sxs-lookup"><span data-stu-id="afdb8-128">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="afdb8-129">Dil listesinden **C#** veya **Visual Basic** seçin ve ardından platform listesinden **tüm platformlar** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="afdb8-129">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="afdb8-130">**Sınıf kitaplığı (.NET Standard)** şablonunu seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="afdb8-130">Choose the **Class Library (.NET Standard)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="afdb8-131">**Yeni projenizi yapılandırın** sayfasında, **Proje adı** kutusuna **StringLibrary** yazın.</span><span class="sxs-lookup"><span data-stu-id="afdb8-131">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box.</span></span> <span data-ttu-id="afdb8-132">Ardından **Oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="afdb8-132">Then, choose **Create**.</span></span>

1. <span data-ttu-id="afdb8-133">Kitaplığın doğru .NET Standard sürümünü hedeflediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="afdb8-133">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="afdb8-134">**Çözüm Gezgini**kitaplık projesine sağ tıklayın ve ardından **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="afdb8-134">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="afdb8-135">**Hedef Framework** metin kutusu, projenin .NET Standard 2,0 ' i hedeflediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="afdb8-135">The **Target Framework** text box shows that the project targets .NET Standard 2.0.</span></span>

   ![Sınıf kitaplığı için proje özellikleri](./media/library-with-visual-studio/library-project-properties.png)

1. <span data-ttu-id="afdb8-137">Visual Basic kullanıyorsanız, **kök ad alanı** metin kutusundaki metni temizleyin.</span><span class="sxs-lookup"><span data-stu-id="afdb8-137">If you're using Visual Basic, clear the text in the **Root namespace** text box.</span></span>

   ![Sınıf kitaplığı için proje özellikleri](./media/library-with-visual-studio/vb/library-project-properties.png)

   <span data-ttu-id="afdb8-139">Her proje için, Visual Basic otomatik olarak proje adına karşılık gelen bir ad alanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="afdb8-139">For each project, Visual Basic automatically creates a namespace that corresponds to the project name.</span></span> <span data-ttu-id="afdb8-140">Bu öğreticide, kod dosyasındaki anahtar sözcüğünü kullanarak üst düzey bir ad alanı tanımlarsınız [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="afdb8-140">In this tutorial, you define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword in the code file.</span></span>

1. <span data-ttu-id="afdb8-141">*Class1.cs* veya *Class1. vb* için kod penceresindeki kodu aşağıdaki kodla değiştirin ve dosyayı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="afdb8-141">Replace the code in the code window for *Class1.cs*  or *Class1.vb* with the following code, and save the file.</span></span> <span data-ttu-id="afdb8-142">Kullanmak istediğiniz dil gösterilmiyorsa sayfanın en üstündeki dil seçicisini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="afdb8-142">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/StringLibrary/Class1.vb":::

   <span data-ttu-id="afdb8-143">Sınıf kitaplığı, `UtilityLibraries.StringLibrary` adlı bir yöntemi içerir `StartsWithUpper` .</span><span class="sxs-lookup"><span data-stu-id="afdb8-143">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="afdb8-144">Bu yöntem <xref:System.Boolean> , geçerli dize örneğinin büyük harfli bir karakterle başlayıp başlamadığını belirten bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="afdb8-144">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="afdb8-145">Unicode standart, büyük harfli karakterleri küçük harfli karakterlerden ayırır.</span><span class="sxs-lookup"><span data-stu-id="afdb8-145">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="afdb8-146"><xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> `true` Bir karakter büyük harfli ise, yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="afdb8-146">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="afdb8-147">**Build**  >  Projenin hatasız derlendiğinden emin olmak için menü çubuğunda, derleme**çözümü** oluştur ' u seçin.</span><span class="sxs-lookup"><span data-stu-id="afdb8-147">On the menu bar, select **Build** > **Build Solution** to verify that the project compiles without error.</span></span>

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="afdb8-148">Çözüme bir konsol uygulaması ekleme</span><span class="sxs-lookup"><span data-stu-id="afdb8-148">Add a console app to the solution</span></span>

<span data-ttu-id="afdb8-149">Sınıf kitaplığını kullanan bir konsol uygulaması ekleyin.</span><span class="sxs-lookup"><span data-stu-id="afdb8-149">Add a console application that uses the class library.</span></span> <span data-ttu-id="afdb8-150">Uygulama kullanıcıdan bir dize girmesini ister ve dizenin büyük harfli bir karakterle başlayıp başlamamadığını rapor eder.</span><span class="sxs-lookup"><span data-stu-id="afdb8-150">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="afdb8-151">Çözüme "gösterimi" adlı yeni bir .NET Core konsol uygulaması ekleyin.</span><span class="sxs-lookup"><span data-stu-id="afdb8-151">Add a new .NET Core console application named "ShowCase" to the solution.</span></span>

   1. <span data-ttu-id="afdb8-152">**Çözüm Gezgini** çözüme sağ tıklayın ve **Add**  >  **Yeni proje**Ekle ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="afdb8-152">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="afdb8-153">**Yeni Proje Ekle** sayfasında, arama kutusuna **konsol** girin.</span><span class="sxs-lookup"><span data-stu-id="afdb8-153">On the **Add a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="afdb8-154">Dil listesinden **C#** veya **Visual Basic** seçin ve ardından platform listesinden **tüm platformlar** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="afdb8-154">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span>

   1. <span data-ttu-id="afdb8-155">**Konsol uygulaması (.NET Core)** şablonunu seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="afdb8-155">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="afdb8-156">**Yeni projenizi yapılandırın** sayfasında, **Proje adı** kutusuna **gösterimi** girin.</span><span class="sxs-lookup"><span data-stu-id="afdb8-156">On the **Configure your new project** page, enter **ShowCase** in the **Project name** box.</span></span> <span data-ttu-id="afdb8-157">Ardından **Oluştur**’u seçin.</span><span class="sxs-lookup"><span data-stu-id="afdb8-157">Then choose **Create**.</span></span>

1. <span data-ttu-id="afdb8-158">*Program.cs* veya *program. vb* dosyasının kod penceresinde, tüm kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="afdb8-158">In the code window for the *Program.cs* or *Program.vb* file, replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/ShowCase/Program.vb":::

   <span data-ttu-id="afdb8-159">Kod, `row` konsol penceresine yazılan veri satırlarının sayısını korumak için değişkenini kullanır.</span><span class="sxs-lookup"><span data-stu-id="afdb8-159">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="afdb8-160">25 ' e eşit veya daha büyük olduğunda, kod konsol penceresini temizler ve kullanıcıya bir ileti görüntüler.</span><span class="sxs-lookup"><span data-stu-id="afdb8-160">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="afdb8-161">Program kullanıcıdan bir dize girmesini ister.</span><span class="sxs-lookup"><span data-stu-id="afdb8-161">The program prompts the user to enter a string.</span></span> <span data-ttu-id="afdb8-162">Dizenin büyük harfle başlatılıp başlatılmayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="afdb8-162">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="afdb8-163">Kullanıcı bir dize girmeden <kbd>ENTER</kbd> tuşuna basarsa, uygulama sonlanır ve konsol penceresi kapanır.</span><span class="sxs-lookup"><span data-stu-id="afdb8-163">If the user presses the <kbd>Enter</kbd> key without entering a string, the application ends, and the console window closes.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="afdb8-164">Proje başvurusu Ekle</span><span class="sxs-lookup"><span data-stu-id="afdb8-164">Add a project reference</span></span>

<span data-ttu-id="afdb8-165">Başlangıçta, yeni konsol uygulaması projesi sınıf kitaplığına erişemez.</span><span class="sxs-lookup"><span data-stu-id="afdb8-165">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="afdb8-166">Sınıf kitaplığındaki yöntemleri çağırmasına izin vermek için, sınıf kitaplığı projesine bir proje başvurusu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="afdb8-166">To allow it to call methods in the class library, create a project reference to the class library project.</span></span>

1. <span data-ttu-id="afdb8-167">**Çözüm Gezgini**, `ShowCase` projenin **Bağımlılıklar** düğümüne sağ tıklayın ve **proje başvurusu Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="afdb8-167">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node, and select **Add Project Reference**.</span></span>

   ![Visual Studio 'da başvuru bağlam menüsü Ekle](media/library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="afdb8-169">**Başvuru Yöneticisi** Iletişim kutusunda **StringLibrary** projesini seçin ve **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="afdb8-169">In the **Reference Manager** dialog, select the **StringLibrary** project, and select **OK**.</span></span>

   ![StringLibrary seçiliyken başvuru Yöneticisi iletişim kutusu](media/library-with-visual-studio/manage-project-references.png)

## <a name="run-the-app"></a><span data-ttu-id="afdb8-171">Uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="afdb8-171">Run the app</span></span>

1. <span data-ttu-id="afdb8-172">**Çözüm Gezgini** **, Gösterim projesine sağ** tıklayın ve bağlam menüsünde **Başlangıç projesi olarak ayarla** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="afdb8-172">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span>

   ![Başlangıç projesini ayarlamak için Visual Studio proje bağlam menüsü](media/library-with-visual-studio/set-startup-project-context-menu.png)

1. <span data-ttu-id="afdb8-174"><kbd>Shift</kbd> + Hata ayıklama olmadan programı derlemek ve çalıştırmak için SHIFT<kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="afdb8-174">Press <kbd>Shift</kbd>+<kbd>F5</kbd> to compile and run the program without debugging.</span></span>

   ![Hata ayıklama düğmesini gösteren Visual Studio proje araç çubuğu](media/library-with-visual-studio/visual-studio-project-toolbar.png)

1. <span data-ttu-id="afdb8-176">Dizeleri girerek ve <kbd>ENTER</kbd>'a basarak programı deneyin ve çıkmak için <kbd>ENTER</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="afdb8-176">Try out the program by entering strings and pressing <kbd>Enter</kbd>, then press <kbd>Enter</kbd> to exit.</span></span>

   :::image type="content" source="media/library-with-visual-studio/run-showcase.png" alt-text="Gösterimi çalışan konsol penceresi":::

## <a name="additional-resources"></a><span data-ttu-id="afdb8-178">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="afdb8-178">Additional resources</span></span>

* [<span data-ttu-id="afdb8-179">.NET Core CLI ile Kitaplıklar geliştirin</span><span class="sxs-lookup"><span data-stu-id="afdb8-179">Develop libraries with the .NET Core CLI</span></span>](libraries.md)
* <span data-ttu-id="afdb8-180">[.NET Standard sürümleri ve destekledikleri platformlar](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="afdb8-180">[.NET Standard versions and the platforms they support](../../standard/net-standard.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="afdb8-181">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="afdb8-181">Next steps</span></span>

<span data-ttu-id="afdb8-182">Bu öğreticide, bir çözüm oluşturdunuz, bir kitaplık projesi eklediniz ve kitaplığı kullanan bir konsol uygulaması projesi ekledik.</span><span class="sxs-lookup"><span data-stu-id="afdb8-182">In this tutorial, you created a solution, added a library project, and added a console app project that uses the library.</span></span> <span data-ttu-id="afdb8-183">Sonraki öğreticide, çözüme bir birim testi projesi eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="afdb8-183">In the next tutorial, you add a unit test project to the solution.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="afdb8-184">Visual Studio kullanarak .NET Core ile .NET Standard kitaplığı test etme</span><span class="sxs-lookup"><span data-stu-id="afdb8-184">Test a .NET Standard library with .NET Core using Visual Studio</span></span>](testing-library-with-visual-studio.md)
