---
description: 'Daha fazla bilgi edinin: const ekstresi (Visual Basic)'
title: Const Deyimi
ms.date: 05/12/2018
f1_keywords:
- vb.Const
helpviewer_keywords:
- Const statement [Visual Basic]
ms.assetid: 495b318d-b7c5-4198-94f8-0790a541b07a
ms.openlocfilehash: 61d898823c7697c91b207a502417b49cdeaf5eea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673862"
---
# <a name="const-statement-visual-basic"></a><span data-ttu-id="07bf8-103">Const Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="07bf8-103">Const Statement (Visual Basic)</span></span>

<span data-ttu-id="07bf8-104">Bir veya daha fazla sabiti bildirir ve tanımlar.</span><span class="sxs-lookup"><span data-stu-id="07bf8-104">Declares and defines one or more constants.</span></span>

## <a name="syntax"></a><span data-ttu-id="07bf8-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="07bf8-105">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ] [ Shadows ]
Const constantlist
```

## <a name="parts"></a><span data-ttu-id="07bf8-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="07bf8-106">Parts</span></span>

`attributelist`  
<span data-ttu-id="07bf8-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="07bf8-107">Optional.</span></span> <span data-ttu-id="07bf8-108">Bu bildirimde belirtilen tüm sabitlere uygulanan özniteliklerin listesi.</span><span class="sxs-lookup"><span data-stu-id="07bf8-108">List of attributes that apply to all the constants declared in this statement.</span></span> <span data-ttu-id="07bf8-109">[Öznitelik listesini](attribute-list.md) açılı ayraçlar (" `<` " ve " `>` ") içinde görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="07bf8-109">See [Attribute List](attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>

`accessmodifier`  
<span data-ttu-id="07bf8-110">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="07bf8-110">Optional.</span></span> <span data-ttu-id="07bf8-111">Bu sabitlere hangi kodun erişebileceğini belirtmek için bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="07bf8-111">Use this to specify what code can access these constants.</span></span> <span data-ttu-id="07bf8-112">[Ortak](../modifiers/public.md), [korumalı](../modifiers/protected.md), [arkadaş](../modifiers/friend.md), [korumalı arkadaş](../modifiers/protected-friend.md), [özel](../modifiers/private.md)veya [özel korumalı](../modifiers/private-protected.md)olabilir.</span><span class="sxs-lookup"><span data-stu-id="07bf8-112">Can be [Public](../modifiers/public.md), [Protected](../modifiers/protected.md), [Friend](../modifiers/friend.md), [Protected Friend](../modifiers/protected-friend.md), [Private](../modifiers/private.md), or [Private Protected](../modifiers/private-protected.md).</span></span>

`Shadows`  
<span data-ttu-id="07bf8-113">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="07bf8-113">Optional.</span></span> <span data-ttu-id="07bf8-114">Bir temel sınıftaki programlama öğesini yeniden bildirmek ve gizlemek için bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="07bf8-114">Use this to redeclare and hide a programming element in a base class.</span></span> <span data-ttu-id="07bf8-115">Bkz. [gölgeler](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="07bf8-115">See [Shadows](../modifiers/shadows.md).</span></span>

`constantlist`  
<span data-ttu-id="07bf8-116">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="07bf8-116">Required.</span></span> <span data-ttu-id="07bf8-117">Bu bildirimde bildirildiği sabitlerin listesi.</span><span class="sxs-lookup"><span data-stu-id="07bf8-117">List of constants being declared in this statement.</span></span>

<span data-ttu-id="07bf8-118">`constant` `[ ,` `constant` `... ]`</span><span class="sxs-lookup"><span data-stu-id="07bf8-118">`constant` `[ ,` `constant` `... ]`</span></span>

<span data-ttu-id="07bf8-119">Her birinin `constant` aşağıdaki söz dizimi ve parçaları vardır:</span><span class="sxs-lookup"><span data-stu-id="07bf8-119">Each `constant` has the following syntax and parts:</span></span>

<span data-ttu-id="07bf8-120">`constantname` `[ As` `datatype` `] =` `initializer`</span><span class="sxs-lookup"><span data-stu-id="07bf8-120">`constantname` `[ As` `datatype` `] =` `initializer`</span></span>

|<span data-ttu-id="07bf8-121">Bölüm</span><span class="sxs-lookup"><span data-stu-id="07bf8-121">Part</span></span>|<span data-ttu-id="07bf8-122">Description</span><span class="sxs-lookup"><span data-stu-id="07bf8-122">Description</span></span>|
|----------|-----------------|
|`constantname`|<span data-ttu-id="07bf8-123">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="07bf8-123">Required.</span></span> <span data-ttu-id="07bf8-124">Sabitin adı.</span><span class="sxs-lookup"><span data-stu-id="07bf8-124">Name of the constant.</span></span> <span data-ttu-id="07bf8-125">Bkz. [tanımlanmış öğe adları](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="07bf8-125">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|
|`datatype`|<span data-ttu-id="07bf8-126">İse gereklidir `Option Strict` `On` .</span><span class="sxs-lookup"><span data-stu-id="07bf8-126">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="07bf8-127">Sabitin veri türü.</span><span class="sxs-lookup"><span data-stu-id="07bf8-127">Data type of the constant.</span></span>|
|`initializer`|<span data-ttu-id="07bf8-128">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="07bf8-128">Required.</span></span> <span data-ttu-id="07bf8-129">Derleme zamanında değerlendirilen ve sabitine atanan ifade.</span><span class="sxs-lookup"><span data-stu-id="07bf8-129">Expression that is evaluated at compile time and assigned to the constant.</span></span>|

## <a name="remarks"></a><span data-ttu-id="07bf8-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="07bf8-130">Remarks</span></span>

<span data-ttu-id="07bf8-131">Uygulamanızda hiçbir değişiklik olmayan bir değer varsa, adlandırılmış bir sabit tanımlayabilir ve bunu bir sabit değer yerine kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07bf8-131">If you have a value that never changes in your application, you can define a named constant and use it in place of a literal value.</span></span> <span data-ttu-id="07bf8-132">Bir ad, bir değerden daha kolay anımsanacak.</span><span class="sxs-lookup"><span data-stu-id="07bf8-132">A name is easier to remember than a value.</span></span> <span data-ttu-id="07bf8-133">Sabiti yalnızca bir kez tanımlayabilir ve kodunuzda birçok yerde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07bf8-133">You can define the constant just once and use it in many places in your code.</span></span> <span data-ttu-id="07bf8-134">Daha sonraki bir sürümde değeri yeniden tanımlamanız gerekiyorsa, `Const` bir değişiklik yapmak için ihtiyacınız olan tek yerdir.</span><span class="sxs-lookup"><span data-stu-id="07bf8-134">If in a later version you need to redefine the value, the `Const` statement is the only place you need to make a change.</span></span>

<span data-ttu-id="07bf8-135">`Const`Yalnızca modül veya yordam düzeyinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07bf8-135">You can use `Const` only at module or procedure level.</span></span> <span data-ttu-id="07bf8-136">Diğer bir deyişle, bir değişken için *Bildirim bağlamı* bir sınıf, yapı, modül, yordam veya blok olmalıdır ve kaynak dosya, ad alanı veya arabirim olamaz.</span><span class="sxs-lookup"><span data-stu-id="07bf8-136">This means the *declaration context* for a variable must be a class, structure, module, procedure, or block, and cannot be a source file, namespace, or interface.</span></span> <span data-ttu-id="07bf8-137">Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="07bf8-137">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="07bf8-138">Yerel sabitler (bir yordam içinde) varsayılan olarak genel erişime ve bunlara hiçbir erişim değiştiricilerini kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="07bf8-138">Local constants (inside a procedure) default to public access, and you cannot use any access modifiers on them.</span></span> <span data-ttu-id="07bf8-139">Sınıf ve modül üyesi sabitleri (herhangi bir yordam dışında), özel erişim için varsayılan olarak, üye sabitlerinin varsayılan olarak ortak erişimine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="07bf8-139">Class and module member constants (outside any procedure) default to private access, and structure member constants default to public access.</span></span> <span data-ttu-id="07bf8-140">Erişim değiştiricilerini kullanarak erişim düzeylerini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07bf8-140">You can adjust their access levels with the access modifiers.</span></span>

## <a name="rules"></a><span data-ttu-id="07bf8-141">Kurallar</span><span class="sxs-lookup"><span data-stu-id="07bf8-141">Rules</span></span>

- <span data-ttu-id="07bf8-142">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="07bf8-142">**Declaration Context.**</span></span> <span data-ttu-id="07bf8-143">Modül düzeyinde belirtilen bir sabit, herhangi bir yordamın dışında, bir *üye sabiti*; Onu bildiren sınıf, yapı veya modülün bir üyesidir.</span><span class="sxs-lookup"><span data-stu-id="07bf8-143">A constant declared at module level, outside any procedure, is a *member constant*; it is a member of the class, structure, or module that declares it.</span></span>

  <span data-ttu-id="07bf8-144">Yordam düzeyinde belirtilen bir sabit, yerel bir *sabittir*; Bu, onu bildiren yordamın veya bloğun yereldir.</span><span class="sxs-lookup"><span data-stu-id="07bf8-144">A constant declared at procedure level is a *local constant*; it is local to the procedure or block that declares it.</span></span>

- <span data-ttu-id="07bf8-145">**Özelliklerine.**</span><span class="sxs-lookup"><span data-stu-id="07bf8-145">**Attributes.**</span></span> <span data-ttu-id="07bf8-146">Öznitelikleri yerel sabitlere değil yalnızca üye sabitlerine uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07bf8-146">You can apply attributes only to member constants, not to local constants.</span></span> <span data-ttu-id="07bf8-147">Bir öznitelik, bilgileri derlemenin meta verilerine katkıda bulunur ve bu, yerel sabitler gibi geçici depolama için anlamlı değildir.</span><span class="sxs-lookup"><span data-stu-id="07bf8-147">An attribute contributes information to the assembly's metadata, which is not meaningful for temporary storage such as local constants.</span></span>

- <span data-ttu-id="07bf8-148">**İlerine.**</span><span class="sxs-lookup"><span data-stu-id="07bf8-148">**Modifiers.**</span></span> <span data-ttu-id="07bf8-149">Varsayılan olarak, tüm sabitler `Shared` , `Static` ve ' dir `ReadOnly` .</span><span class="sxs-lookup"><span data-stu-id="07bf8-149">By default, all constants are `Shared`, `Static`, and `ReadOnly`.</span></span> <span data-ttu-id="07bf8-150">Bir sabit bildirirken bu anahtar sözcüklerden hiçbirini kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="07bf8-150">You cannot use any of these keywords when declaring a constant.</span></span>

  <span data-ttu-id="07bf8-151">Yordam düzeyinde, `Shadows` Yerel sabitleri bildirmek için veya herhangi bir erişim değiştiricilerini kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="07bf8-151">At procedure level, you cannot use `Shadows` or any access modifiers to declare local constants.</span></span>

- <span data-ttu-id="07bf8-152">**Birden çok sabit.**</span><span class="sxs-lookup"><span data-stu-id="07bf8-152">**Multiple Constants.**</span></span> <span data-ttu-id="07bf8-153">Aynı bildirim ifadesinde, her birinin bölümünü belirterek, birkaç sabit belirtebilirsiniz `constantname` .</span><span class="sxs-lookup"><span data-stu-id="07bf8-153">You can declare several constants in the same declaration statement, specifying the `constantname` part for each one.</span></span> <span data-ttu-id="07bf8-154">Birden çok sabit virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="07bf8-154">Multiple constants are separated by commas.</span></span>

## <a name="data-type-rules"></a><span data-ttu-id="07bf8-155">Veri türü kuralları</span><span class="sxs-lookup"><span data-stu-id="07bf8-155">Data Type Rules</span></span>

- <span data-ttu-id="07bf8-156">**Veri türleri.**</span><span class="sxs-lookup"><span data-stu-id="07bf8-156">**Data Types.**</span></span> <span data-ttu-id="07bf8-157">`Const`İfade, bir değişkenin veri türünü bildirebilirler.</span><span class="sxs-lookup"><span data-stu-id="07bf8-157">The `Const` statement can declare the data type of a variable.</span></span> <span data-ttu-id="07bf8-158">Herhangi bir veri türü veya bir numaralandırma adı belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07bf8-158">You can specify any data type or the name of an enumeration.</span></span>

- <span data-ttu-id="07bf8-159">**Varsayılan tür.**</span><span class="sxs-lookup"><span data-stu-id="07bf8-159">**Default Type.**</span></span> <span data-ttu-id="07bf8-160">Belirtmezseniz `datatype` , sabit, veri türünü alır `initializer` .</span><span class="sxs-lookup"><span data-stu-id="07bf8-160">If you do not specify `datatype`, the constant takes the data type of `initializer`.</span></span> <span data-ttu-id="07bf8-161">Hem hem de belirtirseniz `datatype` `initializer` , veri türü `initializer` öğesine dönüştürülebilir olmalıdır `datatype` .</span><span class="sxs-lookup"><span data-stu-id="07bf8-161">If you specify both `datatype` and `initializer`, the data type of `initializer` must be convertible to `datatype`.</span></span> <span data-ttu-id="07bf8-162">Ne yoksa `datatype` ne de `initializer` yoksa, veri türü varsayılan olarak olur `Object` .</span><span class="sxs-lookup"><span data-stu-id="07bf8-162">If neither `datatype` nor `initializer` is present, the data type defaults to `Object`.</span></span>

- <span data-ttu-id="07bf8-163">**Farklı türler.**</span><span class="sxs-lookup"><span data-stu-id="07bf8-163">**Different Types.**</span></span> <span data-ttu-id="07bf8-164">Bildirdiğiniz her değişken için ayrı bir yan tümce kullanarak, farklı sabitler için farklı veri türleri belirtebilirsiniz `As` .</span><span class="sxs-lookup"><span data-stu-id="07bf8-164">You can specify different data types for different constants by using a separate `As` clause for each variable you declare.</span></span> <span data-ttu-id="07bf8-165">Ancak, ortak bir yan tümce kullanarak aynı türde olan birkaç sabiti bildiremezsiniz `As` .</span><span class="sxs-lookup"><span data-stu-id="07bf8-165">However, you cannot declare several constants to be of the same type by using a common `As` clause.</span></span>

- <span data-ttu-id="07bf8-166">**Başlatılmasında.**</span><span class="sxs-lookup"><span data-stu-id="07bf8-166">**Initialization.**</span></span> <span data-ttu-id="07bf8-167">' De her bir sabit değeri başlatmalısınız `constantlist` .</span><span class="sxs-lookup"><span data-stu-id="07bf8-167">You must initialize the value of every constant in `constantlist`.</span></span> <span data-ttu-id="07bf8-168">`initializer`Sabitine atanacak bir ifade sağlamak için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="07bf8-168">You use `initializer` to supply an expression to be assigned to the constant.</span></span> <span data-ttu-id="07bf8-169">İfade, herhangi bir sabit değer, önceden tanımlanmış diğer sabitler ve önceden tanımlanmış sabit listesi üyeleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="07bf8-169">The expression can be any combination of literals, other constants that are already defined, and enumeration members that are already defined.</span></span> <span data-ttu-id="07bf8-170">Bu tür öğeleri birleştirmek için aritmetik ve mantıksal işleçler kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07bf8-170">You can use arithmetic and logical operators to combine such elements.</span></span>

  <span data-ttu-id="07bf8-171">İçindeki değişkenleri veya işlevleri kullanamazsınız `initializer` .</span><span class="sxs-lookup"><span data-stu-id="07bf8-171">You cannot use variables or functions in `initializer`.</span></span> <span data-ttu-id="07bf8-172">Ancak, ve gibi dönüştürme anahtar sözcüklerini kullanabilirsiniz `CByte` `CShort` .</span><span class="sxs-lookup"><span data-stu-id="07bf8-172">However, you can use conversion keywords such as `CByte` and `CShort`.</span></span> <span data-ttu-id="07bf8-173">`AscW` `String` `Char` Derleme zamanında değerlendirilebileceğinizden, bu değeri bir sabit veya bağımsız değişkenle birlikte çağırırsanız de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07bf8-173">You can also use `AscW` if you call it with a constant `String` or `Char` argument, since that can be evaluated at compile time.</span></span>

## <a name="behavior"></a><span data-ttu-id="07bf8-174">Davranış</span><span class="sxs-lookup"><span data-stu-id="07bf8-174">Behavior</span></span>

- <span data-ttu-id="07bf8-175">**Kapsam.**</span><span class="sxs-lookup"><span data-stu-id="07bf8-175">**Scope.**</span></span> <span data-ttu-id="07bf8-176">Yerel sabitler yalnızca kendi yordamının veya bloğunun içinden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="07bf8-176">Local constants are accessible only from within their procedure or block.</span></span> <span data-ttu-id="07bf8-177">Üye sabitlerine, sınıfları, yapısı veya modülü içinde herhangi bir yerden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="07bf8-177">Member constants are accessible from anywhere within their class, structure, or module.</span></span>

- <span data-ttu-id="07bf8-178">**Yeter.**</span><span class="sxs-lookup"><span data-stu-id="07bf8-178">**Qualification.**</span></span> <span data-ttu-id="07bf8-179">Bir sınıf, yapı veya modülün dışındaki kodun, bir üye sabitinin adını bu sınıf, yapı veya modülün adı ile nitelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="07bf8-179">Code outside a class, structure, or module must qualify a member constant's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="07bf8-180">Bir yordamın veya bloğun dışındaki kod, bu yordam veya blok içindeki herhangi bir yerel sabitlere başvuramaz.</span><span class="sxs-lookup"><span data-stu-id="07bf8-180">Code outside a procedure or block cannot refer to any local constants within that procedure or block.</span></span>

## <a name="example"></a><span data-ttu-id="07bf8-181">Örnek</span><span class="sxs-lookup"><span data-stu-id="07bf8-181">Example</span></span>

<span data-ttu-id="07bf8-182">Aşağıdaki örnek, `Const` sabit değer değerlerinin yerine kullanılacak sabitleri bildirmek için bildirimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="07bf8-182">The following example uses the `Const` statement to declare constants for use in place of literal values.</span></span>

[!code-vb[VbVbalrStatements#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#13)]

## <a name="example"></a><span data-ttu-id="07bf8-183">Örnek</span><span class="sxs-lookup"><span data-stu-id="07bf8-183">Example</span></span>

<span data-ttu-id="07bf8-184">Veri türü ile bir sabit tanımlarsanız `Object` , Visual Basic derleyici bunun yerine öğesinin türünü sağlar `initializer` `Object` .</span><span class="sxs-lookup"><span data-stu-id="07bf8-184">If you define a constant with data type `Object`, the Visual Basic compiler gives it the type of `initializer`, instead of `Object`.</span></span> <span data-ttu-id="07bf8-185">Aşağıdaki örnekte, sabit, `naturalLogBase` çalışma zamanı türüne sahiptir `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="07bf8-185">In the following example, the constant `naturalLogBase` has the run-time type `Decimal`.</span></span>

