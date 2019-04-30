---
title: ADO.NET Uygulamalarının Güvenliğini Sağlama
ms.date: 03/30/2017
ms.assetid: 005a1d43-6ee5-471e-ad98-1d30a44d49d5
ms.openlocfilehash: 32d3de15242aaf9cfacd9371289a5a0a675f884b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61664200"
---
# <a name="securing-adonet-applications"></a><span data-ttu-id="a452f-102">ADO.NET Uygulamalarının Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="a452f-102">Securing ADO.NET Applications</span></span>
<span data-ttu-id="a452f-103">Güvenli bir ADO.NET uygulama yazma birden fazla kullanıcı girişini doğrulama değil gibi kodlama yaygın görülen tehlikeleri önleme içerir.</span><span class="sxs-lookup"><span data-stu-id="a452f-103">Writing a secure ADO.NET application involves more than avoiding common coding pitfalls such as not validating user input.</span></span> <span data-ttu-id="a452f-104">Verilere erişen bir uygulamanın birçok olası bir saldırganın almak, işlemek veya hassas verileri yok yararlanabilir hata noktaları vardır.</span><span class="sxs-lookup"><span data-stu-id="a452f-104">An application that accesses data has many potential points of failure that an attacker can exploit to retrieve, manipulate, or destroy sensitive data.</span></span> <span data-ttu-id="a452f-105">Bu nedenle, güvenlik, tehdit modelleme tasarım aşamasında uygulamanızın son dağıtım ve sürekli bakım işlemi tüm yönleri anlamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="a452f-105">It is therefore important to understand all aspects of security, from the process of threat modeling during the design phase of your application, to its eventual deployment and ongoing maintenance.</span></span>  
  
 <span data-ttu-id="a452f-106">.NET Framework, pek çok yararlı sınıfları, hizmetleri ve güvenli hale getirme ve veritabanı uygulamaları yönetmek için araçlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="a452f-106">The .NET Framework provides many useful classes, services, and tools for securing and administering database applications.</span></span> <span data-ttu-id="a452f-107">Ortak dil çalışma zamanı (CLR), daha fazla yönetilen kod izinlerini kısıtlamak için kod erişimi güvenliği ile (CA) çalıştırmak için kod için bir tür kullanımı uyumlu ortamı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a452f-107">The common language runtime (CLR) provides a type-safe environment for code to run in, with code access security (CAS) to restrict further the permissions of managed code.</span></span> <span data-ttu-id="a452f-108">Güvenli veri erişimi kodlama uygulamaları, olası bir saldırgan tarafından şiddet hasarı kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="a452f-108">Following secure data access coding practices limits the damage that can be inflicted by a potential attacker.</span></span>  
  
 <span data-ttu-id="a452f-109">Güvenli kod yazma kendini güvenlik açıkları karşı veritabanları gibi yönetilmeyen kaynaklar ile çalışırken koruma sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="a452f-109">Writing secure code does not guard against self-inflicted security holes when working with unmanaged resources such as databases.</span></span> <span data-ttu-id="a452f-110">Çoğu server veritabanları, SQL Server gibi doğru bir şekilde uygulandığında güvenliğini kendi güvenlik sistemlerinde vardır.</span><span class="sxs-lookup"><span data-stu-id="a452f-110">Most server databases, such as SQL Server, have their own security systems, which enhance security when implemented correctly.</span></span> <span data-ttu-id="a452f-111">Ancak, uygun şekilde yapılandırılmamışsa, sağlam güvenlik sistemi bile veri kaynağıyla bir saldırı kurban.</span><span class="sxs-lookup"><span data-stu-id="a452f-111">However, even a data source with a robust security system can be victimized in an attack if it is not configured appropriately.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a452f-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="a452f-112">In This Section</span></span>  
 [<span data-ttu-id="a452f-113">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a452f-113">Security Overview</span></span>](../../../../docs/framework/data/adonet/security-overview.md)  
 <span data-ttu-id="a452f-114">ADO.NET güvenli uygulamalar tasarlamaya yönelik öneriler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a452f-114">Provides recommendations for designing secure ADO.NET applications.</span></span>  
  
 [<span data-ttu-id="a452f-115">Güvenli Veri Erişimi</span><span class="sxs-lookup"><span data-stu-id="a452f-115">Secure Data Access</span></span>](../../../../docs/framework/data/adonet/secure-data-access.md)  
 <span data-ttu-id="a452f-116">Güvenli veri kaynağı ile nasıl çalışılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="a452f-116">Describes how to work with data from a secured data source.</span></span>  
  
 [<span data-ttu-id="a452f-117">Güvenli İstemci Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="a452f-117">Secure Client Applications</span></span>](../../../../docs/framework/data/adonet/secure-client-applications.md)  
 <span data-ttu-id="a452f-118">İstemci uygulamaları için güvenlik konuları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a452f-118">Describes security considerations for client applications.</span></span>  
  
 [<span data-ttu-id="a452f-119">Kod Erişimi Güvenliği ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a452f-119">Code Access Security and ADO.NET</span></span>](../../../../docs/framework/data/adonet/code-access-security.md)  
 <span data-ttu-id="a452f-120">CAS ADO.NET kod korunmasına nasıl yardımcı olabileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="a452f-120">Describes how CAS can help protect ADO.NET code.</span></span> <span data-ttu-id="a452f-121">Ayrıca, kısmi güven ile nasıl çalışılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a452f-121">Also discusses how to work with partial trust.</span></span>  
  
 [<span data-ttu-id="a452f-122">Gizlilik ve Veri Güvenliği</span><span class="sxs-lookup"><span data-stu-id="a452f-122">Privacy and Data Security</span></span>](../../../../docs/framework/data/adonet/privacy-and-data-security.md)  
 <span data-ttu-id="a452f-123">ADO.NET uygulamalarının şifreleme seçenekleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="a452f-123">Describes encryption options for ADO.NET applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a452f-124">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="a452f-124">Related Sections</span></span>  
 [<span data-ttu-id="a452f-125">SQL Server Güvenliği</span><span class="sxs-lookup"><span data-stu-id="a452f-125">SQL Server Security</span></span>](../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 <span data-ttu-id="a452f-126">Bir geliştiricinin bakış açısından SQL Server güvenlik özellikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="a452f-126">Describes SQL Server security features from a developer's perspective.</span></span>  
  
 [<span data-ttu-id="a452f-127">Güvenlik Konuları</span><span class="sxs-lookup"><span data-stu-id="a452f-127">Security Considerations</span></span>](../../../../docs/framework/data/adonet/ef/security-considerations.md)  
 <span data-ttu-id="a452f-128">Entity Framework uygulamaları için güvenliği açıklar.</span><span class="sxs-lookup"><span data-stu-id="a452f-128">Describes security for Entity Framework applications.</span></span>  
  
 [<span data-ttu-id="a452f-129">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="a452f-129">Security</span></span>](../../../../docs/standard/security/index.md)  
 <span data-ttu-id="a452f-130">. NET'te güvenliği tüm yönleriyle açıklayan konulara bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="a452f-130">Contains links to topics describing all aspects of security in .NET.</span></span>  
  
 <span data-ttu-id="a452f-131">[Güvenlik araçları](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="a452f-131">[Security Tools](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))</span></span>  
 <span data-ttu-id="a452f-132">Güvenlik İlkesi'ni yönetme ve güvenliğini sağlamak için .NET framework Araçları'nı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="a452f-132">.NET Framework tools for securing and administering security policy.</span></span>  
  
 <span data-ttu-id="a452f-133">[Güvenli uygulamalar oluşturmak için kaynaklar](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a452f-133">[Resources for Creating Secure Applications](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))</span></span>  
 <span data-ttu-id="a452f-134">Güvenli uygulamalar oluşturmak için konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="a452f-134">Provides links to topics for creating secure applications.</span></span>  
  
 [<span data-ttu-id="a452f-135">Güvenlik Kaynakçası</span><span class="sxs-lookup"><span data-stu-id="a452f-135">Security Bibliography</span></span>](/visualstudio/ide/security-bibliography)  
 <span data-ttu-id="a452f-136">Çevrimiçi ve yazdırma mevcut dış kaynaklara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="a452f-136">Provides links to external resources available online and in print.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a452f-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a452f-137">See also</span></span>

- [<span data-ttu-id="a452f-138">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a452f-138">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)
- [<span data-ttu-id="a452f-139">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="a452f-139">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
