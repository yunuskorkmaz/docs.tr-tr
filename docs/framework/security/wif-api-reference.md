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
ms.workload: dotnet
ms.openlocfilehash: e3209ac32314e2ac3f4e3e1920991ed29f956832
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="wif-api-reference"></a>WIF API Başvurusu
Windows Identity Foundation (WIF) sınıfları aşağıdaki derlemeler arasında bölme: `mscorlib` (mscorlib.dll) `System.IdentityModel` (System.IdentityModel.dll) `System.IdentityModel.Services` (System.IdentityModel.Services.dll) ve `System.ServiceModel` () System.ServiceModel.dll). Bu konu WIF ad alanları ve her ad alanı içeren sınıfların kısa açıklamaları bağlantılar sağlar.  
  
> [!IMPORTANT]
>  Aşağıdaki `System.IdentityModel` ad alanları içeren WCF beyana dayalı kimlik modelinde uygulayan sınıflar: <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType>, ve <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>. .NET Framework 4. 5'ile başlayarak, WCF beyana dayalı kimlik modelinde WIF tarafından kullanılmaktadır. Sınıflar bu üç ad alanlarında WIF tabanlı çözümler oluştururken kullanmamanız gerekir.  
  
 <xref:System.IdentityModel?displayProperty=nameWithType>  
 Tanımlama bilgisi dönüşümler, güvenlik belirteci Hizmetleri ve özel XML sözlük okuyucular temsil eden sınıfları içerir.  
  
 <xref:System.IdentityModel.Configuration?displayProperty=nameWithType>  
 Uygulamalar ve Windows Identity Foundation (WIF) kullanılarak oluşturulmuş hizmetler için yapılandırma sağlayan sınıflar içerir. Bu ad alanındaki sınıflar ayarlara altında [ \<identityConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi.  
  
 <xref:System.IdentityModel.Metadata?displayProperty=nameWithType>  
 Federasyon meta veri belgesi öğelerini temsil eden sınıfları içerir.  
  
 <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>  
 WS-Trust yapıları temsil eden sınıfları içerir.  
  
 <xref:System.IdentityModel.Services?displayProperty=nameWithType>  
 Pasif (WS-Federation) senaryolarında kullanılan sınıfları içerir. Ayrıca altında ayarlara bazı sınıfları içerir [ \<system.identityModel.services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) öğesi. Bu öğe ayarlarında WS-Federasyon uygulamaları için yapılandırın. `System.IdentityModel.Services.Configuration` Ad alanı, çoğu WS-Federasyon yapılandırmak için kullanılan sınıfları içerir.  
  
 <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>  
 WS-Federasyon protokolünü kullanan WIF uygulamaları için yapılandırma sağlayan sınıflar içerir. Bu ad alanındaki sınıflar ayarlara altında [ \<system.identityModel.services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) öğesi. `System.IdentityModel.Services` Ad alanı da WS-Federasyon yapılandırmak için kullanılan bazı sınıflar içerir.  
  
 <xref:System.IdentityModel.Services.Tokens?displayProperty=nameWithType>  
 Web grubu senaryoları için özel güvenlik belirteci işleyicileri içerir.  
  
 <xref:System.IdentityModel.Tokens?displayProperty=nameWithType>  
 Güvenlik belirteçleri, güvenlik belirteci işleyicileri ve diğer güvenlik belirteci yapıları temsil eden sınıfları içerir.  
  
 <xref:System.Security.Claims?displayProperty=nameWithType>  
 Talepler, talep tabanlı kimlik, talep tabanlı ilkeleri ve diğer talep tabanlı kimlik modeli yapıları temsil eden sınıfları içerir.  
  
 <xref:System.ServiceModel.Security?displayProperty=nameWithType>  
 WCF sözleşmeleri, kanalları, hizmet konakları ve etkin (WS-Trust) senaryolarında kullanılır diğer yapıları temsil eden sınıfları içerir. Bu ad ayrıca Windows Communication Foundation (WCF) özeldir ve WIF tarafından kullanılmayan sınıfları içerir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WIF Yapılandırma Başvurusu](../../../docs/framework/security/wif-configuration-reference.md)  
 [WIF 3.5 ile WIF 4.5 Arasında Ad Alanı Eşleme](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)
