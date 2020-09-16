---
title: SQL Server’da Satır Düzeyinde İzinler Verme
ms.date: 03/30/2017
ms.assetid: a55aaa12-34ab-41cd-9dec-fd255b29258c
ms.openlocfilehash: 0b34eaee4b66a2be82049816f0a98b9f53012303
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554859"
---
# <a name="granting-row-level-permissions-in-sql-server"></a><span data-ttu-id="bc3a2-102">SQL Server’da Satır Düzeyinde İzinler Verme</span><span class="sxs-lookup"><span data-stu-id="bc3a2-102">Granting Row-Level Permissions in SQL Server</span></span>

<span data-ttu-id="bc3a2-103">Bazı senaryolarda verilere erişimi daha ayrıntılı bir düzeyde denetlemek, izinlerin sağlanması, iptal edilmesinin veya reddetmesinin sağladığı bir gereksinimdir.</span><span class="sxs-lookup"><span data-stu-id="bc3a2-103">In some scenarios, there is a requirement to control access to data at a more granular level than what simply granting, revoking, or denying permissions provides.</span></span> <span data-ttu-id="bc3a2-104">Örneğin, bir barındırma veritabanı uygulaması, tek tek her bir Doctors 'ın yalnızca kendi hastalarıyla ilgili bilgilere erişmesine izin verebilir.</span><span class="sxs-lookup"><span data-stu-id="bc3a2-104">For example, a hospital database application may require individual Doctors to be restricted to accessing information related to only their patients.</span></span> <span data-ttu-id="bc3a2-105">Finans, hukuk, devlet ve askeri uygulamalar dahil olmak üzere birçok ortamda benzer gereksinimler mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="bc3a2-105">Similar requirements exist in many environments, including finance, law, government, and military applications.</span></span> <span data-ttu-id="bc3a2-106">SQL Server 2016, bu senaryolara yardımcı olmak için, bir güvenlik ilkesinde satır düzeyi erişim mantığını basitleştiren ve merkezileştiren bir [satır düzeyi güvenlik](/sql/relational-databases/security/row-level-security) özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc3a2-106">To help address these scenarios, SQL Server 2016 provides a [Row-Level Security](/sql/relational-databases/security/row-level-security) feature that simplifies and centralizes row-level access logic in a security policy.</span></span> <span data-ttu-id="bc3a2-107">Daha önceki SQL Server sürümleri için, satır düzeyinde filtrelemeyi uygulamak üzere görünümler kullanılarak benzer işlevler elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="bc3a2-107">For earlier versions of SQL Server, similar functionality can be achieved by using views to enact row-level filtering.</span></span>

## <a name="implementing-row-level-filtering"></a><span data-ttu-id="bc3a2-108">Satır düzeyinde filtreleme uygulama</span><span class="sxs-lookup"><span data-stu-id="bc3a2-108">Implementing Row-level Filtering</span></span>

<span data-ttu-id="bc3a2-109">Satır düzeyinde filtreleme, yukarıdaki barındırma örneğinde olduğu gibi tek bir tabloda bilgi depolayan uygulamalar için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bc3a2-109">Row-level filtering is used for applications storing information in a single table like in the hospital example above.</span></span> <span data-ttu-id="bc3a2-110">Satır düzeyinde filtreleme uygulamak için her satırda bir Kullanıcı adı, etiket veya başka bir tanımlayıcı gibi bir ayrım parametresi tanımlayan bir sütun bulunur.</span><span class="sxs-lookup"><span data-stu-id="bc3a2-110">To implement row-level filtering each row has a column that defines a differentiating parameter, such as a user name, label or other identifier.</span></span> <span data-ttu-id="bc3a2-111">Bir güvenlik ilkesi veya tabloda, kullanıcının erişebileceği satırları filtreleyen bir görünüm oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="bc3a2-111">You create either a security policy or a view on the table, which filters the rows that the user can access.</span></span> <span data-ttu-id="bc3a2-112">Ardından, kullanıcının yürütebileceği sorgu türlerini denetleyen parametreli saklı yordamlar oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="bc3a2-112">You then create parameterized stored procedures, which control the types of queries the user can execute.</span></span>

<span data-ttu-id="bc3a2-113">Aşağıdaki örnek, bir kullanıcı veya oturum açma adına göre satır düzeyinde filtrelemenin nasıl yapılandırılacağını açıklar:</span><span class="sxs-lookup"><span data-stu-id="bc3a2-113">The following example describes how to configure row-level filtering based on a user or login name:</span></span>

- <span data-ttu-id="bc3a2-114">Adı depolamak için bir sütun ekleyerek tablo oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bc3a2-114">Create the table, adding a column to store the name.</span></span>

