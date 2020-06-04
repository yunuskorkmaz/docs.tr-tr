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
ms.openlocfilehash: 1e284b99a36cdf0f62aee2c45fd9f3bf544d1d81
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410714"
---
# <a name="type-promotion-visual-basic"></a><span data-ttu-id="471a7-102">Tür Yükseltme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="471a7-102">Type Promotion (Visual Basic)</span></span>
<span data-ttu-id="471a7-103">Bir modülde programlama öğesi bildirdiğinizde Visual Basic kapsamını modülünü içeren ad alanına yükseltir.</span><span class="sxs-lookup"><span data-stu-id="471a7-103">When you declare a programming element in a module, Visual Basic promotes its scope to the namespace containing the module.</span></span> <span data-ttu-id="471a7-104">Bu, *tür yükseltmesi*olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="471a7-104">This is known as *type promotion*.</span></span>  
  
 <span data-ttu-id="471a7-105">Aşağıdaki örnek, bir modülün iskelet tanımını ve bu modülün iki üyesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="471a7-105">The following example shows a skeleton definition of a module and two members of that module.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#1)]  
  
 <span data-ttu-id="471a7-106">İçinde `projModule` , modül düzeyinde belirtilen programlama öğeleri ' e yükseltilir `projNamespace` .</span><span class="sxs-lookup"><span data-stu-id="471a7-106">Within `projModule`, programming elements declared at module level are promoted to `projNamespace`.</span></span> <span data-ttu-id="471a7-107">Önceki örnekte `basicEnum` ve `innerClass` yükseltilmekte, ancak `numberSub` modül düzeyinde bildirilmemiş olduğundan, değildir.</span><span class="sxs-lookup"><span data-stu-id="471a7-107">In the preceding example, `basicEnum` and `innerClass` are promoted, but `numberSub` is not, because it is not declared at module level.</span></span>  
  
## <a name="effect-of-type-promotion"></a><span data-ttu-id="471a7-108">Yükseltme türü etkisi</span><span class="sxs-lookup"><span data-stu-id="471a7-108">Effect of Type Promotion</span></span>  
 <span data-ttu-id="471a7-109">Yükseltme türünün etkisi, bir nitelik dizesinin modül adını içermesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="471a7-109">The effect of type promotion is that a qualification string does not need to include the module name.</span></span> <span data-ttu-id="471a7-110">Aşağıdaki örnek, önceki örnekteki yordama iki çağrı yapar.</span><span class="sxs-lookup"><span data-stu-id="471a7-110">The following example makes two calls to the procedure in the preceding example.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#2)]  
  
 <span data-ttu-id="471a7-111">Yukarıdaki örnekte, ilk çağrı bütün nitelik dizelerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="471a7-111">In the preceding example, the first call uses complete qualification strings.</span></span> <span data-ttu-id="471a7-112">Ancak, tür yükseltmesi nedeniyle bu gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="471a7-112">However, this is not necessary because of type promotion.</span></span> <span data-ttu-id="471a7-113">İkinci çağrı Ayrıca, nitelik dizelerine dahil etmeden modülün üyelerine erişir `projModule` .</span><span class="sxs-lookup"><span data-stu-id="471a7-113">The second call also accesses the module's members without including `projModule` in the qualification strings.</span></span>  
  
