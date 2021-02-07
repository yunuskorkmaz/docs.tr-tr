---
description: 'Daha fazla bilgi edinin: ADO.NET uygulamalarının güvenliğini sağlama'
title: Uygulamalarının Güvenliğini Sağlama
ms.date: 03/30/2017
ms.assetid: 005a1d43-6ee5-471e-ad98-1d30a44d49d5
ms.openlocfilehash: 4e4d219d1f4249846943d019e174abd6d43687c7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718882"
---
# <a name="securing-adonet-applications"></a><span data-ttu-id="9fbee-103">ADO.NET uygulamalarının güvenliğini sağlama</span><span class="sxs-lookup"><span data-stu-id="9fbee-103">Securing ADO.NET applications</span></span>

<span data-ttu-id="9fbee-104">Güvenli bir ADO.NET uygulaması yazmak, Kullanıcı girişini doğrulamamak gibi yaygın kodlama ile kullanmaktan daha fazlasını içerir.</span><span class="sxs-lookup"><span data-stu-id="9fbee-104">Writing a secure ADO.NET application involves more than avoiding common coding pitfalls such as not validating user input.</span></span> <span data-ttu-id="9fbee-105">Verilere erişen bir uygulama, bir saldırganın duyarlı verileri almak, değiştirmek veya yok etmek için yararlanabilecek birçok olası hata noktası içerir.</span><span class="sxs-lookup"><span data-stu-id="9fbee-105">An application that accesses data has many potential points of failure that an attacker can exploit to retrieve, manipulate, or destroy sensitive data.</span></span> <span data-ttu-id="9fbee-106">Bu nedenle, uygulamanızın tasarım aşamasında, son dağıtım ve devam eden bakımda güvenlik açısından tehdit modellemesi sürecinde güvenliğin tüm yönlerini anlamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="9fbee-106">It is therefore important to understand all aspects of security, from the process of threat modeling during the design phase of your application, to its eventual deployment and ongoing maintenance.</span></span>  
  
<span data-ttu-id="9fbee-107">.NET Framework, veritabanı uygulamalarının güvenliğini sağlamak ve yönetmek için birçok yararlı sınıf, hizmet ve araç sağlar.</span><span class="sxs-lookup"><span data-stu-id="9fbee-107">The .NET Framework provides many useful classes, services, and tools for securing and administering database applications.</span></span> <span data-ttu-id="9fbee-108">Ortak dil çalışma zamanı (CLR), kod erişim güvenliği (CAS) ile, yönetilen kodun izinlerini kısıtlamak için kod ile çalışmak üzere tür açısından güvenli bir ortam sağlar.</span><span class="sxs-lookup"><span data-stu-id="9fbee-108">The common language runtime (CLR) provides a type-safe environment for code to run in, with code access security (CAS) to restrict further the permissions of managed code.</span></span> <span data-ttu-id="9fbee-109">Aşağıdaki güvenli veri erişimi kodlama uygulamaları, olası bir saldırgan tarafından kullanılabilecek hasar süresini sınırlar.</span><span class="sxs-lookup"><span data-stu-id="9fbee-109">Following secure data access coding practices limits the damage that can be inflicted by a potential attacker.</span></span>  
  
