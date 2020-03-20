---
title: Gönderme İşlemleri için Önbellek Paylaşımı Düzeylerini Değiştirme
ms.date: 03/30/2017
ms.assetid: 03926a64-753d-460e-ac06-2a4ff8e1bbf5
ms.openlocfilehash: 101aab98a7d34ad45ad29efbe252cff0814ca290
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185390"
---
# <a name="changing-the-cache-sharing-levels-for-send-activities"></a>Gönderme İşlemleri için Önbellek Paylaşımı Düzeylerini Değiştirme
Uzantı, <xref:System.ServiceModel.Activities.SendMessageChannelCache> ileti etkinliklerini kullanarak <xref:System.ServiceModel.Activities.Send> hizmet bitiş noktalarına ileti gönderen iş akışları için önbellek paylaşım düzeylerini, kanal fabrika önbelleğinin ayarlarını ve kanal önbelleğinin ayarlarını özelleştirmenize olanak tanır. Bu iş akışları genellikle istemci iş akışlarıdır ancak içinde barındırılan iş akışı Hizmetleri ayrıca olabilir bir <xref:System.ServiceModel.WorkflowServiceHost>. Kanal fabrika önbelleği önbelleğe alınmış <xref:System.ServiceModel.ChannelFactory%601> nesneler içerir. Kanal önbelleği önbelleğe alınmış kanallar içerir.  
  
> [!NOTE]
> İş akışları, <xref:System.ServiceModel.Activities.Send> ileti veya parametre göndermek için ileti etkinliklerini kullanabilir. <xref:System.ServiceModel.Channels.IRequestChannel> İş akışı çalışma süresi, bir <xref:System.ServiceModel.Activities.ReceiveReply> <xref:System.ServiceModel.Activities.Send> etkinlikle etkinlik kullandığınızda ve bir <xref:System.ServiceModel.Channels.IOutputChannel> <xref:System.ServiceModel.Activities.Send> etkinlik kullandığınızda (hayır) <xref:System.ServiceModel.Activities.ReceiveReply>tür kanalları oluşturan önbelleğe kanal fabrikaları ekler.  
  
## <a name="the-cache-sharing-levels"></a>Önbellek Paylaşım Düzeyleri  
 Varsayılan olarak, ileti etkinlikleri tarafından <xref:System.ServiceModel.WorkflowServiceHost> kullanılan önbellek <xref:System.ServiceModel.Activities.Send> tarafından barındırılan bir iş akışında <xref:System.ServiceModel.WorkflowServiceHost> (ana bilgisayar düzeyinde önbelleğe alma) tüm iş akışı örnekleri nde paylaşılır. Tarafından barındırılmadığında bir istemci iş akışı için bir <xref:System.ServiceModel.WorkflowServiceHost>, önbelleğe yalnızca (örnek düzeyi önbelleğe alma) iş akışı örneği için kullanılabilir. Önbellek, güvenli olmayan <xref:System.ServiceModel.Activities.Send> önbelleğe alma etkinleştirilmedikçe yalnızca yapılandırmada tanımlanan uç noktaları kullanmayan etkinlikler için kullanılabilir.  
  
 İş akışındaki etkinlikler ve bunların <xref:System.ServiceModel.Activities.Send> önerilen kullanımı için kullanılabilen farklı önbellek paylaşım düzeyleri şunlardır:  
  
- **Ana Bilgisayar Düzeyi**: Ana bilgisayar paylaşım düzeyinde önbellek yalnızca iş akışı hizmeti ana bilgisayarda barındırılan iş akışı örnekleri için kullanılabilir. Önbellek, iş akışı hizmeti ana bilgisayarları arasında işlem genişliğinde bir önbellekte de paylaşılabilir.  
  
- **Örnek Düzeyi**: Örnek paylaşım düzeyinde, önbellek ömrü boyunca belirli bir iş akışı örneği için kullanılabilir, ancak önbellek diğer iş akışı örnekleri için kullanılamaz.  
  
- **Önbellek Yok**: Yapılandırmada tanımlanan uç noktaları kullanan bir iş akışınız varsa önbellek varsayılan olarak kapatılır. Bu durumda önbelleği kapalı tutmanın güvenli olmadığı için de önerilir. Örneğin, her gönderi için farklı bir kimlik (farklı kimlik bilgileri veya kimliğe bürünme kullanımı) gerekiyorsa.  
  
