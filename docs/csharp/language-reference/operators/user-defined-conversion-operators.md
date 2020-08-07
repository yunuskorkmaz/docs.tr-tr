---
title: Kullanıcı tanımlı dönüştürme işleçleri-C# başvurusu
description: C# ' de özel örtük ve açık tür dönüştürmeleri tanımlama hakkında bilgi edinin.
ms.date: 07/09/2019
f1_keywords:
- explicit_CSharpKeyword
- implicit_CSharpKeyword
- explicit
- implicit
helpviewer_keywords:
- explicit keyword [C#]
- implicit keyword [C#]
- conversion operator [C#]
- user-defined conversion [C#]
ms.openlocfilehash: 70f553b129d5ef8a0f9077c16656a17d8e88fed4
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855848"
---
# <a name="user-defined-conversion-operators-c-reference"></a><span data-ttu-id="0cb8f-103">Kullanıcı tanımlı dönüştürme işleçleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="0cb8f-103">User-defined conversion operators (C# reference)</span></span>

<span data-ttu-id="0cb8f-104">Kullanıcı tanımlı bir tür, ya da başka bir türe özel örtük veya açık bir dönüştürme tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="0cb8f-104">A user-defined type can define a custom implicit or explicit conversion from or to another type.</span></span>

<span data-ttu-id="0cb8f-105">Örtük dönüştürmeler özel sözdiziminin çağrılmasını gerektirmez ve örneğin atamalar ve Yöntemler çağırmaları gibi çeşitli durumlarda gerçekleşebilir.</span><span class="sxs-lookup"><span data-stu-id="0cb8f-105">Implicit conversions don't require special syntax to be invoked and can occur in a variety of situations, for example, in assignments and methods invocations.</span></span> <span data-ttu-id="0cb8f-106">Önceden tanımlanmış C# örtük dönüştürmeleri her zaman başarılı olur ve hiçbir zaman özel durum oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="0cb8f-106">Predefined C# implicit conversions always succeed and never throw an exception.</span></span> <span data-ttu-id="0cb8f-107">Kullanıcı tanımlı örtük dönüştürmeler de bu şekilde davranmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0cb8f-107">User-defined implicit conversions should behave in that way as well.</span></span> <span data-ttu-id="0cb8f-108">Özel bir dönüştürme özel durum oluşturabilir veya bilgi kaybedebilir, onu açık bir dönüştürme olarak tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="0cb8f-108">If a custom conversion can throw an exception or lose information, define it as an explicit conversion.</span></span>

<span data-ttu-id="0cb8f-109">Kullanıcı tanımlı dönüştürmeler [, ve](type-testing-and-cast.md#is-operator) [gibi](type-testing-and-cast.md#as-operator) işleçler tarafından değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="0cb8f-109">User-defined conversions are not considered by the [is](type-testing-and-cast.md#is-operator) and [as](type-testing-and-cast.md#as-operator) operators.</span></span> <span data-ttu-id="0cb8f-110">Kullanıcı tanımlı açık dönüştürmeyi çağırmak için bir [atama ifadesi](type-testing-and-cast.md#cast-expression) kullanın.</span><span class="sxs-lookup"><span data-stu-id="0cb8f-110">Use a [cast expression](type-testing-and-cast.md#cast-expression) to invoke a user-defined explicit conversion.</span></span>

<span data-ttu-id="0cb8f-111">`operator` `implicit` `explicit` Sırasıyla örtük veya açık bir dönüştürme tanımlamak için ve veya anahtar sözcüklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0cb8f-111">Use the `operator` and `implicit` or `explicit` keywords to define an implicit or explicit conversion, respectively.</span></span> <span data-ttu-id="0cb8f-112">Bir dönüştürmeyi tanımlayan tür bir kaynak türü ya da bu dönüştürmenin hedef türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0cb8f-112">The type that defines a conversion must be either a source type or a target type of that conversion.</span></span> <span data-ttu-id="0cb8f-113">Kullanıcı tanımlı iki tür arasında dönüştürme iki türden birinde tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="0cb8f-113">A conversion between two user-defined types can be defined in either of the two types.</span></span>

<span data-ttu-id="0cb8f-114">Aşağıdaki örnek, örtük ve açık bir dönüştürmenin nasıl tanımlanacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="0cb8f-114">The following example demonstrates how to define an implicit and explicit conversion:</span></span>

[!code-csharp[implicit an explicit conversions](snippets/UserDefinedConversions.cs)]

<span data-ttu-id="0cb8f-115">Ayrıca, `operator` önceden tanımlanmış bir C# işlecini aşırı yüklemek için anahtar sözcüğünü de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0cb8f-115">You also use the `operator` keyword to overload a predefined C# operator.</span></span> <span data-ttu-id="0cb8f-116">Daha fazla bilgi için bkz. [operatör aşırı yüklemesi](operator-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="0cb8f-116">For more information, see [Operator overloading](operator-overloading.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0cb8f-117">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="0cb8f-117">C# language specification</span></span>

<span data-ttu-id="0cb8f-118">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="0cb8f-118">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="0cb8f-119">Dönüştürme işleçleri</span><span class="sxs-lookup"><span data-stu-id="0cb8f-119">Conversion operators</span></span>](~/_csharplang/spec/classes.md#conversion-operators)
- [<span data-ttu-id="0cb8f-120">Kullanıcı tanımlı dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="0cb8f-120">User-defined conversions</span></span>](~/_csharplang/spec/conversions.md#user-defined-conversions)
- [<span data-ttu-id="0cb8f-121">Örtük dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="0cb8f-121">Implicit conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-conversions)
- [<span data-ttu-id="0cb8f-122">Açık dönüşümler</span><span class="sxs-lookup"><span data-stu-id="0cb8f-122">Explicit conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-conversions)

## <a name="see-also"></a><span data-ttu-id="0cb8f-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0cb8f-123">See also</span></span>

- [<span data-ttu-id="0cb8f-124">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="0cb8f-124">C# reference</span></span>](../index.md)
- [<span data-ttu-id="0cb8f-125">C# işleçleri ve ifadeleri</span><span class="sxs-lookup"><span data-stu-id="0cb8f-125">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="0cb8f-126">İşleç aşırı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="0cb8f-126">Operator overloading</span></span>](operator-overloading.md)
- [<span data-ttu-id="0cb8f-127">Tür testi ve atama işleçleri</span><span class="sxs-lookup"><span data-stu-id="0cb8f-127">Type-testing and cast operators</span></span>](type-testing-and-cast.md)
- [<span data-ttu-id="0cb8f-128">Atama ve tür dönüştürme</span><span class="sxs-lookup"><span data-stu-id="0cb8f-128">Casting and type conversion</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
- [<span data-ttu-id="0cb8f-129">Tasarım yönergeleri-dönüştürme işleçleri</span><span class="sxs-lookup"><span data-stu-id="0cb8f-129">Design guidelines - Conversion operators</span></span>](../../../standard/design-guidelines/operator-overloads.md#conversion-operators)
- [<span data-ttu-id="0cb8f-130">C 'de Kullanıcı tanımlı açık dönüştürmeler zincirleme #</span><span class="sxs-lookup"><span data-stu-id="0cb8f-130">Chained user-defined explicit conversions in C#</span></span>](https://docs.microsoft.com/archive/blogs/ericlippert/chained-user-defined-explicit-conversions-in-c)
