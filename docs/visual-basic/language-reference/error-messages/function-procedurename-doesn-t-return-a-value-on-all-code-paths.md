---
title: "İşlev &#39; &lt;procedurename&gt;&#39; belirlemeden #39; tüm kod yolları bir değer döndürmesi t"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42105
- vbc42105
helpviewer_keywords: BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5244d97a79f2450f44fe05f63510369914375912
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="function-39ltprocedurenamegt39-doesn39t-return-a-value-on-all-code-paths"></a><span data-ttu-id="a619b-102">İşlev &#39; &lt;procedurename&gt;&#39; belirlemeden #39; tüm kod yolları bir değer döndürmesi t</span><span class="sxs-lookup"><span data-stu-id="a619b-102">Function &#39;&lt;procedurename&gt;&#39; doesn&#39;t return a value on all code paths</span></span>
<span data-ttu-id="a619b-103">İşlev '\<procedurename >' tüm kod yolları bir değer döndürmüyor.</span><span class="sxs-lookup"><span data-stu-id="a619b-103">Function '\<procedurename>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="a619b-104">'Return' deyimi eksik olabilir mi?</span><span class="sxs-lookup"><span data-stu-id="a619b-104">Are you missing a 'Return' statement?</span></span>  
  
 <span data-ttu-id="a619b-105">A `Function` yordamının bir değer döndürmüyor kendi kod aracılığıyla en az bir olası yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="a619b-105">A `Function` procedure has at least one possible path through its code that does not return a value.</span></span>  
  
 <span data-ttu-id="a619b-106">Bir değer almak bir `Function` aşağıdaki yollardan birini yordamda:</span><span class="sxs-lookup"><span data-stu-id="a619b-106">You can return a value from a `Function` procedure in any of the following ways:</span></span>  
  
-   <span data-ttu-id="a619b-107">Değer içeren bir [dönüş deyimi](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a619b-107">Include the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
-   <span data-ttu-id="a619b-108">Değer atadığınız `Function` yordamı adlandırın ve ardından gerçekleştirmek bir `Exit Function` deyimi.</span><span class="sxs-lookup"><span data-stu-id="a619b-108">Assign the value to the `Function` procedure name and then perform an `Exit Function` statement.</span></span>  
  
-   <span data-ttu-id="a619b-109">Değer atadığınız `Function` yordamı adlandırın ve ardından gerçekleştirmek `End Function` deyimi.</span><span class="sxs-lookup"><span data-stu-id="a619b-109">Assign the value to the `Function` procedure name and then perform the `End Function` statement.</span></span>  
  
 <span data-ttu-id="a619b-110">Denetim geçirir, `Exit Function` veya `End Function` ve yordam adı herhangi bir değer atamadıysanız, yordamı dönüş verisi türüne varsayılan değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="a619b-110">If control passes to `Exit Function` or `End Function` and you have not assigned any value to the procedure name, the procedure returns the default value of the return data type.</span></span> <span data-ttu-id="a619b-111">Daha fazla bilgi için bkz: "Davranışı" [Function deyimi](../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a619b-111">For more information, see "Behavior" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="a619b-112">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="a619b-112">By default, this message is a warning.</span></span> <span data-ttu-id="a619b-113">Uyarıları gizleme veya uyarıları hata olarak davranma daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="a619b-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="a619b-114">**Hata Kimliği:** BC42105</span><span class="sxs-lookup"><span data-stu-id="a619b-114">**Error ID:** BC42105</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a619b-115">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="a619b-115">To correct this error</span></span>  
  
-   <span data-ttu-id="a619b-116">Denetim akışı mantığınızı denetleyin ve satır başı neden olan her deyimi önce bir değer atadığınız emin olun.</span><span class="sxs-lookup"><span data-stu-id="a619b-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>  
  
     <span data-ttu-id="a619b-117">Her zaman kullanıyorsanız her return yordamdan bir değer döndürür güvence altına almak daha kolay `Return` deyimi.</span><span class="sxs-lookup"><span data-stu-id="a619b-117">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="a619b-118">Bu, son deyim önce yaparsanız `End Function` olması gereken bir `Return` deyimi.</span><span class="sxs-lookup"><span data-stu-id="a619b-118">If you do this, the last statement before `End Function` should be a `Return` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a619b-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a619b-119">See Also</span></span>  
 [<span data-ttu-id="a619b-120">İşlev yordamları</span><span class="sxs-lookup"><span data-stu-id="a619b-120">Function Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)  
 [<span data-ttu-id="a619b-121">Function deyimi</span><span class="sxs-lookup"><span data-stu-id="a619b-121">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="a619b-122">Derle sayfası, Proje Tasarımcısı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a619b-122">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
