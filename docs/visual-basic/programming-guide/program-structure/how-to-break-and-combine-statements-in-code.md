---
title: "Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb._
helpviewer_keywords:
- colons (:)
- line continuation
- _ line-continuation character
- ': line separator character'
- Visual Basic code, line breaks in
- Visual Basic code, line breaks
- Visual Basic code, line continuation
- long lines of code
- line terminator
- line-continuation sequence
- underscores [Visual Basic], in code
- statements [Visual Basic], line continuation in
- line breaks [Visual Basic], in code
- line-continuation character [Visual Basic]
- Visual Basic code, line continuation in
- statements [Visual Basic], line breaks in
ms.assetid: dea01dad-a8ac-484a-bb3a-8c45a1b1eccc
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cf6b3ce7e5f9549ca04c4980bd3c91513b343ff6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a><span data-ttu-id="6ba3e-102">Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6ba3e-102">How to: Break and Combine Statements in Code (Visual Basic)</span></span>
<span data-ttu-id="6ba3e-103">Kodunuzu yazarken, bazen Kod düzenleyicisinde yatay kaydırma başlatılmalarını uzun deyimleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ba3e-103">When writing your code, you might at times create lengthy statements that necessitate horizontal scrolling in the Code Editor.</span></span> <span data-ttu-id="6ba3e-104">Bu şekilde etkilemez, ancak kodunuzun çalıştığı, onu başkalarının veya monitörde göründüğü gibi kodunu okumak zorlaştırır.</span><span class="sxs-lookup"><span data-stu-id="6ba3e-104">Although this doesn't affect the way your code runs, it makes it difficult for you or anyone else to read the code as it appears on the monitor.</span></span> <span data-ttu-id="6ba3e-105">Böyle durumlarda, tek uzun deyimi birkaç satırlara ayırma göz önünde bulundurmalısınız.</span><span class="sxs-lookup"><span data-stu-id="6ba3e-105">In such cases, you should consider breaking the single long statement into several lines.</span></span>  
  
### <a name="to-break-a-single-statement-into-multiple-lines"></a><span data-ttu-id="6ba3e-106">Tek bir deyimde birden çok çizgiye bölün için</span><span class="sxs-lookup"><span data-stu-id="6ba3e-106">To break a single statement into multiple lines</span></span>  
  
