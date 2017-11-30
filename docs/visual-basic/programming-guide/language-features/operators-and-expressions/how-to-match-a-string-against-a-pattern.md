---
title: "Nasıl yapılır: Bir Dizeyi Belirli Bir Desene Göre Eşleştirme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- comparison operators [Visual Basic], comparing strings
- pattern matching
- strings [Visual Basic], comparing
- string comparison [Visual Basic], operators
- Visual Basic code, operators
- pattern matching [Visual Basic], string comparison
- string comparison [Visual Basic]
- Like operator [Visual Basic], pattern matching
- pattern matching, empty strings
- operators [Visual Basic], comparison
ms.assetid: 19a83804-b5af-4739-928b-ac93e64e457f
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 83433bdb41df0ce40d0979f3f44603f10ba1c7d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-match-a-string-against-a-pattern-visual-basic"></a><span data-ttu-id="302fb-102">Nasıl yapılır: Bir Dizeyi Belirli Bir Desene Göre Eşleştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="302fb-102">How to: Match a String against a Pattern (Visual Basic)</span></span>
<span data-ttu-id="302fb-103">Bir ifadenin olmadığını öğrenmek istiyorsanız [dize veri türü](../../../../visual-basic/language-reference/data-types/string-data-type.md) kullanabileceğiniz sonra bir desen karşılayan [gibi işleci](../../../../visual-basic/language-reference/operators/like-operator.md).</span><span class="sxs-lookup"><span data-stu-id="302fb-103">If you want to find out if an expression of the [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md) satisfies a pattern, then you can use the [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md).</span></span>  
  
 <span data-ttu-id="302fb-104">`Like`iki işlenen alır.</span><span class="sxs-lookup"><span data-stu-id="302fb-104">`Like` takes two operands.</span></span> <span data-ttu-id="302fb-105">Sol işleneni bir dize ifadesi ve sağ işleneni eşleştirmek için kullanılacak bir desen içeren bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="302fb-105">The left operand is a string expression, and the right operand is a string containing the pattern to be used for matching.</span></span> <span data-ttu-id="302fb-106">`Like`döndüren bir `Boolean` dize ifadesi düzeni karşılayıp karşılamadığını belirten değer.</span><span class="sxs-lookup"><span data-stu-id="302fb-106">`Like` returns a `Boolean` value indicating whether the string expression satisfies the pattern.</span></span>  
  
 <span data-ttu-id="302fb-107">Belirli bir karakter, bir joker karakter, karakter listesini veya bir karakter aralığı karşı dize ifadesindeki her karakter eşleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="302fb-107">You can match each character in the string expression against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="302fb-108">Desen dizesinde belirtimleri konumlarını string ifadesinde eşleştirilmesini karakterleri konumlarını karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="302fb-108">The positions of the specifications in the pattern string correspond to the positions of the characters to be matched in the string expression.</span></span>  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-specific-character"></a><span data-ttu-id="302fb-109">Belirli bir karakterin karşı string ifadesinde bir karakterle eşleştirmek için</span><span class="sxs-lookup"><span data-stu-id="302fb-109">To match a character in the string expression against a specific character</span></span>  
  
