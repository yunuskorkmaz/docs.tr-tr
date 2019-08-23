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
# <a name="defining-default-values-with-the-shouldserialize-and-reset-methods"></a><span data-ttu-id="da0a8-102">ShouldSerialize ile Varsayılan Değerleri Tanımlama ve Yöntemleri Sıfırlama</span><span class="sxs-lookup"><span data-stu-id="da0a8-102">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>
<span data-ttu-id="da0a8-103">`ShouldSerialize`ve `Reset` özelliğin basit bir varsayılan değeri yoksa, özellik için sağlayabilmeniz için isteğe bağlı yöntemlerdir.</span><span class="sxs-lookup"><span data-stu-id="da0a8-103">`ShouldSerialize` and `Reset` are optional methods that you can provide for a property, if the property does not a have simple default value.</span></span> <span data-ttu-id="da0a8-104">Özelliğin basit bir varsayılan değeri varsa, öğesini uygulamanız <xref:System.ComponentModel.DefaultValueAttribute> ve bunun yerine öznitelik sınıfı oluşturucusuna varsayılan değeri sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="da0a8-104">If the property has a simple default value, you should apply the <xref:System.ComponentModel.DefaultValueAttribute> and supply the default value to the attribute class constructor instead.</span></span> <span data-ttu-id="da0a8-105">Bu mekanizmalardan herhangi biri, tasarımcıda aşağıdaki özellikleri sunar:</span><span class="sxs-lookup"><span data-stu-id="da0a8-105">Either of these mechanisms enables the following features in the designer:</span></span>

- <span data-ttu-id="da0a8-106">Özelliği, varsayılan değerinden değiştirildiyse özellik tarayıcısında görsel gösterge sağlar.</span><span class="sxs-lookup"><span data-stu-id="da0a8-106">The property provides visual indication in the property browser if it has been modified from its default value.</span></span>

- <span data-ttu-id="da0a8-107">Kullanıcı özelliğe sağ tıklayıp **Sıfırla** ' yı seçerek özelliği varsayılan değerine geri yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da0a8-107">The user can right-click on the property and choose **Reset** to restore the property to its default value.</span></span>

- <span data-ttu-id="da0a8-108">Tasarımcı daha verimli kod üretir.</span><span class="sxs-lookup"><span data-stu-id="da0a8-108">The designer generates more efficient code.</span></span>

    > [!NOTE]
    > <span data-ttu-id="da0a8-109">YadaPropertyName<xref:System.ComponentModel.DefaultValueAttribute> ve PropertyName`ShouldSerialize`yöntemlerini uygulayın. `Reset`</span><span class="sxs-lookup"><span data-stu-id="da0a8-109">Either apply the <xref:System.ComponentModel.DefaultValueAttribute> or provide `Reset`*PropertyName* and `ShouldSerialize`*PropertyName* methods.</span></span> <span data-ttu-id="da0a8-110">Her ikisini de kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="da0a8-110">Do not use both.</span></span>

 <span data-ttu-id="da0a8-111">PropertyName yöntemi, aşağıdaki kod parçasında gösterildiği gibi bir özelliği varsayılan değerine ayarlar. `Reset`</span><span class="sxs-lookup"><span data-stu-id="da0a8-111">The `Reset`*PropertyName* method sets a property to its default value, as shown in the following code fragment.</span></span>

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
> <span data-ttu-id="da0a8-112">Bir özelliğin `Reset` yöntemi yoksa, <xref:System.ComponentModel.DefaultValueAttribute>ve bildiriminde `Reset` bir varsayılan değer sağlanmadığında, bu özellik için seçeneği **Özellikler** penceresinin kısayol menüsünde devre dışı bırakılır. Visual Studio 'daki Windows Form Tasarımcısı.</span><span class="sxs-lookup"><span data-stu-id="da0a8-112">If a property does not have a `Reset` method, is not marked with a <xref:System.ComponentModel.DefaultValueAttribute>, and does not have a default value supplied in its declaration, the `Reset` option for that property is disabled in the shortcut menu of the **Properties** window of the Windows Forms Designer in Visual Studio.</span></span>

 <span data-ttu-id="da0a8-113">Visual Studio gibi tasarımcılar, bir özelliğin `ShouldSerialize`varsayılan değerinden değişip değişmediğini denetlemek ve yalnızca bir özellik değiştirilirse, bu sayede daha verimli kod oluşturulmasına izin vermek için bir özelliğin form içine silinip yazmadığını denetlemek için *PropertyName* metodunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="da0a8-113">Designers such as Visual Studio use the `ShouldSerialize`*PropertyName* method to check whether a property has changed from its default value and write code into the form only if a property is changed, thus allowing for more efficient code generation.</span></span> <span data-ttu-id="da0a8-114">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="da0a8-114">For example:</span></span>

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

 <span data-ttu-id="da0a8-115">Tüm kod örnekleri aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="da0a8-115">A complete code example follows.</span></span>

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

 <span data-ttu-id="da0a8-116">Bu `MyFont` durumda, `null` `null`özelliği tarafından erişilen özel değişkenin değeri olsa bile, özellik tarayıcısı görüntülenmez `null`; bunun yerine,, yoksa üst öğenin <xref:System.Windows.Forms.Control.Font%2A> özelliğini görüntüler, veya içinde <xref:System.Windows.Forms.Control.Font%2A> <xref:System.Windows.Forms.Control>tanımlanan varsayılan değer.</span><span class="sxs-lookup"><span data-stu-id="da0a8-116">In this case, even when the value of the private variable accessed by the `MyFont` property is `null`, the property browser does not display `null`; instead, it displays the <xref:System.Windows.Forms.Control.Font%2A> property of the parent, if it is not `null`, or the default <xref:System.Windows.Forms.Control.Font%2A> value defined in <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="da0a8-117">Bu nedenle, varsayılan değeri `MyFont` basitçe ayarlanamaz <xref:System.ComponentModel.DefaultValueAttribute> ve bu özelliğe uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="da0a8-117">Thus the default value for `MyFont` cannot be simply set, and a <xref:System.ComponentModel.DefaultValueAttribute> cannot be applied to this property.</span></span> <span data-ttu-id="da0a8-118">Bunun yerine, `Reset` `MyFont` ve yöntemlerinin özelliği için uygulanması gerekir. `ShouldSerialize`</span><span class="sxs-lookup"><span data-stu-id="da0a8-118">Instead, the `ShouldSerialize` and `Reset` methods must be implemented for the `MyFont` property.</span></span>

## <a name="see-also"></a><span data-ttu-id="da0a8-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da0a8-119">See also</span></span>

- [<span data-ttu-id="da0a8-120">Windows Forms Denetimlerindeki Özellikler</span><span class="sxs-lookup"><span data-stu-id="da0a8-120">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
- [<span data-ttu-id="da0a8-121">Özellik Tanımlama</span><span class="sxs-lookup"><span data-stu-id="da0a8-121">Defining a Property</span></span>](defining-a-property-in-windows-forms-controls.md)
- [<span data-ttu-id="da0a8-122">Özellik Değişti Olayları</span><span class="sxs-lookup"><span data-stu-id="da0a8-122">Property-Changed Events</span></span>](property-changed-events.md)
