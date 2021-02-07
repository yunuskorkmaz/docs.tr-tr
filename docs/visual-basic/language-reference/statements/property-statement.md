---
description: 'Daha fazla bilgi edinin: Özellik açıklaması'
title: Property Deyimi
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
ms.openlocfilehash: 95f2ac1f993fc8698d2033dfe50d925cd55a7dc4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741399"
---
# <a name="property-statement"></a><span data-ttu-id="11128-103">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="11128-103">Property Statement</span></span>

<span data-ttu-id="11128-104">Bir özelliğin adını ve özellik değerini depolamak ve almak için kullanılan özellik yordamlarını bildirir.</span><span class="sxs-lookup"><span data-stu-id="11128-104">Declares the name of a property, and the property procedures used to store and retrieve the value of the property.</span></span>

## <a name="syntax"></a><span data-ttu-id="11128-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="11128-105">Syntax</span></span>

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

## <a name="parts"></a><span data-ttu-id="11128-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="11128-106">Parts</span></span>

- `attributelist`

  <span data-ttu-id="11128-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="11128-107">Optional.</span></span> <span data-ttu-id="11128-108">Bu özellik veya yordam için uygulanan özniteliklerin listesi `Get` `Set` .</span><span class="sxs-lookup"><span data-stu-id="11128-108">List of attributes that apply to this property or `Get` or `Set` procedure.</span></span> <span data-ttu-id="11128-109">Bkz. [öznitelik listesi](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="11128-109">See [Attribute List](attribute-list.md).</span></span>

- `Default`

  <span data-ttu-id="11128-110">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="11128-110">Optional.</span></span> <span data-ttu-id="11128-111">Bu özelliğin tanımlandığı sınıf veya yapı için varsayılan özellik olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="11128-111">Specifies that this property is the default property for the class or structure on which it is defined.</span></span> <span data-ttu-id="11128-112">Varsayılan Özellikler parametreleri kabul etmeli ve özellik adı belirtilmeden ayarlanabilir ve alınmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="11128-112">Default properties must accept parameters and can be set and retrieved without specifying the property name.</span></span> <span data-ttu-id="11128-113">Özelliğini olarak bildirirseniz `Default` , özelliğinde `Private` veya özellik yordamlarından birinde kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="11128-113">If you declare the property as `Default`, you cannot use `Private` on the property or on either of its property procedures.</span></span>

