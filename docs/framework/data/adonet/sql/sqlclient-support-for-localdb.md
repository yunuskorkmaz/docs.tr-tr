---
title: Yerel veritabanı SqlClient desteği
ms.date: 03/30/2017
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
ms.openlocfilehash: 33368ca4b2dc5397087d29e515db6c1094e350bc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33359803"
---
# <a name="sqlclient-support-for-localdb"></a><span data-ttu-id="20908-102">Yerel veritabanı SqlClient desteği</span><span class="sxs-lookup"><span data-stu-id="20908-102">SqlClient Support for LocalDB</span></span>
<span data-ttu-id="20908-103">SQL Server kod adı Denali başlayarak, SQL Server yerel veritabanı, olarak adlandırılan, basit bir sürümü kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="20908-103">Beginning in SQL Server code name Denali, a lightweight version of SQL Server, called LocalDB, will be available.</span></span> <span data-ttu-id="20908-104">Bu konuda bir LocalDB veritabanına bağlanmak nasıl ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="20908-104">This topic discusses how to connect to a LocalDB database.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20908-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="20908-105">Remarks</span></span>  
 <span data-ttu-id="20908-106">Yerel veritabanı yüklemek ve LocalDB örneğinizi yapılandırmak da dahil olmak üzere yerel veritabanı hakkında daha fazla bilgi için SQL Server Books Online'a bakın.</span><span class="sxs-lookup"><span data-stu-id="20908-106">For more information about LocalDB, including how to install LocalDB and configure your LocalDB instance, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="20908-107">Yerel veritabanı ile neler yapabileceğiniz özetlemek için:</span><span class="sxs-lookup"><span data-stu-id="20908-107">To summarize what you can do with LocalDB:</span></span>  
  
-   <span data-ttu-id="20908-108">Oluşturun ve yerel veritabanı örnekleri sqllocaldb.exe veya app.config dosyasını ile başlatın.</span><span class="sxs-lookup"><span data-stu-id="20908-108">Create and start LocalDB instances with sqllocaldb.exe or your app.config file.</span></span>  
  
-   <span data-ttu-id="20908-109">SqlCmd.exe eklemek ve bir yerel veritabanı örneği veritabanlarında değiştirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="20908-109">Use sqlcmd.exe to add and modify databases in a LocalDB instance.</span></span> <span data-ttu-id="20908-110">Örneğin, `sqlcmd -S (localdb)\myinst`.</span><span class="sxs-lookup"><span data-stu-id="20908-110">For example, `sqlcmd -S (localdb)\myinst`.</span></span>  
  
-   <span data-ttu-id="20908-111">Kullanım `AttachDBFilename` bağlantı dizesi anahtar sözcüğü bir veritabanı, yerel veritabanı örneğine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20908-111">Use the `AttachDBFilename` connection string keyword to add a database to your LocalDB instance.</span></span> <span data-ttu-id="20908-112">Kullanırken `AttachDBFilename`, veritabanı adını belirtmezseniz, `Database` bağlantı dizesi anahtar sözcüğü, uygulama kapandığında veritabanı LocalDB örneğinden kaldırılacak.</span><span class="sxs-lookup"><span data-stu-id="20908-112">When using `AttachDBFilename`, if you do not specify the name of the database with the `Database` connection string keyword, the database will be removed from the LocalDB instance when the application closes.</span></span>  
  
-   <span data-ttu-id="20908-113">Bir yerel veritabanı örneği bağlantı dizenizi belirtin.</span><span class="sxs-lookup"><span data-stu-id="20908-113">Specify a LocalDB instance in your connection string.</span></span> <span data-ttu-id="20908-114">Örneğin, örnek adı. `myInstance`, bağlantı dizesi içerir:</span><span class="sxs-lookup"><span data-stu-id="20908-114">For example, your instance name is `myInstance`, the connection string would include:</span></span>  
  
    ```  
    server=(localdb)\\myInstance  
    ```  
  
 <span data-ttu-id="20908-115">`User Instance=True` bir LocalDB veritabanına bağlanırken izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="20908-115">`User Instance=True` is not allowed when connecting to a LocalDB database.</span></span>  
  
 <span data-ttu-id="20908-116">Gelen LocalDB indirebilirsiniz [Microsoft SQL Server 2012 Feature Pack](http://www.microsoft.com/download/en/details.aspx?id=29065).</span><span class="sxs-lookup"><span data-stu-id="20908-116">You can download LocalDB from [Microsoft SQL Server 2012 Feature Pack](http://www.microsoft.com/download/en/details.aspx?id=29065).</span></span> <span data-ttu-id="20908-117">Yerel veritabanı örneğinde veri değiştirmek için sqlcmd.exe kullanacaksa, SQL Server 2012 özellik Paketi'nden almak SQL Server 2012 sqlcmd gerekir.</span><span class="sxs-lookup"><span data-stu-id="20908-117">If you will use sqlcmd.exe to modify data in your LocalDB instance, you will need sqlcmd from SQL Server 2012, which you can also get from the SQL Server 2012 Feature Pack.</span></span>  
  
## <a name="programmatically-create-a-named-instance"></a><span data-ttu-id="20908-118">Adlandırılmış bir örnek program aracılığıyla oluşturma</span><span class="sxs-lookup"><span data-stu-id="20908-118">Programmatically Create a Named Instance</span></span>  
 <span data-ttu-id="20908-119">Bir uygulama, adlandırılmış bir örnek oluşturun ve bir veritabanı gibi belirtin:</span><span class="sxs-lookup"><span data-stu-id="20908-119">An application can create a named instance and specify a database as follows:</span></span>  
  
-   <span data-ttu-id="20908-120">App.config dosyasında şu şekilde oluşturmak için yerel veritabanı örneği belirtin.</span><span class="sxs-lookup"><span data-stu-id="20908-120">Specify the LocalDB instances to create in the app.config file, as follows.</span></span>  <span data-ttu-id="20908-121">Örneğinin sürüm numarası LocalDB yüklemenizin sürüm numarası aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="20908-121">The version number of the instance should be the same as the version number of your LocalDB installation.</span></span>  
  
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
  
-   <span data-ttu-id="20908-122">Kullanarak örnek adı belirtin `server` bağlantı dizesi anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="20908-122">Specify the name of the instance using the `server` connection string keyword.</span></span>  <span data-ttu-id="20908-123">Belirtilen örnek adı `server` bağlantı dizesi anahtar sözcüğü, app.config dosyasında belirtilen adı eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="20908-123">The instance name specified in the `server` connection string keyword must match the name specified in the app.config file.</span></span>  
  
-   <span data-ttu-id="20908-124">Kullanım `AttachDBFilename` belirtmek için bağlantı dizesi anahtar sözcüğü. MDF dosyası.</span><span class="sxs-lookup"><span data-stu-id="20908-124">Use the `AttachDBFilename` connection string keyword to specify the .MDF file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20908-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="20908-125">See Also</span></span>  
 [<span data-ttu-id="20908-126">SQL Server Özellikleri ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="20908-126">SQL Server Features and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md)  
 [<span data-ttu-id="20908-127">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="20908-127">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
