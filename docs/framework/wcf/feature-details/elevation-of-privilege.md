---
title: Ayrıcalık Yükseltme
ms.date: 03/30/2017
helpviewer_keywords:
- elevation of privilege [WCF]
- security [WCF], elevation of privilege
ms.assetid: 146e1c66-2a76-4ed3-98a5-fd77851a06d9
ms.openlocfilehash: 823b41f86080d4802f76fe69865279a7c3506238
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597416"
---
# <a name="elevation-of-privilege"></a>Ayrıcalık Yükseltme
*Ayrıcalık yükselmesi,* başlangıçta verilen bir saldırgan yetkilendirme izinleri vermesinden kaynaklanır. Örneğin, ayrıcalık "salt okuma" olan bir saldırgan, "okuma ve yazma" iznini dahil etmek için bu ayarı bir şekilde yükseltir.  
  
## <a name="trusted-sts-should-sign-saml-token-claims"></a>Güvenilen STS, SAML belirteci taleplerini Imzamalıdır  
 Güvenlik onaylama işlemi biçimlendirme dili (SAML) belirteci, verilen belirteçler için varsayılan tür olan genel bir XML belirtecidir. Bir SAML belirteci, son Web hizmetinin tipik bir alışverişte güvendiği bir güvenlik belirteci hizmeti (STS) tarafından oluşturulabilir. SAML belirteçleri deyimlerde talepler içerir. Bir saldırgan, talepleri geçerli bir belirteçle kopyalayabilir, yeni bir SAML belirteci oluşturabilir ve farklı bir veren ile imzalayabiliriz. Amaç, sunucunun verenler doğrulama yapıp yapmadığını belirlemektir ve yoksa, güvenilir bir STS tarafından sağlananlar dışında ayrıcalıklara izin veren SAML belirteçleri oluşturmak için zayıf kullanımı kullanır.  
  
 <xref:System.IdentityModel.Tokens.SamlAssertion>Sınıfı, BIR SAML belirteci içinde bulunan dijital imzayı doğrular ve varsayılan değer, <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> SAML belirteçlerinin, sınıfının, <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> olarak ayarlandığı zaman geçerli olan bir X. 509.440 sertifikası tarafından imzalanmasını gerektirir <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust> . `ChainTrust`SAML belirtecinin vereni güvenilir olup olmadığını anlamak için tek başına modu yetersiz. Daha ayrıntılı bir güven modeli gerektiren hizmetler, verilen belirteç kimlik doğrulaması tarafından üretilen talep kümelerinin vereni denetlemek için yetkilendirme ve zorlama ilkelerini kullanabilir ya da <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> izin verilen imzalama sertifikaları kümesini kısıtlamak için üzerindeki X. 509.952 doğrulama ayarlarını kullanabilirsiniz. Daha fazla bilgi için bkz. kimlik modeli ve [Federasyon ve verilen belirteçlerle](federation-and-issued-tokens.md) [talepleri yönetme ve yetkilendirme](managing-claims-and-authorization-with-the-identity-model.md) .  
  
## <a name="switching-identity-without-a-security-context"></a>Kimliği güvenlik bağlamı olmadan değiştirme  
 Aşağıdakiler yalnızca WinFX için geçerlidir.  
  
 İstemci ve sunucu arasında bağlantı kurulduktan sonra, bir durum dışında istemcinin kimliği değişmez: aşağıdaki koşulların tümü doğruysa WCF istemcisi açıldıktan sonra:  
  
- Bir güvenlik bağlamı oluşturma yordamları (bir taşıma güvenlik oturumu veya ileti güvenlik oturumu kullanarak) kapalı olur ( <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> `false` ileti güvenliği veya aktarım, aktarım güvenliği durumunda güvenlik oturumları oluşturma yeteneğine sahip olmayan bir durumda olarak ayarlanır). HTTPS, söz konusu taşımanın bir örneğidir).  
  
- Windows kimlik doğrulaması kullanıyorsunuz.  
  
- Kimlik bilgisini açıkça ayarlamayın.  
  
