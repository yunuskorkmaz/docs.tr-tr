---
title: Oturumlar, Örnek Oluşturma ve Eşzamanlılık
ms.date: 03/30/2017
ms.assetid: 50797a3b-7678-44ed-8138-49ac1602f35b
ms.openlocfilehash: a7466d819e15f3bfe8def2d9407dcf2c6e0c7346
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184437"
---
# <a name="sessions-instancing-and-concurrency"></a>Oturumlar, Örnek Oluşturma ve Eşzamanlılık
*Oturum,* iki uç nokta arasında gönderilen tüm iletilerin korelasyonunu konur. *Instancing,* kullanıcı tanımlı hizmet nesnelerinin ve bunların <xref:System.ServiceModel.InstanceContext> ilgili nesnelerinin kullanım ömrünü denetlemeyi ifade eder. *Eşzamanlılık,* aynı <xref:System.ServiceModel.InstanceContext> anda çalıştırılabilen iş parçacığı sayısının denetimine verilen terimdir.  
  
 Bu konu, bu ayarları, bunların nasıl kullanılacağını ve aralarındaki çeşitli etkileşimleri açıklar.  
  
## <a name="sessions"></a>Oturumlar  
 Bir hizmet sözleşmesi <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> özelliği <xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>ayarladığında, bu sözleşme tüm çağrıların (diğer bir şekilde çağrıları destekleyen temel ileti alışverişi) aynı konuşmanın bir parçası olması gerektiğini söylüyor. Bir sözleşme, oturumlara izin verdiğini, ancak gerekmediğini belirtirse, istemciler bağlanabilir ve bir oturum kurabilir veya oluşturamaz. Oturum sona erer ve aynı oturum tabanlı kanal üzerinden bir ileti gönderilirse bir özel durum atılır.  
  
 WCF oturumları aşağıdaki temel kavramsal özelliklere sahiptir:  
  
- Bunlar açıkça başlatılır ve arama uygulaması tarafından sonlandırılır.  
  
- Oturum sırasında iletilen iletiler, alındıkları sırayla işlenir.  
  
- Oturumlar, bir ileti grubunu bir konuşmaya ilişkilendirer. Bu bağıntının anlamı bir soyutlamadır. Örneğin, oturum tabanlı bir kanal paylaşılan ağ bağlantısına dayalı iletileri ilişkilendirebilirken, başka bir oturum tabanlı kanal ileti gövdesindeki paylaşılan etikete dayalı iletileri ilişkilendirebilir. Oturumdan türetilebilen özellikler bağıntının doğasına bağlıdır.  
  
- WCF oturumuyla ilişkili genel bir veri deposu yoktur.  
  
 ASP.NET uygulamalarda <xref:System.Web.SessionState.HttpSessionState?displayProperty=nameWithType> sınıfa ve sağladığı işlevselliği biliyorsanız, bu tür oturumlarla WCF oturumları arasındaki aşağıdaki farkları fark edebilirsiniz:  
  
- ASP.NET oturumları her zaman sunucu tarafından başlatılır.  
  
- ASP.NET oturumlar dolaylı olarak sırasızdır.  
  
- ASP.NET oturumları istekler arasında genel bir veri depolama mekanizması sağlar.  
  
 İstemci uygulamaları ve hizmet uygulamaları oturumlarla farklı şekillerde etkileşimde dir. İstemci uygulamaları oturumları başlatır ve oturum içinde gönderilen iletileri alır ve işlenir. Hizmet uygulamaları, ek davranış eklemek için oturumları genişletilebilirlik noktası olarak kullanabilir. Bu, doğrudan özel <xref:System.ServiceModel.InstanceContext> bir örnek bağlam sağlayıcısıyla çalışarak veya uygulayarak yapılır.  
  
## <a name="instancing"></a>Örnek Oluşturma  
 Gelen iletilere yanıt olarak nasıl <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> <xref:System.ServiceModel.InstanceContext> oluşturulduğunu (özelliği kullanarak ayarlanan) instancing davranış. Varsayılan olarak, <xref:System.ServiceModel.InstanceContext> her biri bir kullanıcı tanımlı hizmet nesnesi ile <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> ilişkilidir, bu nedenle (varsayılan durumda) özelliği ayarlama da kullanıcı tanımlı hizmet nesnelerinin instancing denetler. Numaralandırma, <xref:System.ServiceModel.InstanceContextMode> instancing modlarını tanımlar.  
  
 Aşağıdaki instancing modları kullanılabilir:  
  
- <xref:System.ServiceModel.InstanceContextMode.PerCall>: Her <xref:System.ServiceModel.InstanceContext> istemci isteği için yeni bir (ve bu nedenle hizmet nesnesi) oluşturulur.  
  
