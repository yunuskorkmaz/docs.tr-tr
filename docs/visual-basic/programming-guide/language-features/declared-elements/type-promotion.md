---
title: Tür Yükseltme
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- Partial keyword [Visual Basic], unexpected results with type promotion
- scope [Visual Basic], declared elements
- scope [Visual Basic], Visual Basic
- type promotion
- declared elements [Visual Basic], visibility
ms.assetid: 035eeb15-e4c5-4288-ab3c-6bd5d22f7051
ms.openlocfilehash: aa05bd7dc87510aedb0facadf4b7590c8ec57d1f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345270"
---
# <a name="type-promotion-visual-basic"></a><span data-ttu-id="16b74-102">Tür Yükseltme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="16b74-102">Type Promotion (Visual Basic)</span></span>
<span data-ttu-id="16b74-103">Bir modülde programlama öğesi bildirdiğinizde Visual Basic kapsamını modülünü içeren ad alanına yükseltir.</span><span class="sxs-lookup"><span data-stu-id="16b74-103">When you declare a programming element in a module, Visual Basic promotes its scope to the namespace containing the module.</span></span> <span data-ttu-id="16b74-104">Bu, *tür yükseltmesi*olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="16b74-104">This is known as *type promotion*.</span></span>  
  
 <span data-ttu-id="16b74-105">Aşağıdaki örnek, bir modülün iskelet tanımını ve bu modülün iki üyesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="16b74-105">The following example shows a skeleton definition of a module and two members of that module.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#1)]  
  
 <span data-ttu-id="16b74-106">`projModule`içinde, modül düzeyinde belirtilen programlama öğeleri `projNamespace`yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="16b74-106">Within `projModule`, programming elements declared at module level are promoted to `projNamespace`.</span></span> <span data-ttu-id="16b74-107">Yukarıdaki örnekte `basicEnum` ve `innerClass` yükseltilir, ancak modül düzeyinde bildirilmemiş olduğundan `numberSub` değildir.</span><span class="sxs-lookup"><span data-stu-id="16b74-107">In the preceding example, `basicEnum` and `innerClass` are promoted, but `numberSub` is not, because it is not declared at module level.</span></span>  
  
## <a name="effect-of-type-promotion"></a><span data-ttu-id="16b74-108">Yükseltme türü etkisi</span><span class="sxs-lookup"><span data-stu-id="16b74-108">Effect of Type Promotion</span></span>  
 <span data-ttu-id="16b74-109">Yükseltme türünün etkisi, bir nitelik dizesinin modül adını içermesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="16b74-109">The effect of type promotion is that a qualification string does not need to include the module name.</span></span> <span data-ttu-id="16b74-110">Aşağıdaki örnek, önceki örnekteki yordama iki çağrı yapar.</span><span class="sxs-lookup"><span data-stu-id="16b74-110">The following example makes two calls to the procedure in the preceding example.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#2)]  
  
 <span data-ttu-id="16b74-111">Yukarıdaki örnekte, ilk çağrı bütün nitelik dizelerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="16b74-111">In the preceding example, the first call uses complete qualification strings.</span></span> <span data-ttu-id="16b74-112">Ancak, tür yükseltmesi nedeniyle bu gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="16b74-112">However, this is not necessary because of type promotion.</span></span> <span data-ttu-id="16b74-113">İkinci çağrı Ayrıca, nitelik dizelerine `projModule` dahil etmeden modülün üyelerine erişir.</span><span class="sxs-lookup"><span data-stu-id="16b74-113">The second call also accesses the module's members without including `projModule` in the qualification strings.</span></span>  
  
