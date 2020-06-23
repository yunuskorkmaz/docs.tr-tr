---
title: Oturumlar, Örnek Oluşturma ve Eşzamanlılık
description: Oturumlar, örnek oluşturma ve eşzamanlılık, nasıl kullanılacağı ve WFC arasındaki etkileşimler hakkında bilgi edinin.
ms.date: 03/30/2017
ms.assetid: 50797a3b-7678-44ed-8138-49ac1602f35b
ms.openlocfilehash: 41eef5a962c702eebd6b9a34607b542ec6bbd97b
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246551"
---
# <a name="sessions-instancing-and-concurrency"></a>Oturumlar, Örnek Oluşturma ve Eşzamanlılık
*Oturum* , iki uç nokta arasında gönderilen tüm iletilerin bağıntısı olur. *Örnek* oluşturma, Kullanıcı tanımlı hizmet nesnelerinin ve bunlarla ilgili nesnelerin ömrünü denetlemeye başvurur <xref:System.ServiceModel.InstanceContext> . *Eşzamanlılık* , aynı anda bir içinde yürütülen iş parçacığı sayısı denetimine verilen terimdir <xref:System.ServiceModel.InstanceContext> .  
  
 Bu konu, bu ayarları, nasıl kullanılacağını ve aralarında çeşitli etkileşimleri açıklamaktadır.  
  
## <a name="sessions"></a>Oturumlar  
 Bir hizmet sözleşmesi <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> özelliği olarak ayarladığında <xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType> , bu sözleşme tüm çağrıların (yani, çağrıları destekleyen temel alınan ileti değişimlerinin) aynı görüşmenin parçası olması gerektiğini söyleyecektir. Bir sözleşme, oturumlara izin verdiğini ancak bir tane gerektirmediğini belirtir, istemciler bağlanabilir ve bir oturum oluşturabilir. Oturum sonlanıyorsa ve aynı oturum tabanlı kanalda bir ileti gönderildiğinde bir özel durum oluşturulur.  
  
 WCF oturumları aşağıdaki ana kavramsal özelliklere sahiptir:  
  
- Bunlar, çağıran uygulama tarafından açık bir şekilde başlatılıp sonlandırılır.  
  
- Bir oturum sırasında teslim edilen iletiler alındıkları sırada işlenir.  
  
- Bir ileti grubunu bir konuşmaya ilişkilendirmede oturumlar. Bu korelasyon anlamı bir soyutlamadır. Örneğin, bir oturum tabanlı kanal, bir paylaşılan ağ bağlantısına göre iletileri ilişkilendirebilir, ancak başka bir oturum tabanlı kanal ileti gövdesinde paylaşılan bir etikete göre iletileri ilişkilendirip ilişkilendiremeyebilir. Oturumdan türetilebilen özellikler, bağıntı yapısına bağlıdır.  
  
- Bir WCF oturumuyla ilişkili genel veri deposu yok.  
  
 <xref:System.Web.SessionState.HttpSessionState?displayProperty=nameWithType>ASP.NET uygulamalarında sınıfı ve sağladığı işlevselliği biliyorsanız, bu tür oturum ve WCF oturumları arasında aşağıdaki farklılıkları fark edebilirsiniz:  
  
- ASP.NET oturumları her zaman sunucu tarafından başlatılır.  
  
- ASP.NET oturumları örtük olarak sırasız değildir.  
  
- ASP.NET oturumları, istekler arasında genel bir veri depolama mekanizması sağlar.  
  
 İstemci uygulamaları ve hizmet uygulamaları farklı yollarla oturumlarla etkileşim kurar. İstemci uygulamaları oturumları başlatır ve oturum içinde gönderilen iletileri alır ve işler. Hizmet uygulamaları, ek davranış eklemek için oturumları bir genişletilebilirlik noktası olarak kullanabilir. Bu, doğrudan <xref:System.ServiceModel.InstanceContext> özel bir örnek bağlam sağlayıcısı ile çalışarak veya uygulayarak yapılır.  
  
## <a name="instancing"></a>Örnek Oluşturma  
 Örnek oluşturma davranışı (özelliği kullanılarak ayarlanır <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> ), <xref:System.ServiceModel.InstanceContext> gelen iletilere yanıt olarak nasıl oluşturulduğunu denetler. Varsayılan olarak, her biri <xref:System.ServiceModel.InstanceContext> Kullanıcı tanımlı bir hizmet nesnesiyle ilişkilendirilir, yani (varsayılan durumda) <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özellik ayarı Kullanıcı tanımlı hizmet nesnelerinin örneklemesini de denetler. <xref:System.ServiceModel.InstanceContextMode>Sabit listesi, örnek oluşturma modlarını tanımlar.  
  
 Aşağıdaki örnek oluşturma modları kullanılabilir:  
  
- <xref:System.ServiceModel.InstanceContextMode.PerCall>: <xref:System.ServiceModel.InstanceContext> Her istemci isteği için yeni bir (ve bu nedenle hizmet nesnesi) oluşturulur.  
  
