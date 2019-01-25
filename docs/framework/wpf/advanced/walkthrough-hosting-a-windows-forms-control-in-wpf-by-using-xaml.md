---
title: 'İzlenecek yol: XAML kullanarak WPF içerisinde bir Windows Forms denetimi barındırma'
ms.date: 03/30/2017
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 1aef42cb-4cfb-44b4-9a7a-c02632d3d9c7
ms.openlocfilehash: 7e5984edfc081427214220eadf190282846b1c44
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640738"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml"></a><span data-ttu-id="acb0a-102">İzlenecek yol: XAML kullanarak WPF içerisinde bir Windows Forms denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="acb0a-102">Walkthrough: Hosting a Windows Forms Control in WPF by Using XAML</span></span>
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="acb0a-103">pek çok denetimi ile zengin özellik kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="acb0a-103">provides many controls with a rich feature set.</span></span> <span data-ttu-id="acb0a-104">Ancak, bazen kullanmak isteyebilirsiniz [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimlerini, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sayfaları.</span><span class="sxs-lookup"><span data-stu-id="acb0a-104">However, you may sometimes want to use [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls on your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages.</span></span> <span data-ttu-id="acb0a-105">Örneğin, var olan önemli bir yatırım olabilir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri veya olabilir bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] benzersiz işlevsellik sağlayan denetimi.</span><span class="sxs-lookup"><span data-stu-id="acb0a-105">For example, you may have a substantial investment in existing [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls, or you may have a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control that provides unique functionality.</span></span>  
  
 <span data-ttu-id="acb0a-106">Bu yönerge, bir Windows Forms barındırmak nasıl gösterir <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> denetimi bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kullanarak sayfa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="acb0a-106">This walkthrough shows you how to host a Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 <span data-ttu-id="acb0a-107">Bu izlenecek yolda gösterilen görevler tam kod listesi için bkz. [WPF kullanarak XAML örnek olarak bir Windows Forms denetimi barındırma](https://go.microsoft.com/fwlink/?LinkID=160000).</span><span class="sxs-lookup"><span data-stu-id="acb0a-107">For a complete code listing of the tasks shown in this walkthrough, see [Hosting a Windows Forms Control in WPF by Using XAML Sample](https://go.microsoft.com/fwlink/?LinkID=160000).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="acb0a-108">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="acb0a-108">Prerequisites</span></span>  

<span data-ttu-id="acb0a-109">Bu izlenecek yolu tamamlamak için Visual Studio ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="acb0a-109">You need Visual Studio to complete this walkthrough.</span></span>  
  
## <a name="hosting-the-windows-forms-control"></a><span data-ttu-id="acb0a-110">Windows Forms denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="acb0a-110">Hosting the Windows Forms Control</span></span>  
  
#### <a name="to-host-the-maskedtextbox-control"></a><span data-ttu-id="acb0a-111">MaskedTextBox denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="acb0a-111">To host the MaskedTextBox control</span></span>  
  
1.  <span data-ttu-id="acb0a-112">Adlı bir WPF uygulaması projesi oluşturmak `HostingWfInWpfWithXaml`.</span><span class="sxs-lookup"><span data-stu-id="acb0a-112">Create a WPF Application project named `HostingWfInWpfWithXaml`.</span></span>  
  
2.  <span data-ttu-id="acb0a-113">Aşağıdaki derlemelere başvurular ekleyin.</span><span class="sxs-lookup"><span data-stu-id="acb0a-113">Add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="acb0a-114">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="acb0a-114">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="acb0a-115">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="acb0a-115">System.Windows.Forms</span></span>  
  
3.  <span data-ttu-id="acb0a-116">İçinde MainWindow.xaml açın [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="acb0a-116">Open MainWindow.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
4.  <span data-ttu-id="acb0a-117">İçinde <xref:System.Windows.Window> öğesi, aşağıdaki ad alanı eşlemesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="acb0a-117">In the <xref:System.Windows.Window> element, add the following namespace mapping.</span></span> <span data-ttu-id="acb0a-118">`wf` Ad alanı eşlemesi, Windows Forms denetimi içeren bütünleştirilmiş kod başvuru oluşturur.</span><span class="sxs-lookup"><span data-stu-id="acb0a-118">The `wf` namespace mapping establishes a reference to the assembly that contains the Windows Forms control.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  <span data-ttu-id="acb0a-119">İçinde <xref:System.Windows.Controls.Grid> aşağıdaki XAML öğesini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="acb0a-119">In the <xref:System.Windows.Controls.Grid> element add the following XAML.</span></span>  
  
     <span data-ttu-id="acb0a-120"><xref:System.Windows.Forms.MaskedTextBox> Denetimi, bir alt öğesi olarak oluşturulur <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimi.</span><span class="sxs-lookup"><span data-stu-id="acb0a-120">The <xref:System.Windows.Forms.MaskedTextBox> control is created as a child of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control.</span></span>  
  
     [!code-xaml[HostingWfInWpfWithXaml#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWpfWithXaml/CSharp/HostingWfInWpf/Window1.xaml#3)]  
  
6.  <span data-ttu-id="acb0a-121">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="acb0a-121">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acb0a-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="acb0a-122">See also</span></span>
- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="acb0a-123">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="acb0a-123">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="acb0a-124">İzlenecek yol: WPF'de Windows Forms denetimini barındırma</span><span class="sxs-lookup"><span data-stu-id="acb0a-124">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [<span data-ttu-id="acb0a-125">İzlenecek yol: WPF'de Windows Forms bileşik denetimini barındırma</span><span class="sxs-lookup"><span data-stu-id="acb0a-125">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="acb0a-126">İzlenecek yol: WPF bileşik denetimini Windows Forms içinde barındırma</span><span class="sxs-lookup"><span data-stu-id="acb0a-126">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [<span data-ttu-id="acb0a-127">Windows Forms Denetimleri ve Eşdeğer WPF Denetimleri</span><span class="sxs-lookup"><span data-stu-id="acb0a-127">Windows Forms Controls and Equivalent WPF Controls</span></span>](../../../../docs/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls.md)
- [<span data-ttu-id="acb0a-128">Örnek XAML kullanarak WPF içerisinde bir Windows Forms denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="acb0a-128">Hosting a Windows Forms Control in WPF by Using XAML Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160000)
