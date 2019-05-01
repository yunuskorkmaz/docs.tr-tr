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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61920620"
---
# <a name="partial-visual-basic"></a><span data-ttu-id="dce6a-102">Kısmi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dce6a-102">Partial (Visual Basic)</span></span>
<span data-ttu-id="dce6a-103">Bir tür bildirimi türü kısmi tanımı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="dce6a-103">Indicates that a type declaration is a partial definition of the type.</span></span>  
  
 <span data-ttu-id="dce6a-104">Kullanarak, çeşitli bildirimler arasında bir tür tanımı ayırabilirsiniz `Partial` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="dce6a-104">You can divide the definition of a type among several declarations by using the `Partial` keyword.</span></span> <span data-ttu-id="dce6a-105">İstediğiniz sayıda farklı kaynak dosyaları istediğiniz sayıda kısmi bildirimleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dce6a-105">You can use as many partial declarations as you want, in as many different source files as you want.</span></span> <span data-ttu-id="dce6a-106">Ancak, tüm bildirimler aynı derleme ve aynı ad olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dce6a-106">However, all the declarations must be in the same assembly and the same namespace.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dce6a-107">Visual Basic destekler *kısmi yöntemler*, hangi genellikle uygulanır kısmi sınıflar.</span><span class="sxs-lookup"><span data-stu-id="dce6a-107">Visual Basic supports *partial methods*, which are typically implemented in partial classes.</span></span> <span data-ttu-id="dce6a-108">Daha fazla bilgi için [kısmi yöntemler](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) ve [Sub deyimi](../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="dce6a-108">For more information, see [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) and [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dce6a-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dce6a-109">Syntax</span></span>  
  
```  
[ <attrlist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] _  
Partial { Class | Structure | Interface | Module } name [ (Of typelist) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ variabledeclarations ]  
    [ proceduredeclarations ]  
{ End Class | End Structure }  
```  
  
## <a name="parts"></a><span data-ttu-id="dce6a-110">Bölümler</span><span class="sxs-lookup"><span data-stu-id="dce6a-110">Parts</span></span>  
  
