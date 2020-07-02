---
title: Apache Spark için .NET 'teki yayın değişkenlerini kullanın
description: .NET ' te yayın değişkenlerini Apache Spark uygulamalar için nasıl kullanacağınızı öğrenin.
ms.date: 06/25/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: d86b160855cc4d3f3a6502f5606d4766b7c06aa0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617862"
---
# <a name="use-broadcast-variables-in-net-for-apache-spark"></a><span data-ttu-id="478a6-103">Apache Spark için .NET 'teki yayın değişkenlerini kullanın</span><span class="sxs-lookup"><span data-stu-id="478a6-103">Use broadcast variables in .NET for Apache Spark</span></span>

<span data-ttu-id="478a6-104">Bu makalede, Apache Spark için .NET ' te yayın değişkenlerini nasıl kullanacağınızı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="478a6-104">In this article, you learn how to use broadcast variables in .NET for Apache Spark.</span></span> <span data-ttu-id="478a6-105">[Apache Spark yayın değişkenleri](https://spark.apache.org/docs/2.2.0/rdd-programming-guide.html#broadcast-variables) , Salt okunabilir olması amaçlanan yürüticileri genelinde değişken paylaşma mekanizmalarda bulunur.</span><span class="sxs-lookup"><span data-stu-id="478a6-105">[Broadcast variables in Apache Spark](https://spark.apache.org/docs/2.2.0/rdd-programming-guide.html#broadcast-variables) are mechanisms for sharing variables across executors that are meant to be read-only.</span></span> <span data-ttu-id="478a6-106">Yayın değişkenleri, bir kopyasını görevler ile göndermek yerine, her makinede önbelleğe alınmış bir değişkeni tutmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="478a6-106">Broadcast variables allow you to keep a read-only variable cached on each machine rather than shipping a copy of it with tasks.</span></span> <span data-ttu-id="478a6-107">Her düğüme, büyük bir giriş veri kümesinin bir kopyasını verimli bir şekilde sağlamak için yayın değişkenlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="478a6-107">You can use broadcast variables to give every node a copy of a large input dataset in an efficient manner.</span></span>

<span data-ttu-id="478a6-108">Veriler yalnızca bir kez gönderildiğinden, her görevle birlikte yürüticilere gönderilen yerel değişkenlere kıyasla yayın değişkenlerinin performans avantajları vardır.</span><span class="sxs-lookup"><span data-stu-id="478a6-108">Because the data is sent only once, broadcast variables have performance benefits when compared to local variables that are shipped to the executors with each task.</span></span> <span data-ttu-id="478a6-109">Yayın değişkenlerini ve bunların neden kullanıldığının daha ayrıntılı bir şekilde anlaşılmasını sağlamak için [resmi yayın değişkeni belgelerine](https://spark.apache.org/docs/2.2.0/rdd-programming-guide.html#broadcast-variables) bakın.</span><span class="sxs-lookup"><span data-stu-id="478a6-109">Refer to the [official broadcast variable documentation](https://spark.apache.org/docs/2.2.0/rdd-programming-guide.html#broadcast-variables) to get a deeper understanding of broadcast variables and why they are used.</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="create-broadcast-variables"></a><span data-ttu-id="478a6-110">Yayın değişkenleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="478a6-110">Create broadcast variables</span></span>

<span data-ttu-id="478a6-111">Bir yayın değişkeni oluşturmak için herhangi bir `SparkContext.Broadcast(v)` değişken çağırın `v` .</span><span class="sxs-lookup"><span data-stu-id="478a6-111">To create a broadcast variable, call `SparkContext.Broadcast(v)` for any variable `v`.</span></span> <span data-ttu-id="478a6-112">Yayın değişkeni, değişkenin etrafındaki bir sarmalayıcıdır `v` ve yöntemi çağırarak değerine erişebilir `Value()` .</span><span class="sxs-lookup"><span data-stu-id="478a6-112">The broadcast variable is a wrapper around the variable `v`, and its value can be accessed by calling the `Value()` method.</span></span>

<span data-ttu-id="478a6-113">Aşağıdaki kod parçacığında, bir dize değişkeni `v` oluşturulur ve çağrıldığında bir yayın değişkeni `bv` oluşturulur `SparkContext.Broadcast(v)` .</span><span class="sxs-lookup"><span data-stu-id="478a6-113">In the following code snippet, a string variable `v` is created, and a broadcast variable `bv` is created when `SparkContext.Broadcast(v)`is called.</span></span> <span data-ttu-id="478a6-114">Dize için tür parametresinin, `Broadcast` eklenen değişkenin türüyle eşleştiğini fark edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="478a6-114">Notice the type parameter for `Broadcast`, string, matches the type of the variable being broadcasted.</span></span> <span data-ttu-id="478a6-115">Kullanıcı tanımlı işlev (UDF) değerini döndürür `bv` .</span><span class="sxs-lookup"><span data-stu-id="478a6-115">The user-defined function (UDF) returns the value of `bv`.</span></span>

```csharp
string v = "Variable to be broadcasted";
Broadcast<string> bv = SparkContext.Broadcast(v);

Func<Column, Column> udf = Udf<string, string>(
    str => $"{str}: {bv.Value()}");
```

## <a name="delete-broadcast-variables"></a><span data-ttu-id="478a6-116">Yayın değişkenlerini Sil</span><span class="sxs-lookup"><span data-stu-id="478a6-116">Delete broadcast variables</span></span>

<span data-ttu-id="478a6-117">Yayın değişkeni, yöntemi çağırarak tüm yürüticilerinden silinebilir `Destroy()` .</span><span class="sxs-lookup"><span data-stu-id="478a6-117">The broadcast variable can be deleted from all executors by calling the `Destroy()` method.</span></span>

```csharp
bv.Destroy();
```

<span data-ttu-id="478a6-118">`Destroy()`Yayın değişkeniyle ilgili tüm verileri ve meta verileri siler ve dikkatli kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="478a6-118">`Destroy()` deletes all data and metadata related to the broadcast variable and should be used with caution.</span></span> <span data-ttu-id="478a6-119">Bir yayın değişkeni yok edildiğinde, tekrar kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="478a6-119">Once a broadcast variable is destroyed, it can't be used again.</span></span>

## <a name="limit-broadcast-variable-scope-in-udfs"></a><span data-ttu-id="478a6-120">UDF 'ler içindeki yayın değişken kapsamını sınırla</span><span class="sxs-lookup"><span data-stu-id="478a6-120">Limit broadcast variable scope in UDFs</span></span>

<span data-ttu-id="478a6-121">UDF 'ler içindeki yayın değişkenlerini kullandığınızda, değişkenin kapsamını yalnızca değişkene başvuran UDF ile sınırlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="478a6-121">When you use broadcast variables in UDFs, you need to limit the scope of the variable to only the UDF that is referencing the variable.</span></span> <span data-ttu-id="478a6-122">[Udf 'leri kullanma kılavuzu](udf-guide.md) , bu olgudur 'u ayrıntılı olarak açıklar.</span><span class="sxs-lookup"><span data-stu-id="478a6-122">The [guide to using UDFs](udf-guide.md) describes this phenomenon in detail.</span></span> <span data-ttu-id="478a6-123">Yayın değişkenini çağırdığınızda kapsam özellikle önemlidir `Destroy()` .</span><span class="sxs-lookup"><span data-stu-id="478a6-123">Scope is especially crucial when you call `Destroy()` on the broadcast variable.</span></span>

