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
ms.openlocfilehash: 95bef937912e35cd828bf0090b4cf48ccb3290cc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962475"
---
# <a name="special-characters-in-code-visual-basic"></a><span data-ttu-id="59100-102">Kod'da Özel Karakterler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="59100-102">Special Characters in Code (Visual Basic)</span></span>
<span data-ttu-id="59100-103">Bazen kodunuzda özel karakterler kullanmanız gerekir, diğer bir deyişle, alfabetik veya sayısal olmayan karakterler.</span><span class="sxs-lookup"><span data-stu-id="59100-103">Sometimes you have to use special characters in your code, that is, characters that are not alphabetical or numeric.</span></span> <span data-ttu-id="59100-104">Visual Basic karakter kümesindeki noktalama ve özel karakterlerin çeşitli kullanımları vardır ve program metnini, derleyicinin ya da derlenmiş programın gerçekleştirdiği görevleri tanımlamaya yönelik olarak düzenler.</span><span class="sxs-lookup"><span data-stu-id="59100-104">The punctuation and special characters in the Visual Basic character set have various uses, from organizing program text to defining the tasks that the compiler or the compiled program performs.</span></span> <span data-ttu-id="59100-105">Gerçekleştirilecek bir işlem belirtmez.</span><span class="sxs-lookup"><span data-stu-id="59100-105">They do not specify an operation to be performed.</span></span>  
  
## <a name="parentheses"></a><span data-ttu-id="59100-106">Ayraçlar</span><span class="sxs-lookup"><span data-stu-id="59100-106">Parentheses</span></span>  
 <span data-ttu-id="59100-107">`Sub` Veya`Function`gibi bir yordam tanımladığınızda ayraçları kullanın.</span><span class="sxs-lookup"><span data-stu-id="59100-107">Use parentheses when you define a procedure, such as a `Sub` or `Function`.</span></span> <span data-ttu-id="59100-108">Tüm yordam bağımsız değişken listelerini parantez içine almalısınız.</span><span class="sxs-lookup"><span data-stu-id="59100-108">You must enclose all procedure argument lists in parentheses.</span></span> <span data-ttu-id="59100-109">Ayrıca, özellikle karmaşık bir ifadede işleç önceliği varsayılan sırasını geçersiz kılmak için, değişkenleri veya bağımsız değişkenleri mantıksal gruplara koymak için parantez de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59100-109">You also use parentheses for putting variables or arguments into logical groups, especially to override the default order of operator precedence in a complex expression.</span></span> <span data-ttu-id="59100-110">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="59100-110">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#11)]  
  
 <span data-ttu-id="59100-111">Önceki kodun yürütülmesi sonrasında, değeri `d` 8,225 ve `e` değeri 3 ' dir.</span><span class="sxs-lookup"><span data-stu-id="59100-111">Following execution of the previous code, the value of `d` is 8.225 and the value of `e` is 3.</span></span> <span data-ttu-id="59100-112">İçin `d` hesaplama, '`+` ın `/` ' de `d = b + (c / a)`varsayılan önceliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="59100-112">The calculation for `d` uses the default precedence of `/` over `+` and is equivalent to `d = b + (c / a)`.</span></span> <span data-ttu-id="59100-113">Hesaplama içindeki parantezler varsayılan önceliği `e` geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="59100-113">The parentheses in the calculation for `e` override the default precedence.</span></span>  
  
