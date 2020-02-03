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
# <a name="limitations-of-the-windows-forms-timer-components-interval-property"></a><span data-ttu-id="74772-102">Windows Forms Süreölçer Bileşeninin Aralık Özelliğiyle İlgili Sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="74772-102">Limitations of the Windows Forms Timer Component's Interval Property</span></span>
<span data-ttu-id="74772-103">Windows Forms <xref:System.Windows.Forms.Timer> bileşeni, bir zamanlayıcı olayı ve bir sonraki arasında geçen milisaniye sayısını belirten bir <xref:System.Windows.Forms.Timer.Interval%2A> özelliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="74772-103">The Windows Forms <xref:System.Windows.Forms.Timer> component has an <xref:System.Windows.Forms.Timer.Interval%2A> property that specifies the number of milliseconds that pass between one timer event and the next.</span></span> <span data-ttu-id="74772-104">Bileşen devre dışı bırakılmadığı takdirde Zamanlayıcı kabaca eşit aralıklarla <xref:System.Windows.Forms.Timer.Tick> olayını almaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="74772-104">Unless the component is disabled, a timer continues to receive the <xref:System.Windows.Forms.Timer.Tick> event at roughly equal intervals of time.</span></span>  
  
 <span data-ttu-id="74772-105">Bu bileşen bir Windows Forms ortamı için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="74772-105">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="74772-106">Sunucu ortamı için uygun bir zamanlayıcıya ihtiyacınız varsa bkz. [sunucu tabanlı zamanlayıcılara giriş](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="74772-106">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span></span>  
  
## <a name="the-interval-property"></a><span data-ttu-id="74772-107">Interval özelliği</span><span class="sxs-lookup"><span data-stu-id="74772-107">The Interval Property</span></span>  
 <span data-ttu-id="74772-108"><xref:System.Windows.Forms.Timer.Interval%2A> özelliği, bir <xref:System.Windows.Forms.Timer> bileşenini programlarken göz önünde bulundurmanız gereken birkaç sınırlamalara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="74772-108">The <xref:System.Windows.Forms.Timer.Interval%2A> property has a few limitations to consider when you are programming a <xref:System.Windows.Forms.Timer> component:</span></span>  
  
- <span data-ttu-id="74772-109">Uygulamanız veya başka bir uygulama sistemde uzun döngüler, yoğun hesaplamalar veya sürücü, ağ ya da bağlantı noktası erişimi gibi yoğun talepler alıyorsa, <xref:System.Windows.Forms.Timer.Interval%2A> özelliği tarafından belirtildiği gibi, uygulamanız Zamanlayıcı olaylarını alamaz.</span><span class="sxs-lookup"><span data-stu-id="74772-109">If your application or another application is making heavy demands on the system — such as long loops, intensive calculations, or drive, network, or port access — your application may not get timer events as often as the <xref:System.Windows.Forms.Timer.Interval%2A> property specifies.</span></span>  
  
- <span data-ttu-id="74772-110">Zaman aralığı tam zamanında geçecek şekilde garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="74772-110">The interval is not guaranteed to elapse exactly on time.</span></span> <span data-ttu-id="74772-111">Doğruluk sağlamak için Zamanlayıcı, toplanan süreyi dahili olarak izlemeye çalışmak yerine, sistem saatini gerektiği gibi denetlemelidir.</span><span class="sxs-lookup"><span data-stu-id="74772-111">To ensure accuracy, the timer should check the system clock as needed, rather than try to keep track of accumulated time internally.</span></span>  
  
- <span data-ttu-id="74772-112"><xref:System.Windows.Forms.Timer.Interval%2A> özelliğinin duyarlığı milisaniyedir.</span><span class="sxs-lookup"><span data-stu-id="74772-112">The precision of the <xref:System.Windows.Forms.Timer.Interval%2A> property is in milliseconds.</span></span> <span data-ttu-id="74772-113">Bazı bilgisayarlar, en fazla milisaniyelik çözünürlüğü olan yüksek çözünürlüklü bir sayaç sağlar.</span><span class="sxs-lookup"><span data-stu-id="74772-113">Some computers provide a high-resolution counter that has a resolution higher than milliseconds.</span></span> <span data-ttu-id="74772-114">Böyle bir sayacın kullanılabilirliği bilgisayarınızın işlemci donanımına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="74772-114">The availability of such a counter depends on the processor hardware of your computer.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="74772-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74772-115">See also</span></span>

- <xref:System.Windows.Forms.Timer>
- [<span data-ttu-id="74772-116">Süreölçer Bileşeni</span><span class="sxs-lookup"><span data-stu-id="74772-116">Timer Component</span></span>](timer-component-windows-forms.md)
- [<span data-ttu-id="74772-117">Süreölçer Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="74772-117">Timer Component Overview</span></span>](timer-component-overview-windows-forms.md)
