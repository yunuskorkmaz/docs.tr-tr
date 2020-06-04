---
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
ms.openlocfilehash: e50b79c31c92ac116d6c82bcececba3340894d74
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404180"
---
# <a name="sub-statement-visual-basic"></a><span data-ttu-id="4c9f5-102">Sub Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c9f5-102">Sub Statement (Visual Basic)</span></span>

<span data-ttu-id="4c9f5-103">Bir yordamı tanımlayan adı, parametreleri ve kodu bildirir `Sub` .</span><span class="sxs-lookup"><span data-stu-id="4c9f5-103">Declares the name, parameters, and code that define a `Sub` procedure.</span></span>

## <a name="syntax"></a><span data-ttu-id="4c9f5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4c9f5-104">Syntax</span></span>

```vb
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Sub ]
    [ statements ]
End Sub
```

## <a name="parts"></a><span data-ttu-id="4c9f5-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="4c9f5-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="4c9f5-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-106">Optional.</span></span> <span data-ttu-id="4c9f5-107">Bkz. [öznitelik listesi](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="4c9f5-107">See [Attribute List](attribute-list.md).</span></span>

- `Partial`

  <span data-ttu-id="4c9f5-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-108">Optional.</span></span> <span data-ttu-id="4c9f5-109">Kısmi bir yöntemin tanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-109">Indicates definition of a partial method.</span></span> <span data-ttu-id="4c9f5-110">Bkz. [kısmi Yöntemler](../../programming-guide/language-features/procedures/partial-methods.md).</span><span class="sxs-lookup"><span data-stu-id="4c9f5-110">See [Partial Methods](../../programming-guide/language-features/procedures/partial-methods.md).</span></span>

