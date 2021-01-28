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
# <a name="connect-net-for-apache-spark-to-mongodb"></a><span data-ttu-id="eb785-103">Apache Spark için .NET 'i MongoDB 'ye bağlama</span><span class="sxs-lookup"><span data-stu-id="eb785-103">Connect .NET for Apache Spark to MongoDB</span></span>

<span data-ttu-id="eb785-104">Bu makalede, .NET Apache Spark uygulamasına yönelik bir MongoDB örneğine nasıl bağlanacağınızı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="eb785-104">In this article, you learn how to connect to a MongoDB instance from your .NET for Apache Spark application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="eb785-105">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="eb785-105">Prerequisites</span></span>

- <span data-ttu-id="eb785-106">Bir veritabanı ile bir MongoDB sunucusu çalışır ve buna bir [koleksiyon](https://docs.mongodb.com/manual/core/databases-and-collections/) eklenir (bir yerel sunucu için [Bu topluluk sunucusunu](https://www.mongodb.com/try/download/community) Indirin veya bir bulut MongoDB hizmeti Için [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) 'yi deneyebilirsiniz.)</span><span class="sxs-lookup"><span data-stu-id="eb785-106">Have a MongoDB server up and running with a [database and some collection](https://docs.mongodb.com/manual/core/databases-and-collections/) added to it (Download [this community server](https://www.mongodb.com/try/download/community) for a local server or you can try [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) for a cloud MongoDB service.)</span></span>

## <a name="set-up-your-mongodb-instance"></a><span data-ttu-id="eb785-107">MongoDB örneğinizi ayarlama</span><span class="sxs-lookup"><span data-stu-id="eb785-107">Set up your MongoDB instance</span></span>

<span data-ttu-id="eb785-108">Apache Spark 'nin MongoDB örneğinizle iletişim kurmasını sağlamak için aşağıdakileri yaparak doğru ayarlandığından emin olmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="eb785-108">In order to get .NET for Apache Spark to talk to your MongoDB instance you need to make sure it is set up correctly by doing the following:</span></span>

1. <span data-ttu-id="eb785-109">Uygulamanıza bağlanmak için bir Kullanıcı adı ve parola oluşturun ve Mongo kabuğu aracılığıyla aşağıdaki komutu kullanarak kullanıcıya gerekli izinleri/rolleri verin:</span><span class="sxs-lookup"><span data-stu-id="eb785-109">Create a username and password for your application to connect through, and give the user the necessary permissions/roles using the following command through mongo shell:</span></span>

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

2. <span data-ttu-id="eb785-110">Apache Spark uygulamasına yönelik .NET Ağınızın IP adresinin, MongoDB sunucusunun bağlantı kurabilmesi için allowlistelendiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="eb785-110">Make sure the IP address of the machine your .NET for Apache Spark application is running on is allowlisted for the MongoDB server to be able to connect to.</span></span> <span data-ttu-id="eb785-111">Bunu nasıl yapacağınızı öğrenmek için [bu kılavuza](https://docs.atlas.mongodb.com/security/add-ip-address-to-list/) başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb785-111">You can refer to [this guide](https://docs.atlas.mongodb.com/security/add-ip-address-to-list/) to learn how to do that.</span></span>

## <a name="configure-your-net-for-apache-spark-application"></a><span data-ttu-id="eb785-112">Apache Spark için .NET uygulamanızı yapılandırma</span><span class="sxs-lookup"><span data-stu-id="eb785-112">Configure your .NET for Apache Spark application</span></span>

1. <span data-ttu-id="eb785-113">Uygulamanızı MongoDB örneğiyle konuşmak ve bir koleksiyondan okumak üzere yapılandırmak için aşağıdaki değişkenleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="eb785-113">Have the following variables set to configure your application to talk to the MongoDB instance and read from a collection.</span></span>
    1. <span data-ttu-id="eb785-114">**Authuri**: "uygulamanızı gereken MongoDB örneğine bağlanacak şekilde yetkilendirmek için bağlantı dizesi".</span><span class="sxs-lookup"><span data-stu-id="eb785-114">**authURI**: "Connection string authorizing your application to connect to the required MongoDB instance".</span></span> <span data-ttu-id="eb785-115">Bunun biçimi şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="eb785-115">The format for that is as follows:</span></span>

        ```
        "mongodb+srv://<username>:<password>@<cluster_address>/<database>.<collection>"
        ```

    2. <span data-ttu-id="eb785-116">**Kullanıcı adı**: önceki bölümün adım 1 ' de oluşturduğunuz hesabın Kullanıcı adı</span><span class="sxs-lookup"><span data-stu-id="eb785-116">**username**: Username of the account you created in Step 1 of the previous section</span></span>
    3. <span data-ttu-id="eb785-117">**parola**: oluşturulan kullanıcı hesabının parolası</span><span class="sxs-lookup"><span data-stu-id="eb785-117">**password**: Password of the user account created</span></span>
    4. <span data-ttu-id="eb785-118">**cluster_address**: MongoDB kümenizin ana bilgisayar adı/adresi</span><span class="sxs-lookup"><span data-stu-id="eb785-118">**cluster_address**: hostname/address of your MongoDB cluster</span></span>
    5. <span data-ttu-id="eb785-119">**veritabanı**: bağlanmak Istediğiniz MongoDB veritabanı</span><span class="sxs-lookup"><span data-stu-id="eb785-119">**database**: The MongoDB database you want to connect to</span></span>
    6. <span data-ttu-id="eb785-120">**koleksiyon**: okumak Istediğiniz MongoDB koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="eb785-120">**collection**: The MongoDB collection you want to read.</span></span> <span data-ttu-id="eb785-121">(Bu örnekte, [`people.json`](https://github.com/apache/spark/blob/master/examples/src/main/resources/people.json) her Apache Spark yüklemesiyle birlikte sunulan standart örnek dosyayı kullanıyoruz.)</span><span class="sxs-lookup"><span data-stu-id="eb785-121">(For this example we use the standard [`people.json`](https://github.com/apache/spark/blob/master/examples/src/main/resources/people.json) example file provided with every Apache Spark installation.)</span></span>

2. <span data-ttu-id="eb785-122">`com.mongodb.spark.sql.DefaultSource` `spark.Read()` Aşağıdaki biçimi basit bir kod parçacığında aşağıda gösterildiği gibi kullanın:</span><span class="sxs-lookup"><span data-stu-id="eb785-122">Use the `com.mongodb.spark.sql.DefaultSource` format is `spark.Read()` as shown below in a simple code snippet:</span></span>

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

## <a name="run-your-application"></a><span data-ttu-id="eb785-123">Uygulamanızı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="eb785-123">Run your application</span></span>

<span data-ttu-id="eb785-124">.NET Apache Spark uygulamanızı çalıştırmak için, ' `mongo-spark-connector` `libraryDependency` ın SBT projelerinde ' de kullanarak, Spark projenizde derleme tanımının bir parçası olarak modülü tanımlamanız gerekir `build.sbt` .</span><span class="sxs-lookup"><span data-stu-id="eb785-124">In order to run your .NET for Apache Spark application, you should define the `mongo-spark-connector` module as part of the build definition in your Spark project, using `libraryDependency` in `build.sbt` for sbt projects.</span></span> <span data-ttu-id="eb785-125">`spark-submit`(Veya) gibi Spark ortamları için `spark-shell` , şöyle bir `--packages` komut satırı seçeneğini kullanın:</span><span class="sxs-lookup"><span data-stu-id="eb785-125">For Spark environments such as `spark-submit` (or `spark-shell`), use the `--packages` command-line option like so:</span></span>

```bash
spark-submit --master local --packages org.mongodb.spark:mongo-spark-connector_2.12:3.0.0 --class org.apache.spark.deploy.dotnet.DotnetRunner microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar yourApp.exe
```

> [!NOTE]
> <span data-ttu-id="eb785-126">Çalıştırılan Spark sürümüne uygun olarak paket sürümünü eklediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="eb785-126">Make sure to include the package version in accordance with the version of Spark being run.</span></span>

<span data-ttu-id="eb785-127">Sonuç gösterildiği gibi, burada gösterilen DataFrame ( `df` ) ' dir:</span><span class="sxs-lookup"><span data-stu-id="eb785-127">The result as displayed is the DataFrame (`df`) shown here:</span></span>

```text
+--------------------+----+-------+
|                 _id| age|   name|
+--------------------+----+-------+
|[5f7c28438029a134...|null|Michael|
|[5f7c287f8029a134...|  30|   Andy|
|[5f7c289a8029a134...|  19| Justin|
+--------------------+----+-------+
```
