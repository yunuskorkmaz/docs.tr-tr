---
title: İleti Güveliği Kullanarak İletileri Güvenli Hale Getirme
ms.date: 03/30/2017
ms.assetid: a17ebe67-836b-4c52-9a81-2c3d58e225ee
ms.openlocfilehash: 4432540bfb6238be5b3e102283d6b67bebad07bd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610961"
---
# <a name="securing-messages-using-message-security"></a>İleti Güveliği Kullanarak İletileri Güvenli Hale Getirme
Bu bölümde kullanırken WCF ileti güvenliğini ele alınmaktadır <xref:System.ServiceModel.NetMsmqBinding>.  
  
> [!NOTE]
>  Bu konu içinde okumadan önce okumanızı önerilir [güvenlik kavramları](../../../../docs/framework/wcf/feature-details/security-concepts.md).  
  
 Aşağıdaki çizim, kavramsal modelin WCF kullanan kuyruğa alınan iletişim sağlar. Bu çizimde ve terminoloji açıklamak için kullanılır  
  
 güvenlik kavramları taşıma.  
  
 ![Uygulama diyagramı kuyruğa](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "dağıtılmış-kuyruk-Şekil")  
  
 WCF kullanarak iletileri kuyruğa gönderme, WCF ileti Message Queuing (MSMQ) ileti gövdesi olarak eklenir. Tüm MSMQ İleti, mesaja (veya SOAP) aktarım güvenliği korur ancak güvenlik yalnızca MSMQ iletisinin gövdesini güvenliğini sağlar.  
  
 İleti güvenliği temel kavramı, istemci aktarım güvenliği istemci ileti hedef sıra için burada korur aksine (hizmet), alıcı uygulamanın iletiyi korur ' dir. Bu nedenle, MSMQ hiçbir bölümü ileti güveliği kullanarak WCF ileti güvenliğini sağlama çalar.  
  
 WCF ileti güvenliğini sertifika veya Kerberos protokolü gibi mevcut güvenlik altyapıları ile tümleşen WCF ileti güvenlik üst bilgileri ekler.  
  
## <a name="message-credential-type"></a>İleti kimlik bilgisi türü  
 İleti güveliği kullanarak, hizmet ve istemci, her kimlik doğrulaması için kimlik sunabilir. İleti güvenliği ayarlayarak seçebileceğiniz <xref:System.ServiceModel.NetMsmqBinding.Security%2A> moduna `Message` veya `Both` (diğer bir deyişle, hem aktarım güvenliği ve ileti güvenliği kullanın).  
  
 Hizmeti kullanım <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> özelliği istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini inceleyin. Bu da daha fazla yetkilendirme denetimleri için hizmete uygulamak için seçtiği kullanılabilir.  
  
 Bu bölüm, farklı bir kimlik bilgisi türlerini ve bunları kuyruklarla nasıl kullanacağınızı açıklar.  
  
### <a name="certificate"></a>Sertifika  
 Sertifika kimlik bilgisi türü, hizmet ve istemci tanımlamak için bir X.509 sertifikası kullanır.  
  
 Tipik bir senaryoda, istemciyi ve hizmeti geçerli bir sertifika bir güvenilen sertifika yetkilisi tarafından verilir. Daha sonra bağlantı kurulur, istemci hizmeti güvenip güvenmediğini karar vermek için hizmet sertifikası kullanarak hizmet geçerliliğini doğrular. Benzer şekilde, hizmet istemci güven doğrulamak için istemci sertifikasını kullanır.  
  
 Bağlantısı kesilmiş sıraların göz önünde bulundurulduğunda, hizmet ve istemci aynı anda çevrimiçi olmayabilir. Bu nedenle, hizmet ve istemci sertifikaları-bant exchange gerekir. Özellikle (bir sertifika yetkilisine zincirleme yapılabilir) hizmet sertifikasını kendi güvenilen deposunda bulunduran da istemci, doğru hizmet ile iletişim kurduğunu güvenmesi gerekir. İstemci kimlik doğrulaması için hizmeti kullandığı iletiye ile bağlı X.509 sertifikası, istemcinin orjinalliği doğrulamak için depolama alanındaki sertifikaya ile eşleşir. Yeniden sertifika bir sertifika yetkilisine zincirlenmiş olması gerekir.  
  
 Windows çalıştıran bir bilgisayarda, sertifika depolarını çeşitli türlerde tutulur. Farklı depoları hakkında daha fazla bilgi için bkz. [sertifika depolarını](https://go.microsoft.com/fwlink/?LinkId=87787).  
  
### <a name="windows"></a>Windows  
 Windows ileti kimlik bilgisi türü Kerberos protokolünü kullanır.  
  
 Kerberos protokolü bir etki alanındaki kullanıcıların kimliğini doğrular ve bir etki alanındaki diğer varlıklarla güvenli bağlamları kurmak kimliği doğrulanmış kullanıcılara izin veren bir güvenlik mekanizmasıdır.  
  
 Kuyruğa alınan iletişim için Kerberos protokolünü kullanarak sorunu dağıtan Anahtar Dağıtım Merkezi (KDC) istemci kimliğini içeren biletleri görece kısa süreli olmasıdır. A *ömrü* bilet geçerliliğini gösteren Kerberos anahtarı ile ilişkilidir. Bu nedenle, yüksek oranda gecikme süreleri göz önünde bulundurulduğunda, belirteç için istemci kimlik doğrulaması hizmeti hala geçerli olduğundan emin olamaz.  
  
 Bu kimlik bilgisi türü kullanırken dikkat edin, hizmeti hizmet hesabı altında çalışıyor olmalıdır.  
  
 Kerberos protokolü, ileti kimlik bilgileri seçerken, varsayılan olarak kullanılır. Daha fazla bilgi için [keşfetmeye Kerberos, Windows 2000'de dağıtılmış güvenlik protokolü](https://go.microsoft.com/fwlink/?LinkId=87790).  
  
### <a name="username-password"></a>Kullanıcı adı parola  
 Bu özelliği kullanarak, istemciye ileti güvenlik üst bilgisinde bir kullanıcı adı parola kullanarak sunucuya kimlik doğrulaması yapabilir.  
  
### <a name="issuedtoken"></a>IssuedToken  
 İstemci hizmeti istemcinin kimliğini doğrulamak iletiye eklenebilecek bir belirteç vermek için güvenlik belirteci hizmeti kullanabilirsiniz.  
  
## <a name="using-transport-and-message-security"></a>Taşıma ve ileti güvenliği kullanma  
 Hem aktarım güvenliği ve ileti güvenliği kullanırken hem aktarım ve SOAP iletisi düzeyinde ileti güvenliğini sağlamak için kullanılan sertifikanın aynı olmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Aktarım Güvenliği Kullanarak İletileri Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)
- [Message Queuing Üzerinden İleti Güvenliği](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
- [Güvenlik Kavramları](../../../../docs/framework/wcf/feature-details/security-concepts.md)
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
