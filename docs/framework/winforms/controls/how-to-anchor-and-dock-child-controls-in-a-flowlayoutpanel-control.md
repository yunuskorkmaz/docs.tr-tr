---
title: 'Nasıl yapılır: Sabitleme ve FlowLayoutPanel denetiminde alt denetimleri yerleştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- layout [Windows Forms], child controls
- FlowLayoutPanel control [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
ms.assetid: a2bcdfca-9b63-45e6-9c0e-3411015cba98
ms.openlocfilehash: 9087045aaace5463d375af6850f822abefd45fb7
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56220932"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a><span data-ttu-id="8e5d8-102">Nasıl yapılır: Sabitleme ve FlowLayoutPanel denetiminde alt denetimleri yerleştirme</span><span class="sxs-lookup"><span data-stu-id="8e5d8-102">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>
<span data-ttu-id="8e5d8-103"><xref:System.Windows.Forms.FlowLayoutPanel> Denetim destekler <xref:System.Windows.Forms.Control.Anchor%2A> ve <xref:System.Windows.Forms.Control.Dock%2A> kendi alt denetimlerindeki özellikler.</span><span class="sxs-lookup"><span data-stu-id="8e5d8-103">The <xref:System.Windows.Forms.FlowLayoutPanel> control supports the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties in its child controls.</span></span>  
  
### <a name="to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a><span data-ttu-id="8e5d8-104">Sabitleme ve yerleştirme FlowLayoutPanel denetiminde alt denetimleri için</span><span class="sxs-lookup"><span data-stu-id="8e5d8-104">To anchor and dock child controls in a FlowLayoutPanel control</span></span>  
  
1.  <span data-ttu-id="8e5d8-105">Oluşturma bir <xref:System.Windows.Forms.FlowLayoutPanel> formunuzdaki denetimi.</span><span class="sxs-lookup"><span data-stu-id="8e5d8-105">Create a <xref:System.Windows.Forms.FlowLayoutPanel> control on your form.</span></span>  
  
2.  <span data-ttu-id="8e5d8-106">Ayarlama <xref:System.Windows.Forms.Control.Width%2A> , <xref:System.Windows.Forms.FlowLayoutPanel> denetimini **300**ve onun <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> için <xref:System.Windows.Forms.FlowDirection.TopDown>.</span><span class="sxs-lookup"><span data-stu-id="8e5d8-106">Set the <xref:System.Windows.Forms.Control.Width%2A> of the <xref:System.Windows.Forms.FlowLayoutPanel> control to **300**, and set its <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> to <xref:System.Windows.Forms.FlowDirection.TopDown>.</span></span>  
  
3.  <span data-ttu-id="8e5d8-107">İki <xref:System.Windows.Forms.Button> denetler ve yerleştirebilirsiniz <xref:System.Windows.Forms.FlowLayoutPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="8e5d8-107">Create two <xref:System.Windows.Forms.Button> controls, and place them in the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
4.  <span data-ttu-id="8e5d8-108">Ayarlama <xref:System.Windows.Forms.Control.Width%2A> ilk düğmenin **200**.</span><span class="sxs-lookup"><span data-stu-id="8e5d8-108">Set the <xref:System.Windows.Forms.Control.Width%2A> of the first button to **200**.</span></span>  
  
5.  <span data-ttu-id="8e5d8-109">Ayarlama <xref:System.Windows.Forms.Control.Dock%2A> özelliği ikinci düğmenin <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="8e5d8-109">Set the <xref:System.Windows.Forms.Control.Dock%2A> property of the second button to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8e5d8-110">İlk düğmeyi aynı genişlikte ikinci düğme varsayar.</span><span class="sxs-lookup"><span data-stu-id="8e5d8-110">The second button assumes the same width as the first button.</span></span> <span data-ttu-id="8e5d8-111">Genişliği boyunca genişlemez <xref:System.Windows.Forms.FlowLayoutPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="8e5d8-111">It does not stretch across the width of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
6.  <span data-ttu-id="8e5d8-112">Ayarlama <xref:System.Windows.Forms.Control.Dock%2A> özelliği ikinci düğmenin `None`.</span><span class="sxs-lookup"><span data-stu-id="8e5d8-112">Set the <xref:System.Windows.Forms.Control.Dock%2A> property of the second button to `None`.</span></span> <span data-ttu-id="8e5d8-113">Bu, özgün genişliği varsaymak düğme neden olur.</span><span class="sxs-lookup"><span data-stu-id="8e5d8-113">This causes the button to assume its original width.</span></span>  
  
7.  <span data-ttu-id="8e5d8-114">Ayarlama <xref:System.Windows.Forms.Control.Anchor%2A> özelliği ikinci düğmenin `Left, Right`.</span><span class="sxs-lookup"><span data-stu-id="8e5d8-114">Set the <xref:System.Windows.Forms.Control.Anchor%2A> property of the second button to `Left, Right`.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="8e5d8-115">İlk düğmeyi aynı genişlikte ikinci düğme varsayar.</span><span class="sxs-lookup"><span data-stu-id="8e5d8-115">The second button assumes the same width as the first button.</span></span> <span data-ttu-id="8e5d8-116">Genişliği boyunca genişlemez <xref:System.Windows.Forms.FlowLayoutPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="8e5d8-116">It does not stretch across the width of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span> <span data-ttu-id="8e5d8-117">Sabitleme ve yerleştirme içinde için genel bir kural budur <xref:System.Windows.Forms.FlowLayoutPanel> denetimi: dikey akış yönergeleri için <xref:System.Windows.Forms.FlowLayoutPanel> denetim geniş bir alt denetimin sütunda bir örtük sütun genişliğini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="8e5d8-117">This is the general rule for anchoring and docking in the <xref:System.Windows.Forms.FlowLayoutPanel> control: for vertical flow directions, the <xref:System.Windows.Forms.FlowLayoutPanel> control calculates the width of an implied column from the widest child control in the column.</span></span> <span data-ttu-id="8e5d8-118">Tüm bu sütunla denetimlerinde <xref:System.Windows.Forms.Control.Anchor%2A> veya <xref:System.Windows.Forms.Control.Dock%2A> hizalı ya da örtük bu sütunu sığdırmak için uzatılmış özellikleri.</span><span class="sxs-lookup"><span data-stu-id="8e5d8-118">All other controls in this column with <xref:System.Windows.Forms.Control.Anchor%2A> or <xref:System.Windows.Forms.Control.Dock%2A> properties are aligned or stretched to fit this implied column.</span></span> <span data-ttu-id="8e5d8-119">Davranış yatay akış yönleri için benzer bir şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="8e5d8-119">The behavior works in a similar way for horizontal flow directions.</span></span> <span data-ttu-id="8e5d8-120"><xref:System.Windows.Forms.FlowLayoutPanel> Denetim satırdaki en uzun alt denetiminden örtük bir satırın yüksekliğini hesaplar ve bu satırdaki tüm yerleşik veya bağlantılı alt denetimler hizalı veya zımni satırın sığması için boyutu.</span><span class="sxs-lookup"><span data-stu-id="8e5d8-120">The <xref:System.Windows.Forms.FlowLayoutPanel> control calculates the height of an implied row from the tallest child control in the row, and all docked or anchored child controls in this row are aligned or sized to fit the implied row.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e5d8-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e5d8-121">Example</span></span>  
 <span data-ttu-id="8e5d8-122">Bağlantılı ve göreli mavi bir düğme yerleştirilmiş dört düğme aşağıdaki çizimde bir <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="8e5d8-122">The following illustration shows four buttons that are anchored and docked relative to the blue button in a <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="8e5d8-123"><xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> Olduğu <xref:System.Windows.Forms.FlowDirection.LeftToRight>.</span><span class="sxs-lookup"><span data-stu-id="8e5d8-123">The <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> is <xref:System.Windows.Forms.FlowDirection.LeftToRight>.</span></span>  
  
 <span data-ttu-id="8e5d8-124">![FlowLayoutPanel bağlama](../../../../docs/framework/winforms/controls/media/net-flpanchorexp.gif "NET_FLPanchorExp")</span><span class="sxs-lookup"><span data-stu-id="8e5d8-124">![FlowLayoutPanel anchoring](../../../../docs/framework/winforms/controls/media/net-flpanchorexp.gif "NET_FLPanchorExp")</span></span>  
  
 <span data-ttu-id="8e5d8-125">Bağlantılı ve göreli mavi bir düğme yerleştirilmiş dört düğme aşağıdaki çizimde bir <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="8e5d8-125">The following illustration shows four buttons that are anchored and docked relative to the blue button in a <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="8e5d8-126"><xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> Olduğu <xref:System.Windows.Forms.FlowDirection.TopDown>.</span><span class="sxs-lookup"><span data-stu-id="8e5d8-126">The <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> is <xref:System.Windows.Forms.FlowDirection.TopDown>.</span></span>  
  
 <span data-ttu-id="8e5d8-127">![FlowLayoutPanel bağlama](../../../../docs/framework/winforms/controls/media/vs-flpanchor2.gif "VS_FLPanchor2")</span><span class="sxs-lookup"><span data-stu-id="8e5d8-127">![FlowLayoutPanel anchoring](../../../../docs/framework/winforms/controls/media/vs-flpanchor2.gif "VS_FLPanchor2")</span></span>  
  
 <span data-ttu-id="8e5d8-128">Aşağıdaki kod örneği, çeşitli gösterir <xref:System.Windows.Forms.Control.Anchor%2A> özellik değerleri için bir <xref:System.Windows.Forms.Button> denetimine bir <xref:System.Windows.Forms.FlowLayoutPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="8e5d8-128">The following code example demonstrates various <xref:System.Windows.Forms.Control.Anchor%2A> property values for a <xref:System.Windows.Forms.Button> control in a <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/CS/FlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/VB/FlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8e5d8-129">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="8e5d8-129">Compiling the Code</span></span>  
 <span data-ttu-id="8e5d8-130">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="8e5d8-130">This example requires:</span></span>  
  
-   <span data-ttu-id="8e5d8-131">Sistem, System.Data System.Drawing ve System.Windows.Forms derlemelere başvuruları.</span><span class="sxs-lookup"><span data-stu-id="8e5d8-131">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="8e5d8-132">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="8e5d8-132">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="8e5d8-133">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8e5d8-133">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e5d8-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e5d8-134">See also</span></span>
- <xref:System.Windows.Forms.FlowLayoutPanel>
- [<span data-ttu-id="8e5d8-135">FlowLayoutPanel Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8e5d8-135">FlowLayoutPanel Control Overview</span></span>](../../../../docs/framework/winforms/controls/flowlayoutpanel-control-overview.md)
