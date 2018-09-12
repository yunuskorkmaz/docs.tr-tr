---
title: Hizmet Uç Noktaları ve Kuyruk İşleme
ms.date: 03/30/2017
ms.assetid: 7d2d59d7-f08b-44ed-bd31-913908b83d97
ms.openlocfilehash: 71ebf29e51118a7f555f3e79598e49ffd65e0c63
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44494323"
---
# <a name="service-endpoints-and-queue-addressing"></a>Hizmet Uç Noktaları ve Kuyruk İşleme
Bu konuda, istemciler sıralarından okuyun hizmetleri nasıl karşılayabileceği ve hizmet uç noktaları sıralara nasıl eşleştiği anlatılmaktadır. Aşağıdaki çizimde, bir anımsatıcı Klasik Windows Communication Foundation (WCF) uygulama dağıtımı kuyruğa gösterir.  
  
 ![Uygulama diyagramı kuyruğa](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "dağıtılmış-kuyruk-Şekil")  
  
 İstemci hizmete ileti göndermek istemci, iletinin hedef sıraya yöneliktir. Hizmet iletileri kuyruktan okunmak hedef kuyruğa dinleme adresini ayarlar. Message Queuing (MSMQ) kuyruk adları URI tabanlı değildir; ancak WCF'de adresleme Tekdüzen Kaynak Tanımlayıcısı URI tabanlıdır. Bu nedenle, MSMQ WCF kullanarak oluşturulan kuyruklar adres anlamak için önemlidir.  
  
