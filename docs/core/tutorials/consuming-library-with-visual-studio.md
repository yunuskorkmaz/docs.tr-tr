---
title: Visual Studio 2017’de bir .NET Standard kitaplığı kullanma
description: Visual Studio 2017 ile başka bir sınıf kitaplığının üyelerini çağıran bir .NET Core uygulaması oluşturun.
author: BillWagner
ms.author: wiwagn
ms.date: 06/05/2018
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: cfceb7ba384a28a09f172032f6edb6f5e495e9c0
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73420909"
---
# <a name="consume-a-net-standard-library-in-visual-studio-2017"></a><span data-ttu-id="da0c1-103">Visual Studio 2017’de bir .NET Standard kitaplığı kullanma</span><span class="sxs-lookup"><span data-stu-id="da0c1-103">Consume a .NET Standard library in Visual Studio 2017</span></span>

<span data-ttu-id="da0c1-104">[Visual studio 2017 ' de .NET Core ile bir C# sınıf kitaplığı oluşturma](./library-with-visual-studio.md) veya [Visual Studio 2017 ' de .NET Core ile bir Visual Basic sınıf kitaplığı](vb-library-with-visual-studio.md)oluşturma bölümündeki adımları izleyerek bir .NET Standard sınıf kitaplığı oluşturduktan sonra, bu, içinde [test edilmiştir Visual Studio 2017 ' de .NET Core ile bir sınıf kitaplığını test etme](testing-library-with-visual-studio.md)ve kitaplığın yayın sürümü oluşturma bir sonraki adım, arayanlara hazır hale getirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="da0c1-104">Once you've created a .NET Standard class library by following the steps in [Building a C# class library with .NET Core in Visual Studio 2017](./library-with-visual-studio.md) or [Building a Visual Basic class library with .NET Core in Visual Studio 2017](vb-library-with-visual-studio.md), tested it in [Testing a class library with .NET Core in Visual Studio 2017](testing-library-with-visual-studio.md), and built a Release version of the library, the next step is to make it available to callers.</span></span> <span data-ttu-id="da0c1-105">Bunu iki şekilde yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="da0c1-105">You can do this in two ways:</span></span>

* <span data-ttu-id="da0c1-106">Kitaplık tek bir çözüm tarafından kullanılacaksa (örneğin, tek bir büyük uygulamadaki bir bileşen ise) çözümünüze bir proje olarak dahil edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da0c1-106">If the library will be used by a single solution (for example, if it's a component in a single large application), you can include it as a project in your solution.</span></span>

* <span data-ttu-id="da0c1-107">Kitaplığın genel olarak erişilebilir olacağı bir NuGet paketi olarak dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da0c1-107">If the library will be generally accessible, you can distribute it as a NuGet package.</span></span>

## <a name="including-a-library-as-a-project-in-a-solution"></a><span data-ttu-id="da0c1-108">Bir kitaplığı bir çözüme proje olarak dahil etme</span><span class="sxs-lookup"><span data-stu-id="da0c1-108">Including a library as a project in a solution</span></span>

<span data-ttu-id="da0c1-109">Birim testlerini, sınıf kitaplısınız ile aynı çözümde bulundurmadığınız gibi, uygulamanızı bu çözümün bir parçası olarak dahil edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da0c1-109">Just as you included unit tests in the same solution as your class library, you can include your application as part of that solution.</span></span> <span data-ttu-id="da0c1-110">Örneğin, sınıf kitaplığınızı, kullanıcıdan ilk karakterinin büyük harf olup olmadığını belirten bir dize ve rapor girmesini isteyen bir konsol uygulamasında kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="da0c1-110">For example, you can use your class library in a console application that prompts the user to enter a string and reports whether its first character is uppercase:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="ctabcsharp"></a>[<span data-ttu-id="da0c1-111">C#</span><span class="sxs-lookup"><span data-stu-id="da0c1-111">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="da0c1-112">[Visual Studio 'da .NET Core ile bir C# sınıf kitaplığı oluşturma 2017](./library-with-visual-studio.md) konusunun oluşturduğunuz `ClassLibraryProjects` çözümünü açın.</span><span class="sxs-lookup"><span data-stu-id="da0c1-112">Open the `ClassLibraryProjects` solution you created in the [Building a C# Class Library with .NET Core in Visual Studio 2017](./library-with-visual-studio.md) topic.</span></span> <span data-ttu-id="da0c1-113">**Çözüm Gezgini**, **classlibraryprojects** çözümüne sağ tıklayın ve bağlam menüsünden **Yeni > proje** **Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="da0c1-113">In **Solution Explorer**, right-click the **ClassLibraryProjects** solution and select **Add** > **New Project** from the context menu.</span></span>

1. <span data-ttu-id="da0c1-114">**Yeni Proje Ekle** iletişim kutusunda, **görsel C#**  düğümünü genişletin ve ardından **konsol uygulaması (.NET Core)** proje şablonu tarafından izlenen **.NET Core** düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="da0c1-114">In the **Add New Project** dialog, expand the **Visual C#** node and select the **.NET Core** node followed by the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="da0c1-115">**Ad** metin kutusuna "gösterimi" yazın ve **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="da0c1-115">In the **Name** text box, type "ShowCase", and select the **OK** button.</span></span>

   ![Visual Studio yeni proje Ekle iletişim kutusu-C#](./media/consuming-library-with-visual-studio/add-new-project-dialog.png)

1. <span data-ttu-id="da0c1-117">**Çözüm Gezgini** **, Gösterim projesine sağ** tıklayın ve bağlam menüsünde **Başlangıç projesi olarak ayarla** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="da0c1-117">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span>

   ![Başlangıç projesini ayarlamaya yönelik Visual Studio proje bağlam menüsü-C#](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. <span data-ttu-id="da0c1-119">Başlangıçta, projenizin sınıf kitaplığınıza erişimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="da0c1-119">Initially, your project doesn't have access to your class library.</span></span> <span data-ttu-id="da0c1-120">Sınıf kitaplığınızdaki yöntemleri çağırmasına izin vermek için, sınıf kitaplığına bir başvuru oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="da0c1-120">To allow it to call methods in your class library, you create a reference to the class library.</span></span> <span data-ttu-id="da0c1-121">**Çözüm Gezgini**, `ShowCase` projenin **Bağımlılıklar** düğümüne sağ tıklayın ve **Başvuru Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="da0c1-121">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node and select **Add Reference**.</span></span>

   ![Visual Studio proje başvuru ekleme bağlam menüsü-C#](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="da0c1-123">**Başvuru Yöneticisi** Iletişim kutusunda **StringLibrary**, sınıf kitaplığı projeniz ' i seçin ve **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="da0c1-123">In the **Reference Manager** dialog, select **StringLibrary**, your class library project, and select the **OK** button.</span></span>

   ![Visual Studio başvuruları Yönet iletişim kutusu-C#](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. <span data-ttu-id="da0c1-125">*Program.cs* dosyası için kod penceresinde, tüm kodu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="da0c1-125">In the code window for the *Program.cs* file, replace all of the code with the following code:</span></span>

   [!CODE-csharp[UsingClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]

   <span data-ttu-id="da0c1-126">Kod, konsol penceresine yazılan veri satırlarının sayısını korumak için `row` değişkenini kullanır.</span><span class="sxs-lookup"><span data-stu-id="da0c1-126">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="da0c1-127">25 ' e eşit veya daha büyük olduğunda, kod konsol penceresini temizler ve kullanıcıya bir ileti görüntüler.</span><span class="sxs-lookup"><span data-stu-id="da0c1-127">Whenever it is greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="da0c1-128">Program kullanıcıdan bir dize girmesini ister.</span><span class="sxs-lookup"><span data-stu-id="da0c1-128">The program prompts the user to enter a string.</span></span> <span data-ttu-id="da0c1-129">Dizenin büyük harfle başlatılıp başlatılmayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="da0c1-129">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="da0c1-130">Kullanıcı bir dize girmeden ENTER tuşuna basarsa, uygulama sonlanır ve konsol penceresi kapanır.</span><span class="sxs-lookup"><span data-stu-id="da0c1-130">If the user presses the Enter key without entering a string, the application terminates, and the console window closes.</span></span>

1. <span data-ttu-id="da0c1-131">Gerekirse, `ShowCase` projesinin **hata ayıklama** sürümünü derlemek için araç çubuğunu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="da0c1-131">If necessary, change the toolbar to compile the **Debug** release of the `ShowCase` project.</span></span> <span data-ttu-id="da0c1-132">**Gösterimi** düğmesindeki yeşil oku seçerek programı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="da0c1-132">Compile and run the program by selecting the green arrow on the **ShowCase** button.</span></span>

   ![Hata ayıklama düğmesini gösteren Visual Studio proje araç çubuğu-C#](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)

# <a name="visual-basictabvb"></a>[<span data-ttu-id="da0c1-134">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="da0c1-134">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="da0c1-135">[Visual Studio 'da Visual Basic ve .NET Core ile bir sınıf kitaplığı oluşturma 2017](vb-library-with-visual-studio.md) konusunun oluşturduğunuz `ClassLibraryProjects` çözümünü açın.</span><span class="sxs-lookup"><span data-stu-id="da0c1-135">Open the `ClassLibraryProjects` solution you created in the [Building a class Library with Visual Basic and .NET Core in Visual Studio 2017](vb-library-with-visual-studio.md) topic.</span></span> <span data-ttu-id="da0c1-136">**Çözüm Gezgini**, **classlibraryprojects** çözümüne sağ tıklayın ve bağlam menüsünden **Yeni > proje** **Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="da0c1-136">In **Solution Explorer**, right-click the **ClassLibraryProjects** solution and select **Add** > **New Project** from the context menu.</span></span>

1. <span data-ttu-id="da0c1-137">**Yeni Proje Ekle** iletişim kutusunda **Visual Basic** düğümünü genişletin ve ardından **konsol uygulaması (.NET Core)** proje şablonu tarafından izlenen **.NET Core** düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="da0c1-137">In the **Add New Project** dialog, expand the **Visual Basic** node and select the **.NET Core** node followed by the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="da0c1-138">**Ad** metin kutusuna "gösterimi" yazın ve **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="da0c1-138">In the **Name** text box, type "ShowCase", and select the **OK** button.</span></span>

   ![Visual Studio yeni proje Ekle iletişim kutusu-Visual Basic](./media/consuming-library-with-visual-studio/add-new-vb-project-dialog.png)

1. <span data-ttu-id="da0c1-140">**Çözüm Gezgini** **, Gösterim projesine sağ** tıklayın ve bağlam menüsünde **Başlangıç projesi olarak ayarla** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="da0c1-140">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span> 

   ![Başlangıç projesini ayarlamaya yönelik Visual Studio proje bağlam menüsü-Visual Basic](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. <span data-ttu-id="da0c1-142">Başlangıçta, projenizin sınıf kitaplığınıza erişimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="da0c1-142">Initially, your project doesn't have access to your class library.</span></span> <span data-ttu-id="da0c1-143">Sınıf kitaplığınızdaki yöntemleri çağırmasına izin vermek için, sınıf kitaplığına bir başvuru oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="da0c1-143">To allow it to call methods in your class library, you create a reference to the class library.</span></span> <span data-ttu-id="da0c1-144">**Çözüm Gezgini**, `ShowCase` projenin **Bağımlılıklar** düğümüne sağ tıklayın ve **Başvuru Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="da0c1-144">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node and select **Add Reference**.</span></span>

   ![Visual Studio proje başvuru ekleme bağlam menüsü-Visual Basic](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="da0c1-146">**Başvuru Yöneticisi** Iletişim kutusunda **StringLibrary**, sınıf kitaplığı projeniz ' i seçin ve **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="da0c1-146">In the **Reference Manager** dialog, select **StringLibrary**, your class library project, and select the **OK** button.</span></span>

   ![Visual Studio başvuruları Yönet iletişim kutusu-Visual Basic](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. <span data-ttu-id="da0c1-148">*Program. vb* dosyasının kod penceresinde, tüm kodu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="da0c1-148">In the code window for the *Program.vb* file, replace all of the code with the following code:</span></span>

    [!CODE-vb[UsingClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   <span data-ttu-id="da0c1-149">Kod, konsol penceresine yazılan veri satırlarının sayısını korumak için `row` değişkenini kullanır.</span><span class="sxs-lookup"><span data-stu-id="da0c1-149">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="da0c1-150">25 ' e eşit veya daha büyük olduğunda, kod konsol penceresini temizler ve kullanıcıya bir ileti görüntüler.</span><span class="sxs-lookup"><span data-stu-id="da0c1-150">Whenever it is greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="da0c1-151">Program kullanıcıdan bir dize girmesini ister.</span><span class="sxs-lookup"><span data-stu-id="da0c1-151">The program prompts the user to enter a string.</span></span> <span data-ttu-id="da0c1-152">Dizenin büyük harfle başlatılıp başlatılmayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="da0c1-152">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="da0c1-153">Kullanıcı bir dize girmeden ENTER tuşuna basarsa, uygulama sonlanır ve konsol penceresi kapanır.</span><span class="sxs-lookup"><span data-stu-id="da0c1-153">If the user presses the Enter key without entering a string, the application terminates, and the console window closes.</span></span>

1. <span data-ttu-id="da0c1-154">Gerekirse, `ShowCase` projesinin **hata ayıklama** sürümünü derlemek için araç çubuğunu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="da0c1-154">If necessary, change the toolbar to compile the **Debug** release of the `ShowCase` project.</span></span> <span data-ttu-id="da0c1-155">**Gösterimi** düğmesindeki yeşil oku seçerek programı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="da0c1-155">Compile and run the program by selecting the green arrow on the **ShowCase** button.</span></span>

   ![Araç çubuğunda Hata Ayıkla-Visual Basic](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)

---

<span data-ttu-id="da0c1-157">[Visual studio 2017 ile Merhaba Dünya uygulamanızda hata ayıklama](debugging-with-visual-studio.md) ve [Merhaba Dünya uygulamanızı Visual Studio 2017 ile yayımlama](publishing-with-visual-studio.md)bölümündeki adımları izleyerek, bu kitaplığı kullanan uygulamayı ayıklayabilir ve yayımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da0c1-157">You can debug and publish the application that uses this library by following the steps in [Debugging your Hello World application with Visual Studio 2017](debugging-with-visual-studio.md) and [Publishing your Hello World Application with Visual Studio 2017](publishing-with-visual-studio.md).</span></span>

## <a name="distributing-the-library-in-a-nuget-package"></a><span data-ttu-id="da0c1-158">Kitaplığı bir NuGet paketinde dağıtma</span><span class="sxs-lookup"><span data-stu-id="da0c1-158">Distributing the library in a NuGet package</span></span>

<span data-ttu-id="da0c1-159">Sınıf kitaplığınızı, bir NuGet paketi olarak yayımlayarak geniş oranda kullanılabilir hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da0c1-159">You can make your class library widely available by publishing it as a NuGet package.</span></span> <span data-ttu-id="da0c1-160">Visual Studio, NuGet paketlerinin oluşturulmasını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="da0c1-160">Visual Studio does not support the creation of NuGet packages.</span></span> <span data-ttu-id="da0c1-161">Bir tane oluşturmak için [`dotnet` komut satırı yardımcı programını](../tools/dotnet.md)kullanın:</span><span class="sxs-lookup"><span data-stu-id="da0c1-161">To create one, you use the [`dotnet` command line utility](../tools/dotnet.md):</span></span>

1. <span data-ttu-id="da0c1-162">Bir konsol penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="da0c1-162">Open a console window.</span></span> <span data-ttu-id="da0c1-163">Örneğin, Windows görev çubuğundaki bir **şeyi bana sor** metin kutusunda `Command Prompt` (veya short için `cmd`) girin ve **komut istemi** masaüstü uygulamasını seçerek veya arama sonuçlarında seçiliyse ENTER tuşuna basarak bir konsol penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="da0c1-163">For example in the **Ask me anything** text box in the Windows taskbar, enter `Command Prompt` (or `cmd` for short), and open a console window by either selecting the **Command Prompt** desktop app or pressing Enter if it's selected in the search results.</span></span>

1. <span data-ttu-id="da0c1-164">Kitaplığınızın proje dizinine gidin.</span><span class="sxs-lookup"><span data-stu-id="da0c1-164">Navigate to your library's project directory.</span></span> <span data-ttu-id="da0c1-165">Normal dosya konumunu yeniden yapılandırmadığınız takdirde, bu, bu,, bu,, bu,, bu,, bu, The *Studio 2017 \ projeleri*</span><span class="sxs-lookup"><span data-stu-id="da0c1-165">Unless you've reconfigured the typical file location, it's in the *Documents\Visual Studio 2017\Projects\ClassLibraryProjects\StringLibrary* directory.</span></span> <span data-ttu-id="da0c1-166">Dizin, kaynak kodunuzu ve *StringLibrary. csproj*proje dosyasını içerir.</span><span class="sxs-lookup"><span data-stu-id="da0c1-166">The directory contains your source code and a project file, *StringLibrary.csproj*.</span></span>

1. <span data-ttu-id="da0c1-167">Komutu `dotnet pack --no-build`verin.</span><span class="sxs-lookup"><span data-stu-id="da0c1-167">Issue the command `dotnet pack --no-build`.</span></span> <span data-ttu-id="da0c1-168">`dotnet` yardımcı programı, *. nupkg* uzantılı bir paket oluşturur.</span><span class="sxs-lookup"><span data-stu-id="da0c1-168">The `dotnet` utility generates a package with a *.nupkg* extension.</span></span>

   > [!TIP]
   > <span data-ttu-id="da0c1-169">*DotNet. exe* IÇEREN Dizin yolunuzda değilse, konsol penceresine `where dotnet.exe` girerek konumunu bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da0c1-169">If the directory that contains *dotnet.exe* is not in your PATH, you can find its location by entering `where dotnet.exe` in the console window.</span></span>

<span data-ttu-id="da0c1-170">NuGet paketleri oluşturma hakkında daha fazla bilgi için bkz. [platformlar arası araçlarla NuGet paketi oluşturma](../deploying/creating-nuget-packages.md).</span><span class="sxs-lookup"><span data-stu-id="da0c1-170">For more information on creating NuGet packages, see [How to Create a NuGet Package with Cross Platform Tools](../deploying/creating-nuget-packages.md).</span></span>
