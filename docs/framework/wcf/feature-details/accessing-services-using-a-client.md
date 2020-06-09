---
title: İstemci Kullanarak Hizmetlere Erişme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c8329832-bf66-4064-9034-bf39f153fc2d
ms.openlocfilehash: 001f30d7a0dde952a7d18bfbc50f2c3622287406
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576557"
---
# <a name="accessing-services-using-a-client"></a>İstemci Kullanarak Hizmetlere Erişme
İstemci uygulamaları, hizmetlerle iletişim kurmak için WCF istemcisi veya kanal nesneleri oluşturmalı, yapılandırmalıdır ve kullanmalıdır. [WCF Istemci genel bakış](../wcf-client-overview.md) konusu, temel istemci ve kanal nesneleri oluşturma ve bunları kullanma konularında yer alan nesneler ve adımlara genel bir bakış sağlar.  
  
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
> Hatalı oturumsuz kanalların açıkça algılanmasıyla çalışılması, size bildirimde bulunulduğundan oturum uygulamaya bağlı olarak, genellikle yararlı değildir. Örneğin, <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType> (güvenilir oturum devre dışı bırakılmış), TCP bağlantısının oturumunu yüzey halinde sunırsanız, <xref:System.ServiceModel.ICommunicationObject.Faulted?displayProperty=nameWithType> hizmette veya istemcide olay dinlerken bir ağ arızası durumunda hızlı bir şekilde bildirilmesini sağlayabilirsiniz. Ancak, güvenilir oturumlar (etkin olduğu bağlamalar tarafından oluşturulan <xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType> ), küçük ağ arızalarındaki hizmetleri tahmin etmek için tasarlanmıştır. Oturum makul bir süre içinde yeniden kurulmuyorsa, güvenilir oturumlar için yapılandırılmış aynı bağlama — daha uzun bir süre boyunca kesilene kadar hata olmayabilir.  
  
 Sistem tarafından sunulan bağlamaların (kanalları uygulama katmanında kullanıma sunma) çoğu oturumları varsayılan olarak kullanır, ancak yapmaz <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> . Daha fazla bilgi için bkz. [oturumları kullanma](../using-sessions.md).  
  
### <a name="the-proper-use-of-sessions"></a>Oturumların uygun kullanımı  
 Oturumlar, tüm ileti alışverişi tamamlandı ve her iki taraf da başarılı olarak kabul edildiğinde bilmemiz için bir yol sağlar. Çağıran bir uygulamanın kanalı açması, onu kullanması ve kanalı bir try bloğu içinde kapatması önerilir. Bir oturum kanalı açıksa ve <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType> yöntemi bir kez çağrılırsa ve bu çağrı başarıyla döndürülürse, oturum başarılı olmuştur. Bu durumda başarılı oldu, tüm teslimin belirtilen bağlamanın karşılandığından ve diğer tarafın çağrılmadan önce kanalda çağırmadığından emin olduğu anlamına gelir <xref:System.ServiceModel.ICommunicationObject.Abort%2A?displayProperty=nameWithType> <xref:System.ServiceModel.ICommunicationObject.Close%2A> .  
  
 Aşağıdaki bölümde bu istemci yaklaşımına bir örnek verilmiştir.  
  
### <a name="handling-exceptions"></a>Özel Durumları İşleme  
 İstemci uygulamalarında özel durumların işlenmesi basittir. Bir kanal açılırsa, kullanıldığında ve bir try bloğu içinde kapatılırsa, bir özel durum oluşturulmadığı takdirde konuşma başarılı olur. Genellikle, bir özel durum oluşturulursa, konuşma iptal edilir.  
  
