---
title: Tehlikeli İzinler ve İlke Yönetimi
ms.date: 03/30/2017
helpviewer_keywords:
- permissions [.NET Framework], policy administration
- security [.NET Framework], dangerous permissions
- code security, dangerous permissions
- secure coding, dangerous permissions
- permissions [.NET Framework], dangerous
ms.assetid: 1929e854-23a0-4bb1-94be-e8aa3b609e32
ms.openlocfilehash: 026697feec7afe950628639c5e595ba0a0220b97
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217136"
---
# <a name="dangerous-permissions-and-policy-administration"></a>Tehlikeli İzinler ve İlke Yönetimi
.NET Framework izin sağladığı korumalı işlemlerden bazıları güvenlik sisteminin atlalanmasına izin verebilir. Bu tehlikeli izinler yalnızca güvenilir koda ve yalnızca gerekli şekilde verilmelidir. Bu izinler verildiğinde, genellikle kötü amaçlı koda karşı savunma yoktur.  
  
> [!NOTE]
> .NET Framework 4 ' te, .NET Framework güvenlik modelinde ve terminolojisinde önemli değişiklikler yapıldı. Bu değişiklikler hakkında daha fazla bilgi için bkz. [güvenlik değişiklikleri](../security/security-changes.md).  
  
 Tehlikeli izinler aşağıdaki tabloda açıklanmıştır.  
  
|İzin|Olası risk|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|Yönetilen kodun, genellikle tehlikeli olan yönetilmeyen koda çağrı yapmasına izin verir.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|Doğrulama olmadan kod herhangi bir işlem yapabilir.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|Geçersiz kılınan bulgu, güvenlik ilkesini kullanabilir.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|Güvenlik ilkesini değiştirme özelliği güvenliği devre dışı bırakabilir.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|Serileştirme kullanımı erişilebilirlik mekanizmalarını değiştirebilir. Ayrıntılar için bkz. [güvenlik ve serileştirme](security-and-serialization.md).|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|Geçerli sorumluyu ayarlama özelliği rol tabanlı güvenliği kullanabilir.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|İş parçacıkları ile ilişkili güvenlik durumu nedeniyle iş parçacıklarının işlenmesi tehlikelidir.|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|, Erişilebilirlik mekanizmalarını erteetmek için özel üyeleri kullanabilir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Kodlama Yönergeleri](../../standard/security/secure-coding-guidelines.md)
