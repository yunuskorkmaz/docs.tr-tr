---
title: "İzlenecek yol: WPF'de Windows Forms denetimini barındırma"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 9cb88415-39b0-4c46-80c4-ff325b674286
ms.openlocfilehash: 8ef13ef89072f91c847a05facbcce344dda6ade2
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374901"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf"></a><span data-ttu-id="58010-102">İzlenecek yol: WPF'de Windows Forms denetimini barındırma</span><span class="sxs-lookup"><span data-stu-id="58010-102">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="58010-103">pek çok denetimi ile zengin özellik kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="58010-103">provides many controls with a rich feature set.</span></span> <span data-ttu-id="58010-104">Ancak, bazen kullanmak isteyebilirsiniz [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimlerini, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sayfaları.</span><span class="sxs-lookup"><span data-stu-id="58010-104">However, you may sometimes want to use [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls on your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages.</span></span> <span data-ttu-id="58010-105">Örneğin, var olan önemli bir yatırım olabilir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri veya olabilir bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] benzersiz işlevsellik sağlayan denetimi.</span><span class="sxs-lookup"><span data-stu-id="58010-105">For example, you may have a substantial investment in existing [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls, or you may have a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control that provides unique functionality.</span></span>

<span data-ttu-id="58010-106">Bu izlenecek yol size nasıl barındıracağınızı gösterir bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> denetimi bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kodu kullanarak sayfa.</span><span class="sxs-lookup"><span data-stu-id="58010-106">This walkthrough shows you how to host a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page by using code.</span></span>

<span data-ttu-id="58010-107">Bu izlenecek yolda gösterilen görevler tam kod listesi için bkz. [WPF Örneği'nde bir Windows Forms denetimi barındırma](https://go.microsoft.com/fwlink/?LinkID=160057).</span><span class="sxs-lookup"><span data-stu-id="58010-107">For a complete code listing of the tasks shown in this walkthrough, see [Hosting a Windows Forms Control in WPF Sample](https://go.microsoft.com/fwlink/?LinkID=160057).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="58010-108">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="58010-108">Prerequisites</span></span>

<span data-ttu-id="58010-109">Bu izlenecek yolu tamamlamak için Visual Studio ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="58010-109">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="hosting-the-windows-forms-control"></a><span data-ttu-id="58010-110">Windows Forms denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="58010-110">Hosting the Windows Forms Control</span></span>

### <a name="to-host-the-maskedtextbox-control"></a><span data-ttu-id="58010-111">MaskedTextBox denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="58010-111">To host the MaskedTextBox control</span></span>

1.  <span data-ttu-id="58010-112">Adlı bir WPF uygulaması projesi oluşturmak `HostingWfInWpf`.</span><span class="sxs-lookup"><span data-stu-id="58010-112">Create a WPF Application project named `HostingWfInWpf`.</span></span>

2.  <span data-ttu-id="58010-113">Aşağıdaki derlemelere başvurular ekleyin.</span><span class="sxs-lookup"><span data-stu-id="58010-113">Add references to the following assemblies.</span></span>

    -   <span data-ttu-id="58010-114">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="58010-114">WindowsFormsIntegration</span></span>

    -   <span data-ttu-id="58010-115">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="58010-115">System.Windows.Forms</span></span>

3.  <span data-ttu-id="58010-116">İçinde MainWindow.xaml açın [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="58010-116">Open MainWindow.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>

4.  <span data-ttu-id="58010-117">Adı <xref:System.Windows.Controls.Grid> öğesi `grid1`.</span><span class="sxs-lookup"><span data-stu-id="58010-117">Name the <xref:System.Windows.Controls.Grid> element `grid1`.</span></span>

     [!code-xaml[HostingWfInWPF#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml#1)]

5.  <span data-ttu-id="58010-118">Tasarım görünümü veya XAML görünümünde seçin <xref:System.Windows.Window> öğesi.</span><span class="sxs-lookup"><span data-stu-id="58010-118">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>

6.  <span data-ttu-id="58010-119">Özellikler penceresinde tıklayın **olayları** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="58010-119">In the Properties window, click the **Events** tab.</span></span>

7.  <span data-ttu-id="58010-120">Çift <xref:System.Windows.FrameworkElement.Loaded> olay.</span><span class="sxs-lookup"><span data-stu-id="58010-120">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

8.  <span data-ttu-id="58010-121">İşlemek için aşağıdaki kodu ekleyin <xref:System.Windows.FrameworkElement.Loaded> olay.</span><span class="sxs-lookup"><span data-stu-id="58010-121">Insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

     [!code-csharp[HostingWfInWPF#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#10)]
     [!code-vb[HostingWfInWPF#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#10)]

9. <span data-ttu-id="58010-122">Dosyasının en üstüne aşağıdakileri ekleyin `Imports` veya `using` deyimi.</span><span class="sxs-lookup"><span data-stu-id="58010-122">At the top of the file, add the following `Imports` or `using` statement.</span></span>

     [!code-csharp[HostingWfInWPF#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#11)]
     [!code-vb[HostingWfInWPF#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#11)]

10. <span data-ttu-id="58010-123">Tuşuna **F5** oluşturun ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="58010-123">Press **F5** to build and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="58010-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58010-124">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="58010-125">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="58010-125">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="58010-126">İzlenecek yol: XAML kullanarak WPF içerisinde bir Windows Forms denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="58010-126">Walkthrough: Hosting a Windows Forms Control in WPF by Using XAML</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml.md)
- [<span data-ttu-id="58010-127">İzlenecek yol: WPF'de Windows Forms bileşik denetimini barındırma</span><span class="sxs-lookup"><span data-stu-id="58010-127">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="58010-128">İzlenecek yol: WPF bileşik denetimini Windows Forms içinde barındırma</span><span class="sxs-lookup"><span data-stu-id="58010-128">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [<span data-ttu-id="58010-129">Windows Forms Denetimleri ve Eşdeğer WPF Denetimleri</span><span class="sxs-lookup"><span data-stu-id="58010-129">Windows Forms Controls and Equivalent WPF Controls</span></span>](windows-forms-controls-and-equivalent-wpf-controls.md)
- [<span data-ttu-id="58010-130">Bir WPF Örneği'nde Windows Forms denetimi barındırma</span><span class="sxs-lookup"><span data-stu-id="58010-130">Hosting a Windows Forms Control in WPF Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160057)
