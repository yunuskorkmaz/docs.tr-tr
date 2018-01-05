---
title: "Windows Forms süreölçer bileşeni &#39;sınırlamaları; s aralık özelliği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- timers [Windows Forms], event intervals
- Interval property [Windows Forms], limitations
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], limitations of Interval property
ms.assetid: 7e5fb513-77e7-4046-a8e8-aab94e61ca0f
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ec53957a61806239fdd41761de6e172681b7497b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="limitations-of-the-windows-forms-timer-component39s-interval-property"></a><span data-ttu-id="5854e-102">Windows Forms süreölçer bileşeni &#39;sınırlamaları; s aralık özelliği</span><span class="sxs-lookup"><span data-stu-id="5854e-102">Limitations of the Windows Forms Timer Component&#39;s Interval Property</span></span>
<span data-ttu-id="5854e-103">Windows Forms <xref:System.Windows.Forms.Timer> bileşen bir <xref:System.Windows.Forms.Timer.Interval%2A> özelliği yalnızca bir süreölçer olayı ve sonraki arasında geçen süreyi milisaniye olarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="5854e-103">The Windows Forms <xref:System.Windows.Forms.Timer> component has an <xref:System.Windows.Forms.Timer.Interval%2A> property that specifies the number of milliseconds that pass between one timer event and the next.</span></span> <span data-ttu-id="5854e-104">Bileşen devre dışı bırakılmadığı sürece bir süreölçer almaya devam eder <xref:System.Windows.Forms.Timer.Tick> süre kabaca eşit aralıklarla olay.</span><span class="sxs-lookup"><span data-stu-id="5854e-104">Unless the component is disabled, a timer continues to receive the <xref:System.Windows.Forms.Timer.Tick> event at roughly equal intervals of time.</span></span>  
  
 <span data-ttu-id="5854e-105">Bu bileşen, bir Windows Forms ortamı için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="5854e-105">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="5854e-106">Bir sunucu ortamı için uygun bir süreölçer gerekirse bkz [sunucu tabanlı zamanlayıcılar giriş](http://msdn.microsoft.com/en-us/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span><span class="sxs-lookup"><span data-stu-id="5854e-106">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](http://msdn.microsoft.com/en-us/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span></span>  
  
## <a name="the-interval-property"></a><span data-ttu-id="5854e-107">Aralık özelliği</span><span class="sxs-lookup"><span data-stu-id="5854e-107">The Interval Property</span></span>  
 <span data-ttu-id="5854e-108"><xref:System.Windows.Forms.Timer.Interval%2A> Özelliği, ne zaman programlama dikkate alınması gereken birkaç sınırlamalara sahiptir bir <xref:System.Windows.Forms.Timer> bileşen:</span><span class="sxs-lookup"><span data-stu-id="5854e-108">The <xref:System.Windows.Forms.Timer.Interval%2A> property has a few limitations to consider when you are programming a <xref:System.Windows.Forms.Timer> component:</span></span>  
  
-   <span data-ttu-id="5854e-109">Uygulamanızı veya başka bir uygulama sistem üzerinde ağır taleplerini değiştirirken, — uzun döngüler, yoğun hesaplamalar veya sürücü, ağ veya bağlantı noktası erişim gibi — uygulamanızı Süreölçer olayları kadar sık olarak alamayabilirsiniz <xref:System.Windows.Forms.Timer.Interval%2A> özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="5854e-109">If your application or another application is making heavy demands on the system — such as long loops, intensive calculations, or drive, network, or port access — your application may not get timer events as often as the <xref:System.Windows.Forms.Timer.Interval%2A> property specifies.</span></span>  
  
-   <span data-ttu-id="5854e-110">Aralık tam zamanında geçmesi garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="5854e-110">The interval is not guaranteed to elapse exactly on time.</span></span> <span data-ttu-id="5854e-111">Doğruluk emin olmak için Zamanlayıcı gerektiği gibi sistem saatini denetleyin yerine biriken zaman dahili olarak izlemek deneyin.</span><span class="sxs-lookup"><span data-stu-id="5854e-111">To ensure accuracy, the timer should check the system clock as needed, rather than try to keep track of accumulated time internally.</span></span>  
  
-   <span data-ttu-id="5854e-112">Kesinliğini <xref:System.Windows.Forms.Timer.Interval%2A> milisaniye cinsinden bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="5854e-112">The precision of the <xref:System.Windows.Forms.Timer.Interval%2A> property is in milliseconds.</span></span> <span data-ttu-id="5854e-113">Bazı bilgisayarlarda milisaniye yüksek çözünürlüğe olan yüksek çözünürlüklü bir sayaç sağlar.</span><span class="sxs-lookup"><span data-stu-id="5854e-113">Some computers provide a high-resolution counter that has a resolution higher than milliseconds.</span></span> <span data-ttu-id="5854e-114">Bu tür bir sayaç kullanılabilirliği bilgisayarınızı işlemci donanımda bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="5854e-114">The availability of such a counter depends on the processor hardware of your computer.</span></span> <span data-ttu-id="5854e-115">Daha fazla bilgi için 172338, "Nasıl için kullanım QueryPerformanceCounter için zamanı kodu," http://support.microsoft.com adresindeki Microsoft Bilgi Bankası makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="5854e-115">For more information, see article 172338, "How To Use QueryPerformanceCounter to Time Code," in the Microsoft Knowledge Base at http://support.microsoft.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5854e-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5854e-116">See Also</span></span>  
 <xref:System.Windows.Forms.Timer>  
 [<span data-ttu-id="5854e-117">Süreölçer Bileşeni</span><span class="sxs-lookup"><span data-stu-id="5854e-117">Timer Component</span></span>](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)  
 [<span data-ttu-id="5854e-118">Süreölçer Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5854e-118">Timer Component Overview</span></span>](../../../../docs/framework/winforms/controls/timer-component-overview-windows-forms.md)
