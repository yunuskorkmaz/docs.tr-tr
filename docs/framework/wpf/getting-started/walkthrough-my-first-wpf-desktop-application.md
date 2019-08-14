---
title: Visual Studio 'da WPF uygulaması oluşturma
ms.date: 03/20/2019
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
ms.openlocfilehash: 9d5b5b8a479efd3918dc23616aa331cc07a901ac
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972179"
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a><span data-ttu-id="bec5c-102">İzlenecek yol: İlk WPF masaüstü uygulamam</span><span class="sxs-lookup"><span data-stu-id="bec5c-102">Walkthrough: My first WPF desktop application</span></span>

<span data-ttu-id="bec5c-103">Bu makalede, çoğu WPF uygulaması için ortak olan öğeleri içeren bir Windows Presentation Foundation (WPF) masaüstü uygulaması geliştirme gösterilmektedir: Extensible Application Markup Language (XAML) işaretleme, arka plan kod, uygulama tanımları, denetimler, düzen, veri bağlama ve stiller.</span><span class="sxs-lookup"><span data-stu-id="bec5c-103">This article shows you how to develop a Windows Presentation Foundation (WPF) desktop application that includes the elements that are common to most WPF applications: Extensible Application Markup Language (XAML) markup, code-behind, application definitions, controls, layout, data binding, and styles.</span></span> <span data-ttu-id="bec5c-104">Uygulamayı geliştirmek için Visual Studio 'Yu kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="bec5c-104">To develop the application, you'll use Visual Studio.</span></span> 

<span data-ttu-id="bec5c-105">Bu izlenecek yol aşağıdaki adımları içerir:</span><span class="sxs-lookup"><span data-stu-id="bec5c-105">This walkthrough includes the following steps:</span></span>

- <span data-ttu-id="bec5c-106">Uygulamanın kullanıcı arabiriminin (UI) görünümünü tasarlamak için XAML kullanın.</span><span class="sxs-lookup"><span data-stu-id="bec5c-106">Use XAML to design the appearance of the application's user interface (UI).</span></span>

- <span data-ttu-id="bec5c-107">Uygulamanın davranışını derlemek için kod yazın.</span><span class="sxs-lookup"><span data-stu-id="bec5c-107">Write code to build the application's behavior.</span></span>

- <span data-ttu-id="bec5c-108">Uygulamayı yönetmek için bir uygulama tanımı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bec5c-108">Create an application definition to manage the application.</span></span>

- <span data-ttu-id="bec5c-109">Uygulama kullanıcı arabirimini oluşturmak için denetimler ekleyin ve düzeni oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bec5c-109">Add controls and create the layout to compose the application UI.</span></span>

- <span data-ttu-id="bec5c-110">Uygulamanın kullanıcı arabiriminde tutarlı bir görünüm için stiller oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bec5c-110">Create styles for a consistent appearance throughout the application's UI.</span></span>

- <span data-ttu-id="bec5c-111">Kullanıcı arabirimini verileri veri kaynağından doldurmak ve verileri ve Kullanıcı arabirimini eşitlenmiş halde tutmak için veri ARABIRIMINE bağlayın.</span><span class="sxs-lookup"><span data-stu-id="bec5c-111">Bind the UI to data, both to populate the UI from data and to keep the data and UI synchronized.</span></span>

<span data-ttu-id="bec5c-112">İzlenecek yolun sonuna kadar, kullanıcıların seçili kişilere ait gider raporlarını görüntülemesine olanak sağlayan tek başına bir Windows uygulaması oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="bec5c-112">By the end of the walkthrough, you'll have built a standalone Windows application that allows users to view expense reports for selected people.</span></span> <span data-ttu-id="bec5c-113">Uygulama, tarayıcı stili bir pencerede barındırılan çeşitli WPF sayfalarından oluşur.</span><span class="sxs-lookup"><span data-stu-id="bec5c-113">The application is composed of several WPF pages that are hosted in a browser-style window.</span></span>

> [!TIP]
> <span data-ttu-id="bec5c-114">Bu yönergeyi oluşturmak için kullanılan örnek kod hem Visual Basic C# hem de [WPF uygulaması örnek kodu](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp)için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bec5c-114">The sample code that is used to build this walkthrough is available for both Visual Basic and C# at [Walkthrough WPF App Sample Code](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span></span>
>
> <span data-ttu-id="bec5c-115">Bu makalenin sağ üst tarafındaki açılan eklentiyi kullanarak, C# **\< />** ve Visual Basic arasında örnek kodun kod dilini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bec5c-115">You can toggle the code language of the sample code between C# and Visual Basic by using the **\</>** drop-down on the upper right side of this article.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bec5c-116">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="bec5c-116">Prerequisites</span></span>

