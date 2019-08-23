---
title: İstemci Kullanarak Hizmetlere Erişme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c8329832-bf66-4064-9034-bf39f153fc2d
ms.openlocfilehash: 0923fa70907a4846924395483c86e541cd88f284
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964975"
---
# <a name="accessing-services-using-a-client"></a>İstemci Kullanarak Hizmetlere Erişme
İstemci uygulamaları, hizmetlerle iletişim kurmak için WCF istemcisi veya kanal nesneleri oluşturmalı, yapılandırmalıdır ve kullanmalıdır. [WCF Istemci genel bakış](../../../../docs/framework/wcf/wcf-client-overview.md) konusu, temel istemci ve kanal nesneleri oluşturma ve bunları kullanma konularında yer alan nesneler ve adımlara genel bir bakış sağlar.  
  
 Bu konu, senaryonuza bağlı olarak yararlı olabilecek istemci uygulamaları ve istemci ve kanal nesneleri ile ilgili bazı sorunlar hakkında ayrıntılı bilgi sağlar.  
  
## <a name="overview"></a>Genel Bakış  
 Bu konuda ile ilgili davranış ve sorunlar açıklanmaktadır:  
  
- Kanal ve oturum yaşam süreleri.  
  
- Özel durumları işleme.  
  
- Engelleme sorunlarını anlama.  
  
- Kanalları etkileşimli olarak başlatma.  
  
### <a name="channel-and-session-lifetimes"></a>Kanal ve oturum yaşam süreleri  
 Windows Communication Foundation (WCF) uygulamaları iki kanal, datagram ve oturumsuz kategori içerir.  
  
 *Veri birimi* kanalı, tüm iletilerin bağıntısız olduğu bir kanaldır. Bir veri birimi kanalı ile bir giriş veya çıkış işlemi başarısız olursa, sonraki işlem genellikle etkilenmemiştir ve aynı kanal yeniden kullanılabilir. Bu nedenle, datagram kanalları genellikle hata vermez.  
  
 Ancak *oturumsuz* kanallar, diğer uç noktayla bağlantısı olan kanallardır. Bir taraftaki oturumdaki iletiler, her zaman diğer taraftaki aynı oturumla bağıntılı. Ayrıca, bir oturumdaki her iki katılımcı da bu oturumun başarılı olarak kabul edilmesi için, konuşmaları gereksinimlerinin karşılandığını kabul etmelidir. Kabul etmiyorsanız, oturumsuz kanal hata verebilir.  
  
 İlk işlemi çağırarak istemcileri açıkça veya örtük olarak açın.  
  
> [!NOTE]
> Hatalı oturumsuz kanalların açıkça algılanmasıyla çalışılması, size bildirimde bulunulduğundan oturum uygulamaya bağlı olarak, genellikle yararlı değildir. Örneğin, (güvenilir oturum <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType> devre dışı bırakılmış), TCP bağlantısının oturumunu yüzey halinde sunırsanız, hizmette veya istemcide <xref:System.ServiceModel.ICommunicationObject.Faulted?displayProperty=nameWithType> olay dinlerken bir ağ arızası durumunda hızlı bir şekilde bildirilmesini sağlayabilirsiniz. Ancak, güvenilir oturumlar (etkin olduğu <xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType> bağlamalar tarafından oluşturulan), küçük ağ arızalarındaki hizmetleri tahmin etmek için tasarlanmıştır. Oturum makul bir süre içinde yeniden kurulmuyorsa, güvenilir oturumlar için yapılandırılmış aynı bağlama — daha uzun bir süre boyunca kesilene kadar hata olmayabilir.  
  
 Sistem tarafından sunulan bağlamaların (kanalları uygulama katmanında kullanıma sunma) çoğu oturumları varsayılan olarak kullanır, ancak <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> yapmaz. Daha fazla bilgi için bkz. [oturumları kullanma](../../../../docs/framework/wcf/using-sessions.md).  
  
