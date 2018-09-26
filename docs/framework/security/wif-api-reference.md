---
title: WIF API Başvurusu
ms.date: 03/30/2017
ms.assetid: a027d902-9314-4bfd-b172-4e81847b1d68
author: BrucePerlerMS
ms.openlocfilehash: 0cd373ae3fd5acb1650f0d8614b34c5d19cf9016
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47171653"
---
# <a name="wif-api-reference"></a><span data-ttu-id="a78ed-102">WIF API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="a78ed-102">WIF API Reference</span></span>
<span data-ttu-id="a78ed-103">Windows Identity Foundation (WIF) sınıfları aşağıdaki derlemeler arasında bölmek: `mscorlib` (mscorlib.dll) `System.IdentityModel` (System.IdentityModel.dll) `System.IdentityModel.Services` (System.IdentityModel.Services.dll) ve `System.ServiceModel` () System.ServiceModel.dll).</span><span class="sxs-lookup"><span data-stu-id="a78ed-103">Windows Identity Foundation (WIF) classes are split across the following assemblies: `mscorlib` (mscorlib.dll), `System.IdentityModel` (System.IdentityModel.dll), `System.IdentityModel.Services` (System.IdentityModel.Services.dll), and `System.ServiceModel` (System.ServiceModel.dll).</span></span> <span data-ttu-id="a78ed-104">Bu konuda WIF ad alanları ve kısa açıklamaları sınıfların her ad uzayını içeren bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="a78ed-104">This topic provides links to the WIF namespaces and brief explanations of the classes that each namespace contains.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a78ed-105">Aşağıdaki `System.IdentityModel` WCF beyana dayalı kimlik modeli uygulayan sınıflar ad alanlarında bulunur: <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType>, ve <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a78ed-105">The following `System.IdentityModel` namespaces contain classes that implement the WCF claims-based identity model: <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType>, and <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a78ed-106">.NET Framework 4.5 ile başlayarak, WCF beyana dayalı kimlik modelinin yerini WIF almıştır.</span><span class="sxs-lookup"><span data-stu-id="a78ed-106">Starting with .NET Framework 4.5, the WCF claims-based identity model is superseded by WIF.</span></span> <span data-ttu-id="a78ed-107">Sınıfları bu üç ad alanı üzerinde WIF tabanlı çözümler oluştururken kullanmamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a78ed-107">You should not use classes in these three namespaces when building solutions based on WIF.</span></span>  
  
 <xref:System.IdentityModel?displayProperty=nameWithType>  
 <span data-ttu-id="a78ed-108">Tanımlama bilgisi dönüşümler ve güvenlik belirteci hizmetlerine özel XML sözlük okuyucularına temsil eden sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="a78ed-108">Contains classes that represent cookie transforms, security token services, and specialized XML dictionary readers.</span></span>  
  
 <xref:System.IdentityModel.Configuration?displayProperty=nameWithType>  
 <span data-ttu-id="a78ed-109">Uygulamalar ve Windows Identity Foundation (WIF) kullanılarak oluşturulan hizmetler için yapılandırma sağlayan sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="a78ed-109">Contains classes that provide configuration for applications and services built using the Windows Identity Foundation (WIF).</span></span> <span data-ttu-id="a78ed-110">Bu ad alanındaki sınıflar ayarlara altında [ \<identityConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="a78ed-110">The classes in this namespace represent settings under the [\<identityConfiguration>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span>  
  
 <xref:System.IdentityModel.Metadata?displayProperty=nameWithType>  
 <span data-ttu-id="a78ed-111">Bir Federasyon meta veri belgesinin öğelerini temsil eden sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="a78ed-111">Contains classes that represent elements in a Federation Metadata document.</span></span>  
  
 <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>  
 <span data-ttu-id="a78ed-112">WS-Trust yapıları temsil eden sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="a78ed-112">Contains classes that represent WS-Trust artifacts.</span></span>  
  
 <xref:System.IdentityModel.Services?displayProperty=nameWithType>  
 <span data-ttu-id="a78ed-113">Pasif (WS-Federation) senaryolarında kullanılan sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="a78ed-113">Contains classes that are used in passive (WS-Federation) scenarios.</span></span> <span data-ttu-id="a78ed-114">Ayarlar altında temsil eden bazı sınıflar da içerir [ \<System.IdentityModel.Services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="a78ed-114">Also contains some classes that represent settings under the [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) element.</span></span> <span data-ttu-id="a78ed-115">Bu öğe ayarlarında WS-Federasyon uygulamaları için yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="a78ed-115">Settings under this element configure WS-Federation for applications.</span></span> <span data-ttu-id="a78ed-116">`System.IdentityModel.Services.Configuration` Ad alanı, çoğu WS-Federasyon yapılandırmak için kullanılan sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="a78ed-116">The `System.IdentityModel.Services.Configuration` namespace contains most of the classes that are used to configure WS-Federation.</span></span>  
  
 <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>  
 <span data-ttu-id="a78ed-117">WIF WS-Federasyon protokolünü kullanan uygulamalar için yapılandırma sağlayan sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="a78ed-117">Contains classes that provide configuration for WIF applications that use the WS-Federation protocol.</span></span> <span data-ttu-id="a78ed-118">Bu ad alanındaki sınıflar ayarlara altında [ \<System.IdentityModel.Services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="a78ed-118">The classes in this namespace represent settings under the [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) element.</span></span> <span data-ttu-id="a78ed-119">`System.IdentityModel.Services` Ad alanı, WS-Federasyon yapılandırmak için kullanılan bazı sınıflar da içerir.</span><span class="sxs-lookup"><span data-stu-id="a78ed-119">The `System.IdentityModel.Services` namespace also contains some classes that are used to configure WS-Federation.</span></span>  
  
 <xref:System.IdentityModel.Services.Tokens?displayProperty=nameWithType>  
 <span data-ttu-id="a78ed-120">Web grubu senaryoları için özel güvenlik belirteci işleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="a78ed-120">Contains specialized security token handlers for Web farm scenarios.</span></span>  
  
 <xref:System.IdentityModel.Tokens?displayProperty=nameWithType>  
 <span data-ttu-id="a78ed-121">Güvenlik belirteçleri, güvenlik belirteci işleyicileri ve diğer güvenlik belirteci yapılarını temsil eden sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="a78ed-121">Contains classes that represent security tokens, security token handlers, and other security token artifacts.</span></span>  
  
 <xref:System.Security.Claims?displayProperty=nameWithType>  
 <span data-ttu-id="a78ed-122">Talepler, beyana dayalı kimlikler, talep tabanlı ilkeleri ve diğer beyana dayalı kimlik modeli yapıları temsil eden sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="a78ed-122">Contains classes that represent claims, claims-based identities, claims-based principals, and other claims-based identity model artifacts.</span></span>  
  
 <xref:System.ServiceModel.Security?displayProperty=nameWithType>  
 <span data-ttu-id="a78ed-123">WCF sözleşmeleri, Kanallar, hizmet konakları ve active (WS-Trust) senaryolarında kullanılan diğer yapıları temsil eden sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="a78ed-123">Contains classes that represent WCF contracts, channels, service hosts and other artifacts that are used in active (WS-Trust) scenarios.</span></span> <span data-ttu-id="a78ed-124">Bu ad alanı, Windows Communication Foundation (WCF) için özeldir ve WIF tarafından kullanılmaz sınıflar da içerir.</span><span class="sxs-lookup"><span data-stu-id="a78ed-124">This namespace also contains classes that are specific to Windows Communication Foundation (WCF) and that are not used by WIF.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a78ed-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a78ed-125">See Also</span></span>  
 [<span data-ttu-id="a78ed-126">WIF Yapılandırma Başvurusu</span><span class="sxs-lookup"><span data-stu-id="a78ed-126">WIF Configuration Reference</span></span>](../../../docs/framework/security/wif-configuration-reference.md)  
 [<span data-ttu-id="a78ed-127">WIF 3.5 ile WIF 4.5 Arasında Ad Alanı Eşleme</span><span class="sxs-lookup"><span data-stu-id="a78ed-127">Namespace Mapping between WIF 3.5 and WIF 4.5</span></span>](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)
