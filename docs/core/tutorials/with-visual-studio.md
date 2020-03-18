---
title: Visual Studio'da .NET Core ile Bir Merhaba Dünya uygulaması oluşturun
description: Visual Studio'yu kullanarak C# veya Visual Basic ile ilk .NET Core konsol uygulamanızı nasıl oluşturabilirsiniz öğrenin.
author: BillWagner
ms.author: wiwagn
ms.date: 12/09/2019
ms.custom: vs-dotnet
ms.openlocfilehash: ba996e4add1cfe44681154b00a6530b1f3e70b37
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714008"
---
# <a name="tutorial-create-your-first-net-core-console-application-in-visual-studio-2019"></a><span data-ttu-id="12025-103">Öğretici: Visual Studio 2019'da ilk .NET Core konsol uygulamanızı oluşturun</span><span class="sxs-lookup"><span data-stu-id="12025-103">Tutorial: Create your first .NET Core console application in Visual Studio 2019</span></span>

<span data-ttu-id="12025-104">Bu makale, Visual Studio 2019'da Hello World .NET Core konsol uygulaması oluşturmak ve çalıştırmak için adım adım giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="12025-104">This article provides a step-by-step introduction to create and run a Hello World .NET Core console application in Visual Studio 2019.</span></span> <span data-ttu-id="12025-105">Bir Hello World uygulaması geleneksel olarak yeni bir programlama dili yeni başlayanlar tanıtmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="12025-105">A Hello World application is traditionally used to introduce beginners to a new programming language.</span></span> <span data-ttu-id="12025-106">Bu program sadece ifade görüntüler "Merhaba Dünya!"</span><span class="sxs-lookup"><span data-stu-id="12025-106">This program simply displays the phrase "Hello World!"</span></span> <span data-ttu-id="12025-107">iletisini yazdırdı.</span><span class="sxs-lookup"><span data-stu-id="12025-107">on the screen.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="12025-108">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="12025-108">Prerequisites</span></span>

