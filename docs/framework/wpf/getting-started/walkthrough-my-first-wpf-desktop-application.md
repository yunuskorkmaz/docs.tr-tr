---
title: Visual Studio'da WPF uygulaması oluşturma
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
ms.openlocfilehash: c3440ddf6cdae6b24bcf1059ab2c76d8fb957263
ms.sourcegitcommit: 11deacc8ec9f229ab8ee3cd537515d4c2826515f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2019
ms.locfileid: "66003859"
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a><span data-ttu-id="325ed-102">İzlenecek yol: İlk WPF masaüstü uygulamam</span><span class="sxs-lookup"><span data-stu-id="325ed-102">Walkthrough: My first WPF desktop application</span></span>

<span data-ttu-id="325ed-103">Bu makalede, çoğu WPF uygulamaları için ortak olan öğeler içeren bir Windows Presentation Foundation (WPF) masaüstü uygulaması geliştirme işlemini göstermektedir: Extensible Application Markup Language (XAML) işaretleme, arka plan kod, uygulama tanımları, denetimler, düzen, veri bağlama ve stilleri.</span><span class="sxs-lookup"><span data-stu-id="325ed-103">This article shows you how to develop a Windows Presentation Foundation (WPF) desktop application that includes the elements that are common to most WPF applications: Extensible Application Markup Language (XAML) markup, code-behind, application definitions, controls, layout, data binding, and styles.</span></span> <span data-ttu-id="325ed-104">Uygulama geliştirmek için Visual Studio kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="325ed-104">To develop the application, you'll use Visual Studio.</span></span> 

<span data-ttu-id="325ed-105">Bu izlenecek yol aşağıdaki adımları içerir:</span><span class="sxs-lookup"><span data-stu-id="325ed-105">This walkthrough includes the following steps:</span></span>

- <span data-ttu-id="325ed-106">XAML, uygulamanın kullanıcı arabirimini (UI) görünümünü tasarlamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="325ed-106">Use XAML to design the appearance of the application's user interface (UI).</span></span>

- <span data-ttu-id="325ed-107">Uygulamanın davranışı oluşturmak için kod yazın.</span><span class="sxs-lookup"><span data-stu-id="325ed-107">Write code to build the application's behavior.</span></span>

- <span data-ttu-id="325ed-108">Uygulamayı yönetmek için bir uygulama tanımı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="325ed-108">Create an application definition to manage the application.</span></span>

- <span data-ttu-id="325ed-109">Denetimler ekleme ve uygulama kullanıcı Arabirimi oluşturmak için düzenini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="325ed-109">Add controls and create the layout to compose the application UI.</span></span>

- <span data-ttu-id="325ed-110">Stilleri için uygulamanın UI genelinde tutarlı bir görünüm oluşturun.</span><span class="sxs-lookup"><span data-stu-id="325ed-110">Create styles for a consistent appearance throughout the application's UI.</span></span>

- <span data-ttu-id="325ed-111">Verileri, veri kullanıcı Arabiriminden doldurmak ve verileri tutmak için kullanıcı arabirimini bağlamak ve UI eşitlenir.</span><span class="sxs-lookup"><span data-stu-id="325ed-111">Bind the UI to data, both to populate the UI from data and to keep the data and UI synchronized.</span></span>

<span data-ttu-id="325ed-112">İzlenecek yol sonunda, bağımsız bir seçilen kişilerin gider raporlarını görüntülemek kullanıcılara Windows uygulamasında oluşturulan.</span><span class="sxs-lookup"><span data-stu-id="325ed-112">By the end of the walkthrough, you'll have built a standalone Windows application that allows users to view expense reports for selected people.</span></span> <span data-ttu-id="325ed-113">Uygulama, bir tarayıcı penceresinde barındırılan birçok WPF sayfadan oluşur.</span><span class="sxs-lookup"><span data-stu-id="325ed-113">The application is composed of several WPF pages that are hosted in a browser-style window.</span></span>

> [!TIP]
> <span data-ttu-id="325ed-114">Bu izlenecek yolu oluşturmak için kullanılan örnek kod, hem Visual Basic için kullanılabilir ve C# adresindeki [izlenecek WPF uygulama örnek kodunu](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span><span class="sxs-lookup"><span data-stu-id="325ed-114">The sample code that is used to build this walkthrough is available for both Visual Basic and C# at [Walkthrough WPF App Sample Code](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span></span>
>
> <span data-ttu-id="325ed-115">Kod dili örnek kod arasında geçiş yapabilirsiniz C# ve Visual Basic'ı kullanarak **\< />** bu makalenin üst sağ taraftaki açılır.</span><span class="sxs-lookup"><span data-stu-id="325ed-115">You can toggle the code language of the sample code between C# and Visual Basic by using the **\</>** drop-down on the upper right side of this article.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="325ed-116">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="325ed-116">Prerequisites</span></span>

