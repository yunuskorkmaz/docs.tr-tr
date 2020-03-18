---
title: LINQ sorguları için özel yöntemler ekleme (C#)
ms.date: 07/20/2015
ms.assetid: 1a500f60-2e10-49fb-8b2a-d8d08e4817cb
ms.openlocfilehash: e16175d3332b6ce36458eaa78af093e4f8772723
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141476"
---
# <a name="how-to-add-custom-methods-for-linq-queries-c"></a>LINQ sorguları için özel yöntemler ekleme (C#)

Arabirime uzantı yöntemleri ekleyerek LINQ sorguları için kullanabileceğiniz <xref:System.Collections.Generic.IEnumerable%601> yöntem kümesini genişletebilirsiniz. Örneğin, standart ortalama veya maksimum işlemlere ek olarak, bir değer dizisinden tek bir değer hesaplamak için özel bir toplama yöntemi oluşturabilirsiniz. Ayrıca, bir değer dizisi için özel bir filtre veya belirli bir veri dönüşümü olarak çalışan ve yeni bir sıra döndüren bir yöntem de oluşturabilirsiniz. Bu tür yöntemlere <xref:System.Linq.Enumerable.Skip%2A>örnek <xref:System.Linq.Enumerable.Reverse%2A>olarak <xref:System.Linq.Enumerable.Distinct%2A>, , ve .

<xref:System.Collections.Generic.IEnumerable%601> Arabirimi genişletdiğinizde, özel yöntemlerinizi herhangi bir sayısal koleksiyona uygulayabilirsiniz. Daha fazla bilgi için [Uzantı Yöntemleri'ne](../../classes-and-structs/extension-methods.md)bakın.

## <a name="adding-an-aggregate-method"></a>Toplama Yöntemi Ekleme

Toplu yöntem, bir değer kümesinden tek bir değer hesaplar. LINQ, <xref:System.Linq.Enumerable.Average%2A>, , <xref:System.Linq.Enumerable.Min%2A>ve <xref:System.Linq.Enumerable.Max%2A>. Arabirime bir uzantı yöntemi ekleyerek kendi <xref:System.Collections.Generic.IEnumerable%601> toplama yönteminizi oluşturabilirsiniz.

Aşağıdaki kod örneği, bir tür `Median` `double`sayısı dizisi için ortanca yı hesaplamak için çağrılan bir uzantı yönteminin nasıl oluşturulurunun gösteriş olduğunu gösterir.

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

Bu uzantı yöntemini, <xref:System.Collections.Generic.IEnumerable%601> arabirimden diğer toplu yöntemleri çağırdığınız şekilde numaralandırma yöntemiolarak çağırırsınız.

Aşağıdaki kod örneği, yöntemin `Median` bir tür `double`dizisi için nasıl kullanılacağını gösterir.

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

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a>Çeşitli Türleri Kabul Etmek Için Bir Agrega Yöntemini Aşırı Yükleme

Çeşitli türdeki dizileri kabul etmek için toplu yönteminizi aşırı yükleyebilirsiniz. Standart yaklaşım, her tür için aşırı yük oluşturmaktır. Başka bir yaklaşım, genel bir tür alacak ve bir temsilci kullanarak belirli bir türe dönüştürmek bir aşırı yük oluşturmaktır. Ayrıca her iki yaklaşımı da birleştirebilirsiniz.

#### <a name="to-create-an-overload-for-each-type"></a>Her tür için aşırı yük oluşturmak için

Desteklemek istediğiniz her tür için belirli bir aşırı yükleme oluşturabilirsiniz. Aşağıdaki kod `Median` `integer` örneği, tür için yöntemin aşırı yüklenmesini gösterir.

```csharp
//int overload

public static double Median(this IEnumerable<int> source)
{
    return (from num in source select (double)num).Median();
}
```

Artık aşağıdaki kodda gösterildiği `integer` gibi, hem de `double` türler için `Median` aşırı yüklemeleri arayabilirsiniz:

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

#### <a name="to-create-a-generic-overload"></a>Genel bir aşırı yük oluşturmak için

Ayrıca, genel nesnelerin bir dizi kabul eden bir aşırı yük oluşturabilirsiniz. Bu aşırı yük bir temsilciyi parametre olarak alır ve genel bir türdeki nesnelerin dizisini belirli bir türe dönüştürmek için kullanır.

Aşağıdaki kod, `Median` <xref:System.Func%602> temsilciyi parametre olarak alan yöntemin aşırı yüklenmesini gösterir. Bu temsilci genel t türünde bir nesne `double`alır ve türünde bir nesne döndürür.

```csharp
// Generic overload.

public static double Median<T>(this IEnumerable<T> numbers,
                       Func<T, double> selector)
{
    return (from num in numbers select selector(num)).Median();
}
```

Artık herhangi bir `Median` türdeki nesnelerin bir dizi için yöntemi arayabilirsiniz. Türün kendi yöntemi aşırı yüklemesi yoksa, bir temsilci parametresini geçmeniz gerekir. C#'da, bu amaçla lambda ifadesini kullanabilirsiniz. Ayrıca, yalnızca Visual Basic'te, `Aggregate` `Group By` yöntem çağrısı yerine veya yan tümcesini kullanırsanız, bu yan tümce kapsamında ki herhangi bir değeri veya ifadeyi geçirebilirsiniz.

Aşağıdaki örnek kod, bir `Median` dizi bir karşıcı ve dize dizisi için yöntemin nasıl çağrılmasını gösterir. Dizeleri için, dizideki dizelerin uzunluklarının ortancası hesaplanır. Örnek, <xref:System.Func%602> her servis talebi için `Median` yönteme temsilci parametresinin nasıl geçirilen gösterilmektedir.

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

## <a name="adding-a-method-that-returns-a-collection"></a>Koleksiyon Döndüren Yöntem Ekleme

<xref:System.Collections.Generic.IEnumerable%601> Bir değer dizisi döndüren özel bir sorgu yöntemiyle arabirimi genişletebilirsiniz. Bu durumda, yöntem türünden <xref:System.Collections.Generic.IEnumerable%601>bir koleksiyon döndürmelidir. Bu tür yöntemler, filtreleri veya veri dönüşümlerini bir değer dizisine uygulamak için kullanılabilir.

Aşağıdaki örnek, ilk öğeden başlayarak bir koleksiyondaki diğer tüm öğeyi döndüren adlandırılmış `AlternateElements` bir uzantı yönteminin nasıl oluşturulurdu gösterilmektedir.

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

Aşağıdaki kodda gösterildiği gibi, <xref:System.Collections.Generic.IEnumerable%601> arabirimden diğer yöntemleri çağıracağınız gibi, herhangi bir numaralandırma için bu uzantılı yöntemi arayabilirsiniz:

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
