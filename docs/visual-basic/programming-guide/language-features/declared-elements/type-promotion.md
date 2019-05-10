---
title: Tür Yükseltme (Visual Basic)
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
ms.openlocfilehash: 02d53770186f7600b190231dc73938ff1589cef6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64610353"
---
# <a name="type-promotion-visual-basic"></a><span data-ttu-id="55434-102">Tür Yükseltme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="55434-102">Type Promotion (Visual Basic)</span></span>
<span data-ttu-id="55434-103">Modül içindeki bir programlama öğesi bildirdiğinizde, Visual Basic modülü içeren ad alanı kapsamında yükseltir.</span><span class="sxs-lookup"><span data-stu-id="55434-103">When you declare a programming element in a module, Visual Basic promotes its scope to the namespace containing the module.</span></span> <span data-ttu-id="55434-104">Bu olarak bilinir *türü promosyon*.</span><span class="sxs-lookup"><span data-stu-id="55434-104">This is known as *type promotion*.</span></span>  
  
 <span data-ttu-id="55434-105">Aşağıdaki örnek, bir modül iskelet tanımını ve bu modül iki üyeleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="55434-105">The following example shows a skeleton definition of a module and two members of that module.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#1)]  
  
 <span data-ttu-id="55434-106">İçinde `projModule`, programlama Modül düzeyinde bildirilen öğeler için yükseltilen `projNamespace`.</span><span class="sxs-lookup"><span data-stu-id="55434-106">Within `projModule`, programming elements declared at module level are promoted to `projNamespace`.</span></span> <span data-ttu-id="55434-107">Önceki örnekte `basicEnum` ve `innerClass` yükseltilir, ancak `numberSub` Modül düzeyinde bildirilmediğinden değildir.</span><span class="sxs-lookup"><span data-stu-id="55434-107">In the preceding example, `basicEnum` and `innerClass` are promoted, but `numberSub` is not, because it is not declared at module level.</span></span>  
  
## <a name="effect-of-type-promotion"></a><span data-ttu-id="55434-108">Tür promosyonu etkisi</span><span class="sxs-lookup"><span data-stu-id="55434-108">Effect of Type Promotion</span></span>  
 <span data-ttu-id="55434-109">Tür promosyonu etkisini nitelik dize modül adını içerecek şekilde gerekmeyen ' dir.</span><span class="sxs-lookup"><span data-stu-id="55434-109">The effect of type promotion is that a qualification string does not need to include the module name.</span></span> <span data-ttu-id="55434-110">Aşağıdaki örnek önceki örnekte iki yordam çağrıları yapar.</span><span class="sxs-lookup"><span data-stu-id="55434-110">The following example makes two calls to the procedure in the preceding example.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#2)]  
  
 <span data-ttu-id="55434-111">Önceki örnekte, ilk çağrı, tam nitelenmiş dizeleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="55434-111">In the preceding example, the first call uses complete qualification strings.</span></span> <span data-ttu-id="55434-112">Ancak, bu tür yükseltme nedeniyle gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="55434-112">However, this is not necessary because of type promotion.</span></span> <span data-ttu-id="55434-113">İkinci çağrı da erişir modülün üyeleri dahil etmeden `projModule` nitelik Dizelerdeki.</span><span class="sxs-lookup"><span data-stu-id="55434-113">The second call also accesses the module's members without including `projModule` in the qualification strings.</span></span>  
  
