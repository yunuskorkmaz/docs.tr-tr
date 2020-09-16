---
title: Mac için Visual Studio kullanarak .NET Standard sınıf kitaplığı oluşturma
description: Mac için Visual Studio kullanarak .NET Standard sınıf kitaplığı oluşturmayı öğrenin.
ms.date: 06/08/2020
ms.openlocfilehash: 433f6e0e2d784878c9a1616139b39ec56d695bcf
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537645"
---
# <a name="tutorial-create-a-net-standard-library-using-visual-studio-for-mac"></a><span data-ttu-id="c677e-103">Öğretici: Mac için Visual Studio kullanarak .NET Standard kitaplığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="c677e-103">Tutorial: Create a .NET Standard library using Visual Studio for Mac</span></span>

<span data-ttu-id="c677e-104">Bu öğreticide, tek bir dize işleme yöntemi içeren bir sınıf kitaplığı oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="c677e-104">In this tutorial, you create a class library that contains a single string-handling method.</span></span> <span data-ttu-id="c677e-105">Bunu, sınıfının bir üyesi gibi çağırabilmeniz için bir [genişletme yöntemi](../../csharp/programming-guide/classes-and-structs/extension-methods.md) olarak uygulamalısınız <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="c677e-105">You implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

<span data-ttu-id="c677e-106">Bir *sınıf kitaplığı* , bir uygulama tarafından çağrılan türleri ve yöntemleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c677e-106">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="c677e-107">.NET Standard 2,1 ' i hedefleyen bir sınıf kitaplığı, .NET Standard sürüm 2,1 ' ü destekleyen herhangi bir .NET uygulamasını hedefleyen bir uygulama tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c677e-107">A class library that targets .NET Standard 2.1 can be used by an application that targets any .NET implementation that supports version 2.1 of .NET Standard.</span></span> <span data-ttu-id="c677e-108">Sınıf kitaplığınızı bitirdiğinizde, bir üçüncü taraf bileşen olarak veya bir veya daha fazla uygulamayla paketlenmiş bileşen olarak dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c677e-108">When you finish your class library, you can distribute it as a third-party component or as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="c677e-109">Geri bildiriminiz çok değerli.</span><span class="sxs-lookup"><span data-stu-id="c677e-109">Your feedback is highly valued.</span></span> <span data-ttu-id="c677e-110">Mac için Visual Studio üzerinde geliştirme ekibine geri bildirimde bulunmak için kullanabileceğiniz iki yol vardır:</span><span class="sxs-lookup"><span data-stu-id="c677e-110">There are two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
>
> - <span data-ttu-id="c677e-111">Mac için Visual Studio, **Help**  >  menüden**sorun bildir** veya hoş geldiniz ekranından **sorun** bildir ' i seçerek bir hata raporu dosyalamayı sağlayan bir pencere açar.</span><span class="sxs-lookup"><span data-stu-id="c677e-111">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which opens a window for filing a bug report.</span></span> <span data-ttu-id="c677e-112">Geri bildiriminizi [Geliştirici Topluluğu](https://developercommunity.visualstudio.com/spaces/41/index.html) portalında izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c677e-112">You can track your feedback in the [Developer Community](https://developercommunity.visualstudio.com/spaces/41/index.html) portal.</span></span>
> - <span data-ttu-id="c677e-113">Öneride bulunmak için, **Help**  >  menüden**öneriler sağlama** veya hoş geldiniz ekranından [Mac için Visual Studio Geliştirici topluluğu Web sayfasına](https://developercommunity.visualstudio.com/content/idea/post.html?space=41)götüren **bir öneri** sağlama ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="c677e-113">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which takes you to the [Visual Studio for Mac Developer Community webpage](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c677e-114">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="c677e-114">Prerequisites</span></span>

* <span data-ttu-id="c677e-115">[Mac için Visual Studio sürüm 8,6 veya üstünü yükler](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span><span class="sxs-lookup"><span data-stu-id="c677e-115">[Install Visual Studio for Mac version 8.6 or later](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span> <span data-ttu-id="c677e-116">.NET Core ' u yüklemek için seçeneği belirleyin.</span><span class="sxs-lookup"><span data-stu-id="c677e-116">Select the option to install .NET Core.</span></span> <span data-ttu-id="c677e-117">.NET Core geliştirmesi için Xamarin 'in yüklenmesi isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c677e-117">Installing Xamarin is optional for .NET Core development.</span></span> <span data-ttu-id="c677e-118">Daha fazla bilgi için aşağıdaki kaynaklara bakın:</span><span class="sxs-lookup"><span data-stu-id="c677e-118">For more information, see the following resources:</span></span>

  * <span data-ttu-id="c677e-119">[Öğretici: Mac için Visual Studio yüklemesi](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="c677e-119">[Tutorial: Install Visual Studio for Mac](/visualstudio/mac/installation).</span></span>
  * <span data-ttu-id="c677e-120">[Desteklenen macOS sürümleri](../install/macos.md).</span><span class="sxs-lookup"><span data-stu-id="c677e-120">[Supported macOS versions](../install/macos.md).</span></span>
  * <span data-ttu-id="c677e-121">[Mac için Visual Studio tarafından desteklenen .NET Core sürümleri](/visualstudio/mac/net-core-support).</span><span class="sxs-lookup"><span data-stu-id="c677e-121">[.NET Core versions supported by Visual Studio for Mac](/visualstudio/mac/net-core-support).</span></span>

## <a name="create-a-solution-with-a-class-library-project"></a><span data-ttu-id="c677e-122">Sınıf kitaplığı projesiyle çözüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="c677e-122">Create a solution with a class library project</span></span>

<span data-ttu-id="c677e-123">Visual Studio çözümü bir veya daha fazla proje için kapsayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="c677e-123">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="c677e-124">Çözümde bir çözüm ve bir sınıf kitaplığı projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c677e-124">Create a solution and a class library project in the solution.</span></span> <span data-ttu-id="c677e-125">Aynı çözüme daha sonra ek ve ilgili projeler ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="c677e-125">You'll add additional, related projects to the same solution later.</span></span>

1. <span data-ttu-id="c677e-126">Mac için Visual Studio başlatın.</span><span class="sxs-lookup"><span data-stu-id="c677e-126">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="c677e-127">Başlangıç penceresinde **Yeni proje**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="c677e-127">In the start window, select **New Project**.</span></span>

1. <span data-ttu-id="c677e-128">**Çoklu platform** düğümünün altındaki **Yeni proje** iletişim kutusunda **kitaplık**' ı seçin, sonra **.NET Standard kitaplığı** şablonunu seçin ve **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="c677e-128">In the **New Project** dialog under the **Multi-Platform** node, select **Library**, then select the **.NET Standard Library** template, and select **Next**.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-new-project.png" alt-text="Yeni proje iletişim kutusu":::

1. <span data-ttu-id="c677e-130">**Yeni .NET Standard kitaplığınızı yapılandırın** iletişim kutusunda ".NET Standard 2,1" öğesini seçin ve **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="c677e-130">In the **Configure your new .NET Standard Library** dialog, choose ".NET Standard 2.1", and select **Next**.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/choose-net-std-21.png" alt-text=".NET Standard 2,1 seçin":::

1. <span data-ttu-id="c677e-132">"StringLibrary" projesini ve "ClassLibraryProjects" çözümünü adlandırın.</span><span class="sxs-lookup"><span data-stu-id="c677e-132">Name the project "StringLibrary" and the solution "ClassLibraryProjects".</span></span> <span data-ttu-id="c677e-133">**Çözüm dizini içinde bir proje dizini oluştur** ' un seçili kalsın.</span><span class="sxs-lookup"><span data-stu-id="c677e-133">Leave **Create a project directory within the solution directory** selected.</span></span> <span data-ttu-id="c677e-134">**Oluştur**’u seçin.</span><span class="sxs-lookup"><span data-stu-id="c677e-134">Select **Create**.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-new-project-options.png" alt-text="Yeni proje iletişim kutusu seçeneklerini Mac için Visual Studio":::

1. <span data-ttu-id="c677e-136">Ana menüden **Görünüm**  >  **bölmeleri**  >  **çözüm**' ü seçin ve paneli açık tutmak için Yerleştir simgesini seçin.</span><span class="sxs-lookup"><span data-stu-id="c677e-136">From the main menu, select **View** > **Pads** > **Solution**, and select the dock icon to keep the pad open.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/solution-dock-icon.png" alt-text="Çözüm paneli için yerleştirme simgesi":::

1. <span data-ttu-id="c677e-138">**Çözüm** panelinde, `StringLibrary` *Class1.cs*şablonu tarafından sunulan sınıf dosyasını açığa çıkarmak için düğümünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="c677e-138">In the **Solution** pad, expand the `StringLibrary` node to reveal the class file provided by the template, *Class1.cs*.</span></span> <span data-ttu-id="c677e-139"><kbd>CTRL</kbd>-dosyaya tıklayın, bağlam menüsünden **Yeniden Adlandır** ' ı seçin ve dosyayı *StringLibrary.cs*olarak yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="c677e-139"><kbd>ctrl</kbd>-click the file, select **Rename** from the context menu, and rename the file to *StringLibrary.cs*.</span></span> <span data-ttu-id="c677e-140">Dosyasını açın ve içeriğini şu kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="c677e-140">Open the file and replace the contents with the following code:</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

1. <span data-ttu-id="c677e-141">Dosyayı kaydetmek için <kbd>⌘</kbd><kbd>s</kbd> (<kbd>komut</kbd> + <kbd>S</kbd>) tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c677e-141">Press <kbd>⌘</kbd><kbd>S</kbd> (<kbd>command</kbd>+<kbd>S</kbd>) to save the file.</span></span>

1. <span data-ttu-id="c677e-142">**Hatalar** panelini açmak için IDE penceresinin altındaki kenar boşluğunda bulunan **hataları** seçin.</span><span class="sxs-lookup"><span data-stu-id="c677e-142">Select **Errors** in the margin at the bottom of the IDE window to open the **Errors** panel.</span></span> <span data-ttu-id="c677e-143">**Derleme çıkışı** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="c677e-143">Select the **Build Output** button.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-error-button.png" alt-text="Visual Studio Mac IDE 'nin hatalar düğmesini gösteren alt kenar boşluğu":::

1. <span data-ttu-id="c677e-145">Menüden **Build**  >  **Build All** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="c677e-145">Select **Build** > **Build All** from the menu.</span></span>

   <span data-ttu-id="c677e-146">Çözüm oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c677e-146">The solution builds.</span></span> <span data-ttu-id="c677e-147">Yapı çıktı paneli, yapılandırmanın başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c677e-147">The build output panel shows that the build is successful.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-build-panel.png" alt-text="Derleme başarılı iletisi ile hatalar panelinin Visual Studio Mac derleme çıkış bölmesi":::

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="c677e-149">Çözüme bir konsol uygulaması ekleme</span><span class="sxs-lookup"><span data-stu-id="c677e-149">Add a console app to the solution</span></span>

<span data-ttu-id="c677e-150">Sınıf kitaplığını kullanan bir konsol uygulaması ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c677e-150">Add a console application that uses the class library.</span></span> <span data-ttu-id="c677e-151">Uygulama kullanıcıdan bir dize girmesini ister ve dizenin büyük harfli bir karakterle başlayıp başlamamadığını rapor eder.</span><span class="sxs-lookup"><span data-stu-id="c677e-151">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="c677e-152">**Çözüm** panelinde, çözüme <kbd>CTRL</kbd>-tıklayın `ClassLibraryProjects` .</span><span class="sxs-lookup"><span data-stu-id="c677e-152">In the **Solution** pad, <kbd>ctrl</kbd>-click the `ClassLibraryProjects` solution.</span></span> <span data-ttu-id="c677e-153">**Web ve konsol**uygulaması şablonlarından şablonu seçerek yeni bir **konsol uygulaması** projesi ekleyin  >  **App** ve **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="c677e-153">Add a new **Console Application** project by selecting the template from the **Web and Console** > **App** templates, and select **Next**.</span></span>

1. <span data-ttu-id="c677e-154">**Hedef çerçeve** olarak **.NET Core 3,1** ' ı seçin ve **İleri ' yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="c677e-154">Select **.NET Core 3.1** as the **Target Framework** and select **Next**.</span></span>

1. <span data-ttu-id="c677e-155">Proje **tanıtımı**adlandırın.</span><span class="sxs-lookup"><span data-stu-id="c677e-155">Name the project **ShowCase**.</span></span> <span data-ttu-id="c677e-156">Projeyi çözümde oluşturmak için **Oluştur** ' u seçin.</span><span class="sxs-lookup"><span data-stu-id="c677e-156">Select **Create** to create the project in the solution.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/add-showcase-project.png" alt-text="Gösterimi projesi Ekle":::

1. <span data-ttu-id="c677e-158">*Program.cs* dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="c677e-158">Open the *Program.cs* file.</span></span> <span data-ttu-id="c677e-159">Kodu şu kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="c677e-159">Replace the code with the following code:</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   <span data-ttu-id="c677e-160">Program kullanıcıdan bir dize girmesini ister.</span><span class="sxs-lookup"><span data-stu-id="c677e-160">The program prompts the user to enter a string.</span></span> <span data-ttu-id="c677e-161">Dizenin büyük harfle başlatılıp başlatılmayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c677e-161">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="c677e-162">Kullanıcı bir dize girmeden <kbd>ENTER</kbd> tuşuna basarsa, uygulama sonlanır ve konsol penceresi kapanır.</span><span class="sxs-lookup"><span data-stu-id="c677e-162">If the user presses the <kbd>enter</kbd> key without entering a string, the application ends, and the console window closes.</span></span>

   <span data-ttu-id="c677e-163">Kod, `row` konsol penceresine yazılan veri satırlarının sayısını korumak için değişkenini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c677e-163">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="c677e-164">25 ' e eşit veya daha büyük olduğunda, kod konsol penceresini temizler ve kullanıcıya bir ileti görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c677e-164">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="c677e-165">Proje başvurusu Ekle</span><span class="sxs-lookup"><span data-stu-id="c677e-165">Add a project reference</span></span>

<span data-ttu-id="c677e-166">Başlangıçta, yeni konsol uygulaması projesi sınıf kitaplığına erişemez.</span><span class="sxs-lookup"><span data-stu-id="c677e-166">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="c677e-167">Sınıf kitaplığındaki yöntemleri çağırmasına izin vermek için, sınıf kitaplığı projesine bir proje başvurusu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c677e-167">To allow it to call methods in the class library, create a project reference to the class library project.</span></span>

1. <span data-ttu-id="c677e-168">**Çözümler** panelinde **, yeni Gösterim** projesinin **Bağımlılıklar** düğümüne <kbd>CTRL tuşuna</kbd>tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c677e-168">In the **Solutions** pad, <kbd>ctrl</kbd>-click the **Dependencies** node of the new **ShowCase** project.</span></span> <span data-ttu-id="c677e-169">Bağlam menüsünde **Başvuru Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="c677e-169">In the context menu, select **Add Reference**.</span></span>

1. <span data-ttu-id="c677e-170">**Başvurular** Iletişim kutusunda **StringLibrary** ' yi seçin ve **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="c677e-170">In the **References** dialog, select **StringLibrary** and select **OK**.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="c677e-171">Uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="c677e-171">Run the app</span></span>

1. <span data-ttu-id="c677e-172"><kbd>ctrl</kbd>' i seçerek Proje ' yi tıklatın ve bağlam menüsünden **projeyi Çalıştır** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="c677e-172"><kbd>ctrl</kbd>-click on the ShowCase project and select **Run project** from the context menu.</span></span>

1. <span data-ttu-id="c677e-173">Dizeleri girerek ve <kbd>ENTER</kbd>'a basarak programı deneyin ve çıkmak için <kbd>ENTER</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c677e-173">Try out the program by entering strings and pressing <kbd>enter</kbd>, then press <kbd>enter</kbd> to exit.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-console-window.png" alt-text="Uygulamanızın çalıştığını gösteren Mac için Visual Studio konsol penceresi":::

## <a name="additional-resources"></a><span data-ttu-id="c677e-175">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="c677e-175">Additional resources</span></span>

* [<span data-ttu-id="c677e-176">.NET Core CLI ile Kitaplıklar geliştirin</span><span class="sxs-lookup"><span data-stu-id="c677e-176">Develop libraries with the .NET Core CLI</span></span>](libraries.md)
* <span data-ttu-id="c677e-177">[.NET Standard sürümleri ve destekledikleri platformlar](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="c677e-177">[.NET Standard versions and the platforms they support](../../standard/net-standard.md).</span></span>
* [<span data-ttu-id="c677e-178">Mac için Visual Studio 2019 Sürüm Notları</span><span class="sxs-lookup"><span data-stu-id="c677e-178">Visual Studio 2019 for Mac Release Notes</span></span>](/visualstudio/releasenotes/vs2019-mac-relnotes)

## <a name="next-steps"></a><span data-ttu-id="c677e-179">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="c677e-179">Next steps</span></span>

<span data-ttu-id="c677e-180">Bu öğreticide, bir çözüm ve kitaplık projesi oluşturdunuz ve kitaplığı kullanan bir konsol uygulaması projesi eklediniz.</span><span class="sxs-lookup"><span data-stu-id="c677e-180">In this tutorial, you created a solution and a library project, and added a console app project that uses the library.</span></span> <span data-ttu-id="c677e-181">Sonraki öğreticide, çözüme bir birim testi projesi eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="c677e-181">In the next tutorial, you add a unit test project to the solution.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c677e-182">Mac için Visual Studio kullanarak .NET Core ile .NET Standard kitaplığı test etme</span><span class="sxs-lookup"><span data-stu-id="c677e-182">Test a .NET Standard library with .NET Core using Visual Studio for Mac</span></span>](testing-library-with-visual-studio-mac.md)
