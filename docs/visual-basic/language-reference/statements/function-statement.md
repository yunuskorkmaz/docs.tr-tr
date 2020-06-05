---
title: Function Deyimi
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
ms.openlocfilehash: 49cf4fead2c5594b7ac6815f82fea0dc995ea436
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404634"
---
# <a name="function-statement-visual-basic"></a><span data-ttu-id="d50bf-102">Function Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d50bf-102">Function Statement (Visual Basic)</span></span>

<span data-ttu-id="d50bf-103">Bir yordamı tanımlayan adı, parametreleri ve kodu bildirir `Function` .</span><span class="sxs-lookup"><span data-stu-id="d50bf-103">Declares the name, parameters, and code that define a `Function` procedure.</span></span>

## <a name="syntax"></a><span data-ttu-id="d50bf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d50bf-104">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async | Iterator ]
Function name [ (Of typeparamlist) ] [ (parameterlist) ] [ As returntype ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Function ]
    [ statements ]
End Function
```

## <a name="parts"></a><span data-ttu-id="d50bf-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="d50bf-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="d50bf-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d50bf-106">Optional.</span></span> <span data-ttu-id="d50bf-107">Bkz. [öznitelik listesi](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="d50bf-107">See [Attribute List](attribute-list.md).</span></span>

- `accessmodifier`

  <span data-ttu-id="d50bf-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d50bf-108">Optional.</span></span> <span data-ttu-id="d50bf-109">Aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="d50bf-109">Can be one of the following:</span></span>

  - [<span data-ttu-id="d50bf-110">Geneldir</span><span class="sxs-lookup"><span data-stu-id="d50bf-110">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="d50bf-111">Korunamadı</span><span class="sxs-lookup"><span data-stu-id="d50bf-111">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="d50bf-112">Dost</span><span class="sxs-lookup"><span data-stu-id="d50bf-112">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="d50bf-113">Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="d50bf-113">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="d50bf-114">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="d50bf-114">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="d50bf-115">Özel korumalı</span><span class="sxs-lookup"><span data-stu-id="d50bf-115">Private Protected</span></span>](../modifiers/private-protected.md)

  <span data-ttu-id="d50bf-116">[Visual Basic erişim düzeylerine](../../programming-guide/language-features/declared-elements/access-levels.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="d50bf-116">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `proceduremodifiers`

  <span data-ttu-id="d50bf-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d50bf-117">Optional.</span></span> <span data-ttu-id="d50bf-118">Aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="d50bf-118">Can be one of the following:</span></span>

  - [<span data-ttu-id="d50bf-119">Aşırı Yüklemeler</span><span class="sxs-lookup"><span data-stu-id="d50bf-119">Overloads</span></span>](../modifiers/overloads.md)

  - [<span data-ttu-id="d50bf-120">Geçersiz Kılmalar</span><span class="sxs-lookup"><span data-stu-id="d50bf-120">Overrides</span></span>](../modifiers/overrides.md)

  - [<span data-ttu-id="d50bf-121">Overridable</span><span class="sxs-lookup"><span data-stu-id="d50bf-121">Overridable</span></span>](../modifiers/overridable.md)

  - [<span data-ttu-id="d50bf-122">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="d50bf-122">NotOverridable</span></span>](../modifiers/notoverridable.md)

  - [<span data-ttu-id="d50bf-123">MustOverride</span><span class="sxs-lookup"><span data-stu-id="d50bf-123">MustOverride</span></span>](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  <span data-ttu-id="d50bf-124">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d50bf-124">Optional.</span></span> <span data-ttu-id="d50bf-125">Bkz. [paylaşılan](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="d50bf-125">See [Shared](../modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="d50bf-126">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d50bf-126">Optional.</span></span> <span data-ttu-id="d50bf-127">Bkz. [gölgeler](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="d50bf-127">See [Shadows](../modifiers/shadows.md).</span></span>

- `Async`

  <span data-ttu-id="d50bf-128">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d50bf-128">Optional.</span></span> <span data-ttu-id="d50bf-129">Bkz. [zaman uyumsuz](../modifiers/async.md).</span><span class="sxs-lookup"><span data-stu-id="d50bf-129">See [Async](../modifiers/async.md).</span></span>

- `Iterator`

  <span data-ttu-id="d50bf-130">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d50bf-130">Optional.</span></span> <span data-ttu-id="d50bf-131">Bkz. [Yineleyici](../modifiers/iterator.md).</span><span class="sxs-lookup"><span data-stu-id="d50bf-131">See [Iterator](../modifiers/iterator.md).</span></span>

- `name`

  <span data-ttu-id="d50bf-132">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d50bf-132">Required.</span></span> <span data-ttu-id="d50bf-133">Yordamın adı.</span><span class="sxs-lookup"><span data-stu-id="d50bf-133">Name of the procedure.</span></span> <span data-ttu-id="d50bf-134">Bkz. [tanımlanmış öğe adları](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="d50bf-134">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

- `typeparamlist`

  <span data-ttu-id="d50bf-135">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d50bf-135">Optional.</span></span> <span data-ttu-id="d50bf-136">Genel bir yordamın tür parametrelerinin listesi.</span><span class="sxs-lookup"><span data-stu-id="d50bf-136">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="d50bf-137">Bkz. [tür listesi](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="d50bf-137">See [Type List](type-list.md).</span></span>

- `parameterlist`

  <span data-ttu-id="d50bf-138">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d50bf-138">Optional.</span></span> <span data-ttu-id="d50bf-139">Bu yordamın parametrelerini temsil eden yerel değişken adlarının listesi.</span><span class="sxs-lookup"><span data-stu-id="d50bf-139">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="d50bf-140">Bkz. [parametre listesi](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="d50bf-140">See [Parameter List](parameter-list.md).</span></span>

- `returntype`

  <span data-ttu-id="d50bf-141">İse gereklidir `Option Strict` `On` .</span><span class="sxs-lookup"><span data-stu-id="d50bf-141">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="d50bf-142">Bu yordamın döndürdüğü değerin veri türü.</span><span class="sxs-lookup"><span data-stu-id="d50bf-142">Data type of the value returned by this procedure.</span></span>

- `Implements`

  <span data-ttu-id="d50bf-143">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d50bf-143">Optional.</span></span> <span data-ttu-id="d50bf-144">Bu yordamın `Function` , her biri bu yordamın kapsayan sınıf veya yapı tarafından uygulanan bir arabirimde tanımlanan bir veya daha fazla yordam uyguladığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d50bf-144">Indicates that this procedure implements one or more `Function` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="d50bf-145">Bkz. [Implements açıklaması](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d50bf-145">See [Implements Statement](implements-statement.md).</span></span>

- `implementslist`

  <span data-ttu-id="d50bf-146">Sağlanırsa gereklidir `Implements` .</span><span class="sxs-lookup"><span data-stu-id="d50bf-146">Required if `Implements` is supplied.</span></span> <span data-ttu-id="d50bf-147">`Function`Uygulanan yordamların listesi.</span><span class="sxs-lookup"><span data-stu-id="d50bf-147">List of `Function` procedures being implemented.</span></span>

  `implementedprocedure [ , implementedprocedure ... ]`

  <span data-ttu-id="d50bf-148">Her birinin `implementedprocedure` aşağıdaki söz dizimi ve parçaları vardır:</span><span class="sxs-lookup"><span data-stu-id="d50bf-148">Each `implementedprocedure` has the following syntax and parts:</span></span>

  `interface.definedname`

  |<span data-ttu-id="d50bf-149">Bölüm</span><span class="sxs-lookup"><span data-stu-id="d50bf-149">Part</span></span>|<span data-ttu-id="d50bf-150">Description</span><span class="sxs-lookup"><span data-stu-id="d50bf-150">Description</span></span>|
  |---|---|
  |`interface`|<span data-ttu-id="d50bf-151">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d50bf-151">Required.</span></span> <span data-ttu-id="d50bf-152">Bu yordamın kapsayan sınıf veya yapı tarafından uygulanan bir arabirimin adı.</span><span class="sxs-lookup"><span data-stu-id="d50bf-152">Name of an interface implemented by this procedure's containing class or structure.</span></span>|
  |`definedname`|<span data-ttu-id="d50bf-153">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d50bf-153">Required.</span></span> <span data-ttu-id="d50bf-154">Yordamın tanımlandığı ad `interface` .</span><span class="sxs-lookup"><span data-stu-id="d50bf-154">Name by which the procedure is defined in `interface`.</span></span>|

- `Handles`

  <span data-ttu-id="d50bf-155">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d50bf-155">Optional.</span></span> <span data-ttu-id="d50bf-156">Bu yordamın bir veya daha fazla belirli olayı işleyebileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d50bf-156">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="d50bf-157">Bkz. [işleyiciler](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="d50bf-157">See [Handles](handles-clause.md).</span></span>

- `eventlist`

  <span data-ttu-id="d50bf-158">Sağlanırsa gereklidir `Handles` .</span><span class="sxs-lookup"><span data-stu-id="d50bf-158">Required if `Handles` is supplied.</span></span> <span data-ttu-id="d50bf-159">Bu yordamın işleyeceği olayların listesi.</span><span class="sxs-lookup"><span data-stu-id="d50bf-159">List of events this procedure handles.</span></span>

  `eventspecifier [ , eventspecifier ... ]`

  <span data-ttu-id="d50bf-160">Her birinin `eventspecifier` aşağıdaki söz dizimi ve parçaları vardır:</span><span class="sxs-lookup"><span data-stu-id="d50bf-160">Each `eventspecifier` has the following syntax and parts:</span></span>

  `eventvariable.event`

  |<span data-ttu-id="d50bf-161">Bölüm</span><span class="sxs-lookup"><span data-stu-id="d50bf-161">Part</span></span>|<span data-ttu-id="d50bf-162">Description</span><span class="sxs-lookup"><span data-stu-id="d50bf-162">Description</span></span>|
  |---|---|
  |`eventvariable`|<span data-ttu-id="d50bf-163">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d50bf-163">Required.</span></span> <span data-ttu-id="d50bf-164">Olayı oluşturan sınıfın veya yapının veri türüyle belirtilen nesne değişkeni.</span><span class="sxs-lookup"><span data-stu-id="d50bf-164">Object variable declared with the data type of the class or structure that raises the event.</span></span>|
  |`event`|<span data-ttu-id="d50bf-165">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d50bf-165">Required.</span></span> <span data-ttu-id="d50bf-166">Bu yordamın işleyeceği olayın adı.</span><span class="sxs-lookup"><span data-stu-id="d50bf-166">Name of the event this procedure handles.</span></span>|

- `statements`

  <span data-ttu-id="d50bf-167">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d50bf-167">Optional.</span></span> <span data-ttu-id="d50bf-168">Bu yordamda yürütülecek deyim bloğu.</span><span class="sxs-lookup"><span data-stu-id="d50bf-168">Block of statements to be executed within this procedure.</span></span>

- `End Function`

  <span data-ttu-id="d50bf-169">Bu yordamın tanımını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="d50bf-169">Terminates the definition of this procedure.</span></span>

## <a name="remarks"></a><span data-ttu-id="d50bf-170">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d50bf-170">Remarks</span></span>

<span data-ttu-id="d50bf-171">Tüm yürütülebilir kodların bir yordamın içinde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d50bf-171">All executable code must be inside a procedure.</span></span> <span data-ttu-id="d50bf-172">Her yordam, sırasıyla bir sınıf, yapı veya kapsayan sınıf, yapı veya modül olarak başvurulan bir modül içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d50bf-172">Each procedure, in turn, is declared within a class, a structure, or a module that is referred to as the containing class, structure, or module.</span></span>

<span data-ttu-id="d50bf-173">Çağırma koduna bir değer döndürmek için bir `Function` yordam kullanın; Aksi takdirde, bir `Sub` yordam kullanın.</span><span class="sxs-lookup"><span data-stu-id="d50bf-173">To return a value to the calling code, use a `Function` procedure; otherwise, use a `Sub` procedure.</span></span>

## <a name="defining-a-function"></a><span data-ttu-id="d50bf-174">Işlev tanımlama</span><span class="sxs-lookup"><span data-stu-id="d50bf-174">Defining a Function</span></span>

<span data-ttu-id="d50bf-175">Bir `Function` yordamı yalnızca modül düzeyinde tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d50bf-175">You can define a `Function` procedure only at the module level.</span></span> <span data-ttu-id="d50bf-176">Bu nedenle, bir işlev için bildirim bağlamı bir sınıf, yapı, modül veya arabirim olmalıdır ve kaynak dosya, bir ad alanı, yordam veya bir blok olamaz.</span><span class="sxs-lookup"><span data-stu-id="d50bf-176">Therefore, the declaration context for a function must be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="d50bf-177">Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="d50bf-177">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="d50bf-178">`Function`yordamlar, genel erişim için varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="d50bf-178">`Function` procedures default to public access.</span></span> <span data-ttu-id="d50bf-179">Erişim değiştiricilerini kullanarak erişim düzeylerini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d50bf-179">You can adjust their access levels with the access modifiers.</span></span>

<span data-ttu-id="d50bf-180">`Function`Yordam, yordamın döndürdüğü değerin veri türünü bildirebilirler.</span><span class="sxs-lookup"><span data-stu-id="d50bf-180">A `Function` procedure can declare the data type of the value that the procedure returns.</span></span> <span data-ttu-id="d50bf-181">Herhangi bir veri türü veya bir numaralandırma, bir yapı, sınıf veya arabirim adı belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d50bf-181">You can specify any data type or the name of an enumeration, a structure, a class, or an interface.</span></span> <span data-ttu-id="d50bf-182">`returntype`Parametresini belirtmezseniz, yordam döndürür `Object` .</span><span class="sxs-lookup"><span data-stu-id="d50bf-182">If you don't specify the `returntype` parameter, the procedure returns `Object`.</span></span>

<span data-ttu-id="d50bf-183">Bu yordam `Implements` anahtar sözcüğünü kullanıyorsa, kapsayan sınıf veya yapının aynı zamanda `Implements` veya ifadesiyle hemen sonraki bir deyime sahip olması gerekir `Class` `Structure` .</span><span class="sxs-lookup"><span data-stu-id="d50bf-183">If this procedure uses the `Implements` keyword, the containing class or structure must also have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="d50bf-184">`Implements`İfadesinin içinde belirtilen her arabirimi içermesi gerekir `implementslist` .</span><span class="sxs-lookup"><span data-stu-id="d50bf-184">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="d50bf-185">Ancak, bir arabirimin `Function` (içinde) tanımladığı adın `definedname` Bu yordamın adıyla eşleşmesi gerekmez (içinde `name` ).</span><span class="sxs-lookup"><span data-stu-id="d50bf-185">However, the name by which an interface defines the `Function` (in `definedname`) doesn't need to match the name of this procedure (in `name`).</span></span>

> [!NOTE]
> <span data-ttu-id="d50bf-186">İşlev ifadelerini satır içi olarak tanımlamak için lambda ifadeleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d50bf-186">You can use lambda expressions to define function expressions inline.</span></span> <span data-ttu-id="d50bf-187">Daha fazla bilgi için bkz. [Işlev ifadesi](../operators/function-expression.md) ve [lambda ifadeleri](../../programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="d50bf-187">For more information, see [Function Expression](../operators/function-expression.md) and [Lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).</span></span>

## <a name="returning-from-a-function"></a><span data-ttu-id="d50bf-188">Bir Işlevden dönme</span><span class="sxs-lookup"><span data-stu-id="d50bf-188">Returning from a Function</span></span>

<span data-ttu-id="d50bf-189">`Function`Yordam çağıran koda döndüğünde, yürütme yordamı çağıran deyimden sonraki deyimle devam eder.</span><span class="sxs-lookup"><span data-stu-id="d50bf-189">When the `Function` procedure returns to the calling code, execution continues with the statement that follows the statement that called the procedure.</span></span>

<span data-ttu-id="d50bf-190">Bir işlevden bir değer döndürmek için, değeri işlev adına atayabilir veya bir deyime dahil edebilirsiniz `Return` .</span><span class="sxs-lookup"><span data-stu-id="d50bf-190">To return a value from a function, you can either assign the value to the function name or include it in a `Return` statement.</span></span>

<span data-ttu-id="d50bf-191">`Return`Deyimde döndürülen değeri aynı anda atar ve aşağıdaki örnekte gösterildiği gibi işlevden çıkar.</span><span class="sxs-lookup"><span data-stu-id="d50bf-191">The `Return` statement simultaneously assigns the return value and exits the function, as the following example shows.</span></span>

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

<span data-ttu-id="d50bf-192">Aşağıdaki örnek, dönüş değerini işlev adına atar `myFunction` ve ardından `Exit Function` döndürmek için ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d50bf-192">The following example assigns the return value to the function name `myFunction` and then uses the `Exit Function` statement to return.</span></span>

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

<span data-ttu-id="d50bf-193">`Exit Function`Ve `Return` deyimleri, bir yordamdan hemen çıkılmasına neden olur `Function` .</span><span class="sxs-lookup"><span data-stu-id="d50bf-193">The `Exit Function` and `Return` statements cause an immediate exit from a `Function` procedure.</span></span> <span data-ttu-id="d50bf-194">Herhangi bir sayıda `Exit Function` ve `Return` deyimi yordamda herhangi bir yerde görünebilir ve `Exit Function` ve deyimlerini karıştırabilirsiniz `Return` .</span><span class="sxs-lookup"><span data-stu-id="d50bf-194">Any number of `Exit Function` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Function` and `Return` statements.</span></span>

