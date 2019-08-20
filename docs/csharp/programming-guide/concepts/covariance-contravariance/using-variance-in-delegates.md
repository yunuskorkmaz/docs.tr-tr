---
title: Temsilcilerde (C#) varyans kullanma
ms.date: 07/20/2015
ms.assetid: 1638c95d-dc8b-40c1-972c-c2dcf84be55e
ms.openlocfilehash: 00e11d4ce755c8c75b73023fec14d95ebc96b4fe
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595268"
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
 Bu örnek, temsilci imza parametre türünün temel türü olan bir türün parametrelerine sahip yöntemlerle nasıl kullanılabileceğinizi gösterir. Değişken varyans ile ayrı işleyiciler yerine bir olay işleyicisi kullanabilirsiniz. Örneğin `EventArgs` , bir giriş parametresini kabul eden bir olay işleyicisi oluşturabilir ve bu `MouseEventArgs` `Button.MouseClick` parametreyi parametre `TextBox.KeyDown` olarak bir türü `KeyEventArgs` ve parametre gönderen bir olayla birlikte kullanabilirsiniz.  
  
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
