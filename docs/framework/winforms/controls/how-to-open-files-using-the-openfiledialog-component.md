---
title: "Nasıl Yapılır: OpenFileDialog Bileşenini Kullanarak Dosyaları Açma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 52726a770e33bec4b5ec9b24f33deb44ed6379b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-open-files-using-the-openfiledialog-component"></a>Nasıl Yapılır: OpenFileDialog Bileşenini Kullanarak Dosyaları Açma
<xref:System.Windows.Forms.OpenFileDialog> Bileşeni, kullanıcıların ağ üzerindeki herhangi bir bilgisayar veya bilgisayarlarını klasörleri bulun ve açmak için bir veya daha fazla dosya seçin sağlar. İletişim kutusu, iletişim kutusunda seçili kullanıcı dosyasının adını ve yolunu döndürür.  
  
 Kullanıcı açılması için dosyanın seçtikten sonra dosyayı açma mekanizması için iki yaklaşım vardır. Dosya akışları ile çalışmayı tercih ederseniz örneği oluşturabilirsiniz <xref:System.IO.StreamReader> sınıfı. Alternatif olarak, kullanabileceğiniz <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> seçilen dosyayı açmak için yöntem.  
  
 Aşağıdaki ilk örnekte içerir bir <xref:System.Security.Permissions.FileIOPermission> ("güvenlik Not" aşağıda açıklandığı gibi) izni denetimi ancak dosya adına erişim sağlar. Yerel makine, Intranet ve Internet bölgelerinden bu tekniği kullanabilirsiniz. İkinci yöntem de mu bir <xref:System.Security.Permissions.FileIOPermission> izni denetimi, ancak daha iyi Intranet veya Internet bölgelerde uygulamalar için uygun.  
  
### <a name="to-open-a-file-as-a-stream-using-the-openfiledialog-component"></a>OpenFileDialog bileşenini kullanarak bir akış bir dosyayı açmak için  
  
1.  Görüntü **Dosya Aç** iletişim kutusu ve kullanıcı tarafından seçilen dosyayı açmak için bir yöntemini çağırın.  
  
     Bir yaklaşım ise kullanılacak <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> Dosya Aç iletişim kutusu görüntülemek ve bir örneğini kullanması için yöntem <xref:System.IO.StreamReader> dosyayı açmak için sınıf.  
  
     Kullandığı aşağıdaki örnekte <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Click> bir örneğini açmak için olay işleyicisini <xref:System.Windows.Forms.OpenFileDialog> bileşeni. Bir dosya seçilen ve kullanıcı olduğunda tıklar **Tamam**, iletişim kutusunda seçili dosyasını açar. Bu durumda, içeriği yalnızca dosya akışı Okunmuş göstermek için bir ileti kutusunda görüntülenir.  
  
    > [!IMPORTANT]
    >  Almak veya ayarlamak için <xref:System.Windows.Forms.FileDialog.FileName%2A> özelliği, derlemenizi gerektiren bir ayrıcalık düzeyi verilen tarafından <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> sınıfı. Kısmi güven bağlamda çalıştırıyorsanız, işlem nedeniyle yeterli ayrıcalığa sahip bir özel durum. Daha fazla bilgi için bkz: [kod erişim güvenliği Temelleri](../../../../docs/framework/misc/code-access-security-basics.md).  
  
     Formunuz sahip örnek varsayar bir <xref:System.Windows.Forms.Button> denetim ve bir <xref:System.Windows.Forms.OpenFileDialog> bileşeni.  
  
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
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] ve [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.  
  
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
  
1.  Kullanım <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> iletişim kutusunu görüntülemek için yöntemi ve <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> yöntemi dosyasını açın.  
  
     <xref:System.Windows.Forms.OpenFileDialog> Bileşenin <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> yöntemi dosyasını oluşturan bayt döndürür. Bu bayt okuma bir akış verin. Aşağıdaki örnekte bir <xref:System.Windows.Forms.OpenFileDialog> bileşen örneği yalnızca dosya adı uzantısına sahip dosyalar seçmesine izin verme "imleç" filtre da ile`.cur`. Varsa bir`.cur` dosya seçilmişse, formun imleç seçili imleci ayarlanır.  
  
    > [!IMPORTANT]
    >  Çağrılacak <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> , derlemenizi gerektirdiğine ayrıcalık düzeyi verilen tarafından <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> sınıfı. Kısmi güven bağlamda çalıştırıyorsanız, işlem nedeniyle yeterli ayrıcalığa sahip bir özel durum. Daha fazla bilgi için bkz: [kod erişim güvenliği Temelleri](../../../../docs/framework/misc/code-access-security-basics.md).  
  
     Formunuz sahip örnek varsayar bir <xref:System.Windows.Forms.Button> denetim.  
  
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
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] ve [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.OpenFileDialog>  
 [OpenFileDialog bileşeni](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md)