- <span data-ttu-id="325ed-117">(Bu makalede, Visual Studio 2019 kullanılmıştır) visual Studio 2017 veya üstü</span><span class="sxs-lookup"><span data-stu-id="325ed-117">Visual Studio 2017 or later (this article uses Visual Studio 2019)</span></span>

   <span data-ttu-id="325ed-118">Visual Studio'nun en son sürümü yükleme hakkında daha fazla bilgi için bkz. [Visual Studio'yu yükleyin](/visualstudio/install/install-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="325ed-118">For more information about installing the latest version of Visual Studio, see [Install Visual Studio](/visualstudio/install/install-visual-studio).</span></span>

## <a name="create-the-application-project"></a><span data-ttu-id="325ed-119">Uygulama projesini oluşturun</span><span class="sxs-lookup"><span data-stu-id="325ed-119">Create the application project</span></span>

<span data-ttu-id="325ed-120">İlk adım, bir uygulama tanımı, iki sayfaları ve görüntü içeren uygulama altyapısı oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="325ed-120">The first step is to create the application infrastructure, which includes an application definition, two pages, and an image.</span></span>

1. <span data-ttu-id="325ed-121">Visual Basic veya Visual C# adlı yeni bir WPF uygulaması projesi oluşturma **`ExpenseIt`**:</span><span class="sxs-lookup"><span data-stu-id="325ed-121">Create a new WPF Application project in Visual Basic or Visual C# named **`ExpenseIt`**:</span></span>

   1. <span data-ttu-id="325ed-122">Visual Studio açıp seçin **yeni bir proje oluşturma** altında **başlama** menüsü.</span><span class="sxs-lookup"><span data-stu-id="325ed-122">Open Visual Studio and select **Create a new project** under the **Get started** menu.</span></span>

      <span data-ttu-id="325ed-123">**Yeni bir proje oluşturma** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="325ed-123">The **Create a new project** dialog opens.</span></span>

   2. <span data-ttu-id="325ed-124">İçinde **dil** açılır listesinde, şunlardan birini seçin **C#** veya **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="325ed-124">In the **Language** dropdown, select either **C#** or **Visual Basic**.</span></span>
      
   3. <span data-ttu-id="325ed-125">Seçin **WPF uygulaması (.NET Framework)** şablonu ve ardından **sonraki**.</span><span class="sxs-lookup"><span data-stu-id="325ed-125">Select the **WPF App (.NET Framework)** template and then select **Next**.</span></span> 
     
      ![Yeni Proje iletişim kutusu oluşturma](./media/walkthrough-my-first-wpf-desktop-application/create-new-project-dialog.png)
    
      <span data-ttu-id="325ed-127">**Yeni projenizi yapılandırın** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="325ed-127">The **Configure your new project** dialog opens.</span></span>

   4. <span data-ttu-id="325ed-128">Proje adını girin **`ExpenseIt`** seçip **Oluştur**.</span><span class="sxs-lookup"><span data-stu-id="325ed-128">Enter the project name **`ExpenseIt`** and then select **Create**.</span></span>

      ![Yeni Proje iletişim kutusu yapılandırın](./media/walkthrough-my-first-wpf-desktop-application/configure-new-project-dialog.png)

      <span data-ttu-id="325ed-130">Visual Studio projesi oluşturup adlı varsayılan uygulama penceresi için tasarımcı açılır **MainWindow.xaml**.</span><span class="sxs-lookup"><span data-stu-id="325ed-130">Visual Studio creates the project and opens the designer for the default application window named **MainWindow.xaml**.</span></span>

2. <span data-ttu-id="325ed-131">Açık *Application.xaml* (Visual Basic) veya *App.xaml* (C#).</span><span class="sxs-lookup"><span data-stu-id="325ed-131">Open *Application.xaml* (Visual Basic) or *App.xaml* (C#).</span></span>

    <span data-ttu-id="325ed-132">Bu XAML dosyasını bir WPF uygulaması ve uygulama kaynaklarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="325ed-132">This XAML file defines a WPF application and any application resources.</span></span> <span data-ttu-id="325ed-133">Bu dosya kullanıcı Arabirimi, bu durumda belirtmek için de *MainWindow.xaml*, uygulama başlatıldığında otomatik olarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="325ed-133">You also use this file to specify the UI, in this case *MainWindow.xaml*, that automatically shows when the application starts.</span></span>

    <span data-ttu-id="325ed-134">XAML, Visual Basic'te aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="325ed-134">Your XAML should look like the following in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    <span data-ttu-id="325ed-135">Ve aşağıdaki gibi C#:</span><span class="sxs-lookup"><span data-stu-id="325ed-135">And like the following in C#:</span></span>

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. <span data-ttu-id="325ed-136">Açık *MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="325ed-136">Open *MainWindow.xaml*.</span></span>

    <span data-ttu-id="325ed-137">Bu XAML dosyası ana penceresinde, uygulamanızın ve sayfalarında oluşturulan içeriği görüntüler.</span><span class="sxs-lookup"><span data-stu-id="325ed-137">This XAML file is the main window of your application and displays content created in pages.</span></span> <span data-ttu-id="325ed-138"><xref:System.Windows.Window> Sınıfı gibi başlık, boyut veya simge, bir penceresi özelliklerini tanımlar ve kapatma veya gizleme gibi olayları işler.</span><span class="sxs-lookup"><span data-stu-id="325ed-138">The <xref:System.Windows.Window> class defines the properties of a window, such as its title, size, or icon, and handles events, such as closing or hiding.</span></span>

4. <span data-ttu-id="325ed-139">Değişiklik <xref:System.Windows.Window> öğesine bir <xref:System.Windows.Navigation.NavigationWindow>aşağıdaki XAML içinde gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="325ed-139">Change the <xref:System.Windows.Window> element to a <xref:System.Windows.Navigation.NavigationWindow>, as shown in the following XAML:</span></span>

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   <span data-ttu-id="325ed-140">Bu uygulamanın kullanıcı girişi bağlı olarak farklı içerik gider.</span><span class="sxs-lookup"><span data-stu-id="325ed-140">This app navigates to different content depending on the user input.</span></span> <span data-ttu-id="325ed-141">Bu nedenle, ana <xref:System.Windows.Window> için değiştirilmesi gereken bir <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="325ed-141">This is why the main <xref:System.Windows.Window> needs to be changed to a <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="325ed-142"><xref:System.Windows.Navigation.NavigationWindow> tüm özelliklerini devralır <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="325ed-142"><xref:System.Windows.Navigation.NavigationWindow> inherits all the properties of <xref:System.Windows.Window>.</span></span> <span data-ttu-id="325ed-143"><xref:System.Windows.Navigation.NavigationWindow> XAML dosyasında öğe bir örneğini oluşturur <xref:System.Windows.Navigation.NavigationWindow> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="325ed-143">The <xref:System.Windows.Navigation.NavigationWindow> element in the XAML file creates an instance of the <xref:System.Windows.Navigation.NavigationWindow> class.</span></span> <span data-ttu-id="325ed-144">Daha fazla bilgi için [gezintiye genel bakış](../app-development/navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="325ed-144">For more information, see [Navigation overview](../app-development/navigation-overview.md).</span></span>

5. <span data-ttu-id="325ed-145">Kaldırma <xref:System.Windows.Controls.Grid> öğeleri arasında <xref:System.Windows.Navigation.NavigationWindow> etiketler.</span><span class="sxs-lookup"><span data-stu-id="325ed-145">Remove the <xref:System.Windows.Controls.Grid> elements from between the <xref:System.Windows.Navigation.NavigationWindow> tags.</span></span>

6. <span data-ttu-id="325ed-146">XAML kodunu şu özelliklerde değişiklik <xref:System.Windows.Navigation.NavigationWindow> öğesi:</span><span class="sxs-lookup"><span data-stu-id="325ed-146">Change the following properties in the XAML code for the <xref:System.Windows.Navigation.NavigationWindow> element:</span></span>

    - <span data-ttu-id="325ed-147">Ayarlama <xref:System.Windows.Window.Title%2A> özelliğini "`ExpenseIt`".</span><span class="sxs-lookup"><span data-stu-id="325ed-147">Set the <xref:System.Windows.Window.Title%2A> property to "`ExpenseIt`".</span></span>

    - <span data-ttu-id="325ed-148">Ayarlama <xref:System.Windows.FrameworkElement.Height%2A> özelliğini 350 piksel.</span><span class="sxs-lookup"><span data-stu-id="325ed-148">Set the <xref:System.Windows.FrameworkElement.Height%2A> property to 350 pixels.</span></span>

    - <span data-ttu-id="325ed-149">Ayarlama <xref:System.Windows.FrameworkElement.Width%2A> özelliğini 500 piksel.</span><span class="sxs-lookup"><span data-stu-id="325ed-149">Set the <xref:System.Windows.FrameworkElement.Width%2A> property to 500 pixels.</span></span>

    <span data-ttu-id="325ed-150">XAML, Visual Basic için aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="325ed-150">Your XAML should look like the following for Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    <span data-ttu-id="325ed-151">Ve aşağıdaki gibi C#:</span><span class="sxs-lookup"><span data-stu-id="325ed-151">And like the following for C#:</span></span>

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

7. <span data-ttu-id="325ed-152">Açık *MainWindow.xaml.vb* veya *MainWindow.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="325ed-152">Open *MainWindow.xaml.vb* or *MainWindow.xaml.cs*.</span></span>

    <span data-ttu-id="325ed-153">Bildirilen olaylarını işlemek için kod içeren bir arka plan kod dosyası bu dosyadır *MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="325ed-153">This file is a code-behind file that contains code to handle the events declared in *MainWindow.xaml*.</span></span> <span data-ttu-id="325ed-154">Bu dosya, XAML içinde tanımlanan penceresi için bir parçalı sınıf içerir.</span><span class="sxs-lookup"><span data-stu-id="325ed-154">This file contains a partial class for the window defined in XAML.</span></span>

8. <span data-ttu-id="325ed-155">Kullanıyorsanız C#, değiştirme `MainWindow` öğesinden türetilen sınıfın <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="325ed-155">If you're using C#, change the `MainWindow` class to derive from <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="325ed-156">(XAML penceresinde değiştirdiğinizde Visual Basic'te bu otomatik olarak gerçekleşir.) C# Kod artık şu şekilde görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="325ed-156">(In Visual Basic, this happens automatically when you change the window in XAML.) Your C# code should now look like this:</span></span>

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/MainWindow.xaml.cs?highlight=21)]

## <a name="add-files-to-the-application"></a><span data-ttu-id="325ed-157">Uygulama için dosyaları Ekle</span><span class="sxs-lookup"><span data-stu-id="325ed-157">Add files to the application</span></span>

<span data-ttu-id="325ed-158">Bu bölümde, uygulamaya iki sayfaları ve görüntü ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="325ed-158">In this section, you'll add two pages and an image to the application.</span></span>

1. <span data-ttu-id="325ed-159">Projeye yeni bir sayfa ekleyin ve adlandırın *`ExpenseItHome.xaml`*:</span><span class="sxs-lookup"><span data-stu-id="325ed-159">Add a new page to the project, and name it *`ExpenseItHome.xaml`*:</span></span>

   1. <span data-ttu-id="325ed-160">İçinde **Çözüm Gezgini**, sağ **`ExpenseIt`** projesini düğümünü ve ardından **Ekle** > **sayfa**.</span><span class="sxs-lookup"><span data-stu-id="325ed-160">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="325ed-161">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sayfa (WPF)** şablon zaten seçili.</span><span class="sxs-lookup"><span data-stu-id="325ed-161">In the **Add New Item** dialog, the **Page (WPF)** template is already selected.</span></span> <span data-ttu-id="325ed-162">Bir ad girin **`ExpenseItHome`** ve ardından **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="325ed-162">Enter the name **`ExpenseItHome`**, and then select **Add**.</span></span>

    <span data-ttu-id="325ed-163">Uygulama başlatıldığında görüntülenen ilk sayfa sayfasıdır.</span><span class="sxs-lookup"><span data-stu-id="325ed-163">This page is the first page that's displayed when the application is launched.</span></span> <span data-ttu-id="325ed-164">İçin harcama raporunu görüntülemek için seçmek için kişi listesi gösterilir.</span><span class="sxs-lookup"><span data-stu-id="325ed-164">It will show a list of people to select from, to show an expense report for.</span></span>

1. <span data-ttu-id="325ed-165">Açık *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="325ed-165">Open *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="325ed-166">Ayarlama <xref:System.Windows.Controls.Page.Title%2A> için "`ExpenseIt - Home`".</span><span class="sxs-lookup"><span data-stu-id="325ed-166">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - Home`".</span></span>

1. <span data-ttu-id="325ed-167">Ayarlama `DesignHeight` ve `DesignWidth` öğe değerlerini 300 piksel.</span><span class="sxs-lookup"><span data-stu-id="325ed-167">Set the `DesignHeight` and `DesignWidth` element values to 300 pixels.</span></span>

    <span data-ttu-id="325ed-168">Artık XAML Visual Basic için şu şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="325ed-168">The XAML now appears as follows for Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    <span data-ttu-id="325ed-169">Ve aşağıdaki gibi C#:</span><span class="sxs-lookup"><span data-stu-id="325ed-169">And like the following for C#:</span></span>

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

1. <span data-ttu-id="325ed-170">Açık *MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="325ed-170">Open *MainWindow.xaml*.</span></span>

1. <span data-ttu-id="325ed-171">Ekleme bir <xref:System.Windows.Navigation.NavigationWindow.Source%2A> özelliğini <xref:System.Windows.Navigation.NavigationWindow> öğesi ve ayarlamak "`ExpenseItHome.xaml`".</span><span class="sxs-lookup"><span data-stu-id="325ed-171">Add a <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property to the <xref:System.Windows.Navigation.NavigationWindow> element and set it to "`ExpenseItHome.xaml`".</span></span>

    <span data-ttu-id="325ed-172">Bu ayarlar *`ExpenseItHome.xaml`* ilk olarak uygulama başladığında açılır.</span><span class="sxs-lookup"><span data-stu-id="325ed-172">This sets *`ExpenseItHome.xaml`* to be the first page opened when the application starts.</span></span> 

    <span data-ttu-id="325ed-173">Visual Basic'te XAML. Örneğin:</span><span class="sxs-lookup"><span data-stu-id="325ed-173">Example XAML in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    <span data-ttu-id="325ed-174">C# ve:</span><span class="sxs-lookup"><span data-stu-id="325ed-174">And in C#:</span></span>

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > <span data-ttu-id="325ed-175">Ayrıca **kaynak** özelliğinde **çeşitli** kategorisi **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="325ed-175">You can also set the **Source** property in the **Miscellaneous** category of the **Properties** window.</span></span>
   >
   > ![Özellikler penceresinde Source özelliği](./media/properties-source.png)

1. <span data-ttu-id="325ed-177">Başka bir yeni WPF sayfası projeye ekleyin ve adlandırın *ExpenseReportPage.xaml*::</span><span class="sxs-lookup"><span data-stu-id="325ed-177">Add another new WPF page to the project, and name it *ExpenseReportPage.xaml*::</span></span>

   1. <span data-ttu-id="325ed-178">İçinde **Çözüm Gezgini**, sağ **`ExpenseIt`** projesini düğümünü ve ardından **Ekle** > **sayfa**.</span><span class="sxs-lookup"><span data-stu-id="325ed-178">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="325ed-179">İçinde **Yeni Öğe Ekle** iletişim kutusunda **sayfa (WPF)** şablonu.</span><span class="sxs-lookup"><span data-stu-id="325ed-179">In the **Add New Item** dialog, select the **Page (WPF)** template.</span></span> <span data-ttu-id="325ed-180">Bir ad girin **ExpenseReportPage**ve ardından **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="325ed-180">Enter the name **ExpenseReportPage**, and then select **Add**.</span></span>

    <span data-ttu-id="325ed-181">Bu sayfada, harcama raporlarını seçildiğinde kişinin gösterilir **`ExpenseItHome`** sayfası.</span><span class="sxs-lookup"><span data-stu-id="325ed-181">This page will show the expense report for the person that is selected on the **`ExpenseItHome`** page.</span></span>

1. <span data-ttu-id="325ed-182">Açık *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="325ed-182">Open *ExpenseReportPage.xaml*.</span></span>

1. <span data-ttu-id="325ed-183">Ayarlama <xref:System.Windows.Controls.Page.Title%2A> için "`ExpenseIt - View Expense`".</span><span class="sxs-lookup"><span data-stu-id="325ed-183">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - View Expense`".</span></span>

1. <span data-ttu-id="325ed-184">Ayarlama `DesignHeight` ve `DesignWidth` öğe değerlerini 300 piksel.</span><span class="sxs-lookup"><span data-stu-id="325ed-184">Set the `DesignHeight` and `DesignWidth` element values to 300 pixels.</span></span>

    <span data-ttu-id="325ed-185">*ExpenseReportPage.xaml* artık Visual Basic'te aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="325ed-185">*ExpenseReportPage.xaml* now looks like the following in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    <span data-ttu-id="325ed-186">Ve aşağıdaki gibi C#:</span><span class="sxs-lookup"><span data-stu-id="325ed-186">And like the following in C#:</span></span>

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

1. <span data-ttu-id="325ed-187">Açık *ExpenseItHome.xaml.vb* ve *ExpenseReportPage.xaml.vb*, veya *ExpenseItHome.xaml.cs* ve *ExpenseReportPage.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="325ed-187">Open *ExpenseItHome.xaml.vb* and *ExpenseReportPage.xaml.vb*, or *ExpenseItHome.xaml.cs* and *ExpenseReportPage.xaml.cs*.</span></span>

    <span data-ttu-id="325ed-188">Yeni bir sayfa dosyası oluşturduğunuzda, Visual Studio otomatik olarak oluşturur, *arka plan kod* dosya.</span><span class="sxs-lookup"><span data-stu-id="325ed-188">When you create a new Page file, Visual Studio automatically creates its *code-behind* file.</span></span> <span data-ttu-id="325ed-189">Bu arka plan kod dosyaları, kullanıcı girişine yanıt mantığı işler.</span><span class="sxs-lookup"><span data-stu-id="325ed-189">These code-behind files handle the logic for responding to user input.</span></span>

    <span data-ttu-id="325ed-190">Kodunuz için şunun gibi görünmelidir **`ExpenseItHome`**:</span><span class="sxs-lookup"><span data-stu-id="325ed-190">Your code should look like the following for **`ExpenseItHome`**:</span></span>

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]

    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    <span data-ttu-id="325ed-191">Ve aşağıdaki gibi **ExpenseReportPage**:</span><span class="sxs-lookup"><span data-stu-id="325ed-191">And like the following for **ExpenseReportPage**:</span></span>

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]

    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

