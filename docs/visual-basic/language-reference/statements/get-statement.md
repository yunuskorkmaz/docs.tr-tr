---
title: Get açıklaması (Visual Basic)
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
ms.openlocfilehash: d76155b8ff29e4f5e9206ae8fc689fa4fcaf3b8c
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581829"
---
# <a name="get-statement"></a><span data-ttu-id="e532c-102">Get Deyimi</span><span class="sxs-lookup"><span data-stu-id="e532c-102">Get Statement</span></span>
<span data-ttu-id="e532c-103">Bir özelliğin değerini almak için kullanılan bir `Get` özellik yordamı bildirir.</span><span class="sxs-lookup"><span data-stu-id="e532c-103">Declares a `Get` property procedure used to retrieve the value of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e532c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e532c-104">Syntax</span></span>  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## <a name="parts"></a><span data-ttu-id="e532c-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="e532c-105">Parts</span></span>  
  
|<span data-ttu-id="e532c-106">Terim</span><span class="sxs-lookup"><span data-stu-id="e532c-106">Term</span></span>|<span data-ttu-id="e532c-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="e532c-107">Definition</span></span>|  
|---|---|  
|`attributelist`|<span data-ttu-id="e532c-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e532c-108">Optional.</span></span> <span data-ttu-id="e532c-109">Bkz. [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="e532c-109">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>|  
|`accessmodifier`|<span data-ttu-id="e532c-110">Bu özelliğindeki `Get` ve `Set` deyimlerinin en az birinde isteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e532c-110">Optional on at most one of the `Get` and `Set` statements in this property.</span></span> <span data-ttu-id="e532c-111">Aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="e532c-111">Can be one of the following:</span></span><br /><br /> <span data-ttu-id="e532c-112">-   [korumalı](../../../visual-basic/language-reference/modifiers/protected.md)</span><span class="sxs-lookup"><span data-stu-id="e532c-112">-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)</span></span><br /><span data-ttu-id="e532c-113">-   [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md)</span><span class="sxs-lookup"><span data-stu-id="e532c-113">-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)</span></span><br /><span data-ttu-id="e532c-114">-   [özel](../../../visual-basic/language-reference/modifiers/private.md)</span><span class="sxs-lookup"><span data-stu-id="e532c-114">-   [Private](../../../visual-basic/language-reference/modifiers/private.md)</span></span><br />-   `Protected Friend`<br /><br /> <span data-ttu-id="e532c-115">[Visual Basic erişim düzeylerine](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="e532c-115">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`statements`|<span data-ttu-id="e532c-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e532c-116">Optional.</span></span> <span data-ttu-id="e532c-117">@No__t_0 özellik yordamı çağrıldığında çalışan bir veya daha fazla deyim.</span><span class="sxs-lookup"><span data-stu-id="e532c-117">One or more statements that run when the `Get` property procedure is called.</span></span>|  
|`End Get`|<span data-ttu-id="e532c-118">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="e532c-118">Required.</span></span> <span data-ttu-id="e532c-119">@No__t_0 özelliği yordamının tanımını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="e532c-119">Terminates the definition of the `Get` property procedure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e532c-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e532c-120">Remarks</span></span>  
 <span data-ttu-id="e532c-121">Özellik `WriteOnly` olarak işaretlenmedikçe her özelliğin `Get` Özellik yordamına sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e532c-121">Every property must have a `Get` property procedure unless the property is marked `WriteOnly`.</span></span> <span data-ttu-id="e532c-122">@No__t_0 yordamı, özelliğin geçerli değerini döndürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e532c-122">The `Get` procedure is used to return the current value of the property.</span></span>  
  
 <span data-ttu-id="e532c-123">Visual Basic bir ifade özelliğin değerini istediğinde bir özelliğin `Get` yordamını otomatik olarak çağırır.</span><span class="sxs-lookup"><span data-stu-id="e532c-123">Visual Basic automatically calls a property's `Get` procedure when an expression requests the property's value.</span></span>  
  
 <span data-ttu-id="e532c-124">Özellik bildiriminin gövdesi, Property [ifadesiyle](../../../visual-basic/language-reference/statements/property-statement.md) `End Property` ifadesiyle yalnızca özelliğin `Get` ve `Set` yordamlarını içerebilir.</span><span class="sxs-lookup"><span data-stu-id="e532c-124">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="e532c-125">Bu yordamlar dışında bir şey depolayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="e532c-125">It cannot store anything other than those procedures.</span></span> <span data-ttu-id="e532c-126">Özellikle, özelliğin geçerli değerini depolayaamaz.</span><span class="sxs-lookup"><span data-stu-id="e532c-126">In particular, it cannot store the property's current value.</span></span> <span data-ttu-id="e532c-127">Özellik yordamlarından birinde depolursa, diğer özellik yordamının bu değeri, özelliğin dışında depolamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e532c-127">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span></span> <span data-ttu-id="e532c-128">Her zamanki yaklaşım, değeri özelliği ile aynı düzeyde belirtilen [özel](../../../visual-basic/language-reference/modifiers/private.md) bir değişkende depokullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="e532c-128">The usual approach is to store the value in a [Private](../../../visual-basic/language-reference/modifiers/private.md) variable declared at the same level as the property.</span></span> <span data-ttu-id="e532c-129">Bir `Get` yordamını, uygulandığı özelliğin içinde tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e532c-129">You must define a `Get` procedure inside the property to which it applies.</span></span>  
  
 <span data-ttu-id="e532c-130">@No__t_0 yordamı, `Get` ifadesinde `accessmodifier` kullanmadığınız durumlar dışında, kendisini kapsayan özelliğin erişim düzeyi olur.</span><span class="sxs-lookup"><span data-stu-id="e532c-130">The `Get` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Get` statement.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="e532c-131">Kurallar</span><span class="sxs-lookup"><span data-stu-id="e532c-131">Rules</span></span>  
  
- <span data-ttu-id="e532c-132">**Karışık erişim düzeyleri.**</span><span class="sxs-lookup"><span data-stu-id="e532c-132">**Mixed Access Levels.**</span></span> <span data-ttu-id="e532c-133">Okuma-yazma özelliği tanımlıyorsanız, isteğe bağlı olarak `Get` ya da `Set` yordamı için farklı bir erişim düzeyi belirtebilirsiniz, ancak her ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="e532c-133">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="e532c-134">Bunu yaparsanız, yordam erişim düzeyinin özelliğin erişim düzeyinden daha kısıtlayıcı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e532c-134">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="e532c-135">Örneğin, özellik `Friend` olarak bildirilirse, `Private` `Get` yordamını bildirebilirsiniz, ancak `Public`.</span><span class="sxs-lookup"><span data-stu-id="e532c-135">For example, if the property is declared `Friend`, you can declare the `Get` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="e532c-136">@No__t_0 özelliği tanımlıyorsanız, `Get` yordamı tüm özelliği temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e532c-136">If you are defining a `ReadOnly` property, the `Get` procedure represents the entire property.</span></span> <span data-ttu-id="e532c-137">Özelliği için iki erişim düzeyi ayarlayacağından, `Get` için farklı bir erişim düzeyi bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="e532c-137">You cannot declare a different access level for `Get`, because that would set two access levels for the property.</span></span>  
  
- <span data-ttu-id="e532c-138">**Dönüş türü.**</span><span class="sxs-lookup"><span data-stu-id="e532c-138">**Return Type.**</span></span> <span data-ttu-id="e532c-139">[Property deyimleri](../../../visual-basic/language-reference/statements/property-statement.md) , döndürdüğü değerin veri türünü bildirebilir.</span><span class="sxs-lookup"><span data-stu-id="e532c-139">The [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) can declare the data type of the value it returns.</span></span> <span data-ttu-id="e532c-140">@No__t_0 yordam bu veri türünü otomatik olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="e532c-140">The `Get` procedure automatically returns that data type.</span></span> <span data-ttu-id="e532c-141">Herhangi bir veri türü veya bir numaralandırma, yapı, sınıf veya arabirim adı belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e532c-141">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
     <span data-ttu-id="e532c-142">@No__t_0 deyimin `returntype` belirtmezse yordam `Object` döndürür.</span><span class="sxs-lookup"><span data-stu-id="e532c-142">If the `Property` statement does not specify `returntype`, the procedure returns `Object`.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="e532c-143">Davranış</span><span class="sxs-lookup"><span data-stu-id="e532c-143">Behavior</span></span>  
  
- <span data-ttu-id="e532c-144">**Bir yordamdan dönme.**</span><span class="sxs-lookup"><span data-stu-id="e532c-144">**Returning from a Procedure.**</span></span> <span data-ttu-id="e532c-145">@No__t_0 yordamı çağıran koda döndüğünde, yürütme özelliği değeri istenen deyimin içinde devam eder.</span><span class="sxs-lookup"><span data-stu-id="e532c-145">When the `Get` procedure returns to the calling code, execution continues within the statement that requested the property value.</span></span>  
  
     <span data-ttu-id="e532c-146">`Get` özellik yordamları, [return ifadesini](../../../visual-basic/language-reference/statements/return-statement.md) kullanarak ya da dönüş değerini özellik adına atayarak bir değer döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="e532c-146">`Get` property procedures can return a value using either the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) or by assigning the return value to the property name.</span></span> <span data-ttu-id="e532c-147">Daha fazla bilgi için [Işlev deyimindeki](../../../visual-basic/language-reference/statements/function-statement.md)"dönüş değeri" başlığına bakın.</span><span class="sxs-lookup"><span data-stu-id="e532c-147">For more information, see "Return Value" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
     <span data-ttu-id="e532c-148">@No__t_0 ve `Return` deyimleri, bir özellik yordamından anında çıkış oluşmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="e532c-148">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="e532c-149">Herhangi bir sayıda `Exit Property` ve `Return` deyimi yordamda herhangi bir yerde görünebilir ve `Exit Property` ve `Return` deyimlerini karıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e532c-149">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
- <span data-ttu-id="e532c-150">**Dönüş değeri.**</span><span class="sxs-lookup"><span data-stu-id="e532c-150">**Return Value.**</span></span> <span data-ttu-id="e532c-151">Bir `Get` yordamından bir değer döndürmek için, değeri özellik adına atayabilir ya da bir [Return ifadesine](../../../visual-basic/language-reference/statements/return-statement.md)dahil edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e532c-151">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span> <span data-ttu-id="e532c-152">@No__t_0 deyimleri aynı anda `Get` yordam dönüş değerini atar ve yordamdan çıkar.</span><span class="sxs-lookup"><span data-stu-id="e532c-152">The `Return` statement simultaneously assigns the `Get` procedure return value and exits the procedure.</span></span>  
  
     <span data-ttu-id="e532c-153">Özellik adına bir değer atamadan `Exit Property` kullanırsanız, `Get` yordamı özelliğin veri türü için varsayılan değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="e532c-153">If you use `Exit Property` without assigning a value to the property name, the `Get` procedure returns the default value for the property's data type.</span></span> <span data-ttu-id="e532c-154">Daha fazla bilgi için [Işlev deyimindeki](../../../visual-basic/language-reference/statements/function-statement.md)"dönüş değeri" başlığına bakın.</span><span class="sxs-lookup"><span data-stu-id="e532c-154">For more information, see "Return Value" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
     <span data-ttu-id="e532c-155">Aşağıdaki örnekte, salt okuma özelliğinin `quoteForTheDay` özel değişkende tutulan değeri döndürebileceği iki yol gösterilmektedir `quoteValue`.</span><span class="sxs-lookup"><span data-stu-id="e532c-155">The following example illustrates two ways the read-only property `quoteForTheDay` can return the value held in the private variable `quoteValue`.</span></span>  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]  
  
     [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]  
  
## <a name="example"></a><span data-ttu-id="e532c-156">Örnek</span><span class="sxs-lookup"><span data-stu-id="e532c-156">Example</span></span>  
 <span data-ttu-id="e532c-157">Aşağıdaki örnek, bir özelliğin değerini döndürmek için `Get` ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e532c-157">The following example uses the `Get` statement to return the value of a property.</span></span>  
  
 [!code-vb[VbVbalrStatements#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="e532c-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e532c-158">See also</span></span>

- [<span data-ttu-id="e532c-159">Set Deyimi</span><span class="sxs-lookup"><span data-stu-id="e532c-159">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
- [<span data-ttu-id="e532c-160">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="e532c-160">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="e532c-161">Exit Deyimi</span><span class="sxs-lookup"><span data-stu-id="e532c-161">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="e532c-162">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="e532c-162">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="e532c-163">İzlenecek Yol: Sınıfları Tanımlama</span><span class="sxs-lookup"><span data-stu-id="e532c-163">Walkthrough: Defining Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)
