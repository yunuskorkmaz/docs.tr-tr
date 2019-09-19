---
title: WIF 3.5 ile WIF 4.5 Arasında Ad Alanı Eşleme
ms.date: 03/30/2017
ms.assetid: a092d98c-444d-4336-a644-63c2e11e96c8
author: BrucePerlerMS
ms.openlocfilehash: d967ce931e81ca14645e7464943e1411264d6ca2
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045411"
---
# <a name="namespace-mapping-between-wif-35-and-wif-45"></a>WIF 3.5 ile WIF 4.5 Arasında Ad Alanı Eşleme

.NET 4,5 ile başlayarak, Windows Identity Foundation (WıF) .NET Framework ile tamamen tümleşiktir. Bu tümleştirme, ad değişikliklerini ve WıF ad alanlarının ve API yüzeyinin bazı konsolidasyonlarından oluşur. Bu konuda, WıF 3,5 ad alanları ile WıF 4,5 ad alanları arasında bazı kılavuzluk ve genel eşleme sağlanmaktadır. Kapsamlı olmak üzere tasarlanmamıştır, ancak bunun yerine WıF 4,5 ' de tanıdık WıF 3,5 sınıflarının nerede bulunacağı hakkında genel bilgiler sağlanmaktadır. WıF 3,5 ile WıF 4,5 arasındaki farklar hakkında daha ayrıntılı bilgi için bkz. [Windows Identity Foundation 4,5 'daki](whats-new-in-wif.md)yenilikler. WIF 3,5 kullanılarak oluşturulan uygulamaların WıF 4,5 ' ye nasıl geçirileceği hakkında yönergeler için bkz. [wıf 3,5 kullanılarak oluşturulan bir uygulamayı wıf 4,5 ' e geçirmeye yönelik yönergeler](guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md).

## <a name="wif-35-to-wif-45-namespace-map"></a>WıF 3,5-WıF 4,5 ad alanı eşlemesi

WIF 3,5 ' `Microsoft.IdentityModel` deki ad alanları altında toplanan WIF sınıfları artık şu ad alanları arasında dağıtılır: `System.Security.Claims`, `System.ServiceModel.Security`ve `System.IdentityModel` WIF 4,5 içindeki ad alanları. Ayrıca, bazı WıF 3,5 ad alanları birleştirilir veya tamamen WıF 4,5 ' de bırakılmıştı.

> [!IMPORTANT]
> Aşağıdaki `System.IdentityModel` ad alanlarında, WCF talep tabanlı kimlik modelini uygulayan sınıflar bulunur: <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType>, ve <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>. WCF beyana dayalı kimlik modelinin yerini WIF almıştır. WıF tabanlı çözümler oluştururken bu üç ad alanında sınıfları kullanmamalısınız.

Aşağıdaki tabloda, WIF 3,5 sınıflarının WıF 4,5 ' de bulunabileceği durumlar hakkında bilgi verilmektedir.

