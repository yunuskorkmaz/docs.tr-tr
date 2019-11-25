---
title: Oturumlar, Örnek Oluşturma ve Eşzamanlılık
ms.date: 03/30/2017
ms.assetid: 50797a3b-7678-44ed-8138-49ac1602f35b
ms.openlocfilehash: b8c0b40ca67de92f4f1b481298a8a26d96e887d4
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976088"
---
# <a name="sessions-instancing-and-concurrency"></a>Oturumlar, Örnek Oluşturma ve Eşzamanlılık
*Oturum* , iki uç nokta arasında gönderilen tüm iletilerin bağıntısı olur. *Örnek* oluşturma, Kullanıcı tanımlı hizmet nesnelerinin ve bunlarla ilgili <xref:System.ServiceModel.InstanceContext> nesnelerinin yaşam süresini denetlemeye başvurur. *Eşzamanlılık* , aynı anda bir <xref:System.ServiceModel.InstanceContext> yürüten iş parçacığı sayısı denetimine verilen terimdir.  
  
 Bu konu, bu ayarları, nasıl kullanılacağını ve aralarında çeşitli etkileşimleri açıklamaktadır.  
  
## <a name="sessions"></a>Oturumlar  
 Bir hizmet sözleşmesi <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> özelliğini <xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>olarak ayarlarsa, bu sözleşme tüm çağrıların (yani, çağrıları destekleyen temel alınan ileti değişimlerinin) aynı görüşmenin parçası olması gerektiğini söyleyecektir. Bir sözleşme, oturumlara izin verdiğini ancak bir tane gerektirmediğini belirtir, istemciler bağlanabilir ve bir oturum oluşturabilir. Oturum sonlanıyorsa ve aynı oturum tabanlı kanalda bir ileti gönderildiğinde bir özel durum oluşturulur.  
  
 WCF oturumları aşağıdaki ana kavramsal özelliklere sahiptir:  
  
- Bunlar, çağıran uygulama tarafından açık bir şekilde başlatılıp sonlandırılır.  
  
- Bir oturum sırasında teslim edilen iletiler alındıkları sırada işlenir.  
  
- Bir ileti grubunu bir konuşmaya ilişkilendirmede oturumlar. Bu korelasyon anlamı bir soyutlamadır. Örneğin, bir oturum tabanlı kanal, bir paylaşılan ağ bağlantısına göre iletileri ilişkilendirebilir, ancak başka bir oturum tabanlı kanal ileti gövdesinde paylaşılan bir etikete göre iletileri ilişkilendirip ilişkilendiremeyebilir. Oturumdan türetilebilen özellikler, bağıntı yapısına bağlıdır.  
  
- Bir WCF oturumuyla ilişkili genel veri deposu yok.  
  
 ASP.NET uygulamalarında <xref:System.Web.SessionState.HttpSessionState?displayProperty=nameWithType> sınıfına ve sağladığı işlevselliğe alışkın değilseniz, bu tür oturum ve WCF oturumları arasında aşağıdaki farklılıkları fark edebilirsiniz:  
  
- ASP.NET oturumları her zaman sunucu tarafından başlatılır.  
  
- ASP.NET oturumları örtük olarak sırasız değildir.  
  
- ASP.NET oturumları, istekler arasında genel bir veri depolama mekanizması sağlar.  
  
 İstemci uygulamaları ve hizmet uygulamaları farklı yollarla oturumlarla etkileşim kurar. İstemci uygulamaları oturumları başlatır ve oturum içinde gönderilen iletileri alır ve işler. Hizmet uygulamaları, ek davranış eklemek için oturumları bir genişletilebilirlik noktası olarak kullanabilir. Bu işlem, <xref:System.ServiceModel.InstanceContext> doğrudan çalışarak veya özel bir örnek bağlam sağlayıcısı uygulayarak yapılır.  
  
## <a name="instancing"></a>Örnek Oluşturma  
 Örnek oluşturma davranışı (<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> özelliği kullanılarak ayarlanır), gelen iletilere yanıt olarak <xref:System.ServiceModel.InstanceContext> nasıl oluşturulduğunu denetler. Varsayılan olarak, her <xref:System.ServiceModel.InstanceContext> Kullanıcı tanımlı bir hizmet nesnesiyle ilişkilendirilir, bu nedenle (varsayılan durumda) <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliğinin ayarlanması, Kullanıcı tanımlı hizmet nesnelerinin örneklemesini de denetler. <xref:System.ServiceModel.InstanceContextMode> numaralandırması, örnek oluşturma modlarını tanımlar.  
  
 Aşağıdaki örnek oluşturma modları kullanılabilir:  
  
- <xref:System.ServiceModel.InstanceContextMode.PerCall>: her istemci isteği için yeni bir <xref:System.ServiceModel.InstanceContext> (ve bu nedenle hizmet nesnesi) oluşturulur.  
  
