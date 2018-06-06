---
title: ADO.NET uygulamalarının güvenliğini sağlama
ms.date: 03/30/2017
ms.assetid: 005a1d43-6ee5-471e-ad98-1d30a44d49d5
ms.openlocfilehash: efe25082b4e4de9170179ebeff6a1dca8f67446c
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34728608"
---
# <a name="securing-adonet-applications"></a><span data-ttu-id="0734f-102">ADO.NET uygulamalarının güvenliğini sağlama</span><span class="sxs-lookup"><span data-stu-id="0734f-102">Securing ADO.NET Applications</span></span>
<span data-ttu-id="0734f-103">Güvenli bir ADO.NET uygulama yazma birden fazla kullanıcı girişini doğrulama değil gibi ortak kodlama Tuzaklar önleme içerir.</span><span class="sxs-lookup"><span data-stu-id="0734f-103">Writing a secure ADO.NET application involves more than avoiding common coding pitfalls such as not validating user input.</span></span> <span data-ttu-id="0734f-104">Verilere erişen bir uygulama birçok olası bir saldırganın alınamıyor, değiştirmek veya hassas verilere zarar yararlanabilir hata noktalarını sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0734f-104">An application that accesses data has many potential points of failure that an attacker can exploit to retrieve, manipulate, or destroy sensitive data.</span></span> <span data-ttu-id="0734f-105">Bu nedenle, güvenlik, uygulamanızın son dağıtım ve devam eden bakım tasarım aşamasında modelleme tehdit işleminden tüm yönlerini anlamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="0734f-105">It is therefore important to understand all aspects of security, from the process of threat modeling during the design phase of your application, to its eventual deployment and ongoing maintenance.</span></span>  
  
 <span data-ttu-id="0734f-106">.NET Framework pek çok yararlı sınıfları, hizmetleri ve güvenli hale getirme ve veritabanı uygulamaları yönetmek için araçlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="0734f-106">The .NET Framework provides many useful classes, services, and tools for securing and administering database applications.</span></span> <span data-ttu-id="0734f-107">Ortak dil çalışma zamanı (CLR), daha fazla yönetilen kod izinlerini kısıtlamak için kod erişimi güvenliği ile (CA) çalıştırmak için kod için bir tür kullanımı uyumlu ortamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="0734f-107">The common language runtime (CLR) provides a type-safe environment for code to run in, with code access security (CAS) to restrict further the permissions of managed code.</span></span> <span data-ttu-id="0734f-108">Güvenli veri yöntemler kodlama erişim olası bir saldırgan tarafından şiddet hasarı kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="0734f-108">Following secure data access coding practices limits the damage that can be inflicted by a potential attacker.</span></span>  
  
 <span data-ttu-id="0734f-109">Güvenli kod yazmaya karşı kendi kendine inflicted güvenlik açıklarını veritabanları gibi yönetilmeyen kaynaklar ile çalışırken koruma sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="0734f-109">Writing secure code does not guard against self-inflicted security holes when working with unmanaged resources such as databases.</span></span> <span data-ttu-id="0734f-110">SQL Server gibi birçok server veritabanlarını düzgün şekilde uygulandığında güvenliğini kendi güvenlik sistemlerinde vardır.</span><span class="sxs-lookup"><span data-stu-id="0734f-110">Most server databases, such as SQL Server, have their own security systems, which enhance security when implemented correctly.</span></span> <span data-ttu-id="0734f-111">Ancak, uygun şekilde yapılandırılmamışsa, daha güçlü bir güvenlik sistemi ile bir veri kaynağı bir saldırı kurban.</span><span class="sxs-lookup"><span data-stu-id="0734f-111">However, even a data source with a robust security system can be victimized in an attack if it is not configured appropriately.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0734f-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="0734f-112">In This Section</span></span>  
 [<span data-ttu-id="0734f-113">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0734f-113">Security Overview</span></span>](../../../../docs/framework/data/adonet/security-overview.md)  
 <span data-ttu-id="0734f-114">Güvenli ADO.NET uygulamalar tasarlama için öneriler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0734f-114">Provides recommendations for designing secure ADO.NET applications.</span></span>  
  
 [<span data-ttu-id="0734f-115">Güvenli Veri Erişimi</span><span class="sxs-lookup"><span data-stu-id="0734f-115">Secure Data Access</span></span>](../../../../docs/framework/data/adonet/secure-data-access.md)  
 <span data-ttu-id="0734f-116">Güvenli veri kaynağı ile nasıl çalışılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="0734f-116">Describes how to work with data from a secured data source.</span></span>  
  
 [<span data-ttu-id="0734f-117">Güvenli İstemci Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="0734f-117">Secure Client Applications</span></span>](../../../../docs/framework/data/adonet/secure-client-applications.md)  
 <span data-ttu-id="0734f-118">İstemci uygulamaları için güvenlik konuları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0734f-118">Describes security considerations for client applications.</span></span>  
  
 [<span data-ttu-id="0734f-119">Kod Erişimi Güvenliği ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0734f-119">Code Access Security and ADO.NET</span></span>](../../../../docs/framework/data/adonet/code-access-security.md)  
 <span data-ttu-id="0734f-120">CA'ları ADO.NET kodu korumaya nasıl yardımcı olabileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="0734f-120">Describes how CAS can help protect ADO.NET code.</span></span> <span data-ttu-id="0734f-121">Ayrıca kısmi güven ile çalışma konusunda anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0734f-121">Also discusses how to work with partial trust.</span></span>  
  
 [<span data-ttu-id="0734f-122">Gizlilik ve Veri Güvenliği</span><span class="sxs-lookup"><span data-stu-id="0734f-122">Privacy and Data Security</span></span>](../../../../docs/framework/data/adonet/privacy-and-data-security.md)  
 <span data-ttu-id="0734f-123">ADO.NET uygulamalar için şifreleme seçenekleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="0734f-123">Describes encryption options for ADO.NET applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0734f-124">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="0734f-124">Related Sections</span></span>  
 [<span data-ttu-id="0734f-125">SQL Server Güvenliği</span><span class="sxs-lookup"><span data-stu-id="0734f-125">SQL Server Security</span></span>](../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 <span data-ttu-id="0734f-126">SQL Server güvenlik özellikleri geliştiricinin açısından açıklar.</span><span class="sxs-lookup"><span data-stu-id="0734f-126">Describes SQL Server security features from a developer's perspective.</span></span>  
  
 [<span data-ttu-id="0734f-127">Güvenlik Konuları</span><span class="sxs-lookup"><span data-stu-id="0734f-127">Security Considerations</span></span>](../../../../docs/framework/data/adonet/ef/security-considerations.md)  
 <span data-ttu-id="0734f-128">Entity Framework uygulamaları için güvenliği açıklar.</span><span class="sxs-lookup"><span data-stu-id="0734f-128">Describes security for Entity Framework applications.</span></span>  
  
 [<span data-ttu-id="0734f-129">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="0734f-129">Security</span></span>](../../../../docs/standard/security/index.md)  
 <span data-ttu-id="0734f-130">.NET ve güvenlik tüm yönlerini açıklayan konulara bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="0734f-130">Contains links to topics describing all aspects of security in .NET.</span></span>  
  
 [<span data-ttu-id="0734f-131">Güvenlik araçları</span><span class="sxs-lookup"><span data-stu-id="0734f-131">Security Tools</span></span>](http://msdn.microsoft.com/library/2a3eb98a-2de6-4fba-b41c-01a74d354c11)  
 <span data-ttu-id="0734f-132">Güvenlik İlkesi'ni yönetme ve güvenliğini sağlamak için .NET framework Araçları'nı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="0734f-132">.NET Framework tools for securing and administering security policy.</span></span>  
  
 [<span data-ttu-id="0734f-133">Güvenli uygulamalar oluşturmak için kaynaklar</span><span class="sxs-lookup"><span data-stu-id="0734f-133">Resources for Creating Secure Applications</span></span>](http://msdn.microsoft.com/library/0ebf5f69-76f2-498a-a2df-83cf3443e132)  
 <span data-ttu-id="0734f-134">Güvenli uygulamalar oluşturmak için konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="0734f-134">Provides links to topics for creating secure applications.</span></span>  
  
 [<span data-ttu-id="0734f-135">Güvenlik Kaynakçası</span><span class="sxs-lookup"><span data-stu-id="0734f-135">Security Bibliography</span></span>](/visualstudio/ide/security-bibliography)  
 <span data-ttu-id="0734f-136">Çevrimiçi ve yazdırma kullanılabilir dış kaynaklara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="0734f-136">Provides links to external resources available online and in print.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0734f-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0734f-137">See Also</span></span>  
 [<span data-ttu-id="0734f-138">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0734f-138">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)  
 [<span data-ttu-id="0734f-139">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="0734f-139">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
