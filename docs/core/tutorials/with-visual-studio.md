---
title: ".NET Core ve C# Visual Studio 2017'Hello World uygulaması oluşturma"
description: "Basit bir .NET Core konsol uygulaması Visual Studio 2017 kullanarak C# ile oluşturmayı öğrenin."
keywords: ".NET core, .NET Core konsol uygulaması, Visual Studio 2017"
author: BillWagner
ms.author: wiwagn
ms.date: 09/13/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 97aa50bf-bdf8-416d-a56c-ac77504c14ea
ms.workload:
- dotnetcore
ms.openlocfilehash: 21b36bfa355bbea1b078c4bd29afdf5afeb61453
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2018
---
# <a name="build-a-c-hello-world-application-with-net-core-in-visual-studio-2017"></a><span data-ttu-id="63459-104">Bir C# Hello World uygulamasının Visual Studio 2017 .NET çekirdek ile derleme</span><span class="sxs-lookup"><span data-stu-id="63459-104">Build a C# Hello World application with .NET Core in Visual Studio 2017</span></span>

<span data-ttu-id="63459-105">Bu konuda oluşturma, hata ayıklama ve C# Visual Studio 2017 kullanarak basit bir .NET Core konsol uygulaması yayımlama için adım adım bir giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="63459-105">This topic provides a step-by-step introduction to building, debugging, and publishing a simple .NET Core console application using C# in Visual Studio 2017.</span></span> <span data-ttu-id="63459-106">Visual Studio 2017 .NET Core uygulamaları oluşturmak için bir tam özellikli bir geliştirme ortamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="63459-106">Visual Studio 2017 provides a full-featured development environment for building .NET Core applications.</span></span> <span data-ttu-id="63459-107">Uygulama platforma özgü bağımlılıklar yok sürece, uygulama .NET Core hedefleyen herhangi bir platformda çalışabilir ve .NET Core sahip herhangi bir sisteminde yüklü.</span><span class="sxs-lookup"><span data-stu-id="63459-107">As long as the application doesn't have platform-specific dependencies, the application can run on any platform that .NET Core targets and on any system that has .NET Core installed.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="63459-108">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="63459-108">Prerequisites</span></span>

<span data-ttu-id="63459-109">[Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) yüklü ".NET Core platformlar arası geliştirme" iş yükü ile.</span><span class="sxs-lookup"><span data-stu-id="63459-109">[Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) with the ".NET Core cross-platform development" workload installed.</span></span> <span data-ttu-id="63459-110">.NET Core 1.1 veya .NET Core 2.0 ile uygulamanızı geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="63459-110">You can develop your app with either .NET Core 1.1 or .NET Core 2.0.</span></span>

<span data-ttu-id="63459-111">Daha fazla bilgi için bkz: [.NET Core Windows önkoşulları](../../core/windows-prerequisites.md) konu.</span><span class="sxs-lookup"><span data-stu-id="63459-111">For more information, see the [Prerequisites for .NET Core on Windows](../../core/windows-prerequisites.md) topic.</span></span>

## <a name="a-simple-hello-world-application"></a><span data-ttu-id="63459-112">Basit bir Hello World uygulamasının</span><span class="sxs-lookup"><span data-stu-id="63459-112">A simple Hello World application</span></span>

<span data-ttu-id="63459-113">Basit bir "Hello World" konsol uygulaması oluşturarak başlayın.</span><span class="sxs-lookup"><span data-stu-id="63459-113">Begin by creating a simple "Hello World" console application.</span></span> <span data-ttu-id="63459-114">Aşağıdaki adımları uygulayın:</span><span class="sxs-lookup"><span data-stu-id="63459-114">Follow these steps:</span></span>

