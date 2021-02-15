---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: bir dizeyi bir düzene göre eşleştirme (Visual Basic)'
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
ms.openlocfilehash: f3e3426f85d420726571f03c88546d181cdccf97
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100461950"
---
# <a name="how-to-match-a-string-against-a-pattern-visual-basic"></a><span data-ttu-id="bc683-103">Nasıl yapılır: Bir Dizeyi Belirli Bir Desene Göre Eşleştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bc683-103">How to: Match a String against a Pattern (Visual Basic)</span></span>

<span data-ttu-id="bc683-104">[Dize veri türünde](../../../language-reference/data-types/string-data-type.md) bir ifadenin bir kalıbı karşılayıp karşılamadığını öğrenmek Isterseniz, [LIKE işlecini](../../../language-reference/operators/like-operator.md)kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc683-104">If you want to find out if an expression of the [String Data Type](../../../language-reference/data-types/string-data-type.md) satisfies a pattern, then you can use the [Like Operator](../../../language-reference/operators/like-operator.md).</span></span>

<span data-ttu-id="bc683-105">`Like` iki işlenen alır.</span><span class="sxs-lookup"><span data-stu-id="bc683-105">`Like` takes two operands.</span></span> <span data-ttu-id="bc683-106">Sol işlenen bir dize ifadesidir ve sağ işlenen, eşleştirme için kullanılacak olan kalıbı içeren bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="bc683-106">The left operand is a string expression, and the right operand is a string containing the pattern to be used for matching.</span></span> <span data-ttu-id="bc683-107">`Like``Boolean`dize ifadesinin kalıbı karşılayıp karşılamadığını gösteren bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="bc683-107">`Like` returns a `Boolean` value indicating whether the string expression satisfies the pattern.</span></span>

<span data-ttu-id="bc683-108">Dize ifadesindeki her karakteri belirli bir karakter, joker karakter, bir karakter listesi veya karakter aralığı ile eşleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc683-108">You can match each character in the string expression against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="bc683-109">Model dizesinde belirtimlerin konumları, dize ifadesinde eşleştirilecek karakterlerin konumlarına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="bc683-109">The positions of the specifications in the pattern string correspond to the positions of the characters to be matched in the string expression.</span></span>

## <a name="to-match-a-character-in-the-string-expression-against-a-specific-character"></a><span data-ttu-id="bc683-110">Dize ifadesindeki bir karakteri belirli bir karakterle eşleştirmek için</span><span class="sxs-lookup"><span data-stu-id="bc683-110">To match a character in the string expression against a specific character</span></span>

<span data-ttu-id="bc683-111">Belirli karakteri doğrudan model dizesine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="bc683-111">Put the specific character directly in the pattern string.</span></span> <span data-ttu-id="bc683-112">Belirli özel karakterlerin köşeli ayraç () içine alınması gerekir `[ ]` .</span><span class="sxs-lookup"><span data-stu-id="bc683-112">Certain special characters must be enclosed in brackets (`[ ]`).</span></span> <span data-ttu-id="bc683-113">Daha fazla bilgi için bkz. [LIKE işleci](../../../language-reference/operators/like-operator.md).</span><span class="sxs-lookup"><span data-stu-id="bc683-113">For more information, see [Like Operator](../../../language-reference/operators/like-operator.md).</span></span>

<span data-ttu-id="bc683-114">Aşağıdaki örnek, `myString` tam olarak tek karakter içerip içermediğini sınar `H` .</span><span class="sxs-lookup"><span data-stu-id="bc683-114">The following example tests whether `myString` consists exactly of the single character `H`.</span></span>

