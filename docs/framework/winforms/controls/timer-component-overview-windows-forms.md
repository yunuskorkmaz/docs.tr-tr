---
title: "Süreölçer Bileşenine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Timer
helpviewer_keywords:
- Timer component [Windows Forms], about Timer components
- timers [Windows Forms], about timers
ms.assetid: e672c05b-a8b6-4b26-9e4d-9223aa9e3873
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 90296d2741a96e8788bf7a9b18bf3ea303ad2bae
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="timer-component-overview-windows-forms"></a><span data-ttu-id="3ad31-102">Süreölçer Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="3ad31-102">Timer Component Overview (Windows Forms)</span></span>
<span data-ttu-id="3ad31-103">Windows Forms <xref:System.Windows.Forms.Timer> düzenli aralıklarla bir olay başlatır bir bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="3ad31-103">The Windows Forms <xref:System.Windows.Forms.Timer> is a component that raises an event at regular intervals.</span></span> <span data-ttu-id="3ad31-104">Bu bileşen, bir Windows Forms ortamı için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="3ad31-104">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="3ad31-105">Bir sunucu ortamı için uygun bir süreölçer gerekirse bkz [sunucu tabanlı zamanlayıcılar giriş](http://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span><span class="sxs-lookup"><span data-stu-id="3ad31-105">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](http://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span></span>  
  
## <a name="key-properties-methods-and-events"></a><span data-ttu-id="3ad31-106">Anahtar özellikleri, yöntemleri ve olayları</span><span class="sxs-lookup"><span data-stu-id="3ad31-106">Key Properties, Methods, and Events</span></span>  
 <span data-ttu-id="3ad31-107">Uzunluklarını tarafından tanımlanan <xref:System.Windows.Forms.Timer.Interval%2A> özelliği, değeri olan milisaniye cinsinden.</span><span class="sxs-lookup"><span data-stu-id="3ad31-107">The length of the intervals is defined by the <xref:System.Windows.Forms.Timer.Interval%2A> property, whose value is in milliseconds.</span></span> <span data-ttu-id="3ad31-108">Bileşen etkinleştirildiğinde, <xref:System.Windows.Forms.Timer.Tick> olayı her aralığı.</span><span class="sxs-lookup"><span data-stu-id="3ad31-108">When the component is enabled, the <xref:System.Windows.Forms.Timer.Tick> event is raised every interval.</span></span> <span data-ttu-id="3ad31-109">Burada yürütülmek üzere kod eklemek budur.</span><span class="sxs-lookup"><span data-stu-id="3ad31-109">This is where you would add code to be executed.</span></span> <span data-ttu-id="3ad31-110">Daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms süreölçer bileşeni ile ayarlama aralıklarda yordamları çalıştırmak](../../../../docs/framework/winforms/controls/run-procedures-at-set-intervals-with-wf-timer-component.md).</span><span class="sxs-lookup"><span data-stu-id="3ad31-110">For more information, see [How to: Run Procedures at Set Intervals with the Windows Forms Timer Component](../../../../docs/framework/winforms/controls/run-procedures-at-set-intervals-with-wf-timer-component.md).</span></span> <span data-ttu-id="3ad31-111">Anahtar yöntemleri <xref:System.Windows.Forms.Timer> bileşeni olan <xref:System.Windows.Forms.Timer.Start%2A> ve <xref:System.Windows.Forms.Timer.Stop%2A>, açma ve kapatma Zamanlayıcı açın.</span><span class="sxs-lookup"><span data-stu-id="3ad31-111">The key methods of the <xref:System.Windows.Forms.Timer> component are <xref:System.Windows.Forms.Timer.Start%2A> and <xref:System.Windows.Forms.Timer.Stop%2A>, which turn the timer on and off.</span></span> <span data-ttu-id="3ad31-112">Zamanlayıcı kapalı olduğunda sıfırlar; duraklatmak için bir yolu yoktur bir <xref:System.Windows.Forms.Timer> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="3ad31-112">When the timer is switched off, it resets; there is no way to pause a <xref:System.Windows.Forms.Timer> component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ad31-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3ad31-113">See Also</span></span>  
 <xref:System.Windows.Forms.Timer>  
 [<span data-ttu-id="3ad31-114">Süreölçer Bileşeni</span><span class="sxs-lookup"><span data-stu-id="3ad31-114">Timer Component</span></span>](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)  
 [<span data-ttu-id="3ad31-115">Windows Forms Süreölçer Bileşeninin Aralık Özelliğiyle İlgili Sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="3ad31-115">Limitations of the Windows Forms Timer Component's Interval Property</span></span>](../../../../docs/framework/winforms/controls/limitations-of-the-timer-component-interval-property.md)
