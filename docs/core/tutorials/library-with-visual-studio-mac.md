---
title: Mac için Visual Studio kullanarak bir .NET sınıf kitaplığı oluşturma
description: Mac için Visual Studio kullanarak .NET sınıf kitaplığı oluşturmayı öğrenin.
ms.date: 11/30/2020
ms.openlocfilehash: 1b6b26de06d18d505fa6dde3ff9779a3dab3f1e6
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599321"
---
# <a name="tutorial-create-a-net-class-library-using-visual-studio-for-mac"></a><span data-ttu-id="475dc-103">Öğretici: Mac için Visual Studio kullanarak .NET sınıf kitaplığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="475dc-103">Tutorial: Create a .NET class library using Visual Studio for Mac</span></span>

<span data-ttu-id="475dc-104">Bu öğreticide, tek bir dize işleme yöntemi içeren bir sınıf kitaplığı oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="475dc-104">In this tutorial, you create a class library that contains a single string-handling method.</span></span>

<span data-ttu-id="475dc-105">Bir *sınıf kitaplığı* , bir uygulama tarafından çağrılan türleri ve yöntemleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="475dc-105">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="475dc-106">Kitaplık .NET Standard 2,0 hedefliyorsa, .NET Standard 2,0 ' yi destekleyen herhangi bir .NET uygulamasıyla (.NET Framework dahil) çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="475dc-106">If the library targets .NET Standard 2.0, it can be called by any .NET implementation (including .NET Framework) that supports .NET Standard 2.0.</span></span> <span data-ttu-id="475dc-107">Kitaplık .NET 5 ' i hedefliyorsa, .NET 5 ' i hedefleyen herhangi bir uygulama tarafından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="475dc-107">If the library targets .NET 5, it can be called by any application that targets .NET 5.</span></span> <span data-ttu-id="475dc-108">Bu öğreticide, .NET 5 ' in nasıl hedeflenecek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="475dc-108">This tutorial shows how to target .NET 5.</span></span>

