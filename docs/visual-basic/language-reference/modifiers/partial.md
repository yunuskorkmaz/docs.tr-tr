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
ms.openlocfilehash: dd7550b8b1e164c55bd97828d395b43a60c87cfb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929944"
---
# <a name="partial-visual-basic"></a><span data-ttu-id="904bb-102">Kısmi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="904bb-102">Partial (Visual Basic)</span></span>
<span data-ttu-id="904bb-103">Tür bildiriminin türün kısmi bir tanımı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="904bb-103">Indicates that a type declaration is a partial definition of the type.</span></span>  
  
 <span data-ttu-id="904bb-104">`Partial` Anahtar sözcüğünü kullanarak, bir türün tanımını birkaç bildirim arasında bölebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="904bb-104">You can divide the definition of a type among several declarations by using the `Partial` keyword.</span></span> <span data-ttu-id="904bb-105">İstediğiniz kadar çok sayıda kısmi bildirim, istediğiniz kadar farklı kaynak dosyasında kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="904bb-105">You can use as many partial declarations as you want, in as many different source files as you want.</span></span> <span data-ttu-id="904bb-106">Ancak, tüm bildirimlerin aynı derlemede ve aynı ad alanında olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="904bb-106">However, all the declarations must be in the same assembly and the same namespace.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="904bb-107">Visual Basic, genellikle kısmi sınıflarda uygulanan *Kısmi yöntemleri*destekler.</span><span class="sxs-lookup"><span data-stu-id="904bb-107">Visual Basic supports *partial methods*, which are typically implemented in partial classes.</span></span> <span data-ttu-id="904bb-108">Daha fazla bilgi için bkz. [kısmi Yöntemler](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) ve [Sub deyimleri](../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="904bb-108">For more information, see [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) and [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="904bb-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="904bb-109">Syntax</span></span>  
  
```  
[ <attrlist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] _  
Partial { Class | Structure | Interface | Module } name [ (Of typelist) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ variabledeclarations ]  
    [ proceduredeclarations ]  
{ End Class | End Structure }  
```  
  
## <a name="parts"></a><span data-ttu-id="904bb-110">Bölümler</span><span class="sxs-lookup"><span data-stu-id="904bb-110">Parts</span></span>  
  
|<span data-ttu-id="904bb-111">Terim</span><span class="sxs-lookup"><span data-stu-id="904bb-111">Term</span></span>|<span data-ttu-id="904bb-112">Tanım</span><span class="sxs-lookup"><span data-stu-id="904bb-112">Definition</span></span>|  
|---|---|  
|`attrlist`|<span data-ttu-id="904bb-113">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="904bb-113">Optional.</span></span> <span data-ttu-id="904bb-114">Bu tür için uygulanan özniteliklerin listesi.</span><span class="sxs-lookup"><span data-stu-id="904bb-114">List of attributes that apply to this type.</span></span> <span data-ttu-id="904bb-115">[Öznitelik listesini](../../../visual-basic/language-reference/statements/attribute-list.md) açılı ayraç (`< >`) içine almalısınız.</span><span class="sxs-lookup"><span data-stu-id="904bb-115">You must enclose the [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets (`< >`).</span></span>|  
|`accessmodifier`|<span data-ttu-id="904bb-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="904bb-116">Optional.</span></span> <span data-ttu-id="904bb-117">Hangi kodun bu türe erişebileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="904bb-117">Specifies what code can access this type.</span></span> <span data-ttu-id="904bb-118">[Visual Basic erişim düzeylerine](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="904bb-118">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`Shadows`|<span data-ttu-id="904bb-119">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="904bb-119">Optional.</span></span> <span data-ttu-id="904bb-120">Bkz. [gölgeler](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="904bb-120">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>|  
|`MustInherit`|<span data-ttu-id="904bb-121">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="904bb-121">Optional.</span></span> <span data-ttu-id="904bb-122">Bkz. [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span><span class="sxs-lookup"><span data-stu-id="904bb-122">See [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span></span>|  
|`NotInheritable`|<span data-ttu-id="904bb-123">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="904bb-123">Optional.</span></span> <span data-ttu-id="904bb-124">[NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)öğesine bakın.</span><span class="sxs-lookup"><span data-stu-id="904bb-124">See [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).</span></span>|  
|`name`|<span data-ttu-id="904bb-125">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="904bb-125">Required.</span></span> <span data-ttu-id="904bb-126">Bu türün adı.</span><span class="sxs-lookup"><span data-stu-id="904bb-126">Name of this type.</span></span> <span data-ttu-id="904bb-127">Aynı türdeki tüm diğer kısmi bildirimlerde tanımlanan adla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="904bb-127">Must match the name defined in all other partial declarations of the same type.</span></span>|  
|`Of`|<span data-ttu-id="904bb-128">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="904bb-128">Optional.</span></span> <span data-ttu-id="904bb-129">Bunun genel bir tür olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="904bb-129">Specifies that this is a generic type.</span></span> <span data-ttu-id="904bb-130">Bkz. [Visual Basic genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="904bb-130">See [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span>|  
|`typelist`|<span data-ttu-id="904bb-131">Kullanıyorsanız gereklidir. [](../../../visual-basic/language-reference/statements/of-clause.md)</span><span class="sxs-lookup"><span data-stu-id="904bb-131">Required if you use [Of](../../../visual-basic/language-reference/statements/of-clause.md).</span></span> <span data-ttu-id="904bb-132">Bkz. [tür listesi](../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="904bb-132">See [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>|  
|`Inherits`|<span data-ttu-id="904bb-133">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="904bb-133">Optional.</span></span> <span data-ttu-id="904bb-134">Bkz. [Inherits açıklaması](../../../visual-basic/language-reference/statements/inherits-statement.md).</span><span class="sxs-lookup"><span data-stu-id="904bb-134">See [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md).</span></span>|  
|`classname`|<span data-ttu-id="904bb-135">Kullanıyorsanız gereklidir `Inherits`.</span><span class="sxs-lookup"><span data-stu-id="904bb-135">Required if you use `Inherits`.</span></span> <span data-ttu-id="904bb-136">Bu sınıfın türetildiği sınıfın veya arabirimin adı.</span><span class="sxs-lookup"><span data-stu-id="904bb-136">The name of the class or interface from which this class derives.</span></span>|  
|`Implements`|<span data-ttu-id="904bb-137">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="904bb-137">Optional.</span></span> <span data-ttu-id="904bb-138">Bkz. [Implements açıklaması](../../../visual-basic/language-reference/statements/implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="904bb-138">See [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span>|  
|`interfacenames`|<span data-ttu-id="904bb-139">Kullanıyorsanız gereklidir `Implements`.</span><span class="sxs-lookup"><span data-stu-id="904bb-139">Required if you use `Implements`.</span></span> <span data-ttu-id="904bb-140">Bu türün uyguladığı arabirimlerin adları.</span><span class="sxs-lookup"><span data-stu-id="904bb-140">The names of the interfaces this type implements.</span></span>|  
|`variabledeclarations`|<span data-ttu-id="904bb-141">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="904bb-141">Optional.</span></span> <span data-ttu-id="904bb-142">Türün ek değişkenlerini ve olaylarını bildiren deyimler.</span><span class="sxs-lookup"><span data-stu-id="904bb-142">Statements which declare additional variables and events for the type.</span></span>|  
|`proceduredeclarations`|<span data-ttu-id="904bb-143">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="904bb-143">Optional.</span></span> <span data-ttu-id="904bb-144">Tür için ek yordamlar bildiren ve tanımlayan deyimler.</span><span class="sxs-lookup"><span data-stu-id="904bb-144">Statements which declare and define additional procedures for the type.</span></span>|  
|<span data-ttu-id="904bb-145">`End Class` veya `End Structure`</span><span class="sxs-lookup"><span data-stu-id="904bb-145">`End Class` or `End Structure`</span></span>|<span data-ttu-id="904bb-146">Bu kısmı `Class` veya `Structure` tanımı sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="904bb-146">Ends this partial `Class` or `Structure` definition.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="904bb-147">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="904bb-147">Remarks</span></span>  
 <span data-ttu-id="904bb-148">Visual Basic, oluşturulan kodu ayrı kaynak dosyalardaki Kullanıcı tarafından yazılan koddan ayırmak için kısmi sınıf tanımları kullanır.</span><span class="sxs-lookup"><span data-stu-id="904bb-148">Visual Basic uses partial-class definitions to separate generated code from user-authored code in separate source files.</span></span> <span data-ttu-id="904bb-149">Örneğin, **Windows Form Tasarımcısı** gibi <xref:System.Windows.Forms.Form>denetimler için kısmi sınıfları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="904bb-149">For example, the **Windows Form Designer** defines partial classes for controls such as <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="904bb-150">Bu denetimlerde oluşturulan kodu değiştirmemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="904bb-150">You should not modify the generated code in these controls.</span></span>  
  
 <span data-ttu-id="904bb-151">Değiştirici kullanımı ve devralmayla ilgili olanlar gibi sınıf, yapı, arabirim ve modül oluşturma kuralları kısmi bir tür oluştururken geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="904bb-151">All the rules for class, structure, interface, and module creation, such as those for modifier usage and inheritance, apply when creating a partial type.</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="904bb-152">En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="904bb-152">Best Practices</span></span>  
  
- <span data-ttu-id="904bb-153">Normal koşullarda, tek bir türün geliştirilmesini iki veya daha fazla bildirim arasında bölmemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="904bb-153">Under normal circumstances, you should not split the development of a single type across two or more declarations.</span></span> <span data-ttu-id="904bb-154">Bu nedenle, çoğu durumda `Partial` anahtar sözcüğe gerek kalmaz.</span><span class="sxs-lookup"><span data-stu-id="904bb-154">Therefore, in most cases you do not need the `Partial` keyword.</span></span>  
  
- <span data-ttu-id="904bb-155">Okunabilirlik için, bir türün her kısmi bildirimi `Partial` anahtar sözcüğünü içermelidir.</span><span class="sxs-lookup"><span data-stu-id="904bb-155">For readability, every partial declaration of a type should include the `Partial` keyword.</span></span> <span data-ttu-id="904bb-156">Derleyici en çok bir kısmi bildirimin anahtar sözcüğünü atmasını sağlar; iki veya daha fazla atlarsanız, derleyici bir hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="904bb-156">The compiler allows at most one partial declaration to omit the keyword; if two or more omit it the compiler signals an error.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="904bb-157">Davranış</span><span class="sxs-lookup"><span data-stu-id="904bb-157">Behavior</span></span>  
  
- <span data-ttu-id="904bb-158">**Bildirimlerin birleşimi.**</span><span class="sxs-lookup"><span data-stu-id="904bb-158">**Union of Declarations.**</span></span> <span data-ttu-id="904bb-159">Derleyici, türü tüm kısmi bildirimlerinin birleşimi olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="904bb-159">The compiler treats the type as the union of all its partial declarations.</span></span> <span data-ttu-id="904bb-160">Her kısmi tanımdaki her değiştirici tüm tür için geçerlidir ve her kısmi tanımdan her üye tüm tür için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="904bb-160">Every modifier from every partial definition applies to the entire type, and every member from every partial definition is available to the entire type.</span></span>  
  
- <span data-ttu-id="904bb-161">**Modüllerde kısmi türler Için tür yükseltmeye Izin verilmiyor.**</span><span class="sxs-lookup"><span data-stu-id="904bb-161">**Type Promotion Not Allowed For Partial Types in Modules.**</span></span> <span data-ttu-id="904bb-162">Kısmi Tanım bir modülün içindeyse, bu türden yükseltme otomatik olarak doldurulur.</span><span class="sxs-lookup"><span data-stu-id="904bb-162">If a partial definition is inside a module, type promotion of that type is automatically defeated.</span></span> <span data-ttu-id="904bb-163">Böyle bir durumda, kısmi tanımlar kümesi beklenmedik sonuçlara ve hatta derleyici hatalarına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="904bb-163">In such a case, a set of partial definitions can cause unexpected results and even compiler errors.</span></span> <span data-ttu-id="904bb-164">Daha fazla bilgi için bkz. [yükseltme türü](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span><span class="sxs-lookup"><span data-stu-id="904bb-164">For more information, see [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span></span>  
  
     <span data-ttu-id="904bb-165">Derleyici, kısmi tanımları yalnızca kendi tam yolları özdeş olduğunda birleştirir.</span><span class="sxs-lookup"><span data-stu-id="904bb-165">The compiler merges partial definitions only when their fully qualified paths are identical.</span></span>  
  
 <span data-ttu-id="904bb-166">`Partial` Anahtar sözcüğü şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="904bb-166">The `Partial` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="904bb-167">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="904bb-167">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="904bb-168">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="904bb-168">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
## <a name="example"></a><span data-ttu-id="904bb-169">Örnek</span><span class="sxs-lookup"><span data-stu-id="904bb-169">Example</span></span>  
 <span data-ttu-id="904bb-170">Aşağıdaki örnek, sınıfının `sampleClass` tanımını, her biri farklı `Sub` bir yordam tanımlayan iki bildirime ayırır.</span><span class="sxs-lookup"><span data-stu-id="904bb-170">The following example splits the definition of class `sampleClass` into two declarations, each of which defines a different `Sub` procedure.</span></span>  
  
 [!code-vb[VbVbalrKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#3)]  
  
 <span data-ttu-id="904bb-171">Yukarıdaki örnekteki iki kısmi tanım aynı kaynak dosyasında veya iki farklı kaynak dosyada olabilir.</span><span class="sxs-lookup"><span data-stu-id="904bb-171">The two partial definitions in the preceding example could be in the same source file or in two different source files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="904bb-172">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="904bb-172">See also</span></span>

- [<span data-ttu-id="904bb-173">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="904bb-173">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="904bb-174">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="904bb-174">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="904bb-175">Tür Yükseltme</span><span class="sxs-lookup"><span data-stu-id="904bb-175">Type Promotion</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
- [<span data-ttu-id="904bb-176">Shadows</span><span class="sxs-lookup"><span data-stu-id="904bb-176">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="904bb-177">Visual Basic genel türler</span><span class="sxs-lookup"><span data-stu-id="904bb-177">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="904bb-178">Kısmi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="904bb-178">Partial Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
