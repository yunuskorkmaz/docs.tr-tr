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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350829"
---
# <a name="inheritance-basics-visual-basic"></a>Devralma Temelleri (Visual Basic)

`Inherits` deyimleri, bir *temel sınıf*olarak bilinen mevcut bir sınıfa göre *türetilmiş sınıf*olarak adlandırılan yeni bir sınıfı bildirmek için kullanılır. Türetilmiş sınıflar devralınır ve temel sınıfta tanımlanan özellikleri, yöntemleri, olayları, alanları ve sabitleri genişletebilir. Aşağıdaki bölümde, devralma için bazı kurallar ve sınıfların devralınması veya Devralındığı şekilde değiştirmek için kullanabileceğiniz değiştiriciler açıklanmaktadır:

- Varsayılan olarak, `NotInheritable` anahtar sözcüğüyle işaretlenmedikçe tüm sınıflar devralınabilir. Sınıflar, projenizdeki diğer sınıflardan veya projenizin başvurduğu diğer derlemelerin sınıflarından devralınabilir.

- Birden çok devralmaya izin veren dillerden farklı olarak Visual Basic sınıflarda yalnızca tekli devralmaya izin verir; diğer bir deyişle, türetilmiş sınıfların yalnızca bir taban sınıfı olabilir. Sınıflarda birden çok devralmaya izin verilmese de sınıflar, aynı uçları etkin bir şekilde gerçekleştirebilen birden çok arabirim uygulayabilir.

- Bir temel sınıfta kısıtlı öğelerin sunulmasını engellemek için, türetilmiş bir sınıfın erişim türü, taban sınıfına eşit veya daha kısıtlayıcı olmalıdır. Örneğin, bir `Public` sınıfı bir `Friend` veya `Private` sınıfı alamaz ve bir `Friend` sınıfı `Private` sınıfını alamaz.

## <a name="inheritance-modifiers"></a>Devralma değiştiricileri

Visual Basic devralmayı desteklemek için aşağıdaki sınıf düzeyi deyimleri ve değiştiricilerini tanıtır:

- `Inherits` ifade — temel sınıfı belirtir.

- `NotInheritable` değiştirici — programcıların sınıfı temel sınıf olarak kullanmasını engeller.

