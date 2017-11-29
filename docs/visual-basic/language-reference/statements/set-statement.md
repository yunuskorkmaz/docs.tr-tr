---
title: Set Deyimi (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Set
helpviewer_keywords:
- property procedures [Visual Basic], Set statements
- Set statement [Visual Basic]
- Set statement [Visual Basic], syntax
- write-only properties
- properties [Visual Basic], write-only
ms.assetid: 9ecc27b4-df84-420d-9075-db25455fb3cd
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3b18e6c858e64e78d7ab85fdaafd70e510f7a02f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="set-statement-visual-basic"></a><span data-ttu-id="2a6bf-102">Set Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2a6bf-102">Set Statement (Visual Basic)</span></span>
<span data-ttu-id="2a6bf-103">Bildiren bir `Set` bir özellik için bir değer atamak için kullanılan özellik yordamı.</span><span class="sxs-lookup"><span data-stu-id="2a6bf-103">Declares a `Set` property procedure used to assign a value to a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a6bf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2a6bf-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a><span data-ttu-id="2a6bf-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="2a6bf-105">Parts</span></span>  
 `attributelist`  
 <span data-ttu-id="2a6bf-106">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="2a6bf-106">Optional.</span></span> <span data-ttu-id="2a6bf-107">Bkz: [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="2a6bf-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
 `accessmodifier`  
 <span data-ttu-id="2a6bf-108">İsteğe bağlı en `Get` ve `Set` bu özellik deyimlerinde.</span><span class="sxs-lookup"><span data-stu-id="2a6bf-108">Optional on at most one of the `Get` and `Set` statements in this property.</span></span> <span data-ttu-id="2a6bf-109">Aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="2a6bf-109">Can be one of the following:</span></span>  
  
-   [<span data-ttu-id="2a6bf-110">Korumalı</span><span class="sxs-lookup"><span data-stu-id="2a6bf-110">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
-   [<span data-ttu-id="2a6bf-111">Arkadaş</span><span class="sxs-lookup"><span data-stu-id="2a6bf-111">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
-   [<span data-ttu-id="2a6bf-112">Özel</span><span class="sxs-lookup"><span data-stu-id="2a6bf-112">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
-   `Protected Friend`  
  
 <span data-ttu-id="2a6bf-113">Bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="2a6bf-113">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 `value`  
 <span data-ttu-id="2a6bf-114">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="2a6bf-114">Required.</span></span> <span data-ttu-id="2a6bf-115">Özelliği için yeni değer içeren bir parametre.</span><span class="sxs-lookup"><span data-stu-id="2a6bf-115">Parameter containing the new value for the property.</span></span>  
  
 `datatype`  
 <span data-ttu-id="2a6bf-116">Gerekli olursa `Option Strict` olan `On`.</span><span class="sxs-lookup"><span data-stu-id="2a6bf-116">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="2a6bf-117">Veri türü `value` parametresi.</span><span class="sxs-lookup"><span data-stu-id="2a6bf-117">Data type of the `value` parameter.</span></span> <span data-ttu-id="2a6bf-118">Belirtilen veri türü özelliğin veri türü ile aynı olması gerekir, bu `Set` deyimi bildirildi.</span><span class="sxs-lookup"><span data-stu-id="2a6bf-118">The data type specified must be the same as the data type of the property where this `Set` statement is declared.</span></span>  
  
 `statements`  
 <span data-ttu-id="2a6bf-119">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="2a6bf-119">Optional.</span></span> <span data-ttu-id="2a6bf-120">Çalıştırılan bir veya daha fazla deyimleri `Set` özellik yordamı çağrılır.</span><span class="sxs-lookup"><span data-stu-id="2a6bf-120">One or more statements that run when the `Set` property procedure is called.</span></span>  
  
 `End Set`  
 <span data-ttu-id="2a6bf-121">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="2a6bf-121">Required.</span></span> <span data-ttu-id="2a6bf-122">Tanımını sonlandırır `Set` özellik yordamı.</span><span class="sxs-lookup"><span data-stu-id="2a6bf-122">Terminates the definition of the `Set` property procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a6bf-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2a6bf-123">Remarks</span></span>  
 <span data-ttu-id="2a6bf-124">Her özellik olmalıdır bir `Set` özellik yordamı özelliği işaretlenmemişse `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="2a6bf-124">Every property must have a `Set` property procedure unless the property is marked `ReadOnly`.</span></span> <span data-ttu-id="2a6bf-125">`Set` Yordamı özelliğinin değeri ayarlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2a6bf-125">The `Set` procedure is used to set the value of the property.</span></span>  
  
 <span data-ttu-id="2a6bf-126">Visual Basic otomatik olarak çağıran bir özelliğin `Set` atama deyiminin özelliğinde depolanması için bir değer sağladığında yordamı.</span><span class="sxs-lookup"><span data-stu-id="2a6bf-126">Visual Basic automatically calls a property's `Set` procedure when an assignment statement provides a value to be stored in the property.</span></span>  
  
 <span data-ttu-id="2a6bf-127">Visual Basic geçirir parametresi `Set` yordam sırasında özelliği atamaları.</span><span class="sxs-lookup"><span data-stu-id="2a6bf-127">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="2a6bf-128">İçin bir parametre belirtmezseniz `Set`, tümleşik geliştirme ortamı (IDE) adlı bir örtük parametresini kullanır `value`.</span><span class="sxs-lookup"><span data-stu-id="2a6bf-128">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="2a6bf-129">Parametre özelliğine atanan değer tutar.</span><span class="sxs-lookup"><span data-stu-id="2a6bf-129">The parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="2a6bf-130">Genellikle bu değer bir özel yerel değişkende depolayın ve döndürün her `Get` yordamı çağrılır.</span><span class="sxs-lookup"><span data-stu-id="2a6bf-130">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>  
  
 <span data-ttu-id="2a6bf-131">Özellik bildirimi gövdesi yalnızca özelliğin içerebilir `Get` ve `Set` yordamları arasında [Property deyimi](../../../visual-basic/language-reference/statements/property-statement.md) ve `End Property` deyimi.</span><span class="sxs-lookup"><span data-stu-id="2a6bf-131">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="2a6bf-132">Bu yordamlar dışında her şey depolanamıyor.</span><span class="sxs-lookup"><span data-stu-id="2a6bf-132">It cannot store anything other than those procedures.</span></span> <span data-ttu-id="2a6bf-133">Özellikle, bu özelliğin geçerli değeri depolanamıyor.</span><span class="sxs-lookup"><span data-stu-id="2a6bf-133">In particular, it cannot store the property's current value.</span></span> <span data-ttu-id="2a6bf-134">Özellik yordamları birini içinde depolamak, bir özellik yordamı, erişemediği için bu değeri özellik dışında depolamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2a6bf-134">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span></span> <span data-ttu-id="2a6bf-135">Değeri depolamak için normal yaklaşımdır bir [özel](../../../visual-basic/language-reference/modifiers/private.md) değişkeni bildirilen özelliği ile aynı düzeyde.</span><span class="sxs-lookup"><span data-stu-id="2a6bf-135">The usual approach is to store the value in a [Private](../../../visual-basic/language-reference/modifiers/private.md) variable declared at the same level as the property.</span></span> <span data-ttu-id="2a6bf-136">Tanımlamanız gerekir bir `Set` yordamı uygulandığı özelliği içinde.</span><span class="sxs-lookup"><span data-stu-id="2a6bf-136">You must define a `Set` procedure inside the property to which it applies.</span></span>  
  
 <span data-ttu-id="2a6bf-137">`Set` Yordamı kullanmadığınız sürece, içeren özelliğinin erişim düzeyini varsayılan olarak `accessmodifier` içinde `Set` deyimi.</span><span class="sxs-lookup"><span data-stu-id="2a6bf-137">The `Set` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Set` statement.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="2a6bf-138">Kurallar</span><span class="sxs-lookup"><span data-stu-id="2a6bf-138">Rules</span></span>  
  
-   <span data-ttu-id="2a6bf-139">**Karışık erişim düzeyleri.**</span><span class="sxs-lookup"><span data-stu-id="2a6bf-139">**Mixed Access Levels.**</span></span> <span data-ttu-id="2a6bf-140">Bir okuma-yazma özelliği tanımlıyorsanız, isteğe bağlı olarak farklı erişim düzeyi için ya da belirtebilirsiniz `Get` veya `Set` yordamı, ancak ikisini birden değil.</span><span class="sxs-lookup"><span data-stu-id="2a6bf-140">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="2a6bf-141">Bunu yaparsanız, yordam erişim düzeyi özelliğin erişim düzeyinden daha kısıtlayıcı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2a6bf-141">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="2a6bf-142">Örneğin, özellik bildirilirse `Friend`, bildirebilirsiniz `Set` yordam `Private`, ama `Public`.</span><span class="sxs-lookup"><span data-stu-id="2a6bf-142">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="2a6bf-143">Tanımlıyorsanız, bir `WriteOnly` özelliği, `Set` yordamı tüm özelliğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2a6bf-143">If you are defining a `WriteOnly` property, the `Set` procedure represents the entire property.</span></span> <span data-ttu-id="2a6bf-144">Farklı bir erişim düzeyini bildiremezsiniz `Set`, özellik için iki erişim düzeyleri ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2a6bf-144">You cannot declare a different access level for `Set`, because that would set two access levels for the property.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="2a6bf-145">Davranış</span><span class="sxs-lookup"><span data-stu-id="2a6bf-145">Behavior</span></span>  
  
-   <span data-ttu-id="2a6bf-146">**Bir özellik yordamından döndürülüyor.**</span><span class="sxs-lookup"><span data-stu-id="2a6bf-146">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="2a6bf-147">Zaman `Set` yordamı çağıran kodu döndürür, değerin depolanması için sağlanan deyimi yürütme devam eder.</span><span class="sxs-lookup"><span data-stu-id="2a6bf-147">When the `Set` procedure returns to the calling code, execution continues following the statement that provided the value to be stored.</span></span>  
  
     <span data-ttu-id="2a6bf-148">`Set`özellik yordamları kullanarak dönebilirsiniz [dönüş deyimi](../../../visual-basic/language-reference/statements/return-statement.md) veya [çıkış deyimi](../../../visual-basic/language-reference/statements/exit-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2a6bf-148">`Set` property procedures can return using either the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) or the [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md).</span></span>  
  
     <span data-ttu-id="2a6bf-149">`Exit Property` Ve `Return` deyimleri neden hemen bir çıkış bir özellik yordam.</span><span class="sxs-lookup"><span data-stu-id="2a6bf-149">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="2a6bf-150">Herhangi bir sayıda `Exit Property` ve `Return` deyimleri yordamda herhangi bir yerinde görünebilir ve karıştırabilir miyim `Exit Property` ve `Return` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="2a6bf-150">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a6bf-151">Örnek</span><span class="sxs-lookup"><span data-stu-id="2a6bf-151">Example</span></span>  
 <span data-ttu-id="2a6bf-152">Aşağıdaki örnek kullanır `Set` bir özelliğin değerini ayarlamak için ifade.</span><span class="sxs-lookup"><span data-stu-id="2a6bf-152">The following example uses the `Set` statement to set the value of a property.</span></span>  
  
 [!code-vb[VbVbalrStatements#55](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/set-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="2a6bf-153">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2a6bf-153">See Also</span></span>  
 [<span data-ttu-id="2a6bf-154">Get deyimi</span><span class="sxs-lookup"><span data-stu-id="2a6bf-154">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)  
 [<span data-ttu-id="2a6bf-155">Property deyimi</span><span class="sxs-lookup"><span data-stu-id="2a6bf-155">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="2a6bf-156">Sub deyimi</span><span class="sxs-lookup"><span data-stu-id="2a6bf-156">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="2a6bf-157">Özellik yordamları</span><span class="sxs-lookup"><span data-stu-id="2a6bf-157">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
