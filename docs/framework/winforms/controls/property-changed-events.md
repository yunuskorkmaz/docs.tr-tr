---
title: Özellik Değişti Olayları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property changes (using code)
- properties [Windows Forms], changes
ms.assetid: 268039ec-5aaa-4d76-b902-acccb036c850
ms.openlocfilehash: d02c6f6f3b5a3add7d78f6c3813a36d08b2b9cb3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54584863"
---
# <a name="property-changed-events"></a>Özellik Değişti Olayları
Adlı bir özellik bildirimleri göndermek için denetim istiyorsanız *PropertyName* değişiklikleri tanımlayın adlı bir olay *PropertyName* `Changed` ve adlı bir yöntem `On` *PropertyName* `Changed` , olayını başlatır. Windows Forms'ta adlandırma kuralı kelimenin sonuna eklenecek olan *değiştirilen* özelliğinin adı. Özellik değişti olayları için ilişkili olay temsilci türü <xref:System.EventHandler>, ve olay veri türü <xref:System.EventArgs>. Temel sınıf <xref:System.Windows.Forms.Control> gibi birçok özellik değişti olayları tanımlar <xref:System.Windows.Forms.Control.BackColorChanged>, <xref:System.Windows.Forms.Control.BackgroundImageChanged>, <xref:System.Windows.Forms.Control.FontChanged>, <xref:System.Windows.Forms.Control.LocationChanged>ve diğerleri. Olaylar hakkında bilgi için bkz: [olayları](../../../../docs/standard/events/index.md) ve [Windows Forms denetimlerindeki olaylar](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md).  
  
 Özellik değişti olayları kullanışlı olduğu bunlara yanıt olay işleyicileri eklemek bir denetim tüketicilerinin sağlarlar. Denetiminiz bilmemektedir özelliği değiştirilmiş bir olay yanıt vermesi, karşılık gelen geçersiz kılma `On` *PropertyName* `Changed` bir temsilci olaya eklemek yerine yöntemi. Bir denetimin diğer özelliklerini güncelleştirerek veya bazılarını veya tümünü, çizim yüzeyini yeniden tarafından bir özellik değişti olayı için genellikle yanıt verir.  
  
 Aşağıdaki örnekte gösterildiği nasıl `FlashTrackBar` özel denetiminin vereceği yanıtı devraldığı özellik değişti olayları bazılarının <xref:System.Windows.Forms.Control>. Tam bir örnek için bkz [nasıl yapılır: İlerleme durumunu gösteren Windows Forms denetimi oluşturma](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#2)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Olaylar](../../../../docs/standard/events/index.md)
- [Windows Forms Denetimlerindeki Olaylar](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)
- [Windows Forms Denetimlerindeki Özellikler](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)
