---
title: Uygulamalarının Güvenliğini Sağlama
ms.date: 03/30/2017
ms.assetid: 005a1d43-6ee5-471e-ad98-1d30a44d49d5
ms.openlocfilehash: c1bdf4329665e4d29a47c26fb7dba8eb41c1cc3a
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980034"
---
# <a name="securing-adonet-applications"></a><span data-ttu-id="4f4dc-102">ADO.NET Uygulamalarının Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="4f4dc-102">Securing ADO.NET Applications</span></span>
<span data-ttu-id="4f4dc-103">Güvenli bir ADO.NET uygulaması yazmak, Kullanıcı girişini doğrulamamak gibi yaygın kodlama ile kullanmaktan daha fazlasını içerir.</span><span class="sxs-lookup"><span data-stu-id="4f4dc-103">Writing a secure ADO.NET application involves more than avoiding common coding pitfalls such as not validating user input.</span></span> <span data-ttu-id="4f4dc-104">Verilere erişen bir uygulama, bir saldırganın duyarlı verileri almak, değiştirmek veya yok etmek için yararlanabilecek birçok olası hata noktası içerir.</span><span class="sxs-lookup"><span data-stu-id="4f4dc-104">An application that accesses data has many potential points of failure that an attacker can exploit to retrieve, manipulate, or destroy sensitive data.</span></span> <span data-ttu-id="4f4dc-105">Bu nedenle, uygulamanızın tasarım aşamasında, son dağıtım ve devam eden bakımda güvenlik açısından tehdit modellemesi sürecinde güvenliğin tüm yönlerini anlamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="4f4dc-105">It is therefore important to understand all aspects of security, from the process of threat modeling during the design phase of your application, to its eventual deployment and ongoing maintenance.</span></span>  
  
 <span data-ttu-id="4f4dc-106">.NET Framework, veritabanı uygulamalarının güvenliğini sağlamak ve yönetmek için birçok yararlı sınıf, hizmet ve araç sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f4dc-106">The .NET Framework provides many useful classes, services, and tools for securing and administering database applications.</span></span> <span data-ttu-id="4f4dc-107">Ortak dil çalışma zamanı (CLR), kod erişim güvenliği (CAS) ile, yönetilen kodun izinlerini kısıtlamak için kod ile çalışmak üzere tür açısından güvenli bir ortam sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f4dc-107">The common language runtime (CLR) provides a type-safe environment for code to run in, with code access security (CAS) to restrict further the permissions of managed code.</span></span> <span data-ttu-id="4f4dc-108">Aşağıdaki güvenli veri erişimi kodlama uygulamaları, olası bir saldırgan tarafından kullanılabilecek hasar süresini sınırlar.</span><span class="sxs-lookup"><span data-stu-id="4f4dc-108">Following secure data access coding practices limits the damage that can be inflicted by a potential attacker.</span></span>  
  
 <span data-ttu-id="4f4dc-109">Güvenli kod yazma, veritabanları gibi yönetilmeyen kaynaklarla çalışırken kendinden yetenekli güvenlik boşluklarına karşı koruma sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="4f4dc-109">Writing secure code does not guard against self-inflicted security holes when working with unmanaged resources such as databases.</span></span> <span data-ttu-id="4f4dc-110">SQL Server gibi çoğu sunucu veritabanlarının kendi güvenlik sistemleri vardır ve bu, doğru şekilde uygulandığında güvenliği geliştirir.</span><span class="sxs-lookup"><span data-stu-id="4f4dc-110">Most server databases, such as SQL Server, have their own security systems, which enhance security when implemented correctly.</span></span> <span data-ttu-id="4f4dc-111">Ancak, güçlü güvenlik sistemine sahip bir veri kaynağı, uygun bir şekilde yapılandırılmamışsa bir saldırıya karşı çok daha yakın olabilir.</span><span class="sxs-lookup"><span data-stu-id="4f4dc-111">However, even a data source with a robust security system can be victimized in an attack if it is not configured appropriately.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4f4dc-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="4f4dc-112">In This Section</span></span>  
 [<span data-ttu-id="4f4dc-113">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4f4dc-113">Security Overview</span></span>](security-overview.md)  
 <span data-ttu-id="4f4dc-114">Güvenli ADO.NET uygulamaları tasarlamaya yönelik öneriler sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f4dc-114">Provides recommendations for designing secure ADO.NET applications.</span></span>  
  
 [<span data-ttu-id="4f4dc-115">Güvenli Veri Erişimi</span><span class="sxs-lookup"><span data-stu-id="4f4dc-115">Secure Data Access</span></span>](secure-data-access.md)  
 <span data-ttu-id="4f4dc-116">Güvenli bir veri kaynağından verilerle nasıl çalışabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="4f4dc-116">Describes how to work with data from a secured data source.</span></span>  
  
 [<span data-ttu-id="4f4dc-117">Güvenli İstemci Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="4f4dc-117">Secure Client Applications</span></span>](secure-client-applications.md)  
 <span data-ttu-id="4f4dc-118">İstemci uygulamalarına yönelik güvenlik konularını açıklar.</span><span class="sxs-lookup"><span data-stu-id="4f4dc-118">Describes security considerations for client applications.</span></span>  
  
 [<span data-ttu-id="4f4dc-119">Kod Erişimi Güvenliği ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4f4dc-119">Code Access Security and ADO.NET</span></span>](code-access-security.md)  
 <span data-ttu-id="4f4dc-120">CA 'ların, ADO.NET kodunu korumanıza nasıl yardımcı olduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="4f4dc-120">Describes how CAS can help protect ADO.NET code.</span></span> <span data-ttu-id="4f4dc-121">Ayrıca kısmi güvenle nasıl çalışılabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="4f4dc-121">Also discusses how to work with partial trust.</span></span>  
  
 [<span data-ttu-id="4f4dc-122">Gizlilik ve Veri Güvenliği</span><span class="sxs-lookup"><span data-stu-id="4f4dc-122">Privacy and Data Security</span></span>](privacy-and-data-security.md)  
 <span data-ttu-id="4f4dc-123">ADO.NET uygulamaları için şifreleme seçeneklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="4f4dc-123">Describes encryption options for ADO.NET applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4f4dc-124">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="4f4dc-124">Related Sections</span></span>  
 [<span data-ttu-id="4f4dc-125">SQL Server Güvenliği</span><span class="sxs-lookup"><span data-stu-id="4f4dc-125">SQL Server Security</span></span>](./sql/sql-server-security.md)  
 <span data-ttu-id="4f4dc-126">Bir geliştiricinin perspektifinden SQL Server güvenlik özelliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="4f4dc-126">Describes SQL Server security features from a developer's perspective.</span></span>  
  
 [<span data-ttu-id="4f4dc-127">Güvenlik Konuları</span><span class="sxs-lookup"><span data-stu-id="4f4dc-127">Security Considerations</span></span>](./ef/security-considerations.md)  
 <span data-ttu-id="4f4dc-128">Entity Framework uygulamalar için güvenliği açıklar.</span><span class="sxs-lookup"><span data-stu-id="4f4dc-128">Describes security for Entity Framework applications.</span></span>  
  
 [<span data-ttu-id="4f4dc-129">Security</span><span class="sxs-lookup"><span data-stu-id="4f4dc-129">Security</span></span>](../../../standard/security/index.md)  
 <span data-ttu-id="4f4dc-130">.NET 'teki tüm güvenlik yönlerini açıklayan konuların bağlantılarını içerir.</span><span class="sxs-lookup"><span data-stu-id="4f4dc-130">Contains links to topics describing all aspects of security in .NET.</span></span>  
  
 <span data-ttu-id="4f4dc-131">[Güvenlik araçları](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="4f4dc-131">[Security Tools](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))</span></span>  
 <span data-ttu-id="4f4dc-132">Güvenlik ilkesini güvenli hale getirmek ve yönetmek için .NET Framework araçlar.</span><span class="sxs-lookup"><span data-stu-id="4f4dc-132">.NET Framework tools for securing and administering security policy.</span></span>  
  
 <span data-ttu-id="4f4dc-133">[Güvenli uygulamalar oluşturmak için kaynaklar](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4f4dc-133">[Resources for Creating Secure Applications](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))</span></span>  
 <span data-ttu-id="4f4dc-134">Güvenli uygulamalar oluşturmaya yönelik konuların bağlantılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f4dc-134">Provides links to topics for creating secure applications.</span></span>  
  
 [<span data-ttu-id="4f4dc-135">Güvenlik Kaynakçası</span><span class="sxs-lookup"><span data-stu-id="4f4dc-135">Security Bibliography</span></span>](/visualstudio/ide/securing-applications)  
 <span data-ttu-id="4f4dc-136">Çevrimiçi ve yazdırma için kullanılabilir dış kaynaklara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f4dc-136">Provides links to external resources available online and in print.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f4dc-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f4dc-137">See also</span></span>

- [<span data-ttu-id="4f4dc-138">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4f4dc-138">ADO.NET</span></span>](index.md)
- [<span data-ttu-id="4f4dc-139">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4f4dc-139">ADO.NET Overview</span></span>](ado-net-overview.md)
