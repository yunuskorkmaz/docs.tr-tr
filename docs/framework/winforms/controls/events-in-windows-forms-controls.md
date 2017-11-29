---
title: Windows Forms Denetimlerindeki Olaylar
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- events [Windows Forms], custom controls (using code)
- custom controls [Windows Forms], events overview (using code)
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e568dd7fadea8af399a63aa95347f368b4e13a54
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="events-in-windows-forms-controls"></a><span data-ttu-id="a7c91-102">Windows Forms Denetimlerindeki Olaylar</span><span class="sxs-lookup"><span data-stu-id="a7c91-102">Events in Windows Forms Controls</span></span>
<span data-ttu-id="a7c91-103">Bir Windows Forms denetimi birden fazla altmış olaylarından devralır <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a7c91-103">A Windows Forms control inherits more than sixty events from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a7c91-104">Bunlar <xref:System.Windows.Forms.Control.Paint> çizilecek denetim neden olan olay, bir pencere gibi görüntüleme için ilgili olayları <xref:System.Windows.Forms.Control.Resize> ve <xref:System.Windows.Forms.Control.Layout> olayları ve alt düzey fare ve klavye olayları.</span><span class="sxs-lookup"><span data-stu-id="a7c91-104">These include the <xref:System.Windows.Forms.Control.Paint> event, which causes a control to be drawn, events related to displaying a window, such as the <xref:System.Windows.Forms.Control.Resize> and <xref:System.Windows.Forms.Control.Layout> events, and low-level mouse and keyboard events.</span></span> <span data-ttu-id="a7c91-105">Alt düzey bazı olaylar tarafından oluşturulan <xref:System.Windows.Forms.Control> anlamsal olayları gibi içine <xref:System.Windows.Forms.Control.Click> ve <xref:System.Windows.Forms.Control.DoubleClick>.</span><span class="sxs-lookup"><span data-stu-id="a7c91-105">Some low-level events are synthesized by <xref:System.Windows.Forms.Control> into semantic events such as <xref:System.Windows.Forms.Control.Click> and <xref:System.Windows.Forms.Control.DoubleClick>.</span></span> <span data-ttu-id="a7c91-106">Devralınan olaylar hakkında daha fazla ayrıntı için bkz: <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="a7c91-106">For details about inherited events, see <xref:System.Windows.Forms.Control>.</span></span>  
  
 <span data-ttu-id="a7c91-107">Özel denetim devralınmış olay işlevi geçersiz kılması gerekiyorsa, devralınan geçersiz kılma `On` *EventName* temsilci ekleme yerine yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a7c91-107">If your custom control needs to override inherited event functionality, override the inherited `On`*EventName* method instead of attaching a delegate.</span></span> <span data-ttu-id="a7c91-108">.NET Framework olay modelinde alışık değilseniz bkz [oluşturma olayları bir bileşenin](http://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).</span><span class="sxs-lookup"><span data-stu-id="a7c91-108">If you are not familiar with the event model in the .NET Framework, see [Raising Events from a Component](http://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7c91-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a7c91-109">See Also</span></span>  
 [<span data-ttu-id="a7c91-110">OnPaint yöntemini geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="a7c91-110">Overriding the OnPaint Method</span></span>](../../../../docs/framework/winforms/controls/overriding-the-onpaint-method.md)  
 [<span data-ttu-id="a7c91-111">Kullanıcı girişini işleme</span><span class="sxs-lookup"><span data-stu-id="a7c91-111">Handling User Input</span></span>](../../../../docs/framework/winforms/controls/handling-user-input.md)  
 [<span data-ttu-id="a7c91-112">Olay tanımlama</span><span class="sxs-lookup"><span data-stu-id="a7c91-112">Defining an Event</span></span>](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)  
 [<span data-ttu-id="a7c91-113">Olayları</span><span class="sxs-lookup"><span data-stu-id="a7c91-113">Events</span></span>](../../../../docs/standard/events/index.md)
