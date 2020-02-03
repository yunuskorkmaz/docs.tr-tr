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
# <a name="timer-component-overview-windows-forms"></a><span data-ttu-id="00163-102">Süreölçer Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="00163-102">Timer Component Overview (Windows Forms)</span></span>
<span data-ttu-id="00163-103">Windows Forms <xref:System.Windows.Forms.Timer>, düzenli aralıklarla olay başlatan bir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="00163-103">The Windows Forms <xref:System.Windows.Forms.Timer> is a component that raises an event at regular intervals.</span></span> <span data-ttu-id="00163-104">Bu bileşen bir Windows Forms ortamı için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="00163-104">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="00163-105">Sunucu ortamı için uygun bir zamanlayıcıya ihtiyacınız varsa bkz. [sunucu tabanlı zamanlayıcılara giriş](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="00163-105">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span></span>  
  
## <a name="key-properties-methods-and-events"></a><span data-ttu-id="00163-106">Anahtar özellikler, Yöntemler ve olaylar</span><span class="sxs-lookup"><span data-stu-id="00163-106">Key Properties, Methods, and Events</span></span>  
 <span data-ttu-id="00163-107">Aralıkların uzunluğu, değeri milisaniyelik olan <xref:System.Windows.Forms.Timer.Interval%2A> özelliği tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="00163-107">The length of the intervals is defined by the <xref:System.Windows.Forms.Timer.Interval%2A> property, whose value is in milliseconds.</span></span> <span data-ttu-id="00163-108">Bileşen etkinleştirildiğinde <xref:System.Windows.Forms.Timer.Tick> olayı her zaman oluşur.</span><span class="sxs-lookup"><span data-stu-id="00163-108">When the component is enabled, the <xref:System.Windows.Forms.Timer.Tick> event is raised every interval.</span></span> <span data-ttu-id="00163-109">Burada yürütülecek kodu eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="00163-109">This is where you would add code to be executed.</span></span> <span data-ttu-id="00163-110">Daha fazla bilgi için bkz. [nasıl yapılır: ayarlanan aralıklarda yordamları Windows Forms Zamanlayıcı bileşeniyle çalıştırma](run-procedures-at-set-intervals-with-wf-timer-component.md).</span><span class="sxs-lookup"><span data-stu-id="00163-110">For more information, see [How to: Run Procedures at Set Intervals with the Windows Forms Timer Component](run-procedures-at-set-intervals-with-wf-timer-component.md).</span></span> <span data-ttu-id="00163-111"><xref:System.Windows.Forms.Timer> bileşenin temel yöntemleri <xref:System.Windows.Forms.Timer.Start%2A> ve <xref:System.Windows.Forms.Timer.Stop%2A>ve bu da süreölçeri açıp kapatır.</span><span class="sxs-lookup"><span data-stu-id="00163-111">The key methods of the <xref:System.Windows.Forms.Timer> component are <xref:System.Windows.Forms.Timer.Start%2A> and <xref:System.Windows.Forms.Timer.Stop%2A>, which turn the timer on and off.</span></span> <span data-ttu-id="00163-112">Süreölçer devre dışı bırakıldığında, sıfırlanır; <xref:System.Windows.Forms.Timer> bileşeni duraklamanın bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="00163-112">When the timer is switched off, it resets; there is no way to pause a <xref:System.Windows.Forms.Timer> component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00163-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00163-113">See also</span></span>

- <xref:System.Windows.Forms.Timer>
- [<span data-ttu-id="00163-114">Süreölçer Bileşeni</span><span class="sxs-lookup"><span data-stu-id="00163-114">Timer Component</span></span>](timer-component-windows-forms.md)
- [<span data-ttu-id="00163-115">Windows Forms Süreölçer Bileşeninin Aralık Özelliğiyle İlgili Sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="00163-115">Limitations of the Windows Forms Timer Component's Interval Property</span></span>](limitations-of-the-timer-component-interval-property.md)
