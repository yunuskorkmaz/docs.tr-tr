---
title: WIF talep programlama modeli
ms.date: 03/30/2017
ms.assetid: 149cb875-9b1c-4695-b88a-fbf1725a02f9
author: BrucePerlerMS
ms.openlocfilehash: 95df026684f536a64ffe15f65264c470dff164da
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47171718"
---
# <a name="wif-claims-programming-model"></a>WIF talep programlama modeli
ASP.NET ve Windows Communication Foundation (WCF) geliştiricileri, IIdentity ve IPrincipal arabirimleri genellikle kullanıcının kimlik bilgileri ile çalışmak için kullanın. Artık her zaman Aşağıdaki diyagramda gösterildiği gibi herhangi bir asıl için mevcut taleplerdir şekilde .NET 4.5 içinde Windows Identity Foundation (WIF) tümleştirilmiştir:

 ![WIF talep programlama modeli](../../../docs/framework/security/media/wifclaimsprogrammingmodel.png "WIFClaimsProgrammingModel")

 .NET 4.5 içinde System.Security.Claims (bkz. Yukarıdaki diyagramda) yeni ClaimsPrincipal ve Claimsıdentity sınıfları içerir. . NET'te tüm ilkeleri artık ClaimsPrincipal türetilir. ASP.NET ve artık WindowsIdentity FormsIdentity gibi tüm yerleşik kimlik sınıflar Claimsıdentity türetilir. Benzer şekilde, GenericPrincipal ve WindowsPrincipal gibi tüm yerleşik asıl sınıflar ClaimsPrincipal türetilir.

 Bir talep tarafından temsil edilen <xref:System.Security.Claims.Claim> sınıfı. Bu sınıf, aşağıdaki önemli özelliklere sahiptir:

- <xref:System.Security.Claims.Claim.Type%2A> talep türünü temsil eder ve genellikle bir URI'dir. Örneğin, e-posta adresi talep olarak temsil edilir `http://schemas.microsoft.com/ws/2008/06/identity/claims/email`.

- <xref:System.Security.Claims.Claim.Value%2A> Talep değerini içeren ve bir dize olarak temsil edilir. Örneğin, e-posta adresi olarak gösterilebilir "someone@contoso.com".

- <xref:System.Security.Claims.Claim.ValueType%2A> Talep değeri türünü temsil eder ve genellikle bir URI'dir. Örneğin, dize türü olarak temsil edilir `http://www.w3.org/2001/XMLSchema#string`. Değer türü XML şemasına göre bir QName olmalıdır. Değeri olması gereken biçim `namespace#format` geçerli bir QName değeri çıktısını almak WIF etkinleştirme. Ad alanı, iyi tanımlanmış bir ad alanı değil, olmayacak çünkü bu ad alanı için yayımlanmış bir XSD dosyası oluşturulan XML Şeması doğrulanır, büyük olasılıkla olamaz. Varsayılan değer türü `http://www.w3.org/2001/XMLSchema#string`. Lütfen [ http://www.w3.org/2001/XMLSchema ](https://go.microsoft.com/fwlink/?LinkId=209155) iyi bilinen değer türleri için güvenli bir şekilde kullanabilirsiniz.

- <xref:System.Security.Claims.Claim.Issuer%2A> Talep veren güvenlik belirteci hizmeti (STS) tanımlayıcısıdır. Bu URL STS veya STS gibi temsil eden bir ad olarak temsil edilebilir `https://sts1.contoso.com/sts`.

- <xref:System.Security.Claims.Claim.OriginalIssuer%2A> ilk olarak kaç Sts'ler bakılmaksızın Talep veren STS tanımlayıcısını zincirinde duyarlıdır. Bu gibi temsil edilen <xref:System.Security.Claims.Claim.Issuer%2A>.

- <xref:System.Security.Claims.Claim.Subject%2A> Kimliğe incelenmekte olan konudur. İçerdiği bir <xref:System.Security.Claims.ClaimsIdentity>.

- <xref:System.Security.Claims.Claim.Properties%2A> Geliştirici sağlayan bir sözlük diğer özelliklerle birlikte Kablodaki aktarılmak için uygulamaya özgü verileri sağlayın ve özel doğrulama için kullanılabilir.

## <a name="identity-delegation"></a>Kimlik temsilcisi seçme
Önemli bir özelliği <xref:System.Security.Claims.ClaimsIdentity> olduğu <xref:System.Security.Claims.ClaimsIdentity.Actor%2A>. Bu özellik, bir orta katman istemci istekleri arka uç hizmetinize olarak davranan bir çok katmanlı sistem kimlik bilgileri temsilcisi etkinleştirir.

### <a name="accessing-claims-through-threadcurrentprincipal"></a>Talep Thread.CurrentPrincipal erişme
RP uygulamada talepler kümesi geçerli kullanıcının erişmek için `Thread.CurrentPrincipal`.

Aşağıdaki kod örneği bir System.Security.Claims.ClaimsIdentity almak için bu yöntemi kullanımını gösterir:

```csharp
ClaimsPrincipal claimsPrincipal = Thread.CurrentPrincipal as ClaimsPrincipal;
```

