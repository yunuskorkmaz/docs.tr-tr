---
title: Süreölçer Bileşenine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- Timer
helpviewer_keywords:
- Timer component [Windows Forms], about Timer components
- timers [Windows Forms], about timers
ms.assetid: e672c05b-a8b6-4b26-9e4d-9223aa9e3873
ms.openlocfilehash: a13afba026f1f9eed095817c65637bb6a091c7f0
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57725291"
---
# <a name="timer-component-overview-windows-forms"></a>Süreölçer Bileşenine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.Timer> düzenli aralıklarla bir olayı oluşturan bir bileşendir. Bu bileşen, bir Windows Forms ortamı için tasarlanmıştır. Bir sunucu ortamı için uygun olan bir zamanlayıcı gerekirse bkz [sunucu tabanlı zamanlayıcılar giriş](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).  
  
## <a name="key-properties-methods-and-events"></a>Anahtar özellikleri, yöntemleri ve olayları  
 Aralıkların uzunluğunu tarafından tanımlanan <xref:System.Windows.Forms.Timer.Interval%2A> özelliği, değeri olan milisaniye cinsinden. Bileşen etkinleştirildiğinde <xref:System.Windows.Forms.Timer.Tick> olayı her aralığı. Burada yürütülecek kodu eklersiniz budur. Daha fazla bilgi için [nasıl yapılır: Windows Forms süreölçer bileşeni ile belirlenen aralıklarda yordamları çalıştırma](run-procedures-at-set-intervals-with-wf-timer-component.md). Anahtar yöntemlerini <xref:System.Windows.Forms.Timer> bileşenidir <xref:System.Windows.Forms.Timer.Start%2A> ve <xref:System.Windows.Forms.Timer.Stop%2A>, açma ve kapatma Zamanlayıcı açın. Zamanlayıcı kapalı olduğunda sıfırlar; duraklatmak için bir yolu yoktur bir <xref:System.Windows.Forms.Timer> bileşeni.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.Timer>
- [Süreölçer Bileşeni](timer-component-windows-forms.md)
- [Windows Forms Süreölçer Bileşeninin Aralık Özelliğiyle İlgili Sınırlamalar](limitations-of-the-timer-component-interval-property.md)