## <a name="changing-the-cache-sharing-level-for-a-client-workflow"></a>İstemci İş Akışı için Önbellek Paylaşım Düzeyini Değiştirme  
 Önbellek paylaşımını istemci iş akışında ayarlamak için, <xref:System.ServiceModel.Activities.SendMessageChannelCache> istenen iş akışı örnekleri kümesine uzantı olarak sınıfın bir örneğini ekleyin. Bu, önbelleğin tüm iş akışı örnekleri arasında paylaşılmasıyla sonuçlanır. Aşağıdaki kod örnekleri, bu adımların nasıl gerçekleştirileceğimi gösterir.  
  
 İlk olarak, tür <xref:System.ServiceModel.Activities.SendMessageChannelCache>bir örnek bildirin.  
  
```csharp  
// Create an instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension =  
    new SendMessageChannelCache();  
```  
  
 Ardından, önbellek uzantısını her istemci iş akışı örneğine ekleyin.  
  
```csharp
WorkflowApplication clientInstance1 = new WorkflowApplication(new clientWorkflow1());  
WorkflowApplication clientInstance2 = new WorkflowApplication(new clientWorkflow2());  
  
// Share the cache extension object
  
clientInstance1.Extensions.Add(sharedChannelCacheExtension);  
clientInstance2.Extensions.Add(sharedChannelCacheExtension);  
```  
  
## <a name="changing-the-cache-sharing-level-for-a-hosted-workflow-service"></a>Barındırılan İş Akışı Hizmeti için Önbellek Paylaşım Düzeyini Değiştirme  
 Barındırılan bir iş akışı hizmetinde önbellek paylaşımını <xref:System.ServiceModel.Activities.SendMessageChannelCache> ayarlamak için, sınıfın bir örneğini tüm iş akışı hizmeti ana bilgisayarlarına uzantı olarak ekleyin. Bu, önbelleğin tüm iş akışı hizmeti ana bilgisayarlarında paylaşılmasıyla sonuçlanır. Aşağıdaki kod örnekleri, bu adımları gerçekleştirmek için gösterir.  
  
 İlk olarak, sınıf <xref:System.ServiceModel.Activities.SendMessageChannelCache> düzeyinde bir tür örneği bildirin.  
  
```csharp  
// Create static instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension = new  
    SendMessageChannelCache();  
```  
  
 Ardından, her iş akışı hizmeti ana bilgisayarı için statik önbellek uzantısı ekleyin.  
  
```csharp  
WorkflowServiceHost host1 = new WorkflowServiceHost(new serviceWorkflow1(), new Uri(baseAddress1));  
WorkflowServiceHost host2 = new WorkflowServiceHost(new serviceWorkflow2(), new Uri(baseAddress2));  
  
// Share the static cache to get an AppDomain level cache.  
host1.WorkflowExtensions.Add(sharedChannelCacheExtension);  
host2.WorkflowExtensions.Add(sharedChannelCacheExtension);  
```  
  
 Barındırılan iş akışı hizmetindeki önbellek paylaşımını örnek `Func<SendMessageChannelCache>` düzeyine ayarlamak için, iş akışı hizmeti ana bilgisayarının uzantısı olarak bir temsilci ekleyin <xref:System.ServiceModel.Activities.SendMessageChannelCache> ve bu temsilciyi sınıfın yeni bir örneğini anında atan koda atayın. Bu, iş akışı hizmet ana bilgisayarındaki tüm iş akışı örnekleri tarafından paylaşılan tek bir önbellek yerine her iş akışı örneği için farklı bir önbellek sağlar. Aşağıdaki kod örneği, temsilcinin işaret ettiği uzantıyı <xref:System.ServiceModel.Activities.SendMessageChannelCache> doğrudan tanımlamak için bir lambda ifadesi kullanarak bunu nasıl başarabilirsinizi gösterir.  
  
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
  
