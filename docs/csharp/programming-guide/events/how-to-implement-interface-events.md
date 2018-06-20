---
title: 'Nasıl yapılır: Arabirim Olaylarını Uygulama (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], event implementation in classes
- events [C#], in interfaces
ms.assetid: 63527447-9535-4880-8e95-35e2075827df
ms.openlocfilehash: 9bd030efb2e3e7bdbf3bb727948a2aae04a2fe50
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208436"
---
# <a name="how-to-implement-interface-events-c-programming-guide"></a><span data-ttu-id="0f1b7-102">Nasıl yapılır: Arabirim Olaylarını Uygulama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="0f1b7-102">How to: Implement Interface Events (C# Programming Guide)</span></span>
<span data-ttu-id="0f1b7-103">Bir [arabirimi](../../../csharp/language-reference/keywords/interface.md) bildirebilir bir [olay](../../../csharp/language-reference/keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="0f1b7-103">An [interface](../../../csharp/language-reference/keywords/interface.md) can declare an [event](../../../csharp/language-reference/keywords/event.md).</span></span> <span data-ttu-id="0f1b7-104">Aşağıdaki örnek, bir sınıf içinde arabirim olaylarını uygulama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0f1b7-104">The following example shows how to implement interface events in a class.</span></span> <span data-ttu-id="0f1b7-105">Herhangi bir arabirim yöntemi veya özelliği uyguladığınızda temelde aynı kurallardır.</span><span class="sxs-lookup"><span data-stu-id="0f1b7-105">Basically the rules are the same as when you implement any interface method or property.</span></span>  
  
### <a name="to-implement-interface-events-in-a-class"></a><span data-ttu-id="0f1b7-106">Bir sınıfta arabirim olayları uygulamak için</span><span class="sxs-lookup"><span data-stu-id="0f1b7-106">To implement interface events in a class</span></span>  
  
-   <span data-ttu-id="0f1b7-107">Sınıfınızda olay bildirme ve uygun alanlarında çağırma.</span><span class="sxs-lookup"><span data-stu-id="0f1b7-107">Declare the event in your class and then invoke it in the appropriate areas.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="0f1b7-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f1b7-108">Example</span></span>  
<span data-ttu-id="0f1b7-109">Aşağıdaki örnek sınıfınız iki veya daha fazla arabirimden devralan ve aynı ada sahip bir olay her bir arabirime sahip daha az yaygın durum nasıl ele alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0f1b7-109">The following example shows how to handle the less-common situation in which your class inherits from two or more interfaces and each interface has an event with the same name.</span></span> <span data-ttu-id="0f1b7-110">Bu durumda, olayları en az biri için bir açık arabirim uygulaması sağlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="0f1b7-110">In this situation, you must provide an explicit interface implementation for at least one of the events.</span></span> <span data-ttu-id="0f1b7-111">Bir olay için bir açık arabirim uygulaması yazdığınızda, ayrıca yazmalısınız `add` ve `remove` olay erişimcileri.</span><span class="sxs-lookup"><span data-stu-id="0f1b7-111">When you write an explicit interface implementation for an event, you must also write the `add` and `remove` event accessors.</span></span> <span data-ttu-id="0f1b7-112">Normalde bu derleyici tarafından sağlanır, ancak bu durumda derleyici bunları sağlayamaz.</span><span class="sxs-lookup"><span data-stu-id="0f1b7-112">Normally these are provided by the compiler, but in this case the compiler cannot provide them.</span></span>  
  
<span data-ttu-id="0f1b7-113">Kendi erişimciler sağlayarak, iki olay sınıfınız aynı olay tarafından ya da farklı olaylar tarafından temsil edilen belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f1b7-113">By providing your own accessors, you can specify whether the two events are represented by the same event in your class, or by different events.</span></span> <span data-ttu-id="0f1b7-114">Örneğin, olayları arabirimi belirtimlerine uygun farklı zamanlarda oluşturulması gereken, ayrı bir uygulama ile sınıfınızda her olay ilişkilendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f1b7-114">For example, if the events should be raised at different times according to the interface specifications, you can associate each event with a separate implementation in your class.</span></span> <span data-ttu-id="0f1b7-115">Aşağıdaki örnekte, aboneler hangi belirleme `OnDraw` alacağı şekli başvuru ya da atama tarafından olay bir `IShape` veya bir `IDrawingObject`.</span><span class="sxs-lookup"><span data-stu-id="0f1b7-115">In the following example, subscribers determine which `OnDraw` event they will receive by casting the shape reference to either an `IShape` or an `IDrawingObject`.</span></span>  
  
 [!code-csharp[csProgGuideEvents#10](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-implement-interface-events_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="0f1b7-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0f1b7-116">See Also</span></span>  
 [<span data-ttu-id="0f1b7-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0f1b7-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0f1b7-118">Olaylar</span><span class="sxs-lookup"><span data-stu-id="0f1b7-118">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
 [<span data-ttu-id="0f1b7-119">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="0f1b7-119">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="0f1b7-120">Belirtik Arabirim Kullanma</span><span class="sxs-lookup"><span data-stu-id="0f1b7-120">Explicit Interface Implementation</span></span>](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)  
 [<span data-ttu-id="0f1b7-121">Nasıl yapılır: Türetilmiş Sınıflarda Temel Sınıf Olayları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0f1b7-121">How to: Raise Base Class Events in Derived Classes</span></span>](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)
