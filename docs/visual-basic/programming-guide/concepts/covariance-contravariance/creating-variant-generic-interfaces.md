---
title: Değişken genel arabirimler oluşturma (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d4037dd2-dfe9-4811-9150-93d4e8b20113
ms.openlocfilehash: d6afddf018b4608418f82fa851d018f2c3e1d0fb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663264"
---
# <a name="creating-variant-generic-interfaces-visual-basic"></a>Değişken genel arabirimler oluşturma (Visual Basic)
Genel Tür parametrelerine birlikte değişken olarak arabirimleri bildirebilir veya değişken karşıtı. *Kovaryans* dönüş türleri genel tür parametreleri tarafından tanımlanan değerinden daha fazla türetilmiş arabirim yöntemleri sağlar. *Kontravaryans* genel parametreler tarafından belirtilenden daha az türetilmiş bağımsız değişken türleri arabirim yöntemleri sağlar. Birlikte değişken olan genel bir arabirim veya değişken karşıtı genel tür parametreleri çağrılır *değişken*.  
  
> [!NOTE]
>  .NET framework 4, çeşitli genel arabirimlerin mevcut sapma desteği sunmuştur. .NET Framework'teki değişken arabirimler listesi için bkz. [Variance in Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).  
  
## <a name="declaring-variant-generic-interfaces"></a>Bildirim değişken genel arabirimler  
 Değişken genel arabirimler kullanarak bildirebilirsiniz `in` ve `out` genel tür parametreleri için anahtar sözcükler.  
  
> [!IMPORTANT]
>  `ByRef` Visual Basic'te parametreleri varyant olamaz. Değer türleri varyansı da desteklemez.  
  
 Genel tür parametresi birlikte değişken kullanarak bildirebilirsiniz `out` anahtar sözcüğü. Birlikte değişen türde aşağıdaki koşulları karşılaması gerekir:  
  
-   Türü yalnızca bir dönüş türü arabirim yöntemleri olarak kullanılan ve yöntem bağımsız bir türü olarak kullanılmaz. Bu, aşağıdaki örnekte gösterilmiştir türü `R` birlikte değişken olarak bildirilir.  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        Function GetSomething() As R  
        ' The following statement generates a compiler error.  
        ' Sub SetSomething(ByVal sampleArg As R)  
    End Interface  
    ```  
  
     Bu kuralın tek istisnası yoktur. Bir yöntem parametresi olarak bir değişken karşıtı Genel temsilci varsa, türü için temsilci genel tür parametre olarak kullanabilirsiniz. Bu tür tarafından gösterilmiştir `R` aşağıdaki örnekte. Daha fazla bilgi için [Temsilcilerde varyans (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) ve [işlev ve eylem genel temsilcileri (Visual Basic) kullanarak varyansını](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        Sub DoSomething(ByVal callback As Action(Of R))  
    End Interface  
    ```  
  
-   Türü genel kısıtlama olarak arabirim yöntemleri için kullanılmaz. Bu, aşağıdaki kodda gösterilmiştir.  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        ' The following statement generates a compiler error  
        ' because you can use only contravariant or invariant types  
        ' in generic contstraints.  
        ' Sub DoSomething(Of T As R)()  
    End Interface  
    ```  
  
 Bir genel tür parametresi değişken karşıtı kullanarak bildirebilirsiniz `in` anahtar sözcüğü. Değişken karşıtı türü arabirim yöntemleri dönüş türü olarak değil de yalnızca bir tür yöntem bağımsız olarak kullanılabilir. Değişken karşıtı türü genel kısıtlamalar için de kullanılabilir. Aşağıdaki kod, bir değişken karşıtı arabirimi bildirme ve bir genel kısıtlama yöntemlerinden biri için kullanma gösterilmektedir.  
  
```vb  
Interface IContravariant(Of In A)  
    Sub SetSomething(ByVal sampleArg As A)  
    Sub DoSomething(Of T As A)()  
    ' The following statement generates a compiler error.  
    ' Function GetSomething() As A  
End Interface  
```  
  
 Ayrıca aşağıdaki kod örneğinde gösterildiği gibi aynı arabirimi, ancak farklı türde parametreler için hem Kovaryans ve kontravaryans desteklemek mümkündür.  
  
```vb  
Interface IVariant(Of Out R, In A)  
    Function GetSomething() As R  
    Sub SetSomething(ByVal sampleArg As A)  
    Function GetSetSomething(ByVal sampleArg As A) As R  
End Interface  
```  
  
 Visual Basic'te, temsilci türü belirtmeden değişken Arabirimlerdeki olaylar bildiremezsiniz. Ayrıca, bir değişken arabirimi sınıflar, numaralandırmalar ve yapılar iç içe geçmiş olamaz, ancak arabirimleri içe. Bu, aşağıdaki kodda gösterilmiştir.  
  
```vb  
Interface ICovariant(Of Out R)  
    ' The following statement generates a compiler error.  
    ' Event SampleEvent()  
    ' The following statement specifies the delegate type and   
    ' does not generate an error.  
    Event AnotherEvent As EventHandler  
  
    ' The following statements generate compiler errors,  
    ' because a variant interface cannot have  
    ' nested enums, classes, or structures.  
  
    'Enum SampleEnum : test : End Enum  
    'Class SampleClass : End Class  
    'Structure SampleStructure : Dim value As Integer : End Structure  
  
    ' Variant interfaces can have nested interfaces.  
    Interface INested : End Interface  
End Interface  
```  
  
## <a name="implementing-variant-generic-interfaces"></a>Değişken genel arabirimler uygulama  
 Değişken genel arabirimler sınıflarda sabit arabirimler için kullanılan aynı sözdizimini kullanarak uygulayın. Aşağıdaki kod örneği, birlikte değişken arabirimi genel bir sınıf uygulamak gösterilmektedir.  
  
```vb  
Interface ICovariant(Of Out R)  
    Function GetSomething() As R  
End Interface  
  
Class SampleImplementation(Of R)  
    Implements ICovariant(Of R)  
    Public Function GetSomething() As R _  
    Implements ICovariant(Of R).GetSomething  
        ' Some code.  
    End Function  
End Class  
```  
  
 Sabit değişken arabirimleri uygulayan sınıflar. Örneğin, aşağıdaki kodu düşünün.  
  
```vb  
 The interface is covariant.  
Dim ibutton As ICovariant(Of Button) =  
    New SampleImplementation(Of Button)  
Dim iobj As ICovariant(Of Object) = ibutton  
  
' The class is invariant.  
Dim button As SampleImplementation(Of Button) =  
    New SampleImplementation(Of Button)  
' The following statement generates a compiler error  
' because classes are invariant.  
' Dim obj As SampleImplementation(Of Object) = button  
```  
  
## <a name="extending-variant-generic-interfaces"></a>Genişletme değişken genel arabirimler  
 Bir değişken genel arabirim genişlettiğinizde kullanmak zorunda `in` ve `out` açıkça türetilmiş bir arabirim varyansı destekleyip desteklemediğini belirlemek için anahtar sözcükler. Derleyici, varyans Genişletilmekte olan arabiriminden Infer değil. Örneğin, aşağıdaki arabirimlerinden göz önünde bulundurun.  
  
```vb  
Interface ICovariant(Of Out T)  
End Interface  
  
Interface IInvariant(Of T)  
    Inherits ICovariant(Of T)  
End Interface  
  
Interface IExtCovariant(Of Out T)  
    Inherits ICovariant(Of T)  
End Interface  
```  
  
 İçinde `Invariant(Of T)` arabirim, genel tür parametresi `T` değişmezdir, ise içinde `IExtCovariant (Of Out T)`hem arabirimleri aynı arabirimi genişletmek rağmen tür parametresi değişkendir. Aynı kural, değişken karşıtı genel tür parametreleri için uygulanır.  
  
 Burada, genel tür parametresi her iki arabirimini genişletir bir arabirim oluşturabilirsiniz `T` birlikte değişkendir ve genel tür parametresi, genişletme, değişken karşıtı olduğu arabirimi arabirim `T` değişmezdir. Bu aşağıdaki kod örneğinde gösterilmiştir.  
  
```vb  
Interface ICovariant(Of Out T)  
End Interface  
  
Interface IContravariant(Of In T)  
End Interface  
  
Interface IInvariant(Of T)  
    Inherits ICovariant(Of T), IContravariant(Of T)  
End Interface  
```  
  
 Ancak, genel tür parametresi, `T` olan tek bir arabirimde bildirilen değişken, değişken karşıtı bildirip genişletme arabiriminde veya tam tersi. Bu aşağıdaki kod örneğinde gösterilmiştir.  
  
```vb  
Interface ICovariant(Of Out T)  
End Interface  
  
' The following statements generate a compiler error.  
' Interface ICoContraVariant(Of In T)  
'     Inherits ICovariant(Of T)  
' End Interface  
```  
  
### <a name="avoiding-ambiguity"></a>Belirsizlik kaçınma  
 Değişken genel arabirimler uyguladığınızda, varyans bazen için karışıklığa neden olabilir. Bu kaçınılmalıdır.  
  
 Örneğin, bir sınıf içinde farklı bir genel tür parametreleri ile aynı değişken genel arabirim açıkça uygularsanız, belirsizlik oluşturabilirsiniz. Derleyici bu durumda bir hata oluşturmaz, ancak çalışma zamanında hangi arabirim uygulaması seçilir belirtilmedi. Bu küçük hatalar, kodunuzda neden olabilir. Aşağıdaki kod örneği göz önünde bulundurun.  
  
> [!NOTE]
>  İle `Option Strict Off`, Visual Basic belirsiz arabirimi uygulaması olduğunda bir derleyici uyarısı oluşturur. İle `Option Strict On`, Visual Basic derleyici hatası oluşturur.  
  
```vb  
' Simple class hierarchy.  
Class Animal  
End Class  
  
Class Cat  
    Inherits Animal  
End Class  
  
Class Dog  
    Inherits Animal  
End Class  
  
' This class introduces ambiguity  
' because IEnumerable(Of Out T) is covariant.  
Class Pets  
    Implements IEnumerable(Of Cat), IEnumerable(Of Dog)  
  
    Public Function GetEnumerator() As IEnumerator(Of Cat) _  
        Implements IEnumerable(Of Cat).GetEnumerator  
        Console.WriteLine("Cat")  
        ' Some code.  
    End Function  
  
    Public Function GetEnumerator1() As IEnumerator(Of Dog) _  
        Implements IEnumerable(Of Dog).GetEnumerator  
        Console.WriteLine("Dog")  
        ' Some code.  
    End Function  
  
    Public Function GetEnumerator2() As IEnumerator _  
        Implements IEnumerable.GetEnumerator  
        ' Some code.  
    End Function  
End Class  
  
Sub Main()  
    Dim pets As IEnumerable(Of Animal) = New Pets()  
    pets.GetEnumerator()  
End Sub  
```  
  
 Bu örnekte, belirtilmeyen nasıl `pets.GetEnumerator` ücretlerinin arasında `Cat` ve `Dog`. Kodunuzda bu sorunlara neden olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Variance in Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [İşlev ve eylem genel temsilcileri (Visual Basic) için varyans kullanma](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
