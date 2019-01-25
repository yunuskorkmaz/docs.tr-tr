---
title: "Nasıl yapılır: Kullanıcı girişi bir printdialog'dan çalışma zamanında yakalama"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print options [Windows Forms], changing at run time
- printing [Windows Forms], options
- print options
- run time [Windows Forms], changing print options
ms.assetid: 438501d8-9a70-4fb3-aae6-e46579aba0c6
ms.openlocfilehash: a15563560615f5b857220c0b548fc57f31ee4e09
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527672"
---
# <a name="how-to-capture-user-input-from-a-printdialog-at-run-time"></a>Nasıl yapılır: Kullanıcı girişi bir printdialog'dan çalışma zamanında yakalama
İlgili tasarım zamanında yazdırma seçeneklerini ayarlayabilirsiniz, ancak bazen çalışma zamanında, kullanıcı tarafından yapılan seçimler nedeniyle büyük olasılıkla bu seçenekleri değiştirmek istersiniz. Kullanarak bir belge yazdırma için kullanıcı girişi yakalayabilirsiniz <xref:System.Windows.Forms.PrintDialog> ve <xref:System.Drawing.Printing.PrintDocument> bileşenleri.  
  
### <a name="to-change-print-options-programmatically"></a>Program aracılığıyla yazdırma seçeneklerini değiştirmek için  
  
1.  Ekleme bir <xref:System.Windows.Forms.PrintDialog> ve <xref:System.Drawing.Printing.PrintDocument> formunuza bileşen.  
  
2.  Ayarlama <xref:System.Windows.Forms.PrintDialog.Document%2A> özelliği <xref:System.Windows.Forms.PrintDialog> için <xref:System.Drawing.Printing.PrintDocument> formuna eklenir.  
  
    ```vb  
    PrintDialog1.Document = PrintDocument1  
    ```  
  
    ```csharp  
    printDialog1.Document = PrintDocument1;  
    ```  
  
    ```cpp  
    printDialog1->Document = PrintDocument1;  
    ```  
  
3.  Görüntü <xref:System.Windows.Forms.PrintDialog> kullanarak bileşen <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemi.  
  
    ```vb  
    PrintDialog1.ShowDialog()  
    ```  
  
    ```csharp  
    printDialog1.ShowDialog();  
    ```  
  
    ```cpp  
    printDialog1->ShowDialog();  
    ```  
  
4.  Kullanıcının yazdırma seçenekleri iletişim kutusundan kopyalanmasını <xref:System.Drawing.Printing.PrinterSettings> özelliği <xref:System.Drawing.Printing.PrintDocument> bileşeni.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Windows Forms'ta çok sayfalı metin dosyası yazdırma](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)
- [Windows Forms Yazdırma Desteği](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
