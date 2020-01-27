---
title: Denetimlerindeki olaylar
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], custom controls (using code)
- custom controls [Windows Forms], events overview (using code)
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
ms.openlocfilehash: c60713917b9c84aa7fad50fb1c81fc9252149ad6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745759"
---
# <a name="events-in-windows-forms-controls"></a>Windows Forms Denetimlerindeki Olaylar
Windows Forms denetimi <xref:System.Windows.Forms.Control?displayProperty=nameWithType>60 'den fazla olayı devralır. Bunlar, bir denetimin çizilmesine neden olan <xref:System.Windows.Forms.Control.Paint> olayını, <xref:System.Windows.Forms.Control.Resize> ve <xref:System.Windows.Forms.Control.Layout> olayları ve alt düzey fare ve klavye olayları gibi bir pencereyi görüntüleme ile ilgili olayları içerir. Bazı düşük düzey olaylar, <xref:System.Windows.Forms.Control.Click> ve <xref:System.Windows.Forms.Control.DoubleClick>gibi semantik olaylara <xref:System.Windows.Forms.Control> birleştirilir. Devralınan olaylar hakkında daha fazla bilgi için bkz. <xref:System.Windows.Forms.Control>.  
  
 Özel denetiminizin devralınan olay işlevselliğini geçersiz kılması gerekiyorsa, bir temsilci eklemek yerine devralınan `On`*EventName* metodunu geçersiz kılın. .NET Framework olay modelini bilmiyorsanız, bkz. [bir bileşenden olayları yükseltme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [OnPaint Yöntemini Geçersiz Kılma](overriding-the-onpaint-method.md)
- [Kullanıcı Girişini İşleme](handling-user-input.md)
- [Olay Tanımlama](defining-an-event-in-windows-forms-controls.md)
- [Olaylar](../../../standard/events/index.md)
