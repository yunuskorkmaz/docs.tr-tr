---
title: Oturumları Kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sessions [WCF]
ms.assetid: 864ba12f-3331-4359-a359-6d6d387f1035
ms.openlocfilehash: 671e650a494d314ec1da1957eaae91e2d1811213
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952834"
---
# <a name="using-sessions"></a>Oturumları Kullanma
Windows Communication Foundation (WCF) uygulamalarında, bir *oturum* bir ileti grubunu bir konuşmaya ilişkilendirir. WCF oturumları, ASP.NET uygulamalarında bulunan oturum nesnesinden farklıdır, farklı davranışları destekler ve farklı yollarla denetlenir. Bu konuda, oturum açma özelliklerinin WCF uygulamalarında etkinleştirilmesi ve bunların nasıl kullanılacağı açıklanmaktadır.  
  
## <a name="sessions-in-windows-communication-foundation-applications"></a>Windows Communication Foundation uygulamalardaki oturumlar  
 Bir hizmet sözleşmesi bir oturum gerektirdiğini belirttiğinde, bu sözleşme tüm çağrıların (yani, çağrıları destekleyen temel alınan ileti değişimlerinin) aynı görüşmenin parçası olması gerektiğini belirtir. Bir sözleşme, oturumlara izin verdiğini ancak bir tane gerektirmediğini belirtir, istemciler bağlanabilir ve oturum oluşturabilir ya da bir oturum oluşturmaz. Oturum sonlanıyorsa ve aynı kanaldan bir ileti gönderildiğinde bir özel durum oluşturulur.  
  
 WCF oturumları aşağıdaki ana kavramsal özelliklere sahiptir:  
  
- Bunlar, çağıran uygulama (WCF istemcisi) tarafından açıkça başlatılır ve sonlandırılır.  
  
- Bir oturum sırasında teslim edilen iletiler alındıkları sırada işlenir.  
  
- Bir ileti grubunu bir konuşmaya ilişkilendirmede oturumlar. Farklı bağıntı türleri mümkündür. Örneğin, bir oturum tabanlı kanal, bir paylaşılan ağ bağlantısına göre iletileri ilişkilendirebilir, ancak başka bir oturum tabanlı kanal ileti gövdesinde paylaşılan bir etikete göre iletileri ilişkilendirip ilişkilendiremeyebilir. Oturumdan türetilebilen özellikler, bağıntı yapısına bağlıdır.  
  
- Bir WCF oturumuyla ilişkili genel veri deposu yok.  
  
 ASP.NET uygulamalarında <xref:System.Web.SessionState.HttpSessionState?displayProperty=nameWithType> sınıfı ve sağladığı işlevselliği biliyorsanız, bu tür oturum ve WCF oturumları arasında aşağıdaki farklılıkları fark edebilirsiniz:  
  
- ASP.NET oturumları her zaman sunucu tarafından başlatılır.  
  
- ASP.NET oturumları örtük olarak sırasız değildir.  
  
- ASP.NET oturumları, istekler arasında genel bir veri depolama mekanizması sağlar.  
  
 Bu konuda aşağıdakiler açıklanmaktadır:  
  
- Hizmet modeli katmanında oturum tabanlı bağlamalar kullanılırken varsayılan yürütme davranışı.  
  
- WCF oturum tabanlı, sistem tarafından belirtilen bağlamaların sağladığı Özellik türleri.  
  
- Oturum gereksinimini bildiren bir sözleşme oluşturma.  
  
- Oturumun oluşturulması ve sonlandırılmasını ve hizmetin hizmet örneği ile ilişkisini anlama ve denetleme.  
  
## <a name="default-execution-behavior-using-sessions"></a>Oturumları kullanan varsayılan yürütme davranışı  
 Oturumu başlatmayı deneyen bir bağlamaya *oturum tabanlı* bağlama denir. Hizmet sözleşmeleri, hizmet sözleşmesi arabirimindeki (veya sınıfında) <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> özelliği <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> sabit listesi değerlerinden birine ayarlayarak, oturum tabanlı bağlamalar gerektirdiğini, bunlara izin vermenizi veya reddetmesini belirler. Varsayılan olarak, bu özelliğin <xref:System.ServiceModel.SessionMode.Allowed>değeri, bir istemci bir WCF Hizmeti uygulamasıyla oturum tabanlı bağlama kullanıyorsa, hizmet tarafından sağlanmış oturumu oluşturur ve kullanır.  
  
 Bir WCF hizmeti bir istemci oturumu kabul ettiğinde, aşağıdaki özellikler varsayılan olarak etkindir:  
  
1. WCF istemci nesnesi arasındaki tüm çağrılar aynı hizmet örneği tarafından işlenir.  
  
