---
title: 'Nasıl yapılır: PageSetupDialog Bileşenini Kullanarak Sayfa Özelliklerini Belirleme'
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
ms.openlocfilehash: 306e0dbf7fb819d1214d7d5d93d335b5d2db75e6
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053613"
---
# <a name="how-to-determine-page-properties-using-the-pagesetupdialog-component"></a>Nasıl yapılır: PageSetupDialog Bileşenini Kullanarak Sayfa Özelliklerini Belirleme
[PageSetupDialog](pagesetupdialog-component-windows-forms.md) kullanıcıya bir belge için bileşen sunar düzen, sayfa boyutunu ve diğer sayfa düzeni seçenekleri.  
  
 Örneği belirtmeniz gereken <xref:System.Drawing.Printing.PrintDocument> sınıfı — belgenin yazdırılması budur. Ayrıca, bu kısmen olduğundan kullanıcıların kendi bilgisayarlarında yerel olarak veya bir ağ üzerinden yüklü bir yazıcının olmalıdır nasıl <xref:System.Windows.Forms.PageSetupDialog> bileşen sayfasının kullanıcıya sunulan seçenekler biçimlendirme belirler.  
  
 İle çalışmanın önemli bir yönüdür <xref:System.Windows.Forms.PageSetupDialog> bileşendir nasıl etkileşimde <xref:System.Drawing.Printing.PageSettings> sınıfı. <xref:System.Drawing.Printing.PageSettings> Sınıfı, bir sayfa yazdırılır, sayfa ve kenar boşlukları boyutunu Kağıt yönlendirmesi gibi şekilde ayarlarını belirtmek için kullanılır. Bu ayarların her biri bir özelliği olarak temsil edilen <xref:System.Drawing.Printing.PageSettings> sınıfı. <xref:System.Windows.Forms.PageSetupDialog> Sınıfı belirli bir örneği için bu özellik değerlerini değiştirir <xref:System.Drawing.Printing.PageSettings> belgeyle ilişkili sınıf (ve olarak temsil edilen bir <xref:System.Drawing.Printing.PrintDocument.DefaultPageSettings%2A> özelliği).  
  
### <a name="to-set-page-properties-using-the-pagesetupdialog-component"></a>PageSetupDialog bileşenini kullanarak sayfa özelliklerini ayarlamak için  
  
1. Kullanma <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> iletişim kutusunu görüntülemek için yöntemi belirtme <xref:System.Drawing.Printing.PrintDocument> kullanılacak.  
  
     Aşağıdaki örnekte <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Click> olay işleyicisi örneği açılır <xref:System.Windows.Forms.PageSetupDialog> bileşeni. Var olan bir belgeyi belirtilen <xref:System.Windows.Forms.PageSetupDialog.Document%2A> özelliği ve kendi <xref:System.Drawing.Printing.PageSettings.Color%2A?displayProperty=nameWithType> özelliği `false`.  
  
     Formunuza sahip örnek varsayar bir <xref:System.Windows.Forms.Button> denetimi, bir <xref:System.Drawing.Printing.PrintDocument> bileşeninizin `myDocument`ve <xref:System.Windows.Forms.PageSetupDialog> bileşeni.  
  
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
  
     (Visual C# ve görsel C++) Aşağıdaki kod, olay işleyicisi kaydetmek için formun oluşturucuda yerleştirin.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew   
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.PageSetupDialog>
- [Nasıl yapılır: Standart Windows Forms yazdırma işleri oluşturma](../advanced/how-to-create-standard-windows-forms-print-jobs.md)
- [PageSetupDialog bileşeni](pagesetupdialog-component-windows-forms.md)
