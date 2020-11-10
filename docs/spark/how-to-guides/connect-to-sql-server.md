---
title: Apache Spark için .NET 'e SQL Server bağlama
description: Apache Spark uygulamasına yönelik .NET SQL Server örneğine nasıl bağlanacağınızı öğrenin.
ms.author: nidutta
author: Niharikadutta
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 1fecd796aeefd6c5681c4c2ea623e89f3a5a3c1d
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94439540"
---
# <a name="connect-net-for-apache-spark-to-sql-server"></a>Apache Spark için .NET 'e SQL Server bağlama

Bu makalede, [.net Apache Spark uygulamasına yönelik](https://github.com/dotnet/spark) bir SQL Server örneğine nasıl bağlanacağınızı öğreneceksiniz.

## <a name="configure-sql-server-to-grant-your-application-access"></a>Uygulamanıza erişim izni vermek için SQL Server yapılandırma

1. SQL Server örneğinize SQL Server kimlik doğrulaması seçerek bir oturum açma kullanıcısı ve parolası ekleyin.
2. Bu oturum açma kullanıcısına aşağıda gösterildiği gibi ilgili veritabanı düzeyinde gerekli izinleri verin:

    ![SQL Server izinleri](./media/connect-external-sources/SqlServerAuth.png)

3. SQL Server için varsayılan bağlantı noktasına `1433` güvenlik duvarından izin verildiğinden emin olun.
4. TCP/IP 'yi aşağıda gösterildiği gibi ağ yapılandırması aracılığıyla etkinleştirmek için SQL configure Manager 'ı açın:

    ![SQL Server TCP/IP etkinleştir](./media/connect-external-sources/SqlServerTCPIP.png)

    Ayrıca, **protokol** altındaki Yukarıdaki **Tümünü Dinle** sekmesinde bulunan değeri de aklınızda bulabilirsiniz.

5. TCP/IP bağlantı noktasını tüm gerekli IP adresleri için 1433 olarak ayarlandıysa, ' a `Listen All` ayarlanır `No` . Aksi takdirde, TCP bağlantı noktasını IPAll içinde ayarlayın.

    ![SQL Server TCP/IP bağlantı noktası](./media/connect-external-sources/SQLServerTCPIIPPort.png)

## <a name="connect-to-sql-server-from-your-application"></a>Uygulamanızdan SQL Server bağlama

1. Uygulamanız aracılığıyla veritabanı bağlantısı sağlamak için SQL Server için Microsoft JDBC sürücüsü ( [Bu resmi web sitesinden](/sql/connect/jdbc/download-microsoft-jdbc-driver-for-sql-server?view=sql-server-ver15)indir) kullanın.
2. Uygulamanızdan SQL Server örneğine ve veritabanına bağlanmak için aşağıdaki konfigürasyonları ayarlayın:
    1. **connection_url** : SQL Server örneğine/veritabanına bağlanmak IÇIN kullanılan URL 'dir ve aşağıdaki biçimdedir:

        ```
        jdbc:sqlserver://<SQL_server_IP_address>:1433;instanceName=<instance_name>;databaseName=<database_name>;
        ```

    2. **dbtable** : erişilmekte olan tablonun adı.
    3. **Kullanıcı** : SQL Server 'ı yapılandırma adım 1 ' de oturum açma Kullanıcı Kurulumu.
    4. **parola** : SQL Server 'ı yapılandırmanın 1. adımında ayarlanmış kullanıcının parolası.
3. Aşağıda gösterildiği gibi bir tablodaki verileri okumak için uygulama kodunuzda yukarıdaki yapılandırmayı kullanın:

    ```csharp
    static void Main()
    {
        SparkSession spark = SparkSession
            .Builder()
            .AppName("Connect to SQL Server")
            .GetOrCreate();

        string connection_url = "<URL to connect to SQL server instance>";
        string dbtable = "<database table to access>";
        string user = "<Login user name>";
        string password = "<Login user password>";

        DataFrame jdbcDF = spark.Read()
            .Format("jdbc")
            .Option("driver", "com.microsoft.sqlserver.jdbc.SQLServerDriver")
            .Option("url", connection_url)
            .Option("dbtable", dbtable)
            .Option("user", user)
            .Option("password", password).Load();
        jdbcDF.Show(); // Displays the content of the SQL table as a DataFrame
    }
    ```
