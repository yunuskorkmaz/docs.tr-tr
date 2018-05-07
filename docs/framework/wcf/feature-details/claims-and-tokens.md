---
title: Beyanlar ve Belirteçler
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], and tokens
ms.assetid: eff167f3-33f8-483d-a950-aa3e9f97a189
ms.openlocfilehash: 087deeef91367210db936f2976a3846d0279dcba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="claims-and-tokens"></a>Beyanlar ve Belirteçler
Bu konuda, Windows Communication Foundation (WCF) desteklediği varsayılan gelen belirteçleri oluşturur çeşitli talep türleri açıklanmaktadır.  
  
 Kullanarak bir istemci kimlik bilgileri taleplerini inceleyebilirsiniz <xref:System.IdentityModel.Claims.ClaimSet> ve <xref:System.IdentityModel.Claims.Claim> sınıfları. `ClaimSet` Oluşan bir koleksiyon içeren `Claim` nesneleri. Her `Claim` aşağıdaki önemli üyeler içeriyor:  
  
-   <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> Özelliği yapılan talep türünü belirten bir Tekdüzen Kaynak Tanımlayıcısı (URI) döndürür. Örneğin, bir talep türünü bir durumda URI http:schemas.microsoft.com/ws/20005/05/identity/claims/thumprint olan bir sertifikanın parmak izini, olabilir.  
  
-   <xref:System.IdentityModel.Claims.Claim.Right%2A> Özelliği talep sağındaki belirten bir URI döndürür. Önceden tanımlanmış hakları içinde bulunan <xref:System.IdentityModel.Claims.Rights> sınıfı (<xref:System.IdentityModel.Claims.Rights.Identity%2A>, <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>).  
  
-   <xref:System.IdentityModel.Claims.Claim.Resource%2A> Özelliği taleple ilişkili kaynak döndürür.  
  
 Her <xref:System.IdentityModel.Claims.ClaimSet> de sahip bir <xref:System.IdentityModel.Claims.ClaimSet.Issuer%2A> temsil eden özellik <xref:System.IdentityModel.Claims.ClaimSet> , `Issuer`.  
  
## <a name="windows-accounts"></a>Windows hesapları  
 İstemci kimlik bilgilerini elde edilen bir Windows kullanıcı hesabı için burada eşler <xref:System.IdentityModel.Claims.ClaimSet> şu değerlere sahiptir:  
  
-   `Issuer` Statik Windows özellik tarafından döndürülen değer <xref:System.IdentityModel.Claims.ClaimSet> sınıfı.  
  
-   Koleksiyon Taleplerde şunlardır:  
  
    -   A <xref:System.IdentityModel.Claims.Claim> ile bir <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> güvenlik tanımlayıcısı (SID) değerini bir <xref:System.IdentityModel.Claims.Claim.Right%2A> özellik değerinin `Identity`ve bir <xref:System.IdentityModel.Claims.Claim.Resource%2A> gerçek SID değerini döndürür. Bir SID, her kullanıcı için etki alanı denetleyicisi sorunlarını benzersiz bir değerdir. SID, Windows güvenliği ile etkileşim kullanıcıyı tanımlamak için kullanılır.  
  
    -   A <xref:System.IdentityModel.Claims.Claim> ile bir <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> , SID değerini bir <xref:System.IdentityModel.Claims.Claim.Right%2A> , `PossessProperty`ve bir <xref:System.IdentityModel.Claims.Claim.Resource%2A> SID değeri.  
  
    -   A <xref:System.IdentityModel.Claims.Claim> ile bir <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> , <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, <xref:System.IdentityModel.Claims.Claim.Right%2A> , `PossessProperty` ve <xref:System.IdentityModel.Claims.Claim.Resource%2A> (örneğin, "MYMACHINE\Bob") kullanıcı adını içeren dize.  
  
    -   Ek SID taleplerine sahip <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> kullanıcının ait olduğu için çeşitli gruplar.  
  
## <a name="certificates"></a>Sertifikalar  
 İstemci kimlik bilgileri elde edilen bir sertifika olduğu <xref:System.IdentityModel.Claims.ClaimSet> şu değerlere sahiptir:  
  
