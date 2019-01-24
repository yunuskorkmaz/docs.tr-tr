---
title: 'Nasıl yapılır: LINQ sorguları için özel yöntemler ekleme (C#)'
ms.date: 07/20/2015
ms.assetid: 1a500f60-2e10-49fb-8b2a-d8d08e4817cb
ms.openlocfilehash: 0c90e869c3d56696a072585cca7282b459b39e07
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540734"
---
# <a name="how-to-add-custom-methods-for-linq-queries-c"></a>Nasıl yapılır: LINQ sorguları için özel yöntemler ekleme (C#)
İçin genişletme yöntemleri ekleyerek LINQ sorguları için kullanabileceğiniz yöntemleri kümesini genişletebilirsiniz <xref:System.Collections.Generic.IEnumerable%601> arabirimi. Örneğin, standart ortalama veya en fazla işlem ek olarak, değerler dizisinin tek bir değeri hesaplamak için özel bir toplama yöntemi oluşturabilirsiniz. Özel bir filtre veya belirli veri dönüştürme için değerler olarak çalışır ve yeni bir dizisini döndüren bir yöntemi de oluşturabilirsiniz. Bu tür yöntemler örnekler <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, ve <xref:System.Linq.Enumerable.Reverse%2A>.  
  
 Genişlettiğinizde <xref:System.Collections.Generic.IEnumerable%601> arabirimi, herhangi bir sıralanabilir koleksiyonun özel yöntemlerinizi uygulayabilirsiniz. Daha fazla bilgi için [genişletme yöntemleri](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).  
  
## <a name="adding-an-aggregate-method"></a>Bir toplama yöntemi ekleme  
 Bir toplama yöntemi, bir değerler kümesinden tek bir değer hesaplar. LINQ dahil olmak üzere çeşitli toplama yöntemleri sağlar <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, ve <xref:System.Linq.Enumerable.Max%2A>. Bir uzantı yöntemine ekleyerek kendi toplama yöntemi oluşturabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> arabirimi.  
  
 Aşağıdaki kod örneği, adında bir genişletme yöntemi oluşturma işlemi gösterilmektedir `Median` sayı türünde bir dizi için bir ORTANCA işlem `double`.  
  
```csharp  
public static class LINQExtension  
{  
    public static double Median(this IEnumerable<double> source)  
    {  
        if (source.Count() == 0)  
        {  
            throw new InvalidOperationException("Cannot compute median for an empty set.");  
        }  
  
        var sortedList = from number in source  
                         orderby number  
                         select number;  
  
        int itemIndex = (int)sortedList.Count() / 2;  
  
        if (sortedList.Count() % 2 == 0)  
        {  
            // Even number of items.  
            return (sortedList.ElementAt(itemIndex) + sortedList.ElementAt(itemIndex - 1)) / 2;  
        }  
        else  
        {  
            // Odd number of items.  
            return sortedList.ElementAt(itemIndex);  
        }  
    }  
}  
```  
  
 Aynı şekilde diğer toplama yöntemleri çağırmak için herhangi bir sıralanabilir koleksiyonun bu uzantı metodu çağırma <xref:System.Collections.Generic.IEnumerable%601> arabirimi.  
  
 Aşağıdaki kod örneği kullanma işlemini gösterir `Median` türünde bir dizi yöntemi `double`.  
  
```csharp  
double[] numbers1 = { 1.9, 2, 8, 4, 5.7, 6, 7.2, 0 };  
  
var query1 = numbers1.Median();  
  
Console.WriteLine("double: Median = " + query1);  
```  

```csharp  
/*  
 This code produces the following output:  
  
 Double: Median = 4.85  
*/  
```  
  
### <a name="overloading-an-aggregate-method-to-accept-various-types"></a>Çeşitli türleri kabul etmek için bir toplama yöntemi aşırı yüklemesi  
 Böylece dizileri çeşitli türlerde kabul ettiğiniz toplama yöntemi aşırı yüklenebilir. Standart bir yaklaşım, her tür için bir aşırı oluşturmaktır. Başka bir yaklaşım genel bir tür olması ve temsilci kullanarak belirli bir türe dönüştürme aşırı oluşturmaktır. Ayrıca, iki yaklaşımı birleştirebilirsiniz.  
  
#### <a name="to-create-an-overload-for-each-type"></a>Her tür için bir aşırı yükleme oluşturmak için  
 Desteklemek istediğiniz her bir türü için belirli bir aşırı yükleme oluşturabilirsiniz. Aşağıdaki kod örneği bir aşırı yüklemesini gösterir `Median` yöntemi `integer` türü.  
  
```csharp  
//int overload  
  
public static double Median(this IEnumerable<int> source)  
{  
    return (from num in source select (double)num).Median();  
}  
```   
 Artık çağırabilirsiniz `Median` hem de aşırı `integer` ve `double` türleri, aşağıdaki kodda gösterildiği gibi:  
  