<span data-ttu-id="d50bf-195">`Exit Function`' A bir değer atamakla kullanırsanız `name` , yordam içinde belirtilen veri türü için varsayılan değeri döndürür `returntype` .</span><span class="sxs-lookup"><span data-stu-id="d50bf-195">If you use `Exit Function` without assigning a value to `name`, the procedure returns the default value for the data type that's specified in `returntype`.</span></span> <span data-ttu-id="d50bf-196">`returntype`Belirtilmemişse, yordamı `Nothing` için varsayılan değer olan döndürür `Object` .</span><span class="sxs-lookup"><span data-stu-id="d50bf-196">If `returntype` isn't specified, the procedure returns `Nothing`, which is the default value for `Object`.</span></span>

## <a name="calling-a-function"></a><span data-ttu-id="d50bf-197">İşlev Çağırma</span><span class="sxs-lookup"><span data-stu-id="d50bf-197">Calling a Function</span></span>

<span data-ttu-id="d50bf-198">Yordam adını ve `Function` sonra parantez içindeki bağımsız değişken listesini bir ifadede kullanarak bir yordamı çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d50bf-198">You call a `Function` procedure by using the procedure name, followed by the argument list in parentheses, in an expression.</span></span> <span data-ttu-id="d50bf-199">Parantezleri yalnızca herhangi bir bağımsız değişken belirtmezseniz atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d50bf-199">You can omit the parentheses only if you aren't supplying any arguments.</span></span> <span data-ttu-id="d50bf-200">Ancak, her zaman parantezleri eklerseniz kodunuz daha okunabilir.</span><span class="sxs-lookup"><span data-stu-id="d50bf-200">However, your code is more readable if you always include the parentheses.</span></span>

