---
title: Kimlik Bilgisi Türü Seçme
description: Kimlik bilgileri, WCF 'de nasıl kullanıldıkları ve bir talep edilen kimlik veya özellik oluşturmak için uygulamanızın doğru kimlik bilgisini nasıl seçeceğinizi öğrenin.
ms.date: 03/30/2017
ms.assetid: bf707063-3f30-4304-ab53-0e63413728a8
ms.openlocfilehash: 7a8a6880e5fc3982bb7f470c34a77c771c26effd
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244926"
---
# <a name="selecting-a-credential-type"></a>Kimlik Bilgisi Türü Seçme
*Kimlik bilgileri* , istenen bir kimlik veya özellik oluşturmak için WINDOWS COMMUNICATION FOUNDATION (WCF) tarafından kullanılan veri bilgileridir. Örneğin, bir Passport bir ülkede veya bölgede vatandaşlık kanıtlayan kamu sorunları için bir kimlik bilgileridir. WCF 'de kimlik bilgileri, Kullanıcı adı belirteçleri ve X. 509.440 sertifikaları gibi birçok biçimde olabilir. Bu konuda kimlik bilgileri, WCF 'de nasıl kullanıldıkları ve uygulamanız için doğru kimlik bilgisinin nasıl oluşturulacağı açıklanmaktadır.  
  
 Birçok ülkede ve bölgede, bir sürücünün lisansı bir kimlik bilgisi örneğidir. Bir lisans, bir kişinin kimliğini ve yeteneklerini temsil eden verileri içerir. Bu, desessor 'ın resmi biçiminde sahip olma kanıtını içerir. Lisans, genellikle bir lisanslama Bakanlığı olan güvenilen bir yetkili tarafından verilir. Lisans mühürlü ve üzerinde oynanmadığını veya onay yapılmadığını gösteren bir hologram içerebilir.  
  
 Bir kimlik bilgisi sunmak, verilerin hem verilerin hem de sahip olma kanıtını içerir. WCF, hem aktarım hem de ileti güvenlik düzeylerinde çeşitli kimlik bilgileri türlerini destekler. Örneğin, WCF: Kullanıcı adı ve (X. 509.440) sertifika kimlik bilgileri ' nde desteklenen iki kimlik bilgileri türünü göz önünde bulundurun.  
  
 Kullanıcı adı kimlik bilgisi için Kullanıcı adı, istenen kimliği temsil eder ve parola, elinde bulunan bir kanıt sağlar. Bu durumda güvenilen yetkili, Kullanıcı adını ve parolasını doğrulayan sistemidir.  
  
 X. 509.440 sertifika kimlik bilgileri ile, sertifika içindeki konu adı, konu diğer adı veya belirli alanlar kimlik talepleri olarak, ve alanları gibi diğer alanlar ise `Valid From` `Valid To` sertifikanın geçerliliğini belirtir.  
  
## <a name="transport-credential-types"></a>Aktarım kimlik bilgisi türleri  
 Aşağıdaki tabloda, aktarım güvenliği modundaki bir bağlama tarafından kullanılabilecek olası istemci kimlik bilgileri türleri gösterilmektedir. Bir hizmet oluştururken, `ClientCredentialType` istemcinin hizmetinize iletişim kurmak için sağlaması gereken kimlik bilgilerinin türünü belirtmek için özelliği bu değerlerden birine ayarlayın. Türleri koddaki veya yapılandırma dosyalarındaki şekilde ayarlayabilirsiniz.  
  
