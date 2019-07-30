---
title: Özel Durum Türleri
description: Özel durum türlerini tanımlama ve kullanma F# hakkında bilgi edinin.
ms.date: 05/16/2016
ms.openlocfilehash: 8545fab50ff6338d1f1621710a838a200f9ac705
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630318"
---
# <a name="exception-types"></a><span data-ttu-id="f6bdd-103">Özel Durum Türleri</span><span class="sxs-lookup"><span data-stu-id="f6bdd-103">Exception Types</span></span>

<span data-ttu-id="f6bdd-104">İçinde F#iki özel durum kategorisi vardır: .NET özel durum türleri ve F# özel durum türleri.</span><span class="sxs-lookup"><span data-stu-id="f6bdd-104">There are two categories of exceptions in F#: .NET exception types and F# exception types.</span></span> <span data-ttu-id="f6bdd-105">Bu konu, F# özel durum türlerinin nasıl tanımlanacağını ve kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="f6bdd-105">This topic describes how to define and use F# exception types.</span></span>

## <a name="syntax"></a><span data-ttu-id="f6bdd-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f6bdd-106">Syntax</span></span>

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a><span data-ttu-id="f6bdd-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f6bdd-107">Remarks</span></span>

<span data-ttu-id="f6bdd-108">Önceki sözdiziminde, *özel* durum türü yeni F# bir özel durum türünün adıdır ve *bağımsız değişken türü* , bu türde bir özel durum oluştururken sağlanabilecek bir bağımsız değişkenin türünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f6bdd-108">In the previous syntax, *exception-type* is the name of a new F# exception type, and *argument-type* represents the type of an argument that can be supplied when you raise an exception of this type.</span></span> <span data-ttu-id="f6bdd-109">*Bağımsız değişken*türü için bir demet türü kullanarak birden çok bağımsız değişken belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6bdd-109">You can specify multiple arguments by using a tuple type for *argument-type*.</span></span>

<span data-ttu-id="f6bdd-110">Bir F# özel durum için tipik bir tanım aşağıdakine benzer.</span><span class="sxs-lookup"><span data-stu-id="f6bdd-110">A typical definition for an F# exception resembles the following.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

<span data-ttu-id="f6bdd-111">Aşağıdaki gibi, `raise` işlevini kullanarak bu türde bir özel durum oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6bdd-111">You can generate an exception of this type by using the `raise` function, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

<span data-ttu-id="f6bdd-112">Aşağıdaki örnekte gösterildiği gibi F# , bir `try...with` ifadede doğrudan filtrelerde bir özel durum türü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6bdd-112">You can use an F# exception type directly in the filters in a `try...with` expression, as shown in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

<span data-ttu-id="f6bdd-113">İçindeki `exception` F# anahtar sözcüğüyle tanımladığınız özel durum türü, öğesinden `System.Exception`devralan yeni bir türdür.</span><span class="sxs-lookup"><span data-stu-id="f6bdd-113">The exception type that you define with the `exception` keyword in F# is a new type that inherits from `System.Exception`.</span></span>

## <a name="see-also"></a><span data-ttu-id="f6bdd-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f6bdd-114">See also</span></span>

- [<span data-ttu-id="f6bdd-115">Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="f6bdd-115">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="f6bdd-116">Özel durumlar: `raise` işlev</span><span class="sxs-lookup"><span data-stu-id="f6bdd-116">Exceptions: the `raise` Function</span></span>](the-raise-function.md)
- [<span data-ttu-id="f6bdd-117">Özel durum hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="f6bdd-117">Exception Hierarchy</span></span>](https://msdn.microsoft.com/library/z4c5tckx.aspx)
