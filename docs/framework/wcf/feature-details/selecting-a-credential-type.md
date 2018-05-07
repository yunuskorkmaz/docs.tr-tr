---
title: Kimlik Bilgisi Türü Seçme
ms.date: 03/30/2017
ms.assetid: bf707063-3f30-4304-ab53-0e63413728a8
ms.openlocfilehash: 756017462ccaf8a555b0634e8a43cfdd3bc63d32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="selecting-a-credential-type"></a>Kimlik Bilgisi Türü Seçme
*Kimlik bilgileri* Windows Communication Foundation (WCF) kullanan bir talep kimliği veya özellikleri oluşturmak için verileri. Örneğin, passport bir kamu sorunlarını vatandaşlığa benzer bir ülke veya bölgedeki kanıtlamak için bir kimlik bilgisi ' dir. WCF'de, X.509 sertifikalar ve kullanıcı adı belirteçleri gibi birçok forms kimlik bilgilerini alabilir. Bu konuda, kimlik bilgileri, WCF nasıl kullanıldıkları ve uygulamanız için doğru kimlik bilgilerini seçme nasıl ele alınmıştır.  
  
 Birçok ülke ve bölgelerden içinde bir sürücünün lisans bir kimlik bilgisi örneğidir. Bir lisans kişinin kimlik ve özellikleri temsil eden veri içeriyor. Sahibi'nın resmi biçiminde kanıtını içerir. Lisans, lisans, genellikle bir kamu bölüm gibi güvenilir bir yetkili tarafından verilir. Lisans korumalı ve değil değiştirilmiş veya bırakıldığı sahtesi olduğunu gösteren bir hologramı içerebilir.  
  
 Bir kimlik bilgisi sunan hem veri hem de veri kanıtını sunan içerir. WCF çeşitli güvenlik düzeyleri taşıma ve ileti kimlik bilgisi türlerini destekler. Örneğin, iki tür WCF'de desteklenen kimlik bilgileri göz önünde bulundurun: sertifika kimlik bilgileri kullanıcı adı ve (X.509).  
  
 Kullanıcı adı kimlik bilgisi için kullanıcı adı talep kimliğini temsil eder ve kanıtını parolasını sağlar. Güvenilir yetkili bu durumda kullanıcı adını ve parolayı doğrular sistemidir.  
  
 Bir X.509 sertifikası kimlik bilgileriyle konu adı, konu alternatif adı veya sertifika içinde belirli alanları olarak diğer alanlar sırasında kimlik talepleri gibi kullanılabilir `Valid From` ve `Valid To` alanları, geçerlilik süresini belirtin Sertifika.  
  
## <a name="transport-credential-types"></a>Aktarım kimlik bilgisi türleri  
 Aşağıdaki tabloda olası Aktarım güvenlik modunda bir bağlama tarafından kullanılan istemci kimlik bilgisi türlerinin kullanılmasını gösterir. Bir hizmet oluştururken ayarlama `ClientCredentialType` istemci hizmeti ile iletişim kurmak için sağlamalısınız kimlik bilgisi türünü belirtmek için bu değerlerden birini özelliği. Kod veya yapılandırma dosyalarında türleri ayarlayabilirsiniz.  
  
