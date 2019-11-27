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
ms.openlocfilehash: 11181bacdb919693ffc82c48c061357463a6343b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336757"
---
# <a name="defining-default-values-with-the-shouldserialize-and-reset-methods"></a>ShouldSerialize ile Varsayılan Değerleri Tanımlama ve Yöntemleri Sıfırlama
`ShouldSerialize` ve `Reset`, özelliğin basit bir varsayılan değeri yoksa bir özellik için sağlayabilmeniz için isteğe bağlı yöntemlerdir. Özelliğin basit bir varsayılan değeri varsa, <xref:System.ComponentModel.DefaultValueAttribute> uygulamanız ve bunun yerine öznitelik sınıfı oluşturucusuna varsayılan değeri sağlamanız gerekir. Bu mekanizmalardan herhangi biri, tasarımcıda aşağıdaki özellikleri sunar:

- Özelliği, varsayılan değerinden değiştirildiyse özellik tarayıcısında görsel gösterge sağlar.

- Kullanıcı özelliğe sağ tıklayıp **Sıfırla** ' yı seçerek özelliği varsayılan değerine geri yükleyebilirsiniz.

- Tasarımcı daha verimli kod üretir.

    > [!NOTE]
    > <xref:System.ComponentModel.DefaultValueAttribute> uygulayın ya da `Reset`*PropertyName* ve `ShouldSerialize`*PropertyName* yöntemleri sağlayın. Her ikisini de kullanmayın.

 `Reset`*PropertyName* yöntemi, aşağıdaki kod parçasında gösterildiği gibi bir özelliği varsayılan değerine ayarlar.

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
> Bir özelliğin `Reset` <xref:System.ComponentModel.DefaultValueAttribute>yöntemi yoksa ve bildiriminde varsayılan bir değer yoksa, bu özelliğin `Reset` seçeneği, Visual Studio 'daki Windows Form Tasarımcısı **Özellikler** penceresinin kısayol menüsünde devre dışı bırakılır...

 Visual Studio gibi tasarımcılar, bir özelliğin varsayılan değerinden değişip değişmediğini denetlemek için `ShouldSerialize`*PropertyName* metodunu kullanır ve bu sayede daha verimli kod oluşturulmasına izin verir. Örneğin:

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

 Tüm kod örnekleri aşağıda verilmiştir.

```vb
Option Explicit
Option Strict

Imports System.Drawing
Imports System.Windows.Forms

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
using System.Drawing;
using System.Windows.Forms;

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

 Bu durumda, `MyFont` özelliği tarafından erişilen özel değişkenin değeri `null`olduğunda bile, özellik tarayıcısı `null`görüntülemez; Bunun yerine, <xref:System.Windows.Forms.Control.Font%2A> özelliğini, `null`değilse veya <xref:System.Windows.Forms.Control>' de tanımlanan varsayılan <xref:System.Windows.Forms.Control.Font%2A> değeri görüntüler. Bu nedenle `MyFont` için varsayılan değer basitçe ayarlanamaz ve bu özelliğe bir <xref:System.ComponentModel.DefaultValueAttribute> uygulanamaz. Bunun yerine, `ShouldSerialize` ve `Reset` yöntemlerinin `MyFont` özelliği için uygulanması gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms Denetimlerindeki Özellikler](properties-in-windows-forms-controls.md)
- [Özellik Tanımlama](defining-a-property-in-windows-forms-controls.md)
- [Özellik Değişti Olayları](property-changed-events.md)
