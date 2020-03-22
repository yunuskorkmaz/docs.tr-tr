---
title: Gölge Kullanım
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
ms.openlocfilehash: 20a33478f622fca6d3183772f53dcb3e72f79409
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266891"
---
# <a name="shadowing-in-visual-basic"></a>Visual Basic'de Gölgeleme
İki programlama öğesi aynı adı paylaştığında, bunlardan biri gizleyebilir veya diğeri *gölgelenebilir.* Böyle bir durumda, gölgeli öğe başvuru için kullanılamaz; bunun yerine, kodunuz öğe adını kullandığında, Visual Basic derleyicisi onu gölgeleme öğesine çözer.  
  
## <a name="purpose"></a>Amaç  
 Gölgelemenin temel amacı, sınıf üyelerinizin tanımını korumaktır. Taban sınıf, daha önce tanımladığınız öğeyle aynı ada sahip bir öğe oluşturan bir değişikliğe uğrayabilir. Bu durumda, `Shadows` değiştirici başvuruları sınıfınız aracılığıyla yeni taban sınıf öğesi yerine tanımladığınız üyeye çözümlenecek şekilde zorlar.  
  
## <a name="types-of-shadowing"></a>Gölgeleme Türleri  
 Bir öğe başka bir öğeyi iki farklı şekilde gölgeleyebilir. Gölgeleme öğesi, gölgeli öğeyi içeren bölgenin bir alt bölgesi içinde bildirilebilir ve bu durumda gölgeleme *kapsam boyunca*gerçekleştirilir. Veya türeyen bir sınıf, bir taban sınıfın üyesini yeniden tanımlayabilir, bu durumda gölgeleme *devralma yoluyla*yapılır.  
  
### <a name="shadowing-through-scope"></a>Kapsam Boyunca Gölgeleme  
 Aynı modül, sınıf veya yapıdaki programlama öğelerinin aynı ada ancak farklı bir kapsama sahip olması mümkündür. İki öğe bu şekilde bildirildiğinde ve kod paylaştıkları adı ifade ettiğinde, dar kapsama sahip öğe diğer öğeyi gölgeler (blok kapsamı en dardır).  
  
 Örneğin, bir modül adlı `Public` `temp`bir değişken tanımlayabilir ve modül içindeki bir `temp`yordam da adlı yerel bir değişken bildirebilir. Yordam `temp` ın içinden yapılan başvurular yerel değişkene erişirken, yordamın dışından gelen başvurular değişkene `temp` erişir. `Public` Bu durumda, yordam `temp` değişkeni modül `temp`değişkenini gölgeler.  
  
 Aşağıdaki resimde, her ikisi de `temp`. Yerel değişken, `temp` üye değişkeni `temp` kendi yordamı `p`içinden erişildiğinde gölgeler. Ancak, `MyClass` anahtar kelime gölgeleme atlar ve üye değişkenerişer.  
  
 ![Kapsam boyunca gölgeleme gösteren grafik.](./media/shadowing/shadow-scope-diagram.gif)
  
 Kapsam boyunca gölgeleme örneği için [bkz: Değişkeninizle aynı ada sahip bir Değişkeni gizleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).  
  
### <a name="shadowing-through-inheritance"></a>Devralma Yoluyla Gölgeleme  
 Türetilmiş bir sınıf, taban sınıftan devralınan bir programlama öğesini yeniden tanımlıyorsa, yeniden tanımlayan öğe özgün öğeyi gölgeler. Beyan edilen öğe nin herhangi bir türünü veya aşırı yüklü öğeler kümesini başka bir türle gölgeleyebilirsiniz. Örneğin, bir `Integer` değişken bir `Function` yordamı gölgeleyebilir. Bir yordamı başka bir yordamla gölgelerseniz, farklı bir parametre listesi ve farklı bir iade türü kullanabilirsiniz.  
  
 Aşağıdaki resimde bir taban `b` sınıf ve `d` devralan `b`türetilmiş bir sınıf gösterilmektedir. Taban sınıf adlı `proc`bir yordam tanımlar ve türemiş sınıf aynı adı taşıyan başka bir yordam ile gölgeler. İlk `Call` deyim, türemiş `proc` sınıftaki gölgeleme erişirebedilir. Ancak, `MyBase` anahtar kelime gölgeleme atlar ve temel sınıfta gölgeli yordamı erişer.  
  
 ![Kalıtım yoluyla gölgelemegrafik diyagramı](./media/shadowing/shadowing-inherit-diagram.gif)  
  
 Devralma yoluyla gölgeleme örneği için [bkz: Değişkeninizle Aynı Ada sahip Bir Değişkeni Gizleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) ve [Nasıl Gizleni: Devralınan Değişkeni Gizleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).  
  
