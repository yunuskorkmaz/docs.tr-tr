---
title: Windows Forms'ta Fare Yakalama
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: mouse [Windows Forms], capture
ms.assetid: 8911d4b0-a4f8-4f93-8246-371aebd27d0c
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8004b05ea25341a142bfcfd9ae812ee3bebd6d5b
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="mouse-capture-in-windows-forms"></a><span data-ttu-id="0173c-102">Windows Forms'ta Fare Yakalama</span><span class="sxs-lookup"><span data-stu-id="0173c-102">Mouse Capture in Windows Forms</span></span>
<span data-ttu-id="0173c-103">*Fare yakalama* denetim tüm fare girişi komutu yönlendirdiğinde başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="0173c-103">*Mouse capture* refers to when a control takes command of all mouse input.</span></span> <span data-ttu-id="0173c-104">Bir denetim fare yakalandı, işaretçi sınırlarının içinde olup olmadığını fare girdisi alır.</span><span class="sxs-lookup"><span data-stu-id="0173c-104">When a control has captured the mouse, it receives mouse input whether or not the pointer is within its borders.</span></span>  
  
## <a name="setting-mouse-capture"></a><span data-ttu-id="0173c-105">Fare yakalama ayarlama</span><span class="sxs-lookup"><span data-stu-id="0173c-105">Setting Mouse Capture</span></span>  
 <span data-ttu-id="0173c-106">Windows Forms'ta fare bir denetimde bir fare düğmesini kullanıcı ve kullanıcı fare düğmesini bıraktığında fare denetim tarafından yayımlanan denetim tarafından yakalanır.</span><span class="sxs-lookup"><span data-stu-id="0173c-106">In Windows Forms the mouse is captured by the control when the user presses a mouse button on a control, and the mouse is released by the control when the user releases the mouse button.</span></span>  
  
 <span data-ttu-id="0173c-107"><xref:System.Windows.Forms.Control.Capture%2A> Özelliği <xref:System.Windows.Forms.Control> sınıfı bir denetim fare yakalanan olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0173c-107">The <xref:System.Windows.Forms.Control.Capture%2A> property of the <xref:System.Windows.Forms.Control> class specifies whether a control has captured the mouse.</span></span> <span data-ttu-id="0173c-108">Ne zaman bir denetim fare yakalama kaybederse belirlemek için tanıtıcı <xref:System.Windows.Forms.Control.MouseCaptureChanged> olay.</span><span class="sxs-lookup"><span data-stu-id="0173c-108">To determine when a control loses mouse capture, handle the <xref:System.Windows.Forms.Control.MouseCaptureChanged> event.</span></span>  
  
 <span data-ttu-id="0173c-109">Yalnızca ön plan penceresi fare yakalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0173c-109">Only the foreground window can capture the mouse.</span></span> <span data-ttu-id="0173c-110">Bir arka plan penceresi fare yakalama girişiminde bulunduğunda, pencere iletileri için fare işaretçisini penceresinde görünen dilimini içinde olduğunda oluşan fare olayları alır.</span><span class="sxs-lookup"><span data-stu-id="0173c-110">When a background window attempts to capture the mouse, the window receives messages only for mouse events that occur when the mouse pointer is within the visible portion of the window.</span></span> <span data-ttu-id="0173c-111">Ön plan penceresi fare yakalandı olsa bile, kullanıcı hala başka bir pencere ön plana getiren tıklatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0173c-111">Also, even if the foreground window has captured the mouse, the user can still click another window, bringing it to the foreground.</span></span> <span data-ttu-id="0173c-112">Fare yakalandığında kısayol tuşları çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="0173c-112">When the mouse is captured, shortcut keys do not work.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0173c-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0173c-113">See Also</span></span>  
 [<span data-ttu-id="0173c-114">Forms bir Windows uygulamasında fare girdisi</span><span class="sxs-lookup"><span data-stu-id="0173c-114">Mouse Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
