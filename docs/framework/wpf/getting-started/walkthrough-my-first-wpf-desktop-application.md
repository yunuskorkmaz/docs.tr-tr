---
title: "İzlenecek yol: İlk WPF Masaüstü Uygulamam"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
caps.latest.revision: "71"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3667d507f4c35174c1e888c9781b5f74ffd496a0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a><span data-ttu-id="ae779-102">İzlenecek yol: İlk WPF Masaüstü Uygulamam</span><span class="sxs-lookup"><span data-stu-id="ae779-102">Walkthrough: My first WPF desktop application</span></span>
<span data-ttu-id="ae779-103">Bu kılavuzda geliştirilmesini tanıtılmaktadır bir [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] en yaygın olan öğeleri içeren uygulama [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulamalar: [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] biçimlendirme, arka plan kodu, uygulama tanımları, denetimleri, düzeni veri bağlama ve stiller.</span><span class="sxs-lookup"><span data-stu-id="ae779-103">This walkthrough provides an introduction to the development of a [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] application that includes the elements that are common to most [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications: [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] markup, code-behind, application definitions, controls, layout, data binding, and styles.</span></span> 
  
 <span data-ttu-id="ae779-104">Bu kılavuz, basit bir geliştirme size rehberlik eder [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aşağıdaki adımları kullanarak uygulama.</span><span class="sxs-lookup"><span data-stu-id="ae779-104">This walkthrough guides you through the development of a simple [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application using the following steps.</span></span> 
  
-   <span data-ttu-id="ae779-105">Tanımlama [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] uygulamanın görünümünü tasarlamak için [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ae779-105">Defining [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] to design the appearance of the application's [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span> 
  
-   <span data-ttu-id="ae779-106">Uygulamanın davranışını oluşturmak için kod yazma.</span><span class="sxs-lookup"><span data-stu-id="ae779-106">Writing code to build the application's behavior.</span></span> 
  
-   <span data-ttu-id="ae779-107">Uygulamasını yönetmek için bir uygulama tanımını oluşturma.</span><span class="sxs-lookup"><span data-stu-id="ae779-107">Creating an application definition to manage the application.</span></span> 
  
-   <span data-ttu-id="ae779-108">Denetimler ekleme ve uygulama oluşturmak için düzen oluşturma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ae779-108">Adding controls and creating the layout to compose the application [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].</span></span> 
  
-   <span data-ttu-id="ae779-109">Bir uygulamanın genelinde tutarlı bir görünüm oluşturmak için stiller oluşturma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ae779-109">Creating styles to create a consistent appearance throughout an application's [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].</span></span> 
  
-   <span data-ttu-id="ae779-110">Bağlama [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] her ikisine de verilere doldurmak [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] veri ve canlı verileri ve [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] eşitlenir.</span><span class="sxs-lookup"><span data-stu-id="ae779-110">Binding the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to data to both populate the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] from data and keep the data and [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] synchronized.</span></span> 
  
 <span data-ttu-id="ae779-111">İzlenecek yol ucu tarafından bir tek başına oluşturacaksınız [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] kullanıcıların seçilen kişiler için harcama raporlarını görüntülemesine olanak sağlayan uygulama.</span><span class="sxs-lookup"><span data-stu-id="ae779-111">By the end of the walkthrough, you will have built a standalone [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] application that allows users to view expense reports for selected people.</span></span> <span data-ttu-id="ae779-112">Uygulamayı birkaç oluşacaktır [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tarayıcı stili pencerede barındırılan sayfaları.</span><span class="sxs-lookup"><span data-stu-id="ae779-112">The application will be composed of several [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pages that are hosted in a browser-style window.</span></span> 
  
 <span data-ttu-id="ae779-113">Bu izlenecek yolu oluşturmak için kullanılan örnek kod için kullanılabilir [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] ve [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] adresindeki [WPF uygulamalarını giriş](http://go.microsoft.com/fwlink/?LinkID=160008).</span><span class="sxs-lookup"><span data-stu-id="ae779-113">The sample code that is used to build this walkthrough is available for both [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] and [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] at  [Introduction to Building WPF Applications](http://go.microsoft.com/fwlink/?LinkID=160008).</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="ae779-114">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="ae779-114">Prerequisites</span></span>  

- [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="ae779-115">veya üzeri</span><span class="sxs-lookup"><span data-stu-id="ae779-115"> or later</span></span>

<span data-ttu-id="ae779-116">Visual Studio en son sürümünü yükleme hakkında daha fazla bilgi için bkz: [Visual Studio yükleme](/visualstudio/install/install-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="ae779-116">For more information about installing the latest version of Visual Studio, see [Install Visual Studio](/visualstudio/install/install-visual-studio).</span></span>
  
## <a name="creating-the-application-project"></a><span data-ttu-id="ae779-117">Uygulama projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="ae779-117">Creating the application project</span></span>  
 <span data-ttu-id="ae779-118">Bu bölümde, uygulama tanımı, iki sayfaları ve görüntü içeren uygulama altyapısı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ae779-118">In this section, you create the application infrastructure, which includes an application definition, two pages, and an image.</span></span> 
  
1. <span data-ttu-id="ae779-119">Visual Basic veya Visual C# adlı yeni bir WPF uygulaması projesi oluşturduğunuzda `ExpenseIt`.</span><span class="sxs-lookup"><span data-stu-id="ae779-119">Create a new WPF Application project in Visual Basic or Visual C# named `ExpenseIt`.</span></span> <span data-ttu-id="ae779-120">Daha fazla bilgi için bkz: [nasıl yapılır: yeni bir WPF uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span><span class="sxs-lookup"><span data-stu-id="ae779-120">For more information, see [How to: Create a New WPF Application Project](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span></span> 
  
    > [!NOTE]
    >  <span data-ttu-id="ae779-121">Bu kılavuzda kullanılır <xref:System.Windows.Controls.DataGrid> .NET Framework 4'te kullanılabilir denetim.</span><span class="sxs-lookup"><span data-stu-id="ae779-121">This walkthrough uses the <xref:System.Windows.Controls.DataGrid> control that is available in the .NET Framework 4.</span></span> <span data-ttu-id="ae779-122">Sonraki veya projeniz .NET Framework 4 hedefleyen emin olun.</span><span class="sxs-lookup"><span data-stu-id="ae779-122">Be sure that your project targets the .NET Framework 4 or later.</span></span> <span data-ttu-id="ae779-123">Daha fazla bilgi için bkz:[nasıl yapılır: .NET Framework sürümü hedef](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span><span class="sxs-lookup"><span data-stu-id="ae779-123">For more information, see[How to: Target a Version of the .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span></span> 
  
2. <span data-ttu-id="ae779-124">Application.xaml (Visual Basic) veya App.xaml (C#) açın.</span><span class="sxs-lookup"><span data-stu-id="ae779-124">Open Application.xaml (Visual Basic) or App.xaml (C#).</span></span> 
  
     <span data-ttu-id="ae779-125">Bu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya tanımlayan bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulama ve uygulama kaynaklarını.</span><span class="sxs-lookup"><span data-stu-id="ae779-125">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file defines a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application and any application resources.</span></span> <span data-ttu-id="ae779-126">Bu dosyayı belirtmek için de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] otomatik olarak uygulama başladığında; gösteren bu durumda, MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="ae779-126">You also use this file to specify the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] that automatically shows when the application starts; in this case, MainWindow.xaml.</span></span> 
  
     <span data-ttu-id="ae779-127">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Visual Basic'te gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="ae779-127">Your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] should look like this in Visual Basic:</span></span>  
  
    [!code-xaml[ExpenseIt#1_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]  
  
     <span data-ttu-id="ae779-128">Ya da böyle C#:</span><span class="sxs-lookup"><span data-stu-id="ae779-128">Or like this in C#:</span></span>  
  
    [!code-xaml[ExpenseIt#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]  
  
3. <span data-ttu-id="ae779-129">MainWindow.xaml açın.</span><span class="sxs-lookup"><span data-stu-id="ae779-129">Open MainWindow.xaml.</span></span> 
  
     <span data-ttu-id="ae779-130">Bu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosyası, uygulamanızın ana penceresidir ve sayfalarda oluşturulan içeriği görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ae779-130">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file is the main window of your application and displays content created in pages.</span></span> <span data-ttu-id="ae779-131"><xref:System.Windows.Window> Sınıfı başlık, boyut veya simge, gibi bir pencere özelliklerini tanımlar ve kapatma veya gizleme gibi olayları işler.</span><span class="sxs-lookup"><span data-stu-id="ae779-131">The <xref:System.Windows.Window> class defines the properties of a window, such as its title, size, or icon, and handles events, such as closing or hiding.</span></span> 
  
4. <span data-ttu-id="ae779-132">Değişiklik <xref:System.Windows.Window> öğesine bir <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="ae779-132">Change the <xref:System.Windows.Window> element to a <xref:System.Windows.Navigation.NavigationWindow>.</span></span> 
  
     <span data-ttu-id="ae779-133">Bu uygulama kullanıcı etkileşimi bağlı olarak farklı içerik gider.</span><span class="sxs-lookup"><span data-stu-id="ae779-133">This application will navigate to different content depending on the user interaction.</span></span> <span data-ttu-id="ae779-134">Bu nedenle, ana <xref:System.Windows.Window> için değiştirilmesi gereken bir <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="ae779-134">Therefore, the main <xref:System.Windows.Window> needs to be changed to a <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="ae779-135"><xref:System.Windows.Navigation.NavigationWindow>tüm özelliklerini devralır <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="ae779-135"><xref:System.Windows.Navigation.NavigationWindow> inherits all the properties of <xref:System.Windows.Window>.</span></span> <span data-ttu-id="ae779-136"><xref:System.Windows.Navigation.NavigationWindow> XAML dosyası öğesinde bir örneğini oluşturur <xref:System.Windows.Navigation.NavigationWindow> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ae779-136">The <xref:System.Windows.Navigation.NavigationWindow> element in the XAML file creates an instance of the <xref:System.Windows.Navigation.NavigationWindow> class.</span></span> <span data-ttu-id="ae779-137">Daha fazla bilgi için bkz: [Gezinti genel bakış](../../../../docs/framework/wpf/app-development/navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ae779-137">For more information, see [Navigation Overview](../../../../docs/framework/wpf/app-development/navigation-overview.md).</span></span> 
  
5. <span data-ttu-id="ae779-138">Aşağıdaki özellikleri değiştirin <xref:System.Windows.Navigation.NavigationWindow> öğe:</span><span class="sxs-lookup"><span data-stu-id="ae779-138">Change the following properties on the <xref:System.Windows.Navigation.NavigationWindow> element:</span></span>  
  
    -   <span data-ttu-id="ae779-139">Ayarlama <xref:System.Windows.Window.Title%2A> özelliğini "ExpenseIt".</span><span class="sxs-lookup"><span data-stu-id="ae779-139">Set the <xref:System.Windows.Window.Title%2A> property to "ExpenseIt".</span></span> 
  
    -   <span data-ttu-id="ae779-140">Ayarlama <xref:System.Windows.FrameworkElement.Width%2A> özelliğini 500 piksel.</span><span class="sxs-lookup"><span data-stu-id="ae779-140">Set the <xref:System.Windows.FrameworkElement.Width%2A> property to 500 pixels.</span></span> 
  
    -   <span data-ttu-id="ae779-141">Ayarlama <xref:System.Windows.FrameworkElement.Height%2A> özelliğini 350 piksel.</span><span class="sxs-lookup"><span data-stu-id="ae779-141">Set the <xref:System.Windows.FrameworkElement.Height%2A> property to 350 pixels.</span></span> 
  
    -   <span data-ttu-id="ae779-142">Kaldırma <xref:System.Windows.Controls.Grid> öğeleri arasında <xref:System.Windows.Navigation.NavigationWindow> etiketler.</span><span class="sxs-lookup"><span data-stu-id="ae779-142">Remove the <xref:System.Windows.Controls.Grid> elements between the <xref:System.Windows.Navigation.NavigationWindow> tags.</span></span> 
  
     <span data-ttu-id="ae779-143">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Visual Basic'te gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="ae779-143">Your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] should look like this in Visual Basic:</span></span>  
  
    [!code-xaml[ExpenseIt#2_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]  
  
     <span data-ttu-id="ae779-144">Ya da böyle C#:</span><span class="sxs-lookup"><span data-stu-id="ae779-144">Or like this in C#:</span></span>  
  
    [!code-xaml[ExpenseIt#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]  
  
6. <span data-ttu-id="ae779-145">MainWindow.xaml.vb veya MainWindow.xaml.cs açın.</span><span class="sxs-lookup"><span data-stu-id="ae779-145">Open MainWindow.xaml.vb or MainWindow.xaml.cs.</span></span> 
  
     <span data-ttu-id="ae779-146">Bu dosya MainWindow.xaml içinde bildirilen olayları işlemek için kod içeren bir arka plan kodu dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae779-146">This file is a code-behind file that contains code to handle the events declared in MainWindow.xaml.</span></span> <span data-ttu-id="ae779-147">Bu dosya XAML içinde tanımlanan penceresi için bir parçalı sınıf içerir.</span><span class="sxs-lookup"><span data-stu-id="ae779-147">This file contains a partial class for the window defined in XAML.</span></span> 
  
7. <span data-ttu-id="ae779-148">C# kullanıyorsanız değiştirme `MainWindow` öğesinden türetilen sınıf <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="ae779-148">If you are using C#, change the `MainWindow` class to derive from <xref:System.Windows.Navigation.NavigationWindow>.</span></span> 
  
     <span data-ttu-id="ae779-149">XAML penceresinde değiştirdiğinizde, Visual Basic'te, bu otomatik olarak gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="ae779-149">In Visual Basic, this happens automatically when you change the window in XAML.</span></span> 
  
     <span data-ttu-id="ae779-150">Kodunuzu aşağıdaki gibi görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="ae779-150">Your code should look like this.</span></span> 
  
    [!code-csharp[ExpenseIt#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml.cs#3)]
    [!code-vb[ExpenseIt#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml.vb#3)]  
  
## <a name="adding-files-to-the-application"></a><span data-ttu-id="ae779-151">Dosyalar için uygulama ekleme</span><span class="sxs-lookup"><span data-stu-id="ae779-151">Adding files to the application</span></span>  
 <span data-ttu-id="ae779-152">Bu bölümde, uygulamaya iki sayfaları ve görüntü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ae779-152">In this section, you add two pages and an image to the application.</span></span> 
  
1. <span data-ttu-id="ae779-153">Yeni sayfa (WPF) adlı projeye eklemek `ExpenseItHome.xaml`.</span><span class="sxs-lookup"><span data-stu-id="ae779-153">Add a new Page (WPF) to the project named `ExpenseItHome.xaml`.</span></span> <span data-ttu-id="ae779-154">Daha fazla bilgi için bkz: [nasıl yapılır: bir WPF projesi için yeni öğeler eklemek](http://msdn.microsoft.com/en-us/17e6b238-fc32-4385-98ef-2f66ca09d9ad).</span><span class="sxs-lookup"><span data-stu-id="ae779-154">For more information, see [How to: Add New Items to a WPF Project](http://msdn.microsoft.com/en-us/17e6b238-fc32-4385-98ef-2f66ca09d9ad).</span></span> 
  
     <span data-ttu-id="ae779-155">Uygulama başlatıldığında görüntülenen ilk sayfa sayfasıdır.</span><span class="sxs-lookup"><span data-stu-id="ae779-155">This page is the first page that is displayed when the application is launched.</span></span> <span data-ttu-id="ae779-156">Bir kullanıcı için harcama raporunu göstermek için bir kişinin seçebileceği kişilerin listesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ae779-156">It will show a list of people from which a user can select a person to show an expense report for.</span></span> 
  
2. <span data-ttu-id="ae779-157">ExpenseItHome.xaml açın.</span><span class="sxs-lookup"><span data-stu-id="ae779-157">Open ExpenseItHome.xaml.</span></span> 
  
3. <span data-ttu-id="ae779-158">Ayarlama <xref:System.Windows.Controls.Page.Title%2A> "ExpenseIt - Giriş".</span><span class="sxs-lookup"><span data-stu-id="ae779-158">Set the <xref:System.Windows.Controls.Page.Title%2A> to "ExpenseIt - Home".</span></span> 
  
     <span data-ttu-id="ae779-159">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Visual Basic'te gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="ae779-159">Your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] should look like this in Visual Basic:</span></span>  
  
    [!code-xaml[ExpenseIt#6_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]  
  
     <span data-ttu-id="ae779-160">Veya bu C#:</span><span class="sxs-lookup"><span data-stu-id="ae779-160">Or this in C#:</span></span>  
  
    [!code-xaml[ExpenseIt#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]  
  
4. <span data-ttu-id="ae779-161">MainWindow.xaml açın.</span><span class="sxs-lookup"><span data-stu-id="ae779-161">Open MainWindow.xaml.</span></span> 
  
5. <span data-ttu-id="ae779-162">Ayarlama <xref:System.Windows.Navigation.NavigationWindow.Source%2A> özellikte <xref:System.Windows.Navigation.NavigationWindow> "ExpenseItHome.xaml" için.</span><span class="sxs-lookup"><span data-stu-id="ae779-162">Set the <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property on the <xref:System.Windows.Navigation.NavigationWindow> to "ExpenseItHome.xaml".</span></span> 
  
     <span data-ttu-id="ae779-163">Bu uygulama başladığında açılan ilk sayfa olarak ExpenseItHome.xaml ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ae779-163">This sets ExpenseItHome.xaml to be the first page opened when the application starts.</span></span> <span data-ttu-id="ae779-164">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Visual Basic'te gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="ae779-164">Your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] should look like this in Visual Basic:</span></span>  
  
    [!code-xaml[ExpenseIt#7_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]  
  
     <span data-ttu-id="ae779-165">Veya bu C#:</span><span class="sxs-lookup"><span data-stu-id="ae779-165">Or this in C#:</span></span>  
  
    [!code-xaml[ExpenseIt#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]  
  
6. <span data-ttu-id="ae779-166">Yeni sayfa (WPF) adlı projeye eklemek `ExpenseReportPage.xaml`.</span><span class="sxs-lookup"><span data-stu-id="ae779-166">Add a new Page (WPF) to the project named `ExpenseReportPage.xaml`.</span></span> 
  
     <span data-ttu-id="ae779-167">Bu sayfa, ExpenseItHome.XAML üzerinde seçili kişi için harcama raporunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ae779-167">This page will show the expense report for the person that is selected on ExpenseItHome.xaml.</span></span> 
  
7. <span data-ttu-id="ae779-168">ExpenseReportPage.xaml açın.</span><span class="sxs-lookup"><span data-stu-id="ae779-168">Open ExpenseReportPage.xaml.</span></span> 
  
8. <span data-ttu-id="ae779-169">Ayarlama <xref:System.Windows.Controls.Page.Title%2A> "ExpenseIt - görünüm gider".</span><span class="sxs-lookup"><span data-stu-id="ae779-169">Set the <xref:System.Windows.Controls.Page.Title%2A> to "ExpenseIt - View Expense".</span></span> 
  
     <span data-ttu-id="ae779-170">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Visual Basic'te gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="ae779-170">Your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] should look like this in Visual Basic:</span></span>  
  
    [!code-xaml[ExpenseIt#4_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]  
  
     <span data-ttu-id="ae779-171">Veya bu C#:</span><span class="sxs-lookup"><span data-stu-id="ae779-171">Or this in C#:</span></span>  
  
    [!code-xaml[ExpenseIt#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]  
  
9. <span data-ttu-id="ae779-172">ExpenseItHome.xaml.vb ve ExpenseReportPage.xaml.vb veya ExpenseItHome.xaml.cs ve ExpenseReportPage.xaml.cs açın.</span><span class="sxs-lookup"><span data-stu-id="ae779-172">Open ExpenseItHome.xaml.vb and ExpenseReportPage.xaml.vb, or ExpenseItHome.xaml.cs and ExpenseReportPage.xaml.cs.</span></span> 
  
     <span data-ttu-id="ae779-173">Yeni bir sayfa dosyası oluşturduğunuzda, Visual Studio arka plan kod dosyasından otomatik olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ae779-173">When you create a new Page file, Visual Studio automatically creates a code behind file.</span></span> <span data-ttu-id="ae779-174">Bu arka plan kodu dosyaları için kullanıcı girişine yanıt mantığını işler.</span><span class="sxs-lookup"><span data-stu-id="ae779-174">These code-behind files handle the logic for responding to user input.</span></span> 
  
     <span data-ttu-id="ae779-175">Kodunuzu aşağıdaki gibi görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="ae779-175">Your code should look like this.</span></span> 
  
    [!code-csharp[ExpenseIt#2_5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]
    [!code-vb[ExpenseIt#2_5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]  
  
    [!code-csharp[ExpenseIt#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]
    [!code-vb[ExpenseIt#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]  
  
10. <span data-ttu-id="ae779-176">Projeye watermark.png adlı bir resim ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ae779-176">Add an image named watermark.png to the project.</span></span> <span data-ttu-id="ae779-177">Kendi görüntünüzü oluşturabilir veya örnek koddan dosyasını kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="ae779-177">You can either create your own image, or copy the file from the sample code.</span></span> <span data-ttu-id="ae779-178">Daha fazla bilgi için bkz: [NIB: nasıl yapılır: varolan bir proje öğeleri Ekle](http://msdn.microsoft.com/en-us/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).</span><span class="sxs-lookup"><span data-stu-id="ae779-178">For more information, see [NIB:How to: Add Existing Items to a Project](http://msdn.microsoft.com/en-us/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).</span></span> 

## <a name="building-and-running-the-application"></a><span data-ttu-id="ae779-179">Oluşturma ve uygulama çalıştırma</span><span class="sxs-lookup"><span data-stu-id="ae779-179">Building and running the application</span></span>  
 <span data-ttu-id="ae779-180">Bu bölümde, derleme ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ae779-180">In this section, you build and run the application.</span></span> 
  
1. <span data-ttu-id="ae779-181">Derleme ve seçin veya F5 tuşuna basarak uygulamayı çalıştırma **hata ayıklamayı Başlat** gelen **hata ayıklama** menüsü.</span><span class="sxs-lookup"><span data-stu-id="ae779-181">Build and run the application by pressing F5 or select **Start Debugging** from the **Debug** menu.</span></span> 
  
     <span data-ttu-id="ae779-182">Uygulamayla birlikte aşağıda gösterilmiştir <xref:System.Windows.Navigation.NavigationWindow> düğmeler.</span><span class="sxs-lookup"><span data-stu-id="ae779-182">The following illustration shows the application with the <xref:System.Windows.Navigation.NavigationWindow> buttons.</span></span> 
  
     <span data-ttu-id="ae779-183">![ExpenseIt örnek ekran görüntüsü](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure1.png "GettingStartedFigure1")</span><span class="sxs-lookup"><span data-stu-id="ae779-183">![ExpenseIt sample screen shot](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure1.png "GettingStartedFigure1")</span></span>  
  
2. <span data-ttu-id="ae779-184">Geri dönmek için uygulamayı kapatmak [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ae779-184">Close the application to return to [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span></span> 
  
## <a name="creating-the-layout"></a><span data-ttu-id="ae779-185">Düzen oluşturma</span><span class="sxs-lookup"><span data-stu-id="ae779-185">Creating the layout</span></span>  
 <span data-ttu-id="ae779-186">Düzen yerleştirmek için sıralı bir yol sağlar [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğeleri ve boyutunu ve konumunu bu öğelerin da yönetir, bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] boyutlandırılır.</span><span class="sxs-lookup"><span data-stu-id="ae779-186">Layout provides an ordered way to place [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements, and also manages the size and position of those elements when a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] is resized.</span></span> <span data-ttu-id="ae779-187">Genellikle bir düzen aşağıdaki düzen denetimlerinden biri ile oluşturursunuz:</span><span class="sxs-lookup"><span data-stu-id="ae779-187">You typically create a layout with one of the following layout controls:</span></span>  
  
-   <xref:System.Windows.Controls.Canvas>  
  
-   <xref:System.Windows.Controls.DockPanel>  
  
-   <xref:System.Windows.Controls.Grid>  
  
-   <xref:System.Windows.Controls.StackPanel>  
  
-   <xref:System.Windows.Controls.VirtualizingStackPanel>  
  
-   <xref:System.Windows.Controls.WrapPanel>  
  
 <span data-ttu-id="ae779-188">Bu düzen denetimlerinin her biri kendi alt öğeleri için özel türde bir düzen destekler.</span><span class="sxs-lookup"><span data-stu-id="ae779-188">Each of these layout controls supports a special type of layout for its child elements.</span></span> <span data-ttu-id="ae779-189">ExpenseIt sayfaları yeniden boyutlandırılabilir ve her sayfanın diğer öğeleri yatay ve dikey olarak düzenlenmiş öğesine sahip.</span><span class="sxs-lookup"><span data-stu-id="ae779-189">ExpenseIt pages can be resized, and each page has elements that are arranged horizontally and vertically alongside other elements.</span></span> <span data-ttu-id="ae779-190">Sonuç olarak, <xref:System.Windows.Controls.Grid> uygulama için ideal Düzen öğesidir.</span><span class="sxs-lookup"><span data-stu-id="ae779-190">Consequently, the <xref:System.Windows.Controls.Grid> is the ideal layout element for the application.</span></span> 
  
> [!NOTE]
>  <span data-ttu-id="ae779-191">Hakkında daha fazla bilgi için <xref:System.Windows.Controls.Panel> öğeler, bkz [paneller genel bakış](../../../../docs/framework/wpf/controls/panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ae779-191">For more information about <xref:System.Windows.Controls.Panel> elements, see [Panels Overview](../../../../docs/framework/wpf/controls/panels-overview.md).</span></span> <span data-ttu-id="ae779-192">Düzen hakkında daha fazla bilgi için bkz: [düzeni](../../../../docs/framework/wpf/advanced/layout.md).</span><span class="sxs-lookup"><span data-stu-id="ae779-192">For more information about layout, see [Layout](../../../../docs/framework/wpf/advanced/layout.md).</span></span> 
  
 <span data-ttu-id="ae779-193">Bölümünde, tek sütunlu bir tablo üç satır ve 10 piksel kenar boşluğu ile sütun ve satır tanımları ekleyerek oluşturduğunuz <xref:System.Windows.Controls.Grid> ExpenseItHome.XAML içinde.</span><span class="sxs-lookup"><span data-stu-id="ae779-193">In the section, you create a single-column table with three rows and a 10-pixel margin by adding column and row definitions to the <xref:System.Windows.Controls.Grid> in ExpenseItHome.xaml.</span></span> 
  
1. <span data-ttu-id="ae779-194">ExpenseItHome.xaml açın.</span><span class="sxs-lookup"><span data-stu-id="ae779-194">Open ExpenseItHome.xaml.</span></span> 
  
2. <span data-ttu-id="ae779-195">Ayarlama <xref:System.Windows.FrameworkElement.Margin%2A> özelliği <xref:System.Windows.Controls.Grid> , sol, üst, sağ ve alt kenar boşlukları için karşılık gelen "10,0,10,10"şeklinde öğesi.</span><span class="sxs-lookup"><span data-stu-id="ae779-195">Set the <xref:System.Windows.FrameworkElement.Margin%2A> property on the <xref:System.Windows.Controls.Grid> element to "10,0,10,10" which corresponds to left, top, right and bottom margins.</span></span> 
  
3. <span data-ttu-id="ae779-196">Aşağıdakileri ekleyin [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arasında <xref:System.Windows.Controls.Grid> satır ve sütun tanımları oluşturmak için etiketler.</span><span class="sxs-lookup"><span data-stu-id="ae779-196">Add the following [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] between the <xref:System.Windows.Controls.Grid> tags to create the row and column definitions.</span></span> 
  
    [!code-xaml[ExpenseIt#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]  
  
     <span data-ttu-id="ae779-197"><xref:System.Windows.Controls.RowDefinition.Height%2A> İki satır kümesine <xref:System.Windows.GridLength.Auto%2A> satırları boyutta olması anlamına temel satırları içerikte.</span><span class="sxs-lookup"><span data-stu-id="ae779-197">The <xref:System.Windows.Controls.RowDefinition.Height%2A> of two rows is set to <xref:System.Windows.GridLength.Auto%2A> which means that the rows will be sized base on the content in the rows.</span></span> <span data-ttu-id="ae779-198">Varsayılan <xref:System.Windows.Controls.RowDefinition.Height%2A> olan <xref:System.Windows.GridUnitType.Star> satır kullanılabilir alan ağırlıklı bir kısmının olacağı anlamına gelir boyutlandırma.</span><span class="sxs-lookup"><span data-stu-id="ae779-198">The default <xref:System.Windows.Controls.RowDefinition.Height%2A> is <xref:System.Windows.GridUnitType.Star> sizing, which means that the row will be a weighted proportion of the available space.</span></span> <span data-ttu-id="ae779-199">Her iki satır yüksekliği varsa, örneğin "*", her kullanılabilir alan yarısıdır yüksekliğe sahip olacaktır.</span><span class="sxs-lookup"><span data-stu-id="ae779-199">For example if two rows each have a height of "*", they will each have a height that is half of the available space.</span></span>  
  
     <span data-ttu-id="ae779-200"><xref:System.Windows.Controls.Grid> Aşağıdaki XAML gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="ae779-200">Your <xref:System.Windows.Controls.Grid> should now look like the following XAML:</span></span>  
  
    [!code-xaml[ExpenseIt#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]  
  
## <a name="adding-controls"></a><span data-ttu-id="ae779-201">Denetimler ekleme</span><span class="sxs-lookup"><span data-stu-id="ae779-201">Adding controls</span></span>  
 <span data-ttu-id="ae779-202">Bu bölümde, giriş sayfası [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kişilerin listesi kullanıcıların seçili kişiler için harcama raporunu göstermek için gösterebileceği olduğunu göstermek üzere güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="ae779-202">In this section, the home page [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] is updated to show a list of people that users can select from to show the expense report for a selected person.</span></span> <span data-ttu-id="ae779-203">Denetimler uygulamanız ile etkileşime girmesine izin veren UI nesneleridir.</span><span class="sxs-lookup"><span data-stu-id="ae779-203">Controls are UI objects that allow users to interact with your application.</span></span> <span data-ttu-id="ae779-204">Daha fazla bilgi için bkz: [denetimleri](../../../../docs/framework/wpf/controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="ae779-204">For more information, see [Controls](../../../../docs/framework/wpf/controls/index.md).</span></span> 
  
 <span data-ttu-id="ae779-205">Bu oluşturmak için [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], aşağıdaki öğeleri ExpenseItHome.xaml'e eklenir:</span><span class="sxs-lookup"><span data-stu-id="ae779-205">To create this [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], the following elements are added to ExpenseItHome.xaml:</span></span>  
  
-   <span data-ttu-id="ae779-206"><xref:System.Windows.Controls.ListBox>(listesi kişiler için).</span><span class="sxs-lookup"><span data-stu-id="ae779-206"><xref:System.Windows.Controls.ListBox> (for the list of people).</span></span> 
  
-   <span data-ttu-id="ae779-207"><xref:System.Windows.Controls.Label>(Liste üstbilgisi için).</span><span class="sxs-lookup"><span data-stu-id="ae779-207"><xref:System.Windows.Controls.Label> (for the list header).</span></span> 
  
-   <span data-ttu-id="ae779-208"><xref:System.Windows.Controls.Button>(listede seçilen kişi için harcama raporunu görüntülemek için tıklatın için).</span><span class="sxs-lookup"><span data-stu-id="ae779-208"><xref:System.Windows.Controls.Button> (to click to view the expense report for the person that is selected in the list).</span></span> 
  
 <span data-ttu-id="ae779-209">Her denetim bir satırda yerleştirilir <xref:System.Windows.Controls.Grid> ayarlayarak <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> özelliği eklenmiş.</span><span class="sxs-lookup"><span data-stu-id="ae779-209">Each control is placed in a row of the <xref:System.Windows.Controls.Grid> by setting the <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> attached property.</span></span> <span data-ttu-id="ae779-210">Ekli özellikler hakkında daha fazla bilgi için bkz: [bağlı özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ae779-210">For more information about attached properties, see [Attached Properties Overview](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).</span></span> 
  
1. <span data-ttu-id="ae779-211">ExpenseItHome.xaml açın.</span><span class="sxs-lookup"><span data-stu-id="ae779-211">Open ExpenseItHome.xaml.</span></span> 
  
2. <span data-ttu-id="ae779-212">Aşağıdakileri ekleyin [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arasında <xref:System.Windows.Controls.Grid> etiketler.</span><span class="sxs-lookup"><span data-stu-id="ae779-212">Add the following [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] between the <xref:System.Windows.Controls.Grid> tags.</span></span> 
  
    [!code-xaml[ExpenseIt#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]  
  
3. <span data-ttu-id="ae779-213">Derleme ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ae779-213">Build and run the application.</span></span> 
  
 <span data-ttu-id="ae779-214">Aşağıdaki çizim, bu bölümdeki XAML tarafından oluşturulan denetimleri göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="ae779-214">The following illustration shows the controls that are created by the XAML in this section.</span></span> 
  
 <span data-ttu-id="ae779-215">![ExpenseIt örnek ekran görüntüsü](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure2.png "GettingStartedFigure2")</span><span class="sxs-lookup"><span data-stu-id="ae779-215">![ExpenseIt sample screen shot](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure2.png "GettingStartedFigure2")</span></span>  
  
## <a name="adding-an-image-and-a-title"></a><span data-ttu-id="ae779-216">Görüntüyü ve başlık ekleme</span><span class="sxs-lookup"><span data-stu-id="ae779-216">Adding an image and a title</span></span>  
 <span data-ttu-id="ae779-217">Bu bölümde, giriş sayfası [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] resim ve sayfa başlığı ile güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="ae779-217">In this section, the home page [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] is updated with an image and a page title.</span></span> 
  
1. <span data-ttu-id="ae779-218">ExpenseItHome.xaml açın.</span><span class="sxs-lookup"><span data-stu-id="ae779-218">Open ExpenseItHome.xaml.</span></span> 
  
2. <span data-ttu-id="ae779-219">Başka bir sütuna eklemek <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> bir sabit ile <xref:System.Windows.Controls.ColumnDefinition.Width%2A> 230 piksel.</span><span class="sxs-lookup"><span data-stu-id="ae779-219">Add another column to the <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> with a fixed <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of 230 pixels.</span></span> 
  
    [!code-xaml[ExpenseIt#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11)]  
  
3. <span data-ttu-id="ae779-220">Başka bir satır ekleyin <xref:System.Windows.Controls.Grid.RowDefinitions%2A>.</span><span class="sxs-lookup"><span data-stu-id="ae779-220">Add another row to the <xref:System.Windows.Controls.Grid.RowDefinitions%2A>.</span></span> 
  
    [!code-xaml[ExpenseIt#11b](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11b)]  
  
4. <span data-ttu-id="ae779-221">Denetimleri ayarlayarak ikinci sütun taşımak <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> 1.</span><span class="sxs-lookup"><span data-stu-id="ae779-221">Move the controls to the second column by setting <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> to 1.</span></span> <span data-ttu-id="ae779-222">Her denetim artırarak bir satır aşağı taşı <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> 1.</span><span class="sxs-lookup"><span data-stu-id="ae779-222">Move each control down a row, by increasing the <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> by 1.</span></span> 
  
    [!code-xaml[ExpenseIt#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]  
  
5. <span data-ttu-id="ae779-223">Ayarlama <xref:System.Windows.Controls.Panel.Background%2A> , <xref:System.Windows.Controls.Grid> watermark.png resim dosyası olarak.</span><span class="sxs-lookup"><span data-stu-id="ae779-223">Set the <xref:System.Windows.Controls.Panel.Background%2A> of the <xref:System.Windows.Controls.Grid> to be the watermark.png image file.</span></span> 
  
    [!code-xaml[ExpenseIt#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]  
  
6. <span data-ttu-id="ae779-224">Önce <xref:System.Windows.Controls.Border>, ekleme bir <xref:System.Windows.Controls.Label> "Gider sayfanın başlığı olması için raporu görüntüle" içeriğe sahip.</span><span class="sxs-lookup"><span data-stu-id="ae779-224">Before the <xref:System.Windows.Controls.Border>, add a <xref:System.Windows.Controls.Label> with the content "View Expense Report" to be the title of the page.</span></span> 
  
    [!code-xaml[ExpenseIt#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]  
  
7. <span data-ttu-id="ae779-225">Derleme ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ae779-225">Build and run the application.</span></span> 
  
 <span data-ttu-id="ae779-226">Aşağıdaki çizimde, bu bölümde sonuçlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ae779-226">The following illustration shows the results of this section.</span></span> 
  
 <span data-ttu-id="ae779-227">![ExpenseIt örnek ekran görüntüsü](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure3.png "GettingStartedFigure3")</span><span class="sxs-lookup"><span data-stu-id="ae779-227">![ExpenseIt sample screen shot](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure3.png "GettingStartedFigure3")</span></span>  
  
## <a name="adding-code-to-handle-events"></a><span data-ttu-id="ae779-228">Olayları işlemek için kod ekleme</span><span class="sxs-lookup"><span data-stu-id="ae779-228">Adding code to handle events</span></span>  
  
1. <span data-ttu-id="ae779-229">ExpenseItHome.xaml açın.</span><span class="sxs-lookup"><span data-stu-id="ae779-229">Open ExpenseItHome.xaml.</span></span> 
  
2. <span data-ttu-id="ae779-230">Ekleme bir <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay işleyicisine <xref:System.Windows.Controls.Button> öğesi.</span><span class="sxs-lookup"><span data-stu-id="ae779-230">Add a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to the <xref:System.Windows.Controls.Button> element.</span></span> <span data-ttu-id="ae779-231">Daha fazla bilgi için bkz: [nasıl yapılır: basit bir olay işleyicisi oluşturun](http://msdn.microsoft.com/en-us/b1456e07-9dec-4354-99cf-18666b64f480).</span><span class="sxs-lookup"><span data-stu-id="ae779-231">For more information, see [How to: Create a Simple Event Handler](http://msdn.microsoft.com/en-us/b1456e07-9dec-4354-99cf-18666b64f480).</span></span> 
  
    [!code-xaml[ExpenseIt#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]  
  
3. <span data-ttu-id="ae779-232">ExpenseItHome.xaml.vb veya ExpenseItHome.xaml.cs açın.</span><span class="sxs-lookup"><span data-stu-id="ae779-232">Open ExpenseItHome.xaml.vb or ExpenseItHome.xaml.cs.</span></span> 
  
4. <span data-ttu-id="ae779-233">Aşağıdaki kodu ekleyin <xref:System.Windows.Controls.Primitives.ButtonBase.Click> ExpenseReportPage.xaml dosyaya gitmek için penceresini neden olan olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="ae779-233">Add the following code to the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler, which causes the window to navigate to the ExpenseReportPage.xaml file.</span></span> 
  
    [!code-csharp[ExpenseIt#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]  
  
## <a name="creating-the-ui-for-expensereportpage"></a><span data-ttu-id="ae779-234">ExpenseReportPage için kullanıcı Arabirimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="ae779-234">Creating the UI for ExpenseReportPage</span></span>  
 <span data-ttu-id="ae779-235">ExpenseReportPage.xaml, ExpenseItHome.XAML üzerinde seçili kişi için harcama raporunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ae779-235">ExpenseReportPage.xaml displays the expense report for the person that was selected on the ExpenseItHome.xaml.</span></span> <span data-ttu-id="ae779-236">Bu bölümde denetimleri ekler ve oluşturur [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ExpenseReportPage.xaml için.</span><span class="sxs-lookup"><span data-stu-id="ae779-236">This section adds controls and creates the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] for ExpenseReportPage.xaml.</span></span> <span data-ttu-id="ae779-237">Bu bölümde Ayrıca arka plan ve dolgu renklerini çeşitli ekler [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğeleri.</span><span class="sxs-lookup"><span data-stu-id="ae779-237">This section also adds background and fill colors to the various [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements.</span></span> 
  
1. <span data-ttu-id="ae779-238">ExpenseReportPage.xaml açın.</span><span class="sxs-lookup"><span data-stu-id="ae779-238">Open ExpenseReportPage.xaml.</span></span> 
  
2. <span data-ttu-id="ae779-239">Aşağıdaki XAML'i ekleyin <xref:System.Windows.Controls.Grid> etiketler.</span><span class="sxs-lookup"><span data-stu-id="ae779-239">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags.</span></span> 
  
     <span data-ttu-id="ae779-240">Bu UI ExpenseItHome.XAML üzerinde rapor verilerini görüntülenen dışında oluşturulan UI benzer bir <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="ae779-240">This UI is similar to the UI created on ExpenseItHome.xaml except the report data is displayed in a <xref:System.Windows.Controls.DataGrid>.</span></span> 
  
    [!code-xaml[ExpenseIt#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]  
  
3. <span data-ttu-id="ae779-241">Derleme ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ae779-241">Build and run the application.</span></span> 
  
    > [!NOTE]
    >  <span data-ttu-id="ae779-242">Bir hata alırsanız <xref:System.Windows.Controls.DataGrid> bulunamadı veya olmayabilir, projeniz .NET Framework 4 veya sonrasını hedefleyen emin olun.</span><span class="sxs-lookup"><span data-stu-id="ae779-242">If you get an error that the <xref:System.Windows.Controls.DataGrid> was not found or does not exist, make sure that your project targets the .NET Framework 4 or later.</span></span> <span data-ttu-id="ae779-243">Daha fazla bilgi için bkz: [nasıl yapılır: .NET Framework sürümü hedef](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span><span class="sxs-lookup"><span data-stu-id="ae779-243">For more information, see [How to: Target a Version of the .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span></span> 
  
4. <span data-ttu-id="ae779-244">Tıklatın **Görünüm** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="ae779-244">Click the **View** button.</span></span> 
  
     <span data-ttu-id="ae779-245">Harcama Raporu sayfası görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ae779-245">The expense report page appears.</span></span> 
  
 <span data-ttu-id="ae779-246">Aşağıdaki çizimde gösterildiği [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ExpenseReportPage.xaml'e eklenen öğeleri.</span><span class="sxs-lookup"><span data-stu-id="ae779-246">The following illustration shows the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements added to ExpenseReportPage.xaml.</span></span> <span data-ttu-id="ae779-247">Geri gezinti düğmesi etkinleştirilir dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="ae779-247">Notice that the back navigation button is enabled.</span></span> 
  
 <span data-ttu-id="ae779-248">![ExpenseIt örnek ekran görüntüsü](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure4.png "GettingStartedFigure4")</span><span class="sxs-lookup"><span data-stu-id="ae779-248">![ExpenseIt sample screen shot](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure4.png "GettingStartedFigure4")</span></span>  
  
## <a name="styling-controls"></a><span data-ttu-id="ae779-249">Stil denetimleri</span><span class="sxs-lookup"><span data-stu-id="ae779-249">Styling controls</span></span>  
 <span data-ttu-id="ae779-250">Çeşitli öğelerin görünümü genellikle içindeki aynı türden tüm öğeler için aynı olabilir bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ae779-250">The appearance of various elements can often be the same for all elements of the same type in a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].</span></span> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]<span data-ttu-id="ae779-251">görünümlerin çoklu öğeler arasında yeniden kullanılabilir olması için stilleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="ae779-251"> uses styles to make appearances reusable across multiple elements.</span></span> <span data-ttu-id="ae779-252">Kullanılırlığı yardımcı basitleştirmek için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] oluşturma ve yönetme.</span><span class="sxs-lookup"><span data-stu-id="ae779-252">The reusability of styles helps to simplify [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] creation and management.</span></span> <span data-ttu-id="ae779-253">Stilleri hakkında daha fazla bilgi için bkz: [stil ve şablon](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="ae779-253">For more information about styles, see [Styling and Templating](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span></span> <span data-ttu-id="ae779-254">Bu bölümde stilleri önceki adımlarda tanımlanan öğesi başına özniteliklerini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="ae779-254">This section replaces the per-element attributes that were defined in previous steps with styles.</span></span> 
  
1. <span data-ttu-id="ae779-255">Application.XAML veya App.xaml açın.</span><span class="sxs-lookup"><span data-stu-id="ae779-255">Open Application.xaml or App.xaml.</span></span> 
  
2. <span data-ttu-id="ae779-256">Aşağıdaki XAML'i ekleyin <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> etiketler:</span><span class="sxs-lookup"><span data-stu-id="ae779-256">Add the following XAML between the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tags:</span></span>  
  
    [!code-xaml[ExpenseIt#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]  
  
     <span data-ttu-id="ae779-257">Bu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aşağıdaki stilleri ekler:</span><span class="sxs-lookup"><span data-stu-id="ae779-257">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] adds the following styles:</span></span>  
  
    -  <span data-ttu-id="ae779-258">`headerTextStyle`: Sayfa başlığı Biçimlendirilecek <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="ae779-258">`headerTextStyle`: To format the page title <xref:System.Windows.Controls.Label>.</span></span> 
  
    -  <span data-ttu-id="ae779-259">`labelStyle`: Biçimlendirilecek <xref:System.Windows.Controls.Label> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="ae779-259">`labelStyle`: To format the <xref:System.Windows.Controls.Label> controls.</span></span> 
  
    -  <span data-ttu-id="ae779-260">`columnHeaderStyle`: Biçimlendirilecek <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span><span class="sxs-lookup"><span data-stu-id="ae779-260">`columnHeaderStyle`: To format the <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span></span> 
  
    -  <span data-ttu-id="ae779-261">`listHeaderStyle`: List üstbilgisi Biçimlendirilecek <xref:System.Windows.Controls.Border> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="ae779-261">`listHeaderStyle`: To format the list header <xref:System.Windows.Controls.Border> controls.</span></span> 
  
    -  <span data-ttu-id="ae779-262">`listHeaderTextStyle`: List üstbilgisi Biçimlendirilecek <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="ae779-262">`listHeaderTextStyle`: To format the list header <xref:System.Windows.Controls.Label>.</span></span> 
  
    -  <span data-ttu-id="ae779-263">`buttonStyle`: Biçimlendirilecek <xref:System.Windows.Controls.Button> ExpenseItHome.XAML üzerinde.</span><span class="sxs-lookup"><span data-stu-id="ae779-263">`buttonStyle`: To format the <xref:System.Windows.Controls.Button> on ExpenseItHome.xaml.</span></span> 
  
     <span data-ttu-id="ae779-264">Stilleri kaynakları ve alt öğeleri olduğuna dikkat edin <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> özellik öğesi.</span><span class="sxs-lookup"><span data-stu-id="ae779-264">Notice that the styles are resources and children of the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> property element.</span></span> <span data-ttu-id="ae779-265">Bu konumda stiller tüm öğelere uygulanır.</span><span class="sxs-lookup"><span data-stu-id="ae779-265">In this location, the styles are applied to all the elements in an application.</span></span> <span data-ttu-id="ae779-266">Kaynaklarında kullanma örneği için bir [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] uygulama, bkz: [kullanım uygulama kaynakları](../../../../docs/framework/wpf/advanced/how-to-use-application-resources.md).</span><span class="sxs-lookup"><span data-stu-id="ae779-266">For an example of using resources in a [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] application, see [Use Application Resources](../../../../docs/framework/wpf/advanced/how-to-use-application-resources.md).</span></span> 
  
3. <span data-ttu-id="ae779-267">ExpenseItHome.xaml açın.</span><span class="sxs-lookup"><span data-stu-id="ae779-267">Open ExpenseItHome.xaml.</span></span> 
  
4. <span data-ttu-id="ae779-268">Arasındaki her şeyi değiştirin <xref:System.Windows.Controls.Grid> öğeleri aşağıdaki XAML ile.</span><span class="sxs-lookup"><span data-stu-id="ae779-268">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML.</span></span> 
  
    [!code-xaml[ExpenseIt#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]  
  
     <span data-ttu-id="ae779-269">Gibi özellikler <xref:System.Windows.VerticalAlignment> ve <xref:System.Windows.Media.FontFamily> her denetimin görünümünü tanımlamak kaldırılır ve stiller uygulayarak değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="ae779-269">The properties such as <xref:System.Windows.VerticalAlignment> and <xref:System.Windows.Media.FontFamily> that define the look of each control are removed and replaced by applying the styles.</span></span> <span data-ttu-id="ae779-270">Örneğin, `headerTextStyle` harcama raporu görünümü"için" uygulanan <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="ae779-270">For example, the `headerTextStyle` is applied to the "View Expense Report" <xref:System.Windows.Controls.Label>.</span></span> 
  
5. <span data-ttu-id="ae779-271">ExpenseReportPage.xaml açın.</span><span class="sxs-lookup"><span data-stu-id="ae779-271">Open ExpenseReportPage.xaml.</span></span> 
  
6. <span data-ttu-id="ae779-272">Arasındaki her şeyi değiştirin <xref:System.Windows.Controls.Grid> öğeleri aşağıdaki XAML ile.</span><span class="sxs-lookup"><span data-stu-id="ae779-272">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML.</span></span> 
  
    [!code-xaml[ExpenseIt#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]  
  
     <span data-ttu-id="ae779-273">Bu stiller ekler <xref:System.Windows.Controls.Label> ve <xref:System.Windows.Controls.Border> öğeleri.</span><span class="sxs-lookup"><span data-stu-id="ae779-273">This adds styles to the <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Border> elements.</span></span> 
  
7. <span data-ttu-id="ae779-274">Derleme ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ae779-274">Build and run the application.</span></span> 
  
     <span data-ttu-id="ae779-275">Ekledikten sonra [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stilleri ile güncelleştirilmiş önce yaptığınız gibi bu bölümde, uygulama aynı arar.</span><span class="sxs-lookup"><span data-stu-id="ae779-275">After adding the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] in this section, the application looks the same as it did before being updated with styles.</span></span> 
  
## <a name="binding-data-to-a-control"></a><span data-ttu-id="ae779-276">Denetimine veri bağlama</span><span class="sxs-lookup"><span data-stu-id="ae779-276">Binding data to a control</span></span>  
 <span data-ttu-id="ae779-277">Bu bölümde, oluşturduğunuz [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] çeşitli denetimlere bağlı veri.</span><span class="sxs-lookup"><span data-stu-id="ae779-277">In this section, you create the [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] data that is bound to various controls.</span></span> 
  
1. <span data-ttu-id="ae779-278">ExpenseItHome.xaml açın.</span><span class="sxs-lookup"><span data-stu-id="ae779-278">Open ExpenseItHome.xaml.</span></span> 
  
2. <span data-ttu-id="ae779-279">Açtıktan sonra <xref:System.Windows.Controls.Grid> öğesi oluşturmak için aşağıdaki XAML eklemek bir <xref:System.Windows.Data.XmlDataProvider> , her kişi için veriler içerir.</span><span class="sxs-lookup"><span data-stu-id="ae779-279">After the opening <xref:System.Windows.Controls.Grid> element, add the following XAML to create an <xref:System.Windows.Data.XmlDataProvider> that contains the data for each person.</span></span> 
  
     <span data-ttu-id="ae779-280">Veri olarak oluşturulan bir <xref:System.Windows.Controls.Grid> kaynak.</span><span class="sxs-lookup"><span data-stu-id="ae779-280">The data is created as a <xref:System.Windows.Controls.Grid> resource.</span></span> <span data-ttu-id="ae779-281">Normalde bu dosya olarak yüklenir, ancak kolaylık sağlamak için veriler satır içi eklenir.</span><span class="sxs-lookup"><span data-stu-id="ae779-281">Normally this would be loaded as a file, but for simplicity the data is added inline.</span></span> 
  
    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]  
    [!code-xaml[ExpenseIt#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#23)]  
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]  
  
3. <span data-ttu-id="ae779-282">İçinde <xref:System.Windows.Controls.Grid> kaynak, aşağıdakileri ekleyin <xref:System.Windows.DataTemplate>, verilerin nasıl görüntüleneceğini tanımlayan <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="ae779-282">In the <xref:System.Windows.Controls.Grid> resource, add the following <xref:System.Windows.DataTemplate>, which defines how to display the data in the <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="ae779-283">Veri şablonları hakkında daha fazla bilgi için bkz: [veri şablonu özeti](../../../../docs/framework/wpf/data/data-templating-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ae779-283">For more information about data templates, see [Data Templating Overview](../../../../docs/framework/wpf/data/data-templating-overview.md).</span></span> 
  
    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]  
    [!code-xaml[ExpenseIt#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#24)]  
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]  
  
4. <span data-ttu-id="ae779-284">Varolan <xref:System.Windows.Controls.ListBox> aşağıdaki XAML ile.</span><span class="sxs-lookup"><span data-stu-id="ae779-284">Replace the existing <xref:System.Windows.Controls.ListBox> with the following XAML.</span></span> 
  
    [!code-xaml[ExpenseIt#25](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]  
  
     <span data-ttu-id="ae779-285">Bu XAML bağlar <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliği <xref:System.Windows.Controls.ListBox> veri kaynağı ve veri şablon olarak geçerlidir <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span><span class="sxs-lookup"><span data-stu-id="ae779-285">This XAML binds the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to the data source and applies the data template as the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span></span> 
  
## <a name="connecting-data-to-controls"></a><span data-ttu-id="ae779-286">Verileri denetimlere bağlama</span><span class="sxs-lookup"><span data-stu-id="ae779-286">Connecting data to controls</span></span>  
 <span data-ttu-id="ae779-287">Bu bölümde, ExpenseItHome.xaml sayfası üzerindeki kişiler listesinde seçili ve onun oluşturucusunun referansı aktaran güncel öğeyi alan kodu yazma `ExpenseReportPage` örnek oluşturma sırasında.</span><span class="sxs-lookup"><span data-stu-id="ae779-287">In this section, you write the code that retrieves the current item that is selected in the list of people on the ExpenseItHome.xaml page, and passes its reference to the constructor of `ExpenseReportPage` during instantiation.</span></span> <span data-ttu-id="ae779-288">`ExpenseReportPage`hangi denetimlerin ExpenseReportPage.xaml içinde tanımlı olan geçirilen öğe ile veri bağlamını ayarlar bağlayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="ae779-288">`ExpenseReportPage` sets its data context with the passed item, which is what the controls defined in ExpenseReportPage.xaml will bind to.</span></span> 
  
1. <span data-ttu-id="ae779-289">ExpenseReportPage.xaml.vb veya ExpenseReportPage.xaml.cs açın.</span><span class="sxs-lookup"><span data-stu-id="ae779-289">Open ExpenseReportPage.xaml.vb or ExpenseReportPage.xaml.cs.</span></span> 
  
2. <span data-ttu-id="ae779-290">Seçili kişinin harcama raporu verilerini geçirmek için bir nesne alan bir oluşturucu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ae779-290">Add a constructor that takes an object so you can pass the expense report data of the selected person.</span></span> 
  
    [!code-csharp[ExpenseIt#26](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]  
  
3. <span data-ttu-id="ae779-291">ExpenseItHome.xaml.vb veya ExpenseItHome.xaml.cs açın.</span><span class="sxs-lookup"><span data-stu-id="ae779-291">Open ExpenseItHome.xaml.vb or ExpenseItHome.xaml.cs.</span></span> 
  
4. <span data-ttu-id="ae779-292">Değişiklik <xref:System.Windows.Controls.Primitives.ButtonBase.Click> seçili kişinin harcama raporu geçirilen yeni oluşturucuyu çağırmak için olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="ae779-292">Change the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to call the new constructor passing the expense report data of the selected person.</span></span> 
  
    [!code-csharp[ExpenseIt#27](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]  
  
## <a name="styling-data-with-data-templates"></a><span data-ttu-id="ae779-293">Veri şablonları ile stil verileri</span><span class="sxs-lookup"><span data-stu-id="ae779-293">Styling data with data templates</span></span>  
 <span data-ttu-id="ae779-294">Bu bölümde, güncelleştirme [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] veri şablonlarını kullanarak verileri her öğe listelerini bağlı için.</span><span class="sxs-lookup"><span data-stu-id="ae779-294">In this section, you update the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] for each item in the data bound lists by using data templates.</span></span> 
  
1. <span data-ttu-id="ae779-295">ExpenseReportPage.xaml açın.</span><span class="sxs-lookup"><span data-stu-id="ae779-295">Open ExpenseReportPage.xaml.</span></span> 
  
2. <span data-ttu-id="ae779-296">"Name" ve "Departman" içeriğini bağlama <xref:System.Windows.Controls.Label> uygun veri öğelerine kaynak özelliği.</span><span class="sxs-lookup"><span data-stu-id="ae779-296">Bind the content of the "Name" and "Department" <xref:System.Windows.Controls.Label> elements to the appropriate data source property.</span></span> <span data-ttu-id="ae779-297">Veri bağlama hakkında daha fazla bilgi için bkz: [veri bağlama genel bakış](../../../../docs/framework/wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ae779-297">For more information about data binding, see [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span> 
  
    [!code-xaml[ExpenseIt#31](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]  
  
3. <span data-ttu-id="ae779-298">Açtıktan sonra <xref:System.Windows.Controls.Grid> öğesi, harcama raporu verilerini görüntülemek nasıl tanımlayan aşağıdaki veri şablonlarını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ae779-298">After the opening <xref:System.Windows.Controls.Grid> element, add the following data templates, which define how to display the expense report data.</span></span>  
    [!code-xaml[ExpenseIt#30](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]  
  
4. <span data-ttu-id="ae779-299">Şablonlar için geçerli <xref:System.Windows.Controls.DataGrid> gider gösteren sütunları rapor verileri.</span><span class="sxs-lookup"><span data-stu-id="ae779-299">Apply the templates to the <xref:System.Windows.Controls.DataGrid> columns that display the expense report data.</span></span> 
  
    [!code-xaml[ExpenseIt#32](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]  
  
5. <span data-ttu-id="ae779-300">Derleme ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ae779-300">Build and run the application.</span></span> 
  
6. <span data-ttu-id="ae779-301">Bir kişi tıklatıp **Görünüm** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="ae779-301">Select a person and click the **View** button.</span></span> 
  
 <span data-ttu-id="ae779-302">Aşağıdaki çizimde denetimleri, düzen, stiller, veri bağlama ve uygulanan veri şablonları ile ExpenseIt uygulamasının her iki sayfa gösterir.</span><span class="sxs-lookup"><span data-stu-id="ae779-302">The following illustration shows both pages of the ExpenseIt application with controls, layout, styles, data binding, and data templates applied.</span></span> 
  
 <span data-ttu-id="ae779-303">![ExpenseIt örnek ekran görüntüleri](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure5.png "GettingStartedFigure5")</span><span class="sxs-lookup"><span data-stu-id="ae779-303">![ExpenseIt sample screen shots](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure5.png "GettingStartedFigure5")</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="ae779-304">Önerilen uygulamalar</span><span class="sxs-lookup"><span data-stu-id="ae779-304">Best practices</span></span>  
 <span data-ttu-id="ae779-305">Bu örnek, belirli bir WPF özelliğini gösterir ve sonuç olarak, uygulama geliştirme en iyi yöntemler izlemez.</span><span class="sxs-lookup"><span data-stu-id="ae779-305">This sample demonstrates a specific feature of WPF and, consequently, does not follow application development best practices.</span></span> <span data-ttu-id="ae779-306">Kapsamlı için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] uygulama geliştirme en iyi yöntemler, aşağıdaki konulara uygun şekilde bakın:</span><span class="sxs-lookup"><span data-stu-id="ae779-306">For comprehensive coverage of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] and the [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] application development best practices, see the following topics as appropriate:</span></span>  
  
-   <span data-ttu-id="ae779-307">Erişilebilirlik - [en iyi erişilebilirlik uygulamaları](../../../../docs/framework/ui-automation/accessibility-best-practices.md)</span><span class="sxs-lookup"><span data-stu-id="ae779-307">Accessibility - [Accessibility Best Practices](../../../../docs/framework/ui-automation/accessibility-best-practices.md)</span></span>  
  
-   <span data-ttu-id="ae779-308">Güvenlik - [güvenlik](../../../../docs/framework/wpf/security-wpf.md)</span><span class="sxs-lookup"><span data-stu-id="ae779-308">Security - [Security](../../../../docs/framework/wpf/security-wpf.md)</span></span>  
  
-   <span data-ttu-id="ae779-309">Yerelleştirme - [WPF Genelleştirme ve yerelleştirme genel bakış](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)</span><span class="sxs-lookup"><span data-stu-id="ae779-309">Localization - [WPF Globalization and Localization Overview](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)</span></span>  
  
-   <span data-ttu-id="ae779-310">Performans - [WPF Uygulama performansı en iyi duruma getirme](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)</span><span class="sxs-lookup"><span data-stu-id="ae779-310">Performance - [Optimizing WPF Application Performance](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)</span></span>  
  
## <a name="whats-next"></a><span data-ttu-id="ae779-311">Sırada ne var?</span><span class="sxs-lookup"><span data-stu-id="ae779-311">What's next</span></span>  
 <span data-ttu-id="ae779-312">Şimdi oluşturmak için elden en çeşitli teknikler sahip bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kullanarak [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ae779-312">You now have a number of techniques at your disposal for creating a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] using [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span> <span data-ttu-id="ae779-313">Veri bağlama temel yapı taşlarını geniş bir anlayış şimdi olmalıdır [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="ae779-313">You should now have a broad understanding of the basic building blocks of a data-bound [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] application.</span></span> <span data-ttu-id="ae779-314">Bu konuda halinde kapsamlı, ancak ayrıca artık umarız bazı bu konudaki teknikleri ötesinde kendi keşfedebilirsiniz olasılıklar duygusu vardır.</span><span class="sxs-lookup"><span data-stu-id="ae779-314">This topic is by no means exhaustive, but hopefully you also now have a sense of some of the possibilities you might discover on your own beyond the techniques in this topic.</span></span> 
  
 <span data-ttu-id="ae779-315">WPF mimarisi ve programlama modelleri hakkında daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="ae779-315">For more information about the WPF architecture and programming models, see the following topics:</span></span>  
  
-   [<span data-ttu-id="ae779-316">WPF Mimarisi</span><span class="sxs-lookup"><span data-stu-id="ae779-316">WPF Architecture</span></span>](../../../../docs/framework/wpf/advanced/wpf-architecture.md)  
  
-   [<span data-ttu-id="ae779-317">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="ae779-317">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
  
-   [<span data-ttu-id="ae779-318">Bağımlılık Özelliklerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ae779-318">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
  
-   [<span data-ttu-id="ae779-319">Düzen</span><span class="sxs-lookup"><span data-stu-id="ae779-319">Layout</span></span>](../../../../docs/framework/wpf/advanced/layout.md)  
  
 <span data-ttu-id="ae779-320">Uygulamaları oluşturma hakkında daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="ae779-320">For more information about creating applications, see the following topics:</span></span>  
  
-   [<span data-ttu-id="ae779-321">Uygulama Geliştirme</span><span class="sxs-lookup"><span data-stu-id="ae779-321">Application Development</span></span>](../../../../docs/framework/wpf/app-development/index.md)  
  
-   [<span data-ttu-id="ae779-322">Denetimler</span><span class="sxs-lookup"><span data-stu-id="ae779-322">Controls</span></span>](../../../../docs/framework/wpf/controls/index.md)  
  
-   [<span data-ttu-id="ae779-323">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ae779-323">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
  
-   [<span data-ttu-id="ae779-324">Grafikler ve Multimedya</span><span class="sxs-lookup"><span data-stu-id="ae779-324">Graphics and Multimedia</span></span>](../../../../docs/framework/wpf/graphics-multimedia/index.md)  
  
-   [<span data-ttu-id="ae779-325">WPF'deki Belgeler</span><span class="sxs-lookup"><span data-stu-id="ae779-325">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
  
## <a name="see-also"></a><span data-ttu-id="ae779-326">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae779-326">See also</span></span>  
 [<span data-ttu-id="ae779-327">Panellere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ae779-327">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="ae779-328">Veri Şablonu Oluşturmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ae779-328">Data Templating Overview</span></span>](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [<span data-ttu-id="ae779-329">WPF Uygulaması Derleme</span><span class="sxs-lookup"><span data-stu-id="ae779-329">Building a WPF Application</span></span>](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)  
 [<span data-ttu-id="ae779-330">Stiller ve Şablonlar</span><span class="sxs-lookup"><span data-stu-id="ae779-330">Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/styles-and-templates.md)
