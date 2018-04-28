---
title: Property Deyimi
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.PropertySet
- vb.Property
- vb.PropertyGet
helpviewer_keywords:
- Property statement [Visual Basic]
- default modifier
- property procedures [Visual Basic], Property statements
- Property keyword [Visual Basic]
ms.assetid: 3155edaf-8ebd-45c6-9cef-11d5d2dc8d38
caps.latest.revision: 41
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 558b62dd8c676532355ef12134ad8cb803b70796
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="property-statement"></a><span data-ttu-id="3a143-102">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="3a143-102">Property Statement</span></span>
<span data-ttu-id="3a143-103">Bir özellik ve depolamak ve özellik değerini almak için kullanılan özellik yordamları adını bildirir.</span><span class="sxs-lookup"><span data-stu-id="3a143-103">Declares the name of a property, and the property procedures used to store and retrieve the value of the property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a143-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3a143-104">Syntax</span></span>  
  
```vb  
[ <attributelist> ] [ Default ] [ accessmodifier ]   
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ] [ Iterator ]  
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]  
    [ <attributelist> ] [ accessmodifier ] Get  
        [ statements ]  
    End Get  
    [ <attributelist> ] [ accessmodifier ] Set ( ByVal value As returntype [, parameterlist ] )  
        [ statements ]  
    End Set  
End Property  
- or -  
[ <attributelist> ] [ Default ] [ accessmodifier ]   
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ]   
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]  
```  
  
