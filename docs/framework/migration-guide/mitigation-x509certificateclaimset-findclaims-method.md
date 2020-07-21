---
title: 'Risk azaltma: X509CertificateClaimSet. Findclaim yöntemi'
description: X509CertificateClaimSet. Findclaim yönteminin, .NET Framework 4.6.1 ' i hedefleyen uygulamalar için nasıl değiştiğini öğrenin.
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
ms.openlocfilehash: 304d8fb5adc27b33f2410faaaf8662e0ff9be66d
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475326"
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
