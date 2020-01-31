---
title: Süreölçer Bileşenine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- Timer
helpviewer_keywords:
- Timer component [Windows Forms], about Timer components
- timers [Windows Forms], about timers
ms.assetid: e672c05b-a8b6-4b26-9e4d-9223aa9e3873
ms.openlocfilehash: 83b52d395cdc3e3357bcf83517eab258a5c8ae08
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742771"
---
# <a name="timer-component-overview-windows-forms"></a>Süreölçer Bileşenine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.Timer>, düzenli aralıklarla olay başlatan bir bileşendir. Bu bileşen bir Windows Forms ortamı için tasarlanmıştır. Sunucu ortamı için uygun bir zamanlayıcıya ihtiyacınız varsa bkz. [sunucu tabanlı zamanlayıcılara giriş](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).  
  
## <a name="key-properties-methods-and-events"></a>Anahtar özellikler, Yöntemler ve olaylar  
 Aralıkların uzunluğu, değeri milisaniyelik olan <xref:System.Windows.Forms.Timer.Interval%2A> özelliği tarafından tanımlanır. Bileşen etkinleştirildiğinde <xref:System.Windows.Forms.Timer.Tick> olayı her zaman oluşur. Burada yürütülecek kodu eklersiniz. Daha fazla bilgi için bkz. [nasıl yapılır: ayarlanan aralıklarda yordamları Windows Forms Zamanlayıcı bileşeniyle çalıştırma](run-procedures-at-set-intervals-with-wf-timer-component.md). <xref:System.Windows.Forms.Timer> bileşenin temel yöntemleri <xref:System.Windows.Forms.Timer.Start%2A> ve <xref:System.Windows.Forms.Timer.Stop%2A>ve bu da süreölçeri açıp kapatır. Süreölçer devre dışı bırakıldığında, sıfırlanır; <xref:System.Windows.Forms.Timer> bileşeni duraklamanın bir yolu yoktur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Timer>
- [Süreölçer Bileşeni](timer-component-windows-forms.md)
- [Windows Forms Süreölçer Bileşeninin Aralık Özelliğiyle İlgili Sınırlamalar](limitations-of-the-timer-component-interval-property.md)
