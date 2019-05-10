---
title: Gönderme İşlemleri için Önbellek Paylaşımı Düzeylerini Değiştirme
ms.date: 03/30/2017
ms.assetid: 03926a64-753d-460e-ac06-2a4ff8e1bbf5
ms.openlocfilehash: 1561d053dc04bbea18f4d6cb43399c2c625d5da1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614856"
---
# <a name="changing-the-cache-sharing-levels-for-send-activities"></a>Gönderme İşlemleri için Önbellek Paylaşımı Düzeylerini Değiştirme
<xref:System.ServiceModel.Activities.SendMessageChannelCache> Uzantısı düzeyleri, kanal üreteci önbellek ayarlarını paylaşımı önbellek özelleştirmenize olanak sağlar ve ileti göndermek için hizmet uç noktaları kullanarak iş akışları için kanal ayarlarıyla önbelleğe <xref:System.ServiceModel.Activities.Send> Mesajlaşma etkinlikleri. Bu iş akışları genellikle istemci iş akışlarıdır ancak içinde barındırılan iş akışı Hizmetleri ayrıca olabilir bir <xref:System.ServiceModel.WorkflowServiceHost>. Kanal üreteci önbellek içeren önbelleğe alınmış <xref:System.ServiceModel.ChannelFactory%601> nesneleri. Kanal önbellek önbelleğe alınmış kanalları içerir.  
  
> [!NOTE]
>  İş akışları kullanabilirsiniz <xref:System.ServiceModel.Activities.Send> Mesajlaşma iletileri ya da parametreler göndermek için etkinlikleri. İş akışı çalışma zamanı kanal fabrikaları kanal türü oluşturan önbelleğe ekler <xref:System.ServiceModel.Channels.IRequestChannel> kullandığınızda bir <xref:System.ServiceModel.Activities.ReceiveReply> etkinliği ile bir <xref:System.ServiceModel.Activities.Send> etkinliği ve bir <xref:System.ServiceModel.Channels.IOutputChannel> kullanırken yalnızca bir <xref:System.ServiceModel.Activities.Send> etkinlik (hiçbir <xref:System.ServiceModel.Activities.ReceiveReply>).  
  
## <a name="the-cache-sharing-levels"></a>Önbellek paylaşımı düzeylerini  
 Varsayılan olarak, bir iş akışı tarafından barındırılan bir <xref:System.ServiceModel.WorkflowServiceHost> tarafından kullanılan önbellek <xref:System.ServiceModel.Activities.Send> Mesajlaşma etkinlikleriyle iş akışı durumlarda arasında paylaşılır <xref:System.ServiceModel.WorkflowServiceHost> (ana bilgisayar önbelleğe alma düzeyi). Tarafından barındırılmadığında bir istemci iş akışı için bir <xref:System.ServiceModel.WorkflowServiceHost>, önbelleğe yalnızca (örnek düzeyi önbelleğe alma) iş akışı örneği için kullanılabilir. Önbelleği yalnızca kullanılabilir <xref:System.ServiceModel.Activities.Send> bitiş noktaları yapılandırmasında tanımlandığı, güvenli olmayan önbelleğe almanın etkin olup sürece kullanmayan etkinlikler.  
  
 Aşağıdakiler için kullanılabilir düzeyleri paylaşımı farklı bir önbellek, <xref:System.ServiceModel.Activities.Send> etkinlikleri iş akışı ve önerilen kullanımları:  
  
- **Konak düzeyinde**: Konak paylaşım düzeyi, önbelleğe yalnızca iş akışı hizmeti ana bilgisayarında barındırılan iş akışı örnekleri için kullanılabilir. Bir önbellek, ayrıca iş akışı hizmeti konak işlem genelinde önbelleğinde arasında paylaşılabilir.  
  
- **Örnek düzeyi**: Önbellek paylaşım düzeyi örneğin ömrü boyunca belirli bir iş akışı örneği için kullanılabilir ancak önbelleği için diğer iş akışı örnekleri kullanılabilir değil.  
  