> [!NOTE]
> <span data-ttu-id="475dc-109">Geri bildiriminiz çok değerli.</span><span class="sxs-lookup"><span data-stu-id="475dc-109">Your feedback is highly valued.</span></span> <span data-ttu-id="475dc-110">Mac için Visual Studio üzerinde geliştirme ekibine geri bildirimde bulunmak için kullanabileceğiniz iki yol vardır:</span><span class="sxs-lookup"><span data-stu-id="475dc-110">There are two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
>
> - <span data-ttu-id="475dc-111">Mac için Visual Studio, **Help**  >  menüden **sorun bildir** veya hoş geldiniz ekranından **sorun** bildir ' i seçerek bir hata raporu dosyalamayı sağlayan bir pencere açar.</span><span class="sxs-lookup"><span data-stu-id="475dc-111">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which opens a window for filing a bug report.</span></span> <span data-ttu-id="475dc-112">Geri bildiriminizi [Geliştirici Topluluğu](https://aka.ms/feedback/report?space=41) portalında izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="475dc-112">You can track your feedback in the [Developer Community](https://aka.ms/feedback/report?space=41) portal.</span></span>
> - <span data-ttu-id="475dc-113">Öneride bulunmak için, **Help**  >  menüden **öneriler sağlama** veya hoş geldiniz ekranından [Mac için Visual Studio Geliştirici topluluğu Web sayfasına](https://aka.ms/feedback/suggest?space=41)götüren **bir öneri** sağlama ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="475dc-113">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which takes you to the [Visual Studio for Mac Developer Community webpage](https://aka.ms/feedback/suggest?space=41).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="475dc-114">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="475dc-114">Prerequisites</span></span>

* <span data-ttu-id="475dc-115">[Mac için Visual Studio sürüm 8,8 veya üstünü yükler](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span><span class="sxs-lookup"><span data-stu-id="475dc-115">[Install Visual Studio for Mac version 8.8 or later](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span> <span data-ttu-id="475dc-116">.NET Core ' u yüklemek için seçeneği belirleyin.</span><span class="sxs-lookup"><span data-stu-id="475dc-116">Select the option to install .NET Core.</span></span> <span data-ttu-id="475dc-117">Xamarin 'in yüklenmesi .NET geliştirme için isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="475dc-117">Installing Xamarin is optional for .NET development.</span></span> <span data-ttu-id="475dc-118">Daha fazla bilgi için aşağıdaki kaynaklara bakın:</span><span class="sxs-lookup"><span data-stu-id="475dc-118">For more information, see the following resources:</span></span>

  * <span data-ttu-id="475dc-119">[Öğretici: Mac için Visual Studio yüklemesi](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="475dc-119">[Tutorial: Install Visual Studio for Mac](/visualstudio/mac/installation).</span></span>
  * <span data-ttu-id="475dc-120">[Desteklenen macOS sürümleri](../install/macos.md).</span><span class="sxs-lookup"><span data-stu-id="475dc-120">[Supported macOS versions](../install/macos.md).</span></span>
  * <span data-ttu-id="475dc-121">[Mac için Visual Studio tarafından desteklenen .NET sürümleri](/visualstudio/mac/net-core-support).</span><span class="sxs-lookup"><span data-stu-id="475dc-121">[.NET versions supported by Visual Studio for Mac](/visualstudio/mac/net-core-support).</span></span>

## <a name="create-a-solution-with-a-class-library-project"></a><span data-ttu-id="475dc-122">Sınıf kitaplığı projesiyle çözüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="475dc-122">Create a solution with a class library project</span></span>

<span data-ttu-id="475dc-123">Visual Studio çözümü bir veya daha fazla proje için kapsayıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="475dc-123">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="475dc-124">Çözümde bir çözüm ve bir sınıf kitaplığı projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="475dc-124">Create a solution and a class library project in the solution.</span></span> <span data-ttu-id="475dc-125">Aynı çözüme daha sonra ek ve ilgili projeler ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="475dc-125">You'll add additional, related projects to the same solution later.</span></span>

1. <span data-ttu-id="475dc-126">Mac için Visual Studio başlatın.</span><span class="sxs-lookup"><span data-stu-id="475dc-126">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="475dc-127">Başlangıç penceresinde **Yeni proje**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="475dc-127">In the start window, select **New Project**.</span></span>

1. <span data-ttu-id="475dc-128">**Yeni projeniz için bir şablon seçin** iletişim kutusunda **Web ve konsol**  >  **kitaplığı**  >  **sınıf kitaplığı**' nı seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="475dc-128">In the **Choose a template for your new project** dialog select **Web and Console** > **Library** > **Class Library**, and then select **Next**.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-new-project.png" alt-text="Yeni proje iletişim kutusu":::

1. <span data-ttu-id="475dc-130">**Yeni sınıf kitaplığınızı yapılandırın** iletişim kutusunda, **.NET 5,0**' i seçin ve **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="475dc-130">In the **Configure your new Class Library** dialog, choose **.NET 5.0**, and select **Next**.</span></span>

1. <span data-ttu-id="475dc-131">"StringLibrary" projesini ve "ClassLibraryProjects" çözümünü adlandırın.</span><span class="sxs-lookup"><span data-stu-id="475dc-131">Name the project "StringLibrary" and the solution "ClassLibraryProjects".</span></span> <span data-ttu-id="475dc-132">**Çözüm dizini içinde bir proje dizini oluştur** ' un seçili kalsın.</span><span class="sxs-lookup"><span data-stu-id="475dc-132">Leave **Create a project directory within the solution directory** selected.</span></span> <span data-ttu-id="475dc-133">**Oluştur**’u seçin.</span><span class="sxs-lookup"><span data-stu-id="475dc-133">Select **Create**.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-new-project-options.png" alt-text="Yeni proje iletişim kutusu seçeneklerini Mac için Visual Studio":::

1. <span data-ttu-id="475dc-135">Ana menüden **View**  >  **çözümü** görüntüle ' yi seçin ve paneli açık tutmak için Yerleştir simgesini seçin.</span><span class="sxs-lookup"><span data-stu-id="475dc-135">From the main menu, select **View** > **Solution**, and select the dock icon to keep the pad open.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/solution-dock-icon.png" alt-text="Çözüm paneli için yerleştirme simgesi":::

1. <span data-ttu-id="475dc-137">**Çözüm** panelinde, `StringLibrary` *Class1.cs* şablonu tarafından sunulan sınıf dosyasını açığa çıkarmak için düğümünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="475dc-137">In the **Solution** pad, expand the `StringLibrary` node to reveal the class file provided by the template, *Class1.cs*.</span></span> <span data-ttu-id="475dc-138"><kbd>CTRL</kbd>-dosyaya tıklayın, bağlam menüsünden **Yeniden Adlandır** ' ı seçin ve dosyayı *StringLibrary.cs* olarak yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="475dc-138"><kbd>ctrl</kbd>-click the file, select **Rename** from the context menu, and rename the file to *StringLibrary.cs*.</span></span> <span data-ttu-id="475dc-139">Dosyasını açın ve içeriğini şu kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="475dc-139">Open the file and replace the contents with the following code:</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

1. <span data-ttu-id="475dc-140">Dosyayı kaydetmek için <kbd>⌘</kbd><kbd>s</kbd> (<kbd>komut</kbd> + <kbd>S</kbd>) tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="475dc-140">Press <kbd>⌘</kbd><kbd>S</kbd> (<kbd>command</kbd>+<kbd>S</kbd>) to save the file.</span></span>

1. <span data-ttu-id="475dc-141">**Hatalar** panelini açmak için IDE penceresinin altındaki kenar boşluğunda bulunan **hataları** seçin.</span><span class="sxs-lookup"><span data-stu-id="475dc-141">Select **Errors** in the margin at the bottom of the IDE window to open the **Errors** panel.</span></span> <span data-ttu-id="475dc-142">**Derleme çıkışı** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="475dc-142">Select the **Build Output** button.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-error-button.png" alt-text="Visual Studio Mac IDE 'nin hatalar düğmesini gösteren alt kenar boşluğu":::

1. <span data-ttu-id="475dc-144">Menüden **Build**  >  **Build All** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="475dc-144">Select **Build** > **Build All** from the menu.</span></span>

   <span data-ttu-id="475dc-145">Çözüm oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="475dc-145">The solution builds.</span></span> <span data-ttu-id="475dc-146">Yapı çıktı paneli, yapılandırmanın başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="475dc-146">The build output panel shows that the build is successful.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-build-panel.png" alt-text="Derleme başarılı iletisi ile hatalar panelinin Visual Studio Mac derleme çıkış bölmesi":::

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="475dc-148">Çözüme bir konsol uygulaması ekleme</span><span class="sxs-lookup"><span data-stu-id="475dc-148">Add a console app to the solution</span></span>

<span data-ttu-id="475dc-149">Sınıf kitaplığını kullanan bir konsol uygulaması ekleyin.</span><span class="sxs-lookup"><span data-stu-id="475dc-149">Add a console application that uses the class library.</span></span> <span data-ttu-id="475dc-150">Uygulama kullanıcıdan bir dize girmesini ister ve dizenin büyük harfli bir karakterle başlayıp başlamamadığını rapor eder.</span><span class="sxs-lookup"><span data-stu-id="475dc-150">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="475dc-151">**Çözüm** panelinde, çözüme <kbd>CTRL</kbd>-tıklayın `ClassLibraryProjects` .</span><span class="sxs-lookup"><span data-stu-id="475dc-151">In the **Solution** pad, <kbd>ctrl</kbd>-click the `ClassLibraryProjects` solution.</span></span> <span data-ttu-id="475dc-152">**Web ve konsol** uygulaması şablonlarından şablonu seçerek yeni bir **konsol uygulaması** projesi ekleyin  >  **App** ve **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="475dc-152">Add a new **Console Application** project by selecting the template from the **Web and Console** > **App** templates, and select **Next**.</span></span>

1. <span data-ttu-id="475dc-153">**Hedef çerçeve** olarak **.NET 5,0** ' i seçin ve **İleri ' yi** seçin.</span><span class="sxs-lookup"><span data-stu-id="475dc-153">Select **.NET 5.0** as the **Target Framework** and select **Next**.</span></span>

1. <span data-ttu-id="475dc-154">Proje **tanıtımı** adlandırın.</span><span class="sxs-lookup"><span data-stu-id="475dc-154">Name the project **ShowCase**.</span></span> <span data-ttu-id="475dc-155">Projeyi çözümde oluşturmak için **Oluştur** ' u seçin.</span><span class="sxs-lookup"><span data-stu-id="475dc-155">Select **Create** to create the project in the solution.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/add-showcase-project.png" alt-text="Gösterimi projesi Ekle":::

1. <span data-ttu-id="475dc-157">*Program.cs* dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="475dc-157">Open the *Program.cs* file.</span></span> <span data-ttu-id="475dc-158">Kodu şu kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="475dc-158">Replace the code with the following code:</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   <span data-ttu-id="475dc-159">Program kullanıcıdan bir dize girmesini ister.</span><span class="sxs-lookup"><span data-stu-id="475dc-159">The program prompts the user to enter a string.</span></span> <span data-ttu-id="475dc-160">Dizenin büyük harfle başlatılıp başlatılmayacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="475dc-160">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="475dc-161">Kullanıcı bir dize girmeden <kbd>ENTER</kbd> tuşuna basarsa, uygulama sonlanır ve konsol penceresi kapanır.</span><span class="sxs-lookup"><span data-stu-id="475dc-161">If the user presses the <kbd>enter</kbd> key without entering a string, the application ends, and the console window closes.</span></span>

   <span data-ttu-id="475dc-162">Kod, `row` konsol penceresine yazılan veri satırlarının sayısını korumak için değişkenini kullanır.</span><span class="sxs-lookup"><span data-stu-id="475dc-162">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="475dc-163">25 ' e eşit veya daha büyük olduğunda, kod konsol penceresini temizler ve kullanıcıya bir ileti görüntüler.</span><span class="sxs-lookup"><span data-stu-id="475dc-163">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="475dc-164">Proje başvurusu Ekle</span><span class="sxs-lookup"><span data-stu-id="475dc-164">Add a project reference</span></span>

<span data-ttu-id="475dc-165">Başlangıçta, yeni konsol uygulaması projesi sınıf kitaplığına erişemez.</span><span class="sxs-lookup"><span data-stu-id="475dc-165">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="475dc-166">Sınıf kitaplığındaki yöntemleri çağırmasına izin vermek için, sınıf kitaplığı projesine bir proje başvurusu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="475dc-166">To allow it to call methods in the class library, create a project reference to the class library project.</span></span>

1. <span data-ttu-id="475dc-167">**Çözümler** panelinde **, yeni Gösterim** projesinin **Bağımlılıklar** düğümüne <kbd>CTRL tuşuna</kbd>tıklayın.</span><span class="sxs-lookup"><span data-stu-id="475dc-167">In the **Solutions** pad, <kbd>ctrl</kbd>-click the **Dependencies** node of the new **ShowCase** project.</span></span> <span data-ttu-id="475dc-168">Bağlam menüsünde **Başvuru Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="475dc-168">In the context menu, select **Add Reference**.</span></span>

1. <span data-ttu-id="475dc-169">**Başvurular** Iletişim kutusunda **StringLibrary** ' yi seçin ve **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="475dc-169">In the **References** dialog, select **StringLibrary** and select **OK**.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="475dc-170">Uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="475dc-170">Run the app</span></span>

1. <span data-ttu-id="475dc-171"><kbd>CTRL tuşunu basılı</kbd>olarak **projeye tıklayın** ve bağlam menüsünden **projeyi Çalıştır** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="475dc-171"><kbd>ctrl</kbd>-click the **ShowCase** project and select **Run project** from the context menu.</span></span>

1. <span data-ttu-id="475dc-172">Dizeleri girerek ve <kbd>ENTER</kbd>'a basarak programı deneyin ve çıkmak için <kbd>ENTER</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="475dc-172">Try out the program by entering strings and pressing <kbd>enter</kbd>, then press <kbd>enter</kbd> to exit.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-console-window.png" alt-text="Uygulamanızın çalıştığını gösteren Mac için Visual Studio konsol penceresi":::

## <a name="additional-resources"></a><span data-ttu-id="475dc-174">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="475dc-174">Additional resources</span></span>

* [<span data-ttu-id="475dc-175">.NET CLı ile Kitaplıklar geliştirme</span><span class="sxs-lookup"><span data-stu-id="475dc-175">Develop libraries with the .NET CLI</span></span>](libraries.md)
* [<span data-ttu-id="475dc-176">Mac için Visual Studio 2019 Sürüm Notları</span><span class="sxs-lookup"><span data-stu-id="475dc-176">Visual Studio 2019 for Mac Release Notes</span></span>](/visualstudio/releasenotes/vs2019-mac-relnotes)
* <span data-ttu-id="475dc-177">[.NET Standard sürümleri ve destekledikleri platformlar](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="475dc-177">[.NET Standard versions and the platforms they support](../../standard/net-standard.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="475dc-178">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="475dc-178">Next steps</span></span>

<span data-ttu-id="475dc-179">Bu öğreticide, bir çözüm ve kitaplık projesi oluşturdunuz ve kitaplığı kullanan bir konsol uygulaması projesi eklediniz.</span><span class="sxs-lookup"><span data-stu-id="475dc-179">In this tutorial, you created a solution and a library project, and added a console app project that uses the library.</span></span> <span data-ttu-id="475dc-180">Sonraki öğreticide, çözüme bir birim testi projesi eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="475dc-180">In the next tutorial, you add a unit test project to the solution.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="475dc-181">Mac için Visual Studio kullanarak .NET sınıf kitaplığı test etme</span><span class="sxs-lookup"><span data-stu-id="475dc-181">Test a .NET class library using Visual Studio for Mac</span></span>](testing-library-with-visual-studio-mac.md)