[!code-vb[VbVbalrStatements#87](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#87)]

<span data-ttu-id="07bf8-186">Önceki örnekte,, <xref:System.Type.ToString%2A> <xref:System.Type> ' a dönüştürülemediğinden, [GetType işlecinin](../operators/gettype-operator.md)döndürdüğü nesne üzerinde yöntemi kullanılmaktadır <xref:System.Type> `String` `CStr` .</span><span class="sxs-lookup"><span data-stu-id="07bf8-186">The preceding example uses the <xref:System.Type.ToString%2A> method on the <xref:System.Type> object returned by the [GetType Operator](../operators/gettype-operator.md), because <xref:System.Type> cannot be converted to `String` using `CStr`.</span></span>

## <a name="see-also"></a><span data-ttu-id="07bf8-187">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07bf8-187">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [<span data-ttu-id="07bf8-188">Enum Deyimi</span><span class="sxs-lookup"><span data-stu-id="07bf8-188">Enum Statement</span></span>](enum-statement.md)
- [<span data-ttu-id="07bf8-189">#Const Yönergesi</span><span class="sxs-lookup"><span data-stu-id="07bf8-189">#Const Directive</span></span>](../directives/const-directive.md)
- [<span data-ttu-id="07bf8-190">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="07bf8-190">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="07bf8-191">ReDim Deyimi</span><span class="sxs-lookup"><span data-stu-id="07bf8-191">ReDim Statement</span></span>](redim-statement.md)
- [<span data-ttu-id="07bf8-192">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="07bf8-192">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="07bf8-193">Sabitler ve numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="07bf8-193">Constants and Enumerations</span></span>](../../programming-guide/language-features/constants-enums/index.md)
- [<span data-ttu-id="07bf8-194">Sabitler ve numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="07bf8-194">Constants and Enumerations</span></span>](../constants-and-enumerations.md)
- [<span data-ttu-id="07bf8-195">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="07bf8-195">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