- `MustInherit` değiştirici — sınıfın yalnızca temel sınıf olarak kullanılması amaçlandığını belirtir. `MustInherit` sınıflarının örnekleri doğrudan oluşturulamaz; yalnızca türetilmiş bir sınıfın temel sınıf örnekleri olarak oluşturulabilirler. ( C++ Ve C#gibi diğer programlama dilleri, bu tür bir sınıfı anlatmak için *soyut sınıf* terimini kullanır.)

## <a name="overriding-properties-and-methods-in-derived-classes"></a>Türetilmiş sınıflarda özellikleri ve yöntemleri geçersiz kılma

Varsayılan olarak, türetilmiş bir sınıf, temel sınıfından özellikleri ve yöntemleri devralır. Devralınan bir özelliğin veya yöntemin türetilmiş sınıfta farklı davranması gerekiyorsa, *geçersiz kılınabilir*. Diğer bir deyişle, türetilmiş sınıfta yönteminin yeni bir uygulamasını tanımlayabilirsiniz. Özelliklerin ve yöntemlerin nasıl geçersiz kılınabileceğini denetlemek için aşağıdaki değiştiriciler kullanılır:

- `Overridable` — bir sınıftaki özelliğin veya yöntemin türetilmiş bir sınıfta geçersiz kılınmasına Izin verir.

- `Overrides` — temel sınıfta tanımlanan bir `Overridable` özelliğini veya yöntemini geçersiz kılar.

- `NotOverridable` — bir özelliğin veya yöntemin devralan bir sınıfta geçersiz kılınmasını önler. Varsayılan olarak, `Public` Yöntemler `NotOverridable`.

- `MustOverride` — türetilmiş bir sınıfın özelliği veya yöntemi geçersiz kılmasını gerektirir. `MustOverride` anahtar sözcüğü kullanıldığında, yöntem tanımı yalnızca `Sub`, `Function`veya `Property` deyiminden oluşur. Başka hiçbir deyime izin verilmez ve özellikle `End Sub` veya `End Function` deyimi yoktur. `MustOverride` Yöntemler `MustInherit` sınıflarında bildirilmelidir.

Bordroları işlemek için sınıflar tanımlamak istediğinizi varsayalım. Tipik bir hafta için bordroları hesaplayan bir `RunPayroll` yöntemi içeren genel bir `Payroll` sınıfı tanımlayabilirsiniz. Daha sonra `Payroll`, çalışan primi dağıtılırken kullanılabilecek daha özelleştirilmiş bir `BonusPayroll` sınıfı için temel sınıf olarak kullanabilirsiniz.

`BonusPayroll` sınıfı, temel `Payroll` sınıfında tanımlanan `PayEmployee` yöntemini alabilir ve geçersiz kılabilir.

Aşağıdaki örnek, `PayEmployee`devralınmış bir yöntemi geçersiz kılan `BonusPayroll`bir temel sınıf, `Payroll,` ve türetilmiş bir sınıf tanımlar. Bir yordam `RunPayroll`, bir `Payroll` nesnesini ve `BonusPayroll` nesnesini oluşturup her iki nesnenin `PayEmployee` yöntemini yürüten `Pay`bir işleve geçirir.

[!code-vb[VbVbalrOOP#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#28)]

## <a name="the-mybase-keyword"></a>MyBase anahtar sözcüğü

`MyBase` anahtar sözcüğü, sınıfın geçerli örneğinin temel sınıfına başvuran bir nesne değişkeni gibi davranır. `MyBase`, türetilmiş bir sınıfta geçersiz kılınan veya gölgeli temel sınıf üyelerine erişmek için kullanılır. Özellikle, bir temel sınıf oluşturucusunu türetilmiş sınıf oluşturucusundan açıkça çağırmak için `MyBase.New` kullanılır.

Örneğin, temel sınıftan devralınan bir yöntemi geçersiz kılan türetilmiş bir sınıf tasarlamakta olduğunuzu varsayalım. Geçersiz kılınan yöntem, temel sınıfta yöntemi çağırabilir ve döndürülen değeri aşağıdaki kod parçasında gösterildiği gibi değiştirebilir:

[!code-vb[VbVbalrOOP#109](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#109)]

Aşağıdaki listede `MyBase`kullanımı için kısıtlamalar açıklanmaktadır:

- `MyBase`, anlık temel sınıfa ve devralınan üyelerine başvurur. Sınıftaki `Private` üyelere erişmek için kullanılamaz.

- `MyBase` gerçek bir nesne değil, anahtar sözcüktür. `MyBase` bir değişkene atanamaz, yordamlara geçirilemez veya `Is` karşılaştırmayla kullanılamıyor.

- `MyBase` niteleyen yöntemin, anlık temel sınıfta tanımlanması gerekmez; Bunun yerine, dolaylı olarak devralınan bir temel sınıfta tanımlanabilir. `MyBase` uygun bir başvurunun doğru derlenmesi için, bazı temel sınıflar, çağrıda görünen ad ve parametre türleriyle eşleşen bir yöntem içermelidir.

- `MustOverride` temel sınıf yöntemlerini çağırmak için `MyBase` kullanamazsınız.

- `MyBase` kendisini nitelemek için kullanılamaz. Bu nedenle, aşağıdaki kod geçerli değildir:

  `MyBase.MyBase.BtnOK_Click()`

- `MyBase` modüllerde kullanılamaz.

- `MyBase`, temel sınıf farklı bir derlemese `Friend` olarak işaretlenen temel sınıf üyelerine erişmek için kullanılamaz.

Daha fazla bilgi ve diğer bir örnek için bkz. [nasıl yapılır: türetilmiş bir sınıf tarafından gizlenen bir değişkene erişme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).

## <a name="the-myclass-keyword"></a>MyClass anahtar sözcüğü

`MyClass` anahtar sözcüğü, başlangıçta uygulanmış olan bir sınıfın geçerli örneğine başvuran bir nesne değişkeni gibi davranır. `MyClass` benzer `Me`, ancak `MyClass` her yöntem ve özellik çağrısı, yöntem veya özellik [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md)gibi değerlendirilir. Bu nedenle, yöntem veya özellik türetilmiş bir sınıfta geçersiz kılınmadan etkilenmez.

- `MyClass` gerçek bir nesne değil, anahtar sözcüktür. `MyClass` bir değişkene atanamaz, yordamlara geçirilemez veya `Is` karşılaştırmayla kullanılamıyor.

- `MyClass`, kapsayan sınıfa ve devralınan üyelerine başvurur.

- `MyClass`, `Shared` üyeleri için bir niteleyici olarak kullanılabilir.

- `MyClass`, bir `Shared` yöntemi içinde kullanılamaz, ancak bir sınıfın paylaşılan üyesine erişmek için bir örnek yöntemi içinde kullanılabilir.

- `MyClass` standart modüllerde kullanılamaz.

- `MyClass`, temel sınıfta tanımlanan ve bu sınıfta sağlanmış yöntemin uygulanması olmayan bir yöntemi nitelemek için kullanılabilir. Bu tür bir başvuru, `MyBase.`*yöntemiyle*aynı anlama sahiptir.

Aşağıdaki örnek `Me` ve `MyClass`karşılaştırır.

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

`derivedClass` `testMethod`geçersiz kılsa bile, `useMyClass` içindeki `MyClass` anahtar sözcüğü geçersiz kılma etkilerini artırır ve derleyici, `testMethod`temel sınıf sürümüne çağrıyı çözer.

## <a name="see-also"></a>Ayrıca bkz.

- [Inherits Deyimi](../../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Me, My, MyBase ve MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
