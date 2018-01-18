---
title: "Saklı yordamlar SQL Server'daki imzalama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eeed752c-0084-48e5-9dca-381353007a0d
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a3f1ed66ed7caf2272ca27097dc9a838bec7d0ae
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="signing-stored-procedures-in-sql-server"></a><span data-ttu-id="7affc-102">Saklı yordamlar SQL Server'daki imzalama</span><span class="sxs-lookup"><span data-stu-id="7affc-102">Signing Stored Procedures in SQL Server</span></span>
<span data-ttu-id="7affc-103">Saklı yordam bir sertifika veya asimetrik anahtar ile oturum açabilir.</span><span class="sxs-lookup"><span data-stu-id="7affc-103">You can sign a stored procedure with a certificate or an asymmetric key.</span></span> <span data-ttu-id="7affc-104">Sahiplik zincirleme aracılığıyla izinleri devralınan olamaz veya sahiplik zinciri, dinamik SQL gibi bozuk olduğunda bu senaryoları için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="7affc-104">This is designed for scenarios when permissions cannot be inherited through ownership chaining or when the ownership chain is broken, such as dynamic SQL.</span></span> <span data-ttu-id="7affc-105">Sonra sertifikayı kullanıcı saklı yordamı erişmesi nesneleri izin verme sertifikayla eşleştirilmiş bir kullanıcı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7affc-105">You then create a user mapped to the certificate, granting the certificate user permissions on the objects the stored procedure needs to access.</span></span>  
  
 <span data-ttu-id="7affc-106">Saklı yordam çalıştırıldığında, SQL Server çağıran olanlar sertifika kullanıcının izinleriyle birleştirir.</span><span class="sxs-lookup"><span data-stu-id="7affc-106">When the stored procedure is executed, SQL Server combines the permissions of the certificate user with those of the caller.</span></span> <span data-ttu-id="7affc-107">Aksine EXECUTE AS yan TÜMCESİNİ yordamı yürütme bağlamı değişmez.</span><span class="sxs-lookup"><span data-stu-id="7affc-107">Unlike the EXECUTE AS clause, it does not change the execution context of the procedure.</span></span> <span data-ttu-id="7affc-108">Bu dönüş oturum açma yerleşik işlevler ve kullanıcı adları sertifika kullanıcı adı değil arayan adını döndürür.</span><span class="sxs-lookup"><span data-stu-id="7affc-108">Built-in functions that return login and user names return the name of the caller, not the certificate user name.</span></span>  
  
 <span data-ttu-id="7affc-109">Dijital imza imzalayan özel anahtar ile şifrelenmiş veri Özet ' dir.</span><span class="sxs-lookup"><span data-stu-id="7affc-109">A digital signature is a data digest encrypted with the private key of the signer.</span></span> <span data-ttu-id="7affc-110">Özel anahtar dijital imza, taşıyıcı veya sahibi benzersiz olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="7affc-110">The private key ensures that the digital signature is unique to its bearer or owner.</span></span> <span data-ttu-id="7affc-111">Saklı yordamlar, fonksiyon veya tetikleyici imzalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7affc-111">You can sign stored procedures, functions, or triggers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7affc-112">Sunucu düzeyi izinleri vermek için ana veritabanında bir sertifika oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7affc-112">You can create a certificate in the master database to grant server-level permissions.</span></span>  
  
## <a name="creating-certificates"></a><span data-ttu-id="7affc-113">Sertifikaları oluşturma</span><span class="sxs-lookup"><span data-stu-id="7affc-113">Creating Certificates</span></span>  
 <span data-ttu-id="7affc-114">Saklı yordam bir sertifika ile oturum açtığınızda, saklı yordam kod şifrelenmiş karmasını oluşan bir veri özeti özel anahtarı kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7affc-114">When you sign a stored procedure with a certificate, a data digest consisting of the encrypted hash of the stored procedure code is created using the private key.</span></span> <span data-ttu-id="7affc-115">Çalışma zamanında veri Özet ortak anahtarla şifresi ve saklı yordam karma değeriyle karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="7affc-115">At run time, the data digest is decrypted with the public key and compared with the hash value of the stored procedure.</span></span> <span data-ttu-id="7affc-116">Böylece dijital imza artık eşleşir saklı yordamı değiştirme karma değerini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="7affc-116">Modifying the stored procedure invalidates the hash value so that the digital signature no longer matches.</span></span> <span data-ttu-id="7affc-117">Bu saklı yordam kodunu değiştirme Access'ten özel anahtara sahip olmayan birisi önler.</span><span class="sxs-lookup"><span data-stu-id="7affc-117">This prevents someone who does not have access to the private key from changing the stored procedure code.</span></span> <span data-ttu-id="7affc-118">Bu nedenle, yordam her değiştirdiğinizde yeniden oturum açmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7affc-118">Therefore you must re-sign the procedure each time you modify it.</span></span>  
  
 <span data-ttu-id="7affc-119">Bir modül oturum açma dahil edilen dört adım vardır:</span><span class="sxs-lookup"><span data-stu-id="7affc-119">There are four steps involved in signing a module:</span></span>  
  
