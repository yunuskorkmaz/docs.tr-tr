---
title: Beyanlar ve Belirteçler
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], and tokens
ms.assetid: eff167f3-33f8-483d-a950-aa3e9f97a189
ms.openlocfilehash: 21172ccda5f5f8070d81726d5f4dc6f9d80ab071
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569013"
---
# <a name="claims-and-tokens"></a>Beyanlar ve Belirteçler
Bu konu, Windows Communication Foundation (WCF) desteklediği varsayılan belirteçleri oluşturan çeşitli talep türlerini açıklar.  
  
 Kullanarak bir istemci kimlik bilgileri taleplerini inceleyebilirsiniz <xref:System.IdentityModel.Claims.ClaimSet> ve <xref:System.IdentityModel.Claims.Claim> sınıfları. `ClaimSet` Koleksiyonunu içeren `Claim` nesneleri. Her `Claim` aşağıdaki önemli üyeleri içerir:  
  
-   <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> Özelliği yapılan talep türünü belirten bir Tekdüzen Kaynak Tanımlayıcısı (URI) döndürür. Örneğin, bir talep türü URI durumda olduğu bir sertifika parmak izi olabilir `http://schemas.microsoft.com/ws/20005/05/identity/claims/thumprint`.  
  
-   <xref:System.IdentityModel.Claims.Claim.Right%2A> Özelliği talep sağındaki belirten bir URI döndürür. Önceden tanımlanmış hakları bulunur <xref:System.IdentityModel.Claims.Rights> sınıfı (<xref:System.IdentityModel.Claims.Rights.Identity%2A>, <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>).  
  
-   <xref:System.IdentityModel.Claims.Claim.Resource%2A> Taleple ilişkili kaynak özelliğini döndürür.  
  
 Her <xref:System.IdentityModel.Claims.ClaimSet> de sahip bir <xref:System.IdentityModel.Claims.ClaimSet.Issuer%2A> temsil eden özellik <xref:System.IdentityModel.Claims.ClaimSet> , `Issuer`.  
  
## <a name="windows-accounts"></a>Windows hesapları  
 İstemci kimlik bilgilerini ortaya çıkan bir Windows kullanıcı hesabı için burada eşler <xref:System.IdentityModel.Claims.ClaimSet> aşağıdaki değerlere sahip:  
  
-   `Issuer` Statik Windows özelliği tarafından döndürülen değer <xref:System.IdentityModel.Claims.ClaimSet> sınıfı.  
  
-   Koleksiyon Taleplerde şunlardır:  
  
    -   A <xref:System.IdentityModel.Claims.Claim> ile bir <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> güvenlik tanımlayıcısı (SID) değerini bir <xref:System.IdentityModel.Claims.Claim.Right%2A> özelliği değerinin `Identity`ve <xref:System.IdentityModel.Claims.Claim.Resource%2A> gerçek SID değerini döndürür. SID, her kullanıcı için etki alanı denetleyicisi sorunları benzersiz bir değerdir. SID, Windows Güvenlik ile etkileşim içinde kullanıcıyı tanımlamak için kullanılır.  
  
    -   A <xref:System.IdentityModel.Claims.Claim> ile bir <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> SID, değeri bir <xref:System.IdentityModel.Claims.Claim.Right%2A> , `PossessProperty`ve <xref:System.IdentityModel.Claims.Claim.Resource%2A> SID değeri.  
  
    -   A <xref:System.IdentityModel.Claims.Claim> ile bir <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> , <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, <xref:System.IdentityModel.Claims.Claim.Right%2A> , `PossessProperty` ve <xref:System.IdentityModel.Claims.Claim.Resource%2A> kullanıcı adını (örneğin, "MYMACHINE\Bob") içeren bir dize.  
  
    -   Ek SID taleplerinden ile <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> kullanıcının ait olduğu için çeşitli gruplar.  
  
## <a name="certificates"></a>Sertifikalar  
 İstemci kimlik bilgileri elde edilen, bir sertifika olduğu <xref:System.IdentityModel.Claims.ClaimSet> aşağıdaki değerlere sahip:  
  
