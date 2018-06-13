---
title: "Nasıl yapılır: Bir PrintDialog'dan Çalışma Zamanında Kullanıcı Girdisi Yakalama"
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
ms.openlocfilehash: 554c3c43f8ac4d41ddfc8651472d0b7fbed960bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522882"
---
# <a name="how-to-capture-user-input-from-a-printdialog-at-run-time"></a>Nasıl yapılır: Bir PrintDialog'dan Çalışma Zamanında Kullanıcı Girdisi Yakalama
Tasarım zamanında yazdırma ilgili seçenekleri ayarlayın, ancak bazı durumlarda çalışma zamanında, kullanıcı tarafından yapılan seçimler nedeniyle büyük olasılıkla bu seçeneklerini değiştirmek isteyeceksiniz. Kullanarak bir belge yazdırma için kullanıcı girişi yakalama <xref:System.Windows.Forms.PrintDialog> ve <xref:System.Drawing.Printing.PrintDocument> bileşenleri.  
  
### <a name="to-change-print-options-programmatically"></a>Program aracılığıyla yazdırma seçeneklerini değiştirmek için  
  
1.  Ekleme bir <xref:System.Windows.Forms.PrintDialog> ve <xref:System.Drawing.Printing.PrintDocument> formunuza bileşen.  
  
2.  Ayarlama <xref:System.Windows.Forms.PrintDialog.Document%2A> özelliği <xref:System.Windows.Forms.PrintDialog> için <xref:System.Drawing.Printing.PrintDocument> forma eklenir.  
  
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
  
4.  Kullanıcının yazdırma seçenekleri iletişim kutusundan kopyalanacak <xref:System.Drawing.Printing.PrinterSettings> özelliği <xref:System.Drawing.Printing.PrintDocument> bileşeni.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Windows Forms'ta Çok Sayfalı Metin Dosyası Yazdırma](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 [Windows Forms Yazdırma Desteği](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
