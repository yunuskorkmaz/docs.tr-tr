---
title: 'Nasıl yapılır: Windows Forms Denetimleri için Erişim Tuşları Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], access keys
- Button control [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- mnemonics [Windows Forms], adding to dialog box controls
- mnemonics
- ampersand character in shortcut key
- Windows Forms controls, access keys
- examples [Windows Forms], controls
- Text property [Windows Forms], specifying access keys for controls
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
- ALT key
ms.assetid: 4faa0991-28ec-4eca-91db-51dc2cd6a7ac
ms.openlocfilehash: 53ffd3632ff3e1179a72f1e2bfe4ea366e28b0f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-access-keys-for-windows-forms-controls"></a>Nasıl yapılır: Windows Forms Denetimleri için Erişim Tuşları Oluşturma
Bir *erişim tuşu* altı çizili bir karakter menü, menü öğesi ya da bir düğmesi gibi denetimin etiket metnini,'dir. Bir erişim anahtarı ile kullanıcı "bir düğme önceden tanımlanmış erişim anahtarı ile birlikte ALT tuşuna basarak tıklatabilirsiniz". Örneğin, bir düğme bir form yazdırma için bir yordam çalıştırıyorsa ve bu nedenle, `Text` harf "P" "düğmesi metni çalışma zamanında çizilmesini P" harfi neden olmadan önce ve işareti ekleme özelliği "Yazdır," ayarlanır. Kullanıcı ilişkili düğme ALT + S tuşlarına basarak komutu çalıştırabilirsiniz. Odağı alamayan bir denetim için erişim tuşu sahip olamaz.  
  
### <a name="to-create-an-access-key-for-a-control"></a>Bir denetim için erişim anahtarı oluşturmak için  
  
1.  Ayarlama `Text` özelliği kısayol olur harf önce ve işareti içeren bir dize için (&).  
  
    ```vb  
    ' Set the letter "P" as an access key.  
    Button1.Text = "&Print"  
    ```  
  
    ```csharp  
    // Set the letter "P" as an access key.  
    button1.Text = "&Print";  
    ```  
  
    ```cpp  
    // Set the letter "P" as an access key.  
    button1->Text = "&Print";  
    ```  
  
    > [!NOTE]
    >  Erişim anahtarı oluşturmadan ve işareti bir başlık eklemek için iki ve işaretlerini dahil (& &). Tek bir ve işareti yazısının görüntülenir ve hiçbir karakter çizilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Button>  
 [Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt Verme](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [Nasıl yapılır: Windows Forms Denetimi Tarafından Görüntülenen Metni Ayarlama](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