|<span data-ttu-id="dce6a-111">Terim</span><span class="sxs-lookup"><span data-stu-id="dce6a-111">Term</span></span>|<span data-ttu-id="dce6a-112">Tanım</span><span class="sxs-lookup"><span data-stu-id="dce6a-112">Definition</span></span>|  
|---|---|  
|`attrlist`|<span data-ttu-id="dce6a-113">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="dce6a-113">Optional.</span></span> <span data-ttu-id="dce6a-114">Bu türüne uygulanan özniteliklerin listesi.</span><span class="sxs-lookup"><span data-stu-id="dce6a-114">List of attributes that apply to this type.</span></span> <span data-ttu-id="dce6a-115">İçine almalısınız [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md) açılı ayraçlar içinde (`< >`).</span><span class="sxs-lookup"><span data-stu-id="dce6a-115">You must enclose the [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets (`< >`).</span></span>|  
|`accessmodifier`|<span data-ttu-id="dce6a-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="dce6a-116">Optional.</span></span> <span data-ttu-id="dce6a-117">Bu tür kod erişip belirtir.</span><span class="sxs-lookup"><span data-stu-id="dce6a-117">Specifies what code can access this type.</span></span> <span data-ttu-id="dce6a-118">Bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="dce6a-118">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`Shadows`|<span data-ttu-id="dce6a-119">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="dce6a-119">Optional.</span></span> <span data-ttu-id="dce6a-120">Bkz: [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="dce6a-120">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>|  
|`MustInherit`|<span data-ttu-id="dce6a-121">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="dce6a-121">Optional.</span></span> <span data-ttu-id="dce6a-122">Bkz: [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span><span class="sxs-lookup"><span data-stu-id="dce6a-122">See [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span></span>|  
|`NotInheritable`|<span data-ttu-id="dce6a-123">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="dce6a-123">Optional.</span></span> <span data-ttu-id="dce6a-124">Bkz: [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).</span><span class="sxs-lookup"><span data-stu-id="dce6a-124">See [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).</span></span>|  
|`name`|<span data-ttu-id="dce6a-125">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="dce6a-125">Required.</span></span> <span data-ttu-id="dce6a-126">Bu türün adı.</span><span class="sxs-lookup"><span data-stu-id="dce6a-126">Name of this type.</span></span> <span data-ttu-id="dce6a-127">Tanımlanan tüm diğer kısmi bildirimlerinde aynı tür adıyla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="dce6a-127">Must match the name defined in all other partial declarations of the same type.</span></span>|  
|`Of`|<span data-ttu-id="dce6a-128">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="dce6a-128">Optional.</span></span> <span data-ttu-id="dce6a-129">Bu genel bir tür olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="dce6a-129">Specifies that this is a generic type.</span></span> <span data-ttu-id="dce6a-130">Bkz: [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="dce6a-130">See [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span>|  
|`typelist`|<span data-ttu-id="dce6a-131">İfadesini kullanıyorsanız gereklidir [,](../../../visual-basic/language-reference/statements/of-clause.md).</span><span class="sxs-lookup"><span data-stu-id="dce6a-131">Required if you use [Of](../../../visual-basic/language-reference/statements/of-clause.md).</span></span> <span data-ttu-id="dce6a-132">Bkz: [türü listesinde](../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="dce6a-132">See [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>|  
|`Inherits`|<span data-ttu-id="dce6a-133">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="dce6a-133">Optional.</span></span> <span data-ttu-id="dce6a-134">Bkz: [Inherits deyimi](../../../visual-basic/language-reference/statements/inherits-statement.md).</span><span class="sxs-lookup"><span data-stu-id="dce6a-134">See [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md).</span></span>|  
|`classname`|<span data-ttu-id="dce6a-135">İfadesini kullanıyorsanız gereklidir `Inherits`.</span><span class="sxs-lookup"><span data-stu-id="dce6a-135">Required if you use `Inherits`.</span></span> <span data-ttu-id="dce6a-136">Sınıf veya bu sınıfın türetildiği arabirimin adı.</span><span class="sxs-lookup"><span data-stu-id="dce6a-136">The name of the class or interface from which this class derives.</span></span>|  
|`Implements`|<span data-ttu-id="dce6a-137">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="dce6a-137">Optional.</span></span> <span data-ttu-id="dce6a-138">Bkz: [uygulayan deyimi](../../../visual-basic/language-reference/statements/implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="dce6a-138">See [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span>|  
|`interfacenames`|<span data-ttu-id="dce6a-139">İfadesini kullanıyorsanız gereklidir `Implements`.</span><span class="sxs-lookup"><span data-stu-id="dce6a-139">Required if you use `Implements`.</span></span> <span data-ttu-id="dce6a-140">Bu türün uyguladığı arayüzlerin adları.</span><span class="sxs-lookup"><span data-stu-id="dce6a-140">The names of the interfaces this type implements.</span></span>|  
|`variabledeclarations`|<span data-ttu-id="dce6a-141">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="dce6a-141">Optional.</span></span> <span data-ttu-id="dce6a-142">Bir ek değişkeni ve tür için olaylar bildirmek deyimler.</span><span class="sxs-lookup"><span data-stu-id="dce6a-142">Statements which declare additional variables and events for the type.</span></span>|  
|`proceduredeclarations`|<span data-ttu-id="dce6a-143">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="dce6a-143">Optional.</span></span> <span data-ttu-id="dce6a-144">Bildirme ve türü için ek yordamlar tanımlama deyimleri.</span><span class="sxs-lookup"><span data-stu-id="dce6a-144">Statements which declare and define additional procedures for the type.</span></span>|  
|<span data-ttu-id="dce6a-145">`End Class` veya `End Structure`</span><span class="sxs-lookup"><span data-stu-id="dce6a-145">`End Class` or `End Structure`</span></span>|<span data-ttu-id="dce6a-146">Bu kısmi sona erer `Class` veya `Structure` tanımı.</span><span class="sxs-lookup"><span data-stu-id="dce6a-146">Ends this partial `Class` or `Structure` definition.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dce6a-147">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dce6a-147">Remarks</span></span>  
 <span data-ttu-id="dce6a-148">Visual Basic, kullanıcı tarafından yazılan kodu ayrı kaynak dosyalarında oluşturulan kod ayırmak için kısmi sınıf tanımları kullanır.</span><span class="sxs-lookup"><span data-stu-id="dce6a-148">Visual Basic uses partial-class definitions to separate generated code from user-authored code in separate source files.</span></span> <span data-ttu-id="dce6a-149">Örneğin, **Windows Form Tasarımcısı** denetimleri için kısmi sınıflar gibi tanımlar <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="dce6a-149">For example, the **Windows Form Designer** defines partial classes for controls such as <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="dce6a-150">Bu denetimler oluşturulan kodda değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="dce6a-150">You should not modify the generated code in these controls.</span></span>  
  
 <span data-ttu-id="dce6a-151">Kısmi bir tür oluştururken, sınıf, yapı, arabirimi ve değiştiricisinin kullanımı ve devralma için olanlar gibi modülü oluşturma için tüm kuralları geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="dce6a-151">All the rules for class, structure, interface, and module creation, such as those for modifier usage and inheritance, apply when creating a partial type.</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="dce6a-152">En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="dce6a-152">Best Practices</span></span>  
  
- <span data-ttu-id="dce6a-153">Normal koşullar altında tek bir türde geliştirme arasında iki veya daha fazla bildirimleri bölmeniz gerekir değil.</span><span class="sxs-lookup"><span data-stu-id="dce6a-153">Under normal circumstances, you should not split the development of a single type across two or more declarations.</span></span> <span data-ttu-id="dce6a-154">Bu nedenle, çoğu durumda gerekmeyen `Partial` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="dce6a-154">Therefore, in most cases you do not need the `Partial` keyword.</span></span>  
  
- <span data-ttu-id="dce6a-155">Okunabilirlik için her bir kısmi bildirimi bir tür içermelidir `Partial` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="dce6a-155">For readability, every partial declaration of a type should include the `Partial` keyword.</span></span> <span data-ttu-id="dce6a-156">Derleyicinin anahtar sözcüğü atlamak en fazla bir kısmi bildirimi sağlar; iki veya daha fazla Bunu atlarsanız, derleyici bir hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="dce6a-156">The compiler allows at most one partial declaration to omit the keyword; if two or more omit it the compiler signals an error.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="dce6a-157">Davranış</span><span class="sxs-lookup"><span data-stu-id="dce6a-157">Behavior</span></span>  
  
- <span data-ttu-id="dce6a-158">**Bildirimleri birleşimi.**</span><span class="sxs-lookup"><span data-stu-id="dce6a-158">**Union of Declarations.**</span></span> <span data-ttu-id="dce6a-159">Derleyicinin tür tüm kısmi bildirimleri birleşimi değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="dce6a-159">The compiler treats the type as the union of all its partial declarations.</span></span> <span data-ttu-id="dce6a-160">Kısmi her tanımındaki her değiştiricisi türün tamamı için geçerlidir ve her kısmi tanımındaki her üye, türün tamamı için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dce6a-160">Every modifier from every partial definition applies to the entire type, and every member from every partial definition is available to the entire type.</span></span>  
  
- <span data-ttu-id="dce6a-161">**Tür promosyonu modülleri kısmi türler için izin verilmiyor.**</span><span class="sxs-lookup"><span data-stu-id="dce6a-161">**Type Promotion Not Allowed For Partial Types in Modules.**</span></span> <span data-ttu-id="dce6a-162">Kısmi bir tanımını modül içinde ise, o türün tür yükseltme otomatik olarak engellenmediğinden olur.</span><span class="sxs-lookup"><span data-stu-id="dce6a-162">If a partial definition is inside a module, type promotion of that type is automatically defeated.</span></span> <span data-ttu-id="dce6a-163">Böyle bir durumda, kısmi tanımları kümesini beklenmeyen sonuçlar ve hatta derleyici hataları neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="dce6a-163">In such a case, a set of partial definitions can cause unexpected results and even compiler errors.</span></span> <span data-ttu-id="dce6a-164">Daha fazla bilgi için [tür promosyonu](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span><span class="sxs-lookup"><span data-stu-id="dce6a-164">For more information, see [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span></span>  
  
     <span data-ttu-id="dce6a-165">Yalnızca tam yollarının aynı olduğunda derleyici kısmi tanımları birleştirir.</span><span class="sxs-lookup"><span data-stu-id="dce6a-165">The compiler merges partial definitions only when their fully qualified paths are identical.</span></span>  
  
 <span data-ttu-id="dce6a-166">`Partial` Anahtar sözcüğü bu bağlamda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="dce6a-166">The `Partial` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="dce6a-167">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="dce6a-167">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="dce6a-168">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="dce6a-168">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
## <a name="example"></a><span data-ttu-id="dce6a-169">Örnek</span><span class="sxs-lookup"><span data-stu-id="dce6a-169">Example</span></span>  
 <span data-ttu-id="dce6a-170">Aşağıdaki örnek, sınıf tanımını böler `sampleClass` alanına iki bildirimler, her biri farklı bir tanımlar `Sub` yordamı.</span><span class="sxs-lookup"><span data-stu-id="dce6a-170">The following example splits the definition of class `sampleClass` into two declarations, each of which defines a different `Sub` procedure.</span></span>  
  
 [!code-vb[VbVbalrKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#3)]  
  
 <span data-ttu-id="dce6a-171">İki kısmi tanım önceki örnekte, aynı kaynak dosyada veya iki farklı kaynak dosyalarında olabilir.</span><span class="sxs-lookup"><span data-stu-id="dce6a-171">The two partial definitions in the preceding example could be in the same source file or in two different source files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dce6a-172">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dce6a-172">See also</span></span>

- [<span data-ttu-id="dce6a-173">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="dce6a-173">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="dce6a-174">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="dce6a-174">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="dce6a-175">Tür Yükseltme</span><span class="sxs-lookup"><span data-stu-id="dce6a-175">Type Promotion</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
- [<span data-ttu-id="dce6a-176">Shadows</span><span class="sxs-lookup"><span data-stu-id="dce6a-176">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="dce6a-177">Visual Basic'de genel türler</span><span class="sxs-lookup"><span data-stu-id="dce6a-177">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="dce6a-178">Kısmi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="dce6a-178">Partial Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
