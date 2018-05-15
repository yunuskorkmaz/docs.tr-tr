---
title: Visual Studio'da WPF uygulaması oluşturma
ms.date: 04/12/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7ceb4d79bb88e41e62f3ee136b6beb3324b3dbd7
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a><span data-ttu-id="7e137-102">İzlenecek yol: İlk WPF Masaüstü Uygulamam</span><span class="sxs-lookup"><span data-stu-id="7e137-102">Walkthrough: My first WPF desktop application</span></span>

<span data-ttu-id="7e137-103">Bu makalede, çoğu WPF uygulamaları için ortak olan öğeleri içeren basit bir Windows Presentation Foundation (WPF) uygulama geliştirmek gösterilmiştir: Genişletilebilir uygulama biçimlendirme dili (XAML) işaretleme, arka plan kodu, uygulama tanımları denetimleri, düzeni, veri bağlama ve stiller.</span><span class="sxs-lookup"><span data-stu-id="7e137-103">This article shows you how to develop a simple Windows Presentation Foundation (WPF) application that includes the elements that are common to most WPF applications: Extensible Application Markup Language (XAML) markup, code-behind, application definitions, controls, layout, data binding, and styles.</span></span>

<span data-ttu-id="7e137-104">Bu izlenecek yol aşağıdaki adımları içerir:</span><span class="sxs-lookup"><span data-stu-id="7e137-104">This walkthrough includes the following steps:</span></span>

- <span data-ttu-id="7e137-105">Uygulamanın kullanıcı arabirimini (UI) görünümünü tasarlamak için XAML kullanın.</span><span class="sxs-lookup"><span data-stu-id="7e137-105">Use XAML to design the appearance of the application's user interface (UI).</span></span>

- <span data-ttu-id="7e137-106">Uygulamanın davranışını oluşturmak için kod yazma.</span><span class="sxs-lookup"><span data-stu-id="7e137-106">Write code to build the application's behavior.</span></span>

- <span data-ttu-id="7e137-107">Uygulamasını yönetmek için uygulama tanımı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7e137-107">Create an application definition to manage the application.</span></span>

- <span data-ttu-id="7e137-108">Denetimler ekleme ve uygulama kullanıcı Arabirimi oluşturmak için bir düzen oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7e137-108">Add controls and create the layout to compose the application UI.</span></span>

- <span data-ttu-id="7e137-109">Bir uygulamanın UI genelinde tutarlı bir görünüm için stiller oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7e137-109">Create styles for a consistent appearance throughout an application's UI.</span></span>

- <span data-ttu-id="7e137-110">Kullanıcı arabirimini verilerden UI doldurmak hem UI eşitlenmiş ve verileri korumak için verilere bağlayın.</span><span class="sxs-lookup"><span data-stu-id="7e137-110">Bind the UI to data to both populate the UI from data and keep the data and UI synchronized.</span></span>

<span data-ttu-id="7e137-111">İzlenecek yol ucu tarafından tek başına kullanıcıların seçilen kişiler için harcama raporlarını görüntülemesine olanak sağlayan Windows uygulaması hazırladığınız.</span><span class="sxs-lookup"><span data-stu-id="7e137-111">By the end of the walkthrough, you'll have built a standalone Windows application that allows users to view expense reports for selected people.</span></span> <span data-ttu-id="7e137-112">Uygulaması bir tarayıcı stili pencerede barındırılan birkaç WPF sayfaların oluşur.</span><span class="sxs-lookup"><span data-stu-id="7e137-112">The application is composed of several WPF pages that are hosted in a browser-style window.</span></span>

> [!TIP]
> <span data-ttu-id="7e137-113">Bu izlenecek yolu oluşturmak için kullanılan örnek kod hem Visual Basic ve C# için kullanılabilir [WPF uygulamalarını giriş](http://go.microsoft.com/fwlink/?LinkID=160008).</span><span class="sxs-lookup"><span data-stu-id="7e137-113">The sample code that is used to build this walkthrough is available for both Visual Basic and C# at [Introduction to Building WPF Applications](http://go.microsoft.com/fwlink/?LinkID=160008).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7e137-114">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="7e137-114">Prerequisites</span></span>

- <span data-ttu-id="7e137-115">Visual Studio 2012 veya üzeri</span><span class="sxs-lookup"><span data-stu-id="7e137-115">Visual Studio 2012 or later</span></span>