<span data-ttu-id="d50bf-201">Bir `Function` yordamı, veya gibi herhangi bir kitaplık işlevini çağırdığınız şekilde çağırabilirsiniz `Sqrt` `Cos` `ChrW` .</span><span class="sxs-lookup"><span data-stu-id="d50bf-201">You call a `Function` procedure the same way that you call any library function such as `Sqrt`, `Cos`, or `ChrW`.</span></span>

<span data-ttu-id="d50bf-202">Anahtar sözcüğünü kullanarak bir işlevi de çağırabilirsiniz `Call` .</span><span class="sxs-lookup"><span data-stu-id="d50bf-202">You can also call a function by using the `Call` keyword.</span></span> <span data-ttu-id="d50bf-203">Bu durumda, dönüş değeri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="d50bf-203">In that case, the return value is ignored.</span></span> <span data-ttu-id="d50bf-204">`Call`Çoğu durumda anahtar sözcüğünün kullanılması önerilmez.</span><span class="sxs-lookup"><span data-stu-id="d50bf-204">Use of the `Call` keyword isn't recommended in most cases.</span></span> <span data-ttu-id="d50bf-205">Daha fazla bilgi için bkz. [Call deyimleri](call-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d50bf-205">For more information, see [Call Statement](call-statement.md).</span></span>

