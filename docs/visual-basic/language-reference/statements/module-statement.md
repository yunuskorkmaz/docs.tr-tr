---
title: Module Deyimi
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 92cdcd1919f21243118108da3bc382ea5d954130
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="module-statement"></a><span data-ttu-id="47cfa-102">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="47cfa-102">Module Statement</span></span>
<span data-ttu-id="47cfa-103">Bir modül adını bildirir ve tanımını değişkenleri, özellikleri, olayları ve modülü oluşur yordamları sunar.</span><span class="sxs-lookup"><span data-stu-id="47cfa-103">Declares the name of a module and introduces the definition of the variables, properties, events, and procedures that the module comprises.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47cfa-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="47cfa-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ]  Module name  
    [ statements ]  
End Module  
```  
  
## <a name="parts"></a><span data-ttu-id="47cfa-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="47cfa-105">Parts</span></span>  
 `attributelist`  
 <span data-ttu-id="47cfa-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="47cfa-106">Optional.</span></span> <span data-ttu-id="47cfa-107">Bkz: [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="47cfa-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
 `accessmodifier`  
 <span data-ttu-id="47cfa-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="47cfa-108">Optional.</span></span> <span data-ttu-id="47cfa-109">Aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="47cfa-109">Can be one of the following:</span></span>  
  
-   [<span data-ttu-id="47cfa-110">Ortak</span><span class="sxs-lookup"><span data-stu-id="47cfa-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
-   [<span data-ttu-id="47cfa-111">Arkadaş</span><span class="sxs-lookup"><span data-stu-id="47cfa-111">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
 <span data-ttu-id="47cfa-112">Bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="47cfa-112">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 `name`  
 <span data-ttu-id="47cfa-113">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="47cfa-113">Required.</span></span> <span data-ttu-id="47cfa-114">Bu modül adı.</span><span class="sxs-lookup"><span data-stu-id="47cfa-114">Name of this module.</span></span> <span data-ttu-id="47cfa-115">Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="47cfa-115">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 `statements`  
 <span data-ttu-id="47cfa-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="47cfa-116">Optional.</span></span> <span data-ttu-id="47cfa-117">Değişkenleri, özellikleri, olayları, yordamlar ve bu modülün iç içe geçmiş türler tanımlamak deyimleri.</span><span class="sxs-lookup"><span data-stu-id="47cfa-117">Statements which define the variables, properties, events, procedures, and nested types of this module.</span></span>  
  
 `End Module`  
 <span data-ttu-id="47cfa-118">Sonlandırır `Module` tanımı.</span><span class="sxs-lookup"><span data-stu-id="47cfa-118">Terminates the `Module` definition.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47cfa-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="47cfa-119">Remarks</span></span>  
 <span data-ttu-id="47cfa-120">A `Module` deyimi, ad alanı bir başvuru türü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="47cfa-120">A `Module` statement defines a reference type available throughout its namespace.</span></span> <span data-ttu-id="47cfa-121">A *Modülü* (bazen adlı bir *standart modül*) benzer bir sınıf, ancak bazı önemli farklılıklar.</span><span class="sxs-lookup"><span data-stu-id="47cfa-121">A *module* (sometimes called a *standard module*)is similar to a class but with some important distinctions.</span></span> <span data-ttu-id="47cfa-122">Her modül tam olarak bir örnek var ve oluşturulamaz veya bir değişkenine atanan gerekmez.</span><span class="sxs-lookup"><span data-stu-id="47cfa-122">Every module has exactly one instance and does not need to be created or assigned to a variable.</span></span> <span data-ttu-id="47cfa-123">Modülleri devralma desteklemez veya arabirimlerini.</span><span class="sxs-lookup"><span data-stu-id="47cfa-123">Modules do not support inheritance or implement interfaces.</span></span> <span data-ttu-id="47cfa-124">Bir modül bildirimi bir *türü* bir sınıf veya yapı herkese açık — bir modül veri türüne sahip bir programlama öğesi bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="47cfa-124">Notice that a module is not a *type* in the sense that a class or structure is — you cannot declare a programming element to have the data type of a module.</span></span>  
  
 <span data-ttu-id="47cfa-125">Kullanabileceğiniz `Module` yalnızca ad alanı düzeyinde.</span><span class="sxs-lookup"><span data-stu-id="47cfa-125">You can use `Module` only at namespace level.</span></span> <span data-ttu-id="47cfa-126">Yani *bildirimi bağlam* bir modül kaynak dosya veya ad alanı olmalı ve bir sınıf, yapı, modülü, arabirimi, yordamı veya blok olamaz.</span><span class="sxs-lookup"><span data-stu-id="47cfa-126">This means the *declaration context* for a module must be a source file or namespace, and cannot be a class, structure, module, interface, procedure, or block.</span></span> <span data-ttu-id="47cfa-127">Bir modül herhangi bir tür veya başka bir modül içinde iç içe yerleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="47cfa-127">You cannot nest a module within another module, or within any type.</span></span> <span data-ttu-id="47cfa-128">Daha fazla bilgi için bkz: [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="47cfa-128">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="47cfa-129">Bir modül programınız olarak aynı yaşam süresi vardır.</span><span class="sxs-lookup"><span data-stu-id="47cfa-129">A module has the same lifetime as your program.</span></span> <span data-ttu-id="47cfa-130">Üyeleri tüm olduğundan `Shared`, ayrıca sahip oldukları yaşam süreleri, program eşit.</span><span class="sxs-lookup"><span data-stu-id="47cfa-130">Because its members are all `Shared`, they also have lifetimes equal to that of the program.</span></span>  
  
 <span data-ttu-id="47cfa-131">Modülleri varsayılan [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md) erişim.</span><span class="sxs-lookup"><span data-stu-id="47cfa-131">Modules default to [Friend](../../../visual-basic/language-reference/modifiers/friend.md) access.</span></span> <span data-ttu-id="47cfa-132">Erişim değiştiricileri ile erişim düzeylerine göre ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47cfa-132">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="47cfa-133">Daha fazla bilgi için bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="47cfa-133">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="47cfa-134">Örtük olarak bir modül tüm üyeleri olan `Shared`.</span><span class="sxs-lookup"><span data-stu-id="47cfa-134">All members of a module are implicitly `Shared`.</span></span>  
  
## <a name="classes-and-modules"></a><span data-ttu-id="47cfa-135">Sınıfları ve modülleri</span><span class="sxs-lookup"><span data-stu-id="47cfa-135">Classes and Modules</span></span>  
 <span data-ttu-id="47cfa-136">Benzer şekilde bu öğelere sahip, ancak de önemli bazı farklar vardır.</span><span class="sxs-lookup"><span data-stu-id="47cfa-136">These elements have many similarities, but there are some important differences as well.</span></span>  
  
-   <span data-ttu-id="47cfa-137">**Terminolojisi.**</span><span class="sxs-lookup"><span data-stu-id="47cfa-137">**Terminology.**</span></span> <span data-ttu-id="47cfa-138">Visual Basic önceki sürümlerini tanıması modülleri iki tür: *sınıf modülleri* (.cls dosyaları) ve *Standart modüller* (.bas dosyaları).</span><span class="sxs-lookup"><span data-stu-id="47cfa-138">Previous versions of Visual Basic recognize two types of modules: *class modules* (.cls files) and *standard modules* (.bas files).</span></span> <span data-ttu-id="47cfa-139">Bunlar geçerli sürümü çağırır *sınıfları* ve *modülleri*sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="47cfa-139">The current version calls these *classes* and *modules*, respectively.</span></span>  
  
-   <span data-ttu-id="47cfa-140">**Paylaşılan üyeler.**</span><span class="sxs-lookup"><span data-stu-id="47cfa-140">**Shared Members.**</span></span> <span data-ttu-id="47cfa-141">Bir sınıf üyesi paylaşılan olup veya örnek üyesine kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47cfa-141">You can control whether a member of a class is a shared or instance member.</span></span>  
  
-   <span data-ttu-id="47cfa-142">**Nesne yönü.**</span><span class="sxs-lookup"><span data-stu-id="47cfa-142">**Object Orientation.**</span></span> <span data-ttu-id="47cfa-143">Nesne odaklı sınıfları, ancak modüller değildir.</span><span class="sxs-lookup"><span data-stu-id="47cfa-143">Classes are object-oriented, but modules are not.</span></span> <span data-ttu-id="47cfa-144">Bu nedenle yalnızca sınıfları nesneler olarak oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="47cfa-144">So only classes can be instantiated as objects.</span></span> <span data-ttu-id="47cfa-145">Daha fazla bilgi için bkz: [nesneler ve sınıflar](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span><span class="sxs-lookup"><span data-stu-id="47cfa-145">For more information, see [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="47cfa-146">Kurallar</span><span class="sxs-lookup"><span data-stu-id="47cfa-146">Rules</span></span>  
  
-   <span data-ttu-id="47cfa-147">**Değiştirici.**</span><span class="sxs-lookup"><span data-stu-id="47cfa-147">**Modifiers.**</span></span> <span data-ttu-id="47cfa-148">Tüm modül örtük olarak üyeleridir [paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="47cfa-148">All module members are implicitly [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span> <span data-ttu-id="47cfa-149">Kullanamazsınız `Shared` bildirme üyesi ve herhangi bir üyenin paylaşılan durum değiştirilemiyor, anahtar sözcük.</span><span class="sxs-lookup"><span data-stu-id="47cfa-149">You cannot use the `Shared` keyword when declaring a member, and you cannot alter the shared status of any member.</span></span>  
  
-   <span data-ttu-id="47cfa-150">**Devralma.**</span><span class="sxs-lookup"><span data-stu-id="47cfa-150">**Inheritance.**</span></span> <span data-ttu-id="47cfa-151">Bir modül herhangi bir türünden dışında devral olamaz <xref:System.Object>, tüm modüllerine devralır.</span><span class="sxs-lookup"><span data-stu-id="47cfa-151">A module cannot inherit from any type other than <xref:System.Object>, from which all modules inherit.</span></span> <span data-ttu-id="47cfa-152">Özellikle, bir modül başka bir devralma olamaz.</span><span class="sxs-lookup"><span data-stu-id="47cfa-152">In particular, one module cannot inherit from another.</span></span>  
  
     <span data-ttu-id="47cfa-153">Kullanamazsınız [Inherits deyimi](../../../visual-basic/language-reference/statements/inherits-statement.md) belirtmek için bir modül tanımında bile <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="47cfa-153">You cannot use the [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md) in a module definition, even to specify <xref:System.Object>.</span></span>  
  
-   <span data-ttu-id="47cfa-154">**Varsayılan özellik.**</span><span class="sxs-lookup"><span data-stu-id="47cfa-154">**Default Property.**</span></span> <span data-ttu-id="47cfa-155">Bir modüldeki herhangi bir varsayılan özellik tanımlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="47cfa-155">You cannot define any default properties in a module.</span></span> <span data-ttu-id="47cfa-156">Daha fazla bilgi için bkz: [varsayılan](../../../visual-basic/language-reference/modifiers/default.md).</span><span class="sxs-lookup"><span data-stu-id="47cfa-156">For more information, see [Default](../../../visual-basic/language-reference/modifiers/default.md).</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="47cfa-157">Davranış</span><span class="sxs-lookup"><span data-stu-id="47cfa-157">Behavior</span></span>  
  
-   <span data-ttu-id="47cfa-158">**Erişim düzeyi.**</span><span class="sxs-lookup"><span data-stu-id="47cfa-158">**Access Level.**</span></span> <span data-ttu-id="47cfa-159">Bir modül her üye kendi erişim düzeyi ile bildirebilir.</span><span class="sxs-lookup"><span data-stu-id="47cfa-159">Within a module, you can declare each member with its own access level.</span></span> <span data-ttu-id="47cfa-160">Modül üyeleri için varsayılan değer [ortak](../../../visual-basic/language-reference/modifiers/public.md) erişim, değişkenleri ve sabitleri dışında varsayılan [özel](../../../visual-basic/language-reference/modifiers/private.md) erişim.</span><span class="sxs-lookup"><span data-stu-id="47cfa-160">Module members default to [Public](../../../visual-basic/language-reference/modifiers/public.md) access, except variables and constants, which default to [Private](../../../visual-basic/language-reference/modifiers/private.md) access.</span></span> <span data-ttu-id="47cfa-161">Bir modül daha üyeleri birden sınırlı erişimi Belirtilen modül erişim düzeyi önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="47cfa-161">When a module has more restricted access than one of its members, the specified module access level takes precedence.</span></span>  
  
-   <span data-ttu-id="47cfa-162">**Kapsamı.**</span><span class="sxs-lookup"><span data-stu-id="47cfa-162">**Scope.**</span></span> <span data-ttu-id="47cfa-163">Kendi ad boyunca kapsamdaki bir modüldür.</span><span class="sxs-lookup"><span data-stu-id="47cfa-163">A module is in scope throughout its namespace.</span></span>  
  
     <span data-ttu-id="47cfa-164">Her modül üye kapsamını tüm modülüdür.</span><span class="sxs-lookup"><span data-stu-id="47cfa-164">The scope of every module member is the entire module.</span></span> <span data-ttu-id="47cfa-165">Tüm üyeler uygulanabilecek bildirimi *yazın yükseltme*, kapsamlarına modülü içeren ad alanına yükseltilmesi neden olur.</span><span class="sxs-lookup"><span data-stu-id="47cfa-165">Notice that all members undergo *type promotion*, which causes their scope to be promoted to the namespace containing the module.</span></span> <span data-ttu-id="47cfa-166">Daha fazla bilgi için bkz: [tür yükseltme](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span><span class="sxs-lookup"><span data-stu-id="47cfa-166">For more information, see [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span></span>  
  
-   <span data-ttu-id="47cfa-167">**Niteliğe.**</span><span class="sxs-lookup"><span data-stu-id="47cfa-167">**Qualification.**</span></span> <span data-ttu-id="47cfa-168">Bir projede birden fazla modülü sahip olabilir ve iki veya daha fazla modüllerinde aynı ada sahip üye bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47cfa-168">You can have multiple modules in a project, and you can declare members with the same name in two or more modules.</span></span> <span data-ttu-id="47cfa-169">Ancak, başvuru dışında bu modül ise böyle bir üyesi uygun modül adı ile herhangi bir referans nitelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="47cfa-169">However, you must qualify any reference to such a member with the appropriate module name if the reference is from outside that module.</span></span> <span data-ttu-id="47cfa-170">Daha fazla bilgi için bkz: [bildirilmiş öğelere başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="47cfa-170">For more information, see [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="47cfa-171">Örnek</span><span class="sxs-lookup"><span data-stu-id="47cfa-171">Example</span></span>  
 [!code-vb[VbVbalrStatements#69](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/module-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="47cfa-172">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="47cfa-172">See Also</span></span>  
 [<span data-ttu-id="47cfa-173">Class deyimi</span><span class="sxs-lookup"><span data-stu-id="47cfa-173">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
 [<span data-ttu-id="47cfa-174">Namespace deyimi</span><span class="sxs-lookup"><span data-stu-id="47cfa-174">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [<span data-ttu-id="47cfa-175">Structure deyimi</span><span class="sxs-lookup"><span data-stu-id="47cfa-175">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="47cfa-176">Interface deyimi</span><span class="sxs-lookup"><span data-stu-id="47cfa-176">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="47cfa-177">Property deyimi</span><span class="sxs-lookup"><span data-stu-id="47cfa-177">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="47cfa-178">Tür promosyonu</span><span class="sxs-lookup"><span data-stu-id="47cfa-178">Type Promotion</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
