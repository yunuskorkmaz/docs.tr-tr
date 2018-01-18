---
title: "Yerel veritabanı SqlClient desteği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
caps.latest.revision: "14"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a3d643ac386aebf51673f937b3f47e73c749b78f
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="sqlclient-support-for-localdb"></a><span data-ttu-id="725c4-102">Yerel veritabanı SqlClient desteği</span><span class="sxs-lookup"><span data-stu-id="725c4-102">SqlClient Support for LocalDB</span></span>
<span data-ttu-id="725c4-103">' Den başlayarak [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] kod adı Denali, hafif bir sürümüdür ve [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)], yerel veritabanı olarak adlandırılan, kullanılabilir olacaktır.</span><span class="sxs-lookup"><span data-stu-id="725c4-103">Beginning in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] code name Denali, a lightweight version of [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)], called LocalDB, will be available.</span></span> <span data-ttu-id="725c4-104">Bu konuda bir LocalDB veritabanına bağlanmak nasıl ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="725c4-104">This topic discusses how to connect to a LocalDB database.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="725c4-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="725c4-105">Remarks</span></span>  
 <span data-ttu-id="725c4-106">Yerel veritabanı yüklemek ve LocalDB örneğinizi yapılandırmak da dahil olmak üzere yerel veritabanı hakkında daha fazla bilgi için bkz: [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online.</span><span class="sxs-lookup"><span data-stu-id="725c4-106">For more information about LocalDB, including how to install LocalDB and configure your LocalDB instance, see [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="725c4-107">Yerel veritabanı ile neler yapabileceğiniz özetlemek için:</span><span class="sxs-lookup"><span data-stu-id="725c4-107">To summarize what you can do with LocalDB:</span></span>  
  
-   <span data-ttu-id="725c4-108">Oluşturun ve yerel veritabanı örnekleri sqllocaldb.exe veya app.config dosyasını ile başlatın.</span><span class="sxs-lookup"><span data-stu-id="725c4-108">Create and start LocalDB instances with sqllocaldb.exe or your app.config file.</span></span>  
  
-   <span data-ttu-id="725c4-109">SqlCmd.exe eklemek ve bir yerel veritabanı örneği veritabanlarında değiştirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="725c4-109">Use sqlcmd.exe to add and modify databases in a LocalDB instance.</span></span> <span data-ttu-id="725c4-110">Örneğin, `sqlcmd -S (localdb)\myinst`.</span><span class="sxs-lookup"><span data-stu-id="725c4-110">For example, `sqlcmd -S (localdb)\myinst`.</span></span>  
  
-   <span data-ttu-id="725c4-111">Kullanım `AttachDBFilename` bağlantı dizesi anahtar sözcüğü bir veritabanı, yerel veritabanı örneğine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="725c4-111">Use the `AttachDBFilename` connection string keyword to add a database to your LocalDB instance.</span></span> <span data-ttu-id="725c4-112">Kullanırken `AttachDBFilename`, veritabanı adını belirtmezseniz, `Database` bağlantı dizesi anahtar sözcüğü, uygulama kapandığında veritabanı LocalDB örneğinden kaldırılacak.</span><span class="sxs-lookup"><span data-stu-id="725c4-112">When using `AttachDBFilename`, if you do not specify the name of the database with the `Database` connection string keyword, the database will be removed from the LocalDB instance when the application closes.</span></span>  
  
-   <span data-ttu-id="725c4-113">Bir yerel veritabanı örneği bağlantı dizenizi belirtin.</span><span class="sxs-lookup"><span data-stu-id="725c4-113">Specify a LocalDB instance in your connection string.</span></span> <span data-ttu-id="725c4-114">Örneğin, örnek adı. `myInstance`, bağlantı dizesi içerir:</span><span class="sxs-lookup"><span data-stu-id="725c4-114">For example, your instance name is `myInstance`, the connection string would include:</span></span>  
  
    ```  
    server=(localdb)\\myInstance  
    ```  
  
 <span data-ttu-id="725c4-115">`User Instance=True`bir LocalDB veritabanına bağlanırken izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="725c4-115">`User Instance=True` is not allowed when connecting to a LocalDB database.</span></span>  
  
 <span data-ttu-id="725c4-116">Gelen LocalDB indirebilirsiniz [Microsoft SQL Server 2012 Feature Pack](http://www.microsoft.com/download/en/details.aspx?id=29065).</span><span class="sxs-lookup"><span data-stu-id="725c4-116">You can download LocalDB from [Microsoft SQL Server 2012 Feature Pack](http://www.microsoft.com/download/en/details.aspx?id=29065).</span></span> <span data-ttu-id="725c4-117">Yerel veritabanı örneğinde veri değiştirmek için sqlcmd.exe kullanacaksa, gelen sqlcmd gerekir [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] nden de edinebilirsiniz 2012 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012 özellik paketi.</span><span class="sxs-lookup"><span data-stu-id="725c4-117">If you will use sqlcmd.exe to modify data in your LocalDB instance, you will need sqlcmd from [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012, which you can also get from the [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012 Feature Pack.</span></span>  
  
## <a name="programmatically-create-a-named-instance"></a><span data-ttu-id="725c4-118">Adlandırılmış bir örnek program aracılığıyla oluşturma</span><span class="sxs-lookup"><span data-stu-id="725c4-118">Programmatically Create a Named Instance</span></span>  
 <span data-ttu-id="725c4-119">Bir uygulama, adlandırılmış bir örnek oluşturun ve bir veritabanı gibi belirtin:</span><span class="sxs-lookup"><span data-stu-id="725c4-119">An application can create a named instance and specify a database as follows:</span></span>  
  
-   <span data-ttu-id="725c4-120">App.config dosyasında şu şekilde oluşturmak için yerel veritabanı örneği belirtin.</span><span class="sxs-lookup"><span data-stu-id="725c4-120">Specify the LocalDB instances to create in the app.config file, as follows.</span></span>  <span data-ttu-id="725c4-121">Örneğinin sürüm numarası LocalDB yüklemenizin sürüm numarası aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="725c4-121">The version number of the instance should be the same as the version number of your LocalDB installation.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <configSections>  
        <section  
        name="system.data.localdb"  
        type="System.Data.LocalDBConfigurationSection,System.Data,Version=4.0.0.0,Culture=neutral,PublicKeyToken=b77a5c561934e089"/>  
      </configSections>  
      <system.data.localdb>  
        <localdbinstances>  
          <add name="myInstance" version="11.0" />  
        </localdbinstances>  
      </system.data.localdb>  
    </configuration>  
    ```  
  
-   <span data-ttu-id="725c4-122">Kullanarak örnek adı belirtin `server` bağlantı dizesi anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="725c4-122">Specify the name of the instance using the `server` connection string keyword.</span></span>  <span data-ttu-id="725c4-123">Belirtilen örnek adı `server` bağlantı dizesi anahtar sözcüğü, app.config dosyasında belirtilen adı eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="725c4-123">The instance name specified in the `server` connection string keyword must match the name specified in the app.config file.</span></span>  
  
-   <span data-ttu-id="725c4-124">Kullanım `AttachDBFilename` belirtmek için bağlantı dizesi anahtar sözcüğü. MDF dosyası.</span><span class="sxs-lookup"><span data-stu-id="725c4-124">Use the `AttachDBFilename` connection string keyword to specify the .MDF file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="725c4-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="725c4-125">See Also</span></span>  
 [<span data-ttu-id="725c4-126">SQL Server Özellikleri ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="725c4-126">SQL Server Features and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md)  
 [<span data-ttu-id="725c4-127">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="725c4-127">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
