---
title: Windows Forms süreölçer bileşeni sınırlamaları&#39;s aralık özelliği
ms.date: 03/30/2017
helpviewer_keywords:
- timers [Windows Forms], event intervals
- Interval property [Windows Forms], limitations
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], limitations of Interval property
ms.assetid: 7e5fb513-77e7-4046-a8e8-aab94e61ca0f
ms.openlocfilehash: 9710568c3c21878aa6aad626e3152168a2f0c2fe
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48836400"
---
# <a name="limitations-of-the-windows-forms-timer-component39s-interval-property"></a>Windows Forms süreölçer bileşeni sınırlamaları&#39;s aralık özelliği
Windows Forms <xref:System.Windows.Forms.Timer> bileşeniyse bir <xref:System.Windows.Forms.Timer.Interval%2A> özelliği bir süreölçer olayı ve sonraki arasında geçen milisaniye sayısını belirtir. Bileşen devre dışı bırakılmadığı sürece, bir zamanlayıcı almaya devam ettiğinden <xref:System.Windows.Forms.Timer.Tick> zaman kabaca eşit aralıklarla olay.  
  
 Bu bileşen, bir Windows Forms ortamı için tasarlanmıştır. Bir sunucu ortamı için uygun olan bir zamanlayıcı gerekirse bkz [sunucu tabanlı zamanlayıcılar giriş](https://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).  
  
## <a name="the-interval-property"></a>Aralık özelliği  
 <xref:System.Windows.Forms.Timer.Interval%2A> Özelliğine sahip olduğunda programlama dikkate alınması gereken bazı sınırlamalar bir <xref:System.Windows.Forms.Timer> bileşeni:  
  
-   Uygulamanızı veya başka bir uygulama sistem üzerinde ağır taleplerini değiştirirken, — uzun döngüleri, yoğun hesaplama veya sürücü, ağ veya bağlantı noktası erişim gibi — uygulamanızı Zamanlayıcı olaylar çok sık olarak alamayabilir <xref:System.Windows.Forms.Timer.Interval%2A> özelliği belirtir.  
  
-   Aralık tam zamanında geçmesi garanti edilmez. Doğruluğunu sağlamak için Zamanlayıcıyı gerektiği gibi sistem saati denetlemek yerine biriken zaman dahili olarak izlemek deneyin.  
  
-   Duyarlığını <xref:System.Windows.Forms.Timer.Interval%2A> milisaniye cinsinden bir özelliktir. Bazı bilgisayarlar, bir milisaniyeden daha yüksek çözünürlüğe sahip yüksek çözünürlüklü bir sayaç belirtin. Böyle bir sayaç kullanılabilirliğini bilgisayarınızın işlemci donanımda bağlıdır.
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Timer>  
 [Süreölçer Bileşeni](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)  
 [Süreölçer Bileşenine Genel Bakış](../../../../docs/framework/winforms/controls/timer-component-overview-windows-forms.md)
