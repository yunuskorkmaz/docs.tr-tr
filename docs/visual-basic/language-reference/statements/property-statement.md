---
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
ms.openlocfilehash: 80bce2442d96ecb9c548a88c8e5ee44c6258473b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346752"
---
# <a name="property-statement"></a><span data-ttu-id="e0bac-102">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="e0bac-102">Property Statement</span></span>

<span data-ttu-id="e0bac-103">Bir özelliğin adını ve özellik değerini depolamak ve almak için kullanılan özellik yordamlarını bildirir.</span><span class="sxs-lookup"><span data-stu-id="e0bac-103">Declares the name of a property, and the property procedures used to store and retrieve the value of the property.</span></span>

## <a name="syntax"></a><span data-ttu-id="e0bac-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e0bac-104">Syntax</span></span>

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

## <a name="parts"></a><span data-ttu-id="e0bac-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="e0bac-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="e0bac-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e0bac-106">Optional.</span></span> <span data-ttu-id="e0bac-107">Bu özellik veya `Get` ya da `Set` yordamı için uygulanan özniteliklerin listesi.</span><span class="sxs-lookup"><span data-stu-id="e0bac-107">List of attributes that apply to this property or `Get` or `Set` procedure.</span></span> <span data-ttu-id="e0bac-108">Bkz. [öznitelik listesi](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="e0bac-108">See [Attribute List](attribute-list.md).</span></span>

- `Default`

  <span data-ttu-id="e0bac-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e0bac-109">Optional.</span></span> <span data-ttu-id="e0bac-110">Bu özelliğin tanımlandığı sınıf veya yapı için varsayılan özellik olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e0bac-110">Specifies that this property is the default property for the class or structure on which it is defined.</span></span> <span data-ttu-id="e0bac-111">Varsayılan Özellikler parametreleri kabul etmeli ve özellik adı belirtilmeden ayarlanabilir ve alınmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="e0bac-111">Default properties must accept parameters and can be set and retrieved without specifying the property name.</span></span> <span data-ttu-id="e0bac-112">Özelliği `Default`olarak bildirirseniz, özelliğinde veya özellik yordamlarından birinde `Private` kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="e0bac-112">If you declare the property as `Default`, you cannot use `Private` on the property or on either of its property procedures.</span></span>

