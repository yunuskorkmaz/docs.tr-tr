---
title: Mac için Visual Studio kullanarak macOS üzerinde tam bir .NET Core çözümü oluşturma
description: Bu konu, yeniden kullanılabilir kitaplık ve birim testleri içeren bir .NET Core çözümü oluşturma sürecinde açıklanmaktadır.
keywords: .NET, .NET core macOS, Mac
author: guardrex
ms.author: mairaw
ms.date: 06/12/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 6945bedf-5bf3-4955-8588-83fb87511b79
ms.workload:
- dotnetcore
ms.openlocfilehash: 6d8f89af14167e57b7f1b3b1d6ddce5cae8f6446
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="building-a-complete-net-core-solution-on-macos-using-visual-studio-for-mac"></a><span data-ttu-id="d1640-104">Mac için Visual Studio kullanarak macOS üzerinde tam bir .NET Core çözümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="d1640-104">Building a complete .NET Core solution on macOS using Visual Studio for Mac</span></span>

<span data-ttu-id="d1640-105">Mac için Visual Studio .NET Core uygulamaları geliştirmek için bir tam özellikli tümleşik geliştirme ortamı (IDE) sağlar.</span><span class="sxs-lookup"><span data-stu-id="d1640-105">Visual Studio for Mac provides a full-featured Integrated Development Environment (IDE) for developing .NET Core applications.</span></span> <span data-ttu-id="d1640-106">Bu konu, yeniden kullanılabilir kitaplık ve birim testleri içeren bir .NET Core çözümü oluşturma sürecinde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d1640-106">This topic walks you through building a .NET Core solution that includes a reusable library and unit testing.</span></span>

