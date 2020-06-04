---
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
ms.openlocfilehash: 49d4c36805b64d7232a94e818256723a0437b6ef
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404193"
---
# <a name="set-statement-visual-basic"></a><span data-ttu-id="a5f32-102">Set Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5f32-102">Set Statement (Visual Basic)</span></span>
<span data-ttu-id="a5f32-103">`Set`Bir özelliğe değer atamak için kullanılan bir özellik yordamı bildirir.</span><span class="sxs-lookup"><span data-stu-id="a5f32-103">Declares a `Set` property procedure used to assign a value to a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5f32-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a5f32-104">Syntax</span></span>  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a><span data-ttu-id="a5f32-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="a5f32-105">Parts</span></span>  
 `attributelist`  
 <span data-ttu-id="a5f32-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="a5f32-106">Optional.</span></span> <span data-ttu-id="a5f32-107">Bkz. [öznitelik listesi](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="a5f32-107">See [Attribute List](attribute-list.md).</span></span>  
  
 `accessmodifier`  
 <span data-ttu-id="a5f32-108">`Get`Bu özellikte ve deyimlerden en fazla bir isteğe bağlı `Set` .</span><span class="sxs-lookup"><span data-stu-id="a5f32-108">Optional on at most one of the `Get` and `Set` statements in this property.</span></span> <span data-ttu-id="a5f32-109">Aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="a5f32-109">Can be one of the following:</span></span>  
  
- [<span data-ttu-id="a5f32-110">Korunamadı</span><span class="sxs-lookup"><span data-stu-id="a5f32-110">Protected</span></span>](../modifiers/protected.md)  
  
- [<span data-ttu-id="a5f32-111">Dost</span><span class="sxs-lookup"><span data-stu-id="a5f32-111">Friend</span></span>](../modifiers/friend.md)  
  
- [<span data-ttu-id="a5f32-112">Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="a5f32-112">Private</span></span>](../modifiers/private.md)  
  
