---
title: Onaylamalar (F#)
description: "'Onay' ifadesi, ifadeler F # programlama dilinin test etmek için bir hata ayıklama özelliği olarak kullanmayı öğrenin."
ms.date: 05/16/2016
ms.openlocfilehash: 85b1e839bfd19bada48b7f1821d15ddd8fa77754
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44097544"
---
# <a name="assertions"></a><span data-ttu-id="a14fa-103">Onaylamalar</span><span class="sxs-lookup"><span data-stu-id="a14fa-103">Assertions</span></span>

<span data-ttu-id="a14fa-104">`assert` Bir ifade test etmek için kullanabileceğiniz bir hata ayıklama özelliği ifadesidir.</span><span class="sxs-lookup"><span data-stu-id="a14fa-104">The `assert` expression is a debugging feature that you can use to test an expression.</span></span> <span data-ttu-id="a14fa-105">Hata ayıklama modunda başarısızlık durumunda, bir sistem hatası iletişim kutusu bir onay oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a14fa-105">Upon failure in Debug mode, an assertion generates a system error dialog box.</span></span>

## <a name="syntax"></a><span data-ttu-id="a14fa-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a14fa-106">Syntax</span></span>

```fsharp
assert condition
```

## <a name="remarks"></a><span data-ttu-id="a14fa-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a14fa-107">Remarks</span></span>

<span data-ttu-id="a14fa-108">`assert` İfade türüne sahip `bool -> unit`.</span><span class="sxs-lookup"><span data-stu-id="a14fa-108">The `assert` expression has type `bool -> unit`.</span></span>

<span data-ttu-id="a14fa-109">Önceki sözdiziminde, *koşul* test edilecek bir Boole ifadesi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a14fa-109">In the previous syntax, *condition* represents a Boolean expression that is to be tested.</span></span> <span data-ttu-id="a14fa-110">İfade değerlendirme sonucu `true`, yürütme devam eder etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="a14fa-110">If the expression evaluates to `true`, execution continues unaffected.</span></span> <span data-ttu-id="a14fa-111">Değerlendirilirse `false`, sistem hatası iletişim kutusu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a14fa-111">If it evaluates to `false`, a system error dialog box is generated.</span></span> <span data-ttu-id="a14fa-112">Hata iletişim kutusu dize içeren bir başlığa sahip **onaylama işlemi başarısız oldu**.</span><span class="sxs-lookup"><span data-stu-id="a14fa-112">The error dialog box has a caption that contains the string **Assertion Failed**.</span></span> <span data-ttu-id="a14fa-113">İletişim kutusu, onaylama işlemi hatası nerede oluştuğunu gösteren bir yığın izlemesi içerir.</span><span class="sxs-lookup"><span data-stu-id="a14fa-113">The dialog box contains a stack trace that indicates where the assertion failure occurred.</span></span>

<span data-ttu-id="a14fa-114">Yalnızca, hata ayıklama modunda derleme yaptığınızda, onaylama işlemi denetimi etkinleştirilir; diğer bir deyişle, sabiti `DEBUG` tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="a14fa-114">Assertion checking is enabled only when you compile in Debug mode; that is, if the constant `DEBUG` is defined.</span></span> <span data-ttu-id="a14fa-115">Varsayılan olarak, proje sistemi içindeki `DEBUG` sabiti, hata ayıklama yapılandırmasında ancak sürüm yapılandırmasını içinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="a14fa-115">In the project system, by default, the `DEBUG` constant is defined in the Debug configuration but not in the Release configuration.</span></span>

<span data-ttu-id="a14fa-116">F # özel durum işlemeyi kullanarak, onaylama işlemi hatası yakalanamıyor.</span><span class="sxs-lookup"><span data-stu-id="a14fa-116">The assertion failure error cannot be caught by using F# exception handling.</span></span>

>[!NOTE]
<span data-ttu-id="a14fa-117">`assert` İşlevi çözümler için <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a14fa-117">The `assert` function resolves to <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="a14fa-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="a14fa-118">Example</span></span>

<span data-ttu-id="a14fa-119">Aşağıdaki kod örneği kullanışını `assert` ifade.</span><span class="sxs-lookup"><span data-stu-id="a14fa-119">The following code example illustrates the use of the `assert` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a><span data-ttu-id="a14fa-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a14fa-120">See also</span></span>

- [<span data-ttu-id="a14fa-121">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="a14fa-121">F# Language Reference</span></span>](index.md)
