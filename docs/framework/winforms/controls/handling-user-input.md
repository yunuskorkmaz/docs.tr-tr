---
title: Kullanıcı Girişini İşleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], user input using code
- custom controls [Windows Forms], keyboard events using code
- custom controls [Windows Forms], mouse events using code
ms.assetid: d9b12787-86f6-4022-8e0f-e12d312c4af2
ms.openlocfilehash: f92b742c3f6feec72e5b3150204d7d984636281d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934086"
---
# <a name="handling-user-input"></a><span data-ttu-id="fbe82-102">Kullanıcı Girişini İşleme</span><span class="sxs-lookup"><span data-stu-id="fbe82-102">Handling User Input</span></span>
<span data-ttu-id="fbe82-103">Bu konuda, tarafından <xref:System.Windows.Forms.Control?displayProperty=nameWithType>sunulan ana klavye ve fare olayları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fbe82-103">This topic describes the main keyboard and mouse events provided by <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fbe82-104">Bir olayı işlerken, Denetim yazarları olaya bir temsilci eklemek yerine `On`Protected *EventName* metodunu geçersiz kılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fbe82-104">When handling an event, control authors should override the protected `On`*EventName* method rather than attaching a delegate to the event.</span></span> <span data-ttu-id="fbe82-105">Olayları gözden geçirmek için bkz. [bir bileşenden olayları yükseltme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="fbe82-105">For a review of events, see [Raising Events from a Component](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fbe82-106">Bir olayla ilişkili veri yoksa, temel sınıfın <xref:System.EventArgs> bir örneği, *EventName* yöntemine bir bağımsız değişken `On`olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="fbe82-106">If there is no data associated with an event, an instance of the base class <xref:System.EventArgs> is passed as an argument to the `On`*EventName* method.</span></span>  
  
## <a name="keyboard-events"></a><span data-ttu-id="fbe82-107">Klavye olayları</span><span class="sxs-lookup"><span data-stu-id="fbe82-107">Keyboard Events</span></span>  
 <span data-ttu-id="fbe82-108">Denetiminizin işleyebileceği ortak klavye olayları, ve <xref:System.Windows.Forms.Control.KeyDown> <xref:System.Windows.Forms.Control.KeyUp>' dir <xref:System.Windows.Forms.Control.KeyPress>.</span><span class="sxs-lookup"><span data-stu-id="fbe82-108">The common keyboard events that your control can handle are <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>, and <xref:System.Windows.Forms.Control.KeyUp>.</span></span>  
  
