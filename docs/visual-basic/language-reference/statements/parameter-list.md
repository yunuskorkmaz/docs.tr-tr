---
title: Parametre Listesi (Visual Basic)
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
ms.openlocfilehash: e58d80896d11b4154c7197d4cdaf73a536fdd5e7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64583556"
---
# <a name="parameter-list-visual-basic"></a><span data-ttu-id="da390-102">Parametre Listesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="da390-102">Parameter List (Visual Basic)</span></span>
<span data-ttu-id="da390-103">Bir yordam çağrıldığında bu bekliyor parametreleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="da390-103">Specifies the parameters a procedure expects when it is called.</span></span> <span data-ttu-id="da390-104">Birden çok parametre, virgüllerle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="da390-104">Multiple parameters are separated by commas.</span></span> <span data-ttu-id="da390-105">Bir parametre için sözdizimi aşağıdadır.</span><span class="sxs-lookup"><span data-stu-id="da390-105">The following is the syntax for one parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da390-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="da390-106">Syntax</span></span>  
  
```  
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]   
parametername[( )] [ As parametertype ] [ = defaultvalue ]  
```  
  
## <a name="parts"></a><span data-ttu-id="da390-107">Bölümler</span><span class="sxs-lookup"><span data-stu-id="da390-107">Parts</span></span>  
 `attributelist`  
 <span data-ttu-id="da390-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="da390-108">Optional.</span></span> <span data-ttu-id="da390-109">Bu parametre için geçerli olan özniteliklerin listesi.</span><span class="sxs-lookup"><span data-stu-id="da390-109">List of attributes that apply to this parameter.</span></span> <span data-ttu-id="da390-110">İçine almalısınız [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md) açılı ayraçlar içinde ("`<`"ve"`>`").</span><span class="sxs-lookup"><span data-stu-id="da390-110">You must enclose the [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>  
  
 `Optional`  
 <span data-ttu-id="da390-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="da390-111">Optional.</span></span> <span data-ttu-id="da390-112">Yordam çağrıldığında Bu parametre gerekli olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="da390-112">Specifies that this parameter is not required when the procedure is called.</span></span>  
  
 `ByVal`  
 <span data-ttu-id="da390-113">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="da390-113">Optional.</span></span> <span data-ttu-id="da390-114">Yordam olamaz değiştirin veya karşılık gelen bağımsız değişkenin çağıran koddaki temel değişken öğe yeniden atama belirtir.</span><span class="sxs-lookup"><span data-stu-id="da390-114">Specifies that the procedure cannot replace or reassign the variable element underlying the corresponding argument in the calling code.</span></span>  
  
 `ByRef`  
 <span data-ttu-id="da390-115">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="da390-115">Optional.</span></span> <span data-ttu-id="da390-116">Yordam aynı şekilde çağıran kod çağıran koddaki değişken öğe türüdür değiştirebilirsiniz belirtir.</span><span class="sxs-lookup"><span data-stu-id="da390-116">Specifies that the procedure can modify the underlying variable element in the calling code the same way the calling code itself can.</span></span>  
  
 `ParamArray`  
 <span data-ttu-id="da390-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="da390-117">Optional.</span></span> <span data-ttu-id="da390-118">Belirtilen veri türü öğeler için isteğe bağlı bir dizi parametre listesindeki son parametre olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="da390-118">Specifies that the last parameter in the parameter list is an optional array of elements of the specified data type.</span></span> <span data-ttu-id="da390-119">Bu yordama bağımsız değişkenler rastgele bir sayıdan geçirmek çağıran kod sağlar.</span><span class="sxs-lookup"><span data-stu-id="da390-119">This lets the calling code pass an arbitrary number of arguments to the procedure.</span></span>  
  
 `parametername`  
 <span data-ttu-id="da390-120">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="da390-120">Required.</span></span> <span data-ttu-id="da390-121">Parametreyi temsil eden yerel değişkenin adı.</span><span class="sxs-lookup"><span data-stu-id="da390-121">Name of the local variable representing the parameter.</span></span>  
  
 `parametertype`  
 <span data-ttu-id="da390-122">Gerekli if `Option Strict` olduğu `On`.</span><span class="sxs-lookup"><span data-stu-id="da390-122">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="da390-123">Parametreyi temsil eden yerel değişken veri türü.</span><span class="sxs-lookup"><span data-stu-id="da390-123">Data type of the local variable representing the parameter.</span></span>  
  
 `defaultvalue`  
 <span data-ttu-id="da390-124">Gerekli `Optional` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="da390-124">Required for `Optional` parameters.</span></span> <span data-ttu-id="da390-125">Parametrenin veri türü için değerlendirilen tüm sabit veya sabit ifade.</span><span class="sxs-lookup"><span data-stu-id="da390-125">Any constant or constant expression that evaluates to the data type of the parameter.</span></span> <span data-ttu-id="da390-126">Tür ise `Object`, veya bir sınıf, arabirim, dizi veya yapı, varsayılan değer yalnızca olabilir `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="da390-126">If the type is `Object`, or a class, interface, array, or structure, the default value can only be `Nothing`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da390-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="da390-127">Remarks</span></span>  
 <span data-ttu-id="da390-128">Parametreleri parantez içine ve virgülle ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="da390-128">Parameters are surrounded by parentheses and separated by commas.</span></span> <span data-ttu-id="da390-129">Bir parametre herhangi bir veri türü ile bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="da390-129">A parameter can be declared with any data type.</span></span> <span data-ttu-id="da390-130">Siz belirtmezseniz `parametertype`, varsayılan `Object`.</span><span class="sxs-lookup"><span data-stu-id="da390-130">If you do not specify `parametertype`, it defaults to `Object`.</span></span>  
  
 <span data-ttu-id="da390-131">Çağıran kod yordamı çağırdığında arabimini bir *bağımsız değişken* her gerekli parametre.</span><span class="sxs-lookup"><span data-stu-id="da390-131">When the calling code calls the procedure, it passes an *argument* to each required parameter.</span></span> <span data-ttu-id="da390-132">Daha fazla bilgi için [arasındaki farklar parametreler ve bağımsız değişkenler](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="da390-132">For more information, see [Differences Between Parameters and Arguments](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).</span></span>  
  
 <span data-ttu-id="da390-133">Çağıran kod her parametreye geçirmeden bağımsız değişken temel alınan bir öğe çağıran koddaki bir işaretçisidir.</span><span class="sxs-lookup"><span data-stu-id="da390-133">The argument the calling code passes to each parameter is a pointer to an underlying element in the calling code.</span></span> <span data-ttu-id="da390-134">Bu öğe ise *nonvariable* (bir sabit, değişmez değeri, numaralandırma veya ifade), değiştirmek herhangi bir kod için mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="da390-134">If this element is *nonvariable* (a constant, literal, enumeration, or expression), it is impossible for any code to change it.</span></span> <span data-ttu-id="da390-135">Eğer öyleyse bir *değişkeni* öğesi (bir bildirilmiş bir değişken, alan, özelliği, dizi öğesi veya yapı öğesi), çağıran kodun bunu değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da390-135">If it is a *variable* element (a declared variable, field, property, array element, or structure element), the calling code can change it.</span></span> <span data-ttu-id="da390-136">Daha fazla bilgi için [arasındaki farklar değiştirilebilir ve değiştirilemez bağımsız değişkenler](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="da390-136">For more information, see [Differences Between Modifiable and Nonmodifiable Arguments](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).</span></span>  
  
 <span data-ttu-id="da390-137">Bir değişken öğesi iletilmezse `ByRef`, yordam de değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da390-137">If a variable element is passed `ByRef`, the procedure can change it as well.</span></span> <span data-ttu-id="da390-138">Daha fazla bilgi için [farklar arasında geçen bir bağımsız değişken değer ve başvuru tarafından](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).</span><span class="sxs-lookup"><span data-stu-id="da390-138">For more information, see [Differences Between Passing an Argument By Value and By Reference](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="da390-139">Kurallar</span><span class="sxs-lookup"><span data-stu-id="da390-139">Rules</span></span>  
  
- <span data-ttu-id="da390-140">**Parantezler.**</span><span class="sxs-lookup"><span data-stu-id="da390-140">**Parentheses.**</span></span> <span data-ttu-id="da390-141">Parametre listesi belirtirseniz, parantez içine almalısınız.</span><span class="sxs-lookup"><span data-stu-id="da390-141">If you specify a parameter list, you must enclose it in parentheses.</span></span> <span data-ttu-id="da390-142">Hiçbir parametre varsa, boş bir liste çevreleyen parantezler kullanmaya devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da390-142">If there are no parameters, you can still use parentheses enclosing an empty list.</span></span> <span data-ttu-id="da390-143">Bu öğe bir yordam olduğunu açıklığa kavuşturan tarafından kodunuzun okunabilirliği geliştirir.</span><span class="sxs-lookup"><span data-stu-id="da390-143">This improves the readability of your code by clarifying that the element is a procedure.</span></span>  
  
- <span data-ttu-id="da390-144">**İsteğe bağlı parametreler.**</span><span class="sxs-lookup"><span data-stu-id="da390-144">**Optional Parameters.**</span></span> <span data-ttu-id="da390-145">Kullanırsanız `Optional` bir parametre değiştiricisi, sonraki tüm parametreler listesinde isteğe bağlı olmalıdır ve kullanılarak bildirilen `Optional` değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="da390-145">If you use the `Optional` modifier on a parameter, all subsequent parameters in the list must also be optional and be declared by using the `Optional` modifier.</span></span>  
  
     <span data-ttu-id="da390-146">Her isteğe bağlı parametre bildirimi sağlamalısınız `defaultvalue` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="da390-146">Every optional parameter declaration must supply the `defaultvalue` clause.</span></span>  
  
     <span data-ttu-id="da390-147">Daha fazla bilgi için [isteğe bağlı parametreler](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="da390-147">For more information, see [Optional Parameters](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md).</span></span>  
  
- <span data-ttu-id="da390-148">**Parametre dizileri.**</span><span class="sxs-lookup"><span data-stu-id="da390-148">**Parameter Arrays.**</span></span> <span data-ttu-id="da390-149">Belirtmelisiniz `ByVal` için bir `ParamArray` parametresi.</span><span class="sxs-lookup"><span data-stu-id="da390-149">You must specify `ByVal` for a `ParamArray` parameter.</span></span>  
  
     <span data-ttu-id="da390-150">Her ikisini birden kullanamazsınız `Optional` ve `ParamArray` aynı parametre listesinde.</span><span class="sxs-lookup"><span data-stu-id="da390-150">You cannot use both `Optional` and `ParamArray` in the same parameter list.</span></span>  
  
     <span data-ttu-id="da390-151">Daha fazla bilgi için [parametre dizileri](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="da390-151">For more information, see [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span></span>  
  
- <span data-ttu-id="da390-152">**Geçirme mekanizması.**</span><span class="sxs-lookup"><span data-stu-id="da390-152">**Passing Mechanism.**</span></span> <span data-ttu-id="da390-153">Her bağımsız değişken için varsayılan mekanizmasıdır `ByVal`, yordam başka bir deyişle, temel alınan değişken öğesini değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="da390-153">The default mechanism for every argument is `ByVal`, which means the procedure cannot change the underlying variable element.</span></span> <span data-ttu-id="da390-154">Öğeye bir başvuru türü ise, değiştirin veya nesneyi yeniden atama olsa bile ancak yordamı içeriği veya temel alınan bir nesnenin üyelerine değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da390-154">However, if the element is a reference type, the procedure can modify the contents or members of the underlying object, even though it cannot replace or reassign the object itself.</span></span>  
  
- <span data-ttu-id="da390-155">**Parametre adları.**</span><span class="sxs-lookup"><span data-stu-id="da390-155">**Parameter Names.**</span></span> <span data-ttu-id="da390-156">Parametrenin veri türü bir dizi ise izleyin `parametername` parantez tarafından hemen.</span><span class="sxs-lookup"><span data-stu-id="da390-156">If the parameter's data type is an array, follow `parametername` immediately by parentheses.</span></span> <span data-ttu-id="da390-157">Parametre adları hakkında daha fazla bilgi için bkz. [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="da390-157">For more information on parameter names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="da390-158">Örnek</span><span class="sxs-lookup"><span data-stu-id="da390-158">Example</span></span>  
 <span data-ttu-id="da390-159">Aşağıdaki örnekte gösterildiği bir `Function` iki parametre tanımlayan yordamı.</span><span class="sxs-lookup"><span data-stu-id="da390-159">The following example shows a `Function` procedure that defines two parameters.</span></span>  
  
 [!code-vb[VbVbalrStatements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="da390-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da390-160">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="da390-161">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="da390-161">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="da390-162">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="da390-162">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="da390-163">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="da390-163">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="da390-164">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="da390-164">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="da390-165">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="da390-165">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="da390-166">Öznitelikler genel bakış</span><span class="sxs-lookup"><span data-stu-id="da390-166">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="da390-167">Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme</span><span class="sxs-lookup"><span data-stu-id="da390-167">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
