---
title: HScrollBar ve VScrollBar Denetimlerine Genel Bakış (Windows Forms)
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
ms.openlocfilehash: 2c6436e77753322733580acba5a20d6bb220f29c
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43880123"
---
# <a name="hscrollbar-and-vscrollbar-controls-overview-windows-forms"></a>HScrollBar ve VScrollBar Denetimlerine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ScrollBar> denetimleri yatay kaydırma tarafından veya içinde bir uygulamanın veya denetimin dikey olarak uzun bir liste aracılığıyla kolay gezinti öğeleri veya büyük miktarda bilgi sağlamak amacıyla kullanılır. Kaydırma çubukları Windows arabiriminin ortak bir öğesi olan böylece <xref:System.Windows.Forms.ScrollBar> öğesinden türetilen değil denetimlerle genellikle Denetim kullanılır <xref:System.Windows.Forms.ScrollableControl> sınıfı. Benzer şekilde, dahil etmek birçok geliştiricinin seçin <xref:System.Windows.Forms.ScrollBar> denetlemek, kendi kullanıcı denetimleri yazma.  
  
 <xref:System.Windows.Forms.HScrollBar> (Yatay) ve <xref:System.Windows.Forms.VScrollBar> (dikey) denetimleri diğer denetimleri birbirinden bağımsız olarak çalışır ve kendi olayları, özellikler ve yöntemler vardır. <xref:System.Windows.Forms.ScrollBar> denetimleri metin kutuları, liste kutuları, birleşik giriş kutuları veya MDI formları bağlı yerleşik kaydırma çubuklarının ile aynı değildir ( <xref:System.Windows.Forms.TextBox> kontrolünde bir <xref:System.Windows.Forms.TextBox.ScrollBars%2A> denetime eklidir kaydırma çubuklarını gösterme veya gizleme özelliğini).  
  
 <xref:System.Windows.Forms.ScrollBar> Denetimleri kullanın <xref:System.Windows.Forms.ScrollBar.Scroll> kaydırma çubuğu (bazen thumb adlandırılır) kaydırma kutusunun hareketini izlemek için olay. Kullanarak <xref:System.Windows.Forms.ScrollBar.Scroll> olay sürüklenen gibi kaydırma çubuğu değeri erişim sağlar.  
  
## <a name="value-property"></a>Value özelliği  
 <xref:System.Windows.Forms.ScrollBar.Value%2A> (Bu, varsayılan olarak, 0) özelliği bir `integer` kaydırma çubuğuna ait kaydırma kutusunun konumuna karşılık gelen bir değer. Kaydırma kutusunun konumundaki en düşük değer olduğunda, en soldaki konumu (yatay kaydırma çubuklarını) ya da (dikey kaydırma çubukları için) en üst konuma taşır. Kaydırma kutusuna en yüksek değer, en sağdaki kaydırma kutusuna taşınır veya alt konumunu olduğunda. Benzer şekilde, yarısı alt ve üst aralık arasında bir değer lider ortasında kaydırma çubuğuna ait kaydırma kutusunun yerleştirir.  
  
 Fare tıklama kaydırma çubuğu değeri değiştirmek için kullanmanın yanı sıra, bir kullanıcı kaydırma kutusunun çubuk boyunca herhangi bir noktaya sürükleyebilirsiniz. Sonuç değerini kaydırma kutusunun konumuna bağlıdır, ancak her zaman aralığında ise <xref:System.Windows.Forms.ScrollBar.Minimum%2A> için <xref:System.Windows.Forms.ScrollBar.Maximum%2A> kullanıcı tarafından ayarlanan özellikler.  
  
## <a name="largechange-and-smallchange-properties"></a>LargeChange ve SmallChange özellikleri  
 Kullanıcı PAGE UP veya PAGE DOWN tuşuna bastığında veya her iki tarafında, kaydırma kutusunun kaydırma çubuğu parça içinde tıkladığında <xref:System.Windows.Forms.ScrollBar.Value%2A> içinde ayarlanan değere göre özellik değişiklikleri <xref:System.Windows.Forms.ScrollBar.LargeChange%2A> özelliği.  
  
 Kullanıcı oka birini bastığında anahtarları veya kaydırma çubuğu düğmelerden birine tıklar <xref:System.Windows.Forms.ScrollBar.Value%2A> içinde ayarlanan değere göre özellik değişiklikleri <xref:System.Windows.Forms.ScrollBar.SmallChange%2A> özelliği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.HScrollBar>  
 <xref:System.Windows.Forms.VScrollBar>  
 [.NET Framework 2.0 Windows Forms'a eklemeler](https://msdn.microsoft.com/library/c61a923d-3d6a-4c8c-820c-e94c83f3f9a8)  
 [Windows Forms'da Kullanılacak Denetimler](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
