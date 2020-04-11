---
title: Kullanıcı tanımlı dönüşüm işleçleri - C# başvurusu
description: C#'da özel örtük ve açık tür dönüşümlerini nasıl tanımlayın öğrenin.
ms.date: 07/09/2019
f1_keywords:
- explicit_CSharpKeyword
- implicit_CSharpKeyword
helpviewer_keywords:
- explicit keyword [C#]
- implicit keyword [C#]
- conversion operator [C#]
- user-defined conversion [C#]
ms.openlocfilehash: b59fc27be31f1a38e2a6c3cabd82598933b5ed53
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121398"
---
# <a name="user-defined-conversion-operators-c-reference"></a><span data-ttu-id="2c15a-103">Kullanıcı tanımlı dönüşüm işleçleri (C# başvurusu)</span><span class="sxs-lookup"><span data-stu-id="2c15a-103">User-defined conversion operators (C# reference)</span></span>

<span data-ttu-id="2c15a-104">Kullanıcı tanımlı bir tür, başka bir türe özel örtük veya açık bir dönüştürme tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="2c15a-104">A user-defined type can define a custom implicit or explicit conversion from or to another type.</span></span>

<span data-ttu-id="2c15a-105">Örtük dönüşümler çağrılması için özel sözdizimi gerektirmez ve atamalar ve yöntem çağrıları gibi çeşitli durumlarda oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="2c15a-105">Implicit conversions don't require special syntax to be invoked and can occur in a variety of situations, for example, in assignments and methods invocations.</span></span> <span data-ttu-id="2c15a-106">Önceden tanımlanmış C# örtük dönüşümleri her zaman başarılı olur ve hiçbir zaman bir özel durum atmaz.</span><span class="sxs-lookup"><span data-stu-id="2c15a-106">Predefined C# implicit conversions always succeed and never throw an exception.</span></span> <span data-ttu-id="2c15a-107">Kullanıcı tanımlı örtük dönüşümler de bu şekilde kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2c15a-107">User-defined implicit conversions should behave in that way as well.</span></span> <span data-ttu-id="2c15a-108">Özel bir dönüştürme bir özel durum atabiliyor veya bilgi kaybedebilirse, bunu açık bir dönüştürme olarak tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="2c15a-108">If a custom conversion can throw an exception or lose information, define it as an explicit conversion.</span></span>

<span data-ttu-id="2c15a-109">Kullanıcı tanımlı [dönüşümler, is](type-testing-and-cast.md#is-operator) ve [operatörler tarafından](type-testing-and-cast.md#as-operator) dikkate alınmaz.</span><span class="sxs-lookup"><span data-stu-id="2c15a-109">User-defined conversions are not considered by the [is](type-testing-and-cast.md#is-operator) and [as](type-testing-and-cast.md#as-operator) operators.</span></span> <span data-ttu-id="2c15a-110">Kullanıcı tanımlı açık dönüştürme çağırmak için [döküm ifadesini](type-testing-and-cast.md#cast-expression) kullanın.</span><span class="sxs-lookup"><span data-stu-id="2c15a-110">Use a [cast expression](type-testing-and-cast.md#cast-expression) to invoke a user-defined explicit conversion.</span></span>

<span data-ttu-id="2c15a-111">Örtük `operator` `implicit` veya `explicit` açık bir dönüştürmeyi tanımlamak için anahtar kelimeleri ve veya anahtar kelimeleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="2c15a-111">Use the `operator` and `implicit` or `explicit` keywords to define an implicit or explicit conversion, respectively.</span></span> <span data-ttu-id="2c15a-112">Dönüştürmeyi tanımlayan tür, kaynak türü veya bu dönüşümün hedef türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2c15a-112">The type that defines a conversion must be either a source type or a target type of that conversion.</span></span> <span data-ttu-id="2c15a-113">İki kullanıcı tanımlı tür arasında bir dönüşüm iki türden birinde tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="2c15a-113">A conversion between two user-defined types can be defined in either of the two types.</span></span>

<span data-ttu-id="2c15a-114">Aşağıdaki örnek, örtük ve açık bir dönüştürmenin nasıl tanımlanabildiğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="2c15a-114">The following example demonstrates how to define an implicit and explicit conversion:</span></span>

[!code-csharp[implicit an explicit conversions](snippets/UserDefinedConversions.cs)]

<span data-ttu-id="2c15a-115">Önceden tanımlanmış `operator` bir C# işlecinin aşırı yüklenmesi için de anahtar kelime yi kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="2c15a-115">You also use the `operator` keyword to overload a predefined C# operator.</span></span> <span data-ttu-id="2c15a-116">Daha fazla bilgi için operatör [aşırı yüklemesi'ne](operator-overloading.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="2c15a-116">For more information, see [Operator overloading](operator-overloading.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="2c15a-117">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="2c15a-117">C# language specification</span></span>

<span data-ttu-id="2c15a-118">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:</span><span class="sxs-lookup"><span data-stu-id="2c15a-118">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="2c15a-119">Dönüşüm operatörleri</span><span class="sxs-lookup"><span data-stu-id="2c15a-119">Conversion operators</span></span>](~/_csharplang/spec/classes.md#conversion-operators)
- [<span data-ttu-id="2c15a-120">Kullanıcı tanımlı dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="2c15a-120">User-defined conversions</span></span>](~/_csharplang/spec/conversions.md#user-defined-conversions)
- [<span data-ttu-id="2c15a-121">Örtülü dönüşümler</span><span class="sxs-lookup"><span data-stu-id="2c15a-121">Implicit conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-conversions)
- [<span data-ttu-id="2c15a-122">Açık dönüşümler</span><span class="sxs-lookup"><span data-stu-id="2c15a-122">Explicit conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-conversions)

## <a name="see-also"></a><span data-ttu-id="2c15a-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c15a-123">See also</span></span>

- [<span data-ttu-id="2c15a-124">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="2c15a-124">C# reference</span></span>](../index.md)
- [<span data-ttu-id="2c15a-125">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="2c15a-125">C# operators</span></span>](index.md)
- [<span data-ttu-id="2c15a-126">İşleç aşırı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="2c15a-126">Operator overloading</span></span>](operator-overloading.md)
- [<span data-ttu-id="2c15a-127">Tür testi ve atama işleçleri</span><span class="sxs-lookup"><span data-stu-id="2c15a-127">Type-testing and cast operators</span></span>](type-testing-and-cast.md)
- [<span data-ttu-id="2c15a-128">Döküm ve tür dönüştürme</span><span class="sxs-lookup"><span data-stu-id="2c15a-128">Casting and type conversion</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
- [<span data-ttu-id="2c15a-129">Tasarım yönergeleri - Dönüşüm operatörleri</span><span class="sxs-lookup"><span data-stu-id="2c15a-129">Design guidelines - Conversion operators</span></span>](../../../standard/design-guidelines/operator-overloads.md#conversion-operators)
- [<span data-ttu-id="2c15a-130">C'de zincirlenmiş kullanıcı tanımlı açık dönüşümler #</span><span class="sxs-lookup"><span data-stu-id="2c15a-130">Chained user-defined explicit conversions in C#</span></span>](https://docs.microsoft.com/archive/blogs/ericlippert/chained-user-defined-explicit-conversions-in-c)
