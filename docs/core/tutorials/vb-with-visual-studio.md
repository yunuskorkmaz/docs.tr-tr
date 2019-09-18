---
title: Visual Studio 2017 ' de Visual Basic ile .NET Core Merhaba Dünya uygulaması
description: Visual Studio 2017 kullanarak Visual Basic basit bir .NET Core konsol uygulaması derlemeyi öğrenin.
author: rpetrusha
ms.author: ronpet
ms.date: 08/07/2017
dev_langs:
- vb
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: b4f3cc055f73332db1348ef35174beab614df147
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71039608"
---
# <a name="build-a-visual-basic-hello-world-application-with-the-net-core-sdk-in-visual-studio-2017"></a><span data-ttu-id="c0315-103">Visual Studio 2017 ' de .NET Core SDK ile Visual Basic Merhaba Dünya uygulaması derleme</span><span class="sxs-lookup"><span data-stu-id="c0315-103">Build a Visual Basic Hello World application with the .NET Core SDK in Visual Studio 2017</span></span>

<span data-ttu-id="c0315-104">Bu konu, Visual Studio 2017 ' de Visual Basic kullanarak basit bir .NET Core konsol uygulaması oluşturmaya, hata ayıklamanıza ve yayımlamaya yönelik adım adım bir giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="c0315-104">This topic provides a step-by-step introduction to building, debugging, and publishing a simple .NET Core console application using Visual Basic in Visual Studio 2017.</span></span> <span data-ttu-id="c0315-105">Visual Studio 2017, .NET Core uygulamaları oluşturmak için tam özellikli bir geliştirme ortamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c0315-105">Visual Studio 2017 provides a full-featured development environment for building .NET Core applications.</span></span> <span data-ttu-id="c0315-106">Uygulama platforma özgü bağımlılıklara sahip olmadığı sürece, uygulama .NET Core 'un hedeflediği tüm platformlarda ve .NET Core yüklü olan herhangi bir sistemde çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="c0315-106">As long as the application doesn't have platform-specific dependencies, the application can run on any platform that .NET Core targets and on any system that has .NET Core installed.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c0315-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="c0315-107">Prerequisites</span></span>

<span data-ttu-id="c0315-108">[Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) ".NET Core platformlar arası geliştirme" iş yükü yüklendi.</span><span class="sxs-lookup"><span data-stu-id="c0315-108">[Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) with the ".NET Core cross-platform development" workload installed.</span></span> <span data-ttu-id="c0315-109">Uygulamanızı .NET Core 2,1 veya sonraki sürümleriyle geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c0315-109">You can develop your app with .NET Core 2.1 or later versions.</span></span>

<span data-ttu-id="c0315-110">Daha fazla bilgi için bkz. [Windows üzerinde .NET Core önkoşulları](../windows-prerequisites.md).</span><span class="sxs-lookup"><span data-stu-id="c0315-110">For more information, see [Prerequisites for .NET Core on Windows](../windows-prerequisites.md).</span></span>

## <a name="a-simple-hello-world-application"></a><span data-ttu-id="c0315-111">Basit bir Merhaba Dünya uygulaması</span><span class="sxs-lookup"><span data-stu-id="c0315-111">A simple Hello World application</span></span>

<span data-ttu-id="c0315-112">Basit bir "Merhaba Dünya" konsol uygulaması oluşturarak başlayın.</span><span class="sxs-lookup"><span data-stu-id="c0315-112">Begin by creating a simple "Hello World" console application.</span></span> <span data-ttu-id="c0315-113">Aşağıdaki adımları uygulayın:</span><span class="sxs-lookup"><span data-stu-id="c0315-113">Follow these steps:</span></span>

