---
title: Süreölçer Bileşenine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- Timer
helpviewer_keywords:
- Timer component [Windows Forms], about Timer components
- timers [Windows Forms], about timers
ms.assetid: e672c05b-a8b6-4b26-9e4d-9223aa9e3873
ms.openlocfilehash: 39bc3c8cda06a62eb40b042e46cbd070a82cce01
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="timer-component-overview-windows-forms"></a>Süreölçer Bileşenine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.Timer> düzenli aralıklarla bir olay başlatır bir bileşenidir. Bu bileşen, bir Windows Forms ortamı için tasarlanmıştır. Bir sunucu ortamı için uygun bir süreölçer gerekirse bkz [sunucu tabanlı zamanlayıcılar giriş](http://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).  
  
## <a name="key-properties-methods-and-events"></a>Anahtar özellikleri, yöntemleri ve olayları  
 Uzunluklarını tarafından tanımlanan <xref:System.Windows.Forms.Timer.Interval%2A> özelliği, değeri olan milisaniye cinsinden. Bileşen etkinleştirildiğinde, <xref:System.Windows.Forms.Timer.Tick> olayı her aralığı. Burada yürütülmek üzere kod eklemek budur. Daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms süreölçer bileşeni ile ayarlama aralıklarda yordamları çalıştırmak](../../../../docs/framework/winforms/controls/run-procedures-at-set-intervals-with-wf-timer-component.md). Anahtar yöntemleri <xref:System.Windows.Forms.Timer> bileşeni olan <xref:System.Windows.Forms.Timer.Start%2A> ve <xref:System.Windows.Forms.Timer.Stop%2A>, açma ve kapatma Zamanlayıcı açın. Zamanlayıcı kapalı olduğunda sıfırlar; duraklatmak için bir yolu yoktur bir <xref:System.Windows.Forms.Timer> bileşeni.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Timer>  
 [Süreölçer Bileşeni](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)  
 [Windows Forms Süreölçer Bileşeninin Aralık Özelliğiyle İlgili Sınırlamalar](../../../../docs/framework/winforms/controls/limitations-of-the-timer-component-interval-property.md)
