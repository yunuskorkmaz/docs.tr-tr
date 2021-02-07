---
description: 'Daha fazla bilgi edinin: alt Ifade (Visual Basic)'
title: Sub Deyimi
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
ms.openlocfilehash: 9be40c8284c677a151e4b1665f0b49e5f852bf00
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740996"
---
# <a name="sub-statement-visual-basic"></a><span data-ttu-id="9dead-103">Sub Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9dead-103">Sub Statement (Visual Basic)</span></span>

<span data-ttu-id="9dead-104">Bir yordamı tanımlayan adı, parametreleri ve kodu bildirir `Sub` .</span><span class="sxs-lookup"><span data-stu-id="9dead-104">Declares the name, parameters, and code that define a `Sub` procedure.</span></span>

## <a name="syntax"></a><span data-ttu-id="9dead-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="9dead-105">Syntax</span></span>

```vb
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Sub ]
    [ statements ]
End Sub
```

## <a name="parts"></a><span data-ttu-id="9dead-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="9dead-106">Parts</span></span>

- `attributelist`

  <span data-ttu-id="9dead-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="9dead-107">Optional.</span></span> <span data-ttu-id="9dead-108">Bkz. [öznitelik listesi](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="9dead-108">See [Attribute List](attribute-list.md).</span></span>

- `Partial`

  <span data-ttu-id="9dead-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="9dead-109">Optional.</span></span> <span data-ttu-id="9dead-110">Kısmi bir yöntemin tanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9dead-110">Indicates definition of a partial method.</span></span> <span data-ttu-id="9dead-111">Bkz. [kısmi Yöntemler](../../programming-guide/language-features/procedures/partial-methods.md).</span><span class="sxs-lookup"><span data-stu-id="9dead-111">See [Partial Methods](../../programming-guide/language-features/procedures/partial-methods.md).</span></span>

