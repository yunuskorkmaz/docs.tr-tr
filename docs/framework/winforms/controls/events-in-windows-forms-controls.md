---
title: Windows Forms Denetimlerindeki Olaylar
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], custom controls (using code)
- custom controls [Windows Forms], events overview (using code)
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
ms.openlocfilehash: 253783f50fdbef0890ea16baa9ac996b63795ed8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716973"
---
# <a name="events-in-windows-forms-controls"></a><span data-ttu-id="5f14f-102">Windows Forms Denetimlerindeki Olaylar</span><span class="sxs-lookup"><span data-stu-id="5f14f-102">Events in Windows Forms Controls</span></span>
<span data-ttu-id="5f14f-103">Bir Windows Forms denetimi altmış daha olaylardan devralan <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5f14f-103">A Windows Forms control inherits more than sixty events from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5f14f-104">Bunlar <xref:System.Windows.Forms.Control.Paint> çizilecek denetim neden olan olayı, bir pencere gibi görüntülemek için ilgili olayları <xref:System.Windows.Forms.Control.Resize> ve <xref:System.Windows.Forms.Control.Layout> olayları ve alt düzey fare ve klavye olayları.</span><span class="sxs-lookup"><span data-stu-id="5f14f-104">These include the <xref:System.Windows.Forms.Control.Paint> event, which causes a control to be drawn, events related to displaying a window, such as the <xref:System.Windows.Forms.Control.Resize> and <xref:System.Windows.Forms.Control.Layout> events, and low-level mouse and keyboard events.</span></span> <span data-ttu-id="5f14f-105">Alt düzey bazı olaylar tarafından oluşturulan <xref:System.Windows.Forms.Control> gibi anlamsal olaylara <xref:System.Windows.Forms.Control.Click> ve <xref:System.Windows.Forms.Control.DoubleClick>.</span><span class="sxs-lookup"><span data-stu-id="5f14f-105">Some low-level events are synthesized by <xref:System.Windows.Forms.Control> into semantic events such as <xref:System.Windows.Forms.Control.Click> and <xref:System.Windows.Forms.Control.DoubleClick>.</span></span> <span data-ttu-id="5f14f-106">Devralınan olaylar hakkında daha fazla ayrıntı için bkz: <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="5f14f-106">For details about inherited events, see <xref:System.Windows.Forms.Control>.</span></span>  
  
 <span data-ttu-id="5f14f-107">Özel denetiminizi devralınan olay işlevi geçersiz kılması gerekiyorsa, devralınan geçersiz kılma `On` *EventName* yerine temsilci ekleme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5f14f-107">If your custom control needs to override inherited event functionality, override the inherited `On`*EventName* method instead of attaching a delegate.</span></span> <span data-ttu-id="5f14f-108">.NET Framework'teki olay modeline alışkın değilseniz bkz [Raising Events bir bileşenin](https://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).</span><span class="sxs-lookup"><span data-stu-id="5f14f-108">If you are not familiar with the event model in the .NET Framework, see [Raising Events from a Component](https://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f14f-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f14f-109">See also</span></span>
- [<span data-ttu-id="5f14f-110">OnPaint Yöntemini Geçersiz Kılma</span><span class="sxs-lookup"><span data-stu-id="5f14f-110">Overriding the OnPaint Method</span></span>](../../../../docs/framework/winforms/controls/overriding-the-onpaint-method.md)
- [<span data-ttu-id="5f14f-111">Kullanıcı Girişini İşleme</span><span class="sxs-lookup"><span data-stu-id="5f14f-111">Handling User Input</span></span>](../../../../docs/framework/winforms/controls/handling-user-input.md)
- [<span data-ttu-id="5f14f-112">Olay Tanımlama</span><span class="sxs-lookup"><span data-stu-id="5f14f-112">Defining an Event</span></span>](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)
- [<span data-ttu-id="5f14f-113">Olaylar</span><span class="sxs-lookup"><span data-stu-id="5f14f-113">Events</span></span>](../../../../docs/standard/events/index.md)
