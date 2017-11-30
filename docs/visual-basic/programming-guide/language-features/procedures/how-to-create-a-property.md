---
title: "Nasıl yapılır: Özellik Oluşturma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, properties
- properties [Visual Basic]
ms.assetid: 4d229712-6be8-4c5c-bac5-06995ce9185a
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d140e6a10061f7fabe3d12c6cce5d0c201e103d6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-property-visual-basic"></a><span data-ttu-id="3cf56-102">Nasıl yapılır: Özellik Oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3cf56-102">How to: Create a Property (Visual Basic)</span></span>
<span data-ttu-id="3cf56-103">Özellik tanımı arasında içine bir `Property` deyimi ve bir `End Property` deyimi.</span><span class="sxs-lookup"><span data-stu-id="3cf56-103">You enclose a property definition between a `Property` statement and an `End Property` statement.</span></span> <span data-ttu-id="3cf56-104">Bu tanımı içinde tanımladığınız bir `Get` yordamı, bir `Set` yordam veya her ikisi de.</span><span class="sxs-lookup"><span data-stu-id="3cf56-104">Within this definition you define a `Get` procedure, a `Set` procedure, or both.</span></span> <span data-ttu-id="3cf56-105">Bu yordamlar özelliğin tüm kod arasındadır.</span><span class="sxs-lookup"><span data-stu-id="3cf56-105">All the property's code lies within these procedures.</span></span>  
  
 <span data-ttu-id="3cf56-106">`Get` Yordamı özelliğin değerini alır ve `Set` yordamı depolayan bir değer.</span><span class="sxs-lookup"><span data-stu-id="3cf56-106">The `Get` procedure retrieves the property's value, and the `Set` procedure stores a value.</span></span> <span data-ttu-id="3cf56-107">Özelliği okuma/yazma erişimine sahip olmasını istiyorsanız, her iki yordamı tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3cf56-107">If you want the property to have read/write access, you must define both procedures.</span></span> <span data-ttu-id="3cf56-108">Salt okunur özelliği için yalnızca tanımladığınız `Get`, ve salt yazılır özelliği için yalnızca tanımladığınız `Set`.</span><span class="sxs-lookup"><span data-stu-id="3cf56-108">For a read-only property, you define only `Get`, and for a write-only property, you define only `Set`.</span></span>  
  
### <a name="to-create-a-property"></a><span data-ttu-id="3cf56-109">Bir özellik oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="3cf56-109">To create a property</span></span>  
  
1.  <span data-ttu-id="3cf56-110">Tüm özellik veya yordamı dışında bir [Property deyimi](../../../../visual-basic/language-reference/statements/property-statement.md), ardından bir `End Property` deyimi.</span><span class="sxs-lookup"><span data-stu-id="3cf56-110">Outside any property or procedure, use a [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md), followed by an `End Property` statement.</span></span>  
  
2.  <span data-ttu-id="3cf56-111">Özelliği, parametreler alıyorsa izleyin `Property` yordamı sonra parantez içinde parametre listesi adı olan anahtar sözcük.</span><span class="sxs-lookup"><span data-stu-id="3cf56-111">If the property takes parameters, follow the `Property` keyword with the name of the procedure, then the parameter list in parentheses.</span></span>  
  
3.  <span data-ttu-id="3cf56-112">Parantezler ile izleyin bir `As` yan tümcesini özelliğin değerinin veri türü belirtin.</span><span class="sxs-lookup"><span data-stu-id="3cf56-112">Follow the parentheses with an `As` clause to specify the data type of the property's value.</span></span> <span data-ttu-id="3cf56-113">Salt yazılır özellik için bile veri türünü belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3cf56-113">You must specify the data type even for a write-only property.</span></span>  
  
4.  <span data-ttu-id="3cf56-114">Ekleme `Get` ve `Set` uygun yordamlar.</span><span class="sxs-lookup"><span data-stu-id="3cf56-114">Add `Get` and `Set` procedures, as appropriate.</span></span> <span data-ttu-id="3cf56-115">Aşağıdaki yönergeler bakın.</span><span class="sxs-lookup"><span data-stu-id="3cf56-115">See the following directions.</span></span>  
  
### <a name="to-create-a-get-procedure-that-retrieves-a-property-value"></a><span data-ttu-id="3cf56-116">Get yordamı oluşturmak için bir özellik değeri alır.</span><span class="sxs-lookup"><span data-stu-id="3cf56-116">To create a Get procedure that retrieves a property value</span></span>  
  
