---
title: SQL Server kimlik doğrulaması
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 646ddbf5-dd4e-4285-8e4a-f565f666c5cc
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 1c918df5de4a66c00f6fd9b9dd1719ac05041ce1
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="authentication-in-sql-server"></a><span data-ttu-id="3ce41-102">SQL Server kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="3ce41-102">Authentication in SQL Server</span></span>
<span data-ttu-id="3ce41-103">SQL Server iki kimlik doğrulama modu, Windows kimlik doğrulama modu ve karma mod destekler.</span><span class="sxs-lookup"><span data-stu-id="3ce41-103">SQL Server supports two authentication modes, Windows authentication mode and mixed mode.</span></span>  
  
-   <span data-ttu-id="3ce41-104">Windows kimlik doğrulaması varsayılandır ve bu SQL Server güvenlik modeli sıkı bir şekilde Windows ile tümleşik olduğundan genellikle tümleşik güvenlik adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="3ce41-104">Windows authentication is the default, and is often referred to as integrated security because this SQL Server security model is tightly integrated with Windows.</span></span> <span data-ttu-id="3ce41-105">Belirli Windows kullanıcı ve grup hesaplarını SQL Server'da oturum açma için güvenilir.</span><span class="sxs-lookup"><span data-stu-id="3ce41-105">Specific Windows user and group accounts are trusted to log in to SQL Server.</span></span> <span data-ttu-id="3ce41-106">Önceden doğrulanmış Windows kullanıcılar ek kimlik bilgileri sunmak gerekmez.</span><span class="sxs-lookup"><span data-stu-id="3ce41-106">Windows users who have already been authenticated do not have to present additional credentials.</span></span>  
  
-   <span data-ttu-id="3ce41-107">Karma mod hem Windows hem SQL Server kimlik doğrulamasını destekler.</span><span class="sxs-lookup"><span data-stu-id="3ce41-107">Mixed mode supports authentication both by Windows and by SQL Server.</span></span> <span data-ttu-id="3ce41-108">Kullanıcı adı ve parola çiftleri SQL Server'ın içinde saklanır.</span><span class="sxs-lookup"><span data-stu-id="3ce41-108">User name and password pairs are maintained within SQL Server.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3ce41-109">Mümkün olduğunda Windows kimlik doğrulaması kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="3ce41-109">We recommend using Windows authentication wherever possible.</span></span> <span data-ttu-id="3ce41-110">Windows kimlik doğrulaması şifrelenmiş iletileri bir dizi SQL Server'da kullanıcıların kimliklerini doğrulamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="3ce41-110">Windows authentication uses a series of encrypted messages to authenticate users in SQL Server.</span></span> <span data-ttu-id="3ce41-111">SQL Server oturumları kullanıldığında, SQL Server oturum açma adları ve parolalar daha az güvenli hale getirir ağ üzerinden iletilir.</span><span class="sxs-lookup"><span data-stu-id="3ce41-111">When SQL Server logins are used, SQL Server login names and passwords are passed across the network, which makes them less secure.</span></span>  
  
 <span data-ttu-id="3ce41-112">Windows kimlik doğrulaması, kullanıcıların zaten Windows'da oturum ve ayrı olarak SQL Server'da oturum gerekmez.</span><span class="sxs-lookup"><span data-stu-id="3ce41-112">With Windows authentication, users are already logged onto Windows and do not have to log on separately to SQL Server.</span></span> <span data-ttu-id="3ce41-113">Aşağıdaki `SqlConnection.ConnectionString` gerek kalmadan Windows kimlik doğrulaması belirtir bir kullanıcı adı veya parola.</span><span class="sxs-lookup"><span data-stu-id="3ce41-113">The following `SqlConnection.ConnectionString` specifies Windows authentication without requiring the a user name or password.</span></span>  
  
```  
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;  
```  
  
