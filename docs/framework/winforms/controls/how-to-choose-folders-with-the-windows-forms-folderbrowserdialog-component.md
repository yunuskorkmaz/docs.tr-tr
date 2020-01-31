---
title: FolderBrowserDialog Bileşeni ile klasörleri seçme
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
ms.openlocfilehash: 313388442101f341cfed366143f3c9669fb45cbd
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742234"
---
# <a name="how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component"></a>Nasıl yapılır: Windows Forms FolderBrowserDialog Bileşeni ile Klasörleri Seçme

Genellikle, oluşturduğunuz Windows uygulamalarında, bir dosya kümesini kaydetmek için kullanıcılardan bir klasör seçmesini istemek gerekecektir. Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> bileşeni, bu görevi kolayca gerçekleştirmenize olanak tanır.

### <a name="to-choose-folders-with-the-folderbrowserdialog-component"></a>FolderBrowserDialog Bileşeni ile klasörleri seçmek için

1. Bir yordamda, iletişim kutusunun nasıl kapatıldığını görmek ve <xref:System.Windows.Forms.FolderBrowserDialog> bileşeninin <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> özelliğinin değerini almak için <xref:System.Windows.Forms.FolderBrowserDialog> bileşeninin <xref:System.Windows.Forms.Form.DialogResult%2A> özelliğini denetleyin.

2. İletişim kutusunun ağaç görünümünde görünecek en üstteki klasörü ayarlamanız gerekiyorsa, <xref:System.Environment.SpecialFolder> numaralandırmanın bir üyesini alan <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> özelliğini ayarlayın.

3. Ayrıca, klasör tarayıcısı ağaç görünümünün üst kısmında görünen metin dizesini belirten <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> özelliğini ayarlayabilirsiniz.

    Aşağıdaki örnekte, <xref:System.Windows.Forms.FolderBrowserDialog> bileşeni, Visual Studio 'da bir proje oluştururken olduğu gibi bir klasörü seçmek için kullanılır ve dosyayı kaydetmek için bir klasör seçmeniz istenir. Bu örnekte, klasör adı form üzerindeki bir <xref:System.Windows.Forms.TextBox> denetiminde görüntülenir. Bir <xref:System.Windows.Forms.TextBox> denetimi gibi düzenlenebilir bir alana konum yerleştirmek iyi bir fikirdir. böylece kullanıcılar, hata durumunda veya başka sorunlar durumunda kendi seçimini düzenleyebilir. Bu örnekte, bir <xref:System.Windows.Forms.FolderBrowserDialog> bileşeni ve bir <xref:System.Windows.Forms.TextBox> denetimi olan bir form varsayılır.

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
    > Bu sınıfı kullanmak için, derlemeniz <xref:System.Security.Permissions.FileIOPermissionAccess> numaralandırmanın bir parçası olan <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> özelliği tarafından verilen bir ayrıcalık düzeyi gerektirir. Kısmi güven bağlamında çalıştırıyorsanız, işlem yetersiz ayrıcalıklar nedeniyle bir özel durum oluşturabilir. Daha fazla bilgi için bkz. [kod erişimi güvenlik temelleri](../../misc/code-access-security-basics.md).

Dosyaları kaydetme hakkında bilgi için bkz. [nasıl yapılır: SaveFileDialog bileşenini kullanarak dosyaları kaydetme](how-to-save-files-using-the-savefiledialog-component.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [FolderBrowserDialog Bileşenine Genel Bakış (Windows Forms)](folderbrowserdialog-component-overview-windows-forms.md)
- [FolderBrowserDialog Bileşeni](folderbrowserdialog-component-windows-forms.md)
