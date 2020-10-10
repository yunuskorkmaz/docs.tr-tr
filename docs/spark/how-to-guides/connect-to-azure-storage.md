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
# <a name="connect-to-azure-data-lake-storage-gen-2-or-wasb-account"></a>Azure Data Lake Storage Gen 2 veya 1 GB hesabına bağlanma

Bu makalede, Windows makinenizde yerel olarak çalışan [Apache Spark için bir .net](https://github.com/dotnet/spark) örneği aracılığıyla bir Azure Data Lake Storage (ADLS) Gen 2 veya Windows Azure Depolama Blobu (lerb) hesabına nasıl bağlanacağınızı öğreneceksiniz.

## <a name="set-up-the-environment"></a>Ortamı ayarlama

1. [Resmi Web sitesinden](https://archive.apache.org/dist/spark/) Hadoop olmadan oluşturulan Apache Spark dağıtımını indirin ( [Apache Spark için .NET tarafından desteklenen](https://github.com/dotnet/spark#supported-apache-spark)bir sürüm seçin) ve bir dizine ayıklayın. Ortam değişkenini `SPARK_HOME` Bu dizine ayarlayın.
2. [Buradan](http://hadoop.apache.org/releases.html) Apache Hadoop ikilisini indirin ve bir klasöre ayıklayın ve `HADOOP_HOME` ortam değişkeninizi bu klasöre ayarlayın.
3. `winutils.exe` `hadoop.dll` [Bu konumdan](https://github.com/cdarlint/winutils) ve dosyalarını indirin (önceki adımda yüklenen Hadoop sürümüne bağlı olarak) ve bunları Hadoop 'nizin bin klasörüne yerleştirin. Bu ikili dosyalar, her şeyi doğru şekilde kurmak için Windows 'da gereklidir (Bu, [Apache wiki 'de burada](https://cwiki.apache.org/confluence/display/HADOOP2/WindowsProblems)ayrıntılı olarak açıklanmaktadır).
4. Dosyanıza aşağıdaki değişiklikleri yaparak Hadoop yüklemenizi yapılandırın `%HADOOP_HOME%\etc\hadoop\hadoop-env.cmd` :
    1. `JAVA_HOME`DOS yolunu kullanarak özelliği ayarlayın (Hadoop içinde boşluklar olmadığından `JAVA_HOME` ). Bu, şunun gibi görünmelidir: `C:\Progra~1\Java\jdk1.8.0_241` (yerel makinenize hangi Java sürümünün yüklendiğini işaret eder).
    2. `%HADOOP_HOME%\share\hadoop\tools\lib\*`Öğesine ekleyin `HADOOP_CLASSPATH` .
    Son `hadoop-env.cmd` dosyanız şuna benzer görünmelidir:

    ![Final Hadoop-env. cmd dosyası](./media/connect-external-sources/hadoop-env.png)

## <a name="configure-your-storage-account-in-hadoop"></a>Hadoop 'da depolama hesabınızı yapılandırma

1. [Azure Portal](https://portal.azure.com) ile bağlanmak istediğiniz ADLS Gen 2 veya bellek depolama hesabını açın ve **Ayarlar** dikey penceresinde **erişim anahtarları** panelini açın ve **anahtarın** değerini KEY1 altına kopyalayın.
2. Şimdi ADLS 2. hesabınıza erişmek üzere Hadoop yapılandırmak için, `core-site.xml` `%HADOOP_HOME%\etc\hadoop\` küme genelinde yapılandırma içeren (bulunan) dosyanızı düzenlemeniz gerekir. Aşağıdaki özellikleri `<configuration>` Bu dosyadaki etiketlerin içine ekleyin:

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

    Bir ıLB hesabına bağlanmaya çalışıyorsanız, `dfs` `blob` özellik adlarında ile değiştirin. Örneğin, `fs.azure.account.auth.type.YOUR_ACCOUNT_NAME.blob.core.windows.net`.
3. Dizininizden aşağıdaki komutu çalıştırarak, Hadoop 'tan depolama hesabınıza olan bağlantıyı test edebilirsiniz `%HADOOP_HOME%` :

    ```bash
    bin\hdfs dfs -ls <URI to your account>
    ```

Bu, URI 'niz tarafından belirtilen yoldaki tüm dosyaların/klasörlerin bir listesini görüntülemelidir.

> [!NOTE]
> Depolama hesabınıza URI 'yi türettiğiniz biçim aşağıdaki gibidir:
>
> ```
> For ADLS: abfs[s]://<file_system>@<account_name>.dfs.core.windows.net/<path>/<file_name>
> For WASB: wasb[s]://<file_system>@<account_name>.blob.core.windows.net/<path>/<file_name>
> ```

## <a name="connect-to-your-storage-account"></a>Depolama hesabınıza bağlanma

1. Yukarıdaki komut işe yaradıysa, Spark aracılığıyla bu depolama hesabına erişmek için artık geçiş yapabilirsiniz. İlk olarak, `hadoop classpath` içindeki komut satırında komutunu çalıştırın `%HADOOP_HOME%` ve çıktıyı kopyalayın.
2. Adım 1 ' de çalıştırılan komutun çıkışını ortam değişkeninin değerine ayarlayın `SPARK_DIST_CLASSPATH` .
3. Şimdi aşağıdaki basit örnekte gösterildiği gibi, ADLS veya SUNB depolama hesabınıza, ABFS URI 'sini kullanarak spark .NET aracılığıyla erişebilmelisiniz. (Bu örnekte, [`people.json`](https://github.com/apache/spark/blob/master/examples/src/main/resources/people.json) her Apache Spark yüklemesiyle birlikte sunulan standart örnek dosyayı kullanıyoruz.):

    ```csharp
    SparkSession spark = SparkSession
       .Builder()
       .AppName("Connect to Azure Storage locally")
       .GetOrCreate();
    DataFrame df = spark.Read().Json("wasbs://file_system@account_name.blob.core.windows.net/path/people.json");
    //DataFrame df = spark.Read().Json("abfss://file_system@account_name.dfs.core.windows.net/path/file.json");
    df.Show();
    ```

    Sonuç olarak `df` aşağıda gösterildiği gibi veri çerçevesi () görüntülenir:

    ```text
    +----+-------+
    | age|   name|
    +----+-------+
    |null|Michael|
    |  30|   Andy|
    |  19| Justin|
    +----+-------+
    ```
