---
title: Varyans'ı Temsilcilerde Kullanma (C#)
ms.date: 07/20/2015
ms.assetid: 1638c95d-dc8b-40c1-972c-c2dcf84be55e
ms.openlocfilehash: 83e86e760edb17f6d9ae61864c154062d41416e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169772"
---
# <a name="using-variance-in-delegates-c"></a>Varyans'ı Temsilcilerde Kullanma (C#)
Bir temsilciye bir yöntem atadığınızda, *bir temsilci* türünü yöntem imzasıyla eşleştirmek için esneklik *sağlar.* Covariance, bir yöntemin, temsilcide tanımlanandan daha fazla türemiş iade türüne sahip olmasını izin verir. Kontravariance, temsilci türündekilerden daha az türemiş parametre türleri olan bir yönteme izin verir.  
  
## <a name="example-1-covariance"></a>Örnek 1: Tutarlılık  
  
### <a name="description"></a>Açıklama  
 Bu örnek, temsilci imzasındaki iade türünden türetilen dönüş türleri olan yöntemlerle temsilcilerin nasıl kullanılabileceğini gösterir. Döndürülen `DogsHandler` veri `Dogs`türü, temsilcide tanımlanan `Mammals` türden türetilmiştir.  
  
### <a name="code"></a>Kod  
  
```csharp  
class Mammals {}  
class Dogs : Mammals {}  
  
class Program  
{  
    // Define the delegate.  
    public delegate Mammals HandlerMethod();  
  
    public static Mammals MammalsHandler()  
    {  
        return null;  
    }  
  
    public static Dogs DogsHandler()  
    {  
        return null;  
    }  
  
    static void Test()  
    {  
        HandlerMethod handlerMammals = MammalsHandler;  
  
        // Covariance enables this assignment.  
        HandlerMethod handlerDogs = DogsHandler;  
    }  
}  
```  
  
## <a name="example-2-contravariance"></a>Örnek 2: Kontrayan  
  
### <a name="description"></a>Açıklama

Bu örnek, damada, damaizi parametre türü taban türleri olan parametrelere sahip yöntemlerle nasıl kullanılabileceğini gösterir. Kontravariance ile, ayrı işleyicileri yerine bir olay işleyicisi kullanabilirsiniz. Aşağıdaki örnekte iki temsilci kullanılır:

- <xref:System.Windows.Forms.KeyEventHandler> [Button.KeyDown](xref:System.Windows.Forms.Control.KeyDown) olayının imzasını tanımlayan bir temsilci. İmzası:

   ```csharp
   public delegate void KeyEventHandler(object sender, KeyEventArgs e)
   ```

- <xref:System.Windows.Forms.MouseEventHandler> [Button.MouseClick](xref:System.Windows.Forms.Control.MouseDown) olayının imzasını tanımlayan bir temsilci. İmzası:

   ```csharp
   public delegate void MouseEventHandler(object sender, MouseEventArgs e)
   ```

Örnek, parametresi olan bir <xref:System.EventArgs> olay işleyicisini `Button.KeyDown` tanımlar ve `Button.MouseClick` hem olayları hem de olayları işlemek için kullanır. Her ikisinin <xref:System.EventArgs> de <xref:System.Windows.Forms.KeyEventArgs> bir taban türü <xref:System.Windows.Forms.MouseEventArgs>olduğu için bunu yapabilir ve .
  
### <a name="code"></a>Kod  
  
```csharp  
// Event handler that accepts a parameter of the EventArgs type.  
private void MultiHandler(object sender, System.EventArgs e)  
{  
    label1.Text = System.DateTime.Now.ToString();  
}  
  
public Form1()  
{  
    InitializeComponent();  
  
    // You can use a method that has an EventArgs parameter,  
    // although the event expects the KeyEventArgs parameter.  
    this.button1.KeyDown += this.MultiHandler;  
  
    // You can use the same method
    // for an event that expects the MouseEventArgs parameter.  
    this.button1.MouseClick += this.MultiHandler;  
  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temsilcilerde Varyans (C#)](./variance-in-delegates.md)
- [Func ve Action Generic Delegeler için Varyans Kullanma (C#)](./using-variance-for-func-and-action-generic-delegates.md)
