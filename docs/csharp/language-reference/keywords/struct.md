---
title: struct (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: ddea59e76835ccccd07c299f819796336cddada8
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
---
# <a name="struct-c-reference"></a><span data-ttu-id="0a7b8-102">struct (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="0a7b8-102">struct (C# Reference)</span></span>
<span data-ttu-id="0a7b8-103">A `struct` türüdür genellikle bir dikdörtgen koordinatlarını veya öğeyi bir stok özelliklerini gibi ilgili değişkenlerin küçük gruplar kapsüllemek için kullanılan bir değer türü.</span><span class="sxs-lookup"><span data-stu-id="0a7b8-103">A `struct` type is a value type that is typically used to encapsulate small groups of related variables, such as the coordinates of a rectangle or the characteristics of an item in an inventory.</span></span> <span data-ttu-id="0a7b8-104">Aşağıdaki örnek, bir basit yapı bildirimi gösterir:</span><span class="sxs-lookup"><span data-stu-id="0a7b8-104">The following example shows a simple struct declaration:</span></span>  
  
```csharp  
public struct Book  
{  
    public decimal price;  
    public string title;  
    public string author;  
}  
```  
  
## <a name="remarks"></a><span data-ttu-id="0a7b8-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0a7b8-105">Remarks</span></span>  
 <span data-ttu-id="0a7b8-106">Yapılar de içerebilir [oluşturucular](../../../csharp/programming-guide/classes-and-structs/constructors.md), [sabitleri](../../../csharp/programming-guide/classes-and-structs/constants.md), [alanları](../../../csharp/programming-guide/classes-and-structs/fields.md), [yöntemleri](../../../csharp/programming-guide/classes-and-structs/methods.md), [özellikleri](../../../csharp/programming-guide/classes-and-structs/properties.md), [dizin oluşturucular](../../../csharp/programming-guide/indexers/index.md), [işleçleri](../../../csharp/programming-guide/statements-expressions-operators/operators.md), [olayları](../../../csharp/programming-guide/events/index.md), ve [türleri iç içe geçmiş](../../../csharp/programming-guide/classes-and-structs/nested-types.md), ancak bu tür üyeler, gerekirse, Bunun yerine, türü bir sınıf yapma göz önünde bulundurmalısınız.</span><span class="sxs-lookup"><span data-stu-id="0a7b8-106">Structs can also contain [constructors](../../../csharp/programming-guide/classes-and-structs/constructors.md), [constants](../../../csharp/programming-guide/classes-and-structs/constants.md), [fields](../../../csharp/programming-guide/classes-and-structs/fields.md), [methods](../../../csharp/programming-guide/classes-and-structs/methods.md), [properties](../../../csharp/programming-guide/classes-and-structs/properties.md), [indexers](../../../csharp/programming-guide/indexers/index.md), [operators](../../../csharp/programming-guide/statements-expressions-operators/operators.md), [events](../../../csharp/programming-guide/events/index.md), and [nested types](../../../csharp/programming-guide/classes-and-structs/nested-types.md), although if several such members are required, you should consider making your type a class instead.</span></span>  
  
 <span data-ttu-id="0a7b8-107">Örnekler için bkz: [kullanarak yapılar](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="0a7b8-107">For examples, see [Using Structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span></span>  
  
 <span data-ttu-id="0a7b8-108">Yapılar bir arabirimi uygulayabilirsiniz, ancak başka bir yapı devralınan olamaz.</span><span class="sxs-lookup"><span data-stu-id="0a7b8-108">Structs can implement an interface but they cannot inherit from another struct.</span></span> <span data-ttu-id="0a7b8-109">Bu nedenle, Yapı üyeleri olarak bildirilemez `protected`.</span><span class="sxs-lookup"><span data-stu-id="0a7b8-109">For that reason, struct members cannot be declared as `protected`.</span></span>  
  
 <span data-ttu-id="0a7b8-110">Daha fazla bilgi için bkz: [yapılar](../../../csharp/programming-guide/classes-and-structs/structs.md).</span><span class="sxs-lookup"><span data-stu-id="0a7b8-110">For more information, see [Structs](../../../csharp/programming-guide/classes-and-structs/structs.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="0a7b8-111">Örnekler</span><span class="sxs-lookup"><span data-stu-id="0a7b8-111">Examples</span></span>  
 <span data-ttu-id="0a7b8-112">Örnekler ve daha fazla bilgi için bkz: [kullanarak yapılar](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="0a7b8-112">For examples and more information, see [Using Structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="0a7b8-113">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="0a7b8-113">C# Language Specification</span></span>  
 <span data-ttu-id="0a7b8-114">Örnekler için bkz: [kullanarak yapılar](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="0a7b8-114">For examples, see [Using Structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a7b8-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0a7b8-115">See Also</span></span>  
 [<span data-ttu-id="0a7b8-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="0a7b8-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="0a7b8-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0a7b8-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0a7b8-118">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="0a7b8-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="0a7b8-119">Varsayılan Değerler Tablosu</span><span class="sxs-lookup"><span data-stu-id="0a7b8-119">Default Values Table</span></span>](../../../csharp/language-reference/keywords/default-values-table.md)  
 [<span data-ttu-id="0a7b8-120">Yerleşik Türler Tablosu</span><span class="sxs-lookup"><span data-stu-id="0a7b8-120">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="0a7b8-121">Türler</span><span class="sxs-lookup"><span data-stu-id="0a7b8-121">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="0a7b8-122">Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="0a7b8-122">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
 [<span data-ttu-id="0a7b8-123">class</span><span class="sxs-lookup"><span data-stu-id="0a7b8-123">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
 [<span data-ttu-id="0a7b8-124">interface</span><span class="sxs-lookup"><span data-stu-id="0a7b8-124">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
 [<span data-ttu-id="0a7b8-125">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="0a7b8-125">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
