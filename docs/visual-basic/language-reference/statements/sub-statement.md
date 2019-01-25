---
title: Sub Deyimi (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Sub
helpviewer_keywords:
- Public keyword [Visual Basic], Sub statements
- procedures [Visual Basic], creating
- declaring procedures [Visual Basic], Sub statement
- arguments [Visual Basic], Sub procedures
- As keyword [Visual Basic], Sub statements
- Optional keyword [Visual Basic], Sub statements
- declarations [Visual Basic], procedures
- Sub keyword [Visual Basic]
- Handles keyword [Visual Basic], Sub statements
- Protected Friend keyword [Visual Basic]
- ParamArray keyword [Visual Basic], Sub statements
- Implements keyword [Visual Basic], Sub statements
- Sub statement [Visual Basic]
- subroutines
- ByRef keyword [Visual Basic], Sub statements
- Sub procedures [Visual Basic], Sub statement
- recursive procedures
- Private keyword [Visual Basic], Sub statements
- Friend keyword [Visual Basic], Sub statements
- Exit statement [Visual Basic], Sub statements
- procedures [Visual Basic], Sub
- End keyword [Visual Basic], Sub statements
- ByVal keyword [Visual Basic], Sub statements
- Visual Basic code, Sub procedures
ms.assetid: e347d700-d06c-405b-b302-e9b1edb57dfc
ms.openlocfilehash: e7015474a0617b76ca537d2e84e8d7bfc72b6e12
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737669"
---
# <a name="sub-statement-visual-basic"></a><span data-ttu-id="d3512-102">Sub Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d3512-102">Sub Statement (Visual Basic)</span></span>
<span data-ttu-id="d3512-103">Adı, parametreleri ve kodu tanımlayan bildirir bir `Sub` yordamı.</span><span class="sxs-lookup"><span data-stu-id="d3512-103">Declares the name, parameters, and code that define a `Sub` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3512-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d3512-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]  
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]  
    [ statements ]  
    [ Exit Sub ]  
    [ statements ]  
