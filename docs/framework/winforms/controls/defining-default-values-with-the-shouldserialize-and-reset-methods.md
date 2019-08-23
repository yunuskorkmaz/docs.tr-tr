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
ms.openlocfilehash: 609fe4896a2b01b8a69ff8a3d0854c85ddbd6a26
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969093"
---
# <a name="defining-default-values-with-the-shouldserialize-and-reset-methods"></a>ShouldSerialize ile Varsayılan Değerleri Tanımlama ve Yöntemleri Sıfırlama
`ShouldSerialize`ve `Reset` özelliğin basit bir varsayılan değeri yoksa, özellik için sağlayabilmeniz için isteğe bağlı yöntemlerdir. Özelliğin basit bir varsayılan değeri varsa, öğesini uygulamanız <xref:System.ComponentModel.DefaultValueAttribute> ve bunun yerine öznitelik sınıfı oluşturucusuna varsayılan değeri sağlamanız gerekir. Bu mekanizmalardan herhangi biri, tasarımcıda aşağıdaki özellikleri sunar:

- Özelliği, varsayılan değerinden değiştirildiyse özellik tarayıcısında görsel gösterge sağlar.

- Kullanıcı özelliğe sağ tıklayıp **Sıfırla** ' yı seçerek özelliği varsayılan değerine geri yükleyebilirsiniz.

- Tasarımcı daha verimli kod üretir.

    > [!NOTE]
    > YadaPropertyName<xref:System.ComponentModel.DefaultValueAttribute> ve PropertyName`ShouldSerialize`yöntemlerini uygulayın. `Reset` Her ikisini de kullanmayın.

 PropertyName yöntemi, aşağıdaki kod parçasında gösterildiği gibi bir özelliği varsayılan değerine ayarlar. `Reset`

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
> Bir özelliğin `Reset` yöntemi yoksa, <xref:System.ComponentModel.DefaultValueAttribute>ve bildiriminde `Reset` bir varsayılan değer sağlanmadığında, bu özellik için seçeneği **Özellikler** penceresinin kısayol menüsünde devre dışı bırakılır. Visual Studio 'daki Windows Form Tasarımcısı.

 Visual Studio gibi tasarımcılar, bir özelliğin `ShouldSerialize`varsayılan değerinden değişip değişmediğini denetlemek ve yalnızca bir özellik değiştirilirse, bu sayede daha verimli kod oluşturulmasına izin vermek için bir özelliğin form içine silinip yazmadığını denetlemek için *PropertyName* metodunu kullanır. Örneğin:

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

 Bu `MyFont` durumda, `null` `null`özelliği tarafından erişilen özel değişkenin değeri olsa bile, özellik tarayıcısı görüntülenmez `null`; bunun yerine,, yoksa üst öğenin <xref:System.Windows.Forms.Control.Font%2A> özelliğini görüntüler, veya içinde <xref:System.Windows.Forms.Control.Font%2A> <xref:System.Windows.Forms.Control>tanımlanan varsayılan değer. Bu nedenle, varsayılan değeri `MyFont` basitçe ayarlanamaz <xref:System.ComponentModel.DefaultValueAttribute> ve bu özelliğe uygulanamaz. Bunun yerine, `Reset` `MyFont` ve yöntemlerinin özelliği için uygulanması gerekir. `ShouldSerialize`

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms Denetimlerindeki Özellikler](properties-in-windows-forms-controls.md)
- [Özellik Tanımlama](defining-a-property-in-windows-forms-controls.md)
- [Özellik Değişti Olayları](property-changed-events.md)
