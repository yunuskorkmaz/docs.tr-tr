---
title: Visual Studio 2017'de Visual Basic ile .NET core Merhaba Dünya uygulaması
description: Visual Studio 2017'yi kullanarak Visual Basic ile basit bir .NET Core konsol uygulaması oluşturmayı öğrenin.
author: rpetrusha
ms.author: ronpet
ms.date: 08/07/2017
dev_langs:
- vb
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: de7a423bb3e9a288d17c86e9e0afc3b00f6fd80b
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362268"
---
# <a name="build-a-visual-basic-hello-world-application-with-the-net-core-sdk-in-visual-studio-2017"></a><span data-ttu-id="1140a-103">Visual Studio 2017'de .NET Core SDK'sı ile bir Visual Basic Merhaba Dünya uygulaması derleme</span><span class="sxs-lookup"><span data-stu-id="1140a-103">Build a Visual Basic Hello World application with the .NET Core SDK in Visual Studio 2017</span></span>

<span data-ttu-id="1140a-104">Bu konuda, derleme, hata ayıklama ve Visual Studio 2017'de Visual Basic kullanarak basit bir .NET Core konsol uygulaması yayımlama için adım adım bir giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="1140a-104">This topic provides a step-by-step introduction to building, debugging, and publishing a simple .NET Core console application using Visual Basic in Visual Studio 2017.</span></span> <span data-ttu-id="1140a-105">Visual Studio 2017, .NET Core uygulamaları oluşturmaya yönelik tam özellikli bir geliştirme ortamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="1140a-105">Visual Studio 2017 provides a full-featured development environment for building .NET Core applications.</span></span> <span data-ttu-id="1140a-106">Uygulama, platforma özel bağımlılıklar yok sürece, uygulama, .NET Core hedefleyen herhangi bir platformda çalışabilir ve .NET Core sahip herhangi bir sistemde yüklü.</span><span class="sxs-lookup"><span data-stu-id="1140a-106">As long as the application doesn't have platform-specific dependencies, the application can run on any platform that .NET Core targets and on any system that has .NET Core installed.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1140a-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="1140a-107">Prerequisites</span></span>

<span data-ttu-id="1140a-108">[Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) yüklü ".NET Core çoklu platform geliştirme" iş yüküyle birlikte sağlanır.</span><span class="sxs-lookup"><span data-stu-id="1140a-108">[Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) with the ".NET Core cross-platform development" workload installed.</span></span> <span data-ttu-id="1140a-109">.NET Core 2.0 ile uygulamanızı geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1140a-109">You can develop your app with .NET Core 2.0.</span></span>

<span data-ttu-id="1140a-110">Daha fazla bilgi için [Windows üzerinde .NET Core önkoşulları](../../core/windows-prerequisites.md).</span><span class="sxs-lookup"><span data-stu-id="1140a-110">For more information, see [Prerequisites for .NET Core on Windows](../../core/windows-prerequisites.md).</span></span>

## <a name="a-simple-hello-world-application"></a><span data-ttu-id="1140a-111">Basit bir Hello World uygulaması</span><span class="sxs-lookup"><span data-stu-id="1140a-111">A simple Hello World application</span></span>

<span data-ttu-id="1140a-112">Basit bir "Hello World" konsol uygulaması oluşturarak başlayın.</span><span class="sxs-lookup"><span data-stu-id="1140a-112">Begin by creating a simple "Hello World" console application.</span></span> <span data-ttu-id="1140a-113">Aşağıdaki adımları uygulayın:</span><span class="sxs-lookup"><span data-stu-id="1140a-113">Follow these steps:</span></span>

