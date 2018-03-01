---
title: Sub Deyimi (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0a2d0d5ffdca857a3a5ca58cd38b0930f254526f
ms.sourcegitcommit: 8ed4ebc15b5ef89d06a7507dc9d5e306e30accf7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2017
---
# <a name="sub-statement-visual-basic"></a><span data-ttu-id="f183f-102">Sub Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f183f-102">Sub Statement (Visual Basic)</span></span>
<span data-ttu-id="f183f-103">Ad, parametreleri ve tanımlama kodu bildiren bir `Sub` yordamı.</span><span class="sxs-lookup"><span data-stu-id="f183f-103">Declares the name, parameters, and code that define a `Sub` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f183f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f183f-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]  
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]  
    [ statements ]  
    [ Exit Sub ]  
    [ statements ]  
End Sub  
```  
  
## <a name="parts"></a><span data-ttu-id="f183f-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="f183f-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="f183f-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="f183f-106">Optional.</span></span> <span data-ttu-id="f183f-107">Bkz: [öznitelik listesi](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="f183f-107">See [Attribute List](attribute-list.md).</span></span>  
  
-   `Partial`  
  
     <span data-ttu-id="f183f-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="f183f-108">Optional.</span></span> <span data-ttu-id="f183f-109">Kısmi bir yöntem tanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f183f-109">Indicates definition of a partial method.</span></span> <span data-ttu-id="f183f-110">Bkz: [kısmi yöntemler](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).</span><span class="sxs-lookup"><span data-stu-id="f183f-110">See [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="f183f-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="f183f-111">Optional.</span></span> <span data-ttu-id="f183f-112">Aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="f183f-112">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="f183f-113">Public</span><span class="sxs-lookup"><span data-stu-id="f183f-113">Public</span></span>](../modifiers/public.md)  
  
    -   [<span data-ttu-id="f183f-114">Protected</span><span class="sxs-lookup"><span data-stu-id="f183f-114">Protected</span></span>](../modifiers/protected.md)  
  
    -   [<span data-ttu-id="f183f-115">Friend</span><span class="sxs-lookup"><span data-stu-id="f183f-115">Friend</span></span>](../modifiers/friend.md)  
  
    -   [<span data-ttu-id="f183f-116">Private</span><span class="sxs-lookup"><span data-stu-id="f183f-116">Private</span></span>](../modifiers/private.md)  
  
    -   `Protected Friend`  
  
     <span data-ttu-id="f183f-117">Bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="f183f-117">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `proceduremodifiers`  
  
     <span data-ttu-id="f183f-118">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="f183f-118">Optional.</span></span> <span data-ttu-id="f183f-119">Aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="f183f-119">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="f183f-120">Overloads</span><span class="sxs-lookup"><span data-stu-id="f183f-120">Overloads</span></span>](../modifiers/overloads.md)  
  
    -   [<span data-ttu-id="f183f-121">Overrides</span><span class="sxs-lookup"><span data-stu-id="f183f-121">Overrides</span></span>](../modifiers/overrides.md)  
  
    -   [<span data-ttu-id="f183f-122">Overridable</span><span class="sxs-lookup"><span data-stu-id="f183f-122">Overridable</span></span>](../modifiers/overridable.md)  
  
    -   [<span data-ttu-id="f183f-123">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="f183f-123">NotOverridable</span></span>](../modifiers/notoverridable.md)  
  
    -   [<span data-ttu-id="f183f-124">MustOverride</span><span class="sxs-lookup"><span data-stu-id="f183f-124">MustOverride</span></span>](../modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     <span data-ttu-id="f183f-125">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="f183f-125">Optional.</span></span> <span data-ttu-id="f183f-126">Bkz: [paylaşılan](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="f183f-126">See [Shared](../modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="f183f-127">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="f183f-127">Optional.</span></span> <span data-ttu-id="f183f-128">Bkz: [gölgeleri](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="f183f-128">See [Shadows](../modifiers/shadows.md).</span></span>  
  
-   `Async`  
  
     <span data-ttu-id="f183f-129">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="f183f-129">Optional.</span></span> <span data-ttu-id="f183f-130">Bkz: [zaman uyumsuz](../modifiers/async.md).</span><span class="sxs-lookup"><span data-stu-id="f183f-130">See [Async](../modifiers/async.md).</span></span>  
  
-   `name`  
  
     <span data-ttu-id="f183f-131">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="f183f-131">Required.</span></span> <span data-ttu-id="f183f-132">Yordamın adı.</span><span class="sxs-lookup"><span data-stu-id="f183f-132">Name of the procedure.</span></span> <span data-ttu-id="f183f-133">Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="f183f-133">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span> <span data-ttu-id="f183f-134">Bir sınıf için bir oluşturucu yordam oluşturmak için adını ayarlayın bir `Sub` yordamına `New` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="f183f-134">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="f183f-135">Daha fazla bilgi için bkz: [nesne ömrü: nesneleri oluşturma ve Destroyed şeklini](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="f183f-135">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>  
  
-   `typeparamlist`  
  
     <span data-ttu-id="f183f-136">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="f183f-136">Optional.</span></span> <span data-ttu-id="f183f-137">Tür parametreleri genel bir yordam listesi.</span><span class="sxs-lookup"><span data-stu-id="f183f-137">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="f183f-138">Bkz: [yazın listesi](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="f183f-138">See [Type List](type-list.md).</span></span>  
  
-   `parameterlist`  
  
     <span data-ttu-id="f183f-139">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="f183f-139">Optional.</span></span> <span data-ttu-id="f183f-140">Bu yordam parametreleri temsil eden yerel değişken adları listesi.</span><span class="sxs-lookup"><span data-stu-id="f183f-140">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="f183f-141">Bkz: [parametre listesi](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="f183f-141">See [Parameter List](parameter-list.md).</span></span>  
  
-   `Implements`  
  
     <span data-ttu-id="f183f-142">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="f183f-142">Optional.</span></span> <span data-ttu-id="f183f-143">Bu yordam bir veya daha fazla uyguladığını gösteren `Sub` yordamlar, bu yordamın içeren sınıf veya yapı tarafından uygulanan bir arabirim tanımlanan her biri.</span><span class="sxs-lookup"><span data-stu-id="f183f-143">Indicates that this procedure implements one or more `Sub` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="f183f-144">Bkz: [uygulayan deyimi](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f183f-144">See [Implements Statement](implements-statement.md).</span></span>  
  
-   `implementslist`  
  
     <span data-ttu-id="f183f-145">Gerekli olursa `Implements` sağlanır.</span><span class="sxs-lookup"><span data-stu-id="f183f-145">Required if `Implements` is supplied.</span></span> <span data-ttu-id="f183f-146">Listesi `Sub` uygulanan yordamlar.</span><span class="sxs-lookup"><span data-stu-id="f183f-146">List of `Sub` procedures being implemented.</span></span>  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     <span data-ttu-id="f183f-147">Her `implementedprocedure` aşağıdaki söz dizimini ve bölümleri vardır:</span><span class="sxs-lookup"><span data-stu-id="f183f-147">Each `implementedprocedure` has the following syntax and parts:</span></span>  
  
     `interface.definedname`  
  
    |<span data-ttu-id="f183f-148">Bölümü</span><span class="sxs-lookup"><span data-stu-id="f183f-148">Part</span></span>|<span data-ttu-id="f183f-149">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f183f-149">Description</span></span>|  
    |---|---|  
    |`interface`|<span data-ttu-id="f183f-150">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="f183f-150">Required.</span></span> <span data-ttu-id="f183f-151">Bu yordam tarafından uygulanan bir arabirim adını sınıf veya yapı içeren.</span><span class="sxs-lookup"><span data-stu-id="f183f-151">Name of an interface implemented by this procedure's containing class or structure.</span></span>|  
    |`definedname`|<span data-ttu-id="f183f-152">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="f183f-152">Required.</span></span> <span data-ttu-id="f183f-153">Adı olarak yordamı tanımlanmış `interface`.</span><span class="sxs-lookup"><span data-stu-id="f183f-153">Name by which the procedure is defined in `interface`.</span></span>|  
  
-   `Handles`  
  
     <span data-ttu-id="f183f-154">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="f183f-154">Optional.</span></span> <span data-ttu-id="f183f-155">Bu yordam bir veya daha fazla belirli olayları işleyebilirsiniz gösterir.</span><span class="sxs-lookup"><span data-stu-id="f183f-155">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="f183f-156">Bkz: [işleme](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="f183f-156">See [Handles](handles-clause.md).</span></span>  
  
-   `eventlist`  
  
     <span data-ttu-id="f183f-157">Gerekli olursa `Handles` sağlanır.</span><span class="sxs-lookup"><span data-stu-id="f183f-157">Required if `Handles` is supplied.</span></span> <span data-ttu-id="f183f-158">Bu yordamı işleme olayların listesi.</span><span class="sxs-lookup"><span data-stu-id="f183f-158">List of events this procedure handles.</span></span>  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     <span data-ttu-id="f183f-159">Her `eventspecifier` aşağıdaki söz dizimini ve bölümleri vardır:</span><span class="sxs-lookup"><span data-stu-id="f183f-159">Each `eventspecifier` has the following syntax and parts:</span></span>  
  
     `eventvariable.event`  
  
    |<span data-ttu-id="f183f-160">Bölümü</span><span class="sxs-lookup"><span data-stu-id="f183f-160">Part</span></span>|<span data-ttu-id="f183f-161">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f183f-161">Description</span></span>|  
    |---|---|  
    |`eventvariable`|<span data-ttu-id="f183f-162">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="f183f-162">Required.</span></span> <span data-ttu-id="f183f-163">Nesne değişkeni sınıf veya olayı oluşturan yapı, veri türü ile bildirilmedi.</span><span class="sxs-lookup"><span data-stu-id="f183f-163">Object variable declared with the data type of the class or structure that raises the event.</span></span>|  
    |`event`|<span data-ttu-id="f183f-164">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="f183f-164">Required.</span></span> <span data-ttu-id="f183f-165">Bu yordamı işleme olayın adı.</span><span class="sxs-lookup"><span data-stu-id="f183f-165">Name of the event this procedure handles.</span></span>|  
  
-   `statements`  
  
     <span data-ttu-id="f183f-166">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="f183f-166">Optional.</span></span> <span data-ttu-id="f183f-167">Bu yordam içinde çalıştırmak için deyimleri bloğu.</span><span class="sxs-lookup"><span data-stu-id="f183f-167">Block of statements to run within this procedure.</span></span>  
  
-   `End Sub`  
  
     <span data-ttu-id="f183f-168">Bu yordamı tanımı sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="f183f-168">Terminates the definition of this procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f183f-169">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f183f-169">Remarks</span></span>  
 <span data-ttu-id="f183f-170">Tüm yürütülebilir kod yordam içinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f183f-170">All executable code must be inside a procedure.</span></span> <span data-ttu-id="f183f-171">Kullanım bir `Sub` çağıran kodu için bir değer döndürmesi istemediğinizde yordamı.</span><span class="sxs-lookup"><span data-stu-id="f183f-171">Use a `Sub` procedure when you don't want to return a value to the calling code.</span></span> <span data-ttu-id="f183f-172">Kullanım bir `Function` bir değer döndürmek istediğinizde yordamı.</span><span class="sxs-lookup"><span data-stu-id="f183f-172">Use a `Function` procedure when you want to return a value.</span></span>  
  
## <a name="defining-a-sub-procedure"></a><span data-ttu-id="f183f-173">Bir alt yordam tanımlama</span><span class="sxs-lookup"><span data-stu-id="f183f-173">Defining a Sub Procedure</span></span>  
 <span data-ttu-id="f183f-174">Tanımlayabileceğiniz bir `Sub` yordamı yalnızca modülü düzeyinde.</span><span class="sxs-lookup"><span data-stu-id="f183f-174">You can define a `Sub` procedure only at the module level.</span></span> <span data-ttu-id="f183f-175">Bildirimi bağlam alt yordamı için bu nedenle, bir sınıf, bir yapı, bir modül veya bir arabirim olmalıdır ve kaynak dosyası, bir ad alanı, bir yordam veya bir blok olamaz.</span><span class="sxs-lookup"><span data-stu-id="f183f-175">The declaration context for a sub procedure must, therefore, be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="f183f-176">Daha fazla bilgi için bkz: [bildirim bağlamları ve varsayılan erişim düzeyleri](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="f183f-176">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="f183f-177">`Sub`Genel erişim varsayılan yordamlar.</span><span class="sxs-lookup"><span data-stu-id="f183f-177">`Sub` procedures default to public access.</span></span> <span data-ttu-id="f183f-178">Erişim değiştiricileri kullanarak bunların erişim düzeyleri ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f183f-178">You can adjust their access levels by using the access modifiers.</span></span>  
  
 <span data-ttu-id="f183f-179">Yordam kullanıyorsa `Implements` anahtar sözcüğü, içeren sınıf veya yapı olmalıdır bir `Implements` hemen izleyen deyimi kendi `Class` veya `Structure` deyimi.</span><span class="sxs-lookup"><span data-stu-id="f183f-179">If the procedure uses the `Implements` keyword, the containing class or structure must have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="f183f-180">`Implements` Deyim, belirtilen her bir arabirime içermelidir `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="f183f-180">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="f183f-181">Ancak, bir arabirim tarafından tanımlayan ad `Sub` (içinde `definedname`) bu yordamı adıyla eşleşmesi gerekmez (içinde `name`).</span><span class="sxs-lookup"><span data-stu-id="f183f-181">However, the name by which an interface defines the `Sub` (in `definedname`) doesn't have to match the name of this procedure (in `name`).</span></span>  
  
