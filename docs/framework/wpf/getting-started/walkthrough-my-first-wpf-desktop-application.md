---
title: Visual Studio 2019'da ilk WPF uygulamanızı oluşturun - .NET Framework
titleSuffix: ''
ms.date: 09/06/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
ms.topic: tutorial
ms.custom: mvc,vs-dotnet
ms.openlocfilehash: facb9ebebd9ce1904886a946277185ac2c2e4bc4
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463919"
---
# <a name="tutorial-create-your-first-wpf-application-in-visual-studio-2019"></a><span data-ttu-id="05d81-102">Öğretici: Visual Studio 2019'da ilk WPF uygulamanızı oluşturun</span><span class="sxs-lookup"><span data-stu-id="05d81-102">Tutorial: Create your first WPF application in Visual Studio 2019</span></span>

<span data-ttu-id="05d81-103">Bu makalede, çoğu WPF uygulamasında ortak olan öğeleri içeren bir Windows Presentation Foundation (WPF) masaüstü uygulaması nın nasıl geliştirilildiği gösterilmektedir: Genişletilebilir Uygulama Biçimlendirme Dili (XAML) biçimlendirme, kod arkası, uygulama tanımları, denetimler, düzen, veri bağlama ve stilleri.</span><span class="sxs-lookup"><span data-stu-id="05d81-103">This article shows you how to develop a Windows Presentation Foundation (WPF) desktop application that includes the elements that are common to most WPF applications: Extensible Application Markup Language (XAML) markup, code-behind, application definitions, controls, layout, data binding, and styles.</span></span> <span data-ttu-id="05d81-104">Uygulamayı geliştirmek için Visual Studio'yu kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="05d81-104">To develop the application, you'll use Visual Studio.</span></span>

<span data-ttu-id="05d81-105">Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="05d81-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="05d81-106">Bir WPF projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="05d81-106">Create a WPF project.</span></span>
> - <span data-ttu-id="05d81-107">Uygulamanın kullanıcı arabiriminin (UI) görünümünü tasarlamak için XAML'yi kullanın.</span><span class="sxs-lookup"><span data-stu-id="05d81-107">Use XAML to design the appearance of the application's user interface (UI).</span></span>
> - <span data-ttu-id="05d81-108">Uygulamanın davranışını oluşturmak için kod yazın.</span><span class="sxs-lookup"><span data-stu-id="05d81-108">Write code to build the application's behavior.</span></span>
> - <span data-ttu-id="05d81-109">Uygulamayı yönetmek için bir uygulama tanımı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="05d81-109">Create an application definition to manage the application.</span></span>
> - <span data-ttu-id="05d81-110">Denetimler ekleyin ve uygulama kullanıcı yı oluşturmak için düzen oluşturun.</span><span class="sxs-lookup"><span data-stu-id="05d81-110">Add controls and create the layout to compose the application UI.</span></span>
> - <span data-ttu-id="05d81-111">Uygulamanın Kullanıcı Arabirimi boyunca tutarlı bir görünüm için stiller oluşturun.</span><span class="sxs-lookup"><span data-stu-id="05d81-111">Create styles for a consistent appearance throughout the application's UI.</span></span>
> - <span data-ttu-id="05d81-112">Kullanıcı UI'yi verilere bağlayın, hem veri kullanıcı larını doldurmak hem de verileri ve Kullanıcı Yı'nı eşitlemek için.</span><span class="sxs-lookup"><span data-stu-id="05d81-112">Bind the UI to data, both to populate the UI from data and to keep the data and UI synchronized.</span></span>

<span data-ttu-id="05d81-113">Öğreticinin sonunda, kullanıcıların seçilen kişilerin gider raporlarını görüntülemesine olanak tanıyan bağımsız bir Windows uygulaması oluşturmuş olacaksınız.</span><span class="sxs-lookup"><span data-stu-id="05d81-113">By the end of the tutorial, you'll have built a standalone Windows application that allows users to view expense reports for selected people.</span></span> <span data-ttu-id="05d81-114">Uygulama, tarayıcı tarzı bir pencerede barındırılan birkaç WPF sayfalarından oluşur.</span><span class="sxs-lookup"><span data-stu-id="05d81-114">The application is composed of several WPF pages that are hosted in a browser-style window.</span></span>

