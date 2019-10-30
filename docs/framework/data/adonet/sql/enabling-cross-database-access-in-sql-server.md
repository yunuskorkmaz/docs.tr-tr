---
title: SQL Server'da Veritabanları Arası Erişimi Etkinleştirme
ms.date: 03/30/2017
ms.assetid: 10663fb6-434c-4c81-8178-ec894b9cf895
ms.openlocfilehash: bf46d43f5ac9b0a385e9bc6da1546af1d67a282d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040239"
---
# <a name="enabling-cross-database-access-in-sql-server"></a><span data-ttu-id="b5dd9-102">SQL Server'da Veritabanları Arası Erişimi Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="b5dd9-102">Enabling Cross-Database Access in SQL Server</span></span>
<span data-ttu-id="b5dd9-103">Veritabanları arası sahiplik zinciri, bir veritabanındaki bir yordam başka bir veritabanındaki nesnelere bağımlıysa oluşur.</span><span class="sxs-lookup"><span data-stu-id="b5dd9-103">Cross-database ownership chaining occurs when a procedure in one database depends on objects in another database.</span></span> <span data-ttu-id="b5dd9-104">Veritabanları arası sahiplik zinciri, tek bir veritabanı içindeki sahiplik zinciriyle aynı şekilde çalışarak, bozuk bir sahiplik zinciri, tüm nesne sahiplerinin aynı oturum açma hesabıyla eşlenmesini gerektirmesidir.</span><span class="sxs-lookup"><span data-stu-id="b5dd9-104">A cross-database ownership chain works in the same way as ownership chaining within a single database, except that an unbroken ownership chain requires that all the object owners are mapped to the same login account.</span></span> <span data-ttu-id="b5dd9-105">Kaynak veritabanındaki kaynak nesne ve hedef veritabanlarındaki hedef nesneler aynı oturum açma hesabına aitse, SQL Server hedef nesnelerdeki izinleri denetlemez.</span><span class="sxs-lookup"><span data-stu-id="b5dd9-105">If the source object in the source database and the target objects in the target databases are owned by the same login account, SQL Server does not check permissions on the target objects.</span></span>  
  
## <a name="off-by-default"></a><span data-ttu-id="b5dd9-106">Varsayılan olarak kapalı</span><span class="sxs-lookup"><span data-stu-id="b5dd9-106">Off By Default</span></span>  
 <span data-ttu-id="b5dd9-107">Veritabanları arasında sahiplik zinciri varsayılan olarak kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="b5dd9-107">Ownership chaining across databases is turned off by default.</span></span> <span data-ttu-id="b5dd9-108">Microsoft, aşağıdaki güvenlik risklerini size gösterdiğinden, veritabanları arası sahiplik zincirlemeyi devre dışı bırakmanızı önerir:</span><span class="sxs-lookup"><span data-stu-id="b5dd9-108">Microsoft recommends that you disable cross-database ownership chaining because it exposes you to the following security risks:</span></span>  
  
- <span data-ttu-id="b5dd9-109">Veritabanı sahipleri ve `db_ddladmin` veya `db_owners` veritabanı rollerinin üyeleri, diğer kullanıcılara ait nesneleri oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="b5dd9-109">Database owners and members of the `db_ddladmin` or the `db_owners` database roles can create objects that are owned by other users.</span></span> <span data-ttu-id="b5dd9-110">Bu nesneler, diğer veritabanlarındaki nesneleri hedefleyebilir.</span><span class="sxs-lookup"><span data-stu-id="b5dd9-110">These objects can potentially target objects in other databases.</span></span> <span data-ttu-id="b5dd9-111">Bu, veritabanları arası sahiplik zincirlemeyi etkinleştirirseniz bu kullanıcılara tüm veritabanlarındaki verilerle tam olarak güvenmeniz gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b5dd9-111">This means that if you enable cross-database ownership chaining, you must fully trust these users with data in all databases.</span></span>  
  
- <span data-ttu-id="b5dd9-112">VERITABANı oluştur iznine sahip kullanıcılar yeni veritabanları oluşturabilir ve var olan veritabanlarını ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="b5dd9-112">Users with CREATE DATABASE permission can create new databases and attach existing databases.</span></span> <span data-ttu-id="b5dd9-113">Veritabanları arası sahiplik zinciri etkinse, bu kullanıcılar, oluşturdukları yeni oluşturulan veya eklenen veritabanlarından ayrıcalıklarına sahip olmadıkları diğer veritabanlarındaki nesnelere erişebilir.</span><span class="sxs-lookup"><span data-stu-id="b5dd9-113">If cross-database ownership chaining is enabled, these users can access objects in other databases that they might not have privileges in from the newly created or attached databases that they create.</span></span>  
  
## <a name="enabling-cross-database-ownership-chaining"></a><span data-ttu-id="b5dd9-114">Veritabanları arası sahiplik zincirlemeyi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="b5dd9-114">Enabling Cross-database Ownership Chaining</span></span>  
 <span data-ttu-id="b5dd9-115">Veritabanları arası sahiplik zinciri yalnızca yüksek ayrıcalıklı kullanıcılara tam güvenebileceğiniz ortamlarda etkinleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="b5dd9-115">Cross-database ownership chaining should only be enabled in environments where you can fully trust highly-privileged users.</span></span> <span data-ttu-id="b5dd9-116">Tüm veritabanları için kurulum sırasında ya da Transact-SQL komutları `sp_configure` ve `ALTER DATABASE`kullanılarak belirli veritabanlarına seçmeli olarak yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="b5dd9-116">It can be configured during setup for all databases, or selectively for specific databases using the Transact-SQL commands `sp_configure` and `ALTER DATABASE`.</span></span>  
  
 <span data-ttu-id="b5dd9-117">Veritabanları arası sahiplik zincirlemeyi seçmeli olarak yapılandırmak için `sp_configure` kullanarak sunucu için devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="b5dd9-117">To selectively configure cross-database ownership chaining, use `sp_configure` to turn it off for the server.</span></span> <span data-ttu-id="b5dd9-118">Ardından, tek yapmanız gereken veritabanları için veritabanları arası sahiplik zincirlemesini yapılandırmak üzere SET DB_CHAINING ON ile ALTER DATABASE komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="b5dd9-118">Then use the ALTER DATABASE command with SET DB_CHAINING ON to configure cross-database ownership chaining for only the databases that require it.</span></span>  
  
 <span data-ttu-id="b5dd9-119">Aşağıdaki örnek, tüm veritabanları için çapraz veritabanı sahiplik zincirlemesini etkinleştirir:</span><span class="sxs-lookup"><span data-stu-id="b5dd9-119">The following sample turns on cross-database ownership chaining for all databases:</span></span>  
  