End Sub  
```  
  
## <a name="parts"></a><span data-ttu-id="d3512-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="d3512-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="d3512-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d3512-106">Optional.</span></span> <span data-ttu-id="d3512-107">Bkz: [öznitelik listesi](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="d3512-107">See [Attribute List](attribute-list.md).</span></span>  
  
-   `Partial`  
  
     <span data-ttu-id="d3512-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d3512-108">Optional.</span></span> <span data-ttu-id="d3512-109">Kısmi bir yöntemin tanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d3512-109">Indicates definition of a partial method.</span></span> <span data-ttu-id="d3512-110">Bkz: [kısmi yöntemler](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).</span><span class="sxs-lookup"><span data-stu-id="d3512-110">See [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="d3512-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d3512-111">Optional.</span></span> <span data-ttu-id="d3512-112">Aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="d3512-112">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="d3512-113">Public</span><span class="sxs-lookup"><span data-stu-id="d3512-113">Public</span></span>](../modifiers/public.md)  
  
    -   [<span data-ttu-id="d3512-114">Protected</span><span class="sxs-lookup"><span data-stu-id="d3512-114">Protected</span></span>](../modifiers/protected.md)  
  
    -   [<span data-ttu-id="d3512-115">Friend</span><span class="sxs-lookup"><span data-stu-id="d3512-115">Friend</span></span>](../modifiers/friend.md)  
  
    -   [<span data-ttu-id="d3512-116">Private</span><span class="sxs-lookup"><span data-stu-id="d3512-116">Private</span></span>](../modifiers/private.md)  
  
    - [<span data-ttu-id="d3512-117">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="d3512-117">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md)

    - [<span data-ttu-id="d3512-118">Private Protected</span><span class="sxs-lookup"><span data-stu-id="d3512-118">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)
  
     <span data-ttu-id="d3512-119">Bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="d3512-119">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `proceduremodifiers`  
  
     <span data-ttu-id="d3512-120">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d3512-120">Optional.</span></span> <span data-ttu-id="d3512-121">Aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="d3512-121">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="d3512-122">Overloads</span><span class="sxs-lookup"><span data-stu-id="d3512-122">Overloads</span></span>](../modifiers/overloads.md)  
  
    -   [<span data-ttu-id="d3512-123">Overrides</span><span class="sxs-lookup"><span data-stu-id="d3512-123">Overrides</span></span>](../modifiers/overrides.md)  
  
    -   [<span data-ttu-id="d3512-124">Overridable</span><span class="sxs-lookup"><span data-stu-id="d3512-124">Overridable</span></span>](../modifiers/overridable.md)  
  
    -   [<span data-ttu-id="d3512-125">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="d3512-125">NotOverridable</span></span>](../modifiers/notoverridable.md)  
  
    -   [<span data-ttu-id="d3512-126">MustOverride</span><span class="sxs-lookup"><span data-stu-id="d3512-126">MustOverride</span></span>](../modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     <span data-ttu-id="d3512-127">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d3512-127">Optional.</span></span> <span data-ttu-id="d3512-128">Bkz: [paylaşılan](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="d3512-128">See [Shared](../modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="d3512-129">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d3512-129">Optional.</span></span> <span data-ttu-id="d3512-130">Bkz: [Shadows](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="d3512-130">See [Shadows](../modifiers/shadows.md).</span></span>  
  
-   `Async`  
  
     <span data-ttu-id="d3512-131">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d3512-131">Optional.</span></span> <span data-ttu-id="d3512-132">Bkz: [zaman uyumsuz](../modifiers/async.md).</span><span class="sxs-lookup"><span data-stu-id="d3512-132">See [Async](../modifiers/async.md).</span></span>  
  
-   `name`  
  
     <span data-ttu-id="d3512-133">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="d3512-133">Required.</span></span> <span data-ttu-id="d3512-134">Yordamın adı.</span><span class="sxs-lookup"><span data-stu-id="d3512-134">Name of the procedure.</span></span> <span data-ttu-id="d3512-135">Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="d3512-135">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span> <span data-ttu-id="d3512-136">Bir sınıf için bir oluşturucu yordam oluşturmak için kümesinin adı bir `Sub` yordama `New` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="d3512-136">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="d3512-137">Daha fazla bilgi için [nesne ömrü: Nesneler nasıl oluşturulur ve imha](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="d3512-137">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>  
  
-   `typeparamlist`  
  
     <span data-ttu-id="d3512-138">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d3512-138">Optional.</span></span> <span data-ttu-id="d3512-139">Genel bir yordam için tür parametreleri listesi.</span><span class="sxs-lookup"><span data-stu-id="d3512-139">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="d3512-140">Bkz: [türü listesinde](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="d3512-140">See [Type List](type-list.md).</span></span>  
  
-   `parameterlist`  
  
     <span data-ttu-id="d3512-141">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d3512-141">Optional.</span></span> <span data-ttu-id="d3512-142">Bu yordamı parametrelerini temsil eden yerel değişken adlarının listesi.</span><span class="sxs-lookup"><span data-stu-id="d3512-142">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="d3512-143">Bkz: [parametre listesi](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="d3512-143">See [Parameter List](parameter-list.md).</span></span>  
  
-   `Implements`  
  
     <span data-ttu-id="d3512-144">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d3512-144">Optional.</span></span> <span data-ttu-id="d3512-145">Bu yordam bir veya daha fazla uyguladığını belirtir `Sub` yordamları, bu yordamın içeren sınıf veya yapı tarafından uygulanan bir arabirim içinde tanımlanmış her biri.</span><span class="sxs-lookup"><span data-stu-id="d3512-145">Indicates that this procedure implements one or more `Sub` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="d3512-146">Bkz: [uygulayan deyimi](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d3512-146">See [Implements Statement](implements-statement.md).</span></span>  
  
-   `implementslist`  
  
     <span data-ttu-id="d3512-147">Gerekli if `Implements` sağlanır.</span><span class="sxs-lookup"><span data-stu-id="d3512-147">Required if `Implements` is supplied.</span></span> <span data-ttu-id="d3512-148">Listesi `Sub` uygulanmakta olan yordamlar.</span><span class="sxs-lookup"><span data-stu-id="d3512-148">List of `Sub` procedures being implemented.</span></span>  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     <span data-ttu-id="d3512-149">Her `implementedprocedure` aşağıdaki söz dizimini ve bölümleri vardır:</span><span class="sxs-lookup"><span data-stu-id="d3512-149">Each `implementedprocedure` has the following syntax and parts:</span></span>  
  
     `interface.definedname`  
  
    |<span data-ttu-id="d3512-150">Bölümü</span><span class="sxs-lookup"><span data-stu-id="d3512-150">Part</span></span>|<span data-ttu-id="d3512-151">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3512-151">Description</span></span>|  
    |---|---|  
    |`interface`|<span data-ttu-id="d3512-152">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="d3512-152">Required.</span></span> <span data-ttu-id="d3512-153">Bu yordam tarafından uygulanan arabirimin adını sınıf veya yapı içeren.</span><span class="sxs-lookup"><span data-stu-id="d3512-153">Name of an interface implemented by this procedure's containing class or structure.</span></span>|  
    |`definedname`|<span data-ttu-id="d3512-154">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="d3512-154">Required.</span></span> <span data-ttu-id="d3512-155">Ad tarafından yordamı tanımlanan `interface`.</span><span class="sxs-lookup"><span data-stu-id="d3512-155">Name by which the procedure is defined in `interface`.</span></span>|  
  
-   `Handles`  
  
     <span data-ttu-id="d3512-156">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d3512-156">Optional.</span></span> <span data-ttu-id="d3512-157">Bu yordam, bir veya daha fazla belirli olayları işleyebileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d3512-157">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="d3512-158">Bkz: [işler](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="d3512-158">See [Handles](handles-clause.md).</span></span>  
  
-   `eventlist`  
  
     <span data-ttu-id="d3512-159">Gerekli if `Handles` sağlanır.</span><span class="sxs-lookup"><span data-stu-id="d3512-159">Required if `Handles` is supplied.</span></span> <span data-ttu-id="d3512-160">Bu yordamı işleme olayların listesi.</span><span class="sxs-lookup"><span data-stu-id="d3512-160">List of events this procedure handles.</span></span>  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     <span data-ttu-id="d3512-161">Her `eventspecifier` aşağıdaki söz dizimini ve bölümleri vardır:</span><span class="sxs-lookup"><span data-stu-id="d3512-161">Each `eventspecifier` has the following syntax and parts:</span></span>  
  
     `eventvariable.event`  
  
    |<span data-ttu-id="d3512-162">Bölümü</span><span class="sxs-lookup"><span data-stu-id="d3512-162">Part</span></span>|<span data-ttu-id="d3512-163">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3512-163">Description</span></span>|  
    |---|---|  
    |`eventvariable`|<span data-ttu-id="d3512-164">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="d3512-164">Required.</span></span> <span data-ttu-id="d3512-165">Nesne değişkeni sınıfın veya olayı yükselten yapı veri türü ile bildirilmiş.</span><span class="sxs-lookup"><span data-stu-id="d3512-165">Object variable declared with the data type of the class or structure that raises the event.</span></span>|  
    |`event`|<span data-ttu-id="d3512-166">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="d3512-166">Required.</span></span> <span data-ttu-id="d3512-167">Bu yordamı işleme olayın adı.</span><span class="sxs-lookup"><span data-stu-id="d3512-167">Name of the event this procedure handles.</span></span>|  
  
-   `statements`  
  
     <span data-ttu-id="d3512-168">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d3512-168">Optional.</span></span> <span data-ttu-id="d3512-169">Bu yordam içinde çalıştırılacak deyimler bloğunu.</span><span class="sxs-lookup"><span data-stu-id="d3512-169">Block of statements to run within this procedure.</span></span>  
  
-   `End Sub`  
  
     <span data-ttu-id="d3512-170">Bu yordamın tanımını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="d3512-170">Terminates the definition of this procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3512-171">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d3512-171">Remarks</span></span>  
 <span data-ttu-id="d3512-172">Tüm yürütülebilir kod yordam içinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d3512-172">All executable code must be inside a procedure.</span></span> <span data-ttu-id="d3512-173">Kullanım bir `Sub` çağrıldığı koda bir değer döndürmesi istemediğinizde yordamı.</span><span class="sxs-lookup"><span data-stu-id="d3512-173">Use a `Sub` procedure when you don't want to return a value to the calling code.</span></span> <span data-ttu-id="d3512-174">Kullanım bir `Function` yordamı, bir değer döndürmek istediğinizde.</span><span class="sxs-lookup"><span data-stu-id="d3512-174">Use a `Function` procedure when you want to return a value.</span></span>  
  
## <a name="defining-a-sub-procedure"></a><span data-ttu-id="d3512-175">Bir alt yordam tanımlama</span><span class="sxs-lookup"><span data-stu-id="d3512-175">Defining a Sub Procedure</span></span>  
 <span data-ttu-id="d3512-176">Tanımlayabileceğiniz bir `Sub` yordamı yalnızca Modül düzeyinde.</span><span class="sxs-lookup"><span data-stu-id="d3512-176">You can define a `Sub` procedure only at the module level.</span></span> <span data-ttu-id="d3512-177">Bir alt yordam bildirimi bağlamı, bu nedenle, bir sınıf, yapı, modül veya bir arabirim olmalıdır ve bir kaynak dosyası, bir ad alanı, bir yordam veya bir bloğu olamaz.</span><span class="sxs-lookup"><span data-stu-id="d3512-177">The declaration context for a sub procedure must, therefore, be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="d3512-178">Daha fazla bilgi için [bildirim bağlamları ve varsayılan erişim düzeyleri](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="d3512-178">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="d3512-179">`Sub` yordamları varsayılan genel erişim için.</span><span class="sxs-lookup"><span data-stu-id="d3512-179">`Sub` procedures default to public access.</span></span> <span data-ttu-id="d3512-180">Erişim değiştiricileri kullanarak, kullanıcıların erişim düzeylerini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3512-180">You can adjust their access levels by using the access modifiers.</span></span>  
  
 <span data-ttu-id="d3512-181">Yordamı kullanıyorsa `Implements` anahtar sözcüğü, kapsayan sınıf veya yapı olmalıdır bir `Implements` deyim indisinin hemen ardından kendi `Class` veya `Structure` deyimi.</span><span class="sxs-lookup"><span data-stu-id="d3512-181">If the procedure uses the `Implements` keyword, the containing class or structure must have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="d3512-182">`Implements` Deyimi, belirtilen her bir arabirime içermelidir `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="d3512-182">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="d3512-183">Ancak, bir arabirim tarafından tanımlayan adı `Sub` (içinde `definedname`) bu yordamı adıyla eşleşmesi gerekmez (içinde `name`).</span><span class="sxs-lookup"><span data-stu-id="d3512-183">However, the name by which an interface defines the `Sub` (in `definedname`) doesn't have to match the name of this procedure (in `name`).</span></span>  
  
