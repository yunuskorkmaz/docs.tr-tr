---
title: Temsilcilerde varyans (C#) kullanma
ms.date: 07/20/2015
ms.assetid: 1638c95d-dc8b-40c1-972c-c2dcf84be55e
ms.openlocfilehash: 5be4f786d2e1b8a0ead3fd58fe056e188faa916a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43501730"
---
# <a name="using-variance-in-delegates-c"></a>Temsilcilerde varyans (C#) kullanma
Bir temsilci için bir yöntem atadığınızda *Kovaryans* ve *kontravaryans* yöntem imzasını bir temsilci türüyle eşleştirmek için esneklik sağlar. Kovaryans Temsilcide tanımlanan daha fazla türetilmiş dönüş türüne sahip bir yöntem sağlar. Kontravaryans, temsilci türü olanlardan daha az türetilmiş parametre türleri olan bir yönteme izin verir.  
  
## <a name="example-1-covariance"></a>Örnek 1: Kovaryans  
  
### <a name="description"></a>Açıklama  
 Bu örnekte, temsilci imzasında dönüş türünden türetilmiş dönüş türlerine sahip yöntemler ile temsilciler'ın nasıl kullanılabileceğini gösterir. Tarafından döndürülen veri türünü `DogsHandler` türünde `Dogs`, öğesinden türetildiğini `Mammals` Temsilcide tanımlanan tür.  
  
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
  
## <a name="example-2-contravariance"></a>Örnek 2: kontravaryans  
  
### <a name="description"></a>Açıklama  
 Bu örnek, bir türün temsilci imzası parametre türü temel tür parametreleri olan yöntemler ile temsilciler nasıl kullanılabileceğini gösterir. Kontravaryans ile ayrı işleyicileri yerine bir olay işleyicisi kullanabilirsiniz. Kabul eden bir olay işleyicisi oluşturma gibi bir `EventArgs` giriş parametresi ve kullanılmakta olan bir `Button.MouseClick` gönderen olay bir `MouseEventArgs` türü bir parametre olarak ve ile bir `TextBox.KeyDown` gönderen olay bir `KeyEventArgs` parametresi.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.

- [Temsilcilerde varyans (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)  
- [İşlev ve eylem genel temsilcileri (C#) için varyans kullanma](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
