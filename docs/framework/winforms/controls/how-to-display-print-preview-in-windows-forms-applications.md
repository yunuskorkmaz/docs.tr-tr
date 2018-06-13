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
ms.openlocfilehash: 1c1291ea675d823fab3052b0fa365cb2d4c31088
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532814"
---
# <a name="how-to-display-print-preview-in-windows-forms-applications"></a>Nasıl yapılır: Windows Forms Uygulamalarında Baskı Önizlemede Görüntüleme
Kullanabileceğiniz <xref:System.Windows.Forms.PrintPreviewDialog> denetim yazdırılması için önce bir belgeyi genellikle görüntüleme olanağı verir.  
  
 Bunu yapmak için bir örneğini belirtmeniz gerekir <xref:System.Drawing.Printing.PrintDocument> sınıf; yazdırılması belgeye budur. Baskı Önizleme ile kullanma hakkında daha fazla bilgi için <xref:System.Drawing.Printing.PrintDocument> bileşeni Bkz [nasıl yapılır: Windows Forms kullanarak baskı önizlemede yazdırma](../../../../docs/framework/winforms/advanced/how-to-print-in-windows-forms-using-print-preview.md).  
  
> [!NOTE]
>  Kullanılacak <xref:System.Windows.Forms.PrintPreviewDialog> denetim Bu kısmen olduğundan çalışma zamanında, kullanıcıların bilgisayarlarında, yerel olarak veya bir ağ üzerinden yüklü bir yazıcı olmalıdır nasıl <xref:System.Windows.Forms.PrintPreviewDialog> bileşen bir belge yazdırıldığında nasıl görüneceğini belirler.  
  
 <xref:System.Windows.Forms.PrintPreviewDialog> Kontrol kullanır <xref:System.Drawing.Printing.PrinterSettings> sınıfı. Ayrıca, <xref:System.Windows.Forms.PrintPreviewDialog> kontrol kullanır <xref:System.Drawing.Printing.PageSettings> sınıfı gibi <xref:System.Windows.Forms.PrintPreviewDialog> bileşen yapar. Belirtilen Belgeyi Yazdır <xref:System.Windows.Forms.PrintPreviewDialog> denetimin <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> özelliği hem örneklerine başvurur <xref:System.Drawing.Printing.PrinterSettings> ve <xref:System.Drawing.Printing.PageSettings> sınıfları ve bu Önizleme penceresinde belgeyi işlemek için kullanılır.  
  
### <a name="to-view-pages-using-the-printpreviewdialog-control"></a>PrintPreviewDialog denetimi kullanan sayfalar görüntülemek için  
  
-   Kullanmak <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> iletişim kutusunu görüntülemek için yöntemi belirtme <xref:System.Drawing.Printing.PrintDocument> kullanmak için.  
  
     Aşağıdaki kod örneğinde, <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Click> olay işleyicisi açılır örneği <xref:System.Windows.Forms.PrintPreviewDialog> denetim. Belgeyi Yazdır belirtilen <xref:System.Windows.Forms.PrintDialog.Document%2A> özelliği. Aşağıdaki örnekte, bir yazdırma belge belirtilmediğinde.  
  
     Örnek formunuz olmasını gerektirir bir <xref:System.Windows.Forms.Button> denetimi, bir <xref:System.Drawing.Printing.PrintDocument> adlı bileşeni `myDocument`ve bir <xref:System.Windows.Forms.PrintPreviewDialog> denetim.  
  
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
  
     (Visual C# [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [PrintDocument Bileşeni](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)  
 [PrintPreviewDialog Denetimi](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [Windows Forms Yazdırma Desteği](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [Windows Forms](../../../../docs/framework/winforms/index.md)
