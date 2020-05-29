---
title: Hizmet Uç Noktaları ve Kuyruk İşleme
ms.date: 03/30/2017
ms.assetid: 7d2d59d7-f08b-44ed-bd31-913908b83d97
ms.openlocfilehash: 8b323993a698dac219e0f2be43e9b508a19065dd
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202418"
---
# <a name="service-endpoints-and-queue-addressing"></a>Hizmet Uç Noktaları ve Kuyruk İşleme
Bu konuda, istemcilerin kuyruklardan okuyan hizmetleri nasıl ele aldığı ve hizmet uç noktalarının kuyrukların nasıl eşlenme açıklanmaktadır. Bir anımsatıcı olarak, aşağıdaki çizimde, klasik Windows Communication Foundation (WCF) sıraya alınmış uygulama dağıtımı gösterilmektedir.  
  
 ![Kuyruğa alınmış uygulama diyagramı](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "Dağıtılmış kuyruk-şekil")  
  
 İstemcinin iletiyi hizmete gönderebilmesi için istemci, hedef sıraya iletiyi adresleyen. Hizmetin kuyruktaki iletileri okuyabilmesi için dinleme adresini hedef sıraya ayarlar. WCF 'de adresleme Tekdüzen Kaynak tanımlayıcısı (URI) tabanlı, Message Queuing (MSMQ) sıra adları URI tabanlı değil. Bu nedenle, WCF kullanarak MSMQ 'da oluşturulan sıraların nasıl ele alınacağını anlamak önemlidir.  
  
