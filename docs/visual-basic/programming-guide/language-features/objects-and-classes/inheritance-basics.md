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
# <a name="inheritance-basics-visual-basic"></a>Devralma Temelleri (Visual Basic)
`Inherits` Deyimi adlı yeni bir sınıf bildirmek için kullanılır bir *türetilmiş sınıf*olarak bilinen varolan bir sınıfa göre bir *temel sınıfı*. Türetilmiş sınıflarda devralınır ve genişletebilir, özellikleri, yöntemleri, olaylar, alanları ve temel sınıfta tanımlı sabitler. Aşağıdaki bölümde bazı devralma kuralları açıklar ve yol sınıflarını değiştirmek için kullanabileceğiniz değiştiricileri devralmıyor veya devralınan:  
  
- Varsayılan olarak, tüm sınıflar ile işaretlenen sürece devralınabilir `NotInheritable` anahtar sözcüğü. Sınıflar, projenizdeki diğer sınıfları veya projenizin başvurduğu diğer derlemeleri sınıflarda devralabilir.  
  
- Birden çok devralma izin dillerden farklı olarak, Visual Basic, yalnızca tek devralma sınıfları sağlar; diğer bir deyişle, türetilmiş sınıflarda yalnızca bir temel sınıf olabilir. Birden çok devralma sınıfları izin verilmez ancak sınıfları aynı uçları etkili bir şekilde gerçekleştirebileceğiniz birden çok arabirim uygulayabilir.  
  
- Bir temel sınıf kısıtlı öğelerini açığa çıkarılmasını önlemek için eşit veya daha kısıtlayıcı onun temel sınıfından türetilmiş bir sınıfın erişim türü olmalıdır. Örneğin, bir `Public` sınıfı devralamaz bir `Friend` veya `Private` sınıfı ve `Friend` sınıfı devralamaz bir `Private` sınıfı.  
  
## <a name="inheritance-modifiers"></a>Devralma değiştiriciler  
 Visual Basic, aşağıdaki sınıf düzeyi ifadeleri ve devralma desteklemek için değiştiriciler sunar:  
  
- `Inherits` deyimi — temel sınıfını belirtir.  
  
- `NotInheritable` değiştiricisi — programcıları, sınıfın temel sınıf olarak kullanmasını önler.  
  
