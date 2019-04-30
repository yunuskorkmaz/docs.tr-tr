---
title: -> İşleci - C# başvurusu
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- member access operator (->) [C#]
- -> operator [C#]
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
ms.openlocfilehash: be74f02a85aa05cdab32768ed38222fc4d9289b1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660020"
---
# <a name="--operator-c-reference"></a><span data-ttu-id="fb25a-102">-> İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="fb25a-102">-> Operator (C# Reference)</span></span>

<span data-ttu-id="fb25a-103">İşaretçi üye erişimi işleci `->` işaretçi yöneltme ve üye erişimi birleştirir.</span><span class="sxs-lookup"><span data-stu-id="fb25a-103">The pointer member access operator `->` combines pointer indirection and member access.</span></span>

<span data-ttu-id="fb25a-104">Varsa `x` bir işaretçi türü `T*` ve `y` erişilebilir bir üyesidir `T`, bir ifade formu</span><span class="sxs-lookup"><span data-stu-id="fb25a-104">If `x` is a pointer of the type `T*` and `y` is an accessible member of `T`, an expression of the form</span></span>

```csharp
x->y
```

<span data-ttu-id="fb25a-105">eşdeğerdir</span><span class="sxs-lookup"><span data-stu-id="fb25a-105">is equivalent to</span></span>

```csharp
(*x).y
```

<span data-ttu-id="fb25a-106">`->` İşleci gerektirir [güvenli](../keywords/unsafe.md) bağlamı.</span><span class="sxs-lookup"><span data-stu-id="fb25a-106">The `->` operator requires [unsafe](../keywords/unsafe.md) context.</span></span>

<span data-ttu-id="fb25a-107">Daha fazla bilgi için [nasıl yapılır: işaretçiyle bir üyeye erişme](../../programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md).</span><span class="sxs-lookup"><span data-stu-id="fb25a-107">For more information, see [How to: access a member with a pointer](../../programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="fb25a-108">İşleç overloadability</span><span class="sxs-lookup"><span data-stu-id="fb25a-108">Operator overloadability</span></span>

<span data-ttu-id="fb25a-109">`->` İşleci aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="fb25a-109">The `->` operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="fb25a-110">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="fb25a-110">C# language specification</span></span>

<span data-ttu-id="fb25a-111">Daha fazla bilgi için [işaretçi üye erişimi](~/_csharplang/spec/unsafe-code.md#pointer-member-access) bölümünü [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="fb25a-111">For more information, see the [Pointer member access](~/_csharplang/spec/unsafe-code.md#pointer-member-access) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fb25a-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb25a-112">See also</span></span>

- [<span data-ttu-id="fb25a-113">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="fb25a-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="fb25a-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="fb25a-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="fb25a-115">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="fb25a-115">C# Operators</span></span>](index.md)
- [<span data-ttu-id="fb25a-116">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="fb25a-116">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
