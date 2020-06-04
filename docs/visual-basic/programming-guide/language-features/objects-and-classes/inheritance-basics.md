---
title: Devralma Temelleri
ms.date: 07/20/2015
helpviewer_keywords:
- derived classes [Visual Basic], inheritance
- MyClass keyword [Visual Basic], using
- MyBase keyword [Visual Basic], using
- Inherits statement [Visual Basic], inheritance
- overriding, Overridable keyword
- MustInherit keyword [Visual Basic], using
- Overrides keyword [Visual Basic], using
- inheritance
- MustInherit classes [Visual Basic]
- MustOverride keyword [Visual Basic], using
- classes [Visual Basic], derived
- NotInheritable keyword [Visual Basic], using
- base classes [Visual Basic], extending properties and methods [Visual Basic]
- NotOverridable keyword [Visual Basic], using
- base classes [Visual Basic], inheritance
- abstract classes [Visual Basic], inheritance
- overriding, Overrides keyword
ms.assetid: dfc8deba-f5b3-4d1d-a937-7cb826446fc5
ms.openlocfilehash: 3bf1847f618a642d26df4aa1c5247a4ba2bd3b23
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411785"
---
# <a name="inheritance-basics-visual-basic"></a><span data-ttu-id="25ba1-102">Devralma Temelleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25ba1-102">Inheritance Basics (Visual Basic)</span></span>

<span data-ttu-id="25ba1-103">İfade, bir `Inherits` *temel sınıf*olarak bilinen varolan bir sınıfa göre *türetilmiş sınıf*olarak adlandırılan yeni bir sınıf bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="25ba1-103">The `Inherits` statement is used to declare a new class, called a *derived class*, based on an existing class, known as a *base class*.</span></span> <span data-ttu-id="25ba1-104">Türetilmiş sınıflar devralınır ve temel sınıfta tanımlanan özellikleri, yöntemleri, olayları, alanları ve sabitleri genişletebilir.</span><span class="sxs-lookup"><span data-stu-id="25ba1-104">Derived classes inherit, and can extend, the properties, methods, events, fields, and constants defined in the base class.</span></span> <span data-ttu-id="25ba1-105">Aşağıdaki bölümde, devralma için bazı kurallar ve sınıfların devralınması veya Devralındığı şekilde değiştirmek için kullanabileceğiniz değiştiriciler açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="25ba1-105">The following section describes some of the rules for inheritance, and the modifiers you can use to change the way classes inherit or are inherited:</span></span>

- <span data-ttu-id="25ba1-106">Varsayılan olarak, anahtar sözcüğüyle işaretlenmedikçe tüm sınıflar devralınabilir `NotInheritable` .</span><span class="sxs-lookup"><span data-stu-id="25ba1-106">By default, all classes are inheritable unless marked with the `NotInheritable` keyword.</span></span> <span data-ttu-id="25ba1-107">Sınıflar, projenizdeki diğer sınıflardan veya projenizin başvurduğu diğer derlemelerin sınıflarından devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="25ba1-107">Classes can inherit from other classes in your project or from classes in other assemblies that your project references.</span></span>

- <span data-ttu-id="25ba1-108">Birden çok devralmaya izin veren dillerden farklı olarak Visual Basic sınıflarda yalnızca tekli devralmaya izin verir; diğer bir deyişle, türetilmiş sınıfların yalnızca bir taban sınıfı olabilir.</span><span class="sxs-lookup"><span data-stu-id="25ba1-108">Unlike languages that allow multiple inheritance, Visual Basic allows only single inheritance in classes; that is, derived classes can have only one base class.</span></span> <span data-ttu-id="25ba1-109">Sınıflarda birden çok devralmaya izin verilmese de sınıflar, aynı uçları etkin bir şekilde gerçekleştirebilen birden çok arabirim uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="25ba1-109">Although multiple inheritance is not allowed in classes, classes can implement multiple interfaces, which can effectively accomplish the same ends.</span></span>

