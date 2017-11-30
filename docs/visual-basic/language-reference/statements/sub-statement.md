---
title: Sub Deyimi (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Sub
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
caps.latest.revision: "52"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 02ba9a999db20abce2106269522c9a3221a00cef
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="sub-statement-visual-basic"></a><span data-ttu-id="c2a05-102">Sub Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2a05-102">Sub Statement (Visual Basic)</span></span>
<span data-ttu-id="c2a05-103">Ad, parametreleri ve tanımlama kodu bildiren bir `Sub` yordamı.</span><span class="sxs-lookup"><span data-stu-id="c2a05-103">Declares the name, parameters, and code that define a `Sub` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2a05-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c2a05-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]  
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]  
    [ statements ]  
    [ Exit Sub ]  
    [ statements ]  
End Sub  
```  
  
## <a name="parts"></a><span data-ttu-id="c2a05-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="c2a05-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="c2a05-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c2a05-106">Optional.</span></span> <span data-ttu-id="c2a05-107">Bkz: [öznitelik listesi](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="c2a05-107">See [Attribute List](attribute-list.md).</span></span>  
  
-   `Partial`  
  
     <span data-ttu-id="c2a05-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c2a05-108">Optional.</span></span> <span data-ttu-id="c2a05-109">Kısmi bir yöntem tanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c2a05-109">Indicates definition of a partial method.</span></span> <span data-ttu-id="c2a05-110">Bkz: [kısmi yöntemler](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).</span><span class="sxs-lookup"><span data-stu-id="c2a05-110">See [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="c2a05-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c2a05-111">Optional.</span></span> <span data-ttu-id="c2a05-112">Aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="c2a05-112">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="c2a05-113">Ortak</span><span class="sxs-lookup"><span data-stu-id="c2a05-113">Public</span></span>](../modifiers/public.md)  
  
    -   [<span data-ttu-id="c2a05-114">Korumalı</span><span class="sxs-lookup"><span data-stu-id="c2a05-114">Protected</span></span>](../modifiers/protected.md)  
  
    -   [<span data-ttu-id="c2a05-115">Arkadaş</span><span class="sxs-lookup"><span data-stu-id="c2a05-115">Friend</span></span>](../modifiers/friend.md)  
  
    -   [<span data-ttu-id="c2a05-116">Özel</span><span class="sxs-lookup"><span data-stu-id="c2a05-116">Private</span></span>](../modifiers/private.md)  
  
    -   `Protected Friend`  
  
     <span data-ttu-id="c2a05-117">Bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="c2a05-117">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `proceduremodifiers`  
  
     <span data-ttu-id="c2a05-118">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c2a05-118">Optional.</span></span> <span data-ttu-id="c2a05-119">Aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="c2a05-119">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="c2a05-120">Aşırı yüklemeler</span><span class="sxs-lookup"><span data-stu-id="c2a05-120">Overloads</span></span>](../modifiers/overloads.md)  
  
    -   [<span data-ttu-id="c2a05-121">Geçersiz kılmaları</span><span class="sxs-lookup"><span data-stu-id="c2a05-121">Overrides</span></span>](../modifiers/overrides.md)  
  
    -   [<span data-ttu-id="c2a05-122">Geçersiz kılınabilir</span><span class="sxs-lookup"><span data-stu-id="c2a05-122">Overridable</span></span>](../modifiers/overridable.md)  
  
    -   [<span data-ttu-id="c2a05-123">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="c2a05-123">NotOverridable</span></span>](../modifiers/notoverridable.md)  
  
    -   [<span data-ttu-id="c2a05-124">MustOverride</span><span class="sxs-lookup"><span data-stu-id="c2a05-124">MustOverride</span></span>](../modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     <span data-ttu-id="c2a05-125">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c2a05-125">Optional.</span></span> <span data-ttu-id="c2a05-126">Bkz: [paylaşılan](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="c2a05-126">See [Shared](../modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="c2a05-127">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c2a05-127">Optional.</span></span> <span data-ttu-id="c2a05-128">Bkz: [gölgeleri](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="c2a05-128">See [Shadows](../modifiers/shadows.md).</span></span>  
  
-   `Async`  
  
     <span data-ttu-id="c2a05-129">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c2a05-129">Optional.</span></span> <span data-ttu-id="c2a05-130">Bkz: [zaman uyumsuz](../modifiers/async.md).</span><span class="sxs-lookup"><span data-stu-id="c2a05-130">See [Async](../modifiers/async.md).</span></span>  
  
-   `name`  
  
     <span data-ttu-id="c2a05-131">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="c2a05-131">Required.</span></span> <span data-ttu-id="c2a05-132">Yordamın adı.</span><span class="sxs-lookup"><span data-stu-id="c2a05-132">Name of the procedure.</span></span> <span data-ttu-id="c2a05-133">Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="c2a05-133">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span> <span data-ttu-id="c2a05-134">Bir sınıf için bir oluşturucu yordam oluşturmak için adını ayarlayın bir `Sub` yordamına `New` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="c2a05-134">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="c2a05-135">Daha fazla bilgi için bkz: [nesne ömrü: nesneleri oluşturma ve Destroyed şeklini](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="c2a05-135">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>  
  
-   `typeparamlist`  
  
     <span data-ttu-id="c2a05-136">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c2a05-136">Optional.</span></span> <span data-ttu-id="c2a05-137">Tür parametreleri genel bir yordam listesi.</span><span class="sxs-lookup"><span data-stu-id="c2a05-137">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="c2a05-138">Bkz: [yazın listesi](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="c2a05-138">See [Type List](type-list.md).</span></span>  
  
-   `parameterlist`  
  
     <span data-ttu-id="c2a05-139">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c2a05-139">Optional.</span></span> <span data-ttu-id="c2a05-140">Bu yordam parametreleri temsil eden yerel değişken adları listesi.</span><span class="sxs-lookup"><span data-stu-id="c2a05-140">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="c2a05-141">Bkz: [parametre listesi](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="c2a05-141">See [Parameter List](parameter-list.md).</span></span>  
  
-   `Implements`  
  
     <span data-ttu-id="c2a05-142">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c2a05-142">Optional.</span></span> <span data-ttu-id="c2a05-143">Bu yordam bir veya daha fazla uyguladığını gösteren `Sub` yordamlar, bu yordamın içeren sınıf veya yapı tarafından uygulanan bir arabirim tanımlanan her biri.</span><span class="sxs-lookup"><span data-stu-id="c2a05-143">Indicates that this procedure implements one or more `Sub` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="c2a05-144">Bkz: [uygulayan deyimi](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c2a05-144">See [Implements Statement](implements-statement.md).</span></span>  
  
-   `implementslist`  
  
     <span data-ttu-id="c2a05-145">Gerekli olursa `Implements` sağlanır.</span><span class="sxs-lookup"><span data-stu-id="c2a05-145">Required if `Implements` is supplied.</span></span> <span data-ttu-id="c2a05-146">Listesi `Sub` uygulanan yordamlar.</span><span class="sxs-lookup"><span data-stu-id="c2a05-146">List of `Sub` procedures being implemented.</span></span>  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     <span data-ttu-id="c2a05-147">Her `implementedprocedure` aşağıdaki söz dizimini ve bölümleri vardır:</span><span class="sxs-lookup"><span data-stu-id="c2a05-147">Each `implementedprocedure` has the following syntax and parts:</span></span>  
  
     `interface.definedname`  
  
    |<span data-ttu-id="c2a05-148">Bölümü</span><span class="sxs-lookup"><span data-stu-id="c2a05-148">Part</span></span>|<span data-ttu-id="c2a05-149">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c2a05-149">Description</span></span>|  
    |---|---|  
    |`interface`|<span data-ttu-id="c2a05-150">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="c2a05-150">Required.</span></span> <span data-ttu-id="c2a05-151">Bu yordam tarafından uygulanan bir arabirim adını sınıf veya yapı içeren.</span><span class="sxs-lookup"><span data-stu-id="c2a05-151">Name of an interface implemented by this procedure's containing class or structure.</span></span>|  
    |`definedname`|<span data-ttu-id="c2a05-152">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="c2a05-152">Required.</span></span> <span data-ttu-id="c2a05-153">Adı olarak yordamı tanımlanmış `interface`.</span><span class="sxs-lookup"><span data-stu-id="c2a05-153">Name by which the procedure is defined in `interface`.</span></span>|  
  
-   `Handles`  
  
     <span data-ttu-id="c2a05-154">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c2a05-154">Optional.</span></span> <span data-ttu-id="c2a05-155">Bu yordam bir veya daha fazla belirli olayları işleyebilirsiniz gösterir.</span><span class="sxs-lookup"><span data-stu-id="c2a05-155">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="c2a05-156">Bkz: [işleme](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="c2a05-156">See [Handles](handles-clause.md).</span></span>  
  
-   `eventlist`  
  
     <span data-ttu-id="c2a05-157">Gerekli olursa `Handles` sağlanır.</span><span class="sxs-lookup"><span data-stu-id="c2a05-157">Required if `Handles` is supplied.</span></span> <span data-ttu-id="c2a05-158">Bu yordamı işleme olayların listesi.</span><span class="sxs-lookup"><span data-stu-id="c2a05-158">List of events this procedure handles.</span></span>  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     <span data-ttu-id="c2a05-159">Her `eventspecifier` aşağıdaki söz dizimini ve bölümleri vardır:</span><span class="sxs-lookup"><span data-stu-id="c2a05-159">Each `eventspecifier` has the following syntax and parts:</span></span>  
  
     `eventvariable.event`  
  
    |<span data-ttu-id="c2a05-160">Bölümü</span><span class="sxs-lookup"><span data-stu-id="c2a05-160">Part</span></span>|<span data-ttu-id="c2a05-161">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c2a05-161">Description</span></span>|  
    |---|---|  
    |`eventvariable`|<span data-ttu-id="c2a05-162">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="c2a05-162">Required.</span></span> <span data-ttu-id="c2a05-163">Nesne değişkeni sınıf veya olayı oluşturan yapı, veri türü ile bildirilmedi.</span><span class="sxs-lookup"><span data-stu-id="c2a05-163">Object variable declared with the data type of the class or structure that raises the event.</span></span>|  
    |`event`|<span data-ttu-id="c2a05-164">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="c2a05-164">Required.</span></span> <span data-ttu-id="c2a05-165">Bu yordamı işleme olayın adı.</span><span class="sxs-lookup"><span data-stu-id="c2a05-165">Name of the event this procedure handles.</span></span>|  
  
-   `statements`  
  
     <span data-ttu-id="c2a05-166">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c2a05-166">Optional.</span></span> <span data-ttu-id="c2a05-167">Bu yordam içinde çalıştırmak için deyimleri bloğu.</span><span class="sxs-lookup"><span data-stu-id="c2a05-167">Block of statements to run within this procedure.</span></span>  
  
-   `End Sub`  
  
     <span data-ttu-id="c2a05-168">Bu yordamı tanımı sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="c2a05-168">Terminates the definition of this procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2a05-169">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c2a05-169">Remarks</span></span>  
 <span data-ttu-id="c2a05-170">Tüm yürütülebilir kod yordam içinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c2a05-170">All executable code must be inside a procedure.</span></span> <span data-ttu-id="c2a05-171">Kullanım bir `Sub` çağıran kodu için bir değer döndürmesi istemediğinizde yordamı.</span><span class="sxs-lookup"><span data-stu-id="c2a05-171">Use a `Sub` procedure when you don't want to return a value to the calling code.</span></span> <span data-ttu-id="c2a05-172">Kullanım bir `Function` bir değer döndürmek istediğinizde yordamı.</span><span class="sxs-lookup"><span data-stu-id="c2a05-172">Use a `Function` procedure when you want to return a value.</span></span>  
  
## <a name="defining-a-sub-procedure"></a><span data-ttu-id="c2a05-173">Bir alt yordam tanımlama</span><span class="sxs-lookup"><span data-stu-id="c2a05-173">Defining a Sub Procedure</span></span>  
 <span data-ttu-id="c2a05-174">Tanımlayabileceğiniz bir `Sub` yordamı yalnızca modülü düzeyinde.</span><span class="sxs-lookup"><span data-stu-id="c2a05-174">You can define a `Sub` procedure only at the module level.</span></span> <span data-ttu-id="c2a05-175">Bildirimi bağlam alt yordamı için bu nedenle, bir sınıf, bir yapı, bir modül veya bir arabirim olmalıdır ve kaynak dosyası, bir ad alanı, bir yordam veya bir blok olamaz.</span><span class="sxs-lookup"><span data-stu-id="c2a05-175">The declaration context for a sub procedure must, therefore, be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="c2a05-176">Daha fazla bilgi için bkz: [bildirim bağlamları ve varsayılan erişim düzeyleri](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="c2a05-176">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="c2a05-177">`Sub`Genel erişim varsayılan yordamlar.</span><span class="sxs-lookup"><span data-stu-id="c2a05-177">`Sub` procedures default to public access.</span></span> <span data-ttu-id="c2a05-178">Erişim değiştiricileri kullanarak bunların erişim düzeyleri ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2a05-178">You can adjust their access levels by using the access modifiers.</span></span>  
  
 <span data-ttu-id="c2a05-179">Yordam kullanıyorsa `Implements` anahtar sözcüğü, içeren sınıf veya yapı olmalıdır bir `Implements` hemen izleyen deyimi kendi `Class` veya `Structure` deyimi.</span><span class="sxs-lookup"><span data-stu-id="c2a05-179">If the procedure uses the `Implements` keyword, the containing class or structure must have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="c2a05-180">`Implements` Deyim, belirtilen her bir arabirime içermelidir `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="c2a05-180">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="c2a05-181">Ancak, bir arabirim tarafından tanımlayan ad `Sub` (içinde `definedname`) bu yordamı adıyla eşleşmesi gerekmez (içinde `name`).</span><span class="sxs-lookup"><span data-stu-id="c2a05-181">However, the name by which an interface defines the `Sub` (in `definedname`) doesn't have to match the name of this procedure (in `name`).</span></span>  
  