### <a name="the-proper-use-of-sessions"></a>Oturumların uygun kullanımı  
 Oturumlar, tüm ileti alışverişi tamamlandı ve her iki taraf da başarılı olarak kabul edildiğinde bilmemiz için bir yol sağlar. Çağıran bir uygulamanın kanalı açması, onu kullanması ve kanalı bir try bloğu içinde kapatması önerilir. Bir oturum kanalı açıksa ve <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType> yöntemi bir kez çağrılırsa ve bu çağrı başarıyla döndürülürse, oturum başarılı olmuştur. Bu durumda başarılı oldu, tüm teslimin belirtilen bağlamanın karşılandığından ve diğer tarafın çağrılmadan <xref:System.ServiceModel.ICommunicationObject.Abort%2A?displayProperty=nameWithType> <xref:System.ServiceModel.ICommunicationObject.Close%2A>önce kanalda çağırmadığından emin olduğu anlamına gelir.  
  
 Aşağıdaki bölümde bu istemci yaklaşımına bir örnek verilmiştir.  
  
### <a name="handling-exceptions"></a>Özel Durumları İşleme  
 İstemci uygulamalarında özel durumların işlenmesi basittir. Bir kanal açılırsa, kullanıldığında ve bir try bloğu içinde kapatılırsa, bir özel durum oluşturulmadığı takdirde konuşma başarılı olur. Genellikle, bir özel durum oluşturulursa, konuşma iptal edilir.  
  
