---
title: Arabirimlerdeki Dizin Oluşturucular (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: 120b6e72a6ab906437c593d6eb33024d1df8f52b
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208411"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a><span data-ttu-id="a4a1e-102">Arabirimlerdeki Dizin Oluşturucular (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="a4a1e-102">Indexers in Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="a4a1e-103">Dizin oluşturucular bildirilebilir bir [arabirimi](../../../csharp/language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="a4a1e-103">Indexers can be declared on an [interface](../../../csharp/language-reference/keywords/interface.md).</span></span> <span data-ttu-id="a4a1e-104">Arabirim Dizinleyicileri erişimciler erişimci farklı [sınıfı](../../../csharp/language-reference/keywords/class.md) dizin oluşturucular aşağıdaki yollarla:</span><span class="sxs-lookup"><span data-stu-id="a4a1e-104">Accessors of interface indexers differ from the accessors of [class](../../../csharp/language-reference/keywords/class.md) indexers in the following ways:</span></span>  
  
-   <span data-ttu-id="a4a1e-105">Arabirim erişimciler değiştiricileri kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="a4a1e-105">Interface accessors do not use modifiers.</span></span>  
  
-   <span data-ttu-id="a4a1e-106">Arabirim erişimci gövde yok.</span><span class="sxs-lookup"><span data-stu-id="a4a1e-106">An interface accessor does not have a body.</span></span>  
  
 <span data-ttu-id="a4a1e-107">Bu nedenle, dizin oluşturucu okuma-yazma, salt okunur veya sadece yazılabilir olduğunu belirtmek için erişimci amacı budur.</span><span class="sxs-lookup"><span data-stu-id="a4a1e-107">Thus, the purpose of the accessor is to indicate whether the indexer is read-write, read-only, or write-only.</span></span>  
  
 <span data-ttu-id="a4a1e-108">Arabirim dizin oluşturucu erişimci örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="a4a1e-108">The following is an example of an interface indexer accessor:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/indexers-in-interfaces_1.cs)]  
  
 <span data-ttu-id="a4a1e-109">Bir dizin oluşturucu imza aynı arabirimde bildirilen tüm diğer dizin oluşturucular imzalarını farklı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a4a1e-109">The signature of an indexer must differ from the signatures of all other indexers declared in the same interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4a1e-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="a4a1e-110">Example</span></span>  
 <span data-ttu-id="a4a1e-111">Aşağıdaki örnek, arabirim Dizinleyicileri uygulamak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a4a1e-111">The following example shows how to implement interface indexers.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/indexers-in-interfaces_2.cs)]  
  
 <span data-ttu-id="a4a1e-112">Önceki örnekte, arabirim üyesini tam adını kullanarak açık arabirim üye uygulaması kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4a1e-112">In the preceding example, you could use the explicit interface member implementation by using the fully qualified name of the interface member.</span></span> <span data-ttu-id="a4a1e-113">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="a4a1e-113">For example:</span></span>  
  
```  
string ISomeInterface.this[int index]   
{   
}   
```  
  
 <span data-ttu-id="a4a1e-114">Ancak, tam adı, yalnızca sınıf aynı dizin oluşturucu imzaya sahip birden fazla arabirimi uygularken Karışıklığı önlemek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a4a1e-114">However, the fully qualified name is only needed to avoid ambiguity when the class is implementing more than one interface with the same indexer signature.</span></span> <span data-ttu-id="a4a1e-115">Örneğin, bir `Employee` sınıfı iki arabirim uygulama `ICitizen` ve `IEmployee`, ve her iki arabirimde aynı dizin oluşturucu imza açık arabirim üye uygulaması gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a4a1e-115">For example, if an `Employee` class is implementing two interfaces, `ICitizen` and `IEmployee`, and both interfaces have the same indexer signature, the explicit interface member implementation is necessary.</span></span> <span data-ttu-id="a4a1e-116">Diğer bir deyişle, aşağıdaki dizin oluşturucu bildirimi:</span><span class="sxs-lookup"><span data-stu-id="a4a1e-116">That is, the following indexer declaration:</span></span>  
  
```  
string IEmployee.this[int index]   
{   
}   
```  
  
 <span data-ttu-id="a4a1e-117">üzerine dizinleyici uygulayan `IEmployee` arabirimi, aşağıdaki bildirimi sırasında:</span><span class="sxs-lookup"><span data-stu-id="a4a1e-117">implements the indexer on the `IEmployee` interface, while the following declaration:</span></span>  
  
```  
string ICitizen.this[int index]
{   
}   
```  
  
 <span data-ttu-id="a4a1e-118">üzerine dizinleyici uygulayan `ICitizen` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="a4a1e-118">implements the indexer on the `ICitizen` interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4a1e-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a4a1e-119">See Also</span></span>  
 [<span data-ttu-id="a4a1e-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a4a1e-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a4a1e-121">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="a4a1e-121">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
 [<span data-ttu-id="a4a1e-122">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a4a1e-122">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [<span data-ttu-id="a4a1e-123">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="a4a1e-123">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)
