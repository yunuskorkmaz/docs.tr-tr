---
title: SQL Server'da Sahiplik ve Kullanıcı Şeması Ayrımı
description: Kullanıcı şeması ayrımı SQL Server veritabanı nesne izinlerini yönetirken esnekliğe nasıl izin verdiğini öğrenin. Şemalar nesneleri ayrı ad alanlarına gruplar.
ms.date: 03/30/2017
ms.assetid: 242830c1-31b5-4427-828c-cc22ff339f30
ms.openlocfilehash: e92799237a90c502aa4000d8d4027df522aa0d87
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183149"
---
# <a name="ownership-and-user-schema-separation-in-sql-server"></a><span data-ttu-id="35dd4-104">SQL Server'da Sahiplik ve Kullanıcı Şeması Ayrımı</span><span class="sxs-lookup"><span data-stu-id="35dd4-104">Ownership and User-Schema Separation in SQL Server</span></span>

<span data-ttu-id="35dd4-105">SQL Server güvenliği temel bir kavramı, nesne sahiplerinin bunları yönetmek için geri alınamaz izinlere sahip olmalarından oluşur.</span><span class="sxs-lookup"><span data-stu-id="35dd4-105">A core concept of SQL Server security is that owners of objects have irrevocable permissions to administer them.</span></span> <span data-ttu-id="35dd4-106">Bir nesne sahibinden ayrıcalıkları kaldıramazsınız ve içindeki nesneler varsa kullanıcıları bir veritabanından bırakamazsınız.</span><span class="sxs-lookup"><span data-stu-id="35dd4-106">You cannot remove privileges from an object owner, and you cannot drop users from a database if they own objects in it.</span></span>  
  
## <a name="user-schema-separation"></a><span data-ttu-id="35dd4-107">Kullanıcı şeması ayrımı</span><span class="sxs-lookup"><span data-stu-id="35dd4-107">User-Schema Separation</span></span>  

 <span data-ttu-id="35dd4-108">Kullanıcı şeması ayrımı, veritabanı nesne izinlerinin yönetiminde daha fazla esneklik sağlar.</span><span class="sxs-lookup"><span data-stu-id="35dd4-108">User-schema separation allows for more flexibility in managing database object permissions.</span></span> <span data-ttu-id="35dd4-109">*Şema* , nesneleri ayrı ad alanlarına gruplandırmanıza olanak tanıyan veritabanı nesneleri için adlandırılmış bir kapsayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="35dd4-109">A *schema* is a named container for database objects, which allows you to group objects into separate namespaces.</span></span> <span data-ttu-id="35dd4-110">Örneğin, AdventureWorks örnek veritabanı üretim, satış ve ınsana kaynakları için şemalar içerir.</span><span class="sxs-lookup"><span data-stu-id="35dd4-110">For example, the AdventureWorks sample database contains schemas for Production, Sales, and HumanResources.</span></span>  
  
 <span data-ttu-id="35dd4-111">Nesnelere başvurmak için dört bölümden oluşan adlandırma sözdizimi, şema adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="35dd4-111">The four-part naming syntax for referring to objects specifies the schema name.</span></span>  
  
```text
Server.Database.DatabaseSchema.DatabaseObject  
```  
  
