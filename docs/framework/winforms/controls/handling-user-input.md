---
title: "Kullanıcı Girişini İşleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], user input using code
- custom controls [Windows Forms], keyboard events using code
- custom controls [Windows Forms], mouse events using code
ms.assetid: d9b12787-86f6-4022-8e0f-e12d312c4af2
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0102bab4fad3b224100ae054f572d9b07102fc15
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="handling-user-input"></a><span data-ttu-id="53e0b-102">Kullanıcı Girişini İşleme</span><span class="sxs-lookup"><span data-stu-id="53e0b-102">Handling User Input</span></span>
<span data-ttu-id="53e0b-103">Bu konu, tarafından sağlanan ana klavye ve fare olaylarını açıklar <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="53e0b-103">This topic describes the main keyboard and mouse events provided by <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="53e0b-104">Bir olay işlenirken denetim yazarları korumalı kılmalıdır `On` *EventName* olaya bir temsilci ekleme yerine yöntemi.</span><span class="sxs-lookup"><span data-stu-id="53e0b-104">When handling an event, control authors should override the protected `On`*EventName* method rather than attaching a delegate to the event.</span></span> <span data-ttu-id="53e0b-105">Olayları gözden geçirmek için bkz: [oluşturma olayları bir bileşenin](http://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).</span><span class="sxs-lookup"><span data-stu-id="53e0b-105">For a review of events, see [Raising Events from a Component](http://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53e0b-106">Temel sınıfının bir örneği bir olayla ilişkili veri olup olmadığını <xref:System.EventArgs> bağımsız değişken olarak geçirilen `On` *EventName* yöntemi.</span><span class="sxs-lookup"><span data-stu-id="53e0b-106">If there is no data associated with an event, an instance of the base class <xref:System.EventArgs> is passed as an argument to the `On`*EventName* method.</span></span>  
  
## <a name="keyboard-events"></a><span data-ttu-id="53e0b-107">Klavye olayları</span><span class="sxs-lookup"><span data-stu-id="53e0b-107">Keyboard Events</span></span>  
 <span data-ttu-id="53e0b-108">Denetim işleyebilir ortak klavye olaylar <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>, ve <xref:System.Windows.Forms.Control.KeyUp>.</span><span class="sxs-lookup"><span data-stu-id="53e0b-108">The common keyboard events that your control can handle are <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>, and <xref:System.Windows.Forms.Control.KeyUp>.</span></span>  
  
|<span data-ttu-id="53e0b-109">Olay adı</span><span class="sxs-lookup"><span data-stu-id="53e0b-109">Event Name</span></span>|<span data-ttu-id="53e0b-110">Geçersiz kılma yöntemi</span><span class="sxs-lookup"><span data-stu-id="53e0b-110">Method to Override</span></span>|<span data-ttu-id="53e0b-111">Olay açıklaması</span><span class="sxs-lookup"><span data-stu-id="53e0b-111">Description of Event</span></span>|  
|----------------|------------------------|--------------------------|  
|`KeyDown`|`void OnKeyDown(KeyEventArgs)`|<span data-ttu-id="53e0b-112">Yalnızca zaman bir anahtar başlangıçta basıldığında oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="53e0b-112">Raised only when a key is initially pressed.</span></span>|  
|`KeyPress`|`void OnKeyPress`<br /><br /> `(KeyPressEventArgs)`|<span data-ttu-id="53e0b-113">Bir tuşa her zaman oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="53e0b-113">Raised every time a key is pressed.</span></span> <span data-ttu-id="53e0b-114">Bir anahtar aşağı tutulursa bir <xref:System.Windows.Forms.Control.KeyPress> olayı, işletim sistemi tarafından tanımlanan yineleme oranı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="53e0b-114">If a key is held down, a <xref:System.Windows.Forms.Control.KeyPress> event is raised at the repeat rate defined by the operating system.</span></span>|  
|`KeyUp`|`void OnKeyUp(KeyEventArgs)`|<span data-ttu-id="53e0b-115">Bir anahtar yayımlandığında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="53e0b-115">Raised when a key is released.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="53e0b-116">Klavye girişini işleme yukarıdaki tabloda olayları geçersiz kılma daha önemli ölçüde daha karmaşıktır ve bu konunun kapsamı dışındadır.</span><span class="sxs-lookup"><span data-stu-id="53e0b-116">Handling keyboard input is considerably more complex than overriding the events in the preceding table and is beyond the scope of this topic.</span></span> <span data-ttu-id="53e0b-117">Daha fazla bilgi için bkz: [Windows Forms uygulamasında kullanıcı girdisi](../../../../docs/framework/winforms/user-input-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="53e0b-117">For more information, see [User Input in Windows Forms](../../../../docs/framework/winforms/user-input-in-windows-forms.md).</span></span>  
  
## <a name="mouse-events"></a><span data-ttu-id="53e0b-118">Fare olayları</span><span class="sxs-lookup"><span data-stu-id="53e0b-118">Mouse Events</span></span>  
 <span data-ttu-id="53e0b-119">Denetim işleyebilir fare olaylar <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseHover>, <xref:System.Windows.Forms.Control.MouseLeave>, <xref:System.Windows.Forms.Control.MouseMove>, ve <xref:System.Windows.Forms.Control.MouseUp>.</span><span class="sxs-lookup"><span data-stu-id="53e0b-119">The mouse events that your control can handle are <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseHover>, <xref:System.Windows.Forms.Control.MouseLeave>, <xref:System.Windows.Forms.Control.MouseMove>, and <xref:System.Windows.Forms.Control.MouseUp>.</span></span>  
  
|<span data-ttu-id="53e0b-120">Olay adı</span><span class="sxs-lookup"><span data-stu-id="53e0b-120">Event Name</span></span>|<span data-ttu-id="53e0b-121">Geçersiz kılma yöntemi</span><span class="sxs-lookup"><span data-stu-id="53e0b-121">Method to Override</span></span>|<span data-ttu-id="53e0b-122">Olay açıklaması</span><span class="sxs-lookup"><span data-stu-id="53e0b-122">Description of Event</span></span>|  
|----------------|------------------------|--------------------------|  
|`MouseDown`|`void OnMouseDown(MouseEventArgs)`|<span data-ttu-id="53e0b-123">İşaretçinin üzerinde denetim durumdayken fare düğmesini basılı tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="53e0b-123">Raised when the mouse button is pressed while the pointer is over the control.</span></span>|  
|`MouseEnter`|`void OnMouseEnter(EventArgs)`|<span data-ttu-id="53e0b-124">İşaretçinin ilk denetimi bölge girdiğinde oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="53e0b-124">Raised when the pointer first enters the region of the control.</span></span>|  
|`MouseHover`|`void OnMouseHover(EventArgs)`|<span data-ttu-id="53e0b-125">İşaretçi denetimin üzerine geldiğinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="53e0b-125">Raised when the pointer hovers over the control.</span></span>|  
|`MouseLeave`|`void OnMouseLeave(EventArgs)`|<span data-ttu-id="53e0b-126">İşaretçi denetimi bölge ayrıldığında oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="53e0b-126">Raised when the pointer leaves the region of the control.</span></span>|  
|`MouseMove`|`void OnMouseMove(MouseEventArgs)`|<span data-ttu-id="53e0b-127">İşaretçi denetimi bölgede geldiğinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="53e0b-127">Raised when the pointer moves in the region of the control.</span></span>|  
|`MouseUp`|`void OnMouseUp(MouseEventArgs)`|<span data-ttu-id="53e0b-128">Fare düğmesini işaretçinin üzerinde denetim veya işaretçinin denetimi bölge bırakır kullanımdayken yayımlandığında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="53e0b-128">Raised when the mouse button is released while the pointer is over the control or the pointer leaves the region of the control.</span></span>|  
  
 <span data-ttu-id="53e0b-129">Aşağıdaki kod parçası geçersiz kılma örneği gösterir <xref:System.Windows.Forms.Control.MouseDown> olay.</span><span class="sxs-lookup"><span data-stu-id="53e0b-129">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseDown> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#7)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#7)]  
  
 <span data-ttu-id="53e0b-130">Aşağıdaki kod parçası geçersiz kılma örneği gösterir <xref:System.Windows.Forms.Control.MouseMove> olay.</span><span class="sxs-lookup"><span data-stu-id="53e0b-130">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseMove> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#8)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#8)]  
  
 <span data-ttu-id="53e0b-131">Aşağıdaki kod parçası geçersiz kılma örneği gösterir <xref:System.Windows.Forms.Control.MouseUp> olay.</span><span class="sxs-lookup"><span data-stu-id="53e0b-131">The following code fragment shows an example of overriding the <xref:System.Windows.Forms.Control.MouseUp> event.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#9)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#9)]  
  
 <span data-ttu-id="53e0b-132">İçin tam kaynak kodu `FlashTrackBar` örnek için bkz: [nasıl yapılır: Windows Forms denetimi olduğunu gösteren ilerlemesi oluşturma](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).</span><span class="sxs-lookup"><span data-stu-id="53e0b-132">For the complete source code for the `FlashTrackBar` sample, see [How to: Create a Windows Forms Control That Shows Progress](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53e0b-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="53e0b-133">See Also</span></span>  
 [<span data-ttu-id="53e0b-134">Windows Forms Denetimlerindeki Olaylar</span><span class="sxs-lookup"><span data-stu-id="53e0b-134">Events in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)  
 [<span data-ttu-id="53e0b-135">Olay Tanımlama</span><span class="sxs-lookup"><span data-stu-id="53e0b-135">Defining an Event</span></span>](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)  
 [<span data-ttu-id="53e0b-136">Olaylar</span><span class="sxs-lookup"><span data-stu-id="53e0b-136">Events</span></span>](../../../../docs/standard/events/index.md)  
 [<span data-ttu-id="53e0b-137">Windows Forms'ta Kullanıcı Girdisi</span><span class="sxs-lookup"><span data-stu-id="53e0b-137">User Input in Windows Forms</span></span>](../../../../docs/framework/winforms/user-input-in-windows-forms.md)
