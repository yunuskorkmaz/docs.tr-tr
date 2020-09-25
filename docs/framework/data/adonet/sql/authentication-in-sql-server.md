---
title: SQL Server’da Kimlik Doğrulaması
description: Windows kimlik doğrulama modu ve karma mod dahil olmak üzere ADO.NET için SQL Server kimlik doğrulaması hakkında bilgi edinin.
ms.date: 05/22/2018
ms.assetid: 646ddbf5-dd4e-4285-8e4a-f565f666c5cc
ms.openlocfilehash: 2c4f62391a0d9b5ada27f56eef4c3467d99b4c6d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197540"
---
# <a name="authentication-in-sql-server"></a><span data-ttu-id="2bf54-103">SQL Server’da Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="2bf54-103">Authentication in SQL Server</span></span>

<span data-ttu-id="2bf54-104">SQL Server, Windows kimlik doğrulama modu ve karma mod olmak üzere iki kimlik doğrulama modunu destekler.</span><span class="sxs-lookup"><span data-stu-id="2bf54-104">SQL Server supports two authentication modes, Windows authentication mode and mixed mode.</span></span>  
  
- <span data-ttu-id="2bf54-105">Windows kimlik doğrulaması varsayılandır ve genellikle tümleşik güvenlik olarak adlandırılır çünkü bu SQL Server güvenlik modeli Windows ile sıkı bir şekilde tümleşiktir.</span><span class="sxs-lookup"><span data-stu-id="2bf54-105">Windows authentication is the default, and is often referred to as integrated security because this SQL Server security model is tightly integrated with Windows.</span></span> <span data-ttu-id="2bf54-106">Belirli Windows Kullanıcı ve grup hesaplarının SQL Server oturum açması için güvenilir.</span><span class="sxs-lookup"><span data-stu-id="2bf54-106">Specific Windows user and group accounts are trusted to log in to SQL Server.</span></span> <span data-ttu-id="2bf54-107">Önceden yetkilendirilmiş olan Windows kullanıcılarının ek kimlik bilgileri sunmak zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="2bf54-107">Windows users who have already been authenticated do not have to present additional credentials.</span></span>  
  
- <span data-ttu-id="2bf54-108">Karma mod, hem Windows hem de SQL Server tarafından kimlik doğrulamasını destekler.</span><span class="sxs-lookup"><span data-stu-id="2bf54-108">Mixed mode supports authentication both by Windows and by SQL Server.</span></span> <span data-ttu-id="2bf54-109">Kullanıcı adı ve parola çiftleri SQL Server içinde tutulur.</span><span class="sxs-lookup"><span data-stu-id="2bf54-109">User name and password pairs are maintained within SQL Server.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2bf54-110">Mümkün olan yerlerde Windows kimlik doğrulaması kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="2bf54-110">We recommend using Windows authentication wherever possible.</span></span> <span data-ttu-id="2bf54-111">Windows kimlik doğrulaması, SQL Server kullanıcıların kimliğini doğrulamak için bir dizi şifrelenmiş ileti kullanır.</span><span class="sxs-lookup"><span data-stu-id="2bf54-111">Windows authentication uses a series of encrypted messages to authenticate users in SQL Server.</span></span> <span data-ttu-id="2bf54-112">SQL Server oturumlar kullanıldığında, SQL Server oturum açma adları ve şifreli parolalar ağ üzerinden geçirilir ve bu da daha az güvenli hale gelir.</span><span class="sxs-lookup"><span data-stu-id="2bf54-112">When SQL Server logins are used, SQL Server login names and encrypted passwords are passed across the network, which makes them less secure.</span></span>  
  
 <span data-ttu-id="2bf54-113">Windows kimlik doğrulaması ile kullanıcılar zaten Windows 'da oturum açar ve SQL Server için ayrı olarak oturum açmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="2bf54-113">With Windows authentication, users are already logged onto Windows and do not have to log on separately to SQL Server.</span></span> <span data-ttu-id="2bf54-114">Aşağıda, `SqlConnection.ConnectionString` kullanıcıların bir Kullanıcı adı veya parola sağlaması gerekmeden Windows kimlik doğrulaması belirtilir.</span><span class="sxs-lookup"><span data-stu-id="2bf54-114">The following `SqlConnection.ConnectionString` specifies Windows authentication without requiring users to provide a user name or password.</span></span>  
  
