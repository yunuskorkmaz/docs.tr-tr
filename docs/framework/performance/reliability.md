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
# <a name="reliability"></a>Güvenilirlik
SQL Server gibi sunucu ortamlarında kod yürütürken zaman uyumsuz özel durumları karşı korumak önemlidir. Güvenilirlik, burada açıklandığı gibi SQL Server'a özgü değildir ancak 2.0 ortam için bir .NET Framework sürümünde yürütülen herhangi bir ana bilgisayara yazma güvenilir kod. Ancak SQL Server kapsamlı hale ilk hizmeti örnek olarak kullanılmak üzere sürüm 2.0, yeni güvenilirlik özelliklerini kullanmak olabilir.  
  
 SQL Server'da çalışan kod daha katı güvenilirlik kuralları diğer sunucu ortamlarında daha uğraşmanız gerekir. Bu SQL Server'ın düzenli kaynak tüketimi nedeniyle uçta işlemdir.  <xref:System.OutOfMemoryException> ve <xref:System.Threading.ThreadAbortException> özel durumlar SQL Server ortamında sık karşılaşılan bir durum değildir. Bu genel olarak daha az üzerinde odaklı güvenilirlik yönergelerdir ve yönetilen kod face, düzgün bir şekilde başarısız için daha fazla üzerinde tam olarak güvenilen izin vererek <xref:System.AppDomain>-server, tutarlılık ve kullanılabilirlik tutar birincil yoludur geri dönüşümü düzeyi.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [SQL Server Programlama ve Konak Koruması Öznitelikleri](../../../docs/framework/performance/sql-server-programming-and-host-protection-attributes.md)  
 Açıklayan nasıl <xref:System.Security.Permissions.HostProtectionAttribute> özniteliği SQL Server tarafından yönetilen kodun yürütülmesini kısıtlamak için kullanılır.  
  
 [Güvenilirlik En İyi Yöntemleri](../../../docs/framework/performance/reliability-best-practices.md)  
 Güvenilirlik gereksinimleri karşılayan kodu yazmak için yönergeler sağlar.  
  
 [Kısıtlı Yürütme Bölgeleri](../../../docs/framework/performance/constrained-execution-regions.md)  
 Kısıtlı yürütme bölgeleri (CERs) davranışını ve işlevi açıklanmaktadır.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Security.Permissions.HostProtectionAttribute>  
  
 <xref:System.Security.Permissions.HostProtectionResource>
