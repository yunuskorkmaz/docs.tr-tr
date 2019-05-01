---
title: 'Nasıl yapılır: Bağlı Denetimlerin Özelliklerini Açma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user controls [Windows Forms], exposing constituent controls
- controls [Windows Forms], constituent
- custom controls [Windows Forms], exposing properties
- constituent controls
ms.assetid: 5c1ec98b-aa48-4823-986e-4712551cfdf1
ms.openlocfilehash: 44b96218e674c754a1985f2f22a36707cd1776b6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941381"
---
# <a name="how-to-expose-properties-of-constituent-controls"></a><span data-ttu-id="46c8b-102">Nasıl yapılır: Bağlı Denetimlerin Özelliklerini Açma</span><span class="sxs-lookup"><span data-stu-id="46c8b-102">How to: Expose Properties of Constituent Controls</span></span>
<span data-ttu-id="46c8b-103">Bir bileşik denetimini oluşturan denetimler olarak adlandırılır *bağlı denetimler*.</span><span class="sxs-lookup"><span data-stu-id="46c8b-103">The controls that make up a composite control are called *constituent controls*.</span></span> <span data-ttu-id="46c8b-104">Bu denetimler normalde özel bildirilir ve böylece geliştirici tarafından erişilemez.</span><span class="sxs-lookup"><span data-stu-id="46c8b-104">These controls are normally declared private, and thus cannot be accessed by the developer.</span></span> <span data-ttu-id="46c8b-105">Bu denetimin özelliklerini gelecekteki kullanıcılar için kullanılabilir hale getirmek isterseniz, kullanıcıya göstermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="46c8b-105">If you want to make properties of these controls available to future users, you must expose them to the user.</span></span> <span data-ttu-id="46c8b-106">Bağlı bir denetimin bir özelliğine bir özelliği kullanıcı denetimi oluşturma ve kullanma kullanıma sunulduğunu `get` ve `set` bağlı denetimin özel özellik değişikliği efekt için bu özelliğin erişimcileri.</span><span class="sxs-lookup"><span data-stu-id="46c8b-106">A property of a constituent control is exposed by creating a property in the user control, and using the `get` and `set` accessors of that property to effect the change in the private property of the constituent control.</span></span>  
  
 <span data-ttu-id="46c8b-107">Bir kuramsal bir kullanıcı denetimi adlı bağlı bir düğmeyle göz önünde bulundurun `MyButton`.</span><span class="sxs-lookup"><span data-stu-id="46c8b-107">Consider a hypothetical user control with a constituent button named `MyButton`.</span></span> <span data-ttu-id="46c8b-108">Bu örnekte, kullanıcı istediğinde `ConstituentButtonBackColor` özelliği, içinde depolanan değeri <xref:System.Windows.Forms.Control.BackColor%2A> özelliği `MyButton` teslim edilir.</span><span class="sxs-lookup"><span data-stu-id="46c8b-108">In this example, when the user requests the `ConstituentButtonBackColor` property, the value stored in the <xref:System.Windows.Forms.Control.BackColor%2A> property of `MyButton` is delivered.</span></span> <span data-ttu-id="46c8b-109">Kullanıcı, bu özellik için bir değer atar, bu değeri otomatik olarak geçirilen <xref:System.Windows.Forms.Control.BackColor%2A> özelliği `MyButton` ve `set` kod yürütülecek, rengini değiştirme `MyButton`.</span><span class="sxs-lookup"><span data-stu-id="46c8b-109">When the user assigns a value to this property, that value is automatically passed to the <xref:System.Windows.Forms.Control.BackColor%2A> property of `MyButton` and the `set` code will execute, changing the color of `MyButton`.</span></span>  
  
 <span data-ttu-id="46c8b-110">Aşağıdaki örnek nasıl sunacağınızı öğrenin gösterir <xref:System.Windows.Forms.Control.BackColor%2A> bağlı düğmenin özelliği:</span><span class="sxs-lookup"><span data-stu-id="46c8b-110">The following example shows how to expose the <xref:System.Windows.Forms.Control.BackColor%2A> property of the constituent button:</span></span>  
  
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
  
### <a name="to-expose-a-property-of-a-constituent-control"></a><span data-ttu-id="46c8b-111">Bağlı bir denetimin bir özelliğine göstermek için</span><span class="sxs-lookup"><span data-stu-id="46c8b-111">To expose a property of a constituent control</span></span>  
  
1. <span data-ttu-id="46c8b-112">Kullanıcı denetiminiz için bir ortak özellik oluşturun.</span><span class="sxs-lookup"><span data-stu-id="46c8b-112">Create a public property for your user control.</span></span>  
  
2. <span data-ttu-id="46c8b-113">İçinde `get` bölümünde kullanıma sunmak istediğiniz özelliğin değerini alır. kod yazma özelliği.</span><span class="sxs-lookup"><span data-stu-id="46c8b-113">In the `get` section of the property, write code that retrieves the value of the property you want to expose.</span></span>  
  
3. <span data-ttu-id="46c8b-114">İçinde `set` bölümünü kullanıma sunulan bağlı denetim özelliğine özelliğinin değerini geçirir kod yazma özelliği.</span><span class="sxs-lookup"><span data-stu-id="46c8b-114">In the `set` section of the property, write code that passes the value of the property to the exposed property of the constituent control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46c8b-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46c8b-115">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- [<span data-ttu-id="46c8b-116">Windows Forms Denetimlerindeki Özellikler</span><span class="sxs-lookup"><span data-stu-id="46c8b-116">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
- [<span data-ttu-id="46c8b-117">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="46c8b-117">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