## <a name="msmq-addressing"></a>MSMQ adresleme  
 MSMQ yollarını ve biçim adlarının bir sırayı tanımlamak için kullanır. Yolları, konak adı belirtin ve `QueueName`. İsteğe bağlı olarak olabilir bir `Private$` ana bilgisayar adı arasında ve `QueueName` Active Directory dizin hizmetinde yayınlanmamış özel bir sıra belirtmek için.  
  
 Yol adları "Yönlendirme ve Kuyruk yöneticisi Aktarımı Protokolü dahil olmak üzere adresini, ek yönlerini belirlemek için FormatNames" için eşlenir. Sıra yöneticisini iki aktarım protokollerini destekler: yerel MSMQ protokol ve SOAP Güvenilir Mesajlaşma Protokolü (SRMP).  
  
 MSMQ yolu ve biçim adları hakkında daha fazla bilgi için bkz. [hakkında Message Queuing](https://go.microsoft.com/fwlink/?LinkId=94837).  
  
## <a name="netmsmqbinding-and-service-addressing"></a>NetMsmqBinding ve adresleme hizmeti  
 Bir hizmete bir ileti adresleme, URI düzeni iletişim için kullanılan aktarım göre seçilir. Wcf'de her Aktarım, benzersiz bir düzene sahiptir. Düzeni iletişim için kullanılan aktarım doğasını yansıtmalıdır. Örneğin, net.tcp net.pipe, HTTP ve benzeri.  
  
 MSMQ taşıma WCF kullanıma sunan içinde net.msmq şeması kuyruğa alındı. Net.msmq Şeması kullanılarak gönderilen iletiler kullanılarak gönderilen `NetMsmqBinding` MSMQ sıraya alınan aktarım kanalı üzerinden.  
  
 Şu desen tabanlı WCF kuyrukta adresleme:  
  
 NET.MSMQ: / / \< *ana bilgisayar adı*> / [özel /] \< *kuyruk adı*>  
  
 burada:  
  
-   \<*ana bilgisayar adı*> hedef sıra barındıran bilgisayarın adıdır.  
  
-   [özel] isteğe bağlıdır. Özel bir kuyruk bir hedef kuyruk işleme olduğunda kullanılır. Bir genel sıra gidermek için özel belirtmemelidir. MSMQ yolları, "$" hiçbir WCF URI biçiminde dikkat edin.  
  
-   \<*Kuyruk adı*> Kuyruğun adı. Kuyruk adı için bir alt kuyruk de başvurabilir. Bu nedenle, \< *kuyruk adı*> = \< *kuyruk adı*> [; *Alt ad queue*].  
  
 Örnek1: özel bir sıra bilgisayar abc atadatum.com üzerinde barındırılan PurchaseOrders adreslemek için URI net.msmq://abc.adatum.com/private/PurchaseOrders olacaktır.  
  
 Örnek2: bir genel sıra bilgisayar def atadatum.com üzerinde barındırılan AccountsPayable ele almak için URI net.msmq://def.adatum.com/AccountsPayable olacaktır.  
  
 Kuyruk adresi dinleme URI olarak gelen iletileri okumak için dinleyici tarafından kullanılır. Diğer bir deyişle, kuyruk adresi için dinleme bağlantı noktası TCP yuvası eşdeğerdir.  
  
 Kuyruktan okuyan bir uç nokta ServiceHost açılırken daha önce belirtilen aynı düzeni kullanarak sıraya adresini belirtmeniz gerekir. Örnekler için bkz [ağ MSMQ bağlama](../../../../docs/framework/wcf/samples/net-msmq-binding.md) ve [Message Queuing tümleştirme bağlama örnekleri](https://msdn.microsoft.com/library/997d11cb-f2c5-4ba0-9209-92843d4d0e1a).  
  
### <a name="multiple-contracts-in-a-queue"></a>Kuyruktaki birden fazla anlaşma  
 Sıradaki iletilerin farklı sözleşmeler uygulayabilirsiniz. Bu durumda, aşağıdakilerden birini başarıyla okumak ve tüm iletileri işlemek için doğru olduğunu gereklidir:  
  
-   Tüm anlaşmalar uygulayan bir hizmette bir uç noktasını belirtin. Bu önerilen bir yaklaşımdır.  
  
-   Farklı sözleşmeler ile birden fazla uç nokta belirtin, ancak tüm uç noktalar aynı kullandığınızdan emin olun `NetMsmqBinding` nesne. ServiceModel dispatching mantık sonunda farklı uç noktalar sözleşmeye dayalı iletileri XML'deki bağlantıları çoğaltır gönderisi için taşıma kanalı iletileri okuyan bir ileti pompası kullanır. Bir ileti pompası, bir dinleme URI/bağlama çifti oluşturulur. Kuyruk adresi dinleme URI olarak sıraya alınan dinleyici tarafından kullanılır. Aynı bağlama nesnesi bir tek ileti pompası ileti okumak ve ilgili Uç noktalara çoğullamasını için kullanılmasını sağlar, tüm uç noktaları kullanmak zorunda sözleşme temel.  
  
### <a name="srmp-messaging"></a>SRMP Mesajlaşma  
 Daha önce bahsedildiği gibi SRMP Protokolü kuyruk sırası aktarımları için kullanabilirsiniz. Bir HTTP aktarımı iletileri iletim sırası hedef sıra arasındaki ilettiğinde yaygın olarak kullanılır.  
  
 SRMP aktarım protokolünü kullanmak için daha önce belirtildiği gibi adres net.msmq URI şeması kullanarak ileti ve seçtiğiniz SRMP veya güvenli SRMP içinde belirtin `QueueTransferProtocol` özelliği `NetMsmqBinding`.  
  
 Belirtme `QueueTransferProtocol` yalnızca gönderme özelliği özelliğidir. Bu kuyruk hangi tür Aktarım Protokolü kullanmak için istemci tarafından göstergesidir.  
  
### <a name="using-active-directory"></a>Active Directory kullanarak  
 MSMQ Active Directory Tümleştirme desteği ile birlikte gelir. MSMQ Active Directory Tümleştirmesi ile yüklendiğinde makine bir Windows etki alanının parçası olmalıdır. Active Directory bulma için kuyruklar yayımlamak için kullanılır; Bu tür sıralar adlı *genel sıralar*. Bir kuyruk işleme, kuyruk, Active Directory kullanarak çözülebilir. Bu, etki alanı adı sistemi (DNS) bir ağ adıyla IP adresini çözümlemek için nasıl kullanıldığı için benzer. `UseActiveDirectory` Özelliğinde `NetMsmqBinding` sıranın URI çözmek için kuyruğa alınmış kanalı Active Directory kullanan olup olmadığını gösteren bir Boole değeri. Varsayılan olarak ayarlanmış `false`. Varsa `UseActiveDirectory` özelliği `true`, kuyruğa alınmış kanal URI net.msmq:// biçim adına dönüştürmek için Active Directory kullanıyorsa.  
  
 `UseActiveDirectory` İletileri gönderirken kuyruğun adresini çözümlemek için kullanıldığından, ileti gönderirken yalnızca istemci için anlamlı özelliği.  
  
### <a name="mapping-netmsmq-uri-to-message-queuing-format-names"></a>Message Queuing biçim adlarından net.msmq URI eşleme  
 Sıraya alınan kanal MSMQ biçim adlarından kanala sağlanan net.msmq URI adı eşleme işler. Aşağıdaki tabloda, aralarında eşlemek için kullanılan kuralları özetlenmektedir.  
  
|WCF URI tabanlı sıra adresi|Active Directory özelliğini kullanın|Kuyruk Aktarım Protokolü özelliği|Sonuçta elde edilen MSMQ biçim adları|  
|----------------------------------|-----------------------------------|--------------------------------------|---------------------------------|  
|NET.MSMQ://\<makine-adı >/private/abc|False (varsayılan)|Yerel (varsayılan)|DOĞRUDAN OS:machine =-name\private$ \abc|  
|NET.MSMQ://\<makine-adı >/private/abc|False|SRMP|DOĞRUDAN =http://machine/msmq/private$/ abc|  
|NET.MSMQ://\<makine-adı >/private/abc|Doğru|Yerel|Genel GUID bazı (kuyruk GUID) =|  
  
### <a name="reading-messages-from-the-dead-letter-queue-or-the-poison-message-queue"></a>Eski ileti sırası veya Poison ileti kuyruktan iletileri okuma  
 Hedef sıra sırasına olan poison ileti kuyruktan iletileri okumak için açık `ServiceHost` subqueue adresi.  
  
 Örnek: yerel makineden PurchaseOrders özel sıranın poison ileti kuyruktan okuyan bir hizmet net.msmq://localhost/private/PurchaseOrders;poison adresi.  
  
 Bir sistem işlem eski ileti sırası iletileri okumak için URI biçiminde olmalıdır: net.msmq://localhost/system$; DeadXact.  
  
 Sistem işlem eski ileti kuyruktan iletileri okumak için URI biçiminde olmalıdır: net.msmq://localhost/system$; teslim edilemeyen iletiler.  
  
 Özel bir eski ileti sırası kullanırken, eski ileti sırası yerel bilgisayarda olması gerektiğini unutmayın. Bu nedenle, eski ileti sırası için URI forma sınırlıdır:  
  
 NET.MSMQ: //localhost/ [özel /] \< *özel-eski-harf-kuyruk-name*>.  
  
 Bir WCF hizmeti, aldığı tüm iletileri dinleme yaptığı belirli kuyruğa ele alınan doğrular. İletinin hedef sıraya sıranın içinde bulunan eşleşmiyorsa, hizmet iletiyi işlemez. Bu eski ileti sırası herhangi bir ileti başka bir yerde teslim gerektiği içerdiği Hizmetleri atılacak için dinleme çözülmesi gereken bir sorundur. Eski ileti sırası veya zararlı bir kuyruktan iletileri okumak için bir `ServiceBehavior` ile <xref:System.ServiceModel.AddressFilterMode.Any> parametre kullanılmalıdır. Bir örnek için bkz. [teslim edilemeyen](../../../../docs/framework/wcf/samples/dead-letter-queues.md).  
  
## <a name="msmqintegrationbinding-and-service-addressing"></a>MsmqIntegrationBinding ve adresleme hizmeti  
 `MsmqIntegrationBinding` Geleneksel MSMQ uygulamaları ile iletişim için kullanılır. Varolan bir MSMQ uygulama ile birlikte çalışma kolaylaştırmak için yalnızca biçim adı adresleme WCF destekler. Bu nedenle, bu bağlama kullanılarak gönderilen iletiler için URI şeması uyması gerekir:  
  
 MSMQ.FormatName:\<*MSMQ biçim adı*>>  
  
 MSMQ tarafından belirtilen biçim MSMQ biçim adı olduğu [hakkında Message Queuing](https://go.microsoft.com/fwlink/?LinkId=94837).  
  
 Yalnızca ortak ve özel biçim adlarının yanı sıra doğrudan biçim adlarından kullanabileceğinizi unutmayın (Active Directory ile tümleştirme gerektirir) kullanarak bir kuyruk iletileri alırken `MsmqIntegrationBinding`. Ancak, doğrudan biçim adlarından kullanmanız önerilir. Örneğin, [!INCLUDE[wv](../../../../includes/wv-md.md)], herhangi bir biçim adını kullanarak bir hataya neden olur çünkü sistem ile doğrudan biçim adlarından yalnızca açılabilir bir alt kuyruk açmayı dener.  
  
 SRMP kullanarak belirtirken `MsmqIntegrationBinding`, Internet Information Services (IIS) gönderme ile yardımcı olmak için doğrudan biçim adını /msmq/ eklemek için bir gereksinimi yoktur. Örneğin: abc SRMP kullanarak protokolü, yerine doğrudan bir kuyruk işleme olduğunda =http://adatum.com/msmq/private$/ abc kullanmanız gerektiğini doğrudan =http://adatum.com/private$/ abc.  
  
 Net.msmq:// adresleme kullanamayacağınızı unutmayın `MsmqIntegrationBinding`. Çünkü `MsmqIntegrationBinding` serbest biçimli MSMQ adı biçimi adresleme, destekleyen MSMQ çok noktaya yayın ve dağıtım listesi özellikleri kullanmak için bu bağlamayı kullanan bir WCF hizmeti kullanabilirsiniz. Bir özel durum belirten `CustomDeadLetterQueue` kullanırken `MsmqIntegrationBinding`. Bunun nasıl olduğu için benzer form net.msmq:// olmalıdır kullanarak belirtilen `NetMsmqBinding`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kuyruğa Alınan Bir Uygulamayı Web'de Barındırma](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md)
