---
title: Apache Spark uygulaması için .NET 'ten Java UDF 'Leri çağırma
description: Apache Spark uygulamasına yönelik bir Java UDF 'yi nasıl çağıracağınızı öğrenin.
ms.author: nidutta
author: Niharikadutta
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: edf525102bf5503dcb51247b5fa590aa0d42b369
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92224120"
---
# <a name="call-a-java-udf-from-your-net-for-apache-spark-application"></a>Apache Spark uygulamasında .NET 'ten bir Java UDF çağrısı yapın

Bu makalede, [Apache Spark uygulamasına yönelik .net](https://github.com/dotnet/spark) 'ten Java User-Defined IŞLEVINI (UDF) çağırmayı öğreneceksiniz.

1. Java UDF 'larınızı tanımlama ve bir jar içinde derleme-Bu adım, bir jar dosyasında zaten tanımlanmış bir UDF 'niz varsa gerekli değildir. Bu durumda, tüm ihtiyacınız olan paket de dahil olmak üzere UDF işlevinin tam adıdır.
2. Java UDF 'nizi Apache Spark uygulamanızda .NET uygulamanıza kaydedin ve çağırın.

## <a name="define-and-compile-your-java-udfs"></a>Java UDF 'larınızı tanımlama ve derleme

1. Maven veya SBT projesi oluşturun ve aşağıdaki bağımlılıkları proje yapılandırma dosyasına ekleyin:
    1. `org.apache.spark.spark-core_2.11.<version>`
    2. `org.apache.spark.spark-sql_2.11.<version>`
2. [İlgili arabirimi](https://github.com/apache/spark/blob/master/sql/core/src/main/java/org/apache/spark/sql/api/java/UDF1.java) (UDF 'nin imzasına göre) uygulayarak ve ilgili paketi aşağıda gösterildiği gibi basit bir örnekte Içeri AKTARARAK Java UDF 'nizi tanımlayın

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

3. Projenizi derleyin ve çalıştırılabilir jar, oluşturun ve paketleyin `UdfApp-0.0.1.jar` .

## <a name="register-and-call-java-udfs-in-net-for-apache-spark"></a>Apache Spark için .NET 'te Java UDF 'Leri kaydedin ve çağırın

1. [`RegisterJava`](https://github.com/dotnet/spark/blob/8dcdcdc7c60d5f42cba5a90f1346d854ab5bf7bb/src/csharp/Microsoft.Spark/Sql/UDFRegistration.cs#L424)Java UDF 'Nizi Spark SQL 'e kaydetmek için API 'yi kullanın.
2. `DataFrame`İşlevini kullanarak UDF 'NIZI SQL tablosu olarak çağırmak istediğiniz öğesine kaydolun [`CreateOrReplaceTempView`](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/DataFrame.cs#L982) .
3. `SparkSession.Sql`Spark SQL kullanarak tablo görünümünde UDF 'yi çağırmak için kullanın.
Yukarıdaki adımları göstermek için temel bir örnek:

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

4. Bu uygulamayı kullanarak, `spark-submit` daha önce derlenen Java UDF jar öğesini seçeneğiyle geçirerek gönderebilirsiniz `--jars` :

    ```bash
    spark-submit --master local --jars UdfApp-0.0.1.jar --class org.apache.spark.deploy.dotnet.DotnetRunner microsoft-spark-3.0.x-0.12.1.jar InterRuntimeUDFs.exe
    ```

    Sonuç `dfUdf` veri çerçevesi, giriş sütununun her satırına, tarafından tanımlandığı şekilde 5 sayı eklenerek `JavaUdf` :

    ```text
    +-------+
    | Result|
    +-------+
    |      7|
    |     10|
    +-------+
    ```

## <a name="call-net-udf-from-scala-or-python-in-apache-spark"></a>Apache Spark içindeki Scala veya Python 'tan .NET UDF 'i çağırma

Ayrıca, bir C# UDF 'yi, Isla veya Python 'da yazılmış bir Apache Spark uygulamadan [, mini kullanılan açık kaynak aracını](https://github.com/imback82/sparkdotnetudf)kullanarak kaydedebilir ve çağırabilirsiniz.
