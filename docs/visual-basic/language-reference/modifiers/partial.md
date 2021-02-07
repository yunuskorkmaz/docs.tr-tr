---
description: 'Hakkında daha fazla bilgi edinin: kısmi (Visual Basic)'
title: Kısmi
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
ms.openlocfilehash: bf2d8b06b83f4a90ec2f4edd52405b58695c26e2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701020"
---
# <a name="partial-visual-basic"></a><span data-ttu-id="c071a-103">Kısmi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c071a-103">Partial (Visual Basic)</span></span>

<span data-ttu-id="c071a-104">Tür bildiriminin türün kısmi bir tanımı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c071a-104">Indicates that a type declaration is a partial definition of the type.</span></span>  
  
 <span data-ttu-id="c071a-105">Anahtar sözcüğünü kullanarak, bir türün tanımını birkaç bildirim arasında bölebilirsiniz `Partial` .</span><span class="sxs-lookup"><span data-stu-id="c071a-105">You can divide the definition of a type among several declarations by using the `Partial` keyword.</span></span> <span data-ttu-id="c071a-106">İstediğiniz kadar çok sayıda kısmi bildirim, istediğiniz kadar farklı kaynak dosyasında kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c071a-106">You can use as many partial declarations as you want, in as many different source files as you want.</span></span> <span data-ttu-id="c071a-107">Ancak, tüm bildirimlerin aynı derlemede ve aynı ad alanında olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c071a-107">However, all the declarations must be in the same assembly and the same namespace.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c071a-108">Visual Basic, genellikle kısmi sınıflarda uygulanan *Kısmi yöntemleri* destekler.</span><span class="sxs-lookup"><span data-stu-id="c071a-108">Visual Basic supports *partial methods*, which are typically implemented in partial classes.</span></span> <span data-ttu-id="c071a-109">Daha fazla bilgi için bkz. [kısmi Yöntemler](../../programming-guide/language-features/procedures/partial-methods.md) ve [Sub deyimleri](../statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c071a-109">For more information, see [Partial Methods](../../programming-guide/language-features/procedures/partial-methods.md) and [Sub Statement](../statements/sub-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c071a-110">Syntax</span><span class="sxs-lookup"><span data-stu-id="c071a-110">Syntax</span></span>  
  
```vb  
[ <attrlist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] _  
Partial { Class | Structure | Interface | Module } name [ (Of typelist) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ variabledeclarations ]  
    [ proceduredeclarations ]  
{ End Class | End Structure }  
```  
  
## <a name="parts"></a><span data-ttu-id="c071a-111">Bölümler</span><span class="sxs-lookup"><span data-stu-id="c071a-111">Parts</span></span>  
  
|<span data-ttu-id="c071a-112">Süre</span><span class="sxs-lookup"><span data-stu-id="c071a-112">Term</span></span>|<span data-ttu-id="c071a-113">Tanım</span><span class="sxs-lookup"><span data-stu-id="c071a-113">Definition</span></span>|  
|---|---|  
|`attrlist`|<span data-ttu-id="c071a-114">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c071a-114">Optional.</span></span> <span data-ttu-id="c071a-115">Bu tür için uygulanan özniteliklerin listesi.</span><span class="sxs-lookup"><span data-stu-id="c071a-115">List of attributes that apply to this type.</span></span> <span data-ttu-id="c071a-116">[Öznitelik listesini](../statements/attribute-list.md) açılı ayraç () içine almalısınız `< >` .</span><span class="sxs-lookup"><span data-stu-id="c071a-116">You must enclose the [Attribute List](../statements/attribute-list.md) in angle brackets (`< >`).</span></span>|  
|`accessmodifier`|<span data-ttu-id="c071a-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c071a-117">Optional.</span></span> <span data-ttu-id="c071a-118">Hangi kodun bu türe erişebileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c071a-118">Specifies what code can access this type.</span></span> <span data-ttu-id="c071a-119">[Visual Basic erişim düzeylerine](../../programming-guide/language-features/declared-elements/access-levels.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="c071a-119">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`Shadows`|<span data-ttu-id="c071a-120">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c071a-120">Optional.</span></span> <span data-ttu-id="c071a-121">Bkz. [gölgeler](shadows.md).</span><span class="sxs-lookup"><span data-stu-id="c071a-121">See [Shadows](shadows.md).</span></span>|  
|`MustInherit`|<span data-ttu-id="c071a-122">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c071a-122">Optional.</span></span> <span data-ttu-id="c071a-123">Bkz. [MustInherit](mustinherit.md).</span><span class="sxs-lookup"><span data-stu-id="c071a-123">See [MustInherit](mustinherit.md).</span></span>|  
|`NotInheritable`|<span data-ttu-id="c071a-124">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c071a-124">Optional.</span></span> <span data-ttu-id="c071a-125">[NotInheritable](notinheritable.md)öğesine bakın.</span><span class="sxs-lookup"><span data-stu-id="c071a-125">See [NotInheritable](notinheritable.md).</span></span>|  
|`name`|<span data-ttu-id="c071a-126">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c071a-126">Required.</span></span> <span data-ttu-id="c071a-127">Bu türün adı.</span><span class="sxs-lookup"><span data-stu-id="c071a-127">Name of this type.</span></span> <span data-ttu-id="c071a-128">Aynı türdeki tüm diğer kısmi bildirimlerde tanımlanan adla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="c071a-128">Must match the name defined in all other partial declarations of the same type.</span></span>|  
|`Of`|<span data-ttu-id="c071a-129">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c071a-129">Optional.</span></span> <span data-ttu-id="c071a-130">Bunun genel bir tür olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="c071a-130">Specifies that this is a generic type.</span></span> <span data-ttu-id="c071a-131">Bkz. [Visual Basic genel türler](../../programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="c071a-131">See [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md).</span></span>|  
|`typelist`|<span data-ttu-id="c071a-132">[Kullanıyorsanız gereklidir.](../statements/of-clause.md)</span><span class="sxs-lookup"><span data-stu-id="c071a-132">Required if you use [Of](../statements/of-clause.md).</span></span> <span data-ttu-id="c071a-133">Bkz. [tür listesi](../statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="c071a-133">See [Type List](../statements/type-list.md).</span></span>|  
|`Inherits`|<span data-ttu-id="c071a-134">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c071a-134">Optional.</span></span> <span data-ttu-id="c071a-135">Bkz. [Inherits açıklaması](../statements/inherits-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c071a-135">See [Inherits Statement](../statements/inherits-statement.md).</span></span>|  
|`classname`|<span data-ttu-id="c071a-136">Kullanıyorsanız gereklidir `Inherits` .</span><span class="sxs-lookup"><span data-stu-id="c071a-136">Required if you use `Inherits`.</span></span> <span data-ttu-id="c071a-137">Bu sınıfın türetildiği sınıfın veya arabirimin adı.</span><span class="sxs-lookup"><span data-stu-id="c071a-137">The name of the class or interface from which this class derives.</span></span>|  
|`Implements`|<span data-ttu-id="c071a-138">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c071a-138">Optional.</span></span> <span data-ttu-id="c071a-139">Bkz. [Implements açıklaması](../statements/implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c071a-139">See [Implements Statement](../statements/implements-statement.md).</span></span>|  
|`interfacenames`|<span data-ttu-id="c071a-140">Kullanıyorsanız gereklidir `Implements` .</span><span class="sxs-lookup"><span data-stu-id="c071a-140">Required if you use `Implements`.</span></span> <span data-ttu-id="c071a-141">Bu türün uyguladığı arabirimlerin adları.</span><span class="sxs-lookup"><span data-stu-id="c071a-141">The names of the interfaces this type implements.</span></span>|  
|`variabledeclarations`|<span data-ttu-id="c071a-142">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c071a-142">Optional.</span></span> <span data-ttu-id="c071a-143">Türün ek değişkenlerini ve olaylarını bildiren deyimler.</span><span class="sxs-lookup"><span data-stu-id="c071a-143">Statements which declare additional variables and events for the type.</span></span>|  
|`proceduredeclarations`|<span data-ttu-id="c071a-144">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c071a-144">Optional.</span></span> <span data-ttu-id="c071a-145">Tür için ek yordamlar bildiren ve tanımlayan deyimler.</span><span class="sxs-lookup"><span data-stu-id="c071a-145">Statements which declare and define additional procedures for the type.</span></span>|  
|<span data-ttu-id="c071a-146">`End Class` veya `End Structure`</span><span class="sxs-lookup"><span data-stu-id="c071a-146">`End Class` or `End Structure`</span></span>|<span data-ttu-id="c071a-147">Bu kısmı `Class` veya `Structure` tanımı sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="c071a-147">Ends this partial `Class` or `Structure` definition.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c071a-148">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c071a-148">Remarks</span></span>  

 <span data-ttu-id="c071a-149">Visual Basic, oluşturulan kodu ayrı kaynak dosyalardaki Kullanıcı tarafından yazılan koddan ayırmak için kısmi sınıf tanımları kullanır.</span><span class="sxs-lookup"><span data-stu-id="c071a-149">Visual Basic uses partial-class definitions to separate generated code from user-authored code in separate source files.</span></span> <span data-ttu-id="c071a-150">Örneğin, **Windows Form Tasarımcısı** gibi denetimler için kısmi sınıfları tanımlar <xref:System.Windows.Forms.Form> .</span><span class="sxs-lookup"><span data-stu-id="c071a-150">For example, the **Windows Form Designer** defines partial classes for controls such as <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="c071a-151">Bu denetimlerde oluşturulan kodu değiştirmemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="c071a-151">You should not modify the generated code in these controls.</span></span>  
  
 <span data-ttu-id="c071a-152">Değiştirici kullanımı ve devralmayla ilgili olanlar gibi sınıf, yapı, arabirim ve modül oluşturma kuralları kısmi bir tür oluştururken geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c071a-152">All the rules for class, structure, interface, and module creation, such as those for modifier usage and inheritance, apply when creating a partial type.</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="c071a-153">En İyi Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="c071a-153">Best Practices</span></span>  
  
- <span data-ttu-id="c071a-154">Normal koşullarda, tek bir türün geliştirilmesini iki veya daha fazla bildirim arasında bölmemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="c071a-154">Under normal circumstances, you should not split the development of a single type across two or more declarations.</span></span> <span data-ttu-id="c071a-155">Bu nedenle, çoğu durumda `Partial` anahtar sözcüğe gerek kalmaz.</span><span class="sxs-lookup"><span data-stu-id="c071a-155">Therefore, in most cases you do not need the `Partial` keyword.</span></span>  
  
- <span data-ttu-id="c071a-156">Okunabilirlik için, bir türün her kısmi bildirimi `Partial` anahtar sözcüğünü içermelidir.</span><span class="sxs-lookup"><span data-stu-id="c071a-156">For readability, every partial declaration of a type should include the `Partial` keyword.</span></span> <span data-ttu-id="c071a-157">Derleyici en çok bir kısmi bildirimin anahtar sözcüğünü atmasını sağlar; iki veya daha fazla atlarsanız, derleyici bir hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="c071a-157">The compiler allows at most one partial declaration to omit the keyword; if two or more omit it the compiler signals an error.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="c071a-158">Davranış</span><span class="sxs-lookup"><span data-stu-id="c071a-158">Behavior</span></span>  
  
- <span data-ttu-id="c071a-159">**Bildirimlerin birleşimi.**</span><span class="sxs-lookup"><span data-stu-id="c071a-159">**Union of Declarations.**</span></span> <span data-ttu-id="c071a-160">Derleyici, türü tüm kısmi bildirimlerinin birleşimi olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="c071a-160">The compiler treats the type as the union of all its partial declarations.</span></span> <span data-ttu-id="c071a-161">Her kısmi tanımdaki her değiştirici tüm tür için geçerlidir ve her kısmi tanımdan her üye tüm tür için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c071a-161">Every modifier from every partial definition applies to the entire type, and every member from every partial definition is available to the entire type.</span></span>  
  
- <span data-ttu-id="c071a-162">**Modüllerde kısmi türler Için tür yükseltmeye Izin verilmiyor.**</span><span class="sxs-lookup"><span data-stu-id="c071a-162">**Type Promotion Not Allowed For Partial Types in Modules.**</span></span> <span data-ttu-id="c071a-163">Kısmi Tanım bir modülün içindeyse, bu türden yükseltme otomatik olarak doldurulur.</span><span class="sxs-lookup"><span data-stu-id="c071a-163">If a partial definition is inside a module, type promotion of that type is automatically defeated.</span></span> <span data-ttu-id="c071a-164">Böyle bir durumda, kısmi tanımlar kümesi beklenmedik sonuçlara ve hatta derleyici hatalarına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="c071a-164">In such a case, a set of partial definitions can cause unexpected results and even compiler errors.</span></span> <span data-ttu-id="c071a-165">Daha fazla bilgi için bkz. [yükseltme türü](../../programming-guide/language-features/declared-elements/type-promotion.md).</span><span class="sxs-lookup"><span data-stu-id="c071a-165">For more information, see [Type Promotion](../../programming-guide/language-features/declared-elements/type-promotion.md).</span></span>  
  
     <span data-ttu-id="c071a-166">Derleyici, kısmi tanımları yalnızca kendi tam yolları özdeş olduğunda birleştirir.</span><span class="sxs-lookup"><span data-stu-id="c071a-166">The compiler merges partial definitions only when their fully qualified paths are identical.</span></span>  
  
 <span data-ttu-id="c071a-167">`Partial`Anahtar sözcüğü şu bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="c071a-167">The `Partial` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="c071a-168">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="c071a-168">Class Statement</span></span>](../statements/class-statement.md)  
  
 [<span data-ttu-id="c071a-169">Structure Yapısı</span><span class="sxs-lookup"><span data-stu-id="c071a-169">Structure Statement</span></span>](../statements/structure-statement.md)  
  
## <a name="example"></a><span data-ttu-id="c071a-170">Örnek</span><span class="sxs-lookup"><span data-stu-id="c071a-170">Example</span></span>  

 <span data-ttu-id="c071a-171">Aşağıdaki örnek, sınıfının tanımını `sampleClass` , her biri farklı bir yordam tanımlayan iki bildirime ayırır `Sub` .</span><span class="sxs-lookup"><span data-stu-id="c071a-171">The following example splits the definition of class `sampleClass` into two declarations, each of which defines a different `Sub` procedure.</span></span>  
  
 [!code-vb[VbVbalrKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#3)]  
  
 <span data-ttu-id="c071a-172">Yukarıdaki örnekteki iki kısmi tanım aynı kaynak dosyasında veya iki farklı kaynak dosyada olabilir.</span><span class="sxs-lookup"><span data-stu-id="c071a-172">The two partial definitions in the preceding example could be in the same source file or in two different source files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c071a-173">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c071a-173">See also</span></span>

- [<span data-ttu-id="c071a-174">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="c071a-174">Class Statement</span></span>](../statements/class-statement.md)
- [<span data-ttu-id="c071a-175">Structure Yapısı</span><span class="sxs-lookup"><span data-stu-id="c071a-175">Structure Statement</span></span>](../statements/structure-statement.md)
- [<span data-ttu-id="c071a-176">Tür Yükseltme</span><span class="sxs-lookup"><span data-stu-id="c071a-176">Type Promotion</span></span>](../../programming-guide/language-features/declared-elements/type-promotion.md)
- [<span data-ttu-id="c071a-177">Shadows</span><span class="sxs-lookup"><span data-stu-id="c071a-177">Shadows</span></span>](shadows.md)
- [<span data-ttu-id="c071a-178">Visual Basic genel türler</span><span class="sxs-lookup"><span data-stu-id="c071a-178">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="c071a-179">Kısmi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c071a-179">Partial Methods</span></span>](../../programming-guide/language-features/procedures/partial-methods.md)
