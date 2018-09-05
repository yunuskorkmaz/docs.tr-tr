---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Formları Denetimleri için Erişim Tuşları Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], access keys
- Button control [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- mnemonics [Windows Forms], adding to dialog box controls
- ampersand character in shortcut key
- Windows Forms controls, access keys
- examples [Windows Forms], controls
- Text property [Windows Forms], specifying access keys for controls
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
- ALT key
ms.assetid: 4c374c4c-4ca9-4a68-ac96-9dc3ab0f518a
ms.openlocfilehash: d077de1636888f0e3b763344206692fee2cb2296
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43502981"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Formları Denetimleri için Erişim Tuşları Oluşturma
Bir *erişim anahtarı* menü, menü öğesi ya da bir düğme gibi bir denetimin etiket metninin altı çizili karakterdir. Bunu, "bir düğme önceden tanımlanmış bir erişim anahtarı ile birlikte ALT tuşuna basarak tıklayın" kullanıcının sağlar. Örneğin, bir form yazdırma için bir yordam bir düğme çalıştırır ve bu nedenle kendi `Text` "P" neden harfin altı çizili "P" düğme metni çalışma zamanında harf önce "ve işareti ekleme Yazdır," (&) özelliğini ayarlayın. Kullanıcı, ilişkili düğme ALT + P tuşlarına basarak komut çalıştırabilirsiniz. Bir erişim anahtarı için alamayan bir denetim sahip olamaz.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-an-access-key-for-a-control"></a>Bir denetim için erişim anahtarı oluşturmak için  
  
1.  İçinde **özellikleri** penceresinde `Text` özellik erişim tuşu olacak harfi önce ve işareti içeren bir dize (&). Harfi "P" erişim anahtarı olarak ayarlamak için örneğin **& Yazdır** kılavuza.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Button>  
 [Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt Verme](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [Nasıl yapılır: Windows Forms Denetimi Tarafından Görüntülenen Metni Ayarlama](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
