---
title: XAML kullanarak WPF 'de Windows Forms denetimi barındırma
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 1aef42cb-4cfb-44b4-9a7a-c02632d3d9c7
ms.openlocfilehash: 99c077801a26043e17e0d51ecc0a97b9608784c0
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095066"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml"></a><span data-ttu-id="3b30f-102">İzlenecek yol: XAML Kullanarak WPF İçerisinde bir Windows Forms Denetimi Barındırma</span><span class="sxs-lookup"><span data-stu-id="3b30f-102">Walkthrough: Hosting a Windows Forms Control in WPF by Using XAML</span></span>
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="3b30f-103">zengin özellik kümesiyle birçok denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="3b30f-103">provides many controls with a rich feature set.</span></span> <span data-ttu-id="3b30f-104">Ancak, bazı durumlarda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sayfalarınızda Windows Forms denetimleri kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b30f-104">However, you may sometimes want to use Windows Forms controls on your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages.</span></span> <span data-ttu-id="3b30f-105">Örneğin, varolan Windows Forms Denetimlerinde önemli bir yatırımınız olabilir veya benzersiz işlevler sağlayan bir Windows Forms denetimine sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b30f-105">For example, you may have a substantial investment in existing Windows Forms controls, or you may have a Windows Forms control that provides unique functionality.</span></span>  
  
 <span data-ttu-id="3b30f-106">Bu izlenecek yol, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]kullanarak bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sayfasında Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> denetiminin nasıl barındırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3b30f-106">This walkthrough shows you how to host a Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 <span data-ttu-id="3b30f-107">Bu kılavuzda gösterilen görevlerin tüm kod listesi için bkz. [XAML örneği kullanarak WPF 'de Windows Forms denetimini barındırma](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWpfWithXaml).</span><span class="sxs-lookup"><span data-stu-id="3b30f-107">For a complete code listing of the tasks shown in this walkthrough, see [Hosting a Windows Forms Control in WPF by Using XAML Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWpfWithXaml).</span></span>
  
## <a name="prerequisites"></a><span data-ttu-id="3b30f-108">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="3b30f-108">Prerequisites</span></span>  

<span data-ttu-id="3b30f-109">Bu yönergeyi tamamlamak için Visual Studio gerekir.</span><span class="sxs-lookup"><span data-stu-id="3b30f-109">You need Visual Studio to complete this walkthrough.</span></span>  
  
## <a name="hosting-the-windows-forms-control"></a><span data-ttu-id="3b30f-110">Windows Forms denetimini barındırma</span><span class="sxs-lookup"><span data-stu-id="3b30f-110">Hosting the Windows Forms Control</span></span>  
  
#### <a name="to-host-the-maskedtextbox-control"></a><span data-ttu-id="3b30f-111">MaskedTextBox denetimini barındırmak için</span><span class="sxs-lookup"><span data-stu-id="3b30f-111">To host the MaskedTextBox control</span></span>  
  
1. <span data-ttu-id="3b30f-112">`HostingWfInWpfWithXaml`adlı bir WPF uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3b30f-112">Create a WPF Application project named `HostingWfInWpfWithXaml`.</span></span>  
  
2. <span data-ttu-id="3b30f-113">Aşağıdaki derlemelere başvurular ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3b30f-113">Add references to the following assemblies.</span></span>  
  
    - <span data-ttu-id="3b30f-114">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="3b30f-114">WindowsFormsIntegration</span></span>  
  
    - <span data-ttu-id="3b30f-115">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="3b30f-115">System.Windows.Forms</span></span>  
  
3. <span data-ttu-id="3b30f-116">WPF Tasarımcısında MainWindow. xaml ' i açın.</span><span class="sxs-lookup"><span data-stu-id="3b30f-116">Open MainWindow.xaml in the WPF Designer.</span></span>  
  
4. <span data-ttu-id="3b30f-117"><xref:System.Windows.Window> öğesinde, aşağıdaki ad alanı eşlemesini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3b30f-117">In the <xref:System.Windows.Window> element, add the following namespace mapping.</span></span> <span data-ttu-id="3b30f-118">`wf` ad alanı eşlemesi, Windows Forms denetimini içeren derlemeye bir başvuru oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3b30f-118">The `wf` namespace mapping establishes a reference to the assembly that contains the Windows Forms control.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5. <span data-ttu-id="3b30f-119"><xref:System.Windows.Controls.Grid> öğesinde aşağıdaki XAML 'yi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3b30f-119">In the <xref:System.Windows.Controls.Grid> element add the following XAML.</span></span>  
  
     <span data-ttu-id="3b30f-120"><xref:System.Windows.Forms.MaskedTextBox> denetimi, <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetiminin bir alt öğesi olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3b30f-120">The <xref:System.Windows.Forms.MaskedTextBox> control is created as a child of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control.</span></span>  
  
     [!code-xaml[HostingWfInWpfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWpfWithXaml/CSharp/HostingWfInWpf/Window1.xaml#3)]  
  
6. <span data-ttu-id="3b30f-121">Uygulamayı derleyip çalıştırmak için F5'e basın.</span><span class="sxs-lookup"><span data-stu-id="3b30f-121">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b30f-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b30f-122">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="3b30f-123">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="3b30f-123">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="3b30f-124">İzlenecek yol: WPF'de Windows Forms Denetimini Barındırma</span><span class="sxs-lookup"><span data-stu-id="3b30f-124">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [<span data-ttu-id="3b30f-125">İzlenecek yol: WPF'de Windows Forms Bileşik Denetimini Barındırma</span><span class="sxs-lookup"><span data-stu-id="3b30f-125">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="3b30f-126">İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma</span><span class="sxs-lookup"><span data-stu-id="3b30f-126">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [<span data-ttu-id="3b30f-127">Windows Forms Denetimleri ve Eşdeğer WPF Denetimleri</span><span class="sxs-lookup"><span data-stu-id="3b30f-127">Windows Forms Controls and Equivalent WPF Controls</span></span>](windows-forms-controls-and-equivalent-wpf-controls.md)
- [<span data-ttu-id="3b30f-128">XAML örneğini kullanarak WPF 'de Windows Forms denetimini barındırma</span><span class="sxs-lookup"><span data-stu-id="3b30f-128">Hosting a Windows Forms Control in WPF by Using XAML Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWpfWithXaml)
