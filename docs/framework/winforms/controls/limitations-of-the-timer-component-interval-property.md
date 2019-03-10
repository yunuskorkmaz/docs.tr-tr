---
title: Windows Forms Süreölçer Bileşeninin Aralık Özelliğiyle İlgili Sınırlamalar
ms.date: 03/30/2017
helpviewer_keywords:
- timers [Windows Forms], event intervals
- Interval property [Windows Forms], limitations
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], limitations of Interval property
ms.assetid: 7e5fb513-77e7-4046-a8e8-aab94e61ca0f
ms.openlocfilehash: f564a4ce7fa2d9b8ea5446f2cf6bd016db054dd9
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57724394"
---
# <a name="limitations-of-the-windows-forms-timer-components-interval-property"></a>Windows Forms Süreölçer Bileşeninin Aralık Özelliğiyle İlgili Sınırlamalar
Windows Forms <xref:System.Windows.Forms.Timer> bileşeniyse bir <xref:System.Windows.Forms.Timer.Interval%2A> özelliği bir süreölçer olayı ve sonraki arasında geçen milisaniye sayısını belirtir. Bileşen devre dışı bırakılmadığı sürece, bir zamanlayıcı almaya devam ettiğinden <xref:System.Windows.Forms.Timer.Tick> zaman kabaca eşit aralıklarla olay.  
  
 Bu bileşen, bir Windows Forms ortamı için tasarlanmıştır. Bir sunucu ortamı için uygun olan bir zamanlayıcı gerekirse bkz [sunucu tabanlı zamanlayıcılar giriş](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).  
  
## <a name="the-interval-property"></a>Aralık özelliği  
 <xref:System.Windows.Forms.Timer.Interval%2A> Özelliğine sahip olduğunda programlama dikkate alınması gereken bazı sınırlamalar bir <xref:System.Windows.Forms.Timer> bileşeni:  
  
-   Uygulamanızı veya başka bir uygulama sistem üzerinde ağır taleplerini değiştirirken, — uzun döngüleri, yoğun hesaplama veya sürücü, ağ veya bağlantı noktası erişim gibi — uygulamanızı Zamanlayıcı olaylar çok sık olarak alamayabilir <xref:System.Windows.Forms.Timer.Interval%2A> özelliği belirtir.  
  
-   Aralık tam zamanında geçmesi garanti edilmez. Doğruluğunu sağlamak için Zamanlayıcıyı gerektiği gibi sistem saati denetlemek yerine biriken zaman dahili olarak izlemek deneyin.  
  
-   Duyarlığını <xref:System.Windows.Forms.Timer.Interval%2A> milisaniye cinsinden bir özelliktir. Bazı bilgisayarlar, bir milisaniyeden daha yüksek çözünürlüğe sahip yüksek çözünürlüklü bir sayaç belirtin. Böyle bir sayaç kullanılabilirliğini bilgisayarınızın işlemci donanımda bağlıdır.
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.Timer>
- [Süreölçer Bileşeni](timer-component-windows-forms.md)
- [Süreölçer Bileşenine Genel Bakış](timer-component-overview-windows-forms.md)
