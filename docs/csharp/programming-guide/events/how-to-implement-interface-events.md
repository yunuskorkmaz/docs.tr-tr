---
title: 'Nasıl yapılır: Arabirim olaylarını uygulama- C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], event implementation in classes
- events [C#], in interfaces
ms.assetid: 63527447-9535-4880-8e95-35e2075827df
ms.openlocfilehash: 574ea9927a22c24c356d84652fd29692c519247b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590510"
---
# <a name="how-to-implement-interface-events-c-programming-guide"></a><span data-ttu-id="f7ceb-102">Nasıl yapılır: Arabirim olaylarını uygulama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="f7ceb-102">How to: Implement Interface Events (C# Programming Guide)</span></span>
<span data-ttu-id="f7ceb-103">Bir [arabirim](../../language-reference/keywords/interface.md) , bir [olayı](../../language-reference/keywords/event.md)bildirebilir.</span><span class="sxs-lookup"><span data-stu-id="f7ceb-103">An [interface](../../language-reference/keywords/interface.md) can declare an [event](../../language-reference/keywords/event.md).</span></span> <span data-ttu-id="f7ceb-104">Aşağıdaki örnek, bir sınıfında arabirim olaylarının nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f7ceb-104">The following example shows how to implement interface events in a class.</span></span> <span data-ttu-id="f7ceb-105">Temel olarak kurallar, herhangi bir arabirim yöntemi veya özelliği uygularken olduğu gibidir.</span><span class="sxs-lookup"><span data-stu-id="f7ceb-105">Basically the rules are the same as when you implement any interface method or property.</span></span>  
  
## <a name="to-implement-interface-events-in-a-class"></a><span data-ttu-id="f7ceb-106">Arabirim olaylarını bir sınıfta uygulamak için</span><span class="sxs-lookup"><span data-stu-id="f7ceb-106">To implement interface events in a class</span></span>  
  
<span data-ttu-id="f7ceb-107">Sınıfınıza olayı bildirin ve uygun alanlarda çağırın.</span><span class="sxs-lookup"><span data-stu-id="f7ceb-107">Declare the event in your class and then invoke it in the appropriate areas.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="f7ceb-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="f7ceb-108">Example</span></span>  
<span data-ttu-id="f7ceb-109">Aşağıdaki örnek, sınıfınızın iki veya daha fazla arabirimden devraldığı daha az yaygın olan durumun nasıl işleneceğini ve her arabirimin aynı ada sahip bir olaya sahip olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f7ceb-109">The following example shows how to handle the less-common situation in which your class inherits from two or more interfaces and each interface has an event with the same name.</span></span> <span data-ttu-id="f7ceb-110">Bu durumda, en az bir olay için açık bir arabirim uygulamasını sağlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="f7ceb-110">In this situation, you must provide an explicit interface implementation for at least one of the events.</span></span> <span data-ttu-id="f7ceb-111">Bir olay için açık arabirim uygulama yazdığınızda, `add` ve `remove` olay erişimcilerini de yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7ceb-111">When you write an explicit interface implementation for an event, you must also write the `add` and `remove` event accessors.</span></span> <span data-ttu-id="f7ceb-112">Bunlar normalde derleyici tarafından sağlanır, ancak bu durumda derleyici bunları sağlayamaz.</span><span class="sxs-lookup"><span data-stu-id="f7ceb-112">Normally these are provided by the compiler, but in this case the compiler cannot provide them.</span></span>  
  
<span data-ttu-id="f7ceb-113">Kendi erişimclerinizi sunarak, iki olayın sınıfınıza aynı olay ile mi yoksa farklı olaylara göre mi temsil edileceğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7ceb-113">By providing your own accessors, you can specify whether the two events are represented by the same event in your class, or by different events.</span></span> <span data-ttu-id="f7ceb-114">Örneğin, olayların arabirim belirtimlerine göre farklı zamanlarda oluşturulması gerekiyorsa, her bir olayı sınıfınıza ayrı bir uygulamayla ilişkilendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7ceb-114">For example, if the events should be raised at different times according to the interface specifications, you can associate each event with a separate implementation in your class.</span></span> <span data-ttu-id="f7ceb-115">Aşağıdaki örnekte, aboneler bir `OnDraw` `IShape` veya bir veya bir `IDrawingObject`öğesine şekil başvurusunu kaldırarak hangi olayın alacağını tespit eder.</span><span class="sxs-lookup"><span data-stu-id="f7ceb-115">In the following example, subscribers determine which `OnDraw` event they will receive by casting the shape reference to either an `IShape` or an `IDrawingObject`.</span></span>  
  
 [!code-csharp[csProgGuideEvents#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#10)]
  
## <a name="see-also"></a><span data-ttu-id="f7ceb-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7ceb-116">See also</span></span>

- [<span data-ttu-id="f7ceb-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f7ceb-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f7ceb-118">Olaylar</span><span class="sxs-lookup"><span data-stu-id="f7ceb-118">Events</span></span>](./index.md)
- [<span data-ttu-id="f7ceb-119">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="f7ceb-119">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="f7ceb-120">Belirtik Arabirim Kullanma</span><span class="sxs-lookup"><span data-stu-id="f7ceb-120">Explicit Interface Implementation</span></span>](../interfaces/explicit-interface-implementation.md)
- [<span data-ttu-id="f7ceb-121">Nasıl yapılır: Türetilmiş sınıflarda temel sınıf olayları oluştur</span><span class="sxs-lookup"><span data-stu-id="f7ceb-121">How to: Raise Base Class Events in Derived Classes</span></span>](./how-to-raise-base-class-events-in-derived-classes.md)
