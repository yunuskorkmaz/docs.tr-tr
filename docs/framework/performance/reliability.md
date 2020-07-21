---
title: Güvenilirlik
description: .NET 'teki güvenilirliği anlayın. SQL Server gibi .NET sürümünde çalışan konaklarda zaman uyumsuz özel durumlara karşı koruyun.
ms.date: 03/30/2017
helpviewer_keywords:
- SQL Server [.NET Framework]
- managed code, reliability
- reliability [.NET Framework]
- writing reliable code
- code, reliability
ms.assetid: 294aa306-0afe-4cbe-b397-86ba9f1860f8
ms.openlocfilehash: ce9ffbb7f58c2f5dc016c56c0e2ce13b45c30f26
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474260"
---
# <a name="reliability"></a><span data-ttu-id="754ec-104">Güvenilirlik</span><span class="sxs-lookup"><span data-stu-id="754ec-104">Reliability</span></span>
<span data-ttu-id="754ec-105">SQL Server gibi sunucu ortamlarında yürütülen kodun zaman uyumsuz özel durumlara karşı korunması önemlidir.</span><span class="sxs-lookup"><span data-stu-id="754ec-105">It is important that code executing in server environments such as SQL Server protect against asynchronous exceptions.</span></span> <span data-ttu-id="754ec-106">Burada ele alındığı gibi güvenilirlik, .NET Framework sürüm 2,0 ortamında çalıştırılan tüm ana bilgisayar için SQL Server, ancak güvenilir kod yazmak için özel değildir.</span><span class="sxs-lookup"><span data-stu-id="754ec-106">Reliability, as discussed here, is not specific to SQL Server but to writing reliable code for any host executing in a .NET Framework version 2.0 environment.</span></span> <span data-ttu-id="754ec-107">Ancak, SQL Server sürüm 2,0 ' in yeni güvenilirlik özelliklerinden oluşan, örnek olarak kullanılan ilk hizmettir.</span><span class="sxs-lookup"><span data-stu-id="754ec-107">However, SQL Server is the first service making extensive use of the new reliability features of version 2.0, so it is used as an example.</span></span>  
  
 <span data-ttu-id="754ec-108">SQL Server çalışan kodun diğer sunucu ortamlarından daha sıkı güvenilirlik kılavuzlarıyla uğraşmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="754ec-108">Code running in SQL Server must deal with more stringent reliability guidelines than other server environments.</span></span> <span data-ttu-id="754ec-109">Bunun nedeni, kaynak tüketiminin kenarındaki SQL Server 'in sürekli işlemidir.</span><span class="sxs-lookup"><span data-stu-id="754ec-109">This is due to SQL Server’s steady operation at the edge of resource consumption.</span></span>  <span data-ttu-id="754ec-110"><xref:System.OutOfMemoryException>ve <xref:System.Threading.ThreadAbortException> özel durumlar SQL Server ortamda yaygın olmayan bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="754ec-110"><xref:System.OutOfMemoryException> and <xref:System.Threading.ThreadAbortException> exceptions are not uncommon in the SQL Server environment.</span></span> <span data-ttu-id="754ec-111">Genel olan bu yönergeler, tam güvenilir yönetilen kodun, yüksek düzeyde geri dönüştürme işlemi sırasında düzgün bir şekilde başarısız olmasına ve <xref:System.AppDomain> sunucunun tutarlılık ve kullanılabilirlik düzeyini korumasının birincil yoludur.</span><span class="sxs-lookup"><span data-stu-id="754ec-111">These guidelines in general are focused less on reliability and more on allowing fully trusted managed code to fail gracefully in the face of <xref:System.AppDomain>-level recycling, which is the primary way the server maintains consistency and availability.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="754ec-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="754ec-112">In This Section</span></span>  
 [<span data-ttu-id="754ec-113">SQL Server Programlama ve Ana Bilgisayar Koruması Öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="754ec-113">SQL Server Programming and Host Protection Attributes</span></span>](sql-server-programming-and-host-protection-attributes.md)  
 <span data-ttu-id="754ec-114"><xref:System.Security.Permissions.HostProtectionAttribute>Yönetilen kodun yürütülmesini kısıtlamak için özniteliğinin SQL Server tarafından nasıl kullanıldığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="754ec-114">Describes how the <xref:System.Security.Permissions.HostProtectionAttribute> attribute is used by SQL Server to restrict the execution of managed code.</span></span>  
  
 [<span data-ttu-id="754ec-115">Güvenilirlik En İyi Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="754ec-115">Reliability Best Practices</span></span>](reliability-best-practices.md)  
 <span data-ttu-id="754ec-116">Güvenilirlik gereksinimlerini karşılayan kod yazmak için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="754ec-116">Provides guidelines for writing code that meets reliability requirements.</span></span>  
  
 [<span data-ttu-id="754ec-117">Kısıtlı Yürütme Bölgeleri</span><span class="sxs-lookup"><span data-stu-id="754ec-117">Constrained Execution Regions</span></span>](constrained-execution-regions.md)  
 <span data-ttu-id="754ec-118">Kısıtlanmış yürütme bölgelerinin işlevini ve davranışını açıklar (CERs).</span><span class="sxs-lookup"><span data-stu-id="754ec-118">Describes the function and behavior of constrained execution regions (CERs).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="754ec-119">Başvuru</span><span class="sxs-lookup"><span data-stu-id="754ec-119">Reference</span></span>  
 <xref:System.Security.Permissions.HostProtectionAttribute>  
  
 <xref:System.Security.Permissions.HostProtectionResource>
