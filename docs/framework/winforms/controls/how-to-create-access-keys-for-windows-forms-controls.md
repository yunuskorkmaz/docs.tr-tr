---
title: 'Nasıl yapılır: Windows Forms denetimleri için erişim tuşları oluşturma'
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
ms.openlocfilehash: 5713bc9fa02e6122cc42348160dbe9315e023bc4
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708008"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls"></a>Nasıl yapılır: Windows Forms denetimleri için erişim tuşları oluşturma
Bir *erişim anahtarı* menü, menü öğesi ya da bir düğme gibi bir denetimin etiket metninin altı çizili karakterdir. Bir erişim anahtarı ile kullanıcı "bir düğme önceden tanımlanmış bir erişim anahtarı ile birlikte ALT tuşuna basarak tıklayabilirsiniz". Örneğin, bir form yazdırma için bir yordam bir düğme çalıştırır ve bu nedenle kendi `Text` "P" harfi harfine çalışma zamanında düğmesi metnin altı çizili "P" neden olmadan önce ve işareti ekleme özelliği "Print," ayarlanır. Kullanıcı, ilişkili düğme ALT + P tuşlarına basarak komut çalıştırabilirsiniz. Bir erişim anahtarı için alamayan bir denetim sahip olamaz.  
  
### <a name="to-create-an-access-key-for-a-control"></a>Bir denetim için erişim anahtarı oluşturmak için  
  
1.  Ayarlama `Text` özelliği kısayol olacak harfi önce ve işareti içeren bir dize (&).  
  
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
    >  Bir erişim anahtarı oluşturmadan bir başlık ve işareti eklemek için iki işaretlerini Ekle (& &). Tek bir ve işareti başlığı görüntülenir ve herhangi bir karakter altı çizili olarak gösterilir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.Button>
- [Nasıl yapılır: Windows Forms düğme tıklamalarına yanıt verme](how-to-respond-to-windows-forms-button-clicks.md)
- [Nasıl yapılır: Tarafından görüntülenen metni ayarlama bir Windows Forms denetimi](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
