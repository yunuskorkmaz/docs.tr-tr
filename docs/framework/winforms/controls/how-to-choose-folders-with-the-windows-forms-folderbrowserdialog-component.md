---
title: 'Nasıl yapılır: Windows Forms FolderBrowserDialog bileşeni ile klasörleri seçin'
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
ms.openlocfilehash: 7055875f25aa0f39feb2d944f4b6684c6ae5d9a5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54614699"
---
# <a name="how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component"></a>Nasıl yapılır: Windows Forms FolderBrowserDialog bileşeni ile klasörleri seçin
Genellikle, Windows, içinde oluşturduğunuz uygulamalar, en sık dosya kümesini kaydetmek için bir klasör seçmek için kullanıcılara sor gerekecektir. Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> bileşen kolayca bu görevi gerçekleştirmek sağlar.  
  
### <a name="to-choose-folders-with-the-folderbrowserdialog-component"></a>FolderBrowserDialog bileşeni ile klasörleri seçme  
  
1.  Bir yordamda denetleyin <xref:System.Windows.Forms.FolderBrowserDialog> bileşenin <xref:System.Windows.Forms.Form.DialogResult%2A> iletişim kutusu nasıl kapatıldığı görmek ve değerini almak için özellik <xref:System.Windows.Forms.FolderBrowserDialog> bileşenin <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> özelliği.  
  
2.  İletişim kutusunun ağacı görünümü içinde görünecek kümesi en üstteki klasöre ihtiyacınız varsa, ayarlayın <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> üyesi özelliği <xref:System.Environment.SpecialFolder> sabit listesi.  
  
3.  Ayrıca, ayarlayabileceğiniz <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> metin dizesini belirtir. özellik, klasör tarayıcı ağaç görünümü üst kısmında görünür.  
  
     Aşağıdaki örnekte <xref:System.Windows.Forms.FolderBrowserDialog> bileşen ne zaman Visual Studio'da bir proje oluşturun ve içine kaydetmek için bir klasör seçmeniz istenir benzer bir klasör seçmek için kullanılır. Bu örnekte, klasör adı ardından görüntülenen bir <xref:System.Windows.Forms.TextBox> form denetimi. Konumun düzenlenebilir bir alanda gibi yerleştirmek için iyi bir fikirdir bir <xref:System.Windows.Forms.TextBox> denetlemek ve böylece kullanıcılar kendi seçimi hata veya diğer sorunları durumunda düzenleyebilirsiniz. Bu örnek bir formla varsayar bir <xref:System.Windows.Forms.FolderBrowserDialog> bileşeni ve bir <xref:System.Windows.Forms.TextBox> denetimi.  
  
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
    >  Bu sınıf kullanmak için ayrıcalık düzeyi verilen tarafından derlemeyi <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> parçası olan özelliği, <xref:System.Security.Permissions.FileIOPermissionAccess> sabit listesi. Kısmi güven bağlamda çalıştırıyorsanız, işlem yetersiz ayrıcalıklar nedeniyle özel bir durum fırlatabilir. Daha fazla bilgi için [kod erişimi güvenliği Temelleri](../../../../docs/framework/misc/code-access-security-basics.md).  
  
 Dosyaları kaydetme hakkında daha fazla bilgi için bkz: [nasıl yapılır: SaveFileDialog bileşenini kullanarak dosyaları kaydetme](../../../../docs/framework/winforms/controls/how-to-save-files-using-the-savefiledialog-component.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.FolderBrowserDialog>
- [FolderBrowserDialog Bileşenine Genel Bakış (Windows Forms)](../../../../docs/framework/winforms/controls/folderbrowserdialog-component-overview-windows-forms.md)
- [FolderBrowserDialog Bileşeni](../../../../docs/framework/winforms/controls/folderbrowserdialog-component-windows-forms.md)
