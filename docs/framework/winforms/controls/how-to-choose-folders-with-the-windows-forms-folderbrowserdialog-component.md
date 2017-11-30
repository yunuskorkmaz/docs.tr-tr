---
title: "Nasıl yapılır: Windows Forms FolderBrowserDialog Bileşeni ile Klasörleri Seçme"
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
- directories [Windows Forms], choosing
- FolderBrowserDialog component [Windows Forms], choosing directories
- folders [Windows Forms], selecting
- folders [Windows Forms], choosing
- directories [Windows Forms], selecting
ms.assetid: 4593670e-7c7d-4661-b46b-4ffb63258adb
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0824fb70fa67628326af38ff7fb5e6c097a0378c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component"></a>Nasıl yapılır: Windows Forms FolderBrowserDialog Bileşeni ile Klasörleri Seçme
Genellikle, oluşturduğunuz Windows uygulamaları içinden en sık dosyaları kümesini kaydetmek için bir klasör seçmek için kullanıcılara sor gerekecektir. Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> bileşeni, bu görevi kolayca gerçekleştirmenize olanak sağlar.  
  
### <a name="to-choose-folders-with-the-folderbrowserdialog-component"></a>FolderBrowserDialog bileşeni ile klasörleri seçmek için  
  
1.  Bir yordamda denetleyin <xref:System.Windows.Forms.FolderBrowserDialog> bileşenin <xref:System.Windows.Forms.Form.DialogResult%2A> değerini alın ve iletişim kutusunun nasıl kapatıldığını görmek için özellik <xref:System.Windows.Forms.FolderBrowserDialog> bileşenin <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> özelliği.  
  
2.  İletişim kutusu ağaç görünümü içinde görünür kümesi en üstteki klasörü gerekiyorsa ayarlamak <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> üyesi alır özelliği <xref:System.Environment.SpecialFolder> numaralandırması.  
  
3.  Ayrıca, ayarlayabileceğiniz <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> metin dizesini belirtir özelliği klasör tarayıcı ağaç görünümü üstünde görünür.  
  
     Aşağıdaki örnekte <xref:System.Windows.Forms.FolderBrowserDialog> bileşen zaman Visual Studio'da bir proje oluşturun ve içine kaydetmek için bir klasör seçmek için istenir benzer bir klasör seçmek için kullanılır. Bu örnekte, klasör adı sonra görüntülenen bir <xref:System.Windows.Forms.TextBox> form üzerinde denetim. Düzenlenebilir bir alanı gibi konuma yerleştirmek için iyi bir fikirdir bir <xref:System.Windows.Forms.TextBox> denetlemek, böylece kullanıcılar kendi seçim hatası veya diğer sorunları durumunda düzenleyebilirsiniz. Bu örnek bir formla varsayar bir <xref:System.Windows.Forms.FolderBrowserDialog> bileşeni ve bir <xref:System.Windows.Forms.TextBox> denetim.  
  
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
    >  Bu sınıf kullanmak için derleme ayrıcalık düzeyi verilen tarafından gerektiriyor <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> parçasıdır özelliği, <xref:System.Security.Permissions.FileIOPermissionAccess> numaralandırması. Kısmi güven bağlamda çalıştırıyorsanız, işlem nedeniyle yeterli ayrıcalığa sahip bir özel durum. Daha fazla bilgi için bkz: [kod erişim güvenliği Temelleri](../../../../docs/framework/misc/code-access-security-basics.md).  
  
 Dosyaları kaydetme hakkında daha fazla bilgi için bkz: [nasıl yapılır: SaveFileDialog bileşenini kullanarak dosyaları kaydetme](../../../../docs/framework/winforms/controls/how-to-save-files-using-the-savefiledialog-component.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.FolderBrowserDialog>  
 [FolderBrowserDialog bileşenine genel bakış (Windows Forms)](../../../../docs/framework/winforms/controls/folderbrowserdialog-component-overview-windows-forms.md)  
 [FolderBrowserDialog bileşeni](../../../../docs/framework/winforms/controls/folderbrowserdialog-component-windows-forms.md)