1.  <span data-ttu-id="3cf56-117">Arasında `Property` ve `End Property` deyimleri yazma bir [alma deyimi](../../../../visual-basic/language-reference/statements/get-statement.md)takip eden bir `End Get` deyimi.</span><span class="sxs-lookup"><span data-stu-id="3cf56-117">Between the `Property` and `End Property` statements, write a [Get Statement](../../../../visual-basic/language-reference/statements/get-statement.md), followed by an `End Get` statement.</span></span> <span data-ttu-id="3cf56-118">Herhangi bir parametre tanımlayın gerekmez `Get` yordamı.</span><span class="sxs-lookup"><span data-stu-id="3cf56-118">You do not need to define any parameters for the `Get` procedure.</span></span>  
  
2.  <span data-ttu-id="3cf56-119">Özelliğin değeri arasında almak için kod deyimleri yerleştirin `Get` ve `End Get` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="3cf56-119">Place the code statements to retrieve the property's value between the `Get` and `End Get` statements.</span></span> <span data-ttu-id="3cf56-120">Bu kod, diğer hesaplamalar ve oluşturma ve özelliğin değerini döndüren ek olarak veri değişikliklerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="3cf56-120">This code can include other calculations and data manipulations in addition to generating and returning the property's value.</span></span>  
  
3.  <span data-ttu-id="3cf56-121">Kullanım bir `Return` çağıran kodu özelliğin değerini döndürmek için deyimi.</span><span class="sxs-lookup"><span data-stu-id="3cf56-121">Use a `Return` statement to return the property's value to the calling code.</span></span>  
  
 <span data-ttu-id="3cf56-122">Yazmanız gereken bir `Get` okuma-yazma özelliği için ve salt okunur bir özellik için yordamı.</span><span class="sxs-lookup"><span data-stu-id="3cf56-122">You must write a `Get` procedure for a read-write property and for a read-only property.</span></span> <span data-ttu-id="3cf56-123">Değil tanımlamalısınız bir `Get` salt yazılır özelliği için yordamı.</span><span class="sxs-lookup"><span data-stu-id="3cf56-123">You must not define a `Get` procedure for a write-only property.</span></span>  
  
### <a name="to-create-a-set-procedure-that-writes-a-propertys-value"></a><span data-ttu-id="3cf56-124">Bir özelliğin değerini Yazar kümesi yordam oluşturma</span><span class="sxs-lookup"><span data-stu-id="3cf56-124">To create a Set procedure that writes a property's value</span></span>  
  
1.  <span data-ttu-id="3cf56-125">Arasında `Property` ve `End Property` deyimleri yazma bir [Set deyimi](../../../../visual-basic/language-reference/statements/set-statement.md)takip eden bir `End Set` deyimi.</span><span class="sxs-lookup"><span data-stu-id="3cf56-125">Between the `Property` and `End Property` statements, write a [Set Statement](../../../../visual-basic/language-reference/statements/set-statement.md), followed by an `End Set` statement.</span></span>  
  
2.  <span data-ttu-id="3cf56-126">İçinde `Set` deyimi, izleyin `Set` parantez içinde parametre listesi olan anahtar sözcük.</span><span class="sxs-lookup"><span data-stu-id="3cf56-126">In the `Set` statement, follow the `Set` keyword with a parameter list in parentheses.</span></span> <span data-ttu-id="3cf56-127">Bu parametre listesi çağrıyı yapan kod tarafından geçirilen değeri için en az bir değer parametresini eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3cf56-127">This parameter list must include at least a value parameter for the value passed by the calling code.</span></span> <span data-ttu-id="3cf56-128">Bu değer parametresi için varsayılan ad `Value`, ancak uygun durumlarda farklı bir ad kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3cf56-128">The default name for this value parameter is `Value`, but you can use a different name if appropriate.</span></span> <span data-ttu-id="3cf56-129">Değer parametresi type özelliği aynı verilerine sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3cf56-129">The value parameter must have the same data type as the property itself.</span></span>  
  
3.  <span data-ttu-id="3cf56-130">Özellik arasında bir değer depolamak üzere kod deyimleri yerleştirin `Set` ve `End Set` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="3cf56-130">Place the code statements to store a value in the property between the `Set` and `End Set` statements.</span></span> <span data-ttu-id="3cf56-131">Bu kod, diğer hesaplamalar ve doğrulama ve özelliğin değerini depolama yanı sıra veri değişikliklerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="3cf56-131">This code can include other calculations and data manipulations in addition to validating and storing the property's value.</span></span>  
  
