---
title: 'Azaltma: X509CertificateClaimSet.FindClaims Method'
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f7fb1eb0c502584caac11ca3dde6e7e646b29cfe
ms.sourcegitcommit: 26f4a7697c32978f6a328c89dc4ea87034065989
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66251090"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a>Azaltma: X509CertificateClaimSet.FindClaims Method
.NET Framework 4.6.1'i hedefleyen uygulamalar ile başlayan <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> yöntemi eşleştirilecek deneyecek `claimType` bağımsız değişkeni, SAN alanındaki tüm DNS girişi.  
  
## <a name="impact"></a>Etki  
 Bu değişiklik, yalnızca .NET Framework 4.6.1 ile başlayarak .NET Framework sürümleri hedefleyen uygulamaları etkiler.  
  
 .NET Framework'ün önceki sürümlerini hedefleyen uygulamalar için <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> yöntemi çalışır eşleştirilecek `claimType` son DNS girişi ile yalnızca bağımsız değişken.  
  
## <a name="mitigation"></a>Azaltma  
 Bu değişiklik, istenmeyen ise, .NET Framework 4.6.1 ile başlayarak .NET Framework sürümlerini hedefleyen uygulamalar dışında aşağıdaki yapılandırma ayarı ekleyerek seçebilirsiniz [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) bölümü Uygulamanın yapılandırma dosyası:  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />   
</runtime>  
```  
  
 Ayrıca, .NET Framework'ün önceki sürümlerini hedefleyen ancak .NET Framework 4.6.1 ve sonraki sürümler altında çalışan uygulamalar, bu davranış için aşağıdaki yapılandırma ayarı ekleyerek seçebilirsiniz [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) uygulamanın yapılandırma dosyası bölümünü:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />   
</runtime>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Hedefleme Değişiklikleri](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
