---
title: 'Nasıl yapılır: Windows Forms Etiket Denetimini İçeriğini Sığdıracak Şekilde Boyutlandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- captions [Windows Forms], sizing
- sizing controls
- size [Windows Forms], controls
- labels [Windows Forms], sizing to fit contents
- Label control [Windows Forms], sizing to fit contents
ms.assetid: 99648964-63b2-438c-980e-d24103ad602b
ms.openlocfilehash: 110aab0c0826bb4b06e22158afd6af37b5406be4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971203"
---
# <a name="how-to-size-a-windows-forms-label-control-to-fit-its-contents"></a>Nasıl yapılır: Windows Forms Etiket Denetimini İçeriğini Sığdıracak Şekilde Boyutlandırma
Windows Forms <xref:System.Windows.Forms.Label> denetimi tek satır veya çok satırlı olabilir ve boyutunu ya da düzeltilmesi veya otomatik olarak kendini kendi açıklamalı alt yazı uyum sağlayacak şekilde boyutlandırabilirsiniz. <xref:System.Windows.Forms.Label.AutoSize%2A> Özellik başlığı çalışma zamanında değişir, özellikle yararlı olan daha büyük veya küçük resim yazıları, sığması için denetimleri boyut yardımcı olur.  
  
### <a name="to-make-a-label-control-resize-dynamically-to-fit-its-contents"></a>Bir etiket denetimini içeriğini sığdıracak şekilde dinamik olarak yeniden boyutlandırma yapma  
  
1. Ayarlama, <xref:System.Windows.Forms.Label.AutoSize%2A> özelliğini `true`.  
  
 Varsa <xref:System.Windows.Forms.Label.AutoSize%2A> ayarlanır `false`, belirtilen sözcükleri <xref:System.Windows.Forms.Label.Text%2A> özelliği, mümkünse sonraki satıra kaydırma, ancak denetim yok büyüyecektir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Windows Forms etiket denetimleri ile erişim tuşları oluşturma](how-to-create-access-keys-with-windows-forms-label-controls.md)
- [Etiket Denetimine Genel Bakış](label-control-overview-windows-forms.md)
- [Etiket Denetimi](label-control-windows-forms.md)
