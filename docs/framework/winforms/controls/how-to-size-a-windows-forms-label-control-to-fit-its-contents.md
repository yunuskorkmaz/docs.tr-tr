---
title: Etiket denetimini Içeriğini sığacak şekilde boyutlandır
ms.date: 03/30/2017
helpviewer_keywords:
- captions [Windows Forms], sizing
- sizing controls
- size [Windows Forms], controls
- labels [Windows Forms], sizing to fit contents
- Label control [Windows Forms], sizing to fit contents
ms.assetid: 99648964-63b2-438c-980e-d24103ad602b
ms.openlocfilehash: 6a563693feaa5074f5d13f0b82cc4d0305a79c23
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743778"
---
# <a name="how-to-size-a-windows-forms-label-control-to-fit-its-contents"></a>Nasıl yapılır: Windows Forms Etiket Denetimini İçeriğini Sığdıracak Şekilde Boyutlandırma
Windows Forms <xref:System.Windows.Forms.Label> denetimi tek satırlık veya çok satırlı olabilir ve boyut olarak sabitlenebilir ya da otomatik olarak kendi başlık yazısına sığacak şekilde yeniden boyutlandırılabilir. <xref:System.Windows.Forms.Label.AutoSize%2A> özelliği, daha büyük veya daha küçük açıklamalı alt yazıların sığması için denetimleri boyutlandırmanıza yardımcı olur. Bu, özellikle başlık çalışma zamanında değişliyorsa kullanışlıdır.  
  
### <a name="to-make-a-label-control-resize-dynamically-to-fit-its-contents"></a>Bir etiket denetimini, içeriğini sığdırmak için dinamik olarak yeniden boyutlandırmak için  
  
1. <xref:System.Windows.Forms.Label.AutoSize%2A> özelliğini `true`olarak ayarlayın.  
  
 <xref:System.Windows.Forms.Label.AutoSize%2A> `false`olarak ayarlanırsa, <xref:System.Windows.Forms.Label.Text%2A> özelliğinde belirtilen sözcükler mümkünse sonraki satıra kaydırılır, ancak denetim büyütülecektir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Windows Forms Etiket Denetimleri ile Erişim Tuşları Oluşturma](how-to-create-access-keys-with-windows-forms-label-controls.md)
- [Etiket Denetimine Genel Bakış](label-control-overview-windows-forms.md)
- [Etiket Denetimi](label-control-windows-forms.md)