## <a name="returning-from-a-sub-procedure"></a><span data-ttu-id="c2a05-182">Bir alt yordam döndürme</span><span class="sxs-lookup"><span data-stu-id="c2a05-182">Returning from a Sub Procedure</span></span>  
 <span data-ttu-id="c2a05-183">Zaman bir `Sub` yordamı çağıran kodu döndürür, yürütme adlı deyiminden sonraki ile devam eder.</span><span class="sxs-lookup"><span data-stu-id="c2a05-183">When a `Sub` procedure returns to the calling code, execution continues with the statement after the statement that called it.</span></span>  
  
 <span data-ttu-id="c2a05-184">Aşağıdaki örnek, bir dönüş gösterir bir `Sub` yordamı.</span><span class="sxs-lookup"><span data-stu-id="c2a05-184">The following example shows a return from a `Sub` procedure.</span></span>  
  
```vb  
Sub mySub(ByVal q As String)  
    Return  
End Sub   
```  
  
 <span data-ttu-id="c2a05-185">`Exit Sub` Ve `Return` deyimleri neden bir hemen çıkın bir `Sub` yordamı.</span><span class="sxs-lookup"><span data-stu-id="c2a05-185">The `Exit Sub` and `Return` statements cause an immediate exit from a `Sub` procedure.</span></span> <span data-ttu-id="c2a05-186">Herhangi bir sayıda `Exit Sub` ve `Return` deyimleri yordamda herhangi bir yerinde görünebilir ve karıştırabilir miyim `Exit Sub` ve `Return` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="c2a05-186">Any number of `Exit Sub` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Sub` and `Return` statements.</span></span>  
  
## <a name="calling-a-sub-procedure"></a><span data-ttu-id="c2a05-187">Alt yordamı çağırma</span><span class="sxs-lookup"><span data-stu-id="c2a05-187">Calling a Sub Procedure</span></span>  
 <span data-ttu-id="c2a05-188">Çağırmanız bir `Sub` bir deyimde yordam adı kullanarak ve bu adı taşıyan kendi bağımsız değişken listesi parantez içinde aşağıdaki yordamı.</span><span class="sxs-lookup"><span data-stu-id="c2a05-188">You call a `Sub` procedure by using the procedure name in a statement and then following that name with its argument list in parentheses.</span></span> <span data-ttu-id="c2a05-189">Yalnızca herhangi bir bağımsız değişken belirlemezseniz parantez atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2a05-189">You can omit the parentheses only if you don't supply any arguments.</span></span> <span data-ttu-id="c2a05-190">Ancak, kodunuzun her zaman parantez eklerseniz, daha okunabilir durumdadır.</span><span class="sxs-lookup"><span data-stu-id="c2a05-190">However, your code is more readable if you always include the parentheses.</span></span>  
  
 <span data-ttu-id="c2a05-191">A `Sub` yordam ve `Function` yordamı parametrelere sahip ve bir dizi deyimi gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="c2a05-191">A `Sub` procedure and a `Function` procedure  can have parameters and perform a series of statements.</span></span> <span data-ttu-id="c2a05-192">Ancak, bir `Function` yordamı döndürür bir değer ve bir `Sub` yordam değil.</span><span class="sxs-lookup"><span data-stu-id="c2a05-192">However, a `Function` procedure returns a value, and a `Sub` procedure doesn't.</span></span> <span data-ttu-id="c2a05-193">Bu nedenle, kullanamazsınız bir `Sub` yordamda bir ifade.</span><span class="sxs-lookup"><span data-stu-id="c2a05-193">Therefore, you can't use a `Sub` procedure in an expression.</span></span>  
  
 <span data-ttu-id="c2a05-194">Kullanabileceğiniz `Call` çağırdığınızda anahtar sözcüğü bir `Sub` yordamı, ancak bu anahtar sözcük birçok kullanım için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="c2a05-194">You can use the `Call` keyword when you call a `Sub` procedure, but that keyword isn't recommended for most uses.</span></span> <span data-ttu-id="c2a05-195">Daha fazla bilgi için bkz: [Call deyimi](call-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c2a05-195">For more information, see [Call Statement](call-statement.md).</span></span>  
  
 <span data-ttu-id="c2a05-196">Visual Basic bazen iç verimliliğini artırmak için aritmetik ifadeler yeniden düzenler.</span><span class="sxs-lookup"><span data-stu-id="c2a05-196">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="c2a05-197">Bağımsız değişken listesi diğer yordamlar çağrı ifadeler içeriyorsa, bu nedenle, belirli bir sırada bu ifadeler adlı olduğunu varsayalım döndürmemelidir.</span><span class="sxs-lookup"><span data-stu-id="c2a05-197">For that reason, if your argument list includes expressions that call other procedures, you shouldn't assume that those expressions will be called in a particular order.</span></span>  
  
## <a name="async-sub-procedures"></a><span data-ttu-id="c2a05-198">Zaman uyumsuz alt yordamlar</span><span class="sxs-lookup"><span data-stu-id="c2a05-198">Async Sub Procedures</span></span>  
 <span data-ttu-id="c2a05-199">Async özelliği kullanarak, açık geri aramalar kullanarak veya birden çok işlevleri veya lambda ifadeleri kodunuzu el ile bölme olmadan zaman uyumsuz işlevleri çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="c2a05-199">By using the Async feature, you can invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>  
  
 <span data-ttu-id="c2a05-200">Bir yordam ile işaretlerseniz [zaman uyumsuz](../modifiers/async.md) kullanabileceğiniz değiştiricisi, [bekleme](../../../visual-basic/language-reference/operators/await-operator.md) yordamda işleci.</span><span class="sxs-lookup"><span data-stu-id="c2a05-200">If you mark a procedure with the [Async](../modifiers/async.md) modifier, you can use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in the procedure.</span></span> <span data-ttu-id="c2a05-201">Ulaştığında denetlemek bir `Await` ifadesinde `Async` yordam, Denetim çağırana döndürür ve awaited görevi tamamlanana kadar yordamı ediyor askıya alındı.</span><span class="sxs-lookup"><span data-stu-id="c2a05-201">When control reaches an `Await` expression in the `Async` procedure, control returns to the caller, and progress in the procedure is suspended until the awaited task completes.</span></span> <span data-ttu-id="c2a05-202">Görev tamamlandığında yürütme yordamda devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2a05-202">When the task is complete, execution can resume in the procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c2a05-203">Bir `Async` yordamı döndürür henüz tamamlanmadı ya da ilk awaited nesne karşılaşıldığında çağıran ya da sonunda `Async` yordamı ulaşıldığında, hangisi daha önce gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="c2a05-203">An `Async` procedure returns to the caller when either the first awaited object that’s not yet complete is encountered or the end of the `Async` procedure is reached, whichever occurs first.</span></span>  
  
 <span data-ttu-id="c2a05-204">Ayrıca işaretleyebilirsiniz bir [Function deyimi](function-statement.md) ile `Async` değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="c2a05-204">You can also mark a [Function Statement](function-statement.md) with the `Async` modifier.</span></span> <span data-ttu-id="c2a05-205">Bir `Async` işlevi dönüş türüne sahip <xref:System.Threading.Tasks.Task%601> veya <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="c2a05-205">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="c2a05-206">Bu konuda gösterilmektedir örnek daha sonra da bir `Async` dönüş türüne sahip işlevi <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="c2a05-206">An example later in this topic shows an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
 <span data-ttu-id="c2a05-207">`Async``Sub` yordamları öncelikle kullanılan olay işleyicileri için bir değer nerede iade edilemez.</span><span class="sxs-lookup"><span data-stu-id="c2a05-207">`Async` `Sub` procedures are primarily used for event handlers, where a value can't be returned.</span></span> <span data-ttu-id="c2a05-208">Bir `Async``Sub` yordamı beklemenin olamaz ve çağıran bir `Async``Sub` yordamı catch özel durumları olamaz, `Sub` yordamı atar.</span><span class="sxs-lookup"><span data-stu-id="c2a05-208">An `Async``Sub` procedure can't be awaited, and the caller of an `Async``Sub` procedure can't catch exceptions that the `Sub` procedure throws.</span></span>  
  
 <span data-ttu-id="c2a05-209">Bir `Async` yordam herhangi bildiremez [ByRef](../modifiers/byref.md) parametreleri.</span><span class="sxs-lookup"><span data-stu-id="c2a05-209">An `Async` procedure can't declare any [ByRef](../modifiers/byref.md) parameters.</span></span>  
  
 <span data-ttu-id="c2a05-210">Hakkında daha fazla bilgi için `Async` yordamlar, bkz: [uyumsuz ve bekleme ile zaman uyumsuz programlama](../../../visual-basic/programming-guide/concepts/async/index.md), [akış denetimi zaman uyumsuz programlarda](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), ve [zaman uyumsuz dönüş türleri](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="c2a05-210">For more information about `Async` procedures, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2a05-211">Örnek</span><span class="sxs-lookup"><span data-stu-id="c2a05-211">Example</span></span>  
 <span data-ttu-id="c2a05-212">Aşağıdaki örnek kullanır `Sub` ad, parametreleri ve gövdesini kodu tanımlamak için deyimi bir `Sub` yordamı.</span><span class="sxs-lookup"><span data-stu-id="c2a05-212">The following example uses the `Sub` statement to define the name, parameters, and code that form the body of a `Sub` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#58](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/sub-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="c2a05-213">Örnek</span><span class="sxs-lookup"><span data-stu-id="c2a05-213">Example</span></span>  
 <span data-ttu-id="c2a05-214">Aşağıdaki örnekte, `DelayAsync` olan bir bir `Async``Function` dönüş türüne sahip <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="c2a05-214">In the following example, `DelayAsync` is an an `Async``Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="c2a05-215">`DelayAsync`sahip bir `Return` deyimi bir tamsayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="c2a05-215">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="c2a05-216">Bu nedenle, işlevi bildirimi `DelayAsync` dönüş türüne sahip olmalıdır `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="c2a05-216">Therefore, the function declaration of `DelayAsync` must have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="c2a05-217">Dönüş türü olduğundan `Task(Of Integer)`, değerlendirmesi `Await` ifadesinde `DoSomethingAsync` aşağıdaki deyimi gösterildiği gibi bir tamsayı üretir: `Dim result As Integer = Await delayTask`.</span><span class="sxs-lookup"><span data-stu-id="c2a05-217">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer, as the following statement shows: `Dim result As Integer = Await delayTask`.</span></span>  
  
 <span data-ttu-id="c2a05-218">`startButton_Click` Yordamdır örneği bir `Async Sub` yordamı.</span><span class="sxs-lookup"><span data-stu-id="c2a05-218">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="c2a05-219">Çünkü `DoSomethingAsync` olan bir `Async` işlevi, görev çağrısı için `DoSomethingAsync` , aşağıdaki deyimi gösterildiği beklemenin gerekir: `Await DoSomethingAsync()`.</span><span class="sxs-lookup"><span data-stu-id="c2a05-219">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement shows: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="c2a05-220">`startButton_Click``Sub` Yordamı tanımlı, ile `Async` değiştiricisi içerdiğinden bir `Await` ifade.</span><span class="sxs-lookup"><span data-stu-id="c2a05-220">The `startButton_Click``Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>  
  
 [!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/sub-statement_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c2a05-221">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c2a05-221">See Also</span></span>  
 [<span data-ttu-id="c2a05-222">Implements deyimi</span><span class="sxs-lookup"><span data-stu-id="c2a05-222">Implements Statement</span></span>](implements-statement.md)  
 [<span data-ttu-id="c2a05-223">Function deyimi</span><span class="sxs-lookup"><span data-stu-id="c2a05-223">Function Statement</span></span>](function-statement.md)  
 [<span data-ttu-id="c2a05-224">Parametre listesi</span><span class="sxs-lookup"><span data-stu-id="c2a05-224">Parameter List</span></span>](parameter-list.md)  
 [<span data-ttu-id="c2a05-225">Dim deyimi</span><span class="sxs-lookup"><span data-stu-id="c2a05-225">Dim Statement</span></span>](dim-statement.md)  
 [<span data-ttu-id="c2a05-226">Call deyimi</span><span class="sxs-lookup"><span data-stu-id="c2a05-226">Call Statement</span></span>](call-statement.md)  
 [<span data-ttu-id="c2a05-227">,</span><span class="sxs-lookup"><span data-stu-id="c2a05-227">Of</span></span>](of-clause.md)  
 [<span data-ttu-id="c2a05-228">Parametre dizileri</span><span class="sxs-lookup"><span data-stu-id="c2a05-228">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)  
 [<span data-ttu-id="c2a05-229">Nasıl yapılır: genel bir sınıf kullanma</span><span class="sxs-lookup"><span data-stu-id="c2a05-229">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [<span data-ttu-id="c2a05-230">Sorun giderme yordamları</span><span class="sxs-lookup"><span data-stu-id="c2a05-230">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)  
 [<span data-ttu-id="c2a05-231">Kısmi yöntemler</span><span class="sxs-lookup"><span data-stu-id="c2a05-231">Partial Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
