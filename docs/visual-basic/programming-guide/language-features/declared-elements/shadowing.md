---
title: Visual Basic'de Gölgeleme
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], shadowing
- overriding, and shadowing
- shadowing
- duplicate names [Visual Basic]
- shadowing, by inheritance
- declared elements [Visual Basic], referencing
- shadowing, by scope
- declared elements [Visual Basic], hiding
- naming conflicts, shadowing
- declared elements [Visual Basic], shadowing
- shadowing, and overriding
- scope [Visual Basic], shadowing
- Shadows keyword [Visual Basic], about
- objects [Visual Basic], names
- names [Visual Basic], shadowing
ms.assetid: 54bb4c25-12c4-4181-b4a0-93546053964e
ms.openlocfilehash: fde6259b67a8d963ed8c30b87c94029fb2658664
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656077"
---
# <a name="shadowing-in-visual-basic"></a>Visual Basic'de Gölgeleme
İki programlama öğeleri aynı adı paylaşan, bunlardan birini gizleyebilirsiniz, veya *gölge*, diğerinde. Böyle bir durumda gölgeli öğesi başvurusu için kullanılabilir değil; kodunuzu öğe adı kullandığında, bunun yerine, Visual Basic derleyici gölgeleme öğesine çözer.  
  
## <a name="purpose"></a>Amaç  
 Gölgeleme ana amacı, sınıf üyeleri tanımını korumaktır. Taban sınıf, bir önceden tanımlamış aynı ada sahip bir öğe oluşturan bir değişiklik uygulanabilir. Bu durumda, `Shadows` değiştiricisi zorlar başvuran üyesine çözümlenmesi sınıfınız üzerinden tanımlanmış, yerine yeni bir temel sınıf öğesi için.  
  
## <a name="types-of-shadowing"></a>Gölgeleme türleri  
 Bir öğe başka bir öğe iki farklı şekilde gölge. Gölgeleme öğesi bir durumda gölgeleme gerçekleştirilir gölgeli öğeyi içeren bölge alt içinde bildirilebilir *kapsam aracılığıyla*. Veya türetme sınıfı gölgeleme çalışması yapılır, bir taban sınıf üyesi tanımlayabilirsiniz *devralma yoluyla*.  
  
### <a name="shadowing-through-scope"></a>Kapsam yoluyla gölgeleme  
 Programlama öğelerine modülü, sınıf veya aynı adlı ancak farklı bir kapsam için yapısı için mümkündür. Bu şekilde iki öğe olarak bildirilen ve kod paylaştıkları adına başvuran daha dar kapsamlı öğesi başka bir öğenin shadows (blok kapsamı olan dar).  
  
 Örneğin, bir modül tanımlayabilirsiniz bir `Public` adlı değişken `temp`, ve bir yordam modülü içinde de adlı bir yerel değişken bildirebilir `temp`. Başvurular `temp` içinden yordamı erişim yerel değişken başvuruları sırasında `temp` gelen yordamı erişim dışında `Public` değişkeni. Bu durumda, yordam değişkeni `temp` modülü değişken shadows `temp`.  
  
 Aşağıdaki çizimde iki değişken gösterir, her ikisi de adlı `temp`. Yerel değişken `temp` üye değişkeni shadows `temp` kendi yordam içinde erişildiğinde `p`. Ancak, `MyClass` anahtar sözcüğü gölgeleme atlar ve üye değişkeni erişir.  
  
 ![Kapsam yoluyla gölgeleme grafik diyagramı](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowscope.gif "ShadowScope")  
Kapsam yoluyla gölgeleme  
  
 Kapsam yoluyla gölgeleme ilişkin bir örnek için bkz: [nasıl yapılır: bilgisayarınızı değişken aynı ada sahip bir değişken Gizle](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).  
  
### <a name="shadowing-through-inheritance"></a>Devralma yoluyla gölgeleme  
 Türetilmiş bir sınıf bir taban sınıftan devralınan bir programlama öğesi yeniden tanımlamaktadır, redefining öğesi özgün öğesi shadows. Bildirilen öğe herhangi bir türde veya aşırı yüklenmiş öğelerin herhangi bir türü ile gölge. Örneğin, bir `Integer` değişkeni gölge bir `Function` yordamı. Başka bir yordam yordamla gölge, farklı parametre listesi ve farklı bir dönüş türü kullanabilirsiniz.  
  
 Aşağıdaki çizimde bir taban sınıfı gösterir `b` ve türetilmiş bir sınıf `d` devraldığı `b`. Adlı bir yordam temel sınıf tanımlar `proc`, ve isteğe bağlı olarak türetilmiş sınıf ile aynı ada sahip başka bir yordam shadows. İlk `Call` deyimi erişen gölgeleme `proc` türetilen sınıfta. Ancak, `MyBase` anahtar sözcüğü gölgeleme atlar ve temel sınıfı gölgeli yordamda erişir.  
  
 ![Devralma yoluyla gölgeleme grafik diyagramı](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowinherit.gif "ShadowInherit")  
Devralma yoluyla gölgeleme  
  
 Devralma yoluyla gölgeleme ilişkin bir örnek için bkz: [nasıl yapılır: bilgisayarınızı değişken aynı ada sahip bir değişken Gizle](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) ve [nasıl yapılır: bir devralınmış değişkeni gizleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).  
  
