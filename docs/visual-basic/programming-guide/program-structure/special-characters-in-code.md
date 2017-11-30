---
title: "Kod'da Özel Karakterler (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 11c5ef9ad41fc2362d9ba4f2cb5eb5b63a9ca31c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="special-characters-in-code-visual-basic"></a><span data-ttu-id="a0673-102">Kod'da Özel Karakterler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a0673-102">Special Characters in Code (Visual Basic)</span></span>
<span data-ttu-id="a0673-103">Bazen alfabetik veya sayısal olmayan karakterler kodunuzda, diğer bir deyişle, özel karakterler kullanmak zorunda.</span><span class="sxs-lookup"><span data-stu-id="a0673-103">Sometimes you have to use special characters in your code, that is, characters that are not alphabetical or numeric.</span></span> <span data-ttu-id="a0673-104">Noktalama işaretleri ve özel karakterler [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] karakter kümesine sahip derleyici ya derlenmiş program gerçekleştirdiği görevleri tanımlamak için program metin düzenleme gelen çeşitli kullanır.</span><span class="sxs-lookup"><span data-stu-id="a0673-104">The punctuation and special characters in the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] character set have various uses, from organizing program text to defining the tasks that the compiler or the compiled program performs.</span></span> <span data-ttu-id="a0673-105">Bir işlemin gerçekleştirilmesi için belirtmeyin.</span><span class="sxs-lookup"><span data-stu-id="a0673-105">They do not specify an operation to be performed.</span></span>  
  
## <a name="parentheses"></a><span data-ttu-id="a0673-106">Parantez</span><span class="sxs-lookup"><span data-stu-id="a0673-106">Parentheses</span></span>  
 <span data-ttu-id="a0673-107">Bir yordam gibi tanımlarken parantez kullanmak bir `Sub` veya `Function`.</span><span class="sxs-lookup"><span data-stu-id="a0673-107">Use parentheses when you define a procedure, such as a `Sub` or `Function`.</span></span> <span data-ttu-id="a0673-108">Tüm yordam bağımsız değişken listeleri parantez içine almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a0673-108">You must enclose all procedure argument lists in parentheses.</span></span> <span data-ttu-id="a0673-109">Ayrıca parantez mantıksal gruplar halinde koyarak değişkenleri veya bağımsız değişkenler için özellikle karmaşık bir ifadede İşleç önceliği varsayılan sırasını geçersiz kılmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="a0673-109">You also use parentheses for putting variables or arguments into logical groups, especially to override the default order of operator precedence in a complex expression.</span></span> <span data-ttu-id="a0673-110">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="a0673-110">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#11](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_1.vb)]  
  
 <span data-ttu-id="a0673-111">Değerini önceki kod yürütmeyi izleyen `d` 8.225 ve değerini `e` 3'tür.</span><span class="sxs-lookup"><span data-stu-id="a0673-111">Following execution of the previous code, the value of `d` is 8.225 and the value of `e` is 3.</span></span> <span data-ttu-id="a0673-112">Hesaplama için `d` varsayılan önceliği kullanan `/` üzerinden `+` ve eşdeğerdir `d = b + (c / a)`.</span><span class="sxs-lookup"><span data-stu-id="a0673-112">The calculation for `d` uses the default precedence of `/` over `+` and is equivalent to `d = b + (c / a)`.</span></span> <span data-ttu-id="a0673-113">Hesaplama için parantezlerde `e` varsayılan önceliği geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="a0673-113">The parentheses in the calculation for `e` override the default precedence.</span></span>  
  
