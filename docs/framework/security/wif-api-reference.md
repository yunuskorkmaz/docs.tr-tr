---
title: WIF API Başvurusu
ms.date: 03/30/2017
ms.assetid: a027d902-9314-4bfd-b172-4e81847b1d68
author: BrucePerlerMS
ms.openlocfilehash: 17a1da0a3b0ea6567fd805e7273f793ace35ae69
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958352"
---
# <a name="wif-api-reference"></a><span data-ttu-id="58865-102">WIF API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="58865-102">WIF API Reference</span></span>
<span data-ttu-id="58865-103">Windows Identity Foundation `mscorlib` (WIF) sınıfları şu derlemeler arasında bölünür: (mscorlib. dll), `System.IdentityModel` (System. IdentityModel. dll), `System.IdentityModel.Services` (System. IdentityModel. Services. dll) ve `System.ServiceModel` ( System. ServiceModel. dll).</span><span class="sxs-lookup"><span data-stu-id="58865-103">Windows Identity Foundation (WIF) classes are split across the following assemblies: `mscorlib` (mscorlib.dll), `System.IdentityModel` (System.IdentityModel.dll), `System.IdentityModel.Services` (System.IdentityModel.Services.dll), and `System.ServiceModel` (System.ServiceModel.dll).</span></span> <span data-ttu-id="58865-104">Bu konuda, WıF ad alanları ve her bir ad alanının içerdiği sınıfların kısa açıklamaları için bağlantılar sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="58865-104">This topic provides links to the WIF namespaces and brief explanations of the classes that each namespace contains.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="58865-105">Aşağıdaki `System.IdentityModel` ad alanlarında, WCF talep tabanlı kimlik modelini uygulayan sınıflar bulunur: <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType>, ve <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="58865-105">The following `System.IdentityModel` namespaces contain classes that implement the WCF claims-based identity model: <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType>, and <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>.</span></span> <span data-ttu-id="58865-106">.NET Framework 4,5 ' den başlayarak, WCF talep tabanlı kimlik modelinin yerini WıF almıştır.</span><span class="sxs-lookup"><span data-stu-id="58865-106">Starting with .NET Framework 4.5, the WCF claims-based identity model is superseded by WIF.</span></span> <span data-ttu-id="58865-107">WıF tabanlı çözümler oluştururken bu üç ad alanında sınıfları kullanmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="58865-107">You should not use classes in these three namespaces when building solutions based on WIF.</span></span>  
  
 <xref:System.IdentityModel?displayProperty=nameWithType>  
 <span data-ttu-id="58865-108">Tanımlama bilgisi dönüştürmeleri, güvenlik belirteci Hizmetleri ve özelleşmiş XML sözlüğü okuyucuları temsil eden sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="58865-108">Contains classes that represent cookie transforms, security token services, and specialized XML dictionary readers.</span></span>  
  
 <xref:System.IdentityModel.Configuration?displayProperty=nameWithType>  
 <span data-ttu-id="58865-109">Windows Identity Foundation (WıF) kullanılarak oluşturulan uygulamalar ve hizmetler için yapılandırma sağlayan sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="58865-109">Contains classes that provide configuration for applications and services built using the Windows Identity Foundation (WIF).</span></span> <span data-ttu-id="58865-110">Bu ad alanındaki sınıflar, [ \<IdentityConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi altındaki ayarları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="58865-110">The classes in this namespace represent settings under the [\<identityConfiguration>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span>  
  
 <xref:System.IdentityModel.Metadata?displayProperty=nameWithType>  
 <span data-ttu-id="58865-111">Federasyon meta veri belgesindeki öğeleri temsil eden sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="58865-111">Contains classes that represent elements in a Federation Metadata document.</span></span>  
  
 <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>  
 <span data-ttu-id="58865-112">WS-Trust yapılarını temsil eden sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="58865-112">Contains classes that represent WS-Trust artifacts.</span></span>  
  
 <xref:System.IdentityModel.Services?displayProperty=nameWithType>  
 <span data-ttu-id="58865-113">Pasif (WS-Federation) senaryolarında kullanılan sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="58865-113">Contains classes that are used in passive (WS-Federation) scenarios.</span></span> <span data-ttu-id="58865-114">Ayrıca [ \<System. IdentityModel. Services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) öğesi altındaki ayarları temsil eden bazı sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="58865-114">Also contains some classes that represent settings under the [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) element.</span></span> <span data-ttu-id="58865-115">Bu öğenin altındaki ayarlar, uygulamalar için WS-Federation ' i yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="58865-115">Settings under this element configure WS-Federation for applications.</span></span> <span data-ttu-id="58865-116">Ad `System.IdentityModel.Services.Configuration` alanı, WS-Federation ' i yapılandırmak için kullanılan sınıfların çoğunu içerir.</span><span class="sxs-lookup"><span data-stu-id="58865-116">The `System.IdentityModel.Services.Configuration` namespace contains most of the classes that are used to configure WS-Federation.</span></span>  
  
 <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>  
 <span data-ttu-id="58865-117">WS-Federation protokolünü kullanan WıF uygulamaları için yapılandırma sağlayan sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="58865-117">Contains classes that provide configuration for WIF applications that use the WS-Federation protocol.</span></span> <span data-ttu-id="58865-118">Bu ad alanındaki sınıflar, [ \<System. IdentityModel. Services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) öğesi altındaki ayarları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="58865-118">The classes in this namespace represent settings under the [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) element.</span></span> <span data-ttu-id="58865-119">Ad `System.IdentityModel.Services` alanı, WS-Federation yapılandırmak için kullanılan bazı sınıfları da içerir.</span><span class="sxs-lookup"><span data-stu-id="58865-119">The `System.IdentityModel.Services` namespace also contains some classes that are used to configure WS-Federation.</span></span>  
  
 <xref:System.IdentityModel.Services.Tokens?displayProperty=nameWithType>  
 <span data-ttu-id="58865-120">Web grubu senaryoları için özelleştirilmiş güvenlik belirteci işleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="58865-120">Contains specialized security token handlers for Web farm scenarios.</span></span>  
  
 <xref:System.IdentityModel.Tokens?displayProperty=nameWithType>  
 <span data-ttu-id="58865-121">Güvenlik belirteçlerini, güvenlik belirteci işleyicilerini ve diğer güvenlik belirteci yapıtlarını temsil eden sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="58865-121">Contains classes that represent security tokens, security token handlers, and other security token artifacts.</span></span>  
  
 <xref:System.Security.Claims?displayProperty=nameWithType>  
 <span data-ttu-id="58865-122">Talepleri, talep tabanlı kimlikleri, talep tabanlı sorumluları ve diğer talep tabanlı kimlik modeli yapılarını temsil eden sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="58865-122">Contains classes that represent claims, claims-based identities, claims-based principals, and other claims-based identity model artifacts.</span></span>  
  
 <xref:System.ServiceModel.Security?displayProperty=nameWithType>  
 <span data-ttu-id="58865-123">WCF sözleşmelerini, kanalları, hizmet ana bilgisayarlarını ve etkin (WS-Trust) senaryolarında kullanılan diğer yapıtları temsil eden sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="58865-123">Contains classes that represent WCF contracts, channels, service hosts and other artifacts that are used in active (WS-Trust) scenarios.</span></span> <span data-ttu-id="58865-124">Bu ad alanı Ayrıca, Windows Communication Foundation (WCF) öğesine özgü ve WıF tarafından kullanılmayan sınıfları da içerir.</span><span class="sxs-lookup"><span data-stu-id="58865-124">This namespace also contains classes that are specific to Windows Communication Foundation (WCF) and that are not used by WIF.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58865-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58865-125">See also</span></span>

- [<span data-ttu-id="58865-126">WIF Yapılandırma Başvurusu</span><span class="sxs-lookup"><span data-stu-id="58865-126">WIF Configuration Reference</span></span>](../../../docs/framework/security/wif-configuration-reference.md)
- [<span data-ttu-id="58865-127">WIF 3.5 ile WIF 4.5 Arasında Ad Alanı Eşleme</span><span class="sxs-lookup"><span data-stu-id="58865-127">Namespace Mapping between WIF 3.5 and WIF 4.5</span></span>](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)
