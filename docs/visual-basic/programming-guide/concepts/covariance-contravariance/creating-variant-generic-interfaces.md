---
title: Değişken Genel Arabirimler Oluşturma
ms.date: 07/20/2015
ms.assetid: d4037dd2-dfe9-4811-9150-93d4e8b20113
ms.openlocfilehash: 74362b9d9effab028bebb9e9ecf72ac0111366d3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347063"
---
# <a name="creating-variant-generic-interfaces-visual-basic"></a>Değişken genel arabirimler oluşturma (Visual Basic)

Arabirimlerdeki genel tür parametrelerini birlikte değişken veya değişken karşıtı olarak bildirebilirsiniz. *Kovaryans* , Arabirim yöntemlerinin genel tür parametreleri tarafından tanımlananla daha fazla türetilmiş dönüş türüne sahip olmasına izin verir. *Değişken varyans* , Arabirim yöntemlerinin genel parametreler tarafından belirtilenden daha az türetilmiş bağımsız değişken türlerine sahip olmasına olanak sağlar. Değişkenle birlikte değişken veya değişken karşıtı genel tür parametrelerine sahip genel bir arabirim *değişken*olarak adlandırılır.

> [!NOTE]
> .NET Framework 4, mevcut birçok genel arabirim için varyans desteği getirmiştir. .NET Framework değişken arabirimlerinin listesi için bkz. [Genel Arabirimlerde Varyans (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).

## <a name="declaring-variant-generic-interfaces"></a>VARIANT genel arabirimlerini bildirme

Genel tür parametreleri için `in` ve `out` anahtar sözcüklerini kullanarak VARIANT genel arabirimleri bildirebilirsiniz.

> [!IMPORTANT]
> Visual Basic `ByRef` parametreler Variant olamaz. Değer türleri de varyansı desteklemez.

`out` anahtar sözcüğünü kullanarak genel tür parametresi ortak değişkeni bildirebilirsiniz. Covaryant türü şu koşulları karşılamalıdır:

- Tür, yalnızca Arabirim yöntemlerinin dönüş türü olarak kullanılır ve Yöntem bağımsız değişkenlerinin türü olarak kullanılmaz. Bu, `R` türünün covaryant olarak bildirildiği aşağıdaki örnekte gösterilmiştir.

    ```vb
    Interface ICovariant(Of Out R)
        Function GetSomething() As R
        ' The following statement generates a compiler error.
        ' Sub SetSomething(ByVal sampleArg As R)
    End Interface
    ```

    Bu kural için bir özel durum var. Bir yöntem parametresi olarak bir değişken karşıtı genel temsilciniz varsa, türü temsilci için genel bir tür parametresi olarak kullanabilirsiniz. Bu, aşağıdaki örnekte `R` türü tarafından gösterilmiştir. Daha fazla bilgi için bkz. [Temsilcilerde varyans (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) ve [Func ve eylem genel temsilcileri için varyans kullanma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).

    ```vb
    Interface ICovariant(Of Out R)
        Sub DoSomething(ByVal callback As Action(Of R))
    End Interface
    ```

- Tür, arabirim yöntemleri için genel bir kısıtlama olarak kullanılmaz. Bu, aşağıdaki kodda gösterilmiştir.

    ```vb
    Interface ICovariant(Of Out R)
        ' The following statement generates a compiler error
        ' because you can use only contravariant or invariant types
        ' in generic constraints.
        ' Sub DoSomething(Of T As R)()
    End Interface
    ```

`in` anahtar sözcüğünü kullanarak genel tür parametresi değişken karşıtı bildirebilirsiniz. Değişken karşıtı türü, Arabirim yöntemlerinin dönüş türü olarak değil, yalnızca Yöntem bağımsız değişkenlerinin türü olarak kullanılabilir. Değişken karşıtı türü, genel kısıtlamalar için de kullanılabilir. Aşağıdaki kod, bir değişken karşıtı arabirimin nasıl bildirilemeyeceğini ve yöntemlerinden biri için genel bir kısıtlama nasıl kullanıldığını gösterir.

```vb
Interface IContravariant(Of In A)
    Sub SetSomething(ByVal sampleArg As A)
    Sub DoSomething(Of T As A)()
    ' The following statement generates a compiler error.
    ' Function GetSomething() As A
End Interface
```

Ayrıca, aşağıdaki kod örneğinde gösterildiği gibi farklı tür parametreleri için aynı arabirimdeki kovaryansı ve değişken varyansı desteklemek de mümkündür.

```vb
Interface IVariant(Of Out R, In A)
    Function GetSomething() As R
    Sub SetSomething(ByVal sampleArg As A)
    Function GetSetSomething(ByVal sampleArg As A) As R
End Interface
```

Visual Basic, temsilci türünü belirtmeden değişken arabirimlerde olayları bildiremezsiniz. Ayrıca, bir değişken arabirimde iç içe sınıflar, numaralandırmalar veya yapılar bulunamaz, ancak iç içe arabirimler olabilir. Bu, aşağıdaki kodda gösterilmiştir.

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

## <a name="implementing-variant-generic-interfaces"></a>VARIANT genel arabirimlerini uygulama

Sabit arabirimler için kullanılan söz dizimini kullanarak sınıflarda VARIANT genel arabirimler uygulayabilirsiniz. Aşağıdaki kod örneği, bir genel sınıfta birlikte değişken arabiriminin nasıl uygulanacağını gösterir.

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

Varyant arabirimlerini uygulayan sınıflar sabit. Örneğin, aşağıdaki kodu göz önünde bulundurun.

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

## <a name="extending-variant-generic-interfaces"></a>VARIANT genel arabirimlerini genişletme

Bir varyant genel arabirimini genişlettiğinizde, türetilmiş arabirimin varyansı destekleyip desteklemediğini açıkça belirtmek için `in` ve `out` anahtar sözcüklerini kullanmanız gerekir. Derleyici, genişletilmekte olan arabirimden varyansı çıkarmıyor. Örneğin, aşağıdaki arabirimleri göz önünde bulundurun.

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

`Invariant(Of T)` arabiriminde, `T` genel tür parametresi değişmez, ancak her iki arabirim de aynı arabirimi genişletse de, tür parametresi birlikte değişken `IExtCovariant (Of Out T)`. Aynı kural, değişken karşıtı genel tür parametrelerine uygulanır.

Hem genel tür parametresi `T` birlikte değişken olduğu arabirimi hem de genişletme arabiriminde `T` genel tür parametresi sabiti olan arabirimi genişleten bir arabirim oluşturabilirsiniz. Bu, aşağıdaki kod örneğinde gösterilmiştir.

```vb
Interface ICovariant(Of Out T)
End Interface

Interface IContravariant(Of In T)
End Interface

Interface IInvariant(Of T)
    Inherits ICovariant(Of T), IContravariant(Of T)
End Interface
```

Ancak, bir genel tür parametresi `T` bir arabirimde birlikte değişken olarak bildirilirse, genişletme arabiriminde bu değişken karşıtı olarak bildiremezsiniz veya tam tersi de geçerlidir. Bu, aşağıdaki kod örneğinde gösterilmiştir.

```vb
Interface ICovariant(Of Out T)
End Interface

' The following statements generate a compiler error.
' Interface ICoContraVariant(Of In T)
'     Inherits ICovariant(Of T)
' End Interface
```

### <a name="avoiding-ambiguity"></a>Belirsizlik önleme

VARIANT genel arabirimleri uyguladığınızda, fark bazen belirsizliğe neden olabilir. Bunun kaçınılması gerekir.

Örneğin, tek bir sınıfta farklı genel tür parametreleriyle aynı Varyant genel arabirimini açıkça uygularsanız, belirsizlik oluşturabilir. Derleyici bu durumda bir hata oluşturmaz, ancak çalışma zamanında hangi arabirim uygulamasının seçilme belirtilecektir. Bu, kodunuzda hafif hatalara neden olabilir. Aşağıdaki kod örneğini göz önünde bulundurun.

> [!NOTE]
> `Option Strict Off`, belirsiz bir arabirim uygulaması olduğunda Visual Basic bir derleyici uyarısı oluşturur. `Option Strict On`, Visual Basic bir derleyici hatası oluşturur.

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

Bu örnekte, `pets.GetEnumerator` yönteminin `Cat` ve `Dog`arasında nasıl seçtiği belirtilmemiş. Bu, kodunuzda sorun oluşmasına neden olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Genel Arabirimlerde Varyans (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [Func ve eylem genel temsilcileri için varyans kullanma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
