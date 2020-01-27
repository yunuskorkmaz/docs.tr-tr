---
title: Windows Forms uygulamalarında baskı önizlemeyi görüntüleme
titleSuffix: ''
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
ms.openlocfilehash: ac02339ad86e491cd047dcd4b0c8841374b3bb2e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745575"
---
# <a name="how-to-display-print-preview-in-windows-forms-applications"></a>Nasıl yapılır: Windows Forms Uygulamalarında Baskı Önizlemede Görüntüleme
Kullanıcıların, genellikle yazdırılmadan önce bir belgeyi görüntülemesini sağlamak için <xref:System.Windows.Forms.PrintPreviewDialog> denetimini kullanabilirsiniz.  
  
 Bunu yapmak için <xref:System.Drawing.Printing.PrintDocument> sınıfının bir örneğini belirtmeniz gerekir; Bu, yazdırılacak belgedir. <xref:System.Drawing.Printing.PrintDocument> bileşeniyle baskı önizlemeyi kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: baskı önizlemeyi kullanarak Windows Forms Yazdırma](../advanced/how-to-print-in-windows-forms-using-print-preview.md).  
  
> [!NOTE]
> Çalışma zamanında <xref:System.Windows.Forms.PrintPreviewDialog> denetimini kullanmak için, kullanıcıların, bir belgenin yazdırıldığında nasıl görüneceğine ilişkin bir, <xref:System.Windows.Forms.PrintPreviewDialog> bileşeninin bir yazıcı üzerinden yerel olarak ya da bir ağ üzerinden yüklü olması gerekir.  
  
 <xref:System.Windows.Forms.PrintPreviewDialog> denetim <xref:System.Drawing.Printing.PrinterSettings> sınıfını kullanır. Ayrıca, <xref:System.Windows.Forms.PrintPreviewDialog> bileşeni gibi <xref:System.Windows.Forms.PrintPreviewDialog> denetimi <xref:System.Drawing.Printing.PageSettings> sınıfını kullanır. <xref:System.Windows.Forms.PrintPreviewDialog> denetiminin <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> özelliğinde belirtilen yazdırma belgesi hem <xref:System.Drawing.Printing.PrinterSettings> hem de <xref:System.Drawing.Printing.PageSettings> sınıflarının örneklerine başvurur ve bunlar belgeyi önizleme penceresinde işlemek için kullanılır.  
  
### <a name="to-view-pages-using-the-printpreviewdialog-control"></a>Printönizleme Iletişim kutusu denetimini kullanarak sayfaları görüntülemek için  
  
- Kullanılacak <xref:System.Drawing.Printing.PrintDocument> belirterek iletişim kutusunu göstermek için <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemini kullanın.  
  
     Aşağıdaki kod örneğinde, <xref:System.Windows.Forms.Button> denetiminin <xref:System.Windows.Forms.Control.Click> olay işleyicisi <xref:System.Windows.Forms.PrintPreviewDialog> denetiminin bir örneğini açar. Yazdırma belgesi <xref:System.Windows.Forms.PrintDialog.Document%2A> özelliğinde belirtilmiştir. Aşağıdaki örnekte, bir yazdırma belgesi belirtilmedi.  
  
     Örnekte formunuzun <xref:System.Windows.Forms.Button> denetimi, `myDocument`adlı bir <xref:System.Drawing.Printing.PrintDocument> bileşeni ve <xref:System.Windows.Forms.PrintPreviewDialog> denetimi olması gerekir.  
  
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
  
     (Görsel C#, görsel C++) Olay işleyicisini kaydetmek için formun oluşturucusuna aşağıdaki kodu yerleştirin.  
  
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
