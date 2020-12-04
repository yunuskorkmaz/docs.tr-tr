---
description: "Değer türleri, türleri ve C 'de yerleşik olanlar hakkında bilgi edinin #"
title: Değer türleri-C# başvurusu
ms.date: 01/22/2020
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 64c9e9eba2495531cfef8a603d53fb21c95c87a4
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599401"
---
# <a name="value-types-c-reference"></a><span data-ttu-id="1d6e8-103">Değer türleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="1d6e8-103">Value types (C# reference)</span></span>

<span data-ttu-id="1d6e8-104">*Değer türleri* ve [başvuru türleri](../keywords/reference-types.md) , C# türlerinin iki ana kategorileridir.</span><span class="sxs-lookup"><span data-stu-id="1d6e8-104">*Value types* and [reference types](../keywords/reference-types.md) are the two main categories of C# types.</span></span> <span data-ttu-id="1d6e8-105">Değer türünde bir değişken türün bir örneğini içerir.</span><span class="sxs-lookup"><span data-stu-id="1d6e8-105">A variable of a value type contains an instance of the type.</span></span> <span data-ttu-id="1d6e8-106">Bu, bir tür örneğine başvuru içeren bir başvuru türü değişkeninden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="1d6e8-106">This differs from a variable of a reference type, which contains a reference to an instance of the type.</span></span> <span data-ttu-id="1d6e8-107">Varsayılan olarak, [atama](../operators/assignment-operator.md), bir yönteme bir bağımsız değişken geçirme ve bir yöntem sonucu döndürme, değişken değerleri kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="1d6e8-107">By default, on [assignment](../operators/assignment-operator.md), passing an argument to a method, and returning a method result, variable values are copied.</span></span> <span data-ttu-id="1d6e8-108">Değer türü değişkenler söz konusu olduğunda, karşılık gelen tür örnekleri kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="1d6e8-108">In the case of value-type variables, the corresponding type instances are copied.</span></span> <span data-ttu-id="1d6e8-109">Aşağıdaki örnekte bu davranış gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="1d6e8-109">The following example demonstrates that behavior:</span></span>

