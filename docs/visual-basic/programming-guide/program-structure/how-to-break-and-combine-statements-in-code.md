---
title: 'Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme'
ms.date: 07/20/2015
f1_keywords:
- vb._
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
ms.openlocfilehash: f1a24c001cd20acc7663fb4cbe60e7e35a9c8fc3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347433"
---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a><span data-ttu-id="3c9e5-102">Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c9e5-102">How to: Break and Combine Statements in Code (Visual Basic)</span></span>

<span data-ttu-id="3c9e5-103">Kodunuzu yazarken, kod düzenleyicisinde yatay kaydırmayı gerektiren uzun deyimler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c9e5-103">When writing your code, you might at times create lengthy statements that necessitate horizontal scrolling in the Code Editor.</span></span> <span data-ttu-id="3c9e5-104">Bu, kodunuzun çalışma biçimini etkilemese de, siz veya başka birinin izleyiciden göründüğü şekilde kodu okumasını zorlaştırır.</span><span class="sxs-lookup"><span data-stu-id="3c9e5-104">Although this doesn't affect the way your code runs, it makes it difficult for you or anyone else to read the code as it appears on the monitor.</span></span> <span data-ttu-id="3c9e5-105">Böyle durumlarda, tek uzun bir ifadeyi birkaç satıra bozmalısınız.</span><span class="sxs-lookup"><span data-stu-id="3c9e5-105">In such cases, you should consider breaking the single long statement into several lines.</span></span>

## <a name="to-break-a-single-statement-into-multiple-lines"></a><span data-ttu-id="3c9e5-106">Tek bir ifadeyi birden çok satıra bölmek için</span><span class="sxs-lookup"><span data-stu-id="3c9e5-106">To break a single statement into multiple lines</span></span>

<span data-ttu-id="3c9e5-107">Çizginin kesilmesini istediğiniz noktada alt çizgi (`_`) olan satır devamlılık karakterini kullanın.</span><span class="sxs-lookup"><span data-stu-id="3c9e5-107">Use the line-continuation character, which is an underscore (`_`), at the point at which you want the line to break.</span></span> <span data-ttu-id="3c9e5-108">Alt çizgi hemen öncesinde bir boşluk ve hemen arkasından bir satır Sonlandırıcı (satır sonu) ya da (sürüm 16,0 ' den başlayarak) bir yorum ve ardından bir satır başı gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="3c9e5-108">The underscore must be immediately preceded by a space and immediately followed by a line terminator (carriage return) or (starting with version 16.0) a comment followed by a carriage return.</span></span>

  > [!NOTE]
  > <span data-ttu-id="3c9e5-109">Bazı durumlarda, satır devamlılık karakterini atlarsanız Visual Basic derleyici bir sonraki kod satırında ifadeye dolaylı olarak devam eder.</span><span class="sxs-lookup"><span data-stu-id="3c9e5-109">In some cases, if you omit the line-continuation character, the Visual Basic compiler will implicitly continue the statement on the next line of code.</span></span> <span data-ttu-id="3c9e5-110">Satır devamlılık karakterini yok saybileceğiniz sözdizimi öğelerinin listesi için, bkz. [deyimlerde](../../../visual-basic/programming-guide/language-features/statements.md)"örtük satır devamlılığı".</span><span class="sxs-lookup"><span data-stu-id="3c9e5-110">For a list of syntax elements for which you can omit the line-continuation character, see "Implicit Line Continuation" in [Statements](../../../visual-basic/programming-guide/language-features/statements.md).</span></span>

  <span data-ttu-id="3c9e5-111">Aşağıdaki örnekte,, son satır hariç tüm satır devamlılık karakterleriyle dört satıra bölünmüştür.</span><span class="sxs-lookup"><span data-stu-id="3c9e5-111">In the following example, the statement is broken into four lines with line-continuation characters terminating all but the last line.</span></span>

  [!code-vb[VbVbcnConventions#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#20)]

  <span data-ttu-id="3c9e5-112">Bu dizinin kullanılması, kodunuzun hem çevrimiçi hem de yazdırıldığında okunmasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="3c9e5-112">Using this sequence makes your code easier to read, both online and when printed.</span></span>

  <span data-ttu-id="3c9e5-113">Satır devamlılık karakteri bir satırdaki son karakter olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3c9e5-113">The line-continuation character must be the last character on a line.</span></span> <span data-ttu-id="3c9e5-114">Aynı satırdaki başka herhangi bir şeyle takip edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c9e5-114">You can't follow it with anything else on the same line.</span></span>

  <span data-ttu-id="3c9e5-115">Satır devamlılık karakterini nerede kullanabileceğiniz gibi bazı sınırlamalar vardır; Örneğin, bunu bir bağımsız değişken adının ortasında kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="3c9e5-115">Some limitations exist as to where you can use the line-continuation character; for example, you can't use it in the middle of an argument name.</span></span> <span data-ttu-id="3c9e5-116">Bir bağımsız değişken listesini satır devamlılık karakteriyle kesebilirsiniz, ancak bağımsız değişkenlerin bağımsız adları değişmeden kalmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3c9e5-116">You can break an argument list with the line-continuation character, but the individual names of the arguments must remain intact.</span></span>

  <span data-ttu-id="3c9e5-117">Bir satır devamlılık karakteri kullanarak açıklamaya devam edemiyorum.</span><span class="sxs-lookup"><span data-stu-id="3c9e5-117">You can't continue a comment by using a line-continuation character.</span></span> <span data-ttu-id="3c9e5-118">Derleyici, bir yorum içindeki karakterleri özel anlam açısından inceetmez.</span><span class="sxs-lookup"><span data-stu-id="3c9e5-118">The compiler doesn't examine the characters in a comment for special meaning.</span></span> <span data-ttu-id="3c9e5-119">Birden çok satırlık bir açıklama için, her satırda açıklama sembolünü (`'`) tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="3c9e5-119">For a multiple-line comment, repeat the comment symbol (`'`) on each line.</span></span>

 <span data-ttu-id="3c9e5-120">Her deyimin ayrı bir satıra yerleştirilmesi önerilen yöntem olduğundan, Visual Basic aynı satıra birden çok deyim yerleştirseniz de sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c9e5-120">Although placing each statement on a separate line is the recommended method, Visual Basic also allows you to place multiple statements on the same line.</span></span>

## <a name="to-place-multiple-statements-on-the-same-line"></a><span data-ttu-id="3c9e5-121">Aynı satıra birden çok deyim yerleştirmek için</span><span class="sxs-lookup"><span data-stu-id="3c9e5-121">To place multiple statements on the same line</span></span>

<span data-ttu-id="3c9e5-122">Deyimlerini aşağıdaki örnekte olduğu gibi iki nokta üst üste (`:`) ayırın:</span><span class="sxs-lookup"><span data-stu-id="3c9e5-122">Separate the statements with a colon (`:`), as in the following example:</span></span>

  [!code-vb[VbVbcnConventions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#10)]

## <a name="see-also"></a><span data-ttu-id="3c9e5-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c9e5-123">See also</span></span>

- [<span data-ttu-id="3c9e5-124">Program Yapısı ve Kod Kuralları</span><span class="sxs-lookup"><span data-stu-id="3c9e5-124">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [<span data-ttu-id="3c9e5-125">Deyimler</span><span class="sxs-lookup"><span data-stu-id="3c9e5-125">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
