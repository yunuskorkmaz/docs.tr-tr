---
title: "Tehlikeli İzinler ve İlke Yönetimi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- permissions [.NET Framework], policy administration
- security [.NET Framework], dangerous permissions
- code security, dangerous permissions
- secure coding, dangerous permissions
- permissions [.NET Framework], dangerous
ms.assetid: 1929e854-23a0-4bb1-94be-e8aa3b609e32
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0c8a01cbae2077838a8eef3f2f673e7d9d646717
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="dangerous-permissions-and-policy-administration"></a>Tehlikeli İzinler ve İlke Yönetimi
.NET Framework izinleri sağlayan korumalı işlemlerinin birkaç olası circumvented bir güvenlik sistemi izin verebilirsiniz. Yalnızca güvenilir kod ve ardından yalnızca gerektiğinde bu tehlikeli izinleri verilmelidir. Aynı zamanda bu izinleri verildiğinde genellikle kötü amaçlı kod karşı savunma yoktur yoktur.  
  
> [!NOTE]
>  İçinde [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], terminolojisi ve .NET Framework güvenlik modelinin önemli değişiklikler olmuştur. Bu değişiklikler hakkında daha fazla bilgi için bkz: [güvenlik değişiklikleri](../../../docs/framework/security/security-changes.md).  
  
 Tehlikeli izinler aşağıdaki tabloda açıklanmıştır.  
  
|İzin|Riski|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|Tehlikeli görülür, yönetilmeyen koda çağırmak yönetilen kod sağlar.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|Doğrulama kod herhangi bir şey yapabilirsiniz.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|Geçersiz kılınan kanıt güvenlik ilkesi kandırmaya.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|Güvenlik ilkesini değiştirme olanağı güvenlik devre dışı bırakabilirsiniz.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|Seri hale getirme kullanımını erişilebilirlik mekanizmaları atlayabilir. Ayrıntılar için bkz [güvenlik ve Serileştirme](../../../docs/framework/misc/security-and-serialization.md).|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|Geçerli sorumlu ayarlamanıza olanak rol tabanlı güvenlik neden olabilir.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|İş parçacığı işleme iş parçacıkları ile ilişkili güvenlik durumu nedeniyle tehlikeli.|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|Özel üyelerin erişilebilirlik mekanizmaları üstesinden gelmek için kullanabilirsiniz.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenli kodlama yönergeleri](../../../docs/standard/security/secure-coding-guidelines.md)
