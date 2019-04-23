---
title: Ayrıcalık Yükseltme
ms.date: 03/30/2017
helpviewer_keywords:
- elevation of privilege [WCF]
- security [WCF], elevation of privilege
ms.assetid: 146e1c66-2a76-4ed3-98a5-fd77851a06d9
ms.openlocfilehash: fd5829d2dbb1853bf65f1f6e402b918137bd59e3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59099995"
---
# <a name="elevation-of-privilege"></a>Ayrıcalık Yükseltme
*Ayrıcalık yükseltme* izinleri bu başlangıçta verilen ötesinde bir saldırgan yetkilendirme vermesine neden olur. Örneğin, bir ayrıcalık kümesi "salt okunur" izinlere sahip bir saldırgan kümesi "okuma ve yazma" eklenecek şekilde yükseltir  
  
## <a name="trusted-sts-should-sign-saml-token-claims"></a>SAML belirteç taleplerinden STS imzalamalısınız güvenilir  
 Güvenlik onaylama işaretleme dili (SAML) belirteci verilen belirteçler için varsayılan türü olan genel bir XML belirtecidir. SAML belirteci tarafından bir güvenlik belirteci hizmeti (Web Hizmeti uç tipik Exchange'de güvendiği STS) oluşturulabilir. SAML belirteçlerini deyimleri talepleri içerir. Bir saldırganın, geçerli bir belirteç talep kopyalama, yeni bir SAML belirteci oluştur ve sahip farklı bir veren oturum. Aksi takdirde, güvenilen bir STS tarafından bu amaçlayan ötesinde ayrıcalıkları izin SAML belirteçleri oluşturmak için zayıflık yazılımınız olması ve sunucu verenler doğrulama olup olmadığını belirlemek için hedefi olur.  
  
 <xref:System.IdentityModel.Tokens.SamlAssertion> Sınıfı bir SAML belirtecine ve varsayılan içinde bulunan dijital imzayı doğrular <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> SAML belirteçlerini geçerli olduğunda X.509 sertifikası tarafından imzalanması gerektiren <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> , <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> içinsetsınıfı<xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust>. `ChainTrust` tek başına modu SAML belirteci veren güvenilir olup olmadığını belirlemek için yeterli değil. Daha ayrıntılı bir güven modeli olabilir ya da gerektiren hizmetler verilen belirteç kimlik doğrulaması tarafından üretilen talep kümelerinin veren denetlemek veya X.509 doğrulama ayarlarını kullanmak için yetkilendirme ve zorlama ilkelerini kullanmak <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> kümesini sınırlamak için İmzalama sertifikaları izin verilir. Daha fazla bilgi için [yönetme beyanlar ve yetkilendirmeyi kimlik modeliyle](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md) ve [Federasyon ve verilen belirteçler](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
## <a name="switching-identity-without-a-security-context"></a>Bir güvenlik bağlamı olmadan geçiş kimliği  
 Aşağıdaki yalnızca geçerli [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].  
  
 Bir istemci ve sunucu, istemci kimliği arasında bir bağlantı kurulan ne zaman değiştirmez, dışındaki bir durumda: aşağıdaki koşulların tümü doğruysa, WCF istemcisini açtıktan sonra:  
  
-   (Aktarım güvenliği oturumu veya ileti güvenlik oturumu kullanarak) bir güvenlik bağlamı'kurmak için yordamlar geçti (<xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> özelliği `false` ileti güvenliği veya aktarım güvenliği değil kurabilen durumunda oturumlarının aktarım güvenliği durumda kullanılır. HTTPS gibi aktarım örneğidir).  
  
-   Windows kimlik doğrulaması kullanıyorsunuz.  
  
-   Kimlik bilgisi açıkça ayarlamayın.  
  
-   Hizmet Kimliğine bürünülen güvenlik bağlamı altında arıyoruz.  
  
 Bu koşullar geçerli olduğunda, bir hizmete istemcinin kimliğini doğrulamak için kullanılan kimlik değişiklik yapmış olabilir (bunu başkasının kimliğine bürünülerek gerçekleştirilen kimlik ancak işlem kimliği yerine olmayabilir) WCF istemcisini açıldıktan sonra. Bu, hizmete istemcinin kimliğini doğrulamak için kullanılan Windows kimlik bilgilerini, her ileti ile aktarılan ve kimlik doğrulaması için kullanılan kimlik bilgileri geçerli iş parçacığının Windows kimlikten elde edilen nedeniyle oluşur. İletiye eklenmiş ve bir hizmete istemcinin kimliğini doğrulamak için kullanılan kimlik bilgisi, geçerli iş parçacığının Windows kimliği (örneğin, farklı bir çağıranın kimliğine bürünerek) değişirse, de değişebilir.  
  
 Kimliğe bürünme ile birlikte Windows kimlik doğrulamasını kullanırken belirleyici davranışa sahip istiyorsanız açıkça Windows kimlik bilgilerini ayarlamanız gerekir veya hizmeti ile bir güvenlik bağlamı yapmanız gerekir. Bunu yapmak için bir ileti güvenlik oturumu veya aktarım güvenlik oturumu kullanın. Örneğin, net.tcp taşıma Aktarım güvenlik oturumu sağlayabilir. Ayrıca, hizmeti çağrılırken istemci işlemleri zaman uyumlu bir sürümünü kullanmanız gerekir. Bir ileti güvenlik bağlamı oluşturmak, kimlik oturum yenileme işlemi sırasında da değiştirebilirsiniz çünkü, hizmet bağlantı yapılandırılmış oturum yenileme süresini daha uzun açık tutmalısınız değil.  
  
### <a name="credentials-capture"></a>Kimlik bilgilerini yakalama  
 Aşağıdaki uygulandığı [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]ve sonraki sürümleri.  
  
 Kimlik bilgileri, istemci tarafından kullanılmış veya hizmetin geçerli bağlam iş parçacığı üzerinde temel. Kimlik bilgilerini ne zaman elde edilen `Open` yöntemi (veya `BeginOpen`, zaman uyumsuz çağrılar) istemci veya hizmet olarak adlandırılır. Her ikisi için de <xref:System.ServiceModel.ServiceHost> ve <xref:System.ServiceModel.ClientBase%601> sınıfları `Open` ve `BeginOpen` yöntemleri devralmanız <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> ve <xref:System.ServiceModel.Channels.CommunicationObject.BeginOpen%2A> yöntemlerinin <xref:System.ServiceModel.Channels.CommunicationObject> sınıfı.  
  
> [!NOTE]
>  Kullanırken `BeginOpen` yöntemi, yakalanan kimlik bilgilerini kullanılamaz garanti kimlik bilgilerini yöntemi çağıran işlemin.  
  
## <a name="token-caches-allow-replay-using-obsolete-data"></a>Yeniden yürütme süresi geçmiş verilerini kullanarak belirteci önbellekler izin ver  
 WCF kullanan yerel güvenlik yetkilisi (LSA) `LogonUser` kullanıcı adı ve parola ile kullanıcıların kimliğini doğrulamak için işlevi. Oturum açma işlevi pahalı bir işlem olduğundan, WCF temsil eden önbellek belirteçleri, performansı artırmak için kullanıcıların kimlik doğrulamasını sağlar. Önbelleğe alma mekanizması sonuçlardan kaydeder `LogonUser` sonraki kullanımlar için. Bu mekanizma, varsayılan olarak devre dışıdır; Bunu etkinleştirmek için ayarlanmış <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.CacheLogonTokens%2A> özelliğini `true`, veya `cacheLogonTokens` özniteliği [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md).  
  
 Ayarlayarak önbelleğe alınan belirteçleri için Canlı (TTL) bir zaman ayarlayabilirsiniz <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.CachedLogonTokenLifetime%2A> özelliğini bir <xref:System.TimeSpan>, veya `cachedLogonTokenLifetime` özniteliği `userNameAuthentication` öğesi; varsayılan değer 15 dakikadır. Bir belirteç önbelleğe alınmış olsa aynı kullanıcı adı ve parolayı sunan herhangi bir istemci belirteci bile Windows kullanıcı hesabı silinir veya parolası değiştirildiyse kullanabileceğinizi unutmayın. Belirteç önbellekten kaldırılır ve TTL süresi dolana kadar WCF (kötü amaçlı olabilecek) kullanıcının kimlik doğrulamasını sağlar.  
  
 Bunu azaltmak için: Ayarlayarak saldırı penceresini düşürün `cachedLogonTokenLifetime` kısa bir süre değerine, kullanıcılarının ihtiyaç duyduğu span.  
  
## <a name="issued-token-authorization-expiration-reset-to-large-value"></a>Yetkilendirme belirteci verilen: Büyük bir değer sona erme Sıfırla  
 Belirli koşullar altında <xref:System.IdentityModel.Policy.AuthorizationContext.ExpirationTime%2A> özelliği <xref:System.IdentityModel.Policy.AuthorizationContext> beklenmedik bir şekilde daha büyük bir değere ayarlanabilir ( <xref:System.DateTime.MaxValue> alan değer eksi bir günden veya 20 Aralık 9999).  
  
 Kullanırken böyle <xref:System.ServiceModel.WSFederationHttpBinding> ve kimlik bilgisi herhangi bir istemci olarak verilen bir belirteç olan sistem tarafından sağlanan bağlamalar türü.  
  
 Bu ayrıca, aşağıdaki yöntemlerden birini kullanarak özel bağlamalar oluşturma oluşur:  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenBindingElement%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForCertificateBindingElement%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForSslBindingElement%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenOverTransportBindingElement%2A>  
  
 Bunu azaltmak için yetkilendirme ilkesi, eylem ve süre sonu zamanı her yetkilendirme ilkesinin denetlemelisiniz.  
  
## <a name="the-service-uses-a-different-certificate-than-the-client-intended"></a>Hizmet istemci hedeflenen değerinden farklı bir sertifika kullanır.  
 Bazı koşullar altında bir istemci dijital olarak X.509 sertifikası ile bir ileti oturum ve hedeflenen olandan farklı bir sertifika alma hizmeti.  
  
 Bu şu durumlarda oluşabilir:  
  
-   İstemci bir X.509 sertifikası kullanarak ileti dijital olarak imzalar ve X.509 sertifikasının iletiye eklemek değil, ancak yerine yalnızca kendi konu anahtarı tanımlayıcısı'nı kullanarak sertifikaya başvurur.  
  
-   Hizmetin bilgisayarda aynı ortak anahtara sahip iki veya daha fazla sertifika içeriyor, ancak farklı bilgileri içerirler.  
  
-   Konu anahtarı tanımlayıcısı eşleşen bir sertifika hizmeti alır, ancak kullanmak için istemci hedeflenen sürüm değil. WCF iletiyi alır ve imzayı doğrular, WCF istenmeyen X.509 sertifika bilgileri istemci beklenen gelen farklı ve potansiyel olarak yükseltilmiş bir talepler kümesi eşlenir.  
  
 Bunu azaltmak için başvuru X.509 sertifika kullanma gibi başka bir deyişle, <xref:System.ServiceModel.Security.Tokens.X509KeyIdentifierClauseType.IssuerSerial>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik Konuları](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [Bilgilerin Açığa Çıkması](../../../../docs/framework/wcf/feature-details/information-disclosure.md)
- [Hizmet Reddi](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [Yeniden Yürütme Saldırıları](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
- [İzinsiz Değişiklik](../../../../docs/framework/wcf/feature-details/tampering.md)
- [Desteklenmeyen Senaryolar](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
