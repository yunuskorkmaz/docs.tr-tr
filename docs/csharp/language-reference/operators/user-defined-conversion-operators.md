---
title: Kullanıcı tanımlı dönüştürme operatörleri - C# başvurusu
description: Özel örtük ve açık tür dönüştürmelerinde tanımlamayı öğrenin C#.
ms.date: 07/09/2019
f1_keywords:
- explicit_CSharpKeyword
- implicit_CSharpKeyword
helpviewer_keywords:
- explicit keyword [C#]
- implicit keyword [C#]
- conversion operator [C#]
- user-defined conversion [C#]
ms.openlocfilehash: 5d1882048b2af12c29a3771055cbeba9565b7dab
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67788500"
---
# <a name="user-defined-conversion-operators-c-reference"></a><span data-ttu-id="5b679-103">Kullanıcı tanımlı dönüştürme işleçleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="5b679-103">User-defined conversion operators (C# reference)</span></span>

<span data-ttu-id="5b679-104">Kullanıcı tanımlı bir tür özel örtük veya açık dönüştürme ya da başka bir türe tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b679-104">A user-defined type can define a custom implicit or explicit conversion from or to another type.</span></span>

<span data-ttu-id="5b679-105">Örtük dönüştürmeleri çağrılacak özel sözdizimi gerektirmeyen ve bir çeşitli durumlarda, örneğin, atamalar ve yöntem çağrılarını içinde ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="5b679-105">Implicit conversions don't require special syntax to be invoked and can occur in a variety of situations, for example, in assignments and methods invocations.</span></span> <span data-ttu-id="5b679-106">Önceden tanımlanmış C# örtülü dönüştürmeler her zaman başarılı ve hiçbir zaman bir özel durum veya bilgileri kaybedersiniz.</span><span class="sxs-lookup"><span data-stu-id="5b679-106">Predefined C# implicit conversions always succeed and never throw an exception or lose information.</span></span> <span data-ttu-id="5b679-107">Kullanıcı tanımlı örtük dönüştürmeleri bu yolla çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="5b679-107">User-defined implicit conversions should behave in that way as well.</span></span> <span data-ttu-id="5b679-108">Özel bir dönüştürme bir özel durum veya bilgi kaybı, açık bir dönüştürme tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="5b679-108">If a custom conversion can throw an exception or lose information, define it as an explicit conversion.</span></span>

<span data-ttu-id="5b679-109">Kullanıcı tanımlı dönüştürmeler tarafından dikkate alınmaz [olduğu](type-testing-and-conversion-operators.md#is-operator) ve [olarak](type-testing-and-conversion-operators.md#as-operator) işleçleri.</span><span class="sxs-lookup"><span data-stu-id="5b679-109">User-defined conversions are not considered by the [is](type-testing-and-conversion-operators.md#is-operator) and [as](type-testing-and-conversion-operators.md#as-operator) operators.</span></span> <span data-ttu-id="5b679-110">Kullanım [atama işleci ()](type-testing-and-conversion-operators.md#cast-operator-) kullanıcı tanımlı açık dönüştürme çağırmak için.</span><span class="sxs-lookup"><span data-stu-id="5b679-110">Use the [cast operator ()](type-testing-and-conversion-operators.md#cast-operator-) to invoke a user-defined explicit conversion.</span></span>

<span data-ttu-id="5b679-111">Kullanım `operator` ve `implicit` veya `explicit` örtük veya açık bir dönüştürme sırasıyla tanımlamak için anahtar sözcükler.</span><span class="sxs-lookup"><span data-stu-id="5b679-111">Use the `operator` and `implicit` or `explicit` keywords to define an implicit or explicit conversion, respectively.</span></span> <span data-ttu-id="5b679-112">Bir dönüştürme tanımlayan türü kaynak türü veya bu dönüştürme hedef türünde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5b679-112">The type that defines a conversion must be either a source type or a target type of that conversion.</span></span> <span data-ttu-id="5b679-113">İki kullanıcı tanımlı türler arasında dönüştürme iki türlerinden birini tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="5b679-113">A conversion between two user-defined types can be defined in either of the two types.</span></span>

<span data-ttu-id="5b679-114">Aşağıdaki örnek, örtük ve açık bir dönüştürme tanımlamak gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="5b679-114">The following example demonstrates how to define an implicit and explicit conversion:</span></span>

[!code-csharp[implicit an explicit conversions](~/samples/csharp/language-reference/operators/UserDefinedConversions.cs)]

<span data-ttu-id="5b679-115">Ayrıca `operator` önceden tanımlanmış bir aşırı yüklemeyi anahtar sözcüğü C# işleci.</span><span class="sxs-lookup"><span data-stu-id="5b679-115">You also use the `operator` keyword to overload a predefined C# operator.</span></span> <span data-ttu-id="5b679-116">Daha fazla bilgi için [işleci aşırı yüklemesi](operator-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="5b679-116">For more information, see [Operator overloading](operator-overloading.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="5b679-117">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="5b679-117">C# language specification</span></span>

<span data-ttu-id="5b679-118">Daha fazla bilgi için aşağıdaki bölümlere bakın [ C# dil belirtimi](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="5b679-118">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="5b679-119">Dönüştürme işleçleri</span><span class="sxs-lookup"><span data-stu-id="5b679-119">Conversion operators</span></span>](~/_csharplang/spec/classes.md#conversion-operators)
- [<span data-ttu-id="5b679-120">Kullanıcı tanımlı dönüşümler</span><span class="sxs-lookup"><span data-stu-id="5b679-120">User-defined conversions</span></span>](~/_csharplang/spec/conversions.md#user-defined-conversions)
- [<span data-ttu-id="5b679-121">Örtük dönüşümler</span><span class="sxs-lookup"><span data-stu-id="5b679-121">Implicit conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-conversions)
- [<span data-ttu-id="5b679-122">Açık dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="5b679-122">Explicit conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-conversions)

## <a name="see-also"></a><span data-ttu-id="5b679-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b679-123">See also</span></span>

- [<span data-ttu-id="5b679-124">C#başvuru</span><span class="sxs-lookup"><span data-stu-id="5b679-124">C# reference</span></span>](../index.md)
- [<span data-ttu-id="5b679-125">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="5b679-125">C# operators</span></span>](index.md)
- [<span data-ttu-id="5b679-126">İşleç aşırı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="5b679-126">Operator overloading</span></span>](operator-overloading.md)
- [<span data-ttu-id="5b679-127">Tür test etme ve dönüştürme işleçleri</span><span class="sxs-lookup"><span data-stu-id="5b679-127">Type-testing and conversion operators</span></span>](type-testing-and-conversion-operators.md)
- [<span data-ttu-id="5b679-128">Atama ve tür dönüştürme</span><span class="sxs-lookup"><span data-stu-id="5b679-128">Casting and type conversion</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
- [<span data-ttu-id="5b679-129">Kullanıcı tanımlı C# ' de açık dönüştürmeler zincirleme</span><span class="sxs-lookup"><span data-stu-id="5b679-129">Chained user-defined explicit conversions in C#</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
