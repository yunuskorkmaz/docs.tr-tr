---
title: 'Nasıl yapılır: OpenFileDialog bileşenini kullanarak dosyaları açma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
ms.openlocfilehash: 87e7640da76205341b9e95310314800ac9dbfe30
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54678817"
---
# <a name="how-to-open-files-using-the-openfiledialog-component"></a>Nasıl yapılır: OpenFileDialog bileşenini kullanarak dosyaları açma
<xref:System.Windows.Forms.OpenFileDialog> Bileşen, kullanıcıları, bilgisayarları veya ağ üzerindeki herhangi bir bilgisayarda klasörleri ve açmak için bir veya daha fazla dosya seçmek sağlar. İletişim kutusu iletişim kutusunda seçili kullanıcı dosyasının adını ve yolunu döndürür.  
  
 Kullanıcı açılacak dosyayı seçtikten sonra dosyanın açılış mekanizması için iki yaklaşım vardır. Dosya akışları ile çalışmayı tercih ederseniz, bir örneğini oluşturabilirsiniz <xref:System.IO.StreamReader> sınıfı. Alternatif olarak, kullanabileceğiniz <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> seçili dosyayı açmak için yöntemi.  
  
 İlk örnek içeren bir <xref:System.Security.Permissions.FileIOPermission> izni denetimi ("güvenlik Not" aşağıda açıklandığı gibi), ancak dosya adına erişim sağlar. Yerel makine, Intranet ve Internet bölgelerinden bu tekniği kullanabilirsiniz. İkinci yöntem aynı zamanda mu bir <xref:System.Security.Permissions.FileIOPermission> izni olup olmadığını denetler, ancak daha iyi uygulamalar Intranet veya Internet bölgeleri için uygun.  
  
### <a name="to-open-a-file-as-a-stream-using-the-openfiledialog-component"></a>OpenFileDialog bileşenini kullanarak bir akış olarak bir dosyayı açmak için  
  
