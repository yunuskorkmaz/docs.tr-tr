---
title: Set Deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Set
helpviewer_keywords:
- property procedures [Visual Basic], Set statements
- Set statement [Visual Basic]
- Set statement [Visual Basic], syntax
- write-only properties
- properties [Visual Basic], write-only
ms.assetid: 9ecc27b4-df84-420d-9075-db25455fb3cd
ms.openlocfilehash: cb0dc76d110f3e6a3ea3e74cc0bfb5a669b35396
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583232"
---
# <a name="set-statement-visual-basic"></a><span data-ttu-id="11f63-102">Set Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11f63-102">Set Statement (Visual Basic)</span></span>
<span data-ttu-id="11f63-103">Bir özelliğe değer atamak için kullanılan bir `Set` özellik yordamı bildirir.</span><span class="sxs-lookup"><span data-stu-id="11f63-103">Declares a `Set` property procedure used to assign a value to a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11f63-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="11f63-104">Syntax</span></span>  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a><span data-ttu-id="11f63-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="11f63-105">Parts</span></span>  
 `attributelist`  
 <span data-ttu-id="11f63-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="11f63-106">Optional.</span></span> <span data-ttu-id="11f63-107">Bkz. [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="11f63-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
 `accessmodifier`  
 <span data-ttu-id="11f63-108">Bu özelliğindeki `Get` ve `Set` deyimlerinin en az birinde isteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="11f63-108">Optional on at most one of the `Get` and `Set` statements in this property.</span></span> <span data-ttu-id="11f63-109">Aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="11f63-109">Can be one of the following:</span></span>  
  