2. Farklı oturum tabanlı bağlamalar ek özellikler sağlar.  
  
## <a name="system-provided-session-types"></a>Sistem tarafından sağlanmış oturum türleri  
 Oturum tabanlı bağlama, belirli bir oturumla bir hizmet örneğinin varsayılan ilişkilendirmesini destekler. Ancak, farklı oturum tabanlı bağlamalar, daha önce açıklanan oturum tabanlı örnek oluşturma denetimini etkinleştirmeye ek olarak farklı özellikleri de destekler.  
  
 WCF, aşağıdaki oturum tabanlı uygulama davranışı türlerini sağlar:  
  
- , <xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType> Her iki iletişimin de belirli bir güvenli konuşmaya karşı anlaştığı güvenlik tabanlı oturumları destekler. Daha fazla bilgi için bkz. [hizmetleri güvenli hale getirme](../../../docs/framework/wcf/securing-services.md). Örneğin, <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType> hem güvenlik oturumları hem de güvenilir oturumlar için destek içeren bağlama, varsayılan olarak yalnızca iletileri şifreleyen ve dijital olarak imzalayabilen güvenli bir oturum kullanır.  
  
- Bağlama <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType> , tüm iletilerin yuva düzeyindeki bağlantıyla bağıntılı olduğundan emin olmak için TCP/IP tabanlı oturumları destekler.  
  
- WS <xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType> -ReliableMessaging belirtimini uygulayan öğesi, iletilerin sırayla teslim edileceği ve iletiler seyahat edildiğinde bile iletilerin alınmasını sağlayan güvenilir oturumlara yönelik destek sağlar. konuşma sırasında birden çok düğüm arasında. Daha fazla bilgi için bkz. [Güvenilir Oturumlar](../../../docs/framework/wcf/feature-details/reliable-sessions.md).  
  
