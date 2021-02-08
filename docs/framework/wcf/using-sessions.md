---
description: 'Hakkında daha fazla bilgi edinin: oturumları kullanma'
title: Oturumları Kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sessions [WCF]
ms.assetid: 864ba12f-3331-4359-a359-6d6d387f1035
ms.openlocfilehash: bd5fc82af9b613566885bcf27e659edc4ba0e579
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778171"
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
  
 <xref:System.Web.SessionState.HttpSessionState?displayProperty=nameWithType>ASP.NET uygulamalarında sınıfı ve sağladığı işlevselliği biliyorsanız, bu tür oturum ve WCF oturumları arasında aşağıdaki farklılıkları fark edebilirsiniz:  
  
- ASP.NET oturumları her zaman sunucu tarafından başlatılır.  
  
- ASP.NET oturumları örtük olarak sırasız değildir.  
  
- ASP.NET oturumları, istekler arasında genel bir veri depolama mekanizması sağlar.  
  
 Bu konuda aşağıdakiler açıklanmaktadır:  
  
- Hizmet modeli katmanında oturum tabanlı bağlamalar kullanılırken varsayılan yürütme davranışı.  
  
- WCF oturum tabanlı, sistem tarafından belirtilen bağlamaların sağladığı Özellik türleri.  
  
- Oturum gereksinimini bildiren bir sözleşme oluşturma.  
  
- Oturumun oluşturulması ve sonlandırılmasını ve hizmetin hizmet örneği ile ilişkisini anlama ve denetleme.  
  
## <a name="default-execution-behavior-using-sessions"></a>Oturumları kullanan varsayılan yürütme davranışı  

 Oturumu başlatmayı deneyen bir bağlamaya *oturum tabanlı* bağlama denir. Hizmet sözleşmeleri, <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> hizmet sözleşmesi arabirimindeki (veya sınıfında) özelliği sabit listesi değerlerinden birine ayarlayarak, oturum tabanlı bağlamalar gerektirdiğini, bunlara izin vermenizi veya reddetmesini belirler <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> . Varsayılan olarak, bu özelliğin değeri, <xref:System.ServiceModel.SessionMode.Allowed> bir istemci BIR WCF Hizmeti uygulamasıyla oturum tabanlı bağlama kullanıyorsa, hizmet tarafından sağlanmış oturumu oluşturur ve kullanır.  
  
 Bir WCF hizmeti bir istemci oturumu kabul ettiğinde, aşağıdaki özellikler varsayılan olarak etkindir:  
  
1. WCF istemci nesnesi arasındaki tüm çağrılar aynı hizmet örneği tarafından işlenir.  
  
2. Farklı oturum tabanlı bağlamalar ek özellikler sağlar.  
  
## <a name="system-provided-session-types"></a>System-Provided oturum türleri  

 Oturum tabanlı bağlama, belirli bir oturumla bir hizmet örneğinin varsayılan ilişkilendirmesini destekler. Ancak, farklı oturum tabanlı bağlamalar, daha önce açıklanan oturum tabanlı örnek oluşturma denetimini etkinleştirmeye ek olarak farklı özellikleri de destekler.  
  
 WCF, aşağıdaki oturum tabanlı uygulama davranışı türlerini sağlar:  
  
- , <xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType> Her iki iletişimin de belirli bir güvenli konuşmaya karşı anlaştığı güvenlik tabanlı oturumları destekler. Daha fazla bilgi için bkz. [hizmetleri güvenli hale getirme](securing-services.md). Örneğin, <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType> hem güvenlik oturumları hem de güvenilir oturumlar için destek içeren bağlama, varsayılan olarak yalnızca iletileri şifreleyen ve dijital olarak imzalayabilen güvenli bir oturum kullanır.  
  
- <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType>Bağlama, tüm iletilerin yuva düzeyindeki bağlantıyla bağıntılı olduğundan emin olmak IÇIN TCP/IP tabanlı oturumları destekler.  
  
- <xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType>WS-ReliableMessaging belirtimini uygulayan öğesi, iletilerin, konuşma sırasında birden çok düğüm arasında seyahat edildiğinde bile iletilerin alınmasını sağlamak için, iletilerin sırayla ve tek bir kez teslim edileceği güvenilir oturumlara yönelik destek sağlar. Daha fazla bilgi için bkz. [Güvenilir Oturumlar](./feature-details/reliable-sessions.md).  
  
