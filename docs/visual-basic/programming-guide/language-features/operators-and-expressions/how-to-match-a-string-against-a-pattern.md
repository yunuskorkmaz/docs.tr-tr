---
title: 'Nasıl yapılır: Bir dizeyi bir düzene göre Eşleştir (Visual Basic)'
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
ms.openlocfilehash: 0bac0869d9e319071abb31dd0576edf0450aa198
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054161"
---
# <a name="how-to-match-a-string-against-a-pattern-visual-basic"></a><span data-ttu-id="9a78e-102">Nasıl yapılır: Bir dizeyi bir düzene göre Eşleştir (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a78e-102">How to: Match a String against a Pattern (Visual Basic)</span></span>

<span data-ttu-id="9a78e-103">[Dize veri türünde](../../../../visual-basic/language-reference/data-types/string-data-type.md) bir ifadenin bir kalıbı karşılayıp karşılamadığını öğrenmek Isterseniz, [LIKE işlecini](../../../../visual-basic/language-reference/operators/like-operator.md)kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a78e-103">If you want to find out if an expression of the [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md) satisfies a pattern, then you can use the [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md).</span></span>

<span data-ttu-id="9a78e-104">`Like`iki işlenen alır.</span><span class="sxs-lookup"><span data-stu-id="9a78e-104">`Like` takes two operands.</span></span> <span data-ttu-id="9a78e-105">Sol işlenen bir dize ifadesidir ve sağ işlenen, eşleştirme için kullanılacak olan kalıbı içeren bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="9a78e-105">The left operand is a string expression, and the right operand is a string containing the pattern to be used for matching.</span></span> <span data-ttu-id="9a78e-106">`Like`dize ifadesinin `Boolean` kalıbı karşılayıp karşılamadığını gösteren bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="9a78e-106">`Like` returns a `Boolean` value indicating whether the string expression satisfies the pattern.</span></span>

<span data-ttu-id="9a78e-107">Dize ifadesindeki her karakteri belirli bir karakter, joker karakter, bir karakter listesi veya karakter aralığı ile eşleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a78e-107">You can match each character in the string expression against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="9a78e-108">Model dizesinde belirtimlerin konumları, dize ifadesinde eşleştirilecek karakterlerin konumlarına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="9a78e-108">The positions of the specifications in the pattern string correspond to the positions of the characters to be matched in the string expression.</span></span>

## <a name="to-match-a-character-in-the-string-expression-against-a-specific-character"></a><span data-ttu-id="9a78e-109">Dize ifadesindeki bir karakteri belirli bir karakterle eşleştirmek için</span><span class="sxs-lookup"><span data-stu-id="9a78e-109">To match a character in the string expression against a specific character</span></span>

<span data-ttu-id="9a78e-110">Belirli karakteri doğrudan model dizesine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="9a78e-110">Put the specific character directly in the pattern string.</span></span> <span data-ttu-id="9a78e-111">Belirli özel karakterlerin köşeli ayraç (`[ ]`) içine alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9a78e-111">Certain special characters must be enclosed in brackets (`[ ]`).</span></span> <span data-ttu-id="9a78e-112">Daha fazla bilgi için bkz. [LIKE işleci](../../../../visual-basic/language-reference/operators/like-operator.md).</span><span class="sxs-lookup"><span data-stu-id="9a78e-112">For more information, see [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md).</span></span>

<span data-ttu-id="9a78e-113">Aşağıdaki örnek, tam olarak `myString` tek karakter `H`içerip içermediğini sınar.</span><span class="sxs-lookup"><span data-stu-id="9a78e-113">The following example tests whether `myString` consists exactly of the single character `H`.</span></span>

