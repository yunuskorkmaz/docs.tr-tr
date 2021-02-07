---
description: 'Daha fazla bilgi edinin: set deyimleri (Visual Basic)'
title: Set Deyimi
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
ms.openlocfilehash: 5ee27b35a4639bc20d5b6634de8332c6ede9bf12
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741126"
---
# <a name="set-statement-visual-basic"></a><span data-ttu-id="7f4ad-103">Set Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7f4ad-103">Set Statement (Visual Basic)</span></span>

<span data-ttu-id="7f4ad-104">`Set`Bir özelliğe değer atamak için kullanılan bir özellik yordamı bildirir.</span><span class="sxs-lookup"><span data-stu-id="7f4ad-104">Declares a `Set` property procedure used to assign a value to a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f4ad-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7f4ad-105">Syntax</span></span>  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a><span data-ttu-id="7f4ad-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="7f4ad-106">Parts</span></span>  

 `attributelist`  
 <span data-ttu-id="7f4ad-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="7f4ad-107">Optional.</span></span> <span data-ttu-id="7f4ad-108">Bkz. [öznitelik listesi](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="7f4ad-108">See [Attribute List](attribute-list.md).</span></span>  
  
 `accessmodifier`  
 <span data-ttu-id="7f4ad-109">`Get`Bu özellikte ve deyimlerden en fazla bir isteğe bağlı `Set` .</span><span class="sxs-lookup"><span data-stu-id="7f4ad-109">Optional on at most one of the `Get` and `Set` statements in this property.</span></span> <span data-ttu-id="7f4ad-110">Aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="7f4ad-110">Can be one of the following:</span></span>  
  
- [<span data-ttu-id="7f4ad-111">Korunamadı</span><span class="sxs-lookup"><span data-stu-id="7f4ad-111">Protected</span></span>](../modifiers/protected.md)  
  
- [<span data-ttu-id="7f4ad-112">Arkadaş</span><span class="sxs-lookup"><span data-stu-id="7f4ad-112">Friend</span></span>](../modifiers/friend.md)  
  
- [<span data-ttu-id="7f4ad-113">Özel</span><span class="sxs-lookup"><span data-stu-id="7f4ad-113">Private</span></span>](../modifiers/private.md)  
  
