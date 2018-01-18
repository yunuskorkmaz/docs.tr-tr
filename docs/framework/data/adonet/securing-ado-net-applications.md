---
title: "ADO.NET uygulamalarının güvenliğini sağlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 005a1d43-6ee5-471e-ad98-1d30a44d49d5
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 065a3bcd64500323de7bc37c5896b13acb459fb1
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="securing-adonet-applications"></a><span data-ttu-id="55693-102">ADO.NET uygulamalarının güvenliğini sağlama</span><span class="sxs-lookup"><span data-stu-id="55693-102">Securing ADO.NET Applications</span></span>
<span data-ttu-id="55693-103">Güvenli bir ADO.NET uygulama yazma birden fazla kullanıcı girişini doğrulama değil gibi ortak kodlama Tuzaklar önleme içerir.</span><span class="sxs-lookup"><span data-stu-id="55693-103">Writing a secure ADO.NET application involves more than avoiding common coding pitfalls such as not validating user input.</span></span> <span data-ttu-id="55693-104">Verilere erişen bir uygulama birçok olası bir saldırganın alınamıyor, değiştirmek veya hassas verilere zarar yararlanabilir hata noktalarını sahiptir.</span><span class="sxs-lookup"><span data-stu-id="55693-104">An application that accesses data has many potential points of failure that an attacker can exploit to retrieve, manipulate, or destroy sensitive data.</span></span> <span data-ttu-id="55693-105">Bu nedenle, güvenlik, uygulamanızın son dağıtım ve devam eden bakım tasarım aşamasında modelleme tehdit işleminden tüm yönlerini anlamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="55693-105">It is therefore important to understand all aspects of security, from the process of threat modeling during the design phase of your application, to its eventual deployment and ongoing maintenance.</span></span>  
  
 <span data-ttu-id="55693-106">.NET Framework pek çok yararlı sınıfları, hizmetleri ve güvenli hale getirme ve veritabanı uygulamaları yönetmek için araçlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="55693-106">The .NET Framework provides many useful classes, services, and tools for securing and administering database applications.</span></span> <span data-ttu-id="55693-107">Ortak dil çalışma zamanı (CLR), daha fazla yönetilen kod izinlerini kısıtlamak için kod erişimi güvenliği ile (CA) çalıştırmak için kod için bir tür kullanımı uyumlu ortamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="55693-107">The common language runtime (CLR) provides a type-safe environment for code to run in, with code access security (CAS) to restrict further the permissions of managed code.</span></span> <span data-ttu-id="55693-108">Güvenli veri yöntemler kodlama erişim olası bir saldırgan tarafından şiddet hasarı kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="55693-108">Following secure data access coding practices limits the damage that can be inflicted by a potential attacker.</span></span>  
  
 <span data-ttu-id="55693-109">Güvenli kod yazmaya karşı kendi kendine inflicted güvenlik açıklarını veritabanları gibi yönetilmeyen kaynaklar ile çalışırken koruma sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="55693-109">Writing secure code does not guard against self-inflicted security holes when working with unmanaged resources such as databases.</span></span> <span data-ttu-id="55693-110">SQL Server gibi birçok server veritabanlarını düzgün şekilde uygulandığında güvenliğini kendi güvenlik sistemlerinde vardır.</span><span class="sxs-lookup"><span data-stu-id="55693-110">Most server databases, such as SQL Server, have their own security systems, which enhance security when implemented correctly.</span></span> <span data-ttu-id="55693-111">Ancak, uygun şekilde yapılandırılmamışsa, daha güçlü bir güvenlik sistemi ile bir veri kaynağı bir saldırı kurban.</span><span class="sxs-lookup"><span data-stu-id="55693-111">However, even a data source with a robust security system can be victimized in an attack if it is not configured appropriately.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="55693-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="55693-112">In This Section</span></span>  
 [<span data-ttu-id="55693-113">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="55693-113">Security Overview</span></span>](../../../../docs/framework/data/adonet/security-overview.md)  
 <span data-ttu-id="55693-114">Güvenli ADO.NET uygulamalar tasarlama için öneriler sağlar.</span><span class="sxs-lookup"><span data-stu-id="55693-114">Provides recommendations for designing secure ADO.NET applications.</span></span>  
  
 [<span data-ttu-id="55693-115">Güvenli Veri Erişimi</span><span class="sxs-lookup"><span data-stu-id="55693-115">Secure Data Access</span></span>](../../../../docs/framework/data/adonet/secure-data-access.md)  
 <span data-ttu-id="55693-116">Güvenli veri kaynağı ile nasıl çalışılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="55693-116">Describes how to work with data from a secured data source.</span></span>  
  
 [<span data-ttu-id="55693-117">Güvenli İstemci Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="55693-117">Secure Client Applications</span></span>](../../../../docs/framework/data/adonet/secure-client-applications.md)  
 <span data-ttu-id="55693-118">İstemci uygulamaları için güvenlik konuları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="55693-118">Describes security considerations for client applications.</span></span>  
  
 [<span data-ttu-id="55693-119">Kod Erişimi Güvenliği ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="55693-119">Code Access Security and ADO.NET</span></span>](../../../../docs/framework/data/adonet/code-access-security.md)  
 <span data-ttu-id="55693-120">CA'ları ADO.NET kodu korumaya nasıl yardımcı olabileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="55693-120">Describes how CAS can help protect ADO.NET code.</span></span> <span data-ttu-id="55693-121">Ayrıca kısmi güven ile çalışma konusunda anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="55693-121">Also discusses how to work with partial trust.</span></span>  
  
 [<span data-ttu-id="55693-122">Gizlilik ve Veri Güvenliği</span><span class="sxs-lookup"><span data-stu-id="55693-122">Privacy and Data Security</span></span>](../../../../docs/framework/data/adonet/privacy-and-data-security.md)  
 <span data-ttu-id="55693-123">ADO.NET uygulamalar için şifreleme seçenekleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="55693-123">Describes encryption options for ADO.NET applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="55693-124">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="55693-124">Related Sections</span></span>  
 [<span data-ttu-id="55693-125">SQL Server Güvenliği</span><span class="sxs-lookup"><span data-stu-id="55693-125">SQL Server Security</span></span>](../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 <span data-ttu-id="55693-126">SQL Server güvenlik özellikleri geliştiricinin açısından açıklar.</span><span class="sxs-lookup"><span data-stu-id="55693-126">Describes SQL Server security features from a developer's perspective.</span></span>  
  
 [<span data-ttu-id="55693-127">Güvenlik Konuları</span><span class="sxs-lookup"><span data-stu-id="55693-127">Security Considerations</span></span>](../../../../docs/framework/data/adonet/ef/security-considerations.md)  
 <span data-ttu-id="55693-128">Entity Framework uygulamaları için güvenliği açıklar.</span><span class="sxs-lookup"><span data-stu-id="55693-128">Describes security for Entity Framework applications.</span></span>  
  
 [<span data-ttu-id="55693-129">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="55693-129">Security</span></span>](../../../../docs/standard/security/index.md)  
 <span data-ttu-id="55693-130">.NET Framework güvenliği tüm yönleriyle açıklayan konulara bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="55693-130">Contains links to topics describing all aspects of security in the .NET Framework.</span></span>  
  
 [<span data-ttu-id="55693-131">Güvenlik araçları</span><span class="sxs-lookup"><span data-stu-id="55693-131">Security Tools</span></span>](http://msdn.microsoft.com/en-us/2a3eb98a-2de6-4fba-b41c-01a74d354c11)  
 <span data-ttu-id="55693-132">Güvenlik İlkesi'ni yönetme ve güvenliğini sağlamak için .NET framework Araçları'nı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="55693-132">.NET Framework tools for securing and administering security policy.</span></span>  
  
 [<span data-ttu-id="55693-133">Güvenli uygulamalar oluşturmak için kaynaklar</span><span class="sxs-lookup"><span data-stu-id="55693-133">Resources for Creating Secure Applications</span></span>](http://msdn.microsoft.com/en-us/0ebf5f69-76f2-498a-a2df-83cf3443e132)  
 <span data-ttu-id="55693-134">Güvenli uygulamalar oluşturmak için konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="55693-134">Provides links to topics for creating secure applications.</span></span>  
  
 [<span data-ttu-id="55693-135">Güvenlik Kaynakçası</span><span class="sxs-lookup"><span data-stu-id="55693-135">Security Bibliography</span></span>](/visualstudio/ide/security-bibliography)  
 <span data-ttu-id="55693-136">Çevrimiçi ve yazdırma kullanılabilir dış kaynaklara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="55693-136">Provides links to external resources available online and in print.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55693-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="55693-137">See Also</span></span>  
 [<span data-ttu-id="55693-138">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="55693-138">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)  
 [<span data-ttu-id="55693-139">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="55693-139">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
