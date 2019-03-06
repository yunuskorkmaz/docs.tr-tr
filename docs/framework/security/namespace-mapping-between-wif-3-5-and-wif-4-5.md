---
title: WIF 3.5 ile WIF 4.5 arasında Namespace eşleme
ms.date: 03/30/2017
ms.assetid: a092d98c-444d-4336-a644-63c2e11e96c8
author: BrucePerlerMS
ms.openlocfilehash: ef5801ccfdda22b1c89c22ea9c2b14ea0855ed26
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352795"
---
# <a name="namespace-mapping-between-wif-35-and-wif-45"></a>WIF 3.5 ile WIF 4.5 arasında Namespace eşleme

.NET 4.5 ile başlayarak, Windows Identity Foundation (WIF), tam olarak .NET Framework'e tümleştirilmiştir. Bu tümleştirme, ad değişiklikleri ve bazı birleştirilmesi WIF ad alanları ve API yüzeyi oluşturmuştur. Bu konu, rehberlik ve ad alanlarının WIF 3.5 ile WIF 4.5 ad alanları arasındaki genel bir eşleme sağlar. Kapsamlı, ancak yerine bazı tanıdık WIF 3.5 sınıflar WIF 4.5 içinde nerede bulunacağı hakkında genel bilgileri sağlamak için tasarlanmamıştır. WIF 3.5 ile WIF 4.5 arasındaki farklar hakkında daha ayrıntılı bilgi için bkz: [Windows Identity Foundation 4. 5'deki yenilikler](../../../docs/framework/security/whats-new-in-wif.md). WIF 3.5 to WIF 4.5 kullanılarak oluşturulan bir uygulama geçirme hakkında yönergeler için bkz. [WIF 4.5 için bir Application Built Using WIF 3.5 geçirme yönergeleri](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md).

## <a name="wif-35-to-wif-45-namespace-map"></a>WIF 3.5 ile WIF 4.5 Namespace haritasının

Altında toplanan WIF sınıfları `Microsoft.IdentityModel` WIF 3.5, ad alanları artık aşağıdaki ad alanları arasında dağıtılan: `System.Security.Claims`, `System.ServiceModel.Security`ve `System.IdentityModel` WIF 4.5 ad alanları. Ayrıca bazı WIF 3.5 ad alanları, birleşik veya tamamen WIF 4.5 içinde bırakıldı.

> [!IMPORTANT]
> Aşağıdaki `System.IdentityModel` WCF beyana dayalı kimlik modeli uygulayan sınıflar ad alanlarında bulunur: <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType>, ve <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>. WCF beyana dayalı kimlik modelinin yerini WIF almıştır. Sınıfları bu üç ad alanı üzerinde WIF tabanlı çözümler oluştururken kullanmamanız gerekir.

Aşağıdaki tabloda, WIF 3.5 sınıflar WIF 4.5 içinde bulunabileceği hakkında bilgi sağlar.

