---
title: Ayrıcalık Yükseltme
ms.date: 03/30/2017
helpviewer_keywords:
- elevation of privilege [WCF]
- security [WCF], elevation of privilege
ms.assetid: 146e1c66-2a76-4ed3-98a5-fd77851a06d9
ms.openlocfilehash: eae3c2a72e686774ee510dfc3ec9db04df7db630
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966179"
---
# <a name="elevation-of-privilege"></a>Ayrıcalık Yükseltme
*Ayrıcalık yükselmesi,* başlangıçta verilen bir saldırgan yetkilendirme izinleri vermesinden kaynaklanır. Örneğin, ayrıcalık "salt okuma" olan bir saldırgan, "okuma ve yazma" iznini dahil etmek için bu ayarı bir şekilde yükseltir.  
  
## <a name="trusted-sts-should-sign-saml-token-claims"></a>Güvenilen STS, SAML belirteci taleplerini Imzamalıdır  
 Güvenlik onaylama işlemi biçimlendirme dili (SAML) belirteci, verilen belirteçler için varsayılan tür olan genel bir XML belirtecidir. Bir SAML belirteci, son Web hizmetinin tipik bir alışverişte güvendiği bir güvenlik belirteci hizmeti (STS) tarafından oluşturulabilir. SAML belirteçleri deyimlerde talepler içerir. Bir saldırgan, talepleri geçerli bir belirteçle kopyalayabilir, yeni bir SAML belirteci oluşturabilir ve farklı bir veren ile imzalayabiliriz. Amaç, sunucunun verenler doğrulama yapıp yapmadığını belirlemektir ve yoksa, güvenilir bir STS tarafından sağlananlar dışında ayrıcalıklara izin veren SAML belirteçleri oluşturmak için zayıf kullanımı kullanır.  
  
 Sınıfı, bir SAML belirteci içinde bulunan dijital imzayı doğrular ve varsayılan değer <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> , SAML belirteçlerinin, <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> sınıf için ayarlandığında geçerli olan bir X. 509.440 sertifikası tarafından imzalanmasını gerektirir <xref:System.IdentityModel.Tokens.SamlAssertion> <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust>. `ChainTrust`SAML belirtecinin vereni güvenilir olup olmadığını anlamak için tek başına modu yetersiz. Daha ayrıntılı bir güven modeli gerektiren hizmetler, verilen belirteç kimlik doğrulaması tarafından üretilen talep kümelerinin vereni denetlemek için yetkilendirme ve zorlama ilkelerini kullanabilir ya da bir kümesini kısıtlamak için üzerinde <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> X. 509.440 doğrulama ayarlarını kullanabilir imzalama sertifikaları izin verildi. Daha fazla bilgi için bkz. kimlik modeli ve [Federasyon ve verilen](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md) [belirteçlerle talepleri yönetme ve yetkilendirme](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md) .  
  
## <a name="switching-identity-without-a-security-context"></a>Kimliği güvenlik bağlamı olmadan değiştirme  
 Aşağıdakiler yalnızca WinFX için geçerlidir.  
  
 İstemci ve sunucu arasında bağlantı kurulduktan sonra, bir durum dışında istemcinin kimliği değişmez: aşağıdaki koşulların tümü doğruysa WCF istemcisi açıldıktan sonra:  
  
- Bir güvenlik bağlamı oluşturma yordamları (bir taşıma güvenlik oturumu veya ileti güvenlik oturumu kullanarak) kapalı (<xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> ileti güvenliği veya taşıma güvenlik oluşturma yeteneğine sahip değilse, özelliği olarak `false` ayarlanır) Oturumlar aktarım güvenliği durumunda kullanılır. HTTPS, söz konusu taşımanın bir örneğidir).  
  
- Windows kimlik doğrulaması kullanıyorsunuz.  
  
- Kimlik bilgisini açıkça ayarlamayın.  
  
- Hizmeti kimliğe bürünme güvenlik bağlamı altında arıyoruz.  
  
 Bu koşullar doğru ise, istemcinin kimliğini doğrulamak için kullanılan kimlik, WCF istemcisi açıldıktan sonra değişebilir (Bunun yerine kimliğe bürünülmüş kimlik ancak işlem kimliği olmayabilir). Bu durum, istemcinin kimliğini doğrulamak için kullanılan Windows kimlik bilgisinin her iletiyle iletilmesi ve kimlik doğrulaması için kullanılan kimlik bilgilerinin geçerli iş parçacığının Windows kimliğinden elde edilmesinden kaynaklanır. Geçerli iş parçacığının Windows kimliği değişirse (örneğin, farklı bir çağıranın kimliğine bürünerek), iletiye eklenen ve istemcinin kimlik doğrulaması için kullanılan kimlik bilgileri de değişebilir.  
  
 Windows kimlik doğrulamasını kimliğe bürünme ile birlikte kullanırken belirleyici davranışa sahip olmak istiyorsanız, Windows kimlik bilgilerini açıkça ayarlamanız veya hizmetle bir güvenlik bağlamı oluşturmanız gerekir. Bunu yapmak için bir ileti güvenlik oturumu veya bir taşıma güvenlik oturumu kullanın. Örneğin, net. TCP taşıması bir taşıma güvenlik oturumu sağlayabilir. Ayrıca, hizmeti çağırırken yalnızca zaman uyumlu bir istemci işlemleri sürümü kullanmanız gerekir. İleti güvenlik bağlamı oluşturursanız, kimlik, oturum yenileme işlemi sırasında da değiştirebildiğinden, hizmet bağlantısını yapılandırılan oturum yenileme süresinden daha uzun süre açık tutmanız gerekir.  
  
