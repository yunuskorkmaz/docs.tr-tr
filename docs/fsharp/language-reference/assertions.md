---
title: Onaylamalar
description: F# Programlama dilindeki ifadeleri test etmek için hata ayıklama özelliği olarak ' onaylama ' ifadesini kullanmayı öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: b8b7e9662143b432d650f87515d4af31cced4149
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630029"
---
# <a name="assertions"></a><span data-ttu-id="9c575-103">Onaylamalar</span><span class="sxs-lookup"><span data-stu-id="9c575-103">Assertions</span></span>

<span data-ttu-id="9c575-104">`assert` İfade, bir ifadeyi test etmek için kullanabileceğiniz bir hata ayıklama özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="9c575-104">The `assert` expression is a debugging feature that you can use to test an expression.</span></span> <span data-ttu-id="9c575-105">Hata ayıklama modunda hata oluştuğunda bir onaylama işlemi bir sistem hatası iletişim kutusu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9c575-105">Upon failure in Debug mode, an assertion generates a system error dialog box.</span></span>

## <a name="syntax"></a><span data-ttu-id="9c575-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9c575-106">Syntax</span></span>

```fsharp
assert condition
```

## <a name="remarks"></a><span data-ttu-id="9c575-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9c575-107">Remarks</span></span>

<span data-ttu-id="9c575-108">`assert` İfadenin türü`bool -> unit`.</span><span class="sxs-lookup"><span data-stu-id="9c575-108">The `assert` expression has type `bool -> unit`.</span></span>

<span data-ttu-id="9c575-109">Önceki sözdiziminde, *koşul* test edilecek bir Boole ifadesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9c575-109">In the previous syntax, *condition* represents a Boolean expression that is to be tested.</span></span> <span data-ttu-id="9c575-110">İfade olarak `true`değerlendirilirse, yürütme etkilenmeden devam eder.</span><span class="sxs-lookup"><span data-stu-id="9c575-110">If the expression evaluates to `true`, execution continues unaffected.</span></span> <span data-ttu-id="9c575-111">Değerlendiriliyorsa `false`, bir sistem hatası iletişim kutusu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9c575-111">If it evaluates to `false`, a system error dialog box is generated.</span></span> <span data-ttu-id="9c575-112">Hata iletişim kutusu, dize **onaylama Işlemi başarısız**olan bir açıklamalı alt yazı içeriyor.</span><span class="sxs-lookup"><span data-stu-id="9c575-112">The error dialog box has a caption that contains the string **Assertion Failed**.</span></span> <span data-ttu-id="9c575-113">İletişim kutusu, onaylama hatasının nerede oluştuğunu gösteren bir yığın izlemesi içerir.</span><span class="sxs-lookup"><span data-stu-id="9c575-113">The dialog box contains a stack trace that indicates where the assertion failure occurred.</span></span>

<span data-ttu-id="9c575-114">Onaylama denetimi yalnızca hata ayıklama modunda derlerken etkinleştirilir; Bu, sabit `DEBUG` tanımlanmışsa.</span><span class="sxs-lookup"><span data-stu-id="9c575-114">Assertion checking is enabled only when you compile in Debug mode; that is, if the constant `DEBUG` is defined.</span></span> <span data-ttu-id="9c575-115">Proje sisteminde, varsayılan olarak, `DEBUG` sabit hata ayıklama yapılandırmasında tanımlanmıştır, ancak yayın yapılandırmasında belirlenir.</span><span class="sxs-lookup"><span data-stu-id="9c575-115">In the project system, by default, the `DEBUG` constant is defined in the Debug configuration but not in the Release configuration.</span></span>

<span data-ttu-id="9c575-116">Onaylama hatası hatası özel durum işleme kullanılarak F# yakalanamıyor.</span><span class="sxs-lookup"><span data-stu-id="9c575-116">The assertion failure error cannot be caught by using F# exception handling.</span></span>

> [!NOTE]
> <span data-ttu-id="9c575-117">`assert` İşlevi olarak<xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="9c575-117">The `assert` function resolves to <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="9c575-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="9c575-118">Example</span></span>

<span data-ttu-id="9c575-119">Aşağıdaki kod örneği, `assert` ifadesinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9c575-119">The following code example illustrates the use of the `assert` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a><span data-ttu-id="9c575-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9c575-120">See also</span></span>

- [<span data-ttu-id="9c575-121">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="9c575-121">F# Language Reference</span></span>](index.md)
