---
title: 'İzlenecek yol: XAML Kullanarak WPF İçerisinde bir Windows Forms Denetimi Barındırma'
ms.date: 03/30/2017
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 1aef42cb-4cfb-44b4-9a7a-c02632d3d9c7
ms.openlocfilehash: 71c11a377d49a5e010ab9f33547e0ef63e2c5eaf
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64605485"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml"></a><span data-ttu-id="ef764-102">İzlenecek yol: XAML Kullanarak WPF İçerisinde bir Windows Forms Denetimi Barındırma</span><span class="sxs-lookup"><span data-stu-id="ef764-102">Walkthrough: Hosting a Windows Forms Control in WPF by Using XAML</span></span>
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="ef764-103">pek çok denetimi ile zengin özellik kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ef764-103">provides many controls with a rich feature set.</span></span> <span data-ttu-id="ef764-104">Ancak, bazen kullanmak isteyebilirsiniz [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimlerini, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sayfaları.</span><span class="sxs-lookup"><span data-stu-id="ef764-104">However, you may sometimes want to use [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls on your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages.</span></span> <span data-ttu-id="ef764-105">Örneğin, var olan önemli bir yatırım olabilir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri veya olabilir bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] benzersiz işlevsellik sağlayan denetimi.</span><span class="sxs-lookup"><span data-stu-id="ef764-105">For example, you may have a substantial investment in existing [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls, or you may have a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control that provides unique functionality.</span></span>  
  
 <span data-ttu-id="ef764-106">Bu yönerge, bir Windows Forms barındırmak nasıl gösterir <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> denetimi bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kullanarak sayfa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ef764-106">This walkthrough shows you how to host a Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 <span data-ttu-id="ef764-107">Bu izlenecek yolda gösterilen görevler tam kod listesi için bkz. [WPF kullanarak XAML örnek olarak bir Windows Forms denetimi barındırma](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWpfWithXaml).</span><span class="sxs-lookup"><span data-stu-id="ef764-107">For a complete code listing of the tasks shown in this walkthrough, see [Hosting a Windows Forms Control in WPF by Using XAML Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWpfWithXaml).</span></span>
  
## <a name="prerequisites"></a><span data-ttu-id="ef764-108">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="ef764-108">Prerequisites</span></span>  

<span data-ttu-id="ef764-109">Bu izlenecek yolu tamamlamak için Visual Studio ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="ef764-109">You need Visual Studio to complete this walkthrough.</span></span>  
  
## <a name="hosting-the-windows-forms-control"></a><span data-ttu-id="ef764-110">Windows Forms denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="ef764-110">Hosting the Windows Forms Control</span></span>  
  
#### <a name="to-host-the-maskedtextbox-control"></a><span data-ttu-id="ef764-111">MaskedTextBox denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="ef764-111">To host the MaskedTextBox control</span></span>  
  
1. <span data-ttu-id="ef764-112">Adlı bir WPF uygulaması projesi oluşturmak `HostingWfInWpfWithXaml`.</span><span class="sxs-lookup"><span data-stu-id="ef764-112">Create a WPF Application project named `HostingWfInWpfWithXaml`.</span></span>  
  
2. <span data-ttu-id="ef764-113">Aşağıdaki derlemelere başvurular ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ef764-113">Add references to the following assemblies.</span></span>  
  
    - <span data-ttu-id="ef764-114">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="ef764-114">WindowsFormsIntegration</span></span>  
  
    - <span data-ttu-id="ef764-115">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="ef764-115">System.Windows.Forms</span></span>  
  
3. <span data-ttu-id="ef764-116">İçinde MainWindow.xaml açın [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ef764-116">Open MainWindow.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
4. <span data-ttu-id="ef764-117">İçinde <xref:System.Windows.Window> öğesi, aşağıdaki ad alanı eşlemesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ef764-117">In the <xref:System.Windows.Window> element, add the following namespace mapping.</span></span> <span data-ttu-id="ef764-118">`wf` Ad alanı eşlemesi, Windows Forms denetimi içeren bütünleştirilmiş kod başvuru oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ef764-118">The `wf` namespace mapping establishes a reference to the assembly that contains the Windows Forms control.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5. <span data-ttu-id="ef764-119">İçinde <xref:System.Windows.Controls.Grid> aşağıdaki XAML öğesini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ef764-119">In the <xref:System.Windows.Controls.Grid> element add the following XAML.</span></span>  
  
     <span data-ttu-id="ef764-120"><xref:System.Windows.Forms.MaskedTextBox> Denetimi, bir alt öğesi olarak oluşturulur <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetimi.</span><span class="sxs-lookup"><span data-stu-id="ef764-120">The <xref:System.Windows.Forms.MaskedTextBox> control is created as a child of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control.</span></span>  
  
     [!code-xaml[HostingWfInWpfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWpfWithXaml/CSharp/HostingWfInWpf/Window1.xaml#3)]  
  
6. <span data-ttu-id="ef764-121">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="ef764-121">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef764-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef764-122">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="ef764-123">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="ef764-123">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="ef764-124">İzlenecek yol: WPF'de Windows Forms denetimini barındırma</span><span class="sxs-lookup"><span data-stu-id="ef764-124">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [<span data-ttu-id="ef764-125">İzlenecek yol: WPF'de Windows Forms bileşik denetimini barındırma</span><span class="sxs-lookup"><span data-stu-id="ef764-125">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="ef764-126">İzlenecek yol: WPF bileşik denetimini Windows Forms içinde barındırma</span><span class="sxs-lookup"><span data-stu-id="ef764-126">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [<span data-ttu-id="ef764-127">Windows Forms Denetimleri ve Eşdeğer WPF Denetimleri</span><span class="sxs-lookup"><span data-stu-id="ef764-127">Windows Forms Controls and Equivalent WPF Controls</span></span>](windows-forms-controls-and-equivalent-wpf-controls.md)
- [<span data-ttu-id="ef764-128">Örnek XAML kullanarak WPF içerisinde bir Windows Forms denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="ef764-128">Hosting a Windows Forms Control in WPF by Using XAML Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160000)
