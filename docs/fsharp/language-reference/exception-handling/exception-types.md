---
title: "Özel Durum Türleri (F#)"
description: "F # özel durum türlerini tanımlamak ve nasıl kullanılacağını öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e850205a-b8da-459e-8f6d-cb3510f8f173
ms.openlocfilehash: a0864218841396c0ebdf26c7585e0e5bb778f83e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="exception-types"></a><span data-ttu-id="c57af-104">Özel Durum Türleri</span><span class="sxs-lookup"><span data-stu-id="c57af-104">Exception Types</span></span>

<span data-ttu-id="c57af-105">F # özel durumların iki kategorisi vardır: .NET özel durum türleri ve F # özel durum türleri.</span><span class="sxs-lookup"><span data-stu-id="c57af-105">There are two categories of exceptions in F#: .NET exception types and F# exception types.</span></span> <span data-ttu-id="c57af-106">Bu konu F # özel durum türlerini tanımlamak ve nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="c57af-106">This topic describes how to define and use F# exception types.</span></span>


## <a name="syntax"></a><span data-ttu-id="c57af-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c57af-107">Syntax</span></span>

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a><span data-ttu-id="c57af-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c57af-108">Remarks</span></span>
<span data-ttu-id="c57af-109">Önceki sözdiziminde *özel durum türü* yeni F # özel durum türü, adı ve *bağımsız değişken türü* bu türünde bir özel durum yükselttiğinizde sağlanabilir bir bağımsız değişken türünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c57af-109">In the previous syntax, *exception-type* is the name of a new F# exception type, and *argument-type* represents the type of an argument that can be supplied when you raise an exception of this type.</span></span> <span data-ttu-id="c57af-110">İçin bir tanımlama grubu türü kullanarak birden fazla bağımsız değişkenini belirtebilirsiniz *bağımsız değişken türü*.</span><span class="sxs-lookup"><span data-stu-id="c57af-110">You can specify multiple arguments by using a tuple type for *argument-type*.</span></span>

<span data-ttu-id="c57af-111">F # özel durumu için tipik bir tanım aşağıdakine benzer.</span><span class="sxs-lookup"><span data-stu-id="c57af-111">A typical definition for an F# exception resembles the following.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

<span data-ttu-id="c57af-112">Bu tür bir özel durum kullanarak oluşturabileceğiniz `raise` gibi işlev.</span><span class="sxs-lookup"><span data-stu-id="c57af-112">You can generate an exception of this type by using the `raise` function, as follows.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

<span data-ttu-id="c57af-113">F # özel durum türü doğrudan filtreleri kullanabileceğiniz bir `try...with` aşağıdaki örnekte gösterildiği gibi ifade.</span><span class="sxs-lookup"><span data-stu-id="c57af-113">You can use an F# exception type directly in the filters in a `try...with` expression, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

<span data-ttu-id="c57af-114">İle tanımladığınız özel durum türü `exception` sözcüktür F # devraldığı yeni bir tür `System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="c57af-114">The exception type that you define with the `exception` keyword in F# is a new type that inherits from `System.Exception`.</span></span>


## <a name="see-also"></a><span data-ttu-id="c57af-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c57af-115">See Also</span></span>
[<span data-ttu-id="c57af-116">Özel durum işleme</span><span class="sxs-lookup"><span data-stu-id="c57af-116">Exception Handling</span></span>](index.md)

[<span data-ttu-id="c57af-117">Özel durumlar: `raise` işlevi</span><span class="sxs-lookup"><span data-stu-id="c57af-117">Exceptions: the `raise` Function</span></span>](the-raise-function.md)

[<span data-ttu-id="c57af-118">Özel durum hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="c57af-118">Exception Hierarchy</span></span>](https://msdn.microsoft.com/library/z4c5tckx.aspx)
