---
title: Özellik Değişti Olayları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property changes (using code)
- properties [Windows Forms], changes
ms.assetid: 268039ec-5aaa-4d76-b902-acccb036c850
ms.openlocfilehash: cabfd9e799288a332a0b2f96140f5f1cc328508b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755434"
---
# <a name="property-changed-events"></a><span data-ttu-id="77ce8-102">Özellik Değişti Olayları</span><span class="sxs-lookup"><span data-stu-id="77ce8-102">Property-Changed Events</span></span>
<span data-ttu-id="77ce8-103">Adlı bir özellik bildirimleri göndermek için denetim istiyorsanız *PropertyName* değişiklikleri tanımlayın adlı bir olay *PropertyName* `Changed` ve adlı bir yöntem `On` *PropertyName* `Changed` , olayını başlatır.</span><span class="sxs-lookup"><span data-stu-id="77ce8-103">If you want your control to send notifications when a property named *PropertyName* changes, define an event named *PropertyName*`Changed` and a method named `On`*PropertyName*`Changed` that raises the event.</span></span> <span data-ttu-id="77ce8-104">Windows Forms'ta adlandırma kuralı kelimenin sonuna eklenecek olan *değiştirilen* özelliğinin adı.</span><span class="sxs-lookup"><span data-stu-id="77ce8-104">The naming convention in Windows Forms is to append the word *Changed* to the name of the property.</span></span> <span data-ttu-id="77ce8-105">Özellik değişti olayları için ilişkili olay temsilci türü <xref:System.EventHandler>, ve olay veri türü <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="77ce8-105">The associated event delegate type for property-changed events is <xref:System.EventHandler>, and the event data type is <xref:System.EventArgs>.</span></span> <span data-ttu-id="77ce8-106">Temel sınıf <xref:System.Windows.Forms.Control> gibi birçok özellik değişti olayları tanımlar <xref:System.Windows.Forms.Control.BackColorChanged>, <xref:System.Windows.Forms.Control.BackgroundImageChanged>, <xref:System.Windows.Forms.Control.FontChanged>, <xref:System.Windows.Forms.Control.LocationChanged>ve diğerleri.</span><span class="sxs-lookup"><span data-stu-id="77ce8-106">The base class <xref:System.Windows.Forms.Control> defines many property-changed events, such as <xref:System.Windows.Forms.Control.BackColorChanged>, <xref:System.Windows.Forms.Control.BackgroundImageChanged>, <xref:System.Windows.Forms.Control.FontChanged>, <xref:System.Windows.Forms.Control.LocationChanged>, and others.</span></span> <span data-ttu-id="77ce8-107">Olaylar hakkında bilgi için bkz: [olayları](../../../standard/events/index.md) ve [Windows Forms denetimlerindeki olaylar](events-in-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="77ce8-107">For background information about events, see [Events](../../../standard/events/index.md) and [Events in Windows Forms Controls](events-in-windows-forms-controls.md).</span></span>  
  
 <span data-ttu-id="77ce8-108">Özellik değişti olayları kullanışlı olduğu bunlara yanıt olay işleyicileri eklemek bir denetim tüketicilerinin sağlarlar.</span><span class="sxs-lookup"><span data-stu-id="77ce8-108">Property-changed events are useful because they allow consumers of a control to attach event handlers that respond to the change.</span></span> <span data-ttu-id="77ce8-109">Denetiminiz bilmemektedir özelliği değiştirilmiş bir olay yanıt vermesi, karşılık gelen geçersiz kılma `On` *PropertyName* `Changed` bir temsilci olaya eklemek yerine yöntemi.</span><span class="sxs-lookup"><span data-stu-id="77ce8-109">If your control needs to respond to a property-changed event that it raises, override the corresponding `On`*PropertyName*`Changed` method instead of attaching a delegate to the event.</span></span> <span data-ttu-id="77ce8-110">Bir denetimin diğer özelliklerini güncelleştirerek veya bazılarını veya tümünü, çizim yüzeyini yeniden tarafından bir özellik değişti olayı için genellikle yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="77ce8-110">A control typically responds to a property-changed event by updating other properties or by redrawing some or all of its drawing surface.</span></span>  
  
 <span data-ttu-id="77ce8-111">Aşağıdaki örnekte gösterildiği nasıl `FlashTrackBar` özel denetiminin vereceği yanıtı devraldığı özellik değişti olayları bazılarının <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="77ce8-111">The following example shows how the `FlashTrackBar` custom control responds to some of the property-changed events that it inherits from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="77ce8-112">Tam bir örnek için bkz [nasıl yapılır: İlerleme durumunu gösteren Windows Forms denetimi oluşturma](how-to-create-a-windows-forms-control-that-shows-progress.md).</span><span class="sxs-lookup"><span data-stu-id="77ce8-112">For the complete sample, see [How to: Create a Windows Forms Control That Shows Progress](how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#2)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="77ce8-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77ce8-113">See also</span></span>

- [<span data-ttu-id="77ce8-114">Olaylar</span><span class="sxs-lookup"><span data-stu-id="77ce8-114">Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="77ce8-115">Windows Forms Denetimlerindeki Olaylar</span><span class="sxs-lookup"><span data-stu-id="77ce8-115">Events in Windows Forms Controls</span></span>](events-in-windows-forms-controls.md)
- [<span data-ttu-id="77ce8-116">Windows Forms Denetimlerindeki Özellikler</span><span class="sxs-lookup"><span data-stu-id="77ce8-116">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
