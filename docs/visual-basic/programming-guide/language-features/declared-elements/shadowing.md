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
ms.openlocfilehash: 30c02cf367c461c3896a01538d03380627de294f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004859"
---
# <a name="shadowing-in-visual-basic"></a>Visual Basic'de Gölgeleme
İki programlama öğesi aynı adı paylaşıyorsa, bunlardan biri diğer birini gizleyebilir veya *gölgelendirebilir*. Böyle bir durumda, gölgelendirilmiş öğe başvuru için kullanılamaz; Bunun yerine, kodunuz öğe adını kullandığında, Visual Basic derleyici onu gölgeleme öğesine çözer.  
  
## <a name="purpose"></a>Amaç  
 Gölgeleme için ana amaç, sınıf üyelerinizin tanımını koruyasağlamaktır. Temel sınıf, zaten tanımlamış olduğunuz adla aynı ada sahip bir öğe oluşturan bir değişikliği olumsuz etkileyebilir. Bu durumda, `Shadows` değiştiricisi, sınıfınızın içindeki başvuruyu, yeni temel sınıf öğesi yerine tanımladığınız üyeye çözümlenmeye zorlar.  
  
## <a name="types-of-shadowing"></a>Gölgeleme türleri  
 Bir öğe, başka bir öğeyi iki farklı şekilde gölgelendirebilir. Gölgeleme öğesi, gölgeli öğeyi içeren bölgenin bir alt bölgesi içinde, bu durumda gölgeleme *kapsam aracılığıyla*yapılır. Ya da türetilen bir sınıf temel sınıfın bir üyesini yeniden tanımlayabilir, bu durumda gölgeleme *Devralma yoluyla*yapılır.  
  
### <a name="shadowing-through-scope"></a>Kapsam üzerinden gölgeleme  
 Aynı modül, sınıf veya yapıdaki öğelerin aynı ada ancak farklı kapsama sahip olması için programlama mümkündür. İki öğe bu şekilde bildirildiğinde ve kod paylaştıkları ada başvuruyorsa, dar kapsamdaki öğe diğer öğeyi (blok kapsamı en dar).  
  
 Örneğin, bir modül `temp` adlı `Public` değişkeni tanımlayabilir ve modül içindeki bir yordam, aynı zamanda `temp` adında bir yerel değişken bildirebilir. Yordamın içindeki `temp` ' a yapılan başvurular, `Public` değişkenine erişen yordamın dışındaki `temp` ' e başvuruda bulunan yerel değişkene erişir. Bu durumda, `temp` yordam değişkeni, `temp` modül değişkenini gölgeliyor.  
  
 Aşağıdaki çizimde `temp` adlı iki değişken gösterilmektedir. @No__t-0 yerel değişkeni, kendi yordamından `p` ' den erişildiğinde üye değişkeni `temp` ' i gölgeler. Ancak `MyClass` anahtar sözcüğü, gölgelendirmeyi atlar ve üye değişkenine erişir.  
  
 ![Kapsam aracılığıyla gölgelendirmeyi gösteren grafik.](./media/shadowing/shadow-scope-diagram.gif)
  
 Kapsam üzerinden gölgeleme örneği için bkz. [nasıl yapılır: Değişkeninizle Aynı ada sahip bir değişkeni gizleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).  
  
### <a name="shadowing-through-inheritance"></a>Devralma yoluyla gölgeleme  
 Türetilmiş bir sınıf, temel sınıftan devralınan bir programlama öğesini yeniden tanımlar, yeniden tanımlama öğesi orijinal öğeyi gölmelidir. Herhangi bir tür tanımlanmış öğeyi veya daha fazla öğe kümesini başka herhangi bir türle gölgelendirebilir. Örneğin, `Integer` değişkeni bir `Function` yordamını gölgelendirebilir. Bir yordamı başka bir yordamla gölgelendirmek istiyorsanız farklı bir parametre listesi ve farklı bir dönüş türü kullanabilirsiniz.  
  
 Aşağıdaki çizim `b` ve `b` ' den devralan türetilmiş bir sınıf olan `d` temel sınıfını gösterir. Temel sınıf, `proc` adlı bir yordamı tanımlar ve türetilmiş sınıf onu aynı ada sahip başka bir yordamla birlikte gölgeler. İlk `Call` ifadesinde, türetilmiş sınıfta gölgeleme `proc` erişilir. Ancak `MyBase` anahtar sözcüğü, gölgelendirmeyi atlar ve temel sınıftaki gölgelendirilmiş yordama erişir.  
  
 ![Devralma yoluyla gölgeleme grafik Diyagramı](./media/shadowing/shadowing-inherit-diagram.gif)  
  
 Devralma yoluyla gölgeleme örneği için bkz. [nasıl yapılır: Değişkeninizle Aynı ada sahip bir değişkeni gizleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) ve [nasıl yapılır: devralınan bir değişkeni gizleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).  
  
