---
title: Parametre Listesi
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic
- parameters [Visual Basic], lists
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- arguments [Visual Basic], Visual Basic
- procedures [Visual Basic], parameter lists
ms.assetid: 5d737319-0c34-4df9-a23d-188fc840becd
ms.openlocfilehash: 706fc2414806db5608cce410bf4156839ec2d83e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404323"
---
# <a name="parameter-list-visual-basic"></a><span data-ttu-id="4668f-102">Parametre Listesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4668f-102">Parameter List (Visual Basic)</span></span>

<span data-ttu-id="4668f-103">Bir yordamın çağrıldığında beklediği parametreleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="4668f-103">Specifies the parameters a procedure expects when it is called.</span></span> <span data-ttu-id="4668f-104">Birden çok parametre virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="4668f-104">Multiple parameters are separated by commas.</span></span> <span data-ttu-id="4668f-105">Bir parametre için sözdizimi aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4668f-105">The following is the syntax for one parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="4668f-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4668f-106">Syntax</span></span>

```vb
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]
parametername[( )] [ As parametertype ] [ = defaultvalue ]
```

## <a name="parts"></a><span data-ttu-id="4668f-107">Bölümler</span><span class="sxs-lookup"><span data-stu-id="4668f-107">Parts</span></span>

`attributelist`  
<span data-ttu-id="4668f-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="4668f-108">Optional.</span></span> <span data-ttu-id="4668f-109">Bu parametre için uygulanan özniteliklerin listesi.</span><span class="sxs-lookup"><span data-stu-id="4668f-109">List of attributes that apply to this parameter.</span></span> <span data-ttu-id="4668f-110">[Öznitelik listesini](attribute-list.md) açılı ayraçlar (" `<` " ve " `>` ") içine almalısınız.</span><span class="sxs-lookup"><span data-stu-id="4668f-110">You must enclose the [Attribute List](attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>

`Optional`  
<span data-ttu-id="4668f-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="4668f-111">Optional.</span></span> <span data-ttu-id="4668f-112">Yordam çağrıldığında bu parametrenin gerekli değildir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="4668f-112">Specifies that this parameter is not required when the procedure is called.</span></span>

`ByVal`  
<span data-ttu-id="4668f-113">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="4668f-113">Optional.</span></span> <span data-ttu-id="4668f-114">Yordamın, çağıran koddaki karşılık gelen bağımsız değişkeni temel alan değişken öğesini değiştirmez veya yeniden atayacağınızı belirtir.</span><span class="sxs-lookup"><span data-stu-id="4668f-114">Specifies that the procedure cannot replace or reassign the variable element underlying the corresponding argument in the calling code.</span></span>

`ByRef`  
<span data-ttu-id="4668f-115">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="4668f-115">Optional.</span></span> <span data-ttu-id="4668f-116">Yordamın, çağıran koddaki temeldeki değişken öğesini çağıran kodun kendisi ile aynı şekilde değiştirebileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4668f-116">Specifies that the procedure can modify the underlying variable element in the calling code the same way the calling code itself can.</span></span>

`ParamArray`  
<span data-ttu-id="4668f-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="4668f-117">Optional.</span></span> <span data-ttu-id="4668f-118">Parametre listesindeki son parametrenin, belirtilen veri türü için isteğe bağlı bir öğe dizisi olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="4668f-118">Specifies that the last parameter in the parameter list is an optional array of elements of the specified data type.</span></span> <span data-ttu-id="4668f-119">Bu, çağıran kodun yordama rastgele sayıda bağımsız değişken geçirmelerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="4668f-119">This lets the calling code pass an arbitrary number of arguments to the procedure.</span></span>

`parametername`  
<span data-ttu-id="4668f-120">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4668f-120">Required.</span></span> <span data-ttu-id="4668f-121">Parametreyi temsil eden yerel değişkenin adı.</span><span class="sxs-lookup"><span data-stu-id="4668f-121">Name of the local variable representing the parameter.</span></span>

`parametertype`  
<span data-ttu-id="4668f-122">İse gereklidir `Option Strict` `On` .</span><span class="sxs-lookup"><span data-stu-id="4668f-122">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="4668f-123">Parametreyi temsil eden yerel değişkenin veri türü.</span><span class="sxs-lookup"><span data-stu-id="4668f-123">Data type of the local variable representing the parameter.</span></span>