```csharp  
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;"
```  
  
> [!NOTE]
> <span data-ttu-id="2bf54-115">Oturum açmalar veritabanı kullanıcılarından farklıdır.</span><span class="sxs-lookup"><span data-stu-id="2bf54-115">Logins are distinct from database users.</span></span> <span data-ttu-id="2bf54-116">Ayrı bir işlemde veritabanı kullanıcıları veya rolleri için oturum açma işlemlerini veya Windows gruplarını eşlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2bf54-116">You must map logins or Windows groups to database users or roles in a separate operation.</span></span> <span data-ttu-id="2bf54-117">Daha sonra kullanıcılara veya rollere veritabanı nesnelerine erişim izni verirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2bf54-117">You then grant permissions to users or roles to access database objects.</span></span>  
  
## <a name="authentication-scenarios"></a><span data-ttu-id="2bf54-118">Kimlik doğrulama senaryoları</span><span class="sxs-lookup"><span data-stu-id="2bf54-118">Authentication Scenarios</span></span>  

 <span data-ttu-id="2bf54-119">Windows kimlik doğrulaması, genellikle aşağıdaki durumlarda en iyi seçenektir:</span><span class="sxs-lookup"><span data-stu-id="2bf54-119">Windows authentication is usually the best choice in the following situations:</span></span>  
  
- <span data-ttu-id="2bf54-120">Bir etki alanı denetleyicisi vardır.</span><span class="sxs-lookup"><span data-stu-id="2bf54-120">There is a domain controller.</span></span>  
  
- <span data-ttu-id="2bf54-121">Uygulama ve veritabanı aynı bilgisayarlardır.</span><span class="sxs-lookup"><span data-stu-id="2bf54-121">The application and the database are on the same computer.</span></span>  
  
- <span data-ttu-id="2bf54-122">SQL Server Express veya LocalDB örneğini kullanıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="2bf54-122">You are using an instance of SQL Server Express or LocalDB.</span></span>  
  
 <span data-ttu-id="2bf54-123">SQL Server oturum açma işlemleri genellikle aşağıdaki durumlarda kullanılır:</span><span class="sxs-lookup"><span data-stu-id="2bf54-123">SQL Server logins are often used in the following situations:</span></span>  
  
- <span data-ttu-id="2bf54-124">Bir çalışma grubunuz varsa.</span><span class="sxs-lookup"><span data-stu-id="2bf54-124">If you have a workgroup.</span></span>  
  
- <span data-ttu-id="2bf54-125">Kullanıcılar farklı, güvenilir olmayan etki alanlarından bağlanır.</span><span class="sxs-lookup"><span data-stu-id="2bf54-125">Users connect from different, non-trusted domains.</span></span>  
  
- <span data-ttu-id="2bf54-126">ASP.NET gibi Internet uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="2bf54-126">Internet applications, such as ASP.NET.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2bf54-127">Windows kimlik doğrulamasının belirtilmesi SQL Server oturum açma işlemlerini devre dışı bırakmaz.</span><span class="sxs-lookup"><span data-stu-id="2bf54-127">Specifying Windows authentication does not disable SQL Server logins.</span></span> <span data-ttu-id="2bf54-128">Yüksek ayrıcalıklı SQL Server oturumlarını devre dışı bırakmak için ALTER LOGıN DISABLE Transact-SQL deyimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2bf54-128">Use the ALTER LOGIN DISABLE Transact-SQL statement to disable highly-privileged SQL Server logins.</span></span>  
  
## <a name="login-types"></a><span data-ttu-id="2bf54-129">Oturum açma türleri</span><span class="sxs-lookup"><span data-stu-id="2bf54-129">Login Types</span></span>  

 <span data-ttu-id="2bf54-130">SQL Server üç oturum açma türünü destekler:</span><span class="sxs-lookup"><span data-stu-id="2bf54-130">SQL Server supports three types of logins:</span></span>  
  
