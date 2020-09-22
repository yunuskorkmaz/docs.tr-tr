---
title: Get Deyimi
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
ms.openlocfilehash: 3da6c099b3f43a144484eaddf58605609eb0bbfe
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866206"
---
# <a name="get-statement"></a><span data-ttu-id="915c3-102">Get Deyimi</span><span class="sxs-lookup"><span data-stu-id="915c3-102">Get Statement</span></span>

<span data-ttu-id="915c3-103">`Get`Bir özelliğin değerini almak için kullanılan bir özellik yordamı bildirir.</span><span class="sxs-lookup"><span data-stu-id="915c3-103">Declares a `Get` property procedure used to retrieve the value of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="915c3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="915c3-104">Syntax</span></span>  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## <a name="parts"></a><span data-ttu-id="915c3-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="915c3-105">Parts</span></span>  
  
|<span data-ttu-id="915c3-106">Terim</span><span class="sxs-lookup"><span data-stu-id="915c3-106">Term</span></span>|<span data-ttu-id="915c3-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="915c3-107">Definition</span></span>|  
|---|---|  
|`attributelist`|<span data-ttu-id="915c3-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="915c3-108">Optional.</span></span> <span data-ttu-id="915c3-109">Bkz. [öznitelik listesi](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="915c3-109">See [Attribute List](attribute-list.md).</span></span>|  
|`accessmodifier`|<span data-ttu-id="915c3-110">`Get`Bu özellikte ve deyimlerden en fazla bir isteğe bağlı `Set` .</span><span class="sxs-lookup"><span data-stu-id="915c3-110">Optional on at most one of the `Get` and `Set` statements in this property.</span></span> <span data-ttu-id="915c3-111">Aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="915c3-111">Can be one of the following:</span></span><br /><br /> <span data-ttu-id="915c3-112">-   [Korunamadı](../modifiers/protected.md)</span><span class="sxs-lookup"><span data-stu-id="915c3-112">-   [Protected](../modifiers/protected.md)</span></span><br /><span data-ttu-id="915c3-113">-   [Dost](../modifiers/friend.md)</span><span class="sxs-lookup"><span data-stu-id="915c3-113">-   [Friend](../modifiers/friend.md)</span></span><br /><span data-ttu-id="915c3-114">-   [Özelleştirme](../modifiers/private.md)</span><span class="sxs-lookup"><span data-stu-id="915c3-114">-   [Private](../modifiers/private.md)</span></span><br />-   `Protected Friend`<br /><br /> <span data-ttu-id="915c3-115">[Visual Basic erişim düzeylerine](../../programming-guide/language-features/declared-elements/access-levels.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="915c3-115">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`statements`|<span data-ttu-id="915c3-116">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="915c3-116">Optional.</span></span> <span data-ttu-id="915c3-117">Özellik yordamı çağrıldığında çalışan bir veya daha fazla deyim `Get` .</span><span class="sxs-lookup"><span data-stu-id="915c3-117">One or more statements that run when the `Get` property procedure is called.</span></span>|  
|`End Get`|<span data-ttu-id="915c3-118">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="915c3-118">Required.</span></span> <span data-ttu-id="915c3-119">`Get`Özellik yordamının tanımını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="915c3-119">Terminates the definition of the `Get` property procedure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="915c3-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="915c3-120">Remarks</span></span>  

 <span data-ttu-id="915c3-121">Özellik işaretlenmedikçe her özelliğin bir özellik yordamına sahip olması gerekir `Get` `WriteOnly` .</span><span class="sxs-lookup"><span data-stu-id="915c3-121">Every property must have a `Get` property procedure unless the property is marked `WriteOnly`.</span></span> <span data-ttu-id="915c3-122">`Get`Yordamı, özelliğin geçerli değerini döndürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="915c3-122">The `Get` procedure is used to return the current value of the property.</span></span>  
  
 <span data-ttu-id="915c3-123">Visual Basic, `Get` bir ifade özelliğin değerini istediğinde bir özelliğin yordamını otomatik olarak çağırır.</span><span class="sxs-lookup"><span data-stu-id="915c3-123">Visual Basic automatically calls a property's `Get` procedure when an expression requests the property's value.</span></span>  
  
 <span data-ttu-id="915c3-124">Özellik bildiriminin gövdesi, yalnızca Property Ifadesiyle ve ifadesiyle olan özellik `Get` ve yordamları içerebilir `Set` [Property Statement](property-statement.md) `End Property` .</span><span class="sxs-lookup"><span data-stu-id="915c3-124">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="915c3-125">Bu yordamlar dışında bir şey depolayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="915c3-125">It cannot store anything other than those procedures.</span></span> <span data-ttu-id="915c3-126">Özellikle, özelliğin geçerli değerini depolayaamaz.</span><span class="sxs-lookup"><span data-stu-id="915c3-126">In particular, it cannot store the property's current value.</span></span> <span data-ttu-id="915c3-127">Özellik yordamlarından birinde depolursa, diğer özellik yordamının bu değeri, özelliğin dışında depolamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="915c3-127">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span></span> <span data-ttu-id="915c3-128">Her zamanki yaklaşım, değeri özelliği ile aynı düzeyde belirtilen [özel](../modifiers/private.md) bir değişkende depokullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="915c3-128">The usual approach is to store the value in a [Private](../modifiers/private.md) variable declared at the same level as the property.</span></span> <span data-ttu-id="915c3-129">`Get`Uygulandığı özelliğin içinde bir yordam tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="915c3-129">You must define a `Get` procedure inside the property to which it applies.</span></span>  
  
 <span data-ttu-id="915c3-130">`Get`Yöntemi, bildiriminde kullanmadığınız müddetçe, kendisini kapsayan özelliğin erişim düzeyi olur `accessmodifier` `Get` .</span><span class="sxs-lookup"><span data-stu-id="915c3-130">The `Get` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Get` statement.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="915c3-131">Kurallar</span><span class="sxs-lookup"><span data-stu-id="915c3-131">Rules</span></span>  
  
- <span data-ttu-id="915c3-132">**Karışık erişim düzeyleri.**</span><span class="sxs-lookup"><span data-stu-id="915c3-132">**Mixed Access Levels.**</span></span> <span data-ttu-id="915c3-133">Okuma-yazma özelliği tanımlıyorsanız, isteğe bağlı olarak ya da yordam için farklı bir erişim düzeyi belirtebilirsiniz `Get` `Set` , ancak her ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="915c3-133">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="915c3-134">Bunu yaparsanız, yordam erişim düzeyinin özelliğin erişim düzeyinden daha kısıtlayıcı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="915c3-134">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="915c3-135">Örneğin, özelliği bildirilirse, `Friend` `Get` yordamı bildirebilirsiniz `Private` , ancak kullanamazsınız `Public` .</span><span class="sxs-lookup"><span data-stu-id="915c3-135">For example, if the property is declared `Friend`, you can declare the `Get` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="915c3-136">Bir `ReadOnly` özellik tanımlıyorsanız, `Get` yordam tüm özelliği temsil eder.</span><span class="sxs-lookup"><span data-stu-id="915c3-136">If you are defining a `ReadOnly` property, the `Get` procedure represents the entire property.</span></span> <span data-ttu-id="915c3-137">`Get`Özelliği için iki erişim düzeyi ayarlayacağından, için farklı bir erişim düzeyi bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="915c3-137">You cannot declare a different access level for `Get`, because that would set two access levels for the property.</span></span>  
  
- <span data-ttu-id="915c3-138">**Dönüş türü.**</span><span class="sxs-lookup"><span data-stu-id="915c3-138">**Return Type.**</span></span> <span data-ttu-id="915c3-139">[Property deyimleri](property-statement.md) , döndürdüğü değerin veri türünü bildirebilir.</span><span class="sxs-lookup"><span data-stu-id="915c3-139">The [Property Statement](property-statement.md) can declare the data type of the value it returns.</span></span> <span data-ttu-id="915c3-140">`Get`Yordam, bu veri türünü otomatik olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="915c3-140">The `Get` procedure automatically returns that data type.</span></span> <span data-ttu-id="915c3-141">Herhangi bir veri türü veya bir numaralandırma, yapı, sınıf veya arabirim adı belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="915c3-141">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
     <span data-ttu-id="915c3-142">`Property`Deyimse `returntype` , yordam döndürür `Object` .</span><span class="sxs-lookup"><span data-stu-id="915c3-142">If the `Property` statement does not specify `returntype`, the procedure returns `Object`.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="915c3-143">Davranış</span><span class="sxs-lookup"><span data-stu-id="915c3-143">Behavior</span></span>  
  
- <span data-ttu-id="915c3-144">**Bir yordamdan dönme.**</span><span class="sxs-lookup"><span data-stu-id="915c3-144">**Returning from a Procedure.**</span></span> <span data-ttu-id="915c3-145">`Get`Yordam çağıran koda döndüğünde, yürütme özelliği değeri istenen deyimin içinde devam eder.</span><span class="sxs-lookup"><span data-stu-id="915c3-145">When the `Get` procedure returns to the calling code, execution continues within the statement that requested the property value.</span></span>  
  
     <span data-ttu-id="915c3-146">`Get` özellik yordamları, [dönüş ifadesini](return-statement.md) kullanarak veya dönüş değerini özellik adına atayarak bir değer döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="915c3-146">`Get` property procedures can return a value using either the [Return Statement](return-statement.md) or by assigning the return value to the property name.</span></span> <span data-ttu-id="915c3-147">Daha fazla bilgi için [Işlev deyimindeki](function-statement.md)"dönüş değeri" başlığına bakın.</span><span class="sxs-lookup"><span data-stu-id="915c3-147">For more information, see "Return Value" in [Function Statement](function-statement.md).</span></span>  
  
     <span data-ttu-id="915c3-148">`Exit Property`Ve `Return` deyimleri, bir özellik yordamından anında çıkış oluşmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="915c3-148">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="915c3-149">Herhangi bir sayıda `Exit Property` ve `Return` deyimi yordamda herhangi bir yerde görünebilir ve `Exit Property` ve deyimlerini karıştırabilirsiniz `Return` .</span><span class="sxs-lookup"><span data-stu-id="915c3-149">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
- <span data-ttu-id="915c3-150">**Dönüş değeri.**</span><span class="sxs-lookup"><span data-stu-id="915c3-150">**Return Value.**</span></span> <span data-ttu-id="915c3-151">Bir yordamdan bir değer döndürmek için `Get` , değeri özellik adına atayabilir ya da bir [Return ifadesine](return-statement.md)dahil edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="915c3-151">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a [Return Statement](return-statement.md).</span></span> <span data-ttu-id="915c3-152">`Return`İfade, `Get` yordam dönüş değerini eşzamanlı olarak atar ve yordamdan çıkar.</span><span class="sxs-lookup"><span data-stu-id="915c3-152">The `Return` statement simultaneously assigns the `Get` procedure return value and exits the procedure.</span></span>  
  
     <span data-ttu-id="915c3-153">`Exit Property`Özellik adına bir değer atamadan kullanırsanız, `Get` yordam özelliğin veri türü için varsayılan değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="915c3-153">If you use `Exit Property` without assigning a value to the property name, the `Get` procedure returns the default value for the property's data type.</span></span> <span data-ttu-id="915c3-154">Daha fazla bilgi için [Işlev deyimindeki](function-statement.md)"dönüş değeri" başlığına bakın.</span><span class="sxs-lookup"><span data-stu-id="915c3-154">For more information, see "Return Value" in [Function Statement](function-statement.md).</span></span>  
  
     <span data-ttu-id="915c3-155">Aşağıdaki örnekte, salt okuma özelliğinin `quoteForTheDay` özel değişkende tutulan değeri döndürebileceği iki yol gösterilmektedir `quoteValue` .</span><span class="sxs-lookup"><span data-stu-id="915c3-155">The following example illustrates two ways the read-only property `quoteForTheDay` can return the value held in the private variable `quoteValue`.</span></span>  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]  
  
     [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]  
  
## <a name="example"></a><span data-ttu-id="915c3-156">Örnek</span><span class="sxs-lookup"><span data-stu-id="915c3-156">Example</span></span>  

 <span data-ttu-id="915c3-157">Aşağıdaki örnek, `Get` bir özelliğin değerini döndürmek için ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="915c3-157">The following example uses the `Get` statement to return the value of a property.</span></span>  
  
 [!code-vb[VbVbalrStatements#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="915c3-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="915c3-158">See also</span></span>

- [<span data-ttu-id="915c3-159">Set deyimleri</span><span class="sxs-lookup"><span data-stu-id="915c3-159">Set Statement</span></span>](set-statement.md)
- [<span data-ttu-id="915c3-160">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="915c3-160">Property Statement</span></span>](property-statement.md)
- [<span data-ttu-id="915c3-161">Exit Deyimi</span><span class="sxs-lookup"><span data-stu-id="915c3-161">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="915c3-162">Nesneler ve sınıflar</span><span class="sxs-lookup"><span data-stu-id="915c3-162">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="915c3-163">İzlenecek Yol: Sınıfları Tanımlama</span><span class="sxs-lookup"><span data-stu-id="915c3-163">Walkthrough: Defining Classes</span></span>](../../programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)
