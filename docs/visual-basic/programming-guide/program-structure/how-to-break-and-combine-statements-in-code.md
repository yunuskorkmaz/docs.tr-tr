---
title: 'Nasıl yapılır: (Visual Basic) kodda deyimleri bölme ve birleştirme'
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
ms.openlocfilehash: d3656b924ebaca67c90dc602701c4cef9ce088b4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648787"
---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a><span data-ttu-id="76216-102">Nasıl yapılır: (Visual Basic) kodda deyimleri bölme ve birleştirme</span><span class="sxs-lookup"><span data-stu-id="76216-102">How to: Break and Combine Statements in Code (Visual Basic)</span></span>
<span data-ttu-id="76216-103">Kodunuzu yazarken, bazen Kod Düzenleyicisi'nde yatay kaydırma başlatılmalarını uzun ifadeleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76216-103">When writing your code, you might at times create lengthy statements that necessitate horizontal scrolling in the Code Editor.</span></span> <span data-ttu-id="76216-104">Bu şekilde etkilememesine rağmen kodunuz, bunu siz veya başka hiç kimse izleyicide göründüğü gibi kod okumanız için için zorlaştırır.</span><span class="sxs-lookup"><span data-stu-id="76216-104">Although this doesn't affect the way your code runs, it makes it difficult for you or anyone else to read the code as it appears on the monitor.</span></span> <span data-ttu-id="76216-105">Böyle durumlarda, birkaç satıra tek uzun deyim sonu düşünmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="76216-105">In such cases, you should consider breaking the single long statement into several lines.</span></span>  
  
### <a name="to-break-a-single-statement-into-multiple-lines"></a><span data-ttu-id="76216-106">Tek bir deyimde birden çok satıra ayırmak için</span><span class="sxs-lookup"><span data-stu-id="76216-106">To break a single statement into multiple lines</span></span>  
  
- <span data-ttu-id="76216-107">Bir alt çizgi olan satır devamlılığı karakterini kullanın (`_`), satır sonu istediğiniz noktada.</span><span class="sxs-lookup"><span data-stu-id="76216-107">Use the line-continuation character, which is an underscore (`_`), at the point at which you want the line to break.</span></span> <span data-ttu-id="76216-108">Alt çizgi boşlukla hemen önce ve satır Sonlandırıcı (başı) tarafından hemen ardından.</span><span class="sxs-lookup"><span data-stu-id="76216-108">The underscore must be immediately preceded by a space and immediately followed by a line terminator (carriage return).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="76216-109">Satır devamlılığı karakteri atlarsanız, bazı durumlarda, Visual Basic derleyici örtük olarak deyim kodun sonraki satırında devam eder.</span><span class="sxs-lookup"><span data-stu-id="76216-109">In some cases, if you omit the line-continuation character, the Visual Basic compiler will implicitly continue the statement on the next line of code.</span></span> <span data-ttu-id="76216-110">Kendisi için çıkarabilirsiniz satır devamlılığı karakteri söz dizimi öğeleri listesi için bkz: "Örtük satır devamlılığı" [deyimleri](../../../visual-basic/programming-guide/language-features/statements.md).</span><span class="sxs-lookup"><span data-stu-id="76216-110">For a list of syntax elements for which you can omit the line-continuation character, see "Implicit Line Continuation" in [Statements](../../../visual-basic/programming-guide/language-features/statements.md).</span></span>  
  
     <span data-ttu-id="76216-111">Aşağıdaki örnekte, dört satırı tüm sonlandırma satır devamlılığı karakteri ile ancak son satır deyim ayrılır.</span><span class="sxs-lookup"><span data-stu-id="76216-111">In the following example, the statement is broken into four lines with line-continuation characters terminating all but the last line.</span></span>  
  
     [!code-vb[VbVbcnConventions#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#20)]  
  
     <span data-ttu-id="76216-112">Bu sırayı kullanarak kodunuzu okumak, hem çevrimiçi hem de zaman yazdırılan kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="76216-112">Using this sequence makes your code easier to read, both online and when printed.</span></span>  
  
     <span data-ttu-id="76216-113">Satır devamlılığı karakteri bir satırdaki son karakter olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="76216-113">The line-continuation character must be the last character on a line.</span></span> <span data-ttu-id="76216-114">Bunu başka bir şey ile aynı satırda gelemez.</span><span class="sxs-lookup"><span data-stu-id="76216-114">You can't follow it with anything else on the same line.</span></span>  
  
     <span data-ttu-id="76216-115">Satır devamlılığı karakteri burada kullanabilirsiniz için bazı sınırlamalar mevcuttur; Örneğin, ortasında bir bağımsız değişken adı olarak kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="76216-115">Some limitations exist as to where you can use the line-continuation character; for example, you can't use it in the middle of an argument name.</span></span> <span data-ttu-id="76216-116">Satır devamlılığı karakteri bir bağımsız değişken listesiyle bozabilir ancak bağımsız değişkenlerin adlarını değişmeden kalır.</span><span class="sxs-lookup"><span data-stu-id="76216-116">You can break an argument list with the line-continuation character, but the individual names of the arguments must remain intact.</span></span>  
  
     <span data-ttu-id="76216-117">Bir açıklama satır devam karakterini kullanarak devam edemiyor.</span><span class="sxs-lookup"><span data-stu-id="76216-117">You can't continue a comment by using a line-continuation character.</span></span> <span data-ttu-id="76216-118">Derleyici, özel bir anlamı için bir açıklama karakterleri inceleyin değil.</span><span class="sxs-lookup"><span data-stu-id="76216-118">The compiler doesn't examine the characters in a comment for special meaning.</span></span> <span data-ttu-id="76216-119">Bir çok satırlı açıklama için yorum sembolü yineleyin (`'`) her satırda.</span><span class="sxs-lookup"><span data-stu-id="76216-119">For a multiple-line comment, repeat the comment symbol (`'`) on each line.</span></span>  
  
 <span data-ttu-id="76216-120">Her deyim ayrı bir satıra yerleştirme önerilen yöntem olsa da, Visual Basic da aynı satırda birden çok deyime yerleştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="76216-120">Although placing each statement on a separate line is the recommended method, Visual Basic also allows you to place multiple statements on the same line.</span></span>  
  
### <a name="to-place-multiple-statements-on-the-same-line"></a><span data-ttu-id="76216-121">Aynı satırda birden çok deyime yerleştirmek için</span><span class="sxs-lookup"><span data-stu-id="76216-121">To place multiple statements on the same line</span></span>  
  
- <span data-ttu-id="76216-122">Deyimleri bir iki nokta üst üste ile ayırın (`:`), aşağıdaki örnekte olduğu gibi.</span><span class="sxs-lookup"><span data-stu-id="76216-122">Separate the statements with a colon (`:`), as in the following example.</span></span>  
  
     [!code-vb[VbVbcnConventions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="76216-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76216-123">See also</span></span>

- [<span data-ttu-id="76216-124">Program Yapısı ve Kod Kuralları</span><span class="sxs-lookup"><span data-stu-id="76216-124">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [<span data-ttu-id="76216-125">Deyimler</span><span class="sxs-lookup"><span data-stu-id="76216-125">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