## <a name="returning-from-a-sub-procedure"></a><span data-ttu-id="d3512-184">Bir alt yordamdan döndürme</span><span class="sxs-lookup"><span data-stu-id="d3512-184">Returning from a Sub Procedure</span></span>  
 <span data-ttu-id="d3512-185">Olduğunda bir `Sub` yordamı çağıran koda döndürür, yürütme adlı deyiminden sonraki ile devam eder.</span><span class="sxs-lookup"><span data-stu-id="d3512-185">When a `Sub` procedure returns to the calling code, execution continues with the statement after the statement that called it.</span></span>  
  
 <span data-ttu-id="d3512-186">Aşağıdaki örnek, geri döndürme gösterir. bir `Sub` yordamı.</span><span class="sxs-lookup"><span data-stu-id="d3512-186">The following example shows a return from a `Sub` procedure.</span></span>  
  
```vb  
Sub mySub(ByVal q As String)  
    Return  
End Sub   
```  
  
 <span data-ttu-id="d3512-187">`Exit Sub` Ve `Return` deyimleri neden hemen çıkılmadan bir `Sub` yordamı.</span><span class="sxs-lookup"><span data-stu-id="d3512-187">The `Exit Sub` and `Return` statements cause an immediate exit from a `Sub` procedure.</span></span> <span data-ttu-id="d3512-188">Herhangi bir sayıda `Exit Sub` ve `Return` deyimleri yordamda herhangi bir yerinde görünebilir ve karıştırabilir miyim `Exit Sub` ve `Return` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="d3512-188">Any number of `Exit Sub` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Sub` and `Return` statements.</span></span>  
  
## <a name="calling-a-sub-procedure"></a><span data-ttu-id="d3512-189">Bir alt yordam çağırma</span><span class="sxs-lookup"><span data-stu-id="d3512-189">Calling a Sub Procedure</span></span>  
 <span data-ttu-id="d3512-190">Çağrısı bir `Sub` yordam adı bir deyimde kullanarak ve ardından bu ada sahip, bağımsız değişken listesi parantez içinde aşağıdaki yordamı.</span><span class="sxs-lookup"><span data-stu-id="d3512-190">You call a `Sub` procedure by using the procedure name in a statement and then following that name with its argument list in parentheses.</span></span> <span data-ttu-id="d3512-191">Herhangi bir bağımsız değişkeni belirtmezseniz ayraçları atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3512-191">You can omit the parentheses only if you don't supply any arguments.</span></span> <span data-ttu-id="d3512-192">Ancak, kodunuz her zaman parantezler eklerseniz daha okunabilir olur.</span><span class="sxs-lookup"><span data-stu-id="d3512-192">However, your code is more readable if you always include the parentheses.</span></span>  
  
 <span data-ttu-id="d3512-193">A `Sub` yordam ve `Function` yordam parametreleri ve bir dizi deyim gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="d3512-193">A `Sub` procedure and a `Function` procedure  can have parameters and perform a series of statements.</span></span> <span data-ttu-id="d3512-194">Ancak, bir `Function` yordamı döndürür bir değer ve bir `Sub` yordamı değil.</span><span class="sxs-lookup"><span data-stu-id="d3512-194">However, a `Function` procedure returns a value, and a `Sub` procedure doesn't.</span></span> <span data-ttu-id="d3512-195">Bu nedenle, kullanamazsınız bir `Sub` yordamda bir ifade.</span><span class="sxs-lookup"><span data-stu-id="d3512-195">Therefore, you can't use a `Sub` procedure in an expression.</span></span>  
  
 <span data-ttu-id="d3512-196">Kullanabileceğiniz `Call` çağırdığınızda anahtar sözcüğü bir `Sub` yordamı, ancak bu anahtar sözcüğü birçok kullanım için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="d3512-196">You can use the `Call` keyword when you call a `Sub` procedure, but that keyword isn't recommended for most uses.</span></span> <span data-ttu-id="d3512-197">Daha fazla bilgi için [Call deyimi](call-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d3512-197">For more information, see [Call Statement](call-statement.md).</span></span>  
  
 <span data-ttu-id="d3512-198">Visual Basic, aritmetik ifadeler iç verimliliğini artırmak için bazen yeniden düzenler.</span><span class="sxs-lookup"><span data-stu-id="d3512-198">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="d3512-199">Diğer yordamlar çağrı ifadeleri, bağımsız değişken listesi içeriyorsa, bu nedenle, söz konusu ifadelerden belirli bir sırada çağrılacak varsayılır olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="d3512-199">For that reason, if your argument list includes expressions that call other procedures, you shouldn't assume that those expressions will be called in a particular order.</span></span>  
  
## <a name="async-sub-procedures"></a><span data-ttu-id="d3512-200">Zaman uyumsuz alt yordamlar</span><span class="sxs-lookup"><span data-stu-id="d3512-200">Async Sub Procedures</span></span>  
 <span data-ttu-id="d3512-201">Zaman uyumsuz özelliğini kullanarak, açık geri çağırmaları kullanarak veya kodunuzun birden çok işlevleri veya lambda ifadelerinde el ile bölme olmadan zaman uyumsuz işlevleri çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3512-201">By using the Async feature, you can invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>  
  
 <span data-ttu-id="d3512-202">Bir yordam ile işaretlerseniz [zaman uyumsuz](../modifiers/async.md) kullanabileceğiniz değiştiricisi [Await](../../../visual-basic/language-reference/operators/await-operator.md) yordamda işleci.</span><span class="sxs-lookup"><span data-stu-id="d3512-202">If you mark a procedure with the [Async](../modifiers/async.md) modifier, you can use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in the procedure.</span></span> <span data-ttu-id="d3512-203">Ulaştığında denetlemek bir `Await` ifadesinde `Async` yordam, Denetim çağırana döner ve awaited görevi tamamlanıncaya kadar yordamı ediyor askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="d3512-203">When control reaches an `Await` expression in the `Async` procedure, control returns to the caller, and progress in the procedure is suspended until the awaited task completes.</span></span> <span data-ttu-id="d3512-204">Görev tamamlandığında, yürütme yordamda devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="d3512-204">When the task is complete, execution can resume in the procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d3512-205">Bir `Async` yordamı döndürür henüz tam olmadığı ya da ilk beklenen nesne karşılaşıldığında çağıran ya da sonunda `Async` yordamı ulaşıldığında, hangisi daha önce gerçekleşirse.</span><span class="sxs-lookup"><span data-stu-id="d3512-205">An `Async` procedure returns to the caller when either the first awaited object that’s not yet complete is encountered or the end of the `Async` procedure is reached, whichever occurs first.</span></span>  
  
 <span data-ttu-id="d3512-206">Ayrıca işaretleyebilirsiniz bir [Function deyimi](function-statement.md) ile `Async` değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="d3512-206">You can also mark a [Function Statement](function-statement.md) with the `Async` modifier.</span></span> <span data-ttu-id="d3512-207">Bir `Async` işlevi dönüş türüne sahip <xref:System.Threading.Tasks.Task%601> veya <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="d3512-207">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="d3512-208">Bu konuda gösteren bir örnek daha sonra söz bir `Async` dönüş türü olan işlev <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="d3512-208">An example later in this topic shows an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
 <span data-ttu-id="d3512-209">`Async` `Sub` yordamları, burada bir değer döndürülemez için olay işleyicileri, öncelikli olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d3512-209">`Async` `Sub` procedures are primarily used for event handlers, where a value can't be returned.</span></span> <span data-ttu-id="d3512-210">Bir `Async` `Sub` yordamı beklenemez ve çağıran bir `Async` `Sub` yordamı catch özel durumları olamaz, `Sub` yordam oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d3512-210">An `Async` `Sub` procedure can't be awaited, and the caller of an `Async` `Sub` procedure can't catch exceptions that the `Sub` procedure throws.</span></span>  
  
 <span data-ttu-id="d3512-211">Bir `Async` yordamı herhangi bildiremez [ByRef](../modifiers/byref.md) parametreleri.</span><span class="sxs-lookup"><span data-stu-id="d3512-211">An `Async` procedure can't declare any [ByRef](../modifiers/byref.md) parameters.</span></span>  
  
 <span data-ttu-id="d3512-212">Hakkında daha fazla bilgi için `Async` prosedürler [Async ve Await ile zaman uyumsuz programlama](../../../visual-basic/programming-guide/concepts/async/index.md), [zaman uyumsuz programlarda akış kontrolü](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), ve [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="d3512-212">For more information about `Async` procedures, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3512-213">Örnek</span><span class="sxs-lookup"><span data-stu-id="d3512-213">Example</span></span>  
 <span data-ttu-id="d3512-214">Aşağıdaki örnekte `Sub` adı, parametreleri ve gövdesini kodunu tanımlamak için deyimi bir `Sub` yordamı.</span><span class="sxs-lookup"><span data-stu-id="d3512-214">The following example uses the `Sub` statement to define the name, parameters, and code that form the body of a `Sub` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#58](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/sub-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="d3512-215">Örnek</span><span class="sxs-lookup"><span data-stu-id="d3512-215">Example</span></span>  
 <span data-ttu-id="d3512-216">Aşağıdaki örnekte, `DelayAsync` olduğu bir `Async` `Function` dönüş türü olan <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="d3512-216">In the following example, `DelayAsync` is an `Async` `Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="d3512-217">`DelayAsync` sahip bir `Return` deyimi bir tamsayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="d3512-217">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="d3512-218">Bu nedenle, işlev bildirimi `DelayAsync` dönüş türüne sahip olmalıdır `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="d3512-218">Therefore, the function declaration of `DelayAsync` must have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="d3512-219">Dönüş türü olduğundan `Task(Of Integer)`, değerlendirmesi `Await` ifadesinde `DoSomethingAsync` aşağıdaki deyimi gösterildiği gibi bir tamsayı üretir: `Dim result As Integer = Await delayTask`.</span><span class="sxs-lookup"><span data-stu-id="d3512-219">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer, as the following statement shows: `Dim result As Integer = Await delayTask`.</span></span>  
  
 <span data-ttu-id="d3512-220">`startButton_Click` Yordamdır örneği bir `Async Sub` yordamı.</span><span class="sxs-lookup"><span data-stu-id="d3512-220">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="d3512-221">Çünkü `DoSomethingAsync` olduğu bir `Async` işlevi, görev için yapılan çağrının `DoSomethingAsync` , aşağıdaki deyimi gösterildiği gibi beklenmesini gerekir: `Await DoSomethingAsync()`.</span><span class="sxs-lookup"><span data-stu-id="d3512-221">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement shows: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="d3512-222">`startButton_Click` `Sub` Yordamı ile tanımlanmalıdır `Async` değiştiricisi olduğundan bir `Await` ifade.</span><span class="sxs-lookup"><span data-stu-id="d3512-222">The `startButton_Click` `Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>  
  
 [!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/sub-statement_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d3512-223">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3512-223">See also</span></span>
- [<span data-ttu-id="d3512-224">Implements Deyimi</span><span class="sxs-lookup"><span data-stu-id="d3512-224">Implements Statement</span></span>](implements-statement.md)
- [<span data-ttu-id="d3512-225">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="d3512-225">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="d3512-226">Parametre Listesi</span><span class="sxs-lookup"><span data-stu-id="d3512-226">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="d3512-227">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="d3512-227">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="d3512-228">Call Deyimi</span><span class="sxs-lookup"><span data-stu-id="d3512-228">Call Statement</span></span>](call-statement.md)
- [<span data-ttu-id="d3512-229">,</span><span class="sxs-lookup"><span data-stu-id="d3512-229">Of</span></span>](of-clause.md)
- [<span data-ttu-id="d3512-230">Parametre Dizileri</span><span class="sxs-lookup"><span data-stu-id="d3512-230">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
- [<span data-ttu-id="d3512-231">Nasıl yapılır: Genel Bir Sınıf Kullanma</span><span class="sxs-lookup"><span data-stu-id="d3512-231">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="d3512-232">Yordam Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="d3512-232">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [<span data-ttu-id="d3512-233">Kısmi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d3512-233">Partial Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
