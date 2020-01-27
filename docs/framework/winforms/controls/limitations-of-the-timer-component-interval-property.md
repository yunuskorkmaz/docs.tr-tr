---
title: Zamanlayıcı bileşen aralığı özelliğinin sınırlamaları
ms.date: 03/30/2017
helpviewer_keywords:
- timers [Windows Forms], event intervals
- Interval property [Windows Forms], limitations
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], limitations of Interval property
ms.assetid: 7e5fb513-77e7-4046-a8e8-aab94e61ca0f
ms.openlocfilehash: 15626a53f0541ff79e2098377d9dfdb4626ac155
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745239"
---
# <a name="limitations-of-the-windows-forms-timer-components-interval-property"></a>Windows Forms Süreölçer Bileşeninin Aralık Özelliğiyle İlgili Sınırlamalar
Windows Forms <xref:System.Windows.Forms.Timer> bileşeni, bir zamanlayıcı olayı ve bir sonraki arasında geçen milisaniye sayısını belirten bir <xref:System.Windows.Forms.Timer.Interval%2A> özelliğine sahiptir. Bileşen devre dışı bırakılmadığı takdirde Zamanlayıcı kabaca eşit aralıklarla <xref:System.Windows.Forms.Timer.Tick> olayını almaya devam eder.  
  
 Bu bileşen bir Windows Forms ortamı için tasarlanmıştır. Sunucu ortamı için uygun bir zamanlayıcıya ihtiyacınız varsa bkz. [sunucu tabanlı zamanlayıcılara giriş](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).  
  
## <a name="the-interval-property"></a>Interval özelliği  
 <xref:System.Windows.Forms.Timer.Interval%2A> özelliği, bir <xref:System.Windows.Forms.Timer> bileşenini programlarken göz önünde bulundurmanız gereken birkaç sınırlamalara sahiptir:  
  
- Uygulamanız veya başka bir uygulama sistemde uzun döngüler, yoğun hesaplamalar veya sürücü, ağ ya da bağlantı noktası erişimi gibi yoğun talepler alıyorsa, <xref:System.Windows.Forms.Timer.Interval%2A> özelliği tarafından belirtildiği gibi, uygulamanız Zamanlayıcı olaylarını alamaz.  
  
- Zaman aralığı tam zamanında geçecek şekilde garanti edilmez. Doğruluk sağlamak için Zamanlayıcı, toplanan süreyi dahili olarak izlemeye çalışmak yerine, sistem saatini gerektiği gibi denetlemelidir.  
  
- <xref:System.Windows.Forms.Timer.Interval%2A> özelliğinin duyarlığı milisaniyedir. Bazı bilgisayarlar, en fazla milisaniyelik çözünürlüğü olan yüksek çözünürlüklü bir sayaç sağlar. Böyle bir sayacın kullanılabilirliği bilgisayarınızın işlemci donanımına bağlıdır.
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Timer>
- [Süreölçer Bileşeni](timer-component-windows-forms.md)
- [Süreölçer Bileşenine Genel Bakış](timer-component-overview-windows-forms.md)
