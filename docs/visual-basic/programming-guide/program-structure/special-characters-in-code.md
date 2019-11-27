---
title: Kod'da Özel Karakterler
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
ms.openlocfilehash: f4ab35b56d48ae86bdb024ffea27735b39decdc2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347263"
---
# <a name="special-characters-in-code-visual-basic"></a><span data-ttu-id="b6034-102">Kod'da Özel Karakterler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b6034-102">Special Characters in Code (Visual Basic)</span></span>
<span data-ttu-id="b6034-103">Bazen kodunuzda özel karakterler kullanmanız gerekir, diğer bir deyişle, alfabetik veya sayısal olmayan karakterler.</span><span class="sxs-lookup"><span data-stu-id="b6034-103">Sometimes you have to use special characters in your code, that is, characters that are not alphabetical or numeric.</span></span> <span data-ttu-id="b6034-104">Visual Basic karakter kümesindeki noktalama ve özel karakterlerin çeşitli kullanımları vardır ve program metnini, derleyicinin ya da derlenmiş programın gerçekleştirdiği görevleri tanımlamaya yönelik olarak düzenler.</span><span class="sxs-lookup"><span data-stu-id="b6034-104">The punctuation and special characters in the Visual Basic character set have various uses, from organizing program text to defining the tasks that the compiler or the compiled program performs.</span></span> <span data-ttu-id="b6034-105">Gerçekleştirilecek bir işlem belirtmez.</span><span class="sxs-lookup"><span data-stu-id="b6034-105">They do not specify an operation to be performed.</span></span>  
  
## <a name="parentheses"></a><span data-ttu-id="b6034-106">ayraçlar</span><span class="sxs-lookup"><span data-stu-id="b6034-106">Parentheses</span></span>  
 <span data-ttu-id="b6034-107">`Sub` veya `Function`gibi bir yordam tanımlarken ayraçları kullanın.</span><span class="sxs-lookup"><span data-stu-id="b6034-107">Use parentheses when you define a procedure, such as a `Sub` or `Function`.</span></span> <span data-ttu-id="b6034-108">Tüm yordam bağımsız değişken listelerini parantez içine almalısınız.</span><span class="sxs-lookup"><span data-stu-id="b6034-108">You must enclose all procedure argument lists in parentheses.</span></span> <span data-ttu-id="b6034-109">Ayrıca, özellikle karmaşık bir ifadede işleç önceliği varsayılan sırasını geçersiz kılmak için, değişkenleri veya bağımsız değişkenleri mantıksal gruplara koymak için parantez de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6034-109">You also use parentheses for putting variables or arguments into logical groups, especially to override the default order of operator precedence in a complex expression.</span></span> <span data-ttu-id="b6034-110">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="b6034-110">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#11)]  
  
 <span data-ttu-id="b6034-111">Önceki kodun yürütülmesi sırasında, `d` değeri 8,225 ve `e` değeri 3 ' dir.</span><span class="sxs-lookup"><span data-stu-id="b6034-111">Following execution of the previous code, the value of `d` is 8.225 and the value of `e` is 3.</span></span> <span data-ttu-id="b6034-112">`d` hesaplama, `/` varsayılan önceliği `+` kullanır ve `d = b + (c / a)`eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="b6034-112">The calculation for `d` uses the default precedence of `/` over `+` and is equivalent to `d = b + (c / a)`.</span></span> <span data-ttu-id="b6034-113">`e` hesaplamasında parantez varsayılan önceliği geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="b6034-113">The parentheses in the calculation for `e` override the default precedence.</span></span>  
  
