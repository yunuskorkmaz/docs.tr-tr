---
title: 'Risk azaltma: X509CertificateClaimSet. Findclaim yöntemi'
description: X509CertificateClaimSet. Findclaim yönteminin, .NET Framework 4.6.1 ' i hedefleyen uygulamalar için nasıl değiştiğini öğrenin.
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
ms.openlocfilehash: ed9e345f9e48156f37f493caa78e6b3901cecf23
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253576"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a>Risk azaltma: X509CertificateClaimSet. Findclaim yöntemi

.NET Framework 4.6.1 ' i hedefleyen uygulamalarla başlayarak, <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> yöntemi, `claimType` San ALANıNDAKI tüm DNS girişleriyle bağımsız değişkeni ile eşleştirmeye çalışır.  
  
## <a name="impact"></a>Etki  

 Bu değişiklik yalnızca .NET Framework 4.6.1 başlayarak .NET Framework sürümlerini hedefleyen uygulamaları etkiler.  
  
 .NET Framework önceki sürümlerini hedefleyen uygulamalar için, <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> yöntemi `claimType` yalnızca son DNS girdisiyle bağımsız değişkenle eşleştirmeye çalışır.  
  
## <a name="mitigation"></a>Risk azaltma  

 Bu değişiklik istenmeyen ise, .NET Framework 4.6.1 ile başlayan .NET Framework sürümlerini hedefleyen uygulamalar, [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) uygulamanın yapılandırma dosyasının bölümüne aşağıdaki yapılandırma ayarını ekleyerek devre dışı bırakabilirsiniz:  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />
</runtime>  
```  
  
 Ayrıca, .NET Framework önceki sürümlerini hedefleyen, ancak .NET Framework 4.6.1 altında çalışan uygulamalar ve sonraki sürümler, [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) uygulamanın yapılandırma dosyasının bölümüne aşağıdaki yapılandırma ayarını ekleyerek bu davranışı kabul edebilir:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />
</runtime>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)