> [!NOTE]
> `using`Deyimin kullanımı ( `Using` Visual Basic) önerilmez. Bunun nedeni, `using` deyimin sonunun hakkında bilmeniz gerekebilecek diğer özel durumları maskeleyebilir. Daha fazla bilgi için bkz. [Close ve Abort kullanarak WCF istemci kaynaklarını serbest bırakma](../samples/use-close-abort-release-wcf-client-resources.md).  
  
 Aşağıdaki kod örneği, ifadesiyle değil, bir try/catch bloğu kullanarak önerilen istemci modelini gösterir `using` .  
  
 [!code-csharp[FaultContractAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/client.cs#3)]
 [!code-vb[FaultContractAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/client.vb#3)]  
  
> [!NOTE]
> Özelliğin değerinin denetlenmesi <xref:System.ServiceModel.ICommunicationObject.State%2A?displayProperty=nameWithType> bir yarış durumudur ve bir kanalın yeniden kullanılıp kullanılmayacağını veya kapatılmasını belirlemekte önerilmez.  
  
 Veri birimi kanalları kapandığında özel durumlar gerçekleşse bile hiçbir zaman hata vermez. Ayrıca, güvenli bir konuşma kullanarak kimlik doğrulaması başarısız olan ve çift yönlü olmayan istemciler genellikle bir oluşturur <xref:System.ServiceModel.Security.MessageSecurityException?displayProperty=nameWithType> . Ancak güvenli bir konuşma kullanan çift yönlü istemci kimlik doğrulaması yapamazsa, istemci <xref:System.TimeoutException?displayProperty=nameWithType> bunun yerine bir alır.  
  
 Uygulama düzeyinde hata bilgileriyle çalışma hakkında daha ayrıntılı bilgi için bkz. [sözleşmeleri ve Hizmetleri kullanarak hataları belirtme ve işleme](../specifying-and-handling-faults-in-contracts-and-services.md). [Beklenen özel durumlar](../samples/expected-exceptions.md) beklenen özel durumları açıklar ve bunların nasıl işleneceğini gösterir. Kanalları geliştirirken hataların nasıl işleneceği hakkında daha fazla bilgi için bkz. [özel durumları ve hataları işleme](../extending/handling-exceptions-and-faults.md).  
  
### <a name="client-blocking-and-performance"></a>İstemci engelleme ve performans  
 Bir uygulama bir istek-yanıt işlemini zaman uyumlu olarak çağırdığında, istemci, dönüş değeri alınana veya bir özel durum (örneğin bir <xref:System.TimeoutException?displayProperty=nameWithType> ) atılana kadar engeller. Bu davranış, yerel davranışa benzer. Bir uygulama bir WCF istemci nesnesi veya kanalında eşzamanlı olarak bir işlem çağırdığında, istemci kanal katmanı verileri ağa yazana veya bir özel durum oluşturuluncaya kadar döndürmez. Tek yönlü ileti değişimi deseninin (bir işlem olarak ayarlanmış bir işlem olarak işaretleyerek belirtilen <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> `true` ) bazı istemcilerin daha hızlı yanıt verebilmesini sağlarken, bağlamaya ve bu iletilerin zaten gönderilmiş olmasına bağlı olarak tek yönlü işlemler de engelleyebilirler. Tek yönlü işlemler yalnızca ileti alışverişi hakkında, daha az ve daha az değildir. Daha fazla bilgi için bkz. [tek yönlü hizmetler](one-way-services.md).  
  
 Büyük veri öbekleri ileti değişimi düzeniyle ne fark etmeksizin istemci işlemesini yavaşlatabilir. Bu sorunları nasıl işleyeceğinizi anlamak için bkz. [büyük veri ve akış](large-data-and-streaming.md).  
  
 Bir işlem tamamlandığında uygulamanız daha fazla iş yapabilmelidir, WCF istemcinizin uyguladığı hizmet sözleşmesi arabiriminde zaman uyumsuz bir yöntem çifti oluşturmanız gerekir. Bunu yapmanın en kolay yolu, `/async` [ServiceModel meta veri yardımcı programı aracında (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)anahtarı kullanmaktır. Bir örnek için bkz. [nasıl yapılır: hizmet Işlemlerini zaman uyumsuz olarak çağırma](how-to-call-wcf-service-operations-asynchronously.md).  
  
 İstemci performansını artırma hakkında daha fazla bilgi için bkz. [Orta katman Istemci uygulamaları](middle-tier-client-applications.md).  
  
### <a name="enabling-the-user-to-select-credentials-dynamically"></a>Kullanıcının kimlik bilgilerini dinamik olarak seçmesini sağlama  
 <xref:System.ServiceModel.Dispatcher.IInteractiveChannelInitializer>Arabirim, uygulamanın, zaman aşımı zamanlayıcılar başlamadan önce bir kanalın oluşturulduğu kimlik bilgilerini seçmesini sağlayan bir kullanıcı arabirimi görüntülemesine olanak sağlar.  
  
 Uygulama geliştiricileri, ekleneni <xref:System.ServiceModel.Dispatcher.IInteractiveChannelInitializer> iki şekilde kullanabilir. İstemci uygulaması, <xref:System.ServiceModel.ClientBase%601.DisplayInitializationUI%2A?displayProperty=nameWithType> <xref:System.ServiceModel.IClientChannel.DisplayInitializationUI%2A?displayProperty=nameWithType> kanalı açmadan ( *Açık* yaklaşım) veya ilk işlemi ( *örtük* yaklaşım) çağırmadan önce ya da (ya da bir zaman uyumsuz sürüm) çağırabilir.  
  
 Örtük yaklaşım kullanılıyorsa, uygulamanın bir veya uzantısında ilk işlemi çağırması gerekir <xref:System.ServiceModel.ClientBase%601> <xref:System.ServiceModel.IClientChannel> . İlk işlem dışında bir şey çağırırsa, bir özel durum oluşturulur.  
  
 Açık yaklaşımı kullanıyorsanız, uygulamanın sırasıyla aşağıdaki adımları gerçekleştirmesi gerekir:  
  
1. Ya da <xref:System.ServiceModel.ClientBase%601.DisplayInitializationUI%2A?displayProperty=nameWithType> <xref:System.ServiceModel.IClientChannel.DisplayInitializationUI%2A?displayProperty=nameWithType> (ya da zaman uyumsuz bir sürüm) çağırın.  
  
2. Başlatıcılar döndürüldüğünde, <xref:System.ServiceModel.ICommunicationObject.Open%2A> <xref:System.ServiceModel.IClientChannel> nesne üzerinde veya <xref:System.ServiceModel.IClientChannel> özelliğinden döndürülen nesnede yöntemi çağırın <xref:System.ServiceModel.ClientBase%601.InnerChannel%2A?displayProperty=nameWithType> .  
  
3. Çağrı işlemleri.  
  
 Üretim kalitesi uygulamalarının, açık yaklaşımı benimseerek Kullanıcı arabirimi sürecini denetlemekte olması önerilir.  
  
 Örtük yaklaşımı kullanan uygulamalar Kullanıcı arabirimi başlatıcıları çağırır, ancak uygulamanın kullanıcısı bağlamanın zaman aşımı süresi içinde yanıt vermezse, Kullanıcı arabirimi geri döndüğünde bir özel durum oluşturulur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çift Yönlü Hizmetler](duplex-services.md)
- [Nasıl yapılır: Tek Yönlü ve İstek-Yanıt Sözleşmeleriyle Hizmetlere Erişme](how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)
- [Nasıl yapılır: Çift Yönlü Sözleşme ile Hizmetlere Erişme](how-to-access-services-with-a-duplex-contract.md)
- [Nasıl yapılır: WSE 3.0 Hizmetine Erişme](how-to-access-a-wse-3-0-service-with-a-wcf-client.md)
- [Nasıl yapılır: ChannelFactory Kullanma](how-to-use-the-channelfactory.md)
- [Nasıl yapılır: Hizmet İşlemlerini Zaman Uyumsuz Olarak Çağırma](how-to-call-wcf-service-operations-asynchronously.md)
- [Orta Katman İstemci Uygulamaları](middle-tier-client-applications.md)
