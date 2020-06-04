---
title: Operator Deyimi
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
ms.openlocfilehash: f9e6ffe5a49715592399321ab471d73826e05d8e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404401"
---
# <a name="operator-statement"></a><span data-ttu-id="32412-102">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="32412-102">Operator Statement</span></span>

<span data-ttu-id="32412-103">Bir sınıf veya yapıda operatör yordamını tanımlayan işleç sembolünü, işlenenleri ve kodu bildirir.</span><span class="sxs-lookup"><span data-stu-id="32412-103">Declares the operator symbol, operands, and code that define an operator procedure on a class or structure.</span></span>

## <a name="syntax"></a><span data-ttu-id="32412-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="32412-104">Syntax</span></span>

```vb
[ <attrlist> ] Public [ Overloads ] Shared [ Shadows ] [ Widening | Narrowing ]
Operator operatorsymbol ( operand1 [, operand2 ]) [ As [ <attrlist> ] type ]
    [ statements ]
    [ statements ]
    Return returnvalue
    [ statements ]
End Operator
```

## <a name="parts"></a><span data-ttu-id="32412-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="32412-105">Parts</span></span>

`attrlist`  
<span data-ttu-id="32412-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="32412-106">Optional.</span></span> <span data-ttu-id="32412-107">Bkz. [öznitelik listesi](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="32412-107">See [Attribute List](attribute-list.md).</span></span>

`Public`  
<span data-ttu-id="32412-108">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="32412-108">Required.</span></span> <span data-ttu-id="32412-109">Bu işleç yordamının [ortak](../modifiers/public.md) erişime sahip olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="32412-109">Indicates that this operator procedure has [Public](../modifiers/public.md) access.</span></span>

`Overloads`  
<span data-ttu-id="32412-110">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="32412-110">Optional.</span></span> <span data-ttu-id="32412-111">Bkz. [aşırı yüklemeler](../modifiers/overloads.md).</span><span class="sxs-lookup"><span data-stu-id="32412-111">See [Overloads](../modifiers/overloads.md).</span></span>

`Shared`  
<span data-ttu-id="32412-112">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="32412-112">Required.</span></span> <span data-ttu-id="32412-113">Bu işleç yordamının [paylaşılan](../modifiers/shared.md) bir yordam olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="32412-113">Indicates that this operator procedure is a [Shared](../modifiers/shared.md) procedure.</span></span>

