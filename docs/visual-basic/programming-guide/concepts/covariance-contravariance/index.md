---
title: Kovaryans ve kontravaryans (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 59224c46-9931-466b-8c6e-3648c3e609c6
ms.openlocfilehash: 241b8f5864b6e9b3e1caddde25d032a24e4d0bb7
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48850458"
---
# <a name="covariance-and-contravariance-visual-basic"></a>Kovaryans ve kontravaryans (Visual Basic)
Kovaryans ve kontravaryans, Visual Basic'te, örtük bir başvuru dönüştürmesi dizi türleri, temsilci türleri ve genel tür bağımsız değişkenleri için etkinleştirin. Kovaryans atama uyumluluğu korur ve kontravaryans tersine çevirir.  
  
 Aşağıdaki kod, atama uyumluluğu, Kovaryans ve kontravaryans arasındaki farkı gösterir.  
  
```vb  
' Assignment compatibility.   
Dim str As String = "test"  
' An object of a more derived type is assigned to an object of a less derived type.   
Dim obj As Object = str  
  
' Covariance.   
Dim strings As IEnumerable(Of String) = New List(Of String)()  
' An object that is instantiated with a more derived type argument   
' is assigned to an object instantiated with a less derived type argument.   
' Assignment compatibility is preserved.   
Dim objects As IEnumerable(Of Object) = strings  
  
' Contravariance.             
' Assume that there is the following method in the class:   
' Shared Sub SetObject(ByVal o As Object)  
' End Sub  
Dim actObject As Action(Of Object) = AddressOf SetObject  
  
' An object that is instantiated with a less derived type argument   
' is assigned to an object instantiated with a more derived type argument.   
' Assignment compatibility is reversed.   
Dim actString As Action(Of String) = actObject  
```  
  
 Kovaryans diziler için daha az türetilmiş bir tür dizisini daha türetilmiş bir türde dizi örtük olarak dönüştürülmesine olanak tanır. Ancak bu işlem tür bakımından güvenli, aşağıdaki kod örneğinde gösterildiği gibi değil.  
  
```vb  
Dim array() As Object = New String(10) {}  
' The following statement produces a run-time exception.  
' array(0) = 10  
```  
  
 Kovaryans ve kontravaryans destek yöntemi gruplar için temsilci türleriyle yöntem imzalarının eşleştirilmesi için sağlar. Bu sizin için temsilciler sadece imzaları, aynı zamanda türleri (kovaryans) ya da daha fazla türetilmiş döndüren yöntemler eşleşen yöntemleri atamak için temsilci türü tarafından belirtilenden daha az türetilmiş türler (kontravaryans) sahip parametreleri kabul eder. Daha fazla bilgi için [Temsilcilerde varyans (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) ve [kullanarak Temsilcilerde varyans (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).  
  
 Kovaryans ve kontravaryans yöntemi grupları için destek, aşağıdaki kod örneği gösterilmektedir.  
  
```vb  
Shared Function GetObject() As Object  
    Return Nothing  
End Function  
  
Shared Sub SetObject(ByVal obj As Object)  
End Sub  
  
Shared Function GetString() As String  
    Return ""  
End Function  
  
Shared Sub SetString(ByVal str As String)  
  
End Sub  
  
Shared Sub Test()  
    ' Covariance. A delegate specifies a return type as object,  
    ' but you can assign a method that returns a string.  
    Dim del As Func(Of Object) = AddressOf GetString  
  
    ' Contravariance. A delegate specifies a parameter type as string,  
    ' but you can assign a method that takes an object.  
    Dim del2 As Action(Of String) = AddressOf SetObject  
End Sub  
```  
  
 .NET Framework 4 veya sonraki sürümlerde, Visual Basic içinde genel arabirimlerde ve temsilcilerde Kovaryans ve kontravaryans destekler ve genel tür parametrelerinin örtük dönüştürmelerine izin verir. Daha fazla bilgi için [Variance in Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) ve [Temsilcilerde varyans (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).  
  
 Aşağıdaki kod örneği, genel arabirimler için örtük bir başvuru dönüştürmesi gösterir.  
  
```vb  
Dim strings As IEnumerable(Of String) = New List(Of String)  
Dim objects As IEnumerable(Of Object) = strings  
```  
  
 Bir genel arabirim veya temsilci çağrılır *değişken* genel parametrelerinin birlikte değişken olarak bildirilmemişse veya değişken karşıtı. Visual Basic, kendi değişken arabirimlerde ve temsilcilerde oluşturmanızı sağlar. Daha fazla bilgi için [oluşturma değişken genel arabirimler (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) ve [Temsilcilerde varyans (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Variance in Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)|Kovaryans ve kontravaryans in generic Interfaces açıklar ve .NET Framework'teki değişken genel arabirimler bir listesini sağlar.|  
|[Değişken genel arabirimler oluşturma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)|Özel değişken arabirimler oluşturma işlemi gösterilmektedir.|  
|[(Visual Basic) genel koleksiyonlar için arabirimlerde varyans kullanma](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)|Nasıl Kovaryans ve kontravaryans desteklemek gösterir <xref:System.Collections.Generic.IEnumerable%601> ve <xref:System.IComparable%601> arabirimleri, kodu yeniden kullanmanıza yardımcı olabilir.|  
|[Temsilcilerde varyans (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)|Kovaryans ve kontravaryans, genel ve genel olmayan temsilcileri açıklar ve .NET Framework'teki genel değişken temsilciler bir listesini sağlar.|  
|[Temsilcilerde varyans (Visual Basic) kullanma](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)|Temsilci türleriyle yöntem imzalarının eşleştirmek için genel olmayan temsilcilerde Kovaryans ve kontravaryans destek kullanma işlemi gösterilmektedir.|  
|[İşlev ve eylem genel temsilcileri (Visual Basic) için varyans kullanma](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)|Nasıl Kovaryans ve kontravaryans desteklemek gösterir `Func` ve `Action` Temsilciler, kodu yeniden kullanmanıza yardımcı olabilir.|
