---
title: 'Nasıl yapılır: LINQ sorguları (Visual Basic) için özel yöntemler'
ms.date: 07/20/2015
ms.assetid: 099b2e2a-83cd-45c6-aa4d-01b398b5faaf
ms.openlocfilehash: f61db6c17fa3ead1e9dbc47c172a2cef91c042eb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59123311"
---
# <a name="how-to-add-custom-methods-for-linq-queries-visual-basic"></a>Nasıl yapılır: LINQ sorguları (Visual Basic) için özel yöntemler
İçin genişletme yöntemleri ekleyerek LINQ sorguları için kullanabileceğiniz yöntemleri kümesini genişletebilirsiniz <xref:System.Collections.Generic.IEnumerable%601> arabirimi. Örneğin, standart ortalama veya en fazla işlem ek olarak, değerler dizisinin tek bir değeri hesaplamak için özel bir toplama yöntemi oluşturabilirsiniz. Özel bir filtre veya belirli veri dönüştürme için değerler olarak çalışır ve yeni bir dizisini döndüren bir yöntemi de oluşturabilirsiniz. Bu tür yöntemler örnekler <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, ve <xref:System.Linq.Enumerable.Reverse%2A>.  
  
 Genişlettiğinizde <xref:System.Collections.Generic.IEnumerable%601> arabirimi, herhangi bir sıralanabilir koleksiyonun özel yöntemlerinizi uygulayabilirsiniz. Daha fazla bilgi için [genişletme yöntemleri](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).  
  
## <a name="adding-an-aggregate-method"></a>Bir toplama yöntemi ekleme  
 Bir toplama yöntemi, bir değerler kümesinden tek bir değer hesaplar. LINQ dahil olmak üzere çeşitli toplama yöntemleri sağlar <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, ve <xref:System.Linq.Enumerable.Max%2A>. Bir uzantı yöntemine ekleyerek kendi toplama yöntemi oluşturabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> arabirimi.  
  
 Aşağıdaki kod örneği, adında bir genişletme yöntemi oluşturma işlemi gösterilmektedir `Median` sayı türünde bir dizi için bir ORTANCA işlem `double`.  
  
```vb  
Imports System.Runtime.CompilerServices  
  
Module LINQExtension  
  
    ' Extension method for the IEnumerable(of T) interface.   
    ' The method accepts only values of the Double type.  
    <Extension()>   
    Function Median(ByVal source As IEnumerable(Of Double)) As Double  
        If source.Count = 0 Then  
            Throw New InvalidOperationException("Cannot compute median for an empty set.")  
        End If  
  
        Dim sortedSource = From number In source   
                           Order By number  
  
        Dim itemIndex = sortedSource.Count \ 2  
  
        If sortedSource.Count Mod 2 = 0 Then  
            ' Even number of items in list.  
            Return (sortedSource(itemIndex) + sortedSource(itemIndex - 1)) / 2  
        Else  
            ' Odd number of items in list.  
            Return sortedSource(itemIndex)  
        End If  
    End Function  
End Module  
```  
  
 Aynı şekilde diğer toplama yöntemleri çağırmak için herhangi bir sıralanabilir koleksiyonun bu uzantı metodu çağırma <xref:System.Collections.Generic.IEnumerable%601> arabirimi.  
  
> [!NOTE]
>  Visual Basic'te ya da bir yöntem çağrısı veya standart sorgu söz dizimi için kullanabileceğiniz `Aggregate` veya `Group By` yan tümcesi. Daha fazla bilgi için [Aggregate tümcesi](../../../../visual-basic/language-reference/queries/aggregate-clause.md) ve [Group yan tümcesi tarafından](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
 Aşağıdaki kod örneği kullanma işlemini gösterir `Median` türünde bir dizi yöntemi `double`.  
  
```vb  
Dim numbers1() As Double = {1.9, 2, 8, 4, 5.7, 6, 7.2, 0}  
  
Dim query1 = Aggregate num In numbers1 Into Median()  
  
Console.WriteLine("Double: Median = " & query1)  
```  
  
```vb  
' This code produces the following output:  
'  
' Double: Median = 4.85  
```  

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a>Çeşitli türleri kabul etmek için bir toplama yöntemi aşırı yüklemesi  
 Böylece dizileri çeşitli türlerde kabul ettiğiniz toplama yöntemi aşırı yüklenebilir. Standart bir yaklaşım, her tür için bir aşırı oluşturmaktır. Başka bir yaklaşım genel bir tür olması ve temsilci kullanarak belirli bir türe dönüştürme aşırı oluşturmaktır. Ayrıca, iki yaklaşımı birleştirebilirsiniz.  
  
#### <a name="to-create-an-overload-for-each-type"></a>Her tür için bir aşırı yükleme oluşturmak için  
 Desteklemek istediğiniz her bir türü için belirli bir aşırı yükleme oluşturabilirsiniz. Aşağıdaki kod örneği bir aşırı yüklemesini gösterir `Median` yöntemi `integer` türü.  
  
```vb  
' Integer overload  
  
<Extension()>   
Function Median(ByVal source As IEnumerable(Of Integer)) As Double  
    Return Aggregate num In source Select CDbl(num) Into med = Median()  
End Function  
```  
 Artık çağırabilirsiniz `Median` hem de aşırı `integer` ve `double` türleri, aşağıdaki kodda gösterildiği gibi:  
  