- <xref:System.ServiceModel.InstanceContextMode.PerSession>: Her <xref:System.ServiceModel.InstanceContext> yeni istemci oturumu için yeni bir (ve bu nedenle hizmet nesnesi) oluşturulur ve bu oturumun ömrü boyunca korunur (bu, oturumları destekleyen bir bağlama gerektirir).  
  
- <xref:System.ServiceModel.InstanceContextMode.Single>: Tek <xref:System.ServiceModel.InstanceContext> bir (ve bu nedenle hizmet nesnesi) uygulamanın ömrü için tüm istemci isteklerini işler.  
  
 Aşağıdaki kod örneği, <xref:System.ServiceModel.InstanceContextMode> <xref:System.ServiceModel.InstanceContextMode.PerSession> bir hizmet sınıfında açıkça ayarlanan varsayılan değeri gösterir.  
  
```csharp  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]
public class CalculatorService : ICalculatorInstance
{
    ...  
}  
```  
  
 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> Özellik ne sıklıkta serbest <xref:System.ServiceModel.InstanceContext> bırakıldığını denetlerken, hizmet nesnesi serbest bırakıldığında özellikleri <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> ve özellikleri <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A?displayProperty=nameWithType> denetler.  
  
### <a name="well-known-singleton-services"></a>Tanınmış Singleton Hizmetleri  
 Tek örnek hizmet nesnelerinde bir varyasyon bazen yararlıdır: bir hizmet nesnesi kendiniz oluşturabilir ve bu nesneyi kullanarak servis ana bilgisayarını oluşturabilirsiniz. Bunu yapmak için, <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> özelliği de <xref:System.ServiceModel.InstanceContextMode.Single> ayarlamanız gerekir veya hizmet ana bilgisayar açıldığında bir özel durum atılır.  
  
 Böyle <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Object%2CSystem.Uri%5B%5D%29?displayProperty=nameWithType> bir hizmet oluşturmak için oluşturucuyu kullanın. Singleton hizmeti tarafından kullanılmak <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer?displayProperty=nameWithType> üzere belirli bir nesne örneği sağlamak istediğinizde özel bir uygulama için bir alternatif sağlar. Hizmet uygulama türünüz zor olduğunda (örneğin, parametresiz bir ortak oluşturucu uygulamıyorsa) bu aşırı yükü kullanabilirsiniz.  
  
 Bu oluşturucuya bir nesne sağlandığında, Windows Communication Foundation (WCF) ile ilgili bazı özelliklerin davranış yapısının farklı çalıştığını unutmayın. Örneğin, singleton nesne örneği sağlandığında aramanın <xref:System.ServiceModel.InstanceContext.ReleaseServiceInstance%2A?displayProperty=nameWithType> hiçbir etkisi yoktur. Benzer şekilde, başka bir örnek yayımetme mekanizması yoksayılır. Özellik <xref:System.ServiceModel.ServiceHost> her zaman tüm <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> işlemler <xref:System.ServiceModel.ReleaseInstanceMode.None?displayProperty=nameWithType> için ayarlanmış gibi olur.  
  
### <a name="sharing-instancecontext-objects"></a>Örnek Bağlam Nesnelerini Paylaşma  
 Ayrıca, bu ilişkilendirmeyi kendiniz gerçekleştirerek hangi <xref:System.ServiceModel.InstanceContext> oturumlu kanalın veya çağrının hangi nesneyle ilişkili olduğunu da denetleyebilirsiniz.  
  
## <a name="concurrency"></a>Eşzamanlılık  
 Eşzamanlılık, herhangi bir <xref:System.ServiceModel.InstanceContext> anda etkin olan iş parçacığı sayısının denetimidir. Bu numaralandırma <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> ile <xref:System.ServiceModel.ConcurrencyMode> kullanılarak kontrol edilir.  
  
 Aşağıdaki üç eşzamanlılık modu kullanılabilir:  
  
- <xref:System.ServiceModel.ConcurrencyMode.Single>: Her örnek bağlamın, örnek bağlamında aynı anda en fazla bir iş parçacığı işleme iletisine sahip olması için izin verilir. Aynı örnek bağlamını kullanmak isteyen diğer iş parçacıkları, özgün iş parçacığı örnek bağlamından çıkana kadar engellemelidir.  
  
- <xref:System.ServiceModel.ConcurrencyMode.Multiple>: Her hizmet örneğinde aynı anda iletileri işleyen birden çok iş parçacığı olabilir. Bu eşzamanlılık modunu kullanmak için hizmet uygulaması iş parçacığı güvenli olmalıdır.  
  
- <xref:System.ServiceModel.ConcurrencyMode.Reentrant>: Her hizmet örneği aynı anda bir iletiyi işler, ancak yeniden giren işlem çağrılarını kabul eder. Hizmet bu çağrıları yalnızca bir WCF istemci nesnesi üzerinden çağırırken kabul eder.  
  
