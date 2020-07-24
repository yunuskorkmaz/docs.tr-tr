---
title: Temsilcilerde varyans kullanma (C#)
description: Dahil edilen Kovaryans ve değişken varyans kodu örneklerini kullanarak Temsilcilerde varyansı nasıl kullanacağınızı öğrenin.
ms.date: 07/20/2015
ms.assetid: 1638c95d-dc8b-40c1-972c-c2dcf84be55e
ms.openlocfilehash: 62b0555ee29c5e7d2ba0954a8949d61596122cc7
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105679"
---
# <a name="using-variance-in-delegates-c"></a><span data-ttu-id="cbafd-103">Temsilcilerde varyans kullanma (C#)</span><span class="sxs-lookup"><span data-stu-id="cbafd-103">Using Variance in Delegates (C#)</span></span>
<span data-ttu-id="cbafd-104">Bir temsilciye bir yöntem atadığınızda, *Kovaryans* ve *değişken varyans* , bir temsilci türünü Yöntem imzasıyla eşleştirmek için esneklik sağlar.</span><span class="sxs-lookup"><span data-stu-id="cbafd-104">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="cbafd-105">Kovaryans, bir metodun, temsilde tanımlı olandan daha fazla türetilmiş dönüş türüne sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="cbafd-105">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="cbafd-106">Değişken Varyans, temsilci türünden daha az türetilmiş parametre türlerine sahip bir yönteme izin verir.</span><span class="sxs-lookup"><span data-stu-id="cbafd-106">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>  
  
## <a name="example-1-covariance"></a><span data-ttu-id="cbafd-107">Örnek 1: Kovaryans</span><span class="sxs-lookup"><span data-stu-id="cbafd-107">Example 1: Covariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="cbafd-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cbafd-108">Description</span></span>  
 <span data-ttu-id="cbafd-109">Bu örnek, temsilci imzasında dönüş türünden türetilmiş dönüş türleri olan yöntemlerle temsilcilerin nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="cbafd-109">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="cbafd-110">Tarafından döndürülen veri türü `DogsHandler` `Dogs` , `Mammals` temsilde tanımlanan türden türetilen türüdür.</span><span class="sxs-lookup"><span data-stu-id="cbafd-110">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>  
  
### <a name="code"></a><span data-ttu-id="cbafd-111">Kod</span><span class="sxs-lookup"><span data-stu-id="cbafd-111">Code</span></span>  
  
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
  
## <a name="example-2-contravariance"></a><span data-ttu-id="cbafd-112">Örnek 2: değişken varyans</span><span class="sxs-lookup"><span data-stu-id="cbafd-112">Example 2: Contravariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="cbafd-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cbafd-113">Description</span></span>

<span data-ttu-id="cbafd-114">Bu örnek, temsilci imza parametre türünün temel türleri olan parametrelere sahip Yöntemler ile temsilcilerin nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="cbafd-114">This example demonstrates how delegates can be used with methods that have parameters whose types are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="cbafd-115">Değişken varyans ile ayrı işleyiciler yerine bir olay işleyicisi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cbafd-115">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="cbafd-116">Aşağıdaki örnek iki temsilcinin kullanımını sağlar:</span><span class="sxs-lookup"><span data-stu-id="cbafd-116">The following example makes use of two delegates:</span></span>

- <span data-ttu-id="cbafd-117"><xref:System.Windows.Forms.KeyEventHandler> [Button. KeyDown](xref:System.Windows.Forms.Control.KeyDown) olayının imzasını tanımlayan bir temsilci.</span><span class="sxs-lookup"><span data-stu-id="cbafd-117">A <xref:System.Windows.Forms.KeyEventHandler> delegate that defines the signature of the [Button.KeyDown](xref:System.Windows.Forms.Control.KeyDown) event.</span></span> <span data-ttu-id="cbafd-118">İmzası:</span><span class="sxs-lookup"><span data-stu-id="cbafd-118">Its signature is:</span></span>

   ```csharp
   public delegate void KeyEventHandler(object sender, KeyEventArgs e)
   ```

- <span data-ttu-id="cbafd-119"><xref:System.Windows.Forms.MouseEventHandler> [Button. MouseClick](xref:System.Windows.Forms.Control.MouseDown) olayının imzasını tanımlayan bir temsilci.</span><span class="sxs-lookup"><span data-stu-id="cbafd-119">A <xref:System.Windows.Forms.MouseEventHandler> delegate that defines the signature of the [Button.MouseClick](xref:System.Windows.Forms.Control.MouseDown) event.</span></span> <span data-ttu-id="cbafd-120">İmzası:</span><span class="sxs-lookup"><span data-stu-id="cbafd-120">Its signature is:</span></span>

   ```csharp
   public delegate void MouseEventHandler(object sender, MouseEventArgs e)
   ```

<span data-ttu-id="cbafd-121">Örnek, parametresiyle bir olay işleyicisini tanımlar <xref:System.EventArgs> ve hem hem de olaylarını işlemek için onu kullanır `Button.KeyDown` `Button.MouseClick` .</span><span class="sxs-lookup"><span data-stu-id="cbafd-121">The example defines an event handler with an <xref:System.EventArgs> parameter and uses it to handle both the `Button.KeyDown` and `Button.MouseClick` events.</span></span> <span data-ttu-id="cbafd-122">Bu, <xref:System.EventArgs> hem hem de temel türü olduğundan bunu yapabilir <xref:System.Windows.Forms.KeyEventArgs> <xref:System.Windows.Forms.MouseEventArgs> .</span><span class="sxs-lookup"><span data-stu-id="cbafd-122">It can do this because <xref:System.EventArgs> is a base type of both <xref:System.Windows.Forms.KeyEventArgs>  and <xref:System.Windows.Forms.MouseEventArgs>.</span></span>
  
### <a name="code"></a><span data-ttu-id="cbafd-123">Kod</span><span class="sxs-lookup"><span data-stu-id="cbafd-123">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cbafd-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cbafd-124">See also</span></span>

- [<span data-ttu-id="cbafd-125">Temsilcilerde varyans (C#)</span><span class="sxs-lookup"><span data-stu-id="cbafd-125">Variance in Delegates (C#)</span></span>](./variance-in-delegates.md)
- [<span data-ttu-id="cbafd-126">Func ve eylem genel temsilcileri için varyans kullanma (C#)</span><span class="sxs-lookup"><span data-stu-id="cbafd-126">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)
