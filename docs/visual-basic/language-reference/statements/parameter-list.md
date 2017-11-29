---
title: Parametre Listesi (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic
- parameters [Visual Basic], lists
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- arguments [Visual Basic], Visual Basic
- procedures [Visual Basic], parameter lists
ms.assetid: 5d737319-0c34-4df9-a23d-188fc840becd
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2c7190b618aa98c91b826ca7c065660d3b19c31a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="parameter-list-visual-basic"></a><span data-ttu-id="e5a64-102">Parametre Listesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5a64-102">Parameter List (Visual Basic)</span></span>
<span data-ttu-id="e5a64-103">Bunu çağrıldığında bir yordam bekliyor parametreleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5a64-103">Specifies the parameters a procedure expects when it is called.</span></span> <span data-ttu-id="e5a64-104">Birden çok parametre virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="e5a64-104">Multiple parameters are separated by commas.</span></span> <span data-ttu-id="e5a64-105">Bir parametre sözdizimi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e5a64-105">The following is the syntax for one parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5a64-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e5a64-106">Syntax</span></span>  
  
```  
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]   
parametername[( )] [ As parametertype ] [ = defaultvalue ]  
```  
  
## <a name="parts"></a><span data-ttu-id="e5a64-107">Bölümler</span><span class="sxs-lookup"><span data-stu-id="e5a64-107">Parts</span></span>  
 `attributelist`  
 <span data-ttu-id="e5a64-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e5a64-108">Optional.</span></span> <span data-ttu-id="e5a64-109">Bu parametre için geçerli öznitelikler listesi.</span><span class="sxs-lookup"><span data-stu-id="e5a64-109">List of attributes that apply to this parameter.</span></span> <span data-ttu-id="e5a64-110">İçine almalısınız [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md) açılı ayraç ("`<`"ve"`>`").</span><span class="sxs-lookup"><span data-stu-id="e5a64-110">You must enclose the [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>  
  
 `Optional`  
 <span data-ttu-id="e5a64-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e5a64-111">Optional.</span></span> <span data-ttu-id="e5a64-112">Yordam çağrıldığında, bu parametre gerekli olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5a64-112">Specifies that this parameter is not required when the procedure is called.</span></span>  
  
 `ByVal`  
 <span data-ttu-id="e5a64-113">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e5a64-113">Optional.</span></span> <span data-ttu-id="e5a64-114">Yordamı olamaz veya Değiştir çağıran kodu karşılık gelen değişkeninde temel değişken öğesi yeniden atama belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5a64-114">Specifies that the procedure cannot replace or reassign the variable element underlying the corresponding argument in the calling code.</span></span>  
  
 `ByRef`  
 <span data-ttu-id="e5a64-115">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e5a64-115">Optional.</span></span> <span data-ttu-id="e5a64-116">Yordamı çağıran kod aynı şekilde çağıran kodu temel değişken öğesinde değiştirebilirsiniz belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5a64-116">Specifies that the procedure can modify the underlying variable element in the calling code the same way the calling code itself can.</span></span>  
  
 `ParamArray`  
 <span data-ttu-id="e5a64-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e5a64-117">Optional.</span></span> <span data-ttu-id="e5a64-118">Parametre listesi son parametresinde belirtilen veri türündeki öğeler isteğe bağlı bir dizi olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5a64-118">Specifies that the last parameter in the parameter list is an optional array of elements of the specified data type.</span></span> <span data-ttu-id="e5a64-119">Bu yordama rastgele sayıda bağımsız değişken geçirme çağıran kodu sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5a64-119">This lets the calling code pass an arbitrary number of arguments to the procedure.</span></span>  
  
 `parametername`  
 <span data-ttu-id="e5a64-120">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="e5a64-120">Required.</span></span> <span data-ttu-id="e5a64-121">Parametreyi temsil eden yerel değişkeninin adı.</span><span class="sxs-lookup"><span data-stu-id="e5a64-121">Name of the local variable representing the parameter.</span></span>  
  
 `parametertype`  
 <span data-ttu-id="e5a64-122">Gerekli olursa `Option Strict` olan `On`.</span><span class="sxs-lookup"><span data-stu-id="e5a64-122">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="e5a64-123">Parametreyi temsil eden yerel değişken veri türü.</span><span class="sxs-lookup"><span data-stu-id="e5a64-123">Data type of the local variable representing the parameter.</span></span>  
  
 `defaultvalue`  
 <span data-ttu-id="e5a64-124">İçin gerekli `Optional` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="e5a64-124">Required for `Optional` parameters.</span></span> <span data-ttu-id="e5a64-125">Parametresinin veri türü değerlendiren herhangi sabit veya sabit bir ifade.</span><span class="sxs-lookup"><span data-stu-id="e5a64-125">Any constant or constant expression that evaluates to the data type of the parameter.</span></span> <span data-ttu-id="e5a64-126">Tür ise `Object`, ya da bir sınıf, arabirim, dizi veya yapısı, varsayılan değer yalnızca olabilir `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="e5a64-126">If the type is `Object`, or a class, interface, array, or structure, the default value can only be `Nothing`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5a64-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e5a64-127">Remarks</span></span>  
 <span data-ttu-id="e5a64-128">Parametreleri ayraç içinde kullanılması ve virgülle ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="e5a64-128">Parameters are surrounded by parentheses and separated by commas.</span></span> <span data-ttu-id="e5a64-129">Bir parametre ile herhangi bir veri türü bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="e5a64-129">A parameter can be declared with any data type.</span></span> <span data-ttu-id="e5a64-130">Belirtmezseniz, `parametertype`, onu varsayılan olarak `Object`.</span><span class="sxs-lookup"><span data-stu-id="e5a64-130">If you do not specify `parametertype`, it defaults to `Object`.</span></span>  
  
 <span data-ttu-id="e5a64-131">Çağıran kodu yordamı çağırdığında geçirmeden bir *bağımsız değişkeni* her gerekli parametre için.</span><span class="sxs-lookup"><span data-stu-id="e5a64-131">When the calling code calls the procedure, it passes an *argument* to each required parameter.</span></span> <span data-ttu-id="e5a64-132">Daha fazla bilgi için bkz: [arasındaki farklar parametreler ve bağımsız değişkenler](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="e5a64-132">For more information, see [Differences Between Parameters and Arguments](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).</span></span>  
  
 <span data-ttu-id="e5a64-133">Her bir parametreyi çağıran kodu geçirmeden bağımsız değişkeni, çağıran kodun temel bir öğe için bir işaretçidir.</span><span class="sxs-lookup"><span data-stu-id="e5a64-133">The argument the calling code passes to each parameter is a pointer to an underlying element in the calling code.</span></span> <span data-ttu-id="e5a64-134">Bu öğe ise *nonvariable* (bir sabit değişmez değeri, numaralandırma veya ifadesi), bunu değiştirmek için herhangi bir kod için mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="e5a64-134">If this element is *nonvariable* (a constant, literal, enumeration, or expression), it is impossible for any code to change it.</span></span> <span data-ttu-id="e5a64-135">Eğer öyleyse bir *değişkeni* öğesi (bir bildirilen değişkeni, alan, özellik, dizi öğesi veya yapı öğesi), çağrıyı yapan kod bunu değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5a64-135">If it is a *variable* element (a declared variable, field, property, array element, or structure element), the calling code can change it.</span></span> <span data-ttu-id="e5a64-136">Daha fazla bilgi için bkz: [arasındaki farklar değiştirilebilir ve değiştirilemez bağımsız değişkenler](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="e5a64-136">For more information, see [Differences Between Modifiable and Nonmodifiable Arguments](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).</span></span>  
  
 <span data-ttu-id="e5a64-137">Bir değişken öğesi aktarılırsa `ByRef`, yordamı da değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5a64-137">If a variable element is passed `ByRef`, the procedure can change it as well.</span></span> <span data-ttu-id="e5a64-138">Daha fazla bilgi için bkz: [farklar arasında geçirme bir bağımsız değişken değer ve başvuru tarafından](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).</span><span class="sxs-lookup"><span data-stu-id="e5a64-138">For more information, see [Differences Between Passing an Argument By Value and By Reference](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="e5a64-139">Kurallar</span><span class="sxs-lookup"><span data-stu-id="e5a64-139">Rules</span></span>  
  
-   <span data-ttu-id="e5a64-140">**Parantez.**</span><span class="sxs-lookup"><span data-stu-id="e5a64-140">**Parentheses.**</span></span> <span data-ttu-id="e5a64-141">Parametre listesi belirtirseniz, parantez içine almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e5a64-141">If you specify a parameter list, you must enclose it in parentheses.</span></span> <span data-ttu-id="e5a64-142">Hiçbir parametre varsa, boş bir liste kapsayan parantez kullanmaya devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5a64-142">If there are no parameters, you can still use parentheses enclosing an empty list.</span></span> <span data-ttu-id="e5a64-143">Bu öğe bir yordam olduğunu açıklığa kavuşturan tarafından kodunuzun okunabilirliğini artırır.</span><span class="sxs-lookup"><span data-stu-id="e5a64-143">This improves the readability of your code by clarifying that the element is a procedure.</span></span>  
  
-   <span data-ttu-id="e5a64-144">**İsteğe bağlı parametreler.**</span><span class="sxs-lookup"><span data-stu-id="e5a64-144">**Optional Parameters.**</span></span> <span data-ttu-id="e5a64-145">Kullanırsanız `Optional` parametresi değiştiricisi, listedeki sonraki tüm parametreler isteğe bağlı olmalıdır ve kullanarak bildirilmesi `Optional` değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="e5a64-145">If you use the `Optional` modifier on a parameter, all subsequent parameters in the list must also be optional and be declared by using the `Optional` modifier.</span></span>  
  
     <span data-ttu-id="e5a64-146">Her isteğe bağlı parametre bildirimi sağlamalısınız `defaultvalue` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="e5a64-146">Every optional parameter declaration must supply the `defaultvalue` clause.</span></span>  
  
     <span data-ttu-id="e5a64-147">Daha fazla bilgi için bkz: [isteğe bağlı parametreler](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="e5a64-147">For more information, see [Optional Parameters](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md).</span></span>  
  
-   <span data-ttu-id="e5a64-148">**Parametre dizileri.**</span><span class="sxs-lookup"><span data-stu-id="e5a64-148">**Parameter Arrays.**</span></span> <span data-ttu-id="e5a64-149">Belirtmeniz gerekir `ByVal` için bir `ParamArray` parametresi.</span><span class="sxs-lookup"><span data-stu-id="e5a64-149">You must specify `ByVal` for a `ParamArray` parameter.</span></span>  
  
     <span data-ttu-id="e5a64-150">Her ikisini birden kullanamazsınız `Optional` ve `ParamArray` aynı parametre listesinde.</span><span class="sxs-lookup"><span data-stu-id="e5a64-150">You cannot use both `Optional` and `ParamArray` in the same parameter list.</span></span>  
  
     <span data-ttu-id="e5a64-151">Daha fazla bilgi için bkz: [parametre dizileri](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="e5a64-151">For more information, see [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span></span>  
  
-   <span data-ttu-id="e5a64-152">**Geçirme mekanizması.**</span><span class="sxs-lookup"><span data-stu-id="e5a64-152">**Passing Mechanism.**</span></span> <span data-ttu-id="e5a64-153">Her bağımsız değişkeni için varsayılan mekanizmasıdır `ByVal`, yordam başka bir deyişle, temel alınan değişken öğesini değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5a64-153">The default mechanism for every argument is `ByVal`, which means the procedure cannot change the underlying variable element.</span></span> <span data-ttu-id="e5a64-154">Öğesi bir başvuru türü ise, değiştirir veya nesneyi yeniden olsa bile ancak yordamı içeriği veya temel alınan nesnenin üyelerine değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5a64-154">However, if the element is a reference type, the procedure can modify the contents or members of the underlying object, even though it cannot replace or reassign the object itself.</span></span>  
  
-   <span data-ttu-id="e5a64-155">**Parametre adları.**</span><span class="sxs-lookup"><span data-stu-id="e5a64-155">**Parameter Names.**</span></span> <span data-ttu-id="e5a64-156">Parametrenin veri türü bir dizi ise izleyin `parametername` parantez göre hemen.</span><span class="sxs-lookup"><span data-stu-id="e5a64-156">If the parameter's data type is an array, follow `parametername` immediately by parentheses.</span></span> <span data-ttu-id="e5a64-157">Parametre adları hakkında daha fazla bilgi için bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="e5a64-157">For more information on parameter names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5a64-158">Örnek</span><span class="sxs-lookup"><span data-stu-id="e5a64-158">Example</span></span>  
 <span data-ttu-id="e5a64-159">Aşağıdaki örnekte gösterildiği bir `Function` iki parametreyi tanımlayan yordamı.</span><span class="sxs-lookup"><span data-stu-id="e5a64-159">The following example shows a `Function` procedure that defines two parameters.</span></span>  
  
 [!code-vb[VbVbalrStatements#2](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/parameter-list_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e5a64-160">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e5a64-160">See Also</span></span>  
 <xref:System.Runtime.InteropServices.DllImportAttribute>  
 [<span data-ttu-id="e5a64-161">Function deyimi</span><span class="sxs-lookup"><span data-stu-id="e5a64-161">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="e5a64-162">Sub deyimi</span><span class="sxs-lookup"><span data-stu-id="e5a64-162">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="e5a64-163">Declare deyimi</span><span class="sxs-lookup"><span data-stu-id="e5a64-163">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [<span data-ttu-id="e5a64-164">Structure deyimi</span><span class="sxs-lookup"><span data-stu-id="e5a64-164">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="e5a64-165">Option Strict deyimi</span><span class="sxs-lookup"><span data-stu-id="e5a64-165">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="e5a64-166">Öznitelikler genel bakış</span><span class="sxs-lookup"><span data-stu-id="e5a64-166">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)  
 [<span data-ttu-id="e5a64-167">Nasıl yapılır: kodda deyimleri bölme ve birleştirme</span><span class="sxs-lookup"><span data-stu-id="e5a64-167">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