<span data-ttu-id="478a6-124">Yok edilen yayın değişkeni diğer UDF 'ler tarafından görülebilir veya erişilebilir durumdaysa, bu, kendileri tarafından başvurulmamış olsa bile tüm UDF 'ler tarafından serileştirme için alınır.</span><span class="sxs-lookup"><span data-stu-id="478a6-124">If the broadcast variable that has been destroyed is visible to or accessible from other UDFs, it gets picked up for serialization by all of the UDFs, even if it is not being referenced by them.</span></span> <span data-ttu-id="478a6-125">Apache Spark için .NET, yok edilmiş yayın değişkenini seri hale getiremedi, bu da hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="478a6-125">.NET for Apache Spark is unable to serialize the destroyed broadcast variable, which results in an error.</span></span> <span data-ttu-id="478a6-126">Aşağıdaki kod parçacığı bu hatayı gösterir:</span><span class="sxs-lookup"><span data-stu-id="478a6-126">The following code snippet demonstrates this error:</span></span>

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

<span data-ttu-id="478a6-127">Aşağıdaki kod parçacığı, `bv` `udf2` beklenmeyen bir serileştirme davranışı nedeniyle yok edilirken hiçbir şekilde etkilenmediğini nasıl güvence altına alınacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="478a6-127">The following code snippet demonstrates how to ensure that destroying `bv` doesn't affect `udf2` because of an unexpected serialization behavior:</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="478a6-128">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="478a6-128">Next steps</span></span>

* [<span data-ttu-id="478a6-129">Apache Spark için .NET ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="478a6-129">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="478a6-130">Windows 'da Apache Spark uygulama için bir .NET hatası ayıklama</span><span class="sxs-lookup"><span data-stu-id="478a6-130">Debug a .NET for Apache Spark application on Windows</span></span>](debug.md)
* [<span data-ttu-id="478a6-131">Apache Spark worker ve Kullanıcı tanımlı işlev ikilileri için .NET dağıtma</span><span class="sxs-lookup"><span data-stu-id="478a6-131">Deploy .NET for Apache Spark worker and user-defined function binaries</span></span>](deploy-worker-udf-binaries.md)
