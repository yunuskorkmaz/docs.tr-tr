---
title: Yerel Veritabanı için SqlClient Desteği
ms.date: 03/30/2017
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
ms.openlocfilehash: 841c455605b0b32668d26cab16a6207dc1c0f716
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203429"
---
# <a name="sqlclient-support-for-localdb"></a><span data-ttu-id="de34b-102">Yerel Veritabanı için SqlClient Desteği</span><span class="sxs-lookup"><span data-stu-id="de34b-102">SqlClient Support for LocalDB</span></span>

<span data-ttu-id="de34b-103">SQL Server kod adından itibaren, LocalDB adlı bir SQL Server basit sürümü kullanıma sunulacaktır.</span><span class="sxs-lookup"><span data-stu-id="de34b-103">Beginning in SQL Server code name Denali, a lightweight version of SQL Server, called LocalDB, will be available.</span></span> <span data-ttu-id="de34b-104">Bu konuda, bir LocalDB veritabanına nasıl bağlanabileceği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="de34b-104">This topic discusses how to connect to a LocalDB database.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de34b-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="de34b-105">Remarks</span></span>  

 <span data-ttu-id="de34b-106">LocalDB 'yi yüklemek ve LocalDB örneğinizi yapılandırmak dahil olmak üzere LocalDB hakkında daha fazla bilgi için bkz. Books Online SQL Server.</span><span class="sxs-lookup"><span data-stu-id="de34b-106">For more information about LocalDB, including how to install LocalDB and configure your LocalDB instance, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="de34b-107">LocalDB ile neler yapabileceğinizi özetlemek için:</span><span class="sxs-lookup"><span data-stu-id="de34b-107">To summarize what you can do with LocalDB:</span></span>  
  
- <span data-ttu-id="de34b-108">sqllocaldb.exe veya app.config dosyanız ile LocalDB örnekleri oluşturun ve başlatın.</span><span class="sxs-lookup"><span data-stu-id="de34b-108">Create and start LocalDB instances with sqllocaldb.exe or your app.config file.</span></span>  
  
- <span data-ttu-id="de34b-109">LocalDB örneğindeki veritabanlarını eklemek ve değiştirmek için sqlcmd.exe kullanın.</span><span class="sxs-lookup"><span data-stu-id="de34b-109">Use sqlcmd.exe to add and modify databases in a LocalDB instance.</span></span> <span data-ttu-id="de34b-110">Örneğin, `sqlcmd -S (localdb)\myinst`.</span><span class="sxs-lookup"><span data-stu-id="de34b-110">For example, `sqlcmd -S (localdb)\myinst`.</span></span>  
  
- <span data-ttu-id="de34b-111">`AttachDBFilename`LocalDB örneğiniz için bir veritabanı eklemek üzere bağlantı dizesi anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="de34b-111">Use the `AttachDBFilename` connection string keyword to add a database to your LocalDB instance.</span></span> <span data-ttu-id="de34b-112">Kullanırken `AttachDBFilename` , `Database` bağlantı dizesi anahtar sözcüğü ile veritabanının adını belirtmezseniz, uygulama kapandığında veritabanı LocalDB örneğinden kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="de34b-112">When using `AttachDBFilename`, if you do not specify the name of the database with the `Database` connection string keyword, the database will be removed from the LocalDB instance when the application closes.</span></span>  
  
- <span data-ttu-id="de34b-113">Bağlantı dizeniz için bir LocalDB örneği belirtin.</span><span class="sxs-lookup"><span data-stu-id="de34b-113">Specify a LocalDB instance in your connection string.</span></span> <span data-ttu-id="de34b-114">Örneğin, örnek adınız `myInstance` , bağlantı dizesinde şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="de34b-114">For example, your instance name is `myInstance`, the connection string would include:</span></span>  
  
    `server=(localdb)\\myInstance`  
  
 <span data-ttu-id="de34b-115">`User Instance=True` bir LocalDB veritabanına bağlanılırken izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="de34b-115">`User Instance=True` is not allowed when connecting to a LocalDB database.</span></span>  
  
 <span data-ttu-id="de34b-116">LocalDB 'yi [Microsoft SQL Server 2012 özellik paketinden](https://www.microsoft.com/download/en/details.aspx?id=29065)indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="de34b-116">You can download LocalDB from [Microsoft SQL Server 2012 Feature Pack](https://www.microsoft.com/download/en/details.aspx?id=29065).</span></span> <span data-ttu-id="de34b-117">LocalDB örneğinizdeki verileri değiştirmek için sqlcmd.exe kullanacaksanız, SQL Server 2012 Feature Pack 'ten de alabileceğiniz SQL Server 2012 ' den sqlcmd gerekir.</span><span class="sxs-lookup"><span data-stu-id="de34b-117">If you will use sqlcmd.exe to modify data in your LocalDB instance, you will need sqlcmd from SQL Server 2012, which you can also get from the SQL Server 2012 Feature Pack.</span></span>  
  
## <a name="programmatically-create-a-named-instance"></a><span data-ttu-id="de34b-118">Program aracılığıyla adlandırılmış bir örnek oluşturma</span><span class="sxs-lookup"><span data-stu-id="de34b-118">Programmatically Create a Named Instance</span></span>  

 <span data-ttu-id="de34b-119">Bir uygulama, adlandırılmış bir örnek oluşturabilir ve aşağıdaki gibi bir veritabanı belirtebilir:</span><span class="sxs-lookup"><span data-stu-id="de34b-119">An application can create a named instance and specify a database as follows:</span></span>  
  
- <span data-ttu-id="de34b-120">app.config dosyasında oluşturulacak LocalDB örneklerini aşağıda gösterildiği gibi belirtin.</span><span class="sxs-lookup"><span data-stu-id="de34b-120">Specify the LocalDB instances to create in the app.config file, as follows.</span></span>  <span data-ttu-id="de34b-121">Örneğin sürüm numarası, LocalDB yüklemenizin sürüm numarasıyla aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="de34b-121">The version number of the instance should be the same as the version number of your LocalDB installation.</span></span>  
  
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
  
- <span data-ttu-id="de34b-122">Bağlantı dizesi anahtar sözcüğünü kullanarak örneğin adını belirtin `server` .</span><span class="sxs-lookup"><span data-stu-id="de34b-122">Specify the name of the instance using the `server` connection string keyword.</span></span>  <span data-ttu-id="de34b-123">`server`Bağlantı dizesi anahtar sözcüğü içinde belirtilen örnek adının app.config dosyasında belirtilen adla eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="de34b-123">The instance name specified in the `server` connection string keyword must match the name specified in the app.config file.</span></span>  
  
- <span data-ttu-id="de34b-124">Öğesini `AttachDBFilename` belirtmek için bağlantı dizesi anahtar sözcüğünü kullanın. MDF dosyası.</span><span class="sxs-lookup"><span data-stu-id="de34b-124">Use the `AttachDBFilename` connection string keyword to specify the .MDF file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de34b-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="de34b-125">See also</span></span>

- [<span data-ttu-id="de34b-126">SQL Server Özellikleri ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="de34b-126">SQL Server Features and ADO.NET</span></span>](sql-server-features-and-adonet.md)
- [<span data-ttu-id="de34b-127">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="de34b-127">ADO.NET Overview</span></span>](../ado-net-overview.md)