## <a name="defeat-of-type-promotion"></a><span data-ttu-id="55434-114">Tür yükseltme zorluğunu</span><span class="sxs-lookup"><span data-stu-id="55434-114">Defeat of Type Promotion</span></span>  
 <span data-ttu-id="55434-115">Tür yükseltme, ad alanı aynı ada sahip bir üye modülü üye olarak zaten varsa, bu modül üyenin engellenmediğinden.</span><span class="sxs-lookup"><span data-stu-id="55434-115">If the namespace already has a member with the same name as a module member, type promotion is defeated for that module member.</span></span> <span data-ttu-id="55434-116">Aşağıdaki örnek, bir numaralandırma ve aynı ad alanı içinde bir modül bir çatı tanımı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="55434-116">The following example shows a skeleton definition of an enumeration and a module within the same namespace.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#3)]  
  
 <span data-ttu-id="55434-117">Önceki örnekte, Visual Basic sınıf düzeyine yükseltilemiyor `abc` için `thisNameSpace` zaten var olduğundan ad alanı düzeyinde aynı ada sahip bir sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="55434-117">In the preceding example, Visual Basic cannot promote class `abc` to `thisNameSpace` because there is already an enumeration with the same name at namespace level.</span></span> <span data-ttu-id="55434-118">Erişim için `abcSub`, tam nitelenmiş dize kullanmalısınız `thisNamespace.thisModule.abc.abcSub`.</span><span class="sxs-lookup"><span data-stu-id="55434-118">To access `abcSub`, you must use the full qualification string `thisNamespace.thisModule.abc.abcSub`.</span></span> <span data-ttu-id="55434-119">Ancak, sınıf `xyz` hala yükseltilir ve erişebileceğiniz `xyzSub` kısa nitelik dize ile `thisNamespace.xyz.xyzSub`.</span><span class="sxs-lookup"><span data-stu-id="55434-119">However, class `xyz` is still promoted, and you can access `xyzSub` with the shorter qualification string `thisNamespace.xyz.xyzSub`.</span></span>  
  
### <a name="defeat-of-type-promotion-for-partial-types"></a><span data-ttu-id="55434-120">Kısmi türler için tür yükseltme zorluğunu</span><span class="sxs-lookup"><span data-stu-id="55434-120">Defeat of Type Promotion for Partial Types</span></span>  
 <span data-ttu-id="55434-121">Bir sınıf veya yapı içinde bir modül kullanıyorsa [kısmi](../../../../visual-basic/language-reference/modifiers/partial.md) anahtar sözcüğü, tür yükseltme, bu sınıf veya yapı için otomatik olarak engellenmediğinden aynı ada sahip bir üye ad alanına sahip olup olmadığını.</span><span class="sxs-lookup"><span data-stu-id="55434-121">If a class or structure inside a module uses the [Partial](../../../../visual-basic/language-reference/modifiers/partial.md) keyword, type promotion is automatically defeated for that class or structure, whether or not the namespace has a member with the same name.</span></span> <span data-ttu-id="55434-122">Diğer öğeleri modüldeki tür yükseltme için yine de uygundur.</span><span class="sxs-lookup"><span data-stu-id="55434-122">Other elements in the module are still eligible for type promotion.</span></span>  
  
 <span data-ttu-id="55434-123">**Sonuçları.**</span><span class="sxs-lookup"><span data-stu-id="55434-123">**Consequences.**</span></span> <span data-ttu-id="55434-124">Tür promosyonu kısmi tanımı, zorluğunu, beklenmeyen sonuçlar ve hatta derleyici hataları neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="55434-124">Defeat of type promotion of a partial definition can cause unexpected results and even compiler errors.</span></span> <span data-ttu-id="55434-125">Aşağıdaki örnek, bir sınıfın biri içinde bir modül olan iskelet kısmi tanımları gösterir.</span><span class="sxs-lookup"><span data-stu-id="55434-125">The following example shows skeleton partial definitions of a class, one of which is inside a module.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#4)]  
  
 <span data-ttu-id="55434-126">Önceki örnekte, geliştiricinin iki kısmi tanımlarını birleştirmek için derleyici beklenebilir `sampleClass`.</span><span class="sxs-lookup"><span data-stu-id="55434-126">In the preceding example, the developer might expect the compiler to merge the two partial definitions of `sampleClass`.</span></span> <span data-ttu-id="55434-127">Ancak, derleyici kısmi tanım içinde promosyon düşünmez `sampleModule`.</span><span class="sxs-lookup"><span data-stu-id="55434-127">However, the compiler does not consider promotion for the partial definition inside `sampleModule`.</span></span> <span data-ttu-id="55434-128">Sonuç olarak, iki ayrı ve farklı sınıflar derlemek çalışır, hem adlandırılmış `sampleClass` ancak farklı nitelik yolları.</span><span class="sxs-lookup"><span data-stu-id="55434-128">As a result, it attempts to compile two separate and distinct classes, both named `sampleClass` but with different qualification paths.</span></span>  
  
 <span data-ttu-id="55434-129">Yalnızca tam yollarının aynı olduğunda derleyici kısmi tanımları birleştirir.</span><span class="sxs-lookup"><span data-stu-id="55434-129">The compiler merges partial definitions only when their fully qualified paths are identical.</span></span>  
  
