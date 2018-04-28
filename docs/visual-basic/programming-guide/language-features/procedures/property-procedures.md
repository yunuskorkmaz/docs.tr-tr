---
title: Özellik Yordamları (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Set statement [Visual Basic], Property procedures
- Visual Basic code, procedures
- return values [Visual Basic], Property procedures
- syntax [Visual Basic], Property procedures
- procedures [Visual Basic], property
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], custom
- property procedures
- Get statement [Visual Basic], property procedures
ms.assetid: 46a98379-e1a2-45dd-a48c-b51213f5ab07
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0d9df6f381c89263aa16315fb06a2b3b0d645bbf
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="property-procedures-visual-basic"></a><span data-ttu-id="5aa5b-102">Özellik Yordamları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5aa5b-102">Property Procedures (Visual Basic)</span></span>
<span data-ttu-id="5aa5b-103">Bir özellik yordamı bir özel özellik modülü, sınıf veya yapı işlemek Visual Basic deyimleri dizisidir.</span><span class="sxs-lookup"><span data-stu-id="5aa5b-103">A property procedure is a series of Visual Basic statements that manipulate a custom property on a module, class, or structure.</span></span> <span data-ttu-id="5aa5b-104">Özellik yordamları olan olarak da bilinen *özellik erişimcisi*.</span><span class="sxs-lookup"><span data-stu-id="5aa5b-104">Property procedures are also known as *property accessors*.</span></span>  
  
 <span data-ttu-id="5aa5b-105">Visual Basic için aşağıdaki özellik yordamları sağlar:</span><span class="sxs-lookup"><span data-stu-id="5aa5b-105">Visual Basic provides for the following property procedures:</span></span>  
  
-   <span data-ttu-id="5aa5b-106">A `Get` yordamı bir özelliğin değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="5aa5b-106">A `Get` procedure returns the value of a property.</span></span> <span data-ttu-id="5aa5b-107">Bir ifade özelliğinde eriştiğinizde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="5aa5b-107">It is called when you access the property in an expression.</span></span>  
  
