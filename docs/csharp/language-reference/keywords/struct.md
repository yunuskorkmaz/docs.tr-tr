---
title: struct (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 7931da2e5f5c493b54eb1f33a1d6f57b38592f6e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43530198"
---
# <a name="struct-c-reference"></a><span data-ttu-id="7a4de-102">struct (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="7a4de-102">struct (C# Reference)</span></span>
<span data-ttu-id="7a4de-103">A `struct` türü, genelde küçük bir dikdörtgen koordinatlarını veya bir öğe bir stok özelliklerini gibi ilişkili değişken grupları kapsüllemek için kullanılan bir değer türüdür.</span><span class="sxs-lookup"><span data-stu-id="7a4de-103">A `struct` type is a value type that is typically used to encapsulate small groups of related variables, such as the coordinates of a rectangle or the characteristics of an item in an inventory.</span></span> <span data-ttu-id="7a4de-104">Aşağıdaki örnek, bir basit yapı bildirimi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7a4de-104">The following example shows a simple struct declaration:</span></span>  
  
```csharp  
public struct Book  
{  
    public decimal price;  
    public string title;  
    public string author;  
}  
```  
  
## <a name="remarks"></a><span data-ttu-id="7a4de-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7a4de-105">Remarks</span></span>  
 <span data-ttu-id="7a4de-106">Yapılar içerebilir [oluşturucular](../../../csharp/programming-guide/classes-and-structs/constructors.md), [sabitleri](../../../csharp/programming-guide/classes-and-structs/constants.md), [alanları](../../../csharp/programming-guide/classes-and-structs/fields.md), [yöntemleri](../../../csharp/programming-guide/classes-and-structs/methods.md), [özellikleri](../../../csharp/programming-guide/classes-and-structs/properties.md), [dizin oluşturucular](../../../csharp/programming-guide/indexers/index.md), [işleçleri](../../../csharp/programming-guide/statements-expressions-operators/operators.md), [olayları](../../../csharp/programming-guide/events/index.md), ve [türlerin](../../../csharp/programming-guide/classes-and-structs/nested-types.md), ancak birçok üye gerekliyse, türünüz bunun yerine bir sınıf yapma dikkate almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7a4de-106">Structs can also contain [constructors](../../../csharp/programming-guide/classes-and-structs/constructors.md), [constants](../../../csharp/programming-guide/classes-and-structs/constants.md), [fields](../../../csharp/programming-guide/classes-and-structs/fields.md), [methods](../../../csharp/programming-guide/classes-and-structs/methods.md), [properties](../../../csharp/programming-guide/classes-and-structs/properties.md), [indexers](../../../csharp/programming-guide/indexers/index.md), [operators](../../../csharp/programming-guide/statements-expressions-operators/operators.md), [events](../../../csharp/programming-guide/events/index.md), and [nested types](../../../csharp/programming-guide/classes-and-structs/nested-types.md), although if several such members are required, you should consider making your type a class instead.</span></span>  
  
 <span data-ttu-id="7a4de-107">Örnekler için bkz [yapılar kullanarak](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="7a4de-107">For examples, see [Using Structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span></span>  
  
 <span data-ttu-id="7a4de-108">Yapı birimleri arabirim uygulayabilir, ancak bunlar başka bir yapı devralamaz.</span><span class="sxs-lookup"><span data-stu-id="7a4de-108">Structs can implement an interface but they cannot inherit from another struct.</span></span> <span data-ttu-id="7a4de-109">Bu nedenle, Yapı üyeleri olarak bildirilemez `protected`.</span><span class="sxs-lookup"><span data-stu-id="7a4de-109">For that reason, struct members cannot be declared as `protected`.</span></span>  
  
 <span data-ttu-id="7a4de-110">Daha fazla bilgi için [yapılar](../../../csharp/programming-guide/classes-and-structs/structs.md).</span><span class="sxs-lookup"><span data-stu-id="7a4de-110">For more information, see [Structs](../../../csharp/programming-guide/classes-and-structs/structs.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="7a4de-111">Örnekler</span><span class="sxs-lookup"><span data-stu-id="7a4de-111">Examples</span></span>  
 <span data-ttu-id="7a4de-112">Örnekler ve daha fazla bilgi için bkz. [yapılar kullanarak](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="7a4de-112">For examples and more information, see [Using Structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="7a4de-113">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="7a4de-113">C# Language Specification</span></span>  
 <span data-ttu-id="7a4de-114">Örnekler için bkz [yapılar kullanarak](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="7a4de-114">For examples, see [Using Structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a4de-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7a4de-115">See Also</span></span>

- [<span data-ttu-id="7a4de-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="7a4de-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="7a4de-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7a4de-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="7a4de-118">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="7a4de-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="7a4de-119">Varsayılan Değerler Tablosu</span><span class="sxs-lookup"><span data-stu-id="7a4de-119">Default Values Table</span></span>](../../../csharp/language-reference/keywords/default-values-table.md)  
- [<span data-ttu-id="7a4de-120">Yerleşik Türler Tablosu</span><span class="sxs-lookup"><span data-stu-id="7a4de-120">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [<span data-ttu-id="7a4de-121">Türler</span><span class="sxs-lookup"><span data-stu-id="7a4de-121">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
- [<span data-ttu-id="7a4de-122">Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="7a4de-122">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
- [<span data-ttu-id="7a4de-123">class</span><span class="sxs-lookup"><span data-stu-id="7a4de-123">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
- [<span data-ttu-id="7a4de-124">interface</span><span class="sxs-lookup"><span data-stu-id="7a4de-124">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
- [<span data-ttu-id="7a4de-125">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="7a4de-125">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
