---
title: "Hello World uygulamasının .NET Core ve Visual Studio 2017'de Visual Basic ile oluşturma"
description: "Visual Studio 2017 kullanarak Visual Basic ile basit bir .NET Core konsol uygulaması oluşturmayı öğrenin."
keywords: ".NET core, .NET Core konsol uygulaması, Visual Studio 2017"
author: rpetrusha
ms.author: ronpet
ms.date: 08/07/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-vb
dev_langs: vb
ms.openlocfilehash: 3ff4681f06da06533db5e8e2ce2498a31604bdb7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="build-a-visual-basic-hello-world-application-with-net-core-in-visual-studio-2017"></a><span data-ttu-id="3c9b8-104">Visual Basic Hello World uygulamasının Visual Studio 2017 .NET çekirdek ile derleme</span><span class="sxs-lookup"><span data-stu-id="3c9b8-104">Build a Visual Basic Hello World application with .NET Core in Visual Studio 2017</span></span>

<span data-ttu-id="3c9b8-105">Bu konuda oluşturma, hata ayıklama ve Visual Basic Visual Studio 2017 kullanarak basit bir .NET Core konsol uygulaması yayımlama için adım adım bir giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c9b8-105">This topic provides a step-by-step introduction to building, debugging, and publishing a simple .NET Core console application using Visual Basic in Visual Studio 2017.</span></span> <span data-ttu-id="3c9b8-106">Visual Studio 2017 .NET Core uygulamaları oluşturmak için bir tam özellikli bir geliştirme ortamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c9b8-106">Visual Studio 2017 provides a full-featured development environment for building .NET Core applications.</span></span> <span data-ttu-id="3c9b8-107">Uygulama platforma özgü bağımlılıklar yok sürece, uygulama .NET Core hedefleyen herhangi bir platformda çalışabilir ve .NET Core sahip herhangi bir sisteminde yüklü.</span><span class="sxs-lookup"><span data-stu-id="3c9b8-107">As long as the application doesn't have platform-specific dependencies, the application can run on any platform that .NET Core targets and on any system that has .NET Core installed.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3c9b8-108">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="3c9b8-108">Prerequisites</span></span>

