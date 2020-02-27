---
title: Değer türleri- C# başvuru
ms.date: 01/22/2020
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 76f4a3ed929e3ac8e3e6cc74158e75af7a6c8cf2
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77625953"
---
# <a name="value-types-c-reference"></a><span data-ttu-id="4c2d9-102">Değer türleri (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="4c2d9-102">Value types (C# reference)</span></span>

<span data-ttu-id="4c2d9-103">*Değer türleri* ve [başvuru türleri](../keywords/reference-types.md) , C# türlerin iki ana kategorileridir.</span><span class="sxs-lookup"><span data-stu-id="4c2d9-103">*Value types* and [reference types](../keywords/reference-types.md) are the two main categories of C# types.</span></span> <span data-ttu-id="4c2d9-104">Değer türünde bir değişken türün bir örneğini içerir.</span><span class="sxs-lookup"><span data-stu-id="4c2d9-104">A variable of a value type contains an instance of the type.</span></span> <span data-ttu-id="4c2d9-105">Bu, bir tür örneğine başvuru içeren bir başvuru türü değişkeninden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="4c2d9-105">This differs from a variable of a reference type, which contains a reference to an instance of the type.</span></span> <span data-ttu-id="4c2d9-106">Varsayılan olarak, [atama](../operators/assignment-operator.md), bir yönteme bir bağımsız değişken geçirme ve bir yöntem sonucu döndürme, değişken değerleri kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="4c2d9-106">By default, on [assignment](../operators/assignment-operator.md), passing an argument to a method, and returning a method result, variable values are copied.</span></span> <span data-ttu-id="4c2d9-107">Değer türü değişkenler söz konusu olduğunda, karşılık gelen tür örnekleri kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="4c2d9-107">In the case of value-type variables, the corresponding type instances are copied.</span></span> <span data-ttu-id="4c2d9-108">Aşağıdaki örnekte bu davranış gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="4c2d9-108">The following example demonstrates that behavior:</span></span>

