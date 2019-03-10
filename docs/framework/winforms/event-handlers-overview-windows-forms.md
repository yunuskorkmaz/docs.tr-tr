---
title: Olay İşleyicilerine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, event handling
- event handling [Windows Forms], Windows Forms
- event handlers [Windows Forms], about event handlers
ms.assetid: 228112e1-1711-42ee-8ffa-ff3555bffe66
ms.openlocfilehash: 6dbcffadfd484dc33db2fcd3ee3f680dcc0740e5
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703396"
---
# <a name="event-handlers-overview-windows-forms"></a><span data-ttu-id="950d8-102">Olay İşleyicilerine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="950d8-102">Event Handlers Overview (Windows Forms)</span></span>
<span data-ttu-id="950d8-103">Bir olay işleyicisi olaya bağlı olan bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="950d8-103">An event handler is a method that is bound to an event.</span></span> <span data-ttu-id="950d8-104">Bir olay oluştuğunda, olay işleyicisi içindeki kod yürütülür.</span><span class="sxs-lookup"><span data-stu-id="950d8-104">When the event is raised, the code within the event handler is executed.</span></span> <span data-ttu-id="950d8-105">Her bir olay işleyicisi doğru olayı işlemek izin veren iki parametre sağlar.</span><span class="sxs-lookup"><span data-stu-id="950d8-105">Each event handler provides two parameters that allow you to handle the event properly.</span></span> <span data-ttu-id="950d8-106">Aşağıdaki örnek, bir olay işleyicisi için gösterir. bir <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Click> olay.</span><span class="sxs-lookup"><span data-stu-id="950d8-106">The following example shows an event handler for a <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event.</span></span>  
  
```vb  
Private Sub button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles button1.Click  
  
End Sub  
```  
  
```csharp  
private void button1_Click(object sender, System.EventArgs e)   
{  
  
}  
```  
  
```cpp  
private:  
  void button1_Click(System::Object ^ sender,  
    System::EventArgs ^ e)  
  {  
  
  }  
```  
  
 <span data-ttu-id="950d8-107">İlk parametre`sender`, olayı oluşturan nesneye bir başvuru sağlar.</span><span class="sxs-lookup"><span data-stu-id="950d8-107">The first parameter,`sender`, provides a reference to the object that raised the event.</span></span> <span data-ttu-id="950d8-108">İkinci parametre `e`, yukarıdaki örnekte, bir nesne belirli o anda işlenen olay geçirir.</span><span class="sxs-lookup"><span data-stu-id="950d8-108">The second parameter, `e`, in the example above, passes an object specific to the event that is being handled.</span></span> <span data-ttu-id="950d8-109">Nesnenin özelliklerini (ve bazı durumlarda, metotlarını) başvurarak fare olayları ya da sürükle ve bırak olayları aktarılan veri için fare konumu gibi bilgiler elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="950d8-109">By referencing the object's properties (and, sometimes, its methods), you can obtain information such as the location of the mouse for mouse events or data being transferred in drag-and-drop events.</span></span>  
  
 <span data-ttu-id="950d8-110">Genellikle her olay ikinci parametre için farklı olay nesne türüne sahip bir olay işleyicisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="950d8-110">Typically each event produces an event handler with a different event-object type for the second parameter.</span></span> <span data-ttu-id="950d8-111">Yönelik olanlar gibi bazı olay işleyicileri <xref:System.Windows.Forms.Control.MouseDown> ve <xref:System.Windows.Forms.Control.MouseUp> olaylar, aynı nesne türünü, ikinci parametresinin sahiptir.</span><span class="sxs-lookup"><span data-stu-id="950d8-111">Some event handlers, such as those for the <xref:System.Windows.Forms.Control.MouseDown> and <xref:System.Windows.Forms.Control.MouseUp> events, have the same object type for their second parameter.</span></span> <span data-ttu-id="950d8-112">Bu tür olaylar için her iki olayları işlemek için aynı olay işleyicisi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="950d8-112">For these types of events, you can use the same event handler to handle both events.</span></span>  
  
 <span data-ttu-id="950d8-113">Aynı olay işleyicisi, farklı denetimler için aynı olayı işlemek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="950d8-113">You can also use the same event handler to handle the same event for different controls.</span></span> <span data-ttu-id="950d8-114">Örneğin, bir grup varsa <xref:System.Windows.Forms.RadioButton> bir form üzerinde denetimleri için tek olay işleyicisine oluşturabilir <xref:System.Windows.Forms.Control.Click> olay ve her bir denetimin <xref:System.Windows.Forms.Control.Click> olayını tek olay işleyicisine bağlı.</span><span class="sxs-lookup"><span data-stu-id="950d8-114">For example, if you have a group of <xref:System.Windows.Forms.RadioButton> controls on a form, you could create a single event handler for the <xref:System.Windows.Forms.Control.Click> event and have each control's <xref:System.Windows.Forms.Control.Click> event bound to the single event handler.</span></span> <span data-ttu-id="950d8-115">Daha fazla bilgi için [nasıl yapılır: Windows Forms'ta tek olay işleyicisine birden fazla olay bağlama](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="950d8-115">For more information, see [How to: Connect Multiple Events to a Single Event Handler in Windows Forms](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="950d8-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="950d8-116">See also</span></span>
- [<span data-ttu-id="950d8-117">Windows Forms'ta Olay İşleyicileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="950d8-117">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="950d8-118">Olaylara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="950d8-118">Events Overview</span></span>](events-overview-windows-forms.md)
