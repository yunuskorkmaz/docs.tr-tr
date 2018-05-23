---
title: Function Deyimi (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Function
helpviewer_keywords:
- procedures [Visual Basic], creating
- Function procedures [Visual Basic], Function statement syntax
- functions [Visual Basic], function procedures
- ParamArray keyword [Visual Basic], Function statements
- Private keyword [Visual Basic], Function statements
- declarations [Visual Basic], procedures
- procedures [Visual Basic], declaration
- Public keyword [Visual Basic], in Function statement
- ByVal keyword [Visual Basic], Function statements
- procedures [Visual Basic], recursive
- Implements keyword [Visual Basic], Function statements
- procedures [Visual Basic], returning values
- Exit statement [Visual Basic], in Function procedures
- recursive procedures
- As keyword [Visual Basic], in Function statement
- Optional keyword [Visual Basic], Function statements
- Function statement [Visual Basic]
- Visual Basic code, Function procedures
- procedures [Visual Basic], function
- ByRef keyword [Visual Basic], Function statements
- Friend keyword [Visual Basic], Function statements
- End keyword [Visual Basic], Function statements
- Handles keyword [Visual Basic], Function statements
ms.assetid: a4497077-0f46-4ede-a27f-9e8670df52b9
ms.openlocfilehash: 908aa594ecbdd8ae2ec5a06de8181a1b16bb7e40
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="function-statement-visual-basic"></a><span data-ttu-id="46a17-102">Function Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46a17-102">Function Statement (Visual Basic)</span></span>
<span data-ttu-id="46a17-103">Ad, parametreleri ve tanımlama kodu bildiren bir `Function` yordamı.</span><span class="sxs-lookup"><span data-stu-id="46a17-103">Declares the name, parameters, and code that define a `Function` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46a17-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="46a17-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async | Iterator ]  
Function name [ (Of typeparamlist) ] [ (parameterlist) ] [ As returntype ] [ Implements implementslist | Handles eventlist ]  
    [ statements ]  
    [ Exit Function ]  
    [ statements ]  
End Function  
```  
  
## <a name="parts"></a><span data-ttu-id="46a17-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="46a17-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="46a17-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="46a17-106">Optional.</span></span> <span data-ttu-id="46a17-107">Bkz: [öznitelik listesi](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="46a17-107">See [Attribute List](attribute-list.md).</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="46a17-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="46a17-108">Optional.</span></span> <span data-ttu-id="46a17-109">Aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="46a17-109">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="46a17-110">Public</span><span class="sxs-lookup"><span data-stu-id="46a17-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="46a17-111">Protected</span><span class="sxs-lookup"><span data-stu-id="46a17-111">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="46a17-112">Friend</span><span class="sxs-lookup"><span data-stu-id="46a17-112">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="46a17-113">Private</span><span class="sxs-lookup"><span data-stu-id="46a17-113">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   [<span data-ttu-id="46a17-114">Korumalı Friend</span><span class="sxs-lookup"><span data-stu-id="46a17-114">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md)

    - [<span data-ttu-id="46a17-115">Özel korumalı</span><span class="sxs-lookup"><span data-stu-id="46a17-115">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)  
  
     <span data-ttu-id="46a17-116">Bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="46a17-116">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `proceduremodifiers`  
  
     <span data-ttu-id="46a17-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="46a17-117">Optional.</span></span> <span data-ttu-id="46a17-118">Aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="46a17-118">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="46a17-119">Overloads</span><span class="sxs-lookup"><span data-stu-id="46a17-119">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [<span data-ttu-id="46a17-120">Overrides</span><span class="sxs-lookup"><span data-stu-id="46a17-120">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [<span data-ttu-id="46a17-121">Overridable</span><span class="sxs-lookup"><span data-stu-id="46a17-121">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [<span data-ttu-id="46a17-122">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="46a17-122">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [<span data-ttu-id="46a17-123">MustOverride</span><span class="sxs-lookup"><span data-stu-id="46a17-123">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     <span data-ttu-id="46a17-124">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="46a17-124">Optional.</span></span> <span data-ttu-id="46a17-125">Bkz: [paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="46a17-125">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="46a17-126">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="46a17-126">Optional.</span></span> <span data-ttu-id="46a17-127">Bkz: [gölgeleri](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="46a17-127">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
-   `Async`  
  
     <span data-ttu-id="46a17-128">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="46a17-128">Optional.</span></span> <span data-ttu-id="46a17-129">Bkz: [zaman uyumsuz](../../../visual-basic/language-reference/modifiers/async.md).</span><span class="sxs-lookup"><span data-stu-id="46a17-129">See [Async](../../../visual-basic/language-reference/modifiers/async.md).</span></span>  
  
-   `Iterator`  
  
     <span data-ttu-id="46a17-130">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="46a17-130">Optional.</span></span> <span data-ttu-id="46a17-131">Bkz: [yineleyici](../../../visual-basic/language-reference/modifiers/iterator.md).</span><span class="sxs-lookup"><span data-stu-id="46a17-131">See [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).</span></span>  
  
-   `name`  
  
     <span data-ttu-id="46a17-132">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="46a17-132">Required.</span></span> <span data-ttu-id="46a17-133">Yordamın adı.</span><span class="sxs-lookup"><span data-stu-id="46a17-133">Name of the procedure.</span></span> <span data-ttu-id="46a17-134">Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="46a17-134">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   `typeparamlist`  
  
     <span data-ttu-id="46a17-135">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="46a17-135">Optional.</span></span> <span data-ttu-id="46a17-136">Tür parametreleri genel bir yordam listesi.</span><span class="sxs-lookup"><span data-stu-id="46a17-136">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="46a17-137">Bkz: [yazın listesi](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="46a17-137">See [Type List](type-list.md).</span></span>  
  
-   `parameterlist`  
  
     <span data-ttu-id="46a17-138">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="46a17-138">Optional.</span></span> <span data-ttu-id="46a17-139">Bu yordam parametreleri temsil eden yerel değişken adları listesi.</span><span class="sxs-lookup"><span data-stu-id="46a17-139">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="46a17-140">Bkz: [parametre listesi](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="46a17-140">See [Parameter List](parameter-list.md).</span></span>  
  
-   `returntype`  
  
     <span data-ttu-id="46a17-141">Gerekli olursa `Option Strict` olan `On`.</span><span class="sxs-lookup"><span data-stu-id="46a17-141">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="46a17-142">Bu yordam tarafından döndürülen değerin veri türü.</span><span class="sxs-lookup"><span data-stu-id="46a17-142">Data type of the value returned by this procedure.</span></span>  
  
-   `Implements`  
  
     <span data-ttu-id="46a17-143">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="46a17-143">Optional.</span></span> <span data-ttu-id="46a17-144">Bu yordam bir veya daha fazla uyguladığını gösteren `Function` yordamlar, bu yordamın içeren sınıf veya yapı tarafından uygulanan bir arabirim tanımlanan her biri.</span><span class="sxs-lookup"><span data-stu-id="46a17-144">Indicates that this procedure implements one or more `Function` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="46a17-145">Bkz: [uygulayan deyimi](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="46a17-145">See [Implements Statement](implements-statement.md).</span></span>  
  
-   `implementslist`  
  
     <span data-ttu-id="46a17-146">Gerekli olursa `Implements` sağlanır.</span><span class="sxs-lookup"><span data-stu-id="46a17-146">Required if `Implements` is supplied.</span></span> <span data-ttu-id="46a17-147">Listesi `Function` uygulanan yordamlar.</span><span class="sxs-lookup"><span data-stu-id="46a17-147">List of `Function` procedures being implemented.</span></span>  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     <span data-ttu-id="46a17-148">Her `implementedprocedure` aşağıdaki söz dizimini ve bölümleri vardır:</span><span class="sxs-lookup"><span data-stu-id="46a17-148">Each `implementedprocedure` has the following syntax and parts:</span></span>  
  
     `interface.definedname`  
  
    |<span data-ttu-id="46a17-149">Bölümü</span><span class="sxs-lookup"><span data-stu-id="46a17-149">Part</span></span>|<span data-ttu-id="46a17-150">Açıklama</span><span class="sxs-lookup"><span data-stu-id="46a17-150">Description</span></span>|  
    |---|---|  
    |`interface`|<span data-ttu-id="46a17-151">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="46a17-151">Required.</span></span> <span data-ttu-id="46a17-152">Bu yordam tarafından uygulanan bir arabirim adını sınıf veya yapı içeren.</span><span class="sxs-lookup"><span data-stu-id="46a17-152">Name of an interface implemented by this procedure's containing class or structure.</span></span>|  
    |`definedname`|<span data-ttu-id="46a17-153">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="46a17-153">Required.</span></span> <span data-ttu-id="46a17-154">Adı olarak yordamı tanımlanmış `interface`.</span><span class="sxs-lookup"><span data-stu-id="46a17-154">Name by which the procedure is defined in `interface`.</span></span>|  
  
-   `Handles`  
  
     <span data-ttu-id="46a17-155">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="46a17-155">Optional.</span></span> <span data-ttu-id="46a17-156">Bu yordam bir veya daha fazla belirli olayları işleyebilirsiniz gösterir.</span><span class="sxs-lookup"><span data-stu-id="46a17-156">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="46a17-157">Bkz: [işleme](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="46a17-157">See [Handles](handles-clause.md).</span></span>  
  
-   `eventlist`  
  
     <span data-ttu-id="46a17-158">Gerekli olursa `Handles` sağlanır.</span><span class="sxs-lookup"><span data-stu-id="46a17-158">Required if `Handles` is supplied.</span></span> <span data-ttu-id="46a17-159">Bu yordamı işleme olayların listesi.</span><span class="sxs-lookup"><span data-stu-id="46a17-159">List of events this procedure handles.</span></span>  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     <span data-ttu-id="46a17-160">Her `eventspecifier` aşağıdaki söz dizimini ve bölümleri vardır:</span><span class="sxs-lookup"><span data-stu-id="46a17-160">Each `eventspecifier` has the following syntax and parts:</span></span>  
  
     `eventvariable.event`  
  
    |<span data-ttu-id="46a17-161">Bölümü</span><span class="sxs-lookup"><span data-stu-id="46a17-161">Part</span></span>|<span data-ttu-id="46a17-162">Açıklama</span><span class="sxs-lookup"><span data-stu-id="46a17-162">Description</span></span>|  
    |---|---|  
    |`eventvariable`|<span data-ttu-id="46a17-163">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="46a17-163">Required.</span></span> <span data-ttu-id="46a17-164">Nesne değişkeni sınıf veya olayı oluşturan yapı, veri türü ile bildirilmedi.</span><span class="sxs-lookup"><span data-stu-id="46a17-164">Object variable declared with the data type of the class or structure that raises the event.</span></span>|  
    |`event`|<span data-ttu-id="46a17-165">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="46a17-165">Required.</span></span> <span data-ttu-id="46a17-166">Bu yordamı işleme olayın adı.</span><span class="sxs-lookup"><span data-stu-id="46a17-166">Name of the event this procedure handles.</span></span>|  
  
-   `statements`  
  
     <span data-ttu-id="46a17-167">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="46a17-167">Optional.</span></span> <span data-ttu-id="46a17-168">Bu yordam içinde yürütülecek deyimleri bloğu.</span><span class="sxs-lookup"><span data-stu-id="46a17-168">Block of statements to be executed within this procedure.</span></span>  
  
-   `End Function`  
  
     <span data-ttu-id="46a17-169">Bu yordamı tanımı sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="46a17-169">Terminates the definition of this procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46a17-170">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="46a17-170">Remarks</span></span>  
 <span data-ttu-id="46a17-171">Tüm yürütülebilir kod yordam içinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="46a17-171">All executable code must be inside a procedure.</span></span> <span data-ttu-id="46a17-172">Her bir yordam bir sınıf, bir yapı veya için içeren sınıf, yapı veya modülü adlandırılan bir modül içinde sırayla bildirildi.</span><span class="sxs-lookup"><span data-stu-id="46a17-172">Each procedure, in turn, is declared within a class, a structure, or a module that is referred to as the containing class, structure, or module.</span></span>  
  
 <span data-ttu-id="46a17-173">Çağrıyı yapan kod için bir değer döndürmek için kullanmak bir `Function` yordamı; Aksi takdirde kullanın bir `Sub` yordamı.</span><span class="sxs-lookup"><span data-stu-id="46a17-173">To return a value to the calling code, use a `Function` procedure; otherwise, use a `Sub` procedure.</span></span>  
  
## <a name="defining-a-function"></a><span data-ttu-id="46a17-174">Bir işlev tanımlama</span><span class="sxs-lookup"><span data-stu-id="46a17-174">Defining a Function</span></span>  
 <span data-ttu-id="46a17-175">Tanımlayabileceğiniz bir `Function` yordamı yalnızca modülü düzeyinde.</span><span class="sxs-lookup"><span data-stu-id="46a17-175">You can define a `Function` procedure only at the module level.</span></span> <span data-ttu-id="46a17-176">Bu nedenle, bir işlev bildirimi bağlamının bir sınıf, bir yapı, bir modül veya bir arabirim olmalıdır ve bir kaynak dosyası, bir ad alanı, bir yordam veya bir blok olamaz.</span><span class="sxs-lookup"><span data-stu-id="46a17-176">Therefore, the declaration context for a function must be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="46a17-177">Daha fazla bilgi için bkz: [bildirim bağlamları ve varsayılan erişim düzeyleri](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="46a17-177">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="46a17-178">`Function` Genel erişim varsayılan yordamlar.</span><span class="sxs-lookup"><span data-stu-id="46a17-178">`Function` procedures default to public access.</span></span> <span data-ttu-id="46a17-179">Erişim değiştiricileri ile erişim düzeylerine göre ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46a17-179">You can adjust their access levels with the access modifiers.</span></span>  
  
 <span data-ttu-id="46a17-180">A `Function` yordamı yordamın döndürdüğü değerin veri türü bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46a17-180">A `Function` procedure can declare the data type of the value that the procedure returns.</span></span> <span data-ttu-id="46a17-181">Herhangi bir veri türü veya numaralandırma, bir yapı, bir sınıf veya arabirim adını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46a17-181">You can specify any data type or the name of an enumeration, a structure, a class, or an interface.</span></span> <span data-ttu-id="46a17-182">Belirtmediyseniz `returntype` parametresi yordamın döndürdüğü `Object`.</span><span class="sxs-lookup"><span data-stu-id="46a17-182">If you don't specify the `returntype` parameter, the procedure returns `Object`.</span></span>  
  
 <span data-ttu-id="46a17-183">Bu yordamı kullanıyorsa `Implements` anahtar sözcüğü, içeren sınıf veya yapı de olmalıdır bir `Implements` hemen izleyen deyimi kendi `Class` veya `Structure` deyimi.</span><span class="sxs-lookup"><span data-stu-id="46a17-183">If this procedure uses the `Implements` keyword, the containing class or structure must also have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="46a17-184">`Implements` Deyim, belirtilen her bir arabirime içermelidir `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="46a17-184">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="46a17-185">Ancak, bir arabirim tarafından tanımlayan ad `Function` (içinde `definedname`) bu yordamı adıyla eşleşmesi gerekmez (içinde `name`).</span><span class="sxs-lookup"><span data-stu-id="46a17-185">However, the name by which an interface defines the `Function` (in `definedname`) doesn't need to match the name of this procedure (in `name`).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="46a17-186">Lambda ifadeleri işlev ifadeleri satır içi tanımlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46a17-186">You can use lambda expressions to define function expressions inline.</span></span> <span data-ttu-id="46a17-187">Daha fazla bilgi için bkz: [işlev ifadesi](../../../visual-basic/language-reference/operators/function-expression.md) ve [Lambda ifadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="46a17-187">For more information, see [Function Expression](../../../visual-basic/language-reference/operators/function-expression.md) and [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
## <a name="returning-from-a-function"></a><span data-ttu-id="46a17-188">Bir işlevden döndürme</span><span class="sxs-lookup"><span data-stu-id="46a17-188">Returning from a Function</span></span>  
 <span data-ttu-id="46a17-189">Zaman `Function` yordamı çağıran kodu döndürür, yürütme yordamı adlı deyimi aşağıdaki deyim ile devam eder.</span><span class="sxs-lookup"><span data-stu-id="46a17-189">When the `Function` procedure returns to the calling code, execution continues with the statement that follows the statement that called the procedure.</span></span>  
  
 <span data-ttu-id="46a17-190">Bir işlevden bir değer döndürmek için değer işlev adını atayın veya olmasını bir `Return` deyimi.</span><span class="sxs-lookup"><span data-stu-id="46a17-190">To return a value from a function, you can either assign the value to the function name or include it in a `Return` statement.</span></span>  
  
 <span data-ttu-id="46a17-191">`Return` Deyimi aynı anda dönüş değeri atar ve aşağıdaki örnekte gösterildiği gibi işlev çıkar.</span><span class="sxs-lookup"><span data-stu-id="46a17-191">The `Return` statement simultaneously assigns the return value and exits the function, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrStatements#24](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_1.vb)]  
  
 <span data-ttu-id="46a17-192">Aşağıdaki örnek, işlev adını dönüş değeri atar `myFunction` ve ardından `Exit Function` dönmek için deyimi.</span><span class="sxs-lookup"><span data-stu-id="46a17-192">The following example assigns the return value to the function name `myFunction` and then uses the `Exit Function` statement to return.</span></span>  
  
 [!code-vb[VbVbalrStatements#23](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_2.vb)]  
  
 <span data-ttu-id="46a17-193">`Exit Function` Ve `Return` deyimleri neden bir hemen çıkın bir `Function` yordamı.</span><span class="sxs-lookup"><span data-stu-id="46a17-193">The `Exit Function` and `Return` statements cause an immediate exit from a `Function` procedure.</span></span> <span data-ttu-id="46a17-194">Herhangi bir sayıda `Exit Function` ve `Return` deyimleri yordamda herhangi bir yerinde görünebilir ve karıştırabilir miyim `Exit Function` ve `Return` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="46a17-194">Any number of `Exit Function` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Function` and `Return` statements.</span></span>  
  
 <span data-ttu-id="46a17-195">Kullanırsanız `Exit Function` değerine atama olmadan `name`, belirtilen veri türü için varsayılan değer yordamı döndürür `returntype`.</span><span class="sxs-lookup"><span data-stu-id="46a17-195">If you use `Exit Function` without assigning a value to `name`, the procedure returns the default value for the data type that's specified in `returntype`.</span></span> <span data-ttu-id="46a17-196">Varsa `returntype` , yordam döndürür belirlenmezse `Nothing`, varsayılan değeri olduğu `Object`.</span><span class="sxs-lookup"><span data-stu-id="46a17-196">If `returntype` isn't specified, the procedure returns `Nothing`, which is the default value for `Object`.</span></span>  
  
## <a name="calling-a-function"></a><span data-ttu-id="46a17-197">İşlev Çağırma</span><span class="sxs-lookup"><span data-stu-id="46a17-197">Calling a Function</span></span>  
 <span data-ttu-id="46a17-198">Çağırmanız bir `Function` bir ifadede parantez içinde bağımsız değişken listesi ve ardından yordam adı kullanarak yordamı.</span><span class="sxs-lookup"><span data-stu-id="46a17-198">You call a `Function` procedure by using the procedure name, followed by the argument list in parentheses, in an expression.</span></span> <span data-ttu-id="46a17-199">Herhangi bir bağımsız değişken yalnızca sağladığını olmayan parantez kullanmayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46a17-199">You can omit the parentheses only if you aren't supplying any arguments.</span></span> <span data-ttu-id="46a17-200">Ancak, kodunuzun her zaman parantez eklerseniz, daha okunabilir durumdadır.</span><span class="sxs-lookup"><span data-stu-id="46a17-200">However, your code is more readable if you always include the parentheses.</span></span>  
  
 <span data-ttu-id="46a17-201">Çağırmanız bir `Function` herhangi bir kitaplığı çağrı aynı şekilde işlev gibi yordamı `Sqrt`, `Cos`, veya `ChrW`.</span><span class="sxs-lookup"><span data-stu-id="46a17-201">You call a `Function` procedure the same way that you call any library function such as `Sqrt`, `Cos`, or `ChrW`.</span></span>  
  
 <span data-ttu-id="46a17-202">Bir işlev kullanarak da çağırabilirsiniz `Call` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="46a17-202">You can also call a function by using the `Call` keyword.</span></span> <span data-ttu-id="46a17-203">Bu durumda, dönüş değeri göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="46a17-203">In that case, the return value is ignored.</span></span> <span data-ttu-id="46a17-204">Kullanımı `Call` anahtar sözcüğü, çoğu durumda önerilmez.</span><span class="sxs-lookup"><span data-stu-id="46a17-204">Use of the `Call` keyword isn't recommended in most cases.</span></span> <span data-ttu-id="46a17-205">Daha fazla bilgi için bkz: [Call deyimi](call-statement.md).</span><span class="sxs-lookup"><span data-stu-id="46a17-205">For more information, see [Call Statement](call-statement.md).</span></span>  
  
 <span data-ttu-id="46a17-206">Visual Basic bazen iç verimliliğini artırmak için aritmetik ifadeler yeniden düzenler.</span><span class="sxs-lookup"><span data-stu-id="46a17-206">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="46a17-207">Bu nedenle, kullanmamanız bir `Function` işlevi aynı ifadedeki değişkenlerin değerini değiştiğinde aritmetik ifadelerde yordamı.</span><span class="sxs-lookup"><span data-stu-id="46a17-207">For that reason, you shouldn't use a `Function` procedure in an arithmetic expression when the function changes the value of variables in the same expression.</span></span>  
  
## <a name="async-functions"></a><span data-ttu-id="46a17-208">Zaman uyumsuz işlevleri</span><span class="sxs-lookup"><span data-stu-id="46a17-208">Async Functions</span></span>  
 <span data-ttu-id="46a17-209">*Zaman uyumsuz* özelliği açık geri aramalar kullanarak veya birden çok işlevleri veya lambda ifadeleri kodunuzu el ile bölme olmadan zaman uyumsuz işlevleri çağırmak sağlar.</span><span class="sxs-lookup"><span data-stu-id="46a17-209">The *Async* feature allows you to invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>  
  
 <span data-ttu-id="46a17-210">Bir işlev ile işaretlerseniz [zaman uyumsuz](../../../visual-basic/language-reference/modifiers/async.md) kullanabileceğiniz değiştiricisi, [bekleme](../../../visual-basic/language-reference/operators/await-operator.md) işlevinde işleci.</span><span class="sxs-lookup"><span data-stu-id="46a17-210">If you mark a function with the [Async](../../../visual-basic/language-reference/modifiers/async.md) modifier, you can use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in the function.</span></span> <span data-ttu-id="46a17-211">Ulaştığında denetlemek bir `Await` ifadesinde `Async` işlevi, Denetim çağırana döndürür ve awaited görevi tamamlanana kadar işlevi ediyor askıya alındı.</span><span class="sxs-lookup"><span data-stu-id="46a17-211">When control reaches an `Await` expression in the `Async` function, control returns to the caller, and progress in the function is suspended until the awaited task completes.</span></span> <span data-ttu-id="46a17-212">Görev tamamlandığında yürütme işlevinde devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46a17-212">When the task is complete, execution can resume in the function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="46a17-213">Bir `Async` yordamı ya da tamamlanmamış ilk awaited nesne karşılaştığında çağırana döndürür veya sonuna alır `Async` yordamı, hangisi oluşur ilk.</span><span class="sxs-lookup"><span data-stu-id="46a17-213">An `Async` procedure returns to the caller when either it encounters the first awaited object that’s not yet complete, or it gets to the end of the `Async` procedure, whichever occurs first.</span></span>  
  
 <span data-ttu-id="46a17-214">Bir `Async` işlevi dönüş türüne sahip <xref:System.Threading.Tasks.Task%601> veya <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="46a17-214">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="46a17-215">Örnek olarak bir `Async` dönüş türüne sahip işlevi <xref:System.Threading.Tasks.Task%601> aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="46a17-215">An example of an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601> is provided below.</span></span>  
  
 <span data-ttu-id="46a17-216">Bir `Async` işlevi herhangi bildiremez [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parametreleri.</span><span class="sxs-lookup"><span data-stu-id="46a17-216">An `Async` function cannot declare any [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parameters.</span></span>  
  
 <span data-ttu-id="46a17-217">A [Sub deyimi](sub-statement.md) ile işaretlenebilir `Async` değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="46a17-217">A [Sub Statement](sub-statement.md) can also be marked with the `Async` modifier.</span></span> <span data-ttu-id="46a17-218">Burada bir değer döndürülemiyor bu olay işleyicileri için temel olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="46a17-218">This is primarily used for event handlers, where a value cannot be returned.</span></span> <span data-ttu-id="46a17-219">Bir `Async``Sub` yordamı beklemenin olamaz ve çağıran bir `Async``Sub` yordam tarafından oluşturulan özel durumları yakalama olamaz `Sub` yordamı.</span><span class="sxs-lookup"><span data-stu-id="46a17-219">An `Async``Sub` procedure can't be awaited, and the caller of an `Async``Sub` procedure can't catch exceptions that are thrown by the `Sub` procedure.</span></span>  
  
 <span data-ttu-id="46a17-220">Hakkında daha fazla bilgi için `Async` İşlevler, bkz: [uyumsuz ve bekleme ile zaman uyumsuz programlama](../../../visual-basic/programming-guide/concepts/async/index.md), [akış denetimi zaman uyumsuz programlarda](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), ve [zaman uyumsuz dönüş türleri](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="46a17-220">For more information about `Async` functions, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="iterator-functions"></a><span data-ttu-id="46a17-221">Yineleyici işlevleri</span><span class="sxs-lookup"><span data-stu-id="46a17-221">Iterator Functions</span></span>  
 <span data-ttu-id="46a17-222">Bir *yineleyici* işlevi bir liste veya dizi gibi bir koleksiyon üzerinden özel bir yineleme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="46a17-222">An *iterator* function performs a custom iteration over a collection, such as a list or array.</span></span> <span data-ttu-id="46a17-223">Yineleyici işlevini kullanıyor [verim](yield-statement.md) her öğeye aynı anda geri dönmek için deyimi.</span><span class="sxs-lookup"><span data-stu-id="46a17-223">An iterator function uses the [Yield](yield-statement.md) statement to return each element one at a time.</span></span> <span data-ttu-id="46a17-224">Zaman bir [verim](yield-statement.md) deyimi ulaşıldığında geçerli kod konumda anımsanacak.</span><span class="sxs-lookup"><span data-stu-id="46a17-224">When a [Yield](yield-statement.md) statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="46a17-225">Yürütme o konumdan yineleyici işlevi bir sonraki zamana yeniden başlatılır.</span><span class="sxs-lookup"><span data-stu-id="46a17-225">Execution is restarted from that location the next time the iterator function is called.</span></span>  
  
 <span data-ttu-id="46a17-226">Yineleyici kullanarak istemci kodundan çağıran bir [For Each... Sonraki](for-each-next-statement.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="46a17-226">You call an iterator from client code by using a [For Each…Next](for-each-next-statement.md) statement.</span></span>  
  
 <span data-ttu-id="46a17-227">Bir yineleyici işlevinin dönüş türü olabilir <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, veya <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="46a17-227">The return type of an iterator function can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="46a17-228">Daha fazla bilgi için bkz: [yineleyiciler](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="46a17-228">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="46a17-229">Örnek</span><span class="sxs-lookup"><span data-stu-id="46a17-229">Example</span></span>  
 <span data-ttu-id="46a17-230">Aşağıdaki örnek kullanır `Function` ad, parametreleri ve gövdesini kodu bildirmek için deyimi bir `Function` yordamı.</span><span class="sxs-lookup"><span data-stu-id="46a17-230">The following example uses the `Function` statement to declare the name, parameters, and code that form the body of a `Function` procedure.</span></span> <span data-ttu-id="46a17-231">`ParamArray` Değiştiricisi değişken sayıda bağımsız değişken kabul etmek işlevi sağlar.</span><span class="sxs-lookup"><span data-stu-id="46a17-231">The `ParamArray` modifier enables the function to accept a variable number of arguments.</span></span>  
  
 [!code-vb[VbVbalrStatements#25](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="46a17-232">Örnek</span><span class="sxs-lookup"><span data-stu-id="46a17-232">Example</span></span>  
 <span data-ttu-id="46a17-233">Aşağıdaki örnek, önceki örnekte bildirilen işlevi çağırır.</span><span class="sxs-lookup"><span data-stu-id="46a17-233">The following example invokes the function declared in the preceding example.</span></span>  
  
 [!code-vb[VbVbalrStatements#26](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="46a17-234">Örnek</span><span class="sxs-lookup"><span data-stu-id="46a17-234">Example</span></span>  
 <span data-ttu-id="46a17-235">Aşağıdaki örnekte, `DelayAsync` olan bir `Async``Function` dönüş türüne sahip <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="46a17-235">In the following example, `DelayAsync` is an `Async``Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="46a17-236">`DelayAsync` sahip bir `Return` deyimi bir tamsayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="46a17-236">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="46a17-237">Bu nedenle işlev bildirimi `DelayAsync` dönüş türüne sahip olması `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="46a17-237">Therefore the function declaration of `DelayAsync` needs to have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="46a17-238">Dönüş türü olduğundan `Task(Of Integer)`, değerlendirmesi `Await` ifadesinde `DoSomethingAsync` tamsayı üretir.</span><span class="sxs-lookup"><span data-stu-id="46a17-238">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer.</span></span> <span data-ttu-id="46a17-239">Bu bu deyim içinde gösterilmiştir: `Dim result As Integer = Await delayTask`.</span><span class="sxs-lookup"><span data-stu-id="46a17-239">This is demonstrated in this statement: `Dim result As Integer = Await delayTask`.</span></span>  
  
 <span data-ttu-id="46a17-240">`startButton_Click` Yordamdır örneği bir `Async Sub` yordamı.</span><span class="sxs-lookup"><span data-stu-id="46a17-240">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="46a17-241">Çünkü `DoSomethingAsync` olan bir `Async` işlevi, görev çağrısı için `DoSomethingAsync` aşağıdaki ifadeyi gösterdiği gibi beklemenin gerekir: `Await DoSomethingAsync()`.</span><span class="sxs-lookup"><span data-stu-id="46a17-241">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement demonstrates: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="46a17-242">`startButton_Click``Sub` Yordamı tanımlı, ile `Async` değiştiricisi içerdiğinden bir `Await` ifade.</span><span class="sxs-lookup"><span data-stu-id="46a17-242">The `startButton_Click``Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>  
  
 [!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/function-statement_5.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="46a17-243">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="46a17-243">See Also</span></span>  
 [<span data-ttu-id="46a17-244">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="46a17-244">Sub Statement</span></span>](sub-statement.md)  
 [<span data-ttu-id="46a17-245">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="46a17-245">Function Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)  
 [<span data-ttu-id="46a17-246">Parametre Listesi</span><span class="sxs-lookup"><span data-stu-id="46a17-246">Parameter List</span></span>](parameter-list.md)  
 [<span data-ttu-id="46a17-247">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="46a17-247">Dim Statement</span></span>](dim-statement.md)  
 [<span data-ttu-id="46a17-248">Call Deyimi</span><span class="sxs-lookup"><span data-stu-id="46a17-248">Call Statement</span></span>](call-statement.md)  
 [<span data-ttu-id="46a17-249">,</span><span class="sxs-lookup"><span data-stu-id="46a17-249">Of</span></span>](of-clause.md)  
 [<span data-ttu-id="46a17-250">Parametre Dizileri</span><span class="sxs-lookup"><span data-stu-id="46a17-250">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)  
 [<span data-ttu-id="46a17-251">Nasıl yapılır: Genel Bir Sınıf Kullanma</span><span class="sxs-lookup"><span data-stu-id="46a17-251">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [<span data-ttu-id="46a17-252">Yordam Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="46a17-252">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)  
 [<span data-ttu-id="46a17-253">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="46a17-253">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [<span data-ttu-id="46a17-254">İşlev İfadesi</span><span class="sxs-lookup"><span data-stu-id="46a17-254">Function Expression</span></span>](../../../visual-basic/language-reference/operators/function-expression.md)
