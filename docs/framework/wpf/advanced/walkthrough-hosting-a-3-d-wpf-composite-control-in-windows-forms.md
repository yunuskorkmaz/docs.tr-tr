---
title: 'İzlenecek yol: 3B WPF Bileşik Denetimini Windows Forms İçinde Barındırma'
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
- composite controls [WPF], hosting WPF in
ms.assetid: 486369a9-606a-4a3b-b086-a06f2119c7b0
ms.openlocfilehash: e5b98a33f29759a81ba1cbc1fefbd45c0e5bf736
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59330174"
---
# <a name="walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms"></a><span data-ttu-id="cdcd5-102">İzlenecek yol: 3B WPF Bileşik Denetimini Windows Forms İçinde Barındırma</span><span class="sxs-lookup"><span data-stu-id="cdcd5-102">Walkthrough: Hosting a 3-D WPF Composite Control in Windows Forms</span></span>

<span data-ttu-id="cdcd5-103">Bu izlenecek yol nasıl oluşturacağınızı gösterir. bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bileşik denetleyebilir ve bunu ana [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri ve formları kullanarak <xref:System.Windows.Forms.Integration.ElementHost> denetimi.</span><span class="sxs-lookup"><span data-stu-id="cdcd5-103">This walkthrough demonstrates how you can create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] composite control and host it in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls and forms by using the <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>

