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
ms.openlocfilehash: 49dfe5cf5dbcf8dc6f79f569a92e36aa81806913
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866770"
---
# <a name="like-operator-visual-basic"></a><span data-ttu-id="fa6ac-102">Like İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fa6ac-102">Like Operator (Visual Basic)</span></span>

<span data-ttu-id="fa6ac-103">Bir dizeyi bir düzene göre karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="fa6ac-103">Compares a string against a pattern.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="fa6ac-104">`Like`İşleç Şu anda .NET Core ve .NET Standard projelerinde desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="fa6ac-104">The `Like` operator is currently not supported in .NET Core and .NET Standard projects.</span></span>

## <a name="syntax"></a><span data-ttu-id="fa6ac-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fa6ac-105">Syntax</span></span>  
  
```vb  
result = string Like pattern  
```  
  
## <a name="parts"></a><span data-ttu-id="fa6ac-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="fa6ac-106">Parts</span></span>  

 `result`  
 <span data-ttu-id="fa6ac-107">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fa6ac-107">Required.</span></span> <span data-ttu-id="fa6ac-108">Herhangi bir `Boolean` değişken.</span><span class="sxs-lookup"><span data-stu-id="fa6ac-108">Any `Boolean` variable.</span></span> <span data-ttu-id="fa6ac-109">Sonuç, `Boolean` karşılayıp karşılamadığını gösteren bir değerdir `string` `pattern` .</span><span class="sxs-lookup"><span data-stu-id="fa6ac-109">The result is a `Boolean` value indicating whether or not the `string` satisfies the `pattern`.</span></span>  
  
 `string`  
 <span data-ttu-id="fa6ac-110">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fa6ac-110">Required.</span></span> <span data-ttu-id="fa6ac-111">Herhangi bir `String` ifade.</span><span class="sxs-lookup"><span data-stu-id="fa6ac-111">Any `String` expression.</span></span>  
  
 `pattern`  
 <span data-ttu-id="fa6ac-112">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fa6ac-112">Required.</span></span> <span data-ttu-id="fa6ac-113">`String`"Açıklamalar" bölümünde açıklanan desenler ile eşleşen kurallara uyan ifadeler.</span><span class="sxs-lookup"><span data-stu-id="fa6ac-113">Any `String` expression conforming to the pattern-matching conventions described in "Remarks."</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa6ac-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fa6ac-114">Remarks</span></span>  

 <span data-ttu-id="fa6ac-115">İçindeki değeri `string` içinde bulunan bir kalıbı karşılıyorsa,, `pattern` `result` olur `True` .</span><span class="sxs-lookup"><span data-stu-id="fa6ac-115">If the value in `string` satisfies the pattern contained in `pattern`, `result` is `True`.</span></span> <span data-ttu-id="fa6ac-116">Dize, bu kalıbı karşılamaz `result` `False` .</span><span class="sxs-lookup"><span data-stu-id="fa6ac-116">If the string does not satisfy the pattern, `result` is `False`.</span></span> <span data-ttu-id="fa6ac-117">Hem hem `string` de `pattern` boş dizeler varsa, sonuç olur `True` .</span><span class="sxs-lookup"><span data-stu-id="fa6ac-117">If both `string` and `pattern` are empty strings, the result is `True`.</span></span>  
  
## <a name="comparison-method"></a><span data-ttu-id="fa6ac-118">Karşılaştırma yöntemi</span><span class="sxs-lookup"><span data-stu-id="fa6ac-118">Comparison Method</span></span>  

 <span data-ttu-id="fa6ac-119">`Like`İşlecin davranışı [Seçenek karşılaştırma bildirimine](../statements/option-compare-statement.md)bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="fa6ac-119">The behavior of the `Like` operator depends on the [Option Compare Statement](../statements/option-compare-statement.md).</span></span> <span data-ttu-id="fa6ac-120">Her kaynak dosya için varsayılan dize karşılaştırma yöntemi `Option Compare Binary` .</span><span class="sxs-lookup"><span data-stu-id="fa6ac-120">The default string comparison method for each source file is `Option Compare Binary`.</span></span>  
  