1. <span data-ttu-id="325ed-192">Adlandırılmış resim ekleme *watermark.png* projeye.</span><span class="sxs-lookup"><span data-stu-id="325ed-192">Add an image named *watermark.png* to the project.</span></span> <span data-ttu-id="325ed-193">Kendi görüntünüzü oluşturma,'nden örnek kodu dosyasını kopyalayın veya bunu [burada](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span><span class="sxs-lookup"><span data-stu-id="325ed-193">You can create your own image, copy the file from the sample code, or get it [here](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span></span>

    1. <span data-ttu-id="325ed-194">Proje düğümüne sağ tıklayıp **Ekle** > **var olan öğe**, veya basın **Shift**+**Alt** + **A**.</span><span class="sxs-lookup"><span data-stu-id="325ed-194">Right-click on the project node and select **Add** > **Existing Item**, or press **Shift**+**Alt**+**A**.</span></span>

    2. <span data-ttu-id="325ed-195">İçinde **varolan öğeyi Ekle** iletişim kutusunda, dosya filtresi aşağıdaki seçeneklerden birine ayarlayın **tüm dosyaları** veya **görüntü dosyaları**, kullanın ve ardından istediğiniz görüntü dosyasına Gözat **Ekle** .</span><span class="sxs-lookup"><span data-stu-id="325ed-195">In the **Add Existing Item** dialog, set the file filter to either **All Files** or **Image Files**, browse to the image file you want to use, and then select **Add**.</span></span>

