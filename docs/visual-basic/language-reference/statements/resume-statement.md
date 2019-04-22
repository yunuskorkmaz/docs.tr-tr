---
title: Resume deyimi (Visual Basic)
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
ms.openlocfilehash: 796342d17b0d0f1a642aff381274746d1fda3559
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58816453"
---
# <a name="resume-statement"></a><span data-ttu-id="3af64-102">Resume Deyimi</span><span class="sxs-lookup"><span data-stu-id="3af64-102">Resume Statement</span></span>
<span data-ttu-id="3af64-103">Bir hata işleme yordamını tamamlandıktan sonra yürütmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="3af64-103">Resumes execution after an error-handling routine is finished.</span></span>  
  
 <span data-ttu-id="3af64-104">Yapılandırılmamış özel durum işleme kullanmak yerine, mümkün olduğunda, kodunuzda yapılandırılmış özel durum işleme kullanmanızı öneririz ve `On Error` ve `Resume` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="3af64-104">We suggest that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="3af64-105">Daha fazla bilgi için [deneyin... Catch... Finally deyimini](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3af64-105">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3af64-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3af64-106">Syntax</span></span>  
  
```  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a><span data-ttu-id="3af64-107">Bölümler</span><span class="sxs-lookup"><span data-stu-id="3af64-107">Parts</span></span>  
 `Resume`  
 <span data-ttu-id="3af64-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="3af64-108">Required.</span></span> <span data-ttu-id="3af64-109">Hata işleyicisi aynı yordam içinde hata oluştu, hataya neden olan deyim yürütmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="3af64-109">If the error occurred in the same procedure as the error handler, execution resumes with the statement that caused the error.</span></span> <span data-ttu-id="3af64-110">Çağrılan bir yordamda hata oluştuysa, son hata işleme yordamını içeren yordam dışında adlı deyimindeki yürütmeyi devam ettirir.</span><span class="sxs-lookup"><span data-stu-id="3af64-110">If the error occurred in a called procedure, execution resumes at the statement that last called out of the procedure containing the error-handling routine.</span></span>  
  
 `Next`  
 <span data-ttu-id="3af64-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3af64-111">Optional.</span></span> <span data-ttu-id="3af64-112">Hata işleyicisi aynı yordam içinde hata oluştu, yürütme hemen bir hataya yol açmayan deyiminin sonrasındaki deyime ile devam eder.</span><span class="sxs-lookup"><span data-stu-id="3af64-112">If the error occurred in the same procedure as the error handler, execution resumes with the statement immediately following the statement that caused the error.</span></span> <span data-ttu-id="3af64-113">Adlı bir yordamda hata oluştuysa, hemen en son hata işleme yordamını içeren yordam dışında çağrılan deyiminin sonrasındaki deyime ile yürütme sürdürür (veya `On Error Resume Next` deyimi).</span><span class="sxs-lookup"><span data-stu-id="3af64-113">If the error occurred in a called procedure, execution resumes with the statement immediately following the statement that last called out of the procedure containing the error-handling routine (or `On Error Resume Next` statement).</span></span>  
  
 `line`  
 <span data-ttu-id="3af64-114">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3af64-114">Optional.</span></span> <span data-ttu-id="3af64-115">Yürütmeye devam eder gerekli belirtilen satır `line` bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="3af64-115">Execution resumes at the line specified in the required `line` argument.</span></span> <span data-ttu-id="3af64-116">`line` Bağımsız değişkeni bir satır etiket ya da satır numarasını ve hata işleyicisini aynı yordam içinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3af64-116">The `line` argument is a line label or line number and must be in the same procedure as the error handler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3af64-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3af64-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3af64-118">Yapılandırılmamış özel durum işleme kullanmak yerine, mümkün olduğunda, kodunuzda yapılandırılmış özel durum işleme kullanmanızı öneririz ve `On Error` ve `Resume` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="3af64-118">We recommend that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="3af64-119">Daha fazla bilgi için [deneyin... Catch... Finally deyimini](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3af64-119">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
 <span data-ttu-id="3af64-120">Kullanıyorsanız bir `Resume` deyiminde herhangi bir yere dışında bir hata işleme yordamı, bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="3af64-120">If you use a `Resume` statement anywhere other than in an error-handling routine, an error occurs.</span></span>  
  
 <span data-ttu-id="3af64-121">`Resume` Deyimi içeren herhangi bir yordamda kullanılamaz bir `Try...Catch...Finally` deyimi.</span><span class="sxs-lookup"><span data-stu-id="3af64-121">The `Resume` statement cannot be used in any procedure that contains a `Try...Catch...Finally` statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3af64-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="3af64-122">Example</span></span>  
 <span data-ttu-id="3af64-123">Bu örnekte `Resume` hata bir yordamda işleme ve sonra da hataya neden deyimi yürütme devam deyimi.</span><span class="sxs-lookup"><span data-stu-id="3af64-123">This example uses the `Resume` statement to end error handling in a procedure and then resume execution with the statement that caused the error.</span></span> <span data-ttu-id="3af64-124">Hata numarası 55 kullanımını göstermek için oluşturulan `Resume` deyimi.</span><span class="sxs-lookup"><span data-stu-id="3af64-124">Error number 55 is generated to illustrate use of the `Resume` statement.</span></span>  
  
 [!code-vb[VbVbalrErrorHandling#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#16)]  
  
## <a name="requirements"></a><span data-ttu-id="3af64-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3af64-125">Requirements</span></span>  
 <span data-ttu-id="3af64-126">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="3af64-126">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="3af64-127">**Derleme:** Visual Basic Çalışma Zamanı Kitaplığı (Microsoft.VisualBasic.dll içinde)</span><span class="sxs-lookup"><span data-stu-id="3af64-127">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3af64-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3af64-128">See also</span></span>

- [<span data-ttu-id="3af64-129">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="3af64-129">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="3af64-130">Error Deyimi</span><span class="sxs-lookup"><span data-stu-id="3af64-130">Error Statement</span></span>](../../../visual-basic/language-reference/statements/error-statement.md)
- [<span data-ttu-id="3af64-131">On Error Deyimi</span><span class="sxs-lookup"><span data-stu-id="3af64-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
