---
title: "Nasıl yapılır: Windows Forms Tabcontrol'un görünüşünü değiştirme"
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
ms.openlocfilehash: 1ed062b3991d7738269d30a6ff13cda3c80927c2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54630326"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-tabcontrol"></a>Nasıl yapılır: Windows Forms Tabcontrol'un görünüşünü değiştirme
Özelliklerini kullanarak Windows Forms'da sekme görünümünü değiştirebilirsiniz <xref:System.Windows.Forms.TabControl> ve <xref:System.Windows.Forms.TabPage> ayrı sekmeler denetimi oluşturan nesneleri. Bu özellikleri ayarlayarak sekmelerinde görüntüler, sekme dikey yerine yatay olarak görüntüler, sekme, birden çok satır görüntüleme ve etkinleştirebilir veya sekmeleri program aracılığıyla devre dışı bırakın.  
  
### <a name="to-display-an-icon-on-the-label-part-of-a-tab"></a>Sekmenin etiketi parçası üzerinde bir simge görüntülemek için  
  
1.  Ekleme bir <xref:System.Windows.Forms.ImageList> forma.  
  
2.  Görüntüleri görüntü listesine ekleyin.  
  
     Görüntü listeleri hakkında daha fazla bilgi için bkz: [ImageList bileşeni](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) ve [nasıl yapılır: Ekle veya Kaldır görüntülerle Windows Forms ImageList bileşeni](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).  
  
3.  Ayarlama <xref:System.Windows.Forms.TabControl.ImageList%2A> özelliği <xref:System.Windows.Forms.TabControl> için <xref:System.Windows.Forms.ImageList> denetimi.  
  
4.  Ayarlama <xref:System.Windows.Forms.TabPage.ImageIndex%2A> özelliği <xref:System.Windows.Forms.TabPage> dizine listede uygun görüntü.  
  
### <a name="to-create-multiple-rows-of-tabs"></a>Sekmelerin çoklu satırları oluşturmak için  
  
1.  Sekme sayfaları, istediğiniz sayıda ekleyin.  
  
2.  Ayarlama <xref:System.Windows.Forms.TabControl.Multiline%2A> özelliği <xref:System.Windows.Forms.TabControl> için `true`.  
  
3.  Sekmeleri birden çok satır içinde gösterilmezse ayarlamak <xref:System.Windows.Forms.Control.Width%2A> özelliği <xref:System.Windows.Forms.TabControl> tüm sekmeler dar olacak.  
  
### <a name="to-arrange-tabs-on-the-side-of-the-control"></a>Denetim kenarındaki sekmelerin düzenlemek için  
  
-   Ayarlama <xref:System.Windows.Forms.TabControl.Alignment%2A> özelliği <xref:System.Windows.Forms.TabControl> için <xref:System.Windows.Forms.TabAlignment.Left> veya <xref:System.Windows.Forms.TabAlignment.Right>.  
  
### <a name="to-programmatically-enable-or-disable-all-controls-on-a-tab"></a>Program aracılığıyla etkinleştirme veya bir sekme üzerindeki bütün denetimleri devre dışı  
  
1.  Ayarlama <xref:System.Windows.Forms.TabPage.Enabled%2A> özelliği <xref:System.Windows.Forms.TabPage> için `true` veya `false`.  
  
    ```vb  
    TabPage1.Enabled = False  
    ```  
  
    ```csharp  
    tabPage1.Enabled = false;  
    ```  
  
    ```cpp  
    tabPage1->Enabled = false;  
    ```  
  
### <a name="to-display-tabs-as-buttons"></a>Düğme olarak sekmelerini görüntülemek için  
  
-   Ayarlama <xref:System.Windows.Forms.TabControl.Appearance%2A> özelliği <xref:System.Windows.Forms.TabControl> için <xref:System.Windows.Forms.TabAppearance.Buttons> veya <xref:System.Windows.Forms.TabAppearance.FlatButtons>.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [TabControl Denetimi](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)
- [TabControl Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)
- [Nasıl yapılır: Sekme sayfasına denetim ekleme](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)
- [Nasıl yapılır: Sekme sayfalarını devre dışı bırak](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)
- [Nasıl yapılır: Windows Forms TabControl ile sekme ekleyip](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