[!code-vb[VbVbalrOperators#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#70)]

## <a name="to-match-a-character-in-the-string-expression-against-a-wildcard-character"></a><span data-ttu-id="bc683-115">Dize ifadesindeki bir karakteri joker karakterle eşleştirmek için</span><span class="sxs-lookup"><span data-stu-id="bc683-115">To match a character in the string expression against a wildcard character</span></span>

<span data-ttu-id="bc683-116">Model dizesine bir soru işareti ( `?` ) koyun.</span><span class="sxs-lookup"><span data-stu-id="bc683-116">Put a question mark (`?`) in the pattern string.</span></span> <span data-ttu-id="bc683-117">Bu konumdaki geçerli bir karakter, başarılı bir eşleşme yapar.</span><span class="sxs-lookup"><span data-stu-id="bc683-117">Any valid character in this position makes a successful match.</span></span>

<span data-ttu-id="bc683-118">Aşağıdaki örnek, `myString` tek bir karakteri ve `W` ardından herhangi bir değerin tam olarak iki karakterini içerip içermediğini sınar.</span><span class="sxs-lookup"><span data-stu-id="bc683-118">The following example tests whether `myString` consists of the single character `W` followed by exactly two characters of any values.</span></span>

[!code-vb[VbVbalrOperators#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#71)]

## <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters"></a><span data-ttu-id="bc683-119">Dize ifadesindeki bir karakteri bir karakter listesine göre eşleştirmek için</span><span class="sxs-lookup"><span data-stu-id="bc683-119">To match a character in the string expression against a list of characters</span></span>

<span data-ttu-id="bc683-120">`[ ]`, Model dizesinde köşeli ayraç () koyun ve köşeli ayracın içine karakter listesini koyun.</span><span class="sxs-lookup"><span data-stu-id="bc683-120">Put brackets (`[ ]`) in the pattern string, and inside the brackets put the list of characters.</span></span> <span data-ttu-id="bc683-121">Karakterleri virgülle veya başka bir ayırıcıyla ayırmayın.</span><span class="sxs-lookup"><span data-stu-id="bc683-121">Do not separate the characters with commas or any other separator.</span></span> <span data-ttu-id="bc683-122">Listedeki herhangi bir tek karakter başarılı bir eşleşme yapar.</span><span class="sxs-lookup"><span data-stu-id="bc683-122">Any single character in the list makes a successful match.</span></span>

<span data-ttu-id="bc683-123">Aşağıdaki örnek, `myString` , veya karakterlerinden yalnızca biri tarafından izlenen geçerli bir karakter olup olmadığını sınar `A` `C` `E` .</span><span class="sxs-lookup"><span data-stu-id="bc683-123">The following example tests whether `myString` consists of any valid character followed by exactly one of the characters `A`, `C`, or `E`.</span></span>

[!code-vb[VbVbalrOperators#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#72)]

<span data-ttu-id="bc683-124">Bu eşleşmenin büyük/küçük harfe duyarlı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="bc683-124">Note that this match is case-sensitive.</span></span>

## <a name="to-match-a-character-in-the-string-expression-against-a-range-of-characters"></a><span data-ttu-id="bc683-125">Dize ifadesindeki bir karakteri bir karakter aralığına göre eşleştirmek için</span><span class="sxs-lookup"><span data-stu-id="bc683-125">To match a character in the string expression against a range of characters</span></span>

<span data-ttu-id="bc683-126">Bir köşeli ayraç ( `[ ]` ) stilini, bir kısa çizgi () ile ayırarak aralığa parantez içine koyun ve parantez içinde en düşük ve en yüksek karakterleri koyun `–` .</span><span class="sxs-lookup"><span data-stu-id="bc683-126">Put brackets (`[ ]`) in the pattern string, and inside the brackets put the lowest and highest characters in the range, separated by a hyphen (`–`).</span></span> <span data-ttu-id="bc683-127">Aralık içinde herhangi bir tek karakter başarılı bir eşleşme yapar.</span><span class="sxs-lookup"><span data-stu-id="bc683-127">Any single character within the range makes a successful match.</span></span>

<span data-ttu-id="bc683-128">Aşağıdaki örnek,,,,, `myString` `num` veya karakterlerinden yalnızca biri tarafından izlenen karakterlerden oluştuğunu sınar `i` `j` `k` `l` `m` `n` .</span><span class="sxs-lookup"><span data-stu-id="bc683-128">The following example tests whether `myString` consists of the characters `num` followed by exactly one of the characters `i`, `j`, `k`, `l`, `m`, or `n`.</span></span>

[!code-vb[VbVbalrOperators#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#73)]

<span data-ttu-id="bc683-129">Bu eşleşmenin büyük/küçük harfe duyarlı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="bc683-129">Note that this match is case-sensitive.</span></span>

## <a name="matching-empty-strings"></a><span data-ttu-id="bc683-130">Eşleşen boş dizeler</span><span class="sxs-lookup"><span data-stu-id="bc683-130">Matching Empty Strings</span></span>

<span data-ttu-id="bc683-131">`Like` diziyi `[]` sıfır uzunluklu bir dize () olarak değerlendirir `""` .</span><span class="sxs-lookup"><span data-stu-id="bc683-131">`Like` treats the sequence `[]` as a zero-length string (`""`).</span></span> <span data-ttu-id="bc683-132">`[]`Tüm dize ifadesinin boş olup olmadığını test etmek için kullanabilirsiniz, ancak dize ifadesindeki belirli bir konumun boş olup olmadığını test etmek için kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="bc683-132">You can use `[]` to test whether the entire string expression is empty, but you cannot use it to test if a particular position in the string expression is empty.</span></span> <span data-ttu-id="bc683-133">Boş bir konum test etmeniz gereken seçeneklerden biri ise, birden `Like` çok kez kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc683-133">If an empty position is one of the options you need to test for, you can use `Like` more than once.</span></span>

### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters-or-no-character"></a><span data-ttu-id="bc683-134">Dize ifadesindeki bir karakteri bir karakter listesiyle veya karakter olmadan eşleştirmek için</span><span class="sxs-lookup"><span data-stu-id="bc683-134">To match a character in the string expression against a list of characters or no character</span></span>

1. <span data-ttu-id="bc683-135">`Like`İşleci aynı dize ifadesinde iki kez çağırın ve iki çağrıyı [OR işleci](../../../language-reference/operators/or-operator.md) ya da [orelı işleciyle](../../../language-reference/operators/orelse-operator.md)bağlayın.</span><span class="sxs-lookup"><span data-stu-id="bc683-135">Call the `Like` operator twice on the same string expression, and connect the two calls with either the [Or Operator](../../../language-reference/operators/or-operator.md) or the [OrElse Operator](../../../language-reference/operators/orelse-operator.md).</span></span>

2. <span data-ttu-id="bc683-136">İlk yan tümce için model dizesinde `Like` köşeli ayraç () içine alınmış karakter listesini ekleyin `[ ]` .</span><span class="sxs-lookup"><span data-stu-id="bc683-136">In the pattern string for the first `Like` clause, include the character list, enclosed in brackets (`[ ]`).</span></span>

3. <span data-ttu-id="bc683-137">İkinci yan tümce için model dizesinde `Like` , söz konusu konuma herhangi bir karakter yerleştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="bc683-137">In the pattern string for the second `Like` clause, do not put any character at the position in question.</span></span>

    <span data-ttu-id="bc683-138">Aşağıdaki örnek, yedi basamaklı telefon numarasını `phoneNum` tam olarak üç sayısal basamak, ardından bir boşluk, kısa çizgi ( `–` ), nokta ( `.` ) veya hiç bir karakter ve tam olarak dört sayısal basamakla sınar.</span><span class="sxs-lookup"><span data-stu-id="bc683-138">The following example tests the seven-digit telephone number `phoneNum` for exactly three numeric digits, followed by a space, a hyphen (`–`), a period (`.`), or no character at all, followed by exactly four numeric digits.</span></span>

    [!code-vb[VbVbalrOperators#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#74)]

## <a name="see-also"></a><span data-ttu-id="bc683-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc683-139">See also</span></span>

- [<span data-ttu-id="bc683-140">Karşılaştırma Işleçleri</span><span class="sxs-lookup"><span data-stu-id="bc683-140">Comparison Operators</span></span>](../../../language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="bc683-141">İşleçler ve Ifadeler</span><span class="sxs-lookup"><span data-stu-id="bc683-141">Operators and Expressions</span></span>](index.md)
- [<span data-ttu-id="bc683-142">Like İşleci</span><span class="sxs-lookup"><span data-stu-id="bc683-142">Like Operator</span></span>](../../../language-reference/operators/like-operator.md)
- [<span data-ttu-id="bc683-143">Dize Veri Türü</span><span class="sxs-lookup"><span data-stu-id="bc683-143">String Data Type</span></span>](../../../language-reference/data-types/string-data-type.md)
