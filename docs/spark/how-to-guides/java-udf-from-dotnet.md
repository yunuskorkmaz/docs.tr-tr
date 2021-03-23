---
title: Apache Spark uygulaması için .NET 'ten Java UDF 'Leri çağırma
description: Apache Spark uygulamasına yönelik bir Java UDF 'yi nasıl çağıracağınızı öğrenin.
ms.author: nidutta
author: Niharikadutta
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: f85ed5585c8daef0ca9a21275b8de71b2eead360
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875492"
---
# <a name="call-a-java-udf-from-your-net-for-apache-spark-application"></a><span data-ttu-id="a8ac7-103">Apache Spark uygulamasında .NET 'ten bir Java UDF çağrısı yapın</span><span class="sxs-lookup"><span data-stu-id="a8ac7-103">Call a Java UDF from your .NET for Apache Spark application</span></span>

<span data-ttu-id="a8ac7-104">Bu makalede, [Apache Spark uygulamasına yönelik .net](https://github.com/dotnet/spark) 'ten Java User-Defined IŞLEVINI (UDF) çağırmayı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="a8ac7-104">In this article, you learn how to call a Java User-Defined Function (UDF) from your [.NET for Apache Spark](https://github.com/dotnet/spark) application.</span></span>

1. <span data-ttu-id="a8ac7-105">Java UDF 'larınızı tanımlama ve bir jar içinde derleme-Bu adım, bir jar dosyasında zaten tanımlanmış bir UDF 'niz varsa gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="a8ac7-105">How to define your Java UDFs and compile them into a jar - this step is not needed if you already have a UDF defined in a jar file.</span></span> <span data-ttu-id="a8ac7-106">Bu durumda, tüm ihtiyacınız olan paket de dahil olmak üzere UDF işlevinin tam adıdır.</span><span class="sxs-lookup"><span data-stu-id="a8ac7-106">In which case, all you need is the full name of the UDF function including the package.</span></span>
2. <span data-ttu-id="a8ac7-107">Java UDF 'nizi Apache Spark uygulamanızda .NET uygulamanıza kaydedin ve çağırın.</span><span class="sxs-lookup"><span data-stu-id="a8ac7-107">Register and call your Java UDF in your .NET for Apache Spark application.</span></span>

## <a name="define-and-compile-your-java-udfs"></a><span data-ttu-id="a8ac7-108">Java UDF 'larınızı tanımlama ve derleme</span><span class="sxs-lookup"><span data-stu-id="a8ac7-108">Define and compile your Java UDFs</span></span>

1. <span data-ttu-id="a8ac7-109">Maven veya SBT projesi oluşturun ve aşağıdaki bağımlılıkları proje yapılandırma dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a8ac7-109">Create a Maven or SBT project and add the following dependencies into the project configuration file:</span></span>
    1. `org.apache.spark.spark-core_2.11.<version>`
    2. `org.apache.spark.spark-sql_2.11.<version>`
2. <span data-ttu-id="a8ac7-110">[İlgili arabirimi](https://github.com/apache/spark/blob/master/sql/core/src/main/java/org/apache/spark/sql/api/java/UDF1.java) (UDF 'nin imzasına göre) uygulayarak ve ilgili paketi aşağıda gösterildiği gibi basit bir örnekte Içeri AKTARARAK Java UDF 'nizi tanımlayın</span><span class="sxs-lookup"><span data-stu-id="a8ac7-110">Define your Java UDF by implementing the [relevant interface](https://github.com/apache/spark/blob/master/sql/core/src/main/java/org/apache/spark/sql/api/java/UDF1.java) (according to your UDF's signature) and importing the relevant package as shown below in a simple example</span></span>

    ```java
    package com.ScalaUdf.app; // Name of package where UDF is defined
    import org.apache.spark.sql.api.java.UDF1; // UDF interface to implement

    public class JavaUdf implements UDF1<Integer, Integer> { // Name of the Java UDF
        private static final int serialVersionUID = 1;
        @Override
        public Integer call(Integer num) throws Exception { // Define logic of UDF
            return (num + 5);
        }
    }
    ```

3. <span data-ttu-id="a8ac7-111">Projenizi derleyin ve çalıştırılabilir jar, oluşturun ve paketleyin `UdfApp-0.0.1.jar` .</span><span class="sxs-lookup"><span data-stu-id="a8ac7-111">Compile and package your project to create and executable jar say `UdfApp-0.0.1.jar`.</span></span>

## <a name="register-and-call-java-udfs-in-net-for-apache-spark"></a><span data-ttu-id="a8ac7-112">Apache Spark için .NET 'te Java UDF 'Leri kaydedin ve çağırın</span><span class="sxs-lookup"><span data-stu-id="a8ac7-112">Register and call Java UDFs in .NET for Apache Spark</span></span>

1. <span data-ttu-id="a8ac7-113">[`RegisterJava`](https://github.com/dotnet/spark/blob/8dcdcdc7c60d5f42cba5a90f1346d854ab5bf7bb/src/csharp/Microsoft.Spark/Sql/UDFRegistration.cs#L424)Java UDF 'Nizi Spark SQL 'e kaydetmek için API 'yi kullanın.</span><span class="sxs-lookup"><span data-stu-id="a8ac7-113">Use the [`RegisterJava`](https://github.com/dotnet/spark/blob/8dcdcdc7c60d5f42cba5a90f1346d854ab5bf7bb/src/csharp/Microsoft.Spark/Sql/UDFRegistration.cs#L424) API to register your Java UDF with Spark SQL.</span></span>
2. <span data-ttu-id="a8ac7-114">`DataFrame`İşlevini kullanarak UDF 'NIZI SQL tablosu olarak çağırmak istediğiniz öğesine kaydolun [`CreateOrReplaceTempView`](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark/Sql/DataFrame.cs#L982) .</span><span class="sxs-lookup"><span data-stu-id="a8ac7-114">Register the `DataFrame` on which you want to call your UDF as an SQL Table using the [`CreateOrReplaceTempView`](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark/Sql/DataFrame.cs#L982) function.</span></span>
3. <span data-ttu-id="a8ac7-115">`SparkSession.Sql`Spark SQL kullanarak tablo görünümünde UDF 'yi çağırmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="a8ac7-115">Use `SparkSession.Sql` to call the UDF on the table view using Spark SQL.</span></span>
<span data-ttu-id="a8ac7-116">Yukarıdaki adımları göstermek için temel bir örnek:</span><span class="sxs-lookup"><span data-stu-id="a8ac7-116">A basic example to illustrate the above steps:</span></span>

    ```csharp
    class Program
    {
        static void Main()
        {
            SparkSession spark = SparkSession
                .Builder()
                .AppName("Scala/Java UDFs from .NET for Apache Spark")
                .GetOrCreate();
            spark.Udf().RegisterJava<int>("udfAdd5", "com.ScalaUdf.app.JavaUdf"); // Register your Java UDF as 'udfAdd5'
            DataFrame df = spark.CreateDataFrame(new int[] { 2, 5 });
            df.CreateOrReplaceTempView("numbersData"); // Create an SQL table from the DataFrame `df`
            DataFrame dfUdf = spark.Sql("SELECT udfAdd5(_1) As Result FROM numbersData"); // Call the registered UDF on the table
            dfUdf.Show();
            spark.Stop();
        }
    }
    ```

4. <span data-ttu-id="a8ac7-117">Bu uygulamayı kullanarak, `spark-submit` daha önce derlenen Java UDF jar öğesini seçeneğiyle geçirerek gönderebilirsiniz `--jars` :</span><span class="sxs-lookup"><span data-stu-id="a8ac7-117">Submit this application using `spark-submit` by passing the previously compiled Java UDF jar through the `--jars` option:</span></span>

    ```bash
    spark-submit --master local --jars UdfApp-0.0.1.jar --class org.apache.spark.deploy.dotnet.DotnetRunner microsoft-spark-2-4_2.11-1.0.0.jar InterRuntimeUDFs.exe
    ```

    <span data-ttu-id="a8ac7-118">Sonuç `dfUdf` veri çerçevesi, giriş sütununun her satırına, tarafından tanımlandığı şekilde 5 sayı eklenerek `JavaUdf` :</span><span class="sxs-lookup"><span data-stu-id="a8ac7-118">The resultant `dfUdf` DataFrame had the number 5 added to each row of the input column as defined by `JavaUdf`:</span></span>

    ```text
    +-------+
    | Result|
    +-------+
    |      7|
    |     10|
    +-------+
    ```

## <a name="call-net-udf-from-scala-or-python-in-apache-spark"></a><span data-ttu-id="a8ac7-119">Apache Spark içindeki Scala veya Python 'tan .NET UDF 'i çağırma</span><span class="sxs-lookup"><span data-stu-id="a8ac7-119">Call .NET UDF from Scala or Python in Apache Spark</span></span>

<span data-ttu-id="a8ac7-120">Ayrıca, bir C# UDF 'yi, Isla veya Python 'da yazılmış bir Apache Spark uygulamadan [, mini kullanılan açık kaynak aracını](https://github.com/imback82/sparkdotnetudf)kullanarak kaydedebilir ve çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8ac7-120">You can also register and invoke a C# UDF from an Apache Spark application written in Scala or Python using [the sparkdotnetudf open source tool](https://github.com/imback82/sparkdotnetudf).</span></span>
