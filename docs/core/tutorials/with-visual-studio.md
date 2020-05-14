---
title: Visual Studio 'da .NET Core ile Merhaba Dünya uygulaması oluşturma
description: Visual Studio kullanarak C# veya Visual Basic ilk .NET Core konsol uygulamanızı oluşturmayı öğrenin.
author: BillWagner
ms.author: wiwagn
ms.date: 12/09/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 738fc49a820c3c5d94fb35c1bf7a8b718ed75cb3
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83394820"
---
# <a name="tutorial-create-your-first-net-core-console-application-in-visual-studio-2019"></a><span data-ttu-id="47e25-103">Öğretici: Visual Studio 2019 ' de ilk .NET Core konsol uygulamanızı oluşturma</span><span class="sxs-lookup"><span data-stu-id="47e25-103">Tutorial: Create your first .NET Core console application in Visual Studio 2019</span></span>

<span data-ttu-id="47e25-104">Bu makalede, Visual Studio 2019 ' de Merhaba Dünya .NET Core konsol uygulaması oluşturmak ve çalıştırmak için adım adım bir giriş sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="47e25-104">This article provides a step-by-step introduction to create and run a Hello World .NET Core console application in Visual Studio 2019.</span></span> <span data-ttu-id="47e25-105">Bir Merhaba Dünya uygulaması, genellikle yeni bir programlama diline yeni başlayanlar tanıtmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="47e25-105">A Hello World application is traditionally used to introduce beginners to a new programming language.</span></span> <span data-ttu-id="47e25-106">Bu program yalnızca "Merhaba Dünya!" ifadesini görüntüler</span><span class="sxs-lookup"><span data-stu-id="47e25-106">This program simply displays the phrase "Hello World!"</span></span> <span data-ttu-id="47e25-107">iletisini yazdırdı.</span><span class="sxs-lookup"><span data-stu-id="47e25-107">on the screen.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="47e25-108">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="47e25-108">Prerequisites</span></span>

