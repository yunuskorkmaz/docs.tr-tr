---
title: WPF 'de Windows Forms denetimi barındırma
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 9cb88415-39b0-4c46-80c4-ff325b674286
ms.openlocfilehash: 5e994f65c0665a5726c4c8c19141da5ea3f5e6f6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794176"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf"></a><span data-ttu-id="f8f07-102">İzlenecek yol: WPF'de Windows Forms Denetimini Barındırma</span><span class="sxs-lookup"><span data-stu-id="f8f07-102">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="f8f07-103">zengin özellik kümesiyle birçok denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="f8f07-103">provides many controls with a rich feature set.</span></span> <span data-ttu-id="f8f07-104">Ancak, bazı durumlarda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sayfalarınızda Windows Forms denetimleri kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8f07-104">However, you may sometimes want to use Windows Forms controls on your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages.</span></span> <span data-ttu-id="f8f07-105">Örneğin, varolan Windows Forms Denetimlerinde önemli bir yatırımınız olabilir veya benzersiz işlevler sağlayan bir Windows Forms denetimine sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8f07-105">For example, you may have a substantial investment in existing Windows Forms controls, or you may have a Windows Forms control that provides unique functionality.</span></span>

<span data-ttu-id="f8f07-106">Bu izlenecek yol, kod kullanarak bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sayfasında Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> denetiminin nasıl barındıralınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f8f07-106">This walkthrough shows you how to host a Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page by using code.</span></span>

<span data-ttu-id="f8f07-107">Bu kılavuzda gösterilen görevlerin tüm kod listesi için bkz. [WPF örneğinde Windows Forms denetimini barındırma](https://go.microsoft.com/fwlink/?LinkID=160057).</span><span class="sxs-lookup"><span data-stu-id="f8f07-107">For a complete code listing of the tasks shown in this walkthrough, see [Hosting a Windows Forms Control in WPF Sample](https://go.microsoft.com/fwlink/?LinkID=160057).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f8f07-108">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="f8f07-108">Prerequisites</span></span>

<span data-ttu-id="f8f07-109">Bu yönergeyi tamamlamak için Visual Studio gerekir.</span><span class="sxs-lookup"><span data-stu-id="f8f07-109">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="hosting-the-windows-forms-control"></a><span data-ttu-id="f8f07-110">Windows Forms denetimini barındırma</span><span class="sxs-lookup"><span data-stu-id="f8f07-110">Hosting the Windows Forms Control</span></span>

### <a name="to-host-the-maskedtextbox-control"></a><span data-ttu-id="f8f07-111">MaskedTextBox denetimini barındırmak için</span><span class="sxs-lookup"><span data-stu-id="f8f07-111">To host the MaskedTextBox control</span></span>

1. <span data-ttu-id="f8f07-112">`HostingWfInWpf`adlı bir WPF uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f8f07-112">Create a WPF Application project named `HostingWfInWpf`.</span></span>

2. <span data-ttu-id="f8f07-113">Aşağıdaki derlemelere başvurular ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f8f07-113">Add references to the following assemblies.</span></span>

    - <span data-ttu-id="f8f07-114">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="f8f07-114">WindowsFormsIntegration</span></span>

    - <span data-ttu-id="f8f07-115">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="f8f07-115">System.Windows.Forms</span></span>

3. <span data-ttu-id="f8f07-116">WPF Tasarımcısında MainWindow. xaml ' i açın.</span><span class="sxs-lookup"><span data-stu-id="f8f07-116">Open MainWindow.xaml in the WPF Designer.</span></span>

4. <span data-ttu-id="f8f07-117"><xref:System.Windows.Controls.Grid> öğesi `grid1`adlandırın.</span><span class="sxs-lookup"><span data-stu-id="f8f07-117">Name the <xref:System.Windows.Controls.Grid> element `grid1`.</span></span>

     [!code-xaml[HostingWfInWPF#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml#1)]

5. <span data-ttu-id="f8f07-118">Tasarım görünümü veya XAML görünümünde <xref:System.Windows.Window> öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="f8f07-118">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>

6. <span data-ttu-id="f8f07-119">Özellikler penceresi, **Olaylar** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f8f07-119">In the Properties window, click the **Events** tab.</span></span>

7. <span data-ttu-id="f8f07-120"><xref:System.Windows.FrameworkElement.Loaded> olayına çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f8f07-120">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

8. <span data-ttu-id="f8f07-121"><xref:System.Windows.FrameworkElement.Loaded> olayını işlemek için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f8f07-121">Insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

     [!code-csharp[HostingWfInWPF#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#10)]
     [!code-vb[HostingWfInWPF#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#10)]

9. <span data-ttu-id="f8f07-122">Dosyanın en üstüne aşağıdaki `Imports` veya `using` ifadesini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f8f07-122">At the top of the file, add the following `Imports` or `using` statement.</span></span>

     [!code-csharp[HostingWfInWPF#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#11)]
     [!code-vb[HostingWfInWPF#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#11)]

10. <span data-ttu-id="f8f07-123">Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="f8f07-123">Press **F5** to build and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="f8f07-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8f07-124">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="f8f07-125">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="f8f07-125">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="f8f07-126">İzlenecek yol: XAML Kullanarak WPF İçerisinde bir Windows Forms Denetimi Barındırma</span><span class="sxs-lookup"><span data-stu-id="f8f07-126">Walkthrough: Hosting a Windows Forms Control in WPF by Using XAML</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml.md)
- [<span data-ttu-id="f8f07-127">İzlenecek yol: WPF'de Windows Forms Bileşik Denetimini Barındırma</span><span class="sxs-lookup"><span data-stu-id="f8f07-127">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="f8f07-128">İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma</span><span class="sxs-lookup"><span data-stu-id="f8f07-128">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [<span data-ttu-id="f8f07-129">Windows Forms Denetimleri ve Eşdeğer WPF Denetimleri</span><span class="sxs-lookup"><span data-stu-id="f8f07-129">Windows Forms Controls and Equivalent WPF Controls</span></span>](windows-forms-controls-and-equivalent-wpf-controls.md)
- [<span data-ttu-id="f8f07-130">WPF örneğinde Windows Forms denetimini barındırma</span><span class="sxs-lookup"><span data-stu-id="f8f07-130">Hosting a Windows Forms Control in WPF Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160057)
