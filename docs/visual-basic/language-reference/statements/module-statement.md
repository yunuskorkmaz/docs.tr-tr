---
title: Module ekstresi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Module
- vb.Module
helpviewer_keywords:
- modules, classes
- modules
- Module statement [Visual Basic]
- modules, declaring
- standard modules
- classes [Visual Basic], vs. modules
- declarations [Visual Basic], modules
ms.assetid: a1243afc-14a5-45df-95d5-51118aeac362
ms.openlocfilehash: 9b1aae08d0009a9fd23d6441207f1601ffec2568
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583102"
---
# <a name="module-statement"></a><span data-ttu-id="3c35f-102">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="3c35f-102">Module Statement</span></span>

<span data-ttu-id="3c35f-103">Modülün adını bildirir ve modülün içerdiği değişkenlerin, özelliklerin, olayların ve yordamların tanımını tanıtır.</span><span class="sxs-lookup"><span data-stu-id="3c35f-103">Declares the name of a module and introduces the definition of the variables, properties, events, and procedures that the module comprises.</span></span>

## <a name="syntax"></a><span data-ttu-id="3c35f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3c35f-104">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ]  Module name
    [ statements ]
End Module
```

## <a name="parts"></a><span data-ttu-id="3c35f-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="3c35f-105">Parts</span></span>

`attributelist`  
<span data-ttu-id="3c35f-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3c35f-106">Optional.</span></span> <span data-ttu-id="3c35f-107">Bkz. [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="3c35f-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>

`accessmodifier`  
<span data-ttu-id="3c35f-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3c35f-108">Optional.</span></span> <span data-ttu-id="3c35f-109">Aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="3c35f-109">Can be one of the following:</span></span>

- [<span data-ttu-id="3c35f-110">Public</span><span class="sxs-lookup"><span data-stu-id="3c35f-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)

- [<span data-ttu-id="3c35f-111">Friend</span><span class="sxs-lookup"><span data-stu-id="3c35f-111">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)

<span data-ttu-id="3c35f-112">[Visual Basic erişim düzeylerine](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="3c35f-112">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

`name`  
<span data-ttu-id="3c35f-113">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="3c35f-113">Required.</span></span> <span data-ttu-id="3c35f-114">Bu modülün adı.</span><span class="sxs-lookup"><span data-stu-id="3c35f-114">Name of this module.</span></span> <span data-ttu-id="3c35f-115">Bkz. [tanımlanmış öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="3c35f-115">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

`statements`  
<span data-ttu-id="3c35f-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3c35f-116">Optional.</span></span> <span data-ttu-id="3c35f-117">Değişkenleri, özellikleri, olayları, yordamları ve bu modülün iç içe geçmiş türlerini tanımlayan deyimler.</span><span class="sxs-lookup"><span data-stu-id="3c35f-117">Statements which define the variables, properties, events, procedures, and nested types of this module.</span></span>

`End Module`  
<span data-ttu-id="3c35f-118">@No__t_0 tanımını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="3c35f-118">Terminates the `Module` definition.</span></span>

## <a name="remarks"></a><span data-ttu-id="3c35f-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3c35f-119">Remarks</span></span>

<span data-ttu-id="3c35f-120">@No__t_0 bir ifade, ad alanı genelinde kullanılabilir bir başvuru türü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3c35f-120">A `Module` statement defines a reference type available throughout its namespace.</span></span> <span data-ttu-id="3c35f-121">*Modül* (bazen *Standart Modül*olarak adlandırılır), bir sınıfa benzer ancak bazı önemli ayrımlarla benzerdir.</span><span class="sxs-lookup"><span data-stu-id="3c35f-121">A *module* (sometimes called a *standard module*) is similar to a class but with some important distinctions.</span></span> <span data-ttu-id="3c35f-122">Her modülün tam olarak bir örneği vardır ve oluşturulması veya bir değişkene atanması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="3c35f-122">Every module has exactly one instance and does not need to be created or assigned to a variable.</span></span> <span data-ttu-id="3c35f-123">Modüller devralmayı veya uygulama arabirimlerini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="3c35f-123">Modules do not support inheritance or implement interfaces.</span></span> <span data-ttu-id="3c35f-124">Bir modülün bir sınıfın veya yapının olduğu anlamda bir *tür* olmadığına dikkat edin; bir modül veri türüne sahip olacak bir programlama öğesi bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c35f-124">Notice that a module is not a *type* in the sense that a class or structure is — you cannot declare a programming element to have the data type of a module.</span></span>

<span data-ttu-id="3c35f-125">@No__t_0 yalnızca ad alanı düzeyinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c35f-125">You can use `Module` only at namespace level.</span></span> <span data-ttu-id="3c35f-126">Bu, bir modülün *bildirim bağlamının* bir kaynak dosya veya ad alanı olması ve bir sınıf, yapı, modül, arabirim, yordam veya blok olamayacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3c35f-126">This means the *declaration context* for a module must be a source file or namespace, and cannot be a class, structure, module, interface, procedure, or block.</span></span> <span data-ttu-id="3c35f-127">Bir modülün başka bir modül içinde veya herhangi bir türde iç içe geçirilemez.</span><span class="sxs-lookup"><span data-stu-id="3c35f-127">You cannot nest a module within another module, or within any type.</span></span> <span data-ttu-id="3c35f-128">Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="3c35f-128">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="3c35f-129">Bir modül, programınız ile aynı yaşam süresine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="3c35f-129">A module has the same lifetime as your program.</span></span> <span data-ttu-id="3c35f-130">Üyeleri tüm `Shared` olduğundan, ayrıca yaşam sürelerinin programa eşit olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3c35f-130">Because its members are all `Shared`, they also have lifetimes equal to that of the program.</span></span>

<span data-ttu-id="3c35f-131">Modüller varsayılan olarak [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md) erişimine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="3c35f-131">Modules default to [Friend](../../../visual-basic/language-reference/modifiers/friend.md) access.</span></span> <span data-ttu-id="3c35f-132">Erişim değiştiricilerini kullanarak erişim düzeylerini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c35f-132">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="3c35f-133">Daha fazla bilgi için bkz. [Visual Basic erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="3c35f-133">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="3c35f-134">Modülün tüm üyeleri örtülü olarak `Shared`.</span><span class="sxs-lookup"><span data-stu-id="3c35f-134">All members of a module are implicitly `Shared`.</span></span>

## <a name="classes-and-modules"></a><span data-ttu-id="3c35f-135">Sınıflar ve modüller</span><span class="sxs-lookup"><span data-stu-id="3c35f-135">Classes and Modules</span></span>

<span data-ttu-id="3c35f-136">Bu öğelerin birçok benzerlikleri vardır ancak bazı önemli farklılıklar da vardır.</span><span class="sxs-lookup"><span data-stu-id="3c35f-136">These elements have many similarities, but there are some important differences as well.</span></span>

- <span data-ttu-id="3c35f-137">**Terminolojiyi.**</span><span class="sxs-lookup"><span data-stu-id="3c35f-137">**Terminology.**</span></span> <span data-ttu-id="3c35f-138">Önceki Visual Basic sürümleri iki tür modül tanır: *sınıf modülleri* (. CLS dosyaları) ve *Standart modüller* (. bas dosyaları).</span><span class="sxs-lookup"><span data-stu-id="3c35f-138">Previous versions of Visual Basic recognize two types of modules: *class modules* (.cls files) and *standard modules* (.bas files).</span></span> <span data-ttu-id="3c35f-139">Geçerli sürüm, sırasıyla bu *sınıfları* ve *modülleri*çağırır.</span><span class="sxs-lookup"><span data-stu-id="3c35f-139">The current version calls these *classes* and *modules*, respectively.</span></span>

- <span data-ttu-id="3c35f-140">**Paylaşılan Üyeler.**</span><span class="sxs-lookup"><span data-stu-id="3c35f-140">**Shared Members.**</span></span> <span data-ttu-id="3c35f-141">Bir sınıfın bir üyesinin paylaşılan bir veya örnek üye olup olmadığını kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c35f-141">You can control whether a member of a class is a shared or instance member.</span></span>

- <span data-ttu-id="3c35f-142">**Nesne yönü.**</span><span class="sxs-lookup"><span data-stu-id="3c35f-142">**Object Orientation.**</span></span> <span data-ttu-id="3c35f-143">Sınıflar nesne yönelimlidir, ancak modüller değildir.</span><span class="sxs-lookup"><span data-stu-id="3c35f-143">Classes are object-oriented, but modules are not.</span></span> <span data-ttu-id="3c35f-144">Bu nedenle, yalnızca sınıflar nesne olarak oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="3c35f-144">So only classes can be instantiated as objects.</span></span> <span data-ttu-id="3c35f-145">Daha fazla bilgi için bkz. [nesneler ve sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span><span class="sxs-lookup"><span data-stu-id="3c35f-145">For more information, see [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span></span>

## <a name="rules"></a><span data-ttu-id="3c35f-146">Kurallar</span><span class="sxs-lookup"><span data-stu-id="3c35f-146">Rules</span></span>

- <span data-ttu-id="3c35f-147">**İlerine.**</span><span class="sxs-lookup"><span data-stu-id="3c35f-147">**Modifiers.**</span></span> <span data-ttu-id="3c35f-148">Tüm modül üyeleri örtülü olarak [paylaşılır](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="3c35f-148">All module members are implicitly [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span> <span data-ttu-id="3c35f-149">Bir üyeyi bildirirken `Shared` anahtar sözcüğünü kullanamazsınız ve herhangi bir üyenin paylaşılan durumunu değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c35f-149">You cannot use the `Shared` keyword when declaring a member, and you cannot alter the shared status of any member.</span></span>

- <span data-ttu-id="3c35f-150">**Devralmayı.**</span><span class="sxs-lookup"><span data-stu-id="3c35f-150">**Inheritance.**</span></span> <span data-ttu-id="3c35f-151">Modül, tüm modüllerin devraldığı <xref:System.Object> dışındaki herhangi bir türden devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="3c35f-151">A module cannot inherit from any type other than <xref:System.Object>, from which all modules inherit.</span></span> <span data-ttu-id="3c35f-152">Özellikle, bir modül diğerinden devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="3c35f-152">In particular, one module cannot inherit from another.</span></span>

  <span data-ttu-id="3c35f-153">@No__t_1 belirtmek için de, bir modül tanımında [Inherits ifadesini](../../../visual-basic/language-reference/statements/inherits-statement.md) kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="3c35f-153">You cannot use the [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md) in a module definition, even to specify <xref:System.Object>.</span></span>

- <span data-ttu-id="3c35f-154">**Varsayılan özellik.**</span><span class="sxs-lookup"><span data-stu-id="3c35f-154">**Default Property.**</span></span> <span data-ttu-id="3c35f-155">Modülde herhangi bir varsayılan özellik tanımlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="3c35f-155">You cannot define any default properties in a module.</span></span> <span data-ttu-id="3c35f-156">Daha fazla bilgi için bkz. [Default](../../../visual-basic/language-reference/modifiers/default.md).</span><span class="sxs-lookup"><span data-stu-id="3c35f-156">For more information, see [Default](../../../visual-basic/language-reference/modifiers/default.md).</span></span>

## <a name="behavior"></a><span data-ttu-id="3c35f-157">Davranış</span><span class="sxs-lookup"><span data-stu-id="3c35f-157">Behavior</span></span>

- <span data-ttu-id="3c35f-158">**Erişim düzeyi.**</span><span class="sxs-lookup"><span data-stu-id="3c35f-158">**Access Level.**</span></span> <span data-ttu-id="3c35f-159">Bir modül içinde, her üyeyi kendi erişim düzeyiyle bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c35f-159">Within a module, you can declare each member with its own access level.</span></span> <span data-ttu-id="3c35f-160">Modül üyeleri varsayılan olarak [özel](../../../visual-basic/language-reference/modifiers/private.md) erişim için varsayılan olarak, değişkenler ve sabitler hariç [genel](../../../visual-basic/language-reference/modifiers/public.md) erişime açıktır.</span><span class="sxs-lookup"><span data-stu-id="3c35f-160">Module members default to [Public](../../../visual-basic/language-reference/modifiers/public.md) access, except variables and constants, which default to [Private](../../../visual-basic/language-reference/modifiers/private.md) access.</span></span> <span data-ttu-id="3c35f-161">Bir modülün üyelerinden birine göre daha kısıtlı erişimi olduğunda, belirtilen modül erişim düzeyi öncelik kazanır.</span><span class="sxs-lookup"><span data-stu-id="3c35f-161">When a module has more restricted access than one of its members, the specified module access level takes precedence.</span></span>

- <span data-ttu-id="3c35f-162">**Kapsam.**</span><span class="sxs-lookup"><span data-stu-id="3c35f-162">**Scope.**</span></span> <span data-ttu-id="3c35f-163">Modül, ad alanının tamamında kapsam içinde yer alan bir modüldür.</span><span class="sxs-lookup"><span data-stu-id="3c35f-163">A module is in scope throughout its namespace.</span></span>

  <span data-ttu-id="3c35f-164">Her modül üyesinin kapsamı tüm modüldür.</span><span class="sxs-lookup"><span data-stu-id="3c35f-164">The scope of every module member is the entire module.</span></span> <span data-ttu-id="3c35f-165">Tüm üyelerin *tür promosyonu*olduğuna dikkat edin ve bu, kapsamının modülü içeren ad alanına yükseltilmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="3c35f-165">Notice that all members undergo *type promotion*, which causes their scope to be promoted to the namespace containing the module.</span></span> <span data-ttu-id="3c35f-166">Daha fazla bilgi için bkz. [yükseltme türü](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span><span class="sxs-lookup"><span data-stu-id="3c35f-166">For more information, see [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span></span>

- <span data-ttu-id="3c35f-167">**Yeter.**</span><span class="sxs-lookup"><span data-stu-id="3c35f-167">**Qualification.**</span></span> <span data-ttu-id="3c35f-168">Bir projede birden fazla modülünüz olabilir ve aynı ada sahip üyeleri iki veya daha fazla modülle bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c35f-168">You can have multiple modules in a project, and you can declare members with the same name in two or more modules.</span></span> <span data-ttu-id="3c35f-169">Bununla birlikte, başvurunun bu modülün dışından olması durumunda, ilgili modül adı ile böyle bir üyeye yönelik herhangi bir başvuruyu nitelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3c35f-169">However, you must qualify any reference to such a member with the appropriate module name if the reference is from outside that module.</span></span> <span data-ttu-id="3c35f-170">Daha fazla bilgi için bkz. [bildirilmemiş öğelere başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="3c35f-170">For more information, see [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

## <a name="example"></a><span data-ttu-id="3c35f-171">Örnek</span><span class="sxs-lookup"><span data-stu-id="3c35f-171">Example</span></span>

[!code-vb[VbVbalrStatements#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#69)]

## <a name="see-also"></a><span data-ttu-id="3c35f-172">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c35f-172">See also</span></span>

- [<span data-ttu-id="3c35f-173">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="3c35f-173">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="3c35f-174">Namespace Deyimi</span><span class="sxs-lookup"><span data-stu-id="3c35f-174">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [<span data-ttu-id="3c35f-175">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="3c35f-175">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="3c35f-176">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="3c35f-176">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="3c35f-177">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="3c35f-177">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="3c35f-178">Tür Yükseltme</span><span class="sxs-lookup"><span data-stu-id="3c35f-178">Type Promotion</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
