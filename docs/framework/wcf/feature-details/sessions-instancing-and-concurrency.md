---
title: Oturumlar, Örnek Oluşturma ve Eşzamanlılık
ms.date: 03/30/2017
ms.assetid: 50797a3b-7678-44ed-8138-49ac1602f35b
ms.openlocfilehash: 52c9ed5d672ea05fec3333c9fece8b693143d6f3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64586117"
---
# <a name="sessions-instancing-and-concurrency"></a>Oturumlar, Örnek Oluşturma ve Eşzamanlılık
A *oturumu* iki uç nokta arasında gönderilen tüm iletilerin bir ilişki olduğunu. *Örnek oluşturma* hizmeti kullanıcı tanımlı nesneler ve onların ilgili ömrünü denetlemek için başvuran <xref:System.ServiceModel.InstanceContext> nesneleri. *Eşzamanlılık* içinde çalışan iş parçacıklarının sayısını denetlemek için verilen bir terimdir bir <xref:System.ServiceModel.InstanceContext> aynı anda.  
  
 Bu konuda, bu ayarlar açıklanmaktadır. bunları ve bunların arasında çeşitli etkileşimleri kullanma.  
  
## <a name="sessions"></a>Oturumlar  
 Ne zaman bir hizmet sözleşmesini ayarlar <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> özelliğini <xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>, bu sözleşme tüm çağrıları (çağrıları destekleyen diğer bir deyişle, temel alınan ileti alışverişlerinde) aynı konuşmada bir parçası olması gerektiğini belirten. Bir sözleşme oturumları sağlar ancak bir gerektirmez, istemcilerin bağlanabileceği ya da bir veya oturumu belirtirse. Sona ererse ve ileti üzerinde aynı oturum tabanlı kanal bir özel durum gönderilir.  
  
 WCF oturumları aşağıdaki ana kavramsal özelliklere sahiptir:  
  
- Bunlar açıkça başlatılan ve çağıran uygulama tarafından sonlandırıldı.  
  
- Mesajlar oturumu sırasında bunlar alındığı sırayla işlenir.  
  
- Oturumlarının iletiler grubunu bir sohbete ilişkilendirin. Bu bağıntı anlamı bir soyutlamadır. Örneğin, oturum tabanlı bir kanalı oturum tabanlı başka bir kanal iletileri ileti gövdesinde paylaşılan bir etiketi temel bağıntısını ancak bir paylaşılan ağ bağlantısının dayalı iletiler ilişkilendirilebilir. Oturumdan elde edilebilir özellikleri bağıntı niteliğine bağlı.  
  
