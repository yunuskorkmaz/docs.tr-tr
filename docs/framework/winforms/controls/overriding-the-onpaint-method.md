---
title: OnPaint Yöntemini Geçersiz Kılma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Paint event [Windows Forms], handling in Windows Forms custom control
- OnPaint method [Windows Forms], overriding in Windows Forms custom controls
ms.assetid: e9ca2723-0107-4540-bb21-4f5ffb4a9906
ms.openlocfilehash: 863726a6264f01de9f00296b4a64b9fd1bb96765
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182044"
---
# <a name="overriding-the-onpaint-method"></a>OnPaint Yöntemini Geçersiz Kılma
.NET Framework'de tanımlanan herhangi bir olayı geçersiz kılmak için temel adımlar aynıdır ve aşağıdaki listede özetlenmiştir.  
  
#### <a name="to-override-an-inherited-event"></a>Devralınan bir olayı geçersiz kılmak için  
  
1. Korumalı `On` *EventName* yöntemini geçersiz kılın.  
  
2. Kayıtlı temsilcilerin olayı alması için taban sınıfın `On` *EventName* yöntemini geçersiz kılın *EventName* yönteminden arayın. `On`  
  
 Her <xref:System.Windows.Forms.Control.Paint> Windows Forms denetimi devraldığı <xref:System.Windows.Forms.Control.Paint> olayı geçersiz kılmak zorundadır, çünkü olay <xref:System.Windows.Forms.Control>burada ayrıntılı olarak tartışılır. Taban <xref:System.Windows.Forms.Control> sınıf, türemiş denetimin nasıl çizilmesi gerektiğini bilmez ve <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemde herhangi bir boyama mantığı sağlamaz. <xref:System.Windows.Forms.Control> Yöntem, <xref:System.Windows.Forms.Control.OnPaint%2A> <xref:System.Windows.Forms.Control.Paint> olayı kayıtlı olay alıcılarına gönderir.  
  
 Örnek üzerinde [çalıştıysanız Nasıl Yapılır: Basit Bir Windows Formlar Denetimi](how-to-develop-a-simple-windows-forms-control.md)Geliştirin, <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemin geçersiz kılınması için bir örnek gördünüz. Aşağıdaki kod parçası bu örnekten alınır.  
  
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
public class FirstControl : Control {  
   public FirstControl() {}  
   protected override void OnPaint(PaintEventArgs e) {  
      // Call the OnPaint method of the base class.  
      base.OnPaint(e);  
      // Call methods of the System.Drawing.Graphics object.  
      e.Graphics.DrawString(Text, Font, new SolidBrush(ForeColor), ClientRectangle);  
   }
}
```  
  
 Sınıf <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Windows.Forms.Control.Paint> olay için veri içerir. Aşağıdaki kodda gösterildiği gibi iki özelliği vardır.  
  
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
  
 <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>boyanacak dikdörtgendir ve <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> özellik bir <xref:System.Drawing.Graphics> nesneye başvurur. <xref:System.Drawing?displayProperty=nameWithType> Ad alanındaki sınıflar, yeni Windows grafik kitaplığı olan GDI+'nın işlevselliğine erişim sağlayan yönetilen sınıflardır. Nesnenin <xref:System.Drawing.Graphics> noktaları, dizeleri, çizgileri, yayları, elipsleri ve diğer birçok şekli çizme yöntemleri vardır.  
  
 Denetim, görsel <xref:System.Windows.Forms.Control.OnPaint%2A> ekranını değiştirmesi gerektiğinde yöntemini çağırır. Bu yöntem sırayla <xref:System.Windows.Forms.Control.Paint> olayı yükseltir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olaylar](../../../standard/events/index.md)
- [Windows Forms Denetimini İşleme](rendering-a-windows-forms-control.md)
- [Olay Tanımlama](defining-an-event-in-windows-forms-controls.md)