1. <span data-ttu-id="1140a-114">Visual Studio 2017'yi başlatın.</span><span class="sxs-lookup"><span data-stu-id="1140a-114">Launch Visual Studio 2017.</span></span> <span data-ttu-id="1140a-115">Seçin **dosya** > **yeni** > **proje** menü çubuğundan.</span><span class="sxs-lookup"><span data-stu-id="1140a-115">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="1140a-116">İçinde *yeni proje*\* iletişim kutusunda **Visual Basic** düğümünü ve ardından **.NET Core** düğümü.</span><span class="sxs-lookup"><span data-stu-id="1140a-116">In the *New Project*\* dialog, select the **Visual Basic** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="1140a-117">Ardından **konsol uygulaması (.NET Core)** proje şablonu.</span><span class="sxs-lookup"><span data-stu-id="1140a-117">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="1140a-118">İçinde **adı** metin kutusunda, "HelloWorld" yazın.</span><span class="sxs-lookup"><span data-stu-id="1140a-118">In the **Name** text box, type "HelloWorld".</span></span> <span data-ttu-id="1140a-119">**Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="1140a-119">Select the **OK** button.</span></span>

   ![Seçilen konsol uygulaması ile yeni proje iletişim kutusu](./media/vb-with-visual-studio/visual-studio-new-project.png)
   
1. <span data-ttu-id="1140a-121">Visual Studio, projenizi oluşturmak için şablon kullanır.</span><span class="sxs-lookup"><span data-stu-id="1140a-121">Visual Studio uses the template to create your project.</span></span> <span data-ttu-id="1140a-122">.NET Core için Visual Basic konsol uygulaması şablonu otomatik olarak bir sınıf tanımlar `Program`, tek bir yöntemi olan `Main`, alan bir <xref:System.String> bağımsız değişken olarak bir dizi.</span><span class="sxs-lookup"><span data-stu-id="1140a-122">The Visual Basic Console Application template for .NET Core automatically defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="1140a-123">`Main` uygulama başlatıldığında otomatik olarak çalışma zamanı tarafından çağrılır yöntemi uygulama giriş noktası niteliğindedir.</span><span class="sxs-lookup"><span data-stu-id="1140a-123">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="1140a-124">Uygulama başlatıldığında sağlanan komut satırı bağımsız değişkenleri kullanılabilir *args* dizisi.</span><span class="sxs-lookup"><span data-stu-id="1140a-124">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

   ![Visual Studio ve yeni HelloWorld proje](./media/vb-with-visual-studio/visual-studio-main-window.png)

   <span data-ttu-id="1140a-126">Şablon, basit bir "Hello World" uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1140a-126">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="1140a-127">Çağrı <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> "Hello World!" sabit dizesini görüntülemek için yöntemi</span><span class="sxs-lookup"><span data-stu-id="1140a-127">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display the literal string "Hello World!"</span></span> <span data-ttu-id="1140a-128">Konsol penceresinde.</span><span class="sxs-lookup"><span data-stu-id="1140a-128">in the console window.</span></span> <span data-ttu-id="1140a-129">Seçerek **HelloWorld** düğme araç çubuğundaki yeşil ok ile programın hata ayıklama modunda çalıştırabilir.</span><span class="sxs-lookup"><span data-stu-id="1140a-129">By selecting the **HelloWorld** button with the green arrow on the toolbar, you can run the program in Debug mode.</span></span> <span data-ttu-id="1140a-130">Bunu yaparsanız, kapatılmadan önce konsol penceresi yalnızca kısa bir zaman aralığı için görülebilir.</span><span class="sxs-lookup"><span data-stu-id="1140a-130">If you do, the console window is visible for only a brief time interval before it closes.</span></span> <span data-ttu-id="1140a-131">Bu durum oluşur `Main` yöntemi sonlandırır ve uygulama aşağıdaki tek deyimde olan en kısa sürede sona `Main` yöntemini yürütür.</span><span class="sxs-lookup"><span data-stu-id="1140a-131">This occurs because the `Main` method terminates and the application ends as soon as the single statement in the `Main` method executes.</span></span>

