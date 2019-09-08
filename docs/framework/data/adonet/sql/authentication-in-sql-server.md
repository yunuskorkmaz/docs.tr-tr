---
title: SQL Server’da Kimlik Doğrulaması
ms.date: 05/22/2018
ms.assetid: 646ddbf5-dd4e-4285-8e4a-f565f666c5cc
ms.openlocfilehash: 49835ebf8ebe4d5bd200ed771477edc8af580b7d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794286"
---
# <a name="authentication-in-sql-server"></a><span data-ttu-id="77a9c-102">SQL Server’da Kimlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="77a9c-102">Authentication in SQL Server</span></span>
<span data-ttu-id="77a9c-103">SQL Server, Windows kimlik doğrulama modu ve karma mod olmak üzere iki kimlik doğrulama modunu destekler.</span><span class="sxs-lookup"><span data-stu-id="77a9c-103">SQL Server supports two authentication modes, Windows authentication mode and mixed mode.</span></span>  
  
- <span data-ttu-id="77a9c-104">Windows kimlik doğrulaması varsayılandır ve genellikle tümleşik güvenlik olarak adlandırılır çünkü bu SQL Server güvenlik modeli Windows ile sıkı bir şekilde tümleşiktir.</span><span class="sxs-lookup"><span data-stu-id="77a9c-104">Windows authentication is the default, and is often referred to as integrated security because this SQL Server security model is tightly integrated with Windows.</span></span> <span data-ttu-id="77a9c-105">Belirli Windows Kullanıcı ve grup hesaplarının SQL Server oturum açması için güvenilir.</span><span class="sxs-lookup"><span data-stu-id="77a9c-105">Specific Windows user and group accounts are trusted to log in to SQL Server.</span></span> <span data-ttu-id="77a9c-106">Önceden yetkilendirilmiş olan Windows kullanıcılarının ek kimlik bilgileri sunmak zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="77a9c-106">Windows users who have already been authenticated do not have to present additional credentials.</span></span>  
  
- <span data-ttu-id="77a9c-107">Karma mod, hem Windows hem de SQL Server tarafından kimlik doğrulamasını destekler.</span><span class="sxs-lookup"><span data-stu-id="77a9c-107">Mixed mode supports authentication both by Windows and by SQL Server.</span></span> <span data-ttu-id="77a9c-108">Kullanıcı adı ve parola çiftleri SQL Server içinde tutulur.</span><span class="sxs-lookup"><span data-stu-id="77a9c-108">User name and password pairs are maintained within SQL Server.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="77a9c-109">Mümkün olan yerlerde Windows kimlik doğrulaması kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="77a9c-109">We recommend using Windows authentication wherever possible.</span></span> <span data-ttu-id="77a9c-110">Windows kimlik doğrulaması, SQL Server kullanıcıların kimliğini doğrulamak için bir dizi şifrelenmiş ileti kullanır.</span><span class="sxs-lookup"><span data-stu-id="77a9c-110">Windows authentication uses a series of encrypted messages to authenticate users in SQL Server.</span></span> <span data-ttu-id="77a9c-111">SQL Server oturumlar kullanıldığında, SQL Server oturum açma adları ve şifreli parolalar ağ üzerinden geçirilir ve bu da daha az güvenli hale gelir.</span><span class="sxs-lookup"><span data-stu-id="77a9c-111">When SQL Server logins are used, SQL Server login names and encrypted passwords are passed across the network, which makes them less secure.</span></span>  
  
 <span data-ttu-id="77a9c-112">Windows kimlik doğrulaması ile kullanıcılar zaten Windows 'da oturum açar ve SQL Server için ayrı olarak oturum açmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="77a9c-112">With Windows authentication, users are already logged onto Windows and do not have to log on separately to SQL Server.</span></span> <span data-ttu-id="77a9c-113">Aşağıda `SqlConnection.ConnectionString` , kullanıcıların bir Kullanıcı adı veya parola sağlaması gerekmeden Windows kimlik doğrulaması belirtilir.</span><span class="sxs-lookup"><span data-stu-id="77a9c-113">The following `SqlConnection.ConnectionString` specifies Windows authentication without requiring users to provide a user name or password.</span></span>  
  