[!code-csharp[copy of values](~/samples/csharp/language-reference/builtin-types/ValueTypes.cs#ValueTypeCopied)]

<span data-ttu-id="4c2d9-109">Yukarıdaki örnekte gösterildiği gibi, bir değer türü değişkeni üzerindeki işlemler, değişkende depolanan yalnızca değer türü örneğini etkiler.</span><span class="sxs-lookup"><span data-stu-id="4c2d9-109">As the preceding example shows, operations on a value-type variable affect only that instance of the value type, stored in the variable.</span></span>

<span data-ttu-id="4c2d9-110">Değer türü bir başvuru türünün veri üyesini içeriyorsa, bir değer türü örneği kopyalandığında yalnızca başvuru türü örneğine başvuru kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="4c2d9-110">If a value type contains a data member of a reference type, only the reference to the instance of the reference type is copied when a value-type instance is copied.</span></span> <span data-ttu-id="4c2d9-111">Hem Copy hem de orijinal değer türü örneğinin aynı başvuru türü örneğine erişimi vardır.</span><span class="sxs-lookup"><span data-stu-id="4c2d9-111">Both the copy and original value-type instance have access to the same reference-type instance.</span></span> <span data-ttu-id="4c2d9-112">Aşağıdaki örnekte bu davranış gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="4c2d9-112">The following example demonstrates that behavior:</span></span>

[!code-csharp[shallow copy](~/samples/csharp/language-reference/builtin-types/ValueTypes.cs#ShallowCopy)]

> [!NOTE]
> <span data-ttu-id="4c2d9-113">Kodunuzu daha az hataya açık ve daha sağlam hale getirmek için, değişmez değer türlerini tanımlayın ve kullanın.</span><span class="sxs-lookup"><span data-stu-id="4c2d9-113">To make your code less error-prone and more robust, define and use immutable value types.</span></span> <span data-ttu-id="4c2d9-114">Bu makale yalnızca gösterim amacıyla kesilebilir değer türlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="4c2d9-114">This article uses mutable value types only for demonstration purposes.</span></span>

## <a name="kinds-of-value-types"></a><span data-ttu-id="4c2d9-115">Değer türü türleri</span><span class="sxs-lookup"><span data-stu-id="4c2d9-115">Kinds of value types</span></span>

<span data-ttu-id="4c2d9-116">Değer türü aşağıdaki iki türden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="4c2d9-116">A value type can be one of the two following kinds:</span></span>

- <span data-ttu-id="4c2d9-117">veri ve ilgili işlevleri kapsülleyen bir [Yapı türü](struct.md)</span><span class="sxs-lookup"><span data-stu-id="4c2d9-117">a [structure type](struct.md), which encapsulates data and related functionality</span></span>
- <span data-ttu-id="4c2d9-118">bir adlandırılmış sabitler kümesi tarafından tanımlanan ve bir seçimi veya seçenek bileşimini temsil eden bir [numaralandırma türü](enum.md)</span><span class="sxs-lookup"><span data-stu-id="4c2d9-118">an [enumeration type](enum.md), which is defined by a set of named constants and represents a choice or a combination of choices</span></span>

<span data-ttu-id="4c2d9-119">[Null olabilen bir değer türü](nullable-value-types.md) `T?` temel alınan değer `T` türünün tüm değerlerini ve ek bir [null](../keywords/null.md) değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4c2d9-119">A [nullable value type](nullable-value-types.md) `T?` represents all values of its underlying value type `T` and an additional [null](../keywords/null.md) value.</span></span> <span data-ttu-id="4c2d9-120">Null atanabilir bir değer türü olmadığı takdirde, değer türü değişkenine `null` atayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="4c2d9-120">You cannot assign `null` to a variable of a value type, unless it's a nullable value type.</span></span>

## <a name="built-in-value-types"></a><span data-ttu-id="4c2d9-121">Yerleşik değer türleri</span><span class="sxs-lookup"><span data-stu-id="4c2d9-121">Built-in value types</span></span>

<span data-ttu-id="4c2d9-122">C#, *basit türler*olarak da bilinen aşağıdaki yerleşik değer türlerini sağlar:</span><span class="sxs-lookup"><span data-stu-id="4c2d9-122">C# provides the following built-in value types, also known as *simple types*:</span></span>

- [<span data-ttu-id="4c2d9-123">Integral sayısal türleri</span><span class="sxs-lookup"><span data-stu-id="4c2d9-123">Integral numeric types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="4c2d9-124">Kayan nokta sayısal türleri</span><span class="sxs-lookup"><span data-stu-id="4c2d9-124">Floating-point numeric types</span></span>](floating-point-numeric-types.md)
- <span data-ttu-id="4c2d9-125">Boole değeri temsil eden [bool](bool.md)</span><span class="sxs-lookup"><span data-stu-id="4c2d9-125">[bool](bool.md) that represents a Boolean value</span></span>
- <span data-ttu-id="4c2d9-126">Unicode UTF-16 karakterini temsil eden [karakter](char.md)</span><span class="sxs-lookup"><span data-stu-id="4c2d9-126">[char](char.md) that represents a Unicode UTF-16 character</span></span>

<span data-ttu-id="4c2d9-127">Tüm basit türler yapı türlerdir ve bazı ek işlemlere izin veren diğer yapı türlerinden farklıdır:</span><span class="sxs-lookup"><span data-stu-id="4c2d9-127">All simple types are structure types and differ from other structure types in that they permit certain additional operations:</span></span>

- <span data-ttu-id="4c2d9-128">Basit bir tür değeri sağlamak için sabit değerler kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c2d9-128">You can use literals to provide a value of a simple type.</span></span> <span data-ttu-id="4c2d9-129">Örneğin, `'A'` türü `char` bir değişmez değerdir ve `2001` `int`türü bir değişmez değerdir.</span><span class="sxs-lookup"><span data-stu-id="4c2d9-129">For example, `'A'` is a literal of the type `char` and `2001` is a literal of the type `int`.</span></span>

- <span data-ttu-id="4c2d9-130">[Const](../keywords/const.md) anahtar sözcüğüyle basit türlerin sabitlerini bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c2d9-130">You can declare constants of the simple types with the [const](../keywords/const.md) keyword.</span></span> <span data-ttu-id="4c2d9-131">Diğer yapı türlerinde sabitler olması mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="4c2d9-131">It's not possible to have constants of other structure types.</span></span>

- <span data-ttu-id="4c2d9-132">İşlenenleri basit türlerin tüm sabitleri olan sabit ifadeler, derleme zamanında değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="4c2d9-132">Constant expressions, whose operands are all constants of the simple types, are evaluated at compile time.</span></span>

<span data-ttu-id="4c2d9-133">7,0 ' C# C# den başlayarak [değer tanımlama gruplarını](../../tuples.md)destekler.</span><span class="sxs-lookup"><span data-stu-id="4c2d9-133">Beginning with C# 7.0, C# supports [value tuples](../../tuples.md).</span></span> <span data-ttu-id="4c2d9-134">Değer tanımlama grubu bir değer türüdür, ancak basit bir tür değildir.</span><span class="sxs-lookup"><span data-stu-id="4c2d9-134">A value tuple is a value type, but not a simple type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4c2d9-135">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="4c2d9-135">C# language specification</span></span>

<span data-ttu-id="4c2d9-136">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="4c2d9-136">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="4c2d9-137">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="4c2d9-137">Value types</span></span>](~/_csharplang/spec/types.md#value-types)
- [<span data-ttu-id="4c2d9-138">Basit türler</span><span class="sxs-lookup"><span data-stu-id="4c2d9-138">Simple types</span></span>](~/_csharplang/spec/types.md#simple-types)
- [<span data-ttu-id="4c2d9-139">Değişkenler</span><span class="sxs-lookup"><span data-stu-id="4c2d9-139">Variables</span></span>](~/_csharplang/spec/variables.md)

## <a name="see-also"></a><span data-ttu-id="4c2d9-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c2d9-140">See also</span></span>

- [<span data-ttu-id="4c2d9-141">C#başvurunun</span><span class="sxs-lookup"><span data-stu-id="4c2d9-141">C# reference</span></span>](../index.md)
- <xref:System.ValueType?displayProperty=nameWithType>
- [<span data-ttu-id="4c2d9-142">Başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="4c2d9-142">Reference types</span></span>](../keywords/reference-types.md)
