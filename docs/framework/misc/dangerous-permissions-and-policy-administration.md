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
ms.openlocfilehash: 15d28ff7d11b5d15ce44d9ab1f56548256850ff8
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645754"
---
# <a name="dangerous-permissions-and-policy-administration"></a>Tehlikeli İzinler ve İlke Yönetimi
.NET Framework'ün izin verdiği korumalı işlemlerden bazıları, güvenlik sisteminin atlatılmasına izin verebilir. Bu tehlikeli izinler yalnızca güvenilir koda ve daha sonra yalnızca gerektiği gibi verilmelidir. Bu izinler verilirse genellikle kötü amaçlı koda karşı savunma yoktur.  
  
> [!NOTE]
> .NET Framework 4'te .NET Framework güvenlik modeli nde ve terminolojisinde önemli değişiklikler olmuştur. Bu değişiklikler hakkında daha fazla bilgi için [Güvenlik Değişiklikleri'ne](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes)bakın.  
  
 Tehlikeli izinler aşağıdaki tabloda açıklanmıştır.  
  
|İzin|Potansiyel risk|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|Yönetilen kodun genellikle tehlikeli olan yönetilmeyen koda çağrı lmasına izin verir.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|Doğrulama olmadan, kod her şeyi yapabilir.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|Geçersiz kılınan kanıtlar güvenlik politikasını kandırabilir.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|Güvenlik ilkesini değiştirme özelliği güvenliği devre dışı kılabilir.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|Serileştirme kullanımı erişilebilirlik mekanizmaları atlatmak olabilir. Ayrıntılar için [Güvenlik ve Serileştirme'ye](security-and-serialization.md)bakın.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|Geçerli asıllığı ayarlama yeteneği rol tabanlı güvenliği kandırabilir.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|İş parçacıklarının manipülasyonu, iş parçacıklarıyla ilişkili güvenlik durumu nedeniyle tehlikelidir.|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|Erişilebilirlik mekanizmalarını yenmek için özel üyeler kullanabilir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Kodlama Yönergeleri](../../standard/security/secure-coding-guidelines.md)
