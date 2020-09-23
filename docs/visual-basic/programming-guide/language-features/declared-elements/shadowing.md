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
ms.openlocfilehash: 81e54875a3c1a4bbc5f5631e7ebac649a2e5afaf
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085899"
---
# <a name="shadowing-in-visual-basic"></a>Visual Basic'de Gölgeleme

İki programlama öğesi aynı adı paylaşıyorsa, bunlardan biri diğer birini gizleyebilir veya *gölgelendirebilir*. Böyle bir durumda, gölgelendirilmiş öğe başvuru için kullanılamaz; Bunun yerine, kodunuz öğe adını kullandığında, Visual Basic derleyici onu gölgeleme öğesine çözer.  
  
## <a name="purpose"></a>Amaç  

 Gölgeleme için ana amaç, sınıf üyelerinizin tanımını koruyasağlamaktır. Temel sınıf, zaten tanımlamış olduğunuz adla aynı ada sahip bir öğe oluşturan bir değişikliği olumsuz etkileyebilir. Bu durumda, değiştirici, `Shadows` sınıfınızın içindeki başvuruyu, yeni temel sınıf öğesi yerine tanımladığınız üyeye çözümlenmeye zorlar.  
  
## <a name="types-of-shadowing"></a>Gölgeleme türleri  

 Bir öğe, başka bir öğeyi iki farklı şekilde gölgelendirebilir. Gölgeleme öğesi, gölgeli öğeyi içeren bölgenin bir alt bölgesi içinde, bu durumda gölgeleme *kapsam aracılığıyla*yapılır. Ya da türetilen bir sınıf temel sınıfın bir üyesini yeniden tanımlayabilir, bu durumda gölgeleme *Devralma yoluyla*yapılır.  
  
### <a name="shadowing-through-scope"></a>Kapsam üzerinden gölgeleme  

 Aynı modül, sınıf veya yapıdaki öğelerin aynı ada ancak farklı kapsama sahip olması için programlama mümkündür. İki öğe bu şekilde bildirildiğinde ve kod paylaştıkları ada başvuruyorsa, dar kapsamdaki öğe diğer öğeyi (blok kapsamı en dar).  
  
 Örneğin, bir modül adlı bir değişken tanımlayabilir `Public` `temp` ve modül içindeki bir yordam de adında bir yerel değişken bildirebilir `temp` . Yordamın içinden öğesine yapılan başvurular, `temp` `temp` değişkene erişen yordamın dışından yapılan başvurular için yerel değişkene erişir `Public` . Bu durumda, yordam değişkeni `temp` Modül değişkenini gölgeliyor `temp` .  
  
 Aşağıdaki çizimde, adında iki değişken gösterilmektedir `temp` . Yerel değişken, `temp` `temp` kendi yordamı içinde erişildiğinde üye değişkenini gölgeliyor `p` . Ancak `MyClass` anahtar sözcüğü, gölgelendirmeyi atlar ve üye değişkenine erişir.  
  
 ![Kapsam aracılığıyla gölgelendirmeyi gösteren grafik.](./media/shadowing/shadow-scope-diagram.gif)
  
 Kapsam üzerinden gölgeleme örneği için bkz. [nasıl yapılır: Değişkeninizle Aynı ada sahip bir değişkeni gizleme](how-to-hide-a-variable-with-the-same-name-as-your-variable.md).  
  
### <a name="shadowing-through-inheritance"></a>Devralma yoluyla gölgeleme  

 Türetilmiş bir sınıf, temel sınıftan devralınan bir programlama öğesini yeniden tanımlar, yeniden tanımlama öğesi orijinal öğeyi gölmelidir. Herhangi bir tür tanımlanmış öğeyi veya daha fazla öğe kümesini başka herhangi bir türle gölgelendirebilir. Örneğin, bir `Integer` değişken bir yordamı gölgelendirebilir `Function` . Bir yordamı başka bir yordamla gölgelendirmek istiyorsanız farklı bir parametre listesi ve farklı bir dönüş türü kullanabilirsiniz.  
  
 Aşağıdaki çizimde, bir temel sınıf `b` ve öğesinden devralan türetilmiş bir sınıf gösterilmektedir `d` `b` . Temel sınıf adlı bir yordamı tanımlar `proc` ve türetilmiş sınıf onu aynı ada sahip başka bir yordamla birlikte gölgeler. İlk `Call` ifade, türetilmiş sınıftaki gölgelendirme erişir `proc` . Ancak `MyBase` anahtar sözcüğü, gölgelendirmeyi atlar ve temel sınıftaki gölgelendirilmiş yordama erişir.  
  
 ![Devralma yoluyla gölgeleme grafik Diyagramı](./media/shadowing/shadowing-inherit-diagram.gif)  
  
 Devralma yoluyla gölgeleme örneği için bkz. [nasıl yapılır: Değişkeninizle Aynı ada sahip bir değişkeni gizleme](how-to-hide-a-variable-with-the-same-name-as-your-variable.md) ve [nasıl yapılır: devralınan bir değişkeni gizleme](how-to-hide-an-inherited-variable.md).  
  
