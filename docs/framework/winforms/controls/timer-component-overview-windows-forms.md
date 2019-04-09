---
title: Süreölçer Bileşenine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- Timer
helpviewer_keywords:
- Timer component [Windows Forms], about Timer components
- timers [Windows Forms], about timers
ms.assetid: e672c05b-a8b6-4b26-9e4d-9223aa9e3873
ms.openlocfilehash: 5bef0ba87d6a496acf7575965128be2b20b437ab
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074215"
---
# <a name="timer-component-overview-windows-forms"></a><span data-ttu-id="e3750-102">Süreölçer Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="e3750-102">Timer Component Overview (Windows Forms)</span></span>
<span data-ttu-id="e3750-103">Windows Forms <xref:System.Windows.Forms.Timer> düzenli aralıklarla bir olayı oluşturan bir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="e3750-103">The Windows Forms <xref:System.Windows.Forms.Timer> is a component that raises an event at regular intervals.</span></span> <span data-ttu-id="e3750-104">Bu bileşen, bir Windows Forms ortamı için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e3750-104">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="e3750-105">Bir sunucu ortamı için uygun olan bir zamanlayıcı gerekirse bkz [sunucu tabanlı zamanlayıcılar giriş](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="e3750-105">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span></span>  
  
## <a name="key-properties-methods-and-events"></a><span data-ttu-id="e3750-106">Anahtar özellikleri, yöntemleri ve olayları</span><span class="sxs-lookup"><span data-stu-id="e3750-106">Key Properties, Methods, and Events</span></span>  
 <span data-ttu-id="e3750-107">Aralıkların uzunluğunu tarafından tanımlanan <xref:System.Windows.Forms.Timer.Interval%2A> özelliği, değeri olan milisaniye cinsinden.</span><span class="sxs-lookup"><span data-stu-id="e3750-107">The length of the intervals is defined by the <xref:System.Windows.Forms.Timer.Interval%2A> property, whose value is in milliseconds.</span></span> <span data-ttu-id="e3750-108">Bileşen etkinleştirildiğinde <xref:System.Windows.Forms.Timer.Tick> olayı her aralığı.</span><span class="sxs-lookup"><span data-stu-id="e3750-108">When the component is enabled, the <xref:System.Windows.Forms.Timer.Tick> event is raised every interval.</span></span> <span data-ttu-id="e3750-109">Burada yürütülecek kodu eklersiniz budur.</span><span class="sxs-lookup"><span data-stu-id="e3750-109">This is where you would add code to be executed.</span></span> <span data-ttu-id="e3750-110">Daha fazla bilgi için [nasıl yapılır: Windows Forms süreölçer bileşeni ile belirlenen aralıklarda yordamları çalıştırma](run-procedures-at-set-intervals-with-wf-timer-component.md).</span><span class="sxs-lookup"><span data-stu-id="e3750-110">For more information, see [How to: Run Procedures at Set Intervals with the Windows Forms Timer Component](run-procedures-at-set-intervals-with-wf-timer-component.md).</span></span> <span data-ttu-id="e3750-111">Anahtar yöntemlerini <xref:System.Windows.Forms.Timer> bileşenidir <xref:System.Windows.Forms.Timer.Start%2A> ve <xref:System.Windows.Forms.Timer.Stop%2A>, açma ve kapatma Zamanlayıcı açın.</span><span class="sxs-lookup"><span data-stu-id="e3750-111">The key methods of the <xref:System.Windows.Forms.Timer> component are <xref:System.Windows.Forms.Timer.Start%2A> and <xref:System.Windows.Forms.Timer.Stop%2A>, which turn the timer on and off.</span></span> <span data-ttu-id="e3750-112">Zamanlayıcı kapalı olduğunda sıfırlar; duraklatmak için bir yolu yoktur bir <xref:System.Windows.Forms.Timer> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="e3750-112">When the timer is switched off, it resets; there is no way to pause a <xref:System.Windows.Forms.Timer> component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3750-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e3750-113">See also</span></span>

- <xref:System.Windows.Forms.Timer>
- [<span data-ttu-id="e3750-114">Süreölçer Bileşeni</span><span class="sxs-lookup"><span data-stu-id="e3750-114">Timer Component</span></span>](timer-component-windows-forms.md)
- [<span data-ttu-id="e3750-115">Windows Forms Süreölçer Bileşeninin Aralık Özelliğiyle İlgili Sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="e3750-115">Limitations of the Windows Forms Timer Component's Interval Property</span></span>](limitations-of-the-timer-component-interval-property.md)