## <a name="msmq-addressing"></a>MSMQ adresleme  
 MSMQ, bir kuyruğu tanımlamak için yollar ve biçim adları kullanır. Yollar bir ana bilgisayar adı ve bir belirtir `QueueName` . İsteğe bağlı olarak, `Private$` ana bilgisayar adı arasında ve `QueueName` Active Directory dizin hizmetinde yayımlanmamış bir özel sırayı göstermek için bir de olabilir.  
  
 Yol adları, Yönlendirme ve kuyruk yöneticisi Aktarım Protokolü dahil olmak üzere adresin ek yönlerini belirleyebilmek için "FormatNames" ile eşleştirilir. Kuyruk Yöneticisi iki aktarım protokolünü destekler: yerel MSMQ Protokolü ve SOAP Güvenilir Mesajlaşma Protokolü (SRMP).  
  
 MSMQ yolu ve biçim adları hakkında daha fazla bilgi için bkz. [about Message Queuing](https://docs.microsoft.com/previous-versions/windows/desktop/legacy/ms706032(v=vs.85)).  
  
## <a name="netmsmqbinding-and-service-addressing"></a>NetMsmqBinding ve hizmet adresleme  
 Bir hizmete bir ileti adreslenirken, URI 'deki şema, iletişim için kullanılan ulaşım 'e göre seçilir. WCF 'deki her bir taşımanın benzersiz bir şeması vardır. Düzenin, iletişim için kullanılan taşımanın yapısını yansıtması gerekir. Örneğin, net. TCP, net. pipe, HTTP ve benzeri.  
  
 WCF 'de MSMQ sıraya alınan aktarım bir net. MSMQ şeması gösterir. Net. MSMQ şeması kullanılarak ele alınan tüm iletiler, `NetMsmqBinding` MSMQ sıraya alınmış aktarım kanalı üzerinden kullanılarak gönderilir.  
  
 WCF 'deki bir sıranın adreslenmesi aşağıdaki düzene dayanır:  
  
 net. MSMQ:// \<*host-name*> /[private/]\<*queue-name*>  
  
 burada:  
  
- \<*host-name*>, hedef kuyruğu barındıran makinenin adıdır.  
  
- [private] isteğe bağlıdır. Özel bir kuyruk olan hedef kuyruğu adreslemek için kullanılır. Genel bir kuyruğu ele almak için özel ' i belirtmemelidir. MSMQ yollarından farklı olarak, WCF URI formunda "$" olmadığını unutmayın.  
  
- \<*queue-name*>Kuyruğun adıdır. Sıra adı ayrıca bir alt sıraya de başvurabilir. Bu nedenle, \<*queue-name*>  =  \<*name-of-queue*> [;* alt kuyruk-adı*].  
  
 Example1: PurchaseOrders, abc atadatum.com bilgisayarında barındırılan özel bir sıra Için adreslenebilir, URI net. MSMQ://abc.adatum.com/private/PurchaseOrders.  
  
 Example2: Computer def atadatum.com üzerinde barındırılan ortak bir sıra Accountspayrılabilir öğesine adreslenebilir, URI net. MSMQ://def.adatum.com/AccountsPayable.  
  
 Kuyruk adresi, iletileri okumak için dinleyici tarafından dinleme URI 'SI olarak kullanılır. Diğer bir deyişle, kuyruk adresi TCP yuvasının dinleme bağlantı noktasına eşdeğerdir.  
  
 Sıradan okuyan bir uç nokta, ServiceHost açılırken daha önce belirtilen düzeni kullanarak sıranın adresini belirtmelidir. Örnekler için bkz. [net MSMQ bağlama](../../../../docs/framework/wcf/samples/net-msmq-binding.md).  
  
### <a name="multiple-contracts-in-a-queue"></a>Kuyruktaki birden çok sözleşme  
 Kuyruktaki mesajlar farklı sözleşmeler uygulayabilir. Bu durumda, tüm iletileri başarıyla okumak ve işlemek için aşağıdakilerden birinin doğru olması önemlidir:  
  
- Tüm sözleşmeleri uygulayan bir hizmet için uç nokta belirtin. Bu, önerilen yaklaşımdır.  
  
- Farklı sözleşmelerle birden fazla uç nokta belirtin, ancak tüm uç noktaların aynı nesneyi kullandığından emin olun `NetMsmqBinding` . ServiceModel dağıtım mantığı, gönderimi için taşıma kanalının dışına iletileri okuyan bir ileti göndericisi kullanır ve bu da, sözleşmeye bağlı olarak iletileri farklı uç noktalara göre serbest parçalar. Dinleme URI 'SI/bağlama çifti için bir ileti göndericisi oluşturulur. Sıra adresi, kuyruğa alınan dinleyici tarafından dinleme URI 'SI olarak kullanılır. Tüm uç noktaların aynı bağlama nesnesini kullanmasını sağlamak, iletiyi okumak için tek bir ileti göndericisinin kullanılmasını ve sözleşmeye göre ilgili uç noktalara eşit bir şekilde sahip olmasını sağlar.  
  
### <a name="srmp-messaging"></a>SRMP mesajlaşma  
 Daha önce anlatıldığı gibi, kuyruk-kuyruk aktarımları için SRMP protokolünü kullanabilirsiniz. Bu genellikle bir HTTP taşıması Iletim kuyruğu ve hedef sıra arasında ileti ilettiğinden kullanılır.  
  
 SRMP aktarma protokolünü kullanmak için, daha önce belirtildiği gibi net. MSMQ URI şemasını kullanarak iletileri adresedin ve ' nin özelliğinde SRMP veya güvenli SRMP seçimini belirtin `QueueTransferProtocol` `NetMsmqBinding` .  
  
 Özelliğin belirtilmesi, `QueueTransferProtocol` salt gönder özelliğidir. Bu, istemci tarafından kullanılacak sıra Aktarım protokolünün türünü belirten bir göstergesidir.  
  
### <a name="using-active-directory"></a>Active Directory kullanarak  
 MSMQ, Active Directory tümleştirme desteğiyle birlikte gelir. MSMQ Active Directory tümleştirme ile yüklendiğinde, makinenin bir Windows etki alanının parçası olması gerekir. Active Directory, bulma kuyruklarını yayımlamak için kullanılır; Bu sıralara *genel kuyruklar*denir. Bir kuyruğun adreslenmesi sırasında, kuyruk Active Directory kullanılarak çözülebilir. Bu, bir ağ adının IP adresini çözümlemek için etki alanı adı sistemi 'nin (DNS) kullanılmasına benzer. `UseActiveDirectory`İçindeki özelliği, `NetMsmqBinding` sıraya alınan KANALıN sıra URI 'sini çözümlemek için Active Directory kullanması gerekip gerekmediğini belirten bir Boole değeri. Varsayılan olarak olarak ayarlanır `false` . `UseActiveDirectory`Özelliği olarak ayarlandıysa `true` , sıraya alınan kanal net. MSMQ://URI 'sini biçim adına dönüştürmek için Active Directory kullanır.  
  
 `UseActiveDirectory`Özelliği, ileti gönderilirken sıranın adresini çözümlemek için kullanıldığından, yalnızca iletiyi gönderen istemci için anlamlıdır.  
  
### <a name="mapping-netmsmq-uri-to-message-queuing-format-names"></a>Net. MSMQ URI 'sini Message Queuing biçim adlarına eşleme  
 Sıraya alınan kanal, belirtilen net. MSMQ URI adını kanala, MSMQ biçim adlarına eşlemeyi yönetir. Aşağıdaki tabloda aralarında eşleme yapmak için kullanılan kurallar özetlenmektedir.  
  
|WCF URI tabanlı sıra adresi|Active Directory özelliğini kullan|Sıra Aktarım Protokolü özelliği|Sonuçta elde edilen MSMQ biçim adları|  
|----------------------------------|-----------------------------------|--------------------------------------|---------------------------------|  
|`Net.msmq://<machine-name>/private/abc`|False (varsayılan)|Yerel (varsayılan)|`DIRECT=OS:machine-name\private$\abc`|  
|`Net.msmq://<machine-name>/private/abc`|False|SRMP|`DIRECT=http://machine/msmq/private$/abc`|  
|`Net.msmq://<machine-name>/private/abc`|True|Yerel|`PUBLIC=some-guid`(kuyruğun GUID 'SI)|  
  
### <a name="reading-messages-from-the-dead-letter-queue-or-the-poison-message-queue"></a>Iletileri atılacak ileti sırasından veya Poison-Message sırasından okuma  
 Hedef sıranın alt sırası olan bir zarar iletisi kuyruğundan iletileri okumak için, alt `ServiceHost` sıranın adresiyle birlikte öğesini açın.  
  
 Örnek: yerel makineden PurchaseOrders özel sırasının zarar iletisi kuyruğundan okuyan bir hizmet net. MSMQ://localhost/private/PurchaseOrders; poison adresine sahip olur.  
  
 Sistem işlem dışı ileti sırasından iletileri okumak için URI şu biçimde olmalıdır: net. MSMQ://localhost/System $;D Eadxyasası.  
  
 Bir sistem işlem dışı atılacak ileti sırasından iletileri okumak için URI şu biçimde olmalıdır: net. MSMQ://localhost/System $;D eadLetter.  
  
 Özel bir atılacak mektup sırası kullanırken, atılacak ileti sırasının yerel bilgisayarda bulunması gerektiğini unutmayın. Bu nedenle, atılacak ileti sırası için URI şu formla kısıtlıdır:  
  
 net. MSMQ://localhost/[private/] \<*custom-dead-letter-queue-name*> .  
  
 Bir WCF hizmeti, aldığı tüm iletilerin dinlediği belirli bir kuyruğa geldiğini doğrular. İletinin hedef kuyruğu içinde bulunduğu kuyrukla eşleşmiyorsa, hizmet iletiyi işlemez. Bu, atılacak ileti sırasındaki herhangi bir iletinin başka bir yere teslim edileceği için, atılacak bir sırayı dinleyen hizmetlerin adreslenmesi gereken bir sorundur. İletileri bir atılacak ileti sırasından veya bir zarar sırasından okumak için `ServiceBehavior` parametresi ile birlikte <xref:System.ServiceModel.AddressFilterMode.Any> kullanılması gerekir. Bir örnek için bkz. [atılacak Ileti sıraları](../../../../docs/framework/wcf/samples/dead-letter-queues.md).  
  
## <a name="msmqintegrationbinding-and-service-addressing"></a>MsmqIntegrationBinding ve hizmet adresleme  
 `MsmqIntegrationBinding`Geleneksel MSMQ uygulamalarıyla iletişim için kullanılır. Mevcut bir MSMQ uygulamasıyla birlikte çalışabilirliği kolaylaştırmak için, WCF yalnızca biçim adı adreslemeyi destekler. Bu nedenle, bu bağlama kullanılarak gönderilen iletilerin URI şemasına uygun olması gerekir:  
  
 MSMQ. FormatName:\<*MSMQ-format-name*>>  
  
 MSMQ biçimindeki adı, hakkında MSMQ tarafından belirtilen biçimde belirtilir [Message Queuing](https://docs.microsoft.com/previous-versions/windows/desktop/legacy/ms706032(v=vs.85)).  
  
 Kullanarak bir kuyruktan ileti alırken doğrudan biçim adlarını ve ortak ve özel biçim adlarını (Active Directory tümleştirme gerektirir) kullanabileceğinizi unutmayın `MsmqIntegrationBinding` . Ancak, doğrudan biçim adları kullanmanız önerilir. Örneğin, Windows Vista 'da, başka bir biçim adı kullanılması, sistem bir alt sıra açmaya çalıştığı ve yalnızca doğrudan biçim adlarıyla açılabilen bir hataya neden olur.  
  
 ' Yi kullanarak SRMP `MsmqIntegrationBinding` ' ı adreslarken, doğrudan biçim adında, dağıtma ile Internet Information Services (IIS) yardım için/MSMQ/ekleme gereksinimi yoktur. Örneğin: bir sıra ABC protokolünü kullanan bir kuyruk adreslendirilirken `DIRECT=http://adatum.com/msmq/private$/abc` , yerine kullanmanız gerekir `DIRECT=http://adatum.com/private$/abc` .  
  
 Net. MSMQ://adreslemeyi ile kullanamazsınız `MsmqIntegrationBinding` . `MsmqIntegrationBinding`, Serbest BIÇIMLI MSMQ biçimi adı adreslemesini desteklediğinden, MSMQ 'daki çok noktaya yayın ve dağıtım listesi özelliklerini kullanmak için bu bağlamayı kullanan BIR WCF hizmeti kullanabilirsiniz. Kullanırken bir özel durum belirtiliyor `CustomDeadLetterQueue` `MsmqIntegrationBinding` . Kullanılarak nasıl belirtime benzer şekilde, net. MSMQ://biçiminde olmalıdır `NetMsmqBinding` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kuyruğa Alınan Bir Uygulamayı Web'de Barındırma](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md)