### <a name="schema-owners-and-permissions"></a><span data-ttu-id="35dd4-112">Şema sahipleri ve Izinleri</span><span class="sxs-lookup"><span data-stu-id="35dd4-112">Schema Owners and Permissions</span></span>  

 <span data-ttu-id="35dd4-113">Şemaların herhangi bir veritabanı sorumlusu olabilir ve tek bir sorumlu birden çok şemaya sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="35dd4-113">Schemas can be owned by any database principal, and a single principal can own multiple schemas.</span></span> <span data-ttu-id="35dd4-114">Şemadaki tüm nesneler tarafından devralınan bir şemaya güvenlik kuralları uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35dd4-114">You can apply security rules to a schema, which are inherited by all objects in the schema.</span></span> <span data-ttu-id="35dd4-115">Bir şema için erişim izinleri ayarladıktan sonra, şemaya yeni nesneler eklendikçe bu izinler otomatik olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="35dd4-115">Once you set up access permissions for a schema, those permissions are automatically applied as new objects are added to the schema.</span></span> <span data-ttu-id="35dd4-116">Kullanıcılara varsayılan bir şema atanabilir ve birden çok veritabanı kullanıcısı aynı şemayı paylaşabilir.</span><span class="sxs-lookup"><span data-stu-id="35dd4-116">Users can be assigned a default schema, and multiple database users can share the same schema.</span></span>  
  
 <span data-ttu-id="35dd4-117">Varsayılan olarak, geliştiriciler bir şemada nesne oluştururken nesneler, geliştiriciye değil, şemanın sahibi olan güvenlik sorumlusuna aittir.</span><span class="sxs-lookup"><span data-stu-id="35dd4-117">By default, when developers create objects in a schema, the objects are owned by the security principal that owns the schema, not the developer.</span></span> <span data-ttu-id="35dd4-118">Nesne sahipliği, ALTER AUTHORIZATION Transact-SQL ifadesiyle aktarılabilir.</span><span class="sxs-lookup"><span data-stu-id="35dd4-118">Object ownership can be transferred with ALTER AUTHORIZATION Transact-SQL statement.</span></span> <span data-ttu-id="35dd4-119">Şema, farklı kullanıcılara ait olan ve şemaya atananlardan daha ayrıntılı izinlere sahip olan nesneleri de içerebilir, ancak bu, izinleri yönetmek için karmaşıklık eklediğinden bu önerilmez.</span><span class="sxs-lookup"><span data-stu-id="35dd4-119">A schema can also contain objects that are owned by different users and have more granular permissions than those assigned to the schema, although this is not recommended because it adds complexity to managing permissions.</span></span> <span data-ttu-id="35dd4-120">Nesneler şemalar arasında taşınabilir ve şema sahipliği sorumlular arasında aktarılabilir.</span><span class="sxs-lookup"><span data-stu-id="35dd4-120">Objects can be moved between schemas, and schema ownership can be transferred between principals.</span></span> <span data-ttu-id="35dd4-121">Veritabanı kullanıcıları şemalar etkilenmeden bırakılamaz.</span><span class="sxs-lookup"><span data-stu-id="35dd4-121">Database users can be dropped without affecting schemas.</span></span>  
  
### <a name="built-in-schemas"></a><span data-ttu-id="35dd4-122">Yerleşik şemalar</span><span class="sxs-lookup"><span data-stu-id="35dd4-122">Built-In Schemas</span></span>  

 <span data-ttu-id="35dd4-123">SQL Server, yerleşik veritabanı kullanıcıları ve rolleriyle aynı adlara sahip olan on önceden tanımlanmış şemalar ile birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="35dd4-123">SQL Server ships with ten pre-defined schemas that have the same names as the built-in database users and roles.</span></span> <span data-ttu-id="35dd4-124">Bunlar genellikle geriye dönük uyumluluk için vardır.</span><span class="sxs-lookup"><span data-stu-id="35dd4-124">These exist mainly for backward compatibility.</span></span> <span data-ttu-id="35dd4-125">Aynı ada sahip olan şemaları, gerek duymadıysanız, sabit veritabanı rolleriyle bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35dd4-125">You can drop the schemas that have the same names as the fixed database roles if you do not need them.</span></span> <span data-ttu-id="35dd4-126">Aşağıdaki şemaları bırakamazsınız:</span><span class="sxs-lookup"><span data-stu-id="35dd4-126">You cannot drop the following schemas:</span></span>  
  
- `dbo`  
  
- `guest`  
  
- `sys`  
  
- `INFORMATION_SCHEMA`  
  
 <span data-ttu-id="35dd4-127">Bunları model veritabanından bırakırsanız, bu yeni veritabanlarında görünmez.</span><span class="sxs-lookup"><span data-stu-id="35dd4-127">If you drop them from the model database, they will not appear in new databases.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="35dd4-128">`sys`Ve `INFORMATION_SCHEMA` şemaları sistem nesneleri için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="35dd4-128">The `sys` and `INFORMATION_SCHEMA` schemas are reserved for system objects.</span></span> <span data-ttu-id="35dd4-129">Bu şemalarda nesne oluşturamazsınız ve bunları bırakamazsınız.</span><span class="sxs-lookup"><span data-stu-id="35dd4-129">You cannot create objects in these schemas and you cannot drop them.</span></span>  
  
