---
title: 'Nasıl yapılır: Bir Dizeyi Belirli Bir Desene Göre Eşleştirme'
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
ms.openlocfilehash: 49328a72c2cff78b8fe13ca73209d224495ad7a1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343632"
---
# <a name="how-to-match-a-string-against-a-pattern-visual-basic"></a><span data-ttu-id="e1b16-102">Nasıl yapılır: Bir Dizeyi Belirli Bir Desene Göre Eşleştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e1b16-102">How to: Match a String against a Pattern (Visual Basic)</span></span>

<span data-ttu-id="e1b16-103">[Dize veri türünde](../../../../visual-basic/language-reference/data-types/string-data-type.md) bir ifadenin bir kalıbı karşılayıp karşılamadığını öğrenmek Isterseniz, [LIKE işlecini](../../../../visual-basic/language-reference/operators/like-operator.md)kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1b16-103">If you want to find out if an expression of the [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md) satisfies a pattern, then you can use the [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md).</span></span>

<span data-ttu-id="e1b16-104">`Like` iki işlenen alır.</span><span class="sxs-lookup"><span data-stu-id="e1b16-104">`Like` takes two operands.</span></span> <span data-ttu-id="e1b16-105">Sol işlenen bir dize ifadesidir ve sağ işlenen, eşleştirme için kullanılacak olan kalıbı içeren bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="e1b16-105">The left operand is a string expression, and the right operand is a string containing the pattern to be used for matching.</span></span> <span data-ttu-id="e1b16-106">`Like`, dize ifadesinin kalıbı karşılayıp karşılamadığını gösteren bir `Boolean` değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="e1b16-106">`Like` returns a `Boolean` value indicating whether the string expression satisfies the pattern.</span></span>

<span data-ttu-id="e1b16-107">Dize ifadesindeki her karakteri belirli bir karakter, joker karakter, bir karakter listesi veya karakter aralığı ile eşleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1b16-107">You can match each character in the string expression against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="e1b16-108">Model dizesinde belirtimlerin konumları, dize ifadesinde eşleştirilecek karakterlerin konumlarına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="e1b16-108">The positions of the specifications in the pattern string correspond to the positions of the characters to be matched in the string expression.</span></span>

## <a name="to-match-a-character-in-the-string-expression-against-a-specific-character"></a><span data-ttu-id="e1b16-109">Dize ifadesindeki bir karakteri belirli bir karakterle eşleştirmek için</span><span class="sxs-lookup"><span data-stu-id="e1b16-109">To match a character in the string expression against a specific character</span></span>

<span data-ttu-id="e1b16-110">Belirli karakteri doğrudan model dizesine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="e1b16-110">Put the specific character directly in the pattern string.</span></span> <span data-ttu-id="e1b16-111">Belirli özel karakterler köşeli ayraç içine alınmalıdır (`[ ]`).</span><span class="sxs-lookup"><span data-stu-id="e1b16-111">Certain special characters must be enclosed in brackets (`[ ]`).</span></span> <span data-ttu-id="e1b16-112">Daha fazla bilgi için bkz. [LIKE işleci](../../../../visual-basic/language-reference/operators/like-operator.md).</span><span class="sxs-lookup"><span data-stu-id="e1b16-112">For more information, see [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md).</span></span>

<span data-ttu-id="e1b16-113">Aşağıdaki örnek, `myString` tam olarak tek karakter `H`mi oluştuğunu sınar.</span><span class="sxs-lookup"><span data-stu-id="e1b16-113">The following example tests whether `myString` consists exactly of the single character `H`.</span></span>

