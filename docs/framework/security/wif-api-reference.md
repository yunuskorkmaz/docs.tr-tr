---
title: WIF API Başvurusu
ms.date: 03/30/2017
ms.assetid: a027d902-9314-4bfd-b172-4e81847b1d68
author: BrucePerlerMS
ms.openlocfilehash: fd7f34e619626ddca63074a89ec7253fd818ab55
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045146"
---
# <a name="wif-api-reference"></a>WIF API Başvurusu
Windows Identity Foundation `mscorlib` (WIF) sınıfları şu derlemeler arasında bölünür: (mscorlib. dll), `System.IdentityModel` (System. IdentityModel. dll), `System.IdentityModel.Services` (System. IdentityModel. Services. dll) ve `System.ServiceModel` ( System. ServiceModel. dll). Bu konuda, WıF ad alanları ve her bir ad alanının içerdiği sınıfların kısa açıklamaları için bağlantılar sağlanmaktadır.  
  
> [!IMPORTANT]
> Aşağıdaki `System.IdentityModel` ad alanlarında, WCF talep tabanlı kimlik modelini uygulayan sınıflar bulunur: <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType>, ve <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>. .NET Framework 4,5 ' den başlayarak, WCF talep tabanlı kimlik modelinin yerini WıF almıştır. WıF tabanlı çözümler oluştururken bu üç ad alanında sınıfları kullanmamalısınız.  
  
 <xref:System.IdentityModel?displayProperty=nameWithType>  
 Tanımlama bilgisi dönüştürmeleri, güvenlik belirteci Hizmetleri ve özelleşmiş XML sözlüğü okuyucuları temsil eden sınıflar içerir.  
  
 <xref:System.IdentityModel.Configuration?displayProperty=nameWithType>  
 Windows Identity Foundation (WıF) kullanılarak oluşturulan uygulamalar ve hizmetler için yapılandırma sağlayan sınıfları içerir. Bu ad alanındaki sınıflar, [ \<IdentityConfiguration >](../configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi altındaki ayarları temsil eder.  
  
 <xref:System.IdentityModel.Metadata?displayProperty=nameWithType>  
 Federasyon meta veri belgesindeki öğeleri temsil eden sınıfları içerir.  
  
 <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>  
 WS-Trust yapılarını temsil eden sınıfları içerir.  
  
 <xref:System.IdentityModel.Services?displayProperty=nameWithType>  
 Pasif (WS-Federation) senaryolarında kullanılan sınıfları içerir. Ayrıca [ \<System. IdentityModel. Services >](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) öğesi altındaki ayarları temsil eden bazı sınıflar içerir. Bu öğenin altındaki ayarlar, uygulamalar için WS-Federation ' i yapılandırır. Ad `System.IdentityModel.Services.Configuration` alanı, WS-Federation ' i yapılandırmak için kullanılan sınıfların çoğunu içerir.  
  
 <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>  
 WS-Federation protokolünü kullanan WıF uygulamaları için yapılandırma sağlayan sınıfları içerir. Bu ad alanındaki sınıflar, [ \<System. IdentityModel. Services >](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) öğesi altındaki ayarları temsil eder. Ad `System.IdentityModel.Services` alanı, WS-Federation yapılandırmak için kullanılan bazı sınıfları da içerir.  
  
 <xref:System.IdentityModel.Services.Tokens?displayProperty=nameWithType>  
 Web grubu senaryoları için özelleştirilmiş güvenlik belirteci işleyicileri içerir.  
  
 <xref:System.IdentityModel.Tokens?displayProperty=nameWithType>  
 Güvenlik belirteçlerini, güvenlik belirteci işleyicilerini ve diğer güvenlik belirteci yapıtlarını temsil eden sınıflar içerir.  
  
 <xref:System.Security.Claims?displayProperty=nameWithType>  
 Talepleri, talep tabanlı kimlikleri, talep tabanlı sorumluları ve diğer talep tabanlı kimlik modeli yapılarını temsil eden sınıflar içerir.  
  
 <xref:System.ServiceModel.Security?displayProperty=nameWithType>  
 WCF sözleşmelerini, kanalları, hizmet ana bilgisayarlarını ve etkin (WS-Trust) senaryolarında kullanılan diğer yapıtları temsil eden sınıflar içerir. Bu ad alanı Ayrıca, Windows Communication Foundation (WCF) öğesine özgü ve WıF tarafından kullanılmayan sınıfları da içerir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WIF Yapılandırma Başvurusu](wif-configuration-reference.md)
- [WIF 3.5 ile WIF 4.5 Arasında Ad Alanı Eşleme](namespace-mapping-between-wif-3-5-and-wif-4-5.md)
