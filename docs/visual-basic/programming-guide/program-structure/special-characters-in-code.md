---
description: 'Hakkında daha fazla bilgi edinin: koddaki özel karakterler (Visual Basic)'
title: Koddaki Özel Karakterler
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
ms.openlocfilehash: 4afadc13cea6cc41480cb1674b7ff6f31629b569
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100468258"
---
# <a name="special-characters-in-code-visual-basic"></a><span data-ttu-id="0a13a-103">Kod'da Özel Karakterler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a13a-103">Special Characters in Code (Visual Basic)</span></span>

<span data-ttu-id="0a13a-104">Bazen kodunuzda özel karakterler kullanmanız gerekir, diğer bir deyişle, alfabetik veya sayısal olmayan karakterler.</span><span class="sxs-lookup"><span data-stu-id="0a13a-104">Sometimes you have to use special characters in your code, that is, characters that are not alphabetical or numeric.</span></span> <span data-ttu-id="0a13a-105">Visual Basic karakter kümesindeki noktalama ve özel karakterlerin çeşitli kullanımları vardır ve program metnini, derleyicinin ya da derlenmiş programın gerçekleştirdiği görevleri tanımlamaya yönelik olarak düzenler.</span><span class="sxs-lookup"><span data-stu-id="0a13a-105">The punctuation and special characters in the Visual Basic character set have various uses, from organizing program text to defining the tasks that the compiler or the compiled program performs.</span></span> <span data-ttu-id="0a13a-106">Gerçekleştirilecek bir işlem belirtmez.</span><span class="sxs-lookup"><span data-stu-id="0a13a-106">They do not specify an operation to be performed.</span></span>  
  
## <a name="parentheses"></a><span data-ttu-id="0a13a-107">Parantez</span><span class="sxs-lookup"><span data-stu-id="0a13a-107">Parentheses</span></span>  

 <span data-ttu-id="0a13a-108">Veya gibi bir yordam tanımladığınızda ayraçları kullanın `Sub` `Function` .</span><span class="sxs-lookup"><span data-stu-id="0a13a-108">Use parentheses when you define a procedure, such as a `Sub` or `Function`.</span></span> <span data-ttu-id="0a13a-109">Tüm yordam bağımsız değişken listelerini parantez içine almalısınız.</span><span class="sxs-lookup"><span data-stu-id="0a13a-109">You must enclose all procedure argument lists in parentheses.</span></span> <span data-ttu-id="0a13a-110">Ayrıca, özellikle karmaşık bir ifadede işleç önceliği varsayılan sırasını geçersiz kılmak için, değişkenleri veya bağımsız değişkenleri mantıksal gruplara koymak için parantez de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0a13a-110">You also use parentheses for putting variables or arguments into logical groups, especially to override the default order of operator precedence in a complex expression.</span></span> <span data-ttu-id="0a13a-111">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="0a13a-111">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#11)]  
  
 <span data-ttu-id="0a13a-112">Önceki kodun yürütülmesi sonrasında, değeri `d` 8,225 ve değeri 3 ' dir `e` .</span><span class="sxs-lookup"><span data-stu-id="0a13a-112">Following execution of the previous code, the value of `d` is 8.225 and the value of `e` is 3.</span></span> <span data-ttu-id="0a13a-113">İçin hesaplama, `d` `/` ' ın ' de varsayılan önceliğini kullanır `+` `d = b + (c / a)` .</span><span class="sxs-lookup"><span data-stu-id="0a13a-113">The calculation for `d` uses the default precedence of `/` over `+` and is equivalent to `d = b + (c / a)`.</span></span> <span data-ttu-id="0a13a-114">Hesaplama içindeki parantezler `e` varsayılan önceliği geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="0a13a-114">The parentheses in the calculation for `e` override the default precedence.</span></span>  
  