## <a name="separators"></a><span data-ttu-id="59100-114">Ayırıcı</span><span class="sxs-lookup"><span data-stu-id="59100-114">Separators</span></span>  
 <span data-ttu-id="59100-115">Ayırıcılar, adının ne gibi bir bölümünü ayırır:</span><span class="sxs-lookup"><span data-stu-id="59100-115">Separators do what their name suggests: they separate sections of code.</span></span> <span data-ttu-id="59100-116">Visual Basic, ayırıcı karakter iki nokta (`:`) ' dır.</span><span class="sxs-lookup"><span data-stu-id="59100-116">In Visual Basic, the separator character is the colon (`:`).</span></span> <span data-ttu-id="59100-117">Ayrı satırlar yerine tek bir satıra birden çok deyim eklemek istediğinizde ayırıcılar kullanın.</span><span class="sxs-lookup"><span data-stu-id="59100-117">Use separators when you want to include multiple statements on a single line instead of separate lines.</span></span> <span data-ttu-id="59100-118">Bu, alanı kaydeder ve kodunuzun okunabilirliğini geliştirir.</span><span class="sxs-lookup"><span data-stu-id="59100-118">This saves space and improves the readability of your code.</span></span> <span data-ttu-id="59100-119">Aşağıdaki örnekte, iki nokta üst üste ile ayrılmış üç deyim gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="59100-119">The following example shows three statements separated by colons.</span></span>  
  
 [!code-vb[VbVbcnConventions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#12)]  
  
 <span data-ttu-id="59100-120">Daha fazla bilgi için [nasıl yapılır: Koddaki](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)deyimleri bölün ve birleştirin.</span><span class="sxs-lookup"><span data-stu-id="59100-120">For more information, see [How to: Break and Combine Statements in Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span></span>  
  
 <span data-ttu-id="59100-121">İki nokta (`:`) karakteri de bir ifade etiketini tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="59100-121">The colon (`:`) character is also used to identify a statement label.</span></span> <span data-ttu-id="59100-122">Daha fazla bilgi için [nasıl yapılır: Label deyimleri](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span><span class="sxs-lookup"><span data-stu-id="59100-122">For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
## <a name="concatenation"></a><span data-ttu-id="59100-123">Bitiştirme</span><span class="sxs-lookup"><span data-stu-id="59100-123">Concatenation</span></span>  
 <span data-ttu-id="59100-124">Birleştirmek veya dizeleri birbirinebağlamak için işlecinikullanın.`&`</span><span class="sxs-lookup"><span data-stu-id="59100-124">Use the `&` operator for *concatenation*, or linking strings together.</span></span> <span data-ttu-id="59100-125">Sayısal değerleri bir araya ekleyen `+` işleçle karıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="59100-125">Do not confuse it with the `+` operator, which adds together numeric values.</span></span> <span data-ttu-id="59100-126">Sayısal değerler üzerinde çalışırken `+` birleştirme için işlecini kullanırsanız, yanlış sonuçlar elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59100-126">If you use the `+` operator to concatenate when you operate on numeric values, you can obtain incorrect results.</span></span> <span data-ttu-id="59100-127">Aşağıdaki örnek bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="59100-127">The following example demonstrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#13)]  
  
 <span data-ttu-id="59100-128">Önceki kodun yürütülmesi sonrasında, değeri `resultA` 21,01 ve `resultB` değeri "10,0111" olur.</span><span class="sxs-lookup"><span data-stu-id="59100-128">Following execution of the previous code, the value of `resultA` is 21.01 and the value of `resultB` is "10.0111".</span></span>  
  
## <a name="member-access-operators"></a><span data-ttu-id="59100-129">Üye erişim Işleçleri</span><span class="sxs-lookup"><span data-stu-id="59100-129">Member Access Operators</span></span>  
 <span data-ttu-id="59100-130">Bir türün üyesine erişmek için, tür adı ve üye adı arasında nokta`.`() veya ünlem işareti`!`() işlecini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="59100-130">To access a member of a type, you use the dot (`.`) or exclamation point (`!`) operator between the type name and the member name.</span></span>  
  
### <a name="dot--operator"></a><span data-ttu-id="59100-131">Nokta (.) İşleç</span><span class="sxs-lookup"><span data-stu-id="59100-131">Dot (.) Operator</span></span>  
 <span data-ttu-id="59100-132">`.` İşleci bir sınıf, yapı, arabirim veya sabit listesi üzerinde üye erişim işleci olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="59100-132">Use the `.` operator on a class, structure, interface, or enumeration as a member access operator.</span></span> <span data-ttu-id="59100-133">Üye bir alan, özellik, olay veya yöntem olabilir.</span><span class="sxs-lookup"><span data-stu-id="59100-133">The member can be a field, property, event, or method.</span></span> <span data-ttu-id="59100-134">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="59100-134">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#14)]  
  
### <a name="exclamation-point--operator"></a><span data-ttu-id="59100-135">Ünlem işareti (!) İşleç</span><span class="sxs-lookup"><span data-stu-id="59100-135">Exclamation Point (!) Operator</span></span>  
 <span data-ttu-id="59100-136">`!` İşleci yalnızca bir sınıf veya arabirimde sözlük erişim işleci olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="59100-136">Use the `!` operator only on a class or interface as a dictionary access operator.</span></span> <span data-ttu-id="59100-137">Sınıfın veya arabirimin tek `String` bir bağımsız değişkeni kabul eden bir varsayılan özelliği olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="59100-137">The class or interface must have a default property that accepts a single `String` argument.</span></span> <span data-ttu-id="59100-138">`!` İşlecinden hemen sonraki tanımlayıcı, varsayılan özelliğe dize olarak geçirilen bağımsız değişken değeri olur.</span><span class="sxs-lookup"><span data-stu-id="59100-138">The identifier immediately following the `!` operator becomes the argument value passed to the default property as a string.</span></span> <span data-ttu-id="59100-139">Aşağıdaki örnek bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="59100-139">The following example demonstrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#15)]  
  
 <span data-ttu-id="59100-140">Her birinin `MsgBox` üç çıkış satırı değeri `32856`görüntüler.</span><span class="sxs-lookup"><span data-stu-id="59100-140">The three output lines of `MsgBox` all display the value `32856`.</span></span> <span data-ttu-id="59100-141">İlk satır geleneksel erişim özelliğini `index`kullanır, ikincisi sınıfının `hasDefault`varsayılan özelliği olan `index` olguyu kullanır ve üçüncüsü ise sınıfa sözlük erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="59100-141">The first line uses the traditional access to property `index`, the second makes use of the fact that `index` is the default property of class `hasDefault`, and the third uses dictionary access to the class.</span></span>  
  
 <span data-ttu-id="59100-142">`!` İşlecin ikinci işleneninin, çift tırnak işaretleri (`" "`) içine alınmış geçerli bir Visual Basic tanımlayıcı olması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="59100-142">Note that the second operand of the `!` operator must be a valid Visual Basic identifier not enclosed in double quotation marks (`" "`).</span></span> <span data-ttu-id="59100-143">Diğer bir deyişle, bir dize sabit değeri veya dize değişkeni kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="59100-143">In other words, you cannot use a string literal or string variable.</span></span> <span data-ttu-id="59100-144">`MsgBox` Çağrının son satırına yapılan aşağıdaki değişiklik bir hata oluşturur çünkü `"X"` bir kapalı dize sabit değeri.</span><span class="sxs-lookup"><span data-stu-id="59100-144">The following change to the last line of the `MsgBox` call generates an error because `"X"` is an enclosed string literal.</span></span>  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
> <span data-ttu-id="59100-145">Varsayılan koleksiyonlara yapılan başvurular açık olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="59100-145">References to default collections must be explicit.</span></span> <span data-ttu-id="59100-146">Özellikle, `!` işlecini geç bağlı bir değişkende kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="59100-146">In particular, you cannot use the `!` operator on a late-bound variable.</span></span>  
  
 <span data-ttu-id="59100-147">Karakter, `Single` tür karakteri olarak da kullanılır. `!`</span><span class="sxs-lookup"><span data-stu-id="59100-147">The `!` character is also used as the `Single` type character.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59100-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59100-148">See also</span></span>

- [<span data-ttu-id="59100-149">Program Yapısı ve Kod Kuralları</span><span class="sxs-lookup"><span data-stu-id="59100-149">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [<span data-ttu-id="59100-150">Tür Karakterleri</span><span class="sxs-lookup"><span data-stu-id="59100-150">Type Characters</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
