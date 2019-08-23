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
ms.openlocfilehash: 8252906de9a574f49617609a4cb08a1e8aa6a992
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929003"
---
# <a name="how-to-display-print-preview-in-windows-forms-applications"></a>Nasıl yapılır: Windows Forms Uygulamalarında Baskı Önizlemede Görüntüleme
Kullanıcıların, genellikle yazdırılmadan <xref:System.Windows.Forms.PrintPreviewDialog> önce bir belgeyi görüntülemesini sağlamak için denetimini kullanabilirsiniz.  
  
 Bunu yapmak için, <xref:System.Drawing.Printing.PrintDocument> sınıfının bir örneğini belirtmeniz gerekir; bu, yazdırılacak belgedir. <xref:System.Drawing.Printing.PrintDocument> Bileşen ile baskı önizlemeyi kullanma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Baskı önizlemeyi](../advanced/how-to-print-in-windows-forms-using-print-preview.md)kullanarak Windows Forms yazdır.  
  
> [!NOTE]
> Çalışma zamanında <xref:System.Windows.Forms.PrintPreviewDialog> denetimi kullanmak için, kullanıcıların bir belgenin yazdırıldığında nasıl görüneceğine ilişkin bir yazıcı, yerel olarak veya bir ağ <xref:System.Windows.Forms.PrintPreviewDialog> aracılığıyla bilgisayarında yüklü bir yazıcıya sahip olması gerekir.  
  
 <xref:System.Windows.Forms.PrintPreviewDialog> Denetim ,<xref:System.Drawing.Printing.PrinterSettings> sınıfını kullanır. Ayrıca, <xref:System.Windows.Forms.PrintPreviewDialog> denetim, <xref:System.Windows.Forms.PrintPreviewDialog> bileşeni olduğu <xref:System.Drawing.Printing.PageSettings> gibi sınıfını kullanır. Denetimin özelliğinde belirtilen <xref:System.Drawing.Printing.PrinterSettings> <xref:System.Drawing.Printing.PageSettings> yazdırma belgesi hem hem de sınıflarının örneklerine başvurur ve bunlar belgeyi önizleme penceresinde işlemek için kullanılır. <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> <xref:System.Windows.Forms.PrintPreviewDialog>  
  
### <a name="to-view-pages-using-the-printpreviewdialog-control"></a>Printönizleme Iletişim kutusu denetimini kullanarak sayfaları görüntülemek için  
  
- Kullanılacak öğesini<xref:System.Drawing.Printing.PrintDocument> belirterek iletişim kutusunu göstermek için <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemini kullanın.  
  
     Aşağıdaki kod örneğinde, <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Click> denetimin olay işleyicisi <xref:System.Windows.Forms.PrintPreviewDialog> denetimin bir örneğini açar. Yazdırma belgesi, <xref:System.Windows.Forms.PrintDialog.Document%2A> özelliğinde belirtilmiştir. Aşağıdaki örnekte, bir yazdırma belgesi belirtilmedi.  
  
     Örnekte formunuzun bir <xref:System.Windows.Forms.Button> denetimi, `myDocument`adlı bir <xref:System.Drawing.Printing.PrintDocument> bileşen ve bir <xref:System.Windows.Forms.PrintPreviewDialog> denetim olması gerekir.  
  
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
