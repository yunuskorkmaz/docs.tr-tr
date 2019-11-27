---
title: Module Deyimi
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
ms.openlocfilehash: 56fc4f9383f1fc4779358ef18a4e5c611d897eda
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348014"
---
# <a name="module-statement"></a><span data-ttu-id="359a9-102">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="359a9-102">Module Statement</span></span>

<span data-ttu-id="359a9-103">Modülün adını bildirir ve modülün içerdiği değişkenlerin, özelliklerin, olayların ve yordamların tanımını tanıtır.</span><span class="sxs-lookup"><span data-stu-id="359a9-103">Declares the name of a module and introduces the definition of the variables, properties, events, and procedures that the module comprises.</span></span>

## <a name="syntax"></a><span data-ttu-id="359a9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="359a9-104">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ]  Module name
    [ statements ]
End Module
```

## <a name="parts"></a><span data-ttu-id="359a9-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="359a9-105">Parts</span></span>

`attributelist`  
<span data-ttu-id="359a9-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="359a9-106">Optional.</span></span> <span data-ttu-id="359a9-107">Bkz. [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="359a9-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>

`accessmodifier`  
<span data-ttu-id="359a9-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="359a9-108">Optional.</span></span> <span data-ttu-id="359a9-109">Aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="359a9-109">Can be one of the following:</span></span>

- [<span data-ttu-id="359a9-110">Public</span><span class="sxs-lookup"><span data-stu-id="359a9-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)

- [<span data-ttu-id="359a9-111">Friend</span><span class="sxs-lookup"><span data-stu-id="359a9-111">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)

<span data-ttu-id="359a9-112">[Visual Basic erişim düzeylerine](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="359a9-112">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

`name`  
<span data-ttu-id="359a9-113">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="359a9-113">Required.</span></span> <span data-ttu-id="359a9-114">Bu modülün adı.</span><span class="sxs-lookup"><span data-stu-id="359a9-114">Name of this module.</span></span> <span data-ttu-id="359a9-115">Bkz. [tanımlanmış öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="359a9-115">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

`statements`  
<span data-ttu-id="359a9-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="359a9-116">Optional.</span></span> <span data-ttu-id="359a9-117">Değişkenleri, özellikleri, olayları, yordamları ve bu modülün iç içe geçmiş türlerini tanımlayan deyimler.</span><span class="sxs-lookup"><span data-stu-id="359a9-117">Statements which define the variables, properties, events, procedures, and nested types of this module.</span></span>

`End Module`  
<span data-ttu-id="359a9-118">`Module` tanımını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="359a9-118">Terminates the `Module` definition.</span></span>

## <a name="remarks"></a><span data-ttu-id="359a9-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="359a9-119">Remarks</span></span>

<span data-ttu-id="359a9-120">`Module` bir ifade, ad alanı genelinde kullanılabilir bir başvuru türü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="359a9-120">A `Module` statement defines a reference type available throughout its namespace.</span></span> <span data-ttu-id="359a9-121">*Modül* (bazen *Standart Modül*olarak adlandırılır), bir sınıfa benzer ancak bazı önemli ayrımlarla benzerdir.</span><span class="sxs-lookup"><span data-stu-id="359a9-121">A *module* (sometimes called a *standard module*) is similar to a class but with some important distinctions.</span></span> <span data-ttu-id="359a9-122">Her modülün tam olarak bir örneği vardır ve oluşturulması veya bir değişkene atanması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="359a9-122">Every module has exactly one instance and does not need to be created or assigned to a variable.</span></span> <span data-ttu-id="359a9-123">Modüller devralmayı veya uygulama arabirimlerini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="359a9-123">Modules do not support inheritance or implement interfaces.</span></span> <span data-ttu-id="359a9-124">Bir modülün bir sınıfın veya yapının olduğu anlamda bir *tür* olmadığına dikkat edin; bir modül veri türüne sahip olacak bir programlama öğesi bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="359a9-124">Notice that a module is not a *type* in the sense that a class or structure is — you cannot declare a programming element to have the data type of a module.</span></span>

<span data-ttu-id="359a9-125">`Module` yalnızca ad alanı düzeyinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="359a9-125">You can use `Module` only at namespace level.</span></span> <span data-ttu-id="359a9-126">Bu, bir modülün *bildirim bağlamının* bir kaynak dosya veya ad alanı olması ve bir sınıf, yapı, modül, arabirim, yordam veya blok olamayacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="359a9-126">This means the *declaration context* for a module must be a source file or namespace, and cannot be a class, structure, module, interface, procedure, or block.</span></span> <span data-ttu-id="359a9-127">Bir modülün başka bir modül içinde veya herhangi bir türde iç içe geçirilemez.</span><span class="sxs-lookup"><span data-stu-id="359a9-127">You cannot nest a module within another module, or within any type.</span></span> <span data-ttu-id="359a9-128">Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="359a9-128">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="359a9-129">Bir modül, programınız ile aynı yaşam süresine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="359a9-129">A module has the same lifetime as your program.</span></span> <span data-ttu-id="359a9-130">Üyeleri tüm `Shared`olduğundan, ayrıca yaşam sürelerinin programa eşit olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="359a9-130">Because its members are all `Shared`, they also have lifetimes equal to that of the program.</span></span>

<span data-ttu-id="359a9-131">Modüller varsayılan olarak [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md) erişimine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="359a9-131">Modules default to [Friend](../../../visual-basic/language-reference/modifiers/friend.md) access.</span></span> <span data-ttu-id="359a9-132">Erişim değiştiricilerini kullanarak erişim düzeylerini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="359a9-132">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="359a9-133">Daha fazla bilgi için bkz. [Visual Basic erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="359a9-133">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="359a9-134">Modülün tüm üyeleri örtülü olarak `Shared`.</span><span class="sxs-lookup"><span data-stu-id="359a9-134">All members of a module are implicitly `Shared`.</span></span>

## <a name="classes-and-modules"></a><span data-ttu-id="359a9-135">Sınıflar ve modüller</span><span class="sxs-lookup"><span data-stu-id="359a9-135">Classes and Modules</span></span>

<span data-ttu-id="359a9-136">Bu öğelerin birçok benzerlikleri vardır ancak bazı önemli farklılıklar da vardır.</span><span class="sxs-lookup"><span data-stu-id="359a9-136">These elements have many similarities, but there are some important differences as well.</span></span>

- <span data-ttu-id="359a9-137">**Terminolojiyi.**</span><span class="sxs-lookup"><span data-stu-id="359a9-137">**Terminology.**</span></span> <span data-ttu-id="359a9-138">Önceki Visual Basic sürümleri iki tür modül tanır: *sınıf modülleri* (. CLS dosyaları) ve *Standart modüller* (. bas dosyaları).</span><span class="sxs-lookup"><span data-stu-id="359a9-138">Previous versions of Visual Basic recognize two types of modules: *class modules* (.cls files) and *standard modules* (.bas files).</span></span> <span data-ttu-id="359a9-139">Geçerli sürüm, sırasıyla bu *sınıfları* ve *modülleri*çağırır.</span><span class="sxs-lookup"><span data-stu-id="359a9-139">The current version calls these *classes* and *modules*, respectively.</span></span>

- <span data-ttu-id="359a9-140">**Paylaşılan Üyeler.**</span><span class="sxs-lookup"><span data-stu-id="359a9-140">**Shared Members.**</span></span> <span data-ttu-id="359a9-141">Bir sınıfın bir üyesinin paylaşılan bir veya örnek üye olup olmadığını kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="359a9-141">You can control whether a member of a class is a shared or instance member.</span></span>

- <span data-ttu-id="359a9-142">**Nesne yönü.**</span><span class="sxs-lookup"><span data-stu-id="359a9-142">**Object Orientation.**</span></span> <span data-ttu-id="359a9-143">Sınıflar nesne yönelimlidir, ancak modüller değildir.</span><span class="sxs-lookup"><span data-stu-id="359a9-143">Classes are object-oriented, but modules are not.</span></span> <span data-ttu-id="359a9-144">Bu nedenle, yalnızca sınıflar nesne olarak oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="359a9-144">So only classes can be instantiated as objects.</span></span> <span data-ttu-id="359a9-145">Daha fazla bilgi için bkz. [nesneler ve sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span><span class="sxs-lookup"><span data-stu-id="359a9-145">For more information, see [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span></span>

## <a name="rules"></a><span data-ttu-id="359a9-146">Kurallar</span><span class="sxs-lookup"><span data-stu-id="359a9-146">Rules</span></span>

- <span data-ttu-id="359a9-147">**İlerine.**</span><span class="sxs-lookup"><span data-stu-id="359a9-147">**Modifiers.**</span></span> <span data-ttu-id="359a9-148">Tüm modül üyeleri örtülü olarak [paylaşılır](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="359a9-148">All module members are implicitly [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span> <span data-ttu-id="359a9-149">Bir üyeyi bildirirken `Shared` anahtar sözcüğünü kullanamazsınız ve herhangi bir üyenin paylaşılan durumunu değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="359a9-149">You cannot use the `Shared` keyword when declaring a member, and you cannot alter the shared status of any member.</span></span>

- <span data-ttu-id="359a9-150">**Devralmayı.**</span><span class="sxs-lookup"><span data-stu-id="359a9-150">**Inheritance.**</span></span> <span data-ttu-id="359a9-151">Modül, tüm modüllerin devraldığı <xref:System.Object>dışındaki herhangi bir türden devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="359a9-151">A module cannot inherit from any type other than <xref:System.Object>, from which all modules inherit.</span></span> <span data-ttu-id="359a9-152">Özellikle, bir modül diğerinden devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="359a9-152">In particular, one module cannot inherit from another.</span></span>

  <span data-ttu-id="359a9-153"><xref:System.Object>belirtmek için de, bir modül tanımında [Inherits ifadesini](../../../visual-basic/language-reference/statements/inherits-statement.md) kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="359a9-153">You cannot use the [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md) in a module definition, even to specify <xref:System.Object>.</span></span>

- <span data-ttu-id="359a9-154">**Varsayılan özellik.**</span><span class="sxs-lookup"><span data-stu-id="359a9-154">**Default Property.**</span></span> <span data-ttu-id="359a9-155">Modülde herhangi bir varsayılan özellik tanımlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="359a9-155">You cannot define any default properties in a module.</span></span> <span data-ttu-id="359a9-156">Daha fazla bilgi için bkz. [Default](../../../visual-basic/language-reference/modifiers/default.md).</span><span class="sxs-lookup"><span data-stu-id="359a9-156">For more information, see [Default](../../../visual-basic/language-reference/modifiers/default.md).</span></span>

## <a name="behavior"></a><span data-ttu-id="359a9-157">Davranış</span><span class="sxs-lookup"><span data-stu-id="359a9-157">Behavior</span></span>

- <span data-ttu-id="359a9-158">**Erişim düzeyi.**</span><span class="sxs-lookup"><span data-stu-id="359a9-158">**Access Level.**</span></span> <span data-ttu-id="359a9-159">Bir modül içinde, her üyeyi kendi erişim düzeyiyle bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="359a9-159">Within a module, you can declare each member with its own access level.</span></span> <span data-ttu-id="359a9-160">Modül üyeleri varsayılan olarak [özel](../../../visual-basic/language-reference/modifiers/private.md) erişim için varsayılan olarak, değişkenler ve sabitler hariç [genel](../../../visual-basic/language-reference/modifiers/public.md) erişime açıktır.</span><span class="sxs-lookup"><span data-stu-id="359a9-160">Module members default to [Public](../../../visual-basic/language-reference/modifiers/public.md) access, except variables and constants, which default to [Private](../../../visual-basic/language-reference/modifiers/private.md) access.</span></span> <span data-ttu-id="359a9-161">Bir modülün üyelerinden birine göre daha kısıtlı erişimi olduğunda, belirtilen modül erişim düzeyi öncelik kazanır.</span><span class="sxs-lookup"><span data-stu-id="359a9-161">When a module has more restricted access than one of its members, the specified module access level takes precedence.</span></span>

- <span data-ttu-id="359a9-162">**Kapsam.**</span><span class="sxs-lookup"><span data-stu-id="359a9-162">**Scope.**</span></span> <span data-ttu-id="359a9-163">Modül, ad alanının tamamında kapsam içinde yer alan bir modüldür.</span><span class="sxs-lookup"><span data-stu-id="359a9-163">A module is in scope throughout its namespace.</span></span>

  <span data-ttu-id="359a9-164">Her modül üyesinin kapsamı tüm modüldür.</span><span class="sxs-lookup"><span data-stu-id="359a9-164">The scope of every module member is the entire module.</span></span> <span data-ttu-id="359a9-165">Tüm üyelerin *tür promosyonu*olduğuna dikkat edin ve bu, kapsamının modülü içeren ad alanına yükseltilmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="359a9-165">Notice that all members undergo *type promotion*, which causes their scope to be promoted to the namespace containing the module.</span></span> <span data-ttu-id="359a9-166">Daha fazla bilgi için bkz. [yükseltme türü](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span><span class="sxs-lookup"><span data-stu-id="359a9-166">For more information, see [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span></span>

- <span data-ttu-id="359a9-167">**Yeter.**</span><span class="sxs-lookup"><span data-stu-id="359a9-167">**Qualification.**</span></span> <span data-ttu-id="359a9-168">Bir projede birden fazla modülünüz olabilir ve aynı ada sahip üyeleri iki veya daha fazla modülle bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="359a9-168">You can have multiple modules in a project, and you can declare members with the same name in two or more modules.</span></span> <span data-ttu-id="359a9-169">Bununla birlikte, başvurunun bu modülün dışından olması durumunda, ilgili modül adı ile böyle bir üyeye yönelik herhangi bir başvuruyu nitelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="359a9-169">However, you must qualify any reference to such a member with the appropriate module name if the reference is from outside that module.</span></span> <span data-ttu-id="359a9-170">Daha fazla bilgi için bkz. [bildirilmemiş öğelere başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="359a9-170">For more information, see [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

## <a name="example"></a><span data-ttu-id="359a9-171">Örnek</span><span class="sxs-lookup"><span data-stu-id="359a9-171">Example</span></span>

[!code-vb[VbVbalrStatements#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#69)]

## <a name="see-also"></a><span data-ttu-id="359a9-172">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="359a9-172">See also</span></span>

- [<span data-ttu-id="359a9-173">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="359a9-173">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="359a9-174">Namespace Deyimi</span><span class="sxs-lookup"><span data-stu-id="359a9-174">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [<span data-ttu-id="359a9-175">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="359a9-175">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="359a9-176">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="359a9-176">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="359a9-177">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="359a9-177">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="359a9-178">Tür Yükseltme</span><span class="sxs-lookup"><span data-stu-id="359a9-178">Type Promotion</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
