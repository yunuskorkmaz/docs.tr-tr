---
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
ms.openlocfilehash: a4b8ac3e27348764f537ee9502ce1fbb165bb3ef
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352571"
---
# <a name="property-procedures-visual-basic"></a><span data-ttu-id="9a264-102">Özellik Yordamları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a264-102">Property Procedures (Visual Basic)</span></span>

<span data-ttu-id="9a264-103">Özellik yordamı bir modül, sınıf veya yapıda özel bir özelliği düzenleyen Visual Basic deyimlerinin bir dizisidir.</span><span class="sxs-lookup"><span data-stu-id="9a264-103">A property procedure is a series of Visual Basic statements that manipulate a custom property on a module, class, or structure.</span></span> <span data-ttu-id="9a264-104">Özellik yordamları, *özellik erişimcileri*olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="9a264-104">Property procedures are also known as *property accessors*.</span></span>

<span data-ttu-id="9a264-105">Visual Basic aşağıdaki özellik yordamları için sağlar:</span><span class="sxs-lookup"><span data-stu-id="9a264-105">Visual Basic provides for the following property procedures:</span></span>

- <span data-ttu-id="9a264-106">`Get` yordam bir özelliğin değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="9a264-106">A `Get` procedure returns the value of a property.</span></span> <span data-ttu-id="9a264-107">Bir ifadede özelliğe eriştiğinizde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="9a264-107">It is called when you access the property in an expression.</span></span>
- <span data-ttu-id="9a264-108">`Set` yordam bir özelliği bir nesne başvurusu dahil olmak üzere bir değere ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9a264-108">A `Set` procedure sets a property to a value, including an object reference.</span></span> <span data-ttu-id="9a264-109">Özelliğe bir değer atadığınızda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="9a264-109">It is called when you assign a value to the property.</span></span>

<span data-ttu-id="9a264-110">Genellikle özellik yordamlarını `Get` ve `Set` deyimlerini kullanarak çiftler halinde tanımlarsınız, ancak özellik salt okunurdur ([Get deyimi](../../../../visual-basic/language-reference/statements/get-statement.md)) veya salt yazılır ([küme deyimi](../../../../visual-basic/language-reference/statements/set-statement.md)) olduğunda tek başına yordamı tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a264-110">You usually define property procedures in pairs, using the `Get` and `Set` statements, but you can define either procedure alone if the property is read-only ([Get Statement](../../../../visual-basic/language-reference/statements/get-statement.md)) or write-only ([Set Statement](../../../../visual-basic/language-reference/statements/set-statement.md)).</span></span>

<span data-ttu-id="9a264-111">Otomatik uygulanan bir özellik kullanırken `Get` ve `Set` yordamını atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a264-111">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="9a264-112">Daha fazla bilgi için bkz. [Otomatik uygulanan özellikler](./auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="9a264-112">For more information, see [Auto-Implemented Properties](./auto-implemented-properties.md).</span></span>

<span data-ttu-id="9a264-113">Sınıflar, yapılar ve modüllerde özellikler tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a264-113">You can define properties in classes, structures, and modules.</span></span> <span data-ttu-id="9a264-114">Özellikler varsayılan olarak `Public`, bu da bunları, uygulamanızın özelliğin kapsayıcısına erişebilen herhangi bir yerinden çağırabilmeniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="9a264-114">Properties are `Public` by default, which means you can call them from anywhere in your application that can access the property's container.</span></span>