```  
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;  
```  
  
> [!NOTE]
> <span data-ttu-id="77a9c-114">Oturum açmalar veritabanı kullanıcılarından farklıdır.</span><span class="sxs-lookup"><span data-stu-id="77a9c-114">Logins are distinct from database users.</span></span> <span data-ttu-id="77a9c-115">Ayrı bir işlemde veritabanı kullanıcıları veya rolleri için oturum açma işlemlerini veya Windows gruplarını eşlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="77a9c-115">You must map logins or Windows groups to database users or roles in a separate operation.</span></span> <span data-ttu-id="77a9c-116">Daha sonra kullanıcılara veya rollere veritabanı nesnelerine erişim izni verirsiniz.</span><span class="sxs-lookup"><span data-stu-id="77a9c-116">You then grant permissions to users or roles to access database objects.</span></span>  
  
## <a name="authentication-scenarios"></a><span data-ttu-id="77a9c-117">Kimlik doğrulama senaryoları</span><span class="sxs-lookup"><span data-stu-id="77a9c-117">Authentication Scenarios</span></span>  
 <span data-ttu-id="77a9c-118">Windows kimlik doğrulaması, genellikle aşağıdaki durumlarda en iyi seçenektir:</span><span class="sxs-lookup"><span data-stu-id="77a9c-118">Windows authentication is usually the best choice in the following situations:</span></span>  
  
- <span data-ttu-id="77a9c-119">Bir etki alanı denetleyicisi vardır.</span><span class="sxs-lookup"><span data-stu-id="77a9c-119">There is a domain controller.</span></span>  
  
- <span data-ttu-id="77a9c-120">Uygulama ve veritabanı aynı bilgisayarlardır.</span><span class="sxs-lookup"><span data-stu-id="77a9c-120">The application and the database are on the same computer.</span></span>  
  
- <span data-ttu-id="77a9c-121">SQL Server Express veya LocalDB örneğini kullanıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="77a9c-121">You are using an instance of SQL Server Express or LocalDB.</span></span>  
  
 <span data-ttu-id="77a9c-122">SQL Server oturum açma işlemleri genellikle aşağıdaki durumlarda kullanılır:</span><span class="sxs-lookup"><span data-stu-id="77a9c-122">SQL Server logins are often used in the following situations:</span></span>  
  
- <span data-ttu-id="77a9c-123">Bir çalışma grubunuz varsa.</span><span class="sxs-lookup"><span data-stu-id="77a9c-123">If you have a workgroup.</span></span>  
  
- <span data-ttu-id="77a9c-124">Kullanıcılar farklı, güvenilir olmayan etki alanlarından bağlanır.</span><span class="sxs-lookup"><span data-stu-id="77a9c-124">Users connect from different, non-trusted domains.</span></span>  
  
- <span data-ttu-id="77a9c-125">ASP.NET gibi Internet uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="77a9c-125">Internet applications, such as ASP.NET.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="77a9c-126">Windows kimlik doğrulamasının belirtilmesi SQL Server oturum açma işlemlerini devre dışı bırakmaz.</span><span class="sxs-lookup"><span data-stu-id="77a9c-126">Specifying Windows authentication does not disable SQL Server logins.</span></span> <span data-ttu-id="77a9c-127">Yüksek ayrıcalıklı SQL Server oturumlarını devre dışı bırakmak için ALTER LOGıN DISABLE Transact-SQL deyimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="77a9c-127">Use the ALTER LOGIN DISABLE Transact-SQL statement to disable highly-privileged SQL Server logins.</span></span>  
  
## <a name="login-types"></a><span data-ttu-id="77a9c-128">Oturum açma türleri</span><span class="sxs-lookup"><span data-stu-id="77a9c-128">Login Types</span></span>  
 <span data-ttu-id="77a9c-129">SQL Server üç oturum açma türünü destekler:</span><span class="sxs-lookup"><span data-stu-id="77a9c-129">SQL Server supports three types of logins:</span></span>  
  
