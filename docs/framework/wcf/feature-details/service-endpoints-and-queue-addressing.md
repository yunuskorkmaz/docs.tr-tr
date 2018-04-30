---
title: Hizmet Uç Noktaları ve Kuyruk İşleme
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7d2d59d7-f08b-44ed-bd31-913908b83d97
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f2244ccb1637f944f9e3349cf0d94caa2f6676bf
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="service-endpoints-and-queue-addressing"></a>Hizmet Uç Noktaları ve Kuyruk İşleme
Bu konuda ele alınmıştır nasıl istemcileri adresi sıralarından okuma Hizmetleri ve hizmet uç noktaları sıralara nasıl eşleyin. Bir anımsatıcı Klasik aşağıda gösterilmiştir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] uygulama dağıtımı sıraya alındı.  
  
 ![Sıraya alınan uygulama diyagramı](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "dağıtılmış-sıra-Şekil")  
  
 İstemci hizmete ileti göndermek istemci iletinin hedef sıraya giderir. Sıradaki iletileri okumak için hizmeti, hedef sıra dinleme adresini ayarlar. İçinde adresleme [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Message Queuing (MSMQ) sıra adları URI tabanlı değildir; ancak Tekdüzen Kaynak Tanımlayıcısı URI tabanlıdır. Bu nedenle MSMQ kullanılarak oluşturulan sıraları adres öğrenmek için gerekli olan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="msmq-addressing"></a>MSMQ adresleme  
 MSMQ yolları ve biçim adları bir sırayı tanımlamak için kullanır. Yollar bir ana bilgisayar adı belirtin ve bir `QueueName`. İsteğe bağlı olarak, olabilir bir `Private$` ana bilgisayar adı arasında ve `QueueName` Active Directory dizin hizmetinde yayımlanmamış özel bir sıra belirtmek için.  
  
 Yol adları "Yönlendirme ve sıra yöneticisi Aktarım Protokolü dahil olmak üzere adresini, ek yönlerini belirlemek için FormatNames" için eşlenir. Sıra yöneticisini iki aktarım protokollerini destekler: yerel MSMQ protokolü ve SOAP Güvenilir Mesajlaşma Protokolü (SRMP).  
  
 MSMQ yolu ve biçim adları hakkında daha fazla bilgi için bkz: [hakkında Message Queuing](http://go.microsoft.com/fwlink/?LinkId=94837).  
  
## <a name="netmsmqbinding-and-service-addressing"></a>NetMsmqBinding ve hizmet adresleme  
 Bir hizmet için bir ileti belirtirken, URI düzeni iletişim için kullanılan aktarım göre seçilir. Her aktarım [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] benzersiz şemasına sahip. Düzeni iletişim için kullanılan aktarım yapısını yansıtması gerekir. Örneğin, net.tcp, net.pipe, HTTP ve benzeri.  
  
 MSMQ sıraya taşımasına [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] net.msmq şeması kullanıma sunar. Net.msmq şeması kullanarak ele alınan ileti kullanılarak gönderilen `NetMsmqBinding` MSMQ sıraya alınan aktarım kanalı üzerinden.  
  
 Bir kuyruktaki adresleme [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] şu deseni temel alınarak:  
  
 NET.MSMQ: / / \< *ana bilgisayar adı*> / [özel /] \< *sıra adı*>  
  
 burada:  
  
-   \<*ana bilgisayar adı*> hedef sıra barındıran bilgisayarın adıdır.  
  
-   [özel] isteğe bağlıdır. Bir özel sıra bir hedef sıra adresleme olduğunda kullanılır. Bir genel sıra gidermek için özel belirtmelisiniz değil. MSMQ yolları farklı olarak, hiçbir "$" içindeki yoktur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] URI formu.  
  
-   \<*Kuyruk adı*> sıranın adıdır. Kuyruk adı da iletiler alt kuyruğuna başvurabilir. Bu nedenle, \< *sıra adı*> = \< *kuyruk adı*> [; *alt queue adı*].  
  
 Example1: özel bir sıra bilgisayar abc atadatum.com üzerinde barındırılan PurchaseOrders adreslemek için URI net.msmq://abc.adatum.com/private/PurchaseOrders olacaktır.  
  
 Example2: bir genel sıra bilgisayar def atadatum.com üzerinde barındırılan AccountsPayable adreslemek için URI net.msmq://def.adatum.com/AccountsPayable olacaktır.  
  
 Sıra adresi dinleme URI olarak dinleyicisi tarafından alınan iletileri okumak için kullanılır. Diğer bir deyişle, sıra adres için dinleme bağlantı noktası TCP yuvası eşdeğerdir.  
  
 Bir kuyruktaki iletileri okur bir uç nokta ServiceHost açılırken daha önce belirtilen aynı düzeni kullanarak sıraya adresini belirtmeniz gerekir. Örnekler için bkz: [ağ MSMQ bağlama](../../../../docs/framework/wcf/samples/net-msmq-binding.md) ve [Message Queuing tümleştirme bağlama örnekleri](http://msdn.microsoft.com/library/997d11cb-f2c5-4ba0-9209-92843d4d0e1a).  
  
### <a name="multiple-contracts-in-a-queue"></a>Bir kuyruktaki birden fazla sözleşme  
 Sıradaki iletileri farklı sözleşmeleri uygulayabilirsiniz. Bu durumda, aşağıdakilerden birini başarıyla okumak ve tüm iletileri işlemek için true değerine ayarlandığını önemlidir:  
  
-   Tüm sözleşmeler uygulayan bir hizmet için bir uç nokta belirtin. Bu önerilen yaklaşımdır.  
  
-   Birden çok uç nokta farklı Sözleşmelerle belirtin, ancak tüm uç noktaları aynı kullandığınızdan emin olun `NetMsmqBinding` nesnesi. ServiceModel dağıtırken mantık sonunda farklı uç noktalar sözleşmesine bağlı olarak iletileri çoğullamasını gönderme için taşıyıcı kanal dışında iletilerini okuyan bir ileti Pompalama kullanır. İleti Pompalama için dinleme URI/bağlama çifti oluşturulur. Sıra adresi dinleme URI olarak sıraya alınan dinleyicisi tarafından kullanılır. Tek ileti Pompalama iletisini okuyun ve ilgili Uç noktalara çoğullamasını kullanılır aynı bağlama nesnesi sağlar tüm uç noktaları kullanma sahip sözleşmeyi temel alarak.  
  
### <a name="srmp-messaging"></a>SRMP Mesajlaşma  
 Daha önce ele alındığı gibi SRMP protokolünü kuyruktan kuyruğa aktarımları için kullanabilirsiniz. Bu, genellikle bir HTTP taşıması iletileri iletim sırası ve hedef sırası arasında aktardığında kullanılır.  
  
 SRMP aktarım protokolünü kullanmak için daha önce belirtildiği gibi net.msmq URI şeması'nı kullanarak iletileri adres ve SRMP veya güvenli SRMP de seçimiyle belirtin `QueueTransferProtocol` özelliği `NetMsmqBinding`.  
  
 Belirtme `QueueTransferProtocol` yalnızca gönderme özelliği bir özelliktir. Bu sıra hangi tür aktarım protokolünü kullanmak için istemci tarafından göstergesidir.  
  
### <a name="using-active-directory"></a>Active Directory kullanarak  
 MSMQ Active Directory ile tümleştirme için destek sunar. MSMQ Active Directory Tümleştirme ile yüklendiğinde, makineyi bir Windows etki alanının parçası olması gerekir. Active Directory bulma kuyruklarında yayımlamak için kullanılır; Bu tür sıralar adlı *genel sıraların*. Bir kuyruk işleme, sıra Active Directory kullanılarak çözülebilir. Bu, etki alanı adı sistemi (DNS) bir ağ adıyla IP adresini çözümlemek için nasıl kullanıldığı için benzer. `UseActiveDirectory` Özelliğinde `NetMsmqBinding` sıranın URI çözümlemek için sıraya alınan kanalı Active Directory kullanan olup olmadığını belirten bir Boole değeri değil. Varsayılan olarak ayarlanır `false`. Varsa `UseActiveDirectory` özelliği ayarlanmış `true`, sıraya alınan kanal URI net.msmq:// biçim adına dönüştürmek için Active Directory kullanır.  
  
 `UseActiveDirectory` Özelliği yalnızca ileti gönderirken sıranın adresini çözümlemek için kullanıldığından, ileti gönderen istemci için anlamlı.  
  
### <a name="mapping-netmsmq-uri-to-message-queuing-format-names"></a>Message Queuing biçim adlarının net.msmq URI eşleme  
 Sıraya alınan kanal MSMQ biçim adlarının kanala için sağlanan net.msmq URI adı eşleme işler. Aşağıdaki tabloda, aralarında eşleştirmek için kullanılan kuralları özetler.  
  
|WCF URI tabanlı sıra adresi|Active Directory özelliğini kullanın|Sıra Aktarım Protokolü özelliği|Sonuçta elde edilen MSMQ biçim adları|  
|----------------------------------|-----------------------------------|--------------------------------------|---------------------------------|  
|NET.MSMQ://\<makine adı >/özel/abc|False (varsayılan)|Yerel (varsayılan)|DOĞRUDAN OS:machine =-name\private$ \abc|  
|NET.MSMQ://\<makine adı >/özel/abc|False|SRMP|DOĞRUDAN =http://machine/msmq/private$/ abc|  
|NET.MSMQ://\<makine adı >/özel/abc|Doğru|Yerel|Ortak GUID bazı (sıranın GUID) =|  
  
### <a name="reading-messages-from-the-dead-letter-queue-or-the-poison-message-queue"></a>Sahipsiz sıra veya Poison iletiyi kuyruktan iletileri okuma  
 Hedef sıra sırasına olan poison iletiyi kuyruktan iletileri okumak için açık `ServiceHost` iletiler alt kuyruğuna adresine sahip.  
  
 Örnek: yerel makine PurchaseOrders özel sıradan poison ileti kuyruğunu okur bir hizmet net.msmq://localhost/private/PurchaseOrders;poison adresi.  
  
 Sistem işlem teslim edilemeyen kuyruktan iletileri okumak için URI biçiminde olmalıdır: net.msmq://localhost/system$; DeadXact.  
  
 Sistem işlem teslim edilemeyen kuyruktan iletileri okumak için URI biçiminde olmalıdır: net.msmq://localhost/system$; geçersiz.  
  
 Özel bir sahipsiz sırayı kullanırken, sahipsiz sırayı yerel bilgisayarda bulunmalıdır unutmayın. Bu nedenle, eski ileti sırası için URI forma sınırlıdır:  
  
 NET.MSMQ: //localhost/ [özel /] \< *özel-atılacak-letter-sıra-name*>.  
  
 A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet doğrular aldığı tüm iletileri dinleme üzerinde belirli bir sıraya ele alınan. İletinin hedef sıraya içinde bulunan sıra eşleşmiyorsa, hizmet ileti işlemez. Bu teslim edilemeyen sırasındaki herhangi bir iletisi başka bir yerde teslim gerektiği bulunduğundan atılacak için dinleme Hizmetleri çözülmesi gereken bir sorundur. Sahipsiz Sıra ya da zararlı bir kuyruktan iletileri okumak için bir `ServiceBehavior` ile <xref:System.ServiceModel.AddressFilterMode.Any> parametresi kullanılmalıdır. Bir örnek için bkz: [teslim edilemeyen iletiler sırası](../../../../docs/framework/wcf/samples/dead-letter-queues.md).  
  
## <a name="msmqintegrationbinding-and-service-addressing"></a>MsmqIntegrationBinding ve hizmet adresleme  
 `MsmqIntegrationBinding` Geleneksel MSMQ uygulamaları ile iletişim için kullanılır. Varolan bir MSMQ uygulaması ile birlikte çalışma kolaylaştırmak için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] destekler yalnızca biçim adı adresleme. Bu nedenle, bu bağlama kullanılarak gönderilen iletileri için kullanılacak URI düzeni uygun olmalıdır:  
  
 MSMQ.FormatName:\<*MSMQ biçim adı*>>  
  
 MSMQ biçim adı MSMQ tarafından belirtilen biçimde olduğundan [hakkında Message Queuing](http://go.microsoft.com/fwlink/?LinkId=94837).  
  
 Yalnızca doğrudan biçim adları ve ortak ve özel biçim adları kullanabileceğinizi unutmayın (Active Directory Tümleştirme gerektirir) iletileri kullanarak bir sıra alırken `MsmqIntegrationBinding`. Ancak, doğrudan biçim adları kullanmanız önerilir. Örneğin, [!INCLUDE[wv](../../../../includes/wv-md.md)], başka bir biçim adını kullanarak neden olan bir hata yalnızca doğrudan biçim adıyla açılabilen bir alt sırayı açmak sistem çalışır olduğundan.  
  
 SRMP kullanarak belirtirken `MsmqIntegrationBinding`, /msmq/ göndermeyi ile Internet Information Services (IIS) yardımcı olmak için doğrudan biçim adını eklemek için gereksinimi yoktur. Örneğin: abc SRMP kullanarak protokolü, yerine doğrudan bir sıra belirtirken =http://adatum.com/msmq/private$/ abc, kullanmanız gereken doğrudan =http://adatum.com/private$/ abc.  
  
 Net.msmq:// adresleme kullanamayacağınızı unutmayın `MsmqIntegrationBinding`. Çünkü `MsmqIntegrationBinding` serbest biçimli MSMQ adı biçimi adresleme, destekler kullanabileceğiniz bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] MSMQ çok noktaya yayın ve dağıtım listesi özellikleri kullanmak için bu bağlamayı kullanan hizmet. Yöntemi bir özel durum belirtme `CustomDeadLetterQueue` kullanırken `MsmqIntegrationBinding`. Bunu nasıl olduğu için benzer form net.msmq:// olmalıdır kullanarak belirtilen `NetMsmqBinding`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kuyruğa Alınan Bir Uygulamayı Web'de Barındırma](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md)