[!code-vb[VbVbalrOperators#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#70)]

## <a name="to-match-a-character-in-the-string-expression-against-a-wildcard-character"></a><span data-ttu-id="e1b16-114">Dize ifadesindeki bir karakteri joker karakterle eşleştirmek için</span><span class="sxs-lookup"><span data-stu-id="e1b16-114">To match a character in the string expression against a wildcard character</span></span>

<span data-ttu-id="e1b16-115">Bir soru işareti (`?`), model dizesine koyun.</span><span class="sxs-lookup"><span data-stu-id="e1b16-115">Put a question mark (`?`) in the pattern string.</span></span> <span data-ttu-id="e1b16-116">Bu konumdaki geçerli bir karakter, başarılı bir eşleşme yapar.</span><span class="sxs-lookup"><span data-stu-id="e1b16-116">Any valid character in this position makes a successful match.</span></span>

<span data-ttu-id="e1b16-117">Aşağıdaki örnek, `myString` tek karakterlik `W` ve ardından her değerin tam olarak iki karakterini içerip içermediğini sınar.</span><span class="sxs-lookup"><span data-stu-id="e1b16-117">The following example tests whether `myString` consists of the single character `W` followed by exactly two characters of any values.</span></span>

[!code-vb[VbVbalrOperators#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#71)]

## <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters"></a><span data-ttu-id="e1b16-118">Dize ifadesindeki bir karakteri bir karakter listesine göre eşleştirmek için</span><span class="sxs-lookup"><span data-stu-id="e1b16-118">To match a character in the string expression against a list of characters</span></span>

<span data-ttu-id="e1b16-119">Köşeli parantezleri (`[ ]`), model dizesine koyun ve köşeli ayracın içine karakter listesini koyun.</span><span class="sxs-lookup"><span data-stu-id="e1b16-119">Put brackets (`[ ]`) in the pattern string, and inside the brackets put the list of characters.</span></span> <span data-ttu-id="e1b16-120">Karakterleri virgülle veya başka bir ayırıcıyla ayırmayın.</span><span class="sxs-lookup"><span data-stu-id="e1b16-120">Do not separate the characters with commas or any other separator.</span></span> <span data-ttu-id="e1b16-121">Listedeki herhangi bir tek karakter başarılı bir eşleşme yapar.</span><span class="sxs-lookup"><span data-stu-id="e1b16-121">Any single character in the list makes a successful match.</span></span>

<span data-ttu-id="e1b16-122">Aşağıdaki örnek, `myString` `A`, `C`veya `E`karakterlerden yalnızca birini içeren herhangi bir geçerli karakterden oluştuğunu sınar.</span><span class="sxs-lookup"><span data-stu-id="e1b16-122">The following example tests whether `myString` consists of any valid character followed by exactly one of the characters `A`, `C`, or `E`.</span></span>

[!code-vb[VbVbalrOperators#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#72)]

<span data-ttu-id="e1b16-123">Bu eşleşmenin büyük/küçük harfe duyarlı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e1b16-123">Note that this match is case-sensitive.</span></span>

## <a name="to-match-a-character-in-the-string-expression-against-a-range-of-characters"></a><span data-ttu-id="e1b16-124">Dize ifadesindeki bir karakteri bir karakter aralığına göre eşleştirmek için</span><span class="sxs-lookup"><span data-stu-id="e1b16-124">To match a character in the string expression against a range of characters</span></span>

<span data-ttu-id="e1b16-125">Köşeli parantezleri (`[ ]`), model dizesine koyun ve köşeli ayraçlar içinde, kısa çizgi (`–`) ile ayırarak aralığa en düşük ve en yüksek karakterleri koyun.</span><span class="sxs-lookup"><span data-stu-id="e1b16-125">Put brackets (`[ ]`) in the pattern string, and inside the brackets put the lowest and highest characters in the range, separated by a hyphen (`–`).</span></span> <span data-ttu-id="e1b16-126">Aralık içinde herhangi bir tek karakter başarılı bir eşleşme yapar.</span><span class="sxs-lookup"><span data-stu-id="e1b16-126">Any single character within the range makes a successful match.</span></span>

<span data-ttu-id="e1b16-127">Aşağıdaki örnek, `myString` karakterlerin `num` ve `i`, `j`, `k`, `l`, `m`veya `n`karakterlerinden birini içerip içermediğini sınar.</span><span class="sxs-lookup"><span data-stu-id="e1b16-127">The following example tests whether `myString` consists of the characters `num` followed by exactly one of the characters `i`, `j`, `k`, `l`, `m`, or `n`.</span></span>

[!code-vb[VbVbalrOperators#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#73)]

<span data-ttu-id="e1b16-128">Bu eşleşmenin büyük/küçük harfe duyarlı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e1b16-128">Note that this match is case-sensitive.</span></span>

## <a name="matching-empty-strings"></a><span data-ttu-id="e1b16-129">Eşleşen boş dizeler</span><span class="sxs-lookup"><span data-stu-id="e1b16-129">Matching Empty Strings</span></span>

<span data-ttu-id="e1b16-130">`Like`, dizi `[]` sıfır uzunluklu bir dize (`""`) olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="e1b16-130">`Like` treats the sequence `[]` as a zero-length string (`""`).</span></span> <span data-ttu-id="e1b16-131">Tüm dize ifadesinin boş olup olmadığını test etmek için `[]` kullanabilirsiniz, ancak dize ifadesindeki belirli bir konumun boş olup olmadığını test etmek için kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="e1b16-131">You can use `[]` to test whether the entire string expression is empty, but you cannot use it to test if a particular position in the string expression is empty.</span></span> <span data-ttu-id="e1b16-132">Boş bir konum için test etmeniz gereken seçeneklerden biri ise, `Like` birden çok kez kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1b16-132">If an empty position is one of the options you need to test for, you can use `Like` more than once.</span></span>

### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters-or-no-character"></a><span data-ttu-id="e1b16-133">Dize ifadesindeki bir karakteri bir karakter listesiyle veya karakter olmadan eşleştirmek için</span><span class="sxs-lookup"><span data-stu-id="e1b16-133">To match a character in the string expression against a list of characters or no character</span></span>

1. <span data-ttu-id="e1b16-134">Aynı dize ifadesinde `Like` işlecini iki kez çağırın ve iki çağrıyı [OR işleci](../../../../visual-basic/language-reference/operators/or-operator.md) ya da [Orelu işleciyle](../../../../visual-basic/language-reference/operators/orelse-operator.md)bağlayın.</span><span class="sxs-lookup"><span data-stu-id="e1b16-134">Call the `Like` operator twice on the same string expression, and connect the two calls with either the [Or Operator](../../../../visual-basic/language-reference/operators/or-operator.md) or the [OrElse Operator](../../../../visual-basic/language-reference/operators/orelse-operator.md).</span></span>

2. <span data-ttu-id="e1b16-135">İlk `Like` yan tümcesinin örüntüsünün dizesinde, köşeli ayraç içine alınmış karakter listesini ekleyin (`[ ]`).</span><span class="sxs-lookup"><span data-stu-id="e1b16-135">In the pattern string for the first `Like` clause, include the character list, enclosed in brackets (`[ ]`).</span></span>

3. <span data-ttu-id="e1b16-136">İkinci `Like` yan tümcesinin model dizesinde, söz konusu konuma herhangi bir karakter yerleştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="e1b16-136">In the pattern string for the second `Like` clause, do not put any character at the position in question.</span></span>

    <span data-ttu-id="e1b16-137">Aşağıdaki örnek, yedi basamaklı telefon numarası `phoneNum` tam olarak üç sayısal basamak, ardından bir boşluk, kısa çizgi (`–`), bir nokta (`.`) veya hiç karakter ve tam olarak dört sayısal basamak için sınar.</span><span class="sxs-lookup"><span data-stu-id="e1b16-137">The following example tests the seven-digit telephone number `phoneNum` for exactly three numeric digits, followed by a space, a hyphen (`–`), a period (`.`), or no character at all, followed by exactly four numeric digits.</span></span>

    [!code-vb[VbVbalrOperators#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#74)]

## <a name="see-also"></a><span data-ttu-id="e1b16-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1b16-138">See also</span></span>

- [<span data-ttu-id="e1b16-139">Karşılaştırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="e1b16-139">Comparison Operators</span></span>](../../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="e1b16-140">İşleçler ve İfadeler</span><span class="sxs-lookup"><span data-stu-id="e1b16-140">Operators and Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="e1b16-141">Like İşleci</span><span class="sxs-lookup"><span data-stu-id="e1b16-141">Like Operator</span></span>](../../../../visual-basic/language-reference/operators/like-operator.md)
- [<span data-ttu-id="e1b16-142">String Veri Türü</span><span class="sxs-lookup"><span data-stu-id="e1b16-142">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)