<span data-ttu-id="9a264-115">Özelliklerin ve değişkenlerin karşılaştırması için [Visual Basic Özellikler ve değişkenler arasındaki farklılıklar](differences-between-properties-and-variables.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="9a264-115">For a comparison of properties and variables, see [Differences Between Properties and Variables in Visual Basic](differences-between-properties-and-variables.md).</span></span>

## <a name="declaration-syntax"></a><span data-ttu-id="9a264-116">Bildirim söz dizimi</span><span class="sxs-lookup"><span data-stu-id="9a264-116">Declaration syntax</span></span>

<span data-ttu-id="9a264-117">Bir özelliğin kendisi, [özellik ifadesinin](../../../../visual-basic/language-reference/statements/property-statement.md) içinde ve `End Property` ifadesiyle bir kod bloğu tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="9a264-117">A property itself is defined by a block of code enclosed within the [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="9a264-118">Bu bloğun içinde her özellik yordamı bir bildirim bildirimi (`Get` veya `Set`) ve eşleşen `End` bildirimi içinde iç bir blok olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="9a264-118">Inside this block, each property procedure appears as an internal block enclosed within a declaration statement (`Get` or `Set`) and the matching `End` declaration.</span></span>

<span data-ttu-id="9a264-119">Bir özelliği ve yordamlarını bildirmek için sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="9a264-119">The syntax for declaring a property and its procedures is as follows:</span></span>

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

<span data-ttu-id="9a264-120">`Modifiers`, aşırı yükleme, geçersiz kılma, paylaşma ve gölgeleme ile ilgili erişim düzeyini ve bilgileri belirtebilir, özelliğin salt okunurdur mi yoksa salt yazılır mı olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="9a264-120">The `Modifiers` can specify access level and information regarding overloading, overriding, sharing, and shadowing, as well as whether the property is read-only or write-only.</span></span> <span data-ttu-id="9a264-121">`Get` veya `Set` yordamındaki `AccessLevel`, özelliğin kendisi için belirtilen erişim düzeyinden daha kısıtlayıcı olan herhangi bir düzey olabilir.</span><span class="sxs-lookup"><span data-stu-id="9a264-121">The `AccessLevel` on the `Get` or `Set` procedure can be any level that is more restrictive than the access level specified for the property itself.</span></span> <span data-ttu-id="9a264-122">Daha fazla bilgi için bkz. [özellik açıklaması](../../../../visual-basic/language-reference/statements/property-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9a264-122">For more information, see [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md).</span></span>

### <a name="data-type"></a><span data-ttu-id="9a264-123">Veri Türü</span><span class="sxs-lookup"><span data-stu-id="9a264-123">Data Type</span></span>

<span data-ttu-id="9a264-124">Özelliğin veri türü ve asıl erişim düzeyi, özellik yordamlarında değil, `Property` bildiriminde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9a264-124">A property's data type and principal access level are defined in the `Property` statement, not in the property procedures.</span></span> <span data-ttu-id="9a264-125">Bir özellik yalnızca bir veri türüne sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="9a264-125">A property can have only one data type.</span></span> <span data-ttu-id="9a264-126">Örneğin, `Decimal` bir değeri depolamak için bir özellik tanımlayamazsınız, ancak bir `Double` değeri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a264-126">For example, you cannot define a property to store a `Decimal` value but retrieve a `Double` value.</span></span>

### <a name="access-level"></a><span data-ttu-id="9a264-127">Erişim düzeyi</span><span class="sxs-lookup"><span data-stu-id="9a264-127">Access Level</span></span>

<span data-ttu-id="9a264-128">Ancak, bir özellik için bir asıl erişim düzeyi tanımlayabilir ve özellik yordamlarından birinde erişim düzeyini daha da kısıtlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a264-128">However, you can define a principal access level for a property and further restrict the access level in one of its property procedures.</span></span> <span data-ttu-id="9a264-129">Örneğin, bir `Public` özelliği tanımlayabilir ve sonra bir `Private Set` yordamı tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a264-129">For example, you can define a `Public` property and then define a `Private Set` procedure.</span></span> <span data-ttu-id="9a264-130">`Get` yordam `Public`kalır.</span><span class="sxs-lookup"><span data-stu-id="9a264-130">The `Get` procedure remains `Public`.</span></span> <span data-ttu-id="9a264-131">Erişim düzeyini bir özelliğin yordamlarından yalnızca birinde değiştirebilirsiniz ve yalnızca asıl erişim düzeyinden daha kısıtlayıcı hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a264-131">You can change the access level in only one of a property's procedures, and you can only make it more restrictive than the principal access level.</span></span> <span data-ttu-id="9a264-132">Daha fazla bilgi için bkz. [nasıl yapılır: karışık erişim düzeylerine sahip bir özellik bildirme](how-to-declare-a-property-with-mixed-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="9a264-132">For more information, see [How to: Declare a Property with Mixed Access Levels](how-to-declare-a-property-with-mixed-access-levels.md).</span></span>

## <a name="parameter-declaration"></a><span data-ttu-id="9a264-133">Parametre bildirimi</span><span class="sxs-lookup"><span data-stu-id="9a264-133">Parameter declaration</span></span>

<span data-ttu-id="9a264-134">Geçirilen mekanizmanın `ByVal`olması dışında, her bir parametreyi [alt yordamlar](sub-procedures.md)için yaptığınız gibi bildirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a264-134">You declare each parameter the same way you do for [Sub Procedures](sub-procedures.md), except that the passing mechanism must be `ByVal`.</span></span>

<span data-ttu-id="9a264-135">Parametre listesindeki her bir parametre için sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="9a264-135">The syntax for each parameter in the parameter list is as follows:</span></span>

```vb
[Optional] ByVal [ParamArray] parametername As datatype
```

<span data-ttu-id="9a264-136">Parametre isteğe bağlı ise, bildiriminin bir parçası olarak bir varsayılan değer de belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9a264-136">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="9a264-137">Varsayılan bir değer belirtmek için sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="9a264-137">The syntax for specifying a default value is as follows:</span></span>

```vb
Optional ByVal parametername As datatype = defaultvalue
```

## <a name="property-value"></a><span data-ttu-id="9a264-138">Özellik değeri</span><span class="sxs-lookup"><span data-stu-id="9a264-138">Property value</span></span>

<span data-ttu-id="9a264-139">`Get` yordamında, dönüş değeri, özelliğin değeri olarak çağırma ifadesine sağlanır.</span><span class="sxs-lookup"><span data-stu-id="9a264-139">In a `Get` procedure, the return value is supplied to the calling expression as the value of the property.</span></span>

<span data-ttu-id="9a264-140">`Set` yordamında, yeni özellik değeri `Set` deyimin parametresine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="9a264-140">In a `Set` procedure, the new property value is passed to the parameter of the `Set` statement.</span></span> <span data-ttu-id="9a264-141">Açıkça bir parametre bildirirseniz, özelliği ile aynı veri türüyle bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9a264-141">If you explicitly declare a parameter, you must declare it with the same data type as the property.</span></span> <span data-ttu-id="9a264-142">Bir parametre bildirmezsiniz derleyici, özelliğe atanacak yeni değeri göstermek için `Value` örtük parametresini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9a264-142">If you do not declare a parameter, the compiler uses the implicit parameter `Value` to represent the new value to be assigned to the property.</span></span>

## <a name="calling-syntax"></a><span data-ttu-id="9a264-143">Çağırma sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9a264-143">Calling syntax</span></span>

<span data-ttu-id="9a264-144">Özelliğe başvuru yaparak bir özellik yordamını örtük olarak çağırılır.</span><span class="sxs-lookup"><span data-stu-id="9a264-144">You invoke a property procedure implicitly by making reference to the property.</span></span> <span data-ttu-id="9a264-145">Özelliği, isteğe bağlı olmayan tüm bağımsız değişkenlerin değerlerini sağlamanız ve bağımsız değişken listesini parantez içine almanız gerekir, ancak, özelliğin adını bir değişkenin adını kullandığınız şekilde kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="9a264-145">You use the name of the property the same way you would use the name of a variable, except that you must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="9a264-146">Herhangi bir bağımsız değişken sağlanmazsa, isteğe bağlı olarak ayraçları atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a264-146">If no arguments are supplied, you can optionally omit the parentheses.</span></span>

<span data-ttu-id="9a264-147">Bir `Set` yordamına örtük çağrının sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="9a264-147">The syntax for an implicit call to a `Set` procedure is as follows:</span></span>

```vb
propertyname[(argumentlist)] = expression
```

<span data-ttu-id="9a264-148">Bir `Get` yordamına örtük çağrının sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="9a264-148">The syntax for an implicit call to a `Get` procedure is as follows:</span></span>

```vb
lvalue = propertyname[(argumentlist)]
Do While (propertyname[(argumentlist)] > expression)
```

### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="9a264-149">Bildirim ve çağrı gösterimi</span><span class="sxs-lookup"><span data-stu-id="9a264-149">Illustration of declaration and call</span></span>

<span data-ttu-id="9a264-150">Aşağıdaki özellik, tam adı iki anayent adı, ad ve soyadı olarak depolar.</span><span class="sxs-lookup"><span data-stu-id="9a264-150">The following property stores a full name as two constituent names, the first name and the last name.</span></span> <span data-ttu-id="9a264-151">Çağıran kod `fullName`okurken, `Get` yordamı iki anayent adını birleştirir ve tam adı döndürür.</span><span class="sxs-lookup"><span data-stu-id="9a264-151">When the calling code reads `fullName`, the `Get` procedure combines the two constituent names and returns the full name.</span></span> <span data-ttu-id="9a264-152">Çağıran kod yeni bir tam ad atarken, `Set` yordamı onu iki anayada bölmek için çalışır.</span><span class="sxs-lookup"><span data-stu-id="9a264-152">When the calling code assigns a new full name, the `Set` procedure attempts to break it into two constituent names.</span></span> <span data-ttu-id="9a264-153">Bir boşluk bulamazsa, ilk ad olarak tümünü depolar.</span><span class="sxs-lookup"><span data-stu-id="9a264-153">If it does not find a space, it stores it all as the first name.</span></span>

[!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]

<span data-ttu-id="9a264-154">Aşağıdaki örnek, `fullName`Özellik yordamlarına yapılan tipik çağrıları gösterir:</span><span class="sxs-lookup"><span data-stu-id="9a264-154">The following example shows typical calls to the property procedures of `fullName`:</span></span>

[!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]

## <a name="see-also"></a><span data-ttu-id="9a264-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a264-155">See also</span></span>

- [<span data-ttu-id="9a264-156">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="9a264-156">Procedures</span></span>](index.md)
- [<span data-ttu-id="9a264-157">İşlev Yordamları</span><span class="sxs-lookup"><span data-stu-id="9a264-157">Function Procedures</span></span>](function-procedures.md)
- [<span data-ttu-id="9a264-158">İşleç Yordamları</span><span class="sxs-lookup"><span data-stu-id="9a264-158">Operator Procedures</span></span>](operator-procedures.md)
- [<span data-ttu-id="9a264-159">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="9a264-159">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="9a264-160">Visual Basic Özellikler ve değişkenler arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="9a264-160">Differences Between Properties and Variables in Visual Basic</span></span>](differences-between-properties-and-variables.md)
- [<span data-ttu-id="9a264-161">Nasıl yapılır: Özellik Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9a264-161">How to: Create a Property</span></span>](how-to-create-a-property.md)
- [<span data-ttu-id="9a264-162">Nasıl yapılır: Bir Özellik Yordamı Çağırma</span><span class="sxs-lookup"><span data-stu-id="9a264-162">How to: Call a Property Procedure</span></span>](how-to-call-a-property-procedure.md)
- [<span data-ttu-id="9a264-163">Nasıl yapılır: Visual Basic varsayılan bir özellik bildirme ve çağırma</span><span class="sxs-lookup"><span data-stu-id="9a264-163">How to: Declare and Call a Default Property in Visual Basic</span></span>](how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="9a264-164">Nasıl yapılır: Bir Özelliğe Değer Ekleme</span><span class="sxs-lookup"><span data-stu-id="9a264-164">How to: Put a Value in a Property</span></span>](how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="9a264-165">Nasıl yapılır: Bir Özellikten Değer Alma</span><span class="sxs-lookup"><span data-stu-id="9a264-165">How to: Get a Value from a Property</span></span>](how-to-get-a-value-from-a-property.md)
