---
title: 'Azaltma: X509CertificateClaimSet.FindClaims Method'
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e3b3645d9fc00087e163b9200edb5fbcf0dbbd9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59217217"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a>Azaltma: X509CertificateClaimSet.FindClaims Method
Hedefleyen uygulamalar ile başlayan [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> yöntemi eşleştirilecek deneyecek `claimType` bağımsız değişkeni, SAN alanındaki tüm DNS girişi.  
  
## <a name="impact"></a>Etki  
 Bu değişiklik, yalnızca .NET Framework başlayarak sürümlerini hedefleyen uygulamaları etkiler [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].  
  
 .NET Framework'ün önceki sürümlerini hedefleyen uygulamalar için <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> yöntemi çalışır eşleştirilecek `claimType` son DNS girişi ile yalnızca bağımsız değişken.  
  
## <a name="mitigation"></a>Azaltma  
 Bu değişiklik, istenmeyen ise, uygulamalar hedef başlayarak .NET Framework sürümleri [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] dışında aşağıdaki yapılandırma ayarı ekleyerek iyileştirilmiş [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) uygulamanın bir bölümünü yapılandırma dosyası:  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />   
</runtime>  
```  
  
 Ayrıca, .NET Framework'ün önceki sürümlerini hedefleyen ancak altında çalışan uygulamalar [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] ve sonraki sürümler kabul etme için bu davranış için şu yapılandırma ayarı ekleyerek [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)uygulamanın yapılandırma dosyası bölümünü:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />   
</runtime>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Hedefleme Değişiklikleri](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
