---
title: Kısmi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Partial
- partial
helpviewer_keywords:
- structures [Visual Basic], partial
- classes [Visual Basic]
- partial, types [Visual Basic]
- partial, structures
- partial, classes [Visual Basic]
- classes [Visual Basic], partial
- Partial keyword [Visual Basic]
- type promotion
ms.assetid: 7adaef80-f435-46e1-970a-269fff63b448
ms.openlocfilehash: 0f74935d58d47e65b5eb614abc86a3fc9c8e6c42
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838371"
---
# <a name="partial-visual-basic"></a><span data-ttu-id="1d907-102">Kısmi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d907-102">Partial (Visual Basic)</span></span>
<span data-ttu-id="1d907-103">Bir tür bildirimi türü kısmi tanımı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="1d907-103">Indicates that a type declaration is a partial definition of the type.</span></span>  
  
 <span data-ttu-id="1d907-104">Kullanarak, çeşitli bildirimler arasında bir tür tanımı ayırabilirsiniz `Partial` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="1d907-104">You can divide the definition of a type among several declarations by using the `Partial` keyword.</span></span> <span data-ttu-id="1d907-105">İstediğiniz sayıda farklı kaynak dosyaları istediğiniz sayıda kısmi bildirimleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1d907-105">You can use as many partial declarations as you want, in as many different source files as you want.</span></span> <span data-ttu-id="1d907-106">Ancak, tüm bildirimler aynı derleme ve aynı ad olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1d907-106">However, all the declarations must be in the same assembly and the same namespace.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1d907-107">Visual Basic destekler *kısmi yöntemler*, hangi genellikle uygulanır kısmi sınıflar.</span><span class="sxs-lookup"><span data-stu-id="1d907-107">Visual Basic supports *partial methods*, which are typically implemented in partial classes.</span></span> <span data-ttu-id="1d907-108">Daha fazla bilgi için [kısmi yöntemler](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) ve [Sub deyimi](../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1d907-108">For more information, see [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) and [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d907-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1d907-109">Syntax</span></span>  
  
```  
[ <attrlist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] _  
Partial { Class | Structure | Interface | Module } name [ (Of typelist) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ variabledeclarations ]  
    [ proceduredeclarations ]  
{ End Class | End Structure }  
```  
  
## <a name="parts"></a><span data-ttu-id="1d907-110">Bölümler</span><span class="sxs-lookup"><span data-stu-id="1d907-110">Parts</span></span>  
  
|<span data-ttu-id="1d907-111">Terim</span><span class="sxs-lookup"><span data-stu-id="1d907-111">Term</span></span>|<span data-ttu-id="1d907-112">Tanım</span><span class="sxs-lookup"><span data-stu-id="1d907-112">Definition</span></span>|  
|---|---|  
|`attrlist`|<span data-ttu-id="1d907-113">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="1d907-113">Optional.</span></span> <span data-ttu-id="1d907-114">Bu türüne uygulanan özniteliklerin listesi.</span><span class="sxs-lookup"><span data-stu-id="1d907-114">List of attributes that apply to this type.</span></span> <span data-ttu-id="1d907-115">İçine almalısınız [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md) açılı ayraçlar içinde (`< >`).</span><span class="sxs-lookup"><span data-stu-id="1d907-115">You must enclose the [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets (`< >`).</span></span>|  
|`accessmodifier`|<span data-ttu-id="1d907-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="1d907-116">Optional.</span></span> <span data-ttu-id="1d907-117">Bu tür kod erişip belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d907-117">Specifies what code can access this type.</span></span> <span data-ttu-id="1d907-118">Bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="1d907-118">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`Shadows`|<span data-ttu-id="1d907-119">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="1d907-119">Optional.</span></span> <span data-ttu-id="1d907-120">Bkz: [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="1d907-120">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>|  
|`MustInherit`|<span data-ttu-id="1d907-121">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="1d907-121">Optional.</span></span> <span data-ttu-id="1d907-122">Bkz: [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span><span class="sxs-lookup"><span data-stu-id="1d907-122">See [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span></span>|  
|`NotInheritable`|<span data-ttu-id="1d907-123">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="1d907-123">Optional.</span></span> <span data-ttu-id="1d907-124">Bkz: [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).</span><span class="sxs-lookup"><span data-stu-id="1d907-124">See [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).</span></span>|  
|`name`|<span data-ttu-id="1d907-125">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="1d907-125">Required.</span></span> <span data-ttu-id="1d907-126">Bu türün adı.</span><span class="sxs-lookup"><span data-stu-id="1d907-126">Name of this type.</span></span> <span data-ttu-id="1d907-127">Tanımlanan tüm diğer kısmi bildirimlerinde aynı tür adıyla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="1d907-127">Must match the name defined in all other partial declarations of the same type.</span></span>|  
|`Of`|<span data-ttu-id="1d907-128">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="1d907-128">Optional.</span></span> <span data-ttu-id="1d907-129">Bu genel bir tür olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d907-129">Specifies that this is a generic type.</span></span> <span data-ttu-id="1d907-130">Bkz: [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="1d907-130">See [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span>|  
|`typelist`|<span data-ttu-id="1d907-131">İfadesini kullanıyorsanız gereklidir [,](../../../visual-basic/language-reference/statements/of-clause.md).</span><span class="sxs-lookup"><span data-stu-id="1d907-131">Required if you use [Of](../../../visual-basic/language-reference/statements/of-clause.md).</span></span> <span data-ttu-id="1d907-132">Bkz: [türü listesinde](../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="1d907-132">See [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>|  
|`Inherits`|<span data-ttu-id="1d907-133">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="1d907-133">Optional.</span></span> <span data-ttu-id="1d907-134">Bkz: [Inherits deyimi](../../../visual-basic/language-reference/statements/inherits-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1d907-134">See [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md).</span></span>|  
|`classname`|<span data-ttu-id="1d907-135">İfadesini kullanıyorsanız gereklidir `Inherits`.</span><span class="sxs-lookup"><span data-stu-id="1d907-135">Required if you use `Inherits`.</span></span> <span data-ttu-id="1d907-136">Sınıf veya bu sınıfın türetildiği arabirimin adı.</span><span class="sxs-lookup"><span data-stu-id="1d907-136">The name of the class or interface from which this class derives.</span></span>|  
|`Implements`|<span data-ttu-id="1d907-137">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="1d907-137">Optional.</span></span> <span data-ttu-id="1d907-138">Bkz: [uygulayan deyimi](../../../visual-basic/language-reference/statements/implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1d907-138">See [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span>|  
|`interfacenames`|<span data-ttu-id="1d907-139">İfadesini kullanıyorsanız gereklidir `Implements`.</span><span class="sxs-lookup"><span data-stu-id="1d907-139">Required if you use `Implements`.</span></span> <span data-ttu-id="1d907-140">Bu türün uyguladığı arayüzlerin adları.</span><span class="sxs-lookup"><span data-stu-id="1d907-140">The names of the interfaces this type implements.</span></span>|  
|`variabledeclarations`|<span data-ttu-id="1d907-141">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="1d907-141">Optional.</span></span> <span data-ttu-id="1d907-142">Bir ek değişkeni ve tür için olaylar bildirmek deyimler.</span><span class="sxs-lookup"><span data-stu-id="1d907-142">Statements which declare additional variables and events for the type.</span></span>|  
|`proceduredeclarations`|<span data-ttu-id="1d907-143">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="1d907-143">Optional.</span></span> <span data-ttu-id="1d907-144">Bildirme ve türü için ek yordamlar tanımlama deyimleri.</span><span class="sxs-lookup"><span data-stu-id="1d907-144">Statements which declare and define additional procedures for the type.</span></span>|  
|<span data-ttu-id="1d907-145">`End Class` veya `End Structure`</span><span class="sxs-lookup"><span data-stu-id="1d907-145">`End Class` or `End Structure`</span></span>|<span data-ttu-id="1d907-146">Bu kısmi sona erer `Class` veya `Structure` tanımı.</span><span class="sxs-lookup"><span data-stu-id="1d907-146">Ends this partial `Class` or `Structure` definition.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d907-147">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1d907-147">Remarks</span></span>  
 <span data-ttu-id="1d907-148">Visual Basic, kullanıcı tarafından yazılan kodu ayrı kaynak dosyalarında oluşturulan kod ayırmak için kısmi sınıf tanımları kullanır.</span><span class="sxs-lookup"><span data-stu-id="1d907-148">Visual Basic uses partial-class definitions to separate generated code from user-authored code in separate source files.</span></span> <span data-ttu-id="1d907-149">Örneğin, **Windows Form Tasarımcısı** denetimleri için kısmi sınıflar gibi tanımlar <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="1d907-149">For example, the **Windows Form Designer** defines partial classes for controls such as <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="1d907-150">Bu denetimler oluşturulan kodda değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1d907-150">You should not modify the generated code in these controls.</span></span>  
  
 <span data-ttu-id="1d907-151">Kısmi bir tür oluştururken, sınıf, yapı, arabirimi ve değiştiricisinin kullanımı ve devralma için olanlar gibi modülü oluşturma için tüm kuralları geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="1d907-151">All the rules for class, structure, interface, and module creation, such as those for modifier usage and inheritance, apply when creating a partial type.</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="1d907-152">En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1d907-152">Best Practices</span></span>  
  
-   <span data-ttu-id="1d907-153">Normal koşullar altında tek bir türde geliştirme arasında iki veya daha fazla bildirimleri bölmeniz gerekir değil.</span><span class="sxs-lookup"><span data-stu-id="1d907-153">Under normal circumstances, you should not split the development of a single type across two or more declarations.</span></span> <span data-ttu-id="1d907-154">Bu nedenle, çoğu durumda gerekmeyen `Partial` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="1d907-154">Therefore, in most cases you do not need the `Partial` keyword.</span></span>  
  
-   <span data-ttu-id="1d907-155">Okunabilirlik için her bir kısmi bildirimi bir tür içermelidir `Partial` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="1d907-155">For readability, every partial declaration of a type should include the `Partial` keyword.</span></span> <span data-ttu-id="1d907-156">Derleyicinin anahtar sözcüğü atlamak en fazla bir kısmi bildirimi sağlar; iki veya daha fazla Bunu atlarsanız, derleyici bir hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="1d907-156">The compiler allows at most one partial declaration to omit the keyword; if two or more omit it the compiler signals an error.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="1d907-157">Davranış</span><span class="sxs-lookup"><span data-stu-id="1d907-157">Behavior</span></span>  
  
-   <span data-ttu-id="1d907-158">**Bildirimleri birleşimi.**</span><span class="sxs-lookup"><span data-stu-id="1d907-158">**Union of Declarations.**</span></span> <span data-ttu-id="1d907-159">Derleyicinin tür tüm kısmi bildirimleri birleşimi değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="1d907-159">The compiler treats the type as the union of all its partial declarations.</span></span> <span data-ttu-id="1d907-160">Kısmi her tanımındaki her değiştiricisi türün tamamı için geçerlidir ve her kısmi tanımındaki her üye, türün tamamı için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1d907-160">Every modifier from every partial definition applies to the entire type, and every member from every partial definition is available to the entire type.</span></span>  
  
-   <span data-ttu-id="1d907-161">**Tür promosyonu modülleri kısmi türler için izin verilmiyor.**</span><span class="sxs-lookup"><span data-stu-id="1d907-161">**Type Promotion Not Allowed For Partial Types in Modules.**</span></span> <span data-ttu-id="1d907-162">Kısmi bir tanımını modül içinde ise, o türün tür yükseltme otomatik olarak engellenmediğinden olur.</span><span class="sxs-lookup"><span data-stu-id="1d907-162">If a partial definition is inside a module, type promotion of that type is automatically defeated.</span></span> <span data-ttu-id="1d907-163">Böyle bir durumda, kısmi tanımları kümesini beklenmeyen sonuçlar ve hatta derleyici hataları neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="1d907-163">In such a case, a set of partial definitions can cause unexpected results and even compiler errors.</span></span> <span data-ttu-id="1d907-164">Daha fazla bilgi için [tür promosyonu](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span><span class="sxs-lookup"><span data-stu-id="1d907-164">For more information, see [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span></span>  
  
     <span data-ttu-id="1d907-165">Yalnızca tam yollarının aynı olduğunda derleyici kısmi tanımları birleştirir.</span><span class="sxs-lookup"><span data-stu-id="1d907-165">The compiler merges partial definitions only when their fully qualified paths are identical.</span></span>  
  
 <span data-ttu-id="1d907-166">`Partial` Anahtar sözcüğü bu bağlamda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="1d907-166">The `Partial` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="1d907-167">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="1d907-167">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="1d907-168">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="1d907-168">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
## <a name="example"></a><span data-ttu-id="1d907-169">Örnek</span><span class="sxs-lookup"><span data-stu-id="1d907-169">Example</span></span>  
 <span data-ttu-id="1d907-170">Aşağıdaki örnek, sınıf tanımını böler `sampleClass` alanına iki bildirimler, her biri farklı bir tanımlar `Sub` yordamı.</span><span class="sxs-lookup"><span data-stu-id="1d907-170">The following example splits the definition of class `sampleClass` into two declarations, each of which defines a different `Sub` procedure.</span></span>  
  
 [!code-vb[VbVbalrKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#3)]  
  
 <span data-ttu-id="1d907-171">İki kısmi tanım önceki örnekte, aynı kaynak dosyada veya iki farklı kaynak dosyalarında olabilir.</span><span class="sxs-lookup"><span data-stu-id="1d907-171">The two partial definitions in the preceding example could be in the same source file or in two different source files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d907-172">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d907-172">See also</span></span>

- [<span data-ttu-id="1d907-173">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="1d907-173">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="1d907-174">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="1d907-174">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="1d907-175">Tür Yükseltme</span><span class="sxs-lookup"><span data-stu-id="1d907-175">Type Promotion</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
- [<span data-ttu-id="1d907-176">Shadows</span><span class="sxs-lookup"><span data-stu-id="1d907-176">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="1d907-177">Visual Basic'de genel türler</span><span class="sxs-lookup"><span data-stu-id="1d907-177">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="1d907-178">Kısmi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1d907-178">Partial Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