- `accessmodifier`

  <span data-ttu-id="e0bac-113">`Property` deyiminde ve `Get` ve `Set` deyimlerinin en üstünde yer alan isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e0bac-113">Optional on the `Property` statement and on at most one of the `Get` and `Set` statements.</span></span> <span data-ttu-id="e0bac-114">Aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="e0bac-114">Can be one of the following:</span></span>

  - [<span data-ttu-id="e0bac-115">Public</span><span class="sxs-lookup"><span data-stu-id="e0bac-115">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="e0bac-116">Protected</span><span class="sxs-lookup"><span data-stu-id="e0bac-116">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="e0bac-117">Friend</span><span class="sxs-lookup"><span data-stu-id="e0bac-117">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="e0bac-118">Private</span><span class="sxs-lookup"><span data-stu-id="e0bac-118">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="e0bac-119">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="e0bac-119">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="e0bac-120">Private Protected</span><span class="sxs-lookup"><span data-stu-id="e0bac-120">Private Protected</span></span>](../modifiers/private-protected.md)

  <span data-ttu-id="e0bac-121">[Visual Basic erişim düzeylerine](../../programming-guide/language-features/declared-elements/access-levels.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="e0bac-121">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `propertymodifiers`

  <span data-ttu-id="e0bac-122">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e0bac-122">Optional.</span></span> <span data-ttu-id="e0bac-123">Aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="e0bac-123">Can be one of the following:</span></span>

  - [<span data-ttu-id="e0bac-124">Overloads</span><span class="sxs-lookup"><span data-stu-id="e0bac-124">Overloads</span></span>](../modifiers/overloads.md)

  - [<span data-ttu-id="e0bac-125">Overrides</span><span class="sxs-lookup"><span data-stu-id="e0bac-125">Overrides</span></span>](../modifiers/overrides.md)

  - [<span data-ttu-id="e0bac-126">Overridable</span><span class="sxs-lookup"><span data-stu-id="e0bac-126">Overridable</span></span>](../modifiers/overridable.md)

  - [<span data-ttu-id="e0bac-127">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="e0bac-127">NotOverridable</span></span>](../modifiers/notoverridable.md)

  - [<span data-ttu-id="e0bac-128">MustOverride</span><span class="sxs-lookup"><span data-stu-id="e0bac-128">MustOverride</span></span>](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  <span data-ttu-id="e0bac-129">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e0bac-129">Optional.</span></span> <span data-ttu-id="e0bac-130">Bkz. [paylaşılan](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="e0bac-130">See [Shared](../modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="e0bac-131">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e0bac-131">Optional.</span></span> <span data-ttu-id="e0bac-132">Bkz. [gölgeler](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="e0bac-132">See [Shadows](../modifiers/shadows.md).</span></span>

- `ReadOnly`

  <span data-ttu-id="e0bac-133">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e0bac-133">Optional.</span></span> <span data-ttu-id="e0bac-134">Bkz. [ReadOnly](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="e0bac-134">See [ReadOnly](../modifiers/readonly.md).</span></span>

- `WriteOnly`

  <span data-ttu-id="e0bac-135">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e0bac-135">Optional.</span></span> <span data-ttu-id="e0bac-136">Bkz. [WriteOnly](../modifiers/writeonly.md).</span><span class="sxs-lookup"><span data-stu-id="e0bac-136">See [WriteOnly](../modifiers/writeonly.md).</span></span>

- `Iterator`

  <span data-ttu-id="e0bac-137">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e0bac-137">Optional.</span></span> <span data-ttu-id="e0bac-138">Bkz. [Yineleyici](../modifiers/iterator.md).</span><span class="sxs-lookup"><span data-stu-id="e0bac-138">See [Iterator](../modifiers/iterator.md).</span></span>

- `name`

  <span data-ttu-id="e0bac-139">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="e0bac-139">Required.</span></span> <span data-ttu-id="e0bac-140">Özelliğin adı.</span><span class="sxs-lookup"><span data-stu-id="e0bac-140">Name of the property.</span></span> <span data-ttu-id="e0bac-141">Bkz. [tanımlanmış öğe adları](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="e0bac-141">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

- `parameterlist`

  <span data-ttu-id="e0bac-142">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e0bac-142">Optional.</span></span> <span data-ttu-id="e0bac-143">Bu özelliğin parametrelerini temsil eden yerel değişken adlarının listesi ve `Set` yordamının olası ek parametreleri.</span><span class="sxs-lookup"><span data-stu-id="e0bac-143">List of local variable names representing the parameters of this property, and possible additional parameters of the `Set` procedure.</span></span> <span data-ttu-id="e0bac-144">Bkz. [parametre listesi](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="e0bac-144">See [Parameter List](parameter-list.md).</span></span>

- `returntype`

  <span data-ttu-id="e0bac-145">`Option Strict` `On`olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0bac-145">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="e0bac-146">Bu özellik tarafından döndürülen değerin veri türü.</span><span class="sxs-lookup"><span data-stu-id="e0bac-146">Data type of the value returned by this property.</span></span>

- `Implements`

  <span data-ttu-id="e0bac-147">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e0bac-147">Optional.</span></span> <span data-ttu-id="e0bac-148">Bu özelliğin, her biri bu özelliğin kapsayan sınıf veya yapı tarafından uygulanan bir arabirimde tanımlanan bir veya daha fazla özelliği uyguladığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e0bac-148">Indicates that this property implements one or more properties, each one defined in an interface implemented by this property's containing class or structure.</span></span> <span data-ttu-id="e0bac-149">Bkz. [Implements açıklaması](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e0bac-149">See [Implements Statement](implements-statement.md).</span></span>

- `implementslist`

  <span data-ttu-id="e0bac-150">`Implements` sağlanırsa gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e0bac-150">Required if `Implements` is supplied.</span></span> <span data-ttu-id="e0bac-151">Uygulanan özelliklerin listesi.</span><span class="sxs-lookup"><span data-stu-id="e0bac-151">List of properties being implemented.</span></span>

  `implementedproperty [ , implementedproperty ... ]`

  <span data-ttu-id="e0bac-152">Her `implementedproperty` aşağıdaki söz dizimi ve bölümlere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="e0bac-152">Each `implementedproperty` has the following syntax and parts:</span></span>

  `interface.definedname`

  |<span data-ttu-id="e0bac-153">Bölümüyle</span><span class="sxs-lookup"><span data-stu-id="e0bac-153">Part</span></span>|<span data-ttu-id="e0bac-154">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e0bac-154">Description</span></span>|
  |---|---|
  |`interface`|<span data-ttu-id="e0bac-155">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="e0bac-155">Required.</span></span> <span data-ttu-id="e0bac-156">Bu özelliğin içeren sınıf veya yapı tarafından uygulanan bir arabirimin adı.</span><span class="sxs-lookup"><span data-stu-id="e0bac-156">Name of an interface implemented by this property's containing class or structure.</span></span>|
  |`definedname`|<span data-ttu-id="e0bac-157">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="e0bac-157">Required.</span></span> <span data-ttu-id="e0bac-158">Özelliğin `interface`tanımlı olduğu ad.</span><span class="sxs-lookup"><span data-stu-id="e0bac-158">Name by which the property is defined in `interface`.</span></span>|

- `Get`

  <span data-ttu-id="e0bac-159">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e0bac-159">Optional.</span></span> <span data-ttu-id="e0bac-160">Özellik `ReadOnly`olarak işaretlenmişse gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e0bac-160">Required if the property is marked `ReadOnly`.</span></span> <span data-ttu-id="e0bac-161">Özelliğin değerini döndürmek için kullanılan `Get` Özellik yordamını başlatır.</span><span class="sxs-lookup"><span data-stu-id="e0bac-161">Starts a `Get` property procedure that is used to return the value of the property.</span></span>  <span data-ttu-id="e0bac-162">`Get` deyimleri [Otomatik uygulanan özelliklerle](../../programming-guide/language-features/procedures/auto-implemented-properties.md)kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="e0bac-162">The `Get` statement is not used with [auto-implemented properties](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>

- `statements`

  <span data-ttu-id="e0bac-163">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e0bac-163">Optional.</span></span> <span data-ttu-id="e0bac-164">`Get` veya `Set` yordamında çalıştırılacak deyimler bloğu.</span><span class="sxs-lookup"><span data-stu-id="e0bac-164">Block of statements to run within the `Get` or `Set` procedure.</span></span>

- `End Get`

  <span data-ttu-id="e0bac-165">`Get` Özellik yordamını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="e0bac-165">Terminates the `Get` property procedure.</span></span>

- `Set`

  <span data-ttu-id="e0bac-166">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e0bac-166">Optional.</span></span> <span data-ttu-id="e0bac-167">Özellik `WriteOnly`olarak işaretlenmişse gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e0bac-167">Required if the property is marked `WriteOnly`.</span></span> <span data-ttu-id="e0bac-168">Özelliğin değerini depolamak için kullanılan `Set` Özellik yordamını başlatır.</span><span class="sxs-lookup"><span data-stu-id="e0bac-168">Starts a `Set` property procedure that is used to store the value of the property.</span></span>  <span data-ttu-id="e0bac-169">`Set` deyimleri [Otomatik uygulanan özelliklerle](../../programming-guide/language-features/procedures/auto-implemented-properties.md)kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="e0bac-169">The `Set` statement is not used with [auto-implemented properties](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>

- `End Set`

  <span data-ttu-id="e0bac-170">`Set` Özellik yordamını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="e0bac-170">Terminates the `Set` property procedure.</span></span>

- `End Property`

  <span data-ttu-id="e0bac-171">Bu özelliğin tanımını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="e0bac-171">Terminates the definition of this property.</span></span>

## <a name="remarks"></a><span data-ttu-id="e0bac-172">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e0bac-172">Remarks</span></span>

<span data-ttu-id="e0bac-173">`Property` ifade bir özelliğin bildirimini tanıtır.</span><span class="sxs-lookup"><span data-stu-id="e0bac-173">The `Property` statement introduces the declaration of a property.</span></span> <span data-ttu-id="e0bac-174">Bir özelliğin `Get` yordamı (salt okuma), bir `Set` yordamı (salt yazılır) veya her ikisi (okuma-yazma) olabilir.</span><span class="sxs-lookup"><span data-stu-id="e0bac-174">A property can have a `Get` procedure (read only), a `Set` procedure (write only), or both (read-write).</span></span> <span data-ttu-id="e0bac-175">Otomatik uygulanan bir özellik kullanırken `Get` ve `Set` yordamını atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0bac-175">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="e0bac-176">Daha fazla bilgi için bkz. [Otomatik uygulanan özellikler](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="e0bac-176">For more information, see [Auto-Implemented Properties](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>

<span data-ttu-id="e0bac-177">`Property` yalnızca sınıf düzeyinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0bac-177">You can use `Property` only at class level.</span></span> <span data-ttu-id="e0bac-178">Yani bir özelliğin *Bildirim bağlamı* bir sınıf, yapı, modül veya arabirim olmalıdır ve kaynak dosya, ad alanı, yordam veya blok olamaz.</span><span class="sxs-lookup"><span data-stu-id="e0bac-178">This means the *declaration context* for a property must be a class, structure, module, or interface, and cannot be a source file, namespace, procedure, or block.</span></span> <span data-ttu-id="e0bac-179">Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="e0bac-179">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="e0bac-180">Varsayılan olarak, Özellikler ortak erişim kullanır.</span><span class="sxs-lookup"><span data-stu-id="e0bac-180">By default, properties use public access.</span></span> <span data-ttu-id="e0bac-181">Bir özelliğin erişim düzeyini `Property` deyimindeki bir erişim değiştiricisiyle ayarlayabilirsiniz ve isteğe bağlı olarak özellik yordamlarından birini daha kısıtlayıcı bir erişim düzeyine ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0bac-181">You can adjust a property's access level with an access modifier on the `Property` statement, and you can optionally adjust one of its property procedures to a more restrictive access level.</span></span>

<span data-ttu-id="e0bac-182">Visual Basic, özellik atamaları sırasında `Set` yordama bir parametre geçirir.</span><span class="sxs-lookup"><span data-stu-id="e0bac-182">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="e0bac-183">`Set`için bir parametre belirtmezseniz, tümleşik geliştirme ortamı (IDE) `value`adlı örtük bir parametre kullanır.</span><span class="sxs-lookup"><span data-stu-id="e0bac-183">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="e0bac-184">Bu parametre, özelliğine atanacak değeri tutar.</span><span class="sxs-lookup"><span data-stu-id="e0bac-184">This parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="e0bac-185">Genellikle bu değeri özel bir yerel değişkende depolar ve `Get` yordamı her çağrıldığında döndürün.</span><span class="sxs-lookup"><span data-stu-id="e0bac-185">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>

## <a name="rules"></a><span data-ttu-id="e0bac-186">Kurallar</span><span class="sxs-lookup"><span data-stu-id="e0bac-186">Rules</span></span>

- <span data-ttu-id="e0bac-187">**Karışık erişim düzeyleri.**</span><span class="sxs-lookup"><span data-stu-id="e0bac-187">**Mixed Access Levels.**</span></span> <span data-ttu-id="e0bac-188">Okuma-yazma özelliği tanımlıyorsanız, isteğe bağlı olarak `Get` ya da `Set` yordamı için farklı bir erişim düzeyi belirtebilirsiniz, ancak her ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0bac-188">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="e0bac-189">Bunu yaparsanız, yordam erişim düzeyinin özelliğin erişim düzeyinden daha kısıtlayıcı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0bac-189">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="e0bac-190">Örneğin, özellik `Friend`olarak bildirilirse, `Private``Set` yordamını bildirebilirsiniz, ancak `Public`.</span><span class="sxs-lookup"><span data-stu-id="e0bac-190">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>

  <span data-ttu-id="e0bac-191">`ReadOnly` veya `WriteOnly` özelliğini tanımlıyorsanız, tek özellik yordamı (sırasıyla`Get` veya `Set`) tüm özelliği temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e0bac-191">If you are defining a `ReadOnly` or `WriteOnly` property, the single property procedure (`Get` or `Set`, respectively) represents all of the property.</span></span> <span data-ttu-id="e0bac-192">Bu tür bir yordam için farklı bir erişim düzeyi bildiremezsiniz, çünkü bu özellik için iki erişim düzeyi ayarlayacaktı.</span><span class="sxs-lookup"><span data-stu-id="e0bac-192">You cannot declare a different access level for such a procedure, because that would set two access levels for the property.</span></span>

- <span data-ttu-id="e0bac-193">**Dönüş türü.**</span><span class="sxs-lookup"><span data-stu-id="e0bac-193">**Return Type.**</span></span> <span data-ttu-id="e0bac-194">`Property` deyimin döndürdüğü değerin veri türünü bildirebilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e0bac-194">The `Property` statement can declare the data type of the value it returns.</span></span> <span data-ttu-id="e0bac-195">Herhangi bir veri türü veya bir numaralandırma, yapı, sınıf veya arabirim adı belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0bac-195">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>

  <span data-ttu-id="e0bac-196">`returntype`belirtmezseniz, özellik `Object`döndürür.</span><span class="sxs-lookup"><span data-stu-id="e0bac-196">If you do not specify `returntype`, the property returns `Object`.</span></span>

- <span data-ttu-id="e0bac-197">**Paylaşır.**</span><span class="sxs-lookup"><span data-stu-id="e0bac-197">**Implementation.**</span></span> <span data-ttu-id="e0bac-198">Bu özellik `Implements` anahtar sözcüğünü kullanıyorsa, kapsayan sınıf veya yapının `Class` veya `Structure` deyimlerinden hemen sonra bir `Implements` ifadesine sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0bac-198">If this property uses the `Implements` keyword, the containing class or structure must have an `Implements` statement immediately following its `Class` or `Structure` statement.</span></span> <span data-ttu-id="e0bac-199">`Implements` deyimin `implementslist`belirtilen her arabirimi içermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0bac-199">The `Implements` statement must include each interface specified in `implementslist`.</span></span> <span data-ttu-id="e0bac-200">Ancak, bir arabirimin `Property` tanımladığı ad (`definedname`), bu özelliğin adıyla aynı olması gerekmez (`name`).</span><span class="sxs-lookup"><span data-stu-id="e0bac-200">However, the name by which an interface defines the `Property` (in `definedname`) does not have to be the same as the name of this property (in `name`).</span></span>

## <a name="behavior"></a><span data-ttu-id="e0bac-201">Davranış</span><span class="sxs-lookup"><span data-stu-id="e0bac-201">Behavior</span></span>

- <span data-ttu-id="e0bac-202">**Bir özellik yordamından döndürülüyor.**</span><span class="sxs-lookup"><span data-stu-id="e0bac-202">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="e0bac-203">`Get` veya `Set` yordamı çağıran koda döndüğünde, yürütme onu çağıran deyimden sonraki deyimle devam eder.</span><span class="sxs-lookup"><span data-stu-id="e0bac-203">When the `Get` or `Set` procedure returns to the calling code, execution continues with the statement following the statement that invoked it.</span></span>

  <span data-ttu-id="e0bac-204">`Exit Property` ve `Return` deyimleri, bir özellik yordamından anında çıkış oluşmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="e0bac-204">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="e0bac-205">Herhangi bir sayıda `Exit Property` ve `Return` deyimi yordamda herhangi bir yerde görünebilir ve `Exit Property` ve `Return` deyimlerini karıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0bac-205">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>

- <span data-ttu-id="e0bac-206">**Dönüş değeri.**</span><span class="sxs-lookup"><span data-stu-id="e0bac-206">**Return Value.**</span></span> <span data-ttu-id="e0bac-207">`Get` yordamından bir değer döndürmek için değeri özellik adına atayabilir veya bir `Return` ifadesine ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0bac-207">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a `Return` statement.</span></span> <span data-ttu-id="e0bac-208">Aşağıdaki örnek, `quoteForTheDay` özellik adına döndürülen değeri atar ve sonra geri dönmek için `Exit Property` ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e0bac-208">The following example assigns the return value to the property name `quoteForTheDay` and then uses the `Exit Property` statement to return.</span></span>

  [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]

  [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]

  <span data-ttu-id="e0bac-209">`name`bir değer atamadan `Exit Property` kullanıyorsanız, `Get` yordamı özelliğin veri türü için varsayılan değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="e0bac-209">If you use `Exit Property` without assigning a value to `name`, the `Get` procedure returns the default value for the property's data type.</span></span>

  <span data-ttu-id="e0bac-210">Aynı anda `Return` deyimleri, `Get` yordam dönüş değerini atar ve yordamdan çıkar.</span><span class="sxs-lookup"><span data-stu-id="e0bac-210">The `Return` statement at the same time assigns the `Get` procedure return value and exits the procedure.</span></span> <span data-ttu-id="e0bac-211">Aşağıdaki örnek bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e0bac-211">The following example shows this.</span></span>

  [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]

  [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]

## <a name="example"></a><span data-ttu-id="e0bac-212">Örnek</span><span class="sxs-lookup"><span data-stu-id="e0bac-212">Example</span></span>

<span data-ttu-id="e0bac-213">Aşağıdaki örnek bir sınıfında bir özelliği bildirir.</span><span class="sxs-lookup"><span data-stu-id="e0bac-213">The following example declares a property in a class.</span></span>

[!code-vb[VbVbalrStatements#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#51)]

## <a name="see-also"></a><span data-ttu-id="e0bac-214">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0bac-214">See also</span></span>

- [<span data-ttu-id="e0bac-215">Otomatik Uygulanan Özellikler</span><span class="sxs-lookup"><span data-stu-id="e0bac-215">Auto-Implemented Properties</span></span>](../../programming-guide/language-features/procedures/auto-implemented-properties.md)
- [<span data-ttu-id="e0bac-216">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="e0bac-216">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="e0bac-217">Get Deyimi</span><span class="sxs-lookup"><span data-stu-id="e0bac-217">Get Statement</span></span>](get-statement.md)
- [<span data-ttu-id="e0bac-218">Set Deyimi</span><span class="sxs-lookup"><span data-stu-id="e0bac-218">Set Statement</span></span>](set-statement.md)
- [<span data-ttu-id="e0bac-219">Parametre Listesi</span><span class="sxs-lookup"><span data-stu-id="e0bac-219">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="e0bac-220">Default</span><span class="sxs-lookup"><span data-stu-id="e0bac-220">Default</span></span>](../modifiers/default.md)
