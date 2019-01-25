---
title: 'Nasıl yapılır: Bir Windows Forms etiket denetimini içeriğini sığdıracak şekilde boyutlandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- captions [Windows Forms], sizing
- sizing controls
- size [Windows Forms], controls
- labels [Windows Forms], sizing to fit contents
- Label control [Windows Forms], sizing to fit contents
ms.assetid: 99648964-63b2-438c-980e-d24103ad602b
ms.openlocfilehash: 74947e529a472c9e9a681fcb436ce8aff990c0af
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640413"
---
# <a name="how-to-size-a-windows-forms-label-control-to-fit-its-contents"></a>Nasıl yapılır: Bir Windows Forms etiket denetimini içeriğini sığdıracak şekilde boyutlandırma
Windows Forms <xref:System.Windows.Forms.Label> denetimi tek satır veya çok satırlı olabilir ve boyutunu ya da düzeltilmesi veya otomatik olarak kendini kendi açıklamalı alt yazı uyum sağlayacak şekilde boyutlandırabilirsiniz. <xref:System.Windows.Forms.Label.AutoSize%2A> Özellik başlığı çalışma zamanında değişir, özellikle yararlı olan daha büyük veya küçük resim yazıları, sığması için denetimleri boyut yardımcı olur.  
  
### <a name="to-make-a-label-control-resize-dynamically-to-fit-its-contents"></a>Bir etiket denetimini içeriğini sığdıracak şekilde dinamik olarak yeniden boyutlandırma yapma  
  
1.  Ayarlama, <xref:System.Windows.Forms.Label.AutoSize%2A> özelliğini `true`.  
  
 Varsa <xref:System.Windows.Forms.Label.AutoSize%2A> ayarlanır `false`, belirtilen sözcükleri <xref:System.Windows.Forms.Label.Text%2A> özelliği, mümkünse sonraki satıra kaydırma, ancak denetim yok büyüyecektir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Windows Forms etiket denetimleri ile erişim tuşları oluşturma](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md)
- [Etiket Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)
- [Etiket Denetimi](../../../../docs/framework/winforms/controls/label-control-windows-forms.md)
