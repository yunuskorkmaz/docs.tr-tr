---
title: 'Nasıl yapılır: Windows Forms ColorDialog Bileşeninin Görünüşünü Değiştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ColorDialog component [Windows Forms], examples
- ColorDialog component [Windows Forms], formatting appearance
- color dialog box [Windows Forms], configuring appearance
ms.assetid: bba4e262-1cd7-4f63-89cf-330a36f7b539
ms.openlocfilehash: 816850fa61de97b5f4c251571a74da7e0a70cba8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-colordialog-component"></a>Nasıl yapılır: Windows Forms ColorDialog Bileşeninin Görünüşünü Değiştirme
Windows formlarının görünüşünü yapılandırabilirsiniz <xref:System.Windows.Forms.ColorDialog> özelliklerini sayısıyla bileşen. İletişim kutusu iki bölümü vardır: bir temel renkleri ve özel renk tanımla kullanıcıya veren gösterir.  
  
 Özelliklerin çoğu kullanıcı iletişim kutusundan seçebilir hangi renkleri kısıtlayın. Varsa <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> özelliği ayarlanmış `true`, kullanıcı özel renkler tanımlamak için izin verilir. <xref:System.Windows.Forms.ColorDialog.FullOpen%2A> Özelliği `true` iletişim kutusunda özel renkler; tanımlamak için genişletilmişse Aksi durumda kullanıcı bir "Özel renk tanımla" düğmesini gerekir. Zaman <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> özelliği ayarlanmış `true`, temel renkler kümesinde kullanılabilir olan tüm renkleri iletişim kutusunu görüntüler. Varsa <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> özelliği ayarlanmış `true`, kullanıcı Titremeli renk seçemezsiniz; yalnızca düz renk seçmek kullanılabilir.  
  
 Varsa <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> özelliği ayarlanmış `true`, Yardım düğmesi üzerinde iletişim kutusu görüntülenir. Kullanıcı Yardım düğmesine tıkladığında <xref:System.Windows.Forms.ColorDialog> bileşenin <xref:System.Windows.Forms.CommonDialog.HelpRequest> olayı oluşturulur.  
  
### <a name="to-configure-the-appearance-of-the-color-dialog-box"></a>Renk iletişim kutusu görünümünü yapılandırmak için  
  
1.  Ayarlama <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>, <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>, <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>, ve <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> istenen değerleri özellikleri.  
  
    ```vb  
    ColorDialog1.AllowFullOpen = True  
    ColorDialog1.AnyColor = True  
    ColorDialog1.SolidColorOnly = False  
    ColorDialog1.ShowHelp = True  
    ```  
  
    ```csharp  
    colorDialog1.AllowFullOpen = true;  
    colorDialog1.AnyColor = true;  
    colorDialog1.SolidColorOnly = false;  
    colorDialog1.ShowHelp = true;  
    ```  
  
    ```cpp  
    colorDialog1->AllowFullOpen = true;  
    colorDialog1->AnyColor = true;  
    colorDialog1->SolidColorOnly = false;  
    colorDialog1->ShowHelp = true;  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ColorDialog>  
 [ColorDialog Bileşeni](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)  
 [ColorDialog Bileşenine Genel Bakış](../../../../docs/framework/winforms/controls/colordialog-component-overview-windows-forms.md)
