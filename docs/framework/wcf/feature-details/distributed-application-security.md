---
title: Dağıtılan Uygulama Güvenliği
ms.date: 03/30/2017
helpviewer_keywords:
- distributed application security [WCF]
- security [WCF], transfer
ms.assetid: 53928a10-e474-46d0-ab90-5f98f8d7b668
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: d8f34d0c6b0269cc4837313d6613e3cee0eb26c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="distributed-application-security"></a>Dağıtılan Uygulama Güvenliği
Windows Communication Foundation (WCF) güvenlik üç ana işlevsel alanlara bölünmüş: güvenlik, erişim denetimi ve denetim aktarın. Aktarım güvenlik bütünlüğü, gizlilik ve kimlik doğrulaması sağlar. Aktarım güvenlik şunlardan biri tarafından sağlanır: aktarım güvenliği, ileti güvenliği veya `TransportWithMessageCredential`.  
  
 WCF ileti güvenliği genel bakış için bkz: [güvenliğine genel bakış](../../../../docs/framework/wcf/feature-details/security-overview.md). Diğer iki parça WCF güvenlik hakkında daha fazla bilgi için bkz: [yetkilendirme](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md) ve [denetim](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
## <a name="transfer-security-scenarios"></a>Aktarım güvenlik senaryoları  
 WCF aktarımı güvenlik uygulamadığınız yaygın senaryolar aşağıdakileri içerir:  
  
-   Güvenli aktarım Windows kullanma. Bir WCF istemcisi ve hizmeti bir Windows etki alanı (veya bir Windows ormanı) dağıtılır. İstemci ve hizmet, ileti bütünlüğü ve ileti gizliliği karşılıklı kimlik doğrulama gereksinimleri içerir şekilde iletileri kişisel veriler içerir. Ayrıca, gerekli korumalıdır belirli bir işlem, örneğin, ileti alıcısı imza bilgilerini kaydetmek ortaya çıktığını.  
  
-   Güvenli aktarımı kullanarak `UserName` ve HTTPS. Bir WCF istemcisi ve hizmet Internet üzerinden çalışmak için geliştirilmiş gerekir. İstemci kimlik bilgileri kullanıcı adı/parola çiftleri veritabanına karşı kimlik doğrulaması. Hizmet, güvenilen bir Güvenli Yuva Katmanı (SSL) sertifikası kullanarak HTTPS adresi sırasında dağıtılır. Internet üzerinden iletileri seyahat olduğundan istemci ve hizmet karşılıklı kimlik doğrulaması gerekir ve aktarım sırasında ileti gizliliği ve bütünlük korunması gerekir.  
  
-   Sertifikaları kullanılarak güvenli aktarma. Bir WCF istemcisi ve hizmet ortak internet üzerinden çalışmak için geliştirilmiş gerekir. Hem istemci hem hizmet iletileri güvenli hale getirmek için kullanılan sertifikaları sahiptir. Hizmet ve istemci Internet birbirleri ile iletişim kurmak ve ileti bütünlüğü ve gizliliği karşılıklı kimlik doğrulaması gerektiren yüksek değerli işlemleri gerçekleştirmek için kullanın.  
  
## <a name="integrity-confidentiality-and-authentication"></a>Bütünlük, gizlilik ve kimlik doğrulama  
 Üç işlevleri — bütünlüğü, gizlilik ve kimlik doğrulaması — aktarımı güvenlik birlikte çağrılır. Aktarım güvenlik dağıtılmış uygulama tehditlerin azaltılmasına yardımcı işlevleri sağlar. Aşağıdaki tabloda, aktarım güvenliği olun üç işlevleri kısaca açıklanmaktadır.  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|Bütünlük|*Bütünlük* özellikle başka bir noktadan geçiş ve büyük olasılıkla birçok aktörler tarafından okunan sonra verileri eksiksiz ve doğru olduğundan emin olan. Bütünlük verilerin üzerinde oynamasını önlemek için korunmalıdır ve genellikle bir iletinin dijital imzalanması tarafından sağlanır.|  
|Gizliliği|*Gizlilik* bir ileti hedeflenen okuyucu dışındaki bir kişiye göre okunmadı güvence olduğu. Örneğin, kredi kartı numarası, Internet üzerinden gönderilen gizli tutulmalıdır. Gizliliği genellikle ortak bir anahtar/özel anahtar şeması kullanarak veri şifrelemesi tarafından sağlanır.|  
|Kimlik doğrulaması|*Kimlik doğrulama* talep edilen kimlik doğrulama. Örneğin, bir banka hesabı kullanırken, bu hesap yalnızca gerçek sahibi fon programdan çıkın izin verileceğini zorunludur. Kimlik doğrulama anlamına gelir, çeşitli tarafından sağlanabilir. Bir ortak yöntemi kullanıcı/parola sistemidir. İkinci, üçüncü taraf tarafından sağlanan bir X.509 sertifikası kullanılır.|  
  
## <a name="security-modes"></a>Güvenlik modu  
 WCF aşağıdaki tabloda açıklanan birkaç aktarımı güvenlik modu vardır.  
  
|Mod|Açıklama|  
|----------|-----------------|  
|Yok.|Hiçbir güvenlik aktarım katmanında veya ileti katmanında sağlanır. Önceden tanımlanmış bağlamaları hiçbiri dışında varsayılan olarak bu modu kullanın [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) öğesi veya kod, kullanırken <xref:System.ServiceModel.BasicHttpBinding> sınıfı.|  
|Taşıma|HTTPS gibi güvenli bir taşıma bütünlüğü, gizlilik ve karşılıklı kimlik doğrulaması için kullanır.|  
|İleti|SOAP iletisi güvenlik bütünlüğü, gizlilik ve karşılıklı kimlik doğrulaması için kullanır. SOAP iletilerine göre WS-güvenlik standartları güvenli hale getirilir.|  
|Karma mod|Aktarım güvenliği bütünlüğü, gizlilik ve sunucu kimlik doğrulaması için kullanır. İleti güvenliği (WS-güvenlik ve diğer standartları) istemci kimlik doğrulaması için kullanır.<br /><br /> (Bu mod için bu numaralandırma `TransportWithMessageCredential`.)|  
|Her ikisi|Koruma ve kimlik doğrulama, iki düzeyde gerçekleştirir. Bu modu yalnızca kullanılabilir [ \<netMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md) öğesi.|  
  
## <a name="credentials-and-transfer-security"></a>Kimlik bilgileri ve Aktarım güvenlik  
 A *kimlik bilgisi* bir talep kimliği veya özellikleri oluşturmak için sunulan veriler. Bir kimlik bilgisi sunan hem veri hem de veri kanıtını sunan içerir. WCF çeşitli güvenlik düzeyleri taşıma ve ileti kimlik bilgisi türlerini destekler. Bir WCF bağlama için kimlik bilgisi türünü belirtebilirsiniz.  
  
 Birçok ülke veya bölgelerde, bir sürücünün lisans bir kimlik bilgisi örneğidir. Bir lisans birinin kimlik ve özellikleri temsil eden veri içeriyor. Sahibi'nın resmi biçiminde kanıtını içerir. Lisans, genellikle kamu bir lisans bölüm gibi güvenilir bir yetkili tarafından verilir. Lisans korumalı ve değil değiştirilmiş veya bırakıldığı sahtesi olduğunu gösteren bir hologramı içerebilir.  
  
 Örnek olarak, iki tür WCF'de desteklenen kimlik bilgileri göz önünde bulundurun: sertifika kimlik bilgileri kullanıcı adı ve (X.509).  
  
 Kullanıcı adı kimlik bilgisi için kullanıcı adı talep kimliğini temsil eder ve parola kanıtını sunar. Güvenilir yetkili bu durumda kullanıcı adını ve parolayı doğrular sistemidir.  
  
 Sertifika kimlik bilgisi, konu adı, konu diğer adı ya da sertifika içinde belirli alanları talep edilen kimlik ve/veya özellikleri göstermek için kullanılabilir. Kimlik bilgisi verilerin kanıtını bir imzayı üretmek için ilişkili özel anahtarı kullanılarak oluşturulur.  
  
 Programlama hakkında daha fazla bilgi aktarmak güvenlik ve kimlik bilgileri görmek için [bağlamalar ve güvenlik](../../../../docs/framework/wcf/feature-details/bindings-and-security.md) ve [güvenlik davranışları](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md).  
  
### <a name="transport-client-credential-types"></a>Taşıma istemcisi kimlik bilgisi türleri  
 Aktarım güvenlik kullanan bir uygulama oluşturma sırasında kullanılan olası değerler aşağıdaki tabloda gösterilmektedir. Kod veya bağlama ayarları bu değerleri kullanabilirsiniz.  
  
|Ayar|Açıklama|  
|-------------|-----------------|  
|Yok.|İstemci kimlik sunmak gerekmez belirtir. Anonim istemci için çevirir.|  
|Temel|Temel kimlik doğrulaması belirtir.  RFC2617, ek bilgi için bkz: "[HTTP kimlik doğrulaması: temel ve Özet kimlik doğrulaması](http://go.microsoft.com/fwlink/?LinkId=88313)."|  
|Özet|Özet kimlik doğrulaması belirtir.  RFC2617, ek bilgi için bkz: "[HTTP kimlik doğrulaması: temel ve Özet kimlik doğrulaması](http://go.microsoft.com/fwlink/?LinkId=88313)."|  
|NTLM|Bir Windows etki alanında SSPI anlaşması kullanarak Windows kimlik doğrulaması belirtir.<br /><br /> Kerberos protokolü veya NT LanMan (NTLM) kullanarak SSPI anlaşması sonuçlanır.|  
|Windows|Bir Windows etki alanında SSPI kullanarak Windows kimlik doğrulaması belirtir. SSPI Kerberos protokolü veya NTLM kimlik doğrulama hizmeti olarak seçer.<br /><br /> SSPI, Kerberos protokolü ilk çalışır; başarısız olursa, ardından NTLM kullanır.|  
|Sertifika|Sertifika, genellikle X.509 kullanarak istemci kimlik doğrulaması gerçekleştirir.|  
  
### <a name="message-client-credential-types"></a>İleti istemcisi kimlik bilgisi türleri  
 İleti güvenliği kullanan bir uygulama oluşturma sırasında kullanılan olası değerler aşağıdaki tabloda gösterilmektedir. Kod veya bağlama ayarları bu değerleri kullanabilirsiniz.  
  
|Ayar|Açıklama|  
|-------------|-----------------|  
|Yok.|Hizmetin anonim istemcilerle etkileşime girmesine izin verir.|  
|Windows|Windows kimlik bilgisi kimliği doğrulanmış bağlamı altında gerçekleşmesi SOAP ileti alışverişlerinde sağlar. Kerberos protokolü veya NTLM kimlik doğrulama hizmeti olarak seçmek için SSPI anlaşması mekanizması kullanır.|  
|Kullanıcı adı|Hizmetinin istemci sahip bir kullanıcı adı kimlik bilgisi doğrulanmasını gerektiren izin verir. WCF şifreleme işlemleri imza oluşturulurken veya veri şifreleme gibi kullanıcı adı, izin verme unutmayın. Bu nedenle, WCF taşıma kullanıcı adı kimlik bilgileri kullanırken güvenli zorlar.|  
|Sertifika|Hizmetinin gerektiren izin verir, istemci kimlik doğrulaması kullanarak bir sertifika.|  
|[!INCLUDE[infocard](../../../../includes/infocard-md.md)]|Hizmetinin gerektiren izin verir, istemci kimlik doğrulaması kullanarak bir [!INCLUDE[infocard](../../../../includes/infocard-md.md)].|  
  
### <a name="programming-credentials"></a>Kimlik bilgileri programlama  
 Her istemci kimlik bilgisi türü WCF programlama modeli, kimlik bilgileri değerlerini belirtme ve hizmet davranışları ve kanal davranışları kullanarak doğrulayıcılar kimlik bilgisi olanak sağlar.  
  
 WCF güvenlik kimlik bilgileri iki tür vardır: Hizmet kimlik bilgisi davranışları ve kanal kimlik bilgisi davranışları. Wcf'de kimlik bilgisi davranışları gerçek verileri, yani, bağlamaları ifade güvenlik gereksinimlerini karşılamak için kullanılan kimlik bilgilerini belirtin. WCF'de, işlem çağırma ve iletileri arasında dönüştürür çalışma zamanı bileşeni bir istemci sınıftır. Tüm istemcilerin devralınmalıdır <xref:System.ServiceModel.ClientBase%601> sınıfı. <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> Temel sınıf özelliği çeşitli değerleri istemci kimlik bilgileri belirtmenize olanak verir.  
  
 WCF'de, hizmet davranışları hizmeti programlı olarak denetlemek için bir hizmet sözleşmesini (arabirimi) uygulama sınıfına uygulanan öznitelikleri görüntülenir. <xref:System.ServiceModel.Description.ServiceCredentials> Sınıfı Sertifikalar çeşitli istemci kimlik bilgisi türlerinin hizmeti kimlik bilgileri ve istemci doğrulama ayarları belirtmenize olanak verir.  
  
### <a name="negotiation-model-for-message-security"></a>İleti güvenliği için anlaşma modeli  
 İleti güvenlik modu istemcide bant dışı hizmet kimlik bilgilerini yapılandırılmasını sağlamak amacıyla aktarımı güvenlik işlemleri yapmanıza olanak tanır. Örneğin, Windows sertifika deposunda depolanan bir sertifika kullanıyorsanız, bir Microsoft Yönetim Konsolu (MMC) ek bileşeni gibi bir araç kullanmanız gerekir.  
  
 İleti güvenlik modu aktarımı güvenlik gerçekleştirin, böylelikle hizmet kimlik bilgilerini bir ilk anlaşmasının bir parçası istemcinin değiştirilir sağlar. Anlaşma etkinleştirmek için ayarlanmış <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> özelliğine `true`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uç Nokta Oluşturmaya Genel Bakış](../../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [Sistem Tarafından Sağlanan Bağlamalar](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [Güvenliğe Genel Bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Windows Server App Fabric için güvenlik modeli](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
