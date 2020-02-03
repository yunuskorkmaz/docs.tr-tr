---
title: struct- C# Reference
ms.date: 07/20/2015
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 8d9a23a0813423571c894758257b284ad67a72e2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744651"
---
# <a name="struct-c-reference"></a><span data-ttu-id="03d6c-102">struct (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="03d6c-102">struct (C# Reference)</span></span>

<span data-ttu-id="03d6c-103">`struct` türü, genellikle bir dikdörtgenin koordinatları veya Stoktaki bir öğenin özellikleri gibi ilgili değişkenlerin küçük gruplarını kapsüllemek için kullanılan bir değer türüdür.</span><span class="sxs-lookup"><span data-stu-id="03d6c-103">A `struct` type is a value type that is typically used to encapsulate small groups of related variables, such as the coordinates of a rectangle or the characteristics of an item in an inventory.</span></span> <span data-ttu-id="03d6c-104">Aşağıdaki örnek, basit bir struct bildirimini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="03d6c-104">The following example shows a simple struct declaration:</span></span>

```csharp
public struct Book
{
    public decimal price;
    public string title;
    public string author;
}
```

## <a name="remarks"></a><span data-ttu-id="03d6c-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="03d6c-105">Remarks</span></span>

<span data-ttu-id="03d6c-106">Yapılar ayrıca [oluşturucular](../../programming-guide/classes-and-structs/constructors.md), [sabitler](../../programming-guide/classes-and-structs/constants.md), [alanlar](../../programming-guide/classes-and-structs/fields.md), [Yöntemler](../../programming-guide/classes-and-structs/methods.md), [Özellikler](../../programming-guide/classes-and-structs/properties.md), [Dizin oluşturucular](../../programming-guide/indexers/index.md), [işleçler](../operators/index.md), [Olaylar](../../programming-guide/events/index.md)ve [iç içe türler](../../programming-guide/classes-and-structs/nested-types.md)içerebilir, ancak bu tür Üyeler gerekli olsa da, bu türden bir sınıf oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="03d6c-106">Structs can also contain [constructors](../../programming-guide/classes-and-structs/constructors.md), [constants](../../programming-guide/classes-and-structs/constants.md), [fields](../../programming-guide/classes-and-structs/fields.md), [methods](../../programming-guide/classes-and-structs/methods.md), [properties](../../programming-guide/classes-and-structs/properties.md), [indexers](../../programming-guide/indexers/index.md), [operators](../operators/index.md), [events](../../programming-guide/events/index.md), and [nested types](../../programming-guide/classes-and-structs/nested-types.md), although if several such members are required, you should consider making your type a class instead.</span></span>

<span data-ttu-id="03d6c-107">Örnekler için bkz. [yapıları kullanma](../../programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="03d6c-107">For examples, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

<span data-ttu-id="03d6c-108">Yapılar bir arabirim uygulayabilir, ancak başka bir struct 'tan devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="03d6c-108">Structs can implement an interface but they cannot inherit from another struct.</span></span> <span data-ttu-id="03d6c-109">Bu nedenle, yapı üyeleri `protected`olarak bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="03d6c-109">For that reason, struct members cannot be declared as `protected`.</span></span>

<span data-ttu-id="03d6c-110">Daha fazla bilgi için bkz. [yapılar](../../programming-guide/classes-and-structs/structs.md).</span><span class="sxs-lookup"><span data-stu-id="03d6c-110">For more information, see [Structs](../../programming-guide/classes-and-structs/structs.md).</span></span>

## <a name="examples"></a><span data-ttu-id="03d6c-111">Örnekler</span><span class="sxs-lookup"><span data-stu-id="03d6c-111">Examples</span></span>

<span data-ttu-id="03d6c-112">Örnekler ve daha fazla bilgi için bkz. [yapıları kullanma](../../programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="03d6c-112">For examples and more information, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="03d6c-113">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="03d6c-113">C# language specification</span></span>

<span data-ttu-id="03d6c-114">Örnekler için bkz. [yapıları kullanma](../../programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="03d6c-114">For examples, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="03d6c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03d6c-115">See also</span></span>

- [<span data-ttu-id="03d6c-116">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="03d6c-116">C# reference</span></span>](../index.md)
- [<span data-ttu-id="03d6c-117">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="03d6c-117">C# keywords</span></span>](index.md)
- [<span data-ttu-id="03d6c-118">Yerleşik türler tablosu</span><span class="sxs-lookup"><span data-stu-id="03d6c-118">Built-in types table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="03d6c-119">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="03d6c-119">Value types</span></span>](../builtin-types/value-types.md)
- [<span data-ttu-id="03d6c-120">class</span><span class="sxs-lookup"><span data-stu-id="03d6c-120">class</span></span>](class.md)
- [<span data-ttu-id="03d6c-121">interface</span><span class="sxs-lookup"><span data-stu-id="03d6c-121">interface</span></span>](interface.md)
- [<span data-ttu-id="03d6c-122">Sınıflar ve yapılar</span><span class="sxs-lookup"><span data-stu-id="03d6c-122">Classes and structs</span></span>](../../programming-guide/classes-and-structs/index.md)
