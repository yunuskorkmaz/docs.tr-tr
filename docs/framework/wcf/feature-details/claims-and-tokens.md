---
title: Beyanlar ve Belirteçler
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], and tokens
ms.assetid: eff167f3-33f8-483d-a950-aa3e9f97a189
ms.openlocfilehash: cbc97f2224bce640757e1cef88fe325db477cfd7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84587033"
---
# <a name="claims-and-tokens"></a>Beyanlar ve Belirteçler

Bu konuda Windows Communication Foundation (WCF) tarafından desteklenen varsayılan belirteçlerden oluşturulan çeşitli talep türleri açıklanmaktadır.

Ve sınıflarını kullanarak bir istemci kimlik bilgisinin taleplerini inceleyebilirsiniz <xref:System.IdentityModel.Claims.ClaimSet> <xref:System.IdentityModel.Claims.Claim> . `ClaimSet`Bir nesne koleksiyonu içerir `Claim` . Her biri `Claim` aşağıdaki önemli üyelere sahiptir:

- <xref:System.IdentityModel.Claims.Claim.ClaimType%2A>Özelliği, yapılan talep türünü belirten bir Tekdüzen Kaynak tanımlayıcısı (URI) döndürür. Örneğin, bir talep türü bir sertifikanın parmak izi olabilir, bu durumda URI olur `http://schemas.microsoft.com/ws/20005/05/identity/claims/thumprint` .

- <xref:System.IdentityModel.Claims.Claim.Right%2A>Özelliği, talebin sağına belirten BIR URI döndürür. Önceden tanımlanmış haklar <xref:System.IdentityModel.Claims.Rights> sınıfında ( <xref:System.IdentityModel.Claims.Rights.Identity%2A> , <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> ) bulunur.

- <xref:System.IdentityModel.Claims.Claim.Resource%2A>Özelliği, talep ile ilişkili kaynağı döndürür.

Her birinin, <xref:System.IdentityModel.Claims.ClaimSet> <xref:System.IdentityModel.Claims.ClaimSet.Issuer%2A> ' ı temsil eden bir özelliği de vardır <xref:System.IdentityModel.Claims.ClaimSet> `Issuer` .

## <a name="windows-accounts"></a>Windows hesapları

İstemci kimlik bilgilerinin bir Windows kullanıcı hesabıyla eşlendiği yerde, sonuç <xref:System.IdentityModel.Claims.ClaimSet> aşağıdaki değerlere sahiptir:

- , `Issuer` Sınıfının statik Windows özelliği tarafından döndürülen değerdir <xref:System.IdentityModel.Claims.ClaimSet> .

- Koleksiyondaki talepler şunlardır:

  - <xref:System.IdentityModel.Claims.Claim> <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> Güvenlik tanımlayıcısı (SID) değerine sahip bir, bir <xref:System.IdentityModel.Claims.Claim.Right%2A> özellik değeri `Identity` , ve, <xref:System.IdentityModel.Claims.Claim.Resource%2A> gerçek SID değerini döndüren bir. SID, etki alanı denetleyicisinin her kullanıcıya verdiği benzersiz bir değerdir. SID, kullanıcıyı Windows güvenliğiyle etkileşimler halinde tanımlamak için kullanılır.

  - SID değerine sahip bir, <xref:System.IdentityModel.Claims.Claim> ve SID değeri olan bir <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> <xref:System.IdentityModel.Claims.Claim.Right%2A> `PossessProperty` <xref:System.IdentityModel.Claims.Claim.Resource%2A> .

  - , ' In <xref:System.IdentityModel.Claims.Claim> <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> ' a ve ' a ait <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A> <xref:System.IdentityModel.Claims.Claim.Right%2A> `PossessProperty` <xref:System.IdentityModel.Claims.Claim.Resource%2A> Kullanıcı adını içeren bir dize (örneğin, "mymachınebob").

  - <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>Kullanıcının ait olduğu çeşitli gruplar için ile ek SID talepleri.

## <a name="certificates"></a>Sertifikalar

İstemci kimlik bilgileri bir sertifika olduğunda, sonuç <xref:System.IdentityModel.Claims.ClaimSet> aşağıdaki değerlere sahiptir:

