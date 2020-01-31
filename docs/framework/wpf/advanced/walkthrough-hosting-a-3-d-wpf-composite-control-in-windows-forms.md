---
title: Windows Forms 'da 3B WPF bileşik denetimini barındırma
titleSuffix: ''
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
- composite controls [WPF], hosting WPF in
ms.assetid: 486369a9-606a-4a3b-b086-a06f2119c7b0
ms.openlocfilehash: aaa726ac90fd75a12054c18be6ec08a1372c1128
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794205"
---
# <a name="walkthrough-host-a-3d-wpf-composite-control-in-windows-forms"></a><span data-ttu-id="1f43f-102">İzlenecek yol: Windows Forms bir 3B WPF bileşik denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="1f43f-102">Walkthrough: Host a 3D WPF Composite Control in Windows Forms</span></span>

<span data-ttu-id="1f43f-103">Bu izlenecek yol, <xref:System.Windows.Forms.Integration.ElementHost> denetimini kullanarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bileşik denetim oluşturabileceğiniz ve Windows Forms denetimlerde ve formlarda nasıl barındırabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="1f43f-103">This walkthrough demonstrates how you can create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] composite control and host it in Windows Forms controls and forms by using the <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>

<span data-ttu-id="1f43f-104">Bu izlenecek yolda, iki alt denetim içeren bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> uygulayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="1f43f-104">In this walkthrough, you will implement a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> that contains two child controls.</span></span> <span data-ttu-id="1f43f-105"><xref:System.Windows.Controls.UserControl> üç boyutlu (3B) koni görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1f43f-105">The <xref:System.Windows.Controls.UserControl> displays a three-dimensional (3D) cone.</span></span> <span data-ttu-id="1f43f-106">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 3B nesneleri işleme Windows Forms ile kıyasla çok daha kolay.</span><span class="sxs-lookup"><span data-stu-id="1f43f-106">Rendering 3D objects is much easier with the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] than with Windows Forms.</span></span> <span data-ttu-id="1f43f-107">Bu nedenle, Windows Forms 3B grafikler oluşturmak için bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> sınıfını barındırmak mantıklı olur.</span><span class="sxs-lookup"><span data-stu-id="1f43f-107">Therefore, it makes sense to host a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> class to create 3D graphics in Windows Forms.</span></span>

<span data-ttu-id="1f43f-108">Bu izlenecek yolda gösterilen görevler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="1f43f-108">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="1f43f-109">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="1f43f-109">Creating the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span></span>

- <span data-ttu-id="1f43f-110">Windows Forms konak projesi oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="1f43f-110">Creating the Windows Forms host project.</span></span>

- <span data-ttu-id="1f43f-111">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>barındırma.</span><span class="sxs-lookup"><span data-stu-id="1f43f-111">Hosting the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1f43f-112">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="1f43f-112">Prerequisites</span></span>

<span data-ttu-id="1f43f-113">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="1f43f-113">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="1f43f-114">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="1f43f-114">Visual Studio 2017</span></span>

<a name="To_Create_the_UserControl"></a>
## <a name="create-the-usercontrol"></a><span data-ttu-id="1f43f-115">UserControl oluşturma</span><span class="sxs-lookup"><span data-stu-id="1f43f-115">Create the UserControl</span></span>

1. <span data-ttu-id="1f43f-116">`HostingWpfUserControlInWf`adlı bir **WPF Kullanıcı denetim kitaplığı** projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1f43f-116">Create a **WPF User Control Library** project named `HostingWpfUserControlInWf`.</span></span>

2. <span data-ttu-id="1f43f-117">WPF Tasarımcısında UserControl1. xaml ' i açın.</span><span class="sxs-lookup"><span data-stu-id="1f43f-117">Open UserControl1.xaml in the WPF Designer.</span></span>