- <span data-ttu-id="47e25-109">**.NET Core platformlar arası geliştirme** iş yükünün yüklü olduğu [Visual Studio 2019 sürüm 16,4 veya sonraki bir sürüm](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) .</span><span class="sxs-lookup"><span data-stu-id="47e25-109">[Visual Studio 2019 version 16.4 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="47e25-110">.NET Core 3,1 SDK, bu iş yükünü seçtiğinizde otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="47e25-110">.NET Core 3.1 SDK is automatically installed when you select this workload.</span></span>

<span data-ttu-id="47e25-111">Daha fazla bilgi için, [.NET Core SDK](../install/sdk.md?pivots=os-windows) makalesine [Visual Studio ile install](../install/sdk.md?pivots=os-windows#install-with-visual-studio) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="47e25-111">For more information, see the [Install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) section on the [Install the .NET Core SDK](../install/sdk.md?pivots=os-windows) article.</span></span>

## <a name="create-the-app"></a><span data-ttu-id="47e25-112">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="47e25-112">Create the app</span></span>

<span data-ttu-id="47e25-113">Aşağıdaki yönergeler basit bir Merhaba Dünya konsol uygulaması oluşturur:</span><span class="sxs-lookup"><span data-stu-id="47e25-113">The following instructions create a simple Hello World console application:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[<span data-ttu-id="47e25-114">C#</span><span class="sxs-lookup"><span data-stu-id="47e25-114">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="47e25-115">Visual Studio 2019 ' i açın.</span><span class="sxs-lookup"><span data-stu-id="47e25-115">Open Visual Studio 2019.</span></span>

1. <span data-ttu-id="47e25-116">"HelloWorld" adlı yeni bir C# .NET Core konsol uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="47e25-116">Create a new C# .NET Core console app project named "HelloWorld".</span></span>

   1. <span data-ttu-id="47e25-117">Başlangıç penceresinde **Yeni proje oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="47e25-117">On the start window, choose **Create a new project**.</span></span>

      ![Visual Studio başlangıç penceresinde yeni bir proje oluştur düğmesi seçili](./media/with-visual-studio/start-window.png)

   1. <span data-ttu-id="47e25-119">**Yeni proje oluştur** sayfasında, arama kutusuna **konsol** girin.</span><span class="sxs-lookup"><span data-stu-id="47e25-119">On the **Create a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="47e25-120">Ardından, dil listesinden **C#** öğesini seçin ve ardından platform listesinden **tüm platformlar** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="47e25-120">Next, choose **C#** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="47e25-121">**Konsol uygulaması (.NET Core)** şablonunu seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="47e25-121">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

      ![Filtreler seçiliyken yeni bir proje penceresi oluştur](./media/with-visual-studio/create-new-project.png)

      > [!TIP]
      > <span data-ttu-id="47e25-123">.NET Core şablonlarını görmüyorsanız, muhtemelen gerekli iş yükünün yüklü olması eksik olabilir.</span><span class="sxs-lookup"><span data-stu-id="47e25-123">If you don't see the .NET Core templates, you're probably missing the required workload installed.</span></span> <span data-ttu-id="47e25-124">**Aradığınızı bulmuyor musunuz?** iletisi altında, **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="47e25-124">Under the **Not finding what you're looking for?** message, choose the **Install more tools and features** link.</span></span> <span data-ttu-id="47e25-125">Visual Studio Yükleyicisi açılır.</span><span class="sxs-lookup"><span data-stu-id="47e25-125">The Visual Studio Installer opens.</span></span> <span data-ttu-id="47e25-126">**.NET Core platformlar arası geliştirme** iş yükünün yüklü olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="47e25-126">Make sure you have the **.NET Core cross-platform development** workload installed.</span></span>

   1. <span data-ttu-id="47e25-127">**Yeni projenizi yapılandırın** sayfasında, **Proje adı** kutusuna **HelloWorld** girin.</span><span class="sxs-lookup"><span data-stu-id="47e25-127">On the **Configure your new project** page,  enter **HelloWorld** in the **Project name** box.</span></span> <span data-ttu-id="47e25-128">Ardından **Oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="47e25-128">Then, choose **Create**.</span></span>

      ![Yeni proje pencerenizi proje adı, konum ve çözüm adı alanlarıyla yapılandırın](./media/with-visual-studio/configure-new-project.png)

   <span data-ttu-id="47e25-130">.NET Core için C# konsol uygulaması şablonu, `Program` `Main` bağımsız değişken olarak bir dizi alan tek bir yöntemle bir sınıfını otomatik olarak tanımlar <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="47e25-130">The C# Console Application template for .NET Core automatically defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="47e25-131">`Main`uygulama giriş noktası, uygulamayı başlattığında çalışma zamanı tarafından otomatik olarak çağrılan yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="47e25-131">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="47e25-132">Uygulama başlatıldığında sağlanan herhangi bir komut satırı bağımsız değişkeni, *args* dizisinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="47e25-132">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

   ![Visual Studio ve yeni HelloWorld projesi](./media/with-visual-studio/visual-studio-main-window.png)

# <a name="visual-basic"></a>[<span data-ttu-id="47e25-134">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="47e25-134">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="47e25-135">Visual Studio 2019 ' i açın.</span><span class="sxs-lookup"><span data-stu-id="47e25-135">Open Visual Studio 2019.</span></span>

1. <span data-ttu-id="47e25-136">"HelloWorld" adlı yeni bir Visual Basic .NET Core konsol uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="47e25-136">Create a new Visual Basic .NET Core console app project named "HelloWorld".</span></span>

   1. <span data-ttu-id="47e25-137">Başlangıç penceresinde **Yeni proje oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="47e25-137">On the start window, choose **Create a new project**.</span></span>

      ![Visual Studio başlangıç penceresinde yeni bir proje oluştur düğmesi seçili](./media/with-visual-studio/start-window.png)

   1. <span data-ttu-id="47e25-139">**Yeni proje oluştur** sayfasında, arama kutusuna **konsol** girin.</span><span class="sxs-lookup"><span data-stu-id="47e25-139">On the **Create a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="47e25-140">Ardından, dil listesinden **Visual Basic** ' yi seçin ve ardından platform listesinden **tüm platformlar** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="47e25-140">Next, choose **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="47e25-141">**Konsol uygulaması (.NET Core)** şablonunu seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="47e25-141">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

      ![Konsol uygulaması için Visual Basic şablonu seçin (.NET Framework)](./media/with-visual-studio/vb/create-new-project.png)

      > [!TIP]
      > <span data-ttu-id="47e25-143">.NET Core şablonlarını görmüyorsanız, muhtemelen gerekli iş yükünün yüklü olması eksik olabilir.</span><span class="sxs-lookup"><span data-stu-id="47e25-143">If you don't see the .NET Core templates, you're probably missing the required workload installed.</span></span> <span data-ttu-id="47e25-144">**Aradığınızı bulmuyor musunuz?** iletisi altında, **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="47e25-144">Under the **Not finding what you're looking for?** message, choose the **Install more tools and features** link.</span></span> <span data-ttu-id="47e25-145">Visual Studio Yükleyicisi açılır.</span><span class="sxs-lookup"><span data-stu-id="47e25-145">The Visual Studio Installer opens.</span></span> <span data-ttu-id="47e25-146">**.NET Core platformlar arası geliştirme** iş yükünün yüklü olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="47e25-146">Make sure you have the **.NET Core cross-platform development** workload installed.</span></span>

   1. <span data-ttu-id="47e25-147">**Yeni projenizi yapılandırın** sayfasında, **Proje adı** kutusuna **HelloWorld** girin.</span><span class="sxs-lookup"><span data-stu-id="47e25-147">On the **Configure your new project** page,  enter **HelloWorld** in the **Project name** box.</span></span> <span data-ttu-id="47e25-148">Ardından **Oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="47e25-148">Then, choose **Create**.</span></span>

   <span data-ttu-id="47e25-149">.NET Core konsol uygulaması şablonu, `Program` `Main` bağımsız değişken olarak bir dizi alan tek bir yöntemle bir sınıfını otomatik olarak tanımlar <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="47e25-149">The console app template for .NET Core automatically defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="47e25-150">`Main`uygulama giriş noktası, uygulamayı başlattığında çalışma zamanı tarafından otomatik olarak çağrılan yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="47e25-150">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="47e25-151">Uygulama başlatıldığında sağlanan herhangi bir komut satırı bağımsız değişkeni `args` parametresinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="47e25-151">Any command-line arguments supplied when the application is launched are available in the `args` parameter.</span></span>

   ![Visual Studio ve yeni HelloWorld projesi](./media/with-visual-studio/vb/visual-studio-main-window.png)

---

   <span data-ttu-id="47e25-153">Şablon basit bir "Merhaba Dünya" uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="47e25-153">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="47e25-154"><xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType>"Merhaba Dünya!" değişmez dizesini göstermek için yöntemini çağırır</span><span class="sxs-lookup"><span data-stu-id="47e25-154">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display the literal string "Hello World!"</span></span> <span data-ttu-id="47e25-155">Konsol penceresinde.</span><span class="sxs-lookup"><span data-stu-id="47e25-155">in the console window.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="47e25-156">Uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="47e25-156">Run the app</span></span>

1. <span data-ttu-id="47e25-157">Programı çalıştırmak için araç çubuğunda **HelloWorld** ' ı seçin veya **F5**tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="47e25-157">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

   ![HelloWorld Run düğmesinin seçili olduğu Visual Studio araç çubuğu](./media/with-visual-studio/run-program.png)

   <span data-ttu-id="47e25-159">Bir konsol penceresi "Merhaba Dünya!" metniyle açılıyor</span><span class="sxs-lookup"><span data-stu-id="47e25-159">A console window opens with the text "Hello World!"</span></span> <span data-ttu-id="47e25-160">ekranda ve bazı Visual Studio hata ayıklama bilgilerinde yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="47e25-160">printed on the screen and some Visual Studio debug information.</span></span>

   ![Merhaba Dünya devam etmek için herhangi bir tuşa basarak konsol penceresi](./media/with-visual-studio/hello-world-console.png)

1. <span data-ttu-id="47e25-162">Konsol penceresini kapatmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="47e25-162">Press any key to close the console window.</span></span>

## <a name="enhance-the-app"></a><span data-ttu-id="47e25-163">Uygulamayı geliştirin</span><span class="sxs-lookup"><span data-stu-id="47e25-163">Enhance the app</span></span>

<span data-ttu-id="47e25-164">Uygulamanızı, adını ve Tarih ve saat ile birlikte göstermek için kullanıcıyı geliştirin.</span><span class="sxs-lookup"><span data-stu-id="47e25-164">Enhance your application to prompt the user for their name and display it along with the date and time.</span></span> <span data-ttu-id="47e25-165">Aşağıdaki yönergeler uygulamayı yeniden değiştirip çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="47e25-165">The following instructions modify and run the app again:</span></span>

# <a name="c"></a>[<span data-ttu-id="47e25-166">C#</span><span class="sxs-lookup"><span data-stu-id="47e25-166">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="47e25-167">`Main`Aşağıdaki kod ile Şu anda yalnızca çağıran satırı olan yönteminin içeriğini değiştirin `Console.WriteLine` :</span><span class="sxs-lookup"><span data-stu-id="47e25-167">Replace the contents of the `Main` method, which is currently just the line that calls `Console.WriteLine`, with the following code:</span></span>

   [!code-csharp[GettingStarted#1](~/samples/snippets/csharp/getting_started/with_visual_studio/HelloWorld.cs#1)]

   <span data-ttu-id="47e25-168">Bu kod "adınız nedir?" görüntüler</span><span class="sxs-lookup"><span data-stu-id="47e25-168">This code displays "What is your name?"</span></span> <span data-ttu-id="47e25-169">Konsol penceresinde ve ardından ENTER tuşuna basarak Kullanıcı bir dize girene kadar bekler.</span><span class="sxs-lookup"><span data-stu-id="47e25-169">in the console window and waits until the user enters a string followed by the Enter key.</span></span> <span data-ttu-id="47e25-170">Bu dizeyi adlı bir değişkende depolar `name` .</span><span class="sxs-lookup"><span data-stu-id="47e25-170">It stores this string into a variable named `name`.</span></span> <span data-ttu-id="47e25-171">Ayrıca <xref:System.DateTime.Now?displayProperty=nameWithType> , geçerli yerel saati içeren özelliğinin değerini alır ve bunu adlı bir değişkene atar `date` .</span><span class="sxs-lookup"><span data-stu-id="47e25-171">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="47e25-172">Son olarak, bu değerleri konsol penceresinde göstermek için bir [enterpolasyonlu dize](../../csharp/language-reference/tokens/interpolated.md) kullanır.</span><span class="sxs-lookup"><span data-stu-id="47e25-172">Finally, it uses an [interpolated string](../../csharp/language-reference/tokens/interpolated.md) to display these values in the console window.</span></span>

1. <span data-ttu-id="47e25-173">**Build**  >  **Build Solution**öğesini seçerek programı derleyin.</span><span class="sxs-lookup"><span data-stu-id="47e25-173">Compile the program by choosing **Build** > **Build Solution**.</span></span>

1. <span data-ttu-id="47e25-174">Programı çalıştırmak için araç çubuğunda **HelloWorld** ' ı seçin veya **F5**tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="47e25-174">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

1. <span data-ttu-id="47e25-175">Bir ad girip **ENTER** tuşuna basarak istemi yanıtlayın.</span><span class="sxs-lookup"><span data-stu-id="47e25-175">Respond to the prompt by entering a name and pressing the **Enter** key.</span></span>

   ![Değiştirilen program çıkışıyla konsol penceresi](./media/with-visual-studio/hello-world-update.png)

1. <span data-ttu-id="47e25-177">Konsol penceresini kapatmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="47e25-177">Press any key to close the console window.</span></span>

# <a name="visual-basic"></a>[<span data-ttu-id="47e25-178">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="47e25-178">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="47e25-179">`Main`Aşağıdaki kod ile Şu anda yalnızca çağıran satırı olan yönteminin içeriğini değiştirin `Console.WriteLine` :</span><span class="sxs-lookup"><span data-stu-id="47e25-179">Replace the contents of the `Main` method, which is currently just the line that calls `Console.WriteLine`, with the following code:</span></span>

   [!code-vb[GettingStarted#1](~/samples/snippets/core/tutorials/vb-with-visual-studio/Program.vb#1)]

   <span data-ttu-id="47e25-180">Bu kod "adınız nedir?" görüntüler</span><span class="sxs-lookup"><span data-stu-id="47e25-180">This code displays "What is your name?"</span></span> <span data-ttu-id="47e25-181">Konsol penceresinde ve ardından ENTER tuşuna basarak Kullanıcı bir dize girene kadar bekler.</span><span class="sxs-lookup"><span data-stu-id="47e25-181">in the console window and waits until the user enters a string followed by the Enter key.</span></span> <span data-ttu-id="47e25-182">Bu dizeyi adlı bir değişkende depolar `name` .</span><span class="sxs-lookup"><span data-stu-id="47e25-182">It stores this string into a variable named `name`.</span></span> <span data-ttu-id="47e25-183">Ayrıca <xref:System.DateTime.Now?displayProperty=nameWithType> , geçerli yerel saati içeren özelliğinin değerini alır ve bunu adlı bir değişkene atar `date` .</span><span class="sxs-lookup"><span data-stu-id="47e25-183">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="47e25-184">Son olarak, bu değerleri konsol penceresinde göstermek için bir [enterpolasyonlu dize](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) kullanır.</span><span class="sxs-lookup"><span data-stu-id="47e25-184">Finally, it uses an [interpolated string](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) to display these values in the console window.</span></span>

1. <span data-ttu-id="47e25-185">**Build**  >  **Build Solution**öğesini seçerek programı derleyin.</span><span class="sxs-lookup"><span data-stu-id="47e25-185">Compile the program by choosing **Build** > **Build Solution**.</span></span>

1. <span data-ttu-id="47e25-186">Programı çalıştırmak için araç çubuğunda **HelloWorld** ' ı seçin veya **F5**tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="47e25-186">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

1. <span data-ttu-id="47e25-187">Bir ad girip **ENTER** tuşuna basarak istemi yanıtlayın.</span><span class="sxs-lookup"><span data-stu-id="47e25-187">Respond to the prompt by entering a name and pressing the **Enter** key.</span></span>

   ![Değiştirilen program çıkışıyla konsol penceresi](./media/with-visual-studio/hello-world-update.png)

1. <span data-ttu-id="47e25-189">Konsol penceresini kapatmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="47e25-189">Press any key to close the console window.</span></span>

---

## <a name="next-steps"></a><span data-ttu-id="47e25-190">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="47e25-190">Next steps</span></span>

<span data-ttu-id="47e25-191">Bu makalede ilk .NET Core uygulamanızı oluşturdunuz ve çalıştırdık.</span><span class="sxs-lookup"><span data-stu-id="47e25-191">In this article, you've created and run your first .NET Core application.</span></span> <span data-ttu-id="47e25-192">Sonraki adımda, uygulamanızda hata ayıklaması yapın.</span><span class="sxs-lookup"><span data-stu-id="47e25-192">In the next step, you debug your app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="47e25-193">Visual Studio 'da bir .NET Core Merhaba Dünya uygulamasında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="47e25-193">Debug a .NET Core Hello World application in Visual Studio</span></span>](debugging-with-visual-studio.md)
