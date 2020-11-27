---
title: Gönderme İşlemleri için Önbellek Paylaşımı Düzeylerini Değiştirme
ms.date: 03/30/2017
ms.assetid: 03926a64-753d-460e-ac06-2a4ff8e1bbf5
ms.openlocfilehash: cbb937ac47c93307db922b28e3df0ea694a77960
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262054"
---
# <a name="changing-the-cache-sharing-levels-for-send-activities"></a>Gönderme İşlemleri için Önbellek Paylaşımı Düzeylerini Değiştirme

<xref:System.ServiceModel.Activities.SendMessageChannelCache>Uzantı, önbellek paylaşım düzeylerini, kanal fabrikası önbelleğinin ayarlarını ve mesajlaşma etkinliklerini kullanarak hizmet uç noktalarına ileti gönderen iş akışları için kanal önbelleğinin ayarlarını özelleştirmenize olanak sağlar <xref:System.ServiceModel.Activities.Send> . Bu iş akışları genellikle istemci iş akışlarıdır ancak içinde barındırılan iş akışı Hizmetleri ayrıca olabilir bir <xref:System.ServiceModel.WorkflowServiceHost>. Kanal fabrikası önbelleğinde önbelleğe alınmış <xref:System.ServiceModel.ChannelFactory%601> nesneler bulunur. Kanal önbelleği, önbelleğe alınmış kanalları içerir.  
  
> [!NOTE]
> İş akışları ileti <xref:System.ServiceModel.Activities.Send> ya da parametre göndermek için mesajlaşma etkinliklerini kullanabilir. İş akışı çalışma zamanı, etkinlik ile bir etkinlik kullandığınızda <xref:System.ServiceModel.Channels.IRequestChannel> <xref:System.ServiceModel.Activities.ReceiveReply> <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Channels.IOutputChannel> yalnızca bir <xref:System.ServiceModel.Activities.Send> etkinlik (Hayır) kullandığınızda, bir <xref:System.ServiceModel.Activities.ReceiveReply> türü kanallar oluşturan önbelleğe kanal fabrikaları ekler.  
  
## <a name="the-cache-sharing-levels"></a>Önbellek paylaşım düzeyleri  

 Varsayılan olarak, <xref:System.ServiceModel.WorkflowServiceHost> ileti etkinlikleri tarafından kullanılan önbellek tarafından barındırılan bir iş akışında <xref:System.ServiceModel.Activities.Send> , <xref:System.ServiceModel.WorkflowServiceHost> (konak düzeyinde önbelleğe alma) içindeki tüm iş akışı örnekleri arasında paylaşılır. Tarafından barındırılmadığında bir istemci iş akışı için bir <xref:System.ServiceModel.WorkflowServiceHost>, önbelleğe yalnızca (örnek düzeyi önbelleğe alma) iş akışı örneği için kullanılabilir. Önbellek yalnızca, <xref:System.ServiceModel.Activities.Send> güvenli olmayan önbelleğe alma etkin olmadığı takdirde yapılandırmada tanımlanan uç noktaları kullanmayan etkinliklerde kullanılabilir.  
  
 Aşağıda, bir iş akışındaki etkinlikler için kullanılabilen farklı önbellek paylaşım düzeyleri <xref:System.ServiceModel.Activities.Send> ve bunların önerilen kullanımları verilmiştir:  
  
- **Konak düzeyi**: konak paylaşım düzeyinde, önbellek yalnızca iş akışı hizmeti ana bilgisayarında barındırılan iş akışı örnekleri için kullanılabilir. Bir önbellek, işlem genelinde bir önbellekte iş akışı hizmeti konakları arasında da paylaşılabilir.  
  
- **Örnek düzeyi**: örnek paylaşım düzeyinde önbellek, süresi boyunca belirli bir iş akışı örneği tarafından kullanılabilir, ancak önbellek diğer iş akışı örnekleri için kullanılamaz.  
  
- **Önbellek yok**: yapılandırmada tanımlanan uç noktaları kullanan bir iş akışınız varsa, önbellek varsayılan olarak kapalıdır. Bu durumda, önbelleğin açık olması güvenli hale getirildiğinden önbelleğin kapalı tutulması de önerilir. Örneğin, her gönderme için farklı bir kimlik (farklı kimlik bilgileri veya kimliğe bürünme kullanılarak) gerekliyse.  
  
## <a name="changing-the-cache-sharing-level-for-a-client-workflow"></a>Istemci Iş akışı için önbellek paylaşım düzeyini değiştirme  

 Bir istemci iş akışında önbellek paylaşımını ayarlamak için, <xref:System.ServiceModel.Activities.SendMessageChannelCache> istenen iş akışı örnekleri kümesine uzantı olarak sınıfın bir örneğini ekleyin. Bu, önbelleğin tüm iş akışı örnekleri arasında paylaşılmasına neden olur. Aşağıdaki kod örnekleri, bu adımların nasıl gerçekleştirileceğini gösterir.  
  
 İlk olarak, türünün bir örneğini bildirin <xref:System.ServiceModel.Activities.SendMessageChannelCache> .  
  
