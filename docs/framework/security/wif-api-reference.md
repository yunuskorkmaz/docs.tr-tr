---
title: "WIF API Başvurusu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a027d902-9314-4bfd-b172-4e81847b1d68
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: d7ae7ef82d12c024441d01ef420bc9366e3c589d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="wif-api-reference"></a><span data-ttu-id="6c475-102">WIF API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="6c475-102">WIF API Reference</span></span>
<span data-ttu-id="6c475-103">Windows Identity Foundation (WIF) sınıfları aşağıdaki derlemeler arasında bölme: `mscorlib` (mscorlib.dll) `System.IdentityModel` (System.IdentityModel.dll) `System.IdentityModel.Services` (System.IdentityModel.Services.dll) ve `System.ServiceModel` () System.ServiceModel.dll).</span><span class="sxs-lookup"><span data-stu-id="6c475-103">Windows Identity Foundation (WIF) classes are split across the following assemblies: `mscorlib` (mscorlib.dll), `System.IdentityModel` (System.IdentityModel.dll), `System.IdentityModel.Services` (System.IdentityModel.Services.dll), and `System.ServiceModel` (System.ServiceModel.dll).</span></span> <span data-ttu-id="6c475-104">Bu konu WIF ad alanları ve her ad alanı içeren sınıfların kısa açıklamaları bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c475-104">This topic provides links to the WIF namespaces and brief explanations of the classes that each namespace contains.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6c475-105">Aşağıdaki `System.IdentityModel` ad alanları içeren WCF beyana dayalı kimlik modelinde uygulayan sınıflar: <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType>, ve <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6c475-105">The following `System.IdentityModel` namespaces contain classes that implement the WCF claims-based identity model: <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType>, and <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6c475-106">.NET Framework 4. 5'ile başlayarak, WCF beyana dayalı kimlik modelinde WIF tarafından kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6c475-106">Starting with .NET Framework 4.5, the WCF claims-based identity model is superseded by WIF.</span></span> <span data-ttu-id="6c475-107">Sınıflar bu üç ad alanlarında WIF tabanlı çözümler oluştururken kullanmamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6c475-107">You should not use classes in these three namespaces when building solutions based on WIF.</span></span>  
  
 <xref:System.IdentityModel?displayProperty=nameWithType>  
 <span data-ttu-id="6c475-108">Tanımlama bilgisi dönüşümler, güvenlik belirteci Hizmetleri ve özel XML sözlük okuyucular temsil eden sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="6c475-108">Contains classes that represent cookie transforms, security token services, and specialized XML dictionary readers.</span></span>  
  
 <xref:System.IdentityModel.Configuration?displayProperty=nameWithType>  
 <span data-ttu-id="6c475-109">Uygulamalar ve Windows Identity Foundation (WIF) kullanılarak oluşturulmuş hizmetler için yapılandırma sağlayan sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="6c475-109">Contains classes that provide configuration for applications and services built using the Windows Identity Foundation (WIF).</span></span> <span data-ttu-id="6c475-110">Bu ad alanındaki sınıflar ayarlara altında [ \<identityConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="6c475-110">The classes in this namespace represent settings under the [\<identityConfiguration>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span>  
  
 <xref:System.IdentityModel.Metadata?displayProperty=nameWithType>  
 <span data-ttu-id="6c475-111">Federasyon meta veri belgesi öğelerini temsil eden sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="6c475-111">Contains classes that represent elements in a Federation Metadata document.</span></span>  
  
 <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>  
 <span data-ttu-id="6c475-112">WS-Trust yapıları temsil eden sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="6c475-112">Contains classes that represent WS-Trust artifacts.</span></span>  
  
 <xref:System.IdentityModel.Services?displayProperty=nameWithType>  
 <span data-ttu-id="6c475-113">Pasif (WS-Federation) senaryolarında kullanılan sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="6c475-113">Contains classes that are used in passive (WS-Federation) scenarios.</span></span> <span data-ttu-id="6c475-114">Ayrıca altında ayarlara bazı sınıfları içerir [ \<system.identityModel.services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="6c475-114">Also contains some classes that represent settings under the [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) element.</span></span> <span data-ttu-id="6c475-115">Bu öğe ayarlarında WS-Federasyon uygulamaları için yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="6c475-115">Settings under this element configure WS-Federation for applications.</span></span> <span data-ttu-id="6c475-116">`System.IdentityModel.Services.Configuration` Ad alanı, çoğu WS-Federasyon yapılandırmak için kullanılan sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="6c475-116">The `System.IdentityModel.Services.Configuration` namespace contains most of the classes that are used to configure WS-Federation.</span></span>  
  
 <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>  
 <span data-ttu-id="6c475-117">WS-Federasyon protokolünü kullanan WIF uygulamaları için yapılandırma sağlayan sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="6c475-117">Contains classes that provide configuration for WIF applications that use the WS-Federation protocol.</span></span> <span data-ttu-id="6c475-118">Bu ad alanındaki sınıflar ayarlara altında [ \<system.identityModel.services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="6c475-118">The classes in this namespace represent settings under the [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) element.</span></span> <span data-ttu-id="6c475-119">`System.IdentityModel.Services` Ad alanı da WS-Federasyon yapılandırmak için kullanılan bazı sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="6c475-119">The `System.IdentityModel.Services` namespace also contains some classes that are used to configure WS-Federation.</span></span>  
  
 <xref:System.IdentityModel.Services.Tokens?displayProperty=nameWithType>  
 <span data-ttu-id="6c475-120">Web grubu senaryoları için özel güvenlik belirteci işleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="6c475-120">Contains specialized security token handlers for Web farm scenarios.</span></span>  
  
 <xref:System.IdentityModel.Tokens?displayProperty=nameWithType>  
 <span data-ttu-id="6c475-121">Güvenlik belirteçleri, güvenlik belirteci işleyicileri ve diğer güvenlik belirteci yapıları temsil eden sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="6c475-121">Contains classes that represent security tokens, security token handlers, and other security token artifacts.</span></span>  
  
 <xref:System.Security.Claims?displayProperty=nameWithType>  
 <span data-ttu-id="6c475-122">Talepler, talep tabanlı kimlik, talep tabanlı ilkeleri ve diğer talep tabanlı kimlik modeli yapıları temsil eden sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="6c475-122">Contains classes that represent claims, claims-based identities, claims-based principals, and other claims-based identity model artifacts.</span></span>  
  
 <xref:System.ServiceModel.Security?displayProperty=nameWithType>  
 <span data-ttu-id="6c475-123">WCF sözleşmeleri, kanalları, hizmet konakları ve etkin (WS-Trust) senaryolarında kullanılır diğer yapıları temsil eden sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="6c475-123">Contains classes that represent WCF contracts, channels, service hosts and other artifacts that are used in active (WS-Trust) scenarios.</span></span> <span data-ttu-id="6c475-124">Bu ad ayrıca Windows Communication Foundation (WCF) özeldir ve WIF tarafından kullanılmayan sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="6c475-124">This namespace also contains classes that are specific to Windows Communication Foundation (WCF) and that are not used by WIF.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c475-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6c475-125">See Also</span></span>  
 [<span data-ttu-id="6c475-126">WIF yapılandırma başvurusu</span><span class="sxs-lookup"><span data-stu-id="6c475-126">WIF Configuration Reference</span></span>](../../../docs/framework/security/wif-configuration-reference.md)  
 [<span data-ttu-id="6c475-127">WIF 3.5 ve WIF 4.5 arasında Namespace eşleme</span><span class="sxs-lookup"><span data-stu-id="6c475-127">Namespace Mapping between WIF 3.5 and WIF 4.5</span></span>](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)
