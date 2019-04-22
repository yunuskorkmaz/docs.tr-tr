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
ms.openlocfilehash: 9ad992a53618fa2f410e0b0fb23886c30136384f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58839398"
---
# <a name="shadowing-in-visual-basic"></a>Visual Basic'de Gölgeleme
Bunlardan biri, iki programlama öğeleri aynı adı paylaşan, gizleyebilirsiniz, veya *gölge*, diğerinde. Böyle bir durumda gölgeli öğe başvuru için kullanılabilir değildir; Bunun yerine, kodunuzu öğe adı kullandığında, Visual Basic Derleyicisi, gölgelendirme öğesine çözümler.  
  
## <a name="purpose"></a>Amaç  
 Gölgeleme ana amacı, sınıf üyelerinin tanımına korunmasını sağlamaktır. Temel sınıf olarak zaten tanımlanmış aynı ada sahip bir öğe oluşturan bir değişiklik uygulanabilir. Böyle bir durumda `Shadows` değiştiricisi zorlar başvuruyor, sınıf üyesine çözümlenmesi aracılığıyla tanımlanmış, yerine yeni bir temel sınıf öğe için.  
  
## <a name="types-of-shadowing"></a>Tür gölgeleme  
 Bir öğe başka bir öğeye iki farklı şekilde gölge. Gölgeleme öğesi bir alt bölgeli gölgeleme çalışması gerçekleştirilir gölgeli öğe içeren bölgenin içinde bildirilebilir *kapsam aracılığıyla*. Veya bir türetilen sınıf gölgeleme çalışması yapılır bir taban sınıfın üyesi bulunabileceğini belirleyebileceğiniz manasına *devralma yoluyla*.  
  
### <a name="shadowing-through-scope"></a>Kapsam yoluyla gölgeleme  
 Bu modül, sınıf veya yapı aynı ada ancak farklı bir kapsam için öğeleri programlama için mümkündür. İki öğe, bu şekilde bildirilir ve kod paylaştıkları adıdır, başka bir öğenin öğe daha dar kapsamlı gölgeleri (blok kapsamı olan en düşük).  
  
 Örneğin, bir modül tanımlayabilirsiniz bir `Public` adlı değişken `temp`, ve bir yordamda bir modül olarak da adlandırılan bir yerel değişken bildirebilirsiniz `temp`. Başvurular `temp` yordam başvurularını sırasında yerel değişken içinden erişmek `temp` gelen yordamı erişim dışında `Public` değişkeni. Bu durumda, yordam değişken `temp` modülü değişken gölgeleri `temp`.  
  
 İki değişken aşağıdaki çizimde, hem adlandırılmış `temp`. Yerel değişken `temp` üye değişkeni gölgeleri `temp` kendi yordam içinde erişildiğinde `p`. Ancak, `MyClass` anahtar sözcüğü gölgeleme atlar ve üye değişkeni erişir.  
  
 ![Kapsam yoluyla gölgeleme gösteren grafik.](./media/shadowing/shadow-scope-diagram.gif)
  
 Kapsam yoluyla gölgeleme ilişkin bir örnek için bkz [nasıl yapılır: Değişkeninizle aynı ada sahip bir değişkeni gizleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).  
  
### <a name="shadowing-through-inheritance"></a>Devralma üzerinden gölgeleme  
 Türetilmiş bir sınıf bir temel sınıftan devralınan bir programlama öğesi'ı yeniden tanımladığı, özgün öğe redefining öğesi gölgeliyor. Herhangi bir türü ile herhangi bir türde bildirilen öğe veya aşırı yüklenmiş öğeleri kümesi gölge. Örneğin, bir `Integer` değişkeni gölge bir `Function` yordamı. Başka bir yordam içeren bir yordamı gölge, başka bir parametre listesi ve farklı bir dönüş türü kullanabilirsiniz.  
  
 Aşağıdaki çizimde bir temel sınıf `b` ve türetilmiş bir sınıf `d` öğesinden devralan `b`. Adlı bir yordam temel sınıf tanımlar `proc`, ve isteğe bağlı olarak türetilmiş bir sınıf ile aynı ada sahip başka bir yordam gölgeliyor. İlk `Call` deyimi erişen gölgeleme `proc` türetilen sınıfta. Ancak, `MyBase` anahtar sözcüğü gölgeleme atlar ve temel sınıfta gölgeli yordamı erişir.  
  
 ![Devralma üzerinden gölgeleme grafik diyagramı](./media/shadowing/shadowing-inherit-diagram.gif)  
  
 Devralma üzerinden gölgeleme ilişkin bir örnek için bkz [nasıl yapılır: Değişkeninizle aynı ada sahip bir değişkeni gizleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) ve [nasıl yapılır: Devralınmış değişkeni gizleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).  
  
