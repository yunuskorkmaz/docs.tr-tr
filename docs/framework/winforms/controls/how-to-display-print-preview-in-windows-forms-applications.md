---
title: 'Nasıl yapılır: Windows Forms Uygulamalarında Baskı Önizlemede Görüntüleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print preview [Windows Forms], displaying
- printing [Windows Forms], print preview
- examples [Windows Forms], print preview
ms.assetid: e394134c-0886-4517-bd8d-edc4a3749eb5
ms.openlocfilehash: 9efccc220bb27706448ae555db8958afb0ccd9fa
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053602"
---
# <a name="how-to-display-print-preview-in-windows-forms-applications"></a>Nasıl yapılır: Windows Forms Uygulamalarında Baskı Önizlemede Görüntüleme
Kullanabileceğiniz <xref:System.Windows.Forms.PrintPreviewDialog> yazdırılması için önce bir belge genellikle görüntüleme olanağı denetimi.  
  
 Bunu yapmak için örneği belirtmeniz gerekir <xref:System.Drawing.Printing.PrintDocument> sınıfı; yazdırılması için belgeyi budur. Baskı Önizleme ile kullanma hakkında daha fazla bilgi için <xref:System.Drawing.Printing.PrintDocument> bileşeni Bkz [nasıl yapılır: Windows Forms'ta baskı önizlemeyi kullanarak yazdırma](../advanced/how-to-print-in-windows-forms-using-print-preview.md).  
  
> [!NOTE]
>  Kullanılacak <xref:System.Windows.Forms.PrintPreviewDialog> denetimi şu kısmen olduğundan çalışma zamanında, kullanıcıların kendi bilgisayarlarında yerel olarak veya bir ağ üzerinden yüklü bir yazıcının olmalıdır nasıl <xref:System.Windows.Forms.PrintPreviewDialog> bileşeni, bir belge yazdırıldığında nasıl görüneceğini belirler.  
  
 <xref:System.Windows.Forms.PrintPreviewDialog> Denetim kullandığı <xref:System.Drawing.Printing.PrinterSettings> sınıfı. Ayrıca, <xref:System.Windows.Forms.PrintPreviewDialog> denetim kullandığı <xref:System.Drawing.Printing.PageSettings> sınıfı gibi <xref:System.Windows.Forms.PrintPreviewDialog> bileşen yok. Belirtilen Belgeyi Yazdır <xref:System.Windows.Forms.PrintPreviewDialog> denetimin <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> özelliği hem örneklere başvurur <xref:System.Drawing.Printing.PrinterSettings> ve <xref:System.Drawing.Printing.PageSettings> sınıfları ve bu Önizleme penceresinde belgeyi işlemek için kullanılır.  
  
### <a name="to-view-pages-using-the-printpreviewdialog-control"></a>PrintPreviewDialog denetimi kullanan sayfaları görüntülemek için  
  
- Kullanma <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> iletişim kutusunu görüntülemek için yöntemi belirtme <xref:System.Drawing.Printing.PrintDocument> kullanılacak.  
  
     Aşağıdaki kod örneğinde, <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Click> olay işleyicisi örneği açılır <xref:System.Windows.Forms.PrintPreviewDialog> denetimi. Belgeyi Yazdır belirtilen <xref:System.Windows.Forms.PrintDialog.Document%2A> özelliği. Aşağıdaki örnekte, yazdırma belgesi belirtilmedi.  
  
     Örnek formunuza olmasını gerektirir bir <xref:System.Windows.Forms.Button> denetimi, bir <xref:System.Drawing.Printing.PrintDocument> bileşeninizin `myDocument`ve <xref:System.Windows.Forms.PrintPreviewDialog> denetimi.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       ' The print document 'myDocument' used below  
       ' is merely for an example.  
       ' You will have to specify your own print document.  
       PrintPreviewDialog1.Document = myDocument  
       PrintPreviewDialog1.ShowDialog()  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       // The print document 'myDocument' used below  
       // is merely for an example.  
       // You will have to specify your own print document.  
       printPreviewDialog1.Document = myDocument;  
       printPreviewDialog1.ShowDialog();  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // The print document 'myDocument' used below  
          // is merely for an example.  
          // You will have to specify your own print document.  
          printPreviewDialog1->Document = myDocument;  
          printPreviewDialog1->ShowDialog();  
       }  
    ```  
  
     (Visual C#, Visual C++) Aşağıdaki kod, olay işleyicisi kaydetmek için formun oluşturucuda yerleştirin.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [PrintDocument Bileşeni](printdocument-component-windows-forms.md)
- [PrintPreviewDialog Denetimi](printpreviewdialog-control-windows-forms.md)
- [Windows Forms Yazdırma Desteği](../advanced/windows-forms-print-support.md)
- [Windows Forms](../index.md)