## <a name="separators"></a><span data-ttu-id="a0673-114">Ayırıcı</span><span class="sxs-lookup"><span data-stu-id="a0673-114">Separators</span></span>  
 <span data-ttu-id="a0673-115">Ayırıcılar yapmak ne adlarının önerir: kodun bölümlerini ayırın.</span><span class="sxs-lookup"><span data-stu-id="a0673-115">Separators do what their name suggests: they separate sections of code.</span></span> <span data-ttu-id="a0673-116">İçinde [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], iki nokta üst üste ayırıcı karakter olan (`:`).</span><span class="sxs-lookup"><span data-stu-id="a0673-116">In [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], the separator character is the colon (`:`).</span></span> <span data-ttu-id="a0673-117">Birden çok deyime ayrı satırlara yerine tek bir satırda dahil etmek istediğiniz zaman ayırıcı kullanın.</span><span class="sxs-lookup"><span data-stu-id="a0673-117">Use separators when you want to include multiple statements on a single line instead of separate lines.</span></span> <span data-ttu-id="a0673-118">Bu alanı kaydeder ve kodunuzun okunabilirliğini artırır.</span><span class="sxs-lookup"><span data-stu-id="a0673-118">This saves space and improves the readability of your code.</span></span> <span data-ttu-id="a0673-119">Aşağıdaki örnekte, üç değerlerini virgüllerle ayrılmış gösterir.</span><span class="sxs-lookup"><span data-stu-id="a0673-119">The following example shows three statements separated by colons.</span></span>  
  
 [!code-vb[VbVbcnConventions#12](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_2.vb)]  
  
 <span data-ttu-id="a0673-120">Daha fazla bilgi için bkz: [nasıl yapılır: Break ve kodda deyimleri birleştirmek](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="a0673-120">For more information, see [How to: Break and Combine Statements in Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span></span>  
  
 <span data-ttu-id="a0673-121">İki nokta üst üste (`:`) karakter deyimi etiket tanımlamak için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a0673-121">The colon (`:`) character is also used to identify a statement label.</span></span> <span data-ttu-id="a0673-122">Daha fazla bilgi için bkz: [nasıl yapılır: Etiket deyimleri](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span><span class="sxs-lookup"><span data-stu-id="a0673-122">For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
## <a name="concatenation"></a><span data-ttu-id="a0673-123">Bitiştirme</span><span class="sxs-lookup"><span data-stu-id="a0673-123">Concatenation</span></span>  
 <span data-ttu-id="a0673-124">Kullanım `&` işleci için *birleştirme*, veya dizeleri birbirine bağlama.</span><span class="sxs-lookup"><span data-stu-id="a0673-124">Use the `&` operator for *concatenation*, or linking strings together.</span></span> <span data-ttu-id="a0673-125">İle karıştırmayın `+` sayısal değerleri toplar işleci.</span><span class="sxs-lookup"><span data-stu-id="a0673-125">Do not confuse it with the `+` operator, which adds together numeric values.</span></span> <span data-ttu-id="a0673-126">Kullanırsanız `+` sayısal değerler üzerinde çalışır, birleştirmek için işleci hatalı sonuçlar elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0673-126">If you use the `+` operator to concatenate when you operate on numeric values, you can obtain incorrect results.</span></span> <span data-ttu-id="a0673-127">Aşağıdaki örnekte bu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a0673-127">The following example demonstrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#13](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_3.vb)]  
  
 <span data-ttu-id="a0673-128">Değerini önceki kod yürütmeyi izleyen `resultA` 21.01 ve değeri `resultB` "10.0111" değil.</span><span class="sxs-lookup"><span data-stu-id="a0673-128">Following execution of the previous code, the value of `resultA` is 21.01 and the value of `resultB` is "10.0111".</span></span>  
  
## <a name="member-access-operators"></a><span data-ttu-id="a0673-129">Üye erişimi işleçleri</span><span class="sxs-lookup"><span data-stu-id="a0673-129">Member Access Operators</span></span>  
 <span data-ttu-id="a0673-130">Bir tür üyesi erişmek için nokta kullanın (`.`) veya ünlem işareti (`!`) arasında tür ve üye adı işleci.</span><span class="sxs-lookup"><span data-stu-id="a0673-130">To access a member of a type, you use the dot (`.`) or exclamation point (`!`) operator between the type name and the member name.</span></span>  
  
### <a name="dot--operator"></a><span data-ttu-id="a0673-131">Nokta (.) İşleç</span><span class="sxs-lookup"><span data-stu-id="a0673-131">Dot (.) Operator</span></span>  
 <span data-ttu-id="a0673-132">Kullanım `.` sınıfı, yapısı, arabirim veya numaralandırma operatör olarak bir üye erişimi işleci.</span><span class="sxs-lookup"><span data-stu-id="a0673-132">Use the `.` operator on a class, structure, interface, or enumeration as a member access operator.</span></span> <span data-ttu-id="a0673-133">Üye alan, özellik, olay veya yöntem olabilir.</span><span class="sxs-lookup"><span data-stu-id="a0673-133">The member can be a field, property, event, or method.</span></span> <span data-ttu-id="a0673-134">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="a0673-134">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#14](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_4.vb)]  
  
### <a name="exclamation-point--operator"></a><span data-ttu-id="a0673-135">Ünlem işareti (!) İşleç</span><span class="sxs-lookup"><span data-stu-id="a0673-135">Exclamation Point (!) Operator</span></span>  
 <span data-ttu-id="a0673-136">Kullanım `!` işlecinin yalnızca bir sınıfta veya arabirimde bir sözlük erişim işleci olarak.</span><span class="sxs-lookup"><span data-stu-id="a0673-136">Use the `!` operator only on a class or interface as a dictionary access operator.</span></span> <span data-ttu-id="a0673-137">Sınıf veya arabirim tek bir kabul eder ve varsayılan bir özellik olmalıdır `String` bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="a0673-137">The class or interface must have a default property that accepts a single `String` argument.</span></span> <span data-ttu-id="a0673-138">Hemen ardından tanımlayıcı `!` işleci bir dize olarak varsayılan özelliği için geçirilen bağımsız değişken değeri olur.</span><span class="sxs-lookup"><span data-stu-id="a0673-138">The identifier immediately following the `!` operator becomes the argument value passed to the default property as a string.</span></span> <span data-ttu-id="a0673-139">Aşağıdaki örnekte bu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a0673-139">The following example demonstrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#15](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_5.vb)]  
  
 <span data-ttu-id="a0673-140">Üç satırlık çıktı `MsgBox` tüm değerini görüntülemek `32856`.</span><span class="sxs-lookup"><span data-stu-id="a0673-140">The three output lines of `MsgBox` all display the value `32856`.</span></span> <span data-ttu-id="a0673-141">Geleneksel erişim özelliğine ilk satırını kullanır `index`, ikinci kullanır olgu, `index` varsayılan sınıfın özelliğidir `hasDefault`, ve üçüncü sözlük erişim sınıfına kullanır.</span><span class="sxs-lookup"><span data-stu-id="a0673-141">The first line uses the traditional access to property `index`, the second makes use of the fact that `index` is the default property of class `hasDefault`, and the third uses dictionary access to the class.</span></span>  
  
 <span data-ttu-id="a0673-142">Unutmayın, ikinci işlenen `!` işleci, çift tırnak işaretleri içine alınmamış geçerli bir Visual Basic tanımlayıcı olmalıdır (`" "`).</span><span class="sxs-lookup"><span data-stu-id="a0673-142">Note that the second operand of the `!` operator must be a valid Visual Basic identifier not enclosed in double quotation marks (`" "`).</span></span> <span data-ttu-id="a0673-143">Diğer bir deyişle, bir değişmez dize veya dize değişkeni kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="a0673-143">In other words, you cannot use a string literal or string variable.</span></span> <span data-ttu-id="a0673-144">Şu son satırının değiştirin `MsgBox` çağrısı bir hata nedeniyle oluşturur `"X"` kapalı bir dize değişmez değer olduğunu.</span><span class="sxs-lookup"><span data-stu-id="a0673-144">The following change to the last line of the `MsgBox` call generates an error because `"X"` is an enclosed string literal.</span></span>  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
>  <span data-ttu-id="a0673-145">Varsayılan koleksiyon başvurularını açık olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a0673-145">References to default collections must be explicit.</span></span> <span data-ttu-id="a0673-146">Özellikle, kullanamazsınız `!` geç bağlama değişken işleci.</span><span class="sxs-lookup"><span data-stu-id="a0673-146">In particular, you cannot use the `!` operator on a late-bound variable.</span></span>  
  
 <span data-ttu-id="a0673-147">`!` Karakter olarak da kullanılır `Single` karakteri yazın.</span><span class="sxs-lookup"><span data-stu-id="a0673-147">The `!` character is also used as the `Single` type character.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0673-148">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a0673-148">See Also</span></span>  
 [<span data-ttu-id="a0673-149">Program yapısı ve kod kuralları</span><span class="sxs-lookup"><span data-stu-id="a0673-149">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [<span data-ttu-id="a0673-150">Tür karakterleri</span><span class="sxs-lookup"><span data-stu-id="a0673-150">Type Characters</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
