---
title: Windows Forms Süreölçer Bileşeninin Aralık Özelliğiyle İlgili Sınırlamalar
ms.date: 03/30/2017
helpviewer_keywords:
- timers [Windows Forms], event intervals
- Interval property [Windows Forms], limitations
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], limitations of Interval property
ms.assetid: 7e5fb513-77e7-4046-a8e8-aab94e61ca0f
ms.openlocfilehash: 2d8e25d9d27c0908f2d794a0c3c9646024984764
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269685"
---
# <a name="limitations-of-the-windows-forms-timer-components-interval-property"></a><span data-ttu-id="b16d1-102">Windows Forms Süreölçer Bileşeninin Aralık Özelliğiyle İlgili Sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="b16d1-102">Limitations of the Windows Forms Timer Component's Interval Property</span></span>
<span data-ttu-id="b16d1-103">Windows Forms <xref:System.Windows.Forms.Timer> bileşeniyse bir <xref:System.Windows.Forms.Timer.Interval%2A> özelliği bir süreölçer olayı ve sonraki arasında geçen milisaniye sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b16d1-103">The Windows Forms <xref:System.Windows.Forms.Timer> component has an <xref:System.Windows.Forms.Timer.Interval%2A> property that specifies the number of milliseconds that pass between one timer event and the next.</span></span> <span data-ttu-id="b16d1-104">Bileşen devre dışı bırakılmadığı sürece, bir zamanlayıcı almaya devam ettiğinden <xref:System.Windows.Forms.Timer.Tick> zaman kabaca eşit aralıklarla olay.</span><span class="sxs-lookup"><span data-stu-id="b16d1-104">Unless the component is disabled, a timer continues to receive the <xref:System.Windows.Forms.Timer.Tick> event at roughly equal intervals of time.</span></span>  
  
 <span data-ttu-id="b16d1-105">Bu bileşen, bir Windows Forms ortamı için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="b16d1-105">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="b16d1-106">Bir sunucu ortamı için uygun olan bir zamanlayıcı gerekirse bkz [sunucu tabanlı zamanlayıcılar giriş](https://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span><span class="sxs-lookup"><span data-stu-id="b16d1-106">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span></span>  
  
## <a name="the-interval-property"></a><span data-ttu-id="b16d1-107">Aralık özelliği</span><span class="sxs-lookup"><span data-stu-id="b16d1-107">The Interval Property</span></span>  
 <span data-ttu-id="b16d1-108"><xref:System.Windows.Forms.Timer.Interval%2A> Özelliğine sahip olduğunda programlama dikkate alınması gereken bazı sınırlamalar bir <xref:System.Windows.Forms.Timer> bileşeni:</span><span class="sxs-lookup"><span data-stu-id="b16d1-108">The <xref:System.Windows.Forms.Timer.Interval%2A> property has a few limitations to consider when you are programming a <xref:System.Windows.Forms.Timer> component:</span></span>  
  
-   <span data-ttu-id="b16d1-109">Uygulamanızı veya başka bir uygulama sistem üzerinde ağır taleplerini değiştirirken, — uzun döngüleri, yoğun hesaplama veya sürücü, ağ veya bağlantı noktası erişim gibi — uygulamanızı Zamanlayıcı olaylar çok sık olarak alamayabilir <xref:System.Windows.Forms.Timer.Interval%2A> özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="b16d1-109">If your application or another application is making heavy demands on the system — such as long loops, intensive calculations, or drive, network, or port access — your application may not get timer events as often as the <xref:System.Windows.Forms.Timer.Interval%2A> property specifies.</span></span>  
  
-   <span data-ttu-id="b16d1-110">Aralık tam zamanında geçmesi garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="b16d1-110">The interval is not guaranteed to elapse exactly on time.</span></span> <span data-ttu-id="b16d1-111">Doğruluğunu sağlamak için Zamanlayıcıyı gerektiği gibi sistem saati denetlemek yerine biriken zaman dahili olarak izlemek deneyin.</span><span class="sxs-lookup"><span data-stu-id="b16d1-111">To ensure accuracy, the timer should check the system clock as needed, rather than try to keep track of accumulated time internally.</span></span>  
  
-   <span data-ttu-id="b16d1-112">Duyarlığını <xref:System.Windows.Forms.Timer.Interval%2A> milisaniye cinsinden bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="b16d1-112">The precision of the <xref:System.Windows.Forms.Timer.Interval%2A> property is in milliseconds.</span></span> <span data-ttu-id="b16d1-113">Bazı bilgisayarlar, bir milisaniyeden daha yüksek çözünürlüğe sahip yüksek çözünürlüklü bir sayaç belirtin.</span><span class="sxs-lookup"><span data-stu-id="b16d1-113">Some computers provide a high-resolution counter that has a resolution higher than milliseconds.</span></span> <span data-ttu-id="b16d1-114">Böyle bir sayaç kullanılabilirliğini bilgisayarınızın işlemci donanımda bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b16d1-114">The availability of such a counter depends on the processor hardware of your computer.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b16d1-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b16d1-115">See also</span></span>
- <xref:System.Windows.Forms.Timer>
- [<span data-ttu-id="b16d1-116">Süreölçer Bileşeni</span><span class="sxs-lookup"><span data-stu-id="b16d1-116">Timer Component</span></span>](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)
- [<span data-ttu-id="b16d1-117">Süreölçer Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b16d1-117">Timer Component Overview</span></span>](../../../../docs/framework/winforms/controls/timer-component-overview-windows-forms.md)
