---
title: Devralma Temelleri (Visual Basic)
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
ms.openlocfilehash: a31f69459465368dc7519b5126c6c4eb72e25d29
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663004"
---
# <a name="inheritance-basics-visual-basic"></a><span data-ttu-id="dad70-102">Devralma Temelleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dad70-102">Inheritance Basics (Visual Basic)</span></span>
<span data-ttu-id="dad70-103">`Inherits` Deyimi adlı yeni bir sınıf bildirmek için kullanılır bir *türetilmiş sınıf*olarak bilinen varolan bir sınıfa göre bir *temel sınıfı*.</span><span class="sxs-lookup"><span data-stu-id="dad70-103">The `Inherits` statement is used to declare a new class, called a *derived class*, based on an existing class, known as a *base class*.</span></span> <span data-ttu-id="dad70-104">Türetilmiş sınıflarda devralınır ve genişletebilir, özellikleri, yöntemleri, olaylar, alanları ve temel sınıfta tanımlı sabitler.</span><span class="sxs-lookup"><span data-stu-id="dad70-104">Derived classes inherit, and can extend, the properties, methods, events, fields, and constants defined in the base class.</span></span> <span data-ttu-id="dad70-105">Aşağıdaki bölümde bazı devralma kuralları açıklar ve yol sınıflarını değiştirmek için kullanabileceğiniz değiştiricileri devralmıyor veya devralınan:</span><span class="sxs-lookup"><span data-stu-id="dad70-105">The following section describes some of the rules for inheritance, and the modifiers you can use to change the way classes inherit or are inherited:</span></span>  
  
- <span data-ttu-id="dad70-106">Varsayılan olarak, tüm sınıflar ile işaretlenen sürece devralınabilir `NotInheritable` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="dad70-106">By default, all classes are inheritable unless marked with the `NotInheritable` keyword.</span></span> <span data-ttu-id="dad70-107">Sınıflar, projenizdeki diğer sınıfları veya projenizin başvurduğu diğer derlemeleri sınıflarda devralabilir.</span><span class="sxs-lookup"><span data-stu-id="dad70-107">Classes can inherit from other classes in your project or from classes in other assemblies that your project references.</span></span>  
  
- <span data-ttu-id="dad70-108">Birden çok devralma izin dillerden farklı olarak, Visual Basic, yalnızca tek devralma sınıfları sağlar; diğer bir deyişle, türetilmiş sınıflarda yalnızca bir temel sınıf olabilir.</span><span class="sxs-lookup"><span data-stu-id="dad70-108">Unlike languages that allow multiple inheritance, Visual Basic allows only single inheritance in classes; that is, derived classes can have only one base class.</span></span> <span data-ttu-id="dad70-109">Birden çok devralma sınıfları izin verilmez ancak sınıfları aynı uçları etkili bir şekilde gerçekleştirebileceğiniz birden çok arabirim uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="dad70-109">Although multiple inheritance is not allowed in classes, classes can implement multiple interfaces, which can effectively accomplish the same ends.</span></span>  
  
- <span data-ttu-id="dad70-110">Bir temel sınıf kısıtlı öğelerini açığa çıkarılmasını önlemek için eşit veya daha kısıtlayıcı onun temel sınıfından türetilmiş bir sınıfın erişim türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dad70-110">To prevent exposing restricted items in a base class, the access type of a derived class must be equal to or more restrictive than its base class.</span></span> <span data-ttu-id="dad70-111">Örneğin, bir `Public` sınıfı devralamaz bir `Friend` veya `Private` sınıfı ve `Friend` sınıfı devralamaz bir `Private` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="dad70-111">For example, a `Public` class cannot inherit a `Friend` or a `Private` class, and a `Friend` class cannot inherit a `Private` class.</span></span>  
  
## <a name="inheritance-modifiers"></a><span data-ttu-id="dad70-112">Devralma değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="dad70-112">Inheritance Modifiers</span></span>  
 <span data-ttu-id="dad70-113">Visual Basic, aşağıdaki sınıf düzeyi ifadeleri ve devralma desteklemek için değiştiriciler sunar:</span><span class="sxs-lookup"><span data-stu-id="dad70-113">Visual Basic introduces the following class-level statements and modifiers to support inheritance:</span></span>  
  
- <span data-ttu-id="dad70-114">`Inherits` deyimi — temel sınıfını belirtir.</span><span class="sxs-lookup"><span data-stu-id="dad70-114">`Inherits` statement — Specifies the base class.</span></span>  
  