- <span data-ttu-id="bec5c-117">Visual Studio 2017 veya üzeri (Bu makalede Visual Studio 2019 kullanılır)</span><span class="sxs-lookup"><span data-stu-id="bec5c-117">Visual Studio 2017 or later (this article uses Visual Studio 2019)</span></span>

   <span data-ttu-id="bec5c-118">Visual Studio 'nun en son sürümünü yükleme hakkında daha fazla bilgi için bkz. [Visual Studio 'Yu yükleme](/visualstudio/install/install-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="bec5c-118">For more information about installing the latest version of Visual Studio, see [Install Visual Studio](/visualstudio/install/install-visual-studio).</span></span>

## <a name="create-the-application-project"></a><span data-ttu-id="bec5c-119">Uygulama projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="bec5c-119">Create the application project</span></span>

<span data-ttu-id="bec5c-120">İlk adım, uygulama tanımı, iki sayfa ve bir görüntü içeren uygulama altyapısını oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="bec5c-120">The first step is to create the application infrastructure, which includes an application definition, two pages, and an image.</span></span>

1. <span data-ttu-id="bec5c-121">Visual Basic veya görsel C# adında **`ExpenseIt`** yeni bir WPF uygulama projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="bec5c-121">Create a new WPF Application project in Visual Basic or Visual C# named **`ExpenseIt`**:</span></span>

   1. <span data-ttu-id="bec5c-122">Visual Studio 'Yu açın ve **Başlarken** menüsünde **Yeni proje oluştur** ' u seçin.</span><span class="sxs-lookup"><span data-stu-id="bec5c-122">Open Visual Studio and select **Create a new project** under the **Get started** menu.</span></span>

      <span data-ttu-id="bec5c-123">**Yeni proje oluştur** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="bec5c-123">The **Create a new project** dialog opens.</span></span>

   2. <span data-ttu-id="bec5c-124">**Dil** açılan listesinde ya da **C#** **Visual Basic**seçin.</span><span class="sxs-lookup"><span data-stu-id="bec5c-124">In the **Language** dropdown, select either **C#** or **Visual Basic**.</span></span>
      
   3. <span data-ttu-id="bec5c-125">**WPF uygulaması (.NET Framework)** şablonunu seçin ve ardından **İleri**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="bec5c-125">Select the **WPF App (.NET Framework)** template and then select **Next**.</span></span> 
     
      ![Yeni proje iletişim kutusu oluştur](./media/walkthrough-my-first-wpf-desktop-application/create-new-project-dialog.png)
    
      <span data-ttu-id="bec5c-127">**Yeni projenizi yapılandırma** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="bec5c-127">The **Configure your new project** dialog opens.</span></span>

   4. <span data-ttu-id="bec5c-128">Proje adını **`ExpenseIt`** girip **Oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="bec5c-128">Enter the project name **`ExpenseIt`** and then select **Create**.</span></span>

      ![Yeni bir proje iletişim kutusu Yapılandır](./media/walkthrough-my-first-wpf-desktop-application/configure-new-project-dialog.png)

      <span data-ttu-id="bec5c-130">Visual Studio projeyi oluşturur ve **MainWindow. xaml**adlı varsayılan uygulama penceresi için tasarımcıyı açar.</span><span class="sxs-lookup"><span data-stu-id="bec5c-130">Visual Studio creates the project and opens the designer for the default application window named **MainWindow.xaml**.</span></span>

2. <span data-ttu-id="bec5c-131">*Application. xaml* (Visual Basic) veya *app. xaml* (C#) öğesini açın.</span><span class="sxs-lookup"><span data-stu-id="bec5c-131">Open *Application.xaml* (Visual Basic) or *App.xaml* (C#).</span></span>

    <span data-ttu-id="bec5c-132">Bu XAML dosyası bir WPF uygulamasını ve uygulama kaynaklarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bec5c-132">This XAML file defines a WPF application and any application resources.</span></span> <span data-ttu-id="bec5c-133">Bu dosyayı, Kullanıcı arabirimini belirtmek için de kullanabilirsiniz. Bu durumda *MainWindow. xaml*, uygulamanın başladığı zaman otomatik olarak gösterilir.</span><span class="sxs-lookup"><span data-stu-id="bec5c-133">You also use this file to specify the UI, in this case *MainWindow.xaml*, that automatically shows when the application starts.</span></span>

    <span data-ttu-id="bec5c-134">XAML 'niz Visual Basic aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="bec5c-134">Your XAML should look like the following in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    <span data-ttu-id="bec5c-135">Ve aşağıdaki gibi C#:</span><span class="sxs-lookup"><span data-stu-id="bec5c-135">And like the following in C#:</span></span>

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. <span data-ttu-id="bec5c-136">*MainWindow. xaml*' i açın.</span><span class="sxs-lookup"><span data-stu-id="bec5c-136">Open *MainWindow.xaml*.</span></span>

    <span data-ttu-id="bec5c-137">Bu XAML dosyası, uygulamanızın ana penceresidir ve sayfalarda oluşturulan içeriği görüntüler.</span><span class="sxs-lookup"><span data-stu-id="bec5c-137">This XAML file is the main window of your application and displays content created in pages.</span></span> <span data-ttu-id="bec5c-138"><xref:System.Windows.Window> Sınıfı, bir pencerenin başlık, boyut veya simgesi gibi özelliklerini tanımlar ve kapatma ya da gizleme gibi olayları işler.</span><span class="sxs-lookup"><span data-stu-id="bec5c-138">The <xref:System.Windows.Window> class defines the properties of a window, such as its title, size, or icon, and handles events, such as closing or hiding.</span></span>

4. <span data-ttu-id="bec5c-139">Aşağıdaki XAML 'de gösterildiği gibi <xref:System.Windows.Navigation.NavigationWindow>, öğesiniolarakdeğiştirin:<xref:System.Windows.Window></span><span class="sxs-lookup"><span data-stu-id="bec5c-139">Change the <xref:System.Windows.Window> element to a <xref:System.Windows.Navigation.NavigationWindow>, as shown in the following XAML:</span></span>

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   <span data-ttu-id="bec5c-140">Bu uygulama, kullanıcı girişine bağlı olarak farklı içeriğe gider.</span><span class="sxs-lookup"><span data-stu-id="bec5c-140">This app navigates to different content depending on the user input.</span></span> <span data-ttu-id="bec5c-141">Bunun nedeni, Main <xref:System.Windows.Window> 'in bir <xref:System.Windows.Navigation.NavigationWindow>olarak değiştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="bec5c-141">This is why the main <xref:System.Windows.Window> needs to be changed to a <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="bec5c-142"><xref:System.Windows.Navigation.NavigationWindow>tüm özelliklerini <xref:System.Windows.Window>devralır.</span><span class="sxs-lookup"><span data-stu-id="bec5c-142"><xref:System.Windows.Navigation.NavigationWindow> inherits all the properties of <xref:System.Windows.Window>.</span></span> <span data-ttu-id="bec5c-143">XAML dosyasındaki <xref:System.Windows.Navigation.NavigationWindow> öğesi, sınıfının bir örneğini oluşturur. <xref:System.Windows.Navigation.NavigationWindow></span><span class="sxs-lookup"><span data-stu-id="bec5c-143">The <xref:System.Windows.Navigation.NavigationWindow> element in the XAML file creates an instance of the <xref:System.Windows.Navigation.NavigationWindow> class.</span></span> <span data-ttu-id="bec5c-144">Daha fazla bilgi için bkz. [gezintiye genel bakış](../app-development/navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bec5c-144">For more information, see [Navigation overview](../app-development/navigation-overview.md).</span></span>

5. <span data-ttu-id="bec5c-145"><xref:System.Windows.Controls.Grid> Öğeleri Etiketler<xref:System.Windows.Navigation.NavigationWindow> arasından kaldırın.</span><span class="sxs-lookup"><span data-stu-id="bec5c-145">Remove the <xref:System.Windows.Controls.Grid> elements from between the <xref:System.Windows.Navigation.NavigationWindow> tags.</span></span>

6. <span data-ttu-id="bec5c-146"><xref:System.Windows.Navigation.NavigationWindow> Öğesi için XAML kodunda aşağıdaki özellikleri değiştirin:</span><span class="sxs-lookup"><span data-stu-id="bec5c-146">Change the following properties in the XAML code for the <xref:System.Windows.Navigation.NavigationWindow> element:</span></span>

    - <span data-ttu-id="bec5c-147"><xref:System.Windows.Window.Title%2A> Özelliği"`ExpenseIt`" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bec5c-147">Set the <xref:System.Windows.Window.Title%2A> property to "`ExpenseIt`".</span></span>

    - <span data-ttu-id="bec5c-148"><xref:System.Windows.FrameworkElement.Height%2A> Özelliği 350 piksel olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bec5c-148">Set the <xref:System.Windows.FrameworkElement.Height%2A> property to 350 pixels.</span></span>

    - <span data-ttu-id="bec5c-149"><xref:System.Windows.FrameworkElement.Width%2A> Özelliği 500 piksel olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bec5c-149">Set the <xref:System.Windows.FrameworkElement.Width%2A> property to 500 pixels.</span></span>

    <span data-ttu-id="bec5c-150">Visual Basic için XAML 'niz aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="bec5c-150">Your XAML should look like the following for Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    <span data-ttu-id="bec5c-151">Ve şunun için C#aşağıdakiler gibi:</span><span class="sxs-lookup"><span data-stu-id="bec5c-151">And like the following for C#:</span></span>

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

7. <span data-ttu-id="bec5c-152">*MainWindow. xaml. vb* veya *MainWindow.xaml.cs*öğesini açın.</span><span class="sxs-lookup"><span data-stu-id="bec5c-152">Open *MainWindow.xaml.vb* or *MainWindow.xaml.cs*.</span></span>

    <span data-ttu-id="bec5c-153">Bu dosya, *MainWindow. xaml*içinde belirtilen olayları işlemek için kod içeren bir arka plan kod dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="bec5c-153">This file is a code-behind file that contains code to handle the events declared in *MainWindow.xaml*.</span></span> <span data-ttu-id="bec5c-154">Bu dosya XAML 'de tanımlanan pencere için kısmi bir sınıf içerir.</span><span class="sxs-lookup"><span data-stu-id="bec5c-154">This file contains a partial class for the window defined in XAML.</span></span>

8. <span data-ttu-id="bec5c-155">Kullanıyorsanız C#, ' den `MainWindow` <xref:System.Windows.Navigation.NavigationWindow>türetmek için sınıfını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="bec5c-155">If you're using C#, change the `MainWindow` class to derive from <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="bec5c-156">(Visual Basic, XAML 'de pencereyi değiştirdiğinizde bu otomatik olarak gerçekleşir.) C# Kodunuz şu şekilde görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="bec5c-156">(In Visual Basic, this happens automatically when you change the window in XAML.) Your C# code should now look like this:</span></span>

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/MainWindow.xaml.cs?highlight=21)]

## <a name="add-files-to-the-application"></a><span data-ttu-id="bec5c-157">Uygulamaya dosya ekleme</span><span class="sxs-lookup"><span data-stu-id="bec5c-157">Add files to the application</span></span>

<span data-ttu-id="bec5c-158">Bu bölümde, uygulamaya iki sayfa ve bir görüntü ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="bec5c-158">In this section, you'll add two pages and an image to the application.</span></span>

1. <span data-ttu-id="bec5c-159">Projeye yeni bir sayfa ekleyin ve bunu *`ExpenseItHome.xaml`* adlandırın:</span><span class="sxs-lookup"><span data-stu-id="bec5c-159">Add a new page to the project, and name it *`ExpenseItHome.xaml`*:</span></span>

   1. <span data-ttu-id="bec5c-160">**Çözüm Gezgini**, **`ExpenseIt`** proje düğümüne sağ tıklayın ve**sayfa** **Ekle** > ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="bec5c-160">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="bec5c-161">**Yeni öğe Ekle** Iletişim kutusunda **sayfa (WPF)** şablonu zaten seçilidir.</span><span class="sxs-lookup"><span data-stu-id="bec5c-161">In the **Add New Item** dialog, the **Page (WPF)** template is already selected.</span></span> <span data-ttu-id="bec5c-162">Adı **`ExpenseItHome`** girin ve ardından **Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="bec5c-162">Enter the name **`ExpenseItHome`**, and then select **Add**.</span></span>

    <span data-ttu-id="bec5c-163">Bu sayfa, uygulama başlatıldığında görüntülenen ilk sayfasıdır.</span><span class="sxs-lookup"><span data-stu-id="bec5c-163">This page is the first page that's displayed when the application is launched.</span></span> <span data-ttu-id="bec5c-164">İçin bir gider raporu göstermek üzere içinden seçilecek kişilerin listesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="bec5c-164">It will show a list of people to select from, to show an expense report for.</span></span>