<span data-ttu-id="d1640-107">Bu öğretici, bir arama sözcüğü ve kullanıcıdan bir metin dizesi kabul eder, arama Word'ün bir sınıf kitaplığı'nda bir yöntem kullanarak dize görünür ve kullanıcıya sonucu döndürür sayısını sayar bir uygulama oluşturmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="d1640-107">This tutorial shows you how to create an application that accepts a search word and a string of text from the user, counts the number of times the search word appears in the string using a method in a class library, and returns the result to the user.</span></span> <span data-ttu-id="d1640-108">Çözüm ayrıca birim teste dayalı geliştirme (TDD) kavramları giriş olarak için sınıf kitaplığı testi içerir.</span><span class="sxs-lookup"><span data-stu-id="d1640-108">The solution also includes unit testing for the class library as an introduction to test-driven development (TDD) concepts.</span></span> <span data-ttu-id="d1640-109">Bu öğreticiyi tam bir örnek üzerinden geçmek isterseniz, indirme [örnek çözümü](https://github.com/dotnet/samples/blob/master/core/tutorials/using-on-mac-vs-full-solution/WordCounter).</span><span class="sxs-lookup"><span data-stu-id="d1640-109">If you prefer to proceed through the tutorial with a complete sample, download the [sample solution](https://github.com/dotnet/samples/blob/master/core/tutorials/using-on-mac-vs-full-solution/WordCounter).</span></span> <span data-ttu-id="d1640-110">Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="d1640-110">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

> [!NOTE]
> <span data-ttu-id="d1640-111">Geri bildiriminiz yüksek değerli.</span><span class="sxs-lookup"><span data-stu-id="d1640-111">Your feedback is highly valued.</span></span> <span data-ttu-id="d1640-112">Mac için Visual Studio geliştirme ekibine geribildirim sağlayabilir iki yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="d1640-112">There are two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
> * <span data-ttu-id="d1640-113">Mac için Visual Studio'da seçin **yardımcı** > **bir sorun bildirmek** menüsünden veya **bir sorun bildirmek** Karşılama ekranında dosyalama için bir pencere açan bir hata raporu.</span><span class="sxs-lookup"><span data-stu-id="d1640-113">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which opens a window for filing a bug report.</span></span> <span data-ttu-id="d1640-114">Geri bildiriminizi [Geliştirici Topluluğu](https://developercommunity.visualstudio.com/spaces/41/index.html) portalında izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1640-114">You can track your feedback in the [Developer Community](https://developercommunity.visualstudio.com/spaces/41/index.html) portal.</span></span>
> * <span data-ttu-id="d1640-115">Bir öneride bulunmak için seçin **yardımcı** > **bir öneride bulunmak** menüsünden veya **bir öneride bulunmak** Karşılama ekranında aldığı, [ Visual Studio Web sayfası Mac UserVoice için](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac).</span><span class="sxs-lookup"><span data-stu-id="d1640-115">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which takes you to the [Visual Studio for Mac UserVoice webpage](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d1640-116">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="d1640-116">Prerequisites</span></span>

- <span data-ttu-id="d1640-117">(.NET Core 1.1 çalıştırılıyorsa) OpenSSL: bkz [.NET Core Mac üzerinde önkoşulları](../macos-prerequisites.md) konu.</span><span class="sxs-lookup"><span data-stu-id="d1640-117">OpenSSL (if running .NET Core 1.1): See the [Prerequisites for .NET Core on Mac](../macos-prerequisites.md) topic.</span></span>
- [<span data-ttu-id="d1640-118">.NET core SDK 1.1 veya üstü</span><span class="sxs-lookup"><span data-stu-id="d1640-118">.NET Core SDK 1.1 or later</span></span>](https://www.microsoft.com/net/core#macos)
- [<span data-ttu-id="d1640-119">Mac için Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="d1640-119">Visual Studio 2017 for Mac</span></span>](https://www.visualstudio.com/vs/visual-studio-mac/)

<span data-ttu-id="d1640-120">Önkoşullar hakkında daha fazla bilgi için bkz: [.NET Core Mac üzerinde önkoşulları](../../core/macos-prerequisites.md).</span><span class="sxs-lookup"><span data-stu-id="d1640-120">For more information on prerequisites, see the [Prerequisites for .NET Core on Mac](../../core/macos-prerequisites.md).</span></span> <span data-ttu-id="d1640-121">Tam sistem gereksinimlerini Visual Studio 2017 için Mac için bkz: [Mac ürün ailesi sistem gereksinimleri için Visual Studio 2017](/visualstudio/productinfo/vs2017-system-requirements-mac).</span><span class="sxs-lookup"><span data-stu-id="d1640-121">For the full system requirements of Visual Studio 2017 for Mac, see [Visual Studio 2017 for Mac Product Family System Requirements](/visualstudio/productinfo/vs2017-system-requirements-mac).</span></span>

## <a name="building-a-library"></a><span data-ttu-id="d1640-122">Bir kitaplığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="d1640-122">Building a library</span></span>

1. <span data-ttu-id="d1640-123">Hoş Geldiniz ekranında seçin **yeni proje**.</span><span class="sxs-lookup"><span data-stu-id="d1640-123">On the Welcome screen, select **New Project**.</span></span> <span data-ttu-id="d1640-124">İçinde **yeni proje** altında iletişim **Multiplatform** düğümü, select **.NET standart Kitaplığı** şablonu.</span><span class="sxs-lookup"><span data-stu-id="d1640-124">In the **New Project** dialog under the **Multiplatform** node, select the **.NET Standard Library** template.</span></span> <span data-ttu-id="d1640-125">Seçin **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="d1640-125">Select **Next**.</span></span>

   ![Yeni Proje iletişim kutusu](./media/using-on-mac-vs-full-solution/vsmacfull01.png)

1. <span data-ttu-id="d1640-127">Proje adı "TextUtils" ("Metin yardımcı programlar" için kısa ad) ve "WordCounter" çözümü.</span><span class="sxs-lookup"><span data-stu-id="d1640-127">Name the project "TextUtils" (a short name for "Text Utilities") and the solution "WordCounter".</span></span> <span data-ttu-id="d1640-128">Bırakın **çözüm dizini içinde proje dizin oluşturma** işaretli.</span><span class="sxs-lookup"><span data-stu-id="d1640-128">Leave **Create a project directory within the solution directory** checked.</span></span> <span data-ttu-id="d1640-129">Seçin **oluşturma**.</span><span class="sxs-lookup"><span data-stu-id="d1640-129">Select **Create**.</span></span>

   ![Yeni Proje iletişim kutusu](./media/using-on-mac-vs-full-solution/vsmacfull02.png)

1. <span data-ttu-id="d1640-131">İçinde **çözüm** kenar genişletin `TextUtils` şablon tarafından sağlanan sınıf dosyası ortaya düğüme *Class1.cs*.</span><span class="sxs-lookup"><span data-stu-id="d1640-131">In the **Solution** sidebar, expand the `TextUtils` node to reveal the class file provided by the template, *Class1.cs*.</span></span> <span data-ttu-id="d1640-132">Dosyaya sağ tıklayın, **yeniden adlandırma** ve bağlam menüsünden ve dosyayı yeniden adlandırın *WordCount.cs*.</span><span class="sxs-lookup"><span data-stu-id="d1640-132">Right-click the file, select **Rename** from the context menu, and rename the file to *WordCount.cs*.</span></span> <span data-ttu-id="d1640-133">Dosyasını açın ve içeriğini aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="d1640-133">Open the file and replace the contents with the following code:</span></span>

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/TextUtils/WordCount.cs)]

1. <span data-ttu-id="d1640-134">Üç farklı yöntemlerden birini kullanarak dosyayı kaydedin: klavye kısayolunu kullanın <kbd> &#8984; </kbd> + <kbd>s</kbd>seçin **dosya**  >  **Kaydetmek** menüsünden veya sağ tıklatın dosyanın sekmesi ve select **kaydetmek** bağlam menüsünde.</span><span class="sxs-lookup"><span data-stu-id="d1640-134">Save the file by using any of three different methods: use the keyboard shortcut <kbd>&#8984;</kbd>+<kbd>s</kbd>, select **File** > **Save** from the menu, or right-click on the file's tab and select **Save** from the contextual menu.</span></span> <span data-ttu-id="d1640-135">Aşağıdaki resimde IDE penceresi gösterilir:</span><span class="sxs-lookup"><span data-stu-id="d1640-135">The following image shows the IDE window:</span></span>

   ![IDE pencere TextUtils gösteren sınıf kitaplığı, WordCount sınıf dosyası, statik sınıf WordCount ve GetWordCount yöntemi](./media/using-on-mac-vs-full-solution/vsmacfull03.png)

1. <span data-ttu-id="d1640-137">Seçin **hataları** IDE penceresini ekranın alt kısmındaki kenar boşluğunda **hataları** paneli.</span><span class="sxs-lookup"><span data-stu-id="d1640-137">Select **Errors** in the margin at the bottom of the IDE window to open the **Errors** panel.</span></span> <span data-ttu-id="d1640-138">Seçin **yapı çıktı** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="d1640-138">Select the **Build Output** button.</span></span>

   ![Alt kenar boşluğu hataları düğmesini gösteren IDE](./media/using-on-mac-vs-full-solution/vsmacfull03b.png)

1. <span data-ttu-id="d1640-140">Seçin **yapı** > **yapı tüm** menüsünde.</span><span class="sxs-lookup"><span data-stu-id="d1640-140">Select **Build** > **Build All** from the menu.</span></span>

   <span data-ttu-id="d1640-141">Çözüm oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d1640-141">The solution builds.</span></span> <span data-ttu-id="d1640-142">Derleme Çıktı paneli yapılandırmanın başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d1640-142">The build output panel shows that the build is successful.</span></span>

   ![Çıkış Bölmesi'yapı başarılı iletisini gösteren hatalar panelinin derleme](./media/using-on-mac-vs-full-solution/vsmacfull04.png)

## <a name="creating-a-test-project"></a><span data-ttu-id="d1640-144">Test projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="d1640-144">Creating a test project</span></span>

<span data-ttu-id="d1640-145">Birim testleri, geliştirme sırasında sınama ve yayımlama otomatik yazılım sağlar.</span><span class="sxs-lookup"><span data-stu-id="d1640-145">Unit tests provide automated software testing during your development and publishing.</span></span> <span data-ttu-id="d1640-146">Bu öğreticide kullandığınız test çerçevesi [xUnit (sürüm 2.2.0 veya sonraki)](https://xunit.github.io/), hangi otomatik olarak yüklenir aşağıdaki adımları çözümde xUnit test projesi eklenir:</span><span class="sxs-lookup"><span data-stu-id="d1640-146">The testing framework that you use in this tutorial is [xUnit (version 2.2.0 or later)](https://xunit.github.io/), which is installed automatically when the xUnit test project is added to the solution in the following steps:</span></span>

1. <span data-ttu-id="d1640-147">İçinde **çözüm** kenar sağ `WordCounter` çözümü ve Seç **Ekle** > **Yeni Proje Ekle**.</span><span class="sxs-lookup"><span data-stu-id="d1640-147">In the **Solution** sidebar, right-click the `WordCounter` solution and select **Add** > **Add New Project**.</span></span>

1. <span data-ttu-id="d1640-148">İçinde **yeni proje** iletişim kutusunda **testleri** gelen **.NET Core** düğümü.</span><span class="sxs-lookup"><span data-stu-id="d1640-148">In the **New Project** dialog, select **Tests** from the **.NET Core** node.</span></span> <span data-ttu-id="d1640-149">Seçin **xUnit Test projesi** arkasından **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="d1640-149">Select the **xUnit Test Project** followed by **Next**.</span></span>

   ![Yeni Proje iletişim kutusu xUnit test projesi oluşturma](./media/using-on-mac-vs-full-solution/vsmacfull05.png)

1. <span data-ttu-id="d1640-151">Yeni Proje "TestLibrary" olarak adlandırın ve seçin **oluşturma**.</span><span class="sxs-lookup"><span data-stu-id="d1640-151">Name the new project "TestLibrary" and select **Create**.</span></span>

   ![Proje adı sağlayan yeni proje iletişim kutusu](./media/using-on-mac-vs-full-solution/vsmacfull06.png)

1. <span data-ttu-id="d1640-153">Çalışmak test kitaplığının sırayla `WordCount` sınıfı, bir başvuru ekleyin `TextUtils` projesi.</span><span class="sxs-lookup"><span data-stu-id="d1640-153">In order for the test library to work with the `WordCount` class, add a reference to the `TextUtils` project.</span></span> <span data-ttu-id="d1640-154">İçinde **çözüm** kenar sağ **bağımlılıkları** altında **TestLibrary**.</span><span class="sxs-lookup"><span data-stu-id="d1640-154">In the **Solution** sidebar, right-click **Dependencies** under **TestLibrary**.</span></span> <span data-ttu-id="d1640-155">Seçin **Düzenle başvuruları** ve bağlam menüsünden.</span><span class="sxs-lookup"><span data-stu-id="d1640-155">Select **Edit References** from the context menu.</span></span>

1. <span data-ttu-id="d1640-156">İçinde **Düzenle başvuruları** iletişim kutusunda **TextUtils** üzerinde proje **projeleri** sekmesi. Seçin **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="d1640-156">In the **Edit References** dialog, select the **TextUtils** project on the **Projects** tab. Select **OK**.</span></span>

   ![Başvurular iletişim Düzenle](./media/using-on-mac-vs-full-solution/vsmacfull07.png)

1. <span data-ttu-id="d1640-158">İçinde **TestLibrary** projesi, yeniden adlandırma *UnitTest1.cs* dosya *TextUtilsTests.cs*.</span><span class="sxs-lookup"><span data-stu-id="d1640-158">In the **TestLibrary** project, rename the *UnitTest1.cs* file to *TextUtilsTests.cs*.</span></span>

1. <span data-ttu-id="d1640-159">Dosyasını açın ve kodu aşağıdakilerle değiştirin:</span><span class="sxs-lookup"><span data-stu-id="d1640-159">Open the file and replace the code with the following:</span></span>

   ```csharp
   using Xunit;
   using TextUtils;
   using System.Diagnostics;

   namespace TestLibrary
   {
       public class TextUtils_GetWordCountShould
       {
           [Fact]
           public void IgnoreCasing()
           {
               var wordCount = WordCount.GetWordCount("Jack", "Jack jack");
   
               Assert.NotEqual(2, wordCount);
           }
       }
   }
   ```

   <span data-ttu-id="d1640-160">Aşağıdaki resimde yerinde IDE birim test kodu ile gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d1640-160">The following image shows the IDE with the unit test code in place.</span></span> <span data-ttu-id="d1640-161">Dikkat `Assert.NotEqual` deyimi.</span><span class="sxs-lookup"><span data-stu-id="d1640-161">Pay attention to the `Assert.NotEqual` statement.</span></span>

   ![IDE ana penceresinde GetWordCount denetlemek için ilk birim testi](./media/using-on-mac-vs-full-solution/vsmacfull08.png)

   <span data-ttu-id="d1640-163">TDD kullanarak, test mantığını doğru olduğunu doğrulamak bir kez başarısız yeni bir test olmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="d1640-163">Using TDD, it's important to make a new test fail once to confirm its testing logic is correct.</span></span> <span data-ttu-id="d1640-164">(Büyük ve küçük harf) adı "Prizine" (büyük harf) ve "Prizine" ve "prizine" dizesiyle yöntemi geçirir.</span><span class="sxs-lookup"><span data-stu-id="d1640-164">The method passes in the name "Jack" (uppercase) and a string with "Jack" and "jack" (uppercase and lowercase).</span></span> <span data-ttu-id="d1640-165">Varsa `GetWordCount` yöntemi düzgün çalıştığından, arama word'ün iki örnek sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="d1640-165">If the `GetWordCount` method is working properly, it returns a count of two instances of the search word.</span></span> <span data-ttu-id="d1640-166">Bu test başarısız amaç için önce arama Word'ün "Prizine" iki örneği tarafından döndürülen olmayan test sunduğundan uygulamanız `GetWordCount` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d1640-166">In order to fail this test on purpose, you first implement the test asserting that two instances of the search word "Jack" aren't returned by the `GetWordCount` method.</span></span> <span data-ttu-id="d1640-167">Test amaç başarısız için sonraki adıma devam edin.</span><span class="sxs-lookup"><span data-stu-id="d1640-167">Continue to the next step to fail the test on purpose.</span></span>

1. <span data-ttu-id="d1640-168">Açık **birim testleri** paneli ekranın sağ tarafında.</span><span class="sxs-lookup"><span data-stu-id="d1640-168">Open the **Unit Tests** panel on the right side of the screen.</span></span>

![Birim testleri paneli](./media/using-on-mac-vs-full-solution/vsmacfull_UnitTestPanel.png)

1. <span data-ttu-id="d1640-170">Tıklatın **yerleştirme** paneli açık tutmak için simge.</span><span class="sxs-lookup"><span data-stu-id="d1640-170">Click the **Dock** icon to keep the panel open.</span></span>

![Birim testleri panelini yerleştirme simgesi](./media/using-on-mac-vs-full-solution/vsmacfull_UnitTestPanelDockIcon.png)

1. <span data-ttu-id="d1640-172">Tıklatın **tümünü Çalıştır** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="d1640-172">Click the **Run All** button.</span></span>
   
   <span data-ttu-id="d1640-173">Doğru sonuç olduğu test başarısız.</span><span class="sxs-lookup"><span data-stu-id="d1640-173">The test fails, which is the correct result.</span></span> <span data-ttu-id="d1640-174">Bu iki test yöntemini onaylar örneklerini `inputString`, "Prizine," değil "için sağlanan prizine prizine" dizesi sağlayıcıdan döndürülen `GetWordCount` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d1640-174">The test method asserts that two instances of the `inputString`, "Jack," aren't returned from the string "Jack jack" provided to the `GetWordCount` method.</span></span> <span data-ttu-id="d1640-175">Word büyük/küçük harf out oluşturmak bu yana `GetWordCount` yöntemi, iki örneği döndürülür.</span><span class="sxs-lookup"><span data-stu-id="d1640-175">Since word casing was factored out in the `GetWordCount` method, two instances are returned.</span></span> <span data-ttu-id="d1640-176">Onaylama işlemi, 2 *eşit değil* 2 başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="d1640-176">The assertion that 2 *is not equal to* 2 fails.</span></span> <span data-ttu-id="d1640-177">Bu doğru sonucu ve bizim test mantığı iyidir.</span><span class="sxs-lookup"><span data-stu-id="d1640-177">This is the correct outcome, and the logic of our test is good.</span></span>

   ![Sınama hatası](./media/using-on-mac-vs-full-solution/vsmacfull09.png)

1. <span data-ttu-id="d1640-179">Değiştirme `IgnoreCasing` test yöntemi değiştirerek `Assert.NotEqual` için `Assert.Equal`.</span><span class="sxs-lookup"><span data-stu-id="d1640-179">Modify the `IgnoreCasing` test method by changing `Assert.NotEqual` to `Assert.Equal`.</span></span> <span data-ttu-id="d1640-180">Klavye kısayolunu kullanarak dosyayı kaydedin <kbd> &#8984; </kbd> + <kbd>s</kbd>, **dosya** > **kaydetmek** menüsünde veya dosyanın sekmesinde sağ tıklayıp seçerek **kaydetmek** ve bağlam menüsünden.</span><span class="sxs-lookup"><span data-stu-id="d1640-180">Save the file by using the keyboard shortcut <kbd>&#8984;</kbd>+<kbd>s</kbd>, **File** > **Save** from the menu, or right-clicking on the file's tab and selecting **Save** from the context menu.</span></span>

   <span data-ttu-id="d1640-181">Beklediğiniz `searchWord` "Prizine" döndürür iki örnekleriyle `inputString` "Prizine prizine" geçirildi `GetWordCount`.</span><span class="sxs-lookup"><span data-stu-id="d1640-181">You expect that the `searchWord` "Jack" returns two instances with `inputString` "Jack jack" passed into `GetWordCount`.</span></span> <span data-ttu-id="d1640-182">Tıklayarak test yeniden çalıştırın **Testleri Çalıştır** düğmesini **birim testleri** Masası veya **yeniden çalıştır testleri** düğmesini **Test sonuçları** paneli ekranın alt kısmında.</span><span class="sxs-lookup"><span data-stu-id="d1640-182">Run the test again by clicking the **Run Tests** button in the **Unit Tests** panel or the **Rerun Tests** button in the **Test Results** panel at the bottom of the screen.</span></span> <span data-ttu-id="d1640-183">Test başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="d1640-183">The test passes.</span></span> <span data-ttu-id="d1640-184">"(Büyük/küçük harf yoksayar) prizine prizine" dizesindeki "Prizine" iki örneği vardır ve test onayı ifade eder `true`.</span><span class="sxs-lookup"><span data-stu-id="d1640-184">There are two instances of "Jack" in the string "Jack jack" (ignoring casing), and the test assertion is `true`.</span></span>

   ![Test geçişi](./media/using-on-mac-vs-full-solution/vsmacfull10.png)

1. <span data-ttu-id="d1640-186">Tek tek dönüş değerleri ile test etme bir `Fact` birim testi ile ne yapabileceğinizi sadece başlangıçtır.</span><span class="sxs-lookup"><span data-stu-id="d1640-186">Testing individual return values with a `Fact` is only the beginning of what you can do with unit testing.</span></span> <span data-ttu-id="d1640-187">Başka bir güçlü teknik aynı anda kullanarak çeşitli değerleri test sayesinde bir `Theory`.</span><span class="sxs-lookup"><span data-stu-id="d1640-187">Another powerful technique allows you to test several values at once using a `Theory`.</span></span> <span data-ttu-id="d1640-188">Aşağıdaki yöntemi ekleyin, `TextUtils_GetWordCountShould` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d1640-188">Add the following method to your `TextUtils_GetWordCountShould` class.</span></span> <span data-ttu-id="d1640-189">Bu yöntem ekledikten sonra sınıfında iki yöntem vardır:</span><span class="sxs-lookup"><span data-stu-id="d1640-189">You have two methods in the class after you add this method:</span></span>

   ```csharp
   [Theory]
   [InlineData(0, "Ting", "Does not appear in the string.")]
   [InlineData(1, "Ting", "Ting appears once.")]
   [InlineData(2, "Ting", "Ting appears twice with Ting.")]
   public void CountInstancesCorrectly(int count, 
                                       string searchWord, 
                                       string inputString)
   {
       Assert.NotEqual(count, WordCount.GetWordCount(searchWord,
                                                  inputString));
   }
   ```

   <span data-ttu-id="d1640-190">`CountInstancesCorrectly` Denetleyen `GetWordCount` yöntemi sayıları doğru.</span><span class="sxs-lookup"><span data-stu-id="d1640-190">The `CountInstancesCorrectly` checks that the `GetWordCount` method counts correctly.</span></span> <span data-ttu-id="d1640-191">`InlineData` Bir sayısı, bir arama sözcüğü ve denetlemek için bir giriş dizesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d1640-191">The `InlineData` provides a count, a search word, and an input string to check.</span></span> <span data-ttu-id="d1640-192">Test yöntemi, her veri satırı için bir kez çalışır.</span><span class="sxs-lookup"><span data-stu-id="d1640-192">The test method runs once for each line of data.</span></span> <span data-ttu-id="d1640-193">Bir kez daha, bir hata ilk kullanarak sunduğundan olduğunu unutmayın `Assert.NotEqual`, hatta veri sayıları doğru olduğunu ve tarafından döndürülen sayıları eşleşen değerleri bildiğinizde `GetWordCount` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d1640-193">Note once again that you're asserting a failure first by using `Assert.NotEqual`, even when you know that the counts in the data are correct and that the values match the counts returned by the `GetWordCount` method.</span></span> <span data-ttu-id="d1640-194">İlk zaman kaybı gibi test amaç başarısız adımı gerçekleştirmeden görünebilir, ancak ilk olup testlerinizi mantığını üzerinde önemli bir denetimi başarısız tarafından test mantığı olmadığı denetleniyor.</span><span class="sxs-lookup"><span data-stu-id="d1640-194">Performing the step of failing the test on purpose might seem like a waste of time at first, but checking the logic of the test by failing it first is an important check on the logic of your tests.</span></span> <span data-ttu-id="d1640-195">Başarısız beklediğiniz geçirmeden bir test yöntemi geldiğinizde, bir hata test mantığında buldunuz.</span><span class="sxs-lookup"><span data-stu-id="d1640-195">When you come across a test method that passes when you expect it to fail, you've found a bug in the logic of the test.</span></span> <span data-ttu-id="d1640-196">Bu bir test yöntemi her oluşturduğunuzda bu adımı için değer.</span><span class="sxs-lookup"><span data-stu-id="d1640-196">It's worth the effort to take this step every time you create a test method.</span></span>
   
1. <span data-ttu-id="d1640-197">Dosyayı kaydedin ve testleri yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d1640-197">Save the file and run the tests again.</span></span> <span data-ttu-id="d1640-198">Büyük/küçük harf test geçirir, ancak üç sayısı sınama başarısız.</span><span class="sxs-lookup"><span data-stu-id="d1640-198">The casing test passes but the three count tests fail.</span></span> <span data-ttu-id="d1640-199">Bu, tam olarak gerçekleşecek şekilde beklediğiniz olur.</span><span class="sxs-lookup"><span data-stu-id="d1640-199">This is exactly what you expect to happen.</span></span>

   ![Sınama hatası](./media/using-on-mac-vs-full-solution/vsmacfull11.png)

1. <span data-ttu-id="d1640-201">Değiştirme `CountInstancesCorrectly` test yöntemi değiştirerek `Assert.NotEqual` için `Assert.Equal`.</span><span class="sxs-lookup"><span data-stu-id="d1640-201">Modify the `CountInstancesCorrectly` test method by changing `Assert.NotEqual` to `Assert.Equal`.</span></span> <span data-ttu-id="d1640-202">Dosyayı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="d1640-202">Save the file.</span></span> <span data-ttu-id="d1640-203">Testleri yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d1640-203">Run the tests again.</span></span> <span data-ttu-id="d1640-204">Tüm sınamaları geçmesi.</span><span class="sxs-lookup"><span data-stu-id="d1640-204">All tests pass.</span></span>

   ![Test geçişi](./media/using-on-mac-vs-full-solution/vsmacfull12.png)

## <a name="adding-a-console-app"></a><span data-ttu-id="d1640-206">Bir konsol uygulaması ekleme</span><span class="sxs-lookup"><span data-stu-id="d1640-206">Adding a console app</span></span>

1. <span data-ttu-id="d1640-207">İçinde **çözüm** kenar sağ `WordCounter` çözümü.</span><span class="sxs-lookup"><span data-stu-id="d1640-207">In the **Solution** sidebar, right-click the `WordCounter` solution.</span></span> <span data-ttu-id="d1640-208">Yeni bir ekleme **konsol uygulaması** şablonu seçerek proje **.NET Core** > **uygulama** şablonları.</span><span class="sxs-lookup"><span data-stu-id="d1640-208">Add a new **Console Application** project by selecting the template from the **.NET Core** > **App** templates.</span></span> <span data-ttu-id="d1640-209">Seçin **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="d1640-209">Select **Next**.</span></span> <span data-ttu-id="d1640-210">Proje adı **WordCounterApp**.</span><span class="sxs-lookup"><span data-stu-id="d1640-210">Name the project **WordCounterApp**.</span></span> <span data-ttu-id="d1640-211">Seçin **oluşturma** çözümde projesi oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="d1640-211">Select **Create** to create the project in the solution.</span></span>

1. <span data-ttu-id="d1640-212">İçinde **çözümleri** kenar sağ **bağımlılıkları** yeni düğümü **WordCounterApp** proje.</span><span class="sxs-lookup"><span data-stu-id="d1640-212">In the **Solutions** sidebar, right-click the **Dependencies** node of the new **WordCounterApp** project.</span></span> <span data-ttu-id="d1640-213">İçinde **Düzenle başvuruları** iletişim kutusunda, onay **TextUtils** seçip **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="d1640-213">In the **Edit References** dialog, check **TextUtils** and select **OK**.</span></span>

1. <span data-ttu-id="d1640-214">Açık *Program.cs* dosya.</span><span class="sxs-lookup"><span data-stu-id="d1640-214">Open the *Program.cs* file.</span></span> <span data-ttu-id="d1640-215">Kod aşağıdakiyle değiştirin:</span><span class="sxs-lookup"><span data-stu-id="d1640-215">Replace the code with the following:</span></span>

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/WordCounterApp/Program.cs)]

1. <span data-ttu-id="d1640-216">IDE yerine bir konsol penceresinde uygulamayı çalıştırmak için sağ `WordCounterApp` proje, select **seçenekleri**ve açın **varsayılan** düğümü altında **yapılandırmaları**.</span><span class="sxs-lookup"><span data-stu-id="d1640-216">To run the app in a console window instead of the IDE, right-click the `WordCounterApp` project, select **Options**, and open the **Default** node under **Configurations**.</span></span> <span data-ttu-id="d1640-217">Onay kutusunu için **dış konsolda çalıştırmak**.</span><span class="sxs-lookup"><span data-stu-id="d1640-217">Check the box for **Run on external console**.</span></span> <span data-ttu-id="d1640-218">Bırakın **duraklatma konsol çıktısı** iade seçeneği.</span><span class="sxs-lookup"><span data-stu-id="d1640-218">Leave the **Pause console output** option checked.</span></span> <span data-ttu-id="d1640-219">Bu ayar için giriş yazabilirsiniz böylece bir konsol penceresi oluşturma uygulama neden `Console.ReadLine` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="d1640-219">This setting causes the app to spawn in a console window so that you can type input for the `Console.ReadLine` statements.</span></span> <span data-ttu-id="d1640-220">IDE içinde çalıştırmak için uygulamayı değiştirmeden bırakırsanız, yalnızca çıktısını görebilirsiniz `Console.WriteLine` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="d1640-220">If you leave the app to run in the IDE, you can only see the output of `Console.WriteLine` statements.</span></span> <span data-ttu-id="d1640-221">`Console.ReadLine` deyimleri IDE'nin içinde çalışmıyor **uygulama çıktısı** paneli.</span><span class="sxs-lookup"><span data-stu-id="d1640-221">`Console.ReadLine` statements do not work in the IDE's **Application Output** panel.</span></span>

   ![Proje Seçenekleri penceresi](./media/using-on-mac-vs-full-solution/vsmacfull13.png)

1. <span data-ttu-id="d1640-223">Çözüm çalıştırdığınızda, Visual Studio Mac için geçerli sürümü testleri çalışamadığı konsol uygulaması doğrudan çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d1640-223">Because the current version of Visual Studio for Mac cannot run the tests when the solution is run, you run the console app directly.</span></span> <span data-ttu-id="d1640-224">Sağ `WordCounterApp` proje ve seçin **öğesi çalıştırmak** ve bağlam menüsünden.</span><span class="sxs-lookup"><span data-stu-id="d1640-224">Right-click on the `WordCounterApp` project and select **Run item** from the context menu.</span></span> <span data-ttu-id="d1640-225">Uygulama ile YÜRÜT düğmesine çalıştırmayı denerseniz, çalıştırmak test Çalıştırıcısı ve uygulama başarısız.</span><span class="sxs-lookup"><span data-stu-id="d1640-225">If you attempt to run the app with the Play button, the test runner and app fail to run.</span></span> <span data-ttu-id="d1640-226">Bu sorunla ilgili iş durumu hakkında daha fazla bilgi için bkz: [xunit/xamarinstudio.xunit (#60)](https://github.com/xunit/xamarinstudio.xunit/issues/60).</span><span class="sxs-lookup"><span data-stu-id="d1640-226">For more information on the status of the work on this issue, see [xunit/xamarinstudio.xunit (#60)](https://github.com/xunit/xamarinstudio.xunit/issues/60).</span></span> <span data-ttu-id="d1640-227">Uygulamayı çalıştırdığınızda, konsol penceresinde istemleri giriş dizesini ve arama word için değerler sağlayın.</span><span class="sxs-lookup"><span data-stu-id="d1640-227">When you run the app, provide values for the search word and input string at the prompts in the console window.</span></span> <span data-ttu-id="d1640-228">Uygulama arama sözcüğü dizesinde görünür sayısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d1640-228">The app indicates the number of times the search word appears in the string.</span></span>

   ![Konsol penceresi word Zeytin gösteren arama dizesinde 'Iro tarafından lake Zeytin tarih ve Zeytin harika.'](./media/using-on-mac-vs-full-solution/vsmacfull14.png)

1. <span data-ttu-id="d1640-231">Keşfetmek için son özelliğini Mac için hata Visual Studio ile ayıklama</span><span class="sxs-lookup"><span data-stu-id="d1640-231">The last feature to explore is debugging with Visual Studio for Mac.</span></span> <span data-ttu-id="d1640-232">Bir kesme noktası ayarlayın `Console.WriteLine` deyimi: 23 satırının sol kenar boşluğunda seçin ve kod satırı yanındaki görünür kırmızı bir daire görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="d1640-232">Set a breakpoint on the `Console.WriteLine` statement: Select in the left margin of line 23, and you see a red circle appear next to the line of code.</span></span> <span data-ttu-id="d1640-233">Alternatif olarak, herhangi bir yere satırında seçin ve kodu seçin **çalıştırmak** > **kesme** menüsünde.</span><span class="sxs-lookup"><span data-stu-id="d1640-233">Alternatively, select anywhere on the line of code and select **Run** > **Toggle Breakpoint** from the menu.</span></span>

   ![Satır 23 Console.WriteLine deyimi kesme noktası ayarlama](./media/using-on-mac-vs-full-solution/vsmacfull15.png)

1. <span data-ttu-id="d1640-235">Sağ `WordCounterApp` projesi.</span><span class="sxs-lookup"><span data-stu-id="d1640-235">Right-click the `WordCounterApp` project.</span></span> <span data-ttu-id="d1640-236">Seçin **hata ayıklamayı Başlat öğesi** ve bağlam menüsünden.</span><span class="sxs-lookup"><span data-stu-id="d1640-236">Select **Start Debugging item** from the context menu.</span></span> <span data-ttu-id="d1640-237">Uygulama çalıştırıldığında arama word "kat" ve "köpek kat aranır; kat kaçışlı" girin.</span><span class="sxs-lookup"><span data-stu-id="d1640-237">When the app runs, enter the search word "cat" and "The dog chased the cat, but the cat escaped."</span></span> <span data-ttu-id="d1640-238">Arama için dize.</span><span class="sxs-lookup"><span data-stu-id="d1640-238">for the string to search.</span></span> <span data-ttu-id="d1640-239">Zaman `Console.WriteLine` deyimi ulaşıldığında, program yürütme deyimi yürütülmeden önce durur.</span><span class="sxs-lookup"><span data-stu-id="d1640-239">When the `Console.WriteLine` statement is reached, program execution halts before the statement is executed.</span></span> <span data-ttu-id="d1640-240">İçinde **Yereller** sekmesinde, gördüğünüz `searchWord`, `inputString`, `wordCount`, ve `pluralChar` değerleri.</span><span class="sxs-lookup"><span data-stu-id="d1640-240">In the **Locals** tab, you can see the `searchWord`, `inputString`, `wordCount`, and `pluralChar` values.</span></span>

   ![Program yürütme hemen Console.WriteLine deyimi yürütülmeden önce değerleri gösteren yerel penceresiyle Console.WriteLine ifadesine durduruldu.](./media/using-on-mac-vs-full-solution/vsmacfull16.png)

1. <span data-ttu-id="d1640-242">İçinde **hemen** bölmesi, türü "wordCount 999; =" ve Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d1640-242">In the **Immediate** pane, type "wordCount = 999;" and press Enter.</span></span> <span data-ttu-id="d1640-243">Bu 999 arasında anlamsız değeri atar `wordCount` değişkeni gösteren hata ayıklama sırasında değişken değerlerini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1640-243">This assigns a nonsense value of 999 to the `wordCount` variable showing that you can replace variable values while debugging.</span></span>

   ![Bizim kesme noktası isabet.](./media/using-on-mac-vs-full-solution/vsmacfull17.png)

1. <span data-ttu-id="d1640-246">Araç çubuğunda *devam* oku.</span><span class="sxs-lookup"><span data-stu-id="d1640-246">In the toolbar, click the *continue* arrow.</span></span> <span data-ttu-id="d1640-247">Konsol penceresinde çıktı bakın.</span><span class="sxs-lookup"><span data-stu-id="d1640-247">Look at the output in the console window.</span></span> <span data-ttu-id="d1640-248">Uygulama hata ayıklaması ayarladığınız 999 yanlış değerini bildirir.</span><span class="sxs-lookup"><span data-stu-id="d1640-248">It reports the incorrect value of 999 that you set when you were debugging the app.</span></span>

   ![Araç çubuğu düğmesi devam](./media/using-on-mac-vs-full-solution/vsmacfull18.png)

   ![Arama sözcük sayısını 999 uygulamanın çıktıda bir değere değiştirilir](./media/using-on-mac-vs-full-solution/vsmacfull19.png)

## <a name="see-also"></a><span data-ttu-id="d1640-251">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1640-251">See also</span></span>

[<span data-ttu-id="d1640-252">Visual Studio 2017 Mac sürüm notları</span><span class="sxs-lookup"><span data-stu-id="d1640-252">Visual Studio 2017 for Mac Release Notes</span></span>](/visualstudio/releasenotes/vs2017-mac-relnotes)