- <span data-ttu-id="dad70-115">`NotInheritable` değiştiricisi — programcıları, sınıfın temel sınıf olarak kullanmasını önler.</span><span class="sxs-lookup"><span data-stu-id="dad70-115">`NotInheritable` modifier — Prevents programmers from using the class as a base class.</span></span>  
  
- <span data-ttu-id="dad70-116">`MustInherit` değiştiricisi — sınıf yalnızca temel sınıf olarak kullanılmak üzere tasarlanmıştır belirtir.</span><span class="sxs-lookup"><span data-stu-id="dad70-116">`MustInherit` modifier — Specifies that the class is intended for use as a base class only.</span></span> <span data-ttu-id="dad70-117">Örneklerini `MustInherit` sınıfları doğrudan oluşturulamıyor; bunlar yalnızca türetilmiş bir sınıf olarak taban sınıf örneklerinin oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="dad70-117">Instances of `MustInherit` classes cannot be created directly; they can only be created as base class instances of a derived class.</span></span> <span data-ttu-id="dad70-118">(C++ gibi diğer programlama dilleri ve C#, terim kullanın *soyut sınıf* gibi bir sınıf tanımlamak için.)</span><span class="sxs-lookup"><span data-stu-id="dad70-118">(Other programming languages, such as C++ and C#, use the term *abstract class* to describe such a class.)</span></span>  
  
## <a name="overriding-properties-and-methods-in-derived-classes"></a><span data-ttu-id="dad70-119">Geçersiz kılma özellikleri ve yöntemleri türetilmiş sınıflarda</span><span class="sxs-lookup"><span data-stu-id="dad70-119">Overriding Properties and Methods in Derived Classes</span></span>  
 <span data-ttu-id="dad70-120">Varsayılan olarak, özellik ve yöntem türetilmiş bir sınıf kendi temel sınıfından devralır.</span><span class="sxs-lookup"><span data-stu-id="dad70-120">By default, a derived class inherits properties and methods from its base class.</span></span> <span data-ttu-id="dad70-121">Bir devralınan özellik veya yöntem türetilmiş bir sınıf içindeki farklı davrandığını varsa olabilir *geçersiz kılınan*.</span><span class="sxs-lookup"><span data-stu-id="dad70-121">If an inherited property or method has to behave differently in the derived class it can be *overridden*.</span></span> <span data-ttu-id="dad70-122">Diğer bir deyişle, türetilmiş bir sınıf içindeki yöntemin yeni bir uygulamasını tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dad70-122">That is, you can define a new implementation of the method in the derived class.</span></span> <span data-ttu-id="dad70-123">Özellikleri ve yöntemleri nasıl geçersiz kılınacağını denetlemek için aşağıdaki değiştiriciler kullanılır:</span><span class="sxs-lookup"><span data-stu-id="dad70-123">The following modifiers are used to control how properties and methods are overridden:</span></span>  
  
- <span data-ttu-id="dad70-124">`Overridable` — Türetilen bir sınıfta geçersiz kılınacak bir sınıftaki bir özellik veya yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="dad70-124">`Overridable` — Allows a property or method in a class to be overridden in a derived class.</span></span>  
  
- <span data-ttu-id="dad70-125">`Overrides` — Geçersiz kılar bir `Overridable` özellik veya yöntem temel sınıfta tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="dad70-125">`Overrides` — Overrides an `Overridable` property or method defined in the base class.</span></span>  
  
- <span data-ttu-id="dad70-126">`NotOverridable` — Türetilen bir sınıfta geçersiz kılınan bir özellik veya yöntem engeller.</span><span class="sxs-lookup"><span data-stu-id="dad70-126">`NotOverridable` — Prevents a property or method from being overridden in an inheriting class.</span></span> <span data-ttu-id="dad70-127">Varsayılan olarak, `Public` yöntemler `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="dad70-127">By default, `Public` methods are `NotOverridable`.</span></span>  
  
- <span data-ttu-id="dad70-128">`MustOverride` — Bir türetilen sınıf özelliği veya yöntemi geçersiz gerektirir.</span><span class="sxs-lookup"><span data-stu-id="dad70-128">`MustOverride` — Requires that a derived class override the property or method.</span></span> <span data-ttu-id="dad70-129">Zaman `MustOverride` anahtar sözcüğü kullanılır, yöntem tanımını oluşan yalnızca `Sub`, `Function`, veya `Property` deyimi.</span><span class="sxs-lookup"><span data-stu-id="dad70-129">When the `MustOverride` keyword is used, the method definition consists of just the `Sub`, `Function`, or `Property` statement.</span></span> <span data-ttu-id="dad70-130">Diğer bir deyimlerine izin ve özellikle yoktur hiçbir `End Sub` veya `End Function` deyimi.</span><span class="sxs-lookup"><span data-stu-id="dad70-130">No other statements are allowed, and specifically there is no `End Sub` or `End Function` statement.</span></span> <span data-ttu-id="dad70-131">`MustOverride` yöntem içinde bildirilmesi gerekir `MustInherit` sınıfları.</span><span class="sxs-lookup"><span data-stu-id="dad70-131">`MustOverride` methods must be declared in `MustInherit` classes.</span></span>  
  
 <span data-ttu-id="dad70-132">Bordro işlemek için sınıflar tanımlamak istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="dad70-132">Suppose you want to define classes to handle payroll.</span></span> <span data-ttu-id="dad70-133">Genel tanımlayabilirsiniz `Payroll` içeren sınıf bir `RunPayroll` için tipik bir haftada bir bordro hesaplar yöntemi.</span><span class="sxs-lookup"><span data-stu-id="dad70-133">You could define a generic `Payroll` class that contains a `RunPayroll` method that calculates payroll for a typical week.</span></span> <span data-ttu-id="dad70-134">Ardından kullanabileceğinizi `Payroll` bir temel sınıf için daha özel olarak `BonusPayroll` çalışan ikramiyeler dağıtırken kullanılabilen sınıfı.</span><span class="sxs-lookup"><span data-stu-id="dad70-134">You could then use `Payroll` as a base class for a more specialized `BonusPayroll` class, which could be used when distributing employee bonuses.</span></span>  
  
 <span data-ttu-id="dad70-135">`BonusPayroll` Sınıf devralma ve geçersiz kılmak, `PayEmployee` temel içinde tanımlanan yöntem `Payroll` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="dad70-135">The `BonusPayroll` class can inherit, and override, the `PayEmployee` method defined in the base `Payroll` class.</span></span>  
  
 <span data-ttu-id="dad70-136">Aşağıdaki örnek, bir temel sınıf tanımlar `Payroll,` ve türetilmiş bir sınıf `BonusPayroll`, devralınan bir yöntemi geçersiz kılmalar `PayEmployee`.</span><span class="sxs-lookup"><span data-stu-id="dad70-136">The following example defines a base class, `Payroll,` and a derived class, `BonusPayroll`, which overrides an inherited method, `PayEmployee`.</span></span> <span data-ttu-id="dad70-137">Yordamı, bir `RunPayroll`oluşturur ve sonra geçen bir `Payroll` nesne ve bir `BonusPayroll` bir işlev nesnesine `Pay`, yürütür `PayEmployee` her iki nesnenin yöntemi.</span><span class="sxs-lookup"><span data-stu-id="dad70-137">A procedure, `RunPayroll`, creates and then passes a `Payroll` object and a `BonusPayroll` object to a function, `Pay`, that executes the `PayEmployee` method of both objects.</span></span>  
  
 [!code-vb[VbVbalrOOP#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#28)]  
  
## <a name="the-mybase-keyword"></a><span data-ttu-id="dad70-138">MyBase anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="dad70-138">The MyBase Keyword</span></span>  
 <span data-ttu-id="dad70-139">`MyBase` Anahtar sözcüğü davranacağını gibi geçerli bir sınıf örneğinin temel sınıfına başvuran bir nesne değişkeni.</span><span class="sxs-lookup"><span data-stu-id="dad70-139">The `MyBase` keyword behaves like an object variable that refers to the base class of the current instance of a class.</span></span> <span data-ttu-id="dad70-140">`MyBase` sık sık geçersiz kılınan ya da türetilen bir sınıfta gölgeli bir temel sınıf üyelerinin erişmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dad70-140">`MyBase` is frequently used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="dad70-141">Özellikle, `MyBase.New` bir temel sınıf oluşturucusu bir türetilmiş sınıf oluşturucusunda açıkça çağırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dad70-141">In particular, `MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>  
  
 <span data-ttu-id="dad70-142">Örneğin, temel sınıftan devralınan bir yöntemi geçersiz kılan türetilmiş bir sınıf tasarlarken varsayalım.</span><span class="sxs-lookup"><span data-stu-id="dad70-142">For example, suppose you are designing a derived class that overrides a method inherited from the base class.</span></span> <span data-ttu-id="dad70-143">Geçersiz kılınan yöntemi, temel sınıf yöntemini çağırın ve dönüş değeri aşağıdaki kod parçasını gösterildiği gibi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="dad70-143">The overridden method can call the method in the base class and modify the return value as shown in the following code fragment:</span></span>  
  
 [!code-vb[VbVbalrOOP#109](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#109)]  
  
 <span data-ttu-id="dad70-144">Aşağıdaki listede kullanarak kısıtlamaları açıklamaktadır. `MyBase`:</span><span class="sxs-lookup"><span data-stu-id="dad70-144">The following list describes restrictions on using `MyBase`:</span></span>  
  
- <span data-ttu-id="dad70-145">`MyBase` hemen bir temel sınıf ve devralınan üyeleri ifade eder.</span><span class="sxs-lookup"><span data-stu-id="dad70-145">`MyBase` refers to the immediate base class and its inherited members.</span></span> <span data-ttu-id="dad70-146">Kullanılamaz erişimi `Private` sınıftaki üyeleri.</span><span class="sxs-lookup"><span data-stu-id="dad70-146">It cannot be used to access `Private` members in the class.</span></span>  
  
- <span data-ttu-id="dad70-147">`MyBase` gerçek bir nesne bir anahtar sözcüktür.</span><span class="sxs-lookup"><span data-stu-id="dad70-147">`MyBase` is a keyword, not a real object.</span></span> <span data-ttu-id="dad70-148">`MyBase` bir değişkene atanamaz, yordamlara geçirilen veya kullanılan bir `Is` karşılaştırma.</span><span class="sxs-lookup"><span data-stu-id="dad70-148">`MyBase` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>  
  
- <span data-ttu-id="dad70-149">Yöntemi, `MyBase` niteleyen hemen temel sınıfta tanımlanmış olması gerekmez bunun yerine bir dolaylı olarak devralınan taban sınıf içinde tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="dad70-149">The method that `MyBase` qualifies does not have to be defined in the immediate base class; it may instead be defined in an indirectly inherited base class.</span></span> <span data-ttu-id="dad70-150">Nitelenen başvuru için sırayla `MyBase` doğru şekilde derlenmesi için bazı temel sınıf adını ve çağrıda görünen parametre türleri ile eşleşen bir yöntem içermelidir.</span><span class="sxs-lookup"><span data-stu-id="dad70-150">In order for a reference qualified by `MyBase` to compile correctly, some base class must contain a method matching the name and types of parameters that appear in the call.</span></span>  
  
- <span data-ttu-id="dad70-151">Kullanamazsınız `MyBase` çağrılacak `MustOverride` temel sınıf yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="dad70-151">You cannot use `MyBase` to call `MustOverride` base class methods.</span></span>  
  
- <span data-ttu-id="dad70-152">`MyBase` kendisini nitelemek için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="dad70-152">`MyBase` cannot be used to qualify itself.</span></span> <span data-ttu-id="dad70-153">Bu nedenle, aşağıdaki kodu geçerli değil:</span><span class="sxs-lookup"><span data-stu-id="dad70-153">Therefore, the following code is not valid:</span></span>  
  
     `MyBase.MyBase.BtnOK_Click()`  
  
- <span data-ttu-id="dad70-154">`MyBase` modüllerinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="dad70-154">`MyBase` cannot be used in modules.</span></span>  
  
- <span data-ttu-id="dad70-155">`MyBase` olarak işaretlenmiş temel sınıfın üyelerine erişmek için kullanılamaz `Friend` temel sınıf içinde farklı bir derleme ise.</span><span class="sxs-lookup"><span data-stu-id="dad70-155">`MyBase` cannot be used to access base class members that are marked as `Friend` if the base class is in a different assembly.</span></span>  
  
 <span data-ttu-id="dad70-156">Daha fazla bilgi ve başka bir örnek için bkz: [nasıl yapılır: Türetilmiş sınıf tarafından gizlenen bir değişkene erişme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span><span class="sxs-lookup"><span data-stu-id="dad70-156">For more information and another example, see [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>  
  
## <a name="the-myclass-keyword"></a><span data-ttu-id="dad70-157">MyClass anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="dad70-157">The MyClass Keyword</span></span>  
 <span data-ttu-id="dad70-158">`MyClass` Anahtar sözcüğü davranacağını gibi bir nesne değişkeni özgün olarak uygulandığı bir sınıfın geçerli örneğine başvurur.</span><span class="sxs-lookup"><span data-stu-id="dad70-158">The `MyClass` keyword behaves like an object variable that refers to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="dad70-159">`MyClass` benzer `Me`, ancak her yöntem ve özellik arama üzerinde `MyClass` yöntemi veya özelliği gibi davranılır [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md).</span><span class="sxs-lookup"><span data-stu-id="dad70-159">`MyClass` resembles `Me`, but every method and property call on `MyClass` is treated as if the method or property were [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md).</span></span> <span data-ttu-id="dad70-160">Bu nedenle, yöntemi veya özelliği türetilen bir sınıfta geçersiz kılarak etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="dad70-160">Therefore, the method or property is not affected by overriding in a derived class.</span></span>  
  
- <span data-ttu-id="dad70-161">`MyClass` gerçek bir nesne bir anahtar sözcüktür.</span><span class="sxs-lookup"><span data-stu-id="dad70-161">`MyClass` is a keyword, not a real object.</span></span> <span data-ttu-id="dad70-162">`MyClass` bir değişkene atanamaz, yordamlara geçirilen veya kullanılan bir `Is` karşılaştırma.</span><span class="sxs-lookup"><span data-stu-id="dad70-162">`MyClass` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>  
  
- <span data-ttu-id="dad70-163">`MyClass` kapsayan sınıfı ve devralınan üyeleri ifade eder.</span><span class="sxs-lookup"><span data-stu-id="dad70-163">`MyClass` refers to the containing class and its inherited members.</span></span>  
  
- <span data-ttu-id="dad70-164">`MyClass` için bir niteleyici olarak kullanılabilir `Shared` üyeleri.</span><span class="sxs-lookup"><span data-stu-id="dad70-164">`MyClass` can be used as a qualifier for `Shared` members.</span></span>  
  
- <span data-ttu-id="dad70-165">`MyClass` içinde kullanılamaz bir `Shared` yöntemi, ancak bir sınıfın paylaşılan bir üyesine erişmek için bir örnek yöntemi içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dad70-165">`MyClass` cannot be used inside a `Shared` method, but can be used inside an instance method to access a shared member of a class.</span></span>  
  
- <span data-ttu-id="dad70-166">`MyClass` Standart modüllerinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="dad70-166">`MyClass` cannot be used in standard modules.</span></span>  
  
- <span data-ttu-id="dad70-167">`MyClass` bir temel sınıfta tanımlanan ve bu sınıfı sağlanan yöntem uygulaması olmayan bir yöntem nitelemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dad70-167">`MyClass` can be used to qualify a method that is defined in a base class and that has no implementation of the method provided in that class.</span></span> <span data-ttu-id="dad70-168">Böyle bir başvuruya sahip aynı anlamı `MyBase.` *yöntemi*.</span><span class="sxs-lookup"><span data-stu-id="dad70-168">Such a reference has the same meaning as `MyBase.`*Method*.</span></span>  
  
 <span data-ttu-id="dad70-169">Aşağıdaki örnek `Me` ve `MyClass`.</span><span class="sxs-lookup"><span data-stu-id="dad70-169">The following example compares `Me` and `MyClass`.</span></span>  
  
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
  
 <span data-ttu-id="dad70-170">Olsa da `derivedClass` geçersiz kılmalar `testMethod`, `MyClass` anahtar sözcüğünü `useMyClass` temel sınıf sürümü çağrısına geçersiz kılma ve derleyici çözümler etkilerini nullifies `testMethod`.</span><span class="sxs-lookup"><span data-stu-id="dad70-170">Even though `derivedClass` overrides `testMethod`, the `MyClass` keyword in `useMyClass` nullifies the effects of overriding, and the compiler resolves the call to the base class version of `testMethod`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dad70-171">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dad70-171">See also</span></span>

- [<span data-ttu-id="dad70-172">Inherits Deyimi</span><span class="sxs-lookup"><span data-stu-id="dad70-172">Inherits Statement</span></span>](../../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="dad70-173">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="dad70-173">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