1.  Görüntü **Dosya Aç** iletişim kutusu ve kullanıcının seçtiği dosyayı açmak için bir yöntem çağrısı.  
  
     Bir yaklaşım ise kullanılacak <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> Dosya Aç iletişim kutusunu görüntülemek ve kullanmak için yöntem <xref:System.IO.StreamReader> dosyayı açmak için sınıf.  
  
     Kullanan aşağıdaki örnekte <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Click> örneğini açmak için olay işleyicisi <xref:System.Windows.Forms.OpenFileDialog> bileşeni. Seçilen ve kullanıcı bir dosya olduğunda tıkladığında **Tamam**, iletişim kutusunda seçili dosyayı açar. Bu durumda, içeriği yalnızca dosya akışı Okunmuş olduğunu göstermek için bir ileti kutusunda görüntülenir.  
  
    > [!IMPORTANT]
    >  Alınacak veya ayarlanacak <xref:System.Windows.Forms.FileDialog.FileName%2A> özellik, derlemenizin gerektirir ayrıcalık düzeyi verilmiş tarafından <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> sınıfı. Kısmi güven bağlamda çalıştırıyorsanız, işlem yetersiz ayrıcalıklar nedeniyle bir özel durum fırlatabilir. Daha fazla bilgi için [kod erişimi güvenliği Temelleri](../../../../docs/framework/misc/code-access-security-basics.md).  
  
     Formunuza sahip örnek varsayar bir <xref:System.Windows.Forms.Button> denetimi ve bir <xref:System.Windows.Forms.OpenFileDialog> bileşeni.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       If OpenFileDialog1.ShowDialog() = System.Windows.Forms.DialogResult.OK Then  
         Dim sr As New System.IO.StreamReader(OpenFileDialog1.FileName)  
         MessageBox.Show(sr.ReadToEnd)  
         sr.Close()  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       if(openFileDialog1.ShowDialog() == System.Windows.Forms.DialogResult.OK)  
       {  
          System.IO.StreamReader sr = new   
             System.IO.StreamReader(openFileDialog1.FileName);  
          MessageBox.Show(sr.ReadToEnd());  
          sr.Close();  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          if(openFileDialog1->ShowDialog() == System::Windows::Forms::DialogResult::OK)  
          {  
             System::IO::StreamReader ^ sr = gcnew  
                System::IO::StreamReader(openFileDialog1->FileName);  
             MessageBox::Show(sr->ReadToEnd());  
             sr->Close();  
          }  
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
  
    > [!NOTE]
    >  Dosya akışları okuma hakkında daha fazla bilgi için bkz: <xref:System.IO.FileStream.BeginRead%2A> ve <xref:System.IO.FileStream.Read%2A>.  
  
### <a name="to-open-a-file-as-a-file-using-the-openfiledialog-component"></a>OpenFileDialog bileşenini kullanarak bir dosya olarak bir dosyayı açmak için  
  
1.  Kullanım <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> iletişim kutusunu görüntülemek için yöntemi ve <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> dosyayı açmak için yöntemi.  
  
     <xref:System.Windows.Forms.OpenFileDialog> Bileşenin <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> yöntemi compose dosyası bayt döndürür. Bir akış okumak için size bu bayt. Aşağıdaki örnekte bir <xref:System.Windows.Forms.OpenFileDialog> bileşen örneği ile yalnızca dosya adı uzantısına sahip dosyaları seçmesine izin verme "imleç" filtre da`.cur`. Varsa bir`.cur` dosyası seçilmişse, formun imleç seçili imleci ayarlanır.  
  
    > [!IMPORTANT]
    >  Çağrılacak <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> , derlemenizin gerektirdiğine ayrıcalık düzeyi verilen tarafından <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> sınıfı. Kısmi güven bağlamda çalıştırıyorsanız, işlem yetersiz ayrıcalıklar nedeniyle bir özel durum fırlatabilir. Daha fazla bilgi için [kod erişimi güvenliği Temelleri](../../../../docs/framework/misc/code-access-security-basics.md).  
  
     Formunuza sahip örnek varsayar bir <xref:System.Windows.Forms.Button> denetimi.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       ' Displays an OpenFileDialog so the user can select a Cursor.  
       Dim openFileDialog1 As New OpenFileDialog()  
       openFileDialog1.Filter = "Cursor Files|*.cur"  
       openFileDialog1.Title = "Select a Cursor File"  
  
       ' Show the Dialog.  
       ' If the user clicked OK in the dialog and   
       ' a .CUR file was selected, open it.  
       If openFileDialog1.ShowDialog() = System.Windows.Forms.DialogResult.OK Then  
         ' Assign the cursor in the Stream to the Form's Cursor property.  
         Me.Cursor = New Cursor(openFileDialog1.OpenFile())  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       // Displays an OpenFileDialog so the user can select a Cursor.  
       OpenFileDialog openFileDialog1 = new OpenFileDialog();  
       openFileDialog1.Filter = "Cursor Files|*.cur";  
       openFileDialog1.Title = "Select a Cursor File";  
  
       // Show the Dialog.  
       // If the user clicked OK in the dialog and  
       // a .CUR file was selected, open it.  
        if (openFileDialog1.ShowDialog() == System.Windows.Forms.DialogResult.OK)  
       {  
          // Assign the cursor in the Stream to the Form's Cursor property.  
          this.Cursor = new Cursor(openFileDialog1.OpenFile());  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // Displays an OpenFileDialog so the user can select a Cursor.  
          OpenFileDialog ^ openFileDialog1 = new OpenFileDialog();  
          openFileDialog1->Filter = "Cursor Files|*.cur";  
          openFileDialog1->Title = "Select a Cursor File";  
  
          // Show the Dialog.  
          // If the user clicked OK in the dialog and  
          // a .CUR file was selected, open it.  
          if (openFileDialog1->ShowDialog() == System::Windows::Forms::DialogResult::OK)  
          {  
             // Assign the cursor in the Stream to  
             // the Form's Cursor property.  
             this->Cursor = gcnew  
                System::Windows::Forms::Cursor(  
                openFileDialog1->OpenFile());  
          }  
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
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.OpenFileDialog>
- [OpenFileDialog Bileşeni](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md)