### <a name="credentials-capture"></a>Kimlik bilgileri yakalama  
 Aşağıdakiler ve sonraki sürümler [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]için geçerlidir.  
  
 İstemci veya hizmet tarafından kullanılan kimlik bilgileri, geçerli bağlam iş parçacığını temel alır. İstemci veya hizmetin `Open` yöntemi (ya `BeginOpen`da zaman uyumsuz çağrılar) çağrıldığında kimlik bilgileri alınır. `BeginOpen` <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> <xref:System.ServiceModel.Channels.CommunicationObject.BeginOpen%2A> Hem hem de`Open` sınıfları için, ve yöntemleri, sınıfının<xref:System.ServiceModel.Channels.CommunicationObject> ve yöntemlerinden devralınır. <xref:System.ServiceModel.ClientBase%601> <xref:System.ServiceModel.ServiceHost>  
  
> [!NOTE]
> `BeginOpen` Yöntemi kullanılırken, yakalanan kimlik bilgilerinin yöntemini çağıran işlemin kimlik bilgileri olması garanti edilemez.  
  
## <a name="token-caches-allow-replay-using-obsolete-data"></a>Belirteç önbellekleri eski verileri kullanarak yeniden yürütmeye Izin verir  
 WCF, Kullanıcı adı ve parola ile kullanıcıların kimliğini `LogonUser` doğrulamak için yerel güvenlik yetkilisi (LSA) işlevini kullanır. Oturum açma işlevi maliyetli bir işlem olduğundan, WCF, performansı artırmak için kimliği doğrulanmış kullanıcıları temsil eden belirteçleri önbelleğe almanıza olanak sağlar. Önbelleğe alma mekanizması, sonraki kullanımlar `LogonUser` için sonuçlarını kaydeder. Bu mekanizma varsayılan olarak devre dışıdır; etkinleştirmek için <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.CacheLogonTokens%2A> özelliğini olarak `true`ayarlayın veya [ \<UserNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) `cacheLogonTokens` özniteliğini kullanın.  
  
 <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.CachedLogonTokenLifetime%2A> Özelliği bir <xref:System.TimeSpan>olarak ayarlayarak önbelleğe alınmış belirteçler için yaşam süresi (TTL) ayarlayabilir veya `userNameAuthentication` öğenin `cachedLogonTokenLifetime` özniteliğini kullanabilirsiniz; varsayılan değer 15 dakikadır. Bir belirteç önbelleğe alındığında, Kullanıcı hesabı Windows 'tan silinse veya parolası değiştirilmişse bile, aynı kullanıcı adını ve parolayı sunan tüm istemciler belirteci kullanabilir. TTL süresi dolana ve belirteç önbellekten kaldırılana kadar, WCF (muhtemelen kötü amaçlı) kullanıcının kimliğini doğrulamasına izin verir.  
  
 Bunu azaltmak için: `cachedLogonTokenLifetime` Değeri kullanıcılarınızın ihtiyaç duyduğu en kısa zaman aralığına ayarlayarak saldırı penceresini azaltın.  
  
## <a name="issued-token-authorization-expiration-reset-to-large-value"></a>Verilen belirteç yetkilendirmesi: Süre sonu değeri büyük değere sıfırlandı  
 Belirli koşullar <xref:System.IdentityModel.Policy.AuthorizationContext.ExpirationTime%2A> altında, <xref:System.IdentityModel.Policy.AuthorizationContext> öğesinin özelliği <xref:System.DateTime.MaxValue> beklenmedik bir şekilde büyük bir değere ayarlanabilir (alan değeri eksi bir gün veya 20 Aralık 9999).  
  
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
  
 Bunu azaltmak için, X. 509.440 sertifikasına, using <xref:System.ServiceModel.Security.Tokens.X509KeyIdentifierClauseType.IssuerSerial>gibi başka bir şekilde başvurun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik Konuları](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [Bilgilerin Açığa Çıkması](../../../../docs/framework/wcf/feature-details/information-disclosure.md)
- [Hizmet Reddi](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [Yeniden Yürütme Saldırıları](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
- [İzinsiz Değişiklik](../../../../docs/framework/wcf/feature-details/tampering.md)
- [Desteklenmeyen Senaryolar](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
