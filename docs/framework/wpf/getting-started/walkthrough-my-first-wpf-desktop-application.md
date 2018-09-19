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
ms.custom: vs-dotnet
ms.openlocfilehash: 1a9c82a0bca25fa1242b29393e41e6eb4ce7f3b9
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46007262"
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a><span data-ttu-id="cda96-102">İzlenecek yol: İlk WPF Masaüstü Uygulamam</span><span class="sxs-lookup"><span data-stu-id="cda96-102">Walkthrough: My first WPF desktop application</span></span>

<span data-ttu-id="cda96-103">Bu makalede, çoğu WPF uygulamaları için ortak olan öğeler içeren basit bir Windows Presentation Foundation (WPF) uygulaması geliştirme işlemini göstermektedir: Extensible Application Markup Language (XAML) işaretleme, arka plan kod, uygulama tanımları denetimler, düzen, veri bağlama ve stilleri.</span><span class="sxs-lookup"><span data-stu-id="cda96-103">This article shows you how to develop a simple Windows Presentation Foundation (WPF) application that includes the elements that are common to most WPF applications: Extensible Application Markup Language (XAML) markup, code-behind, application definitions, controls, layout, data binding, and styles.</span></span>

<span data-ttu-id="cda96-104">Bu izlenecek yol aşağıdaki adımları içerir:</span><span class="sxs-lookup"><span data-stu-id="cda96-104">This walkthrough includes the following steps:</span></span>

- <span data-ttu-id="cda96-105">XAML, uygulamanın kullanıcı arabirimini (UI) görünümünü tasarlamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="cda96-105">Use XAML to design the appearance of the application's user interface (UI).</span></span>

- <span data-ttu-id="cda96-106">Uygulamanın davranışı oluşturmak için kod yazın.</span><span class="sxs-lookup"><span data-stu-id="cda96-106">Write code to build the application's behavior.</span></span>

- <span data-ttu-id="cda96-107">Uygulamayı yönetmek için bir uygulama tanımı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cda96-107">Create an application definition to manage the application.</span></span>

- <span data-ttu-id="cda96-108">Denetimler ekleme ve uygulama kullanıcı Arabirimi oluşturmak için düzenini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cda96-108">Add controls and create the layout to compose the application UI.</span></span>

- <span data-ttu-id="cda96-109">Stilleri için uygulamanın UI genelinde tutarlı bir görünüm oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cda96-109">Create styles for a consistent appearance throughout an application's UI.</span></span>

- <span data-ttu-id="cda96-110">Kullanıcı arabirimini hem veri kullanıcı Arabiriminden doldurmak ve verileri ve eşitlenmiş kullanıcı Arabirimi tutmak için verilere bağlayın.</span><span class="sxs-lookup"><span data-stu-id="cda96-110">Bind the UI to data to both populate the UI from data and keep the data and UI synchronized.</span></span>

<span data-ttu-id="cda96-111">İzlenecek yol sonunda, bağımsız bir seçilen kişilerin gider raporlarını görüntülemek kullanıcılara Windows uygulamasında oluşturulan.</span><span class="sxs-lookup"><span data-stu-id="cda96-111">By the end of the walkthrough, you'll have built a standalone Windows application that allows users to view expense reports for selected people.</span></span> <span data-ttu-id="cda96-112">Uygulama, bir tarayıcı penceresinde barındırılan birçok WPF sayfadan oluşur.</span><span class="sxs-lookup"><span data-stu-id="cda96-112">The application is composed of several WPF pages that are hosted in a browser-style window.</span></span>

> [!TIP]
> <span data-ttu-id="cda96-113">Bu izlenecek yolu oluşturmak için kullanılan örnek kod, Visual Basic ve C# için kullanılabilir [WPF uygulamalarını oluşturmaya giriş](https://go.microsoft.com/fwlink/?LinkID=160008).</span><span class="sxs-lookup"><span data-stu-id="cda96-113">The sample code that is used to build this walkthrough is available for both Visual Basic and C# at [Introduction to Building WPF Applications](https://go.microsoft.com/fwlink/?LinkID=160008).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cda96-114">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="cda96-114">Prerequisites</span></span>

