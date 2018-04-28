---
title: Tür Yükseltme (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- Partial keyword [Visual Basic], unexpected results with type promotion
- scope [Visual Basic], declared elements
- scope [Visual Basic], Visual Basic
- type promotion
- declared elements [Visual Basic], visibility
ms.assetid: 035eeb15-e4c5-4288-ab3c-6bd5d22f7051
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ddb0d61f0f1c94e8e28493d0c62afe1e09503804
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="type-promotion-visual-basic"></a><span data-ttu-id="2dad6-102">Tür Yükseltme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2dad6-102">Type Promotion (Visual Basic)</span></span>
<span data-ttu-id="2dad6-103">Bir modüldeki bir programlama öğesi bildirirken Visual Basic kapsamı modülü içeren ad alanına yükseltir.</span><span class="sxs-lookup"><span data-stu-id="2dad6-103">When you declare a programming element in a module, Visual Basic promotes its scope to the namespace containing the module.</span></span> <span data-ttu-id="2dad6-104">Bu olarak bilinir *yazın yükseltme*.</span><span class="sxs-lookup"><span data-stu-id="2dad6-104">This is known as *type promotion*.</span></span>  
  
 <span data-ttu-id="2dad6-105">Aşağıdaki örnek, bir modül iskelet tanımının ve bu modül iki üyeleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="2dad6-105">The following example shows a skeleton definition of a module and two members of that module.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#1](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_1.vb)]  
  
 <span data-ttu-id="2dad6-106">İçinde `projModule`, programlama Modül düzeyinde bildirilen öğeler için yükseltilen `projNamespace`.</span><span class="sxs-lookup"><span data-stu-id="2dad6-106">Within `projModule`, programming elements declared at module level are promoted to `projNamespace`.</span></span> <span data-ttu-id="2dad6-107">Önceki örnekte, `basicEnum` ve `innerClass` öne, ancak `numberSub` Modül düzeyinde bildirilmediğinden değildir.</span><span class="sxs-lookup"><span data-stu-id="2dad6-107">In the preceding example, `basicEnum` and `innerClass` are promoted, but `numberSub` is not, because it is not declared at module level.</span></span>  
  
## <a name="effect-of-type-promotion"></a><span data-ttu-id="2dad6-108">Tür promosyonu etkisi</span><span class="sxs-lookup"><span data-stu-id="2dad6-108">Effect of Type Promotion</span></span>  
 <span data-ttu-id="2dad6-109">Tür promosyonu etkisini niteliğe dize modül adını içermesi gerekmez ' dir.</span><span class="sxs-lookup"><span data-stu-id="2dad6-109">The effect of type promotion is that a qualification string does not need to include the module name.</span></span> <span data-ttu-id="2dad6-110">Aşağıdaki örnekte iki yordam önceki örnekte çağrılar.</span><span class="sxs-lookup"><span data-stu-id="2dad6-110">The following example makes two calls to the procedure in the preceding example.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#2](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_2.vb)]  
  
 <span data-ttu-id="2dad6-111">Önceki örnekte, ilk çağrıda tam nitelenmiş dizelerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2dad6-111">In the preceding example, the first call uses complete qualification strings.</span></span> <span data-ttu-id="2dad6-112">Ancak, bu tür yükseltme nedeniyle gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="2dad6-112">However, this is not necessary because of type promotion.</span></span> <span data-ttu-id="2dad6-113">İkinci çağrı da erişir modülün üyeleri dahil etmeden `projModule` niteliğe dizelerde.</span><span class="sxs-lookup"><span data-stu-id="2dad6-113">The second call also accesses the module's members without including `projModule` in the qualification strings.</span></span>  
  
## <a name="defeat-of-type-promotion"></a><span data-ttu-id="2dad6-114">Tür promosyonu zorluğunu</span><span class="sxs-lookup"><span data-stu-id="2dad6-114">Defeat of Type Promotion</span></span>  
 <span data-ttu-id="2dad6-115">Tür promosyonu ad alanı aynı ada sahip bir üye modülü üyesi olarak zaten varsa, bu modülü üyenin engellenmediğinden.</span><span class="sxs-lookup"><span data-stu-id="2dad6-115">If the namespace already has a member with the same name as a module member, type promotion is defeated for that module member.</span></span> <span data-ttu-id="2dad6-116">Aşağıdaki örnek, bir numaralandırma ve aynı ad alanı içindeki bir modül iskelet tanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2dad6-116">The following example shows a skeleton definition of an enumeration and a module within the same namespace.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#3](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_3.vb)]  
  
 <span data-ttu-id="2dad6-117">Önceki örnekte, Visual Basic sınıfı yükseltemezsiniz `abc` için `thisNameSpace` zaten bir numaralandırma ad alanı düzeyinde aynı ada sahip olduğundan.</span><span class="sxs-lookup"><span data-stu-id="2dad6-117">In the preceding example, Visual Basic cannot promote class `abc` to `thisNameSpace` because there is already an enumeration with the same name at namespace level.</span></span> <span data-ttu-id="2dad6-118">Erişim için `abcSub`, tam nitelenmiş dize kullanmalısınız `thisNamespace.thisModule.abc.abcSub`.</span><span class="sxs-lookup"><span data-stu-id="2dad6-118">To access `abcSub`, you must use the full qualification string `thisNamespace.thisModule.abc.abcSub`.</span></span> <span data-ttu-id="2dad6-119">Ancak, sınıf `xyz` hala yükseltilir ve dosyaya erişebildiğinizi `xyzSub` kısa niteliğe dizesiyle `thisNamespace.xyz.xyzSub`.</span><span class="sxs-lookup"><span data-stu-id="2dad6-119">However, class `xyz` is still promoted, and you can access `xyzSub` with the shorter qualification string `thisNamespace.xyz.xyzSub`.</span></span>  
  
### <a name="defeat-of-type-promotion-for-partial-types"></a><span data-ttu-id="2dad6-120">Tür promosyonu kısmi türler için zorluğunu</span><span class="sxs-lookup"><span data-stu-id="2dad6-120">Defeat of Type Promotion for Partial Types</span></span>  
 <span data-ttu-id="2dad6-121">Bir sınıf veya yapı bir modül içinde kullanıyorsa [kısmi](../../../../visual-basic/language-reference/modifiers/partial.md) anahtar sözcüğü, tür yükseltme Bu sınıf veya yapı, için otomatik olarak engellenmediğinden aynı ada sahip bir üye ad alanına sahip olup olmadığına bakılmaksızın.</span><span class="sxs-lookup"><span data-stu-id="2dad6-121">If a class or structure inside a module uses the [Partial](../../../../visual-basic/language-reference/modifiers/partial.md) keyword, type promotion is automatically defeated for that class or structure, whether or not the namespace has a member with the same name.</span></span> <span data-ttu-id="2dad6-122">Modülü diğer öğeleri için tür yükseltme hala uygundur.</span><span class="sxs-lookup"><span data-stu-id="2dad6-122">Other elements in the module are still eligible for type promotion.</span></span>  
  
 <span data-ttu-id="2dad6-123">**Sonuçları.**</span><span class="sxs-lookup"><span data-stu-id="2dad6-123">**Consequences.**</span></span> <span data-ttu-id="2dad6-124">Tür promosyonu kısmi tanımının zorluğunu beklenmeyen sonuçlara ve hatta derleyici hataları neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="2dad6-124">Defeat of type promotion of a partial definition can cause unexpected results and even compiler errors.</span></span> <span data-ttu-id="2dad6-125">Aşağıdaki örnekte, biri olan bir modül içinde bir sınıfın iskelet kısmi tanımlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2dad6-125">The following example shows skeleton partial definitions of a class, one of which is inside a module.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#4](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_4.vb)]  
  
 <span data-ttu-id="2dad6-126">Önceki örnekte, iki kısmi tanımlarını birleştirmek için derleyici Geliştirici bekleyebilirsiniz `sampleClass`.</span><span class="sxs-lookup"><span data-stu-id="2dad6-126">In the preceding example, the developer might expect the compiler to merge the two partial definitions of `sampleClass`.</span></span> <span data-ttu-id="2dad6-127">Ancak, derleyici kısmi tanımının içinde yükseltme dikkate almaz `sampleModule`.</span><span class="sxs-lookup"><span data-stu-id="2dad6-127">However, the compiler does not consider promotion for the partial definition inside `sampleModule`.</span></span> <span data-ttu-id="2dad6-128">Sonuç olarak, iki farklı ve ayrıdır sınıf derlemeye çalışır, her ikisi de adlı `sampleClass` ancak farklı nitelik yolları.</span><span class="sxs-lookup"><span data-stu-id="2dad6-128">As a result, it attempts to compile two separate and distinct classes, both named `sampleClass` but with different qualification paths.</span></span>  
  
 <span data-ttu-id="2dad6-129">Yalnızca tam yollarına aynı zaman derleyici kısmi tanımları birleştirir.</span><span class="sxs-lookup"><span data-stu-id="2dad6-129">The compiler merges partial definitions only when their fully qualified paths are identical.</span></span>  
  
## <a name="recommendations"></a><span data-ttu-id="2dad6-130">Önerileri</span><span class="sxs-lookup"><span data-stu-id="2dad6-130">Recommendations</span></span>  
 <span data-ttu-id="2dad6-131">Aşağıdaki öneriler iyi bir programlama uygulama temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2dad6-131">The following recommendations represent good programming practice.</span></span>  
  
-   <span data-ttu-id="2dad6-132">**Benzersiz adlar.**</span><span class="sxs-lookup"><span data-stu-id="2dad6-132">**Unique Names.**</span></span> <span data-ttu-id="2dad6-133">Programlama öğelerine adlandırma üzerinde tam denetime sahip olduğunuzda, her zaman benzersiz adlar her yerde kullanmak iyi bir fikir değil.</span><span class="sxs-lookup"><span data-stu-id="2dad6-133">When you have full control over the naming of programming elements, it is always a good idea to use unique names everywhere.</span></span> <span data-ttu-id="2dad6-134">Aynı ek niteliğe gerektirir ve kodunuzu okumak daha zor hale getirebilir.</span><span class="sxs-lookup"><span data-stu-id="2dad6-134">Identical names require extra qualification and can make your code harder to read.</span></span> <span data-ttu-id="2dad6-135">Bunlar ayrıca Zarif hataları ve beklenmeyen sonuçlara yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="2dad6-135">They can also lead to subtle errors and unexpected results.</span></span>  
  
-   <span data-ttu-id="2dad6-136">**Tam nitelenmiş.**</span><span class="sxs-lookup"><span data-stu-id="2dad6-136">**Full Qualification.**</span></span> <span data-ttu-id="2dad6-137">Modüller ve diğer öğeleri aynı ad ile çalışırken, güvenli bir yaklaşım her zaman tam nitelenmiş için tüm programlama öğeleri kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="2dad6-137">When you are working with modules and other elements in the same namespace, the safest approach is to always use full qualification for all programming elements.</span></span> <span data-ttu-id="2dad6-138">Tür promosyonu modülü üyesi için engellenmediğinden ise ve tam olarak bu üyede uygun değil, farklı bir programlama öğesi yanlışlıkla erişebilir.</span><span class="sxs-lookup"><span data-stu-id="2dad6-138">If type promotion is defeated for a module member and you do not fully qualify that member, you could inadvertently access a different programming element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dad6-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2dad6-139">See Also</span></span>  
 [<span data-ttu-id="2dad6-140">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="2dad6-140">Module Statement</span></span>](../../../../visual-basic/language-reference/statements/module-statement.md)  
 [<span data-ttu-id="2dad6-141">Namespace Deyimi</span><span class="sxs-lookup"><span data-stu-id="2dad6-141">Namespace Statement</span></span>](../../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [<span data-ttu-id="2dad6-142">Partial</span><span class="sxs-lookup"><span data-stu-id="2dad6-142">Partial</span></span>](../../../../visual-basic/language-reference/modifiers/partial.md)  
 [<span data-ttu-id="2dad6-143">Visual Basic'de kapsam</span><span class="sxs-lookup"><span data-stu-id="2dad6-143">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [<span data-ttu-id="2dad6-144">Nasıl yapılır: Bir Değişkenin Kapsamını Denetleme</span><span class="sxs-lookup"><span data-stu-id="2dad6-144">How to: Control the Scope of a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)  
 [<span data-ttu-id="2dad6-145">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="2dad6-145">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
