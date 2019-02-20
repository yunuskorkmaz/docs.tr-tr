---
title: Windows Forms Denetimlerindeki Olaylar
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], custom controls (using code)
- custom controls [Windows Forms], events overview (using code)
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
ms.openlocfilehash: 56de08f039fd4dee9dcc5a1b3f86cc0e8e577b43
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2019
ms.locfileid: "56442444"
---
# <a name="events-in-windows-forms-controls"></a>Windows Forms Denetimlerindeki Olaylar
Bir Windows Forms denetimi altmış daha olaylardan devralan <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Bunlar <xref:System.Windows.Forms.Control.Paint> çizilecek denetim neden olan olayı, bir pencere gibi görüntülemek için ilgili olayları <xref:System.Windows.Forms.Control.Resize> ve <xref:System.Windows.Forms.Control.Layout> olayları ve alt düzey fare ve klavye olayları. Alt düzey bazı olaylar tarafından oluşturulan <xref:System.Windows.Forms.Control> gibi anlamsal olaylara <xref:System.Windows.Forms.Control.Click> ve <xref:System.Windows.Forms.Control.DoubleClick>. Devralınan olaylar hakkında daha fazla ayrıntı için bkz: <xref:System.Windows.Forms.Control>.  
  
 Özel denetiminizi devralınan olay işlevi geçersiz kılması gerekiyorsa, devralınan geçersiz kılma `On` *EventName* yerine temsilci ekleme yöntemi. .NET Framework'teki olay modeline alışkın değilseniz bkz [Raising Events bir bileşenin](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [OnPaint Yöntemini Geçersiz Kılma](../../../../docs/framework/winforms/controls/overriding-the-onpaint-method.md)
- [Kullanıcı Girişini İşleme](../../../../docs/framework/winforms/controls/handling-user-input.md)
- [Olay Tanımlama](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)
- [Olaylar](../../../../docs/standard/events/index.md)
