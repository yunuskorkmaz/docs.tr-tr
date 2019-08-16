---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms Denetimleri için Erişim Tuşları Oluşturma'
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
ms.openlocfilehash: 01bed04483702ba2e62162b675aa1138bc1b0e01
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039517"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Forms Denetimleri için Erişim Tuşları Oluşturma
*Erişim tuşu* , bir menü, menü öğesi veya düğme gibi bir denetimin etiketi içindeki altı çizili bir karakterdir. Daha önceden tanımlanmış erişim anahtarıyla birlikte ALT tuşuna basarak, kullanıcının bir düğmeye tıklamasına olanak sağlar. Örneğin, bir düğme bir formu yazdırmak için bir yordam çalıştırıyorsa ve bu nedenle `Text` özelliği "Yazdır" olarak ayarlanırsa, "p" harfinden önce bir ampersan (&) eklemek "p" harfinin çalışma zamanında düğme metninde altı çizili olmasına neden olur. Kullanıcı, ALT + P tuşlarına basarak düğmeyle ilişkili komutu çalıştırabilir. Odak alamayan bir denetim için erişim anahtarınız olamaz.

## <a name="to-create-an-access-key-for-a-control"></a>Bir denetim için erişim anahtarı oluşturmak için

1. **Özellikler** penceresinde, `Text` özelliği, erişim anahtarı olacak harften önce bir ve işareti (&) içeren bir dizeye ayarlayın. Örneğin, "P" harfini erişim anahtarı olarak ayarlamak için kılavuza **&** yazın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Button>
- [Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt verme](how-to-respond-to-windows-forms-button-clicks.md)
- [Nasıl yapılır: Windows Forms denetimi tarafından görünen metni ayarlama](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