- `accessmodifier`

  <span data-ttu-id="4c9f5-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-111">Optional.</span></span> <span data-ttu-id="4c9f5-112">Aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="4c9f5-112">Can be one of the following:</span></span>

  - [<span data-ttu-id="4c9f5-113">Geneldir</span><span class="sxs-lookup"><span data-stu-id="4c9f5-113">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="4c9f5-114">Korunamadı</span><span class="sxs-lookup"><span data-stu-id="4c9f5-114">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="4c9f5-115">Dost</span><span class="sxs-lookup"><span data-stu-id="4c9f5-115">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="4c9f5-116">Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="4c9f5-116">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="4c9f5-117">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="4c9f5-117">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="4c9f5-118">Özel korumalı</span><span class="sxs-lookup"><span data-stu-id="4c9f5-118">Private Protected</span></span>](../modifiers/private-protected.md)

  <span data-ttu-id="4c9f5-119">[Visual Basic erişim düzeylerine](../../programming-guide/language-features/declared-elements/access-levels.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-119">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `proceduremodifiers`

  <span data-ttu-id="4c9f5-120">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-120">Optional.</span></span> <span data-ttu-id="4c9f5-121">Aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="4c9f5-121">Can be one of the following:</span></span>

  - [<span data-ttu-id="4c9f5-122">Aşırı Yüklemeler</span><span class="sxs-lookup"><span data-stu-id="4c9f5-122">Overloads</span></span>](../modifiers/overloads.md)

  - [<span data-ttu-id="4c9f5-123">Geçersiz Kılmalar</span><span class="sxs-lookup"><span data-stu-id="4c9f5-123">Overrides</span></span>](../modifiers/overrides.md)

  - [<span data-ttu-id="4c9f5-124">Overridable</span><span class="sxs-lookup"><span data-stu-id="4c9f5-124">Overridable</span></span>](../modifiers/overridable.md)

  - [<span data-ttu-id="4c9f5-125">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="4c9f5-125">NotOverridable</span></span>](../modifiers/notoverridable.md)

  - [<span data-ttu-id="4c9f5-126">MustOverride</span><span class="sxs-lookup"><span data-stu-id="4c9f5-126">MustOverride</span></span>](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  <span data-ttu-id="4c9f5-127">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-127">Optional.</span></span> <span data-ttu-id="4c9f5-128">Bkz. [paylaşılan](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="4c9f5-128">See [Shared](../modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="4c9f5-129">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-129">Optional.</span></span> <span data-ttu-id="4c9f5-130">Bkz. [gölgeler](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="4c9f5-130">See [Shadows](../modifiers/shadows.md).</span></span>

- `Async`

  <span data-ttu-id="4c9f5-131">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-131">Optional.</span></span> <span data-ttu-id="4c9f5-132">Bkz. [zaman uyumsuz](../modifiers/async.md).</span><span class="sxs-lookup"><span data-stu-id="4c9f5-132">See [Async](../modifiers/async.md).</span></span>

- `name`

  <span data-ttu-id="4c9f5-133">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-133">Required.</span></span> <span data-ttu-id="4c9f5-134">Yordamın adı.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-134">Name of the procedure.</span></span> <span data-ttu-id="4c9f5-135">Bkz. [tanımlanmış öğe adları](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="4c9f5-135">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span> <span data-ttu-id="4c9f5-136">Bir sınıf için bir Oluşturucu yordamı oluşturmak için, bir `Sub` yordamın adını `New` anahtar sözcüğe ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-136">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="4c9f5-137">Daha fazla bilgi için bkz. [nesne ömrü: nesneleri oluşturma ve yok etme](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="4c9f5-137">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>

- `typeparamlist`

  <span data-ttu-id="4c9f5-138">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-138">Optional.</span></span> <span data-ttu-id="4c9f5-139">Genel bir yordamın tür parametrelerinin listesi.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-139">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="4c9f5-140">Bkz. [tür listesi](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="4c9f5-140">See [Type List](type-list.md).</span></span>

- `parameterlist`

  <span data-ttu-id="4c9f5-141">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-141">Optional.</span></span> <span data-ttu-id="4c9f5-142">Bu yordamın parametrelerini temsil eden yerel değişken adlarının listesi.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-142">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="4c9f5-143">Bkz. [parametre listesi](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="4c9f5-143">See [Parameter List](parameter-list.md).</span></span>

- `Implements`

  <span data-ttu-id="4c9f5-144">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-144">Optional.</span></span> <span data-ttu-id="4c9f5-145">Bu yordamın `Sub` , her biri bu yordamın kapsayan sınıf veya yapı tarafından uygulanan bir arabirimde tanımlanan bir veya daha fazla yordam uyguladığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-145">Indicates that this procedure implements one or more `Sub` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="4c9f5-146">Bkz. [Implements açıklaması](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4c9f5-146">See [Implements Statement](implements-statement.md).</span></span>

- `implementslist`

  <span data-ttu-id="4c9f5-147">Sağlanırsa gereklidir `Implements` .</span><span class="sxs-lookup"><span data-stu-id="4c9f5-147">Required if `Implements` is supplied.</span></span> <span data-ttu-id="4c9f5-148">`Sub`Uygulanan yordamların listesi.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-148">List of `Sub` procedures being implemented.</span></span>

  `implementedprocedure [ , implementedprocedure ... ]`

  <span data-ttu-id="4c9f5-149">Her birinin `implementedprocedure` aşağıdaki söz dizimi ve parçaları vardır:</span><span class="sxs-lookup"><span data-stu-id="4c9f5-149">Each `implementedprocedure` has the following syntax and parts:</span></span>

  `interface.definedname`

  |<span data-ttu-id="4c9f5-150">Bölüm</span><span class="sxs-lookup"><span data-stu-id="4c9f5-150">Part</span></span>|<span data-ttu-id="4c9f5-151">Description</span><span class="sxs-lookup"><span data-stu-id="4c9f5-151">Description</span></span>|
  |---|---|
  |`interface`|<span data-ttu-id="4c9f5-152">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-152">Required.</span></span> <span data-ttu-id="4c9f5-153">Bu yordamın kapsayan sınıf veya yapı tarafından uygulanan bir arabirimin adı.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-153">Name of an interface implemented by this procedure's containing class or structure.</span></span>|
  |`definedname`|<span data-ttu-id="4c9f5-154">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-154">Required.</span></span> <span data-ttu-id="4c9f5-155">Yordamın tanımlandığı ad `interface` .</span><span class="sxs-lookup"><span data-stu-id="4c9f5-155">Name by which the procedure is defined in `interface`.</span></span>|

- `Handles`

  <span data-ttu-id="4c9f5-156">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-156">Optional.</span></span> <span data-ttu-id="4c9f5-157">Bu yordamın bir veya daha fazla belirli olayı işleyebileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-157">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="4c9f5-158">Bkz. [işleyiciler](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="4c9f5-158">See [Handles](handles-clause.md).</span></span>

- `eventlist`

  <span data-ttu-id="4c9f5-159">Sağlanırsa gereklidir `Handles` .</span><span class="sxs-lookup"><span data-stu-id="4c9f5-159">Required if `Handles` is supplied.</span></span> <span data-ttu-id="4c9f5-160">Bu yordamın işleyeceği olayların listesi.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-160">List of events this procedure handles.</span></span>

  `eventspecifier [ , eventspecifier ... ]`

  <span data-ttu-id="4c9f5-161">Her birinin `eventspecifier` aşağıdaki söz dizimi ve parçaları vardır:</span><span class="sxs-lookup"><span data-stu-id="4c9f5-161">Each `eventspecifier` has the following syntax and parts:</span></span>

  `eventvariable.event`

  |<span data-ttu-id="4c9f5-162">Bölüm</span><span class="sxs-lookup"><span data-stu-id="4c9f5-162">Part</span></span>|<span data-ttu-id="4c9f5-163">Description</span><span class="sxs-lookup"><span data-stu-id="4c9f5-163">Description</span></span>|
  |---|---|
  |`eventvariable`|<span data-ttu-id="4c9f5-164">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-164">Required.</span></span> <span data-ttu-id="4c9f5-165">Olayı oluşturan sınıfın veya yapının veri türüyle belirtilen nesne değişkeni.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-165">Object variable declared with the data type of the class or structure that raises the event.</span></span>|
  |`event`|<span data-ttu-id="4c9f5-166">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-166">Required.</span></span> <span data-ttu-id="4c9f5-167">Bu yordamın işleyeceği olayın adı.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-167">Name of the event this procedure handles.</span></span>|

- `statements`

  <span data-ttu-id="4c9f5-168">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-168">Optional.</span></span> <span data-ttu-id="4c9f5-169">Bu yordam içinde çalıştırılacak deyimler bloğu.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-169">Block of statements to run within this procedure.</span></span>

- `End Sub`

  <span data-ttu-id="4c9f5-170">Bu yordamın tanımını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-170">Terminates the definition of this procedure.</span></span>

## <a name="remarks"></a><span data-ttu-id="4c9f5-171">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4c9f5-171">Remarks</span></span>

<span data-ttu-id="4c9f5-172">Tüm yürütülebilir kodların bir yordamın içinde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-172">All executable code must be inside a procedure.</span></span> <span data-ttu-id="4c9f5-173">`Sub`Çağırma koduna bir değer döndürmek istemediğinizde bir yordam kullanın.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-173">Use a `Sub` procedure when you don't want to return a value to the calling code.</span></span> <span data-ttu-id="4c9f5-174">Bir `Function` değer döndürmek istediğinizde bir yordam kullanın.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-174">Use a `Function` procedure when you want to return a value.</span></span>

## <a name="defining-a-sub-procedure"></a><span data-ttu-id="4c9f5-175">Bir alt yordam tanımlama</span><span class="sxs-lookup"><span data-stu-id="4c9f5-175">Defining a Sub Procedure</span></span>

<span data-ttu-id="4c9f5-176">Bir `Sub` yordamı yalnızca modül düzeyinde tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-176">You can define a `Sub` procedure only at the module level.</span></span> <span data-ttu-id="4c9f5-177">Bir alt yordamın bildirim bağlamı, bu nedenle bir sınıf, yapı, modül veya arabirim olmalıdır ve kaynak dosya, bir ad alanı, yordam veya bir blok olamaz.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-177">The declaration context for a sub procedure must, therefore, be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="4c9f5-178">Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="4c9f5-178">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="4c9f5-179">`Sub`yordamlar, genel erişim için varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-179">`Sub` procedures default to public access.</span></span> <span data-ttu-id="4c9f5-180">Erişim değiştiricilerini kullanarak erişim düzeylerini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-180">You can adjust their access levels by using the access modifiers.</span></span>

<span data-ttu-id="4c9f5-181">Yordam `Implements` anahtar sözcüğünü kullanıyorsa, kapsayan sınıf veya yapının, `Implements` veya ifadesiyle hemen sonraki bir deyime sahip olması gerekir `Class` `Structure` .</span><span class="sxs-lookup"><span data-stu-id="4c9f5-181">If the procedure uses the `Implements` keyword, the containing class or structure must have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="4c9f5-182">`Implements`İfadesinin içinde belirtilen her arabirimi içermesi gerekir `implementslist` .</span><span class="sxs-lookup"><span data-stu-id="4c9f5-182">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="4c9f5-183">Ancak, bir arabirimin `Sub` (içinde) tanımladığı adın `definedname` Bu yordamın adıyla eşleşmesi gerekmez (içinde `name` ).</span><span class="sxs-lookup"><span data-stu-id="4c9f5-183">However, the name by which an interface defines the `Sub` (in `definedname`) doesn't have to match the name of this procedure (in `name`).</span></span>

## <a name="returning-from-a-sub-procedure"></a><span data-ttu-id="4c9f5-184">Bir alt yordamdan dönme</span><span class="sxs-lookup"><span data-stu-id="4c9f5-184">Returning from a Sub Procedure</span></span>

<span data-ttu-id="4c9f5-185">Bir `Sub` yordam çağıran koda döndüğünde, yürütme onu çağıran deyimden sonra ifadesiyle devam eder.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-185">When a `Sub` procedure returns to the calling code, execution continues with the statement after the statement that called it.</span></span>

<span data-ttu-id="4c9f5-186">Aşağıdaki örnek bir yordamdan bir dönüş gösterir `Sub` .</span><span class="sxs-lookup"><span data-stu-id="4c9f5-186">The following example shows a return from a `Sub` procedure.</span></span>

```vb
Sub mySub(ByVal q As String)
    Return
End Sub
```

<span data-ttu-id="4c9f5-187">`Exit Sub`Ve `Return` deyimleri, bir yordamdan hemen çıkılmasına neden olur `Sub` .</span><span class="sxs-lookup"><span data-stu-id="4c9f5-187">The `Exit Sub` and `Return` statements cause an immediate exit from a `Sub` procedure.</span></span> <span data-ttu-id="4c9f5-188">Herhangi bir sayıda `Exit Sub` ve `Return` deyimi yordamda herhangi bir yerde görünebilir ve `Exit Sub` ve deyimlerini karıştırabilirsiniz `Return` .</span><span class="sxs-lookup"><span data-stu-id="4c9f5-188">Any number of `Exit Sub` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Sub` and `Return` statements.</span></span>

## <a name="calling-a-sub-procedure"></a><span data-ttu-id="4c9f5-189">Bir alt yordamı çağırma</span><span class="sxs-lookup"><span data-stu-id="4c9f5-189">Calling a Sub Procedure</span></span>

<span data-ttu-id="4c9f5-190">`Sub`Bir deyimindeki yordam adını kullanarak bir yordamı çağırır ve ardından bu adı parantez içindeki bağımsız değişken listesiyle takip edersiniz.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-190">You call a `Sub` procedure by using the procedure name in a statement and then following that name with its argument list in parentheses.</span></span> <span data-ttu-id="4c9f5-191">Parantezleri yalnızca herhangi bir bağımsız değişken belirtmezseniz atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-191">You can omit the parentheses only if you don't supply any arguments.</span></span> <span data-ttu-id="4c9f5-192">Ancak, her zaman parantezleri eklerseniz kodunuz daha okunabilir.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-192">However, your code is more readable if you always include the parentheses.</span></span>

<span data-ttu-id="4c9f5-193">Bir `Sub` yordam ve `Function` yordam parametrelere sahip olabilir ve bir dizi deyim gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-193">A `Sub` procedure and a `Function` procedure  can have parameters and perform a series of statements.</span></span> <span data-ttu-id="4c9f5-194">Ancak, bir `Function` yordam bir değer döndürür ve bir `Sub` yordam değildir.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-194">However, a `Function` procedure returns a value, and a `Sub` procedure doesn't.</span></span> <span data-ttu-id="4c9f5-195">Bu nedenle, bir ifadede bir `Sub` yordam kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-195">Therefore, you can't use a `Sub` procedure in an expression.</span></span>

<span data-ttu-id="4c9f5-196">`Call`Bir yordamı çağırdığınızda anahtar sözcüğünü kullanabilirsiniz `Sub` , ancak bu anahtar sözcük çoğu kullanımlar için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-196">You can use the `Call` keyword when you call a `Sub` procedure, but that keyword isn't recommended for most uses.</span></span> <span data-ttu-id="4c9f5-197">Daha fazla bilgi için bkz. [Call deyimleri](call-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4c9f5-197">For more information, see [Call Statement](call-statement.md).</span></span>

<span data-ttu-id="4c9f5-198">Visual Basic bazen, iç verimliliği artırmak için aritmetik ifadeleri yeniden düzenler.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-198">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="4c9f5-199">Bu nedenle, bağımsız değişken listeniz diğer yordamları çağıran ifadeler içeriyorsa, bu ifadelerin belirli bir sırada çağrılacağını varsaymamalıdır.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-199">For that reason, if your argument list includes expressions that call other procedures, you shouldn't assume that those expressions will be called in a particular order.</span></span>

## <a name="async-sub-procedures"></a><span data-ttu-id="4c9f5-200">Zaman uyumsuz alt yordamlar</span><span class="sxs-lookup"><span data-stu-id="4c9f5-200">Async Sub Procedures</span></span>

<span data-ttu-id="4c9f5-201">Async özelliğini kullanarak, zaman uyumsuz işlevleri açık geri çağırmaları kullanmadan çağırabilir veya kodunuzu birden çok işlev veya lambda ifadesine el ile böedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-201">By using the Async feature, you can invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>

<span data-ttu-id="4c9f5-202">Bir yordamı [zaman uyumsuz](../modifiers/async.md) değiştiriciyle işaretlerseniz, yordamda [await](../operators/await-operator.md) işlecini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-202">If you mark a procedure with the [Async](../modifiers/async.md) modifier, you can use the [Await](../operators/await-operator.md) operator in the procedure.</span></span> <span data-ttu-id="4c9f5-203">Denetim, yordamda bir `Await` ifadeye ulaştığında `Async` Denetim çağırana döner ve beklenen görev tamamlanana kadar yordamdaki ilerleme durumu askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-203">When control reaches an `Await` expression in the `Async` procedure, control returns to the caller, and progress in the procedure is suspended until the awaited task completes.</span></span> <span data-ttu-id="4c9f5-204">Görev tamamlandığında, yürütme yordamda çalışmaya çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-204">When the task is complete, execution can resume in the procedure.</span></span>

> [!NOTE]
> <span data-ttu-id="4c9f5-205">Bir `Async` yordam, henüz tamamlanmamış olan ilk bekleme nesnesine rastlandı veya `Async` yordamın sonuna ulaşıldığında, hangisi önce gerçekleşirse çağıran öğesine geri döner.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-205">An `Async` procedure returns to the caller when either the first awaited object that’s not yet complete is encountered or the end of the `Async` procedure is reached, whichever occurs first.</span></span>

<span data-ttu-id="4c9f5-206">Değiştirici ile bir [Işlev ifadesini](function-statement.md) de işaretleyebilirsiniz `Async` .</span><span class="sxs-lookup"><span data-stu-id="4c9f5-206">You can also mark a [Function Statement](function-statement.md) with the `Async` modifier.</span></span> <span data-ttu-id="4c9f5-207">Bir `Async` işlev, veya dönüş türüne sahip olabilir <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.Task> .</span><span class="sxs-lookup"><span data-stu-id="4c9f5-207">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="4c9f5-208">Bu konunun ilerleyen kısımlarında yer alan bir örnek `Async` , dönüş türü olan bir işlevi gösterir <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="4c9f5-208">An example later in this topic shows an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span>

<span data-ttu-id="4c9f5-209">`Async``Sub`yordamlar öncelikle bir değer döndürülmediğinde olay işleyicileri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-209">`Async` `Sub` procedures are primarily used for event handlers, where a value can't be returned.</span></span> <span data-ttu-id="4c9f5-210">Bir yordam beklenemez `Async` `Sub` ve bir yordamın çağıranı `Async` `Sub` yordamın aldığı özel durumları yakalayamaz `Sub` .</span><span class="sxs-lookup"><span data-stu-id="4c9f5-210">An `Async` `Sub` procedure can't be awaited, and the caller of an `Async` `Sub` procedure can't catch exceptions that the `Sub` procedure throws.</span></span>

<span data-ttu-id="4c9f5-211">Bir `Async` yordam [ByRef](../modifiers/byref.md) parametreleri bildiremez.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-211">An `Async` procedure can't declare any [ByRef](../modifiers/byref.md) parameters.</span></span>

<span data-ttu-id="4c9f5-212">Yordamlar hakkında daha fazla bilgi için `Async` bkz. [Async ve await Ile zaman uyumsuz programlama](../../programming-guide/concepts/async/index.md), [zaman uyumsuz programlarda denetim akışı](../../programming-guide/concepts/async/control-flow-in-async-programs.md)ve [zaman uyumsuz dönüş türleri](../../programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="4c9f5-212">For more information about `Async` procedures, see [Asynchronous Programming with Async and Await](../../programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../programming-guide/concepts/async/async-return-types.md).</span></span>

## <a name="example"></a><span data-ttu-id="4c9f5-213">Örnek</span><span class="sxs-lookup"><span data-stu-id="4c9f5-213">Example</span></span>

<span data-ttu-id="4c9f5-214">Aşağıdaki örnek, `Sub` bir yordamın gövdesini oluşturan adı, parametreleri ve kodu tanımlamak için ifadesini kullanır `Sub` .</span><span class="sxs-lookup"><span data-stu-id="4c9f5-214">The following example uses the `Sub` statement to define the name, parameters, and code that form the body of a `Sub` procedure.</span></span>

[!code-vb[VbVbalrStatements#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#58)]

## <a name="example"></a><span data-ttu-id="4c9f5-215">Örnek</span><span class="sxs-lookup"><span data-stu-id="4c9f5-215">Example</span></span>

<span data-ttu-id="4c9f5-216">Aşağıdaki örnekte, `DelayAsync` `Async` `Function` öğesinin dönüş türü olan bir <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="4c9f5-216">In the following example, `DelayAsync` is an `Async` `Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="4c9f5-217">`DelayAsync`, `Return` bir tamsayı döndüren bir ifadeye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-217">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="4c9f5-218">Bu nedenle, öğesinin işlev bildirimi `DelayAsync` bir dönüş türüne sahip olmalıdır `Task(Of Integer)` .</span><span class="sxs-lookup"><span data-stu-id="4c9f5-218">Therefore, the function declaration of `DelayAsync` must have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="4c9f5-219">Dönüş türü olduğu için `Task(Of Integer)` , `Await` içindeki ifadesinin değerlendirmesi `DoSomethingAsync` bir tamsayı oluşturur, çünkü aşağıdaki deyim şunu gösterir: `Dim result As Integer = Await delayTask` .</span><span class="sxs-lookup"><span data-stu-id="4c9f5-219">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer, as the following statement shows: `Dim result As Integer = Await delayTask`.</span></span>

<span data-ttu-id="4c9f5-220">`startButton_Click`Yordam bir `Async Sub` yordam örneğidir.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-220">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="4c9f5-221">`DoSomethingAsync`Bir işlev olduğundan `Async` , `DoSomethingAsync` Aşağıdaki ifadede gösterildiği gibi çağrının görevi beklenmelidir: `Await DoSomethingAsync()` .</span><span class="sxs-lookup"><span data-stu-id="4c9f5-221">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement shows: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="4c9f5-222">`startButton_Click` `Sub` Bir ifadesi içerdiğinden yordamın değiştirici ile tanımlanması gerekir `Async` `Await` .</span><span class="sxs-lookup"><span data-stu-id="4c9f5-222">The `startButton_Click` `Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a><span data-ttu-id="4c9f5-223">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c9f5-223">See also</span></span>

- [<span data-ttu-id="4c9f5-224">Implements Deyimi</span><span class="sxs-lookup"><span data-stu-id="4c9f5-224">Implements Statement</span></span>](implements-statement.md)
- [<span data-ttu-id="4c9f5-225">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="4c9f5-225">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="4c9f5-226">Parametre Listesi</span><span class="sxs-lookup"><span data-stu-id="4c9f5-226">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="4c9f5-227">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="4c9f5-227">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="4c9f5-228">Call Deyimi</span><span class="sxs-lookup"><span data-stu-id="4c9f5-228">Call Statement</span></span>](call-statement.md)
- [<span data-ttu-id="4c9f5-229">Durumunu</span><span class="sxs-lookup"><span data-stu-id="4c9f5-229">Of</span></span>](of-clause.md)
- [<span data-ttu-id="4c9f5-230">Parametre Dizileri</span><span class="sxs-lookup"><span data-stu-id="4c9f5-230">Parameter Arrays</span></span>](../../programming-guide/language-features/procedures/parameter-arrays.md)
- [<span data-ttu-id="4c9f5-231">Nasıl yapılır: Genel Bir Sınıf Kullanma</span><span class="sxs-lookup"><span data-stu-id="4c9f5-231">How to: Use a Generic Class</span></span>](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="4c9f5-232">Yordam Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="4c9f5-232">Troubleshooting Procedures</span></span>](../../programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [<span data-ttu-id="4c9f5-233">Kısmi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4c9f5-233">Partial Methods</span></span>](../../programming-guide/language-features/procedures/partial-methods.md)