> [!NOTE]
>  <span data-ttu-id="3ce41-114">Oturum açma bilgileri, veritabanı kullanıcıları farklıdır.</span><span class="sxs-lookup"><span data-stu-id="3ce41-114">Logins are distinct from database users.</span></span> <span data-ttu-id="3ce41-115">Veritabanı kullanıcılar ya da ayrı bir işlemle roller için oturum açma veya Windows grupları eşlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3ce41-115">You must map logins or Windows groups to database users or roles in a separate operation.</span></span> <span data-ttu-id="3ce41-116">Veritabanı nesneleri erişmek için kullanıcı veya rol ardından izinleri verin.</span><span class="sxs-lookup"><span data-stu-id="3ce41-116">You then grant permissions to users or roles to access database objects.</span></span>  
  
## <a name="authentication-scenarios"></a><span data-ttu-id="3ce41-117">Kimlik doğrulama senaryoları</span><span class="sxs-lookup"><span data-stu-id="3ce41-117">Authentication Scenarios</span></span>  
 <span data-ttu-id="3ce41-118">Windows kimlik doğrulaması, genellikle en iyi seçenek aşağıdaki durumlarda şöyledir:</span><span class="sxs-lookup"><span data-stu-id="3ce41-118">Windows authentication is usually the best choice in the following situations:</span></span>  
  
-   <span data-ttu-id="3ce41-119">Bir etki alanı denetleyicisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="3ce41-119">There is a domain controller.</span></span>  
  
-   <span data-ttu-id="3ce41-120">Uygulama ve veritabanı aynı bilgisayarda bulunur.</span><span class="sxs-lookup"><span data-stu-id="3ce41-120">The application and the database are on the same computer.</span></span>  
  
-   <span data-ttu-id="3ce41-121">SQL Server Express veya yerel veritabanı örneği kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="3ce41-121">You are using an instance of SQL Server Express or LocalDB.</span></span>  
  
 <span data-ttu-id="3ce41-122">SQL Server oturumları genellikle aşağıdaki durumlarda kullanılır:</span><span class="sxs-lookup"><span data-stu-id="3ce41-122">SQL Server logins are often used in the following situations:</span></span>  
  
-   <span data-ttu-id="3ce41-123">Bir çalışma grubu varsa.</span><span class="sxs-lookup"><span data-stu-id="3ce41-123">If you have a workgroup.</span></span>  
  
-   <span data-ttu-id="3ce41-124">Kullanıcılar farklı, güvenilmeyen etki alanlarından bağlanır.</span><span class="sxs-lookup"><span data-stu-id="3ce41-124">Users connect from different, non-trusted domains.</span></span>  
  