|Ayar|Description|  
|-------------|-----------------|  
|Yok|İstemcinin herhangi bir kimlik bilgisi sunması gerekmediğini belirtir. Bu, anonim bir istemciyi dönüştürür.|  
|Temel|İstemci için temel kimlik doğrulamasını belirtir. Daha fazla bilgi için bkz. RFC2617 —[http kimlik doğrulaması: temel ve Özet kimlik doğrulaması](ftp://ftp.rfc-editor.org/in-notes/rfc2617.txt).|  
|Bilgisi|İstemci için Özet kimlik doğrulamasını belirtir. Daha fazla bilgi için bkz. RFC2617 —[http kimlik doğrulaması: temel ve Özet kimlik doğrulaması](ftp://ftp.rfc-editor.org/in-notes/rfc2617.txt).|  
|NT|NT LAN Manager (NTLM) kimlik doğrulamasını belirtir. Bu, bir nedenden dolayı Kerberos kimlik doğrulamasını kullanmanızın ardından kullanılır. Ayrıca, özelliğini olarak ayarlayarak geri dönüş olarak kullanımını devre dışı bırakabilirsiniz <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> `false` . Bu, WCF 'nin NTLM kullanılıyorsa bir özel durum oluşturmak için en iyi çaba oluşturmasına neden olur. Bu özelliği olarak ayarlamanın `false` , NTLM kimlik bilgilerinin tel üzerinden gönderilmesini engelleyemeyeceğini unutmayın.|  
|Windows|Windows kimlik doğrulamasını belirtir. Yalnızca bir Windows etki alanında Kerberos protokolünü belirtmek için <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> özelliğini olarak ayarlayın `false` (varsayılan değer `true` ).|  
|Sertifika|Bir X. 509.440 sertifikası kullanarak istemci kimlik doğrulaması gerçekleştirir.|  
|Parola|Kullanıcının bir Kullanıcı adı ve parola sağlaması gerekir. Kullanıcı adı/parola çiftini Windows kimlik doğrulaması veya başka bir özel çözüm kullanarak doğrulayın.|  
  
### <a name="message-client-credential-types"></a>İleti Istemci kimlik bilgisi türleri  
 Aşağıdaki tabloda, ileti güvenliği kullanan bir uygulama oluştururken kullanabileceğiniz olası kimlik bilgisi türleri gösterilmektedir. Bu değerleri, kod veya yapılandırma dosyalarında kullanabilirsiniz.  
  
|Ayar|Description|  
|-------------|-----------------|  
|Yok|İstemcinin bir kimlik bilgisi sunması gerekmediğini belirtir. Bu, anonim bir istemciyi dönüştürür.|  
|Windows|SOAP ileti değişimlerinin Windows kimlik bilgileriyle kurulu güvenlik bağlamı altında oluşmasına izin verir.|  
|Kullanıcı adı|Hizmetin, istemcinin kimliğinin Kullanıcı adı kimlik bilgileriyle doğrulanmasını gerektirmesini sağlar. WCF, bir imza oluşturma veya veri şifreleme gibi kullanıcı adlarıyla herhangi bir şifreleme işlemine izin vermediğini unutmayın. WCF, Kullanıcı adı kimlik bilgileri kullanılırken taşımanın güvenli olmasını sağlar.|  
|Sertifika|Hizmetin bir X. 509.952 sertifikası kullanarak kimlik doğrulaması yapmasını gerektirmesini sağlar.|  
|Verilen belirteç|Bir güvenlik ilkesine göre yapılandırılmış özel bir belirteç türü. Varsayılan belirteç türü güvenlik onaylama işlemi biçimlendirme dili (SAML) ' dir. Belirteç, güvenli bir belirteç hizmeti tarafından verilir. Daha fazla bilgi için bkz. [Federasyon ve verilen belirteçler](federation-and-issued-tokens.md).|  
  
### <a name="negotiation-model-of-service-credentials"></a>Hizmet kimlik bilgilerinin anlaşma modeli  
 *Anlaşma* , kimlik bilgilerini değiştirerek bir istemci ve hizmet arasında güven oluşturma işlemidir. İşlem, istemci ve hizmet arasında yinelemeli olarak gerçekleştirilir, bu nedenle yalnızca anlaşma sürecinde bir sonraki adım için gereken bilgileri açıklayana. Uygulamada, nihai sonuç bir hizmetin kimlik bilgisinin sonraki işlemlerde kullanılacak istemciye teslim edilmesiyle sonuçlanır.  
  
 Tek bir özel durum ile, varsayılan olarak WCF 'deki sistem tarafından sağlanmış bağlamalar, ileti düzeyinde güvenlik kullanırken hizmet kimlik bilgilerini otomatik olarak görüşyordu. (Özel durum, <xref:System.ServiceModel.BasicHttpBinding> Varsayılan olarak güvenliği etkinleştirmez.) Bu davranışı devre dışı bırakmak için <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> ve <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.NegotiateServiceCredential%2A> özelliklerine bakın.  
  
> [!NOTE]
> SSL güvenliği .NET Framework 3,5 ve üzeri bir sürümde kullanıldığında, bir WCF istemcisi hem sertifika deposundaki ara sertifikaları hem de hizmetin sertifikasında sertifika zinciri doğrulaması gerçekleştirmek için SSL anlaşması sırasında alınan ara sertifikaları kullanır. .NET Framework 3,0 yalnızca yerel sertifika deposunda yüklü olan ara sertifikaları kullanır.  
  
#### <a name="out-of-band-negotiation"></a>Bant dışı anlaşma  
 Otomatik anlaşma devre dışıysa, hizmete herhangi bir ileti gönderilmeden önce hizmet kimlik bilgisinin istemcide sağlanması gerekir. Bu, *bant dışı* sağlama olarak da bilinir. Örneğin, belirtilen kimlik bilgisi türü bir sertifika ise ve otomatik anlaşma devre dışıysa, istemcinin istemci uygulamasını çalıştıran bilgisayara sertifikayı alıp yüklemesi için hizmet sahibiyle iletişim kurabilmesi gerekir. Bu, örneğin, bir işletmeden işletmeye senaryosundaki bir hizmete hangi istemcilerin erişebileceğini kesinlikle denetlemek istediğinizde yapılabilir. Bu bant dışı anlaşma, e-posta ile yapılabilir ve X. 509.440 sertifikası, Microsoft Yönetim Konsolu (MMC) sertifikaları ek bileşeni gibi bir araç kullanılarak Windows sertifika deposunda depolanır.  
  
> [!NOTE]
> <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>Özelliği, bant dışı anlaşmasına göre kullanıma hazır bir sertifikayla hizmeti sağlamak için kullanılır. <xref:System.ServiceModel.BasicHttpBinding>Bağlama otomatik anlaşmaya izin vermediğinden, sınıfı kullanılırken bu gereklidir. Özelliği, bağıntılı olmayan bir çift yönlü senaryoda da kullanılır. Bu, bir sunucunun istemciye istek göndermesi gerekmeden istemciye bir ileti gönderdiği bir senaryodur. Sunucu istemciden bir istek içermediğinden, iletiyi istemciye şifrelemek için istemcinin sertifikasını kullanması gerekir.  
  
## <a name="setting-credential-values"></a>Kimlik bilgisi değerlerini ayarlama  
 Bir güvenlik modu seçtikten sonra, gerçek kimlik bilgilerini belirtmeniz gerekir. Örneğin, kimlik bilgisi türü "sertifika" olarak ayarlanırsa, belirli bir kimlik bilgisini (örneğin, belirli bir X. 509.440 sertifikası) hizmet veya istemciyle ilişkilendirmeniz gerekir.  
  
 Bir hizmet veya istemci programlama yönteminize bağlı olarak, kimlik bilgisi değerini ayarlama yöntemi biraz farklılık gösterir.  
  
### <a name="setting-service-credentials"></a>Hizmet kimlik bilgilerini ayarlama  
 Aktarım modunu kullanıyorsanız ve aktarım olarak HTTP kullanıyorsanız, Internet Information Services (IIS) kullanmanız veya bağlantı noktasını bir sertifikayla yapılandırmanız gerekir. Daha fazla bilgi için bkz. [Aktarım güvenliğine genel bakış](transport-security-overview.md) ve [http aktarım güvenliği](http-transport-security.md).  
  
 Kodda kimlik bilgileriyle bir hizmet sağlamak için, sınıfının bir örneğini oluşturun <xref:System.ServiceModel.ServiceHost> ve <xref:System.ServiceModel.Description.ServiceCredentials> özelliği aracılığıyla erişilen sınıfını kullanarak uygun kimlik bilgisini belirtin <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> .  
  
#### <a name="setting-a-certificate"></a>Sertifika ayarlama  
 İstemcilere hizmetin kimliğini doğrulamak için kullanılacak X. 509.440 sertifikasıyla bir hizmet sağlamak için, <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.SetCertificate%2A> sınıfının yöntemini kullanın <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> .  
  
 İstemci sertifikası ile bir hizmet sağlamak için, <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> sınıfının yöntemini kullanın <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential> .  
  
#### <a name="setting-windows-credentials"></a>Windows kimlik bilgilerini ayarlama  
 İstemci geçerli bir Kullanıcı adı ve parola belirtiyorsa, istemcinin kimliğini doğrulamak için bu kimlik bilgileri kullanılır. Aksi takdirde, oturum açmış geçerli kullanıcının kimlik bilgileri kullanılır.  
  
### <a name="setting-client-credentials"></a>Istemci kimlik bilgilerini ayarlama  
 WCF 'de, istemci uygulamaları hizmetlere bağlanmak için bir WCF istemcisi kullanır. Her istemci <xref:System.ServiceModel.ClientBase%601> sınıfından türetilir ve <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> istemcideki özelliği, istemci kimlik bilgilerinin çeşitli değerlerinin belirtimine izin verir.  
  
#### <a name="setting-a-certificate"></a>Sertifika ayarlama  
 Bir hizmette istemcinin kimliğini doğrulamak için kullanılan X. 509.440 sertifikasıyla bir hizmet sağlamak için, <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> sınıfının yöntemini kullanın <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> .  
  
## <a name="how-client-credentials-are-used-to-authenticate-a-client-to-the-service"></a>İstemci kimlik bilgileri, hizmette bir Istemcinin kimliğini doğrulamak için nasıl kullanılır  
 Bir hizmetle iletişim kurmak için gereken istemci kimlik bilgileri, <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> özelliği veya özelliği kullanılarak sağlanır <xref:System.ServiceModel.ChannelFactory.Credentials%2A> . Güvenlik kanalı, bu bilgileri istemcinin kimliğini doğrulamak için kullanır. Kimlik doğrulaması iki moddan biri aracılığıyla gerçekleştirilir:  
  
- İstemci kimlik bilgileri, ilk ileti gönderilmeden önce, bir güvenlik bağlamı oluşturmak için WCF istemci örneği kullanılarak kullanılır. Tüm uygulama iletileri daha sonra güvenlik bağlamı aracılığıyla güvenli hale getirilir.  
  
- İstemci kimlik bilgileri, hizmete gönderilen her uygulama iletisinin kimliğini doğrulamak için kullanılır. Bu durumda, istemci ve hizmet arasında hiçbir bağlam kurulmaz.  
  
### <a name="established-identities-cannot-be-changed"></a>Belirlenen kimlikler değiştirilemez  
 İlk yöntem kullanıldığında, belirlenen bağlam, istemci kimliğiyle kalıcı olarak ilişkilendirilir. Diğer bir deyişle, güvenlik bağlamı kurulduktan sonra istemciyle ilişkili kimlik değiştirilemez.  
  
> [!IMPORTANT]
> Kimliğin ne zaman geçmediği (yani güvenlik bağlamı oluşturma sırasında, varsayılan davranış) bilinmesi gereken bir durum vardır. İkinci bir hizmetle iletişim kuran bir hizmet oluşturursanız, ikinci hizmette WCF istemcisini açmak için kullanılan kimlik değiştirilemez. Bu, birden çok istemcinin ilk hizmeti kullanmasına izin veriliyorsa ve hizmetin ikinci hizmete erişirken istemcileri taklit ettiğinde bir sorun haline gelir. Hizmet tüm çağıranlar için aynı istemciyi yeniden kullanıyorsa, ikinci hizmete yapılan tüm çağrılar istemciyi ikinci hizmete açmak için kullanılan ilk çağıranın kimliği altında yapılır. Diğer bir deyişle, hizmet, ikinci hizmetle iletişim kurmak üzere tüm istemcileri için ilk istemcinin kimliğini kullanır. Bu, ayrıcalık yükselmesine neden olabilir. Bu, hizmetinizin istenen davranışı değilse, her bir çağrıyı izlemeniz ve her ayrı arayan için ikinci hizmete yeni bir istemci oluşturmanız ve hizmetin ikinci hizmetle iletişim kurması için yalnızca doğru çağıran istemciyi kullandığından emin olmanız gerekir.  
  
 Kimlik bilgileri ve güvenli oturumlar hakkında daha fazla bilgi için bkz. [Güvenli Oturumlar Için güvenlik konuları](security-considerations-for-secure-sessions.md).  
  
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
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.SetCertificate%2A?displayProperty=nameWithType>
- [Güvenlik kavramları](security-concepts.md)
- [Hizmet ve İstemcileri Güvenli Hale Getirme](securing-services-and-clients.md)
- [WCF Güvenliğini Programlama](programming-wcf-security.md)
- [HTTP Aktarım Güvenliği](http-transport-security.md)