1. <span data-ttu-id="bec5c-165">Öğesini *`ExpenseItHome.xaml`* açın.</span><span class="sxs-lookup"><span data-stu-id="bec5c-165">Open *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="bec5c-166"><xref:System.Windows.Controls.Page.Title%2A> "`ExpenseIt - Home`" Olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bec5c-166">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - Home`".</span></span>

1. <span data-ttu-id="bec5c-167">`DesignHeight` Ve`DesignWidth` öğesi değerlerini 300 piksel olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bec5c-167">Set the `DesignHeight` and `DesignWidth` element values to 300 pixels.</span></span>

    <span data-ttu-id="bec5c-168">XAML artık Visual Basic için aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="bec5c-168">The XAML now appears as follows for Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    <span data-ttu-id="bec5c-169">Ve şunun için C#aşağıdakiler gibi:</span><span class="sxs-lookup"><span data-stu-id="bec5c-169">And like the following for C#:</span></span>

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

1. <span data-ttu-id="bec5c-170">*MainWindow. xaml*' i açın.</span><span class="sxs-lookup"><span data-stu-id="bec5c-170">Open *MainWindow.xaml*.</span></span>

1. <span data-ttu-id="bec5c-171"><xref:System.Windows.Navigation.NavigationWindow> Öğeye bir <xref:System.Windows.Navigation.NavigationWindow.Source%2A> özellik ekleyin ve bunu "`ExpenseItHome.xaml`" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bec5c-171">Add a <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property to the <xref:System.Windows.Navigation.NavigationWindow> element and set it to "`ExpenseItHome.xaml`".</span></span>

    <span data-ttu-id="bec5c-172">Bu, *`ExpenseItHome.xaml`* uygulama başlatıldığında açılan ilk sayfa olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="bec5c-172">This sets *`ExpenseItHome.xaml`* to be the first page opened when the application starts.</span></span> 

    <span data-ttu-id="bec5c-173">Visual Basic örnek XAML:</span><span class="sxs-lookup"><span data-stu-id="bec5c-173">Example XAML in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    <span data-ttu-id="bec5c-174">C# ve:</span><span class="sxs-lookup"><span data-stu-id="bec5c-174">And in C#:</span></span>

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > <span data-ttu-id="bec5c-175">Ayrıca, **Özellikler** penceresinin **çeşitli** kategorisindeki **Source** özelliğini de ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bec5c-175">You can also set the **Source** property in the **Miscellaneous** category of the **Properties** window.</span></span>
   >
   > ![Özellikler penceresi kaynak özelliği](./media/properties-source.png)

1. <span data-ttu-id="bec5c-177">Projeye yeni bir WPF sayfası ekleyin ve bunu *ExpenseReportPage. xaml*olarak adlandırın::</span><span class="sxs-lookup"><span data-stu-id="bec5c-177">Add another new WPF page to the project, and name it *ExpenseReportPage.xaml*::</span></span>

   1. <span data-ttu-id="bec5c-178">**Çözüm Gezgini**, **`ExpenseIt`** proje düğümüne sağ tıklayın ve**sayfa** **Ekle** > ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="bec5c-178">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="bec5c-179">**Yeni öğe Ekle** Iletişim kutusunda **sayfa (WPF)** şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="bec5c-179">In the **Add New Item** dialog, select the **Page (WPF)** template.</span></span> <span data-ttu-id="bec5c-180">**ExpenseReportPage**adını girip **Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="bec5c-180">Enter the name **ExpenseReportPage**, and then select **Add**.</span></span>

    <span data-ttu-id="bec5c-181">Bu sayfa, **`ExpenseItHome`** sayfada seçili olan kişinin gider raporunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="bec5c-181">This page will show the expense report for the person that is selected on the **`ExpenseItHome`** page.</span></span>

1. <span data-ttu-id="bec5c-182">*ExpenseReportPage. xaml*' i açın.</span><span class="sxs-lookup"><span data-stu-id="bec5c-182">Open *ExpenseReportPage.xaml*.</span></span>

1. <span data-ttu-id="bec5c-183"><xref:System.Windows.Controls.Page.Title%2A> "`ExpenseIt - View Expense`" Olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bec5c-183">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - View Expense`".</span></span>

1. <span data-ttu-id="bec5c-184">`DesignHeight` Ve`DesignWidth` öğesi değerlerini 300 piksel olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bec5c-184">Set the `DesignHeight` and `DesignWidth` element values to 300 pixels.</span></span>

    <span data-ttu-id="bec5c-185">*ExpenseReportPage. xaml* artık Visual Basic ' de aşağıdakine benzer:</span><span class="sxs-lookup"><span data-stu-id="bec5c-185">*ExpenseReportPage.xaml* now looks like the following in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    <span data-ttu-id="bec5c-186">Ve aşağıdaki gibi C#:</span><span class="sxs-lookup"><span data-stu-id="bec5c-186">And like the following in C#:</span></span>

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

1. <span data-ttu-id="bec5c-187">*ExpenseItHome. xaml. vb* ve *ExpenseReportPage. xaml. vb*veya *ExpenseItHome.xaml.cs* ve *ExpenseReportPage.xaml.cs*öğesini açın.</span><span class="sxs-lookup"><span data-stu-id="bec5c-187">Open *ExpenseItHome.xaml.vb* and *ExpenseReportPage.xaml.vb*, or *ExpenseItHome.xaml.cs* and *ExpenseReportPage.xaml.cs*.</span></span>

    <span data-ttu-id="bec5c-188">Yeni bir sayfa dosyası oluşturduğunuzda, Visual Studio otomatik olarak *arka plan kod* dosyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bec5c-188">When you create a new Page file, Visual Studio automatically creates its *code-behind* file.</span></span> <span data-ttu-id="bec5c-189">Bu arka plan kod dosyaları, kullanıcı girişine yanıt verme mantığını işler.</span><span class="sxs-lookup"><span data-stu-id="bec5c-189">These code-behind files handle the logic for responding to user input.</span></span>

    <span data-ttu-id="bec5c-190">Kodunuz şunlar **`ExpenseItHome`** gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="bec5c-190">Your code should look like the following for **`ExpenseItHome`**:</span></span>

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]

    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    <span data-ttu-id="bec5c-191">**ExpenseReportPage**için aşağıdakiler gibi:</span><span class="sxs-lookup"><span data-stu-id="bec5c-191">And like the following for **ExpenseReportPage**:</span></span>

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]

    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

1. <span data-ttu-id="bec5c-192">Projeye *filigran. png* adlı bir resim ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bec5c-192">Add an image named *watermark.png* to the project.</span></span> <span data-ttu-id="bec5c-193">Kendi görüntünüzü oluşturabilir, dosyayı örnek koddan kopyalayabilir veya [buradan](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png)edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bec5c-193">You can create your own image, copy the file from the sample code, or get it [here](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png).</span></span>

    1. <span data-ttu-id="bec5c-194">Proje düğümüne sağ tıklayın ve**Varolan öğe** **Ekle** > ' yi seçin veya **SHIFT**+**alt**+**A**'ya basın.</span><span class="sxs-lookup"><span data-stu-id="bec5c-194">Right-click on the project node and select **Add** > **Existing Item**, or press **Shift**+**Alt**+**A**.</span></span>

    2. <span data-ttu-id="bec5c-195">**Varolan öğe Ekle** iletişim kutusunda, dosya filtresini **tüm dosyalar** veya **görüntü dosyaları**olarak ayarlayın, kullanmak istediğiniz görüntü dosyasına gidin ve **Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="bec5c-195">In the **Add Existing Item** dialog, set the file filter to either **All Files** or **Image Files**, browse to the image file you want to use, and then select **Add**.</span></span>

