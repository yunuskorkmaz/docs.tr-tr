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
ms.openlocfilehash: e3c48aec830cdc3ccceb8683f93e3a99ee6364e2
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506189"
---
# <a name="overriding-the-onpaint-method"></a>OnPaint Yöntemini Geçersiz Kılma
.NET Framework içinde tanımlanmış herhangi bir olayı geçersiz kılmak için temel adımlar aynıdır ve aşağıda özetlenmiştir.  
  
#### <a name="to-override-an-inherited-event"></a>Devralınan bir olayı geçersiz kılmak için  
  
1. Geçersiz kılma korumalı `On` *EventName* yöntemi.  
  
2. Çağrı `On` *EventName* yöntemi geçersiz kılınan taban sınıfından `On` *EventName* yöntemi, temsilcileri kayıtlı için olay alırsınız.  
  
 <xref:System.Windows.Forms.Control.Paint> Olay her Windows Forms denetimi geçersiz kılmanız gerekir çünkü burada ayrıntılı olarak ele <xref:System.Windows.Forms.Control.Paint> devraldığı olay <xref:System.Windows.Forms.Control>. Temel <xref:System.Windows.Forms.Control> sınıfı türetilmiş bir denetimi nasıl çizilmesi gerektiğinde bilmeyen ve bir boyama mantığında sağlamaz <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi. <xref:System.Windows.Forms.Control.OnPaint%2A> Yöntemi <xref:System.Windows.Forms.Control> yalnızca gönderir <xref:System.Windows.Forms.Control.Paint> kayıtlı olay alıcıları için olay.  
  
 Örnekte aracılığıyla yaradıysa [nasıl yapılır: Basit bir Windows Forms denetimi geliştirme](how-to-develop-a-simple-windows-forms-control.md), geçersiz kılma örneği gördünüz <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi. Aşağıdaki kod parçası bu örnekten alınır.  
  
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
  
 <xref:System.Windows.Forms.PaintEventArgs> Sınıfı içeren verileri <xref:System.Windows.Forms.Control.Paint> olay. Aşağıdaki kodda gösterildiği gibi iki özelliğe sahiptir.  
  
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
  
 <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> boyanacak, dikdörtgen ve <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> özelliği başvurduğu bir <xref:System.Drawing.Graphics> nesne. Sınıflarda <xref:System.Drawing?displayProperty=nameWithType> ad alanı yönetilen GDI +'da, yeni bir Windows grafik kitaplığı işlevlerini erişimi sağlayan sınıflar. <xref:System.Drawing.Graphics> Nesne noktaları, dizeler, çizgiler, yaylar, üç nokta ve birçok diğer şekiller çizmek için yöntemleri vardır.  
  
 Bir denetim çağırır, <xref:System.Windows.Forms.Control.OnPaint%2A> görsel görünümünü değiştirmek gerektiğinde yöntemi. Bu yöntem sırayla başlatır <xref:System.Windows.Forms.Control.Paint> olay.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olaylar](../../../standard/events/index.md)
- [Windows Forms Denetimini İşleme](rendering-a-windows-forms-control.md)
- [Olay Tanımlama](defining-an-event-in-windows-forms-controls.md)
