---
title: "SQL Server güvenlik genel bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae66dd75-5c16-4cc0-9e12-774dd26d3fb9
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d93d077153cd15534175c1e60e63a765ce893c71
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="overview-of-sql-server-security"></a><span data-ttu-id="f5a53-102">SQL Server güvenlik genel bakış</span><span class="sxs-lookup"><span data-stu-id="f5a53-102">Overview of SQL Server Security</span></span>
<span data-ttu-id="f5a53-103">Güvenlik, katmanları çakışan bir savunma stratejisi, sayaç güvenlik tehditleri için en iyi yoludur.</span><span class="sxs-lookup"><span data-stu-id="f5a53-103">A defense-in-depth strategy, with overlapping layers of security, is the best way to counter security threats.</span></span> <span data-ttu-id="f5a53-104">SQL Server veritabanı Yöneticiler ve geliştiriciler güvenli veritabanı uygulamaları ve sayaç tehditlere oluşturmak izin vermek için tasarlanmış bir güvenlik mimarisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5a53-104">SQL Server provides a security architecture that is designed to allow database administrators and developers to create secure database applications and counter threats.</span></span> <span data-ttu-id="f5a53-105">Her SQL Server sürümü, SQL Server'ın önceki sürümlerinde kullanıma sunulması, yeni özellikler ve işlevsellik ile geliştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f5a53-105">Each version of SQL Server has improved on previous versions of SQL Server with the introduction of new features and functionality.</span></span> <span data-ttu-id="f5a53-106">Ancak, güvenlik kutusuna gelmez.</span><span class="sxs-lookup"><span data-stu-id="f5a53-106">However, security does not ship in the box.</span></span> <span data-ttu-id="f5a53-107">Her uygulama, güvenlik gereksinimleri açısından benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="f5a53-107">Each application is unique in its security requirements.</span></span> <span data-ttu-id="f5a53-108">Geliştiriciler hangi özellik bileşimi anlamak gerekir ve işlevselliği için en uygun sayaç bilinen tehditlere ve gelecekte kaynaklanabilecek tehditleri tahmin etmenize.</span><span class="sxs-lookup"><span data-stu-id="f5a53-108">Developers need to understand which combination of features and functionality are most appropriate to counter known threats, and to anticipate threats that may arise in the future.</span></span>  
  
 <span data-ttu-id="f5a53-109">Bir SQL Server örneği sunucuyla başlama varlıklar, hiyerarşik bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="f5a53-109">A SQL Server instance contains a hierarchical collection of entities, starting with the server.</span></span> <span data-ttu-id="f5a53-110">Birden çok veritabanı her sunucuyu içerir ve her veritabanı güvenliği sağlanabilir nesneler koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="f5a53-110">Each server contains multiple databases, and each database contains a collection of securable objects.</span></span> <span data-ttu-id="f5a53-111">Güvenli kılınabilir her SQL Server ilişkili *izinleri* , olanağı verilir bir *asıl*, bir kişi, Grup olduğu veya SQL Server'a erişim verilen işlem.</span><span class="sxs-lookup"><span data-stu-id="f5a53-111">Every SQL Server securable has associated *permissions* that can be granted to a *principal*, which is an individual, group or process granted access to SQL Server.</span></span> <span data-ttu-id="f5a53-112">SQL Server güvenlik çerçevesi güvenliği sağlanabilir varlıklara erişimi yöneten *kimlik doğrulaması* ve *yetkilendirme*.</span><span class="sxs-lookup"><span data-stu-id="f5a53-112">The SQL Server security framework manages access to securable entities through *authentication* and *authorization*.</span></span>  
  
-   <span data-ttu-id="f5a53-113">Kimlik doğrulaması olarak bir asıl sunucusu değerlendirir kimlik bilgileri göndererek erişim isteğinde SQL Server'da oturum açmayı işlemidir.</span><span class="sxs-lookup"><span data-stu-id="f5a53-113">Authentication is the process of logging on to SQL Server by which a principal requests access by submitting credentials that the server evaluates.</span></span> <span data-ttu-id="f5a53-114">Kimlik doğrulaması kullanıcı veya kimlik doğrulaması gerçekleştirilen işlem kimliği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f5a53-114">Authentication establishes the identity of the user or process being authenticated.</span></span>  
  
