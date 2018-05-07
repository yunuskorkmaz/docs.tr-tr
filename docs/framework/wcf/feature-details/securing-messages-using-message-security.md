---
title: İleti Güveliği Kullanarak İletileri Güvenli Hale Getirme
ms.date: 03/30/2017
ms.assetid: a17ebe67-836b-4c52-9a81-2c3d58e225ee
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 1ebe2526e564ef24d20f1602fd5824b44e2e2bbd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="securing-messages-using-message-security"></a>İleti Güveliği Kullanarak İletileri Güvenli Hale Getirme
Bu bölümde WCF ileti güvenliğini kullanırken ele alınmaktadır <xref:System.ServiceModel.NetMsmqBinding>.  
  
> [!NOTE]
>  Bu konuyu okumadan önce okumanız önerilir [güvenlik kavramları](../../../../docs/framework/wcf/feature-details/security-concepts.md).  
  
 Aşağıdaki çizimde, kavramsal model WCF kullanarak kuyruğa alınan iletişim sağlar. Bu çizim ve terminolojiyi açıklamak için kullanılır  
  
 güvenlik kavramları taşıma.  
  
 ![Sıraya alınan uygulama diyagramı](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "dağıtılmış-sıra-Şekil")  
  
 Kuyruğa Alınan WCF kullanarak ileti gönderme, WCF ileti Message Queuing (MSMQ) ileti gövdesi olarak eklenir. Taşıma güvenliği tüm MSMQ iletiyi, ileti (veya SOAP) güvenliğini sağlar ancak güvenlik yalnızca MSMQ İleti gövdesini güvenliğini sağlar.  
  
 Anahtar ileti güvenlik istemci ileti alma işlemini yapan uygulamanın (hizmeti) için burada istemci ileti hedef sıra için güvenli hale getirdiği taşıma güvenliği aksine güvenliğini sağlama kavramdır. Bu nedenle, MSMQ hiçbir bölümü ileti güvenliği kullanarak WCF ileti güvenliğini sağlama çalar.  
  
 WCF ileti güvenliğini bir sertifika veya Kerberos protokolü gibi mevcut güvenlik altyapısı ile tümleşen WCF ileti güvenlik üstbilgileri ekler.  
  
## <a name="message-credential-type"></a>İleti kimlik bilgisi türü  
 İleti güvenliği kullanarak, hizmet ve istemci, her başka kimlik doğrulaması için kimlik sunabilir. İleti güvenliği ayarlayarak seçebileceğiniz <xref:System.ServiceModel.NetMsmqBinding.Security%2A> moduna `Message` veya `Both` (diğer bir deyişle, taşıma Güveniği ve ileti güvenliği kullanın).  
  
 Hizmetin kullanabileceği <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> özelliği istemcinin kimlik doğrulama için kullanılan kimlik bilgilerini inceleyin. Bu da daha fazla yetkilendirme denetimleri için uygulamak için hizmet seçtiği kullanılabilir.  
  
 Bu bölüm, farklı bir kimlik bilgisi türlerini ve bunların kuyruklarla nasıl kullanılacağını açıklar.  
  
### <a name="certificate"></a>Sertifika  
 Sertifika kimlik bilgisi türü, hizmet ve istemci tanımlamak için bir X.509 sertifikası kullanır.  
  
 Tipik bir senaryoda istemci ve hizmet geçerli bir sertifika bir güvenilen sertifika yetkilisi tarafından verilir. Ardından istemci hizmeti güvenip güvenmediğini karar vermek için hizmetin sertifikayı kullanarak hizmet geçerliliğini doğrular bir bağlantı kurulur. Benzer şekilde, hizmet istemci güveni doğrulamak için istemci sertifikasını kullanır.  
  
 Kuyruklar bağlantısı kesilmiş yapısını verildiğinde, istemci ve hizmet aynı anda çevrimiçi olmayabilir. Bu nedenle, hizmet ve istemci sertifikaları, bant exchange gerekir. Özellikle, bir sertifika yetkilisine zincirlenmiş) hizmet sertifikası (kendi güvenilen deposunda tutan, istemci, doğru hizmetiyle iletişim kurduğunu güvenmesi gerekir. İstemci kimlik doğrulaması için hizmet kullandığı iletiye iliştirilmiş X.509 sertifikası, istemci orijinalliğini doğrulamak için kendi deposundaki sertifikayı ile eşleşir. Yeniden, sertifika bir sertifika yetkilisine zincirleme gerekir.  
  
 Windows çalıştıran bir bilgisayarda, sertifika depoları çeşitli türlerde tutulur. Farklı depoları hakkında daha fazla bilgi için bkz: [sertifika depoları](http://go.microsoft.com/fwlink/?LinkId=87787).  
  
### <a name="windows"></a>Windows  
 Windows ileti kimlik bilgisi türü Kerberos protokolünü kullanır.  
  
 Kerberos protokolü bir etki alanındaki kullanıcıların kimliğini doğrular ve bir etki alanındaki diğer varlıklarla güvenli bağlamları kurmak kimliği doğrulanmış kullanıcılar izin veren bir güvenlik mekanizmadır.  
  
 Kuyruğa alınan iletişim için Kerberos protokolünü kullanarak sorun Anahtar Dağıtım Merkezi (KDC) dağıtır istemci kimliğini içeren biletleri görece kısa süreli olmasıdır. A *ömrü* bilet geçerliliğini gösterir Kerberos anahtarı ile ilişkilendirilmiş. Bu nedenle, yüksek gecikme verildiğinde, belirteç istemcinin kimliğini doğrular hizmeti için hala geçerli olduğundan emin olamaz.  
  
 Bu kimlik bilgisi türü kullanırken, hizmet hizmet hesabı altında çalışmalıdır unutmayın.  
  
 Kerberos protokolü, ileti kimlik bilgileri seçerken, varsayılan olarak kullanılır. Daha fazla bilgi için bkz: [keşfetme Kerberos, Windows 2000'de dağıtılmış güvenlik protokolü](http://go.microsoft.com/fwlink/?LinkId=87790).  
  
### <a name="username-password"></a>Kullanıcı adı parolası  
 Bu özelliği kullanarak, istemci bir kullanıcı adı parola ileti güvenlik üstbilgisinde kullanarak sunucu kimlik doğrulaması yapabilir.  
  
### <a name="issuedtoken"></a>IssuedToken  
 İstemci hizmetinin istemci kimlik doğrulaması iletiye eklenebilecek bir belirteç vermek için güvenlik belirteci hizmeti kullanabilirsiniz.  
  
## <a name="using-transport-and-message-security"></a>Taşıma ve ileti güvenliği kullanma  
 Taşıma Güveniği ve ileti güvenliği kullanırken, hem taşıma ve SOAP iletisi düzeyinde ileti güvenliğini sağlamak için kullanılan sertifikanın aynı olmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Aktarım Güvenliği Kullanarak İletileri Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)  
 [Message Queuing Üzerinden İleti Güvenliği](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)  
 [Güvenlik Kavramları](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
 [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
