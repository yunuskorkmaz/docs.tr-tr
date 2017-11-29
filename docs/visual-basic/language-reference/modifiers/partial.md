---
title: "Kısmi (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "36"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5129ef7737b1b07317d47f8d18e9aceb668bf05a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="partial-visual-basic"></a><span data-ttu-id="fdc52-102">Kısmi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fdc52-102">Partial (Visual Basic)</span></span>
<span data-ttu-id="fdc52-103">Tür bildirimi kısmi tanım türü olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="fdc52-103">Indicates that a type declaration is a partial definition of the type.</span></span>  
  
 <span data-ttu-id="fdc52-104">Kullanarak birkaç bildirimler arasında bir tür tanımını bölebilirsiniz `Partial` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="fdc52-104">You can divide the definition of a type among several declarations by using the `Partial` keyword.</span></span> <span data-ttu-id="fdc52-105">İstediğiniz sayıda farklı kaynak dosyalar istediğiniz sayıda kısmi bildirimleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fdc52-105">You can use as many partial declarations as you want, in as many different source files as you want.</span></span> <span data-ttu-id="fdc52-106">Ancak, tüm bildirimler aynı bütünleştirilmiş kodda ve aynı ad olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fdc52-106">However, all the declarations must be in the same assembly and the same namespace.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fdc52-107">Visual Basic destekler *kısmi yöntemler*, hangi genellikle uygulanır kısmi sınıflar.</span><span class="sxs-lookup"><span data-stu-id="fdc52-107">Visual Basic supports *partial methods*, which are typically implemented in partial classes.</span></span> <span data-ttu-id="fdc52-108">Daha fazla bilgi için bkz: [kısmi yöntemler](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) ve [Sub deyimi](../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fdc52-108">For more information, see [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) and [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdc52-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fdc52-109">Syntax</span></span>  
  
```  
[ <attrlist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] _  
Partial { Class | Structure | Interface | Module } name [ (Of typelist) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ variabledeclarations ]  
    [ proceduredeclarations ]  
{ End Class | End Structure }  
```  
  
## <a name="parts"></a><span data-ttu-id="fdc52-110">Bölümler</span><span class="sxs-lookup"><span data-stu-id="fdc52-110">Parts</span></span>  
  
|<span data-ttu-id="fdc52-111">Terim</span><span class="sxs-lookup"><span data-stu-id="fdc52-111">Term</span></span>|<span data-ttu-id="fdc52-112">Tanım</span><span class="sxs-lookup"><span data-stu-id="fdc52-112">Definition</span></span>|  
|---|---|  
|`attrlist`|<span data-ttu-id="fdc52-113">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="fdc52-113">Optional.</span></span> <span data-ttu-id="fdc52-114">Bu türü için geçerli öznitelikler listesi.</span><span class="sxs-lookup"><span data-stu-id="fdc52-114">List of attributes that apply to this type.</span></span> <span data-ttu-id="fdc52-115">İçine almalısınız [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md) açılı ayraç (`< >`).</span><span class="sxs-lookup"><span data-stu-id="fdc52-115">You must enclose the [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets (`< >`).</span></span>|  
|`accessmodifier`|<span data-ttu-id="fdc52-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="fdc52-116">Optional.</span></span> <span data-ttu-id="fdc52-117">Bu tür hangi kod erişip belirtir.</span><span class="sxs-lookup"><span data-stu-id="fdc52-117">Specifies what code can access this type.</span></span> <span data-ttu-id="fdc52-118">Bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="fdc52-118">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`Shadows`|<span data-ttu-id="fdc52-119">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="fdc52-119">Optional.</span></span> <span data-ttu-id="fdc52-120">Bkz: [gölgeleri](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="fdc52-120">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>|  
|`MustInherit`|<span data-ttu-id="fdc52-121">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="fdc52-121">Optional.</span></span> <span data-ttu-id="fdc52-122">Bkz: [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span><span class="sxs-lookup"><span data-stu-id="fdc52-122">See [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span></span>|  
|`NotInheritable`|<span data-ttu-id="fdc52-123">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="fdc52-123">Optional.</span></span> <span data-ttu-id="fdc52-124">Bkz: [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).</span><span class="sxs-lookup"><span data-stu-id="fdc52-124">See [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).</span></span>|  
|`name`|<span data-ttu-id="fdc52-125">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="fdc52-125">Required.</span></span> <span data-ttu-id="fdc52-126">Bu tür adı.</span><span class="sxs-lookup"><span data-stu-id="fdc52-126">Name of this type.</span></span> <span data-ttu-id="fdc52-127">Tüm diğer kısmi bildirimlerinde aynı türde tanımlanan adıyla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="fdc52-127">Must match the name defined in all other partial declarations of the same type.</span></span>|  
|`Of`|<span data-ttu-id="fdc52-128">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="fdc52-128">Optional.</span></span> <span data-ttu-id="fdc52-129">Bu genel bir tür olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="fdc52-129">Specifies that this is a generic type.</span></span> <span data-ttu-id="fdc52-130">Bkz: [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="fdc52-130">See [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span>|  
|`typelist`|<span data-ttu-id="fdc52-131">Kullanırsanız, gerekli [,](../../../visual-basic/language-reference/statements/of-clause.md).</span><span class="sxs-lookup"><span data-stu-id="fdc52-131">Required if you use [Of](../../../visual-basic/language-reference/statements/of-clause.md).</span></span> <span data-ttu-id="fdc52-132">Bkz: [yazın listesi](../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="fdc52-132">See [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>|  
|`Inherits`|<span data-ttu-id="fdc52-133">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="fdc52-133">Optional.</span></span> <span data-ttu-id="fdc52-134">Bkz: [Inherits deyimi](../../../visual-basic/language-reference/statements/inherits-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fdc52-134">See [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md).</span></span>|  
|`classname`|<span data-ttu-id="fdc52-135">Kullanırsanız, gerekli `Inherits`.</span><span class="sxs-lookup"><span data-stu-id="fdc52-135">Required if you use `Inherits`.</span></span> <span data-ttu-id="fdc52-136">Sınıf veya bu sınıf türetilen arabirim adı.</span><span class="sxs-lookup"><span data-stu-id="fdc52-136">The name of the class or interface from which this class derives.</span></span>|  
|`Implements`|<span data-ttu-id="fdc52-137">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="fdc52-137">Optional.</span></span> <span data-ttu-id="fdc52-138">Bkz: [uygulayan deyimi](../../../visual-basic/language-reference/statements/implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fdc52-138">See [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span>|  
|`interfacenames`|<span data-ttu-id="fdc52-139">Kullanırsanız, gerekli `Implements`.</span><span class="sxs-lookup"><span data-stu-id="fdc52-139">Required if you use `Implements`.</span></span> <span data-ttu-id="fdc52-140">Bu tür uygulayan arabirimleri adları.</span><span class="sxs-lookup"><span data-stu-id="fdc52-140">The names of the interfaces this type implements.</span></span>|  
|`variabledeclarations`|<span data-ttu-id="fdc52-141">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="fdc52-141">Optional.</span></span> <span data-ttu-id="fdc52-142">Ek değişkenleri ve tür için olaylar declare deyimlerini.</span><span class="sxs-lookup"><span data-stu-id="fdc52-142">Statements which declare additional variables and events for the type.</span></span>|  
|`proceduredeclarations`|<span data-ttu-id="fdc52-143">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="fdc52-143">Optional.</span></span> <span data-ttu-id="fdc52-144">Bildirme ve türü için ek yordamlar tanımlama deyimleri.</span><span class="sxs-lookup"><span data-stu-id="fdc52-144">Statements which declare and define additional procedures for the type.</span></span>|  
|<span data-ttu-id="fdc52-145">`End Class`veya`End Structure`</span><span class="sxs-lookup"><span data-stu-id="fdc52-145">`End Class` or `End Structure`</span></span>|<span data-ttu-id="fdc52-146">Bu kısmi sona `Class` veya `Structure` tanımı.</span><span class="sxs-lookup"><span data-stu-id="fdc52-146">Ends this partial `Class` or `Structure` definition.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fdc52-147">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fdc52-147">Remarks</span></span>  
 <span data-ttu-id="fdc52-148">Visual Basic parçalı sınıf tanımları oluşturulan kod kullanıcı tarafından yazılan kodu ayrı kaynak dosyalarında ayırmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="fdc52-148">Visual Basic uses partial-class definitions to separate generated code from user-authored code in separate source files.</span></span> <span data-ttu-id="fdc52-149">Örneğin, **Windows Form Tasarımcısı** denetimleri için kısmi sınıflar gibi tanımlar <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="fdc52-149">For example, the **Windows Form Designer** defines partial classes for controls such as <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="fdc52-150">Bu denetimler oluşturulan kodda değiştirmemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fdc52-150">You should not modify the generated code in these controls.</span></span>  
  
 <span data-ttu-id="fdc52-151">Sınıfı, yapısı, arabirim ve değiştirici kullanım ve devralma için olanlar gibi modülü oluşturma için tüm kuralları kısmi türü oluştururken uygulayın.</span><span class="sxs-lookup"><span data-stu-id="fdc52-151">All the rules for class, structure, interface, and module creation, such as those for modifier usage and inheritance, apply when creating a partial type.</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="fdc52-152">En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="fdc52-152">Best Practices</span></span>  
  
-   <span data-ttu-id="fdc52-153">Normal koşullar altında tek bir türü geliştirme iki veya daha fazla bildirimler arasında bölmek değil.</span><span class="sxs-lookup"><span data-stu-id="fdc52-153">Under normal circumstances, you should not split the development of a single type across two or more declarations.</span></span> <span data-ttu-id="fdc52-154">Bu nedenle, çoğu durumda, gerekmeyen `Partial` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="fdc52-154">Therefore, in most cases you do not need the `Partial` keyword.</span></span>  
  
-   <span data-ttu-id="fdc52-155">Okunabilirlik için bir türün kısmi her bildirimi içermelidir `Partial` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="fdc52-155">For readability, every partial declaration of a type should include the `Partial` keyword.</span></span> <span data-ttu-id="fdc52-156">Derleyici anahtar sözcüğü atlamak en çok bir kısmi bildirimi sağlar; iki veya daha fazla atlarsanız, derleyici bir hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="fdc52-156">The compiler allows at most one partial declaration to omit the keyword; if two or more omit it the compiler signals an error.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="fdc52-157">Davranış</span><span class="sxs-lookup"><span data-stu-id="fdc52-157">Behavior</span></span>  
  
-   <span data-ttu-id="fdc52-158">**Bildirimleri birleşimi.**</span><span class="sxs-lookup"><span data-stu-id="fdc52-158">**Union of Declarations.**</span></span> <span data-ttu-id="fdc52-159">Derleyici türü tüm kısmi bildirimlerinde birleşimi değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="fdc52-159">The compiler treats the type as the union of all its partial declarations.</span></span> <span data-ttu-id="fdc52-160">Her değiştiricisi her kısmi tanımından tüm türü için geçerlidir ve her kısmi tanımından her bir üyenin tüm türü kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fdc52-160">Every modifier from every partial definition applies to the entire type, and every member from every partial definition is available to the entire type.</span></span>  
  
-   <span data-ttu-id="fdc52-161">**Tür promosyonu modüllerinde kısmi türleri için izin verilmiyor.**</span><span class="sxs-lookup"><span data-stu-id="fdc52-161">**Type Promotion Not Allowed For Partial Types in Modules.**</span></span> <span data-ttu-id="fdc52-162">Kısmi bir tanımı içinde bir modül türü tür yükseltme otomatik olarak engellenmediğinden ise.</span><span class="sxs-lookup"><span data-stu-id="fdc52-162">If a partial definition is inside a module, type promotion of that type is automatically defeated.</span></span> <span data-ttu-id="fdc52-163">Böyle bir durumda, kısmi tanımları kümesini beklenmeyen sonuçlara ve hatta derleyici hataları neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="fdc52-163">In such a case, a set of partial definitions can cause unexpected results and even compiler errors.</span></span> <span data-ttu-id="fdc52-164">Daha fazla bilgi için bkz: [tür yükseltme](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span><span class="sxs-lookup"><span data-stu-id="fdc52-164">For more information, see [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span></span>  
  
     <span data-ttu-id="fdc52-165">Yalnızca tam yollarına aynı zaman derleyici kısmi tanımları birleştirir.</span><span class="sxs-lookup"><span data-stu-id="fdc52-165">The compiler merges partial definitions only when their fully qualified paths are identical.</span></span>  
  
 <span data-ttu-id="fdc52-166">`Partial` Anahtar sözcüğü bu bağlamlarında kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="fdc52-166">The `Partial` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="fdc52-167">Class deyimi</span><span class="sxs-lookup"><span data-stu-id="fdc52-167">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="fdc52-168">Structure deyimi</span><span class="sxs-lookup"><span data-stu-id="fdc52-168">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
## <a name="example"></a><span data-ttu-id="fdc52-169">Örnek</span><span class="sxs-lookup"><span data-stu-id="fdc52-169">Example</span></span>  
 <span data-ttu-id="fdc52-170">Aşağıdaki örnek sınıfının tanımını böler `sampleClass` iki bildirimleri her biri farklı bir tanımlar `Sub` yordamı.</span><span class="sxs-lookup"><span data-stu-id="fdc52-170">The following example splits the definition of class `sampleClass` into two declarations, each of which defines a different `Sub` procedure.</span></span>  
  
 [!code-vb[VbVbalrKeywords#3](../../../visual-basic/language-reference/codesnippet/VisualBasic/partial_1.vb)]  
  
 <span data-ttu-id="fdc52-171">Önceki örnekte iki kısmi tanımları, aynı kaynak dosyasında veya iki farklı kaynak dosyalar olabilir.</span><span class="sxs-lookup"><span data-stu-id="fdc52-171">The two partial definitions in the preceding example could be in the same source file or in two different source files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdc52-172">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fdc52-172">See Also</span></span>  
 [<span data-ttu-id="fdc52-173">Class deyimi</span><span class="sxs-lookup"><span data-stu-id="fdc52-173">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
 [<span data-ttu-id="fdc52-174">Structure deyimi</span><span class="sxs-lookup"><span data-stu-id="fdc52-174">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="fdc52-175">Tür promosyonu</span><span class="sxs-lookup"><span data-stu-id="fdc52-175">Type Promotion</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)  
 [<span data-ttu-id="fdc52-176">Gölgeleri</span><span class="sxs-lookup"><span data-stu-id="fdc52-176">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="fdc52-177">Visual Basic'de genel türler</span><span class="sxs-lookup"><span data-stu-id="fdc52-177">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="fdc52-178">Kısmi yöntemler</span><span class="sxs-lookup"><span data-stu-id="fdc52-178">Partial Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