<span data-ttu-id="cdcd5-104">Bu izlenecek yolda, uygulayan bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> , iki alt denetimler de içerir.</span><span class="sxs-lookup"><span data-stu-id="cdcd5-104">In this walkthrough, you will implement a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> that contains two child controls.</span></span> <span data-ttu-id="cdcd5-105"><xref:System.Windows.Controls.UserControl> Üç boyutlu (3B) koni görüntüler.</span><span class="sxs-lookup"><span data-stu-id="cdcd5-105">The <xref:System.Windows.Controls.UserControl> displays a three-dimensional (3-D) cone.</span></span> <span data-ttu-id="cdcd5-106">3B nesneleri oluşturma ile çok daha kolay [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] daha ile [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cdcd5-106">Rendering 3-D objects is much easier with the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] than with [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span> <span data-ttu-id="cdcd5-107">Bu nedenle, konağa mantıklı bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> 3B grafikleri oluşturmak için sınıf [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cdcd5-107">Therefore, it makes sense to host a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> class to create 3-D graphics in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span></span>

<span data-ttu-id="cdcd5-108">Bu kılavuzda gösterilen görevler aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="cdcd5-108">Tasks illustrated in this walkthrough include:</span></span>

-   <span data-ttu-id="cdcd5-109">Oluşturma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="cdcd5-109">Creating the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span></span>

-   <span data-ttu-id="cdcd5-110">Windows Forms konak projesi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="cdcd5-110">Creating the Windows Forms host project.</span></span>

-   <span data-ttu-id="cdcd5-111">Barındırma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="cdcd5-111">Hosting the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cdcd5-112">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="cdcd5-112">Prerequisites</span></span>

<span data-ttu-id="cdcd5-113">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="cdcd5-113">You need the following components to complete this walkthrough:</span></span>

-   <span data-ttu-id="cdcd5-114">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="cdcd5-114">Visual Studio 2017</span></span>

<a name="To_Create_the_UserControl"></a>
## <a name="create-the-usercontrol"></a><span data-ttu-id="cdcd5-115">UserControl oluşturma</span><span class="sxs-lookup"><span data-stu-id="cdcd5-115">Create the UserControl</span></span>

1. <span data-ttu-id="cdcd5-116">Oluşturma bir **WPF kullanıcı denetimi Kitaplığı** adlı proje `HostingWpfUserControlInWf`.</span><span class="sxs-lookup"><span data-stu-id="cdcd5-116">Create a **WPF User Control Library** project named `HostingWpfUserControlInWf`.</span></span>

2. <span data-ttu-id="cdcd5-117">İçinde UserControl1.xaml açın [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cdcd5-117">Open UserControl1.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>

3. <span data-ttu-id="cdcd5-118">Oluşturulan kodu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="cdcd5-118">Replace the generated code with the following code:</span></span>

     [!code-xaml[HostingWpfUserControlInWf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]

     <span data-ttu-id="cdcd5-119">Bu kodu tanımlayan bir <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> , iki alt denetimler de içerir.</span><span class="sxs-lookup"><span data-stu-id="cdcd5-119">This code defines a <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> that contains two child controls.</span></span> <span data-ttu-id="cdcd5-120">İlk alt denetim bir <xref:System.Windows.Controls.Label?displayProperty=nameWithType> denetimi; ikinci olduğu bir <xref:System.Windows.Controls.Viewport3D> 3B koni görüntüleyen denetim.</span><span class="sxs-lookup"><span data-stu-id="cdcd5-120">The first child control is a <xref:System.Windows.Controls.Label?displayProperty=nameWithType> control; the second is a <xref:System.Windows.Controls.Viewport3D> control that displays a 3-D cone.</span></span>

<a name="To_Create_the_Windows_Forms_Host_Project"></a>
## <a name="create-the-host-project"></a><span data-ttu-id="cdcd5-121">Ana proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="cdcd5-121">Create the host project</span></span>

1. <span data-ttu-id="cdcd5-122">Ekleme bir **WPF uygulaması (.NET Framework)** adlı proje `WpfUserControlHost` çözüm.</span><span class="sxs-lookup"><span data-stu-id="cdcd5-122">Add a **WPF App (.NET Framework)** project named `WpfUserControlHost` to the solution.</span></span> <span data-ttu-id="cdcd5-123">Daha fazla bilgi için [izlenecek yol: İlk WPF Masaüstü Uygulamam](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span><span class="sxs-lookup"><span data-stu-id="cdcd5-123">For more information, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>

2. <span data-ttu-id="cdcd5-124">İçinde **Çözüm Gezgini**, WindowsFormsIntegration.dll adlı WindowsFormsIntegration derlemesine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cdcd5-124">In **Solution Explorer**, add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

3. <span data-ttu-id="cdcd5-125">Aşağıdaki başvuruları ekleyin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] derlemeler:</span><span class="sxs-lookup"><span data-stu-id="cdcd5-125">Add references to the following [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] assemblies:</span></span>

    -   <span data-ttu-id="cdcd5-126">PresentationCore</span><span class="sxs-lookup"><span data-stu-id="cdcd5-126">PresentationCore</span></span>

    -   <span data-ttu-id="cdcd5-127">PresentationFramework</span><span class="sxs-lookup"><span data-stu-id="cdcd5-127">PresentationFramework</span></span>

    -   <span data-ttu-id="cdcd5-128">WindowsBase</span><span class="sxs-lookup"><span data-stu-id="cdcd5-128">WindowsBase</span></span>

4. <span data-ttu-id="cdcd5-129">Bir başvuru ekleyin `HostingWpfUserControlInWf` proje.</span><span class="sxs-lookup"><span data-stu-id="cdcd5-129">Add a reference to the `HostingWpfUserControlInWf` project.</span></span>

5. <span data-ttu-id="cdcd5-130">Çözüm Gezgini içinde ayarlamak `WpfUserControlHost` projesini başlangıç projesi olarak.</span><span class="sxs-lookup"><span data-stu-id="cdcd5-130">In Solution Explorer, set the `WpfUserControlHost` project to be the startup project.</span></span>

<a name="To_Host_the_Windows_Presentation_Foundation"></a>
## <a name="host-the-usercontrol"></a><span data-ttu-id="cdcd5-131">UserControl barındırın</span><span class="sxs-lookup"><span data-stu-id="cdcd5-131">Host the UserControl</span></span>

1. <span data-ttu-id="cdcd5-132">Windows Form Tasarımcısı'nda Form1'i açın.</span><span class="sxs-lookup"><span data-stu-id="cdcd5-132">In the Windows Forms Designer, open Form1.</span></span>

2. <span data-ttu-id="cdcd5-133">Özellikler penceresinde tıklayın **olayları**ve çift tıklatarak <xref:System.Windows.Forms.Form.Load> bir olay işleyicisi oluşturmak için olay.</span><span class="sxs-lookup"><span data-stu-id="cdcd5-133">In the Properties window, click **Events**, and then double-click the <xref:System.Windows.Forms.Form.Load> event to create an event handler.</span></span>

     <span data-ttu-id="cdcd5-134">Yeni oluşturulan kod düzenleyicisi açılır `Form1_Load` olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="cdcd5-134">The Code Editor opens to the newly generated `Form1_Load` event handler.</span></span>

3. <span data-ttu-id="cdcd5-135">Form1.cs içindeki kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="cdcd5-135">Replace the code in Form1.cs with the following code.</span></span>

     <span data-ttu-id="cdcd5-136">`Form1_Load` Olay işleyicisi bir örneğini oluşturur `UserControl1` ve onu ekler <xref:System.Windows.Forms.Integration.ElementHost> denetimin alt denetimler koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="cdcd5-136">The `Form1_Load` event handler creates an instance of `UserControl1` and adds itto the <xref:System.Windows.Forms.Integration.ElementHost> control's collection of child controls.</span></span> <span data-ttu-id="cdcd5-137"><xref:System.Windows.Forms.Integration.ElementHost> Denetimi, form alt denetimler koleksiyonuna eklenir.</span><span class="sxs-lookup"><span data-stu-id="cdcd5-137">The <xref:System.Windows.Forms.Integration.ElementHost> control is added to the form's collection of child controls.</span></span>

     [!code-csharp[HostingWpfUserControlInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/WpfUserControlHost/Form1.cs#10)]
     [!code-vb[HostingWpfUserControlInWf#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWpfUserControlInWf/VisualBasic/WpfUserControlHost/Form1.vb#10)]

4. <span data-ttu-id="cdcd5-138">Tuşuna **F5** oluşturun ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cdcd5-138">Press **F5** to build and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="cdcd5-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cdcd5-139">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="cdcd5-140">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="cdcd5-140">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="cdcd5-141">İzlenecek yol: WPF bileşik denetimini Windows Forms içinde barındırma</span><span class="sxs-lookup"><span data-stu-id="cdcd5-141">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [<span data-ttu-id="cdcd5-142">İzlenecek yol: WPF'de Windows Forms bileşik denetimini barındırma</span><span class="sxs-lookup"><span data-stu-id="cdcd5-142">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="cdcd5-143">Windows Forms örneğinde bir WPF bileşik denetimini barındırma</span><span class="sxs-lookup"><span data-stu-id="cdcd5-143">Hosting a WPF Composite Control in Windows Forms Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160001)