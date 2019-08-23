---
title: Oturumlar, Örnek Oluşturma ve Eşzamanlılık
ms.date: 03/30/2017
ms.assetid: 50797a3b-7678-44ed-8138-49ac1602f35b
ms.openlocfilehash: d780488f7bb0bd46a22ef205b3954b6b4614cae0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969208"
---
# <a name="sessions-instancing-and-concurrency"></a>Oturumlar, Örnek Oluşturma ve Eşzamanlılık
*Oturum* , iki uç nokta arasında gönderilen tüm iletilerin bağıntısı olur. *Örnek* oluşturma, Kullanıcı tanımlı hizmet nesnelerinin ve bunlarla ilgili <xref:System.ServiceModel.InstanceContext> nesnelerin ömrünü denetlemeye başvurur. *Eşzamanlılık* , aynı anda bir <xref:System.ServiceModel.InstanceContext> içinde yürütülen iş parçacığı sayısı denetimine verilen terimdir.  
  
 Bu konu, bu ayarları, nasıl kullanılacağını ve aralarında çeşitli etkileşimleri açıklamaktadır.  
  
## <a name="sessions"></a>Oturumlar  
 Bir hizmet sözleşmesi <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> özelliği olarak <xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>ayarladığında, bu sözleşme tüm çağrıların (yani, çağrıları destekleyen temel alınan ileti değişimlerinin) aynı görüşmenin parçası olması gerektiğini söyleyecektir. Bir sözleşme, oturumlara izin verdiğini ancak bir tane gerektirmediğini belirtir, istemciler bağlanabilir ve bir oturum oluşturabilir. Oturum sonlanıyorsa ve aynı oturum tabanlı kanalda bir ileti gönderildiğinde bir özel durum oluşturulur.  
  
 WCF oturumları aşağıdaki ana kavramsal özelliklere sahiptir:  
  
- Bunlar, çağıran uygulama tarafından açık bir şekilde başlatılıp sonlandırılır.  
  
- Bir oturum sırasında teslim edilen iletiler alındıkları sırada işlenir.  
  
- Bir ileti grubunu bir konuşmaya ilişkilendirmede oturumlar. Bu korelasyon anlamı bir soyutlamadır. Örneğin, bir oturum tabanlı kanal, bir paylaşılan ağ bağlantısına göre iletileri ilişkilendirebilir, ancak başka bir oturum tabanlı kanal ileti gövdesinde paylaşılan bir etikete göre iletileri ilişkilendirip ilişkilendiremeyebilir. Oturumdan türetilebilen özellikler, bağıntı yapısına bağlıdır.  
  
- Bir WCF oturumuyla ilişkili genel veri deposu yok.  
  
 ASP.NET uygulamalarında <xref:System.Web.SessionState.HttpSessionState?displayProperty=nameWithType> sınıfı ve sağladığı işlevselliği biliyorsanız, bu tür oturum ve WCF oturumları arasında aşağıdaki farklılıkları fark edebilirsiniz:  
  
- ASP.NET oturumları her zaman sunucu tarafından başlatılır.  
  
- ASP.NET oturumları örtük olarak sırasız değildir.  
  
- ASP.NET oturumları, istekler arasında genel bir veri depolama mekanizması sağlar.  
  
 İstemci uygulamaları ve hizmet uygulamaları farklı yollarla oturumlarla etkileşim kurar. İstemci uygulamaları oturumları başlatır ve oturum içinde gönderilen iletileri alır ve işler. Hizmet uygulamaları, ek davranış eklemek için oturumları bir genişletilebilirlik noktası olarak kullanabilir. Bu, <xref:System.ServiceModel.InstanceContext> doğrudan özel bir örnek bağlam sağlayıcısı ile çalışarak veya uygulayarak yapılır.  
  
## <a name="instancing"></a>Örnek Oluşturma  
 Örnek oluşturma davranışı ( <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> özelliği kullanılarak ayarlanır), <xref:System.ServiceModel.InstanceContext> gelen iletilere yanıt olarak nasıl oluşturulduğunu denetler. Varsayılan olarak, her <xref:System.ServiceModel.InstanceContext> biri Kullanıcı tanımlı bir hizmet nesnesiyle ilişkilendirilir, yani (varsayılan durumda) <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özellik ayarı Kullanıcı tanımlı hizmet nesnelerinin örneklemesini de denetler. <xref:System.ServiceModel.InstanceContextMode> Sabit listesi, örnek oluşturma modlarını tanımlar.  
  
 Aşağıdaki örnek oluşturma modları kullanılabilir:  
  
- <xref:System.ServiceModel.InstanceContextMode.PerCall>: Her istemci <xref:System.ServiceModel.InstanceContext> isteği için yeni bir (ve bu nedenle hizmet nesnesi) oluşturulur.  
  
- <xref:System.ServiceModel.InstanceContextMode.PerSession>: Her yeni <xref:System.ServiceModel.InstanceContext> istemci oturumu için yeni bir (ve bu nedenle hizmet nesnesi) oluşturulur ve bu oturumun kullanım ömrü boyunca korunur (Bu, oturumları destekleyen bir bağlama gerektirir).  
  
