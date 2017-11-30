---
title: "İzlenecek yol: WPF'de Windows Forms Denetimini Barındırma"
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
helpviewer_keywords: hosting Windows Forms control in WPF [WPF]
ms.assetid: 9cb88415-39b0-4c46-80c4-ff325b674286
caps.latest.revision: "36"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 71c48b85af6767d59eaa68621faf566321af613c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf"></a><span data-ttu-id="35ed4-102">İzlenecek yol: WPF'de Windows Forms Denetimini Barındırma</span><span class="sxs-lookup"><span data-stu-id="35ed4-102">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="35ed4-103">birçok denetimleri ile zengin özellik kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="35ed4-103"> provides many controls with a rich feature set.</span></span> <span data-ttu-id="35ed4-104">Ancak, bazen kullanmak istediğiniz [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimlerini, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sayfaları.</span><span class="sxs-lookup"><span data-stu-id="35ed4-104">However, you may sometimes want to use [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls on your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages.</span></span> <span data-ttu-id="35ed4-105">Örneğin, varolan önemli ölçüde yatırımınız olabilir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri veya olabilir bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] benzersiz işlevsellik sağlayan denetim.</span><span class="sxs-lookup"><span data-stu-id="35ed4-105">For example, you may have a substantial investment in existing [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls, or you may have a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control that provides unique functionality.</span></span>  
  
 <span data-ttu-id="35ed4-106">Bu kılavuzda barındırmak gösterilmiştir bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> denetiminin bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kodu kullanarak sayfa.</span><span class="sxs-lookup"><span data-stu-id="35ed4-106">This walkthrough shows you how to host a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page by using code.</span></span>  
  
 <span data-ttu-id="35ed4-107">Bu kılavuzda gösterilen görevlerin tam kod listesi için bkz: [WPF örnek bir Windows Forms denetimi barındırma](http://go.microsoft.com/fwlink/?LinkID=160057).</span><span class="sxs-lookup"><span data-stu-id="35ed4-107">For a complete code listing of the tasks shown in this walkthrough, see [Hosting a Windows Forms Control in WPF Sample](http://go.microsoft.com/fwlink/?LinkID=160057).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="35ed4-108">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="35ed4-108">Prerequisites</span></span>  
 <span data-ttu-id="35ed4-109">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="35ed4-109">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="35ed4-110">.</span><span class="sxs-lookup"><span data-stu-id="35ed4-110">.</span></span>  
  
## <a name="hosting-the-windows-forms-control"></a><span data-ttu-id="35ed4-111">Windows Forms denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="35ed4-111">Hosting the Windows Forms Control</span></span>  
  
#### <a name="to-host-the-maskedtextbox-control"></a><span data-ttu-id="35ed4-112">MaskedTextBox denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="35ed4-112">To host the MaskedTextBox control</span></span>  
  
1.  <span data-ttu-id="35ed4-113">Adlı bir WPF uygulaması projesi oluşturduğunuzda `HostingWfInWpf`.</span><span class="sxs-lookup"><span data-stu-id="35ed4-113">Create a WPF Application project named `HostingWfInWpf`.</span></span>  
  
2.  <span data-ttu-id="35ed4-114">Aşağıdaki derlemeler başvurular ekleyin.</span><span class="sxs-lookup"><span data-stu-id="35ed4-114">Add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="35ed4-115">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="35ed4-115">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="35ed4-116">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="35ed4-116">System.Windows.Forms</span></span>  
  
3.  <span data-ttu-id="35ed4-117">MainWindow.xaml içinde açmak [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="35ed4-117">Open MainWindow.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
4.  <span data-ttu-id="35ed4-118">Ad <xref:System.Windows.Controls.Grid> öğesi `grid1`.</span><span class="sxs-lookup"><span data-stu-id="35ed4-118">Name the <xref:System.Windows.Controls.Grid> element `grid1`.</span></span>  
  
     [!code-xaml[HostingWfInWPF#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml#1)]  
  
5.  <span data-ttu-id="35ed4-119">Tasarım görünümü ya da XAML görünümdeki seçmek <xref:System.Windows.Window> öğesi.</span><span class="sxs-lookup"><span data-stu-id="35ed4-119">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>  
  
6.  <span data-ttu-id="35ed4-120">Özellikler penceresinde **olayları** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="35ed4-120">In the Properties window, click the **Events** tab.</span></span>  
  
7.  <span data-ttu-id="35ed4-121">Çift <xref:System.Windows.FrameworkElement.Loaded> olay.</span><span class="sxs-lookup"><span data-stu-id="35ed4-121">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>  
  
8.  <span data-ttu-id="35ed4-122">İşlemek için aşağıdaki kodu ekleyin <xref:System.Windows.FrameworkElement.Loaded> olay.</span><span class="sxs-lookup"><span data-stu-id="35ed4-122">Insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>  
  
     [!code-csharp[HostingWfInWPF#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#10)]
     [!code-vb[HostingWfInWPF#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#10)]  
  
9. <span data-ttu-id="35ed4-123">Dosyanın üst kısmında, aşağıdaki ekleyin `Imports` veya `using` deyimi.</span><span class="sxs-lookup"><span data-stu-id="35ed4-123">At the top of the file, add the following `Imports` or `using` statement.</span></span>  
  
     [!code-csharp[HostingWfInWPF#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#11)]
     [!code-vb[HostingWfInWPF#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#11)]  
  
10. <span data-ttu-id="35ed4-124">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="35ed4-124">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35ed4-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="35ed4-125">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="35ed4-126">WPF Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="35ed4-126">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="35ed4-127">İzlenecek yol: XAML kullanarak WPF Windows Forms denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="35ed4-127">Walkthrough: Hosting a Windows Forms Control in WPF by Using XAML</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml.md)  
 [<span data-ttu-id="35ed4-128">İzlenecek yol: bir Windows Forms Bileşik Denetimi WPF barındırma</span><span class="sxs-lookup"><span data-stu-id="35ed4-128">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="35ed4-129">İzlenecek yol: Windows Forms içerisinde WPF bileşik denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="35ed4-129">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [<span data-ttu-id="35ed4-130">Windows Forms denetimleri ve eşdeğer WPF denetimleri</span><span class="sxs-lookup"><span data-stu-id="35ed4-130">Windows Forms Controls and Equivalent WPF Controls</span></span>](../../../../docs/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls.md)  
 [<span data-ttu-id="35ed4-131">WPF örnek bir Windows Forms denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="35ed4-131">Hosting a Windows Forms Control in WPF Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160057)
