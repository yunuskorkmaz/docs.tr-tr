---
title: 'Nasıl yapılır: Windows Forms RichTextBox Denetimine Dosyaları Yükleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- text boxes [Windows Forms], displaying files
- examples [Windows Forms], text boxes
- .rtf files [Windows Forms], opening in RichTextBox control
- RTF files [Windows Forms], opening in RichTextBox control
- text files [Windows Forms], displaying in RichTextBox control
- .rtf files [Windows Forms], displaying in RichTextBox control
- RichTextBox control [Windows Forms], opening files
- RTF files [Windows Forms], displaying in RichTextBox control
ms.assetid: c03451be-f285-4428-a71a-c41e002cc919
ms.openlocfilehash: 0456190f160c555dcc8ce5553674eee2cb73db8d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59086786"
---
# <a name="how-to-load-files-into-the-windows-forms-richtextbox-control"></a>Nasıl yapılır: Windows Forms RichTextBox Denetimine Dosyaları Yükleme
Windows Forms <xref:System.Windows.Forms.RichTextBox> denetimi, bir düz metin, Unicode düz metin veya zengin metin biçimi (RTF) dosyasını görüntüleyebilirsiniz. Bunu yapmak için çağrı <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> yöntemi. Ayrıca <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> yöntemi bir akıştan verileri yüklenemedi. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.RichTextBox.LoadFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.  
  
### <a name="to-load-a-file-into-the-richtextbox-control"></a>RichTextBox denetimine bir dosya yüklemek için  
  
1.  Kullanılarak açılmasını dosyasının yolunu belirlemek <xref:System.Windows.Forms.OpenFileDialog> bileşeni. Genel bakış için bkz. [OpenFileDialog bileşenine genel bakış](openfiledialog-component-overview-windows-forms.md).  
  
2.  Çağrı <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> yöntemi <xref:System.Windows.Forms.RichTextBox> yüklenecek dosyanın ve isteğe bağlı olarak bir dosya türünü belirten denetimi. Aşağıdaki örnekte, yüklenecek dosyanın sınıfından alınmıştır <xref:System.Windows.Forms.OpenFileDialog> bileşenin <xref:System.Windows.Forms.FileDialog.FileName%2A> özelliği. Bir dosya adı yalnızca bağımsız değişken olarak yöntemi çağırın, dosya türü RTF olarak kabul edilir. Başka bir dosya türü belirtmek için bir değerini yöntemi çağırın <xref:System.Windows.Forms.RichTextBoxStreamType> ikinci bağımsız değişken olarak numaralandırması.  
  
     Aşağıdaki örnekte <xref:System.Windows.Forms.OpenFileDialog> bileşeni, bir düğmeye tıklandığında gösterilir. Seçilen dosya sonra açıldı ve görüntülenen <xref:System.Windows.Forms.RichTextBox> denetimi. Bu örnek, bir formda bir düğme bulunur varsayar`btnOpenFile`.  
  
    ```vb  
    Private Sub btnOpenFile_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles btnOpenFile.Click  
         If OpenFileDialog1.ShowDialog() = DialogResult.OK Then  
           RichTextBox1.LoadFile(OpenFileDialog1.FileName, _  
              RichTextBoxStreamType.RichText)  
          End If  
    End Sub  
    ```  
  
    ```csharp  
    private void btnOpenFile_Click(object sender, System.EventArgs e)  
    {  
       if(openFileDialog1.ShowDialog() == DialogResult.OK)  
       {  
         richTextBox1.LoadFile(openFileDialog1.FileName, RichTextBoxStreamType.RichText);  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void btnOpenFile_Click(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          if(openFileDialog1->ShowDialog() == DialogResult::OK)  
          {  
             richTextBox1->LoadFile(openFileDialog1->FileName,  
                RichTextBoxStreamType::RichText);  
          }  
       }  
    ```  
  
     (Visual C# [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.  
  
    ```csharp  
    this.btnOpenFile.Click += new System.EventHandler(this. btnOpenFile_Click);  
    ```  
  
    ```cpp  
    this->btnOpenFile->Click += gcnew   
       System::EventHandler(this, &Form1::btnOpenFile_Click);  
    ```  
  
    > [!IMPORTANT]
    >  Bu işlemi çalıştırmak için derlemenizi ayrıcalık düzeyi verilen tarafından gerekli kılabiliriz <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> sınıfı. Kısmi güven bağlamda çalıştırıyorsanız, işlem yetersiz ayrıcalıklar nedeniyle özel bir durum fırlatabilir. Daha fazla bilgi için [kod erişimi güvenliği Temelleri](../../misc/code-access-security-basics.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.RichTextBox.LoadFile%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox Denetimi](richtextbox-control-windows-forms.md)
- [Windows Forms'ta Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)
