---
title: Özel Durum Türleri
description: Tanımlama ve kullanma hakkında bilgi edinin F# özel durum türleri.
ms.date: 05/16/2016
ms.openlocfilehash: ed721dd0dc46a486fafeac2fa4c096800995ccb7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772729"
---
# <a name="exception-types"></a><span data-ttu-id="10c03-103">Özel Durum Türleri</span><span class="sxs-lookup"><span data-stu-id="10c03-103">Exception Types</span></span>

<span data-ttu-id="10c03-104">Özel durumları iki kategorisi vardır F#: .NET özel durum türlerini ve F# özel durum türleri.</span><span class="sxs-lookup"><span data-stu-id="10c03-104">There are two categories of exceptions in F#: .NET exception types and F# exception types.</span></span> <span data-ttu-id="10c03-105">Bu konu nasıl tanımlanacağını ve kullanılacağını açıklar F# özel durum türleri.</span><span class="sxs-lookup"><span data-stu-id="10c03-105">This topic describes how to define and use F# exception types.</span></span>

## <a name="syntax"></a><span data-ttu-id="10c03-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="10c03-106">Syntax</span></span>

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a><span data-ttu-id="10c03-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="10c03-107">Remarks</span></span>

<span data-ttu-id="10c03-108">Önceki sözdiziminde, *özel durum türü* yeni adı F# özel durum türü ve *bağımsız değişken türü* bu türde bir özel durum yükselttiğinizde sağlanabilir bir bağımsız değişken türünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="10c03-108">In the previous syntax, *exception-type* is the name of a new F# exception type, and *argument-type* represents the type of an argument that can be supplied when you raise an exception of this type.</span></span> <span data-ttu-id="10c03-109">Bir demet türü için'ı kullanarak birden çok bağımsız değişkeni belirtebilirsiniz *bağımsız değişken türü*.</span><span class="sxs-lookup"><span data-stu-id="10c03-109">You can specify multiple arguments by using a tuple type for *argument-type*.</span></span>

<span data-ttu-id="10c03-110">Tipik bir tanımı için bir F# özel durum aşağıdakine benzer.</span><span class="sxs-lookup"><span data-stu-id="10c03-110">A typical definition for an F# exception resembles the following.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

<span data-ttu-id="10c03-111">Bu tür bir özel durum kullanarak oluşturabileceğiniz `raise` gibi işlev.</span><span class="sxs-lookup"><span data-stu-id="10c03-111">You can generate an exception of this type by using the `raise` function, as follows.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

<span data-ttu-id="10c03-112">Kullanabileceğiniz bir F# özel durum türünü doğrudan filtreleri bir `try...with` aşağıdaki örnekte gösterildiği gibi ifade.</span><span class="sxs-lookup"><span data-stu-id="10c03-112">You can use an F# exception type directly in the filters in a `try...with` expression, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

<span data-ttu-id="10c03-113">İle tanımladığınız özel durum türü `exception` anahtar sözcüğünü F# devralan yeni bir türdür `System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="10c03-113">The exception type that you define with the `exception` keyword in F# is a new type that inherits from `System.Exception`.</span></span>

## <a name="see-also"></a><span data-ttu-id="10c03-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10c03-114">See also</span></span>

- [<span data-ttu-id="10c03-115">Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="10c03-115">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="10c03-116">Özel durumlar: `raise` işlevi</span><span class="sxs-lookup"><span data-stu-id="10c03-116">Exceptions: the `raise` Function</span></span>](the-raise-function.md)
- [<span data-ttu-id="10c03-117">Özel durum hiyerarşisi</span><span class="sxs-lookup"><span data-stu-id="10c03-117">Exception Hierarchy</span></span>](https://msdn.microsoft.com/library/z4c5tckx.aspx)