Daha fazla bilgi için bkz. <xref:System.Security.Claims>.

### <a name="role-claim-type"></a>Rol talep türü
RP uygulamanızı yapılandırma bir parçası olan hangi rolünüz belirlemek için talep türü olmalıdır. Bu talep türü System.Security.Claims.ClaimsPrincipal.IsInRole(System.String) tarafından kullanılır. Varsayılan talep türü `http://schemas.microsoft.com/ws/2008/06/identity/claims/role`.

### <a name="claims-extracted-by-windows-identity-foundation-from-different-token-types"></a>Windows Identity Foundation'dan farklı bir belirteç türleri tarafından ayıklanan talepleri
WIF, çeşitli kimlik doğrulama mekanizmaları hazır birleşimleri destekler. Aşağıdaki tabloda, farklı bir belirteç türlerinden WIF ayıklar talepleri listeler.

|Belirteç türü|Oluşturulan talep|Windows erişim belirteci eşleyin|
|-|-|-|
|SAML 1.1|1.  System.IdentityModel.SecurityTokenService.GetOutputClaimsIdentity(System.Security.Claims.ClaimsPrincipal,System.IdentityModel.Protocols.WSTrust.RequestSecurityToken,System.IdentityModel.Scope) gelen tüm talepleri.<br />2.  `http://schemas.microsoft.com/ws/2008/06/identity/claims/confirmationkey` Onay anahtarının XML serileştirme belirteci düzeltme belirteci içerirse içeren talep.<br />3.  `http://schemas.microsoft.com/ws/2008/06/identity/claims/samlissuername` Talep veren öğesinden.<br />4.  Belirteç kimlik doğrulaması deyimi içeriyorsa AuthenticationMethod ve AuthenticationInstant talepler.|Talep yanı sıra dışında talep türü "SAML 1.1", listelenen `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name`, Windows kimlik doğrulamasıyla ilgili talep eklenir ve kimlik Windowsclaimsıdentity tarafından temsil edilir.|
|SAML 2.0|"SAML 1.1" ile aynıdır.|"SAML 1.1 Windows eşlenmiş" ile aynıdır.|
|X509|1.  Talep X500 ile ayırt edici adı, epostaadı dnsName, SimpleName, UpnName UrlName, parmak izini (Bu ayıklanan X509Certificate2.PublicKey.Key özelliğinden RSACryptoServiceProvider.ExportParameters yöntemi kullanarak), RsaKey DsaKey ( Bunu ayıklanan X509Certificate2.PublicKey.Key özelliğinden DSACryptoServiceProvider.ExportParameters yöntemi kullanarak), seri numarası X509 özelliklerinden sertifika.<br />2.  AuthenticationMethod talep değeriyle `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/x509`. Sertifika XmlSchema tarih saat biçiminde zaman doğrulandığı zaman değeri ile AuthenticationInstant talep.|1.  Windows hesabı tam etki alanı adını kullanan `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name` talep değeri. biçimindeki telefon numarasıdır.<br />2.  Sertifika için Windows eşlenmedi X509 gelen talepleri ve Windows için sertifika eşleyerek elde edilen windows hesabı gelen talepler.|
|UPN|1.  Talepler, talep Windows kimlik doğrulaması bölümünde benzerdir.<br />2.  AuthenticationMethod talep değeriyle `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/password`. Parola XmlSchema tarih saat biçiminde zaman doğrulandığı zaman değeri ile AuthenticationInstant talep.||
|Windows (Kerberos veya NTLM)|1.  Erişim belirtecinden gibi oluşturulan talepler: PrimarySID, DenyOnlyPrimarySID, PrimaryGroupSID, DenyOnlyPrimaryGroupSID, GrupSID, DenyOnlySID ve adı<br />2.  AuthenticationMethod değerle `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/windows`. Windows belirteç eriştiğinizde zaman değeri ile AuthenticationInstant XMLSchema tarih saat biçiminde oluşturulur.||
|RSA anahtar çifti|1.  `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/rsa` RSAKeyValue değeriyle talep.<br />2.  AuthenticationMethod talep değeriyle `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/signature`. AuthenticationInstant talebi zaman RSA anahtarı kimlik doğrulaması zaman değeri (diğer bir deyişle, İmza doğrulandı) XMLSchema tarih saat biçiminde.||

|Kimlik doğrulaması türü|"AuthenticationMethod" talebi yayılan URI'si|
|-|-|
|Parola|`urn:oasis:names:tc:SAML:1.0:am:password`|
|Kerberos|`urn:ietf:rfc:1510`|
|SecureRemotePassword|`urn:ietf:rfc:2945`|
|TLSClient|`urn:ietf:rfc:2246`|
|X509|`urn:oasis:names:tc:SAML:1.0:am:X509-PKI`|
|PGP|`urn:oasis:names:tc:SAML:1.0:am:PGP`|
|Spki|`urn:oasis:names:tc:SAML:1.0:am:SPKI`|
|XmlDSig|`urn:ietf:rfc:3075`|
|Belirtilmemiş|`urn:oasis:names:tc:SAML:1.0:am:unspecified`|