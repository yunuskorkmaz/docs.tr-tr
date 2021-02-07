---
description: 'Daha fazla bilgi edinin: LocalDB için SqlClient desteği'
title: Yerel Veritabanı için SqlClient Desteği
ms.date: 03/30/2017
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
ms.openlocfilehash: f99c46277638c810c91f7ceffd0e47c896125c63
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767173"
---
# <a name="sqlclient-support-for-localdb"></a><span data-ttu-id="56a41-103">Yerel Veritabanı için SqlClient Desteği</span><span class="sxs-lookup"><span data-stu-id="56a41-103">SqlClient Support for LocalDB</span></span>

<span data-ttu-id="56a41-104">Bu makalede bir LocalDB veritabanına nasıl bağlanabileceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="56a41-104">This article discusses how to connect to a LocalDB database.</span></span> <span data-ttu-id="56a41-105">LocalDB SQL Server basit bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="56a41-105">LocalDB is a lightweight version of SQL Server.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="56a41-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="56a41-106">Remarks</span></span>
  
 <span data-ttu-id="56a41-107">LocalDB ile neler yapabileceğinizi özetlemek için:</span><span class="sxs-lookup"><span data-stu-id="56a41-107">To summarize what you can do with LocalDB:</span></span>  
  
- <span data-ttu-id="56a41-108">sqllocaldb.exe veya app.config dosyanız ile LocalDB örnekleri oluşturun ve başlatın.</span><span class="sxs-lookup"><span data-stu-id="56a41-108">Create and start LocalDB instances with sqllocaldb.exe or your app.config file.</span></span>  
  
- <span data-ttu-id="56a41-109">LocalDB örneğindeki veritabanlarını eklemek ve değiştirmek için sqlcmd.exe kullanın.</span><span class="sxs-lookup"><span data-stu-id="56a41-109">Use sqlcmd.exe to add and modify databases in a LocalDB instance.</span></span> <span data-ttu-id="56a41-110">Örneğin, `sqlcmd -S (localdb)\myinst`.</span><span class="sxs-lookup"><span data-stu-id="56a41-110">For example, `sqlcmd -S (localdb)\myinst`.</span></span>  
  
- <span data-ttu-id="56a41-111">`AttachDBFilename`LocalDB örneğiniz için bir veritabanı eklemek üzere bağlantı dizesi anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="56a41-111">Use the `AttachDBFilename` connection string keyword to add a database to your LocalDB instance.</span></span> <span data-ttu-id="56a41-112">Kullanırken `AttachDBFilename` , `Database` bağlantı dizesi anahtar sözcüğü ile veritabanının adını belirtmezseniz, uygulama kapandığında veritabanı LocalDB örneğinden kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="56a41-112">When using `AttachDBFilename`, if you do not specify the name of the database with the `Database` connection string keyword, the database will be removed from the LocalDB instance when the application closes.</span></span>  
  
- <span data-ttu-id="56a41-113">Bağlantı dizeniz için bir LocalDB örneği belirtin.</span><span class="sxs-lookup"><span data-stu-id="56a41-113">Specify a LocalDB instance in your connection string.</span></span> <span data-ttu-id="56a41-114">Örneğin, örnek adınız `myInstance` , bağlantı dizesinde şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="56a41-114">For example, your instance name is `myInstance`, the connection string would include:</span></span>  
  
    `server=(localdb)\\myInstance`  
  
 <span data-ttu-id="56a41-115">`User Instance=True` bir LocalDB veritabanına bağlanılırken izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="56a41-115">`User Instance=True` is not allowed when connecting to a LocalDB database.</span></span>  
  
<span data-ttu-id="56a41-116">LocalDB 'yi yükleme hakkında daha fazla bilgi için bkz. [SQL Server Express LocalDB](/sql/database-engine/configure-windows/sql-server-express-localdb).</span><span class="sxs-lookup"><span data-stu-id="56a41-116">For information about installing LocalDB, see [SQL Server Express LocalDB](/sql/database-engine/configure-windows/sql-server-express-localdb).</span></span>
  
## <a name="programmatically-create-a-named-instance"></a><span data-ttu-id="56a41-117">Program aracılığıyla adlandırılmış bir örnek oluşturma</span><span class="sxs-lookup"><span data-stu-id="56a41-117">Programmatically Create a Named Instance</span></span>  

 <span data-ttu-id="56a41-118">Bir uygulama, adlandırılmış bir örnek oluşturabilir ve aşağıdaki gibi bir veritabanı belirtebilir:</span><span class="sxs-lookup"><span data-stu-id="56a41-118">An application can create a named instance and specify a database as follows:</span></span>  
  
- <span data-ttu-id="56a41-119">app.config dosyasında oluşturulacak LocalDB örneklerini aşağıda gösterildiği gibi belirtin.</span><span class="sxs-lookup"><span data-stu-id="56a41-119">Specify the LocalDB instances to create in the app.config file, as follows.</span></span>  <span data-ttu-id="56a41-120">Örneğin sürüm numarası, LocalDB yüklemenizin sürüm numarasıyla aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="56a41-120">The version number of the instance should be the same as the version number of your LocalDB installation.</span></span>  
  
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
  
- <span data-ttu-id="56a41-121">Bağlantı dizesi anahtar sözcüğünü kullanarak örneğin adını belirtin `server` .</span><span class="sxs-lookup"><span data-stu-id="56a41-121">Specify the name of the instance using the `server` connection string keyword.</span></span>  <span data-ttu-id="56a41-122">`server`Bağlantı dizesi anahtar sözcüğü içinde belirtilen örnek adının app.config dosyasında belirtilen adla eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="56a41-122">The instance name specified in the `server` connection string keyword must match the name specified in the app.config file.</span></span>  
  
- <span data-ttu-id="56a41-123">Öğesini `AttachDBFilename` belirtmek için bağlantı dizesi anahtar sözcüğünü kullanın. MDF dosyası.</span><span class="sxs-lookup"><span data-stu-id="56a41-123">Use the `AttachDBFilename` connection string keyword to specify the .MDF file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56a41-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56a41-124">See also</span></span>

- [<span data-ttu-id="56a41-125">SQL Server Özellikleri ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="56a41-125">SQL Server Features and ADO.NET</span></span>](sql-server-features-and-adonet.md)
- [<span data-ttu-id="56a41-126">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="56a41-126">ADO.NET Overview</span></span>](../ado-net-overview.md)
