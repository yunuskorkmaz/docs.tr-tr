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
ms.openlocfilehash: 046a3a7d50d15cd3e59205998554a4c330d4552c
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581844"
---
# <a name="function-statement-visual-basic"></a><span data-ttu-id="51dfa-102">Function Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="51dfa-102">Function Statement (Visual Basic)</span></span>

<span data-ttu-id="51dfa-103">Bir `Function` yordamını tanımlayan adı, parametreleri ve kodu bildirir.</span><span class="sxs-lookup"><span data-stu-id="51dfa-103">Declares the name, parameters, and code that define a `Function` procedure.</span></span>

## <a name="syntax"></a><span data-ttu-id="51dfa-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="51dfa-104">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async | Iterator ]
Function name [ (Of typeparamlist) ] [ (parameterlist) ] [ As returntype ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Function ]
    [ statements ]
End Function
```

## <a name="parts"></a><span data-ttu-id="51dfa-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="51dfa-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="51dfa-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="51dfa-106">Optional.</span></span> <span data-ttu-id="51dfa-107">Bkz. [öznitelik listesi](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="51dfa-107">See [Attribute List](attribute-list.md).</span></span>

- `accessmodifier`

  <span data-ttu-id="51dfa-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="51dfa-108">Optional.</span></span> <span data-ttu-id="51dfa-109">Aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="51dfa-109">Can be one of the following:</span></span>

  - [<span data-ttu-id="51dfa-110">Public</span><span class="sxs-lookup"><span data-stu-id="51dfa-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)

  - [<span data-ttu-id="51dfa-111">Protected</span><span class="sxs-lookup"><span data-stu-id="51dfa-111">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)

  - [<span data-ttu-id="51dfa-112">Friend</span><span class="sxs-lookup"><span data-stu-id="51dfa-112">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)

  - [<span data-ttu-id="51dfa-113">Private</span><span class="sxs-lookup"><span data-stu-id="51dfa-113">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)

  - [<span data-ttu-id="51dfa-114">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="51dfa-114">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md)

  - [<span data-ttu-id="51dfa-115">Private Protected</span><span class="sxs-lookup"><span data-stu-id="51dfa-115">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)

  <span data-ttu-id="51dfa-116">[Visual Basic erişim düzeylerine](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="51dfa-116">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `proceduremodifiers`

  <span data-ttu-id="51dfa-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="51dfa-117">Optional.</span></span> <span data-ttu-id="51dfa-118">Aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="51dfa-118">Can be one of the following:</span></span>

  - [<span data-ttu-id="51dfa-119">Overloads</span><span class="sxs-lookup"><span data-stu-id="51dfa-119">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)

  - [<span data-ttu-id="51dfa-120">Overrides</span><span class="sxs-lookup"><span data-stu-id="51dfa-120">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)

  - [<span data-ttu-id="51dfa-121">Overridable</span><span class="sxs-lookup"><span data-stu-id="51dfa-121">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)

  - [<span data-ttu-id="51dfa-122">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="51dfa-122">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)

  - [<span data-ttu-id="51dfa-123">MustOverride</span><span class="sxs-lookup"><span data-stu-id="51dfa-123">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  <span data-ttu-id="51dfa-124">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="51dfa-124">Optional.</span></span> <span data-ttu-id="51dfa-125">Bkz. [paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="51dfa-125">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="51dfa-126">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="51dfa-126">Optional.</span></span> <span data-ttu-id="51dfa-127">Bkz. [gölgeler](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="51dfa-127">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>

- `Async`

  <span data-ttu-id="51dfa-128">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="51dfa-128">Optional.</span></span> <span data-ttu-id="51dfa-129">Bkz. [zaman uyumsuz](../../../visual-basic/language-reference/modifiers/async.md).</span><span class="sxs-lookup"><span data-stu-id="51dfa-129">See [Async](../../../visual-basic/language-reference/modifiers/async.md).</span></span>

- `Iterator`

  <span data-ttu-id="51dfa-130">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="51dfa-130">Optional.</span></span> <span data-ttu-id="51dfa-131">Bkz. [Yineleyici](../../../visual-basic/language-reference/modifiers/iterator.md).</span><span class="sxs-lookup"><span data-stu-id="51dfa-131">See [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).</span></span>

- `name`

  <span data-ttu-id="51dfa-132">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="51dfa-132">Required.</span></span> <span data-ttu-id="51dfa-133">Yordamın adı.</span><span class="sxs-lookup"><span data-stu-id="51dfa-133">Name of the procedure.</span></span> <span data-ttu-id="51dfa-134">Bkz. [tanımlanmış öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="51dfa-134">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

- `typeparamlist`

  <span data-ttu-id="51dfa-135">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="51dfa-135">Optional.</span></span> <span data-ttu-id="51dfa-136">Genel bir yordamın tür parametrelerinin listesi.</span><span class="sxs-lookup"><span data-stu-id="51dfa-136">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="51dfa-137">Bkz. [tür listesi](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="51dfa-137">See [Type List](type-list.md).</span></span>

- `parameterlist`

  <span data-ttu-id="51dfa-138">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="51dfa-138">Optional.</span></span> <span data-ttu-id="51dfa-139">Bu yordamın parametrelerini temsil eden yerel değişken adlarının listesi.</span><span class="sxs-lookup"><span data-stu-id="51dfa-139">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="51dfa-140">Bkz. [parametre listesi](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="51dfa-140">See [Parameter List](parameter-list.md).</span></span>

- `returntype`

  <span data-ttu-id="51dfa-141">@No__t_0 `On` olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="51dfa-141">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="51dfa-142">Bu yordamın döndürdüğü değerin veri türü.</span><span class="sxs-lookup"><span data-stu-id="51dfa-142">Data type of the value returned by this procedure.</span></span>

- `Implements`

  <span data-ttu-id="51dfa-143">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="51dfa-143">Optional.</span></span> <span data-ttu-id="51dfa-144">Bu yordamın, her biri bu yordamın kapsayan sınıf veya yapı tarafından uygulanan bir arabirimde tanımlanan bir veya daha fazla `Function` yordamlarını uyguladığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="51dfa-144">Indicates that this procedure implements one or more `Function` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="51dfa-145">Bkz. [Implements açıklaması](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="51dfa-145">See [Implements Statement](implements-statement.md).</span></span>

- `implementslist`

  <span data-ttu-id="51dfa-146">@No__t_0 sağlanırsa gereklidir.</span><span class="sxs-lookup"><span data-stu-id="51dfa-146">Required if `Implements` is supplied.</span></span> <span data-ttu-id="51dfa-147">Uygulanan `Function` yordamlarının listesi.</span><span class="sxs-lookup"><span data-stu-id="51dfa-147">List of `Function` procedures being implemented.</span></span>

  `implementedprocedure [ , implementedprocedure ... ]`

  <span data-ttu-id="51dfa-148">Her `implementedprocedure` aşağıdaki söz dizimi ve bölümlere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="51dfa-148">Each `implementedprocedure` has the following syntax and parts:</span></span>

  `interface.definedname`

  |<span data-ttu-id="51dfa-149">Bölümüyle</span><span class="sxs-lookup"><span data-stu-id="51dfa-149">Part</span></span>|<span data-ttu-id="51dfa-150">Açıklama</span><span class="sxs-lookup"><span data-stu-id="51dfa-150">Description</span></span>|
  |---|---|
  |`interface`|<span data-ttu-id="51dfa-151">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="51dfa-151">Required.</span></span> <span data-ttu-id="51dfa-152">Bu yordamın kapsayan sınıf veya yapı tarafından uygulanan bir arabirimin adı.</span><span class="sxs-lookup"><span data-stu-id="51dfa-152">Name of an interface implemented by this procedure's containing class or structure.</span></span>|
  |`definedname`|<span data-ttu-id="51dfa-153">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="51dfa-153">Required.</span></span> <span data-ttu-id="51dfa-154">Yordamın `interface` tanımladığı ad.</span><span class="sxs-lookup"><span data-stu-id="51dfa-154">Name by which the procedure is defined in `interface`.</span></span>|

- `Handles`

  <span data-ttu-id="51dfa-155">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="51dfa-155">Optional.</span></span> <span data-ttu-id="51dfa-156">Bu yordamın bir veya daha fazla belirli olayı işleyebileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="51dfa-156">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="51dfa-157">Bkz. [işleyiciler](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="51dfa-157">See [Handles](handles-clause.md).</span></span>

- `eventlist`

  <span data-ttu-id="51dfa-158">@No__t_0 sağlanırsa gereklidir.</span><span class="sxs-lookup"><span data-stu-id="51dfa-158">Required if `Handles` is supplied.</span></span> <span data-ttu-id="51dfa-159">Bu yordamın işleyeceği olayların listesi.</span><span class="sxs-lookup"><span data-stu-id="51dfa-159">List of events this procedure handles.</span></span>

  `eventspecifier [ , eventspecifier ... ]`

  <span data-ttu-id="51dfa-160">Her `eventspecifier` aşağıdaki söz dizimi ve bölümlere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="51dfa-160">Each `eventspecifier` has the following syntax and parts:</span></span>

  `eventvariable.event`

  |<span data-ttu-id="51dfa-161">Bölümüyle</span><span class="sxs-lookup"><span data-stu-id="51dfa-161">Part</span></span>|<span data-ttu-id="51dfa-162">Açıklama</span><span class="sxs-lookup"><span data-stu-id="51dfa-162">Description</span></span>|
  |---|---|
  |`eventvariable`|<span data-ttu-id="51dfa-163">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="51dfa-163">Required.</span></span> <span data-ttu-id="51dfa-164">Olayı oluşturan sınıfın veya yapının veri türüyle belirtilen nesne değişkeni.</span><span class="sxs-lookup"><span data-stu-id="51dfa-164">Object variable declared with the data type of the class or structure that raises the event.</span></span>|
  |`event`|<span data-ttu-id="51dfa-165">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="51dfa-165">Required.</span></span> <span data-ttu-id="51dfa-166">Bu yordamın işleyeceği olayın adı.</span><span class="sxs-lookup"><span data-stu-id="51dfa-166">Name of the event this procedure handles.</span></span>|

- `statements`

  <span data-ttu-id="51dfa-167">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="51dfa-167">Optional.</span></span> <span data-ttu-id="51dfa-168">Bu yordamda yürütülecek deyim bloğu.</span><span class="sxs-lookup"><span data-stu-id="51dfa-168">Block of statements to be executed within this procedure.</span></span>

- `End Function`

  <span data-ttu-id="51dfa-169">Bu yordamın tanımını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="51dfa-169">Terminates the definition of this procedure.</span></span>

## <a name="remarks"></a><span data-ttu-id="51dfa-170">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="51dfa-170">Remarks</span></span>

<span data-ttu-id="51dfa-171">Tüm yürütülebilir kodların bir yordamın içinde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="51dfa-171">All executable code must be inside a procedure.</span></span> <span data-ttu-id="51dfa-172">Her yordam, sırasıyla bir sınıf, yapı veya kapsayan sınıf, yapı veya modül olarak başvurulan bir modül içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="51dfa-172">Each procedure, in turn, is declared within a class, a structure, or a module that is referred to as the containing class, structure, or module.</span></span>

<span data-ttu-id="51dfa-173">Çağırma koduna bir değer döndürmek için `Function` yordamı kullanın; Aksi takdirde, `Sub` prosedürü kullanın.</span><span class="sxs-lookup"><span data-stu-id="51dfa-173">To return a value to the calling code, use a `Function` procedure; otherwise, use a `Sub` procedure.</span></span>

## <a name="defining-a-function"></a><span data-ttu-id="51dfa-174">Işlev tanımlama</span><span class="sxs-lookup"><span data-stu-id="51dfa-174">Defining a Function</span></span>

<span data-ttu-id="51dfa-175">Bir `Function` yordamını yalnızca modül düzeyinde tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51dfa-175">You can define a `Function` procedure only at the module level.</span></span> <span data-ttu-id="51dfa-176">Bu nedenle, bir işlev için bildirim bağlamı bir sınıf, yapı, modül veya arabirim olmalıdır ve kaynak dosya, bir ad alanı, yordam veya bir blok olamaz.</span><span class="sxs-lookup"><span data-stu-id="51dfa-176">Therefore, the declaration context for a function must be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="51dfa-177">Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="51dfa-177">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="51dfa-178">yordamları, genel erişim için varsayılan `Function`.</span><span class="sxs-lookup"><span data-stu-id="51dfa-178">`Function` procedures default to public access.</span></span> <span data-ttu-id="51dfa-179">Erişim değiştiricilerini kullanarak erişim düzeylerini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51dfa-179">You can adjust their access levels with the access modifiers.</span></span>

<span data-ttu-id="51dfa-180">@No__t_0 yordam, yordamın döndürdüğü değerin veri türünü bildirebilirler.</span><span class="sxs-lookup"><span data-stu-id="51dfa-180">A `Function` procedure can declare the data type of the value that the procedure returns.</span></span> <span data-ttu-id="51dfa-181">Herhangi bir veri türü veya bir numaralandırma, bir yapı, sınıf veya arabirim adı belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51dfa-181">You can specify any data type or the name of an enumeration, a structure, a class, or an interface.</span></span> <span data-ttu-id="51dfa-182">@No__t_0 parametresini belirtmezseniz, yordam `Object` döndürür.</span><span class="sxs-lookup"><span data-stu-id="51dfa-182">If you don't specify the `returntype` parameter, the procedure returns `Object`.</span></span>

<span data-ttu-id="51dfa-183">Bu yordam `Implements` anahtar sözcüğünü kullanıyorsa, kapsayan sınıf veya yapının, `Class` veya `Structure` bildirisini hemen izleyen bir `Implements` ifadesine de sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="51dfa-183">If this procedure uses the `Implements` keyword, the containing class or structure must also have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="51dfa-184">@No__t_0 deyimin `implementslist` belirtilen her arabirimi içermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="51dfa-184">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="51dfa-185">Ancak, bir arabirimin `Function` tanımladığı adın (`definedname`) bu yordamın adıyla eşleşmesi gerekmez (`name`).</span><span class="sxs-lookup"><span data-stu-id="51dfa-185">However, the name by which an interface defines the `Function` (in `definedname`) doesn't need to match the name of this procedure (in `name`).</span></span>

> [!NOTE]
> <span data-ttu-id="51dfa-186">İşlev ifadelerini satır içi olarak tanımlamak için lambda ifadeleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51dfa-186">You can use lambda expressions to define function expressions inline.</span></span> <span data-ttu-id="51dfa-187">Daha fazla bilgi için bkz. [Işlev ifadesi](../../../visual-basic/language-reference/operators/function-expression.md) ve [lambda ifadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="51dfa-187">For more information, see [Function Expression](../../../visual-basic/language-reference/operators/function-expression.md) and [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>

## <a name="returning-from-a-function"></a><span data-ttu-id="51dfa-188">Bir Işlevden dönme</span><span class="sxs-lookup"><span data-stu-id="51dfa-188">Returning from a Function</span></span>

<span data-ttu-id="51dfa-189">@No__t_0 yordamı çağıran koda döndüğünde, yürütme yordamı çağıran deyimden sonraki deyimle devam eder.</span><span class="sxs-lookup"><span data-stu-id="51dfa-189">When the `Function` procedure returns to the calling code, execution continues with the statement that follows the statement that called the procedure.</span></span>

<span data-ttu-id="51dfa-190">Bir işlevden bir değer döndürmek için, değeri işlev adına atayabilir veya bir `Return` ifadesine dahil edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51dfa-190">To return a value from a function, you can either assign the value to the function name or include it in a `Return` statement.</span></span>

<span data-ttu-id="51dfa-191">@No__t_0 deyimin döndürdüğü değeri aynı anda atar ve aşağıdaki örnekte gösterildiği gibi işlevden çıkar.</span><span class="sxs-lookup"><span data-stu-id="51dfa-191">The `Return` statement simultaneously assigns the return value and exits the function, as the following example shows.</span></span>

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

<span data-ttu-id="51dfa-192">Aşağıdaki örnek, `myFunction` işlev adına döndürülen değeri atar ve sonra geri dönmek için `Exit Function` ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="51dfa-192">The following example assigns the return value to the function name `myFunction` and then uses the `Exit Function` statement to return.</span></span>

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

<span data-ttu-id="51dfa-193">@No__t_0 ve `Return` deyimleri, bir `Function` yordamından anında çıkış oluşmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="51dfa-193">The `Exit Function` and `Return` statements cause an immediate exit from a `Function` procedure.</span></span> <span data-ttu-id="51dfa-194">Herhangi bir sayıda `Exit Function` ve `Return` deyimi yordamda herhangi bir yerde görünebilir ve `Exit Function` ve `Return` deyimlerini karıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51dfa-194">Any number of `Exit Function` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Function` and `Return` statements.</span></span>

