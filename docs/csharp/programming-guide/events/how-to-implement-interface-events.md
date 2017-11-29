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
ms.openlocfilehash: 944b894e7e5f305d35d4db96d7426bf05322ca54
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-interface-events-c-programming-guide"></a>Nasıl yapılır: Arabirim Olaylarını Uygulama (C# Programlama Kılavuzu)
Bir [arabirimi](../../../csharp/language-reference/keywords/interface.md) bildirebilir bir [olay](../../../csharp/language-reference/keywords/event.md). Aşağıdaki örnek, bir sınıf içinde arabirim olaylarını uygulama gösterilmektedir. Herhangi bir arabirim yöntemi veya özelliği uyguladığınızda temelde aynı kurallardır.  
  
### <a name="to-implement-interface-events-in-a-class"></a>Bir sınıfta arabirim olayları uygulamak için  
  
-   Sınıfınızda olay bildirme ve uygun alanlarında çağırma.  
  
    ```  
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
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek sınıfınız iki veya daha fazla arabirimden devralan ve aynı ada sahip bir olay her bir arabirime sahip daha az yaygın durum nasıl ele alınacağını gösterir. Bu durumda, olayları en az biri için bir açık arabirim uygulaması sağlamalısınız. Bir olay için bir açık arabirim uygulaması yazdığınızda, ayrıca yazmalısınız `add` ve `remove` olay erişimcileri. Normalde bu derleyici tarafından sağlanır, ancak bu durumda derleyici bunları sağlayamaz.  
  
 Kendi erişimciler sağlayarak, iki olay sınıfınız aynı olay tarafından ya da farklı olaylar tarafından temsil edilen belirtebilirsiniz. Örneğin, olayları arabirimi belirtimlerine uygun farklı zamanlarda oluşturulması gereken, ayrı bir uygulama ile sınıfınızda her olay ilişkilendirebilirsiniz. Aşağıdaki örnekte, aboneler hangi belirleme `OnDraw` alacağı şekli başvuru ya da atama tarafından olay bir `IShape` veya bir `IDrawingObject`.  
  
 [!code-csharp[csProgGuideEvents#10](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-implement-interface-events_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Olayları](../../../csharp/programming-guide/events/index.md)  
 [Temsilciler](../../../csharp/programming-guide/delegates/index.md)  
 [Açık arabirim uygulaması](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)  
 [Nasıl yapılır: türetilmiş sınıflarda temel sınıf olayları oluşturma](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)
