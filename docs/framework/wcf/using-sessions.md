---
title: Oturumları Kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sessions [WCF]
ms.assetid: 864ba12f-3331-4359-a359-6d6d387f1035
ms.openlocfilehash: a879e90aeab7b40529df1f1a60cd1f879c39720a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143180"
---
# <a name="using-sessions"></a>Oturumları Kullanma
Windows Communication Foundation (WCF) uygulamalarında, *oturum* bir ileti grubunu bir konuşmayla ilişkilendirer. WCF oturumları, ASP.NET uygulamalarında kullanılabilen oturum nesnesinden farklıdır, farklı davranışları destekler ve farklı şekillerde denetlenir. Bu konu, oturumların WCF uygulamalarında etkinleştirmek özellikleri ve bunları nasıl kullanılacağını açıklar.  
  
## <a name="sessions-in-windows-communication-foundation-applications"></a>Windows Communication Foundation Applications Oturumları  
 Bir hizmet sözleşmesi bir oturum gerektirdiğini belirttiğinde, söz konusu sözleşme tüm çağrıların (diğer bir şekilde çağrıları destekleyen temel ileti alışverişi) aynı konuşmanın bir parçası olması gerektiğini belirtir. Bir sözleşme, oturumlara izin verdiğini, ancak bir oturum gerektirmediğini belirtirse, istemciler bağlanabilir ve bir oturum kurabilir veya oturum oluşturamaz. Oturum sona erer ve aynı kanalüzerinden bir ileti gönderilirse bir özel durum atılır.  
  
 WCF oturumları aşağıdaki temel kavramsal özelliklere sahiptir:  
  
- Bunlar açıkça başlatılır ve arama uygulaması (WCF istemcisi) tarafından sonlandırılır.  
  
- Oturum sırasında iletilen iletiler, alındıkları sırayla işlenir.  
  
- Oturumlar, bir ileti grubunu bir konuşmaya ilişkilendirer. Farklı türde korelasyon mümkündür. Örneğin, oturum tabanlı bir kanal paylaşılan ağ bağlantısına dayalı iletileri ilişkilendirebilirken, başka bir oturum tabanlı kanal ileti gövdesindeki paylaşılan etikete dayalı iletileri ilişkilendirebilir. Oturumdan türetilebilen özellikler bağıntının doğasına bağlıdır.  
  
- WCF oturumuyla ilişkili genel bir veri deposu yoktur.  
  
 ASP.NET uygulamalarda <xref:System.Web.SessionState.HttpSessionState?displayProperty=nameWithType> sınıfa ve sağladığı işlevselliği biliyorsanız, bu tür oturumlarla WCF oturumları arasındaki aşağıdaki farkları fark edebilirsiniz:  
  
- ASP.NET oturumları her zaman sunucu tarafından başlatılır.  
  
- ASP.NET oturumlar dolaylı olarak sırasızdır.  
  
- ASP.NET oturumları istekler arasında genel bir veri depolama mekanizması sağlar.  
  
 Bu konu açıklar:  
  
- Hizmet modeli katmanında oturum tabanlı bağlamaları kullanırken varsayılan yürütme davranışı.  
  
- WCF oturum tabanlı, sistem tarafından sağlanan bağlamaların sağladığı özellik türleri.  
  
- Oturum gereksinimini bildiren bir sözleşme oluşturma.  
  
- Oturumun oluşturulması ve sonlandırılması ile oturumun hizmet örneğiyle ilişkisinin nasıl anlaşılır ve denetler.  
  
## <a name="default-execution-behavior-using-sessions"></a>Oturumları Kullanarak Varsayılan Yürütme Davranışı  
 Oturum başlatmaya çalışan bağlayıcıya oturum *tabanlı* bağlama denir. Hizmet sözleşmeleri, <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> özelliği hizmet sözleşmesi arabiriminde (veya sınıf) numaralandırma değerlerinden <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> birine ayarlayarak oturum tabanlı bağlamalar gerektirdiğini, izin verdiklerini veya reddetmelerini belirtir. Varsayılan olarak, bu özelliğin <xref:System.ServiceModel.SessionMode.Allowed>değeri , yani bir istemci WCF hizmeti uygulaması yla oturum tabanlı bir bağlama kullanırsa, hizmet sağlanan oturumu kurar ve kullanır.  
  
 Bir WCF hizmeti istemci oturumunu kabul ettiğinde, aşağıdaki özellikler varsayılan olarak etkinleştirilir:  
  
1. WCF istemci nesnesi arasındaki tüm aramalar aynı hizmet örneği tarafından işlenir.  
  
2. Farklı oturum tabanlı bağlamalar ek özellikler sağlar.  
  