- <xref:System.ServiceModel.InstanceContextMode.PerSession>: <xref:System.ServiceModel.InstanceContext> Her yeni istemci oturumu için yeni bir (ve bu nedenle hizmet nesnesi) oluşturulur ve bu oturumun kullanım ömrü boyunca korunur (Bu, oturumları destekleyen bir bağlama gerektirir).  
  
- <xref:System.ServiceModel.InstanceContextMode.Single>: Tek bir <xref:System.ServiceModel.InstanceContext> (ve bu nedenle hizmet nesnesi), uygulamanın kullanım ömrü boyunca tüm istemci isteklerini işler.  
  
 Aşağıdaki kod örneği <xref:System.ServiceModel.InstanceContextMode> , <xref:System.ServiceModel.InstanceContextMode.PerSession> bir hizmet sınıfında açıkça ayarlanan varsayılan değeri gösterir.  
  
```csharp  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]
public class CalculatorService : ICalculatorInstance
{
    ...  
}  
```  
  
 Ancak <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> özellik ne sıklıkta yayınlanacağını denetken, <xref:System.ServiceModel.InstanceContext> <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A?displayProperty=nameWithType> hizmet nesnesi serbest bırakıldığında ve özellikleri denetimi.  
  
### <a name="well-known-singleton-services"></a>İyi bilinen Singleton Hizmetleri  
 Tek örnekli hizmet nesnelerinde bir çeşitleme bazen yararlı olur: bir hizmet nesnesi oluşturabilir ve bu nesneyi kullanarak hizmet konağını oluşturabilirsiniz. Bunu yapmak için, <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> <xref:System.ServiceModel.InstanceContextMode.Single> hizmet ana bilgisayarı açıldığında özelliği olarak ayarlamanız veya bir özel durum oluşturulması gerekir.  
  
 <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Object%2CSystem.Uri%5B%5D%29>Bu tür bir hizmet oluşturmak için oluşturucuyu kullanın. <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer?displayProperty=nameWithType>Tek bir hizmet tarafından kullanılmak üzere belirli bir nesne örneği sağlamak istediğinizde özel uygulamaya bir alternatif sağlar. Bu aşırı yüklemeyi, hizmet uygulama türü oluşturulması zor olduğunda kullanabilirsiniz (örneğin, parametresiz bir ortak Oluşturucu uygulamadıysanız).  
  
 Bu oluşturucuya bir nesne sağlandığında, Windows Communication Foundation (WCF) örnek oluşturma davranışıyla ilgili bazı özelliklerin farklı şekilde çalıştığını unutmayın. Örneğin, <xref:System.ServiceModel.InstanceContext.ReleaseServiceInstance%2A?displayProperty=nameWithType> tek bir nesne örneği sağlandığında çağırmanın hiçbir etkisi yoktur. Benzer şekilde, diğer örnek yayın mekanizması yok sayılır. <xref:System.ServiceModel.ServiceHost>Her zaman <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> özelliği tüm işlemler için olarak ayarlanmış gibi davranır <xref:System.ServiceModel.ReleaseInstanceMode.None?displayProperty=nameWithType> .  
  
### <a name="sharing-instancecontext-objects"></a>InstanceContext nesnelerini paylaşma  
 Ayrıca, <xref:System.ServiceModel.InstanceContext> Bu ilişkilendirmeyi kendi başınıza gerçekleştirerek hangi oturumsuz kanalın veya çağrının hangi nesneyle ilişkilendirildiğini da denetleyebilirsiniz.  
  
## <a name="concurrency"></a>Eşzamanlılık  
 Eşzamanlılık, tek seferde etkin olan iş parçacıklarının sayısı denetimidir <xref:System.ServiceModel.InstanceContext> . Bu, numaralandırmasıyla birlikte kullanılarak denetlenir <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> <xref:System.ServiceModel.ConcurrencyMode> .  
  
 Aşağıdaki üç eşzamanlılık modu kullanılabilir:  
  
- <xref:System.ServiceModel.ConcurrencyMode.Single>: Her örnek bağlamının, örnek bağlamında aynı anda en fazla bir iş parçacığı işlem iletisi işlemesine izin verilir. Aynı örnek bağlamını kullanmak isteyen diğer iş parçacıklarının, özgün iş parçacığı örnek bağlamından çıkana kadar blok olması gerekir.  
  
- <xref:System.ServiceModel.ConcurrencyMode.Multiple>: Her hizmet örneği aynı anda iletileri işleyen birden fazla iş parçacığına sahip olabilir. Bu eşzamanlılık modunu kullanabilmek için hizmet uygulamasının iş parçacığı açısından güvenli olması gerekir.  
  
- <xref:System.ServiceModel.ConcurrencyMode.Reentrant>: Her hizmet örneği tek seferde bir ileti işler, ancak yeniden entrant işlem çağrılarını kabul eder. Hizmet yalnızca bir WCF istemci nesnesi aracılığıyla çağrı yapıldığında bu çağrıları kabul eder.  
  
