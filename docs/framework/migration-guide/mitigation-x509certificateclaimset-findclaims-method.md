---
title: 'Azaltma: X509CertificateClaimSet.FindClaims Yöntemi'
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
ms.openlocfilehash: f94a5f685a5aa94332bf2e15e5d5eb0def02d7ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400143"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a>Azaltma: X509CertificateClaimSet.FindClaims Yöntemi
.NET Framework 4.6.1'i hedefleyen uygulamalardan başlayarak, <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> `claimType` yöntem bağımsız değişkeni SAN alanındaki tüm DNS girişleriyle eşleştirmeye çalışacaktır.  
  
## <a name="impact"></a>Etki  
 Bu değişiklik yalnızca .NET Framework 4.6.1 ile başlayan .NET Framework sürümlerini hedefleyen uygulamaları etkiler.  
  
 .NET Framework'ün önceki sürümlerini hedefleyen <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> uygulamalar için `claimType` yöntem, bağımsız değişkeni yalnızca son DNS girişiyle eşleştirmeyi dener.  
  
## <a name="mitigation"></a>Risk azaltma  
 Bu değişiklik istenmiyorsa, .NET Framework 4.6.1 ile başlayan .NET Framework sürümlerini hedefleyen uygulamalar, uygulamanın yapılandırma dosyasının [ \<çalışma zamanı>](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne aşağıdaki yapılandırma ayarını ekleyerek bu çerçeveyi devre dışı edebilir:  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />
</runtime>  
```  
  
 Buna ek olarak, .NET Framework'ün önceki sürümlerini hedefleyen ancak .NET Framework 4.6.1 ve sonraki sürümler altında çalışan uygulamalar, uygulamanın yapılandırma dosyasının [ \<çalışma>](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne aşağıdaki yapılandırma ayarını ekleyerek bu davranışı seçebilir:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />
</runtime>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)
