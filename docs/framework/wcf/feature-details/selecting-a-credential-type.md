---
title: Kimlik Bilgisi Türü Seçme
ms.date: 03/30/2017
ms.assetid: bf707063-3f30-4304-ab53-0e63413728a8
ms.openlocfilehash: 8aa959aa952e839039bebffddddd951fbc1eb0d4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59167849"
---
# <a name="selecting-a-credential-type"></a>Kimlik Bilgisi Türü Seçme
*Kimlik bilgileri* Windows Communication Foundation (WCF) kullanan bir talep kimliği veya özellikleri kurmak için verilerdir. Örneğin, bir passport bir devlet kurumu sorunlarını ülke veya bölgenizde Vatandaşlık kanıtlamak için bir kimlik bilgisi ' dir. WCF'de, kullanıcı adı belirteçleri ve X.509 sertifikaları gibi birçok forms kimlik bilgilerini alabilir. Bu konuda, kimlik bilgileri, WCF'de nasıl kullanılacağını ve nasıl seçileceğini, uygulamanız için doğru kimlik bilgisi anlatılmaktadır.  
  
 Bir sürücünün lisans bir fazla ülke ve bölge içinde bir kimlik bilgisi örneğidir. Bir lisansı, bir kişinin kimlik ve özellikleri temsil eden veri içerir. Bu kaynağı'nın resmi biçiminde kanıtını içerir. Lisans, genellikle lisanslama kamu departmanı gibi güvenilir bir yetkili tarafından verilmiş. Lisans, korumalı ve onu olmayan kurcalanmadığından veya sahtesi olduğunu gösteren, bir hologramı içerebilir.  
  
 Bir kimlik bilgisi sunma hem verileri hem de veri kanıtını sunma içerir. WCF çeşitli hem aktarım hem de ileti güvenlik düzeylerinde kimlik bilgisi türlerini destekler. Örneğin, iki tür WCF'de desteklenen kimlik bilgileri göz önünde bulundurun: sertifika kimlik bilgileri kullanıcı adı ve (X.509).  
  
 Kullanıcı adı kimlik bilgisi için kullanıcı adını temsil eden talep kimliğini ve parolayı kanıtını sağlar. Güvenilir yetkili bu durumda kullanıcı adını ve parolayı doğrular sistemidir.  
  
 X.509 sertifika kimlik bilgileriyle konu adı, konu alternatif adı veya sertifika belirli alanları olarak talep kimliğinin diğer alanlarında çalışırken gibi kullanılabilir `Valid From` ve `Valid To` geçerliliğini alanları belirtin Sertifika.  
  
## <a name="transport-credential-types"></a>Kimlik bilgisi türlerinin taşıma  
 Aşağıdaki tabloda, olası bir transport güvenlik modunu bağlama tarafından kullanılan istemci kimlik bilgileri türleri gösterilmektedir. Bir hizmet oluştururken şu ayarları yapın `ClientCredentialType` özelliğini hizmetinizle iletişim kurmak için istemci sağlamalısınız kimlik bilgisi türünü belirtmek için şu değerlerden biri. Kod veya yapılandırma dosyalarında türleri ayarlayabilirsiniz.  
  
