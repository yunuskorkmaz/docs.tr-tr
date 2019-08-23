---
title: 'Nasıl yapılır: FlowLayoutPanel Denetiminde Alt Denetimleri Sabitleme ve Yerleştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- layout [Windows Forms], child controls
- FlowLayoutPanel control [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
ms.assetid: a2bcdfca-9b63-45e6-9c0e-3411015cba98
ms.openlocfilehash: 9a00fcd53211dd126c0e9203d6d577959b971e70
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922916"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a><span data-ttu-id="5e780-102">Nasıl yapılır: FlowLayoutPanel Denetiminde Alt Denetimleri Sabitleme ve Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="5e780-102">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>
<span data-ttu-id="5e780-103">Denetim, <xref:System.Windows.Forms.Control.Anchor%2A> alt denetimlerinde ve <xref:System.Windows.Forms.Control.Dock%2A> özelliklerini destekler. <xref:System.Windows.Forms.FlowLayoutPanel></span><span class="sxs-lookup"><span data-stu-id="5e780-103">The <xref:System.Windows.Forms.FlowLayoutPanel> control supports the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties in its child controls.</span></span>  
  
### <a name="to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a><span data-ttu-id="5e780-104">FlowLayoutPanel denetiminde alt denetimleri bağlamak ve yerleştirmek için</span><span class="sxs-lookup"><span data-stu-id="5e780-104">To anchor and dock child controls in a FlowLayoutPanel control</span></span>  
  
1. <span data-ttu-id="5e780-105">Formunuzda bir <xref:System.Windows.Forms.FlowLayoutPanel> denetim oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5e780-105">Create a <xref:System.Windows.Forms.FlowLayoutPanel> control on your form.</span></span>  
  
2. <span data-ttu-id="5e780-106"><xref:System.Windows.Forms.FlowDirection.TopDown> <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> Denetimin değerini 300 olarak ayarlayın ve öğesini olarak ayarlayın. <xref:System.Windows.Forms.Control.Width%2A> <xref:System.Windows.Forms.FlowLayoutPanel></span><span class="sxs-lookup"><span data-stu-id="5e780-106">Set the <xref:System.Windows.Forms.Control.Width%2A> of the <xref:System.Windows.Forms.FlowLayoutPanel> control to **300**, and set its <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> to <xref:System.Windows.Forms.FlowDirection.TopDown>.</span></span>  
  
3. <span data-ttu-id="5e780-107">İki <xref:System.Windows.Forms.Button> denetim oluşturun ve bunları <xref:System.Windows.Forms.FlowLayoutPanel> denetime yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="5e780-107">Create two <xref:System.Windows.Forms.Button> controls, and place them in the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
4. <span data-ttu-id="5e780-108">İlk düğmenin öğesini 200 olarak ayarlayın. <xref:System.Windows.Forms.Control.Width%2A></span><span class="sxs-lookup"><span data-stu-id="5e780-108">Set the <xref:System.Windows.Forms.Control.Width%2A> of the first button to **200**.</span></span>  
  
5. <span data-ttu-id="5e780-109">İkinci düğmenin <xref:System.Windows.Forms.DockStyle.Fill>özelliğini olarak ayarlayın. <xref:System.Windows.Forms.Control.Dock%2A></span><span class="sxs-lookup"><span data-stu-id="5e780-109">Set the <xref:System.Windows.Forms.Control.Dock%2A> property of the second button to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="5e780-110">İkinci düğme, ilk düğmeyle aynı genişliği varsayar.</span><span class="sxs-lookup"><span data-stu-id="5e780-110">The second button assumes the same width as the first button.</span></span> <span data-ttu-id="5e780-111"><xref:System.Windows.Forms.FlowLayoutPanel> Denetimin genişliğine göre genişlemez.</span><span class="sxs-lookup"><span data-stu-id="5e780-111">It does not stretch across the width of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
6. <span data-ttu-id="5e780-112">İkinci düğmenin `None`özelliğini olarak ayarlayın. <xref:System.Windows.Forms.Control.Dock%2A></span><span class="sxs-lookup"><span data-stu-id="5e780-112">Set the <xref:System.Windows.Forms.Control.Dock%2A> property of the second button to `None`.</span></span> <span data-ttu-id="5e780-113">Bu, düğmenin orijinal genişliğini varsaymasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="5e780-113">This causes the button to assume its original width.</span></span>  
  
7. <span data-ttu-id="5e780-114">İkinci düğmenin `Left, Right`özelliğini olarak ayarlayın. <xref:System.Windows.Forms.Control.Anchor%2A></span><span class="sxs-lookup"><span data-stu-id="5e780-114">Set the <xref:System.Windows.Forms.Control.Anchor%2A> property of the second button to `Left, Right`.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="5e780-115">İkinci düğme, ilk düğmeyle aynı genişliği varsayar.</span><span class="sxs-lookup"><span data-stu-id="5e780-115">The second button assumes the same width as the first button.</span></span> <span data-ttu-id="5e780-116"><xref:System.Windows.Forms.FlowLayoutPanel> Denetimin genişliğine göre genişlemez.</span><span class="sxs-lookup"><span data-stu-id="5e780-116">It does not stretch across the width of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span> <span data-ttu-id="5e780-117">Bu, <xref:System.Windows.Forms.FlowLayoutPanel> denetimdeki sabitleme ve yerleştirme için genel bir kuraldır: Dikey Akış yönleri için <xref:System.Windows.Forms.FlowLayoutPanel> , denetimin kapsanan bir sütunun genişliğini sütunundaki en geniş alt denetimden hesaplar.</span><span class="sxs-lookup"><span data-stu-id="5e780-117">This is the general rule for anchoring and docking in the <xref:System.Windows.Forms.FlowLayoutPanel> control: for vertical flow directions, the <xref:System.Windows.Forms.FlowLayoutPanel> control calculates the width of an implied column from the widest child control in the column.</span></span> <span data-ttu-id="5e780-118">Bu sütunda <xref:System.Windows.Forms.Control.Anchor%2A> veya <xref:System.Windows.Forms.Control.Dock%2A> özelliklerde bulunan diğer tüm denetimler, bu kapsanan sütuna uyacak şekilde hizalanır veya uzatılır.</span><span class="sxs-lookup"><span data-stu-id="5e780-118">All other controls in this column with <xref:System.Windows.Forms.Control.Anchor%2A> or <xref:System.Windows.Forms.Control.Dock%2A> properties are aligned or stretched to fit this implied column.</span></span> <span data-ttu-id="5e780-119">Davranış, yatay akış yönlerine benzer bir şekilde çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="5e780-119">The behavior works in a similar way for horizontal flow directions.</span></span> <span data-ttu-id="5e780-120"><xref:System.Windows.Forms.FlowLayoutPanel> Denetim, satırdaki en uzun alt denetimden kapsanan bir satırın yüksekliğini hesaplar ve bu satırdaki tüm sabitlenmiş veya bağlantılı alt denetimler, kapsanan satıra sığacak şekilde hizalanır veya boyutlandırılır.</span><span class="sxs-lookup"><span data-stu-id="5e780-120">The <xref:System.Windows.Forms.FlowLayoutPanel> control calculates the height of an implied row from the tallest child control in the row, and all docked or anchored child controls in this row are aligned or sized to fit the implied row.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e780-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="5e780-121">Example</span></span>  
 <span data-ttu-id="5e780-122">Aşağıdaki çizimde, içindeki <xref:System.Windows.Forms.FlowLayoutPanel>mavi düğmeye göre sabitlenmiş ve yerleştirilmiş dört düğme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5e780-122">The following illustration shows four buttons that are anchored and docked relative to the blue button in a <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="5e780-123"><xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> . <xref:System.Windows.Forms.FlowDirection.LeftToRight></span><span class="sxs-lookup"><span data-stu-id="5e780-123">The <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> is <xref:System.Windows.Forms.FlowDirection.LeftToRight>.</span></span>  
  
 <span data-ttu-id="5e780-124">![FlowLayoutPanel sabitleme](./media/net-flpanchorexp.gif "NET_FLPanchorExp")</span><span class="sxs-lookup"><span data-stu-id="5e780-124">![FlowLayoutPanel anchoring](./media/net-flpanchorexp.gif "NET_FLPanchorExp")</span></span>  
  
 <span data-ttu-id="5e780-125">Aşağıdaki çizimde, içindeki <xref:System.Windows.Forms.FlowLayoutPanel>mavi düğmeye göre sabitlenmiş ve yerleştirilmiş dört düğme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5e780-125">The following illustration shows four buttons that are anchored and docked relative to the blue button in a <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="5e780-126"><xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> . <xref:System.Windows.Forms.FlowDirection.TopDown></span><span class="sxs-lookup"><span data-stu-id="5e780-126">The <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> is <xref:System.Windows.Forms.FlowDirection.TopDown>.</span></span>  
  
 <span data-ttu-id="5e780-127">![FlowLayoutPanel sabitleme](./media/vs-flpanchor2.gif "VS_FLPanchor2")</span><span class="sxs-lookup"><span data-stu-id="5e780-127">![FlowLayoutPanel anchoring](./media/vs-flpanchor2.gif "VS_FLPanchor2")</span></span>  
  
 <span data-ttu-id="5e780-128">Aşağıdaki kod örneği, bir <xref:System.Windows.Forms.Control.Anchor%2A> <xref:System.Windows.Forms.FlowLayoutPanel> denetimdeki <xref:System.Windows.Forms.Button> denetim için çeşitli özellik değerlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5e780-128">The following code example demonstrates various <xref:System.Windows.Forms.Control.Anchor%2A> property values for a <xref:System.Windows.Forms.Button> control in a <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/CS/FlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/VB/FlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5e780-129">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="5e780-129">Compiling the Code</span></span>  
 <span data-ttu-id="5e780-130">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="5e780-130">This example requires:</span></span>  
  
- <span data-ttu-id="5e780-131">System, System. Data, System. Drawing ve System. Windows. Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="5e780-131">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e780-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e780-132">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel>
- [<span data-ttu-id="5e780-133">FlowLayoutPanel Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5e780-133">FlowLayoutPanel Control Overview</span></span>](flowlayoutpanel-control-overview.md)
