---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Özellik oluşturma (Visual Basic)'
title: 'Nasıl yapılır: Özellik Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, properties
- properties [Visual Basic]
ms.assetid: 4d229712-6be8-4c5c-bac5-06995ce9185a
ms.openlocfilehash: cf6c76f6a6284cf055f16cf3973da1bb1c54e48d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472481"
---
# <a name="how-to-create-a-property-visual-basic"></a><span data-ttu-id="46fc5-103">Nasıl yapılır: Özellik Oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46fc5-103">How to: Create a Property (Visual Basic)</span></span>

<span data-ttu-id="46fc5-104">Bir ifade ve bir ifade arasında bir özellik tanımı çevrelemektir `Property` `End Property` .</span><span class="sxs-lookup"><span data-stu-id="46fc5-104">You enclose a property definition between a `Property` statement and an `End Property` statement.</span></span> <span data-ttu-id="46fc5-105">Bu tanım içinde bir `Get` yordam, `Set` yordam veya her ikisini de tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="46fc5-105">Within this definition you define a `Get` procedure, a `Set` procedure, or both.</span></span> <span data-ttu-id="46fc5-106">Tüm özellik kodu bu yordamların içinde yer alır.</span><span class="sxs-lookup"><span data-stu-id="46fc5-106">All the property's code lies within these procedures.</span></span>  
  
 <span data-ttu-id="46fc5-107">`Get`Yordam, özelliğin değerini alır ve `Set` yordam bir değer depolar.</span><span class="sxs-lookup"><span data-stu-id="46fc5-107">The `Get` procedure retrieves the property's value, and the `Set` procedure stores a value.</span></span> <span data-ttu-id="46fc5-108">Özelliğin okuma/yazma erişimine sahip olmasını istiyorsanız her iki yordamı da tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="46fc5-108">If you want the property to have read/write access, you must define both procedures.</span></span> <span data-ttu-id="46fc5-109">Salt okunurdur bir özellik için, yalnızca tanımlarsınız ve yalnızca `Get` bir salt yazılır özellik için tanımlarsınız `Set` .</span><span class="sxs-lookup"><span data-stu-id="46fc5-109">For a read-only property, you define only `Get`, and for a write-only property, you define only `Set`.</span></span>  
  
### <a name="to-create-a-property"></a><span data-ttu-id="46fc5-110">Bir özellik oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="46fc5-110">To create a property</span></span>  
  
1. <span data-ttu-id="46fc5-111">Herhangi bir özellik veya yordamın dışında, bir [Property ifadesini](../../../language-reference/statements/property-statement.md)ve ardından bir `End Property` ifadesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="46fc5-111">Outside any property or procedure, use a [Property Statement](../../../language-reference/statements/property-statement.md), followed by an `End Property` statement.</span></span>  
  
2. <span data-ttu-id="46fc5-112">Özelliği parametreleri alırsa, `Property` yordam adı ile anahtar sözcüğü, sonra parantez içindeki parametre listesini izleyin.</span><span class="sxs-lookup"><span data-stu-id="46fc5-112">If the property takes parameters, follow the `Property` keyword with the name of the procedure, then the parameter list in parentheses.</span></span>  
  
3. <span data-ttu-id="46fc5-113">`As`Özelliğin değerinin veri türünü belirtmek için bir yan tümcesiyle ayraçları izleyin.</span><span class="sxs-lookup"><span data-stu-id="46fc5-113">Follow the parentheses with an `As` clause to specify the data type of the property's value.</span></span> <span data-ttu-id="46fc5-114">Salt yazılır bir özellik için bile veri türünü belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="46fc5-114">You must specify the data type even for a write-only property.</span></span>  
  
4. <span data-ttu-id="46fc5-115">`Get`Ve `Set` yordamlarını uygun şekilde ekleyin.</span><span class="sxs-lookup"><span data-stu-id="46fc5-115">Add `Get` and `Set` procedures, as appropriate.</span></span> <span data-ttu-id="46fc5-116">Aşağıdaki yönergelere bakın.</span><span class="sxs-lookup"><span data-stu-id="46fc5-116">See the following directions.</span></span>  
  
### <a name="to-create-a-get-procedure-that-retrieves-a-property-value"></a><span data-ttu-id="46fc5-117">Bir özellik değeri alan bir Get yordamı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="46fc5-117">To create a Get procedure that retrieves a property value</span></span>  
  
