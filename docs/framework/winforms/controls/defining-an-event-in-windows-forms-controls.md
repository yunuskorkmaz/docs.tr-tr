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
ms.openlocfilehash: 4235c8b3c513509023388112071e78cfd079ec6f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972347"
---
# <a name="defining-an-event-in-windows-forms-controls"></a><span data-ttu-id="0ee91-102">Windows Forms Denetimlerinde Olay Tanımlama</span><span class="sxs-lookup"><span data-stu-id="0ee91-102">Defining an Event in Windows Forms Controls</span></span>
<span data-ttu-id="0ee91-103">Özel olaylar tanımlama hakkında daha fazla ayrıntı için bkz [olayları](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="0ee91-103">For details about defining custom events, see [Events](../../../standard/events/index.md).</span></span> <span data-ttu-id="0ee91-104">İlişkili tüm veriler yok. bir olay tanımlarsanız, temel tür, olay verileri için kullanın. <xref:System.EventArgs>ve <xref:System.EventHandler> olay temsilci olarak.</span><span class="sxs-lookup"><span data-stu-id="0ee91-104">If you define an event that does not have any associated data, use the base type for event data, <xref:System.EventArgs>, and use <xref:System.EventHandler> as the event delegate.</span></span> <span data-ttu-id="0ee91-105">Yapmak için kalan tek şey bir olay üyesi ve korumalı tanımlamak için `On` *EventName* olayını yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0ee91-105">All that remains to do is to define an event member and a protected `On`*EventName* method that raises the event.</span></span>  
  
 <span data-ttu-id="0ee91-106">Aşağıdaki kod parçası gösterir nasıl `FlashTrackBar` özel denetim tanımlayan özel bir olay `ValueChanged`.</span><span class="sxs-lookup"><span data-stu-id="0ee91-106">The following code fragment shows how the `FlashTrackBar` custom control defines a custom event, `ValueChanged`.</span></span> <span data-ttu-id="0ee91-107">İçin tam kod için `FlashTrackBar` örnek için bkz: [nasıl yapılır: İlerleme durumunu gösteren Windows Forms denetimi oluşturma](how-to-create-a-windows-forms-control-that-shows-progress.md).</span><span class="sxs-lookup"><span data-stu-id="0ee91-107">For the complete code for the `FlashTrackBar` sample, see the [How to: Create a Windows Forms Control That Shows Progress](how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0ee91-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ee91-108">See also</span></span>

- [<span data-ttu-id="0ee91-109">Windows Forms Denetimlerindeki Olaylar</span><span class="sxs-lookup"><span data-stu-id="0ee91-109">Events in Windows Forms Controls</span></span>](events-in-windows-forms-controls.md)
- [<span data-ttu-id="0ee91-110">Olaylar</span><span class="sxs-lookup"><span data-stu-id="0ee91-110">Events</span></span>](../../../standard/events/index.md)