1. <span data-ttu-id="63459-115">Visual Studio 2017 başlatın.</span><span class="sxs-lookup"><span data-stu-id="63459-115">Launch Visual Studio 2017.</span></span> <span data-ttu-id="63459-116">Seçin **dosya** > **yeni** > **proje** menü çubuğundan.</span><span class="sxs-lookup"><span data-stu-id="63459-116">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="63459-117">İçinde *yeni proje*\* iletişim kutusunda **Visual C#** düğümünü ve ardından **.NET Core** düğümü.</span><span class="sxs-lookup"><span data-stu-id="63459-117">In the *New Project*\* dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="63459-118">Ardından **konsol uygulaması (.NET Core)** proje şablonu.</span><span class="sxs-lookup"><span data-stu-id="63459-118">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="63459-119">İçinde **adı** metin kutusuna, "HelloWorld" yazın.</span><span class="sxs-lookup"><span data-stu-id="63459-119">In the **Name** text box, type "HelloWorld".</span></span> <span data-ttu-id="63459-120">Seçin **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="63459-120">Select the **OK** button.</span></span>

   ![Konsol seçilen uygulama ile yeni proje iletişim kutusu](./media/with-visual-studio/newproject.png)
   
1. <span data-ttu-id="63459-122">Visual Studio projenizi oluşturmak için şablon kullanır.</span><span class="sxs-lookup"><span data-stu-id="63459-122">Visual Studio uses the template to create your project.</span></span> <span data-ttu-id="63459-123">.NET Core için C# konsol uygulaması şablonu otomatik olarak bir sınıf tanımlar `Program`, tek bir yöntem ile `Main`, alan bir <xref:System.String> bağımsız değişken olarak bir dizi.</span><span class="sxs-lookup"><span data-stu-id="63459-123">The C# Console Application template for .NET Core automatically defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="63459-124">`Main` Uygulama giriş noktası, uygulama başlatıldığında otomatik olarak çalışma zamanı tarafından çağrılan yöntemi niteliğindedir.</span><span class="sxs-lookup"><span data-stu-id="63459-124">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="63459-125">Uygulama başlatıldığında sağlanan tüm komut satırı bağımsız değişkenleri kullanılabilir *args* dizi.</span><span class="sxs-lookup"><span data-stu-id="63459-125">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

   ![Visual Studio ve yeni HelloWorld projesi](./media/with-visual-studio/devenv.png)

   <span data-ttu-id="63459-127">Şablon, basit bir "Hello World" uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="63459-127">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="63459-128">Çağırır <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> değişmez değer dize "Hello World!" görüntülenecek yöntemi</span><span class="sxs-lookup"><span data-stu-id="63459-128">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display the literal string "Hello World!"</span></span> <span data-ttu-id="63459-129">Konsol penceresinde.</span><span class="sxs-lookup"><span data-stu-id="63459-129">in the console window.</span></span> <span data-ttu-id="63459-130">Seçerek **HelloWorld** düğmesi araç çubuğundaki yeşil ok ile hata ayıklama modunda program çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="63459-130">By selecting the **HelloWorld** button with the green arrow on the toolbar, you can run the program in Debug mode.</span></span> <span data-ttu-id="63459-131">Bunu yaparsanız, kapanmadan önce konsol penceresi yalnızca kısa zaman aralığı için görünür olur.</span><span class="sxs-lookup"><span data-stu-id="63459-131">If you do, the console window is visible for only a brief time interval before it closes.</span></span> <span data-ttu-id="63459-132">Bu kaynaklanır `Main` yöntemi sonlandırır ve uygulama sona tek deyiminde olan en kısa sürede `Main` yöntemini yürütür.</span><span class="sxs-lookup"><span data-stu-id="63459-132">This occurs because the `Main` method terminates and the application ends as soon as the single statement in the `Main` method executes.</span></span>

1. <span data-ttu-id="63459-133">Konsol penceresinde kapanmadan önce duraklatmak uygulamanın neden için çağırdıktan hemen sonra aşağıdaki kodu ekleyin <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> yöntemi:</span><span class="sxs-lookup"><span data-stu-id="63459-133">To cause the application to pause before it closes the console window, add the following code immediately after the call to the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method:</span></span>

   ```csharp
   Console.Write("Press any key to continue...");
   Console.ReadKey(true);
   ```
   <span data-ttu-id="63459-134">Bu kod, kullanıcıdan herhangi bir tuşa basın ve bir tuşuna basılana kadar program duraklatılır.</span><span class="sxs-lookup"><span data-stu-id="63459-134">This code prompts the user to press any key and then pauses the program until a key is pressed.</span></span>