## <a name="parts"></a><span data-ttu-id="3a143-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="3a143-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="3a143-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3a143-106">Optional.</span></span> <span data-ttu-id="3a143-107">Bu özellik için geçerli öznitelikler listesi veya `Get` veya `Set` yordamı.</span><span class="sxs-lookup"><span data-stu-id="3a143-107">List of attributes that apply to this property or `Get` or `Set` procedure.</span></span> <span data-ttu-id="3a143-108">Bkz: [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="3a143-108">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
-   `Default`  
  
     <span data-ttu-id="3a143-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3a143-109">Optional.</span></span> <span data-ttu-id="3a143-110">Bu özellik varsayılan özelliği sınıf veya yapı tanımlı için olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="3a143-110">Specifies that this property is the default property for the class or structure on which it is defined.</span></span> <span data-ttu-id="3a143-111">Varsayılan Özellikler parametreleri kabul etmeniz gerekir ve ayarlanabilir ve özellik adı belirtmeden alınır.</span><span class="sxs-lookup"><span data-stu-id="3a143-111">Default properties must accept parameters and can be set and retrieved without specifying the property name.</span></span> <span data-ttu-id="3a143-112">Özelliği olarak bildirirseniz `Default`, kullanamazsınız `Private` özelliği veya onun özellik yordamlardan birini.</span><span class="sxs-lookup"><span data-stu-id="3a143-112">If you declare the property as `Default`, you cannot use `Private` on the property or on either of its property procedures.</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="3a143-113">İsteğe bağlı `Property` deyimi ve en fazla birinde `Get` ve `Set` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="3a143-113">Optional on the `Property` statement and on at most one of the `Get` and `Set` statements.</span></span> <span data-ttu-id="3a143-114">Aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="3a143-114">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="3a143-115">Public</span><span class="sxs-lookup"><span data-stu-id="3a143-115">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="3a143-116">Protected</span><span class="sxs-lookup"><span data-stu-id="3a143-116">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="3a143-117">Friend</span><span class="sxs-lookup"><span data-stu-id="3a143-117">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="3a143-118">Private</span><span class="sxs-lookup"><span data-stu-id="3a143-118">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
     <span data-ttu-id="3a143-119">Bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="3a143-119">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `propertymodifiers`  
  
     <span data-ttu-id="3a143-120">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3a143-120">Optional.</span></span> <span data-ttu-id="3a143-121">Aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="3a143-121">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="3a143-122">Overloads</span><span class="sxs-lookup"><span data-stu-id="3a143-122">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [<span data-ttu-id="3a143-123">Overrides</span><span class="sxs-lookup"><span data-stu-id="3a143-123">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [<span data-ttu-id="3a143-124">Overridable</span><span class="sxs-lookup"><span data-stu-id="3a143-124">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [<span data-ttu-id="3a143-125">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="3a143-125">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [<span data-ttu-id="3a143-126">MustOverride</span><span class="sxs-lookup"><span data-stu-id="3a143-126">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     <span data-ttu-id="3a143-127">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3a143-127">Optional.</span></span> <span data-ttu-id="3a143-128">Bkz: [paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="3a143-128">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="3a143-129">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3a143-129">Optional.</span></span> <span data-ttu-id="3a143-130">Bkz: [gölgeleri](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="3a143-130">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
-   `ReadOnly`  
  
     <span data-ttu-id="3a143-131">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3a143-131">Optional.</span></span> <span data-ttu-id="3a143-132">Bkz: [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="3a143-132">See [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
-   `WriteOnly`  
  
     <span data-ttu-id="3a143-133">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3a143-133">Optional.</span></span> <span data-ttu-id="3a143-134">Bkz: [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).</span><span class="sxs-lookup"><span data-stu-id="3a143-134">See [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).</span></span>  
  
-   `Iterator`  
  
     <span data-ttu-id="3a143-135">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3a143-135">Optional.</span></span> <span data-ttu-id="3a143-136">Bkz: [yineleyici](../../../visual-basic/language-reference/modifiers/iterator.md).</span><span class="sxs-lookup"><span data-stu-id="3a143-136">See [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).</span></span>  
  
-   `name`  
  
     <span data-ttu-id="3a143-137">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="3a143-137">Required.</span></span> <span data-ttu-id="3a143-138">Özelliğin adı.</span><span class="sxs-lookup"><span data-stu-id="3a143-138">Name of the property.</span></span> <span data-ttu-id="3a143-139">Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="3a143-139">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   `parameterlist`  
  
     <span data-ttu-id="3a143-140">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3a143-140">Optional.</span></span> <span data-ttu-id="3a143-141">Bu özellik parametrelerinin ve olası ek parametreleri temsil eden yerel değişken adları listesi `Set` yordamı.</span><span class="sxs-lookup"><span data-stu-id="3a143-141">List of local variable names representing the parameters of this property, and possible additional parameters of the `Set` procedure.</span></span> <span data-ttu-id="3a143-142">Bkz: [parametre listesi](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="3a143-142">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>  
  
-   `returntype`  
  
     <span data-ttu-id="3a143-143">Gerekli olursa `Option``Strict` olan `On`.</span><span class="sxs-lookup"><span data-stu-id="3a143-143">Required if `Option``Strict` is `On`.</span></span> <span data-ttu-id="3a143-144">Bu özellik tarafından döndürülen değerin veri türü.</span><span class="sxs-lookup"><span data-stu-id="3a143-144">Data type of the value returned by this property.</span></span>  
  
-   `Implements`  
  
     <span data-ttu-id="3a143-145">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3a143-145">Optional.</span></span> <span data-ttu-id="3a143-146">Bu özellik bir veya daha fazla özellikler, bu özelliğin içeren sınıf veya yapı tarafından uygulanan bir arabirim tanımlanan her biri uygulayan gösterir.</span><span class="sxs-lookup"><span data-stu-id="3a143-146">Indicates that this property implements one or more properties, each one defined in an interface implemented by this property's containing class or structure.</span></span> <span data-ttu-id="3a143-147">Bkz: [uygulayan deyimi](../../../visual-basic/language-reference/statements/implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3a143-147">See [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span>  
  
-   `implementslist`  
  
     <span data-ttu-id="3a143-148">Gerekli olursa `Implements` sağlanır.</span><span class="sxs-lookup"><span data-stu-id="3a143-148">Required if `Implements` is supplied.</span></span> <span data-ttu-id="3a143-149">Uygulanan özelliklerin listesi.</span><span class="sxs-lookup"><span data-stu-id="3a143-149">List of properties being implemented.</span></span>  
  
     `implementedproperty [ , implementedproperty ... ]`  
  
     <span data-ttu-id="3a143-150">Her `implementedproperty` aşağıdaki söz dizimini ve bölümleri vardır:</span><span class="sxs-lookup"><span data-stu-id="3a143-150">Each `implementedproperty` has the following syntax and parts:</span></span>  
  
     `interface.definedname`  
  
    |<span data-ttu-id="3a143-151">Bölümü</span><span class="sxs-lookup"><span data-stu-id="3a143-151">Part</span></span>|<span data-ttu-id="3a143-152">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3a143-152">Description</span></span>|  
    |---|---|  
    |`interface`|<span data-ttu-id="3a143-153">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="3a143-153">Required.</span></span> <span data-ttu-id="3a143-154">Bu özellik tarafından uygulanan bir arabirim adını sınıf veya yapı içeren.</span><span class="sxs-lookup"><span data-stu-id="3a143-154">Name of an interface implemented by this property's containing class or structure.</span></span>|  
    |`definedname`|<span data-ttu-id="3a143-155">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="3a143-155">Required.</span></span> <span data-ttu-id="3a143-156">Adı olarak özelliği tanımlanmış `interface`.</span><span class="sxs-lookup"><span data-stu-id="3a143-156">Name by which the property is defined in `interface`.</span></span>|  
  
-   `Get`  
  
     <span data-ttu-id="3a143-157">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3a143-157">Optional.</span></span> <span data-ttu-id="3a143-158">Özellik işaretlenmişse gerekli `WriteOnly`.</span><span class="sxs-lookup"><span data-stu-id="3a143-158">Required if the property is marked `WriteOnly`.</span></span> <span data-ttu-id="3a143-159">Başlayan bir `Get` özelliğinin değeri döndürmek için kullanılan özellik yordamı.</span><span class="sxs-lookup"><span data-stu-id="3a143-159">Starts a `Get` property procedure that is used to return the value of the property.</span></span>  
  
-   `statements`  
  
     <span data-ttu-id="3a143-160">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3a143-160">Optional.</span></span> <span data-ttu-id="3a143-161">İçinde çalıştırmak için deyimleri bloğunu `Get` veya `Set` yordamı.</span><span class="sxs-lookup"><span data-stu-id="3a143-161">Block of statements to run within the `Get` or `Set` procedure.</span></span>  
  
-   `End Get`  
  
     <span data-ttu-id="3a143-162">Sonlandırır `Get` özellik yordamı.</span><span class="sxs-lookup"><span data-stu-id="3a143-162">Terminates the `Get` property procedure.</span></span>  
  
-   `Set`  
  
     <span data-ttu-id="3a143-163">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3a143-163">Optional.</span></span> <span data-ttu-id="3a143-164">Özellik işaretlenmişse gerekli `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="3a143-164">Required if the property is marked `ReadOnly`.</span></span> <span data-ttu-id="3a143-165">Başlayan bir `Set` özelliğinin değeri depolamak için kullanılan özellik yordamı.</span><span class="sxs-lookup"><span data-stu-id="3a143-165">Starts a `Set` property procedure that is used to store the value of the property.</span></span>  
  
-   `End Set`  
  
     <span data-ttu-id="3a143-166">Sonlandırır `Set` özellik yordamı.</span><span class="sxs-lookup"><span data-stu-id="3a143-166">Terminates the `Set` property procedure.</span></span>  
  
-   `End Property`  
  
     <span data-ttu-id="3a143-167">Bu özellik tanımını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="3a143-167">Terminates the definition of this property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a143-168">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3a143-168">Remarks</span></span>  
 <span data-ttu-id="3a143-169">`Property` Deyimi bir özellik bildirimi tanıtır.</span><span class="sxs-lookup"><span data-stu-id="3a143-169">The `Property` statement introduces the declaration of a property.</span></span> <span data-ttu-id="3a143-170">Bir özelliğin sahip olabileceği bir `Get` (salt okunur), yordam bir `Set` yordamı (yalnızca yazma) veya her iki (okuma-yazma).</span><span class="sxs-lookup"><span data-stu-id="3a143-170">A property can have a `Get` procedure (read only), a `Set` procedure (write only), or both (read-write).</span></span> <span data-ttu-id="3a143-171">Atlayabilirsiniz `Get` ve `Set` otomatik uygulanan özelliğini kullanırken yordamı.</span><span class="sxs-lookup"><span data-stu-id="3a143-171">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="3a143-172">Daha fazla bilgi için bkz: [Auto-Implemented özellikleri](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="3a143-172">For more information, see [Auto-Implemented Properties](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>  
  
 <span data-ttu-id="3a143-173">Kullanabileceğiniz `Property` yalnızca sınıf düzeyinde.</span><span class="sxs-lookup"><span data-stu-id="3a143-173">You can use `Property` only at class level.</span></span> <span data-ttu-id="3a143-174">Yani *bildirimi bağlam* bir özelliği bir sınıf, yapısı, modül veya arabirim olmalı ve kaynak dosyasını, ad alanı, yordam veya blok olamaz.</span><span class="sxs-lookup"><span data-stu-id="3a143-174">This means the *declaration context* for a property must be a class, structure, module, or interface, and cannot be a source file, namespace, procedure, or block.</span></span> <span data-ttu-id="3a143-175">Daha fazla bilgi için bkz: [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="3a143-175">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="3a143-176">Varsayılan olarak, genel erişim özelliklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="3a143-176">By default, properties use public access.</span></span> <span data-ttu-id="3a143-177">Bir özelliğin erişim düzeyi bir erişim değiştiricisi ile ayarlayabilirsiniz `Property` deyimi ve isteğe bağlı olarak ayarlayabilir, özellik yordamları daha kısıtlayıcı bir erişim düzeyi için.</span><span class="sxs-lookup"><span data-stu-id="3a143-177">You can adjust a property's access level with an access modifier on the `Property` statement, and you can optionally adjust one of its property procedures to a more restrictive access level.</span></span>  
  
 <span data-ttu-id="3a143-178">Visual Basic geçirir parametresi `Set` yordam sırasında özelliği atamaları.</span><span class="sxs-lookup"><span data-stu-id="3a143-178">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="3a143-179">İçin bir parametre belirtmezseniz `Set`, tümleşik geliştirme ortamı (IDE) adlı bir örtük parametresini kullanır `value`.</span><span class="sxs-lookup"><span data-stu-id="3a143-179">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="3a143-180">Bu parametre özelliğine atanan değer tutar.</span><span class="sxs-lookup"><span data-stu-id="3a143-180">This parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="3a143-181">Genellikle bu değer bir özel yerel değişkende depolayın ve döndürün her `Get` yordamı çağrılır.</span><span class="sxs-lookup"><span data-stu-id="3a143-181">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="3a143-182">Kurallar</span><span class="sxs-lookup"><span data-stu-id="3a143-182">Rules</span></span>  
  
-   <span data-ttu-id="3a143-183">**Karışık erişim düzeyleri.**</span><span class="sxs-lookup"><span data-stu-id="3a143-183">**Mixed Access Levels.**</span></span> <span data-ttu-id="3a143-184">Bir okuma-yazma özelliği tanımlıyorsanız, isteğe bağlı olarak farklı erişim düzeyi için ya da belirtebilirsiniz `Get` veya `Set` yordamı, ancak ikisini birden değil.</span><span class="sxs-lookup"><span data-stu-id="3a143-184">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="3a143-185">Bunu yaparsanız, yordam erişim düzeyi özelliğin erişim düzeyinden daha kısıtlayıcı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3a143-185">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="3a143-186">Örneğin, özellik bildirilirse `Friend`, bildirebilirsiniz `Set` yordam `Private`, ama `Public`.</span><span class="sxs-lookup"><span data-stu-id="3a143-186">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="3a143-187">Tanımlıyorsanız, bir `ReadOnly` veya `WriteOnly` özelliği, tek bir özellik yordamı (`Get` veya `Set`sırasıyla) tüm özelliğinin temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3a143-187">If you are defining a `ReadOnly` or `WriteOnly` property, the single property procedure (`Get` or `Set`, respectively) represents all of the property.</span></span> <span data-ttu-id="3a143-188">Özelliği için iki erişim düzeyleri ayarlamanız gerekir çünkü bu tür bir yordam için farklı erişim düzeyi bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a143-188">You cannot declare a different access level for such a procedure, because that would set two access levels for the property.</span></span>  
  
-   <span data-ttu-id="3a143-189">**Dönüş türü.**</span><span class="sxs-lookup"><span data-stu-id="3a143-189">**Return Type.**</span></span> <span data-ttu-id="3a143-190">`Property` Deyimi döndürdüğü değerin veri türü bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a143-190">The `Property` statement can declare the data type of the value it returns.</span></span> <span data-ttu-id="3a143-191">Herhangi bir veri türü veya bir numaralandırma, yapısı, sınıf veya arabirim adını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a143-191">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
     <span data-ttu-id="3a143-192">Belirtmezseniz, `returntype`, özellik döndürür `Object`.</span><span class="sxs-lookup"><span data-stu-id="3a143-192">If you do not specify `returntype`, the property returns `Object`.</span></span>  
  
-   <span data-ttu-id="3a143-193">**Uygulaması.**</span><span class="sxs-lookup"><span data-stu-id="3a143-193">**Implementation.**</span></span> <span data-ttu-id="3a143-194">Bu özellik kullanıyorsa `Implements` anahtar sözcüğü, içeren sınıf veya yapı olmalıdır bir `Implements` hemen ardından deyimi kendi `Class` veya `Structure` deyimi.</span><span class="sxs-lookup"><span data-stu-id="3a143-194">If this property uses the `Implements` keyword, the containing class or structure must have an `Implements` statement immediately following its `Class` or `Structure` statement.</span></span> <span data-ttu-id="3a143-195">`Implements` Deyim, belirtilen her bir arabirime içermelidir `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="3a143-195">The `Implements` statement must include each interface specified in `implementslist`.</span></span> <span data-ttu-id="3a143-196">Ancak, bir arabirim tarafından tanımlayan ad `Property` (içinde `definedname`) bu özelliğin adı ile aynı olması gerekmez (içinde `name`).</span><span class="sxs-lookup"><span data-stu-id="3a143-196">However, the name by which an interface defines the `Property` (in `definedname`) does not have to be the same as the name of this property (in `name`).</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="3a143-197">Davranış</span><span class="sxs-lookup"><span data-stu-id="3a143-197">Behavior</span></span>  
  
-   <span data-ttu-id="3a143-198">**Bir özellik yordamından döndürülüyor.**</span><span class="sxs-lookup"><span data-stu-id="3a143-198">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="3a143-199">Zaman `Get` veya `Set` yordamı çağıran kodu döndürür, yürütme çağrılması deyiminden deyim ile devam eder.</span><span class="sxs-lookup"><span data-stu-id="3a143-199">When the `Get` or `Set` procedure returns to the calling code, execution continues with the statement following the statement that invoked it.</span></span>  
  
     <span data-ttu-id="3a143-200">`Exit Property` Ve `Return` deyimleri neden hemen bir çıkış bir özellik yordam.</span><span class="sxs-lookup"><span data-stu-id="3a143-200">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="3a143-201">Herhangi bir sayıda `Exit Property` ve `Return` deyimleri yordamda herhangi bir yerinde görünebilir ve karıştırabilir miyim `Exit Property` ve `Return` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="3a143-201">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
-   <span data-ttu-id="3a143-202">**Dönüş değeri.**</span><span class="sxs-lookup"><span data-stu-id="3a143-202">**Return Value.**</span></span> <span data-ttu-id="3a143-203">Bir değer almak için bir `Get` yordamı, özellik adı değerini atayın veya olmasını bir `Return` deyimi.</span><span class="sxs-lookup"><span data-stu-id="3a143-203">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a `Return` statement.</span></span> <span data-ttu-id="3a143-204">Aşağıdaki örnek, özellik adı dönüş değeri atar `quoteForTheDay` ve ardından `Exit Property` dönmek için deyimi.</span><span class="sxs-lookup"><span data-stu-id="3a143-204">The following example assigns the return value to the property name `quoteForTheDay` and then uses the `Exit Property` statement to return.</span></span>  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#28](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_2.vb)]  
  
     <span data-ttu-id="3a143-205">Kullanırsanız `Exit Property` değerine atama olmadan `name`, `Get` yordamı özelliğin veri türü için varsayılan değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="3a143-205">If you use `Exit Property` without assigning a value to `name`, the `Get` procedure returns the default value for the property's data type.</span></span>  
  
     <span data-ttu-id="3a143-206">`Return` Deyimi aynı anda atar `Get` yordamı dönüş değeri ve yordamdan çıkar.</span><span class="sxs-lookup"><span data-stu-id="3a143-206">The `Return` statement at the same time assigns the `Get` procedure return value and exits the procedure.</span></span> <span data-ttu-id="3a143-207">Aşağıdaki örnekte bu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3a143-207">The following example shows this.</span></span>  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#29](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="3a143-208">Örnek</span><span class="sxs-lookup"><span data-stu-id="3a143-208">Example</span></span>  
 <span data-ttu-id="3a143-209">Aşağıdaki örnekte bir sınıftaki bir özelliği bildirir.</span><span class="sxs-lookup"><span data-stu-id="3a143-209">The following example declares a property in a class.</span></span>  
  
 [!code-vb[VbVbalrStatements#51](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="3a143-210">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3a143-210">See Also</span></span>  
 [<span data-ttu-id="3a143-211">Otomatik Uygulanan Özellikler</span><span class="sxs-lookup"><span data-stu-id="3a143-211">Auto-Implemented Properties</span></span>](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)  
 [<span data-ttu-id="3a143-212">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="3a143-212">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="3a143-213">Get Deyimi</span><span class="sxs-lookup"><span data-stu-id="3a143-213">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)  
 [<span data-ttu-id="3a143-214">Set Deyimi</span><span class="sxs-lookup"><span data-stu-id="3a143-214">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)  
 [<span data-ttu-id="3a143-215">Parametre Listesi</span><span class="sxs-lookup"><span data-stu-id="3a143-215">Parameter List</span></span>](../../../visual-basic/language-reference/statements/parameter-list.md)  
 [<span data-ttu-id="3a143-216">Default</span><span class="sxs-lookup"><span data-stu-id="3a143-216">Default</span></span>](../../../visual-basic/language-reference/modifiers/default.md)
