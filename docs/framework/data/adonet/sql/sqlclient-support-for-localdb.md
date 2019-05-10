---
title: Yerel Veritabanı için SqlClient Desteği
ms.date: 03/30/2017
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
ms.openlocfilehash: 23fe0d19ad31c0b09e1a12b5ea25e45a973a14f4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645836"
---
# <a name="sqlclient-support-for-localdb"></a><span data-ttu-id="272e7-102">Yerel Veritabanı için SqlClient Desteği</span><span class="sxs-lookup"><span data-stu-id="272e7-102">SqlClient Support for LocalDB</span></span>
<span data-ttu-id="272e7-103">SQL Server kod adı Denali başlayarak adlı LocalDB, SQL Server'ın basit bir sürümü kullanıma sunulacaktır.</span><span class="sxs-lookup"><span data-stu-id="272e7-103">Beginning in SQL Server code name Denali, a lightweight version of SQL Server, called LocalDB, will be available.</span></span> <span data-ttu-id="272e7-104">Bu konuda, bir LocalDB veritabanına bağlanmak nasıl ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="272e7-104">This topic discusses how to connect to a LocalDB database.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="272e7-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="272e7-105">Remarks</span></span>  
 <span data-ttu-id="272e7-106">LocalDB yükleme ve uygulamanızı LocalDB örneğini yapılandırmak da dahil olmak üzere LocalDB hakkında daha fazla bilgi için SQL Server Books Online'a bakın.</span><span class="sxs-lookup"><span data-stu-id="272e7-106">For more information about LocalDB, including how to install LocalDB and configure your LocalDB instance, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="272e7-107">LocalDB ile neler yapabileceğinizi özetlemek için:</span><span class="sxs-lookup"><span data-stu-id="272e7-107">To summarize what you can do with LocalDB:</span></span>  
  
- <span data-ttu-id="272e7-108">Oluşturup LocalDB örnekleri sqllocaldb.exe veya app.config dosyanız ile başlatın.</span><span class="sxs-lookup"><span data-stu-id="272e7-108">Create and start LocalDB instances with sqllocaldb.exe or your app.config file.</span></span>  
  
- <span data-ttu-id="272e7-109">SqlCmd.exe eklemek ve bir LocalDB örneğini veritabanlarında değiştirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="272e7-109">Use sqlcmd.exe to add and modify databases in a LocalDB instance.</span></span> <span data-ttu-id="272e7-110">Örneğin: `sqlcmd -S (localdb)\myinst`</span><span class="sxs-lookup"><span data-stu-id="272e7-110">For example, `sqlcmd -S (localdb)\myinst`.</span></span>  
  
- <span data-ttu-id="272e7-111">Kullanım `AttachDBFilename` LocalDB Örneğiniz için bir veritabanı eklemek için bağlantı dizesi anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="272e7-111">Use the `AttachDBFilename` connection string keyword to add a database to your LocalDB instance.</span></span> <span data-ttu-id="272e7-112">Kullanırken `AttachDBFilename`, veritabanı adı belirtmezseniz, `Database` bağlantı dizesi anahtar sözcüğü, bir veritabanı uygulama kapandığında LocalDB örneğinden kaldırılacak.</span><span class="sxs-lookup"><span data-stu-id="272e7-112">When using `AttachDBFilename`, if you do not specify the name of the database with the `Database` connection string keyword, the database will be removed from the LocalDB instance when the application closes.</span></span>  
  
- <span data-ttu-id="272e7-113">LocalDB örneğini bağlantı dizenizi belirtin.</span><span class="sxs-lookup"><span data-stu-id="272e7-113">Specify a LocalDB instance in your connection string.</span></span> <span data-ttu-id="272e7-114">Örneğin, örnek adınızdır `myInstance`, bağlantı dizesini içerir:</span><span class="sxs-lookup"><span data-stu-id="272e7-114">For example, your instance name is `myInstance`, the connection string would include:</span></span>  
  
    ```  
    server=(localdb)\\myInstance  
    ```  
  
 <span data-ttu-id="272e7-115">`User Instance=True` bir LocalDB veritabanına bağlanırken izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="272e7-115">`User Instance=True` is not allowed when connecting to a LocalDB database.</span></span>  
  
 <span data-ttu-id="272e7-116">Localdb'den indirebileceğiniz [Microsoft SQL Server 2012 Feature Pack'in](https://www.microsoft.com/download/en/details.aspx?id=29065).</span><span class="sxs-lookup"><span data-stu-id="272e7-116">You can download LocalDB from [Microsoft SQL Server 2012 Feature Pack](https://www.microsoft.com/download/en/details.aspx?id=29065).</span></span> <span data-ttu-id="272e7-117">Sqlcmd.exe LocalDB Örneğinizde verileri değiştirmek için kullanacaksanız, SQL Server 2012 özellik Paketi'nden da edinebilirsiniz SQL Server 2012'den sqlcmd gerekir.</span><span class="sxs-lookup"><span data-stu-id="272e7-117">If you will use sqlcmd.exe to modify data in your LocalDB instance, you will need sqlcmd from SQL Server 2012, which you can also get from the SQL Server 2012 Feature Pack.</span></span>  
  
## <a name="programmatically-create-a-named-instance"></a><span data-ttu-id="272e7-118">Adlandırılmış bir örnek program aracılığıyla oluşturma</span><span class="sxs-lookup"><span data-stu-id="272e7-118">Programmatically Create a Named Instance</span></span>  
 <span data-ttu-id="272e7-119">Bir uygulama, adlandırılmış bir örnek oluşturursanız ve bir veritabanı gibi belirtin:</span><span class="sxs-lookup"><span data-stu-id="272e7-119">An application can create a named instance and specify a database as follows:</span></span>  
  
- <span data-ttu-id="272e7-120">App.config dosyasında gibi oluşturmak üzere LocalDB örneklerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="272e7-120">Specify the LocalDB instances to create in the app.config file, as follows.</span></span>  <span data-ttu-id="272e7-121">Örnek uygulamanın sürüm sayısını LocalDB yüklemenizin sürüm numarası aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="272e7-121">The version number of the instance should be the same as the version number of your LocalDB installation.</span></span>  
  
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
  
- <span data-ttu-id="272e7-122">Kullanarak örnek adını belirtin `server` bağlantı dizesi anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="272e7-122">Specify the name of the instance using the `server` connection string keyword.</span></span>  <span data-ttu-id="272e7-123">Belirtilen örnek adı `server` bağlantı dizesi anahtar kelimesi, app.config dosyasında belirtilen adı eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="272e7-123">The instance name specified in the `server` connection string keyword must match the name specified in the app.config file.</span></span>  
  
- <span data-ttu-id="272e7-124">Kullanım `AttachDBFilename` belirtmek için bağlantı dizesi anahtar sözcüğü. MDF dosyası.</span><span class="sxs-lookup"><span data-stu-id="272e7-124">Use the `AttachDBFilename` connection string keyword to specify the .MDF file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="272e7-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="272e7-125">See also</span></span>

- [<span data-ttu-id="272e7-126">SQL Server Özellikleri ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="272e7-126">SQL Server Features and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md)
- [<span data-ttu-id="272e7-127">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="272e7-127">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
