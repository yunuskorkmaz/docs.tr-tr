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
ms.openlocfilehash: db9d47798d087d60f4318b06fe3291fb895e6618
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871876"
---
# <a name="resume-statement"></a><span data-ttu-id="8ee54-102">Resume Deyimi</span><span class="sxs-lookup"><span data-stu-id="8ee54-102">Resume Statement</span></span>

<span data-ttu-id="8ee54-103">Bir hata işleme yordamı tamamlandıktan sonra yürütmeyi sürdürür.</span><span class="sxs-lookup"><span data-stu-id="8ee54-103">Resumes execution after an error-handling routine is finished.</span></span>  
  
 <span data-ttu-id="8ee54-104">Yapılandırılmamış özel durum işleme ve ve deyimlerini kullanmak yerine kodunuzda yapılandırılmış özel durum işlemeyi kullanmanızı öneririz `On Error` `Resume` .</span><span class="sxs-lookup"><span data-stu-id="8ee54-104">We suggest that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="8ee54-105">Daha fazla bilgi için bkz [. TRY... Yakala... Finally ekstresi](try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8ee54-105">For more information, see [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ee54-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8ee54-106">Syntax</span></span>  
  
```vb  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a><span data-ttu-id="8ee54-107">Bölümler</span><span class="sxs-lookup"><span data-stu-id="8ee54-107">Parts</span></span>  

 `Resume`  
 <span data-ttu-id="8ee54-108">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8ee54-108">Required.</span></span> <span data-ttu-id="8ee54-109">Hata işleyicisiyle aynı yordamda hata oluştuysa, yürütme hataya neden olan deyimle devam eder.</span><span class="sxs-lookup"><span data-stu-id="8ee54-109">If the error occurred in the same procedure as the error handler, execution resumes with the statement that caused the error.</span></span> <span data-ttu-id="8ee54-110">Çağrılan yordamda hata oluştuysa, yürütme son çağrılan ve hata işleme yordamını içeren yordamın dışında devam eden ifadede sürdürülür.</span><span class="sxs-lookup"><span data-stu-id="8ee54-110">If the error occurred in a called procedure, execution resumes at the statement that last called out of the procedure containing the error-handling routine.</span></span>  
  
 `Next`  
 <span data-ttu-id="8ee54-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="8ee54-111">Optional.</span></span> <span data-ttu-id="8ee54-112">Hata işleyicisiyle aynı yordamda hata oluştuysa, yürütme hataya neden olan deyimin hemen ardından gelen ifadesiyle devam eder.</span><span class="sxs-lookup"><span data-stu-id="8ee54-112">If the error occurred in the same procedure as the error handler, execution resumes with the statement immediately following the statement that caused the error.</span></span> <span data-ttu-id="8ee54-113">Çağrılan yordamda hata oluştuysa, yürütme, hata işleme yordamını (veya ifadesini) içeren yordamın en son çağrıldığı deyimin hemen sonrasında ifadesiyle devam eder `On Error Resume Next` .</span><span class="sxs-lookup"><span data-stu-id="8ee54-113">If the error occurred in a called procedure, execution resumes with the statement immediately following the statement that last called out of the procedure containing the error-handling routine (or `On Error Resume Next` statement).</span></span>  
  
 `line`  
 <span data-ttu-id="8ee54-114">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="8ee54-114">Optional.</span></span> <span data-ttu-id="8ee54-115">Yürütme, gerekli bağımsız değişkende belirtilen satırda sürdürülür `line` .</span><span class="sxs-lookup"><span data-stu-id="8ee54-115">Execution resumes at the line specified in the required `line` argument.</span></span> <span data-ttu-id="8ee54-116">`line`Bağımsız değişken bir satır etiketi veya satır numarasıdır ve hata işleyicisiyle aynı yordamda olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8ee54-116">The `line` argument is a line label or line number and must be in the same procedure as the error handler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ee54-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8ee54-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8ee54-118">Yapılandırılmamış özel durum işleme ve ve deyimlerini kullanmak yerine kodunuzda yapılandırılmış özel durum işlemeyi kullanmanızı öneririz `On Error` `Resume` .</span><span class="sxs-lookup"><span data-stu-id="8ee54-118">We recommend that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="8ee54-119">Daha fazla bilgi için bkz [. TRY... Yakala... Finally ekstresi](try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8ee54-119">For more information, see [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span></span>  
  
 <span data-ttu-id="8ee54-120">Bir `Resume` ifadeyi hata işleme yordamında dışında bir yerde kullanıyorsanız bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="8ee54-120">If you use a `Resume` statement anywhere other than in an error-handling routine, an error occurs.</span></span>  
  
 <span data-ttu-id="8ee54-121">`Resume`İfade, bir ifade içeren herhangi bir yordamda kullanılamaz `Try...Catch...Finally` .</span><span class="sxs-lookup"><span data-stu-id="8ee54-121">The `Resume` statement cannot be used in any procedure that contains a `Try...Catch...Finally` statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ee54-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="8ee54-122">Example</span></span>  

 <span data-ttu-id="8ee54-123">Bu örnek, `Resume` bir yordamda hata işlemeyi sonlandırmak için ifadesini kullanır ve ardından hataya neden olan deyimle yürütmeyi sürdürür.</span><span class="sxs-lookup"><span data-stu-id="8ee54-123">This example uses the `Resume` statement to end error handling in a procedure and then resume execution with the statement that caused the error.</span></span> <span data-ttu-id="8ee54-124">Deyimin kullanımını göstermek için 55 hata numarası oluşturulur `Resume` .</span><span class="sxs-lookup"><span data-stu-id="8ee54-124">Error number 55 is generated to illustrate use of the `Resume` statement.</span></span>  
  
 [!code-vb[VbVbalrErrorHandling#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#16)]  
  
## <a name="requirements"></a><span data-ttu-id="8ee54-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8ee54-125">Requirements</span></span>  

 <span data-ttu-id="8ee54-126">**Ad alanı:** [Microsoft. VisualBasic](../runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="8ee54-126">**Namespace:** [Microsoft.VisualBasic](../runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="8ee54-127">**Bütünleştirilmiş kod:** Visual Basic çalışma zamanı kitaplığı (Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="8ee54-127">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ee54-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ee54-128">See also</span></span>

- [<span data-ttu-id="8ee54-129">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="8ee54-129">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
- [<span data-ttu-id="8ee54-130">Error Deyimi</span><span class="sxs-lookup"><span data-stu-id="8ee54-130">Error Statement</span></span>](error-statement.md)
- [<span data-ttu-id="8ee54-131">On Error Deyimi</span><span class="sxs-lookup"><span data-stu-id="8ee54-131">On Error Statement</span></span>](on-error-statement.md)