1. <span data-ttu-id="63459-135">Menü çubuğunda seçin **yapı** > **yapı çözümü**.</span><span class="sxs-lookup"><span data-stu-id="63459-135">On the menu bar, select **Build** > **Build Solution**.</span></span> <span data-ttu-id="63459-136">Tam zamanında (JIT) derleyici tarafından ikili koda dönüştürülür bir ara dile (IL) programınızı derler.</span><span class="sxs-lookup"><span data-stu-id="63459-136">This compiles your program into an intermediate language (IL) that's converted into binary code by a just-in-time (JIT) compiler.</span></span>

1. <span data-ttu-id="63459-137">Seçerek program Çalıştır **HelloWorld** araç çubuğundaki Yeşil oklu düğmesi.</span><span class="sxs-lookup"><span data-stu-id="63459-137">Run the program by selecting the **HelloWorld** button with the green arrow on the toolbar.</span></span>

   ![Devam etmek için herhangi bir tuşa Hello World tuşuna gösteren konsol penceresi](./media/with-visual-studio/helloworld1.png)

1. <span data-ttu-id="63459-139">Konsol penceresini kapatmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="63459-139">Press any key to close the console window.</span></span>

## <a name="enhancing-the-hello-world-application"></a><span data-ttu-id="63459-140">Hello World uygulamasının geliştirme</span><span class="sxs-lookup"><span data-stu-id="63459-140">Enhancing the Hello World application</span></span>

<span data-ttu-id="63459-141">Kullanıcıdan adına ve tarih ve saati ile birlikte görüntülemek için uygulamanızı geliştirin.</span><span class="sxs-lookup"><span data-stu-id="63459-141">Enhance your application to prompt the user for their name and display it along with the date and time.</span></span> <span data-ttu-id="63459-142">Program sınamak ve değiştirmek için aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="63459-142">To modify and test the program, do the following:</span></span>

