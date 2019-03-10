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
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705388"
---
# <a name="defining-an-event-in-windows-forms-controls"></a>Windows Forms Denetimlerinde Olay Tanımlama
Özel olaylar tanımlama hakkında daha fazla ayrıntı için bkz [olayları](../../../standard/events/index.md). İlişkili tüm veriler yok. bir olay tanımlarsanız, temel tür, olay verileri için kullanın. <xref:System.EventArgs>ve <xref:System.EventHandler> olay temsilci olarak. Yapmak için kalan tek şey bir olay üyesi ve korumalı tanımlamak için `On` *EventName* olayını yöntemi.  
  
 Aşağıdaki kod parçası gösterir nasıl `FlashTrackBar` özel denetim tanımlayan özel bir olay `ValueChanged`. İçin tam kod için `FlashTrackBar` örnek için bkz: [nasıl yapılır: İlerleme durumunu gösteren Windows Forms denetimi oluşturma](how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms Denetimlerindeki Olaylar](events-in-windows-forms-controls.md)
- [Olaylar](../../../standard/events/index.md)
