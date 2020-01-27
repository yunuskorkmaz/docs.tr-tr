---
title: ColorDialog bileşeninin görünümünü değiştirme
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
ms.openlocfilehash: 0402d7f3c03a0771512a03ac54e1b093c9fe6e9b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746641"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-colordialog-component"></a>Nasıl yapılır: Windows Forms ColorDialog Bileşeninin Görünüşünü Değiştirme
Windows Forms <xref:System.Windows.Forms.ColorDialog> bileşeninin görünümünü bir dizi özelliği ile yapılandırabilirsiniz. İletişim kutusu, temel renkleri ve bir kullanıcının özel renkler tanımlamasına izin veren bir tane olmak üzere iki bölümden oluşur.  
  
 Özelliklerin çoğu, kullanıcının iletişim kutusundan seçim yapabilecekleri renkleri kısıtlar. <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> özelliği `true`olarak ayarlanırsa, kullanıcının özel renkler tanımlamasına izin verilir. İletişim kutusu özel renkler tanımlamak için genişletilmişse, <xref:System.Windows.Forms.ColorDialog.FullOpen%2A> özelliği `true`. Aksi takdirde Kullanıcı "özel renkleri tanımla" düğmesine tıklamalıdır. <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> özelliği `true`olarak ayarlandığında iletişim kutusu, temel renkler kümesindeki kullanılabilir tüm renkleri görüntüler. <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> özelliği `true`olarak ayarlanırsa, Kullanıcı titremeli renklerini seçemezsiniz; yalnızca düz renkler seçilecek şekilde kullanılabilir.  
  
 <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> özelliği `true`olarak ayarlanırsa, iletişim kutusunda bir Yardım düğmesi görünür. Kullanıcı Yardım düğmesine tıkladığında <xref:System.Windows.Forms.ColorDialog> bileşenin <xref:System.Windows.Forms.CommonDialog.HelpRequest> olayı tetiklenir.  
  
### <a name="to-configure-the-appearance-of-the-color-dialog-box"></a>Renk iletişim kutusunun görünümünü yapılandırmak için  
  
1. <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>, <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>, <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>ve <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> özelliklerini istenen değerlere ayarlayın.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ColorDialog>
- [ColorDialog Bileşeni](colordialog-component-windows-forms.md)
- [ColorDialog Bileşenine Genel Bakış](colordialog-component-overview-windows-forms.md)
