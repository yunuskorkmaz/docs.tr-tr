---
title: Dağıtılan Uygulama Güvenliği
ms.date: 03/30/2017
helpviewer_keywords:
- distributed application security [WCF]
- security [WCF], transfer
ms.assetid: 53928a10-e474-46d0-ab90-5f98f8d7b668
ms.openlocfilehash: 3cae20cfe8d52497646ca173740533a22326c8f8
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599158"
---
# <a name="distributed-application-security"></a>Dağıtılan Uygulama Güvenliği
Windows Communication Foundation (WCF) güvenliği üç önemli işlevsel alana bölünmüştür: aktarım güvenliği, erişim denetimi ve denetim. Aktarım güvenliği bütünlük, gizlilik ve kimlik doğrulama sağlar. Aktarım güvenliği, aşağıdakilerden biri tarafından sağlanır: aktarım güvenliği, ileti güvenliği veya `TransportWithMessageCredential` .  
  
 WCF ileti güvenliğine genel bakış için bkz. [Güvenliğe genel bakış](security-overview.md). WCF güvenliğinin diğer iki parçası hakkında daha fazla bilgi için bkz. [Yetkilendirme](authorization-in-wcf.md) ve [Denetim](auditing-security-events.md).  
  
## <a name="transfer-security-scenarios"></a>Güvenlik senaryolarını aktarma  
 WCF Aktarım güvenliği kullanan yaygın senaryolar şunlardır:  
  
- Windows kullanarak güvenli aktarım. WCF istemcisi ve hizmeti bir Windows etki alanına (veya Windows ormanına) dağıtılır. İletiler kişisel veriler içerir, bu nedenle gereksinimler istemci ve hizmetin karşılıklı kimlik doğrulamasını, ileti bütünlüğünü ve ileti gizliliğini içerir. Ayrıca, belirli bir işlemin gerçekleşmesinin gerekli olması gerekir, örneğin, iletinin alıcısı imza bilgilerini kaydeder.  
  
- Ve HTTPS kullanarak güvenli aktarım `UserName` . Internet üzerinden çalışmak için bir WCF istemcisi ve hizmetinin geliştirilmesi gerekir. İstemci kimlik bilgileri, Kullanıcı adı/parola çiftleri veritabanına göre kimlik doğrular. Hizmet, güvenilir bir Güvenli Yuva Katmanı (SSL) sertifikası kullanarak bir HTTPS adresinde dağıtılır. İletiler Internet üzerinden seyahat ettiğinden, istemci ve hizmetin karşılıklı olarak kimlik doğrulaması yapması ve iletilerin gizli ve bütünlüğü aktarım sırasında korunması gerekir.  
  
- Sertifikaları kullanarak güvenli aktarım. Genel internet üzerinden çalışacak bir WCF istemcisi ve hizmetinin geliştirilmesi gerekir. İstemci ve hizmetin her ikisinin de iletileri güvenli hale getirmek için kullanılabilecek sertifikaları vardır. İstemci ve hizmet, Internet 'i birbirleriyle iletişim kurmak ve ileti bütünlüğü, gizlilik ve karşılıklı kimlik doğrulaması gerektiren yüksek değerli işlemleri gerçekleştirmek için kullanır.  
  
## <a name="integrity-confidentiality-and-authentication"></a>Bütünlük, gizlilik ve kimlik doğrulama  
 Bütünlük, gizlilik ve kimlik doğrulama dahil olmak üzere üç işlev birlikte aktarım güvenliği olarak adlandırılır. Aktarım güvenliği, dağıtılmış bir uygulamayla ilgili tehditleri azaltmaya yardımcı olan işlevleri sağlar. Aşağıdaki tabloda, aktarım güvenliği oluşturan üç işlev kısaca açıklanmaktadır.  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|Bütünlük|*Bütünlük* , verilerin tam ve doğru, özellikle bir noktadan diğerine geçen ve büyük olasılıkla birçok aktör tarafından okunan güvencedir. Verilerin üzerinde oynanmasını engellemek için bütünlük korunmalıdır ve genellikle bir iletinin dijital olarak imzalanmasıyla elde edilir.|  
|Gizlilik|*Gizlilik* , bir iletinin amaçlanan okuyucu dışında bir kişi tarafından okunmadığını güvence altına taşımaktadır. Örneğin, Internet üzerinden gönderildiği için kredi kartı numarasının gizli tutulması gerekir. Gizlilik, genellikle ortak anahtar/özel anahtar düzeni kullanılarak verilerin şifrelenmesi tarafından sağlanır.|  
|Kimlik Doğrulaması|*Kimlik doğrulaması* , istenen kimliğin doğrulanmasıdır. Örneğin, bir banka hesabı kullanırken, yalnızca hesabın gerçek sahibinin fonları geri çekmesini sağlamak zorunludur. Kimlik doğrulaması çeşitli yollarla sağlanarak yapılabilir. Yaygın olarak kullanılan bir yöntem, Kullanıcı/parola sistemidir. İkincisi, üçüncü taraf tarafından sunulan bir X. 509.440 sertifikası kullanmaktır.|  
  
