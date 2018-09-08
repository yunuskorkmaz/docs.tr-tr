---
title: Süreölçer Bileşenine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- Timer
helpviewer_keywords:
- Timer component [Windows Forms], about Timer components
- timers [Windows Forms], about timers
ms.assetid: e672c05b-a8b6-4b26-9e4d-9223aa9e3873
ms.openlocfilehash: 6e453f6b7718c6c5be3109f51153a3f5e4b5b6f4
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44136465"
---
# <a name="timer-component-overview-windows-forms"></a>Süreölçer Bileşenine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.Timer> düzenli aralıklarla bir olayı oluşturan bir bileşendir. Bu bileşen, bir Windows Forms ortamı için tasarlanmıştır. Bir sunucu ortamı için uygun olan bir zamanlayıcı gerekirse bkz [sunucu tabanlı zamanlayıcılar giriş](https://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).  
  
## <a name="key-properties-methods-and-events"></a>Anahtar özellikleri, yöntemleri ve olayları  
 Aralıkların uzunluğunu tarafından tanımlanan <xref:System.Windows.Forms.Timer.Interval%2A> özelliği, değeri olan milisaniye cinsinden. Bileşen etkinleştirildiğinde <xref:System.Windows.Forms.Timer.Tick> olayı her aralığı. Burada yürütülecek kodu eklersiniz budur. Daha fazla bilgi için [nasıl yapılır: Windows Forms süreölçer bileşeni ile ayarlama aralıklarda yordamları çalıştırma](../../../../docs/framework/winforms/controls/run-procedures-at-set-intervals-with-wf-timer-component.md). Anahtar yöntemlerini <xref:System.Windows.Forms.Timer> bileşenidir <xref:System.Windows.Forms.Timer.Start%2A> ve <xref:System.Windows.Forms.Timer.Stop%2A>, açma ve kapatma Zamanlayıcı açın. Zamanlayıcı kapalı olduğunda sıfırlar; duraklatmak için bir yolu yoktur bir <xref:System.Windows.Forms.Timer> bileşeni.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Timer>  
 [Süreölçer Bileşeni](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)  
 [Windows Forms Süreölçer Bileşeninin Aralık Özelliğiyle İlgili Sınırlamalar](../../../../docs/framework/winforms/controls/limitations-of-the-timer-component-interval-property.md)
