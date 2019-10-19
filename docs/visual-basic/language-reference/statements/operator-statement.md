---
title: Operator ekstresi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.operator
helpviewer_keywords:
- operators [Visual Basic]
- procedures [Visual Basic], operator
- Narrowing keyword [Visual Basic], conversion operators
- Visual Basic code, operators
- Widening keyword [Visual Basic], conversion operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
- Operator statement [Visual Basic]
- CType function [Visual Basic], Operator statement
ms.assetid: b12ec4af-1ad7-4a17-865b-c5ee96320ae5
ms.openlocfilehash: c4fae40992fa665121aff637ae427ef0cafbf547
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582377"
---
# <a name="operator-statement"></a><span data-ttu-id="387f1-102">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="387f1-102">Operator Statement</span></span>

<span data-ttu-id="387f1-103">Bir sınıf veya yapıda operatör yordamını tanımlayan işleç sembolünü, işlenenleri ve kodu bildirir.</span><span class="sxs-lookup"><span data-stu-id="387f1-103">Declares the operator symbol, operands, and code that define an operator procedure on a class or structure.</span></span>

## <a name="syntax"></a><span data-ttu-id="387f1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="387f1-104">Syntax</span></span>

```vb
[ <attrlist> ] Public [ Overloads ] Shared [ Shadows ] [ Widening | Narrowing ]
Operator operatorsymbol ( operand1 [, operand2 ]) [ As [ <attrlist> ] type ]
    [ statements ]
    [ statements ]
    Return returnvalue
    [ statements ]
End Operator
```

## <a name="parts"></a><span data-ttu-id="387f1-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="387f1-105">Parts</span></span>

`attrlist`  
<span data-ttu-id="387f1-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="387f1-106">Optional.</span></span> <span data-ttu-id="387f1-107">Bkz. [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="387f1-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>

`Public`  
<span data-ttu-id="387f1-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="387f1-108">Required.</span></span> <span data-ttu-id="387f1-109">Bu işleç yordamının [ortak](../../../visual-basic/language-reference/modifiers/public.md) erişime sahip olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="387f1-109">Indicates that this operator procedure has [Public](../../../visual-basic/language-reference/modifiers/public.md) access.</span></span>

`Overloads`  
<span data-ttu-id="387f1-110">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="387f1-110">Optional.</span></span> <span data-ttu-id="387f1-111">Bkz. [aşırı yüklemeler](../../../visual-basic/language-reference/modifiers/overloads.md).</span><span class="sxs-lookup"><span data-stu-id="387f1-111">See [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md).</span></span>

`Shared`  
<span data-ttu-id="387f1-112">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="387f1-112">Required.</span></span> <span data-ttu-id="387f1-113">Bu işleç yordamının [paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md) bir yordam olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="387f1-113">Indicates that this operator procedure is a [Shared](../../../visual-basic/language-reference/modifiers/shared.md) procedure.</span></span>

