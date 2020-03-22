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
ms.openlocfilehash: 89fcf2a14d8938d536aa72628218242811baa1a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400885"
---
# <a name="inheritance-basics-visual-basic"></a><span data-ttu-id="6c8b8-102">Devralma Temelleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6c8b8-102">Inheritance Basics (Visual Basic)</span></span>

<span data-ttu-id="6c8b8-103">Deyim, *taban sınıf*olarak bilinen varolan bir sınıfa dayalı olarak *türetilmiş sınıf*olarak adlandırılan yeni bir sınıf bildirmek için kullanılır. `Inherits`</span><span class="sxs-lookup"><span data-stu-id="6c8b8-103">The `Inherits` statement is used to declare a new class, called a *derived class*, based on an existing class, known as a *base class*.</span></span> <span data-ttu-id="6c8b8-104">Türetilen sınıflar, taban sınıfta tanımlanan özellikleri, yöntemleri, olayları, alanları ve sabitleri devralır ve genişletebilir.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-104">Derived classes inherit, and can extend, the properties, methods, events, fields, and constants defined in the base class.</span></span> <span data-ttu-id="6c8b8-105">Aşağıdaki bölümde, devralma kurallarının bazıları ve sınıfların devralınması veya devralınması biçimini değiştirmek için kullanabileceğiniz değiştiriciler açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="6c8b8-105">The following section describes some of the rules for inheritance, and the modifiers you can use to change the way classes inherit or are inherited:</span></span>

- <span data-ttu-id="6c8b8-106">Varsayılan olarak, `NotInheritable` anahtar kelimeyle işaretlenmediği sürece tüm sınıflar devralınır.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-106">By default, all classes are inheritable unless marked with the `NotInheritable` keyword.</span></span> <span data-ttu-id="6c8b8-107">Sınıflar, projenizdeki diğer sınıflardan veya projenizin başvurulmugeldiği diğer derlemelerde bulunan sınıflardan devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-107">Classes can inherit from other classes in your project or from classes in other assemblies that your project references.</span></span>

- <span data-ttu-id="6c8b8-108">Birden çok devralmaya izin veren dillerin aksine, Visual Basic sınıflarda yalnızca tek bir devralmaya izin verir; diğer bir tanesi, türetilmiş sınıfların yalnızca bir taban sınıfı olabilir.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-108">Unlike languages that allow multiple inheritance, Visual Basic allows only single inheritance in classes; that is, derived classes can have only one base class.</span></span> <span data-ttu-id="6c8b8-109">Sınıflarda birden çok devralmaya izin verilmese de, sınıflar aynı uçları etkin bir şekilde gerçekleştirebilen birden çok arabirim uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-109">Although multiple inheritance is not allowed in classes, classes can implement multiple interfaces, which can effectively accomplish the same ends.</span></span>

- <span data-ttu-id="6c8b8-110">Bir taban sınıfta kısıtlanmış öğelerin açığa çıkarılmasını önlemek için, türetilmiş bir sınıfın erişim türü taban sınıfına eşit veya daha kısıtlayıcı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-110">To prevent exposing restricted items in a base class, the access type of a derived class must be equal to or more restrictive than its base class.</span></span> <span data-ttu-id="6c8b8-111">Örneğin, bir `Public` sınıf bir `Friend` sınıf `Private` veya bir `Friend` sınıf devralamaz ve bir sınıf bir `Private` sınıf devralamaz.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-111">For example, a `Public` class cannot inherit a `Friend` or a `Private` class, and a `Friend` class cannot inherit a `Private` class.</span></span>

## <a name="inheritance-modifiers"></a><span data-ttu-id="6c8b8-112">Kalıtım Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="6c8b8-112">Inheritance Modifiers</span></span>

<span data-ttu-id="6c8b8-113">Visual Basic, devralmayı desteklemek için aşağıdaki sınıf düzeyindeki deyimleri ve değiştiriciler tanıtır:</span><span class="sxs-lookup"><span data-stu-id="6c8b8-113">Visual Basic introduces the following class-level statements and modifiers to support inheritance:</span></span>

