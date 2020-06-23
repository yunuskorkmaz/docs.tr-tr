---
title: Apache Spark için .NET 'te Kullanıcı tanımlı işlevler (UDF) oluşturun
description: .NET ' te Apache Spark uygulamalar için Kullanıcı tanımlı işlevler (UDF) uygulamayı öğrenin.
ms.date: 06/11/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: fe3dec187f94f84adb1217c39ff6aabc4b4db1c5
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/22/2020
ms.locfileid: "85142023"
---
# <a name="create-user-defined-functions-udf-in-net-for-apache-spark"></a>Apache Spark için .NET 'te Kullanıcı tanımlı işlevler (UDF) oluşturun

Bu makalede, .NET 'te Apache Spark için Kullanıcı tanımlı işlevlerin (UDF) nasıl kullanılacağını öğrenirsiniz. [Udf 'ler)](https://spark.apache.org/docs/latest/api/java/org/apache/spark/sql/expressions/UserDefinedFunction.html) , sistemin yerleşik işlevlerini genişletmek için özel işlevleri kullanmanıza imkan tanıyan bir Spark özelliğidir. UDF 'ler, bir tablodaki tek bir satırdaki değerleri, UDF 'de tanımlanan mantığa göre her satırda tek bir karşılık gelen bir çıktı değeri oluşturacak şekilde dönüştürür.

## <a name="define-udfs"></a>UDF 'Leri tanımlama

Aşağıdaki UDF tanımını gözden geçirin:

```csharp
string s1 = "hello";
Func<Column, Column> udf = Udf<string, string>(
    str => $"{s1} {str}");
```

UDF bir `string` [veri çerçevesinin](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/DataFrame.cs#L24) [sütunu](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/Column.cs#L14) olarak bir giriş olarak alır ve `string` `hello` girişin önüne eklenmiş bir ile döndürür.

Aşağıdaki veri çerçevesi `df` adların bir listesini içerir:

```text
+-------+
|   name|
+-------+
|Michael|
|   Andy|
| Justin|
+-------+
```

Şimdi, yukarıda tanımlanan `udf` veri çerçevesine uygulayalim `df` :

```csharp
DataFrame udfResult = df.Select(udf(df["name"]));
```

Aşağıdaki DataFrame, `udfResult` udf 'in sonucudur:

```text
+-------------+
|         name|
+-------------+
|hello Michael|
|   hello Andy|
| hello Justin|
+-------------+
```

UDF 'Leri nasıl uygulayacağınızı daha iyi anlamak için, [udf yardımcı işlevlerini](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/Functions.cs#L3616) ve GitHub 'daki [örnekleri](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark.E2ETest/UdfTests/UdfSimpleTypesTests.cs#L49) gözden geçirin.

## <a name="udf-serialization"></a>UDF serileştirme

UDF 'ler, çalışanlar üzerinde yürütülmesi gereken işlevler olduğundan, sürücüden yükün bir parçası olarak serileştirilmesi ve çalışanlara gönderilmesi gerekir. Yöntemine bir başvuru olan [temsilcinin](../../csharp/programming-guide/delegates/index.md), geçerli temsilcinin örnek yöntemi çağırdığı sınıf örneği olan hedefinin yanı sıra, [hedefine](xref:System.Delegate.Target%2A)da serileştirilmesi gerekir. UDF serileştirmenin nasıl yapıldığını daha iyi anlamak için [GitHub 'da Bu kod örneğini](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Utils/CommandSerDe.cs#L149) inceleyin.

.NET Apache Spark .NET Core kullanır, bu da temsilcilerin serileştirilmesi desteklenmez. Bunun yerine, temsilcinin tanımlandığı hedefi seri hale getirmek için yansıma kullanılır. Ortak bir kapsamda birden çok temsilci tanımlandığında, serileştirme için yansıma hedefi olan bir paylaşılan kapatılmak olur.

### <a name="serialization-example"></a>Serileştirme örneği

Aşağıdaki kod parçacığı, bir sonuç olarak ilgili dizeleri döndüren iki işlev temsilcisi içinde başvurulmakta olan iki dize değişkenini tanımlar:

```csharp
using System;

public class C {
    public void M() {
        string s1 = "s1";
        string s2 = "s2";
        Func<string, string> a = str => s1;
        Func<string, string> b = str => s2;
    }
}
```

Yukarıdaki C# kodu, derleyicisinden aşağıdaki C# ayrıştırılmış derleme (kredi kaynağı: [sharplab.io](https://sharplab.io)) kodunu üretir:

```csharp
public class C
{
    [CompilerGenerated]
    private sealed class <>c__DisplayClass0_0
    {
        public string s1;

        public string s2;

        internal string <M>b__0(string str)
        {
            return s1;
        }

        internal string <M>b__1(string str)
        {
            return s2;
        }
    }

    public void M()
    {
        <>c__DisplayClass0_0 <>c__DisplayClass0_ = new <>c__DisplayClass0_0();
        <>c__DisplayClass0_.s1 = "s1";
        <>c__DisplayClass0_.s2 = "s2";
        Func<string, string> func = new Func<string, string>(<>c__DisplayClass0_.<M>b__0);
        Func<string, string> func2 = new Func<string, string>(<>c__DisplayClass0_.<M>b__1);
    }
}
```

`func`Ve `func2` `<>c__DisplayClass0_0` temsilcileri serileştirilirken serileştirilmiş olan hedef olan aynı kapanışı paylaşır `func` `func2` . `Func<string, string> a`Yalnızca başvuru olsa da `s1` , dosyalar `s2` çalışanlara gönderildiğinde da serileştirilir.

Bu, çalışma zamanında bazı beklenmeyen davranışlara (örneğin, [yayın değişkenlerini](broadcast-guide.md)kullanırken olduğu gibi) neden olabilir. bu nedenle, bir işlevde kullanılan değişkenlerin görünürlüğünü bu işlevin kapsamına göre kısıtlamanız önerilir.

Aşağıdaki kod parçacığı, istenen serileştirme davranışını uygulamak için önerilen yoldur:

```csharp
using System;

public class C {
    public void M() {
        {
            string s1 = "s1";
            Func<string, string> a = str => s1;
        }
        {
            string s2 = "s2";
            Func<string, string> b = str => s2;
        }
    }
}
```

Yukarıdaki C# kodu, derleyicisinden aşağıdaki C# ayrıştırılmış derleme (kredi kaynağı: [sharplab.io](https://sharplab.io)) kodunu üretir:

```csharp
public class C
{
    [CompilerGenerated]
    private sealed class <>c__DisplayClass0_0
    {
        public string s1;

        internal string <M>b__0(string str)
        {
            return s1;
        }
    }

    [CompilerGenerated]
    private sealed class <>c__DisplayClass0_1
    {
        public string s2;

        internal string <M>b__1(string str)
        {
            return s2;
        }
    }

    public void M()
    {
        <>c__DisplayClass0_0 <>c__DisplayClass0_ = new <>c__DisplayClass0_0();
        <>c__DisplayClass0_.s1 = "s1";
        Func<string, string> func = new Func<string, string>(<>c__DisplayClass0_.<M>b__0);
        <>c__DisplayClass0_1 <>c__DisplayClass0_2 = new <>c__DisplayClass0_1();
        <>c__DisplayClass0_2.s2 = "s2";
        Func<string, string> func2 = new Func<string, string>(<>c__DisplayClass0_2.<M>b__1);
    }
}
```

`func` `func2` Artık bir kapanışı paylaşmadığına ve bunların kendi ayrı kapanışlarına ve sırasıyla kendilerine sahip olmadığına dikkat edin `<>c__DisplayClass0_0` `<>c__DisplayClass0_1` . Serileştirme hedefi olarak kullanıldığında, başvurulan değişkenlerden başka hiçbir şey temsilci için serileştirilmez. Bu davranış, ortak bir kapsamda birden çok UDF uygulanırken göz önünde bulundurmanız önemlidir.

## <a name="some-spark-udf-caveats"></a>Bazı Spark UDF uyarıları

* UDF 'ler içindeki null değerler özel durumlar oluşturabilir. Bu, geliştiricilerin bunları işleme sorumluluğundadır.
* UDF 'ler Spark 'ın yerleşik işlevleri tarafından sunulan iyileştirmelerinden yararlanır, bu nedenle mümkün olduğunda yerleşik işlevler kullanılması önerilir.

## <a name="next-steps"></a>Sonraki adımlar

* [Apache Spark için .NET ile çalışmaya başlama](../tutorials/get-started.md)
* [Windows 'da Apache Spark uygulama için bir .NET hatası ayıklama](debug.md)
