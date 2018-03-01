---
title: "struct (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e8a848d5543291ef335e72cb7806158827e865dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="struct-c-reference"></a><span data-ttu-id="76934-102">struct (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="76934-102">struct (C# Reference)</span></span>
<span data-ttu-id="76934-103">A `struct` türüdür genellikle bir dikdörtgen koordinatlarını veya öğeyi bir stok özelliklerini gibi ilgili değişkenlerin küçük gruplar kapsüllemek için kullanılan bir değer türü.</span><span class="sxs-lookup"><span data-stu-id="76934-103">A `struct` type is a value type that is typically used to encapsulate small groups of related variables, such as the coordinates of a rectangle or the characteristics of an item in an inventory.</span></span> <span data-ttu-id="76934-104">Aşağıdaki örnek, bir basit yapı bildirimi gösterir:</span><span class="sxs-lookup"><span data-stu-id="76934-104">The following example shows a simple struct declaration:</span></span>  
  
```  
public struct Book  
{  
    public decimal price;  
    public string title;  
    public string author;  
}  
```  
  
## <a name="remarks"></a><span data-ttu-id="76934-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="76934-105">Remarks</span></span>  
 <span data-ttu-id="76934-106">Yapılar de içerebilir [oluşturucular](../../../csharp/programming-guide/classes-and-structs/constructors.md), [sabitleri](../../../csharp/programming-guide/classes-and-structs/constants.md), [alanları](../../../csharp/programming-guide/classes-and-structs/fields.md), [yöntemleri](../../../csharp/programming-guide/classes-and-structs/methods.md), [özellikleri](../../../csharp/programming-guide/classes-and-structs/properties.md), [dizin oluşturucular](../../../csharp/programming-guide/indexers/index.md), [işleçleri](../../../csharp/programming-guide/statements-expressions-operators/operators.md), [olayları](../../../csharp/programming-guide/events/index.md), ve [türleri iç içe geçmiş](../../../csharp/programming-guide/classes-and-structs/nested-types.md), ancak bu tür üyeler, gerekirse, Bunun yerine, türü bir sınıf yapma göz önünde bulundurmalısınız.</span><span class="sxs-lookup"><span data-stu-id="76934-106">Structs can also contain [constructors](../../../csharp/programming-guide/classes-and-structs/constructors.md), [constants](../../../csharp/programming-guide/classes-and-structs/constants.md), [fields](../../../csharp/programming-guide/classes-and-structs/fields.md), [methods](../../../csharp/programming-guide/classes-and-structs/methods.md), [properties](../../../csharp/programming-guide/classes-and-structs/properties.md), [indexers](../../../csharp/programming-guide/indexers/index.md), [operators](../../../csharp/programming-guide/statements-expressions-operators/operators.md), [events](../../../csharp/programming-guide/events/index.md), and [nested types](../../../csharp/programming-guide/classes-and-structs/nested-types.md), although if several such members are required, you should consider making your type a class instead.</span></span>  
  
 <span data-ttu-id="76934-107">Örnekler için bkz: [kullanarak yapılar](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="76934-107">For examples, see [Using Structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span></span>  
  
 <span data-ttu-id="76934-108">Yapılar bir arabirimi uygulayabilirsiniz, ancak başka bir yapı devralınan olamaz.</span><span class="sxs-lookup"><span data-stu-id="76934-108">Structs can implement an interface but they cannot inherit from another struct.</span></span> <span data-ttu-id="76934-109">Bu nedenle, Yapı üyeleri olarak bildirilemez `protected`.</span><span class="sxs-lookup"><span data-stu-id="76934-109">For that reason, struct members cannot be declared as `protected`.</span></span>  
  
 <span data-ttu-id="76934-110">Daha fazla bilgi için bkz: [yapılar](../../../csharp/programming-guide/classes-and-structs/structs.md).</span><span class="sxs-lookup"><span data-stu-id="76934-110">For more information, see [Structs](../../../csharp/programming-guide/classes-and-structs/structs.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="76934-111">Örnekler</span><span class="sxs-lookup"><span data-stu-id="76934-111">Examples</span></span>  
 <span data-ttu-id="76934-112">Örnekler ve daha fazla bilgi için bkz: [kullanarak yapılar](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="76934-112">For examples and more information, see [Using Structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="76934-113">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="76934-113">C# Language Specification</span></span>  
 <span data-ttu-id="76934-114">Örnekler için bkz: [kullanarak yapılar](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="76934-114">For examples, see [Using Structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76934-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="76934-115">See Also</span></span>  
 [<span data-ttu-id="76934-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="76934-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="76934-117">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="76934-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="76934-118">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="76934-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="76934-119">Varsayılan değerler tablosu</span><span class="sxs-lookup"><span data-stu-id="76934-119">Default Values Table</span></span>](../../../csharp/language-reference/keywords/default-values-table.md)  
 [<span data-ttu-id="76934-120">Yerleşik türler tablosu</span><span class="sxs-lookup"><span data-stu-id="76934-120">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="76934-121">Türler</span><span class="sxs-lookup"><span data-stu-id="76934-121">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="76934-122">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="76934-122">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
 [<span data-ttu-id="76934-123">sınıfı</span><span class="sxs-lookup"><span data-stu-id="76934-123">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
 [<span data-ttu-id="76934-124">arabirimi</span><span class="sxs-lookup"><span data-stu-id="76934-124">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
 [<span data-ttu-id="76934-125">Sınıflar ve yapılar</span><span class="sxs-lookup"><span data-stu-id="76934-125">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