-   <span data-ttu-id="f5a53-115">Yetkilendirme sorumlu erişmek için hangi güvenliği sağlanabilir kaynakları ve işlemleri kaynaklarla için izin verilen belirleme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="f5a53-115">Authorization is the process of determining which securable resources a principal can access, and which operations are allowed for those resources.</span></span>  
  
 <span data-ttu-id="f5a53-116">Bu bölümdeki konular, SQL Server, SQL Server Books Online'nın ilgili sürümünde kapsamlı belgeler bağlantılar sağlayan güvenlik temelleri kapsar.</span><span class="sxs-lookup"><span data-stu-id="f5a53-116">The topics in this section cover SQL Server security fundamentals, providing links to the complete documentation in the relevant version of SQL Server Books Online.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f5a53-117">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="f5a53-117">In This Section</span></span>  
 [<span data-ttu-id="f5a53-118">SQL Server kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="f5a53-118">Authentication in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 <span data-ttu-id="f5a53-119">Oturum açma bilgileri ve SQL Server kimlik doğrulaması açıklanmakta ve ek kaynaklara bağlantılar sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f5a53-119">Describes logins and authentication in SQL Server and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="f5a53-120">Sunucusu ve SQL Server veritabanı rolleri</span><span class="sxs-lookup"><span data-stu-id="f5a53-120">Server and Database Roles in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)  
 <span data-ttu-id="f5a53-121">Sabit sunucu ve veritabanı rolleri, özel veritabanı rolleri ve yerleşik hesapları açıklanmakta ve ek kaynaklara bağlantılar sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f5a53-121">Describes fixed server and database roles, custom database roles, and built-in accounts and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="f5a53-122">Sahipliği ve SQL Server'daki kullanıcı şema ayırma</span><span class="sxs-lookup"><span data-stu-id="f5a53-122">Ownership and User-Schema Separation in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)  
 <span data-ttu-id="f5a53-123">Nesne sahipliği ve kullanıcı-schema ayrımı açıklanmakta ve ek kaynaklara bağlantılar sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f5a53-123">Describes object ownership and  user-schema separation and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="f5a53-124">Yetkilendirme ve SQL Server'daki izinleri</span><span class="sxs-lookup"><span data-stu-id="f5a53-124">Authorization and Permissions in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)  
 <span data-ttu-id="f5a53-125">En az ayrıcalık ilkesini kullanarak izinleri verme açıklanmakta ve ek kaynaklara bağlantılar sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f5a53-125">Describes granting permissions using the principle of least privilege and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="f5a53-126">SQL Server verileri şifreleme</span><span class="sxs-lookup"><span data-stu-id="f5a53-126">Data Encryption in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/data-encryption-in-sql-server.md)  
 <span data-ttu-id="f5a53-127">SQL Server veri şifreleme seçenekleri açıklar ve ek kaynaklara bağlantılar sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f5a53-127">Describes data encryption options in SQL Server and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="f5a53-128">SQL Server CLR tümleştirmesi güvenliği</span><span class="sxs-lookup"><span data-stu-id="f5a53-128">CLR Integration Security in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/clr-integration-security-in-sql-server.md)  
 <span data-ttu-id="f5a53-129">CLR tümleştirme güvenlik kaynaklara bağlantılar sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f5a53-129">Provides links to CLR integration security resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5a53-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f5a53-130">See Also</span></span>  
 [<span data-ttu-id="f5a53-131">ADO.NET uygulamalarının güvenliğini sağlama</span><span class="sxs-lookup"><span data-stu-id="f5a53-131">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="f5a53-132">SQL Server güvenlik</span><span class="sxs-lookup"><span data-stu-id="f5a53-132">SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 [<span data-ttu-id="f5a53-133">SQL Server'daki uygulama güvenlik senaryoları</span><span class="sxs-lookup"><span data-stu-id="f5a53-133">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [<span data-ttu-id="f5a53-134">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="f5a53-134">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