- <span data-ttu-id="2bf54-131">Yerel bir Windows Kullanıcı hesabı veya güvenilen etki alanı hesabı.</span><span class="sxs-lookup"><span data-stu-id="2bf54-131">A local Windows user account or trusted domain account.</span></span> <span data-ttu-id="2bf54-132">SQL Server Windows Kullanıcı hesaplarının kimliğini doğrulamak için Windows 'a bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="2bf54-132">SQL Server relies on Windows to authenticate the Windows user accounts.</span></span>  
  
- <span data-ttu-id="2bf54-133">Windows grubu.</span><span class="sxs-lookup"><span data-stu-id="2bf54-133">Windows group.</span></span> <span data-ttu-id="2bf54-134">Bir Windows grubuna erişim verilmesi, grubun üyesi olan tüm Windows kullanıcı oturumlarına erişim verir.</span><span class="sxs-lookup"><span data-stu-id="2bf54-134">Granting access to a Windows group grants access to all Windows user logins that are members of the group.</span></span>  
  
- <span data-ttu-id="2bf54-135">SQL Server oturum açma.</span><span class="sxs-lookup"><span data-stu-id="2bf54-135">SQL Server login.</span></span> <span data-ttu-id="2bf54-136">SQL Server, oturum açma girişimlerini doğrulamak için iç kimlik doğrulama yöntemlerini kullanarak hem Kullanıcı adını hem de parolanın karmasını ana veritabanında depolar.</span><span class="sxs-lookup"><span data-stu-id="2bf54-136">SQL Server stores both the username and a hash of the password in the master database, by using internal authentication methods to verify login attempts.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2bf54-137">SQL Server, sertifikalardan veya yalnızca kod imzalama için kullanılan asimetrik anahtarlardan oluşturulan oturum açma işlemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="2bf54-137">SQL Server provides logins created from certificates or asymmetric keys that are used only for code signing.</span></span> <span data-ttu-id="2bf54-138">SQL Server bağlanmak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2bf54-138">They cannot be used to connect to SQL Server.</span></span>  
  
