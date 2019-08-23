---
title: Gönderme İşlemleri için Önbellek Paylaşımı Düzeylerini Değiştirme
ms.date: 03/30/2017
ms.assetid: 03926a64-753d-460e-ac06-2a4ff8e1bbf5
ms.openlocfilehash: 587440bd343513aeff51f1ed0947573fbe612f22
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952584"
---
# <a name="changing-the-cache-sharing-levels-for-send-activities"></a>Gönderme İşlemleri için Önbellek Paylaşımı Düzeylerini Değiştirme
Uzantı, önbellek paylaşım düzeylerini, kanal fabrikası önbelleğinin ayarlarını ve mesajlaşma etkinliklerini kullanarak <xref:System.ServiceModel.Activities.Send> hizmet uç noktalarına ileti gönderen iş akışları için kanal önbelleğinin ayarlarını özelleştirmenize olanak sağlar. <xref:System.ServiceModel.Activities.SendMessageChannelCache> Bu iş akışları genellikle istemci iş akışlarıdır ancak içinde barındırılan iş akışı Hizmetleri ayrıca olabilir bir <xref:System.ServiceModel.WorkflowServiceHost>. Kanal fabrikası önbelleğinde önbelleğe alınmış <xref:System.ServiceModel.ChannelFactory%601> nesneler bulunur. Kanal önbelleği, önbelleğe alınmış kanalları içerir.  
  
> [!NOTE]
> İş akışları ileti <xref:System.ServiceModel.Activities.Send> ya da parametre göndermek için mesajlaşma etkinliklerini kullanabilir. İş akışı çalışma zamanı, etkinlik ile <xref:System.ServiceModel.Channels.IRequestChannel> <xref:System.ServiceModel.Activities.Send> bir etkinlik kullandığınızda ve yalnızca bir <xref:System.ServiceModel.Activities.Send> etkinlik (Hayır <xref:System.ServiceModel.Activities.ReceiveReply>) kullandığınızda <xref:System.ServiceModel.Activities.ReceiveReply> , bir <xref:System.ServiceModel.Channels.IOutputChannel> türü kanallar oluşturan önbelleğe kanal fabrikaları ekler.  
  
## <a name="the-cache-sharing-levels"></a>Önbellek paylaşım düzeyleri  
 Varsayılan olarak, ileti etkinlikleri tarafından <xref:System.ServiceModel.WorkflowServiceHost> <xref:System.ServiceModel.Activities.Send> kullanılan önbellek tarafından barındırılan bir iş akışında, <xref:System.ServiceModel.WorkflowServiceHost> (konak düzeyinde önbelleğe alma) içindeki tüm iş akışı örnekleri arasında paylaşılır. Tarafından barındırılmadığında bir istemci iş akışı için bir <xref:System.ServiceModel.WorkflowServiceHost>, önbelleğe yalnızca (örnek düzeyi önbelleğe alma) iş akışı örneği için kullanılabilir. Önbellek yalnızca, güvenli olmayan önbelleğe <xref:System.ServiceModel.Activities.Send> alma etkin olmadığı takdirde yapılandırmada tanımlanan uç noktaları kullanmayan etkinliklerde kullanılabilir.  
  
 Aşağıda, bir iş akışındaki etkinlikler için <xref:System.ServiceModel.Activities.Send> kullanılabilen farklı önbellek paylaşım düzeyleri ve bunların önerilen kullanımları verilmiştir:  
  
- **Ana bilgisayar düzeyi**: Konak paylaşım düzeyinde, önbellek yalnızca iş akışı hizmeti ana bilgisayarında barındırılan iş akışı örnekleri için kullanılabilir. Bir önbellek, işlem genelinde bir önbellekte iş akışı hizmeti konakları arasında da paylaşılabilir.  
  
- **Örnek düzeyi**: Örnek paylaşım düzeyinde, önbellek, ömrü boyunca belirli bir iş akışı örneği tarafından kullanılabilir, ancak önbellek diğer iş akışı örnekleri için kullanılamaz.  
  
- **Önbellek yok**: Yapılandırma bölümünde tanımlanan uç noktaları kullanan bir iş akışınız varsa önbellek varsayılan olarak kapalıdır. Bu durumda, önbelleğin açık olması güvenli hale getirildiğinden önbelleğin kapalı tutulması de önerilir. Örneğin, her gönderme için farklı bir kimlik (farklı kimlik bilgileri veya kimliğe bürünme kullanılarak) gerekliyse.  
  
