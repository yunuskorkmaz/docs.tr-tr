---
title: 'Nasıl yapılır: FlowLayoutPanel Denetiminde Alt Denetimleri Sabitleme ve Yerleştirme'
description: Windows Forms FlowLayoutPanel denetiminde alt denetimleri program aracılığıyla yerleştirmeyi ve yerleştirmeyi öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- layout [Windows Forms], child controls
- FlowLayoutPanel control [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
ms.assetid: a2bcdfca-9b63-45e6-9c0e-3411015cba98
ms.openlocfilehash: b4fb3bf6d148a526a75926bd67c1f967286332bf
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174542"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a><span data-ttu-id="6c60d-103">Nasıl yapılır: FlowLayoutPanel Denetiminde Alt Denetimleri Sabitleme ve Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="6c60d-103">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>

<span data-ttu-id="6c60d-104"><xref:System.Windows.Forms.FlowLayoutPanel>Denetim, <xref:System.Windows.Forms.Control.Anchor%2A> <xref:System.Windows.Forms.Control.Dock%2A> alt denetimlerinde ve özelliklerini destekler.</span><span class="sxs-lookup"><span data-stu-id="6c60d-104">The <xref:System.Windows.Forms.FlowLayoutPanel> control supports the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties in its child controls.</span></span>

### <a name="to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a><span data-ttu-id="6c60d-105">FlowLayoutPanel denetiminde alt denetimleri bağlamak ve yerleştirmek için</span><span class="sxs-lookup"><span data-stu-id="6c60d-105">To anchor and dock child controls in a FlowLayoutPanel control</span></span>

1. <span data-ttu-id="6c60d-106">Formunuzda bir <xref:System.Windows.Forms.FlowLayoutPanel> denetim oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6c60d-106">Create a <xref:System.Windows.Forms.FlowLayoutPanel> control on your form.</span></span>

2. <span data-ttu-id="6c60d-107"><xref:System.Windows.Forms.Control.Width%2A>Denetimin değerini 300 olarak ayarlayın <xref:System.Windows.Forms.FlowLayoutPanel> ve **300**öğesini <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> olarak ayarlayın <xref:System.Windows.Forms.FlowDirection.TopDown> .</span><span class="sxs-lookup"><span data-stu-id="6c60d-107">Set the <xref:System.Windows.Forms.Control.Width%2A> of the <xref:System.Windows.Forms.FlowLayoutPanel> control to **300**, and set its <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> to <xref:System.Windows.Forms.FlowDirection.TopDown>.</span></span>

3. <span data-ttu-id="6c60d-108">İki <xref:System.Windows.Forms.Button> denetim oluşturun ve bunları <xref:System.Windows.Forms.FlowLayoutPanel> denetime yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="6c60d-108">Create two <xref:System.Windows.Forms.Button> controls, and place them in the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

4. <span data-ttu-id="6c60d-109"><xref:System.Windows.Forms.Control.Width%2A>İlk düğmenin öğesini **200**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6c60d-109">Set the <xref:System.Windows.Forms.Control.Width%2A> of the first button to **200**.</span></span>

5. <span data-ttu-id="6c60d-110"><xref:System.Windows.Forms.Control.Dock%2A>İkinci düğmenin özelliğini olarak ayarlayın <xref:System.Windows.Forms.DockStyle.Fill> .</span><span class="sxs-lookup"><span data-stu-id="6c60d-110">Set the <xref:System.Windows.Forms.Control.Dock%2A> property of the second button to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6c60d-111">İkinci düğme, ilk düğmeyle aynı genişliği varsayar.</span><span class="sxs-lookup"><span data-stu-id="6c60d-111">The second button assumes the same width as the first button.</span></span> <span data-ttu-id="6c60d-112">Denetimin genişliğine göre genişlemez <xref:System.Windows.Forms.FlowLayoutPanel> .</span><span class="sxs-lookup"><span data-stu-id="6c60d-112">It does not stretch across the width of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

6. <span data-ttu-id="6c60d-113"><xref:System.Windows.Forms.Control.Dock%2A>İkinci düğmenin özelliğini olarak ayarlayın `None` .</span><span class="sxs-lookup"><span data-stu-id="6c60d-113">Set the <xref:System.Windows.Forms.Control.Dock%2A> property of the second button to `None`.</span></span> <span data-ttu-id="6c60d-114">Bu, düğmenin orijinal genişliğini varsaymasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="6c60d-114">This causes the button to assume its original width.</span></span>

7. <span data-ttu-id="6c60d-115"><xref:System.Windows.Forms.Control.Anchor%2A>İkinci düğmenin özelliğini olarak ayarlayın `Left, Right` .</span><span class="sxs-lookup"><span data-stu-id="6c60d-115">Set the <xref:System.Windows.Forms.Control.Anchor%2A> property of the second button to `Left, Right`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="6c60d-116">İkinci düğme, ilk düğmeyle aynı genişliği varsayar.</span><span class="sxs-lookup"><span data-stu-id="6c60d-116">The second button assumes the same width as the first button.</span></span> <span data-ttu-id="6c60d-117">Denetimin genişliğine göre genişlemez <xref:System.Windows.Forms.FlowLayoutPanel> .</span><span class="sxs-lookup"><span data-stu-id="6c60d-117">It does not stretch across the width of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span> <span data-ttu-id="6c60d-118">Bu, denetimdeki sabitleme ve yerleştirme için genel bir kuraldır <xref:System.Windows.Forms.FlowLayoutPanel> : Dikey Akış yönleri için, <xref:System.Windows.Forms.FlowLayoutPanel> denetimin kapsanan bir sütunun genişliğini sütunundaki en geniş alt denetimden hesaplar.</span><span class="sxs-lookup"><span data-stu-id="6c60d-118">This is the general rule for anchoring and docking in the <xref:System.Windows.Forms.FlowLayoutPanel> control: for vertical flow directions, the <xref:System.Windows.Forms.FlowLayoutPanel> control calculates the width of an implied column from the widest child control in the column.</span></span> <span data-ttu-id="6c60d-119">Bu sütunda veya özelliklerde bulunan diğer tüm <xref:System.Windows.Forms.Control.Anchor%2A> denetimler <xref:System.Windows.Forms.Control.Dock%2A> , bu kapsanan sütuna uyacak şekilde hizalanır veya uzatılır.</span><span class="sxs-lookup"><span data-stu-id="6c60d-119">All other controls in this column with <xref:System.Windows.Forms.Control.Anchor%2A> or <xref:System.Windows.Forms.Control.Dock%2A> properties are aligned or stretched to fit this implied column.</span></span> <span data-ttu-id="6c60d-120">Davranış, yatay akış yönlerine benzer bir şekilde çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="6c60d-120">The behavior works in a similar way for horizontal flow directions.</span></span> <span data-ttu-id="6c60d-121"><xref:System.Windows.Forms.FlowLayoutPanel>Denetim, satırdaki en uzun alt denetimden kapsanan bir satırın yüksekliğini hesaplar ve bu satırdaki tüm sabitlenmiş veya bağlantılı alt denetimler, kapsanan satıra sığacak şekilde hizalanır veya boyutlandırılır.</span><span class="sxs-lookup"><span data-stu-id="6c60d-121">The <xref:System.Windows.Forms.FlowLayoutPanel> control calculates the height of an implied row from the tallest child control in the row, and all docked or anchored child controls in this row are aligned or sized to fit the implied row.</span></span>

## <a name="example"></a><span data-ttu-id="6c60d-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="6c60d-122">Example</span></span>

<span data-ttu-id="6c60d-123">Aşağıdaki çizimde, içindeki mavi düğmeye göre sabitlenmiş ve yerleştirilmiş dört düğme gösterilmektedir <xref:System.Windows.Forms.FlowLayoutPanel> .</span><span class="sxs-lookup"><span data-stu-id="6c60d-123">The following illustration shows four buttons that are anchored and docked relative to the blue button in a <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="6c60d-124"><xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> <xref:System.Windows.Forms.FlowDirection.LeftToRight> .</span><span class="sxs-lookup"><span data-stu-id="6c60d-124">The <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> is <xref:System.Windows.Forms.FlowDirection.LeftToRight>.</span></span>

<span data-ttu-id="6c60d-125">![FlowLayoutPanel sabitleme](./media/net-flpanchorexp.gif "NET_FLPanchorExp")</span><span class="sxs-lookup"><span data-stu-id="6c60d-125">![FlowLayoutPanel anchoring](./media/net-flpanchorexp.gif "NET_FLPanchorExp")</span></span>

<span data-ttu-id="6c60d-126">Aşağıdaki çizimde, içindeki mavi düğmeye göre sabitlenmiş ve yerleştirilmiş dört düğme gösterilmektedir <xref:System.Windows.Forms.FlowLayoutPanel> .</span><span class="sxs-lookup"><span data-stu-id="6c60d-126">The following illustration shows four buttons that are anchored and docked relative to the blue button in a <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="6c60d-127"><xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> <xref:System.Windows.Forms.FlowDirection.TopDown> .</span><span class="sxs-lookup"><span data-stu-id="6c60d-127">The <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> is <xref:System.Windows.Forms.FlowDirection.TopDown>.</span></span>

<span data-ttu-id="6c60d-128">![FlowLayoutPanel sabitleme](./media/vs-flpanchor2.gif "VS_FLPanchor2")</span><span class="sxs-lookup"><span data-stu-id="6c60d-128">![FlowLayoutPanel anchoring](./media/vs-flpanchor2.gif "VS_FLPanchor2")</span></span>

<span data-ttu-id="6c60d-129">Aşağıdaki kod örneği, <xref:System.Windows.Forms.Control.Anchor%2A> bir denetimdeki denetim için çeşitli özellik değerlerini gösterir <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.FlowLayoutPanel> .</span><span class="sxs-lookup"><span data-stu-id="6c60d-129">The following code example demonstrates various <xref:System.Windows.Forms.Control.Anchor%2A> property values for a <xref:System.Windows.Forms.Button> control in a <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

[!code-csharp[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/CS/FlpAnchorExampleForm.cs#1)]
[!code-vb[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/VB/FlpAnchorExampleForm.vb#1)]

## <a name="compiling-the-code"></a><span data-ttu-id="6c60d-130">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="6c60d-130">Compiling the Code</span></span>

<span data-ttu-id="6c60d-131">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="6c60d-131">This example requires:</span></span>

- <span data-ttu-id="6c60d-132">System, System. Data, System. Drawing ve System. Windows. Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="6c60d-132">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="6c60d-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c60d-133">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel>
- [<span data-ttu-id="6c60d-134">FlowLayoutPanel Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6c60d-134">FlowLayoutPanel Control Overview</span></span>](flowlayoutpanel-control-overview.md)
