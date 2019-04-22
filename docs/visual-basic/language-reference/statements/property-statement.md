---
title: Property deyimi (Visual Basic)
ms.date: 05/12/2018
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
ms.openlocfilehash: 7b2d388cbcd1995178adf4102520ecaa1c9b1889
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814196"
---
# <a name="property-statement"></a><span data-ttu-id="3e1ea-102">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="3e1ea-102">Property Statement</span></span>
<span data-ttu-id="3e1ea-103">Adı bir özelliği ve depolamak ve özelliğin değerini almak için kullanılan özellik yordamlarını bildirir.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-103">Declares the name of a property, and the property procedures used to store and retrieve the value of the property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e1ea-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3e1ea-104">Syntax</span></span>  
  
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
  
## <a name="parts"></a><span data-ttu-id="3e1ea-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="3e1ea-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="3e1ea-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-106">Optional.</span></span> <span data-ttu-id="3e1ea-107">Bu özellik için geçerli olan özniteliklerin listesi veya `Get` veya `Set` yordamı.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-107">List of attributes that apply to this property or `Get` or `Set` procedure.</span></span> <span data-ttu-id="3e1ea-108">Bkz: [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="3e1ea-108">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
-   `Default`  
  
     <span data-ttu-id="3e1ea-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-109">Optional.</span></span> <span data-ttu-id="3e1ea-110">Bu özellik bir sınıf ya da yapı üzerinde tanımlandığı için varsayılan özelliği olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-110">Specifies that this property is the default property for the class or structure on which it is defined.</span></span> <span data-ttu-id="3e1ea-111">Varsayılan özellikleri parametreleri kabul etmeniz gerekir ve ayarlanabilir ve özellik adı belirtmeden alınır.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-111">Default properties must accept parameters and can be set and retrieved without specifying the property name.</span></span> <span data-ttu-id="3e1ea-112">Özellik olarak bildirirseniz `Default`, kullanamazsınız `Private` özelliği veya ya da kendi özellik yordamları.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-112">If you declare the property as `Default`, you cannot use `Private` on the property or on either of its property procedures.</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="3e1ea-113">İsteğe bağlı `Property` deyimi ve en fazla bir `Get` ve `Set` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-113">Optional on the `Property` statement and on at most one of the `Get` and `Set` statements.</span></span> <span data-ttu-id="3e1ea-114">Aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="3e1ea-114">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="3e1ea-115">Public</span><span class="sxs-lookup"><span data-stu-id="3e1ea-115">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="3e1ea-116">Protected</span><span class="sxs-lookup"><span data-stu-id="3e1ea-116">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="3e1ea-117">Friend</span><span class="sxs-lookup"><span data-stu-id="3e1ea-117">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="3e1ea-118">Private</span><span class="sxs-lookup"><span data-stu-id="3e1ea-118">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    - [<span data-ttu-id="3e1ea-119">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="3e1ea-119">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md) 

    - [<span data-ttu-id="3e1ea-120">Private Protected</span><span class="sxs-lookup"><span data-stu-id="3e1ea-120">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)
  
     <span data-ttu-id="3e1ea-121">Bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="3e1ea-121">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `propertymodifiers`  
  
     <span data-ttu-id="3e1ea-122">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-122">Optional.</span></span> <span data-ttu-id="3e1ea-123">Aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="3e1ea-123">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="3e1ea-124">Overloads</span><span class="sxs-lookup"><span data-stu-id="3e1ea-124">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [<span data-ttu-id="3e1ea-125">Overrides</span><span class="sxs-lookup"><span data-stu-id="3e1ea-125">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [<span data-ttu-id="3e1ea-126">Overridable</span><span class="sxs-lookup"><span data-stu-id="3e1ea-126">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [<span data-ttu-id="3e1ea-127">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="3e1ea-127">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [<span data-ttu-id="3e1ea-128">MustOverride</span><span class="sxs-lookup"><span data-stu-id="3e1ea-128">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     <span data-ttu-id="3e1ea-129">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-129">Optional.</span></span> <span data-ttu-id="3e1ea-130">Bkz: [paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="3e1ea-130">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="3e1ea-131">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-131">Optional.</span></span> <span data-ttu-id="3e1ea-132">Bkz: [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="3e1ea-132">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
-   `ReadOnly`  
  
     <span data-ttu-id="3e1ea-133">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-133">Optional.</span></span> <span data-ttu-id="3e1ea-134">Bkz: [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="3e1ea-134">See [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
-   `WriteOnly`  
  
     <span data-ttu-id="3e1ea-135">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-135">Optional.</span></span> <span data-ttu-id="3e1ea-136">Bkz: [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).</span><span class="sxs-lookup"><span data-stu-id="3e1ea-136">See [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).</span></span>  
  
-   `Iterator`  
  
     <span data-ttu-id="3e1ea-137">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-137">Optional.</span></span> <span data-ttu-id="3e1ea-138">Bkz: [yineleyici](../../../visual-basic/language-reference/modifiers/iterator.md).</span><span class="sxs-lookup"><span data-stu-id="3e1ea-138">See [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).</span></span>  
  
-   `name`  
  
     <span data-ttu-id="3e1ea-139">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-139">Required.</span></span> <span data-ttu-id="3e1ea-140">Özelliğin adı.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-140">Name of the property.</span></span> <span data-ttu-id="3e1ea-141">Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="3e1ea-141">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   `parameterlist`  
  
     <span data-ttu-id="3e1ea-142">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-142">Optional.</span></span> <span data-ttu-id="3e1ea-143">Bu özelliğin parametreleri ve olası ek parametrelerini temsil eden yerel değişken adlarının listesini `Set` yordamı.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-143">List of local variable names representing the parameters of this property, and possible additional parameters of the `Set` procedure.</span></span> <span data-ttu-id="3e1ea-144">Bkz: [parametre listesi](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="3e1ea-144">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>  
  
-   `returntype`  
  
     <span data-ttu-id="3e1ea-145">Gerekli if `Option Strict` olduğu `On`.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-145">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="3e1ea-146">Bu özellik tarafından döndürülen değerin veri türü.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-146">Data type of the value returned by this property.</span></span>  
  
-   `Implements`  
  
     <span data-ttu-id="3e1ea-147">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-147">Optional.</span></span> <span data-ttu-id="3e1ea-148">Bu özellik bir veya daha fazla özellik, her biri bu özelliğin içeren sınıf veya yapı tarafından uygulanan bir arabirim içinde tanımlanmış uygulayan gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-148">Indicates that this property implements one or more properties, each one defined in an interface implemented by this property's containing class or structure.</span></span> <span data-ttu-id="3e1ea-149">Bkz: [uygulayan deyimi](../../../visual-basic/language-reference/statements/implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3e1ea-149">See [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span>  
  
-   `implementslist`  
  
     <span data-ttu-id="3e1ea-150">Gerekli if `Implements` sağlanır.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-150">Required if `Implements` is supplied.</span></span> <span data-ttu-id="3e1ea-151">Uygulanan özelliklerin listesi.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-151">List of properties being implemented.</span></span>  
  
     `implementedproperty [ , implementedproperty ... ]`  
  
     <span data-ttu-id="3e1ea-152">Her `implementedproperty` aşağıdaki söz dizimini ve bölümleri vardır:</span><span class="sxs-lookup"><span data-stu-id="3e1ea-152">Each `implementedproperty` has the following syntax and parts:</span></span>  
  
     `interface.definedname`  
  
    |<span data-ttu-id="3e1ea-153">Bölümü</span><span class="sxs-lookup"><span data-stu-id="3e1ea-153">Part</span></span>|<span data-ttu-id="3e1ea-154">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3e1ea-154">Description</span></span>|  
    |---|---|  
    |`interface`|<span data-ttu-id="3e1ea-155">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-155">Required.</span></span> <span data-ttu-id="3e1ea-156">Bu özellik tarafından uygulanan arabirimin adını sınıf veya yapı içeren.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-156">Name of an interface implemented by this property's containing class or structure.</span></span>|  
    |`definedname`|<span data-ttu-id="3e1ea-157">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-157">Required.</span></span> <span data-ttu-id="3e1ea-158">Ad tarafından özelliği tanımlanan `interface`.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-158">Name by which the property is defined in `interface`.</span></span>|  
  
-   `Get`  
  
     <span data-ttu-id="3e1ea-159">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-159">Optional.</span></span> <span data-ttu-id="3e1ea-160">Özellik işaretlenmişse gerekli `WriteOnly`.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-160">Required if the property is marked `WriteOnly`.</span></span> <span data-ttu-id="3e1ea-161">Başlatan bir `Get` özelliğinin değeri döndürmek için kullanılan bir özellik yordamı.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-161">Starts a `Get` property procedure that is used to return the value of the property.</span></span>  
  
-   `statements`  
  
     <span data-ttu-id="3e1ea-162">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-162">Optional.</span></span> <span data-ttu-id="3e1ea-163">İçinde çalıştırılacak deyimler bloğunu `Get` veya `Set` yordamı.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-163">Block of statements to run within the `Get` or `Set` procedure.</span></span>  
  
-   `End Get`  
  
     <span data-ttu-id="3e1ea-164">Sonlandırır `Get` özellik yordamı.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-164">Terminates the `Get` property procedure.</span></span>  
  
-   `Set`  
  
     <span data-ttu-id="3e1ea-165">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-165">Optional.</span></span> <span data-ttu-id="3e1ea-166">Özellik işaretlenmişse gerekli `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-166">Required if the property is marked `ReadOnly`.</span></span> <span data-ttu-id="3e1ea-167">Başlatan bir `Set` özellik değerini depolamak için kullanılan bir özellik yordamı.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-167">Starts a `Set` property procedure that is used to store the value of the property.</span></span>  
  
-   `End Set`  
  
     <span data-ttu-id="3e1ea-168">Sonlandırır `Set` özellik yordamı.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-168">Terminates the `Set` property procedure.</span></span>  
  
-   `End Property`  
  
     <span data-ttu-id="3e1ea-169">Bu özelliğin tanımını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-169">Terminates the definition of this property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e1ea-170">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3e1ea-170">Remarks</span></span>  
 <span data-ttu-id="3e1ea-171">`Property` Deyimi, özelliğin bildirimini sunar.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-171">The `Property` statement introduces the declaration of a property.</span></span> <span data-ttu-id="3e1ea-172">Bir özelliğin sahip olabileceği bir `Get` yordamı (salt okunur), bir `Set` yordamı (salt okunur) veya her iki (okuma ve yazma).</span><span class="sxs-lookup"><span data-stu-id="3e1ea-172">A property can have a `Get` procedure (read only), a `Set` procedure (write only), or both (read-write).</span></span> <span data-ttu-id="3e1ea-173">Atlayabilirsiniz `Get` ve `Set` otomatik uygulanan bir özellik kullanıldığında yordamı.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-173">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="3e1ea-174">Daha fazla bilgi için [Implemented Properties](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="3e1ea-174">For more information, see [Auto-Implemented Properties](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>  
  
 <span data-ttu-id="3e1ea-175">Kullanabileceğiniz `Property` yalnızca sınıf düzeyinde.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-175">You can use `Property` only at class level.</span></span> <span data-ttu-id="3e1ea-176">Başka bir deyişle *bildirim içeriğinin* bir özellik bir sınıf, yapı, modül veya arabirimi olması gerekir ve bir kaynak dosyası, ad alanı, yordam veya blok olamayacağı için.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-176">This means the *declaration context* for a property must be a class, structure, module, or interface, and cannot be a source file, namespace, procedure, or block.</span></span> <span data-ttu-id="3e1ea-177">Daha fazla bilgi için [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="3e1ea-177">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="3e1ea-178">Varsayılan olarak, genel erişim özelliklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-178">By default, properties use public access.</span></span> <span data-ttu-id="3e1ea-179">Bir özelliğin erişim düzeyiyle bir erişim değiştiricisidir düzenleyebilirsiniz `Property` deyimi ve isteğe bağlı olarak ayarlayabilir, özellik yordamları daha kısıtlayıcı bir erişim düzeyi.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-179">You can adjust a property's access level with an access modifier on the `Property` statement, and you can optionally adjust one of its property procedures to a more restrictive access level.</span></span>  
  
 <span data-ttu-id="3e1ea-180">Visual Basic için bir parametre geçirir `Set` yordam sırasında özelliği atamaları.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-180">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="3e1ea-181">İçin bir parametre belirtmezseniz `Set`, tümleşik geliştirme ortamı (IDE) adlı bir örtük parametresini kullanan `value`.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-181">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="3e1ea-182">Bu parametre, özelliğe atanacak değer tutar.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-182">This parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="3e1ea-183">Genellikle bu değer özel bir yerel değişkene depolayın ve döndürün. her `Get` yordamı çağrılır.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-183">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="3e1ea-184">Kurallar</span><span class="sxs-lookup"><span data-stu-id="3e1ea-184">Rules</span></span>  
  
-   <span data-ttu-id="3e1ea-185">**Karışık erişim düzeyleri.**</span><span class="sxs-lookup"><span data-stu-id="3e1ea-185">**Mixed Access Levels.**</span></span> <span data-ttu-id="3e1ea-186">Okuma-yazma özelliği tanımlıyorsanız, isteğe bağlı olarak farklı erişim düzeyi için belirtebilirsiniz `Get` veya `Set` yordamı, ancak ikisine birden değil.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-186">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="3e1ea-187">Bunu yaparsanız, yordam erişim düzeyi özellik erişim düzeyinden daha kısıtlayıcı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-187">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="3e1ea-188">Örneğin, özellik bildirilirse `Friend`, bildirebilirsiniz `Set` yordamı `Private`, ama `Public`.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-188">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="3e1ea-189">Tanımlıyorsanız, bir `ReadOnly` veya `WriteOnly` özelliği, tek bir özellik yordamı (`Get` veya `Set`sırasıyla) tüm özelliği temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-189">If you are defining a `ReadOnly` or `WriteOnly` property, the single property procedure (`Get` or `Set`, respectively) represents all of the property.</span></span> <span data-ttu-id="3e1ea-190">İki erişim düzeyi özelliği ayarlamanız gerekir çünkü bu tür bir yordam için bir farklı erişim düzeyi bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-190">You cannot declare a different access level for such a procedure, because that would set two access levels for the property.</span></span>  
  
-   <span data-ttu-id="3e1ea-191">**Dönüş türü.**</span><span class="sxs-lookup"><span data-stu-id="3e1ea-191">**Return Type.**</span></span> <span data-ttu-id="3e1ea-192">`Property` Deyimi döndürdüğü değerin veri türü bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-192">The `Property` statement can declare the data type of the value it returns.</span></span> <span data-ttu-id="3e1ea-193">Herhangi bir veri türü veya bir sabit listesi, yapısı, sınıf veya arabirim adını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-193">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
     <span data-ttu-id="3e1ea-194">Siz belirtmezseniz `returntype`, özellik döndürür `Object`.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-194">If you do not specify `returntype`, the property returns `Object`.</span></span>  
  
-   <span data-ttu-id="3e1ea-195">**Uygulama.**</span><span class="sxs-lookup"><span data-stu-id="3e1ea-195">**Implementation.**</span></span> <span data-ttu-id="3e1ea-196">Bu özellik kullanıyorsa `Implements` anahtar sözcüğü, kapsayan sınıf veya yapı olmalıdır bir `Implements` hemen deyimi, `Class` veya `Structure` deyimi.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-196">If this property uses the `Implements` keyword, the containing class or structure must have an `Implements` statement immediately following its `Class` or `Structure` statement.</span></span> <span data-ttu-id="3e1ea-197">`Implements` Deyimi belirttiğiniz her arabirim içermelidir `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-197">The `Implements` statement must include each interface specified in `implementslist`.</span></span> <span data-ttu-id="3e1ea-198">Ancak, bir arabirim tarafından tanımlayan adı `Property` (içinde `definedname`) bu özelliğin adı ile aynı olması gerekmez (içinde `name`).</span><span class="sxs-lookup"><span data-stu-id="3e1ea-198">However, the name by which an interface defines the `Property` (in `definedname`) does not have to be the same as the name of this property (in `name`).</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="3e1ea-199">Davranış</span><span class="sxs-lookup"><span data-stu-id="3e1ea-199">Behavior</span></span>  
  
-   <span data-ttu-id="3e1ea-200">**Bir özellik yordamı döndürüyor.**</span><span class="sxs-lookup"><span data-stu-id="3e1ea-200">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="3e1ea-201">Zaman `Get` veya `Set` yordamı çağıran koda döndürür, kendisini çağıran deyiminin sonrasındaki deyime ile yürütme devam eder.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-201">When the `Get` or `Set` procedure returns to the calling code, execution continues with the statement following the statement that invoked it.</span></span>  
  
     <span data-ttu-id="3e1ea-202">`Exit Property` Ve `Return` deyimleri neden hemen bir çıkış bir özellik yordamı.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-202">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="3e1ea-203">Herhangi bir sayıda `Exit Property` ve `Return` deyimleri yordamda herhangi bir yerinde görünebilir ve karıştırabilir miyim `Exit Property` ve `Return` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-203">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
-   <span data-ttu-id="3e1ea-204">**Dönüş değeri.**</span><span class="sxs-lookup"><span data-stu-id="3e1ea-204">**Return Value.**</span></span> <span data-ttu-id="3e1ea-205">Bir değer döndürmek için bir `Get` yordam, özellik adı için değer atamak veya olmasını bir `Return` deyimi.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-205">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a `Return` statement.</span></span> <span data-ttu-id="3e1ea-206">Aşağıdaki örnek, özellik adı için dönüş değeri atar `quoteForTheDay` ve ardından `Exit Property` döndürülecek deyimi.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-206">The following example assigns the return value to the property name `quoteForTheDay` and then uses the `Exit Property` statement to return.</span></span>  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]  
  
     <span data-ttu-id="3e1ea-207">Kullanırsanız `Exit Property` değerine atama olmadan `name`, `Get` yordamı özelliğin veri türü için varsayılan değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-207">If you use `Exit Property` without assigning a value to `name`, the `Get` procedure returns the default value for the property's data type.</span></span>  
  
     <span data-ttu-id="3e1ea-208">`Return` Deyimi aynı anda atar `Get` yordamı dönüş değeri ve yordamdan çıkar.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-208">The `Return` statement at the same time assigns the `Get` procedure return value and exits the procedure.</span></span> <span data-ttu-id="3e1ea-209">Aşağıdaki örnekte bu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-209">The following example shows this.</span></span>  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]  
  
## <a name="example"></a><span data-ttu-id="3e1ea-210">Örnek</span><span class="sxs-lookup"><span data-stu-id="3e1ea-210">Example</span></span>  
 <span data-ttu-id="3e1ea-211">Aşağıdaki örnek, bir sınıftaki bir özelliği bildirir.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-211">The following example declares a property in a class.</span></span>  
  
 [!code-vb[VbVbalrStatements#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#51)]  
  
## <a name="see-also"></a><span data-ttu-id="3e1ea-212">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e1ea-212">See also</span></span>

- [<span data-ttu-id="3e1ea-213">Otomatik Uygulanan Özellikler</span><span class="sxs-lookup"><span data-stu-id="3e1ea-213">Auto-Implemented Properties</span></span>](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)
- [<span data-ttu-id="3e1ea-214">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="3e1ea-214">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="3e1ea-215">Get Deyimi</span><span class="sxs-lookup"><span data-stu-id="3e1ea-215">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="3e1ea-216">Set Deyimi</span><span class="sxs-lookup"><span data-stu-id="3e1ea-216">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
- [<span data-ttu-id="3e1ea-217">Parametre Listesi</span><span class="sxs-lookup"><span data-stu-id="3e1ea-217">Parameter List</span></span>](../../../visual-basic/language-reference/statements/parameter-list.md)
- [<span data-ttu-id="3e1ea-218">Default</span><span class="sxs-lookup"><span data-stu-id="3e1ea-218">Default</span></span>](../../../visual-basic/language-reference/modifiers/default.md)
