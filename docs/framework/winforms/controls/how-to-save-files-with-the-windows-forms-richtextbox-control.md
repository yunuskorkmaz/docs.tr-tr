---
title: RichTextBox denetimiyle dosyaları kaydetme
ms.date: 03/30/2017
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
ms.openlocfilehash: a87b93a53347aeba54f944b0f4c455aa272ea243
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744824"
---
# <a name="how-to-save-files-with-the-windows-forms-richtextbox-control"></a>Nasıl yapılır: Windows Forms RichTextBox Denetimi Dosyaları Kaydetme

Windows Forms <xref:System.Windows.Forms.RichTextBox> denetimi, görüntülenen bilgileri birkaç biçimden birinde yazabilir:

- Düz metin

- Unicode düz metin

- Zengin metin biçimi (RTF)

- OLE nesneleri yerine boşluklar içeren RTF

- OLE nesnelerinin metinsel gösterimine sahip düz metin

Bir dosyayı kaydetmek için <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> yöntemini çağırın. Verileri bir akışa kaydetmek için **SaveFile** yöntemini de kullanabilirsiniz. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.

### <a name="to-save-the-contents-of-the-control-to-a-file"></a>Denetimin içeriğini bir dosyaya kaydetmek için

1. Kaydedilecek dosyanın yolunu belirleme.

    Bunu gerçek dünya uygulamasında yapmak için genellikle <xref:System.Windows.Forms.SaveFileDialog> bileşenini kullanırsınız. Genel bakış için bkz. [SaveFileDialog Bileşenine Genel Bakış](savefiledialog-component-overview-windows-forms.md).

2. Kaydedilecek dosyayı ve isteğe bağlı olarak bir dosya türünü belirterek <xref:System.Windows.Forms.RichTextBox> denetiminin <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> yöntemini çağırın. Yöntemini tek bağımsız değişkeni olarak bir dosya adı ile çağırırsanız, Dosya RTF olarak kaydedilir. Başka bir dosya türü belirtmek için, ikinci bağımsız değişkeni olarak <xref:System.Windows.Forms.RichTextBoxStreamType> numaralandırması değeri ile yöntemini çağırın.

    Aşağıdaki örnekte, zengin metin dosyasının konumu için ayarlanan yol **Belgelerim klasörüdür.** Bu konum, Windows işletim sistemini çalıştıran bilgisayarların çoğunun bu klasörü içerdiğini varsaydığı için kullanılır. Bu konumun seçilmesi, en az sistem erişim düzeylerine sahip kullanıcıların uygulamayı güvenle çalıştırmasına olanak tanır. Aşağıdaki örnekte, <xref:System.Windows.Forms.RichTextBox> denetimi zaten eklenmiş bir form varsayılır.

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
    > Bu örnek, dosya zaten yoksa yeni bir dosya oluşturur. Uygulamanın bir dosya oluşturması gerekiyorsa, bu uygulamanın klasör için erişim oluşturması gerekir. İzinler, erişim denetim listeleri kullanılarak ayarlanır. Dosya zaten mevcutsa, uygulamanın daha küçük bir ayrıcalık yalnızca yazma erişimine ihtiyacı vardır. Mümkün olduğunda, dağıtım sırasında dosyanın oluşturulması ve bir klasör için erişim oluşturmak yerine yalnızca tek bir dosyaya okuma erişimi verilmesi daha güvenlidir. Ayrıca, Kullanıcı klasörlerine veri yazmak, kök klasör veya Program Files klasöründen daha güvenlidir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.RichTextBox.SaveFile%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox Denetimi](richtextbox-control-windows-forms.md)
- [Windows Forms'da Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)
