---
title: Resume Deyimi
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
ms.openlocfilehash: 95137a9f6a4a4a18655b51b95300bfaf93cca193
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333024"
---
# <a name="resume-statement"></a><span data-ttu-id="91813-102">Resume Deyimi</span><span class="sxs-lookup"><span data-stu-id="91813-102">Resume Statement</span></span>
<span data-ttu-id="91813-103">Bir hata işleme yordamı tamamlandıktan sonra yürütmeyi sürdürür.</span><span class="sxs-lookup"><span data-stu-id="91813-103">Resumes execution after an error-handling routine is finished.</span></span>  
  
 <span data-ttu-id="91813-104">Yapılandırılmamış özel durum işleme ve `On Error` ve `Resume` deyimlerini kullanmak yerine kodunuzda yapılandırılmış özel durum işlemeyi kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="91813-104">We suggest that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="91813-105">Daha fazla bilgi için bkz [. TRY... Yakala... Finally ekstresi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="91813-105">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91813-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="91813-106">Syntax</span></span>  
  
```vb  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a><span data-ttu-id="91813-107">Bölümler</span><span class="sxs-lookup"><span data-stu-id="91813-107">Parts</span></span>  
 `Resume`  
 <span data-ttu-id="91813-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="91813-108">Required.</span></span> <span data-ttu-id="91813-109">Hata işleyicisiyle aynı yordamda hata oluştuysa, yürütme hataya neden olan deyimle devam eder.</span><span class="sxs-lookup"><span data-stu-id="91813-109">If the error occurred in the same procedure as the error handler, execution resumes with the statement that caused the error.</span></span> <span data-ttu-id="91813-110">Çağrılan yordamda hata oluştuysa, yürütme son çağrılan ve hata işleme yordamını içeren yordamın dışında devam eden ifadede sürdürülür.</span><span class="sxs-lookup"><span data-stu-id="91813-110">If the error occurred in a called procedure, execution resumes at the statement that last called out of the procedure containing the error-handling routine.</span></span>  
  
 `Next`  
 <span data-ttu-id="91813-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="91813-111">Optional.</span></span> <span data-ttu-id="91813-112">Hata işleyicisiyle aynı yordamda hata oluştuysa, yürütme hataya neden olan deyimin hemen ardından gelen ifadesiyle devam eder.</span><span class="sxs-lookup"><span data-stu-id="91813-112">If the error occurred in the same procedure as the error handler, execution resumes with the statement immediately following the statement that caused the error.</span></span> <span data-ttu-id="91813-113">Çağrılan yordamda hata oluştuysa, yürütme, hata işleme yordamını (veya `On Error Resume Next` ifadesini) içeren yordamın en son çağrıldığı deyimden hemen sonra gelen deyimle devam eder.</span><span class="sxs-lookup"><span data-stu-id="91813-113">If the error occurred in a called procedure, execution resumes with the statement immediately following the statement that last called out of the procedure containing the error-handling routine (or `On Error Resume Next` statement).</span></span>  
  
 `line`  
 <span data-ttu-id="91813-114">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="91813-114">Optional.</span></span> <span data-ttu-id="91813-115">Yürütme, gerekli `line` bağımsız değişkeninde belirtilen satırda sürdürülür.</span><span class="sxs-lookup"><span data-stu-id="91813-115">Execution resumes at the line specified in the required `line` argument.</span></span> <span data-ttu-id="91813-116">`line` bağımsız değişkeni bir çizgi etiketi veya satır numarasıdır ve hata işleyicisiyle aynı yordamda olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="91813-116">The `line` argument is a line label or line number and must be in the same procedure as the error handler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91813-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="91813-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="91813-118">Yapılandırılmamış özel durum işleme ve `On Error` ve `Resume` deyimlerini kullanmak yerine kodunuzda yapılandırılmış özel durum işlemeyi kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="91813-118">We recommend that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="91813-119">Daha fazla bilgi için bkz [. TRY... Yakala... Finally ekstresi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="91813-119">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
 <span data-ttu-id="91813-120">Hata işleme yordamında dışında herhangi bir yerde `Resume` ifadesini kullanıyorsanız bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="91813-120">If you use a `Resume` statement anywhere other than in an error-handling routine, an error occurs.</span></span>  
  
 <span data-ttu-id="91813-121">`Resume` deyimleri `Try...Catch...Finally` bir ifade içeren herhangi bir yordamda kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="91813-121">The `Resume` statement cannot be used in any procedure that contains a `Try...Catch...Finally` statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91813-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="91813-122">Example</span></span>  
 <span data-ttu-id="91813-123">Bu örnek, bir yordamdaki hata işlemeyi sonlandırmak için `Resume` ifadesini kullanır ve ardından hataya neden olan deyimle yürütmeyi sürdürür.</span><span class="sxs-lookup"><span data-stu-id="91813-123">This example uses the `Resume` statement to end error handling in a procedure and then resume execution with the statement that caused the error.</span></span> <span data-ttu-id="91813-124">`Resume` deyimin kullanımını göstermek için 55 hata numarası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="91813-124">Error number 55 is generated to illustrate use of the `Resume` statement.</span></span>  
  
 [!code-vb[VbVbalrErrorHandling#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#16)]  
  
## <a name="requirements"></a><span data-ttu-id="91813-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="91813-125">Requirements</span></span>  
 <span data-ttu-id="91813-126">**Ad alanı:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="91813-126">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="91813-127">**Bütünleştirilmiş kod:** Visual Basic çalışma zamanı kitaplığı (Microsoft. VisualBasic. dll içinde)</span><span class="sxs-lookup"><span data-stu-id="91813-127">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91813-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91813-128">See also</span></span>

- [<span data-ttu-id="91813-129">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="91813-129">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="91813-130">Error Deyimi</span><span class="sxs-lookup"><span data-stu-id="91813-130">Error Statement</span></span>](../../../visual-basic/language-reference/statements/error-statement.md)
- [<span data-ttu-id="91813-131">On Error Deyimi</span><span class="sxs-lookup"><span data-stu-id="91813-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