- **Önbelleğin**: Bitiş noktaları yapılandırmasında tanımlandığı kullanan bir iş akışı varsa önbelleği varsayılan olarak kapalıdır. Ayrıca, açma güvensiz olabilir çünkü bu durumda kapalı önbellek tutmanız önerilir. Örneğin, farklı bir kimlik (farklı kimlik bilgileri veya kimliğe bürünme kullanma) her gönderme için gereklidir.  
  
## <a name="changing-the-cache-sharing-level-for-a-client-workflow"></a>Bir istemci iş akışı için paylaşım düzeyi önbellek değiştirme  
 Bir istemci iş akışında paylaşımı önbellek ayarlamak için bir örneğini ekleme <xref:System.ServiceModel.Activities.SendMessageChannelCache> istenen iş akışı örnekleri kümesi için bir genişletme olarak sınıf. Bu, tüm iş akışı örnekleri arasında önbellek paylaşımı ile sonuçlanır. Aşağıdaki kod örnekleri, bu adımların nasıl gerçekleştirileceğini gösterir.  
  
 İlk olarak, türün bir örneğini bildirmeniz <xref:System.ServiceModel.Activities.SendMessageChannelCache>.  
  
```csharp  
// Create an instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension =  
    new SendMessageChannelCache();  
```  
  
 Ardından, her istemci iş akışı örneği için önbellek uzantısı ekleyin.  
  
```csharp 
WorkflowApplication clientInstance1 = new WorkflowApplication(new clientWorkflow1());  
WorkflowApplication clientInstance2 = new WorkflowApplication(new clientWorkflow2());  
  
// Share the cache extension object   
  
clientInstance1.Extensions.Add(sharedChannelCacheExtension);  
clientInstance2.Extensions.Add(sharedChannelCacheExtension);  
```  
  
## <a name="changing-the-cache-sharing-level-for-a-hosted-workflow-service"></a>Paylaşım düzeyi barındırılan iş akışı hizmeti için önbellek değiştirme  
 Bir barındırılan iş akışı hizmetinde paylaşımı önbellek ayarlamak için bir örneğini ekleme <xref:System.ServiceModel.Activities.SendMessageChannelCache> tüm iş akışı hizmet konakları için bir genişletme olarak sınıf. Bu, tüm iş akışı hizmeti konak arasında önbellek paylaşımı ile sonuçlanır. Bu adımları gerçekleştirmek için aşağıdaki kod örnekleri göster.  
  
 İlk olarak, türün bir örneğini bildirmeniz <xref:System.ServiceModel.Activities.SendMessageChannelCache> sınıf düzeyinde.  
  
```csharp  
// Create static instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension = new  
    SendMessageChannelCache();  
```  
  
 Ardından, her iş akışı hizmeti konağı için statik önbellek uzantısı ekleyin.  
  
```csharp  
WorkflowServiceHost host1 = new WorkflowServiceHost(new serviceWorkflow1(), new Uri(baseAddress1));  
WorkflowServiceHost host2 = new WorkflowServiceHost(new serviceWorkflow2(), new Uri(baseAddress2));  
  
// Share the static cache to get an AppDomain level cache.  
host1.WorkflowExtensions.Add(sharedChannelCacheExtension);  
host2.WorkflowExtensions.Add(sharedChannelCacheExtension);  
```  
  
 Örnek düzeyi bir barındırılan iş akışı hizmetinde paylaşımı önbellek için ekleyin bir `Func<SendMessageChannelCache>` temsilci iş akışı hizmeti konağı için bir genişletme olarak ve yeni bir örneğini başlatan kodu bu temsilci atama <xref:System.ServiceModel.Activities.SendMessageChannelCache> sınıfı. İş akışı hizmeti konak tüm iş akışı örnekleri tarafından paylaşılan tek bir önbellek yerine her bir ayrı ayrı iş akışı örneği için farklı bir önbellek sonuçlanır. Aşağıdaki kod örneği, doğrudan tanımlamak için bir lambda ifadesi kullanarak bunu başarmanın gösterilmektedir <xref:System.ServiceModel.Activities.SendMessageChannelCache> temsilci işaret uzantısı.  
  
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
 Kanal üreteci önbellek ve kanal önbellek için önbellek ayarlarını özelleştirebilirsiniz. Önbellek ayarları tanımlanan <xref:System.ServiceModel.Activities.ChannelCacheSettings> sınıfı. <xref:System.ServiceModel.Activities.SendMessageChannelCache> Sınıf varsayılan oluşturucusuna varsayılan kanal üreteci önbellek ve kanal önbellek için önbellek ayarlarını tanımlar. Aşağıdaki tabloda, bu önbelleğin her türü için önbellek ayarları için varsayılan değerleri listelenmektedir.  
  
