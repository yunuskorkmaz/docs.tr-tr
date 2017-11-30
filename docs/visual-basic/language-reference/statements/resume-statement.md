---
title: Resume Deyimi
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3cb4334f302c07c81b6b8a7d0626be08cc69b1ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="resume-statement"></a><span data-ttu-id="6d412-102">Resume Deyimi</span><span class="sxs-lookup"><span data-stu-id="6d412-102">Resume Statement</span></span>
<span data-ttu-id="6d412-103">Hata işleme yordamı tamamladıktan sonra yürütme devam ettirir.</span><span class="sxs-lookup"><span data-stu-id="6d412-103">Resumes execution after an error-handling routine is finished.</span></span>  
  
 <span data-ttu-id="6d412-104">Yapılandırılmamış özel durum işleme kullanmak yerine, mümkün olduğunda, kodunuzda yapılandırılmış özel durum işleme kullanmanızı öneririz ve `On Error` ve `Resume` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="6d412-104">We suggest that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="6d412-105">Daha fazla bilgi için bkz: [deneyin... Catch... Finally ifadesi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6d412-105">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d412-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6d412-106">Syntax</span></span>  
  
```  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a><span data-ttu-id="6d412-107">Bölümler</span><span class="sxs-lookup"><span data-stu-id="6d412-107">Parts</span></span>  
 `Resume`  
 <span data-ttu-id="6d412-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="6d412-108">Required.</span></span> <span data-ttu-id="6d412-109">Yordamın aynısını hata işleyicisine hata oluştu, yürütme hataya deyimiyle devam ettirir.</span><span class="sxs-lookup"><span data-stu-id="6d412-109">If the error occurred in the same procedure as the error handler, execution resumes with the statement that caused the error.</span></span> <span data-ttu-id="6d412-110">Adlı bir yordamda bir hata oluştu, en son hata işleme yordamı içeren yordamı dışında adlı deyimi yürütme sürdürür.</span><span class="sxs-lookup"><span data-stu-id="6d412-110">If the error occurred in a called procedure, execution resumes at the statement that last called out of the procedure containing the error-handling routine.</span></span>  
  
 `Next`  
 <span data-ttu-id="6d412-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="6d412-111">Optional.</span></span> <span data-ttu-id="6d412-112">Yordamın aynısını hata işleyicisine hata oluştu, yürütme hemen aşağıdaki hata nedeniyle ifadeyi deyimiyle devam ettirir.</span><span class="sxs-lookup"><span data-stu-id="6d412-112">If the error occurred in the same procedure as the error handler, execution resumes with the statement immediately following the statement that caused the error.</span></span> <span data-ttu-id="6d412-113">Adlı bir yordamda bir hata oluştu, yürütme hemen son hata işleme yordamı içeren yordamı dışında adlı deyimi aşağıdaki deyim ile devam ettirir (veya `On Error Resume Next` deyimi).</span><span class="sxs-lookup"><span data-stu-id="6d412-113">If the error occurred in a called procedure, execution resumes with the statement immediately following the statement that last called out of the procedure containing the error-handling routine (or `On Error Resume Next` statement).</span></span>  
  
 `line`  
 <span data-ttu-id="6d412-114">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="6d412-114">Optional.</span></span> <span data-ttu-id="6d412-115">Yürütme sürdürür gerekli belirtilen satırında `line` bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="6d412-115">Execution resumes at the line specified in the required `line` argument.</span></span> <span data-ttu-id="6d412-116">`line` Bağımsız değişkeni bir satır etiket veya satır numarası ve bu yordamın aynısını hata işleyicisine olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6d412-116">The `line` argument is a line label or line number and must be in the same procedure as the error handler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d412-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6d412-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6d412-118">Yapılandırılmamış özel durum işleme kullanmak yerine, mümkün olduğunda, kodunuzda yapılandırılmış özel durum işleme kullanmanızı öneririz ve `On Error` ve `Resume` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="6d412-118">We recommend that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="6d412-119">Daha fazla bilgi için bkz: [deneyin... Catch... Finally ifadesi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6d412-119">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
 <span data-ttu-id="6d412-120">Kullanırsanız, bir `Resume` deyiminde herhangi bir yere dışında bir hata işleme yordamı, bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="6d412-120">If you use a `Resume` statement anywhere other than in an error-handling routine, an error occurs.</span></span>  
  
 <span data-ttu-id="6d412-121">`Resume` Deyimi içeren herhangi bir yordamı kullanılamaz bir `Try...Catch...Finally` deyimi.</span><span class="sxs-lookup"><span data-stu-id="6d412-121">The `Resume` statement cannot be used in any procedure that contains a `Try...Catch...Finally` statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d412-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="6d412-122">Example</span></span>  
 <span data-ttu-id="6d412-123">Bu örnekte `Resume` hata bir yordamda işleme sonlandırmak ve yürütme hataya deyim ile devam etmek için bildirimi.</span><span class="sxs-lookup"><span data-stu-id="6d412-123">This example uses the `Resume` statement to end error handling in a procedure and then resume execution with the statement that caused the error.</span></span> <span data-ttu-id="6d412-124">Hata numarası 55 kullanımını göstermek için oluşturulur `Resume` deyimi.</span><span class="sxs-lookup"><span data-stu-id="6d412-124">Error number 55 is generated to illustrate use of the `Resume` statement.</span></span>  
  
 [!code-vb[VbVbalrErrorHandling#16](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/resume-statement_1.vb)]  
  
## <a name="requirements"></a><span data-ttu-id="6d412-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6d412-125">Requirements</span></span>  
 <span data-ttu-id="6d412-126">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="6d412-126">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="6d412-127">**Derleme:** Visual Basic çalışma zamanı kitaplığı (Microsoft.VisualBasic.dll içinde)</span><span class="sxs-lookup"><span data-stu-id="6d412-127">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d412-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6d412-128">See Also</span></span>  
 [<span data-ttu-id="6d412-129">Try... Catch... Finally ifadesi</span><span class="sxs-lookup"><span data-stu-id="6d412-129">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="6d412-130">Error deyimi</span><span class="sxs-lookup"><span data-stu-id="6d412-130">Error Statement</span></span>](../../../visual-basic/language-reference/statements/error-statement.md)  
 [<span data-ttu-id="6d412-131">On Error deyimi</span><span class="sxs-lookup"><span data-stu-id="6d412-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
