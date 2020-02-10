---
title: struct- C# Reference
ms.date: 07/20/2015
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 77d5c83dd4c81b96bc62ace6e609db8bc411dc41
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093168"
---
# <a name="struct-c-reference"></a><span data-ttu-id="c8d51-102">struct (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c8d51-102">struct (C# Reference)</span></span>

<span data-ttu-id="c8d51-103">`struct` türü, genellikle bir dikdörtgenin koordinatları veya Stoktaki bir öğenin özellikleri gibi ilgili değişkenlerin küçük gruplarını kapsüllemek için kullanılan bir değer türüdür.</span><span class="sxs-lookup"><span data-stu-id="c8d51-103">A `struct` type is a value type that is typically used to encapsulate small groups of related variables, such as the coordinates of a rectangle or the characteristics of an item in an inventory.</span></span> <span data-ttu-id="c8d51-104">Aşağıdaki örnek, basit bir struct bildirimini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="c8d51-104">The following example shows a simple struct declaration:</span></span>

```csharp
public struct Book
{
    public decimal price;
    public string title;
    public string author;
}
```

## <a name="remarks"></a><span data-ttu-id="c8d51-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c8d51-105">Remarks</span></span>

<span data-ttu-id="c8d51-106">Yapılar ayrıca [oluşturucular](../../programming-guide/classes-and-structs/constructors.md), [sabitler](../../programming-guide/classes-and-structs/constants.md), [alanlar](../../programming-guide/classes-and-structs/fields.md), [Yöntemler](../../programming-guide/classes-and-structs/methods.md), [Özellikler](../../programming-guide/classes-and-structs/properties.md), [Dizin oluşturucular](../../programming-guide/indexers/index.md), [işleçler](../operators/index.md), [Olaylar](../../programming-guide/events/index.md)ve [iç içe türler](../../programming-guide/classes-and-structs/nested-types.md)içerebilir, ancak bu tür Üyeler gerekli olsa da, bu türden bir sınıf oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c8d51-106">Structs can also contain [constructors](../../programming-guide/classes-and-structs/constructors.md), [constants](../../programming-guide/classes-and-structs/constants.md), [fields](../../programming-guide/classes-and-structs/fields.md), [methods](../../programming-guide/classes-and-structs/methods.md), [properties](../../programming-guide/classes-and-structs/properties.md), [indexers](../../programming-guide/indexers/index.md), [operators](../operators/index.md), [events](../../programming-guide/events/index.md), and [nested types](../../programming-guide/classes-and-structs/nested-types.md), although if several such members are required, you should consider making your type a class instead.</span></span>

<span data-ttu-id="c8d51-107">Örnekler için bkz. [yapıları kullanma](../../programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="c8d51-107">For examples, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

<span data-ttu-id="c8d51-108">Yapılar bir arabirim uygulayabilir, ancak başka bir struct 'tan devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="c8d51-108">Structs can implement an interface but they cannot inherit from another struct.</span></span> <span data-ttu-id="c8d51-109">Bu nedenle, yapı üyeleri `protected`olarak bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="c8d51-109">For that reason, struct members cannot be declared as `protected`.</span></span>

<span data-ttu-id="c8d51-110">Daha fazla bilgi için bkz. [yapılar](../../programming-guide/classes-and-structs/structs.md).</span><span class="sxs-lookup"><span data-stu-id="c8d51-110">For more information, see [Structs](../../programming-guide/classes-and-structs/structs.md).</span></span>

## <a name="examples"></a><span data-ttu-id="c8d51-111">Örnekler</span><span class="sxs-lookup"><span data-stu-id="c8d51-111">Examples</span></span>

<span data-ttu-id="c8d51-112">Örnekler ve daha fazla bilgi için bkz. [yapıları kullanma](../../programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="c8d51-112">For examples and more information, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c8d51-113">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="c8d51-113">C# language specification</span></span>

<span data-ttu-id="c8d51-114">Örnekler için bkz. [yapıları kullanma](../../programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="c8d51-114">For examples, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c8d51-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8d51-115">See also</span></span>

- [<span data-ttu-id="c8d51-116">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="c8d51-116">C# reference</span></span>](../index.md)
- [<span data-ttu-id="c8d51-117">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="c8d51-117">C# keywords</span></span>](index.md)
- [<span data-ttu-id="c8d51-118">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="c8d51-118">Value types</span></span>](../builtin-types/value-types.md)
- [<span data-ttu-id="c8d51-119">class</span><span class="sxs-lookup"><span data-stu-id="c8d51-119">class</span></span>](class.md)
- [<span data-ttu-id="c8d51-120">interface</span><span class="sxs-lookup"><span data-stu-id="c8d51-120">interface</span></span>](interface.md)
- [<span data-ttu-id="c8d51-121">Sınıflar ve yapılar</span><span class="sxs-lookup"><span data-stu-id="c8d51-121">Classes and structs</span></span>](../../programming-guide/classes-and-structs/index.md)
