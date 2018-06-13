---
title: WIF 3.5 ve WIF 4.5 arasında Namespace eşleme
ms.date: 03/30/2017
ms.assetid: a092d98c-444d-4336-a644-63c2e11e96c8
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: a120347d20de5b881ccb60d03da482856d9e68a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407988"
---
# <a name="namespace-mapping-between-wif-35-and-wif-45"></a>WIF 3.5 ve WIF 4.5 arasında Namespace eşleme
.NET 4. 5'ile başlayan, Windows Identity Foundation (WIF), tam olarak .NET Framework'e tümleştirilmiştir. Bu tümleştirme ad değişikliklerini ve bazı WIF ad alanları ve API yüzeyi birleştirilmesi oluşturmuştur. Bu konu, bazı yönergeler ve WIF 3.5 ad alanları ve WIF 4.5 ad alanları arasında genel bir eşleme sağlar. Kapsamlı, ancak yerine tanıdık WIF 3.5 sınıfları WIF 4.5 nerede bulacağını ilgili bazı genel bilgileri sağlamak üzere tasarlanmamıştır. WIF 3.5 ve WIF 4.5 arasındaki farklar hakkında daha ayrıntılı bilgi için bkz: [Windows Identity Foundation 4. 5'de](../../../docs/framework/security/whats-new-in-wif.md). WIF 4.5 WIF 3.5 kullanılarak oluşturulan bir uygulamalar geçirme hakkında yönergeler için bkz [bir uygulama yerleşik kullanarak WIF 3.5 WIF 4.5 sürümüne geçirmek için yönergeler](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md).  
  
## <a name="wif-35-to-wif-45-namespace-map"></a>WIF 4.5 Namespace harita WIF 3.5  
 Altında toplanan WIF sınıfları `Microsoft.IdentityModel` WIF 3.5, ad alanları artık aşağıdaki ad alanları arasında dağıtılan: `System.Security.Claims`, `System.ServiceModel.Security`ve `System.IdentityModel` WIF 4.5 ad alanları. Ayrıca bazı WIF 3.5 ad alanları birleştirilmiş veya tamamen WIF 4.5 bırakıldı.  
  
> [!IMPORTANT]
>  Aşağıdaki `System.IdentityModel` ad alanları içeren WCF beyana dayalı kimlik modelinde uygulayan sınıflar: <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType>, ve <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>. WCF beyana dayalı kimlik modelinin yerini WIF almıştır. Sınıflar bu üç ad alanlarında WIF tabanlı çözümler oluştururken kullanmamanız gerekir.  
  
 Aşağıdaki tabloda WIF 4.5 WIF 3.5 sınıfları bulunabileceği hakkında bilgi sağlar.  
  
|**WIF 3.5 Namespace**|**WIF 4.5 Namespace**|**Açıklamalar**|  
|-|-|-|  
|`Microsoft.IdentityModel`|<xref:System.IdentityModel?displayProperty=nameWithType>|-Sabitleri temsil eden sınıflar çoğunu uygulanmadı.<br />-Güvenlik belirteci hizmetleri oluşturmak için kullanılan sınıfları gelen taşınmış `Microsoft.IdentityModel.SecurityTokenService` için <xref:System.IdentityModel?displayProperty=nameWithType>.<br />-Sınıflarda `Microsoft.IdentityModel.Threading` taşınmıştır <xref:System.IdentityModel?displayProperty=nameWithType>.<br />- `ExceptionMapper` Ve `MruSecurityTokenCache` sınıfları uygulanmadı.|  
|`Microsoft.IdentityModel.Claims`|<xref:System.Security.Claims?displayProperty=nameWithType>|- `IClaimsPrincipal` Ve `IClaimsIdentity` arabirimleri WIF 4.5 uygulanmadı. Bunun yerine <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType> ve <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> çoğu hangi .NET temel sınıflardan asıl sunulmuştur ve kimlik sınıflar türetilir. Bu asıl ve kimlik sınıflar gibi özelleştirilmiş talepler için gerekli olduğu anlamına gelir `Microsoft.IdentityModel.Claims.WindowsClaimsPrincipal` ve `Microsoft.IdentityModel.Claims.WindowsClaimsIdentity` WIF 4.5 içinde kullanmak <xref:System.Security.Principal.WindowsPrincipal?displayProperty=nameWithType> ve <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType> yerine. Aynı diğer WIF 3.5 var olan diğer özel talep asıl ve kimlik sınıflar için geçerlidir.<br />- `Microsoft.IdentityModel.Claims.ClaimsCollection` Sınıfı WIF 4.5 uygulanmadı. Bunun yerine, talep koleksiyonları numaralandırılabilir koleksiyon türü olarak sunulan <xref:System.Security.Claims.Claim?displayProperty=nameWithType>.<br />-   <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType> ve <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> şimdi LINQ tam destek yöntemleri sağlar.|  
|`Microsoft.IdentityModel.Configuration`|<xref:System.IdentityModel.Configuration?displayProperty=nameWithType>|Bazı öğeler ve sınıf adı değişiklikler yapılması ve bazı WIF 4.5 bırakıldı; Örneğin `Microsoft.IdentityModel.Configuraiton.ServiceConfiguration` artık <xref:System.IdentityModel.Configuration.IdentityConfiguration?displayProperty=nameWithType>.|  
|`Microsoft.IdentityModel.Protocols`|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|-|  
|`Microsoft.IdentityModel.Protocols.WSFederation`|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|-|  
|`Microsoft.IdentityModel.Protocols.WSFederation.Metadata`|<xref:System.IdentityModel.Metadata?displayProperty=nameWithType>|-|  
|`Microsoft.IdentityModel.Protocols.WSIdentity`|WIF 4.5 uygulanmadı|WIF 3.5 WIF 4.5 uygulanmadı CardSpace desteklemek için sınıflar içeriyor.|  
|`Microsoft.IdentityModel.Protocols.WSTrust`|Arasında bölme <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType> ve <xref:System.ServiceModel.Security?displayProperty=nameWithType> ad alanları.|WS-Trust yapıları temsil eden sınıfları olan <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType> ad alanı; Örneğin, <xref:System.IdentityModel.Protocols.WSTrust.RequestSecurityToken> sınıfı. WCF hizmet sözleşmelerini, hizmet konakları ve WS-Trust protokolünü kullanarak iletişim kurmak bir WCF hizmeti etkinleştirmek kanalları temsil eden sınıflar olan <xref:System.ServiceModel.Security?displayProperty=nameWithType> ad alanı; Örneğin, <xref:System.ServiceModel.Security.WSTrustServiceHost> sınıfı.|  
|`Microsoft.IdentityModel.Protocols.WSTrust.Bindings`|WIF 4.5 uygulanmadı|-|  
|`Microsoft.IdentityModel.Protocols.XmlEncryption`|WIF 4.5 uygulanmadı|XML şifrelemesi sabitleri WIF 3.5 temsil eden sınıflar içeriyor. Bu sabitleri WIF 4.5 uygulanmadı.|  
|`Microsoft.IdentityModel.Protocols.XmlSignature`|<xref:System.IdentityModel?displayProperty=nameWithType>|`EnvelopingSignature` Sınıfı ve sabitleri temsil eden sınıflar uygulanmadı.|  
|`Microsoft.IdentityModel.SecurityTokenService`|Arasında bölme <xref:System.IdentityModel?displayProperty=nameWithType>, <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>, ve <xref:System.IdentityModel.Tokens?displayProperty=nameWithType> ad alanları.|-|  
|`Microsoft.IdentityModel.Threading`|<xref:System.IdentityModel?displayProperty=nameWithType>|-|  
|`Microsoft.IdentityModel.Tokens`|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|-|  
|`Microsoft.IdentityModel.Tokens.Saml11`|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|-|  
|`Microsoft.IdentityModel.Tokens.Saml2`|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|-|  
|`Microsoft.IdentityModel.Web`|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|-|  
|`Microsoft.IdentityModel.Web.Configuration`|<xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>|Pasif (WS-Federation) senaryoları için büyük ölçüde taşınmış için yapılandırma sağlayan sınıflar <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>; ancak, bu sınıfların bazıları bulunan <xref:System.IdentityModel.Services?displayProperty=nameWithType>.|  
|`Microsoft.IdentityModel.Web.Controls`|WIF 4.5 uygulanmadı|Sınıflarda `Microsoft.IdentityModel.Web.Controls` Federasyon pasif oturum açma, WIF 4.5 yok denetimi uygulanmadı.|  
|`Microsoft.IdentityModel.WindowsTokenService`|WIF 4.5 uygulanmadı|-|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Identity Foundation 4.5'teki Yenilikler](../../../docs/framework/security/whats-new-in-wif.md)  
 [WIF 3.5 Kullanılarak Derlenmiş bir Uygulamayı WIF 4.5’e Geçirme Yönergeleri](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md)
