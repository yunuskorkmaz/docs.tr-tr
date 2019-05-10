---
title: "'<procedurename>' işlevi tüm kod yollarında değer döndürmüyor"
ms.date: 07/20/2015
f1_keywords:
- bc42105
- vbc42105
helpviewer_keywords:
- BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
ms.openlocfilehash: 5564f95048f6b44a48229c7e5be9331839803439
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662097"
---
# <a name="function-procedurename-doesnt-return-a-value-on-all-code-paths"></a><span data-ttu-id="fb982-102">İşlev '\<procedurename >' bütün kod yollarında değer döndürmüyor</span><span class="sxs-lookup"><span data-stu-id="fb982-102">Function '\<procedurename>' doesn't return a value on all code paths</span></span>
<span data-ttu-id="fb982-103">İşlev '\<procedurename >' bütün kod yollarında değer döndürmüyor.</span><span class="sxs-lookup"><span data-stu-id="fb982-103">Function '\<procedurename>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="fb982-104">'Return' deyiminiz eksik olabilir mi?</span><span class="sxs-lookup"><span data-stu-id="fb982-104">Are you missing a 'Return' statement?</span></span>  
  
 <span data-ttu-id="fb982-105">A `Function` yordamının bir değer döndürmeyen kendi kod aracılığıyla en az bir olası yol vardır.</span><span class="sxs-lookup"><span data-stu-id="fb982-105">A `Function` procedure has at least one possible path through its code that does not return a value.</span></span>  
  
 <span data-ttu-id="fb982-106">Bir değer döndürmek bir `Function` aşağıdaki yollardan biriyle yordamda:</span><span class="sxs-lookup"><span data-stu-id="fb982-106">You can return a value from a `Function` procedure in any of the following ways:</span></span>  
  
- <span data-ttu-id="fb982-107">Değer bir [dönüş deyimi](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fb982-107">Include the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
- <span data-ttu-id="fb982-108">Değer atayın `Function` yordamı adlandırın ve ardından gerçekleştirmek bir `Exit Function` deyimi.</span><span class="sxs-lookup"><span data-stu-id="fb982-108">Assign the value to the `Function` procedure name and then perform an `Exit Function` statement.</span></span>  
  
- <span data-ttu-id="fb982-109">Değer atayın `Function` yordamı adlandırın ve ardından gerçekleştirmek `End Function` deyimi.</span><span class="sxs-lookup"><span data-stu-id="fb982-109">Assign the value to the `Function` procedure name and then perform the `End Function` statement.</span></span>  
  
 <span data-ttu-id="fb982-110">Denetim için geçerse `Exit Function` veya `End Function` ve yordam adı için herhangi bir değer atamadıysanız, yordamın dönüş veri türünün varsayılan değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="fb982-110">If control passes to `Exit Function` or `End Function` and you have not assigned any value to the procedure name, the procedure returns the default value of the return data type.</span></span> <span data-ttu-id="fb982-111">Daha fazla bilgi için "Davranışı" bölümüne bakın. [Function deyimi](../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fb982-111">For more information, see "Behavior" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="fb982-112">Varsayılan olarak, bu iletiyi bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="fb982-112">By default, this message is a warning.</span></span> <span data-ttu-id="fb982-113">Uyarıları gizleme veya uyarıları hata olarak değerlendirmesini daha fazla bilgi için bkz: [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="fb982-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="fb982-114">**Hata Kimliği:** BC42105</span><span class="sxs-lookup"><span data-stu-id="fb982-114">**Error ID:** BC42105</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fb982-115">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="fb982-115">To correct this error</span></span>  
  
- <span data-ttu-id="fb982-116">Denetim akışı mantığınızı denetleyin ve bir dönüş neden her deyiminden önce bir değer atadığınız emin olun.</span><span class="sxs-lookup"><span data-stu-id="fb982-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>  
  
     <span data-ttu-id="fb982-117">Her zaman kullanırsanız her iade yordamdan gelen bir değer döndürür garanti daha kolaydır `Return` deyimi.</span><span class="sxs-lookup"><span data-stu-id="fb982-117">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="fb982-118">Bu, son deyim önce yaparsanız `End Function` olmalıdır bir `Return` deyimi.</span><span class="sxs-lookup"><span data-stu-id="fb982-118">If you do this, the last statement before `End Function` should be a `Return` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb982-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb982-119">See also</span></span>

- [<span data-ttu-id="fb982-120">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="fb982-120">Function Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)
- [<span data-ttu-id="fb982-121">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="fb982-121">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="fb982-122">Derleme Sayfası, Proje Tasarımcısı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fb982-122">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
