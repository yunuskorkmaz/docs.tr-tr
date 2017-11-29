---
title: "Nasıl yapılır: LINQ sorguları için (C#) özel yöntemler ekleme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 1a500f60-2e10-49fb-8b2a-d8d08e4817cb
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 01617ec2583361099eb5afb7957960ba39812680
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-custom-methods-for-linq-queries-c"></a>Nasıl yapılır: LINQ sorguları için (C#) özel yöntemler ekleme
İçin genişletme yöntemleri ekleyerek LINQ sorguları için kullanabileceğiniz yöntemler kümesi genişletebilirsiniz <xref:System.Collections.Generic.IEnumerable%601> arabirimi. Örneğin, standart ortalama veya en fazla işlemlerinin yanı sıra, değerlerin bir sırasından tek bir değeri hesaplamak için özel bir toplama yöntemi oluşturabilirsiniz. Özel filtre veya değerleri dizisi için belirli veri dönüştürme olarak çalışır ve yeni sırası döndüren bir yöntem de oluşturabilirsiniz. Bu tür yöntemler örnekleridir <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, ve <xref:System.Linq.Enumerable.Reverse%2A>.  
  
 Genişlettiğinizde <xref:System.Collections.Generic.IEnumerable%601> arabirimi, özel yöntemlerinizi herhangi numaralandırılabilir koleksiyonuna uygulayabilirsiniz. Daha fazla bilgi için bkz: [genişletme yöntemleri](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).  
  
## <a name="adding-an-aggregate-method"></a>Toplama yöntemi ekleme  
 Birleşik bir yöntemi, bir değerler kümesinden tek bir değer hesaplar. LINQ sağlar dahil olmak üzere birkaç toplama yöntemleri <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, ve <xref:System.Linq.Enumerable.Max%2A>. Bir genişletme yöntemi ekleyerek toplama yönteminizi oluşturabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> arabirimi.  
  
 Aşağıdaki kod örneği olarak adlandırılan bir genişletme yöntemi oluşturulacağını gösterir `Median` ORTANCA bir dizi sayı türü için işlem için `double`.  
  
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
  
 Toplam diğer yöntemleri çağırmak aynı şekilde numaralandırılabilir herhangi bir koleksiyon için bu uzantı metodu çağırma <xref:System.Collections.Generic.IEnumerable%601> arabirimi.  
  
 Aşağıdaki kod örneğinde nasıl kullanılacağını gösterir `Median` türünde bir dizi yöntem `double`.  
  
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
  
### <a name="overloading-an-aggregate-method-to-accept-various-types"></a>Çeşitli türlerini kabul edecek şekilde bir toplama yöntemi aşırı yüklemesi  
 Toplama yöntemi aşırı yükleme çeşitli türlerdeki dizilerini kabul. Standart yaklaşımı, her tür için bir aşırı oluşturmaktır. Başka bir yaklaşım, genel bir tür olması ve bir temsilci kullanarak belirli bir türe dönüştürmek aşırı oluşturmaktır. Ayrıca, her iki yaklaşımın da birleştirebilirsiniz.  
  
#### <a name="to-create-an-overload-for-each-type"></a>Her tür için bir aşırı oluşturmak için  
 Desteklemek istediğiniz her bir türü için belirli bir aşırı oluşturabilirsiniz. Aşağıdaki kod örneğinde bir aşırı yüklemesini gösterir `Median` yöntemi `integer` türü.  
  
```csharp  
//int overload  
  
public static double Median(this IEnumerable<int> source)  
{  
    return (from num in source select (double)num).Median();  
}  
```   
 Şimdi Ara `Median` her ikisi için de aşırı `integer` ve `double` aşağıdaki kodda gösterildiği gibi türleri:  
  
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

#### <a name="to-create-a-generic-overload"></a>Bir genel aşırı oluşturmak için  
 Genel nesneler dizisi kabul eden bir aşırı de oluşturabilirsiniz. Bu aşırı temsilci bir parametre olarak alır ve belirli bir türe genel bir tür nesnelerin bir dizi dönüştürmek için kullanır.  
  
 Aşağıdaki kod bir aşırı yüklemesini gösterir `Median` yönteminin alan <xref:System.Func%602> temsilci parametre olarak. Bu temsilci T genel türünde bir nesne alır ve türünde bir nesne döndürür `double`.  
  
```csharp  
// Generic overload.  
  
public static double Median<T>(this IEnumerable<T> numbers,  
                       Func<T, double> selector)  
{  
    return (from num in numbers select selector(num)).Median();  
}  
```  
  
 Şimdi Ara `Median` herhangi bir türde nesnelerinin bir dizisi için yöntem. Türü kendi yöntemi aşırı yüklemesini yoksa bir temsilci parametre geçirmek zorunda. C# ' ta lambda ifadesi bu amaç için kullanabilirsiniz. Ayrıca, Visual Basic'te yalnızca kullanırsanız `Aggregate` veya `Group By` yöntem çağrısının yerine yan tümcesi, herhangi bir değer veya bu yan tümce kapsamı içinde olan deyimi iletebilir.  
  
 Aşağıdaki kod örneği nasıl çağrılacağını gösterir `Median` yöntemi dizisi ve bir dizeler dizisi. Dizeler için dizi dizelerde uzunlukları ORTANCA hesaplanır. Örnek nasıl iletileceğini gösterir <xref:System.Func%602> temsilci parametresi `Median` yöntemi her örneği için.  
  
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
 Genişletebilirsiniz <xref:System.Collections.Generic.IEnumerable%601> arabirimi bir özel sorgu yöntemiyle değerleri dizisi döndürür. Bu durumda, yöntem bir koleksiyon türü döndürmelidir <xref:System.Collections.Generic.IEnumerable%601>. Bu tür yöntemleri değerleri dizisi için filtre ya da veri dönüşüm uygulamak için kullanılabilir.  
  
 Aşağıdaki örnek adlı bir genişletme yöntemi oluşturulacağını gösterir `AlternateElements` ilk öğesinden başlayarak, bir koleksiyondaki her bir öğe getirir.  
  
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
 Diğer yöntemleri çağırmak gibi herhangi bir numaralandırılabilir koleksiyonu için bu genişletme yöntemi çağırabilir <xref:System.Collections.Generic.IEnumerable%601> aşağıdaki kodda gösterildiği gibi arabirim:  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [Genişletme yöntemleri](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