## <a name="defeat-of-type-promotion"></a><span data-ttu-id="16b74-114">Tür promosyonu</span><span class="sxs-lookup"><span data-stu-id="16b74-114">Defeat of Type Promotion</span></span>  
 <span data-ttu-id="16b74-115">Ad alanı zaten bir modül üyesiyle aynı ada sahip bir üyeye sahipse, bu modül üyesi için yükseltme yapılır yazın.</span><span class="sxs-lookup"><span data-stu-id="16b74-115">If the namespace already has a member with the same name as a module member, type promotion is defeated for that module member.</span></span> <span data-ttu-id="16b74-116">Aşağıdaki örnek, bir numaralandırma ve aynı ad uzayı içindeki bir modülün iskelet tanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="16b74-116">The following example shows a skeleton definition of an enumeration and a module within the same namespace.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#3)]  
  
 <span data-ttu-id="16b74-117">Yukarıdaki örnekte, ad alanı düzeyinde aynı ada sahip bir sabit listesi olduğundan Visual Basic sınıf `abc` `thisNameSpace` olarak yükseltememesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="16b74-117">In the preceding example, Visual Basic cannot promote class `abc` to `thisNameSpace` because there is already an enumeration with the same name at namespace level.</span></span> <span data-ttu-id="16b74-118">`abcSub`erişmek için, tam niteleme dizesi `thisNamespace.thisModule.abc.abcSub`kullanmalısınız.</span><span class="sxs-lookup"><span data-stu-id="16b74-118">To access `abcSub`, you must use the full qualification string `thisNamespace.thisModule.abc.abcSub`.</span></span> <span data-ttu-id="16b74-119">Ancak, sınıf `xyz` hala yükseltilir ve `xyzSub` daha kısa niteleme dizesiyle `thisNamespace.xyz.xyzSub`erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16b74-119">However, class `xyz` is still promoted, and you can access `xyzSub` with the shorter qualification string `thisNamespace.xyz.xyzSub`.</span></span>  
  
### <a name="defeat-of-type-promotion-for-partial-types"></a><span data-ttu-id="16b74-120">Kısmi türler için tür promosyonu</span><span class="sxs-lookup"><span data-stu-id="16b74-120">Defeat of Type Promotion for Partial Types</span></span>  
 <span data-ttu-id="16b74-121">Modül içindeki bir sınıf veya yapı [kısmi](../../../../visual-basic/language-reference/modifiers/partial.md) anahtar sözcüğünü kullanıyorsa, ad alanının aynı ada sahip bir üyeye sahip olup olmadığına bakılmaksızın, bu sınıf veya yapı için otomatik olarak tür yükseltmesi yapılır.</span><span class="sxs-lookup"><span data-stu-id="16b74-121">If a class or structure inside a module uses the [Partial](../../../../visual-basic/language-reference/modifiers/partial.md) keyword, type promotion is automatically defeated for that class or structure, whether or not the namespace has a member with the same name.</span></span> <span data-ttu-id="16b74-122">Modüldeki diğer öğeler de tür yükseltme için uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="16b74-122">Other elements in the module are still eligible for type promotion.</span></span>  
  
 <span data-ttu-id="16b74-123">**Larının.**</span><span class="sxs-lookup"><span data-stu-id="16b74-123">**Consequences.**</span></span> <span data-ttu-id="16b74-124">Kısmi bir tanımın tür promosyonu, beklenmedik sonuçlara ve hatta derleyici hatalarına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="16b74-124">Defeat of type promotion of a partial definition can cause unexpected results and even compiler errors.</span></span> <span data-ttu-id="16b74-125">Aşağıdaki örnek, bir sınıfının bir modül içinde olan bir sınıfın iskelet kısmi tanımlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="16b74-125">The following example shows skeleton partial definitions of a class, one of which is inside a module.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#4)]  
  
 <span data-ttu-id="16b74-126">Yukarıdaki örnekte, geliştirici derleyicinin iki kısmi tanımını `sampleClass`birleştirme işlemini bekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="16b74-126">In the preceding example, the developer might expect the compiler to merge the two partial definitions of `sampleClass`.</span></span> <span data-ttu-id="16b74-127">Ancak, derleyici `sampleModule`içindeki kısmi Tanım için yükseltmeyi göz önünde bulundurmaz.</span><span class="sxs-lookup"><span data-stu-id="16b74-127">However, the compiler does not consider promotion for the partial definition inside `sampleModule`.</span></span> <span data-ttu-id="16b74-128">Sonuç olarak, hem `sampleClass` hem de farklı nitelik yollarıyla iki ayrı ve farklı sınıf derlemeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="16b74-128">As a result, it attempts to compile two separate and distinct classes, both named `sampleClass` but with different qualification paths.</span></span>  
  
 <span data-ttu-id="16b74-129">Derleyici, kısmi tanımları yalnızca kendi tam yolları özdeş olduğunda birleştirir.</span><span class="sxs-lookup"><span data-stu-id="16b74-129">The compiler merges partial definitions only when their fully qualified paths are identical.</span></span>  
  