- `accessmodifier`

  <span data-ttu-id="9dead-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="9dead-112">Optional.</span></span> <span data-ttu-id="9dead-113">Aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="9dead-113">Can be one of the following:</span></span>

  - [<span data-ttu-id="9dead-114">Genel</span><span class="sxs-lookup"><span data-stu-id="9dead-114">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="9dead-115">Korunamadı</span><span class="sxs-lookup"><span data-stu-id="9dead-115">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="9dead-116">Arkadaş</span><span class="sxs-lookup"><span data-stu-id="9dead-116">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="9dead-117">Özel</span><span class="sxs-lookup"><span data-stu-id="9dead-117">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="9dead-118">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="9dead-118">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="9dead-119">Özel korumalı</span><span class="sxs-lookup"><span data-stu-id="9dead-119">Private Protected</span></span>](../modifiers/private-protected.md)

  <span data-ttu-id="9dead-120">[Visual Basic erişim düzeylerine](../../programming-guide/language-features/declared-elements/access-levels.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="9dead-120">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `proceduremodifiers`

  <span data-ttu-id="9dead-121">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="9dead-121">Optional.</span></span> <span data-ttu-id="9dead-122">Aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="9dead-122">Can be one of the following:</span></span>

  - [<span data-ttu-id="9dead-123">Aşırı Yüklemeler</span><span class="sxs-lookup"><span data-stu-id="9dead-123">Overloads</span></span>](../modifiers/overloads.md)

  - [<span data-ttu-id="9dead-124">Geçersiz Kılmalar</span><span class="sxs-lookup"><span data-stu-id="9dead-124">Overrides</span></span>](../modifiers/overrides.md)

  - [<span data-ttu-id="9dead-125">Overridable</span><span class="sxs-lookup"><span data-stu-id="9dead-125">Overridable</span></span>](../modifiers/overridable.md)

  - [<span data-ttu-id="9dead-126">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="9dead-126">NotOverridable</span></span>](../modifiers/notoverridable.md)

  - [<span data-ttu-id="9dead-127">MustOverride</span><span class="sxs-lookup"><span data-stu-id="9dead-127">MustOverride</span></span>](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  <span data-ttu-id="9dead-128">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="9dead-128">Optional.</span></span> <span data-ttu-id="9dead-129">Bkz. [paylaşılan](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="9dead-129">See [Shared](../modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="9dead-130">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="9dead-130">Optional.</span></span> <span data-ttu-id="9dead-131">Bkz. [gölgeler](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="9dead-131">See [Shadows](../modifiers/shadows.md).</span></span>

- `Async`

  <span data-ttu-id="9dead-132">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="9dead-132">Optional.</span></span> <span data-ttu-id="9dead-133">Bkz. [zaman uyumsuz](../modifiers/async.md).</span><span class="sxs-lookup"><span data-stu-id="9dead-133">See [Async](../modifiers/async.md).</span></span>

- `name`

  <span data-ttu-id="9dead-134">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9dead-134">Required.</span></span> <span data-ttu-id="9dead-135">Yordamın adı.</span><span class="sxs-lookup"><span data-stu-id="9dead-135">Name of the procedure.</span></span> <span data-ttu-id="9dead-136">Bkz. [tanımlanmış öğe adları](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="9dead-136">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span> <span data-ttu-id="9dead-137">Bir sınıf için bir Oluşturucu yordamı oluşturmak için, bir `Sub` yordamın adını `New` anahtar sözcüğe ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9dead-137">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="9dead-138">Daha fazla bilgi için bkz. [nesne ömrü: nesneleri oluşturma ve yok etme](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="9dead-138">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>

- `typeparamlist`

  <span data-ttu-id="9dead-139">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="9dead-139">Optional.</span></span> <span data-ttu-id="9dead-140">Genel bir yordamın tür parametrelerinin listesi.</span><span class="sxs-lookup"><span data-stu-id="9dead-140">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="9dead-141">Bkz. [tür listesi](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="9dead-141">See [Type List](type-list.md).</span></span>

- `parameterlist`

  <span data-ttu-id="9dead-142">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="9dead-142">Optional.</span></span> <span data-ttu-id="9dead-143">Bu yordamın parametrelerini temsil eden yerel değişken adlarının listesi.</span><span class="sxs-lookup"><span data-stu-id="9dead-143">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="9dead-144">Bkz. [parametre listesi](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="9dead-144">See [Parameter List](parameter-list.md).</span></span>

- `Implements`

  <span data-ttu-id="9dead-145">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="9dead-145">Optional.</span></span> <span data-ttu-id="9dead-146">Bu yordamın `Sub` , her biri bu yordamın kapsayan sınıf veya yapı tarafından uygulanan bir arabirimde tanımlanan bir veya daha fazla yordam uyguladığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9dead-146">Indicates that this procedure implements one or more `Sub` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="9dead-147">Bkz. [Implements açıklaması](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9dead-147">See [Implements Statement](implements-statement.md).</span></span>

- `implementslist`

  <span data-ttu-id="9dead-148">Sağlanırsa gereklidir `Implements` .</span><span class="sxs-lookup"><span data-stu-id="9dead-148">Required if `Implements` is supplied.</span></span> <span data-ttu-id="9dead-149">`Sub`Uygulanan yordamların listesi.</span><span class="sxs-lookup"><span data-stu-id="9dead-149">List of `Sub` procedures being implemented.</span></span>

  `implementedprocedure [ , implementedprocedure ... ]`

  <span data-ttu-id="9dead-150">Her birinin `implementedprocedure` aşağıdaki söz dizimi ve parçaları vardır:</span><span class="sxs-lookup"><span data-stu-id="9dead-150">Each `implementedprocedure` has the following syntax and parts:</span></span>

  `interface.definedname`

  |<span data-ttu-id="9dead-151">Bölüm</span><span class="sxs-lookup"><span data-stu-id="9dead-151">Part</span></span>|<span data-ttu-id="9dead-152">Description</span><span class="sxs-lookup"><span data-stu-id="9dead-152">Description</span></span>|
  |---|---|
  |`interface`|<span data-ttu-id="9dead-153">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9dead-153">Required.</span></span> <span data-ttu-id="9dead-154">Bu yordamın kapsayan sınıf veya yapı tarafından uygulanan bir arabirimin adı.</span><span class="sxs-lookup"><span data-stu-id="9dead-154">Name of an interface implemented by this procedure's containing class or structure.</span></span>|
  |`definedname`|<span data-ttu-id="9dead-155">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9dead-155">Required.</span></span> <span data-ttu-id="9dead-156">Yordamın tanımlandığı ad `interface` .</span><span class="sxs-lookup"><span data-stu-id="9dead-156">Name by which the procedure is defined in `interface`.</span></span>|

- `Handles`

  <span data-ttu-id="9dead-157">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="9dead-157">Optional.</span></span> <span data-ttu-id="9dead-158">Bu yordamın bir veya daha fazla belirli olayı işleyebileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9dead-158">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="9dead-159">Bkz. [işleyiciler](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="9dead-159">See [Handles](handles-clause.md).</span></span>

- `eventlist`

  <span data-ttu-id="9dead-160">Sağlanırsa gereklidir `Handles` .</span><span class="sxs-lookup"><span data-stu-id="9dead-160">Required if `Handles` is supplied.</span></span> <span data-ttu-id="9dead-161">Bu yordamın işleyeceği olayların listesi.</span><span class="sxs-lookup"><span data-stu-id="9dead-161">List of events this procedure handles.</span></span>

  `eventspecifier [ , eventspecifier ... ]`

  <span data-ttu-id="9dead-162">Her birinin `eventspecifier` aşağıdaki söz dizimi ve parçaları vardır:</span><span class="sxs-lookup"><span data-stu-id="9dead-162">Each `eventspecifier` has the following syntax and parts:</span></span>

  `eventvariable.event`

  |<span data-ttu-id="9dead-163">Bölüm</span><span class="sxs-lookup"><span data-stu-id="9dead-163">Part</span></span>|<span data-ttu-id="9dead-164">Description</span><span class="sxs-lookup"><span data-stu-id="9dead-164">Description</span></span>|
  |---|---|
  |`eventvariable`|<span data-ttu-id="9dead-165">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9dead-165">Required.</span></span> <span data-ttu-id="9dead-166">Olayı oluşturan sınıfın veya yapının veri türüyle belirtilen nesne değişkeni.</span><span class="sxs-lookup"><span data-stu-id="9dead-166">Object variable declared with the data type of the class or structure that raises the event.</span></span>|
  |`event`|<span data-ttu-id="9dead-167">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9dead-167">Required.</span></span> <span data-ttu-id="9dead-168">Bu yordamın işleyeceği olayın adı.</span><span class="sxs-lookup"><span data-stu-id="9dead-168">Name of the event this procedure handles.</span></span>|

- `statements`

  <span data-ttu-id="9dead-169">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="9dead-169">Optional.</span></span> <span data-ttu-id="9dead-170">Bu yordam içinde çalıştırılacak deyimler bloğu.</span><span class="sxs-lookup"><span data-stu-id="9dead-170">Block of statements to run within this procedure.</span></span>

- `End Sub`

  <span data-ttu-id="9dead-171">Bu yordamın tanımını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="9dead-171">Terminates the definition of this procedure.</span></span>

## <a name="remarks"></a><span data-ttu-id="9dead-172">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9dead-172">Remarks</span></span>

<span data-ttu-id="9dead-173">Tüm yürütülebilir kodların bir yordamın içinde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9dead-173">All executable code must be inside a procedure.</span></span> <span data-ttu-id="9dead-174">`Sub`Çağırma koduna bir değer döndürmek istemediğinizde bir yordam kullanın.</span><span class="sxs-lookup"><span data-stu-id="9dead-174">Use a `Sub` procedure when you don't want to return a value to the calling code.</span></span> <span data-ttu-id="9dead-175">Bir `Function` değer döndürmek istediğinizde bir yordam kullanın.</span><span class="sxs-lookup"><span data-stu-id="9dead-175">Use a `Function` procedure when you want to return a value.</span></span>

## <a name="defining-a-sub-procedure"></a><span data-ttu-id="9dead-176">Bir alt yordam tanımlama</span><span class="sxs-lookup"><span data-stu-id="9dead-176">Defining a Sub Procedure</span></span>

<span data-ttu-id="9dead-177">Bir `Sub` yordamı yalnızca modül düzeyinde tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9dead-177">You can define a `Sub` procedure only at the module level.</span></span> <span data-ttu-id="9dead-178">Bir alt yordamın bildirim bağlamı, bu nedenle bir sınıf, yapı, modül veya arabirim olmalıdır ve kaynak dosya, bir ad alanı, yordam veya bir blok olamaz.</span><span class="sxs-lookup"><span data-stu-id="9dead-178">The declaration context for a sub procedure must, therefore, be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="9dead-179">Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="9dead-179">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="9dead-180">`Sub` yordamlar, genel erişim için varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="9dead-180">`Sub` procedures default to public access.</span></span> <span data-ttu-id="9dead-181">Erişim değiştiricilerini kullanarak erişim düzeylerini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9dead-181">You can adjust their access levels by using the access modifiers.</span></span>

<span data-ttu-id="9dead-182">Yordam `Implements` anahtar sözcüğünü kullanıyorsa, kapsayan sınıf veya yapının, `Implements` veya ifadesiyle hemen sonraki bir deyime sahip olması gerekir `Class` `Structure` .</span><span class="sxs-lookup"><span data-stu-id="9dead-182">If the procedure uses the `Implements` keyword, the containing class or structure must have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="9dead-183">`Implements`İfadesinin içinde belirtilen her arabirimi içermesi gerekir `implementslist` .</span><span class="sxs-lookup"><span data-stu-id="9dead-183">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="9dead-184">Ancak, bir arabirimin `Sub` (içinde) tanımladığı adın `definedname` Bu yordamın adıyla eşleşmesi gerekmez (içinde `name` ).</span><span class="sxs-lookup"><span data-stu-id="9dead-184">However, the name by which an interface defines the `Sub` (in `definedname`) doesn't have to match the name of this procedure (in `name`).</span></span>

## <a name="returning-from-a-sub-procedure"></a><span data-ttu-id="9dead-185">Bir alt yordamdan dönme</span><span class="sxs-lookup"><span data-stu-id="9dead-185">Returning from a Sub Procedure</span></span>

<span data-ttu-id="9dead-186">Bir `Sub` yordam çağıran koda döndüğünde, yürütme onu çağıran deyimden sonra ifadesiyle devam eder.</span><span class="sxs-lookup"><span data-stu-id="9dead-186">When a `Sub` procedure returns to the calling code, execution continues with the statement after the statement that called it.</span></span>

<span data-ttu-id="9dead-187">Aşağıdaki örnek bir yordamdan bir dönüş gösterir `Sub` .</span><span class="sxs-lookup"><span data-stu-id="9dead-187">The following example shows a return from a `Sub` procedure.</span></span>

```vb
Sub mySub(ByVal q As String)
    Return
End Sub
```

<span data-ttu-id="9dead-188">`Exit Sub`Ve `Return` deyimleri, bir yordamdan hemen çıkılmasına neden olur `Sub` .</span><span class="sxs-lookup"><span data-stu-id="9dead-188">The `Exit Sub` and `Return` statements cause an immediate exit from a `Sub` procedure.</span></span> <span data-ttu-id="9dead-189">Herhangi bir sayıda `Exit Sub` ve `Return` deyimi yordamda herhangi bir yerde görünebilir ve `Exit Sub` ve deyimlerini karıştırabilirsiniz `Return` .</span><span class="sxs-lookup"><span data-stu-id="9dead-189">Any number of `Exit Sub` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Sub` and `Return` statements.</span></span>

## <a name="calling-a-sub-procedure"></a><span data-ttu-id="9dead-190">Bir alt yordamı çağırma</span><span class="sxs-lookup"><span data-stu-id="9dead-190">Calling a Sub Procedure</span></span>

<span data-ttu-id="9dead-191">`Sub`Bir deyimindeki yordam adını kullanarak bir yordamı çağırır ve ardından bu adı parantez içindeki bağımsız değişken listesiyle takip edersiniz.</span><span class="sxs-lookup"><span data-stu-id="9dead-191">You call a `Sub` procedure by using the procedure name in a statement and then following that name with its argument list in parentheses.</span></span> <span data-ttu-id="9dead-192">Parantezleri yalnızca herhangi bir bağımsız değişken belirtmezseniz atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9dead-192">You can omit the parentheses only if you don't supply any arguments.</span></span> <span data-ttu-id="9dead-193">Ancak, her zaman parantezleri eklerseniz kodunuz daha okunabilir.</span><span class="sxs-lookup"><span data-stu-id="9dead-193">However, your code is more readable if you always include the parentheses.</span></span>

<span data-ttu-id="9dead-194">Bir `Sub` yordam ve `Function` yordam parametrelere sahip olabilir ve bir dizi deyim gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="9dead-194">A `Sub` procedure and a `Function` procedure  can have parameters and perform a series of statements.</span></span> <span data-ttu-id="9dead-195">Ancak, bir `Function` yordam bir değer döndürür ve bir `Sub` yordam değildir.</span><span class="sxs-lookup"><span data-stu-id="9dead-195">However, a `Function` procedure returns a value, and a `Sub` procedure doesn't.</span></span> <span data-ttu-id="9dead-196">Bu nedenle, bir ifadede bir `Sub` yordam kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="9dead-196">Therefore, you can't use a `Sub` procedure in an expression.</span></span>

<span data-ttu-id="9dead-197">`Call`Bir yordamı çağırdığınızda anahtar sözcüğünü kullanabilirsiniz `Sub` , ancak bu anahtar sözcük çoğu kullanımlar için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="9dead-197">You can use the `Call` keyword when you call a `Sub` procedure, but that keyword isn't recommended for most uses.</span></span> <span data-ttu-id="9dead-198">Daha fazla bilgi için bkz. [Call deyimleri](call-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9dead-198">For more information, see [Call Statement](call-statement.md).</span></span>

<span data-ttu-id="9dead-199">Visual Basic bazen, iç verimliliği artırmak için aritmetik ifadeleri yeniden düzenler.</span><span class="sxs-lookup"><span data-stu-id="9dead-199">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="9dead-200">Bu nedenle, bağımsız değişken listeniz diğer yordamları çağıran ifadeler içeriyorsa, bu ifadelerin belirli bir sırada çağrılacağını varsaymamalıdır.</span><span class="sxs-lookup"><span data-stu-id="9dead-200">For that reason, if your argument list includes expressions that call other procedures, you shouldn't assume that those expressions will be called in a particular order.</span></span>

## <a name="async-sub-procedures"></a><span data-ttu-id="9dead-201">Zaman uyumsuz alt yordamlar</span><span class="sxs-lookup"><span data-stu-id="9dead-201">Async Sub Procedures</span></span>

<span data-ttu-id="9dead-202">Async özelliğini kullanarak, zaman uyumsuz işlevleri açık geri çağırmaları kullanmadan çağırabilir veya kodunuzu birden çok işlev veya lambda ifadesine el ile böedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9dead-202">By using the Async feature, you can invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>

<span data-ttu-id="9dead-203">Bir yordamı [zaman uyumsuz](../modifiers/async.md) değiştiriciyle işaretlerseniz, yordamda [await](../operators/await-operator.md) işlecini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9dead-203">If you mark a procedure with the [Async](../modifiers/async.md) modifier, you can use the [Await](../operators/await-operator.md) operator in the procedure.</span></span> <span data-ttu-id="9dead-204">Denetim, yordamda bir `Await` ifadeye ulaştığında `Async` Denetim çağırana döner ve beklenen görev tamamlanana kadar yordamdaki ilerleme durumu askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="9dead-204">When control reaches an `Await` expression in the `Async` procedure, control returns to the caller, and progress in the procedure is suspended until the awaited task completes.</span></span> <span data-ttu-id="9dead-205">Görev tamamlandığında, yürütme yordamda çalışmaya çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="9dead-205">When the task is complete, execution can resume in the procedure.</span></span>

> [!NOTE]
> <span data-ttu-id="9dead-206">Bir `Async` yordam, henüz tamamlanmamış olan ilk bekleme nesnesine rastlandı veya `Async` yordamın sonuna ulaşıldığında, hangisi önce gerçekleşirse çağıran öğesine geri döner.</span><span class="sxs-lookup"><span data-stu-id="9dead-206">An `Async` procedure returns to the caller when either the first awaited object that’s not yet complete is encountered or the end of the `Async` procedure is reached, whichever occurs first.</span></span>

<span data-ttu-id="9dead-207">Değiştirici ile bir [Işlev ifadesini](function-statement.md) de işaretleyebilirsiniz `Async` .</span><span class="sxs-lookup"><span data-stu-id="9dead-207">You can also mark a [Function Statement](function-statement.md) with the `Async` modifier.</span></span> <span data-ttu-id="9dead-208">Bir `Async` işlev, veya dönüş türüne sahip olabilir <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.Task> .</span><span class="sxs-lookup"><span data-stu-id="9dead-208">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="9dead-209">Bu konunun ilerleyen kısımlarında yer alan bir örnek `Async` , dönüş türü olan bir işlevi gösterir <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="9dead-209">An example later in this topic shows an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span>

<span data-ttu-id="9dead-210">`Async``Sub`yordamlar öncelikle bir değer döndürülmediğinde olay işleyicileri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9dead-210">`Async` `Sub` procedures are primarily used for event handlers, where a value can't be returned.</span></span> <span data-ttu-id="9dead-211">Bir yordam beklenemez `Async` `Sub` ve bir yordamın çağıranı `Async` `Sub` yordamın aldığı özel durumları yakalayamaz `Sub` .</span><span class="sxs-lookup"><span data-stu-id="9dead-211">An `Async` `Sub` procedure can't be awaited, and the caller of an `Async` `Sub` procedure can't catch exceptions that the `Sub` procedure throws.</span></span>

<span data-ttu-id="9dead-212">Bir `Async` yordam [ByRef](../modifiers/byref.md) parametreleri bildiremez.</span><span class="sxs-lookup"><span data-stu-id="9dead-212">An `Async` procedure can't declare any [ByRef](../modifiers/byref.md) parameters.</span></span>

<span data-ttu-id="9dead-213">Yordamlar hakkında daha fazla bilgi için `Async` bkz. [Async ve await Ile zaman uyumsuz programlama](../../programming-guide/concepts/async/index.md), [zaman uyumsuz programlarda denetim akışı](../../programming-guide/concepts/async/control-flow-in-async-programs.md)ve [zaman uyumsuz dönüş türleri](../../programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="9dead-213">For more information about `Async` procedures, see [Asynchronous Programming with Async and Await](../../programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../programming-guide/concepts/async/async-return-types.md).</span></span>

## <a name="example"></a><span data-ttu-id="9dead-214">Örnek</span><span class="sxs-lookup"><span data-stu-id="9dead-214">Example</span></span>

<span data-ttu-id="9dead-215">Aşağıdaki örnek, `Sub` bir yordamın gövdesini oluşturan adı, parametreleri ve kodu tanımlamak için ifadesini kullanır `Sub` .</span><span class="sxs-lookup"><span data-stu-id="9dead-215">The following example uses the `Sub` statement to define the name, parameters, and code that form the body of a `Sub` procedure.</span></span>

[!code-vb[VbVbalrStatements#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#58)]

## <a name="example"></a><span data-ttu-id="9dead-216">Örnek</span><span class="sxs-lookup"><span data-stu-id="9dead-216">Example</span></span>

<span data-ttu-id="9dead-217">Aşağıdaki örnekte, `DelayAsync` `Async` `Function` öğesinin dönüş türü olan bir <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="9dead-217">In the following example, `DelayAsync` is an `Async` `Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="9dead-218">`DelayAsync` , `Return` bir tamsayı döndüren bir ifadeye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="9dead-218">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="9dead-219">Bu nedenle, öğesinin işlev bildirimi `DelayAsync` bir dönüş türüne sahip olmalıdır `Task(Of Integer)` .</span><span class="sxs-lookup"><span data-stu-id="9dead-219">Therefore, the function declaration of `DelayAsync` must have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="9dead-220">Dönüş türü olduğu için `Task(Of Integer)` , `Await` içindeki ifadesinin değerlendirmesi `DoSomethingAsync` bir tamsayı oluşturur, çünkü aşağıdaki deyim şunu gösterir: `Dim result As Integer = Await delayTask` .</span><span class="sxs-lookup"><span data-stu-id="9dead-220">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer, as the following statement shows: `Dim result As Integer = Await delayTask`.</span></span>

<span data-ttu-id="9dead-221">`startButton_Click`Yordam bir `Async Sub` yordam örneğidir.</span><span class="sxs-lookup"><span data-stu-id="9dead-221">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="9dead-222">`DoSomethingAsync`Bir işlev olduğundan `Async` , `DoSomethingAsync` Aşağıdaki ifadede gösterildiği gibi çağrının görevi beklenmelidir: `Await DoSomethingAsync()` .</span><span class="sxs-lookup"><span data-stu-id="9dead-222">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement shows: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="9dead-223">`startButton_Click` `Sub` Bir ifadesi içerdiğinden yordamın değiştirici ile tanımlanması gerekir `Async` `Await` .</span><span class="sxs-lookup"><span data-stu-id="9dead-223">The `startButton_Click` `Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a><span data-ttu-id="9dead-224">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9dead-224">See also</span></span>

- [<span data-ttu-id="9dead-225">Implements Deyimi</span><span class="sxs-lookup"><span data-stu-id="9dead-225">Implements Statement</span></span>](implements-statement.md)
- [<span data-ttu-id="9dead-226">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="9dead-226">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="9dead-227">Parametre Listesi</span><span class="sxs-lookup"><span data-stu-id="9dead-227">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="9dead-228">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="9dead-228">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="9dead-229">Call Deyimi</span><span class="sxs-lookup"><span data-stu-id="9dead-229">Call Statement</span></span>](call-statement.md)
- [<span data-ttu-id="9dead-230">Durumunu</span><span class="sxs-lookup"><span data-stu-id="9dead-230">Of</span></span>](of-clause.md)
- [<span data-ttu-id="9dead-231">Parametre Dizileri</span><span class="sxs-lookup"><span data-stu-id="9dead-231">Parameter Arrays</span></span>](../../programming-guide/language-features/procedures/parameter-arrays.md)
- [<span data-ttu-id="9dead-232">Nasıl yapılır: Genel Bir Sınıf Kullanma</span><span class="sxs-lookup"><span data-stu-id="9dead-232">How to: Use a Generic Class</span></span>](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="9dead-233">Yordam Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="9dead-233">Troubleshooting Procedures</span></span>](../../programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [<span data-ttu-id="9dead-234">Kısmi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9dead-234">Partial Methods</span></span>](../../programming-guide/language-features/procedures/partial-methods.md)
