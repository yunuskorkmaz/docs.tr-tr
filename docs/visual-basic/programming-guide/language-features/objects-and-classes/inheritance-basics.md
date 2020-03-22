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
# <a name="inheritance-basics-visual-basic"></a>Devralma Temelleri (Visual Basic)

Deyim, *taban sınıf*olarak bilinen varolan bir sınıfa dayalı olarak *türetilmiş sınıf*olarak adlandırılan yeni bir sınıf bildirmek için kullanılır. `Inherits` Türetilen sınıflar, taban sınıfta tanımlanan özellikleri, yöntemleri, olayları, alanları ve sabitleri devralır ve genişletebilir. Aşağıdaki bölümde, devralma kurallarının bazıları ve sınıfların devralınması veya devralınması biçimini değiştirmek için kullanabileceğiniz değiştiriciler açıklanmaktadır:

- Varsayılan olarak, `NotInheritable` anahtar kelimeyle işaretlenmediği sürece tüm sınıflar devralınır. Sınıflar, projenizdeki diğer sınıflardan veya projenizin başvurulmugeldiği diğer derlemelerde bulunan sınıflardan devralınabilir.

- Birden çok devralmaya izin veren dillerin aksine, Visual Basic sınıflarda yalnızca tek bir devralmaya izin verir; diğer bir tanesi, türetilmiş sınıfların yalnızca bir taban sınıfı olabilir. Sınıflarda birden çok devralmaya izin verilmese de, sınıflar aynı uçları etkin bir şekilde gerçekleştirebilen birden çok arabirim uygulayabilir.

- Bir taban sınıfta kısıtlanmış öğelerin açığa çıkarılmasını önlemek için, türetilmiş bir sınıfın erişim türü taban sınıfına eşit veya daha kısıtlayıcı olmalıdır. Örneğin, bir `Public` sınıf bir `Friend` sınıf `Private` veya bir `Friend` sınıf devralamaz ve bir sınıf bir `Private` sınıf devralamaz.

## <a name="inheritance-modifiers"></a>Kalıtım Değiştiriciler

Visual Basic, devralmayı desteklemek için aşağıdaki sınıf düzeyindeki deyimleri ve değiştiriciler tanıtır:

- `Inherits`deyim — Taban sınıfı belirtir.

- `NotInheritable`değiştirici — Programcıların sınıfı taban sınıf olarak kullanmasını engeller.