## <a name="security-modes"></a>Güvenlik modları  
 WCF, aşağıdaki tabloda açıklanan çeşitli aktarım güvenliği modlarına sahiptir.  
  
|Mod|Açıklama|  
|----------|-----------------|  
|Yok|Aktarım katmanında veya ileti katmanında güvenlik sağlanmaz. Önceden tanımlı bağlamalardan hiçbiri, bu modu öğesi hariç, varsayılan olarak, [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) kod kullanırken <xref:System.ServiceModel.BasicHttpBinding> sınıfı kullanır.|  
|Aktarım|Bütünlük, gizlilik ve karşılıklı kimlik doğrulama için HTTPS gibi güvenli bir aktarım kullanır.|  
|İleti|Bütünlük, gizlilik ve karşılıklı kimlik doğrulama için SOAP iletisi güvenliği kullanır. SOAP iletileri WS-Security standartlarına göre güvenli hale getirilir.|  
|Karma mod|Bütünlük, gizlilik ve sunucu kimlik doğrulaması için Transport Security 'yi kullanır. İstemci kimlik doğrulaması için ileti güvenliğini (WS-Security ve diğer standartları) kullanır.<br /><br /> (Bu mod için bu sabit listesi `TransportWithMessageCredential` .)|  
|Her ikisi de|Her iki düzeyde koruma ve kimlik doğrulaması gerçekleştirir. Bu mod yalnızca [\<netMsmqBinding>](../../configure-apps/file-schema/wcf/netmsmqbinding.md) öğesinde kullanılabilir.|  
  
## <a name="credentials-and-transfer-security"></a>Kimlik bilgileri ve aktarım güvenliği  
 Bir *kimlik bilgisi* , istenen bir kimlik veya özellik kurmak için sunulan bir veri olabilir. Bir kimlik bilgisi sunmak, verilerin hem verilerin hem de sahip olma kanıtını içerir. WCF, hem aktarım hem de ileti güvenlik düzeylerinde çeşitli kimlik bilgileri türlerini destekler. WCF bağlaması için bir kimlik bilgisi türü belirtebilirsiniz.  
  
 Birçok ülkede veya bölgede, bir sürücünün lisansı bir kimlik bilgisi örneğidir. Bir lisans, bir kullanıcının kimliğini ve yeteneklerini temsil eden verileri içerir. Bu, desessor 'ın resmi biçiminde sahip olma kanıtını içerir. Lisans, genellikle bir kamu lisanslama departmanı olan güvenilen bir yetkili tarafından verilir. Lisans mühürlü ve üzerinde oynanmadığını veya onay yapılmadığını gösteren bir hologram içerebilir.  
  
 Örnek olarak, WCF: Kullanıcı adı ve (X. 509.440) sertifika kimlik bilgileri ' nde desteklenen iki kimlik bilgileri türünü göz önünde bulundurun.  
  
 Kullanıcı adı kimlik bilgisi için Kullanıcı adı, istenen kimliği temsil eder ve parola, sahip olma kanıtını gösterir. Bu durumda güvenilen yetkili, Kullanıcı adını ve parolasını doğrulayan sistemidir.  
  
 Sertifika kimlik bilgilerinde, konu adı, konu diğer adı veya sertifika içindeki belirli alanlar, istenen kimliği ve/veya özellikleri temsil etmek için kullanılabilir. Kimlik bilgilerinde bulunan verilerin kanıtı, bir imza oluşturmak için ilişkili özel anahtar kullanılarak oluşturulur.  
  
 Aktarım güvenliğini programlama ve kimlik bilgilerini belirtme hakkında daha fazla bilgi için bkz. [bağlamalar ve güvenlik](bindings-and-security.md) ve [güvenlik davranışları](security-behaviors-in-wcf.md).  
  
### <a name="transport-client-credential-types"></a>Aktarım Istemci kimlik bilgisi türleri  
 Aşağıdaki tabloda, aktarım güvenliği kullanan bir uygulama oluşturulurken kullanılan olası değerler gösterilmektedir. Bu değerleri, kod veya bağlama ayarlarından kullanabilirsiniz.  
  
|Ayar|Açıklama|  
|-------------|-----------------|  
|Yok|İstemcinin herhangi bir kimlik bilgisi sunması gerekmediğini belirtir. Bu, anonim bir istemciyi dönüştürür.|  
|Temel|Temel kimlik doğrulamasını belirtir. Daha fazla bilgi için bkz. RFC2617, "[http Authentication: Basic ve Digest Authentication](http://schemas.xmlsoap.org/ws/2004/10/discovery/ws-discovery.pdf)."|  
|Bilgisi|Özet kimlik doğrulamasını belirtir. Daha fazla bilgi için bkz. RFC2617, "[http Authentication: Basic ve Digest Authentication](http://schemas.xmlsoap.org/ws/2004/10/discovery/ws-discovery.pdf)."|  
|NT|Windows etki alanında SSPI anlaşması kullanan Windows kimlik doğrulamasını belirtir.<br /><br /> SSPI anlaşması, Kerberos protokolünü veya NT LanMan (NTLM) kullanarak sonuçlanır.|  
|Windows|Windows etki alanında SSPI kullanarak Windows kimlik doğrulamasını belirtir. SSPI, Kerberos protokolünü veya kimlik doğrulama hizmeti olarak NTLM 'yi seçer.<br /><br /> SSPI önce Kerberos protokolünü dener; başarısız olursa, NTLM kullanır.|  
|Sertifika|Genellikle X. 509.440 olan bir sertifika kullanarak istemci kimlik doğrulaması gerçekleştirir.|  
  
