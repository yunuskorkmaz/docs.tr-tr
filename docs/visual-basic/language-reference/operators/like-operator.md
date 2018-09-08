---
title: Like İşleci (Visual Basic)
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
ms.openlocfilehash: c5b26bd1d3ebae5136718833c124e3c6e575e9b7
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44198172"
---
# <a name="like-operator-visual-basic"></a><span data-ttu-id="06845-102">Like İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06845-102">Like Operator (Visual Basic)</span></span>
<span data-ttu-id="06845-103">Bir dizeyi bir desene göre karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="06845-103">Compares a string against a pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06845-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="06845-104">Syntax</span></span>  
  
```  
result = string Like pattern  
```  
  
## <a name="parts"></a><span data-ttu-id="06845-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="06845-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="06845-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="06845-106">Required.</span></span> <span data-ttu-id="06845-107">Tüm `Boolean` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="06845-107">Any `Boolean` variable.</span></span> <span data-ttu-id="06845-108">Sonuç bir `Boolean` belirten değer olup olmadığını `string` karşılayan `pattern`.</span><span class="sxs-lookup"><span data-stu-id="06845-108">The result is a `Boolean` value indicating whether or not the `string` satisfies the `pattern`.</span></span>  
  
 `string`  
 <span data-ttu-id="06845-109">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="06845-109">Required.</span></span> <span data-ttu-id="06845-110">Tüm `String` ifade.</span><span class="sxs-lookup"><span data-stu-id="06845-110">Any `String` expression.</span></span>  
  
 `pattern`  
 <span data-ttu-id="06845-111">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="06845-111">Required.</span></span> <span data-ttu-id="06845-112">Tüm `String` ifade "Açıklamalar" içinde tanımlanan desen eşleştirme kuralları uyumludur</span><span class="sxs-lookup"><span data-stu-id="06845-112">Any `String` expression conforming to the pattern-matching conventions described in "Remarks."</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06845-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="06845-113">Remarks</span></span>  
 <span data-ttu-id="06845-114">Varsa değerini `string` bulunan deseni karşılayan `pattern`, `result` olduğu `True`.</span><span class="sxs-lookup"><span data-stu-id="06845-114">If the value in `string` satisfies the pattern contained in `pattern`, `result` is `True`.</span></span> <span data-ttu-id="06845-115">Dizeyi bir desen karşılamaz, `result` olduğu `False`.</span><span class="sxs-lookup"><span data-stu-id="06845-115">If the string does not satisfy the pattern, `result` is `False`.</span></span> <span data-ttu-id="06845-116">Her iki `string` ve `pattern` boş dizeleri olan sonuç `True`.</span><span class="sxs-lookup"><span data-stu-id="06845-116">If both `string` and `pattern` are empty strings, the result is `True`.</span></span>  
  
