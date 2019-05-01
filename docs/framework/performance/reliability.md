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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3b00ba0fdf732a864fb4fb757c6012a3d36740b2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949298"
---
# <a name="reliability"></a><span data-ttu-id="33c67-102">Güvenilirlik</span><span class="sxs-lookup"><span data-stu-id="33c67-102">Reliability</span></span>
<span data-ttu-id="33c67-103">SQL Server gibi sunucu ortamlarında kod yürütürken zaman uyumsuz özel durumları karşı korumak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="33c67-103">It is important that code executing in server environments such as SQL Server protect against asynchronous exceptions.</span></span> <span data-ttu-id="33c67-104">Güvenilirlik, burada açıklandığı gibi SQL Server'a özgü değildir ancak 2.0 ortam için bir .NET Framework sürümünde yürütülen herhangi bir ana bilgisayara yazma güvenilir kod.</span><span class="sxs-lookup"><span data-stu-id="33c67-104">Reliability, as discussed here, is not specific to SQL Server but to writing reliable code for any host executing in a .NET Framework version 2.0 environment.</span></span> <span data-ttu-id="33c67-105">Ancak SQL Server kapsamlı hale ilk hizmeti örnek olarak kullanılmak üzere sürüm 2.0, yeni güvenilirlik özelliklerini kullanmak olabilir.</span><span class="sxs-lookup"><span data-stu-id="33c67-105">However, SQL Server is the first service making extensive use of the new reliability features of version 2.0, so it is used as an example.</span></span>  
  
 <span data-ttu-id="33c67-106">SQL Server'da çalışan kod daha katı güvenilirlik kuralları diğer sunucu ortamlarında daha uğraşmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="33c67-106">Code running in SQL Server must deal with more stringent reliability guidelines than other server environments.</span></span> <span data-ttu-id="33c67-107">Bu SQL Server'ın düzenli kaynak tüketimi nedeniyle uçta işlemdir.</span><span class="sxs-lookup"><span data-stu-id="33c67-107">This is due to SQL Server’s steady operation at the edge of resource consumption.</span></span>  <span data-ttu-id="33c67-108"><xref:System.OutOfMemoryException> ve <xref:System.Threading.ThreadAbortException> özel durumlar SQL Server ortamında sık karşılaşılan bir durum değildir.</span><span class="sxs-lookup"><span data-stu-id="33c67-108"><xref:System.OutOfMemoryException> and <xref:System.Threading.ThreadAbortException> exceptions are not uncommon in the SQL Server environment.</span></span> <span data-ttu-id="33c67-109">Bu genel olarak daha az üzerinde odaklı güvenilirlik yönergelerdir ve yönetilen kod face, düzgün bir şekilde başarısız için daha fazla üzerinde tam olarak güvenilen izin vererek <xref:System.AppDomain>-server, tutarlılık ve kullanılabilirlik tutar birincil yoludur geri dönüşümü düzeyi.</span><span class="sxs-lookup"><span data-stu-id="33c67-109">These guidelines in general are focused less on reliability and more on allowing fully trusted managed code to fail gracefully in the face of <xref:System.AppDomain>-level recycling, which is the primary way the server maintains consistency and availability.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="33c67-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="33c67-110">In This Section</span></span>  
 [<span data-ttu-id="33c67-111">SQL Server Programlama ve Konak Koruması Öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="33c67-111">SQL Server Programming and Host Protection Attributes</span></span>](../../../docs/framework/performance/sql-server-programming-and-host-protection-attributes.md)  
 <span data-ttu-id="33c67-112">Açıklayan nasıl <xref:System.Security.Permissions.HostProtectionAttribute> özniteliği SQL Server tarafından yönetilen kodun yürütülmesini kısıtlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="33c67-112">Describes how the <xref:System.Security.Permissions.HostProtectionAttribute> attribute is used by SQL Server to restrict the execution of managed code.</span></span>  
  
 [<span data-ttu-id="33c67-113">Güvenilirlik En İyi Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="33c67-113">Reliability Best Practices</span></span>](../../../docs/framework/performance/reliability-best-practices.md)  
 <span data-ttu-id="33c67-114">Güvenilirlik gereksinimleri karşılayan kodu yazmak için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="33c67-114">Provides guidelines for writing code that meets reliability requirements.</span></span>  
  
 [<span data-ttu-id="33c67-115">Kısıtlı Yürütme Bölgeleri</span><span class="sxs-lookup"><span data-stu-id="33c67-115">Constrained Execution Regions</span></span>](../../../docs/framework/performance/constrained-execution-regions.md)  
 <span data-ttu-id="33c67-116">Kısıtlı yürütme bölgeleri (CERs) davranışını ve işlevi açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="33c67-116">Describes the function and behavior of constrained execution regions (CERs).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="33c67-117">Başvuru</span><span class="sxs-lookup"><span data-stu-id="33c67-117">Reference</span></span>  
 <xref:System.Security.Permissions.HostProtectionAttribute>  
  
 <xref:System.Security.Permissions.HostProtectionResource>