## <a name="separators"></a><span data-ttu-id="b6034-114">Ayırıcı</span><span class="sxs-lookup"><span data-stu-id="b6034-114">Separators</span></span>  
 <span data-ttu-id="b6034-115">Ayırıcılar, adının ne gibi bir bölümünü ayırır:</span><span class="sxs-lookup"><span data-stu-id="b6034-115">Separators do what their name suggests: they separate sections of code.</span></span> <span data-ttu-id="b6034-116">Visual Basic, ayırıcı karakter iki nokta olur (`:`).</span><span class="sxs-lookup"><span data-stu-id="b6034-116">In Visual Basic, the separator character is the colon (`:`).</span></span> <span data-ttu-id="b6034-117">Ayrı satırlar yerine tek bir satıra birden çok deyim eklemek istediğinizde ayırıcılar kullanın.</span><span class="sxs-lookup"><span data-stu-id="b6034-117">Use separators when you want to include multiple statements on a single line instead of separate lines.</span></span> <span data-ttu-id="b6034-118">Bu, alanı kaydeder ve kodunuzun okunabilirliğini geliştirir.</span><span class="sxs-lookup"><span data-stu-id="b6034-118">This saves space and improves the readability of your code.</span></span> <span data-ttu-id="b6034-119">Aşağıdaki örnekte, iki nokta üst üste ile ayrılmış üç deyim gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b6034-119">The following example shows three statements separated by colons.</span></span>  
  
 [!code-vb[VbVbcnConventions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#12)]  
  
 <span data-ttu-id="b6034-120">Daha fazla bilgi için bkz. [nasıl yapılır: kod Içinde deyimleri kesme ve birleştirme](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="b6034-120">For more information, see [How to: Break and Combine Statements in Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span></span>  
  
 <span data-ttu-id="b6034-121">İki nokta (`:`) karakteri de bir ifade etiketini tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b6034-121">The colon (`:`) character is also used to identify a statement label.</span></span> <span data-ttu-id="b6034-122">Daha fazla bilgi için bkz. [nasıl yapılır: Label deyimleri](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span><span class="sxs-lookup"><span data-stu-id="b6034-122">For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
## <a name="concatenation"></a><span data-ttu-id="b6034-123">Birleştirme</span><span class="sxs-lookup"><span data-stu-id="b6034-123">Concatenation</span></span>  
 <span data-ttu-id="b6034-124">*Birleştirmek*veya dizeleri birbirine bağlamak için `&` işlecini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b6034-124">Use the `&` operator for *concatenation*, or linking strings together.</span></span> <span data-ttu-id="b6034-125">Sayısal değerleri bir araya ekleyen `+` işleçle karıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="b6034-125">Do not confuse it with the `+` operator, which adds together numeric values.</span></span> <span data-ttu-id="b6034-126">Sayısal değerler üzerinde çalışırken birleştirmek için `+` işlecini kullanırsanız, yanlış sonuçlar elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6034-126">If you use the `+` operator to concatenate when you operate on numeric values, you can obtain incorrect results.</span></span> <span data-ttu-id="b6034-127">Aşağıdaki örnek bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6034-127">The following example demonstrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#13)]  
  
 <span data-ttu-id="b6034-128">Önceki kodun yürütülmesi sırasında, `resultA` değeri 21,01 ve `resultB` değeri "10,0111" olur.</span><span class="sxs-lookup"><span data-stu-id="b6034-128">Following execution of the previous code, the value of `resultA` is 21.01 and the value of `resultB` is "10.0111".</span></span>  
  
## <a name="member-access-operators"></a><span data-ttu-id="b6034-129">Üye erişim Işleçleri</span><span class="sxs-lookup"><span data-stu-id="b6034-129">Member Access Operators</span></span>  
 <span data-ttu-id="b6034-130">Bir türün üyesine erişmek için, tür adı ve üye adı arasında nokta (`.`) veya ünlem işareti (`!`) işlecini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="b6034-130">To access a member of a type, you use the dot (`.`) or exclamation point (`!`) operator between the type name and the member name.</span></span>  
  
### <a name="dot--operator"></a><span data-ttu-id="b6034-131">Nokta (.) İşlecinde</span><span class="sxs-lookup"><span data-stu-id="b6034-131">Dot (.) Operator</span></span>  
 <span data-ttu-id="b6034-132">Bir sınıf, yapı, arabirim veya sabit listesi üzerinde `.` işlecini üye erişim işleci olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="b6034-132">Use the `.` operator on a class, structure, interface, or enumeration as a member access operator.</span></span> <span data-ttu-id="b6034-133">Üye bir alan, özellik, olay veya yöntem olabilir.</span><span class="sxs-lookup"><span data-stu-id="b6034-133">The member can be a field, property, event, or method.</span></span> <span data-ttu-id="b6034-134">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="b6034-134">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#14)]  
  
### <a name="exclamation-point--operator"></a><span data-ttu-id="b6034-135">Ünlem işareti (!) İşlecinde</span><span class="sxs-lookup"><span data-stu-id="b6034-135">Exclamation Point (!) Operator</span></span>  
 <span data-ttu-id="b6034-136">`!` işlecini yalnızca bir sınıf veya arabirimde sözlük erişim işleci olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="b6034-136">Use the `!` operator only on a class or interface as a dictionary access operator.</span></span> <span data-ttu-id="b6034-137">Sınıfın veya arabirimin tek bir `String` bağımsız değişkenini kabul eden bir varsayılan özelliği olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b6034-137">The class or interface must have a default property that accepts a single `String` argument.</span></span> <span data-ttu-id="b6034-138">`!` işlecinden hemen sonraki tanımlayıcı, varsayılan özelliğe dize olarak geçirilen bağımsız değişken değeri olur.</span><span class="sxs-lookup"><span data-stu-id="b6034-138">The identifier immediately following the `!` operator becomes the argument value passed to the default property as a string.</span></span> <span data-ttu-id="b6034-139">Aşağıdaki örnek bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6034-139">The following example demonstrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#15)]  
  
 <span data-ttu-id="b6034-140">`MsgBox` her birinin üç çıkış satırı `32856`değeri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="b6034-140">The three output lines of `MsgBox` all display the value `32856`.</span></span> <span data-ttu-id="b6034-141">İlk satır, özellik `index`için geleneksel erişimi kullanır, ikincisi, `index` sınıfının varsayılan özelliği olan `hasDefault`ve üçüncü sözlük ise sınıfa erişimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="b6034-141">The first line uses the traditional access to property `index`, the second makes use of the fact that `index` is the default property of class `hasDefault`, and the third uses dictionary access to the class.</span></span>  
  
 <span data-ttu-id="b6034-142">`!` işlecinin ikinci işleneni, çift tırnak işaretleri (`" "`) içine alınmış geçerli bir Visual Basic tanımlayıcısı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b6034-142">Note that the second operand of the `!` operator must be a valid Visual Basic identifier not enclosed in double quotation marks (`" "`).</span></span> <span data-ttu-id="b6034-143">Diğer bir deyişle, bir dize sabit değeri veya dize değişkeni kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="b6034-143">In other words, you cannot use a string literal or string variable.</span></span> <span data-ttu-id="b6034-144">`MsgBox` çağrısının son satırına yapılan aşağıdaki değişiklik bir hata üretir çünkü `"X"` bir kapalı dize sabit değeri.</span><span class="sxs-lookup"><span data-stu-id="b6034-144">The following change to the last line of the `MsgBox` call generates an error because `"X"` is an enclosed string literal.</span></span>  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
> <span data-ttu-id="b6034-145">Varsayılan koleksiyonlara yapılan başvurular açık olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b6034-145">References to default collections must be explicit.</span></span> <span data-ttu-id="b6034-146">Özellikle, `!` işlecini geç bağlı bir değişkende kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="b6034-146">In particular, you cannot use the `!` operator on a late-bound variable.</span></span>  
  
 <span data-ttu-id="b6034-147">`!` karakteri `Single` tür karakteri olarak da kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b6034-147">The `!` character is also used as the `Single` type character.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6034-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6034-148">See also</span></span>

- [<span data-ttu-id="b6034-149">Program Yapısı ve Kod Kuralları</span><span class="sxs-lookup"><span data-stu-id="b6034-149">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [<span data-ttu-id="b6034-150">Tür Karakterleri</span><span class="sxs-lookup"><span data-stu-id="b6034-150">Type Characters</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
