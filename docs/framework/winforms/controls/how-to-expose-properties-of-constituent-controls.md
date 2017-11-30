---
title: "Nasıl yapılır: Bağlı Denetimlerin Özelliklerini Açma"
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
- user controls [Windows Forms], exposing constituent controls
- controls [Windows Forms], constituent
- custom controls [Windows Forms], exposing properties
- constituent controls
ms.assetid: 5c1ec98b-aa48-4823-986e-4712551cfdf1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eb85cb77c28ad443fb6837a5305a080c450220f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-expose-properties-of-constituent-controls"></a><span data-ttu-id="6d821-102">Nasıl yapılır: Bağlı Denetimlerin Özelliklerini Açma</span><span class="sxs-lookup"><span data-stu-id="6d821-102">How to: Expose Properties of Constituent Controls</span></span>
<span data-ttu-id="6d821-103">Bileşik denetimini oluşturan denetimler adlandırılır *bağlı denetimler*.</span><span class="sxs-lookup"><span data-stu-id="6d821-103">The controls that make up a composite control are called *constituent controls*.</span></span> <span data-ttu-id="6d821-104">Bu denetimler, normalde özel bildirilir ve böylece geliştirici tarafından erişilemez.</span><span class="sxs-lookup"><span data-stu-id="6d821-104">These controls are normally declared private, and thus cannot be accessed by the developer.</span></span> <span data-ttu-id="6d821-105">Bu denetimlerin özelliklerini gelecekteki kullanıcılar için kullanılabilir hale getirmek istiyorsanız, kullanıcıya ortaya gerekir.</span><span class="sxs-lookup"><span data-stu-id="6d821-105">If you want to make properties of these controls available to future users, you must expose them to the user.</span></span> <span data-ttu-id="6d821-106">Bağlı bir denetimin bir özelliği bir özellik, kullanıcı denetimi oluşturma ve kullanma sunulan `get` ve `set` bağlı denetiminin özel özellik değişikliği etkilemek için o özelliğin erişimciler.</span><span class="sxs-lookup"><span data-stu-id="6d821-106">A property of a constituent control is exposed by creating a property in the user control, and using the `get` and `set` accessors of that property to effect the change in the private property of the constituent control.</span></span>  
  
 <span data-ttu-id="6d821-107">Adlı bir bağlı düğmesi ile bir kuramsal kullanıcı denetimi göz önünde bulundurun `MyButton`.</span><span class="sxs-lookup"><span data-stu-id="6d821-107">Consider a hypothetical user control with a constituent button named `MyButton`.</span></span> <span data-ttu-id="6d821-108">Bu örnekte, kullanıcı istediğinde `ConstituentButtonBackColor` özelliği, depolanan değer <xref:System.Windows.Forms.Control.BackColor%2A> özelliği `MyButton` teslim edilir.</span><span class="sxs-lookup"><span data-stu-id="6d821-108">In this example, when the user requests the `ConstituentButtonBackColor` property, the value stored in the <xref:System.Windows.Forms.Control.BackColor%2A> property of `MyButton` is delivered.</span></span> <span data-ttu-id="6d821-109">Kullanıcı Bu özellik için bir değer atandığında, bu değeri otomatik olarak geçirilir <xref:System.Windows.Forms.Control.BackColor%2A> özelliği `MyButton` ve `set` kod yürütülecek, rengi değiştirme `MyButton`.</span><span class="sxs-lookup"><span data-stu-id="6d821-109">When the user assigns a value to this property, that value is automatically passed to the <xref:System.Windows.Forms.Control.BackColor%2A> property of `MyButton` and the `set` code will execute, changing the color of `MyButton`.</span></span>  
  
 <span data-ttu-id="6d821-110">Aşağıdaki örnek, kullanıma sunmak gösterilmiştir <xref:System.Windows.Forms.Control.BackColor%2A> bağlı düğmesinin özelliği:</span><span class="sxs-lookup"><span data-stu-id="6d821-110">The following example shows how to expose the <xref:System.Windows.Forms.Control.BackColor%2A> property of the constituent button:</span></span>  
  
```vb  
Public Property ButtonColor() as System.Drawing.Color  
   Get  
      Return MyButton.BackColor  
   End Get  
   Set(Value as System.Drawing.Color)  
      MyButton.BackColor = Value  
   End Set  
End Property  
```  
  
```csharp  
public Color ButtonColor  
{  
   get  
   {  
      return(myButton.BackColor);  
   }  
   set  
   {  
      myButton.BackColor = value;  
   }  
}  
```  
  
### <a name="to-expose-a-property-of-a-constituent-control"></a><span data-ttu-id="6d821-111">Bağlı bir denetimin bir özellik kullanıma sunmak için</span><span class="sxs-lookup"><span data-stu-id="6d821-111">To expose a property of a constituent control</span></span>  
  
1.  <span data-ttu-id="6d821-112">Kullanıcı denetimi için ortak bir özellik oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6d821-112">Create a public property for your user control.</span></span>  
  
2.  <span data-ttu-id="6d821-113">İçinde `get` kullanıma sunmak istediğiniz özelliğin değerini alan kod yazma özelliği bölümü.</span><span class="sxs-lookup"><span data-stu-id="6d821-113">In the `get` section of the property, write code that retrieves the value of the property you want to expose.</span></span>  
  
3.  <span data-ttu-id="6d821-114">İçinde `set` özelliği, özelliğin değerini bağlı denetiminin gösterilen özelliğine gönderdiği kod yazma bölümü.</span><span class="sxs-lookup"><span data-stu-id="6d821-114">In the `set` section of the property, write code that passes the value of the property to the exposed property of the constituent control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d821-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6d821-115">See Also</span></span>  
 <xref:System.Windows.Forms.UserControl>  
 [<span data-ttu-id="6d821-116">Windows Forms denetimlerindeki Özellikler</span><span class="sxs-lookup"><span data-stu-id="6d821-116">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [<span data-ttu-id="6d821-117">Özel denetim çeşitleri</span><span class="sxs-lookup"><span data-stu-id="6d821-117">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