<span data-ttu-id="51dfa-195">@No__t_1 bir değer atamadan `Exit Function` kullanırsanız yordam, `returntype` belirtilen veri türü için varsayılan değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="51dfa-195">If you use `Exit Function` without assigning a value to `name`, the procedure returns the default value for the data type that's specified in `returntype`.</span></span> <span data-ttu-id="51dfa-196">@No__t_0 belirtilmemişse, yordam, `Object` için varsayılan değer olan `Nothing` döndürür.</span><span class="sxs-lookup"><span data-stu-id="51dfa-196">If `returntype` isn't specified, the procedure returns `Nothing`, which is the default value for `Object`.</span></span>

## <a name="calling-a-function"></a><span data-ttu-id="51dfa-197">İşlev Çağırma</span><span class="sxs-lookup"><span data-stu-id="51dfa-197">Calling a Function</span></span>

<span data-ttu-id="51dfa-198">Yordam adını, ardından parantez içindeki bağımsız değişken listesini kullanarak bir ifadede bir `Function` yordamını çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51dfa-198">You call a `Function` procedure by using the procedure name, followed by the argument list in parentheses, in an expression.</span></span> <span data-ttu-id="51dfa-199">Parantezleri yalnızca herhangi bir bağımsız değişken belirtmezseniz atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51dfa-199">You can omit the parentheses only if you aren't supplying any arguments.</span></span> <span data-ttu-id="51dfa-200">Ancak, her zaman parantezleri eklerseniz kodunuz daha okunabilir.</span><span class="sxs-lookup"><span data-stu-id="51dfa-200">However, your code is more readable if you always include the parentheses.</span></span>

