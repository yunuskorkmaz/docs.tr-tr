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
ms.openlocfilehash: 3ebe82fc18deba52fafe76da7ff85fb247446e46
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074962"
---
# <a name="handling-user-input"></a><span data-ttu-id="6b74e-102">Kullanıcı Girişini İşleme</span><span class="sxs-lookup"><span data-stu-id="6b74e-102">Handling User Input</span></span>
<span data-ttu-id="6b74e-103">Bu konu tarafından sağlanan ana klavye ve fare olayları açıklar <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6b74e-103">This topic describes the main keyboard and mouse events provided by <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6b74e-104">Bir olay işleme, denetim yazarları korumalı geçersiz kılmalıdır `On` *EventName* bir temsilci olaya eklemek yerine yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6b74e-104">When handling an event, control authors should override the protected `On`*EventName* method rather than attaching a delegate to the event.</span></span> <span data-ttu-id="6b74e-105">Olayları gözden geçirmek için bkz: [Raising Events bir bileşenin](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="6b74e-105">For a review of events, see [Raising Events from a Component](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6b74e-106">Bir olay, temel sınıfın bir örneği ile ilişkili hiçbir veri olup olmadığını <xref:System.EventArgs> bağımsız değişken olarak geçirilen `On` *EventName* yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6b74e-106">If there is no data associated with an event, an instance of the base class <xref:System.EventArgs> is passed as an argument to the `On`*EventName* method.</span></span>  
  
## <a name="keyboard-events"></a><span data-ttu-id="6b74e-107">Klavye olayları</span><span class="sxs-lookup"><span data-stu-id="6b74e-107">Keyboard Events</span></span>  
 <span data-ttu-id="6b74e-108">Denetiminiz işleyebileceği ortak klavye olayları <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>, ve <xref:System.Windows.Forms.Control.KeyUp>.</span><span class="sxs-lookup"><span data-stu-id="6b74e-108">The common keyboard events that your control can handle are <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>, and <xref:System.Windows.Forms.Control.KeyUp>.</span></span>  
  
|<span data-ttu-id="6b74e-109">Olay adı</span><span class="sxs-lookup"><span data-stu-id="6b74e-109">Event Name</span></span>|<span data-ttu-id="6b74e-110">Geçersiz kılma yöntemi</span><span class="sxs-lookup"><span data-stu-id="6b74e-110">Method to Override</span></span>|<span data-ttu-id="6b74e-111">Olay açıklaması</span><span class="sxs-lookup"><span data-stu-id="6b74e-111">Description of Event</span></span>|  
|----------------|------------------------|--------------------------|  
|`KeyDown`|`void OnKeyDown(KeyEventArgs)`|<span data-ttu-id="6b74e-112">Yalnızca bir anahtar başlangıçta basıldığında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6b74e-112">Raised only when a key is initially pressed.</span></span>|  
|`KeyPress`|`void OnKeyPress`<br /><br /> `(KeyPressEventArgs)`|<span data-ttu-id="6b74e-113">Bir tuşa basıldığında her zaman oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6b74e-113">Raised every time a key is pressed.</span></span> <span data-ttu-id="6b74e-114">Bir anahtar aşağı yapılmazsa bir <xref:System.Windows.Forms.Control.KeyPress> olayı işletim sistemi tarafından tanımlanan yineleme hızında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6b74e-114">If a key is held down, a <xref:System.Windows.Forms.Control.KeyPress> event is raised at the repeat rate defined by the operating system.</span></span>|  
|`KeyUp`|`void OnKeyUp(KeyEventArgs)`|<span data-ttu-id="6b74e-115">Bir tuş bırakıldığında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6b74e-115">Raised when a key is released.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="6b74e-116">Klavye girişini işleme olayları önceki tabloda geçersiz kılma daha önemli ölçüde daha karmaşıktır ve bu konunun kapsamı dışındadır.</span><span class="sxs-lookup"><span data-stu-id="6b74e-116">Handling keyboard input is considerably more complex than overriding the events in the preceding table and is beyond the scope of this topic.</span></span> <span data-ttu-id="6b74e-117">Daha fazla bilgi için [Windows Forms'ta kullanıcı girdisi](../user-input-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="6b74e-117">For more information, see [User Input in Windows Forms](../user-input-in-windows-forms.md).</span></span>  
  
## <a name="mouse-events"></a><span data-ttu-id="6b74e-118">Fare olayları</span><span class="sxs-lookup"><span data-stu-id="6b74e-118">Mouse Events</span></span>  
 <span data-ttu-id="6b74e-119">Denetiminiz işleyebilir fare olayları <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseHover>, <xref:System.Windows.Forms.Control.MouseLeave>, <xref:System.Windows.Forms.Control.MouseMove>, ve <xref:System.Windows.Forms.Control.MouseUp>.</span><span class="sxs-lookup"><span data-stu-id="6b74e-119">The mouse events that your control can handle are <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseHover>, <xref:System.Windows.Forms.Control.MouseLeave>, <xref:System.Windows.Forms.Control.MouseMove>, and <xref:System.Windows.Forms.Control.MouseUp>.</span></span>  
  
