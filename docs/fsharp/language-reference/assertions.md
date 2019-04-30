---
title: Onaylamalar
description: İfadeleri test etmek için bir hata ayıklama özelliği olarak 'onay' ifadesi kullanmayı öğrenirsiniz F# programlama dilidir.
ms.date: 05/16/2016
ms.openlocfilehash: c2d97386e87e9b915da490a78fff9aedb9def616
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61703224"
---
# <a name="assertions"></a><span data-ttu-id="a2d92-103">Onaylamalar</span><span class="sxs-lookup"><span data-stu-id="a2d92-103">Assertions</span></span>

<span data-ttu-id="a2d92-104">`assert` Bir ifade test etmek için kullanabileceğiniz bir hata ayıklama özelliği ifadesidir.</span><span class="sxs-lookup"><span data-stu-id="a2d92-104">The `assert` expression is a debugging feature that you can use to test an expression.</span></span> <span data-ttu-id="a2d92-105">Hata ayıklama modunda başarısızlık durumunda, bir sistem hatası iletişim kutusu bir onay oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a2d92-105">Upon failure in Debug mode, an assertion generates a system error dialog box.</span></span>

## <a name="syntax"></a><span data-ttu-id="a2d92-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a2d92-106">Syntax</span></span>

```fsharp
assert condition
```

## <a name="remarks"></a><span data-ttu-id="a2d92-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a2d92-107">Remarks</span></span>

<span data-ttu-id="a2d92-108">`assert` İfade türüne sahip `bool -> unit`.</span><span class="sxs-lookup"><span data-stu-id="a2d92-108">The `assert` expression has type `bool -> unit`.</span></span>

<span data-ttu-id="a2d92-109">Önceki sözdiziminde, *koşul* test edilecek bir Boole ifadesi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a2d92-109">In the previous syntax, *condition* represents a Boolean expression that is to be tested.</span></span> <span data-ttu-id="a2d92-110">İfade değerlendirme sonucu `true`, yürütme devam eder etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="a2d92-110">If the expression evaluates to `true`, execution continues unaffected.</span></span> <span data-ttu-id="a2d92-111">Değerlendirilirse `false`, sistem hatası iletişim kutusu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a2d92-111">If it evaluates to `false`, a system error dialog box is generated.</span></span> <span data-ttu-id="a2d92-112">Hata iletişim kutusu dize içeren bir başlığa sahip **onaylama işlemi başarısız oldu**.</span><span class="sxs-lookup"><span data-stu-id="a2d92-112">The error dialog box has a caption that contains the string **Assertion Failed**.</span></span> <span data-ttu-id="a2d92-113">İletişim kutusu, onaylama işlemi hatası nerede oluştuğunu gösteren bir yığın izlemesi içerir.</span><span class="sxs-lookup"><span data-stu-id="a2d92-113">The dialog box contains a stack trace that indicates where the assertion failure occurred.</span></span>

<span data-ttu-id="a2d92-114">Yalnızca, hata ayıklama modunda derleme yaptığınızda, onaylama işlemi denetimi etkinleştirilir; diğer bir deyişle, sabiti `DEBUG` tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="a2d92-114">Assertion checking is enabled only when you compile in Debug mode; that is, if the constant `DEBUG` is defined.</span></span> <span data-ttu-id="a2d92-115">Varsayılan olarak, proje sistemi içindeki `DEBUG` sabiti, hata ayıklama yapılandırmasında ancak sürüm yapılandırmasını içinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="a2d92-115">In the project system, by default, the `DEBUG` constant is defined in the Debug configuration but not in the Release configuration.</span></span>

<span data-ttu-id="a2d92-116">Onaylama işlemi hatası kullanarak yakalanamaz F# özel durum işleme.</span><span class="sxs-lookup"><span data-stu-id="a2d92-116">The assertion failure error cannot be caught by using F# exception handling.</span></span>

> [!NOTE]
> <span data-ttu-id="a2d92-117">`assert` İşlevi çözümler için <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a2d92-117">The `assert` function resolves to <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="a2d92-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2d92-118">Example</span></span>

<span data-ttu-id="a2d92-119">Aşağıdaki kod örneği kullanışını `assert` ifade.</span><span class="sxs-lookup"><span data-stu-id="a2d92-119">The following code example illustrates the use of the `assert` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a><span data-ttu-id="a2d92-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2d92-120">See also</span></span>

- [<span data-ttu-id="a2d92-121">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="a2d92-121">F# Language Reference</span></span>](index.md)