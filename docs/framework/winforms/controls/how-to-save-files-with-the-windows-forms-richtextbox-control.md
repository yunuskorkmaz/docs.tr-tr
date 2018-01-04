---
title: "Nasıl yapılır: Windows Forms RichTextBox Denetimi Dosyaları Kaydetme"
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
- RTF files [Windows Forms], saving in RichTextBox control
- examples [Windows Forms], text boxes
- saving files [Windows Forms], RichTextBox control
- files [Windows Forms], saving with RichTextBox control
- RichTextBox control [Windows Forms], saving files
- .rtf files [Windows Forms], saving in RichTextBox control
- text files [Windows Forms], saving from RichTextBox control
ms.assetid: 4a58ec19-84d1-4383-9110-298c06adcfca
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7fece6685c1ac71d6ddc152e25c22010e6d579c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-save-files-with-the-windows-forms-richtextbox-control"></a>Nasıl yapılır: Windows Forms RichTextBox Denetimi Dosyaları Kaydetme
Windows Forms <xref:System.Windows.Forms.RichTextBox> denetim birkaç biçimlerinden birinde görüntülediği bilgi yazabilirsiniz:  
  
-   Düz metin  
  
-   Unicode düz metin  
  
-   Zengin metin biçimi (RTF)  
  
-   OLE nesneleri yerine boşluklu RTF  
  
-   OLE nesneleri metinsel gösterimini düz metin  
  
 Bir dosyayı kaydetmek için arama <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> yöntemi. Aynı zamanda **SaveFile** bir akış için verileri kaydetmek için yöntem. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.  
  
### <a name="to-save-the-contents-of-the-control-to-a-file"></a>Denetimin içeriğini bir dosyaya kaydetmek için  
  
1.  Kaydedilecek dosyasının yolunu belirler.  
  
     Gerçek dünya uygulamada Bunu yapmak için genellikle kullanırsınız <xref:System.Windows.Forms.SaveFileDialog> bileşeni. Genel bir bakış için bkz: [SaveFileDialog bileşenine genel bakış](../../../../docs/framework/winforms/controls/savefiledialog-component-overview-windows-forms.md).  
  
2.  Çağrı <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> yöntemi <xref:System.Windows.Forms.RichTextBox> denetim, kaydedin ve isteğe bağlı olarak bir dosya türünü belirtme. Yalnızca bağımsız değişkeni olarak bir dosya adıyla yöntemini çağırırsanız, dosyayı RTF olarak kaydedilir. Başka bir dosya türü belirtmek için değerini yöntemi çağırma <xref:System.Windows.Forms.RichTextBoxStreamType> numaralandırması ikinci bağımsız değişkeni olarak.  
  
     Aşağıdaki örnekte yolunu ayarlamak için zengin metin dosyasının konumunu **Belgelerim** klasör. Windows işletim sistemi çalıştıran bilgisayarların çoğu bu klasör içerdiğini varsayar çünkü bu konumu kullanılır. Bu konumu seçme, güvenli bir şekilde uygulamayı çalıştırmak minimum sistem erişim düzeyleri kullanıcılarla sağlar. Aşağıdaki örnek bir formla varsayar bir <xref:System.Windows.Forms.RichTextBox> denetimi zaten eklendi.  
  
    ```vb  
    Public Sub SaveFile()  
       ' You should replace the bold file name in the   
       ' sample below with a file name of your own choosing.  
       RichTextBox1.SaveFile(System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Testdoc.rtf", _  
          RichTextBoxStreamType.RichNoOleObjs)  
    End Sub  
    ```  
  
    ```csharp  
    public void SaveFile()  
    {  
       // You should replace the bold file name in the   
       // sample below with a file name of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       richTextBox1.SaveFile(System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Testdoc.rtf",  
          RichTextBoxStreamType.RichNoOleObjs);  
    }  
    ```  
  
    ```cpp  
    public:  
       void SaveFile()  
       {  
          // You should replace the bold file name in the   
          // sample below with a file name of your own choosing.  
          richTextBox1->SaveFile(String::Concat  
             (System::Environment::GetFolderPath  
             (System::Environment::SpecialFolder::Personal),  
             "\\Testdoc.rtf"), RichTextBoxStreamType::RichNoOleObjs);  
       }  
    ```  
  
    > [!IMPORTANT]
    >  Bu örnek, dosyanın zaten mevcut değilse yeni bir dosya oluşturur. Bir uygulama bir dosya oluşturmak gerekirse, bu uygulama için klasör oluşturma erişimi olmalıdır. İzinler, erişim denetim listeleri kullanılarak ayarlanır. Dosya zaten varsa, uygulamanın daha düşük ayrıcalık yalnızca yazma erişimi gerekir. Mümkünse, dağıtım sırasında dosyayı oluşturmak ve yalnızca tek bir dosya için okuma yetkisi vermek yerine, erişim için bir klasör oluşturmak için daha güvenlidir. Ayrıca, kök klasöre veya Program dosyaları klasörü kullanıcı klasörleri verileri yazmak amacıyla daha güvenlidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.RichTextBox.SaveFile%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.RichTextBox>  
 [RichTextBox Denetimi](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [Windows Forms'da Kullanılacak Denetimler](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
