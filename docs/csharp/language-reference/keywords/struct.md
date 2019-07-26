---
title: struct- C# Reference
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 1f1c512e1995df07fc4b9e18e34a85119e270bda
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433778"
---
# <a name="struct-c-reference"></a><span data-ttu-id="463ef-102">struct (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="463ef-102">struct (C# Reference)</span></span>

<span data-ttu-id="463ef-103">`struct` Tür, genellikle bir dikdörtgenin koordinatları veya Stoktaki bir öğenin özellikleri gibi ilgili değişkenlerin küçük gruplarını kapsüllemek için kullanılan bir değer türüdür.</span><span class="sxs-lookup"><span data-stu-id="463ef-103">A `struct` type is a value type that is typically used to encapsulate small groups of related variables, such as the coordinates of a rectangle or the characteristics of an item in an inventory.</span></span> <span data-ttu-id="463ef-104">Aşağıdaki örnek, basit bir struct bildirimini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="463ef-104">The following example shows a simple struct declaration:</span></span>

```csharp
public struct Book
{
    public decimal price;
    public string title;
    public string author;
}
```

## <a name="remarks"></a><span data-ttu-id="463ef-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="463ef-105">Remarks</span></span>

<span data-ttu-id="463ef-106">Yapılar, birçok üye olsa da, [oluşturucular](../../programming-guide/classes-and-structs/constructors.md), [sabitler](../../programming-guide/classes-and-structs/constants.md), [alanlar](../../programming-guide/classes-and-structs/fields.md), [Yöntemler](../../programming-guide/classes-and-structs/methods.md), [Özellikler](../../programming-guide/classes-and-structs/properties.md), [Dizin oluşturucular](../../programming-guide/indexers/index.md), [işleçler](../../programming-guide/statements-expressions-operators/operators.md), [Olaylar](../../programming-guide/events/index.md)ve [iç içe türler](../../programming-guide/classes-and-structs/nested-types.md)içerebilir. gerekli, bunun yerine bir sınıf yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="463ef-106">Structs can also contain [constructors](../../programming-guide/classes-and-structs/constructors.md), [constants](../../programming-guide/classes-and-structs/constants.md), [fields](../../programming-guide/classes-and-structs/fields.md), [methods](../../programming-guide/classes-and-structs/methods.md), [properties](../../programming-guide/classes-and-structs/properties.md), [indexers](../../programming-guide/indexers/index.md), [operators](../../programming-guide/statements-expressions-operators/operators.md), [events](../../programming-guide/events/index.md), and [nested types](../../programming-guide/classes-and-structs/nested-types.md), although if several such members are required, you should consider making your type a class instead.</span></span>

<span data-ttu-id="463ef-107">Örnekler için bkz. [yapıları kullanma](../../programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="463ef-107">For examples, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

<span data-ttu-id="463ef-108">Yapılar bir arabirim uygulayabilir, ancak başka bir struct 'tan devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="463ef-108">Structs can implement an interface but they cannot inherit from another struct.</span></span> <span data-ttu-id="463ef-109">Bu nedenle, yapı üyeleri olarak `protected`bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="463ef-109">For that reason, struct members cannot be declared as `protected`.</span></span>

<span data-ttu-id="463ef-110">Daha fazla bilgi için bkz. [yapılar](../../programming-guide/classes-and-structs/structs.md).</span><span class="sxs-lookup"><span data-stu-id="463ef-110">For more information, see [Structs](../../programming-guide/classes-and-structs/structs.md).</span></span>

## <a name="examples"></a><span data-ttu-id="463ef-111">Örnekler</span><span class="sxs-lookup"><span data-stu-id="463ef-111">Examples</span></span>

<span data-ttu-id="463ef-112">Örnekler ve daha fazla bilgi için bkz. [yapıları kullanma](../../programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="463ef-112">For examples and more information, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="463ef-113">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="463ef-113">C# language specification</span></span>

<span data-ttu-id="463ef-114">Örnekler için bkz. [yapıları kullanma](../../programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="463ef-114">For examples, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="463ef-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="463ef-115">See also</span></span>

- [<span data-ttu-id="463ef-116">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="463ef-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="463ef-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="463ef-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="463ef-118">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="463ef-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="463ef-119">Varsayılan Değerler Tablosu</span><span class="sxs-lookup"><span data-stu-id="463ef-119">Default Values Table</span></span>](default-values-table.md)
- [<span data-ttu-id="463ef-120">Yerleşik Türler Tablosu</span><span class="sxs-lookup"><span data-stu-id="463ef-120">Built-In Types Table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="463ef-121">Türler</span><span class="sxs-lookup"><span data-stu-id="463ef-121">Types</span></span>](types.md)
- [<span data-ttu-id="463ef-122">Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="463ef-122">Value Types</span></span>](value-types.md)
- [<span data-ttu-id="463ef-123">class</span><span class="sxs-lookup"><span data-stu-id="463ef-123">class</span></span>](class.md)
- [<span data-ttu-id="463ef-124">interface</span><span class="sxs-lookup"><span data-stu-id="463ef-124">interface</span></span>](interface.md)
- [<span data-ttu-id="463ef-125">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="463ef-125">Classes and Structs</span></span>](../../programming-guide/classes-and-structs/index.md)
