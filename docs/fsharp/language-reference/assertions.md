---
title: Onaylamalar
description: F# Programlama dilindeki ifadeleri test etmek için hata ayıklama özelliği olarak ' onaylama ' ifadesini kullanmayı öğrenin.
ms.date: 10/22/2019
ms.openlocfilehash: 430db20e5ca307ba43a72e678a0424e03b0ac381
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799067"
---
# <a name="assertions"></a><span data-ttu-id="4777e-103">Onaylamalar</span><span class="sxs-lookup"><span data-stu-id="4777e-103">Assertions</span></span>

<span data-ttu-id="4777e-104">`assert` ifadesi bir ifadeyi test etmek için kullanabileceğiniz bir hata ayıklama özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="4777e-104">The `assert` expression is a debugging feature that you can use to test an expression.</span></span> <span data-ttu-id="4777e-105">Hata ayıklama modunda hata oluştuğunda bir onaylama işlemi bir sistem hatası iletişim kutusu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4777e-105">Upon failure in Debug mode, an assertion generates a system error dialog box.</span></span>

## <a name="syntax"></a><span data-ttu-id="4777e-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4777e-106">Syntax</span></span>

```fsharp
assert condition
```

## <a name="remarks"></a><span data-ttu-id="4777e-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4777e-107">Remarks</span></span>

<span data-ttu-id="4777e-108">`assert` ifadesi tür `bool -> unit`.</span><span class="sxs-lookup"><span data-stu-id="4777e-108">The `assert` expression has type `bool -> unit`.</span></span>

<span data-ttu-id="4777e-109">`assert` işlevi <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>olarak çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="4777e-109">The `assert` function resolves to <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4777e-110">Bu, davranışının <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> doğrudan çağırmasına benzer şekilde olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="4777e-110">This means its behavior is identical to having called <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> directly.</span></span>

<span data-ttu-id="4777e-111">Onaylama denetimi yalnızca hata ayıklama modunda derlerken etkinleştirilir; diğer bir deyişle, sabit `DEBUG` tanımlanmışsa.</span><span class="sxs-lookup"><span data-stu-id="4777e-111">Assertion checking is enabled only when you compile in Debug mode; that is, if the constant `DEBUG` is defined.</span></span> <span data-ttu-id="4777e-112">Proje sisteminde, varsayılan olarak `DEBUG` sabiti, sürüm yapılandırmasında değil, hata ayıklama yapılandırmasında tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4777e-112">In the project system, by default, the `DEBUG` constant is defined in the Debug configuration but not in the Release configuration.</span></span>

<span data-ttu-id="4777e-113">Onaylama hatası hatası özel durum işleme kullanılarak F# yakalanamıyor.</span><span class="sxs-lookup"><span data-stu-id="4777e-113">The assertion failure error cannot be caught by using F# exception handling.</span></span>

## <a name="example"></a><span data-ttu-id="4777e-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="4777e-114">Example</span></span>

<span data-ttu-id="4777e-115">Aşağıdaki kod örneği `assert` ifadesinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4777e-115">The following code example illustrates the use of the `assert` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a><span data-ttu-id="4777e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4777e-116">See also</span></span>

- [<span data-ttu-id="4777e-117">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="4777e-117">F# Language Reference</span></span>](index.md)
