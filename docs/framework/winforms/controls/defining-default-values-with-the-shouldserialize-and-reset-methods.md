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
ms.openlocfilehash: f1f5a668c5d4f52ef7dd9f60a31c04f2173165f6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59090621"
---
# <a name="defining-default-values-with-the-shouldserialize-and-reset-methods"></a>ShouldSerialize ile Varsayılan Değerleri Tanımlama ve Yöntemleri Sıfırlama
`ShouldSerialize` ve `Reset` özelliği yoksa, bir özelliği için sağlayabilirsiniz isteğe bağlı yöntemlerdir bir basit varsayılan değere sahip. Özelliği bir basit varsayılan değere sahipse, uygulamalıdır <xref:System.ComponentModel.DefaultValueAttribute> ve bunun yerine varsayılan değer özniteliği sınıf oluşturucusuna sağlayın. Bu mekanizmaların birini Tasarımcısı'nda aşağıdaki özellikleri sağlar:  
  
-   Varsayılan değerini değiştirdiyseniz özellik tarayıcısında visual belirtme özelliği sağlar.  
  
-   Kullanıcı özelliği sağ tıklatın ve seçin **sıfırlama** özelliği varsayılan değerine geri yüklemek için.  
  
-   Tasarımcı daha verimli kod oluşturur.  
  
    > [!NOTE]
    >  Ya da uygulama <xref:System.ComponentModel.DefaultValueAttribute> veya sağlayan `Reset` *PropertyName* ve `ShouldSerialize` *PropertyName* yöntemleri. Her ikisini birden kullanmayın.  
  
 `Reset` *PropertyName* yöntemini aşağıdaki kod parçasını gösterildiği gibi bu bir özelliği varsayılan değerine ayarlar.  
  
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
>  Bir özellik yoksa bir `Reset` yöntemi ile işaretlenmemiş bir <xref:System.ComponentModel.DefaultValueAttribute>ve bildiriminden, sağlanan varsayılan değeri yok `Reset` kısayol menüsünde, bu özelliği devre dışı seçeneği **özellikleri** Windows Form Tasarımcısı'nda Visual Studio penceresi.  
  
 Visual Studio gibi tasarımcıları `ShouldSerialize` *PropertyName* yöntemi bir özelliği varsayılan değerine değişip değişmediğini denetleyin ve kod yazma form eksikse bir özelliği değiştirildiğinde, bu nedenle daha verimli kod için izin verme oluşturma. Örneğin:  
  
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
  
 Bu durumda, hatta özel bir değişken değeri tarafından erişildiğinde `MyFont` özelliği `null`, özellik tarayıcısı aşağıdaki dotnetclıtools'u görüntülemiyor `null`; bunun yerine, görüntülediği <xref:System.Windows.Forms.Control.Font%2A> değilse üst öğesinin özellik `null`, Varsayılan <xref:System.Windows.Forms.Control.Font%2A> tanımlanan değer <xref:System.Windows.Forms.Control>. Bu nedenle için varsayılan değer `MyFont` yalnızca ayarlanamaz ve <xref:System.ComponentModel.DefaultValueAttribute> bu özelliğe uygulanamaz. Bunun yerine, `ShouldSerialize` ve `Reset` yöntemleri için uygulanmalı `MyFont` özelliği.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms Denetimlerindeki Özellikler](properties-in-windows-forms-controls.md)
- [Özellik Tanımlama](defining-a-property-in-windows-forms-controls.md)
- [Özellik Değişti Olayları](property-changed-events.md)