<span data-ttu-id="51dfa-201">Bir `Function` yordamını, `Sqrt`, `Cos` veya `ChrW` gibi herhangi bir kitaplık işlevini çağırdığınız şekilde çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51dfa-201">You call a `Function` procedure the same way that you call any library function such as `Sqrt`, `Cos`, or `ChrW`.</span></span>

<span data-ttu-id="51dfa-202">Ayrıca, `Call` anahtar sözcüğünü kullanarak bir işlevi çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51dfa-202">You can also call a function by using the `Call` keyword.</span></span> <span data-ttu-id="51dfa-203">Bu durumda, dönüş değeri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="51dfa-203">In that case, the return value is ignored.</span></span> <span data-ttu-id="51dfa-204">Çoğu durumda `Call` anahtar sözcüğünün kullanılması önerilmez.</span><span class="sxs-lookup"><span data-stu-id="51dfa-204">Use of the `Call` keyword isn't recommended in most cases.</span></span> <span data-ttu-id="51dfa-205">Daha fazla bilgi için bkz. [Call deyimleri](call-statement.md).</span><span class="sxs-lookup"><span data-stu-id="51dfa-205">For more information, see [Call Statement](call-statement.md).</span></span>

<span data-ttu-id="51dfa-206">Visual Basic bazen, iç verimliliği artırmak için aritmetik ifadeleri yeniden düzenler.</span><span class="sxs-lookup"><span data-stu-id="51dfa-206">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="51dfa-207">Bu nedenle, işlev aynı ifadedeki değişkenlerin değerini değiştirdiğinde bir aritmetik ifadede `Function` yordamı kullanmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="51dfa-207">For that reason, you shouldn't use a `Function` procedure in an arithmetic expression when the function changes the value of variables in the same expression.</span></span>

