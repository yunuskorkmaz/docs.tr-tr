---
title: Get deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Get
helpviewer_keywords:
- Get statement [Visual Basic], syntax
- Get statement [Visual Basic]
- properties [Visual Basic], read-only
- read-only properties
- Get keyword [Visual Basic]
- property procedures [Visual Basic], Get statements
ms.assetid: 56b05cdc-bd64-4dfd-bb12-824eacec6f94
ms.openlocfilehash: 245d2cc36abde76a8f8bd73bae5d7ede183d4d03
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58840516"
---
# <a name="get-statement"></a><span data-ttu-id="488d3-102">Get Deyimi</span><span class="sxs-lookup"><span data-stu-id="488d3-102">Get Statement</span></span>
<span data-ttu-id="488d3-103">Bildiren bir `Get` özellik yordamı bir özelliğin değerini almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="488d3-103">Declares a `Get` property procedure used to retrieve the value of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="488d3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="488d3-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## <a name="parts"></a><span data-ttu-id="488d3-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="488d3-105">Parts</span></span>  
  
|<span data-ttu-id="488d3-106">Terim</span><span class="sxs-lookup"><span data-stu-id="488d3-106">Term</span></span>|<span data-ttu-id="488d3-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="488d3-107">Definition</span></span>|  
|---|---|  
|`attributelist`|<span data-ttu-id="488d3-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="488d3-108">Optional.</span></span> <span data-ttu-id="488d3-109">Bkz: [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="488d3-109">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>|  
|`accessmodifier`|<span data-ttu-id="488d3-110">İsteğe bağlı biri `Get` ve `Set` bu özellik deyimlerinde.</span><span class="sxs-lookup"><span data-stu-id="488d3-110">Optional on at most one of the `Get` and `Set` statements in this property.</span></span> <span data-ttu-id="488d3-111">Aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="488d3-111">Can be one of the following:</span></span><br /><br /> <span data-ttu-id="488d3-112">-   [Korumalı](../../../visual-basic/language-reference/modifiers/protected.md)</span><span class="sxs-lookup"><span data-stu-id="488d3-112">-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)</span></span><br /><span data-ttu-id="488d3-113">-   [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md)</span><span class="sxs-lookup"><span data-stu-id="488d3-113">-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)</span></span><br /><span data-ttu-id="488d3-114">-   [Özel](../../../visual-basic/language-reference/modifiers/private.md)</span><span class="sxs-lookup"><span data-stu-id="488d3-114">-   [Private](../../../visual-basic/language-reference/modifiers/private.md)</span></span><br />-   `Protected Friend`<br /><br /> <span data-ttu-id="488d3-115">Bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="488d3-115">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`statements`|<span data-ttu-id="488d3-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="488d3-116">Optional.</span></span> <span data-ttu-id="488d3-117">Çalıştırılan bir veya daha fazla deyim `Get` özelliği yordamı çağrılır.</span><span class="sxs-lookup"><span data-stu-id="488d3-117">One or more statements that run when the `Get` property procedure is called.</span></span>|  
|`End Get`|<span data-ttu-id="488d3-118">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="488d3-118">Required.</span></span> <span data-ttu-id="488d3-119">Tanımını sonlandırır `Get` özellik yordamı.</span><span class="sxs-lookup"><span data-stu-id="488d3-119">Terminates the definition of the `Get` property procedure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="488d3-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="488d3-120">Remarks</span></span>  
 <span data-ttu-id="488d3-121">Her özelliği bir `Get` özellik yordamı özelliği işaretlenmediği sürece `WriteOnly`.</span><span class="sxs-lookup"><span data-stu-id="488d3-121">Every property must have a `Get` property procedure unless the property is marked `WriteOnly`.</span></span> <span data-ttu-id="488d3-122">`Get` Yordamı özelliğinin geçerli değeri döndürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="488d3-122">The `Get` procedure is used to return the current value of the property.</span></span>  
  
 <span data-ttu-id="488d3-123">Visual Basic otomatik olarak çağıran bir özelliğin `Get` özelliğinin değeri bir ifade istediğinde yordamı.</span><span class="sxs-lookup"><span data-stu-id="488d3-123">Visual Basic automatically calls a property's `Get` procedure when an expression requests the property's value.</span></span>  
  
 <span data-ttu-id="488d3-124">Özellik bildirimi gövdesi yalnızca özelliğin içerebilir `Get` ve `Set` yordamları arasında [Property deyimi](../../../visual-basic/language-reference/statements/property-statement.md) ve `End Property` deyimi.</span><span class="sxs-lookup"><span data-stu-id="488d3-124">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="488d3-125">Bu yordamlar dışında her şey depolanamıyor.</span><span class="sxs-lookup"><span data-stu-id="488d3-125">It cannot store anything other than those procedures.</span></span> <span data-ttu-id="488d3-126">Özellikle, bu özelliğin geçerli değerini depolanamıyor.</span><span class="sxs-lookup"><span data-stu-id="488d3-126">In particular, it cannot store the property's current value.</span></span> <span data-ttu-id="488d3-127">Özellik yordamları birini içinde depolamak, bir özellik yordamı, erişemediği için bu değer özelliği dışında depolamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="488d3-127">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span></span> <span data-ttu-id="488d3-128">Değeri depolamak için her zamanki yaklaşımdır bir [özel](../../../visual-basic/language-reference/modifiers/private.md) bildirilen değişkenin özelliği ile aynı düzeyde.</span><span class="sxs-lookup"><span data-stu-id="488d3-128">The usual approach is to store the value in a [Private](../../../visual-basic/language-reference/modifiers/private.md) variable declared at the same level as the property.</span></span> <span data-ttu-id="488d3-129">Tanımlamanız gerekir bir `Get` yordam içinde geçerli olduğu özellik.</span><span class="sxs-lookup"><span data-stu-id="488d3-129">You must define a `Get` procedure inside the property to which it applies.</span></span>  
  
 <span data-ttu-id="488d3-130">`Get` Yordamı kullanmadığınız sürece, kapsayan özelliği erişim düzeyi için varsayılan olarak `accessmodifier` içinde `Get` deyimi.</span><span class="sxs-lookup"><span data-stu-id="488d3-130">The `Get` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Get` statement.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="488d3-131">Kurallar</span><span class="sxs-lookup"><span data-stu-id="488d3-131">Rules</span></span>  
  
-   <span data-ttu-id="488d3-132">**Karışık erişim düzeyleri.**</span><span class="sxs-lookup"><span data-stu-id="488d3-132">**Mixed Access Levels.**</span></span> <span data-ttu-id="488d3-133">Okuma-yazma özelliği tanımlıyorsanız, isteğe bağlı olarak farklı erişim düzeyi için belirtebilirsiniz `Get` veya `Set` yordamı, ancak ikisine birden değil.</span><span class="sxs-lookup"><span data-stu-id="488d3-133">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="488d3-134">Bunu yaparsanız, yordam erişim düzeyi özellik erişim düzeyinden daha kısıtlayıcı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="488d3-134">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="488d3-135">Örneğin, özellik bildirilirse `Friend`, bildirebilirsiniz `Get` yordamı `Private`, ama `Public`.</span><span class="sxs-lookup"><span data-stu-id="488d3-135">For example, if the property is declared `Friend`, you can declare the `Get` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="488d3-136">Tanımlıyorsanız, bir `ReadOnly` özelliği `Get` yordamı tüm özelliği temsil eder.</span><span class="sxs-lookup"><span data-stu-id="488d3-136">If you are defining a `ReadOnly` property, the `Get` procedure represents the entire property.</span></span> <span data-ttu-id="488d3-137">Farklı bir erişim düzeyini bildiremezsiniz `Get`, iki erişim düzeyi özelliği ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="488d3-137">You cannot declare a different access level for `Get`, because that would set two access levels for the property.</span></span>  
  
-   <span data-ttu-id="488d3-138">**Dönüş türü.**</span><span class="sxs-lookup"><span data-stu-id="488d3-138">**Return Type.**</span></span> <span data-ttu-id="488d3-139">[Property deyimi](../../../visual-basic/language-reference/statements/property-statement.md) döndürdüğü değerin veri türü bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="488d3-139">The [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) can declare the data type of the value it returns.</span></span> <span data-ttu-id="488d3-140">`Get` Yordamı otomatik olarak döndürür veri türü.</span><span class="sxs-lookup"><span data-stu-id="488d3-140">The `Get` procedure automatically returns that data type.</span></span> <span data-ttu-id="488d3-141">Herhangi bir veri türü veya bir sabit listesi, yapısı, sınıf veya arabirim adını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="488d3-141">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
     <span data-ttu-id="488d3-142">Varsa `Property` deyimi belirtmiyor `returntype`, yordam döndürür `Object`.</span><span class="sxs-lookup"><span data-stu-id="488d3-142">If the `Property` statement does not specify `returntype`, the procedure returns `Object`.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="488d3-143">Davranış</span><span class="sxs-lookup"><span data-stu-id="488d3-143">Behavior</span></span>  
  
-   <span data-ttu-id="488d3-144">**Bir yordam döndürüyor.**</span><span class="sxs-lookup"><span data-stu-id="488d3-144">**Returning from a Procedure.**</span></span> <span data-ttu-id="488d3-145">Zaman `Get` yordamı çağıran koda döndürür, özellik değeri istenen deyimi içinde yürütme devam eder.</span><span class="sxs-lookup"><span data-stu-id="488d3-145">When the `Get` procedure returns to the calling code, execution continues within the statement that requested the property value.</span></span>  
  
     <span data-ttu-id="488d3-146">`Get` özellik yordamları kullanarak bir değer döndürebilir [dönüş deyimi](../../../visual-basic/language-reference/statements/return-statement.md) ya da dönüş değeri, özellik adına atayarak.</span><span class="sxs-lookup"><span data-stu-id="488d3-146">`Get` property procedures can return a value using either the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) or by assigning the return value to the property name.</span></span> <span data-ttu-id="488d3-147">Daha fazla bilgi için bkz: "Value dönüş" [Function deyimi](../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="488d3-147">For more information, see "Return Value" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
     <span data-ttu-id="488d3-148">`Exit Property` Ve `Return` deyimleri neden hemen bir çıkış bir özellik yordamı.</span><span class="sxs-lookup"><span data-stu-id="488d3-148">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="488d3-149">Herhangi bir sayıda `Exit Property` ve `Return` deyimleri yordamda herhangi bir yerinde görünebilir ve karıştırabilir miyim `Exit Property` ve `Return` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="488d3-149">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
-   <span data-ttu-id="488d3-150">**Dönüş değeri.**</span><span class="sxs-lookup"><span data-stu-id="488d3-150">**Return Value.**</span></span> <span data-ttu-id="488d3-151">Bir değer döndürmek için bir `Get` yordam, özellik adı için değer atamak veya olmasını bir [dönüş deyimi](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="488d3-151">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span> <span data-ttu-id="488d3-152">`Return` Deyimi aynı anda atar `Get` yordamı dönüş değeri ve yordamdan çıkar.</span><span class="sxs-lookup"><span data-stu-id="488d3-152">The `Return` statement simultaneously assigns the `Get` procedure return value and exits the procedure.</span></span>  
  
     <span data-ttu-id="488d3-153">Kullanırsanız `Exit Property` özellik adı için bir değer atama olmadan `Get` yordamı özelliğin veri türü için varsayılan değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="488d3-153">If you use `Exit Property` without assigning a value to the property name, the `Get` procedure returns the default value for the property's data type.</span></span> <span data-ttu-id="488d3-154">Daha fazla bilgi için bkz: "Value dönüş" [Function deyimi](../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="488d3-154">For more information, see "Return Value" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
     <span data-ttu-id="488d3-155">Aşağıdaki örnekte iki şekilde salt okunur özelliği `quoteForTheDay` özel değişkeninde tuttuğu değeri döndürebilir `quoteValue`.</span><span class="sxs-lookup"><span data-stu-id="488d3-155">The following example illustrates two ways the read-only property `quoteForTheDay` can return the value held in the private variable `quoteValue`.</span></span>  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]  
  
     [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]  
  
## <a name="example"></a><span data-ttu-id="488d3-156">Örnek</span><span class="sxs-lookup"><span data-stu-id="488d3-156">Example</span></span>  
 <span data-ttu-id="488d3-157">Aşağıdaki örnekte `Get` deyimini bir özelliğinin değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="488d3-157">The following example uses the `Get` statement to return the value of a property.</span></span>  
  
 [!code-vb[VbVbalrStatements#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="488d3-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="488d3-158">See also</span></span>

- [<span data-ttu-id="488d3-159">Set Deyimi</span><span class="sxs-lookup"><span data-stu-id="488d3-159">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
- [<span data-ttu-id="488d3-160">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="488d3-160">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="488d3-161">Exit Deyimi</span><span class="sxs-lookup"><span data-stu-id="488d3-161">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="488d3-162">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="488d3-162">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="488d3-163">İzlenecek yol: Sınıfları tanımlama</span><span class="sxs-lookup"><span data-stu-id="488d3-163">Walkthrough: Defining Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)