`defaultvalue`  
<span data-ttu-id="4668f-124">Parametreler için gereklidir `Optional` .</span><span class="sxs-lookup"><span data-stu-id="4668f-124">Required for `Optional` parameters.</span></span> <span data-ttu-id="4668f-125">Parametrenin veri türünü değerlendiren herhangi bir sabit veya sabit ifade.</span><span class="sxs-lookup"><span data-stu-id="4668f-125">Any constant or constant expression that evaluates to the data type of the parameter.</span></span> <span data-ttu-id="4668f-126">Tür `Object` veya bir sınıf, arabirim, dizi ya da yapı ise, varsayılan değer yalnızca olabilir `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="4668f-126">If the type is `Object`, or a class, interface, array, or structure, the default value can only be `Nothing`.</span></span>

## <a name="remarks"></a><span data-ttu-id="4668f-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4668f-127">Remarks</span></span>

<span data-ttu-id="4668f-128">Parametreler parantezler ile çevrelenmiş ve virgülle ayrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4668f-128">Parameters are surrounded by parentheses and separated by commas.</span></span> <span data-ttu-id="4668f-129">Bir parametre herhangi bir veri türü ile bildirilebilecek.</span><span class="sxs-lookup"><span data-stu-id="4668f-129">A parameter can be declared with any data type.</span></span> <span data-ttu-id="4668f-130">Belirtmezseniz `parametertype` , varsayılan olarak olur `Object` .</span><span class="sxs-lookup"><span data-stu-id="4668f-130">If you do not specify `parametertype`, it defaults to `Object`.</span></span>

<span data-ttu-id="4668f-131">Çağıran kod yordamı çağırdığında, gerekli her parametreye bir *bağımsız değişken* geçirir.</span><span class="sxs-lookup"><span data-stu-id="4668f-131">When the calling code calls the procedure, it passes an *argument* to each required parameter.</span></span> <span data-ttu-id="4668f-132">Daha fazla bilgi için bkz. [Parametreler ve bağımsız değişkenler arasındaki farklar](../../programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="4668f-132">For more information, see [Differences Between Parameters and Arguments](../../programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).</span></span>

<span data-ttu-id="4668f-133">Çağıran kodun her parametreye geçtiği bağımsız değişken, çağıran koddaki temeldeki öğenin bir işaretçisidir.</span><span class="sxs-lookup"><span data-stu-id="4668f-133">The argument the calling code passes to each parameter is a pointer to an underlying element in the calling code.</span></span> <span data-ttu-id="4668f-134">Bu öğe *değişken olmayan* bir değerse (bir sabit, değişmez değer, sabit listesi veya ifade), herhangi bir kodun değiştirilmesi olanaksızdır.</span><span class="sxs-lookup"><span data-stu-id="4668f-134">If this element is *nonvariable* (a constant, literal, enumeration, or expression), it is impossible for any code to change it.</span></span> <span data-ttu-id="4668f-135">*Değişken* bir öğe ise (belirtilen değişken, alan, özellik, dizi öğesi veya yapı öğesi), çağıran kod değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="4668f-135">If it is a *variable* element (a declared variable, field, property, array element, or structure element), the calling code can change it.</span></span> <span data-ttu-id="4668f-136">Daha fazla bilgi için bkz. [değiştirilebilir ve değiştirilemez bağımsız değişkenler arasındaki farklar](../../programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="4668f-136">For more information, see [Differences Between Modifiable and Nonmodifiable Arguments](../../programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).</span></span>

<span data-ttu-id="4668f-137">Bir değişken öğesi geçmişse `ByRef` , yordam de değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="4668f-137">If a variable element is passed `ByRef`, the procedure can change it as well.</span></span> <span data-ttu-id="4668f-138">Daha fazla bilgi için, [bir bağımsız değişkeni değere ve başvuruya göre geçirme arasındaki farklılıklar](../../programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="4668f-138">For more information, see [Differences Between Passing an Argument By Value and By Reference](../../programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).</span></span>

## <a name="rules"></a><span data-ttu-id="4668f-139">Kurallar</span><span class="sxs-lookup"><span data-stu-id="4668f-139">Rules</span></span>

- <span data-ttu-id="4668f-140">**Ayraçlar.**</span><span class="sxs-lookup"><span data-stu-id="4668f-140">**Parentheses.**</span></span> <span data-ttu-id="4668f-141">Bir parametre listesi belirtirseniz, parantez içine almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4668f-141">If you specify a parameter list, you must enclose it in parentheses.</span></span> <span data-ttu-id="4668f-142">Parametre yoksa boş bir listeyi kapsayan ayraçları kullanmaya devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4668f-142">If there are no parameters, you can still use parentheses enclosing an empty list.</span></span> <span data-ttu-id="4668f-143">Bunun yapılması, öğenin bir yordam olduğunu açıklığa kavuşturarak kodunuzun okunabilirliğini geliştirir.</span><span class="sxs-lookup"><span data-stu-id="4668f-143">This improves the readability of your code by clarifying that the element is a procedure.</span></span>

- <span data-ttu-id="4668f-144">**İsteğe bağlı parametreler.**</span><span class="sxs-lookup"><span data-stu-id="4668f-144">**Optional Parameters.**</span></span> <span data-ttu-id="4668f-145">`Optional`Değiştirici bir parametre üzerinde kullanırsanız, listedeki izleyen tüm parametrelerin da isteğe bağlı olması ve değiştirici kullanılarak bildirilenler gerekir `Optional` .</span><span class="sxs-lookup"><span data-stu-id="4668f-145">If you use the `Optional` modifier on a parameter, all subsequent parameters in the list must also be optional and be declared by using the `Optional` modifier.</span></span>

     <span data-ttu-id="4668f-146">Her isteğe bağlı parametre bildirimi `defaultvalue` yan tümceyi sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="4668f-146">Every optional parameter declaration must supply the `defaultvalue` clause.</span></span>

     <span data-ttu-id="4668f-147">Daha fazla bilgi için bkz. [Isteğe bağlı parametreler](../../programming-guide/language-features/procedures/optional-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="4668f-147">For more information, see [Optional Parameters](../../programming-guide/language-features/procedures/optional-parameters.md).</span></span>

- <span data-ttu-id="4668f-148">**Parametre dizileri.**</span><span class="sxs-lookup"><span data-stu-id="4668f-148">**Parameter Arrays.**</span></span> <span data-ttu-id="4668f-149">`ByVal`Bir parametre için belirtmeniz gerekir `ParamArray` .</span><span class="sxs-lookup"><span data-stu-id="4668f-149">You must specify `ByVal` for a `ParamArray` parameter.</span></span>

     <span data-ttu-id="4668f-150">Hem hem de `Optional` `ParamArray` aynı parametre listesinde kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="4668f-150">You cannot use both `Optional` and `ParamArray` in the same parameter list.</span></span>

     <span data-ttu-id="4668f-151">Daha fazla bilgi için bkz. [parametre dizileri](../../programming-guide/language-features/procedures/parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="4668f-151">For more information, see [Parameter Arrays](../../programming-guide/language-features/procedures/parameter-arrays.md).</span></span>

- <span data-ttu-id="4668f-152">**Geçirme mekanizması.**</span><span class="sxs-lookup"><span data-stu-id="4668f-152">**Passing Mechanism.**</span></span> <span data-ttu-id="4668f-153">Her bağımsız değişken için varsayılan mekanizma, `ByVal` Bu yordamın temel alınan değişken öğesini değiştiremeyeceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="4668f-153">The default mechanism for every argument is `ByVal`, which means the procedure cannot change the underlying variable element.</span></span> <span data-ttu-id="4668f-154">Ancak, öğe bir başvuru türü ise, yordam nesnenin kendisini değiştiremese veya yeniden atanmasa bile, temel nesnenin içeriğini veya üyelerini değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="4668f-154">However, if the element is a reference type, the procedure can modify the contents or members of the underlying object, even though it cannot replace or reassign the object itself.</span></span>

- <span data-ttu-id="4668f-155">**Parametre adları.**</span><span class="sxs-lookup"><span data-stu-id="4668f-155">**Parameter Names.**</span></span> <span data-ttu-id="4668f-156">Parametrenin veri türü bir diziyse, `parametername` hemen parantez ile izleyin.</span><span class="sxs-lookup"><span data-stu-id="4668f-156">If the parameter's data type is an array, follow `parametername` immediately by parentheses.</span></span> <span data-ttu-id="4668f-157">Parametre adları hakkında daha fazla bilgi için bkz. [bildirilmemiş öğe adları](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="4668f-157">For more information on parameter names, see [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

## <a name="example"></a><span data-ttu-id="4668f-158">Örnek</span><span class="sxs-lookup"><span data-stu-id="4668f-158">Example</span></span>

<span data-ttu-id="4668f-159">Aşağıdaki örnekte `Function` iki parametre tanımlayan bir yordam gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4668f-159">The following example shows a `Function` procedure that defines two parameters.</span></span>

[!code-vb[VbVbalrStatements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#2)]

## <a name="see-also"></a><span data-ttu-id="4668f-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4668f-160">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="4668f-161">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="4668f-161">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="4668f-162">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="4668f-162">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="4668f-163">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="4668f-163">Declare Statement</span></span>](declare-statement.md)
- [<span data-ttu-id="4668f-164">Structure Yapısı</span><span class="sxs-lookup"><span data-stu-id="4668f-164">Structure Statement</span></span>](structure-statement.md)
- [<span data-ttu-id="4668f-165">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="4668f-165">Option Strict Statement</span></span>](option-strict-statement.md)
- [<span data-ttu-id="4668f-166">Özniteliklere genel bakış</span><span class="sxs-lookup"><span data-stu-id="4668f-166">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="4668f-167">Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme</span><span class="sxs-lookup"><span data-stu-id="4668f-167">How to: Break and Combine Statements in Code</span></span>](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