## <a name="build-and-run-the-application"></a><span data-ttu-id="bec5c-196">Uygulamayı derleyin ve çalıştırın</span><span class="sxs-lookup"><span data-stu-id="bec5c-196">Build and run the application</span></span>

1. <span data-ttu-id="bec5c-197">Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın veya **Hata Ayıkla** menüsünden **hata ayıklamayı Başlat** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="bec5c-197">To build and run the application, press **F5** or select **Start Debugging** from the **Debug** menu.</span></span>

    <span data-ttu-id="bec5c-198">Aşağıdaki çizim, <xref:System.Windows.Navigation.NavigationWindow> düğmeleri içeren uygulamayı göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="bec5c-198">The following illustration shows the application with the <xref:System.Windows.Navigation.NavigationWindow> buttons:</span></span>

    ![Uygulamanızı derleyip çalıştırdıktan sonra.](./media/walkthrough-my-first-wpf-desktop-application/build-run-application.png)

2. <span data-ttu-id="bec5c-200">Visual Studio 'ya dönmek için uygulamayı kapatın.</span><span class="sxs-lookup"><span data-stu-id="bec5c-200">Close the application to return to Visual Studio.</span></span>

## <a name="create-the-layout"></a><span data-ttu-id="bec5c-201">Düzen oluşturma</span><span class="sxs-lookup"><span data-stu-id="bec5c-201">Create the layout</span></span>

<span data-ttu-id="bec5c-202">Düzen, Kullanıcı arabirimi öğelerini yerleştirmek için sıralı bir yol sağlar ve ayrıca bir kullanıcı arabirimi yeniden boyutlandırılırken bu öğelerin boyutunu ve konumunu yönetir.</span><span class="sxs-lookup"><span data-stu-id="bec5c-202">Layout provides an ordered way to place UI elements, and also manages the size and position of those elements when a UI is resized.</span></span> <span data-ttu-id="bec5c-203">Genellikle aşağıdaki düzen denetimlerinden birini kullanarak bir düzen oluşturursunuz:</span><span class="sxs-lookup"><span data-stu-id="bec5c-203">You typically create a layout with one of the following layout controls:</span></span>

- <span data-ttu-id="bec5c-204"><xref:System.Windows.Controls.Canvas>-Tuval alanına göreli koordinatları kullanarak alt öğeleri açıkça konumlandırabileceğiniz bir alan tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bec5c-204"><xref:System.Windows.Controls.Canvas> - Defines an area within which you can explicitly position child elements by using coordinates that are relative to the Canvas area.</span></span>
- <span data-ttu-id="bec5c-205"><xref:System.Windows.Controls.DockPanel>-Alt öğeleri yatay veya dikey olarak birbirlerine göre düzenlemek için kullanabileceğiniz bir alan tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bec5c-205"><xref:System.Windows.Controls.DockPanel> - Defines an area where you can arrange child elements either horizontally or vertically, relative to each other.</span></span>
- <span data-ttu-id="bec5c-206"><xref:System.Windows.Controls.Grid>-Sütun ve satırlardan oluşan esnek bir kılavuz alanı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bec5c-206"><xref:System.Windows.Controls.Grid> - Defines a flexible grid area that consists of columns and rows.</span></span>
- <span data-ttu-id="bec5c-207"><xref:System.Windows.Controls.StackPanel>-Alt öğeleri yatay veya dikey olarak yönelimli tek bir satıra yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="bec5c-207"><xref:System.Windows.Controls.StackPanel> - Arranges child elements into a single line that can be oriented horizontally or vertically.</span></span>
- <span data-ttu-id="bec5c-208"><xref:System.Windows.Controls.VirtualizingStackPanel>-İçeriği yatay veya dikey olarak tek bir satırda düzenler ve sanallaştırır.</span><span class="sxs-lookup"><span data-stu-id="bec5c-208"><xref:System.Windows.Controls.VirtualizingStackPanel> - Arranges and virtualizes content on a single line that is oriented either horizontally or vertically.</span></span>
- <span data-ttu-id="bec5c-209"><xref:System.Windows.Controls.WrapPanel>-Alt öğeleri soldan sağa, kapsayan kutunun kenarındaki içerikleri sonraki satıra kadar konumlandırır.</span><span class="sxs-lookup"><span data-stu-id="bec5c-209"><xref:System.Windows.Controls.WrapPanel> - Positions child elements in sequential position from left to right, breaking content to the next line at the edge of the containing box.</span></span> <span data-ttu-id="bec5c-210">Yönlendirme özelliğinin değerine bağlı olarak, sonraki sıralama yukarıdan aşağıya doğru veya sağdan sola doğru bir şekilde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="bec5c-210">Subsequent ordering happens sequentially from top to bottom or from right to left, depending on the value of the Orientation property.</span></span>

<span data-ttu-id="bec5c-211">Bu düzen denetimlerinin her biri, alt öğeleri için belirli bir düzen türünü destekler.</span><span class="sxs-lookup"><span data-stu-id="bec5c-211">Each of these layout controls supports a particular type of layout for its child elements.</span></span> <span data-ttu-id="bec5c-212">`ExpenseIt`sayfalar yeniden boyutlandırılabilir ve her sayfanın diğer öğelerin yanı sıra yatay ve dikey olarak düzenlenmiş öğeleri vardır.</span><span class="sxs-lookup"><span data-stu-id="bec5c-212">`ExpenseIt` pages can be resized, and each page has elements that are arranged horizontally and vertically alongside other elements.</span></span> <span data-ttu-id="bec5c-213">Bu örnekte <xref:System.Windows.Controls.Grid> , uygulama için düzen öğesi olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bec5c-213">In this example, the <xref:System.Windows.Controls.Grid> is used as  layout element for the application.</span></span>