## <a name="build-and-run-the-application"></a><span data-ttu-id="325ed-196">Uygulaması derleme ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="325ed-196">Build and run the application</span></span>

1. <span data-ttu-id="325ed-197">Uygulaması derleme ve çalıştırma için basın **F5** veya **hata ayıklamayı Başlat** gelen **hata ayıklama** menüsü.</span><span class="sxs-lookup"><span data-stu-id="325ed-197">To build and run the application, press **F5** or select **Start Debugging** from the **Debug** menu.</span></span>

    <span data-ttu-id="325ed-198">Uygulama ile aşağıdaki çizimde <xref:System.Windows.Navigation.NavigationWindow> düğmeleri:</span><span class="sxs-lookup"><span data-stu-id="325ed-198">The following illustration shows the application with the <xref:System.Windows.Navigation.NavigationWindow> buttons:</span></span>

    ![Uygulama sonra derleyin ve çalıştırın.](./media/walkthrough-my-first-wpf-desktop-application/build-run-application.png)

2. <span data-ttu-id="325ed-200">Visual Studio'ya dönmek için uygulamayı kapatın.</span><span class="sxs-lookup"><span data-stu-id="325ed-200">Close the application to return to Visual Studio.</span></span>

## <a name="create-the-layout"></a><span data-ttu-id="325ed-201">Düzen oluştur</span><span class="sxs-lookup"><span data-stu-id="325ed-201">Create the layout</span></span>

<span data-ttu-id="325ed-202">Düzeni, kullanıcı Arabirimi öğeleri yerleştirmek için sıralı bir yol sağlar ve bir kullanıcı Arabirimi yeniden boyutlandırıldığında boyutunu ve konumunu söz konusu öğelerin da yönetir.</span><span class="sxs-lookup"><span data-stu-id="325ed-202">Layout provides an ordered way to place UI elements, and also manages the size and position of those elements when a UI is resized.</span></span> <span data-ttu-id="325ed-203">Genellikle bir düzen aşağıdaki düzen denetimlerden birini oluşturursunuz:</span><span class="sxs-lookup"><span data-stu-id="325ed-203">You typically create a layout with one of the following layout controls:</span></span>

- <span data-ttu-id="325ed-204"><xref:System.Windows.Controls.Canvas> -İçinde açıkça alt öğeleri tuval alanına göre koordinatlar kullanarak yerleştirebilir bir alan tanımlar.</span><span class="sxs-lookup"><span data-stu-id="325ed-204"><xref:System.Windows.Controls.Canvas> - Defines an area within which you can explicitly position child elements by using coordinates that are relative to the Canvas area.</span></span>
- <span data-ttu-id="325ed-205"><xref:System.Windows.Controls.DockPanel> -Burada, alt öğeleri yatay veya dikey olarak birbirlerine göreli dizebileceğiniz bir alan tanımlar.</span><span class="sxs-lookup"><span data-stu-id="325ed-205"><xref:System.Windows.Controls.DockPanel> - Defines an area where you can arrange child elements either horizontally or vertically, relative to each other.</span></span>
- <span data-ttu-id="325ed-206"><xref:System.Windows.Controls.Grid> -Sütun ve satırlardan oluşan esnek bir kılavuz alanı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="325ed-206"><xref:System.Windows.Controls.Grid> - Defines a flexible grid area that consists of columns and rows.</span></span>
- <span data-ttu-id="325ed-207"><xref:System.Windows.Controls.StackPanel> -Alt öğeleri yatay veya dikey olarak yönlendirilebilir tek bir çizgi yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="325ed-207"><xref:System.Windows.Controls.StackPanel> - Arranges child elements into a single line that can be oriented horizontally or vertically.</span></span>
- <span data-ttu-id="325ed-208"><xref:System.Windows.Controls.VirtualizingStackPanel> -Düzenler ve içerik yatay veya dikey yönlendirilmiş tek bir satırda sanallaştırır.</span><span class="sxs-lookup"><span data-stu-id="325ed-208"><xref:System.Windows.Controls.VirtualizingStackPanel> - Arranges and virtualizes content on a single line that is oriented either horizontally or vertically.</span></span>
- <span data-ttu-id="325ed-209"><xref:System.Windows.Controls.WrapPanel> -Sonraki satır kutusunun kenarında içerik bozucu sağa doğru ardışık konumlarını alt öğeleri kalmadı.</span><span class="sxs-lookup"><span data-stu-id="325ed-209"><xref:System.Windows.Controls.WrapPanel> - Positions child elements in sequential position from left to right, breaking content to the next line at the edge of the containing box.</span></span> <span data-ttu-id="325ed-210">Sonraki sıralama yukarıdan aşağıya veya Yönlendirme özelliğinin değerine bağlı olarak bir soldan sağa ardışık olarak gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="325ed-210">Subsequent ordering happens sequentially from top to bottom or from right to left, depending on the value of the Orientation property.</span></span>

<span data-ttu-id="325ed-211">Bu düzen denetimlerin her birinden alt öğeleri için belirli bir düzen türünü destekler.</span><span class="sxs-lookup"><span data-stu-id="325ed-211">Each of these layout controls supports a particular type of layout for its child elements.</span></span> <span data-ttu-id="325ed-212">`ExpenseIt` sayfaları yeniden boyutlandırılıp boyutlandırılamayacağını ve her sayfanın diğer öğeleri Yatayda ve Dikeyde düzenlenmiş öğelere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="325ed-212">`ExpenseIt` pages can be resized, and each page has elements that are arranged horizontally and vertically alongside other elements.</span></span> <span data-ttu-id="325ed-213">Bu örnekte, <xref:System.Windows.Controls.Grid> uygulama için Düzen öğesi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="325ed-213">In this example, the <xref:System.Windows.Controls.Grid> is used as  layout element for the application.</span></span>

