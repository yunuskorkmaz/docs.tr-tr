---
title: Arabirim olaylarını uygulama-C# Programlama Kılavuzu
description: Sınıfında arabirim olaylarının nasıl uygulanacağını öğrenin. Kod örneklerine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], event implementation in classes
- events [C#], in interfaces
ms.assetid: 63527447-9535-4880-8e95-35e2075827df
ms.openlocfilehash: 153a2efa254bf2f2c81cec4b28a53207cdc4efe5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167554"
---
# <a name="how-to-implement-interface-events-c-programming-guide"></a><span data-ttu-id="ad0cc-104">Arabirim olaylarını uygulama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="ad0cc-104">How to implement interface events (C# Programming Guide)</span></span>

<span data-ttu-id="ad0cc-105">Bir [arabirim](../../language-reference/keywords/interface.md) , bir [olayı](../../language-reference/keywords/event.md)bildirebilir.</span><span class="sxs-lookup"><span data-stu-id="ad0cc-105">An [interface](../../language-reference/keywords/interface.md) can declare an [event](../../language-reference/keywords/event.md).</span></span> <span data-ttu-id="ad0cc-106">Aşağıdaki örnek, bir sınıfında arabirim olaylarının nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ad0cc-106">The following example shows how to implement interface events in a class.</span></span> <span data-ttu-id="ad0cc-107">Temel olarak kurallar, herhangi bir arabirim yöntemi veya özelliği uygularken olduğu gibidir.</span><span class="sxs-lookup"><span data-stu-id="ad0cc-107">Basically the rules are the same as when you implement any interface method or property.</span></span>  
  
## <a name="to-implement-interface-events-in-a-class"></a><span data-ttu-id="ad0cc-108">Arabirim olaylarını bir sınıfta uygulamak için</span><span class="sxs-lookup"><span data-stu-id="ad0cc-108">To implement interface events in a class</span></span>  
  
<span data-ttu-id="ad0cc-109">Sınıfınıza olayı bildirin ve uygun alanlarda çağırın.</span><span class="sxs-lookup"><span data-stu-id="ad0cc-109">Declare the event in your class and then invoke it in the appropriate areas.</span></span>  
  
```csharp
namespace ImplementInterfaceEvents  
{  
    public interface IDrawingObject  
    {  
        event EventHandler ShapeChanged;  
    }  
    public class MyEventArgs : EventArgs
    {  
        // class members  
    }  
    public class Shape : IDrawingObject  
    {  
        public event EventHandler ShapeChanged;  
        void ChangeShape()  
        {  
            // Do something here before the event…  

            OnShapeChanged(new MyEventArgs(/*arguments*/));  

            // or do something here after the event.
        }  
        protected virtual void OnShapeChanged(MyEventArgs e)  
        {  
            ShapeChanged?.Invoke(this, e);  
        }  
    }  

}  
```  
  
## <a name="example"></a><span data-ttu-id="ad0cc-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="ad0cc-110">Example</span></span>  

<span data-ttu-id="ad0cc-111">Aşağıdaki örnek, sınıfınızın iki veya daha fazla arabirimden devraldığı daha az yaygın olan durumun nasıl işleneceğini ve her arabirimin aynı ada sahip bir olaya sahip olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ad0cc-111">The following example shows how to handle the less-common situation in which your class inherits from two or more interfaces and each interface has an event with the same name.</span></span> <span data-ttu-id="ad0cc-112">Bu durumda, en az bir olay için açık bir arabirim uygulamasını sağlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="ad0cc-112">In this situation, you must provide an explicit interface implementation for at least one of the events.</span></span> <span data-ttu-id="ad0cc-113">Bir olay için açık arabirim uygulama yazdığınızda, `add` ve `remove` olay erişimcilerini de yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ad0cc-113">When you write an explicit interface implementation for an event, you must also write the `add` and `remove` event accessors.</span></span> <span data-ttu-id="ad0cc-114">Bunlar normalde derleyici tarafından sağlanır, ancak bu durumda derleyici bunları sağlayamaz.</span><span class="sxs-lookup"><span data-stu-id="ad0cc-114">Normally these are provided by the compiler, but in this case the compiler cannot provide them.</span></span>  
  
<span data-ttu-id="ad0cc-115">Kendi erişimclerinizi sunarak, iki olayın sınıfınıza aynı olay ile mi yoksa farklı olaylara göre mi temsil edileceğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ad0cc-115">By providing your own accessors, you can specify whether the two events are represented by the same event in your class, or by different events.</span></span> <span data-ttu-id="ad0cc-116">Örneğin, olayların arabirim belirtimlerine göre farklı zamanlarda oluşturulması gerekiyorsa, her bir olayı sınıfınıza ayrı bir uygulamayla ilişkilendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ad0cc-116">For example, if the events should be raised at different times according to the interface specifications, you can associate each event with a separate implementation in your class.</span></span> <span data-ttu-id="ad0cc-117">Aşağıdaki örnekte, aboneler `OnDraw` bir `IShape` veya bir veya bir öğesine şekil başvurusunu kaldırarak hangi olayın alacağını tespit eder `IDrawingObject` .</span><span class="sxs-lookup"><span data-stu-id="ad0cc-117">In the following example, subscribers determine which `OnDraw` event they will receive by casting the shape reference to either an `IShape` or an `IDrawingObject`.</span></span>  
  
 [!code-csharp[csProgGuideEvents#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#10)]
  
## <a name="see-also"></a><span data-ttu-id="ad0cc-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad0cc-118">See also</span></span>

- [<span data-ttu-id="ad0cc-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ad0cc-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ad0cc-120">Olaylar</span><span class="sxs-lookup"><span data-stu-id="ad0cc-120">Events</span></span>](./index.md)
- [<span data-ttu-id="ad0cc-121">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="ad0cc-121">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="ad0cc-122">Açık Arabirim Uygulaması</span><span class="sxs-lookup"><span data-stu-id="ad0cc-122">Explicit Interface Implementation</span></span>](../interfaces/explicit-interface-implementation.md)
- [<span data-ttu-id="ad0cc-123">Türetilmiş sınıflarda temel sınıf olayları oluşturma</span><span class="sxs-lookup"><span data-stu-id="ad0cc-123">How to raise base class events in derived classes</span></span>](./how-to-raise-base-class-events-in-derived-classes.md)