#### <a name="shadowing-and-access-level"></a>Gölgeleme ve erişim düzeyi  
 Gölgeleme öğe her zaman türetilen sınıfın kullanarak koddan erişilebilir değil. Örneğin, bu bildirilmesi `Private`. Böyle bir durumda gölgeleme engellenmediğinden ve aynı öğeye sahip herhangi bir referans derleyici çözümler geliştirilmişse gölgeleme yok. Bu öğe en az derivational adımları geri gölgeleme sınıftan erişilebilir öğedir. Gölgeli öğe bir yordam varsa çözümleme en yakın erişilebilir sürüme, parametre listesi, aynı ada sahip olan ve dönüş türü.  
  
 Aşağıdaki örnek, üç sınıfların Devralma Hiyerarşisi gösterir. Her bir sınıf tanımlayan bir `Sub` yordamı `display`, ve her bir türetilmiş sınıf shadows `display` yordamı temel sınıfındaki.  
  
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
  
 Yukarıdaki örnekte, türetilen sınıfın `secondClass` shadows `display` ile bir `Private` yordamı. Zaman Modülü `callDisplay` çağrıları `display` içinde `secondClass`, çağıran kodun dışında `secondClass` ve özel etkinleştirilemez `display` yordamı. Gölgeleme engellenmediğinden ve derleyicinin temel sınıf başvurusunu çözümler `display` yordamı.  
  
 Ancak, daha fazla türetilmiş sınıf `thirdClass` bildirir `display` olarak `Public`, bu nedenle kodda `callDisplay` buna erişebilir.  
  
## <a name="shadowing-and-overriding"></a>Gölgeleme ve geçersiz kılma  
 Geçersiz kılma ile gölgeleme karıştırmayın. Her ikisi de bir temel sınıftan türetilmiş bir sınıf devralır ve her ikisini de diğerine ile bildirilen bir öğe yeniden kullanılır. Ancak, ikisi arasındaki önemli farklar vardır. Bir karşılaştırması için bkz. [arasındaki farklar gölgeleme ve geçersiz kılmak](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).  
  
## <a name="shadowing-and-overloading"></a>Gölgeleme ve aşırı yükleme  
 Gölgeleme öğeleri, türetilen bir sınıfta birden fazla öğe ile aynı temel sınıf öğesi gölge, o öğenin aşırı yüklü sürümlerini haline gelir. Daha fazla bilgi için [yordam aşırı yüklemesi](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).  
  
## <a name="accessing-a-shadowed-element"></a>Gölgeli öğe erişme  
 Türetilmiş bir sınıftan bir öğe eriştiğinizde, normalde, türetilmiş sınıfın geçerli örneği üzerinden öğe adı ile uygun olarak bunu `Me` anahtar sözcüğü. Öğenin temel sınıfta türetilmiş sınıfınızın gölgeliyor, temel sınıf öğesi ile uygun erişebilirsiniz `MyBase` anahtar sözcüğü.  
  
 Gölgeli öğe erişmenin bir örnek için bkz [nasıl yapılır: Türetilmiş sınıf tarafından gizlenen bir değişkene erişme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).  
  
### <a name="declaration-of-the-object-variable"></a>Nesne değişken bildirimi  
 Nesne değişkeni oluşturma, ayrıca bir gölgeleme gölgeli öğesi veya türetilmiş sınıf erişen olmadığını etkileyebilir. Aşağıdaki örnek, iki nesne öğesinden türetilmiş bir sınıf oluşturur, ancak bir nesne, temel sınıf ve türetilen sınıf olarak bildirilir.  
  
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
  
 Yukarıdaki örnekte, değişken `basObj` temel sınıf olarak bildirilir. Atama bir `dervCls` nesnesiyle Genişletme dönüşümü oluşturan ve bu nedenle geçerli değil. Ancak, temel sınıf değişkeni gölgeleme sürümünü erişemez `z` türetilen sınıfta, böylece derleyici çözümler `basObj.z` özgün değere temel sınıf.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bildirilmiş Öğelere Başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Visual Basic'de kapsam](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Genişletme ve Daraltma Dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me, My, MyBase ve MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Devralma Temelleri](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
