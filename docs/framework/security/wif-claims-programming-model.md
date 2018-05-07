---
title: WIF talep programlama modeli
ms.date: 03/30/2017
ms.assetid: 149cb875-9b1c-4695-b88a-fbf1725a02f9
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 71327fb5a86c30d15ff060eff5cce170695e86a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="wif-claims-programming-model"></a>WIF talep programlama modeli
ASP.NET ve Windows Communication Foundation (WCF) geliştiriciler kimlik ve IPrincipal arabirimleri kullanıcının kimlik bilgileri ile çalışmak için normalde kullanın. Talep şimdi her zaman aşağıdaki çizimde gösterildiği gibi herhangi bir asıl için mevcut olduğundan .NET 4.5, Windows Identity Foundation (WIF) entegre edilmiş:  
  
 ![WIF talep programlama modeli](../../../docs/framework/security/media/wifclaimsprogrammingmodel.png "WIFClaimsProgrammingModel")  
  
 .NET 4.5 içinde System.Security.Claims (Yukarıdaki diyagramda bakın) yeni ClaimsPrincipal ve Claimsıdentity sınıfları içerir. .NET içinde tüm Sorumlular şimdi ClaimsPrincipal türetilir. ASP.NET ve şimdi WindowsIdentity FormsIdentity gibi tüm yerleşik kimlik sınıflar Claimsıdentity türetilir. Benzer şekilde, GenericPrincipal ve WindowsPrincipal gibi tüm yerleşik asıl sınıflar ClaimsPrincipal türetilir.  
  
 Bir talep tarafından temsil edilen <xref:System.Security.Claims.Claim> sınıfı. Bu sınıf aşağıdaki önemli özelliklere sahiptir:  
  
-   <xref:System.Security.Claims.Claim.Type%2A> talep türünü temsil eder ve genellikle bir URI'dır. Örneğin, e-posta adresi talep olarak temsil edilir `http://schemas.microsoft.com/ws/2008/06/identity/claims/email`.  
  
-   <xref:System.Security.Claims.Claim.Value%2A> Talep değerini içerir ve bir dize olarak temsil edilir. Örneğin, e-posta adresi olarak temsil edilebilir "someone@contoso.com".  
  
-   <xref:System.Security.Claims.Claim.ValueType%2A> Talep değeri türünü temsil eder ve genellikle bir URI'dır. Örneğin, dize türü olarak temsil edilir `http://www.w3.org/2001/XMLSchema#string`. Değer türü QName XML şemasına göre olması gerekir. Değer biçiminde olmalıdır `namespace#format` geçerli bir QName değer çıktı WIF etkinleştirmek için. Ad alanı iyi tanımlanmış bir ad değil, olmayacaktır çünkü bu ad alanı için yayımlanan bir XSD dosyası oluşturulmuş XML büyük olasılıkla doğrulandığında, şema olamaz. Varsayılan değer türü `http://www.w3.org/2001/XMLSchema#string`. Lütfen bakın [ http://www.w3.org/2001/XMLSchema ](http://go.microsoft.com/fwlink/?LinkId=209155) iyi bilinen değer türleri için güvenli bir şekilde kullanabilirsiniz.  
  
-   <xref:System.Security.Claims.Claim.Issuer%2A> Talep veren güvenlik belirteci hizmeti (STS) tanımlayıcısıdır. Bu URL STS veya STS gibi temsil eden bir ad olarak temsil edilebilir `https://sts1.contoso.com/sts`.  
  
-   <xref:System.Security.Claims.Claim.OriginalIssuer%2A> ilk olarak kaç Sts'ler bağımsız olarak Talep veren STS tanıtıcısı zincirinde'dır. Bu tıpkı temsil edilen <xref:System.Security.Claims.Claim.Issuer%2A>.  
  
-   <xref:System.Security.Claims.Claim.Subject%2A> Kimliğe incelenir konusudur. İçerdiği bir <xref:System.Security.Claims.ClaimsIdentity>.  
  
-   <xref:System.Security.Claims.Claim.Properties%2A> Geliştirici olanak sağlayan bir sözlük diğer özelliklerle birlikte hattaki aktarılması için uygulamaya özgü verileri sağlamak ve özel doğrulama için kullanılabilir.  
  
## <a name="identity-delegation"></a>Kimlik temsilcisi seçme  
 Önemli bir özelliği <xref:System.Security.Claims.ClaimsIdentity> olan <xref:System.Security.Claims.ClaimsIdentity.Actor%2A>. Bu özelliği, orta katman istemci isteklerini bir arka uç hizmetinde yapmak için olarak davranan çok katmanlı sistemindeki kimlik bilgilerinin temsili sağlar.  
  