## <a name="recommendations"></a><span data-ttu-id="55434-130">Öneriler</span><span class="sxs-lookup"><span data-stu-id="55434-130">Recommendations</span></span>  
 <span data-ttu-id="55434-131">Aşağıdaki öneriler, iyi bir programlama uygulama temsil eder.</span><span class="sxs-lookup"><span data-stu-id="55434-131">The following recommendations represent good programming practice.</span></span>  
  
- <span data-ttu-id="55434-132">**Benzersiz adları.**</span><span class="sxs-lookup"><span data-stu-id="55434-132">**Unique Names.**</span></span> <span data-ttu-id="55434-133">Programlama öğelerine adlandırma üzerinde tam denetime sahiptir, bu her zaman her yerde benzersiz adlar kullanacak şekilde iyi bir fikirdir.</span><span class="sxs-lookup"><span data-stu-id="55434-133">When you have full control over the naming of programming elements, it is always a good idea to use unique names everywhere.</span></span> <span data-ttu-id="55434-134">Aynı adlara ek onay gerektirir ve kodunuzun okunmasını zorlaştırabilir.</span><span class="sxs-lookup"><span data-stu-id="55434-134">Identical names require extra qualification and can make your code harder to read.</span></span> <span data-ttu-id="55434-135">Bunlar ayrıca ince hatalar ve beklenmeyen sonuçlara yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="55434-135">They can also lead to subtle errors and unexpected results.</span></span>  
  
- <span data-ttu-id="55434-136">**Tam nitelenmiş.**</span><span class="sxs-lookup"><span data-stu-id="55434-136">**Full Qualification.**</span></span> <span data-ttu-id="55434-137">Modüller ve diğer öğeleri aynı ad ile çalışırken, güvenli bir yaklaşım her zaman tam nitelenmiş için tüm programlama öğeleri kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="55434-137">When you are working with modules and other elements in the same namespace, the safest approach is to always use full qualification for all programming elements.</span></span> <span data-ttu-id="55434-138">Tür promosyonu modülü üyesi engellenmediğinden ve tam olarak bu üyede nitelendirmeyin, yanlışlıkla farklı bir programlama öğesine erişebilir.</span><span class="sxs-lookup"><span data-stu-id="55434-138">If type promotion is defeated for a module member and you do not fully qualify that member, you could inadvertently access a different programming element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55434-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55434-139">See also</span></span>

- [<span data-ttu-id="55434-140">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="55434-140">Module Statement</span></span>](../../../../visual-basic/language-reference/statements/module-statement.md)
- [<span data-ttu-id="55434-141">Namespace Deyimi</span><span class="sxs-lookup"><span data-stu-id="55434-141">Namespace Statement</span></span>](../../../../visual-basic/language-reference/statements/namespace-statement.md)
- [<span data-ttu-id="55434-142">Partial</span><span class="sxs-lookup"><span data-stu-id="55434-142">Partial</span></span>](../../../../visual-basic/language-reference/modifiers/partial.md)
- [<span data-ttu-id="55434-143">Visual Basic'de kapsam</span><span class="sxs-lookup"><span data-stu-id="55434-143">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [<span data-ttu-id="55434-144">Nasıl yapılır: Bir değişkenin kapsamını denetleme</span><span class="sxs-lookup"><span data-stu-id="55434-144">How to: Control the Scope of a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)
- [<span data-ttu-id="55434-145">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="55434-145">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
