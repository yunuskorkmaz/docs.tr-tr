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
# <a name="using-variance-in-delegates-c"></a><span data-ttu-id="5457e-102">Varyans'ı Temsilcilerde Kullanma (C#)</span><span class="sxs-lookup"><span data-stu-id="5457e-102">Using Variance in Delegates (C#)</span></span>
<span data-ttu-id="5457e-103">Bir temsilciye bir yöntem atadığınızda, *bir temsilci* türünü yöntem imzasıyla eşleştirmek için esneklik *sağlar.*</span><span class="sxs-lookup"><span data-stu-id="5457e-103">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="5457e-104">Covariance, bir yöntemin, temsilcide tanımlanandan daha fazla türemiş iade türüne sahip olmasını izin verir.</span><span class="sxs-lookup"><span data-stu-id="5457e-104">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="5457e-105">Kontravariance, temsilci türündekilerden daha az türemiş parametre türleri olan bir yönteme izin verir.</span><span class="sxs-lookup"><span data-stu-id="5457e-105">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>  
  
## <a name="example-1-covariance"></a><span data-ttu-id="5457e-106">Örnek 1: Tutarlılık</span><span class="sxs-lookup"><span data-stu-id="5457e-106">Example 1: Covariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="5457e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5457e-107">Description</span></span>  
 <span data-ttu-id="5457e-108">Bu örnek, temsilci imzasındaki iade türünden türetilen dönüş türleri olan yöntemlerle temsilcilerin nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5457e-108">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="5457e-109">Döndürülen `DogsHandler` veri `Dogs`türü, temsilcide tanımlanan `Mammals` türden türetilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5457e-109">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>  
  
### <a name="code"></a><span data-ttu-id="5457e-110">Kod</span><span class="sxs-lookup"><span data-stu-id="5457e-110">Code</span></span>  
  
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
  
## <a name="example-2-contravariance"></a><span data-ttu-id="5457e-111">Örnek 2: Kontrayan</span><span class="sxs-lookup"><span data-stu-id="5457e-111">Example 2: Contravariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="5457e-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5457e-112">Description</span></span>

<span data-ttu-id="5457e-113">Bu örnek, damada, damaizi parametre türü taban türleri olan parametrelere sahip yöntemlerle nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5457e-113">This example demonstrates how delegates can be used with methods that have parameters whose types are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="5457e-114">Kontravariance ile, ayrı işleyicileri yerine bir olay işleyicisi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5457e-114">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="5457e-115">Aşağıdaki örnekte iki temsilci kullanılır:</span><span class="sxs-lookup"><span data-stu-id="5457e-115">The following example makes use of two delegates:</span></span>

- <span data-ttu-id="5457e-116"><xref:System.Windows.Forms.KeyEventHandler> [Button.KeyDown](xref:System.Windows.Forms.Control.KeyDown) olayının imzasını tanımlayan bir temsilci.</span><span class="sxs-lookup"><span data-stu-id="5457e-116">A <xref:System.Windows.Forms.KeyEventHandler> delegate that defines the signature of the [Button.KeyDown](xref:System.Windows.Forms.Control.KeyDown) event.</span></span> <span data-ttu-id="5457e-117">İmzası:</span><span class="sxs-lookup"><span data-stu-id="5457e-117">Its signature is:</span></span>

   ```csharp
   public delegate void KeyEventHandler(object sender, KeyEventArgs e)
   ```

- <span data-ttu-id="5457e-118"><xref:System.Windows.Forms.MouseEventHandler> [Button.MouseClick](xref:System.Windows.Forms.Control.MouseDown) olayının imzasını tanımlayan bir temsilci.</span><span class="sxs-lookup"><span data-stu-id="5457e-118">A <xref:System.Windows.Forms.MouseEventHandler> delegate that defines the signature of the [Button.MouseClick](xref:System.Windows.Forms.Control.MouseDown) event.</span></span> <span data-ttu-id="5457e-119">İmzası:</span><span class="sxs-lookup"><span data-stu-id="5457e-119">Its signature is:</span></span>

   ```csharp
   public delegate void MouseEventHandler(object sender, MouseEventArgs e)
   ```

<span data-ttu-id="5457e-120">Örnek, parametresi olan bir <xref:System.EventArgs> olay işleyicisini `Button.KeyDown` tanımlar ve `Button.MouseClick` hem olayları hem de olayları işlemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="5457e-120">The example defines an event handler with an <xref:System.EventArgs> parameter and uses it to handle both the `Button.KeyDown` and `Button.MouseClick` events.</span></span> <span data-ttu-id="5457e-121">Her ikisinin <xref:System.EventArgs> de <xref:System.Windows.Forms.KeyEventArgs> bir taban türü <xref:System.Windows.Forms.MouseEventArgs>olduğu için bunu yapabilir ve .</span><span class="sxs-lookup"><span data-stu-id="5457e-121">It can do this because <xref:System.EventArgs> is a base type of both <xref:System.Windows.Forms.KeyEventArgs>  and <xref:System.Windows.Forms.MouseEventArgs>.</span></span>
  
### <a name="code"></a><span data-ttu-id="5457e-122">Kod</span><span class="sxs-lookup"><span data-stu-id="5457e-122">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5457e-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5457e-123">See also</span></span>

- [<span data-ttu-id="5457e-124">Temsilcilerde Varyans (C#)</span><span class="sxs-lookup"><span data-stu-id="5457e-124">Variance in Delegates (C#)</span></span>](./variance-in-delegates.md)
- [<span data-ttu-id="5457e-125">Func ve Action Generic Delegeler için Varyans Kullanma (C#)</span><span class="sxs-lookup"><span data-stu-id="5457e-125">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)
