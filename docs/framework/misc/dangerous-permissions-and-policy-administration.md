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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 17a596d9fc223dc53268ae9c91f7d02357b0a9b8
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489981"
---
# <a name="dangerous-permissions-and-policy-administration"></a>Tehlikeli İzinler ve İlke Yönetimi
.NET Framework için izinleri sağlayan korumalı işlemlerinin birkaç olası circumvented güvenlik sistemi izin verebilirsiniz. Yalnızca güvenilir kod ve ardından yalnızca gerektiğinde bu tehlikeli izinleri verilmelidir. Aynı zamanda bu izinleri verdiyseniz genellikle kötü amaçlı kod karşı savunması yoktur yoktur.  
  
> [!NOTE]
>  .NET Framework 4'te .NET Framework güvenlik modeli ve terminoloji önemli değişiklikler olmuştur. Bu değişiklikler hakkında daha fazla bilgi için bkz. [güvenlik değişiklikleri](../../../docs/framework/security/security-changes.md).  
  
 Tehlikeli izinler aşağıdaki tabloda açıklanmıştır.  
  
|İzin|Riski|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|Yönetilen kodun çoğunlukla tehlikeli olduğu yönetilmeyen koda çağrı sağlar.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|Doğrulama kod her şeyi yapabilirsiniz.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|Geçersiz kılınan kanıt güvenlik ilkesi kandırmaya.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|Güvenlik, güvenlik ilkesini değiştirmek için bu özelliği devre dışı bırakabilirsiniz.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|Serileştirme kullanımını erişilebilirlik mekanizmaları atlayabilir. Ayrıntılar için bkz [güvenlik ve Serileştirme](../../../docs/framework/misc/security-and-serialization.md).|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|Rol tabanlı güvenlik özelliğine geçerli sorumlu neden olabilir.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|İşleme iş parçacıkları iş parçacıkları ile ilişkili güvenlik durumu nedeniyle tehlikelidir.|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|Özel üyeler erişilebilirlik mekanizmalarını aşmak için kullanabilirsiniz.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Kodlama Yönergeleri](../../../docs/standard/security/secure-coding-guidelines.md)
