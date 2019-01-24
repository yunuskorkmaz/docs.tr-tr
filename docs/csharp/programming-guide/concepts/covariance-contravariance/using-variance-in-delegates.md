---
title: Temsilcilerde varyans (C#) kullanma
ms.date: 07/20/2015
ms.assetid: 1638c95d-dc8b-40c1-972c-c2dcf84be55e
ms.openlocfilehash: 44a6153a9a1c0aa0aebb18710ea9e770fd4e57fe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54667287"
---
# <a name="using-variance-in-delegates-c"></a><span data-ttu-id="ee1fa-102">Temsilcilerde varyans (C#) kullanma</span><span class="sxs-lookup"><span data-stu-id="ee1fa-102">Using Variance in Delegates (C#)</span></span>
<span data-ttu-id="ee1fa-103">Bir temsilci için bir yöntem atadığınızda *Kovaryans* ve *kontravaryans* yöntem imzasını bir temsilci türüyle eşleştirmek için esneklik sağlar.</span><span class="sxs-lookup"><span data-stu-id="ee1fa-103">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="ee1fa-104">Kovaryans Temsilcide tanımlanan daha fazla türetilmiş dönüş türüne sahip bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="ee1fa-104">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="ee1fa-105">Kontravaryans, temsilci türü olanlardan daha az türetilmiş parametre türleri olan bir yönteme izin verir.</span><span class="sxs-lookup"><span data-stu-id="ee1fa-105">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>  
  
## <a name="example-1-covariance"></a><span data-ttu-id="ee1fa-106">Örnek 1: Kovaryans</span><span class="sxs-lookup"><span data-stu-id="ee1fa-106">Example 1: Covariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="ee1fa-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ee1fa-107">Description</span></span>  
 <span data-ttu-id="ee1fa-108">Bu örnekte, temsilci imzasında dönüş türünden türetilmiş dönüş türlerine sahip yöntemler ile temsilciler'ın nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ee1fa-108">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="ee1fa-109">Tarafından döndürülen veri türünü `DogsHandler` türünde `Dogs`, öğesinden türetildiğini `Mammals` Temsilcide tanımlanan tür.</span><span class="sxs-lookup"><span data-stu-id="ee1fa-109">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ee1fa-110">Kod</span><span class="sxs-lookup"><span data-stu-id="ee1fa-110">Code</span></span>  
  
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
  
## <a name="example-2-contravariance"></a><span data-ttu-id="ee1fa-111">Örnek 2: Kontravaryans</span><span class="sxs-lookup"><span data-stu-id="ee1fa-111">Example 2: Contravariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="ee1fa-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ee1fa-112">Description</span></span>  
 <span data-ttu-id="ee1fa-113">Bu örnek, bir türün temsilci imzası parametre türü temel tür parametreleri olan yöntemler ile temsilciler nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ee1fa-113">This example demonstrates how delegates can be used with methods that have parameters of a type that are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="ee1fa-114">Kontravaryans ile ayrı işleyicileri yerine bir olay işleyicisi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee1fa-114">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="ee1fa-115">Kabul eden bir olay işleyicisi oluşturma gibi bir `EventArgs` giriş parametresi ve kullanılmakta olan bir `Button.MouseClick` gönderen olay bir `MouseEventArgs` türü bir parametre olarak ve ile bir `TextBox.KeyDown` gönderen olay bir `KeyEventArgs` parametresi.</span><span class="sxs-lookup"><span data-stu-id="ee1fa-115">For example, you can create an event handler that accepts an `EventArgs` input parameter and use it with a `Button.MouseClick` event that sends a `MouseEventArgs` type as a parameter, and also with a `TextBox.KeyDown` event that sends a `KeyEventArgs` parameter.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ee1fa-116">Kod</span><span class="sxs-lookup"><span data-stu-id="ee1fa-116">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ee1fa-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee1fa-117">See also</span></span>

- [<span data-ttu-id="ee1fa-118">Temsilcilerde varyans (C#)</span><span class="sxs-lookup"><span data-stu-id="ee1fa-118">Variance in Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
- [<span data-ttu-id="ee1fa-119">İşlev ve eylem genel temsilcileri (C#) için varyans kullanma</span><span class="sxs-lookup"><span data-stu-id="ee1fa-119">Using Variance for Func and Action Generic Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