|Ayarlar|LeaseTimeout (min)|IdleTimeout (min)|MaxItemsInCache|  
|-|-|-|-|  
|Önbellek varsayılan fabrika|TimeSpan.MaxValue|2|16|  
|Kanal önbellek varsayılan|5|2|16|  
  
 Üreteci önbellek ve kanal önbellek ayarlarını özelleştirmek için örneği <xref:System.ServiceModel.Activities.SendMessageChannelCache> parametreli bir kurucu kullanarak <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> ve yeni bir örneğini geçirin <xref:System.ServiceModel.Activities.ChannelCacheSettings> her biri için özel değerlerle `factorySettings` ve `channelSettings` Parametreler. Ardından, bu sınıfın yeni bir örneğini bir iş akışı hizmeti konak ya da bir iş akışı örneği bir uzantısı olarak ekleyin. Aşağıdaki kod örneği, bir iş akışı örneği için bu adımları gösterilmektedir.  
  
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
  
 İş akışı hizmetinizi bitiş noktaları yapılandırmasında tanımlandığı sahip olduğunda önbelleğe almayı etkinleştirmek için örneği <xref:System.ServiceModel.Activities.SendMessageChannelCache> parametreli bir kurucu kullanarak <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> ile `allowUnsafeCaching` parametresini `true`. Ardından, bu sınıfın yeni bir örneğini bir iş akışı hizmeti konak ya da bir iş akışı örneği bir uzantısı olarak ekleyin. Aşağıdaki kod örneği, bir iş akışı örneği için önbelleğe almayı etkinleştirmek gösterilmektedir.  
  
```csharp  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache{ AllowUnsafeCaching = true };  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 Kanal fabrikaları ve kanallar için tamamen önbelleğini devre dışı bırakmak için kanal üreteci önbellek devre dışı bırakın. Kanal tarafından karşılık gelen, kanal fabrikaları sahip olduğu gibi Bunun yapılması kanal önbellek de etkinleştirir. Kanal üreteci önbellek devre dışı bırakmak için geçirmek `factorySettings` parametresi <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> oluşturucusu için başlatılan bir <xref:System.ServiceModel.Activities.ChannelCacheSettings> ile örnek bir <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> 0 değeri. Aşağıdaki kod örneği bunu gösterir.  
  
```csharp  
// Disable the factory cache. This results in the channel cache to be turned off as well.  
ChannelCacheSettings factorySettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0 };  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings();  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);   
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 Yalnızca kanal üreteci önbellek ve kanal önbellek geçirerek devre dışı seçebilirsiniz `channelSettings` parametresi <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> oluşturucusu için başlatılan bir <xref:System.ServiceModel.Activities.ChannelCacheSettings> ile örnek bir <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> 0 değeri. Aşağıdaki kod örneği bunu gösterir.  
  
```csharp  
ChannelCacheSettings factorySettings = new ChannelCacheSettings();  
// Disable only the channel cache.  
ChannelCacheSettings channelSettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0};  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);   
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 Barındırılan iş akışı hizmetinde, uygulama yapılandırma dosyasında üreteci önbellek ve kanal önbellek ayarları belirtebilirsiniz. Bunu yapmak için üretecini ve kanal önbellek için önbellek ayarlarını içeren bir hizmet davranışını ekleyin ve bu hizmet davranışını hizmetinize ekleyin. Aşağıdaki örnek, içeren bir yapılandırma dosyası içeriğini gösterir `MyChannelCacheBehavior` özel üreteci önbellek ve kanal önbellek ayarları ile hizmet davranışı. Bu hizmet davranışını hizmet aracılığıyla eklenen `behaviorConfiguarion` özniteliği.  
  
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
