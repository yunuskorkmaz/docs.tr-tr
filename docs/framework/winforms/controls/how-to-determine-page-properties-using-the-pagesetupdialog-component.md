---
title: 'Nasıl Yapılır: PageSetupDialog Bileşenini Kullanarak Sayfa Özelliklerini Belirleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- page properties
- page setup
- PageSetupDialog component
ms.assetid: 6dae05bc-c0fd-4357-bb93-841a1631d98f
ms.openlocfilehash: 8a015c199193dfd9c43bec53cc93cbf9dc201413
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142049"
---
# <a name="how-to-determine-page-properties-using-the-pagesetupdialog-component"></a>Nasıl Yapılır: PageSetupDialog Bileşenini Kullanarak Sayfa Özelliklerini Belirleme
[PageSetupDialog](pagesetupdialog-component-windows-forms.md) bileşeni, bir belge için kullanıcıya düzen, kağıt boyutu ve diğer sayfa düzeni seçeneklerini sunar.  
  
 <xref:System.Drawing.Printing.PrintDocument> Sınıfın bir örneğini belirtmeniz gerekir, bu yazdırılacak belgedir. Ayrıca, bileşenin kullanıcıya sunulan sayfa biçimlendirme seçeneklerini kısmen nasıl <xref:System.Windows.Forms.PageSetupDialog> belirlediği nden, kullanıcıların bilgisayarında yerel olarak veya ağ üzerinden bir yazıcı yüklü olması gerekir.  
  
 <xref:System.Windows.Forms.PageSetupDialog> Bileşenle çalışmanın önemli bir yönü de <xref:System.Drawing.Printing.PageSettings> sınıfla nasıl etkileşimde olduğudur. Sınıf, <xref:System.Drawing.Printing.PageSettings> kağıt yönlendirmesi, sayfanın boyutu ve kenar boşlukları gibi sayfanın yazdırılma biçimini değiştiren ayarları belirtmek için kullanılır. Bu ayarların her biri <xref:System.Drawing.Printing.PageSettings> sınıfın bir özelliği olarak temsil edilir. Sınıf, <xref:System.Windows.Forms.PageSetupDialog> belgeyle ilişkili (ve özellik <xref:System.Drawing.Printing.PageSettings> <xref:System.Drawing.Printing.PrintDocument.DefaultPageSettings%2A> olarak temsil edilen) sınıfın belirli bir örneği için bu özellik değerlerini değiştirir.  
  
### <a name="to-set-page-properties-using-the-pagesetupdialog-component"></a>PageSetupDialog bileşenini kullanarak sayfa özelliklerini ayarlamak için  
  
1. İletişim <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> kutusunu görüntülemek için kullanımı belirten <xref:System.Drawing.Printing.PrintDocument> yöntemi kullanın.  
  
     Aşağıdaki örnekte, <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Click> olay işleyicisi bileşenin bir örneğini <xref:System.Windows.Forms.PageSetupDialog> açar. Özellikte <xref:System.Windows.Forms.PageSetupDialog.Document%2A> varolan bir belge belirtilir <xref:System.Drawing.Printing.PageSettings.Color%2A?displayProperty=nameWithType> ve özelliği `false`.  
  
     Örnek, formunuzun bir <xref:System.Windows.Forms.Button> denetimi, <xref:System.Drawing.Printing.PrintDocument> adında `myDocument`bir <xref:System.Windows.Forms.PageSetupDialog> bileşeni ve bir bileşeni olduğunu varsayar.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles Button1.Click  
       ' The print document 'myDocument' used below  
       ' is merely for an example.  
       'You will have to specify your own print document.  
       PageSetupDialog1.Document = myDocument  
       ' Sets the print document's color setting to false,  
       ' so that the page will not be printed in color.  
       PageSetupDialog1.Document.DefaultPageSettings.Color = False  
       PageSetupDialog1.ShowDialog()  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       // The print document 'myDocument' used below  
       // is merely for an example.  
       // You will have to specify your own print document.  
       pageSetupDialog1.Document = myDocument;  
       // Sets the print document's color setting to false,  
       // so that the page will not be printed in color.  
       pageSetupDialog1.Document.DefaultPageSettings.Color = false;  
       pageSetupDialog1.ShowDialog();  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void button1_Click(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          // The print document 'myDocument' used below  
          // is merely for an example.  
          // You will have to specify your own print document.  
          pageSetupDialog1->Document = myDocument;  
          // Sets the print document's color setting to false,  
          // so that the page will not be printed in color.  
          pageSetupDialog1->Document->DefaultPageSettings->Color = false;  
          pageSetupDialog1->ShowDialog();  
       }  
    ```  
  
     (Görsel C# ve Görsel C++) Olay işleyicisini kaydetmek için aşağıdaki kodu formun oluşturucusuna yerleştirin.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.PageSetupDialog>
- [Nasıl yapılır: Standart Windows Forms Yazdırma İşleri Oluşturma](../advanced/how-to-create-standard-windows-forms-print-jobs.md)
- [PageSetupDialog bileşeni](pagesetupdialog-component-windows-forms.md)