- Hizmeti kimliğe bürünme güvenlik bağlamı altında arıyoruz.  
  
 Bu koşullar doğru ise, istemcinin kimliğini doğrulamak için kullanılan kimlik, WCF istemcisi açıldıktan sonra değişebilir (Bunun yerine kimliğe bürünülmüş kimlik ancak işlem kimliği olmayabilir). Bu durum, istemcinin kimliğini doğrulamak için kullanılan Windows kimlik bilgisinin her iletiyle iletilmesi ve kimlik doğrulaması için kullanılan kimlik bilgilerinin geçerli iş parçacığının Windows kimliğinden elde edilmesinden kaynaklanır. Geçerli iş parçacığının Windows kimliği değişirse (örneğin, farklı bir çağıranın kimliğine bürünerek), iletiye eklenen ve istemcinin kimlik doğrulaması için kullanılan kimlik bilgileri de değişebilir.  
  
 Windows kimlik doğrulamasını kimliğe bürünme ile birlikte kullanırken belirleyici davranışa sahip olmak istiyorsanız, Windows kimlik bilgilerini açıkça ayarlamanız veya hizmetle bir güvenlik bağlamı oluşturmanız gerekir. Bunu yapmak için bir ileti güvenlik oturumu veya bir taşıma güvenlik oturumu kullanın. Örneğin, net. TCP taşıması bir taşıma güvenlik oturumu sağlayabilir. Ayrıca, hizmeti çağırırken yalnızca zaman uyumlu bir istemci işlemleri sürümü kullanmanız gerekir. İleti güvenlik bağlamı oluşturursanız, kimlik, oturum yenileme işlemi sırasında da değiştirebildiğinden, hizmet bağlantısını yapılandırılan oturum yenileme süresinden daha uzun süre açık tutmanız gerekir.  
  
### <a name="credentials-capture"></a>Kimlik bilgileri yakalama  
 Aşağıdakiler .NET Framework 3,5 ve sonraki sürümler için geçerlidir.  
  
 İstemci veya hizmet tarafından kullanılan kimlik bilgileri, geçerli bağlam iş parçacığını temel alır. `Open` `BeginOpen` İstemci veya hizmetin yöntemi (ya da zaman uyumsuz çağrılar) çağrıldığında kimlik bilgileri alınır. Hem hem de <xref:System.ServiceModel.ServiceHost> sınıfları için, <xref:System.ServiceModel.ClientBase%601> `Open` ve yöntemleri, `BeginOpen` <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> sınıfının ve yöntemlerinden devralınır <xref:System.ServiceModel.Channels.CommunicationObject.BeginOpen%2A> <xref:System.ServiceModel.Channels.CommunicationObject> .  
  
> [!NOTE]
> `BeginOpen`Yöntemi kullanılırken, yakalanan kimlik bilgilerinin yöntemini çağıran işlemin kimlik bilgileri olması garanti edilemez.  
  
## <a name="token-caches-allow-replay-using-obsolete-data"></a>Belirteç önbellekleri eski verileri kullanarak yeniden yürütmeye Izin verir  
 WCF, `LogonUser` Kullanıcı adı ve parola ile kullanıcıların kimliğini doğrulamak için yerel güvenlik yetkilisi (LSA) işlevini kullanır. Oturum açma işlevi maliyetli bir işlem olduğundan, WCF, performansı artırmak için kimliği doğrulanmış kullanıcıları temsil eden belirteçleri önbelleğe almanıza olanak sağlar. Önbelleğe alma mekanizması, `LogonUser` sonraki kullanımlar için sonuçlarını kaydeder. Bu mekanizma varsayılan olarak devre dışıdır; etkinleştirmek için <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.CacheLogonTokens%2A> özelliğini olarak ayarlayın `true` veya `cacheLogonTokens` özniteliğini kullanın [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) .  
  
 Özelliği bir olarak ayarlayarak önbelleğe alınmış belirteçler için yaşam süresi (TTL) ayarlayabilir <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.CachedLogonTokenLifetime%2A> <xref:System.TimeSpan> veya `cachedLogonTokenLifetime` öğenin özniteliğini kullanabilirsiniz `userNameAuthentication` ; varsayılan değer 15 dakikadır. Bir belirteç önbelleğe alındığında, Kullanıcı hesabı Windows 'tan silinse veya parolası değiştirilmişse bile, aynı kullanıcı adını ve parolayı sunan tüm istemciler belirteci kullanabilir. TTL süresi dolana ve belirteç önbellekten kaldırılana kadar, WCF (muhtemelen kötü amaçlı) kullanıcının kimliğini doğrulamasına izin verir.  
  
 Bunu azaltmak için: `cachedLogonTokenLifetime` değeri kullanıcılarınızın ihtiyaç duyduğu en kısa zaman aralığına ayarlayarak saldırı penceresini azaltın.  
  