## <a name="recommendations"></a><span data-ttu-id="16b74-130">Öneriler</span><span class="sxs-lookup"><span data-stu-id="16b74-130">Recommendations</span></span>  
 <span data-ttu-id="16b74-131">Aşağıdaki öneriler iyi programlama uygulamasını temsil etmektedir.</span><span class="sxs-lookup"><span data-stu-id="16b74-131">The following recommendations represent good programming practice.</span></span>  
  
- <span data-ttu-id="16b74-132">**Benzersiz adlar.**</span><span class="sxs-lookup"><span data-stu-id="16b74-132">**Unique Names.**</span></span> <span data-ttu-id="16b74-133">Programlama öğelerinin adlandırılması üzerinde tam denetime sahip olduğunuzda her yerde benzersiz adların kullanılması her zaman iyi bir fikirdir.</span><span class="sxs-lookup"><span data-stu-id="16b74-133">When you have full control over the naming of programming elements, it is always a good idea to use unique names everywhere.</span></span> <span data-ttu-id="16b74-134">Aynı adlar ek nitelik gerektirir ve kodunuzun okunmasını daha zor hale getirir.</span><span class="sxs-lookup"><span data-stu-id="16b74-134">Identical names require extra qualification and can make your code harder to read.</span></span> <span data-ttu-id="16b74-135">Ayrıca, hafif hatalara ve beklenmedik sonuçlara yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="16b74-135">They can also lead to subtle errors and unexpected results.</span></span>  
  
- <span data-ttu-id="16b74-136">**Tam nitelik.**</span><span class="sxs-lookup"><span data-stu-id="16b74-136">**Full Qualification.**</span></span> <span data-ttu-id="16b74-137">Aynı ad alanındaki modüller ve diğer öğelerle çalışırken, en güvenli yaklaşım tüm programlama öğeleri için her zaman tam niteliğin kullanılması.</span><span class="sxs-lookup"><span data-stu-id="16b74-137">When you are working with modules and other elements in the same namespace, the safest approach is to always use full qualification for all programming elements.</span></span> <span data-ttu-id="16b74-138">Tür promosyonu bir modül üyesi için ertelendirilürse ve bu üyeyi tamamen nitelemeniz durumunda farklı bir programlama öğesine yanlışlıkla erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16b74-138">If type promotion is defeated for a module member and you do not fully qualify that member, you could inadvertently access a different programming element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16b74-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16b74-139">See also</span></span>

- [<span data-ttu-id="16b74-140">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="16b74-140">Module Statement</span></span>](../../../../visual-basic/language-reference/statements/module-statement.md)
- [<span data-ttu-id="16b74-141">Namespace Deyimi</span><span class="sxs-lookup"><span data-stu-id="16b74-141">Namespace Statement</span></span>](../../../../visual-basic/language-reference/statements/namespace-statement.md)
- [<span data-ttu-id="16b74-142">Partial</span><span class="sxs-lookup"><span data-stu-id="16b74-142">Partial</span></span>](../../../../visual-basic/language-reference/modifiers/partial.md)
- [<span data-ttu-id="16b74-143">Visual Basic kapsam</span><span class="sxs-lookup"><span data-stu-id="16b74-143">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [<span data-ttu-id="16b74-144">Nasıl yapılır: Bir Değişkenin Kapsamını Denetleme</span><span class="sxs-lookup"><span data-stu-id="16b74-144">How to: Control the Scope of a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)
- [<span data-ttu-id="16b74-145">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="16b74-145">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