<span data-ttu-id="3c9b8-109">[Visual Studio 2017](https://www.visualstudio.com/downloads/) yüklü ".NET Core platformlar arası geliştirme" iş yükü ile.</span><span class="sxs-lookup"><span data-stu-id="3c9b8-109">[Visual Studio 2017](https://www.visualstudio.com/downloads/) with the ".NET Core cross-platform development" workload installed.</span></span> <span data-ttu-id="3c9b8-110">.NET Core 2.0 ile uygulamanızı geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c9b8-110">You can develop your app with .NET Core 2.0.</span></span>

<span data-ttu-id="3c9b8-111">Daha fazla bilgi için bkz: [.NET Core Windows önkoşulları](../../core/windows-prerequisites.md).</span><span class="sxs-lookup"><span data-stu-id="3c9b8-111">For more information, see [Prerequisites for .NET Core on Windows](../../core/windows-prerequisites.md).</span></span>

## <a name="a-simple-hello-world-application"></a><span data-ttu-id="3c9b8-112">Basit bir Hello World uygulamasının</span><span class="sxs-lookup"><span data-stu-id="3c9b8-112">A simple Hello World application</span></span>

<span data-ttu-id="3c9b8-113">Basit bir "Hello World" konsol uygulaması oluşturarak başlayın.</span><span class="sxs-lookup"><span data-stu-id="3c9b8-113">Begin by creating a simple "Hello World" console application.</span></span> <span data-ttu-id="3c9b8-114">Aşağıdaki adımları uygulayın:</span><span class="sxs-lookup"><span data-stu-id="3c9b8-114">Follow these steps:</span></span>

1. <span data-ttu-id="3c9b8-115">Visual Studio 2017 başlatın.</span><span class="sxs-lookup"><span data-stu-id="3c9b8-115">Launch Visual Studio 2017.</span></span> <span data-ttu-id="3c9b8-116">Seçin **dosya** > **yeni** > **proje** menü çubuğundan.</span><span class="sxs-lookup"><span data-stu-id="3c9b8-116">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="3c9b8-117">İçinde *yeni proje** iletişim kutusunda **Visual Basic** düğümünü ve ardından **.NET Core** düğümü.</span><span class="sxs-lookup"><span data-stu-id="3c9b8-117">In the *New Project** dialog, select the **Visual Basic** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="3c9b8-118">Ardından **konsol uygulaması (.NET Core)** proje şablonu.</span><span class="sxs-lookup"><span data-stu-id="3c9b8-118">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="3c9b8-119">İçinde **adı** metin kutusuna, "HelloWorld" yazın.</span><span class="sxs-lookup"><span data-stu-id="3c9b8-119">In the **Name** text box, type "HelloWorld".</span></span> <span data-ttu-id="3c9b8-120">Seçin **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="3c9b8-120">Select the **OK** button.</span></span>

   ![Konsol seçilen uygulama ile yeni proje iletişim kutusu](./media/vb-with-visual-studio/new-project.png)
   
1. <span data-ttu-id="3c9b8-122">Visual Studio projenizi oluşturmak için şablon kullanır.</span><span class="sxs-lookup"><span data-stu-id="3c9b8-122">Visual Studio uses the template to create your project.</span></span> <span data-ttu-id="3c9b8-123">Visual Basic konsol uygulaması şablonu .NET Core için otomatik olarak bir sınıf tanımlar `Program`, tek bir yöntem ile `Main`, alan bir <xref:System.String> bağımsız değişken olarak bir dizi.</span><span class="sxs-lookup"><span data-stu-id="3c9b8-123">The Visual Basic Console Application template for .NET Core automatically defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="3c9b8-124">`Main`Uygulama giriş noktası, uygulama başlatıldığında otomatik olarak çalışma zamanı tarafından çağrılan yöntemi niteliğindedir.</span><span class="sxs-lookup"><span data-stu-id="3c9b8-124">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="3c9b8-125">Uygulama başlatıldığında sağlanan tüm komut satırı bağımsız değişkenleri kullanılabilir *args* dizi.</span><span class="sxs-lookup"><span data-stu-id="3c9b8-125">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

   ![Visual Studio ve yeni HelloWorld projesi](./media/vb-with-visual-studio/devenv.png)

   <span data-ttu-id="3c9b8-127">Şablon, basit bir "Hello World" uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3c9b8-127">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="3c9b8-128">Çağırır <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> değişmez değer dize "Hello World!" görüntülenecek yöntemi</span><span class="sxs-lookup"><span data-stu-id="3c9b8-128">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display the literal string "Hello World!"</span></span> <span data-ttu-id="3c9b8-129">Konsol penceresinde.</span><span class="sxs-lookup"><span data-stu-id="3c9b8-129">in the console window.</span></span> <span data-ttu-id="3c9b8-130">Seçerek **HelloWorld** düğmesi araç çubuğundaki yeşil ok ile hata ayıklama modunda program çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="3c9b8-130">By selecting the **HelloWorld** button with the green arrow on the toolbar, you can run the program in Debug mode.</span></span> <span data-ttu-id="3c9b8-131">Bunu yaparsanız, kapanmadan önce konsol penceresi yalnızca kısa zaman aralığı için görünür olur.</span><span class="sxs-lookup"><span data-stu-id="3c9b8-131">If you do, the console window is visible for only a brief time interval before it closes.</span></span> <span data-ttu-id="3c9b8-132">Bu kaynaklanır `Main` yöntemi sonlandırır ve uygulama sona tek deyiminde olan en kısa sürede `Main` yöntemini yürütür.</span><span class="sxs-lookup"><span data-stu-id="3c9b8-132">This occurs because the `Main` method terminates and the application ends as soon as the single statement in the `Main` method executes.</span></span>

1. <span data-ttu-id="3c9b8-133">Konsol penceresinde kapanmadan önce duraklatmak uygulamanın neden için çağırdıktan hemen sonra aşağıdaki kodu ekleyin <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> yöntemi:</span><span class="sxs-lookup"><span data-stu-id="3c9b8-133">To cause the application to pause before it closes the console window, add the following code immediately after the call to the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method:</span></span>

   ```vb
   Console.Write("Press any key to continue...")
   Console.ReadKey(true)
   ```
   <span data-ttu-id="3c9b8-134">Bu kod, kullanıcıdan herhangi bir tuşa basın ve bir tuşuna basılana kadar program duraklatılır.</span><span class="sxs-lookup"><span data-stu-id="3c9b8-134">This code prompts the user to press any key and then pauses the program until a key is pressed.</span></span>

1. <span data-ttu-id="3c9b8-135">Menü çubuğunda seçin **yapı** > **yapı çözümü**.</span><span class="sxs-lookup"><span data-stu-id="3c9b8-135">On the menu bar, select **Build** > **Build Solution**.</span></span> <span data-ttu-id="3c9b8-136">Tam zamanında (JIT) derleyici tarafından ikili koda dönüştürülür bir ara dile (IL) programınızı derler.</span><span class="sxs-lookup"><span data-stu-id="3c9b8-136">This compiles your program into an intermediate language (IL) that's converted into binary code by a just-in-time (JIT) compiler.</span></span>

1. <span data-ttu-id="3c9b8-137">Seçerek program Çalıştır **HelloWorld** araç çubuğundaki Yeşil oklu düğmesi.</span><span class="sxs-lookup"><span data-stu-id="3c9b8-137">Run the program by selecting the **HelloWorld** button with the green arrow on the toolbar.</span></span>

   ![Devam etmek için herhangi bir tuşa Hello World tuşuna gösteren konsol penceresi](./media/with-visual-studio/helloworld1.png)

1. <span data-ttu-id="3c9b8-139">Konsol penceresini kapatmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="3c9b8-139">Press any key to close the console window.</span></span>

## <a name="enhancing-the-hello-world-application"></a><span data-ttu-id="3c9b8-140">Hello World uygulamasının geliştirme</span><span class="sxs-lookup"><span data-stu-id="3c9b8-140">Enhancing the Hello World application</span></span>

<span data-ttu-id="3c9b8-141">Kendi adı için kullanıcıya sor ve tarih ve saati ile birlikte görüntülemek için uygulamanızı geliştirin.</span><span class="sxs-lookup"><span data-stu-id="3c9b8-141">Enhance your application to prompt the user for his or her name and to display it along with the date and time.</span></span> <span data-ttu-id="3c9b8-142">Program sınamak ve değiştirmek için aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="3c9b8-142">To modify and test the program, do the following:</span></span>

1. <span data-ttu-id="3c9b8-143">Aşağıdaki Visual Basic kodu code penceresinde aşağıdaki hemen ayraç sonra girin `Sub Main(args As String())` satır ve ilk ayraç önce:</span><span class="sxs-lookup"><span data-stu-id="3c9b8-143">Enter the following Visual Basic code in the code window immediately after the opening bracket that follows the `Sub Main(args As String())` line and before the first closing bracket:</span></span>

   [!code-vb[GettingStarted#1](../../../samples/snippets/core/tutorials/vb-with-visual-studio/helloworld.vb#1)]

   <span data-ttu-id="3c9b8-144">Bu kod varolan değiştirir <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, <xref:System.Console.Write%2A?displayProperty=nameWithType>, ve <xref:System.Console.ReadKey%2A?displayProperty=nameWithType> deyimleri.</span><span class="sxs-lookup"><span data-stu-id="3c9b8-144">This code replaces the existing <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, <xref:System.Console.Write%2A?displayProperty=nameWithType>, and <xref:System.Console.ReadKey%2A?displayProperty=nameWithType> statements.</span></span>

   ![Güncelleştirilmiş Main yöntemi ile Visual Studio Program dosyası](./media/vb-with-visual-studio/codewindow.png)

   <span data-ttu-id="3c9b8-146">Bu kodu ", adı nedir?" görüntüler</span><span class="sxs-lookup"><span data-stu-id="3c9b8-146">This code displays "What is your name?"</span></span> <span data-ttu-id="3c9b8-147">Kullanıcı kadar bekler ve konsol penceresi Enter tuşuna bir dize girer.</span><span class="sxs-lookup"><span data-stu-id="3c9b8-147">in the console window and waits until the user enters a string followed by the Enter key.</span></span> <span data-ttu-id="3c9b8-148">Bu dize adlı bir değişkende depolar `name`.</span><span class="sxs-lookup"><span data-stu-id="3c9b8-148">It stores this string into a variable named `name`.</span></span> <span data-ttu-id="3c9b8-149">Ayrıca değerini alır <xref:System.DateTime.Now?displayProperty=nameWithType> geçerli yerel saat içeren ve adlı bir değişkene atar özelliği `currentDate`.</span><span class="sxs-lookup"><span data-stu-id="3c9b8-149">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `currentDate`.</span></span> <span data-ttu-id="3c9b8-150">Son olarak, kullanan bir [Ara değerli dize](../../csharp/language-reference/keywords/interpolated-strings.md) konsol penceresinde bu değerleri görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="3c9b8-150">Finally, it uses an [interpolated string](../../csharp/language-reference/keywords/interpolated-strings.md) to display these values in the console window.</span></span>

1. <span data-ttu-id="3c9b8-151">Program seçerek derleme **yapı** > **yapı çözümü**.</span><span class="sxs-lookup"><span data-stu-id="3c9b8-151">Compile the program by choosing **Build** > **Build Solution**.</span></span>

1. <span data-ttu-id="3c9b8-152">Araç çubuğundaki yeşil ok tuşunu seçerek, F5 tuşuna basarak veya belirleyerek Visual Studio'da hata ayıklama modunda programı çalıştırın **hata ayıklama** > **hata ayıklamayı Başlat** menü öğesi.</span><span class="sxs-lookup"><span data-stu-id="3c9b8-152">Run the program in Debug mode in Visual Studio by selecting the green arrow on the toolbar, pressing F5, or choosing the **Debug** > **Start Debugging** menu item.</span></span> <span data-ttu-id="3c9b8-153">Bir ad girin ve Enter tuşuna basarak komutuna yanıt.</span><span class="sxs-lookup"><span data-stu-id="3c9b8-153">Respond to the prompt by entering a name and pressing the Enter key.</span></span>

   ![Değiştirilen program çıkış konsol penceresi](./media/with-visual-studio/helloworld2.png)

1. <span data-ttu-id="3c9b8-155">Konsol penceresini kapatmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="3c9b8-155">Press any key to close the console window.</span></span>

<span data-ttu-id="3c9b8-156">Oluşturulan artık ve uygulamanızı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3c9b8-156">You've created and run your application.</span></span> <span data-ttu-id="3c9b8-157">Profesyonel bir uygulama geliştirmek için uygulamanızı sürüm için hazır hale getirmek için bazı ek adımlar uygulayın:</span><span class="sxs-lookup"><span data-stu-id="3c9b8-157">To develop a professional application, take some additional steps to make your application ready for release:</span></span>

- <span data-ttu-id="3c9b8-158">Uygulamanızın hatalarını ayıklama hakkında daha fazla bilgi için bkz: [C# Hello World uygulamanızı Visual Studio 2017 ile hata ayıklama](debugging-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="3c9b8-158">For information on debugging your application, see [Debugging your C# Hello World application with Visual Studio 2017](debugging-with-visual-studio.md).</span></span>

- <span data-ttu-id="3c9b8-159">Geliştirme ve uygulamanızın dağıtılabilir sürümünü yayımlama hakkında daha fazla bilgi için bkz: [C# Hello World uygulamanızla Visual Studio 2017 yayımlama](publishing-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="3c9b8-159">For information on developing and publishing a distributable version of your application, see [Publishing your C# Hello World application with Visual Studio 2017](publishing-with-visual-studio.md).</span></span>

<!--
## Related topics

Instead of a console application, you can also build a class library with .NET Core and Visual Studio 2017. For a step-by-step introduction, see [Building a class library with C# and .NET Core in Visual Studio 2017](library-with-visual-studio.md).

You can also develop a .NET Core console app on Mac, Linux, and Windows by using [Visual Studio Code](https://code.visualstudio.com/), a downloadable code editor. For a step-by-step tutorial, see [Getting Started with Visual Studio Code](with-visual-studio-code.md). -->
