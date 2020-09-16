---
title: Uygulamalarının Güvenliğini Sağlama
ms.date: 03/30/2017
ms.assetid: 005a1d43-6ee5-471e-ad98-1d30a44d49d5
ms.openlocfilehash: af184f64b43c2d3dc39f8c0add08940d3b002c24
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550761"
---
# <a name="securing-adonet-applications"></a><span data-ttu-id="ac036-102">ADO.NET uygulamalarının güvenliğini sağlama</span><span class="sxs-lookup"><span data-stu-id="ac036-102">Securing ADO.NET applications</span></span>

<span data-ttu-id="ac036-103">Güvenli bir ADO.NET uygulaması yazmak, Kullanıcı girişini doğrulamamak gibi yaygın kodlama ile kullanmaktan daha fazlasını içerir.</span><span class="sxs-lookup"><span data-stu-id="ac036-103">Writing a secure ADO.NET application involves more than avoiding common coding pitfalls such as not validating user input.</span></span> <span data-ttu-id="ac036-104">Verilere erişen bir uygulama, bir saldırganın duyarlı verileri almak, değiştirmek veya yok etmek için yararlanabilecek birçok olası hata noktası içerir.</span><span class="sxs-lookup"><span data-stu-id="ac036-104">An application that accesses data has many potential points of failure that an attacker can exploit to retrieve, manipulate, or destroy sensitive data.</span></span> <span data-ttu-id="ac036-105">Bu nedenle, uygulamanızın tasarım aşamasında, son dağıtım ve devam eden bakımda güvenlik açısından tehdit modellemesi sürecinde güvenliğin tüm yönlerini anlamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="ac036-105">It is therefore important to understand all aspects of security, from the process of threat modeling during the design phase of your application, to its eventual deployment and ongoing maintenance.</span></span>  
  
<span data-ttu-id="ac036-106">.NET Framework, veritabanı uygulamalarının güvenliğini sağlamak ve yönetmek için birçok yararlı sınıf, hizmet ve araç sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac036-106">The .NET Framework provides many useful classes, services, and tools for securing and administering database applications.</span></span> <span data-ttu-id="ac036-107">Ortak dil çalışma zamanı (CLR), kod erişim güvenliği (CAS) ile, yönetilen kodun izinlerini kısıtlamak için kod ile çalışmak üzere tür açısından güvenli bir ortam sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac036-107">The common language runtime (CLR) provides a type-safe environment for code to run in, with code access security (CAS) to restrict further the permissions of managed code.</span></span> <span data-ttu-id="ac036-108">Aşağıdaki güvenli veri erişimi kodlama uygulamaları, olası bir saldırgan tarafından kullanılabilecek hasar süresini sınırlar.</span><span class="sxs-lookup"><span data-stu-id="ac036-108">Following secure data access coding practices limits the damage that can be inflicted by a potential attacker.</span></span>  
  
