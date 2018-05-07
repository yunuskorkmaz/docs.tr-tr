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
ms.openlocfilehash: 4b1acef216e4f8eca078d47a8cde87fb8f95ee0b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-determine-page-properties-using-the-pagesetupdialog-component"></a>Nasıl Yapılır: PageSetupDialog Bileşenini Kullanarak Sayfa Özelliklerini Belirleme
[PageSetupDialog](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) kullanıcı bir belge için bileşen sunar düzeni, sayfa boyutu ve diğer sayfa düzeni seçenekleri.  
  
 Örneği belirtmek zorunda <xref:System.Drawing.Printing.PrintDocument> sınıfı — yazdırılması belgeye budur. Ayrıca, bu kısmen olduğu gibi kullanıcıların bilgisayarlarında, yerel olarak veya bir ağ üzerinden yüklü bir yazıcı olmalıdır nasıl <xref:System.Windows.Forms.PageSetupDialog> bileşeni kullanıcıya sunulan seçimleri biçimlendirme sayfa belirler.  
  
 İle çalışma önemli bir yönü <xref:System.Windows.Forms.PageSetupDialog> bileşenidir, ile nasıl etkileşim kurduğu <xref:System.Drawing.Printing.PageSettings> sınıfı. <xref:System.Drawing.Printing.PageSettings> Sınıfı, bir sayfa yazdırılabilir, sayfayı ve kenar boşluklarını boyutunu Kağıt yönlendirmesi gibi şekilde değiştiren ayarları belirtmek için kullanılır. Bu ayarların her biri bir özelliği olarak temsil edilir <xref:System.Drawing.Printing.PageSettings> sınıfı. <xref:System.Windows.Forms.PageSetupDialog> Sınıfı, belirli bir örneği için bu özellik değerlerini değiştirir <xref:System.Drawing.Printing.PageSettings> belge ile ilişkili sınıfı (ve olarak temsil edilen bir <xref:System.Drawing.Printing.PrintDocument.DefaultPageSettings%2A> özelliği).  
  
### <a name="to-set-page-properties-using-the-pagesetupdialog-component"></a>PageSetupDialog bileşenini kullanarak sayfa özelliklerini ayarlamak için  
  
1.  Kullanmak <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> iletişim kutusunu görüntülemek için yöntemi belirtme <xref:System.Drawing.Printing.PrintDocument> kullanmak için.  
  
     Aşağıdaki örnekte <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Click> olay işleyicisi açılır örneği <xref:System.Windows.Forms.PageSetupDialog> bileşeni. Var olan bir belgeyi belirtilen <xref:System.Windows.Forms.PageSetupDialog.Document%2A> özelliği ve kendi <xref:System.Drawing.Printing.PageSettings.Color%2A?displayProperty=nameWithType> özelliği ayarlanmış `false`.  
  
     Formunuz sahip örnek varsayar bir <xref:System.Windows.Forms.Button> denetimi, bir <xref:System.Drawing.Printing.PrintDocument> adlı bileşeni `myDocument`ve bir <xref:System.Windows.Forms.PageSetupDialog> bileşeni.  
  
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
  
     (Visual C# ve [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew   
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.PageSetupDialog>  
 [Nasıl yapılır: Standart Windows Forms Yazdırma İşleri Oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)  
 [PageSetupDialog bileşeni](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)
