---
title: 'Nasıl yapılır: FlowLayoutPanel Denetiminde Alt Denetimleri Sabitleme ve Yerleştirme'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- layout [Windows Forms], child controls
- FlowLayoutPanel control [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
ms.assetid: a2bcdfca-9b63-45e6-9c0e-3411015cba98
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 183e9ea4a8451b3d1ed59aa5200dd4da22e50cf1
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a><span data-ttu-id="cbb8b-102">Nasıl yapılır: FlowLayoutPanel Denetiminde Alt Denetimleri Sabitleme ve Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="cbb8b-102">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>
<span data-ttu-id="cbb8b-103"><xref:System.Windows.Forms.FlowLayoutPanel> Kontrol destekler <xref:System.Windows.Forms.Control.Anchor%2A> ve <xref:System.Windows.Forms.Control.Dock%2A> alt denetimlerinden özelliklerinde.</span><span class="sxs-lookup"><span data-stu-id="cbb8b-103">The <xref:System.Windows.Forms.FlowLayoutPanel> control supports the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties in its child controls.</span></span>  
  
### <a name="to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a><span data-ttu-id="cbb8b-104">Sabitleme ve yerleştirme FlowLayoutPanel denetiminde alt denetimleri için</span><span class="sxs-lookup"><span data-stu-id="cbb8b-104">To anchor and dock child controls in a FlowLayoutPanel control</span></span>  
  
1.  <span data-ttu-id="cbb8b-105">Oluşturma bir <xref:System.Windows.Forms.FlowLayoutPanel> formunuzda denetim.</span><span class="sxs-lookup"><span data-stu-id="cbb8b-105">Create a <xref:System.Windows.Forms.FlowLayoutPanel> control on your form.</span></span>  
  
2.  <span data-ttu-id="cbb8b-106">Ayarlama <xref:System.Windows.Forms.Control.Width%2A> , <xref:System.Windows.Forms.FlowLayoutPanel> denetimini **300**ve kendi <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> için <xref:System.Windows.Forms.FlowDirection.TopDown>.</span><span class="sxs-lookup"><span data-stu-id="cbb8b-106">Set the <xref:System.Windows.Forms.Control.Width%2A> of the <xref:System.Windows.Forms.FlowLayoutPanel> control to **300**, and set its <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> to <xref:System.Windows.Forms.FlowDirection.TopDown>.</span></span>  
  
3.  <span data-ttu-id="cbb8b-107">İki oluşturmak <xref:System.Windows.Forms.Button> denetler ve bunların içine yerleştirin <xref:System.Windows.Forms.FlowLayoutPanel> denetim.</span><span class="sxs-lookup"><span data-stu-id="cbb8b-107">Create two <xref:System.Windows.Forms.Button> controls, and place them in the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
4.  <span data-ttu-id="cbb8b-108">Ayarlama <xref:System.Windows.Forms.Control.Width%2A> için ilk düğmesinin **200**.</span><span class="sxs-lookup"><span data-stu-id="cbb8b-108">Set the <xref:System.Windows.Forms.Control.Width%2A> of the first button to **200**.</span></span>  
  
5.  <span data-ttu-id="cbb8b-109">Ayarlama <xref:System.Windows.Forms.Control.Dock%2A> ikinci düğme özelliğinin <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="cbb8b-109">Set the <xref:System.Windows.Forms.Control.Dock%2A> property of the second button to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cbb8b-110">İkinci düğme ilk düğme aynı genişliğe varsayar.</span><span class="sxs-lookup"><span data-stu-id="cbb8b-110">The second button assumes the same width as the first button.</span></span> <span data-ttu-id="cbb8b-111">Genişliği boyunca genişlemez <xref:System.Windows.Forms.FlowLayoutPanel> denetim.</span><span class="sxs-lookup"><span data-stu-id="cbb8b-111">It does not stretch across the width of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
6.  <span data-ttu-id="cbb8b-112">Ayarlama <xref:System.Windows.Forms.Control.Dock%2A> ikinci düğme özelliğinin `None`.</span><span class="sxs-lookup"><span data-stu-id="cbb8b-112">Set the <xref:System.Windows.Forms.Control.Dock%2A> property of the second button to `None`.</span></span> <span data-ttu-id="cbb8b-113">Bu, özgün genişliğinin varsaymak düğmesi neden olur.</span><span class="sxs-lookup"><span data-stu-id="cbb8b-113">This causes the button to assume its original width.</span></span>  
  
7.  <span data-ttu-id="cbb8b-114">Ayarlama <xref:System.Windows.Forms.Control.Anchor%2A> ikinci düğme özelliğinin `Left, Right`.</span><span class="sxs-lookup"><span data-stu-id="cbb8b-114">Set the <xref:System.Windows.Forms.Control.Anchor%2A> property of the second button to `Left, Right`.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="cbb8b-115">İkinci düğme ilk düğme aynı genişliğe varsayar.</span><span class="sxs-lookup"><span data-stu-id="cbb8b-115">The second button assumes the same width as the first button.</span></span> <span data-ttu-id="cbb8b-116">Genişliği boyunca genişlemez <xref:System.Windows.Forms.FlowLayoutPanel> denetim.</span><span class="sxs-lookup"><span data-stu-id="cbb8b-116">It does not stretch across the width of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span> <span data-ttu-id="cbb8b-117">Sabitleme ve yerleştirme içinde için genel kural budur <xref:System.Windows.Forms.FlowLayoutPanel> denetimi: dikey akış yönleri için <xref:System.Windows.Forms.FlowLayoutPanel> denetim hesaplar sütun geniş alt denetiminden kapsanan bir sütunun genişliği.</span><span class="sxs-lookup"><span data-stu-id="cbb8b-117">This is the general rule for anchoring and docking in the <xref:System.Windows.Forms.FlowLayoutPanel> control: for vertical flow directions, the <xref:System.Windows.Forms.FlowLayoutPanel> control calculates the width of an implied column from the widest child control in the column.</span></span> <span data-ttu-id="cbb8b-118">Tüm bu sütunla denetimlerinde <xref:System.Windows.Forms.Control.Anchor%2A> veya <xref:System.Windows.Forms.Control.Dock%2A> hizalı ya da örtük bu sütunu sığdırmak için uzatılmış özellikleri.</span><span class="sxs-lookup"><span data-stu-id="cbb8b-118">All other controls in this column with <xref:System.Windows.Forms.Control.Anchor%2A> or <xref:System.Windows.Forms.Control.Dock%2A> properties are aligned or stretched to fit this implied column.</span></span> <span data-ttu-id="cbb8b-119">Davranış yatay akış yönleri için benzer şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="cbb8b-119">The behavior works in a similar way for horizontal flow directions.</span></span> <span data-ttu-id="cbb8b-120"><xref:System.Windows.Forms.FlowLayoutPanel> Denetim satırda en uzun alt denetiminden kapsanan bir satırın yüksekliğini hesaplar ve tüm yerleşik veya bağlantılı alt denetimleri bu satırda hizalı veya örtük satır sığacak şekilde boyutlandırılmış.</span><span class="sxs-lookup"><span data-stu-id="cbb8b-120">The <xref:System.Windows.Forms.FlowLayoutPanel> control calculates the height of an implied row from the tallest child control in the row, and all docked or anchored child controls in this row are aligned or sized to fit the implied row.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbb8b-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="cbb8b-121">Example</span></span>  
 <span data-ttu-id="cbb8b-122">Bağlantılı ve mavi düğmesini göre sabitlenmiş dört düğme aşağıdaki çizimde gösterilmektedir bir <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="cbb8b-122">The following illustration shows four buttons that are anchored and docked relative to the blue button in a <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="cbb8b-123"><xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> Olan <xref:System.Windows.Forms.FlowDirection.LeftToRight>.</span><span class="sxs-lookup"><span data-stu-id="cbb8b-123">The <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> is <xref:System.Windows.Forms.FlowDirection.LeftToRight>.</span></span>  
  
 <span data-ttu-id="cbb8b-124">![FlowLayoutPanel bağlama](../../../../docs/framework/winforms/controls/media/net-flpanchorexp.gif "NET_FLPanchorExp")</span><span class="sxs-lookup"><span data-stu-id="cbb8b-124">![FlowLayoutPanel anchoring](../../../../docs/framework/winforms/controls/media/net-flpanchorexp.gif "NET_FLPanchorExp")</span></span>  
  
 <span data-ttu-id="cbb8b-125">Bağlantılı ve mavi düğmesini göre sabitlenmiş dört düğme aşağıdaki çizimde gösterilmektedir bir <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="cbb8b-125">The following illustration shows four buttons that are anchored and docked relative to the blue button in a <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="cbb8b-126"><xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> Olan <xref:System.Windows.Forms.FlowDirection.TopDown>.</span><span class="sxs-lookup"><span data-stu-id="cbb8b-126">The <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> is <xref:System.Windows.Forms.FlowDirection.TopDown>.</span></span>  
  
 <span data-ttu-id="cbb8b-127">![FlowLayoutPanel bağlama](../../../../docs/framework/winforms/controls/media/vs-flpanchor2.gif "VS_FLPanchor2")</span><span class="sxs-lookup"><span data-stu-id="cbb8b-127">![FlowLayoutPanel anchoring](../../../../docs/framework/winforms/controls/media/vs-flpanchor2.gif "VS_FLPanchor2")</span></span>  
  
 <span data-ttu-id="cbb8b-128">Aşağıdaki kod örneğinde çeşitli gösterilmektedir <xref:System.Windows.Forms.Control.Anchor%2A> özellik değerleri için bir <xref:System.Windows.Forms.Button> denetim bir <xref:System.Windows.Forms.FlowLayoutPanel> denetim.</span><span class="sxs-lookup"><span data-stu-id="cbb8b-128">The following code example demonstrates various <xref:System.Windows.Forms.Control.Anchor%2A> property values for a <xref:System.Windows.Forms.Button> control in a <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/CS/FlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/VB/FlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cbb8b-129">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="cbb8b-129">Compiling the Code</span></span>  
 <span data-ttu-id="cbb8b-130">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="cbb8b-130">This example requires:</span></span>  
  
-   <span data-ttu-id="cbb8b-131">Sistem, System.Data, System.Drawing ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="cbb8b-131">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="cbb8b-132">Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="cbb8b-132">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="cbb8b-133">Bu örnek ayrıca oluşturmak [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] yeni bir proje kodunu yapıştırma tarafından.</span><span class="sxs-lookup"><span data-stu-id="cbb8b-133">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="cbb8b-134">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="cbb8b-134">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbb8b-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cbb8b-135">See Also</span></span>  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 [<span data-ttu-id="cbb8b-136">FlowLayoutPanel Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cbb8b-136">FlowLayoutPanel Control Overview</span></span>](../../../../docs/framework/winforms/controls/flowlayoutpanel-control-overview.md)