## <a name="pattern-options"></a><span data-ttu-id="fa6ac-121">Model seçenekleri</span><span class="sxs-lookup"><span data-stu-id="fa6ac-121">Pattern Options</span></span>  

 <span data-ttu-id="fa6ac-122">Yerleşik model eşleştirme, dize karşılaştırmaları için çok yönlü bir araç sağlar.</span><span class="sxs-lookup"><span data-stu-id="fa6ac-122">Built-in pattern matching provides a versatile tool for string comparisons.</span></span> <span data-ttu-id="fa6ac-123">Desenler ile eşleşen özellikler, içindeki her karakteri `string` belirli bir karakter, joker karakter, bir karakter listesi veya karakter aralığı ile eşleştirirken izin verir.</span><span class="sxs-lookup"><span data-stu-id="fa6ac-123">The pattern-matching features allow you to match each character in `string` against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="fa6ac-124">Aşağıdaki tabloda ' da izin verilen karakterler `pattern` ve bunların eşleştiği özellikler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fa6ac-124">The following table shows the characters allowed in `pattern` and what they match.</span></span>  
  
|<span data-ttu-id="fa6ac-125">İçindeki karakterler `pattern`</span><span class="sxs-lookup"><span data-stu-id="fa6ac-125">Characters in `pattern`</span></span>|<span data-ttu-id="fa6ac-126">İçindeki eşleşmeler `string`</span><span class="sxs-lookup"><span data-stu-id="fa6ac-126">Matches in `string`</span></span>|  
|-----------------------------|-------------------------|  
|`?`|<span data-ttu-id="fa6ac-127">Herhangi bir tek karakter</span><span class="sxs-lookup"><span data-stu-id="fa6ac-127">Any single character</span></span>|  
|`*`|<span data-ttu-id="fa6ac-128">Sıfır veya daha fazla karakter</span><span class="sxs-lookup"><span data-stu-id="fa6ac-128">Zero or more characters</span></span>|  
|`#`|<span data-ttu-id="fa6ac-129">Herhangi bir tek basamak (0 – 9)</span><span class="sxs-lookup"><span data-stu-id="fa6ac-129">Any single digit (0–9)</span></span>|  
|`[charlist]`|<span data-ttu-id="fa6ac-130">İçinde herhangi bir tek karakter `charlist`</span><span class="sxs-lookup"><span data-stu-id="fa6ac-130">Any single character in `charlist`</span></span>|  
|`[!charlist]`|<span data-ttu-id="fa6ac-131">Herhangi bir tek karakter `charlist`</span><span class="sxs-lookup"><span data-stu-id="fa6ac-131">Any single character not in `charlist`</span></span>|  
  
## <a name="character-lists"></a><span data-ttu-id="fa6ac-132">Karakter listeleri</span><span class="sxs-lookup"><span data-stu-id="fa6ac-132">Character Lists</span></span>  

 <span data-ttu-id="fa6ac-133">Parantez dahil bir veya daha fazla karakter () içeren bir grup () `charlist` `[ ]` , içindeki herhangi bir karakteri eşleştirmek için kullanılabilir `string` ve rakamlar dahil neredeyse tüm karakter kodlarını içerebilir.</span><span class="sxs-lookup"><span data-stu-id="fa6ac-133">A group of one or more characters (`charlist`) enclosed in brackets (`[ ]`) can be used to match any single character in `string` and can include almost any character code, including digits.</span></span>  
  
 <span data-ttu-id="fa6ac-134">Öğesinin başındaki bir ünlem işareti ( `!` ), içinde `charlist` karakterler dışında herhangi bir karakter içinde bulunursa eşleşme yapılır anlamına gelir `charlist` `string` .</span><span class="sxs-lookup"><span data-stu-id="fa6ac-134">An exclamation point (`!`) at the beginning of `charlist` means that a match is made if any character except the characters in `charlist` is found in `string`.</span></span> <span data-ttu-id="fa6ac-135">Köşeli ayraçlar dışında kullanıldığında, ünlem işareti kendisiyle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="fa6ac-135">When used outside brackets, the exclamation point matches itself.</span></span>  
  