- Bağlama <xref:System.ServiceModel.NetMsmqBinding?displayProperty=nameWithType> , MSMQ veri birimi oturumları sağlar. Daha fazla bilgi için bkz. [WCF 'de kuyruklar](../../../docs/framework/wcf/feature-details/queues-in-wcf.md).  
  
 <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> Özelliği ayarlamak, sözleşmenin gerektirdiği oturum türünü belirtmez, yalnızca bir tane gerektirir.  
  
## <a name="creating-a-contract-that-requires-a-session"></a>Oturum gerektiren bir sözleşme oluşturma  
 Oturum gerektiren bir sözleşmenin oluşturulması, hizmet sözleşmesinin bildirdiği işlem grubunun tümünün aynı oturum içinde yürütülmesi ve iletilerin sırayla teslim edilmesi gerektiğini belirtir. Bir hizmet sözleşmesinin gerektirdiği oturum desteğinin düzeyini belirlemek için, hizmet sözleşmesi arabiriminizdeki veya <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> sınıfınızın özelliğini, sözleşmenin değerini belirtmek için <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> numaralandırmanın değerine ayarlayın:  
  
- Bir oturum gerektirir.  
  
- Bir istemcinin oturum kurmasını sağlar.  
  
- Bir oturumu yasaklar.  
  
 <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> Ancak özelliğin ayarlanması, sözleşmenin gerektirdiği oturum tabanlı davranış türünü belirtir. Bu, WCF 'nin hizmet için yapılandırılmış bağlamanın (iletişim kanalını oluşturan) çalışma zamanında, bir hizmet uygularken bir oturum oluşturmadığını veya bir oturumu oluşturduğunu onaylamasını sağlar. Bu durumda, bağlama, tercih eden her türlü oturum tabanlı davranışla (güvenlik, taşıma, güvenilir veya bir bileşim) bu gereksinimi karşılayamaz. Tam davranış seçili <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> değere bağlıdır. Yapılandırılmış hizmetin bağlaması değerine <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A>uygun değilse, bir özel durum oluşturulur. Bağlama ve destek oturumlarını oluşturdukları kanallar, oturum tabanlı olarak kabul edilir.  
  
 Aşağıdaki hizmet sözleşmesi, `ICalculatorSession` içindeki tüm işlemlerin bir oturum içinde alışverişi gerektiğini belirtir. İşlemlerden hiçbiri `Equals` Yöntem dışında çağırana bir değer döndürmez. Ancak, yöntemi parametre içermez ve bu nedenle, yalnızca verilerin diğer işlemlere geçirilmiş bir oturum içinde sıfır olmayan bir değer döndürebilir. `Equals` Bu sözleşme, bir oturumun düzgün çalışmasını gerektirir. Belirli bir istemciyle ilişkili bir oturum olmadan, hizmet örneğinin bu istemcinin gönderdiği önceki verileri bilmesinin bir yolu yoktur.  
  
 [!code-csharp[S_Service_Session#1](../../../samples/snippets/csharp/VS_Snippets_CFX/s_service_session/cs/service.cs#1)]
 [!code-vb[S_Service_Session#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_service_session/vb/service.vb#1)]  
  
 Bir hizmet bir oturuma izin veriyorsa, bir oturum oluşturulur ve istemci bir tane başlatırsa kullanılır; Aksi takdirde, hiçbir oturum kurulmaz.  
  
## <a name="sessions-and-service-instances"></a>Oturumlar ve hizmet örnekleri  
 WCF 'de varsayılan örnek oluşturma davranışını kullanırsanız, WCF istemci nesnesi arasındaki tüm çağrılar aynı hizmet örneği tarafından işlenir. Bu nedenle, uygulama düzeyinde, yerel çağrı davranışına benzer şekilde uygulama davranışını etkinleştirme olarak bir oturum düşünebilirsiniz. Örneğin, yerel bir nesne oluşturduğunuzda:  
  
- Bir Oluşturucu çağırılır.  
  
- WCF istemci nesne başvurusuna yapılan sonraki tüm çağrılar aynı nesne örneği tarafından işlenir.  
  
- Nesne başvurusu yok edildiğinde yıkıcı çağrılır.  
  
 Oturumlar, varsayılan hizmet örneği davranışı kullanıldığı sürece istemciler ve hizmetler arasında benzer bir davranışı etkinleştirir. Bir hizmet sözleşmesi oturumları gerektiriyorsa veya destekliyorsa, bir veya daha fazla sözleşme işlemi, <xref:System.ServiceModel.OperationContractAttribute.IsInitiating%2A> ve <xref:System.ServiceModel.OperationContractAttribute.IsTerminating%2A> özelliklerini ayarlayarak bir oturumu başlatma veya sonlandırma olarak işaretlenebilir.  
  
 *Başlatma işlemleri* , yeni bir oturumun ilk işlemi olarak çağrılması gereken olanlardır. Başlatma olmayan işlemler, en az bir başlatma işlemi çağrıldıktan sonra çağrılabilir. Bu nedenle, hizmet örneğinin başlangıcına uygun istemcilerden giriş almak üzere tasarlanan başlatma işlemlerini bildirerek hizmetinize yönelik bir dizi oturum Oluşturucu oluşturabilirsiniz. (Durum, ancak hizmet nesnesi değil, oturumla ilişkilendirilir.)  
  
 Diğer yandan, *Işlemleri sonlandırma*, var olan bir oturumda son ileti olarak çağrılması gereken olanlardır. Varsayılan durumda, WCF hizmet nesnesini ve hizmetin ilişkili olduğu oturum kapatıldıktan sonra bağlamını geri dönüştürür. Bu nedenle, hizmet örneğinin sonuna uygun bir işlevi gerçekleştirmek için tasarlanan sonlandırma işlemlerini bildirerek bir tür yıkıcı oluşturabilirsiniz.  
  
> [!NOTE]
> Varsayılan davranış yerel oluşturucular ve Yıkıcılar ile benzerliği olsa da, yalnızca benzerliği vardır. Herhangi bir WCF hizmeti işlemi, bir başlatma veya sonlandırma işlemi ya da aynı anda her ikisi de olabilir. Ayrıca, varsayılan durumda, başlatma işlemlerine herhangi bir sırada herhangi bir sayıda çağrılabilir. oturum kurulduktan ve hizmet örneğinin ömrünü açıkça denetmediğiniz ( <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> nesneyi işleyerek) bir örnekle ilişkilendirildiğinde hiçbir ek oturum oluşturulmaz. Son olarak, durum hizmet nesnesi değil, oturumla ilişkilendirilir.  
  
 Örneğin, `ICalculatorSession` önceki örnekte kullanılan sözleşme, WCF istemci nesnesinin diğer bir işlemden önce `Clear` işlemi ilk kez çağırmasını ve bu WCF istemci nesnesiyle olan oturumun, `Equals` işlem. Aşağıdaki kod örneğinde, bu gereksinimleri zorlayan bir sözleşme gösterilmektedir. `Clear`bir oturumu başlatmak için önce çağrılmalıdır ve bu oturum çağrıldığında oturumu sonlandırır `Equals` .  
  
 [!code-csharp[SCA.IsInitiatingIsTerminating#1](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.isinitiatingisterminating/cs/service.cs#1)]
 [!code-vb[SCA.IsInitiatingIsTerminating#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.isinitiatingisterminating/vb/service.vb#1)]  
  
 Hizmetler, istemcileri ile oturum başlatmazlar. WCF istemci uygulamalarında, oturum tabanlı kanalın yaşam süresi ve oturumun kendisinin ömrü arasında doğrudan bir ilişki bulunur. Bu nedenle, istemciler yeni oturum tabanlı kanallar oluşturarak ve oturum tabanlı kanalları düzgün bir şekilde kapatarak mevcut oturumları kopararak yeni oturumlar oluşturur. İstemci, aşağıdakilerden birini çağırarak hizmet uç noktasıyla bir oturum başlatır:  
  
- <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType>bir çağrısıyla <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>döndürülen kanalda.  
  
- <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType>[ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)tarafından oluşturulan WCF istemci nesnesinde.  
  
- Her iki tür WCF istemci nesnesi (varsayılan olarak, tüm işlemler başlatılıyor) üzerinde başlatma işlemi. İlk işlem çağrıldığında, WCF istemci nesnesi kanalı otomatik olarak açar ve bir oturum başlatır.  
  
 Genellikle bir istemci, aşağıdakilerden birini çağırarak bir hizmet uç noktasıyla oturumu sonlandırır:  
  
- <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType>bir çağrısıyla <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>döndürülen kanalda.  
  
- <xref:System.ServiceModel.ClientBase%601.Close%2A?displayProperty=nameWithType>Svcutil. exe tarafından oluşturulan WCF istemci nesnesi üzerinde.  
  
- Her iki tür WCF istemci nesnesi üzerinde sonlandırma işlemi (varsayılan olarak, hiçbir işlem sonlandıralınmaz; sözleşme açıkça bir sonlandırma işlemi belirtmelidir). İlk işlem çağrıldığında, WCF istemci nesnesi kanalı otomatik olarak açar ve bir oturum başlatır.  
  
 Örnekler için bkz [. nasıl yapılır: [Varsayılan hizmet davranışı](../../../docs/framework/wcf/samples/default-service-behavior.md) ve [örnek](../../../docs/framework/wcf/samples/instancing.md) oluşturma](../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md) örneklerinin yanı sıra oturum gerektiren bir hizmet oluşturun.  
  
 İstemciler ve oturumlar hakkında daha fazla bilgi için bkz. [WCF Istemcisi kullanarak hizmetlere erişme](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md).  
  
## <a name="sessions-interact-with-instancecontext-settings"></a>Oturumlar InstanceContext ayarlarıyla etkileşim kurar  
 Bir sözleşmede <xref:System.ServiceModel.SessionMode> sabit listesi <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> ile belirli hizmet nesneleri arasındaki ilişkilendirmeyi denetleyen özelliği arasında bir etkileşim vardır. Daha fazla bilgi için bkz. [Oturumlar, örnek oluşturma ve eşzamanlılık](../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md).  
  
### <a name="sharing-instancecontext-objects"></a>InstanceContext nesnelerini paylaşma  
 Ayrıca, bu ilişkilendirmeyi kendiniz gerçekleştirerek hangi oturum tabanlı kanalın veya çağrının hangi <xref:System.ServiceModel.InstanceContext> nesneyle ilişkili olduğunu da denetleyebilirsiniz. 
  
## <a name="sessions-and-streaming"></a>Oturumlar ve akış  
 Aktarılacak büyük miktarda veriniz olduğunda, WCF 'deki akış aktarım modu, iletilerin arabelleğe alınması ve işlenmesi için varsayılan davranış için uygun bir alternatiftir. Oturum tabanlı bağlama ile çağrı akışı yaparken beklenmedik bir davranış alabilirsiniz. Kullanılan bağlama oturumları kullanacak şekilde yapılandırılmış olsa bile, tüm akış çağrıları, oturumları desteklemeyen tek bir kanal (Datagram kanalı) aracılığıyla yapılır. Birden çok istemci, oturum tabanlı bir bağlama üzerinden aynı hizmet nesnesine akış çağrıları yapar ve hizmet nesnesinin eşzamanlılık modu tek olarak ayarlanır ve örnek bağlam modu olarak `PerSession`ayarlanmışsa, tüm çağrılar veri birimi kanalının üzerinde ilermelidir ve bu nedenle tek seferde yalnızca bir çağrı işlenir. Daha sonra bir veya daha fazla istemci zaman aşımına uğrar. Bu soruna geçici bir çözüm olarak, hizmet nesnesinin `InstanceContextMode` `PerCall` ' i ' veya eşzamanlılık ' i ' i ' olarak ayarlayarak çalışabilirsiniz.  
  
> [!NOTE]
> Yalnızca bir "oturum" var olduğundan, MaxConcurrentSessions bu durumda hiçbir etkiye sahip değildir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.OperationContractAttribute.IsInitiating%2A>
- <xref:System.ServiceModel.OperationContractAttribute.IsTerminating%2A>