[!code-csharp[copy of values](snippets/shared/ValueTypes.cs#ValueTypeCopied)]

<span data-ttu-id="1d6e8-110">Yukarıdaki örnekte gösterildiği gibi, bir değer türü değişkeni üzerindeki işlemler, değişkende depolanan yalnızca değer türü örneğini etkiler.</span><span class="sxs-lookup"><span data-stu-id="1d6e8-110">As the preceding example shows, operations on a value-type variable affect only that instance of the value type, stored in the variable.</span></span>

<span data-ttu-id="1d6e8-111">Değer türü bir başvuru türünün veri üyesini içeriyorsa, bir değer türü örneği kopyalandığında yalnızca başvuru türü örneğine başvuru kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="1d6e8-111">If a value type contains a data member of a reference type, only the reference to the instance of the reference type is copied when a value-type instance is copied.</span></span> <span data-ttu-id="1d6e8-112">Hem Copy hem de orijinal değer türü örneğinin aynı başvuru türü örneğine erişimi vardır.</span><span class="sxs-lookup"><span data-stu-id="1d6e8-112">Both the copy and original value-type instance have access to the same reference-type instance.</span></span> <span data-ttu-id="1d6e8-113">Aşağıdaki örnekte bu davranış gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="1d6e8-113">The following example demonstrates that behavior:</span></span>

[!code-csharp[shallow copy](snippets/shared/ValueTypes.cs#ShallowCopy)]

> [!NOTE]
> <span data-ttu-id="1d6e8-114">Kodunuzu daha az hataya açık ve daha sağlam hale getirmek için, değişmez değer türlerini tanımlayın ve kullanın.</span><span class="sxs-lookup"><span data-stu-id="1d6e8-114">To make your code less error-prone and more robust, define and use immutable value types.</span></span> <span data-ttu-id="1d6e8-115">Bu makale yalnızca gösterim amacıyla kesilebilir değer türlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1d6e8-115">This article uses mutable value types only for demonstration purposes.</span></span>

## <a name="kinds-of-value-types-and-type-constraints"></a><span data-ttu-id="1d6e8-116">Değer türleri ve tür kısıtlamaları türleri</span><span class="sxs-lookup"><span data-stu-id="1d6e8-116">Kinds of value types and type constraints</span></span>

<span data-ttu-id="1d6e8-117">Değer türü aşağıdaki iki türden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="1d6e8-117">A value type can be one of the two following kinds:</span></span>

- <span data-ttu-id="1d6e8-118">veri ve ilgili işlevleri kapsülleyen bir [Yapı türü](struct.md)</span><span class="sxs-lookup"><span data-stu-id="1d6e8-118">a [structure type](struct.md), which encapsulates data and related functionality</span></span>
- <span data-ttu-id="1d6e8-119">bir adlandırılmış sabitler kümesi tarafından tanımlanan ve bir seçimi veya seçenek bileşimini temsil eden bir [numaralandırma türü](enum.md)</span><span class="sxs-lookup"><span data-stu-id="1d6e8-119">an [enumeration type](enum.md), which is defined by a set of named constants and represents a choice or a combination of choices</span></span>

<span data-ttu-id="1d6e8-120">[Null yapılabilir bir değer türü](nullable-value-types.md) , `T?` temel alınan değer türünün tüm değerlerini `T` ve ek bir [null](../keywords/null.md) değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1d6e8-120">A [nullable value type](nullable-value-types.md) `T?` represents all values of its underlying value type `T` and an additional [null](../keywords/null.md) value.</span></span> <span data-ttu-id="1d6e8-121">`null`Null atanabilir bir değer türü olmadığı takdirde, değer türünde bir değişkene atayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="1d6e8-121">You cannot assign `null` to a variable of a value type, unless it's a nullable value type.</span></span>

<span data-ttu-id="1d6e8-122">Bir tür parametresinin null yapılamayan bir değer türü olduğunu belirtmek için [ `struct` kısıtlamasını](../../programming-guide/generics/constraints-on-type-parameters.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d6e8-122">You can use the [`struct` constraint](../../programming-guide/generics/constraints-on-type-parameters.md) to specify that a type parameter is a non-nullable value type.</span></span> <span data-ttu-id="1d6e8-123">Hem yapı hem de numaralandırma türleri `struct` kısıtlamayı karşılar.</span><span class="sxs-lookup"><span data-stu-id="1d6e8-123">Both structure and enumeration types satisfy the `struct` constraint.</span></span> <span data-ttu-id="1d6e8-124">C# 7,3 ' den başlayarak, bir `System.Enum` tür parametresinin bir numaralandırma türü olduğunu belirtmek için bir temel sınıf kısıtlamasında ( [enum kısıtlaması](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)olarak bilinir) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d6e8-124">Beginning with C# 7.3, you can use `System.Enum` in a base class constraint (that is known as the [enum constraint](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)) to specify that a type parameter is an enumeration type.</span></span>

## <a name="built-in-value-types"></a><span data-ttu-id="1d6e8-125">Yerleşik değer türleri</span><span class="sxs-lookup"><span data-stu-id="1d6e8-125">Built-in value types</span></span>

<span data-ttu-id="1d6e8-126">C# *basit türler* olarak da bilinen aşağıdaki yerleşik değer türlerini sağlar:</span><span class="sxs-lookup"><span data-stu-id="1d6e8-126">C# provides the following built-in value types, also known as *simple types*:</span></span>

- [<span data-ttu-id="1d6e8-127">Tamsayı sayısal türler</span><span class="sxs-lookup"><span data-stu-id="1d6e8-127">Integral numeric types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="1d6e8-128">Kayan nokta sayısal türleri</span><span class="sxs-lookup"><span data-stu-id="1d6e8-128">Floating-point numeric types</span></span>](floating-point-numeric-types.md)
- <span data-ttu-id="1d6e8-129">Boole değeri temsil eden [bool](bool.md)</span><span class="sxs-lookup"><span data-stu-id="1d6e8-129">[bool](bool.md) that represents a Boolean value</span></span>
- <span data-ttu-id="1d6e8-130">Unicode UTF-16 karakterini temsil eden [karakter](char.md)</span><span class="sxs-lookup"><span data-stu-id="1d6e8-130">[char](char.md) that represents a Unicode UTF-16 character</span></span>

<span data-ttu-id="1d6e8-131">Tüm basit türler yapı türlerdir ve bazı ek işlemlere izin veren diğer yapı türlerinden farklıdır:</span><span class="sxs-lookup"><span data-stu-id="1d6e8-131">All simple types are structure types and differ from other structure types in that they permit certain additional operations:</span></span>

- <span data-ttu-id="1d6e8-132">Basit bir tür değeri sağlamak için sabit değerler kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d6e8-132">You can use literals to provide a value of a simple type.</span></span> <span data-ttu-id="1d6e8-133">Örneğin, `'A'` türünün bir sabit değeri `char` ve `2001` türünün bir sabit değeri `int` .</span><span class="sxs-lookup"><span data-stu-id="1d6e8-133">For example, `'A'` is a literal of the type `char` and `2001` is a literal of the type `int`.</span></span>

- <span data-ttu-id="1d6e8-134">[Const](../keywords/const.md) anahtar sözcüğüyle basit türlerin sabitlerini bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d6e8-134">You can declare constants of the simple types with the [const](../keywords/const.md) keyword.</span></span> <span data-ttu-id="1d6e8-135">Diğer yapı türlerinde sabitler olması mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="1d6e8-135">It's not possible to have constants of other structure types.</span></span>

- <span data-ttu-id="1d6e8-136">İşlenenleri basit türlerin tüm sabitleri olan sabit ifadeler, derleme zamanında değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="1d6e8-136">Constant expressions, whose operands are all constants of the simple types, are evaluated at compile time.</span></span>

<span data-ttu-id="1d6e8-137">C# 7,0 ' den başlayarak, c# [değer tanımlama gruplarını](value-tuples.md)destekler.</span><span class="sxs-lookup"><span data-stu-id="1d6e8-137">Beginning with C# 7.0, C# supports [value tuples](value-tuples.md).</span></span> <span data-ttu-id="1d6e8-138">Değer tanımlama grubu bir değer türüdür, ancak basit bir tür değildir.</span><span class="sxs-lookup"><span data-stu-id="1d6e8-138">A value tuple is a value type, but not a simple type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1d6e8-139">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="1d6e8-139">C# language specification</span></span>

<span data-ttu-id="1d6e8-140">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="1d6e8-140">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="1d6e8-141">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="1d6e8-141">Value types</span></span>](~/_csharplang/spec/types.md#value-types)
- [<span data-ttu-id="1d6e8-142">Basit türler</span><span class="sxs-lookup"><span data-stu-id="1d6e8-142">Simple types</span></span>](~/_csharplang/spec/types.md#simple-types)
- [<span data-ttu-id="1d6e8-143">Değişkenler</span><span class="sxs-lookup"><span data-stu-id="1d6e8-143">Variables</span></span>](~/_csharplang/spec/variables.md)

## <a name="see-also"></a><span data-ttu-id="1d6e8-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d6e8-144">See also</span></span>

- [<span data-ttu-id="1d6e8-145">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="1d6e8-145">C# reference</span></span>](../index.md)
- <xref:System.ValueType?displayProperty=nameWithType>
- [<span data-ttu-id="1d6e8-146">Başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="1d6e8-146">Reference types</span></span>](../keywords/reference-types.md)
