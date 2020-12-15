---
title: Visual Studio kullanarak .NET sınıf kitaplığı oluşturma
description: Visual Studio kullanarak .NET sınıf kitaplığı oluşturmayı öğrenin.
ms.date: 08/07/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet,contperf-fy21q1
ms.openlocfilehash: 2d9b02a155c950b77565a66417948568f5fa039f
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513126"
---
# <a name="tutorial-create-a-net-class-library-using-visual-studio"></a><span data-ttu-id="7d36e-103">Öğretici: Visual Studio kullanarak .NET sınıf kitaplığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="7d36e-103">Tutorial: Create a .NET class library using Visual Studio</span></span>

<span data-ttu-id="7d36e-104">Bu öğreticide, tek bir dize işleme yöntemi içeren basit bir sınıf kitaplığı oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="7d36e-104">In this tutorial, you create a simple class library that contains a single string-handling method.</span></span>

<span data-ttu-id="7d36e-105">Bir *sınıf kitaplığı* , bir uygulama tarafından çağrılan türleri ve yöntemleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7d36e-105">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="7d36e-106">Kitaplık .NET Standard 2,0 hedefliyorsa, .NET Standard 2,0 ' yi destekleyen herhangi bir .NET uygulamasıyla (.NET Framework dahil) çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="7d36e-106">If the library targets .NET Standard 2.0, it can be called by any .NET implementation (including .NET Framework) that supports .NET Standard 2.0.</span></span> <span data-ttu-id="7d36e-107">Kitaplık .NET 5 ' i hedefliyorsa, .NET 5 ' i hedefleyen herhangi bir uygulama tarafından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="7d36e-107">If the library targets .NET 5, it can be called by any application that targets .NET 5.</span></span> <span data-ttu-id="7d36e-108">Bu öğreticide, .NET 5 ' in nasıl hedeflenecek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7d36e-108">This tutorial shows how to target .NET 5.</span></span>

<span data-ttu-id="7d36e-109">Bir sınıf kitaplığı oluşturduğunuzda, bir NuGet paketi olarak veya onu kullanan uygulamayla paketlenmiş bir bileşen olarak dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d36e-109">When you create a class library, you can distribute it as a NuGet package or as a component bundled with the application that uses it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7d36e-110">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="7d36e-110">Prerequisites</span></span>

