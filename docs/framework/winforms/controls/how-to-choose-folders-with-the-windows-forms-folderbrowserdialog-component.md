---
title: FolderBrowserDialog Bileşeni ile klasörleri seçme
description: Kullanıcıların bir klasör seçmesini istemek için oluşturduğunuz Windows uygulamalarında Windows Forms FolderBrowserDialog bileşenini nasıl kullanacağınızı öğrenin.
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
ms.openlocfilehash: 11d01bbaec3b82bc221960ebab5e33ca1aa302db
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903681"
---
# <a name="how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component"></a>Nasıl yapılır: Windows Forms FolderBrowserDialog Bileşeni ile Klasörleri Seçme

Genellikle, oluşturduğunuz Windows uygulamalarında, bir dosya kümesini kaydetmek için kullanıcılardan bir klasör seçmesini istemek gerekecektir. Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> bileşeni bu görevi kolayca gerçekleştirmenize olanak tanır.

### <a name="to-choose-folders-with-the-folderbrowserdialog-component"></a>FolderBrowserDialog Bileşeni ile klasörleri seçmek için

1. Bir yordamda, <xref:System.Windows.Forms.FolderBrowserDialog> <xref:System.Windows.Forms.Form.DialogResult%2A> iletişim kutusunun nasıl kapatıldığını görmek ve bileşen özelliğinin değerini almak için bileşenin özelliğini denetleyin <xref:System.Windows.Forms.FolderBrowserDialog> <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> .

2. İletişim kutusunun ağaç görünümünde görünecek en üstteki klasörü ayarlamanız gerekirse, <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> sabit listesinin bir üyesini alan özelliğini ayarlayın <xref:System.Environment.SpecialFolder> .

3. Ayrıca, <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> klasör tarayıcısı ağaç görünümünün en üstünde görünen metin dizesini belirten özelliğini de ayarlayabilirsiniz.

    Aşağıdaki örnekte, <xref:System.Windows.Forms.FolderBrowserDialog> bileşeni, Visual Studio 'da bir proje oluştururken olduğu gibi bir klasörü seçmek için kullanılır ve dosyayı kaydetmek için bir klasör seçmeniz istenir. Bu örnekte, klasör adı <xref:System.Windows.Forms.TextBox> form üzerindeki bir denetimde görüntülenir. Bu, bir denetim gibi düzenlenebilir bir alana, <xref:System.Windows.Forms.TextBox> kullanıcıların bir hata durumunda veya başka sorunlar durumunda kendi seçimini düzenleyebilmeleri için, konumunu bir şekilde yerleştirmek iyi bir fikir olabilir. Bu örnekte, bir form ve bir denetim içeren bir form varsayılır <xref:System.Windows.Forms.FolderBrowserDialog> <xref:System.Windows.Forms.TextBox> .

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
    > Bu sınıfı kullanmak için, derlemeniz, numaralandırmanın bir parçası olan özelliği tarafından verilen bir ayrıcalık düzeyi gerektirir <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> <xref:System.Security.Permissions.FileIOPermissionAccess> . Kısmi güven bağlamında çalıştırıyorsanız, işlem yetersiz ayrıcalıklar nedeniyle bir özel durum oluşturabilir. Daha fazla bilgi için bkz. [kod erişimi güvenlik temelleri](../../misc/code-access-security-basics.md).

Dosyaları kaydetme hakkında bilgi için bkz. [nasıl yapılır: SaveFileDialog bileşenini kullanarak dosyaları kaydetme](how-to-save-files-using-the-savefiledialog-component.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [FolderBrowserDialog Bileşenine Genel Bakış (Windows Forms)](folderbrowserdialog-component-overview-windows-forms.md)
- [FolderBrowserDialog Bileşeni](folderbrowserdialog-component-windows-forms.md)
