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
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a><span data-ttu-id="c6f7f-102">Risk azaltma: X509CertificateClaimSet. Findclaim yöntemi</span><span class="sxs-lookup"><span data-stu-id="c6f7f-102">Mitigation: X509CertificateClaimSet.FindClaims Method</span></span>
<span data-ttu-id="c6f7f-103"><xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> yöntemi, .NET Framework 4.6.1 hedefleyen uygulamalarla başlayarak, SAN alanındaki tüm DNS girişleriyle `claimType` bağımsız değişkenini eşleştirmeye çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="c6f7f-103">Starting with apps that target the .NET Framework 4.6.1,  the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method will attempt to match the `claimType` argument with all the DNS entries in its SAN field.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="c6f7f-104">Etki</span><span class="sxs-lookup"><span data-stu-id="c6f7f-104">Impact</span></span>  
 <span data-ttu-id="c6f7f-105">Bu değişiklik yalnızca .NET Framework 4.6.1 başlayarak .NET Framework sürümlerini hedefleyen uygulamaları etkiler.</span><span class="sxs-lookup"><span data-stu-id="c6f7f-105">This change only affects apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>  
  
 <span data-ttu-id="c6f7f-106">.NET Framework önceki sürümlerini hedefleyen uygulamalar için <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> yöntemi yalnızca son DNS girdisiyle `claimType` bağımsız değişkeniyle eşleştirmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="c6f7f-106">For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method attempts to match the `claimType` argument only with the last  DNS entry.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="c6f7f-107">Azaltma</span><span class="sxs-lookup"><span data-stu-id="c6f7f-107">Mitigation</span></span>  
 <span data-ttu-id="c6f7f-108">Bu değişiklik istenmeyen ise, .NET Framework 4.6.1 ile başlayan .NET Framework sürümlerini hedefleyen uygulamalar, uygulamanın yapılandırma dosyasının [\<çalışma zamanı >](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne aşağıdaki yapılandırma ayarını ekleyerek devre dışı bırakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c6f7f-108">If this change is undesirable, apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1 can opt out of it by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />   
</runtime>  
```  
  
 <span data-ttu-id="c6f7f-109">Ayrıca, .NET Framework önceki sürümlerini hedefleyen, ancak .NET Framework 4.6.1 altında çalışan uygulamalar ve sonraki sürümler, aşağıdaki yapılandırma ayarını [\<çalışma zamanı >](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne ekleyerek bu davranışı kabul edebilir. uygulamanın yapılandırma dosyası:</span><span class="sxs-lookup"><span data-stu-id="c6f7f-109">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />   
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c6f7f-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6f7f-110">See also</span></span>

- [<span data-ttu-id="c6f7f-111">Yeniden Hedefleme Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="c6f7f-111">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6-1.md)
