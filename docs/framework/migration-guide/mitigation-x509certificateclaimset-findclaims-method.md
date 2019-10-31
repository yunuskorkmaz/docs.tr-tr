---
title: 'Risk azaltma: X509CertificateClaimSet. Findclaim yöntemi'
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
ms.openlocfilehash: 5591ecebeb924f84cc0efdaf78f40f9d835d2d02
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126078"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a>Risk azaltma: X509CertificateClaimSet. Findclaim yöntemi
<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> yöntemi, .NET Framework 4.6.1 hedefleyen uygulamalarla başlayarak, SAN alanındaki tüm DNS girişleriyle `claimType` bağımsız değişkenini eşleştirmeye çalışacaktır.  
  
## <a name="impact"></a>Etki  
 Bu değişiklik yalnızca .NET Framework 4.6.1 başlayarak .NET Framework sürümlerini hedefleyen uygulamaları etkiler.  
  
 .NET Framework önceki sürümlerini hedefleyen uygulamalar için <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> yöntemi yalnızca son DNS girdisiyle `claimType` bağımsız değişkeniyle eşleştirmeye çalışır.  
  
## <a name="mitigation"></a>Azaltma  
 Bu değişiklik istenmeyen ise, .NET Framework 4.6.1 ile başlayan .NET Framework sürümlerini hedefleyen uygulamalar, uygulamanın yapılandırma dosyasının [\<çalışma zamanı >](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne aşağıdaki yapılandırma ayarını ekleyerek devre dışı bırakabilirsiniz:  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />   
</runtime>  
```  
  
 Ayrıca, .NET Framework önceki sürümlerini hedefleyen, ancak .NET Framework 4.6.1 altında çalışan uygulamalar ve sonraki sürümler, aşağıdaki yapılandırma ayarını [\<çalışma zamanı >](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne ekleyerek bu davranışı kabul edebilir. uygulamanın yapılandırma dosyası:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />   
</runtime>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Hedefleme Değişiklikleri](retargeting-changes-in-the-net-framework-4-6-1.md)