> [!TIP]
> <span data-ttu-id="325ed-214">Hakkında daha fazla bilgi için <xref:System.Windows.Controls.Panel> öğeler, bkz [panellere genel bakış](../controls/panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="325ed-214">For more information about <xref:System.Windows.Controls.Panel> elements, see [Panels overview](../controls/panels-overview.md).</span></span> <span data-ttu-id="325ed-215">Düzen hakkında daha fazla bilgi için bkz. [Düzen](../advanced/layout.md).</span><span class="sxs-lookup"><span data-stu-id="325ed-215">For more information about layout, see [Layout](../advanced/layout.md).</span></span>

<span data-ttu-id="325ed-216">Bu bölümde, bir tek sütunlu tablo üç satır ve 10-piksel kenar boşluğu ile sütun ve satır tanımlara ekleyerek oluşturduğunuz <xref:System.Windows.Controls.Grid> içinde *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="325ed-216">In this section, you create a single-column table with three rows and a 10-pixel margin by adding column and row definitions to the <xref:System.Windows.Controls.Grid> in *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="325ed-217">İçinde *`ExpenseItHome.xaml`* ayarlayın <xref:System.Windows.FrameworkElement.Margin%2A> özelliği <xref:System.Windows.Controls.Grid> ", sol, üst, sağ ve alt kenar boşlukları için karşılık gelen 10,0,10,10 şeklinde", öğe:</span><span class="sxs-lookup"><span data-stu-id="325ed-217">In *`ExpenseItHome.xaml`*, set the <xref:System.Windows.FrameworkElement.Margin%2A> property on the <xref:System.Windows.Controls.Grid> element to "10,0,10,10", which corresponds to left, top, right and bottom margins:</span></span>

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > <span data-ttu-id="325ed-218">Ayrıca **kenar boşluğu** değerler **özellikleri** penceresi altında **Düzen** kategorisi:</span><span class="sxs-lookup"><span data-stu-id="325ed-218">You can also set the **Margin** values in the **Properties** window, under the **Layout** category:</span></span>
   >
   > ![Özellikler penceresinde kenar boşluğu değerleri](./media/properties-margin.png)

2. <span data-ttu-id="325ed-220">Aşağıdaki XAML arasında ekleme <xref:System.Windows.Controls.Grid> etiketleri satır ve sütun tanımları oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="325ed-220">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags to create the row and column definitions:</span></span>

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    <span data-ttu-id="325ed-221"><xref:System.Windows.Controls.RowDefinition.Height%2A> İki satır kümesine <xref:System.Windows.GridLength.Auto%2A>, satırları içeriği temel satırları boyutlandırılır anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="325ed-221">The <xref:System.Windows.Controls.RowDefinition.Height%2A> of two rows is set to <xref:System.Windows.GridLength.Auto%2A>, which means that the rows are sized based on the content in the rows.</span></span> <span data-ttu-id="325ed-222">Varsayılan <xref:System.Windows.Controls.RowDefinition.Height%2A> olduğu <xref:System.Windows.GridUnitType.Star> boyutlandırma, satır yüksekliğini kullanılabilir alanı ağırlıklı oranını olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="325ed-222">The default <xref:System.Windows.Controls.RowDefinition.Height%2A> is <xref:System.Windows.GridUnitType.Star> sizing, which means that the row height is a weighted proportion of the available space.</span></span> <span data-ttu-id="325ed-223">Örneğin her iki satır varsa bir <xref:System.Windows.Controls.RowDefinition.Height%2A> , "\*", sahip oldukları her ikiye kadar kullanılabilir alan olduğundan bir yükseklik.</span><span class="sxs-lookup"><span data-stu-id="325ed-223">For example if two rows each have a <xref:System.Windows.Controls.RowDefinition.Height%2A> of "\*", they each have a height that is half of the available space.</span></span>

    <span data-ttu-id="325ed-224"><xref:System.Windows.Controls.Grid> Artık aşağıdaki XAML içermelidir:</span><span class="sxs-lookup"><span data-stu-id="325ed-224">Your <xref:System.Windows.Controls.Grid> should now contain the following XAML:</span></span>

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a><span data-ttu-id="325ed-225">Denetimler ekleme</span><span class="sxs-lookup"><span data-stu-id="325ed-225">Add controls</span></span>

<span data-ttu-id="325ed-226">Bu bölümde, giriş sayfası, harcama raporu görüntülemek için tek bir kişi seçtiğiniz kişi listesini gösteren kullanıcı Arabirimi güncelleştireceksiniz.</span><span class="sxs-lookup"><span data-stu-id="325ed-226">In this section, you'll update the home page UI to show a list of people, where you select one person to display their expense report.</span></span> <span data-ttu-id="325ed-227">Kullanıcıların uygulamanızla etkileşmesini UI nesneleri denetimlerdir.</span><span class="sxs-lookup"><span data-stu-id="325ed-227">Controls are UI objects that allow users to interact with your application.</span></span> <span data-ttu-id="325ed-228">Daha fazla bilgi için [denetimleri](../controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="325ed-228">For more information, see [Controls](../controls/index.md).</span></span>

<span data-ttu-id="325ed-229">Bu kullanıcı Arabirimi oluşturmak için aşağıdaki öğelere ekleyeceksiniz *`ExpenseItHome.xaml`*:</span><span class="sxs-lookup"><span data-stu-id="325ed-229">To create this UI, you'll add the following elements to *`ExpenseItHome.xaml`*:</span></span>

- <span data-ttu-id="325ed-230">A <xref:System.Windows.Controls.ListBox> (için kişi listesi).</span><span class="sxs-lookup"><span data-stu-id="325ed-230">A <xref:System.Windows.Controls.ListBox> (for the list of people).</span></span>
- <span data-ttu-id="325ed-231">A <xref:System.Windows.Controls.Label> (için liste başlığı).</span><span class="sxs-lookup"><span data-stu-id="325ed-231">A <xref:System.Windows.Controls.Label> (for the list header).</span></span>
- <span data-ttu-id="325ed-232">A <xref:System.Windows.Controls.Button> (listede seçilen kişi için harcama raporlarını görüntülemek için tıklayın için).</span><span class="sxs-lookup"><span data-stu-id="325ed-232">A <xref:System.Windows.Controls.Button> (to click to view the expense report for the person that is selected in the list).</span></span>

<span data-ttu-id="325ed-233">Her denetim bir satırda yerleştirilir <xref:System.Windows.Controls.Grid> ayarlayarak <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> ekli özellik.</span><span class="sxs-lookup"><span data-stu-id="325ed-233">Each control is placed in a row of the <xref:System.Windows.Controls.Grid> by setting the <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> attached property.</span></span> <span data-ttu-id="325ed-234">Ekli özellikler hakkında daha fazla bilgi için bkz. [ekli özelliklere genel bakış](../advanced/attached-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="325ed-234">For more information about attached properties, see [Attached Properties Overview](../advanced/attached-properties-overview.md).</span></span>

1. <span data-ttu-id="325ed-235">İçinde *`ExpenseItHome.xaml`*, aşağıdaki XAML bir yerde arasında ekleme <xref:System.Windows.Controls.Grid> etiketler:</span><span class="sxs-lookup"><span data-stu-id="325ed-235">In *`ExpenseItHome.xaml`*, add the following XAML somewhere between the <xref:System.Windows.Controls.Grid> tags:</span></span>

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > <span data-ttu-id="325ed-236">Denetimlere sürükleyerek de oluşturabilirsiniz **araç kutusu** tasarım penceresini ve özelliklerini ayarlayarak ardından penceresinden **özellikleri** penceresi.</span><span class="sxs-lookup"><span data-stu-id="325ed-236">You can also create the controls by dragging them from the **Toolbox** window onto the design window, and then setting their properties in the **Properties** window.</span></span>

2. <span data-ttu-id="325ed-237">Derleme ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="325ed-237">Build and run the application.</span></span>

    <span data-ttu-id="325ed-238">Aşağıdaki çizim, oluşturduğunuz denetimleri gösterir:</span><span class="sxs-lookup"><span data-stu-id="325ed-238">The following illustration shows the controls you created:</span></span>

![ExpenseIt örnek adlarının bir listesini gösteren ekran görüntüsü](./media/walkthrough-my-first-wpf-desktop-application/add-application-controls.png)

## <a name="add-an-image-and-a-title"></a><span data-ttu-id="325ed-240">Resim ve Başlık Ekle</span><span class="sxs-lookup"><span data-stu-id="325ed-240">Add an image and a title</span></span>

<span data-ttu-id="325ed-241">Bu bölümde, giriş sayfası kullanıcı Arabirimi, görüntü ve sayfa başlığı ile güncelleştireceksiniz.</span><span class="sxs-lookup"><span data-stu-id="325ed-241">In this section, you'll update the home page UI with an image and a page title.</span></span>

1. <span data-ttu-id="325ed-242">İçinde *`ExpenseItHome.xaml`*, başka bir sütuna eklemek <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> sabit ile <xref:System.Windows.Controls.ColumnDefinition.Width%2A> 230 piksel:</span><span class="sxs-lookup"><span data-stu-id="325ed-242">In *`ExpenseItHome.xaml`*, add another column to the <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> with a fixed <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of 230 pixels:</span></span>

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=52-55)]

2. <span data-ttu-id="325ed-243">Başka bir satır <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, toplam dört satır için:</span><span class="sxs-lookup"><span data-stu-id="325ed-243">Add another row to the <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, for a total of four rows:</span></span>

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=57-62)]

3. <span data-ttu-id="325ed-244">Denetimleri ayarlayarak ikinci sütuna Taşı <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> özelliği 1 her üç denetimleri (Kenarlık, liste kutusu ve düğme).</span><span class="sxs-lookup"><span data-stu-id="325ed-244">Move the controls to the second column by setting the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property to 1 in each of the three controls (Border, ListBox, and Button).</span></span>

4. <span data-ttu-id="325ed-245">Her denetim artırılarak bir satır aşağı taşı, <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> her üç denetimleri (Kenarlık, liste kutusu ve düğme) ve kenarlık öğesinin 1 değeriyle.</span><span class="sxs-lookup"><span data-stu-id="325ed-245">Move each control down a row by incrementing its <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> value by 1 for each of the three controls (Border, ListBox, and Button) and for the Border element.</span></span>

   <span data-ttu-id="325ed-246">XAML üç denetim için aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="325ed-246">The XAML for the three controls now looks like the following:</span></span>

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

5. <span data-ttu-id="325ed-247">Ayarlama <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> özelliğini *watermark.png* görüntü dosyası, aşağıdaki XAML herhangi bir yere arasında ekleyerek `<Grid>` ve `</Grid>` etiketler:</span><span class="sxs-lookup"><span data-stu-id="325ed-247">Set the <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> property to the *watermark.png* image file, by adding the following XAML anywhere between the `<Grid>` and `</Grid>` tags:</span></span>

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

