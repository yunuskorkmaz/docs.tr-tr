---
title: "Özellik Değişti Olayları"
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
- custom controls [Windows Forms], property changes (using code)
- properties [Windows Forms], changes
ms.assetid: 268039ec-5aaa-4d76-b902-acccb036c850
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ad22d77043f00ab0caaa6d8b08b6b0a9eef1fed5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="property-changed-events"></a><span data-ttu-id="d2e9c-102">Özellik Değişti Olayları</span><span class="sxs-lookup"><span data-stu-id="d2e9c-102">Property-Changed Events</span></span>
<span data-ttu-id="d2e9c-103">Adlı bir özellik olduğunda bildirim göndermek için denetiminizi istiyorsanız *PropertyName* değişiklikleri tanımlamak adlı bir olay *PropertyName* `Changed` ve adlı bir yöntem `On` *PropertyName* `Changed` olayını başlatır.</span><span class="sxs-lookup"><span data-stu-id="d2e9c-103">If you want your control to send notifications when a property named *PropertyName* changes, define an event named *PropertyName*`Changed` and a method named `On`*PropertyName*`Changed` that raises the event.</span></span> <span data-ttu-id="d2e9c-104">Windows Forms'ta adlandırma kuralı word eklenecek olan *değiştirilen* özelliğinin adı.</span><span class="sxs-lookup"><span data-stu-id="d2e9c-104">The naming convention in Windows Forms is to append the word *Changed* to the name of the property.</span></span> <span data-ttu-id="d2e9c-105">Özellik değişti olayları için ilişkili olay temsilci türüdür <xref:System.EventHandler>, ve olay veri türü <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="d2e9c-105">The associated event delegate type for property-changed events is <xref:System.EventHandler>, and the event data type is <xref:System.EventArgs>.</span></span> <span data-ttu-id="d2e9c-106">Taban sınıfı <xref:System.Windows.Forms.Control> gibi pek çok özellik değişti olayları tanımlayan <xref:System.Windows.Forms.Control.BackColorChanged>, <xref:System.Windows.Forms.Control.BackgroundImageChanged>, <xref:System.Windows.Forms.Control.FontChanged>, <xref:System.Windows.Forms.Control.LocationChanged>ve diğerleri.</span><span class="sxs-lookup"><span data-stu-id="d2e9c-106">The base class <xref:System.Windows.Forms.Control> defines many property-changed events, such as <xref:System.Windows.Forms.Control.BackColorChanged>, <xref:System.Windows.Forms.Control.BackgroundImageChanged>, <xref:System.Windows.Forms.Control.FontChanged>, <xref:System.Windows.Forms.Control.LocationChanged>, and others.</span></span> <span data-ttu-id="d2e9c-107">Olaylar hakkında bilgi için bkz: [olayları](../../../../docs/standard/events/index.md) ve [Windows Forms denetimlerindeki olaylar](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="d2e9c-107">For background information about events, see [Events](../../../../docs/standard/events/index.md) and [Events in Windows Forms Controls](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md).</span></span>  
  
 <span data-ttu-id="d2e9c-108">Özellik değişti olayları değişiklik yanıt olay işleyicileri eklemek bir denetim tüketicileri izin için faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="d2e9c-108">Property-changed events are useful because they allow consumers of a control to attach event handlers that respond to the change.</span></span> <span data-ttu-id="d2e9c-109">Denetim yükseltir özelliği değiştirilmiş bir olaya yanıt vermesi, karşılık gelen geçersiz kılma `On` *PropertyName* `Changed` olaya bir temsilci ekleme yerine yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d2e9c-109">If your control needs to respond to a property-changed event that it raises, override the corresponding `On`*PropertyName*`Changed` method instead of attaching a delegate to the event.</span></span> <span data-ttu-id="d2e9c-110">Bir denetim diğer özelliklerini güncelleştirme veya bazılarını veya tümünü, çizim yüzeyini gerçekleşen bir özellik değişti olayı için genellikle yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="d2e9c-110">A control typically responds to a property-changed event by updating other properties or by redrawing some or all of its drawing surface.</span></span>  
  
 <span data-ttu-id="d2e9c-111">Aşağıdaki örnekte gösterildiği nasıl `FlashTrackBar` özel denetim yanıt öğesinden devralınan özellik değişti olayları, bazı <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="d2e9c-111">The following example shows how the `FlashTrackBar` custom control responds to some of the property-changed events that it inherits from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="d2e9c-112">Tam bir örnek için bkz: [nasıl yapılır: Windows Forms denetimi olduğunu gösteren ilerlemesi oluşturma](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).</span><span class="sxs-lookup"><span data-stu-id="d2e9c-112">For the complete sample, see [How to: Create a Windows Forms Control That Shows Progress](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#2)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d2e9c-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d2e9c-113">See Also</span></span>  
 [<span data-ttu-id="d2e9c-114">Olaylar</span><span class="sxs-lookup"><span data-stu-id="d2e9c-114">Events</span></span>](../../../../docs/standard/events/index.md)  
 [<span data-ttu-id="d2e9c-115">Windows Forms Denetimlerindeki Olaylar</span><span class="sxs-lookup"><span data-stu-id="d2e9c-115">Events in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)  
 [<span data-ttu-id="d2e9c-116">Windows Forms Denetimlerindeki Özellikler</span><span class="sxs-lookup"><span data-stu-id="d2e9c-116">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)
