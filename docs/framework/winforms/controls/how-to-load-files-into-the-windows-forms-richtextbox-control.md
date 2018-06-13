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
ms.openlocfilehash: 4d43536cab7806b8cf2de3d63b2d9f7f10024c71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534459"
---
# <a name="how-to-load-files-into-the-windows-forms-richtextbox-control"></a>Nasıl yapılır: Windows Forms RichTextBox Denetimine Dosyaları Yükleme
Windows Forms <xref:System.Windows.Forms.RichTextBox> denetim düz metin, Unicode düz metin veya zengin metin biçimi (RTF) dosyasını görüntüleyebilirsiniz. Bunu yapmak için arama <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> yöntemi. Aynı zamanda <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> bir akışından veri yükleme yöntemi. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.RichTextBox.LoadFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.  
  
### <a name="to-load-a-file-into-the-richtextbox-control"></a>RichTextBox denetimine bir dosya yüklemek için  
  
1.  Kullanılarak açılması için dosyanın yolunu belirlemek <xref:System.Windows.Forms.OpenFileDialog> bileşeni. Genel bir bakış için bkz: [OpenFileDialog bileşenine genel bakış](../../../../docs/framework/winforms/controls/openfiledialog-component-overview-windows-forms.md).  
  
2.  Çağrı <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> yöntemi <xref:System.Windows.Forms.RichTextBox> denetim, yüklemek için dosya ve isteğe bağlı olarak bir dosya türünü belirtme. Aşağıdaki örnekte, yük dosyaya alınırlar <xref:System.Windows.Forms.OpenFileDialog> bileşenin <xref:System.Windows.Forms.FileDialog.FileName%2A> özelliği. Yalnızca bağımsız değişkeni olarak bir dosya adıyla yöntemini çağırırsanız, dosya türü RTF olarak kabul edilir. Başka bir dosya türü belirtmek için değerini yöntemi çağırma <xref:System.Windows.Forms.RichTextBoxStreamType> numaralandırması ikinci bağımsız değişkeni olarak.  
  
     Aşağıdaki örnekte <xref:System.Windows.Forms.OpenFileDialog> bileşen bir düğme tıklatıldığında gösterilir. Seçilen dosya sonra açılır ve görüntülenen <xref:System.Windows.Forms.RichTextBox> denetim. Bu örnek bir biçime sahip bir düğme varsayar`btnOpenFile`.  
  
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
    >  Bu işlem çalıştırmayı derlemenizi ayrıcalık düzeyi verilen tarafından gerektirebilir <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> sınıfı. Kısmi güven bağlamda çalıştırıyorsanız, işlem nedeniyle yeterli ayrıcalığa sahip bir özel durum. Daha fazla bilgi için bkz: [kod erişim güvenliği Temelleri](../../../../docs/framework/misc/code-access-security-basics.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.RichTextBox.LoadFile%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.RichTextBox>  
 [RichTextBox Denetimi](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [Windows Forms'da Kullanılacak Denetimler](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
