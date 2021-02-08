---
description: "Şu konuda daha fazla bilgi edinin: BC42105: ' <procedurename> ' işlevi tüm kod yollarında değer döndürmüyor"
title: "'<procedurename>' işlevi tüm kod yollarında değer döndürmüyor"
ms.date: 07/20/2015
f1_keywords:
- bc42105
- vbc42105
helpviewer_keywords:
- BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
ms.openlocfilehash: 2d0fa99906606228595a0c0d45f58dae0b269b77
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796177"
---
# <a name="bc42105-function-procedurename-doesnt-return-a-value-on-all-code-paths"></a><span data-ttu-id="21caa-103">BC42105: ' \<procedurename> ' işlevi tüm kod yollarında bir değer döndürmüyor</span><span class="sxs-lookup"><span data-stu-id="21caa-103">BC42105: Function '\<procedurename>' doesn't return a value on all code paths</span></span>

<span data-ttu-id="21caa-104">' \<procedurename> ' İşlevi tüm kod yollarında bir değer döndürmüyor.</span><span class="sxs-lookup"><span data-stu-id="21caa-104">Function '\<procedurename>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="21caa-105">' Return ' deyiminiz eksik mi?</span><span class="sxs-lookup"><span data-stu-id="21caa-105">Are you missing a 'Return' statement?</span></span>

 <span data-ttu-id="21caa-106">Bir `Function` yordamın, bir değer döndürmeyen kodu aracılığıyla olası en az bir yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="21caa-106">A `Function` procedure has at least one possible path through its code that does not return a value.</span></span>

 <span data-ttu-id="21caa-107">Aşağıdaki yollarla bir yordamdan bir değer döndürebilirsiniz `Function` :</span><span class="sxs-lookup"><span data-stu-id="21caa-107">You can return a value from a `Function` procedure in any of the following ways:</span></span>

- <span data-ttu-id="21caa-108">Değeri [Return ifadesine](../statements/return-statement.md)ekleyin.</span><span class="sxs-lookup"><span data-stu-id="21caa-108">Include the value in a [Return Statement](../statements/return-statement.md).</span></span>

- <span data-ttu-id="21caa-109">`Function`Yordam adına değeri atayın ve sonra bir `Exit Function` ifade gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="21caa-109">Assign the value to the `Function` procedure name and then perform an `Exit Function` statement.</span></span>

- <span data-ttu-id="21caa-110">`Function`Yordam adına değeri atayın ve sonra `End Function` ifadesini gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="21caa-110">Assign the value to the `Function` procedure name and then perform the `End Function` statement.</span></span>

 <span data-ttu-id="21caa-111">Denetim veya öğesine geçerse `Exit Function` `End Function` ve yordam adına herhangi bir değer atamadıysanız, yordam dönüş veri türünün varsayılan değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="21caa-111">If control passes to `Exit Function` or `End Function` and you have not assigned any value to the procedure name, the procedure returns the default value of the return data type.</span></span> <span data-ttu-id="21caa-112">Daha fazla bilgi için bkz. [Işlev deyimindeki](../statements/function-statement.md)"davranış".</span><span class="sxs-lookup"><span data-stu-id="21caa-112">For more information, see "Behavior" in [Function Statement](../statements/function-statement.md).</span></span>

 <span data-ttu-id="21caa-113">Bu ileti, varsayılan olarak bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="21caa-113">By default, this message is a warning.</span></span> <span data-ttu-id="21caa-114">Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="21caa-114">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="21caa-115">**Hata kimliği:** BC42105</span><span class="sxs-lookup"><span data-stu-id="21caa-115">**Error ID:** BC42105</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="21caa-116">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="21caa-116">To correct this error</span></span>

- <span data-ttu-id="21caa-117">Denetim akışı mantığınızı denetleyin ve dönüşe neden olan her deyimden önce bir değer atadığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="21caa-117">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>

     <span data-ttu-id="21caa-118">Her zaman ifadesini kullanıyorsanız, yordamdan gelen her döndürün bir değer döndürdüğünden emin olmak daha kolaydır `Return` .</span><span class="sxs-lookup"><span data-stu-id="21caa-118">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="21caa-119">Bunu yaparsanız, önceki son deyimin `End Function` bir ifade olması gerekir `Return` .</span><span class="sxs-lookup"><span data-stu-id="21caa-119">If you do this, the last statement before `End Function` should be a `Return` statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="21caa-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21caa-120">See also</span></span>

- [<span data-ttu-id="21caa-121">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="21caa-121">Function Procedures</span></span>](../../programming-guide/language-features/procedures/function-procedures.md)
- [<span data-ttu-id="21caa-122">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="21caa-122">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="21caa-123">Derleme Sayfası, Proje Tasarımcısı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21caa-123">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
