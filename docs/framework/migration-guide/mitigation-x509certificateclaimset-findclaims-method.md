---
title: 'Azaltma: X509CertificateClaimSet.FindClaims Method'
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ccc24cd494866c087860144f1720988ccfc2dfa8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54536444"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a><span data-ttu-id="5376d-102">Azaltma: X509CertificateClaimSet.FindClaims Method</span><span class="sxs-lookup"><span data-stu-id="5376d-102">Mitigation: X509CertificateClaimSet.FindClaims Method</span></span>
<span data-ttu-id="5376d-103">Hedefleyen uygulamalar ile başlayan [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> yöntemi eşleştirilecek deneyecek `claimType` bağımsız değişkeni, SAN alanındaki tüm DNS girişi.</span><span class="sxs-lookup"><span data-stu-id="5376d-103">Starting with apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)],  the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method will attempt to match the `claimType` argument with all the DNS entries in its SAN field.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="5376d-104">Etki</span><span class="sxs-lookup"><span data-stu-id="5376d-104">Impact</span></span>  
 <span data-ttu-id="5376d-105">Bu değişiklik, yalnızca .NET Framework başlayarak sürümlerini hedefleyen uygulamaları etkiler [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5376d-105">This change only affects apps that target versions of the .NET Framework starting with the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].</span></span>  
  
 <span data-ttu-id="5376d-106">.NET Framework'ün önceki sürümlerini hedefleyen uygulamalar için <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> yöntemi çalışır eşleştirilecek `claimType` son DNS girişi ile yalnızca bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="5376d-106">For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method attempts to match the `claimType` argument only with the last  DNS entry.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="5376d-107">Azaltma</span><span class="sxs-lookup"><span data-stu-id="5376d-107">Mitigation</span></span>  
 <span data-ttu-id="5376d-108">Bu değişiklik, istenmeyen ise, uygulamalar hedef başlayarak .NET Framework sürümleri [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] dışında aşağıdaki yapılandırma ayarı ekleyerek iyileştirilmiş [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) uygulamanın bir bölümünü yapılandırma dosyası:</span><span class="sxs-lookup"><span data-stu-id="5376d-108">If this change is undesirable, apps that target versions of the .NET Framework starting with the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] can opt out of it by adding the following configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />   
</runtime>  
```  
  
 <span data-ttu-id="5376d-109">Ayrıca, .NET Framework'ün önceki sürümlerini hedefleyen ancak altında çalışan uygulamalar [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] ve sonraki sürümler kabul etme için bu davranış için şu yapılandırma ayarı ekleyerek [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)uygulamanın yapılandırma dosyası bölümünü:</span><span class="sxs-lookup"><span data-stu-id="5376d-109">In addition, apps that target previous versions of the .NET Framework but are running under the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and later versions can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />   
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5376d-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5376d-110">See also</span></span>
- [<span data-ttu-id="5376d-111">Yeniden Hedefleme Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="5376d-111">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
