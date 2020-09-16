---
title: İleti Güveliği Kullanarak İletileri Güvenli Hale Getirme
ms.date: 03/30/2017
ms.assetid: a17ebe67-836b-4c52-9a81-2c3d58e225ee
ms.openlocfilehash: b5f7679d5e5ec82e63b588cebd90ce873c055088
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558309"
---
# <a name="securing-messages-using-message-security"></a>İleti Güveliği Kullanarak İletileri Güvenli Hale Getirme
Bu bölümde kullanırken WCF ileti güvenliği ele alınmaktadır <xref:System.ServiceModel.NetMsmqBinding> .  
  
> [!NOTE]
> Bu konuyu okumadan önce [güvenlik kavramlarını](security-concepts.md)okumanız önerilir.  
  
 Aşağıdaki çizimde, WCF kullanılarak sıraya alınmış iletişimin kavramsal bir modeli verilmiştir. Bu çizim ve terminoloji açıklamak için kullanılır  
  
 taşıma güvenlik kavramları.  
  
 ![Kuyruğa alınmış uygulama diyagramı](media/distributed-queue-figure.jpg "Dağıtılmış kuyruk-şekil")  
  
 WCF kullanarak sıraya alınan iletileri gönderirken WCF iletisi Message Queuing (MSMQ) iletisinin bir gövdesi olarak eklenir. Taşıma güvenliği tüm MSMQ iletisinin güvenliğini sağlarken, ileti (veya SOAP) güvenliği yalnızca MSMQ iletisinin gövdesine güvenlik sağlar.  
  
 İleti güvenliği kavramı, istemcinin hedef sıranın iletisini güvenlik altına aldığı aktarım güvenliği aksine, istemci alıcı uygulama (hizmet) için iletiyi güvenlik altına almadır. Bu nedenle, MSMQ ileti güvenliği kullanılarak WCF iletisini güvenli hale getirirken hiçbir bölüm vermez.  
  
 WCF ileti güvenliği, bir sertifika veya Kerberos protokolü gibi mevcut güvenlik altyapılarıyla tümleştirilen WCF iletisine güvenlik üstbilgileri ekler.  
  
## <a name="message-credential-type"></a>İleti kimlik bilgisi türü  
 Hizmet ve istemci, ileti güvenliğini kullanarak birbirlerinin kimliğini doğrulamak için kimlik bilgilerini sunabilir. Modu veya olarak ayarlayarak ileti güvenliği seçebilirsiniz <xref:System.ServiceModel.NetMsmqBinding.Security%2A> `Message` `Both` (yani, hem aktarım güvenliği hem de ileti güvenliği kullanın).  
  
 Hizmet, <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> istemcinin kimliğini doğrulamak için kullanılan kimlik bilgilerini incelemek için özelliğini kullanabilir. Bu, hizmetin uygulamayı seçtiği daha fazla yetkilendirme denetimi için de kullanılabilir.  
  
 Bu bölümde farklı kimlik bilgisi türleri ve kuyrukların nasıl kullanılacağı açıklanmaktadır.  
  
### <a name="certificate"></a>Sertifika  
 Sertifika kimlik bilgileri türü bir X. 509.440 sertifikası kullanarak hizmeti ve istemciyi belirler.  
  
 Tipik bir senaryoda, istemci ve hizmet güvenilen bir sertifika yetkilisi tarafından geçerli bir sertifika verilir. Sonra bağlantı oluşturulur, istemci hizmete güvenip güvenmeyeceğine karar vermek için hizmetin sertifikasını kullanarak hizmetin geçerliliğini doğrular. Benzer şekilde, hizmet istemci güvenini doğrulamak için istemcinin sertifikasını kullanır.  
  
 Kuyrukların bağlantısı kesilen doğası gereği, istemci ve hizmet aynı anda çevrimiçi olmayabilir. Bu nedenle, istemci ve hizmetin sertifikaları bant dışı olarak alışverişi gerekir. Özellikle, güvenilen depodaki hizmetin sertifikasını (bir sertifika yetkilisine zincirlenebilir) tutan istemci sanallaştırılan istemci, doğru hizmetle iletişim kurduğu güvenmelidir. İstemcinin kimliğini doğrulamak için hizmet, istemciyle birlikte gelen X. 509.440 sertifikasını kullanarak istemcinin orijinalliğini doğrular. Yeniden, sertifikanın bir sertifika yetkilisine zincirleme olması gerekir.  
  
 Windows çalıştıran bir bilgisayarda, sertifikalar çeşitli türlerde depolarda tutulur. Farklı mağazalar hakkında daha fazla bilgi için bkz. [sertifika depoları](/previous-versions/windows/it-pro/windows-server-2003/cc757138(v=ws.10)).  
  
### <a name="windows"></a>Windows  
 Windows ileti kimlik bilgisi türü Kerberos protokolünü kullanır.  
  
 Kerberos protokolü, bir etki alanındaki kullanıcıların kimliğini doğrulayan ve kimliği doğrulanmış kullanıcıların bir etki alanındaki diğer varlıklarla güvenli bağlamlar kurmasını sağlayan bir güvenlik mekanizmasıdır.  
  
 Sıraya alınan iletişim için Kerberos protokolünü kullanmayla ilgili sorun, Anahtar Dağıtım Merkezi (KDC) tarafından dağıtılan istemci kimliğini içeren anahtarların görece kısa ömürlü olduğundan emin olur. Bir *yaşam süresi* , Bilet geçerliliğini gösteren Kerberos bileti ile ilişkilendirilir. Bu nedenle, yüksek gecikme süresi verilen, belirtecin istemcinin kimliğini doğrulayan hizmet için hala geçerli olduğundan emin olabilirsiniz.  
  
 Bu kimlik bilgisi türü kullanılırken hizmetin HIZMET hesabı altında çalışıyor olması gerektiğini unutmayın.  
  
 İleti kimlik bilgisi seçerken Kerberos protokolü varsayılan olarak kullanılır.
  
### <a name="username-password"></a>Kullanıcı adı parolası  
 Bu özelliği kullanarak istemci, iletinin güvenlik üstbilgisinde bir Kullanıcı adı parolası kullanarak sunucuda kimlik doğrulaması yapabilir.  
  
### <a name="issuedtoken"></a>IssuedToken  
 İstemci, istemcinin kimliğini doğrulamak üzere hizmetin iletisine iliştirilebilecek bir belirteç vermek için güvenlik belirteci hizmetini kullanabilir.  
  
## <a name="using-transport-and-message-security"></a>Aktarım ve Ileti güvenliğini kullanma  
 Hem aktarım güvenliği hem de ileti güvenliği kullanılırken, iletiyi hem aktarımda hem de SOAP ileti düzeyinde güvenli hale getirmek için kullanılan sertifikanın aynı olması gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Taşıma Güveliği Kullanarak İletileri Güvenli Hale Getirme](securing-messages-using-transport-security.md)
- [İleti Kuyruğa Alma ile İleti Güvenliği](../samples/message-security-over-message-queuing.md)
- [Güvenlik Kavramları](security-concepts.md)
- [Hizmet ve İstemcileri Güvenli Hale Getirme](securing-services-and-clients.md)