## <a name="changing-the-cache-sharing-level-for-a-client-workflow"></a>Istemci Iş akışı için önbellek paylaşım düzeyini değiştirme  
 Bir istemci iş akışında önbellek paylaşımını ayarlamak için, istenen iş akışı örnekleri kümesine uzantı <xref:System.ServiceModel.Activities.SendMessageChannelCache> olarak sınıfın bir örneğini ekleyin. Bu, önbelleğin tüm iş akışı örnekleri arasında paylaşılmasına neden olur. Aşağıdaki kod örnekleri, bu adımların nasıl gerçekleştirileceğini gösterir.  
  
 İlk olarak, türünün <xref:System.ServiceModel.Activities.SendMessageChannelCache>bir örneğini bildirin.  
  
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
 Barındırılan iş akışı hizmetinde önbellek paylaşımını ayarlamak için, <xref:System.ServiceModel.Activities.SendMessageChannelCache> sınıfın bir örneğini bir uzantı olarak tüm iş akışı hizmeti konaklarına ekleyin. Bu, önbelleğin tüm iş akışı hizmeti konakları arasında paylaşılmasına neden olur. Aşağıdaki kod örnekleri, bu adımları gerçekleştirmek için gösterir.  
  
 İlk olarak, sınıf düzeyinde türünün <xref:System.ServiceModel.Activities.SendMessageChannelCache> bir örneğini bildirin.  
  
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
  
 Barındırılan bir iş akışı hizmetindeki önbellek paylaşımını örnek düzeyine ayarlamak için, bir `Func<SendMessageChannelCache>` temsilciyi iş akışı hizmet konağına uzantı olarak ekleyin ve bu temsilciyi, <xref:System.ServiceModel.Activities.SendMessageChannelCache> sınıfının yeni bir örneğini örnekleyen koda atayın. Bu, iş akışı hizmet ana bilgisayarındaki tüm iş akışı örnekleri tarafından paylaşılan tek bir önbellek yerine her bir iş akışı örneği için farklı bir önbellekte sonuçlanır. Aşağıdaki kod örneği, temsilcinin işaret ettiği <xref:System.ServiceModel.Activities.SendMessageChannelCache> uzantıyı doğrudan tanımlamak için bir lambda ifadesi kullanarak bunu nasıl elde ettiğini gösterir.  
  
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
 Kanal fabrikası önbelleği ve kanal önbelleği için önbellek ayarlarını özelleştirebilirsiniz. Önbellek ayarları <xref:System.ServiceModel.Activities.ChannelCacheSettings> sınıfta tanımlanmıştır. <xref:System.ServiceModel.Activities.SendMessageChannelCache> Sınıfı, kanal fabrikası önbelleğinin varsayılan önbellek ayarlarını ve parametresiz oluşturucusunda kanal önbelleğini tanımlar. Aşağıdaki tabloda her önbellek türü için bu önbellek ayarlarının varsayılan değerleri listelenmektedir.  
  
|Ayarlar|LeaseTimeout (dk)|IdleTimeout (dk)|MaxItemsInCache|  
|-|-|-|-|  
|Fabrika önbelleği varsayılanı|TimeSpan. MaxValue|2|16|  
|Kanal önbelleği varsayılanı|5|2|16|  
  
 Fabrika önbelleğini ve kanal önbelleği ayarlarını özelleştirmek için <xref:System.ServiceModel.Activities.SendMessageChannelCache> parametreli oluşturucuyu <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> kullanarak sınıfı örneğini oluşturun ve `factorySettings` ve ' `channelSettings` nin her birine özel değerleri <xref:System.ServiceModel.Activities.ChannelCacheSettings> içeren yeni bir örneğini geçirin parametrelere. Sonra, bu sınıfın yeni örneğini bir iş akışı hizmet konağına veya bir iş akışı örneğine uzantı olarak ekleyin. Aşağıdaki kod örneği, bir iş akışı örneği için bu adımların nasıl gerçekleştirileceğini gösterir.  
  
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
  
 İş akışı hizmetiniz yapılandırmada tanımlı uç noktalara sahip olduğunda önbelleğe almayı etkinleştirmek <xref:System.ServiceModel.Activities.SendMessageChannelCache> için, `allowUnsafeCaching` parametresi olarak `true`ayarlanmış parametreli oluşturucuyu <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> kullanarak sınıfı örneğini oluşturun. Sonra, bu sınıfın yeni örneğini bir iş akışı hizmet konağına veya bir iş akışı örneğine uzantı olarak ekleyin. Aşağıdaki kod örneğinde, bir iş akışı örneği için önbelleğe almanın nasıl etkinleştirileceği gösterilmektedir.  
  
```csharp  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache{ AllowUnsafeCaching = true };  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 Kanal fabrikaları ve kanallar için önbelleği tamamen devre dışı bırakmak için, kanal fabrikası önbelleğini devre dışı bırakın. Bunun yapılması, kanalların ilgili kanal fabrikalarına ait olduğu için kanal önbelleğini de kapatır. Kanal fabrikası önbelleğini devre dışı bırakmak için `factorySettings` , parametresini <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> 0 <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> değerine sahip bir <xref:System.ServiceModel.Activities.ChannelCacheSettings> örneğe başlatılan oluşturucuya geçirin. Aşağıdaki kod örneği bunu gösterir.  
  
```csharp  
// Disable the factory cache. This results in the channel cache to be turned off as well.  
ChannelCacheSettings factorySettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0 };  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings();  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);   
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 Yalnızca kanal fabrikası önbelleğini kullanmayı seçebilir `channelSettings` ve parametresini <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> 0 <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> değerine sahip bir <xref:System.ServiceModel.Activities.ChannelCacheSettings> örneğe başlatılan oluşturucuya geçirerek kanal önbelleğini devre dışı bırakabilirsiniz. Aşağıdaki kod örneği bunu gösterir.  
  
```csharp  
ChannelCacheSettings factorySettings = new ChannelCacheSettings();  
// Disable only the channel cache.  
ChannelCacheSettings channelSettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0};  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);   
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 Barındırılan iş akışı hizmetinde, uygulama yapılandırma dosyasında üreteci önbellek ve kanal önbellek ayarları belirtebilirsiniz. Bunu yapmak için üretecini ve kanal önbellek için önbellek ayarlarını içeren bir hizmet davranışını ekleyin ve bu hizmet davranışını hizmetinize ekleyin. Aşağıdaki örnek, özel fabrika önbelleği ve kanal önbelleği ayarları ile `MyChannelCacheBehavior` hizmet davranışını içeren bir yapılandırma dosyasının içeriğini gösterir. Bu hizmet davranışı, `behaviorConfiguration` özelliği aracılığıyla hizmete eklenir.  
  
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