- <xref:System.ServiceModel.InstanceContextMode.PerSession>: yeni bir <xref:System.ServiceModel.InstanceContext> (ve bu nedenle hizmet nesnesi) her yeni istemci oturumu için oluşturulur ve bu oturumun kullanım ömrü boyunca korunur (Bu, oturumları destekleyen bir bağlama gerektirir).  
  
- <xref:System.ServiceModel.InstanceContextMode.Single>: tek bir <xref:System.ServiceModel.InstanceContext> (ve bu nedenle hizmet nesnesi) uygulamanın kullanım ömrü boyunca tüm istemci isteklerini işler.  
  
 Aşağıdaki kod örneği, bir hizmet sınıfında açıkça ayarlanmakta olan <xref:System.ServiceModel.InstanceContextMode.PerSession> varsayılan <xref:System.ServiceModel.InstanceContextMode> değerini gösterir.  
  
```csharp  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]   
public class CalculatorService : ICalculatorInstance   
{   
    ...  
}  
```  
  
 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> özelliği <xref:System.ServiceModel.InstanceContext> ne sıklıkta yayınlanacağını denetken, hizmet nesnesi serbest bırakıldığında <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> ve <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A?displayProperty=nameWithType> özellikleri denetimi.  
  
### <a name="well-known-singleton-services"></a>İyi bilinen Singleton Hizmetleri  
 Tek örnekli hizmet nesnelerinde bir çeşitleme bazen yararlı olur: bir hizmet nesnesi oluşturabilir ve bu nesneyi kullanarak hizmet konağını oluşturabilirsiniz. Bunu yapmak için <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> özelliğini <xref:System.ServiceModel.InstanceContextMode.Single> olarak ayarlamanız gerekir veya hizmet ana bilgisayarı açıldığında bir özel durum oluşturulur.  
  
 Böyle bir hizmet oluşturmak için <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Object%2CSystem.Uri%5B%5D%29?displayProperty=nameWithType> oluşturucusunu kullanın. Tek bir hizmet tarafından kullanılmak üzere belirli bir nesne örneği sağlamak istediğinizde özel bir <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer?displayProperty=nameWithType> uygulamak için alternatif sağlar. Bu aşırı yüklemeyi, hizmet uygulama türü oluşturulması zor olduğunda kullanabilirsiniz (örneğin, parametresiz bir ortak Oluşturucu uygulamadıysanız).  
  
 Bu oluşturucuya bir nesne sağlandığında, Windows Communication Foundation (WCF) örnek oluşturma davranışıyla ilgili bazı özelliklerin farklı şekilde çalıştığını unutmayın. Örneğin, tek bir nesne örneği sağlandığında <xref:System.ServiceModel.InstanceContext.ReleaseServiceInstance%2A?displayProperty=nameWithType> çağırmak etkisizdir. Benzer şekilde, diğer örnek yayın mekanizması yok sayılır. <xref:System.ServiceModel.ServiceHost> her zaman, <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> özelliği tüm işlemler için <xref:System.ServiceModel.ReleaseInstanceMode.None?displayProperty=nameWithType> olarak ayarlanmış gibi davranır.  
  
### <a name="sharing-instancecontext-objects"></a>InstanceContext nesnelerini paylaşma  
 Ayrıca, bu ilişkilendirmeyi kendi başınıza gerçekleştirerek ne <xref:System.ServiceModel.InstanceContext> nesnesiyle ilişkili olduğunu da denetleyebilirsiniz.  
  
## <a name="concurrency"></a>Eşzamanlılık  
 Eşzamanlılık, bir <xref:System.ServiceModel.InstanceContext> etkin olan iş parçacıklarının sayısını herhangi bir zamanda denetler. Bu, <xref:System.ServiceModel.ConcurrencyMode> numaralandırmasında <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> kullanılarak denetlenir.  
  
 Aşağıdaki üç eşzamanlılık modu kullanılabilir:  
  
- <xref:System.ServiceModel.ConcurrencyMode.Single>: her bir örnek bağlamının, her seferinde örnek bağlamında en fazla bir iş parçacığı işleme iletisi olmasına izin verilir. Aynı örnek bağlamını kullanmak isteyen diğer iş parçacıklarının, özgün iş parçacığı örnek bağlamından çıkana kadar blok olması gerekir.  
  
- <xref:System.ServiceModel.ConcurrencyMode.Multiple>: her hizmet örneği aynı anda iletileri işleyen birden fazla iş parçacığına sahip olabilir. Bu eşzamanlılık modunu kullanabilmek için hizmet uygulamasının iş parçacığı açısından güvenli olması gerekir.  
  
- <xref:System.ServiceModel.ConcurrencyMode.Reentrant>: her hizmet örneği tek seferde bir ileti işler, ancak yeniden entrant işlem çağrılarını kabul eder. Hizmet yalnızca bir WCF istemci nesnesi aracılığıyla çağrı yapıldığında bu çağrıları kabul eder.  
  