## <a name="mixed-mode-authentication"></a><span data-ttu-id="2bf54-139">Karma mod kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="2bf54-139">Mixed Mode Authentication</span></span>  

 <span data-ttu-id="2bf54-140">Karma mod kimlik doğrulaması kullanmanız gerekiyorsa, SQL Server depolanan SQL Server oturum açma bilgileri oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2bf54-140">If you must use mixed mode authentication, you must create SQL Server logins, which are stored in SQL Server.</span></span> <span data-ttu-id="2bf54-141">Daha sonra çalışma zamanında SQL Server Kullanıcı adı ve parola sağlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="2bf54-141">You then have to supply the SQL Server user name and password at run time.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2bf54-142">SQL Server, `sa` ("Sistem Yöneticisi" kısaltması) adlı SQL Server bir oturum açma ile yüklenir.</span><span class="sxs-lookup"><span data-stu-id="2bf54-142">SQL Server installs with a SQL Server login named `sa` (an abbreviation of "system administrator").</span></span> <span data-ttu-id="2bf54-143">Oturum açmak için güçlü bir parola atayın `sa` ve `sa` uygulamanızdaki oturum açma bilgilerini kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="2bf54-143">Assign a strong password to the `sa` login and do not use the `sa` login in your application.</span></span> <span data-ttu-id="2bf54-144">`sa`Oturum açma, `sysadmin` Tüm sunucuda yönetici kimlik bilgilerini geri alınamaz olan sabit sunucu rolüyle eşlenir.</span><span class="sxs-lookup"><span data-stu-id="2bf54-144">The `sa` login maps to the `sysadmin` fixed server role, which has irrevocable administrative credentials on the whole server.</span></span> <span data-ttu-id="2bf54-145">Bir saldırgan sistem yöneticisi olarak erişim kazanırsa olası hasara yönelik bir sınır yoktur.</span><span class="sxs-lookup"><span data-stu-id="2bf54-145">There are no limits to the potential damage if an attacker gains access as a system administrator.</span></span> <span data-ttu-id="2bf54-146">Windows `BUILTIN\Administrators` grubunun (yerel yönetici grubu) tüm üyeleri, `sysadmin` Varsayılan olarak rolün üyeleridir, ancak bu rolden kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="2bf54-146">All members of the Windows `BUILTIN\Administrators` group (the local administrator's group) are members of the `sysadmin` role by default, but can be removed from that role.</span></span>  
  
 <span data-ttu-id="2bf54-147">SQL Server, SQL Server oturum açma işlemleri için Windows parola ilke mekanizmaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="2bf54-147">SQL Server provides Windows password policy mechanisms for SQL Server logins.</span></span> <span data-ttu-id="2bf54-148">Parola karmaşıklığı ilkeleri, olası parola sayısını artırarak deneme yanılma saldırılarını ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="2bf54-148">Password complexity policies are designed to deter brute force attacks by increasing the number of possible passwords.</span></span> <span data-ttu-id="2bf54-149">SQL Server, SQL Server içinde kullanılan parolalara aynı karmaşıklık ve süre sonu ilkelerini uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="2bf54-149">SQL Server can apply the same complexity and expiration policies to passwords used inside SQL Server.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2bf54-150">Bağlantı dizelerini Kullanıcı girişinden bitiştirme, bağlantı dizesi ekleme saldırısına karşı savunmasız bırakabilir.</span><span class="sxs-lookup"><span data-stu-id="2bf54-150">Concatenating connection strings from user input can leave you vulnerable to a connection string injection attack.</span></span> <span data-ttu-id="2bf54-151"><xref:System.Data.SqlClient.SqlConnectionStringBuilder>Çalışma zamanında sözdizimsel olarak geçerli bağlantı dizeleri oluşturmak için öğesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2bf54-151">Use the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> to create syntactically valid connection strings at run time.</span></span> <span data-ttu-id="2bf54-152">Daha fazla bilgi için bkz. [bağlantı dizesi oluşturucuları](../connection-string-builders.md).</span><span class="sxs-lookup"><span data-stu-id="2bf54-152">For more information, see [Connection String Builders](../connection-string-builders.md).</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="2bf54-153">Dış Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="2bf54-153">External Resources</span></span>  

 <span data-ttu-id="2bf54-154">Daha fazla bilgi için aşağıdaki kaynaklara bakın.</span><span class="sxs-lookup"><span data-stu-id="2bf54-154">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="2bf54-155">Kaynak</span><span class="sxs-lookup"><span data-stu-id="2bf54-155">Resource</span></span>|<span data-ttu-id="2bf54-156">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2bf54-156">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="2bf54-157">Sorumlular</span><span class="sxs-lookup"><span data-stu-id="2bf54-157">Principals</span></span>](/sql/relational-databases/security/authentication-access/principals-database-engine)|<span data-ttu-id="2bf54-158">SQL Server oturum açma işlemlerini ve diğer güvenlik sorumlularını açıklar.</span><span class="sxs-lookup"><span data-stu-id="2bf54-158">Describes logins and other security principals in SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2bf54-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2bf54-159">See also</span></span>

- [<span data-ttu-id="2bf54-160">ADO.NET Uygulamalarının Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="2bf54-160">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="2bf54-161">SQL Server'da Uygulama Güvenliği Senaryoları</span><span class="sxs-lookup"><span data-stu-id="2bf54-161">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="2bf54-162">Bir veri kaynağına bağlanma</span><span class="sxs-lookup"><span data-stu-id="2bf54-162">Connecting to a Data Source</span></span>](../connecting-to-a-data-source.md)
- [<span data-ttu-id="2bf54-163">Bağlantı dizeleri</span><span class="sxs-lookup"><span data-stu-id="2bf54-163">Connection Strings</span></span>](../connection-strings.md)
- [<span data-ttu-id="2bf54-164">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2bf54-164">ADO.NET Overview</span></span>](../ado-net-overview.md)
