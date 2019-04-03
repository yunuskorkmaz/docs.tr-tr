---
title: 'Nasıl yapılır: Bir dizeyi belirli bir desene (Visual Basic) göre eşleştirme'
ms.date: 07/20/2015
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
ms.openlocfilehash: ca6537d81f080120fcbea0cf083f450dce4e9f62
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826021"
---
# <a name="how-to-match-a-string-against-a-pattern-visual-basic"></a><span data-ttu-id="598b1-102">Nasıl yapılır: Bir dizeyi belirli bir desene (Visual Basic) göre eşleştirme</span><span class="sxs-lookup"><span data-stu-id="598b1-102">How to: Match a String against a Pattern (Visual Basic)</span></span>
<span data-ttu-id="598b1-103">Bir ifade kaydolmadığı istiyorsanız [dize veri türü](../../../../visual-basic/language-reference/data-types/string-data-type.md) sonra kullanabileceğiniz bir desen karşılayan [gibi işleci](../../../../visual-basic/language-reference/operators/like-operator.md).</span><span class="sxs-lookup"><span data-stu-id="598b1-103">If you want to find out if an expression of the [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md) satisfies a pattern, then you can use the [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md).</span></span>  
  
 <span data-ttu-id="598b1-104">`Like` iki işlenen alır.</span><span class="sxs-lookup"><span data-stu-id="598b1-104">`Like` takes two operands.</span></span> <span data-ttu-id="598b1-105">Sol işlenen bir dize ifadesi ve sağ işlenen eşleştirmek için kullanılacak bir desen içeren bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="598b1-105">The left operand is a string expression, and the right operand is a string containing the pattern to be used for matching.</span></span> <span data-ttu-id="598b1-106">`Like` döndürür bir `Boolean` dize ifade desenini karşılayıp karşılamadığını belirten değer.</span><span class="sxs-lookup"><span data-stu-id="598b1-106">`Like` returns a `Boolean` value indicating whether the string expression satisfies the pattern.</span></span>  
  
 <span data-ttu-id="598b1-107">Belirli bir karakter, bir joker karakter, karakter listesini veya bir karakter aralığı dize ifadeyi her karaktere eşleştirir.</span><span class="sxs-lookup"><span data-stu-id="598b1-107">You can match each character in the string expression against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="598b1-108">Desen dizesi belirtimlerinde konumlarını dize ifadesinin eşleştirilecek karakterleri konumlarını karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="598b1-108">The positions of the specifications in the pattern string correspond to the positions of the characters to be matched in the string expression.</span></span>  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-specific-character"></a><span data-ttu-id="598b1-109">Bir karakter, belirli bir karakter dizesi ifadeyi eşleştirilecek</span><span class="sxs-lookup"><span data-stu-id="598b1-109">To match a character in the string expression against a specific character</span></span>  
  
