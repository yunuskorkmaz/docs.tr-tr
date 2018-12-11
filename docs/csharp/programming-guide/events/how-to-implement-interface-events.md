---
title: 'Nasıl Yapılır: -Arabirim olaylarını uygulama C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], event implementation in classes
- events [C#], in interfaces
ms.assetid: 63527447-9535-4880-8e95-35e2075827df
ms.openlocfilehash: d52d4d5140e96f81377733e39d1c36886718b706
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236446"
---
# <a name="how-to-implement-interface-events-c-programming-guide"></a><span data-ttu-id="cf663-102">Nasıl Yapılır: Arabirim olaylarını uygulama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="cf663-102">How to: Implement Interface Events (C# Programming Guide)</span></span>
<span data-ttu-id="cf663-103">Bir [arabirimi](../../../csharp/language-reference/keywords/interface.md) bildirebilirsiniz bir [olay](../../../csharp/language-reference/keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="cf663-103">An [interface](../../../csharp/language-reference/keywords/interface.md) can declare an [event](../../../csharp/language-reference/keywords/event.md).</span></span> <span data-ttu-id="cf663-104">Aşağıdaki örnek, bir sınıf içinde arabirim olaylarını uygulama gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="cf663-104">The following example shows how to implement interface events in a class.</span></span> <span data-ttu-id="cf663-105">Herhangi bir arabirim yöntemi veya özelliği uygularken temelde aynı kurallardır.</span><span class="sxs-lookup"><span data-stu-id="cf663-105">Basically the rules are the same as when you implement any interface method or property.</span></span>  
  
## <a name="to-implement-interface-events-in-a-class"></a><span data-ttu-id="cf663-106">Bir sınıf içinde arabirim olaylarını uygulama</span><span class="sxs-lookup"><span data-stu-id="cf663-106">To implement interface events in a class</span></span>  
  
<span data-ttu-id="cf663-107">Sınıf içinde olay bildirmek ve ardından uygun alanları çağırır.</span><span class="sxs-lookup"><span data-stu-id="cf663-107">Declare the event in your class and then invoke it in the appropriate areas.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="cf663-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="cf663-108">Example</span></span>  
<span data-ttu-id="cf663-109">Aşağıdaki örnek, sınıfınıza iki veya daha fazla arabirimlerinden devralır ve her bir arabirime sahip aynı ada sahip bir olay daha az yaygın durum nasıl ele alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cf663-109">The following example shows how to handle the less-common situation in which your class inherits from two or more interfaces and each interface has an event with the same name.</span></span> <span data-ttu-id="cf663-110">Bu durumda, olayları en az biri için açık arabirim uygulaması sağlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="cf663-110">In this situation, you must provide an explicit interface implementation for at least one of the events.</span></span> <span data-ttu-id="cf663-111">Bir olayın açık arabirim uygulaması yazdığınızda, ayrıca yazmalısınız `add` ve `remove` olay erişimcileri.</span><span class="sxs-lookup"><span data-stu-id="cf663-111">When you write an explicit interface implementation for an event, you must also write the `add` and `remove` event accessors.</span></span> <span data-ttu-id="cf663-112">Normalde bu derleyici tarafından sağlanır, ancak bu durumda derleyici bunları sağlayamaz.</span><span class="sxs-lookup"><span data-stu-id="cf663-112">Normally these are provided by the compiler, but in this case the compiler cannot provide them.</span></span>  
  
<span data-ttu-id="cf663-113">Kendi erişimcileri sağlayarak, iki olay sınıfınızın aynı olay tarafından ya da farklı olaylar tarafından temsil edilen belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf663-113">By providing your own accessors, you can specify whether the two events are represented by the same event in your class, or by different events.</span></span> <span data-ttu-id="cf663-114">Örneğin, farklı zamanlarda arabirimi belirtimlerine göre olaylar harekete Geçirilmemesi gereken, ayrı bir uygulama ile Sınıfınız içinde her olay ilişkilendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf663-114">For example, if the events should be raised at different times according to the interface specifications, you can associate each event with a separate implementation in your class.</span></span> <span data-ttu-id="cf663-115">Aşağıdaki örnekte, aboneleri hangi belirleme `OnDraw` olay alacağı şekli başvuru ya da atayarak bir `IShape` veya bir `IDrawingObject`.</span><span class="sxs-lookup"><span data-stu-id="cf663-115">In the following example, subscribers determine which `OnDraw` event they will receive by casting the shape reference to either an `IShape` or an `IDrawingObject`.</span></span>  
  
 [!code-csharp[WrapTwoInterfaceEvents](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-implement-interface-events_1.cs#everything)]
  
## <a name="see-also"></a><span data-ttu-id="cf663-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cf663-116">See Also</span></span>

- [<span data-ttu-id="cf663-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="cf663-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="cf663-118">Olaylar</span><span class="sxs-lookup"><span data-stu-id="cf663-118">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
- [<span data-ttu-id="cf663-119">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="cf663-119">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
- [<span data-ttu-id="cf663-120">Belirtik Arabirim Kullanma</span><span class="sxs-lookup"><span data-stu-id="cf663-120">Explicit Interface Implementation</span></span>](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)  
- [<span data-ttu-id="cf663-121">Nasıl yapılır: Türetilmiş sınıflarda temel sınıf olayları Yükselt</span><span class="sxs-lookup"><span data-stu-id="cf663-121">How to: Raise Base Class Events in Derived Classes</span></span>](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)
