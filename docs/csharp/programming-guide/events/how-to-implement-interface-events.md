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
# <a name="how-to-implement-interface-events-c-programming-guide"></a>Arabirim olayları nasıl uygulanır (C# Programlama Kılavuzu)
[Arabirim](../../language-reference/keywords/interface.md) bir [olayı](../../language-reference/keywords/event.md)bildirebilir. Aşağıdaki örnek, bir sınıfta arabirim olaylarının nasıl uygulanacağını gösterir. Temelde kurallar herhangi bir arabirim yöntemi veya özelliği uyguladığınız zaman aynıdır.  
  
## <a name="to-implement-interface-events-in-a-class"></a>Bir sınıfta arabirim olayları uygulamak için  
  
Olayı sınıfınızda bildirin ve ardından uygun alanlarda çağırın.  
  
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
Aşağıdaki örnek, sınıfınızın iki veya daha fazla arabirimden devraldığı ve her arabirimin aynı ada sahip bir olayı olduğu daha az yaygın durumu nasıl ele alınılacağını gösterir. Bu durumda, olaylardan en az biri için açık bir arabirim uygulaması sağlamanız gerekir. Bir olay için açık bir arabirim uygulaması yazdığınızda, olay ve `add` `remove` olay aksesuarlarını da yazmanız gerekir. Normalde bunlar derleyici tarafından sağlanır, ancak bu durumda derleyici bunları sağlayamaz.  
  
Kendi erişimcilerinizi sağlayarak, iki olayın sınıfınızda aynı olayla mı yoksa farklı olaylarla mı temsil edildiğini belirtebilirsiniz. Örneğin, olaylar arabirim belirtimlerine göre farklı zamanlarda yükseltilecekse, her olayı sınıfınızda ayrı bir uygulamayla ilişkilendirebilirsiniz. Aşağıdaki örnekte, aboneler `OnDraw` şekil referansını bir veya bir `IShape` `IDrawingObject`'e atarak hangi olayı alacaklarını belirlerler.  
  
 [!code-csharp[csProgGuideEvents#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#10)]
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Olaylar](./index.md)
- [Temsilciler](../delegates/index.md)
- [Belirtik Arabirim Kullanma](../interfaces/explicit-interface-implementation.md)
- [Türetilmiş sınıflarda temel sınıf olayları oluşturma](./how-to-raise-base-class-events-in-derived-classes.md)
