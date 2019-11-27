---
title: Like İşleci
ms.date: 07/20/2015
f1_keywords:
- Like
- vb.Like
helpviewer_keywords:
- similar to
- pattern matching
- Like operator [Visual Basic]
- '? symbol, wildcard character'
- string comparison [Visual Basic], Like operator
- strings [Visual Basic], comparing
- comparison operators [Visual Basic]
- symbols, wildcard
- wildcards, Like operator
- strings [Visual Basic], matching
- string comparison [Visual Basic], sorting data
- data [Visual Basic], sorting
- text [Visual Basic], comparing
- operators [Visual Basic], pattern-matching
- data [Visual Basic], string comparisons
- string comparison [Visual Basic], Like operators
ms.assetid: 966283ec-80e2-4294-baa8-c75baff804f9
ms.openlocfilehash: 5db9488bbec716156a3ab464042c0853241a82b1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350941"
---
# <a name="like-operator-visual-basic"></a><span data-ttu-id="23792-102">Like İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="23792-102">Like Operator (Visual Basic)</span></span>
<span data-ttu-id="23792-103">Bir dizeyi bir düzene göre karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="23792-103">Compares a string against a pattern.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="23792-104">`Like` işleci Şu anda .NET Core ve .NET Standard projelerinde desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="23792-104">The `Like` operator is currently not supported in .NET Core and .NET Standard projects.</span></span>

## <a name="syntax"></a><span data-ttu-id="23792-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="23792-105">Syntax</span></span>  
  
```vb  
result = string Like pattern  
```  
  
## <a name="parts"></a><span data-ttu-id="23792-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="23792-106">Parts</span></span>  
 `result`  
 <span data-ttu-id="23792-107">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="23792-107">Required.</span></span> <span data-ttu-id="23792-108">Herhangi bir `Boolean` değişken.</span><span class="sxs-lookup"><span data-stu-id="23792-108">Any `Boolean` variable.</span></span> <span data-ttu-id="23792-109">Sonuç, `string` `pattern`karşılayıp karşılamadığını belirten `Boolean` bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="23792-109">The result is a `Boolean` value indicating whether or not the `string` satisfies the `pattern`.</span></span>  
  
 `string`  
 <span data-ttu-id="23792-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="23792-110">Required.</span></span> <span data-ttu-id="23792-111">Herhangi bir `String` ifadesi.</span><span class="sxs-lookup"><span data-stu-id="23792-111">Any `String` expression.</span></span>  
  
 `pattern`  
 <span data-ttu-id="23792-112">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="23792-112">Required.</span></span> <span data-ttu-id="23792-113">"Açıklamalar" bölümünde açıklanan desenler ile eşleşen kurallara uyan herhangi bir `String` ifadesi.</span><span class="sxs-lookup"><span data-stu-id="23792-113">Any `String` expression conforming to the pattern-matching conventions described in "Remarks."</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23792-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="23792-114">Remarks</span></span>  
 <span data-ttu-id="23792-115">`string` değeri `pattern`bulunan kalıbı karşılıyorsa `result` `True`.</span><span class="sxs-lookup"><span data-stu-id="23792-115">If the value in `string` satisfies the pattern contained in `pattern`, `result` is `True`.</span></span> <span data-ttu-id="23792-116">Dize, `False``result`.</span><span class="sxs-lookup"><span data-stu-id="23792-116">If the string does not satisfy the pattern, `result` is `False`.</span></span> <span data-ttu-id="23792-117">Hem `string` hem de `pattern` boş dizelerdir, sonuç `True`olur.</span><span class="sxs-lookup"><span data-stu-id="23792-117">If both `string` and `pattern` are empty strings, the result is `True`.</span></span>  
  
