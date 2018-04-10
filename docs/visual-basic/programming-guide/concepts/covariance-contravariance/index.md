---
title: Kovaryans ve kontravaryans (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59224c46-9931-466b-8c6e-3648c3e609c6
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1df3b01573ae1a9dc5c106efa5e387927c57c55f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="covariance-and-contravariance-visual-basic"></a>Kovaryans ve kontravaryans (Visual Basic)
Visual Basic'te dizi türleri, temsilci türleri ve genel tür bağımsız değişkenleri için dolaylı başvuru dönüştürme Kovaryans ve kontravaryans etkinleştirin. Kovaryans atama uyumluluğu korur ve değişken karşıtı tersine çevirir.  
  
 Aşağıdaki kod atama uyumluluğu, Kovaryans ve kontravaryans arasındaki farkı gösterir.  
  
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
  
 Kovaryans diziler için daha az türetilmiş bir tür bir dizi bir dizi daha türetilmiş bir tür örtük dönüştürme sağlar. Ancak bu işlem güvenli, aşağıdaki kod örneğinde gösterildiği gibi türünde değil.  
  
```vb  
Dim array() As Object = New String(10) {}  
' The following statement produces a run-time exception.  
' array(0) = 10  
```  
  
 Yöntem imzaları temsilci türleri ile eşleşen yöntem grupları Kovaryans ve kontravaryans desteği verir. Bu etkinleştirir, temsilcileri yalnızca imzalar, aynı zamanda türleri (kovaryans) ya da daha fazla türetilmiş döndüren yöntemler eşleşen yöntemleri atamak için temsilci türü tarafından belirtilenden daha az türetilmiş türler (kontravaryans) sahip parametreleri kabul eder. Daha fazla bilgi için bkz: [Temsilcilerde varyans (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) ve [kullanarak Temsilcilerde varyans (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).  
  
 Aşağıdaki kod örneğinde Kovaryans ve kontravaryans yöntemini grupları için destek gösterir.  
  
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
  
 .NET Framework 4 veya sonraki Visual Basic'te Kovaryans ve kontravaryans genel arabirimler ve temsilciler destekler ve genel tür parametreleri örtük dönüştürme için izin verin. Daha fazla bilgi için bkz: [genel arabirimler (Visual Basic) varyans](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) ve [Temsilcilerde varyans (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).  
  
 Aşağıdaki kod örneğinde dolaylı başvuru dönüştürme genel arabirimler için gösterir.  
  
```vb  
Dim strings As IEnumerable(Of String) = New List(Of String)  
Dim objects As IEnumerable(Of Object) = strings  
```  
  
 Genel arabirim veya temsilci adlı *değişken* genel parametreleri eşdeğişken bildirilir varsa veya karşıtı. Visual Basic, kendi değişken arabirimler ve temsilciler oluşturmanıza olanak sağlar. Daha fazla bilgi için bkz: [oluşturma değişken genel arabirimler (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) ve [Temsilcilerde varyans (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Genel arabirimler (Visual Basic) varyans](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)|Kovaryans ve kontravaryans genel arabirimler açıklanır ve .NET Framework değişken genel arabirimler listesini sağlar.|  
|[Değişken genel arabirimler oluşturma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)|Özel değişken arabirimler oluşturulacağını gösterir.|  
|[(Visual Basic) genel koleksiyonlar için arabirimlerde varyans kullanma](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)|Nasıl Kovaryans ve kontravaryans desteklemek gösterir <xref:System.Collections.Generic.IEnumerable%601> ve <xref:System.IComparable%601> arabirimleri, kodu yeniden kullanmanıza yardımcı olabilir.|  
|[Temsilcilerde varyans (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)|Kovaryans ve kontravaryans genel ve genel olmayan temsilciler açıklanır ve .NET Framework değişken genel temsilciler listesini sağlar.|  
|[Temsilcilerde varyans (Visual Basic) kullanma](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)|Kovaryans ve kontravaryans Destek genel olmayan temsilcileri yöntem imzaları temsilci türleri ile eşleşmesi için nasıl kullanılacağını gösterir.|  
|[İşlev ve eylem genel temsilciler (Visual Basic) için varyans kullanma](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)|Nasıl Kovaryans ve kontravaryans desteklemek gösterir `Func` ve `Action` Temsilciler, kodu yeniden kullanmanıza yardımcı olabilir.|
