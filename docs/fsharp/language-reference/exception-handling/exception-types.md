---
title: Özel Durum Türleri
description: 'F # özel durum türlerini tanımlama ve kullanma hakkında bilgi edinin.'
ms.date: 05/16/2016
ms.openlocfilehash: 8b4ceec31a2d68abbcd025812ffeeefc0c090efb
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557235"
---
# <a name="exception-types"></a><span data-ttu-id="03e07-103">Özel Durum Türleri</span><span class="sxs-lookup"><span data-stu-id="03e07-103">Exception Types</span></span>

<span data-ttu-id="03e07-104">F #: .NET özel durum türlerinde ve F # özel durum türlerinde iki özel durum kategorisi vardır.</span><span class="sxs-lookup"><span data-stu-id="03e07-104">There are two categories of exceptions in F#: .NET exception types and F# exception types.</span></span> <span data-ttu-id="03e07-105">Bu konu başlığı altında, F # özel durum türlerinin nasıl tanımlanacağı ve kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="03e07-105">This topic describes how to define and use F# exception types.</span></span>

## <a name="syntax"></a><span data-ttu-id="03e07-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="03e07-106">Syntax</span></span>

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a><span data-ttu-id="03e07-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="03e07-107">Remarks</span></span>

<span data-ttu-id="03e07-108">Önceki sözdiziminde, *özel durum türü* yeni bir F # özel durum türünün adıdır ve *bağımsız değişken türü* , bu türde bir özel durum oluştururken sağlanabilecek bir bağımsız değişkenin türünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="03e07-108">In the previous syntax, *exception-type* is the name of a new F# exception type, and *argument-type* represents the type of an argument that can be supplied when you raise an exception of this type.</span></span> <span data-ttu-id="03e07-109">*Bağımsız değişken*türü için bir demet türü kullanarak birden çok bağımsız değişken belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03e07-109">You can specify multiple arguments by using a tuple type for *argument-type*.</span></span>

<span data-ttu-id="03e07-110">F # özel durumu için tipik bir tanım aşağıdakine benzer.</span><span class="sxs-lookup"><span data-stu-id="03e07-110">A typical definition for an F# exception resembles the following.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

<span data-ttu-id="03e07-111">Aşağıdaki gibi, işlevini kullanarak bu türde bir özel durum oluşturabilirsiniz `raise` .</span><span class="sxs-lookup"><span data-stu-id="03e07-111">You can generate an exception of this type by using the `raise` function, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

<span data-ttu-id="03e07-112">Aşağıdaki örnekte gösterildiği gibi, bir ifadedeki doğrudan filtrelerde bir F # özel durum türü kullanabilirsiniz `try...with` .</span><span class="sxs-lookup"><span data-stu-id="03e07-112">You can use an F# exception type directly in the filters in a `try...with` expression, as shown in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

<span data-ttu-id="03e07-113">`exception`F # içindeki anahtar sözcükle tanımladığınız özel durum türü, öğesinden devralan yeni bir türdür `System.Exception` .</span><span class="sxs-lookup"><span data-stu-id="03e07-113">The exception type that you define with the `exception` keyword in F# is a new type that inherits from `System.Exception`.</span></span>

## <a name="see-also"></a><span data-ttu-id="03e07-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03e07-114">See also</span></span>

- [<span data-ttu-id="03e07-115">Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="03e07-115">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="03e07-116">Özel durumlar: `raise` işlev</span><span class="sxs-lookup"><span data-stu-id="03e07-116">Exceptions: the `raise` Function</span></span>](the-raise-function.md)
- [<span data-ttu-id="03e07-117">Özel durum hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="03e07-117">Exception Hierarchy</span></span>](../../../standard/exceptions/index.md)
