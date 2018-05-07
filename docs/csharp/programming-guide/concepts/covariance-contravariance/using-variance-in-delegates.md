---
title: Temsilcilerde varyans (C#) kullanma
ms.date: 07/20/2015
ms.assetid: 1638c95d-dc8b-40c1-972c-c2dcf84be55e
ms.openlocfilehash: 46c09da9adac7ed47c32b1fed4311dfedbf5764e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="using-variance-in-delegates-c"></a>Temsilcilerde varyans (C#) kullanma
Bir temsilci için bir yöntem atadığınızda *Kovaryans* ve *değişken karşıtı* yöntemi imza bir temsilci türüyle eşleştirmek için esneklik sağlar. Kovaryans temsilci içinde tanımlanan daha fazla türetilmiş dönüş türüne sahip bir yöntem izin verir. Değişken karşıtı temsilci türü olandan daha az türetilmiş parametre türleri içeren bir yöntem izin verir.  
  
## <a name="example-1-covariance"></a>Örnek 1: kovaryansı  
  
### <a name="description"></a>Açıklama  
 Bu örnek, temsilci imza dönüş türden türetilmiş dönüş türlerine sahip yöntemleriyle temsilciler'ın nasıl kullanılabileceğini gösterir. Tarafından döndürülen veri türünü `DogsHandler` türü `Dogs`, den türetilen `Mammals` temsilci tanımlanan türü.  
  
### <a name="code"></a>Kod  
  
```csharp  
class Mammals{}  
class Dogs : Mammals{}  
  
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
  
## <a name="example-2-contravariance"></a>Örnek 2: değişken karşıtı  
  
### <a name="description"></a>Açıklama  
 Bu örnek temsilciler türünün temel türleri temsilci imza parametre türü parametrelerine sahip yöntemleriyle nasıl kullanılabileceğini gösterir. Değişken karşıtı ile bir olay işleyicisi yerine ayrı işleyicileri kullanabilirsiniz. Örneğin, kabul eden olay işleyicisi oluşturabilirsiniz bir `EventArgs` giriş parametresi ve onunla kullanmak bir `Button.MouseClick` gönderir olay bir `MouseEventArgs` türünü bir parametre olarak ve ile bir `TextBox.KeyDown` gönderir olay bir `KeyEventArgs` parametresi.  
  
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
 [Temsilcilerde varyans (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)  
 [İşlev ve eylem genel temsilciler (C#) için varyans kullanma](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