```vb  
Dim numbers1() As Double = {1.9, 2, 8, 4, 5.7, 6, 7.2, 0}  
  
Dim query1 = Aggregate num In numbers1 Into Median()  
  
Console.WriteLine("Double: Median = " & query1)  
```  
  
```vb  
Dim numbers2() As Integer = {1, 2, 3, 4, 5}  
  
Dim query2 = Aggregate num In numbers2 Into Median()  
  
Console.WriteLine("Integer: Median = " & query2)  
```  
  
```vb  
' This code produces the following output:  
'  
' Double: Median = 4.85  
' Integer: Median = 3  
```  

#### <a name="to-create-a-generic-overload"></a>Genel bir aşırı yükleme oluşturmak için  
 Genel nesneler dizisi kabul eden bir aşırı yüklemeyi de oluşturabilirsiniz. Bu aşırı yükleme, bir temsilci bir parametre olarak alır ve genel bir türün nesnelerinin bir dizisi belirli bir türe dönüştürmek için kullanır.  
  
 Aşağıdaki kod, bir aşırı yüklemesini göstermektedir `Median` gereken yöntemini <xref:System.Func%602> temsilci bir parametre olarak. Bu temsilci T genel türünün bir nesnesini alır ve türünde bir nesne döndürür `double`.  
  
```vb  
' Generic overload.  
  
<Extension()>   
Function Median(Of T)(ByVal source As IEnumerable(Of T),   
                      ByVal selector As Func(Of T, Double)) As Double  
    Return Aggregate num In source Select selector(num) Into med = Median()  
End Function  
```  
  
 Artık çağırabilirsiniz `Median` herhangi bir türde nesneler dizisi için yöntemi. Türü kendi yöntemi aşırı yüklemesini yoksa bir temsilci parametresi geçirmek zorunda. Visual Basic'te, bir lambda ifadesi bu amaç için kullanabilirsiniz. Ayrıca, kullanırsanız `Aggregate` veya `Group By` yan tümcesi yerine bir yöntem çağrısı, herhangi bir değer veya kapsamda bu yan tümce ifadesi iletebilir.  
  
 Aşağıdaki kod örneği nasıl çağrılacağını gösterir `Median` yöntemi için tamsayı dizisi ve dize dizisi. Dizeler için dize dizisinde uzunluklarının için ORTANCA hesaplanır. Bu örnek nasıl geçirileceğini gösterir <xref:System.Func%602> temsilci parametresi `Median` her örneği için yöntemi.  
  
```vb  
Dim numbers3() As Integer = {1, 2, 3, 4, 5}  
  
' You can use num as a parameter for the Median method   
' so that the compiler will implicitly convert its value to double.  
' If there is no implicit conversion, the compiler will  
' display an error message.  
  
Dim query3 = Aggregate num In numbers3 Into Median(num)  
  
Console.WriteLine("Integer: Median = " & query3)  
  
Dim numbers4() As String = {"one", "two", "three", "four", "five"}  
  
' With the generic overload, you can also use numeric properties of objects.  
  
Dim query4 = Aggregate str In numbers4 Into Median(str.Length)  
  
Console.WriteLine("String: Median = " & query4)  
  
' This code produces the following output:  
'  
' Integer: Median = 3  
' String: Median = 4  
```  
## <a name="adding-a-method-that-returns-a-collection"></a>Bir koleksiyonu döndüren bir yöntem ekleme  
 Genişletebileceğiniz <xref:System.Collections.Generic.IEnumerable%601> değerlerini bir dizi döndürür bir özel sorgu yöntemi ile arabirim. Bu durumda, yöntem türü bir koleksiyon döndürmelidir <xref:System.Collections.Generic.IEnumerable%601>. Bu tür yöntemler, değerler dizisi için filtre veya veri dönüşüm uygulamak için kullanılabilir.  
  
 Aşağıdaki örnekte adlı bir genişletme yöntemi oluşturma işlemi gösterilmektedir `AlternateElements` ilk öğesinden başlayarak, bir koleksiyondaki her bir öğe döndürür.  
  
```vb  
' Extension method for the IEnumerable(of T) interface.   
' The method returns every other element of a sequence.  
  
<Extension()>   
Function AlternateElements(Of T)(  
    ByVal source As IEnumerable(Of T)  
    ) As IEnumerable(Of T)  
  
    Dim list As New List(Of T)  
    Dim i = 0  
    For Each element In source  
        If (i Mod 2 = 0) Then  
            list.Add(element)  
        End If  
        i = i + 1  
    Next  
    Return list  
End Function  
```  
 Gibi diğer yöntemleri çağırmak bu genişletme yöntemi için herhangi bir sıralanabilir koleksiyonun çağırabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> aşağıdaki kodda gösterildiği gibi arabirim:  
  
```vb  
Dim strings() As String = {"a", "b", "c", "d", "e"}  
  
Dim query = strings.AlternateElements()  
  
For Each element In query  
    Console.WriteLine(element)  
Next  
  
' This code produces the following output:  
'  
' a  
' c  
' e  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic.IEnumerable%601>
- [Genişletme Yöntemleri](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