## <a name="async-functions"></a><span data-ttu-id="51dfa-208">Zaman uyumsuz Işlevler</span><span class="sxs-lookup"><span data-stu-id="51dfa-208">Async Functions</span></span>

<span data-ttu-id="51dfa-209">*Async* özelliği, açık geri çağırmaları kullanmadan veya kodunuzu birden çok işlev veya lambda ifadesine el ile bölmeden zaman uyumsuz işlevleri çağırabilmeniz için izin verir.</span><span class="sxs-lookup"><span data-stu-id="51dfa-209">The *Async* feature allows you to invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>

<span data-ttu-id="51dfa-210">Bir işlevi [zaman uyumsuz](../../../visual-basic/language-reference/modifiers/async.md) değiştiriciyle işaretlerseniz, işlevindeki [await](../../../visual-basic/language-reference/operators/await-operator.md) işlecini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51dfa-210">If you mark a function with the [Async](../../../visual-basic/language-reference/modifiers/async.md) modifier, you can use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in the function.</span></span> <span data-ttu-id="51dfa-211">Denetim, `Async` işlevindeki bir `Await` ifadesine ulaştığında, Denetim çağırana döner ve beklenen görev tamamlanana kadar işlevdeki ilerleme durumu askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="51dfa-211">When control reaches an `Await` expression in the `Async` function, control returns to the caller, and progress in the function is suspended until the awaited task completes.</span></span> <span data-ttu-id="51dfa-212">Görev tamamlandığında, yürütme işlevinde çalışmaya çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="51dfa-212">When the task is complete, execution can resume in the function.</span></span>

