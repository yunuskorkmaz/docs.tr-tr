---
title: 'Nasıl Yapılır: SaveFileDialog Bileşenini Kullanarak Dosyaları Kaydetme'
ms.date: 03/30/2017
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
ms.openlocfilehash: 32de7f7e38195271e179d4fae3884b7a39f37c45
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868089"
---
# <a name="how-to-save-files-using-the-savefiledialog-component"></a>Nasıl Yapılır: SaveFileDialog Bileşenini Kullanarak Dosyaları Kaydetme

<xref:System.Windows.Forms.SaveFileDialog> bileşeni, kullanıcıların dosya sistemine gözatmasına ve kaydedilecek dosyaları seçmesine olanak tanır. İletişim kutusu, iletişim kutusunda kullanıcının seçtiği dosyanın yolunu ve adını döndürür. Ancak, dosyaları diske gerçekten yazmak için kodu yazmanız gerekir.

### <a name="to-save-a-file-using-the-savefiledialog-component"></a>SaveFileDialog bileşenini kullanarak bir dosyayı kaydetmek için

- **Dosya Kaydet** iletişim kutusunu görüntüleyin ve Kullanıcı tarafından seçilen dosyayı kaydetmek için bir yöntem çağırın.

  Dosyayı kaydetmek için <xref:System.Windows.Forms.SaveFileDialog> bileşenin <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> metodunu kullanın. Bu yöntem, size yazabileceğiniz <xref:System.IO.Stream> bir nesne sağlar.

  Aşağıdaki örnek, dosyanın adını almak için <xref:System.Windows.Forms.DialogResult> özelliğini ve dosyayı kaydetmek için <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> yöntemini kullanır. <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> yöntemi, dosyayı dosyasına yazmak için bir akış sağlar.

  Aşağıdaki örnekte, kendisine atanmış bir görüntü içeren <xref:System.Windows.Forms.Button> bir denetim vardır. Düğmeye tıkladığınızda, Type. gif,. JPEG ve. BMP dosyalarına izin veren bir filtre ile birlikte <xref:System.Windows.Forms.SaveFileDialog> bileşen oluşturulur. Dosya Kaydet iletişim kutusunda bu türden bir dosya seçiliyse düğmenin görüntüsü kaydedilir.

  > [!IMPORTANT]
  > <xref:System.Windows.Forms.FileDialog.FileName%2A> özelliğini almak veya ayarlamak için, derlemeniz <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> sınıfı tarafından verilen ayrıcalık düzeyini gerektirir. Kısmi güven bağlamında çalıştırıyorsanız, işlem yetersiz ayrıcalıklar nedeniyle bir özel durum oluşturabilir. Daha fazla bilgi için bkz. [kod erişimi güvenlik temelleri](../../misc/code-access-security-basics.md).

  Örnek, formunuzun <xref:System.Windows.Forms.ButtonBase.Image%2A> özelliği. gif,. jpeg veya. bmp dosyası olarak ayarlanan <xref:System.Windows.Forms.Button> denetimine sahip olduğunu varsayar.

  > [!NOTE]
  > <xref:System.Windows.Forms.FileDialog> sınıfın <xref:System.Windows.Forms.FileDialog.FilterIndex%2A> özelliği (devralma nedeniyle <xref:System.Windows.Forms.SaveFileDialog> sınıfının bir parçası) tek tabanlı bir dizin kullanır. Verileri belirli bir biçimde kaydetmek için kod yazıyorsanız (örneğin, bir dosyayı düz metin ve ikili biçimde kaydetme), bu önemlidir. Bu özellik aşağıdaki örnekte öne çıkmıştır.

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

  (Görsel C# ve görsel C++) Olay işleyicisini kaydetmek için formun oluşturucusuna aşağıdaki kodu yerleştirin.

  ```csharp
  this.button2.Click += new System.EventHandler(this.button2_Click);
  ```

  ```cpp
  this->button2->Click += gcnew
      System::EventHandler(this, &Form1::button2_Click);
  ```

  Dosya akışları yazma hakkında daha fazla bilgi için bkz. <xref:System.IO.FileStream.BeginWrite%2A> ve <xref:System.IO.FileStream.Write%2A>.

  > [!NOTE]
  > <xref:System.Windows.Forms.RichTextBox> denetimi gibi bazı denetimlerin dosyaları kaydetme yeteneği vardır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.SaveFileDialog>
- [SaveFileDialog Bileşeni](savefiledialog-component-windows-forms.md)