-   Şirket içinde verilen sertifikalara `Issuer` olduğu <xref:System.IdentityModel.Claims.ClaimSet> kendisi. <xref:System.IdentityModel.Claims.ClaimSet> Döndürür bir <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> , <xref:System.IdentityModel.Claims.ClaimTypes.Thumbprint%2A>, <xref:System.IdentityModel.Claims.Claim.Right%2A> , `Identity`ve <xref:System.IdentityModel.Claims.Claim.Resource%2A> değeri olan bir <xref:System.Byte> sertifikanın parmak izini içeren bir dizi.  
  
-   Sertifikayı veren sertifika yetkilisi tarafından verilmiş bir sertifika için olan `ClaimSet` sertifika yetkilisinin sertifikayı temsil eden.  
  
-   `Claims` Koleksiyona dahil:  
  
    -   A `Claim` ile bir `ClaimType` parmak izi, bir `Right` PossessProperty, ve `Resource` diğer bir deyişle sertifikanın parmak izini içeren bir bayt dizisi  
  
    -   Ek PossessProperty talep X500DistinguishedName, Dns, ad, Upn ve Rsa, dahil olmak üzere çeşitli türlerde sertifikanın çeşitli özelliklerini temsil eder. Sertifikanın ortak anahtarı için Rsa talep kaynaktır. **Not** istemci kimlik bilgisi türü için bir Windows hizmet eşlemeleri bir sertifika olduğu hesap, iki `ClaimSet` nesneleri oluşturulur. İlk Windows hesapla ilgili tüm talepleri içeren ve ikinci sertifikayı ilgili tüm talepleri içerir.  
  
## <a name="user-namepassword"></a>Kullanıcı adı/parola  
 İstemci kimlik bilgilerini bir kullanıcı adı/parola (veya eşdeğeri) olduğu, eşlenmiyor ortaya çıkan bir Windows hesabı `ClaimSet` statik tarafından verilen <xref:System.IdentityModel.Claims.ClaimSet.System%2A> özelliği `ClaimSet` sınıfı. `ClaimSet` İçeren bir `Identity` türü talep <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A> istemci kullanıcı adı, kaynak sağlar. Karşılık gelen bir talep sahip bir `Right` , `PossessProperty`.  
  
## <a name="rsa-keys"></a>RSA anahtarları  
 Bir sertifika ile ilişkili olmayan bir RSA anahtarı kullanıldığı ortaya çıkan `ClaimSet` Self verilir ve içeren bir `Identity` türü talep <xref:System.IdentityModel.Claims.ClaimTypes.Rsa%2A> RSA anahtarı olan bir kaynaktır. Karşılık gelen bir talep sahip bir `Right` , `PossessProperty`.  
  
## <a name="saml"></a>SAML  
 İstemci güvenlik onaylama işaretleme dili (SAML) belirteci elde edilen bir burada kimlik doğrulaması `ClaimSet` genellikle SAML belirtecinde verilen güvenlik belirteci hizmeti (STS) sertifikasını SAML belirteci imzalayan varlık tarafından verilir. `ClaimSet` SAML belirtecinde bulunan çeşitli talepleri içerir. SAML belirteci içerirse bir `SamlSubject` sahip olmayan bir`null` adını ardından bir `Identity` talep türü ile <xref:System.IdentityModel.Claims.ClaimTypes.NameIdentifier%2A> ve kaynak türü <xref:System.IdentityModel.Tokens.SamlNameIdentifierClaimResource> oluşturulur.  
  
## <a name="identity-claims-and-servicesecuritycontextisanonymous"></a>Kimlik talepleri ve ServiceSecurityContext.IsAnonymous  
 Hiçbiri `ClaimSet` istemci kimlik bilgileri kaynaklanan nesneleri içeren bir talep ile bir `Right` , `Identity,` sonra <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> özelliği döndürür `true`. Bir veya daha fazla tür talep varsa `IsAnonymous` özelliği döndürür `false`.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.IdentityModel.Claims.ClaimSet>
- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- [Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
