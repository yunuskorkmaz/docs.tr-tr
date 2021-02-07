---
description: 'Hakkında daha fazla bilgi edinin: SQL Server çapraz veritabanı erişimini etkinleştirme'
title: SQL Server'da Veritabanları Arası Erişimi Etkinleştirme
ms.date: 03/30/2017
ms.assetid: 10663fb6-434c-4c81-8178-ec894b9cf895
ms.openlocfilehash: 4e818b4f0294fdc7edd351a1e60203357579a320
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695872"
---
# <a name="enabling-cross-database-access-in-sql-server"></a><span data-ttu-id="6a126-103">SQL Server'da Veritabanları Arası Erişimi Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="6a126-103">Enabling Cross-Database Access in SQL Server</span></span>

<span data-ttu-id="6a126-104">Veritabanları arası sahiplik zinciri, bir veritabanındaki bir yordam başka bir veritabanındaki nesnelere bağımlıysa oluşur.</span><span class="sxs-lookup"><span data-stu-id="6a126-104">Cross-database ownership chaining occurs when a procedure in one database depends on objects in another database.</span></span> <span data-ttu-id="6a126-105">Veritabanları arası sahiplik zinciri, tek bir veritabanı içindeki sahiplik zinciriyle aynı şekilde çalışarak, bozuk bir sahiplik zinciri, tüm nesne sahiplerinin aynı oturum açma hesabıyla eşlenmesini gerektirmesidir.</span><span class="sxs-lookup"><span data-stu-id="6a126-105">A cross-database ownership chain works in the same way as ownership chaining within a single database, except that an unbroken ownership chain requires that all the object owners are mapped to the same login account.</span></span> <span data-ttu-id="6a126-106">Kaynak veritabanındaki kaynak nesne ve hedef veritabanlarındaki hedef nesneler aynı oturum açma hesabına aitse, SQL Server hedef nesnelerdeki izinleri denetlemez.</span><span class="sxs-lookup"><span data-stu-id="6a126-106">If the source object in the source database and the target objects in the target databases are owned by the same login account, SQL Server does not check permissions on the target objects.</span></span>  
  
## <a name="off-by-default"></a><span data-ttu-id="6a126-107">Varsayılan olarak kapalı</span><span class="sxs-lookup"><span data-stu-id="6a126-107">Off By Default</span></span>  

 <span data-ttu-id="6a126-108">Veritabanları arasında sahiplik zinciri varsayılan olarak kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="6a126-108">Ownership chaining across databases is turned off by default.</span></span> <span data-ttu-id="6a126-109">Microsoft, aşağıdaki güvenlik risklerini size gösterdiğinden, veritabanları arası sahiplik zincirlemeyi devre dışı bırakmanızı önerir:</span><span class="sxs-lookup"><span data-stu-id="6a126-109">Microsoft recommends that you disable cross-database ownership chaining because it exposes you to the following security risks:</span></span>  
  
- <span data-ttu-id="6a126-110">Veritabanı sahipleri ve `db_ddladmin` veya veritabanı rollerinin üyeleri, `db_owners` diğer kullanıcılara ait nesneler oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="6a126-110">Database owners and members of the `db_ddladmin` or the `db_owners` database roles can create objects that are owned by other users.</span></span> <span data-ttu-id="6a126-111">Bu nesneler, diğer veritabanlarındaki nesneleri hedefleyebilir.</span><span class="sxs-lookup"><span data-stu-id="6a126-111">These objects can potentially target objects in other databases.</span></span> <span data-ttu-id="6a126-112">Bu, veritabanları arası sahiplik zincirlemeyi etkinleştirirseniz bu kullanıcılara tüm veritabanlarındaki verilerle tam olarak güvenmeniz gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6a126-112">This means that if you enable cross-database ownership chaining, you must fully trust these users with data in all databases.</span></span>  
  
- <span data-ttu-id="6a126-113">VERITABANı oluştur iznine sahip kullanıcılar yeni veritabanları oluşturabilir ve var olan veritabanlarını ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="6a126-113">Users with CREATE DATABASE permission can create new databases and attach existing databases.</span></span> <span data-ttu-id="6a126-114">Veritabanları arası sahiplik zinciri etkinse, bu kullanıcılar, oluşturdukları yeni oluşturulan veya eklenen veritabanlarından ayrıcalıklarına sahip olmadıkları diğer veritabanlarındaki nesnelere erişebilir.</span><span class="sxs-lookup"><span data-stu-id="6a126-114">If cross-database ownership chaining is enabled, these users can access objects in other databases that they might not have privileges in from the newly created or attached databases that they create.</span></span>  
  
## <a name="enabling-cross-database-ownership-chaining"></a><span data-ttu-id="6a126-115">Veritabanları arası sahiplik zincirlemeyi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="6a126-115">Enabling Cross-database Ownership Chaining</span></span>  

 <span data-ttu-id="6a126-116">Veritabanları arası sahiplik zinciri yalnızca yüksek ayrıcalıklı kullanıcılara tam güvenebileceğiniz ortamlarda etkinleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="6a126-116">Cross-database ownership chaining should only be enabled in environments where you can fully trust highly-privileged users.</span></span> <span data-ttu-id="6a126-117">Tüm veritabanları için kurulum sırasında veya Transact-SQL komutları kullanılarak belirli veritabanlarına seçmeli olarak yapılandırılabilir `sp_configure` `ALTER DATABASE` .</span><span class="sxs-lookup"><span data-stu-id="6a126-117">It can be configured during setup for all databases, or selectively for specific databases using the Transact-SQL commands `sp_configure` and `ALTER DATABASE`.</span></span>  
  
 <span data-ttu-id="6a126-118">Veritabanları arası sahiplik zincirlemeyi seçmeli olarak yapılandırmak için, ' yi kullanarak `sp_configure` sunucu için devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="6a126-118">To selectively configure cross-database ownership chaining, use `sp_configure` to turn it off for the server.</span></span> <span data-ttu-id="6a126-119">Ardından, tek yapmanız gereken veritabanları için veritabanları arası sahiplik zincirlemesini yapılandırmak üzere DB_CHAINING SET ile ALTER DATABASE komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="6a126-119">Then use the ALTER DATABASE command with SET DB_CHAINING ON to configure cross-database ownership chaining for only the databases that require it.</span></span>  
  
 <span data-ttu-id="6a126-120">Aşağıdaki örnek, tüm veritabanları için çapraz veritabanı sahiplik zincirlemesini etkinleştirir:</span><span class="sxs-lookup"><span data-stu-id="6a126-120">The following sample turns on cross-database ownership chaining for all databases:</span></span>  
  