- <span data-ttu-id="bc3a2-115">Satır düzeyinde filtrelemeyi etkinleştir:</span><span class="sxs-lookup"><span data-stu-id="bc3a2-115">Enable row-level filtering:</span></span>

  - <span data-ttu-id="bc3a2-116">SQL Server 2016 veya üzeri ya da [Azure SQL veritabanı](/azure/sql-database/)kullanıyorsanız, geçerli veritabanı kullanıcısı ile eşleşen satırları kısıtlayan bir güvenlik ilkesi oluşturun (CURRENT_USER () yerleşik işlevini kullanarak) ya da geçerli oturum açma adını (suser_sname () yerleşik işlevini kullanarak).</span><span class="sxs-lookup"><span data-stu-id="bc3a2-116">If you are using SQL Server 2016 or higher, or [Azure SQL Database](/azure/sql-database/), create a security policy that adds a predicate on the table restricting the rows returned to those that match either the current database user (using the CURRENT_USER() built-in function) or the current login name (using the SUSER_SNAME() built-in function):</span></span>

      ```sql
      CREATE SCHEMA Security
      GO

      CREATE FUNCTION Security.userAccessPredicate(@UserName sysname)
          RETURNS TABLE
          WITH SCHEMABINDING
      AS
          RETURN SELECT 1 AS accessResult
          WHERE @UserName = SUSER_SNAME()
      GO

      CREATE SECURITY POLICY Security.userAccessPolicy
          ADD FILTER PREDICATE Security.userAccessPredicate(UserName) ON dbo.MyTable,
          ADD BLOCK PREDICATE Security.userAccessPredicate(UserName) ON dbo.MyTable
      GO
      ```

  - <span data-ttu-id="bc3a2-117">2016 ' den önceki bir SQL Server sürümünü kullanıyorsanız, bir görünümü kullanarak benzer işlevlere ulaşabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bc3a2-117">If you are using a version of SQL Server prior to 2016, you can achieve similar functionality using a view:</span></span>

      ```sql
      CREATE VIEW vw_MyTable
      AS
          RETURN SELECT * FROM MyTable
          WHERE UserName = SUSER_SNAME()
      GO
      ```

- <span data-ttu-id="bc3a2-118">Verileri seçmek, eklemek, güncelleştirmek ve silmek için saklı yordamlar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bc3a2-118">Create stored procedures to select, insert, update, and delete data.</span></span> <span data-ttu-id="bc3a2-119">Filtreleme bir güvenlik ilkesiyle çalışıyorsa, saklı yordamlar bu işlemleri doğrudan temel tabloda gerçekleştirmelidir; Aksi takdirde, filtreleme bir görünüm tarafından işlem halinde kullanılıyorsa, saklı yordamlar bu görünümde bunun yerine çalışır.</span><span class="sxs-lookup"><span data-stu-id="bc3a2-119">If the filtering is enacted by a security policy, the stored procedures should perform these operations on the base table directly; otherwise, if the filtering is enacted by a view, the stored procedures should instead operate against the view.</span></span> <span data-ttu-id="bc3a2-120">Güvenlik ilkesi veya görünümü, Kullanıcı sorguları tarafından döndürülen veya değiştirilen satırları otomatik olarak filtreleyecek ve saklı yordam, kullanıcıların, filtrelenmiş verilerin varlığını çıkarmayan sorguları başarıyla çalıştırmasından doğrudan sorgu erişimi yapılmasını engellemek için daha zor bir güvenlik sınırı sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc3a2-120">The security policy or view will automatically filter the rows returned or modified by user queries, and the stored procedure will provide a harder security boundary to prevent users with direct query access from successfully running queries that can infer the existence of filtered data.</span></span>

- <span data-ttu-id="bc3a2-121">Veri ekleyen saklı yordamlar için, güvenlik ilkesinde veya görünümünde belirtilen işlevi kullanarak Kullanıcı adını yakalayın ve bu değeri Kullanıcı adı sütununa ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bc3a2-121">For stored procedures that insert data, capture the user name using the same function specified in the security policy or view, and insert that value into the UserName column.</span></span>

- <span data-ttu-id="bc3a2-122">Roldeki tablolardaki (ve varsa görünümler) tüm izinleri reddedin `public` .</span><span class="sxs-lookup"><span data-stu-id="bc3a2-122">Deny all permissions on the tables (and views, if applicable) to the `public` role.</span></span> <span data-ttu-id="bc3a2-123">Filtre koşulu, rollere değil Kullanıcı veya oturum açma adlarını temel aldığı için kullanıcılar diğer veritabanı rollerinden izinleri devralmasını mümkün olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="bc3a2-123">Users will not be able to inherit permissions from other database roles, because the filter predicate is based on user or login names, not on roles.</span></span>

- <span data-ttu-id="bc3a2-124">Saklı yordamlarda veritabanı rollerine yürütme izni verin.</span><span class="sxs-lookup"><span data-stu-id="bc3a2-124">Grant EXECUTE on the stored procedures to database roles.</span></span> <span data-ttu-id="bc3a2-125">Kullanıcılar verilere yalnızca belirtilen saklı yordamlar aracılığıyla erişebilir.</span><span class="sxs-lookup"><span data-stu-id="bc3a2-125">Users can only access data through the stored procedures provided.</span></span>

## <a name="see-also"></a><span data-ttu-id="bc3a2-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc3a2-126">See also</span></span>

- [<span data-ttu-id="bc3a2-127">Satır düzeyi güvenlik</span><span class="sxs-lookup"><span data-stu-id="bc3a2-127">Row-Level Security</span></span>](/sql/relational-databases/security/row-level-security)
- [<span data-ttu-id="bc3a2-128">ADO.NET Uygulamalarının Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="bc3a2-128">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="bc3a2-129">SQL Server Güvenliğine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bc3a2-129">Overview of SQL Server Security</span></span>](overview-of-sql-server-security.md)
- [<span data-ttu-id="bc3a2-130">SQL Server'da Uygulama Güvenliği Senaryoları</span><span class="sxs-lookup"><span data-stu-id="bc3a2-130">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="bc3a2-131">SQL Server'da Saklı Yordam İzinlerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="bc3a2-131">Managing Permissions with Stored Procedures in SQL Server</span></span>](managing-permissions-with-stored-procedures-in-sql-server.md)
- [<span data-ttu-id="bc3a2-132">SQL Server’da Secure Dynamic SQL Yazma</span><span class="sxs-lookup"><span data-stu-id="bc3a2-132">Writing Secure Dynamic SQL in SQL Server</span></span>](writing-secure-dynamic-sql-in-sql-server.md)
- [<span data-ttu-id="bc3a2-133">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bc3a2-133">ADO.NET Overview</span></span>](../ado-net-overview.md)
