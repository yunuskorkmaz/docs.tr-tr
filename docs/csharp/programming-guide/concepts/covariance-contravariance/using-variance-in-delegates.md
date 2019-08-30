---
title: Temsilcilerde (C#) varyans kullanma
ms.date: 07/20/2015
ms.assetid: 1638c95d-dc8b-40c1-972c-c2dcf84be55e
ms.openlocfilehash: 980caf8d5e4699115d203a89fab7994d18cc1707
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168359"
---
# <a name="using-variance-in-delegates-c"></a>Temsilcilerde (C#) varyans kullanma
Bir temsilciye bir yöntem atadığınızda, *Kovaryans* ve *değişken varyans* , bir temsilci türünü Yöntem imzasıyla eşleştirmek için esneklik sağlar. Kovaryans, bir metodun, temsilde tanımlı olandan daha fazla türetilmiş dönüş türüne sahip olmasını sağlar. Değişken Varyans, temsilci türünden daha az türetilmiş parametre türlerine sahip bir yönteme izin verir.  
  
## <a name="example-1-covariance"></a>Örnek 1: Ko  
  
### <a name="description"></a>Açıklama  
 Bu örnek, temsilci imzasında dönüş türünden türetilmiş dönüş türleri olan yöntemlerle temsilcilerin nasıl kullanılabileceğini gösterir. Tarafından `DogsHandler` döndürülen veri `Dogs` türü`Mammals` , temsilde tanımlanan türden türetilen türüdür.  
  
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
  
## <a name="example-2-contravariance"></a>Örnek 2: Kontravaryans  
  
### <a name="description"></a>Açıklama

Bu örnek, temsilci imza parametre türünün temel türleri olan parametrelere sahip Yöntemler ile temsilcilerin nasıl kullanılabileceğini gösterir. Değişken varyans ile ayrı işleyiciler yerine bir olay işleyicisi kullanabilirsiniz. Aşağıdaki örnek iki temsilcinin kullanımını sağlar:

- <xref:System.Windows.Forms.KeyEventHandler> [Button. KeyDown](xref:System.Windows.Forms.Control.KeyDown) olayının imzasını tanımlayan bir temsilci. İmzası:

   ```csharp
   public delegate void KeyEventHandler(object sender, KeyEventArgs e)
   ```

- <xref:System.Windows.Forms.MouseEventHandler> [Button. MouseClick](xref:System.Windows.Forms.Control.MouseDown) olayının imzasını tanımlayan bir temsilci. İmzası:

   ```csharp
   public delegate void MouseEventHandler(object sender, MouseEventArgs e)
   ```

Örnek, <xref:System.EventArgs> parametresiyle bir olay işleyicisini tanımlar ve `Button.KeyDown` hem hem de `Button.MouseClick` olaylarını işlemek için onu kullanır. Bu <xref:System.EventArgs> <xref:System.Windows.Forms.KeyEventArgs> ,<xref:System.Windows.Forms.MouseEventArgs>hem hem de temel türü olduğundan bunu yapabilir. 
  
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

- [Temsilcilerde varyans (C#)](./variance-in-delegates.md)
- [Func ve eylem genel temsilcileri için varyans kullanma (C#)](./using-variance-for-func-and-action-generic-delegates.md)
