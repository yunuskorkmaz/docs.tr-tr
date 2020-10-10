---
title: Yerel makinenizden uzak depolama 'ya bağlanma
description: Yerel makinenizden Apache Spark için .NET kullanarak Azure Storage hesaplarına bağlanın.
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 09e92b0cae848f9c98b691a11842f131f613396b
ms.sourcegitcommit: eb7e87496f42361b1da98562dd75b516c9d58bbc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91877953"
---
# <a name="connect-to-azure-data-lake-storage-gen-2-or-wasb-account"></a><span data-ttu-id="d9f4c-103">Azure Data Lake Storage Gen 2 veya 1 GB hesabına bağlanma</span><span class="sxs-lookup"><span data-stu-id="d9f4c-103">Connect to Azure Data Lake Storage Gen 2 or WASB account</span></span>

<span data-ttu-id="d9f4c-104">Bu makalede, Windows makinenizde yerel olarak çalışan [Apache Spark için bir .net](https://github.com/dotnet/spark) örneği aracılığıyla bir Azure Data Lake Storage (ADLS) Gen 2 veya Windows Azure Depolama Blobu (lerb) hesabına nasıl bağlanacağınızı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="d9f4c-104">In this article, you learn how to connect to an Azure Data Lake Storage (ADLS) Gen 2 or Windows Azure Storage Blob (WASB) account through an instance of [.NET for Apache Spark](https://github.com/dotnet/spark) running locally on your Windows machine.</span></span>

## <a name="set-up-the-environment"></a><span data-ttu-id="d9f4c-105">Ortamı ayarlama</span><span class="sxs-lookup"><span data-stu-id="d9f4c-105">Set up the environment</span></span>

1. <span data-ttu-id="d9f4c-106">[Resmi Web sitesinden](https://archive.apache.org/dist/spark/) Hadoop olmadan oluşturulan Apache Spark dağıtımını indirin ( [Apache Spark için .NET tarafından desteklenen](https://github.com/dotnet/spark#supported-apache-spark)bir sürüm seçin) ve bir dizine ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="d9f4c-106">Download the Apache Spark distribution built without Hadoop from [official website](https://archive.apache.org/dist/spark/) (choose a version [supported by .NET for Apache Spark](https://github.com/dotnet/spark#supported-apache-spark)), and extract it to a directory.</span></span> <span data-ttu-id="d9f4c-107">Ortam değişkenini `SPARK_HOME` Bu dizine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d9f4c-107">Set the environment variable `SPARK_HOME` to this directory.</span></span>
2. <span data-ttu-id="d9f4c-108">[Buradan](http://hadoop.apache.org/releases.html) Apache Hadoop ikilisini indirin ve bir klasöre ayıklayın ve `HADOOP_HOME` ortam değişkeninizi bu klasöre ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d9f4c-108">Download the Apache Hadoop binary from [here](http://hadoop.apache.org/releases.html) and extract to a folder, and set your `HADOOP_HOME` environment variable to this folder.</span></span>
3. <span data-ttu-id="d9f4c-109">`winutils.exe` `hadoop.dll` [Bu konumdan](https://github.com/cdarlint/winutils) ve dosyalarını indirin (önceki adımda yüklenen Hadoop sürümüne bağlı olarak) ve bunları Hadoop 'nizin bin klasörüne yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="d9f4c-109">Download the `winutils.exe` and `hadoop.dll` files from [this location](https://github.com/cdarlint/winutils) (depending on the version of Hadoop installed in the previous step) and put them in the bin folder of your Hadoop.</span></span> <span data-ttu-id="d9f4c-110">Bu ikili dosyalar, her şeyi doğru şekilde kurmak için Windows 'da gereklidir (Bu, [Apache wiki 'de burada](https://cwiki.apache.org/confluence/display/HADOOP2/WindowsProblems)ayrıntılı olarak açıklanmaktadır).</span><span class="sxs-lookup"><span data-stu-id="d9f4c-110">These binaries are needed on Windows in order to get everything setup correctly (this is explained in detail in the [Apache wiki here](https://cwiki.apache.org/confluence/display/HADOOP2/WindowsProblems)).</span></span>
4. <span data-ttu-id="d9f4c-111">Dosyanıza aşağıdaki değişiklikleri yaparak Hadoop yüklemenizi yapılandırın `%HADOOP_HOME%\etc\hadoop\hadoop-env.cmd` :</span><span class="sxs-lookup"><span data-stu-id="d9f4c-111">Configure your Hadoop installation by making the following changes to your `%HADOOP_HOME%\etc\hadoop\hadoop-env.cmd` file:</span></span>
    1. <span data-ttu-id="d9f4c-112">`JAVA_HOME`DOS yolunu kullanarak özelliği ayarlayın (Hadoop içinde boşluklar olmadığından `JAVA_HOME` ).</span><span class="sxs-lookup"><span data-stu-id="d9f4c-112">Set the `JAVA_HOME` property using the DOS path (since Hadoop doesn't like spaces in `JAVA_HOME`).</span></span> <span data-ttu-id="d9f4c-113">Bu, şunun gibi görünmelidir: `C:\Progra~1\Java\jdk1.8.0_241` (yerel makinenize hangi Java sürümünün yüklendiğini işaret eder).</span><span class="sxs-lookup"><span data-stu-id="d9f4c-113">This should look something like this: `C:\Progra~1\Java\jdk1.8.0_241` (Pointing to whatever version of Java you have installed on your local machine).</span></span>
    2. <span data-ttu-id="d9f4c-114">`%HADOOP_HOME%\share\hadoop\tools\lib\*`Öğesine ekleyin `HADOOP_CLASSPATH` .</span><span class="sxs-lookup"><span data-stu-id="d9f4c-114">Append `%HADOOP_HOME%\share\hadoop\tools\lib\*` to `HADOOP_CLASSPATH`.</span></span>
    <span data-ttu-id="d9f4c-115">Son `hadoop-env.cmd` dosyanız şuna benzer görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="d9f4c-115">Your final `hadoop-env.cmd` file should look something like this:</span></span>

    ![Final Hadoop-env. cmd dosyası](./media/connect-external-sources/hadoop-env.png)

## <a name="configure-your-storage-account-in-hadoop"></a><span data-ttu-id="d9f4c-117">Hadoop 'da depolama hesabınızı yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d9f4c-117">Configure your storage account in Hadoop</span></span>

1. <span data-ttu-id="d9f4c-118">[Azure Portal](https://portal.azure.com) ile bağlanmak istediğiniz ADLS Gen 2 veya bellek depolama hesabını açın ve **Ayarlar** dikey penceresinde **erişim anahtarları** panelini açın ve **anahtarın** değerini KEY1 altına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="d9f4c-118">Open the ADLS Gen 2 or WASB storage account you want to connect to through the [Azure portal](https://portal.azure.com) and open the **Access keys** panel under the **Settings** blade and copy the value of **Key** from under key1.</span></span>
2. <span data-ttu-id="d9f4c-119">Şimdi ADLS 2. hesabınıza erişmek üzere Hadoop yapılandırmak için, `core-site.xml` `%HADOOP_HOME%\etc\hadoop\` küme genelinde yapılandırma içeren (bulunan) dosyanızı düzenlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d9f4c-119">Now in order to configure Hadoop to access your ADLS Gen2 account you would have to edit your `core-site.xml` (located in `%HADOOP_HOME%\etc\hadoop\` ) file which contains cluster-wide configuration.</span></span> <span data-ttu-id="d9f4c-120">Aşağıdaki özellikleri `<configuration>` Bu dosyadaki etiketlerin içine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d9f4c-120">Add the following properties inside the `<configuration>` tags in this file:</span></span>

    ```xml
    <configuration>
      <property>
        <name>fs.azure.account.auth.type.YOUR_ACCOUNT_NAME.dfs.core.windows.net</name>
        <value>SharedKey</value>
        <description></description>
      </property>
      <property>
        <name>fs.azure.account.key.YOUR_ACCOUNT_NAME.dfs.core.windows.net</name>
        <value>YOUR ACCESS KEY (copied from Step 1)</value>
        <description>The secret password. Never share these.</description>
      </property>
    </configuration>
    ```

    <span data-ttu-id="d9f4c-121">Bir ıLB hesabına bağlanmaya çalışıyorsanız, `dfs` `blob` özellik adlarında ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d9f4c-121">If you are trying to connect to a WASB account, replace `dfs` with `blob` in the property names.</span></span> <span data-ttu-id="d9f4c-122">Örneğin, `fs.azure.account.auth.type.YOUR_ACCOUNT_NAME.blob.core.windows.net`.</span><span class="sxs-lookup"><span data-stu-id="d9f4c-122">For example, `fs.azure.account.auth.type.YOUR_ACCOUNT_NAME.blob.core.windows.net`.</span></span>
3. <span data-ttu-id="d9f4c-123">Dizininizden aşağıdaki komutu çalıştırarak, Hadoop 'tan depolama hesabınıza olan bağlantıyı test edebilirsiniz `%HADOOP_HOME%` :</span><span class="sxs-lookup"><span data-stu-id="d9f4c-123">You can test the connectivity to your Storage Account from Hadoop by running the following command from your `%HADOOP_HOME%` directory:</span></span>

    ```bash
    bin\hdfs dfs -ls <URI to your account>
    ```

<span data-ttu-id="d9f4c-124">Bu, URI 'niz tarafından belirtilen yoldaki tüm dosyaların/klasörlerin bir listesini görüntülemelidir.</span><span class="sxs-lookup"><span data-stu-id="d9f4c-124">This should display a list of all files/folders in the path provided by your URI.</span></span>

> [!NOTE]
> <span data-ttu-id="d9f4c-125">Depolama hesabınıza URI 'yi türettiğiniz biçim aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="d9f4c-125">The format to derive the URI to your Storage account is as follows:</span></span>
>
> ```
> For ADLS: abfs[s]://<file_system>@<account_name>.dfs.core.windows.net/<path>/<file_name>
> For WASB: wasb[s]://<file_system>@<account_name>.blob.core.windows.net/<path>/<file_name>
> ```

## <a name="connect-to-your-storage-account"></a><span data-ttu-id="d9f4c-126">Depolama hesabınıza bağlanma</span><span class="sxs-lookup"><span data-stu-id="d9f4c-126">Connect to your storage account</span></span>

1. <span data-ttu-id="d9f4c-127">Yukarıdaki komut işe yaradıysa, Spark aracılığıyla bu depolama hesabına erişmek için artık geçiş yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d9f4c-127">If the above command worked, you can now move on to accessing this storage account through Spark.</span></span> <span data-ttu-id="d9f4c-128">İlk olarak, `hadoop classpath` içindeki komut satırında komutunu çalıştırın `%HADOOP_HOME%` ve çıktıyı kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="d9f4c-128">First run the command `hadoop classpath` from the commandline inside `%HADOOP_HOME%` and copy the output.</span></span>
2. <span data-ttu-id="d9f4c-129">Adım 1 ' de çalıştırılan komutun çıkışını ortam değişkeninin değerine ayarlayın `SPARK_DIST_CLASSPATH` .</span><span class="sxs-lookup"><span data-stu-id="d9f4c-129">Set the output of the command run in Step 1 to the value of environment variable `SPARK_DIST_CLASSPATH`.</span></span>
3. <span data-ttu-id="d9f4c-130">Şimdi aşağıdaki basit örnekte gösterildiği gibi, ADLS veya SUNB depolama hesabınıza, ABFS URI 'sini kullanarak spark .NET aracılığıyla erişebilmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="d9f4c-130">Now you should be able to access your ADLS or WASB storage account through Spark .NET using the abfs URI as shown in the simple example below.</span></span> <span data-ttu-id="d9f4c-131">(Bu örnekte, [`people.json`](https://github.com/apache/spark/blob/master/examples/src/main/resources/people.json) her Apache Spark yüklemesiyle birlikte sunulan standart örnek dosyayı kullanıyoruz.):</span><span class="sxs-lookup"><span data-stu-id="d9f4c-131">(For this example we use the standard [`people.json`](https://github.com/apache/spark/blob/master/examples/src/main/resources/people.json) example file provided with every Apache Spark installation.):</span></span>

    ```csharp
    SparkSession spark = SparkSession
       .Builder()
       .AppName("Connect to Azure Storage locally")
       .GetOrCreate();
    DataFrame df = spark.Read().Json("wasbs://file_system@account_name.blob.core.windows.net/path/people.json");
    //DataFrame df = spark.Read().Json("abfss://file_system@account_name.dfs.core.windows.net/path/file.json");
    df.Show();
    ```

    <span data-ttu-id="d9f4c-132">Sonuç olarak `df` aşağıda gösterildiği gibi veri çerçevesi () görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="d9f4c-132">The result as displayed is the DataFrame (`df`) as shown below:</span></span>

    ```text
    +----+-------+
    | age|   name|
    +----+-------+
    |null|Michael|
    |  30|   Andy|
    |  19| Justin|
    +----+-------+
    ```
