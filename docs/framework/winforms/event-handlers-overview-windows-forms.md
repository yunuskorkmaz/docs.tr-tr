---
title: Olay İşleyicilerine Genel Bakış
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
ms.openlocfilehash: 10ba458197973ede35849a86fec35003f139b8d2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743462"
---
# <a name="event-handlers-overview-windows-forms"></a><span data-ttu-id="cb97e-102">Olay İşleyicilerine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="cb97e-102">Event Handlers Overview (Windows Forms)</span></span>
<span data-ttu-id="cb97e-103">Olay işleyicisi, bir olaya bağlanan bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="cb97e-103">An event handler is a method that is bound to an event.</span></span> <span data-ttu-id="cb97e-104">Olay ortaya çıktığında, olay işleyicisi içindeki kod yürütülür.</span><span class="sxs-lookup"><span data-stu-id="cb97e-104">When the event is raised, the code within the event handler is executed.</span></span> <span data-ttu-id="cb97e-105">Her olay işleyicisi, olayı doğru bir şekilde işleyebilmeniz için iki parametre sağlar.</span><span class="sxs-lookup"><span data-stu-id="cb97e-105">Each event handler provides two parameters that allow you to handle the event properly.</span></span> <span data-ttu-id="cb97e-106">Aşağıdaki örnekte, bir <xref:System.Windows.Forms.Button> denetiminin <xref:System.Windows.Forms.Control.Click> olayı için bir olay işleyicisi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cb97e-106">The following example shows an event handler for a <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event.</span></span>  
  
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
  
 <span data-ttu-id="cb97e-107">`sender`ilk parametresi, olayı oluşturan nesneye bir başvuru sağlar.</span><span class="sxs-lookup"><span data-stu-id="cb97e-107">The first parameter,`sender`, provides a reference to the object that raised the event.</span></span> <span data-ttu-id="cb97e-108">Yukarıdaki örnekte `e`ikinci parametresi, işlenmekte olan olaya özgü bir nesne geçirir.</span><span class="sxs-lookup"><span data-stu-id="cb97e-108">The second parameter, `e`, in the example above, passes an object specific to the event that is being handled.</span></span> <span data-ttu-id="cb97e-109">Nesnenin özelliklerine (ve bazen yöntemlerine) başvurarak, fare olayları veya sürükle ve bırak olaylarında aktarılan veriler için fare konumu gibi bilgileri elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cb97e-109">By referencing the object's properties (and, sometimes, its methods), you can obtain information such as the location of the mouse for mouse events or data being transferred in drag-and-drop events.</span></span>  
  
 <span data-ttu-id="cb97e-110">Genellikle her olay, ikinci parametre için farklı bir olay nesnesi türüne sahip bir olay işleyicisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cb97e-110">Typically each event produces an event handler with a different event-object type for the second parameter.</span></span> <span data-ttu-id="cb97e-111"><xref:System.Windows.Forms.Control.MouseDown> ve <xref:System.Windows.Forms.Control.MouseUp> olayları gibi bazı olay işleyicileri, ikinci parametreleri için aynı nesne türüne sahiptir.</span><span class="sxs-lookup"><span data-stu-id="cb97e-111">Some event handlers, such as those for the <xref:System.Windows.Forms.Control.MouseDown> and <xref:System.Windows.Forms.Control.MouseUp> events, have the same object type for their second parameter.</span></span> <span data-ttu-id="cb97e-112">Bu olay türleri için, her iki olayı da işlemek üzere aynı olay işleyicisini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cb97e-112">For these types of events, you can use the same event handler to handle both events.</span></span>  
  
 <span data-ttu-id="cb97e-113">Aynı olay işleyicisini farklı denetimler için aynı olayı işlemek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cb97e-113">You can also use the same event handler to handle the same event for different controls.</span></span> <span data-ttu-id="cb97e-114">Örneğin, bir formda <xref:System.Windows.Forms.RadioButton> denetimleri grubunuz varsa, <xref:System.Windows.Forms.Control.Click> olayı için tek bir olay işleyicisi oluşturabilir ve her bir denetimin <xref:System.Windows.Forms.Control.Click> olayının tek olay işleyicisine bağlı olmasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cb97e-114">For example, if you have a group of <xref:System.Windows.Forms.RadioButton> controls on a form, you could create a single event handler for the <xref:System.Windows.Forms.Control.Click> event and have each control's <xref:System.Windows.Forms.Control.Click> event bound to the single event handler.</span></span> <span data-ttu-id="cb97e-115">Daha fazla bilgi için bkz. [nasıl yapılır: birden çok olayı Windows Forms Içindeki tek bir olay Işleyicisine bağlama](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="cb97e-115">For more information, see [How to: Connect Multiple Events to a Single Event Handler in Windows Forms](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb97e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb97e-116">See also</span></span>

- [<span data-ttu-id="cb97e-117">Windows Forms'ta Olay İşleyicileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="cb97e-117">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="cb97e-118">Olaylara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cb97e-118">Events Overview</span></span>](events-overview-windows-forms.md)