### <a name="message-client-credential-types"></a>İleti Istemci kimlik bilgisi türleri  
 Aşağıdaki tabloda ileti güvenliği kullanan bir uygulama oluşturulurken kullanılan olası değerler gösterilmektedir. Bu değerleri, kod veya bağlama ayarlarından kullanabilirsiniz.  
  
|Ayar|Açıklama|  
|-------------|-----------------|  
|Yok|Hizmetin anonim istemcilerle etkileşime geçmesini sağlar.|  
|Windows|SOAP ileti değişimlerinin, bir Windows kimlik bilgisinin kimliği doğrulanmış bağlamı altında oluşmasına izin verir. , Kerberos protokolünü veya bir kimlik doğrulama hizmeti olarak NTLM 'yi seçmek için SSPI anlaşma mekanizmasını kullanır.|  
|Kullanıcı adı|Hizmetin, istemcinin kimliğinin Kullanıcı adı kimlik bilgileriyle doğrulanmasını gerektirmesini sağlar. WCF 'nin Kullanıcı adı ile imza oluşturma veya veri şifreleme gibi herhangi bir şifreleme işlemine izin vermediği unutulmamalıdır. Bu nedenle, WCF Kullanıcı adı kimlik bilgileri kullanılırken taşımanın güvenli hale getirilme işlemi uygular.|  
|Sertifika|Hizmetin, bir sertifika kullanarak istemcinin kimliğinin doğrulanmasını gerektirmesini sağlar.|  
|CardSpace|Hizmetin, istemcinin bir CardSpace kullanarak kimliğinin doğrulanmasını gerektirmesini sağlar.|  
  
### <a name="programming-credentials"></a>Programlama kimlik bilgileri  
 Her istemci kimlik bilgisi türü için, WCF programlama modeli, hizmet davranışları ve kanal davranışları kullanarak kimlik bilgisi değerlerini ve kimlik bilgisi Doğrulayıcıları belirtmenize olanak tanır.  
  
 WCF güvenliği iki tür kimlik bilgisine sahiptir: hizmet kimlik bilgileri davranışları ve kanal kimlik bilgisi davranışları. WCF 'de kimlik bilgisi davranışları, bağlar aracılığıyla ifade edilen güvenlik gereksinimlerini karşılamak için kullanılan kimlik bilgilerini, yani, gerçek verileri belirler. WCF 'de istemci sınıfı, işlem çağrısı ve iletileri arasında dönüştürme yapan çalışma zamanı bileşenidir. Tüm istemciler <xref:System.ServiceModel.ClientBase%601> sınıfından devralınır. <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>Temel sınıftaki özelliği, istemci kimlik bilgilerinin çeşitli değerlerini belirtmenize olanak tanır.  
  
 WCF 'de hizmet davranışları, hizmeti programlı bir şekilde denetlemek için bir hizmet sözleşmesi (arabirim) uygulayan sınıfa uygulanan özniteliklerdir. <xref:System.ServiceModel.Description.ServiceCredentials>Sınıfı, çeşitli istemci kimlik bilgileri türleri için hizmet kimlik bilgileri ve istemci doğrulama ayarları için sertifikalar belirtmenize olanak tanır.  
  
### <a name="negotiation-model-for-message-security"></a>Ileti güvenliği için anlaşma modeli  
 İleti güvenliği modu, hizmet kimlik bilgilerinin bant dışı istemcide yapılandırılması için aktarım güvenliği gerçekleştirmenize olanak tanır. Örneğin, Windows sertifika deposunda depolanan bir sertifika kullanıyorsanız, Microsoft Yönetim Konsolu (MMC) ek bileşeni gibi bir araç kullanmanız gerekir.  
  
 İleti güvenliği modu, hizmet kimlik bilgisinin istemci ile ilk anlaşmanın bir parçası olarak alınıp aktarılması için aktarım güvenliği gerçekleştirmenize olanak tanır. Anlaşmayı etkinleştirmek için <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> özelliğini olarak ayarlayın `true` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uç Noktası Oluşturma Genel Bakış](../endpoint-creation-overview.md)
- [Sistem tarafından sağlanmış bağlamalar](../system-provided-bindings.md)
- [Güvenliğe genel bakış](security-overview.md)
- [Windows Server App Fabric için güvenlik modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
