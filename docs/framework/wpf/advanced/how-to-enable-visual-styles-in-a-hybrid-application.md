---
title: 'Nasıl yapılır: Karma Uygulamada Görsel Stilleri Etkinleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- visual styles [Windows Forms]
ms.assetid: 95de9b9c-d804-405c-b2d1-49a88c1e0fe1
ms.openlocfilehash: 251c53a8665d2eae7c3b5bb23b0a388009362dcc
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960118"
---
# <a name="how-to-enable-visual-styles-in-a-hybrid-application"></a><span data-ttu-id="1773f-102">Nasıl yapılır: Karma Uygulamada Görsel Stilleri Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="1773f-102">How to: Enable Visual Styles in a Hybrid Application</span></span>
<span data-ttu-id="1773f-103">Bu konuda, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]tabanlı bir uygulamada barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetiminde görsel stillerin nasıl etkinleştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1773f-103">This topic shows how to enable visual styles on a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control hosted in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span>  
  
 <span data-ttu-id="1773f-104">Uygulamanız <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> yöntemini çağırırsa, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimlerinizin çoğu otomatik olarak görsel stilleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="1773f-104">If your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method, most of your [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls will automatically use visual styles.</span></span> <span data-ttu-id="1773f-105">Daha fazla bilgi için bkz. [görsel stillerle denetim işleme](../../winforms/controls/rendering-controls-with-visual-styles.md).</span><span class="sxs-lookup"><span data-stu-id="1773f-105">For more information, see [Rendering Controls with Visual Styles](../../winforms/controls/rendering-controls-with-visual-styles.md).</span></span>  
  
 <span data-ttu-id="1773f-106">Bu konuda gösterilen görevlerin tüm kod listesi için bkz. [karma uygulama örneğinde görsel stilleri etkinleştirme](https://go.microsoft.com/fwlink/?LinkID=159986).</span><span class="sxs-lookup"><span data-stu-id="1773f-106">For a complete code listing of the tasks illustrated in this topic, see [Enabling Visual Styles in a Hybrid Application Sample](https://go.microsoft.com/fwlink/?LinkID=159986).</span></span>  
  
## <a name="enabling-windows-forms-visual-styles"></a><span data-ttu-id="1773f-107">Windows Forms Görsel stilleri etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="1773f-107">Enabling Windows Forms Visual Styles</span></span>  
  
#### <a name="to-enable-windows-forms-visual-styles"></a><span data-ttu-id="1773f-108">Windows Forms Görsel stilleri etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="1773f-108">To enable Windows Forms visual styles</span></span>  
  
1. <span data-ttu-id="1773f-109">`HostingWfWithVisualStyles`adlı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir uygulama projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1773f-109">Create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Application project named `HostingWfWithVisualStyles`.</span></span>  
  
2. <span data-ttu-id="1773f-110">Çözüm Gezgini, aşağıdaki derlemelere başvurular ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1773f-110">In Solution Explorer, add references to the following assemblies.</span></span>  
  
    - <span data-ttu-id="1773f-111">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="1773f-111">WindowsFormsIntegration</span></span>  
  
    - <span data-ttu-id="1773f-112">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="1773f-112">System.Windows.Forms</span></span>  
  
3. <span data-ttu-id="1773f-113">Araç kutusunda, tasarım yüzeyine bir <xref:System.Windows.Controls.Grid> öğesi yerleştirmek için <xref:System.Windows.Controls.Grid> simgesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1773f-113">In the Toolbox, double-click the <xref:System.Windows.Controls.Grid> icon to place a <xref:System.Windows.Controls.Grid> element on the design surface.</span></span>  
  
4. <span data-ttu-id="1773f-114">Özellikler penceresi, <xref:System.Windows.FrameworkElement.Height%2A> ve <xref:System.Windows.FrameworkElement.Width%2A> özelliklerinin değerlerini **Otomatik**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1773f-114">In the Properties window, set the values of the <xref:System.Windows.FrameworkElement.Height%2A> and <xref:System.Windows.FrameworkElement.Width%2A> properties to **Auto**.</span></span>  
  
5. <span data-ttu-id="1773f-115">Tasarım görünümü veya XAML görünümünde <xref:System.Windows.Window>seçin.</span><span class="sxs-lookup"><span data-stu-id="1773f-115">In Design view or XAML view, select the <xref:System.Windows.Window>.</span></span>  
  
6. <span data-ttu-id="1773f-116">Özellikler penceresi, **Olaylar** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1773f-116">In the Properties window, click the **Events** tab.</span></span>  
  
7. <span data-ttu-id="1773f-117"><xref:System.Windows.FrameworkElement.Loaded> olayına çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1773f-117">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>
  
8. <span data-ttu-id="1773f-118">MainWindow. xaml. vb veya MainWindow.xaml.cs içinde, <xref:System.Windows.FrameworkElement.Loaded> olayını işlemek için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1773f-118">In MainWindow.xaml.vb or MainWindow.xaml.cs, insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>  
  
     [!code-csharp[HostingWfWithVisualStyles#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfWithVisualStyles/CSharp/HostingWfWithVisualStyles/Window1.xaml.cs#11)]
     [!code-vb[HostingWfWithVisualStyles#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfWithVisualStyles/VisualBasic/HostingWfWithVisualStyles/Window1.xaml.vb#11)]  
  
9. <span data-ttu-id="1773f-119">Uygulamayı derleyip çalıştırmak için F5'e basın.</span><span class="sxs-lookup"><span data-stu-id="1773f-119">Press F5 to build and run the application.</span></span>  
  
     <span data-ttu-id="1773f-120">[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi görsel stillerle boyanmıştır.</span><span class="sxs-lookup"><span data-stu-id="1773f-120">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is painted with visual styles.</span></span>  
  
## <a name="disabling-windows-forms-visual-styles"></a><span data-ttu-id="1773f-121">Windows Forms görsel stillerini devre dışı bırakma</span><span class="sxs-lookup"><span data-stu-id="1773f-121">Disabling Windows Forms Visual Styles</span></span>  
 <span data-ttu-id="1773f-122">Görsel stilleri devre dışı bırakmak için <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metoduna çağrıyı kaldırmanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="1773f-122">To disable visual styles, simply remove the call to the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>  
  
#### <a name="to-disable-windows-forms-visual-styles"></a><span data-ttu-id="1773f-123">Windows Forms görsel stillerini devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="1773f-123">To disable Windows Forms visual styles</span></span>  
  
1. <span data-ttu-id="1773f-124">Kod düzenleyicisinde MainWindow. xaml. vb veya MainWindow.xaml.cs öğesini açın.</span><span class="sxs-lookup"><span data-stu-id="1773f-124">Open MainWindow.xaml.vb or MainWindow.xaml.cs in the Code Editor.</span></span>  
  
2. <span data-ttu-id="1773f-125"><xref:System.Windows.Forms.Application.EnableVisualStyles%2A> yöntemine yapılan çağrıyı açıklama.</span><span class="sxs-lookup"><span data-stu-id="1773f-125">Comment out the call to the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>  
  
3. <span data-ttu-id="1773f-126">Uygulamayı derleyip çalıştırmak için F5'e basın.</span><span class="sxs-lookup"><span data-stu-id="1773f-126">Press F5 to build and run the application.</span></span>  
  
     <span data-ttu-id="1773f-127">[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi varsayılan sistem stiliyle boyanır.</span><span class="sxs-lookup"><span data-stu-id="1773f-127">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is painted with the default system style.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1773f-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1773f-128">See also</span></span>

- <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>
- <xref:System.Windows.Forms.VisualStyles>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="1773f-129">Denetimleri Görsel Stilde İşleme</span><span class="sxs-lookup"><span data-stu-id="1773f-129">Rendering Controls with Visual Styles</span></span>](../../winforms/controls/rendering-controls-with-visual-styles.md)
- [<span data-ttu-id="1773f-130">İzlenecek yol: WPF'de Windows Forms Denetimini Barındırma</span><span class="sxs-lookup"><span data-stu-id="1773f-130">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