- <xref:System.ServiceModel.InstanceContextMode.Single>: Tek <xref:System.ServiceModel.InstanceContext> bir (ve bu nedenle hizmet nesnesi), uygulamanın kullanım ömrü boyunca tüm istemci isteklerini işler.  
  
 Aşağıdaki kod örneği, <xref:System.ServiceModel.InstanceContextMode> <xref:System.ServiceModel.InstanceContextMode.PerSession> bir hizmet sınıfında açıkça ayarlanan varsayılan değeri gösterir.  
  
```  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]   
public class CalculatorService : ICalculatorInstance   
{   
    ...  
}  
```  
  
 Ancak <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> özellik ne <xref:System.ServiceModel.InstanceContext> sıklıkta yayınlanacağını <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> denetken, hizmet nesnesi serbest bırakıldığında <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A?displayProperty=nameWithType> ve özellikleri denetimi.  
  
### <a name="well-known-singleton-services"></a>İyi bilinen Singleton Hizmetleri  
 Tek örnekli hizmet nesnelerinde bir çeşitleme bazen yararlı olur: bir hizmet nesnesi oluşturabilir ve bu nesneyi kullanarak hizmet konağını oluşturabilirsiniz. Bunu yapmak için, hizmet ana bilgisayarı açıldığında <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> özelliği olarak <xref:System.ServiceModel.InstanceContextMode.Single> ayarlamanız veya bir özel durum oluşturulması gerekir.  
  
 Bu tür bir hizmet oluşturmak için oluşturucuyukullanın.<xref:System.ServiceModel.ServiceHost.%23ctor%28System.Object%2CSystem.Uri%5B%5D%29?displayProperty=nameWithType> Tek bir hizmet tarafından kullanılmak üzere belirli bir <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer?displayProperty=nameWithType> nesne örneği sağlamak istediğinizde özel uygulamaya bir alternatif sağlar. Bu aşırı yüklemeyi, hizmet uygulama türü oluşturulması zor olduğunda kullanabilirsiniz (örneğin, varsayılan parametresiz ortak Oluşturucu uygulamadıysanız).  
  
 Bu oluşturucuya bir nesne sağlandığında, Windows Communication Foundation (WCF) örnek oluşturma davranışıyla ilgili bazı özelliklerin farklı şekilde çalıştığını unutmayın. Örneğin, tek bir <xref:System.ServiceModel.InstanceContext.ReleaseServiceInstance%2A?displayProperty=nameWithType> nesne örneği sağlandığında çağırmanın hiçbir etkisi yoktur. Benzer şekilde, diğer örnek yayın mekanizması yok sayılır. Her zaman <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> özelliği tüm işlemler <xref:System.ServiceModel.ReleaseInstanceMode.None?displayProperty=nameWithType> için olarak ayarlanmış gibi davranır. <xref:System.ServiceModel.ServiceHost>  
  
### <a name="sharing-instancecontext-objects"></a>InstanceContext nesnelerini paylaşma  
 Ayrıca, bu ilişkilendirmeyi kendi başınıza gerçekleştirerek hangi oturumsuz kanalın veya çağrının hangi <xref:System.ServiceModel.InstanceContext> nesneyle ilişkilendirildiğini da denetleyebilirsiniz.  
  
## <a name="concurrency"></a>Eşzamanlılık  
 Eşzamanlılık, tek seferde etkin <xref:System.ServiceModel.InstanceContext> olan iş parçacıklarının sayısı denetimidir. Bu, <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> <xref:System.ServiceModel.ConcurrencyMode> numaralandırmasıyla birlikte kullanılarak denetlenir.  
  
 Aşağıdaki üç eşzamanlılık modu kullanılabilir:  
  
- <xref:System.ServiceModel.ConcurrencyMode.Single>: Her örnek bağlam, örnek bağlamında aynı anda en fazla bir iş parçacığı işlem iletisi işlemesine izin verilir. Aynı örnek bağlamını kullanmak isteyen diğer iş parçacıklarının, özgün iş parçacığı örnek bağlamından çıkana kadar blok olması gerekir.  
  
- <xref:System.ServiceModel.ConcurrencyMode.Multiple>: Her hizmet örneği aynı anda iletileri işleyen birden fazla iş parçacığına sahip olabilir. Bu eşzamanlılık modunu kullanabilmek için hizmet uygulamasının iş parçacığı açısından güvenli olması gerekir.  
  
- <xref:System.ServiceModel.ConcurrencyMode.Reentrant>: Her hizmet örneği tek seferde bir ileti işler, ancak yeniden entrant işlem çağrılarını kabul eder. Hizmet yalnızca bir WCF istemci nesnesi aracılığıyla çağrı yapıldığında bu çağrıları kabul eder.  
  
