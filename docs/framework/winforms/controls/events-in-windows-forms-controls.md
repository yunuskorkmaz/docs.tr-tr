---
title: Windows Forms Denetimlerindeki Olaylar
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], custom controls (using code)
- custom controls [Windows Forms], events overview (using code)
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
ms.openlocfilehash: 41ad95de7a65dbd0cb3a0d1af8f5c8cb00c1ccdd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59215897"
---
# <a name="events-in-windows-forms-controls"></a>Windows Forms Denetimlerindeki Olaylar
Bir Windows Forms denetimi altmış daha olaylardan devralan <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Bunlar <xref:System.Windows.Forms.Control.Paint> çizilecek denetim neden olan olayı, bir pencere gibi görüntülemek için ilgili olayları <xref:System.Windows.Forms.Control.Resize> ve <xref:System.Windows.Forms.Control.Layout> olayları ve alt düzey fare ve klavye olayları. Alt düzey bazı olaylar tarafından oluşturulan <xref:System.Windows.Forms.Control> gibi anlamsal olaylara <xref:System.Windows.Forms.Control.Click> ve <xref:System.Windows.Forms.Control.DoubleClick>. Devralınan olaylar hakkında daha fazla ayrıntı için bkz: <xref:System.Windows.Forms.Control>.  
  
 Özel denetiminizi devralınan olay işlevi geçersiz kılması gerekiyorsa, devralınan geçersiz kılma `On` *EventName* yerine temsilci ekleme yöntemi. .NET Framework'teki olay modeline alışkın değilseniz bkz [Raising Events bir bileşenin](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [OnPaint Yöntemini Geçersiz Kılma](overriding-the-onpaint-method.md)
- [Kullanıcı Girişini İşleme](handling-user-input.md)
- [Olay Tanımlama](defining-an-event-in-windows-forms-controls.md)
- [Olaylar](../../../standard/events/index.md)