1. <span data-ttu-id="46fc5-118">`Property`Ve deyimleri arasında bir `End Property` [Get deyimi](../../../language-reference/statements/get-statement.md), ardından bir `End Get` deyimi yazın.</span><span class="sxs-lookup"><span data-stu-id="46fc5-118">Between the `Property` and `End Property` statements, write a [Get Statement](../../../language-reference/statements/get-statement.md), followed by an `End Get` statement.</span></span> <span data-ttu-id="46fc5-119">Yordam için herhangi bir parametre tanımlamanız gerekmez `Get` .</span><span class="sxs-lookup"><span data-stu-id="46fc5-119">You do not need to define any parameters for the `Get` procedure.</span></span>  
  
2. <span data-ttu-id="46fc5-120">Ve deyimleri arasında özelliğin değerini almak için kod deyimlerini yerleştirin `Get` `End Get` .</span><span class="sxs-lookup"><span data-stu-id="46fc5-120">Place the code statements to retrieve the property's value between the `Get` and `End Get` statements.</span></span> <span data-ttu-id="46fc5-121">Bu kod, özelliğin değerini oluşturma ve döndürmenin yanı sıra diğer hesaplamalar ve veri düzenlemeleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="46fc5-121">This code can include other calculations and data manipulations in addition to generating and returning the property's value.</span></span>  
  
3. <span data-ttu-id="46fc5-122">`Return`Özelliğin değerini çağıran koda döndürmek için bir ifade kullanın.</span><span class="sxs-lookup"><span data-stu-id="46fc5-122">Use a `Return` statement to return the property's value to the calling code.</span></span>  
  
 <span data-ttu-id="46fc5-123">`Get`Okuma-yazma özelliği için ve salt okunurdur özelliği için bir yordam yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="46fc5-123">You must write a `Get` procedure for a read-write property and for a read-only property.</span></span> <span data-ttu-id="46fc5-124">`Get`Salt yazılır özellik için bir yordam tanımlamamalısınız.</span><span class="sxs-lookup"><span data-stu-id="46fc5-124">You must not define a `Get` procedure for a write-only property.</span></span>  
  
### <a name="to-create-a-set-procedure-that-writes-a-propertys-value"></a><span data-ttu-id="46fc5-125">Özelliğin değerini yazan bir ayarlama yordamı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="46fc5-125">To create a Set procedure that writes a property's value</span></span>  
  
1. <span data-ttu-id="46fc5-126">`Property`Ve deyimleri arasında bir `End Property` [set deyimi](../../../language-reference/statements/set-statement.md)ve ardından bir `End Set` deyimi yazın.</span><span class="sxs-lookup"><span data-stu-id="46fc5-126">Between the `Property` and `End Property` statements, write a [Set Statement](../../../language-reference/statements/set-statement.md), followed by an `End Set` statement.</span></span>  
  
2. <span data-ttu-id="46fc5-127">`Set`İfadesinde, `Set` parantez içinde bir parametre listesi ile anahtar sözcüğünü izleyin.</span><span class="sxs-lookup"><span data-stu-id="46fc5-127">In the `Set` statement, follow the `Set` keyword with a parameter list in parentheses.</span></span> <span data-ttu-id="46fc5-128">Bu parametre listesi, çağıran kodun geçirilmiş değeri için en az bir değer parametresi içermelidir.</span><span class="sxs-lookup"><span data-stu-id="46fc5-128">This parameter list must include at least a value parameter for the value passed by the calling code.</span></span> <span data-ttu-id="46fc5-129">Bu değer parametresinin varsayılan adı vardır `Value` ancak uygunsa farklı bir ad kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46fc5-129">The default name for this value parameter is `Value`, but you can use a different name if appropriate.</span></span> <span data-ttu-id="46fc5-130">Değer parametresi, özelliğin kendisiyle aynı veri türüne sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="46fc5-130">The value parameter must have the same data type as the property itself.</span></span>  
  
3. <span data-ttu-id="46fc5-131">Ve deyimleri arasındaki özellikte bir değeri depolamak için kod deyimlerini yerleştirin `Set` `End Set` .</span><span class="sxs-lookup"><span data-stu-id="46fc5-131">Place the code statements to store a value in the property between the `Set` and `End Set` statements.</span></span> <span data-ttu-id="46fc5-132">Bu kod, özelliğin değerini doğrulamaya ve depolamaya ek olarak diğer hesaplamalar ve veri düzenlemeleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="46fc5-132">This code can include other calculations and data manipulations in addition to validating and storing the property's value.</span></span>  
  