## <a name="special-characters"></a><span data-ttu-id="fa6ac-136">Özel Karakterler</span><span class="sxs-lookup"><span data-stu-id="fa6ac-136">Special Characters</span></span>  

 <span data-ttu-id="fa6ac-137">Sol köşeli ayraç ( `[` ), soru işareti ( `?` ), sayı işareti ( `#` ) ve yıldız işareti () gibi özel karakterleri eşleştirmek için `*` bunları köşeli ayraç içine alın.</span><span class="sxs-lookup"><span data-stu-id="fa6ac-137">To match the special characters left bracket (`[`), question mark (`?`), number sign (`#`), and asterisk (`*`), enclose them in brackets.</span></span> <span data-ttu-id="fa6ac-138">Sağ köşeli ayraç ( `]` ) bir grup içinde kendisiyle eşleşecek şekilde kullanılamaz, ancak tek bir karakter olarak bir grup dışında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fa6ac-138">The right bracket (`]`) cannot be used within a group to match itself, but it can be used outside a group as an individual character.</span></span>  
  
 <span data-ttu-id="fa6ac-139">Karakter sırası `[]` sıfır uzunluklu bir dize () olarak kabul edilir `""` .</span><span class="sxs-lookup"><span data-stu-id="fa6ac-139">The character sequence `[]` is considered a zero-length string (`""`).</span></span> <span data-ttu-id="fa6ac-140">Ancak, köşeli ayraç içine alınmış bir karakter listesinin parçası olamaz.</span><span class="sxs-lookup"><span data-stu-id="fa6ac-140">However, it cannot be part of a character list enclosed in brackets.</span></span> <span data-ttu-id="fa6ac-141">İçindeki bir konumun bir `string` karakter grubundan birini mi yoksa herhangi bir karakteri mi içerdiğini denetlemek isterseniz `Like` iki kez kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa6ac-141">If you want to check whether a position in `string` contains one of a group of characters or no character at all, you can use `Like` twice.</span></span> <span data-ttu-id="fa6ac-142">Bir örnek için bkz. [nasıl yapılır: bir dizeyi bir düzene göre eşleştirme](../../programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="fa6ac-142">For an example, see [How to: Match a String against a Pattern](../../programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).</span></span>  
  
## <a name="character-ranges"></a><span data-ttu-id="fa6ac-143">Karakter aralıkları</span><span class="sxs-lookup"><span data-stu-id="fa6ac-143">Character Ranges</span></span>  

 <span data-ttu-id="fa6ac-144">`–`Aralığın alt ve üst sınırlarını ayırmak için kısa çizgi () kullanarak `charlist` bir karakter aralığı belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa6ac-144">By using a hyphen (`–`) to separate the lower and upper bounds of the range, `charlist` can specify a range of characters.</span></span> <span data-ttu-id="fa6ac-145">Örneğin, `[A–Z]` içindeki karşılık gelen karakter konumu, `string` Aralık içinde herhangi bir karakter içeriyorsa `A` `Z` ve `[!H–L]` karşılık gelen karakter konumu Aralık dışında herhangi bir karakter içeriyorsa bir `H` `L` eşleşme ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="fa6ac-145">For example, `[A–Z]` results in a match if the corresponding character position in `string` contains any character within the range `A`–`Z`, and `[!H–L]` results in a match if the corresponding character position contains any character outside the range `H`–`L`.</span></span>  
  
 <span data-ttu-id="fa6ac-146">Bir karakter aralığı belirttiğinizde, bu karakterlerin artan sıralama düzeninde görünmesi gerekir, yani en küçükten en büyüğe.</span><span class="sxs-lookup"><span data-stu-id="fa6ac-146">When you specify a range of characters, they must appear in ascending sort order, that is, from lowest to highest.</span></span> <span data-ttu-id="fa6ac-147">Bu nedenle, `[A–Z]` geçerli bir örüntü, ancak `[Z–A]` değildir.</span><span class="sxs-lookup"><span data-stu-id="fa6ac-147">Thus, `[A–Z]` is a valid pattern, but `[Z–A]` is not.</span></span>  
  