1. <span data-ttu-id="1140a-132">Konsol penceresinde kapatılmadan önce beklenecek Uygulanmanın için çağırdıktan hemen sonra aşağıdaki kodu ekleyin <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> yöntemi:</span><span class="sxs-lookup"><span data-stu-id="1140a-132">To cause the application to pause before it closes the console window, add the following code immediately after the call to the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method:</span></span>

   ```vb
   Console.Write("Press any key to continue...")
   Console.ReadKey(true)
   ```
   <span data-ttu-id="1140a-133">Bu kod, herhangi bir tuşa basın ister ve daha sonra bir tuşa basıldığında kadar program duraklatılır.</span><span class="sxs-lookup"><span data-stu-id="1140a-133">This code prompts the user to press any key and then pauses the program until a key is pressed.</span></span>

1. <span data-ttu-id="1140a-134">Menü çubuğunda, seçin **derleme** > **Çözümü Derle**.</span><span class="sxs-lookup"><span data-stu-id="1140a-134">On the menu bar, select **Build** > **Build Solution**.</span></span> <span data-ttu-id="1140a-135">Bu, just-in-time (JIT) derleyici tarafından ikili koda dönüştürülür bir ara dile (IL) programınızı derler.</span><span class="sxs-lookup"><span data-stu-id="1140a-135">This compiles your program into an intermediate language (IL) that's converted into binary code by a just-in-time (JIT) compiler.</span></span>

1. <span data-ttu-id="1140a-136">Programı çalıştırmayı seçerek tarafından **HelloWorld** araç çubuğundaki yeşil bir ok düğmesi.</span><span class="sxs-lookup"><span data-stu-id="1140a-136">Run the program by selecting the **HelloWorld** button with the green arrow on the toolbar.</span></span>

   ![Devam etmek için herhangi bir tuşa Hello World tuşuna gösteren konsol penceresi](./media/with-visual-studio/hello-world-console.png)

1. <span data-ttu-id="1140a-138">Konsol penceresini kapatmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="1140a-138">Press any key to close the console window.</span></span>

## <a name="enhancing-the-hello-world-application"></a><span data-ttu-id="1140a-139">Hello World uygulaması geliştirme</span><span class="sxs-lookup"><span data-stu-id="1140a-139">Enhancing the Hello World application</span></span>

<span data-ttu-id="1140a-140">Kullanıcıdan kendi ad ve tarih ve saat ile birlikte görüntülemek için uygulama geliştirin.</span><span class="sxs-lookup"><span data-stu-id="1140a-140">Enhance your application to prompt the user for his or her name and to display it along with the date and time.</span></span> <span data-ttu-id="1140a-141">Program sınama ve değiştirmek için aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="1140a-141">To modify and test the program, do the following:</span></span>