> [!NOTE]
> <span data-ttu-id="51dfa-213">Bir `Async` yordam, henüz tamamlanmamış olan ilk beklemiş nesneyle karşılaştığında arayan öğesine geri döner veya `Async` yordamının sonuna, hangisi önce gerçekleştiğine gelir.</span><span class="sxs-lookup"><span data-stu-id="51dfa-213">An `Async` procedure returns to the caller when either it encounters the first awaited object that’s not yet complete, or it gets to the end of the `Async` procedure, whichever occurs first.</span></span>

<span data-ttu-id="51dfa-214">@No__t_0 işlevi <xref:System.Threading.Tasks.Task%601> veya <xref:System.Threading.Tasks.Task> dönüş türüne sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="51dfa-214">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="51dfa-215">Aşağıda <xref:System.Threading.Tasks.Task%601> dönüş türüne sahip `Async` işleve bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="51dfa-215">An example of an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601> is provided below.</span></span>

<span data-ttu-id="51dfa-216">Bir `Async` işlevi herhangi bir [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parametresi bildiremeyebilir.</span><span class="sxs-lookup"><span data-stu-id="51dfa-216">An `Async` function cannot declare any [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parameters.</span></span>

<span data-ttu-id="51dfa-217">Bir [alt ifade](sub-statement.md) `Async` değiştiricisi ile de işaretlenebilir.</span><span class="sxs-lookup"><span data-stu-id="51dfa-217">A [Sub Statement](sub-statement.md) can also be marked with the `Async` modifier.</span></span> <span data-ttu-id="51dfa-218">Bu, öncelikle bir değer döndürülmediğinde olay işleyicileri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="51dfa-218">This is primarily used for event handlers, where a value cannot be returned.</span></span> <span data-ttu-id="51dfa-219">Bir `Async` `Sub` yordamı beklelenemez ve `Async` `Sub` yordamının çağıranı `Sub` yordamı tarafından oluşturulan özel durumları yakalayamaz.</span><span class="sxs-lookup"><span data-stu-id="51dfa-219">An `Async` `Sub` procedure can't be awaited, and the caller of an `Async` `Sub` procedure can't catch exceptions that are thrown by the `Sub` procedure.</span></span>

<span data-ttu-id="51dfa-220">@No__t_0 işlevleri hakkında daha fazla bilgi için bkz. [Async ve await Ile zaman uyumsuz programlama](../../../visual-basic/programming-guide/concepts/async/index.md), [zaman uyumsuz programlarda denetim akışı](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)ve [zaman uyumsuz dönüş türleri](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="51dfa-220">For more information about `Async` functions, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>

## <a name="iterator-functions"></a><span data-ttu-id="51dfa-221">Yineleyici Işlevleri</span><span class="sxs-lookup"><span data-stu-id="51dfa-221">Iterator Functions</span></span>

<span data-ttu-id="51dfa-222">*Yineleyici* işlevi, bir koleksiyon üzerinde liste veya dizi gibi özel bir yineleme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="51dfa-222">An *iterator* function performs a custom iteration over a collection, such as a list or array.</span></span> <span data-ttu-id="51dfa-223">Yineleyici işlevi, her öğeyi birer birer döndürmek için [yield](yield-statement.md) ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="51dfa-223">An iterator function uses the [Yield](yield-statement.md) statement to return each element one at a time.</span></span> <span data-ttu-id="51dfa-224">Bir [yield](yield-statement.md) ifadesine ulaşıldığında, koddaki geçerli konum hatırlanır.</span><span class="sxs-lookup"><span data-stu-id="51dfa-224">When a [Yield](yield-statement.md) statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="51dfa-225">Bu konumdan, Yineleyici işlevinin bir sonraki çağrılışında yürütme yeniden başlatılır.</span><span class="sxs-lookup"><span data-stu-id="51dfa-225">Execution is restarted from that location the next time the iterator function is called.</span></span>

<span data-ttu-id="51dfa-226">Her biri Için bir kullanarak istemci kodundan bir yineleyici çağırın [... Sonraki](for-each-next-statement.md) ifade.</span><span class="sxs-lookup"><span data-stu-id="51dfa-226">You call an iterator from client code by using a [For Each…Next](for-each-next-statement.md) statement.</span></span>

<span data-ttu-id="51dfa-227">Yineleyici işlevinin dönüş türü <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator> veya <xref:System.Collections.Generic.IEnumerator%601> olabilir.</span><span class="sxs-lookup"><span data-stu-id="51dfa-227">The return type of an iterator function can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="51dfa-228">Daha fazla bilgi için bkz. [yineleyiciler](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="51dfa-228">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>

## <a name="example"></a><span data-ttu-id="51dfa-229">Örnek</span><span class="sxs-lookup"><span data-stu-id="51dfa-229">Example</span></span>

<span data-ttu-id="51dfa-230">Aşağıdaki örnek, bir `Function` yordamının gövdesini oluşturan adı, parametreleri ve kodu bildirmek için `Function` bildirimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="51dfa-230">The following example uses the `Function` statement to declare the name, parameters, and code that form the body of a `Function` procedure.</span></span> <span data-ttu-id="51dfa-231">@No__t_0 değiştiricisi, işlevin değişken sayıda bağımsız değişken kabul etmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="51dfa-231">The `ParamArray` modifier enables the function to accept a variable number of arguments.</span></span>

[!code-vb[VbVbalrStatements#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#25)]

## <a name="example"></a><span data-ttu-id="51dfa-232">Örnek</span><span class="sxs-lookup"><span data-stu-id="51dfa-232">Example</span></span>

<span data-ttu-id="51dfa-233">Aşağıdaki örnek, önceki örnekte belirtilen işlevi çağırır.</span><span class="sxs-lookup"><span data-stu-id="51dfa-233">The following example invokes the function declared in the preceding example.</span></span>

[!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]

## <a name="example"></a><span data-ttu-id="51dfa-234">Örnek</span><span class="sxs-lookup"><span data-stu-id="51dfa-234">Example</span></span>

<span data-ttu-id="51dfa-235">Aşağıdaki örnekte, `DelayAsync` dönüş türü <xref:System.Threading.Tasks.Task%601> olan bir `Async` `Function`.</span><span class="sxs-lookup"><span data-stu-id="51dfa-235">In the following example, `DelayAsync` is an `Async` `Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="51dfa-236">`DelayAsync`, bir tamsayı döndüren bir `Return` bildirimine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="51dfa-236">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="51dfa-237">Bu nedenle `DelayAsync` işlev bildiriminin `Task(Of Integer)` dönüş türü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="51dfa-237">Therefore the function declaration of `DelayAsync` needs to have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="51dfa-238">Dönüş türü `Task(Of Integer)` olduğundan, `DoSomethingAsync` `Await` ifadesinin değerlendirmesi bir tamsayı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="51dfa-238">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer.</span></span> <span data-ttu-id="51dfa-239">Bu bildirimde gösterilmiştir: `Dim result As Integer = Await delayTask`.</span><span class="sxs-lookup"><span data-stu-id="51dfa-239">This is demonstrated in this statement: `Dim result As Integer = Await delayTask`.</span></span>

<span data-ttu-id="51dfa-240">@No__t_0 yordam bir `Async Sub` yordamının bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="51dfa-240">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="51dfa-241">@No__t_0 bir `Async` işlevi olduğundan, aşağıdaki ifadede gösterildiği gibi, `DoSomethingAsync` çağrısı için de beklenen bir görev olmalıdır: `Await DoSomethingAsync()`.</span><span class="sxs-lookup"><span data-stu-id="51dfa-241">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement demonstrates: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="51dfa-242">Bir `Await` ifadesi içerdiğinden `startButton_Click` `Sub` yordamının `Async` değiştiricisi ile tanımlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="51dfa-242">The `startButton_Click` `Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a><span data-ttu-id="51dfa-243">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51dfa-243">See also</span></span>

- [<span data-ttu-id="51dfa-244">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="51dfa-244">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="51dfa-245">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="51dfa-245">Function Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)
- [<span data-ttu-id="51dfa-246">Parametre Listesi</span><span class="sxs-lookup"><span data-stu-id="51dfa-246">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="51dfa-247">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="51dfa-247">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="51dfa-248">Call Deyimi</span><span class="sxs-lookup"><span data-stu-id="51dfa-248">Call Statement</span></span>](call-statement.md)
- [<span data-ttu-id="51dfa-249">Durumunu</span><span class="sxs-lookup"><span data-stu-id="51dfa-249">Of</span></span>](of-clause.md)
- [<span data-ttu-id="51dfa-250">Parametre Dizileri</span><span class="sxs-lookup"><span data-stu-id="51dfa-250">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
- [<span data-ttu-id="51dfa-251">Nasıl yapılır: Genel Bir Sınıf Kullanma</span><span class="sxs-lookup"><span data-stu-id="51dfa-251">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="51dfa-252">Yordam Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="51dfa-252">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [<span data-ttu-id="51dfa-253">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="51dfa-253">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="51dfa-254">İşlev İfadesi</span><span class="sxs-lookup"><span data-stu-id="51dfa-254">Function Expression</span></span>](../../../visual-basic/language-reference/operators/function-expression.md)
