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
# <a name="reliability"></a>Güvenilirlik
SQL Server gibi sunucu ortamlarında yürütülen kodun zaman uyumsuz özel durumlara karşı korunması önemlidir. Burada ele alındığı gibi güvenilirlik, .NET Framework sürüm 2,0 ortamında çalıştırılan tüm ana bilgisayar için SQL Server, ancak güvenilir kod yazmak için özel değildir. Ancak, SQL Server sürüm 2,0 ' in yeni güvenilirlik özelliklerinden oluşan, örnek olarak kullanılan ilk hizmettir.  
  
 SQL Server çalışan kodun diğer sunucu ortamlarından daha sıkı güvenilirlik kılavuzlarıyla uğraşmanız gerekir. Bunun nedeni, kaynak tüketiminin kenarındaki SQL Server 'in sürekli işlemidir.  <xref:System.OutOfMemoryException> ve <xref:System.Threading.ThreadAbortException> özel durumlar SQL Server ortamında yaygın olmayan bir durumdur. Genel olarak bu yönergeler, tam güvenilir yönetilen kodun, <xref:System.AppDomain>düzeyinde geri dönüştürme tarafında düzgün şekilde başarısız olmasına olanak tanıyan güvenilirlik ve daha fazlasına karşı, sunucunun tutarlılık ve kullanılabilirliği koruduğu birincil yoldur.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [SQL Server Programlama ve Konak Koruması Öznitelikleri](sql-server-programming-and-host-protection-attributes.md)  
 Yönetilen kodun yürütülmesini kısıtlamak için <xref:System.Security.Permissions.HostProtectionAttribute> özniteliğinin SQL Server tarafından nasıl kullanıldığını açıklar.  
  
 [Güvenilirlik En İyi Yöntemleri](reliability-best-practices.md)  
 Güvenilirlik gereksinimlerini karşılayan kod yazmak için yönergeler sağlar.  
  
 [Kısıtlı Yürütme Bölgeleri](constrained-execution-regions.md)  
 Kısıtlanmış yürütme bölgelerinin işlevini ve davranışını açıklar (CERs).  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Security.Permissions.HostProtectionAttribute>  
  
 <xref:System.Security.Permissions.HostProtectionResource>