- <span data-ttu-id="7d36e-111">**.NET Core platformlar arası geliştirme** iş yükünün yüklü olduğu [Visual Studio 2019 sürüm 16,8 veya sonraki bir sürüm](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) .</span><span class="sxs-lookup"><span data-stu-id="7d36e-111">[Visual Studio 2019 version 16.8 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="7d36e-112">.NET 5,0 SDK, bu iş yükünü seçtiğinizde otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="7d36e-112">The .NET 5.0 SDK is automatically installed when you select this workload.</span></span> <span data-ttu-id="7d36e-113">Bu öğreticide, [Visual Studio kullanarak .NET konsol uygulaması oluşturma](with-visual-studio.md)bölümünde gösterildiği gibi, **Yeni projede tüm .NET Core şablonlarını göster** seçeneğini etkinleştirdiğiniz varsayılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7d36e-113">This tutorial assumes you have enabled **Show all .NET Core templates in the New project**, as shown in [Tutorial: Create a .NET console application using Visual Studio](with-visual-studio.md).</span></span>

## <a name="create-a-solution"></a><span data-ttu-id="7d36e-114">Çözüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="7d36e-114">Create a solution</span></span>

<span data-ttu-id="7d36e-115">' De Sınıf Kitaplığı projesini yerleştirmek için boş bir çözüm oluşturarak başlayın.</span><span class="sxs-lookup"><span data-stu-id="7d36e-115">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="7d36e-116">Visual Studio çözümü bir veya daha fazla proje için kapsayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="7d36e-116">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="7d36e-117">Aynı çözüme ek ve ilgili projeler ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="7d36e-117">You'll add additional, related projects to the same solution.</span></span>

<span data-ttu-id="7d36e-118">Boş çözümü oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="7d36e-118">To create the blank solution:</span></span>

1. <span data-ttu-id="7d36e-119">Visual Studio’yu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7d36e-119">Start Visual Studio.</span></span>

2. <span data-ttu-id="7d36e-120">Başlangıç penceresinde **Yeni proje oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="7d36e-120">On the start window, choose **Create a new project**.</span></span>

3. <span data-ttu-id="7d36e-121">**Yeni proje oluştur** sayfasında, arama kutusuna **çözüm** girin.</span><span class="sxs-lookup"><span data-stu-id="7d36e-121">On the **Create a new project** page, enter **solution** in the search box.</span></span> <span data-ttu-id="7d36e-122">**Boş çözüm** şablonunu seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="7d36e-122">Choose the **Blank Solution** template, and then choose **Next**.</span></span>

   :::image type="content" source="media/library-with-visual-studio/blank-solution.png" alt-text="Visual Studio 'da boş çözüm şablonu":::

4. <span data-ttu-id="7d36e-124">**Yeni projenizi yapılandırın** sayfasında, **Proje adı** kutusuna **classlibraryprojects** ' i girin.</span><span class="sxs-lookup"><span data-stu-id="7d36e-124">On the **Configure your new project** page, enter **ClassLibraryProjects** in the **Project name** box.</span></span> <span data-ttu-id="7d36e-125">Ardından **Oluştur**’u seçin.</span><span class="sxs-lookup"><span data-stu-id="7d36e-125">Then choose **Create**.</span></span>

## <a name="create-a-class-library-project"></a><span data-ttu-id="7d36e-126">Sınıf kitaplığı projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="7d36e-126">Create a class library project</span></span>

1. <span data-ttu-id="7d36e-127">Çözüme "StringLibrary" adlı yeni bir .NET sınıf kitaplığı projesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7d36e-127">Add a new .NET class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="7d36e-128">**Çözüm Gezgini** çözüme sağ tıklayın ve   >  **Yeni proje** Ekle ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="7d36e-128">Right-click on the solution in **Solution Explorer** and select **Add** > **New Project**.</span></span>

   1. <span data-ttu-id="7d36e-129">**Yeni Proje Ekle** sayfasında, arama kutusuna **kitaplık** yazın.</span><span class="sxs-lookup"><span data-stu-id="7d36e-129">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="7d36e-130">Dil listesinden **C#** veya **Visual Basic** seçin ve ardından platform listesinden **tüm platformlar** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="7d36e-130">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="7d36e-131">**Sınıf kitaplığı** şablonunu seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="7d36e-131">Choose the **Class Library** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="7d36e-132">**Yeni projenizi yapılandırın** sayfasında, **Proje adı** kutusuna **StringLibrary** girin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="7d36e-132">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box, and then choose **Next**.</span></span>

   1. <span data-ttu-id="7d36e-133">**Ek bilgi** sayfasında **.NET 5,0 (geçerli)** öğesini seçin ve ardından **Oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="7d36e-133">On the **Additional information** page, select **.NET 5.0 (Current)**, and then choose **Create**.</span></span>

1. <span data-ttu-id="7d36e-134">Kitaplığın doğru .NET sürümünü hedeflediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="7d36e-134">Check to make sure that the library targets the correct version of .NET.</span></span> <span data-ttu-id="7d36e-135">**Çözüm Gezgini** kitaplık projesine sağ tıklayın ve ardından **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="7d36e-135">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="7d36e-136">**Hedef Framework** metin kutusu, projenin .NET 5,0 ' i hedeflediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7d36e-136">The **Target Framework** text box shows that the project targets .NET 5.0.</span></span>

1. <span data-ttu-id="7d36e-137">Visual Basic kullanıyorsanız, **kök ad alanı** metin kutusundaki metni temizleyin.</span><span class="sxs-lookup"><span data-stu-id="7d36e-137">If you're using Visual Basic, clear the text in the **Root namespace** text box.</span></span>

   :::image type="content" source="./media/library-with-visual-studio/vb/library-project-properties.png" alt-text="Sınıf kitaplığı için proje özellikleri":::

   <span data-ttu-id="7d36e-139">Her proje için, Visual Basic otomatik olarak proje adına karşılık gelen bir ad alanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7d36e-139">For each project, Visual Basic automatically creates a namespace that corresponds to the project name.</span></span> <span data-ttu-id="7d36e-140">Bu öğreticide, kod dosyasındaki anahtar sözcüğünü kullanarak üst düzey bir ad alanı tanımlarsınız [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="7d36e-140">In this tutorial, you define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword in the code file.</span></span>

1. <span data-ttu-id="7d36e-141">*Class1.cs* veya *Class1. vb* için kod penceresindeki kodu aşağıdaki kodla değiştirin ve dosyayı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="7d36e-141">Replace the code in the code window for *Class1.cs*  or *Class1.vb* with the following code, and save the file.</span></span> <span data-ttu-id="7d36e-142">Kullanmak istediğiniz dil gösterilmiyorsa sayfanın en üstündeki dil seçicisini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7d36e-142">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/StringLibrary/Class1.vb":::

   <span data-ttu-id="7d36e-143">Sınıf kitaplığı, `UtilityLibraries.StringLibrary` adlı bir yöntemi içerir `StartsWithUpper` .</span><span class="sxs-lookup"><span data-stu-id="7d36e-143">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="7d36e-144">Bu yöntem <xref:System.Boolean> , geçerli dize örneğinin büyük harfli bir karakterle başlayıp başlamadığını belirten bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="7d36e-144">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="7d36e-145">Unicode standart, büyük harfli karakterleri küçük harfli karakterlerden ayırır.</span><span class="sxs-lookup"><span data-stu-id="7d36e-145">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="7d36e-146"><xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> `true` Bir karakter büyük harfli ise, yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="7d36e-146">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

   <span data-ttu-id="7d36e-147">`StartsWithUpper` , sınıfının bir üyesi gibi çağırabilmeniz için bir [genişletme yöntemi](../../csharp/programming-guide/classes-and-structs/extension-methods.md) olarak uygulanır <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="7d36e-147">`StartsWithUpper` is implemented as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

1. <span data-ttu-id="7d36e-148">Projenin hatasız derlendiğinden emin olmak için, menü çubuğunda yapı çözümü **Oluştur**' u seçin  >   veya <kbd>CTRL</kbd> + <kbd>SHIFT</kbd> + <kbd>B</kbd> ' ye basın.</span><span class="sxs-lookup"><span data-stu-id="7d36e-148">On the menu bar, select **Build** > **Build Solution** or press <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>B</kbd> to verify that the project compiles without error.</span></span>

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="7d36e-149">Çözüme bir konsol uygulaması ekleme</span><span class="sxs-lookup"><span data-stu-id="7d36e-149">Add a console app to the solution</span></span>

<span data-ttu-id="7d36e-150">Sınıf kitaplığını kullanan bir konsol uygulaması ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7d36e-150">Add a console application that uses the class library.</span></span> <span data-ttu-id="7d36e-151">Uygulama kullanıcıdan bir dize girmesini ister ve dizenin büyük harfli bir karakterle başlayıp başlamamadığını rapor eder.</span><span class="sxs-lookup"><span data-stu-id="7d36e-151">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="7d36e-152">Çözüme "gösterimi" adlı yeni bir .NET konsol uygulaması ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7d36e-152">Add a new .NET console application named "ShowCase" to the solution.</span></span>

   1. <span data-ttu-id="7d36e-153">**Çözüm Gezgini** çözüme sağ tıklayın ve   >  **Yeni proje** Ekle ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="7d36e-153">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="7d36e-154">**Yeni Proje Ekle** sayfasında, arama kutusuna **konsol** girin.</span><span class="sxs-lookup"><span data-stu-id="7d36e-154">On the **Add a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="7d36e-155">Dil listesinden **C#** veya **Visual Basic** seçin ve ardından platform listesinden **tüm platformlar** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="7d36e-155">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span>

   1. <span data-ttu-id="7d36e-156">**Konsol uygulaması** şablonunu seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="7d36e-156">Choose the **Console Application** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="7d36e-157">**Yeni projenizi yapılandırın** sayfasında, **Proje adı** kutusuna **gösterimi** girin.</span><span class="sxs-lookup"><span data-stu-id="7d36e-157">On the **Configure your new project** page, enter **ShowCase** in the **Project name** box.</span></span> <span data-ttu-id="7d36e-158">Ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="7d36e-158">Then choose **Next**.</span></span>

   1. <span data-ttu-id="7d36e-159">**Ek bilgiler** sayfasında, **hedef çerçeve** kutusunda **.NET 5,0 (geçerli)** seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="7d36e-159">On the **Additional information** page, select **.NET 5.0 (Current)** in the **Target Framework** box.</span></span> <span data-ttu-id="7d36e-160">Ardından **Oluştur**’u seçin.</span><span class="sxs-lookup"><span data-stu-id="7d36e-160">Then choose **Create**.</span></span>

1. <span data-ttu-id="7d36e-161">*Program.cs* veya *program. vb* dosyasının kod penceresinde, tüm kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7d36e-161">In the code window for the *Program.cs* or *Program.vb* file, replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/ShowCase/Program.vb":::

   <span data-ttu-id="7d36e-162">Kod, `row` konsol penceresine yazılan veri satırlarının sayısını korumak için değişkenini kullanır.</span><span class="sxs-lookup"><span data-stu-id="7d36e-162">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="7d36e-163">25 ' e eşit veya daha büyük olduğunda, kod konsol penceresini temizler ve kullanıcıya bir ileti görüntüler.</span><span class="sxs-lookup"><span data-stu-id="7d36e-163">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="7d36e-164">Program kullanıcıdan bir dize girmesini ister.</span><span class="sxs-lookup"><span data-stu-id="7d36e-164">The program prompts the user to enter a string.</span></span> <span data-ttu-id="7d36e-165">Dizenin büyük harfle başlatılıp başlatılmayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7d36e-165">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="7d36e-166">Kullanıcı bir dize girmeden <kbd>ENTER</kbd> tuşuna basarsa, uygulama sonlanır ve konsol penceresi kapanır.</span><span class="sxs-lookup"><span data-stu-id="7d36e-166">If the user presses the <kbd>Enter</kbd> key without entering a string, the application ends, and the console window closes.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="7d36e-167">Proje başvurusu Ekle</span><span class="sxs-lookup"><span data-stu-id="7d36e-167">Add a project reference</span></span>

<span data-ttu-id="7d36e-168">Başlangıçta, yeni konsol uygulaması projesi sınıf kitaplığına erişemez.</span><span class="sxs-lookup"><span data-stu-id="7d36e-168">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="7d36e-169">Sınıf kitaplığındaki yöntemleri çağırmasına izin vermek için, sınıf kitaplığı projesine bir proje başvurusu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7d36e-169">To allow it to call methods in the class library, create a project reference to the class library project.</span></span>

1. <span data-ttu-id="7d36e-170">**Çözüm Gezgini**, `ShowCase` projenin **Bağımlılıklar** düğümüne sağ tıklayın ve **proje başvurusu Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="7d36e-170">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node, and select **Add Project Reference**.</span></span>

   :::image type="content" source="media/library-with-visual-studio/add-reference-context-menu.png" alt-text="Visual Studio 'da başvuru bağlam menüsü Ekle":::

1. <span data-ttu-id="7d36e-172">**Başvuru Yöneticisi** Iletişim kutusunda **StringLibrary** projesini seçin ve **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="7d36e-172">In the **Reference Manager** dialog, select the **StringLibrary** project, and select **OK**.</span></span>

   :::image type="content" source="media/library-with-visual-studio/manage-project-references.png" alt-text="StringLibrary seçiliyken başvuru Yöneticisi iletişim kutusu":::

## <a name="run-the-app"></a><span data-ttu-id="7d36e-174">Uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="7d36e-174">Run the app</span></span>

1. <span data-ttu-id="7d36e-175">**Çözüm Gezgini** **, Gösterim projesine sağ** tıklayın ve bağlam menüsünde **Başlangıç projesi olarak ayarla** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="7d36e-175">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span>

   :::image type="content" source="media/library-with-visual-studio/set-startup-project-context-menu.png" alt-text="Başlangıç projesini ayarlamak için Visual Studio proje bağlam menüsü":::

1. <span data-ttu-id="7d36e-177"><kbd></kbd> + Hata ayıklama olmadan programı derlemek ve çalıştırmak için CTRL<kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7d36e-177">Press <kbd>Ctrl</kbd>+<kbd>F5</kbd> to compile and run the program without debugging.</span></span>

   :::image type="content" source="media/library-with-visual-studio/visual-studio-project-toolbar.png" alt-text="Hata ayıklama düğmesini gösteren Visual Studio proje araç çubuğu":::

1. <span data-ttu-id="7d36e-179">Dizeleri girerek ve <kbd>ENTER</kbd>'a basarak programı deneyin ve çıkmak için <kbd>ENTER</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7d36e-179">Try out the program by entering strings and pressing <kbd>Enter</kbd>, then press <kbd>Enter</kbd> to exit.</span></span>

   :::image type="content" source="media/library-with-visual-studio/run-showcase.png" alt-text="Gösterimi çalışan konsol penceresi":::

## <a name="additional-resources"></a><span data-ttu-id="7d36e-181">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="7d36e-181">Additional resources</span></span>

* [<span data-ttu-id="7d36e-182">.NET CLı ile Kitaplıklar geliştirme</span><span class="sxs-lookup"><span data-stu-id="7d36e-182">Develop libraries with the .NET CLI</span></span>](libraries.md)
* <span data-ttu-id="7d36e-183">[.NET Standard sürümleri ve destekledikleri platformlar](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="7d36e-183">[.NET Standard versions and the platforms they support](../../standard/net-standard.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="7d36e-184">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="7d36e-184">Next steps</span></span>

<span data-ttu-id="7d36e-185">Bu öğreticide, bir sınıf kitaplığı oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="7d36e-185">In this tutorial, you created a class library.</span></span> <span data-ttu-id="7d36e-186">Sonraki öğreticide, sınıf kitaplığını birim testi ile öğrenin.</span><span class="sxs-lookup"><span data-stu-id="7d36e-186">In the next tutorial, you learn how to unit test the class library.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7d36e-187">Visual Studio kullanarak .NET sınıf kitaplığı ile birim testi</span><span class="sxs-lookup"><span data-stu-id="7d36e-187">Unit test a .NET class library using Visual Studio</span></span>](testing-library-with-visual-studio.md)

<span data-ttu-id="7d36e-188">Ya da otomatik birim testlerini atlayabilir ve bir NuGet paketi oluşturarak kitaplığı nasıl paylaşacağınızı öğrenebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7d36e-188">Or you can skip automated unit testing and learn how to share the library by creating a NuGet package:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7d36e-189">Visual Studio kullanarak paket oluşturma ve yayımlama</span><span class="sxs-lookup"><span data-stu-id="7d36e-189">Create and publish a package using Visual Studio</span></span>](/nuget/quickstart/create-and-publish-a-package-using-visual-studio)

<span data-ttu-id="7d36e-190">Ya da bir konsol uygulamasını yayımlamayı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="7d36e-190">Or learn how to publish a console app.</span></span> <span data-ttu-id="7d36e-191">Konsol uygulamasını, bu öğreticide oluşturduğunuz çözümden yayımlarsanız, sınıf kitaplığı bir *. dll* dosyası olarak onunla birlikte görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7d36e-191">If you publish the console app from the solution you created in this tutorial, the class library goes with it as a *.dll* file.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7d36e-192">Visual Studio kullanarak bir .NET konsol uygulaması yayımlama</span><span class="sxs-lookup"><span data-stu-id="7d36e-192">Publish a .NET console application using Visual Studio</span></span>](publishing-with-visual-studio.md)
