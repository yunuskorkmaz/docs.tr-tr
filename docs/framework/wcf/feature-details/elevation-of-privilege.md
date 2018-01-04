---
title: "Ayrıcalık Yükseltme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- elevation of privilege [WCF]
- security [WCF], elevation of privilege
ms.assetid: 146e1c66-2a76-4ed3-98a5-fd77851a06d9
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4225460698d36b3b56b9b0b03cde34e4502b13c9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="elevation-of-privilege"></a>Ayrıcalık Yükseltme
*Ayrıcalık yükseltme* izinleri bu başlangıçta verilen ötesinde bir saldırganın yetkilendirme vermesine neden olur. Örneğin, bir saldırganın bir ayrıcalık kümesi "salt okunur" izinleri ile "okuma ve yazma" içerecek şekilde kümesi şekilde yükseltir  
  
## <a name="trusted-sts-should-sign-saml-token-claims"></a>STS SAML belirteç talep imzalamalısınız güvenilir  
 Verilen belirteçler için varsayılan türdür genel bir XML belirteci bir güvenlik onaylar biçimlendirme dili (SAML) belirtecidir. SAML belirteci tarafından bir güvenlik belirteci hizmeti (Web hizmeti bitiş tipik Exchange'de güvendiği STS) oluşturulabilir. SAML belirteçleri deyimlerinde içerir. Bir saldırgan, uygulamasından geçerli bir belirteç talep kopyalama, yeni bir SAML belirteci oluşturun ve farklı bir veren ile oturum açın. Sunucu verenler doğrulama olup olmadığını belirlemek ve değilse, bu amaçlayan bir güvenilen STS tarafından ötesinde ayrıcalıklarına izin SAML belirteçleri oluşturmak için zayıflık kullanmak için hedefi değil.  
  
 <xref:System.IdentityModel.Tokens.SamlAssertion> Sınıfı bir SAML belirtecine ve varsayılan içinde bulunan dijital imzayı doğrular <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> SAML belirteçleri geçerli olduğunda bir X.509 sertifikası tarafından imzalanmış olmasını gerektirir <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> , <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> içinsetsınıfı<xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust>. `ChainTrust`tek başına modunda SAML belirteci veren güvenilir olup olmadığını belirlemek için yeterli değil. Daha ayrıntılı bir güven modeli ya da gerektirebilirsiniz Hizmetleri verilen belirteç kimlik doğrulaması tarafından üretilen talep kümelerinin veren denetleyin veya üzerinde X.509 doğrulama ayarlarını kullanmak için yetkilendirme ve zorlama ilkelerini kullanmak <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> kümesini kısıtlamak için İmzalama sertifikaları izin verilir. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Beyanlar ve yetkilendirmeyi kimlik modeliyle yönetme](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md) ve [Federasyon ve verilen belirteçleri](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
## <a name="switching-identity-without-a-security-context"></a>Bir güvenlik bağlamı olmadan kimliğini değiştirme  
 Aşağıdaki yalnızca geçerli [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].  
  
 Bir istemci ve sunucu, istemci kimliğini arasında bir bağlantı kuran zaman değiştirmez, dışındaki bir durumda: sonra [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci açıldığında, aşağıdaki koşulların tümü doğruysa:  
  
-   (Aktarım güvenlik oturumu veya ileti güvenlik oturumu kullanarak) bir güvenlik bağlamı kurmak için yordamları işlev kapalı (<xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> özelliği ayarlanmış `false` ileti güvenliği veya güvenlik değil kurabilen aktarım durumunda oturumları Aktarım güvenlik durumda kullanılır. HTTPS bir tür taşıma örnektir).  
  
-   Windows kimlik doğrulaması kullanıyor.  
  
-   Açıkça kimlik bilgisi ayarlamayın.  
  
-   Hizmetin Kimliğine bürünülen güvenlik bağlamı altında aradığınız.  
  
 Bu koşullar geçerli olduğunda, istemci hizmeti için kimlik doğrulaması için kullanılan kimlik olabilir (bunu olabilir Kimliğine bürünülen kimlik ancak işlem kimliği yerine) değişiklikten sonra [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci açılır. Bu, istemci hizmeti için kimlik doğrulaması için kullanılan Windows kimlik bilgileri ile her ileti iletilir ve kimlik doğrulaması için kullanılan kimlik bilgileri geçerli iş parçacığının Windows kimlik elde nedeniyle oluşur. Geçerli iş parçacığının Windows kimliğini (örneğin, farklı çağıran kimliğine bürünerek) değişirse iletisine ve hizmet için istemci kimlik doğrulaması için kullanılan kimlik bilgisini de değişebilir.  
  
 Kimliğe bürünme ile birlikte Windows kimlik doğrulamasını kullanırken belirleyici davranışı sahip olmak istiyorsanız açıkça Windows kimlik bilgilerini ayarlamanız gerekir veya bir güvenlik bağlamı hizmetiyle oluşturmanız gerekir. Bunu yapmak için bir ileti güvenlik oturumu veya bir aktarım güvenlik oturumu kullanın. Örneğin, net.tcp aktarım taşıma güvenlik oturumu sağlayabilir. Ayrıca, hizmeti çağrılırken istemci işlemleri zaman uyumlu bir sürümünü kullanmanız gerekir. Bir ileti güvenlik bağlamı kurmak, kimliğini de oturum yenileme işlemi sırasında değişebildiğinden, hizmeti bağlantısı yapılandırılmış oturum yenileme süresini daha uzun açık tutmalısınız değil.  
  
### <a name="credentials-capture"></a>Kimlik bilgilerini yakalama  
 Aşağıdaki uygulandığı [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]ve sonraki sürümleri.  
  
 Kimlik bilgileri istemci tarafından kullanılan veya hizmet, geçerli bağlam iş parçacığı üzerinde dayalı. Kimlik bilgileri ne zaman elde edilen `Open` yöntemi (veya `BeginOpen`, zaman uyumsuz çağrılar için) istemci veya hizmet adlandırılır. Her ikisi için de <xref:System.ServiceModel.ServiceHost> ve <xref:System.ServiceModel.ClientBase%601> sınıfları `Open` ve `BeginOpen` yöntemleri devral <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> ve <xref:System.ServiceModel.Channels.CommunicationObject.BeginOpen%2A> yöntemlerinin <xref:System.ServiceModel.Channels.CommunicationObject> sınıfı.  
  
> [!NOTE]
>  Kullanırken `BeginOpen` yöntemi, yakalanan kimlik bilgilerini garanti edilemediği yöntemini çağırır işlem kimlik bilgileri olmalıdır.  
  
## <a name="token-caches-allow-replay-using-obsolete-data"></a>Belirteç önbellekleri kullanarak eski verileri yeniden yürütme izin ver  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Yerel güvenlik yetkilisi (LSA) kullanan `LogonUser` kullanıcı adı ve parola ile kullanıcıların kimliklerini doğrulamak için işlev. Oturum açma işlevini pahalı bir işlem olduğundan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] performansını artırmak için kimliği doğrulanmış kullanıcılar temsil eden önbellek belirteçleri sağlar. Önbelleğe alma mekanizması sonuçlarından kaydeder `LogonUser` sonraki kullanımlar için. Bu düzenek, varsayılan olarak devre dışıdır; etkinleştirmek için ayarlanmış <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.CacheLogonTokens%2A> özelliğine `true`, veya `cacheLogonTokens` özniteliği [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md).  
  
 Ayarlayarak için önbelleğe alınmış belirteçleri Live (TTL) bir süresini ayarlayabilirsiniz <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.CachedLogonTokenLifetime%2A> özelliğine bir <xref:System.TimeSpan>, veya `cachedLogonTokenLifetime` özniteliği `userNameAuthentication` öğesi; varsayılan değer 15 dakikadır. Bir belirteç önbelleğe olsa da, aynı kullanıcı adı ve parola sunan herhangi bir istemci bir belirteç kullanıcı hesabı Windows'dan silinse bile veya parolasını değiştirdiyseniz kullanabileceğinizi unutmayın. TTL süresi ve belirteç önbellekten kaldırılır kadar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] (büyük olasılıkla kötü amaçlı) kullanıcının kimlik doğrulamasını sağlar.  
  
 Bunu azaltmak için: ayarlayarak saldırı penceresini azaltmak `cachedLogonTokenLifetime` en kısa süre değerine span kullanıcılar gereksiniminizi.  
  
## <a name="issued-token-authorization-expiration-reset-to-large-value"></a>Verilen belirteç yetkilendirme: Büyük değer sona erme Sıfırla  
 Belirli koşullar altında <xref:System.IdentityModel.Policy.AuthorizationContext.ExpirationTime%2A> özelliği <xref:System.IdentityModel.Policy.AuthorizationContext> beklenmedik bir şekilde daha büyük bir değere ayarlanabilir ( <xref:System.DateTime.MaxValue> alan değer eksi bir günden veya 20 Aralık 9999).  
  
 Bu kullanırken oluşur <xref:System.ServiceModel.WSFederationHttpBinding> ve kimlik bilgisi herhangi bir istemci olarak verilen bir belirteç olan sistem tarafından sağlanan bağlamalar türü.  
  
 Bu ayrıca, aşağıdaki yöntemlerden birini kullanarak özel bağlama oluşturma oluşur:  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenBindingElement%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForCertificateBindingElement%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForSslBindingElement%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenOverTransportBindingElement%2A>  
  
 Bunu azaltmak için yetkilendirme ilkesi, eylem ve süre sonu zamanı her yetkilendirme ilkesinin denetlemelisiniz.  
  
## <a name="the-service-uses-a-different-certificate-than-the-client-intended"></a>Hizmet, istemci istenen değerinden farklı bir sertifika kullanır.  
 Belirli koşullar altında bir istemci dijital olarak bir X.509 sertifikası içeren bir ileti oturum ve hedeflenen olandan farklı bir sertifika almak hizmet olmalıdır.  
  
 Bu şu durumlarda oluşabilir:  
  
-   İstemci bir X.509 sertifikası kullanarak ileti dijital imzalar ve X.509 sertifikası iletiye eklemek değil, ancak yerine yalnızca kendi konu anahtarı tanımlayıcısı kullanarak sertifikaya başvurur.  
  
-   Hizmetin bilgisayar aynı ortak anahtara sahip iki veya daha fazla sertifikaları içerir, ancak farklı bilgiler içerir.  
  
-   Konu anahtarı tanımlayıcısı eşleşen bir sertifika hizmet alır, ancak istemci kullanmak için amaçlanan bir değil. Zaman [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iletiyi alır ve imzayı doğrular [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne istemcisi beklenenden farklı ve büyük olasılıkla yükseltilmiş talepler kümesi için istenmeyen X.509 sertifikası bilgileri eşler.  
  
 Başvuru X.509 Sertifika kullanarak gibi başka bir yolu, bunu azaltmak için <xref:System.ServiceModel.Security.Tokens.X509KeyIdentifierClauseType.IssuerSerial>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenlik Konuları](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [Bilgilerin Açığa Çıkması](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 [Hizmet Reddi](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [Yeniden Yürütme Saldırıları](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 [İzinsiz Değişiklik](../../../../docs/framework/wcf/feature-details/tampering.md)  
 [Desteklenmeyen Senaryolar](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
