---
title: "Nasıl yapılır: Windows Forms TabControl'nin Görünüşünü Değiştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b244930f0837d3b1d548e0f7a8c77dd80e1ce039
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-tabcontrol"></a>Nasıl yapılır: Windows Forms TabControl'nin Görünüşünü Değiştirme
Özelliklerini kullanarak Windows Forms'ta sekmeler görünümünü değiştirebilirsiniz <xref:System.Windows.Forms.TabControl> ve <xref:System.Windows.Forms.TabPage> denetimi tek tek sekmelerinde oluşturan nesneleri. Bu özellikleri ayarlayarak, görüntüleri sekmelerde görüntüleme, dikey yerine yatay sekmelerini görüntülemek, sekme, birden çok satır görüntüleme ve etkinleştirebilir veya sekmeleri program aracılığıyla devre dışı bırakın.  
  
### <a name="to-display-an-icon-on-the-label-part-of-a-tab"></a>Simge bir sekme etiketi parçası görüntülemek için  
  
1.  Ekleme bir <xref:System.Windows.Forms.ImageList> forma denetim.  
  
2.  Görüntüleri görüntü listesine ekleyin.  
  
     Görüntü listeleri hakkında daha fazla bilgi için bkz: [ImageList bileşeni](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) ve [nasıl yapılır: Windows Forms ImageList bileşeni ile görüntüleri ekleme veya kaldırma](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).  
  
3.  Ayarlama <xref:System.Windows.Forms.TabControl.ImageList%2A> özelliği <xref:System.Windows.Forms.TabControl> için <xref:System.Windows.Forms.ImageList> denetim.  
  
4.  Ayarlama <xref:System.Windows.Forms.TabPage.ImageIndex%2A> özelliği <xref:System.Windows.Forms.TabPage> listesinde uygun görüntünün dizin.  
  
### <a name="to-create-multiple-rows-of-tabs"></a>Birden çok satır sekmelerinin oluşturmak için  
  
1.  Sekme sayfaları istediğiniz sayısı ekleyin.  
  
2.  Ayarlama <xref:System.Windows.Forms.TabControl.Multiline%2A> özelliği <xref:System.Windows.Forms.TabControl> için `true`.  
  
3.  Sekmeleri birden çok satır gösterilmezse ayarlamak <xref:System.Windows.Forms.Control.Width%2A> özelliği <xref:System.Windows.Forms.TabControl> sekmelerin dar olmalıdır.  
  
### <a name="to-arrange-tabs-on-the-side-of-the-control"></a>Sekme denetimi yan tarafında düzenlemek için  
  
-   Ayarlama <xref:System.Windows.Forms.TabControl.Alignment%2A> özelliği <xref:System.Windows.Forms.TabControl> için <xref:System.Windows.Forms.TabAlignment.Left> veya <xref:System.Windows.Forms.TabAlignment.Right>.  
  
### <a name="to-programmatically-enable-or-disable-all-controls-on-a-tab"></a>Program aracılığıyla etkinleştirmek veya bir sekmede tüm denetimleri devre dışı bırakmak için  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [TabControl denetimi](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)  
 [TabControl denetimine genel bakış](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [Nasıl yapılır: sekme sayfasına denetim ekleme](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)  
 [Nasıl yapılır: sekme sayfalarını devre dışı bırak](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)  
 [Nasıl yapılır: Windows Forms TabControl ile sekme ekleme ve kaldırma](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