> [!TIP]
> <span data-ttu-id="bec5c-214">Öğeler hakkında <xref:System.Windows.Controls.Panel> daha fazla bilgi için bkz. [panellere genel bakış](../controls/panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bec5c-214">For more information about <xref:System.Windows.Controls.Panel> elements, see [Panels overview](../controls/panels-overview.md).</span></span> <span data-ttu-id="bec5c-215">Düzen hakkında daha fazla bilgi için bkz. [Düzen](../advanced/layout.md).</span><span class="sxs-lookup"><span data-stu-id="bec5c-215">For more information about layout, see [Layout](../advanced/layout.md).</span></span>

<span data-ttu-id="bec5c-216">Bu bölümde, <xref:System.Windows.Controls.Grid> içinde *`ExpenseItHome.xaml`* sütun ve satır tanımları ekleyerek üç satırı ve 10 piksellik bir kenar boşluğu içeren tek sütunlu bir tablo oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="bec5c-216">In this section, you create a single-column table with three rows and a 10-pixel margin by adding column and row definitions to the <xref:System.Windows.Controls.Grid> in *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="bec5c-217">İçinde *`ExpenseItHome.xaml`* <xref:System.Windows.FrameworkElement.Margin%2A> , öğesinde<xref:System.Windows.Controls.Grid> özelliğini sol, üst, sağ ve alt kenar boşluklarına karşılık gelen "10, 0, 10, 10" olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="bec5c-217">In *`ExpenseItHome.xaml`*, set the <xref:System.Windows.FrameworkElement.Margin%2A> property on the <xref:System.Windows.Controls.Grid> element to "10,0,10,10", which corresponds to left, top, right and bottom margins:</span></span>

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > <span data-ttu-id="bec5c-218">Ayrıca, **Özellikler** penceresinde, **Düzen** kategorisi altında **kenar boşluğu** değerlerini de ayarlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bec5c-218">You can also set the **Margin** values in the **Properties** window, under the **Layout** category:</span></span>
   >
   > ![Özellikler penceresi kenar boşluğu değerleri](./media/properties-margin.png)

2. <span data-ttu-id="bec5c-220">Satır ve sütun tanımları oluşturmak için <xref:System.Windows.Controls.Grid> aşağıdaki xaml etiketleri arasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bec5c-220">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags to create the row and column definitions:</span></span>

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    <span data-ttu-id="bec5c-221">İki satır olarak <xref:System.Windows.GridLength.Auto%2A>ayarlanır, yani satırlar satırlardaki içeriğe göre boyutlandırılır. <xref:System.Windows.Controls.RowDefinition.Height%2A></span><span class="sxs-lookup"><span data-stu-id="bec5c-221">The <xref:System.Windows.Controls.RowDefinition.Height%2A> of two rows is set to <xref:System.Windows.GridLength.Auto%2A>, which means that the rows are sized based on the content in the rows.</span></span> <span data-ttu-id="bec5c-222">Varsayılan değer <xref:System.Windows.Controls.RowDefinition.Height%2A> <xref:System.Windows.GridUnitType.Star> boyutlardır, bu da satır yüksekliğinin, kullanılabilir alanın ağırlıklı oransıdır.</span><span class="sxs-lookup"><span data-stu-id="bec5c-222">The default <xref:System.Windows.Controls.RowDefinition.Height%2A> is <xref:System.Windows.GridUnitType.Star> sizing, which means that the row height is a weighted proportion of the available space.</span></span> <span data-ttu-id="bec5c-223">Örneğin, her <xref:System.Windows.Controls.RowDefinition.Height%2A> biri "\*" olan iki satır, kullanılabilir alanın yarısı olan bir yüksekliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="bec5c-223">For example if two rows each have a <xref:System.Windows.Controls.RowDefinition.Height%2A> of "\*", they each have a height that is half of the available space.</span></span>

    <span data-ttu-id="bec5c-224"><xref:System.Windows.Controls.Grid> Şimdi aşağıdaki xaml 'yi içermelidir:</span><span class="sxs-lookup"><span data-stu-id="bec5c-224">Your <xref:System.Windows.Controls.Grid> should now contain the following XAML:</span></span>

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a><span data-ttu-id="bec5c-225">Denetim Ekle</span><span class="sxs-lookup"><span data-stu-id="bec5c-225">Add controls</span></span>

<span data-ttu-id="bec5c-226">Bu bölümde, giriş sayfası kullanıcı arabirimini, bir kişinin gider raporlarını görüntülemek için bir kişi seçtiğiniz bir kişi listesini gösterecek şekilde güncelleştireceksiniz.</span><span class="sxs-lookup"><span data-stu-id="bec5c-226">In this section, you'll update the home page UI to show a list of people, where you select one person to display their expense report.</span></span> <span data-ttu-id="bec5c-227">Denetimler, kullanıcıların uygulamanızla etkileşime geçmesini sağlayan UI nesneleridir.</span><span class="sxs-lookup"><span data-stu-id="bec5c-227">Controls are UI objects that allow users to interact with your application.</span></span> <span data-ttu-id="bec5c-228">Daha fazla bilgi için bkz. [denetimler](../controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="bec5c-228">For more information, see [Controls](../controls/index.md).</span></span>

<span data-ttu-id="bec5c-229">Bu Kullanıcı arabirimini oluşturmak için aşağıdaki öğeleri öğesine *`ExpenseItHome.xaml`* ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bec5c-229">To create this UI, you'll add the following elements to *`ExpenseItHome.xaml`*:</span></span>

- <span data-ttu-id="bec5c-230">A <xref:System.Windows.Controls.ListBox> (kişiler listesi için).</span><span class="sxs-lookup"><span data-stu-id="bec5c-230">A <xref:System.Windows.Controls.ListBox> (for the list of people).</span></span>
- <span data-ttu-id="bec5c-231">A <xref:System.Windows.Controls.Label> (liste üst bilgisi için).</span><span class="sxs-lookup"><span data-stu-id="bec5c-231">A <xref:System.Windows.Controls.Label> (for the list header).</span></span>
- <span data-ttu-id="bec5c-232">A <xref:System.Windows.Controls.Button> (listede Seçilen kişiye ait gider raporunu görüntülemek için tıklayın).</span><span class="sxs-lookup"><span data-stu-id="bec5c-232">A <xref:System.Windows.Controls.Button> (to click to view the expense report for the person that is selected in the list).</span></span>

<span data-ttu-id="bec5c-233">Her denetim, <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> iliştirilmiş özelliği ayarlanarak öğesinin bir satırına yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="bec5c-233">Each control is placed in a row of the <xref:System.Windows.Controls.Grid> by setting the <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> attached property.</span></span> <span data-ttu-id="bec5c-234">Ekli Özellikler hakkında daha fazla bilgi için bkz. [ekli özelliklere genel bakış](../advanced/attached-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bec5c-234">For more information about attached properties, see [Attached Properties Overview](../advanced/attached-properties-overview.md).</span></span>

1. <span data-ttu-id="bec5c-235">İçinde *`ExpenseItHome.xaml`* aşağıdaki xaml 'yi <xref:System.Windows.Controls.Grid> Etiketler arasına bir yere ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bec5c-235">In *`ExpenseItHome.xaml`*, add the following XAML somewhere between the <xref:System.Windows.Controls.Grid> tags:</span></span>

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > <span data-ttu-id="bec5c-236">Ayrıca, denetimleri **araç kutusu** penceresinden tasarım penceresine sürükleyerek ve sonra Özellikler penceresinde özelliklerini ayarlayarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bec5c-236">You can also create the controls by dragging them from the **Toolbox** window onto the design window, and then setting their properties in the **Properties** window.</span></span>

2. <span data-ttu-id="bec5c-237">Uygulamayı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="bec5c-237">Build and run the application.</span></span>

    <span data-ttu-id="bec5c-238">Aşağıdaki çizimde, oluşturduğunuz denetimler gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="bec5c-238">The following illustration shows the controls you created:</span></span>

![ExpenseIt örnek bir ad listesini görüntüleyen ekran görüntüsü](./media/walkthrough-my-first-wpf-desktop-application/add-application-controls.png)

## <a name="add-an-image-and-a-title"></a><span data-ttu-id="bec5c-240">Görüntü ve başlık ekleme</span><span class="sxs-lookup"><span data-stu-id="bec5c-240">Add an image and a title</span></span>

<span data-ttu-id="bec5c-241">Bu bölümde, ana sayfa Kullanıcı arabirimini bir görüntüyle ve bir sayfa başlığıyla güncelleştireceksiniz.</span><span class="sxs-lookup"><span data-stu-id="bec5c-241">In this section, you'll update the home page UI with an image and a page title.</span></span>

1. <span data-ttu-id="bec5c-242">İçinde *`ExpenseItHome.xaml`* , 230 piksellik bir sabit <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> <xref:System.Windows.Controls.ColumnDefinition.Width%2A> ile başka bir sütun ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bec5c-242">In *`ExpenseItHome.xaml`*, add another column to the <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> with a fixed <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of 230 pixels:</span></span>

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=52-55)]

2. <span data-ttu-id="bec5c-243">Toplam dört satır için başka <xref:System.Windows.Controls.Grid.RowDefinitions%2A>bir satır ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bec5c-243">Add another row to the <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, for a total of four rows:</span></span>

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=57-62)]

3. <span data-ttu-id="bec5c-244">Her üç denetimin (kenarlık, ListBox ve düğme) <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> her birinde özelliği 1 olarak ayarlayarak denetimleri ikinci sütuna taşıyın.</span><span class="sxs-lookup"><span data-stu-id="bec5c-244">Move the controls to the second column by setting the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property to 1 in each of the three controls (Border, ListBox, and Button).</span></span>

4. <span data-ttu-id="bec5c-245">Üç denetimin (kenarlık, ListBox ve düğme) <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> ve kenarlık öğesinin her biri için değerini 1 artırarak her denetimi bir satırı aşağı taşıyın.</span><span class="sxs-lookup"><span data-stu-id="bec5c-245">Move each control down a row by incrementing its <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> value by 1 for each of the three controls (Border, ListBox, and Button) and for the Border element.</span></span>

   <span data-ttu-id="bec5c-246">Üç denetim için XAML artık aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="bec5c-246">The XAML for the three controls now looks like the following:</span></span>

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

5. <span data-ttu-id="bec5c-247">Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> ve`</Grid>`etiketleri arasında bir yere ekleyerek, özelliği filigran. png resim dosyasına ayarlayın: `<Grid>`</span><span class="sxs-lookup"><span data-stu-id="bec5c-247">Set the <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> property to the *watermark.png* image file, by adding the following XAML anywhere between the `<Grid>` and `</Grid>` tags:</span></span>

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

6. <span data-ttu-id="bec5c-248">Öğesinden önce, "harcama raporu <xref:System.Windows.Controls.Label> görüntüle" içerikli bir öğesi ekleyin. <xref:System.Windows.Controls.Border></span><span class="sxs-lookup"><span data-stu-id="bec5c-248">Before the <xref:System.Windows.Controls.Border> element, add a <xref:System.Windows.Controls.Label> with the content "View Expense Report".</span></span> <span data-ttu-id="bec5c-249">Bu etiket sayfanın başlığıdır.</span><span class="sxs-lookup"><span data-stu-id="bec5c-249">This label is the title of the page.</span></span>

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