- <span data-ttu-id="25ba1-110">Bir temel sınıfta kısıtlı öğelerin sunulmasını engellemek için, türetilmiş bir sınıfın erişim türü, taban sınıfına eşit veya daha kısıtlayıcı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="25ba1-110">To prevent exposing restricted items in a base class, the access type of a derived class must be equal to or more restrictive than its base class.</span></span> <span data-ttu-id="25ba1-111">Örneğin, bir sınıf `Public` bir `Friend` veya `Private` sınıfını alamaz ve bir sınıf bir `Friend` `Private` sınıfı devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="25ba1-111">For example, a `Public` class cannot inherit a `Friend` or a `Private` class, and a `Friend` class cannot inherit a `Private` class.</span></span>

## <a name="inheritance-modifiers"></a><span data-ttu-id="25ba1-112">Devralma değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="25ba1-112">Inheritance Modifiers</span></span>

<span data-ttu-id="25ba1-113">Visual Basic devralmayı desteklemek için aşağıdaki sınıf düzeyi deyimleri ve değiştiricilerini tanıtır:</span><span class="sxs-lookup"><span data-stu-id="25ba1-113">Visual Basic introduces the following class-level statements and modifiers to support inheritance:</span></span>

- <span data-ttu-id="25ba1-114">`Inherits`ifade — temel sınıfı belirtir.</span><span class="sxs-lookup"><span data-stu-id="25ba1-114">`Inherits` statement — Specifies the base class.</span></span>

- <span data-ttu-id="25ba1-115">`NotInheritable`değiştirici — programcıların sınıfı temel sınıf olarak kullanmasını engeller.</span><span class="sxs-lookup"><span data-stu-id="25ba1-115">`NotInheritable` modifier — Prevents programmers from using the class as a base class.</span></span>

