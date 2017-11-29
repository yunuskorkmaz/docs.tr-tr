---
title: Onaylamalar (F#)
description: "'Onay' ifadesi ifadeleri F # programlama dili test etmek için hata ayıklama bir özellik olarak kullanmayı öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 2badaad7-f086-47e7-99c1-91f35117da83
ms.openlocfilehash: 56891769602afaa765ebfe7e7822a179c7a22968
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="assertions"></a><span data-ttu-id="c68c8-104">Onaylamalar</span><span class="sxs-lookup"><span data-stu-id="c68c8-104">Assertions</span></span>

<span data-ttu-id="c68c8-105">`assert` İfadesidir bir ifade test etmek için kullanabileceğiniz bir hata ayıklama özelliği.</span><span class="sxs-lookup"><span data-stu-id="c68c8-105">The `assert` expression is a debugging feature that you can use to test an expression.</span></span> <span data-ttu-id="c68c8-106">Hata ayıklama modunda başarısızlık durumunda, bir onaylama sistem hata iletişim kutusu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c68c8-106">Upon failure in Debug mode, an assertion generates a system error dialog box.</span></span>

## <a name="syntax"></a><span data-ttu-id="c68c8-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c68c8-107">Syntax</span></span>

```fsharp
assert condition
```

## <a name="remarks"></a><span data-ttu-id="c68c8-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c68c8-108">Remarks</span></span>

<span data-ttu-id="c68c8-109">`assert` İfade türüne sahip `bool -> unit`.</span><span class="sxs-lookup"><span data-stu-id="c68c8-109">The `assert` expression has type `bool -> unit`.</span></span>

<span data-ttu-id="c68c8-110">Önceki sözdiziminde *koşulu* test edilmesi için bir Boole ifadesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c68c8-110">In the previous syntax, *condition* represents a Boolean expression that is to be tested.</span></span> <span data-ttu-id="c68c8-111">İfade değerlendirilirse `true`, yürütülmeye etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="c68c8-111">If the expression evaluates to `true`, execution continues unaffected.</span></span> <span data-ttu-id="c68c8-112">Değerlendirilirse `false`, bir sistem hatası iletişim kutusu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c68c8-112">If it evaluates to `false`, a system error dialog box is generated.</span></span> <span data-ttu-id="c68c8-113">Hata iletişim kutusu dizeyi içeren bir resim yazısını **onaylama başarısız**.</span><span class="sxs-lookup"><span data-stu-id="c68c8-113">The error dialog box has a caption that contains the string **Assertion Failed**.</span></span> <span data-ttu-id="c68c8-114">İletişim kutusu onaylama hatası nerede oluştuğunu gösteren bir yığın izlemeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="c68c8-114">The dialog box contains a stack trace that indicates where the assertion failure occurred.</span></span>

<span data-ttu-id="c68c8-115">Yalnızca hata ayıklama modunda derlediğinizde, onaylama işlemi denetimi etkinleştirilir; diğer bir deyişle, sabit `DEBUG` tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="c68c8-115">Assertion checking is enabled only when you compile in Debug mode; that is, if the constant `DEBUG` is defined.</span></span> <span data-ttu-id="c68c8-116">Varsayılan olarak, proje sisteminde `DEBUG` sabiti hata ayıklama yapılandırmasını ancak sürüm yapılandırmasında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="c68c8-116">In the project system, by default, the `DEBUG` constant is defined in the Debug configuration but not in the Release configuration.</span></span>

<span data-ttu-id="c68c8-117">F # özel durum işleme kullanarak onaylama hata yakalandı olamaz.</span><span class="sxs-lookup"><span data-stu-id="c68c8-117">The assertion failure error cannot be caught by using F# exception handling.</span></span>

>[!NOTE]
<span data-ttu-id="c68c8-118">`assert` İşlevi çözümler için <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c68c8-118">The `assert` function resolves to <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="c68c8-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="c68c8-119">Example</span></span>

<span data-ttu-id="c68c8-120">Aşağıdaki kod örneğinde kullanımını göstermektedir `assert` ifade.</span><span class="sxs-lookup"><span data-stu-id="c68c8-120">The following code example illustrates the use of the `assert` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]
    
## <a name="see-also"></a><span data-ttu-id="c68c8-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c68c8-121">See Also</span></span>

[<span data-ttu-id="c68c8-122">F # dili başvurusu</span><span class="sxs-lookup"><span data-stu-id="c68c8-122">F# Language Reference</span></span>](index.md)