- <span data-ttu-id="cda96-115">(Bu makalede, Visual Studio 2017'de bağlıdır) visual Studio 2012 veya üzeri</span><span class="sxs-lookup"><span data-stu-id="cda96-115">Visual Studio 2012 or later (this article is based on Visual Studio 2017)</span></span>

   <span data-ttu-id="cda96-116">Visual Studio'nun en son sürümü yükleme hakkında daha fazla bilgi için bkz. [Visual Studio'yu yükleyin](/visualstudio/install/install-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="cda96-116">For more information about installing the latest version of Visual Studio, see [Install Visual Studio](/visualstudio/install/install-visual-studio).</span></span>

## <a name="create-the-application-project"></a><span data-ttu-id="cda96-117">Uygulama projesini oluşturun</span><span class="sxs-lookup"><span data-stu-id="cda96-117">Create the application project</span></span>

<span data-ttu-id="cda96-118">İlk adım, bir uygulama tanımı, iki sayfaları ve görüntü içeren uygulama altyapısı oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="cda96-118">The first step is to create the application infrastructure, which includes an application definition, two pages, and an image.</span></span>

1. <span data-ttu-id="cda96-119">Visual Basic veya Visual C# adlı yeni bir WPF uygulaması projesi oluşturma **`ExpenseIt`**:</span><span class="sxs-lookup"><span data-stu-id="cda96-119">Create a new WPF Application project in Visual Basic or Visual C# named **`ExpenseIt`**:</span></span>

   1. <span data-ttu-id="cda96-120">Visual Studio açıp seçin **dosya** > **yeni** > **proje**.</span><span class="sxs-lookup"><span data-stu-id="cda96-120">Open Visual Studio and select **File** > **New** > **Project**.</span></span>

      <span data-ttu-id="cda96-121">**Yeni proje** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="cda96-121">The **New Project** dialog opens.</span></span>

   2. <span data-ttu-id="cda96-122">Altında **yüklü** kategorisini genişletin **Visual C#** veya **Visual Basic** düğümüne tıklayın ve ardından **Windows Klasik Masaüstü**.</span><span class="sxs-lookup"><span data-stu-id="cda96-122">Under the **Installed** category, expand either the **Visual C#** or **Visual Basic** node, and then select **Windows Classic Desktop**.</span></span>

   3. <span data-ttu-id="cda96-123">Seçin **WPF uygulaması (.NET Framework)** şablonu.</span><span class="sxs-lookup"><span data-stu-id="cda96-123">Select the **WPF App (.NET Framework)** template.</span></span> <span data-ttu-id="cda96-124">Bir ad girin **`ExpenseIt`** seçip **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="cda96-124">Enter the name **`ExpenseIt`** and then select **OK**.</span></span>

      ![Yeni Proje iletişim kutusu ile WPF uygulama seçildi](media/new-project-dialog.png)

      <span data-ttu-id="cda96-126">Visual Studio projesi oluşturup adlı varsayılan uygulama penceresi için tasarımcı açılır **MainWindow.xaml**.</span><span class="sxs-lookup"><span data-stu-id="cda96-126">Visual Studio creates the project and opens the designer for the default application window named **MainWindow.xaml**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="cda96-127">Bu izlenecek yolda <xref:System.Windows.Controls.DataGrid> kullanılabilir .NET Framework 4 ve üzeri olan denetim.</span><span class="sxs-lookup"><span data-stu-id="cda96-127">This walkthrough uses the <xref:System.Windows.Controls.DataGrid> control that is available in the .NET Framework 4 and later.</span></span> <span data-ttu-id="cda96-128">Sonraki veya projeniz .NET Framework 4 hedefleyen emin olun.</span><span class="sxs-lookup"><span data-stu-id="cda96-128">Be sure that your project targets the .NET Framework 4 or later.</span></span> <span data-ttu-id="cda96-129">Daha fazla bilgi için [nasıl yapılır: .NET Framework sürümü hedefleme](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span><span class="sxs-lookup"><span data-stu-id="cda96-129">For more information, see [How to: Target a Version of the .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span></span>

2. <span data-ttu-id="cda96-130">Açık *Application.xaml* (Visual Basic) veya *App.xaml* (C#).</span><span class="sxs-lookup"><span data-stu-id="cda96-130">Open *Application.xaml* (Visual Basic) or *App.xaml* (C#).</span></span>

    <span data-ttu-id="cda96-131">Bu XAML dosyasını bir WPF uygulaması ve uygulama kaynaklarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cda96-131">This XAML file defines a WPF application and any application resources.</span></span> <span data-ttu-id="cda96-132">Bu dosya otomatik olarak gösteren bir UI belirtmek için de uygulama başladığında; Bu durumda, *MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="cda96-132">You also use this file to specify the UI that automatically shows when the application starts; in this case, *MainWindow.xaml*.</span></span>

    <span data-ttu-id="cda96-133">Visual Basic, XAML şu şekilde görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="cda96-133">Your XAML should look like this in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#1_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    <span data-ttu-id="cda96-134">Ya da böyle C# ' de:</span><span class="sxs-lookup"><span data-stu-id="cda96-134">Or like this in C#:</span></span>

    [!code-xaml[ExpenseIt#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. <span data-ttu-id="cda96-135">Açık *MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="cda96-135">Open *MainWindow.xaml*.</span></span>

    <span data-ttu-id="cda96-136">Bu XAML dosyası ana penceresinde, uygulamanızın ve sayfalarında oluşturulan içeriği görüntüler.</span><span class="sxs-lookup"><span data-stu-id="cda96-136">This XAML file is the main window of your application and displays content created in pages.</span></span> <span data-ttu-id="cda96-137"><xref:System.Windows.Window> Sınıfı gibi başlık, boyut veya simge, bir penceresi özelliklerini tanımlar ve kapatma veya gizleme gibi olayları işler.</span><span class="sxs-lookup"><span data-stu-id="cda96-137">The <xref:System.Windows.Window> class defines the properties of a window, such as its title, size, or icon, and handles events, such as closing or hiding.</span></span>

4. <span data-ttu-id="cda96-138">Değişiklik <xref:System.Windows.Window> öğesine bir <xref:System.Windows.Navigation.NavigationWindow>aşağıdaki XAML içinde gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="cda96-138">Change the <xref:System.Windows.Window> element to a <xref:System.Windows.Navigation.NavigationWindow>, as shown in the following XAML:</span></span>

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   <span data-ttu-id="cda96-139">Bu uygulamanın kullanıcı girişi bağlı olarak farklı içerik gider.</span><span class="sxs-lookup"><span data-stu-id="cda96-139">This app navigates to different content depending on the user input.</span></span> <span data-ttu-id="cda96-140">Bu nedenle, ana <xref:System.Windows.Window> için değiştirilmesi gereken bir <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="cda96-140">This is why the main <xref:System.Windows.Window> needs to be changed to a <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="cda96-141"><xref:System.Windows.Navigation.NavigationWindow> tüm özelliklerini devralır <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="cda96-141"><xref:System.Windows.Navigation.NavigationWindow> inherits all the properties of <xref:System.Windows.Window>.</span></span> <span data-ttu-id="cda96-142"><xref:System.Windows.Navigation.NavigationWindow> XAML dosyasında öğe bir örneğini oluşturur <xref:System.Windows.Navigation.NavigationWindow> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="cda96-142">The <xref:System.Windows.Navigation.NavigationWindow> element in the XAML file creates an instance of the <xref:System.Windows.Navigation.NavigationWindow> class.</span></span> <span data-ttu-id="cda96-143">Daha fazla bilgi için [gezintiye genel bakış](../../../../docs/framework/wpf/app-development/navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cda96-143">For more information, see [Navigation overview](../../../../docs/framework/wpf/app-development/navigation-overview.md).</span></span>

5. <span data-ttu-id="cda96-144">Aşağıdaki özellikleri değiştirmek <xref:System.Windows.Navigation.NavigationWindow> öğesi:</span><span class="sxs-lookup"><span data-stu-id="cda96-144">Change the following properties on the <xref:System.Windows.Navigation.NavigationWindow> element:</span></span>

    - <span data-ttu-id="cda96-145">Ayarlama <xref:System.Windows.Window.Title%2A> özelliğini "`ExpenseIt`".</span><span class="sxs-lookup"><span data-stu-id="cda96-145">Set the <xref:System.Windows.Window.Title%2A> property to "`ExpenseIt`".</span></span>

    - <span data-ttu-id="cda96-146">Ayarlama <xref:System.Windows.FrameworkElement.Width%2A> özelliğini 500 piksel.</span><span class="sxs-lookup"><span data-stu-id="cda96-146">Set the <xref:System.Windows.FrameworkElement.Width%2A> property to 500 pixels.</span></span>

    - <span data-ttu-id="cda96-147">Ayarlama <xref:System.Windows.FrameworkElement.Height%2A> özelliğini 350 piksel.</span><span class="sxs-lookup"><span data-stu-id="cda96-147">Set the <xref:System.Windows.FrameworkElement.Height%2A> property to 350 pixels.</span></span>

    - <span data-ttu-id="cda96-148">Kaldırma <xref:System.Windows.Controls.Grid> öğeler arasında <xref:System.Windows.Navigation.NavigationWindow> etiketler.</span><span class="sxs-lookup"><span data-stu-id="cda96-148">Remove the <xref:System.Windows.Controls.Grid> elements between the <xref:System.Windows.Navigation.NavigationWindow> tags.</span></span>

    <span data-ttu-id="cda96-149">Visual Basic, XAML şu şekilde görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="cda96-149">Your XAML should look like this in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#2_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    <span data-ttu-id="cda96-150">Ya da böyle C# ' de:</span><span class="sxs-lookup"><span data-stu-id="cda96-150">Or like this in C#:</span></span>

    [!code-xaml[ExpenseIt#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

6. <span data-ttu-id="cda96-151">Açık *MainWindow.xaml.vb* veya *MainWindow.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="cda96-151">Open *MainWindow.xaml.vb* or *MainWindow.xaml.cs*.</span></span>

    <span data-ttu-id="cda96-152">Bildirilen olaylarını işlemek için kod içeren bir arka plan kod dosyası bu dosyadır *MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="cda96-152">This file is a code-behind file that contains code to handle the events declared in *MainWindow.xaml*.</span></span> <span data-ttu-id="cda96-153">Bu dosya, XAML içinde tanımlanan penceresi için bir parçalı sınıf içerir.</span><span class="sxs-lookup"><span data-stu-id="cda96-153">This file contains a partial class for the window defined in XAML.</span></span>

7. <span data-ttu-id="cda96-154">C# kullanıyorsanız değiştirme `MainWindow` öğesinden türetilen sınıfın <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="cda96-154">If you are using C#, change the `MainWindow` class to derive from <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="cda96-155">(XAML penceresinde değiştirdiğinizde Visual Basic'te bu otomatik olarak gerçekleşir.)</span><span class="sxs-lookup"><span data-stu-id="cda96-155">(In Visual Basic, this happens automatically when you change the window in XAML.)</span></span>

   <span data-ttu-id="cda96-156">Kodunuz şu şekilde görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="cda96-156">Your code should look like this:</span></span>

   [!code-csharp[ExpenseIt#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml.cs#3)]
   [!code-vb[ExpenseIt#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml.vb#3)]

   > [!TIP]
   > <span data-ttu-id="cda96-157">Kod dili örnek kodun C# ve Visual Basic'te arasında geçiş yapabilirsiniz **dil** bu makalenin üst sağ taraftaki açılır.</span><span class="sxs-lookup"><span data-stu-id="cda96-157">You can toggle the code language of the sample code between C# and Visual Basic in the **Language** drop-down on the upper right side of this article.</span></span>

## <a name="add-files-to-the-application"></a><span data-ttu-id="cda96-158">Uygulama için dosyaları Ekle</span><span class="sxs-lookup"><span data-stu-id="cda96-158">Add files to the application</span></span>

<span data-ttu-id="cda96-159">Bu bölümde, uygulamaya iki sayfaları ve görüntü ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="cda96-159">In this section, you'll add two pages and an image to the application.</span></span>

1. <span data-ttu-id="cda96-160">Projeye yeni bir WPF sayfa ekleyin ve adlandırın *`ExpenseItHome.xaml`*:</span><span class="sxs-lookup"><span data-stu-id="cda96-160">Add a new WPF page to the project, and name it *`ExpenseItHome.xaml`*:</span></span>

   1. <span data-ttu-id="cda96-161">İçinde **Çözüm Gezgini**, sağ **`ExpenseIt`** projesini düğümünü ve ardından **Ekle** > **sayfa**.</span><span class="sxs-lookup"><span data-stu-id="cda96-161">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="cda96-162">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sayfa (WPF)** şablon zaten seçili.</span><span class="sxs-lookup"><span data-stu-id="cda96-162">In the **Add New Item** dialog, the **Page (WPF)** template is already selected.</span></span> <span data-ttu-id="cda96-163">Bir ad girin **`ExpenseItHome`** ve ardından **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="cda96-163">Enter the name **`ExpenseItHome`**, and then select **Add**.</span></span>

    <span data-ttu-id="cda96-164">Uygulama başlatıldığında görüntülenen ilk sayfa sayfasıdır.</span><span class="sxs-lookup"><span data-stu-id="cda96-164">This page is the first page that's displayed when the application is launched.</span></span> <span data-ttu-id="cda96-165">İçin harcama raporunu görüntülemek için seçmek için kişi listesi gösterilir.</span><span class="sxs-lookup"><span data-stu-id="cda96-165">It will show a list of people to select from, to show an expense report for.</span></span>

2. <span data-ttu-id="cda96-166">Açık *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="cda96-166">Open *`ExpenseItHome.xaml`*.</span></span>

3. <span data-ttu-id="cda96-167">Ayarlama <xref:System.Windows.Controls.Page.Title%2A> için "`ExpenseIt - Home`".</span><span class="sxs-lookup"><span data-stu-id="cda96-167">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - Home`".</span></span>

    <span data-ttu-id="cda96-168">Visual Basic, XAML şu şekilde görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="cda96-168">Your XAML should look like this in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#6_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    <span data-ttu-id="cda96-169">Veya bu C# ' de:</span><span class="sxs-lookup"><span data-stu-id="cda96-169">Or this in C#:</span></span>

    [!code-xaml[ExpenseIt#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

4. <span data-ttu-id="cda96-170">Açık *MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="cda96-170">Open *MainWindow.xaml*.</span></span>

5. <span data-ttu-id="cda96-171">Ayarlama <xref:System.Windows.Navigation.NavigationWindow.Source%2A> özelliği <xref:System.Windows.Navigation.NavigationWindow> için "`ExpenseItHome.xaml`".</span><span class="sxs-lookup"><span data-stu-id="cda96-171">Set the <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property on the <xref:System.Windows.Navigation.NavigationWindow> to "`ExpenseItHome.xaml`".</span></span>

    <span data-ttu-id="cda96-172">Bu ayarlar *`ExpenseItHome.xaml`* ilk olarak uygulama başladığında açılır.</span><span class="sxs-lookup"><span data-stu-id="cda96-172">This sets *`ExpenseItHome.xaml`* to be the first page opened when the application starts.</span></span> <span data-ttu-id="cda96-173">Visual Basic, XAML şu şekilde görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="cda96-173">Your XAML should look like this in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#7_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    <span data-ttu-id="cda96-174">Veya bu C# ' de:</span><span class="sxs-lookup"><span data-stu-id="cda96-174">Or this in C#:</span></span>

    [!code-xaml[ExpenseIt#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > <span data-ttu-id="cda96-175">Ayrıca **kaynak** özelliğinde **çeşitli** kategorisi **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="cda96-175">You can also set the **Source** property in the **Miscellaneous** category of the **Properties** window.</span></span>
   >
   > ![Özellikler penceresinde Source özelliği](media/properties-source.png)

6. <span data-ttu-id="cda96-177">Başka bir yeni WPF sayfası projeye ekleyin ve adlandırın *ExpenseReportPage.xaml*::</span><span class="sxs-lookup"><span data-stu-id="cda96-177">Add another new WPF page to the project, and name it *ExpenseReportPage.xaml*::</span></span>

   1. <span data-ttu-id="cda96-178">İçinde **Çözüm Gezgini**, sağ **`ExpenseIt`** projesini düğümünü ve ardından **Ekle** > **sayfa**.</span><span class="sxs-lookup"><span data-stu-id="cda96-178">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="cda96-179">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sayfa (WPF)** şablon zaten seçili.</span><span class="sxs-lookup"><span data-stu-id="cda96-179">In the **Add New Item** dialog, the **Page (WPF)** template is already selected.</span></span> <span data-ttu-id="cda96-180">Bir ad girin **ExpenseReportPage**ve ardından **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="cda96-180">Enter the name **ExpenseReportPage**, and then select **Add**.</span></span>

    <span data-ttu-id="cda96-181">Bu sayfada, harcama raporlarını seçildiğinde kişinin gösterilir **`ExpenseItHome`** sayfası.</span><span class="sxs-lookup"><span data-stu-id="cda96-181">This page will show the expense report for the person that is selected on the **`ExpenseItHome`** page.</span></span>

7. <span data-ttu-id="cda96-182">Açık *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="cda96-182">Open *ExpenseReportPage.xaml*.</span></span>

8. <span data-ttu-id="cda96-183">Ayarlama <xref:System.Windows.Controls.Page.Title%2A> için "`ExpenseIt - View Expense`".</span><span class="sxs-lookup"><span data-stu-id="cda96-183">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - View Expense`".</span></span>

    <span data-ttu-id="cda96-184">Visual Basic, XAML şu şekilde görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="cda96-184">Your XAML should look like this in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#4_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    <span data-ttu-id="cda96-185">Veya bu C# ' de:</span><span class="sxs-lookup"><span data-stu-id="cda96-185">Or this in C#:</span></span>

    [!code-xaml[ExpenseIt#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

9. <span data-ttu-id="cda96-186">Açık *ExpenseItHome.xaml.vb* ve *ExpenseReportPage.xaml.vb*, veya *ExpenseItHome.xaml.cs* ve *ExpenseReportPage.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="cda96-186">Open *ExpenseItHome.xaml.vb* and *ExpenseReportPage.xaml.vb*, or *ExpenseItHome.xaml.cs* and *ExpenseReportPage.xaml.cs*.</span></span>

    <span data-ttu-id="cda96-187">Yeni bir sayfa dosyası oluşturduğunuzda, Visual Studio otomatik olarak oluşturur bir *arka plan kod* dosya.</span><span class="sxs-lookup"><span data-stu-id="cda96-187">When you create a new Page file, Visual Studio automatically creates a *code-behind* file.</span></span> <span data-ttu-id="cda96-188">Bu arka plan kod dosyaları, kullanıcı girişine yanıt mantığı işler.</span><span class="sxs-lookup"><span data-stu-id="cda96-188">These code-behind files handle the logic for responding to user input.</span></span>

    <span data-ttu-id="cda96-189">Kodunuz için şunun gibi görünmelidir **`ExpenseItHome`**:</span><span class="sxs-lookup"><span data-stu-id="cda96-189">Your code should look like this for **`ExpenseItHome`**:</span></span>

    [!code-csharp[ExpenseIt#2_5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]
    [!code-vb[ExpenseIt#2_5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    <span data-ttu-id="cda96-190">Ve bunun gibi **ExpenseReportPage**:</span><span class="sxs-lookup"><span data-stu-id="cda96-190">And like this for **ExpenseReportPage**:</span></span>

    [!code-csharp[ExpenseIt#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]
    [!code-vb[ExpenseIt#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

10. <span data-ttu-id="cda96-191">Adlandırılmış resim ekleme *watermark.png* projeye.</span><span class="sxs-lookup"><span data-stu-id="cda96-191">Add an image named *watermark.png* to the project.</span></span> <span data-ttu-id="cda96-192">Kendi görüntünüzü oluşturma,'nden örnek kodu dosyasını kopyalayın veya bunu [burada](https://github.com/dotnet/docs/blob/master/docs/framework/wpf/getting-started/media/watermark.png).</span><span class="sxs-lookup"><span data-stu-id="cda96-192">You can create your own image, copy the file from the sample code, or get it [here](https://github.com/dotnet/docs/blob/master/docs/framework/wpf/getting-started/media/watermark.png).</span></span>

   1. <span data-ttu-id="cda96-193">Proje düğümüne sağ tıklayıp **Ekle** > **var olan öğe**, veya basın **Shift**+**Alt** + **A**.</span><span class="sxs-lookup"><span data-stu-id="cda96-193">Right-click on the project node and select **Add** > **Existing Item**, or press **Shift**+**Alt**+**A**.</span></span>

   2. <span data-ttu-id="cda96-194">İçinde **varolan öğeyi Ekle** iletişim kutusunu kullanın ve ardından istediğiniz görüntü dosyasına Gözat **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="cda96-194">In the **Add Existing Item** dialog, browse to the image file you want to use, and then select **Add**.</span></span>

## <a name="build-and-run-the-application"></a><span data-ttu-id="cda96-195">Uygulaması derleme ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="cda96-195">Build and run the application</span></span>

1. <span data-ttu-id="cda96-196">Uygulaması derleme ve çalıştırma için basın **F5** veya **hata ayıklamayı Başlat** gelen **hata ayıklama** menüsü.</span><span class="sxs-lookup"><span data-stu-id="cda96-196">To build and run the application, press **F5** or select **Start Debugging** from the **Debug** menu.</span></span>

    <span data-ttu-id="cda96-197">Uygulama ile aşağıdaki çizimde <xref:System.Windows.Navigation.NavigationWindow> düğmeleri:</span><span class="sxs-lookup"><span data-stu-id="cda96-197">The following illustration shows the application with the <xref:System.Windows.Navigation.NavigationWindow> buttons:</span></span>

    ![ExpenseIt örnek ekran görüntüsü](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure1.png)

2. <span data-ttu-id="cda96-199">Visual Studio'ya dönmek için uygulamayı kapatın.</span><span class="sxs-lookup"><span data-stu-id="cda96-199">Close the application to return to Visual Studio.</span></span>

## <a name="create-the-layout"></a><span data-ttu-id="cda96-200">Düzen oluştur</span><span class="sxs-lookup"><span data-stu-id="cda96-200">Create the layout</span></span>

<span data-ttu-id="cda96-201">Düzeni, kullanıcı Arabirimi öğeleri yerleştirmek için sıralı bir yol sağlar ve bir kullanıcı Arabirimi yeniden boyutlandırıldığında boyutunu ve konumunu söz konusu öğelerin da yönetir.</span><span class="sxs-lookup"><span data-stu-id="cda96-201">Layout provides an ordered way to place UI elements, and also manages the size and position of those elements when a UI is resized.</span></span> <span data-ttu-id="cda96-202">Genellikle bir düzen aşağıdaki düzen denetimlerden birini oluşturursunuz:</span><span class="sxs-lookup"><span data-stu-id="cda96-202">You typically create a layout with one of the following layout controls:</span></span>

- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.DockPanel>
- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.VirtualizingStackPanel>
- <xref:System.Windows.Controls.WrapPanel>

<span data-ttu-id="cda96-203">Bu düzen denetimlerin her birinden alt öğeleri için özel bir düzen türünü destekler.</span><span class="sxs-lookup"><span data-stu-id="cda96-203">Each of these layout controls supports a special type of layout for its child elements.</span></span> <span data-ttu-id="cda96-204">`ExpenseIt` sayfaları yeniden boyutlandırılıp boyutlandırılamayacağını ve her sayfanın diğer öğeleri Yatayda ve Dikeyde düzenlenmiş öğelere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="cda96-204">`ExpenseIt` pages can be resized, and each page has elements that are arranged horizontally and vertically alongside other elements.</span></span> <span data-ttu-id="cda96-205">Sonuç olarak, <xref:System.Windows.Controls.Grid> uygulama için ideal bir düzen öğesidir.</span><span class="sxs-lookup"><span data-stu-id="cda96-205">Consequently, the <xref:System.Windows.Controls.Grid> is the ideal layout element for the application.</span></span>

> [!TIP]
> <span data-ttu-id="cda96-206">Hakkında daha fazla bilgi için <xref:System.Windows.Controls.Panel> öğeler, bkz [panellere genel bakış](../../../../docs/framework/wpf/controls/panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cda96-206">For more information about <xref:System.Windows.Controls.Panel> elements, see [Panels overview](../../../../docs/framework/wpf/controls/panels-overview.md).</span></span> <span data-ttu-id="cda96-207">Düzen hakkında daha fazla bilgi için bkz. [Düzen](../../../../docs/framework/wpf/advanced/layout.md).</span><span class="sxs-lookup"><span data-stu-id="cda96-207">For more information about layout, see [Layout](../../../../docs/framework/wpf/advanced/layout.md).</span></span>

<span data-ttu-id="cda96-208">Bölümünde, bir tek sütunlu tablo üç satır ve 10-piksel kenar boşluğu ile sütun ve satır tanımlara ekleyerek oluşturduğunuz <xref:System.Windows.Controls.Grid> içinde *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="cda96-208">In the section, you create a single-column table with three rows and a 10-pixel margin by adding column and row definitions to the <xref:System.Windows.Controls.Grid> in *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="cda96-209">Açık *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="cda96-209">Open *`ExpenseItHome.xaml`*.</span></span>

2. <span data-ttu-id="cda96-210">Ayarlama <xref:System.Windows.FrameworkElement.Margin%2A> özelliği <xref:System.Windows.Controls.Grid> ", sol, üst, sağ ve alt kenar boşlukları için karşılık gelen 10,0,10,10 şeklinde", öğe:</span><span class="sxs-lookup"><span data-stu-id="cda96-210">Set the <xref:System.Windows.FrameworkElement.Margin%2A> property on the <xref:System.Windows.Controls.Grid> element to "10,0,10,10", which corresponds to left, top, right and bottom margins:</span></span>

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > <span data-ttu-id="cda96-211">Ayrıca **kenar boşluğu** değerler **özellikleri** penceresi altında **Düzen** kategorisi:</span><span class="sxs-lookup"><span data-stu-id="cda96-211">You can also set the **Margin** values in the **Properties** window, under the **Layout** category:</span></span>
   >
   > ![Özellikler penceresinde kenar boşluğu değerleri](media/properties-margin.png)

3. <span data-ttu-id="cda96-213">Aşağıdaki XAML arasında ekleme <xref:System.Windows.Controls.Grid> etiketleri satır ve sütun tanımları oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="cda96-213">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags to create the row and column definitions:</span></span>

    [!code-xaml[ExpenseIt#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    <span data-ttu-id="cda96-214"><xref:System.Windows.Controls.RowDefinition.Height%2A> İki satır kümesine <xref:System.Windows.GridLength.Auto%2A>, satırları boyutlandırılır anlamına temel satırları içerikte.</span><span class="sxs-lookup"><span data-stu-id="cda96-214">The <xref:System.Windows.Controls.RowDefinition.Height%2A> of two rows is set to <xref:System.Windows.GridLength.Auto%2A>, which means that the rows are sized base on the content in the rows.</span></span> <span data-ttu-id="cda96-215">Varsayılan <xref:System.Windows.Controls.RowDefinition.Height%2A> olduğu <xref:System.Windows.GridUnitType.Star> boyutlandırma, satır yüksekliğini kullanılabilir alanı ağırlıklı oranını olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="cda96-215">The default <xref:System.Windows.Controls.RowDefinition.Height%2A> is <xref:System.Windows.GridUnitType.Star> sizing, which means that the row height is a weighted proportion of the available space.</span></span> <span data-ttu-id="cda96-216">Örneğin her iki satır varsa bir <xref:System.Windows.Controls.RowDefinition.Height%2A> , "\*", sahip oldukları her ikiye kadar kullanılabilir alan olduğundan bir yükseklik.</span><span class="sxs-lookup"><span data-stu-id="cda96-216">For example if two rows each have a <xref:System.Windows.Controls.RowDefinition.Height%2A> of "\*", they each have a height that is half of the available space.</span></span>

    <span data-ttu-id="cda96-217"><xref:System.Windows.Controls.Grid> Aşağıdaki XAML gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="cda96-217">Your <xref:System.Windows.Controls.Grid> should now look like the following XAML:</span></span>

    [!code-xaml[ExpenseIt#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a><span data-ttu-id="cda96-218">Denetimler ekleme</span><span class="sxs-lookup"><span data-stu-id="cda96-218">Add controls</span></span>

<span data-ttu-id="cda96-219">Bu bölümde, giriş sayfasında bir kullanıcı için harcama raporlarını seçebilirsiniz kişilerin listesini gösteren kullanıcı Arabirimi güncelleştireceksiniz.</span><span class="sxs-lookup"><span data-stu-id="cda96-219">In this section, you'll update the home page UI to show a list of people that a user can select from to show the expense report for.</span></span> <span data-ttu-id="cda96-220">Kullanıcıların uygulamanızla etkileşmesini UI nesneleri denetimlerdir.</span><span class="sxs-lookup"><span data-stu-id="cda96-220">Controls are UI objects that allow users to interact with your application.</span></span> <span data-ttu-id="cda96-221">Daha fazla bilgi için [denetimleri](../../../../docs/framework/wpf/controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="cda96-221">For more information, see [Controls](../../../../docs/framework/wpf/controls/index.md).</span></span>

<span data-ttu-id="cda96-222">Bu kullanıcı Arabirimi oluşturmak için aşağıdaki öğelere ekleyeceksiniz *`ExpenseItHome.xaml`*:</span><span class="sxs-lookup"><span data-stu-id="cda96-222">To create this UI, you'll add the following elements to *`ExpenseItHome.xaml`*:</span></span>

- <span data-ttu-id="cda96-223"><xref:System.Windows.Controls.ListBox> (kişilerin listesi için).</span><span class="sxs-lookup"><span data-stu-id="cda96-223"><xref:System.Windows.Controls.ListBox> (for the list of people).</span></span>
- <span data-ttu-id="cda96-224"><xref:System.Windows.Controls.Label> (liste başlığı için).</span><span class="sxs-lookup"><span data-stu-id="cda96-224"><xref:System.Windows.Controls.Label> (for the list header).</span></span>
- <span data-ttu-id="cda96-225"><xref:System.Windows.Controls.Button> (listeden seçilen kişi için harcama raporlarını görüntülemek için tıklayın için).</span><span class="sxs-lookup"><span data-stu-id="cda96-225"><xref:System.Windows.Controls.Button> (to click to view the expense report for the person that is selected in the list).</span></span>

<span data-ttu-id="cda96-226">Her denetim bir satırda yerleştirilir <xref:System.Windows.Controls.Grid> ayarlayarak <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> ekli özellik.</span><span class="sxs-lookup"><span data-stu-id="cda96-226">Each control is placed in a row of the <xref:System.Windows.Controls.Grid> by setting the <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> attached property.</span></span> <span data-ttu-id="cda96-227">Ekli özellikler hakkında daha fazla bilgi için bkz. [ekli özelliklere genel bakış](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cda96-227">For more information about attached properties, see [Attached Properties Overview](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).</span></span>

1. <span data-ttu-id="cda96-228">Açık *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="cda96-228">Open *`ExpenseItHome.xaml`*.</span></span>

2. <span data-ttu-id="cda96-229">Aşağıdaki XAML bir yerde arasında ekleme <xref:System.Windows.Controls.Grid> etiketler:</span><span class="sxs-lookup"><span data-stu-id="cda96-229">Add the following XAML somewhere between the <xref:System.Windows.Controls.Grid> tags:</span></span>

   [!code-xaml[ExpenseIt#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > <span data-ttu-id="cda96-230">Denetimlere sürükleyerek de oluşturabilirsiniz **araç kutusu** tasarım penceresini ve özelliklerini ayarlayarak ardından penceresinden **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="cda96-230">You can also create the controls by dragging them from the **Toolbox** window onto the design window, and then setting their properties in the **Properties** window.</span></span>

3. <span data-ttu-id="cda96-231">Derleme ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cda96-231">Build and run the application.</span></span>

<span data-ttu-id="cda96-232">Aşağıdaki çizimde, yeni oluşturduğunuz denetimleri gösterir:</span><span class="sxs-lookup"><span data-stu-id="cda96-232">The following illustration shows the controls you just created:</span></span>

![ExpenseIt örnek ekran görüntüsü](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure2.png)

## <a name="add-an-image-and-a-title"></a><span data-ttu-id="cda96-234">Resim ve Başlık Ekle</span><span class="sxs-lookup"><span data-stu-id="cda96-234">Add an image and a title</span></span>

<span data-ttu-id="cda96-235">Bu bölümde, giriş sayfası kullanıcı Arabirimi, görüntü ve sayfa başlığı ile güncelleştireceksiniz.</span><span class="sxs-lookup"><span data-stu-id="cda96-235">In this section, you'll update the home page UI with an image and a page title.</span></span>

1. <span data-ttu-id="cda96-236">Açık *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="cda96-236">Open *`ExpenseItHome.xaml`*.</span></span>

2. <span data-ttu-id="cda96-237">Başka bir sütuna eklemek <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> sabit ile <xref:System.Windows.Controls.ColumnDefinition.Width%2A> 230 piksel:</span><span class="sxs-lookup"><span data-stu-id="cda96-237">Add another column to the <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> with a fixed <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of 230 pixels:</span></span>

    [!code-xaml[ExpenseIt#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11)]

3. <span data-ttu-id="cda96-238">Başka bir satır <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, toplam dört satır için:</span><span class="sxs-lookup"><span data-stu-id="cda96-238">Add another row to the <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, for a total of four rows:</span></span>

    [!code-xaml[ExpenseIt#11b](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11b)]

4. <span data-ttu-id="cda96-239">Denetimleri ayarlayarak ikinci sütuna Taşı <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> özelliği 1 her üç denetimleri (Kenarlık, liste kutusu ve düğme).</span><span class="sxs-lookup"><span data-stu-id="cda96-239">Move the controls to the second column by setting the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property to 1 in each of the three controls (Border, ListBox, and Button).</span></span>

5. <span data-ttu-id="cda96-240">Her denetim artırılarak bir satır aşağı taşı, <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> değeri 1.</span><span class="sxs-lookup"><span data-stu-id="cda96-240">Move each control down a row, by incrementing its <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> value by 1.</span></span>

   <span data-ttu-id="cda96-241">XAML için üç denetim artık şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="cda96-241">The XAML for the three controls now looks like this:</span></span>

    [!code-xaml[ExpenseIt#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

6. <span data-ttu-id="cda96-242">Ayarlama <xref:System.Windows.Controls.Panel.Background%2A> , <xref:System.Windows.Controls.Grid> olmasını *watermark.png* görüntü dosyası, aşağıdaki XAML bir yerde arasında ekleyerek `<Grid>` ve `</Grid>` etiketler:</span><span class="sxs-lookup"><span data-stu-id="cda96-242">Set the <xref:System.Windows.Controls.Panel.Background%2A> of the <xref:System.Windows.Controls.Grid> to be the *watermark.png* image file, by adding the following XAML somewhere between the `<Grid>` and `</Grid>` tags:</span></span>

    [!code-xaml[ExpenseIt#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

7. <span data-ttu-id="cda96-243">Önce <xref:System.Windows.Controls.Border> öğe, Ekle bir <xref:System.Windows.Controls.Label> "Harcama Raporu Görüntüle" içeriğe sahip.</span><span class="sxs-lookup"><span data-stu-id="cda96-243">Before the <xref:System.Windows.Controls.Border> element, add a <xref:System.Windows.Controls.Label> with the content "View Expense Report".</span></span> <span data-ttu-id="cda96-244">Sayfanın başlığını budur.</span><span class="sxs-lookup"><span data-stu-id="cda96-244">This is the title of the page.</span></span>

    [!code-xaml[ExpenseIt#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

8. <span data-ttu-id="cda96-245">Derleme ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cda96-245">Build and run the application.</span></span>

<span data-ttu-id="cda96-246">Hangi yeni eklediğiniz sonucu aşağıda gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="cda96-246">The following illustration shows the results of what you just added:</span></span>

![ExpenseIt örnek ekran görüntüsü](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure3.png)

## <a name="add-code-to-handle-events"></a><span data-ttu-id="cda96-248">Olayları işlemek için kod ekleyin</span><span class="sxs-lookup"><span data-stu-id="cda96-248">Add code to handle events</span></span>

1. <span data-ttu-id="cda96-249">Açık *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="cda96-249">Open *`ExpenseItHome.xaml`*.</span></span>

2. <span data-ttu-id="cda96-250">Ekleme bir <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay işleyicisine <xref:System.Windows.Controls.Button> öğesi.</span><span class="sxs-lookup"><span data-stu-id="cda96-250">Add a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to the <xref:System.Windows.Controls.Button> element.</span></span> <span data-ttu-id="cda96-251">Daha fazla bilgi için [nasıl yapılır: Basit olay işleyicisi oluşturun](https://msdn.microsoft.com/library/b1456e07-9dec-4354-99cf-18666b64f480).</span><span class="sxs-lookup"><span data-stu-id="cda96-251">For more information, see [How to: Create a simple event handler](https://msdn.microsoft.com/library/b1456e07-9dec-4354-99cf-18666b64f480).</span></span>

    [!code-xaml[ExpenseIt#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

3. <span data-ttu-id="cda96-252">Açık *`ExpenseItHome.xaml.vb`* veya *`ExpenseItHome.xaml.cs`*.</span><span class="sxs-lookup"><span data-stu-id="cda96-252">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

4. <span data-ttu-id="cda96-253">Aşağıdaki kodu ekleyin `ExpenseItHome` sınıfı bir düğme eklemek için tıklama olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="cda96-253">Add the following code to the `ExpenseItHome` class to add a button click event handler.</span></span> <span data-ttu-id="cda96-254">Olay işleyicisi açılır **ExpenseReportPage** sayfası.</span><span class="sxs-lookup"><span data-stu-id="cda96-254">The event handler opens the **ExpenseReportPage** page.</span></span>

    [!code-csharp[ExpenseIt#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a><span data-ttu-id="cda96-255">ExpenseReportPage için kullanıcı Arabirimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="cda96-255">Create the UI for ExpenseReportPage</span></span>

<span data-ttu-id="cda96-256">*ExpenseReportPage.xaml* seçili kişi için harcama raporlarını görüntüler **`ExpenseItHome`** sayfası.</span><span class="sxs-lookup"><span data-stu-id="cda96-256">*ExpenseReportPage.xaml* displays the expense report for the person that's selected on the **`ExpenseItHome`** page.</span></span> <span data-ttu-id="cda96-257">Bu bölümde, kullanıcı Arabiriminde oluşturacaksınız **ExpenseReportPage**.</span><span class="sxs-lookup"><span data-stu-id="cda96-257">In this section, you'll create the UI for **ExpenseReportPage**.</span></span> <span data-ttu-id="cda96-258">Ayrıca, arka plan ekleyebilir ve çeşitli kullanıcı Arabirimi öğeleri için renk dolgu.</span><span class="sxs-lookup"><span data-stu-id="cda96-258">You'll also add background and fill colors to the various UI elements.</span></span>

1. <span data-ttu-id="cda96-259">Açık *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="cda96-259">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="cda96-260">Aşağıdaki XAML arasında ekleme <xref:System.Windows.Controls.Grid> etiketler:</span><span class="sxs-lookup"><span data-stu-id="cda96-260">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags:</span></span>

    [!code-xaml[ExpenseIt#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    <span data-ttu-id="cda96-261">Bu kullanıcı arabirimini benzer *`ExpenseItHome.xaml`* rapor verilerini görüntülenen dışında bir <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="cda96-261">This UI is similar to *`ExpenseItHome.xaml`*, except the report data is displayed in a <xref:System.Windows.Controls.DataGrid>.</span></span>

3. <span data-ttu-id="cda96-262">Derleme ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cda96-262">Build and run the application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="cda96-263">Bir hata alırsanız <xref:System.Windows.Controls.DataGrid> bulunamadı veya mevcut değilse, projeniz .NET Framework 4 veya sonraki sürümlerini hedefleyen emin olun.</span><span class="sxs-lookup"><span data-stu-id="cda96-263">If you get an error that the <xref:System.Windows.Controls.DataGrid> was not found or does not exist, make sure that your project targets the .NET Framework 4 or later.</span></span> <span data-ttu-id="cda96-264">Daha fazla bilgi için [nasıl yapılır: .NET Framework sürümü hedefleme](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span><span class="sxs-lookup"><span data-stu-id="cda96-264">For more information, see [How to: Target a Version of the .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span></span>

4. <span data-ttu-id="cda96-265">Seçin **görünümü** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="cda96-265">Select the **View** button.</span></span>

    <span data-ttu-id="cda96-266">Harcama Raporu sayfası görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="cda96-266">The expense report page appears.</span></span> <span data-ttu-id="cda96-267">Ayrıca geri gezinme düğmesi etkinleştirilir dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="cda96-267">Also notice that the back navigation button is enabled.</span></span>

<span data-ttu-id="cda96-268">Eklenen kullanıcı Arabirimi öğeleri aşağıdaki çizimde *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="cda96-268">The following illustration shows the UI elements added to *ExpenseReportPage.xaml*.</span></span>

![ExpenseIt örnek ekran görüntüsü](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure4.png)

## <a name="style-controls"></a><span data-ttu-id="cda96-270">Stil denetimleri</span><span class="sxs-lookup"><span data-stu-id="cda96-270">Style controls</span></span>

<span data-ttu-id="cda96-271">Çeşitli öğelerin görünümünü genellikle bir kullanıcı arabiriminde aynı türdeki tüm öğeler için aynıdır.</span><span class="sxs-lookup"><span data-stu-id="cda96-271">The appearance of various elements is often the same for all elements of the same type in a UI.</span></span> <span data-ttu-id="cda96-272">Kullanıcı Arabirimi kullanan [stilleri](../../../../docs/framework/wpf/controls/styling-and-templating.md) görünümleri arasında birden çok öğe yeniden kullanılabilir hale getirmek için.</span><span class="sxs-lookup"><span data-stu-id="cda96-272">UI uses [styles](../../../../docs/framework/wpf/controls/styling-and-templating.md) to make appearances reusable across multiple elements.</span></span> <span data-ttu-id="cda96-273">Yeniden kullanılırlığı XAML oluşturulmasını ve yönetimini basitleştirmeye yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="cda96-273">The reusability of styles helps to simplify XAML creation and management.</span></span> <span data-ttu-id="cda96-274">Bu bölümde, stiller, önceki adımlarda tanımlanan öğe başına özniteliklerini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="cda96-274">This section replaces the per-element attributes that were defined in previous steps with styles.</span></span>

1. <span data-ttu-id="cda96-275">Açık *Application.xaml* veya *App.xaml*.</span><span class="sxs-lookup"><span data-stu-id="cda96-275">Open *Application.xaml* or *App.xaml*.</span></span>

2. <span data-ttu-id="cda96-276">Aşağıdaki XAML arasında ekleme <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> etiketler:</span><span class="sxs-lookup"><span data-stu-id="cda96-276">Add the following XAML between the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tags:</span></span>

    [!code-xaml[ExpenseIt#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    <span data-ttu-id="cda96-277">Bu XAML aşağıdaki stilleri ekler:</span><span class="sxs-lookup"><span data-stu-id="cda96-277">This XAML adds the following styles:</span></span>

    - <span data-ttu-id="cda96-278">`headerTextStyle`: Sayfa başlığı biçimine <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="cda96-278">`headerTextStyle`: To format the page title <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="cda96-279">`labelStyle`: Biçimine <xref:System.Windows.Controls.Label> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="cda96-279">`labelStyle`: To format the <xref:System.Windows.Controls.Label> controls.</span></span>

    - <span data-ttu-id="cda96-280">`columnHeaderStyle`: Biçimine <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span><span class="sxs-lookup"><span data-stu-id="cda96-280">`columnHeaderStyle`: To format the <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span></span>

    - <span data-ttu-id="cda96-281">`listHeaderStyle`: List üstbilgisi biçimine <xref:System.Windows.Controls.Border> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="cda96-281">`listHeaderStyle`: To format the list header <xref:System.Windows.Controls.Border> controls.</span></span>

    - <span data-ttu-id="cda96-282">`listHeaderTextStyle`: List üstbilgisi biçimine <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="cda96-282">`listHeaderTextStyle`: To format the list header <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="cda96-283">`buttonStyle`: Biçimine <xref:System.Windows.Controls.Button> üzerinde `ExpenseItHome.xaml`.</span><span class="sxs-lookup"><span data-stu-id="cda96-283">`buttonStyle`: To format the <xref:System.Windows.Controls.Button> on `ExpenseItHome.xaml`.</span></span>

    <span data-ttu-id="cda96-284">Stilleri kaynakları ve alt olduğunu fark <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> özellik öğesi.</span><span class="sxs-lookup"><span data-stu-id="cda96-284">Notice that the styles are resources and children of the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> property element.</span></span> <span data-ttu-id="cda96-285">Bu konumda, stilleri bir uygulamadaki tüm öğelere uygulanır.</span><span class="sxs-lookup"><span data-stu-id="cda96-285">In this location, the styles are applied to all the elements in an application.</span></span> <span data-ttu-id="cda96-286">Bir .NET Framework uygulamasında kaynakları kullanma örneği için bkz: [kullanım uygulama kaynaklarını](../../../../docs/framework/wpf/advanced/how-to-use-application-resources.md).</span><span class="sxs-lookup"><span data-stu-id="cda96-286">For an example of using resources in a .NET Framework application, see [Use Application Resources](../../../../docs/framework/wpf/advanced/how-to-use-application-resources.md).</span></span>

3. <span data-ttu-id="cda96-287">Açık *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="cda96-287">Open *`ExpenseItHome.xaml`*.</span></span>

4. <span data-ttu-id="cda96-288">Arasındaki her şeyi değiştirin <xref:System.Windows.Controls.Grid> aşağıdaki XAML ile öğeleri:</span><span class="sxs-lookup"><span data-stu-id="cda96-288">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    <span data-ttu-id="cda96-289">Gibi özellikler <xref:System.Windows.VerticalAlignment> ve <xref:System.Windows.Media.FontFamily> her denetimin görünümünü tanımlamak kaldırılır ve stilleri uygulayarak değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="cda96-289">The properties such as <xref:System.Windows.VerticalAlignment> and <xref:System.Windows.Media.FontFamily> that define the look of each control are removed and replaced by applying the styles.</span></span> <span data-ttu-id="cda96-290">Örneğin, `headerTextStyle` harcama raporu görünümü"için" uygulanan <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="cda96-290">For example, the `headerTextStyle` is applied to the "View Expense Report" <xref:System.Windows.Controls.Label>.</span></span>

5. <span data-ttu-id="cda96-291">Açık *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="cda96-291">Open *ExpenseReportPage.xaml*.</span></span>

6. <span data-ttu-id="cda96-292">Arasındaki her şeyi değiştirin <xref:System.Windows.Controls.Grid> aşağıdaki XAML ile öğeleri:</span><span class="sxs-lookup"><span data-stu-id="cda96-292">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    <span data-ttu-id="cda96-293">Bu stiller ekler <xref:System.Windows.Controls.Label> ve <xref:System.Windows.Controls.Border> öğeleri.</span><span class="sxs-lookup"><span data-stu-id="cda96-293">This adds styles to the <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Border> elements.</span></span>

## <a name="bind-data-to-a-control"></a><span data-ttu-id="cda96-294">Veriyi denetime bağlama</span><span class="sxs-lookup"><span data-stu-id="cda96-294">Bind data to a control</span></span>

<span data-ttu-id="cda96-295">Bu bölümde, çeşitli denetimlere bağlı XML verileri oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="cda96-295">In this section, you'll create the XML data that is bound to various controls.</span></span>

1. <span data-ttu-id="cda96-296">Açık *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="cda96-296">Open *`ExpenseItHome.xaml`*.</span></span>

2. <span data-ttu-id="cda96-297">Açılış <xref:System.Windows.Controls.Grid> öğesi oluşturmak için aşağıdaki XAML ekleme bir <xref:System.Windows.Data.XmlDataProvider> her kişi için veri içeren:</span><span class="sxs-lookup"><span data-stu-id="cda96-297">After the opening <xref:System.Windows.Controls.Grid> element, add the following XAML to create an <xref:System.Windows.Data.XmlDataProvider> that contains the data for each person:</span></span>

    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]
    [!code-xaml[ExpenseIt#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#23)]
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]

    <span data-ttu-id="cda96-298">Veri olarak oluşturulan bir <xref:System.Windows.Controls.Grid> kaynak.</span><span class="sxs-lookup"><span data-stu-id="cda96-298">The data is created as a <xref:System.Windows.Controls.Grid> resource.</span></span> <span data-ttu-id="cda96-299">Normalde bu dosya olarak yüklenir, ancak kolaylık olması için satır içi veriler eklenir.</span><span class="sxs-lookup"><span data-stu-id="cda96-299">Normally this would be loaded as a file, but for simplicity the data is added inline.</span></span>

3. <span data-ttu-id="cda96-300">İçinde `<Grid.Resources>` öğesi, aşağıdaki <xref:System.Windows.DataTemplate>, içinde verilerin nasıl görüntüleneceğini tanımlar <xref:System.Windows.Controls.ListBox>:</span><span class="sxs-lookup"><span data-stu-id="cda96-300">Within the `<Grid.Resources>` element, add the following <xref:System.Windows.DataTemplate>, which defines how to display the data in the <xref:System.Windows.Controls.ListBox>:</span></span>

    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]
    [!code-xaml[ExpenseIt#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#24)]
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]

    <span data-ttu-id="cda96-301">Veri şablonları hakkında daha fazla bilgi için bkz. [veri şablonu oluşturmaya genel bakış](../../../../docs/framework/wpf/data/data-templating-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cda96-301">For more information about data templates, see [Data templating overview](../../../../docs/framework/wpf/data/data-templating-overview.md).</span></span>

4. <span data-ttu-id="cda96-302">Varolan <xref:System.Windows.Controls.ListBox> aşağıdaki XAML ile:</span><span class="sxs-lookup"><span data-stu-id="cda96-302">Replace the existing <xref:System.Windows.Controls.ListBox> with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#25](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    <span data-ttu-id="cda96-303">Bu XAML bağlar <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliği <xref:System.Windows.Controls.ListBox> veri kaynağı ve veri şablonu olarak geçerli <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span><span class="sxs-lookup"><span data-stu-id="cda96-303">This XAML binds the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to the data source and applies the data template as the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span></span>

## <a name="connect-data-to-controls"></a><span data-ttu-id="cda96-304">Denetimlere veri bağlama</span><span class="sxs-lookup"><span data-stu-id="cda96-304">Connect data to controls</span></span>

<span data-ttu-id="cda96-305">Ardından, seçili adını almak için kod ekleyeceksiniz **`ExpenseItHome`** sayfasında ve oluşturucusuna iletmektir **ExpenseReportPage**.</span><span class="sxs-lookup"><span data-stu-id="cda96-305">Next, you'll add code to retrieve the name that's selected on the **`ExpenseItHome`** page and pass it to the constructor of **ExpenseReportPage**.</span></span> <span data-ttu-id="cda96-306">**ExpenseReportPage** denetimlerin ne tanımlanır geçirilen öğe ile veri bağlamını ayarlar içinde *ExpenseReportPage.xaml* bağlayın.</span><span class="sxs-lookup"><span data-stu-id="cda96-306">**ExpenseReportPage** sets its data context with the passed item, which is what the controls defined in *ExpenseReportPage.xaml* bind to.</span></span>

1. <span data-ttu-id="cda96-307">Açık *ExpenseReportPage.xaml.vb* veya *ExpenseReportPage.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="cda96-307">Open *ExpenseReportPage.xaml.vb* or *ExpenseReportPage.xaml.cs*.</span></span>

2. <span data-ttu-id="cda96-308">Seçilen kişiyi harcama raporu verilerini geçirebilirsiniz. Bu nedenle bir nesne alan bir oluşturucu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cda96-308">Add a constructor that takes an object so you can pass the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#26](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. <span data-ttu-id="cda96-309">Açık *`ExpenseItHome.xaml.vb`* veya *`ExpenseItHome.xaml.cs`*.</span><span class="sxs-lookup"><span data-stu-id="cda96-309">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

4. <span data-ttu-id="cda96-310">Değişiklik <xref:System.Windows.Controls.Primitives.ButtonBase.Click> seçilen kişiyi harcama raporu verilerini geçirme yeni oluşturucuyu çağırmak için olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="cda96-310">Change the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to call the new constructor passing the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#27](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a><span data-ttu-id="cda96-311">Veri şablonları ile stil verileri</span><span class="sxs-lookup"><span data-stu-id="cda96-311">Style data with data templates</span></span>

<span data-ttu-id="cda96-312">Bu bölümde, veri şablonları kullanarak verilere bağlı listeler her öğe için kullanıcı Arabirimi güncelleştireceksiniz.</span><span class="sxs-lookup"><span data-stu-id="cda96-312">In this section, you'll update the UI for each item in the data-bound lists by using data templates.</span></span>

1. <span data-ttu-id="cda96-313">Açık *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="cda96-313">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="cda96-314">"Name" ve "Departman" içeriğini bağlama <xref:System.Windows.Controls.Label> uygun veri öğelerine kaynak özelliği.</span><span class="sxs-lookup"><span data-stu-id="cda96-314">Bind the content of the "Name" and "Department" <xref:System.Windows.Controls.Label> elements to the appropriate data source property.</span></span> <span data-ttu-id="cda96-315">Veri bağlama hakkında daha fazla bilgi için bkz. [veri bağlamaya genel bakış](../../../../docs/framework/wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cda96-315">For more information about data binding, see [Data binding overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>

    [!code-xaml[ExpenseIt#31](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. <span data-ttu-id="cda96-316">Açılış <xref:System.Windows.Controls.Grid> öğesi, harcama raporu verilerini görüntülemek nasıl tanımlamak aşağıdaki veri şablonları ekleyin:</span><span class="sxs-lookup"><span data-stu-id="cda96-316">After the opening <xref:System.Windows.Controls.Grid> element, add the following data templates, which define how to display the expense report data:</span></span>

    [!code-xaml[ExpenseIt#30](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. <span data-ttu-id="cda96-317">Değiştirin <xref:System.Windows.Controls.DataGridTextColumn> öğelerle <xref:System.Windows.Controls.DataGridTemplateColumn> altında <xref:System.Windows.Controls.DataGrid> öğesi ve şablonlar uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cda96-317">Replace the <xref:System.Windows.Controls.DataGridTextColumn> elements with <xref:System.Windows.Controls.DataGridTemplateColumn> under the <xref:System.Windows.Controls.DataGrid> element and apply the templates to them.</span></span>

    [!code-xaml[ExpenseIt#32](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. <span data-ttu-id="cda96-318">Derleme ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cda96-318">Build and run the application.</span></span>

6. <span data-ttu-id="cda96-319">Bir kişi seçin ve ardından **görünümü** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="cda96-319">Select a person and then select the **View** button.</span></span>

<span data-ttu-id="cda96-320">Her iki sayfaları aşağıdaki resimde gösterilmektedir `ExpenseIt` uygulama denetimleri, düzeni, stiller, veri bağlama ve uygulanan veri şablonları:</span><span class="sxs-lookup"><span data-stu-id="cda96-320">The following illustration shows both pages of the `ExpenseIt` application with controls, layout, styles, data binding, and data templates applied:</span></span>

![ExpenseIt örnek ekran görüntüleri](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure5.png)

> [!NOTE]
> <span data-ttu-id="cda96-322">Bu örnek, belirli bir WPF özelliğini gösterir ve güvenlik, yerelleştirme ve erişilebilirlik gibi şeyler için tüm en iyi uygulamaları izleyin değil.</span><span class="sxs-lookup"><span data-stu-id="cda96-322">This sample demonstrates a specific feature of WPF and doesn't follow all best practices for things like security, localization, and accessibility.</span></span> <span data-ttu-id="cda96-323">WPF ve .NET Framework uygulama geliştirme en iyi yöntemler ilişkin kapsamlı bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="cda96-323">For comprehensive coverage of WPF and the .NET Framework application development best practices, see the following topics:</span></span>
>
> - [<span data-ttu-id="cda96-324">Erişilebilirlik</span><span class="sxs-lookup"><span data-stu-id="cda96-324">Accessibility</span></span>](../../../../docs/framework/ui-automation/accessibility-best-practices.md)
>
> - [<span data-ttu-id="cda96-325">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="cda96-325">Security</span></span>](../../../../docs/framework/wpf/security-wpf.md)
>
> - [<span data-ttu-id="cda96-326">WPF Genelleştirme ve yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="cda96-326">WPF globalization and localization</span></span>](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)
>
> - [<span data-ttu-id="cda96-327">WPF Performans</span><span class="sxs-lookup"><span data-stu-id="cda96-327">WPF performance</span></span>](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a><span data-ttu-id="cda96-328">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="cda96-328">Next steps</span></span>

<span data-ttu-id="cda96-329">Bu izlenecek yolda çeşitli teknikler Windows Presentation Foundation (WPF) kullanarak bir kullanıcı Arabirimi oluşturma hakkında bilgi edindiniz.</span><span class="sxs-lookup"><span data-stu-id="cda96-329">In this walkthrough you learned a number of techniques for creating a UI using Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="cda96-330">Artık verilere bağlı .NET Framework uygulamasının yapı taşları ilgili temel bilgilere sahipsiniz.</span><span class="sxs-lookup"><span data-stu-id="cda96-330">You should now have a basic understanding of the building blocks of a data-bound, .NET Framework application.</span></span> <span data-ttu-id="cda96-331">WPF mimarisi ve programlama modelleri hakkında daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="cda96-331">For more information about the WPF architecture and programming models, see the following topics:</span></span>

- [<span data-ttu-id="cda96-332">WPF mimarisi</span><span class="sxs-lookup"><span data-stu-id="cda96-332">WPF architecture</span></span>](../../../../docs/framework/wpf/advanced/wpf-architecture.md)
- [<span data-ttu-id="cda96-333">XAML genel bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="cda96-333">XAML overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="cda96-334">Bağımlılık özelliklerine genel bakış</span><span class="sxs-lookup"><span data-stu-id="cda96-334">Dependency properties overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
- [<span data-ttu-id="cda96-335">Düzen</span><span class="sxs-lookup"><span data-stu-id="cda96-335">Layout</span></span>](../../../../docs/framework/wpf/advanced/layout.md)

<span data-ttu-id="cda96-336">Uygulamaları oluşturma hakkında daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="cda96-336">For more information about creating applications, see the following topics:</span></span>

- [<span data-ttu-id="cda96-337">Uygulama geliştirme</span><span class="sxs-lookup"><span data-stu-id="cda96-337">Application development</span></span>](../../../../docs/framework/wpf/app-development/index.md)
- [<span data-ttu-id="cda96-338">Denetimler</span><span class="sxs-lookup"><span data-stu-id="cda96-338">Controls</span></span>](../../../../docs/framework/wpf/controls/index.md)
- [<span data-ttu-id="cda96-339">Veri bağlamaya genel bakış</span><span class="sxs-lookup"><span data-stu-id="cda96-339">Data binding overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [<span data-ttu-id="cda96-340">Grafikler ve multimedya</span><span class="sxs-lookup"><span data-stu-id="cda96-340">Graphics and multimedia</span></span>](../../../../docs/framework/wpf/graphics-multimedia/index.md)
- [<span data-ttu-id="cda96-341">WPF'deki Belgeler</span><span class="sxs-lookup"><span data-stu-id="cda96-341">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)

## <a name="see-also"></a><span data-ttu-id="cda96-342">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cda96-342">See also</span></span>

- [<span data-ttu-id="cda96-343">Panellere genel bakış</span><span class="sxs-lookup"><span data-stu-id="cda96-343">Panels overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
- [<span data-ttu-id="cda96-344">Veri şablonu oluşturmaya genel bakış</span><span class="sxs-lookup"><span data-stu-id="cda96-344">Data templating overview</span></span>](../../../../docs/framework/wpf/data/data-templating-overview.md)
- [<span data-ttu-id="cda96-345">Bir WPF uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="cda96-345">Build a WPF application</span></span>](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)
- [<span data-ttu-id="cda96-346">Stilleri ve şablonları</span><span class="sxs-lookup"><span data-stu-id="cda96-346">Styles and templates</span></span>](../../../../docs/framework/wpf/controls/styles-and-templates.md)
