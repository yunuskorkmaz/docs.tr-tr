---
title: Apache Spark için .NET 'e SQL Server bağlama
description: Apache Spark uygulamasına yönelik .NET SQL Server örneğine nasıl bağlanacağınızı öğrenin.
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 773e743a67c066438cb86d983ebfa34f73692c2d
ms.sourcegitcommit: eb7e87496f42361b1da98562dd75b516c9d58bbc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91877951"
---
# <a name="connect-net-for-apache-spark-to-sql-server"></a><span data-ttu-id="88a3a-103">Apache Spark için .NET 'e SQL Server bağlama</span><span class="sxs-lookup"><span data-stu-id="88a3a-103">Connect .NET for Apache Spark to SQL Server</span></span>

<span data-ttu-id="88a3a-104">Bu makalede, [.net Apache Spark uygulamasına yönelik](https://github.com/dotnet/spark) bir SQL Server örneğine nasıl bağlanacağınızı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="88a3a-104">In this article, you learn how to connect to an SQL server instance from your [.NET for Apache Spark](https://github.com/dotnet/spark) application.</span></span>

## <a name="configure-sql-server-to-grant-your-application-access"></a><span data-ttu-id="88a3a-105">Uygulamanıza erişim izni vermek için SQL Server yapılandırma</span><span class="sxs-lookup"><span data-stu-id="88a3a-105">Configure SQL Server to grant your application access</span></span>

1. <span data-ttu-id="88a3a-106">SQL Server örneğinize SQL Server kimlik doğrulaması seçerek bir oturum açma kullanıcısı ve parolası ekleyin.</span><span class="sxs-lookup"><span data-stu-id="88a3a-106">Add a login user and password choosing SQL Server authentication to your SQL Server instance.</span></span>
2. <span data-ttu-id="88a3a-107">Bu oturum açma kullanıcısına aşağıda gösterildiği gibi ilgili veritabanı düzeyinde gerekli izinleri verin:</span><span class="sxs-lookup"><span data-stu-id="88a3a-107">Give that login user necessary permissions at the relevant database level as shown below:</span></span>

    ![SQL Server izinleri](./media/connect-external-sources/SqlServerAuth.png)

3. <span data-ttu-id="88a3a-109">SQL Server için varsayılan bağlantı noktasına `1433` güvenlik duvarından izin verildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="88a3a-109">Make sure the default port for SQL Server `1433` is allowed through the firewall.</span></span>
4. <span data-ttu-id="88a3a-110">TCP/IP 'yi aşağıda gösterildiği gibi ağ yapılandırması aracılığıyla etkinleştirmek için SQL configure Manager 'ı açın:</span><span class="sxs-lookup"><span data-stu-id="88a3a-110">Open SQL configure manager to enable TCP/IP through the network configuration as shown below:</span></span>

    ![SQL Server TCP/IP etkinleştir](./media/connect-external-sources/SqlServerTCPIP.png)

    <span data-ttu-id="88a3a-112">Ayrıca, **protokol**altındaki Yukarıdaki **Tümünü Dinle** sekmesinde bulunan değeri de aklınızda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="88a3a-112">Also note the value of **Listen All** in above tab under **Protocol**.</span></span>

5. <span data-ttu-id="88a3a-113">TCP/IP bağlantı noktasını tüm gerekli IP adresleri için 1433 olarak ayarlandıysa, ' a `Listen All` ayarlanır `No` .</span><span class="sxs-lookup"><span data-stu-id="88a3a-113">Configure the TCP/IP port to 1433 for all required IP addresses if the `Listen All` is set to `No`.</span></span> <span data-ttu-id="88a3a-114">Aksi takdirde, TCP bağlantı noktasını IPAll içinde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="88a3a-114">Otherwise, set the TCP Port in IPAll.</span></span>

    ![SQL Server TCP/IP bağlantı noktası](./media/connect-external-sources/SQLServerTCPIIPPort.png)

## <a name="connect-to-sql-server-from-your-application"></a><span data-ttu-id="88a3a-116">Uygulamanızdan SQL Server bağlama</span><span class="sxs-lookup"><span data-stu-id="88a3a-116">Connect to SQL Server from your application</span></span>

1. <span data-ttu-id="88a3a-117">Uygulamanız aracılığıyla veritabanı bağlantısı sağlamak için SQL Server için Microsoft JDBC sürücüsü ( [Bu resmi web sitesinden](https://docs.microsoft.com/sql/connect/jdbc/download-microsoft-jdbc-driver-for-sql-server?view=sql-server-ver15)indir) kullanın.</span><span class="sxs-lookup"><span data-stu-id="88a3a-117">Use the Microsoft JDBC Driver for SQL Server to provide database connectivity through your application (download from [this official website](https://docs.microsoft.com/sql/connect/jdbc/download-microsoft-jdbc-driver-for-sql-server?view=sql-server-ver15)).</span></span>
2. <span data-ttu-id="88a3a-118">Uygulamanızdan SQL Server örneğine ve veritabanına bağlanmak için aşağıdaki konfigürasyonları ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="88a3a-118">Set the following configurations to connect to the SQL server instance and database from your application:</span></span>
    1. <span data-ttu-id="88a3a-119">**connection_url**: SQL Server örneğine/veritabanına bağlanmak IÇIN kullanılan URL 'dir ve aşağıdaki biçimdedir:</span><span class="sxs-lookup"><span data-stu-id="88a3a-119">**connection_url**: This is the URL used to connect to the SQL server instance/database and has the following format:</span></span>

        ```
        jdbc:sqlserver://<SQL_server_IP_address>:1433;instanceName=<instance_name>;databaseName=<database_name>;
        ```

    2. <span data-ttu-id="88a3a-120">**dbtable**: erişilmekte olan tablonun adı.</span><span class="sxs-lookup"><span data-stu-id="88a3a-120">**dbtable**: Name of table being accessed.</span></span>
    3. <span data-ttu-id="88a3a-121">**Kullanıcı**: SQL Server 'ı yapılandırma adım 1 ' de oturum açma Kullanıcı Kurulumu.</span><span class="sxs-lookup"><span data-stu-id="88a3a-121">**user**: Login user set up in Step 1 of configuring the SQL server.</span></span>
    4. <span data-ttu-id="88a3a-122">**parola**: SQL Server 'ı yapılandırmanın 1. adımında ayarlanmış kullanıcının parolası.</span><span class="sxs-lookup"><span data-stu-id="88a3a-122">**password**: Password of user set up in Step 1 of configuring the SQL server.</span></span>
3. <span data-ttu-id="88a3a-123">Aşağıda gösterildiği gibi bir tablodaki verileri okumak için uygulama kodunuzda yukarıdaki yapılandırmayı kullanın:</span><span class="sxs-lookup"><span data-stu-id="88a3a-123">Use the above configuration in your application code to read the data from a table as shown below:</span></span>

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