```csharp  
double[] numbers1 = { 1.9, 2, 8, 4, 5.7, 6, 7.2, 0 };  
  
var query1 = numbers1.Median();  
  
Console.WriteLine("double: Median = " + query1);  
```  
  
```csharp  
int[] numbers2 = { 1, 2, 3, 4, 5 };  
  
var query2 = numbers2.Median();  
  
Console.WriteLine("int: Median = " + query2);  
```  
  
```csharp  
/*  
 This code produces the following output:  
  
 Double: Median = 4.85  
 Integer: Median = 3  
*/  
```  

#### <a name="to-create-a-generic-overload"></a>Genel bir aşırı yükleme oluşturmak için  
 Genel nesneler dizisi kabul eden bir aşırı yüklemeyi de oluşturabilirsiniz. Bu aşırı yükleme, bir temsilci bir parametre olarak alır ve genel bir türün nesnelerinin bir dizisi belirli bir türe dönüştürmek için kullanır.  
  
 Aşağıdaki kod, bir aşırı yüklemesini göstermektedir `Median` gereken yöntemini <xref:System.Func%602> temsilci bir parametre olarak. Bu temsilci T genel türünün bir nesnesini alır ve türünde bir nesne döndürür `double`.  
  
```csharp  
// Generic overload.  
  
public static double Median<T>(this IEnumerable<T> numbers,  
                       Func<T, double> selector)  
{  
    return (from num in numbers select selector(num)).Median();  
}  
```  
  
 Artık çağırabilirsiniz `Median` herhangi bir türde nesneler dizisi için yöntemi. Türü kendi yöntemi aşırı yüklemesini yoksa bir temsilci parametresi geçirmek zorunda. C# içinde bir lambda ifadesi bu amaç için kullanabilirsiniz. Ayrıca, yalnızca Visual Basic'te, kullanırsanız `Aggregate` veya `Group By` yan tümcesi yerine bir yöntem çağrısı, herhangi bir değer veya kapsamda bu yan tümce ifadesi iletebilir.  
  
 Aşağıdaki kod örneği nasıl çağrılacağını gösterir `Median` yöntemi için tamsayı dizisi ve dize dizisi. Dizeler için dize dizisinde uzunluklarının için ORTANCA hesaplanır. Bu örnek nasıl geçirileceğini gösterir <xref:System.Func%602> temsilci parametresi `Median` her örneği için yöntemi.  
  
```csharp  
int[] numbers3 = { 1, 2, 3, 4, 5 };  
  
/*   
  You can use the num=>num lambda expression as a parameter for the Median method   
  so that the compiler will implicitly convert its value to double.  
  If there is no implicit conversion, the compiler will display an error message.            
*/  
  
var query3 = numbers3.Median(num => num);  
  
Console.WriteLine("int: Median = " + query3);  
  
string[] numbers4 = { "one", "two", "three", "four", "five" };  
  
// With the generic overload, you can also use numeric properties of objects.  
  
var query4 = numbers4.Median(str => str.Length);  
  
Console.WriteLine("String: Median = " + query4);  
  
/*  
 This code produces the following output:  
  
 Integer: Median = 3  
 String: Median = 4  
*/  
```   
## <a name="adding-a-method-that-returns-a-collection"></a>Bir koleksiyonu döndüren bir yöntem ekleme  
 Genişletebileceğiniz <xref:System.Collections.Generic.IEnumerable%601> değerlerini bir dizi döndürür bir özel sorgu yöntemi ile arabirim. Bu durumda, yöntem türü bir koleksiyon döndürmelidir <xref:System.Collections.Generic.IEnumerable%601>. Bu tür yöntemler, değerler dizisi için filtre veya veri dönüşüm uygulamak için kullanılabilir.  
  
 Aşağıdaki örnekte adlı bir genişletme yöntemi oluşturma işlemi gösterilmektedir `AlternateElements` ilk öğesinden başlayarak, bir koleksiyondaki her bir öğe döndürür.  
  
```csharp  
// Extension method for the IEnumerable<T> interface.   
// The method returns every other element of a sequence.  
  
public static IEnumerable<T> AlternateElements<T>(this IEnumerable<T> source)  
{  
    List<T> list = new List<T>();  
  
    int i = 0;  
  
    foreach (var element in source)  
    {  
        if (i % 2 == 0)  
        {  
            list.Add(element);  
        }  
  
        i++;  
    }  
  
    return list;  
}  
```  
 Gibi diğer yöntemleri çağırmak bu genişletme yöntemi için herhangi bir sıralanabilir koleksiyonun çağırabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> aşağıdaki kodda gösterildiği gibi arabirim:  
  
```csharp  
string[] strings = { "a", "b", "c", "d", "e" };  
  
var query = strings.AlternateElements();  
  
foreach (var element in query)  
{  
    Console.WriteLine(element);  
}  
/*  
 This code produces the following output:  
  
 a  
 c  
 e  
*/  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic.IEnumerable%601>
- [Genişletme Yöntemleri](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
