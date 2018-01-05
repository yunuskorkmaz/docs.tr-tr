---
title: "Azaltma: X509CertificateClaimSet.FindClaims yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d1b10d5c746839f504eab258664b2a60d12244f7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a><span data-ttu-id="3a935-102">Azaltma: X509CertificateClaimSet.FindClaims yöntemi</span><span class="sxs-lookup"><span data-stu-id="3a935-102">Mitigation: X509CertificateClaimSet.FindClaims Method</span></span>
<span data-ttu-id="3a935-103">Hedefleyen uygulamalar ile başlayan [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> yöntemi eşleşen deneyecek `claimType` bağımsız değişkeni, SAN alanındaki tüm DNS girişlerini ile.</span><span class="sxs-lookup"><span data-stu-id="3a935-103">Starting with apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)],  the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method will attempt to match the `claimType` argument with all the DNS entries in its SAN field.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="3a935-104">Etki</span><span class="sxs-lookup"><span data-stu-id="3a935-104">Impact</span></span>  
 <span data-ttu-id="3a935-105">Bu değişiklik, yalnızca .NET Framework başlayarak sürümlerini hedefleyen uygulamaları etkiler [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3a935-105">This change only affects apps that target versions of the .NET Framework starting with the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].</span></span>  
  
 <span data-ttu-id="3a935-106">.NET Framework'ün önceki sürümlerini hedefleyen uygulamalar için <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> yöntemi çalışır eşleşecek şekilde `claimType` bağımsız değişkeni yalnızca son DNS girişi ile.</span><span class="sxs-lookup"><span data-stu-id="3a935-106">For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method attempts to match the `claimType` argument only with the last  DNS entry.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="3a935-107">Azaltma</span><span class="sxs-lookup"><span data-stu-id="3a935-107">Mitigation</span></span>  
 <span data-ttu-id="3a935-108">Bu değişiklik istenmeyen ise, uygulamalar, hedef başlayarak .NET Framework sürümleri [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] onu dışında şu yapılandırma ayarı ekleyerek seçebilirsiniz [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) uygulamanın bölümü yapılandırma dosyası:</span><span class="sxs-lookup"><span data-stu-id="3a935-108">If this change is undesirable, apps that target versions of the .NET Framework starting with the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] can opt out of it by adding the following configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />   
</runtime>  
```  
  
 <span data-ttu-id="3a935-109">Buna ek olarak, .NET Framework'ün önceki sürümlerini hedefleyen ancak altında çalışan uygulamalar [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] ve sonraki sürümler kabul etme Bu davranışı şu yapılandırma ayarı ekleyerek [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)uygulamanın yapılandırma dosyasının:</span><span class="sxs-lookup"><span data-stu-id="3a935-109">In addition, apps that target previous versions of the .NET Framework but are running under the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and later versions can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />   
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3a935-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3a935-110">See Also</span></span>  
 [<span data-ttu-id="3a935-111">Yeniden Hedefleme Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="3a935-111">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