1.  <span data-ttu-id="7affc-120">Transact-SQL kullanarak bir sertifika oluşturmak `CREATE CERTIFICATE [certificateName]` deyimi.</span><span class="sxs-lookup"><span data-stu-id="7affc-120">Create a certificate using the Transact-SQL `CREATE CERTIFICATE [certificateName]` statement.</span></span> <span data-ttu-id="7affc-121">Bu deyim bir başlangıç ve bitiş tarihi ve bir parola ayarlamak için birkaç seçenek vardır.</span><span class="sxs-lookup"><span data-stu-id="7affc-121">This statement has several options for setting a start and end date and a password.</span></span> <span data-ttu-id="7affc-122">Bir yıl varsayılan sona erme tarihi olan</span><span class="sxs-lookup"><span data-stu-id="7affc-122">The default expiration date is one year</span></span>  
  
2.  <span data-ttu-id="7affc-123">Transact-SQL kullanarak bu sertifikayla ilişkili bir veritabanı kullanıcısı oluşturmalıdır `CREATE USER [userName] FROM CERTIFICATE [certificateName]` deyimi.</span><span class="sxs-lookup"><span data-stu-id="7affc-123">Create a database user associated with that certificate using the Transact-SQL `CREATE USER [userName] FROM CERTIFICATE [certificateName]` statement.</span></span> <span data-ttu-id="7affc-124">Bu kullanıcı yalnızca veritabanında var ve bir oturum ile ilişkili değil.</span><span class="sxs-lookup"><span data-stu-id="7affc-124">This user exists in the database only and is not associated with a login.</span></span>  
  
3.  <span data-ttu-id="7affc-125">Sertifika kullanıcı veritabanı nesneleri üzerinde gerekli izinleri verin.</span><span class="sxs-lookup"><span data-stu-id="7affc-125">Grant the certificate user the required permissions on the database objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7affc-126">Bir sertifika verme deyimi kullanarak iptal izinleri olan bir kullanıcı için izinleri olamaz.</span><span class="sxs-lookup"><span data-stu-id="7affc-126">A certificate cannot grant permissions to a user that has had permissions revoked using the DENY statement.</span></span> <span data-ttu-id="7affc-127">REDDETME her zaman izin ver çağıran sertifika kullanıcıya verilen izinler devralmayı engelleme önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="7affc-127">DENY always takes precedence over GRANT, preventing the caller from inheriting permissions granted to the certificate user.</span></span>  
  
1.  <span data-ttu-id="7affc-128">Yordam Transact-SQL kullanarak sertifika ile oturum `ADD SIGNATURE TO [procedureName] BY CERTIFICATE [certificateName]` deyimi.</span><span class="sxs-lookup"><span data-stu-id="7affc-128">Sign the procedure with the certificate using the Transact-SQL `ADD SIGNATURE TO [procedureName] BY CERTIFICATE [certificateName]` statement.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="7affc-129">Dış Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="7affc-129">External Resources</span></span>  
 <span data-ttu-id="7affc-130">Daha fazla bilgi için aşağıdaki kaynaklara bakın.</span><span class="sxs-lookup"><span data-stu-id="7affc-130">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="7affc-131">Kaynak</span><span class="sxs-lookup"><span data-stu-id="7affc-131">Resource</span></span>|<span data-ttu-id="7affc-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7affc-132">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="7affc-133">[İmzalama Modülü](http://go.microsoft.com/fwlink/?LinkId=98590) SQL Server Çevrimiçi Kitapları'nda</span><span class="sxs-lookup"><span data-stu-id="7affc-133">[Module Signing](http://go.microsoft.com/fwlink/?LinkId=98590) in SQL Server Books Online</span></span>|<span data-ttu-id="7affc-134">İmzalama, bir örnek senaryo ve ilgili Transact-SQL konulara bağlantılar sağlayan modülü açıklar.</span><span class="sxs-lookup"><span data-stu-id="7affc-134">Describes module signing, providing a sample scenario and links to the relevant Transact-SQL topics.</span></span>|  
|<span data-ttu-id="7affc-135">[Saklı yordamlar bir sertifika ile imzalama](http://msdn.microsoft.com/library/bb283630.aspx) SQL Server Çevrimiçi Kitapları'nda</span><span class="sxs-lookup"><span data-stu-id="7affc-135">[Signing Stored Procedures with a Certificate](http://msdn.microsoft.com/library/bb283630.aspx) in SQL Server Books Online</span></span>|<span data-ttu-id="7affc-136">Saklı yordam bir sertifika ile imzalamak için bir öğretici sağlar.</span><span class="sxs-lookup"><span data-stu-id="7affc-136">Provides a tutorial for signing a stored procedure with a certificate.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7affc-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7affc-137">See Also</span></span>  
 [<span data-ttu-id="7affc-138">ADO.NET Uygulamalarının Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="7affc-138">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="7affc-139">SQL Server Güvenliğine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7affc-139">Overview of SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [<span data-ttu-id="7affc-140">SQL Server'da Uygulama Güvenliği Senaryoları</span><span class="sxs-lookup"><span data-stu-id="7affc-140">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [<span data-ttu-id="7affc-141">SQL Server'da Saklı Yordam İzinlerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="7affc-141">Managing Permissions with Stored Procedures in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 [<span data-ttu-id="7affc-142">SQL Server’da Secure Dynamic SQL Yazma</span><span class="sxs-lookup"><span data-stu-id="7affc-142">Writing Secure Dynamic SQL in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 [<span data-ttu-id="7affc-143">SQL Server'da Kimliğe Bürünme İzinlerini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="7affc-143">Customizing Permissions with Impersonation in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)  
 [<span data-ttu-id="7affc-144">Saklı Yordamlarla Verileri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="7affc-144">Modifying Data with Stored Procedures</span></span>](../../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 [<span data-ttu-id="7affc-145">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="7affc-145">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
