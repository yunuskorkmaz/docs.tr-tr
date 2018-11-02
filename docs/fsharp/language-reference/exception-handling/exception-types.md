---
title: Özel Durum Türleri (F#)
description: 'Tanımlama ve F # özel durum türlerini kullanma hakkında bilgi edinin.'
ms.date: 05/16/2016
ms.openlocfilehash: b8d648a3649153a3604856deb61ce41db8c40bf2
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "43858827"
---
# <a name="exception-types"></a><span data-ttu-id="caab9-103">Özel Durum Türleri</span><span class="sxs-lookup"><span data-stu-id="caab9-103">Exception Types</span></span>

<span data-ttu-id="caab9-104">F # dilinde özel durumlar iki kategorisi vardır: .NET özel durum türlerini ve F # özel durum türleri.</span><span class="sxs-lookup"><span data-stu-id="caab9-104">There are two categories of exceptions in F#: .NET exception types and F# exception types.</span></span> <span data-ttu-id="caab9-105">Bu konuda, tanımlamak ve F # özel durum türlerini kullanın açıklar.</span><span class="sxs-lookup"><span data-stu-id="caab9-105">This topic describes how to define and use F# exception types.</span></span>

## <a name="syntax"></a><span data-ttu-id="caab9-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="caab9-106">Syntax</span></span>

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a><span data-ttu-id="caab9-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="caab9-107">Remarks</span></span>

<span data-ttu-id="caab9-108">Önceki sözdiziminde, *özel durum türü* yeni F # özel durum türü adıdır ve *bağımsız değişken türü* bu türde bir özel durum yükselttiğinizde sağlanabilir bir bağımsız değişken türünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="caab9-108">In the previous syntax, *exception-type* is the name of a new F# exception type, and *argument-type* represents the type of an argument that can be supplied when you raise an exception of this type.</span></span> <span data-ttu-id="caab9-109">Bir demet türü için'ı kullanarak birden çok bağımsız değişkeni belirtebilirsiniz *bağımsız değişken türü*.</span><span class="sxs-lookup"><span data-stu-id="caab9-109">You can specify multiple arguments by using a tuple type for *argument-type*.</span></span>

<span data-ttu-id="caab9-110">Bir F # özel durum için tipik bir tanım aşağıdakine benzer.</span><span class="sxs-lookup"><span data-stu-id="caab9-110">A typical definition for an F# exception resembles the following.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

<span data-ttu-id="caab9-111">Bu tür bir özel durum kullanarak oluşturabileceğiniz `raise` gibi işlev.</span><span class="sxs-lookup"><span data-stu-id="caab9-111">You can generate an exception of this type by using the `raise` function, as follows.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

<span data-ttu-id="caab9-112">Bir F # özel durum türü, doğrudan, filtreleri kullanabilirsiniz bir `try...with` aşağıdaki örnekte gösterildiği gibi ifade.</span><span class="sxs-lookup"><span data-stu-id="caab9-112">You can use an F# exception type directly in the filters in a `try...with` expression, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

<span data-ttu-id="caab9-113">İle tanımladığınız özel durum türü `exception` sözcüktür F #'de devraldığı yeni bir tür `System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="caab9-113">The exception type that you define with the `exception` keyword in F# is a new type that inherits from `System.Exception`.</span></span>

## <a name="see-also"></a><span data-ttu-id="caab9-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="caab9-114">See also</span></span>

- [<span data-ttu-id="caab9-115">Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="caab9-115">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="caab9-116">Özel durumlar: `raise` işlevi</span><span class="sxs-lookup"><span data-stu-id="caab9-116">Exceptions: the `raise` Function</span></span>](the-raise-function.md)
- [<span data-ttu-id="caab9-117">Özel durum hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="caab9-117">Exception Hierarchy</span></span>](https://msdn.microsoft.com/library/z4c5tckx.aspx)