## <a name="comparison-method"></a><span data-ttu-id="06845-117">Karşılaştırma yöntemi</span><span class="sxs-lookup"><span data-stu-id="06845-117">Comparison Method</span></span>  
 <span data-ttu-id="06845-118">Davranışını `Like` işleci bağlıdır [seçenek karşılaştırma ifadesini](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="06845-118">The behavior of the `Like` operator depends on the [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span> <span data-ttu-id="06845-119">Her kaynak dosyası için varsayılan dize karşılaştırma yöntemi: `Option Compare Binary`.</span><span class="sxs-lookup"><span data-stu-id="06845-119">The default string comparison method for each source file is `Option Compare Binary`.</span></span>  
  
## <a name="pattern-options"></a><span data-ttu-id="06845-120">Düzen Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="06845-120">Pattern Options</span></span>  
 <span data-ttu-id="06845-121">Yerleşik bir desenle eşleşen dize karşılaştırmaları için çok yönlü bir araç sağlar.</span><span class="sxs-lookup"><span data-stu-id="06845-121">Built-in pattern matching provides a versatile tool for string comparisons.</span></span> <span data-ttu-id="06845-122">Desen eşleştirme özellikleri, her bir karakterle Eşleştir imkan tanır `string` belirli bir karakter, bir joker karakter, karakter listesini ya da bir karakter aralığı.</span><span class="sxs-lookup"><span data-stu-id="06845-122">The pattern-matching features allow you to match each character in `string` against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="06845-123">Aşağıdaki tablo, izin verilen karakter gösterir `pattern` ve bunların eşleşmesi.</span><span class="sxs-lookup"><span data-stu-id="06845-123">The following table shows the characters allowed in `pattern` and what they match.</span></span>  
  
|<span data-ttu-id="06845-124">Karakter `pattern`</span><span class="sxs-lookup"><span data-stu-id="06845-124">Characters in `pattern`</span></span>|<span data-ttu-id="06845-125">Eşleştirme `string`</span><span class="sxs-lookup"><span data-stu-id="06845-125">Matches in `string`</span></span>|  
|-----------------------------|-------------------------|  
|`?`|<span data-ttu-id="06845-126">Herhangi bir tek karakter</span><span class="sxs-lookup"><span data-stu-id="06845-126">Any single character</span></span>|  
|`*`|<span data-ttu-id="06845-127">Sıfır veya daha fazla karakter</span><span class="sxs-lookup"><span data-stu-id="06845-127">Zero or more characters</span></span>|  
|`#`|<span data-ttu-id="06845-128">Herhangi bir tek basamak (0 – 9)</span><span class="sxs-lookup"><span data-stu-id="06845-128">Any single digit (0–9)</span></span>|  
|`[charlist]`|<span data-ttu-id="06845-129">Herhangi bir tek karakterle `charlist`</span><span class="sxs-lookup"><span data-stu-id="06845-129">Any single character in `charlist`</span></span>|  
|`[!charlist]`|<span data-ttu-id="06845-130">Herhangi bir tek karakterle içinde değil `charlist`</span><span class="sxs-lookup"><span data-stu-id="06845-130">Any single character not in `charlist`</span></span>|  
  
## <a name="character-lists"></a><span data-ttu-id="06845-131">Karakter listeler</span><span class="sxs-lookup"><span data-stu-id="06845-131">Character Lists</span></span>  
 <span data-ttu-id="06845-132">Bir veya daha fazla karakter grubu (`charlist`) parantezleri içine alınan (`[ ]`) herhangi bir tek karakterle eşleştirmek için kullanılan `string` basamak dahil olmak üzere neredeyse her karakter kodu içerebilir.</span><span class="sxs-lookup"><span data-stu-id="06845-132">A group of one or more characters (`charlist`) enclosed in brackets (`[ ]`) can be used to match any single character in `string` and can include almost any character code, including digits.</span></span>  
  
 <span data-ttu-id="06845-133">Ünlem işareti (`!`) başında `charlist` karakterler dışında herhangi bir karakterin varsa bir eşleşme yapılan anlamına gelir `charlist` bulunur `string`.</span><span class="sxs-lookup"><span data-stu-id="06845-133">An exclamation point (`!`) at the beginning of `charlist` means that a match is made if any character except the characters in `charlist` is found in `string`.</span></span> <span data-ttu-id="06845-134">Köşeli ayraç içine kullanıldığında, ünlem kendisi ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="06845-134">When used outside brackets, the exclamation point matches itself.</span></span>  
  
## <a name="special-characters"></a><span data-ttu-id="06845-135">Özel Karakterler</span><span class="sxs-lookup"><span data-stu-id="06845-135">Special Characters</span></span>  
 <span data-ttu-id="06845-136">Özel karakterleri sol köşeli ayraç eşleştirmek için (`[`), soru işareti (`?`), numara işareti (`#`) ve yıldız işareti (`*`), bunları köşeli ayraç içine alın.</span><span class="sxs-lookup"><span data-stu-id="06845-136">To match the special characters left bracket (`[`), question mark (`?`), number sign (`#`), and asterisk (`*`), enclose them in brackets.</span></span> <span data-ttu-id="06845-137">Sağ köşeli ayraç (`]`) içindeki bir grubun kendisi eşleştirmek için kullanılamaz ancak tek bir karakter olarak bir grubun dışına kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="06845-137">The right bracket (`]`) cannot be used within a group to match itself, but it can be used outside a group as an individual character.</span></span>  
  
 <span data-ttu-id="06845-138">Karakter dizisi `[]` sıfır uzunlukta bir dize olarak kabul edilir (`""`).</span><span class="sxs-lookup"><span data-stu-id="06845-138">The character sequence `[]` is considered a zero-length string (`""`).</span></span> <span data-ttu-id="06845-139">Ancak, ayraç içine bir karakter listesinin bir parçası olamaz.</span><span class="sxs-lookup"><span data-stu-id="06845-139">However, it cannot be part of a character list enclosed in brackets.</span></span> <span data-ttu-id="06845-140">Bir konumda olup olmadığını denetlemek istiyorsanız `string` birini içeren karakter veya hiçbir karakter grubu kullandığınız `Like` iki kez.</span><span class="sxs-lookup"><span data-stu-id="06845-140">If you want to check whether a position in `string` contains one of a group of characters or no character at all, you can use `Like` twice.</span></span> <span data-ttu-id="06845-141">Bir örnek için bkz. [nasıl yapılır: bir dizeyi belirli bir desene göre eşleştirme](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="06845-141">For an example, see [How to: Match a String against a Pattern](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).</span></span>  
  
## <a name="character-ranges"></a><span data-ttu-id="06845-142">Karakter aralığı</span><span class="sxs-lookup"><span data-stu-id="06845-142">Character Ranges</span></span>  
 <span data-ttu-id="06845-143">Kullanarak bir tire (`–`) alt ve üst sınırları aralığını ayırmak için `charlist` da karakter aralığını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06845-143">By using a hyphen (`–`) to separate the lower and upper bounds of the range, `charlist` can specify a range of characters.</span></span> <span data-ttu-id="06845-144">Örneğin, `[A–Z]` karaktere karşılık gelen yerleştirin, sonuçları bir eşleşme `string` aralığındaki herhangi bir karakter içeren `A`–`Z`, ve `[!H–L]` karaktere karşılık gelen konum, içinde bir eşleşme sonuçları izin verilen aralığın dışında herhangi bir karakter içeren `H`–`L`.</span><span class="sxs-lookup"><span data-stu-id="06845-144">For example, `[A–Z]` results in a match if the corresponding character position in `string` contains any character within the range `A`–`Z`, and `[!H–L]` results in a match if the corresponding character position contains any character outside the range `H`–`L`.</span></span>  
  
 <span data-ttu-id="06845-145">Karakter aralığı belirttiğinizde, en düşükten en yükseğe yüksek için sıralama düzeni, diğer bir deyişle, artan sırada görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="06845-145">When you specify a range of characters, they must appear in ascending sort order, that is, from lowest to highest.</span></span> <span data-ttu-id="06845-146">Bu nedenle, `[A–Z]` geçerli bir düzen olduğunu ancak `[Z–A]` değil.</span><span class="sxs-lookup"><span data-stu-id="06845-146">Thus, `[A–Z]` is a valid pattern, but `[Z–A]` is not.</span></span>  
  
### <a name="multiple-character-ranges"></a><span data-ttu-id="06845-147">Birden çok karakter aralıkları</span><span class="sxs-lookup"><span data-stu-id="06845-147">Multiple Character Ranges</span></span>  
 <span data-ttu-id="06845-148">Aynı karakterin konumu için birden çok aralık belirtmek için sınırlayıcılar aynı ayraçlar içine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="06845-148">To specify multiple ranges for the same character position, put them within the same brackets without delimiters.</span></span> <span data-ttu-id="06845-149">Örneğin, `[A–CX–Z]` karaktere karşılık gelen yerleştirin, sonuçları bir eşleşme `string` ya da aralıktaki herhangi bir karakter içeren `A`–`C` veya aralığını `X`–`Z`.</span><span class="sxs-lookup"><span data-stu-id="06845-149">For example, `[A–CX–Z]` results in a match if the corresponding character position in `string` contains any character within either the range `A`–`C` or the range `X`–`Z`.</span></span>  
  
### <a name="usage-of-the-hyphen"></a><span data-ttu-id="06845-150">Kısa çizgi kullanımı</span><span class="sxs-lookup"><span data-stu-id="06845-150">Usage of the Hyphen</span></span>  
 <span data-ttu-id="06845-151">Bir tire (`–`) (sonra bir ünlem işareti varsa) başında veya sonunda görünebilir `charlist` kendisini eşleştirilecek.</span><span class="sxs-lookup"><span data-stu-id="06845-151">A hyphen (`–`) can appear either at the beginning (after an exclamation point, if any) or at the end of `charlist` to match itself.</span></span> <span data-ttu-id="06845-152">Herhangi diğer konumda kısa çizgi, kısa çizgi her iki tarafındaki karakterleri tarafından ayrılmış karakter aralığı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="06845-152">In any other location, the hyphen identifies a range of characters delimited by the characters on either side of the hyphen.</span></span>  
  
## <a name="collating-sequence"></a><span data-ttu-id="06845-153">Harmanlama sırası</span><span class="sxs-lookup"><span data-stu-id="06845-153">Collating Sequence</span></span>  
 <span data-ttu-id="06845-154">Belirtilen bir aralıktaki anlamını tarafından belirlenen şekilde çalışma zamanında sıralama karakter bağlıdır `Option Compare` ve sistemin yerel ayarı kodu çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="06845-154">The meaning of a specified range depends on the character ordering at run time, as determined by `Option Compare` and the locale setting of the system the code is running on.</span></span> <span data-ttu-id="06845-155">İle `Option Compare Binary`, aralığın `[A–E]` eşleşen `A`, `B`, `C`, `D`, ve `E`.</span><span class="sxs-lookup"><span data-stu-id="06845-155">With `Option Compare Binary`, the range `[A–E]` matches `A`, `B`, `C`, `D`, and `E`.</span></span> <span data-ttu-id="06845-156">İle `Option Compare Text`, `[A–E]` eşleşen `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, ve `e`.</span><span class="sxs-lookup"><span data-stu-id="06845-156">With `Option Compare Text`, `[A–E]` matches `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, and `e`.</span></span> <span data-ttu-id="06845-157">Aralığın eşleşmiyor `Ê` veya `ê` sıralama düzeninde vurgulanmamış karakterden sonra vurgulu karakterlerin collate olduğundan.</span><span class="sxs-lookup"><span data-stu-id="06845-157">The range does not match `Ê` or `ê` because accented characters collate after unaccented characters in the sort order.</span></span>  
  
## <a name="digraph-characters"></a><span data-ttu-id="06845-158">Digraph karakter</span><span class="sxs-lookup"><span data-stu-id="06845-158">Digraph Characters</span></span>  
 <span data-ttu-id="06845-159">Bazı dillerde, iki ayrı karakterleri temsil alfabetik karakterler vardır.</span><span class="sxs-lookup"><span data-stu-id="06845-159">In some languages, there are alphabetic characters that represent two separate characters.</span></span> <span data-ttu-id="06845-160">Örneğin, çeşitli diller karakter kullanın `æ` karakterleri temsil etmek için `a` ve `e` birlikte görüntülendiğinde.</span><span class="sxs-lookup"><span data-stu-id="06845-160">For example, several languages use the character `æ` to represent the characters `a` and `e` when they appear together.</span></span> <span data-ttu-id="06845-161">`Like` İşleci tek digraph karakter ve karakterlerin tek tek iki eşdeğer olduğunu algılar.</span><span class="sxs-lookup"><span data-stu-id="06845-161">The `Like` operator recognizes that the single digraph character and the two individual characters are equivalent.</span></span>  
  
 <span data-ttu-id="06845-162">Sistem yerel ayarları digraph karakter kullanan bir dil belirtildiğinde, bir olayın ya da tek digraph karakterinin `pattern` veya `string` diğer dizede eşdeğer iki karakter dizisiyle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="06845-162">When a language that uses a digraph character is specified in the system locale settings, an occurrence of the single digraph character in either `pattern` or `string` matches the equivalent two-character sequence in the other string.</span></span> <span data-ttu-id="06845-163">Benzer şekilde, bir digraph karakter `pattern` parantezleri içine alınan (tek başına bir liste veya bir aralıktaki) eşdeğer iki karakter dizisi ile eşleşen `string`.</span><span class="sxs-lookup"><span data-stu-id="06845-163">Similarly, a digraph character in `pattern` enclosed in brackets (by itself, in a list, or in a range) matches the equivalent two-character sequence in `string`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="06845-164">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="06845-164">Overloading</span></span>  
 <span data-ttu-id="06845-165">`Like` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="06845-165">The `Like` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="06845-166">Kodunuz bu tür bir sınıf veya yapı üzerinde bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="06845-166">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="06845-167">Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="06845-167">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="06845-168">Örnek</span><span class="sxs-lookup"><span data-stu-id="06845-168">Example</span></span>  
 <span data-ttu-id="06845-169">Bu örnekte `Like` çeşitli desenleri için dizeleri karşılaştırmak için işleci.</span><span class="sxs-lookup"><span data-stu-id="06845-169">This example uses the `Like` operator to compare strings to various patterns.</span></span> <span data-ttu-id="06845-170">Tarihinden itibaren bu sonuçları bir `Boolean` her dize deseni karşılayıp karşılamadığını belirten değişkeni.</span><span class="sxs-lookup"><span data-stu-id="06845-170">The results go into a `Boolean` variable indicating whether each string satisfies the pattern.</span></span>  
  
 [!code-vb[VbVbalrOperators#30](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/like-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="06845-171">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="06845-171">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Strings.InStr%2A>  
 <xref:Microsoft.VisualBasic.Strings.StrComp%2A>  
 [<span data-ttu-id="06845-172">Karşılaştırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="06845-172">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [<span data-ttu-id="06845-173">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="06845-173">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="06845-174">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="06845-174">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="06845-175">Option Compare Deyimi</span><span class="sxs-lookup"><span data-stu-id="06845-175">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [<span data-ttu-id="06845-176">İşleçler ve İfadeler</span><span class="sxs-lookup"><span data-stu-id="06845-176">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="06845-177">Nasıl yapılır: Bir Dizeyi Belirli Bir Desene Göre Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="06845-177">How to: Match a String against a Pattern</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)