|Ayar|Açıklama|  
|-------------|-----------------|  
|Yok.|İstemci kimlik sunmak gerekmez belirtir. Anonim istemci için çevirir.|  
|Temel|Temel kimlik doğrulaması için istemci belirtir. Ek bilgi için bkz: RFC2617 —[HTTP kimlik doğrulaması: temel ve Özet kimlik doğrulaması](http://go.microsoft.com/fwlink/?LinkID=88313).|  
|Özet|Özet kimlik doğrulaması için istemci belirtir. Ek bilgi için bkz: RFC2617 —[HTTP kimlik doğrulaması: temel ve Özet kimlik doğrulaması](http://go.microsoft.com/fwlink/?LinkID=88313).|  
|NTLM|NT LAN Yöneticisi (NTLM) kimlik doğrulamasını belirtir. Bu, Kerberos kimlik doğrulaması için herhangi bir nedenle kullanılamaz olduğunda kullanılır. Ayarlayarak da bir geri dönüş olarak kullanılmasını devre dışı bırakabilirsiniz <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> özelliğine `false`, NTLM kullanılırsa, bir özel durum için bir en iyi çaba yapmak WCF neden olur. Bu özelliği ayarlamak Not `false` NTLM kimlik bilgileri kablo üzerinden gönderilen engelleyebilir değil.|  
|Windows|Windows kimlik doğrulaması belirtir. Bir Windows etki alanında yalnızca Kerberos protokolünü belirtmek için ayarlayın <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> özelliğine `false` (varsayılan `true`).|  
|Sertifika|Bir X.509 sertifikası kullanarak istemci kimlik doğrulaması gerçekleştirir.|  
|Parola|Kullanıcı, bir kullanıcı adı ve parola girmeniz gerekir. Windows kimlik doğrulaması veya başka bir özel çözüm kullanarak kullanıcı adı/parola çifti doğrulayın.|  
  
### <a name="message-client-credential-types"></a>İleti istemcisi kimlik bilgisi türleri  
 Aşağıdaki tabloda, ileti güvenliği kullanan bir uygulama oluşturma kullanabileceğiniz olası kimlik bilgisi türünü gösterir. Kod veya yapılandırma dosyalarında bu değerleri kullanabilirsiniz.  
  
|Ayar|Açıklama|  
|-------------|-----------------|  
|Yok.|İstemci bir kimlik bilgisi sunmak gerekmez belirtir. Anonim istemci için çevirir.|  
|Windows|Windows kimlik bilgileri ile kurulan güvenlik bağlamı altında gerçekleşmesi SOAP ileti alışverişlerinde sağlar.|  
|Kullanıcı adı|Hizmetinin istemci sahip bir kullanıcı adı kimlik bilgisi doğrulanmasını gerektiren izin verir. WCF imza oluşturulurken veya veri şifreleme gibi kullanıcı adları ile şifreleme işlemleri izin verme unutmayın. WCF taşıma kullanıcı adı kimlik bilgileri kullanırken güvenliği sağlar.|  
|Sertifika|Hizmetinin gerektiren izin verir, istemci kimlik doğrulaması X.509 sertifikası kullanarak.|  
|Belirteci veren|Bir güvenlik ilkesine göre yapılandırılmış bir özel simge türü. Varsayılan belirteci güvenlik onaylar biçimlendirme dili (SAML) türüdür. Belirtecin bir güvenli belirteç hizmeti tarafından verilir. Daha fazla bilgi için bkz: [Federasyon ve verilen belirteçleri](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).|  
  
### <a name="negotiation-model-of-service-credentials"></a>Hizmet kimlik bilgileri anlaşma modeli  
 *Anlaşma* kimlik bilgilerini değiştirerek bir istemci ile hizmet arasında güven oluşturma işlemidir. İşlem, istemci ve hizmet, yalnızca sonraki adımda anlaşma işlemi için gerekli bilgileri ifşa amacıyla arasındaki yinelemeli olarak gerçekleştirilir. Uygulamada, bir hizmetin kimlik bilgisinin sonraki işlemlerde kullanılacak istemcisine teslim edilmesini son sonucudur.  
  
 Bunun tek istisnası varsayılan olarak sistem tarafından sağlanan bağlamalar WCF'de hizmet kimlik bilgilerini otomatik olarak ileti düzeyi güvenlik kullanılırken anlaşır. (Özel durum <xref:System.ServiceModel.BasicHttpBinding>, hangi sağlamaz güvenlik varsayılan.) Bu davranışı devre dışı bırakmak için bkz: <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> ve <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.NegotiateServiceCredential%2A> özellikleri.  
  
> [!NOTE]
>  SSL güvenlik .NET Framework 3.5 ve sonraki sürümleriyle birlikte kullanıldığında, bir WCF istemcisi hem SSL anlaşması sırasında alınan Ara sertifikalar ve ara sertifika, sertifika deposunda sertifika zinciri doğrulaması hizmetin üzerinde gerçekleştirmek için kullanır Sertifika. .NET framework 3.0 yalnızca yerel sertifika deposunda yüklü Ara sertifikaları kullanır.  
  
#### <a name="out-of-band-negotiation"></a>Bant dışı anlaşması  
 Otomatik Anlaşma devre dışıysa, hizmete iletileri göndermeden önce istemcide hizmet kimlik bilgileri sağlanmalıdır. Bu da denir bir *bant dışı* sağlama. Örneğin, belirtilen kimlik bilgisi türü bir sertifika olduğundan ve otomatik anlaşma devre dışı, istemci almak ve sertifika istemci uygulaması çalıştıran bilgisayara yüklemek için hizmet sahibi başvurmanız gerekir. Hangi istemcilerin bir iş iş senaryosu hizmetinde erişebileceği kesinlikle denetlemek istediğinizde bu, örneğin, yapılabilir. Bu çıkış,-bant-anlaşma e-posta ile yapılabilir ve X.509 Sertifika Microsoft Yönetim Konsolu (MMC) Sertifikalar ek bileşenini gibi bir araç kullanarak Windows sertifika deposunda saklanır.  
  
> [!NOTE]
>  <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> Özelliği bant dışı anlaşma ulaşılan bir sertifika ile hizmet sağlamak için kullanılır. Kullanılırken bu gereklidir <xref:System.ServiceModel.BasicHttpBinding> sınıfı bağlama izin verme olduğundan otomatik anlaşma. Özellik de uncorrelated çift yönlü senaryosunda kullanılır. Bu, burada bir sunucu bir ileti ilk sunucusuna bir istek göndermek istemci gerek kalmadan istemciye bir senaryodur. Sunucu istemciden gelen istekte sahip olmadığından, bu istemci sertifikasını istemciye iletiyi şifrelemek için kullanmanız gerekir.  
  
## <a name="setting-credential-values"></a>Kimlik bilgisi değerleri ayarlama  
 Güvenlik modu seçtikten sonra asıl kimlik bilgilerini belirtmelisiniz. Kimlik bilgisi türü "sertifika için" ayarlanırsa, örneğin, ardından, belirli kimlik bilgileri (örneğin, belirli bir X.509 sertifikası) hizmet veya istemci ile ilişkilendirmeniz gerekir.  
  
 Olup, bir hizmet veya istemci programlama bağlı olarak, kimlik bilgisi değeri ayarlamak için kullanılan yöntem biraz farklıdır.  
  
### <a name="setting-service-credentials"></a>Hizmet kimlik bilgilerini ayarlama  
 Aktarım Modu kullanıyorsanız ve aktarım olarak HTTP kullanarak, bir sertifika ile bağlantı noktasını yapılandırın veya ya da Internet Information Services (IIS) kullanmanız gerekir. Daha fazla bilgi için bkz: [taşıma güvenliği genel bakış](../../../../docs/framework/wcf/feature-details/transport-security-overview.md) ve [HTTP taşıma güvenliği](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
 Kodda kimlik bilgilerine sahip bir hizmet sağlamak için bir örneğini oluşturmak <xref:System.ServiceModel.ServiceHost> sınıfı ve uygun kimlik bilgilerini kullanarak belirtin <xref:System.ServiceModel.Description.ServiceCredentials> üzerinden erişilen sınıfı <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> özelliği.  
  
#### <a name="setting-a-certificate"></a>Sertifika ayarlama  
 İstemcilere hizmet kimlik doğrulaması için kullanılacak bir X.509 sertifikası ile bir hizmet sağlamak için kullanmanız <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.SetCertificate%2A> yöntemi <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> sınıfı.  
  
 Bir istemci sertifikasına sahip bir hizmet sağlamak için kullanmanız <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> yöntemi <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential> sınıfı.  
  
#### <a name="setting-windows-credentials"></a>Windows kimlik bilgilerini ayarlama  
 İstemcinin geçerli bir kullanıcı adı ve parola belirtiyorsa, bu kimlik bilgisi istemci kimlik doğrulaması için kullanılır. Aksi takdirde, geçerli oturum açmış kullanıcının kimlik bilgileri kullanılır.  
  
### <a name="setting-client-credentials"></a>İstemci kimlik bilgilerini ayarlama  
 WCF'de, istemci uygulamaları hizmetlerine bağlanmak için bir WCF istemcisi kullanır. Her istemci türetilen <xref:System.ServiceModel.ClientBase%601> sınıfı ve <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> istemcide özelliği, istemci kimlik bilgileri çeşitli değerleri belirtimi izin verir.  
  
#### <a name="setting-a-certificate"></a>Sertifika ayarlama  
 Bir hizmet için istemci kimlik doğrulaması için kullanılan bir X.509 sertifikası ile bir hizmet sağlamak için kullanmanız <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> yöntemi <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> sınıfı.  
  
## <a name="how-client-credentials-are-used-to-authenticate-a-client-to-the-service"></a>Hizmet için bir istemci kimlik doğrulaması için istemci kimlik bilgileri nasıl kullanılır  
 Bir hizmeti ile iletişim kurmak için gerekli istemci kimlik bilgileri kullanılarak sağlanır <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> özelliği veya <xref:System.ServiceModel.ChannelFactory.Credentials%2A> özelliği. Güvenlik kanalı hizmeti için istemci kimlik doğrulaması için bu bilgileri kullanır. Kimlik doğrulaması iki moddan birini gerçekleştirilir:  
  
-   Bir güvenlik bağlamı kurmak için WCF istemci örneğini kullanarak ilk ileti gönderilmeden önce istemci kimlik bilgileri bir kez kullanılır. Tüm uygulama iletileri sonra güvenlik bağlamı ile güvenli hale getirilir.  
  
-   İstemci kimlik bilgileri, hizmete gönderilen her uygulama ileti kimlik doğrulaması için kullanılır. Bu durumda, istemci ile hizmet arasında hiçbir bağlam kurulur.  
  
### <a name="established-identities-cannot-be-changed"></a>Oluşturulan kimlikleri değiştirilemez  
 İlk yöntem kullanıldığında, belirlenen bağlamı için istemci kimliği ile kalıcı olarak ilişkilidir. Diğer bir deyişle, istemciyle ilişkili kimlik güvenlik bağlamı kurulduktan sonra değiştirilemez.  
  
> [!IMPORTANT]
>  Ne zaman kimliğini döndürülemez farkında olması için bir durum yok (diğer bir deyişle, ne zaman güvenliğini sağlayın bağlamı, varsayılan davranış olduğu). İkinci bir hizmeti ile iletişim kuran bir hizmet oluşturursanız, ikinci hizmetine WCF İstemcisi'ni açmak için kullanılan kimlik değiştirilemez. Bu bir sorun birden çok istemci ilk hizmetin kullanmasına izin verilen ve ikinci hizmet erişirken istemcilere hizmet taklit haline gelir. Aynı istemci tüm çağıranlar için hizmeti yeniden kullanır, ikinci hizmet tüm çağrıları ikinci hizmet İstemcisi'ni açmak için kullanılan ilk arayan kimliği altında yapılır. Diğer bir deyişle, hizmet ikinci hizmetiyle iletişim kurmak için tüm istemciler için ilk istemci kimliğini kullanır. Bu ayrıcalık yükselmesine yol açabilir. İstenen davranışı hizmetinizin bu değilse, her çağıran izlemek ve yeni bir istemci için her ayrı çağıran ikinci hizmetini oluşturun ve hizmet ikinci hizmetiyle iletişim kurmak için doğru çağıran için yalnızca doğru istemci kullanır olmanız gerekir.  
  
 Kimlik bilgileri ve güvenli oturumlar hakkında daha fazla bilgi için bkz: [güvenli oturumlar için güvenlik konuları](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>  
 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A?displayProperty=nameWithType>  
 <xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A?displayProperty=nameWithType>  
 <xref:System.ServiceModel.BasicHttpMessageSecurity.ClientCredentialType%2A?displayProperty=nameWithType>  
 <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A?displayProperty=nameWithType>  
 <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A?displayProperty=nameWithType>  
 <xref:System.ServiceModel.MessageSecurityOverMsmq.ClientCredentialType%2A?displayProperty=nameWithType>  
 <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A?displayProperty=nameWithType>  
 <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A?displayProperty=nameWithType>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.SetCertificate%2A?displayProperty=nameWithType>  
 [Güvenlik Kavramları](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
 [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [WCF Güvenliğini Programlama](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 [HTTP Aktarım Güvenliği](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