## <a name="defeat-of-type-promotion"></a><span data-ttu-id="471a7-114">Tür promosyonu</span><span class="sxs-lookup"><span data-stu-id="471a7-114">Defeat of Type Promotion</span></span>  
 <span data-ttu-id="471a7-115">Ad alanı zaten bir modül üyesiyle aynı ada sahip bir üyeye sahipse, bu modül üyesi için yükseltme yapılır yazın.</span><span class="sxs-lookup"><span data-stu-id="471a7-115">If the namespace already has a member with the same name as a module member, type promotion is defeated for that module member.</span></span> <span data-ttu-id="471a7-116">Aşağıdaki örnek, bir numaralandırma ve aynı ad uzayı içindeki bir modülün iskelet tanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="471a7-116">The following example shows a skeleton definition of an enumeration and a module within the same namespace.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#3)]  
  
 <span data-ttu-id="471a7-117">Yukarıdaki örnekte, `abc` `thisNameSpace` ad alanı düzeyinde aynı ada sahip bir sabit listesi olduğundan, Visual Basic sınıfını öğesine yükseltemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="471a7-117">In the preceding example, Visual Basic cannot promote class `abc` to `thisNameSpace` because there is already an enumeration with the same name at namespace level.</span></span> <span data-ttu-id="471a7-118">Erişmek için `abcSub` tam niteleme dizesini kullanmanız gerekir `thisNamespace.thisModule.abc.abcSub` .</span><span class="sxs-lookup"><span data-stu-id="471a7-118">To access `abcSub`, you must use the full qualification string `thisNamespace.thisModule.abc.abcSub`.</span></span> <span data-ttu-id="471a7-119">Ancak, sınıf `xyz` hala yükseltilir ve `xyzSub` daha kısa nitelik dizesiyle erişebilirsiniz `thisNamespace.xyz.xyzSub` .</span><span class="sxs-lookup"><span data-stu-id="471a7-119">However, class `xyz` is still promoted, and you can access `xyzSub` with the shorter qualification string `thisNamespace.xyz.xyzSub`.</span></span>  
  
### <a name="defeat-of-type-promotion-for-partial-types"></a><span data-ttu-id="471a7-120">Kısmi türler için tür promosyonu</span><span class="sxs-lookup"><span data-stu-id="471a7-120">Defeat of Type Promotion for Partial Types</span></span>  
 <span data-ttu-id="471a7-121">Modül içindeki bir sınıf veya yapı [kısmi](../../../language-reference/modifiers/partial.md) anahtar sözcüğünü kullanıyorsa, ad alanının aynı ada sahip bir üyeye sahip olup olmadığına bakılmaksızın, bu sınıf veya yapı için otomatik olarak tür yükseltmesi yapılır.</span><span class="sxs-lookup"><span data-stu-id="471a7-121">If a class or structure inside a module uses the [Partial](../../../language-reference/modifiers/partial.md) keyword, type promotion is automatically defeated for that class or structure, whether or not the namespace has a member with the same name.</span></span> <span data-ttu-id="471a7-122">Modüldeki diğer öğeler de tür yükseltme için uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="471a7-122">Other elements in the module are still eligible for type promotion.</span></span>  
  
 <span data-ttu-id="471a7-123">**Larının.**</span><span class="sxs-lookup"><span data-stu-id="471a7-123">**Consequences.**</span></span> <span data-ttu-id="471a7-124">Kısmi bir tanımın tür promosyonu, beklenmedik sonuçlara ve hatta derleyici hatalarına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="471a7-124">Defeat of type promotion of a partial definition can cause unexpected results and even compiler errors.</span></span> <span data-ttu-id="471a7-125">Aşağıdaki örnek, bir sınıfının bir modül içinde olan bir sınıfın iskelet kısmi tanımlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="471a7-125">The following example shows skeleton partial definitions of a class, one of which is inside a module.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#4)]  
  
 <span data-ttu-id="471a7-126">Yukarıdaki örnekte, geliştirici derleyicinin iki kısmi tanımını birleştirme işlemini bekleyebilir `sampleClass` .</span><span class="sxs-lookup"><span data-stu-id="471a7-126">In the preceding example, the developer might expect the compiler to merge the two partial definitions of `sampleClass`.</span></span> <span data-ttu-id="471a7-127">Ancak derleyici, içindeki kısmi Tanım için yükseltmeyi göz önünde bulundurmaz `sampleModule` .</span><span class="sxs-lookup"><span data-stu-id="471a7-127">However, the compiler does not consider promotion for the partial definition inside `sampleModule`.</span></span> <span data-ttu-id="471a7-128">Sonuç olarak, hem adında hem de `sampleClass` farklı nitelik yollarıyla birlikte iki ayrı ve farklı sınıf derlemeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="471a7-128">As a result, it attempts to compile two separate and distinct classes, both named `sampleClass` but with different qualification paths.</span></span>  
  
 <span data-ttu-id="471a7-129">Derleyici, kısmi tanımları yalnızca kendi tam yolları özdeş olduğunda birleştirir.</span><span class="sxs-lookup"><span data-stu-id="471a7-129">The compiler merges partial definitions only when their fully qualified paths are identical.</span></span>  
  
