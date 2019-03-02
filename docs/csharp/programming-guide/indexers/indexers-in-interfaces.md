---
title: Arabirimlerdeki dizin - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: c56369b28f8e1bab1ca8e8c13ebd9710c8f1d9fb
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57200110"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a><span data-ttu-id="77405-102">Arabirimlerdeki Dizin Oluşturucular (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="77405-102">Indexers in Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="77405-103">Dizin oluşturucular bildirilebilir bir [arabirimi](../../../csharp/language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="77405-103">Indexers can be declared on an [interface](../../../csharp/language-reference/keywords/interface.md).</span></span> <span data-ttu-id="77405-104">Arabirim dizin oluşturucuları erişicilerini erişicilerini farklı [sınıfı](../../../csharp/language-reference/keywords/class.md) dizin oluşturucuları aşağıdaki yollarla:</span><span class="sxs-lookup"><span data-stu-id="77405-104">Accessors of interface indexers differ from the accessors of [class](../../../csharp/language-reference/keywords/class.md) indexers in the following ways:</span></span>  
  
-   <span data-ttu-id="77405-105">Arabirimi erişimcileri değiştiriciler kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="77405-105">Interface accessors do not use modifiers.</span></span>  
  
-   <span data-ttu-id="77405-106">Bir arabirim erişimcisini bir gövde yok.</span><span class="sxs-lookup"><span data-stu-id="77405-106">An interface accessor does not have a body.</span></span>  
  
 <span data-ttu-id="77405-107">Bu nedenle, amacı erişimci, dizin oluşturucu salt okunur, salt okunur veya sadece yazılabilir olup olmadığını belirtmektir.</span><span class="sxs-lookup"><span data-stu-id="77405-107">Thus, the purpose of the accessor is to indicate whether the indexer is read-write, read-only, or write-only.</span></span>  
  
 <span data-ttu-id="77405-108">Arabirim dizin oluşturucu erişimci örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="77405-108">The following is an example of an interface indexer accessor:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#3)]  
  
 <span data-ttu-id="77405-109">Bir dizin oluşturucu imzasının aynı arabirimde bildirilen tüm diğer dizin imzalarını farklı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="77405-109">The signature of an indexer must differ from the signatures of all other indexers declared in the same interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77405-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="77405-110">Example</span></span>  
 <span data-ttu-id="77405-111">Aşağıdaki örnek, arabirim dizin oluşturucuları uygulamak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="77405-111">The following example shows how to implement interface indexers.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#4)]  
  
 <span data-ttu-id="77405-112">Önceki örnekte, arabirim üyesini tam olarak nitelenmiş adını kullanarak açık arabirim üyesi uygulaması kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="77405-112">In the preceding example, you could use the explicit interface member implementation by using the fully qualified name of the interface member.</span></span> <span data-ttu-id="77405-113">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="77405-113">For example:</span></span>  
  
```  
string ISomeInterface.this[int index]   
{   
}   
```  
  
 <span data-ttu-id="77405-114">Ancak tam nitelikli ad, yalnızca aynı dizin oluşturucu imzaya sahip birden fazla arabirim sınıfı uygulanırken belirsizlik önlemek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="77405-114">However, the fully qualified name is only needed to avoid ambiguity when the class is implementing more than one interface with the same indexer signature.</span></span> <span data-ttu-id="77405-115">Örneğin, bir `Employee` sınıf iki arabirim uygulama `ICitizen` ve `IEmployee`, ve her iki arabirimde aynı dizin oluşturucu imzası, açık arabirim üyesi uygulaması gereklidir.</span><span class="sxs-lookup"><span data-stu-id="77405-115">For example, if an `Employee` class is implementing two interfaces, `ICitizen` and `IEmployee`, and both interfaces have the same indexer signature, the explicit interface member implementation is necessary.</span></span> <span data-ttu-id="77405-116">Diğer bir deyişle, aşağıdaki dizin oluşturucu bildirimi:</span><span class="sxs-lookup"><span data-stu-id="77405-116">That is, the following indexer declaration:</span></span>  
  
```  
string IEmployee.this[int index]   
{   
}   
```  
  
 <span data-ttu-id="77405-117">Dizin Oluşturucu üzerinde uygulayan `IEmployee` arabirimi, aşağıdaki bildirim yandan:</span><span class="sxs-lookup"><span data-stu-id="77405-117">implements the indexer on the `IEmployee` interface, while the following declaration:</span></span>  
  
```  
string ICitizen.this[int index]
{   
}   
```  
  
 <span data-ttu-id="77405-118">Dizin Oluşturucu üzerinde uygulayan `ICitizen` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="77405-118">implements the indexer on the `ICitizen` interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77405-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77405-119">See also</span></span>

- [<span data-ttu-id="77405-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="77405-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="77405-121">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="77405-121">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)
- [<span data-ttu-id="77405-122">Özellikler</span><span class="sxs-lookup"><span data-stu-id="77405-122">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [<span data-ttu-id="77405-123">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="77405-123">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)
