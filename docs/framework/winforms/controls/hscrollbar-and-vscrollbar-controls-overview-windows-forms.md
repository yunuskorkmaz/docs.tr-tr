---
title: HScrollBar ve VScrollBar Denetimlerine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- HScrollBar
- VScrollBar
helpviewer_keywords:
- ScrollBar control [Windows Forms]
- HScrollBar control [Windows Forms], about HScrollBar
- VScrollBar control [Windows Forms], about VScrollBar control
- ScrollBar control [Windows Forms], about ScrollBar control
- scroll bars [Windows Forms], about scroll bars
ms.assetid: 8b307679-1cae-41d8-99aa-3d1efd207cd6
ms.openlocfilehash: abe0c8da9723f17cb80715454f6ab7297724a21f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728166"
---
# <a name="hscrollbar-and-vscrollbar-controls-overview-windows-forms"></a>HScrollBar ve VScrollBar Denetimlerine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ScrollBar> denetimleri, bir uygulama veya denetim içinde yatay veya dikey olarak gezinerek uzun bir öğe listesi veya büyük miktarda bilgi için kolay gezinti sağlamak üzere kullanılır. Kaydırma çubukları Windows arabiriminin ortak bir öğesidir, bu nedenle <xref:System.Windows.Forms.ScrollBar> denetimi genellikle <xref:System.Windows.Forms.ScrollableControl> sınıfından türemeyen denetimlerle kullanılır. Benzer şekilde birçok geliştirici, kendi kullanıcı denetimlerini yazarken <xref:System.Windows.Forms.ScrollBar> denetimini de eklemenizi seçer.  
  
 <xref:System.Windows.Forms.HScrollBar> (yatay) ve <xref:System.Windows.Forms.VScrollBar> (dikey) denetimleri, diğer denetimlerden bağımsız olarak çalışır ve kendi olay, özellik ve Yöntem kümesine sahip olabilir. <xref:System.Windows.Forms.ScrollBar> denetimleri, metin kutularına, liste kutularına, Birleşik giriş kutularına veya MDI formlarına eklenen yerleşik kaydırma çubuklarıyla aynı değildir (<xref:System.Windows.Forms.TextBox> denetim, denetime eklenmiş olan kaydırma çubuklarını göstermek veya gizlemek için bir <xref:System.Windows.Forms.TextBox.ScrollBars%2A> özelliğine sahiptir).  
  
 <xref:System.Windows.Forms.ScrollBar> denetimleri kaydırma çubuğunun yanı da kaydırma kutusunun hareketini (bazen Thumb olarak adlandırılır) izlemek için <xref:System.Windows.Forms.ScrollBar.Scroll> olayını kullanır. <xref:System.Windows.Forms.ScrollBar.Scroll> olayının kullanılması kaydırma çubuğu değerine sürüklenirken erişim sağlar.  
  
## <a name="value-property"></a>Value özelliği  
 <xref:System.Windows.Forms.ScrollBar.Value%2A> özelliği (varsayılan olarak, 0 ' dır), kaydırma çubuğundaki kaydırma kutusunun konumuna karşılık gelen bir `integer` değeridir. Kaydırma kutusu konumu en düşük değerde olduğunda, en sol konuma (yatay kaydırma çubukları için) veya üst konuma (dikey kaydırma çubukları için) gider. Kaydırma kutusu en büyük değerde olduğunda, kaydırma kutusu en sağ veya alt konuma gider. Benzer şekilde, aralığın alt ve üst sınırı arasındaki bir değer, kaydırma çubuğunun ortasındaki kaydırma kutusunun baştaki ucunu koyar.  
  
 Kullanıcı kaydırma çubuğu değerini değiştirmek için fare tıklamalarının kullanılmasına ek olarak, kaydırma kutusunu da çubuk üzerinde herhangi bir noktaya sürükleyebilirsiniz. Elde edilen değer, kaydırma kutusunun konumuna bağlıdır, ancak her zaman <xref:System.Windows.Forms.ScrollBar.Minimum%2A> aralığı içinde Kullanıcı tarafından ayarlanan <xref:System.Windows.Forms.ScrollBar.Maximum%2A> özelliklere sahiptir.  
  
## <a name="largechange-and-smallchange-properties"></a>LargeChange ve SmallChange özellikleri  
 Kullanıcı sayfa yukarı veya sayfa aşağı tuşuna bastığında veya kaydırma kutusunun her iki tarafında da kaydırma çubuğu kanalında tıkladığı zaman, <xref:System.Windows.Forms.ScrollBar.Value%2A> özelliği <xref:System.Windows.Forms.ScrollBar.LargeChange%2A> özelliğinde ayarlanan değere göre değişir.  
  
 Kullanıcı, ok tuşlarından birine bastığında veya kaydırma çubuğu düğmelerinden birine tıkladığında, <xref:System.Windows.Forms.ScrollBar.Value%2A> özelliği <xref:System.Windows.Forms.ScrollBar.SmallChange%2A> özelliğinde ayarlanan değere göre değişir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.HScrollBar>
- <xref:System.Windows.Forms.VScrollBar>
- [Windows Forms'da Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)
