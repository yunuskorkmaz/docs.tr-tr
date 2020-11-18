---
title: Yerel Veritabanı için SqlClient Desteği
ms.date: 03/30/2017
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
ms.openlocfilehash: 55ab1346de6f5c14f15d01344a984c18edf30e02
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94824486"
---
# <a name="sqlclient-support-for-localdb"></a><span data-ttu-id="adb4d-102">Yerel Veritabanı için SqlClient Desteği</span><span class="sxs-lookup"><span data-stu-id="adb4d-102">SqlClient Support for LocalDB</span></span>

<span data-ttu-id="adb4d-103">Bu makalede bir LocalDB veritabanına nasıl bağlanabileceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="adb4d-103">This article discusses how to connect to a LocalDB database.</span></span> <span data-ttu-id="adb4d-104">LocalDB SQL Server basit bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="adb4d-104">LocalDB is a lightweight version of SQL Server.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="adb4d-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="adb4d-105">Remarks</span></span>
  
 <span data-ttu-id="adb4d-106">LocalDB ile neler yapabileceğinizi özetlemek için:</span><span class="sxs-lookup"><span data-stu-id="adb4d-106">To summarize what you can do with LocalDB:</span></span>  
  
- <span data-ttu-id="adb4d-107">sqllocaldb.exe veya app.config dosyanız ile LocalDB örnekleri oluşturun ve başlatın.</span><span class="sxs-lookup"><span data-stu-id="adb4d-107">Create and start LocalDB instances with sqllocaldb.exe or your app.config file.</span></span>  
  
- <span data-ttu-id="adb4d-108">LocalDB örneğindeki veritabanlarını eklemek ve değiştirmek için sqlcmd.exe kullanın.</span><span class="sxs-lookup"><span data-stu-id="adb4d-108">Use sqlcmd.exe to add and modify databases in a LocalDB instance.</span></span> <span data-ttu-id="adb4d-109">Örneğin, `sqlcmd -S (localdb)\myinst`.</span><span class="sxs-lookup"><span data-stu-id="adb4d-109">For example, `sqlcmd -S (localdb)\myinst`.</span></span>  
  
- <span data-ttu-id="adb4d-110">`AttachDBFilename`LocalDB örneğiniz için bir veritabanı eklemek üzere bağlantı dizesi anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="adb4d-110">Use the `AttachDBFilename` connection string keyword to add a database to your LocalDB instance.</span></span> <span data-ttu-id="adb4d-111">Kullanırken `AttachDBFilename` , `Database` bağlantı dizesi anahtar sözcüğü ile veritabanının adını belirtmezseniz, uygulama kapandığında veritabanı LocalDB örneğinden kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="adb4d-111">When using `AttachDBFilename`, if you do not specify the name of the database with the `Database` connection string keyword, the database will be removed from the LocalDB instance when the application closes.</span></span>  
  
- <span data-ttu-id="adb4d-112">Bağlantı dizeniz için bir LocalDB örneği belirtin.</span><span class="sxs-lookup"><span data-stu-id="adb4d-112">Specify a LocalDB instance in your connection string.</span></span> <span data-ttu-id="adb4d-113">Örneğin, örnek adınız `myInstance` , bağlantı dizesinde şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="adb4d-113">For example, your instance name is `myInstance`, the connection string would include:</span></span>  
  
    `server=(localdb)\\myInstance`  
  
 <span data-ttu-id="adb4d-114">`User Instance=True` bir LocalDB veritabanına bağlanılırken izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="adb4d-114">`User Instance=True` is not allowed when connecting to a LocalDB database.</span></span>  
  
<span data-ttu-id="adb4d-115">LocalDB 'yi yükleme hakkında daha fazla bilgi için bkz. [SQL Server Express LocalDB](/sql/database-engine/configure-windows/sql-server-express-localdb).</span><span class="sxs-lookup"><span data-stu-id="adb4d-115">For information about installing LocalDB, see [SQL Server Express LocalDB](/sql/database-engine/configure-windows/sql-server-express-localdb).</span></span>
  
## <a name="programmatically-create-a-named-instance"></a><span data-ttu-id="adb4d-116">Program aracılığıyla adlandırılmış bir örnek oluşturma</span><span class="sxs-lookup"><span data-stu-id="adb4d-116">Programmatically Create a Named Instance</span></span>  

 <span data-ttu-id="adb4d-117">Bir uygulama, adlandırılmış bir örnek oluşturabilir ve aşağıdaki gibi bir veritabanı belirtebilir:</span><span class="sxs-lookup"><span data-stu-id="adb4d-117">An application can create a named instance and specify a database as follows:</span></span>  
  
- <span data-ttu-id="adb4d-118">app.config dosyasında oluşturulacak LocalDB örneklerini aşağıda gösterildiği gibi belirtin.</span><span class="sxs-lookup"><span data-stu-id="adb4d-118">Specify the LocalDB instances to create in the app.config file, as follows.</span></span>  <span data-ttu-id="adb4d-119">Örneğin sürüm numarası, LocalDB yüklemenizin sürüm numarasıyla aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="adb4d-119">The version number of the instance should be the same as the version number of your LocalDB installation.</span></span>  
  
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
  
- <span data-ttu-id="adb4d-120">Bağlantı dizesi anahtar sözcüğünü kullanarak örneğin adını belirtin `server` .</span><span class="sxs-lookup"><span data-stu-id="adb4d-120">Specify the name of the instance using the `server` connection string keyword.</span></span>  <span data-ttu-id="adb4d-121">`server`Bağlantı dizesi anahtar sözcüğü içinde belirtilen örnek adının app.config dosyasında belirtilen adla eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="adb4d-121">The instance name specified in the `server` connection string keyword must match the name specified in the app.config file.</span></span>  
  
- <span data-ttu-id="adb4d-122">Öğesini `AttachDBFilename` belirtmek için bağlantı dizesi anahtar sözcüğünü kullanın. MDF dosyası.</span><span class="sxs-lookup"><span data-stu-id="adb4d-122">Use the `AttachDBFilename` connection string keyword to specify the .MDF file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adb4d-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="adb4d-123">See also</span></span>

- [<span data-ttu-id="adb4d-124">SQL Server Özellikleri ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="adb4d-124">SQL Server Features and ADO.NET</span></span>](sql-server-features-and-adonet.md)
- [<span data-ttu-id="adb4d-125">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="adb4d-125">ADO.NET Overview</span></span>](../ado-net-overview.md)