- Kendi kendine verilen sertifikalar için, kendi `Issuer` <xref:System.IdentityModel.Claims.ClaimSet> kendisidir. , ' A <xref:System.IdentityModel.Claims.ClaimSet> <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> <xref:System.IdentityModel.Claims.ClaimTypes.Thumbprint%2A> , ' a <xref:System.IdentityModel.Claims.Claim.Right%2A> `Identity` ve <xref:System.IdentityModel.Claims.Claim.Resource%2A> <xref:System.Byte> sertifikanın parmak izini içeren bir dizi değeri döndürür.

- Sertifika yetkilisi tarafından verilen bir sertifika için sertifikayı veren sertifika `ClaimSet` yetkilisinin sertifikasını temsil eder.

- `Claims`Koleksiyondaki öğesine şunlar dahildir:

  - `Claim` `ClaimType` Parmak izi olan a, `Right` PossessProperty ve `Resource` sertifikanın parmak izini içeren bir bayt dizisidir

  - X500DistinguishedName, DNS, Name, UPN ve RSA gibi çeşitli türlerde ek PossessProperty talepleri, sertifikanın çeşitli özelliklerini temsil eder. RSA talebinin kaynağı sertifikayla ilişkili ortak anahtardır. **Göz önünde** İstemci kimlik bilgileri türü, hizmetin bir Windows hesabıyla eşlendiği bir sertifika olduğunda, iki `ClaimSet` nesne oluşturulur. İlki Windows hesabıyla ilgili tüm talepleri içerir ve ikincisi sertifikayla ilgili tüm talepleri içerir.

## <a name="user-namepassword"></a>Kullanıcı adı/parola

İstemci kimlik bilgisinin bir Windows hesabıyla eşleşmeyen bir Kullanıcı adı/parolası (veya eşdeğeri) olduğu durumlarda, sonuç `ClaimSet` sınıfın statik özelliği tarafından verilir <xref:System.IdentityModel.Claims.ClaimSet.System%2A> `ClaimSet` . , `ClaimSet` `Identity` <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A> Kaynağı istemcinin sağladığı Kullanıcı adı olan bir tür talebi içerir. Karşılık gelen bir talep, öğesine sahiptir `Right` `PossessProperty` .

## <a name="rsa-keys"></a>RSA anahtarları

Bir sertifika ile ilişkilendirilmemiş bir RSA anahtarı kullanıldığında, sonuçta elde edilen `ClaimSet` kendi kendine verilir ve `Identity` kaynağı RSA anahtarı olan bir tür talebi içerir <xref:System.IdentityModel.Claims.ClaimTypes.Rsa%2A> . Karşılık gelen bir talep, öğesine sahiptir `Right` `PossessProperty` .

## <a name="saml"></a>SAML

İstemci bir güvenlik onaylama işlemi Işaretleme dili (SAML) belirteciyle kimlik doğruladığında, sonuç olarak `ClaimSet` SAML belirtecini imzalayan varlık tarafından verilir, genellıkle SAML belirtecini veren güvenlik belirteci hizmeti (STS) sertifikasıdır. `ClaimSet`SAML belirtecinde bulunan çeşitli talepler içerir. SAML belirteci adı olmayan bir içeriyorsa `SamlSubject` `null` , `Identity` türü <xref:System.IdentityModel.Claims.ClaimTypes.NameIdentifier%2A> ve kaynak türü olan bir talep <xref:System.IdentityModel.Tokens.SamlNameIdentifierClaimResource> oluşturulur.

## <a name="identity-claims-and-servicesecuritycontextisanonymous"></a>Kimlik talepleri ve ServiceSecurityContext. ıanonymous

`ClaimSet`İstemci kimlik bilgilerinden kaynaklanan nesnelerden hiçbiri, ' ın ' a sahip bir talep içermiyorsa `Right` `Identity,` , <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> özelliği döndürülür `true` . Bir veya daha fazla talep varsa, `IsAnonymous` özelliği döndürür `false` .

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IdentityModel.Claims.ClaimSet>
- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- [Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme](managing-claims-and-authorization-with-the-identity-model.md)
