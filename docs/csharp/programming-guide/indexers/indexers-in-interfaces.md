---
title: Arabirimlerde Dizin oluşturucular- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: 4ac51589ed1680f8484fde797c045d15beed3af9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712123"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a><span data-ttu-id="ea4e6-102">Arabirimlerdeki Dizin Oluşturucular (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="ea4e6-102">Indexers in Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="ea4e6-103">Dizin oluşturucular bir [arabirimde](../../language-reference/keywords/interface.md)bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="ea4e6-103">Indexers can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="ea4e6-104">Arabirim dizin oluşturucularının erişimcileri, [sınıf](../../language-reference/keywords/class.md) dizin oluşturucularının erişimcilerine aşağıdaki yollarla göre farklılık gösterir:</span><span class="sxs-lookup"><span data-stu-id="ea4e6-104">Accessors of interface indexers differ from the accessors of [class](../../language-reference/keywords/class.md) indexers in the following ways:</span></span>  
  
- <span data-ttu-id="ea4e6-105">Arabirim erişimcileri değiştiriciler kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="ea4e6-105">Interface accessors do not use modifiers.</span></span>  
  
- <span data-ttu-id="ea4e6-106">Arabirim erişimcisinin gövdesi yok.</span><span class="sxs-lookup"><span data-stu-id="ea4e6-106">An interface accessor does not have a body.</span></span>  
  
 <span data-ttu-id="ea4e6-107">Bu nedenle, erişimcinin amacı, dizin oluşturucunun okuma-yazma, salt okunurdur veya salt yazılır olduğunu belirtsağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="ea4e6-107">Thus, the purpose of the accessor is to indicate whether the indexer is read-write, read-only, or write-only.</span></span>  
  
 <span data-ttu-id="ea4e6-108">Arabirim dizin oluşturucu erişimcisine bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="ea4e6-108">The following is an example of an interface indexer accessor:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#3)]  
  
 <span data-ttu-id="ea4e6-109">Bir dizin oluşturucunun imzası aynı arabirimde belirtilen diğer tüm dizin oluşturucularının imzalarından farklı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ea4e6-109">The signature of an indexer must differ from the signatures of all other indexers declared in the same interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea4e6-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="ea4e6-110">Example</span></span>  
 <span data-ttu-id="ea4e6-111">Aşağıdaki örnek, arabirim dizin oluşturucularının nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ea4e6-111">The following example shows how to implement interface indexers.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#4)]  
  
 <span data-ttu-id="ea4e6-112">Yukarıdaki örnekte, arabirim üyesinin tam adını kullanarak açık arabirim üye uygulamasını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ea4e6-112">In the preceding example, you could use the explicit interface member implementation by using the fully qualified name of the interface member.</span></span> <span data-ttu-id="ea4e6-113">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="ea4e6-113">For example:</span></span>  
  
```csharp  
string ISomeInterface.this[int index]   
{   
}   
```  
  
 <span data-ttu-id="ea4e6-114">Ancak, tam adı yalnızca, sınıf aynı Dizin Oluşturucu imzasına sahip birden fazla arabirim uygularken karışıklığı önlemek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ea4e6-114">However, the fully qualified name is only needed to avoid ambiguity when the class is implementing more than one interface with the same indexer signature.</span></span> <span data-ttu-id="ea4e6-115">Örneğin, bir `Employee` sınıfı iki arabirim uygusa, `ICitizen` ve `IEmployee`ve her iki arabirimde de aynı Dizin Oluşturucu imzası varsa, açık arabirim üye uygulaması gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ea4e6-115">For example, if an `Employee` class is implementing two interfaces, `ICitizen` and `IEmployee`, and both interfaces have the same indexer signature, the explicit interface member implementation is necessary.</span></span> <span data-ttu-id="ea4e6-116">Diğer bir deyişle, aşağıdaki Dizin Oluşturucu bildirimi:</span><span class="sxs-lookup"><span data-stu-id="ea4e6-116">That is, the following indexer declaration:</span></span>  
  
```csharp  
string IEmployee.this[int index]   
{   
}   
```  
  
 <span data-ttu-id="ea4e6-117">, aşağıdaki bildirim sırasında `IEmployee` arabiriminde Dizin oluşturucuyu uygular:</span><span class="sxs-lookup"><span data-stu-id="ea4e6-117">implements the indexer on the `IEmployee` interface, while the following declaration:</span></span>  
  
```csharp  
string ICitizen.this[int index]
{   
}   
```  
  
 <span data-ttu-id="ea4e6-118">`ICitizen` arabirimindeki Dizin oluşturucuyu uygular.</span><span class="sxs-lookup"><span data-stu-id="ea4e6-118">implements the indexer on the `ICitizen` interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea4e6-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea4e6-119">See also</span></span>

- [<span data-ttu-id="ea4e6-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ea4e6-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ea4e6-121">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="ea4e6-121">Indexers</span></span>](./index.md)
- [<span data-ttu-id="ea4e6-122">Veri Erişimi</span><span class="sxs-lookup"><span data-stu-id="ea4e6-122">Properties</span></span>](../classes-and-structs/properties.md)
- [<span data-ttu-id="ea4e6-123">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="ea4e6-123">Interfaces</span></span>](../interfaces/index.md)
