---
title: Devralma Temelleri (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 76813bb36c0bcf75791932a0fec081f0fc1958e3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="inheritance-basics-visual-basic"></a>Devralma Temelleri (Visual Basic)
`Inherits` Deyimi adında yeni bir sınıf bildirmek için kullanılan bir *türetilmiş sınıf*, olarak bilinen varolan bir sınıfa göre bir *temel sınıfı*. Türetilen sınıflar devralır ve genişletebilir, özellikleri, yöntemleri, olayları, alanları ve taban sınıf içinde tanımlı sabitler. Aşağıdaki bölümde devralma kurallarını bazıları açıklanır ve yol sınıflarını değiştirmek için kullanabileceğiniz değiştiriciler devralır veya devralınan:  
  
-   Varsayılan olarak, tüm sınıflar ile işaretlenen sürece devralınabilir `NotInheritable` anahtar sözcüğü. Sınıfları projenizdeki diğer sınıflardan veya projenizin başvuran diğer derlemelerde sınıflardan devralabilirsiniz.  
  
-   Birden çok devralma izin dilleri aksine [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] sınıflarda; yalnızca tek devralma verir türetilen sınıflar yalnızca bir temel sınıf başka bir deyişle, olabilir. Birden çok devralma sınıflarda izin verilmez ancak sınıflar aynı uçları etkili bir şekilde gerçekleştirebilirsiniz birden çok arabirimleri uygulayabilir.  
  
-   Bir taban sınıf kısıtlı öğelerde gösterilmesini önlemek için türetilmiş bir sınıf erişim türünü eşit veya onun temel sınıfı daha kısıtlayıcı olması gerekir. Örneğin, bir `Public` olamaz sınıf devralma bir `Friend` veya `Private` sınıfı ve bir `Friend` olamaz sınıf devralma bir `Private` sınıfı.  
  
## <a name="inheritance-modifiers"></a>Devralma değiştiricileri  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]Aşağıdaki sınıf düzeyi ifadeleri ve devralma desteklemek için değiştiricileri sunar:  
  
-   `Inherits`deyimi — temel sınıfı belirtir.  
  
-   `NotInheritable`Değiştirici — programcıları sınıfın temel sınıf olarak kullanmalarını engeller.  
  
-   `MustInherit`Değiştirici — sınıfı yalnızca temel sınıf olarak kullanılmak üzere tasarlanmıştır belirtir. Örneklerini `MustInherit` sınıfları doğrudan oluşturulamıyor; bunlar yalnızca türetilmiş bir sınıf olarak temel sınıf örneklerinin oluşturulabilir. (C++ ve C# gibi diğer programlama dilleri terim kullanın *soyut sınıf* böyle bir sınıfın açıklamak için.)  
  
## <a name="overriding-properties-and-methods-in-derived-classes"></a>Geçersiz kılma özellikleri ve yöntemleri türetilmiş sınıflarda  
 Varsayılan olarak, türetilmiş bir sınıf kendi temel sınıfından özellikleri ve yöntemleri devralır. Devralınan özellik veya yöntem türetilen sınıfta farklı şekilde davranmasına içeriyorsa olabilir *geçersiz*. Diğer bir deyişle, yeni bir uygulama yönteminin türetilen sınıfta tanımlayabilirsiniz. Aşağıdaki değiştiricileri özellikleri ve yöntemleri nasıl geçersiz kılınır denetlemek için kullanılır:  
  
-   `Overridable`— Türetilen bir sınıfta geçersiz kılınmak üzere bir sınıfta bir özellik veya yöntem sağlar.  
  
-   `Overrides`— Geçersiz kılar bir `Overridable` özellik veya yöntem temel sınıfında tanımlanır.  
  
-   `NotOverridable`— Türetilen bir sınıfta geçersiz bir özellik veya yöntem engeller. Varsayılan olarak, `Public` yöntemleri `NotOverridable`.  
  
-   `MustOverride`— Türetilmiş bir sınıf özellik veya yöntem geçersiz gerektirir. Zaman `MustOverride` anahtar sözcüğü kullanılır, yöntem tanımı oluşan yalnızca `Sub`, `Function`, veya `Property` deyimi. Diğer bir deyime izin ve özellikle olmadığından hiçbir `End Sub` veya `End Function` deyimi. `MustOverride`yöntemleri bildirilmelidir `MustInherit` sınıfları.  
  
 Bordro işlemek için sınıflar tanımlamak istediğinizi varsayalım. Genel tanımlayabilirsiniz `Payroll` içeren sınıf bir `RunPayroll` için tipik bir hafta Bordro hesaplar yöntemi. Daha sonra kullanabilirsiniz `Payroll` daha özelleştirilmiş için temel sınıf olarak `BonusPayroll` çalışan ikramiyeler dağıtırken kullanılabilir sınıfı.  
  
 `BonusPayroll` Sınıfı devralır ve geçersiz kılma, `PayEmployee` Bankası'nda tanımlanan yöntemi `Payroll` sınıfı.  
  
 Aşağıdaki örnek, bir temel sınıf tanımlar `Payroll,` ve türetilmiş bir sınıf `BonusPayroll`, devralınan bir yöntemini geçersiz kılar `PayEmployee`. Yordamı, bir `RunPayroll`, oluşturur ve ardından geçirir bir `Payroll` nesne ve `BonusPayroll` bir işlev nesnesine `Pay`, yürütmelerinin `PayEmployee` yöntemi her iki nesne.  
  
 [!code-vb[VbVbalrOOP#28](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_1.vb)]  
  
## <a name="the-mybase-keyword"></a>MyBase anahtar sözcüğü  
 `MyBase` Anahtar sözcüğü sınıfının geçerli örneği taban sınıfına başvuruyor bir nesne değişkeni gibi davranır. `MyBase`sık sık geçersiz kılınan veya türetilen bir sınıfta gölgeli taban sınıfı üyeleri erişmek için kullanılır. Özellikle, `MyBase.New` açıkça bir temel sınıf oluşturucu türetilmiş bir sınıf oluşturucudan çağırmak için kullanılır.  
  
 Örneğin, taban sınıfından devralınan bir yöntemini geçersiz kılar türetilmiş bir sınıf tasarlama varsayalım. Geçersiz kılınan yöntemi taban sınıf içinde yöntemini çağırın ve aşağıdaki kod parçasında gösterildiği gibi dönüş değerini değiştirin:  
  
 [!code-vb[VbVbalrOOP#109](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_2.vb)]  
  
 Aşağıdaki listede kullanarak kısıtlamaları açıklar `MyBase`:  
  
-   `MyBase`hemen temel sınıfını hem de devralınan üyeleri anlamına gelir. Bu kullanılamaz erişimi `Private` sınıfı üyeleri.  
  
-   `MyBase`gerçek bir nesne bir anahtar sözcüktür. `MyBase`bir değişkene atanır, yordamlara geçirilen veya değiştirilemez kullanılan bir `Is` karşılaştırması.  
  
-   Yöntemi, `MyBase` niteleyen hemen taban sınıf içinde; tanımlanması gerekmez yerine dolaylı olarak devralınan bir taban sınıf içinde tanımlanabilir. Nitelenen başvurusu için sırayla `MyBase` doğru şekilde derlenmesi için bazı temel sınıf adını ve çağrıda görünen parametre türlerini eşleşen bir yöntem içermelidir.  
  
-   Kullanamazsınız `MyBase` çağırmak için `MustOverride` taban sınıf yöntemlerini.  
  
-   `MyBase`kendisini nitelemek için kullanılamaz. Bu nedenle, aşağıdaki kodu geçerli değil:  
  
     `MyBase.MyBase.BtnOK_Click()`  
  
-   `MyBase`modülleri kullanılamaz.  
  
-   `MyBase`olarak işaretlenmiş taban sınıfı üyeleri erişmek için kullanılamaz `Friend` temel sınıfı farklı bir derlemede ise.  
  
 Daha fazla bilgi ve başka bir örnek için bkz: [nasıl yapılır: değişken gizli türetilmiş bir sınıf tarafından erişim](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).  
  
## <a name="the-myclass-keyword"></a>MyClass anahtar sözcüğü  
 `MyClass` Anahtar sözcüğü olarak ilk olarak uygulanan bir sınıfın örneğini ifade geçerli bir nesne değişkeni gibi davranır. `MyClass`benzer `Me`, ancak her yöntem ve özellik çağrı üzerinde `MyClass` yöntemi veya özelliği değilmiş gibi davranılır [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md). Bu nedenle, yöntemi veya özelliği türetilen bir sınıfta geçersiz kılarak etkilenmez.  
  
-   `MyClass`gerçek bir nesne bir anahtar sözcüktür. `MyClass`bir değişkene atanır, yordamlara geçirilen veya değiştirilemez kullanılan bir `Is` karşılaştırması.  
  
-   `MyClass`kapsayan sınıfı hem de devralınan üyeleri anlamına gelir.  
  
-   `MyClass`Niteleyici için olarak kullanılan `Shared` üyeleri.  
  
-   `MyClass`içinde kullanılamaz bir `Shared` yöntemi, ancak paylaşılan bir sınıf üyesi erişmek için bir örnek yöntemi içinde kullanılabilir.  
  
-   `MyClass`Standart modüller kullanılamaz.  
  
-   `MyClass`taban sınıf içinde tanımlanır ve bu sınıfta sağlanan yönteminin uygulaması olan bir yöntem nitelemek için kullanılabilir. Böyle bir başvuru olarak ile aynı anlamı taşır `MyBase.` *yöntemi*.  
  
 Aşağıdaki örnek karşılaştırır `Me` ve `MyClass`.  
  
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
  
 Olsa bile `derivedClass` geçersiz kılmaları `testMethod`, `MyClass` anahtar sözcük `useMyClass` geçersiz kılma ve derleyici çözümler etkileri temel sınıf sürümü çağrısı nullifies `testMethod`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Inherits deyimi](../../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [Me, My, MyBase ve MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