> [!TIP]
> <span data-ttu-id="05d81-115">Bu öğreticide kullanılan örnek kod, [Öğretici WPF Uygulama Örnek Kodu'nda](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp)hem Visual Basic hem de C# için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="05d81-115">The sample code that is used in this tutorial is available for both Visual Basic and C# at [Tutorial WPF App Sample Code](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span></span>
>
> <span data-ttu-id="05d81-116">Bu sayfanın üstündeki dil seçiciyi kullanarak örnek kodun kod dilini C# ve Visual Basic arasında geçiş yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05d81-116">You can toggle the code language of the sample code between C# and Visual Basic by using the language selector on top of this page.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="05d81-117">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="05d81-117">Prerequisites</span></span>

- <span data-ttu-id="05d81-118">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ile **.NET masaüstü geliştirme** iş yükü yüklendi.</span><span class="sxs-lookup"><span data-stu-id="05d81-118">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET desktop development** workload installed.</span></span>

   <span data-ttu-id="05d81-119">Visual Studio'nun en son sürümünü yükleme hakkında daha fazla bilgi için Visual [Studio'yu yükle'ye](/visualstudio/install/install-visual-studio)bakın.</span><span class="sxs-lookup"><span data-stu-id="05d81-119">For more information about installing the latest version of Visual Studio, see [Install Visual Studio](/visualstudio/install/install-visual-studio).</span></span>

## <a name="create-the-application-project"></a><span data-ttu-id="05d81-120">Uygulama projesini oluşturma</span><span class="sxs-lookup"><span data-stu-id="05d81-120">Create the application project</span></span>

<span data-ttu-id="05d81-121">İlk adım, uygulama tanımı, iki sayfa ve bir görüntü içeren uygulama altyapısı oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="05d81-121">The first step is to create the application infrastructure, which includes an application definition, two pages, and an image.</span></span>

1. <span data-ttu-id="05d81-122">Visual Basic veya Visual C# adlı **`ExpenseIt`** yeni bir WPF Uygulama projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="05d81-122">Create a new WPF Application project in Visual Basic or Visual C# named **`ExpenseIt`**:</span></span>

   1. <span data-ttu-id="05d81-123">Visual Studio'yu açın ve **Başlat menüsü** altında yeni bir **proje oluştur'u** seçin.</span><span class="sxs-lookup"><span data-stu-id="05d81-123">Open Visual Studio and select **Create a new project** under the **Get started** menu.</span></span>

      <span data-ttu-id="05d81-124">**Yeni proje oluştur** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="05d81-124">The **Create a new project** dialog opens.</span></span>

   2. <span data-ttu-id="05d81-125">**Dil** açılır düşüşünde **C#** veya **Visual Basic'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="05d81-125">In the **Language** dropdown, select either **C#** or **Visual Basic**.</span></span>

   3. <span data-ttu-id="05d81-126">**WPF Uygulaması (.NET Framework)** şablonunu seçin ve sonra **İleri'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="05d81-126">Select the **WPF App (.NET Framework)** template and then select **Next**.</span></span>

      ![Yeni bir proje iletişim kutusu oluşturma](./media/walkthrough-my-first-wpf-desktop-application/create-new-project-dialog.png)

      <span data-ttu-id="05d81-128">Yeni proje iletişim **günlüğüne Yapıla** açılır.</span><span class="sxs-lookup"><span data-stu-id="05d81-128">The **Configure your new project** dialog opens.</span></span>

   4. <span data-ttu-id="05d81-129">Proje adını **`ExpenseIt`** girin ve sonra **Oluştur'u**seçin.</span><span class="sxs-lookup"><span data-stu-id="05d81-129">Enter the project name **`ExpenseIt`** and then select **Create**.</span></span>

      ![Yeni bir proje iletişim kutusunu yapılandırma](./media/walkthrough-my-first-wpf-desktop-application/configure-new-project-dialog.png)

      <span data-ttu-id="05d81-131">Visual Studio projeyi oluşturur ve **MainWindow.xaml**adlı varsayılan uygulama penceresi için tasarımcıyı açar.</span><span class="sxs-lookup"><span data-stu-id="05d81-131">Visual Studio creates the project and opens the designer for the default application window named **MainWindow.xaml**.</span></span>

2. <span data-ttu-id="05d81-132">*Open Application.xaml* (Visual Basic) veya *App.xaml* (C#).</span><span class="sxs-lookup"><span data-stu-id="05d81-132">Open *Application.xaml* (Visual Basic) or *App.xaml* (C#).</span></span>

    <span data-ttu-id="05d81-133">Bu XAML dosyası bir WPF uygulamasını ve uygulama kaynaklarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="05d81-133">This XAML file defines a WPF application and any application resources.</span></span> <span data-ttu-id="05d81-134">Ayrıca ui belirtmek için bu dosyayı kullanın, Bu durumda *MainWindow.xaml*, otomatik olarak uygulama başladığında gösterir.</span><span class="sxs-lookup"><span data-stu-id="05d81-134">You also use this file to specify the UI, in this case *MainWindow.xaml*, that automatically shows when the application starts.</span></span>

    <span data-ttu-id="05d81-135">XAML'niz Visual Basic'te aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="05d81-135">Your XAML should look like the following in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    <span data-ttu-id="05d81-136">Ve C#'daki gibi:</span><span class="sxs-lookup"><span data-stu-id="05d81-136">And like the following in C#:</span></span>

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. <span data-ttu-id="05d81-137">*Açık MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="05d81-137">Open *MainWindow.xaml*.</span></span>

    <span data-ttu-id="05d81-138">Bu XAML dosyası uygulamanızın ana penceresidir ve sayfalarda oluşturulan içeriği görüntüler.</span><span class="sxs-lookup"><span data-stu-id="05d81-138">This XAML file is the main window of your application and displays content created in pages.</span></span> <span data-ttu-id="05d81-139">Sınıf, <xref:System.Windows.Window> başlığı, boyutu veya simgesi gibi bir pencerenin özelliklerini tanımlar ve kapatma veya gizleme gibi olayları işler.</span><span class="sxs-lookup"><span data-stu-id="05d81-139">The <xref:System.Windows.Window> class defines the properties of a window, such as its title, size, or icon, and handles events, such as closing or hiding.</span></span>

4. <span data-ttu-id="05d81-140">Aşağıdaki <xref:System.Windows.Window> XAML'de gösterildiği gibi öğeyi bir <xref:System.Windows.Navigation.NavigationWindow>olarak değiştirin:</span><span class="sxs-lookup"><span data-stu-id="05d81-140">Change the <xref:System.Windows.Window> element to a <xref:System.Windows.Navigation.NavigationWindow>, as shown in the following XAML:</span></span>

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   <span data-ttu-id="05d81-141">Bu uygulama, kullanıcı girişine bağlı olarak farklı içeriğe yönlendirin.</span><span class="sxs-lookup"><span data-stu-id="05d81-141">This app navigates to different content depending on the user input.</span></span> <span data-ttu-id="05d81-142">Bu nedenle ana <xref:System.Windows.Window> bir <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="05d81-142">This is why the main <xref:System.Windows.Window> needs to be changed to a <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="05d81-143"><xref:System.Windows.Navigation.NavigationWindow>tüm özelliklerini <xref:System.Windows.Window>devralır.</span><span class="sxs-lookup"><span data-stu-id="05d81-143"><xref:System.Windows.Navigation.NavigationWindow> inherits all the properties of <xref:System.Windows.Window>.</span></span> <span data-ttu-id="05d81-144">XAML dosyasındaki <xref:System.Windows.Navigation.NavigationWindow> öğe sınıfın bir örneğini <xref:System.Windows.Navigation.NavigationWindow> oluşturur.</span><span class="sxs-lookup"><span data-stu-id="05d81-144">The <xref:System.Windows.Navigation.NavigationWindow> element in the XAML file creates an instance of the <xref:System.Windows.Navigation.NavigationWindow> class.</span></span> <span data-ttu-id="05d81-145">Daha fazla bilgi için [Gezintiye genel bakış](../app-development/navigation-overview.md)alabiliyorum.</span><span class="sxs-lookup"><span data-stu-id="05d81-145">For more information, see [Navigation overview](../app-development/navigation-overview.md).</span></span>

5. <span data-ttu-id="05d81-146"><xref:System.Windows.Navigation.NavigationWindow> Etiketler arasındaki <xref:System.Windows.Controls.Grid> öğeleri kaldırın.</span><span class="sxs-lookup"><span data-stu-id="05d81-146">Remove the <xref:System.Windows.Controls.Grid> elements from between the <xref:System.Windows.Navigation.NavigationWindow> tags.</span></span>

6. <span data-ttu-id="05d81-147">Öğe için XAML kodunda aşağıdaki <xref:System.Windows.Navigation.NavigationWindow> özellikleri değiştirin:</span><span class="sxs-lookup"><span data-stu-id="05d81-147">Change the following properties in the XAML code for the <xref:System.Windows.Navigation.NavigationWindow> element:</span></span>

    - <span data-ttu-id="05d81-148"><xref:System.Windows.Window.Title%2A> Özelliği " "`ExpenseIt`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="05d81-148">Set the <xref:System.Windows.Window.Title%2A> property to "`ExpenseIt`".</span></span>

    - <span data-ttu-id="05d81-149"><xref:System.Windows.FrameworkElement.Height%2A> Özelliği 350 piksele ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="05d81-149">Set the <xref:System.Windows.FrameworkElement.Height%2A> property to 350 pixels.</span></span>

    - <span data-ttu-id="05d81-150"><xref:System.Windows.FrameworkElement.Width%2A> Özelliği 500 piksele ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="05d81-150">Set the <xref:System.Windows.FrameworkElement.Width%2A> property to 500 pixels.</span></span>

    <span data-ttu-id="05d81-151">XAML'niz Visual Basic için aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="05d81-151">Your XAML should look like the following for Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    <span data-ttu-id="05d81-152">Ve C# için aşağıdaki gibi:</span><span class="sxs-lookup"><span data-stu-id="05d81-152">And like the following for C#:</span></span>

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

7. <span data-ttu-id="05d81-153">*Açık MainWindow.xaml.vb* veya *MainWindow.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="05d81-153">Open *MainWindow.xaml.vb* or *MainWindow.xaml.cs*.</span></span>

    <span data-ttu-id="05d81-154">Bu *dosya, MainWindow.xaml'da*bildirilen olayları işlemek için kod içeren kod arkası bir dosyadır.</span><span class="sxs-lookup"><span data-stu-id="05d81-154">This file is a code-behind file that contains code to handle the events declared in *MainWindow.xaml*.</span></span> <span data-ttu-id="05d81-155">Bu dosya XAML'de tanımlanan pencere için kısmi bir sınıf içerir.</span><span class="sxs-lookup"><span data-stu-id="05d81-155">This file contains a partial class for the window defined in XAML.</span></span>

8. <span data-ttu-id="05d81-156">C# kullanıyorsanız, `MainWindow` 'den <xref:System.Windows.Navigation.NavigationWindow>türeecek sınıfı değiştirin.</span><span class="sxs-lookup"><span data-stu-id="05d81-156">If you're using C#, change the `MainWindow` class to derive from <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="05d81-157">(Visual Basic'te, XAML'de pencereyi değiştirdiğinizde bu otomatik olarak gerçekleşir.) C# kodunuz şimdi şu na benzemelidir:</span><span class="sxs-lookup"><span data-stu-id="05d81-157">(In Visual Basic, this happens automatically when you change the window in XAML.) Your C# code should now look like this:</span></span>

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/MainWindow.xaml.cs?highlight=21)]

## <a name="add-files-to-the-application"></a><span data-ttu-id="05d81-158">Uygulamaya dosya ekleme</span><span class="sxs-lookup"><span data-stu-id="05d81-158">Add files to the application</span></span>

<span data-ttu-id="05d81-159">Bu bölümde, uygulamaya iki sayfa ve bir resim eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="05d81-159">In this section, you'll add two pages and an image to the application.</span></span>

