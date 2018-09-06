---
title: Dağıtılan Uygulama Güvenliği
ms.date: 03/30/2017
helpviewer_keywords:
- distributed application security [WCF]
- security [WCF], transfer
ms.assetid: 53928a10-e474-46d0-ab90-5f98f8d7b668
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 0dbc06afd4695b85f426fad2859b4c6d4b6684d6
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43857186"
---
# <a name="distributed-application-security"></a>Dağıtılan Uygulama Güvenliği
Windows Communication Foundation (WCF) güvenlik üç önemli işlevsel alanları bozuk: güvenlik, erişim denetimi ve denetim aktarın. Aktarım güvenliği, kimlik doğrulaması bütünlüğü ve gizliliği sağlar. Aktarım güvenliği aşağıdakilerden biri tarafından sağlanır: aktarım güvenliği, ileti güvenliği veya `TransportWithMessageCredential`.  
  
 WCF ileti güvenliğini genel bakış için bkz. [güvenliğine genel bakış](../../../../docs/framework/wcf/feature-details/security-overview.md). Diğer iki parça WCF güvenlik hakkında daha fazla bilgi için bkz: [yetkilendirme](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md) ve [denetim](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
## <a name="transfer-security-scenarios"></a>Aktarım güvenliği senaryoları  
 WCF aktarma güvenlik görevlendirmek yaygın senaryolar şunlardır:  
  
-   Windows kullanarak güvenli aktarım. Bir WCF istemcisi ve hizmet, bir Windows etki alanı (veya Windows orman) dağıtılır. İstemci ve hizmet, ileti bütünlüğü ve ileti gizliliği karşılıklı kimlik doğrulaması gereksinimleri içerir böylece iletileri kişisel verileri içerir. Ayrıca, kavram gereklidir belirli bir işlem, örneğin, ileti alıcısı imza bilgilerini kaydetmek oluştuğunu.  
  
-   Güvenli aktarım kullanarak `UserName` ve HTTPS. Bir WCF istemcisi ve hizmet Internet üzerinden çalışacak şekilde geliştirilen gerekir. İstemci kimlik bilgileri, bir kullanıcı adı/parola çiftleri veritabanına karşı kimlik doğrulaması. Hizmet, güvenilir bir Güvenli Yuva Katmanı (SSL) sertifikasını kullanarak bir HTTPS adresi dağıtılır. İletileri Internet üzerinden yolculuk ediyor çünkü istemci ve hizmet birbirini doğrulanması gerekir ve iletileri gizliliği ve bütünlüğü aktarım sırasında korunur.  
  
-   Sertifikaları kullanarak güvenli aktarım. Bir WCF istemcisi ve hizmet genel internet üzerinden çalışmak için geliştirilmiş gerekir. İstemci ve hizmet iletileri güvenli hale getirmek için kullanılan sertifikaları her ikisi de sahiptir. Hizmet ve istemci Internet birbirleri ile iletişim kurmak ve ileti bütünlüğü ve gizliliği karşılıklı kimlik doğrulaması gerektiren yüksek değerli işlemleri gerçekleştirmek için kullanın.  
  
## <a name="integrity-confidentiality-and-authentication"></a>Kimlik doğrulaması bütünlüğü ve gizlilik  
 Üç işlev — bütünlüğü, gizlilik ve kimlik doğrulaması — birlikte Aktarım güvenlik olarak da adlandırılır. Aktarım güvenliği bir dağıtılmış uygulama tehditlerin azaltılmasına yardımcı olacak işlevleri sağlar. Aşağıdaki tabloda kısaca aktarım güvenliği olun üç işlevleri açıklanmaktadır.  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|Bütünlüğü|*Bütünlük* özellikle bir noktasından diğerine geçiş ve büyük olasılıkla pek çok aktörler tarafından Okunmuş sonra veri tam ve doğru olduğundan emin olan. Bütünlük verilerle kurcalanmaya karşı korunmalıdır ve genellikle bir iletinin dijital imzalama tarafından sağlanır.|  
|Gizliliği|*Gizlilik* tarafından istenen okuyucu dışındaki bir ileti okunmadı güvencesi olduğu. Örneğin, bir kredi kartı numarası, Internet üzerinden gönderilen gizli tutulmalıdır. Gizlilik genellikle ortak bir anahtar/özel anahtar şeması kullanarak veri şifrelemesi tarafından sağlanır.|  
|Kimlik doğrulaması|*Kimlik doğrulaması* talep edilen kimlik doğrulama. Örneğin, bir banka hesabı kullanırken, yalnızca gerçek hesap sahibini fon geri izin verileceğini olmazsa olmaz. Kimlik doğrulaması anlamına gelir çeşitli tarafından sağlanabilir. Bir genel yöntem kullanıcı/parola sistemidir. İkinci bir üçüncü taraf tarafından sağlanan bir X.509 sertifikası kullanılır.|  
  
## <a name="security-modes"></a>Güvenlik modu  
 Aşağıdaki tabloda açıklanan birkaç Aktarım güvenlik modu WCF sahiptir.  
  
|Mod|Açıklama|  
|----------|-----------------|  
|Yok.|Güvenlik aktarım katmanında veya ileti katmanında sağlanır. Önceden tanımlanmış bağlamaları hiçbiri dışında varsayılan olarak bu modu kullanın [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) öğesi veya kodun kullanırken <xref:System.ServiceModel.BasicHttpBinding> sınıfı.|  
|Taşıma|HTTPS gibi güvenli aktarım bütünlüğü, gizliliği ve karşılıklı kimlik doğrulaması için kullanır.|  
|İleti|SOAP ileti güvenliği bütünlüğü, gizliliği ve karşılıklı kimlik doğrulaması için kullanır. SOAP iletilerini göre WS-güvenlik standartları güvenlidir.|  
|Karma mod|Kullanan bütünlüğü, gizliliği ve sunucu kimlik doğrulaması için güvenlik taşıma. Güvenlik (WS-güvenlik ve diğer standartların) istemci kimlik doğrulaması için kullandığı ileti.<br /><br /> (Bu modu için bu numaralandırma `TransportWithMessageCredential`.)|  
|Her ikisi de|Koruma ve kimlik doğrulama, iki düzeyde gerçekleştirir. Bu mod yalnızca kullanılabilir [ \<netMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md) öğesi.|  
  
## <a name="credentials-and-transfer-security"></a>Kimlik bilgileri ve aktarım güvenliği  
 A *kimlik bilgisi* bir talep kimliği veya özellikleri kurmak için sunulan veriler. Bir kimlik bilgisi sunma hem verileri hem de veri kanıtını sunma içerir. WCF çeşitli hem aktarım hem de ileti güvenlik düzeylerinde kimlik bilgisi türlerini destekler. Bir WCF bağlama için kimlik bilgisi türünü belirtebilirsiniz.  
  
 Birçok ülkede veya bölgede, bir sürücünün lisans, bir kimlik bilgisi örneğidir. Bir lisans birinin kimlik ve özellikleri temsil eden veriler içerir. Bu kaynağı'nın resmi biçiminde kanıtını içerir. Lisans, genellikle bir kamu lisanslama departmanı gibi güvenilir bir yetkili tarafından verilmiş. Lisans, korumalı ve onu olmayan kurcalanmadığından veya sahtesi olduğunu gösteren, bir hologramı içerebilir.  
  
 Örneğin, iki tür kimlik bilgileri WCF'de desteklenen göz önünde bulundurun: sertifika kimlik bilgileri kullanıcı adı ve (X.509).  
  
 Kullanıcı adı kimlik bilgisi için kullanıcı adını temsil eden talep kimliğini ve parolayı kanıtını sunar. Güvenilir yetkili bu durumda kullanıcı adını ve parolayı doğrular sistemidir.  
  
 Sertifika kimlik bilgisi, konu adı, konu alternatif adı veya belirli alanların sertifika talep edilen kimlik ve/veya özellikleri temsil etmek için kullanılabilir. Kimlik bilgisi verilerinin kanıtını bir imzayı üretmek için ilişkili özel anahtarı kullanılarak oluşturulur.  
  
 Aktarım güvenliği ve kimlik bilgilerini belirtme programlama hakkında daha fazla bilgi için [bağlamalar ve güvenlik](../../../../docs/framework/wcf/feature-details/bindings-and-security.md) ve [güvenlik davranışları](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md).  
  
### <a name="transport-client-credential-types"></a>Taşıma istemcisi kimlik bilgisi türü  
 Bir uygulama oluşturma aktarım güvenliği kullandığında kullanılan olası değerler aşağıdaki tabloda gösterilmektedir. Bu değerleri kod veya bağlama ayarları kullanabilirsiniz.  
  
|Ayar|Açıklama|  
|-------------|-----------------|  
|Yok.|İstemci mevcut herhangi bir kimlik bilgisi gerekmez belirtir. Bu, anonim bir istemciye dönüşür.|  
|Temel|Temel kimlik doğrulaması belirtir.  RFC2617, ek bilgi için bkz. "[HTTP kimlik doğrulaması: temel ve Özet kimlik doğrulaması](https://go.microsoft.com/fwlink/?LinkId=88313)."|  
|Özet|Özet kimlik doğrulaması belirtir.  RFC2617, ek bilgi için bkz. "[HTTP kimlik doğrulaması: temel ve Özet kimlik doğrulaması](https://go.microsoft.com/fwlink/?LinkId=88313)."|  
|NTLM|Bir Windows etki alanında SSPI anlaşması kullanılarak Windows kimlik doğrulaması belirtir.<br /><br /> SSPI anlaşması Kerberos protokolü veya NT LanMan (NTLM) kullanarak sonuçlanır.|  
|Windows|SSPI kullanarak bir Windows etki alanında Windows kimlik doğrulaması belirtir. SSPI, hizmet olarak kimlik doğrulaması Kerberos protokolü veya NTLM sitesinden seçer.<br /><br /> SSPI Kerberos protokolü ilk olarak çalışır; Bu başarısız olursa, NTLM kullanır.|  
|Sertifika|Genellikle X.509 sertifikası kullanarak istemci kimlik doğrulaması gerçekleştirir.|  
  
### <a name="message-client-credential-types"></a>İleti istemci kimlik bilgisi türleri  
 İleti güvenliği bir uygulama oluşturma kullandığında, kullanılan olası değerler aşağıdaki tabloda gösterilmektedir. Bu değerleri kod veya bağlama ayarları kullanabilirsiniz.  
  
|Ayar|Açıklama|  
|-------------|-----------------|  
|Yok.|Anonim istemci ile etkileşim kurmak hizmet sağlar.|  
|Windows|SOAP ileti alışverişlerinde Windows kimlik bilgisi kimliği doğrulanmış bağlamı altında gerçekleşmesini sağlar. Kerberos protokolü veya NTLM kimlik doğrulama hizmeti olarak çekmek için SSPI anlaşması mekanizması kullanır.|  
|Kullanıcı adı|Bir kullanıcı adı kimlik bilgisi ile istemcinin kimliğinin doğrulanmasını gerektiren hizmet sağlar. WCF kullanıcı adıyla bir imza oluşturma veya verileri şifreleme gibi şifreleme işlemleri izin vermediğini unutmayın. Bu nedenle, WCF aktarma kullanıcı adı kimlik bilgilerini kullanarak güvenli zorlar.|  
|Sertifika|Gerekli izin verir, istemci kimlik doğrulaması kullanarak bir sertifika.|  
|[!INCLUDE[infocard](../../../../includes/infocard-md.md)]|Gerekli izin verir, istemci kimlik doğrulaması kullanarak bir [!INCLUDE[infocard](../../../../includes/infocard-md.md)].|  
  
### <a name="programming-credentials"></a>Kimlik bilgilerini programlama  
 Her bir istemci kimlik bilgisi türü için WCF programlama modeli, kimlik bilgileri değerlerini belirtme ve hizmet davranışlarını ve kanal davranışlarını kullanarak doğrulayıcılar kimlik bilgisi sağlar.  
  
 WCF güvenlik kimlik bilgilerini iki tür vardır: Hizmet kimlik bilgisi davranışları ve kanal kimlik bilgisi davranışlarını. Wcf'de kimlik bilgisi davranışları gerçek verileri, yani bağlamaları ifade güvenlik gereksinimlerini karşılamak için kullanılan kimlik bilgilerini belirtin. WCF'de, işlem çağırma ve iletileri arasında dönüştürür çalışma zamanı bileşeni bir istemci sınıftır. Tüm istemcilerin devralınacak <xref:System.ServiceModel.ClientBase%601> sınıfı. <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> Temel sınıf özelliği, istemci kimlik bilgileri çeşitli değerleri belirtmenize olanak sağlar.  
  
 WCF'de, hizmet davranışları hizmeti programlı olarak denetlemek için bir hizmet sözleşmesini (arabirimi) uygulama sınıfına uygulanan öznitelikleri görüntülenir. <xref:System.ServiceModel.Description.ServiceCredentials> Sınıfı, çeşitli istemci kimlik bilgisi türlerinin hizmet kimlik bilgilerini ve istemci doğrulama ayarları için sertifikaları belirtmenize olanak sağlar.  
  
### <a name="negotiation-model-for-message-security"></a>İleti güvenliği için anlaşma modeli  
 İleti güvenlik modunu İstemci bant dışı hizmet kimlik bilgisi yapılandırılması aktarım güvenliği yapmanıza olanak tanır. Örneğin, Windows sertifika depolama alanında depolanan bir sertifika kullanıyorsanız, bir Microsoft Yönetim Konsolu (MMC) ek bileşenini gibi bir araç kullanmanız gerekir.  
  
 İleti güvenlik modunu hizmeti kimlik bilgileri istemcinin bir başlangıç anlaşmasının bir parçası değiştirilir aktarım güvenliği gerçekleştirmenizi sağlar. Anlaşma etkinleştirmek için <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> özelliğini `true`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uç Nokta Oluşturmaya Genel Bakış](../../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [Sistem Tarafından Sağlanan Bağlamalar](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [Güvenliğe Genel Bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Windows Server AppFabric için güvenlik modeli](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