## <a name="recommendations"></a><span data-ttu-id="471a7-130">Öneriler</span><span class="sxs-lookup"><span data-stu-id="471a7-130">Recommendations</span></span>  
 <span data-ttu-id="471a7-131">Aşağıdaki öneriler iyi programlama uygulamasını temsil etmektedir.</span><span class="sxs-lookup"><span data-stu-id="471a7-131">The following recommendations represent good programming practice.</span></span>  
  
- <span data-ttu-id="471a7-132">**Benzersiz adlar.**</span><span class="sxs-lookup"><span data-stu-id="471a7-132">**Unique Names.**</span></span> <span data-ttu-id="471a7-133">Programlama öğelerinin adlandırılması üzerinde tam denetime sahip olduğunuzda her yerde benzersiz adların kullanılması her zaman iyi bir fikirdir.</span><span class="sxs-lookup"><span data-stu-id="471a7-133">When you have full control over the naming of programming elements, it is always a good idea to use unique names everywhere.</span></span> <span data-ttu-id="471a7-134">Aynı adlar ek nitelik gerektirir ve kodunuzun okunmasını daha zor hale getirir.</span><span class="sxs-lookup"><span data-stu-id="471a7-134">Identical names require extra qualification and can make your code harder to read.</span></span> <span data-ttu-id="471a7-135">Ayrıca, hafif hatalara ve beklenmedik sonuçlara yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="471a7-135">They can also lead to subtle errors and unexpected results.</span></span>  
  
- <span data-ttu-id="471a7-136">**Tam nitelik.**</span><span class="sxs-lookup"><span data-stu-id="471a7-136">**Full Qualification.**</span></span> <span data-ttu-id="471a7-137">Aynı ad alanındaki modüller ve diğer öğelerle çalışırken, en güvenli yaklaşım tüm programlama öğeleri için her zaman tam niteliğin kullanılması.</span><span class="sxs-lookup"><span data-stu-id="471a7-137">When you are working with modules and other elements in the same namespace, the safest approach is to always use full qualification for all programming elements.</span></span> <span data-ttu-id="471a7-138">Tür promosyonu bir modül üyesi için ertelendirilürse ve bu üyeyi tamamen nitelemeniz durumunda farklı bir programlama öğesine yanlışlıkla erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="471a7-138">If type promotion is defeated for a module member and you do not fully qualify that member, you could inadvertently access a different programming element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="471a7-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="471a7-139">See also</span></span>

- [<span data-ttu-id="471a7-140">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="471a7-140">Module Statement</span></span>](../../../language-reference/statements/module-statement.md)
- [<span data-ttu-id="471a7-141">Namespace Deyimi</span><span class="sxs-lookup"><span data-stu-id="471a7-141">Namespace Statement</span></span>](../../../language-reference/statements/namespace-statement.md)
- [<span data-ttu-id="471a7-142">Kısmi</span><span class="sxs-lookup"><span data-stu-id="471a7-142">Partial</span></span>](../../../language-reference/modifiers/partial.md)
- [<span data-ttu-id="471a7-143">Visual Basic'de Kapsam</span><span class="sxs-lookup"><span data-stu-id="471a7-143">Scope in Visual Basic</span></span>](scope.md)
- [<span data-ttu-id="471a7-144">Nasıl yapılır: Bir Değişkenin Kapsamını Denetleme</span><span class="sxs-lookup"><span data-stu-id="471a7-144">How to: Control the Scope of a Variable</span></span>](how-to-control-the-scope-of-a-variable.md)
- [<span data-ttu-id="471a7-145">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="471a7-145">References to Declared Elements</span></span>](references-to-declared-elements.md)
