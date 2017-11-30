---
title: "Nasıl Yapılır: SaveFileDialog Bileşenini Kullanarak Dosyaları Kaydetme"
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
- saving files
- SaveFileDialog component [Windows Forms], saving files
- files [Windows Forms], saving
- OpenFile method [Windows Forms], saving files with SaveFileDialog component
ms.assetid: 02e8f409-b83f-4707-babb-e71f6b223d90
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 01bac8fc020955e78e7648db72492014acc19944
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-save-files-using-the-savefiledialog-component"></a>Nasıl Yapılır: SaveFileDialog Bileşenini Kullanarak Dosyaları Kaydetme
<xref:System.Windows.Forms.SaveFileDialog> Bileşeni, dosya sistemi göz atın ve kaydedilecek dosyaları seçmek kullanıcıların sağlar. İletişim kutusu, kullanıcı iletişim kutusundaki seçilmiş dosyanın adını ve yolunu döndürür. Ancak, aslında dosyaları diske yazmak için kod yazmanız gerekir.  
  
### <a name="to-save-a-file-using-the-savefiledialog-component"></a>SaveFileDialog bileşenini kullanarak bir dosyayı kaydetmek için  
  
-   Görüntü **dosyayı Kaydet** iletişim kutusu ve kullanıcı tarafından seçilen dosyanın kaydedileceği bir yöntemini çağırın.  
  
     Kullanım <xref:System.Windows.Forms.SaveFileDialog> bileşenin <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> yöntemi dosyayı kaydedin. Bu yöntem sağlayan bir <xref:System.IO.Stream> nesnesi için yazma.  
  
     Kullandığı aşağıdaki örnekte <xref:System.Windows.Forms.DialogResult> dosyasının adını almak için özellik ve <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> yöntemi dosyayı kaydedin. <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> Yöntemi veya dosyaya yazmak için bir akış sunar.  
  
     Aşağıdaki örnekte, var olan bir <xref:System.Windows.Forms.Button> kendisine atanmış bir görüntüyle denetim. Düğmeye tıkladığınızda bir <xref:System.Windows.Forms.SaveFileDialog> bileşen türü .gif, .jpeg ve .bmp dosyaları tanıyan bir filtre ile örneği. Bu tür bir dosyayı dosya Kaydet iletişim kutusunda seçili ise, düğmenin resim kaydedilir.  
  
    > [!IMPORTANT]
    >  Almak veya ayarlamak için <xref:System.Windows.Forms.FileDialog.FileName%2A> özelliği, derlemenizi gerektiren bir ayrıcalık düzeyi verilen tarafından <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> sınıfı. Kısmi güven bağlamda çalıştırıyorsanız, işlem nedeniyle yeterli ayrıcalığa sahip bir özel durum. Daha fazla bilgi için bkz: [kod erişim güvenliği Temelleri](../../../../docs/framework/misc/code-access-security-basics.md).  
  
     Formunuz sahip örnek varsayar bir <xref:System.Windows.Forms.Button> ile denetim kendi <xref:System.Windows.Forms.ButtonBase.Image%2A> özellik türü .gif, .jpeg veya .bmp dosyasına ayarlayın.  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.FileDialog> Sınıfının <xref:System.Windows.Forms.FileDialog.FilterIndex%2A> özelliği (, devralma nedeniyle olduğu parçası <xref:System.Windows.Forms.SaveFileDialog> sınıfı) tabanlı bir dizin kullanır. Bu verileri (örneğin, kaydetme ikili biçimi yerine düz metin dosyasında) belirli bir biçimde kaydetmek için kod yazıyorsanız önemlidir. Bu özellik, aşağıdaki örnekte öne çıkan.  
  
    ```vb  
    Private Sub Button2_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles Button2.Click  
       ' Displays a SaveFileDialog so the user can save the Image  
       ' assigned to Button2.  
       Dim saveFileDialog1 As New SaveFileDialog()  
       saveFileDialog1.Filter = "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif"  
       saveFileDialog1.Title = "Save an Image File"  
       saveFileDialog1.ShowDialog()  
  
       ' If the file name is not an empty string open it for saving.  
       If saveFileDialog1.FileName <> "" Then  
          ' Saves the Image via a FileStream created by the OpenFile method.  
          Dim fs As System.IO.FileStream = Ctype _  
             (saveFileDialog1.OpenFile(), System.IO.FileStream)  
          ' Saves the Image in the appropriate ImageFormat based upon the  
          ' file type selected in the dialog box.  
          ' NOTE that the FilterIndex property is one-based.  
          Select Case saveFileDialog1.FilterIndex  
             Case 1  
                Me.button2.Image.Save(fs, _  
                   System.Drawing.Imaging.ImageFormat.Jpeg)  
  
             Case 2  
                Me.button2.Image.Save(fs, _  
                   System.Drawing.Imaging.ImageFormat.Bmp)  
  
             Case 3  
                Me.button2.Image.Save(fs, _  
                   System.Drawing.Imaging.ImageFormat.Gif)  
           End Select  
  
           fs.Close()  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button2_Click(object sender, System.EventArgs e)  
    {  
       // Displays a SaveFileDialog so the user can save the Image  
       // assigned to Button2.  
       SaveFileDialog saveFileDialog1 = new SaveFileDialog();  
       saveFileDialog1.Filter = "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif";  
       saveFileDialog1.Title = "Save an Image File";  
       saveFileDialog1.ShowDialog();  
  
       // If the file name is not an empty string open it for saving.  
       if(saveFileDialog1.FileName != "")  
       {  
          // Saves the Image via a FileStream created by the OpenFile method.  
          System.IO.FileStream fs =   
             (System.IO.FileStream)saveFileDialog1.OpenFile();  
          // Saves the Image in the appropriate ImageFormat based upon the  
          // File type selected in the dialog box.  
          // NOTE that the FilterIndex property is one-based.  
          switch(saveFileDialog1.FilterIndex)  
          {  
             case 1 :   
             this.button2.Image.Save(fs,   
                System.Drawing.Imaging.ImageFormat.Jpeg);  
             break;  
  
             case 2 :   
             this.button2.Image.Save(fs,   
                System.Drawing.Imaging.ImageFormat.Bmp);  
             break;  
  
             case 3 :   
             this.button2.Image.Save(fs,   
                System.Drawing.Imaging.ImageFormat.Gif);  
             break;  
          }  
  
       fs.Close();  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void button2_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // Displays a SaveFileDialog so the user can save the Image  
          // assigned to Button2.  
          SaveFileDialog ^ saveFileDialog1 = new SaveFileDialog();  
          saveFileDialog1->Filter =   
             "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif";  
          saveFileDialog1->Title = "Save an Image File";  
          saveFileDialog1->ShowDialog();  
          // If the file name is not an empty string, open it for saving.  
          if(saveFileDialog1->FileName != "")  
          {  
             // Saves the Image through a FileStream created by  
             // the OpenFile method.  
             System::IO::FileStream ^ fs =   
                safe_cast\<System::IO::FileStream*>(  
                saveFileDialog1->OpenFile());  
             // Saves the Image in the appropriate ImageFormat based on  
             // the file type selected in the dialog box.  
             // Note that the FilterIndex property is one based.  
             switch(saveFileDialog1->FilterIndex)  
             {  
                case 1 :  
                   this->button2->Image->Save(fs,  
                      System::Drawing::Imaging::ImageFormat::Jpeg);  
                   break;  
                case 2 :  
                   this->button2->Image->Save(fs,   
                      System::Drawing::Imaging::ImageFormat::Bmp);  
                   break;  
                case 3 :  
                   this->button2->Image->Save(fs,   
                      System::Drawing::Imaging::ImageFormat::Gif);  
                   break;  
             }  
          fs->Close();  
          }  
       }  
    ```  
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] ve [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.  
  
    ```csharp  
    this.button2.Click += new System.EventHandler(this.button2_Click);  
    ```  
  
    ```cpp  
    this->button2->Click += gcnew  
       System::EventHandler(this, &Form1::button2_Click);  
    ```  
  
     Dosya akışları yazma hakkında daha fazla bilgi için bkz: <xref:System.IO.FileStream.BeginWrite%2A> ve <xref:System.IO.FileStream.Write%2A>.  
  
    > [!NOTE]
    >  Gibi belirli denetimleri <xref:System.Windows.Forms.RichTextBox> denetlemek, dosyaları kaydedebilir seçeneğine sahipsiniz. Daha fazla bilgi için MSDN Çevrimiçi Kitaplığı teknik makalenin "SaveFileDialog bileşeni" bölümüne bakın [Windows için önemli kod Forms iletişim kutuları](http://go.microsoft.com/fwlink/?LinkID=102575).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.SaveFileDialog>  
 [SaveFileDialog bileşeni](../../../../docs/framework/winforms/controls/savefiledialog-component-windows-forms.md)
