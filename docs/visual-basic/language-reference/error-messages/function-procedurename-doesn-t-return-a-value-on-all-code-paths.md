---
title: "'<procedurename>' işlevi tüm kod yollarında değer döndürmüyor"
ms.date: 07/20/2015
f1_keywords:
- bc42105
- vbc42105
helpviewer_keywords:
- BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
ms.openlocfilehash: 5295775b2541219e611e167e304ca8ef99cf6bd8
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874140"
---
# <a name="function-procedurename-doesnt-return-a-value-on-all-code-paths"></a><span data-ttu-id="1b686-102">'\<procedurename>' işlevi tüm kod yollarında değer döndürmüyor</span><span class="sxs-lookup"><span data-stu-id="1b686-102">Function '\<procedurename>' doesn't return a value on all code paths</span></span>

<span data-ttu-id="1b686-103">' \<procedurename> ' İşlevi tüm kod yollarında bir değer döndürmüyor.</span><span class="sxs-lookup"><span data-stu-id="1b686-103">Function '\<procedurename>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="1b686-104">' Return ' deyiminiz eksik mi?</span><span class="sxs-lookup"><span data-stu-id="1b686-104">Are you missing a 'Return' statement?</span></span>  
  
 <span data-ttu-id="1b686-105">Bir `Function` yordamın, bir değer döndürmeyen kodu aracılığıyla olası en az bir yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="1b686-105">A `Function` procedure has at least one possible path through its code that does not return a value.</span></span>  
  
 <span data-ttu-id="1b686-106">Aşağıdaki yollarla bir yordamdan bir değer döndürebilirsiniz `Function` :</span><span class="sxs-lookup"><span data-stu-id="1b686-106">You can return a value from a `Function` procedure in any of the following ways:</span></span>  
  
- <span data-ttu-id="1b686-107">Değeri [Return ifadesine](../statements/return-statement.md)ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1b686-107">Include the value in a [Return Statement](../statements/return-statement.md).</span></span>  
  
- <span data-ttu-id="1b686-108">`Function`Yordam adına değeri atayın ve sonra bir `Exit Function` ifade gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="1b686-108">Assign the value to the `Function` procedure name and then perform an `Exit Function` statement.</span></span>  
  
- <span data-ttu-id="1b686-109">`Function`Yordam adına değeri atayın ve sonra `End Function` ifadesini gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="1b686-109">Assign the value to the `Function` procedure name and then perform the `End Function` statement.</span></span>  
  
 <span data-ttu-id="1b686-110">Denetim veya öğesine geçerse `Exit Function` `End Function` ve yordam adına herhangi bir değer atamadıysanız, yordam dönüş veri türünün varsayılan değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="1b686-110">If control passes to `Exit Function` or `End Function` and you have not assigned any value to the procedure name, the procedure returns the default value of the return data type.</span></span> <span data-ttu-id="1b686-111">Daha fazla bilgi için bkz. [Işlev deyimindeki](../statements/function-statement.md)"davranış".</span><span class="sxs-lookup"><span data-stu-id="1b686-111">For more information, see "Behavior" in [Function Statement](../statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="1b686-112">Bu ileti, varsayılan olarak bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="1b686-112">By default, this message is a warning.</span></span> <span data-ttu-id="1b686-113">Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="1b686-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="1b686-114">**Hata kimliği:** BC42105</span><span class="sxs-lookup"><span data-stu-id="1b686-114">**Error ID:** BC42105</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1b686-115">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="1b686-115">To correct this error</span></span>  
  
- <span data-ttu-id="1b686-116">Denetim akışı mantığınızı denetleyin ve dönüşe neden olan her deyimden önce bir değer atadığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="1b686-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>  
  
     <span data-ttu-id="1b686-117">Her zaman ifadesini kullanıyorsanız, yordamdan gelen her döndürün bir değer döndürdüğünden emin olmak daha kolaydır `Return` .</span><span class="sxs-lookup"><span data-stu-id="1b686-117">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="1b686-118">Bunu yaparsanız, önceki son deyimin `End Function` bir ifade olması gerekir `Return` .</span><span class="sxs-lookup"><span data-stu-id="1b686-118">If you do this, the last statement before `End Function` should be a `Return` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b686-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b686-119">See also</span></span>

- [<span data-ttu-id="1b686-120">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="1b686-120">Function Procedures</span></span>](../../programming-guide/language-features/procedures/function-procedures.md)
- [<span data-ttu-id="1b686-121">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="1b686-121">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="1b686-122">Derleme Sayfası, Proje Tasarımcısı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1b686-122">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