<span data-ttu-id="ac036-109">Güvenli kod yazma, veritabanları gibi yönetilmeyen kaynaklarla çalışırken kendinden yetenekli güvenlik boşluklarına karşı koruma sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="ac036-109">Writing secure code does not guard against self-inflicted security holes when working with unmanaged resources such as databases.</span></span> <span data-ttu-id="ac036-110">SQL Server gibi çoğu sunucu veritabanlarının kendi güvenlik sistemleri vardır ve bu, doğru şekilde uygulandığında güvenliği geliştirir.</span><span class="sxs-lookup"><span data-stu-id="ac036-110">Most server databases, such as SQL Server, have their own security systems, which enhance security when implemented correctly.</span></span> <span data-ttu-id="ac036-111">Ancak, güçlü güvenlik sistemine sahip bir veri kaynağı, uygun bir şekilde yapılandırılmamışsa bir saldırıya karşı çok daha yakın olabilir.</span><span class="sxs-lookup"><span data-stu-id="ac036-111">However, even a data source with a robust security system can be victimized in an attack if it is not configured appropriately.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ac036-112">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="ac036-112">In this section</span></span>

 [<span data-ttu-id="ac036-113">Güvenliğe genel bakış</span><span class="sxs-lookup"><span data-stu-id="ac036-113">Security Overview</span></span>](security-overview.md)  
 <span data-ttu-id="ac036-114">Güvenli ADO.NET uygulamaları tasarlamaya yönelik öneriler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac036-114">Provides recommendations for designing secure ADO.NET applications.</span></span>  
  
 [<span data-ttu-id="ac036-115">Güvenli Veri Erişimi</span><span class="sxs-lookup"><span data-stu-id="ac036-115">Secure Data Access</span></span>](secure-data-access.md)  
 <span data-ttu-id="ac036-116">Güvenli bir veri kaynağından verilerle nasıl çalışabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="ac036-116">Describes how to work with data from a secured data source.</span></span>  
  
 [<span data-ttu-id="ac036-117">Güvenli İstemci Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="ac036-117">Secure Client Applications</span></span>](secure-client-applications.md)  
 <span data-ttu-id="ac036-118">İstemci uygulamalarına yönelik güvenlik konularını açıklar.</span><span class="sxs-lookup"><span data-stu-id="ac036-118">Describes security considerations for client applications.</span></span>  
  
 [<span data-ttu-id="ac036-119">Kod Erişimi Güvenliği ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ac036-119">Code Access Security and ADO.NET</span></span>](code-access-security.md)  
 <span data-ttu-id="ac036-120">CA 'ların, ADO.NET kodunu korumanıza nasıl yardımcı olduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="ac036-120">Describes how CAS can help protect ADO.NET code.</span></span> <span data-ttu-id="ac036-121">Ayrıca kısmi güvenle nasıl çalışılabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="ac036-121">Also discusses how to work with partial trust.</span></span>  
  
 [<span data-ttu-id="ac036-122">Gizlilik ve Veri Güvenliği</span><span class="sxs-lookup"><span data-stu-id="ac036-122">Privacy and Data Security</span></span>](privacy-and-data-security.md)  
 <span data-ttu-id="ac036-123">ADO.NET uygulamaları için şifreleme seçeneklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="ac036-123">Describes encryption options for ADO.NET applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ac036-124">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="ac036-124">Related sections</span></span>

 [<span data-ttu-id="ac036-125">Veri kümesi ve DataTable Güvenlik Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ac036-125">DataSet and DataTable security guidance</span></span>](dataset-datatable-dataview/security-guidance.md)  
 <span data-ttu-id="ac036-126">Ve için Güvenlik Kılavuzu <xref:System.Data.DataSet> sağlar <xref:System.Data.DataTable> .</span><span class="sxs-lookup"><span data-stu-id="ac036-126">Provides security guidance for <xref:System.Data.DataSet> and <xref:System.Data.DataTable>.</span></span>

 [<span data-ttu-id="ac036-127">SQL Server Güvenliği</span><span class="sxs-lookup"><span data-stu-id="ac036-127">SQL Server Security</span></span>](./sql/sql-server-security.md)  
 <span data-ttu-id="ac036-128">Bir geliştiricinin perspektifinden SQL Server güvenlik özelliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="ac036-128">Describes SQL Server security features from a developer's perspective.</span></span>  
  
 [<span data-ttu-id="ac036-129">Güvenlik konuları</span><span class="sxs-lookup"><span data-stu-id="ac036-129">Security Considerations</span></span>](./ef/security-considerations.md)  
 <span data-ttu-id="ac036-130">Entity Framework uygulamalar için güvenliği açıklar.</span><span class="sxs-lookup"><span data-stu-id="ac036-130">Describes security for Entity Framework applications.</span></span>  
  
 [<span data-ttu-id="ac036-131">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="ac036-131">Security</span></span>](../../../standard/security/index.md)  
 <span data-ttu-id="ac036-132">.NET 'teki tüm güvenlik yönlerini açıklayan makalelere bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="ac036-132">Contains links to articles describing all aspects of security in .NET.</span></span>  
  
 <span data-ttu-id="ac036-133">[Güvenlik araçları](/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="ac036-133">[Security Tools](/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))</span></span>  
 <span data-ttu-id="ac036-134">Güvenlik ilkesini güvenli hale getirmek ve yönetmek için .NET Framework araçlar.</span><span class="sxs-lookup"><span data-stu-id="ac036-134">.NET Framework tools for securing and administering security policy.</span></span>  
  
 <span data-ttu-id="ac036-135">[Güvenli uygulamalar oluşturmak için kaynaklar](/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ac036-135">[Resources for Creating Secure Applications](/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))</span></span>  
 <span data-ttu-id="ac036-136">Güvenli uygulamalar oluşturmaya yönelik makalelere bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac036-136">Provides links to articles for creating secure applications.</span></span>  
  
 [<span data-ttu-id="ac036-137">Güvenlik Kaynakçası</span><span class="sxs-lookup"><span data-stu-id="ac036-137">Security Bibliography</span></span>](/visualstudio/ide/securing-applications)  
 <span data-ttu-id="ac036-138">Çevrimiçi ve yazdırma için kullanılabilir dış kaynaklara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="ac036-138">Provides links to external resources available online and in print.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac036-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac036-139">See also</span></span>

- [<span data-ttu-id="ac036-140">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ac036-140">ADO.NET</span></span>](index.md)
- [<span data-ttu-id="ac036-141">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ac036-141">ADO.NET Overview</span></span>](ado-net-overview.md)