- <span data-ttu-id="77a9c-130">Yerel bir Windows Kullanıcı hesabı veya güvenilen etki alanı hesabı.</span><span class="sxs-lookup"><span data-stu-id="77a9c-130">A local Windows user account or trusted domain account.</span></span> <span data-ttu-id="77a9c-131">SQL Server Windows Kullanıcı hesaplarının kimliğini doğrulamak için Windows 'a bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="77a9c-131">SQL Server relies on Windows to authenticate the Windows user accounts.</span></span>  
  
- <span data-ttu-id="77a9c-132">Windows grubu.</span><span class="sxs-lookup"><span data-stu-id="77a9c-132">Windows group.</span></span> <span data-ttu-id="77a9c-133">Bir Windows grubuna erişim verilmesi, grubun üyesi olan tüm Windows kullanıcı oturumlarına erişim verir.</span><span class="sxs-lookup"><span data-stu-id="77a9c-133">Granting access to a Windows group grants access to all Windows user logins that are members of the group.</span></span>  
  
- <span data-ttu-id="77a9c-134">SQL Server oturum açma.</span><span class="sxs-lookup"><span data-stu-id="77a9c-134">SQL Server login.</span></span> <span data-ttu-id="77a9c-135">SQL Server, oturum açma girişimlerini doğrulamak için iç kimlik doğrulama yöntemlerini kullanarak hem Kullanıcı adını hem de parolanın karmasını ana veritabanında depolar.</span><span class="sxs-lookup"><span data-stu-id="77a9c-135">SQL Server stores both the username and a hash of the password in the master database, by using internal authentication methods to verify login attempts.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="77a9c-136">SQL Server, sertifikalardan veya yalnızca kod imzalama için kullanılan asimetrik anahtarlardan oluşturulan oturum açma işlemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="77a9c-136">SQL Server provides logins created from certificates or asymmetric keys that are used only for code signing.</span></span> <span data-ttu-id="77a9c-137">SQL Server bağlanmak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="77a9c-137">They cannot be used to connect to SQL Server.</span></span>  
  