`Shadows`  
<span data-ttu-id="387f1-114">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="387f1-114">Optional.</span></span> <span data-ttu-id="387f1-115">Bkz. [gölgeler](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="387f1-115">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>

`Widening`  
<span data-ttu-id="387f1-116">@No__t_0 belirtmediğiniz takdirde bir dönüştürme işleci için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="387f1-116">Required for a conversion operator unless you specify `Narrowing`.</span></span> <span data-ttu-id="387f1-117">Bu işleç yordamının bir [genişletme](../../../visual-basic/language-reference/modifiers/widening.md) dönüşümünü tanımladığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="387f1-117">Indicates that this operator procedure defines a [Widening](../../../visual-basic/language-reference/modifiers/widening.md) conversion.</span></span> <span data-ttu-id="387f1-118">Bu Yardım sayfasında "genişletme ve daraltma dönüşümleri" başlığına bakın.</span><span class="sxs-lookup"><span data-stu-id="387f1-118">See "Widening and Narrowing Conversions" on this Help page.</span></span>

`Narrowing`  
<span data-ttu-id="387f1-119">@No__t_0 belirtmediğiniz takdirde bir dönüştürme işleci için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="387f1-119">Required for a conversion operator unless you specify `Widening`.</span></span> <span data-ttu-id="387f1-120">Bu işleç yordamının bir [daraltma](../../../visual-basic/language-reference/modifiers/narrowing.md) dönüşümünü tanımladığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="387f1-120">Indicates that this operator procedure defines a [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md) conversion.</span></span> <span data-ttu-id="387f1-121">Bu Yardım sayfasında "genişletme ve daraltma dönüşümleri" başlığına bakın.</span><span class="sxs-lookup"><span data-stu-id="387f1-121">See "Widening and Narrowing Conversions" on this Help page.</span></span>

`operatorsymbol`  
<span data-ttu-id="387f1-122">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="387f1-122">Required.</span></span> <span data-ttu-id="387f1-123">Bu işleç yordamının tanımladığı işlecin simgesi veya tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="387f1-123">The symbol or identifier of the operator that this operator procedure defines.</span></span>

`operand1`  
<span data-ttu-id="387f1-124">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="387f1-124">Required.</span></span> <span data-ttu-id="387f1-125">Birli işlecin tek işleneninin adı ve türü (dönüştürme işleci dahil) veya bir ikili işlecinin sol işleneni.</span><span class="sxs-lookup"><span data-stu-id="387f1-125">The name and type of the single operand of a unary operator (including a conversion operator) or the left operand of a binary operator.</span></span>

`operand2`  
<span data-ttu-id="387f1-126">İkili işleçler için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="387f1-126">Required for binary operators.</span></span> <span data-ttu-id="387f1-127">Bir ikili işlecinin sağ işleneninin adı ve türü.</span><span class="sxs-lookup"><span data-stu-id="387f1-127">The name and type of the right operand of a binary operator.</span></span>

<span data-ttu-id="387f1-128">`operand1` ve `operand2` aşağıdaki söz dizimi ve bölümlere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="387f1-128">`operand1` and `operand2` have the following syntax and parts:</span></span>

`[ ByVal ] operandname [ As operandtype ]`

|<span data-ttu-id="387f1-129">Bölümüyle</span><span class="sxs-lookup"><span data-stu-id="387f1-129">Part</span></span>|<span data-ttu-id="387f1-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="387f1-130">Description</span></span>|
|----------|-----------------|
|`ByVal`|<span data-ttu-id="387f1-131">İsteğe bağlı, ancak geçen mekanizmanın [ByVal](../../../visual-basic/language-reference/modifiers/byval.md)olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="387f1-131">Optional, but the passing mechanism must be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span></span>|
|`operandname`|<span data-ttu-id="387f1-132">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="387f1-132">Required.</span></span> <span data-ttu-id="387f1-133">Bu işleneni temsil eden değişkenin adı.</span><span class="sxs-lookup"><span data-stu-id="387f1-133">Name of the variable representing this operand.</span></span> <span data-ttu-id="387f1-134">Bkz. [tanımlanmış öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="387f1-134">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|
|`operandtype`|<span data-ttu-id="387f1-135">@No__t_0 `On` olmadığı müddetçe isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="387f1-135">Optional unless `Option Strict` is `On`.</span></span> <span data-ttu-id="387f1-136">Bu işlenenin veri türü.</span><span class="sxs-lookup"><span data-stu-id="387f1-136">Data type of this operand.</span></span>|

`type`  
<span data-ttu-id="387f1-137">@No__t_0 `On` olmadığı müddetçe isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="387f1-137">Optional unless `Option Strict` is `On`.</span></span> <span data-ttu-id="387f1-138">İşleç yordamının döndürdüğü değerin veri türü.</span><span class="sxs-lookup"><span data-stu-id="387f1-138">Data type of the value the operator procedure returns.</span></span>

`statements`  
<span data-ttu-id="387f1-139">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="387f1-139">Optional.</span></span> <span data-ttu-id="387f1-140">İşleç yordamının çalıştığı deyimler bloğu.</span><span class="sxs-lookup"><span data-stu-id="387f1-140">Block of statements that the operator procedure runs.</span></span>

`returnvalue`  
<span data-ttu-id="387f1-141">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="387f1-141">Required.</span></span> <span data-ttu-id="387f1-142">İşleç yordamının çağırma koduna döndürdüğü değer.</span><span class="sxs-lookup"><span data-stu-id="387f1-142">The value that the operator procedure returns to the calling code.</span></span>

<span data-ttu-id="387f1-143">`End``Operator`</span><span class="sxs-lookup"><span data-stu-id="387f1-143">`End` `Operator`</span></span>  
<span data-ttu-id="387f1-144">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="387f1-144">Required.</span></span> <span data-ttu-id="387f1-145">Bu işleç yordamının tanımını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="387f1-145">Terminates the definition of this operator procedure.</span></span>

## <a name="remarks"></a><span data-ttu-id="387f1-146">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="387f1-146">Remarks</span></span>

<span data-ttu-id="387f1-147">Yalnızca bir sınıf veya yapıda `Operator` kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="387f1-147">You can use `Operator` only in a class or structure.</span></span> <span data-ttu-id="387f1-148">Bu, bir işlecin *bildirim bağlamının* kaynak dosya, ad alanı, modül, arabirim, yordam veya blok olamayacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="387f1-148">This means the *declaration context* for an operator cannot be a source file, namespace, module, interface, procedure, or block.</span></span> <span data-ttu-id="387f1-149">Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="387f1-149">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="387f1-150">Tüm işleçler `Public Shared` olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="387f1-150">All operators must be `Public Shared`.</span></span> <span data-ttu-id="387f1-151">Her iki işlenen için `ByRef`, `Optional` veya `ParamArray` belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="387f1-151">You cannot specify `ByRef`, `Optional`, or `ParamArray` for either operand.</span></span>

<span data-ttu-id="387f1-152">Dönüş değerini tutmak için işleç sembolünü veya tanımlayıcıyı kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="387f1-152">You cannot use the operator symbol or identifier to hold a return value.</span></span> <span data-ttu-id="387f1-153">@No__t_0 ifadesini kullanmanız ve bir değer belirtmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="387f1-153">You must use the `Return` statement, and it must specify a value.</span></span> <span data-ttu-id="387f1-154">Herhangi bir sayıda `Return` deyimi yordamda herhangi bir yerde görünebilir.</span><span class="sxs-lookup"><span data-stu-id="387f1-154">Any number of `Return` statements can appear anywhere in the procedure.</span></span>

<span data-ttu-id="387f1-155">Bir işlecin bu şekilde tanımlanması, `Overloads` anahtar sözcüğünü kullanıp kullanmayacağınızı, *işleç aşırı yüklemesi*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="387f1-155">Defining an operator in this way is called *operator overloading*, whether or not you use the `Overloads` keyword.</span></span> <span data-ttu-id="387f1-156">Aşağıdaki tabloda, tanımlayabilmeniz için kullanabileceğiniz işleçler listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="387f1-156">The following table lists the operators you can define.</span></span>

|<span data-ttu-id="387f1-157">Tür</span><span class="sxs-lookup"><span data-stu-id="387f1-157">Type</span></span>|<span data-ttu-id="387f1-158">İşleçler</span><span class="sxs-lookup"><span data-stu-id="387f1-158">Operators</span></span>|
|----------|---------------|
|<span data-ttu-id="387f1-159">Li</span><span class="sxs-lookup"><span data-stu-id="387f1-159">Unary</span></span>|<span data-ttu-id="387f1-160">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span><span class="sxs-lookup"><span data-stu-id="387f1-160">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span></span>|
|<span data-ttu-id="387f1-161">İkili</span><span class="sxs-lookup"><span data-stu-id="387f1-161">Binary</span></span>|<span data-ttu-id="387f1-162">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, 0, 1, 2, 3, 4, 5 , 6, 7, 8, 9</span><span class="sxs-lookup"><span data-stu-id="387f1-162">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span></span>|
|<span data-ttu-id="387f1-163">Dönüştürme (birli)</span><span class="sxs-lookup"><span data-stu-id="387f1-163">Conversion (unary)</span></span>|`CType`|

<span data-ttu-id="387f1-164">İkili listedeki `=` işlecinin, atama operatörü değil karşılaştırma operatörü olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="387f1-164">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>

<span data-ttu-id="387f1-165">@No__t_0 tanımladığınızda, `Widening` veya `Narrowing` belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="387f1-165">When you define `CType`, you must specify either `Widening` or `Narrowing`.</span></span>

## <a name="matched-pairs"></a><span data-ttu-id="387f1-166">Eşleşen çiftler</span><span class="sxs-lookup"><span data-stu-id="387f1-166">Matched Pairs</span></span>

<span data-ttu-id="387f1-167">Belirli işleçleri eşleşen çiftler olarak tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="387f1-167">You must define certain operators as matched pairs.</span></span> <span data-ttu-id="387f1-168">Böyle bir çiftin işlecini tanımlarsanız, diğerini de tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="387f1-168">If you define either operator of such a pair, you must define the other as well.</span></span> <span data-ttu-id="387f1-169">Eşleşen çiftler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="387f1-169">The matched pairs are the following:</span></span>

- <span data-ttu-id="387f1-170">`=` ve `<>`</span><span class="sxs-lookup"><span data-stu-id="387f1-170">`=` and `<>`</span></span>

- <span data-ttu-id="387f1-171">`>` ve `<`</span><span class="sxs-lookup"><span data-stu-id="387f1-171">`>` and `<`</span></span>

- <span data-ttu-id="387f1-172">`>=` ve `<=`</span><span class="sxs-lookup"><span data-stu-id="387f1-172">`>=` and `<=`</span></span>

- <span data-ttu-id="387f1-173">`IsTrue` ve `IsFalse`</span><span class="sxs-lookup"><span data-stu-id="387f1-173">`IsTrue` and `IsFalse`</span></span>

## <a name="data-type-restrictions"></a><span data-ttu-id="387f1-174">Veri türü kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="387f1-174">Data Type Restrictions</span></span>

<span data-ttu-id="387f1-175">Tanımladığınız her operatör, üzerinde tanımladığınız sınıf veya yapıyı içermelidir.</span><span class="sxs-lookup"><span data-stu-id="387f1-175">Every operator you define must involve the class or structure on which you define it.</span></span> <span data-ttu-id="387f1-176">Bu, sınıfın veya yapının aşağıdakilerin veri türü olarak görünmesi gerektiği anlamına gelir:</span><span class="sxs-lookup"><span data-stu-id="387f1-176">This means that the class or structure must appear as the data type of the following:</span></span>

- <span data-ttu-id="387f1-177">Birli işlecin işleneni.</span><span class="sxs-lookup"><span data-stu-id="387f1-177">The operand of a unary operator.</span></span>

- <span data-ttu-id="387f1-178">Bir ikili işlecinin işlenenlerinden en az biri.</span><span class="sxs-lookup"><span data-stu-id="387f1-178">At least one of the operands of a binary operator.</span></span>

- <span data-ttu-id="387f1-179">Bir dönüştürme işlecinin işleneni ya da dönüş türü.</span><span class="sxs-lookup"><span data-stu-id="387f1-179">Either the operand or the return type of a conversion operator.</span></span>

 <span data-ttu-id="387f1-180">Bazı işleçler, aşağıdaki gibi ek veri türü kısıtlamalarına sahiptir:</span><span class="sxs-lookup"><span data-stu-id="387f1-180">Certain operators have additional data type restrictions, as follows:</span></span>

- <span data-ttu-id="387f1-181">@No__t_0 ve `IsFalse` işleçlerini tanımlarsanız, her ikisi de `Boolean` türünü döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="387f1-181">If you define the `IsTrue` and `IsFalse` operators, they must both return the `Boolean` type.</span></span>

- <span data-ttu-id="387f1-182">@No__t_0 ve `>>` işleçlerini tanımlarsanız, her ikisi de `operand2` `operandtype` için `Integer` türünü belirtmelidir.</span><span class="sxs-lookup"><span data-stu-id="387f1-182">If you define the `<<` and `>>` operators, they must both specify the `Integer` type for the `operandtype` of `operand2`.</span></span>

<span data-ttu-id="387f1-183">Dönüş türünün, her iki işlenenin türüne karşılık gelmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="387f1-183">The return type does not have to correspond to the type of either operand.</span></span> <span data-ttu-id="387f1-184">Örneğin, `=` veya `<>` gibi bir karşılaştırma işleci, hiçbir işlenen `Boolean` bile `Boolean` döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="387f1-184">For example, a comparison operator such as `=` or `<>` can return `Boolean` even if neither operand is `Boolean`.</span></span>

## <a name="logical-and-bitwise-operators"></a><span data-ttu-id="387f1-185">Mantıksal ve Bit Düzeyinde İşleçler</span><span class="sxs-lookup"><span data-stu-id="387f1-185">Logical and Bitwise Operators</span></span>

<span data-ttu-id="387f1-186">@No__t_0, `Or`, `Not` ve `Xor` işleçleri Visual Basic mantıksal veya bit tabanlı işlemler gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="387f1-186">The `And`, `Or`, `Not`, and `Xor` operators can perform either logical or bitwise operations in Visual Basic.</span></span> <span data-ttu-id="387f1-187">Ancak, bu işleçlerden birini bir sınıf veya yapıda tanımlarsanız, yalnızca bit düzeyinde işlemini tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="387f1-187">However, if you define one of these operators on a class or structure, you can define only its bitwise operation.</span></span>

<span data-ttu-id="387f1-188">@No__t_0 işlecini doğrudan bir `Operator` ifadesiyle tanımlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="387f1-188">You cannot define the `AndAlso` operator directly with an `Operator` statement.</span></span> <span data-ttu-id="387f1-189">Ancak, aşağıdaki koşulları karşıladıysanız `AndAlso` kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="387f1-189">However, you can use `AndAlso` if you have fulfilled the following conditions:</span></span>

- <span data-ttu-id="387f1-190">@No__t_1 için kullanmak istediğiniz aynı işlenen türlerinde `And` tanımladınız.</span><span class="sxs-lookup"><span data-stu-id="387f1-190">You have defined `And` on the same operand types you want to use for `AndAlso`.</span></span>

- <span data-ttu-id="387f1-191">@No__t_0 tanımınız, tanımladığınız sınıf veya yapı ile aynı türü döndürür.</span><span class="sxs-lookup"><span data-stu-id="387f1-191">Your definition of `And` returns the same type as the class or structure on which you have defined it.</span></span>

- <span data-ttu-id="387f1-192">@No__t_1 tanımladığınız sınıf veya yapıda `IsFalse` işlecini tanımladınız.</span><span class="sxs-lookup"><span data-stu-id="387f1-192">You have defined the `IsFalse` operator on the class or structure on which you have defined `And`.</span></span>

<span data-ttu-id="387f1-193">Benzer şekilde, aynı işlenenler üzerinde `Or` tanımladıysanız, sınıf veya yapının dönüş türü ile ve sınıf veya yapı üzerinde `IsTrue` tanımlamış olmanız durumunda `OrElse` kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="387f1-193">Similarly, you can use `OrElse` if you have defined `Or` on the same operands, with the return type of the class or structure, and you have defined `IsTrue` on the class or structure.</span></span>

## <a name="widening-and-narrowing-conversions"></a><span data-ttu-id="387f1-194">Genişletme ve Daraltma Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="387f1-194">Widening and Narrowing Conversions</span></span>

<span data-ttu-id="387f1-195">Her *zaman* çalışma zamanında bir daraltma dönüştürmesi başarısız olsa da, bir *daraltma* dönüştürmesi çalışma zamanında başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="387f1-195">A *widening conversion* always succeeds at run time, while a *narrowing conversion* can fail at run time.</span></span> <span data-ttu-id="387f1-196">Daha fazla bilgi için bkz. [genişletme ve daraltma dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="387f1-196">For more information, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>

<span data-ttu-id="387f1-197">@No__t_0 bir dönüştürme yordamı bildirirseniz, yordam kodunuzun herhangi bir başarısızlık üretmemelidir.</span><span class="sxs-lookup"><span data-stu-id="387f1-197">If you declare a conversion procedure to be `Widening`, your procedure code must not generate any failures.</span></span> <span data-ttu-id="387f1-198">Bu, aşağıdakiler anlamına gelir:</span><span class="sxs-lookup"><span data-stu-id="387f1-198">This means the following:</span></span>

- <span data-ttu-id="387f1-199">Her zaman `type` türünde geçerli bir değer döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="387f1-199">It must always return a valid value of type `type`.</span></span>

- <span data-ttu-id="387f1-200">Tüm olası özel durumları ve diğer hata koşullarını ele almalıdır.</span><span class="sxs-lookup"><span data-stu-id="387f1-200">It must handle all possible exceptions and other error conditions.</span></span>

- <span data-ttu-id="387f1-201">Çağrı yaptığı tüm yordamlardan hata getirlerinin işlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="387f1-201">It must handle any error returns from any procedures it calls.</span></span>

<span data-ttu-id="387f1-202">Bir dönüştürme yordamının başarılı bir şekilde başarısız olabileceği veya işlenmemiş bir özel duruma neden olabileceği durumlarda, `Narrowing` olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="387f1-202">If there is any possibility that a conversion procedure might not succeed, or that it might cause an unhandled exception, you must declare it to be `Narrowing`.</span></span>

## <a name="example"></a><span data-ttu-id="387f1-203">Örnek</span><span class="sxs-lookup"><span data-stu-id="387f1-203">Example</span></span>

<span data-ttu-id="387f1-204">Aşağıdaki kod örneği, `And`, `Or`, `IsFalse` ve `IsTrue` işleçleri için işleç yordamları içeren bir yapının anahattını tanımlamak için `Operator` ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="387f1-204">The following code example uses the `Operator` statement to define the outline of a structure that includes operator procedures for the `And`, `Or`, `IsFalse`, and `IsTrue` operators.</span></span> <span data-ttu-id="387f1-205">`And` ve `Or` her biri, `abc` türü ve dönüş türü `abc` iki işlenen alır.</span><span class="sxs-lookup"><span data-stu-id="387f1-205">`And` and `Or` each take two operands of type `abc` and return type `abc`.</span></span> <span data-ttu-id="387f1-206">`IsFalse` ve `IsTrue` her biri `abc` türünde tek bir işlenen alır ve `Boolean` döndürür.</span><span class="sxs-lookup"><span data-stu-id="387f1-206">`IsFalse` and `IsTrue` each take a single operand of type `abc` and return `Boolean`.</span></span> <span data-ttu-id="387f1-207">Bu tanımlar çağıran kodun, `abc` türündeki işlenenleri `And`, `AndAlso`, `Or` ve `OrElse` kullanmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="387f1-207">These definitions allow the calling code to use `And`, `AndAlso`, `Or`, and `OrElse` with operands of type `abc`.</span></span>

[!code-vb[VbVbalrStatements#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#44)]

## <a name="see-also"></a><span data-ttu-id="387f1-208">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="387f1-208">See also</span></span>

- [<span data-ttu-id="387f1-209">IsFalse İşleci</span><span class="sxs-lookup"><span data-stu-id="387f1-209">IsFalse Operator</span></span>](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [<span data-ttu-id="387f1-210">IsTrue İşleci</span><span class="sxs-lookup"><span data-stu-id="387f1-210">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [<span data-ttu-id="387f1-211">Widening</span><span class="sxs-lookup"><span data-stu-id="387f1-211">Widening</span></span>](../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="387f1-212">Narrowing</span><span class="sxs-lookup"><span data-stu-id="387f1-212">Narrowing</span></span>](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="387f1-213">Genişletme ve Daraltma Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="387f1-213">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="387f1-214">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="387f1-214">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="387f1-215">Nasıl yapılır: İşleç Tanımlama</span><span class="sxs-lookup"><span data-stu-id="387f1-215">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="387f1-216">Nasıl yapılır: Dönüştürme İşleci Tanımlama</span><span class="sxs-lookup"><span data-stu-id="387f1-216">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="387f1-217">Nasıl yapılır: Bir İşleç Yordamı Çağırma</span><span class="sxs-lookup"><span data-stu-id="387f1-217">How to: Call an Operator Procedure</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="387f1-218">Nasıl yapılır: İşleçleri Tanımlayan Bir Sınıf Kullanma</span><span class="sxs-lookup"><span data-stu-id="387f1-218">How to: Use a Class that Defines Operators</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)