6. <span data-ttu-id="325ed-248">Önce <xref:System.Windows.Controls.Border> öğe, Ekle bir <xref:System.Windows.Controls.Label> "Harcama Raporu Görüntüle" içeriğe sahip.</span><span class="sxs-lookup"><span data-stu-id="325ed-248">Before the <xref:System.Windows.Controls.Border> element, add a <xref:System.Windows.Controls.Label> with the content "View Expense Report".</span></span> <span data-ttu-id="325ed-249">Bu sayfa başlığının etiketidir.</span><span class="sxs-lookup"><span data-stu-id="325ed-249">This label is the title of the page.</span></span>

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

7. <span data-ttu-id="325ed-250">Derleme ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="325ed-250">Build and run the application.</span></span>

<span data-ttu-id="325ed-251">Hangi yeni eklediğiniz sonucu aşağıda gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="325ed-251">The following illustration shows the results of what you just added:</span></span>

![Yeni görüntü arka plan ve sayfa başlığını gösteren ExpenseIt örnek ekran görüntüsü](./media/walkthrough-my-first-wpf-desktop-application/add-application-image-title.png)

## <a name="add-code-to-handle-events"></a><span data-ttu-id="325ed-253">Olayları işlemek için kod ekleyin</span><span class="sxs-lookup"><span data-stu-id="325ed-253">Add code to handle events</span></span>

1. <span data-ttu-id="325ed-254">İçinde *`ExpenseItHome.xaml`*, ekleme bir <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay işleyicisine <xref:System.Windows.Controls.Button> öğesi.</span><span class="sxs-lookup"><span data-stu-id="325ed-254">In *`ExpenseItHome.xaml`*, add a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to the <xref:System.Windows.Controls.Button> element.</span></span> <span data-ttu-id="325ed-255">Daha fazla bilgi için [nasıl yapılır: Basit olay işleyicisi oluşturun](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="325ed-255">For more information, see [How to: Create a simple event handler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span></span>

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

2. <span data-ttu-id="325ed-256">Açık *`ExpenseItHome.xaml.vb`* veya *`ExpenseItHome.xaml.cs`*.</span><span class="sxs-lookup"><span data-stu-id="325ed-256">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

3. <span data-ttu-id="325ed-257">Aşağıdaki kodu ekleyin `ExpenseItHome` sınıfı bir düğme eklemek için tıklama olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="325ed-257">Add the following code to the `ExpenseItHome` class to add a button click event handler.</span></span> <span data-ttu-id="325ed-258">Olay işleyicisi açılır **ExpenseReportPage** sayfası.</span><span class="sxs-lookup"><span data-stu-id="325ed-258">The event handler opens the **ExpenseReportPage** page.</span></span>

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a><span data-ttu-id="325ed-259">ExpenseReportPage için kullanıcı Arabirimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="325ed-259">Create the UI for ExpenseReportPage</span></span>

<span data-ttu-id="325ed-260">*ExpenseReportPage.xaml* seçili kişi için harcama raporlarını görüntüler **`ExpenseItHome`** sayfası.</span><span class="sxs-lookup"><span data-stu-id="325ed-260">*ExpenseReportPage.xaml* displays the expense report for the person that's selected on the **`ExpenseItHome`** page.</span></span> <span data-ttu-id="325ed-261">Bu bölümde, kullanıcı Arabiriminde oluşturacaksınız **ExpenseReportPage**.</span><span class="sxs-lookup"><span data-stu-id="325ed-261">In this section, you'll create the UI for **ExpenseReportPage**.</span></span> <span data-ttu-id="325ed-262">Ayrıca, arka plan ekleyebilir ve çeşitli kullanıcı Arabirimi öğeleri için renk dolgu.</span><span class="sxs-lookup"><span data-stu-id="325ed-262">You'll also add background and fill colors to the various UI elements.</span></span>

1. <span data-ttu-id="325ed-263">Açık *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="325ed-263">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="325ed-264">Aşağıdaki XAML arasında ekleme <xref:System.Windows.Controls.Grid> etiketler:</span><span class="sxs-lookup"><span data-stu-id="325ed-264">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags:</span></span>

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    <span data-ttu-id="325ed-265">Bu kullanıcı arabirimini benzer *`ExpenseItHome.xaml`* rapor verilerini görüntülenen dışında bir <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="325ed-265">This UI is similar to *`ExpenseItHome.xaml`*, except the report data is displayed in a <xref:System.Windows.Controls.DataGrid>.</span></span>

3. <span data-ttu-id="325ed-266">Derleme ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="325ed-266">Build and run the application.</span></span>

4. <span data-ttu-id="325ed-267">Seçin **görünümü** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="325ed-267">Select the **View** button.</span></span>

    <span data-ttu-id="325ed-268">Harcama Raporu sayfası görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="325ed-268">The expense report page appears.</span></span> <span data-ttu-id="325ed-269">Ayrıca geri gezinme düğmesi etkinleştirilir dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="325ed-269">Also notice that the back navigation button is enabled.</span></span>

<span data-ttu-id="325ed-270">Eklenen kullanıcı Arabirimi öğeleri aşağıdaki çizimde *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="325ed-270">The following illustration shows the UI elements added to *ExpenseReportPage.xaml*.</span></span>

![ExpenseReportPage için oluşturduğunuz kullanıcı arabirimini gösteren ExpenseIt örnek ekran görüntüsü.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

## <a name="style-controls"></a><span data-ttu-id="325ed-272">Stil denetimleri</span><span class="sxs-lookup"><span data-stu-id="325ed-272">Style controls</span></span>

<span data-ttu-id="325ed-273">Çeşitli öğelerin görünümünü genellikle bir kullanıcı arabiriminde aynı türdeki tüm öğeler için aynıdır.</span><span class="sxs-lookup"><span data-stu-id="325ed-273">The appearance of various elements is often the same for all elements of the same type in a UI.</span></span> <span data-ttu-id="325ed-274">Kullanıcı Arabirimi kullanan [stilleri](../controls/styling-and-templating.md) görünümleri arasında birden çok öğe yeniden kullanılabilir hale getirmek için.</span><span class="sxs-lookup"><span data-stu-id="325ed-274">UI uses [styles](../controls/styling-and-templating.md) to make appearances reusable across multiple elements.</span></span> <span data-ttu-id="325ed-275">Yeniden kullanılırlığı XAML oluşturulmasını ve yönetimini basitleştirmeye yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="325ed-275">The reusability of styles helps to simplify XAML creation and management.</span></span> <span data-ttu-id="325ed-276">Bu bölümde, stiller, önceki adımlarda tanımlanan öğe başına özniteliklerini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="325ed-276">This section replaces the per-element attributes that were defined in previous steps with styles.</span></span>

1. <span data-ttu-id="325ed-277">Açık *Application.xaml* veya *App.xaml*.</span><span class="sxs-lookup"><span data-stu-id="325ed-277">Open *Application.xaml* or *App.xaml*.</span></span>

2. <span data-ttu-id="325ed-278">Aşağıdaki XAML arasında ekleme <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> etiketler:</span><span class="sxs-lookup"><span data-stu-id="325ed-278">Add the following XAML between the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tags:</span></span>

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    <span data-ttu-id="325ed-279">Bu XAML aşağıdaki stilleri ekler:</span><span class="sxs-lookup"><span data-stu-id="325ed-279">This XAML adds the following styles:</span></span>

    - <span data-ttu-id="325ed-280">`headerTextStyle`: Sayfa başlığı biçimlendirmek için <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="325ed-280">`headerTextStyle`: To format the page title <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="325ed-281">`labelStyle`: Biçimlendirilecek <xref:System.Windows.Controls.Label> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="325ed-281">`labelStyle`: To format the <xref:System.Windows.Controls.Label> controls.</span></span>

    - <span data-ttu-id="325ed-282">`columnHeaderStyle`: Biçimlendirilecek <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span><span class="sxs-lookup"><span data-stu-id="325ed-282">`columnHeaderStyle`: To format the <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span></span>

    - <span data-ttu-id="325ed-283">`listHeaderStyle`: List üstbilgisi biçimlendirmek için <xref:System.Windows.Controls.Border> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="325ed-283">`listHeaderStyle`: To format the list header <xref:System.Windows.Controls.Border> controls.</span></span>

    - <span data-ttu-id="325ed-284">`listHeaderTextStyle`: List üstbilgisi biçimlendirmek için <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="325ed-284">`listHeaderTextStyle`: To format the list header <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="325ed-285">`buttonStyle`: Biçimlendirilecek <xref:System.Windows.Controls.Button> üzerinde `ExpenseItHome.xaml`.</span><span class="sxs-lookup"><span data-stu-id="325ed-285">`buttonStyle`: To format the <xref:System.Windows.Controls.Button> on `ExpenseItHome.xaml`.</span></span>

    <span data-ttu-id="325ed-286">Stilleri kaynakları ve alt olduğunu fark <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> özellik öğesi.</span><span class="sxs-lookup"><span data-stu-id="325ed-286">Notice that the styles are resources and children of the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> property element.</span></span> <span data-ttu-id="325ed-287">Bu konumda, stilleri bir uygulamadaki tüm öğelere uygulanır.</span><span class="sxs-lookup"><span data-stu-id="325ed-287">In this location, the styles are applied to all the elements in an application.</span></span> <span data-ttu-id="325ed-288">Bir .NET uygulamasında kaynakları kullanma örneği için bkz: [kullanım uygulama kaynaklarını](../advanced/how-to-use-application-resources.md).</span><span class="sxs-lookup"><span data-stu-id="325ed-288">For an example of using resources in a .NET app, see [Use Application Resources](../advanced/how-to-use-application-resources.md).</span></span>

3. <span data-ttu-id="325ed-289">İçinde *`ExpenseItHome.xaml`*, arasındaki her şeyi değiştirin <xref:System.Windows.Controls.Grid> aşağıdaki XAML ile öğeleri:</span><span class="sxs-lookup"><span data-stu-id="325ed-289">In *`ExpenseItHome.xaml`*, replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    <span data-ttu-id="325ed-290">Gibi özellikler <xref:System.Windows.VerticalAlignment> ve <xref:System.Windows.Media.FontFamily> her denetimin görünümünü tanımlamak kaldırılır ve stilleri uygulayarak değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="325ed-290">The properties such as <xref:System.Windows.VerticalAlignment> and <xref:System.Windows.Media.FontFamily> that define the look of each control are removed and replaced by applying the styles.</span></span> <span data-ttu-id="325ed-291">Örneğin, `headerTextStyle` harcama raporu görünümü"için" uygulanan <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="325ed-291">For example, the `headerTextStyle` is applied to the "View Expense Report" <xref:System.Windows.Controls.Label>.</span></span>

4. <span data-ttu-id="325ed-292">Açık *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="325ed-292">Open *ExpenseReportPage.xaml*.</span></span>

5. <span data-ttu-id="325ed-293">Arasındaki her şeyi değiştirin <xref:System.Windows.Controls.Grid> aşağıdaki XAML ile öğeleri:</span><span class="sxs-lookup"><span data-stu-id="325ed-293">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    <span data-ttu-id="325ed-294">Bu XAML stilleri ekler <xref:System.Windows.Controls.Label> ve <xref:System.Windows.Controls.Border> öğeleri.</span><span class="sxs-lookup"><span data-stu-id="325ed-294">This XAML adds styles to the <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Border> elements.</span></span>

6. <span data-ttu-id="325ed-295">Derleme ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="325ed-295">Build and run the application.</span></span> <span data-ttu-id="325ed-296">Pencere görünümü önceden aynıdır.</span><span class="sxs-lookup"><span data-stu-id="325ed-296">The window appearance is the same as previously.</span></span>

    ![Son bölümde olduğu gibi aynı görünümle ExpenseIt örnek ekran görüntüsü.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

7. <span data-ttu-id="325ed-298">Visual Studio'ya dönmek için uygulamayı kapatın.</span><span class="sxs-lookup"><span data-stu-id="325ed-298">Close the application to return to Visual Studio.</span></span>

## <a name="bind-data-to-a-control"></a><span data-ttu-id="325ed-299">Veriyi denetime bağlama</span><span class="sxs-lookup"><span data-stu-id="325ed-299">Bind data to a control</span></span>

<span data-ttu-id="325ed-300">Bu bölümde, çeşitli denetimlere bağlı XML verileri oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="325ed-300">In this section, you'll create the XML data that is bound to various controls.</span></span>

1. <span data-ttu-id="325ed-301">İçinde *`ExpenseItHome.xaml`*, açılış <xref:System.Windows.Controls.Grid> öğesi oluşturmak için aşağıdaki XAML ekleme bir <xref:System.Windows.Data.XmlDataProvider> her kişi için veri içeren:</span><span class="sxs-lookup"><span data-stu-id="325ed-301">In *`ExpenseItHome.xaml`*, after the opening <xref:System.Windows.Controls.Grid> element, add the following XAML to create an <xref:System.Windows.Data.XmlDataProvider> that contains the data for each person:</span></span>

    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,16-40,49)]

    <span data-ttu-id="325ed-302">Veri olarak oluşturulan bir <xref:System.Windows.Controls.Grid> kaynak.</span><span class="sxs-lookup"><span data-stu-id="325ed-302">The data is created as a <xref:System.Windows.Controls.Grid> resource.</span></span> <span data-ttu-id="325ed-303">Normalde bu verilerin bir dosya olarak yüklenmesi, ancak kolaylık olması için satır içi veriler eklenir.</span><span class="sxs-lookup"><span data-stu-id="325ed-303">Normally this data would be loaded as a file, but for simplicity the data is added inline.</span></span>

2. <span data-ttu-id="325ed-304">İçinde `<Grid.Resources>` öğesi, aşağıdaki `<xref:System.Windows.DataTemplate>` içinde verilerin nasıl görüntüleneceğini tanımlar <xref:System.Windows.Controls.ListBox>, sonra `<XmlDataProvider>` öğesi:</span><span class="sxs-lookup"><span data-stu-id="325ed-304">Within the `<Grid.Resources>` element, add the following `<xref:System.Windows.DataTemplate>` element, which defines how to display the data in the <xref:System.Windows.Controls.ListBox>, after the `<XmlDataProvider>` element:</span></span>

    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,43-46,49)]

    <span data-ttu-id="325ed-305">Veri şablonları hakkında daha fazla bilgi için bkz. [veri şablonu oluşturmaya genel bakış](../data/data-templating-overview.md).</span><span class="sxs-lookup"><span data-stu-id="325ed-305">For more information about data templates, see [Data templating overview](../data/data-templating-overview.md).</span></span>