- `MustInherit` değiştiricisi — sınıf yalnızca temel sınıf olarak kullanılmak üzere tasarlanmıştır belirtir. Örneklerini `MustInherit` sınıfları doğrudan oluşturulamıyor; bunlar yalnızca türetilmiş bir sınıf olarak taban sınıf örneklerinin oluşturulabilir. (C++ gibi diğer programlama dilleri ve C#, terim kullanın *soyut sınıf* gibi bir sınıf tanımlamak için.)  
  
## <a name="overriding-properties-and-methods-in-derived-classes"></a>Geçersiz kılma özellikleri ve yöntemleri türetilmiş sınıflarda  
 Varsayılan olarak, özellik ve yöntem türetilmiş bir sınıf kendi temel sınıfından devralır. Bir devralınan özellik veya yöntem türetilmiş bir sınıf içindeki farklı davrandığını varsa olabilir *geçersiz kılınan*. Diğer bir deyişle, türetilmiş bir sınıf içindeki yöntemin yeni bir uygulamasını tanımlayabilirsiniz. Özellikleri ve yöntemleri nasıl geçersiz kılınacağını denetlemek için aşağıdaki değiştiriciler kullanılır:  
  
- `Overridable` — Türetilen bir sınıfta geçersiz kılınacak bir sınıftaki bir özellik veya yöntem sağlar.  
  
- `Overrides` — Geçersiz kılar bir `Overridable` özellik veya yöntem temel sınıfta tanımlanmış.  
  
- `NotOverridable` — Türetilen bir sınıfta geçersiz kılınan bir özellik veya yöntem engeller. Varsayılan olarak, `Public` yöntemler `NotOverridable`.  
  
- `MustOverride` — Bir türetilen sınıf özelliği veya yöntemi geçersiz gerektirir. Zaman `MustOverride` anahtar sözcüğü kullanılır, yöntem tanımını oluşan yalnızca `Sub`, `Function`, veya `Property` deyimi. Diğer bir deyimlerine izin ve özellikle yoktur hiçbir `End Sub` veya `End Function` deyimi. `MustOverride` yöntem içinde bildirilmesi gerekir `MustInherit` sınıfları.  
  
 Bordro işlemek için sınıflar tanımlamak istediğinizi varsayalım. Genel tanımlayabilirsiniz `Payroll` içeren sınıf bir `RunPayroll` için tipik bir haftada bir bordro hesaplar yöntemi. Ardından kullanabileceğinizi `Payroll` bir temel sınıf için daha özel olarak `BonusPayroll` çalışan ikramiyeler dağıtırken kullanılabilen sınıfı.  
  
 `BonusPayroll` Sınıf devralma ve geçersiz kılmak, `PayEmployee` temel içinde tanımlanan yöntem `Payroll` sınıfı.  
  
 Aşağıdaki örnek, bir temel sınıf tanımlar `Payroll,` ve türetilmiş bir sınıf `BonusPayroll`, devralınan bir yöntemi geçersiz kılmalar `PayEmployee`. Yordamı, bir `RunPayroll`oluşturur ve sonra geçen bir `Payroll` nesne ve bir `BonusPayroll` bir işlev nesnesine `Pay`, yürütür `PayEmployee` her iki nesnenin yöntemi.  
  
 [!code-vb[VbVbalrOOP#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#28)]  
  
## <a name="the-mybase-keyword"></a>MyBase anahtar sözcüğü  
 `MyBase` Anahtar sözcüğü davranacağını gibi geçerli bir sınıf örneğinin temel sınıfına başvuran bir nesne değişkeni. `MyBase` sık sık geçersiz kılınan ya da türetilen bir sınıfta gölgeli bir temel sınıf üyelerinin erişmek için kullanılır. Özellikle, `MyBase.New` bir temel sınıf oluşturucusu bir türetilmiş sınıf oluşturucusunda açıkça çağırmak için kullanılır.  
  
 Örneğin, temel sınıftan devralınan bir yöntemi geçersiz kılan türetilmiş bir sınıf tasarlarken varsayalım. Geçersiz kılınan yöntemi, temel sınıf yöntemini çağırın ve dönüş değeri aşağıdaki kod parçasını gösterildiği gibi değiştirin:  
  
 [!code-vb[VbVbalrOOP#109](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#109)]  
  
 Aşağıdaki listede kullanarak kısıtlamaları açıklamaktadır. `MyBase`:  
  
- `MyBase` hemen bir temel sınıf ve devralınan üyeleri ifade eder. Kullanılamaz erişimi `Private` sınıftaki üyeleri.  
  
- `MyBase` gerçek bir nesne bir anahtar sözcüktür. `MyBase` bir değişkene atanamaz, yordamlara geçirilen veya kullanılan bir `Is` karşılaştırma.  
  
- Yöntemi, `MyBase` niteleyen hemen temel sınıfta tanımlanmış olması gerekmez bunun yerine bir dolaylı olarak devralınan taban sınıf içinde tanımlanabilir. Nitelenen başvuru için sırayla `MyBase` doğru şekilde derlenmesi için bazı temel sınıf adını ve çağrıda görünen parametre türleri ile eşleşen bir yöntem içermelidir.  
  
- Kullanamazsınız `MyBase` çağrılacak `MustOverride` temel sınıf yöntemleri.  
  
- `MyBase` kendisini nitelemek için kullanılamaz. Bu nedenle, aşağıdaki kodu geçerli değil:  
  
     `MyBase.MyBase.BtnOK_Click()`  
  
- `MyBase` modüllerinde kullanılamaz.  
  
- `MyBase` olarak işaretlenmiş temel sınıfın üyelerine erişmek için kullanılamaz `Friend` temel sınıf içinde farklı bir derleme ise.  
  
 Daha fazla bilgi ve başka bir örnek için bkz: [nasıl yapılır: Türetilmiş sınıf tarafından gizlenen bir değişkene erişme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).  
  
## <a name="the-myclass-keyword"></a>MyClass anahtar sözcüğü  
 `MyClass` Anahtar sözcüğü davranacağını gibi bir nesne değişkeni özgün olarak uygulandığı bir sınıfın geçerli örneğine başvurur. `MyClass` benzer `Me`, ancak her yöntem ve özellik arama üzerinde `MyClass` yöntemi veya özelliği gibi davranılır [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md). Bu nedenle, yöntemi veya özelliği türetilen bir sınıfta geçersiz kılarak etkilenmez.  
  
- `MyClass` gerçek bir nesne bir anahtar sözcüktür. `MyClass` bir değişkene atanamaz, yordamlara geçirilen veya kullanılan bir `Is` karşılaştırma.  
  
- `MyClass` kapsayan sınıfı ve devralınan üyeleri ifade eder.  
  
- `MyClass` için bir niteleyici olarak kullanılabilir `Shared` üyeleri.  
  
- `MyClass` içinde kullanılamaz bir `Shared` yöntemi, ancak bir sınıfın paylaşılan bir üyesine erişmek için bir örnek yöntemi içinde kullanılabilir.  
  
- `MyClass` Standart modüllerinde kullanılamaz.  
  
- `MyClass` bir temel sınıfta tanımlanan ve bu sınıfı sağlanan yöntem uygulaması olmayan bir yöntem nitelemek için kullanılabilir. Böyle bir başvuruya sahip aynı anlamı `MyBase.` *yöntemi*.  
  
 Aşağıdaki örnek `Me` ve `MyClass`.  
  
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
  
 Olsa da `derivedClass` geçersiz kılmalar `testMethod`, `MyClass` anahtar sözcüğünü `useMyClass` temel sınıf sürümü çağrısına geçersiz kılma ve derleyici çözümler etkilerini nullifies `testMethod`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Inherits Deyimi](../../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Me, My, MyBase ve MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