-   Kendi kendine verilen sertifikalar için `Issuer` olan <xref:System.IdentityModel.Claims.ClaimSet> kendisi. <xref:System.IdentityModel.Claims.ClaimSet> Döndüren bir <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> , <xref:System.IdentityModel.Claims.ClaimTypes.Thumbprint%2A>, <xref:System.IdentityModel.Claims.Claim.Right%2A> , `Identity`ve bir <xref:System.IdentityModel.Claims.Claim.Resource%2A> değeri olan bir <xref:System.Byte> sertifikanın parmak izi içeren bir dizi.  
  
-   Sertifikayı veren sertifika yetkilisi tarafından verilen bir sertifika için olan `ClaimSet` sertifika yetkilisinin sertifikasını temsil eden.  
  
-   `Claims` Koleksiyonda içerir:  
  
    -   A `Claim` ile bir `ClaimType` parmak izi, bir `Right` PossessProperty, ve bir `Resource` diğer bir deyişle sertifikanın parmak izini içeren bir bayt dizisi  
  
    -   Ek PossessProperty talep X500DistinguishedName, Dns, ad, Upn ve Rsa, dahil olmak üzere çeşitli türlerdeki sertifikanın çeşitli özelliklerini temsil eder. Sertifikanın ortak anahtarı Rsa talep için kaynaktır. **Not** istemci kimlik bilgisi türü için bir Windows hizmet eşlemeleri bir sertifika olduğu hesap, iki `ClaimSet` nesneleri oluşturulur. İlk Windows hesabıyla ilişkili tüm talepler ve ikinci sertifikayla ilgili tüm hak talepleri içerir.  
  
## <a name="user-namepassword"></a>Kullanıcı adı/parola  
 İstemci kimlik bilgileri bir kullanıcı adı/parola (veya eşdeğeri) olduğu, eşlenmiyor elde edilen bir Windows hesabı için `ClaimSet` statik tarafından verilen <xref:System.IdentityModel.Claims.ClaimSet.System%2A> özelliği `ClaimSet` sınıfı. `ClaimSet` İçeren bir `Identity` türü talep <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A> istemci kullanıcı adı, kaynak sağlar. Karşılık gelen bir talep sahip bir `Right` , `PossessProperty`.  
  
## <a name="rsa-keys"></a>RSA anahtarları  
 Bir sertifika ile ilişkili olmayan bir RSA anahtarı kullanıldığı elde edilen `ClaimSet` otomatik olarak verilir ve içeren bir `Identity` türü talep <xref:System.IdentityModel.Claims.ClaimTypes.Rsa%2A> RSA anahtarı olan kaynaktır. Karşılık gelen bir talep sahip bir `Right` , `PossessProperty`.  
  
## <a name="saml"></a>SAML  
 İstemci, elde edilen bir güvenlik onaylar biçimlendirme dili (SAML) belirteci burada kimliğini doğrulayan `ClaimSet` genellikle SAML belirtecinde verilen güvenlik belirteci hizmeti (STS) sertifika SAML belirteci imzalayan varlık tarafından verilir. `ClaimSet` İçinde SAML belirteci bulunan çeşitli talepleri içerir. SAML belirteci içeriyorsa bir `SamlSubject` sahip olmayan bir`null` adını, sonra bir `Identity` türü ile talep <xref:System.IdentityModel.Claims.ClaimTypes.NameIdentifier%2A> ve bir kaynak türü <xref:System.IdentityModel.Tokens.SamlNameIdentifierClaimResource> oluşturulur.  
  
## <a name="identity-claims-and-servicesecuritycontextisanonymous"></a>Kimlik talepleri ve ServiceSecurityContext.IsAnonymous  
 Hiçbiri `ClaimSet` istemci kimlik bilgileri kaynaklanan nesneleri içeren bir talebi bir `Right` , `Identity,` sonra <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> özelliği döndürür `true`. Bir veya daha fazla tür talep yoksa `IsAnonymous` özelliği döndürür `false`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IdentityModel.Claims.ClaimSet>  
 <xref:System.IdentityModel.Claims.Claim>  
 <xref:System.IdentityModel.Claims.Rights>  
 <xref:System.IdentityModel.Claims.ClaimTypes>  
 [Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
