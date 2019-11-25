---
title: LINQ sorguları için özel yöntemler ekleme (C#)
ms.date: 07/20/2015
ms.assetid: 1a500f60-2e10-49fb-8b2a-d8d08e4817cb
ms.openlocfilehash: e16175d3332b6ce36458eaa78af093e4f8772723
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141476"
---
# <a name="how-to-add-custom-methods-for-linq-queries-c"></a>LINQ sorguları için özel yöntemler ekleme (C#)

<xref:System.Collections.Generic.IEnumerable%601> arabirimine uzantı yöntemleri ekleyerek, LINQ sorguları için kullanabileceğiniz yöntemlerin kümesini genişletebilirsiniz. Örneğin, standart ortalama veya en yüksek işlemlere ek olarak, bir dizi değerden tek bir değeri hesaplamak için özel bir toplama yöntemi oluşturabilirsiniz. Ayrıca, bir dizi değer için özel bir filtre veya belirli bir veri dönüştürmesi olarak çalışacak bir yöntem oluşturabilirsiniz ve yeni bir dizi döndürür. Bu tür yöntemlere örnek olarak <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>ve <xref:System.Linq.Enumerable.Reverse%2A>verilebilir.

<xref:System.Collections.Generic.IEnumerable%601> arabirimini genişlettiğinizde, özel yöntemlerinizi herhangi bir sıralanabilir koleksiyona uygulayabilirsiniz. Daha fazla bilgi için bkz. [Uzantı yöntemleri](../../classes-and-structs/extension-methods.md).

## <a name="adding-an-aggregate-method"></a>Toplama yöntemi ekleme

Toplama yöntemi bir değer kümesinden tek bir değeri hesaplar. LINQ, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>ve <xref:System.Linq.Enumerable.Max%2A>dahil olmak üzere birkaç toplama yöntemi sağlar. <xref:System.Collections.Generic.IEnumerable%601> arabirimine bir genişletme yöntemi ekleyerek kendi toplama yönteminizi oluşturabilirsiniz.

Aşağıdaki kod örneği, `double`tür bir sayı dizisi için ortanca hesaplamak üzere `Median` adlı bir genişletme yönteminin nasıl oluşturulacağını gösterir.

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

Bu genişletme yöntemini, her türlü sıralanabilir koleksiyon için <xref:System.Collections.Generic.IEnumerable%601> arabiriminden diğer toplama yöntemlerini çağırdığınız şekilde çağırabilirsiniz.

Aşağıdaki kod örneği, `double`türünde bir dizi için `Median` yönteminin nasıl kullanılacağını gösterir.

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

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a>Çeşitli türleri kabul etmek için bir toplama yöntemini aşırı yükleme

Toplama yönteminizi çeşitli türlerde dizileri kabul edecek şekilde aşırı yükleyebilirsiniz. Standart yaklaşım, her tür için bir aşırı yükleme oluşturmaktır. Başka bir yaklaşım ise genel bir tür alacak ve bir temsilciyi kullanarak belirli bir türe dönüştürecek bir aşırı yükleme oluşturmaktır. Her iki yaklaşımı de birleştirebilirsiniz.

#### <a name="to-create-an-overload-for-each-type"></a>Her tür için bir aşırı yükleme oluşturmak için

Desteklemek istediğiniz her tür için belirli bir aşırı yükleme oluşturabilirsiniz. Aşağıdaki kod örneğinde, `integer` türü için `Median` yönteminin aşırı yüklemesi gösterilmektedir.

```csharp
//int overload

public static double Median(this IEnumerable<int> source)
{
    return (from num in source select (double)num).Median();
}
```

Artık aşağıdaki kodda gösterildiği gibi `integer` ve `double` türleri için `Median` aşırı yüklerini çağırabilirsiniz:

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

#### <a name="to-create-a-generic-overload"></a>Genel aşırı yükleme oluşturmak için

Ayrıca, genel nesne dizisini kabul eden bir aşırı yükleme de oluşturabilirsiniz. Bu aşırı yükleme bir temsilciyi parametre olarak alır ve bir genel türdeki nesne dizisini belirli bir türe dönüştürmek için kullanır.

Aşağıdaki kod, <xref:System.Func%602> temsilcisini bir parametre olarak alan `Median` yönteminin aşırı yüklemesini gösterir. Bu temsilci, T genel türünde bir nesne alır ve `double`türünde bir nesne döndürür.

```csharp
// Generic overload.

public static double Median<T>(this IEnumerable<T> numbers,
                       Func<T, double> selector)
{
    return (from num in numbers select selector(num)).Median();
}
```

Artık herhangi bir türdeki nesne dizisi için `Median` yöntemini çağırabilirsiniz. Türün kendi yöntem aşırı yüklemesi yoksa, bir temsilci parametresi geçirmeniz gerekir. ' C#De, bu amaçla bir lambda ifadesi kullanabilirsiniz. Ayrıca, yalnızca Visual Basic içinde yöntem çağrısı yerine `Aggregate` veya `Group By` yan tümcesini kullanırsanız, bu yan tümce kapsamındaki herhangi bir değer veya ifade geçirebilirsiniz.

Aşağıdaki örnek kod, bir tamsayılar dizisi ve dizeler dizisi için `Median` yönteminin nasıl çağrılacağını gösterir. Dizeler için, dizideki dizelerin uzunluklarının ortancası hesaplanır. Örnek, <xref:System.Func%602> temsilci parametresinin her durum için `Median` yöntemine nasıl geçirileceğini gösterir.

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

## <a name="adding-a-method-that-returns-a-collection"></a>Koleksiyon döndüren bir yöntem ekleme

<xref:System.Collections.Generic.IEnumerable%601> arabirimini bir değer dizisi döndüren özel bir sorgu yöntemiyle genişletebilirsiniz. Bu durumda, yöntemin <xref:System.Collections.Generic.IEnumerable%601>türünde bir koleksiyon döndürmesi gerekir. Bu tür yöntemler, bir değerler dizisine filtre veya veri dönüştürmeleri uygulamak için kullanılabilir.

Aşağıdaki örnek, ilk öğeden başlayarak bir koleksiyondaki her öğeyi döndüren `AlternateElements` adlı bir genişletme yönteminin nasıl oluşturulacağını gösterir.

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

Aşağıdaki kodda gösterildiği gibi, diğer yöntemleri <xref:System.Collections.Generic.IEnumerable%601> arabiriminden çağırdığınız gibi, herhangi bir sıralanabilir koleksiyon için bu genişletme yöntemini çağırabilirsiniz:

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
- [Genişletme Yöntemleri](../../classes-and-structs/extension-methods.md)
