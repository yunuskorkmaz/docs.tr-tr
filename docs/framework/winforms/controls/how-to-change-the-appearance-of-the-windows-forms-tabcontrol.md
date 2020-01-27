---
title: TabControl görünümünü değiştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- icons [Windows Forms], displaying on tabs
- TabControl control [Windows Forms], changing page appearance
- tabs [Windows Forms], controlling appearance
- buttons [Windows Forms], displaying tabs as
ms.assetid: 7c6cc443-ed62-4d26-b94d-b8913b44f773
ms.openlocfilehash: 056070177e6bbaba0c93c7b94f5adfd7887be6a8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746616"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-tabcontrol"></a>Nasıl yapılır: Windows Forms TabControl'nin Görünüşünü Değiştirme
<xref:System.Windows.Forms.TabControl> özelliklerini ve denetimdeki tek sekmeleri oluşturan <xref:System.Windows.Forms.TabPage> nesnelerini kullanarak Windows Forms sekmelerin görünümünü değiştirebilirsiniz. Bu özellikleri ayarlayarak sekmeleri sekmelerde görüntüleyebilir, yatay olarak sekmeler üzerinde dikey olarak görüntüleyebilir, birden çok sekme satırını görüntüleyebilir ve sekmeleri programlı bir şekilde etkinleştirebilir veya devre dışı bırakabilirsiniz.  
  
### <a name="to-display-an-icon-on-the-label-part-of-a-tab"></a>Bir sekmenin etiket bölümünde bir simge göstermek için  
  
1. Forma <xref:System.Windows.Forms.ImageList> denetimi ekleyin.  
  
2. Görüntü listesine resim ekleyin.  
  
     Görüntü listeleri hakkında daha fazla bilgi için bkz. [ImageList bileşeni](imagelist-component-windows-forms.md) ve [nasıl yapılır: Windows Forms ImageList bileşeni ile görüntü ekleme veya kaldırma](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).  
  
3. <xref:System.Windows.Forms.TabControl> <xref:System.Windows.Forms.TabControl.ImageList%2A> özelliğini <xref:System.Windows.Forms.ImageList> denetimine ayarlayın.  
  
4. <xref:System.Windows.Forms.TabPage> <xref:System.Windows.Forms.TabPage.ImageIndex%2A> özelliğini, listedeki uygun bir görüntünün dizinine ayarlayın.  
  
### <a name="to-create-multiple-rows-of-tabs"></a>Birden çok sekme satırı oluşturmak için  
  
1. İstediğiniz sekme sayfası sayısını ekleyin.  
  
2. <xref:System.Windows.Forms.TabControl> <xref:System.Windows.Forms.TabControl.Multiline%2A> özelliğini `true`olarak ayarlayın.  
  
3. Sekmeler zaten birden çok satırda görünmezse, <xref:System.Windows.Forms.TabControl> <xref:System.Windows.Forms.Control.Width%2A> özelliğini tüm sekmelerden daha dar olacak şekilde ayarlayın.  
  
### <a name="to-arrange-tabs-on-the-side-of-the-control"></a>Denetimin tarafındaki sekmeleri düzenlemek için  
  
- <xref:System.Windows.Forms.TabControl> <xref:System.Windows.Forms.TabControl.Alignment%2A> özelliğini <xref:System.Windows.Forms.TabAlignment.Left> veya <xref:System.Windows.Forms.TabAlignment.Right>olarak ayarlayın.  
  
### <a name="to-programmatically-enable-or-disable-all-controls-on-a-tab"></a>Bir sekmedeki tüm denetimleri programlı bir şekilde etkinleştirmek veya devre dışı bırakmak için  
  
1. <xref:System.Windows.Forms.TabPage> <xref:System.Windows.Forms.TabPage.Enabled%2A> özelliğini `true` veya `false`olarak ayarlayın.  
  
    ```vb  
    TabPage1.Enabled = False  
    ```  
  
    ```csharp  
    tabPage1.Enabled = false;  
    ```  
  
    ```cpp  
    tabPage1->Enabled = false;  
    ```  
  
### <a name="to-display-tabs-as-buttons"></a>Sekmeleri düğme olarak görüntüleme  
  
- <xref:System.Windows.Forms.TabControl> <xref:System.Windows.Forms.TabControl.Appearance%2A> özelliğini <xref:System.Windows.Forms.TabAppearance.Buttons> veya <xref:System.Windows.Forms.TabAppearance.FlatButtons>olarak ayarlayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [TabControl Denetimi](tabcontrol-control-windows-forms.md)
- [TabControl Denetimine Genel Bakış](tabcontrol-control-overview-windows-forms.md)
- [Nasıl yapılır: Sekme Sayfasına Denetim Ekleme](how-to-add-a-control-to-a-tab-page.md)
- [Nasıl yapılır: Sekme Sayfalarını Devre Dışı Bırakma](how-to-disable-tab-pages.md)
- [Nasıl yapılır: Windows Forms TabControl ile Sekme Ekleme ve Kaldırma](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
