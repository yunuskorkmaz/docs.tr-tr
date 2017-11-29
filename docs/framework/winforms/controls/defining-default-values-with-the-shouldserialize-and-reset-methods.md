---
title: "ShouldSerialize ile Varsayılan Değerleri Tanımlama ve Yöntemleri Sıfırlama"
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
- custom controls [Windows Forms], property methods
- ShouldPersist method
ms.assetid: 7b6c5e00-3771-46b4-9142-5a80d5864a5e
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d082b0e3db1e1c115d28446cf515cf6acf60a7d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="defining-default-values-with-the-shouldserialize-and-reset-methods"></a><span data-ttu-id="bba02-102">ShouldSerialize ile Varsayılan Değerleri Tanımlama ve Yöntemleri Sıfırlama</span><span class="sxs-lookup"><span data-stu-id="bba02-102">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>
<span data-ttu-id="bba02-103">`ShouldSerialize`ve `Reset` özelliği yoksa, bir özellik için sağladığınız isteğe bağlı yöntemlerdir bir basit varsayılan değere sahip.</span><span class="sxs-lookup"><span data-stu-id="bba02-103">`ShouldSerialize` and `Reset` are optional methods that you can provide for a property, if the property does not a have simple default value.</span></span> <span data-ttu-id="bba02-104">Basit varsayılan bir değer özelliğine sahipse uygulamalıdır <xref:System.ComponentModel.DefaultValueAttribute> ve bunun yerine öznitelik sınıfı Oluşturucu için varsayılan değer sağlayın.</span><span class="sxs-lookup"><span data-stu-id="bba02-104">If the property has a simple default value, you should apply the <xref:System.ComponentModel.DefaultValueAttribute> and supply the default value to the attribute class constructor instead.</span></span> <span data-ttu-id="bba02-105">Bu mekanizmaların birini Tasarımcısı'nda aşağıdaki özellikleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="bba02-105">Either of these mechanisms enables the following features in the designer:</span></span>  
  
-   <span data-ttu-id="bba02-106">Varsayılan değerden değiştirilirse özelliği özellik tarayıcısında görsel bir gösterge sağlar.</span><span class="sxs-lookup"><span data-stu-id="bba02-106">The property provides visual indication in the property browser if it has been modified from its default value.</span></span>  
  
-   <span data-ttu-id="bba02-107">Kullanıcı özelliği sağ tıklatın ve seçin **sıfırlama** özelliğin varsayılan değeri geri yüklemek için.</span><span class="sxs-lookup"><span data-stu-id="bba02-107">The user can right-click on the property and choose **Reset** to restore the property to its default value.</span></span>  
  
-   <span data-ttu-id="bba02-108">Tasarımcı daha verimli kod oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bba02-108">The designer generates more efficient code.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bba02-109">Ya da geçerli <xref:System.ComponentModel.DefaultValueAttribute> veya sağlayın `Reset` *PropertyName* ve `ShouldSerialize` *PropertyName* yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="bba02-109">Either apply the <xref:System.ComponentModel.DefaultValueAttribute> or provide `Reset`*PropertyName* and `ShouldSerialize`*PropertyName* methods.</span></span> <span data-ttu-id="bba02-110">Her ikisini birden kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="bba02-110">Do not use both.</span></span>  
  
 <span data-ttu-id="bba02-111">`Reset` *PropertyName* yöntemini aşağıdaki kod parçasında gösterildiği gibi bu özellik varsayılan değerine ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bba02-111">The `Reset`*PropertyName* method sets a property to its default value, as shown in the following code fragment.</span></span>  
  
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
>  <span data-ttu-id="bba02-112">Bir özellik yoksa bir `Reset` yöntemi ile işaretlenmemiş bir <xref:System.ComponentModel.DefaultValueAttribute>ve kendi bildiriminde sağlanan varsayılan değeri yok `Reset` bu özellik kısayol menüsünü devre dışı seçeneğini **özellikleri** Windows Forms Tasarımcısı'nda pencerenin [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bba02-112">If a property does not have a `Reset` method, is not marked with a <xref:System.ComponentModel.DefaultValueAttribute>, and does not have a default value supplied in its declaration, the `Reset` option for that property is disabled in the shortcut menu of the **Properties** window of the Windows Forms Designer in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span></span>  
  
 <span data-ttu-id="bba02-113">Tasarımcılar gibi [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] kullanmak `ShouldSerialize` *PropertyName* yöntemi bir özelliğin varsayılan değerinden değişip değişmediğini denetleyin ve kod yazma form eksikse bir özelliği değiştirildiğinde, böylece daha verimli sağlar kod oluşturma.</span><span class="sxs-lookup"><span data-stu-id="bba02-113">Designers such as [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] use the `ShouldSerialize`*PropertyName* method to check whether a property has changed from its default value and write code into the form only if a property is changed, thus allowing for more efficient code generation.</span></span> <span data-ttu-id="bba02-114">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="bba02-114">For example:</span></span>  
  
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
  
 <span data-ttu-id="bba02-115">Tam kod örnek aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="bba02-115">A complete code example follows.</span></span>  
  
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
  
 <span data-ttu-id="bba02-116">Bu durumda, hatta özel değişkeninin değeri tarafından erişildiğinde `MyFont` özelliği `null`, özellik tarayıcısı görüntülenmez `null`; bunun yerine, gösterir <xref:System.Windows.Forms.Control.Font%2A> özellik değilse üst `null`, veya varsayılan <xref:System.Windows.Forms.Control.Font%2A> tanımlanan değer <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="bba02-116">In this case, even when the value of the private variable accessed by the `MyFont` property is `null`, the property browser does not display `null`; instead, it displays the <xref:System.Windows.Forms.Control.Font%2A> property of the parent, if it is not `null`, or the default <xref:System.Windows.Forms.Control.Font%2A> value defined in <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="bba02-117">Bu nedenle için varsayılan değer `MyFont` yalnızca ayarlanamaz ve bir <xref:System.ComponentModel.DefaultValueAttribute> bu özelliğe uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="bba02-117">Thus the default value for `MyFont` cannot be simply set, and a <xref:System.ComponentModel.DefaultValueAttribute> cannot be applied to this property.</span></span> <span data-ttu-id="bba02-118">Bunun yerine, `ShouldSerialize` ve `Reset` yöntem uygulanmadı, için `MyFont` özelliği.</span><span class="sxs-lookup"><span data-stu-id="bba02-118">Instead, the `ShouldSerialize` and `Reset` methods must be implemented for the `MyFont` property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bba02-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bba02-119">See Also</span></span>  
 [<span data-ttu-id="bba02-120">Windows Forms denetimlerindeki Özellikler</span><span class="sxs-lookup"><span data-stu-id="bba02-120">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [<span data-ttu-id="bba02-121">Özellik tanımlama</span><span class="sxs-lookup"><span data-stu-id="bba02-121">Defining a Property</span></span>](../../../../docs/framework/winforms/controls/defining-a-property-in-windows-forms-controls.md)  
 [<span data-ttu-id="bba02-122">Özellik değişti olayları</span><span class="sxs-lookup"><span data-stu-id="bba02-122">Property-Changed Events</span></span>](../../../../docs/framework/winforms/controls/property-changed-events.md)