<span data-ttu-id="9fbee-110">Güvenli kod yazma, veritabanları gibi yönetilmeyen kaynaklarla çalışırken kendinden yetenekli güvenlik boşluklarına karşı koruma sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="9fbee-110">Writing secure code does not guard against self-inflicted security holes when working with unmanaged resources such as databases.</span></span> <span data-ttu-id="9fbee-111">SQL Server gibi çoğu sunucu veritabanlarının kendi güvenlik sistemleri vardır ve bu, doğru şekilde uygulandığında güvenliği geliştirir.</span><span class="sxs-lookup"><span data-stu-id="9fbee-111">Most server databases, such as SQL Server, have their own security systems, which enhance security when implemented correctly.</span></span> <span data-ttu-id="9fbee-112">Ancak, güçlü güvenlik sistemine sahip bir veri kaynağı, uygun bir şekilde yapılandırılmamışsa bir saldırıya karşı çok daha yakın olabilir.</span><span class="sxs-lookup"><span data-stu-id="9fbee-112">However, even a data source with a robust security system can be victimized in an attack if it is not configured appropriately.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9fbee-113">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="9fbee-113">In this section</span></span>

 [<span data-ttu-id="9fbee-114">Güvenliğe genel bakış</span><span class="sxs-lookup"><span data-stu-id="9fbee-114">Security Overview</span></span>](security-overview.md)  
 <span data-ttu-id="9fbee-115">Güvenli ADO.NET uygulamaları tasarlamaya yönelik öneriler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9fbee-115">Provides recommendations for designing secure ADO.NET applications.</span></span>  
  
 [<span data-ttu-id="9fbee-116">Güvenli Veri Erişimi</span><span class="sxs-lookup"><span data-stu-id="9fbee-116">Secure Data Access</span></span>](secure-data-access.md)  
 <span data-ttu-id="9fbee-117">Güvenli bir veri kaynağından verilerle nasıl çalışabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="9fbee-117">Describes how to work with data from a secured data source.</span></span>  
  
 [<span data-ttu-id="9fbee-118">Güvenli İstemci Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="9fbee-118">Secure Client Applications</span></span>](secure-client-applications.md)  
 <span data-ttu-id="9fbee-119">İstemci uygulamalarına yönelik güvenlik konularını açıklar.</span><span class="sxs-lookup"><span data-stu-id="9fbee-119">Describes security considerations for client applications.</span></span>  
  
 [<span data-ttu-id="9fbee-120">Kod Erişimi Güvenliği ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9fbee-120">Code Access Security and ADO.NET</span></span>](code-access-security.md)  
 <span data-ttu-id="9fbee-121">CA 'ların, ADO.NET kodunu korumanıza nasıl yardımcı olduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="9fbee-121">Describes how CAS can help protect ADO.NET code.</span></span> <span data-ttu-id="9fbee-122">Ayrıca kısmi güvenle nasıl çalışılabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="9fbee-122">Also discusses how to work with partial trust.</span></span>  
  
 [<span data-ttu-id="9fbee-123">Gizlilik ve Veri Güvenliği</span><span class="sxs-lookup"><span data-stu-id="9fbee-123">Privacy and Data Security</span></span>](privacy-and-data-security.md)  
 <span data-ttu-id="9fbee-124">ADO.NET uygulamaları için şifreleme seçeneklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="9fbee-124">Describes encryption options for ADO.NET applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9fbee-125">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="9fbee-125">Related sections</span></span>

 [<span data-ttu-id="9fbee-126">Veri kümesi ve DataTable Güvenlik Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9fbee-126">DataSet and DataTable security guidance</span></span>](dataset-datatable-dataview/security-guidance.md)  
 <span data-ttu-id="9fbee-127">Ve için Güvenlik Kılavuzu <xref:System.Data.DataSet> sağlar <xref:System.Data.DataTable> .</span><span class="sxs-lookup"><span data-stu-id="9fbee-127">Provides security guidance for <xref:System.Data.DataSet> and <xref:System.Data.DataTable>.</span></span>

 [<span data-ttu-id="9fbee-128">SQL Server Güvenliği</span><span class="sxs-lookup"><span data-stu-id="9fbee-128">SQL Server Security</span></span>](./sql/sql-server-security.md)  
 <span data-ttu-id="9fbee-129">Bir geliştiricinin perspektifinden SQL Server güvenlik özelliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="9fbee-129">Describes SQL Server security features from a developer's perspective.</span></span>  
  
 [<span data-ttu-id="9fbee-130">Güvenlik konuları</span><span class="sxs-lookup"><span data-stu-id="9fbee-130">Security Considerations</span></span>](./ef/security-considerations.md)  
 <span data-ttu-id="9fbee-131">Entity Framework uygulamalar için güvenliği açıklar.</span><span class="sxs-lookup"><span data-stu-id="9fbee-131">Describes security for Entity Framework applications.</span></span>  
  
 [<span data-ttu-id="9fbee-132">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="9fbee-132">Security</span></span>](../../../standard/security/index.md)  
 <span data-ttu-id="9fbee-133">.NET 'teki tüm güvenlik yönlerini açıklayan makalelere bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="9fbee-133">Contains links to articles describing all aspects of security in .NET.</span></span>  
  
 <span data-ttu-id="9fbee-134">[Güvenlik araçları](/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="9fbee-134">[Security Tools](/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))</span></span>  
 <span data-ttu-id="9fbee-135">Güvenlik ilkesini güvenli hale getirmek ve yönetmek için .NET Framework araçlar.</span><span class="sxs-lookup"><span data-stu-id="9fbee-135">.NET Framework tools for securing and administering security policy.</span></span>  
  
 <span data-ttu-id="9fbee-136">[Güvenli uygulamalar oluşturmak için kaynaklar](/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9fbee-136">[Resources for Creating Secure Applications](/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))</span></span>  
 <span data-ttu-id="9fbee-137">Güvenli uygulamalar oluşturmaya yönelik makalelere bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="9fbee-137">Provides links to articles for creating secure applications.</span></span>  
  
 [<span data-ttu-id="9fbee-138">Güvenlik Kaynakçası</span><span class="sxs-lookup"><span data-stu-id="9fbee-138">Security Bibliography</span></span>](/visualstudio/ide/securing-applications)  
 <span data-ttu-id="9fbee-139">Çevrimiçi ve yazdırma için kullanılabilir dış kaynaklara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="9fbee-139">Provides links to external resources available online and in print.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fbee-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9fbee-140">See also</span></span>

- [<span data-ttu-id="9fbee-141">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9fbee-141">ADO.NET</span></span>](index.md)
- [<span data-ttu-id="9fbee-142">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9fbee-142">ADO.NET Overview</span></span>](ado-net-overview.md)