## <a name="issued-token-authorization-expiration-reset-to-large-value"></a>Verilen belirteç yetkilendirmesi: zaman aşımı değeri büyük değere sıfırlandı  
 Belirli koşullar altında, <xref:System.IdentityModel.Policy.AuthorizationContext.ExpirationTime%2A> öğesinin özelliği <xref:System.IdentityModel.Policy.AuthorizationContext> beklenmedik bir şekilde büyük bir değere ayarlanabilir ( <xref:System.DateTime.MaxValue> alan değeri eksi bir gün veya 20 Aralık 9999).  
  
 Bu durum, <xref:System.ServiceModel.WSFederationHttpBinding> istemci kimlik bilgisi türü olarak verilen belirteci olan sistem tarafından belirtilen bağlamalardan herhangi birini kullanırken oluşur.  
  
 Bu durum, aşağıdaki yöntemlerden birini kullanarak özel bağlamalar oluşturduğunuzda da oluşur:  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenBindingElement%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForCertificateBindingElement%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForSslBindingElement%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenOverTransportBindingElement%2A>  
  
 Bunu azaltmak için, yetkilendirme ilkesi, her yetkilendirme ilkesinin eylemini ve sona erme tarihini denetmelidir.  
  
## <a name="the-service-uses-a-different-certificate-than-the-client-intended"></a>Hizmet, Istemcinin hedefinden farklı bir sertifika kullanıyor  
 Belirli koşullar altında, bir istemci bir X. 509.952 sertifikasıyla bir iletiyi dijital olarak imzalayabilir ve hizmetin amaçlanan olandan farklı bir sertifika almasına sahip olabilir.  
  
 Bu durum aşağıdaki koşullarda oluşabilir:  
  
- İstemci bir X. 509.440 sertifikası kullanarak bir iletiyi dijital olarak imzalar ve X. 509.952 sertifikasını iletiye eklemez, bunun yerine yalnızca konu anahtarı tanımlayıcısı kullanılarak sertifikaya başvurur.  
  
- Hizmetin bilgisayarında aynı ortak anahtara sahip iki veya daha fazla sertifika var, ancak bunlar farklı bilgiler içerir.  
  
- Hizmet, konu anahtarı tanımlayıcısı ile eşleşen bir sertifika alır, ancak istemcinin kullanması amaçlanan bir sertifika değildir. WCF iletiyi alıp imzayı doğruladığında, WCF, istenmeyen X. 509.952 sertifikasındaki bilgileri, istemcinin beklenen şekilde farklı ve potansiyel olarak yükseltilmiş bir talepler kümesiyle eşler.  
  
 Bunu azaltmak için, X. 509.440 sertifikasına, using gibi başka bir şekilde başvurun <xref:System.ServiceModel.Security.Tokens.X509KeyIdentifierClauseType.IssuerSerial> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik konuları](security-considerations-in-wcf.md)
- [Bilgileri Açıklama](information-disclosure.md)
- [Hizmet Reddi](denial-of-service.md)
- [Yeniden Yürütme Saldırıları](replay-attacks.md)
- [İzinsiz Değişiklik](tampering.md)
- [Desteklenmeyen Senaryolar](unsupported-scenarios.md)
