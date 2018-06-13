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
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33395417"
---
# <a name="reliability"></a>Güvenilirlik
SQL Server gibi sunucu ortamlarında kod yürütme zaman uyumsuz özel durumları karşı korumak önemlidir. Güvenilirlik, burada açıklandığı gibi SQL Server'a özel değildir ancak yazma için güvenilir bir .NET Framework sürüm yürütülen herhangi bir ana bilgisayar için 2.0 ortamı kodu. Ancak, SQL Server kapsamlı yapmadan ilk Hizmeti'yle sürüm 2.0, yeni güvenilirlik özelliklerini örnek olarak kullanılmak üzere olur.  
  
 SQL Server çalıştıran kodu diğer sunucu ortamları'den daha sıkı güvenilirlik yönergeleri uğraşmanız gerekir. Bu SQL Server'ın sürekli kaynak tüketimi nedeniyle kenarına işlemdir.  <xref:System.OutOfMemoryException> ve <xref:System.Threading.ThreadAbortException> özel durumlar SQL Server ortamında seyrek değildir. Bu genel olarak daha az üzerinde odaklanmış güvenilirlik yönergelerdir ve yönetilen kod face, düzgün biçimde başarısız olmasına daha fazla üzerinde tam olarak güvenilmeyen izin verme <xref:System.AppDomain>-sunucusu tutar tutarlılık ve kullanılabilirlik birincil yoludur geri dönüşümü düzeyi.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [SQL Server Programlama ve Konak Koruması Öznitelikleri](../../../docs/framework/performance/sql-server-programming-and-host-protection-attributes.md)  
 Açıklar nasıl <xref:System.Security.Permissions.HostProtectionAttribute> özniteliği SQL Server tarafından yönetilen kodun yürütülmesini kısıtlamak için kullanılır.  
  
 [Güvenilirlik En İyi Yöntemleri](../../../docs/framework/performance/reliability-best-practices.md)  
 Güvenilirlik gereksinimlerini karşılayan kod yazma için yönergeler sağlar.  
  
 [Kısıtlı Yürütme Bölgeleri](../../../docs/framework/performance/constrained-execution-regions.md)  
 Kısıtlı yürütme bölgeleri (CERs) davranışını ve işlevi açıklanmaktadır.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Security.Permissions.HostProtectionAttribute>  
  
 <xref:System.Security.Permissions.HostProtectionResource>
