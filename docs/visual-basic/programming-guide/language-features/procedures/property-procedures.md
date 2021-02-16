---
description: 'Daha fazla bilgi edinin: özellik yordamları (Visual Basic)'
title: Özellik Yordamları
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
ms.openlocfilehash: 55588278cdb8423a4f13a4e7ecc02f7ea692a618
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466594"
---
# <a name="property-procedures-visual-basic"></a><span data-ttu-id="0e679-103">Özellik Yordamları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0e679-103">Property Procedures (Visual Basic)</span></span>

<span data-ttu-id="0e679-104">Özellik yordamı bir modül, sınıf veya yapıda özel bir özelliği düzenleyen Visual Basic deyimlerinin bir dizisidir.</span><span class="sxs-lookup"><span data-stu-id="0e679-104">A property procedure is a series of Visual Basic statements that manipulate a custom property on a module, class, or structure.</span></span> <span data-ttu-id="0e679-105">Özellik yordamları, *özellik erişimcileri* olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="0e679-105">Property procedures are also known as *property accessors*.</span></span>

<span data-ttu-id="0e679-106">Visual Basic aşağıdaki özellik yordamları için sağlar:</span><span class="sxs-lookup"><span data-stu-id="0e679-106">Visual Basic provides for the following property procedures:</span></span>

- <span data-ttu-id="0e679-107">Bir `Get` yordam bir özelliğin değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="0e679-107">A `Get` procedure returns the value of a property.</span></span> <span data-ttu-id="0e679-108">Bir ifadede özelliğe eriştiğinizde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="0e679-108">It is called when you access the property in an expression.</span></span>
- <span data-ttu-id="0e679-109">Bir `Set` yordam, bir özelliği bir nesne başvurusu dahil olmak üzere bir değere ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0e679-109">A `Set` procedure sets a property to a value, including an object reference.</span></span> <span data-ttu-id="0e679-110">Özelliğe bir değer atadığınızda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="0e679-110">It is called when you assign a value to the property.</span></span>

<span data-ttu-id="0e679-111">Genellikle özellik yordamlarını ve deyimlerini kullanarak çiftler halinde tanımlarsınız `Get` `Set` , ancak özellik salt okunurdur ([Get deyimi](../../../language-reference/statements/get-statement.md)) ya da salt yazılır ([küme deyimi](../../../language-reference/statements/set-statement.md)) ise tek başına yordamı tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e679-111">You usually define property procedures in pairs, using the `Get` and `Set` statements, but you can define either procedure alone if the property is read-only ([Get Statement](../../../language-reference/statements/get-statement.md)) or write-only ([Set Statement](../../../language-reference/statements/set-statement.md)).</span></span>

<span data-ttu-id="0e679-112">`Get` `Set` Otomatik uygulanan bir özellik kullanırken ve yordamını atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e679-112">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="0e679-113">Daha fazla bilgi için bkz. [Otomatik uygulanan özellikler](./auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="0e679-113">For more information, see [Auto-Implemented Properties](./auto-implemented-properties.md).</span></span>

<span data-ttu-id="0e679-114">Sınıflar, yapılar ve modüllerde özellikler tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e679-114">You can define properties in classes, structures, and modules.</span></span> <span data-ttu-id="0e679-115">Özellikler `Public` Varsayılan olarak, uygulamanın, özelliğin kapsayıcısına erişebilen uygulamanızdaki herhangi bir yerden çağırabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="0e679-115">Properties are `Public` by default, which means you can call them from anywhere in your application that can access the property's container.</span></span>