1. <span data-ttu-id="05d81-160">Projeye yeni bir sayfa ekleyin ve *`ExpenseItHome.xaml`* adlandırın:</span><span class="sxs-lookup"><span data-stu-id="05d81-160">Add a new page to the project, and name it *`ExpenseItHome.xaml`*:</span></span>

   1. <span data-ttu-id="05d81-161">**Çözüm Gezgini'nde**proje **`ExpenseIt`** düğümüne sağ tıklayın ve**Sayfa** **Ekle'yi** > seçin.</span><span class="sxs-lookup"><span data-stu-id="05d81-161">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="05d81-162">Yeni **Öğe Ekle** iletişim kutusunda, **Sayfa (WPF)** şablonu zaten seçilir.</span><span class="sxs-lookup"><span data-stu-id="05d81-162">In the **Add New Item** dialog, the **Page (WPF)** template is already selected.</span></span> <span data-ttu-id="05d81-163">Adı **`ExpenseItHome`** girin ve sonra **Ekle'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="05d81-163">Enter the name **`ExpenseItHome`**, and then select **Add**.</span></span>

    <span data-ttu-id="05d81-164">Bu sayfa, uygulama başlatıldığında görüntülenen ilk sayfadır.</span><span class="sxs-lookup"><span data-stu-id="05d81-164">This page is the first page that's displayed when the application is launched.</span></span> <span data-ttu-id="05d81-165">Bu, bir gider raporu göstermek için seçilecek kişilerin listesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="05d81-165">It will show a list of people to select from, to show an expense report for.</span></span>

1. <span data-ttu-id="05d81-166">Aç. *`ExpenseItHome.xaml`*</span><span class="sxs-lookup"><span data-stu-id="05d81-166">Open *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="05d81-167">" <xref:System.Windows.Controls.Page.Title%2A> "`ExpenseIt - Home`".</span><span class="sxs-lookup"><span data-stu-id="05d81-167">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - Home`".</span></span>

1. <span data-ttu-id="05d81-168">`DesignHeight` 350 piksele ve 500 `DesignWidth` piksele ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="05d81-168">Set the `DesignHeight` to 350 pixels and the `DesignWidth` to 500 pixels.</span></span>

    <span data-ttu-id="05d81-169">XAML şimdi Visual Basic için aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="05d81-169">The XAML now appears as follows for Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    <span data-ttu-id="05d81-170">Ve C# için aşağıdaki gibi:</span><span class="sxs-lookup"><span data-stu-id="05d81-170">And like the following for C#:</span></span>

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

1. <span data-ttu-id="05d81-171">*Açık MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="05d81-171">Open *MainWindow.xaml*.</span></span>

1. <span data-ttu-id="05d81-172">Öğeye <xref:System.Windows.Navigation.NavigationWindow.Source%2A> bir özellik ekleyin ve`ExpenseItHome.xaml`" " olarak ayarlayın. <xref:System.Windows.Navigation.NavigationWindow></span><span class="sxs-lookup"><span data-stu-id="05d81-172">Add a <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property to the <xref:System.Windows.Navigation.NavigationWindow> element and set it to "`ExpenseItHome.xaml`".</span></span>

    <span data-ttu-id="05d81-173">Bu, *`ExpenseItHome.xaml`* uygulama başladığında açılan ilk sayfa olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="05d81-173">This sets *`ExpenseItHome.xaml`* to be the first page opened when the application starts.</span></span>

    <span data-ttu-id="05d81-174">Örnek XAML Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="05d81-174">Example XAML in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    <span data-ttu-id="05d81-175">Ve C#' da:</span><span class="sxs-lookup"><span data-stu-id="05d81-175">And in C#:</span></span>

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > <span data-ttu-id="05d81-176">**Kaynak** özelliğini **Özellikler** penceresinin **çeşitli** kategorisinde de ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05d81-176">You can also set the **Source** property in the **Miscellaneous** category of the **Properties** window.</span></span>
   >
   > ![Özellikler penceresinde kaynak özelliği](./media/properties-source.png)

1. <span data-ttu-id="05d81-178">Projeye yeni bir WPF sayfası daha ekleyin ve *expensereport.xaml*adını verin ::</span><span class="sxs-lookup"><span data-stu-id="05d81-178">Add another new WPF page to the project, and name it *ExpenseReportPage.xaml*::</span></span>

   1. <span data-ttu-id="05d81-179">**Çözüm Gezgini'nde**proje **`ExpenseIt`** düğümüne sağ tıklayın ve**Sayfa** **Ekle'yi** > seçin.</span><span class="sxs-lookup"><span data-stu-id="05d81-179">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="05d81-180">Yeni **Öğe Ekle** iletişim kutusunda **Sayfa (WPF)** şablonu öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="05d81-180">In the **Add New Item** dialog, select the **Page (WPF)** template.</span></span> <span data-ttu-id="05d81-181">**GiderRaporu Sayfası**adını girin ve sonra **Ekle'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="05d81-181">Enter the name **ExpenseReportPage**, and then select **Add**.</span></span>

    <span data-ttu-id="05d81-182">Bu sayfada, **`ExpenseItHome`** sayfada seçilen kişinin gider raporu gösterilecek.</span><span class="sxs-lookup"><span data-stu-id="05d81-182">This page will show the expense report for the person that is selected on the **`ExpenseItHome`** page.</span></span>

1. <span data-ttu-id="05d81-183">*Açık GiderReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="05d81-183">Open *ExpenseReportPage.xaml*.</span></span>

1. <span data-ttu-id="05d81-184">" <xref:System.Windows.Controls.Page.Title%2A> "`ExpenseIt - View Expense`".</span><span class="sxs-lookup"><span data-stu-id="05d81-184">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - View Expense`".</span></span>

1. <span data-ttu-id="05d81-185">`DesignHeight` 350 piksele ve 500 `DesignWidth` piksele ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="05d81-185">Set the `DesignHeight` to 350 pixels and the `DesignWidth` to 500 pixels.</span></span>

    <span data-ttu-id="05d81-186">*ExpenseReportPage.xaml* şimdi Visual Basic aşağıdaki gibi görünüyor:</span><span class="sxs-lookup"><span data-stu-id="05d81-186">*ExpenseReportPage.xaml* now looks like the following in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    <span data-ttu-id="05d81-187">Ve C#'daki gibi:</span><span class="sxs-lookup"><span data-stu-id="05d81-187">And like the following in C#:</span></span>

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

1. <span data-ttu-id="05d81-188">Açık *GiderItHome.xaml.vb* ve *GiderReportPage.xaml.vb*, veya *ExpenseItHome.xaml.cs* ve *ExpenseReportPage.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="05d81-188">Open *ExpenseItHome.xaml.vb* and *ExpenseReportPage.xaml.vb*, or *ExpenseItHome.xaml.cs* and *ExpenseReportPage.xaml.cs*.</span></span>

    <span data-ttu-id="05d81-189">Yeni bir Sayfa dosyası oluşturduğunuzda, Visual Studio otomatik olarak *kod arkasındaki* dosyayı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="05d81-189">When you create a new Page file, Visual Studio automatically creates its *code-behind* file.</span></span> <span data-ttu-id="05d81-190">Bu kod arkası dosyalar, kullanıcı girişine yanıt verme mantığını işler.</span><span class="sxs-lookup"><span data-stu-id="05d81-190">These code-behind files handle the logic for responding to user input.</span></span>

    <span data-ttu-id="05d81-191">Kodunuz aşağıdaki **`ExpenseItHome`** gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="05d81-191">Your code should look like the following for **`ExpenseItHome`**:</span></span>

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]

    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    <span data-ttu-id="05d81-192">Ve **GiderReportPage**için aşağıdaki gibi:</span><span class="sxs-lookup"><span data-stu-id="05d81-192">And like the following for **ExpenseReportPage**:</span></span>

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]

    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

1. <span data-ttu-id="05d81-193">Projeye *filigran.png* adlı bir resim ekleyin.</span><span class="sxs-lookup"><span data-stu-id="05d81-193">Add an image named *watermark.png* to the project.</span></span> <span data-ttu-id="05d81-194">Kendi resminizi oluşturabilir, dosyayı örnek koddan kopyalayabilir veya [microsoft/WPF-Samples](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png) GitHub deposundan alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05d81-194">You can create your own image, copy the file from the sample code, or get it from the [microsoft/WPF-Samples](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png) GitHub repository.</span></span>

    1. <span data-ttu-id="05d81-195">Proje düğümüne sağ tıklayın ve**Varolan Öğe** **ekle'yi** > seçin veya **Shift**+**Alt**+**A tuşuna**basın.</span><span class="sxs-lookup"><span data-stu-id="05d81-195">Right-click on the project node and select **Add** > **Existing Item**, or press **Shift**+**Alt**+**A**.</span></span>

    2. <span data-ttu-id="05d81-196">**Varolan Öğe Ekle** iletişim kutusunda, dosya filtresini **Tüm Dosyalar** veya **Resim Dosyaları'na**ayarlayın, kullanmak istediğiniz resim dosyasına göz atın ve sonra **Ekle'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="05d81-196">In the **Add Existing Item** dialog, set the file filter to either **All Files** or **Image Files**, browse to the image file you want to use, and then select **Add**.</span></span>