#### <a name="shadowing-and-access-level"></a>Gölgeleme ve erişim düzeyi  
 Gölgeleme öğe her zaman koddan türetilmiş bir sınıf kullanarak erişilebilir değil. Örneğin, bunu bildirilmesi `Private`. Böyle bir durumda gölgeleme engellenmediğinden ve derleyici sahip aynı öğesine herhangi bir referans çözümler geliştirilmişse gölgeleme yok. Bu öğe ve en az derivational adımları geriye doğru gölgeleme sınıfından erişilebilir öğedir. Gölgeli öğesi bir yordam ise, çözümleme en yakın erişilebilir sürüme parametre listesi, aynı ada sahip olan ve dönüş türü.  
  
 Aşağıdaki örnekte, üç sınıf devralma hiyerarşisini gösterir. Her sınıf tanımlayan bir `Sub` yordamı `display`, ve her türetilmiş sınıf gölgeleri `display` devralınabilir. taban sınıf yordamda.  
  
```  
Public Class firstClass  
    Public Sub display()  
        MsgBox("This is firstClass")  
    End Sub  
End Class  
Public Class secondClass  
    Inherits firstClass  
    Private Shadows Sub display()  
        MsgBox("This is secondClass")  
    End Sub  
End Class  
Public Class thirdClass  
    Inherits secondClass  
    Public Shadows Sub display()  
        MsgBox("This is thirdClass")  
    End Sub  
End Class  
Module callDisplay  
    Dim first As New firstClass  
    Dim second As New secondClass  
    Dim third As New thirdClass  
    Public Sub callDisplayProcedures()  
        ' The following statement displays "This is firstClass".  
        first.display()  
        ' The following statement displays "This is firstClass".  
        second.display()  
        ' The following statement displays "This is thirdClass".  
        third.display()  
    End Sub  
End Module  
```  
  
 Önceki örnekte, türetilmiş sınıf `secondClass` gölgeleri `display` ile bir `Private` yordamı. Zaman Modülü `callDisplay` çağrıları `display` içinde `secondClass`, çağrıyı yapan kod dışında `secondClass` ve bu nedenle özel erişemiyor `display` yordamı. Gölgeleme engellenmediğinden ve temel sınıfı referansı derleyici çözümler `display` yordamı.  
  
 Ancak, daha fazla türetilmiş sınıf `thirdClass` bildirir `display` olarak `Public`, bu nedenle kodda `callDisplay` erişilebilir.  
  
## <a name="shadowing-and-overriding"></a>Gölgeleme ve geçersiz kılma  
 Geçersiz kılma ile gölgeleme karıştırmayın. Her ikisi de türetilmiş bir sınıf bir taban sınıfından devralıyor ve her ikisi de bildirilen bir öğe başka bir yeniden tanımlamanız olduğunda kullanılır. Ancak ikisi arasındaki önemli farklılıklar vardır. Bir karşılaştırması için bkz: [arasındaki farklar gölgeleme ve geçersiz kılınıyor](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).  
  
## <a name="shadowing-and-overloading"></a>Gölgeleme ve aşırı yüklemesi  
 Türetilen sınıfta birden fazla öğe ile aynı temel sınıfı öğesi gölge varsa, o öğenin aşırı yüklenmiş sürümler gölgeleme öğeleri olur. Daha fazla bilgi için bkz: [yordam aşırı yüklemesi](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).  
  
## <a name="accessing-a-shadowed-element"></a>Gölgeli öğesi erişme  
 Türetilen bir sınıftan bir öğe eriştiğinizde, normalde bu türetilmiş sınıfının geçerli örneği aracılığıyla öğe adı ile niteleme tarafından bunu `Me` anahtar sözcüğü. Türetilmiş sınıf temel sınıfı öğesinde shadows, kendisiyle niteleme temel sınıf öğesi erişebilir `MyBase` anahtar sözcüğü.  
  
 Gölgeli öğesi erişme ilişkin bir örnek için bkz: [nasıl yapılır: değişken gizli türetilmiş bir sınıf tarafından erişim](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).  
  
### <a name="declaration-of-the-object-variable"></a>Nesne değişken bildirimi  
 Nesne değişkeni oluşturma, ayrıca bir gölgeleme gölgeli öğesi veya türetilmiş bir sınıf erişen olup olmadığını etkileyebilir. Aşağıdaki örnekte iki nesne öğesinden türetilmiş bir sınıf oluşturur, ancak bir nesne temel sınıf ve türetilen sınıf olarak diğer olarak bildirilir.  
  
```  
Public Class baseCls  
    ' The following statement declares the element that is to be shadowed.  
    Public z As Integer = 100  
End Class  
Public Class dervCls  
    Inherits baseCls  
    ' The following statement declares the shadowing element.  
    Public Shadows z As String = "*"  
End Class  
Public Class useClasses  
    ' The following statement creates the object declared as the base class.  
    Dim basObj As baseCls = New dervCls()  
    ' Note that dervCls widens to its base class baseCls.  
    ' The following statement creates the object declared as the derived class.  
    Dim derObj As dervCls = New dervCls()  
    Public Sub showZ()   
    ' The following statement outputs 100 (the shadowed element).  
        MsgBox("Accessed through base class: " & basObj.z)  
    ' The following statement outputs "*" (the shadowing element).  
        MsgBox("Accessed through derived class: " & derObj.z)  
    End Sub  
End Class  
```  
  
 Önceki örnekte, değişken `basObj` temel sınıf olarak bildirilmedi. Atama bir `dervCls` nesnesiyle Genişletme dönüşümü oluşturduğunu ve bu nedenle geçerli değil. Ancak, temel sınıf değişkeni gölgeleme sürümü erişemiyor `z` türetilen sınıfta bu nedenle derleyici çözümler `basObj.z` özgün temel sınıf değerine.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bildirilmiş Öğelere Başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Visual Basic'de kapsam](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [Genişletme ve Daraltma Dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)  
 [Me, My, MyBase ve MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [Devralma Temelleri](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
