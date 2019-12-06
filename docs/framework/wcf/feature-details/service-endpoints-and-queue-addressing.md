---
title: Hizmet Uç Noktaları ve Kuyruk İşleme
ms.date: 03/30/2017
ms.assetid: 7d2d59d7-f08b-44ed-bd31-913908b83d97
ms.openlocfilehash: 6bdd3b0966f85ff456e0e2ed0b6da773046201dc
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837993"
---
# <a name="service-endpoints-and-queue-addressing"></a>Hizmet Uç Noktaları ve Kuyruk İşleme
Bu konuda, istemcilerin kuyruklardan okuyan hizmetleri nasıl ele aldığı ve hizmet uç noktalarının kuyrukların nasıl eşlenme açıklanmaktadır. Bir anımsatıcı olarak, aşağıdaki çizimde, klasik Windows Communication Foundation (WCF) sıraya alınmış uygulama dağıtımı gösterilmektedir.  
  
 ![Kuyruğa alınmış uygulama diyagramı](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "Dağıtılmış kuyruk-şekil")  
  
 İstemcinin iletiyi hizmete gönderebilmesi için istemci, hedef sıraya iletiyi adresleyen. Hizmetin kuyruktaki iletileri okuyabilmesi için dinleme adresini hedef sıraya ayarlar. WCF 'de adresleme Tekdüzen Kaynak tanımlayıcısı (URI) tabanlı, Message Queuing (MSMQ) sıra adları URI tabanlı değil. Bu nedenle, WCF kullanarak MSMQ 'da oluşturulan sıraların nasıl ele alınacağını anlamak önemlidir.  
  