### <a name="multiple-character-ranges"></a><span data-ttu-id="fa6ac-148">Birden çok karakter aralığı</span><span class="sxs-lookup"><span data-stu-id="fa6ac-148">Multiple Character Ranges</span></span>  

 <span data-ttu-id="fa6ac-149">Aynı karakter konumu için birden çok Aralık belirtmek için, bunları sınırlayıcılar olmadan aynı köşeli ayraç içine alın.</span><span class="sxs-lookup"><span data-stu-id="fa6ac-149">To specify multiple ranges for the same character position, put them within the same brackets without delimiters.</span></span> <span data-ttu-id="fa6ac-150">Örneğin, `[A–CX–Z]` içindeki karşılık gelen karakter konumu, `string` Aralık içinde herhangi bir karakter `A` `C` veya-aralığı içinde herhangi bir karakter içeriyorsa, bir eşleşme ile sonuçlanır `X` `Z` .</span><span class="sxs-lookup"><span data-stu-id="fa6ac-150">For example, `[A–CX–Z]` results in a match if the corresponding character position in `string` contains any character within either the range `A`–`C` or the range `X`–`Z`.</span></span>  
  
### <a name="usage-of-the-hyphen"></a><span data-ttu-id="fa6ac-151">Kısa çizgi kullanımı</span><span class="sxs-lookup"><span data-stu-id="fa6ac-151">Usage of the Hyphen</span></span>  

 <span data-ttu-id="fa6ac-152">Kısa çizgi ( `–` ), başında (ünlem işaretiyle, varsa) veya sonuna kadar bir nokta () görünebilir `charlist` .</span><span class="sxs-lookup"><span data-stu-id="fa6ac-152">A hyphen (`–`) can appear either at the beginning (after an exclamation point, if any) or at the end of `charlist` to match itself.</span></span> <span data-ttu-id="fa6ac-153">Diğer herhangi bir konumda, tire, tirein her iki tarafındaki karakterlerle sınırlandırılmış bir karakter aralığı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fa6ac-153">In any other location, the hyphen identifies a range of characters delimited by the characters on either side of the hyphen.</span></span>  
  
