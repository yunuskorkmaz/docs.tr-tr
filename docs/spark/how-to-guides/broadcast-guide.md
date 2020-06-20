---
title: Apache Spark için .NET 'teki yayın değişkenlerini kullanın
description: .NET ' te yayın değişkenlerini Apache Spark uygulamalar için nasıl kullanacağınızı öğrenin.
ms.date: 06/11/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 391e32cda14a9b3186ac96800351ddcb39a3d359
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105604"
---
# <a name="use-broadcast-variables-in-net-for-apache-spark"></a>Apache Spark için .NET 'teki yayın değişkenlerini kullanın

Bu makalede, Apache Spark için .NET ' te yayın değişkenlerini nasıl kullanacağınızı öğreneceksiniz. [Apache Spark yayın değişkenleri](https://spark.apache.org/docs/2.2.0/rdd-programming-guide.html#broadcast-variables) , Salt okunabilir olması amaçlanan yürüticileri genelinde değişken paylaşma mekanizmalarda bulunur. Yayın değişkenleri, bir kopyasını görevler ile göndermek yerine, her makinede önbelleğe alınmış bir değişkeni tutmanıza olanak sağlar. Her düğüme, büyük bir giriş veri kümesinin bir kopyasını verimli bir şekilde sağlamak için yayın değişkenlerini kullanabilirsiniz.

Veriler yalnızca bir kez gönderildiğinden, her görevle birlikte yürüticilere gönderilen yerel değişkenlere kıyasla yayın değişkenlerinin performans avantajları vardır. Yayın değişkenlerini ve bunların neden kullanıldığının daha ayrıntılı bir şekilde anlaşılmasını sağlamak için [resmi yayın değişkeni belgelerine](https://spark.apache.org/docs/2.2.0/rdd-programming-guide.html#broadcast-variables) bakın.

## <a name="create-broadcast-variables"></a>Yayın değişkenleri oluşturma

Bir yayın değişkeni oluşturmak için herhangi bir `SparkContext.Broadcast(v)` değişken çağırın `v` . Yayın değişkeni, değişkenin etrafındaki bir sarmalayıcıdır `v` ve yöntemi çağırarak değerine erişebilir `Value()` .

Aşağıdaki kod parçacığında, bir dize değişkeni `v` oluşturulur ve çağrıldığında bir yayın değişkeni `bv` oluşturulur `SparkContext.Broadcast(v)` . Dize için tür parametresinin, `Broadcast` eklenen değişkenin türüyle eşleştiğini fark edebilirsiniz. Kullanıcı tanımlı işlev (UDF) değerini döndürür `bv` .

```csharp
string v = "Variable to be broadcasted";
Broadcast<string> bv = SparkContext.Broadcast(v);

Func<Column, Column> udf = Udf<string, string>(
    str => $"{str}: {bv.Value()}");
```

## <a name="delete-broadcast-variables"></a>Yayın değişkenlerini Sil

Yayın değişkeni, yöntemi çağırarak tüm yürüticilerinden silinebilir `Destroy()` .

```csharp
bv.Destroy();
```

`Destroy()`Yayın değişkeniyle ilgili tüm verileri ve meta verileri siler ve dikkatli kullanılmalıdır. Bir yayın değişkeni yok edildiğinde, tekrar kullanılamaz.

## <a name="limit-broadcast-variable-scope-in-udfs"></a>UDF 'ler içindeki yayın değişken kapsamını sınırla

UDF 'ler içindeki yayın değişkenlerini kullandığınızda, değişkenin kapsamını yalnızca değişkene başvuran UDF ile sınırlamanız gerekir. [Udf 'leri kullanma kılavuzu](udf-guide.md) , bu olgudur 'u ayrıntılı olarak açıklar. Yayın değişkenini çağırdığınızda kapsam özellikle önemlidir `Destroy()` .

Yok edilen yayın değişkeni diğer UDF 'ler tarafından görülebilir veya erişilebilir durumdaysa, bu, kendileri tarafından başvurulmamış olsa bile tüm UDF 'ler tarafından serileştirme için alınır. Apache Spark için .NET, yok edilmiş yayın değişkenini seri hale getiremedi, bu da hataya neden olur. Aşağıdaki kod parçacığı bu hatayı gösterir:

```csharp
string v = "Variable to be broadcasted";
Broadcast<string> bv = SparkContext.Broadcast(v);

// Using the broadcast variable in a UDF:
Func<Column, Column> udf1 = Udf<string, string>(
    str => $"{str}: {bv.Value()}");

// Destroying bv
bv.Destroy();

// Calling udf1 after destroying bv throws the following expected exception:
// org.apache.spark.SparkException: Attempted to use Broadcast(0) after it was destroyed
df.Select(udf1(df["_1"])).Show();

// Different UDF udf2 that is not referencing bv
Func<Column, Column> udf2 = Udf<string, string>(
    str => $"{str}: not referencing broadcast variable");

// Calling udf2 throws the following (unexpected) exception:
// [Error] [JvmBridge] org.apache.spark.SparkException: Task not serializable
df.Select(udf2(df["_1"])).Show();
```

Aşağıdaki kod parçacığı, `bv` `udf2` beklenmeyen bir serileştirme davranışı nedeniyle yok edilirken hiçbir şekilde etkilenmediğini nasıl güvence altına alınacağını gösterir:

```csharp
string v = "Variable to be broadcasted";
// Restricting the visibility of bv to only the UDF referencing it
{
    Broadcast<string> bv = SparkContext.Broadcast(v);

    // Using the broadcast variable in a UDF:
    Func<Column, Column> udf1 = Udf<string, string>(
        str => $"{str}: {bv.Value()}");

    // Destroying bv
    bv.Destroy();
}

// Different UDF udf2 that is not referencing bv
Func<Column, Column> udf2 = Udf<string, string>(
    str => $"{str}: not referencing broadcast variable");

// Calling udf2 works fine as expected
df.Select(udf2(df["_1"])).Show();
```

## <a name="next-steps"></a>Sonraki adımlar

* [Apache Spark için .NET ile çalışmaya başlama](../tutorials/get-started.md)
* [Windows 'da Apache Spark uygulama için bir .NET hatası ayıklama](debug.md)
* [Apache Spark worker ve Kullanıcı tanımlı işlev ikilileri için .NET dağıtma](deploy-worker-udf-binaries.md)