- `accessmodifier`

  <span data-ttu-id="11128-114">`Property`Deyimde ve `Get` ve deyimlerinin en üzerinde isteğe bağlı `Set` .</span><span class="sxs-lookup"><span data-stu-id="11128-114">Optional on the `Property` statement and on at most one of the `Get` and `Set` statements.</span></span> <span data-ttu-id="11128-115">Aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="11128-115">Can be one of the following:</span></span>

  - [<span data-ttu-id="11128-116">Genel</span><span class="sxs-lookup"><span data-stu-id="11128-116">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="11128-117">Korunamadı</span><span class="sxs-lookup"><span data-stu-id="11128-117">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="11128-118">Arkadaş</span><span class="sxs-lookup"><span data-stu-id="11128-118">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="11128-119">Özel</span><span class="sxs-lookup"><span data-stu-id="11128-119">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="11128-120">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="11128-120">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="11128-121">Özel korumalı</span><span class="sxs-lookup"><span data-stu-id="11128-121">Private Protected</span></span>](../modifiers/private-protected.md)

  <span data-ttu-id="11128-122">[Visual Basic erişim düzeylerine](../../programming-guide/language-features/declared-elements/access-levels.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="11128-122">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `propertymodifiers`

  <span data-ttu-id="11128-123">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="11128-123">Optional.</span></span> <span data-ttu-id="11128-124">Aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="11128-124">Can be one of the following:</span></span>

  - [<span data-ttu-id="11128-125">Aşırı Yüklemeler</span><span class="sxs-lookup"><span data-stu-id="11128-125">Overloads</span></span>](../modifiers/overloads.md)

  - [<span data-ttu-id="11128-126">Geçersiz Kılmalar</span><span class="sxs-lookup"><span data-stu-id="11128-126">Overrides</span></span>](../modifiers/overrides.md)

  - [<span data-ttu-id="11128-127">Overridable</span><span class="sxs-lookup"><span data-stu-id="11128-127">Overridable</span></span>](../modifiers/overridable.md)

  - [<span data-ttu-id="11128-128">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="11128-128">NotOverridable</span></span>](../modifiers/notoverridable.md)

  - [<span data-ttu-id="11128-129">MustOverride</span><span class="sxs-lookup"><span data-stu-id="11128-129">MustOverride</span></span>](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  <span data-ttu-id="11128-130">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="11128-130">Optional.</span></span> <span data-ttu-id="11128-131">Bkz. [paylaşılan](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="11128-131">See [Shared](../modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="11128-132">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="11128-132">Optional.</span></span> <span data-ttu-id="11128-133">Bkz. [gölgeler](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="11128-133">See [Shadows](../modifiers/shadows.md).</span></span>

- `ReadOnly`

  <span data-ttu-id="11128-134">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="11128-134">Optional.</span></span> <span data-ttu-id="11128-135">Bkz. [ReadOnly](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="11128-135">See [ReadOnly](../modifiers/readonly.md).</span></span>

- `WriteOnly`

  <span data-ttu-id="11128-136">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="11128-136">Optional.</span></span> <span data-ttu-id="11128-137">Bkz. [WriteOnly](../modifiers/writeonly.md).</span><span class="sxs-lookup"><span data-stu-id="11128-137">See [WriteOnly](../modifiers/writeonly.md).</span></span>

- `Iterator`

  <span data-ttu-id="11128-138">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="11128-138">Optional.</span></span> <span data-ttu-id="11128-139">Bkz. [Yineleyici](../modifiers/iterator.md).</span><span class="sxs-lookup"><span data-stu-id="11128-139">See [Iterator](../modifiers/iterator.md).</span></span>

- `name`

  <span data-ttu-id="11128-140">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="11128-140">Required.</span></span> <span data-ttu-id="11128-141">Özelliğin adı.</span><span class="sxs-lookup"><span data-stu-id="11128-141">Name of the property.</span></span> <span data-ttu-id="11128-142">Bkz. [tanımlanmış öğe adları](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="11128-142">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

- `parameterlist`

  <span data-ttu-id="11128-143">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="11128-143">Optional.</span></span> <span data-ttu-id="11128-144">Bu özelliğin parametrelerini ve yordamın olası ek parametrelerini temsil eden yerel değişken adlarının listesi `Set` .</span><span class="sxs-lookup"><span data-stu-id="11128-144">List of local variable names representing the parameters of this property, and possible additional parameters of the `Set` procedure.</span></span> <span data-ttu-id="11128-145">Bkz. [parametre listesi](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="11128-145">See [Parameter List](parameter-list.md).</span></span>

- `returntype`

  <span data-ttu-id="11128-146">İse gereklidir `Option Strict` `On` .</span><span class="sxs-lookup"><span data-stu-id="11128-146">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="11128-147">Bu özellik tarafından döndürülen değerin veri türü.</span><span class="sxs-lookup"><span data-stu-id="11128-147">Data type of the value returned by this property.</span></span>

- `Implements`

  <span data-ttu-id="11128-148">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="11128-148">Optional.</span></span> <span data-ttu-id="11128-149">Bu özelliğin, her biri bu özelliğin kapsayan sınıf veya yapı tarafından uygulanan bir arabirimde tanımlanan bir veya daha fazla özelliği uyguladığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="11128-149">Indicates that this property implements one or more properties, each one defined in an interface implemented by this property's containing class or structure.</span></span> <span data-ttu-id="11128-150">Bkz. [Implements açıklaması](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="11128-150">See [Implements Statement](implements-statement.md).</span></span>

- `implementslist`

  <span data-ttu-id="11128-151">Sağlanırsa gereklidir `Implements` .</span><span class="sxs-lookup"><span data-stu-id="11128-151">Required if `Implements` is supplied.</span></span> <span data-ttu-id="11128-152">Uygulanan özelliklerin listesi.</span><span class="sxs-lookup"><span data-stu-id="11128-152">List of properties being implemented.</span></span>

  `implementedproperty [ , implementedproperty ... ]`

  <span data-ttu-id="11128-153">Her birinin `implementedproperty` aşağıdaki söz dizimi ve parçaları vardır:</span><span class="sxs-lookup"><span data-stu-id="11128-153">Each `implementedproperty` has the following syntax and parts:</span></span>

  `interface.definedname`

  |<span data-ttu-id="11128-154">Bölüm</span><span class="sxs-lookup"><span data-stu-id="11128-154">Part</span></span>|<span data-ttu-id="11128-155">Description</span><span class="sxs-lookup"><span data-stu-id="11128-155">Description</span></span>|
  |---|---|
  |`interface`|<span data-ttu-id="11128-156">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="11128-156">Required.</span></span> <span data-ttu-id="11128-157">Bu özelliğin içeren sınıf veya yapı tarafından uygulanan bir arabirimin adı.</span><span class="sxs-lookup"><span data-stu-id="11128-157">Name of an interface implemented by this property's containing class or structure.</span></span>|
  |`definedname`|<span data-ttu-id="11128-158">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="11128-158">Required.</span></span> <span data-ttu-id="11128-159">Özelliğin tanımlandığı ad `interface` .</span><span class="sxs-lookup"><span data-stu-id="11128-159">Name by which the property is defined in `interface`.</span></span>|

- `Get`

  <span data-ttu-id="11128-160">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="11128-160">Optional.</span></span> <span data-ttu-id="11128-161">Özellik işaretlenmişse gereklidir `ReadOnly` .</span><span class="sxs-lookup"><span data-stu-id="11128-161">Required if the property is marked `ReadOnly`.</span></span> <span data-ttu-id="11128-162">`Get`Özelliğin değerini döndürmek için kullanılan bir özellik yordamını başlatır.</span><span class="sxs-lookup"><span data-stu-id="11128-162">Starts a `Get` property procedure that is used to return the value of the property.</span></span>  <span data-ttu-id="11128-163">`Get`İfade, [Otomatik uygulanan özelliklerle](../../programming-guide/language-features/procedures/auto-implemented-properties.md)kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="11128-163">The `Get` statement is not used with [auto-implemented properties](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>

- `statements`

  <span data-ttu-id="11128-164">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="11128-164">Optional.</span></span> <span data-ttu-id="11128-165">Or yordamı içinde çalıştırılacak deyimler bloğu `Get` `Set` .</span><span class="sxs-lookup"><span data-stu-id="11128-165">Block of statements to run within the `Get` or `Set` procedure.</span></span>

- `End Get`

  <span data-ttu-id="11128-166">`Get`Özellik yordamını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="11128-166">Terminates the `Get` property procedure.</span></span>

- `Set`

  <span data-ttu-id="11128-167">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="11128-167">Optional.</span></span> <span data-ttu-id="11128-168">Özellik işaretlenmişse gereklidir `WriteOnly` .</span><span class="sxs-lookup"><span data-stu-id="11128-168">Required if the property is marked `WriteOnly`.</span></span> <span data-ttu-id="11128-169">`Set`Özelliğin değerini depolamak için kullanılan bir özellik yordamını başlatır.</span><span class="sxs-lookup"><span data-stu-id="11128-169">Starts a `Set` property procedure that is used to store the value of the property.</span></span>  <span data-ttu-id="11128-170">`Set`İfade, [Otomatik uygulanan özelliklerle](../../programming-guide/language-features/procedures/auto-implemented-properties.md)kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="11128-170">The `Set` statement is not used with [auto-implemented properties](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>

- `End Set`

  <span data-ttu-id="11128-171">`Set`Özellik yordamını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="11128-171">Terminates the `Set` property procedure.</span></span>

- `End Property`

  <span data-ttu-id="11128-172">Bu özelliğin tanımını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="11128-172">Terminates the definition of this property.</span></span>

## <a name="remarks"></a><span data-ttu-id="11128-173">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="11128-173">Remarks</span></span>

<span data-ttu-id="11128-174">`Property`İfade bir özelliğin bildirimini tanıtır.</span><span class="sxs-lookup"><span data-stu-id="11128-174">The `Property` statement introduces the declaration of a property.</span></span> <span data-ttu-id="11128-175">Bir özellik bir `Get` yordama (salt okuma), bir `Set` yordama (salt yazılır) veya her ikisine (okuma-yazma) sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="11128-175">A property can have a `Get` procedure (read only), a `Set` procedure (write only), or both (read-write).</span></span> <span data-ttu-id="11128-176">`Get` `Set` Otomatik uygulanan bir özellik kullanırken ve yordamını atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="11128-176">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="11128-177">Daha fazla bilgi için bkz. [Otomatik uygulanan özellikler](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="11128-177">For more information, see [Auto-Implemented Properties](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>

<span data-ttu-id="11128-178">`Property`Yalnızca sınıf düzeyinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="11128-178">You can use `Property` only at class level.</span></span> <span data-ttu-id="11128-179">Yani bir özelliğin *Bildirim bağlamı* bir sınıf, yapı, modül veya arabirim olmalıdır ve kaynak dosya, ad alanı, yordam veya blok olamaz.</span><span class="sxs-lookup"><span data-stu-id="11128-179">This means the *declaration context* for a property must be a class, structure, module, or interface, and cannot be a source file, namespace, procedure, or block.</span></span> <span data-ttu-id="11128-180">Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="11128-180">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="11128-181">Varsayılan olarak, Özellikler ortak erişim kullanır.</span><span class="sxs-lookup"><span data-stu-id="11128-181">By default, properties use public access.</span></span> <span data-ttu-id="11128-182">Bir özelliğin erişim düzeyini deyimdeki bir erişim değiştiricisiyle ayarlayabilirsiniz `Property` ve isteğe bağlı olarak özellik yordamlarından birini daha kısıtlayıcı bir erişim düzeyine ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="11128-182">You can adjust a property's access level with an access modifier on the `Property` statement, and you can optionally adjust one of its property procedures to a more restrictive access level.</span></span>

<span data-ttu-id="11128-183">Visual Basic, `Set` özellik atamaları sırasında yordama bir parametre geçirir.</span><span class="sxs-lookup"><span data-stu-id="11128-183">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="11128-184">İçin bir parametre belirtmezseniz `Set` , tümleşik geliştirme ortamı (IDE) adlı örtülü bir parametre kullanır `value` .</span><span class="sxs-lookup"><span data-stu-id="11128-184">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="11128-185">Bu parametre, özelliğine atanacak değeri tutar.</span><span class="sxs-lookup"><span data-stu-id="11128-185">This parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="11128-186">Genellikle bu değeri özel bir yerel değişkende depoluyordu ve yordam her çağrıldığında döndürülür `Get` .</span><span class="sxs-lookup"><span data-stu-id="11128-186">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>

## <a name="rules"></a><span data-ttu-id="11128-187">Kurallar</span><span class="sxs-lookup"><span data-stu-id="11128-187">Rules</span></span>

- <span data-ttu-id="11128-188">**Karışık erişim düzeyleri.**</span><span class="sxs-lookup"><span data-stu-id="11128-188">**Mixed Access Levels.**</span></span> <span data-ttu-id="11128-189">Okuma-yazma özelliği tanımlıyorsanız, isteğe bağlı olarak ya da yordam için farklı bir erişim düzeyi belirtebilirsiniz `Get` `Set` , ancak her ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="11128-189">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="11128-190">Bunu yaparsanız, yordam erişim düzeyinin özelliğin erişim düzeyinden daha kısıtlayıcı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="11128-190">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="11128-191">Örneğin, özelliği bildirilirse, `Friend` `Set` yordamı bildirebilirsiniz `Private` , ancak kullanamazsınız `Public` .</span><span class="sxs-lookup"><span data-stu-id="11128-191">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>

  <span data-ttu-id="11128-192">`ReadOnly`Veya `WriteOnly` özelliğini tanımlıyorsanız, tek özellik yordamı ( `Get` veya `Set` sırasıyla) tüm özelliği temsil eder.</span><span class="sxs-lookup"><span data-stu-id="11128-192">If you are defining a `ReadOnly` or `WriteOnly` property, the single property procedure (`Get` or `Set`, respectively) represents all of the property.</span></span> <span data-ttu-id="11128-193">Bu tür bir yordam için farklı bir erişim düzeyi bildiremezsiniz, çünkü bu özellik için iki erişim düzeyi ayarlayacaktı.</span><span class="sxs-lookup"><span data-stu-id="11128-193">You cannot declare a different access level for such a procedure, because that would set two access levels for the property.</span></span>

- <span data-ttu-id="11128-194">**Dönüş türü.**</span><span class="sxs-lookup"><span data-stu-id="11128-194">**Return Type.**</span></span> <span data-ttu-id="11128-195">`Property`İfade, döndürdüğü değerin veri türünü bildirebilirler.</span><span class="sxs-lookup"><span data-stu-id="11128-195">The `Property` statement can declare the data type of the value it returns.</span></span> <span data-ttu-id="11128-196">Herhangi bir veri türü veya bir numaralandırma, yapı, sınıf veya arabirim adı belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="11128-196">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>

  <span data-ttu-id="11128-197">Belirtmezseniz `returntype` , özelliği döndürür `Object` .</span><span class="sxs-lookup"><span data-stu-id="11128-197">If you do not specify `returntype`, the property returns `Object`.</span></span>

- <span data-ttu-id="11128-198">**Paylaşır.**</span><span class="sxs-lookup"><span data-stu-id="11128-198">**Implementation.**</span></span> <span data-ttu-id="11128-199">Bu özellik `Implements` anahtar sözcüğünü kullanıyorsa, kapsayan sınıf veya yapının, `Implements` veya bildiriminin hemen ardından bir ifadeye sahip olması `Class` gerekir `Structure` .</span><span class="sxs-lookup"><span data-stu-id="11128-199">If this property uses the `Implements` keyword, the containing class or structure must have an `Implements` statement immediately following its `Class` or `Structure` statement.</span></span> <span data-ttu-id="11128-200">`Implements`Deyimin içinde belirtilen her arabirimi içermesi gerekir `implementslist` .</span><span class="sxs-lookup"><span data-stu-id="11128-200">The `Implements` statement must include each interface specified in `implementslist`.</span></span> <span data-ttu-id="11128-201">Ancak, bir arabirimin `Property` (içinde) tanımladığı adın `definedname` Bu özelliğin adıyla aynı olması gerekmez (içinde `name` ).</span><span class="sxs-lookup"><span data-stu-id="11128-201">However, the name by which an interface defines the `Property` (in `definedname`) does not have to be the same as the name of this property (in `name`).</span></span>

## <a name="behavior"></a><span data-ttu-id="11128-202">Davranış</span><span class="sxs-lookup"><span data-stu-id="11128-202">Behavior</span></span>

- <span data-ttu-id="11128-203">**Bir özellik yordamından döndürülüyor.**</span><span class="sxs-lookup"><span data-stu-id="11128-203">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="11128-204">Ya da `Get` `Set` yordamı çağıran koda döndüğünde, yürütme onu çağıran deyimden sonraki deyimle devam eder.</span><span class="sxs-lookup"><span data-stu-id="11128-204">When the `Get` or `Set` procedure returns to the calling code, execution continues with the statement following the statement that invoked it.</span></span>

  <span data-ttu-id="11128-205">`Exit Property`Ve `Return` deyimleri, bir özellik yordamından anında çıkış oluşmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="11128-205">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="11128-206">Herhangi bir sayıda `Exit Property` ve `Return` deyimi yordamda herhangi bir yerde görünebilir ve `Exit Property` ve deyimlerini karıştırabilirsiniz `Return` .</span><span class="sxs-lookup"><span data-stu-id="11128-206">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>

- <span data-ttu-id="11128-207">**Dönüş değeri.**</span><span class="sxs-lookup"><span data-stu-id="11128-207">**Return Value.**</span></span> <span data-ttu-id="11128-208">Bir yordamdan bir değer döndürmek için `Get` , değeri özellik adına atayabilir veya bir deyime dahil edebilirsiniz `Return` .</span><span class="sxs-lookup"><span data-stu-id="11128-208">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a `Return` statement.</span></span> <span data-ttu-id="11128-209">Aşağıdaki örnek, dönüş değerini özellik adına atar `quoteForTheDay` ve ardından `Exit Property` döndürmek için ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="11128-209">The following example assigns the return value to the property name `quoteForTheDay` and then uses the `Exit Property` statement to return.</span></span>

  [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]

  [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]

  <span data-ttu-id="11128-210">`Exit Property`' A değer atamakla kullanırsanız `name` , `Get` yordam özelliğin veri türü için varsayılan değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="11128-210">If you use `Exit Property` without assigning a value to `name`, the `Get` procedure returns the default value for the property's data type.</span></span>

  <span data-ttu-id="11128-211">`Return`Aynı anda yer aldığı ifade, `Get` yordam dönüş değerini atar ve yordamdan çıkar.</span><span class="sxs-lookup"><span data-stu-id="11128-211">The `Return` statement at the same time assigns the `Get` procedure return value and exits the procedure.</span></span> <span data-ttu-id="11128-212">Aşağıdaki örnek bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="11128-212">The following example shows this.</span></span>

  [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]

  [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]

## <a name="example"></a><span data-ttu-id="11128-213">Örnek</span><span class="sxs-lookup"><span data-stu-id="11128-213">Example</span></span>

<span data-ttu-id="11128-214">Aşağıdaki örnek bir sınıfında bir özelliği bildirir.</span><span class="sxs-lookup"><span data-stu-id="11128-214">The following example declares a property in a class.</span></span>

[!code-vb[VbVbalrStatements#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#51)]

## <a name="see-also"></a><span data-ttu-id="11128-215">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11128-215">See also</span></span>

- [<span data-ttu-id="11128-216">Otomatik Uygulanan Özellikler</span><span class="sxs-lookup"><span data-stu-id="11128-216">Auto-Implemented Properties</span></span>](../../programming-guide/language-features/procedures/auto-implemented-properties.md)
- [<span data-ttu-id="11128-217">Nesneler ve sınıflar</span><span class="sxs-lookup"><span data-stu-id="11128-217">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="11128-218">Get Deyimi</span><span class="sxs-lookup"><span data-stu-id="11128-218">Get Statement</span></span>](get-statement.md)
- [<span data-ttu-id="11128-219">Set deyimleri</span><span class="sxs-lookup"><span data-stu-id="11128-219">Set Statement</span></span>](set-statement.md)
- [<span data-ttu-id="11128-220">Parametre Listesi</span><span class="sxs-lookup"><span data-stu-id="11128-220">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="11128-221">Varsayılanını</span><span class="sxs-lookup"><span data-stu-id="11128-221">Default</span></span>](../modifiers/default.md)
