---
title: "SQL Server'da veritabanları arası erişimini etkinleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10663fb6-434c-4c81-8178-ec894b9cf895
caps.latest.revision: "10"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 2a31bddfec44ad4b33f1b595c2746d1a0e841b82
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="enabling-cross-database-access-in-sql-server"></a><span data-ttu-id="9c59f-102">SQL Server'da veritabanları arası erişimini etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="9c59f-102">Enabling Cross-Database Access in SQL Server</span></span>
<span data-ttu-id="9c59f-103">Veritabanları arası sahiplik zincirleme nesneleri başka bir veritabanındaki bir veritabanı yordamda bağlı olduğunda oluşur.</span><span class="sxs-lookup"><span data-stu-id="9c59f-103">Cross-database ownership chaining occurs when a procedure in one database depends on objects in another database.</span></span> <span data-ttu-id="9c59f-104">Tüm nesne sahiplerini aynı oturum açma hesabıyla eşlenir kırık sahiplik zinciri gerektirir veritabanları arası sahiplik zinciri içinde tek bir veritabanı, sahipliği zincirleme olarak aynı şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="9c59f-104">A cross-database ownership chain works in the same way as ownership chaining within a single database, except that an unbroken ownership chain requires that all the object owners are mapped to the same login account.</span></span> <span data-ttu-id="9c59f-105">Kaynak veritabanındaki kaynak nesnesi ve hedef veritabanlarına hedef nesneleri aynı oturum açma hesabı tarafından sahip olunan, SQL Server hedef nesneler üzerindeki izinleri denetlemez.</span><span class="sxs-lookup"><span data-stu-id="9c59f-105">If the source object in the source database and the target objects in the target databases are owned by the same login account, SQL Server does not check permissions on the target objects.</span></span>  
  
## <a name="off-by-default"></a><span data-ttu-id="9c59f-106">Varsayılan olarak kapalıdır</span><span class="sxs-lookup"><span data-stu-id="9c59f-106">Off By Default</span></span>  
 <span data-ttu-id="9c59f-107">Veritabanları arasında sahipliği zincirleme varsayılan olarak kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="9c59f-107">Ownership chaining across databases is turned off by default.</span></span> <span data-ttu-id="9c59f-108">Microsoft, aşağıdaki güvenlik risklerini kullanıma sunan çünkü veritabanları arası sahiplik zincirleme devre dışı bırakmak önerir:</span><span class="sxs-lookup"><span data-stu-id="9c59f-108">Microsoft recommends that you disable cross-database ownership chaining because it exposes you to the following security risks:</span></span>  
  
-   <span data-ttu-id="9c59f-109">Veritabanı sahipleri ve üyeleri `db_ddladmin` veya `db_owners` veritabanı rolleri, diğer kullanıcılar tarafından sahip olunan nesneler oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="9c59f-109">Database owners and members of the `db_ddladmin` or the `db_owners` database roles can create objects that are owned by other users.</span></span> <span data-ttu-id="9c59f-110">Bu nesneler, büyük olasılıkla diğer veritabanlarındaki nesneler hedefleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c59f-110">These objects can potentially target objects in other databases.</span></span> <span data-ttu-id="9c59f-111">Bu veritabanları arası sahiplik zincirleme etkinleştirirseniz, bu kullanıcılar tüm veritabanlarındaki veriler ile tam olarak güvenmelidir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="9c59f-111">This means that if you enable cross-database ownership chaining, you must fully trust these users with data in all databases.</span></span>  
  
-   <span data-ttu-id="9c59f-112">CREATE DATABASE iznine sahip kullanıcılar, yeni veritabanları oluşturabilir ve varolan veritabanları ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c59f-112">Users with CREATE DATABASE permission can create new databases and attach existing databases.</span></span> <span data-ttu-id="9c59f-113">Veritabanları arası sahiplik zincirleme etkinse, bu kullanıcılar oluşturdukları yeni oluşturulan veya ekli veritabanlarından bunlar ayrıcalıklara sahip olmayabilir diğer veritabanlarındaki nesnelere erişebilir.</span><span class="sxs-lookup"><span data-stu-id="9c59f-113">If cross-database ownership chaining is enabled, these users can access objects in other databases that they might not have privileges in from the newly created or attached databases that they create.</span></span>  
  