- `Protected Friend`  
  
 <span data-ttu-id="a5f32-113">[Visual Basic erişim düzeylerine](../../programming-guide/language-features/declared-elements/access-levels.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="a5f32-113">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 `value`  
 <span data-ttu-id="a5f32-114">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a5f32-114">Required.</span></span> <span data-ttu-id="a5f32-115">Özelliği için yeni değeri içeren parametre.</span><span class="sxs-lookup"><span data-stu-id="a5f32-115">Parameter containing the new value for the property.</span></span>  
  
 `datatype`  
 <span data-ttu-id="a5f32-116">İse gereklidir `Option Strict` `On` .</span><span class="sxs-lookup"><span data-stu-id="a5f32-116">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="a5f32-117">Parametrenin veri türü `value` .</span><span class="sxs-lookup"><span data-stu-id="a5f32-117">Data type of the `value` parameter.</span></span> <span data-ttu-id="a5f32-118">Belirtilen veri türü, bu deyimin bildirildiği özelliğin veri türüyle aynı olmalıdır `Set` .</span><span class="sxs-lookup"><span data-stu-id="a5f32-118">The data type specified must be the same as the data type of the property where this `Set` statement is declared.</span></span>  
  
 `statements`  
 <span data-ttu-id="a5f32-119">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="a5f32-119">Optional.</span></span> <span data-ttu-id="a5f32-120">Özellik yordamı çağrıldığında çalışan bir veya daha fazla deyim `Set` .</span><span class="sxs-lookup"><span data-stu-id="a5f32-120">One or more statements that run when the `Set` property procedure is called.</span></span>  
  
 `End Set`  
 <span data-ttu-id="a5f32-121">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a5f32-121">Required.</span></span> <span data-ttu-id="a5f32-122">`Set`Özellik yordamının tanımını sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="a5f32-122">Terminates the definition of the `Set` property procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5f32-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a5f32-123">Remarks</span></span>  
 <span data-ttu-id="a5f32-124">Özellik işaretlenmedikçe her özelliğin bir özellik yordamına sahip olması gerekir `Set` `ReadOnly` .</span><span class="sxs-lookup"><span data-stu-id="a5f32-124">Every property must have a `Set` property procedure unless the property is marked `ReadOnly`.</span></span> <span data-ttu-id="a5f32-125">`Set`Yordamı, özelliğinin değerini ayarlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a5f32-125">The `Set` procedure is used to set the value of the property.</span></span>  
  
 <span data-ttu-id="a5f32-126">`Set`Bir atama ekstresi özellikte depolanacak bir değer sağlıyorsa, bir özelliğin yordamını otomatik olarak çağırır Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a5f32-126">Visual Basic automatically calls a property's `Set` procedure when an assignment statement provides a value to be stored in the property.</span></span>  
  
 <span data-ttu-id="a5f32-127">Visual Basic, `Set` özellik atamaları sırasında yordama bir parametre geçirir.</span><span class="sxs-lookup"><span data-stu-id="a5f32-127">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="a5f32-128">İçin bir parametre belirtmezseniz `Set` , tümleşik geliştirme ortamı (IDE) adlı örtülü bir parametre kullanır `value` .</span><span class="sxs-lookup"><span data-stu-id="a5f32-128">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="a5f32-129">Parametresi, özelliğine atanacak değeri tutar.</span><span class="sxs-lookup"><span data-stu-id="a5f32-129">The parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="a5f32-130">Genellikle bu değeri özel bir yerel değişkende depoluyordu ve yordam her çağrıldığında döndürülür `Get` .</span><span class="sxs-lookup"><span data-stu-id="a5f32-130">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>  
  
 <span data-ttu-id="a5f32-131">Özellik bildiriminin gövdesi, yalnızca Property Ifadesiyle ve ifadesiyle olan özellik `Get` ve yordamları içerebilir `Set` [Property Statement](property-statement.md) `End Property` .</span><span class="sxs-lookup"><span data-stu-id="a5f32-131">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="a5f32-132">Bu yordamlar dışında bir şey depolayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="a5f32-132">It cannot store anything other than those procedures.</span></span> <span data-ttu-id="a5f32-133">Özellikle, özelliğin geçerli değerini depolayaamaz.</span><span class="sxs-lookup"><span data-stu-id="a5f32-133">In particular, it cannot store the property's current value.</span></span> <span data-ttu-id="a5f32-134">Özellik yordamlarından birinde depolursa, diğer özellik yordamının bu değeri, özelliğin dışında depolamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a5f32-134">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span></span> <span data-ttu-id="a5f32-135">Her zamanki yaklaşım, değeri özelliği ile aynı düzeyde belirtilen [özel](../modifiers/private.md) bir değişkende depokullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="a5f32-135">The usual approach is to store the value in a [Private](../modifiers/private.md) variable declared at the same level as the property.</span></span> <span data-ttu-id="a5f32-136">`Set`Uygulandığı özelliğin içinde bir yordam tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a5f32-136">You must define a `Set` procedure inside the property to which it applies.</span></span>  
  
 <span data-ttu-id="a5f32-137">`Set`Yöntemi, bildiriminde kullanmadığınız müddetçe, kendisini kapsayan özelliğin erişim düzeyi olur `accessmodifier` `Set` .</span><span class="sxs-lookup"><span data-stu-id="a5f32-137">The `Set` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Set` statement.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="a5f32-138">Kurallar</span><span class="sxs-lookup"><span data-stu-id="a5f32-138">Rules</span></span>  
  
- <span data-ttu-id="a5f32-139">**Karışık erişim düzeyleri.**</span><span class="sxs-lookup"><span data-stu-id="a5f32-139">**Mixed Access Levels.**</span></span> <span data-ttu-id="a5f32-140">Okuma-yazma özelliği tanımlıyorsanız, isteğe bağlı olarak ya da yordam için farklı bir erişim düzeyi belirtebilirsiniz `Get` `Set` , ancak her ikisini birden belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5f32-140">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="a5f32-141">Bunu yaparsanız, yordam erişim düzeyinin özelliğin erişim düzeyinden daha kısıtlayıcı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a5f32-141">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="a5f32-142">Örneğin, özelliği bildirilirse, `Friend` `Set` yordamı bildirebilirsiniz `Private` , ancak kullanamazsınız `Public` .</span><span class="sxs-lookup"><span data-stu-id="a5f32-142">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="a5f32-143">Bir `WriteOnly` özellik tanımlıyorsanız, `Set` yordam tüm özelliği temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a5f32-143">If you are defining a `WriteOnly` property, the `Set` procedure represents the entire property.</span></span> <span data-ttu-id="a5f32-144">`Set`Özelliği için iki erişim düzeyi ayarlayacağından, için farklı bir erişim düzeyi bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5f32-144">You cannot declare a different access level for `Set`, because that would set two access levels for the property.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="a5f32-145">Davranış</span><span class="sxs-lookup"><span data-stu-id="a5f32-145">Behavior</span></span>  
  
- <span data-ttu-id="a5f32-146">**Bir özellik yordamından döndürülüyor.**</span><span class="sxs-lookup"><span data-stu-id="a5f32-146">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="a5f32-147">`Set`Yordam çağıran koda döndüğünde, yürütme, depolanacak değeri sağlayan deyimden sonra devam eder.</span><span class="sxs-lookup"><span data-stu-id="a5f32-147">When the `Set` procedure returns to the calling code, execution continues following the statement that provided the value to be stored.</span></span>  
  
     <span data-ttu-id="a5f32-148">`Set`özellik yordamları, [Return](return-statement.md) ya da [Exit deyimlerini](exit-statement.md)kullanarak dönebilir.</span><span class="sxs-lookup"><span data-stu-id="a5f32-148">`Set` property procedures can return using either the [Return Statement](return-statement.md) or the [Exit Statement](exit-statement.md).</span></span>  
  
     <span data-ttu-id="a5f32-149">`Exit Property`Ve `Return` deyimleri, bir özellik yordamından anında çıkış oluşmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="a5f32-149">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="a5f32-150">Herhangi bir sayıda `Exit Property` ve `Return` deyimi yordamda herhangi bir yerde görünebilir ve `Exit Property` ve deyimlerini karıştırabilirsiniz `Return` .</span><span class="sxs-lookup"><span data-stu-id="a5f32-150">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5f32-151">Örnek</span><span class="sxs-lookup"><span data-stu-id="a5f32-151">Example</span></span>  
 <span data-ttu-id="a5f32-152">Aşağıdaki örnek, `Set` bir özelliğin değerini ayarlamak için ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a5f32-152">The following example uses the `Set` statement to set the value of a property.</span></span>  
  
 [!code-vb[VbVbalrStatements#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#55)]  
  
## <a name="see-also"></a><span data-ttu-id="a5f32-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a5f32-153">See also</span></span>

- [<span data-ttu-id="a5f32-154">Get Deyimi</span><span class="sxs-lookup"><span data-stu-id="a5f32-154">Get Statement</span></span>](get-statement.md)
- [<span data-ttu-id="a5f32-155">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="a5f32-155">Property Statement</span></span>](property-statement.md)
- [<span data-ttu-id="a5f32-156">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="a5f32-156">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="a5f32-157">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="a5f32-157">Property Procedures</span></span>](../../programming-guide/language-features/procedures/property-procedures.md)