## <a name="system-provided-session-types"></a>Sistem Destekli Oturum Türleri  
 Oturum tabanlı bağlama, belirli bir oturumla hizmet örneğinin varsayılan ilişkisini destekler. Ancak, farklı oturum tabanlı bağlamalar, daha önce açıklanan oturum tabanlı instancing denetimini etkinleştirmenin yanı sıra farklı özellikleri destekler.  
  
 WCF aşağıdaki oturum tabanlı uygulama davranışı türlerini sağlar:  
  
- Destek, <xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType> iletişimin her iki ucunun da belirli bir güvenli görüşme üzerinde anlaştığı güvenlik tabanlı oturumları destekler. Daha fazla bilgi için [Bkz. Güvenlik Hizmetleri.](securing-services.md) Örneğin, varsayılan <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType> olarak, hem güvenlik oturumları hem de güvenilir oturumlar için destek içeren bağlama, yalnızca iletileri şifreleyen ve dijital olarak imzalayan güvenli bir oturum kullanır.  
  
- Bağlama, <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType> tüm iletilerin soket düzeyindeki bağlantıyla ilişkilendirilmesini sağlamak için TCP/IP tabanlı oturumları destekler.  
  
- WS-ReliableMessaging belirtimini uygulayan <xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType> öğe, iletilerin sırayla ve tam olarak bir kez teslim edilecek şekilde yapılandırılabildiği güvenilir oturumlar için destek sağlayarak, iletilerin konuşma sırasında birden fazla düğüm arasında seyahat ederken bile iletilerin alınmasını sağlar. Daha fazla bilgi için [Güvenilir Oturumlar'a](./feature-details/reliable-sessions.md)bakın.  
  
- Bağlama, <xref:System.ServiceModel.NetMsmqBinding?displayProperty=nameWithType> MSMQ datagram oturumları sağlar. Daha fazla bilgi için [WCF'deki Kuyruklar'a](./feature-details/queues-in-wcf.md)bakın.  
  
 Özelliğiayarlamak, <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> sözleşmenin gerektirdiği oturum türünü belirtmez, yalnızca bir oturum gerektirdiğini belirtir.  
  
## <a name="creating-a-contract-that-requires-a-session"></a>Oturum Gerektiren Bir Sözleşme Oluşturma  
 Oturum gerektiren bir sözleşme oluşturmak, hizmet sözleşmesinin bildirdiği işlem grubunun hepsinin aynı oturum içinde yürütülmesi ve iletilerin sırayla teslim edilmesi gerektiğini belirtir. Bir hizmet sözleşmesinin gerektirdiği oturum desteği düzeyini <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> belirlemek için, hizmet sözleşmesi arabiriminizdeki <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> veya sınıfınızdaki özelliği, sözleşmenin olup olmadığını belirtmek için numaralandırmanın değerine ayarlayın:  
  
- Bir oturum gerektirir.  
  
- İstemci bir oturum kurmak için izin verir.  
  
- Oturumu yasaklar.  
  
 <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> Ancak özelliği ayarlamak, sözleşmenin gerektirdiği oturum tabanlı davranış türünü belirtmez. WCF'ye, hizmet için yapılandırılan bağlamanın (iletişim kanalını oluşturan) bir hizmeti uygularken bir oturum oluşturduğunu, oluşturmadığını veya oluşturabileceğini çalışma zamanında onaylamasını emreder. Yine, bağlama, bu gereksinimi seçtiği oturum tabanlı davranış türüyle (güvenlik, aktarım, güvenilir veya bazı kombinasyonlar) karşılayabilir. Tam davranış seçilen değere <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> bağlıdır. Hizmetin yapılandırılan bağlama değerine uygun <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A>değilse, bir özel durum atılır. Bağlamalar ve destek oturumları oluşturduğu kanallar oturum tabanlı olduğu söyleniyor.  
  
 Aşağıdaki hizmet sözleşmesi, oturum daki tüm `ICalculatorSession` işlemlerin bir oturum içinde değiştirilmesi gerektiğini belirtir. İşlemlerin hiçbiri `Equals` yöntem dışında arayana bir değer döndürür. Ancak, `Equals` yöntem hiçbir parametre almaz ve bu nedenle, yalnızca verilerin zaten diğer işlemlere geçirildiği bir oturum içinde sıfır olmayan bir değer döndürebilir. Bu sözleşme düzgün çalışması için bir oturum gerektirir. Belirli bir istemciyle ilişkili bir oturum olmadan, hizmet örneğinin bu istemcinin hangi önceki verileri gönderdiğini bilmenin bir yolu yoktur.  
  
 [!code-csharp[S_Service_Session#1](../../../samples/snippets/csharp/VS_Snippets_CFX/s_service_session/cs/service.cs#1)]
 [!code-vb[S_Service_Session#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_service_session/vb/service.vb#1)]  
  
 Bir hizmet oturuma izin veriyorsa, istemci oturum uyguluyorsa bir oturum kurulur ve kullanılır; aksi takdirde oturum kurulamaz.  
  
## <a name="sessions-and-service-instances"></a>Oturumlar ve Hizmet Örnekleri  
 WCF'de varsayılan instancing davranışını kullanırsanız, WCF istemci nesnesi arasındaki tüm çağrılar aynı hizmet örneği tarafından işlenir. Bu nedenle, uygulama düzeyinde, bir oturumu yerel arama davranışına benzer uygulama davranışını etkinleştirmek olarak düşünebilirsiniz. Örneğin, yerel bir nesne oluşturduğunuzda:  
  
- Bir yapıcı denir.  
  
- WCF istemci nesnesi başvurusuna yapılan sonraki tüm aramalar aynı nesne örneği tarafından işlenir.  
  
- Nesne başvurusu yok edildiğinde bir yıkıcı çağrılır.  
  
 Varsayılan hizmet örneği davranışı kullanıldığı sürece, oturumlar istemciler ve hizmetler arasında benzer bir davranışı etkinleştirin. Bir hizmet sözleşmesi oturumları gerektiriyor veya destekliyorsa, bir veya daha fazla sözleşme işlemi, <xref:System.ServiceModel.OperationContractAttribute.IsInitiating%2A> <xref:System.ServiceModel.OperationContractAttribute.IsTerminating%2A> bir oturumu ve özellikleri ayarlayarak oturumu başlatmak veya sonlandırmaolarak işaretlenebilir.  
  
 *Başlatma işlemleri,* yeni bir oturumun ilk işlemi olarak adlandırılması gereken işlemlerdir. Başlatmama işlemleri yalnızca en az bir başlatma işlemi çağrıldıktan sonra çağrılabilir. Bu nedenle, hizmet örneğinin başına uygun istemcilerden giriş almak üzere tasarlanmış başlatma işlemleri bildirerek hizmetiniz için bir tür oturum oluşturucu oluşturabilirsiniz. (Durum, ancak, hizmet nesnesi değil, oturum ile ilişkilidir.)  
  
 *Sonlandırma işlemleri*, tersine, varolan bir oturumdaki son ileti olarak çağrılması gereken işlemlerdir. Varsayılan durumda, WCF hizmet nesnesini ve bağlamını, hizmetin ilişkili olduğu oturum kapatıldıktan sonra geri dönüştürür. Bu nedenle, hizmet örneğinin sonuna uygun bir işlevi gerçekleştirmek üzere tasarlanmış sonlandırıcı işlemleri bildirerek bir tür yıkıcı oluşturabilirsiniz.  
  
> [!NOTE]
> Varsayılan davranış yerel yapıcılar ve yıkıcılar için bir benzerlik taşısa da, sadece bir benzerlik. Herhangi bir WCF hizmet işlemi, başlatma veya sonlandırma işlemi olabilir veya her ikisi de aynı anda olabilir. Buna ek olarak, varsayılan durumda, başlatma işlemleri herhangi bir sırada herhangi bir sayıda çağrılabilir; <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> (nesneyi manipüle ederek) hizmet örneğinin ömrünü açıkça denetlemediğiniz sürece, oturum oluşturulduktan ve bir örnekle ilişkilendirildikten sonra ek oturumlar oluşturulmaz. Son olarak, durum hizmet nesnesi ile değil, oturum ile ilişkilidir.  
  
 Örneğin, önceki `ICalculatorSession` örnekte kullanılan sözleşme, WCF istemci nesnesinin `Clear` önce işlemi başka bir işlemden önce çağırmasını ve bu WCF `Equals` istemci nesnesi ile oturumun işlemi çağırdığında sona erdirmesini gerektirir. Aşağıdaki kod örneği, bu gereksinimleri zorlayan bir sözleşme gösterir. `Clear`oturumu başlatmak için önce çağrılması gerekir ve `Equals` bu oturum çağrıldığında sona erer.  
  
 [!code-csharp[SCA.IsInitiatingIsTerminating#1](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.isinitiatingisterminating/cs/service.cs#1)]
 [!code-vb[SCA.IsInitiatingIsTerminating#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.isinitiatingisterminating/vb/service.vb#1)]  
  
 Hizmetler istemcilerle oturum başlatmaz. WCF istemci uygulamalarında, oturum tabanlı kanalın ömrü ile oturumun ömrü arasında doğrudan bir ilişki vardır. Bu nedenle, istemciler yeni oturum tabanlı kanallar oluşturarak yeni oturumlar oluşturur ve oturum tabanlı kanalları incelikle kapatarak varolan oturumları yıkar. İstemci aşağıdakilerden birini arayarak bir hizmet bitiş noktası ile bir oturum başlatır:  
  
- <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType>kanalda bir çağrı ile <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>döndürülen .  
  
- <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType>[ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)tarafından oluşturulan WCF istemci nesnesinde.  
  
- WCF istemci nesnesi (varsayılan olarak, tüm işlemler başlatılıyor) her iki türde bir başlatma işlemi. İlk işlem çağrıldığında, WCF istemci nesnesi kanalı otomatik olarak açar ve bir oturum başlatır.  
  
 Genellikle bir istemci aşağıdakilerden birini arayarak bir hizmet bitiş noktası ile oturumu sona erdirer:  
  
- <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType>kanalda bir çağrı ile <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>döndürülen .  
  
- <xref:System.ServiceModel.ClientBase%601.Close%2A?displayProperty=nameWithType>Svcutil.exe tarafından oluşturulan WCF istemci nesnesi üzerinde.  
  
- WCF istemci nesnesi türünde sonlandırıcı bir işlem (varsayılan olarak, hiçbir işlem sona erdirmiyor; sözleşme açıkça bir sonlandırma işlemi belirtmelidir). İlk işlem çağrıldığında, WCF istemci nesnesi kanalı otomatik olarak açar ve bir oturum başlatır.  
  
 Örnekler için [bkz: Oturumlar gerektiren bir Hizmet oluşturmanın](./feature-details/how-to-create-a-service-that-requires-sessions.md) yanı sıra [Varsayılan Hizmet Davranışı](./samples/default-service-behavior.md) ve Örnekleri Ara [verme.](./samples/instancing.md)  
  
 İstemciler ve oturumlar hakkında daha fazla bilgi için [WCF İstemci Kullanarak Hizmetlere Erişim'e](./feature-details/accessing-services-using-a-client.md)bakın.  
  
## <a name="sessions-interact-with-instancecontext-settings"></a>Oturumlar ÖrnekBağlam Ayarlarıyla Etkileşimde  
 Bir sözleşmedeki <xref:System.ServiceModel.SessionMode> numaralandırma ile kanallar ve belirli <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> hizmet nesneleri arasındaki ilişkiyi kontrol eden özellik arasında bir etkileşim vardır. Daha fazla bilgi için [Oturumlar, Instancing ve Concurrency'e](./feature-details/sessions-instancing-and-concurrency.md)bakın.  
  
### <a name="sharing-instancecontext-objects"></a>Örnek Bağlam Nesnelerini Paylaşma  
 Ayrıca, bu ilişkilendirmeyi kendiniz gerçekleştirerek hangi <xref:System.ServiceModel.InstanceContext> oturum tabanlı kanalın veya çağrının hangi nesneyle ilişkili olduğunu da denetleyebilirsiniz.
  
## <a name="sessions-and-streaming"></a>Oturumlar ve Akış  
 Aktarım için büyük miktarda veri varsa, WCF'deki akış aktarım modu, iletileri bellekte tümüyle arabelleğe alma ve işleme varsayılan davranışına uygun bir alternatiftir. Oturum tabanlı bağlama yla çağrıları akışa aktarırken beklenmeyen davranışlar alabilirsiniz. Tüm akış çağrıları, kullanılan bağlama oturumları kullanmak üzere yapılandırılan olsa bile oturumları desteklemeyen tek bir kanal (datagram kanalı) üzerinden yapılır. Birden çok istemci oturum tabanlı bağlama üzerinden aynı hizmet nesnesine akış çağrıları yaparsa ve hizmet nesnesinin eşzamanlılık modu `PerSession`tek olarak ayarlanırsa ve örnek bağlam modu ayarlanırsa, tüm aramalar veri gramı kanalından geçmelidir ve bu nedenle aynı anda yalnızca bir arama işlenir. Bir veya daha fazla istemci daha sonra zaman dışarı olabilir. Bu sorunu, hizmet nesnesinin veya Concurrency'in `InstanceContextMode` `PerCall` birden çok olarak ayarlayarak çözebilirsiniz.  
  
> [!NOTE]
> Yalnızca bir "oturum" olduğundan MaxConcurrentSessions bu durumda hiçbir etkisi yoktur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.OperationContractAttribute.IsInitiating%2A>
- <xref:System.ServiceModel.OperationContractAttribute.IsTerminating%2A>