## <a name="comparison-method"></a><span data-ttu-id="23792-118">Karşılaştırma yöntemi</span><span class="sxs-lookup"><span data-stu-id="23792-118">Comparison Method</span></span>  
 <span data-ttu-id="23792-119">`Like` işlecinin davranışı [Seçenek karşılaştırma bildirimine](../../../visual-basic/language-reference/statements/option-compare-statement.md)bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="23792-119">The behavior of the `Like` operator depends on the [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span> <span data-ttu-id="23792-120">Her kaynak dosya için varsayılan dize karşılaştırma yöntemi `Option Compare Binary`.</span><span class="sxs-lookup"><span data-stu-id="23792-120">The default string comparison method for each source file is `Option Compare Binary`.</span></span>  
  
## <a name="pattern-options"></a><span data-ttu-id="23792-121">Model seçenekleri</span><span class="sxs-lookup"><span data-stu-id="23792-121">Pattern Options</span></span>  
 <span data-ttu-id="23792-122">Yerleşik model eşleştirme, dize karşılaştırmaları için çok yönlü bir araç sağlar.</span><span class="sxs-lookup"><span data-stu-id="23792-122">Built-in pattern matching provides a versatile tool for string comparisons.</span></span> <span data-ttu-id="23792-123">Desenler ile eşleşen özellikler, `string` her bir karakteri belirli bir karakter, joker karakter, bir karakter listesi veya bir karakter aralığı ile eşleştirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="23792-123">The pattern-matching features allow you to match each character in `string` against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="23792-124">Aşağıdaki tabloda `pattern` ' de izin verilen karakterler ve bunların eşleştikleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="23792-124">The following table shows the characters allowed in `pattern` and what they match.</span></span>  
  
|<span data-ttu-id="23792-125">`pattern` karakterler</span><span class="sxs-lookup"><span data-stu-id="23792-125">Characters in `pattern`</span></span>|<span data-ttu-id="23792-126">`string` eşleşiyor</span><span class="sxs-lookup"><span data-stu-id="23792-126">Matches in `string`</span></span>|  
|-----------------------------|-------------------------|  
|`?`|<span data-ttu-id="23792-127">Herhangi bir tek karakter</span><span class="sxs-lookup"><span data-stu-id="23792-127">Any single character</span></span>|  
|`*`|<span data-ttu-id="23792-128">Sıfır veya daha fazla karakter</span><span class="sxs-lookup"><span data-stu-id="23792-128">Zero or more characters</span></span>|  
|`#`|<span data-ttu-id="23792-129">Herhangi bir tek basamak (0 – 9)</span><span class="sxs-lookup"><span data-stu-id="23792-129">Any single digit (0–9)</span></span>|  
|`[charlist]`|<span data-ttu-id="23792-130">`charlist` bir tek karakter</span><span class="sxs-lookup"><span data-stu-id="23792-130">Any single character in `charlist`</span></span>|  
|`[!charlist]`|<span data-ttu-id="23792-131">`charlist` olmayan bir tek karakter</span><span class="sxs-lookup"><span data-stu-id="23792-131">Any single character not in `charlist`</span></span>|  
  
## <a name="character-lists"></a><span data-ttu-id="23792-132">Karakter listeleri</span><span class="sxs-lookup"><span data-stu-id="23792-132">Character Lists</span></span>  
 <span data-ttu-id="23792-133">Köşeli ayraçlar (`[ ]`) içindeki bir veya daha fazla karakter (`charlist`) grubu, `string` tek bir karakterle eşleştirmek için kullanılabilir ve rakamlar dahil neredeyse tüm karakter kodlarını içerebilir.</span><span class="sxs-lookup"><span data-stu-id="23792-133">A group of one or more characters (`charlist`) enclosed in brackets (`[ ]`) can be used to match any single character in `string` and can include almost any character code, including digits.</span></span>  
  
 <span data-ttu-id="23792-134">`charlist` başındaki bir ünlem işareti (`!`), `charlist` karakterler dışında herhangi bir karakter `string`içinde bulunursa bir eşleşmenin yapıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="23792-134">An exclamation point (`!`) at the beginning of `charlist` means that a match is made if any character except the characters in `charlist` is found in `string`.</span></span> <span data-ttu-id="23792-135">Köşeli ayraçlar dışında kullanıldığında, ünlem işareti kendisiyle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="23792-135">When used outside brackets, the exclamation point matches itself.</span></span>  
  
## <a name="special-characters"></a><span data-ttu-id="23792-136">Özel Karakterler</span><span class="sxs-lookup"><span data-stu-id="23792-136">Special Characters</span></span>  
 <span data-ttu-id="23792-137">Sol köşeli ayraç (`[`), soru işareti (`?`), numara işareti (`#`) ve yıldız işareti (`*`) ile eşleştirmek için bunları köşeli ayraç içine alın.</span><span class="sxs-lookup"><span data-stu-id="23792-137">To match the special characters left bracket (`[`), question mark (`?`), number sign (`#`), and asterisk (`*`), enclose them in brackets.</span></span> <span data-ttu-id="23792-138">Sağ köşeli ayraç (`]`), bir grup içinde kendisiyle eşleşmek için kullanılamaz, ancak tek bir karakter olarak bir grup dışında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="23792-138">The right bracket (`]`) cannot be used within a group to match itself, but it can be used outside a group as an individual character.</span></span>  
  
 <span data-ttu-id="23792-139">`[]` karakter sırası sıfır uzunluklu bir dize (`""`) olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="23792-139">The character sequence `[]` is considered a zero-length string (`""`).</span></span> <span data-ttu-id="23792-140">Ancak, köşeli ayraç içine alınmış bir karakter listesinin parçası olamaz.</span><span class="sxs-lookup"><span data-stu-id="23792-140">However, it cannot be part of a character list enclosed in brackets.</span></span> <span data-ttu-id="23792-141">`string` bir konumun bir karakter grubundan birini mi yoksa herhangi bir karakteri mi içerdiğini denetlemek istiyorsanız, `Like` iki kez kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="23792-141">If you want to check whether a position in `string` contains one of a group of characters or no character at all, you can use `Like` twice.</span></span> <span data-ttu-id="23792-142">Bir örnek için bkz. [nasıl yapılır: bir dizeyi bir düzene göre eşleştirme](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="23792-142">For an example, see [How to: Match a String against a Pattern](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).</span></span>  
  
## <a name="character-ranges"></a><span data-ttu-id="23792-143">Karakter aralıkları</span><span class="sxs-lookup"><span data-stu-id="23792-143">Character Ranges</span></span>  
 <span data-ttu-id="23792-144">Aralığın alt ve üst sınırlarını ayırmak için kısa çizgi (`–`) kullanarak `charlist` bir karakter aralığı belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="23792-144">By using a hyphen (`–`) to separate the lower and upper bounds of the range, `charlist` can specify a range of characters.</span></span> <span data-ttu-id="23792-145">Örneğin, `string` karşılık gelen karakter konumu `A`–`Z`aralığı içinde herhangi bir karakter içeriyorsa ve `[!H–L]`, karşılık gelen karakter konumu Aralık dışında herhangi bir karakter içeriyorsa, bir eşleşme ile sonuçlanır `[A–Z]`.`H``L`</span><span class="sxs-lookup"><span data-stu-id="23792-145">For example, `[A–Z]` results in a match if the corresponding character position in `string` contains any character within the range `A`–`Z`, and `[!H–L]` results in a match if the corresponding character position contains any character outside the range `H`–`L`.</span></span>  
  
 <span data-ttu-id="23792-146">Bir karakter aralığı belirttiğinizde, bu karakterlerin artan sıralama düzeninde görünmesi gerekir, yani en küçükten en büyüğe.</span><span class="sxs-lookup"><span data-stu-id="23792-146">When you specify a range of characters, they must appear in ascending sort order, that is, from lowest to highest.</span></span> <span data-ttu-id="23792-147">Bu nedenle, `[A–Z]` geçerli bir örüntü, ancak `[Z–A]` değildir.</span><span class="sxs-lookup"><span data-stu-id="23792-147">Thus, `[A–Z]` is a valid pattern, but `[Z–A]` is not.</span></span>  
  
### <a name="multiple-character-ranges"></a><span data-ttu-id="23792-148">Birden çok karakter aralığı</span><span class="sxs-lookup"><span data-stu-id="23792-148">Multiple Character Ranges</span></span>  
 <span data-ttu-id="23792-149">Aynı karakter konumu için birden çok Aralık belirtmek için, bunları sınırlayıcılar olmadan aynı köşeli ayraç içine alın.</span><span class="sxs-lookup"><span data-stu-id="23792-149">To specify multiple ranges for the same character position, put them within the same brackets without delimiters.</span></span> <span data-ttu-id="23792-150">Örneğin, `string` karşılık gelen karakter konumu `A`–`C` veya `X`–`Z`aralığında herhangi bir karakter içeriyorsa, `[A–CX–Z]` bir eşleştirmeye neden olur.</span><span class="sxs-lookup"><span data-stu-id="23792-150">For example, `[A–CX–Z]` results in a match if the corresponding character position in `string` contains any character within either the range `A`–`C` or the range `X`–`Z`.</span></span>  
  
### <a name="usage-of-the-hyphen"></a><span data-ttu-id="23792-151">Kısa çizgi kullanımı</span><span class="sxs-lookup"><span data-stu-id="23792-151">Usage of the Hyphen</span></span>  
 <span data-ttu-id="23792-152">Kısa çizgi (`–`), başında (ünlem işaretiyle, varsa) veya `charlist` sonunda ile eşleşmek için görünebilir.</span><span class="sxs-lookup"><span data-stu-id="23792-152">A hyphen (`–`) can appear either at the beginning (after an exclamation point, if any) or at the end of `charlist` to match itself.</span></span> <span data-ttu-id="23792-153">Diğer herhangi bir konumda, tire, tirein her iki tarafındaki karakterlerle sınırlandırılmış bir karakter aralığı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="23792-153">In any other location, the hyphen identifies a range of characters delimited by the characters on either side of the hyphen.</span></span>  
  
## <a name="collating-sequence"></a><span data-ttu-id="23792-154">Harmanlama sırası</span><span class="sxs-lookup"><span data-stu-id="23792-154">Collating Sequence</span></span>  
 <span data-ttu-id="23792-155">Belirtilen bir aralığın anlamı, `Option Compare` tarafından belirlendiği şekilde, çalışma zamanında karakter sıralamasına ve kodun üzerinde çalıştığı sistemin yerel ayar ayarına göre değişir.</span><span class="sxs-lookup"><span data-stu-id="23792-155">The meaning of a specified range depends on the character ordering at run time, as determined by `Option Compare` and the locale setting of the system the code is running on.</span></span> <span data-ttu-id="23792-156">`Option Compare Binary`, Aralık `[A–E]` `A`, `B`, `C`, `D`ve `E`eşleşir.</span><span class="sxs-lookup"><span data-stu-id="23792-156">With `Option Compare Binary`, the range `[A–E]` matches `A`, `B`, `C`, `D`, and `E`.</span></span> <span data-ttu-id="23792-157">`Option Compare Text`, `[A–E]` `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`ve `e`eşleşir.</span><span class="sxs-lookup"><span data-stu-id="23792-157">With `Option Compare Text`, `[A–E]` matches `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, and `e`.</span></span> <span data-ttu-id="23792-158">Aralık `Ê` veya `ê` eşleşmiyor çünkü aksanlı karakterler sıralama düzeninde vurgusuz sonra harmanlandıktan sonra harmanlama.</span><span class="sxs-lookup"><span data-stu-id="23792-158">The range does not match `Ê` or `ê` because accented characters collate after unaccented characters in the sort order.</span></span>  
  
## <a name="digraph-characters"></a><span data-ttu-id="23792-159">Digraf karakterleri</span><span class="sxs-lookup"><span data-stu-id="23792-159">Digraph Characters</span></span>  
 <span data-ttu-id="23792-160">Bazı dillerde, iki ayrı karakteri temsil eden alfabetik karakterler vardır.</span><span class="sxs-lookup"><span data-stu-id="23792-160">In some languages, there are alphabetic characters that represent two separate characters.</span></span> <span data-ttu-id="23792-161">Örneğin, birkaç dil, `a` karakterleri göstermek için `æ` karakter kullanır ve birlikte görüntülendiklerinde `e`.</span><span class="sxs-lookup"><span data-stu-id="23792-161">For example, several languages use the character `æ` to represent the characters `a` and `e` when they appear together.</span></span> <span data-ttu-id="23792-162">`Like` işleci, tek bir digraf karakterinin ve iki ayrı karakterin eşdeğer olduğunu algılar.</span><span class="sxs-lookup"><span data-stu-id="23792-162">The `Like` operator recognizes that the single digraph character and the two individual characters are equivalent.</span></span>  
  
 <span data-ttu-id="23792-163">Sistem yerel ayarları 'nda bir digraf karakteri kullanan bir dil belirtildiğinde, `pattern` veya `string` tek bir digraf karakterinin bir oluşumu, diğer dizedeki eşdeğer iki karakterli dizi ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="23792-163">When a language that uses a digraph character is specified in the system locale settings, an occurrence of the single digraph character in either `pattern` or `string` matches the equivalent two-character sequence in the other string.</span></span> <span data-ttu-id="23792-164">Benzer şekilde, köşeli ayraçlar içinde `pattern` bir digraf karakteri (bir listede veya bir Aralık içinde), `string`denk iki karakterlik sırayla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="23792-164">Similarly, a digraph character in `pattern` enclosed in brackets (by itself, in a list, or in a range) matches the equivalent two-character sequence in `string`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="23792-165">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="23792-165">Overloading</span></span>  
 <span data-ttu-id="23792-166">`Like` işleci *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="23792-166">The `Like` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="23792-167">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="23792-167">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="23792-168">Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="23792-168">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="23792-169">Örnek</span><span class="sxs-lookup"><span data-stu-id="23792-169">Example</span></span>  
 <span data-ttu-id="23792-170">Bu örnek, dizeleri çeşitli desenlerle karşılaştırmak için `Like` işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="23792-170">This example uses the `Like` operator to compare strings to various patterns.</span></span> <span data-ttu-id="23792-171">Sonuçlar, her bir dizenin düzene uygun olup olmadığını gösteren bir `Boolean` değişkenine gider.</span><span class="sxs-lookup"><span data-stu-id="23792-171">The results go into a `Boolean` variable indicating whether each string satisfies the pattern.</span></span>  
  
 [!code-vb[VbVbalrOperators#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="23792-172">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23792-172">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [<span data-ttu-id="23792-173">Karşılaştırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="23792-173">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="23792-174">Visual Basic operatör önceliği</span><span class="sxs-lookup"><span data-stu-id="23792-174">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="23792-175">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="23792-175">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="23792-176">Option Compare Deyimi</span><span class="sxs-lookup"><span data-stu-id="23792-176">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="23792-177">İşleçler ve İfadeler</span><span class="sxs-lookup"><span data-stu-id="23792-177">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="23792-178">Nasıl yapılır: Bir Dizeyi Belirli Bir Desene Göre Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="23792-178">How to: Match a String against a Pattern</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)