[!code-vb[VbVbalrOperators#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#70)]

## <a name="to-match-a-character-in-the-string-expression-against-a-wildcard-character"></a><span data-ttu-id="9a78e-114">Dize ifadesindeki bir karakteri joker karakterle eşleştirmek için</span><span class="sxs-lookup"><span data-stu-id="9a78e-114">To match a character in the string expression against a wildcard character</span></span>

<span data-ttu-id="9a78e-115">Model dizesine bir soru işareti`?`() koyun.</span><span class="sxs-lookup"><span data-stu-id="9a78e-115">Put a question mark (`?`) in the pattern string.</span></span> <span data-ttu-id="9a78e-116">Bu konumdaki geçerli bir karakter, başarılı bir eşleşme yapar.</span><span class="sxs-lookup"><span data-stu-id="9a78e-116">Any valid character in this position makes a successful match.</span></span>

<span data-ttu-id="9a78e-117">Aşağıdaki örnek, tek bir `myString` karakteri `W` ve ardından herhangi bir değerin tam olarak iki karakterini içerip içermediğini sınar.</span><span class="sxs-lookup"><span data-stu-id="9a78e-117">The following example tests whether `myString` consists of the single character `W` followed by exactly two characters of any values.</span></span>

[!code-vb[VbVbalrOperators#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#71)]

## <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters"></a><span data-ttu-id="9a78e-118">Dize ifadesindeki bir karakteri bir karakter listesine göre eşleştirmek için</span><span class="sxs-lookup"><span data-stu-id="9a78e-118">To match a character in the string expression against a list of characters</span></span>

<span data-ttu-id="9a78e-119">, Model dizesinde`[ ]`köşeli ayraç () koyun ve köşeli ayracın içine karakter listesini koyun.</span><span class="sxs-lookup"><span data-stu-id="9a78e-119">Put brackets (`[ ]`) in the pattern string, and inside the brackets put the list of characters.</span></span> <span data-ttu-id="9a78e-120">Karakterleri virgülle veya başka bir ayırıcıyla ayırmayın.</span><span class="sxs-lookup"><span data-stu-id="9a78e-120">Do not separate the characters with commas or any other separator.</span></span> <span data-ttu-id="9a78e-121">Listedeki herhangi bir tek karakter başarılı bir eşleşme yapar.</span><span class="sxs-lookup"><span data-stu-id="9a78e-121">Any single character in the list makes a successful match.</span></span>

<span data-ttu-id="9a78e-122">Aşağıdaki örnek, `myString` `C`, veya `A` karakterlerindenyalnızcabiritarafındanizlenengeçerlibirkarakterolupolmadığınısınar.`E`</span><span class="sxs-lookup"><span data-stu-id="9a78e-122">The following example tests whether `myString` consists of any valid character followed by exactly one of the characters `A`, `C`, or `E`.</span></span>

[!code-vb[VbVbalrOperators#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#72)]

<span data-ttu-id="9a78e-123">Bu eşleşmenin büyük/küçük harfe duyarlı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9a78e-123">Note that this match is case-sensitive.</span></span>

## <a name="to-match-a-character-in-the-string-expression-against-a-range-of-characters"></a><span data-ttu-id="9a78e-124">Dize ifadesindeki bir karakteri bir karakter aralığına göre eşleştirmek için</span><span class="sxs-lookup"><span data-stu-id="9a78e-124">To match a character in the string expression against a range of characters</span></span>

<span data-ttu-id="9a78e-125">Bir köşeli ayraç`[ ]`() stilini, bir kısa çizgi (`–`) ile ayırarak aralığa parantez içine koyun ve parantez içinde en düşük ve en yüksek karakterleri koyun.</span><span class="sxs-lookup"><span data-stu-id="9a78e-125">Put brackets (`[ ]`) in the pattern string, and inside the brackets put the lowest and highest characters in the range, separated by a hyphen (`–`).</span></span> <span data-ttu-id="9a78e-126">Aralık içinde herhangi bir tek karakter başarılı bir eşleşme yapar.</span><span class="sxs-lookup"><span data-stu-id="9a78e-126">Any single character within the range makes a successful match.</span></span>

<span data-ttu-id="9a78e-127">Aşağıdaki örnek,,, `myString` ,, veya `j` `k` `num` `i` karakterlerindenyalnızcabiri`l`tarafından izlenen karakterlerden oluştuğunu sınar. `m` `n`</span><span class="sxs-lookup"><span data-stu-id="9a78e-127">The following example tests whether `myString` consists of the characters `num` followed by exactly one of the characters `i`, `j`, `k`, `l`, `m`, or `n`.</span></span>

[!code-vb[VbVbalrOperators#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#73)]

<span data-ttu-id="9a78e-128">Bu eşleşmenin büyük/küçük harfe duyarlı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9a78e-128">Note that this match is case-sensitive.</span></span>

## <a name="matching-empty-strings"></a><span data-ttu-id="9a78e-129">Eşleşen boş dizeler</span><span class="sxs-lookup"><span data-stu-id="9a78e-129">Matching Empty Strings</span></span>

<span data-ttu-id="9a78e-130">`Like`diziyi `[]` sıfır uzunluklu bir dize (`""`) olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="9a78e-130">`Like` treats the sequence `[]` as a zero-length string (`""`).</span></span> <span data-ttu-id="9a78e-131">Tüm dize ifadesinin `[]` boş olup olmadığını test etmek için kullanabilirsiniz, ancak dize ifadesindeki belirli bir konumun boş olup olmadığını test etmek için kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="9a78e-131">You can use `[]` to test whether the entire string expression is empty, but you cannot use it to test if a particular position in the string expression is empty.</span></span> <span data-ttu-id="9a78e-132">Boş bir konum test etmeniz gereken seçeneklerden biri ise, birden çok kez kullanabilirsiniz `Like` .</span><span class="sxs-lookup"><span data-stu-id="9a78e-132">If an empty position is one of the options you need to test for, you can use `Like` more than once.</span></span>

### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters-or-no-character"></a><span data-ttu-id="9a78e-133">Dize ifadesindeki bir karakteri bir karakter listesiyle veya karakter olmadan eşleştirmek için</span><span class="sxs-lookup"><span data-stu-id="9a78e-133">To match a character in the string expression against a list of characters or no character</span></span>

1. <span data-ttu-id="9a78e-134">İşleci aynı dize ifadesinde iki kez çağırın ve iki çağrıyı [OR işleci](../../../../visual-basic/language-reference/operators/or-operator.md) ya da [orelı işleciyle](../../../../visual-basic/language-reference/operators/orelse-operator.md)bağlayın. `Like`</span><span class="sxs-lookup"><span data-stu-id="9a78e-134">Call the `Like` operator twice on the same string expression, and connect the two calls with either the [Or Operator](../../../../visual-basic/language-reference/operators/or-operator.md) or the [OrElse Operator](../../../../visual-basic/language-reference/operators/orelse-operator.md).</span></span>

2. <span data-ttu-id="9a78e-135">İlk `Like` yan tümce için model dizesinde köşeli ayraç (`[ ]`) içine alınmış karakter listesini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9a78e-135">In the pattern string for the first `Like` clause, include the character list, enclosed in brackets (`[ ]`).</span></span>

3. <span data-ttu-id="9a78e-136">İkinci `Like` yan tümce için model dizesinde, söz konusu konuma herhangi bir karakter yerleştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="9a78e-136">In the pattern string for the second `Like` clause, do not put any character at the position in question.</span></span>

    <span data-ttu-id="9a78e-137">Aşağıdaki örnek, yedi basamaklı telefon numarasını `phoneNum` tam olarak üç sayısal basamak, ardından bir boşluk, kısa çizgi (`–`), nokta (`.`) veya hiç bir karakter ve tam olarak dört sayısal basamakla sınar.</span><span class="sxs-lookup"><span data-stu-id="9a78e-137">The following example tests the seven-digit telephone number `phoneNum` for exactly three numeric digits, followed by a space, a hyphen (`–`), a period (`.`), or no character at all, followed by exactly four numeric digits.</span></span>

    [!code-vb[VbVbalrOperators#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#74)]

## <a name="see-also"></a><span data-ttu-id="9a78e-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a78e-138">See also</span></span>

- [<span data-ttu-id="9a78e-139">Karşılaştırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="9a78e-139">Comparison Operators</span></span>](../../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="9a78e-140">İşleçler ve İfadeler</span><span class="sxs-lookup"><span data-stu-id="9a78e-140">Operators and Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="9a78e-141">Like İşleci</span><span class="sxs-lookup"><span data-stu-id="9a78e-141">Like Operator</span></span>](../../../../visual-basic/language-reference/operators/like-operator.md)
- [<span data-ttu-id="9a78e-142">String Veri Türü</span><span class="sxs-lookup"><span data-stu-id="9a78e-142">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)