- <span data-ttu-id="6c8b8-114">`Inherits`deyim — Taban sınıfı belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-114">`Inherits` statement — Specifies the base class.</span></span>

- <span data-ttu-id="6c8b8-115">`NotInheritable`değiştirici — Programcıların sınıfı taban sınıf olarak kullanmasını engeller.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-115">`NotInheritable` modifier — Prevents programmers from using the class as a base class.</span></span>

- <span data-ttu-id="6c8b8-116">`MustInherit`değiştirici — Sınıfın yalnızca taban sınıf olarak kullanılmak üzere tasarlandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-116">`MustInherit` modifier — Specifies that the class is intended for use as a base class only.</span></span> <span data-ttu-id="6c8b8-117">`MustInherit` Sınıf örnekleri doğrudan oluşturulamaz; bunlar yalnızca türemiş bir sınıfın taban sınıf örnekleri olarak oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-117">Instances of `MustInherit` classes cannot be created directly; they can only be created as base class instances of a derived class.</span></span> <span data-ttu-id="6c8b8-118">(C++ ve C# gibi diğer programlama dilleri, böyle bir sınıfı tanımlamak için *soyut sınıf* terimini kullanır.)</span><span class="sxs-lookup"><span data-stu-id="6c8b8-118">(Other programming languages, such as C++ and C#, use the term *abstract class* to describe such a class.)</span></span>

## <a name="overriding-properties-and-methods-in-derived-classes"></a><span data-ttu-id="6c8b8-119">Türemiş Sınıflarda Özellikleri ve Yöntemleri Geçersiz Kılma</span><span class="sxs-lookup"><span data-stu-id="6c8b8-119">Overriding Properties and Methods in Derived Classes</span></span>

<span data-ttu-id="6c8b8-120">Varsayılan olarak, türetilmiş bir sınıf özellikleri ve yöntemleri taban sınıfından devralır.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-120">By default, a derived class inherits properties and methods from its base class.</span></span> <span data-ttu-id="6c8b8-121">Devralınan bir özellik veya yöntemtüretilen sınıfta farklı davranması gerekiyorsa *geçersiz kılınabilir.*</span><span class="sxs-lookup"><span data-stu-id="6c8b8-121">If an inherited property or method has to behave differently in the derived class it can be *overridden*.</span></span> <span data-ttu-id="6c8b8-122">Diğer bir deyişle, türemiş sınıfta yöntemin yeni bir uygulama tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-122">That is, you can define a new implementation of the method in the derived class.</span></span> <span data-ttu-id="6c8b8-123">Aşağıdaki değiştiriciler özelliklerin ve yöntemlerin nasıl geçersiz kılındığını denetlemek için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="6c8b8-123">The following modifiers are used to control how properties and methods are overridden:</span></span>

- <span data-ttu-id="6c8b8-124">`Overridable`— Bir sınıftaki bir özelliğin veya yöntemin türetilmiş bir sınıfta geçersiz kılınmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-124">`Overridable` — Allows a property or method in a class to be overridden in a derived class.</span></span>

- <span data-ttu-id="6c8b8-125">`Overrides`— Taban `Overridable` sınıfta tanımlanan bir özelliği veya yöntemi geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-125">`Overrides` — Overrides an `Overridable` property or method defined in the base class.</span></span>

- <span data-ttu-id="6c8b8-126">`NotOverridable`— Bir özelliğin veya yöntemin devralan bir sınıfta geçersiz kılınmasını önler.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-126">`NotOverridable` — Prevents a property or method from being overridden in an inheriting class.</span></span> <span data-ttu-id="6c8b8-127">Varsayılan olarak, `Public` `NotOverridable`yöntemler .</span><span class="sxs-lookup"><span data-stu-id="6c8b8-127">By default, `Public` methods are `NotOverridable`.</span></span>

- <span data-ttu-id="6c8b8-128">`MustOverride`— Türetilmiş bir sınıfın özelliği veya yöntemi geçersiz kılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-128">`MustOverride` — Requires that a derived class override the property or method.</span></span> <span data-ttu-id="6c8b8-129">`MustOverride` Anahtar kelime kullanıldığında, yöntem tanımı yalnızca `Sub`, `Function`veya `Property` deyimi içerir.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-129">When the `MustOverride` keyword is used, the method definition consists of just the `Sub`, `Function`, or `Property` statement.</span></span> <span data-ttu-id="6c8b8-130">Başka hiçbir ifadeye izin verilmez `End Sub` ve `End Function` özellikle hiçbir ifade veya ifade yoktur.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-130">No other statements are allowed, and specifically there is no `End Sub` or `End Function` statement.</span></span> <span data-ttu-id="6c8b8-131">`MustOverride`sınıflarda `MustInherit` yöntemler beyan edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-131">`MustOverride` methods must be declared in `MustInherit` classes.</span></span>

<span data-ttu-id="6c8b8-132">Bordro işlemek için sınıfları tanımlamak istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-132">Suppose you want to define classes to handle payroll.</span></span> <span data-ttu-id="6c8b8-133">Tipik bir hafta `Payroll` için bordro `RunPayroll` hesaplayan bir yöntem içeren genel bir sınıf tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-133">You could define a generic `Payroll` class that contains a `RunPayroll` method that calculates payroll for a typical week.</span></span> <span data-ttu-id="6c8b8-134">Daha sonra, `Payroll` çalışan bonuslarını dağıtırken `BonusPayroll` kullanılabilecek daha özel bir sınıf için taban sınıf olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-134">You could then use `Payroll` as a base class for a more specialized `BonusPayroll` class, which could be used when distributing employee bonuses.</span></span>

<span data-ttu-id="6c8b8-135">Sınıf, `BonusPayroll` taban `PayEmployee` `Payroll` sınıfta tanımlanan yöntemi devralabilir ve geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-135">The `BonusPayroll` class can inherit, and override, the `PayEmployee` method defined in the base `Payroll` class.</span></span>

<span data-ttu-id="6c8b8-136">Aşağıdaki örnekte, `Payroll,` devralınan bir yöntemi geçersiz `BonusPayroll`kılan bir taban sınıf `PayEmployee`ve türetilmiş bir sınıf tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-136">The following example defines a base class, `Payroll,` and a derived class, `BonusPayroll`, which overrides an inherited method, `PayEmployee`.</span></span> <span data-ttu-id="6c8b8-137">Bir `RunPayroll`yordam, oluşturur ve sonra `Payroll` bir `BonusPayroll` nesne ve bir `Pay`nesne bir `PayEmployee` işleve geçer, her iki nesnenin yöntemini yürütür.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-137">A procedure, `RunPayroll`, creates and then passes a `Payroll` object and a `BonusPayroll` object to a function, `Pay`, that executes the `PayEmployee` method of both objects.</span></span>

[!code-vb[VbVbalrOOP#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#28)]

## <a name="the-mybase-keyword"></a><span data-ttu-id="6c8b8-138">MyBase Anahtar Kelime</span><span class="sxs-lookup"><span data-stu-id="6c8b8-138">The MyBase Keyword</span></span>

<span data-ttu-id="6c8b8-139">Anahtar `MyBase` kelime, bir sınıfın geçerli örneğinin taban sınıfına başvuran bir nesne değişkeni gibi olur.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-139">The `MyBase` keyword behaves like an object variable that refers to the base class of the current instance of a class.</span></span> <span data-ttu-id="6c8b8-140">`MyBase`türetilmiş bir sınıfta geçersiz kılınan veya gölgelenen taban sınıf üyelerine erişmek için sıklıkla kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-140">`MyBase` is frequently used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="6c8b8-141">Özellikle, `MyBase.New` türemiş bir sınıf oluşturucudan taban sınıf oluşturucusu çağırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-141">In particular, `MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>

<span data-ttu-id="6c8b8-142">Örneğin, taban sınıftan devralınan bir yöntemi geçersiz kılan türetilmiş bir sınıf tasarladığınızı varsayalım.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-142">For example, suppose you are designing a derived class that overrides a method inherited from the base class.</span></span> <span data-ttu-id="6c8b8-143">Geçersiz kılınan yöntem, yöntemi taban sınıfta arayabilir ve aşağıdaki kod parçasında gösterildiği gibi iade değerini değiştirebilir:</span><span class="sxs-lookup"><span data-stu-id="6c8b8-143">The overridden method can call the method in the base class and modify the return value as shown in the following code fragment:</span></span>

[!code-vb[VbVbalrOOP#109](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#109)]

<span data-ttu-id="6c8b8-144">Aşağıdaki liste, kullanma `MyBase`yla ilgili kısıtlamaları açıklar:</span><span class="sxs-lookup"><span data-stu-id="6c8b8-144">The following list describes restrictions on using `MyBase`:</span></span>

- <span data-ttu-id="6c8b8-145">`MyBase`hemen taban sınıf ve onun devralınan üyeleri anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-145">`MyBase` refers to the immediate base class and its inherited members.</span></span> <span data-ttu-id="6c8b8-146">Sınıftaki üyelere `Private` erişmek için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-146">It cannot be used to access `Private` members in the class.</span></span>

- <span data-ttu-id="6c8b8-147">`MyBase`gerçek bir nesne değil, bir anahtar kelimedir.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-147">`MyBase` is a keyword, not a real object.</span></span> <span data-ttu-id="6c8b8-148">`MyBase`bir değişkene atanamaz, yordamlara geçirilemez `Is` veya bir karşılaştırmada kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-148">`MyBase` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>

- <span data-ttu-id="6c8b8-149">Niteleyen `MyBase` yöntemin hemen taban sınıfta tanımlanması gerekmez; bunun yerine dolaylı olarak devralınan bir taban sınıfta tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-149">The method that `MyBase` qualifies does not have to be defined in the immediate base class; it may instead be defined in an indirectly inherited base class.</span></span> <span data-ttu-id="6c8b8-150">Doğru `MyBase` derlemek için nitelikli bir başvuru için, bazı taban sınıf adı ve çağrıda görünen parametre türleri eşleşen bir yöntem içermelidir.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-150">In order for a reference qualified by `MyBase` to compile correctly, some base class must contain a method matching the name and types of parameters that appear in the call.</span></span>

- <span data-ttu-id="6c8b8-151">Taban sınıf `MyBase` yöntemlerini aramak `MustOverride` için kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-151">You cannot use `MyBase` to call `MustOverride` base class methods.</span></span>

- <span data-ttu-id="6c8b8-152">`MyBase`kendini nitelemek için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-152">`MyBase` cannot be used to qualify itself.</span></span> <span data-ttu-id="6c8b8-153">Bu nedenle, aşağıdaki kod geçerli değildir:</span><span class="sxs-lookup"><span data-stu-id="6c8b8-153">Therefore, the following code is not valid:</span></span>

  `MyBase.MyBase.BtnOK_Click()`

- <span data-ttu-id="6c8b8-154">`MyBase`modüllerde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-154">`MyBase` cannot be used in modules.</span></span>

- <span data-ttu-id="6c8b8-155">`MyBase`taban sınıf farklı bir derlemede gibi `Friend` işaretlenmiş taban sınıf üyelerine erişmek için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-155">`MyBase` cannot be used to access base class members that are marked as `Friend` if the base class is in a different assembly.</span></span>

<span data-ttu-id="6c8b8-156">Daha fazla bilgi ve başka bir örnek için [bkz.](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)</span><span class="sxs-lookup"><span data-stu-id="6c8b8-156">For more information and another example, see [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>

## <a name="the-myclass-keyword"></a><span data-ttu-id="6c8b8-157">MyClass Anahtar Kelime</span><span class="sxs-lookup"><span data-stu-id="6c8b8-157">The MyClass Keyword</span></span>

<span data-ttu-id="6c8b8-158">Anahtar `MyClass` kelime, başlangıçta uygulanan bir sınıfın geçerli örneğini ifade eden bir nesne değişkeni gibi olur.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-158">The `MyClass` keyword behaves like an object variable that refers to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="6c8b8-159">`MyClass`benzer, `Me`ancak her yöntem ve `MyClass` özellik arama yöntem veya özellik [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md)sanki kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-159">`MyClass` resembles `Me`, but every method and property call on `MyClass` is treated as if the method or property were [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md).</span></span> <span data-ttu-id="6c8b8-160">Bu nedenle, yöntem veya özellik türetilmiş bir sınıfta geçersiz kılma etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-160">Therefore, the method or property is not affected by overriding in a derived class.</span></span>

- <span data-ttu-id="6c8b8-161">`MyClass`gerçek bir nesne değil, bir anahtar kelimedir.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-161">`MyClass` is a keyword, not a real object.</span></span> <span data-ttu-id="6c8b8-162">`MyClass`bir değişkene atanamaz, yordamlara geçirilemez `Is` veya bir karşılaştırmada kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-162">`MyClass` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>

- <span data-ttu-id="6c8b8-163">`MyClass`içeren sınıf ve onun devralınan üyeleri anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-163">`MyClass` refers to the containing class and its inherited members.</span></span>

- <span data-ttu-id="6c8b8-164">`MyClass`üyeler için `Shared` bir niteleyici olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-164">`MyClass` can be used as a qualifier for `Shared` members.</span></span>

- <span data-ttu-id="6c8b8-165">`MyClass`bir `Shared` yöntem içinde kullanılamaz, ancak bir sınıfın paylaşılan bir üyesine erişmek için bir örnek yöntemi içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-165">`MyClass` cannot be used inside a `Shared` method, but can be used inside an instance method to access a shared member of a class.</span></span>

- <span data-ttu-id="6c8b8-166">`MyClass`standart modüllerde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-166">`MyClass` cannot be used in standard modules.</span></span>

- <span data-ttu-id="6c8b8-167">`MyClass`taban sınıfta tanımlanan ve bu sınıfta sağlanan yöntemin uygulanması olmayan bir yöntemi nitelemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-167">`MyClass` can be used to qualify a method that is defined in a base class and that has no implementation of the method provided in that class.</span></span> <span data-ttu-id="6c8b8-168">Böyle bir başvuru `MyBase.` *Yöntemi*ile aynı anlama gelir.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-168">Such a reference has the same meaning as `MyBase.`*Method*.</span></span>

<span data-ttu-id="6c8b8-169">Aşağıdaki örnek `Me` karşılaştırır `MyClass`ve .</span><span class="sxs-lookup"><span data-stu-id="6c8b8-169">The following example compares `Me` and `MyClass`.</span></span>

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

<span data-ttu-id="6c8b8-170">Geçersiz `derivedClass` kılar, `testMethod` `MyClass` anahtar `useMyClass` kelime geçersiz kılma nın etkilerini geçersiz kılar ve derleyici çağrıyı `testMethod`'un taban sınıf sürümüne giderir.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-170">Even though `derivedClass` overrides `testMethod`, the `MyClass` keyword in `useMyClass` nullifies the effects of overriding, and the compiler resolves the call to the base class version of `testMethod`.</span></span>

## <a name="see-also"></a><span data-ttu-id="6c8b8-171">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c8b8-171">See also</span></span>

- [<span data-ttu-id="6c8b8-172">Inherits Deyimi</span><span class="sxs-lookup"><span data-stu-id="6c8b8-172">Inherits Statement</span></span>](../../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="6c8b8-173">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="6c8b8-173">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
