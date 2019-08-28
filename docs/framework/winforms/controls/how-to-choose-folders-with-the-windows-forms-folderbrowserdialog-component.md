---
title: 'Nasıl yapılır: Windows Forms FolderBrowserDialog Bileşeni ile Klasörleri Seçme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- directories [Windows Forms], choosing
- FolderBrowserDialog component [Windows Forms], choosing directories
- folders [Windows Forms], selecting
- folders [Windows Forms], choosing
- directories [Windows Forms], selecting
ms.assetid: 4593670e-7c7d-4661-b46b-4ffb63258adb
ms.openlocfilehash: fc19ea466f535f783d3b0537a973ce41c223902d
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046130"
---
# <a name="how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component"></a>Nasıl yapılır: Windows Forms FolderBrowserDialog Bileşeni ile Klasörleri Seçme

Genellikle, oluşturduğunuz Windows uygulamalarında, bir dosya kümesini kaydetmek için kullanıcılardan bir klasör seçmesini istemek gerekecektir. Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> bileşeni bu görevi kolayca gerçekleştirmenize olanak tanır.

### <a name="to-choose-folders-with-the-folderbrowserdialog-component"></a>FolderBrowserDialog Bileşeni ile klasörleri seçmek için

1. Bir yordamda, iletişim kutusunun nasıl <xref:System.Windows.Forms.FolderBrowserDialog> kapatıldığını görmek <xref:System.Windows.Forms.Form.DialogResult%2A> ve <xref:System.Windows.Forms.FolderBrowserDialog> bileşen <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> özelliğinin değerini almak için bileşenin özelliğini denetleyin.

2. İletişim kutusunun ağaç görünümünde görünecek en üstteki klasörü ayarlamanız gerekirse, <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> <xref:System.Environment.SpecialFolder> sabit listesinin bir üyesini alan özelliğini ayarlayın.

3. Ayrıca, klasör tarayıcısı ağaç görünümünün <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> en üstünde görünen metin dizesini belirten özelliğini de ayarlayabilirsiniz.

    Aşağıdaki örnekte, <xref:System.Windows.Forms.FolderBrowserDialog> bileşeni, Visual Studio 'da bir proje oluştururken olduğu gibi bir klasörü seçmek için kullanılır ve dosyayı kaydetmek için bir klasör seçmeniz istenir. Bu örnekte, klasör adı form üzerindeki bir <xref:System.Windows.Forms.TextBox> denetimde görüntülenir. Bu, bir denetim gibi düzenlenebilir bir alana, kullanıcıların bir hata durumunda veya başka sorunlar durumunda <xref:System.Windows.Forms.TextBox> kendi seçimini düzenleyebilmeleri için, konumunu bir şekilde yerleştirmek iyi bir fikir olabilir. Bu örnekte <xref:System.Windows.Forms.FolderBrowserDialog> <xref:System.Windows.Forms.TextBox> , bir form ve bir denetim içeren bir form varsayılır.

    ```vb
    Public Sub ChooseFolder()
        If FolderBrowserDialog1.ShowDialog() = DialogResult.OK Then
            TextBox1.Text = FolderBrowserDialog1.SelectedPath
        End If
    End Sub
    ```

    ```csharp
    public void ChooseFolder()
    {
        if (folderBrowserDialog1.ShowDialog() == DialogResult.OK)
        {
            textBox1.Text = folderBrowserDialog1.SelectedPath;
        }
    }
    ```

    ```cpp
    public:
       void ChooseFolder()
       {
          if (folderBrowserDialog1->ShowDialog() == DialogResult::OK)
          {
             textBox1->Text = folderBrowserDialog1->SelectedPath;
          }
       }
    ```

    > [!IMPORTANT]
    > Bu sınıfı kullanmak için, derlemeniz, <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> <xref:System.Security.Permissions.FileIOPermissionAccess> numaralandırmanın bir parçası olan özelliği tarafından verilen bir ayrıcalık düzeyi gerektirir. Kısmi güven bağlamında çalıştırıyorsanız, işlem yetersiz ayrıcalıklar nedeniyle bir özel durum oluşturabilir. Daha fazla bilgi için bkz. [kod erişimi güvenlik temelleri](../../misc/code-access-security-basics.md).

Dosyaların nasıl kaydedileceği hakkında bilgi için bkz [. nasıl yapılır: Dosyaları SaveFileDialog bileşenini](how-to-save-files-using-the-savefiledialog-component.md)kullanarak kaydedin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [FolderBrowserDialog Bileşenine Genel Bakış (Windows Forms)](folderbrowserdialog-component-overview-windows-forms.md)
- [FolderBrowserDialog Bileşeni](folderbrowserdialog-component-windows-forms.md)