1. <span data-ttu-id="c0315-114">Visual Studio 2017 ' i başlatın.</span><span class="sxs-lookup"><span data-stu-id="c0315-114">Launch Visual Studio 2017.</span></span> <span data-ttu-id="c0315-115">Menü çubuğundan **Dosya** > **Yeni** > **Proje** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="c0315-115">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="c0315-116">*Yeni proje*\* iletişim kutusunda **Visual Basic** düğümünü ve ardından **.NET Core** düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="c0315-116">In the *New Project*\* dialog, select the **Visual Basic** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="c0315-117">Ardından **konsol uygulaması (.NET Core)** proje şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="c0315-117">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="c0315-118">**Ad** metin kutusuna "HelloWorld" yazın.</span><span class="sxs-lookup"><span data-stu-id="c0315-118">In the **Name** text box, type "HelloWorld".</span></span> <span data-ttu-id="c0315-119">**Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="c0315-119">Select the **OK** button.</span></span>

   ![Konsol uygulaması seçiliyken yeni proje iletişim kutusu](./media/vb-with-visual-studio/visual-studio-new-project.png)

1. <span data-ttu-id="c0315-121">Visual Studio, projenizi oluşturmak için şablonu kullanır.</span><span class="sxs-lookup"><span data-stu-id="c0315-121">Visual Studio uses the template to create your project.</span></span> <span data-ttu-id="c0315-122">.NET Core için Visual Basic konsol uygulaması şablonu, bağımsız değişken olarak bir `Program` <xref:System.String> dizi alan tek bir `Main`yöntemle bir sınıfını otomatik olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c0315-122">The Visual Basic Console Application template for .NET Core automatically defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="c0315-123">`Main`uygulama giriş noktası, uygulamayı başlattığında çalışma zamanı tarafından otomatik olarak çağrılan yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="c0315-123">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="c0315-124">Uygulama başlatıldığında sağlanan herhangi bir komut satırı bağımsız değişkeni, *args* dizisinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c0315-124">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

   ![Visual Studio ve yeni HelloWorld projesi](./media/vb-with-visual-studio/visual-studio-main-window.png)

   <span data-ttu-id="c0315-126">Şablon basit bir "Merhaba Dünya" uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c0315-126">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="c0315-127">"Merhaba Dünya! <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> " değişmez dizesini göstermek için yöntemini çağırır</span><span class="sxs-lookup"><span data-stu-id="c0315-127">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display the literal string "Hello World!"</span></span> <span data-ttu-id="c0315-128">Konsol penceresinde.</span><span class="sxs-lookup"><span data-stu-id="c0315-128">in the console window.</span></span> <span data-ttu-id="c0315-129">Araç çubuğunda yeşil oklu **HelloWorld** düğmesini seçerek programı hata ayıklama modunda çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c0315-129">By selecting the **HelloWorld** button with the green arrow on the toolbar, you can run the program in Debug mode.</span></span> <span data-ttu-id="c0315-130">Bunu yaparsanız, konsol penceresi kapanmadan önce yalnızca kısa bir zaman aralığı için görünür olur.</span><span class="sxs-lookup"><span data-stu-id="c0315-130">If you do, the console window is visible for only a brief time interval before it closes.</span></span> <span data-ttu-id="c0315-131">Bu durum, yöntemin `Main` sonlandırdığı ve `Main` yöntemin bir tek deyimin yürütüldüğü anda sona erdiği için oluşur.</span><span class="sxs-lookup"><span data-stu-id="c0315-131">This occurs because the `Main` method terminates and the application ends as soon as the single statement in the `Main` method executes.</span></span>

1. <span data-ttu-id="c0315-132">Uygulamanın konsol penceresini kapatmadan önce duraklatılmasına neden olmak için, <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> yöntemine yapılan çağrıdan hemen sonra aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c0315-132">To cause the application to pause before it closes the console window, add the following code immediately after the call to the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method:</span></span>

   ```vb
   Console.Write("Press any key to continue...")
   Console.ReadKey(true)
   ```

   <span data-ttu-id="c0315-133">Bu kod, kullanıcıdan herhangi bir tuşa basması ve bir tuşa basılana kadar programı duraklayacağını ister.</span><span class="sxs-lookup"><span data-stu-id="c0315-133">This code prompts the user to press any key and then pauses the program until a key is pressed.</span></span>