```sql
EXECUTE sp_configure 'show advanced', 1;  
RECONFIGURE;  
EXECUTE sp_configure 'cross db ownership chaining', 1;  
RECONFIGURE;  
```  
  
 <span data-ttu-id="b5dd9-120">Aşağıdaki örnek, belirli veritabanları için veritabanları arası sahiplik zincirlemeyi etkinleştirir:</span><span class="sxs-lookup"><span data-stu-id="b5dd9-120">The following sample turns on cross-database ownership chaining for specific databases:</span></span>  
  
```sql
ALTER DATABASE Database1 SET DB_CHAINING ON;  
ALTER DATABASE Database2 SET DB_CHAINING ON;  
```  
  
### <a name="dynamic-sql"></a><span data-ttu-id="b5dd9-121">Dinamik SQL</span><span class="sxs-lookup"><span data-stu-id="b5dd9-121">Dynamic SQL</span></span>  
 <span data-ttu-id="b5dd9-122">Veritabanları arası sahiplik zinciri, aynı kullanıcı her iki veritabanında da mevcut olmadığı takdirde dinamik olarak oluşturulan SQL deyimlerinin yürütüldüğü durumlarda çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="b5dd9-122">Cross-database ownership chaining does not work in cases where dynamically created SQL statements are executed unless the same user exists in both databases.</span></span> <span data-ttu-id="b5dd9-123">Başka bir veritabanındaki verilere erişen ve yordamı her iki veritabanında bulunan bir sertifikayla imzalayan bir saklı yordam oluşturarak bu SQL Server geçici bir çözüm bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5dd9-123">You can work around this in SQL Server by creating a stored procedure that accesses data in another database and signing the procedure with a certificate that exists in both databases.</span></span> <span data-ttu-id="b5dd9-124">Bu, kullanıcılara veritabanı erişimi veya izinleri vermeden yordam tarafından kullanılan veritabanı kaynaklarına erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="b5dd9-124">This gives users access to the database resources used by the procedure without granting them database access or permissions.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="b5dd9-125">Dış Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="b5dd9-125">External Resources</span></span>  
 <span data-ttu-id="b5dd9-126">Daha fazla bilgi için aşağıdaki kaynaklara bakın.</span><span class="sxs-lookup"><span data-stu-id="b5dd9-126">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="b5dd9-127">Kaynak</span><span class="sxs-lookup"><span data-stu-id="b5dd9-127">Resource</span></span>|<span data-ttu-id="b5dd9-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b5dd9-128">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="b5dd9-129">FARKLı ÇALıŞTıR ve [çapraz veritabanı sahiplik zinciri seçeneğini](/sql/database-engine/configure-windows/cross-db-ownership-chaining-server-configuration-option) [kullanarak veritabanı kimliğe bürünme özelliğini genişletme](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms188304(v=sql.105)) .</span><span class="sxs-lookup"><span data-stu-id="b5dd9-129">[Extending Database Impersonation by Using EXECUTE AS](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms188304(v=sql.105)) and [Cross DB Ownership Chaining Option](/sql/database-engine/configure-windows/cross-db-ownership-chaining-server-configuration-option).</span></span>|<span data-ttu-id="b5dd9-130">Makaleler, bir SQL Server örneği için veritabanları arası sahiplik zincirinin nasıl yapılandırılacağını açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="b5dd9-130">Articles describe how to configure cross-database ownership chaining for an instance of SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b5dd9-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5dd9-131">See also</span></span>

- [<span data-ttu-id="b5dd9-132">ADO.NET Uygulamalarının Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="b5dd9-132">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="b5dd9-133">SQL Server Güvenliğine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b5dd9-133">Overview of SQL Server Security</span></span>](overview-of-sql-server-security.md)
- [<span data-ttu-id="b5dd9-134">SQL Server'da Saklı Yordam İzinlerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="b5dd9-134">Managing Permissions with Stored Procedures in SQL Server</span></span>](managing-permissions-with-stored-procedures-in-sql-server.md)
- [<span data-ttu-id="b5dd9-135">SQL Server’da Secure Dynamic SQL Yazma</span><span class="sxs-lookup"><span data-stu-id="b5dd9-135">Writing Secure Dynamic SQL in SQL Server</span></span>](writing-secure-dynamic-sql-in-sql-server.md)
- [<span data-ttu-id="b5dd9-136">SQL Server'da Saklı Yordam İmzalama</span><span class="sxs-lookup"><span data-stu-id="b5dd9-136">Signing Stored Procedures in SQL Server</span></span>](signing-stored-procedures-in-sql-server.md)
- [<span data-ttu-id="b5dd9-137">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b5dd9-137">ADO.NET Overview</span></span>](../ado-net-overview.md)