|**WıF 3,5 ad alanı**|**WıF 4,5 ad alanı**|**Açıklamalar**|
|-|-|-|
|`Microsoft.IdentityModel`|<xref:System.IdentityModel?displayProperty=nameWithType>|-Sabitleri temsil eden sınıfların çoğu uygulanmaz.<br />-Güvenlik belirteci Hizmetleri oluşturmak için kullanılan sınıflar sürümünden `Microsoft.IdentityModel.SecurityTokenService` öğesine <xref:System.IdentityModel?displayProperty=nameWithType>taşınmıştır.<br />-İçindeki `Microsoft.IdentityModel.Threading` sınıflar öğesine <xref:System.IdentityModel?displayProperty=nameWithType>taşındı.<br />`ExceptionMapper` -Ve `MruSecurityTokenCache` sınıfları uygulanmadı.|
|`Microsoft.IdentityModel.Claims`|<xref:System.Security.Claims?displayProperty=nameWithType>|`IClaimsPrincipal` -Ve `IClaimsIdentity` arabirimleri WIF 4,5 ' de uygulanmaz. Bunun yerine <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType> , en fazla .net sorumlusu ve kimlik sınıfının türettikleri temel sınıflardır. <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> Bu, WIF `Microsoft.IdentityModel.Claims.WindowsClaimsPrincipal` 4,5 gibi `Microsoft.IdentityModel.Claims.WindowsClaimsIdentity` özel talep sorumlusu ve kimlik sınıfları için gerek olmadığı anlamına gelir, bunun yerine ve <xref:System.Security.Principal.WindowsPrincipal?displayProperty=nameWithType> <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType> kullanın. Aynı, diğer özel talep sorumlusu ve WıF 3,5 ' de var olan kimlik sınıfları için de geçerlidir.<br />`Microsoft.IdentityModel.Claims.ClaimsCollection` -Sınıf WIF 4,5 ' de uygulanmaz. Bunun yerine, talep koleksiyonları türünde <xref:System.Security.Claims.Claim?displayProperty=nameWithType>sıralanabilir koleksiyonlar olarak sunulur.<br />-   <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>ve <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> artık LINQ 'i tam olarak destekleyen yöntemler sağlar.|
|`Microsoft.IdentityModel.Configuration`|<xref:System.IdentityModel.Configuration?displayProperty=nameWithType>|Bazı öğeler ve sınıflar, değiştirilmiş ad değişikliklerine sahiptir ve bazıları WıF 4,5 ' de bırakılmıştı; Örneğin `Microsoft.IdentityModel.Configuration.ServiceConfiguration` , şu anda <xref:System.IdentityModel.Configuration.IdentityConfiguration?displayProperty=nameWithType>.|
|`Microsoft.IdentityModel.Protocols`|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Protocols.WSFederation`|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Protocols.WSFederation.Metadata`|<xref:System.IdentityModel.Metadata?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Protocols.WSIdentity`|WıF 4,5 ' de uygulanmadı|WıF 3,5 içinde, CardSpace 'i desteklemek için sınıflar bulunur ve WıF 4,5 ' de uygulanmaz.|
|`Microsoft.IdentityModel.Protocols.WSTrust`|<xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType> Ve<xref:System.ServiceModel.Security?displayProperty=nameWithType> ad alanları arasında bölme.|WS-Trust yapıtları <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType> temsil eden sınıflar ad uzayında; örneğin <xref:System.IdentityModel.Protocols.WSTrust.RequestSecurityToken> , sınıfı. WCF hizmeti sözleşmelerini, hizmet ana bilgisayarlarını ve bir WCF hizmetinin WS-Trust protokolünü kullanarak iletişim kurmasını sağlayan kanalları temsil eden sınıflar, <xref:System.ServiceModel.Security?displayProperty=nameWithType> ad alanında yer alır; örneğin <xref:System.ServiceModel.Security.WSTrustServiceHost> , sınıfı.|
|`Microsoft.IdentityModel.Protocols.WSTrust.Bindings`|WıF 4,5 ' de uygulanmadı|-|
|`Microsoft.IdentityModel.Protocols.XmlEncryption`|WıF 4,5 ' de uygulanmadı|WıF 3,5 ' deki XML şifreleme sabitlerini temsil eden sınıflar içerir. Bu sabitler WıF 4,5 ' de uygulanmaz.|
|`Microsoft.IdentityModel.Protocols.XmlSignature`|<xref:System.IdentityModel?displayProperty=nameWithType>|Sabitleri temsil eden sınıf ve sınıflar uygulanmaz. `EnvelopingSignature`|
|`Microsoft.IdentityModel.SecurityTokenService`|<xref:System.IdentityModel?displayProperty=nameWithType> ,<xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>Ve ad<xref:System.IdentityModel.Tokens?displayProperty=nameWithType> alanları arasında bölme.|-|
|`Microsoft.IdentityModel.Threading`|<xref:System.IdentityModel?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Tokens`|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Tokens.Saml11`|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Tokens.Saml2`|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Web`|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|-|
|`Microsoft.IdentityModel.Web.Configuration`|<xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>|Pasif (WS-Federation) senaryoları için yapılandırma sağlayan sınıflar, büyük ölçüde öğesine <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>taşınmıştır; ancak, bu sınıflardan bazıları içinde <xref:System.IdentityModel.Services?displayProperty=nameWithType>bulunur.|
|`Microsoft.IdentityModel.Web.Controls`|WıF 4,5 ' de uygulanmadı|İçindeki `Microsoft.IdentityModel.Web.Controls` sınıflar, WIF 4,5 ' de bulunmayan Federal pasif oturum açma denetimini uyguladık.|
|`Microsoft.IdentityModel.WindowsTokenService`|WıF 4,5 ' de uygulanmadı|-|

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Identity Foundation 4.5'teki Yenilikler](whats-new-in-wif.md)
- [WIF 3.5 Kullanılarak Derlenmiş bir Uygulamayı WIF 4.5’e Geçirme Yönergeleri](guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md)