3. <span data-ttu-id="325ed-306">Varolan <xref:System.Windows.Controls.ListBox> aşağıdaki XAML ile:</span><span class="sxs-lookup"><span data-stu-id="325ed-306">Replace the existing <xref:System.Windows.Controls.ListBox> with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    <span data-ttu-id="325ed-307">Bu XAML bağlar <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliği <xref:System.Windows.Controls.ListBox> veri kaynağı ve veri şablonu olarak geçerli <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span><span class="sxs-lookup"><span data-stu-id="325ed-307">This XAML binds the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to the data source and applies the data template as the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span></span>

## <a name="connect-data-to-controls"></a><span data-ttu-id="325ed-308">Denetimlere veri bağlama</span><span class="sxs-lookup"><span data-stu-id="325ed-308">Connect data to controls</span></span>

<span data-ttu-id="325ed-309">Ardından, seçili adını almak için kod ekleyeceksiniz **`ExpenseItHome`** sayfasında ve oluşturucusuna iletmektir **ExpenseReportPage**.</span><span class="sxs-lookup"><span data-stu-id="325ed-309">Next, you'll add code to retrieve the name that's selected on the **`ExpenseItHome`** page and pass it to the constructor of **ExpenseReportPage**.</span></span> <span data-ttu-id="325ed-310">**ExpenseReportPage** denetimlerin ne tanımlanır geçirilen öğe ile veri bağlamını ayarlar içinde *ExpenseReportPage.xaml* bağlayın.</span><span class="sxs-lookup"><span data-stu-id="325ed-310">**ExpenseReportPage** sets its data context with the passed item, which is what the controls defined in *ExpenseReportPage.xaml* bind to.</span></span>

1. <span data-ttu-id="325ed-311">Açık *ExpenseReportPage.xaml.vb* veya *ExpenseReportPage.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="325ed-311">Open *ExpenseReportPage.xaml.vb* or *ExpenseReportPage.xaml.cs*.</span></span>

2. <span data-ttu-id="325ed-312">Seçilen kişiyi harcama raporu verilerini geçirebilirsiniz. Bu nedenle bir nesne alan bir oluşturucu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="325ed-312">Add a constructor that takes an object so you can pass the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. <span data-ttu-id="325ed-313">Açık *`ExpenseItHome.xaml.vb`* veya *`ExpenseItHome.xaml.cs`*.</span><span class="sxs-lookup"><span data-stu-id="325ed-313">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

