---
title: ADO.NET Uygulamalarının Güvenliğini Sağlama
ms.date: 03/30/2017
ms.assetid: 005a1d43-6ee5-471e-ad98-1d30a44d49d5
ms.openlocfilehash: c99c56afca475caafe32cca3f50d074fb82e0e00
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73196719"
---
# <a name="securing-adonet-applications"></a><span data-ttu-id="09c33-102">ADO.NET Uygulamalarının Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="09c33-102">Securing ADO.NET Applications</span></span>
<span data-ttu-id="09c33-103">Güvenli bir ADO.NET uygulaması yazmak, Kullanıcı girişini doğrulamamak gibi yaygın kodlama ile kullanmaktan daha fazlasını içerir.</span><span class="sxs-lookup"><span data-stu-id="09c33-103">Writing a secure ADO.NET application involves more than avoiding common coding pitfalls such as not validating user input.</span></span> <span data-ttu-id="09c33-104">Verilere erişen bir uygulama, bir saldırganın duyarlı verileri almak, değiştirmek veya yok etmek için yararlanabilecek birçok olası hata noktası içerir.</span><span class="sxs-lookup"><span data-stu-id="09c33-104">An application that accesses data has many potential points of failure that an attacker can exploit to retrieve, manipulate, or destroy sensitive data.</span></span> <span data-ttu-id="09c33-105">Bu nedenle, uygulamanızın tasarım aşamasında, son dağıtım ve devam eden bakımda güvenlik açısından tehdit modellemesi sürecinde güvenliğin tüm yönlerini anlamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="09c33-105">It is therefore important to understand all aspects of security, from the process of threat modeling during the design phase of your application, to its eventual deployment and ongoing maintenance.</span></span>  
  
 <span data-ttu-id="09c33-106">.NET Framework, veritabanı uygulamalarının güvenliğini sağlamak ve yönetmek için birçok yararlı sınıf, hizmet ve araç sağlar.</span><span class="sxs-lookup"><span data-stu-id="09c33-106">The .NET Framework provides many useful classes, services, and tools for securing and administering database applications.</span></span> <span data-ttu-id="09c33-107">Ortak dil çalışma zamanı (CLR), kod erişim güvenliği (CAS) ile, yönetilen kodun izinlerini kısıtlamak için kod ile çalışmak üzere tür açısından güvenli bir ortam sağlar.</span><span class="sxs-lookup"><span data-stu-id="09c33-107">The common language runtime (CLR) provides a type-safe environment for code to run in, with code access security (CAS) to restrict further the permissions of managed code.</span></span> <span data-ttu-id="09c33-108">Aşağıdaki güvenli veri erişimi kodlama uygulamaları, olası bir saldırgan tarafından kullanılabilecek hasar süresini sınırlar.</span><span class="sxs-lookup"><span data-stu-id="09c33-108">Following secure data access coding practices limits the damage that can be inflicted by a potential attacker.</span></span>  
  
 <span data-ttu-id="09c33-109">Güvenli kod yazma, veritabanları gibi yönetilmeyen kaynaklarla çalışırken kendinden yetenekli güvenlik boşluklarına karşı koruma sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="09c33-109">Writing secure code does not guard against self-inflicted security holes when working with unmanaged resources such as databases.</span></span> <span data-ttu-id="09c33-110">SQL Server gibi çoğu sunucu veritabanlarının kendi güvenlik sistemleri vardır ve bu, doğru şekilde uygulandığında güvenliği geliştirir.</span><span class="sxs-lookup"><span data-stu-id="09c33-110">Most server databases, such as SQL Server, have their own security systems, which enhance security when implemented correctly.</span></span> <span data-ttu-id="09c33-111">Ancak, güçlü güvenlik sistemine sahip bir veri kaynağı, uygun bir şekilde yapılandırılmamışsa bir saldırıya karşı çok daha yakın olabilir.</span><span class="sxs-lookup"><span data-stu-id="09c33-111">However, even a data source with a robust security system can be victimized in an attack if it is not configured appropriately.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="09c33-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="09c33-112">In This Section</span></span>  
 [<span data-ttu-id="09c33-113">Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="09c33-113">Security Overview</span></span>](security-overview.md)  
 <span data-ttu-id="09c33-114">Güvenli ADO.NET uygulamaları tasarlamaya yönelik öneriler sağlar.</span><span class="sxs-lookup"><span data-stu-id="09c33-114">Provides recommendations for designing secure ADO.NET applications.</span></span>  
  
 [<span data-ttu-id="09c33-115">Güvenli Veri Erişimi</span><span class="sxs-lookup"><span data-stu-id="09c33-115">Secure Data Access</span></span>](secure-data-access.md)  
 <span data-ttu-id="09c33-116">Güvenli bir veri kaynağından verilerle nasıl çalışabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="09c33-116">Describes how to work with data from a secured data source.</span></span>  
  
 [<span data-ttu-id="09c33-117">Güvenli İstemci Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="09c33-117">Secure Client Applications</span></span>](secure-client-applications.md)  
 <span data-ttu-id="09c33-118">İstemci uygulamalarına yönelik güvenlik konularını açıklar.</span><span class="sxs-lookup"><span data-stu-id="09c33-118">Describes security considerations for client applications.</span></span>  
  
 [<span data-ttu-id="09c33-119">Kod Erişimi Güvenliği ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="09c33-119">Code Access Security and ADO.NET</span></span>](code-access-security.md)  
 <span data-ttu-id="09c33-120">CA 'ların, ADO.NET kodunu korumanıza nasıl yardımcı olduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="09c33-120">Describes how CAS can help protect ADO.NET code.</span></span> <span data-ttu-id="09c33-121">Ayrıca kısmi güvenle nasıl çalışılabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="09c33-121">Also discusses how to work with partial trust.</span></span>  
  
 [<span data-ttu-id="09c33-122">Gizlilik ve Veri Güvenliği</span><span class="sxs-lookup"><span data-stu-id="09c33-122">Privacy and Data Security</span></span>](privacy-and-data-security.md)  
 <span data-ttu-id="09c33-123">ADO.NET uygulamaları için şifreleme seçeneklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="09c33-123">Describes encryption options for ADO.NET applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="09c33-124">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="09c33-124">Related Sections</span></span>  
 [<span data-ttu-id="09c33-125">SQL Server Güvenliği</span><span class="sxs-lookup"><span data-stu-id="09c33-125">SQL Server Security</span></span>](./sql/sql-server-security.md)  
 <span data-ttu-id="09c33-126">Bir geliştiricinin perspektifinden SQL Server güvenlik özelliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="09c33-126">Describes SQL Server security features from a developer's perspective.</span></span>  
  
 [<span data-ttu-id="09c33-127">Güvenlik Konuları</span><span class="sxs-lookup"><span data-stu-id="09c33-127">Security Considerations</span></span>](./ef/security-considerations.md)  
 <span data-ttu-id="09c33-128">Entity Framework uygulamalar için güvenliği açıklar.</span><span class="sxs-lookup"><span data-stu-id="09c33-128">Describes security for Entity Framework applications.</span></span>  
  
 [<span data-ttu-id="09c33-129">Security</span><span class="sxs-lookup"><span data-stu-id="09c33-129">Security</span></span>](../../../standard/security/index.md)  
 <span data-ttu-id="09c33-130">.NET 'teki tüm güvenlik yönlerini açıklayan konuların bağlantılarını içerir.</span><span class="sxs-lookup"><span data-stu-id="09c33-130">Contains links to topics describing all aspects of security in .NET.</span></span>  
  
 <span data-ttu-id="09c33-131">[Güvenlik araçları](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="09c33-131">[Security Tools](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))</span></span>  
 <span data-ttu-id="09c33-132">Güvenlik ilkesini güvenli hale getirmek ve yönetmek için .NET Framework araçlar.</span><span class="sxs-lookup"><span data-stu-id="09c33-132">.NET Framework tools for securing and administering security policy.</span></span>  
  
 <span data-ttu-id="09c33-133">[Güvenli uygulamalar oluşturmak için kaynaklar](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="09c33-133">[Resources for Creating Secure Applications](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))</span></span>  
 <span data-ttu-id="09c33-134">Güvenli uygulamalar oluşturmaya yönelik konuların bağlantılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="09c33-134">Provides links to topics for creating secure applications.</span></span>  
  
 [<span data-ttu-id="09c33-135">Güvenlik Kaynakçası</span><span class="sxs-lookup"><span data-stu-id="09c33-135">Security Bibliography</span></span>](/visualstudio/ide/securing-applications)  
 <span data-ttu-id="09c33-136">Çevrimiçi ve yazdırma için kullanılabilir dış kaynaklara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="09c33-136">Provides links to external resources available online and in print.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09c33-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="09c33-137">See also</span></span>

- [<span data-ttu-id="09c33-138">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="09c33-138">ADO.NET</span></span>](index.md)
- [<span data-ttu-id="09c33-139">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="09c33-139">ADO.NET Overview</span></span>](ado-net-overview.md)