3. <span data-ttu-id="1f43f-118">Oluşturulan kodu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="1f43f-118">Replace the generated code with the following code:</span></span>

     [!code-xaml[HostingWpfUserControlInWf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]

     <span data-ttu-id="1f43f-119">Bu kod, iki alt denetim içeren bir <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1f43f-119">This code defines a <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> that contains two child controls.</span></span> <span data-ttu-id="1f43f-120">İlk alt denetim bir <xref:System.Windows.Controls.Label?displayProperty=nameWithType> denetimidir; İkincisi 3B koni görüntüleyen bir <xref:System.Windows.Controls.Viewport3D> denetimidir.</span><span class="sxs-lookup"><span data-stu-id="1f43f-120">The first child control is a <xref:System.Windows.Controls.Label?displayProperty=nameWithType> control; the second is a <xref:System.Windows.Controls.Viewport3D> control that displays a 3D cone.</span></span>

<a name="To_Create_the_Windows_Forms_Host_Project"></a>
## <a name="create-the-host-project"></a><span data-ttu-id="1f43f-121">Konak projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="1f43f-121">Create the host project</span></span>

1. <span data-ttu-id="1f43f-122">Çözüme `WpfUserControlHost` adlı bir **Windows Forms App (.NET Framework)** projesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1f43f-122">Add a **Windows Forms App (.NET Framework)** project named `WpfUserControlHost` to the solution.</span></span>

2. <span data-ttu-id="1f43f-123">**Çözüm Gezgini**' de, WindowsFormsIntegration. dll adlı WindowsFormsIntegration derlemesine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1f43f-123">In **Solution Explorer**, add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

3. <span data-ttu-id="1f43f-124">Aşağıdaki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] derlemelerine başvuruları ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1f43f-124">Add references to the following [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] assemblies:</span></span>

    - <span data-ttu-id="1f43f-125">PresentationCore</span><span class="sxs-lookup"><span data-stu-id="1f43f-125">PresentationCore</span></span>

    - <span data-ttu-id="1f43f-126">PresentationFramework</span><span class="sxs-lookup"><span data-stu-id="1f43f-126">PresentationFramework</span></span>

    - <span data-ttu-id="1f43f-127">WindowsBase</span><span class="sxs-lookup"><span data-stu-id="1f43f-127">WindowsBase</span></span>

4. <span data-ttu-id="1f43f-128">`HostingWpfUserControlInWf` projesine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1f43f-128">Add a reference to the `HostingWpfUserControlInWf` project.</span></span>

5. <span data-ttu-id="1f43f-129">Çözüm Gezgini, `WpfUserControlHost` projesini başlangıç projesi olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1f43f-129">In Solution Explorer, set the `WpfUserControlHost` project to be the startup project.</span></span>

<a name="To_Host_the_Windows_Presentation_Foundation"></a>
## <a name="host-the-usercontrol"></a><span data-ttu-id="1f43f-130">UserControl barındırın</span><span class="sxs-lookup"><span data-stu-id="1f43f-130">Host the UserControl</span></span>

1. <span data-ttu-id="1f43f-131">Windows Form Tasarımcısı Form1 ' i açın.</span><span class="sxs-lookup"><span data-stu-id="1f43f-131">In the Windows Forms Designer, open Form1.</span></span>

2. <span data-ttu-id="1f43f-132">Özellikler penceresi, **Olaylar**' a tıklayın ve sonra bir olay işleyicisi oluşturmak için <xref:System.Windows.Forms.Form.Load> olayına çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1f43f-132">In the Properties window, click **Events**, and then double-click the <xref:System.Windows.Forms.Form.Load> event to create an event handler.</span></span>

     <span data-ttu-id="1f43f-133">Kod Düzenleyicisi, yeni oluşturulan `Form1_Load` olay işleyicisine açılır.</span><span class="sxs-lookup"><span data-stu-id="1f43f-133">The Code Editor opens to the newly generated `Form1_Load` event handler.</span></span>

3. <span data-ttu-id="1f43f-134">Form1.cs içindeki kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="1f43f-134">Replace the code in Form1.cs with the following code.</span></span>

     <span data-ttu-id="1f43f-135">`Form1_Load` olay işleyicisi `UserControl1` örneğini oluşturur ve <xref:System.Windows.Forms.Integration.ElementHost> denetimin alt denetim koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="1f43f-135">The `Form1_Load` event handler creates an instance of `UserControl1` and adds itto the <xref:System.Windows.Forms.Integration.ElementHost> control's collection of child controls.</span></span> <span data-ttu-id="1f43f-136"><xref:System.Windows.Forms.Integration.ElementHost> denetimi formun alt denetim koleksiyonuna eklenir.</span><span class="sxs-lookup"><span data-stu-id="1f43f-136">The <xref:System.Windows.Forms.Integration.ElementHost> control is added to the form's collection of child controls.</span></span>

     [!code-csharp[HostingWpfUserControlInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/WpfUserControlHost/Form1.cs#10)]
     [!code-vb[HostingWpfUserControlInWf#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWpfUserControlInWf/VisualBasic/WpfUserControlHost/Form1.vb#10)]

4. <span data-ttu-id="1f43f-137">Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1f43f-137">Press **F5** to build and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="1f43f-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f43f-138">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="1f43f-139">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="1f43f-139">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="1f43f-140">İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma</span><span class="sxs-lookup"><span data-stu-id="1f43f-140">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [<span data-ttu-id="1f43f-141">İzlenecek yol: WPF'de Windows Forms Bileşik Denetimini Barındırma</span><span class="sxs-lookup"><span data-stu-id="1f43f-141">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="1f43f-142">Windows Forms örnekte WPF bileşik denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="1f43f-142">Hosting a WPF Composite Control in Windows Forms Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160001)
