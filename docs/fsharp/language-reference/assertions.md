---
title: Onaylamalar (F#)
description: "'Onay' ifadesi ifadeleri F # programlama dili test etmek için hata ayıklama bir özellik olarak kullanmayı öğrenin."
ms.date: 05/16/2016
ms.openlocfilehash: 83e6cd77bbbb2c32e9b778e5bf6dd9d2e9c8fe32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563152"
---
# <a name="assertions"></a><span data-ttu-id="0f8eb-103">Onaylamalar</span><span class="sxs-lookup"><span data-stu-id="0f8eb-103">Assertions</span></span>

<span data-ttu-id="0f8eb-104">`assert` İfadesidir bir ifade test etmek için kullanabileceğiniz bir hata ayıklama özelliği.</span><span class="sxs-lookup"><span data-stu-id="0f8eb-104">The `assert` expression is a debugging feature that you can use to test an expression.</span></span> <span data-ttu-id="0f8eb-105">Hata ayıklama modunda başarısızlık durumunda, bir onaylama sistem hata iletişim kutusu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0f8eb-105">Upon failure in Debug mode, an assertion generates a system error dialog box.</span></span>

## <a name="syntax"></a><span data-ttu-id="0f8eb-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0f8eb-106">Syntax</span></span>

```fsharp
assert condition
```

## <a name="remarks"></a><span data-ttu-id="0f8eb-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0f8eb-107">Remarks</span></span>

<span data-ttu-id="0f8eb-108">`assert` İfade türüne sahip `bool -> unit`.</span><span class="sxs-lookup"><span data-stu-id="0f8eb-108">The `assert` expression has type `bool -> unit`.</span></span>

<span data-ttu-id="0f8eb-109">Önceki sözdiziminde *koşulu* test edilmesi için bir Boole ifadesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0f8eb-109">In the previous syntax, *condition* represents a Boolean expression that is to be tested.</span></span> <span data-ttu-id="0f8eb-110">İfade değerlendirilirse `true`, yürütülmeye etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="0f8eb-110">If the expression evaluates to `true`, execution continues unaffected.</span></span> <span data-ttu-id="0f8eb-111">Değerlendirilirse `false`, bir sistem hatası iletişim kutusu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0f8eb-111">If it evaluates to `false`, a system error dialog box is generated.</span></span> <span data-ttu-id="0f8eb-112">Hata iletişim kutusu dizeyi içeren bir resim yazısını **onaylama başarısız**.</span><span class="sxs-lookup"><span data-stu-id="0f8eb-112">The error dialog box has a caption that contains the string **Assertion Failed**.</span></span> <span data-ttu-id="0f8eb-113">İletişim kutusu onaylama hatası nerede oluştuğunu gösteren bir yığın izlemeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="0f8eb-113">The dialog box contains a stack trace that indicates where the assertion failure occurred.</span></span>

<span data-ttu-id="0f8eb-114">Yalnızca hata ayıklama modunda derlediğinizde, onaylama işlemi denetimi etkinleştirilir; diğer bir deyişle, sabit `DEBUG` tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="0f8eb-114">Assertion checking is enabled only when you compile in Debug mode; that is, if the constant `DEBUG` is defined.</span></span> <span data-ttu-id="0f8eb-115">Varsayılan olarak, proje sisteminde `DEBUG` sabiti hata ayıklama yapılandırmasını ancak sürüm yapılandırmasında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="0f8eb-115">In the project system, by default, the `DEBUG` constant is defined in the Debug configuration but not in the Release configuration.</span></span>

<span data-ttu-id="0f8eb-116">F # özel durum işleme kullanarak onaylama hata yakalandı olamaz.</span><span class="sxs-lookup"><span data-stu-id="0f8eb-116">The assertion failure error cannot be caught by using F# exception handling.</span></span>

>[!NOTE]
<span data-ttu-id="0f8eb-117">`assert` İşlevi çözümler için <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0f8eb-117">The `assert` function resolves to <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="0f8eb-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f8eb-118">Example</span></span>

<span data-ttu-id="0f8eb-119">Aşağıdaki kod örneğinde kullanımını göstermektedir `assert` ifade.</span><span class="sxs-lookup"><span data-stu-id="0f8eb-119">The following code example illustrates the use of the `assert` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]
    
## <a name="see-also"></a><span data-ttu-id="0f8eb-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0f8eb-120">See Also</span></span>

[<span data-ttu-id="0f8eb-121">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="0f8eb-121">F# Language Reference</span></span>](index.md)
