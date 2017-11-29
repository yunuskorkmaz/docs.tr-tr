---
title: "OnPaint Yöntemini Geçersiz Kılma"
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
- Paint event [Windows Forms], handling in Windows Forms custom control
- OnPaint method [Windows Forms], overriding in Windows Forms custom controls
ms.assetid: e9ca2723-0107-4540-bb21-4f5ffb4a9906
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 41205f7f0ec21e27b97d0b12415fca89ae526552
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="overriding-the-onpaint-method"></a>OnPaint Yöntemini Geçersiz Kılma
Tanımlanan herhangi bir olay geçersiz kılma için temel adımlar [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aynıdır ve aşağıdaki listede özetlenmiştir.  
  
#### <a name="to-override-an-inherited-event"></a>Devralınan bir olay geçersiz kılmak için  
  
1.  Korumalı geçersiz kılma `On` *EventName* yöntemi.  
  
2.  Çağrı `On` *EventName* geçersiz kılınan temel sınıfından yöntemi `On` *EventName* yöntemi, temsilcileri kayıtlı şekilde alma olayı.  
  
 <xref:System.Windows.Forms.Control.Paint> Olay her Windows Forms denetimi geçersiz kılmanız gerekir çünkü aşağıda ayrıntılı olarak ele alınmıştır <xref:System.Windows.Forms.Control.Paint> öğesinden devralınan olay <xref:System.Windows.Forms.Control>. Temel <xref:System.Windows.Forms.Control> sınıf türetilmiş bir denetim nasıl çizilmesi gerektiğinde bilmez ve herhangi bir boyama mantık sağlamaz <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi. <xref:System.Windows.Forms.Control.OnPaint%2A> Yöntemi <xref:System.Windows.Forms.Control> yalnızca gönderir <xref:System.Windows.Forms.Control.Paint> kayıtlı olay alıcıları olay.  
  
 Örnek aracılığıyla çalışılan varsa [nasıl yapılır: basit bir Windows Forms denetimi geliştirme](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md), geçersiz kılma örneği gördünüz <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi. Aşağıdaki kod parçası, bu örnekten alınır.  
  
```vb  
Public Class FirstControl  
   Inherits Control  
  
   Public Sub New()  
   End Sub  
  
   Protected Overrides Sub OnPaint(e As PaintEventArgs)  
      ' Call the OnPaint method of the base class.  
      MyBase.OnPaint(e)  
      ' Call methods of the System.Drawing.Graphics object.  
      e.Graphics.DrawString(Text, Font, New SolidBrush(ForeColor), RectangleF.op_Implicit(ClientRectangle))  
   End Sub  
End Class   
```  
  
```csharp  
public class FirstControl : Control{  
   public FirstControl() {}  
   protected override void OnPaint(PaintEventArgs e) {  
      // Call the OnPaint method of the base class.  
      base.OnPaint(e);  
      // Call methods of the System.Drawing.Graphics object.  
      e.Graphics.DrawString(Text, Font, new SolidBrush(ForeColor), ClientRectangle);  
   }   
}   
```  
  
 <xref:System.Windows.Forms.PaintEventArgs> Sınıfı için verileri içeren <xref:System.Windows.Forms.Control.Paint> olay. Aşağıdaki kodda gösterildiği gibi iki özellik içeriyor.  
  
```vb  
Public Class PaintEventArgs  
   Inherits EventArgs  
   ...  
   Public ReadOnly Property ClipRectangle() As System.Drawing.Rectangle  
      ...  
   End Property  
  
   Public ReadOnly Property Graphics() As System.Drawing.Graphics  
      ...  
   End Property   
   ...  
End Class  
```  
  
```csharp  
public class PaintEventArgs : EventArgs {  
...  
    public System.Drawing.Rectangle ClipRectangle {}  
    public System.Drawing.Graphics Graphics {}  
...  
}  
```  
  
 <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>tanımlanabilir için dikdörtgen ve <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> özelliği başvurduğu bir <xref:System.Drawing.Graphics> nesnesi. Sınıflarda <xref:System.Drawing?displayProperty=nameWithType> ad alanı yönetilen işlevselliğini erişebilmesi sınıflar [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], yeni Windows grafik kitaplığı. <xref:System.Drawing.Graphics> Nesnenin noktaları, dizeleri, çizgi, yaylar, üç nokta ve diğer birçok şekiller çizmek için yöntemleri vardır.  
  
 Bir denetim çağırır kendi <xref:System.Windows.Forms.Control.OnPaint%2A> görsel görünümünü değiştirmeye ihtiyaç duyduğunda yöntemi. Bu yöntem sırayla başlatır <xref:System.Windows.Forms.Control.Paint> olay.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Olayları](../../../../docs/standard/events/index.md)  
 [Windows Forms denetimi oluşturma](../../../../docs/framework/winforms/controls/rendering-a-windows-forms-control.md)  
 [Olay tanımlama](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)