|<span data-ttu-id="fbe82-109">Olay adı</span><span class="sxs-lookup"><span data-stu-id="fbe82-109">Event Name</span></span>|<span data-ttu-id="fbe82-110">Geçersiz kılınacak Yöntem</span><span class="sxs-lookup"><span data-stu-id="fbe82-110">Method to Override</span></span>|<span data-ttu-id="fbe82-111">Olayın açıklaması</span><span class="sxs-lookup"><span data-stu-id="fbe82-111">Description of Event</span></span>|  
|----------------|------------------------|--------------------------|  
|`KeyDown`|`void OnKeyDown(KeyEventArgs)`|<span data-ttu-id="fbe82-112">Yalnızca bir tuşa başlangıçta basıldığında tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="fbe82-112">Raised only when a key is initially pressed.</span></span>|  
|`KeyPress`|`void OnKeyPress`<br /><br /> `(KeyPressEventArgs)`|<span data-ttu-id="fbe82-113">Her tuşa basıldığında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="fbe82-113">Raised every time a key is pressed.</span></span> <span data-ttu-id="fbe82-114">Bir anahtar kapalıysa, işletim sistemi tarafından tanımlanan <xref:System.Windows.Forms.Control.KeyPress> yineleme hızında bir olay oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="fbe82-114">If a key is held down, a <xref:System.Windows.Forms.Control.KeyPress> event is raised at the repeat rate defined by the operating system.</span></span>|  
|`KeyUp`|`void OnKeyUp(KeyEventArgs)`|<span data-ttu-id="fbe82-115">Bir anahtar bırakıldığında tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="fbe82-115">Raised when a key is released.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="fbe82-116">Klavye girişini işlemek, yukarıdaki tablodaki olayları geçersiz kılmadan ve bu konunun kapsamının ötesinde önemli ölçüde karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="fbe82-116">Handling keyboard input is considerably more complex than overriding the events in the preceding table and is beyond the scope of this topic.</span></span> <span data-ttu-id="fbe82-117">Daha fazla bilgi için [Windows Forms Içindeki Kullanıcı girişi](../user-input-in-windows-forms.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="fbe82-117">For more information, see [User Input in Windows Forms](../user-input-in-windows-forms.md).</span></span>  
  
## <a name="mouse-events"></a><span data-ttu-id="fbe82-118">Fare olayları</span><span class="sxs-lookup"><span data-stu-id="fbe82-118">Mouse Events</span></span>  
 <span data-ttu-id="fbe82-119">Denetiminizin işleyebileceği fare olayları,,,, ve <xref:System.Windows.Forms.Control.MouseDown> <xref:System.Windows.Forms.Control.MouseHover> <xref:System.Windows.Forms.Control.MouseMove> <xref:System.Windows.Forms.Control.MouseEnter> <xref:System.Windows.Forms.Control.MouseLeave> 'dir<xref:System.Windows.Forms.Control.MouseUp>.</span><span class="sxs-lookup"><span data-stu-id="fbe82-119">The mouse events that your control can handle are <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseHover>, <xref:System.Windows.Forms.Control.MouseLeave>, <xref:System.Windows.Forms.Control.MouseMove>, and <xref:System.Windows.Forms.Control.MouseUp>.</span></span>  
  
|<span data-ttu-id="fbe82-120">Olay adı</span><span class="sxs-lookup"><span data-stu-id="fbe82-120">Event Name</span></span>|<span data-ttu-id="fbe82-121">Geçersiz kılınacak Yöntem</span><span class="sxs-lookup"><span data-stu-id="fbe82-121">Method to Override</span></span>|<span data-ttu-id="fbe82-122">Olayın açıklaması</span><span class="sxs-lookup"><span data-stu-id="fbe82-122">Description of Event</span></span>|  
|----------------|------------------------|--------------------------|  
|`MouseDown`|`void OnMouseDown(MouseEventArgs)`|<span data-ttu-id="fbe82-123">İşaretçi denetimin üzerindeyken fare düğmesine basıldığında tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="fbe82-123">Raised when the mouse button is pressed while the pointer is over the control.</span></span>|  
|`MouseEnter`|`void OnMouseEnter(EventArgs)`|<span data-ttu-id="fbe82-124">İşaretçi denetimin bölgesine ilk kez girdiğinde tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="fbe82-124">Raised when the pointer first enters the region of the control.</span></span>|  
|`MouseHover`|`void OnMouseHover(EventArgs)`|<span data-ttu-id="fbe82-125">İşaretçi denetimin üzerine geldiğinde tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="fbe82-125">Raised when the pointer hovers over the control.</span></span>|  
|`MouseLeave`|`void OnMouseLeave(EventArgs)`|<span data-ttu-id="fbe82-126">İşaretçi denetimin bölgesinden ayrıldığında tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="fbe82-126">Raised when the pointer leaves the region of the control.</span></span>|  
|`MouseMove`|`void OnMouseMove(MouseEventArgs)`|<span data-ttu-id="fbe82-127">İşaretçi denetimin bölgesinde ne zaman geçerse tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="fbe82-127">Raised when the pointer moves in the region of the control.</span></span>|  
|`MouseUp`|`void OnMouseUp(MouseEventArgs)`|<span data-ttu-id="fbe82-128">İşaretçi denetimin üzerindeyken fare düğmesi bırakıldığında veya işaretçi denetimin bölgesinden ayrıldığında tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="fbe82-128">Raised when the mouse button is released while the pointer is over the control or the pointer leaves the region of the control.</span></span>|  
  
 <span data-ttu-id="fbe82-129">Aşağıdaki kod parçası, <xref:System.Windows.Forms.Control.MouseDown> olayı geçersiz kılan bir örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="fbe82-129">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseDown> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#7)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#7)]  
  
 <span data-ttu-id="fbe82-130">Aşağıdaki kod parçası, <xref:System.Windows.Forms.Control.MouseMove> olayı geçersiz kılan bir örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="fbe82-130">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseMove> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#8)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#8)]  
  
 <span data-ttu-id="fbe82-131">Aşağıdaki kod parçası, <xref:System.Windows.Forms.Control.MouseUp> olayı geçersiz kılan bir örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="fbe82-131">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseUp> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#9)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#9)]  
  
 <span data-ttu-id="fbe82-132">`FlashTrackBar` Örnek için tüm kaynak kodu için bkz [. nasıl yapılır: Ilerleme durumunu](how-to-create-a-windows-forms-control-that-shows-progress.md)gösteren bir Windows Forms denetimi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fbe82-132">For the complete source code for the `FlashTrackBar` sample, see [How to: Create a Windows Forms Control That Shows Progress](how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbe82-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fbe82-133">See also</span></span>

- [<span data-ttu-id="fbe82-134">Windows Forms Denetimlerindeki Olaylar</span><span class="sxs-lookup"><span data-stu-id="fbe82-134">Events in Windows Forms Controls</span></span>](events-in-windows-forms-controls.md)
- [<span data-ttu-id="fbe82-135">Olay Tanımlama</span><span class="sxs-lookup"><span data-stu-id="fbe82-135">Defining an Event</span></span>](defining-an-event-in-windows-forms-controls.md)
- [<span data-ttu-id="fbe82-136">Olaylar</span><span class="sxs-lookup"><span data-stu-id="fbe82-136">Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="fbe82-137">Windows Forms'ta Kullanıcı Girdisi</span><span class="sxs-lookup"><span data-stu-id="fbe82-137">User Input in Windows Forms</span></span>](../user-input-in-windows-forms.md)