```csharp  
// Create an instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension =  
    new SendMessageChannelCache();  
```  
  
 Ardından, her bir istemci iş akışı örneğine önbellek uzantısını ekleyin.  
  
```csharp
WorkflowApplication clientInstance1 = new WorkflowApplication(new clientWorkflow1());  
WorkflowApplication clientInstance2 = new WorkflowApplication(new clientWorkflow2());  
  
// Share the cache extension object
  
clientInstance1.Extensions.Add(sharedChannelCacheExtension);  
clientInstance2.Extensions.Add(sharedChannelCacheExtension);  
```  
  
## <a name="changing-the-cache-sharing-level-for-a-hosted-workflow-service"></a>Barındırılan Iş akışı hizmeti için önbellek paylaşım düzeyini değiştirme  

 Barındırılan iş akışı hizmetinde önbellek paylaşımını ayarlamak için, sınıfın bir örneğini bir <xref:System.ServiceModel.Activities.SendMessageChannelCache> uzantı olarak tüm iş akışı hizmeti konaklarına ekleyin. Bu, önbelleğin tüm iş akışı hizmeti konakları arasında paylaşılmasına neden olur. Aşağıdaki kod örnekleri, bu adımları gerçekleştirmek için gösterir.  
  
 İlk olarak, sınıf düzeyinde türünün bir örneğini bildirin <xref:System.ServiceModel.Activities.SendMessageChannelCache> .  
  
```csharp  
// Create static instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension = new  
    SendMessageChannelCache();  
```  
  
 Sonra, her iş akışı hizmeti konağına statik önbellek uzantısını ekleyin.  
  
```csharp  
WorkflowServiceHost host1 = new WorkflowServiceHost(new serviceWorkflow1(), new Uri(baseAddress1));  
WorkflowServiceHost host2 = new WorkflowServiceHost(new serviceWorkflow2(), new Uri(baseAddress2));  
  
// Share the static cache to get an AppDomain level cache.  
host1.WorkflowExtensions.Add(sharedChannelCacheExtension);  
host2.WorkflowExtensions.Add(sharedChannelCacheExtension);  
```  
  
 Barındırılan bir iş akışı hizmetindeki önbellek paylaşımını örnek düzeyine ayarlamak için, bir `Func<SendMessageChannelCache>` temsilciyi iş akışı hizmet konağına uzantı olarak ekleyin ve bu temsilciyi, sınıfının yeni bir örneğini örnekleyen koda atayın <xref:System.ServiceModel.Activities.SendMessageChannelCache> . Bu, iş akışı hizmet ana bilgisayarındaki tüm iş akışı örnekleri tarafından paylaşılan tek bir önbellek yerine her bir iş akışı örneği için farklı bir önbellekte sonuçlanır. Aşağıdaki kod örneği <xref:System.ServiceModel.Activities.SendMessageChannelCache> , temsilcinin işaret ettiği uzantıyı doğrudan tanımlamak için bir lambda ifadesi kullanarak bunu nasıl elde ettiğini gösterir.  
  
```csharp
serviceHost.WorkflowExtensions.Add(() => new SendMessageChannelCache  
{  
    // Use FactorySettings property to add custom factory cache settings.  
    FactorySettings = new ChannelCacheSettings
    { MaxItemsInCache = 5, },  
    // Use ChannelSettings property to add custom channel cache settings.  
    ChannelSettings = new ChannelCacheSettings
    { MaxItemsInCache = 10 },  
});  
```  
  
## <a name="customizing-cache-settings"></a>Önbellek ayarlarını özelleştirme  

 Kanal fabrikası önbelleği ve kanal önbelleği için önbellek ayarlarını özelleştirebilirsiniz. Önbellek ayarları <xref:System.ServiceModel.Activities.ChannelCacheSettings> sınıfta tanımlanmıştır. <xref:System.ServiceModel.Activities.SendMessageChannelCache>Sınıfı, kanal fabrikası önbelleğinin varsayılan önbellek ayarlarını ve parametresiz oluşturucusunda kanal önbelleğini tanımlar. Aşağıdaki tabloda her önbellek türü için bu önbellek ayarlarının varsayılan değerleri listelenmektedir.  
  
