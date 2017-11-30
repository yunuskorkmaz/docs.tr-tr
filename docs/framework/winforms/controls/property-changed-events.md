---
title: "Özellik Değişti Olayları"
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
helpviewer_keywords:
- custom controls [Windows Forms], property changes (using code)
- properties [Windows Forms], changes
ms.assetid: 268039ec-5aaa-4d76-b902-acccb036c850
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7685891e99f1dcb2ca9e515c7dc6d7730ff0b2e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="property-changed-events"></a>Özellik Değişti Olayları
Adlı bir özellik olduğunda bildirim göndermek için denetiminizi istiyorsanız *PropertyName* değişiklikleri tanımlamak adlı bir olay *PropertyName* `Changed` ve adlı bir yöntem `On` *PropertyName* `Changed` olayını başlatır. Windows Forms'ta adlandırma kuralı word eklenecek olan *değiştirilen* özelliğinin adı. Özellik değişti olayları için ilişkili olay temsilci türüdür <xref:System.EventHandler>, ve olay veri türü <xref:System.EventArgs>. Taban sınıfı <xref:System.Windows.Forms.Control> gibi pek çok özellik değişti olayları tanımlayan <xref:System.Windows.Forms.Control.BackColorChanged>, <xref:System.Windows.Forms.Control.BackgroundImageChanged>, <xref:System.Windows.Forms.Control.FontChanged>, <xref:System.Windows.Forms.Control.LocationChanged>ve diğerleri. Olaylar hakkında bilgi için bkz: [olayları](../../../../docs/standard/events/index.md) ve [Windows Forms denetimlerindeki olaylar](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md).  
  
 Özellik değişti olayları değişiklik yanıt olay işleyicileri eklemek bir denetim tüketicileri izin için faydalıdır. Denetim yükseltir özelliği değiştirilmiş bir olaya yanıt vermesi, karşılık gelen geçersiz kılma `On` *PropertyName* `Changed` olaya bir temsilci ekleme yerine yöntemi. Bir denetim diğer özelliklerini güncelleştirme veya bazılarını veya tümünü, çizim yüzeyini gerçekleşen bir özellik değişti olayı için genellikle yanıt verir.  
  
 Aşağıdaki örnekte gösterildiği nasıl `FlashTrackBar` özel denetim yanıt öğesinden devralınan özellik değişti olayları, bazı <xref:System.Windows.Forms.Control>. Tam bir örnek için bkz: [nasıl yapılır: Windows Forms denetimi olduğunu gösteren ilerlemesi oluşturma](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#2)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Olayları](../../../../docs/standard/events/index.md)  
 [Windows Forms denetimlerindeki olaylar](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)  
 [Windows Forms denetimlerindeki Özellikler](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)