<span data-ttu-id="d50bf-206">Visual Basic bazen, iç verimliliği artırmak için aritmetik ifadeleri yeniden düzenler.</span><span class="sxs-lookup"><span data-stu-id="d50bf-206">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="d50bf-207">Bu nedenle, `Function` işlev aynı ifadedeki değişkenlerin değerini değiştirdiğinde aritmetik ifadede bir yordam kullanmamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d50bf-207">For that reason, you shouldn't use a `Function` procedure in an arithmetic expression when the function changes the value of variables in the same expression.</span></span>

## <a name="async-functions"></a><span data-ttu-id="d50bf-208">Zaman uyumsuz Işlevler</span><span class="sxs-lookup"><span data-stu-id="d50bf-208">Async Functions</span></span>

<span data-ttu-id="d50bf-209">*Async* özelliği, açık geri çağırmaları kullanmadan veya kodunuzu birden çok işlev veya lambda ifadesine el ile bölmeden zaman uyumsuz işlevleri çağırabilmeniz için izin verir.</span><span class="sxs-lookup"><span data-stu-id="d50bf-209">The *Async* feature allows you to invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>

<span data-ttu-id="d50bf-210">Bir işlevi [zaman uyumsuz](../modifiers/async.md) değiştiriciyle işaretlerseniz, işlevindeki [await](../operators/await-operator.md) işlecini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d50bf-210">If you mark a function with the [Async](../modifiers/async.md) modifier, you can use the [Await](../operators/await-operator.md) operator in the function.</span></span> <span data-ttu-id="d50bf-211">Denetim, işlevdeki bir `Await` ifadeye ulaştığında `Async` Denetim çağırana döner ve beklenen görev tamamlanana kadar işlevdeki ilerleme durumu askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="d50bf-211">When control reaches an `Await` expression in the `Async` function, control returns to the caller, and progress in the function is suspended until the awaited task completes.</span></span> <span data-ttu-id="d50bf-212">Görev tamamlandığında, yürütme işlevinde çalışmaya çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="d50bf-212">When the task is complete, execution can resume in the function.</span></span>