## <a name="separators"></a><span data-ttu-id="0a13a-115">Ayırıcı</span><span class="sxs-lookup"><span data-stu-id="0a13a-115">Separators</span></span>  

 <span data-ttu-id="0a13a-116">Ayırıcılar, adının ne gibi bir bölümünü ayırır:</span><span class="sxs-lookup"><span data-stu-id="0a13a-116">Separators do what their name suggests: they separate sections of code.</span></span> <span data-ttu-id="0a13a-117">Visual Basic, ayırıcı karakter iki nokta () ' dır `:` .</span><span class="sxs-lookup"><span data-stu-id="0a13a-117">In Visual Basic, the separator character is the colon (`:`).</span></span> <span data-ttu-id="0a13a-118">Ayrı satırlar yerine tek bir satıra birden çok deyim eklemek istediğinizde ayırıcılar kullanın.</span><span class="sxs-lookup"><span data-stu-id="0a13a-118">Use separators when you want to include multiple statements on a single line instead of separate lines.</span></span> <span data-ttu-id="0a13a-119">Bu, alanı kaydeder ve kodunuzun okunabilirliğini geliştirir.</span><span class="sxs-lookup"><span data-stu-id="0a13a-119">This saves space and improves the readability of your code.</span></span> <span data-ttu-id="0a13a-120">Aşağıdaki örnekte, iki nokta üst üste ile ayrılmış üç deyim gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0a13a-120">The following example shows three statements separated by colons.</span></span>  
  
 [!code-vb[VbVbcnConventions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#12)]  
  
 <span data-ttu-id="0a13a-121">Daha fazla bilgi için bkz. [nasıl yapılır: kod Içinde deyimleri kesme ve birleştirme](how-to-break-and-combine-statements-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="0a13a-121">For more information, see [How to: Break and Combine Statements in Code](how-to-break-and-combine-statements-in-code.md).</span></span>  
  
 <span data-ttu-id="0a13a-122">İki nokta ( `:` ) karakteri de bir ifade etiketini tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0a13a-122">The colon (`:`) character is also used to identify a statement label.</span></span> <span data-ttu-id="0a13a-123">Daha fazla bilgi için bkz. [nasıl yapılır: Label deyimleri](how-to-label-statements.md).</span><span class="sxs-lookup"><span data-stu-id="0a13a-123">For more information, see [How to: Label Statements](how-to-label-statements.md).</span></span>  
  
## <a name="concatenation"></a><span data-ttu-id="0a13a-124">Birleştirme</span><span class="sxs-lookup"><span data-stu-id="0a13a-124">Concatenation</span></span>  

 <span data-ttu-id="0a13a-125">`&` *Birleştirmek* veya dizeleri birbirine bağlamak için işlecini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0a13a-125">Use the `&` operator for *concatenation*, or linking strings together.</span></span> <span data-ttu-id="0a13a-126">`+`Sayısal değerleri bir araya ekleyen işleçle karıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="0a13a-126">Do not confuse it with the `+` operator, which adds together numeric values.</span></span> <span data-ttu-id="0a13a-127">`+`Sayısal değerler üzerinde çalışırken birleştirme için işlecini kullanırsanız, yanlış sonuçlar elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0a13a-127">If you use the `+` operator to concatenate when you operate on numeric values, you can obtain incorrect results.</span></span> <span data-ttu-id="0a13a-128">Aşağıdaki örnek bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0a13a-128">The following example demonstrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#13)]  
  
 <span data-ttu-id="0a13a-129">Önceki kodun yürütülmesi sonrasında, değeri `resultA` 21,01 ve değeri `resultB` "10,0111" olur.</span><span class="sxs-lookup"><span data-stu-id="0a13a-129">Following execution of the previous code, the value of `resultA` is 21.01 and the value of `resultB` is "10.0111".</span></span>  
  
## <a name="member-access-operators"></a><span data-ttu-id="0a13a-130">Üye erişim Işleçleri</span><span class="sxs-lookup"><span data-stu-id="0a13a-130">Member Access Operators</span></span>  

 <span data-ttu-id="0a13a-131">Bir türün üyesine erişmek için, `.` `!` tür adı ve üye adı arasında nokta () veya ünlem işareti () işlecini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="0a13a-131">To access a member of a type, you use the dot (`.`) or exclamation point (`!`) operator between the type name and the member name.</span></span>  
  
### <a name="dot--operator"></a><span data-ttu-id="0a13a-132">Nokta (.) İşlecinde</span><span class="sxs-lookup"><span data-stu-id="0a13a-132">Dot (.) Operator</span></span>  

 <span data-ttu-id="0a13a-133">`.`İşleci bir sınıf, yapı, arabirim veya sabit listesi üzerinde üye erişim işleci olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="0a13a-133">Use the `.` operator on a class, structure, interface, or enumeration as a member access operator.</span></span> <span data-ttu-id="0a13a-134">Üye bir alan, özellik, olay veya yöntem olabilir.</span><span class="sxs-lookup"><span data-stu-id="0a13a-134">The member can be a field, property, event, or method.</span></span> <span data-ttu-id="0a13a-135">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="0a13a-135">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#14)]  
  
### <a name="exclamation-point--operator"></a><span data-ttu-id="0a13a-136">Ünlem işareti (!) İşlecinde</span><span class="sxs-lookup"><span data-stu-id="0a13a-136">Exclamation Point (!) Operator</span></span>  

 <span data-ttu-id="0a13a-137">`!`İşleci yalnızca bir sınıf veya arabirimde sözlük erişim işleci olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="0a13a-137">Use the `!` operator only on a class or interface as a dictionary access operator.</span></span> <span data-ttu-id="0a13a-138">Sınıfın veya arabirimin tek bir bağımsız değişkeni kabul eden bir varsayılan özelliği olmalıdır `String` .</span><span class="sxs-lookup"><span data-stu-id="0a13a-138">The class or interface must have a default property that accepts a single `String` argument.</span></span> <span data-ttu-id="0a13a-139">İşlecinden hemen sonraki tanımlayıcı, `!` varsayılan özelliğe dize olarak geçirilen bağımsız değişken değeri olur.</span><span class="sxs-lookup"><span data-stu-id="0a13a-139">The identifier immediately following the `!` operator becomes the argument value passed to the default property as a string.</span></span> <span data-ttu-id="0a13a-140">Aşağıdaki örnek bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0a13a-140">The following example demonstrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#15)]  
  
 <span data-ttu-id="0a13a-141">Her birinin üç çıkış satırı `MsgBox` değeri görüntüler `32856` .</span><span class="sxs-lookup"><span data-stu-id="0a13a-141">The three output lines of `MsgBox` all display the value `32856`.</span></span> <span data-ttu-id="0a13a-142">İlk satır geleneksel erişim özelliğini kullanır `index` , ikincisi sınıfının varsayılan özelliği olan olguyu kullanır `index` `hasDefault` ve üçüncüsü ise sınıfa sözlük erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="0a13a-142">The first line uses the traditional access to property `index`, the second makes use of the fact that `index` is the default property of class `hasDefault`, and the third uses dictionary access to the class.</span></span>  
  
 <span data-ttu-id="0a13a-143">İşlecin ikinci işleneninin, `!` çift tırnak işaretleri () içine alınmış geçerli bir Visual Basic tanımlayıcı olması gerektiğini unutmayın `" "` .</span><span class="sxs-lookup"><span data-stu-id="0a13a-143">Note that the second operand of the `!` operator must be a valid Visual Basic identifier not enclosed in double quotation marks (`" "`).</span></span> <span data-ttu-id="0a13a-144">Diğer bir deyişle, bir dize sabit değeri veya dize değişkeni kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="0a13a-144">In other words, you cannot use a string literal or string variable.</span></span> <span data-ttu-id="0a13a-145">Çağrının son satırına yapılan aşağıdaki değişiklik `MsgBox` bir hata oluşturur çünkü `"X"` bir kapalı dize sabit değeri.</span><span class="sxs-lookup"><span data-stu-id="0a13a-145">The following change to the last line of the `MsgBox` call generates an error because `"X"` is an enclosed string literal.</span></span>  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
> <span data-ttu-id="0a13a-146">Varsayılan koleksiyonlara yapılan başvurular açık olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0a13a-146">References to default collections must be explicit.</span></span> <span data-ttu-id="0a13a-147">Özellikle, `!` işlecini geç bağlı bir değişkende kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="0a13a-147">In particular, you cannot use the `!` operator on a late-bound variable.</span></span>  
  
 <span data-ttu-id="0a13a-148">`!`Karakter, tür karakteri olarak da kullanılır `Single` .</span><span class="sxs-lookup"><span data-stu-id="0a13a-148">The `!` character is also used as the `Single` type character.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a13a-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a13a-149">See also</span></span>

- [<span data-ttu-id="0a13a-150">Program yapısı ve kod kuralları</span><span class="sxs-lookup"><span data-stu-id="0a13a-150">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
- [<span data-ttu-id="0a13a-151">Tür Karakterleri</span><span class="sxs-lookup"><span data-stu-id="0a13a-151">Type Characters</span></span>](../language-features/data-types/type-characters.md)