- `MustInherit`değiştirici — Sınıfın yalnızca taban sınıf olarak kullanılmak üzere tasarlandığını belirtir. `MustInherit` Sınıf örnekleri doğrudan oluşturulamaz; bunlar yalnızca türemiş bir sınıfın taban sınıf örnekleri olarak oluşturulabilir. (C++ ve C# gibi diğer programlama dilleri, böyle bir sınıfı tanımlamak için *soyut sınıf* terimini kullanır.)

## <a name="overriding-properties-and-methods-in-derived-classes"></a>Türemiş Sınıflarda Özellikleri ve Yöntemleri Geçersiz Kılma

Varsayılan olarak, türetilmiş bir sınıf özellikleri ve yöntemleri taban sınıfından devralır. Devralınan bir özellik veya yöntemtüretilen sınıfta farklı davranması gerekiyorsa *geçersiz kılınabilir.* Diğer bir deyişle, türemiş sınıfta yöntemin yeni bir uygulama tanımlayabilirsiniz. Aşağıdaki değiştiriciler özelliklerin ve yöntemlerin nasıl geçersiz kılındığını denetlemek için kullanılır:

- `Overridable`— Bir sınıftaki bir özelliğin veya yöntemin türetilmiş bir sınıfta geçersiz kılınmasına izin verir.

- `Overrides`— Taban `Overridable` sınıfta tanımlanan bir özelliği veya yöntemi geçersiz kılar.

- `NotOverridable`— Bir özelliğin veya yöntemin devralan bir sınıfta geçersiz kılınmasını önler. Varsayılan olarak, `Public` `NotOverridable`yöntemler .

- `MustOverride`— Türetilmiş bir sınıfın özelliği veya yöntemi geçersiz kılmasını gerektirir. `MustOverride` Anahtar kelime kullanıldığında, yöntem tanımı yalnızca `Sub`, `Function`veya `Property` deyimi içerir. Başka hiçbir ifadeye izin verilmez `End Sub` ve `End Function` özellikle hiçbir ifade veya ifade yoktur. `MustOverride`sınıflarda `MustInherit` yöntemler beyan edilmelidir.

Bordro işlemek için sınıfları tanımlamak istediğinizi varsayalım. Tipik bir hafta `Payroll` için bordro `RunPayroll` hesaplayan bir yöntem içeren genel bir sınıf tanımlayabilirsiniz. Daha sonra, `Payroll` çalışan bonuslarını dağıtırken `BonusPayroll` kullanılabilecek daha özel bir sınıf için taban sınıf olarak kullanabilirsiniz.

Sınıf, `BonusPayroll` taban `PayEmployee` `Payroll` sınıfta tanımlanan yöntemi devralabilir ve geçersiz kılabilir.

Aşağıdaki örnekte, `Payroll,` devralınan bir yöntemi geçersiz `BonusPayroll`kılan bir taban sınıf `PayEmployee`ve türetilmiş bir sınıf tanımlanır. Bir `RunPayroll`yordam, oluşturur ve sonra `Payroll` bir `BonusPayroll` nesne ve bir `Pay`nesne bir `PayEmployee` işleve geçer, her iki nesnenin yöntemini yürütür.

[!code-vb[VbVbalrOOP#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#28)]

## <a name="the-mybase-keyword"></a>MyBase Anahtar Kelime

Anahtar `MyBase` kelime, bir sınıfın geçerli örneğinin taban sınıfına başvuran bir nesne değişkeni gibi olur. `MyBase`türetilmiş bir sınıfta geçersiz kılınan veya gölgelenen taban sınıf üyelerine erişmek için sıklıkla kullanılır. Özellikle, `MyBase.New` türemiş bir sınıf oluşturucudan taban sınıf oluşturucusu çağırmak için kullanılır.

Örneğin, taban sınıftan devralınan bir yöntemi geçersiz kılan türetilmiş bir sınıf tasarladığınızı varsayalım. Geçersiz kılınan yöntem, yöntemi taban sınıfta arayabilir ve aşağıdaki kod parçasında gösterildiği gibi iade değerini değiştirebilir:

[!code-vb[VbVbalrOOP#109](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#109)]

Aşağıdaki liste, kullanma `MyBase`yla ilgili kısıtlamaları açıklar:

- `MyBase`hemen taban sınıf ve onun devralınan üyeleri anlamına gelir. Sınıftaki üyelere `Private` erişmek için kullanılamaz.

- `MyBase`gerçek bir nesne değil, bir anahtar kelimedir. `MyBase`bir değişkene atanamaz, yordamlara geçirilemez `Is` veya bir karşılaştırmada kullanılamaz.

- Niteleyen `MyBase` yöntemin hemen taban sınıfta tanımlanması gerekmez; bunun yerine dolaylı olarak devralınan bir taban sınıfta tanımlanabilir. Doğru `MyBase` derlemek için nitelikli bir başvuru için, bazı taban sınıf adı ve çağrıda görünen parametre türleri eşleşen bir yöntem içermelidir.

- Taban sınıf `MyBase` yöntemlerini aramak `MustOverride` için kullanamazsınız.

- `MyBase`kendini nitelemek için kullanılamaz. Bu nedenle, aşağıdaki kod geçerli değildir:

  `MyBase.MyBase.BtnOK_Click()`

- `MyBase`modüllerde kullanılamaz.

- `MyBase`taban sınıf farklı bir derlemede gibi `Friend` işaretlenmiş taban sınıf üyelerine erişmek için kullanılamaz.

Daha fazla bilgi ve başka bir örnek için [bkz.](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)

## <a name="the-myclass-keyword"></a>MyClass Anahtar Kelime

Anahtar `MyClass` kelime, başlangıçta uygulanan bir sınıfın geçerli örneğini ifade eden bir nesne değişkeni gibi olur. `MyClass`benzer, `Me`ancak her yöntem ve `MyClass` özellik arama yöntem veya özellik [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md)sanki kabul edilir. Bu nedenle, yöntem veya özellik türetilmiş bir sınıfta geçersiz kılma etkilenmez.

- `MyClass`gerçek bir nesne değil, bir anahtar kelimedir. `MyClass`bir değişkene atanamaz, yordamlara geçirilemez `Is` veya bir karşılaştırmada kullanılamaz.

- `MyClass`içeren sınıf ve onun devralınan üyeleri anlamına gelir.

- `MyClass`üyeler için `Shared` bir niteleyici olarak kullanılabilir.

- `MyClass`bir `Shared` yöntem içinde kullanılamaz, ancak bir sınıfın paylaşılan bir üyesine erişmek için bir örnek yöntemi içinde kullanılabilir.

- `MyClass`standart modüllerde kullanılamaz.

- `MyClass`taban sınıfta tanımlanan ve bu sınıfta sağlanan yöntemin uygulanması olmayan bir yöntemi nitelemek için kullanılabilir. Böyle bir başvuru `MyBase.` *Yöntemi*ile aynı anlama gelir.

Aşağıdaki örnek `Me` karşılaştırır `MyClass`ve .

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

Geçersiz `derivedClass` kılar, `testMethod` `MyClass` anahtar `useMyClass` kelime geçersiz kılma nın etkilerini geçersiz kılar ve derleyici çağrıyı `testMethod`'un taban sınıf sürümüne giderir.

## <a name="see-also"></a>Ayrıca bkz.

- [Inherits Deyimi](../../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Me, My, MyBase ve MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