- <xref:System.ServiceModel.NetMsmqBinding?displayProperty=nameWithType>Bağlama, MSMQ veri birimi oturumları sağlar. Daha fazla bilgi için bkz. [WCF 'de kuyruklar](./feature-details/queues-in-wcf.md).  
  
 Özelliği ayarlamak, <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> sözleşmenin gerektirdiği oturum türünü belirtmez, yalnızca bir tane gerektirir.  
  
## <a name="creating-a-contract-that-requires-a-session"></a>Oturum gerektiren bir sözleşme oluşturma  

 Oturum gerektiren bir sözleşmenin oluşturulması, hizmet sözleşmesinin bildirdiği işlem grubunun tümünün aynı oturum içinde yürütülmesi ve iletilerin sırayla teslim edilmesi gerektiğini belirtir. Bir hizmet sözleşmesinin gerektirdiği oturum desteğinin düzeyini belirlemek için, <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> hizmet sözleşmesi arabiriminizdeki veya sınıfınızın özelliğini, <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> sözleşmenin değerini belirtmek için numaralandırmanın değerine ayarlayın:  
  
- Bir oturum gerektirir.  
  
- Bir istemcinin oturum kurmasını sağlar.  
  
- Bir oturumu yasaklar.  
  
 <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A>Ancak özelliğin ayarlanması, sözleşmenin gerektirdiği oturum tabanlı davranış türünü belirtir. Bu, WCF 'nin hizmet için yapılandırılmış bağlamanın (iletişim kanalını oluşturan) çalışma zamanında, bir hizmet uygularken bir oturum oluşturmadığını veya bir oturumu oluşturduğunu onaylamasını sağlar. Bu durumda, bağlama, tercih eden her türlü oturum tabanlı davranışla (güvenlik, taşıma, güvenilir veya bir bileşim) bu gereksinimi karşılayamaz. Tam davranış <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> Seçili değere bağlıdır. Yapılandırılmış hizmetin bağlaması değerine uygun değilse <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> , bir özel durum oluşturulur. Bağlama ve destek oturumlarını oluşturdukları kanallar, oturum tabanlı olarak kabul edilir.  
  
 Aşağıdaki hizmet sözleşmesi, içindeki tüm işlemlerin `ICalculatorSession` bir oturum içinde alışverişi gerektiğini belirtir. İşlemlerden hiçbiri Yöntem dışında çağırana bir değer döndürmez `Equals` . Ancak, `Equals` yöntemi parametre içermez ve bu nedenle, yalnızca verilerin diğer işlemlere geçirilmiş bir oturum içinde sıfır olmayan bir değer döndürebilir. Bu sözleşme, bir oturumun düzgün çalışmasını gerektirir. Belirli bir istemciyle ilişkili bir oturum olmadan, hizmet örneğinin bu istemcinin gönderdiği önceki verileri bilmesinin bir yolu yoktur.  
  
 [!code-csharp[S_Service_Session#1](../../../samples/snippets/csharp/VS_Snippets_CFX/s_service_session/cs/service.cs#1)]
 [!code-vb[S_Service_Session#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_service_session/vb/service.vb#1)]  
  
 Bir hizmet bir oturuma izin veriyorsa, bir oturum oluşturulur ve istemci bir tane başlatırsa kullanılır; Aksi takdirde, hiçbir oturum kurulmaz.  
  
## <a name="sessions-and-service-instances"></a>Oturumlar ve hizmet örnekleri  

 WCF 'de varsayılan örnek oluşturma davranışını kullanırsanız, WCF istemci nesnesi arasındaki tüm çağrılar aynı hizmet örneği tarafından işlenir. Bu nedenle, uygulama düzeyinde, yerel çağrı davranışına benzer şekilde uygulama davranışını etkinleştirme olarak bir oturum düşünebilirsiniz. Örneğin, yerel bir nesne oluşturduğunuzda:  
  
- Bir Oluşturucu çağırılır.  
  
- WCF istemci nesne başvurusuna yapılan sonraki tüm çağrılar aynı nesne örneği tarafından işlenir.  
  
- Nesne başvurusu yok edildiğinde yıkıcı çağrılır.  
  
 Oturumlar, varsayılan hizmet örneği davranışı kullanıldığı sürece istemciler ve hizmetler arasında benzer bir davranışı etkinleştirir. Bir hizmet sözleşmesi oturumları gerektiriyorsa veya destekliyorsa, bir veya daha fazla sözleşme işlemi, ve özelliklerini ayarlayarak bir oturumu başlatma veya sonlandırma olarak işaretlenebilir <xref:System.ServiceModel.OperationContractAttribute.IsInitiating%2A> <xref:System.ServiceModel.OperationContractAttribute.IsTerminating%2A> .  
  
 *Başlatma işlemleri* , yeni bir oturumun ilk işlemi olarak çağrılması gereken olanlardır. Başlatma olmayan işlemler, en az bir başlatma işlemi çağrıldıktan sonra çağrılabilir. Bu nedenle, hizmet örneğinin başlangıcına uygun istemcilerden giriş almak üzere tasarlanan başlatma işlemlerini bildirerek hizmetinize yönelik bir dizi oturum Oluşturucu oluşturabilirsiniz. (Durum, ancak hizmet nesnesi değil, oturumla ilişkilendirilir.)  
  
 Diğer yandan, *Işlemleri sonlandırma*, var olan bir oturumda son ileti olarak çağrılması gereken olanlardır. Varsayılan durumda, WCF hizmet nesnesini ve hizmetin ilişkili olduğu oturum kapatıldıktan sonra bağlamını geri dönüştürür. Bu nedenle, hizmet örneğinin sonuna uygun bir işlevi gerçekleştirmek için tasarlanan sonlandırma işlemlerini bildirerek bir tür yıkıcı oluşturabilirsiniz.  
  
> [!NOTE]
> Varsayılan davranış yerel oluşturucular ve Yıkıcılar ile benzerliği olsa da, yalnızca benzerliği vardır. Herhangi bir WCF hizmeti işlemi, bir başlatma veya sonlandırma işlemi ya da aynı anda her ikisi de olabilir. Ayrıca, varsayılan durumda, başlatma işlemlerine herhangi bir sırada herhangi bir sayıda çağrılabilir. oturum kurulduktan ve hizmet örneğinin ömrünü açıkça denetmediğiniz (nesneyi işleyerek) bir örnekle ilişkilendirildiğinde hiçbir ek oturum oluşturulmaz <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> . Son olarak, durum hizmet nesnesi değil, oturumla ilişkilendirilir.  
  
 Örneğin, `ICalculatorSession` Önceki örnekte kullanılan sözleşme, WCF istemci nesnesinin `Clear` diğer bir işlemden önce işlemi ilk kez çağırmasını ve bu WCF istemci nesnesiyle olan oturumun işlemi aradığında sonlandırılması gerekir `Equals` . Aşağıdaki kod örneğinde, bu gereksinimleri zorlayan bir sözleşme gösterilmektedir. `Clear` bir oturumu başlatmak için önce çağrılmalıdır ve bu oturum çağrıldığında oturumu sonlandırır `Equals` .  
  
 [!code-csharp[SCA.IsInitiatingIsTerminating#1](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.isinitiatingisterminating/cs/service.cs#1)]
 [!code-vb[SCA.IsInitiatingIsTerminating#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.isinitiatingisterminating/vb/service.vb#1)]  
  
 Hizmetler, istemcileri ile oturum başlatmazlar. WCF istemci uygulamalarında, oturum tabanlı kanalın yaşam süresi ve oturumun kendisinin ömrü arasında doğrudan bir ilişki bulunur. Bu nedenle, istemciler yeni oturum tabanlı kanallar oluşturarak ve oturum tabanlı kanalları düzgün bir şekilde kapatarak mevcut oturumları kopararak yeni oturumlar oluşturur. İstemci, aşağıdakilerden birini çağırarak hizmet uç noktasıyla bir oturum başlatır:  
  
- <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> bir çağrısıyla döndürülen kanalda <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> .  
  
- <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType>[ServiceModel meta veri yardımcı programı aracı](servicemodel-metadata-utility-tool-svcutil-exe.md)tarafından oluşturulan WCF istemci nesnesinde (Svcutil.exe).  
  
- Her iki tür WCF istemci nesnesi (varsayılan olarak, tüm işlemler başlatılıyor) üzerinde başlatma işlemi. İlk işlem çağrıldığında, WCF istemci nesnesi kanalı otomatik olarak açar ve bir oturum başlatır.  
  
 Genellikle bir istemci, aşağıdakilerden birini çağırarak bir hizmet uç noktasıyla oturumu sonlandırır:  
  
- <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType> bir çağrısıyla döndürülen kanalda <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> .  
  
- <xref:System.ServiceModel.ClientBase%601.Close%2A?displayProperty=nameWithType> Svcutil.exe tarafından oluşturulan WCF istemci nesnesi üzerinde.  
  
- Her iki tür WCF istemci nesnesi üzerinde sonlandırma işlemi (varsayılan olarak, hiçbir işlem sonlandıralınmaz; sözleşme açıkça bir sonlandırma işlemi belirtmelidir). İlk işlem çağrıldığında, WCF istemci nesnesi kanalı otomatik olarak açar ve bir oturum başlatır.  
  
 Örnekler için bkz. [nasıl yapılır: oturum gerektiren bir hizmet oluşturma](./feature-details/how-to-create-a-service-that-requires-sessions.md) ve [varsayılan hizmet davranışı](./samples/default-service-behavior.md) ve [örnek](./samples/instancing.md) oluşturma örnekleri.  
  
 İstemciler ve oturumlar hakkında daha fazla bilgi için bkz. [WCF Istemcisi kullanarak hizmetlere erişme](./feature-details/accessing-services-using-a-client.md).  
  
## <a name="sessions-interact-with-instancecontext-settings"></a>Oturumlar InstanceContext ayarlarıyla etkileşim kurar  

 <xref:System.ServiceModel.SessionMode>Bir sözleşmede sabit listesi ile <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> belirli hizmet nesneleri arasındaki ilişkilendirmeyi denetleyen özelliği arasında bir etkileşim vardır. Daha fazla bilgi için bkz. [Oturumlar, örnek oluşturma ve eşzamanlılık](./feature-details/sessions-instancing-and-concurrency.md).  
  
### <a name="sharing-instancecontext-objects"></a>InstanceContext nesnelerini paylaşma  

 Ayrıca, <xref:System.ServiceModel.InstanceContext> Bu ilişkilendirmeyi kendiniz gerçekleştirerek hangi oturum tabanlı kanalın veya çağrının hangi nesneyle ilişkili olduğunu da denetleyebilirsiniz.
  
## <a name="sessions-and-streaming"></a>Oturumlar ve akış  

 Aktarılacak büyük miktarda veriniz olduğunda, WCF 'deki akış aktarım modu, iletilerin arabelleğe alınması ve işlenmesi için varsayılan davranış için uygun bir alternatiftir. Oturum tabanlı bağlama ile çağrı akışı yaparken beklenmedik bir davranış alabilirsiniz. Kullanılan bağlama oturumları kullanacak şekilde yapılandırılmış olsa bile, tüm akış çağrıları, oturumları desteklemeyen tek bir kanal (Datagram kanalı) aracılığıyla yapılır. Birden çok istemci, oturum tabanlı bir bağlama üzerinden aynı hizmet nesnesine akış çağrıları yapar ve hizmet nesnesinin eşzamanlılık modu tek olarak ayarlanır ve örnek bağlam modu olarak ayarlanmışsa `PerSession` , tüm çağrılar aynı anda yalnızca bir çağrı işlenir. Daha sonra bir veya daha fazla istemci zaman aşımına uğrar. Bu soruna geçici bir çözüm olarak, hizmet nesnesinin ' i ' veya eşzamanlılık ' i ' i ' olarak ayarlayarak çalışabilirsiniz `InstanceContextMode` `PerCall` .  
  
> [!NOTE]
> Yalnızca bir "oturum" var olduğundan, MaxConcurrentSessions bu durumda hiçbir etkiye sahip değildir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.OperationContractAttribute.IsInitiating%2A>
- <xref:System.ServiceModel.OperationContractAttribute.IsTerminating%2A>