4. <span data-ttu-id="325ed-314">Değişiklik <xref:System.Windows.Controls.Primitives.ButtonBase.Click> seçilen kişiyi harcama raporu verilerini geçirme yeni oluşturucuyu çağırmak için olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="325ed-314">Change the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to call the new constructor passing the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a><span data-ttu-id="325ed-315">Veri şablonları ile stil verileri</span><span class="sxs-lookup"><span data-stu-id="325ed-315">Style data with data templates</span></span>

<span data-ttu-id="325ed-316">Bu bölümde, veri şablonları kullanarak verilere bağlı listeler her öğe için kullanıcı Arabirimi güncelleştireceksiniz.</span><span class="sxs-lookup"><span data-stu-id="325ed-316">In this section, you'll update the UI for each item in the data-bound lists by using data templates.</span></span>

1. <span data-ttu-id="325ed-317">Açık *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="325ed-317">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="325ed-318">"Name" ve "Departman" içeriğini bağlama <xref:System.Windows.Controls.Label> uygun veri öğelerine kaynak özelliği.</span><span class="sxs-lookup"><span data-stu-id="325ed-318">Bind the content of the "Name" and "Department" <xref:System.Windows.Controls.Label> elements to the appropriate data source property.</span></span> <span data-ttu-id="325ed-319">Veri bağlama hakkında daha fazla bilgi için bkz. [veri bağlamaya genel bakış](../data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="325ed-319">For more information about data binding, see [Data binding overview](../data/data-binding-overview.md).</span></span>

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. <span data-ttu-id="325ed-320">Açılış <xref:System.Windows.Controls.Grid> öğesi, harcama raporu verilerini görüntülemek nasıl tanımlamak aşağıdaki veri şablonları ekleyin:</span><span class="sxs-lookup"><span data-stu-id="325ed-320">After the opening <xref:System.Windows.Controls.Grid> element, add the following data templates, which define how to display the expense report data:</span></span>

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. <span data-ttu-id="325ed-321">Değiştirin <xref:System.Windows.Controls.DataGridTextColumn> öğelerle <xref:System.Windows.Controls.DataGridTemplateColumn> altında <xref:System.Windows.Controls.DataGrid> öğesi ve şablonlar uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="325ed-321">Replace the <xref:System.Windows.Controls.DataGridTextColumn> elements with <xref:System.Windows.Controls.DataGridTemplateColumn> under the <xref:System.Windows.Controls.DataGrid> element and apply the templates to them.</span></span>

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. <span data-ttu-id="325ed-322">Derleme ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="325ed-322">Build and run the application.</span></span>

6. <span data-ttu-id="325ed-323">Bir kişi seçin ve ardından **görünümü** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="325ed-323">Select a person and then select the **View** button.</span></span>

<span data-ttu-id="325ed-324">Her iki sayfaları aşağıdaki resimde gösterilmektedir `ExpenseIt` uygulama denetimleri, düzeni, stiller, veri bağlama ve uygulanan veri şablonları:</span><span class="sxs-lookup"><span data-stu-id="325ed-324">The following illustration shows both pages of the `ExpenseIt` application with controls, layout, styles, data binding, and data templates applied:</span></span>

![Her iki sayfa adları listesi ve bir harcama raporu gösteren uygulama.](./media/walkthrough-my-first-wpf-desktop-application/application-data-templates.png)

> [!NOTE]
> <span data-ttu-id="325ed-326">Bu örnek, belirli bir WPF özelliğini gösterir ve güvenlik, yerelleştirme ve erişilebilirlik gibi şeyler için tüm en iyi uygulamaları izleyin değil.</span><span class="sxs-lookup"><span data-stu-id="325ed-326">This sample demonstrates a specific feature of WPF and doesn't follow all best practices for things like security, localization, and accessibility.</span></span> <span data-ttu-id="325ed-327">WPF ve .NET uygulama geliştirme en iyi yöntemler ilişkin kapsamlı bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="325ed-327">For comprehensive coverage of WPF and the .NET app development best practices, see the following topics:</span></span>
>
> - [<span data-ttu-id="325ed-328">Erişilebilirlik</span><span class="sxs-lookup"><span data-stu-id="325ed-328">Accessibility</span></span>](../../ui-automation/accessibility-best-practices.md)
>
> - [<span data-ttu-id="325ed-329">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="325ed-329">Security</span></span>](../security-wpf.md)
>
> - [<span data-ttu-id="325ed-330">WPF Genelleştirme ve yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="325ed-330">WPF globalization and localization</span></span>](../advanced/wpf-globalization-and-localization-overview.md)
>
> - [<span data-ttu-id="325ed-331">WPF Performans</span><span class="sxs-lookup"><span data-stu-id="325ed-331">WPF performance</span></span>](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a><span data-ttu-id="325ed-332">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="325ed-332">Next steps</span></span>

<span data-ttu-id="325ed-333">Bu izlenecek yolda çeşitli teknikler Windows Presentation Foundation (WPF) kullanarak bir kullanıcı Arabirimi oluşturma hakkında bilgi edindiniz.</span><span class="sxs-lookup"><span data-stu-id="325ed-333">In this walkthrough you learned a number of techniques for creating a UI using Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="325ed-334">Artık verilere bağlı .NET uygulaması yapı taşları ilgili temel bilgilere sahipsiniz.</span><span class="sxs-lookup"><span data-stu-id="325ed-334">You should now have a basic understanding of the building blocks of a data-bound .NET app.</span></span> <span data-ttu-id="325ed-335">WPF mimarisi ve programlama modelleri hakkında daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="325ed-335">For more information about the WPF architecture and programming models, see the following topics:</span></span>

- [<span data-ttu-id="325ed-336">WPF mimarisi</span><span class="sxs-lookup"><span data-stu-id="325ed-336">WPF architecture</span></span>](../advanced/wpf-architecture.md)
- [<span data-ttu-id="325ed-337">XAML genel bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="325ed-337">XAML overview (WPF)</span></span>](../advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="325ed-338">Bağımlılık özelliklerine genel bakış</span><span class="sxs-lookup"><span data-stu-id="325ed-338">Dependency properties overview</span></span>](../advanced/dependency-properties-overview.md)
- [<span data-ttu-id="325ed-339">Düzen</span><span class="sxs-lookup"><span data-stu-id="325ed-339">Layout</span></span>](../advanced/layout.md)

<span data-ttu-id="325ed-340">Uygulamaları oluşturma hakkında daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="325ed-340">For more information about creating applications, see the following topics:</span></span>

- [<span data-ttu-id="325ed-341">Uygulama geliştirme</span><span class="sxs-lookup"><span data-stu-id="325ed-341">Application development</span></span>](../app-development/index.md)
- [<span data-ttu-id="325ed-342">Denetimler</span><span class="sxs-lookup"><span data-stu-id="325ed-342">Controls</span></span>](../controls/index.md)
- [<span data-ttu-id="325ed-343">Veri bağlamaya genel bakış</span><span class="sxs-lookup"><span data-stu-id="325ed-343">Data binding overview</span></span>](../data/data-binding-overview.md)
- [<span data-ttu-id="325ed-344">Grafikler ve multimedya</span><span class="sxs-lookup"><span data-stu-id="325ed-344">Graphics and multimedia</span></span>](../graphics-multimedia/index.md)
- [<span data-ttu-id="325ed-345">WPF'deki Belgeler</span><span class="sxs-lookup"><span data-stu-id="325ed-345">Documents in WPF</span></span>](../advanced/documents-in-wpf.md)

## <a name="see-also"></a><span data-ttu-id="325ed-346">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="325ed-346">See also</span></span>

- [<span data-ttu-id="325ed-347">Panellere genel bakış</span><span class="sxs-lookup"><span data-stu-id="325ed-347">Panels overview</span></span>](../controls/panels-overview.md)
- [<span data-ttu-id="325ed-348">Veri şablonu oluşturmaya genel bakış</span><span class="sxs-lookup"><span data-stu-id="325ed-348">Data templating overview</span></span>](../data/data-templating-overview.md)
- [<span data-ttu-id="325ed-349">Bir WPF uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="325ed-349">Build a WPF application</span></span>](../app-development/building-a-wpf-application-wpf.md)
- [<span data-ttu-id="325ed-350">Stilleri ve şablonları</span><span class="sxs-lookup"><span data-stu-id="325ed-350">Styles and templates</span></span>](../controls/styles-and-templates.md)