> [!NOTE]
> Birden fazla iş parçacığının güvenli bir şekilde kullanıldığı kodun anlaşılmasına ve geliştirilmesine, başarıyla yazılması zor olabilir. <xref:System.ServiceModel.ConcurrencyMode.Multiple> veya <xref:System.ServiceModel.ConcurrencyMode.Reentrant> değerlerini kullanmadan önce, hizmetinizin bu modlar için doğru şekilde tasarlandığından emin olun. Daha fazla bilgi için bkz. <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>.  
  
 Eşzamanlılık kullanımı, örnek oluşturma moduyla ilgilidir. <xref:System.ServiceModel.InstanceContextMode.PerCall> örnek oluşturma, her ileti yeni bir <xref:System.ServiceModel.InstanceContext> tarafından işlendiği ve bu nedenle <xref:System.ServiceModel.InstanceContext>birden çok iş parçacığı etkin olmadığından eşzamanlılık ilgili değildir.  
  
 Aşağıdaki kod örneği, <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> özelliğini <xref:System.ServiceModel.ConcurrencyMode.Multiple>olarak ayarlamayı gösterir.  
  
```csharp
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.Single)]   
public class CalculatorService : ICalculatorConcurrency   
{   
    ...  
}  
```  
  
## <a name="sessions-interact-with-instancecontext-settings"></a>Oturumlar InstanceContext ayarlarıyla etkileşim kurar  
 Oturumlar ve <xref:System.ServiceModel.InstanceContext>, bir sözleşmede <xref:System.ServiceModel.SessionMode> numaralandırması değerinin birleşimine ve hizmet uygulamasındaki <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> özelliğine bağlı olarak, kanallar ve belirli hizmet nesneleri arasındaki ilişkilendirmeyi denetleyen şekilde etkileşim kurar.  
  
 Aşağıdaki tabloda, bir gelen kanalın sonuçları destekleme veya bir hizmetin <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> özelliği ve <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> özelliği değerlerinin birleşimine verilen oturumları desteklemekte olduğu gösterilmektedir.  
  
|InstanceContextMode değeri|<xref:System.ServiceModel.SessionMode.Required>|<xref:System.ServiceModel.SessionMode.Allowed>|<xref:System.ServiceModel.SessionMode.NotAllowed>|  
|-------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|  
|PerCall|-Oturumsuz kanal ile davranış: her çağrının bir oturumu ve <xref:System.ServiceModel.InstanceContext>.<br />-Oturumsuz kanal ile davranış: bir özel durum oluşturulur.|-Oturumsuz kanal ile davranış: her çağrının bir oturumu ve <xref:System.ServiceModel.InstanceContext>.<br />-Oturumsuz kanal ile davranış: her çağrı için bir <xref:System.ServiceModel.InstanceContext>.|-Oturumsuz kanal ile davranış: bir özel durum oluşturulur.<br />-Oturumsuz kanal ile davranış: her çağrı için bir <xref:System.ServiceModel.InstanceContext>.|  
|PerSession|-Oturumsuz kanal ile davranış: her kanal için bir oturum ve <xref:System.ServiceModel.InstanceContext>.<br />-Oturumsuz kanal ile davranış: bir özel durum oluşturulur.|-Oturumsuz kanal ile davranış: her kanal için bir oturum ve <xref:System.ServiceModel.InstanceContext>.<br />-Oturumsuz kanal ile davranış: her çağrı için bir <xref:System.ServiceModel.InstanceContext>.|-Oturumsuz kanal ile davranış: bir özel durum oluşturulur.<br />-Oturumsuz kanal ile davranış: her çağrı için bir <xref:System.ServiceModel.InstanceContext>.|  
|Tek|-Oturumsuz kanal ile davranış: tüm çağrılar için bir oturum ve bir <xref:System.ServiceModel.InstanceContext>.<br />-Oturumsuz kanal ile davranış: bir özel durum oluşturulur.|-Oturumlı kanal ile davranış: oluşturulan veya Kullanıcı tarafından belirtilen tek için bir oturum ve <xref:System.ServiceModel.InstanceContext>.<br />-Oturumsuz kanal ile davranış: oluşturulan veya Kullanıcı tarafından belirtilen singleton için bir <xref:System.ServiceModel.InstanceContext>.|-Oturumsuz kanal ile davranış: bir özel durum oluşturulur.<br />-Oturumsuz kanal ile davranış: her oluşturulan tek tekil veya Kullanıcı tarafından belirtilen tek için <xref:System.ServiceModel.InstanceContext>.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Oturumları Kullanma](../../../../docs/framework/wcf/using-sessions.md)
- [Nasıl yapılır: Oturum Gerektiren Bir Hizmet Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
- [Nasıl yapılır: Hizmet Örneği Oluşturmayı Denetleme](../../../../docs/framework/wcf/feature-details/how-to-control-service-instancing.md)
- [Eşzamanlılık](../../../../docs/framework/wcf/samples/concurrency.md)
- [Örnek Oluşturma](../../../../docs/framework/wcf/samples/instancing.md)
- [Oturum](../../../../docs/framework/wcf/samples/session.md)
