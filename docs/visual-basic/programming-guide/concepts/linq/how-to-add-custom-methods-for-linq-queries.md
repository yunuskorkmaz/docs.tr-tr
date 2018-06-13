---
title: 'Nasıl yapılır: özel yöntemler ekleme LINQ sorgularını (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 099b2e2a-83cd-45c6-aa4d-01b398b5faaf
ms.openlocfilehash: 6fa212ff05547e8edd3964a6e1c9f76c11cdbe08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644062"
---
# <a name="how-to-add-custom-methods-for-linq-queries-visual-basic"></a>Nasıl yapılır: özel yöntemler ekleme LINQ sorgularını (Visual Basic)
İçin genişletme yöntemleri ekleyerek LINQ sorguları için kullanabileceğiniz yöntemler kümesi genişletebilirsiniz <xref:System.Collections.Generic.IEnumerable%601> arabirimi. Örneğin, standart ortalama veya en fazla işlemlerinin yanı sıra, değerlerin bir sırasından tek bir değeri hesaplamak için özel bir toplama yöntemi oluşturabilirsiniz. Özel filtre veya değerleri dizisi için belirli veri dönüştürme olarak çalışır ve yeni sırası döndüren bir yöntem de oluşturabilirsiniz. Bu tür yöntemler örnekleridir <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, ve <xref:System.Linq.Enumerable.Reverse%2A>.  
  
 Genişlettiğinizde <xref:System.Collections.Generic.IEnumerable%601> arabirimi, özel yöntemlerinizi herhangi numaralandırılabilir koleksiyonuna uygulayabilirsiniz. Daha fazla bilgi için bkz: [genişletme yöntemleri](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).  
  
## <a name="adding-an-aggregate-method"></a>Toplama yöntemi ekleme  
 Birleşik bir yöntemi, bir değerler kümesinden tek bir değer hesaplar. LINQ sağlar dahil olmak üzere birkaç toplama yöntemleri <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, ve <xref:System.Linq.Enumerable.Max%2A>. Bir genişletme yöntemi ekleyerek toplama yönteminizi oluşturabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> arabirimi.  
  
 Aşağıdaki kod örneği olarak adlandırılan bir genişletme yöntemi oluşturulacağını gösterir `Median` ORTANCA bir dizi sayı türü için işlem için `double`.  
  
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
  
 Toplam diğer yöntemleri çağırmak aynı şekilde numaralandırılabilir herhangi bir koleksiyon için bu uzantı metodu çağırma <xref:System.Collections.Generic.IEnumerable%601> arabirimi.  
  
> [!NOTE]
>  Visual Basic'te ya da bir yöntem çağrısı veya standart sorgu sözdizimi için kullanabileceğiniz `Aggregate` veya `Group By` yan tümcesi. Daha fazla bilgi için bkz: [Aggregate tümcesi](../../../../visual-basic/language-reference/queries/aggregate-clause.md) ve [Grup By yan tümcesi](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
 Aşağıdaki kod örneğinde nasıl kullanılacağını gösterir `Median` türünde bir dizi yöntem `double`.  
  
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
  

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a>Çeşitli türlerini kabul edecek şekilde bir toplama yöntemi aşırı yüklemesi  
 Toplama yöntemi aşırı yükleme çeşitli türlerdeki dizilerini kabul. Standart yaklaşımı, her tür için bir aşırı oluşturmaktır. Başka bir yaklaşım, genel bir tür olması ve bir temsilci kullanarak belirli bir türe dönüştürmek aşırı oluşturmaktır. Ayrıca, her iki yaklaşımın da birleştirebilirsiniz.  
  
#### <a name="to-create-an-overload-for-each-type"></a>Her tür için bir aşırı oluşturmak için  
 Desteklemek istediğiniz her bir türü için belirli bir aşırı oluşturabilirsiniz. Aşağıdaki kod örneğinde bir aşırı yüklemesini gösterir `Median` yöntemi `integer` türü.  
  
```vb  
' Integer overload  
  
<Extension()>   
Function Median(ByVal source As IEnumerable(Of Integer)) As Double  
    Return Aggregate num In source Select CDbl(num) Into med = Median()  
End Function  
```  
 Şimdi Ara `Median` her ikisi için de aşırı `integer` ve `double` aşağıdaki kodda gösterildiği gibi türleri:  
  
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
  
 
#### <a name="to-create-a-generic-overload"></a>Bir genel aşırı oluşturmak için  
 Genel nesneler dizisi kabul eden bir aşırı de oluşturabilirsiniz. Bu aşırı temsilci bir parametre olarak alır ve belirli bir türe genel bir tür nesnelerin bir dizi dönüştürmek için kullanır.  
  
 Aşağıdaki kod bir aşırı yüklemesini gösterir `Median` yönteminin alan <xref:System.Func%602> temsilci parametre olarak. Bu temsilci T genel türünde bir nesne alır ve türünde bir nesne döndürür `double`.  
  
```vb  
' Generic overload.  
  
<Extension()>   
Function Median(Of T)(ByVal source As IEnumerable(Of T),   
                      ByVal selector As Func(Of T, Double)) As Double  
    Return Aggregate num In source Select selector(num) Into med = Median()  
End Function  
```  
  
 Şimdi Ara `Median` herhangi bir türde nesnelerinin bir dizisi için yöntem. Türü kendi yöntemi aşırı yüklemesini yoksa bir temsilci parametre geçirmek zorunda. Visual Basic'te, bu amaçla bir lambda ifadesi kullanabilirsiniz. Ayrıca, kullanırsanız `Aggregate` veya `Group By` yöntem çağrısının yerine yan tümcesi, herhangi bir değer veya bu yan tümce kapsamı içinde olan deyimi iletebilir.  
  
 Aşağıdaki kod örneği nasıl çağrılacağını gösterir `Median` yöntemi dizisi ve bir dizeler dizisi. Dizeler için dizi dizelerde uzunlukları ORTANCA hesaplanır. Örnek nasıl iletileceğini gösterir <xref:System.Func%602> temsilci parametresi `Median` yöntemi her örneği için.  
  
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
 Genişletebilirsiniz <xref:System.Collections.Generic.IEnumerable%601> arabirimi bir özel sorgu yöntemiyle değerleri dizisi döndürür. Bu durumda, yöntem bir koleksiyon türü döndürmelidir <xref:System.Collections.Generic.IEnumerable%601>. Bu tür yöntemleri değerleri dizisi için filtre ya da veri dönüşüm uygulamak için kullanılabilir.  
  
 Aşağıdaki örnek adlı bir genişletme yöntemi oluşturulacağını gösterir `AlternateElements` ilk öğesinden başlayarak, bir koleksiyondaki her bir öğe getirir.  
  
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
 Diğer yöntemleri çağırmak gibi herhangi bir numaralandırılabilir koleksiyonu için bu genişletme yöntemi çağırabilir <xref:System.Collections.Generic.IEnumerable%601> aşağıdaki kodda gösterildiği gibi arabirim:  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [Genişletme Yöntemleri](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
