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
ms.openlocfilehash: 60ae01ca63f895bfb1c7aabbe3337596cd13933d
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45743277"
---
# <a name="defining-an-event-in-windows-forms-controls"></a><span data-ttu-id="95a7f-102">Windows Forms Denetimlerinde Olay Tanımlama</span><span class="sxs-lookup"><span data-stu-id="95a7f-102">Defining an Event in Windows Forms Controls</span></span>
<span data-ttu-id="95a7f-103">Özel olaylar tanımlama hakkında daha fazla ayrıntı için bkz [olayları](../../../../docs/standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="95a7f-103">For details about defining custom events, see [Events](../../../../docs/standard/events/index.md).</span></span> <span data-ttu-id="95a7f-104">İlişkili tüm veriler yok. bir olay tanımlarsanız, temel tür, olay verileri için kullanın. <xref:System.EventArgs>ve <xref:System.EventHandler> olay temsilci olarak.</span><span class="sxs-lookup"><span data-stu-id="95a7f-104">If you define an event that does not have any associated data, use the base type for event data, <xref:System.EventArgs>, and use <xref:System.EventHandler> as the event delegate.</span></span> <span data-ttu-id="95a7f-105">Yapmak için kalan tek şey bir olay üyesi ve korumalı tanımlamak için `On` *EventName* olayını yöntemi.</span><span class="sxs-lookup"><span data-stu-id="95a7f-105">All that remains to do is to define an event member and a protected `On`*EventName* method that raises the event.</span></span>  
  
 <span data-ttu-id="95a7f-106">Aşağıdaki kod parçası gösterir nasıl `FlashTrackBar` özel denetim tanımlayan özel bir olay `ValueChanged`.</span><span class="sxs-lookup"><span data-stu-id="95a7f-106">The following code fragment shows how the `FlashTrackBar` custom control defines a custom event, `ValueChanged`.</span></span> <span data-ttu-id="95a7f-107">İçin tam kod için `FlashTrackBar` örnek için bkz: [nasıl yapılır: bir Windows Forms denetimi olduğunu gösteren oluşturma ilerleme durumu](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).</span><span class="sxs-lookup"><span data-stu-id="95a7f-107">For the complete code for the `FlashTrackBar` sample, see the [How to: Create a Windows Forms Control That Shows Progress](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="95a7f-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95a7f-108">See also</span></span>

- [<span data-ttu-id="95a7f-109">Windows Forms Denetimlerindeki Olaylar</span><span class="sxs-lookup"><span data-stu-id="95a7f-109">Events in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)
- [<span data-ttu-id="95a7f-110">Olaylar</span><span class="sxs-lookup"><span data-stu-id="95a7f-110">Events</span></span>](../../../../docs/standard/events/index.md)