- Bir WCF oturum ile ilişkili hiçbir genel veri deposu bulunmaktadır.  
  
 Alışkın olduğunuz <xref:System.Web.SessionState.HttpSessionState?displayProperty=nameWithType> sınıfını [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulamalar ve işlevselliği sağlar, bu tür bir oturum ve WCF oturumları arasında aşağıdaki değişiklikler fark edebilirsiniz:  
  
- [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] oturumlarının her zaman sunucu-başlatılır.  
  
- [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] oturumlarının örtük olarak sırasız.  
  
- [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] oturumları istekler genelinde bir genel veri depolama mekanizmasını sağlar.  
  
 Oturumları, istemci uygulamaları ve hizmet uygulamaları farklı şekillerde etkileşim kurun. İstemci uygulamaları oturumlarını başlatmak ve ardından almak ve oturumunda gönderilen iletileri işlemek. Hizmet uygulamaları oturumlarını ek davranış eklemek için bir genişletilebilirlik noktası olarak kullanabilirsiniz. Bu doğrudan birlikte çalışarak yapılır <xref:System.ServiceModel.InstanceContext> veya özel örnek içerik sağlayıcısı uygulaması.  
  
## <a name="instancing"></a>Örnek Oluşturma  
 Örneklemesini davranışı (kullanarak <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> özelliği) denetimleri nasıl <xref:System.ServiceModel.InstanceContext> gelen iletiye yanıt olarak oluşturulur. Varsayılan olarak, her <xref:System.ServiceModel.InstanceContext> bir kullanıcı tanımlı bir hizmet nesneyle ilişkili (varsayılan durumda) bunu ayarı <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliği de denetler örneği kullanıcı tarafından tanımlanan hizmet nesneleri oluşturma. <xref:System.ServiceModel.InstanceContextMode> Örneklemesini modları sabit listesi tanımlar.  
  
 Aşağıdaki örneklemesini modları kullanılabilir:  
  
- <xref:System.ServiceModel.InstanceContextMode.PerCall>: Yeni bir <xref:System.ServiceModel.InstanceContext> (ve bu nedenle nesne hizmet) her istemci isteği için oluşturulur.  
  
- <xref:System.ServiceModel.InstanceContextMode.PerSession>: Yeni bir <xref:System.ServiceModel.InstanceContext> (ve bu nedenle nesne hizmeti) için yeni her istemci oturumu oluşturulur ve bu oturuma (Bu gerektirir oturumları destekleyen bir bağlama) ömrü boyunca saklanır.  
  
- <xref:System.ServiceModel.InstanceContextMode.Single>: Tek bir <xref:System.ServiceModel.InstanceContext> (ve bu nedenle nesne hizmet) uygulama ömrü boyunca tüm istemci isteklerini işler.  
  
 Aşağıdaki kod örneği varsayılan gösterir <xref:System.ServiceModel.InstanceContextMode> değeri <xref:System.ServiceModel.InstanceContextMode.PerSession> üzerinde bir hizmet sınıfı açıkça ayarlanıyor.  
  
```  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]   
public class CalculatorService : ICalculatorInstance   
{   
    ...  
}  
```  
  
 Ve while <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> özellik denetler ne sıklıkta <xref:System.ServiceModel.InstanceContext> yayımlandığı <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> ve <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A?displayProperty=nameWithType> denetim özelliklerini hizmet nesnesi yayınlandığında.  
  
### <a name="well-known-singleton-services"></a>İyi bilinen tekil hizmetin  
 Tek Örnekli hizmet nesneleri bir versiyonu, bazen kullanışlıdır: bir hizmet nesnesi kendiniz oluşturmanız ve bu nesneyi kullanarak hizmet ana bilgisayarını oluşturun. Bunu yapmak için de ayarlamalısınız <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> özelliğini <xref:System.ServiceModel.InstanceContextMode.Single> veya hizmet ana bilgisayarı açıldığında bir özel durum oluşturulur.  
  
 Kullanım <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Object%2CSystem.Uri%5B%5D%29?displayProperty=nameWithType> böyle bir hizmet oluşturmak için oluşturucu. Özel bir uygulama için bir alternatif sağlayan <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer?displayProperty=nameWithType> belirli nesne örneği, tek bir hizmet tarafından kullanılmak üzere sağlamak istediğiniz zaman. Hizmet uygulama türünüzü (örneğin, varsayılan bir parametresiz public Oluşturucu uygulamıyorsa) oluşturmak zor olduğunda, bu aşırı yüklemesini kullanabilirsiniz.  
  
 Bu oluşturucuya bir nesne sağlandığında, Windows Communication Foundation (davranışı depolamasına WCF için) ilgili bazı özellikler farklı iş unutmayın. Örneğin, çağırma <xref:System.ServiceModel.InstanceContext.ReleaseServiceInstance%2A?displayProperty=nameWithType> tek bir nesne örneği sağlandığında hiçbir etkisi olmaz. Benzer şekilde, başka bir örneği yayın mekanizması göz ardı edilir. <xref:System.ServiceModel.ServiceHost> Her zaman davranacağını gibi <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> özelliği <xref:System.ServiceModel.ReleaseInstanceMode.None?displayProperty=nameWithType> tüm işlemler için.  
  
### <a name="sharing-instancecontext-objects"></a>InstanceContext nesneleri paylaşma  
 Hangi oturum kanalı de denetleyebilirsiniz veya çağrı ile ilişkili <xref:System.ServiceModel.InstanceContext> kendinizi bu ilişkiyi gerçekleştirerek nesne.  
  
## <a name="concurrency"></a>Eşzamanlılık  
 Eşzamanlılık denetimi etkin iş parçacığı sayısı, bir <xref:System.ServiceModel.InstanceContext> herhangi bir zamanda. Bu kullanılarak denetlenir <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> ile <xref:System.ServiceModel.ConcurrencyMode> sabit listesi.  
  
 Aşağıdaki üç eşzamanlılık modu kullanılabilir:  
  
- <xref:System.ServiceModel.ConcurrencyMode.Single>: Her örnek bağlamı, en fazla bir iş parçacığının aynı anda örnek bağlamı iletileri işleme izin verilmez. Örnek bağlamı özgün iş parçacığı çıkana kadar aynı örnek bağlamı kullanmak isteyen diğer iş parçacıklarını engellemeniz gerekir.  
  
- <xref:System.ServiceModel.ConcurrencyMode.Multiple>: Her hizmet örneği birden çok iş parçacığı iletileri eşzamanlı olarak işleme sahip olabilir. Hizmet uygulaması bu eşzamanlılık modu kullanmak için iş parçacığı açısından güvenli olması gerekir.  
  
- <xref:System.ServiceModel.ConcurrencyMode.Reentrant>: Her hizmet örneği, tek bir ileti işler, ancak a işlem çağrıları kabul eder. WCF istemci nesnesi okunamayabilir bu hizmet yalnızca bu çağrıları kabul eder.  
  
> [!NOTE]
>  Anlama ve güvenli bir şekilde birden fazla iş parçacığı kullanan kod geliştirme başarıyla yazmak zor olabilir. Kullanmadan önce <xref:System.ServiceModel.ConcurrencyMode.Multiple> veya <xref:System.ServiceModel.ConcurrencyMode.Reentrant> değerleri emin olmak için hizmetinizin bu modları için düzgün şekilde tasarlanmıştır. Daha fazla bilgi için bkz. <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>.  
  
 Eşzamanlılık kullanımını örneklemesini moduna ilişkilidir. İçinde <xref:System.ServiceModel.InstanceContextMode.PerCall> her ileti yeni tarafından işlenir depolamasına, eşzamanlılık ilgili değildir, çünkü <xref:System.ServiceModel.InstanceContext> ve bu nedenle, hiçbir zaman birden çok iş parçacığı etkin olduğu <xref:System.ServiceModel.InstanceContext>.  
  
 Aşağıdaki kod örneği ayarı gösterir <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> özelliğini <xref:System.ServiceModel.ConcurrencyMode.Multiple>.  
  
```  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.Single)]   
public class CalculatorService : ICalculatorConcurrency   
{   
    ...  
}  
```  
  
## <a name="sessions-interact-with-instancecontext-settings"></a>Oturumlarının InstanceContext ayarlarla etkileşim  
 Oturumlar ve <xref:System.ServiceModel.InstanceContext> değerini birleşimi bağlı olarak etkileşimde <xref:System.ServiceModel.SessionMode> sözleşme numaralandırmada ve <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> Kanallar ve özel arasındaki ilişkiyi denetleyen hizmet uygulaması özelliği Hizmet nesneleri.  
  
 Aşağıdaki tabloda bir gelen kanal oturumları destekleyen veya değerleri birleşimi bir hizmet verilen oturumları desteklemediğinden sonucunu gösterir <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> özelliği ve <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> özelliği.  
  
|InstanceContextMode değeri|<xref:System.ServiceModel.SessionMode.Required>|<xref:System.ServiceModel.SessionMode.Allowed>|<xref:System.ServiceModel.SessionMode.NotAllowed>|  
|-------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|  
|PerCall|-Oturum kanalı ile davranışı: Bir oturum ve <xref:System.ServiceModel.InstanceContext> her çağrı için.<br />-Oturumsuz kanal davranışı: Bir özel durum oluşturulur.|-Oturum kanalı ile davranışı: Bir oturum ve <xref:System.ServiceModel.InstanceContext> her çağrı için.<br />-Oturumsuz kanal davranışı: Bir <xref:System.ServiceModel.InstanceContext> her çağrı için.|-Oturum kanalı ile davranışı: Bir özel durum oluşturulur.<br />-Oturumsuz kanal davranışı: Bir <xref:System.ServiceModel.InstanceContext> her çağrı için.|  
|Değeri PerSession|-Oturum kanalı ile davranışı: Bir oturum ve <xref:System.ServiceModel.InstanceContext> her kanal için.<br />-Oturumsuz kanal davranışı: Bir özel durum oluşturulur.|-Oturum kanalı ile davranışı: Bir oturum ve <xref:System.ServiceModel.InstanceContext> her kanal için.<br />-Oturumsuz kanal davranışı: Bir <xref:System.ServiceModel.InstanceContext> her çağrı için.|-Oturum kanalı ile davranışı: Bir özel durum oluşturulur.<br />-Oturumsuz kanal davranışı: Bir <xref:System.ServiceModel.InstanceContext> her çağrı için.|  
|Tek|-Oturum kanalı ile davranışı: Bir oturum ve bir <xref:System.ServiceModel.InstanceContext> tüm çağrıları için.<br />-Oturumsuz kanal davranışı: Bir özel durum oluşturulur.|-Oturum kanalı ile davranışı: Bir oturum ve <xref:System.ServiceModel.InstanceContext> oluşturulan veya kullanıcı tarafından belirtilen tekli için.<br />-Oturumsuz kanal davranışı: Bir <xref:System.ServiceModel.InstanceContext> oluşturulan veya kullanıcı tarafından belirtilen tekli için.|-Oturum kanalı ile davranışı: Bir özel durum oluşturulur.<br />-Oturumsuz kanal davranışı: Bir <xref:System.ServiceModel.InstanceContext> oluşturulan her tekil veya kullanıcı tarafından belirtilen tekli için.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Oturumları Kullanma](../../../../docs/framework/wcf/using-sessions.md)
- [Nasıl yapılır: Oturumlarının gerektiren bir hizmet oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
- [Nasıl yapılır: Hizmet örneği oluşturmayı denetleme](../../../../docs/framework/wcf/feature-details/how-to-control-service-instancing.md)
- [Eşzamanlılık](../../../../docs/framework/wcf/samples/concurrency.md)
- [Örnek Oluşturma](../../../../docs/framework/wcf/samples/instancing.md)
- [Oturum](../../../../docs/framework/wcf/samples/session.md)