## <a name="build-and-run-the-application"></a><span data-ttu-id="05d81-197">Uygulamayı derleme ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="05d81-197">Build and run the application</span></span>

1. <span data-ttu-id="05d81-198">Uygulamayı oluşturmak ve çalıştırmak için Hata **Ayıklama** menüsünden **F5** tuşuna basın veya Hata **Ayıklama başlat'ı** seçin.</span><span class="sxs-lookup"><span data-stu-id="05d81-198">To build and run the application, press **F5** or select **Start Debugging** from the **Debug** menu.</span></span>

    <span data-ttu-id="05d81-199">Aşağıdaki resimde <xref:System.Windows.Navigation.NavigationWindow> düğmeleri ile uygulama gösterir:</span><span class="sxs-lookup"><span data-stu-id="05d81-199">The following illustration shows the application with the <xref:System.Windows.Navigation.NavigationWindow> buttons:</span></span>

    ![Oluşturup çalıştırdıktan sonra uygulama.](./media/walkthrough-my-first-wpf-desktop-application/build-run-application.png)

2. <span data-ttu-id="05d81-201">Visual Studio'ya dönmek için uygulamayı kapatın.</span><span class="sxs-lookup"><span data-stu-id="05d81-201">Close the application to return to Visual Studio.</span></span>

## <a name="create-the-layout"></a><span data-ttu-id="05d81-202">Düzeni oluşturma</span><span class="sxs-lookup"><span data-stu-id="05d81-202">Create the layout</span></span>

<span data-ttu-id="05d81-203">Düzen, Kullanıcı Arabirimi öğelerini yerleştirmek için sıralı bir yol sağlar ve kullanıcı arabirimi yeniden boyutlandığında bu öğelerin boyutunu ve konumunu yönetir.</span><span class="sxs-lookup"><span data-stu-id="05d81-203">Layout provides an ordered way to place UI elements, and also manages the size and position of those elements when a UI is resized.</span></span> <span data-ttu-id="05d81-204">Genellikle aşağıdaki düzen denetimlerinden biriyle bir düzen oluşturursunuz:</span><span class="sxs-lookup"><span data-stu-id="05d81-204">You typically create a layout with one of the following layout controls:</span></span>

- <span data-ttu-id="05d81-205"><xref:System.Windows.Controls.Canvas>- Tuval alanına göre koordinatları kullanarak alt öğeleri açıkça konumlandırabileceğiniz bir alan tanımlar.</span><span class="sxs-lookup"><span data-stu-id="05d81-205"><xref:System.Windows.Controls.Canvas> - Defines an area within which you can explicitly position child elements by using coordinates that are relative to the Canvas area.</span></span>
- <span data-ttu-id="05d81-206"><xref:System.Windows.Controls.DockPanel>- Alt öğeleri yatay veya dikey olarak, birbirlerine göre düzenleyebileceğiniz bir alan tanımlar.</span><span class="sxs-lookup"><span data-stu-id="05d81-206"><xref:System.Windows.Controls.DockPanel> - Defines an area where you can arrange child elements either horizontally or vertically, relative to each other.</span></span>
- <span data-ttu-id="05d81-207"><xref:System.Windows.Controls.Grid>- Sütun ve satırlardan oluşan esnek bir ızgara alanı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="05d81-207"><xref:System.Windows.Controls.Grid> - Defines a flexible grid area that consists of columns and rows.</span></span>
- <span data-ttu-id="05d81-208"><xref:System.Windows.Controls.StackPanel>- Alt öğeleri yatay veya dikey olarak yönlendirilebilen tek bir satıra düzenler.</span><span class="sxs-lookup"><span data-stu-id="05d81-208"><xref:System.Windows.Controls.StackPanel> - Arranges child elements into a single line that can be oriented horizontally or vertically.</span></span>
- <span data-ttu-id="05d81-209"><xref:System.Windows.Controls.VirtualizingStackPanel>- İçeriği yatay veya dikey olarak yönlendirilen tek bir satırda düzenler ve sanallaştırır.</span><span class="sxs-lookup"><span data-stu-id="05d81-209"><xref:System.Windows.Controls.VirtualizingStackPanel> - Arranges and virtualizes content on a single line that is oriented either horizontally or vertically.</span></span>
- <span data-ttu-id="05d81-210"><xref:System.Windows.Controls.WrapPanel>- Alt öğeleri soldan sağa sıralı konuma yerleştirerek içeriği içeren kutunun kenarındaki bir sonraki satıra ayırın.</span><span class="sxs-lookup"><span data-stu-id="05d81-210"><xref:System.Windows.Controls.WrapPanel> - Positions child elements in sequential position from left to right, breaking content to the next line at the edge of the containing box.</span></span> <span data-ttu-id="05d81-211">Sonraki sıralama, Yönlendirme özelliğinin değerine bağlı olarak yukarıdan aşağıya veya sağdan sola sırayla gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="05d81-211">Subsequent ordering happens sequentially from top to bottom or from right to left, depending on the value of the Orientation property.</span></span>

<span data-ttu-id="05d81-212">Bu düzen denetimlerinin her biri, alt öğeleri için belirli bir düzen türünü destekler.</span><span class="sxs-lookup"><span data-stu-id="05d81-212">Each of these layout controls supports a particular type of layout for its child elements.</span></span> <span data-ttu-id="05d81-213">`ExpenseIt`sayfalar yeniden boyutlandırılabilir ve her sayfada diğer öğelerle birlikte yatay ve dikey olarak düzenlenmiş öğeler vardır.</span><span class="sxs-lookup"><span data-stu-id="05d81-213">`ExpenseIt` pages can be resized, and each page has elements that are arranged horizontally and vertically alongside other elements.</span></span> <span data-ttu-id="05d81-214">Bu örnekte, <xref:System.Windows.Controls.Grid> uygulama için düzen öğesi olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="05d81-214">In this example, the <xref:System.Windows.Controls.Grid> is used as  layout element for the application.</span></span>