- `Protected Friend`  
  
 <span data-ttu-id="7f4ad-114">[Visual Basic erişim düzeylerine](../../programming-guide/language-features/declared-elements/access-levels.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="7f4ad-114">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 `value`  
 <span data-ttu-id="7f4ad-115">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7f4ad-115">Required.</span></span> <span data-ttu-id="7f4ad-116">Özelliği için yeni değeri içeren parametre.</span><span class="sxs-lookup"><span data-stu-id="7f4ad-116">Parameter containing the new value for the property.</span></span>  
  
 `datatype`  
 <span data-ttu-id="7f4ad-117">İse gereklidir `Option Strict` `On` .</span><span class="sxs-lookup"><span data-stu-id="7f4ad-117">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="7f4ad-118">Parametrenin veri türü `value` .</span><span class="sxs-lookup"><span data-stu-id="7f4ad-118">Data type of the `value` parameter.</span></span> <span data-ttu-id="7f4ad-119">Belirtilen veri türü, bu deyimin bildirildiği özelliğin veri türüyle aynı olmalıdır `Set` .</span><span class="sxs-lookup"><span data-stu-id="7f4ad-119">The data type specified must be the same as the data type of the property where this `Set` statement is declared.</span></span>  
  
 `statements`  
 <span data-ttu-id="7f4ad-120">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="7f4ad-120">Optional.</span></span> <span data-ttu-id="7f4ad-121">Özellik yordamı çağrıldığında çalışan bir veya daha fazla deyim `Set` .</span><span class="sxs-lookup"><span data-stu-id="7f4ad-121">One or more statements that run when the `Set` property procedure is called.</span></span>  
  
 `End Set`  
 <span data-ttu-id="7f4ad-122">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7f4ad-122">Required.</span></span> <span data-ttu-id="7f4ad-123">`Set`Özellik yordamının tanımını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="7f4ad-123">Terminates the definition of the `Set` property procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f4ad-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7f4ad-124">Remarks</span></span>  

 <span data-ttu-id="7f4ad-125">Özellik işaretlenmedikçe her özelliğin bir özellik yordamına sahip olması gerekir `Set` `ReadOnly` .</span><span class="sxs-lookup"><span data-stu-id="7f4ad-125">Every property must have a `Set` property procedure unless the property is marked `ReadOnly`.</span></span> <span data-ttu-id="7f4ad-126">`Set`Yordamı, özelliğinin değerini ayarlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7f4ad-126">The `Set` procedure is used to set the value of the property.</span></span>  
  
 <span data-ttu-id="7f4ad-127">`Set`Bir atama ekstresi özellikte depolanacak bir değer sağlıyorsa, bir özelliğin yordamını otomatik olarak çağırır Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7f4ad-127">Visual Basic automatically calls a property's `Set` procedure when an assignment statement provides a value to be stored in the property.</span></span>  
  
 <span data-ttu-id="7f4ad-128">Visual Basic, `Set` özellik atamaları sırasında yordama bir parametre geçirir.</span><span class="sxs-lookup"><span data-stu-id="7f4ad-128">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="7f4ad-129">İçin bir parametre belirtmezseniz `Set` , tümleşik geliştirme ortamı (IDE) adlı örtülü bir parametre kullanır `value` .</span><span class="sxs-lookup"><span data-stu-id="7f4ad-129">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="7f4ad-130">Parametresi, özelliğine atanacak değeri tutar.</span><span class="sxs-lookup"><span data-stu-id="7f4ad-130">The parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="7f4ad-131">Genellikle bu değeri özel bir yerel değişkende depoluyordu ve yordam her çağrıldığında döndürülür `Get` .</span><span class="sxs-lookup"><span data-stu-id="7f4ad-131">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>  
  
 <span data-ttu-id="7f4ad-132">Özellik bildiriminin gövdesi, yalnızca Property Ifadesiyle ve ifadesiyle olan özellik `Get` ve yordamları içerebilir `Set` [](property-statement.md) `End Property` .</span><span class="sxs-lookup"><span data-stu-id="7f4ad-132">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="7f4ad-133">Bu yordamlar dışında bir şey depolayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="7f4ad-133">It cannot store anything other than those procedures.</span></span> <span data-ttu-id="7f4ad-134">Özellikle, özelliğin geçerli değerini depolayaamaz.</span><span class="sxs-lookup"><span data-stu-id="7f4ad-134">In particular, it cannot store the property's current value.</span></span> <span data-ttu-id="7f4ad-135">Özellik yordamlarından birinde depolursa, diğer özellik yordamının bu değeri, özelliğin dışında depolamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7f4ad-135">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span></span> <span data-ttu-id="7f4ad-136">Her zamanki yaklaşım, değeri özelliği ile aynı düzeyde belirtilen [özel](../modifiers/private.md) bir değişkende depokullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="7f4ad-136">The usual approach is to store the value in a [Private](../modifiers/private.md) variable declared at the same level as the property.</span></span> <span data-ttu-id="7f4ad-137">`Set`Uygulandığı özelliğin içinde bir yordam tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7f4ad-137">You must define a `Set` procedure inside the property to which it applies.</span></span>  
  
 <span data-ttu-id="7f4ad-138">`Set`Yöntemi, bildiriminde kullanmadığınız müddetçe, kendisini kapsayan özelliğin erişim düzeyi olur `accessmodifier` `Set` .</span><span class="sxs-lookup"><span data-stu-id="7f4ad-138">The `Set` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Set` statement.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="7f4ad-139">Kurallar</span><span class="sxs-lookup"><span data-stu-id="7f4ad-139">Rules</span></span>  
  
- <span data-ttu-id="7f4ad-140">**Karışık erişim düzeyleri.**</span><span class="sxs-lookup"><span data-stu-id="7f4ad-140">**Mixed Access Levels.**</span></span> <span data-ttu-id="7f4ad-141">Okuma-yazma özelliği tanımlıyorsanız, isteğe bağlı olarak ya da yordam için farklı bir erişim düzeyi belirtebilirsiniz `Get` `Set` , ancak her ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="7f4ad-141">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="7f4ad-142">Bunu yaparsanız, yordam erişim düzeyinin özelliğin erişim düzeyinden daha kısıtlayıcı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7f4ad-142">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="7f4ad-143">Örneğin, özelliği bildirilirse, `Friend` `Set` yordamı bildirebilirsiniz `Private` , ancak kullanamazsınız `Public` .</span><span class="sxs-lookup"><span data-stu-id="7f4ad-143">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="7f4ad-144">Bir `WriteOnly` özellik tanımlıyorsanız, `Set` yordam tüm özelliği temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7f4ad-144">If you are defining a `WriteOnly` property, the `Set` procedure represents the entire property.</span></span> <span data-ttu-id="7f4ad-145">`Set`Özelliği için iki erişim düzeyi ayarlayacağından, için farklı bir erişim düzeyi bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="7f4ad-145">You cannot declare a different access level for `Set`, because that would set two access levels for the property.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="7f4ad-146">Davranış</span><span class="sxs-lookup"><span data-stu-id="7f4ad-146">Behavior</span></span>  
  
- <span data-ttu-id="7f4ad-147">**Bir özellik yordamından döndürülüyor.**</span><span class="sxs-lookup"><span data-stu-id="7f4ad-147">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="7f4ad-148">`Set`Yordam çağıran koda döndüğünde, yürütme, depolanacak değeri sağlayan deyimden sonra devam eder.</span><span class="sxs-lookup"><span data-stu-id="7f4ad-148">When the `Set` procedure returns to the calling code, execution continues following the statement that provided the value to be stored.</span></span>  
  
     <span data-ttu-id="7f4ad-149">`Set` özellik yordamları, [Return](return-statement.md) ya da [Exit deyimlerini](exit-statement.md)kullanarak dönebilir.</span><span class="sxs-lookup"><span data-stu-id="7f4ad-149">`Set` property procedures can return using either the [Return Statement](return-statement.md) or the [Exit Statement](exit-statement.md).</span></span>  
  
     <span data-ttu-id="7f4ad-150">`Exit Property`Ve `Return` deyimleri, bir özellik yordamından anında çıkış oluşmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="7f4ad-150">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="7f4ad-151">Herhangi bir sayıda `Exit Property` ve `Return` deyimi yordamda herhangi bir yerde görünebilir ve `Exit Property` ve deyimlerini karıştırabilirsiniz `Return` .</span><span class="sxs-lookup"><span data-stu-id="7f4ad-151">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f4ad-152">Örnek</span><span class="sxs-lookup"><span data-stu-id="7f4ad-152">Example</span></span>  

 <span data-ttu-id="7f4ad-153">Aşağıdaki örnek, `Set` bir özelliğin değerini ayarlamak için ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="7f4ad-153">The following example uses the `Set` statement to set the value of a property.</span></span>  
  
 [!code-vb[VbVbalrStatements#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#55)]  
  
## <a name="see-also"></a><span data-ttu-id="7f4ad-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f4ad-154">See also</span></span>

- [<span data-ttu-id="7f4ad-155">Get Deyimi</span><span class="sxs-lookup"><span data-stu-id="7f4ad-155">Get Statement</span></span>](get-statement.md)
- [<span data-ttu-id="7f4ad-156">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="7f4ad-156">Property Statement</span></span>](property-statement.md)
- [<span data-ttu-id="7f4ad-157">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="7f4ad-157">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="7f4ad-158">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="7f4ad-158">Property Procedures</span></span>](../../programming-guide/language-features/procedures/property-procedures.md)
