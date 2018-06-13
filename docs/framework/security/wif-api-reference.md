---
title: WIF API Başvurusu
ms.date: 03/30/2017
ms.assetid: a027d902-9314-4bfd-b172-4e81847b1d68
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: f5a38420cf5ddb0a76946d5e44e98e1f39118236
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401693"
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