## <a name="enabling-cross-database-ownership-chaining"></a><span data-ttu-id="9c59f-114">Veritabanları arası sahiplik zincirleme etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="9c59f-114">Enabling Cross-database Ownership Chaining</span></span>  
 <span data-ttu-id="9c59f-115">Veritabanları arası sahiplik zincirleme yüksek ayrıcalıklı kullanıcıların tam olarak güvenebildiğiniz ortamlarda yalnızca etkinleştirilmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9c59f-115">Cross-database ownership chaining should only be enabled in environments where you can fully trust highly-privileged users.</span></span> <span data-ttu-id="9c59f-116">Tüm veritabanları için veya seçmeli olarak kullanarak belirli veritabanları için Kurulum sırasında yapılandırılabilir [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] komutları `sp_configure` ve `ALTER DATABASE`.</span><span class="sxs-lookup"><span data-stu-id="9c59f-116">It can be configured during setup for all databases, or selectively for specific databases using the [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] commands `sp_configure` and `ALTER DATABASE`.</span></span>  
  
 <span data-ttu-id="9c59f-117">Veritabanları arası sahiplik zincirleme seçmeli olarak yapılandırmak için kullanın `sp_configure` sunucu için devre dışı bırakma.</span><span class="sxs-lookup"><span data-stu-id="9c59f-117">To selectively configure cross-database ownership chaining, use `sp_configure` to turn it off for the server.</span></span> <span data-ttu-id="9c59f-118">Ardından yalnızca gerektiren veritabanları için zincirleme veritabanları arası sahiplik yapılandırmak için SET DB_CHAINING ON ile ALTER DATABASE komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="9c59f-118">Then use the ALTER DATABASE command with SET DB_CHAINING ON to configure cross-database ownership chaining for only the databases that require it.</span></span>  
  
 <span data-ttu-id="9c59f-119">Aşağıdaki örnek veritabanları arası sahiplik tüm veritabanları için zincirleme açar:</span><span class="sxs-lookup"><span data-stu-id="9c59f-119">The following sample turns on cross-database ownership chaining for all databases:</span></span>  
  
```  
EXECUTE sp_configure 'show advanced', 1;  
RECONFIGURE;  
EXECUTE sp_configure 'cross db ownership chaining', 1;  
RECONFIGURE;  
```  
  
 <span data-ttu-id="9c59f-120">Aşağıdaki örnek veritabanları arası sahiplik belirli veritabanları için zincirleme açar:</span><span class="sxs-lookup"><span data-stu-id="9c59f-120">The following sample turns on cross-database ownership chaining for specific databases:</span></span>  
  
```  
ALTER DATABASE Database1 SET DB_CHAINING ON;  
ALTER DATABASE Database2 SET DB_CHAINING ON;  
```  
  
### <a name="dynamic-sql"></a><span data-ttu-id="9c59f-121">Dinamik SQL</span><span class="sxs-lookup"><span data-stu-id="9c59f-121">Dynamic SQL</span></span>  
 <span data-ttu-id="9c59f-122">Veritabanları arası sahiplik zincirleme, aynı kullanıcı her iki veritabanı olmadığı sürece dinamik olarak oluşturulan SQL deyimlerini yürütüldüğü durumlarda çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="9c59f-122">Cross-database ownership chaining does not work in cases where dynamically created SQL statements are executed unless the same user exists in both databases.</span></span> <span data-ttu-id="9c59f-123">Bu geçici çözüm [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] başka bir veritabanındaki verilere erişen bir saklı yordam oluşturarak ve yordam her iki veritabanlarınızda var olan bir sertifika ile imzalama.</span><span class="sxs-lookup"><span data-stu-id="9c59f-123">You can work around this in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] by creating a stored procedure that accesses data in another database and signing the procedure with a certificate that exists in both databases.</span></span> <span data-ttu-id="9c59f-124">Bu kullanıcılar veritabanı erişimi ya da izin vermeden yordamı tarafından kullanılan veritabanı kaynaklarına erişmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="9c59f-124">This gives users access to the database resources used by the procedure without granting them database access or permissions.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="9c59f-125">Dış Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="9c59f-125">External Resources</span></span>  
 <span data-ttu-id="9c59f-126">Daha fazla bilgi için aşağıdaki kaynaklara bakın.</span><span class="sxs-lookup"><span data-stu-id="9c59f-126">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="9c59f-127">Kaynak</span><span class="sxs-lookup"><span data-stu-id="9c59f-127">Resource</span></span>|<span data-ttu-id="9c59f-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9c59f-128">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="9c59f-129">[EXECUTE AS kullanarak veritabanı kimliğe bürünme genişletme](http://msdn.microsoft.com/library/ms188304\(SQL.105\).aspx) ve [arası seçeneği zincirleme DB sahipliği](http://msdn.microsoft.com/library/ms188694.aspx) [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Çevrimiçi Kitapları.</span><span class="sxs-lookup"><span data-stu-id="9c59f-129">[Extending Database Impersonation by Using EXECUTE AS](http://msdn.microsoft.com/library/ms188304\(SQL.105\).aspx) and [Cross DB Ownership Chaining Option](http://msdn.microsoft.com/library/ms188694.aspx)[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online.</span></span>|<span data-ttu-id="9c59f-130">Konular açıklayan bir örneği için veritabanları arası sahiplik zincirleme yapılandırma [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9c59f-130">Topics describe how to configure cross-database ownership chaining for an instance of [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9c59f-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9c59f-131">See Also</span></span>  
 [<span data-ttu-id="9c59f-132">ADO.NET Uygulamalarının Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="9c59f-132">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="9c59f-133">SQL Server Güvenliğine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9c59f-133">Overview of SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [<span data-ttu-id="9c59f-134">SQL Server'da Saklı Yordam İzinlerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="9c59f-134">Managing Permissions with Stored Procedures in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 [<span data-ttu-id="9c59f-135">SQL Server’da Secure Dynamic SQL Yazma</span><span class="sxs-lookup"><span data-stu-id="9c59f-135">Writing Secure Dynamic SQL in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 [<span data-ttu-id="9c59f-136">SQL Server'da Saklı Yordam İmzalama</span><span class="sxs-lookup"><span data-stu-id="9c59f-136">Signing Stored Procedures in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)  
 [<span data-ttu-id="9c59f-137">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="9c59f-137">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