> [!NOTE]
> Deyimin kullanımı (`Using` Visual Basic) önerilmez. `using` Bunun nedeni, `using` deyimin sonunun hakkında bilmeniz gerekebilecek diğer özel durumları maskeleyebilir. Daha fazla bilgi için bkz. [Close ve Abort kullanarak WCF istemci kaynaklarını serbest bırakma](../../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md).  
  
 Aşağıdaki kod örneği, `using` ifadesiyle değil, bir try/catch bloğu kullanarak önerilen istemci modelini gösterir.  
  
 [!code-csharp[FaultContractAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/client.cs#3)]
 [!code-vb[FaultContractAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/client.vb#3)]  
  
> [!NOTE]
> <xref:System.ServiceModel.ICommunicationObject.State%2A?displayProperty=nameWithType> Özelliğin değerinin denetlenmesi bir yarış durumudur ve bir kanalın yeniden kullanılıp kullanılmayacağını veya kapatılmasını belirlemekte önerilmez.  
  
 Veri birimi kanalları kapandığında özel durumlar gerçekleşse bile hiçbir zaman hata vermez. Ayrıca, güvenli bir konuşma kullanarak kimlik doğrulaması başarısız olan ve çift yönlü olmayan istemciler genellikle bir <xref:System.ServiceModel.Security.MessageSecurityException?displayProperty=nameWithType>oluşturur. Ancak güvenli bir konuşma kullanan çift yönlü istemci kimlik doğrulaması yapamazsa, istemci bunun yerine bir <xref:System.TimeoutException?displayProperty=nameWithType> alır.  
  
 Uygulama düzeyinde hata bilgileriyle çalışma hakkında daha ayrıntılı bilgi için bkz. [sözleşmeleri ve Hizmetleri kullanarak hataları belirtme ve işleme](../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md). [Beklenen özel durumlar](../../../../docs/framework/wcf/samples/expected-exceptions.md) beklenen özel durumları açıklar ve bunların nasıl işleneceğini gösterir. Kanalları geliştirirken hataların nasıl işleneceği hakkında daha fazla bilgi için bkz. [özel durumları ve hataları işleme](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).  
  
### <a name="client-blocking-and-performance"></a>İstemci engelleme ve performans  
 Bir uygulama bir istek-yanıt işlemini zaman uyumlu olarak çağırdığında, istemci, dönüş değeri alınana veya bir özel durum (örneğin bir <xref:System.TimeoutException?displayProperty=nameWithType>) atılana kadar engeller. Bu davranış, yerel davranışa benzer. Bir uygulama bir WCF istemci nesnesi veya kanalında eşzamanlı olarak bir işlem çağırdığında, istemci kanal katmanı verileri ağa yazana veya bir özel durum oluşturuluncaya kadar döndürmez. Tek yönlü ileti değişimi deseninin (bir işlem olarak <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> `true`ayarlanmış bir işlem olarak işaretleyerek belirtilen) bazı istemcilerin daha hızlı yanıt vermesine yol açabilir ve bağlamaya bağlı olarak tek yönlü işlemler de engelleyebilirler gönderilip. Tek yönlü işlemler yalnızca ileti alışverişi hakkında, daha az ve daha az değildir. Daha fazla bilgi için bkz. [tek yönlü hizmetler](../../../../docs/framework/wcf/feature-details/one-way-services.md).  
  
 Büyük veri öbekleri ileti değişimi düzeniyle ne fark etmeksizin istemci işlemesini yavaşlatabilir. Bu sorunları nasıl işleyeceğinizi anlamak için bkz. [büyük veri ve akış](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
 Bir işlem tamamlandığında uygulamanız daha fazla iş yapabilmelidir, WCF istemcinizin uyguladığı hizmet sözleşmesi arabiriminde zaman uyumsuz bir yöntem çifti oluşturmanız gerekir. Bunu yapmanın en kolay yolu, `/async` [ServiceModel meta veri yardımcı programı aracında (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)anahtarı kullanmaktır. Bir örnek için bkz [. nasıl yapılır: Hizmet Işlemlerini zaman uyumsuz](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)olarak çağırın.  
  
 İstemci performansını artırma hakkında daha fazla bilgi için bkz. [Orta katman Istemci uygulamaları](../../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md).  
  
### <a name="enabling-the-user-to-select-credentials-dynamically"></a>Kullanıcının kimlik bilgilerini dinamik olarak seçmesini sağlama  
 <xref:System.ServiceModel.Dispatcher.IInteractiveChannelInitializer> Arabirim, uygulamanın, zaman aşımı zamanlayıcılar başlamadan önce bir kanalın oluşturulduğu kimlik bilgilerini seçmesini sağlayan bir kullanıcı arabirimi görüntülemesine olanak sağlar.  
  
 Uygulama geliştiricileri, ekleneni <xref:System.ServiceModel.Dispatcher.IInteractiveChannelInitializer> iki şekilde kullanabilir. İstemci uygulaması, kanalı açmadan ( <xref:System.ServiceModel.ClientBase%601.DisplayInitializationUI%2A?displayProperty=nameWithType> *Açık* yaklaşım) veya ilk işlemi ( *örtük* yaklaşım) çağırmadan önce ya da <xref:System.ServiceModel.IClientChannel.DisplayInitializationUI%2A?displayProperty=nameWithType> (ya da bir zaman uyumsuz sürüm) çağırabilir.  
  
 Örtük yaklaşım kullanılıyorsa, uygulamanın bir <xref:System.ServiceModel.ClientBase%601> veya <xref:System.ServiceModel.IClientChannel> uzantısında ilk işlemi çağırması gerekir. İlk işlem dışında bir şey çağırırsa, bir özel durum oluşturulur.  
  
 Açık yaklaşımı kullanıyorsanız, uygulamanın sırasıyla aşağıdaki adımları gerçekleştirmesi gerekir:  
  
1. <xref:System.ServiceModel.ClientBase%601.DisplayInitializationUI%2A?displayProperty=nameWithType> Ya<xref:System.ServiceModel.IClientChannel.DisplayInitializationUI%2A?displayProperty=nameWithType> da (ya da zaman uyumsuz bir sürüm) çağırın.  
  
2. Başlatıcılar <xref:System.ServiceModel.ICommunicationObject.Open%2A> döndürüldüğünde, <xref:System.ServiceModel.IClientChannel> nesne üzerinde veya <xref:System.ServiceModel.IClientChannel> <xref:System.ServiceModel.ClientBase%601.InnerChannel%2A?displayProperty=nameWithType> özelliğinden döndürülen nesnede yöntemi çağırın.  
  
3. Çağrı işlemleri.  
  
 Üretim kalitesi uygulamalarının, açık yaklaşımı benimseerek Kullanıcı arabirimi sürecini denetlemekte olması önerilir.  
  
 Örtük yaklaşımı kullanan uygulamalar Kullanıcı arabirimi başlatıcıları çağırır, ancak uygulamanın kullanıcısı bağlamanın zaman aşımı süresi içinde yanıt vermezse, Kullanıcı arabirimi geri döndüğünde bir özel durum oluşturulur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çift Yönlü Hizmetler](../../../../docs/framework/wcf/feature-details/duplex-services.md)
- [Nasıl yapılır: Tek yönlü ve Istek-yanıt sözleşmeleriyle hizmetlere erişin](../../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)
- [Nasıl yapılır: Çift yönlü sözleşme ile hizmetlere erişme](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)
- [Nasıl yapılır: WVA3,0 hizmetine erişme](../../../../docs/framework/wcf/feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)
- [Nasıl yapılır: ChannelFactory kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)
- [Nasıl yapılır: Hizmet Işlemlerini zaman uyumsuz olarak çağır](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)
- [Orta Katman İstemci Uygulamaları](../../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md)