|Ayar|Açıklama|  
|-------------|-----------------|  
|Yok.|İstemci mevcut herhangi bir kimlik bilgisi gerekmez belirtir. Bu, anonim bir istemciye dönüşür.|  
|Temel|Temel kimlik doğrulaması için istemci belirtir. Ek bilgi için bkz: RFC2617 —[HTTP kimlik doğrulaması: Temel ve Özet kimlik doğrulama](https://go.microsoft.com/fwlink/?LinkID=88313).|  
|Özet|Özet kimlik doğrulaması için istemci belirtir. Ek bilgi için bkz: RFC2617 —[HTTP kimlik doğrulaması: Temel ve Özet kimlik doğrulama](https://go.microsoft.com/fwlink/?LinkID=88313).|  
|NTLM|NT LAN Manager (NTLM) kimlik doğrulaması belirtir. Bu, herhangi bir nedenle Kerberos kimlik doğrulaması kullanamadığınızda kullanılır. Ayarlayarak da bir geri dönüş olarak kullanılmasını devre dışı bırakabilirsiniz <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> özelliğini `false`, bir NTLM kullanılırsa, bir özel durum için mümkün olan en iyi hale getirmek WCF neden olur. Unutmayın, bu özelliği ayarlamak `false` NTLM kimlik bilgileri kablo üzerinden gönderilen engelleyemeyebilir.|  
|Windows|Windows kimlik doğrulaması belirtir. Bir Windows etki alanında yalnızca Kerberos protokolü belirtmek için ayarlayın <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> özelliğini `false` (varsayılan değer `true`).|  
|Sertifika|X.509 sertifikası kullanarak istemci kimlik doğrulaması gerçekleştirir.|  
|Parola|Kullanıcı, bir kullanıcı adı ve parola sağlamanız gerekir. Windows kimlik doğrulaması veya başka bir özel bir çözüm kullanarak kullanıcı adı/parola çifti doğrulayın.|  
  
### <a name="message-client-credential-types"></a>İleti istemci kimlik bilgisi türleri  
 İleti güvenliği kullanan bir uygulama oluşturma sırasında kullanabileceğiniz olası kimlik bilgisi türleri aşağıdaki tabloda gösterilmektedir. Kod veya yapılandırma dosyalarında bu değerleri kullanabilirsiniz.  
  
|Ayar|Açıklama|  
|-------------|-----------------|  
|None|İstemci mevcut bir kimlik bilgisi gerekmez belirtir. Bu, anonim bir istemciye dönüşür.|  
|Windows|SOAP ileti alışverişlerinde bir Windows kimlik bilgileri ile oluşturulan güvenlik bağlamı altında gerçekleşmesini sağlar.|  
|Kullanıcı adı|Bir kullanıcı adı kimlik bilgisi ile istemcinin kimliğinin doğrulanmasını gerektiren hizmet sağlar. WCF ile kullanıcı adlarını, imza oluşturma veya verileri şifreleme gibi şifreleme işlemleri izin vermediğini unutmayın. WCF aktarma kullanıcı adı kimlik bilgilerini kullanarak güvenli sağlar.|  
|Sertifika|Gerekli izin verir, istemci kimlik doğrulaması kullanarak bir X.509 sertifikası.|  
|Belirteci veren|Bir güvenlik ilkesine göre yapılandırılmış özel bir simge türü. Varsayılan simge güvenlik onaylama işaretleme dili (SAML) türüdür. Belirteç güvenli belirteç hizmeti tarafından verilir. Daha fazla bilgi için [Federasyon ve verilen belirteçler](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).|  
  
### <a name="negotiation-model-of-service-credentials"></a>Hizmet kimlik bilgilerini belirleme modelinin  
 *Anlaşma* kimlik değişimi ile bir istemci ve hizmet arasında güven oluşturma işlemidir. İşlem, istemciyi ve hizmeti yalnızca anlaşma işlemi bir sonraki adım için gerekli bilgileri ifşa bileşenlerinizi arasında yinelemeli olarak gerçekleştirilir. Uygulamada, bir hizmetin kimlik bilgisi istemcinin sonraki işlemlerde kullanılan teslimini son sonucudur.  
  
 Bir özel durum ile varsayılan olarak sistem tarafından sağlanan bağlamalar WCF hizmeti kimlik bilgileri otomatik olarak ileti düzeyi güvenlik kullanılırken anlaşır. (Özel durum <xref:System.ServiceModel.BasicHttpBinding>, hangi sağlamaz güvenlik varsayılan.) Bu davranışı devre dışı bırakmak için bkz: <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> ve <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.NegotiateServiceCredential%2A> özellikleri.  
  
> [!NOTE]
>  SSL güvenlik .NET Framework 3.5 ve üzeri kullanıldığında, bir WCF istemcisi hem kendi sertifika deposu Ara sertifikaları ve SSL anlaşması sırasında alınan Ara sertifikaları hizmetin üzerinde sertifika zinciri doğrulamayı gerçekleştirmek için kullanır Sertifika. .NET framework 3.0, yalnızca yerel sertifika deposunda yüklü Ara sertifikaları kullanır.  
  
#### <a name="out-of-band-negotiation"></a>Bant dışı anlaşması  
 Otomatik anlaşması devre dışıysa, hizmete herhangi bir ileti göndermeden önce istemci hizmeti kimlik bilgileri sağlanmalıdır. Bu olarak da bilinen, bir *bant dışı* sağlama. Örneğin, bir sertifika belirtilen kimlik bilgisi türüdür ve otomatik anlaşma devre dışı ise istemci almak ve istemci uygulamasını çalıştıran bilgisayarda sertifikayı yüklemek için hizmet sahibi başvurmanız gerekir. Hangi istemcilerin işletmeler arası senaryosunda bir hizmete erişebilir sıkı bir şekilde denetlemek istediğinizde bu, örneğin, yapılabilir. Bu çıkış,-bant-anlaşma e-posta ile yapılabilir ve X.509 sertifikası, Microsoft Yönetim Konsolu (MMC) Sertifikalar ek bileşenini gibi bir araç kullanarak Windows sertifika deposunda depolanır.  
  
> [!NOTE]
>  <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> Özelliği, bant dışı anlaşması ile ulaşılan bir sertifika ile hizmet sağlamak amacıyla kullanılır. Kullanılırken bu gereklidir <xref:System.ServiceModel.BasicHttpBinding> sınıfı bağlamaya izin vermez çünkü otomatik anlaşması. Özelliği de uncorrelated çift yönlü bir senaryoda kullanılır. Bu, burada bir sunucu ileti bir istek sunucuya ilk göndermek istemci gerek kalmadan istemciye bir senaryodur. Sunucu, istemciden gelen istekte olmadığı için bu istemciye iletiyi şifrelemek için istemci sertifikasını kullanmanız gerekir.  
  
## <a name="setting-credential-values"></a>Kimlik bilgisi değerleri ayarlama  
 Güvenlik modu seçtikten sonra gerçek kimlik bilgileri belirtmeniz gerekir. Kimlik bilgisi türü "sertifika için" olarak ayarlanırsa, ardından, belirli kimlik bilgileri (örneğin, belirli bir X.509 sertifikası) hizmet veya istemci ile ilişkilendirmeniz gerekir.  
  
 İster bir hizmet veya istemci programlama bağlı olarak, kimlik bilgisi değeri ayarlamak için yöntemi biraz farklıdır.  
  
### <a name="setting-service-credentials"></a>Hizmet kimlik bilgilerini ayarlama  
 Aktarım Modu kullanıyorsanız ve HTTP aktarım olarak kullanıyorsanız, ya da Internet Information Services (IIS) kullanın veya bir sertifika ile bağlantı noktasını yapılandırın. Daha fazla bilgi için [aktarım güvenliğine genel bakış](../../../../docs/framework/wcf/feature-details/transport-security-overview.md) ve [HTTP aktarım güvenliği](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
 Kod içinde kimlik bilgilerine sahip bir hizmet sağlamak için bir örneğini oluşturmak <xref:System.ServiceModel.ServiceHost> sınıfı ve uygun kimlik bilgilerini kullanarak belirttiğiniz <xref:System.ServiceModel.Description.ServiceCredentials> aracılığıyla erişilebilen sınıfı <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> özelliği.  
  
#### <a name="setting-a-certificate"></a>Sertifika ayarlama  
 İstemciler hizmete kimlik doğrulaması için kullanılan X.509 sertifikası ile bir hizmet sağlamak için kullanmak <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.SetCertificate%2A> yöntemi <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> sınıfı.  
  
 Bir istemci sertifikası ile bir hizmeti sağlamak için kullanın <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> yöntemi <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential> sınıfı.  
  
#### <a name="setting-windows-credentials"></a>Windows kimlik bilgilerini ayarlama  
 İstemci geçerli bir kullanıcı adı ve parola belirtiyorsa, bu kimlik bilgisi istemcinin kimliğini doğrulamak için kullanılır. Aksi takdirde, geçerli oturum açan kullanıcının kimlik bilgileri kullanılır.  
  
### <a name="setting-client-credentials"></a>İstemci kimlik bilgilerini ayarlama  
 WCF'de, istemci uygulamaları hizmetlerine bağlanmak için bir WCF istemcisi kullanır. Her istemci türetildiği <xref:System.ServiceModel.ClientBase%601> sınıfı ve <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> özelliği istemcideki çeşitli istemci kimlik bilgileri değerlerini belirtimi sağlar.  
  
#### <a name="setting-a-certificate"></a>Sertifika ayarlama  
 Bir hizmete istemcinin kimliğini doğrulamak için kullanılan X.509 sertifikası ile bir hizmet sağlamak için kullanmak <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> yöntemi <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> sınıfı.  
  
## <a name="how-client-credentials-are-used-to-authenticate-a-client-to-the-service"></a>Bir hizmete istemcinin kimliğini doğrulamak için istemci kimlik bilgileri nasıl kullanılır  
 Bir hizmetle iletişim kurmak için gereken istemci kimlik bilgilerini kullanarak sağlanan <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> özelliği veya <xref:System.ServiceModel.ChannelFactory.Credentials%2A> özelliği. Güvenlik kanalı hizmete istemcinin kimliğini doğrulamak için bu bilgileri kullanır. Kimlik doğrulama, iki moddan birini gerçekleştirilir:  
  
-   Bir güvenlik bağlamı'kurmak için WCF istemci örneği kullanarak ilk ileti gönderilmeden önce istemci kimlik bilgileri bir kez kullanılır. Tüm uygulama iletileri ardından güvenlik bağlamı olarak güvenlidir.  
  
-   İstemci kimlik bilgileri, hizmete gönderilen her bir uygulama iletisi kimliğini doğrulamak için kullanılır. Bu durumda, istemci ile hizmet arasında hiçbir bağlam kurulur.  
  
### <a name="established-identities-cannot-be-changed"></a>Kurulan kimlikleri değiştirilemez  
 İlk yöntem kullanıldığında, belirlenen bağlamı için istemci kimliği ile kalıcı olarak ilişkilendirilir. Güvenlik bağlamı kurulduktan sonra diğer bir deyişle, istemciyle ilişkili kimliği değiştirilemez.  
  
> [!IMPORTANT]
>  Ne zaman kimlik alınamaz dikkat etmeniz bir durum yoktur (diğer bir deyişle, güvenlik zaman kurmak bağlam, varsayılan davranıştır). İkinci bir hizmet ile iletişim kuran bir hizmeti oluşturursanız, ikinci hizmeti WCF İstemcisi'ni açmak için kullanılan kimliği değiştirilemez. Bu birden çok istemci ilk hizmeti kullanmasına izin verilen ve ikinci hizmet erişirken istemcilere hizmet kimliğine bürünür bir sorun haline gelir. Tüm arayanlar için aynı istemci hizmeti kullanır, tüm ikinci hizmete çağrı çağıranın kimliğini, ikinci Hizmeti İstemcisi'ni açmak için kullanılan ilk altında gerçekleştirilir. Diğer bir deyişle, hizmet, tüm istemciler için ilk istemci kimliğini ikinci hizmetiyle iletişim kurmak için kullanır. Bu, ayrıcalıkların yükseltilmesine neden olabilir. İstenen davranışı hizmetinizin bu değilse, her çağıranın izlemek ve oluşturmak için her ayrı çağıran ikinci hizmetini yeni bir istemci ve hizmet ikinci hizmetiyle iletişim kurmak için yalnızca doğru arayan için doğru istemci kullandığından emin olun.  
  
 Kimlik bilgileri ve güvenli oturumlar hakkında daha fazla bilgi için bkz: [güvenli oturumlar için güvenlik konuları](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpMessageSecurity.ClientCredentialType%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageSecurityOverMsmq.ClientCredentialType%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.SetCertificate%2A?displayProperty=nameWithType>
- [Güvenlik Kavramları](../../../../docs/framework/wcf/feature-details/security-concepts.md)
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [WCF Güvenliğini Programlama](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
- [HTTP Aktarım Güvenliği](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
