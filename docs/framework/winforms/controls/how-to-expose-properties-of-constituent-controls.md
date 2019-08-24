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
ms.openlocfilehash: f006e42771a5ecc71f6a508fd78d0e2dd8f2d2f2
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015867"
---
# <a name="how-to-expose-properties-of-constituent-controls"></a><span data-ttu-id="2dd30-102">Nasıl yapılır: Bağlı Denetimlerin Özelliklerini Açma</span><span class="sxs-lookup"><span data-stu-id="2dd30-102">How to: Expose Properties of Constituent Controls</span></span>
<span data-ttu-id="2dd30-103">Bileşik denetim oluşturan denetimlere *bileşen denetimleri*denir.</span><span class="sxs-lookup"><span data-stu-id="2dd30-103">The controls that make up a composite control are called *constituent controls*.</span></span> <span data-ttu-id="2dd30-104">Bu denetimler normalde özel olarak tanımlanır ve bu nedenle geliştirici tarafından erişilemez.</span><span class="sxs-lookup"><span data-stu-id="2dd30-104">These controls are normally declared private, and thus cannot be accessed by the developer.</span></span> <span data-ttu-id="2dd30-105">Bu denetimlerin özelliklerini gelecekteki kullanıcılar için kullanılabilir hale getirmek istiyorsanız, bunları kullanıcıya kullanıma sunmalısınız.</span><span class="sxs-lookup"><span data-stu-id="2dd30-105">If you want to make properties of these controls available to future users, you must expose them to the user.</span></span> <span data-ttu-id="2dd30-106">Yapısal denetimin bir özelliği, Kullanıcı denetimindeki bir özellik oluşturularak ve bu özelliğin, `get` bileşen denetiminin Private özelliğindeki değişikliği uygulamak için ve `set` erişimcilerinin kullanılması halinde sunulur.</span><span class="sxs-lookup"><span data-stu-id="2dd30-106">A property of a constituent control is exposed by creating a property in the user control, and using the `get` and `set` accessors of that property to effect the change in the private property of the constituent control.</span></span>

 <span data-ttu-id="2dd30-107">Adlı `MyButton`bir bileşen düğme ile kuramsal bir kullanıcı denetimi düşünün.</span><span class="sxs-lookup"><span data-stu-id="2dd30-107">Consider a hypothetical user control with a constituent button named `MyButton`.</span></span> <span data-ttu-id="2dd30-108">Bu örnekte, Kullanıcı `ConstituentButtonBackColor` özelliği istediğinde, <xref:System.Windows.Forms.Control.BackColor%2A> özelliğinde `MyButton` depolanan değer dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="2dd30-108">In this example, when the user requests the `ConstituentButtonBackColor` property, the value stored in the <xref:System.Windows.Forms.Control.BackColor%2A> property of `MyButton` is delivered.</span></span> <span data-ttu-id="2dd30-109">Kullanıcı bu özelliğe bir <xref:System.Windows.Forms.Control.BackColor%2A> değer atadığında, bu değer otomatik olarak `MyButton` özelliğine geçirilir ve `set` `MyButton`kod yürütülür ve rengini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="2dd30-109">When the user assigns a value to this property, that value is automatically passed to the <xref:System.Windows.Forms.Control.BackColor%2A> property of `MyButton` and the `set` code will execute, changing the color of `MyButton`.</span></span>

 <span data-ttu-id="2dd30-110">Aşağıdaki örnek, anayent düğmesinin <xref:System.Windows.Forms.Control.BackColor%2A> özelliğinin nasıl kullanıma sunulanın gösterir:</span><span class="sxs-lookup"><span data-stu-id="2dd30-110">The following example shows how to expose the <xref:System.Windows.Forms.Control.BackColor%2A> property of the constituent button:</span></span>

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

### <a name="to-expose-a-property-of-a-constituent-control"></a><span data-ttu-id="2dd30-111">Bir bileşen denetiminin özelliğini göstermek için</span><span class="sxs-lookup"><span data-stu-id="2dd30-111">To expose a property of a constituent control</span></span>

1. <span data-ttu-id="2dd30-112">Kullanıcı denetiminiz için bir ortak özellik oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2dd30-112">Create a public property for your user control.</span></span>

2. <span data-ttu-id="2dd30-113">`get` Özelliğinin bölümünde, göstermek istediğiniz özelliğin değerini alan kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="2dd30-113">In the `get` section of the property, write code that retrieves the value of the property you want to expose.</span></span>

3. <span data-ttu-id="2dd30-114">`set` Özelliğinin bölümünde, özelliğin değerini yapısal denetimin sunulma özelliğine geçiren kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="2dd30-114">In the `set` section of the property, write code that passes the value of the property to the exposed property of the constituent control.</span></span>

## <a name="see-also"></a><span data-ttu-id="2dd30-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2dd30-115">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- [<span data-ttu-id="2dd30-116">Windows Forms Denetimlerindeki Özellikler</span><span class="sxs-lookup"><span data-stu-id="2dd30-116">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
- [<span data-ttu-id="2dd30-117">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="2dd30-117">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