## <a name="collating-sequence"></a><span data-ttu-id="fa6ac-154">Harmanlama sırası</span><span class="sxs-lookup"><span data-stu-id="fa6ac-154">Collating Sequence</span></span>  

 <span data-ttu-id="fa6ac-155">Belirtilen bir aralığın anlamı, tarafından belirlendiği şekilde çalışma zamanında karakter sıralamasına `Option Compare` ve kodun üzerinde çalıştığı sistemin yerel ayar ayarına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="fa6ac-155">The meaning of a specified range depends on the character ordering at run time, as determined by `Option Compare` and the locale setting of the system the code is running on.</span></span> <span data-ttu-id="fa6ac-156">İle, aralığı,,, `Option Compare Binary` `[A–E]` ve ile eşleşir `A` `B` `C` `D` `E` .</span><span class="sxs-lookup"><span data-stu-id="fa6ac-156">With `Option Compare Binary`, the range `[A–E]` matches `A`, `B`, `C`, `D`, and `E`.</span></span> <span data-ttu-id="fa6ac-157">,,,,,,,,,,,,, `Option Compare Text` `[A–E]` Ve ile eşleşir `A` `a` `À` `à` `B` `b` `C` `c` `D` `d` `E` `e` .</span><span class="sxs-lookup"><span data-stu-id="fa6ac-157">With `Option Compare Text`, `[A–E]` matches `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, and `e`.</span></span> <span data-ttu-id="fa6ac-158">Aralık eşleşmiyor `Ê` veya aksanlı `ê` karakterler sıralama düzeninde vurgusuz olmayan karakterlerden sonra harmanlanmıyor.</span><span class="sxs-lookup"><span data-stu-id="fa6ac-158">The range does not match `Ê` or `ê` because accented characters collate after unaccented characters in the sort order.</span></span>  
  
## <a name="digraph-characters"></a><span data-ttu-id="fa6ac-159">Digraf karakterleri</span><span class="sxs-lookup"><span data-stu-id="fa6ac-159">Digraph Characters</span></span>  

 <span data-ttu-id="fa6ac-160">Bazı dillerde, iki ayrı karakteri temsil eden alfabetik karakterler vardır.</span><span class="sxs-lookup"><span data-stu-id="fa6ac-160">In some languages, there are alphabetic characters that represent two separate characters.</span></span> <span data-ttu-id="fa6ac-161">Örneğin, birkaç dil, `æ` karakterleri temsil eden karakteri `a` ve `e` birlikte görüntülendikleri karakteri kullanır.</span><span class="sxs-lookup"><span data-stu-id="fa6ac-161">For example, several languages use the character `æ` to represent the characters `a` and `e` when they appear together.</span></span> <span data-ttu-id="fa6ac-162">`Like`İşleci, tek bir digraf karakterinin ve iki ayrı karakterin eşdeğer olduğunu algılar.</span><span class="sxs-lookup"><span data-stu-id="fa6ac-162">The `Like` operator recognizes that the single digraph character and the two individual characters are equivalent.</span></span>  
  
 <span data-ttu-id="fa6ac-163">Sistem yerel ayarlarında bir digraf karakteri kullanan bir dil belirtildiğinde, ya da içinde tek bir digraf karakterinin bir oluşumu `pattern` `string` diğer dizedeki eşdeğer iki karakterli dizi ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="fa6ac-163">When a language that uses a digraph character is specified in the system locale settings, an occurrence of the single digraph character in either `pattern` or `string` matches the equivalent two-character sequence in the other string.</span></span> <span data-ttu-id="fa6ac-164">Benzer şekilde, parantez içine alınmış bir dime karakteri `pattern` (kendisiyle, bir listede veya bir aralığa göre), içindeki eşdeğer iki karakterli sırayla eşleşir `string` .</span><span class="sxs-lookup"><span data-stu-id="fa6ac-164">Similarly, a digraph character in `pattern` enclosed in brackets (by itself, in a list, or in a range) matches the equivalent two-character sequence in `string`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="fa6ac-165">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="fa6ac-165">Overloading</span></span>  

 <span data-ttu-id="fa6ac-166">`Like`İşleç *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="fa6ac-166">The `Like` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="fa6ac-167">Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="fa6ac-167">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="fa6ac-168">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="fa6ac-168">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa6ac-169">Örnek</span><span class="sxs-lookup"><span data-stu-id="fa6ac-169">Example</span></span>  

 <span data-ttu-id="fa6ac-170">Bu örnek, `Like` dizeleri çeşitli desenlerle karşılaştırmak için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="fa6ac-170">This example uses the `Like` operator to compare strings to various patterns.</span></span> <span data-ttu-id="fa6ac-171">Sonuçlar, `Boolean` her bir dizenin düzene uygun olup olmadığını gösteren bir değişkene gider.</span><span class="sxs-lookup"><span data-stu-id="fa6ac-171">The results go into a `Boolean` variable indicating whether each string satisfies the pattern.</span></span>  
  
 [!code-vb[VbVbalrOperators#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="fa6ac-172">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa6ac-172">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [<span data-ttu-id="fa6ac-173">Karşılaştırma Işleçleri</span><span class="sxs-lookup"><span data-stu-id="fa6ac-173">Comparison Operators</span></span>](comparison-operators.md)
- [<span data-ttu-id="fa6ac-174">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="fa6ac-174">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="fa6ac-175">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="fa6ac-175">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="fa6ac-176">Option Compare Deyimi</span><span class="sxs-lookup"><span data-stu-id="fa6ac-176">Option Compare Statement</span></span>](../statements/option-compare-statement.md)
- [<span data-ttu-id="fa6ac-177">İşleçler ve Ifadeler</span><span class="sxs-lookup"><span data-stu-id="fa6ac-177">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="fa6ac-178">Nasıl yapılır: Bir Dizeyi Belirli Bir Desene Göre Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="fa6ac-178">How to: Match a String against a Pattern</span></span>](../../programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)
