---
title: Özgeçmişi ekstresi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Resume
- vb.ResumeNext
helpviewer_keywords:
- Next statement [Visual Basic], Resume
- Resume Next statement [Visual Basic]
- execution [Visual Basic], resuming
- run-time errors [Visual Basic], resuming after
- Resume statement [Visual Basic], syntax
- errors [Visual Basic], resuming after
- Error statement [Visual Basic], and Resume statement
- execution
- Resume statement [Visual Basic]
ms.assetid: e24d058b-1a5c-4274-acb9-7d295d3ea537
ms.openlocfilehash: 7b8c2e123c04ff9720d690507ee41a6b52f40c3f
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583270"
---
# <a name="resume-statement"></a><span data-ttu-id="69d09-102">Resume Deyimi</span><span class="sxs-lookup"><span data-stu-id="69d09-102">Resume Statement</span></span>
<span data-ttu-id="69d09-103">Bir hata işleme yordamı tamamlandıktan sonra yürütmeyi sürdürür.</span><span class="sxs-lookup"><span data-stu-id="69d09-103">Resumes execution after an error-handling routine is finished.</span></span>  
  
 <span data-ttu-id="69d09-104">Yapılandırılmamış özel durum işleme ve `On Error` ve `Resume` deyimlerini kullanmak yerine kodunuzda yapılandırılmış özel durum işlemeyi kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="69d09-104">We suggest that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="69d09-105">Daha fazla bilgi için bkz [. TRY... Yakala... Finally ekstresi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="69d09-105">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69d09-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="69d09-106">Syntax</span></span>  
  
```vb  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a><span data-ttu-id="69d09-107">Bölümler</span><span class="sxs-lookup"><span data-stu-id="69d09-107">Parts</span></span>  
 `Resume`  
 <span data-ttu-id="69d09-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="69d09-108">Required.</span></span> <span data-ttu-id="69d09-109">Hata işleyicisiyle aynı yordamda hata oluştuysa, yürütme hataya neden olan deyimle devam eder.</span><span class="sxs-lookup"><span data-stu-id="69d09-109">If the error occurred in the same procedure as the error handler, execution resumes with the statement that caused the error.</span></span> <span data-ttu-id="69d09-110">Çağrılan yordamda hata oluştuysa, yürütme son çağrılan ve hata işleme yordamını içeren yordamın dışında devam eden ifadede sürdürülür.</span><span class="sxs-lookup"><span data-stu-id="69d09-110">If the error occurred in a called procedure, execution resumes at the statement that last called out of the procedure containing the error-handling routine.</span></span>  
  
 `Next`  
 <span data-ttu-id="69d09-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="69d09-111">Optional.</span></span> <span data-ttu-id="69d09-112">Hata işleyicisiyle aynı yordamda hata oluştuysa, yürütme hataya neden olan deyimin hemen ardından gelen ifadesiyle devam eder.</span><span class="sxs-lookup"><span data-stu-id="69d09-112">If the error occurred in the same procedure as the error handler, execution resumes with the statement immediately following the statement that caused the error.</span></span> <span data-ttu-id="69d09-113">Çağrılan yordamda hata oluştuysa, yürütme, hata işleme yordamını (veya `On Error Resume Next` ifadesini) içeren yordamın en son çağrıldığı deyimden hemen sonra gelen deyimle devam eder.</span><span class="sxs-lookup"><span data-stu-id="69d09-113">If the error occurred in a called procedure, execution resumes with the statement immediately following the statement that last called out of the procedure containing the error-handling routine (or `On Error Resume Next` statement).</span></span>  
  
 `line`  
 <span data-ttu-id="69d09-114">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="69d09-114">Optional.</span></span> <span data-ttu-id="69d09-115">Yürütme, gerekli `line` bağımsız değişkeninde belirtilen satırda sürdürülür.</span><span class="sxs-lookup"><span data-stu-id="69d09-115">Execution resumes at the line specified in the required `line` argument.</span></span> <span data-ttu-id="69d09-116">@No__t_0 bağımsız değişkeni bir çizgi etiketi veya satır numarasıdır ve hata işleyicisiyle aynı yordamda olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="69d09-116">The `line` argument is a line label or line number and must be in the same procedure as the error handler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69d09-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="69d09-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="69d09-118">Yapılandırılmamış özel durum işleme ve `On Error` ve `Resume` deyimlerini kullanmak yerine kodunuzda yapılandırılmış özel durum işlemeyi kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="69d09-118">We recommend that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="69d09-119">Daha fazla bilgi için bkz [. TRY... Yakala... Finally ekstresi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="69d09-119">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
 <span data-ttu-id="69d09-120">Hata işleme yordamında dışında herhangi bir yerde `Resume` ifadesini kullanıyorsanız bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="69d09-120">If you use a `Resume` statement anywhere other than in an error-handling routine, an error occurs.</span></span>  
  
 <span data-ttu-id="69d09-121">@No__t_0 deyimleri `Try...Catch...Finally` bir ifade içeren herhangi bir yordamda kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="69d09-121">The `Resume` statement cannot be used in any procedure that contains a `Try...Catch...Finally` statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69d09-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="69d09-122">Example</span></span>  
 <span data-ttu-id="69d09-123">Bu örnek, bir yordamdaki hata işlemeyi sonlandırmak için `Resume` ifadesini kullanır ve ardından hataya neden olan deyimle yürütmeyi sürdürür.</span><span class="sxs-lookup"><span data-stu-id="69d09-123">This example uses the `Resume` statement to end error handling in a procedure and then resume execution with the statement that caused the error.</span></span> <span data-ttu-id="69d09-124">@No__t_0 deyimin kullanımını göstermek için 55 hata numarası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="69d09-124">Error number 55 is generated to illustrate use of the `Resume` statement.</span></span>  
  
 [!code-vb[VbVbalrErrorHandling#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#16)]  
  
## <a name="requirements"></a><span data-ttu-id="69d09-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="69d09-125">Requirements</span></span>  
 <span data-ttu-id="69d09-126">**Ad alanı:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="69d09-126">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="69d09-127">**Bütünleştirilmiş kod:** Visual Basic çalışma zamanı kitaplığı (Microsoft. VisualBasic. dll içinde)</span><span class="sxs-lookup"><span data-stu-id="69d09-127">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69d09-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69d09-128">See also</span></span>

- [<span data-ttu-id="69d09-129">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="69d09-129">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="69d09-130">Error Deyimi</span><span class="sxs-lookup"><span data-stu-id="69d09-130">Error Statement</span></span>](../../../visual-basic/language-reference/statements/error-statement.md)
- [<span data-ttu-id="69d09-131">On Error Deyimi</span><span class="sxs-lookup"><span data-stu-id="69d09-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