```sql
EXECUTE sp_configure 'show advanced', 1;  
RECONFIGURE;  
EXECUTE sp_configure 'cross db ownership chaining', 1;  
RECONFIGURE;  
```  
  
 <span data-ttu-id="6a126-121">Aşağıdaki örnek, belirli veritabanları için veritabanları arası sahiplik zincirlemeyi etkinleştirir:</span><span class="sxs-lookup"><span data-stu-id="6a126-121">The following sample turns on cross-database ownership chaining for specific databases:</span></span>  
  
```sql
ALTER DATABASE Database1 SET DB_CHAINING ON;  
ALTER DATABASE Database2 SET DB_CHAINING ON;  
```  
  
### <a name="dynamic-sql"></a><span data-ttu-id="6a126-122">Dinamik SQL</span><span class="sxs-lookup"><span data-stu-id="6a126-122">Dynamic SQL</span></span>  

 <span data-ttu-id="6a126-123">Veritabanları arası sahiplik zinciri, aynı kullanıcı her iki veritabanında da mevcut olmadığı takdirde dinamik olarak oluşturulan SQL deyimlerinin yürütüldüğü durumlarda çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="6a126-123">Cross-database ownership chaining does not work in cases where dynamically created SQL statements are executed unless the same user exists in both databases.</span></span> <span data-ttu-id="6a126-124">Başka bir veritabanındaki verilere erişen ve yordamı her iki veritabanında bulunan bir sertifikayla imzalayan bir saklı yordam oluşturarak bu SQL Server geçici bir çözüm bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6a126-124">You can work around this in SQL Server by creating a stored procedure that accesses data in another database and signing the procedure with a certificate that exists in both databases.</span></span> <span data-ttu-id="6a126-125">Bu, kullanıcılara veritabanı erişimi veya izinleri vermeden yordam tarafından kullanılan veritabanı kaynaklarına erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="6a126-125">This gives users access to the database resources used by the procedure without granting them database access or permissions.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="6a126-126">Dış Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="6a126-126">External Resources</span></span>  

 <span data-ttu-id="6a126-127">Daha fazla bilgi için aşağıdaki kaynaklara bakın.</span><span class="sxs-lookup"><span data-stu-id="6a126-127">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="6a126-128">Kaynak</span><span class="sxs-lookup"><span data-stu-id="6a126-128">Resource</span></span>|<span data-ttu-id="6a126-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a126-129">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="6a126-130">FARKLı ÇALıŞTıR ve [çapraz veritabanı sahiplik zinciri seçeneğini](/sql/database-engine/configure-windows/cross-db-ownership-chaining-server-configuration-option) [kullanarak veritabanı kimliğe bürünme özelliğini genişletme](/previous-versions/sql/sql-server-2008-r2/ms188304(v=sql.105)) .</span><span class="sxs-lookup"><span data-stu-id="6a126-130">[Extending Database Impersonation by Using EXECUTE AS](/previous-versions/sql/sql-server-2008-r2/ms188304(v=sql.105)) and [Cross DB Ownership Chaining Option](/sql/database-engine/configure-windows/cross-db-ownership-chaining-server-configuration-option).</span></span>|<span data-ttu-id="6a126-131">Makaleler, bir SQL Server örneği için veritabanları arası sahiplik zincirinin nasıl yapılandırılacağını açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="6a126-131">Articles describe how to configure cross-database ownership chaining for an instance of SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6a126-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a126-132">See also</span></span>

- [<span data-ttu-id="6a126-133">ADO.NET Uygulamalarının Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="6a126-133">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="6a126-134">SQL Server Güvenliğine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6a126-134">Overview of SQL Server Security</span></span>](overview-of-sql-server-security.md)
- [<span data-ttu-id="6a126-135">SQL Server'da Saklı Yordam İzinlerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="6a126-135">Managing Permissions with Stored Procedures in SQL Server</span></span>](managing-permissions-with-stored-procedures-in-sql-server.md)
- [<span data-ttu-id="6a126-136">SQL Server’da Secure Dynamic SQL Yazma</span><span class="sxs-lookup"><span data-stu-id="6a126-136">Writing Secure Dynamic SQL in SQL Server</span></span>](writing-secure-dynamic-sql-in-sql-server.md)
- [<span data-ttu-id="6a126-137">SQL Server'da Saklı Yordam İmzalama</span><span class="sxs-lookup"><span data-stu-id="6a126-137">Signing Stored Procedures in SQL Server</span></span>](signing-stored-procedures-in-sql-server.md)
- [<span data-ttu-id="6a126-138">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6a126-138">ADO.NET Overview</span></span>](../ado-net-overview.md)
