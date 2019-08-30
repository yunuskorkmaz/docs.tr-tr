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
# <a name="using-variance-in-delegates-c"></a><span data-ttu-id="0cb7b-102">Temsilcilerde (C#) varyans kullanma</span><span class="sxs-lookup"><span data-stu-id="0cb7b-102">Using Variance in Delegates (C#)</span></span>
<span data-ttu-id="0cb7b-103">Bir temsilciye bir yöntem atadığınızda, *Kovaryans* ve *değişken varyans* , bir temsilci türünü Yöntem imzasıyla eşleştirmek için esneklik sağlar.</span><span class="sxs-lookup"><span data-stu-id="0cb7b-103">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="0cb7b-104">Kovaryans, bir metodun, temsilde tanımlı olandan daha fazla türetilmiş dönüş türüne sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="0cb7b-104">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="0cb7b-105">Değişken Varyans, temsilci türünden daha az türetilmiş parametre türlerine sahip bir yönteme izin verir.</span><span class="sxs-lookup"><span data-stu-id="0cb7b-105">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>  
  
## <a name="example-1-covariance"></a><span data-ttu-id="0cb7b-106">Örnek 1: Ko</span><span class="sxs-lookup"><span data-stu-id="0cb7b-106">Example 1: Covariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="0cb7b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0cb7b-107">Description</span></span>  
 <span data-ttu-id="0cb7b-108">Bu örnek, temsilci imzasında dönüş türünden türetilmiş dönüş türleri olan yöntemlerle temsilcilerin nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0cb7b-108">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="0cb7b-109">Tarafından `DogsHandler` döndürülen veri `Dogs` türü`Mammals` , temsilde tanımlanan türden türetilen türüdür.</span><span class="sxs-lookup"><span data-stu-id="0cb7b-109">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>  
  
### <a name="code"></a><span data-ttu-id="0cb7b-110">Kod</span><span class="sxs-lookup"><span data-stu-id="0cb7b-110">Code</span></span>  
  
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
  
## <a name="example-2-contravariance"></a><span data-ttu-id="0cb7b-111">Örnek 2: Kontravaryans</span><span class="sxs-lookup"><span data-stu-id="0cb7b-111">Example 2: Contravariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="0cb7b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0cb7b-112">Description</span></span>

<span data-ttu-id="0cb7b-113">Bu örnek, temsilci imza parametre türünün temel türleri olan parametrelere sahip Yöntemler ile temsilcilerin nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0cb7b-113">This example demonstrates how delegates can be used with methods that have parameters whose types are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="0cb7b-114">Değişken varyans ile ayrı işleyiciler yerine bir olay işleyicisi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0cb7b-114">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="0cb7b-115">Aşağıdaki örnek iki temsilcinin kullanımını sağlar:</span><span class="sxs-lookup"><span data-stu-id="0cb7b-115">The following example makes use of two delegates:</span></span>

- <span data-ttu-id="0cb7b-116"><xref:System.Windows.Forms.KeyEventHandler> [Button. KeyDown](xref:System.Windows.Forms.Control.KeyDown) olayının imzasını tanımlayan bir temsilci.</span><span class="sxs-lookup"><span data-stu-id="0cb7b-116">A <xref:System.Windows.Forms.KeyEventHandler> delegate that defines the signature of the [Button.KeyDown](xref:System.Windows.Forms.Control.KeyDown) event.</span></span> <span data-ttu-id="0cb7b-117">İmzası:</span><span class="sxs-lookup"><span data-stu-id="0cb7b-117">Its signature is:</span></span>

   ```csharp
   public delegate void KeyEventHandler(object sender, KeyEventArgs e)
   ```

- <span data-ttu-id="0cb7b-118"><xref:System.Windows.Forms.MouseEventHandler> [Button. MouseClick](xref:System.Windows.Forms.Control.MouseDown) olayının imzasını tanımlayan bir temsilci.</span><span class="sxs-lookup"><span data-stu-id="0cb7b-118">A <xref:System.Windows.Forms.MouseEventHandler> delegate that defines the signature of the [Button.MouseClick](xref:System.Windows.Forms.Control.MouseDown) event.</span></span> <span data-ttu-id="0cb7b-119">İmzası:</span><span class="sxs-lookup"><span data-stu-id="0cb7b-119">Its signature is:</span></span>

   ```csharp
   public delegate void MouseEventHandler(object sender, MouseEventArgs e)
   ```

<span data-ttu-id="0cb7b-120">Örnek, <xref:System.EventArgs> parametresiyle bir olay işleyicisini tanımlar ve `Button.KeyDown` hem hem de `Button.MouseClick` olaylarını işlemek için onu kullanır.</span><span class="sxs-lookup"><span data-stu-id="0cb7b-120">The example defines an event handler with an <xref:System.EventArgs> parameter and uses it to handle both the `Button.KeyDown` and `Button.MouseClick` events.</span></span> <span data-ttu-id="0cb7b-121">Bu <xref:System.EventArgs> <xref:System.Windows.Forms.KeyEventArgs> ,<xref:System.Windows.Forms.MouseEventArgs>hem hem de temel türü olduğundan bunu yapabilir.</span><span class="sxs-lookup"><span data-stu-id="0cb7b-121">It can do this because <xref:System.EventArgs> is a base type of both <xref:System.Windows.Forms.KeyEventArgs>  and <xref:System.Windows.Forms.MouseEventArgs>.</span></span> 
  
### <a name="code"></a><span data-ttu-id="0cb7b-122">Kod</span><span class="sxs-lookup"><span data-stu-id="0cb7b-122">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0cb7b-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0cb7b-123">See also</span></span>

- [<span data-ttu-id="0cb7b-124">Temsilcilerde varyans (C#)</span><span class="sxs-lookup"><span data-stu-id="0cb7b-124">Variance in Delegates (C#)</span></span>](./variance-in-delegates.md)
- [<span data-ttu-id="0cb7b-125">Func ve eylem genel temsilcileri için varyans kullanma (C#)</span><span class="sxs-lookup"><span data-stu-id="0cb7b-125">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)