1. <span data-ttu-id="63459-143">Aşağıdaki C# kodu code penceresinde aşağıdaki hemen ayraç sonra girin `static void Main(string[] args)` satır ve ilk ayraç önce:</span><span class="sxs-lookup"><span data-stu-id="63459-143">Enter the following C# code in the code window immediately after the opening bracket that follows the `static void Main(string[] args)` line and before the first closing bracket:</span></span>

   [!code-csharp[GettingStarted#1](../../../samples/snippets/csharp/getting_started/with_visual_studio/helloworld.cs#1)]

   <span data-ttu-id="63459-144">Bu kod varolan değiştirir <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, <xref:System.Console.Write%2A?displayProperty=nameWithType>, ve <xref:System.Console.ReadKey%2A?displayProperty=nameWithType> deyimleri.</span><span class="sxs-lookup"><span data-stu-id="63459-144">This code replaces the existing <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, <xref:System.Console.Write%2A?displayProperty=nameWithType>, and <xref:System.Console.ReadKey%2A?displayProperty=nameWithType> statements.</span></span>

   ![Visual Studio Program c-sharp dosyasını güncelleştirilmiş Main yöntemi](./media/with-visual-studio/codewindow.png)

   <span data-ttu-id="63459-146">Bu kodu ", adı nedir?" görüntüler</span><span class="sxs-lookup"><span data-stu-id="63459-146">This code displays "What is your name?"</span></span> <span data-ttu-id="63459-147">Kullanıcı kadar bekler ve konsol penceresi Enter tuşuna bir dize girer.</span><span class="sxs-lookup"><span data-stu-id="63459-147">in the console window and waits until the user enters a string followed by the Enter key.</span></span> <span data-ttu-id="63459-148">Bu dize adlı bir değişkende depolar `name`.</span><span class="sxs-lookup"><span data-stu-id="63459-148">It stores this string into a variable named `name`.</span></span> <span data-ttu-id="63459-149">Ayrıca değerini alır <xref:System.DateTime.Now?displayProperty=nameWithType> geçerli yerel saat içeren ve adlı bir değişkene atar özelliği `date`.</span><span class="sxs-lookup"><span data-stu-id="63459-149">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="63459-150">Son olarak, kullanan bir [Ara değerli dize](../../csharp/language-reference/keywords/interpolated-strings.md) konsol penceresinde bu değerleri görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="63459-150">Finally, it uses an [interpolated string](../../csharp/language-reference/keywords/interpolated-strings.md) to display these values in the console window.</span></span>

1. <span data-ttu-id="63459-151">Program seçerek derleme **yapı** > **yapı çözümü**.</span><span class="sxs-lookup"><span data-stu-id="63459-151">Compile the program by choosing **Build** > **Build Solution**.</span></span>

1. <span data-ttu-id="63459-152">Araç çubuğundaki yeşil ok tuşunu seçerek, F5 tuşuna basarak veya belirleyerek Visual Studio'da hata ayıklama modunda programı çalıştırın **hata ayıklama** > **hata ayıklamayı Başlat** menü öğesi.</span><span class="sxs-lookup"><span data-stu-id="63459-152">Run the program in Debug mode in Visual Studio by selecting the green arrow on the toolbar, pressing F5, or choosing the **Debug** > **Start Debugging** menu item.</span></span> <span data-ttu-id="63459-153">Bir ad girin ve Enter tuşuna basarak komutuna yanıt.</span><span class="sxs-lookup"><span data-stu-id="63459-153">Respond to the prompt by entering a name and pressing the Enter key.</span></span>

   ![Değiştirilen program çıkış konsol penceresi](./media/with-visual-studio/helloworld2.png)

1. <span data-ttu-id="63459-155">Konsol penceresini kapatmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="63459-155">Press any key to close the console window.</span></span>

<span data-ttu-id="63459-156">Oluşturulan artık ve uygulamanızı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="63459-156">You've created and run your application.</span></span> <span data-ttu-id="63459-157">Profesyonel bir uygulama geliştirmek için uygulamanızı sürüm için hazır hale getirmek için bazı ek adımlar uygulayın:</span><span class="sxs-lookup"><span data-stu-id="63459-157">To develop a professional application, take some additional steps to make your application ready for release:</span></span>

- <span data-ttu-id="63459-158">Uygulamanızın hatalarını ayıklama hakkında daha fazla bilgi için bkz: [C# Hello World uygulamanızı Visual Studio 2017 ile hata ayıklama](debugging-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="63459-158">For information on debugging your application, see [Debugging your C# Hello World application with Visual Studio 2017](debugging-with-visual-studio.md).</span></span>

- <span data-ttu-id="63459-159">Geliştirme ve uygulamanızın dağıtılabilir sürümünü yayımlama hakkında daha fazla bilgi için bkz: [C# Hello World uygulamanızla Visual Studio 2017 yayımlama](publishing-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="63459-159">For information on developing and publishing a distributable version of your application, see [Publishing your C# Hello World application with Visual Studio 2017](publishing-with-visual-studio.md).</span></span>

## <a name="related-topics"></a><span data-ttu-id="63459-160">İlgili konular</span><span class="sxs-lookup"><span data-stu-id="63459-160">Related topics</span></span>

<span data-ttu-id="63459-161">Bir konsol uygulaması yerine bir sınıf kitaplığı .NET Core ve Visual Studio 2017 ile de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="63459-161">Instead of a console application, you can also build a class library with .NET Core and Visual Studio 2017.</span></span> <span data-ttu-id="63459-162">Adım adım bir giriş için bkz [oluşturma C# ve Visual Studio 2017 .NET çekirdek sınıf kitaplığına](library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="63459-162">For a step-by-step introduction, see [Building a class library with C# and .NET Core in Visual Studio 2017](library-with-visual-studio.md).</span></span>

<span data-ttu-id="63459-163">Mac, Linux ve Windows .NET Core konsol uygulaması kullanarak da geliştirebilirsiniz [Visual Studio Code](https://code.visualstudio.com/), indirilebilir Kod Düzenleyicisi.</span><span class="sxs-lookup"><span data-stu-id="63459-163">You can also develop a .NET Core console app on Mac, Linux, and Windows by using [Visual Studio Code](https://code.visualstudio.com/), a downloadable code editor.</span></span> <span data-ttu-id="63459-164">Adım adım bir öğretici için bkz: [Visual Studio Code ile çalışmaya başlama](with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="63459-164">For a step-by-step tutorial, see [Getting Started with Visual Studio Code](with-visual-studio-code.md).</span></span>