### <a name="accessing-claims-through-threadcurrentprincipal"></a>Talep Thread.CurrentPrincipal erişme  
 Geçerli kullanıcının RP uygulamada talep kümesini erişmek için `Thread.CurrentPrincipal`.  
  
 Aşağıdaki kod örneği bir System.Security.Claims.ClaimsIdentity almak için bu yöntemi kullanımını gösterir:  
  
```  
ClaimsPrincipal claimsPrincipal = Thread.CurrentPrincipal as ClaimsPrincipal;  
```  
  
 Daha fazla bilgi için bkz. <xref:System.Security.Claims>.  
  
### <a name="role-claim-type"></a>Rol talep türü  
 RP uygulamanızı yapılandırmanın parçasıdır hangi rolünüze belirlemek için talep türü olmalıdır. Bu talep türü System.Security.Claims.ClaimsPrincipal.IsInRole(System.String) tarafından kullanılır. Varsayılan talep türü `http://schemas.microsoft.com/ws/2008/06/identity/claims/role`.  
  
### <a name="claims-extracted-by-windows-identity-foundation-from-different-token-types"></a>Windows Identity Foundation'ı farklı belirteci türlerinden tarafından ayıklanan talepleri  
 WIF kutunun dışında kimlik doğrulama mekanizmaları birkaç birleşimlerini destekler. Aşağıdaki tabloda farklı belirteci türlerinden WIF ayıklar talepleri listeler.  
  
|Belirteç türü|Oluşturulan talep|Windows erişim belirteci Eşle|  
|-|-|-|  
|SAML 1.1|1.  System.IdentityModel.SecurityTokenService.GetOutputClaimsIdentity(System.Security.Claims.ClaimsPrincipal,System.IdentityModel.Protocols.WSTrust.RequestSecurityToken,System.IdentityModel.Scope) tüm talepleri.<br />2.  `http://schemas.microsoft.com/ws/2008/06/identity/claims/confirmationkey` Talep belirteci düzeltme belirteci içeriyorsa, onay anahtarının XML serileştirme içerir.<br />3.  `http://schemas.microsoft.com/ws/2008/06/identity/claims/samlissuername` Veren öğesinden talep.<br />4.  Belirteç kimlik doğrulama deyimi içerir, AuthenticationMethod ve AuthenticationInstant talepleri.|Ek olarak talep türü talep dışında "SAML 1.1", listelenen `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name`, Windows kimlik doğrulaması ilgili talep eklenir ve kimlik tarafından WindowsClaimsIdentity temsil edilir.|  
|SAML 2.0|"SAML 1.1" ile aynıdır.|"SAML Windows hesabına eşlenen 1.1" ile aynıdır.|  
|X509|1.  X500 olan talepleri ayırt edici adı, epostaadı, dnsName SimpleName, UpnName, UrlName, parmak izi, (Bu ayıklanan X509Certificate2.PublicKey.Key özelliğinden RSACryptoServiceProvider.ExportParameters yöntemini kullanarak) RsaKey DsaKey () Bu ayıklanan X509Certificate2.PublicKey.Key özelliğinden DSACryptoServiceProvider.ExportParameters yöntemini kullanarak), X509 SerialNumber özelliklerinden sertifika.<br />2.  AuthenticationMethod talebi değeri `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/x509`. Sertifika XmlSchema tarih saat biçiminde zaman doğrulandı saat değeri ile AuthenticationInstant talep.|1.  Windows hesap tam etki alanı adı olarak kullandığı `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name` talep değeri. biçimindeki telefon numarasıdır.<br />2.  Sertifika Windows eşlenmedi X509 talepleri ve talep Windows sertifika eşleyerek elde windows hesabı.|  
|UPN|1.  Talepler, talep Windows kimlik doğrulaması bölümünde benzerdir.<br />2.  AuthenticationMethod talebi değeri `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/password`. Parola XmlSchema tarih saat biçiminde zaman doğrulandı saat değeri ile AuthenticationInstant talep.||  
|Windows (Kerberos veya NTLM)|1.  Erişim belirtecinden gibi oluşturulan talep: PrimarySID, DenyOnlyPrimarySID, PrimaryGroupSID, DenyOnlyPrimaryGroupSID, GrupSID, DenyOnlySID ve adı<br />2.  AuthenticationMethod değerle `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/windows`. Windows belirteç eriştiğinizde saat değeri ile AuthenticationInstant XMLSchema tarih saat biçiminde oluşturuldu.||  
|RSA anahtar çifti|1.  `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/rsa` Talep RSAKeyValue değerine.<br />2.  AuthenticationMethod talep değeriyle `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/signature`. Ne zaman RSA anahtarı kimliği doğrulanmış saat değeri ile AuthenticationInstant talep (diğer bir deyişle, İmza doğrulandı) XMLSchema tarih saat biçiminde.||  
  
|Kimlik doğrulama türü|"AuthenticationMethod" talep yayılan URI|  
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
