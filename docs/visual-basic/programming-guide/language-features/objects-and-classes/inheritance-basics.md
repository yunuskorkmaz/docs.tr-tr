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
# <a name="inheritance-basics-visual-basic"></a>Devralma Temelleri (Visual Basic)

İfade, bir `Inherits` *temel sınıf*olarak bilinen varolan bir sınıfa göre *türetilmiş sınıf*olarak adlandırılan yeni bir sınıf bildirmek için kullanılır. Türetilmiş sınıflar devralınır ve temel sınıfta tanımlanan özellikleri, yöntemleri, olayları, alanları ve sabitleri genişletebilir. Aşağıdaki bölümde, devralma için bazı kurallar ve sınıfların devralınması veya Devralındığı şekilde değiştirmek için kullanabileceğiniz değiştiriciler açıklanmaktadır:

- Varsayılan olarak, anahtar sözcüğüyle işaretlenmedikçe tüm sınıflar devralınabilir `NotInheritable` . Sınıflar, projenizdeki diğer sınıflardan veya projenizin başvurduğu diğer derlemelerin sınıflarından devralınabilir.

- Birden çok devralmaya izin veren dillerden farklı olarak Visual Basic sınıflarda yalnızca tekli devralmaya izin verir; diğer bir deyişle, türetilmiş sınıfların yalnızca bir taban sınıfı olabilir. Sınıflarda birden çok devralmaya izin verilmese de sınıflar, aynı uçları etkin bir şekilde gerçekleştirebilen birden çok arabirim uygulayabilir.

- Bir temel sınıfta kısıtlı öğelerin sunulmasını engellemek için, türetilmiş bir sınıfın erişim türü, taban sınıfına eşit veya daha kısıtlayıcı olmalıdır. Örneğin, bir sınıf `Public` bir `Friend` veya `Private` sınıfını alamaz ve bir sınıf bir `Friend` `Private` sınıfı devralınabilir.

## <a name="inheritance-modifiers"></a>Devralma değiştiricileri

Visual Basic devralmayı desteklemek için aşağıdaki sınıf düzeyi deyimleri ve değiştiricilerini tanıtır:

- `Inherits`ifade — temel sınıfı belirtir.

- `NotInheritable`değiştirici — programcıların sınıfı temel sınıf olarak kullanmasını engeller.