-   <span data-ttu-id="302fb-110">Belirli karakterlerin doğrudan düzeni dizesinde yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="302fb-110">Put the specific character directly in the pattern string.</span></span> <span data-ttu-id="302fb-111">Özel karakterleri parantez içine alınmalıdır (`[ ]`).</span><span class="sxs-lookup"><span data-stu-id="302fb-111">Certain special characters must be enclosed in brackets (`[ ]`).</span></span> <span data-ttu-id="302fb-112">Daha fazla bilgi için bkz: [gibi işleci](../../../../visual-basic/language-reference/operators/like-operator.md).</span><span class="sxs-lookup"><span data-stu-id="302fb-112">For more information, see [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md).</span></span>  
  
     <span data-ttu-id="302fb-113">Aşağıdaki örnek testleri olup olmadığını `myString` tam olarak tek karakterinin oluşur `H`.</span><span class="sxs-lookup"><span data-stu-id="302fb-113">The following example tests whether `myString` consists exactly of the single character `H`.</span></span>  
  
     [!code-vb[VbVbalrOperators#70](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_1.vb)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-wildcard-character"></a><span data-ttu-id="302fb-114">Bir joker karakter karşı string ifadesinde bir karakterle eşleştirmek için</span><span class="sxs-lookup"><span data-stu-id="302fb-114">To match a character in the string expression against a wildcard character</span></span>  
  
-   <span data-ttu-id="302fb-115">Bir soru işareti koyma (`?`) desen dizesi içinde.</span><span class="sxs-lookup"><span data-stu-id="302fb-115">Put a question mark (`?`) in the pattern string.</span></span> <span data-ttu-id="302fb-116">Bu konumda herhangi bir geçerli karakter başarılı bir eşleşme yapar.</span><span class="sxs-lookup"><span data-stu-id="302fb-116">Any valid character in this position makes a successful match.</span></span>  
  
     <span data-ttu-id="302fb-117">Aşağıdaki örnek testleri olup olmadığını `myString` tek karakteri oluşur `W` herhangi bir değeri tam olarak iki karakterle devam etmelidir.</span><span class="sxs-lookup"><span data-stu-id="302fb-117">The following example tests whether `myString` consists of the single character `W` followed by exactly two characters of any values.</span></span>  
  
     [!code-vb[VbVbalrOperators#71](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_2.vb)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters"></a><span data-ttu-id="302fb-118">Karakterden oluşan bir liste karşı dize ifadesinde bir karakterle eşleştirmek için</span><span class="sxs-lookup"><span data-stu-id="302fb-118">To match a character in the string expression against a list of characters</span></span>  
  
-   <span data-ttu-id="302fb-119">Köşeli ayraçlar put (`[ ]`) deseni dize ve karakter listesinin put ayraç içinde.</span><span class="sxs-lookup"><span data-stu-id="302fb-119">Put brackets (`[ ]`) in the pattern string, and inside the brackets put the list of characters.</span></span> <span data-ttu-id="302fb-120">Karakterleri, virgül veya başka bir ayırıcı ayırmayın.</span><span class="sxs-lookup"><span data-stu-id="302fb-120">Do not separate the characters with commas or any other separator.</span></span> <span data-ttu-id="302fb-121">Herhangi bir tek karakteri başarılı bir eşleşme yapar.</span><span class="sxs-lookup"><span data-stu-id="302fb-121">Any single character in the list makes a successful match.</span></span>  
  
     <span data-ttu-id="302fb-122">Aşağıdaki örnek testleri olup olmadığını `myString` karakterleri tam olarak biri tarafından izlenen herhangi bir geçerli karakter oluşan `A`, `C`, veya `E`.</span><span class="sxs-lookup"><span data-stu-id="302fb-122">The following example tests whether `myString` consists of any valid character followed by exactly one of the characters `A`, `C`, or `E`.</span></span>  
  
     [!code-vb[VbVbalrOperators#72](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_3.vb)]  
  
     <span data-ttu-id="302fb-123">Bu eşleştirme büyük küçük harfe duyarlı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="302fb-123">Note that this match is case-sensitive.</span></span>  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-range-of-characters"></a><span data-ttu-id="302fb-124">Karakter aralığı karşı string ifadesinde bir karakterle eşleştirmek için</span><span class="sxs-lookup"><span data-stu-id="302fb-124">To match a character in the string expression against a range of characters</span></span>  
  
-   <span data-ttu-id="302fb-125">Köşeli ayraçlar put (`[ ]`) desen dizesi ve en düşük ve en yüksek karakter aralığı içinde put ayraç içinde bir tire ile ayrılmış (`–`).</span><span class="sxs-lookup"><span data-stu-id="302fb-125">Put brackets (`[ ]`) in the pattern string, and inside the brackets put the lowest and highest characters in the range, separated by a hyphen (`–`).</span></span> <span data-ttu-id="302fb-126">Aralık içinde herhangi bir tek karakteri başarılı bir eşleşme yapar.</span><span class="sxs-lookup"><span data-stu-id="302fb-126">Any single character within the range makes a successful match.</span></span>  
  
     <span data-ttu-id="302fb-127">Aşağıdaki örnek testleri olup olmadığını `myString` karakterden oluşan `num` karakterleri tam olarak biri tarafından izlenen `i`, `j`, `k`, `l`, `m`, veya `n`.</span><span class="sxs-lookup"><span data-stu-id="302fb-127">The following example tests whether `myString` consists of the characters `num` followed by exactly one of the characters `i`, `j`, `k`, `l`, `m`, or `n`.</span></span>  
  
     [!code-vb[VbVbalrOperators#73](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_4.vb)]  
  
     <span data-ttu-id="302fb-128">Bu eşleştirme büyük küçük harfe duyarlı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="302fb-128">Note that this match is case-sensitive.</span></span>  
  
## <a name="matching-empty-strings"></a><span data-ttu-id="302fb-129">Eşleşen boş dizeler</span><span class="sxs-lookup"><span data-stu-id="302fb-129">Matching Empty Strings</span></span>  
 <span data-ttu-id="302fb-130">`Like`sıra işler `[]` sıfır uzunlukta bir dize olarak (`""`).</span><span class="sxs-lookup"><span data-stu-id="302fb-130">`Like` treats the sequence `[]` as a zero-length string (`""`).</span></span> <span data-ttu-id="302fb-131">Kullanabileceğiniz `[]` tüm dize ifadesi boş olan, ancak dize ifadesi belirli bir konumda boşsa, test etmek için kullanamazsınız olup olmadığını sınamak için.</span><span class="sxs-lookup"><span data-stu-id="302fb-131">You can use `[]` to test whether the entire string expression is empty, but you cannot use it to test if a particular position in the string expression is empty.</span></span> <span data-ttu-id="302fb-132">Boş bir konum seçeneklerden birini ise kullanabileceğiniz için test yapmanız `Like` birden çok kez.</span><span class="sxs-lookup"><span data-stu-id="302fb-132">If an empty position is one of the options you need to test for, you can use `Like` more than once.</span></span>  
  
#### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters-or-no-character"></a><span data-ttu-id="302fb-133">Bir karakter dizesi bir ifade listesini karşı karakterleri veya herhangi bir karakter eşleştirmek için</span><span class="sxs-lookup"><span data-stu-id="302fb-133">To match a character in the string expression against a list of characters or no character</span></span>  
  
1.  <span data-ttu-id="302fb-134">Çağrı `Like` işlecinin iki kere aynı dize ifadesi ve iki çağrıları biriyle bağlanmak [veya işleci](../../../../visual-basic/language-reference/operators/or-operator.md) veya [OrElse işleci](../../../../visual-basic/language-reference/operators/orelse-operator.md).</span><span class="sxs-lookup"><span data-stu-id="302fb-134">Call the `Like` operator twice on the same string expression, and connect the two calls with either the [Or Operator](../../../../visual-basic/language-reference/operators/or-operator.md) or the [OrElse Operator](../../../../visual-basic/language-reference/operators/orelse-operator.md).</span></span>  
  
2.  <span data-ttu-id="302fb-135">İlk düzeni dizesinde `Like` yan tümcesi, ayraç karakter listede yer (`[ ]`).</span><span class="sxs-lookup"><span data-stu-id="302fb-135">In the pattern string for the first `Like` clause, include the character list, enclosed in brackets (`[ ]`).</span></span>  
  
3.  <span data-ttu-id="302fb-136">İkinci düzeni dizesinde `Like` yan tümcesi, herhangi bir karakter konumunda söz konusu koymayın.</span><span class="sxs-lookup"><span data-stu-id="302fb-136">In the pattern string for the second `Like` clause, do not put any character at the position in question.</span></span>  
  
     <span data-ttu-id="302fb-137">Aşağıdaki örnekte yedi basamaklı telefon numarasını testleri `phoneNum` için tam olarak üç Sayısal basamaklar, ardından bir boşluk, tire (`–`), nokta (`.`), veya hiçbir karakter tarafından tam olarak dört Sayısal basamaklar, ardından.</span><span class="sxs-lookup"><span data-stu-id="302fb-137">The following example tests the seven-digit telephone number `phoneNum` for exactly three numeric digits, followed by a space, a hyphen (`–`), a period (`.`), or no character at all, followed by exactly four numeric digits.</span></span>  
  
     [!code-vb[VbVbalrOperators#74](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_5.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="302fb-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="302fb-138">See Also</span></span>  
 [<span data-ttu-id="302fb-139">Karşılaştırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="302fb-139">Comparison Operators</span></span>](../../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [<span data-ttu-id="302fb-140">İşleçler ve ifadeler</span><span class="sxs-lookup"><span data-stu-id="302fb-140">Operators and Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="302fb-141">Like işleci</span><span class="sxs-lookup"><span data-stu-id="302fb-141">Like Operator</span></span>](../../../../visual-basic/language-reference/operators/like-operator.md)  
 [<span data-ttu-id="302fb-142">Dize veri türü</span><span class="sxs-lookup"><span data-stu-id="302fb-142">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)