4.  <span data-ttu-id="3cf56-132">Çağrıyı yapan kod tarafından sağlanan değer kabul etmek için değer parametresini kullanın.</span><span class="sxs-lookup"><span data-stu-id="3cf56-132">Use the value parameter to accept the value supplied by the calling code.</span></span> <span data-ttu-id="3cf56-133">Bu değer bir atama deyimde doğrudan depolamak veya depolanması için iç değerini hesaplamak için bir ifadede kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3cf56-133">You can either store this value directly in an assignment statement, or use it in an expression to calculate the internal value to be stored.</span></span>  
  
 <span data-ttu-id="3cf56-134">Yazmanız gereken bir `Set` yordamı salt yazılır özellik ve okuma-yazma özelliği için.</span><span class="sxs-lookup"><span data-stu-id="3cf56-134">You must write a `Set` procedure for a read-write property and for a write-only property.</span></span> <span data-ttu-id="3cf56-135">Değil tanımlamalısınız bir `Set` salt okunur bir özellik için yordamı.</span><span class="sxs-lookup"><span data-stu-id="3cf56-135">You must not define a `Set` procedure for a read-only property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3cf56-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="3cf56-136">Example</span></span>  
 <span data-ttu-id="3cf56-137">Aşağıdaki örnek, bir tam ad iki bağlı adları, ad ve Soyadı depolayan bir okuma/yazma özelliği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3cf56-137">The following example creates a read/write property that stores a full name as two constituent names, the first name and the last name.</span></span> <span data-ttu-id="3cf56-138">Ne zaman çağıran kodu okur `fullName`, `Get` yordamı iki bağlı adları birleştirir ve tam adını döndürür.</span><span class="sxs-lookup"><span data-stu-id="3cf56-138">When the calling code reads `fullName`, the `Get` procedure combines the two constituent names and returns the full name.</span></span> <span data-ttu-id="3cf56-139">Çağrıyı yapan kod yeni bir tam ad atarken `Set` yordamı iki bağlı adlarına bölün dener.</span><span class="sxs-lookup"><span data-stu-id="3cf56-139">When the calling code assigns a new full name, the `Set` procedure attempts to break it into two constituent names.</span></span> <span data-ttu-id="3cf56-140">Bir alan bulamazsa, tüm ad depolar.</span><span class="sxs-lookup"><span data-stu-id="3cf56-140">If it does not find a space, it stores it all as the first name.</span></span>  
  
 [!code-vb[VbVbcnProcedures#8](./codesnippet/VisualBasic/how-to-create-a-property_1.vb)]  
  
 <span data-ttu-id="3cf56-141">Aşağıdaki örnek özellik yordamları tipik çağrı gösterilir `fullName`.</span><span class="sxs-lookup"><span data-stu-id="3cf56-141">The following example shows typical calls to the property procedures of `fullName`.</span></span> <span data-ttu-id="3cf56-142">İlk çağrıda özellik değerini ayarlar ve ikinci çağrı alır.</span><span class="sxs-lookup"><span data-stu-id="3cf56-142">The first call sets the property value and the second call retrieves it.</span></span>  
  
 [!code-vb[VbVbcnProcedures#9](./codesnippet/VisualBasic/how-to-create-a-property_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="3cf56-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3cf56-143">See Also</span></span>  
 [<span data-ttu-id="3cf56-144">Yordamları</span><span class="sxs-lookup"><span data-stu-id="3cf56-144">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="3cf56-145">Özellik yordamları</span><span class="sxs-lookup"><span data-stu-id="3cf56-145">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="3cf56-146">Parametreler ve bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="3cf56-146">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="3cf56-147">Visual Basic'de özellikler ve değişkenler arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="3cf56-147">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)  
 [<span data-ttu-id="3cf56-148">Nasıl yapılır: bir özelliği karışık erişim düzeyleriyle bildirme</span><span class="sxs-lookup"><span data-stu-id="3cf56-148">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [<span data-ttu-id="3cf56-149">Nasıl yapılır: bir özellik yordamı çağırma</span><span class="sxs-lookup"><span data-stu-id="3cf56-149">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)  
 [<span data-ttu-id="3cf56-150">Nasıl yapılır: bildirme ve Visual Basic'te varsayılan özelliğini çağırın</span><span class="sxs-lookup"><span data-stu-id="3cf56-150">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="3cf56-151">Nasıl yapılır: bir özelliğe değer ekleme</span><span class="sxs-lookup"><span data-stu-id="3cf56-151">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)  
 [<span data-ttu-id="3cf56-152">Nasıl yapılır: bir özellikten değer alma</span><span class="sxs-lookup"><span data-stu-id="3cf56-152">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