- `MustInherit`değiştirici — sınıfın yalnızca temel sınıf olarak kullanılması amaçlandığını belirtir. Sınıfların örnekleri `MustInherit` doğrudan oluşturulamaz; yalnızca türetilmiş bir sınıfın temel sınıf örnekleri olarak oluşturulabilirler. (C++ ve C# gibi diğer programlama dilleri, bu tür bir sınıfı anlatmak için *soyut sınıf* terimini kullanır.)

## <a name="overriding-properties-and-methods-in-derived-classes"></a>Türetilmiş sınıflarda özellikleri ve yöntemleri geçersiz kılma

Varsayılan olarak, türetilmiş bir sınıf, temel sınıfından özellikleri ve yöntemleri devralır. Devralınan bir özelliğin veya yöntemin türetilmiş sınıfta farklı davranması gerekiyorsa, *geçersiz kılınabilir*. Diğer bir deyişle, türetilmiş sınıfta yönteminin yeni bir uygulamasını tanımlayabilirsiniz. Özelliklerin ve yöntemlerin nasıl geçersiz kılınabileceğini denetlemek için aşağıdaki değiştiriciler kullanılır:

- `Overridable`— Bir sınıftaki özelliğin veya yöntemin türetilmiş bir sınıfta geçersiz kılınmasına izin verir.

- `Overrides`— `Overridable` Temel sınıfta tanımlanan bir özelliği veya yöntemi geçersiz kılar.

- `NotOverridable`— Bir özelliğin veya yöntemin devralan bir sınıfta geçersiz kılınmasını önler. Varsayılan olarak `Public` Yöntemler `NotOverridable` .

- `MustOverride`— Türetilmiş bir sınıfın özelliği veya yöntemi geçersiz kılmasını gerektirir. `MustOverride`Anahtar sözcüğü kullanıldığında, yöntem tanımı yalnızca `Sub` , `Function` , veya `Property` deyiminden oluşur. Başka hiçbir ifadeye izin verilmez ve özellikle bir `End Sub` veya `End Function` deyimi yoktur. `MustOverride`Yöntemler `MustInherit` sınıflarda bildirilmelidir.

Bordroları işlemek için sınıflar tanımlamak istediğinizi varsayalım. `Payroll` `RunPayroll` Tipik bir hafta için bordroları hesaplayan bir yöntemi içeren genel bir sınıf tanımlayabilirsiniz. `Payroll`Daha sonra `BonusPayroll` , çalışan primi dağıtılırken kullanılabilecek daha özelleştirilmiş bir sınıf için temel sınıf olarak kullanabilirsiniz.

`BonusPayroll`Sınıfı, `PayEmployee` temel sınıfta tanımlanan yöntemi alabilir ve geçersiz kılabilir `Payroll` .

Aşağıdaki örnek, bir temel sınıfı `Payroll,` ve devralınmış bir yöntemi geçersiz kılan türetilmiş bir sınıfı tanımlar `BonusPayroll` `PayEmployee` . Bir yordam,, her iki nesnenin yöntemini çalıştıran bir `RunPayroll` işleve bir nesne ve bir nesnesi oluşturur ve geçirir `Payroll` `BonusPayroll` `Pay` `PayEmployee` .

[!code-vb[VbVbalrOOP#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#28)]

## <a name="the-mybase-keyword"></a>MyBase anahtar sözcüğü

`MyBase`Anahtar sözcüğü, sınıfın geçerli örneğinin temel sınıfına başvuran bir nesne değişkeni gibi davranır. `MyBase`, türetilmiş bir sınıfta geçersiz kılınan veya gölgeli temel sınıf üyelerine erişmek için sık kullanılır. Özellikle, `MyBase.New` türetilmiş bir sınıf oluşturucusundan bir temel sınıf oluşturucusunu açıkça çağırmak için kullanılır.

Örneğin, temel sınıftan devralınan bir yöntemi geçersiz kılan türetilmiş bir sınıf tasarlamakta olduğunuzu varsayalım. Geçersiz kılınan yöntem, temel sınıfta yöntemi çağırabilir ve döndürülen değeri aşağıdaki kod parçasında gösterildiği gibi değiştirebilir:

[!code-vb[VbVbalrOOP#109](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#109)]

Aşağıdaki listede, kullanma kısıtlamaları açıklanmaktadır `MyBase` :

- `MyBase`en hızlı temel sınıfa ve devralınan üyelerine başvurur. Sınıftaki üyelere erişmek için kullanılamaz `Private` .

- `MyBase`, gerçek bir nesne değil, bir anahtar sözcüktür. `MyBase`bir değişkene atanamaz, yordamlara geçirilemez veya bir `Is` karşılaştırmada kullanılamaz.

- `MyBase`Niteleyen yöntemin, anlık temel sınıfta tanımlanması gerekmez; bunun yerine dolaylı olarak devralınan bir temel sınıfta tanımlanabilir. Bir başvurunun `MyBase` doğru bir şekilde derlenmesi için, bazı temel sınıflar, çağrıda görünen ad ve parametre türleriyle eşleşen bir yöntem içermelidir.

- `MyBase` `MustOverride` Temel sınıf yöntemlerini çağırmak için kullanamazsınız.

- `MyBase`kendisini nitelemek için kullanılamaz. Bu nedenle, aşağıdaki kod geçerli değildir:

  `MyBase.MyBase.BtnOK_Click()`

- `MyBase`modüllerde kullanılamaz.

- `MyBase``Friend`temel sınıf farklı bir derlemede yer alıyorsa olarak işaretlenen temel sınıf üyelerine erişmek için kullanılamaz.

Daha fazla bilgi ve diğer bir örnek için bkz. [nasıl yapılır: türetilmiş bir sınıf tarafından gizlenen bir değişkene erişme](../declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).

## <a name="the-myclass-keyword"></a>MyClass anahtar sözcüğü

`MyClass`Anahtar sözcüğü, başlangıçta uygulanmış olan bir sınıfın geçerli örneğine başvuran bir nesne değişkeni gibi davranır. `MyClass`benzerdir `Me` , ancak her yöntem ve özellik çağrısı, `MyClass` Yöntem veya özellik [NotOverridable](../../../language-reference/modifiers/notoverridable.md)gibi değerlendirilir. Bu nedenle, yöntem veya özellik türetilmiş bir sınıfta geçersiz kılınmadan etkilenmez.

- `MyClass`, gerçek bir nesne değil, bir anahtar sözcüktür. `MyClass`bir değişkene atanamaz, yordamlara geçirilemez veya bir `Is` karşılaştırmada kullanılamaz.

- `MyClass`içerilen sınıfa ve devralınan üyelerine başvurur.

- `MyClass`, Üyeler için bir niteleyici olarak kullanılabilir `Shared` .

- `MyClass`bir yöntem içinde kullanılamaz `Shared` , ancak bir sınıfın paylaşılan üyesine erişmek için bir örnek yöntemi içinde kullanılabilir.

- `MyClass`standart modüllerde kullanılamaz.

- `MyClass`, bir temel sınıfta tanımlanan ve bu sınıfta sağlanmış yöntemin uygulanması olmayan bir yöntemi nitelemek için kullanılabilir. Bu tür bir başvuru, yöntemiyle aynı anlama sahiptir `MyBase.` *Method*.

Aşağıdaki örnek `Me` ve ile karşılaştırılır `MyClass` .

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

`derivedClass`Geçersiz kılmalar olsa da `testMethod` , `MyClass` içindeki anahtar sözcüğü `useMyClass` geçersiz kılma etkilerini artırır ve derleyici, öğesinin temel sınıf sürümü çağrısını çözer `testMethod` .

## <a name="see-also"></a>Ayrıca bkz.

- [Inherits Deyimi](../../../language-reference/statements/inherits-statement.md)
- [Me, My, MyBase ve MyClass](../../program-structure/me-my-mybase-and-myclass.md)