> [!NOTE]
> <span data-ttu-id="d50bf-213">Bir `Async` yordam, henüz tamamlanmamış olan ilk beklemiş nesneyle karşılaştığında çağrı yapana geri döner veya `Async` yordamın sonuna, hangisi önce gerçekleşirse olur.</span><span class="sxs-lookup"><span data-stu-id="d50bf-213">An `Async` procedure returns to the caller when either it encounters the first awaited object that’s not yet complete, or it gets to the end of the `Async` procedure, whichever occurs first.</span></span>

<span data-ttu-id="d50bf-214">Bir `Async` işlev, veya dönüş türüne sahip olabilir <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.Task> .</span><span class="sxs-lookup"><span data-stu-id="d50bf-214">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="d50bf-215">`Async`Bir dönüş türüne sahip bir işlev örneği <xref:System.Threading.Tasks.Task%601> aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d50bf-215">An example of an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601> is provided below.</span></span>

<span data-ttu-id="d50bf-216">Bir `Async` Işlev [ByRef](../modifiers/byref.md) parametreleri bildiremez.</span><span class="sxs-lookup"><span data-stu-id="d50bf-216">An `Async` function cannot declare any [ByRef](../modifiers/byref.md) parameters.</span></span>

<span data-ttu-id="d50bf-217">Bir [alt ifade](sub-statement.md) , `Async` değiştiriciyle de işaretlenebilir.</span><span class="sxs-lookup"><span data-stu-id="d50bf-217">A [Sub Statement](sub-statement.md) can also be marked with the `Async` modifier.</span></span> <span data-ttu-id="d50bf-218">Bu, öncelikle bir değer döndürülmediğinde olay işleyicileri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d50bf-218">This is primarily used for event handlers, where a value cannot be returned.</span></span> <span data-ttu-id="d50bf-219">Bir yordam beklenemez `Async` `Sub` ve bir yordamın çağıranu `Async` `Sub` yordam tarafından oluşturulan özel durumları yakalayamaz `Sub` .</span><span class="sxs-lookup"><span data-stu-id="d50bf-219">An `Async` `Sub` procedure can't be awaited, and the caller of an `Async` `Sub` procedure can't catch exceptions that are thrown by the `Sub` procedure.</span></span>