- [<span data-ttu-id="11f63-110">Protected</span><span class="sxs-lookup"><span data-stu-id="11f63-110">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
- [<span data-ttu-id="11f63-111">Friend</span><span class="sxs-lookup"><span data-stu-id="11f63-111">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
- [<span data-ttu-id="11f63-112">Private</span><span class="sxs-lookup"><span data-stu-id="11f63-112">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
- `Protected Friend`  
  
 <span data-ttu-id="11f63-113">[Visual Basic erişim düzeylerine](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="11f63-113">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 `value`  
 <span data-ttu-id="11f63-114">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="11f63-114">Required.</span></span> <span data-ttu-id="11f63-115">Özelliği için yeni değeri içeren parametre.</span><span class="sxs-lookup"><span data-stu-id="11f63-115">Parameter containing the new value for the property.</span></span>  
  
 `datatype`  
 <span data-ttu-id="11f63-116">@No__t_0 `On` olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="11f63-116">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="11f63-117">@No__t_0 parametresinin veri türü.</span><span class="sxs-lookup"><span data-stu-id="11f63-117">Data type of the `value` parameter.</span></span> <span data-ttu-id="11f63-118">Belirtilen veri türü, bu `Set` deyimin bildirildiği özelliğin veri türüyle aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="11f63-118">The data type specified must be the same as the data type of the property where this `Set` statement is declared.</span></span>  
  
 `statements`  
 <span data-ttu-id="11f63-119">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="11f63-119">Optional.</span></span> <span data-ttu-id="11f63-120">@No__t_0 özellik yordamı çağrıldığında çalışan bir veya daha fazla deyim.</span><span class="sxs-lookup"><span data-stu-id="11f63-120">One or more statements that run when the `Set` property procedure is called.</span></span>  
  
 `End Set`  
 <span data-ttu-id="11f63-121">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="11f63-121">Required.</span></span> <span data-ttu-id="11f63-122">@No__t_0 özelliği yordamının tanımını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="11f63-122">Terminates the definition of the `Set` property procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11f63-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="11f63-123">Remarks</span></span>  
 <span data-ttu-id="11f63-124">Özellik `ReadOnly` olarak işaretlenmedikçe her özelliğin `Set` Özellik yordamına sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="11f63-124">Every property must have a `Set` property procedure unless the property is marked `ReadOnly`.</span></span> <span data-ttu-id="11f63-125">@No__t_0 yordamı, özelliğinin değerini ayarlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="11f63-125">The `Set` procedure is used to set the value of the property.</span></span>  
  
 <span data-ttu-id="11f63-126">Bir atama ekstresi özellikte depolanacak bir değer sağlıyorsa, Visual Basic bir özelliğin `Set` yordamını otomatik olarak çağırır.</span><span class="sxs-lookup"><span data-stu-id="11f63-126">Visual Basic automatically calls a property's `Set` procedure when an assignment statement provides a value to be stored in the property.</span></span>  
  
 <span data-ttu-id="11f63-127">Visual Basic, özellik atamaları sırasında `Set` yordama bir parametre geçirir.</span><span class="sxs-lookup"><span data-stu-id="11f63-127">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="11f63-128">@No__t_0 için bir parametre belirtmezseniz, tümleşik geliştirme ortamı (IDE) `value` adlı örtük bir parametre kullanır.</span><span class="sxs-lookup"><span data-stu-id="11f63-128">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="11f63-129">Parametresi, özelliğine atanacak değeri tutar.</span><span class="sxs-lookup"><span data-stu-id="11f63-129">The parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="11f63-130">Genellikle bu değeri özel bir yerel değişkende depolar ve `Get` yordamı her çağrıldığında döndürün.</span><span class="sxs-lookup"><span data-stu-id="11f63-130">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>  
  
 <span data-ttu-id="11f63-131">Özellik bildiriminin gövdesi, Property [ifadesiyle](../../../visual-basic/language-reference/statements/property-statement.md) `End Property` ifadesiyle yalnızca özelliğin `Get` ve `Set` yordamlarını içerebilir.</span><span class="sxs-lookup"><span data-stu-id="11f63-131">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="11f63-132">Bu yordamlar dışında bir şey depolayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="11f63-132">It cannot store anything other than those procedures.</span></span> <span data-ttu-id="11f63-133">Özellikle, özelliğin geçerli değerini depolayaamaz.</span><span class="sxs-lookup"><span data-stu-id="11f63-133">In particular, it cannot store the property's current value.</span></span> <span data-ttu-id="11f63-134">Özellik yordamlarından birinde depolursa, diğer özellik yordamının bu değeri, özelliğin dışında depolamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="11f63-134">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span></span> <span data-ttu-id="11f63-135">Her zamanki yaklaşım, değeri özelliği ile aynı düzeyde belirtilen [özel](../../../visual-basic/language-reference/modifiers/private.md) bir değişkende depokullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="11f63-135">The usual approach is to store the value in a [Private](../../../visual-basic/language-reference/modifiers/private.md) variable declared at the same level as the property.</span></span> <span data-ttu-id="11f63-136">Bir `Set` yordamını, uygulandığı özelliğin içinde tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="11f63-136">You must define a `Set` procedure inside the property to which it applies.</span></span>  
  
 <span data-ttu-id="11f63-137">@No__t_0 yordamı, `Set` ifadesinde `accessmodifier` kullanmadığınız durumlar dışında, kendisini kapsayan özelliğin erişim düzeyi olur.</span><span class="sxs-lookup"><span data-stu-id="11f63-137">The `Set` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Set` statement.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="11f63-138">Kurallar</span><span class="sxs-lookup"><span data-stu-id="11f63-138">Rules</span></span>  
  
- <span data-ttu-id="11f63-139">**Karışık erişim düzeyleri.**</span><span class="sxs-lookup"><span data-stu-id="11f63-139">**Mixed Access Levels.**</span></span> <span data-ttu-id="11f63-140">Okuma-yazma özelliği tanımlıyorsanız, isteğe bağlı olarak `Get` ya da `Set` yordamı için farklı bir erişim düzeyi belirtebilirsiniz, ancak her ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="11f63-140">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="11f63-141">Bunu yaparsanız, yordam erişim düzeyinin özelliğin erişim düzeyinden daha kısıtlayıcı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="11f63-141">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="11f63-142">Örneğin, özellik `Friend` olarak bildirilirse, `Private` `Set` yordamını bildirebilirsiniz, ancak `Public`.</span><span class="sxs-lookup"><span data-stu-id="11f63-142">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="11f63-143">@No__t_0 özelliği tanımlıyorsanız, `Set` yordamı tüm özelliği temsil eder.</span><span class="sxs-lookup"><span data-stu-id="11f63-143">If you are defining a `WriteOnly` property, the `Set` procedure represents the entire property.</span></span> <span data-ttu-id="11f63-144">Özelliği için iki erişim düzeyi ayarlayacağından, `Set` için farklı bir erişim düzeyi bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="11f63-144">You cannot declare a different access level for `Set`, because that would set two access levels for the property.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="11f63-145">Davranış</span><span class="sxs-lookup"><span data-stu-id="11f63-145">Behavior</span></span>  
  
- <span data-ttu-id="11f63-146">**Bir özellik yordamından döndürülüyor.**</span><span class="sxs-lookup"><span data-stu-id="11f63-146">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="11f63-147">@No__t_0 yordamı çağıran koda döndüğünde, yürütme, depolanacak değeri sağlayan deyimden sonra devam eder.</span><span class="sxs-lookup"><span data-stu-id="11f63-147">When the `Set` procedure returns to the calling code, execution continues following the statement that provided the value to be stored.</span></span>  
  
     <span data-ttu-id="11f63-148">`Set` özellik yordamları, [Return](../../../visual-basic/language-reference/statements/return-statement.md) veya [Exit deyimlerini](../../../visual-basic/language-reference/statements/exit-statement.md)kullanarak dönebilir.</span><span class="sxs-lookup"><span data-stu-id="11f63-148">`Set` property procedures can return using either the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) or the [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md).</span></span>  
  
     <span data-ttu-id="11f63-149">@No__t_0 ve `Return` deyimleri, bir özellik yordamından anında çıkış oluşmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="11f63-149">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="11f63-150">Herhangi bir sayıda `Exit Property` ve `Return` deyimi yordamda herhangi bir yerde görünebilir ve `Exit Property` ve `Return` deyimlerini karıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="11f63-150">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11f63-151">Örnek</span><span class="sxs-lookup"><span data-stu-id="11f63-151">Example</span></span>  
 <span data-ttu-id="11f63-152">Aşağıdaki örnek, bir özelliğin değerini ayarlamak için `Set` ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="11f63-152">The following example uses the `Set` statement to set the value of a property.</span></span>  
  
 [!code-vb[VbVbalrStatements#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#55)]  
  
## <a name="see-also"></a><span data-ttu-id="11f63-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11f63-153">See also</span></span>

- [<span data-ttu-id="11f63-154">Get Deyimi</span><span class="sxs-lookup"><span data-stu-id="11f63-154">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="11f63-155">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="11f63-155">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="11f63-156">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="11f63-156">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="11f63-157">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="11f63-157">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
