---
description: 'Daha fazla bilgi edinin: özgeçmişi ekstresi'
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
ms.openlocfilehash: fd3a02fc2606355d7e3a34f5c0d69eef577809de
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741191"
---
# <a name="resume-statement"></a><span data-ttu-id="30f53-103">Resume Deyimi</span><span class="sxs-lookup"><span data-stu-id="30f53-103">Resume Statement</span></span>

<span data-ttu-id="30f53-104">Bir hata işleme yordamı tamamlandıktan sonra yürütmeyi sürdürür.</span><span class="sxs-lookup"><span data-stu-id="30f53-104">Resumes execution after an error-handling routine is finished.</span></span>  
  
 <span data-ttu-id="30f53-105">Yapılandırılmamış özel durum işleme ve ve deyimlerini kullanmak yerine kodunuzda yapılandırılmış özel durum işlemeyi kullanmanızı öneririz `On Error` `Resume` .</span><span class="sxs-lookup"><span data-stu-id="30f53-105">We suggest that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="30f53-106">Daha fazla bilgi için bkz [. TRY... Yakala... Finally ekstresi](try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="30f53-106">For more information, see [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30f53-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="30f53-107">Syntax</span></span>  
  
```vb  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a><span data-ttu-id="30f53-108">Bölümler</span><span class="sxs-lookup"><span data-stu-id="30f53-108">Parts</span></span>  

 `Resume`  
 <span data-ttu-id="30f53-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="30f53-109">Required.</span></span> <span data-ttu-id="30f53-110">Hata işleyicisiyle aynı yordamda hata oluştuysa, yürütme hataya neden olan deyimle devam eder.</span><span class="sxs-lookup"><span data-stu-id="30f53-110">If the error occurred in the same procedure as the error handler, execution resumes with the statement that caused the error.</span></span> <span data-ttu-id="30f53-111">Çağrılan yordamda hata oluştuysa, yürütme son çağrılan ve hata işleme yordamını içeren yordamın dışında devam eden ifadede sürdürülür.</span><span class="sxs-lookup"><span data-stu-id="30f53-111">If the error occurred in a called procedure, execution resumes at the statement that last called out of the procedure containing the error-handling routine.</span></span>  
  
 `Next`  
 <span data-ttu-id="30f53-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="30f53-112">Optional.</span></span> <span data-ttu-id="30f53-113">Hata işleyicisiyle aynı yordamda hata oluştuysa, yürütme hataya neden olan deyimin hemen ardından gelen ifadesiyle devam eder.</span><span class="sxs-lookup"><span data-stu-id="30f53-113">If the error occurred in the same procedure as the error handler, execution resumes with the statement immediately following the statement that caused the error.</span></span> <span data-ttu-id="30f53-114">Çağrılan yordamda hata oluştuysa, yürütme, hata işleme yordamını (veya ifadesini) içeren yordamın en son çağrıldığı deyimin hemen sonrasında ifadesiyle devam eder `On Error Resume Next` .</span><span class="sxs-lookup"><span data-stu-id="30f53-114">If the error occurred in a called procedure, execution resumes with the statement immediately following the statement that last called out of the procedure containing the error-handling routine (or `On Error Resume Next` statement).</span></span>  
  
 `line`  
 <span data-ttu-id="30f53-115">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="30f53-115">Optional.</span></span> <span data-ttu-id="30f53-116">Yürütme, gerekli bağımsız değişkende belirtilen satırda sürdürülür `line` .</span><span class="sxs-lookup"><span data-stu-id="30f53-116">Execution resumes at the line specified in the required `line` argument.</span></span> <span data-ttu-id="30f53-117">`line`Bağımsız değişken bir satır etiketi veya satır numarasıdır ve hata işleyicisiyle aynı yordamda olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="30f53-117">The `line` argument is a line label or line number and must be in the same procedure as the error handler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30f53-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="30f53-118">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="30f53-119">Yapılandırılmamış özel durum işleme ve ve deyimlerini kullanmak yerine kodunuzda yapılandırılmış özel durum işlemeyi kullanmanızı öneririz `On Error` `Resume` .</span><span class="sxs-lookup"><span data-stu-id="30f53-119">We recommend that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="30f53-120">Daha fazla bilgi için bkz [. TRY... Yakala... Finally ekstresi](try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="30f53-120">For more information, see [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span></span>  
  
 <span data-ttu-id="30f53-121">Bir `Resume` ifadeyi hata işleme yordamında dışında bir yerde kullanıyorsanız bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="30f53-121">If you use a `Resume` statement anywhere other than in an error-handling routine, an error occurs.</span></span>  
  
 <span data-ttu-id="30f53-122">`Resume`İfade, bir ifade içeren herhangi bir yordamda kullanılamaz `Try...Catch...Finally` .</span><span class="sxs-lookup"><span data-stu-id="30f53-122">The `Resume` statement cannot be used in any procedure that contains a `Try...Catch...Finally` statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30f53-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="30f53-123">Example</span></span>  

 <span data-ttu-id="30f53-124">Bu örnek, `Resume` bir yordamda hata işlemeyi sonlandırmak için ifadesini kullanır ve ardından hataya neden olan deyimle yürütmeyi sürdürür.</span><span class="sxs-lookup"><span data-stu-id="30f53-124">This example uses the `Resume` statement to end error handling in a procedure and then resume execution with the statement that caused the error.</span></span> <span data-ttu-id="30f53-125">Deyimin kullanımını göstermek için 55 hata numarası oluşturulur `Resume` .</span><span class="sxs-lookup"><span data-stu-id="30f53-125">Error number 55 is generated to illustrate use of the `Resume` statement.</span></span>  
  
 [!code-vb[VbVbalrErrorHandling#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#16)]  
  
## <a name="requirements"></a><span data-ttu-id="30f53-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="30f53-126">Requirements</span></span>  

 <span data-ttu-id="30f53-127">**Ad alanı:** [Microsoft. VisualBasic](../runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="30f53-127">**Namespace:** [Microsoft.VisualBasic](../runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="30f53-128">**Bütünleştirilmiş kod:** Visual Basic çalışma zamanı kitaplığı (Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="30f53-128">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30f53-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30f53-129">See also</span></span>

- [<span data-ttu-id="30f53-130">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="30f53-130">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
- [<span data-ttu-id="30f53-131">Error Deyimi</span><span class="sxs-lookup"><span data-stu-id="30f53-131">Error Statement</span></span>](error-statement.md)
- [<span data-ttu-id="30f53-132">On Error Deyimi</span><span class="sxs-lookup"><span data-stu-id="30f53-132">On Error Statement</span></span>](on-error-statement.md)
