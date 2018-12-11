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
# <a name="how-to-implement-interface-events-c-programming-guide"></a>Nasıl Yapılır: Arabirim olaylarını uygulama (C# Programlama Kılavuzu)
Bir [arabirimi](../../../csharp/language-reference/keywords/interface.md) bildirebilirsiniz bir [olay](../../../csharp/language-reference/keywords/event.md). Aşağıdaki örnek, bir sınıf içinde arabirim olaylarını uygulama gösterilmiştir. Herhangi bir arabirim yöntemi veya özelliği uygularken temelde aynı kurallardır.  
  
## <a name="to-implement-interface-events-in-a-class"></a>Bir sınıf içinde arabirim olaylarını uygulama  
  
Sınıf içinde olay bildirmek ve ardından uygun alanları çağırır.  
  
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
  
## <a name="example"></a>Örnek  
Aşağıdaki örnek, sınıfınıza iki veya daha fazla arabirimlerinden devralır ve her bir arabirime sahip aynı ada sahip bir olay daha az yaygın durum nasıl ele alınacağını gösterir. Bu durumda, olayları en az biri için açık arabirim uygulaması sağlamalısınız. Bir olayın açık arabirim uygulaması yazdığınızda, ayrıca yazmalısınız `add` ve `remove` olay erişimcileri. Normalde bu derleyici tarafından sağlanır, ancak bu durumda derleyici bunları sağlayamaz.  
  
Kendi erişimcileri sağlayarak, iki olay sınıfınızın aynı olay tarafından ya da farklı olaylar tarafından temsil edilen belirtebilirsiniz. Örneğin, farklı zamanlarda arabirimi belirtimlerine göre olaylar harekete Geçirilmemesi gereken, ayrı bir uygulama ile Sınıfınız içinde her olay ilişkilendirebilirsiniz. Aşağıdaki örnekte, aboneleri hangi belirleme `OnDraw` olay alacağı şekli başvuru ya da atayarak bir `IShape` veya bir `IDrawingObject`.  
  
 [!code-csharp[WrapTwoInterfaceEvents](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-implement-interface-events_1.cs#everything)]
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Olaylar](../../../csharp/programming-guide/events/index.md)  
- [Temsilciler](../../../csharp/programming-guide/delegates/index.md)  
- [Belirtik Arabirim Kullanma](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)  
- [Nasıl yapılır: Türetilmiş sınıflarda temel sınıf olayları Yükselt](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)