#### <a name="shadowing-and-access-level"></a>Gölgeleme ve Erişim Düzeyi  
 Gölgeleme öğesine türetilmiş sınıfı kullanarak koddan her zaman erişilemez. Örneğin, '. `Private` Böyle bir durumda, gölgeleme yenir ve derleyici, gölgeleme olmasaydı aynı öğeye herhangi bir başvuruyu çözer. Bu öğe, gölgeleme sınıfından geriye doğru en az türev basamakları erişilebilir öğedir. Gölgeli öğe bir yordamsa, çözünürlük aynı ada, parametre listesine ve iade türüne sahip en yakın erişilebilir sürüme verilir.  
  
 Aşağıdaki örnekte, üç sınıfın kalıtım hiyerarşisi gösterilmektedir. Her sınıf bir `Sub` `display`yordam tanımlar ve türetilen `display` her sınıf yordamı kendi taban sınıfında gölgeler.  
  
```vb  
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
  
 Önceki örnekte, türemiş `secondClass` sınıf `display` bir `Private` yordam ile gölgeler. Modül `callDisplay` `display` `secondClass`aradığında, arama kodu `secondClass` dışarıdadır ve bu `display` nedenle özel yordama erişemez. Gölgeleme yenilir ve derleyici temel sınıf `display` yordamına başvuru çözer.  
  
 Ancak, türetilen `thirdClass` sınıf `display` `Public`, kod `callDisplay` erişebilmek için bildirir.  
  
## <a name="shadowing-and-overriding"></a>Gölgeleme ve Geçersiz Kılma  
 Gölgeleme ile geçersiz kılmayı karıştırmayın. Her ikisi de türetilmiş bir sınıf bir taban sınıftan devraldığında kullanılır ve her ikisi de bir bildirilen öğeyi başka bir öğeyle yeniden tanımlar. Ama ikisi arasında önemli farklar vardır. Karşılaştırma için, [Gölgeleme ve Geçersiz Kılma Arasındaki Farklar'a](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)bakın.  
  
## <a name="shadowing-and-overloading"></a>Gölgeleme ve Aşırı Yükleme  
 Türemiş sınıfınızda birden fazla öğeyle aynı taban sınıf öğesini gölgelerseniz, gölgeleme öğeleri bu öğenin aşırı yüklenmiş sürümleri haline gelir. Daha fazla bilgi için [bkz.](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)  
  
## <a name="accessing-a-shadowed-element"></a>Gölgeli Öğeye Erişim  
 Türemiş bir sınıftan bir öğeye erişdiğinizde, normalde bunu türemiş sınıfın geçerli örneği `Me` aracılığıyla, öğe adını anahtar kelimeyle niteleyerek yaparsınız. Türemiş sınıfınız taban sınıftaki öğeyi gölgelerse, anahtar kelimeyle niteleyerek taban sınıf öğesine `MyBase` erişebilirsiniz.  
  
 Gölgeli bir öğeye erişmek için [bkz: Türemiş Sınıf tarafından gizlenmiş bir değişkene erişim.](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)  
  
### <a name="declaration-of-the-object-variable"></a>Nesne Değişkeninin Bildirimi  
 Nesne değişkenini nasıl oluşturduğunuz, türemiş sınıfın gölgeleme öğesine mi yoksa gölgeli öğeye mi erişeceğini de etkileyebilir. Aşağıdaki örnektüre bir sınıftan iki nesne oluşturur, ancak bir nesne taban sınıf ve diğer türemiş sınıf olarak bildirilir.  
  
```vb  
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
  
 Önceki örnekte, değişken `basObj` taban sınıf olarak bildirilir. Bir `dervCls` nesneyi ona atamak genişleyen bir dönüşüm oluşturur ve bu nedenle geçerlidir. Ancak, taban sınıf türetilmiş sınıfta değişkenin `z` gölgeleme sürümüne erişemez, `basObj.z` bu nedenle derleyici özgün taban sınıf değerine giderir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bildirilmiş Öğelere Başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Visual Basic'de Kapsam](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Genişletme ve Daraltma Dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me, My, MyBase ve MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Devralma Temelleri](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