|**WIF 3.5 Namespace**|**WIF 4.5 Namespace**|**Açıklamalar**|
|-|-|-|
|`Microsoft.IdentityModel`|<xref:System.IdentityModel?displayProperty=nameWithType>|-Sabitleri temsil eden sınıfları çoğunu uygulanmadı.<br />-Gelen güvenlik belirteci hizmetleri oluşturmak için kullanılan sınıflar taşınmış `Microsoft.IdentityModel.SecurityTokenService` için <xref:System.IdentityModel?displayProperty=nameWithType>.<br />-Sınıflarda `Microsoft.IdentityModel.Threading` taşındı <xref:System.IdentityModel?displayProperty=nameWithType>.<br />- `ExceptionMapper` Ve `MruSecurityTokenCache` sınıfları uygulanmadı.|
|`Microsoft.IdentityModel.Claims`|<xref:System.Security.Claims?displayProperty=nameWithType>|- `IClaimsPrincipal` Ve `IClaimsIdentity` arabirimleri WIF 4. 5 ' uygulanmamıştır. Bunun yerine <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType> ve <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> artık çoğu .NET temel sınıfların asıl ve kimlik sınıflar türetilir. Bu asıl ve kimlik sınıflar gibi özel talepler için gerek yoktur anlamına gelir `Microsoft.IdentityModel.Claims.WindowsClaimsPrincipal` ve `Microsoft.IdentityModel.Claims.WindowsClaimsIdentity` WIF 4.5 içinde kullanma <xref:System.Security.Principal.WindowsPrincipal?displayProperty=nameWithType> ve <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType> yerine. Aynı diğer WIF 3.5 var olan diğer özel talep sorumlusu ve kimlik sınıflar için geçerlidir.<br />- `Microsoft.IdentityModel.Claims.ClaimsCollection` Sınıfı WIF 4. 5 ' uygulanmamıştır. Bunun yerine, koleksiyonları talep numaralandırılabilir koleksiyon türü olarak sunulan <xref:System.Security.Claims.Claim?displayProperty=nameWithType>.<br />-   <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType> ve <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> artık tam olarak LINQ destekleyen yöntemler sağlar.|
|`Microsoft.IdentityModel.Configuration`|<xref:System.IdentityModel.Configuration?displayProperty=nameWithType>|Bazı öğeleri ve sınıfları ad değişiklikleri yapılmıştır ve bazı WIF 4.5 içinde bırakıldı; Örneğin `Microsoft.IdentityModel.Configuration.ServiceConfiguration` artık <xref:System.IdentityModel.Configuration.IdentityConfiguration?displayProperty=nameWithType>.|
|`Microsoft.IdentityModel.Protocols`|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Protocols.WSFederation`|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Protocols.WSFederation.Metadata`|<xref:System.IdentityModel.Metadata?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Protocols.WSIdentity`|WIF 4.5 uygulanmadı|WIF 3.5 CardSpace, WIF 4.5 içinde uygulanmadı desteklemek için sınıflar içeriyor.|
|`Microsoft.IdentityModel.Protocols.WSTrust`|Arasında bölünür <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType> ve <xref:System.ServiceModel.Security?displayProperty=nameWithType> ad alanları.|WS-Trust yapıları temsil eden sınıflar bulunduğunuz <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType> ad alanı; Örneğin, <xref:System.IdentityModel.Protocols.WSTrust.RequestSecurityToken> sınıfı. WCF hizmet sözleşmeleri, hizmet konakları ve WS-Güven protokolünü kullanarak iletişim kurmak bir WCF hizmetini etkinleştirme kanalları temsil eden sınıfları bulunduğunuz <xref:System.ServiceModel.Security?displayProperty=nameWithType> ad alanı; Örneğin, <xref:System.ServiceModel.Security.WSTrustServiceHost> sınıfı.|
|`Microsoft.IdentityModel.Protocols.WSTrust.Bindings`|WIF 4.5 uygulanmadı|-|
|`Microsoft.IdentityModel.Protocols.XmlEncryption`|WIF 4.5 uygulanmadı|WIF 3.5 XML şifreleme sabitlerle temsil eden sınıflar içeriyor. Bu sabiti WIF 4. 5 ' uygulanmamıştır.|
|`Microsoft.IdentityModel.Protocols.XmlSignature`|<xref:System.IdentityModel?displayProperty=nameWithType>|`EnvelopingSignature` Sınıfı ve sabitleri temsil eden sınıfları uygulanmadı.|
|`Microsoft.IdentityModel.SecurityTokenService`|Arasında bölünür <xref:System.IdentityModel?displayProperty=nameWithType>, <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>, ve <xref:System.IdentityModel.Tokens?displayProperty=nameWithType> ad alanları.|-|
|`Microsoft.IdentityModel.Threading`|<xref:System.IdentityModel?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Tokens`|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Tokens.Saml11`|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Tokens.Saml2`|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Web`|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Web.Configuration`|<xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>|Pasif (WS-Federation) senaryoları için büyük ölçüde taşınmış için yapılandırma sağlayan sınıflar <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>; ancak, bu sınıfların bazıları bulunan <xref:System.IdentityModel.Services?displayProperty=nameWithType>.|
|`Microsoft.IdentityModel.Web.Controls`|WIF 4.5 uygulanmadı|Sınıflarda `Microsoft.IdentityModel.Web.Controls` Federasyon pasif oturum WIF 4. 5 ' bulunmayan denetimi uygulanır.|
|`Microsoft.IdentityModel.WindowsTokenService`|WIF 4.5 uygulanmadı|-|

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Identity Foundation 4.5'teki Yenilikler](../../../docs/framework/security/whats-new-in-wif.md)
- [WIF 3.5 Kullanılarak Derlenmiş bir Uygulamayı WIF 4.5’e Geçirme Yönergeleri](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md)