## <a name="returning-from-a-sub-procedure"></a><span data-ttu-id="f183f-182">Bir alt yordam döndürme</span><span class="sxs-lookup"><span data-stu-id="f183f-182">Returning from a Sub Procedure</span></span>  
 <span data-ttu-id="f183f-183">Zaman bir `Sub` yordamı çağıran kodu döndürür, yürütme adlı deyiminden sonraki ile devam eder.</span><span class="sxs-lookup"><span data-stu-id="f183f-183">When a `Sub` procedure returns to the calling code, execution continues with the statement after the statement that called it.</span></span>  
  
 <span data-ttu-id="f183f-184">Aşağıdaki örnek, bir dönüş gösterir bir `Sub` yordamı.</span><span class="sxs-lookup"><span data-stu-id="f183f-184">The following example shows a return from a `Sub` procedure.</span></span>  
  
```vb  
Sub mySub(ByVal q As String)  
    Return  
End Sub   
```  
  
 <span data-ttu-id="f183f-185">`Exit Sub` Ve `Return` deyimleri neden bir hemen çıkın bir `Sub` yordamı.</span><span class="sxs-lookup"><span data-stu-id="f183f-185">The `Exit Sub` and `Return` statements cause an immediate exit from a `Sub` procedure.</span></span> <span data-ttu-id="f183f-186">Herhangi bir sayıda `Exit Sub` ve `Return` deyimleri yordamda herhangi bir yerinde görünebilir ve karıştırabilir miyim `Exit Sub` ve `Return` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="f183f-186">Any number of `Exit Sub` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Sub` and `Return` statements.</span></span>  
  
## <a name="calling-a-sub-procedure"></a><span data-ttu-id="f183f-187">Alt yordamı çağırma</span><span class="sxs-lookup"><span data-stu-id="f183f-187">Calling a Sub Procedure</span></span>  
 <span data-ttu-id="f183f-188">Çağırmanız bir `Sub` bir deyimde yordam adı kullanarak ve bu adı taşıyan kendi bağımsız değişken listesi parantez içinde aşağıdaki yordamı.</span><span class="sxs-lookup"><span data-stu-id="f183f-188">You call a `Sub` procedure by using the procedure name in a statement and then following that name with its argument list in parentheses.</span></span> <span data-ttu-id="f183f-189">Yalnızca herhangi bir bağımsız değişken belirlemezseniz parantez atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f183f-189">You can omit the parentheses only if you don't supply any arguments.</span></span> <span data-ttu-id="f183f-190">Ancak, kodunuzun her zaman parantez eklerseniz, daha okunabilir durumdadır.</span><span class="sxs-lookup"><span data-stu-id="f183f-190">However, your code is more readable if you always include the parentheses.</span></span>  
  
 <span data-ttu-id="f183f-191">A `Sub` yordam ve `Function` yordamı parametrelere sahip ve bir dizi deyimi gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="f183f-191">A `Sub` procedure and a `Function` procedure  can have parameters and perform a series of statements.</span></span> <span data-ttu-id="f183f-192">Ancak, bir `Function` yordamı döndürür bir değer ve bir `Sub` yordam değil.</span><span class="sxs-lookup"><span data-stu-id="f183f-192">However, a `Function` procedure returns a value, and a `Sub` procedure doesn't.</span></span> <span data-ttu-id="f183f-193">Bu nedenle, kullanamazsınız bir `Sub` yordamda bir ifade.</span><span class="sxs-lookup"><span data-stu-id="f183f-193">Therefore, you can't use a `Sub` procedure in an expression.</span></span>  
  
 <span data-ttu-id="f183f-194">Kullanabileceğiniz `Call` çağırdığınızda anahtar sözcüğü bir `Sub` yordamı, ancak bu anahtar sözcük birçok kullanım için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="f183f-194">You can use the `Call` keyword when you call a `Sub` procedure, but that keyword isn't recommended for most uses.</span></span> <span data-ttu-id="f183f-195">Daha fazla bilgi için bkz: [Call deyimi](call-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f183f-195">For more information, see [Call Statement](call-statement.md).</span></span>  
  
 <span data-ttu-id="f183f-196">Visual Basic bazen iç verimliliğini artırmak için aritmetik ifadeler yeniden düzenler.</span><span class="sxs-lookup"><span data-stu-id="f183f-196">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="f183f-197">Bağımsız değişken listesi diğer yordamlar çağrı ifadeler içeriyorsa, bu nedenle, belirli bir sırada bu ifadeler adlı olduğunu varsayalım döndürmemelidir.</span><span class="sxs-lookup"><span data-stu-id="f183f-197">For that reason, if your argument list includes expressions that call other procedures, you shouldn't assume that those expressions will be called in a particular order.</span></span>  
  
## <a name="async-sub-procedures"></a><span data-ttu-id="f183f-198">Zaman uyumsuz alt yordamlar</span><span class="sxs-lookup"><span data-stu-id="f183f-198">Async Sub Procedures</span></span>  
 <span data-ttu-id="f183f-199">Async özelliği kullanarak, açık geri aramalar kullanarak veya birden çok işlevleri veya lambda ifadeleri kodunuzu el ile bölme olmadan zaman uyumsuz işlevleri çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="f183f-199">By using the Async feature, you can invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>  
  
 <span data-ttu-id="f183f-200">Bir yordam ile işaretlerseniz [zaman uyumsuz](../modifiers/async.md) kullanabileceğiniz değiştiricisi, [bekleme](../../../visual-basic/language-reference/operators/await-operator.md) yordamda işleci.</span><span class="sxs-lookup"><span data-stu-id="f183f-200">If you mark a procedure with the [Async](../modifiers/async.md) modifier, you can use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in the procedure.</span></span> <span data-ttu-id="f183f-201">Ulaştığında denetlemek bir `Await` ifadesinde `Async` yordam, Denetim çağırana döndürür ve awaited görevi tamamlanana kadar yordamı ediyor askıya alındı.</span><span class="sxs-lookup"><span data-stu-id="f183f-201">When control reaches an `Await` expression in the `Async` procedure, control returns to the caller, and progress in the procedure is suspended until the awaited task completes.</span></span> <span data-ttu-id="f183f-202">Görev tamamlandığında yürütme yordamda devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f183f-202">When the task is complete, execution can resume in the procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f183f-203">Bir `Async` yordamı döndürür henüz tamamlanmadı ya da ilk awaited nesne karşılaşıldığında çağıran ya da sonunda `Async` yordamı ulaşıldığında, hangisi daha önce gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="f183f-203">An `Async` procedure returns to the caller when either the first awaited object that’s not yet complete is encountered or the end of the `Async` procedure is reached, whichever occurs first.</span></span>  
  
 <span data-ttu-id="f183f-204">Ayrıca işaretleyebilirsiniz bir [Function deyimi](function-statement.md) ile `Async` değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="f183f-204">You can also mark a [Function Statement](function-statement.md) with the `Async` modifier.</span></span> <span data-ttu-id="f183f-205">Bir `Async` işlevi dönüş türüne sahip <xref:System.Threading.Tasks.Task%601> veya <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="f183f-205">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="f183f-206">Bu konuda gösterilmektedir örnek daha sonra da bir `Async` dönüş türüne sahip işlevi <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="f183f-206">An example later in this topic shows an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
 <span data-ttu-id="f183f-207">`Async``Sub` yordamları öncelikle kullanılan olay işleyicileri için bir değer nerede iade edilemez.</span><span class="sxs-lookup"><span data-stu-id="f183f-207">`Async` `Sub` procedures are primarily used for event handlers, where a value can't be returned.</span></span> <span data-ttu-id="f183f-208">Bir `Async``Sub` yordamı beklemenin olamaz ve çağıran bir `Async``Sub` yordamı catch özel durumları olamaz, `Sub` yordamı atar.</span><span class="sxs-lookup"><span data-stu-id="f183f-208">An `Async``Sub` procedure can't be awaited, and the caller of an `Async``Sub` procedure can't catch exceptions that the `Sub` procedure throws.</span></span>  
  
 <span data-ttu-id="f183f-209">Bir `Async` yordam herhangi bildiremez [ByRef](../modifiers/byref.md) parametreleri.</span><span class="sxs-lookup"><span data-stu-id="f183f-209">An `Async` procedure can't declare any [ByRef](../modifiers/byref.md) parameters.</span></span>  
  
 <span data-ttu-id="f183f-210">Hakkında daha fazla bilgi için `Async` yordamlar, bkz: [uyumsuz ve bekleme ile zaman uyumsuz programlama](../../../visual-basic/programming-guide/concepts/async/index.md), [akış denetimi zaman uyumsuz programlarda](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), ve [zaman uyumsuz dönüş türleri](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="f183f-210">For more information about `Async` procedures, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f183f-211">Örnek</span><span class="sxs-lookup"><span data-stu-id="f183f-211">Example</span></span>  
 <span data-ttu-id="f183f-212">Aşağıdaki örnek kullanır `Sub` ad, parametreleri ve gövdesini kodu tanımlamak için deyimi bir `Sub` yordamı.</span><span class="sxs-lookup"><span data-stu-id="f183f-212">The following example uses the `Sub` statement to define the name, parameters, and code that form the body of a `Sub` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#58](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/sub-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="f183f-213">Örnek</span><span class="sxs-lookup"><span data-stu-id="f183f-213">Example</span></span>  
 <span data-ttu-id="f183f-214">Aşağıdaki örnekte, `DelayAsync` olan bir `Async``Function` dönüş türüne sahip <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="f183f-214">In the following example, `DelayAsync` is an `Async``Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="f183f-215">`DelayAsync`sahip bir `Return` deyimi bir tamsayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="f183f-215">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="f183f-216">Bu nedenle, işlevi bildirimi `DelayAsync` dönüş türüne sahip olmalıdır `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="f183f-216">Therefore, the function declaration of `DelayAsync` must have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="f183f-217">Dönüş türü olduğundan `Task(Of Integer)`, değerlendirmesi `Await` ifadesinde `DoSomethingAsync` aşağıdaki deyimi gösterildiği gibi bir tamsayı üretir: `Dim result As Integer = Await delayTask`.</span><span class="sxs-lookup"><span data-stu-id="f183f-217">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer, as the following statement shows: `Dim result As Integer = Await delayTask`.</span></span>  
  
 <span data-ttu-id="f183f-218">`startButton_Click` Yordamdır örneği bir `Async Sub` yordamı.</span><span class="sxs-lookup"><span data-stu-id="f183f-218">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="f183f-219">Çünkü `DoSomethingAsync` olan bir `Async` işlevi, görev çağrısı için `DoSomethingAsync` , aşağıdaki deyimi gösterildiği beklemenin gerekir: `Await DoSomethingAsync()`.</span><span class="sxs-lookup"><span data-stu-id="f183f-219">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement shows: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="f183f-220">`startButton_Click``Sub` Yordamı tanımlı, ile `Async` değiştiricisi içerdiğinden bir `Await` ifade.</span><span class="sxs-lookup"><span data-stu-id="f183f-220">The `startButton_Click``Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>  
  
 [!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/sub-statement_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f183f-221">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f183f-221">See Also</span></span>  
 [<span data-ttu-id="f183f-222">Implements Deyimi</span><span class="sxs-lookup"><span data-stu-id="f183f-222">Implements Statement</span></span>](implements-statement.md)  
 [<span data-ttu-id="f183f-223">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="f183f-223">Function Statement</span></span>](function-statement.md)  
 [<span data-ttu-id="f183f-224">Parametre Listesi</span><span class="sxs-lookup"><span data-stu-id="f183f-224">Parameter List</span></span>](parameter-list.md)  
 [<span data-ttu-id="f183f-225">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="f183f-225">Dim Statement</span></span>](dim-statement.md)  
 [<span data-ttu-id="f183f-226">Call Deyimi</span><span class="sxs-lookup"><span data-stu-id="f183f-226">Call Statement</span></span>](call-statement.md)  
 [<span data-ttu-id="f183f-227">,</span><span class="sxs-lookup"><span data-stu-id="f183f-227">Of</span></span>](of-clause.md)  
 [<span data-ttu-id="f183f-228">Parametre Dizileri</span><span class="sxs-lookup"><span data-stu-id="f183f-228">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)  
 [<span data-ttu-id="f183f-229">Nasıl yapılır: Genel Bir Sınıf Kullanma</span><span class="sxs-lookup"><span data-stu-id="f183f-229">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [<span data-ttu-id="f183f-230">Yordam Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="f183f-230">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)  
 [<span data-ttu-id="f183f-231">Kısmi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f183f-231">Partial Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
