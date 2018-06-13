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
ms.openlocfilehash: c94c3bf1a1e3e4c724f90690f52e97e8216cb9a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604620"
---
# <a name="partial-visual-basic"></a><span data-ttu-id="7613e-102">Kısmi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7613e-102">Partial (Visual Basic)</span></span>
<span data-ttu-id="7613e-103">Tür bildirimi kısmi tanım türü olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="7613e-103">Indicates that a type declaration is a partial definition of the type.</span></span>  
  
 <span data-ttu-id="7613e-104">Kullanarak birkaç bildirimler arasında bir tür tanımını bölebilirsiniz `Partial` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="7613e-104">You can divide the definition of a type among several declarations by using the `Partial` keyword.</span></span> <span data-ttu-id="7613e-105">İstediğiniz sayıda farklı kaynak dosyalar istediğiniz sayıda kısmi bildirimleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7613e-105">You can use as many partial declarations as you want, in as many different source files as you want.</span></span> <span data-ttu-id="7613e-106">Ancak, tüm bildirimler aynı bütünleştirilmiş kodda ve aynı ad olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7613e-106">However, all the declarations must be in the same assembly and the same namespace.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7613e-107">Visual Basic destekler *kısmi yöntemler*, hangi genellikle uygulanır kısmi sınıflar.</span><span class="sxs-lookup"><span data-stu-id="7613e-107">Visual Basic supports *partial methods*, which are typically implemented in partial classes.</span></span> <span data-ttu-id="7613e-108">Daha fazla bilgi için bkz: [kısmi yöntemler](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) ve [Sub deyimi](../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7613e-108">For more information, see [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) and [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7613e-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7613e-109">Syntax</span></span>  
  
```  
[ <attrlist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] _  
Partial { Class | Structure | Interface | Module } name [ (Of typelist) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ variabledeclarations ]  
    [ proceduredeclarations ]  
{ End Class | End Structure }  
```  
  
## <a name="parts"></a><span data-ttu-id="7613e-110">Bölümler</span><span class="sxs-lookup"><span data-stu-id="7613e-110">Parts</span></span>  
  
|<span data-ttu-id="7613e-111">Terim</span><span class="sxs-lookup"><span data-stu-id="7613e-111">Term</span></span>|<span data-ttu-id="7613e-112">Tanım</span><span class="sxs-lookup"><span data-stu-id="7613e-112">Definition</span></span>|  
|---|---|  
|`attrlist`|<span data-ttu-id="7613e-113">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="7613e-113">Optional.</span></span> <span data-ttu-id="7613e-114">Bu türü için geçerli öznitelikler listesi.</span><span class="sxs-lookup"><span data-stu-id="7613e-114">List of attributes that apply to this type.</span></span> <span data-ttu-id="7613e-115">İçine almalısınız [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md) açılı ayraç (`< >`).</span><span class="sxs-lookup"><span data-stu-id="7613e-115">You must enclose the [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets (`< >`).</span></span>|  
|`accessmodifier`|<span data-ttu-id="7613e-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="7613e-116">Optional.</span></span> <span data-ttu-id="7613e-117">Bu tür hangi kod erişip belirtir.</span><span class="sxs-lookup"><span data-stu-id="7613e-117">Specifies what code can access this type.</span></span> <span data-ttu-id="7613e-118">Bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="7613e-118">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`Shadows`|<span data-ttu-id="7613e-119">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="7613e-119">Optional.</span></span> <span data-ttu-id="7613e-120">Bkz: [gölgeleri](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="7613e-120">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>|  
|`MustInherit`|<span data-ttu-id="7613e-121">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="7613e-121">Optional.</span></span> <span data-ttu-id="7613e-122">Bkz: [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span><span class="sxs-lookup"><span data-stu-id="7613e-122">See [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span></span>|  
|`NotInheritable`|<span data-ttu-id="7613e-123">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="7613e-123">Optional.</span></span> <span data-ttu-id="7613e-124">Bkz: [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).</span><span class="sxs-lookup"><span data-stu-id="7613e-124">See [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).</span></span>|  
|`name`|<span data-ttu-id="7613e-125">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="7613e-125">Required.</span></span> <span data-ttu-id="7613e-126">Bu tür adı.</span><span class="sxs-lookup"><span data-stu-id="7613e-126">Name of this type.</span></span> <span data-ttu-id="7613e-127">Tüm diğer kısmi bildirimlerinde aynı türde tanımlanan adıyla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="7613e-127">Must match the name defined in all other partial declarations of the same type.</span></span>|  
|`Of`|<span data-ttu-id="7613e-128">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="7613e-128">Optional.</span></span> <span data-ttu-id="7613e-129">Bu genel bir tür olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="7613e-129">Specifies that this is a generic type.</span></span> <span data-ttu-id="7613e-130">Bkz: [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="7613e-130">See [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span>|  
|`typelist`|<span data-ttu-id="7613e-131">Kullanırsanız, gerekli [,](../../../visual-basic/language-reference/statements/of-clause.md).</span><span class="sxs-lookup"><span data-stu-id="7613e-131">Required if you use [Of](../../../visual-basic/language-reference/statements/of-clause.md).</span></span> <span data-ttu-id="7613e-132">Bkz: [yazın listesi](../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="7613e-132">See [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>|  
|`Inherits`|<span data-ttu-id="7613e-133">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="7613e-133">Optional.</span></span> <span data-ttu-id="7613e-134">Bkz: [Inherits deyimi](../../../visual-basic/language-reference/statements/inherits-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7613e-134">See [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md).</span></span>|  
|`classname`|<span data-ttu-id="7613e-135">Kullanırsanız, gerekli `Inherits`.</span><span class="sxs-lookup"><span data-stu-id="7613e-135">Required if you use `Inherits`.</span></span> <span data-ttu-id="7613e-136">Sınıf veya bu sınıf türetilen arabirim adı.</span><span class="sxs-lookup"><span data-stu-id="7613e-136">The name of the class or interface from which this class derives.</span></span>|  
|`Implements`|<span data-ttu-id="7613e-137">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="7613e-137">Optional.</span></span> <span data-ttu-id="7613e-138">Bkz: [uygulayan deyimi](../../../visual-basic/language-reference/statements/implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7613e-138">See [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span>|  
|`interfacenames`|<span data-ttu-id="7613e-139">Kullanırsanız, gerekli `Implements`.</span><span class="sxs-lookup"><span data-stu-id="7613e-139">Required if you use `Implements`.</span></span> <span data-ttu-id="7613e-140">Bu tür uygulayan arabirimleri adları.</span><span class="sxs-lookup"><span data-stu-id="7613e-140">The names of the interfaces this type implements.</span></span>|  
|`variabledeclarations`|<span data-ttu-id="7613e-141">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="7613e-141">Optional.</span></span> <span data-ttu-id="7613e-142">Ek değişkenleri ve tür için olaylar declare deyimlerini.</span><span class="sxs-lookup"><span data-stu-id="7613e-142">Statements which declare additional variables and events for the type.</span></span>|  
|`proceduredeclarations`|<span data-ttu-id="7613e-143">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="7613e-143">Optional.</span></span> <span data-ttu-id="7613e-144">Bildirme ve türü için ek yordamlar tanımlama deyimleri.</span><span class="sxs-lookup"><span data-stu-id="7613e-144">Statements which declare and define additional procedures for the type.</span></span>|  
|<span data-ttu-id="7613e-145">`End Class` Veya `End Structure`</span><span class="sxs-lookup"><span data-stu-id="7613e-145">`End Class` or `End Structure`</span></span>|<span data-ttu-id="7613e-146">Bu kısmi sona `Class` veya `Structure` tanımı.</span><span class="sxs-lookup"><span data-stu-id="7613e-146">Ends this partial `Class` or `Structure` definition.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7613e-147">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7613e-147">Remarks</span></span>  
 <span data-ttu-id="7613e-148">Visual Basic parçalı sınıf tanımları oluşturulan kod kullanıcı tarafından yazılan kodu ayrı kaynak dosyalarında ayırmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="7613e-148">Visual Basic uses partial-class definitions to separate generated code from user-authored code in separate source files.</span></span> <span data-ttu-id="7613e-149">Örneğin, **Windows Form Tasarımcısı** denetimleri için kısmi sınıflar gibi tanımlar <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="7613e-149">For example, the **Windows Form Designer** defines partial classes for controls such as <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="7613e-150">Bu denetimler oluşturulan kodda değiştirmemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7613e-150">You should not modify the generated code in these controls.</span></span>  
  
 <span data-ttu-id="7613e-151">Sınıfı, yapısı, arabirim ve değiştirici kullanım ve devralma için olanlar gibi modülü oluşturma için tüm kuralları kısmi türü oluştururken uygulayın.</span><span class="sxs-lookup"><span data-stu-id="7613e-151">All the rules for class, structure, interface, and module creation, such as those for modifier usage and inheritance, apply when creating a partial type.</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="7613e-152">En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7613e-152">Best Practices</span></span>  
  
-   <span data-ttu-id="7613e-153">Normal koşullar altında tek bir türü geliştirme iki veya daha fazla bildirimler arasında bölmek değil.</span><span class="sxs-lookup"><span data-stu-id="7613e-153">Under normal circumstances, you should not split the development of a single type across two or more declarations.</span></span> <span data-ttu-id="7613e-154">Bu nedenle, çoğu durumda, gerekmeyen `Partial` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="7613e-154">Therefore, in most cases you do not need the `Partial` keyword.</span></span>  
  
-   <span data-ttu-id="7613e-155">Okunabilirlik için bir türün kısmi her bildirimi içermelidir `Partial` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="7613e-155">For readability, every partial declaration of a type should include the `Partial` keyword.</span></span> <span data-ttu-id="7613e-156">Derleyici anahtar sözcüğü atlamak en çok bir kısmi bildirimi sağlar; iki veya daha fazla atlarsanız, derleyici bir hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="7613e-156">The compiler allows at most one partial declaration to omit the keyword; if two or more omit it the compiler signals an error.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="7613e-157">Davranış</span><span class="sxs-lookup"><span data-stu-id="7613e-157">Behavior</span></span>  
  
-   <span data-ttu-id="7613e-158">**Bildirimleri birleşimi.**</span><span class="sxs-lookup"><span data-stu-id="7613e-158">**Union of Declarations.**</span></span> <span data-ttu-id="7613e-159">Derleyici türü tüm kısmi bildirimlerinde birleşimi değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="7613e-159">The compiler treats the type as the union of all its partial declarations.</span></span> <span data-ttu-id="7613e-160">Her değiştiricisi her kısmi tanımından tüm türü için geçerlidir ve her kısmi tanımından her bir üyenin tüm türü kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7613e-160">Every modifier from every partial definition applies to the entire type, and every member from every partial definition is available to the entire type.</span></span>  
  
-   <span data-ttu-id="7613e-161">**Tür promosyonu modüllerinde kısmi türleri için izin verilmiyor.**</span><span class="sxs-lookup"><span data-stu-id="7613e-161">**Type Promotion Not Allowed For Partial Types in Modules.**</span></span> <span data-ttu-id="7613e-162">Kısmi bir tanımı içinde bir modül türü tür yükseltme otomatik olarak engellenmediğinden ise.</span><span class="sxs-lookup"><span data-stu-id="7613e-162">If a partial definition is inside a module, type promotion of that type is automatically defeated.</span></span> <span data-ttu-id="7613e-163">Böyle bir durumda, kısmi tanımları kümesini beklenmeyen sonuçlara ve hatta derleyici hataları neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="7613e-163">In such a case, a set of partial definitions can cause unexpected results and even compiler errors.</span></span> <span data-ttu-id="7613e-164">Daha fazla bilgi için bkz: [tür yükseltme](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span><span class="sxs-lookup"><span data-stu-id="7613e-164">For more information, see [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span></span>  
  
     <span data-ttu-id="7613e-165">Yalnızca tam yollarına aynı zaman derleyici kısmi tanımları birleştirir.</span><span class="sxs-lookup"><span data-stu-id="7613e-165">The compiler merges partial definitions only when their fully qualified paths are identical.</span></span>  
  
 <span data-ttu-id="7613e-166">`Partial` Anahtar sözcüğü bu bağlamlarında kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="7613e-166">The `Partial` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="7613e-167">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="7613e-167">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="7613e-168">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="7613e-168">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
## <a name="example"></a><span data-ttu-id="7613e-169">Örnek</span><span class="sxs-lookup"><span data-stu-id="7613e-169">Example</span></span>  
 <span data-ttu-id="7613e-170">Aşağıdaki örnek sınıfının tanımını böler `sampleClass` iki bildirimleri her biri farklı bir tanımlar `Sub` yordamı.</span><span class="sxs-lookup"><span data-stu-id="7613e-170">The following example splits the definition of class `sampleClass` into two declarations, each of which defines a different `Sub` procedure.</span></span>  
  
 [!code-vb[VbVbalrKeywords#3](../../../visual-basic/language-reference/codesnippet/VisualBasic/partial_1.vb)]  
  
 <span data-ttu-id="7613e-171">Önceki örnekte iki kısmi tanımları, aynı kaynak dosyasında veya iki farklı kaynak dosyalar olabilir.</span><span class="sxs-lookup"><span data-stu-id="7613e-171">The two partial definitions in the preceding example could be in the same source file or in two different source files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7613e-172">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7613e-172">See Also</span></span>  
 [<span data-ttu-id="7613e-173">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="7613e-173">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
 [<span data-ttu-id="7613e-174">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="7613e-174">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="7613e-175">Tür Yükseltme</span><span class="sxs-lookup"><span data-stu-id="7613e-175">Type Promotion</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)  
 [<span data-ttu-id="7613e-176">Shadows</span><span class="sxs-lookup"><span data-stu-id="7613e-176">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="7613e-177">Visual Basic'de genel türler</span><span class="sxs-lookup"><span data-stu-id="7613e-177">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="7613e-178">Kısmi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7613e-178">Partial Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