> [!NOTE]
> Birden fazla iş parçacığı güvenli bir şekilde kullanan kodu anlamak ve geliştirmek başarılı bir şekilde yazmak zor olabilir. Kullanmadan <xref:System.ServiceModel.ConcurrencyMode.Multiple> <xref:System.ServiceModel.ConcurrencyMode.Reentrant> veya değer vermeden önce, hizmetinizin bu modlar için uygun şekilde tasarlandığından emin olun. Daha fazla bilgi için bkz. <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>.  
  
 Eşzamanlılık kullanımı instancing modu ile ilgilidir. Her <xref:System.ServiceModel.InstanceContextMode.PerCall> ileti yeni <xref:System.ServiceModel.InstanceContext> bir ileti tarafından işlendiğinden ve bu nedenle, hiçbir zaman birden fazla iş parçacığı <xref:System.ServiceModel.InstanceContext>etkin olmadığından, eşzamanlılık ilgili değildir.  
  
 Aşağıdaki kod örneği özelliği <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> <xref:System.ServiceModel.ConcurrencyMode.Multiple>' niçin ayarlıyor  
  
```csharp
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.Single)]
public class CalculatorService : ICalculatorConcurrency
{
    ...  
}  
```  
  
## <a name="sessions-interact-with-instancecontext-settings"></a>Oturumlar ÖrnekBağlam Ayarlarıyla Etkileşimde  
 Kanallar <xref:System.ServiceModel.InstanceContext> ve belirli hizmet nesneleri arasındaki ilişkiyi kontrol eden, bir sözleşmedeki numaralandırma değerinin <xref:System.ServiceModel.SessionMode> ve hizmet uygulamasındaki <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> özelliğin birleşimine bağlı olarak oturumlar ve etkileşim.  
  
 Aşağıdaki tablo, bir hizmetin <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> özellik ve <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> özellik değerlerinin birleşimi ni göz önüne alındığında oturumları destekleyen veya desteklemeyen bir kanalın sonucunu gösterir.  
  
|InstanceContextMode değeri|<xref:System.ServiceModel.SessionMode.Required>|<xref:System.ServiceModel.SessionMode.Allowed>|<xref:System.ServiceModel.SessionMode.NotAllowed>|  
|-------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|  
|PerCall|- Oturumlu kanal ile davranış: Bir oturum ve <xref:System.ServiceModel.InstanceContext> her çağrı için.<br />- Oturumsuz kanalile davranış: Bir özel durum atılır.|- Oturumlu kanal ile davranış: Bir oturum ve <xref:System.ServiceModel.InstanceContext> her çağrı için.<br />- Oturumsuz kanalile <xref:System.ServiceModel.InstanceContext> davranış: Her arama için bir.|- Oturumlu kanal ile davranış: Bir özel durum atılır.<br />- Oturumsuz kanalile <xref:System.ServiceModel.InstanceContext> davranış: Her arama için bir.|  
|Oturum Başına|- Oturumlu kanal ile davranış: Bir oturum ve <xref:System.ServiceModel.InstanceContext> her kanal için.<br />- Oturumsuz kanalile davranış: Bir özel durum atılır.|- Oturumlu kanal ile davranış: Bir oturum ve <xref:System.ServiceModel.InstanceContext> her kanal için.<br />- Oturumsuz kanalile <xref:System.ServiceModel.InstanceContext> davranış: Her arama için bir.|- Oturumlu kanal ile davranış: Bir özel durum atılır.<br />- Oturumsuz kanalile <xref:System.ServiceModel.InstanceContext> davranış: Her arama için bir.|  
|Tek|- Oturumlu kanal ile davranış: <xref:System.ServiceModel.InstanceContext> Bir oturum ve tüm aramalar için bir.<br />- Oturumsuz kanalile davranış: Bir özel durum atılır.|- Oturumlu kanal ile davranış: Bir oturum ve <xref:System.ServiceModel.InstanceContext> oluşturulan veya kullanıcı tarafından belirtilen singleton için.<br />- Oturumsuz kanalile <xref:System.ServiceModel.InstanceContext> davranış: Oluşturulan veya kullanıcı tarafından belirtilen singleton için bir.|- Oturumlu kanal ile davranış: Bir özel durum atılır.<br />- Oturumsuz kanalile <xref:System.ServiceModel.InstanceContext> davranış: Oluşturulan her singleton veya kullanıcı tarafından belirtilen singleton için bir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Oturumları Kullanma](../../../../docs/framework/wcf/using-sessions.md)
- [Nasıl yapılır: Oturum Gerektiren Bir Hizmet Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
- [Nasıl yapılır: Hizmet Örneği Oluşturmayı Denetleme](../../../../docs/framework/wcf/feature-details/how-to-control-service-instancing.md)
- [Eşzamanlılık](../../../../docs/framework/wcf/samples/concurrency.md)
- [ınstancing](../../../../docs/framework/wcf/samples/instancing.md)
- [Oturum](../../../../docs/framework/wcf/samples/session.md)
