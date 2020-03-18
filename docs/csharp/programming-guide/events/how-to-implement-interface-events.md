---
title: Arayüz olayları nasıl uygulanır - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], event implementation in classes
- events [C#], in interfaces
ms.assetid: 63527447-9535-4880-8e95-35e2075827df
ms.openlocfilehash: 8c0d221ef1272a43e2682ef2af3fa37d2d12d35e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167487"
---
# <a name="how-to-implement-interface-events-c-programming-guide"></a><span data-ttu-id="04680-102">Arabirim olayları nasıl uygulanır (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="04680-102">How to implement interface events (C# Programming Guide)</span></span>
<span data-ttu-id="04680-103">[Arabirim](../../language-reference/keywords/interface.md) bir [olayı](../../language-reference/keywords/event.md)bildirebilir.</span><span class="sxs-lookup"><span data-stu-id="04680-103">An [interface](../../language-reference/keywords/interface.md) can declare an [event](../../language-reference/keywords/event.md).</span></span> <span data-ttu-id="04680-104">Aşağıdaki örnek, bir sınıfta arabirim olaylarının nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="04680-104">The following example shows how to implement interface events in a class.</span></span> <span data-ttu-id="04680-105">Temelde kurallar herhangi bir arabirim yöntemi veya özelliği uyguladığınız zaman aynıdır.</span><span class="sxs-lookup"><span data-stu-id="04680-105">Basically the rules are the same as when you implement any interface method or property.</span></span>  
  
## <a name="to-implement-interface-events-in-a-class"></a><span data-ttu-id="04680-106">Bir sınıfta arabirim olayları uygulamak için</span><span class="sxs-lookup"><span data-stu-id="04680-106">To implement interface events in a class</span></span>  
  
<span data-ttu-id="04680-107">Olayı sınıfınızda bildirin ve ardından uygun alanlarda çağırın.</span><span class="sxs-lookup"><span data-stu-id="04680-107">Declare the event in your class and then invoke it in the appropriate areas.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="04680-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="04680-108">Example</span></span>  
<span data-ttu-id="04680-109">Aşağıdaki örnek, sınıfınızın iki veya daha fazla arabirimden devraldığı ve her arabirimin aynı ada sahip bir olayı olduğu daha az yaygın durumu nasıl ele alınılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="04680-109">The following example shows how to handle the less-common situation in which your class inherits from two or more interfaces and each interface has an event with the same name.</span></span> <span data-ttu-id="04680-110">Bu durumda, olaylardan en az biri için açık bir arabirim uygulaması sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="04680-110">In this situation, you must provide an explicit interface implementation for at least one of the events.</span></span> <span data-ttu-id="04680-111">Bir olay için açık bir arabirim uygulaması yazdığınızda, olay ve `add` `remove` olay aksesuarlarını da yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="04680-111">When you write an explicit interface implementation for an event, you must also write the `add` and `remove` event accessors.</span></span> <span data-ttu-id="04680-112">Normalde bunlar derleyici tarafından sağlanır, ancak bu durumda derleyici bunları sağlayamaz.</span><span class="sxs-lookup"><span data-stu-id="04680-112">Normally these are provided by the compiler, but in this case the compiler cannot provide them.</span></span>  
  
<span data-ttu-id="04680-113">Kendi erişimcilerinizi sağlayarak, iki olayın sınıfınızda aynı olayla mı yoksa farklı olaylarla mı temsil edildiğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="04680-113">By providing your own accessors, you can specify whether the two events are represented by the same event in your class, or by different events.</span></span> <span data-ttu-id="04680-114">Örneğin, olaylar arabirim belirtimlerine göre farklı zamanlarda yükseltilecekse, her olayı sınıfınızda ayrı bir uygulamayla ilişkilendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="04680-114">For example, if the events should be raised at different times according to the interface specifications, you can associate each event with a separate implementation in your class.</span></span> <span data-ttu-id="04680-115">Aşağıdaki örnekte, aboneler `OnDraw` şekil referansını bir veya bir `IShape` `IDrawingObject`'e atarak hangi olayı alacaklarını belirlerler.</span><span class="sxs-lookup"><span data-stu-id="04680-115">In the following example, subscribers determine which `OnDraw` event they will receive by casting the shape reference to either an `IShape` or an `IDrawingObject`.</span></span>  
  
 [!code-csharp[csProgGuideEvents#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#10)]
  
## <a name="see-also"></a><span data-ttu-id="04680-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04680-116">See also</span></span>

- [<span data-ttu-id="04680-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="04680-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="04680-118">Olaylar</span><span class="sxs-lookup"><span data-stu-id="04680-118">Events</span></span>](./index.md)
- [<span data-ttu-id="04680-119">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="04680-119">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="04680-120">Belirtik Arabirim Kullanma</span><span class="sxs-lookup"><span data-stu-id="04680-120">Explicit Interface Implementation</span></span>](../interfaces/explicit-interface-implementation.md)
- [<span data-ttu-id="04680-121">Türetilmiş sınıflarda temel sınıf olayları oluşturma</span><span class="sxs-lookup"><span data-stu-id="04680-121">How to raise base class events in derived classes</span></span>](./how-to-raise-base-class-events-in-derived-classes.md)
