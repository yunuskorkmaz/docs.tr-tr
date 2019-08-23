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
# <a name="how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a>Nasıl yapılır: FlowLayoutPanel Denetiminde Alt Denetimleri Sabitleme ve Yerleştirme
Denetim, <xref:System.Windows.Forms.Control.Anchor%2A> alt denetimlerinde ve <xref:System.Windows.Forms.Control.Dock%2A> özelliklerini destekler. <xref:System.Windows.Forms.FlowLayoutPanel>  
  
### <a name="to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a>FlowLayoutPanel denetiminde alt denetimleri bağlamak ve yerleştirmek için  
  
1. Formunuzda bir <xref:System.Windows.Forms.FlowLayoutPanel> denetim oluşturun.  
  
2. <xref:System.Windows.Forms.FlowDirection.TopDown> <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> Denetimin değerini 300 olarak ayarlayın ve öğesini olarak ayarlayın. <xref:System.Windows.Forms.Control.Width%2A> <xref:System.Windows.Forms.FlowLayoutPanel>  
  
3. İki <xref:System.Windows.Forms.Button> denetim oluşturun ve bunları <xref:System.Windows.Forms.FlowLayoutPanel> denetime yerleştirin.  
  
4. İlk düğmenin öğesini 200 olarak ayarlayın. <xref:System.Windows.Forms.Control.Width%2A>  
  
5. İkinci düğmenin <xref:System.Windows.Forms.DockStyle.Fill>özelliğini olarak ayarlayın. <xref:System.Windows.Forms.Control.Dock%2A>  
  
    > [!NOTE]
    > İkinci düğme, ilk düğmeyle aynı genişliği varsayar. <xref:System.Windows.Forms.FlowLayoutPanel> Denetimin genişliğine göre genişlemez.  
  
6. İkinci düğmenin `None`özelliğini olarak ayarlayın. <xref:System.Windows.Forms.Control.Dock%2A> Bu, düğmenin orijinal genişliğini varsaymasına neden olur.  
  
7. İkinci düğmenin `Left, Right`özelliğini olarak ayarlayın. <xref:System.Windows.Forms.Control.Anchor%2A>  
  
    > [!IMPORTANT]
    >  İkinci düğme, ilk düğmeyle aynı genişliği varsayar. <xref:System.Windows.Forms.FlowLayoutPanel> Denetimin genişliğine göre genişlemez. Bu, <xref:System.Windows.Forms.FlowLayoutPanel> denetimdeki sabitleme ve yerleştirme için genel bir kuraldır: Dikey Akış yönleri için <xref:System.Windows.Forms.FlowLayoutPanel> , denetimin kapsanan bir sütunun genişliğini sütunundaki en geniş alt denetimden hesaplar. Bu sütunda <xref:System.Windows.Forms.Control.Anchor%2A> veya <xref:System.Windows.Forms.Control.Dock%2A> özelliklerde bulunan diğer tüm denetimler, bu kapsanan sütuna uyacak şekilde hizalanır veya uzatılır. Davranış, yatay akış yönlerine benzer bir şekilde çalışabilir. <xref:System.Windows.Forms.FlowLayoutPanel> Denetim, satırdaki en uzun alt denetimden kapsanan bir satırın yüksekliğini hesaplar ve bu satırdaki tüm sabitlenmiş veya bağlantılı alt denetimler, kapsanan satıra sığacak şekilde hizalanır veya boyutlandırılır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki çizimde, içindeki <xref:System.Windows.Forms.FlowLayoutPanel>mavi düğmeye göre sabitlenmiş ve yerleştirilmiş dört düğme gösterilmektedir. <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> . <xref:System.Windows.Forms.FlowDirection.LeftToRight>  
  
 ![FlowLayoutPanel sabitleme](./media/net-flpanchorexp.gif "NET_FLPanchorExp")  
  
 Aşağıdaki çizimde, içindeki <xref:System.Windows.Forms.FlowLayoutPanel>mavi düğmeye göre sabitlenmiş ve yerleştirilmiş dört düğme gösterilmektedir. <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> . <xref:System.Windows.Forms.FlowDirection.TopDown>  
  
 ![FlowLayoutPanel sabitleme](./media/vs-flpanchor2.gif "VS_FLPanchor2")  
  
 Aşağıdaki kod örneği, bir <xref:System.Windows.Forms.Control.Anchor%2A> <xref:System.Windows.Forms.FlowLayoutPanel> denetimdeki <xref:System.Windows.Forms.Button> denetim için çeşitli özellik değerlerini gösterir.  
  
 [!code-csharp[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/CS/FlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/VB/FlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- System, System. Data, System. Drawing ve System. Windows. Forms derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.FlowLayoutPanel>
- [FlowLayoutPanel Denetimine Genel Bakış](flowlayoutpanel-control-overview.md)