4. <span data-ttu-id="46fc5-133">Çağıran kodun sağladığı değeri kabul etmek için value parametresini kullanın.</span><span class="sxs-lookup"><span data-stu-id="46fc5-133">Use the value parameter to accept the value supplied by the calling code.</span></span> <span data-ttu-id="46fc5-134">Bu değeri doğrudan bir atama deyiminde saklayabilir veya depolanacağı iç değeri hesaplamak için bir ifadede kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46fc5-134">You can either store this value directly in an assignment statement, or use it in an expression to calculate the internal value to be stored.</span></span>  
  
 <span data-ttu-id="46fc5-135">`Set`Okuma-yazma özelliği için ve salt yazılır bir özellik için bir yordam yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="46fc5-135">You must write a `Set` procedure for a read-write property and for a write-only property.</span></span> <span data-ttu-id="46fc5-136">`Set`Salt okunurdur özelliği için bir yordam tanımlamamalısınız.</span><span class="sxs-lookup"><span data-stu-id="46fc5-136">You must not define a `Set` procedure for a read-only property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46fc5-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="46fc5-137">Example</span></span>  

 <span data-ttu-id="46fc5-138">Aşağıdaki örnek, tam adı iki anayent adı, ilk adı ve soyadı olarak depolayan bir okuma/yazma özelliği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="46fc5-138">The following example creates a read/write property that stores a full name as two constituent names, the first name and the last name.</span></span> <span data-ttu-id="46fc5-139">Çağıran kod okuduğunda `fullName` , `Get` yordam iki anayent adı birleştirir ve tam adı döndürür.</span><span class="sxs-lookup"><span data-stu-id="46fc5-139">When the calling code reads `fullName`, the `Get` procedure combines the two constituent names and returns the full name.</span></span> <span data-ttu-id="46fc5-140">Çağıran kod yeni bir tam ad atarken, `Set` yordam onu iki anayada bölmek için çalışır.</span><span class="sxs-lookup"><span data-stu-id="46fc5-140">When the calling code assigns a new full name, the `Set` procedure attempts to break it into two constituent names.</span></span> <span data-ttu-id="46fc5-141">Bir boşluk bulamazsa, ilk ad olarak tümünü depolar.</span><span class="sxs-lookup"><span data-stu-id="46fc5-141">If it does not find a space, it stores it all as the first name.</span></span>  
  
 [!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]  
  
 <span data-ttu-id="46fc5-142">Aşağıdaki örnek, öğesinin özellik yordamlarına yapılan tipik çağrıları gösterir `fullName` .</span><span class="sxs-lookup"><span data-stu-id="46fc5-142">The following example shows typical calls to the property procedures of `fullName`.</span></span> <span data-ttu-id="46fc5-143">İlk çağrı, özellik değerini ayarlar ve ikinci çağrı onu alır.</span><span class="sxs-lookup"><span data-stu-id="46fc5-143">The first call sets the property value and the second call retrieves it.</span></span>  
  
 [!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="46fc5-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46fc5-144">See also</span></span>

- [<span data-ttu-id="46fc5-145">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="46fc5-145">Procedures</span></span>](./index.md)
- [<span data-ttu-id="46fc5-146">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="46fc5-146">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="46fc5-147">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="46fc5-147">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="46fc5-148">Visual Basic'de Özellikler ve Değişkenler Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="46fc5-148">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="46fc5-149">Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme</span><span class="sxs-lookup"><span data-stu-id="46fc5-149">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="46fc5-150">Nasıl yapılır: Bir Özellik Yordamı Çağırma</span><span class="sxs-lookup"><span data-stu-id="46fc5-150">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="46fc5-151">Nasıl yapılır: Visual Basic'de Varsayılan Bir Özelliği Bildirme ve Çağırma</span><span class="sxs-lookup"><span data-stu-id="46fc5-151">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="46fc5-152">Nasıl yapılır: Bir Özelliğe Değer Ekleme</span><span class="sxs-lookup"><span data-stu-id="46fc5-152">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="46fc5-153">Nasıl yapılır: Bir Özellikten Değer Alma</span><span class="sxs-lookup"><span data-stu-id="46fc5-153">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
