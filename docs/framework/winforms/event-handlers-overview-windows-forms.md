---
title: "Olay İşleyicilerine Genel Bakış (Windows Forms)"
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
- cpp
helpviewer_keywords:
- Windows Forms, event handling
- event handling [Windows Forms], Windows Forms
- event handlers [Windows Forms], about event handlers
ms.assetid: 228112e1-1711-42ee-8ffa-ff3555bffe66
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7353f3ab4513d8331b1d38cb01ad16c7d3cde165
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="event-handlers-overview-windows-forms"></a><span data-ttu-id="c8a59-102">Olay İşleyicilerine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="c8a59-102">Event Handlers Overview (Windows Forms)</span></span>
<span data-ttu-id="c8a59-103">Olay işleyicisi olaya bağlı bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="c8a59-103">An event handler is a method that is bound to an event.</span></span> <span data-ttu-id="c8a59-104">Olay işleyicisi içindeki kod olay oluşturulduğunda yürütülür.</span><span class="sxs-lookup"><span data-stu-id="c8a59-104">When the event is raised, the code within the event handler is executed.</span></span> <span data-ttu-id="c8a59-105">Her olay işleyicisi olayını düzgün bir şekilde işlemek izin veren iki parametre sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8a59-105">Each event handler provides two parameters that allow you to handle the event properly.</span></span> <span data-ttu-id="c8a59-106">Aşağıdaki örnekte bir olay işleyicisi için bir <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Click> olay.</span><span class="sxs-lookup"><span data-stu-id="c8a59-106">The following example shows an event handler for a <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event.</span></span>  
  
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
  
 <span data-ttu-id="c8a59-107">İlk parametre`sender`, olayı nesnesine başvuru sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8a59-107">The first parameter,`sender`, provides a reference to the object that raised the event.</span></span> <span data-ttu-id="c8a59-108">İkinci parametre `e`, yukarıdaki örnekte, bir nesne belirli o anda işlenen olayı geçirir.</span><span class="sxs-lookup"><span data-stu-id="c8a59-108">The second parameter, `e`, in the example above, passes an object specific to the event that is being handled.</span></span> <span data-ttu-id="c8a59-109">Nesnenin özelliklerini (ve bazı durumlarda, yöntemlerinden) başvurarak fare olayları ya da sürükle ve bırak olayları aktarılan veri için fareyi konumu gibi bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8a59-109">By referencing the object's properties (and, sometimes, its methods), you can obtain information such as the location of the mouse for mouse events or data being transferred in drag-and-drop events.</span></span>  
  
 <span data-ttu-id="c8a59-110">Genellikle her olay ikinci parametre için farklı olay nesne türüne sahip bir olay işleyicisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c8a59-110">Typically each event produces an event handler with a different event-object type for the second parameter.</span></span> <span data-ttu-id="c8a59-111">İçin olanlar gibi bazı olay işleyicileri <xref:System.Windows.Forms.Control.MouseDown> ve <xref:System.Windows.Forms.Control.MouseUp> olayları, kendi ikinci parametre için aynı nesne türü vardır.</span><span class="sxs-lookup"><span data-stu-id="c8a59-111">Some event handlers, such as those for the <xref:System.Windows.Forms.Control.MouseDown> and <xref:System.Windows.Forms.Control.MouseUp> events, have the same object type for their second parameter.</span></span> <span data-ttu-id="c8a59-112">Bu olaylar türleri için her iki olayları işlemek için aynı olay işleyicisi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8a59-112">For these types of events, you can use the same event handler to handle both events.</span></span>  
  
 <span data-ttu-id="c8a59-113">Aynı olay işleyicisi, farklı denetimleri için aynı olayını işlemek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8a59-113">You can also use the same event handler to handle the same event for different controls.</span></span> <span data-ttu-id="c8a59-114">Örneğin, bir grup varsa <xref:System.Windows.Forms.RadioButton> formdaki denetimler, bir tek olay işleyicisi oluşturabilir <xref:System.Windows.Forms.Control.Click> olay ve her bir denetimin <xref:System.Windows.Forms.Control.Click> olay tek olay işleyicisine bağımlı.</span><span class="sxs-lookup"><span data-stu-id="c8a59-114">For example, if you have a group of <xref:System.Windows.Forms.RadioButton> controls on a form, you could create a single event handler for the <xref:System.Windows.Forms.Control.Click> event and have each control's <xref:System.Windows.Forms.Control.Click> event bound to the single event handler.</span></span> <span data-ttu-id="c8a59-115">Daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms'ta tek olay işleyicisine birden çok olay bağlanmak](../../../docs/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="c8a59-115">For more information, see [How to: Connect Multiple Events to a Single Event Handler in Windows Forms](../../../docs/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8a59-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c8a59-116">See Also</span></span>  
 [<span data-ttu-id="c8a59-117">Windows Forms'ta olay işleyicileri oluşturma</span><span class="sxs-lookup"><span data-stu-id="c8a59-117">Creating Event Handlers in Windows Forms</span></span>](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [<span data-ttu-id="c8a59-118">Olaylara genel bakış</span><span class="sxs-lookup"><span data-stu-id="c8a59-118">Events Overview</span></span>](../../../docs/framework/winforms/events-overview-windows-forms.md)
