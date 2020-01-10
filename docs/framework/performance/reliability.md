---
title: Güvenilirlik
ms.date: 03/30/2017
helpviewer_keywords:
- SQL Server [.NET Framework]
- managed code, reliability
- reliability [.NET Framework]
- writing reliable code
- code, reliability
ms.assetid: 294aa306-0afe-4cbe-b397-86ba9f1860f8
ms.openlocfilehash: 2d6601c4cbad32f768ff16301307083f35d986a0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715961"
---
# <a name="reliability"></a><span data-ttu-id="a96ae-102">Güvenilirlik</span><span class="sxs-lookup"><span data-stu-id="a96ae-102">Reliability</span></span>
<span data-ttu-id="a96ae-103">SQL Server gibi sunucu ortamlarında yürütülen kodun zaman uyumsuz özel durumlara karşı korunması önemlidir.</span><span class="sxs-lookup"><span data-stu-id="a96ae-103">It is important that code executing in server environments such as SQL Server protect against asynchronous exceptions.</span></span> <span data-ttu-id="a96ae-104">Burada ele alındığı gibi güvenilirlik, .NET Framework sürüm 2,0 ortamında çalıştırılan tüm ana bilgisayar için SQL Server, ancak güvenilir kod yazmak için özel değildir.</span><span class="sxs-lookup"><span data-stu-id="a96ae-104">Reliability, as discussed here, is not specific to SQL Server but to writing reliable code for any host executing in a .NET Framework version 2.0 environment.</span></span> <span data-ttu-id="a96ae-105">Ancak, SQL Server sürüm 2,0 ' in yeni güvenilirlik özelliklerinden oluşan, örnek olarak kullanılan ilk hizmettir.</span><span class="sxs-lookup"><span data-stu-id="a96ae-105">However, SQL Server is the first service making extensive use of the new reliability features of version 2.0, so it is used as an example.</span></span>  
  
 <span data-ttu-id="a96ae-106">SQL Server çalışan kodun diğer sunucu ortamlarından daha sıkı güvenilirlik kılavuzlarıyla uğraşmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a96ae-106">Code running in SQL Server must deal with more stringent reliability guidelines than other server environments.</span></span> <span data-ttu-id="a96ae-107">Bunun nedeni, kaynak tüketiminin kenarındaki SQL Server 'in sürekli işlemidir.</span><span class="sxs-lookup"><span data-stu-id="a96ae-107">This is due to SQL Server’s steady operation at the edge of resource consumption.</span></span>  <span data-ttu-id="a96ae-108"><xref:System.OutOfMemoryException> ve <xref:System.Threading.ThreadAbortException> özel durumlar SQL Server ortamında yaygın olmayan bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="a96ae-108"><xref:System.OutOfMemoryException> and <xref:System.Threading.ThreadAbortException> exceptions are not uncommon in the SQL Server environment.</span></span> <span data-ttu-id="a96ae-109">Genel olarak bu yönergeler, tam güvenilir yönetilen kodun, <xref:System.AppDomain>düzeyinde geri dönüştürme tarafında düzgün şekilde başarısız olmasına olanak tanıyan güvenilirlik ve daha fazlasına karşı, sunucunun tutarlılık ve kullanılabilirliği koruduğu birincil yoldur.</span><span class="sxs-lookup"><span data-stu-id="a96ae-109">These guidelines in general are focused less on reliability and more on allowing fully trusted managed code to fail gracefully in the face of <xref:System.AppDomain>-level recycling, which is the primary way the server maintains consistency and availability.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a96ae-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="a96ae-110">In This Section</span></span>  
 [<span data-ttu-id="a96ae-111">SQL Server Programlama ve Konak Koruması Öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="a96ae-111">SQL Server Programming and Host Protection Attributes</span></span>](sql-server-programming-and-host-protection-attributes.md)  
 <span data-ttu-id="a96ae-112">Yönetilen kodun yürütülmesini kısıtlamak için <xref:System.Security.Permissions.HostProtectionAttribute> özniteliğinin SQL Server tarafından nasıl kullanıldığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="a96ae-112">Describes how the <xref:System.Security.Permissions.HostProtectionAttribute> attribute is used by SQL Server to restrict the execution of managed code.</span></span>  
  
 [<span data-ttu-id="a96ae-113">Güvenilirlik En İyi Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="a96ae-113">Reliability Best Practices</span></span>](reliability-best-practices.md)  
 <span data-ttu-id="a96ae-114">Güvenilirlik gereksinimlerini karşılayan kod yazmak için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a96ae-114">Provides guidelines for writing code that meets reliability requirements.</span></span>  
  
 [<span data-ttu-id="a96ae-115">Kısıtlı Yürütme Bölgeleri</span><span class="sxs-lookup"><span data-stu-id="a96ae-115">Constrained Execution Regions</span></span>](constrained-execution-regions.md)  
 <span data-ttu-id="a96ae-116">Kısıtlanmış yürütme bölgelerinin işlevini ve davranışını açıklar (CERs).</span><span class="sxs-lookup"><span data-stu-id="a96ae-116">Describes the function and behavior of constrained execution regions (CERs).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a96ae-117">Başvuru</span><span class="sxs-lookup"><span data-stu-id="a96ae-117">Reference</span></span>  
 <xref:System.Security.Permissions.HostProtectionAttribute>  
  
 <xref:System.Security.Permissions.HostProtectionResource>
