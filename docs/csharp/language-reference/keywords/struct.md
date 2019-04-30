---
title: Yapı - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 2d0cba75e067e4d75ca5b544a664d7dede153c73
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660625"
---
# <a name="struct-c-reference"></a><span data-ttu-id="5fb65-102">struct (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="5fb65-102">struct (C# Reference)</span></span>

<span data-ttu-id="5fb65-103">A `struct` türü, genelde küçük bir dikdörtgen koordinatlarını veya bir öğe bir stok özelliklerini gibi ilişkili değişken grupları kapsüllemek için kullanılan bir değer türüdür.</span><span class="sxs-lookup"><span data-stu-id="5fb65-103">A `struct` type is a value type that is typically used to encapsulate small groups of related variables, such as the coordinates of a rectangle or the characteristics of an item in an inventory.</span></span> <span data-ttu-id="5fb65-104">Aşağıdaki örnek, bir basit yapı bildirimi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="5fb65-104">The following example shows a simple struct declaration:</span></span>

```csharp
public struct Book
{
    public decimal price;
    public string title;
    public string author;
}
```

## <a name="remarks"></a><span data-ttu-id="5fb65-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5fb65-105">Remarks</span></span>

<span data-ttu-id="5fb65-106">Yapılar içerebilir [oluşturucular](../../programming-guide/classes-and-structs/constructors.md), [sabitleri](../../programming-guide/classes-and-structs/constants.md), [alanları](../../programming-guide/classes-and-structs/fields.md), [yöntemleri](../../programming-guide/classes-and-structs/methods.md), [özellikleri](../../programming-guide/classes-and-structs/properties.md), [dizin oluşturucular](../../programming-guide/indexers/index.md), [işleçleri](../../programming-guide/statements-expressions-operators/operators.md), [olayları](../../programming-guide/events/index.md), ve [türlerin](../../programming-guide/classes-and-structs/nested-types.md), ancak birçok üye gerekliyse, türünüz bunun yerine bir sınıf yapma dikkate almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5fb65-106">Structs can also contain [constructors](../../programming-guide/classes-and-structs/constructors.md), [constants](../../programming-guide/classes-and-structs/constants.md), [fields](../../programming-guide/classes-and-structs/fields.md), [methods](../../programming-guide/classes-and-structs/methods.md), [properties](../../programming-guide/classes-and-structs/properties.md), [indexers](../../programming-guide/indexers/index.md), [operators](../../programming-guide/statements-expressions-operators/operators.md), [events](../../programming-guide/events/index.md), and [nested types](../../programming-guide/classes-and-structs/nested-types.md), although if several such members are required, you should consider making your type a class instead.</span></span>

<span data-ttu-id="5fb65-107">Örnekler için bkz [yapılar kullanarak](../../programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="5fb65-107">For examples, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

<span data-ttu-id="5fb65-108">Yapı birimleri arabirim uygulayabilir, ancak bunlar başka bir yapı devralamaz.</span><span class="sxs-lookup"><span data-stu-id="5fb65-108">Structs can implement an interface but they cannot inherit from another struct.</span></span> <span data-ttu-id="5fb65-109">Bu nedenle, Yapı üyeleri olarak bildirilemez `protected`.</span><span class="sxs-lookup"><span data-stu-id="5fb65-109">For that reason, struct members cannot be declared as `protected`.</span></span>

<span data-ttu-id="5fb65-110">Daha fazla bilgi için [yapılar](../../programming-guide/classes-and-structs/structs.md).</span><span class="sxs-lookup"><span data-stu-id="5fb65-110">For more information, see [Structs](../../programming-guide/classes-and-structs/structs.md).</span></span>

## <a name="examples"></a><span data-ttu-id="5fb65-111">Örnekler</span><span class="sxs-lookup"><span data-stu-id="5fb65-111">Examples</span></span>

<span data-ttu-id="5fb65-112">Örnekler ve daha fazla bilgi için bkz. [yapılar kullanarak](../../programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="5fb65-112">For examples and more information, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="5fb65-113">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="5fb65-113">C# language specification</span></span>

<span data-ttu-id="5fb65-114">Örnekler için bkz [yapılar kullanarak](../../programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="5fb65-114">For examples, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5fb65-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5fb65-115">See also</span></span>

- [<span data-ttu-id="5fb65-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="5fb65-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="5fb65-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5fb65-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="5fb65-118">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="5fb65-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="5fb65-119">Varsayılan Değerler Tablosu</span><span class="sxs-lookup"><span data-stu-id="5fb65-119">Default Values Table</span></span>](default-values-table.md)
- [<span data-ttu-id="5fb65-120">Yerleşik Türler Tablosu</span><span class="sxs-lookup"><span data-stu-id="5fb65-120">Built-In Types Table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="5fb65-121">Türler</span><span class="sxs-lookup"><span data-stu-id="5fb65-121">Types</span></span>](types.md)
- [<span data-ttu-id="5fb65-122">Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="5fb65-122">Value Types</span></span>](value-types.md)
- [<span data-ttu-id="5fb65-123">class</span><span class="sxs-lookup"><span data-stu-id="5fb65-123">class</span></span>](class.md)
- [<span data-ttu-id="5fb65-124">interface</span><span class="sxs-lookup"><span data-stu-id="5fb65-124">interface</span></span>](interface.md)
- [<span data-ttu-id="5fb65-125">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="5fb65-125">Classes and Structs</span></span>](../../programming-guide/classes-and-structs/index.md)