|Ayarlar|LeaseTimeout (dk)|IdleTimeout (dk)|MaxItemsInCache|  
|-|-|-|-|  
|Fabrika önbelleği varsayılanı|TimeSpan. MaxValue|2|16|  
|Kanal önbelleği varsayılanı|5|2|16|  
  
 Fabrika önbelleğini ve kanal önbelleği ayarlarını özelleştirmek için <xref:System.ServiceModel.Activities.SendMessageChannelCache> parametreli oluşturucuyu kullanarak sınıfı örneğini oluşturun <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> ve <xref:System.ServiceModel.Activities.ChannelCacheSettings> her bir ve parametresi için özel değerleri olan yeni bir örneğini geçirin `factorySettings` `channelSettings` . Sonra, bu sınıfın yeni örneğini bir iş akışı hizmet konağına veya bir iş akışı örneğine uzantı olarak ekleyin. Aşağıdaki kod örneği, bir iş akışı örneği için bu adımların nasıl gerçekleştirileceğini gösterir.  
  
```csharp  
ChannelCacheSettings factorySettings = new ChannelCacheSettings{  
                        MaxItemsInCache = 5,
                        IdleTimeout = TimeSpan.FromMinutes(5),
                        LeaseTimeout = TimeSpan.FromMinutes(20)};  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings{  
                        MaxItemsInCache = 5,
                        IdleTimeout = TimeSpan.FromMinutes(2),  
                        LeaseTimeout = TimeSpan.FromMinutes(10) };  
  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache(factorySettings, channelSettings);  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 İş akışı hizmetiniz yapılandırmada tanımlı uç noktalara sahip olduğunda önbelleğe almayı etkinleştirmek için, <xref:System.ServiceModel.Activities.SendMessageChannelCache> <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> `allowUnsafeCaching` parametresi olarak ayarlanmış parametreli oluşturucuyu kullanarak sınıfı örneğini oluşturun `true` . Sonra, bu sınıfın yeni örneğini bir iş akışı hizmet konağına veya bir iş akışı örneğine uzantı olarak ekleyin. Aşağıdaki kod örneğinde, bir iş akışı örneği için önbelleğe almanın nasıl etkinleştirileceği gösterilmektedir.  
  
```csharp  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache{ AllowUnsafeCaching = true };  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 Kanal fabrikaları ve kanallar için önbelleği tamamen devre dışı bırakmak için, kanal fabrikası önbelleğini devre dışı bırakın. Bunun yapılması, kanalların ilgili kanal fabrikalarına ait olduğu için kanal önbelleğini de kapatır. Kanal fabrikası önbelleğini devre dışı bırakmak için, `factorySettings` parametresini <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> <xref:System.ServiceModel.Activities.ChannelCacheSettings> 0 değerine sahip bir örneğe başlatılan oluşturucuya geçirin <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> . Aşağıdaki kod örneği bunu gösterir.  
  
```csharp  
// Disable the factory cache. This results in the channel cache to be turned off as well.  
ChannelCacheSettings factorySettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0 };  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings();  
  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache(factorySettings, channelSettings);
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 Yalnızca kanal fabrikası önbelleğini kullanmayı seçebilir ve `channelSettings` parametresini <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> <xref:System.ServiceModel.Activities.ChannelCacheSettings> 0 değerine sahip bir örneğe başlatılan oluşturucuya geçirerek kanal önbelleğini devre dışı bırakabilirsiniz <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> . Aşağıdaki kod örneği bunu gösterir.  
  
```csharp  
ChannelCacheSettings factorySettings = new ChannelCacheSettings();  
// Disable only the channel cache.  
ChannelCacheSettings channelSettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0};  
  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache(factorySettings, channelSettings);
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 Barındırılan iş akışı hizmetinde, uygulama yapılandırma dosyasında üreteci önbellek ve kanal önbellek ayarları belirtebilirsiniz. Bunu yapmak için üretecini ve kanal önbellek için önbellek ayarlarını içeren bir hizmet davranışını ekleyin ve bu hizmet davranışını hizmetinize ekleyin. Aşağıdaki örnek, `MyChannelCacheBehavior` özel fabrika önbelleği ve kanal önbelleği ayarları ile hizmet davranışını içeren bir yapılandırma dosyasının içeriğini gösterir. Bu hizmet davranışı, özelliği aracılığıyla hizmete eklenir `behaviorConfiguration` .  
  
```xml  
<configuration>
  <system.serviceModel>  
    <!-- List of other config sections here -->
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="MyChannelCacheBehavior">  
          <sendMessageChannelCache allowUnsafeCaching ="false" >  
            <!-- Control only the host level settings -->
            <factorySettings maxItemsInCache = "8" idleTimeout = "00:05:00" leaseTimeout="10:00:00" />  
            <channelSettings maxItemsInCache = "32" idleTimeout = "00:05:00" leaseTimeout="00:06:00" />  
          </sendMessageChannelCache>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="MyService" behaviorConfiguration="MyChannelCacheBehavior" />  
    </services>  
  </system.serviceModel>  
</configuration>  
```