## <a name="msmq-addressing"></a>MSMQ adresleme  
 MSMQ, bir kuyruğu tanımlamak için yollar ve biçim adları kullanır. Yollar bir ana bilgisayar adı ve bir `QueueName`belirtir. İsteğe bağlı olarak, Active Directory dizin hizmetinde yayımlanmamış bir özel sırayı göstermek için ana bilgisayar adı ve `QueueName` arasında bir `Private$` olabilir.  
  
 Yol adları, Yönlendirme ve kuyruk yöneticisi Aktarım Protokolü dahil olmak üzere adresin ek yönlerini belirleyebilmek için "FormatNames" ile eşleştirilir. Kuyruk Yöneticisi iki aktarım protokolünü destekler: yerel MSMQ Protokolü ve SOAP Güvenilir Mesajlaşma Protokolü (SRMP).  
  
 MSMQ yolu ve biçim adları hakkında daha fazla bilgi için bkz. [about Message Queuing](https://go.microsoft.com/fwlink/?LinkId=94837).  
  
## <a name="netmsmqbinding-and-service-addressing"></a>NetMsmqBinding ve hizmet adresleme  
 Bir hizmete bir ileti adreslenirken, URI 'deki şema, iletişim için kullanılan ulaşım 'e göre seçilir. WCF 'deki her bir taşımanın benzersiz bir şeması vardır. Düzenin, iletişim için kullanılan taşımanın yapısını yansıtması gerekir. Örneğin, net. TCP, net. pipe, HTTP ve benzeri.  
  
 WCF 'de MSMQ sıraya alınan aktarım bir net. MSMQ şeması gösterir. Net. MSMQ şeması kullanılarak ele alınan herhangi bir ileti, MSMQ sıraya alınmış aktarım kanalı üzerinden `NetMsmqBinding` kullanılarak gönderilir.  
  
 WCF 'deki bir sıranın adreslenmesi aşağıdaki düzene dayanır:  
  
 net. MSMQ://\<*ana bilgisayar-adı*>/[private/] \<*kuyruk-adı*>  
  
 burada:  
  
- \<*konak adı*>, hedef kuyruğu barındıran makinenin adıdır.  
  
- [private] isteğe bağlıdır. Özel bir kuyruk olan hedef kuyruğu adreslemek için kullanılır. Genel bir kuyruğu ele almak için özel ' i belirtmemelidir. MSMQ yollarından farklı olarak, WCF URI formunda "$" olmadığını unutmayın.  
  
- \<*kuyruğu-adı*> kuyruğun adıdır. Sıra adı ayrıca bir alt sıraya de başvurabilir. Bu nedenle \<*kuyruk adı*> = \<*sıra adı*> [; *alt kuyruk-adı*].  
  
 Example1: PurchaseOrders, abc atadatum.com bilgisayarında barındırılan özel bir sıra Için adreslenebilir, URI net. MSMQ://abc.adatum.com/private/PurchaseOrders.  
  
 Example2: Computer def atadatum.com üzerinde barındırılan ortak bir sıra Accountspayrılabilir öğesine adreslenebilir, URI net. MSMQ://def.adatum.com/AccountsPayable.  
  
 Kuyruk adresi, iletileri okumak için dinleyici tarafından dinleme URI 'SI olarak kullanılır. Diğer bir deyişle, kuyruk adresi TCP yuvasının dinleme bağlantı noktasına eşdeğerdir.  
  
 Sıradan okuyan bir uç nokta, ServiceHost açılırken daha önce belirtilen düzeni kullanarak sıranın adresini belirtmelidir. Örnekler için bkz. [net MSMQ bağlama](../../../../docs/framework/wcf/samples/net-msmq-binding.md).  
  
### <a name="multiple-contracts-in-a-queue"></a>Kuyruktaki birden çok sözleşme  
 Kuyruktaki mesajlar farklı sözleşmeler uygulayabilir. Bu durumda, tüm iletileri başarıyla okumak ve işlemek için aşağıdakilerden birinin doğru olması önemlidir:  
  
- Tüm sözleşmeleri uygulayan bir hizmet için uç nokta belirtin. Bu, önerilen yaklaşımdır.  
  
- Farklı sözleşmelerle birden fazla uç nokta belirtin, ancak tüm uç noktaların aynı `NetMsmqBinding` nesnesini kullandığından emin olun. ServiceModel dağıtım mantığı, gönderimi için taşıma kanalının dışına iletileri okuyan bir ileti göndericisi kullanır ve bu da, sözleşmeye bağlı olarak iletileri farklı uç noktalara göre serbest parçalar. Dinleme URI 'SI/bağlama çifti için bir ileti göndericisi oluşturulur. Sıra adresi, kuyruğa alınan dinleyici tarafından dinleme URI 'SI olarak kullanılır. Tüm uç noktaların aynı bağlama nesnesini kullanmasını sağlamak, iletiyi okumak için tek bir ileti göndericisinin kullanılmasını ve sözleşmeye göre ilgili uç noktalara eşit bir şekilde sahip olmasını sağlar.  
  
### <a name="srmp-messaging"></a>SRMP mesajlaşma  
 Daha önce anlatıldığı gibi, kuyruk-kuyruk aktarımları için SRMP protokolünü kullanabilirsiniz. Bu genellikle bir HTTP taşıması Iletim kuyruğu ve hedef sıra arasında ileti ilettiğinden kullanılır.  
  
 SRMP aktarma protokolünü kullanmak için, daha önce belirtildiği gibi net. MSMQ URI şemasını kullanarak iletileri adresedin ve `NetMsmqBinding``QueueTransferProtocol` özelliğinde SRMP veya güvenli SRMP seçimini belirtin.  
  
 `QueueTransferProtocol` özelliğinin belirtilmesi, salt gönder özelliğidir. Bu, istemci tarafından kullanılacak sıra Aktarım protokolünün türünü belirten bir göstergesidir.  
  
### <a name="using-active-directory"></a>Active Directory kullanma  
 MSMQ, Active Directory tümleştirme desteğiyle birlikte gelir. MSMQ Active Directory tümleştirme ile yüklendiğinde, makinenin bir Windows etki alanının parçası olması gerekir. Active Directory, bulma kuyruklarını yayımlamak için kullanılır; Bu sıralara *genel kuyruklar*denir. Bir kuyruğun adreslenmesi sırasında, kuyruk Active Directory kullanılarak çözülebilir. Bu, bir ağ adının IP adresini çözümlemek için etki alanı adı sistemi 'nin (DNS) kullanılmasına benzer. `NetMsmqBinding` `UseActiveDirectory` özelliği, sıraya alınmış kanalın sıra URI 'sini çözümlemek için Active Directory kullanması gerekip gerekmediğini belirten bir Boole değeri. Varsayılan olarak, `false`olarak ayarlanır. `UseActiveDirectory` özelliği `true`olarak ayarlanırsa, sıraya alınan kanal net. MSMQ://URI 'sini biçim adına dönüştürmek için Active Directory kullanır.  
  
 `UseActiveDirectory` özelliği, ileti gönderilirken sıranın adresini çözümlemek için kullanıldığından, yalnızca iletiyi gönderen istemci için anlamlıdır.  
  
### <a name="mapping-netmsmq-uri-to-message-queuing-format-names"></a>Net. MSMQ URI 'sini Message Queuing biçim adlarına eşleme  
 Sıraya alınan kanal, belirtilen net. MSMQ URI adını kanala, MSMQ biçim adlarına eşlemeyi yönetir. Aşağıdaki tabloda aralarında eşleme yapmak için kullanılan kurallar özetlenmektedir.  
  
|WCF URI tabanlı sıra adresi|Active Directory özelliğini kullan|Sıra Aktarım Protokolü özelliği|Sonuçta elde edilen MSMQ biçim adları|  
|----------------------------------|-----------------------------------|--------------------------------------|---------------------------------|  
|Net. MSMQ://\<makine-adı >/Private/ABC|False (varsayılan)|Yerel (varsayılan)|DIRECT = OS: Machine-name\private $ \abc|  
|Net. MSMQ://\<makine-adı >/Private/ABC|False|SRMP|DIRECT =http://machine/msmq/private $/ABC|  
|Net. MSMQ://\<makine-adı >/Private/ABC|Doğru|Yerel|PUBLIC = bazı-GUID (kuyruğun GUID 'SI)|  
  
### <a name="reading-messages-from-the-dead-letter-queue-or-the-poison-message-queue"></a>Iletileri atılacak ileti sırasından veya Poison-Message sırasından okuma  
 Hedef sıranın alt sırası olan bir zarar iletisi kuyruğundan iletileri okumak için, alt sıranın adresine sahip `ServiceHost` açın.  
  
 Örnek: yerel makineden PurchaseOrders özel sırasının zarar iletisi kuyruğundan okuyan bir hizmet net. MSMQ://localhost/private/PurchaseOrders; poison adresine sahip olur.  
  
 Sistem işlem dışı ileti sırasından iletileri okumak için URI şu biçimde olmalıdır: net. MSMQ://localhost/System $;D Eadxyasası.  
  
 Bir sistem işlem dışı atılacak ileti sırasından iletileri okumak için URI şu biçimde olmalıdır: net. MSMQ://localhost/System $;D eadLetter.  
  
 Özel bir atılacak mektup sırası kullanırken, atılacak ileti sırasının yerel bilgisayarda bulunması gerektiğini unutmayın. Bu nedenle, atılacak ileti sırası için URI şu formla kısıtlıdır:  
  
 net. MSMQ://localhost/[private/] \<*özel-atılacak-harf kuyruğu-adı*>.  
  
 Bir WCF hizmeti, aldığı tüm iletilerin dinlediği belirli bir kuyruğa geldiğini doğrular. İletinin hedef kuyruğu içinde bulunduğu kuyrukla eşleşmiyorsa, hizmet iletiyi işlemez. Bu, atılacak ileti sırasındaki herhangi bir iletinin başka bir yere teslim edileceği için, atılacak bir sırayı dinleyen hizmetlerin adreslenmesi gereken bir sorundur. İletileri atılacak ileti sırasından veya bir zarar sırasından okumak için <xref:System.ServiceModel.AddressFilterMode.Any> parametresine sahip bir `ServiceBehavior` kullanılması gerekir. Bir örnek için bkz. [atılacak Ileti sıraları](../../../../docs/framework/wcf/samples/dead-letter-queues.md).  
  
## <a name="msmqintegrationbinding-and-service-addressing"></a>MsmqIntegrationBinding ve hizmet adresleme  
 `MsmqIntegrationBinding` geleneksel MSMQ uygulamalarıyla iletişim için kullanılır. Mevcut bir MSMQ uygulamasıyla birlikte çalışabilirliği kolaylaştırmak için, WCF yalnızca biçim adı adreslemeyi destekler. Bu nedenle, bu bağlama kullanılarak gönderilen iletilerin URI şemasına uygun olması gerekir:  
  
 MSMQ. FormatName:\<*MSMQ-biçim-adı*>>  
  
 MSMQ biçimindeki adı, hakkında MSMQ tarafından belirtilen biçimde belirtilir [Message Queuing](https://go.microsoft.com/fwlink/?LinkId=94837).  
  
 `MsmqIntegrationBinding`kullanarak bir kuyruktan ileti alırken yalnızca doğrudan biçim adlarını ve ortak ve özel biçim adlarını (Active Directory tümleştirme gerektirir) kullanabileceğinizi unutmayın. Ancak, doğrudan biçim adları kullanmanız önerilir. Örneğin, Windows Vista 'da, başka bir biçim adı kullanılması, sistem bir alt sıra açmaya çalıştığı ve yalnızca doğrudan biçim adlarıyla açılabilen bir hataya neden olur.  
  
 `MsmqIntegrationBinding`kullanarak SRMP 'nin adreslenmesi sırasında, doğrudan biçim Internet Information Services adında/MSMQ/eklemek için bir gereksinim yoktur. Örneğin: doğrudan =http://adatum.com/msmq/private $/ABC yerine SRMP protokolünü kullanarak ABC kuyruğunu adreslendirirken doğrudan =http://adatum.com/private $/abckullanmanız gerekir.  
  
 `MsmqIntegrationBinding`ile net. MSMQ://adreslemeyi kullanmayacağınızı unutmayın. `MsmqIntegrationBinding`, serbest biçimli MSMQ biçimi adı adresini desteklediğinden, MSMQ 'daki çok noktaya yayın ve dağıtım listesi özelliklerini kullanmak için bu bağlamayı kullanan bir WCF hizmeti kullanabilirsiniz. Bir özel durum, `MsmqIntegrationBinding`kullanılırken `CustomDeadLetterQueue` belirtmektir. Bu, `NetMsmqBinding`kullanarak nasıl belirtime benzer şekilde net. MSMQ://biçiminde olmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kuyruğa Alınan Bir Uygulamayı Web'de Barındırma](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md)