> [!NOTE]
> Birden fazla iş parçacığının güvenli bir şekilde kullanıldığı kodun anlaşılmasına ve geliştirilmesine, başarıyla yazılması zor olabilir. <xref:System.ServiceModel.ConcurrencyMode.Multiple>Veya değerlerini kullanmadan önce <xref:System.ServiceModel.ConcurrencyMode.Reentrant> , hizmetinizin bu modlar için doğru şekilde tasarlandığından emin olun. Daha fazla bilgi için bkz. <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>.  
  
 Eşzamanlılık kullanımı, örnek oluşturma moduyla ilgilidir. <xref:System.ServiceModel.InstanceContextMode.PerCall>Örnek olarak, her ileti yeni bir tarafından işlendiği için eşzamanlılık ilgili değildir <xref:System.ServiceModel.InstanceContext> ve bu nedenle, içinde hiç bir iş parçacığı etkin değildir <xref:System.ServiceModel.InstanceContext> .  
  
 Aşağıdaki kod örneği özelliği olarak ayarlamayı gösterir <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> <xref:System.ServiceModel.ConcurrencyMode.Multiple> .  
  
```csharp
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.Single)]
public class CalculatorService : ICalculatorConcurrency
{
    ...  
}  
```  
  
## <a name="sessions-interact-with-instancecontext-settings"></a>Oturumlar InstanceContext ayarlarıyla etkileşim kurar  
 Oturumlar ve <xref:System.ServiceModel.InstanceContext> <xref:System.ServiceModel.SessionMode> bir sözleşmede numaralandırma değerinin birleşimine ve <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> hizmet uygulamasındaki özelliğe bağlı olarak, kanallar ve belirli hizmet nesneleri arasındaki ilişkilendirmeyi denetleyen şekilde etkileşime geçin.  
  
 Aşağıdaki tabloda, bir gelen kanalın sonuçları destekleme veya bir hizmetin özelliğin değerlerinin ve özelliğinin bir birleşimi olan oturumları desteklememinde gösterilmektedir <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> .  
  
|InstanceContextMode değeri|<xref:System.ServiceModel.SessionMode.Required>|<xref:System.ServiceModel.SessionMode.Allowed>|<xref:System.ServiceModel.SessionMode.NotAllowed>|  
|-------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|  
|PerCall|-Oturumsuz kanal ile davranış: bir oturum ve <xref:System.ServiceModel.InstanceContext> her çağrı için.<br />-Oturumsuz kanal ile davranış: bir özel durum oluşturulur.|-Oturumsuz kanal ile davranış: bir oturum ve <xref:System.ServiceModel.InstanceContext> her çağrı için.<br />-Oturumsuz kanal: <xref:System.ServiceModel.InstanceContext> her bir çağrı Için bir davranıştır.|-Oturumsuz kanal ile davranış: bir özel durum oluşturulur.<br />-Oturumsuz kanal: <xref:System.ServiceModel.InstanceContext> her bir çağrı Için bir davranıştır.|  
|PerSession|-Oturumsuz kanal ile davranış: bir oturum ve <xref:System.ServiceModel.InstanceContext> her kanal için.<br />-Oturumsuz kanal ile davranış: bir özel durum oluşturulur.|-Oturumsuz kanal ile davranış: bir oturum ve <xref:System.ServiceModel.InstanceContext> her kanal için.<br />-Oturumsuz kanal: <xref:System.ServiceModel.InstanceContext> her bir çağrı Için bir davranıştır.|-Oturumsuz kanal ile davranış: bir özel durum oluşturulur.<br />-Oturumsuz kanal: <xref:System.ServiceModel.InstanceContext> her bir çağrı Için bir davranıştır.|  
|Tek|-Oturumsuz kanal ile davranış: bir oturum ve <xref:System.ServiceModel.InstanceContext> Tüm çağrılar için bir oturum.<br />-Oturumsuz kanal ile davranış: bir özel durum oluşturulur.|-Oturumlı kanal ile davranış: bir oturum ve <xref:System.ServiceModel.InstanceContext> oluşturulan ya da Kullanıcı tarafından belirtilen tek.<br />-Oturumsuz kanal ile davranış: <xref:System.ServiceModel.InstanceContext> oluşturulan veya Kullanıcı tarafından belirtilen tek.|-Oturumsuz kanal ile davranış: bir özel durum oluşturulur.<br />-Oturumsuz kanal ile davranış: <xref:System.ServiceModel.InstanceContext> her oluşturulan tek tekil veya Kullanıcı tarafından belirtilen tek için.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Oturumları Kullanma](../using-sessions.md)
- [Nasıl yapılır: Oturum Gerektiren Bir Hizmet Oluşturma](how-to-create-a-service-that-requires-sessions.md)
- [Nasıl yapılır: Hizmet Örneği Oluşturmayı Denetleme](how-to-control-service-instancing.md)
- [Eşzamanlılık](../samples/concurrency.md)
- [Örnek Oluşturma](../samples/instancing.md)
- [Oturum](../samples/session.md)
