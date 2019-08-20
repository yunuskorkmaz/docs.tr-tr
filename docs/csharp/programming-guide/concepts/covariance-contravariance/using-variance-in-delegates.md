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
# <a name="using-variance-in-delegates-c"></a><span data-ttu-id="aa641-102">Temsilcilerde (C#) varyans kullanma</span><span class="sxs-lookup"><span data-stu-id="aa641-102">Using Variance in Delegates (C#)</span></span>
<span data-ttu-id="aa641-103">Bir temsilciye bir yöntem atadığınızda, *Kovaryans* ve *değişken varyans* , bir temsilci türünü Yöntem imzasıyla eşleştirmek için esneklik sağlar.</span><span class="sxs-lookup"><span data-stu-id="aa641-103">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="aa641-104">Kovaryans, bir metodun, temsilde tanımlı olandan daha fazla türetilmiş dönüş türüne sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="aa641-104">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="aa641-105">Değişken Varyans, temsilci türünden daha az türetilmiş parametre türlerine sahip bir yönteme izin verir.</span><span class="sxs-lookup"><span data-stu-id="aa641-105">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>  
  
## <a name="example-1-covariance"></a><span data-ttu-id="aa641-106">Örnek 1: Ko</span><span class="sxs-lookup"><span data-stu-id="aa641-106">Example 1: Covariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="aa641-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aa641-107">Description</span></span>  
 <span data-ttu-id="aa641-108">Bu örnek, temsilci imzasında dönüş türünden türetilmiş dönüş türleri olan yöntemlerle temsilcilerin nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="aa641-108">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="aa641-109">Tarafından `DogsHandler` döndürülen veri `Dogs` türü`Mammals` , temsilde tanımlanan türden türetilen türüdür.</span><span class="sxs-lookup"><span data-stu-id="aa641-109">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>  
  
### <a name="code"></a><span data-ttu-id="aa641-110">Kod</span><span class="sxs-lookup"><span data-stu-id="aa641-110">Code</span></span>  
  
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
  
## <a name="example-2-contravariance"></a><span data-ttu-id="aa641-111">Örnek 2: Kontravaryans</span><span class="sxs-lookup"><span data-stu-id="aa641-111">Example 2: Contravariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="aa641-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aa641-112">Description</span></span>  
 <span data-ttu-id="aa641-113">Bu örnek, temsilci imza parametre türünün temel türü olan bir türün parametrelerine sahip yöntemlerle nasıl kullanılabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="aa641-113">This example demonstrates how delegates can be used with methods that have parameters of a type that are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="aa641-114">Değişken varyans ile ayrı işleyiciler yerine bir olay işleyicisi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aa641-114">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="aa641-115">Örneğin `EventArgs` , bir giriş parametresini kabul eden bir olay işleyicisi oluşturabilir ve bu `MouseEventArgs` `Button.MouseClick` parametreyi parametre `TextBox.KeyDown` olarak bir türü `KeyEventArgs` ve parametre gönderen bir olayla birlikte kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aa641-115">For example, you can create an event handler that accepts an `EventArgs` input parameter and use it with a `Button.MouseClick` event that sends a `MouseEventArgs` type as a parameter, and also with a `TextBox.KeyDown` event that sends a `KeyEventArgs` parameter.</span></span>  
  
### <a name="code"></a><span data-ttu-id="aa641-116">Kod</span><span class="sxs-lookup"><span data-stu-id="aa641-116">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="aa641-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa641-117">See also</span></span>

- [<span data-ttu-id="aa641-118">Temsilcilerde varyans (C#)</span><span class="sxs-lookup"><span data-stu-id="aa641-118">Variance in Delegates (C#)</span></span>](./variance-in-delegates.md)
- [<span data-ttu-id="aa641-119">Func ve eylem genel temsilcileri için varyans kullanma (C#)</span><span class="sxs-lookup"><span data-stu-id="aa641-119">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)
