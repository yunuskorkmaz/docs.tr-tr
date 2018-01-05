---
title: "Gönderme İşlemleri için Önbellek Paylaşımı Düzeylerini Değiştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03926a64-753d-460e-ac06-2a4ff8e1bbf5
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 59c6ae1ae31a5aa256844e6efca158e4702b6aba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="changing-the-cache-sharing-levels-for-send-activities"></a>Gönderme İşlemleri için Önbellek Paylaşımı Düzeylerini Değiştirme
<xref:System.ServiceModel.Activities.SendMessageChannelCache> Uzantısı düzeyleri, kanal fabrikası önbellek ayarlarını paylaşımı önbellek özelleştirmenize olanak sağlar ve kanal ayarlarını önbelleğe kullanarak hizmet uç noktaları için ileti gönderme iş akışları için <xref:System.ServiceModel.Activities.Send> Mesajlaşma etkinlikleri. Bu iş akışları genellikle istemci iş akışlarıdır ancak içinde barındırılan iş akışı Hizmetleri ayrıca olabilir bir <xref:System.ServiceModel.WorkflowServiceHost>. Kanal fabrikası önbellek içeren önbelleğe alınmış <xref:System.ServiceModel.ChannelFactory%601> nesneleri. Kanal önbelleği önbelleğe alınmış kanalları içerir.  
  
> [!NOTE]
>  İş akışları kullanabilirsiniz <xref:System.ServiceModel.Activities.Send> Mesajlaşma etkinlikleri iletileri veya parametreleri göndermek için. İş akışı çalışma zamanı tür kanallar oluşturmak önbelleğine kanal fabrikaları ekler <xref:System.ServiceModel.Channels.IRequestChannel> kullandığınızda, bir <xref:System.ServiceModel.Activities.ReceiveReply> etkinliği ile bir <xref:System.ServiceModel.Activities.Send> etkinliği ve bir <xref:System.ServiceModel.Channels.IOutputChannel> yalnızca kullanırken bir <xref:System.ServiceModel.Activities.Send> etkinlik (hiçbir <xref:System.ServiceModel.Activities.ReceiveReply>).  
  
## <a name="the-cache-sharing-levels"></a>Önbellek paylaşımı düzeylerini  
 Varsayılan olarak, bir iş akışı tarafından barındırılan bir <xref:System.ServiceModel.WorkflowServiceHost> tarafından kullanılan önbellek <xref:System.ServiceModel.Activities.Send> Mesajlaşma etkinlikleri tüm iş akışı örnekleri arasında paylaşılır <xref:System.ServiceModel.WorkflowServiceHost> (ana bilgisayar önbelleğe alma düzeyi). Tarafından barındırılmadığında bir istemci iş akışı için bir <xref:System.ServiceModel.WorkflowServiceHost>, önbelleğe yalnızca (örnek düzeyi önbelleğe alma) iş akışı örneği için kullanılabilir. Önbellek yalnızca için kullanılabilir <xref:System.ServiceModel.Activities.Send> güvensiz önbelleğe alma etkin değilse yapılandırmasında tanımlanmış uç nokta kullanmayın etkinlikler.  
  
 Düzeyleri için kullanılabilir paylaşımı farklı önbellek şunlardır <xref:System.ServiceModel.Activities.Send> bir iş akışı ve önerilen kullanımlarını etkinlikleri:  
  
-   **Ana bilgisayar düzeyinde**: paylaşım düzeyi konak içinde önbellek iş akışı hizmeti ana bilgisayarında barındırılan iş akışı örnekleri için kullanılabilir. Bir önbellek de bir işlem genelinde önbellekte iş akışı hizmeti ana bilgisayarlar arasında paylaşılabilir.  
  
-   **Örnek düzeyi**: paylaşım düzeyi örneğinde önbellek belirli iş akışı örneği ömrü boyunca kullanılabilir, ancak önbellek diğer iş akışı örnekleri kullanılabilir değil.  
  
-   **Önbellek yok**: yapılandırmasında tanımlanmış uç noktaları kullanan bir iş akışı varsa önbelleği varsayılan olarak kapalıdır. Ayrıca, açma güvensiz olabilir çünkü bu durumda kapalı önbellek tutmanız önerilir. Örneğin, farklı bir kimlik (farklı kimlik bilgileri veya kimliğe bürünme özelliğini kullanarak) her gönderme için gereklidir.  
  