> [!NOTE]
> Birden fazla iş parçacığının güvenli bir şekilde kullanıldığı kodun anlaşılmasına ve geliştirilmesine, başarıyla yazılması zor olabilir. <xref:System.ServiceModel.ConcurrencyMode.Multiple> Veya<xref:System.ServiceModel.ConcurrencyMode.Reentrant> değerlerini kullanmadan önce, hizmetinizin bu modlar için doğru şekilde tasarlandığından emin olun. Daha fazla bilgi için bkz. <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>.  
  
 Eşzamanlılık kullanımı, örnek oluşturma moduyla ilgilidir. Örnek olarak, her ileti yeni <xref:System.ServiceModel.InstanceContext> bir tarafından işlendiği için <xref:System.ServiceModel.InstanceContext>eşzamanlılık ilgili değildir ve bu nedenle, içinde hiç bir iş parçacığı etkin değildir. <xref:System.ServiceModel.InstanceContextMode.PerCall>  
  
 Aşağıdaki kod örneği <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> özelliği olarak <xref:System.ServiceModel.ConcurrencyMode.Multiple>ayarlamayı gösterir.  
  
```  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.Single)]   
public class CalculatorService : ICalculatorConcurrency   
{   
    ...  
}  
```  
  
## <a name="sessions-interact-with-instancecontext-settings"></a>Oturumlar InstanceContext ayarlarıyla etkileşim kurar  
 Oturumlar ve <xref:System.ServiceModel.InstanceContext> bir sözleşmede <xref:System.ServiceModel.SessionMode> numaralandırma değerinin birleşimine ve <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> hizmet uygulamasındaki özelliğe bağlı olarak, kanallar ve belirli özellikler arasındaki ilişkiyi denetleyen etkileşim hizmet nesneleri.  
  
 Aşağıdaki tabloda, bir gelen kanalın sonuçları destekleme veya bir hizmetin <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> özelliğin değerlerinin <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> ve özelliğinin bir birleşimi olan oturumları desteklememinde gösterilmektedir.  
  
|InstanceContextMode değeri|<xref:System.ServiceModel.SessionMode.Required>|<xref:System.ServiceModel.SessionMode.Allowed>|<xref:System.ServiceModel.SessionMode.NotAllowed>|  
|-------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|  
|PerCall|-Oturumsuz kanal ile davranış: Her çağrı için <xref:System.ServiceModel.InstanceContext> bir oturum ve.<br />-Oturumsuz kanal ile davranış: Bir özel durum oluşturulur.|-Oturumsuz kanal ile davranış: Her çağrı için <xref:System.ServiceModel.InstanceContext> bir oturum ve.<br />-Oturumsuz kanal ile davranış: Her <xref:System.ServiceModel.InstanceContext> çağrı için bir.|-Oturumsuz kanal ile davranış: Bir özel durum oluşturulur.<br />-Oturumsuz kanal ile davranış: Her <xref:System.ServiceModel.InstanceContext> çağrı için bir.|  
|PerSession|-Oturumsuz kanal ile davranış: Her kanal için <xref:System.ServiceModel.InstanceContext> bir oturum ve.<br />-Oturumsuz kanal ile davranış: Bir özel durum oluşturulur.|-Oturumsuz kanal ile davranış: Her kanal için <xref:System.ServiceModel.InstanceContext> bir oturum ve.<br />-Oturumsuz kanal ile davranış: Her <xref:System.ServiceModel.InstanceContext> çağrı için bir.|-Oturumsuz kanal ile davranış: Bir özel durum oluşturulur.<br />-Oturumsuz kanal ile davranış: Her <xref:System.ServiceModel.InstanceContext> çağrı için bir.|  
|Tek|-Oturumsuz kanal ile davranış: Bir oturum ve <xref:System.ServiceModel.InstanceContext> tüm çağrılar için.<br />-Oturumsuz kanal ile davranış: Bir özel durum oluşturulur.|-Oturumsuz kanal ile davranış: Bir oturum ve <xref:System.ServiceModel.InstanceContext> oluşturulan ya da Kullanıcı tarafından belirtilen tek.<br />-Oturumsuz kanal ile davranış: <xref:System.ServiceModel.InstanceContext> Oluşturulan veya Kullanıcı tarafından belirtilen tek.|-Oturumsuz kanal ile davranış: Bir özel durum oluşturulur.<br />-Oturumsuz kanal ile davranış: Her <xref:System.ServiceModel.InstanceContext> oluşturulan tekil veya Kullanıcı tarafından belirtilen singleton için bir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Oturumları Kullanma](../../../../docs/framework/wcf/using-sessions.md)
- [Nasıl yapılır: Oturum gerektiren bir hizmet oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
- [Nasıl yapılır: Denetim hizmeti örnek oluşturma](../../../../docs/framework/wcf/feature-details/how-to-control-service-instancing.md)
- [Eşzamanlılık](../../../../docs/framework/wcf/samples/concurrency.md)
- [Örnek Oluşturma](../../../../docs/framework/wcf/samples/instancing.md)
- [Oturum](../../../../docs/framework/wcf/samples/session.md)
