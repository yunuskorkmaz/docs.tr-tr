---
title: Denetimlerindeki olaylar
ms.date: 03/30/2017
helpviewer_keywords:
- events [Windows Forms], custom controls (using code)
- custom controls [Windows Forms], events overview (using code)
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
ms.openlocfilehash: c60713917b9c84aa7fad50fb1c81fc9252149ad6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745759"
---
# <a name="events-in-windows-forms-controls"></a><span data-ttu-id="9dd6e-102">Windows Forms Denetimlerindeki Olaylar</span><span class="sxs-lookup"><span data-stu-id="9dd6e-102">Events in Windows Forms Controls</span></span>
<span data-ttu-id="9dd6e-103">Windows Forms denetimi <xref:System.Windows.Forms.Control?displayProperty=nameWithType>60 'den fazla olayı devralır.</span><span class="sxs-lookup"><span data-stu-id="9dd6e-103">A Windows Forms control inherits more than sixty events from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9dd6e-104">Bunlar, bir denetimin çizilmesine neden olan <xref:System.Windows.Forms.Control.Paint> olayını, <xref:System.Windows.Forms.Control.Resize> ve <xref:System.Windows.Forms.Control.Layout> olayları ve alt düzey fare ve klavye olayları gibi bir pencereyi görüntüleme ile ilgili olayları içerir.</span><span class="sxs-lookup"><span data-stu-id="9dd6e-104">These include the <xref:System.Windows.Forms.Control.Paint> event, which causes a control to be drawn, events related to displaying a window, such as the <xref:System.Windows.Forms.Control.Resize> and <xref:System.Windows.Forms.Control.Layout> events, and low-level mouse and keyboard events.</span></span> <span data-ttu-id="9dd6e-105">Bazı düşük düzey olaylar, <xref:System.Windows.Forms.Control.Click> ve <xref:System.Windows.Forms.Control.DoubleClick>gibi semantik olaylara <xref:System.Windows.Forms.Control> birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="9dd6e-105">Some low-level events are synthesized by <xref:System.Windows.Forms.Control> into semantic events such as <xref:System.Windows.Forms.Control.Click> and <xref:System.Windows.Forms.Control.DoubleClick>.</span></span> <span data-ttu-id="9dd6e-106">Devralınan olaylar hakkında daha fazla bilgi için bkz. <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="9dd6e-106">For details about inherited events, see <xref:System.Windows.Forms.Control>.</span></span>  
  
 <span data-ttu-id="9dd6e-107">Özel denetiminizin devralınan olay işlevselliğini geçersiz kılması gerekiyorsa, bir temsilci eklemek yerine devralınan `On`*EventName* metodunu geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="9dd6e-107">If your custom control needs to override inherited event functionality, override the inherited `On`*EventName* method instead of attaching a delegate.</span></span> <span data-ttu-id="9dd6e-108">.NET Framework olay modelini bilmiyorsanız, bkz. [bir bileşenden olayları yükseltme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="9dd6e-108">If you are not familiar with the event model in the .NET Framework, see [Raising Events from a Component](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dd6e-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9dd6e-109">See also</span></span>

- [<span data-ttu-id="9dd6e-110">OnPaint Yöntemini Geçersiz Kılma</span><span class="sxs-lookup"><span data-stu-id="9dd6e-110">Overriding the OnPaint Method</span></span>](overriding-the-onpaint-method.md)
- [<span data-ttu-id="9dd6e-111">Kullanıcı Girişini İşleme</span><span class="sxs-lookup"><span data-stu-id="9dd6e-111">Handling User Input</span></span>](handling-user-input.md)
- [<span data-ttu-id="9dd6e-112">Olay Tanımlama</span><span class="sxs-lookup"><span data-stu-id="9dd6e-112">Defining an Event</span></span>](defining-an-event-in-windows-forms-controls.md)
- [<span data-ttu-id="9dd6e-113">Olaylar</span><span class="sxs-lookup"><span data-stu-id="9dd6e-113">Events</span></span>](../../../standard/events/index.md)