- <span data-ttu-id="25ba1-116">`MustInherit`değiştirici — sınıfın yalnızca temel sınıf olarak kullanılması amaçlandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="25ba1-116">`MustInherit` modifier — Specifies that the class is intended for use as a base class only.</span></span> <span data-ttu-id="25ba1-117">Sınıfların örnekleri `MustInherit` doğrudan oluşturulamaz; yalnızca türetilmiş bir sınıfın temel sınıf örnekleri olarak oluşturulabilirler.</span><span class="sxs-lookup"><span data-stu-id="25ba1-117">Instances of `MustInherit` classes cannot be created directly; they can only be created as base class instances of a derived class.</span></span> <span data-ttu-id="25ba1-118">(C++ ve C# gibi diğer programlama dilleri, bu tür bir sınıfı anlatmak için *soyut sınıf* terimini kullanır.)</span><span class="sxs-lookup"><span data-stu-id="25ba1-118">(Other programming languages, such as C++ and C#, use the term *abstract class* to describe such a class.)</span></span>

## <a name="overriding-properties-and-methods-in-derived-classes"></a><span data-ttu-id="25ba1-119">Türetilmiş sınıflarda özellikleri ve yöntemleri geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="25ba1-119">Overriding Properties and Methods in Derived Classes</span></span>

<span data-ttu-id="25ba1-120">Varsayılan olarak, türetilmiş bir sınıf, temel sınıfından özellikleri ve yöntemleri devralır.</span><span class="sxs-lookup"><span data-stu-id="25ba1-120">By default, a derived class inherits properties and methods from its base class.</span></span> <span data-ttu-id="25ba1-121">Devralınan bir özelliğin veya yöntemin türetilmiş sınıfta farklı davranması gerekiyorsa, *geçersiz kılınabilir*.</span><span class="sxs-lookup"><span data-stu-id="25ba1-121">If an inherited property or method has to behave differently in the derived class it can be *overridden*.</span></span> <span data-ttu-id="25ba1-122">Diğer bir deyişle, türetilmiş sınıfta yönteminin yeni bir uygulamasını tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25ba1-122">That is, you can define a new implementation of the method in the derived class.</span></span> <span data-ttu-id="25ba1-123">Özelliklerin ve yöntemlerin nasıl geçersiz kılınabileceğini denetlemek için aşağıdaki değiştiriciler kullanılır:</span><span class="sxs-lookup"><span data-stu-id="25ba1-123">The following modifiers are used to control how properties and methods are overridden:</span></span>

- <span data-ttu-id="25ba1-124">`Overridable`— Bir sınıftaki özelliğin veya yöntemin türetilmiş bir sınıfta geçersiz kılınmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="25ba1-124">`Overridable` — Allows a property or method in a class to be overridden in a derived class.</span></span>

- <span data-ttu-id="25ba1-125">`Overrides`— `Overridable` Temel sınıfta tanımlanan bir özelliği veya yöntemi geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="25ba1-125">`Overrides` — Overrides an `Overridable` property or method defined in the base class.</span></span>

- <span data-ttu-id="25ba1-126">`NotOverridable`— Bir özelliğin veya yöntemin devralan bir sınıfta geçersiz kılınmasını önler.</span><span class="sxs-lookup"><span data-stu-id="25ba1-126">`NotOverridable` — Prevents a property or method from being overridden in an inheriting class.</span></span> <span data-ttu-id="25ba1-127">Varsayılan olarak `Public` Yöntemler `NotOverridable` .</span><span class="sxs-lookup"><span data-stu-id="25ba1-127">By default, `Public` methods are `NotOverridable`.</span></span>

- <span data-ttu-id="25ba1-128">`MustOverride`— Türetilmiş bir sınıfın özelliği veya yöntemi geçersiz kılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="25ba1-128">`MustOverride` — Requires that a derived class override the property or method.</span></span> <span data-ttu-id="25ba1-129">`MustOverride`Anahtar sözcüğü kullanıldığında, yöntem tanımı yalnızca `Sub` , `Function` , veya `Property` deyiminden oluşur.</span><span class="sxs-lookup"><span data-stu-id="25ba1-129">When the `MustOverride` keyword is used, the method definition consists of just the `Sub`, `Function`, or `Property` statement.</span></span> <span data-ttu-id="25ba1-130">Başka hiçbir ifadeye izin verilmez ve özellikle bir `End Sub` veya `End Function` deyimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="25ba1-130">No other statements are allowed, and specifically there is no `End Sub` or `End Function` statement.</span></span> <span data-ttu-id="25ba1-131">`MustOverride`Yöntemler `MustInherit` sınıflarda bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="25ba1-131">`MustOverride` methods must be declared in `MustInherit` classes.</span></span>

<span data-ttu-id="25ba1-132">Bordroları işlemek için sınıflar tanımlamak istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="25ba1-132">Suppose you want to define classes to handle payroll.</span></span> <span data-ttu-id="25ba1-133">`Payroll` `RunPayroll` Tipik bir hafta için bordroları hesaplayan bir yöntemi içeren genel bir sınıf tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25ba1-133">You could define a generic `Payroll` class that contains a `RunPayroll` method that calculates payroll for a typical week.</span></span> <span data-ttu-id="25ba1-134">`Payroll`Daha sonra `BonusPayroll` , çalışan primi dağıtılırken kullanılabilecek daha özelleştirilmiş bir sınıf için temel sınıf olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="25ba1-134">You could then use `Payroll` as a base class for a more specialized `BonusPayroll` class, which could be used when distributing employee bonuses.</span></span>

<span data-ttu-id="25ba1-135">`BonusPayroll`Sınıfı, `PayEmployee` temel sınıfta tanımlanan yöntemi alabilir ve geçersiz kılabilir `Payroll` .</span><span class="sxs-lookup"><span data-stu-id="25ba1-135">The `BonusPayroll` class can inherit, and override, the `PayEmployee` method defined in the base `Payroll` class.</span></span>

<span data-ttu-id="25ba1-136">Aşağıdaki örnek, bir temel sınıfı `Payroll,` ve devralınmış bir yöntemi geçersiz kılan türetilmiş bir sınıfı tanımlar `BonusPayroll` `PayEmployee` .</span><span class="sxs-lookup"><span data-stu-id="25ba1-136">The following example defines a base class, `Payroll,` and a derived class, `BonusPayroll`, which overrides an inherited method, `PayEmployee`.</span></span> <span data-ttu-id="25ba1-137">Bir yordam,, her iki nesnenin yöntemini çalıştıran bir `RunPayroll` işleve bir nesne ve bir nesnesi oluşturur ve geçirir `Payroll` `BonusPayroll` `Pay` `PayEmployee` .</span><span class="sxs-lookup"><span data-stu-id="25ba1-137">A procedure, `RunPayroll`, creates and then passes a `Payroll` object and a `BonusPayroll` object to a function, `Pay`, that executes the `PayEmployee` method of both objects.</span></span>

[!code-vb[VbVbalrOOP#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#28)]

## <a name="the-mybase-keyword"></a><span data-ttu-id="25ba1-138">MyBase anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="25ba1-138">The MyBase Keyword</span></span>

<span data-ttu-id="25ba1-139">`MyBase`Anahtar sözcüğü, sınıfın geçerli örneğinin temel sınıfına başvuran bir nesne değişkeni gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="25ba1-139">The `MyBase` keyword behaves like an object variable that refers to the base class of the current instance of a class.</span></span> <span data-ttu-id="25ba1-140">`MyBase`, türetilmiş bir sınıfta geçersiz kılınan veya gölgeli temel sınıf üyelerine erişmek için sık kullanılır.</span><span class="sxs-lookup"><span data-stu-id="25ba1-140">`MyBase` is frequently used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="25ba1-141">Özellikle, `MyBase.New` türetilmiş bir sınıf oluşturucusundan bir temel sınıf oluşturucusunu açıkça çağırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="25ba1-141">In particular, `MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>

<span data-ttu-id="25ba1-142">Örneğin, temel sınıftan devralınan bir yöntemi geçersiz kılan türetilmiş bir sınıf tasarlamakta olduğunuzu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="25ba1-142">For example, suppose you are designing a derived class that overrides a method inherited from the base class.</span></span> <span data-ttu-id="25ba1-143">Geçersiz kılınan yöntem, temel sınıfta yöntemi çağırabilir ve döndürülen değeri aşağıdaki kod parçasında gösterildiği gibi değiştirebilir:</span><span class="sxs-lookup"><span data-stu-id="25ba1-143">The overridden method can call the method in the base class and modify the return value as shown in the following code fragment:</span></span>

[!code-vb[VbVbalrOOP#109](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#109)]

<span data-ttu-id="25ba1-144">Aşağıdaki listede, kullanma kısıtlamaları açıklanmaktadır `MyBase` :</span><span class="sxs-lookup"><span data-stu-id="25ba1-144">The following list describes restrictions on using `MyBase`:</span></span>

- <span data-ttu-id="25ba1-145">`MyBase`en hızlı temel sınıfa ve devralınan üyelerine başvurur.</span><span class="sxs-lookup"><span data-stu-id="25ba1-145">`MyBase` refers to the immediate base class and its inherited members.</span></span> <span data-ttu-id="25ba1-146">Sınıftaki üyelere erişmek için kullanılamaz `Private` .</span><span class="sxs-lookup"><span data-stu-id="25ba1-146">It cannot be used to access `Private` members in the class.</span></span>

- <span data-ttu-id="25ba1-147">`MyBase`, gerçek bir nesne değil, bir anahtar sözcüktür.</span><span class="sxs-lookup"><span data-stu-id="25ba1-147">`MyBase` is a keyword, not a real object.</span></span> <span data-ttu-id="25ba1-148">`MyBase`bir değişkene atanamaz, yordamlara geçirilemez veya bir `Is` karşılaştırmada kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="25ba1-148">`MyBase` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>

- <span data-ttu-id="25ba1-149">`MyBase`Niteleyen yöntemin, anlık temel sınıfta tanımlanması gerekmez; bunun yerine dolaylı olarak devralınan bir temel sınıfta tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="25ba1-149">The method that `MyBase` qualifies does not have to be defined in the immediate base class; it may instead be defined in an indirectly inherited base class.</span></span> <span data-ttu-id="25ba1-150">Bir başvurunun `MyBase` doğru bir şekilde derlenmesi için, bazı temel sınıflar, çağrıda görünen ad ve parametre türleriyle eşleşen bir yöntem içermelidir.</span><span class="sxs-lookup"><span data-stu-id="25ba1-150">In order for a reference qualified by `MyBase` to compile correctly, some base class must contain a method matching the name and types of parameters that appear in the call.</span></span>

- <span data-ttu-id="25ba1-151">`MyBase` `MustOverride` Temel sınıf yöntemlerini çağırmak için kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="25ba1-151">You cannot use `MyBase` to call `MustOverride` base class methods.</span></span>

- <span data-ttu-id="25ba1-152">`MyBase`kendisini nitelemek için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="25ba1-152">`MyBase` cannot be used to qualify itself.</span></span> <span data-ttu-id="25ba1-153">Bu nedenle, aşağıdaki kod geçerli değildir:</span><span class="sxs-lookup"><span data-stu-id="25ba1-153">Therefore, the following code is not valid:</span></span>

  `MyBase.MyBase.BtnOK_Click()`

- <span data-ttu-id="25ba1-154">`MyBase`modüllerde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="25ba1-154">`MyBase` cannot be used in modules.</span></span>

- <span data-ttu-id="25ba1-155">`MyBase``Friend`temel sınıf farklı bir derlemede yer alıyorsa olarak işaretlenen temel sınıf üyelerine erişmek için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="25ba1-155">`MyBase` cannot be used to access base class members that are marked as `Friend` if the base class is in a different assembly.</span></span>

<span data-ttu-id="25ba1-156">Daha fazla bilgi ve diğer bir örnek için bkz. [nasıl yapılır: türetilmiş bir sınıf tarafından gizlenen bir değişkene erişme](../declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span><span class="sxs-lookup"><span data-stu-id="25ba1-156">For more information and another example, see [How to: Access a Variable Hidden by a Derived Class](../declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>

## <a name="the-myclass-keyword"></a><span data-ttu-id="25ba1-157">MyClass anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="25ba1-157">The MyClass Keyword</span></span>

<span data-ttu-id="25ba1-158">`MyClass`Anahtar sözcüğü, başlangıçta uygulanmış olan bir sınıfın geçerli örneğine başvuran bir nesne değişkeni gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="25ba1-158">The `MyClass` keyword behaves like an object variable that refers to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="25ba1-159">`MyClass`benzerdir `Me` , ancak her yöntem ve özellik çağrısı, `MyClass` Yöntem veya özellik [NotOverridable](../../../language-reference/modifiers/notoverridable.md)gibi değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="25ba1-159">`MyClass` resembles `Me`, but every method and property call on `MyClass` is treated as if the method or property were [NotOverridable](../../../language-reference/modifiers/notoverridable.md).</span></span> <span data-ttu-id="25ba1-160">Bu nedenle, yöntem veya özellik türetilmiş bir sınıfta geçersiz kılınmadan etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="25ba1-160">Therefore, the method or property is not affected by overriding in a derived class.</span></span>

- <span data-ttu-id="25ba1-161">`MyClass`, gerçek bir nesne değil, bir anahtar sözcüktür.</span><span class="sxs-lookup"><span data-stu-id="25ba1-161">`MyClass` is a keyword, not a real object.</span></span> <span data-ttu-id="25ba1-162">`MyClass`bir değişkene atanamaz, yordamlara geçirilemez veya bir `Is` karşılaştırmada kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="25ba1-162">`MyClass` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>

- <span data-ttu-id="25ba1-163">`MyClass`içerilen sınıfa ve devralınan üyelerine başvurur.</span><span class="sxs-lookup"><span data-stu-id="25ba1-163">`MyClass` refers to the containing class and its inherited members.</span></span>

- <span data-ttu-id="25ba1-164">`MyClass`, Üyeler için bir niteleyici olarak kullanılabilir `Shared` .</span><span class="sxs-lookup"><span data-stu-id="25ba1-164">`MyClass` can be used as a qualifier for `Shared` members.</span></span>

- <span data-ttu-id="25ba1-165">`MyClass`bir yöntem içinde kullanılamaz `Shared` , ancak bir sınıfın paylaşılan üyesine erişmek için bir örnek yöntemi içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="25ba1-165">`MyClass` cannot be used inside a `Shared` method, but can be used inside an instance method to access a shared member of a class.</span></span>

- <span data-ttu-id="25ba1-166">`MyClass`standart modüllerde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="25ba1-166">`MyClass` cannot be used in standard modules.</span></span>

- <span data-ttu-id="25ba1-167">`MyClass`, bir temel sınıfta tanımlanan ve bu sınıfta sağlanmış yöntemin uygulanması olmayan bir yöntemi nitelemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="25ba1-167">`MyClass` can be used to qualify a method that is defined in a base class and that has no implementation of the method provided in that class.</span></span> <span data-ttu-id="25ba1-168">Bu tür bir başvuru, yöntemiyle aynı anlama sahiptir `MyBase.` *Method*.</span><span class="sxs-lookup"><span data-stu-id="25ba1-168">Such a reference has the same meaning as `MyBase.`*Method*.</span></span>

<span data-ttu-id="25ba1-169">Aşağıdaki örnek `Me` ve ile karşılaştırılır `MyClass` .</span><span class="sxs-lookup"><span data-stu-id="25ba1-169">The following example compares `Me` and `MyClass`.</span></span>

```vb
Class baseClass
    Public Overridable Sub testMethod()
        MsgBox("Base class string")
    End Sub
    Public Sub useMe()
        ' The following call uses the calling class's method, even if
        ' that method is an override.
        Me.testMethod()
    End Sub
    Public Sub useMyClass()
        ' The following call uses this instance's method and not any
        ' override.
        MyClass.testMethod()
    End Sub
End Class
Class derivedClass : Inherits baseClass
    Public Overrides Sub testMethod()
        MsgBox("Derived class string")
    End Sub
End Class
Class testClasses
    Sub startHere()
        Dim testObj As derivedClass = New derivedClass()
        ' The following call displays "Derived class string".
        testObj.useMe()
        ' The following call displays "Base class string".
        testObj.useMyClass()
    End Sub
End Class
```

<span data-ttu-id="25ba1-170">`derivedClass`Geçersiz kılmalar olsa da `testMethod` , `MyClass` içindeki anahtar sözcüğü `useMyClass` geçersiz kılma etkilerini artırır ve derleyici, öğesinin temel sınıf sürümü çağrısını çözer `testMethod` .</span><span class="sxs-lookup"><span data-stu-id="25ba1-170">Even though `derivedClass` overrides `testMethod`, the `MyClass` keyword in `useMyClass` nullifies the effects of overriding, and the compiler resolves the call to the base class version of `testMethod`.</span></span>

## <a name="see-also"></a><span data-ttu-id="25ba1-171">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25ba1-171">See also</span></span>

- [<span data-ttu-id="25ba1-172">Inherits Deyimi</span><span class="sxs-lookup"><span data-stu-id="25ba1-172">Inherits Statement</span></span>](../../../language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="25ba1-173">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="25ba1-173">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
