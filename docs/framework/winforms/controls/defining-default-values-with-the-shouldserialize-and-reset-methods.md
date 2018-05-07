---
title: ShouldSerialize ile Varsayılan Değerleri Tanımlama ve Yöntemleri Sıfırlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property methods
- ShouldPersist method
ms.assetid: 7b6c5e00-3771-46b4-9142-5a80d5864a5e
ms.openlocfilehash: 8d7645e8de5edee711c30bbe7edde8ba7b5b1dab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="defining-default-values-with-the-shouldserialize-and-reset-methods"></a>ShouldSerialize ile Varsayılan Değerleri Tanımlama ve Yöntemleri Sıfırlama
`ShouldSerialize` ve `Reset` özelliği yoksa, bir özellik için sağladığınız isteğe bağlı yöntemlerdir bir basit varsayılan değere sahip. Basit varsayılan bir değer özelliğine sahipse uygulamalıdır <xref:System.ComponentModel.DefaultValueAttribute> ve bunun yerine öznitelik sınıfı Oluşturucu için varsayılan değer sağlayın. Bu mekanizmaların birini Tasarımcısı'nda aşağıdaki özellikleri sağlar:  
  
-   Varsayılan değerden değiştirilirse özelliği özellik tarayıcısında görsel bir gösterge sağlar.  
  
-   Kullanıcı özelliği sağ tıklatın ve seçin **sıfırlama** özelliğin varsayılan değeri geri yüklemek için.  
  
-   Tasarımcı daha verimli kod oluşturur.  
  
    > [!NOTE]
    >  Ya da geçerli <xref:System.ComponentModel.DefaultValueAttribute> veya sağlayın `Reset` *PropertyName* ve `ShouldSerialize` *PropertyName* yöntemleri. Her ikisini birden kullanmayın.  
  
 `Reset` *PropertyName* yöntemini aşağıdaki kod parçasında gösterildiği gibi bu özellik varsayılan değerine ayarlar.  
  
```vb  
Public Sub ResetMyFont()  
   MyFont = Nothing  
End Sub  
```  
  
```csharp  
public void ResetMyFont() {  
   MyFont = null;  
}  
```  
  
> [!NOTE]
>  Bir özellik yoksa bir `Reset` yöntemi ile işaretlenmemiş bir <xref:System.ComponentModel.DefaultValueAttribute>ve kendi bildiriminde sağlanan varsayılan değeri yok `Reset` bu özellik kısayol menüsünü devre dışı seçeneğini **özellikleri** Visual Studio'da Windows Forms Tasarımcısı penceresinin.  
  
 Visual Studio gibi tasarımcıları `ShouldSerialize` *PropertyName* yöntemi bir özelliğin varsayılan değerinden değişip değişmediğini denetleyin ve kod yazma form eksikse bir özelliği değiştirildiğinde, böylece daha verimli kodunu sağlar oluşturma. Örneğin:  
  
```vb  
'Returns true if the font has changed; otherwise, returns false.  
' The designer writes code to the form only if true is returned.  
Public Function ShouldSerializeMyFont() As Boolean  
   Return Not (thefont Is Nothing)  
End Function  
```  
  
```csharp  
// Returns true if the font has changed; otherwise, returns false.  
// The designer writes code to the form only if true is returned.  
public bool ShouldSerializeMyFont() {  
   return thefont != null;  
}  
```  
  
 Tam kod örnek aşağıda verilmiştir.  
  
```vb  
Option Explicit  
Option Strict  
  
Imports System  
Imports System.Windows.Forms  
Imports System.Drawing  
  
Public Class MyControl  
   Inherits Control  
  
   ' Declare an instance of the Font class  
   ' and set its default value to Nothing.  
   Private thefont As Font = Nothing  
  
   ' The MyFont property.   
   Public Property MyFont() As Font  
      ' Note that the Font property never  
      ' returns null.  
      Get  
         If Not (thefont Is Nothing) Then  
            Return thefont  
         End If  
         If Not (Parent Is Nothing) Then  
            Return Parent.Font  
         End If  
         Return Control.DefaultFont  
      End Get  
      Set  
         thefont = value  
      End Set  
   End Property  
  
   Public Function ShouldSerializeMyFont() As Boolean  
      Return Not (thefont Is Nothing)  
   End Function  
  
   Public Sub ResetMyFont()  
      MyFont = Nothing  
   End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Windows.Forms;  
using System.Drawing;  
  
public class MyControl : Control {  
   // Declare an instance of the Font class  
   // and set its default value to null.  
   private Font thefont = null;  
  
   // The MyFont property.      
   public Font MyFont {  
      // Note that the MyFont property never  
      // returns null.  
      get {  
         if (thefont != null) return thefont;  
         if (Parent != null) return Parent.Font;  
         return Control.DefaultFont;  
      }  
      set {  
         thefont = value;  
      }  
   }  
  
   public bool ShouldSerializeMyFont() {  
      return thefont != null;  
   }  
  
   public void ResetMyFont() {  
      MyFont = null;  
   }  
}  
```  
  
 Bu durumda, hatta özel değişkeninin değeri tarafından erişildiğinde `MyFont` özelliği `null`, özellik tarayıcısı görüntülenmez `null`; bunun yerine, gösterir <xref:System.Windows.Forms.Control.Font%2A> özellik değilse üst `null`, veya varsayılan <xref:System.Windows.Forms.Control.Font%2A> tanımlanan değer <xref:System.Windows.Forms.Control>. Bu nedenle için varsayılan değer `MyFont` yalnızca ayarlanamaz ve bir <xref:System.ComponentModel.DefaultValueAttribute> bu özelliğe uygulanamaz. Bunun yerine, `ShouldSerialize` ve `Reset` yöntem uygulanmadı, için `MyFont` özelliği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms Denetimlerindeki Özellikler](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [Özellik Tanımlama](../../../../docs/framework/winforms/controls/defining-a-property-in-windows-forms-controls.md)  
 [Özellik Değişti Olayları](../../../../docs/framework/winforms/controls/property-changed-events.md)
