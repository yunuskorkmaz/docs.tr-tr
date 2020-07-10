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
# <a name="how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a>Nasıl yapılır: FlowLayoutPanel Denetiminde Alt Denetimleri Sabitleme ve Yerleştirme

<xref:System.Windows.Forms.FlowLayoutPanel>Denetim, <xref:System.Windows.Forms.Control.Anchor%2A> <xref:System.Windows.Forms.Control.Dock%2A> alt denetimlerinde ve özelliklerini destekler.

### <a name="to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a>FlowLayoutPanel denetiminde alt denetimleri bağlamak ve yerleştirmek için

1. Formunuzda bir <xref:System.Windows.Forms.FlowLayoutPanel> denetim oluşturun.

2. <xref:System.Windows.Forms.Control.Width%2A>Denetimin değerini 300 olarak ayarlayın <xref:System.Windows.Forms.FlowLayoutPanel> ve **300**öğesini <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> olarak ayarlayın <xref:System.Windows.Forms.FlowDirection.TopDown> .

3. İki <xref:System.Windows.Forms.Button> denetim oluşturun ve bunları <xref:System.Windows.Forms.FlowLayoutPanel> denetime yerleştirin.

4. <xref:System.Windows.Forms.Control.Width%2A>İlk düğmenin öğesini **200**olarak ayarlayın.

5. <xref:System.Windows.Forms.Control.Dock%2A>İkinci düğmenin özelliğini olarak ayarlayın <xref:System.Windows.Forms.DockStyle.Fill> .

    > [!NOTE]
    > İkinci düğme, ilk düğmeyle aynı genişliği varsayar. Denetimin genişliğine göre genişlemez <xref:System.Windows.Forms.FlowLayoutPanel> .

6. <xref:System.Windows.Forms.Control.Dock%2A>İkinci düğmenin özelliğini olarak ayarlayın `None` . Bu, düğmenin orijinal genişliğini varsaymasına neden olur.

7. <xref:System.Windows.Forms.Control.Anchor%2A>İkinci düğmenin özelliğini olarak ayarlayın `Left, Right` .

    > [!IMPORTANT]
    > İkinci düğme, ilk düğmeyle aynı genişliği varsayar. Denetimin genişliğine göre genişlemez <xref:System.Windows.Forms.FlowLayoutPanel> . Bu, denetimdeki sabitleme ve yerleştirme için genel bir kuraldır <xref:System.Windows.Forms.FlowLayoutPanel> : Dikey Akış yönleri için, <xref:System.Windows.Forms.FlowLayoutPanel> denetimin kapsanan bir sütunun genişliğini sütunundaki en geniş alt denetimden hesaplar. Bu sütunda veya özelliklerde bulunan diğer tüm <xref:System.Windows.Forms.Control.Anchor%2A> denetimler <xref:System.Windows.Forms.Control.Dock%2A> , bu kapsanan sütuna uyacak şekilde hizalanır veya uzatılır. Davranış, yatay akış yönlerine benzer bir şekilde çalışabilir. <xref:System.Windows.Forms.FlowLayoutPanel>Denetim, satırdaki en uzun alt denetimden kapsanan bir satırın yüksekliğini hesaplar ve bu satırdaki tüm sabitlenmiş veya bağlantılı alt denetimler, kapsanan satıra sığacak şekilde hizalanır veya boyutlandırılır.

## <a name="example"></a>Örnek

Aşağıdaki çizimde, içindeki mavi düğmeye göre sabitlenmiş ve yerleştirilmiş dört düğme gösterilmektedir <xref:System.Windows.Forms.FlowLayoutPanel> . <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> <xref:System.Windows.Forms.FlowDirection.LeftToRight> .

![FlowLayoutPanel sabitleme](./media/net-flpanchorexp.gif "NET_FLPanchorExp")

Aşağıdaki çizimde, içindeki mavi düğmeye göre sabitlenmiş ve yerleştirilmiş dört düğme gösterilmektedir <xref:System.Windows.Forms.FlowLayoutPanel> . <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> <xref:System.Windows.Forms.FlowDirection.TopDown> .

![FlowLayoutPanel sabitleme](./media/vs-flpanchor2.gif "VS_FLPanchor2")

Aşağıdaki kod örneği, <xref:System.Windows.Forms.Control.Anchor%2A> bir denetimdeki denetim için çeşitli özellik değerlerini gösterir <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.FlowLayoutPanel> .

[!code-csharp[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/CS/FlpAnchorExampleForm.cs#1)]
[!code-vb[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/VB/FlpAnchorExampleForm.vb#1)]

## <a name="compiling-the-code"></a>Kod Derleniyor

Bu örnek şunları gerektirir:

- System, System. Data, System. Drawing ve System. Windows. Forms derlemelerine başvurular.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.FlowLayoutPanel>
- [FlowLayoutPanel Denetimine Genel Bakış](flowlayoutpanel-control-overview.md)