## <a name="customizing-cache-settings"></a>Önbellek Ayarlarını Özelleştirme  
 Kanal fabrika önbelleği ve kanal önbelleği için önbellek ayarlarını özelleştirebilirsiniz. Önbellek ayarları <xref:System.ServiceModel.Activities.ChannelCacheSettings> sınıfta tanımlanır. Sınıf, <xref:System.ServiceModel.Activities.SendMessageChannelCache> kanal fabrika önbelleği için varsayılan önbellek ayarlarını ve parametresiz oluşturucusundaki kanal önbelleği'ni tanımlar. Aşağıdaki tabloda, her önbellek türü için bu önbellek ayarlarının varsayılan değerleri listelenir.  
  
|Ayarlar|LeaseTimeout (dk)|Boşta Zaman (dk)|MaxItemsInÖnbellek|  
|-|-|-|-|  
|Fabrika Önbellek Varsayılan|TimeSpan.MaxValue|2|16|  
|Kanal Önbelleği Varsayılan|5|2|16|  
  
 Fabrika önbelleği ve kanal önbelleği ayarlarını özelleştirmek <xref:System.ServiceModel.Activities.SendMessageChannelCache> için, parametreli <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> oluşturucuyu kullanarak <xref:System.ServiceModel.Activities.ChannelCacheSettings> sınıfı anında anlayın `factorySettings` ve `channelSettings` özel değerlere sahip yeni bir örneğini her bir ve parametrelere geçirin. Ardından, iş akışı hizmeti ana bilgisayarı veya iş akışı örneğine uzantı olarak bu sınıfın yeni örneğini ekleyin. Aşağıdaki kod örneği, iş akışı örneği için bu adımların nasıl gerçekleştirilileceğigösterilmektedir.  
  
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
  
 İş akışı hizmetinizin yapılandırmada tanımlanan uç noktaları olduğunda önbelleğe alma sağlamak <xref:System.ServiceModel.Activities.SendMessageChannelCache> için, <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> `allowUnsafeCaching` `true`parametre olarak ayarlanmış parametreli oluşturucuyu kullanarak sınıfı anında Ardından, iş akışı hizmeti ana bilgisayarı veya iş akışı örneğine uzantı olarak bu sınıfın yeni örneğini ekleyin. Aşağıdaki kod örneği, iş akışı örneği için önbelleğe almanın nasıl etkinleştirileceğinizi gösterir.  
  
```csharp  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache{ AllowUnsafeCaching = true };  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 Kanal fabrikaları ve kanallar için önbelleği tamamen devre dışı kakmak için kanal fabrika önbelleğini devre dışı edin. Bunu yapmak, kanallar ilgili kanal fabrikalarına ait olduğundan kanal önbelleğini de kapatır. Kanal fabrika önbelleğini devre dışı `factorySettings` katlamak için <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> parametreyi 0 <xref:System.ServiceModel.Activities.ChannelCacheSettings> <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> değeri olan bir örneğe başlatılan yapıya geçirin. Aşağıdaki kod örneği bunu gösterir.  
  
```csharp  
// Disable the factory cache. This results in the channel cache to be turned off as well.  
ChannelCacheSettings factorySettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0 };  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings();  
  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache(factorySettings, channelSettings);
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 Yalnızca kanal fabrika önbelleğini kullanmayı ve `channelSettings` parametreyi 0 <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> <xref:System.ServiceModel.Activities.ChannelCacheSettings> <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> değeri olan bir örneğe başlatılan yapıcıya geçirerek kanal önbelleğini devre dışı bırakmayı seçebilirsiniz. Aşağıdaki kod örneği bunu gösterir.  
  
```csharp  
ChannelCacheSettings factorySettings = new ChannelCacheSettings();  
// Disable only the channel cache.  
ChannelCacheSettings channelSettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0};  
  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache(factorySettings, channelSettings);
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 Barındırılan iş akışı hizmetinde, uygulama yapılandırma dosyasında üreteci önbellek ve kanal önbellek ayarları belirtebilirsiniz. Bunu yapmak için üretecini ve kanal önbellek için önbellek ayarlarını içeren bir hizmet davranışını ekleyin ve bu hizmet davranışını hizmetinize ekleyin. Aşağıdaki örnek, özel fabrika önbelleği `MyChannelCacheBehavior` ve kanal önbelleği ayarlarıyla hizmet davranışını içeren bir yapılandırma dosyasının içeriğini gösterir. Bu hizmet davranışı öznitelik aracılığıyla `behaviorConfiguration` hizmete eklenir.  
  
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
