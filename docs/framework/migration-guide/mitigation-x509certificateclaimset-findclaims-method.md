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
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a><span data-ttu-id="287c0-102">Azaltma: X509CertificateClaimSet.FindClaims Method</span><span class="sxs-lookup"><span data-stu-id="287c0-102">Mitigation: X509CertificateClaimSet.FindClaims Method</span></span>
<span data-ttu-id="287c0-103">.NET Framework 4.6.1'i hedefleyen uygulamalar ile başlayan <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> yöntemi eşleştirilecek deneyecek `claimType` bağımsız değişkeni, SAN alanındaki tüm DNS girişi.</span><span class="sxs-lookup"><span data-stu-id="287c0-103">Starting with apps that target the .NET Framework 4.6.1,  the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method will attempt to match the `claimType` argument with all the DNS entries in its SAN field.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="287c0-104">Etki</span><span class="sxs-lookup"><span data-stu-id="287c0-104">Impact</span></span>  
 <span data-ttu-id="287c0-105">Bu değişiklik, yalnızca .NET Framework 4.6.1 ile başlayarak .NET Framework sürümleri hedefleyen uygulamaları etkiler.</span><span class="sxs-lookup"><span data-stu-id="287c0-105">This change only affects apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>  
  
 <span data-ttu-id="287c0-106">.NET Framework'ün önceki sürümlerini hedefleyen uygulamalar için <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> yöntemi çalışır eşleştirilecek `claimType` son DNS girişi ile yalnızca bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="287c0-106">For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method attempts to match the `claimType` argument only with the last  DNS entry.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="287c0-107">Azaltma</span><span class="sxs-lookup"><span data-stu-id="287c0-107">Mitigation</span></span>  
 <span data-ttu-id="287c0-108">Bu değişiklik, istenmeyen ise, .NET Framework 4.6.1 ile başlayarak .NET Framework sürümlerini hedefleyen uygulamalar dışında aşağıdaki yapılandırma ayarı ekleyerek seçebilirsiniz [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) bölümü Uygulamanın yapılandırma dosyası:</span><span class="sxs-lookup"><span data-stu-id="287c0-108">If this change is undesirable, apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1 can opt out of it by adding the following configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />   
</runtime>  
```  
  
 <span data-ttu-id="287c0-109">Ayrıca, .NET Framework'ün önceki sürümlerini hedefleyen ancak .NET Framework 4.6.1 ve sonraki sürümler altında çalışan uygulamalar, bu davranış için aşağıdaki yapılandırma ayarı ekleyerek seçebilirsiniz [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) uygulamanın yapılandırma dosyası bölümünü:</span><span class="sxs-lookup"><span data-stu-id="287c0-109">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />   
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="287c0-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="287c0-110">See also</span></span>

- [<span data-ttu-id="287c0-111">Yeniden Hedefleme Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="287c0-111">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