<span data-ttu-id="7e137-116">Visual Studio en son sürümünü yükleme hakkında daha fazla bilgi için bkz: [Visual Studio yükleme](/visualstudio/install/install-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="7e137-116">For more information about installing the latest version of Visual Studio, see [Install Visual Studio](/visualstudio/install/install-visual-studio).</span></span>

## <a name="create-the-application-project"></a><span data-ttu-id="7e137-117">Uygulama projesi oluşturun</span><span class="sxs-lookup"><span data-stu-id="7e137-117">Create the application project</span></span>

<span data-ttu-id="7e137-118">İlk adım, uygulama tanımı, iki sayfaları ve görüntü içeren uygulama altyapısı oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="7e137-118">The first step is to create the application infrastructure, which includes an application definition, two pages, and an image.</span></span>

1. <span data-ttu-id="7e137-119">Visual Basic veya Visual C# adlı yeni bir WPF uygulaması projesi oluşturduğunuzda **ExpenseIt**:</span><span class="sxs-lookup"><span data-stu-id="7e137-119">Create a new WPF Application project in Visual Basic or Visual C# named **ExpenseIt**:</span></span>

   1. <span data-ttu-id="7e137-120">Visual Studio'yu açın ve seçin **dosya** > **yeni** > **proje**.</span><span class="sxs-lookup"><span data-stu-id="7e137-120">Open Visual Studio and select **File** > **New** > **Project**.</span></span>

      <span data-ttu-id="7e137-121">**Yeni proje** iletişim kutusunu açar.</span><span class="sxs-lookup"><span data-stu-id="7e137-121">The **New Project** dialog opens.</span></span>

   2. <span data-ttu-id="7e137-122">Altında **yüklü** kategorisini genişletin **Visual C#** veya **Visual Basic** düğümünü ve ardından **Windows Klasik Masaüstü**.</span><span class="sxs-lookup"><span data-stu-id="7e137-122">Under the **Installed** category, expand either the **Visual C#** or **Visual Basic** node, and then select **Windows Classic Desktop**.</span></span>

   3. <span data-ttu-id="7e137-123">Seçin **WPF uygulaması (.NET Framework)** şablonu.</span><span class="sxs-lookup"><span data-stu-id="7e137-123">Select the **WPF App (.NET Framework)** template.</span></span> <span data-ttu-id="7e137-124">Bir ad girin **ExpenseIt** ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="7e137-124">Enter the name **ExpenseIt** and then select **OK**.</span></span>

      ![Seçili WPF uygulaması ile yeni proje iletişim kutusu](media/new-project-dialog.png)

      <span data-ttu-id="7e137-126">Visual Studio projesi oluşturur ve tasarımcı adlı varsayılan uygulama penceresi açar **MainWindow.xaml**.</span><span class="sxs-lookup"><span data-stu-id="7e137-126">Visual Studio creates the project and opens the designer for the default application window named **MainWindow.xaml**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="7e137-127">Bu kılavuzda kullanılır <xref:System.Windows.Controls.DataGrid> kullanılabilir .NET Framework 4 ve üzeri denetim.</span><span class="sxs-lookup"><span data-stu-id="7e137-127">This walkthrough uses the <xref:System.Windows.Controls.DataGrid> control that is available in the .NET Framework 4 and later.</span></span> <span data-ttu-id="7e137-128">Sonraki veya projeniz .NET Framework 4 hedefleyen emin olun.</span><span class="sxs-lookup"><span data-stu-id="7e137-128">Be sure that your project targets the .NET Framework 4 or later.</span></span> <span data-ttu-id="7e137-129">Daha fazla bilgi için bkz: [nasıl yapılır: .NET Framework sürümü hedef](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span><span class="sxs-lookup"><span data-stu-id="7e137-129">For more information, see [How to: Target a Version of the .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span></span>

2. <span data-ttu-id="7e137-130">Açık *Application.xaml* (Visual Basic) veya *App.xaml* (C#).</span><span class="sxs-lookup"><span data-stu-id="7e137-130">Open *Application.xaml* (Visual Basic) or *App.xaml* (C#).</span></span>

    <span data-ttu-id="7e137-131">Bu XAML dosyası WPF uygulaması ve uygulama kaynaklarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7e137-131">This XAML file defines a WPF application and any application resources.</span></span> <span data-ttu-id="7e137-132">Bu dosyayı otomatik olarak ne zaman gösterir UI belirtmek için de uygulamayı başlatır; Bu durumda, *MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="7e137-132">You also use this file to specify the UI that automatically shows when the application starts; in this case, *MainWindow.xaml*.</span></span>

    <span data-ttu-id="7e137-133">Visual Basic'te XAML aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="7e137-133">Your XAML should look like this in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#1_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    <span data-ttu-id="7e137-134">Ya da böyle C#:</span><span class="sxs-lookup"><span data-stu-id="7e137-134">Or like this in C#:</span></span>

    [!code-xaml[ExpenseIt#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. <span data-ttu-id="7e137-135">Açık *MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="7e137-135">Open *MainWindow.xaml*.</span></span>

    <span data-ttu-id="7e137-136">Bu XAML dosyası, uygulamanızın ana penceresidir ve sayfalarda oluşturulan içeriği görüntüler.</span><span class="sxs-lookup"><span data-stu-id="7e137-136">This XAML file is the main window of your application and displays content created in pages.</span></span> <span data-ttu-id="7e137-137"><xref:System.Windows.Window> Sınıfı başlık, boyut veya simge, gibi bir pencere özelliklerini tanımlar ve kapatma veya gizleme gibi olayları işler.</span><span class="sxs-lookup"><span data-stu-id="7e137-137">The <xref:System.Windows.Window> class defines the properties of a window, such as its title, size, or icon, and handles events, such as closing or hiding.</span></span>

4. <span data-ttu-id="7e137-138">Değişiklik <xref:System.Windows.Window> öğesine bir <xref:System.Windows.Navigation.NavigationWindow>aşağıdaki XAML'de gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="7e137-138">Change the <xref:System.Windows.Window> element to a <xref:System.Windows.Navigation.NavigationWindow>, as shown in the following XAML:</span></span>

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   <span data-ttu-id="7e137-139">Bu uygulama için kullanıcı girişi bağlı olarak farklı içeriğe götürür.</span><span class="sxs-lookup"><span data-stu-id="7e137-139">This app navigates to different content depending on the user input.</span></span> <span data-ttu-id="7e137-140">Nedeni budur ana <xref:System.Windows.Window> için değiştirilmesi gereken bir <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="7e137-140">This is why the main <xref:System.Windows.Window> needs to be changed to a <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="7e137-141"><xref:System.Windows.Navigation.NavigationWindow> tüm özelliklerini devralır <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="7e137-141"><xref:System.Windows.Navigation.NavigationWindow> inherits all the properties of <xref:System.Windows.Window>.</span></span> <span data-ttu-id="7e137-142"><xref:System.Windows.Navigation.NavigationWindow> XAML dosyası öğesinde bir örneğini oluşturur <xref:System.Windows.Navigation.NavigationWindow> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7e137-142">The <xref:System.Windows.Navigation.NavigationWindow> element in the XAML file creates an instance of the <xref:System.Windows.Navigation.NavigationWindow> class.</span></span> <span data-ttu-id="7e137-143">Daha fazla bilgi için bkz: [Gezinti genel bakış](../../../../docs/framework/wpf/app-development/navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="7e137-143">For more information, see [Navigation overview](../../../../docs/framework/wpf/app-development/navigation-overview.md).</span></span>

5. <span data-ttu-id="7e137-144">Aşağıdaki özellikleri değiştirin <xref:System.Windows.Navigation.NavigationWindow> öğe:</span><span class="sxs-lookup"><span data-stu-id="7e137-144">Change the following properties on the <xref:System.Windows.Navigation.NavigationWindow> element:</span></span>

    - <span data-ttu-id="7e137-145">Ayarlama <xref:System.Windows.Window.Title%2A> özelliğini "ExpenseIt".</span><span class="sxs-lookup"><span data-stu-id="7e137-145">Set the <xref:System.Windows.Window.Title%2A> property to "ExpenseIt".</span></span>

    - <span data-ttu-id="7e137-146">Ayarlama <xref:System.Windows.FrameworkElement.Width%2A> özelliğini 500 piksel.</span><span class="sxs-lookup"><span data-stu-id="7e137-146">Set the <xref:System.Windows.FrameworkElement.Width%2A> property to 500 pixels.</span></span>

    - <span data-ttu-id="7e137-147">Ayarlama <xref:System.Windows.FrameworkElement.Height%2A> özelliğini 350 piksel.</span><span class="sxs-lookup"><span data-stu-id="7e137-147">Set the <xref:System.Windows.FrameworkElement.Height%2A> property to 350 pixels.</span></span>

    - <span data-ttu-id="7e137-148">Kaldırma <xref:System.Windows.Controls.Grid> öğeleri arasında <xref:System.Windows.Navigation.NavigationWindow> etiketler.</span><span class="sxs-lookup"><span data-stu-id="7e137-148">Remove the <xref:System.Windows.Controls.Grid> elements between the <xref:System.Windows.Navigation.NavigationWindow> tags.</span></span>

    <span data-ttu-id="7e137-149">Visual Basic'te XAML aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="7e137-149">Your XAML should look like this in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#2_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    <span data-ttu-id="7e137-150">Ya da böyle C#:</span><span class="sxs-lookup"><span data-stu-id="7e137-150">Or like this in C#:</span></span>

    [!code-xaml[ExpenseIt#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

6. <span data-ttu-id="7e137-151">Açık *MainWindow.xaml.vb* veya *MainWindow.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="7e137-151">Open *MainWindow.xaml.vb* or *MainWindow.xaml.cs*.</span></span>

    <span data-ttu-id="7e137-152">Bu dosya bildirilen olayları işlemek için kod içeren bir arka plan kodu dosyasıdır *MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="7e137-152">This file is a code-behind file that contains code to handle the events declared in *MainWindow.xaml*.</span></span> <span data-ttu-id="7e137-153">Bu dosya XAML içinde tanımlanan penceresi için bir parçalı sınıf içerir.</span><span class="sxs-lookup"><span data-stu-id="7e137-153">This file contains a partial class for the window defined in XAML.</span></span>

7. <span data-ttu-id="7e137-154">C# kullanıyorsanız değiştirme `MainWindow` öğesinden türetilen sınıf <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="7e137-154">If you are using C#, change the `MainWindow` class to derive from <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="7e137-155">(XAML penceresinde değiştirdiğinizde, Visual Basic'te, bu otomatik olarak gerçekleşir.)</span><span class="sxs-lookup"><span data-stu-id="7e137-155">(In Visual Basic, this happens automatically when you change the window in XAML.)</span></span>

   <span data-ttu-id="7e137-156">Kodunuzu aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="7e137-156">Your code should look like this:</span></span>

   [!code-csharp[ExpenseIt#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml.cs#3)]
   [!code-vb[ExpenseIt#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml.vb#3)]

   > [!TIP]
   > <span data-ttu-id="7e137-157">C# ve Visual Basic'te arasında yer alan örnek kodunu kod dili Değiştir **dil** bu makalenin üst sağ taraftaki açılır.</span><span class="sxs-lookup"><span data-stu-id="7e137-157">You can toggle the code language of the sample code between C# and Visual Basic in the **Language** drop-down on the upper right side of this article.</span></span>

## <a name="add-files-to-the-application"></a><span data-ttu-id="7e137-158">Uygulama dosyaları ekleme</span><span class="sxs-lookup"><span data-stu-id="7e137-158">Add files to the application</span></span>

<span data-ttu-id="7e137-159">Bu bölümde, uygulama için iki sayfaları ve görüntü ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="7e137-159">In this section, you'll add two pages and an image to the application.</span></span>

1. <span data-ttu-id="7e137-160">Yeni bir WPF sayfası projeye ekleyin ve adını *ExpenseItHome.XAML*:</span><span class="sxs-lookup"><span data-stu-id="7e137-160">Add a new WPF page to the project, and name it *ExpenseItHome.xaml*:</span></span>

   1. <span data-ttu-id="7e137-161">İçinde **Çözüm Gezgini**, sağ tıklayın **ExpenseIt** proje düğümünü ve seçin **Ekle** > **sayfa**.</span><span class="sxs-lookup"><span data-stu-id="7e137-161">In **Solution Explorer**, right-click on the **ExpenseIt** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="7e137-162">İçinde **Yeni Öğe Ekle** iletişim kutusunda, **sayfa (WPF)** şablon zaten seçilmiş.</span><span class="sxs-lookup"><span data-stu-id="7e137-162">In the **Add New Item** dialog, the **Page (WPF)** template is already selected.</span></span> <span data-ttu-id="7e137-163">Bir ad girin **ExpenseItHome**ve ardından **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="7e137-163">Enter the name **ExpenseItHome**, and then select **Add**.</span></span>

    <span data-ttu-id="7e137-164">Uygulama başlatıldığında görüntülenen ilk sayfa sayfasıdır.</span><span class="sxs-lookup"><span data-stu-id="7e137-164">This page is the first page that's displayed when the application is launched.</span></span> <span data-ttu-id="7e137-165">Kişiler için harcama raporunu göstermek için arasından seçim listesi gösterilir.</span><span class="sxs-lookup"><span data-stu-id="7e137-165">It will show a list of people to select from, to show an expense report for.</span></span>

2. <span data-ttu-id="7e137-166">Açık *ExpenseItHome.XAML*.</span><span class="sxs-lookup"><span data-stu-id="7e137-166">Open *ExpenseItHome.xaml*.</span></span>

3. <span data-ttu-id="7e137-167">Ayarlama <xref:System.Windows.Controls.Page.Title%2A> "ExpenseIt - Giriş".</span><span class="sxs-lookup"><span data-stu-id="7e137-167">Set the <xref:System.Windows.Controls.Page.Title%2A> to "ExpenseIt - Home".</span></span>

    <span data-ttu-id="7e137-168">Visual Basic'te XAML aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="7e137-168">Your XAML should look like this in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#6_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    <span data-ttu-id="7e137-169">Veya bu C#:</span><span class="sxs-lookup"><span data-stu-id="7e137-169">Or this in C#:</span></span>

    [!code-xaml[ExpenseIt#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

4. <span data-ttu-id="7e137-170">Açık *MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="7e137-170">Open *MainWindow.xaml*.</span></span>

5. <span data-ttu-id="7e137-171">Ayarlama <xref:System.Windows.Navigation.NavigationWindow.Source%2A> özellikte <xref:System.Windows.Navigation.NavigationWindow> "ExpenseItHome.xaml" için.</span><span class="sxs-lookup"><span data-stu-id="7e137-171">Set the <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property on the <xref:System.Windows.Navigation.NavigationWindow> to "ExpenseItHome.xaml".</span></span>

    <span data-ttu-id="7e137-172">Bu ayarlar *ExpenseItHome.XAML* ilk sayfa olarak uygulama başladığında açılır.</span><span class="sxs-lookup"><span data-stu-id="7e137-172">This sets *ExpenseItHome.xaml* to be the first page opened when the application starts.</span></span> <span data-ttu-id="7e137-173">Visual Basic'te XAML aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="7e137-173">Your XAML should look like this in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#7_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    <span data-ttu-id="7e137-174">Veya bu C#:</span><span class="sxs-lookup"><span data-stu-id="7e137-174">Or this in C#:</span></span>

    [!code-xaml[ExpenseIt#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > <span data-ttu-id="7e137-175">Ayrıca ayarlayabilirsiniz **kaynak** özelliğinde **çeşitli** kategorisini **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="7e137-175">You can also set the **Source** property in the **Miscellaneous** category of the **Properties** window.</span></span>
   >
   > ![Özellikleri penceresinde kaynak özelliği](media/properties-source.png)

6. <span data-ttu-id="7e137-177">Başka bir yeni WPF sayfası projeye ekleyin ve adını *ExpenseReportPage.xaml*::</span><span class="sxs-lookup"><span data-stu-id="7e137-177">Add another new WPF page to the project, and name it *ExpenseReportPage.xaml*::</span></span>

   1. <span data-ttu-id="7e137-178">İçinde **Çözüm Gezgini**, sağ tıklayın **ExpenseIt** proje düğümünü ve seçin **Ekle** > **sayfa**.</span><span class="sxs-lookup"><span data-stu-id="7e137-178">In **Solution Explorer**, right-click on the **ExpenseIt** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="7e137-179">İçinde **Yeni Öğe Ekle** iletişim kutusunda, **sayfa (WPF)** şablon zaten seçilmiş.</span><span class="sxs-lookup"><span data-stu-id="7e137-179">In the **Add New Item** dialog, the **Page (WPF)** template is already selected.</span></span> <span data-ttu-id="7e137-180">Bir ad girin **ExpenseReportPage**ve ardından **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="7e137-180">Enter the name **ExpenseReportPage**, and then select **Add**.</span></span>

    <span data-ttu-id="7e137-181">Bu sayfada seçili kişi için harcama raporunu gösterilir **ExpenseItHome** sayfası.</span><span class="sxs-lookup"><span data-stu-id="7e137-181">This page will show the expense report for the person that is selected on the **ExpenseItHome** page.</span></span>

7. <span data-ttu-id="7e137-182">Açık *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="7e137-182">Open *ExpenseReportPage.xaml*.</span></span>

8. <span data-ttu-id="7e137-183">Ayarlama <xref:System.Windows.Controls.Page.Title%2A> "ExpenseIt - görünüm gider".</span><span class="sxs-lookup"><span data-stu-id="7e137-183">Set the <xref:System.Windows.Controls.Page.Title%2A> to "ExpenseIt - View Expense".</span></span>

    <span data-ttu-id="7e137-184">Visual Basic'te XAML aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="7e137-184">Your XAML should look like this in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#4_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    <span data-ttu-id="7e137-185">Veya bu C#:</span><span class="sxs-lookup"><span data-stu-id="7e137-185">Or this in C#:</span></span>

    [!code-xaml[ExpenseIt#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

9. <span data-ttu-id="7e137-186">Açık *ExpenseItHome.xaml.vb* ve *ExpenseReportPage.xaml.vb*, veya *ExpenseItHome.xaml.cs* ve *ExpenseReportPage.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="7e137-186">Open *ExpenseItHome.xaml.vb* and *ExpenseReportPage.xaml.vb*, or *ExpenseItHome.xaml.cs* and *ExpenseReportPage.xaml.cs*.</span></span>

    <span data-ttu-id="7e137-187">Yeni bir sayfa dosyası oluşturduğunuzda, Visual Studio otomatik olarak oluşturur bir *arka plan kodu* dosya.</span><span class="sxs-lookup"><span data-stu-id="7e137-187">When you create a new Page file, Visual Studio automatically creates a *code-behind* file.</span></span> <span data-ttu-id="7e137-188">Bu arka plan kodu dosyaları için kullanıcı girişine yanıt mantığını işler.</span><span class="sxs-lookup"><span data-stu-id="7e137-188">These code-behind files handle the logic for responding to user input.</span></span>

    <span data-ttu-id="7e137-189">Kodunuz için şuna benzer görünmelidir **ExpenseItHome**:</span><span class="sxs-lookup"><span data-stu-id="7e137-189">Your code should look like this for **ExpenseItHome**:</span></span>

    [!code-csharp[ExpenseIt#2_5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]
    [!code-vb[ExpenseIt#2_5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    <span data-ttu-id="7e137-190">Ve bu gibi **ExpenseReportPage**:</span><span class="sxs-lookup"><span data-stu-id="7e137-190">And like this for **ExpenseReportPage**:</span></span>

    [!code-csharp[ExpenseIt#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]
    [!code-vb[ExpenseIt#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

10. <span data-ttu-id="7e137-191">Adlı bir resim ekleyin *watermark.png* projeye.</span><span class="sxs-lookup"><span data-stu-id="7e137-191">Add an image named *watermark.png* to the project.</span></span> <span data-ttu-id="7e137-192">Kendi görüntünüzü oluşturabilir, dosyanın örnek kodu kopyalayabilir veya alın [burada](https://github.com/dotnet/docs/blob/master/docs/framework/wpf/getting-started/media/watermark.png).</span><span class="sxs-lookup"><span data-stu-id="7e137-192">You can create your own image, copy the file from the sample code, or get it [here](https://github.com/dotnet/docs/blob/master/docs/framework/wpf/getting-started/media/watermark.png).</span></span>

   1. <span data-ttu-id="7e137-193">Proje düğümüne sağ tıklatıp **Ekle** > **varolan öğeyi**, veya basın **Shift**+**Alt** + **A**.</span><span class="sxs-lookup"><span data-stu-id="7e137-193">Right-click on the project node and select **Add** > **Existing Item**, or press **Shift**+**Alt**+**A**.</span></span>

   2. <span data-ttu-id="7e137-194">İçinde **varolan öğeyi Ekle** iletişim kutusunda, kullanın ve ardından istediğiniz görüntü dosyasına Gözat **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="7e137-194">In the **Add Existing Item** dialog, browse to the image file you want to use, and then select **Add**.</span></span>

## <a name="build-and-run-the-application"></a><span data-ttu-id="7e137-195">Derleme ve uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="7e137-195">Build and run the application</span></span>

1. <span data-ttu-id="7e137-196">Derleme ve uygulamayı çalıştırmak için basın **F5** veya seçin **hata ayıklamayı Başlat** gelen **hata ayıklama** menüsü.</span><span class="sxs-lookup"><span data-stu-id="7e137-196">To build and run the application, press **F5** or select **Start Debugging** from the **Debug** menu.</span></span>

    <span data-ttu-id="7e137-197">Uygulamayla birlikte aşağıda gösterilmiştir <xref:System.Windows.Navigation.NavigationWindow> düğmeleri:</span><span class="sxs-lookup"><span data-stu-id="7e137-197">The following illustration shows the application with the <xref:System.Windows.Navigation.NavigationWindow> buttons:</span></span>

    ![ExpenseIt örnek ekran görüntüsü](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure1.png)

2. <span data-ttu-id="7e137-199">Visual Studio'ya dönmek için uygulamayı kapatın.</span><span class="sxs-lookup"><span data-stu-id="7e137-199">Close the application to return to Visual Studio.</span></span>

## <a name="create-the-layout"></a><span data-ttu-id="7e137-200">Düzeni oluşturma</span><span class="sxs-lookup"><span data-stu-id="7e137-200">Create the layout</span></span>

<span data-ttu-id="7e137-201">Düzen kullanıcı Arabirimi öğeleri yerleştirmek için sıralı bir yol sağlar ve bir kullanıcı Arabirimi yeniden boyutlandırıldığında boyutunu ve konumunu bu öğelerin da yönetir.</span><span class="sxs-lookup"><span data-stu-id="7e137-201">Layout provides an ordered way to place UI elements, and also manages the size and position of those elements when a UI is resized.</span></span> <span data-ttu-id="7e137-202">Genellikle bir düzen aşağıdaki düzen denetimlerinden biri ile oluşturursunuz:</span><span class="sxs-lookup"><span data-stu-id="7e137-202">You typically create a layout with one of the following layout controls:</span></span>

- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.DockPanel>
- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.VirtualizingStackPanel>
- <xref:System.Windows.Controls.WrapPanel>

<span data-ttu-id="7e137-203">Bu düzen denetimlerinin her biri kendi alt öğeleri için özel türde bir düzen destekler.</span><span class="sxs-lookup"><span data-stu-id="7e137-203">Each of these layout controls supports a special type of layout for its child elements.</span></span> <span data-ttu-id="7e137-204">ExpenseIt sayfaları yeniden boyutlandırılabilir ve her sayfanın diğer öğeleri yatay ve dikey olarak düzenlenmiş öğesine sahip.</span><span class="sxs-lookup"><span data-stu-id="7e137-204">ExpenseIt pages can be resized, and each page has elements that are arranged horizontally and vertically alongside other elements.</span></span> <span data-ttu-id="7e137-205">Sonuç olarak, <xref:System.Windows.Controls.Grid> uygulama için ideal Düzen öğesidir.</span><span class="sxs-lookup"><span data-stu-id="7e137-205">Consequently, the <xref:System.Windows.Controls.Grid> is the ideal layout element for the application.</span></span>

> [!TIP]
> <span data-ttu-id="7e137-206">Hakkında daha fazla bilgi için <xref:System.Windows.Controls.Panel> öğeler, bkz [paneller genel bakış](../../../../docs/framework/wpf/controls/panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="7e137-206">For more information about <xref:System.Windows.Controls.Panel> elements, see [Panels overview](../../../../docs/framework/wpf/controls/panels-overview.md).</span></span> <span data-ttu-id="7e137-207">Düzen hakkında daha fazla bilgi için bkz: [düzeni](../../../../docs/framework/wpf/advanced/layout.md).</span><span class="sxs-lookup"><span data-stu-id="7e137-207">For more information about layout, see [Layout](../../../../docs/framework/wpf/advanced/layout.md).</span></span>

<span data-ttu-id="7e137-208">Bölümünde, tek sütunlu bir tablo üç satır ve 10 piksel kenar boşluğu ile sütun ve satır tanımları ekleyerek oluşturduğunuz <xref:System.Windows.Controls.Grid> içinde *ExpenseItHome.XAML*.</span><span class="sxs-lookup"><span data-stu-id="7e137-208">In the section, you create a single-column table with three rows and a 10-pixel margin by adding column and row definitions to the <xref:System.Windows.Controls.Grid> in *ExpenseItHome.xaml*.</span></span>

1. <span data-ttu-id="7e137-209">Açık *ExpenseItHome.XAML*.</span><span class="sxs-lookup"><span data-stu-id="7e137-209">Open *ExpenseItHome.xaml*.</span></span>

2. <span data-ttu-id="7e137-210">Ayarlama <xref:System.Windows.FrameworkElement.Margin%2A> özellikte <xref:System.Windows.Controls.Grid> ", sol, üst, sağ ve alt kenar boşlukları için karşılık gelen 10,0,10,10"şeklinde, öğe:</span><span class="sxs-lookup"><span data-stu-id="7e137-210">Set the <xref:System.Windows.FrameworkElement.Margin%2A> property on the <xref:System.Windows.Controls.Grid> element to "10,0,10,10", which corresponds to left, top, right and bottom margins:</span></span>

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > <span data-ttu-id="7e137-211">Ayrıca ayarlayabilirsiniz **kenar boşluğu** değerler **özellikleri** penceresi altında **düzeni** Kategori:</span><span class="sxs-lookup"><span data-stu-id="7e137-211">You can also set the **Margin** values in the **Properties** window, under the **Layout** category:</span></span>
   >
   > ![Özellikler penceresi kenar değerlerde](media/properties-margin.png)

3. <span data-ttu-id="7e137-213">Aşağıdaki XAML'i ekleyin <xref:System.Windows.Controls.Grid> etiketleri satır ve sütun tanımları oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="7e137-213">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags to create the row and column definitions:</span></span>

    [!code-xaml[ExpenseIt#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    <span data-ttu-id="7e137-214"><xref:System.Windows.Controls.RowDefinition.Height%2A> İki satır kümesine <xref:System.Windows.GridLength.Auto%2A>, satırları boyutlandırılır anlamına temel satırları içerikte.</span><span class="sxs-lookup"><span data-stu-id="7e137-214">The <xref:System.Windows.Controls.RowDefinition.Height%2A> of two rows is set to <xref:System.Windows.GridLength.Auto%2A>, which means that the rows are sized base on the content in the rows.</span></span> <span data-ttu-id="7e137-215">Varsayılan <xref:System.Windows.Controls.RowDefinition.Height%2A> olan <xref:System.Windows.GridUnitType.Star> satır yüksekliğini kullanılabilir alan ağırlıklı bir kısmının anlamına gelir boyutlandırma.</span><span class="sxs-lookup"><span data-stu-id="7e137-215">The default <xref:System.Windows.Controls.RowDefinition.Height%2A> is <xref:System.Windows.GridUnitType.Star> sizing, which means that the row height is a weighted proportion of the available space.</span></span> <span data-ttu-id="7e137-216">Her iki satır varsa, örneğin bir <xref:System.Windows.Controls.RowDefinition.Height%2A> , "\*", kullanılabilir alanı yarısıdır yükseklik sahip oldukları her.</span><span class="sxs-lookup"><span data-stu-id="7e137-216">For example if two rows each have a <xref:System.Windows.Controls.RowDefinition.Height%2A> of "\*", they each have a height that is half of the available space.</span></span>

    <span data-ttu-id="7e137-217"><xref:System.Windows.Controls.Grid> Aşağıdaki XAML gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="7e137-217">Your <xref:System.Windows.Controls.Grid> should now look like the following XAML:</span></span>

    [!code-xaml[ExpenseIt#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a><span data-ttu-id="7e137-218">Denetimler ekleme</span><span class="sxs-lookup"><span data-stu-id="7e137-218">Add controls</span></span>

<span data-ttu-id="7e137-219">Bu bölümde, bir kullanıcı için harcama raporunu göstermek için seçebilirsiniz kişilerin listesini göstermek için kullanıcı Arabirimi giriş sayfasını güncelleştirmeniz.</span><span class="sxs-lookup"><span data-stu-id="7e137-219">In this section, you'll update the home page UI to show a list of people that a user can select from to show the expense report for.</span></span> <span data-ttu-id="7e137-220">Denetimler uygulamanız ile etkileşime girmesine izin veren UI nesneleridir.</span><span class="sxs-lookup"><span data-stu-id="7e137-220">Controls are UI objects that allow users to interact with your application.</span></span> <span data-ttu-id="7e137-221">Daha fazla bilgi için bkz: [denetimleri](../../../../docs/framework/wpf/controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="7e137-221">For more information, see [Controls](../../../../docs/framework/wpf/controls/index.md).</span></span>

<span data-ttu-id="7e137-222">Bu kullanıcı Arabirimi oluşturmak için aşağıdaki öğeleri ekleyeceksiniz *ExpenseItHome.XAML*:</span><span class="sxs-lookup"><span data-stu-id="7e137-222">To create this UI, you'll add the following elements to *ExpenseItHome.xaml*:</span></span>

- <span data-ttu-id="7e137-223"><xref:System.Windows.Controls.ListBox> (listesi kişiler için).</span><span class="sxs-lookup"><span data-stu-id="7e137-223"><xref:System.Windows.Controls.ListBox> (for the list of people).</span></span>
- <span data-ttu-id="7e137-224"><xref:System.Windows.Controls.Label> (Liste üstbilgisi için).</span><span class="sxs-lookup"><span data-stu-id="7e137-224"><xref:System.Windows.Controls.Label> (for the list header).</span></span>
- <span data-ttu-id="7e137-225"><xref:System.Windows.Controls.Button> (listede seçilen kişi için harcama raporunu görüntülemek için tıklatın için).</span><span class="sxs-lookup"><span data-stu-id="7e137-225"><xref:System.Windows.Controls.Button> (to click to view the expense report for the person that is selected in the list).</span></span>

<span data-ttu-id="7e137-226">Her denetim bir satırda yerleştirilir <xref:System.Windows.Controls.Grid> ayarlayarak <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> özelliği eklenmiş.</span><span class="sxs-lookup"><span data-stu-id="7e137-226">Each control is placed in a row of the <xref:System.Windows.Controls.Grid> by setting the <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> attached property.</span></span> <span data-ttu-id="7e137-227">Ekli özellikler hakkında daha fazla bilgi için bkz: [bağlı özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="7e137-227">For more information about attached properties, see [Attached Properties Overview](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).</span></span>

1. <span data-ttu-id="7e137-228">Açık *ExpenseItHome.XAML*.</span><span class="sxs-lookup"><span data-stu-id="7e137-228">Open *ExpenseItHome.xaml*.</span></span>

2. <span data-ttu-id="7e137-229">Aşağıdaki XAML'i yere ekleyin <xref:System.Windows.Controls.Grid> etiketler:</span><span class="sxs-lookup"><span data-stu-id="7e137-229">Add the following XAML somewhere between the <xref:System.Windows.Controls.Grid> tags:</span></span>

   [!code-xaml[ExpenseIt#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > <span data-ttu-id="7e137-230">Sürükleyerek denetimleri oluşturabilirsiniz **araç** tasarım penceresini ve bunların özelliklerini ayarlama penceresinden **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="7e137-230">You can also create the controls by dragging them from the **Toolbox** window onto the design window, and then setting their properties in the **Properties** window.</span></span>

3. <span data-ttu-id="7e137-231">Derleme ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7e137-231">Build and run the application.</span></span>

<span data-ttu-id="7e137-232">Aşağıdaki resimde, az önce oluşturduğunuz denetimleri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7e137-232">The following illustration shows the controls you just created:</span></span>

![ExpenseIt örnek ekran görüntüsü](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure2.png)

## <a name="add-an-image-and-a-title"></a><span data-ttu-id="7e137-234">Görüntüyü ve başlık ekleme</span><span class="sxs-lookup"><span data-stu-id="7e137-234">Add an image and a title</span></span>

<span data-ttu-id="7e137-235">Bu bölümde, giriş sayfası kullanıcı Arabirimi bir görüntü ve sayfa başlığını güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="7e137-235">In this section, you'll update the home page UI with an image and a page title.</span></span>

1. <span data-ttu-id="7e137-236">Açık *ExpenseItHome.XAML*.</span><span class="sxs-lookup"><span data-stu-id="7e137-236">Open *ExpenseItHome.xaml*.</span></span>

2. <span data-ttu-id="7e137-237">Başka bir sütuna eklemek <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> bir sabit ile <xref:System.Windows.Controls.ColumnDefinition.Width%2A> 230 piksel:</span><span class="sxs-lookup"><span data-stu-id="7e137-237">Add another column to the <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> with a fixed <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of 230 pixels:</span></span>

    [!code-xaml[ExpenseIt#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11)]

3. <span data-ttu-id="7e137-238">Başka bir satır ekleyin <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, dört satır toplam için:</span><span class="sxs-lookup"><span data-stu-id="7e137-238">Add another row to the <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, for a total of four rows:</span></span>

    [!code-xaml[ExpenseIt#11b](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11b)]

4. <span data-ttu-id="7e137-239">Denetimleri ayarlayarak ikinci sütun taşımak <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> özelliği 1 her üç denetimleri (Kenarlık, ListBox ve düğmesi).</span><span class="sxs-lookup"><span data-stu-id="7e137-239">Move the controls to the second column by setting the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property to 1 in each of the three controls (Border, ListBox, and Button).</span></span>

5. <span data-ttu-id="7e137-240">Her denetim artırılarak bir satır aşağı taşı kendi <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> değeri 1.</span><span class="sxs-lookup"><span data-stu-id="7e137-240">Move each control down a row, by incrementing its <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> value by 1.</span></span>

   <span data-ttu-id="7e137-241">XAML üç denetimleri için şimdi şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="7e137-241">The XAML for the three controls now looks like this:</span></span>

    [!code-xaml[ExpenseIt#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

6. <span data-ttu-id="7e137-242">Ayarlama <xref:System.Windows.Controls.Panel.Background%2A> , <xref:System.Windows.Controls.Grid> olmasını *watermark.png* aşağıdaki XAML yere arasında ekleyerek resim dosyası `<Grid>` ve `<\/Grid>` etiketler:</span><span class="sxs-lookup"><span data-stu-id="7e137-242">Set the <xref:System.Windows.Controls.Panel.Background%2A> of the <xref:System.Windows.Controls.Grid> to be the *watermark.png* image file, by adding the following XAML somewhere between the `<Grid>` and `<\/Grid>` tags:</span></span>

    [!code-xaml[ExpenseIt#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

7. <span data-ttu-id="7e137-243">Önce <xref:System.Windows.Controls.Border> öğesi ekleme bir <xref:System.Windows.Controls.Label> "Gider raporu görüntüle" içeriğe sahip.</span><span class="sxs-lookup"><span data-stu-id="7e137-243">Before the <xref:System.Windows.Controls.Border> element, add a <xref:System.Windows.Controls.Label> with the content "View Expense Report".</span></span> <span data-ttu-id="7e137-244">Bu sayfa başlığıdır.</span><span class="sxs-lookup"><span data-stu-id="7e137-244">This is the title of the page.</span></span>

    [!code-xaml[ExpenseIt#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

8. <span data-ttu-id="7e137-245">Derleme ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7e137-245">Build and run the application.</span></span>

<span data-ttu-id="7e137-246">Aşağıdaki çizimde ne eklemiş sonuçlarını gösterir:</span><span class="sxs-lookup"><span data-stu-id="7e137-246">The following illustration shows the results of what you just added:</span></span>

![ExpenseIt örnek ekran görüntüsü](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure3.png)

## <a name="add-code-to-handle-events"></a><span data-ttu-id="7e137-248">Olayları işlemek için kod ekleme</span><span class="sxs-lookup"><span data-stu-id="7e137-248">Add code to handle events</span></span>

1. <span data-ttu-id="7e137-249">Açık *ExpenseItHome.XAML*.</span><span class="sxs-lookup"><span data-stu-id="7e137-249">Open *ExpenseItHome.xaml*.</span></span>

2. <span data-ttu-id="7e137-250">Ekleme bir <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay işleyicisine <xref:System.Windows.Controls.Button> öğesi.</span><span class="sxs-lookup"><span data-stu-id="7e137-250">Add a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to the <xref:System.Windows.Controls.Button> element.</span></span> <span data-ttu-id="7e137-251">Daha fazla bilgi için bkz: [nasıl yapılır: Basit olay işleyicisi oluşturun](http://msdn.microsoft.com/library/b1456e07-9dec-4354-99cf-18666b64f480).</span><span class="sxs-lookup"><span data-stu-id="7e137-251">For more information, see [How to: Create a simple event handler](http://msdn.microsoft.com/library/b1456e07-9dec-4354-99cf-18666b64f480).</span></span>

    [!code-xaml[ExpenseIt#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

3. <span data-ttu-id="7e137-252">Açık *ExpenseItHome.xaml.vb* veya *ExpenseItHome.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="7e137-252">Open *ExpenseItHome.xaml.vb* or *ExpenseItHome.xaml.cs*.</span></span>

4. <span data-ttu-id="7e137-253">Aşağıdaki kodu ekleyin `ExpenseItHome` düğme eklemek için sınıfı olay işleyicisi'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="7e137-253">Add the following code to the `ExpenseItHome` class to add a button click event handler.</span></span> <span data-ttu-id="7e137-254">Olay işleyicisi açılır **ExpenseReportPage** sayfası.</span><span class="sxs-lookup"><span data-stu-id="7e137-254">The event handler opens the **ExpenseReportPage** page.</span></span>

    [!code-csharp[ExpenseIt#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a><span data-ttu-id="7e137-255">ExpenseReportPage için kullanıcı Arabirimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="7e137-255">Create the UI for ExpenseReportPage</span></span>

<span data-ttu-id="7e137-256">*ExpenseReportPage.xaml* seçili kişi için harcama raporunu görüntüler **ExpenseItHome** sayfası.</span><span class="sxs-lookup"><span data-stu-id="7e137-256">*ExpenseReportPage.xaml* displays the expense report for the person that's selected on the **ExpenseItHome** page.</span></span> <span data-ttu-id="7e137-257">Bu bölümde denetimleri gerekir ve ilişkin kullanıcı Arabirimi oluşturma **ExpenseReportPage**.</span><span class="sxs-lookup"><span data-stu-id="7e137-257">In this section, you'll controls and create the UI for **ExpenseReportPage**.</span></span> <span data-ttu-id="7e137-258">Ayrıca, arka plan ekleyebilir ve Dolgu renkleri çeşitli kullanıcı Arabirimi öğeleri için.</span><span class="sxs-lookup"><span data-stu-id="7e137-258">You'll also add background and fill colors to the various UI elements.</span></span>

1. <span data-ttu-id="7e137-259">Açık *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="7e137-259">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="7e137-260">Aşağıdaki XAML'i ekleyin <xref:System.Windows.Controls.Grid> etiketler:</span><span class="sxs-lookup"><span data-stu-id="7e137-260">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags:</span></span>

    [!code-xaml[ExpenseIt#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    <span data-ttu-id="7e137-261">Bu UI benzer *ExpenseItHome.XAML*, rapor verilerini görüntülenen dışında bir <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="7e137-261">This UI is similar to *ExpenseItHome.xaml*, except the report data is displayed in a <xref:System.Windows.Controls.DataGrid>.</span></span>

3. <span data-ttu-id="7e137-262">Derleme ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7e137-262">Build and run the application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="7e137-263">Bir hata alırsanız <xref:System.Windows.Controls.DataGrid> bulunamadı veya olmayabilir, projeniz .NET Framework 4 veya sonrasını hedefleyen emin olun.</span><span class="sxs-lookup"><span data-stu-id="7e137-263">If you get an error that the <xref:System.Windows.Controls.DataGrid> was not found or does not exist, make sure that your project targets the .NET Framework 4 or later.</span></span> <span data-ttu-id="7e137-264">Daha fazla bilgi için bkz: [nasıl yapılır: .NET Framework sürümü hedef](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span><span class="sxs-lookup"><span data-stu-id="7e137-264">For more information, see [How to: Target a Version of the .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span></span>

4. <span data-ttu-id="7e137-265">Seçin **Görünüm** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="7e137-265">Select the **View** button.</span></span>

    <span data-ttu-id="7e137-266">Harcama Raporu sayfası görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7e137-266">The expense report page appears.</span></span> <span data-ttu-id="7e137-267">Ayrıca geri gezinti düğmesi etkinleştirilir dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="7e137-267">Also notice that the back navigation button is enabled.</span></span>

<span data-ttu-id="7e137-268">Eklenen kullanıcı Arabirimi öğeleri aşağıda gösterilmiştir *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="7e137-268">The following illustration shows the UI elements added to *ExpenseReportPage.xaml*.</span></span>

![ExpenseIt örnek ekran görüntüsü](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure4.png)

## <a name="style-controls"></a><span data-ttu-id="7e137-270">Stili denetimleri</span><span class="sxs-lookup"><span data-stu-id="7e137-270">Style controls</span></span>

<span data-ttu-id="7e137-271">Çeşitli öğelerin görünümü genellikle bir kullanıcı arabiriminde aynı türden tüm öğeler için aynıdır.</span><span class="sxs-lookup"><span data-stu-id="7e137-271">The appearance of various elements is often the same for all elements of the same type in a UI.</span></span> <span data-ttu-id="7e137-272">UI kullanan [stilleri](../../../../docs/framework/wpf/controls/styling-and-templating.md) görünümlerin çoklu öğeler arasında yeniden kullanılabilir olması için.</span><span class="sxs-lookup"><span data-stu-id="7e137-272">UI uses [styles](../../../../docs/framework/wpf/controls/styling-and-templating.md) to make appearances reusable across multiple elements.</span></span> <span data-ttu-id="7e137-273">Kullanılırlığı XAML oluşturulmasını ve yönetimini basitleştirmeye yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="7e137-273">The reusability of styles helps to simplify XAML creation and management.</span></span> <span data-ttu-id="7e137-274">Bu bölümde stilleri önceki adımlarda tanımlanan öğesi başına özniteliklerini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="7e137-274">This section replaces the per-element attributes that were defined in previous steps with styles.</span></span>

1. <span data-ttu-id="7e137-275">Açık *Application.xaml* veya *App.xaml*.</span><span class="sxs-lookup"><span data-stu-id="7e137-275">Open *Application.xaml* or *App.xaml*.</span></span>

2. <span data-ttu-id="7e137-276">Aşağıdaki XAML'i ekleyin <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> etiketler:</span><span class="sxs-lookup"><span data-stu-id="7e137-276">Add the following XAML between the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tags:</span></span>

    [!code-xaml[ExpenseIt#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    <span data-ttu-id="7e137-277">Bu XAML aşağıdaki stilleri ekler:</span><span class="sxs-lookup"><span data-stu-id="7e137-277">This XAML adds the following styles:</span></span>

    - <span data-ttu-id="7e137-278">`headerTextStyle`: Sayfa başlığı Biçimlendirilecek <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="7e137-278">`headerTextStyle`: To format the page title <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="7e137-279">`labelStyle`: Biçimlendirilecek <xref:System.Windows.Controls.Label> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="7e137-279">`labelStyle`: To format the <xref:System.Windows.Controls.Label> controls.</span></span>

    - <span data-ttu-id="7e137-280">`columnHeaderStyle`: Biçimlendirilecek <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span><span class="sxs-lookup"><span data-stu-id="7e137-280">`columnHeaderStyle`: To format the <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span></span>

    - <span data-ttu-id="7e137-281">`listHeaderStyle`: List üstbilgisi Biçimlendirilecek <xref:System.Windows.Controls.Border> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="7e137-281">`listHeaderStyle`: To format the list header <xref:System.Windows.Controls.Border> controls.</span></span>

    - <span data-ttu-id="7e137-282">`listHeaderTextStyle`: List üstbilgisi Biçimlendirilecek <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="7e137-282">`listHeaderTextStyle`: To format the list header <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="7e137-283">`buttonStyle`: Biçimlendirilecek <xref:System.Windows.Controls.Button> ExpenseItHome.XAML üzerinde.</span><span class="sxs-lookup"><span data-stu-id="7e137-283">`buttonStyle`: To format the <xref:System.Windows.Controls.Button> on ExpenseItHome.xaml.</span></span>

    <span data-ttu-id="7e137-284">Stilleri kaynakları ve alt öğeleri olduğuna dikkat edin <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> özellik öğesi.</span><span class="sxs-lookup"><span data-stu-id="7e137-284">Notice that the styles are resources and children of the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> property element.</span></span> <span data-ttu-id="7e137-285">Bu konumda stiller tüm öğelere uygulanır.</span><span class="sxs-lookup"><span data-stu-id="7e137-285">In this location, the styles are applied to all the elements in an application.</span></span> <span data-ttu-id="7e137-286">Bir .NET Framework uygulamasında kaynaklarını kullanan bir örnek için bkz: [kullanım uygulama kaynakları](../../../../docs/framework/wpf/advanced/how-to-use-application-resources.md).</span><span class="sxs-lookup"><span data-stu-id="7e137-286">For an example of using resources in a .NET Framework application, see [Use Application Resources](../../../../docs/framework/wpf/advanced/how-to-use-application-resources.md).</span></span>

3. <span data-ttu-id="7e137-287">Açık *ExpenseItHome.XAML*.</span><span class="sxs-lookup"><span data-stu-id="7e137-287">Open *ExpenseItHome.xaml*.</span></span>

4. <span data-ttu-id="7e137-288">Arasındaki her şeyi değiştirin <xref:System.Windows.Controls.Grid> aşağıdaki XAML ile öğeleri:</span><span class="sxs-lookup"><span data-stu-id="7e137-288">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    <span data-ttu-id="7e137-289">Gibi özellikler <xref:System.Windows.VerticalAlignment> ve <xref:System.Windows.Media.FontFamily> her denetimin görünümünü tanımlamak kaldırılır ve stiller uygulayarak değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="7e137-289">The properties such as <xref:System.Windows.VerticalAlignment> and <xref:System.Windows.Media.FontFamily> that define the look of each control are removed and replaced by applying the styles.</span></span> <span data-ttu-id="7e137-290">Örneğin, `headerTextStyle` harcama raporu görünümü"için" uygulanan <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="7e137-290">For example, the `headerTextStyle` is applied to the "View Expense Report" <xref:System.Windows.Controls.Label>.</span></span>

5. <span data-ttu-id="7e137-291">Açık *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="7e137-291">Open *ExpenseReportPage.xaml*.</span></span>

6. <span data-ttu-id="7e137-292">Arasındaki her şeyi değiştirin <xref:System.Windows.Controls.Grid> aşağıdaki XAML ile öğeleri:</span><span class="sxs-lookup"><span data-stu-id="7e137-292">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    <span data-ttu-id="7e137-293">Bu stiller ekler <xref:System.Windows.Controls.Label> ve <xref:System.Windows.Controls.Border> öğeleri.</span><span class="sxs-lookup"><span data-stu-id="7e137-293">This adds styles to the <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Border> elements.</span></span>

## <a name="bind-data-to-a-control"></a><span data-ttu-id="7e137-294">Bir denetimine veri bağlama</span><span class="sxs-lookup"><span data-stu-id="7e137-294">Bind data to a control</span></span>

<span data-ttu-id="7e137-295">Bu bölümde, çeşitli denetimlere bağlı XML verileri oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="7e137-295">In this section, you'll create the XML data that is bound to various controls.</span></span>

1. <span data-ttu-id="7e137-296">Açık *ExpenseItHome.XAML*.</span><span class="sxs-lookup"><span data-stu-id="7e137-296">Open *ExpenseItHome.xaml*.</span></span>

2. <span data-ttu-id="7e137-297">Açtıktan sonra <xref:System.Windows.Controls.Grid> öğesi oluşturmak için aşağıdaki XAML eklemek bir <xref:System.Windows.Data.XmlDataProvider> her kişi için veri içeren:</span><span class="sxs-lookup"><span data-stu-id="7e137-297">After the opening <xref:System.Windows.Controls.Grid> element, add the following XAML to create an <xref:System.Windows.Data.XmlDataProvider> that contains the data for each person:</span></span>

    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]
    [!code-xaml[ExpenseIt#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#23)]
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]

    <span data-ttu-id="7e137-298">Veri olarak oluşturulan bir <xref:System.Windows.Controls.Grid> kaynak.</span><span class="sxs-lookup"><span data-stu-id="7e137-298">The data is created as a <xref:System.Windows.Controls.Grid> resource.</span></span> <span data-ttu-id="7e137-299">Normalde bu dosya olarak yüklenir, ancak kolaylık sağlamak için veriler satır içi eklenir.</span><span class="sxs-lookup"><span data-stu-id="7e137-299">Normally this would be loaded as a file, but for simplicity the data is added inline.</span></span>

3. <span data-ttu-id="7e137-300">İçinde `<Grid.Resources>` öğesi, aşağıdaki ekleyin <xref:System.Windows.DataTemplate>, verilerin nasıl görüntüleneceğini tanımlayan <xref:System.Windows.Controls.ListBox>:</span><span class="sxs-lookup"><span data-stu-id="7e137-300">Within the `<Grid.Resources>` element, add the following <xref:System.Windows.DataTemplate>, which defines how to display the data in the <xref:System.Windows.Controls.ListBox>:</span></span>

    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]
    [!code-xaml[ExpenseIt#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#24)]
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]

    <span data-ttu-id="7e137-301">Veri şablonları hakkında daha fazla bilgi için bkz: [veri şablonu özeti](../../../../docs/framework/wpf/data/data-templating-overview.md).</span><span class="sxs-lookup"><span data-stu-id="7e137-301">For more information about data templates, see [Data templating overview](../../../../docs/framework/wpf/data/data-templating-overview.md).</span></span>

4. <span data-ttu-id="7e137-302">Varolan <xref:System.Windows.Controls.ListBox> aşağıdaki XAML ile:</span><span class="sxs-lookup"><span data-stu-id="7e137-302">Replace the existing <xref:System.Windows.Controls.ListBox> with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#25](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    <span data-ttu-id="7e137-303">Bu XAML bağlar <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliği <xref:System.Windows.Controls.ListBox> veri kaynağı ve veri şablon olarak geçerlidir <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span><span class="sxs-lookup"><span data-stu-id="7e137-303">This XAML binds the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to the data source and applies the data template as the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span></span>

## <a name="connect-data-to-controls"></a><span data-ttu-id="7e137-304">Veri denetimleri Bağlan</span><span class="sxs-lookup"><span data-stu-id="7e137-304">Connect data to controls</span></span>

<span data-ttu-id="7e137-305">Ardından, seçili adı almak için kod ekleyeceksiniz **ExpenseItHome** sayfasında ve oluşturucusuna geçirin **ExpenseReportPage**.</span><span class="sxs-lookup"><span data-stu-id="7e137-305">Next, you'll add code to retrieve the name that's selected on the **ExpenseItHome** page and pass it to the constructor of **ExpenseReportPage**.</span></span> <span data-ttu-id="7e137-306">**ExpenseReportPage** ne denetimleri tanımlandığı geçirilen öğe ile veri bağlamını ayarlar içinde *ExpenseReportPage.xaml* bağlayın.</span><span class="sxs-lookup"><span data-stu-id="7e137-306">**ExpenseReportPage** sets its data context with the passed item, which is what the controls defined in *ExpenseReportPage.xaml* bind to.</span></span>

1. <span data-ttu-id="7e137-307">Açık *ExpenseReportPage.xaml.vb* veya *ExpenseReportPage.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="7e137-307">Open *ExpenseReportPage.xaml.vb* or *ExpenseReportPage.xaml.cs*.</span></span>

2. <span data-ttu-id="7e137-308">Seçili kişinin harcama raporu verilerini geçirmek için bir nesne alan bir oluşturucu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7e137-308">Add a constructor that takes an object so you can pass the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#26](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. <span data-ttu-id="7e137-309">Açık *ExpenseItHome.xaml.vb* veya *ExpenseItHome.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="7e137-309">Open *ExpenseItHome.xaml.vb* or *ExpenseItHome.xaml.cs*.</span></span>

4. <span data-ttu-id="7e137-310">Değişiklik <xref:System.Windows.Controls.Primitives.ButtonBase.Click> seçili kişinin harcama raporu geçirilen yeni oluşturucuyu çağırmak için olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="7e137-310">Change the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to call the new constructor passing the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#27](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a><span data-ttu-id="7e137-311">Veri şablonları ile stil verileri</span><span class="sxs-lookup"><span data-stu-id="7e137-311">Style data with data templates</span></span>

<span data-ttu-id="7e137-312">Bu bölümde, veri şablonlarını kullanarak veri bağlama listesindeki her bir öğe için kullanıcı Arabirimi güncelleştireceksiniz.</span><span class="sxs-lookup"><span data-stu-id="7e137-312">In this section, you'll update the UI for each item in the data-bound lists by using data templates.</span></span>

1. <span data-ttu-id="7e137-313">Açık *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="7e137-313">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="7e137-314">"Name" ve "Departman" içeriğini bağlama <xref:System.Windows.Controls.Label> uygun veri öğelerine kaynak özelliği.</span><span class="sxs-lookup"><span data-stu-id="7e137-314">Bind the content of the "Name" and "Department" <xref:System.Windows.Controls.Label> elements to the appropriate data source property.</span></span> <span data-ttu-id="7e137-315">Veri bağlama hakkında daha fazla bilgi için bkz: [veri bağlama genel bakış](../../../../docs/framework/wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="7e137-315">For more information about data binding, see [Data binding overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>

    [!code-xaml[ExpenseIt#31](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. <span data-ttu-id="7e137-316">Açtıktan sonra <xref:System.Windows.Controls.Grid> öğesi, harcama raporu verilerini görüntülemek nasıl tanımlayan aşağıdaki veri şablonlarını ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7e137-316">After the opening <xref:System.Windows.Controls.Grid> element, add the following data templates, which define how to display the expense report data:</span></span>

    [!code-xaml[ExpenseIt#30](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. <span data-ttu-id="7e137-317">Şablonlar için geçerli <xref:System.Windows.Controls.DataGrid> gider gösteren sütunları rapor verileri.</span><span class="sxs-lookup"><span data-stu-id="7e137-317">Apply the templates to the <xref:System.Windows.Controls.DataGrid> columns that display the expense report data.</span></span>

    [!code-xaml[ExpenseIt#32](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. <span data-ttu-id="7e137-318">Derleme ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7e137-318">Build and run the application.</span></span>

6. <span data-ttu-id="7e137-319">Bir kişi seçin ve ardından **Görünüm** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="7e137-319">Select a person and then select the **View** button.</span></span>

<span data-ttu-id="7e137-320">Her iki sayfa denetimleri, düzen, stiller, veri bağlama ve uygulanan veri şablonları ile ExpenseIt uygulamasının aşağıda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="7e137-320">The following illustration shows both pages of the ExpenseIt application with controls, layout, styles, data binding, and data templates applied:</span></span>

![ExpenseIt örnek ekran görüntüleri](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure5.png)

> [!NOTE]
> <span data-ttu-id="7e137-322">Bu örnek, belirli bir WPF özelliğini gösterir ve güvenlik, yerelleştirme ve erişilebilirlik gibi için tüm en iyi uygulamaları izleyin değil.</span><span class="sxs-lookup"><span data-stu-id="7e137-322">This sample demonstrates a specific feature of WPF and doesn't follow all best practices for things like security, localization, and accessibility.</span></span> <span data-ttu-id="7e137-323">Kapsamlı WPF ve .NET Framework uygulama geliştirme en iyi uygulamalar için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="7e137-323">For comprehensive coverage of WPF and the .NET Framework application development best practices, see the following topics:</span></span>
>
> - [<span data-ttu-id="7e137-324">Erişilebilirlik</span><span class="sxs-lookup"><span data-stu-id="7e137-324">Accessibility</span></span>](../../../../docs/framework/ui-automation/accessibility-best-practices.md)
>
> - [<span data-ttu-id="7e137-325">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="7e137-325">Security</span></span>](../../../../docs/framework/wpf/security-wpf.md)
>
> - [<span data-ttu-id="7e137-326">WPF Genelleştirme ve yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="7e137-326">WPF globalization and localization</span></span>](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)
>
> - [<span data-ttu-id="7e137-327">WPF Performans</span><span class="sxs-lookup"><span data-stu-id="7e137-327">WPF performance</span></span>](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a><span data-ttu-id="7e137-328">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="7e137-328">Next steps</span></span>

<span data-ttu-id="7e137-329">Bu kılavuzda Windows Presentation Foundation (WPF) kullanarak kullanıcı Arabirimi oluşturma teknikleri sayısı öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="7e137-329">In this walkthrough you learned a number of techniques for creating a UI using Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="7e137-330">Veri bağlama, .NET Framework uygulama yapı taşlarını temel bir anlayış şimdi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7e137-330">You should now have a basic understanding of the building blocks of a data-bound, .NET Framework application.</span></span> <span data-ttu-id="7e137-331">WPF mimarisi ve programlama modelleri hakkında daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="7e137-331">For more information about the WPF architecture and programming models, see the following topics:</span></span>

- [<span data-ttu-id="7e137-332">WPF mimarisi</span><span class="sxs-lookup"><span data-stu-id="7e137-332">WPF architecture</span></span>](../../../../docs/framework/wpf/advanced/wpf-architecture.md)
- [<span data-ttu-id="7e137-333">XAML genel bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="7e137-333">XAML overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="7e137-334">Bağımlılık özelliklerine genel bakış</span><span class="sxs-lookup"><span data-stu-id="7e137-334">Dependency properties overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
- [<span data-ttu-id="7e137-335">Düzen</span><span class="sxs-lookup"><span data-stu-id="7e137-335">Layout</span></span>](../../../../docs/framework/wpf/advanced/layout.md)

<span data-ttu-id="7e137-336">Uygulamaları oluşturma hakkında daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="7e137-336">For more information about creating applications, see the following topics:</span></span>

- [<span data-ttu-id="7e137-337">Uygulama geliştirme</span><span class="sxs-lookup"><span data-stu-id="7e137-337">Application development</span></span>](../../../../docs/framework/wpf/app-development/index.md)
- [<span data-ttu-id="7e137-338">Denetimler</span><span class="sxs-lookup"><span data-stu-id="7e137-338">Controls</span></span>](../../../../docs/framework/wpf/controls/index.md)
- [<span data-ttu-id="7e137-339">Veri bağlama genel bakış</span><span class="sxs-lookup"><span data-stu-id="7e137-339">Data binding overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [<span data-ttu-id="7e137-340">Grafik ve çoklu ortam</span><span class="sxs-lookup"><span data-stu-id="7e137-340">Graphics and multimedia</span></span>](../../../../docs/framework/wpf/graphics-multimedia/index.md)
- [<span data-ttu-id="7e137-341">WPF'deki Belgeler</span><span class="sxs-lookup"><span data-stu-id="7e137-341">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)

## <a name="see-also"></a><span data-ttu-id="7e137-342">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e137-342">See also</span></span>

- [<span data-ttu-id="7e137-343">Paneller Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7e137-343">Panels overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
- [<span data-ttu-id="7e137-344">Veri şablonu özeti</span><span class="sxs-lookup"><span data-stu-id="7e137-344">Data templating overview</span></span>](../../../../docs/framework/wpf/data/data-templating-overview.md)
- [<span data-ttu-id="7e137-345">Bir WPF uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="7e137-345">Build a WPF application</span></span>](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)
- [<span data-ttu-id="7e137-346">Stilleri ve şablonları</span><span class="sxs-lookup"><span data-stu-id="7e137-346">Styles and templates</span></span>](../../../../docs/framework/wpf/controls/styles-and-templates.md)
