---
title: "Nasıl yapılır: Arabirim Olaylarını Uygulama (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- interfaces [C#], event implementation in classes
- events [C#], in interfaces
ms.assetid: 63527447-9535-4880-8e95-35e2075827df
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a53c6ba29837ad8827d97ea745be0462451eb145
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/05/2018
---
# <a name="how-to-implement-interface-events-c-programming-guide"></a><span data-ttu-id="c38a1-102">Nasıl yapılır: Arabirim Olaylarını Uygulama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c38a1-102">How to: Implement Interface Events (C# Programming Guide)</span></span>
<span data-ttu-id="c38a1-103">Bir [arabirimi](../../../csharp/language-reference/keywords/interface.md) bildirebilir bir [olay](../../../csharp/language-reference/keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="c38a1-103">An [interface](../../../csharp/language-reference/keywords/interface.md) can declare an [event](../../../csharp/language-reference/keywords/event.md).</span></span> <span data-ttu-id="c38a1-104">Aşağıdaki örnek, bir sınıf içinde arabirim olaylarını uygulama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c38a1-104">The following example shows how to implement interface events in a class.</span></span> <span data-ttu-id="c38a1-105">Herhangi bir arabirim yöntemi veya özelliği uyguladığınızda temelde aynı kurallardır.</span><span class="sxs-lookup"><span data-stu-id="c38a1-105">Basically the rules are the same as when you implement any interface method or property.</span></span>  
  
### <a name="to-implement-interface-events-in-a-class"></a><span data-ttu-id="c38a1-106">Bir sınıfta arabirim olayları uygulamak için</span><span class="sxs-lookup"><span data-stu-id="c38a1-106">To implement interface events in a class</span></span>  
  
-   <span data-ttu-id="c38a1-107">Sınıfınızda olay bildirme ve uygun alanlarında çağırma.</span><span class="sxs-lookup"><span data-stu-id="c38a1-107">Declare the event in your class and then invoke it in the appropriate areas.</span></span>  
  
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
                if(ShapeChanged != null)  
                {  
                   ShapeChanged(this, e);  
                }  
            }  
        }  
  
    }  
    ```  
  
## <a name="example"></a><span data-ttu-id="c38a1-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="c38a1-108">Example</span></span>  
 <span data-ttu-id="c38a1-109">Aşağıdaki örnek sınıfınız iki veya daha fazla arabirimden devralan ve aynı ada sahip bir olay her bir arabirime sahip daha az yaygın durum nasıl ele alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c38a1-109">The following example shows how to handle the less-common situation in which your class inherits from two or more interfaces and each interface has an event with the same name.</span></span> <span data-ttu-id="c38a1-110">Bu durumda, olayları en az biri için bir açık arabirim uygulaması sağlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="c38a1-110">In this situation, you must provide an explicit interface implementation for at least one of the events.</span></span> <span data-ttu-id="c38a1-111">Bir olay için bir açık arabirim uygulaması yazdığınızda, ayrıca yazmalısınız `add` ve `remove` olay erişimcileri.</span><span class="sxs-lookup"><span data-stu-id="c38a1-111">When you write an explicit interface implementation for an event, you must also write the `add` and `remove` event accessors.</span></span> <span data-ttu-id="c38a1-112">Normalde bu derleyici tarafından sağlanır, ancak bu durumda derleyici bunları sağlayamaz.</span><span class="sxs-lookup"><span data-stu-id="c38a1-112">Normally these are provided by the compiler, but in this case the compiler cannot provide them.</span></span>  
  
 <span data-ttu-id="c38a1-113">Kendi erişimciler sağlayarak, iki olay sınıfınız aynı olay tarafından ya da farklı olaylar tarafından temsil edilen belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c38a1-113">By providing your own accessors, you can specify whether the two events are represented by the same event in your class, or by different events.</span></span> <span data-ttu-id="c38a1-114">Örneğin, olayları arabirimi belirtimlerine uygun farklı zamanlarda oluşturulması gereken, ayrı bir uygulama ile sınıfınızda her olay ilişkilendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c38a1-114">For example, if the events should be raised at different times according to the interface specifications, you can associate each event with a separate implementation in your class.</span></span> <span data-ttu-id="c38a1-115">Aşağıdaki örnekte, aboneler hangi belirleme `OnDraw` alacağı şekli başvuru ya da atama tarafından olay bir `IShape` veya bir `IDrawingObject`.</span><span class="sxs-lookup"><span data-stu-id="c38a1-115">In the following example, subscribers determine which `OnDraw` event they will receive by casting the shape reference to either an `IShape` or an `IDrawingObject`.</span></span>  
  
 [!code-csharp[csProgGuideEvents#10](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-implement-interface-events_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="c38a1-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c38a1-116">See Also</span></span>  
 [<span data-ttu-id="c38a1-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c38a1-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c38a1-118">Olaylar</span><span class="sxs-lookup"><span data-stu-id="c38a1-118">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
 [<span data-ttu-id="c38a1-119">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="c38a1-119">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="c38a1-120">Belirtik Arabirim Kullanma</span><span class="sxs-lookup"><span data-stu-id="c38a1-120">Explicit Interface Implementation</span></span>](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)  
 [<span data-ttu-id="c38a1-121">Nasıl yapılır: Türetilmiş Sınıflarda Temel Sınıf Olayları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c38a1-121">How to: Raise Base Class Events in Derived Classes</span></span>](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)