> [!TIP]
> <span data-ttu-id="05d81-215">Öğeler hakkında <xref:System.Windows.Controls.Panel> daha fazla bilgi için [Paneller genel bakış](../controls/panels-overview.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="05d81-215">For more information about <xref:System.Windows.Controls.Panel> elements, see [Panels overview](../controls/panels-overview.md).</span></span> <span data-ttu-id="05d81-216">Düzen hakkında daha fazla bilgi için [Bkz. Düzen.](../advanced/layout.md)</span><span class="sxs-lookup"><span data-stu-id="05d81-216">For more information about layout, see [Layout](../advanced/layout.md).</span></span>

<span data-ttu-id="05d81-217">Bu bölümde, <xref:System.Windows.Controls.Grid> içinde *`ExpenseItHome.xaml`* sütun ve satır tanımları ekleyerek üç satır ve 10 piksel kenar boşluğu içeren tek sütunlu bir tablo oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="05d81-217">In this section, you create a single-column table with three rows and a 10-pixel margin by adding column and row definitions to the <xref:System.Windows.Controls.Grid> in *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="05d81-218">In *`ExpenseItHome.xaml`*, <xref:System.Windows.FrameworkElement.Margin%2A> öğe üzerindeki <xref:System.Windows.Controls.Grid> özelliği "10,0,10,10" olarak ayarlayın, hangi sol, üst, sağ ve alt kenar boşlukları karşılık gelir:</span><span class="sxs-lookup"><span data-stu-id="05d81-218">In *`ExpenseItHome.xaml`*, set the <xref:System.Windows.FrameworkElement.Margin%2A> property on the <xref:System.Windows.Controls.Grid> element to "10,0,10,10", which corresponds to left, top, right and bottom margins:</span></span>

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > <span data-ttu-id="05d81-219">**Özellikler** penceresinde, **Düzen** kategorisi altında **Kenar Boşluğu** değerlerini de ayarlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="05d81-219">You can also set the **Margin** values in the **Properties** window, under the **Layout** category:</span></span>
   >
   > ![Özellikler penceresinde kenar boşluğu değerleri](./media/properties-margin.png)

2. <span data-ttu-id="05d81-221">Satır ve sütun tanımlarını <xref:System.Windows.Controls.Grid> oluşturmak için etiketlerin arasına aşağıdaki XAML'yi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="05d81-221">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags to create the row and column definitions:</span></span>

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    <span data-ttu-id="05d81-222">İki <xref:System.Windows.Controls.RowDefinition.Height%2A> satırın <xref:System.Windows.GridLength.Auto%2A>kümesi, satırlar satırlarda içeriğe göre boyutlandırılır anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="05d81-222">The <xref:System.Windows.Controls.RowDefinition.Height%2A> of two rows is set to <xref:System.Windows.GridLength.Auto%2A>, which means that the rows are sized based on the content in the rows.</span></span> <span data-ttu-id="05d81-223">Varsayılan <xref:System.Windows.Controls.RowDefinition.Height%2A> boyutlandırmadır, <xref:System.Windows.GridUnitType.Star> bu da satır yüksekliğinin kullanılabilir alanın ağırlıklı bir oranı olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="05d81-223">The default <xref:System.Windows.Controls.RowDefinition.Height%2A> is <xref:System.Windows.GridUnitType.Star> sizing, which means that the row height is a weighted proportion of the available space.</span></span> <span data-ttu-id="05d81-224">Örneğin, her <xref:System.Windows.Controls.RowDefinition.Height%2A> biri "\*" olan iki satır varsa, her birinin kullanılabilir alanın yarısı olan bir yüksekliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="05d81-224">For example if two rows each have a <xref:System.Windows.Controls.RowDefinition.Height%2A> of "\*", they each have a height that is half of the available space.</span></span>

    <span data-ttu-id="05d81-225">Şimdi <xref:System.Windows.Controls.Grid> aşağıdaki XAML içermelidir:</span><span class="sxs-lookup"><span data-stu-id="05d81-225">Your <xref:System.Windows.Controls.Grid> should now contain the following XAML:</span></span>

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a><span data-ttu-id="05d81-226">Denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="05d81-226">Add controls</span></span>

<span data-ttu-id="05d81-227">Bu bölümde, harcama raporunu görüntülemek için bir kişi seçtiğiniz kişilerin listesini göstermek için ana sayfa kullanıcı arabirimi bilgilerini güncelleştireceksiniz.</span><span class="sxs-lookup"><span data-stu-id="05d81-227">In this section, you'll update the home page UI to show a list of people, where you select one person to display their expense report.</span></span> <span data-ttu-id="05d81-228">Denetimler, kullanıcıların uygulamanızla etkileşimkurmasını sağlayan Kullanıcı GEtki nesneleridir.</span><span class="sxs-lookup"><span data-stu-id="05d81-228">Controls are UI objects that allow users to interact with your application.</span></span> <span data-ttu-id="05d81-229">Daha fazla bilgi için [Denetimler'e](../controls/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="05d81-229">For more information, see [Controls](../controls/index.md).</span></span>

<span data-ttu-id="05d81-230">Bu UI'yi oluşturmak için *`ExpenseItHome.xaml`* aşağıdaki öğeleri eklersiniz:</span><span class="sxs-lookup"><span data-stu-id="05d81-230">To create this UI, you'll add the following elements to *`ExpenseItHome.xaml`*:</span></span>

- <span data-ttu-id="05d81-231">A <xref:System.Windows.Controls.ListBox> (kişi listesi için).</span><span class="sxs-lookup"><span data-stu-id="05d81-231">A <xref:System.Windows.Controls.ListBox> (for the list of people).</span></span>
- <span data-ttu-id="05d81-232">A <xref:System.Windows.Controls.Label> (liste üstbilgi için).</span><span class="sxs-lookup"><span data-stu-id="05d81-232">A <xref:System.Windows.Controls.Label> (for the list header).</span></span>
- <span data-ttu-id="05d81-233">A <xref:System.Windows.Controls.Button> (listede seçilen kişinin gider raporunu görüntülemek için tıklatın).</span><span class="sxs-lookup"><span data-stu-id="05d81-233">A <xref:System.Windows.Controls.Button> (to click to view the expense report for the person that is selected in the list).</span></span>

<span data-ttu-id="05d81-234">Her denetim <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> ekli özelliği ayarlayarak bir satır yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="05d81-234">Each control is placed in a row of the <xref:System.Windows.Controls.Grid> by setting the <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> attached property.</span></span> <span data-ttu-id="05d81-235">Ekteki özellikler hakkında daha fazla bilgi için [bkz.](../advanced/attached-properties-overview.md)</span><span class="sxs-lookup"><span data-stu-id="05d81-235">For more information about attached properties, see [Attached Properties Overview](../advanced/attached-properties-overview.md).</span></span>

1. <span data-ttu-id="05d81-236">In *`ExpenseItHome.xaml`*, <xref:System.Windows.Controls.Grid> etiketleri arasında bir yere aşağıdaki XAML ekleyin:</span><span class="sxs-lookup"><span data-stu-id="05d81-236">In *`ExpenseItHome.xaml`*, add the following XAML somewhere between the <xref:System.Windows.Controls.Grid> tags:</span></span>

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > <span data-ttu-id="05d81-237">Denetimleri **Araç Kutusu** penceresinden tasarım penceresine sürükleyerek ve özellikleri özellikleriözelliklerini ayarlayarak **Properties** da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05d81-237">You can also create the controls by dragging them from the **Toolbox** window onto the design window, and then setting their properties in the **Properties** window.</span></span>

2. <span data-ttu-id="05d81-238">Uygulamayı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="05d81-238">Build and run the application.</span></span>

    <span data-ttu-id="05d81-239">Aşağıdaki resimde oluşturduğunuz denetimler gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="05d81-239">The following illustration shows the controls you created:</span></span>

![GiderAd listesini gösteren örnek ekran görüntüsü](./media/walkthrough-my-first-wpf-desktop-application/add-application-controls.png)

## <a name="add-an-image-and-a-title"></a><span data-ttu-id="05d81-241">Resim ve başlık ekleme</span><span class="sxs-lookup"><span data-stu-id="05d81-241">Add an image and a title</span></span>

<span data-ttu-id="05d81-242">Bu bölümde, ana sayfa kullanıcı kullanıcı sını bir resim ve sayfa başlığıyla güncelleştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05d81-242">In this section, you'll update the home page UI with an image and a page title.</span></span>

1. <span data-ttu-id="05d81-243">In *`ExpenseItHome.xaml`*, 230 <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> piksel <xref:System.Windows.Controls.ColumnDefinition.Width%2A> sabit başka bir sütun ekleyin:</span><span class="sxs-lookup"><span data-stu-id="05d81-243">In *`ExpenseItHome.xaml`*, add another column to the <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> with a fixed <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of 230 pixels:</span></span>

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=2#NewColumn)]

2. <span data-ttu-id="05d81-244">Toplam dört satır <xref:System.Windows.Controls.Grid.RowDefinitions%2A>için başka bir satır ekleyin:</span><span class="sxs-lookup"><span data-stu-id="05d81-244">Add another row to the <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, for a total of four rows:</span></span>

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=2#NewRows)]

3. <span data-ttu-id="05d81-245"><xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> Üç denetimin (Kenarlık, ListBox ve Düğme) her birinde özelliği 1'e ayarlayarak denetimleri ikinci sütuna taşıyın.</span><span class="sxs-lookup"><span data-stu-id="05d81-245">Move the controls to the second column by setting the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property to 1 in each of the three controls (Border, ListBox, and Button).</span></span>

4. <span data-ttu-id="05d81-246">Her denetimi, üç denetimin (Kenarlık, ListBox ve Düğme) her biri için 1'e ve Kenarlık öğesine göre 1'e ekleyerek <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> her denetimi bir satıraşağı taşıyın.</span><span class="sxs-lookup"><span data-stu-id="05d81-246">Move each control down a row by incrementing its <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> value by 1 for each of the three controls (Border, ListBox, and Button) and for the Border element.</span></span>

   <span data-ttu-id="05d81-247">Üç denetim için XAML şimdi aşağıdaki gibi görünüyor:</span><span class="sxs-lookup"><span data-stu-id="05d81-247">The XAML for the three controls now looks like the following:</span></span>

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

5. <span data-ttu-id="05d81-248">Aşağıdaki XAML'yi `</Grid>` etiketler in arasına ekleyerek özelliği *filigran.png* resim dosyasına `<Grid>` ayarlayın: <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="05d81-248">Set the <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> property to the *watermark.png* image file, by adding the following XAML anywhere between the `<Grid>` and `</Grid>` tags:</span></span>

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

6. <span data-ttu-id="05d81-249">Öğeden <xref:System.Windows.Controls.Border> önce, <xref:System.Windows.Controls.Label> "Gider Raporu Görüntüle" içeriğiyle bir öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="05d81-249">Before the <xref:System.Windows.Controls.Border> element, add a <xref:System.Windows.Controls.Label> with the content "View Expense Report".</span></span> <span data-ttu-id="05d81-250">Bu etiket sayfanın başlığıdır.</span><span class="sxs-lookup"><span data-stu-id="05d81-250">This label is the title of the page.</span></span>

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

7. <span data-ttu-id="05d81-251">Uygulamayı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="05d81-251">Build and run the application.</span></span>

<span data-ttu-id="05d81-252">Aşağıdaki resimde az önce eklediğiniz şeyin sonuçları gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="05d81-252">The following illustration shows the results of what you just added:</span></span>

![GiderYeni resim arka planını ve sayfa başlığını gösteren örnek ekran görüntüsü](./media/walkthrough-my-first-wpf-desktop-application/add-application-image-title.png)

## <a name="add-code-to-handle-events"></a><span data-ttu-id="05d81-254">Olayları işlemek için kod ekleme</span><span class="sxs-lookup"><span data-stu-id="05d81-254">Add code to handle events</span></span>

1. <span data-ttu-id="05d81-255">In *`ExpenseItHome.xaml`*, <xref:System.Windows.Controls.Primitives.ButtonBase.Click> öğeye bir <xref:System.Windows.Controls.Button> olay işleyicisi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="05d81-255">In *`ExpenseItHome.xaml`*, add a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to the <xref:System.Windows.Controls.Button> element.</span></span> <span data-ttu-id="05d81-256">Daha fazla bilgi için [bkz: Basit bir olay işleyicisi oluşturun.](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="05d81-256">For more information, see [How to: Create a simple event handler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span></span>

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

2. <span data-ttu-id="05d81-257">Aç *`ExpenseItHome.xaml.vb`* *`ExpenseItHome.xaml.cs`* veya .</span><span class="sxs-lookup"><span data-stu-id="05d81-257">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

3. <span data-ttu-id="05d81-258">Bir düğme tıklatmak `ExpenseItHome` olay işleyicisi eklemek için sınıfa aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="05d81-258">Add the following code to the `ExpenseItHome` class to add a button click event handler.</span></span> <span data-ttu-id="05d81-259">Olay işleyicisi **Gider Raporu Sayfası** sayfasını açar.</span><span class="sxs-lookup"><span data-stu-id="05d81-259">The event handler opens the **ExpenseReportPage** page.</span></span>

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a><span data-ttu-id="05d81-260">Gider Raporu Sayfası için UI oluşturma</span><span class="sxs-lookup"><span data-stu-id="05d81-260">Create the UI for ExpenseReportPage</span></span>

<span data-ttu-id="05d81-261">**`ExpenseItHome`** *ExpenseReportPage.xaml,* sayfada seçilen kişinin gider raporunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="05d81-261">*ExpenseReportPage.xaml* displays the expense report for the person that's selected on the **`ExpenseItHome`** page.</span></span> <span data-ttu-id="05d81-262">Bu bölümde, **GiderReportPage**için UI'yi oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="05d81-262">In this section, you'll create the UI for **ExpenseReportPage**.</span></span> <span data-ttu-id="05d81-263">Ayrıca, çeşitli UI öğelerine arka plan ve dolgu renkleri eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="05d81-263">You'll also add background and fill colors to the various UI elements.</span></span>

1. <span data-ttu-id="05d81-264">*Açık GiderReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="05d81-264">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="05d81-265">Etiketler arasına aşağıdaki XAML'yi <xref:System.Windows.Controls.Grid> ekleyin:</span><span class="sxs-lookup"><span data-stu-id="05d81-265">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags:</span></span>

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    <span data-ttu-id="05d81-266">Bu UI benzer *`ExpenseItHome.xaml`*, rapor verileri dışında <xref:System.Windows.Controls.DataGrid>bir .</span><span class="sxs-lookup"><span data-stu-id="05d81-266">This UI is similar to *`ExpenseItHome.xaml`*, except the report data is displayed in a <xref:System.Windows.Controls.DataGrid>.</span></span>

3. <span data-ttu-id="05d81-267">Uygulamayı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="05d81-267">Build and run the application.</span></span>

4. <span data-ttu-id="05d81-268">**Görünüm** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="05d81-268">Select the **View** button.</span></span>

    <span data-ttu-id="05d81-269">Gider raporu sayfası görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="05d81-269">The expense report page appears.</span></span> <span data-ttu-id="05d81-270">Ayrıca, geri navigasyon düğmesinin etkin olduğunu da unutmayın.</span><span class="sxs-lookup"><span data-stu-id="05d81-270">Also notice that the back navigation button is enabled.</span></span>

<span data-ttu-id="05d81-271">Aşağıdaki resimde *ExpenseReportPage.xaml'a*eklenen UI öğeleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="05d81-271">The following illustration shows the UI elements added to *ExpenseReportPage.xaml*.</span></span>

![ExpenseReportPage için oluşturulan UI'yi gösteren örnek ekran görüntüsü.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

## <a name="style-controls"></a><span data-ttu-id="05d81-273">Stil denetimleri</span><span class="sxs-lookup"><span data-stu-id="05d81-273">Style controls</span></span>

<span data-ttu-id="05d81-274">Çeşitli öğelerin görünümü genellikle bir UI aynı türdeki tüm öğeler için aynıdır.</span><span class="sxs-lookup"><span data-stu-id="05d81-274">The appearance of various elements is often the same for all elements of the same type in a UI.</span></span> <span data-ttu-id="05d81-275">UI, görünümleri birden çok öğe arasında yeniden kullanılabilir hale getirmek için [stilleri](../controls/styling-and-templating.md) kullanır.</span><span class="sxs-lookup"><span data-stu-id="05d81-275">UI uses [styles](../controls/styling-and-templating.md) to make appearances reusable across multiple elements.</span></span> <span data-ttu-id="05d81-276">Stillerin yeniden kullanılabilirliği XAML oluşturma ve yönetimini basitleştirmeye yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="05d81-276">The reusability of styles helps to simplify XAML creation and management.</span></span> <span data-ttu-id="05d81-277">Bu bölüm, önceki adımlarda tanımlanan öğe başına öznitelikleri stilleri ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="05d81-277">This section replaces the per-element attributes that were defined in previous steps with styles.</span></span>

1. <span data-ttu-id="05d81-278">*Açık Uygulama.xaml* veya *App.xaml*.</span><span class="sxs-lookup"><span data-stu-id="05d81-278">Open *Application.xaml* or *App.xaml*.</span></span>

2. <span data-ttu-id="05d81-279">Etiketler arasına aşağıdaki XAML'yi <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> ekleyin:</span><span class="sxs-lookup"><span data-stu-id="05d81-279">Add the following XAML between the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tags:</span></span>

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    <span data-ttu-id="05d81-280">Bu XAML aşağıdaki stilleri ekler:</span><span class="sxs-lookup"><span data-stu-id="05d81-280">This XAML adds the following styles:</span></span>

    - <span data-ttu-id="05d81-281">`headerTextStyle`: Sayfa başlığını <xref:System.Windows.Controls.Label>biçimlendirmek için .</span><span class="sxs-lookup"><span data-stu-id="05d81-281">`headerTextStyle`: To format the page title <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="05d81-282">`labelStyle`: Denetimleri <xref:System.Windows.Controls.Label> biçimlendirmek için.</span><span class="sxs-lookup"><span data-stu-id="05d81-282">`labelStyle`: To format the <xref:System.Windows.Controls.Label> controls.</span></span>

    - <span data-ttu-id="05d81-283">`columnHeaderStyle`: Biçimlendirmek <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>için .</span><span class="sxs-lookup"><span data-stu-id="05d81-283">`columnHeaderStyle`: To format the <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span></span>

    - <span data-ttu-id="05d81-284">`listHeaderStyle`: Liste üstbilgi <xref:System.Windows.Controls.Border> denetimlerini biçimlendirmek için.</span><span class="sxs-lookup"><span data-stu-id="05d81-284">`listHeaderStyle`: To format the list header <xref:System.Windows.Controls.Border> controls.</span></span>

    - <span data-ttu-id="05d81-285">`listHeaderTextStyle`: Liste üstbilgisini <xref:System.Windows.Controls.Label>biçimlendirmek için .</span><span class="sxs-lookup"><span data-stu-id="05d81-285">`listHeaderTextStyle`: To format the list header <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="05d81-286">`buttonStyle`: Üzerinde `ExpenseItHome.xaml` <xref:System.Windows.Controls.Button> biçimlendirmek için .</span><span class="sxs-lookup"><span data-stu-id="05d81-286">`buttonStyle`: To format the <xref:System.Windows.Controls.Button> on `ExpenseItHome.xaml`.</span></span>

    <span data-ttu-id="05d81-287">Stillerin özellik öğesinin kaynakları <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> ve çocukları olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="05d81-287">Notice that the styles are resources and children of the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> property element.</span></span> <span data-ttu-id="05d81-288">Bu konumda, stilleri bir uygulamadaki tüm öğelere uygulanır.</span><span class="sxs-lookup"><span data-stu-id="05d81-288">In this location, the styles are applied to all the elements in an application.</span></span> <span data-ttu-id="05d81-289">Bir .NET uygulamasında kaynakları kullanma örneği [için](../advanced/how-to-use-application-resources.md)bkz.</span><span class="sxs-lookup"><span data-stu-id="05d81-289">For an example of using resources in a .NET app, see [Use Application Resources](../advanced/how-to-use-application-resources.md).</span></span>

3. <span data-ttu-id="05d81-290">In *`ExpenseItHome.xaml`*, <xref:System.Windows.Controls.Grid> aşağıdaki XAML ile öğeler arasındaki her şeyi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="05d81-290">In *`ExpenseItHome.xaml`*, replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    <span data-ttu-id="05d81-291">Her denetimin <xref:System.Windows.VerticalAlignment> <xref:System.Windows.Media.FontFamily> görünümünü tanımlayan özellikler kaldırılır ve stilleri uygulanarak değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="05d81-291">The properties such as <xref:System.Windows.VerticalAlignment> and <xref:System.Windows.Media.FontFamily> that define the look of each control are removed and replaced by applying the styles.</span></span> <span data-ttu-id="05d81-292">Örneğin, `headerTextStyle` "Görünüm Gider Raporu"na <xref:System.Windows.Controls.Label>uygulanır.</span><span class="sxs-lookup"><span data-stu-id="05d81-292">For example, the `headerTextStyle` is applied to the "View Expense Report" <xref:System.Windows.Controls.Label>.</span></span>

4. <span data-ttu-id="05d81-293">*Açık GiderReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="05d81-293">Open *ExpenseReportPage.xaml*.</span></span>

5. <span data-ttu-id="05d81-294"><xref:System.Windows.Controls.Grid> Öğeler arasındaki her şeyi aşağıdaki XAML ile değiştirin:</span><span class="sxs-lookup"><span data-stu-id="05d81-294">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    <span data-ttu-id="05d81-295">Bu XAML stilleri <xref:System.Windows.Controls.Label> ve <xref:System.Windows.Controls.Border> öğeleri ekler.</span><span class="sxs-lookup"><span data-stu-id="05d81-295">This XAML adds styles to the <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Border> elements.</span></span>

6. <span data-ttu-id="05d81-296">Uygulamayı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="05d81-296">Build and run the application.</span></span> <span data-ttu-id="05d81-297">Pencere görünümü öncekiyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="05d81-297">The window appearance is the same as previously.</span></span>

    ![GiderÖnceki bölümde ki görünüme sahip örnek ekran görüntüsü.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

7. <span data-ttu-id="05d81-299">Visual Studio'ya dönmek için uygulamayı kapatın.</span><span class="sxs-lookup"><span data-stu-id="05d81-299">Close the application to return to Visual Studio.</span></span>

## <a name="bind-data-to-a-control"></a><span data-ttu-id="05d81-300">Verileri denetime bağlama</span><span class="sxs-lookup"><span data-stu-id="05d81-300">Bind data to a control</span></span>

<span data-ttu-id="05d81-301">Bu bölümde, çeşitli denetimlere bağlı XML verileri oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="05d81-301">In this section, you'll create the XML data that is bound to various controls.</span></span>

1. <span data-ttu-id="05d81-302">Açılış *`ExpenseItHome.xaml`* <xref:System.Windows.Controls.Grid> öğesinden sonra, her kişi için verileri <xref:System.Windows.Data.XmlDataProvider> içeren bir tane oluşturmak için aşağıdaki XAML'yi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="05d81-302">In *`ExpenseItHome.xaml`*, after the opening <xref:System.Windows.Controls.Grid> element, add the following XAML to create an <xref:System.Windows.Data.XmlDataProvider> that contains the data for each person:</span></span>

    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,16-40,49)]

    <span data-ttu-id="05d81-303">Veriler kaynak <xref:System.Windows.Controls.Grid> olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="05d81-303">The data is created as a <xref:System.Windows.Controls.Grid> resource.</span></span> <span data-ttu-id="05d81-304">Normalde bu veriler bir dosya olarak yüklenir, ancak basitlik için veriler satır satıreklenir.</span><span class="sxs-lookup"><span data-stu-id="05d81-304">Normally this data would be loaded as a file, but for simplicity the data is added inline.</span></span>

2. <span data-ttu-id="05d81-305">Öğe `<Grid.Resources>` içinde, `<XmlDataProvider>` aşağıdaki `<xref:System.Windows.DataTemplate>` öğeyi ekleyin, hangi veri görüntülemek <xref:System.Windows.Controls.ListBox>için nasıl tanımlar , öğesonra:</span><span class="sxs-lookup"><span data-stu-id="05d81-305">Within the `<Grid.Resources>` element, add the following `<xref:System.Windows.DataTemplate>` element, which defines how to display the data in the <xref:System.Windows.Controls.ListBox>, after the `<XmlDataProvider>` element:</span></span>

    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,43-46,49)]

    <span data-ttu-id="05d81-306">Veri şablonları hakkında daha fazla bilgi için [bkz.](../data/data-templating-overview.md)</span><span class="sxs-lookup"><span data-stu-id="05d81-306">For more information about data templates, see [Data templating overview](../data/data-templating-overview.md).</span></span>

3. <span data-ttu-id="05d81-307">Varolan <xref:System.Windows.Controls.ListBox> xaml'ı aşağıdaki XAML ile değiştirin:</span><span class="sxs-lookup"><span data-stu-id="05d81-307">Replace the existing <xref:System.Windows.Controls.ListBox> with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    <span data-ttu-id="05d81-308">Bu XAML, veri <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> kaynağının <xref:System.Windows.Controls.ListBox> özelliğini bağlar ve veri şablonu <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span><span class="sxs-lookup"><span data-stu-id="05d81-308">This XAML binds the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to the data source and applies the data template as the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span></span>

## <a name="connect-data-to-controls"></a><span data-ttu-id="05d81-309">Verileri denetimlere bağlama</span><span class="sxs-lookup"><span data-stu-id="05d81-309">Connect data to controls</span></span>

<span data-ttu-id="05d81-310">Ardından, **`ExpenseItHome`** sayfada seçilen adı almak için kod ekler ve **GiderReportPage'in**oluşturucusuna iletirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05d81-310">Next, you'll add code to retrieve the name that's selected on the **`ExpenseItHome`** page and pass it to the constructor of **ExpenseReportPage**.</span></span> <span data-ttu-id="05d81-311">**ExpenseReportPage,** *harcamaReportPage.xaml* bağlamada tanımlanan denetimlerin aktarDığı öğeyle veri bağlamını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="05d81-311">**ExpenseReportPage** sets its data context with the passed item, which is what the controls defined in *ExpenseReportPage.xaml* bind to.</span></span>

1. <span data-ttu-id="05d81-312">*Açık GiderReportPage.xaml.vb* veya *ExpenseReportPage.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="05d81-312">Open *ExpenseReportPage.xaml.vb* or *ExpenseReportPage.xaml.cs*.</span></span>

2. <span data-ttu-id="05d81-313">Seçili kişinin gider raporu verilerini geçirebilmeniz için nesne alan bir oluşturucu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="05d81-313">Add a constructor that takes an object so you can pass the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. <span data-ttu-id="05d81-314">Aç *`ExpenseItHome.xaml.vb`* *`ExpenseItHome.xaml.cs`* veya .</span><span class="sxs-lookup"><span data-stu-id="05d81-314">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

4. <span data-ttu-id="05d81-315"><xref:System.Windows.Controls.Primitives.ButtonBase.Click> Seçilen kişinin gider raporu verilerini geçen yeni oluşturucuyu çağırmak için olay işleyicisini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="05d81-315">Change the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to call the new constructor passing the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a><span data-ttu-id="05d81-316">Veri şablonları ile stil verileri</span><span class="sxs-lookup"><span data-stu-id="05d81-316">Style data with data templates</span></span>

<span data-ttu-id="05d81-317">Bu bölümde, veri şablonlarını kullanarak veri ye bağlı listelerdeki her öğe için Kullanıcı Arabirimi'ni güncelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05d81-317">In this section, you'll update the UI for each item in the data-bound lists by using data templates.</span></span>

1. <span data-ttu-id="05d81-318">*Açık GiderReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="05d81-318">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="05d81-319">"Ad" ve "Departman" <xref:System.Windows.Controls.Label> öğelerinin içeriğini uygun veri kaynağı özelliğine bağla.</span><span class="sxs-lookup"><span data-stu-id="05d81-319">Bind the content of the "Name" and "Department" <xref:System.Windows.Controls.Label> elements to the appropriate data source property.</span></span> <span data-ttu-id="05d81-320">Veri bağlama hakkında daha fazla bilgi için [bkz.](../../../desktop-wpf/data/data-binding-overview.md)</span><span class="sxs-lookup"><span data-stu-id="05d81-320">For more information about data binding, see [Data binding overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. <span data-ttu-id="05d81-321">Açılış <xref:System.Windows.Controls.Grid> öğesinden sonra, gider raporu verilerinin nasıl görüntüleyeceğini tanımlayan aşağıdaki veri şablonlarını ekleyin:</span><span class="sxs-lookup"><span data-stu-id="05d81-321">After the opening <xref:System.Windows.Controls.Grid> element, add the following data templates, which define how to display the expense report data:</span></span>

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. <span data-ttu-id="05d81-322">Öğeleri <xref:System.Windows.Controls.DataGridTextColumn> öğenin <xref:System.Windows.Controls.DataGridTemplateColumn> <xref:System.Windows.Controls.DataGrid> altında değiştirin ve şablonları onlara uygulayın.</span><span class="sxs-lookup"><span data-stu-id="05d81-322">Replace the <xref:System.Windows.Controls.DataGridTextColumn> elements with <xref:System.Windows.Controls.DataGridTemplateColumn> under the <xref:System.Windows.Controls.DataGrid> element and apply the templates to them.</span></span>

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. <span data-ttu-id="05d81-323">Uygulamayı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="05d81-323">Build and run the application.</span></span>

6. <span data-ttu-id="05d81-324">Bir kişi seçin ve ardından **Görünüm** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="05d81-324">Select a person and then select the **View** button.</span></span>

<span data-ttu-id="05d81-325">Aşağıdaki resimde, uygulamanın `ExpenseIt` denetimleri, düzeni, stilleri, veri bağlama ve uygulanan veri şablonları ile her iki sayfa gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="05d81-325">The following illustration shows both pages of the `ExpenseIt` application with controls, layout, styles, data binding, and data templates applied:</span></span>

![Ad listesini ve gider raporunu gösteren uygulamanın her iki sayfası.](./media/walkthrough-my-first-wpf-desktop-application/application-data-templates.png)

> [!NOTE]
> <span data-ttu-id="05d81-327">Bu örnek WPF'nin belirli bir özelliğini gösterir ve güvenlik, yerelleştirme ve erişilebilirlik gibi şeyler için en iyi tüm uygulamaları izlemez.</span><span class="sxs-lookup"><span data-stu-id="05d81-327">This sample demonstrates a specific feature of WPF and doesn't follow all best practices for things like security, localization, and accessibility.</span></span> <span data-ttu-id="05d81-328">WPF ve .NET uygulama geliştirme en iyi uygulamaları kapsamlı kapsama alanı için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="05d81-328">For comprehensive coverage of WPF and the .NET app development best practices, see the following topics:</span></span>
>
> - [<span data-ttu-id="05d81-329">Erişilebilirlik</span><span class="sxs-lookup"><span data-stu-id="05d81-329">Accessibility</span></span>](../../ui-automation/accessibility-best-practices.md)
> - [<span data-ttu-id="05d81-330">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="05d81-330">Security</span></span>](../security-wpf.md)
> - [<span data-ttu-id="05d81-331">WPF küreselleşmeve yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="05d81-331">WPF globalization and localization</span></span>](../advanced/wpf-globalization-and-localization-overview.md)
> - [<span data-ttu-id="05d81-332">WPF performansı</span><span class="sxs-lookup"><span data-stu-id="05d81-332">WPF performance</span></span>](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a><span data-ttu-id="05d81-333">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="05d81-333">Next steps</span></span>

<span data-ttu-id="05d81-334">Bu walkthrough windows presentation foundation (WPF) kullanarak bir ui oluşturmak için bir dizi teknik öğrendim.</span><span class="sxs-lookup"><span data-stu-id="05d81-334">In this walkthrough you learned a number of techniques for creating a UI using Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="05d81-335">Artık veriye bağlı bir .NET uygulamasının yapı taşları hakkında temel bir anlayışa sahip olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="05d81-335">You should now have a basic understanding of the building blocks of a data-bound .NET app.</span></span> <span data-ttu-id="05d81-336">WPF mimarisi ve programlama modelleri hakkında daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="05d81-336">For more information about the WPF architecture and programming models, see the following topics:</span></span>

- [<span data-ttu-id="05d81-337">WPF mimarisi</span><span class="sxs-lookup"><span data-stu-id="05d81-337">WPF architecture</span></span>](../advanced/wpf-architecture.md)
- [<span data-ttu-id="05d81-338">XAML genel bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="05d81-338">XAML overview (WPF)</span></span>](../advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="05d81-339">Bağımlılık özelliklerine genel bakış</span><span class="sxs-lookup"><span data-stu-id="05d81-339">Dependency properties overview</span></span>](../advanced/dependency-properties-overview.md)
- [<span data-ttu-id="05d81-340">Düzen</span><span class="sxs-lookup"><span data-stu-id="05d81-340">Layout</span></span>](../advanced/layout.md)

<span data-ttu-id="05d81-341">Uygulama oluşturma hakkında daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="05d81-341">For more information about creating applications, see the following topics:</span></span>

- [<span data-ttu-id="05d81-342">Uygulama geliştirme</span><span class="sxs-lookup"><span data-stu-id="05d81-342">Application development</span></span>](../app-development/index.md)
- [<span data-ttu-id="05d81-343">Denetimler</span><span class="sxs-lookup"><span data-stu-id="05d81-343">Controls</span></span>](../controls/index.md)
- [<span data-ttu-id="05d81-344">Veri bağlamaya genel bakış</span><span class="sxs-lookup"><span data-stu-id="05d81-344">Data binding overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="05d81-345">Grafik ve multimedya</span><span class="sxs-lookup"><span data-stu-id="05d81-345">Graphics and multimedia</span></span>](../graphics-multimedia/index.md)
- [<span data-ttu-id="05d81-346">WPF'deki Belgeler</span><span class="sxs-lookup"><span data-stu-id="05d81-346">Documents in WPF</span></span>](../advanced/documents-in-wpf.md)

## <a name="see-also"></a><span data-ttu-id="05d81-347">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05d81-347">See also</span></span>

- [<span data-ttu-id="05d81-348">Paneller genel bakış</span><span class="sxs-lookup"><span data-stu-id="05d81-348">Panels overview</span></span>](../controls/panels-overview.md)
- [<span data-ttu-id="05d81-349">Veri cazip genel bakış</span><span class="sxs-lookup"><span data-stu-id="05d81-349">Data templating overview</span></span>](../data/data-templating-overview.md)
- [<span data-ttu-id="05d81-350">WPF uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="05d81-350">Build a WPF application</span></span>](../app-development/building-a-wpf-application-wpf.md)
- [<span data-ttu-id="05d81-351">Stiller ve şablonlar</span><span class="sxs-lookup"><span data-stu-id="05d81-351">Styles and templates</span></span>](../controls/styles-and-templates.md)