## <a name="changing-the-cache-sharing-level-for-a-client-workflow"></a>Paylaşım düzeyi için bir istemci iş akışı önbellek değiştirme  
 Bir istemci iş akışında paylaşımı önbelleği ayarlamak için bir örnek ekler <xref:System.ServiceModel.Activities.SendMessageChannelCache> sınıfı istenen iş akışı örnekleri kümesi bir uzantısı olarak. Bu, tüm iş akışı örnekleri arasında önbellek paylaşımı ile sonuçlanır. Aşağıdaki kod örnekleri, bu adımların nasıl gerçekleştirileceğini gösterir.  
  
 Öncelikle, türünün bir örneği bildirin <xref:System.ServiceModel.Activities.SendMessageChannelCache>.  
  
```  
// Create an instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension =  
    new SendMessageChannelCache();  
```  
  
 Ardından, her istemci iş akışı örneğine önbellek uzantısı ekleyin.  
  
```  
WorkflowApplication clientInstance1 = new WorkflowApplication(new clientWorkflow1());  
WorkflowApplication clientInstance2 = new WorkflowApplication(new clientWorkflow2());  
  
// Share the cache extension object   
  
clientInstance1.Extensions.Add(sharedChannelCacheExtension);  
clientInstance2.Extensions.Add(sharedChannelCacheExtension);  
```  
  
## <a name="changing-the-cache-sharing-level-for-a-hosted-workflow-service"></a>Paylaşım düzeyi barındırılan iş akışı hizmeti için önbellek değiştirme  
 Barındırılan iş akışı hizmetinde paylaşımı önbelleği ayarlamak için bir örnek ekler <xref:System.ServiceModel.Activities.SendMessageChannelCache> tüm iş akışı hizmeti ana bir uzantısı olarak sınıfı. Bu, tüm iş akışı hizmeti ana bilgisayarlar arasında önbellek paylaşımı ile sonuçlanır. Bu adımları gerçekleştirmek için aşağıdaki kod örnekleri göster.  
  
 Öncelikle, türünün bir örneği bildirin <xref:System.ServiceModel.Activities.SendMessageChannelCache> sınıf düzeyinde.  
  
```  
// Create static instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension = new  
    SendMessageChannelCache();  
```  
  
 Ardından, statik önbellek uzantısı, her iş akışı hizmeti ana bilgisayarı ekleyin.  
  
```  
WorkflowServiceHost host1 = new WorkflowServiceHost(new serviceWorkflow1(), new Uri(baseAddress1));  
WorkflowServiceHost host2 = new WorkflowServiceHost(new serviceWorkflow2(), new Uri(baseAddress2));  
  
// Share the static cache to get an AppDomain level cache.  
host1.WorkflowExtensions.Add(sharedChannelCacheExtension);  
host2.WorkflowExtensions.Add(sharedChannelCacheExtension);  
```  
  
 Barındırılan iş akışı hizmeti örneği düzeyine paylaşımı önbelleği ayarlamak için ekleme bir `Func<SendMessageChannelCache>` temsilci iş akışı hizmeti ana bilgisayarı için bir uzantısı olarak ve yeni bir örneğini başlatır kodu bu temsilci atamak <xref:System.ServiceModel.Activities.SendMessageChannelCache> sınıfı. Bu, iş akışı hizmeti ana bilgisayar tüm iş akışı örnekleri tarafından paylaşılan tek bir önbellek yerine her ayrı ayrı iş akışı örneği için farklı bir önbellek sonuçlanır. Aşağıdaki kod örneğinde, doğrudan tanımlamak için bir lambda ifadesi kullanarak bunu başarmanın gösterilmiştir <xref:System.ServiceModel.Activities.SendMessageChannelCache> temsilci işaret uzantısı.  
  
