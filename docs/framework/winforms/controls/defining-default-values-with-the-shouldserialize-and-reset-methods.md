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
# <a name="defining-default-values-with-the-shouldserialize-and-reset-methods"></a><span data-ttu-id="694a0-102">ShouldSerialize ile Varsayılan Değerleri Tanımlama ve Yöntemleri Sıfırlama</span><span class="sxs-lookup"><span data-stu-id="694a0-102">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>
<span data-ttu-id="694a0-103">`ShouldSerialize` ve `Reset` özelliği yoksa, bir özelliği için sağlayabilirsiniz isteğe bağlı yöntemlerdir bir basit varsayılan değere sahip.</span><span class="sxs-lookup"><span data-stu-id="694a0-103">`ShouldSerialize` and `Reset` are optional methods that you can provide for a property, if the property does not a have simple default value.</span></span> <span data-ttu-id="694a0-104">Özelliği bir basit varsayılan değere sahipse, uygulamalıdır <xref:System.ComponentModel.DefaultValueAttribute> ve bunun yerine varsayılan değer özniteliği sınıf oluşturucusuna sağlayın.</span><span class="sxs-lookup"><span data-stu-id="694a0-104">If the property has a simple default value, you should apply the <xref:System.ComponentModel.DefaultValueAttribute> and supply the default value to the attribute class constructor instead.</span></span> <span data-ttu-id="694a0-105">Bu mekanizmaların birini Tasarımcısı'nda aşağıdaki özellikleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="694a0-105">Either of these mechanisms enables the following features in the designer:</span></span>  
  
-   <span data-ttu-id="694a0-106">Varsayılan değerini değiştirdiyseniz özellik tarayıcısında visual belirtme özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="694a0-106">The property provides visual indication in the property browser if it has been modified from its default value.</span></span>  
  
-   <span data-ttu-id="694a0-107">Kullanıcı özelliği sağ tıklatın ve seçin **sıfırlama** özelliği varsayılan değerine geri yüklemek için.</span><span class="sxs-lookup"><span data-stu-id="694a0-107">The user can right-click on the property and choose **Reset** to restore the property to its default value.</span></span>  
  
-   <span data-ttu-id="694a0-108">Tasarımcı daha verimli kod oluşturur.</span><span class="sxs-lookup"><span data-stu-id="694a0-108">The designer generates more efficient code.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="694a0-109">Ya da uygulama <xref:System.ComponentModel.DefaultValueAttribute> veya sağlayan `Reset` *PropertyName* ve `ShouldSerialize` *PropertyName* yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="694a0-109">Either apply the <xref:System.ComponentModel.DefaultValueAttribute> or provide `Reset`*PropertyName* and `ShouldSerialize`*PropertyName* methods.</span></span> <span data-ttu-id="694a0-110">Her ikisini birden kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="694a0-110">Do not use both.</span></span>  
  
 <span data-ttu-id="694a0-111">`Reset` *PropertyName* yöntemini aşağıdaki kod parçasını gösterildiği gibi bu bir özelliği varsayılan değerine ayarlar.</span><span class="sxs-lookup"><span data-stu-id="694a0-111">The `Reset`*PropertyName* method sets a property to its default value, as shown in the following code fragment.</span></span>  
  
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
>  <span data-ttu-id="694a0-112">Bir özellik yoksa bir `Reset` yöntemi ile işaretlenmemiş bir <xref:System.ComponentModel.DefaultValueAttribute>ve bildiriminden, sağlanan varsayılan değeri yok `Reset` kısayol menüsünde, bu özelliği devre dışı seçeneği **özellikleri** Windows Form Tasarımcısı'nda Visual Studio penceresi.</span><span class="sxs-lookup"><span data-stu-id="694a0-112">If a property does not have a `Reset` method, is not marked with a <xref:System.ComponentModel.DefaultValueAttribute>, and does not have a default value supplied in its declaration, the `Reset` option for that property is disabled in the shortcut menu of the **Properties** window of the Windows Forms Designer in Visual Studio.</span></span>  
  
 <span data-ttu-id="694a0-113">Visual Studio gibi tasarımcıları `ShouldSerialize` *PropertyName* yöntemi bir özelliği varsayılan değerine değişip değişmediğini denetleyin ve kod yazma form eksikse bir özelliği değiştirildiğinde, bu nedenle daha verimli kod için izin verme oluşturma.</span><span class="sxs-lookup"><span data-stu-id="694a0-113">Designers such as Visual Studio use the `ShouldSerialize`*PropertyName* method to check whether a property has changed from its default value and write code into the form only if a property is changed, thus allowing for more efficient code generation.</span></span> <span data-ttu-id="694a0-114">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="694a0-114">For example:</span></span>  
  
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
  
 <span data-ttu-id="694a0-115">Tam kod örnek aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="694a0-115">A complete code example follows.</span></span>  
  
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
  
 <span data-ttu-id="694a0-116">Bu durumda, hatta özel bir değişken değeri tarafından erişildiğinde `MyFont` özelliği `null`, özellik tarayıcısı aşağıdaki dotnetclıtools'u görüntülemiyor `null`; bunun yerine, görüntülediği <xref:System.Windows.Forms.Control.Font%2A> değilse üst öğesinin özellik `null`, Varsayılan <xref:System.Windows.Forms.Control.Font%2A> tanımlanan değer <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="694a0-116">In this case, even when the value of the private variable accessed by the `MyFont` property is `null`, the property browser does not display `null`; instead, it displays the <xref:System.Windows.Forms.Control.Font%2A> property of the parent, if it is not `null`, or the default <xref:System.Windows.Forms.Control.Font%2A> value defined in <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="694a0-117">Bu nedenle için varsayılan değer `MyFont` yalnızca ayarlanamaz ve <xref:System.ComponentModel.DefaultValueAttribute> bu özelliğe uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="694a0-117">Thus the default value for `MyFont` cannot be simply set, and a <xref:System.ComponentModel.DefaultValueAttribute> cannot be applied to this property.</span></span> <span data-ttu-id="694a0-118">Bunun yerine, `ShouldSerialize` ve `Reset` yöntemleri için uygulanmalı `MyFont` özelliği.</span><span class="sxs-lookup"><span data-stu-id="694a0-118">Instead, the `ShouldSerialize` and `Reset` methods must be implemented for the `MyFont` property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="694a0-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="694a0-119">See also</span></span>

- [<span data-ttu-id="694a0-120">Windows Forms Denetimlerindeki Özellikler</span><span class="sxs-lookup"><span data-stu-id="694a0-120">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
- [<span data-ttu-id="694a0-121">Özellik Tanımlama</span><span class="sxs-lookup"><span data-stu-id="694a0-121">Defining a Property</span></span>](defining-a-property-in-windows-forms-controls.md)
- [<span data-ttu-id="694a0-122">Özellik Değişti Olayları</span><span class="sxs-lookup"><span data-stu-id="694a0-122">Property-Changed Events</span></span>](property-changed-events.md)
