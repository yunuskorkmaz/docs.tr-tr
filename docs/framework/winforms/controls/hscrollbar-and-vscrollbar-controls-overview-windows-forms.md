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
ms.openlocfilehash: 572ba9f16d1c78e1825d0c9db7530c6c78175d27
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="hscrollbar-and-vscrollbar-controls-overview-windows-forms"></a>HScrollBar ve VScrollBar Denetimlerine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ScrollBar> denetimleri kaydırarak ya da yatay veya dikey olarak bir uygulama veya denetim içinde uzun bir listesi ile kolay gezinme öğeleri veya büyük miktarda bilgi sağlamak için kullanılır. Kaydırma çubukları Windows arabiriminin ortak bir öğesi olan böylece <xref:System.Windows.Forms.ScrollBar> denetim öğesinden türetilen değil denetimleri ile kullanılan genellikle <xref:System.Windows.Forms.ScrollableControl> sınıfı. Benzer şekilde, içerecek şekilde Çoğu geliştirici seçin <xref:System.Windows.Forms.ScrollBar> denetim kendi kullanıcı denetimleri yazarken.  
  
 <xref:System.Windows.Forms.HScrollBar> (Yatay) ve <xref:System.Windows.Forms.VScrollBar> (dikey) denetimleri diğer denetimlerden bağımsız olarak çalışır ve olaylar, özellikleri ve yöntemleri kendi kümesine sahip. <xref:System.Windows.Forms.ScrollBar> denetimleri metin kutuları, liste kutuları, birleşik giriş kutuları veya MDI formları bağlı yerleşik kaydırma çubukları ile aynı değildir ( <xref:System.Windows.Forms.TextBox> denetimi sahip bir <xref:System.Windows.Forms.TextBox.ScrollBars%2A> özelliğini denetime bağlı kaydırma çubuklarını gösterme veya gizleme).  
  
 <xref:System.Windows.Forms.ScrollBar> Denetimleri kullanın <xref:System.Windows.Forms.ScrollBar.Scroll> kaydırma çubuğu taşıma (bazen Flash adlandırılır) kaydırma kutusunun izlemek için olay. Kullanarak <xref:System.Windows.Forms.ScrollBar.Scroll> olay sürüklenen gibi kaydırma çubuğu değeri erişim sağlar.  
  
## <a name="value-property"></a>Value özelliği  
 <xref:System.Windows.Forms.ScrollBar.Value%2A> (Bu, varsayılan olarak, 0) özelliği bir `integer` kaydırma çubuğuna ait kaydırma kutusunun konumuna karşılık gelen değer. Kaydırma kutusunun konumundaki en düşük değer olduğunda (için yatay kaydırma çubuklarını) en solundaki konumu ya da üst konumunu (dikey kaydırma çubukları) taşır. Kaydırma kutusu en büyük değer, en sağdaki kaydırma kutusuna taşınır veya alt konumunu olduğunda. Benzer şekilde, bir değer aralığın üst ve alt arasında yarısı ortasında kaydırma çubuğunun Kaydırma kutusu başında köşesine yerleştirir.  
  
 Kaydırma çubuğu değerini değiştirmek için fare tıklamaları kullanarak ek olarak, bir kullanıcı Kaydırma kutusu çubuğu boyunca herhangi bir noktaya sürükleyebilirsiniz. Sonuç değeri kaydırma kutusunun konumuna bağlıdır, ancak bu her zaman aralığı içinde <xref:System.Windows.Forms.ScrollBar.Minimum%2A> için <xref:System.Windows.Forms.ScrollBar.Maximum%2A> kullanıcı tarafından ayarlanan özellikleri.  
  
## <a name="largechange-and-smallchange-properties"></a>LargeChange ve SmallChange özellikleri  
 Kullanıcı PAGE UP veya PAGE DOWN tuşuna bastığında veya her iki yanına kaydırma kutusunun kaydırma çubuğu izlemede içinde tıklattığında <xref:System.Windows.Forms.ScrollBar.Value%2A> içinde ayarlanan değere göre özelliği değişiklikler <xref:System.Windows.Forms.ScrollBar.LargeChange%2A> özelliği.  
  
 Kullanıcı oku birini bastığında anahtarları veya kaydırma çubuğu düğmelerinin birini tıklattığında <xref:System.Windows.Forms.ScrollBar.Value%2A> içinde ayarlanan değere göre özelliği değişiklikler <xref:System.Windows.Forms.ScrollBar.SmallChange%2A> özelliği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.HScrollBar>  
 <xref:System.Windows.Forms.VScrollBar>  
 [.NET Framework 2.0 için Windows Forms'a ekleme](http://msdn.microsoft.com/library/c61a923d-3d6a-4c8c-820c-e94c83f3f9a8)  
 [Windows Forms'da Kullanılacak Denetimler](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