1. <span data-ttu-id="1140a-142">Aşağıdaki kod Visual Basic kod penceresinde izleyen hemen ayraç sonra girin `Sub Main(args As String())` satır ve ilk ayraç önce:</span><span class="sxs-lookup"><span data-stu-id="1140a-142">Enter the following Visual Basic code in the code window immediately after the opening bracket that follows the `Sub Main(args As String())` line and before the first closing bracket:</span></span>

   [!code-vb[GettingStarted#1](../../../samples/snippets/core/tutorials/vb-with-visual-studio/helloworld.vb#1)]

   <span data-ttu-id="1140a-143">Bu kodu varolan değiştirir <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, <xref:System.Console.Write%2A?displayProperty=nameWithType>, ve <xref:System.Console.ReadKey%2A?displayProperty=nameWithType> deyimleri.</span><span class="sxs-lookup"><span data-stu-id="1140a-143">This code replaces the existing <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, <xref:System.Console.Write%2A?displayProperty=nameWithType>, and <xref:System.Console.ReadKey%2A?displayProperty=nameWithType> statements.</span></span>

   ![Visual Studio Program dosyası ile güncelleştirilmiş Main yöntemi](./media/vb-with-visual-studio/visual-basic-code-window.png)

   <span data-ttu-id="1140a-145">Bu kod, "Adınız ne?" görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1140a-145">This code displays "What is your name?"</span></span> <span data-ttu-id="1140a-146">Kullanıcı kadar bekler ve konsol penceresinde Enter tuşuna basın, bir dize girer.</span><span class="sxs-lookup"><span data-stu-id="1140a-146">in the console window and waits until the user enters a string followed by the Enter key.</span></span> <span data-ttu-id="1140a-147">Bu dize adlı bir değişkende depoladığı `name`.</span><span class="sxs-lookup"><span data-stu-id="1140a-147">It stores this string into a variable named `name`.</span></span> <span data-ttu-id="1140a-148">Ayrıca bir değeri alır <xref:System.DateTime.Now?displayProperty=nameWithType> geçerli yerel saat içerir ve adlı bir değişkene atar özelliği `currentDate`.</span><span class="sxs-lookup"><span data-stu-id="1140a-148">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `currentDate`.</span></span> <span data-ttu-id="1140a-149">Son olarak, bunu kullanan bir [ilişkilendirilmiş bir dizedir](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) bu değerleri konsol penceresinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1140a-149">Finally, it uses an [interpolated string](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) to display these values in the console window.</span></span>

1. <span data-ttu-id="1140a-150">Program seçerek derleme **derleme** > **Çözümü Derle**.</span><span class="sxs-lookup"><span data-stu-id="1140a-150">Compile the program by choosing **Build** > **Build Solution**.</span></span>

1. <span data-ttu-id="1140a-151">Araç çubuğundaki yeşil oku seçerek, F5 tuşuna basarak veya seçerek Visual Studio'da hata ayıklama modunda programı çalıştırın **hata ayıklama** > **hata ayıklamayı Başlat** menü öğesi.</span><span class="sxs-lookup"><span data-stu-id="1140a-151">Run the program in Debug mode in Visual Studio by selecting the green arrow on the toolbar, pressing F5, or choosing the **Debug** > **Start Debugging** menu item.</span></span> <span data-ttu-id="1140a-152">Bir ad girmeniz ve Enter tuşuna basarak istemine yanıt.</span><span class="sxs-lookup"><span data-stu-id="1140a-152">Respond to the prompt by entering a name and pressing the Enter key.</span></span>

   ![Konsol penceresi ile değiştirilmiş program çıktısı](./media/with-visual-studio/hello-world-update.png)

1. <span data-ttu-id="1140a-154">Konsol penceresini kapatmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="1140a-154">Press any key to close the console window.</span></span>

<span data-ttu-id="1140a-155">Oluşturduğunuz ve uygulamanızı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1140a-155">You've created and run your application.</span></span> <span data-ttu-id="1140a-156">Profesyonel uygulama geliştirmek için uygulamanız yayımlanmaya hazır hale getirmek için bazı ek adımlar uygulayın:</span><span class="sxs-lookup"><span data-stu-id="1140a-156">To develop a professional application, take some additional steps to make your application ready for release:</span></span>

- <span data-ttu-id="1140a-157">Uygulamanızda hata ayıklamak için bkz: [Visual Studio 2017 kullanarak .NET Core Merhaba Dünya uygulamanızın hatalarını](debugging-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="1140a-157">To debug your application, see [Debug your .NET Core Hello World application using Visual Studio 2017](debugging-with-visual-studio.md).</span></span>

- <span data-ttu-id="1140a-158">Uygulamanızı bir dağıtılabilir sürümünü yayımlamak için bkz: [Visual Studio 2017 ile .NET Core Merhaba Dünya uygulamanızı yayımlama](publishing-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="1140a-158">To publish a distributable version of your application, see [Publish your .NET Core Hello World application with Visual Studio 2017](publishing-with-visual-studio.md).</span></span>

<!--
## Related topics

Instead of a console application, you can also build a class library with .NET Core and Visual Studio 2017. For a step-by-step introduction, see [Building a class library with C# and .NET Core in Visual Studio 2017](library-with-visual-studio.md).

You can also develop a .NET Core console app on Mac, Linux, and Windows by using [Visual Studio Code](https://code.visualstudio.com/), a downloadable code editor. For a step-by-step tutorial, see [Getting Started with Visual Studio Code](with-visual-studio-code.md). -->