`Shadows`  
<span data-ttu-id="32412-114">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="32412-114">Optional.</span></span> <span data-ttu-id="32412-115">Bkz. [gölgeler](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="32412-115">See [Shadows](../modifiers/shadows.md).</span></span>

`Widening`  
<span data-ttu-id="32412-116">Belirtmediğiniz takdirde bir dönüştürme işleci için gereklidir `Narrowing` .</span><span class="sxs-lookup"><span data-stu-id="32412-116">Required for a conversion operator unless you specify `Narrowing`.</span></span> <span data-ttu-id="32412-117">Bu işleç yordamının bir [genişletme](../modifiers/widening.md) dönüşümünü tanımladığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="32412-117">Indicates that this operator procedure defines a [Widening](../modifiers/widening.md) conversion.</span></span> <span data-ttu-id="32412-118">Bu Yardım sayfasında "genişletme ve daraltma dönüşümleri" başlığına bakın.</span><span class="sxs-lookup"><span data-stu-id="32412-118">See "Widening and Narrowing Conversions" on this Help page.</span></span>

`Narrowing`  
<span data-ttu-id="32412-119">Belirtmediğiniz takdirde bir dönüştürme işleci için gereklidir `Widening` .</span><span class="sxs-lookup"><span data-stu-id="32412-119">Required for a conversion operator unless you specify `Widening`.</span></span> <span data-ttu-id="32412-120">Bu işleç yordamının bir [daraltma](../modifiers/narrowing.md) dönüşümünü tanımladığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="32412-120">Indicates that this operator procedure defines a [Narrowing](../modifiers/narrowing.md) conversion.</span></span> <span data-ttu-id="32412-121">Bu Yardım sayfasında "genişletme ve daraltma dönüşümleri" başlığına bakın.</span><span class="sxs-lookup"><span data-stu-id="32412-121">See "Widening and Narrowing Conversions" on this Help page.</span></span>

`operatorsymbol`  
<span data-ttu-id="32412-122">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="32412-122">Required.</span></span> <span data-ttu-id="32412-123">Bu işleç yordamının tanımladığı işlecin simgesi veya tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="32412-123">The symbol or identifier of the operator that this operator procedure defines.</span></span>

`operand1`  
<span data-ttu-id="32412-124">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="32412-124">Required.</span></span> <span data-ttu-id="32412-125">Birli işlecin tek işleneninin adı ve türü (dönüştürme işleci dahil) veya bir ikili işlecinin sol işleneni.</span><span class="sxs-lookup"><span data-stu-id="32412-125">The name and type of the single operand of a unary operator (including a conversion operator) or the left operand of a binary operator.</span></span>

`operand2`  
<span data-ttu-id="32412-126">İkili işleçler için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="32412-126">Required for binary operators.</span></span> <span data-ttu-id="32412-127">Bir ikili işlecinin sağ işleneninin adı ve türü.</span><span class="sxs-lookup"><span data-stu-id="32412-127">The name and type of the right operand of a binary operator.</span></span>

<span data-ttu-id="32412-128">`operand1`ve `operand2` aşağıdaki söz dizimi ve bölümlere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="32412-128">`operand1` and `operand2` have the following syntax and parts:</span></span>

`[ ByVal ] operandname [ As operandtype ]`

|<span data-ttu-id="32412-129">Bölüm</span><span class="sxs-lookup"><span data-stu-id="32412-129">Part</span></span>|<span data-ttu-id="32412-130">Description</span><span class="sxs-lookup"><span data-stu-id="32412-130">Description</span></span>|
|----------|-----------------|
|`ByVal`|<span data-ttu-id="32412-131">İsteğe bağlı, ancak geçen mekanizmanın [ByVal](../modifiers/byval.md)olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="32412-131">Optional, but the passing mechanism must be [ByVal](../modifiers/byval.md).</span></span>|
|`operandname`|<span data-ttu-id="32412-132">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="32412-132">Required.</span></span> <span data-ttu-id="32412-133">Bu işleneni temsil eden değişkenin adı.</span><span class="sxs-lookup"><span data-stu-id="32412-133">Name of the variable representing this operand.</span></span> <span data-ttu-id="32412-134">Bkz. [tanımlanmış öğe adları](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="32412-134">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|
|`operandtype`|<span data-ttu-id="32412-135">Olmadığı müddetçe isteğe bağlıdır `Option Strict` `On` .</span><span class="sxs-lookup"><span data-stu-id="32412-135">Optional unless `Option Strict` is `On`.</span></span> <span data-ttu-id="32412-136">Bu işlenenin veri türü.</span><span class="sxs-lookup"><span data-stu-id="32412-136">Data type of this operand.</span></span>|

`type`  
<span data-ttu-id="32412-137">Olmadığı müddetçe isteğe bağlıdır `Option Strict` `On` .</span><span class="sxs-lookup"><span data-stu-id="32412-137">Optional unless `Option Strict` is `On`.</span></span> <span data-ttu-id="32412-138">İşleç yordamının döndürdüğü değerin veri türü.</span><span class="sxs-lookup"><span data-stu-id="32412-138">Data type of the value the operator procedure returns.</span></span>

`statements`  
<span data-ttu-id="32412-139">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="32412-139">Optional.</span></span> <span data-ttu-id="32412-140">İşleç yordamının çalıştığı deyimler bloğu.</span><span class="sxs-lookup"><span data-stu-id="32412-140">Block of statements that the operator procedure runs.</span></span>

`returnvalue`  
<span data-ttu-id="32412-141">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="32412-141">Required.</span></span> <span data-ttu-id="32412-142">İşleç yordamının çağırma koduna döndürdüğü değer.</span><span class="sxs-lookup"><span data-stu-id="32412-142">The value that the operator procedure returns to the calling code.</span></span>

<span data-ttu-id="32412-143">`End` `Operator`</span><span class="sxs-lookup"><span data-stu-id="32412-143">`End` `Operator`</span></span>  
<span data-ttu-id="32412-144">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="32412-144">Required.</span></span> <span data-ttu-id="32412-145">Bu işleç yordamının tanımını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="32412-145">Terminates the definition of this operator procedure.</span></span>

## <a name="remarks"></a><span data-ttu-id="32412-146">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="32412-146">Remarks</span></span>

<span data-ttu-id="32412-147">`Operator`Yalnızca bir sınıf veya yapı içinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32412-147">You can use `Operator` only in a class or structure.</span></span> <span data-ttu-id="32412-148">Bu, bir işlecin *bildirim bağlamının* kaynak dosya, ad alanı, modül, arabirim, yordam veya blok olamayacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="32412-148">This means the *declaration context* for an operator cannot be a source file, namespace, module, interface, procedure, or block.</span></span> <span data-ttu-id="32412-149">Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="32412-149">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="32412-150">Tüm işleçler olmalıdır `Public Shared` .</span><span class="sxs-lookup"><span data-stu-id="32412-150">All operators must be `Public Shared`.</span></span> <span data-ttu-id="32412-151">`ByRef` `Optional` `ParamArray` Her iki işlenen için, veya belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="32412-151">You cannot specify `ByRef`, `Optional`, or `ParamArray` for either operand.</span></span>

<span data-ttu-id="32412-152">Dönüş değerini tutmak için işleç sembolünü veya tanımlayıcıyı kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="32412-152">You cannot use the operator symbol or identifier to hold a return value.</span></span> <span data-ttu-id="32412-153">İfadesini kullanmanız gerekir `Return` ve bir değer belirtmelidir.</span><span class="sxs-lookup"><span data-stu-id="32412-153">You must use the `Return` statement, and it must specify a value.</span></span> <span data-ttu-id="32412-154">Herhangi bir sayıda `Return` deyim yordamda herhangi bir yerde görünebilir.</span><span class="sxs-lookup"><span data-stu-id="32412-154">Any number of `Return` statements can appear anywhere in the procedure.</span></span>

<span data-ttu-id="32412-155">Bu şekilde bir işleci tanımlamak *işleç aşırı yüklemesi*olarak adlandırılır, `Overloads` anahtar sözcüğünü kullanıp kullanmayacağınızı.</span><span class="sxs-lookup"><span data-stu-id="32412-155">Defining an operator in this way is called *operator overloading*, whether or not you use the `Overloads` keyword.</span></span> <span data-ttu-id="32412-156">Aşağıdaki tabloda, tanımlayabilmeniz için kullanabileceğiniz işleçler listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="32412-156">The following table lists the operators you can define.</span></span>

|<span data-ttu-id="32412-157">Tür</span><span class="sxs-lookup"><span data-stu-id="32412-157">Type</span></span>|<span data-ttu-id="32412-158">İşleçler</span><span class="sxs-lookup"><span data-stu-id="32412-158">Operators</span></span>|
|----------|---------------|
|<span data-ttu-id="32412-159">Birli</span><span class="sxs-lookup"><span data-stu-id="32412-159">Unary</span></span>|<span data-ttu-id="32412-160">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span><span class="sxs-lookup"><span data-stu-id="32412-160">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span></span>|
|<span data-ttu-id="32412-161">İkili</span><span class="sxs-lookup"><span data-stu-id="32412-161">Binary</span></span>|<span data-ttu-id="32412-162">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span><span class="sxs-lookup"><span data-stu-id="32412-162">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span></span>|
|<span data-ttu-id="32412-163">Dönüştürme (birli)</span><span class="sxs-lookup"><span data-stu-id="32412-163">Conversion (unary)</span></span>|`CType`|

<span data-ttu-id="32412-164">`=`İkili listedeki işlecin atama işleci değil karşılaştırma operatörü olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="32412-164">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>

<span data-ttu-id="32412-165">Tanımlarken, ya `CType` da belirtmeniz gerekir `Widening` `Narrowing` .</span><span class="sxs-lookup"><span data-stu-id="32412-165">When you define `CType`, you must specify either `Widening` or `Narrowing`.</span></span>

## <a name="matched-pairs"></a><span data-ttu-id="32412-166">Eşleşen çiftler</span><span class="sxs-lookup"><span data-stu-id="32412-166">Matched Pairs</span></span>

<span data-ttu-id="32412-167">Belirli işleçleri eşleşen çiftler olarak tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="32412-167">You must define certain operators as matched pairs.</span></span> <span data-ttu-id="32412-168">Böyle bir çiftin işlecini tanımlarsanız, diğerini de tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="32412-168">If you define either operator of such a pair, you must define the other as well.</span></span> <span data-ttu-id="32412-169">Eşleşen çiftler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="32412-169">The matched pairs are the following:</span></span>

- <span data-ttu-id="32412-170">`=` ve `<>`</span><span class="sxs-lookup"><span data-stu-id="32412-170">`=` and `<>`</span></span>

- <span data-ttu-id="32412-171">`>` ve `<`</span><span class="sxs-lookup"><span data-stu-id="32412-171">`>` and `<`</span></span>

- <span data-ttu-id="32412-172">`>=` ve `<=`</span><span class="sxs-lookup"><span data-stu-id="32412-172">`>=` and `<=`</span></span>

- <span data-ttu-id="32412-173">`IsTrue` ve `IsFalse`</span><span class="sxs-lookup"><span data-stu-id="32412-173">`IsTrue` and `IsFalse`</span></span>

## <a name="data-type-restrictions"></a><span data-ttu-id="32412-174">Veri türü kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="32412-174">Data Type Restrictions</span></span>

<span data-ttu-id="32412-175">Tanımladığınız her operatör, üzerinde tanımladığınız sınıf veya yapıyı içermelidir.</span><span class="sxs-lookup"><span data-stu-id="32412-175">Every operator you define must involve the class or structure on which you define it.</span></span> <span data-ttu-id="32412-176">Bu, sınıfın veya yapının aşağıdakilerin veri türü olarak görünmesi gerektiği anlamına gelir:</span><span class="sxs-lookup"><span data-stu-id="32412-176">This means that the class or structure must appear as the data type of the following:</span></span>

- <span data-ttu-id="32412-177">Birli işlecin işleneni.</span><span class="sxs-lookup"><span data-stu-id="32412-177">The operand of a unary operator.</span></span>

- <span data-ttu-id="32412-178">Bir ikili işlecinin işlenenlerinden en az biri.</span><span class="sxs-lookup"><span data-stu-id="32412-178">At least one of the operands of a binary operator.</span></span>

- <span data-ttu-id="32412-179">Bir dönüştürme işlecinin işleneni ya da dönüş türü.</span><span class="sxs-lookup"><span data-stu-id="32412-179">Either the operand or the return type of a conversion operator.</span></span>

 <span data-ttu-id="32412-180">Bazı işleçler, aşağıdaki gibi ek veri türü kısıtlamalarına sahiptir:</span><span class="sxs-lookup"><span data-stu-id="32412-180">Certain operators have additional data type restrictions, as follows:</span></span>

- <span data-ttu-id="32412-181">`IsTrue`Ve `IsFalse` işleçlerini tanımlarsanız, her ikisi de `Boolean` türü döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="32412-181">If you define the `IsTrue` and `IsFalse` operators, they must both return the `Boolean` type.</span></span>

- <span data-ttu-id="32412-182">Ve işleçlerini tanımlarsanız, `<<` `>>` her ikisi de `Integer` öğesinin türünü belirtmelidir `operandtype` `operand2` .</span><span class="sxs-lookup"><span data-stu-id="32412-182">If you define the `<<` and `>>` operators, they must both specify the `Integer` type for the `operandtype` of `operand2`.</span></span>

<span data-ttu-id="32412-183">Dönüş türünün, her iki işlenenin türüne karşılık gelmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="32412-183">The return type does not have to correspond to the type of either operand.</span></span> <span data-ttu-id="32412-184">Örneğin, veya gibi bir karşılaştırma işleci `=` `<>` `Boolean` , hiçbir işleneni olmasa bile dönebilir `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="32412-184">For example, a comparison operator such as `=` or `<>` can return `Boolean` even if neither operand is `Boolean`.</span></span>

## <a name="logical-and-bitwise-operators"></a><span data-ttu-id="32412-185">Mantıksal ve Bit Düzeyinde İşleçler</span><span class="sxs-lookup"><span data-stu-id="32412-185">Logical and Bitwise Operators</span></span>

<span data-ttu-id="32412-186">`And`,, `Or` `Not` Ve `Xor` işleçleri Visual Basic mantıksal veya bit tabanlı işlemler gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="32412-186">The `And`, `Or`, `Not`, and `Xor` operators can perform either logical or bitwise operations in Visual Basic.</span></span> <span data-ttu-id="32412-187">Ancak, bu işleçlerden birini bir sınıf veya yapıda tanımlarsanız, yalnızca bit düzeyinde işlemini tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32412-187">However, if you define one of these operators on a class or structure, you can define only its bitwise operation.</span></span>

<span data-ttu-id="32412-188">`AndAlso`İşleci bir ifadesiyle doğrudan tanımlayamazsınız `Operator` .</span><span class="sxs-lookup"><span data-stu-id="32412-188">You cannot define the `AndAlso` operator directly with an `Operator` statement.</span></span> <span data-ttu-id="32412-189">Ancak, `AndAlso` aşağıdaki koşulları karşıladıysanız kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="32412-189">However, you can use `AndAlso` if you have fulfilled the following conditions:</span></span>

- <span data-ttu-id="32412-190">`And`İçin kullanmak istediğiniz aynı işlenen türlerinde tanımladınız `AndAlso` .</span><span class="sxs-lookup"><span data-stu-id="32412-190">You have defined `And` on the same operand types you want to use for `AndAlso`.</span></span>

- <span data-ttu-id="32412-191">Tanımınız, `And` tanımladığınız sınıf veya yapı ile aynı türü döndürür.</span><span class="sxs-lookup"><span data-stu-id="32412-191">Your definition of `And` returns the same type as the class or structure on which you have defined it.</span></span>

- <span data-ttu-id="32412-192">`IsFalse`İşleci, tanımladığınız sınıf veya yapı üzerinde tanımladınız `And` .</span><span class="sxs-lookup"><span data-stu-id="32412-192">You have defined the `IsFalse` operator on the class or structure on which you have defined `And`.</span></span>

<span data-ttu-id="32412-193">Benzer şekilde, `OrElse` `Or` sınıf veya yapının dönüş türü ile aynı işlenenler üzerinde tanımlamış olmanız ve `IsTrue` sınıf veya yapıda tanımladığınız durumlarda kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32412-193">Similarly, you can use `OrElse` if you have defined `Or` on the same operands, with the return type of the class or structure, and you have defined `IsTrue` on the class or structure.</span></span>

## <a name="widening-and-narrowing-conversions"></a><span data-ttu-id="32412-194">Genişletme ve Daraltma Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="32412-194">Widening and Narrowing Conversions</span></span>

<span data-ttu-id="32412-195">Her *zaman* çalışma zamanında bir daraltma dönüştürmesi başarısız olsa da, bir *daraltma* dönüştürmesi çalışma zamanında başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="32412-195">A *widening conversion* always succeeds at run time, while a *narrowing conversion* can fail at run time.</span></span> <span data-ttu-id="32412-196">Daha fazla bilgi için bkz. [genişletme ve daraltma dönüştürmeleri](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="32412-196">For more information, see [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>

<span data-ttu-id="32412-197">Bir dönüştürme yordamı belirtmek isterseniz `Widening` , yordam kodunuzun herhangi bir başarısızlık üretmemelidir.</span><span class="sxs-lookup"><span data-stu-id="32412-197">If you declare a conversion procedure to be `Widening`, your procedure code must not generate any failures.</span></span> <span data-ttu-id="32412-198">Bunun anlamı:</span><span class="sxs-lookup"><span data-stu-id="32412-198">This means the following:</span></span>

- <span data-ttu-id="32412-199">Her zaman geçerli bir tür değeri döndürmelidir `type` .</span><span class="sxs-lookup"><span data-stu-id="32412-199">It must always return a valid value of type `type`.</span></span>

- <span data-ttu-id="32412-200">Tüm olası özel durumları ve diğer hata koşullarını ele almalıdır.</span><span class="sxs-lookup"><span data-stu-id="32412-200">It must handle all possible exceptions and other error conditions.</span></span>

- <span data-ttu-id="32412-201">Çağrı yaptığı tüm yordamlardan hata getirlerinin işlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="32412-201">It must handle any error returns from any procedures it calls.</span></span>

<span data-ttu-id="32412-202">Bir dönüştürme yordamının başarılı bir şekilde başarısız olabileceği veya işlenmemiş bir özel duruma neden olabileceği durumlarda, bunu olarak bildirmeniz gerekir `Narrowing` .</span><span class="sxs-lookup"><span data-stu-id="32412-202">If there is any possibility that a conversion procedure might not succeed, or that it might cause an unhandled exception, you must declare it to be `Narrowing`.</span></span>

## <a name="example"></a><span data-ttu-id="32412-203">Örnek</span><span class="sxs-lookup"><span data-stu-id="32412-203">Example</span></span>

<span data-ttu-id="32412-204">Aşağıdaki kod örneği,,, `Operator` ve işleçleri için işleç yordamları içeren bir yapının anahattını tanımlamak için ifadesini kullanır `And` `Or` `IsFalse` `IsTrue` .</span><span class="sxs-lookup"><span data-stu-id="32412-204">The following code example uses the `Operator` statement to define the outline of a structure that includes operator procedures for the `And`, `Or`, `IsFalse`, and `IsTrue` operators.</span></span> <span data-ttu-id="32412-205">`And`ve `Or` her biri türü ve dönüş türü iki işleneni alır `abc` `abc` .</span><span class="sxs-lookup"><span data-stu-id="32412-205">`And` and `Or` each take two operands of type `abc` and return type `abc`.</span></span> <span data-ttu-id="32412-206">`IsFalse`ve `IsTrue` her biri, türünde tek bir işlenen alır `abc` ve döndürür `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="32412-206">`IsFalse` and `IsTrue` each take a single operand of type `abc` and return `Boolean`.</span></span> <span data-ttu-id="32412-207">Bu tanımlar çağıran kodun,,, `And` `AndAlso` `Or` ve `OrElse` türündeki işlenenleri `abc` kullanmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="32412-207">These definitions allow the calling code to use `And`, `AndAlso`, `Or`, and `OrElse` with operands of type `abc`.</span></span>

[!code-vb[VbVbalrStatements#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#44)]

## <a name="see-also"></a><span data-ttu-id="32412-208">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32412-208">See also</span></span>

- [<span data-ttu-id="32412-209">IsFalse İşleci</span><span class="sxs-lookup"><span data-stu-id="32412-209">IsFalse Operator</span></span>](../operators/isfalse-operator.md)
- [<span data-ttu-id="32412-210">IsTrue İşleci</span><span class="sxs-lookup"><span data-stu-id="32412-210">IsTrue Operator</span></span>](../operators/istrue-operator.md)
- [<span data-ttu-id="32412-211">Genişletme</span><span class="sxs-lookup"><span data-stu-id="32412-211">Widening</span></span>](../modifiers/widening.md)
- [<span data-ttu-id="32412-212">Narrowing</span><span class="sxs-lookup"><span data-stu-id="32412-212">Narrowing</span></span>](../modifiers/narrowing.md)
- [<span data-ttu-id="32412-213">Genişletme ve Daraltma Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="32412-213">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="32412-214">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="32412-214">Operator Procedures</span></span>](../../programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="32412-215">Nasıl yapılır: İşleç Tanımlama</span><span class="sxs-lookup"><span data-stu-id="32412-215">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="32412-216">Nasıl yapılır: Dönüştürme İşleci Tanımlama</span><span class="sxs-lookup"><span data-stu-id="32412-216">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="32412-217">Nasıl yapılır: Bir İşleç Yordamı Çağırma</span><span class="sxs-lookup"><span data-stu-id="32412-217">How to: Call an Operator Procedure</span></span>](../../programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="32412-218">Nasıl yapılır: İşleçleri Tanımlayan Bir Sınıf Kullanma</span><span class="sxs-lookup"><span data-stu-id="32412-218">How to: Use a Class that Defines Operators</span></span>](../../programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)