## <a name="mixed-mode-authentication"></a><span data-ttu-id="77a9c-138">Karma mod kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="77a9c-138">Mixed Mode Authentication</span></span>  
 <span data-ttu-id="77a9c-139">Karma mod kimlik doğrulaması kullanmanız gerekiyorsa, SQL Server depolanan SQL Server oturum açma bilgileri oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="77a9c-139">If you must use mixed mode authentication, you must create SQL Server logins, which are stored in SQL Server.</span></span> <span data-ttu-id="77a9c-140">Daha sonra çalışma zamanında SQL Server Kullanıcı adı ve parola sağlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="77a9c-140">You then have to supply the SQL Server user name and password at run time.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="77a9c-141">SQL Server, ("Sistem Yöneticisi" `sa` kısaltması) adlı SQL Server bir oturum açma ile yüklenir.</span><span class="sxs-lookup"><span data-stu-id="77a9c-141">SQL Server installs with a SQL Server login named `sa` (an abbreviation of "system administrator").</span></span> <span data-ttu-id="77a9c-142">`sa` Oturum açmak için güçlü bir parola atayın ve uygulamanızdaki `sa` oturum açma bilgilerini kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="77a9c-142">Assign a strong password to the `sa` login and do not use the `sa` login in your application.</span></span> <span data-ttu-id="77a9c-143">Oturum açma, tüm sunucuda `sysadmin` yönetici kimlik bilgilerini geri alınamaz olan sabit sunucu rolüyle eşlenir. `sa`</span><span class="sxs-lookup"><span data-stu-id="77a9c-143">The `sa` login maps to the `sysadmin` fixed server role, which has irrevocable administrative credentials on the whole server.</span></span> <span data-ttu-id="77a9c-144">Bir saldırgan sistem yöneticisi olarak erişim kazanırsa olası hasara yönelik bir sınır yoktur.</span><span class="sxs-lookup"><span data-stu-id="77a9c-144">There are no limits to the potential damage if an attacker gains access as a system administrator.</span></span> <span data-ttu-id="77a9c-145">Windows `BUILTIN\Administrators` grubunun (yerel yönetici grubu) tüm üyeleri, varsayılan olarak `sysadmin` rolün üyeleridir, ancak bu rolden kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="77a9c-145">All members of the Windows `BUILTIN\Administrators` group (the local administrator's group) are members of the `sysadmin` role by default, but can be removed from that role.</span></span>  
  
 <span data-ttu-id="77a9c-146">SQL Server, [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] veya sonraki sürümlerde çalışırken SQL Server oturum açma işlemleri için Windows parola ilkesi mekanizmaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="77a9c-146">SQL Server provides Windows password policy mechanisms for SQL Server logins when it is running on [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] or later versions.</span></span> <span data-ttu-id="77a9c-147">Parola karmaşıklığı ilkeleri, olası parola sayısını artırarak deneme yanılma saldırılarını ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="77a9c-147">Password complexity policies are designed to deter brute force attacks by increasing the number of possible passwords.</span></span> <span data-ttu-id="77a9c-148">SQL Server, ' de [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] kullanılan karmaşıklık ve süre sonu ilkelerini SQL Server içinde kullanılan parolalara uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="77a9c-148">SQL Server can apply the same complexity and expiration policies used in [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] to passwords used inside SQL Server.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="77a9c-149">Bağlantı dizelerini Kullanıcı girişinden bitiştirme, bağlantı dizesi ekleme saldırısına karşı savunmasız bırakabilir.</span><span class="sxs-lookup"><span data-stu-id="77a9c-149">Concatenating connection strings from user input can leave you vulnerable to a connection string injection attack.</span></span> <span data-ttu-id="77a9c-150">Çalışma zamanında sözdizimsel olarak geçerli bağlantı dizeleri oluşturmak için öğesini kullanın. <xref:System.Data.SqlClient.SqlConnectionStringBuilder></span><span class="sxs-lookup"><span data-stu-id="77a9c-150">Use the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> to create syntactically valid connection strings at run time.</span></span> <span data-ttu-id="77a9c-151">Daha fazla bilgi için bkz. [bağlantı dizesi oluşturucuları](../connection-string-builders.md).</span><span class="sxs-lookup"><span data-stu-id="77a9c-151">For more information, see [Connection String Builders](../connection-string-builders.md).</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="77a9c-152">Dış Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="77a9c-152">External Resources</span></span>  
 <span data-ttu-id="77a9c-153">Daha fazla bilgi için aşağıdaki kaynaklara bakın.</span><span class="sxs-lookup"><span data-stu-id="77a9c-153">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="77a9c-154">Kaynak</span><span class="sxs-lookup"><span data-stu-id="77a9c-154">Resource</span></span>|<span data-ttu-id="77a9c-155">Açıklama</span><span class="sxs-lookup"><span data-stu-id="77a9c-155">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="77a9c-156">Sorumlusu</span><span class="sxs-lookup"><span data-stu-id="77a9c-156">Principals</span></span>](/sql/relational-databases/security/authentication-access/principals-database-engine)|<span data-ttu-id="77a9c-157">SQL Server oturum açma işlemlerini ve diğer güvenlik sorumlularını açıklar.</span><span class="sxs-lookup"><span data-stu-id="77a9c-157">Describes logins and other security principals in SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="77a9c-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77a9c-158">See also</span></span>

- [<span data-ttu-id="77a9c-159">ADO.NET Uygulamalarının Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="77a9c-159">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="77a9c-160">SQL Server'da Uygulama Güvenliği Senaryoları</span><span class="sxs-lookup"><span data-stu-id="77a9c-160">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="77a9c-161">Veri Kaynağına Bağlanma</span><span class="sxs-lookup"><span data-stu-id="77a9c-161">Connecting to a Data Source</span></span>](../connecting-to-a-data-source.md)
- [<span data-ttu-id="77a9c-162">Bağlantı Dizeleri</span><span class="sxs-lookup"><span data-stu-id="77a9c-162">Connection Strings</span></span>](../connection-strings.md)
- [<span data-ttu-id="77a9c-163">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="77a9c-163">ADO.NET Overview</span></span>](../ado-net-overview.md)