7. <span data-ttu-id="bec5c-250">Uygulamayı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="bec5c-250">Build and run the application.</span></span>

<span data-ttu-id="bec5c-251">Aşağıdaki çizimde, yeni eklediklerinize ilişkin sonuçlar gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="bec5c-251">The following illustration shows the results of what you just added:</span></span>

![Yeni görüntü arka planını ve sayfa başlığını gösteren ExpenseIt örnek ekran görüntüsü](./media/walkthrough-my-first-wpf-desktop-application/add-application-image-title.png)

## <a name="add-code-to-handle-events"></a><span data-ttu-id="bec5c-253">Olayları işlemek için kod ekleme</span><span class="sxs-lookup"><span data-stu-id="bec5c-253">Add code to handle events</span></span>

1. <span data-ttu-id="bec5c-254">İçinde *`ExpenseItHome.xaml`* , <xref:System.Windows.Controls.Button> öğesine bir <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay işleyicisi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bec5c-254">In *`ExpenseItHome.xaml`*, add a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to the <xref:System.Windows.Controls.Button> element.</span></span> <span data-ttu-id="bec5c-255">Daha fazla bilgi için [nasıl yapılır: Basit bir olay işleyicisi](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100))oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bec5c-255">For more information, see [How to: Create a simple event handler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span></span>

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

2. <span data-ttu-id="bec5c-256">*`ExpenseItHome.xaml.vb`* *Veya`ExpenseItHome.xaml.cs`* öğesini açın.</span><span class="sxs-lookup"><span data-stu-id="bec5c-256">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

3. <span data-ttu-id="bec5c-257">Bir düğme tıklama olayı işleyicisi eklemek `ExpenseItHome` için aşağıdaki kodu sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bec5c-257">Add the following code to the `ExpenseItHome` class to add a button click event handler.</span></span> <span data-ttu-id="bec5c-258">Olay işleyicisi **ExpenseReportPage** sayfasını açar.</span><span class="sxs-lookup"><span data-stu-id="bec5c-258">The event handler opens the **ExpenseReportPage** page.</span></span>

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a><span data-ttu-id="bec5c-259">ExpenseReportPage için Kullanıcı arabirimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="bec5c-259">Create the UI for ExpenseReportPage</span></span>

<span data-ttu-id="bec5c-260">*ExpenseReportPage. xaml* , **`ExpenseItHome`** sayfada seçili olan kişinin gider raporunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="bec5c-260">*ExpenseReportPage.xaml* displays the expense report for the person that's selected on the **`ExpenseItHome`** page.</span></span> <span data-ttu-id="bec5c-261">Bu bölümde, **ExpenseReportPage**için Kullanıcı arabirimi oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="bec5c-261">In this section, you'll create the UI for **ExpenseReportPage**.</span></span> <span data-ttu-id="bec5c-262">Ayrıca, çeşitli UI öğelerine arkaplan ve Fill renkleri de ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="bec5c-262">You'll also add background and fill colors to the various UI elements.</span></span>

1. <span data-ttu-id="bec5c-263">*ExpenseReportPage. xaml*' i açın.</span><span class="sxs-lookup"><span data-stu-id="bec5c-263">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="bec5c-264">Aşağıdaki XAML <xref:System.Windows.Controls.Grid> etiketleri arasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bec5c-264">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags:</span></span>

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    <span data-ttu-id="bec5c-265">Rapor verileri bir <xref:System.Windows.Controls.DataGrid>içinde görüntülenirken *`ExpenseItHome.xaml`* , bu kullanıcı arabirimi öğesine benzerdir.</span><span class="sxs-lookup"><span data-stu-id="bec5c-265">This UI is similar to *`ExpenseItHome.xaml`*, except the report data is displayed in a <xref:System.Windows.Controls.DataGrid>.</span></span>

3. <span data-ttu-id="bec5c-266">Uygulamayı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="bec5c-266">Build and run the application.</span></span>

4. <span data-ttu-id="bec5c-267">**Görünüm** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="bec5c-267">Select the **View** button.</span></span>

    <span data-ttu-id="bec5c-268">Gider raporu sayfası görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="bec5c-268">The expense report page appears.</span></span> <span data-ttu-id="bec5c-269">Ayrıca, geri gezinme düğmesinin etkin olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="bec5c-269">Also notice that the back navigation button is enabled.</span></span>

<span data-ttu-id="bec5c-270">Aşağıdaki çizimde, *ExpenseReportPage. xaml*'e eklenen UI öğeleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bec5c-270">The following illustration shows the UI elements added to *ExpenseReportPage.xaml*.</span></span>

![Yalnızca ExpenseReportPage için oluşturulan kullanıcı arabirimini gösteren ExpenseIt örnek ekran görüntüsü.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

## <a name="style-controls"></a><span data-ttu-id="bec5c-272">Stil denetimleri</span><span class="sxs-lookup"><span data-stu-id="bec5c-272">Style controls</span></span>

<span data-ttu-id="bec5c-273">Çeşitli öğelerin görünümü, bir kullanıcı arabirimindeki aynı türdeki tüm öğeler için genellikle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="bec5c-273">The appearance of various elements is often the same for all elements of the same type in a UI.</span></span> <span data-ttu-id="bec5c-274">UI, görünümleri birden çok öğe arasında yeniden kullanılabilir hale getirmek için [stilleri](../controls/styling-and-templating.md) kullanır.</span><span class="sxs-lookup"><span data-stu-id="bec5c-274">UI uses [styles](../controls/styling-and-templating.md) to make appearances reusable across multiple elements.</span></span> <span data-ttu-id="bec5c-275">Stillerin yeniden kullanılabilirliği XAML oluşturma ve yönetimini basitleştirmeye yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="bec5c-275">The reusability of styles helps to simplify XAML creation and management.</span></span> <span data-ttu-id="bec5c-276">Bu bölüm, önceki adımlarda tanımlanan öğe başına özniteliklerin stil ile yerini alır.</span><span class="sxs-lookup"><span data-stu-id="bec5c-276">This section replaces the per-element attributes that were defined in previous steps with styles.</span></span>

1. <span data-ttu-id="bec5c-277">*Application. xaml* veya *app. xaml*açın.</span><span class="sxs-lookup"><span data-stu-id="bec5c-277">Open *Application.xaml* or *App.xaml*.</span></span>

2. <span data-ttu-id="bec5c-278">Aşağıdaki XAML <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> etiketleri arasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bec5c-278">Add the following XAML between the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tags:</span></span>

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    <span data-ttu-id="bec5c-279">Bu XAML aşağıdaki stilleri ekler:</span><span class="sxs-lookup"><span data-stu-id="bec5c-279">This XAML adds the following styles:</span></span>

    - <span data-ttu-id="bec5c-280">`headerTextStyle`: Sayfa başlığını <xref:System.Windows.Controls.Label>biçimlendirmek için.</span><span class="sxs-lookup"><span data-stu-id="bec5c-280">`headerTextStyle`: To format the page title <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="bec5c-281">`labelStyle`: <xref:System.Windows.Controls.Label> Denetimleri biçimlendirmek için.</span><span class="sxs-lookup"><span data-stu-id="bec5c-281">`labelStyle`: To format the <xref:System.Windows.Controls.Label> controls.</span></span>

    - <span data-ttu-id="bec5c-282">`columnHeaderStyle`: Öğesini biçimlendirin <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span><span class="sxs-lookup"><span data-stu-id="bec5c-282">`columnHeaderStyle`: To format the <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span></span>

    - <span data-ttu-id="bec5c-283">`listHeaderStyle`: Liste üst bilgi <xref:System.Windows.Controls.Border> denetimlerini biçimlendirmek için.</span><span class="sxs-lookup"><span data-stu-id="bec5c-283">`listHeaderStyle`: To format the list header <xref:System.Windows.Controls.Border> controls.</span></span>

    - <span data-ttu-id="bec5c-284">`listHeaderTextStyle`: Liste üst bilgisini <xref:System.Windows.Controls.Label>biçimlendirmek için.</span><span class="sxs-lookup"><span data-stu-id="bec5c-284">`listHeaderTextStyle`: To format the list header <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="bec5c-285">`buttonStyle`: Öğesini biçimlendirin <xref:System.Windows.Controls.Button>. `ExpenseItHome.xaml`</span><span class="sxs-lookup"><span data-stu-id="bec5c-285">`buttonStyle`: To format the <xref:System.Windows.Controls.Button> on `ExpenseItHome.xaml`.</span></span>

    <span data-ttu-id="bec5c-286">Stillerin kaynak ve <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> özellik öğesinin alt öğesi olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="bec5c-286">Notice that the styles are resources and children of the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> property element.</span></span> <span data-ttu-id="bec5c-287">Bu konumda, stiller bir uygulamadaki tüm öğelere uygulanır.</span><span class="sxs-lookup"><span data-stu-id="bec5c-287">In this location, the styles are applied to all the elements in an application.</span></span> <span data-ttu-id="bec5c-288">Bir .NET uygulamasında kaynak kullanmanın bir örneği için bkz. [uygulama kaynaklarını kullanma](../advanced/how-to-use-application-resources.md).</span><span class="sxs-lookup"><span data-stu-id="bec5c-288">For an example of using resources in a .NET app, see [Use Application Resources](../advanced/how-to-use-application-resources.md).</span></span>

3. <span data-ttu-id="bec5c-289">İçinde *`ExpenseItHome.xaml`* , <xref:System.Windows.Controls.Grid> öğeler arasındaki her şeyi aşağıdaki xaml ile değiştirin:</span><span class="sxs-lookup"><span data-stu-id="bec5c-289">In *`ExpenseItHome.xaml`*, replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    <span data-ttu-id="bec5c-290"><xref:System.Windows.VerticalAlignment> Ve<xref:System.Windows.Media.FontFamily> her bir denetimin görünümünü tanımlayan özellikler, stiller uygulanarak kaldırılır ve değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="bec5c-290">The properties such as <xref:System.Windows.VerticalAlignment> and <xref:System.Windows.Media.FontFamily> that define the look of each control are removed and replaced by applying the styles.</span></span> <span data-ttu-id="bec5c-291">Örneğin `headerTextStyle` , "harcama raporu görüntüle" <xref:System.Windows.Controls.Label>öğesine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="bec5c-291">For example, the `headerTextStyle` is applied to the "View Expense Report" <xref:System.Windows.Controls.Label>.</span></span>

4. <span data-ttu-id="bec5c-292">*ExpenseReportPage. xaml*' i açın.</span><span class="sxs-lookup"><span data-stu-id="bec5c-292">Open *ExpenseReportPage.xaml*.</span></span>

5. <span data-ttu-id="bec5c-293">Aşağıdaki XAML ile <xref:System.Windows.Controls.Grid> öğeler arasındaki her şeyi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="bec5c-293">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    <span data-ttu-id="bec5c-294">Bu XAML, <xref:System.Windows.Controls.Label> ve <xref:System.Windows.Controls.Border> öğelerine stiller ekler.</span><span class="sxs-lookup"><span data-stu-id="bec5c-294">This XAML adds styles to the <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Border> elements.</span></span>

6. <span data-ttu-id="bec5c-295">Uygulamayı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="bec5c-295">Build and run the application.</span></span> <span data-ttu-id="bec5c-296">Pencere görünümü daha önce olduğu gibi.</span><span class="sxs-lookup"><span data-stu-id="bec5c-296">The window appearance is the same as previously.</span></span>

    ![En son bölümle aynı görünüme sahip olan ExpenseIt örnek ekran görüntüsü.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

7. <span data-ttu-id="bec5c-298">Visual Studio 'ya dönmek için uygulamayı kapatın.</span><span class="sxs-lookup"><span data-stu-id="bec5c-298">Close the application to return to Visual Studio.</span></span>

## <a name="bind-data-to-a-control"></a><span data-ttu-id="bec5c-299">Verileri bir denetime bağlama</span><span class="sxs-lookup"><span data-stu-id="bec5c-299">Bind data to a control</span></span>

<span data-ttu-id="bec5c-300">Bu bölümde, çeşitli denetimlere bağlanan XML verilerini oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="bec5c-300">In this section, you'll create the XML data that is bound to various controls.</span></span>

1. <span data-ttu-id="bec5c-301">' *`ExpenseItHome.xaml`* De, açılış <xref:System.Windows.Controls.Grid> öğesinden sonra, her bir kişiye ait verileri içeren bir <xref:System.Windows.Data.XmlDataProvider> oluşturmak için aşağıdaki xaml 'yi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bec5c-301">In *`ExpenseItHome.xaml`*, after the opening <xref:System.Windows.Controls.Grid> element, add the following XAML to create an <xref:System.Windows.Data.XmlDataProvider> that contains the data for each person:</span></span>

    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,16-40,49)]

    <span data-ttu-id="bec5c-302">Veriler bir <xref:System.Windows.Controls.Grid> kaynak olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="bec5c-302">The data is created as a <xref:System.Windows.Controls.Grid> resource.</span></span> <span data-ttu-id="bec5c-303">Normalde bu veriler bir dosya olarak yüklenir, ancak kolaylık sağlaması için veriler satır içi eklenir.</span><span class="sxs-lookup"><span data-stu-id="bec5c-303">Normally this data would be loaded as a file, but for simplicity the data is added inline.</span></span>

2. <span data-ttu-id="bec5c-304">Öğesi içinde <xref:System.Windows.Controls.ListBox>, öğesinden`<XmlDataProvider>` sonra ' de `<xref:System.Windows.DataTemplate>` verilerin nasıl görüntüleneceğini tanımlayan aşağıdaki öğeyi ekleyin: `<Grid.Resources>`</span><span class="sxs-lookup"><span data-stu-id="bec5c-304">Within the `<Grid.Resources>` element, add the following `<xref:System.Windows.DataTemplate>` element, which defines how to display the data in the <xref:System.Windows.Controls.ListBox>, after the `<XmlDataProvider>` element:</span></span>

    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,43-46,49)]

    <span data-ttu-id="bec5c-305">Veri şablonları hakkında daha fazla bilgi için bkz. [veri şablonu oluşturmaya genel bakış](../data/data-templating-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bec5c-305">For more information about data templates, see [Data templating overview](../data/data-templating-overview.md).</span></span>

3. <span data-ttu-id="bec5c-306">Var olan <xref:System.Windows.Controls.ListBox> aşağıdaki xaml ile değiştirin:</span><span class="sxs-lookup"><span data-stu-id="bec5c-306">Replace the existing <xref:System.Windows.Controls.ListBox> with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    <span data-ttu-id="bec5c-307">Bu XAML, <xref:System.Windows.Controls.ListBox> öğesinin <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliğini veri kaynağına bağlar ve veri şablonunu olarak <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>uygular.</span><span class="sxs-lookup"><span data-stu-id="bec5c-307">This XAML binds the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to the data source and applies the data template as the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span></span>

## <a name="connect-data-to-controls"></a><span data-ttu-id="bec5c-308">Verileri denetimlere bağlama</span><span class="sxs-lookup"><span data-stu-id="bec5c-308">Connect data to controls</span></span>

<span data-ttu-id="bec5c-309">Daha sonra, **`ExpenseItHome`** sayfada seçilen adı almak için kod ekleyeceksiniz ve bunu **ExpenseReportPage**oluşturucusuna geçireceğiz.</span><span class="sxs-lookup"><span data-stu-id="bec5c-309">Next, you'll add code to retrieve the name that's selected on the **`ExpenseItHome`** page and pass it to the constructor of **ExpenseReportPage**.</span></span> <span data-ttu-id="bec5c-310">**ExpenseReportPage** ,, *ExpenseReportPage. xaml* ' de tanımlanan denetimlerin, geçirilen öğeyle veri bağlamını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bec5c-310">**ExpenseReportPage** sets its data context with the passed item, which is what the controls defined in *ExpenseReportPage.xaml* bind to.</span></span>

1. <span data-ttu-id="bec5c-311">*ExpenseReportPage. xaml. vb* veya *ExpenseReportPage.xaml.cs*öğesini açın.</span><span class="sxs-lookup"><span data-stu-id="bec5c-311">Open *ExpenseReportPage.xaml.vb* or *ExpenseReportPage.xaml.cs*.</span></span>

2. <span data-ttu-id="bec5c-312">Seçili kişinin gider raporu verilerini geçirebilmeniz için bir nesnesi alan bir Oluşturucu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bec5c-312">Add a constructor that takes an object so you can pass the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. <span data-ttu-id="bec5c-313">*`ExpenseItHome.xaml.vb`* *Veya`ExpenseItHome.xaml.cs`* öğesini açın.</span><span class="sxs-lookup"><span data-stu-id="bec5c-313">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

4. <span data-ttu-id="bec5c-314"><xref:System.Windows.Controls.Primitives.ButtonBase.Click> Olay işleyicisini, seçilen kişinin harcama raporu verilerini geçen yeni oluşturucuyu çağırmak üzere değiştirin.</span><span class="sxs-lookup"><span data-stu-id="bec5c-314">Change the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to call the new constructor passing the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a><span data-ttu-id="bec5c-315">Veri şablonlarıyla stil verileri</span><span class="sxs-lookup"><span data-stu-id="bec5c-315">Style data with data templates</span></span>

<span data-ttu-id="bec5c-316">Bu bölümde, veri şablonlarını kullanarak veri bağlantılı listelerdeki her öğe için Kullanıcı arabirimini güncelleştireceksiniz.</span><span class="sxs-lookup"><span data-stu-id="bec5c-316">In this section, you'll update the UI for each item in the data-bound lists by using data templates.</span></span>

1. <span data-ttu-id="bec5c-317">*ExpenseReportPage. xaml*' i açın.</span><span class="sxs-lookup"><span data-stu-id="bec5c-317">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="bec5c-318">"Name" ve "Department" <xref:System.Windows.Controls.Label> öğelerinin içeriğini uygun veri kaynağı özelliğine bağlayın.</span><span class="sxs-lookup"><span data-stu-id="bec5c-318">Bind the content of the "Name" and "Department" <xref:System.Windows.Controls.Label> elements to the appropriate data source property.</span></span> <span data-ttu-id="bec5c-319">Veri bağlama hakkında daha fazla bilgi için bkz. [veri bağlamaya genel bakış](../data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bec5c-319">For more information about data binding, see [Data binding overview](../data/data-binding-overview.md).</span></span>

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. <span data-ttu-id="bec5c-320">Açılış <xref:System.Windows.Controls.Grid> öğesinden sonra, harcama raporu verilerinin nasıl görüntüleneceğini tanımlayan aşağıdaki veri şablonlarını ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bec5c-320">After the opening <xref:System.Windows.Controls.Grid> element, add the following data templates, which define how to display the expense report data:</span></span>

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. <span data-ttu-id="bec5c-321">Öğeleri öğesi altında ile <xref:System.Windows.Controls.DataGridTemplateColumn> değiştirin ve şablonları bunlara uygulayın. <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Controls.DataGridTextColumn></span><span class="sxs-lookup"><span data-stu-id="bec5c-321">Replace the <xref:System.Windows.Controls.DataGridTextColumn> elements with <xref:System.Windows.Controls.DataGridTemplateColumn> under the <xref:System.Windows.Controls.DataGrid> element and apply the templates to them.</span></span>

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. <span data-ttu-id="bec5c-322">Uygulamayı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="bec5c-322">Build and run the application.</span></span>

6. <span data-ttu-id="bec5c-323">Bir kişi seçin ve ardından **Görünüm** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="bec5c-323">Select a person and then select the **View** button.</span></span>

<span data-ttu-id="bec5c-324">Aşağıdaki çizimde denetimler, düzen, stiller, `ExpenseIt` veri bağlama ve veri şablonları uygulanmış uygulamanın her iki sayfası gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="bec5c-324">The following illustration shows both pages of the `ExpenseIt` application with controls, layout, styles, data binding, and data templates applied:</span></span>

![Uygulamanın her iki sayfası da adlar listesini ve bir gider raporunu gösterir.](./media/walkthrough-my-first-wpf-desktop-application/application-data-templates.png)

> [!NOTE]
> <span data-ttu-id="bec5c-326">Bu örnek, WPF 'nin belirli bir özelliğini gösterir ve güvenlik, yerelleştirme ve erişilebilirlik gibi şeyler için en iyi uygulamaları izlemez.</span><span class="sxs-lookup"><span data-stu-id="bec5c-326">This sample demonstrates a specific feature of WPF and doesn't follow all best practices for things like security, localization, and accessibility.</span></span> <span data-ttu-id="bec5c-327">WPF ve .NET uygulama geliştirmenin en iyi uygulamalarının kapsamlı kapsamı için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="bec5c-327">For comprehensive coverage of WPF and the .NET app development best practices, see the following topics:</span></span>
>
> - [<span data-ttu-id="bec5c-328">Erişilebilirlik</span><span class="sxs-lookup"><span data-stu-id="bec5c-328">Accessibility</span></span>](../../ui-automation/accessibility-best-practices.md)
>
> - [<span data-ttu-id="bec5c-329">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="bec5c-329">Security</span></span>](../security-wpf.md)
>
> - [<span data-ttu-id="bec5c-330">WPF Genelleştirme ve yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="bec5c-330">WPF globalization and localization</span></span>](../advanced/wpf-globalization-and-localization-overview.md)
>
> - [<span data-ttu-id="bec5c-331">WPF performansı</span><span class="sxs-lookup"><span data-stu-id="bec5c-331">WPF performance</span></span>](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a><span data-ttu-id="bec5c-332">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="bec5c-332">Next steps</span></span>

<span data-ttu-id="bec5c-333">Bu kılavuzda, Windows Presentation Foundation (WPF) kullanarak Kullanıcı arabirimi oluşturmaya yönelik çeşitli teknikler öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="bec5c-333">In this walkthrough you learned a number of techniques for creating a UI using Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="bec5c-334">Artık, veri bağlantılı bir .NET uygulamasının yapı taşlarından daha basit bir bilgiye sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="bec5c-334">You should now have a basic understanding of the building blocks of a data-bound .NET app.</span></span> <span data-ttu-id="bec5c-335">WPF mimarisi ve programlama modelleri hakkında daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="bec5c-335">For more information about the WPF architecture and programming models, see the following topics:</span></span>

- [<span data-ttu-id="bec5c-336">WPF mimarisi</span><span class="sxs-lookup"><span data-stu-id="bec5c-336">WPF architecture</span></span>](../advanced/wpf-architecture.md)
- [<span data-ttu-id="bec5c-337">XAML 'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="bec5c-337">XAML overview (WPF)</span></span>](../advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="bec5c-338">Bağımlılık özelliklerine genel bakış</span><span class="sxs-lookup"><span data-stu-id="bec5c-338">Dependency properties overview</span></span>](../advanced/dependency-properties-overview.md)
- [<span data-ttu-id="bec5c-339">Düzen</span><span class="sxs-lookup"><span data-stu-id="bec5c-339">Layout</span></span>](../advanced/layout.md)

<span data-ttu-id="bec5c-340">Uygulama oluşturma hakkında daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="bec5c-340">For more information about creating applications, see the following topics:</span></span>

- [<span data-ttu-id="bec5c-341">Uygulama geliştirme</span><span class="sxs-lookup"><span data-stu-id="bec5c-341">Application development</span></span>](../app-development/index.md)
- [<span data-ttu-id="bec5c-342">Denetimler</span><span class="sxs-lookup"><span data-stu-id="bec5c-342">Controls</span></span>](../controls/index.md)
- [<span data-ttu-id="bec5c-343">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bec5c-343">Data binding overview</span></span>](../data/data-binding-overview.md)
- [<span data-ttu-id="bec5c-344">Grafikler ve multimedya</span><span class="sxs-lookup"><span data-stu-id="bec5c-344">Graphics and multimedia</span></span>](../graphics-multimedia/index.md)
- [<span data-ttu-id="bec5c-345">WPF'deki Belgeler</span><span class="sxs-lookup"><span data-stu-id="bec5c-345">Documents in WPF</span></span>](../advanced/documents-in-wpf.md)

## <a name="see-also"></a><span data-ttu-id="bec5c-346">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bec5c-346">See also</span></span>

- [<span data-ttu-id="bec5c-347">Panellere genel bakış</span><span class="sxs-lookup"><span data-stu-id="bec5c-347">Panels overview</span></span>](../controls/panels-overview.md)
- [<span data-ttu-id="bec5c-348">Veri şablonu genel bakış</span><span class="sxs-lookup"><span data-stu-id="bec5c-348">Data templating overview</span></span>](../data/data-templating-overview.md)
- [<span data-ttu-id="bec5c-349">WPF uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="bec5c-349">Build a WPF application</span></span>](../app-development/building-a-wpf-application-wpf.md)
- [<span data-ttu-id="bec5c-350">Stiller ve şablonlar</span><span class="sxs-lookup"><span data-stu-id="bec5c-350">Styles and templates</span></span>](../controls/styles-and-templates.md)