<span data-ttu-id="0e679-116">Özelliklerin ve değişkenlerin karşılaştırması için [Visual Basic Özellikler ve değişkenler arasındaki farklılıklar](differences-between-properties-and-variables.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="0e679-116">For a comparison of properties and variables, see [Differences Between Properties and Variables in Visual Basic](differences-between-properties-and-variables.md).</span></span>

## <a name="declaration-syntax"></a><span data-ttu-id="0e679-117">Bildirim söz dizimi</span><span class="sxs-lookup"><span data-stu-id="0e679-117">Declaration syntax</span></span>

<span data-ttu-id="0e679-118">Özelliğin kendisi, [özellik bildiriminde](../../../language-reference/statements/property-statement.md) ve ifadesiyle alınmış bir kod bloğu tarafından tanımlanır `End Property` .</span><span class="sxs-lookup"><span data-stu-id="0e679-118">A property itself is defined by a block of code enclosed within the [Property Statement](../../../language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="0e679-119">Bu bloğun içinde her özellik yordamı, bir bildirim bildirimi ( `Get` veya `Set` ) ve eşleşen bildirim içinde iç bir blok olarak görünür `End` .</span><span class="sxs-lookup"><span data-stu-id="0e679-119">Inside this block, each property procedure appears as an internal block enclosed within a declaration statement (`Get` or `Set`) and the matching `End` declaration.</span></span>

<span data-ttu-id="0e679-120">Bir özelliği ve yordamlarını bildirmek için sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="0e679-120">The syntax for declaring a property and its procedures is as follows:</span></span>

```vb
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
' - or -
[Default] [Modifiers] Property PropertyName [(ParameterList)] [As DataType]
```

<span data-ttu-id="0e679-121">, `Modifiers` Aşırı yükleme, geçersiz kılma, paylaşma ve gölgeleme ile ilgili erişim düzeyini ve bilgileri, özelliğin salt okunurdur mi yoksa salt yazılır mi olduğunu belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="0e679-121">The `Modifiers` can specify access level and information regarding overloading, overriding, sharing, and shadowing, as well as whether the property is read-only or write-only.</span></span> <span data-ttu-id="0e679-122">`AccessLevel` `Get` Veya `Set` yordamı, özelliğin kendisi için belirtilen erişim düzeyinden daha kısıtlayıcı olan herhangi bir düzey olabilir.</span><span class="sxs-lookup"><span data-stu-id="0e679-122">The `AccessLevel` on the `Get` or `Set` procedure can be any level that is more restrictive than the access level specified for the property itself.</span></span> <span data-ttu-id="0e679-123">Daha fazla bilgi için bkz. [özellik açıklaması](../../../language-reference/statements/property-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0e679-123">For more information, see [Property Statement](../../../language-reference/statements/property-statement.md).</span></span>

### <a name="data-type"></a><span data-ttu-id="0e679-124">Veri Türü</span><span class="sxs-lookup"><span data-stu-id="0e679-124">Data Type</span></span>

<span data-ttu-id="0e679-125">Özelliğin veri türü ve asıl erişim düzeyi, `Property` özellik yordamlarında değil, bildiriminde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0e679-125">A property's data type and principal access level are defined in the `Property` statement, not in the property procedures.</span></span> <span data-ttu-id="0e679-126">Bir özellik yalnızca bir veri türüne sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="0e679-126">A property can have only one data type.</span></span> <span data-ttu-id="0e679-127">Örneğin, bir değeri depolamak için bir özellik tanımlayamazsınız `Decimal` ancak bir `Double` değer alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e679-127">For example, you cannot define a property to store a `Decimal` value but retrieve a `Double` value.</span></span>

### <a name="access-level"></a><span data-ttu-id="0e679-128">Erişim düzeyi</span><span class="sxs-lookup"><span data-stu-id="0e679-128">Access Level</span></span>

<span data-ttu-id="0e679-129">Ancak, bir özellik için bir asıl erişim düzeyi tanımlayabilir ve özellik yordamlarından birinde erişim düzeyini daha da kısıtlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e679-129">However, you can define a principal access level for a property and further restrict the access level in one of its property procedures.</span></span> <span data-ttu-id="0e679-130">Örneğin, bir `Public` özellik tanımlayabilir ve ardından bir `Private Set` yordam tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e679-130">For example, you can define a `Public` property and then define a `Private Set` procedure.</span></span> <span data-ttu-id="0e679-131">`Get`Yordam kalır `Public` .</span><span class="sxs-lookup"><span data-stu-id="0e679-131">The `Get` procedure remains `Public`.</span></span> <span data-ttu-id="0e679-132">Erişim düzeyini bir özelliğin yordamlarından yalnızca birinde değiştirebilirsiniz ve yalnızca asıl erişim düzeyinden daha kısıtlayıcı hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e679-132">You can change the access level in only one of a property's procedures, and you can only make it more restrictive than the principal access level.</span></span> <span data-ttu-id="0e679-133">Daha fazla bilgi için bkz. [nasıl yapılır: karışık erişim düzeylerine sahip bir özellik bildirme](how-to-declare-a-property-with-mixed-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="0e679-133">For more information, see [How to: Declare a Property with Mixed Access Levels](how-to-declare-a-property-with-mixed-access-levels.md).</span></span>

## <a name="parameter-declaration"></a><span data-ttu-id="0e679-134">Parametre bildirimi</span><span class="sxs-lookup"><span data-stu-id="0e679-134">Parameter declaration</span></span>

<span data-ttu-id="0e679-135">Geçirilen mekanizmanın olması dışında, her parametreyi [alt yordamlar](sub-procedures.md)için yaptığınız gibi bildirirsiniz `ByVal` .</span><span class="sxs-lookup"><span data-stu-id="0e679-135">You declare each parameter the same way you do for [Sub Procedures](sub-procedures.md), except that the passing mechanism must be `ByVal`.</span></span>

<span data-ttu-id="0e679-136">Parametre listesindeki her bir parametre için sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="0e679-136">The syntax for each parameter in the parameter list is as follows:</span></span>

```vb
[Optional] ByVal [ParamArray] parametername As datatype
```

<span data-ttu-id="0e679-137">Parametre isteğe bağlı ise, bildiriminin bir parçası olarak bir varsayılan değer de belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0e679-137">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="0e679-138">Varsayılan bir değer belirtmek için sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="0e679-138">The syntax for specifying a default value is as follows:</span></span>

```vb
Optional ByVal parametername As datatype = defaultvalue
```

## <a name="property-value"></a><span data-ttu-id="0e679-139">Özellik değeri</span><span class="sxs-lookup"><span data-stu-id="0e679-139">Property value</span></span>

<span data-ttu-id="0e679-140">Bir `Get` yordamda, dönüş değeri, özelliğin değeri olarak çağırma ifadesine sağlanır.</span><span class="sxs-lookup"><span data-stu-id="0e679-140">In a `Get` procedure, the return value is supplied to the calling expression as the value of the property.</span></span>

<span data-ttu-id="0e679-141">Bir `Set` yordamda, yeni özellik değeri deyimin parametresine geçirilir `Set` .</span><span class="sxs-lookup"><span data-stu-id="0e679-141">In a `Set` procedure, the new property value is passed to the parameter of the `Set` statement.</span></span> <span data-ttu-id="0e679-142">Açıkça bir parametre bildirirseniz, özelliği ile aynı veri türüyle bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0e679-142">If you explicitly declare a parameter, you must declare it with the same data type as the property.</span></span> <span data-ttu-id="0e679-143">Bir parametre bildirmezsiniz derleyici, `Value` özelliğe atanacak yeni değeri temsil etmek için örtük parametresini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0e679-143">If you do not declare a parameter, the compiler uses the implicit parameter `Value` to represent the new value to be assigned to the property.</span></span>

## <a name="calling-syntax"></a><span data-ttu-id="0e679-144">Çağırma sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0e679-144">Calling syntax</span></span>

<span data-ttu-id="0e679-145">Özelliğe başvuru yaparak bir özellik yordamını örtük olarak çağırılır.</span><span class="sxs-lookup"><span data-stu-id="0e679-145">You invoke a property procedure implicitly by making reference to the property.</span></span> <span data-ttu-id="0e679-146">Özelliği, isteğe bağlı olmayan tüm bağımsız değişkenlerin değerlerini sağlamanız ve bağımsız değişken listesini parantez içine almanız gerekir, ancak, özelliğin adını bir değişkenin adını kullandığınız şekilde kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="0e679-146">You use the name of the property the same way you would use the name of a variable, except that you must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="0e679-147">Herhangi bir bağımsız değişken sağlanmazsa, isteğe bağlı olarak ayraçları atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e679-147">If no arguments are supplied, you can optionally omit the parentheses.</span></span>

<span data-ttu-id="0e679-148">Bir yordama örtük çağrının sözdizimi `Set` aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="0e679-148">The syntax for an implicit call to a `Set` procedure is as follows:</span></span>

```vb
propertyname[(argumentlist)] = expression
```

<span data-ttu-id="0e679-149">Bir yordama örtük çağrının sözdizimi `Get` aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="0e679-149">The syntax for an implicit call to a `Get` procedure is as follows:</span></span>

```vb
lvalue = propertyname[(argumentlist)]
Do While (propertyname[(argumentlist)] > expression)
```

### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="0e679-150">Bildirim ve çağrı gösterimi</span><span class="sxs-lookup"><span data-stu-id="0e679-150">Illustration of declaration and call</span></span>

<span data-ttu-id="0e679-151">Aşağıdaki özellik, tam adı iki anayent adı, ad ve soyadı olarak depolar.</span><span class="sxs-lookup"><span data-stu-id="0e679-151">The following property stores a full name as two constituent names, the first name and the last name.</span></span> <span data-ttu-id="0e679-152">Çağıran kod okuduğunda `fullName` , `Get` yordam iki anayent adı birleştirir ve tam adı döndürür.</span><span class="sxs-lookup"><span data-stu-id="0e679-152">When the calling code reads `fullName`, the `Get` procedure combines the two constituent names and returns the full name.</span></span> <span data-ttu-id="0e679-153">Çağıran kod yeni bir tam ad atarken, `Set` yordam onu iki anayada bölmek için çalışır.</span><span class="sxs-lookup"><span data-stu-id="0e679-153">When the calling code assigns a new full name, the `Set` procedure attempts to break it into two constituent names.</span></span> <span data-ttu-id="0e679-154">Bir boşluk bulamazsa, ilk ad olarak tümünü depolar.</span><span class="sxs-lookup"><span data-stu-id="0e679-154">If it does not find a space, it stores it all as the first name.</span></span>

[!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]

<span data-ttu-id="0e679-155">Aşağıdaki örnek, öğesinin özellik yordamlarına yapılan tipik çağrıları gösterir `fullName` :</span><span class="sxs-lookup"><span data-stu-id="0e679-155">The following example shows typical calls to the property procedures of `fullName`:</span></span>

[!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]

## <a name="see-also"></a><span data-ttu-id="0e679-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e679-156">See also</span></span>

- [<span data-ttu-id="0e679-157">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="0e679-157">Procedures</span></span>](index.md)
- [<span data-ttu-id="0e679-158">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="0e679-158">Function Procedures</span></span>](function-procedures.md)
- [<span data-ttu-id="0e679-159">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="0e679-159">Operator Procedures</span></span>](operator-procedures.md)
- [<span data-ttu-id="0e679-160">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="0e679-160">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="0e679-161">Visual Basic'de Özellikler ve Değişkenler Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="0e679-161">Differences Between Properties and Variables in Visual Basic</span></span>](differences-between-properties-and-variables.md)
- [<span data-ttu-id="0e679-162">Nasıl yapılır: Özellik Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0e679-162">How to: Create a Property</span></span>](how-to-create-a-property.md)
- [<span data-ttu-id="0e679-163">Nasıl yapılır: Bir Özellik Yordamı Çağırma</span><span class="sxs-lookup"><span data-stu-id="0e679-163">How to: Call a Property Procedure</span></span>](how-to-call-a-property-procedure.md)
- [<span data-ttu-id="0e679-164">Nasıl yapılır: Visual Basic'de Varsayılan Bir Özelliği Bildirme ve Çağırma</span><span class="sxs-lookup"><span data-stu-id="0e679-164">How to: Declare and Call a Default Property in Visual Basic</span></span>](how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="0e679-165">Nasıl yapılır: Bir Özelliğe Değer Ekleme</span><span class="sxs-lookup"><span data-stu-id="0e679-165">How to: Put a Value in a Property</span></span>](how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="0e679-166">Nasıl yapılır: Bir Özellikten Değer Alma</span><span class="sxs-lookup"><span data-stu-id="0e679-166">How to: Get a Value from a Property</span></span>](how-to-get-a-value-from-a-property.md)
