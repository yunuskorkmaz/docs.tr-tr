---
title: Özellik Yordamları (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 47e93ee17f160ce5cd701fd0a12ec16b3997ce9b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58828358"
---
# <a name="property-procedures-visual-basic"></a><span data-ttu-id="f53fd-102">Özellik Yordamları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f53fd-102">Property Procedures (Visual Basic)</span></span>
<span data-ttu-id="f53fd-103">Bir özellik yordamı bir özel özellik bir modül, sınıf veya yapı işleyen Visual Basic deyimleri bir dizisidir.</span><span class="sxs-lookup"><span data-stu-id="f53fd-103">A property procedure is a series of Visual Basic statements that manipulate a custom property on a module, class, or structure.</span></span> <span data-ttu-id="f53fd-104">Özellik yordamları olan olarak da bilinen *özellik erişimcileri*.</span><span class="sxs-lookup"><span data-stu-id="f53fd-104">Property procedures are also known as *property accessors*.</span></span>  
  
 <span data-ttu-id="f53fd-105">Visual Basic için aşağıdaki özellik yordamları sağlar:</span><span class="sxs-lookup"><span data-stu-id="f53fd-105">Visual Basic provides for the following property procedures:</span></span>  
  
-   <span data-ttu-id="f53fd-106">A `Get` yordamı bir özelliğinin değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="f53fd-106">A `Get` procedure returns the value of a property.</span></span> <span data-ttu-id="f53fd-107">Bir ifade özelliğinde eriştiğinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f53fd-107">It is called when you access the property in an expression.</span></span>  
  
-   <span data-ttu-id="f53fd-108">A `Set` yordamı bir özellik içeren bir nesne başvurusu bir değere ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f53fd-108">A `Set` procedure sets a property to a value, including an object reference.</span></span> <span data-ttu-id="f53fd-109">Özellik için bir değer atadığınızda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f53fd-109">It is called when you assign a value to the property.</span></span>  
  
 <span data-ttu-id="f53fd-110">Özellik yordamları kullanarak çiftlerinde genellikle tanımlamak `Get` ve `Set` deyimleri, ancak tanımlayabilirsiniz tek başına ya da yordam özellik salt okunur ise ([alma deyimi](../../../../visual-basic/language-reference/statements/get-statement.md)) veya salt yazılır ([ayarlayın Deyimi](../../../../visual-basic/language-reference/statements/set-statement.md)).</span><span class="sxs-lookup"><span data-stu-id="f53fd-110">You usually define property procedures in pairs, using the `Get` and `Set` statements, but you can define either procedure alone if the property is read-only ([Get Statement](../../../../visual-basic/language-reference/statements/get-statement.md)) or write-only ([Set Statement](../../../../visual-basic/language-reference/statements/set-statement.md)).</span></span>  
  
 <span data-ttu-id="f53fd-111">Atlayabilirsiniz `Get` ve `Set` otomatik uygulanan bir özellik kullanıldığında yordamı.</span><span class="sxs-lookup"><span data-stu-id="f53fd-111">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="f53fd-112">Daha fazla bilgi için [Implemented Properties](./auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="f53fd-112">For more information, see [Auto-Implemented Properties](./auto-implemented-properties.md).</span></span>  
  
 <span data-ttu-id="f53fd-113">Özellikler, sınıflar, yapılar ve modülleri tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f53fd-113">You can define properties in classes, structures, and modules.</span></span> <span data-ttu-id="f53fd-114">Özellikleri `Public` varsayılan olarak, yani çağırabilirsiniz bunları yerden uygulamanızdaki özelliğin kapsayıcı erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f53fd-114">Properties are `Public` by default, which means you can call them from anywhere in your application that can access the property's container.</span></span>  
  
 <span data-ttu-id="f53fd-115">Özellikler ve değişkenlerin bir karşılaştırması için bkz. [arasındaki farklar özelliklerini ve Visual Basic'te değişkenler](./differences-between-properties-and-variables.md).</span><span class="sxs-lookup"><span data-stu-id="f53fd-115">For a comparison of properties and variables, see [Differences Between Properties and Variables in Visual Basic](./differences-between-properties-and-variables.md).</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="f53fd-116">Bildirim Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f53fd-116">Declaration Syntax</span></span>  
 <span data-ttu-id="f53fd-117">İçine alınmış bir kod bloğunu tarafından tanımlanan bir özellik [Property deyimi](../../../../visual-basic/language-reference/statements/property-statement.md) ve `End Property` deyimi.</span><span class="sxs-lookup"><span data-stu-id="f53fd-117">A property itself is defined by a block of code enclosed within the [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="f53fd-118">Bir bildirim deyiminin alınmış bir dahili bloğu olarak her bir özellik yordamı bu blok içinde görünür (`Get` veya `Set`) ile eşleşen `End` bildirimi.</span><span class="sxs-lookup"><span data-stu-id="f53fd-118">Inside this block, each property procedure appears as an internal block enclosed within a declaration statement (`Get` or `Set`) and the matching `End` declaration.</span></span>  
  
 <span data-ttu-id="f53fd-119">Bir özellik ve işlemleri bildirmek için sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="f53fd-119">The syntax for declaring a property and its procedures is as follows:</span></span>  
  
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
  
 <span data-ttu-id="f53fd-120">`Modifiers` Erişim düzeyi ve aşırı yüklemesi, geçersiz kılma, paylaşımı ve Gölgeleme, ilgili bilgileri yanı sıra özelliğin salt okunur veya sadece yazılabilir olup belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f53fd-120">The `Modifiers` can specify access level and information regarding overloading, overriding, sharing, and shadowing, as well as whether the property is read-only or write-only.</span></span> <span data-ttu-id="f53fd-121">`AccessLevel` Üzerinde `Get` veya `Set` yordamı özelliği için belirtilen erişim düzeyi daha kısıtlayıcı olan herhangi bir düzeyinde olabilir.</span><span class="sxs-lookup"><span data-stu-id="f53fd-121">The `AccessLevel` on the `Get` or `Set` procedure can be any level that is more restrictive than the access level specified for the property itself.</span></span> <span data-ttu-id="f53fd-122">Daha fazla bilgi için [Property deyimi](../../../../visual-basic/language-reference/statements/property-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f53fd-122">For more information, see [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="f53fd-123">Veri Türü</span><span class="sxs-lookup"><span data-stu-id="f53fd-123">Data Type</span></span>  
 <span data-ttu-id="f53fd-124">Bir özelliğin veri türü ve asıl erişim düzeyi tanımlanan `Property` deyimi, özellik yordamları içinde değil.</span><span class="sxs-lookup"><span data-stu-id="f53fd-124">A property's data type and principal access level are defined in the `Property` statement, not in the property procedures.</span></span> <span data-ttu-id="f53fd-125">Bir özellik, yalnızca bir veri türü olabilir.</span><span class="sxs-lookup"><span data-stu-id="f53fd-125">A property can have only one data type.</span></span> <span data-ttu-id="f53fd-126">Örneğin, depolamak için bir özellik tanımlanamaz bir `Decimal` değer ancak almak bir `Double` değeri.</span><span class="sxs-lookup"><span data-stu-id="f53fd-126">For example, you cannot define a property to store a `Decimal` value but retrieve a `Double` value.</span></span>  
  
### <a name="access-level"></a><span data-ttu-id="f53fd-127">Erişim düzeyi</span><span class="sxs-lookup"><span data-stu-id="f53fd-127">Access Level</span></span>  
 <span data-ttu-id="f53fd-128">Ancak, bir özellik için bir asıl erişim düzeylerini tanımlayın ve kendi özellik yordamları biriyle erişim düzeyi kısıtlamanız.</span><span class="sxs-lookup"><span data-stu-id="f53fd-128">However, you can define a principal access level for a property and further restrict the access level in one of its property procedures.</span></span> <span data-ttu-id="f53fd-129">Örneğin, tanımlayabileceğiniz bir `Public` özelliği ve tanımlayabilirsiniz bir `Private Set` yordamı.</span><span class="sxs-lookup"><span data-stu-id="f53fd-129">For example, you can define a `Public` property and then define a `Private Set` procedure.</span></span> <span data-ttu-id="f53fd-130">`Get` Yordamı kalır `Public`.</span><span class="sxs-lookup"><span data-stu-id="f53fd-130">The `Get` procedure remains `Public`.</span></span> <span data-ttu-id="f53fd-131">Bir özelliğin yordamlar yalnızca birinde erişim düzeyini değiştirebilir ve yalnızca bunu asıl erişim düzeyi daha kısıtlayıcı bir duruma getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f53fd-131">You can change the access level in only one of a property's procedures, and you can only make it more restrictive than the principal access level.</span></span> <span data-ttu-id="f53fd-132">Daha fazla bilgi için [nasıl yapılır: Bir özelliği karışık erişim düzeyleriyle bildirme](./how-to-declare-a-property-with-mixed-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="f53fd-132">For more information, see [How to: Declare a Property with Mixed Access Levels](./how-to-declare-a-property-with-mixed-access-levels.md).</span></span>  
  
## <a name="parameter-declaration"></a><span data-ttu-id="f53fd-133">Parametre bildirimi</span><span class="sxs-lookup"><span data-stu-id="f53fd-133">Parameter Declaration</span></span>  
 <span data-ttu-id="f53fd-134">Her parametre için yaptığınız gibi bildirdiğiniz [alt yordamlar](./sub-procedures.md)geçirme mekanizması olmalı, dışında `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="f53fd-134">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md), except that the passing mechanism must be `ByVal`.</span></span>  
  
 <span data-ttu-id="f53fd-135">Parametre listesindeki her parametre için sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="f53fd-135">The syntax for each parameter in the parameter list is as follows:</span></span>  
  
 `[Optional] ByVal [ParamArray] parametername As datatype`  
  
 <span data-ttu-id="f53fd-136">Parametre isteğe bağlıysa, varsayılan değer bildiriminin bir parçası olarak da belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f53fd-136">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="f53fd-137">Varsayılan bir değer belirtmek için sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="f53fd-137">The syntax for specifying a default value is as follows:</span></span>  
  
 `Optional ByVal parametername As datatype = defaultvalue`  
  
## <a name="property-value"></a><span data-ttu-id="f53fd-138">Özellik Değeri</span><span class="sxs-lookup"><span data-stu-id="f53fd-138">Property Value</span></span>  
 <span data-ttu-id="f53fd-139">İçinde bir `Get` yordamı, dönüş değeri, çağıran ifadeye özelliğinin değeri olarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="f53fd-139">In a `Get` procedure, the return value is supplied to the calling expression as the value of the property.</span></span>  
  
 <span data-ttu-id="f53fd-140">İçinde bir `Set` yordamı, yeni özellik değeri için parametresi geçirilir `Set` deyimi.</span><span class="sxs-lookup"><span data-stu-id="f53fd-140">In a `Set` procedure, the new property value is passed to the parameter of the `Set` statement.</span></span> <span data-ttu-id="f53fd-141">Bir parametre açıkça bildirirseniz özelliği olarak aynı veri türünde bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f53fd-141">If you explicitly declare a parameter, you must declare it with the same data type as the property.</span></span> <span data-ttu-id="f53fd-142">Bir parametre bildirmeyin, derleyici örtük parametresini kullanır. `Value` özelliğe atanacak yeni değeri gösterecek.</span><span class="sxs-lookup"><span data-stu-id="f53fd-142">If you do not declare a parameter, the compiler uses the implicit parameter `Value` to represent the new value to be assigned to the property.</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="f53fd-143">Arama söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f53fd-143">Calling Syntax</span></span>  
 <span data-ttu-id="f53fd-144">Bir özellik yordamı örtük olarak özelliğine başvuru yaparak çağırın.</span><span class="sxs-lookup"><span data-stu-id="f53fd-144">You invoke a property procedure implicitly by making reference to the property.</span></span> <span data-ttu-id="f53fd-145">İsteğe bağlı olmayan tüm bağımsız değişkenler için değer sağlamanız gereken dışında aynı şekilde, bir değişken adını kullanırsınız özelliğin adını kullanın ve bağımsız değişken listesi parantez içine almalısınız.</span><span class="sxs-lookup"><span data-stu-id="f53fd-145">You use the name of the property the same way you would use the name of a variable, except that you must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="f53fd-146">Hiçbir bağımsız değişken sağlanmadıysa, parantezler isteğe bağlı olarak atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f53fd-146">If no arguments are supplied, you can optionally omit the parentheses.</span></span>  
  
 <span data-ttu-id="f53fd-147">Örtük çağrıyla sözdizimi bir `Set` yordam şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="f53fd-147">The syntax for an implicit call to a `Set` procedure is as follows:</span></span>  
  
 `propertyname[(argumentlist)] = expression`  
  
 <span data-ttu-id="f53fd-148">Örtük çağrıyla sözdizimi bir `Get` yordam şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="f53fd-148">The syntax for an implicit call to a `Get` procedure is as follows:</span></span>  
  
 `lvalue = propertyname[(argumentlist)]`  
  
 `Do While (propertyname[(argumentlist)] > expression)`  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="f53fd-149">Bildirim ve çağrı gösterimi</span><span class="sxs-lookup"><span data-stu-id="f53fd-149">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="f53fd-150">Aşağıdaki özelliği tam adı, iki bağlı ad, ad ve Soyadı depolar.</span><span class="sxs-lookup"><span data-stu-id="f53fd-150">The following property stores a full name as two constituent names, the first name and the last name.</span></span> <span data-ttu-id="f53fd-151">Çağıran kod zaman okur `fullName`, `Get` yordam iki bağlı adları birleştirir ve tam adını döndürür.</span><span class="sxs-lookup"><span data-stu-id="f53fd-151">When the calling code reads `fullName`, the `Get` procedure combines the two constituent names and returns the full name.</span></span> <span data-ttu-id="f53fd-152">Çağıran kod yeni bir tam ad atarken `Set` yordamı iki bağlı adlarına sonu dener.</span><span class="sxs-lookup"><span data-stu-id="f53fd-152">When the calling code assigns a new full name, the `Set` procedure attempts to break it into two constituent names.</span></span> <span data-ttu-id="f53fd-153">Bir alan bulamazsa, tüm ad depolar.</span><span class="sxs-lookup"><span data-stu-id="f53fd-153">If it does not find a space, it stores it all as the first name.</span></span>  
  
 [!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]  
  
 <span data-ttu-id="f53fd-154">Aşağıdaki örnek özellik yordamları tipik çağrıları gösterir `fullName`.</span><span class="sxs-lookup"><span data-stu-id="f53fd-154">The following example shows typical calls to the property procedures of `fullName`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="f53fd-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f53fd-155">See also</span></span>

- [<span data-ttu-id="f53fd-156">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="f53fd-156">Procedures</span></span>](./index.md)
- [<span data-ttu-id="f53fd-157">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="f53fd-157">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="f53fd-158">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="f53fd-158">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="f53fd-159">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="f53fd-159">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="f53fd-160">Visual Basic'de özellikler ile değişkenler arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="f53fd-160">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="f53fd-161">Nasıl yapılır: Özellik oluşturma</span><span class="sxs-lookup"><span data-stu-id="f53fd-161">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="f53fd-162">Nasıl yapılır: Bir özellik yordamı çağırma</span><span class="sxs-lookup"><span data-stu-id="f53fd-162">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="f53fd-163">Nasıl yapılır: Bildirme ve Visual Basic'te bir varsayılan özelliğini çağırın</span><span class="sxs-lookup"><span data-stu-id="f53fd-163">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="f53fd-164">Nasıl yapılır: Bir özelliğe değer ekleme</span><span class="sxs-lookup"><span data-stu-id="f53fd-164">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="f53fd-165">Nasıl yapılır: Bir özellikten değer alma</span><span class="sxs-lookup"><span data-stu-id="f53fd-165">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
