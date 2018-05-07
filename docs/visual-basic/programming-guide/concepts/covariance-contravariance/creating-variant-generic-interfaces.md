---
title: Değişken genel arabirimler oluşturma (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d4037dd2-dfe9-4811-9150-93d4e8b20113
ms.openlocfilehash: 9e79183cd75e3e222cfa82c6b8ca651eb99ffc02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="creating-variant-generic-interfaces-visual-basic"></a>Değişken genel arabirimler oluşturma (Visual Basic)
Genel tür parametreleri eşdeğişken olarak arabirimlerdeki bildirebilir veya karşıtı. *Kovaryans* dönüş türleri genel tür parametreleri tarafından tanımlanan daha fazla türetilmiş arabirim yöntemleri sağlar. *Değişken karşıtı* genel parametreler tarafından belirtilenden daha az türetilmiş bağımsız değişken türleri arabirim yöntemleri sağlar. Eşdeğişken sahip genel arabirim veya karşıtı genel tür parametreleri çağrılır *değişken*.  
  
> [!NOTE]
>  .NET framework 4 birkaç mevcut genel arabirimler sapma desteği sunmuştur. .NET Framework'teki değişken arabirimler listesi için bkz: [genel arabirimler (Visual Basic) varyans](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).  
  
## <a name="declaring-variant-generic-interfaces"></a>Bildiren değişken genel arabirimler  
 Değişken genel arabirimler kullanarak bildirebilirsiniz `in` ve `out` genel tür parametreleri için anahtar sözcükler.  
  
> [!IMPORTANT]
>  `ByRef` Visual Basic'de değişken olamaz. Türlerin varyans da desteklemez.  
  
 Genel tür parametresi eşdeğişken kullanarak bildirebilirsiniz `out` anahtar sözcüğü. Eşdeğişken türü aşağıdaki koşulları karşılaması gerekir:  
  
-   Türü yalnızca bir dönüş türü arabirim yöntemleri olarak kullanılan ve yöntem bağımsız değişkenleri bir tür olarak kullanılmaz. Bu, aşağıdaki örnekte gösterilmiştir türü `R` eşdeğişken bildirilir.  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        Function GetSomething() As R  
        ' The following statement generates a compiler error.  
        ' Sub SetSomething(ByVal sampleArg As R)  
    End Interface  
    ```  
  
     Bu kural için bir istisna vardır. Karşıtı Genel temsilci bir yöntem parametresi olarak varsa, türü için temsilci genel tür parametresi olarak kullanabilirsiniz. Bu türü tarafından gösterilen `R` aşağıdaki örnekte. Daha fazla bilgi için bkz: [Temsilcilerde varyans (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) ve [işlev ve eylem genel temsilciler (Visual Basic) kullanarak varyansını](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        Sub DoSomething(ByVal callback As Action(Of R))  
    End Interface  
    ```  
  
-   Türü, arabirim yöntemleri için genel bir kısıtlama olarak kullanılmaz. Bu aşağıdaki kodda gösterilmiştir.  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        ' The following statement generates a compiler error  
        ' because you can use only contravariant or invariant types  
        ' in generic contstraints.  
        ' Sub DoSomething(Of T As R)()  
    End Interface  
    ```  
  
 Genel tür parametresi karşıtı kullanarak bildirebilirsiniz `in` anahtar sözcüğü. Karşıtı türü arabirim yöntemleri dönüş türü olarak değil de yalnızca yöntem bağımsız değişkenleri bir tür olarak kullanılabilir. Karşıtı türü, genel kısıtlamalar için de kullanılabilir. Aşağıdaki kod karşıtı arabirimi bildirin ve genel bir kısıtlama yöntemlerinden biri için nasıl kullanılacağını gösterir.  
  
```vb  
Interface IContravariant(Of In A)  
    Sub SetSomething(ByVal sampleArg As A)  
    Sub DoSomething(Of T As A)()  
    ' The following statement generates a compiler error.  
    ' Function GetSomething() As A  
End Interface  
```  
  
 Ayrıca aşağıdaki kod örneğinde gösterildiği gibi farklı tür parametreleri yanı sıra, aynı arabiriminde Kovaryans ve kontravaryans desteklemek mümkündür.  
  
```vb  
Interface IVariant(Of Out R, In A)  
    Function GetSomething() As R  
    Sub SetSomething(ByVal sampleArg As A)  
    Function GetSetSomething(ByVal sampleArg As A) As R  
End Interface  
```  
  
 Visual Basic'te temsilci türü belirtmeden değişken arabirimler olayları bildiremezsiniz. Ayrıca, bir değişken arabirimi sınıfları, numaralandırmaları ve yapıları iç içe geçmiş olamaz, ancak arabirimleri içe. Bu aşağıdaki kodda gösterilmiştir.  
  
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
  
## <a name="implementing-variant-generic-interfaces"></a>Uygulama değişken genel arabirimler  
 Değişken genel arabirimler değişmez arabirimleri için kullanılan aynı sözdizimini kullanarak sınıflarda uygulayın. Aşağıdaki kod örneğinde, genel bir sınıf bir eşdeğişken arabirimini uygulayan gösterilmektedir.  
  
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
  
 Değişken arabirimler uygulayan sınıflar değişmez. Örneğin, aşağıdaki kodu göz önünde bulundurun.  
  
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
 Değişken genel bir arabirim genişlettiğinizde kullanmak zorunda `in` ve `out` açıkça türetilmiş bir arabirim farkı destekleyip desteklemediğini belirlemek için anahtar sözcükler. Derleyici genişletilen arabiriminden varyansı Infer değil. Örneğin, aşağıdaki arabirimleri göz önünde bulundurun.  
  
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
  
 İçinde `Invariant(Of T)` arabirim, genel tür parametresi `T` değişmez, olan ancak içinde `IExtCovariant (Of Out T)`aynı arabirimi her iki arabirimde genişletmek rağmen tür parametresi değişkendir. Aynı kural karşıtı genel tür parametreleri için uygulanır.  
  
 Genel parametre girildiği iki arabirim genişleten bir arabirim oluşturabilirsiniz `T` değişkendir ve varsa genişletme içinde karşıtı olduğu arabirimi arabirim genel tür parametresi `T` sabit değil. Bu aşağıdaki kod örneğinde gösterilmiştir.  
  
```vb  
Interface ICovariant(Of Out T)  
End Interface  
  
Interface IContravariant(Of In T)  
End Interface  
  
Interface IInvariant(Of T)  
    Inherits ICovariant(Of T), IContravariant(Of T)  
End Interface  
```  
  
 Ancak, genel türde bir parametre değilse `T` olan bir arabiriminde eşdeğişken bildirilen, siz onu karşıtı bildiremezsiniz genişletme arabiriminde veya tersi. Bu aşağıdaki kod örneğinde gösterilmiştir.  
  
```vb  
Interface ICovariant(Of Out T)  
End Interface  
  
' The following statements generate a compiler error.  
' Interface ICoContraVariant(Of In T)  
'     Inherits ICovariant(Of T)  
' End Interface  
```  
  
### <a name="avoiding-ambiguity"></a>Belirsizliği önleme  
 Değişken genel arabirimler uyguladığınızda farkı bazen belirsizlik için yol açabilir. Bu kaçınılmalıdır.  
  
 Örneğin, bir sınıf tarafından açıkça farklı genel tür parametreleri ile aynı değişken genel arabirim uygularsanız, belirsizlik oluşturabilirsiniz. Derleyici bir hata bu durumda üretmez, ancak çalışma zamanında hangi arabirim uygulamasına seçilir belirtilmedi. Bu, kodunuzda Zarif hataları neden olabilir. Aşağıdaki kod örneği göz önünde bulundurun.  
  
> [!NOTE]
>  İle `Option Strict Off`, Visual Basic belirsiz arabirim uygulamasına olduğunda bir derleyici uyarı oluşturur. İle `Option Strict On`, Visual Basic derleyici hatası oluşturur.  
  
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
  
 Bu örnekte, belirtilmeyen nasıl `pets.GetEnumerator` ücretlerinin arasında `Cat` ve `Dog`. Bu, kodunuzda sorunlara neden olabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Genel arabirimler (Visual Basic) varyans](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [İşlev ve eylem genel temsilciler (Visual Basic) için varyans kullanma](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