#### <a name="shadowing-and-access-level"></a>Gölgeleme ve erişim düzeyi  

 Gölgeleme öğesine, türetilmiş sınıf kullanılarak her zaman koddan erişilebilir. Örneğin, bu durum bildirilmiştir `Private` . Böyle bir durumda, gölgeleme ertelenmiş olur ve bir gölgeleme yoksa, derleyici aynı öğeye yapılan herhangi bir başvuruyu çözer. Bu öğe, gölgeleme sınıfından en az bir adım daha doğru olan erişilebilir öğedir. Gölgelendirilmiş öğe bir yordamdır, çözüm aynı ada, parametre listesine ve dönüş türüne sahip en yakın erişilebilir sürüme göre yapılır.  
  
 Aşağıdaki örnekte, üç sınıfın devralma hiyerarşisi gösterilmektedir. Her sınıf bir `Sub` yordamı tanımlar `display` ve türetilmiş her sınıf, `display` yordamı temel sınıfında gölmelidir.  
  
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
  
 Önceki örnekte, türetilmiş sınıf `secondClass` `display` bir yordam ile gölgeler `Private` . Modül `callDisplay` içinde çağırdığında `display` `secondClass` , çağıran kod dışarıda olur `secondClass` ve bu nedenle özel `display` yordama erişemez. Gölgeleme ertelenmiş ve derleyici, temel sınıf yordamının başvurusunu çözümlüyor `display` .  
  
 Bununla birlikte, diğer türetilmiş sınıf `thirdClass` `display` olarak bildirilir `Public` , bu nedenle içindeki kod `callDisplay` buna erişebilir.  
  
## <a name="shadowing-and-overriding"></a>Gölgeleme ve geçersiz kılma  

 Geçersiz kılma ile gölgelendirmeyi karıştırmayın. Her ikisi de türetilmiş bir sınıf temel sınıftan devralındığında ve her ikisi de bir beyan edilen öğeyi başka bir ile yeniden tanımlayarak kullanılır. Ancak ikisi arasında önemli farklılıklar vardır. Karşılaştırma için bkz. [gölgeleme ve geçersiz kılma arasındaki farklar](differences-between-shadowing-and-overriding.md).  
  
## <a name="shadowing-and-overloading"></a>Gölgeleme ve aşırı yükleme  

 Türetilmiş sınıfınıza birden fazla öğe ile aynı temel sınıf öğesini gölgelendirebiliyorsanız, gölgeleme öğeleri o öğenin aşırı yüklenmiş sürümleri haline gelir. Daha fazla bilgi için bkz. [yordam aşırı yüklemesi](../procedures/procedure-overloading.md).  
  
## <a name="accessing-a-shadowed-element"></a>Gölgelendirilmiş bir öğeye erişme  

 Türetilmiş bir sınıftan bir öğeye eriştiğinizde, genellikle bu türetilmiş sınıfın geçerli örneği aracılığıyla, öğe adını anahtar sözcüğüyle niteleyerek yapabilirsiniz `Me` . Türetilmiş sınıfınız temel sınıftaki öğesini göltiği, anahtar sözcüğü ile niteleyerek temel sınıf öğesine erişebilirsiniz `MyBase` .  
  
 Gölgelendirilmiş bir öğeye erişme örneği için bkz. [nasıl yapılır: türetilmiş bir sınıf tarafından gizlenen bir değişkene erişme](how-to-access-a-variable-hidden-by-a-derived-class.md).  
  
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
  
 Önceki örnekte, değişkeni `basObj` temel sınıf olarak bildirilmiştir. Nesnesine bir `dervCls` nesne atamak, genişleyen dönüştürme oluşturur ve bu nedenle geçerli olur. Ancak, temel sınıf türetilmiş sınıftaki değişkeninin gölgeleme sürümüne erişemez `z` , bu nedenle derleyici `basObj.z` özgün temel sınıf değerine çözümlenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bildirilmiş Öğelere Başvurular](references-to-declared-elements.md)
- [Visual Basic'de Kapsam](scope.md)
- [Genişletme ve Daraltma Dönüşümleri](../data-types/widening-and-narrowing-conversions.md)
- [Shadows](../../../language-reference/modifiers/shadows.md)
- [Geçersiz Kılmalar](../../../language-reference/modifiers/overrides.md)
- [Me, My, MyBase ve MyClass](../../program-structure/me-my-mybase-and-myclass.md)
- [Devralma Temelleri](../objects-and-classes/inheritance-basics.md)