1. <span data-ttu-id="c0315-134">Menü çubuğunda Build**Build Solution**öğesini **seçin.**  > </span><span class="sxs-lookup"><span data-stu-id="c0315-134">On the menu bar, select **Build** > **Build Solution**.</span></span> <span data-ttu-id="c0315-135">Bu, programınızı bir tam zamanında (JıT) derleyicisi tarafından ikili koda dönüştürülen bir ara dile (IL) derler.</span><span class="sxs-lookup"><span data-stu-id="c0315-135">This compiles your program into an intermediate language (IL) that's converted into binary code by a just-in-time (JIT) compiler.</span></span>

1. <span data-ttu-id="c0315-136">Araç çubuğunda yeşil oklu **HelloWorld** düğmesini seçerek programı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c0315-136">Run the program by selecting the **HelloWorld** button with the green arrow on the toolbar.</span></span>

   ![Merhaba Dünya devam etmek için herhangi bir tuşa basarak konsol penceresi](./media/with-visual-studio/hello-world-console.png)

1. <span data-ttu-id="c0315-138">Konsol penceresini kapatmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="c0315-138">Press any key to close the console window.</span></span>

## <a name="enhancing-the-hello-world-application"></a><span data-ttu-id="c0315-139">Merhaba Dünya uygulamasını geliştirme</span><span class="sxs-lookup"><span data-stu-id="c0315-139">Enhancing the Hello World application</span></span>

<span data-ttu-id="c0315-140">Uygulamanızı, adını ve Tarih ve saat ile birlikte göstermek için kullanıcıya bir ad isteyecek şekilde geliştirin.</span><span class="sxs-lookup"><span data-stu-id="c0315-140">Enhance your application to prompt the user for his or her name and to display it along with the date and time.</span></span> <span data-ttu-id="c0315-141">Programı değiştirmek ve test etmek için aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="c0315-141">To modify and test the program, do the following:</span></span>