#### <a name="the-dbo-schema"></a><span data-ttu-id="35dd4-130">Dbo şeması</span><span class="sxs-lookup"><span data-stu-id="35dd4-130">The dbo Schema</span></span>  

 <span data-ttu-id="35dd4-131">`dbo`Şema, yeni oluşturulan bir veritabanı için varsayılan şemadır.</span><span class="sxs-lookup"><span data-stu-id="35dd4-131">The `dbo` schema is the default schema for a newly created database.</span></span> <span data-ttu-id="35dd4-132">`dbo`Şemanın `dbo` Kullanıcı hesabına ait olması.</span><span class="sxs-lookup"><span data-stu-id="35dd4-132">The `dbo` schema is owned by the `dbo` user account.</span></span> <span data-ttu-id="35dd4-133">Varsayılan olarak, CREATE USER Transact-SQL komutuyla oluşturulan kullanıcılar `dbo` varsayılan şemasına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="35dd4-133">By default, users created with the CREATE USER Transact-SQL command have `dbo` as their default schema.</span></span>  
  
 <span data-ttu-id="35dd4-134">Şemaya atanan kullanıcılar, `dbo` `dbo` Kullanıcı hesabının izinlerini almıyor.</span><span class="sxs-lookup"><span data-stu-id="35dd4-134">Users who are assigned the `dbo` schema do not inherit the permissions of the `dbo` user account.</span></span> <span data-ttu-id="35dd4-135">Bir şemadan kullanıcılar tarafından devralınan izin yok; şema izinleri, şemada bulunan veritabanı nesneleri tarafından devralınır.</span><span class="sxs-lookup"><span data-stu-id="35dd4-135">No permissions are inherited from a schema by users; schema permissions are inherited by the database objects contained in the schema.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="35dd4-136">Veritabanı nesnelerine tek parçalı ad kullanılarak başvurulduğunda, SQL Server önce kullanıcının varsayılan şemasına bakar.</span><span class="sxs-lookup"><span data-stu-id="35dd4-136">When database objects are referenced by using a one-part name, SQL Server first looks in the user's default schema.</span></span> <span data-ttu-id="35dd4-137">Nesne bulunamazsa, şemada bir sonraki SQL Server görünür `dbo` .</span><span class="sxs-lookup"><span data-stu-id="35dd4-137">If the object is not found there, SQL Server looks next in the `dbo` schema.</span></span> <span data-ttu-id="35dd4-138">Nesne `dbo` şemada değilse bir hata döndürülür.</span><span class="sxs-lookup"><span data-stu-id="35dd4-138">If the object is not in the `dbo` schema, an error is returned.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="35dd4-139">Dış Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="35dd4-139">External Resources</span></span>  

 <span data-ttu-id="35dd4-140">Nesne sahipliği ve şemaları hakkında daha fazla bilgi için aşağıdaki kaynaklara bakın.</span><span class="sxs-lookup"><span data-stu-id="35dd4-140">For more information on object ownership and schemas, see the following resources.</span></span>  
  
|<span data-ttu-id="35dd4-141">Kaynak</span><span class="sxs-lookup"><span data-stu-id="35dd4-141">Resource</span></span>|<span data-ttu-id="35dd4-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="35dd4-142">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="35dd4-143">[Kullanıcı şeması ayrımı](/previous-versions/sql/sql-server-2008-r2/ms190387(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="35dd4-143">[User-Schema Separation](/previous-versions/sql/sql-server-2008-r2/ms190387(v=sql.105))</span></span>|<span data-ttu-id="35dd4-144">Kullanıcı şeması ayrımı tarafından tanıtılan değişiklikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="35dd4-144">Describes the changes introduced by user-schema separation.</span></span> <span data-ttu-id="35dd4-145">Yeni davranış, sahiplik üzerindeki etkisi, katalog görünümleri ve izinleri içerir.</span><span class="sxs-lookup"><span data-stu-id="35dd4-145">Includes new behavior, its impact on ownership, catalog views, and permissions.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="35dd4-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35dd4-146">See also</span></span>

- [<span data-ttu-id="35dd4-147">ADO.NET Uygulamalarının Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="35dd4-147">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="35dd4-148">SQL Server'da Uygulama Güvenliği Senaryoları</span><span class="sxs-lookup"><span data-stu-id="35dd4-148">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="35dd4-149">SQL Server’da Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="35dd4-149">Authentication in SQL Server</span></span>](authentication-in-sql-server.md)
- [<span data-ttu-id="35dd4-150">SQL Server’da Sunucu ve Veritabanı Rolleri</span><span class="sxs-lookup"><span data-stu-id="35dd4-150">Server and Database Roles in SQL Server</span></span>](server-and-database-roles-in-sql-server.md)
- [<span data-ttu-id="35dd4-151">SQL Server’da Yetkilendirme ve İzinler</span><span class="sxs-lookup"><span data-stu-id="35dd4-151">Authorization and Permissions in SQL Server</span></span>](authorization-and-permissions-in-sql-server.md)
- [<span data-ttu-id="35dd4-152">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="35dd4-152">ADO.NET Overview</span></span>](../ado-net-overview.md)