-   <span data-ttu-id="5aa5b-108">A `Set` yordamı bir nesne başvurusu dahil olmak üzere bir değer için bir özellik ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5aa5b-108">A `Set` procedure sets a property to a value, including an object reference.</span></span> <span data-ttu-id="5aa5b-109">Özelliği için bir değer atadığınızda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="5aa5b-109">It is called when you assign a value to the property.</span></span>  
  
 <span data-ttu-id="5aa5b-110">Özellik yordamları kullanarak çiftler halinde genellikle tanımlamak `Get` ve `Set` deyimleri, ancak tanımlayabilirsiniz tek başına ya da yordamı özelliği salt okunur ise ([Get deyimi](../../../../visual-basic/language-reference/statements/get-statement.md)) veya salt yazılır ([ayarlayın Deyimi](../../../../visual-basic/language-reference/statements/set-statement.md)).</span><span class="sxs-lookup"><span data-stu-id="5aa5b-110">You usually define property procedures in pairs, using the `Get` and `Set` statements, but you can define either procedure alone if the property is read-only ([Get Statement](../../../../visual-basic/language-reference/statements/get-statement.md)) or write-only ([Set Statement](../../../../visual-basic/language-reference/statements/set-statement.md)).</span></span>  
  
 <span data-ttu-id="5aa5b-111">Atlayabilirsiniz `Get` ve `Set` otomatik uygulanan özelliğini kullanırken yordamı.</span><span class="sxs-lookup"><span data-stu-id="5aa5b-111">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="5aa5b-112">Daha fazla bilgi için bkz: [Auto-Implemented özellikleri](./auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="5aa5b-112">For more information, see [Auto-Implemented Properties](./auto-implemented-properties.md).</span></span>  
  
 <span data-ttu-id="5aa5b-113">Özellikler, sınıflar, yapılar ve modülleri tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5aa5b-113">You can define properties in classes, structures, and modules.</span></span> <span data-ttu-id="5aa5b-114">Özellikleri `Public` varsayılan olarak, yani çağırabilirsiniz bunları yerden uygulamanızda özelliğin kapsayıcı erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5aa5b-114">Properties are `Public` by default, which means you can call them from anywhere in your application that can access the property's container.</span></span>  
  
 <span data-ttu-id="5aa5b-115">Özellikler ve değişkenler karşılaştırması için bkz: [özellikleri arasındaki farklar ve Visual Basic değişken](./differences-between-properties-and-variables.md).</span><span class="sxs-lookup"><span data-stu-id="5aa5b-115">For a comparison of properties and variables, see [Differences Between Properties and Variables in Visual Basic](./differences-between-properties-and-variables.md).</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="5aa5b-116">Bildirim Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5aa5b-116">Declaration Syntax</span></span>  
 <span data-ttu-id="5aa5b-117">Bir özellik içine alınmış kod bloğunu tarafından tanımlanan [Property deyimi](../../../../visual-basic/language-reference/statements/property-statement.md) ve `End Property` deyimi.</span><span class="sxs-lookup"><span data-stu-id="5aa5b-117">A property itself is defined by a block of code enclosed within the [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="5aa5b-118">Bu bloğunun içine bildirimi deyimi içinde çevrelenmiş bir iç bloğu olarak her bir özellik yordam görünür (`Get` veya `Set`) ve eşleşen `End` bildirimi.</span><span class="sxs-lookup"><span data-stu-id="5aa5b-118">Inside this block, each property procedure appears as an internal block enclosed within a declaration statement (`Get` or `Set`) and the matching `End` declaration.</span></span>  
  
 <span data-ttu-id="5aa5b-119">Bir özellik ve onun yordamları bildirme söz dizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="5aa5b-119">The syntax for declaring a property and its procedures is as follows:</span></span>  
  
```  
[Default] [Modifiers] Property PropertyName[(ParameterList)] [As DataType]  
    [AccessLevel] Get  
        ' Statements of the Get procedure.  
        ' The following statement returns an expression as the property's value.  
        Return Expression  
    End Get  
    [AccessLevel] Set[(ByVal NewValue As DataType)]  
        ' Statements of the Set procedure.  
        ' The following statement assigns newvalue as the property's value.  
        LValue = NewValue  
    End Set  
End Property  
- or -  
[Default] [Modifiers] Property PropertyName [(ParameterList)] [As DataType]  
```  
  
 <span data-ttu-id="5aa5b-120">`Modifiers` Erişim düzeyini ve aşırı yüklemesi, geçersiz kılma, paylaşımı ve Gölgeleme, ilgili bilgileri yanı sıra özelliği salt okunur veya sadece yazılabilir olup belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5aa5b-120">The `Modifiers` can specify access level and information regarding overloading, overriding, sharing, and shadowing, as well as whether the property is read-only or write-only.</span></span> <span data-ttu-id="5aa5b-121">`AccessLevel` Üzerinde `Get` veya `Set` yordamı özelliği için belirtilen erişim düzeyini daha kısıtlayıcı olan herhangi bir düzeye olabilir.</span><span class="sxs-lookup"><span data-stu-id="5aa5b-121">The `AccessLevel` on the `Get` or `Set` procedure can be any level that is more restrictive than the access level specified for the property itself.</span></span> <span data-ttu-id="5aa5b-122">Daha fazla bilgi için bkz: [Property deyimi](../../../../visual-basic/language-reference/statements/property-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5aa5b-122">For more information, see [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="5aa5b-123">Veri Türü</span><span class="sxs-lookup"><span data-stu-id="5aa5b-123">Data Type</span></span>  
 <span data-ttu-id="5aa5b-124">Bir özelliğin veri türüne ve asıl erişim düzeyi tanımlanır `Property` özelliği yordamlardaki deyimi.</span><span class="sxs-lookup"><span data-stu-id="5aa5b-124">A property's data type and principal access level are defined in the `Property` statement, not in the property procedures.</span></span> <span data-ttu-id="5aa5b-125">Bir özelliği yalnızca bir veri türüne sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="5aa5b-125">A property can have only one data type.</span></span> <span data-ttu-id="5aa5b-126">Örneğin, depolamak için bir özellik tanımlanamaz bir `Decimal` değer ancak almak bir `Double` değeri.</span><span class="sxs-lookup"><span data-stu-id="5aa5b-126">For example, you cannot define a property to store a `Decimal` value but retrieve a `Double` value.</span></span>  
  
### <a name="access-level"></a><span data-ttu-id="5aa5b-127">Erişim düzeyi</span><span class="sxs-lookup"><span data-stu-id="5aa5b-127">Access Level</span></span>  
 <span data-ttu-id="5aa5b-128">Ancak, bir özellik için bir asıl erişim düzeylerini tanımlayın ve daha fazla özellik yordamları birinde erişim düzeyi kısıtlayın.</span><span class="sxs-lookup"><span data-stu-id="5aa5b-128">However, you can define a principal access level for a property and further restrict the access level in one of its property procedures.</span></span> <span data-ttu-id="5aa5b-129">Örneğin, tanımlayabilirsiniz bir `Public` özelliği ve ardından tanımlayan bir `Private Set` yordamı.</span><span class="sxs-lookup"><span data-stu-id="5aa5b-129">For example, you can define a `Public` property and then define a `Private Set` procedure.</span></span> <span data-ttu-id="5aa5b-130">`Get` Yordamı kalır `Public`.</span><span class="sxs-lookup"><span data-stu-id="5aa5b-130">The `Get` procedure remains `Public`.</span></span> <span data-ttu-id="5aa5b-131">Bir özelliğin yordamlar yalnızca birinde erişim düzeyini değiştirebilirsiniz ve yalnızca bunu asıl erişim düzeyini daha kısıtlayıcı bir duruma getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5aa5b-131">You can change the access level in only one of a property's procedures, and you can only make it more restrictive than the principal access level.</span></span> <span data-ttu-id="5aa5b-132">Daha fazla bilgi için bkz: [nasıl yapılır: bir özelliği karışık erişim düzeyleriyle bildirme](./how-to-declare-a-property-with-mixed-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="5aa5b-132">For more information, see [How to: Declare a Property with Mixed Access Levels](./how-to-declare-a-property-with-mixed-access-levels.md).</span></span>  
  
## <a name="parameter-declaration"></a><span data-ttu-id="5aa5b-133">Parametre bildirimi</span><span class="sxs-lookup"><span data-stu-id="5aa5b-133">Parameter Declaration</span></span>  
 <span data-ttu-id="5aa5b-134">Her bir parametreyi yapmak için aynı şekilde bildirme [alt yordamlar](./sub-procedures.md)geçirme mekanizması olmalı, dışında `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="5aa5b-134">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md), except that the passing mechanism must be `ByVal`.</span></span>  
  
 <span data-ttu-id="5aa5b-135">Parametre listesindeki her parametre için söz dizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="5aa5b-135">The syntax for each parameter in the parameter list is as follows:</span></span>  
  
 `[Optional] ByVal [ParamArray] parametername As datatype`  
  
 <span data-ttu-id="5aa5b-136">Parametre isteğe bağlı ise, varsayılan değer bildiriminden bir parçası olarak sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5aa5b-136">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="5aa5b-137">Varsayılan bir değer belirtmek için sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="5aa5b-137">The syntax for specifying a default value is as follows:</span></span>  
  
 `Optional ByVal parametername As datatype = defaultvalue`  
  
## <a name="property-value"></a><span data-ttu-id="5aa5b-138">Özellik Değeri</span><span class="sxs-lookup"><span data-stu-id="5aa5b-138">Property Value</span></span>  
 <span data-ttu-id="5aa5b-139">İçinde bir `Get` yordamı, dönüş değeri arama ifade özelliğinin değeri olarak sağlanan.</span><span class="sxs-lookup"><span data-stu-id="5aa5b-139">In a `Get` procedure, the return value is supplied to the calling expression as the value of the property.</span></span>  
  
 <span data-ttu-id="5aa5b-140">İçinde bir `Set` yordamı, yeni özellik değeri için parametresinin geçirilir `Set` deyimi.</span><span class="sxs-lookup"><span data-stu-id="5aa5b-140">In a `Set` procedure, the new property value is passed to the parameter of the `Set` statement.</span></span> <span data-ttu-id="5aa5b-141">Bir parametre açıkça bildirirseniz özelliği olarak aynı veri türüne sahip bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5aa5b-141">If you explicitly declare a parameter, you must declare it with the same data type as the property.</span></span> <span data-ttu-id="5aa5b-142">Bir parametre bildirmeyin, derleyici örtük parametre kullanıyorsa `Value` özelliğine atanacak yeni değer temsil etmek için.</span><span class="sxs-lookup"><span data-stu-id="5aa5b-142">If you do not declare a parameter, the compiler uses the implicit parameter `Value` to represent the new value to be assigned to the property.</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="5aa5b-143">Arama sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5aa5b-143">Calling Syntax</span></span>  
 <span data-ttu-id="5aa5b-144">Bir özellik yordamı örtük olarak özellik referansı yaparak çağırır.</span><span class="sxs-lookup"><span data-stu-id="5aa5b-144">You invoke a property procedure implicitly by making reference to the property.</span></span> <span data-ttu-id="5aa5b-145">Bağımsız değişken listesi parantez içine alın ve isteğe bağlı olmayan tüm bağımsız değişkenler için değer sağlamalısınız dışında bir değişken adını kullanacağınız aynı şekilde özelliğinin adını kullanın.</span><span class="sxs-lookup"><span data-stu-id="5aa5b-145">You use the name of the property the same way you would use the name of a variable, except that you must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="5aa5b-146">Bağımsız değişkenler sağlandıysa, isteğe bağlı olarak parantez atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5aa5b-146">If no arguments are supplied, you can optionally omit the parentheses.</span></span>  
  
 <span data-ttu-id="5aa5b-147">Örtük bir çağrı sözdizimi bir `Set` yordam aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="5aa5b-147">The syntax for an implicit call to a `Set` procedure is as follows:</span></span>  
  
 `propertyname[(argumentlist)] = expression`  
  
 <span data-ttu-id="5aa5b-148">Örtük bir çağrı sözdizimi bir `Get` yordam aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="5aa5b-148">The syntax for an implicit call to a `Get` procedure is as follows:</span></span>  
  
 `lvalue = propertyname[(argumentlist)]`  
  
 `Do While (propertyname[(argumentlist)] > expression)`  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="5aa5b-149">Bildirim ve çağrı çizimi</span><span class="sxs-lookup"><span data-stu-id="5aa5b-149">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="5aa5b-150">Aşağıdaki özellikler, iki bağlı adları, ad ve Soyadı bir tam ad depolar.</span><span class="sxs-lookup"><span data-stu-id="5aa5b-150">The following property stores a full name as two constituent names, the first name and the last name.</span></span> <span data-ttu-id="5aa5b-151">Ne zaman çağıran kodu okur `fullName`, `Get` yordamı iki bağlı adları birleştirir ve tam adını döndürür.</span><span class="sxs-lookup"><span data-stu-id="5aa5b-151">When the calling code reads `fullName`, the `Get` procedure combines the two constituent names and returns the full name.</span></span> <span data-ttu-id="5aa5b-152">Çağrıyı yapan kod yeni bir tam ad atarken `Set` yordamı iki bağlı adlarına bölün dener.</span><span class="sxs-lookup"><span data-stu-id="5aa5b-152">When the calling code assigns a new full name, the `Set` procedure attempts to break it into two constituent names.</span></span> <span data-ttu-id="5aa5b-153">Bir alan bulamazsa, tüm ad depolar.</span><span class="sxs-lookup"><span data-stu-id="5aa5b-153">If it does not find a space, it stores it all as the first name.</span></span>  
  
 [!code-vb[VbVbcnProcedures#8](./codesnippet/VisualBasic/property-procedures_1.vb)]  
  
 <span data-ttu-id="5aa5b-154">Aşağıdaki örnek özellik yordamları tipik çağrı gösterilir `fullName`.</span><span class="sxs-lookup"><span data-stu-id="5aa5b-154">The following example shows typical calls to the property procedures of `fullName`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#9](./codesnippet/VisualBasic/property-procedures_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5aa5b-155">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5aa5b-155">See Also</span></span>  
 [<span data-ttu-id="5aa5b-156">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="5aa5b-156">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="5aa5b-157">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="5aa5b-157">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="5aa5b-158">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="5aa5b-158">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="5aa5b-159">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="5aa5b-159">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="5aa5b-160">Visual Basic'de özellikler ve değişkenler arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="5aa5b-160">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)  
 [<span data-ttu-id="5aa5b-161">Nasıl yapılır: Özellik Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5aa5b-161">How to: Create a Property</span></span>](./how-to-create-a-property.md)  
 [<span data-ttu-id="5aa5b-162">Nasıl yapılır: Bir Özellik Yordamı Çağırma</span><span class="sxs-lookup"><span data-stu-id="5aa5b-162">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)  
 [<span data-ttu-id="5aa5b-163">Nasıl yapılır: bildirme ve Visual Basic'te varsayılan özelliğini çağırın</span><span class="sxs-lookup"><span data-stu-id="5aa5b-163">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="5aa5b-164">Nasıl yapılır: Bir Özelliğe Değer Ekleme</span><span class="sxs-lookup"><span data-stu-id="5aa5b-164">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)  
 [<span data-ttu-id="5aa5b-165">Nasıl yapılır: Bir Özellikten Değer Alma</span><span class="sxs-lookup"><span data-stu-id="5aa5b-165">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
