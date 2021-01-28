---
title: Apache Spark için .NET 'i MongoDB 'ye bağlama
description: Apache Spark uygulamanızın .NET 'ınızdan MongoDB örneğinizi nasıl bağlayacağınızı öğrenin.
ms.author: nidutta
author: Niharikadutta
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 3889088ce32046f72a9a3392e28a5a36cda4745e
ms.sourcegitcommit: 7e42488c2f8f63f6d499b5f8fb1dec5bac9ad254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2021
ms.locfileid: "98957851"
---
# <a name="connect-net-for-apache-spark-to-mongodb"></a>Apache Spark için .NET 'i MongoDB 'ye bağlama

Bu makalede, .NET Apache Spark uygulamasına yönelik bir MongoDB örneğine nasıl bağlanacağınızı öğreneceksiniz.

## <a name="prerequisites"></a>Önkoşullar

- Bir veritabanı ile bir MongoDB sunucusu çalışır ve buna bir [koleksiyon](https://docs.mongodb.com/manual/core/databases-and-collections/) eklenir (bir yerel sunucu için [Bu topluluk sunucusunu](https://www.mongodb.com/try/download/community) Indirin veya bir bulut MongoDB hizmeti Için [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) 'yi deneyebilirsiniz.)

## <a name="set-up-your-mongodb-instance"></a>MongoDB örneğinizi ayarlama

Apache Spark 'nin MongoDB örneğinizle iletişim kurmasını sağlamak için aşağıdakileri yaparak doğru ayarlandığından emin olmanız gerekir:

1. Uygulamanıza bağlanmak için bir Kullanıcı adı ve parola oluşturun ve Mongo kabuğu aracılığıyla aşağıdaki komutu kullanarak kullanıcıya gerekli izinleri/rolleri verin:

    ```bash
    use database
    db.createUser(
      {
        user: "mySparkUser",
        pwd: "<password>",
        roles: [ { role: "userAdminAnyDatabase", db: "admin" }, "readWriteAnyDatabase" ]
      }
    )
    ```

2. Apache Spark uygulamasına yönelik .NET Ağınızın IP adresinin, MongoDB sunucusunun bağlantı kurabilmesi için allowlistelendiğinden emin olun. Bunu nasıl yapacağınızı öğrenmek için [bu kılavuza](https://docs.atlas.mongodb.com/security/add-ip-address-to-list/) başvurabilirsiniz.

## <a name="configure-your-net-for-apache-spark-application"></a>Apache Spark için .NET uygulamanızı yapılandırma

1. Uygulamanızı MongoDB örneğiyle konuşmak ve bir koleksiyondan okumak üzere yapılandırmak için aşağıdaki değişkenleri ayarlayın.
    1. **Authuri**: "uygulamanızı gereken MongoDB örneğine bağlanacak şekilde yetkilendirmek için bağlantı dizesi". Bunun biçimi şu şekildedir:

        ```
        "mongodb+srv://<username>:<password>@<cluster_address>/<database>.<collection>"
        ```

    2. **Kullanıcı adı**: önceki bölümün adım 1 ' de oluşturduğunuz hesabın Kullanıcı adı
    3. **parola**: oluşturulan kullanıcı hesabının parolası
    4. **cluster_address**: MongoDB kümenizin ana bilgisayar adı/adresi
    5. **veritabanı**: bağlanmak Istediğiniz MongoDB veritabanı
    6. **koleksiyon**: okumak Istediğiniz MongoDB koleksiyonu. (Bu örnekte, [`people.json`](https://github.com/apache/spark/blob/master/examples/src/main/resources/people.json) her Apache Spark yüklemesiyle birlikte sunulan standart örnek dosyayı kullanıyoruz.)

2. `com.mongodb.spark.sql.DefaultSource` `spark.Read()` Aşağıdaki biçimi basit bir kod parçacığında aşağıda gösterildiği gibi kullanın:

    ```csharp
    class Program
    {
        static void Main()
        {
            var authURI = "mongodb+srv://<username>:<password>@<cluster_address>/<database>.<collection>?retryWrites=true&w=majority";
            SparkSession spark = SparkSession
                .Builder()
                .AppName("Connect to Mongo DB example")
                .Config("spark.mongodb.input.uri", authURI)
                .GetOrCreate();

            DataFrame df = spark.Read().Format("com.mongodb.spark.sql.DefaultSource").Load();
            df.PrintSchema();
            df.Show();
            spark.Stop();
        }
    }
    ```

## <a name="run-your-application"></a>Uygulamanızı çalıştırma

.NET Apache Spark uygulamanızı çalıştırmak için, ' `mongo-spark-connector` `libraryDependency` ın SBT projelerinde ' de kullanarak, Spark projenizde derleme tanımının bir parçası olarak modülü tanımlamanız gerekir `build.sbt` . `spark-submit`(Veya) gibi Spark ortamları için `spark-shell` , şöyle bir `--packages` komut satırı seçeneğini kullanın:

```bash
spark-submit --master local --packages org.mongodb.spark:mongo-spark-connector_2.12:3.0.0 --class org.apache.spark.deploy.dotnet.DotnetRunner microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar yourApp.exe
```

> [!NOTE]
> Çalıştırılan Spark sürümüne uygun olarak paket sürümünü eklediğinizden emin olun.

Sonuç gösterildiği gibi, burada gösterilen DataFrame ( `df` ) ' dir:

```text
+--------------------+----+-------+
|                 _id| age|   name|
+--------------------+----+-------+
|[5f7c28438029a134...|null|Michael|
|[5f7c287f8029a134...|  30|   Andy|
|[5f7c289a8029a134...|  19| Justin|
+--------------------+----+-------+
```