-   <span data-ttu-id="598b1-110">Belirli karakter doğrudan deseni dizesinde yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="598b1-110">Put the specific character directly in the pattern string.</span></span> <span data-ttu-id="598b1-111">Özel karakterleri ayraçlar içine alınmalıdır (`[ ]`).</span><span class="sxs-lookup"><span data-stu-id="598b1-111">Certain special characters must be enclosed in brackets (`[ ]`).</span></span> <span data-ttu-id="598b1-112">Daha fazla bilgi için [gibi işleci](../../../../visual-basic/language-reference/operators/like-operator.md).</span><span class="sxs-lookup"><span data-stu-id="598b1-112">For more information, see [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md).</span></span>  
  
     <span data-ttu-id="598b1-113">Aşağıdaki örnek testleri olmadığını `myString` tam olarak tek karakterden oluşan `H`.</span><span class="sxs-lookup"><span data-stu-id="598b1-113">The following example tests whether `myString` consists exactly of the single character `H`.</span></span>  
  
     [!code-vb[VbVbalrOperators#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#70)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-wildcard-character"></a><span data-ttu-id="598b1-114">Bir karakter, bir joker karakter dizesi ifadeyi eşleştirilecek</span><span class="sxs-lookup"><span data-stu-id="598b1-114">To match a character in the string expression against a wildcard character</span></span>  
  
-   <span data-ttu-id="598b1-115">Bir soru işareti (`?`) deseni dizesi içinde.</span><span class="sxs-lookup"><span data-stu-id="598b1-115">Put a question mark (`?`) in the pattern string.</span></span> <span data-ttu-id="598b1-116">Bu konumda herhangi bir geçerli karakter başarılı bir eşleşme yapar.</span><span class="sxs-lookup"><span data-stu-id="598b1-116">Any valid character in this position makes a successful match.</span></span>  
  
     <span data-ttu-id="598b1-117">Aşağıdaki örnek testleri olmadığını `myString` tek karakterden oluşan `W` herhangi bir değeri tam olarak iki karakterlerle devam eder.</span><span class="sxs-lookup"><span data-stu-id="598b1-117">The following example tests whether `myString` consists of the single character `W` followed by exactly two characters of any values.</span></span>  
  
     [!code-vb[VbVbalrOperators#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#71)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters"></a><span data-ttu-id="598b1-118">Bir karakter, karakter dize ifadesinin bir listeyle eşleşecek şekilde</span><span class="sxs-lookup"><span data-stu-id="598b1-118">To match a character in the string expression against a list of characters</span></span>  
  
-   <span data-ttu-id="598b1-119">Köşeli ayraçlar yerleştirin (`[ ]`) desen dizesi ve karakterlerin listesini put köşeli ayraçlar içinde.</span><span class="sxs-lookup"><span data-stu-id="598b1-119">Put brackets (`[ ]`) in the pattern string, and inside the brackets put the list of characters.</span></span> <span data-ttu-id="598b1-120">Karakterleri, virgül veya başka bir ayırıcı ile ayırmayın.</span><span class="sxs-lookup"><span data-stu-id="598b1-120">Do not separate the characters with commas or any other separator.</span></span> <span data-ttu-id="598b1-121">Herhangi bir tek karakterle başarılı bir eşleşme yapar.</span><span class="sxs-lookup"><span data-stu-id="598b1-121">Any single character in the list makes a successful match.</span></span>  
  
     <span data-ttu-id="598b1-122">Aşağıdaki örnek testleri olmadığını `myString` karakter tam olarak biri tarafından izlenen herhangi bir geçerli karakter oluşan `A`, `C`, veya `E`.</span><span class="sxs-lookup"><span data-stu-id="598b1-122">The following example tests whether `myString` consists of any valid character followed by exactly one of the characters `A`, `C`, or `E`.</span></span>  
  
     [!code-vb[VbVbalrOperators#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#72)]  
  
     <span data-ttu-id="598b1-123">Bu eşleşme büyük küçük harfe duyarlı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="598b1-123">Note that this match is case-sensitive.</span></span>  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-range-of-characters"></a><span data-ttu-id="598b1-124">Bir karakter, karakter aralığı dize ifadeyi eşleştirilecek</span><span class="sxs-lookup"><span data-stu-id="598b1-124">To match a character in the string expression against a range of characters</span></span>  
  
-   <span data-ttu-id="598b1-125">Köşeli ayraçlar yerleştirin (`[ ]`) deseni dizesinde ve en düşük ve en yüksek karakter aralığında put köşeli ayraçlar içinde ayrılmış bir tire işaretiyle (`–`).</span><span class="sxs-lookup"><span data-stu-id="598b1-125">Put brackets (`[ ]`) in the pattern string, and inside the brackets put the lowest and highest characters in the range, separated by a hyphen (`–`).</span></span> <span data-ttu-id="598b1-126">Herhangi bir tek karakterle aralıktaki başarılı bir eşleşme yapar.</span><span class="sxs-lookup"><span data-stu-id="598b1-126">Any single character within the range makes a successful match.</span></span>  
  
     <span data-ttu-id="598b1-127">Aşağıdaki örnek testleri olmadığını `myString` karakterden oluşan `num` karakter tam olarak biri tarafından izlenen `i`, `j`, `k`, `l`, `m`, veya `n`.</span><span class="sxs-lookup"><span data-stu-id="598b1-127">The following example tests whether `myString` consists of the characters `num` followed by exactly one of the characters `i`, `j`, `k`, `l`, `m`, or `n`.</span></span>  
  
     [!code-vb[VbVbalrOperators#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#73)]  
  
     <span data-ttu-id="598b1-128">Bu eşleşme büyük küçük harfe duyarlı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="598b1-128">Note that this match is case-sensitive.</span></span>  
  
## <a name="matching-empty-strings"></a><span data-ttu-id="598b1-129">Eşleşen boş dizeler</span><span class="sxs-lookup"><span data-stu-id="598b1-129">Matching Empty Strings</span></span>  
 <span data-ttu-id="598b1-130">`Like` sıra işler `[]` sıfır uzunlukta bir dize olarak (`""`).</span><span class="sxs-lookup"><span data-stu-id="598b1-130">`Like` treats the sequence `[]` as a zero-length string (`""`).</span></span> <span data-ttu-id="598b1-131">Kullanabileceğiniz `[]` tüm dize ifadesi boş, ancak dize ifadesi belirli bir konumda boş olup olmadığını test etmek için kullanamazsınız olup olmadığını test etmek için.</span><span class="sxs-lookup"><span data-stu-id="598b1-131">You can use `[]` to test whether the entire string expression is empty, but you cannot use it to test if a particular position in the string expression is empty.</span></span> <span data-ttu-id="598b1-132">Boş bir konum seçenekleri ise kullanabileceğiniz için test etmeniz `Like` birden çok kez.</span><span class="sxs-lookup"><span data-stu-id="598b1-132">If an empty position is one of the options you need to test for, you can use `Like` more than once.</span></span>  
  
#### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters-or-no-character"></a><span data-ttu-id="598b1-133">Bir karakter, karakter veya hiçbir karakter dize ifadesi bir listesiyle eşleşecek şekilde</span><span class="sxs-lookup"><span data-stu-id="598b1-133">To match a character in the string expression against a list of characters or no character</span></span>  
  
1.  <span data-ttu-id="598b1-134">Çağrı `Like` işlecinin iki kez aynı dize ifadesi ve iki çağrıları ile bağlanma [veya işleci](../../../../visual-basic/language-reference/operators/or-operator.md) veya [OrElse işleci](../../../../visual-basic/language-reference/operators/orelse-operator.md).</span><span class="sxs-lookup"><span data-stu-id="598b1-134">Call the `Like` operator twice on the same string expression, and connect the two calls with either the [Or Operator](../../../../visual-basic/language-reference/operators/or-operator.md) or the [OrElse Operator](../../../../visual-basic/language-reference/operators/orelse-operator.md).</span></span>  
  
2.  <span data-ttu-id="598b1-135">İlk kez deseni dizesinde `Like` yan tümcesi, parantez içine alınmış karakter listede yer (`[ ]`).</span><span class="sxs-lookup"><span data-stu-id="598b1-135">In the pattern string for the first `Like` clause, include the character list, enclosed in brackets (`[ ]`).</span></span>  
  
3.  <span data-ttu-id="598b1-136">İkinci deseni dizesinde `Like` yan tümcesi, herhangi bir karakter konumunda söz konusu koymayın.</span><span class="sxs-lookup"><span data-stu-id="598b1-136">In the pattern string for the second `Like` clause, do not put any character at the position in question.</span></span>  
  
     <span data-ttu-id="598b1-137">Aşağıdaki örnek, yedi rakamlı bir telefon numarasını testleri `phoneNum` için tam olarak üç sayısal basamak, ardından bir boşluk, tire (`–`), nokta (`.`), veya hiçbir karakter tam olarak dört sayısal basamak, ardından.</span><span class="sxs-lookup"><span data-stu-id="598b1-137">The following example tests the seven-digit telephone number `phoneNum` for exactly three numeric digits, followed by a space, a hyphen (`–`), a period (`.`), or no character at all, followed by exactly four numeric digits.</span></span>  
  
     [!code-vb[VbVbalrOperators#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#74)]  
  
## <a name="see-also"></a><span data-ttu-id="598b1-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="598b1-138">See also</span></span>

- [<span data-ttu-id="598b1-139">Karşılaştırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="598b1-139">Comparison Operators</span></span>](../../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="598b1-140">İşleçler ve İfadeler</span><span class="sxs-lookup"><span data-stu-id="598b1-140">Operators and Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="598b1-141">Like İşleci</span><span class="sxs-lookup"><span data-stu-id="598b1-141">Like Operator</span></span>](../../../../visual-basic/language-reference/operators/like-operator.md)
- [<span data-ttu-id="598b1-142">String Veri Türü</span><span class="sxs-lookup"><span data-stu-id="598b1-142">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)