-   <span data-ttu-id="6ba3e-107">Alt çizgi olan satır devamlılığı karakteri kullanın (`_`), satır sonu için istediğiniz noktada.</span><span class="sxs-lookup"><span data-stu-id="6ba3e-107">Use the line-continuation character, which is an underscore (`_`), at the point at which you want the line to break.</span></span> <span data-ttu-id="6ba3e-108">Alt çizgi boşlukla hemen önünde ve bir satır Sonlandırıcı (başı) hemen ardından gerekir.</span><span class="sxs-lookup"><span data-stu-id="6ba3e-108">The underscore must be immediately preceded by a space and immediately followed by a line terminator (carriage return).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6ba3e-109">Satır devamlılığı karakteri atlarsanız, bazı durumlarda, Visual Basic derleyici örtük olarak deyim kodun sonraki satırında devam eder.</span><span class="sxs-lookup"><span data-stu-id="6ba3e-109">In some cases, if you omit the line-continuation character, the Visual Basic compiler will implicitly continue the statement on the next line of code.</span></span> <span data-ttu-id="6ba3e-110">Kendisi için kullanmayabilir satır devamlılığı karakteri söz dizimi öğeleri listesi için bkz: "Örtük satır devamlılığı" [deyimleri](../../../visual-basic/programming-guide/language-features/statements.md).</span><span class="sxs-lookup"><span data-stu-id="6ba3e-110">For a list of syntax elements for which you can omit the line-continuation character, see "Implicit Line Continuation" in [Statements](../../../visual-basic/programming-guide/language-features/statements.md).</span></span>  
  
     <span data-ttu-id="6ba3e-111">Aşağıdaki örnekte, tüm sonlandırma satır devamlılığı karakteri dört satırıyla ancak son satırında deyim ayrılır.</span><span class="sxs-lookup"><span data-stu-id="6ba3e-111">In the following example, the statement is broken into four lines with line-continuation characters terminating all but the last line.</span></span>  
  
     [!code-vb[VbVbcnConventions#20](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_1.vb)]  
  
     <span data-ttu-id="6ba3e-112">Bu sırayı kullanarak kodunuzu okumak hem çevrimiçi hem de zaman yazdırılan kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="6ba3e-112">Using this sequence makes your code easier to read, both online and when printed.</span></span>  
  
     <span data-ttu-id="6ba3e-113">Satır devamlılığı karakteri son karakter bir satırda olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6ba3e-113">The line-continuation character must be the last character on a line.</span></span> <span data-ttu-id="6ba3e-114">Bunu başka bir şey ile aynı satırda izlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="6ba3e-114">You can't follow it with anything else on the same line.</span></span>  
  
     <span data-ttu-id="6ba3e-115">Satır devamlılığı karakteri burada kullanabilirsiniz ilişkin bazı sınırlamalar var; Örneğin, ortasında bir bağımsız değişken adı olarak kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="6ba3e-115">Some limitations exist as to where you can use the line-continuation character; for example, you can't use it in the middle of an argument name.</span></span> <span data-ttu-id="6ba3e-116">Satır devamlılığı karakteri ile bir bağımsız değişken listesi bozulabilir, ancak bağımsız değişkenler tek tek adlarını değişmeden kalmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6ba3e-116">You can break an argument list with the line-continuation character, but the individual names of the arguments must remain intact.</span></span>  
  
     <span data-ttu-id="6ba3e-117">Satır devamlılığı karakteri kullanarak bir yorum devam edemiyor.</span><span class="sxs-lookup"><span data-stu-id="6ba3e-117">You can't continue a comment by using a line-continuation character.</span></span> <span data-ttu-id="6ba3e-118">Derleyici özel bir anlamı için bir açıklama karakterleri inceleyin değil.</span><span class="sxs-lookup"><span data-stu-id="6ba3e-118">The compiler doesn't examine the characters in a comment for special meaning.</span></span> <span data-ttu-id="6ba3e-119">Birden çok satırlı açıklaması için Yorum simgesinin yineleyin (`'`) her satırda.</span><span class="sxs-lookup"><span data-stu-id="6ba3e-119">For a multiple-line comment, repeat the comment symbol (`'`) on each line.</span></span>  
  
 <span data-ttu-id="6ba3e-120">Ayrı bir satırda her deyimi yerleştirme önerilen yöntem olsa da [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] de aynı satıra birden çok deyime yerleştirin olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="6ba3e-120">Although placing each statement on a separate line is the recommended method, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] also allows you to place multiple statements on the same line.</span></span>  
  
### <a name="to-place-multiple-statements-on-the-same-line"></a><span data-ttu-id="6ba3e-121">Aynı çizgi üzerinde birden çok deyime yerleştirmek için</span><span class="sxs-lookup"><span data-stu-id="6ba3e-121">To place multiple statements on the same line</span></span>  
  
-   <span data-ttu-id="6ba3e-122">İki nokta üst üste ile deyimleri ayırın (`:`), aşağıdaki örnekte olduğu gibi.</span><span class="sxs-lookup"><span data-stu-id="6ba3e-122">Separate the statements with a colon (`:`), as in the following example.</span></span>  
  
     [!code-vb[VbVbcnConventions#10](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="6ba3e-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6ba3e-123">See Also</span></span>  
 [<span data-ttu-id="6ba3e-124">Program yapısı ve kod kuralları</span><span class="sxs-lookup"><span data-stu-id="6ba3e-124">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [<span data-ttu-id="6ba3e-125">Deyimleri</span><span class="sxs-lookup"><span data-stu-id="6ba3e-125">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