1. <span data-ttu-id="c0315-142">`Sub Main(args As String())` Satırı izleyen açılış ayracından hemen sonra ve ilk kapanış parantezinden önce kod penceresine aşağıdaki Visual Basic kodu girin:</span><span class="sxs-lookup"><span data-stu-id="c0315-142">Enter the following Visual Basic code in the code window immediately after the opening bracket that follows the `Sub Main(args As String())` line and before the first closing bracket:</span></span>

   [!code-vb[GettingStarted#1](../../../samples/snippets/core/tutorials/vb-with-visual-studio/helloworld.vb#1)]

   <span data-ttu-id="c0315-143">Bu kod, `Main` yönteminin içeriğini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="c0315-143">This code replaces the contents of the `Main` method.</span></span>

   ![Güncelleştirilmiş Main yöntemiyle Visual Studio program dosyası](./media/vb-with-visual-studio/visual-basic-code-window.png)

   <span data-ttu-id="c0315-145">Bu kod "adınız nedir?" görüntüler</span><span class="sxs-lookup"><span data-stu-id="c0315-145">This code displays "What is your name?"</span></span> <span data-ttu-id="c0315-146">Konsol penceresinde ve ardından ENTER tuşuna basarak Kullanıcı bir dize girene kadar bekler.</span><span class="sxs-lookup"><span data-stu-id="c0315-146">in the console window and waits until the user enters a string followed by the Enter key.</span></span> <span data-ttu-id="c0315-147">Bu dizeyi adlı `name`bir değişkende depolar.</span><span class="sxs-lookup"><span data-stu-id="c0315-147">It stores this string into a variable named `name`.</span></span> <span data-ttu-id="c0315-148">Ayrıca, geçerli yerel saati içeren <xref:System.DateTime.Now?displayProperty=nameWithType> özelliğinin değerini alır ve bunu adlı `currentDate`bir değişkene atar.</span><span class="sxs-lookup"><span data-stu-id="c0315-148">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `currentDate`.</span></span> <span data-ttu-id="c0315-149">Son olarak, bu değerleri konsol penceresinde göstermek için bir [enterpolasyonlu dize](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) kullanır.</span><span class="sxs-lookup"><span data-stu-id="c0315-149">Finally, it uses an [interpolated string](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) to display these values in the console window.</span></span>

1. <span data-ttu-id="c0315-150">Build**Build Solution** **öğesini seçerek** > programı derleyin.</span><span class="sxs-lookup"><span data-stu-id="c0315-150">Compile the program by choosing **Build** > **Build Solution**.</span></span>

1. <span data-ttu-id="c0315-151">Araç çubuğundan yeşil oku seçerek, F5 tuşuna basarak veya **hata** > ayıklama**başlatma hata ayıklamayı Başlat** menü öğesini seçerek programı Visual Studio 'daki hata ayıklama modunda çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c0315-151">Run the program in Debug mode in Visual Studio by selecting the green arrow on the toolbar, pressing F5, or choosing the **Debug** > **Start Debugging** menu item.</span></span> <span data-ttu-id="c0315-152">Bir ad girip ENTER tuşuna basarak istemi yanıtlayın.</span><span class="sxs-lookup"><span data-stu-id="c0315-152">Respond to the prompt by entering a name and pressing the Enter key.</span></span>

   ![Değiştirilen program çıkışıyla konsol penceresi](./media/with-visual-studio/hello-world-update.png)

1. <span data-ttu-id="c0315-154">Konsol penceresini kapatmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="c0315-154">Press any key to close the console window.</span></span>

<span data-ttu-id="c0315-155">Uygulamanızı oluşturdunuz ve çalıştırdık.</span><span class="sxs-lookup"><span data-stu-id="c0315-155">You've created and run your application.</span></span> <span data-ttu-id="c0315-156">Profesyonel bir uygulama geliştirmek için uygulamanızı yayın için hazırlamak üzere bazı ek adımlar gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="c0315-156">To develop a professional application, take some additional steps to make your application ready for release:</span></span>

- <span data-ttu-id="c0315-157">Uygulamanızda hata ayıklamak için bkz. [Visual Studio 2017 kullanarak .NET Core Merhaba Dünya uygulamanızda hata ayıklama](debugging-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="c0315-157">To debug your application, see [Debug your .NET Core Hello World application using Visual Studio 2017](debugging-with-visual-studio.md).</span></span>

- <span data-ttu-id="c0315-158">Uygulamanızın dağıtılabilir bir sürümünü yayımlamak için bkz. [Visual Studio 2017 ile .NET Core Merhaba Dünya uygulamanızı yayımlama](publishing-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="c0315-158">To publish a distributable version of your application, see [Publish your .NET Core Hello World application with Visual Studio 2017](publishing-with-visual-studio.md).</span></span>

## <a name="related-topics"></a><span data-ttu-id="c0315-159">İlgili konular</span><span class="sxs-lookup"><span data-stu-id="c0315-159">Related topics</span></span>

<span data-ttu-id="c0315-160">Konsol uygulaması yerine, Visual Basic, .NET Core ve Visual Studio 2017 ile .NET Standard bir sınıf kitaplığı da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c0315-160">Instead of a console application, you can also build a .NET Standard class library with Visual Basic, .NET Core, and Visual Studio 2017.</span></span> <span data-ttu-id="c0315-161">Adım adım bir giriş için bkz. [Visual Studio 2017 'de Visual Basic ve .NET Core SDK ile .NET Standard kitaplığı oluşturma](vb-library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="c0315-161">For a step-by-step introduction, see [Build a .NET Standard library with Visual Basic and .NET Core SDK in Visual Studio 2017](vb-library-with-visual-studio.md).</span></span>
