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
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a><span data-ttu-id="4717b-102">Azaltma: X509CertificateClaimSet.FindClaims Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4717b-102">Mitigation: X509CertificateClaimSet.FindClaims Method</span></span>
<span data-ttu-id="4717b-103">.NET Framework 4.6.1'i hedefleyen uygulamalardan başlayarak, <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> `claimType` yöntem bağımsız değişkeni SAN alanındaki tüm DNS girişleriyle eşleştirmeye çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="4717b-103">Starting with apps that target the .NET Framework 4.6.1,  the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method will attempt to match the `claimType` argument with all the DNS entries in its SAN field.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="4717b-104">Etki</span><span class="sxs-lookup"><span data-stu-id="4717b-104">Impact</span></span>  
 <span data-ttu-id="4717b-105">Bu değişiklik yalnızca .NET Framework 4.6.1 ile başlayan .NET Framework sürümlerini hedefleyen uygulamaları etkiler.</span><span class="sxs-lookup"><span data-stu-id="4717b-105">This change only affects apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>  
  
 <span data-ttu-id="4717b-106">.NET Framework'ün önceki sürümlerini hedefleyen <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> uygulamalar için `claimType` yöntem, bağımsız değişkeni yalnızca son DNS girişiyle eşleştirmeyi dener.</span><span class="sxs-lookup"><span data-stu-id="4717b-106">For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method attempts to match the `claimType` argument only with the last  DNS entry.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="4717b-107">Risk azaltma</span><span class="sxs-lookup"><span data-stu-id="4717b-107">Mitigation</span></span>  
 <span data-ttu-id="4717b-108">Bu değişiklik istenmiyorsa, .NET Framework 4.6.1 ile başlayan .NET Framework sürümlerini hedefleyen uygulamalar, uygulamanın yapılandırma dosyasının [ \<çalışma zamanı>](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne aşağıdaki yapılandırma ayarını ekleyerek bu çerçeveyi devre dışı edebilir:</span><span class="sxs-lookup"><span data-stu-id="4717b-108">If this change is undesirable, apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1 can opt out of it by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />
</runtime>  
```  
  
 <span data-ttu-id="4717b-109">Buna ek olarak, .NET Framework'ün önceki sürümlerini hedefleyen ancak .NET Framework 4.6.1 ve sonraki sürümler altında çalışan uygulamalar, uygulamanın yapılandırma dosyasının [ \<çalışma>](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne aşağıdaki yapılandırma ayarını ekleyerek bu davranışı seçebilir:</span><span class="sxs-lookup"><span data-stu-id="4717b-109">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4717b-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4717b-110">See also</span></span>

- [<span data-ttu-id="4717b-111">Uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="4717b-111">Application compatibility</span></span>](application-compatibility.md)
