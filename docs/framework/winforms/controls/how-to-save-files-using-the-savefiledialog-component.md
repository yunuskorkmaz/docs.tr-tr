---
title: 'Nasıl Yapılır: SaveFileDialog Bileşenini Kullanarak Dosyaları Kaydetme'
description: Dosya sistemine gözatıp kaydedilecek dosyaları seçmek için SaveFileDialog bileşenini nasıl kullanacağınızı öğrenin.
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
ms.openlocfilehash: cd773c3d4aa2b907eb09dd87c3fdbe138bf533bb
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904409"
---
# <a name="how-to-save-files-using-the-savefiledialog-component"></a>Nasıl Yapılır: SaveFileDialog Bileşenini Kullanarak Dosyaları Kaydetme

<xref:System.Windows.Forms.SaveFileDialog>Bileşen, kullanıcıların dosya sistemine gözatmasına ve kaydedilecek dosyaları seçmesine olanak sağlar. İletişim kutusu, iletişim kutusunda kullanıcının seçtiği dosyanın yolunu ve adını döndürür. Ancak, dosyaları diske gerçekten yazmak için kodu yazmanız gerekir.

### <a name="to-save-a-file-using-the-savefiledialog-component"></a>SaveFileDialog bileşenini kullanarak bir dosyayı kaydetmek için

- **Dosya Kaydet** iletişim kutusunu görüntüleyin ve Kullanıcı tarafından seçilen dosyayı kaydetmek için bir yöntem çağırın.

  <xref:System.Windows.Forms.SaveFileDialog> <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> Dosyayı kaydetmek için bileşenin metodunu kullanın. Bu yöntem, size <xref:System.IO.Stream> yazabilmenizi sağlayan bir nesne sağlar.

  Aşağıdaki örnek, <xref:System.Windows.Forms.DialogResult> dosyanın adını ve dosyayı kaydetme yöntemini almak için özelliğini kullanır <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> . <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A>Yöntemi, size dosyayı yazmak için bir akış sağlar.

  Aşağıdaki örnekte, <xref:System.Windows.Forms.Button> bir görüntüye atanmış bir denetim vardır. Düğmeye tıkladığınızda bir <xref:System.Windows.Forms.SaveFileDialog> bileşen örneği, Type. gif,. JPEG ve. bmp olan dosyalara izin veren bir filtreyle oluşturulur. Dosya Kaydet iletişim kutusunda bu türden bir dosya seçiliyse düğmenin görüntüsü kaydedilir.

  > [!IMPORTANT]
  > Özelliği almak veya ayarlamak için <xref:System.Windows.Forms.FileDialog.FileName%2A> , derlemeniz sınıf tarafından verilen bir ayrıcalık düzeyi gerektirir <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> . Kısmi güven bağlamında çalıştırıyorsanız, işlem yetersiz ayrıcalıklar nedeniyle bir özel durum oluşturabilir. Daha fazla bilgi için bkz. [kod erişimi güvenlik temelleri](../../misc/code-access-security-basics.md).

  Örnek, formunuzun <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.ButtonBase.Image%2A> özelliği. gif,. jpeg veya. bmp olan bir dosyaya ayarlanmış bir denetime sahip olduğunu varsayar.

  > [!NOTE]
  > <xref:System.Windows.Forms.FileDialog>Sınıfın <xref:System.Windows.Forms.FileDialog.FilterIndex%2A> Özelliği (devralma nedeniyle, sınıfın bir parçası olduğu için <xref:System.Windows.Forms.SaveFileDialog> ) tek tabanlı bir dizin kullanır. Verileri belirli bir biçimde kaydetmek için kod yazıyorsanız (örneğin, bir dosyayı düz metin ve ikili biçimde kaydetme), bu önemlidir. Bu özellik aşağıdaki örnekte öne çıkmıştır.

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

  (Visual C# ve Visual C++) Olay işleyicisini kaydetmek için formun oluşturucusuna aşağıdaki kodu yerleştirin.

  ```csharp
  this.button2.Click += new System.EventHandler(this.button2_Click);
  ```

  ```cpp
  this->button2->Click += gcnew
      System::EventHandler(this, &Form1::button2_Click);
  ```

  Dosya akışları yazma hakkında daha fazla bilgi için bkz <xref:System.IO.FileStream.BeginWrite%2A> <xref:System.IO.FileStream.Write%2A> . ve.

  > [!NOTE]
  > Denetim gibi bazı denetimlerin <xref:System.Windows.Forms.RichTextBox> dosyaları kaydetme yeteneği vardır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.SaveFileDialog>
- [SaveFileDialog Bileşeni](savefiledialog-component-windows-forms.md)
