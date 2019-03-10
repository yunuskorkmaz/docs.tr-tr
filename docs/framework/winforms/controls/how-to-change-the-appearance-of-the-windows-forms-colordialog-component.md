---
title: 'Nasıl yapılır: Windows Forms ColorDialog bileşeninin görünüşünü değiştirme'
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
ms.openlocfilehash: 6bc59f08d811ef542206b5788f251f30f89af301
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57702795"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-colordialog-component"></a>Nasıl yapılır: Windows Forms ColorDialog bileşeninin görünüşünü değiştirme
Windows Forms görünümünü yapılandırabileceğiniz <xref:System.Windows.Forms.ColorDialog> özelliklerini sayıda bileşen. İletişim kutusu iki bölümü vardır: bir temel renkleri ve kullanıcının özel renkler tanımlamasına olanak tanıyan bir gösterir.  
  
 Özelliklerin çoğu kullanıcının iletişim kutusundan seçip hangi renkleri kısıtlayın. Varsa <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> özelliği `true`, kullanıcı özel renkler tanımlamak için kullanılabilir. <xref:System.Windows.Forms.ColorDialog.FullOpen%2A> Özelliği `true` iletişim kutusuna özel renkler; tanımlamak için genişletilmişse Aksi takdirde kullanıcı bir "Özel renkler tanımlama" düğmesine gerekir. Zaman <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> özelliği `true`, temel renkleri kümesindeki tüm kullanılabilir renklerin iletişim kutusunda görüntülenir. Varsa <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> özelliği `true`, kullanıcı Titremeli renk seçemez; yalnızca düz renk seçmek kullanılabilir.  
  
 Varsa <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> özelliği `true`, iletişim kutusundaki Yardım düğmesini görünür. Kullanıcı Yardım düğmesine tıkladığında <xref:System.Windows.Forms.ColorDialog> bileşenin <xref:System.Windows.Forms.CommonDialog.HelpRequest> olayı oluşturulur.  
  
### <a name="to-configure-the-appearance-of-the-color-dialog-box"></a>Renk iletişim kutusu görünümünü yapılandırmak için  
  
1.  Ayarlama <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>, <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>, <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>, ve <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> özellikleri için istenen değerleri.  
  
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