|<span data-ttu-id="6b74e-120">Olay adı</span><span class="sxs-lookup"><span data-stu-id="6b74e-120">Event Name</span></span>|<span data-ttu-id="6b74e-121">Geçersiz kılma yöntemi</span><span class="sxs-lookup"><span data-stu-id="6b74e-121">Method to Override</span></span>|<span data-ttu-id="6b74e-122">Olay açıklaması</span><span class="sxs-lookup"><span data-stu-id="6b74e-122">Description of Event</span></span>|  
|----------------|------------------------|--------------------------|  
|`MouseDown`|`void OnMouseDown(MouseEventArgs)`|<span data-ttu-id="6b74e-123">İşaretçi denetimin üzerine üzerindeyken fare düğmesine basıldığında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6b74e-123">Raised when the mouse button is pressed while the pointer is over the control.</span></span>|  
|`MouseEnter`|`void OnMouseEnter(EventArgs)`|<span data-ttu-id="6b74e-124">İşaretçi denetimin bölge ilk girdiğinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6b74e-124">Raised when the pointer first enters the region of the control.</span></span>|  
|`MouseHover`|`void OnMouseHover(EventArgs)`|<span data-ttu-id="6b74e-125">İşaretçi denetimin üzerine geldiğinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6b74e-125">Raised when the pointer hovers over the control.</span></span>|  
|`MouseLeave`|`void OnMouseLeave(EventArgs)`|<span data-ttu-id="6b74e-126">İşaretçi denetimin bölge ayrıldığında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6b74e-126">Raised when the pointer leaves the region of the control.</span></span>|  
|`MouseMove`|`void OnMouseMove(MouseEventArgs)`|<span data-ttu-id="6b74e-127">İşaretçiyi denetimin bölgede hareket ettiğinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6b74e-127">Raised when the pointer moves in the region of the control.</span></span>|  
|`MouseUp`|`void OnMouseUp(MouseEventArgs)`|<span data-ttu-id="6b74e-128">Fare düğmesi denetimin üzerine işaretçiyse veya işaretçiyi denetimin bölge ayrıldığında bırakıldığında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6b74e-128">Raised when the mouse button is released while the pointer is over the control or the pointer leaves the region of the control.</span></span>|  
  
 <span data-ttu-id="6b74e-129">Aşağıdaki kod parçası, geçersiz kılma bir örnek gösterilmektedir <xref:System.Windows.Forms.Control.MouseDown> olay.</span><span class="sxs-lookup"><span data-stu-id="6b74e-129">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseDown> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#7)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#7)]  
  
 <span data-ttu-id="6b74e-130">Aşağıdaki kod parçası, geçersiz kılma bir örnek gösterilmektedir <xref:System.Windows.Forms.Control.MouseMove> olay.</span><span class="sxs-lookup"><span data-stu-id="6b74e-130">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseMove> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#8)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#8)]  
  
 <span data-ttu-id="6b74e-131">Aşağıdaki kod parçası, geçersiz kılma bir örnek gösterilmektedir <xref:System.Windows.Forms.Control.MouseUp> olay.</span><span class="sxs-lookup"><span data-stu-id="6b74e-131">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseUp> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#9)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#9)]  
  
 <span data-ttu-id="6b74e-132">İçin tam kaynak kodu `FlashTrackBar` örnek için bkz: [nasıl yapılır: İlerleme durumunu gösteren Windows Forms denetimi oluşturma](how-to-create-a-windows-forms-control-that-shows-progress.md).</span><span class="sxs-lookup"><span data-stu-id="6b74e-132">For the complete source code for the `FlashTrackBar` sample, see [How to: Create a Windows Forms Control That Shows Progress](how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b74e-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b74e-133">See also</span></span>

- [<span data-ttu-id="6b74e-134">Windows Forms Denetimlerindeki Olaylar</span><span class="sxs-lookup"><span data-stu-id="6b74e-134">Events in Windows Forms Controls</span></span>](events-in-windows-forms-controls.md)
- [<span data-ttu-id="6b74e-135">Olay Tanımlama</span><span class="sxs-lookup"><span data-stu-id="6b74e-135">Defining an Event</span></span>](defining-an-event-in-windows-forms-controls.md)
- [<span data-ttu-id="6b74e-136">Olaylar</span><span class="sxs-lookup"><span data-stu-id="6b74e-136">Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="6b74e-137">Windows Forms'ta Kullanıcı Girdisi</span><span class="sxs-lookup"><span data-stu-id="6b74e-137">User Input in Windows Forms</span></span>](../user-input-in-windows-forms.md)