#### <a name="shadowing-and-access-level"></a>Gölgeleme ve erişim düzeyi  
 Gölgeleme öğesine, türetilmiş sınıf kullanılarak her zaman koddan erişilebilir. Örneğin, `Private` olarak tanımlanmış olabilir. Böyle bir durumda, gölgeleme ertelenmiş olur ve bir gölgeleme yoksa, derleyici aynı öğeye yapılan herhangi bir başvuruyu çözer. Bu öğe, gölgeleme sınıfından en az bir adım daha doğru olan erişilebilir öğedir. Gölgelendirilmiş öğe bir yordamdır, çözüm aynı ada, parametre listesine ve dönüş türüne sahip en yakın erişilebilir sürüme göre yapılır.  
  
 Aşağıdaki örnekte, üç sınıfın devralma hiyerarşisi gösterilmektedir. Her sınıf `display` `Sub` yordamını tanımlar ve türetilmiş her sınıf temel sınıfında `display` yordamını gölmelidir.  
  
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
  
 Önceki örnekte, türetilmiş sınıf `secondClass` gölgeleri `display` `Private` prosedürü ile. @No__t-0 `display` ' i `secondClass` ' de çağırdığında, çağıran kod `secondClass` ' ün dışındadır ve bu nedenle özel `display` yordamına erişemez. Gölgeleme ertelenmiş ve derleyici, temel sınıf `display` yordamının başvurusunu çözer.  
  
 Ancak, daha fazla türetilmiş sınıf `thirdClass` `display` ' i `Public` olarak bildirir `callDisplay` ' teki kod buna erişebilir.  
  
## <a name="shadowing-and-overriding"></a>Gölgeleme ve geçersiz kılma  
 Geçersiz kılma ile gölgelendirmeyi karıştırmayın. Her ikisi de türetilmiş bir sınıf temel sınıftan devralındığında ve her ikisi de bir beyan edilen öğeyi başka bir ile yeniden tanımlayarak kullanılır. Ancak ikisi arasında önemli farklılıklar vardır. Karşılaştırma için bkz. [gölgeleme ve geçersiz kılma arasındaki farklar](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).  
  
## <a name="shadowing-and-overloading"></a>Gölgeleme ve aşırı yükleme  
 Türetilmiş sınıfınıza birden fazla öğe ile aynı temel sınıf öğesini gölgelendirebiliyorsanız, gölgeleme öğeleri o öğenin aşırı yüklenmiş sürümleri haline gelir. Daha fazla bilgi için bkz. [yordam aşırı yüklemesi](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).  
  
## <a name="accessing-a-shadowed-element"></a>Gölgelendirilmiş bir öğeye erişme  
 Türetilmiş bir sınıftan bir öğeye eriştiğinizde, genellikle bu türetilmiş sınıfın geçerli örneği aracılığıyla, öğe adını `Me` anahtar sözcüğüyle niteleyerek yapabilirsiniz. Türetilmiş sınıfınız temel sınıftaki öğeyi gölmişse, `MyBase` anahtar sözcüğüyle niteleyerek temel sınıf öğesine erişebilirsiniz.  
  
 Gölgelendirilmiş bir öğeye erişme örneği için bkz. [nasıl yapılır: türetilmiş bir sınıf tarafından gizlenen bir değişkene erişme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).  
  
### <a name="declaration-of-the-object-variable"></a>Nesne değişkeninin bildirimi  
 Nesne değişkenini nasıl oluşturacağınız, türetilmiş sınıfın bir gölgeleme öğesine mi yoksa gölgelendirilmiş öğeye mi eriştiğini de etkileyebilir. Aşağıdaki örnek, türetilmiş bir sınıftan iki nesne oluşturur, ancak bir nesne temel sınıf olarak ve diğeri türetilmiş sınıf olarak bildirilmiştir.  
  
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
  
 Yukarıdaki örnekte, `basObj` değişkeni temel sınıf olarak bildirilmiştir. @No__t-0 nesnesine atama, genişleyen dönüştürme oluşturur ve bu nedenle geçerli olur. Ancak, temel sınıf türetilmiş sınıfta `z` değişkeninin gölgeleme sürümüne erişemez, bu nedenle derleyici `basObj.z` ' i özgün temel sınıf değerine çözümlemez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bildirilmiş Öğelere Başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Visual Basic kapsam](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Genişletme ve Daraltma Dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me, My, MyBase ve MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Devralma Temelleri](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
