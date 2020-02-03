---
title: Denetimlerde bir olay tanımlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- events [Windows Forms], defining within Windows Forms custom controls
- custom controls [Windows Forms], events using code
ms.assetid: d89f1096-8061-42e2-a855-a1f053f1940a
ms.openlocfilehash: d45c369e1fc82ee009a85b5b35fe6aa754873436
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746082"
---
# <a name="defining-an-event-in-windows-forms-controls"></a><span data-ttu-id="84ae7-102">Windows Forms Denetimlerinde Olay Tanımlama</span><span class="sxs-lookup"><span data-stu-id="84ae7-102">Defining an Event in Windows Forms Controls</span></span>
<span data-ttu-id="84ae7-103">Özel olayları tanımlama hakkında daha fazla bilgi için bkz. [Olaylar](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="84ae7-103">For details about defining custom events, see [Events](../../../standard/events/index.md).</span></span> <span data-ttu-id="84ae7-104">İlişkili verileri olmayan bir olay tanımlarsanız, olay verileri için temel türü kullanın, <xref:System.EventArgs>ve olay temsilcisi olarak <xref:System.EventHandler> kullanın.</span><span class="sxs-lookup"><span data-stu-id="84ae7-104">If you define an event that does not have any associated data, use the base type for event data, <xref:System.EventArgs>, and use <xref:System.EventHandler> as the event delegate.</span></span> <span data-ttu-id="84ae7-105">Her şey, olayı oluşturan bir olay üyesini ve korunan `On`*EventName* metodunu tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="84ae7-105">All that remains to do is to define an event member and a protected `On`*EventName* method that raises the event.</span></span>  
  
 <span data-ttu-id="84ae7-106">Aşağıdaki kod parçası, `FlashTrackBar` özel denetiminin özel bir olayı `ValueChanged`nasıl tanımladığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="84ae7-106">The following code fragment shows how the `FlashTrackBar` custom control defines a custom event, `ValueChanged`.</span></span> <span data-ttu-id="84ae7-107">`FlashTrackBar` örneği için tüm kod için bkz. [nasıl yapılır: bir Windows Forms denetimi oluşturma Ilerlemeyi gösterir](how-to-create-a-windows-forms-control-that-shows-progress.md).</span><span class="sxs-lookup"><span data-stu-id="84ae7-107">For the complete code for the `FlashTrackBar` sample, see the [How to: Create a Windows Forms Control That Shows Progress](how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
```vb  
Option Explicit  
Option Strict  
  
Imports System  
Imports System.Windows.Forms  
Imports System.Drawing  
  
Public Class FlashTrackBar  
   Inherits Control  
  
   ' The event does not have any data, so EventHandler is adequate   
   ' as the event delegate.          
   ' Define the event member using the event keyword.  
   ' In this case, for efficiency, the event is defined   
   ' using the event property construct.  
   Public Event ValueChanged As EventHandler  
   ' The protected method that raises the ValueChanged   
   ' event when the value has actually   
   ' changed. Derived controls can override this method.    
   Protected Overridable Sub OnValueChanged(e As EventArgs)  
      RaiseEvent ValueChanged(Me, e)  
   End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Windows.Forms;  
using System.Drawing;  
  
public class FlashTrackBar : Control {  
   // The event does not have any data, so EventHandler is adequate   
   // as the event delegate.  
   private EventHandler onValueChanged;  
   // Define the event member using the event keyword.  
   // In this case, for efficiency, the event is defined   
   // using the event property construct.  
   public event EventHandler ValueChanged {  
            add {  
                onValueChanged += value;  
            }  
            remove {  
                onValueChanged -= value;  
            }  
        }  
   // The protected method that raises the ValueChanged  
   // event when the value has actually   
   // changed. Derived controls can override this method.    
   protected virtual void OnValueChanged(EventArgs e) 
   {  
       ValueChanged?.Invoke(this, e);  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="84ae7-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84ae7-108">See also</span></span>

- [<span data-ttu-id="84ae7-109">Windows Forms Denetimlerindeki Olaylar</span><span class="sxs-lookup"><span data-stu-id="84ae7-109">Events in Windows Forms Controls</span></span>](events-in-windows-forms-controls.md)
- [<span data-ttu-id="84ae7-110">Olaylar</span><span class="sxs-lookup"><span data-stu-id="84ae7-110">Events</span></span>](../../../standard/events/index.md)
