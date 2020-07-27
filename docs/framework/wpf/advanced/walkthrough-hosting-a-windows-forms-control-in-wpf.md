---
title: WPF 'de Windows Forms denetimi barındırma
description: Zengin bir özellik kümesiyle çok sayıda denetim sağlayan Windows Presentation Foundation Windows Forms denetimlerini nasıl barındıralabileceğinizi öğrenin.
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 9cb88415-39b0-4c46-80c4-ff325b674286
ms.openlocfilehash: ec67cf9fabaa5b7aadbb2a3c21ebf8dd828ee20f
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164972"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf"></a><span data-ttu-id="3083a-103">İzlenecek yol: WPF içinde Windows Forms Denetimi Barındırma</span><span class="sxs-lookup"><span data-stu-id="3083a-103">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="3083a-104">zengin özellik kümesine sahip birçok denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="3083a-104">provides many controls with a rich feature set.</span></span> <span data-ttu-id="3083a-105">Ancak, bazen sayfalarınızda Windows Forms denetimlerini kullanmak isteyebilirsiniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="3083a-105">However, you may sometimes want to use Windows Forms controls on your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages.</span></span> <span data-ttu-id="3083a-106">Örneğin, varolan Windows Forms Denetimlerinde önemli bir yatırımınız olabilir veya benzersiz işlevler sağlayan bir Windows Forms denetimine sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3083a-106">For example, you may have a substantial investment in existing Windows Forms controls, or you may have a Windows Forms control that provides unique functionality.</span></span>

<span data-ttu-id="3083a-107">Bu izlenecek yol, <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> kod kullanarak sayfada bir Windows Forms denetiminin nasıl barındıralınacağını gösterir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="3083a-107">This walkthrough shows you how to host a Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page by using code.</span></span>

<span data-ttu-id="3083a-108">Bu kılavuzda gösterilen görevlerin tüm kod listesi için bkz. [WPF örneğinde Windows Forms denetimini barındırma](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWPF).</span><span class="sxs-lookup"><span data-stu-id="3083a-108">For a complete code listing of the tasks shown in this walkthrough, see [Hosting a Windows Forms Control in WPF Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWPF).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3083a-109">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="3083a-109">Prerequisites</span></span>

<span data-ttu-id="3083a-110">Bu yönergeyi tamamlamak için Visual Studio gerekir.</span><span class="sxs-lookup"><span data-stu-id="3083a-110">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="hosting-the-windows-forms-control"></a><span data-ttu-id="3083a-111">Windows Forms denetimini barındırma</span><span class="sxs-lookup"><span data-stu-id="3083a-111">Hosting the Windows Forms Control</span></span>

### <a name="to-host-the-maskedtextbox-control"></a><span data-ttu-id="3083a-112">MaskedTextBox denetimini barındırmak için</span><span class="sxs-lookup"><span data-stu-id="3083a-112">To host the MaskedTextBox control</span></span>

1. <span data-ttu-id="3083a-113">Adlı bir WPF uygulaması projesi oluşturun `HostingWfInWpf` .</span><span class="sxs-lookup"><span data-stu-id="3083a-113">Create a WPF Application project named `HostingWfInWpf`.</span></span>

2. <span data-ttu-id="3083a-114">Aşağıdaki derlemelere başvurular ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3083a-114">Add references to the following assemblies.</span></span>

    - <span data-ttu-id="3083a-115">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="3083a-115">WindowsFormsIntegration</span></span>

    - <span data-ttu-id="3083a-116">System. Windows. Forms</span><span class="sxs-lookup"><span data-stu-id="3083a-116">System.Windows.Forms</span></span>

3. <span data-ttu-id="3083a-117">WPF Tasarımcısında MainWindow. xaml ' i açın.</span><span class="sxs-lookup"><span data-stu-id="3083a-117">Open MainWindow.xaml in the WPF Designer.</span></span>

4. <span data-ttu-id="3083a-118">Öğeyi adlandırın <xref:System.Windows.Controls.Grid> `grid1` .</span><span class="sxs-lookup"><span data-stu-id="3083a-118">Name the <xref:System.Windows.Controls.Grid> element `grid1`.</span></span>

     [!code-xaml[HostingWfInWPF#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml#1)]

5. <span data-ttu-id="3083a-119">Tasarım görünümü veya XAML görünümünde <xref:System.Windows.Window> öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="3083a-119">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>

6. <span data-ttu-id="3083a-120">Özellikler penceresi, **Olaylar** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="3083a-120">In the Properties window, click the **Events** tab.</span></span>

7. <span data-ttu-id="3083a-121">Olaya çift tıklayın <xref:System.Windows.FrameworkElement.Loaded> .</span><span class="sxs-lookup"><span data-stu-id="3083a-121">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

8. <span data-ttu-id="3083a-122">Olayı işlemek için aşağıdaki kodu ekleyin <xref:System.Windows.FrameworkElement.Loaded> .</span><span class="sxs-lookup"><span data-stu-id="3083a-122">Insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

     [!code-csharp[HostingWfInWPF#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#10)]
     [!code-vb[HostingWfInWPF#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#10)]

9. <span data-ttu-id="3083a-123">Dosyanın en üstüne aşağıdaki `Imports` veya `using` ifadesini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3083a-123">At the top of the file, add the following `Imports` or `using` statement.</span></span>

     [!code-csharp[HostingWfInWPF#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#11)]
     [!code-vb[HostingWfInWPF#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#11)]

10. <span data-ttu-id="3083a-124">Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="3083a-124">Press **F5** to build and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="3083a-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3083a-125">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="3083a-126">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="3083a-126">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="3083a-127">İzlenecek yol: XAML Kullanarak WPF İçerisinde bir Windows Forms Denetimi Barındırma</span><span class="sxs-lookup"><span data-stu-id="3083a-127">Walkthrough: Hosting a Windows Forms Control in WPF by Using XAML</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml.md)
- [<span data-ttu-id="3083a-128">İzlenecek yol: WPF'de Windows Forms Bileşik Denetimini Barındırma</span><span class="sxs-lookup"><span data-stu-id="3083a-128">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="3083a-129">İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma</span><span class="sxs-lookup"><span data-stu-id="3083a-129">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [<span data-ttu-id="3083a-130">Windows Forms Denetimleri ve Eşdeğer WPF Denetimleri</span><span class="sxs-lookup"><span data-stu-id="3083a-130">Windows Forms Controls and Equivalent WPF Controls</span></span>](windows-forms-controls-and-equivalent-wpf-controls.md)
- [<span data-ttu-id="3083a-131">WPF örneğinde Windows Forms denetimini barındırma</span><span class="sxs-lookup"><span data-stu-id="3083a-131">Hosting a Windows Forms Control in WPF Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWPF)
