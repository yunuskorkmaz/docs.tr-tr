---
title: Arabirimlerdeki dizin - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: 07f2297512d59492320e7ac31fd44c9b0a7bedd7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970694"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a><span data-ttu-id="eb2cd-102">Arabirimlerdeki Dizin Oluşturucular (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="eb2cd-102">Indexers in Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="eb2cd-103">Dizin oluşturucular bildirilebilir bir [arabirimi](../../../csharp/language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="eb2cd-103">Indexers can be declared on an [interface](../../../csharp/language-reference/keywords/interface.md).</span></span> <span data-ttu-id="eb2cd-104">Arabirim dizin oluşturucuları erişicilerini erişicilerini farklı [sınıfı](../../../csharp/language-reference/keywords/class.md) dizin oluşturucuları aşağıdaki yollarla:</span><span class="sxs-lookup"><span data-stu-id="eb2cd-104">Accessors of interface indexers differ from the accessors of [class](../../../csharp/language-reference/keywords/class.md) indexers in the following ways:</span></span>  
  
-   <span data-ttu-id="eb2cd-105">Arabirimi erişimcileri değiştiriciler kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="eb2cd-105">Interface accessors do not use modifiers.</span></span>  
  
-   <span data-ttu-id="eb2cd-106">Bir arabirim erişimcisini bir gövde yok.</span><span class="sxs-lookup"><span data-stu-id="eb2cd-106">An interface accessor does not have a body.</span></span>  
  
 <span data-ttu-id="eb2cd-107">Bu nedenle, amacı erişimci, dizin oluşturucu salt okunur, salt okunur veya sadece yazılabilir olup olmadığını belirtmektir.</span><span class="sxs-lookup"><span data-stu-id="eb2cd-107">Thus, the purpose of the accessor is to indicate whether the indexer is read-write, read-only, or write-only.</span></span>  
  
 <span data-ttu-id="eb2cd-108">Arabirim dizin oluşturucu erişimci örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="eb2cd-108">The following is an example of an interface indexer accessor:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#3)]  
  
 <span data-ttu-id="eb2cd-109">Bir dizin oluşturucu imzasının aynı arabirimde bildirilen tüm diğer dizin imzalarını farklı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="eb2cd-109">The signature of an indexer must differ from the signatures of all other indexers declared in the same interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb2cd-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="eb2cd-110">Example</span></span>  
 <span data-ttu-id="eb2cd-111">Aşağıdaki örnek, arabirim dizin oluşturucuları uygulamak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="eb2cd-111">The following example shows how to implement interface indexers.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/indexers-in-interfaces_2.cs)]  
  
 <span data-ttu-id="eb2cd-112">Önceki örnekte, arabirim üyesini tam olarak nitelenmiş adını kullanarak açık arabirim üyesi uygulaması kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb2cd-112">In the preceding example, you could use the explicit interface member implementation by using the fully qualified name of the interface member.</span></span> <span data-ttu-id="eb2cd-113">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="eb2cd-113">For example:</span></span>  
  
```  
string ISomeInterface.this[int index]   
{   
}   
```  
  
 <span data-ttu-id="eb2cd-114">Ancak tam nitelikli ad, yalnızca aynı dizin oluşturucu imzaya sahip birden fazla arabirim sınıfı uygulanırken belirsizlik önlemek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="eb2cd-114">However, the fully qualified name is only needed to avoid ambiguity when the class is implementing more than one interface with the same indexer signature.</span></span> <span data-ttu-id="eb2cd-115">Örneğin, bir `Employee` sınıf iki arabirim uygulama `ICitizen` ve `IEmployee`, ve her iki arabirimde aynı dizin oluşturucu imzası, açık arabirim üyesi uygulaması gereklidir.</span><span class="sxs-lookup"><span data-stu-id="eb2cd-115">For example, if an `Employee` class is implementing two interfaces, `ICitizen` and `IEmployee`, and both interfaces have the same indexer signature, the explicit interface member implementation is necessary.</span></span> <span data-ttu-id="eb2cd-116">Diğer bir deyişle, aşağıdaki dizin oluşturucu bildirimi:</span><span class="sxs-lookup"><span data-stu-id="eb2cd-116">That is, the following indexer declaration:</span></span>  
  
```  
string IEmployee.this[int index]   
{   
}   
```  
  
 <span data-ttu-id="eb2cd-117">Dizin Oluşturucu üzerinde uygulayan `IEmployee` arabirimi, aşağıdaki bildirim yandan:</span><span class="sxs-lookup"><span data-stu-id="eb2cd-117">implements the indexer on the `IEmployee` interface, while the following declaration:</span></span>  
  
```  
string ICitizen.this[int index]
{   
}   
```  
  
 <span data-ttu-id="eb2cd-118">Dizin Oluşturucu üzerinde uygulayan `ICitizen` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="eb2cd-118">implements the indexer on the `ICitizen` interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb2cd-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb2cd-119">See also</span></span>

- [<span data-ttu-id="eb2cd-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="eb2cd-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="eb2cd-121">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="eb2cd-121">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)
- [<span data-ttu-id="eb2cd-122">Özellikler</span><span class="sxs-lookup"><span data-stu-id="eb2cd-122">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [<span data-ttu-id="eb2cd-123">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="eb2cd-123">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)
