---
title: Apache Spark için .NET 'te Kullanıcı tanımlı işlevler (UDF) oluşturun
description: .NET ' te Apache Spark uygulamalar için Kullanıcı tanımlı işlevler (UDF) uygulamayı öğrenin.
ms.date: 06/25/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 97afda8ed17d3719c534d72ad3ad026745a70922
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620930"
---
# <a name="create-user-defined-functions-udf-in-net-for-apache-spark"></a><span data-ttu-id="3a2e5-103">Apache Spark için .NET 'te Kullanıcı tanımlı işlevler (UDF) oluşturun</span><span class="sxs-lookup"><span data-stu-id="3a2e5-103">Create user-defined functions (UDF) in .NET for Apache Spark</span></span>

<span data-ttu-id="3a2e5-104">Bu makalede, .NET 'te Apache Spark için Kullanıcı tanımlı işlevlerin (UDF) nasıl kullanılacağını öğrenirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a2e5-104">In this article, you learn how to use user-defined functions (UDF) in .NET for Apache Spark.</span></span> <span data-ttu-id="3a2e5-105">[Udf 'ler)](https://spark.apache.org/docs/latest/api/java/org/apache/spark/sql/expressions/UserDefinedFunction.html) , sistemin yerleşik işlevlerini genişletmek için özel işlevleri kullanmanıza imkan tanıyan bir Spark özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="3a2e5-105">[UDFs)](https://spark.apache.org/docs/latest/api/java/org/apache/spark/sql/expressions/UserDefinedFunction.html) are a Spark feature that allow you to use custom functions to extend the system's built-in functionality.</span></span> <span data-ttu-id="3a2e5-106">UDF 'ler, bir tablodaki tek bir satırdaki değerleri, UDF 'de tanımlanan mantığa göre her satırda tek bir karşılık gelen bir çıktı değeri oluşturacak şekilde dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="3a2e5-106">UDFs transform values from a single row within a table to produce a single corresponding output value per row based on the logic defined in the UDF.</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="define-udfs"></a><span data-ttu-id="3a2e5-107">UDF 'Leri tanımlama</span><span class="sxs-lookup"><span data-stu-id="3a2e5-107">Define UDFs</span></span>

<span data-ttu-id="3a2e5-108">Aşağıdaki UDF tanımını gözden geçirin:</span><span class="sxs-lookup"><span data-stu-id="3a2e5-108">Review the following UDF definition:</span></span>

```csharp
string s1 = "hello";
Func<Column, Column> udf = Udf<string, string>(
    str => $"{s1} {str}");
```

<span data-ttu-id="3a2e5-109">UDF bir `string` [veri çerçevesinin](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/DataFrame.cs#L24) [sütunu](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/Column.cs#L14) olarak bir giriş olarak alır ve `string` `hello` girişin önüne eklenmiş bir ile döndürür.</span><span class="sxs-lookup"><span data-stu-id="3a2e5-109">The UDF takes a `string` as an input in the form of a [Column](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/Column.cs#L14) of a [Dataframe](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/DataFrame.cs#L24)) and returns a `string` with `hello` appended in front of the input.</span></span>

<span data-ttu-id="3a2e5-110">Aşağıdaki veri çerçevesi `df` adların bir listesini içerir:</span><span class="sxs-lookup"><span data-stu-id="3a2e5-110">The following DataFrame `df` contains a list of names:</span></span>

```text
+-------+
|   name|
+-------+
|Michael|
|   Andy|
| Justin|
+-------+
```

<span data-ttu-id="3a2e5-111">Şimdi, yukarıda tanımlanan `udf` veri çerçevesine uygulayalim `df` :</span><span class="sxs-lookup"><span data-stu-id="3a2e5-111">Now let's apply the above defined `udf` to the DataFrame `df`:</span></span>

```csharp
DataFrame udfResult = df.Select(udf(df["name"]));
```

<span data-ttu-id="3a2e5-112">Aşağıdaki DataFrame, `udfResult` udf 'in sonucudur:</span><span class="sxs-lookup"><span data-stu-id="3a2e5-112">The following DataFrame `udfResult` is the result of the UDF:</span></span>

```text
+-------------+
|         name|
+-------------+
|hello Michael|
|   hello Andy|
| hello Justin|
+-------------+
```

<span data-ttu-id="3a2e5-113">UDF 'Leri nasıl uygulayacağınızı daha iyi anlamak için, [udf yardımcı işlevlerini](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/Functions.cs#L3616) ve GitHub 'daki [örnekleri](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark.E2ETest/UdfTests/UdfSimpleTypesTests.cs#L49) gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="3a2e5-113">To better understand how to implement UDFs, review the [UDF helper functions](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/Functions.cs#L3616) and [examples](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark.E2ETest/UdfTests/UdfSimpleTypesTests.cs#L49) on GitHub.</span></span>

## <a name="udf-serialization"></a><span data-ttu-id="3a2e5-114">UDF serileştirme</span><span class="sxs-lookup"><span data-stu-id="3a2e5-114">UDF serialization</span></span>

<span data-ttu-id="3a2e5-115">UDF 'ler, çalışanlar üzerinde yürütülmesi gereken işlevler olduğundan, sürücüden yükün bir parçası olarak serileştirilmesi ve çalışanlara gönderilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="3a2e5-115">Because UDFs are functions that need to be executed on workers, they have to be serialized and sent to the workers as part of the payload from the driver.</span></span> <span data-ttu-id="3a2e5-116">Yöntemine bir başvuru olan [temsilcinin](../../csharp/programming-guide/delegates/index.md), geçerli temsilcinin örnek yöntemi çağırdığı sınıf örneği olan hedefinin yanı sıra, [hedefine](xref:System.Delegate.Target%2A)da serileştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="3a2e5-116">The [delegate](../../csharp/programming-guide/delegates/index.md), which is a reference to the method, needs to be serialized as well as its [target](xref:System.Delegate.Target%2A), which is the class instance on which the current delegate invokes the instance method.</span></span> <span data-ttu-id="3a2e5-117">UDF serileştirmenin nasıl yapıldığını daha iyi anlamak için [GitHub 'da Bu kod örneğini](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Utils/CommandSerDe.cs#L149) inceleyin.</span><span class="sxs-lookup"><span data-stu-id="3a2e5-117">Review this [code example in GitHub](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Utils/CommandSerDe.cs#L149) to get a better understanding of how UDF serialization is being done.</span></span>

<span data-ttu-id="3a2e5-118">.NET Apache Spark .NET Core kullanır, bu da temsilcilerin serileştirilmesi desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="3a2e5-118">.NET for Apache Spark uses .NET Core, which doesn't support serializing delegates.</span></span> <span data-ttu-id="3a2e5-119">Bunun yerine, temsilcinin tanımlandığı hedefi seri hale getirmek için yansıma kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3a2e5-119">Instead, reflection is used to serialize the target where the delegate is defined.</span></span> <span data-ttu-id="3a2e5-120">Ortak bir kapsamda birden çok temsilci tanımlandığında, serileştirme için yansıma hedefi olan bir paylaşılan kapatılmak olur.</span><span class="sxs-lookup"><span data-stu-id="3a2e5-120">When multiple delegates are defined in a common scope, they have a shared closure that becomes the target of reflection for serialization.</span></span>

### <a name="serialization-example"></a><span data-ttu-id="3a2e5-121">Serileştirme örneği</span><span class="sxs-lookup"><span data-stu-id="3a2e5-121">Serialization example</span></span>

<span data-ttu-id="3a2e5-122">Aşağıdaki kod parçacığı, bir sonuç olarak ilgili dizeleri döndüren iki işlev temsilcisi içinde başvurulmakta olan iki dize değişkenini tanımlar:</span><span class="sxs-lookup"><span data-stu-id="3a2e5-122">The following code snippet defines two string variables that are being referenced in two function delegates that return the respective strings as a result:</span></span>

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

<span data-ttu-id="3a2e5-123">Yukarıdaki C# kodu, derleyicisinden aşağıdaki C# ayrıştırılmış derleme (kredi kaynağı: [sharplab.io](https://sharplab.io)) kodunu üretir:</span><span class="sxs-lookup"><span data-stu-id="3a2e5-123">The above C# code generates the following C# disassembly (credit source: [sharplab.io](https://sharplab.io)) code from the compiler:</span></span>

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

<span data-ttu-id="3a2e5-124">`func`Ve `func2` `<>c__DisplayClass0_0` temsilcileri serileştirilirken serileştirilmiş olan hedef olan aynı kapanışı paylaşır `func` `func2` .</span><span class="sxs-lookup"><span data-stu-id="3a2e5-124">Both `func` and `func2` share the same closure `<>c__DisplayClass0_0`, which is the target that is serialized when serializing the delegates `func` and `func2`.</span></span> <span data-ttu-id="3a2e5-125">`Func<string, string> a`Yalnızca başvuru olsa da `s1` , dosyalar `s2` çalışanlara gönderildiğinde da serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="3a2e5-125">Even though `Func<string, string> a` is only referencing `s1`, `s2` is also serialized when the bytes are sent to the workers.</span></span>

<span data-ttu-id="3a2e5-126">Bu, çalışma zamanında bazı beklenmeyen davranışlara (örneğin, [yayın değişkenlerini](broadcast-guide.md)kullanırken olduğu gibi) neden olabilir. bu nedenle, bir işlevde kullanılan değişkenlerin görünürlüğünü bu işlevin kapsamına göre kısıtlamanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="3a2e5-126">This can lead to some unexpected behaviors at runtime (like in the case of using [broadcast variables](broadcast-guide.md)), which is why we recommend that you restrict the visibility of the variables used in a function to that function's scope.</span></span>

<span data-ttu-id="3a2e5-127">Aşağıdaki kod parçacığı, istenen serileştirme davranışını uygulamak için önerilen yoldur:</span><span class="sxs-lookup"><span data-stu-id="3a2e5-127">The following code snippet is the recommended way to implement the desired serialization behavior:</span></span>

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

<span data-ttu-id="3a2e5-128">Yukarıdaki C# kodu, derleyicisinden aşağıdaki C# ayrıştırılmış derleme (kredi kaynağı: [sharplab.io](https://sharplab.io)) kodunu üretir:</span><span class="sxs-lookup"><span data-stu-id="3a2e5-128">The above C# code generates the following C# disassembly (credit source: [sharplab.io](https://sharplab.io)) code from the compiler:</span></span>

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

<span data-ttu-id="3a2e5-129">`func` `func2` Artık bir kapanışı paylaşmadığına ve bunların kendi ayrı kapanışlarına ve sırasıyla kendilerine sahip olmadığına dikkat edin `<>c__DisplayClass0_0` `<>c__DisplayClass0_1` .</span><span class="sxs-lookup"><span data-stu-id="3a2e5-129">Notice that `func` and `func2` no longer share a closure, and they have their own separate closures `<>c__DisplayClass0_0` and `<>c__DisplayClass0_1` respectively.</span></span> <span data-ttu-id="3a2e5-130">Serileştirme hedefi olarak kullanıldığında, başvurulan değişkenlerden başka hiçbir şey temsilci için serileştirilmez.</span><span class="sxs-lookup"><span data-stu-id="3a2e5-130">When used as the target for serialization, nothing other than the referenced variables will get serialized for the delegate.</span></span> <span data-ttu-id="3a2e5-131">Bu davranış, ortak bir kapsamda birden çok UDF uygulanırken göz önünde bulundurmanız önemlidir.</span><span class="sxs-lookup"><span data-stu-id="3a2e5-131">This behavior is important to keep in mind while implementing multiple UDFs in a common scope.</span></span>

## <a name="some-spark-udf-caveats"></a><span data-ttu-id="3a2e5-132">Bazı Spark UDF uyarıları</span><span class="sxs-lookup"><span data-stu-id="3a2e5-132">Some Spark UDF caveats</span></span>

* <span data-ttu-id="3a2e5-133">UDF 'ler içindeki null değerler özel durumlar oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="3a2e5-133">Null values in UDFs can throw exceptions.</span></span> <span data-ttu-id="3a2e5-134">Bu, geliştiricilerin bunları işleme sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="3a2e5-134">It's the responsibility of the developer to handle them.</span></span>
* <span data-ttu-id="3a2e5-135">UDF 'ler Spark 'ın yerleşik işlevleri tarafından sunulan iyileştirmelerinden yararlanır, bu nedenle mümkün olduğunda yerleşik işlevler kullanılması önerilir.</span><span class="sxs-lookup"><span data-stu-id="3a2e5-135">UDFs don't leverage the optimizations provided by Spark's built-in functions, so it's recommended to use built-in functions where possible.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3a2e5-136">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="3a2e5-136">Next steps</span></span>

* [<span data-ttu-id="3a2e5-137">Apache Spark için .NET ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="3a2e5-137">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="3a2e5-138">Windows 'da Apache Spark uygulama için bir .NET hatası ayıklama</span><span class="sxs-lookup"><span data-stu-id="3a2e5-138">Debug a .NET for Apache Spark application on Windows</span></span>](debug.md)