- <span data-ttu-id="12025-109">[Visual Studio 2019 sürüm 16.4 veya](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) daha sonraki bir sürümü **.NET Core çapraz platform geliştirme** iş yükü yüklü.</span><span class="sxs-lookup"><span data-stu-id="12025-109">[Visual Studio 2019 version 16.4 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="12025-110">.NET Core 3.1 Bu iş yükünü seçtiğinizde Otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="12025-110">.NET Core 3.1 SDK is automatically installed when you select this workload.</span></span>

<span data-ttu-id="12025-111">Daha fazla bilgi için [,.NET Core SDK](../install/sdk.md?pivots=os-windows) makalesini [yükleyin Visual Studio ile Yükle](../install/sdk.md?pivots=os-windows#install-with-visual-studio) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="12025-111">For more information, see the [Install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) section on the [Install the .NET Core SDK](../install/sdk.md?pivots=os-windows) article.</span></span>

## <a name="create-the-app"></a><span data-ttu-id="12025-112">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="12025-112">Create the app</span></span>

<span data-ttu-id="12025-113">Aşağıdaki talimatlar basit bir Hello World konsol uygulaması oluşturur:</span><span class="sxs-lookup"><span data-stu-id="12025-113">The following instructions create a simple Hello World console application:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[<span data-ttu-id="12025-114">C #</span><span class="sxs-lookup"><span data-stu-id="12025-114">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="12025-115">Görsel Stüdyo 2019'u açın.</span><span class="sxs-lookup"><span data-stu-id="12025-115">Open Visual Studio 2019.</span></span>

1. <span data-ttu-id="12025-116">"HelloWorld" adında yeni bir C# .NET Core konsol uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="12025-116">Create a new C# .NET Core console app project named "HelloWorld".</span></span>

   1. <span data-ttu-id="12025-117">Başlangıç penceresinde yeni **bir proje oluştur'u**seçin.</span><span class="sxs-lookup"><span data-stu-id="12025-117">On the start window, choose **Create a new project**.</span></span>

      ![Visual Studio başlangıç penceresinde seçilen yeni bir proje düğmesi oluşturma](./media/with-visual-studio/start-window.png)

   1. <span data-ttu-id="12025-119">Yeni **bir proje oluştur** sayfasında, arama kutusuna **konsolgirin.**</span><span class="sxs-lookup"><span data-stu-id="12025-119">On the **Create a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="12025-120">Ardından, Dil listesinden **C#'yi** seçin ve ardından Platform listesinden **Tüm platformları** seçin.</span><span class="sxs-lookup"><span data-stu-id="12025-120">Next, choose **C#** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="12025-121">Konsol **Uygulaması (.NET Core)** şablonunu seçin ve ardından **İleri'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="12025-121">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

      ![Filtreler seçili yeni bir proje penceresi oluşturma](./media/with-visual-studio/create-new-project.png)

      > [!TIP]
      > <span data-ttu-id="12025-123">.NET Core şablonlarını görmüyorsanız, yüklü olan gerekli iş yükünü büyük olasılıkla kaçırıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="12025-123">If you don't see the .NET Core templates, you're probably missing the required workload installed.</span></span> <span data-ttu-id="12025-124">**Aradığınızı bulamıyor?** iletinin **altında, daha fazla araç ve özellik yükle** bağlantısını seçin.</span><span class="sxs-lookup"><span data-stu-id="12025-124">Under the **Not finding what you're looking for?** message, choose the **Install more tools and features** link.</span></span> <span data-ttu-id="12025-125">Visual Studio Yükleyici açılır.</span><span class="sxs-lookup"><span data-stu-id="12025-125">The Visual Studio Installer opens.</span></span> <span data-ttu-id="12025-126">**.NET Core çapraz platform geliştirme** iş yükünün yüklü olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="12025-126">Make sure you have the **.NET Core cross-platform development** workload installed.</span></span>

   1. <span data-ttu-id="12025-127">Yeni **proje sayfanızı Yapılandır'da,** **Project ad** kutusuna **HelloWorld'u** girin.</span><span class="sxs-lookup"><span data-stu-id="12025-127">On the **Configure your new project** page,  enter **HelloWorld** in the **Project name** box.</span></span> <span data-ttu-id="12025-128">Ardından **Oluştur'u**seçin.</span><span class="sxs-lookup"><span data-stu-id="12025-128">Then, choose **Create**.</span></span>

      ![Yeni proje pencerenizi Proje adı, konum ve çözüm adı alanlarıyla yapılandırma](./media/with-visual-studio/configure-new-project.png)

   <span data-ttu-id="12025-130">.NET Core için C# Console Application şablonu, `Program`bir <xref:System.String> diziyi `Main`bağımsız değişken olarak alan bir sınıfı otomatik olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="12025-130">The C# Console Application template for .NET Core automatically defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="12025-131">`Main`uygulama giriş noktasıdır, uygulamayı başlattığında çalışma süresine göre otomatik olarak çağrılan yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="12025-131">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="12025-132">Uygulama başlatıldığında sağlanan tüm komut satırı bağımsız *değişkenleri args* dizisinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="12025-132">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

   ![Visual Studio ve yeni HelloWorld projesi](./media/with-visual-studio/visual-studio-main-window.png)

# <a name="visual-basic"></a>[<span data-ttu-id="12025-134">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="12025-134">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="12025-135">Görsel Stüdyo 2019'u açın.</span><span class="sxs-lookup"><span data-stu-id="12025-135">Open Visual Studio 2019.</span></span>

1. <span data-ttu-id="12025-136">"HelloWorld" adlı yeni bir Visual Basic .NET Core konsol uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="12025-136">Create a new Visual Basic .NET Core console app project named "HelloWorld".</span></span>

   1. <span data-ttu-id="12025-137">Başlangıç penceresinde yeni **bir proje oluştur'u**seçin.</span><span class="sxs-lookup"><span data-stu-id="12025-137">On the start window, choose **Create a new project**.</span></span>

      ![Visual Studio başlangıç penceresinde seçilen yeni bir proje düğmesi oluşturma](./media/with-visual-studio/start-window.png)

   1. <span data-ttu-id="12025-139">Yeni **bir proje oluştur** sayfasında, arama kutusuna **konsolgirin.**</span><span class="sxs-lookup"><span data-stu-id="12025-139">On the **Create a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="12025-140">Ardından, Dil listesinden **Visual Basic'i** seçin ve ardından Platform listesindeki **Tüm platformları** seçin.</span><span class="sxs-lookup"><span data-stu-id="12025-140">Next, choose **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="12025-141">Konsol **Uygulaması (.NET Core)** şablonunu seçin ve ardından **İleri'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="12025-141">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

      ![Konsol Uygulaması için Visual Basic şablonu (.NET Framework) seçeneğini seçin](./media/with-visual-studio/vb/create-new-project.png)

      > [!TIP]
      > <span data-ttu-id="12025-143">.NET Core şablonlarını görmüyorsanız, yüklü olan gerekli iş yükünü büyük olasılıkla kaçırıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="12025-143">If you don't see the .NET Core templates, you're probably missing the required workload installed.</span></span> <span data-ttu-id="12025-144">**Aradığınızı bulamıyor?** iletinin **altında, daha fazla araç ve özellik yükle** bağlantısını seçin.</span><span class="sxs-lookup"><span data-stu-id="12025-144">Under the **Not finding what you're looking for?** message, choose the **Install more tools and features** link.</span></span> <span data-ttu-id="12025-145">Visual Studio Yükleyici açılır.</span><span class="sxs-lookup"><span data-stu-id="12025-145">The Visual Studio Installer opens.</span></span> <span data-ttu-id="12025-146">**.NET Core çapraz platform geliştirme** iş yükünün yüklü olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="12025-146">Make sure you have the **.NET Core cross-platform development** workload installed.</span></span>

   1. <span data-ttu-id="12025-147">Yeni **proje sayfanızı Yapılandır'da,** **Project ad** kutusuna **HelloWorld'u** girin.</span><span class="sxs-lookup"><span data-stu-id="12025-147">On the **Configure your new project** page,  enter **HelloWorld** in the **Project name** box.</span></span> <span data-ttu-id="12025-148">Ardından **Oluştur'u**seçin.</span><span class="sxs-lookup"><span data-stu-id="12025-148">Then, choose **Create**.</span></span>

   <span data-ttu-id="12025-149">.NET Core konsol uygulaması şablonu, bir `Program` <xref:System.String> diziyi bağımsız değişken `Main`olarak alan bir sınıfı otomatik olarak tek bir yöntemle tanımlar.</span><span class="sxs-lookup"><span data-stu-id="12025-149">The console app template for .NET Core automatically defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="12025-150">`Main`uygulama giriş noktasıdır, uygulamayı başlattığında çalışma süresine göre otomatik olarak çağrılan yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="12025-150">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="12025-151">Uygulama başlatıldığında sağlanan tüm komut satırı bağımsız `args` değişkenleri parametrede kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="12025-151">Any command-line arguments supplied when the application is launched are available in the `args` parameter.</span></span>

   ![Visual Studio ve yeni HelloWorld projesi](./media/with-visual-studio/vb/visual-studio-main-window.png)

---

   <span data-ttu-id="12025-153">Şablon basit bir "Hello World" uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="12025-153">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="12025-154">Bu kelime <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> dizesini görüntülemek için yöntem çağırır "Merhaba Dünya!"</span><span class="sxs-lookup"><span data-stu-id="12025-154">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display the literal string "Hello World!"</span></span> <span data-ttu-id="12025-155">konsol penceresinde.</span><span class="sxs-lookup"><span data-stu-id="12025-155">in the console window.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="12025-156">Uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="12025-156">Run the app</span></span>

1. <span data-ttu-id="12025-157">Programı çalıştırmak için araç çubuğunda **HelloWorld'u** seçin veya **F5 tuşuna**basın.</span><span class="sxs-lookup"><span data-stu-id="12025-157">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

   ![HelloWorld çalıştır düğmesi seçili Visual Studio araç çubuğu](./media/with-visual-studio/run-program.png)

   <span data-ttu-id="12025-159">"Merhaba Dünya!" metniyle bir konsol penceresi açılır.</span><span class="sxs-lookup"><span data-stu-id="12025-159">A console window opens with the text "Hello World!"</span></span> <span data-ttu-id="12025-160">ekrana ve bazı Visual Studio hata ayıklama bilgileri yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="12025-160">printed on the screen and some Visual Studio debug information.</span></span>

   ![Devam etmek için Hello World Press tuşlarını gösteren konsol penceresi](./media/with-visual-studio/hello-world-console.png)

1. <span data-ttu-id="12025-162">Konsol penceresini kapatmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="12025-162">Press any key to close the console window.</span></span>

## <a name="enhance-the-app"></a><span data-ttu-id="12025-163">Uygulamayı geliştirin</span><span class="sxs-lookup"><span data-stu-id="12025-163">Enhance the app</span></span>

<span data-ttu-id="12025-164">Kullanıcıdan adını almak için uygulamanızı geliştirin ve tarih ve saatle birlikte görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="12025-164">Enhance your application to prompt the user for their name and display it along with the date and time.</span></span> <span data-ttu-id="12025-165">Aşağıdaki talimatlar uygulamayı değiştirip yeniden çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="12025-165">The following instructions modify and run the app again:</span></span>

# <a name="c"></a>[<span data-ttu-id="12025-166">C #</span><span class="sxs-lookup"><span data-stu-id="12025-166">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="12025-167">Şu anda `Main` sadece çağıran satır `Console.WriteLine`olan yöntemin içeriğini aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="12025-167">Replace the contents of the `Main` method, which is currently just the line that calls `Console.WriteLine`, with the following code:</span></span>

   [!code-csharp[GettingStarted#1](~/samples/snippets/csharp/getting_started/with_visual_studio/helloworld.cs#1)]

   <span data-ttu-id="12025-168">Bu kod "Adınız nedir?"</span><span class="sxs-lookup"><span data-stu-id="12025-168">This code displays "What is your name?"</span></span> <span data-ttu-id="12025-169">konsol penceresinde ve kullanıcı enter tuşu ardından bir dize girene kadar bekler.</span><span class="sxs-lookup"><span data-stu-id="12025-169">in the console window and waits until the user enters a string followed by the Enter key.</span></span> <span data-ttu-id="12025-170">Bu dizeyi . `name`</span><span class="sxs-lookup"><span data-stu-id="12025-170">It stores this string into a variable named `name`.</span></span> <span data-ttu-id="12025-171">Ayrıca, geçerli yerel saati <xref:System.DateTime.Now?displayProperty=nameWithType> içeren özelliğin değerini alır ve onu adlı `date`bir değişkene atar.</span><span class="sxs-lookup"><span data-stu-id="12025-171">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="12025-172">Son olarak, konsol penceresinde bu değerleri görüntülemek için [bir enterpolasyonlu dize](../../csharp/language-reference/tokens/interpolated.md) kullanır.</span><span class="sxs-lookup"><span data-stu-id="12025-172">Finally, it uses an [interpolated string](../../csharp/language-reference/tokens/interpolated.md) to display these values in the console window.</span></span>

1. <span data-ttu-id="12025-173">**Yapı** > **Çözüm'üne**seçerek programı derle.</span><span class="sxs-lookup"><span data-stu-id="12025-173">Compile the program by choosing **Build** > **Build Solution**.</span></span>

1. <span data-ttu-id="12025-174">Programı çalıştırmak için araç çubuğunda **HelloWorld'u** seçin veya **F5 tuşuna**basın.</span><span class="sxs-lookup"><span data-stu-id="12025-174">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

1. <span data-ttu-id="12025-175">Bir ad girerek ve **Enter** tuşuna basarak istemi yanıtlayın.</span><span class="sxs-lookup"><span data-stu-id="12025-175">Respond to the prompt by entering a name and pressing the **Enter** key.</span></span>

   ![Değiştirilmiş program çıktılı konsol penceresi](./media/with-visual-studio/hello-world-update.png)

1. <span data-ttu-id="12025-177">Konsol penceresini kapatmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="12025-177">Press any key to close the console window.</span></span>

# <a name="visual-basic"></a>[<span data-ttu-id="12025-178">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="12025-178">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="12025-179">Şu anda `Main` sadece çağıran satır `Console.WriteLine`olan yöntemin içeriğini aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="12025-179">Replace the contents of the `Main` method, which is currently just the line that calls `Console.WriteLine`, with the following code:</span></span>

   [!code-vb[GettingStarted#1](~/samples/snippets/core/tutorials/vb-with-visual-studio/helloworld.vb#1)]

   <span data-ttu-id="12025-180">Bu kod "Adınız nedir?"</span><span class="sxs-lookup"><span data-stu-id="12025-180">This code displays "What is your name?"</span></span> <span data-ttu-id="12025-181">konsol penceresinde ve kullanıcı enter tuşu ardından bir dize girene kadar bekler.</span><span class="sxs-lookup"><span data-stu-id="12025-181">in the console window and waits until the user enters a string followed by the Enter key.</span></span> <span data-ttu-id="12025-182">Bu dizeyi . `name`</span><span class="sxs-lookup"><span data-stu-id="12025-182">It stores this string into a variable named `name`.</span></span> <span data-ttu-id="12025-183">Ayrıca, geçerli yerel saati <xref:System.DateTime.Now?displayProperty=nameWithType> içeren özelliğin değerini alır ve onu adlı `date`bir değişkene atar.</span><span class="sxs-lookup"><span data-stu-id="12025-183">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="12025-184">Son olarak, konsol penceresinde bu değerleri görüntülemek için [bir enterpolasyonlu dize](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) kullanır.</span><span class="sxs-lookup"><span data-stu-id="12025-184">Finally, it uses an [interpolated string](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) to display these values in the console window.</span></span>

1. <span data-ttu-id="12025-185">**Yapı** > **Çözüm'üne**seçerek programı derle.</span><span class="sxs-lookup"><span data-stu-id="12025-185">Compile the program by choosing **Build** > **Build Solution**.</span></span>

1. <span data-ttu-id="12025-186">Programı çalıştırmak için araç çubuğunda **HelloWorld'u** seçin veya **F5 tuşuna**basın.</span><span class="sxs-lookup"><span data-stu-id="12025-186">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

1. <span data-ttu-id="12025-187">Bir ad girerek ve **Enter** tuşuna basarak istemi yanıtlayın.</span><span class="sxs-lookup"><span data-stu-id="12025-187">Respond to the prompt by entering a name and pressing the **Enter** key.</span></span>

   ![Değiştirilmiş program çıktılı konsol penceresi](./media/with-visual-studio/hello-world-update.png)

1. <span data-ttu-id="12025-189">Konsol penceresini kapatmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="12025-189">Press any key to close the console window.</span></span>

---

## <a name="next-steps"></a><span data-ttu-id="12025-190">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="12025-190">Next steps</span></span>

<span data-ttu-id="12025-191">Bu makalede, ilk .NET Core uygulamanızı oluşturdunuz ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="12025-191">In this article, you've created and run your first .NET Core application.</span></span> <span data-ttu-id="12025-192">Bir sonraki adımda, uygulamanızı hata ayıklama.</span><span class="sxs-lookup"><span data-stu-id="12025-192">In the next step, you debug your app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="12025-193">Visual Studio'da Hata Ayıklama .NET Core Hello World uygulaması</span><span class="sxs-lookup"><span data-stu-id="12025-193">Debug a .NET Core Hello World application in Visual Studio</span></span>](debugging-with-visual-studio.md)