-   <span data-ttu-id="3ce41-125">Internet uygulamaları gibi [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3ce41-125">Internet applications, such as [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3ce41-126">Belirterek Windows kimlik doğrulaması, SQL Server oturumları devre dışı bırakmaz.</span><span class="sxs-lookup"><span data-stu-id="3ce41-126">Specifying Windows authentication does not disable SQL Server logins.</span></span> <span data-ttu-id="3ce41-127">ALTER oturum açma devre dışı kullanmak [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] yüksek ayrıcalıklı SQL Server oturumları devre dışı bırakmak için deyimi.</span><span class="sxs-lookup"><span data-stu-id="3ce41-127">Use the ALTER LOGIN DISABLE [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] statement to disable highly-privileged SQL Server logins.</span></span>  
  
## <a name="login-types"></a><span data-ttu-id="3ce41-128">Oturum açma türleri</span><span class="sxs-lookup"><span data-stu-id="3ce41-128">Login Types</span></span>  
 <span data-ttu-id="3ce41-129">SQL Server oturumu açma üç türlerini destekler:</span><span class="sxs-lookup"><span data-stu-id="3ce41-129">SQL Server supports three types of logins:</span></span>  
  
-   <span data-ttu-id="3ce41-130">Yerel Windows kullanıcı hesabı veya güvenilen etki alanı hesabı.</span><span class="sxs-lookup"><span data-stu-id="3ce41-130">A local Windows user account or trusted domain account.</span></span> <span data-ttu-id="3ce41-131">SQL Server, Windows kullanıcı hesaplarının kimliğini doğrulamak amacıyla Windows kullanır.</span><span class="sxs-lookup"><span data-stu-id="3ce41-131">SQL Server relies on Windows to authenticate the Windows user accounts.</span></span>  
  
-   <span data-ttu-id="3ce41-132">Windows grubu.</span><span class="sxs-lookup"><span data-stu-id="3ce41-132">Windows group.</span></span> <span data-ttu-id="3ce41-133">Bir Windows grubuna erişim verilirken grubunun üyesi olan tüm Windows kullanıcı oturumları erişim verir.</span><span class="sxs-lookup"><span data-stu-id="3ce41-133">Granting access to a Windows group grants access to all Windows user logins that are members of the group.</span></span>  
  
-   <span data-ttu-id="3ce41-134">SQL Server oturum açma.</span><span class="sxs-lookup"><span data-stu-id="3ce41-134">SQL Server login.</span></span> <span data-ttu-id="3ce41-135">SQL Server kullanıcı adı ve parola karmasını ana veritabanında oturum açma denemesi doğrulamak için iç kimlik doğrulama yöntemlerini kullanarak depolar.</span><span class="sxs-lookup"><span data-stu-id="3ce41-135">SQL Server stores both the username and a hash of the password in the master database, by using internal authentication methods to verify login attempts.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3ce41-136">SQL Server, sertifikalar veya yalnızca kod imzalama için kullanılan asimetrik anahtarlar oluşturulan oturum açma bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="3ce41-136">SQL Server provides logins created from certificates or asymmetric keys that are used only for code signing.</span></span> <span data-ttu-id="3ce41-137">SQL Server'a bağlanmak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3ce41-137">They cannot be used to connect to SQL Server.</span></span>  
  
## <a name="mixed-mode-authentication"></a><span data-ttu-id="3ce41-138">Karma mod kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="3ce41-138">Mixed Mode Authentication</span></span>  
 <span data-ttu-id="3ce41-139">Karma mod kimlik doğrulaması kullanmanız gerekiyorsa, SQL sunucusunda depolanan SQL Server oturumları oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3ce41-139">If you must use mixed mode authentication, you must create SQL Server logins, which are stored in SQL Server.</span></span> <span data-ttu-id="3ce41-140">Ardından çalışma zamanında SQL Server kullanıcı adı ve parolasını sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3ce41-140">You then have to supply the SQL Server user name and password at run time.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3ce41-141">SQL Server adlandırılmış bir SQL Server oturum açma ile yükler `sa` ("sistem yöneticisinin" kısaltma).</span><span class="sxs-lookup"><span data-stu-id="3ce41-141">SQL Server installs with a SQL Server login named `sa` (an abbreviation of "system administrator").</span></span> <span data-ttu-id="3ce41-142">Güçlü bir parola atayın `sa` oturum açma ve kullanmayın `sa` uygulamanızda oturum açma.</span><span class="sxs-lookup"><span data-stu-id="3ce41-142">Assign a strong password to the `sa` login and do not use the `sa` login in your application.</span></span> <span data-ttu-id="3ce41-143">`sa` Oturum açma eşlendiğini `sysadmin` tüm sunucuda değiştirilemeyen yönetici kimlik bilgilerine sahip sabit sunucu rolü.</span><span class="sxs-lookup"><span data-stu-id="3ce41-143">The `sa` login maps to the `sysadmin` fixed server role, which has irrevocable administrative credentials on the whole server.</span></span> <span data-ttu-id="3ce41-144">Bir saldırganın bir sistem yöneticisi olarak erişim sağlarsa potansiyel hasarı herhangi bir sınırı vardır.</span><span class="sxs-lookup"><span data-stu-id="3ce41-144">There are no limits to the potential damage if an attacker gains access as a system administrator.</span></span> <span data-ttu-id="3ce41-145">Tüm üyeleri Windows `BUILTIN\Administrators` grubu (yerel yönetici'nin grup) üyeleri olan `sysadmin` rol varsayılan olarak, ancak bu rolden kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="3ce41-145">All members of the Windows `BUILTIN\Administrators` group (the local administrator's group) are members of the `sysadmin` role by default, but can be removed from that role.</span></span>  
  
 <span data-ttu-id="3ce41-146">SQL Server çalışırken SQL Server oturumları için Windows parola ilkesi mekanizmaları sağlar [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] veya sonraki sürümler.</span><span class="sxs-lookup"><span data-stu-id="3ce41-146">SQL Server provides Windows password policy mechanisms for SQL Server logins when it is running on [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] or later versions.</span></span> <span data-ttu-id="3ce41-147">Parola karmaşıklık ilkeleri, deneme yanılma saldırıları mümkün olan parola sayısını artırarak engellenmesine için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="3ce41-147">Password complexity policies are designed to deter brute force attacks by increasing the number of possible passwords.</span></span> <span data-ttu-id="3ce41-148">SQL Server kullanılan aynı karmaşıklık ve sona erme tarihi ilkeleri uygulayabilir [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] için SQL Server içinde kullanılan parolalar.</span><span class="sxs-lookup"><span data-stu-id="3ce41-148">SQL Server can apply the same complexity and expiration policies used in [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] to passwords used inside SQL Server.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3ce41-149">Bağlantı dizeleri kullanıcı girişinden birleştirme bir bağlantı dizesi ekleme saldırısına karşı savunmasız bırakabilir.</span><span class="sxs-lookup"><span data-stu-id="3ce41-149">Concatenating connection strings from user input can leave you vulnerable to a connection string injection attack.</span></span> <span data-ttu-id="3ce41-150">Kullanım <xref:System.Data.SqlClient.SqlConnectionStringBuilder> çalışma zamanında sözdizimsel olarak geçerli bir bağlantı dizesi oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="3ce41-150">Use the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> to create syntactically valid connection strings at run time.</span></span> <span data-ttu-id="3ce41-151">Daha fazla bilgi için bkz: [bağlantı dizesi oluşturucular](../../../../../docs/framework/data/adonet/connection-string-builders.md).</span><span class="sxs-lookup"><span data-stu-id="3ce41-151">For more information, see [Connection String Builders](../../../../../docs/framework/data/adonet/connection-string-builders.md).</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="3ce41-152">Dış Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="3ce41-152">External Resources</span></span>  
 <span data-ttu-id="3ce41-153">Daha fazla bilgi için aşağıdaki kaynaklara bakın.</span><span class="sxs-lookup"><span data-stu-id="3ce41-153">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="3ce41-154">Kaynak</span><span class="sxs-lookup"><span data-stu-id="3ce41-154">Resource</span></span>|<span data-ttu-id="3ce41-155">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3ce41-155">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="3ce41-156">[Asıl adlar](http://msdn.microsoft.com/library/bb543165.aspx) SQL Server Çevrimiçi Kitapları'nda</span><span class="sxs-lookup"><span data-stu-id="3ce41-156">[Principals](http://msdn.microsoft.com/library/bb543165.aspx) in SQL Server Books Online</span></span>|<span data-ttu-id="3ce41-157">Oturum açma bilgileri ve SQL Server'daki diğer güvenlik sorumluları açıklar.</span><span class="sxs-lookup"><span data-stu-id="3ce41-157">Describes logins and other security principals in SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3ce41-158">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3ce41-158">See Also</span></span>  
 [<span data-ttu-id="3ce41-159">ADO.NET Uygulamalarının Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="3ce41-159">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="3ce41-160">SQL Server'da Uygulama Güvenliği Senaryoları</span><span class="sxs-lookup"><span data-stu-id="3ce41-160">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [<span data-ttu-id="3ce41-161">Veri Kaynağına Bağlanma</span><span class="sxs-lookup"><span data-stu-id="3ce41-161">Connecting to a Data Source</span></span>](../../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [<span data-ttu-id="3ce41-162">Bağlantı Dizeleri</span><span class="sxs-lookup"><span data-stu-id="3ce41-162">Connection Strings</span></span>](../../../../../docs/framework/data/adonet/connection-strings.md)  
 [<span data-ttu-id="3ce41-163">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="3ce41-163">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
