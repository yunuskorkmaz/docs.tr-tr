---
title: Operator deyimi (Visual Basic)
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
ms.openlocfilehash: 184970d33aae4af135153f9d6f6755770bdf84f6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58818598"
---
# <a name="operator-statement"></a><span data-ttu-id="e8912-102">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="e8912-102">Operator Statement</span></span>
<span data-ttu-id="e8912-103">Operatör sembolünü, işlenenleri ve bir sınıf ya da yapı üzerinde bir işleç yordamı tanımlayan kodu bildirir.</span><span class="sxs-lookup"><span data-stu-id="e8912-103">Declares the operator symbol, operands, and code that define an operator procedure on a class or structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8912-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e8912-104">Syntax</span></span>  
  
```  
[ <attrlist> ] Public [ Overloads ] Shared [ Shadows ] [ Widening | Narrowing ]   
Operator operatorsymbol ( operand1 [, operand2 ]) [ As [ <attrlist> ] type ]  
    [ statements ]  
    [ statements ]  
    Return returnvalue  
    [ statements ]  
End Operator  
```  
  
## <a name="parts"></a><span data-ttu-id="e8912-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="e8912-105">Parts</span></span>  
 `attrlist`  
 <span data-ttu-id="e8912-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e8912-106">Optional.</span></span> <span data-ttu-id="e8912-107">Bkz: [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="e8912-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
 `Public`  
 <span data-ttu-id="e8912-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="e8912-108">Required.</span></span> <span data-ttu-id="e8912-109">Bu işleç yordamı sahip olduğunu gösterir [genel](../../../visual-basic/language-reference/modifiers/public.md) erişim.</span><span class="sxs-lookup"><span data-stu-id="e8912-109">Indicates that this operator procedure has [Public](../../../visual-basic/language-reference/modifiers/public.md) access.</span></span>  
  
 `Overloads`  
 <span data-ttu-id="e8912-110">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e8912-110">Optional.</span></span> <span data-ttu-id="e8912-111">Bkz: [aşırı](../../../visual-basic/language-reference/modifiers/overloads.md).</span><span class="sxs-lookup"><span data-stu-id="e8912-111">See [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md).</span></span>  
  
 `Shared`  
 <span data-ttu-id="e8912-112">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="e8912-112">Required.</span></span> <span data-ttu-id="e8912-113">Bu işleç yordamı olduğunu belirten bir [paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md) yordamı.</span><span class="sxs-lookup"><span data-stu-id="e8912-113">Indicates that this operator procedure is a [Shared](../../../visual-basic/language-reference/modifiers/shared.md) procedure.</span></span>  
  
 `Shadows`  
 <span data-ttu-id="e8912-114">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e8912-114">Optional.</span></span> <span data-ttu-id="e8912-115">Bkz: [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="e8912-115">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
 `Widening`  
 <span data-ttu-id="e8912-116">Siz belirtmediğiniz sürece, bir dönüştürme işleci için gerekli `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="e8912-116">Required for a conversion operator unless you specify `Narrowing`.</span></span> <span data-ttu-id="e8912-117">Bu işleç yordamı tanımlayan gösteren bir [Widening](../../../visual-basic/language-reference/modifiers/widening.md) dönüştürme.</span><span class="sxs-lookup"><span data-stu-id="e8912-117">Indicates that this operator procedure defines a [Widening](../../../visual-basic/language-reference/modifiers/widening.md) conversion.</span></span> <span data-ttu-id="e8912-118">"Genişletme ve daraltma dönüştürmeleri" Bu Yardım sayfasında bakın.</span><span class="sxs-lookup"><span data-stu-id="e8912-118">See "Widening and Narrowing Conversions" on this Help page.</span></span>  
  
 `Narrowing`  
 <span data-ttu-id="e8912-119">Siz belirtmediğiniz sürece, bir dönüştürme işleci için gerekli `Widening`.</span><span class="sxs-lookup"><span data-stu-id="e8912-119">Required for a conversion operator unless you specify `Widening`.</span></span> <span data-ttu-id="e8912-120">Bu işleç yordamı tanımlayan gösteren bir [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md) dönüştürme.</span><span class="sxs-lookup"><span data-stu-id="e8912-120">Indicates that this operator procedure defines a [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md) conversion.</span></span> <span data-ttu-id="e8912-121">"Genişletme ve daraltma dönüştürmeleri" Bu Yardım sayfasında bakın.</span><span class="sxs-lookup"><span data-stu-id="e8912-121">See "Widening and Narrowing Conversions" on this Help page.</span></span>  
  
 `operatorsymbol`  
 <span data-ttu-id="e8912-122">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="e8912-122">Required.</span></span> <span data-ttu-id="e8912-123">Simge veya bu işleç yordamı tanımlar işlecin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="e8912-123">The symbol or identifier of the operator that this operator procedure defines.</span></span>  
  
 `operand1`  
 <span data-ttu-id="e8912-124">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="e8912-124">Required.</span></span> <span data-ttu-id="e8912-125">Adı ve tek bir işlenen (dönüştürme işleci dahil) birli işleç veya sol işleneni, ikili işleç türü.</span><span class="sxs-lookup"><span data-stu-id="e8912-125">The name and type of the single operand of a unary operator (including a conversion operator) or the left operand of a binary operator.</span></span>  
  
 `operand2`  
 <span data-ttu-id="e8912-126">İkili işleçler için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e8912-126">Required for binary operators.</span></span> <span data-ttu-id="e8912-127">Bir ikili işlecinin sağ işleneninin türü ve adı.</span><span class="sxs-lookup"><span data-stu-id="e8912-127">The name and type of the right operand of a binary operator.</span></span>  
  
 <span data-ttu-id="e8912-128">`operand1` ve `operand2` aşağıdaki söz dizimini ve bölümleri vardır:</span><span class="sxs-lookup"><span data-stu-id="e8912-128">`operand1` and `operand2` have the following syntax and parts:</span></span>  
  
 `[ ByVal ] operandname [ As operandtype ]`  
  
|<span data-ttu-id="e8912-129">Bölümü</span><span class="sxs-lookup"><span data-stu-id="e8912-129">Part</span></span>|<span data-ttu-id="e8912-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e8912-130">Description</span></span>|  
|----------|-----------------|  
|`ByVal`|<span data-ttu-id="e8912-131">İsteğe bağlı, ancak geçirme mekanizması olmalıdır [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="e8912-131">Optional, but the passing mechanism must be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span></span>|  
|`operandname`|<span data-ttu-id="e8912-132">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="e8912-132">Required.</span></span> <span data-ttu-id="e8912-133">Bu işlenen temsil eden değişkenin adı.</span><span class="sxs-lookup"><span data-stu-id="e8912-133">Name of the variable representing this operand.</span></span> <span data-ttu-id="e8912-134">Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="e8912-134">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`operandtype`|<span data-ttu-id="e8912-135">İsteğe bağlı sürece `Option Strict` olduğu `On`.</span><span class="sxs-lookup"><span data-stu-id="e8912-135">Optional unless `Option Strict` is `On`.</span></span> <span data-ttu-id="e8912-136">Bu işlenen veri türü.</span><span class="sxs-lookup"><span data-stu-id="e8912-136">Data type of this operand.</span></span>|  
  
 `type`  
 <span data-ttu-id="e8912-137">İsteğe bağlı sürece `Option Strict` olduğu `On`.</span><span class="sxs-lookup"><span data-stu-id="e8912-137">Optional unless `Option Strict` is `On`.</span></span> <span data-ttu-id="e8912-138">İşleç yordamı değerinin veri türü döndürür.</span><span class="sxs-lookup"><span data-stu-id="e8912-138">Data type of the value the operator procedure returns.</span></span>  
  
 `statements`  
 <span data-ttu-id="e8912-139">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e8912-139">Optional.</span></span> <span data-ttu-id="e8912-140">İşleç yordamı çalıştıran bir deyimler bloğunu.</span><span class="sxs-lookup"><span data-stu-id="e8912-140">Block of statements that the operator procedure runs.</span></span>  
  
 `returnvalue`  
 <span data-ttu-id="e8912-141">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="e8912-141">Required.</span></span> <span data-ttu-id="e8912-142">İşleç yordamı çağırma koda döndürür. değer.</span><span class="sxs-lookup"><span data-stu-id="e8912-142">The value that the operator procedure returns to the calling code.</span></span>  
  
 <span data-ttu-id="e8912-143">`End``Operator`</span><span class="sxs-lookup"><span data-stu-id="e8912-143">`End` `Operator`</span></span>  
 <span data-ttu-id="e8912-144">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="e8912-144">Required.</span></span> <span data-ttu-id="e8912-145">Bu işleç yordamı tanımını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="e8912-145">Terminates the definition of this operator procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8912-146">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e8912-146">Remarks</span></span>  
 <span data-ttu-id="e8912-147">Kullanabileceğiniz `Operator` yalnızca bir sınıf veya yapı içinde.</span><span class="sxs-lookup"><span data-stu-id="e8912-147">You can use `Operator` only in a class or structure.</span></span> <span data-ttu-id="e8912-148">Başka bir deyişle *bildirim içeriğinin* operatörün bir kaynak dosyası, ad alanı, modülü, arabirim, yordam veya blok olamayacağı için.</span><span class="sxs-lookup"><span data-stu-id="e8912-148">This means the *declaration context* for an operator cannot be a source file, namespace, module, interface, procedure, or block.</span></span> <span data-ttu-id="e8912-149">Daha fazla bilgi için [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="e8912-149">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="e8912-150">Tüm işleçler olmalıdır `Public Shared`.</span><span class="sxs-lookup"><span data-stu-id="e8912-150">All operators must be `Public Shared`.</span></span> <span data-ttu-id="e8912-151">Belirtemezsiniz `ByRef`, `Optional`, veya `ParamArray` iki işlenenden için.</span><span class="sxs-lookup"><span data-stu-id="e8912-151">You cannot specify `ByRef`, `Optional`, or `ParamArray` for either operand.</span></span>  
  
 <span data-ttu-id="e8912-152">Dönüş değerini tutmak için işlecin veya tanımlayıcısı'nı kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="e8912-152">You cannot use the operator symbol or identifier to hold a return value.</span></span> <span data-ttu-id="e8912-153">Kullanmalısınız `Return` ifadesi ve bir değer belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e8912-153">You must use the `Return` statement, and it must specify a value.</span></span> <span data-ttu-id="e8912-154">Herhangi bir sayıda `Return` deyimleri yordamda herhangi bir yerinde görünebilir.</span><span class="sxs-lookup"><span data-stu-id="e8912-154">Any number of `Return` statements can appear anywhere in the procedure.</span></span>  
  
 <span data-ttu-id="e8912-155">Bu şekilde bir işleci tanımlama çağrılır *İşleç aşırı yüklemesi*, kullandığınız olup olmadığını `Overloads` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="e8912-155">Defining an operator in this way is called *operator overloading*, whether or not you use the `Overloads` keyword.</span></span> <span data-ttu-id="e8912-156">Aşağıdaki tabloda, tanımlayabileceğiniz işleçleri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="e8912-156">The following table lists the operators you can define.</span></span>  
  
|<span data-ttu-id="e8912-157">Tür</span><span class="sxs-lookup"><span data-stu-id="e8912-157">Type</span></span>|<span data-ttu-id="e8912-158">İşleçler</span><span class="sxs-lookup"><span data-stu-id="e8912-158">Operators</span></span>|  
|----------|---------------|  
|<span data-ttu-id="e8912-159">Birli</span><span class="sxs-lookup"><span data-stu-id="e8912-159">Unary</span></span>|<span data-ttu-id="e8912-160">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span><span class="sxs-lookup"><span data-stu-id="e8912-160">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span></span>|  
|<span data-ttu-id="e8912-161">İkili</span><span class="sxs-lookup"><span data-stu-id="e8912-161">Binary</span></span>|<span data-ttu-id="e8912-162">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span><span class="sxs-lookup"><span data-stu-id="e8912-162">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span></span>|  
|<span data-ttu-id="e8912-163">Dönüştürme (tekli)</span><span class="sxs-lookup"><span data-stu-id="e8912-163">Conversion (unary)</span></span>|`CType`|  
  
 <span data-ttu-id="e8912-164">Unutmayın `=` işlecidir ikili listesinde karşılaştırma işleci atama işleci.</span><span class="sxs-lookup"><span data-stu-id="e8912-164">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>  
  
 <span data-ttu-id="e8912-165">Tanımladığınızda `CType`, belirtmeli `Widening` veya `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="e8912-165">When you define `CType`, you must specify either `Widening` or `Narrowing`.</span></span>  
  
## <a name="matched-pairs"></a><span data-ttu-id="e8912-166">Eşleşen çiftleri</span><span class="sxs-lookup"><span data-stu-id="e8912-166">Matched Pairs</span></span>  
 <span data-ttu-id="e8912-167">Belirli işleçleri eşleşen çiftleri tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e8912-167">You must define certain operators as matched pairs.</span></span> <span data-ttu-id="e8912-168">Böyle bir çifti ya da işleç tanımlarsanız, diğeri de tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e8912-168">If you define either operator of such a pair, you must define the other as well.</span></span> <span data-ttu-id="e8912-169">Eşleşen çiftleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e8912-169">The matched pairs are the following:</span></span>  
  
-   <span data-ttu-id="e8912-170">`=` ve `<>`</span><span class="sxs-lookup"><span data-stu-id="e8912-170">`=` and `<>`</span></span>  
  
-   <span data-ttu-id="e8912-171">`>` ve `<`</span><span class="sxs-lookup"><span data-stu-id="e8912-171">`>` and `<`</span></span>  
  
-   <span data-ttu-id="e8912-172">`>=` ve `<=`</span><span class="sxs-lookup"><span data-stu-id="e8912-172">`>=` and `<=`</span></span>  
  
-   <span data-ttu-id="e8912-173">`IsTrue` ve `IsFalse`</span><span class="sxs-lookup"><span data-stu-id="e8912-173">`IsTrue` and `IsFalse`</span></span>  
  
## <a name="data-type-restrictions"></a><span data-ttu-id="e8912-174">Veri türü kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="e8912-174">Data Type Restrictions</span></span>  
 <span data-ttu-id="e8912-175">Tanımladığınız her işleci üzerinde tanımladığınız sınıf veya yapı kapsaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e8912-175">Every operator you define must involve the class or structure on which you define it.</span></span> <span data-ttu-id="e8912-176">Başka bir deyişle, sınıf veya yapı aşağıdaki veri türünde yer almalıdır:</span><span class="sxs-lookup"><span data-stu-id="e8912-176">This means that the class or structure must appear as the data type of the following:</span></span>  
  
-   <span data-ttu-id="e8912-177">Birli işleç işleneni.</span><span class="sxs-lookup"><span data-stu-id="e8912-177">The operand of a unary operator.</span></span>  
  
-   <span data-ttu-id="e8912-178">En az bir ikili işlecinin işlenenleri.</span><span class="sxs-lookup"><span data-stu-id="e8912-178">At least one of the operands of a binary operator.</span></span>  
  
-   <span data-ttu-id="e8912-179">İşlenen veya bir dönüştürme işlecinin dönüş türü.</span><span class="sxs-lookup"><span data-stu-id="e8912-179">Either the operand or the return type of a conversion operator.</span></span>  
  
 <span data-ttu-id="e8912-180">Belirli operatörün ek veri kısıtlamaları, aşağıdaki gibi yazın:</span><span class="sxs-lookup"><span data-stu-id="e8912-180">Certain operators have additional data type restrictions, as follows:</span></span>  
  
-   <span data-ttu-id="e8912-181">Tanımlarsanız `IsTrue` ve `IsFalse` işleçleri, bunların her ikisi de döndürmelidir `Boolean` türü.</span><span class="sxs-lookup"><span data-stu-id="e8912-181">If you define the `IsTrue` and `IsFalse` operators, they must both return the `Boolean` type.</span></span>  
  
-   <span data-ttu-id="e8912-182">Tanımlarsanız `<<` ve `>>` işleçleri, bunların her ikisini de belirtmelisiniz `Integer` yazın `operandtype` , `operand2`.</span><span class="sxs-lookup"><span data-stu-id="e8912-182">If you define the `<<` and `>>` operators, they must both specify the `Integer` type for the `operandtype` of `operand2`.</span></span>  
  
 <span data-ttu-id="e8912-183">İki işlenenden türüne karşılık gelen dönüş türü yok.</span><span class="sxs-lookup"><span data-stu-id="e8912-183">The return type does not have to correspond to the type of either operand.</span></span> <span data-ttu-id="e8912-184">Örneğin, bir karşılaştırma işleci gibi `=` veya `<>` döndürebilir `Boolean` iki işlenenin olsa bile `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="e8912-184">For example, a comparison operator such as `=` or `<>` can return `Boolean` even if neither operand is `Boolean`.</span></span>  
  
## <a name="logical-and-bitwise-operators"></a><span data-ttu-id="e8912-185">Mantıksal ve Bit Düzeyinde İşleçler</span><span class="sxs-lookup"><span data-stu-id="e8912-185">Logical and Bitwise Operators</span></span>  
 <span data-ttu-id="e8912-186">`And`, `Or`, `Not`, Ve `Xor` işleçleri Visual Basic'de mantıksal ve bit düzeyinde işlemleri gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="e8912-186">The `And`, `Or`, `Not`, and `Xor` operators can perform either logical or bitwise operations in Visual Basic.</span></span> <span data-ttu-id="e8912-187">Ancak, bu işleçler birini bir sınıf veya yapı tanımlarsanız, yalnızca, bit düzeyinde işlem tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8912-187">However, if you define one of these operators on a class or structure, you can define only its bitwise operation.</span></span>  
  
 <span data-ttu-id="e8912-188">Tanımlanamaz `AndAlso` işleci ile doğrudan bir `Operator` deyimi.</span><span class="sxs-lookup"><span data-stu-id="e8912-188">You cannot define the `AndAlso` operator directly with an `Operator` statement.</span></span> <span data-ttu-id="e8912-189">Ancak, kullanabileceğiniz `AndAlso` aşağıdaki koşulların yerine getirilmesini varsa:</span><span class="sxs-lookup"><span data-stu-id="e8912-189">However, you can use `AndAlso` if you have fulfilled the following conditions:</span></span>  
  
-   <span data-ttu-id="e8912-190">Tanımladığınız `And` için kullanmak istediğiniz aynı işlenen türlerinde `AndAlso`.</span><span class="sxs-lookup"><span data-stu-id="e8912-190">You have defined `And` on the same operand types you want to use for `AndAlso`.</span></span>  
  
-   <span data-ttu-id="e8912-191">Tanımınız `And` üzerinde tanımladığınız, sınıf veya yapı aynı türü döndürür.</span><span class="sxs-lookup"><span data-stu-id="e8912-191">Your definition of `And` returns the same type as the class or structure on which you have defined it.</span></span>  
  
-   <span data-ttu-id="e8912-192">Tanımladığınız `IsFalse` üzerinde tanımladığınız sınıf ya da yapı üzerinde operatör `And`.</span><span class="sxs-lookup"><span data-stu-id="e8912-192">You have defined the `IsFalse` operator on the class or structure on which you have defined `And`.</span></span>  
  
 <span data-ttu-id="e8912-193">Benzer şekilde, kullanabileceğiniz `OrElse` tanımladıysanız, `Or` sınıf veya yapı ve size dönüş türüyle aynı işlenenlerde tanımladığınız `IsTrue` sınıf veya yapı.</span><span class="sxs-lookup"><span data-stu-id="e8912-193">Similarly, you can use `OrElse` if you have defined `Or` on the same operands, with the return type of the class or structure, and you have defined `IsTrue` on the class or structure.</span></span>  
  
## <a name="widening-and-narrowing-conversions"></a><span data-ttu-id="e8912-194">Genişletme ve Daraltma Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="e8912-194">Widening and Narrowing Conversions</span></span>  
 <span data-ttu-id="e8912-195">A *dönüştürme genişletme* çalışma zamanında, her zaman başarılı ancak bir *daraltma dönüştürmesi* çalışma zamanında başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="e8912-195">A *widening conversion* always succeeds at run time, while a *narrowing conversion* can fail at run time.</span></span> <span data-ttu-id="e8912-196">Daha fazla bilgi için [Widening ve daraltma dönüşümleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="e8912-196">For more information, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
 <span data-ttu-id="e8912-197">Bir dönüştürme yordamı olmasını bildirirseniz `Widening`, yordam kodunuzun hatalarını oluşturmamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e8912-197">If you declare a conversion procedure to be `Widening`, your procedure code must not generate any failures.</span></span> <span data-ttu-id="e8912-198">Aşağıdaki anlamına gelir:</span><span class="sxs-lookup"><span data-stu-id="e8912-198">This means the following:</span></span>  
  
-   <span data-ttu-id="e8912-199">Her zaman geçerli bir değer türü döndürmelidir `type`.</span><span class="sxs-lookup"><span data-stu-id="e8912-199">It must always return a valid value of type `type`.</span></span>  
  
-   <span data-ttu-id="e8912-200">Tüm olası özel durumları ve diğer hata durumlarını işlemelidir.</span><span class="sxs-lookup"><span data-stu-id="e8912-200">It must handle all possible exceptions and other error conditions.</span></span>  
  
-   <span data-ttu-id="e8912-201">Bu çağrı yaptığı tüm yordamları bir hata döndürür işlemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e8912-201">It must handle any error returns from any procedures it calls.</span></span>  
  
 <span data-ttu-id="e8912-202">Bir dönüştürme yordamı başarısız olabilir bir olasılık yoktur veya onun işlenmeyen bir özel durum neden olabilir, olmasını bildirmelidir `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="e8912-202">If there is any possibility that a conversion procedure might not succeed, or that it might cause an unhandled exception, you must declare it to be `Narrowing`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8912-203">Örnek</span><span class="sxs-lookup"><span data-stu-id="e8912-203">Example</span></span>  
 <span data-ttu-id="e8912-204">Aşağıdaki kod örneğinde `Operator` deyimi için işleç yordamları içeren bir yapının ana hatlarını tanımlayacak `And`, `Or`, `IsFalse`, ve `IsTrue` işleçleri.</span><span class="sxs-lookup"><span data-stu-id="e8912-204">The following code example uses the `Operator` statement to define the outline of a structure that includes operator procedures for the `And`, `Or`, `IsFalse`, and `IsTrue` operators.</span></span> <span data-ttu-id="e8912-205">`And` ve `Or` her iki işleneni de türü ele `abc` ve dönüş türü `abc`.</span><span class="sxs-lookup"><span data-stu-id="e8912-205">`And` and `Or` each take two operands of type `abc` and return type `abc`.</span></span> <span data-ttu-id="e8912-206">`IsFalse` ve `IsTrue` türünde tek bir işlenen herbiri `abc` ve dönüş `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="e8912-206">`IsFalse` and `IsTrue` each take a single operand of type `abc` and return `Boolean`.</span></span> <span data-ttu-id="e8912-207">Çağıran kod kullanmak bu tanımları izin `And`, `AndAlso`, `Or`, ve `OrElse` türündeki işlenenler ile `abc`.</span><span class="sxs-lookup"><span data-stu-id="e8912-207">These definitions allow the calling code to use `And`, `AndAlso`, `Or`, and `OrElse` with operands of type `abc`.</span></span>  
  
 [!code-vb[VbVbalrStatements#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#44)]  
  
## <a name="see-also"></a><span data-ttu-id="e8912-208">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e8912-208">See also</span></span>

- [<span data-ttu-id="e8912-209">IsFalse İşleci</span><span class="sxs-lookup"><span data-stu-id="e8912-209">IsFalse Operator</span></span>](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [<span data-ttu-id="e8912-210">IsTrue İşleci</span><span class="sxs-lookup"><span data-stu-id="e8912-210">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [<span data-ttu-id="e8912-211">Widening</span><span class="sxs-lookup"><span data-stu-id="e8912-211">Widening</span></span>](../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="e8912-212">Narrowing</span><span class="sxs-lookup"><span data-stu-id="e8912-212">Narrowing</span></span>](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="e8912-213">Genişletme ve Daraltma Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="e8912-213">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="e8912-214">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="e8912-214">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="e8912-215">Nasıl yapılır: Bir işleci tanımlama</span><span class="sxs-lookup"><span data-stu-id="e8912-215">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="e8912-216">Nasıl yapılır: Bir dönüşüm işleci tanımlama</span><span class="sxs-lookup"><span data-stu-id="e8912-216">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="e8912-217">Nasıl yapılır: Bir işleç yordamı çağırma</span><span class="sxs-lookup"><span data-stu-id="e8912-217">How to: Call an Operator Procedure</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="e8912-218">Nasıl yapılır: İşleçleri tanımlayan bir sınıf kullanma</span><span class="sxs-lookup"><span data-stu-id="e8912-218">How to: Use a Class that Defines Operators</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)
