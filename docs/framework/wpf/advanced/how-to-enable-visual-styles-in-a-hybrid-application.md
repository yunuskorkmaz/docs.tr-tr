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
ms.openlocfilehash: f4684e277335a119d41d5bd79d504ed37a76d6fc
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44268477"
---
# <a name="how-to-enable-visual-styles-in-a-hybrid-application"></a><span data-ttu-id="b71c6-102">Nasıl yapılır: Karma Uygulamada Görsel Stilleri Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="b71c6-102">How to: Enable Visual Styles in a Hybrid Application</span></span>
<span data-ttu-id="b71c6-103">Bu konuda nasıl etkinleştirileceği gösterilmektedir [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] görsel stillerin bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetiminde barındırılan bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-tabanlı bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="b71c6-103">This topic shows how to enable [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] visual styles on a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control hosted in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span>  
  
 <span data-ttu-id="b71c6-104">Uygulamanız çağırıyorsa <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> yöntemi, çoğu, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] uygulamanız çalıştırıldığında denetimleri görsel stilde otomatik olarak kullanır [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b71c6-104">If your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method, most of your [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls will automatically use visual styles when your application is run on [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)].</span></span> <span data-ttu-id="b71c6-105">Daha fazla bilgi için [denetimleri görsel stilde işleme](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md).</span><span class="sxs-lookup"><span data-stu-id="b71c6-105">For more information, see [Rendering Controls with Visual Styles](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md).</span></span>  
  
 <span data-ttu-id="b71c6-106">Bu konu başlığında gösterilen görevlerin tam kod listesi için bkz. [karma uygulama örneğinde görsel stilleri etkinleştirme](https://go.microsoft.com/fwlink/?LinkID=159986).</span><span class="sxs-lookup"><span data-stu-id="b71c6-106">For a complete code listing of the tasks illustrated in this topic, see [Enabling Visual Styles in a Hybrid Application Sample](https://go.microsoft.com/fwlink/?LinkID=159986).</span></span>  
  
## <a name="enabling-windows-forms-visual-styles"></a><span data-ttu-id="b71c6-107">Forms görsel stilleri Windows etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="b71c6-107">Enabling Windows Forms Visual Styles</span></span>  
  
#### <a name="to-enable-windows-forms-visual-styles"></a><span data-ttu-id="b71c6-108">Windows Forms görsel stilleri etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="b71c6-108">To enable Windows Forms visual styles</span></span>  
  
1.  <span data-ttu-id="b71c6-109">Oluşturma bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] adlı uygulama projesi `HostingWfWithVisualStyles`.</span><span class="sxs-lookup"><span data-stu-id="b71c6-109">Create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Application project named `HostingWfWithVisualStyles`.</span></span>  
  
2.  <span data-ttu-id="b71c6-110">Çözüm Gezgini'nde, aşağıdaki derlemelere başvurular ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b71c6-110">In Solution Explorer, add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="b71c6-111">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="b71c6-111">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="b71c6-112">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="b71c6-112">System.Windows.Forms</span></span>  
  
3.  <span data-ttu-id="b71c6-113">Araç kutusunda çift <xref:System.Windows.Controls.Grid> simgesini yerleştirmek için bir <xref:System.Windows.Controls.Grid> tasarım yüzeyinde öğesi.</span><span class="sxs-lookup"><span data-stu-id="b71c6-113">In the Toolbox, double-click the <xref:System.Windows.Controls.Grid> icon to place a <xref:System.Windows.Controls.Grid> element on the design surface.</span></span>  
  
4.  <span data-ttu-id="b71c6-114">Özellikler penceresinde değerlerini ayarlayın <xref:System.Windows.FrameworkElement.Height%2A> ve <xref:System.Windows.FrameworkElement.Width%2A> özelliklerine **otomatik**.</span><span class="sxs-lookup"><span data-stu-id="b71c6-114">In the Properties window, set the values of the <xref:System.Windows.FrameworkElement.Height%2A> and <xref:System.Windows.FrameworkElement.Width%2A> properties to **Auto**.</span></span>  
  
5.  <span data-ttu-id="b71c6-115">Tasarım görünümü veya XAML görünümünde seçin <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="b71c6-115">In Design view or XAML view, select the <xref:System.Windows.Window>.</span></span>  
  
6.  <span data-ttu-id="b71c6-116">Özellikler penceresinde tıklayın **olayları** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="b71c6-116">In the Properties window, click the **Events** tab.</span></span>  
  
7.  <span data-ttu-id="b71c6-117">Çift <xref:System.Windows.FrameworkElement.Loaded> olay.</span><span class="sxs-lookup"><span data-stu-id="b71c6-117">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>
  
8.  <span data-ttu-id="b71c6-118">MainWindow.xaml.vb veya MainWindow.xaml.cs içinde işlemek için aşağıdaki kodu ekleyin <xref:System.Windows.FrameworkElement.Loaded> olay.</span><span class="sxs-lookup"><span data-stu-id="b71c6-118">In MainWindow.xaml.vb or MainWindow.xaml.cs, insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>  
  
     [!code-csharp[HostingWfWithVisualStyles#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfWithVisualStyles/CSharp/HostingWfWithVisualStyles/Window1.xaml.cs#11)]
     [!code-vb[HostingWfWithVisualStyles#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfWithVisualStyles/VisualBasic/HostingWfWithVisualStyles/Window1.xaml.vb#11)]  
  
9. <span data-ttu-id="b71c6-119">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b71c6-119">Press F5 to build and run the application.</span></span>  
  
     <span data-ttu-id="b71c6-120">[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Denetimi ile görsel stilleri boyanır.</span><span class="sxs-lookup"><span data-stu-id="b71c6-120">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is painted with visual styles.</span></span>  
  
## <a name="disabling-windows-forms-visual-styles"></a><span data-ttu-id="b71c6-121">Devre dışı Windows Forms görsel stilleri</span><span class="sxs-lookup"><span data-stu-id="b71c6-121">Disabling Windows Forms Visual Styles</span></span>  
 <span data-ttu-id="b71c6-122">Görsel stiller devre dışı bırakmak için basitçe çağrısını kaldırın <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b71c6-122">To disable visual styles, simply remove the call to the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>  
  
#### <a name="to-disable-windows-forms-visual-styles"></a><span data-ttu-id="b71c6-123">Windows Forms görsel stiller devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="b71c6-123">To disable Windows Forms visual styles</span></span>  
  
1.  <span data-ttu-id="b71c6-124">MainWindow.xaml.vb veya MainWindow.xaml.cs Kod Düzenleyicisi'nde açın.</span><span class="sxs-lookup"><span data-stu-id="b71c6-124">Open MainWindow.xaml.vb or MainWindow.xaml.cs in the Code Editor.</span></span>  
  
2.  <span data-ttu-id="b71c6-125">Çağrı yorum <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b71c6-125">Comment out the call to the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>  
  
3.  <span data-ttu-id="b71c6-126">Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b71c6-126">Press F5 to build and run the application.</span></span>  
  
     <span data-ttu-id="b71c6-127">[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Denetimi, varsayılan sistem stiliyle boyanır.</span><span class="sxs-lookup"><span data-stu-id="b71c6-127">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is painted with the default system style.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b71c6-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b71c6-128">See Also</span></span>  
 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>  
 <xref:System.Windows.Forms.VisualStyles>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="b71c6-129">Denetimleri Görsel Stilde İşleme</span><span class="sxs-lookup"><span data-stu-id="b71c6-129">Rendering Controls with Visual Styles</span></span>](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)  
 [<span data-ttu-id="b71c6-130">İzlenecek yol: WPF'de Windows Forms Denetimini Barındırma</span><span class="sxs-lookup"><span data-stu-id="b71c6-130">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)