```  
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
  
## <a name="customizing-cache-settings"></a>Önbellek Ayarları özelleştirme  
 Kanal fabrikası önbellek ve kanal önbelleği için önbellek ayarlarını özelleştirebilirsiniz. Önbellek ayarları tanımlanan <xref:System.ServiceModel.Activities.ChannelCacheSettings> sınıfı. <xref:System.ServiceModel.Activities.SendMessageChannelCache> Sınıfı, varsayılan kurucusunda kanal fabrikası önbellek ve kanal önbellek için varsayılan önbellek ayarlarını tanımlar. Aşağıdaki tabloda bu önbellek ayarları önbellek her tür için varsayılan değerler listelenmektedir.  
  
|Ayarlar|LeaseTimeout (min.)|IdleTimeout (min.)|MaxItemsInCache|  
|-|-|-|-|  
|Fabrika önbellek varsayılan|TimeSpan.MaxValue|2|16|  
|Kanal önbellek varsayılan|5|2|16|  
  
 Fabrika önbellek ve kanal önbellek ayarlarını özelleştirmek için örneği <xref:System.ServiceModel.Activities.SendMessageChannelCache> parametreli Oluşturucusu kullanılarak sınıf <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> ve yeni bir örneğini geçirin <xref:System.ServiceModel.Activities.ChannelCacheSettings> her biri için özel değerler ile `factorySettings` ve `channelSettings` parametreleri. Ardından, bu sınıfın yeni bir örneğini bir iş akışı hizmeti ana bilgisayarı veya bir iş akışı örneği bir uzantısı olarak ekleyin. Aşağıdaki kod örneği, bir iş akışı örneği için bu adımları uygulamadan gösterilmektedir.  
  
```  
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
  
 İş akışı Hizmeti uç noktaları yapılandırmasında tanımlı olduğunda önbelleğe almayı etkinleştirmek için örneği <xref:System.ServiceModel.Activities.SendMessageChannelCache> parametreli Oluşturucusu kullanılarak sınıf <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> ile `allowUnsafeCaching` parametre kümesine `true`. Ardından, bu sınıfın yeni bir örneğini bir iş akışı hizmeti ana bilgisayarı veya bir iş akışı örneği bir uzantısı olarak ekleyin. Aşağıdaki kod örneği, bir iş akışı örneği için önbelleğe almayı etkinleştirmek gösterilmiştir.  
  
```  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache{ AllowUnsafeCaching = true };  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 Kanal fabrikaları ve kanallar için tamamen önbelleği devre dışı bırakmak için kanal fabrikası önbelleği devre dışı bırakın. Kanallar, karşılık gelen kanal üreteçleri tarafından sahip olunan gibi Bunun yapılması kanal önbelleği devre dışı de etkinleştirir. Kanal fabrikası önbelleğini devre dışı bırakmak için geçirdiğiniz `factorySettings` parametresi <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> Oluşturucusu başlatılır bir <xref:System.ServiceModel.Activities.ChannelCacheSettings> örneği bir <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> 0 değeri. Aşağıdaki kod örneğinde bu gösterir.  
  
```  
// Disable the factory cache. This results in the channel cache to be turned off as well.  
ChannelCacheSettings factorySettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0 };  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings();  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);   
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 Yalnızca kanal fabrikası önbelleğinin kullanımı ve geçirerek kanal önbelleğini devre dışı bırakmak seçebileceğiniz `channelSettings` parametresi <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> Oluşturucusu başlatılır bir <xref:System.ServiceModel.Activities.ChannelCacheSettings> örneği bir <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> 0 değeri. Aşağıdaki kod örneğinde bu gösterir.  
  
```  
ChannelCacheSettings factorySettings = new ChannelCacheSettings();  
// Disable only the channel cache.  
ChannelCacheSettings channelSettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0};  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);   
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 Barındırılan iş akışı hizmetinde, uygulama yapılandırma dosyasında üreteci önbellek ve kanal önbellek ayarları belirtebilirsiniz. Bunu yapmak için üretecini ve kanal önbellek için önbellek ayarlarını içeren bir hizmet davranışını ekleyin ve bu hizmet davranışını hizmetinize ekleyin. Aşağıdaki örnek içeren bir yapılandırma dosyası içeriğini gösterir `MyChannelCacheBehavior` hizmet davranışı özel fabrika önbellek ve kanal önbellek ayarlarına. Bu hizmet davranışı hizmet aracılığıyla eklenen `behaviorConfiguarion` özniteliği.  
  
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
