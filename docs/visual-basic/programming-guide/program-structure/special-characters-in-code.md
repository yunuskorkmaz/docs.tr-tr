---
title: Kod'da Özel Karakterler (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.)
- vb.(
- vb.colon
- vb.!
- vb..
- 'vb.:'
helpviewer_keywords:
- special characters [Visual Basic], in code
- parentheses [Visual Basic], using in code
- colons (:)
- period character in code
- dot operator (.)
- dictionary access operator [Visual Basic]
- concatenation operators [Visual Basic], special characters in code
- concatenation operators [Visual Basic], vs. addition operator
- '! operator'
- separators [Visual Basic], using in code
- operators [Visual Basic], dictionary access
- ': separator character'
- member access operator [Visual Basic]
- addition operator [Visual Basic]
- operators [Visual Basic], member access
- . operator
- exclamation points
- separators
- exclamation point operator (!)
- Visual Basic code, special characters
ms.assetid: 310dce0c-45b5-4e0d-83e9-32df258d2a3e
ms.openlocfilehash: 17b5fcc2be2730abfd7ee0090f9f34053e81c5f8
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971903"
---
# <a name="special-characters-in-code-visual-basic"></a><span data-ttu-id="60fb9-102">Kod'da Özel Karakterler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="60fb9-102">Special Characters in Code (Visual Basic)</span></span>
<span data-ttu-id="60fb9-103">Bazen özel karakterler kodunuzda, diğer bir deyişle, alfabetik veya sayısal olmayan karakterler kullanmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="60fb9-103">Sometimes you have to use special characters in your code, that is, characters that are not alphabetical or numeric.</span></span> <span data-ttu-id="60fb9-104">Noktalama işaretleri ve özel karakterler Visual temel karakter kümesinde derleyici veya derlenmiş programın gerçekleştirdiği görevler tanımlama program metni düzenleme gelen çeşitli kullanımlar sahip.</span><span class="sxs-lookup"><span data-stu-id="60fb9-104">The punctuation and special characters in the Visual Basic character set have various uses, from organizing program text to defining the tasks that the compiler or the compiled program performs.</span></span> <span data-ttu-id="60fb9-105">Gerçekleştirilecek bir işlemi belirtmeyin.</span><span class="sxs-lookup"><span data-stu-id="60fb9-105">They do not specify an operation to be performed.</span></span>  
  
## <a name="parentheses"></a><span data-ttu-id="60fb9-106">Parantez</span><span class="sxs-lookup"><span data-stu-id="60fb9-106">Parentheses</span></span>  
 <span data-ttu-id="60fb9-107">Bir yordam gibi tanımlarken parantez kullanan bir `Sub` veya `Function`.</span><span class="sxs-lookup"><span data-stu-id="60fb9-107">Use parentheses when you define a procedure, such as a `Sub` or `Function`.</span></span> <span data-ttu-id="60fb9-108">Tüm yordam bağımsız değişken listeleri parantez içine almalısınız.</span><span class="sxs-lookup"><span data-stu-id="60fb9-108">You must enclose all procedure argument lists in parentheses.</span></span> <span data-ttu-id="60fb9-109">De parantez değişkenleri ya da bağımsız değişkenler mantıksal gruplar halinde koymak için özellikle karmaşık bir ifadede İşleç önceliği varsayılan düzenini geçersiz kılmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60fb9-109">You also use parentheses for putting variables or arguments into logical groups, especially to override the default order of operator precedence in a complex expression.</span></span> <span data-ttu-id="60fb9-110">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="60fb9-110">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#11)]  
  
 <span data-ttu-id="60fb9-111">Değerini önceki kodu yürütülmesinin `d` 8.225 ve değerini `e` 3'tür.</span><span class="sxs-lookup"><span data-stu-id="60fb9-111">Following execution of the previous code, the value of `d` is 8.225 and the value of `e` is 3.</span></span> <span data-ttu-id="60fb9-112">Hesaplama için `d` varsayılan önceliği kullanan `/` üzerinden `+` ve eşdeğerdir `d = b + (c / a)`.</span><span class="sxs-lookup"><span data-stu-id="60fb9-112">The calculation for `d` uses the default precedence of `/` over `+` and is equivalent to `d = b + (c / a)`.</span></span> <span data-ttu-id="60fb9-113">Hesaplama için parantezler `e` varsayılan önceliği geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="60fb9-113">The parentheses in the calculation for `e` override the default precedence.</span></span>  
  
## <a name="separators"></a><span data-ttu-id="60fb9-114">Ayırıcı</span><span class="sxs-lookup"><span data-stu-id="60fb9-114">Separators</span></span>  
 <span data-ttu-id="60fb9-115">Ayırıcılar yapmak ne kendi adından da anlaşılacağı: Bunlar kod bölümlerini ayırın.</span><span class="sxs-lookup"><span data-stu-id="60fb9-115">Separators do what their name suggests: they separate sections of code.</span></span> <span data-ttu-id="60fb9-116">Visual Basic'te iki nokta üst üste ayırıcı karakteridir (`:`).</span><span class="sxs-lookup"><span data-stu-id="60fb9-116">In Visual Basic, the separator character is the colon (`:`).</span></span> <span data-ttu-id="60fb9-117">Birden çok deyime ayrı satırlara yerine tek bir satırda dahil etmek istediğiniz zaman ayırıcı kullanın.</span><span class="sxs-lookup"><span data-stu-id="60fb9-117">Use separators when you want to include multiple statements on a single line instead of separate lines.</span></span> <span data-ttu-id="60fb9-118">Bu alan tasarrufu yapılmasını sağlar ve kodunuzun okunabilirliği geliştirir.</span><span class="sxs-lookup"><span data-stu-id="60fb9-118">This saves space and improves the readability of your code.</span></span> <span data-ttu-id="60fb9-119">Aşağıdaki örnek, üç deyimi virgülle ayırarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="60fb9-119">The following example shows three statements separated by colons.</span></span>  
  
 [!code-vb[VbVbcnConventions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#12)]  
  
 <span data-ttu-id="60fb9-120">Daha fazla bilgi için [nasıl yapılır: Kodda deyimleri bölme ve birleştirme](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="60fb9-120">For more information, see [How to: Break and Combine Statements in Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span></span>  
  
 <span data-ttu-id="60fb9-121">İki nokta üst üste (`:`) karakter deyimi etiketi belirlemek için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="60fb9-121">The colon (`:`) character is also used to identify a statement label.</span></span> <span data-ttu-id="60fb9-122">Daha fazla bilgi için [nasıl yapılır: Etiket deyimleri](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span><span class="sxs-lookup"><span data-stu-id="60fb9-122">For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
## <a name="concatenation"></a><span data-ttu-id="60fb9-123">Bitiştirme</span><span class="sxs-lookup"><span data-stu-id="60fb9-123">Concatenation</span></span>  
 <span data-ttu-id="60fb9-124">Kullanım `&` işleci için *birleştirme*, veya dizeleri birbirine bağlayarak.</span><span class="sxs-lookup"><span data-stu-id="60fb9-124">Use the `&` operator for *concatenation*, or linking strings together.</span></span> <span data-ttu-id="60fb9-125">İle karıştırmayın `+` işleci, sayısal değerleri toplar.</span><span class="sxs-lookup"><span data-stu-id="60fb9-125">Do not confuse it with the `+` operator, which adds together numeric values.</span></span> <span data-ttu-id="60fb9-126">Kullanırsanız `+` işleci sayısal değerler üzerinde çalışır, birleştirmek için hatalı sonuçlar elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60fb9-126">If you use the `+` operator to concatenate when you operate on numeric values, you can obtain incorrect results.</span></span> <span data-ttu-id="60fb9-127">Aşağıdaki örnekte bu gösterir.</span><span class="sxs-lookup"><span data-stu-id="60fb9-127">The following example demonstrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#13)]  
  
 <span data-ttu-id="60fb9-128">Değerini önceki kodu yürütülmesinin `resultA` 21.01 ve değerini `resultB` "10.0111" olduğu.</span><span class="sxs-lookup"><span data-stu-id="60fb9-128">Following execution of the previous code, the value of `resultA` is 21.01 and the value of `resultB` is "10.0111".</span></span>  
  
## <a name="member-access-operators"></a><span data-ttu-id="60fb9-129">Üye erişim işleçleri</span><span class="sxs-lookup"><span data-stu-id="60fb9-129">Member Access Operators</span></span>  
 <span data-ttu-id="60fb9-130">Türünün bir üyesine erişmek için nokta kullanın (`.`) ya da ünlem işareti (`!`) arasında tür adı ve üye adı işleci.</span><span class="sxs-lookup"><span data-stu-id="60fb9-130">To access a member of a type, you use the dot (`.`) or exclamation point (`!`) operator between the type name and the member name.</span></span>  
  
### <a name="dot--operator"></a><span data-ttu-id="60fb9-131">Nokta (.) İşleç</span><span class="sxs-lookup"><span data-stu-id="60fb9-131">Dot (.) Operator</span></span>  
 <span data-ttu-id="60fb9-132">Kullanım `.` sınıfı, yapı, arabirim ya da numaralandırma işlecinin bir üye erişim işleci olarak.</span><span class="sxs-lookup"><span data-stu-id="60fb9-132">Use the `.` operator on a class, structure, interface, or enumeration as a member access operator.</span></span> <span data-ttu-id="60fb9-133">Üye bir alan, özelliği, olay veya yöntemi olabilir.</span><span class="sxs-lookup"><span data-stu-id="60fb9-133">The member can be a field, property, event, or method.</span></span> <span data-ttu-id="60fb9-134">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="60fb9-134">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#14)]  
  
### <a name="exclamation-point--operator"></a><span data-ttu-id="60fb9-135">Ünlem işareti (!) İşleç</span><span class="sxs-lookup"><span data-stu-id="60fb9-135">Exclamation Point (!) Operator</span></span>  
 <span data-ttu-id="60fb9-136">Kullanım `!` sözlük erişim işleci olarak yalnızca bir sınıf veya arabirim üzerinde işleci.</span><span class="sxs-lookup"><span data-stu-id="60fb9-136">Use the `!` operator only on a class or interface as a dictionary access operator.</span></span> <span data-ttu-id="60fb9-137">Sınıf veya arabirim kabul eden tek bir varsayılan özellik olmalıdır `String` bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="60fb9-137">The class or interface must have a default property that accepts a single `String` argument.</span></span> <span data-ttu-id="60fb9-138">Hemen tanımlayıcısı `!` işleci bir dize olarak varsayılan özelliği için geçirilen bağımsız değişken değeri olur.</span><span class="sxs-lookup"><span data-stu-id="60fb9-138">The identifier immediately following the `!` operator becomes the argument value passed to the default property as a string.</span></span> <span data-ttu-id="60fb9-139">Aşağıdaki örnekte bu gösterir.</span><span class="sxs-lookup"><span data-stu-id="60fb9-139">The following example demonstrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#15)]  
  
 <span data-ttu-id="60fb9-140">Üç satır çıkış `MsgBox` tüm görüntüleme `32856`.</span><span class="sxs-lookup"><span data-stu-id="60fb9-140">The three output lines of `MsgBox` all display the value `32856`.</span></span> <span data-ttu-id="60fb9-141">Geleneksel erişim özelliği ilk satırını kullanır `index`, ikinci kullanır olgu, `index` sınıfın varsayılan özelliğidir `hasDefault`, ve üçüncü sözlük erişimi sınıfı kullanır.</span><span class="sxs-lookup"><span data-stu-id="60fb9-141">The first line uses the traditional access to property `index`, the second makes use of the fact that `index` is the default property of class `hasDefault`, and the third uses dictionary access to the class.</span></span>  
  
 <span data-ttu-id="60fb9-142">Unutmayın, ikinci işlenenin `!` işleci, çift tırnak işaretleri arasına değil, geçerli bir Visual Basic tanımlayıcı olmalıdır (`" "`).</span><span class="sxs-lookup"><span data-stu-id="60fb9-142">Note that the second operand of the `!` operator must be a valid Visual Basic identifier not enclosed in double quotation marks (`" "`).</span></span> <span data-ttu-id="60fb9-143">Diğer bir deyişle, bir dize sabit değeri veya dize değişkeni kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="60fb9-143">In other words, you cannot use a string literal or string variable.</span></span> <span data-ttu-id="60fb9-144">Şu son satırını değiştirin `MsgBox` çağrı olduğundan hata oluşturur `"X"` kapalı bir dize sabitidir.</span><span class="sxs-lookup"><span data-stu-id="60fb9-144">The following change to the last line of the `MsgBox` call generates an error because `"X"` is an enclosed string literal.</span></span>  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
>  <span data-ttu-id="60fb9-145">Varsayılan koleksiyon başvuruları açık olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="60fb9-145">References to default collections must be explicit.</span></span> <span data-ttu-id="60fb9-146">Özellikle, kullanamazsınız `!` geç bağlanan bir değişken üzerinde işleci.</span><span class="sxs-lookup"><span data-stu-id="60fb9-146">In particular, you cannot use the `!` operator on a late-bound variable.</span></span>  
  
 <span data-ttu-id="60fb9-147">`!` Karakter olarak kullanılan ayrıca `Single` karakter yazın.</span><span class="sxs-lookup"><span data-stu-id="60fb9-147">The `!` character is also used as the `Single` type character.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60fb9-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60fb9-148">See also</span></span>
- [<span data-ttu-id="60fb9-149">Program Yapısı ve Kod Kuralları</span><span class="sxs-lookup"><span data-stu-id="60fb9-149">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [<span data-ttu-id="60fb9-150">Tür Karakterleri</span><span class="sxs-lookup"><span data-stu-id="60fb9-150">Type Characters</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
