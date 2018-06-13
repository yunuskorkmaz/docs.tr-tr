---
title: Windows Forms Denetimlerinde Olay Tanımlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- events [Windows Forms], defining within Windows Forms custom controls
- custom controls [Windows Forms], events using code
ms.assetid: d89f1096-8061-42e2-a855-a1f053f1940a
ms.openlocfilehash: 552f2b8441ae5323f55f236fabb9f50f8f8b5ab0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524039"
---
# <a name="defining-an-event-in-windows-forms-controls"></a><span data-ttu-id="0b058-102">Windows Forms Denetimlerinde Olay Tanımlama</span><span class="sxs-lookup"><span data-stu-id="0b058-102">Defining an Event in Windows Forms Controls</span></span>
<span data-ttu-id="0b058-103">Özel olaylar tanımlama hakkında daha fazla bilgi için bkz [olayları](../../../../docs/standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="0b058-103">For details about defining custom events, see [Events](../../../../docs/standard/events/index.md).</span></span> <span data-ttu-id="0b058-104">Tüm ilişkili veriler sahip olmayan bir olay tanımlarsanız, olay verileri için temel türü kullanın <xref:System.EventArgs>ve <xref:System.EventHandler> olay temsilci olarak.</span><span class="sxs-lookup"><span data-stu-id="0b058-104">If you define an event that does not have any associated data, use the base type for event data, <xref:System.EventArgs>, and use <xref:System.EventHandler> as the event delegate.</span></span> <span data-ttu-id="0b058-105">Yapmak için kalan tek şey bir olay üye ve korumalı bir tanımlamak için `On` *EventName* olayını yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0b058-105">All that remains to do is to define an event member and a protected `On`*EventName* method that raises the event.</span></span>  
  
 <span data-ttu-id="0b058-106">Aşağıdaki kodda gösterildiği parçalara nasıl `FlashTrackBar` özel denetim tanımlayan özel bir olay `ValueChanged`.</span><span class="sxs-lookup"><span data-stu-id="0b058-106">The following code fragment shows how the `FlashTrackBar` custom control defines a custom event, `ValueChanged`.</span></span> <span data-ttu-id="0b058-107">İçin tam kodu `FlashTrackBar` örnek için bkz: [nasıl yapılır: Windows Forms denetimi olduğunu gösteren ilerlemesi oluşturma](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).</span><span class="sxs-lookup"><span data-stu-id="0b058-107">For the complete code for the `FlashTrackBar` sample, see the [How to: Create a Windows Forms Control That Shows Progress](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
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
   protected virtual void OnValueChanged(EventArgs e) {  
      if (ValueChanged != null) {  
         ValueChanged(this, e);  
      }  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="0b058-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0b058-108">See Also</span></span>  
 [<span data-ttu-id="0b058-109">Windows Forms Denetimlerindeki Olaylar</span><span class="sxs-lookup"><span data-stu-id="0b058-109">Events in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)  
 [<span data-ttu-id="0b058-110">Olaylar</span><span class="sxs-lookup"><span data-stu-id="0b058-110">Events</span></span>](../../../../docs/standard/events/index.md)  
 [<span data-ttu-id="0b058-111">Olaylar</span><span class="sxs-lookup"><span data-stu-id="0b058-111">Events</span></span>](../../../../docs/standard/events/index.md)
