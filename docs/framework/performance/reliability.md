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
ms.openlocfilehash: acb84c6617cdffabfe276895f81e7df2b04bb8bb
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046243"
---
# <a name="reliability"></a>Güvenilirlik
SQL Server gibi sunucu ortamlarında yürütülen kodun zaman uyumsuz özel durumlara karşı korunması önemlidir. Burada ele alındığı gibi güvenilirlik, .NET Framework sürüm 2,0 ortamında çalıştırılan tüm ana bilgisayar için SQL Server, ancak güvenilir kod yazmak için özel değildir. Ancak, SQL Server sürüm 2,0 ' in yeni güvenilirlik özelliklerinden oluşan, örnek olarak kullanılan ilk hizmettir.  
  
 SQL Server çalışan kodun diğer sunucu ortamlarından daha sıkı güvenilirlik kılavuzlarıyla uğraşmanız gerekir. Bunun nedeni, kaynak tüketiminin kenarındaki SQL Server 'in sürekli işlemidir.  <xref:System.OutOfMemoryException>ve <xref:System.Threading.ThreadAbortException> özel durumlar SQL Server ortamda yaygın olmayan bir durumdur. Genel olan bu yönergeler, tam güvenilir yönetilen kodun, <xref:System.AppDomain>yüksek düzeyde geri dönüştürme işlemi sırasında düzgün bir şekilde başarısız olmasına ve sunucunun tutarlılık ve kullanılabilirlik düzeyini korumasının birincil yoludur.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [SQL Server Programlama ve Konak Koruması Öznitelikleri](sql-server-programming-and-host-protection-attributes.md)  
 Yönetilen kodun yürütülmesini <xref:System.Security.Permissions.HostProtectionAttribute> kısıtlamak için özniteliğinin SQL Server tarafından nasıl kullanıldığını açıklar.  
  
 [Güvenilirlik En İyi Yöntemleri](reliability-best-practices.md)  
 Güvenilirlik gereksinimlerini karşılayan kod yazmak için yönergeler sağlar.  
  
 [Kısıtlı Yürütme Bölgeleri](constrained-execution-regions.md)  
 Kısıtlanmış yürütme bölgelerinin işlevini ve davranışını açıklar (CERs).  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Security.Permissions.HostProtectionAttribute>  
  
 <xref:System.Security.Permissions.HostProtectionResource>