<span data-ttu-id="d50bf-220">İşlevler hakkında daha fazla bilgi için `Async` bkz. [Async ve await Ile zaman uyumsuz programlama](../../programming-guide/concepts/async/index.md), [zaman uyumsuz programlarda denetim akışı](../../programming-guide/concepts/async/control-flow-in-async-programs.md)ve [zaman uyumsuz dönüş türleri](../../programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="d50bf-220">For more information about `Async` functions, see [Asynchronous Programming with Async and Await](../../programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../programming-guide/concepts/async/async-return-types.md).</span></span>

## <a name="iterator-functions"></a><span data-ttu-id="d50bf-221">Yineleyici Işlevleri</span><span class="sxs-lookup"><span data-stu-id="d50bf-221">Iterator Functions</span></span>

<span data-ttu-id="d50bf-222">*Yineleyici* işlevi, bir koleksiyon üzerinde liste veya dizi gibi özel bir yineleme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="d50bf-222">An *iterator* function performs a custom iteration over a collection, such as a list or array.</span></span> <span data-ttu-id="d50bf-223">Yineleyici işlevi, her öğeyi birer birer döndürmek için [yield](yield-statement.md) ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d50bf-223">An iterator function uses the [Yield](yield-statement.md) statement to return each element one at a time.</span></span> <span data-ttu-id="d50bf-224">Bir [yield](yield-statement.md) ifadesine ulaşıldığında, koddaki geçerli konum hatırlanır.</span><span class="sxs-lookup"><span data-stu-id="d50bf-224">When a [Yield](yield-statement.md) statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="d50bf-225">Bu konumdan, Yineleyici işlevinin bir sonraki çağrılışında yürütme yeniden başlatılır.</span><span class="sxs-lookup"><span data-stu-id="d50bf-225">Execution is restarted from that location the next time the iterator function is called.</span></span>

<span data-ttu-id="d50bf-226">Her biri Için bir kullanarak istemci kodundan bir yineleyici çağırın [... Sonraki](for-each-next-statement.md) ifade.</span><span class="sxs-lookup"><span data-stu-id="d50bf-226">You call an iterator from client code by using a [For Each…Next](for-each-next-statement.md) statement.</span></span>

<span data-ttu-id="d50bf-227">Yineleyici işlevinin dönüş türü,,, veya olabilir <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerator> <xref:System.Collections.Generic.IEnumerator%601> .</span><span class="sxs-lookup"><span data-stu-id="d50bf-227">The return type of an iterator function can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="d50bf-228">Daha fazla bilgi için bkz. [yineleyiciler](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="d50bf-228">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>

## <a name="example"></a><span data-ttu-id="d50bf-229">Örnek</span><span class="sxs-lookup"><span data-stu-id="d50bf-229">Example</span></span>

<span data-ttu-id="d50bf-230">Aşağıdaki örnek, `Function` bir yordamın gövdesini oluşturan adı, parametreleri ve kodu bildirmek için bildirimini kullanır `Function` .</span><span class="sxs-lookup"><span data-stu-id="d50bf-230">The following example uses the `Function` statement to declare the name, parameters, and code that form the body of a `Function` procedure.</span></span> <span data-ttu-id="d50bf-231">`ParamArray`Değiştirici, işlevin değişken sayıda bağımsız değişken kabul etmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d50bf-231">The `ParamArray` modifier enables the function to accept a variable number of arguments.</span></span>

[!code-vb[VbVbalrStatements#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#25)]

## <a name="example"></a><span data-ttu-id="d50bf-232">Örnek</span><span class="sxs-lookup"><span data-stu-id="d50bf-232">Example</span></span>

<span data-ttu-id="d50bf-233">Aşağıdaki örnek, önceki örnekte belirtilen işlevi çağırır.</span><span class="sxs-lookup"><span data-stu-id="d50bf-233">The following example invokes the function declared in the preceding example.</span></span>

[!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]

## <a name="example"></a><span data-ttu-id="d50bf-234">Örnek</span><span class="sxs-lookup"><span data-stu-id="d50bf-234">Example</span></span>

<span data-ttu-id="d50bf-235">Aşağıdaki örnekte, `DelayAsync` `Async` `Function` öğesinin dönüş türü olan bir <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="d50bf-235">In the following example, `DelayAsync` is an `Async` `Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="d50bf-236">`DelayAsync`, `Return` bir tamsayı döndüren bir ifadeye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d50bf-236">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="d50bf-237">Bu nedenle, işlev bildiriminin `DelayAsync` bir dönüş türüne sahip olması gerekir `Task(Of Integer)` .</span><span class="sxs-lookup"><span data-stu-id="d50bf-237">Therefore the function declaration of `DelayAsync` needs to have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="d50bf-238">Dönüş türü olduğundan `Task(Of Integer)` , `Await` ifadesinin içindeki değerlendirmesi `DoSomethingAsync` bir tamsayı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d50bf-238">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer.</span></span> <span data-ttu-id="d50bf-239">Bu bildirimde gösterilmiştir: `Dim result As Integer = Await delayTask` .</span><span class="sxs-lookup"><span data-stu-id="d50bf-239">This is demonstrated in this statement: `Dim result As Integer = Await delayTask`.</span></span>

<span data-ttu-id="d50bf-240">`startButton_Click`Yordam bir `Async Sub` yordam örneğidir.</span><span class="sxs-lookup"><span data-stu-id="d50bf-240">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="d50bf-241">`DoSomethingAsync`Bir işlev olduğundan `Async` , `DoSomethingAsync` Aşağıdaki ifadede gösterildiği gibi çağrının görevi beklenmelidir: `Await DoSomethingAsync()` .</span><span class="sxs-lookup"><span data-stu-id="d50bf-241">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement demonstrates: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="d50bf-242">`startButton_Click` `Sub` Bir ifadesi içerdiğinden yordamın değiştirici ile tanımlanması gerekir `Async` `Await` .</span><span class="sxs-lookup"><span data-stu-id="d50bf-242">The `startButton_Click` `Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a><span data-ttu-id="d50bf-243">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d50bf-243">See also</span></span>

- [<span data-ttu-id="d50bf-244">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="d50bf-244">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="d50bf-245">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="d50bf-245">Function Procedures</span></span>](../../programming-guide/language-features/procedures/function-procedures.md)
- [<span data-ttu-id="d50bf-246">Parametre Listesi</span><span class="sxs-lookup"><span data-stu-id="d50bf-246">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="d50bf-247">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="d50bf-247">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="d50bf-248">Call Deyimi</span><span class="sxs-lookup"><span data-stu-id="d50bf-248">Call Statement</span></span>](call-statement.md)
- [<span data-ttu-id="d50bf-249">Durumunu</span><span class="sxs-lookup"><span data-stu-id="d50bf-249">Of</span></span>](of-clause.md)
- [<span data-ttu-id="d50bf-250">Parametre Dizileri</span><span class="sxs-lookup"><span data-stu-id="d50bf-250">Parameter Arrays</span></span>](../../programming-guide/language-features/procedures/parameter-arrays.md)
- [<span data-ttu-id="d50bf-251">Nasıl yapılır: Genel Bir Sınıf Kullanma</span><span class="sxs-lookup"><span data-stu-id="d50bf-251">How to: Use a Generic Class</span></span>](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="d50bf-252">Yordam Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="d50bf-252">Troubleshooting Procedures</span></span>](../../programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [<span data-ttu-id="d50bf-253">Lambda Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="d50bf-253">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="d50bf-254">İşlev Ifadesi</span><span class="sxs-lookup"><span data-stu-id="d50bf-254">Function Expression</span></span>](../operators/function-expression.md)
