---
title: Basitleştirilmiş Yapılandırma
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: 567f03e8f35ed72ba7e2a602bf47257158741fb3
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321165"
---
# <a name="simplified-configuration"></a>Basitleştirilmiş Yapılandırma
Windows Communication Foundation (WCF) hizmetleri yapılandırmak karmaşık bir görev olabilir. Birçok farklı seçenek vardır ve hangi ayarların gerekli olduğunu belirlemek her zaman kolay değildir. Yapılandırma dosyaları WCF hizmetlerinin esnekliğini artırırken, ayrıca sorunları bulmak için çok zor olan kaynaktır. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] bu sorunları giderir ve hizmet yapılandırmasının boyutunu ve karmaşıklığını azaltmak için bir yol sağlar.  
  
## <a name="simplified-configuration"></a>Basitleştirilmiş Yapılandırma  
 WCF hizmeti yapılandırma dosyalarında < `system.serviceModel` > bölümü barındırılan her hizmet için bir < `service` > öğesi içerir. < @No__t-0 > öğesi, her hizmet için sunulan uç noktaları ve isteğe bağlı olarak bir hizmet davranışı kümesini belirten < `endpoint` > öğelerinin bir koleksiyonunu içerir. < @No__t-0 > öğeleri, uç nokta tarafından kullanıma sunulan adresi, bağlamayı ve sözleşmeyi belirtir ve isteğe bağlı olarak yapılandırma ve uç nokta davranışları bağlama. < @No__t-0 > bölümü Ayrıca hizmet veya uç nokta davranışları belirtmenize olanak tanıyan bir < `behaviors` > öğesi içerir. Aşağıdaki örnek, bir yapılandırma dosyasının < `system.serviceModel` > bölümünü gösterir.  
  
```  
<system.serviceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="MyServiceBehavior">  
        <serviceMetadata httpGetEnabled="true">  
        <serviceDebug includeExceptionDetailInFaults="false">  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
  <bindings>  
   <basicHttpBinding>  
      <binding name=MyBindingConfig"  
               maxBufferSize="100"  
               maxReceiveBufferSize="100" />  
   </basicHttpBinding>  
   </bindings>   <services>  
    <service behaviorConfiguration="MyServiceBehavior"  
             name="MyService">  
      <endpoint address=""  
                binding="basicHttpBinding"  
                contract="ICalculator"  
                bindingConfiguration="MyBindingConfig" />  
      <endpoint address="mex"  
                binding="mexHttpBinding"  
                contract="IMetadataExchange"/>  
    </service>  
  </services>  
</system.serviceModel>  
```  
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], < `service` > öğesi gereksinimini kaldırarak bir WCF hizmetini yapılandırmayı daha kolay hale getirir. Bir < `service` > bölümü ekleyemez veya bir < `service` > bölümünde herhangi bir uç nokta eklerseniz ve hizmetiniz program aracılığıyla herhangi bir uç nokta tanımlamıyor, her hizmet temel adresi için bir varsayılan uç nokta kümesi otomatik olarak hizmetinize eklenir ve hizmetiniz tarafından uygulanan her sözleşme için. Bu uç noktaların her birinde, uç nokta adresi temel adrese karşılık gelir, bağlama ise temel adres düzeni tarafından belirlenir ve sözleşme hizmetiniz tarafından uygulanan bir sözleşmedir. Herhangi bir uç nokta veya hizmet davranışı belirtmeniz veya herhangi bir bağlama ayarı değişikliği yapmanız gerekmiyorsa, bir hizmet yapılandırma dosyası belirtmeniz gerekmez. Bir hizmet iki sözleşme uygularsa ve ana bilgisayar hem HTTP hem de TCP taşımalarını etkinleştirse, hizmet ana bilgisayarı her bir taşıyıcı kullanan her bir sözleşme için dört varsayılan uç nokta oluşturur. Varsayılan uç noktalar oluşturmak için hizmet ana bilgisayarının hangi bağlamaları kullanacağınızı bilmeleri gerekir. Bu ayarlar < `system.serviceModel` > bölümündeki bir < `protocolMappings` > bölümünde belirtilir. < @No__t-0 > bölümü, bağlama türlerine eşlenmiş Aktarım Protokolü düzenlerinin bir listesini içerir. Hizmet ana bilgisayarı, hangi bağlamanın kullanılacağını belirleyen, kendisine geçirilen temel adresleri kullanır. Aşağıdaki örnek < `protocolMappings` > öğesini kullanır.  
  
> [!WARNING]
> Bağlamalar veya davranışlar gibi varsayılan yapılandırma öğelerinin değiştirilmesi, bu varsayılan bağlamaları ve davranışları kullandıklarından, yapılandırma hiyerarşisinin daha düşük düzeylerinde tanımlanan Hizmetleri etkileyebilir. Bu nedenle, varsayılan bağlamaları ve davranışları değiştirmenin, bu değişikliklerin hiyerarşideki diğer hizmetleri etkileyebileceğini unutmayın.  
  
> [!NOTE]
> Internet Information Services (IIS) veya Windows Işlem etkinleştirme hizmeti (WAS) altında barındırılan hizmetler, sanal dizini kendi temel adresleri olarak kullanır.  
  
```xml  
<protocolMapping>  
  <add scheme="http"     binding="basicHttpBinding" bindingConfiguration="MyBindingConfiguration"/>  
  <add scheme="net.tcp"  binding="netTcpBinding"/>  
  <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
  <add scheme="net.msmq" binding="netMSMQBinding"/>  
</protocolMapping>  
```  
  
 Önceki örnekte, "http" düzeniyle başlayan temel adrese sahip bir uç nokta <xref:System.ServiceModel.BasicHttpBinding> kullanır. Temel adresi "net. TCP" düzeniyle başlayan bir uç nokta, <xref:System.ServiceModel.NetTcpBinding> kullanır. Yerel bir App. config veya Web. config dosyasındaki ayarları geçersiz kılabilirsiniz.  
  
 < @No__t-0 > bölümündeki her öğe bir düzen ve bir bağlama belirtmelidir. İsteğe bağlı olarak, yapılandırma dosyasının < `bindings` > bölümünde bir bağlama yapılandırması belirten `bindingConfiguration` özniteliği belirtebilir. @No__t-0 belirtilmemişse, uygun bağlama türünün adsız bağlama yapılandırması kullanılır.  
  
 Hizmet davranışları, < `serviceBehaviors` > bölümlerinde anonim < `behavior` > bölümleri kullanılarak varsayılan uç noktalar için yapılandırılır. < @No__t-1 > içindeki adlandırılmamış < `behavior` > öğeleri hizmet davranışlarını yapılandırmak için kullanılır. Örneğin, aşağıdaki yapılandırma dosyası konak içindeki tüm hizmetler için hizmet meta verileri yayımlamayı mümkün bir şekilde sunar.  
  
```xml  
<system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>    <!-- No <service> tag is necessary. Default endpoints are added to the service -->  
    <!-- The service behavior with name="" is picked up by the service -->  
 </system.serviceModel>  
```  
  
 Uç nokta davranışları < `serviceBehaviors` > bölümlerinde anonim < `behavior` > bölümleri kullanılarak yapılandırılır.  
  
 Aşağıdaki örnek, Basitleştirilmiş yapılandırma modelini kullanan bu konunun başındaki bir yapılandırma dosyasıdır.  
  
```xml  
<system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <serviceMetadata httpGetEnabled="true" />
          <serviceDebug includeExceptionDetailInFaults="false" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <bindings>
       <basicHttpBinding>
          <binding maxBufferSize="100"
                   maxReceiveBufferSize="100" />
       </basicHttpBinding>
    </bindings>
    <!-- No <service> tag is necessary. Default endpoints will be added to the service -->
    <!-- The service behavior with name="" will be picked up by the service -->
    <protocolMapping>
      <add scheme="http" binding="basicHttpBinding" />
  </protocolMapping>
  </system.serviceModel>
```  
  
> [!IMPORTANT]
> Bu özellik yalnızca WCF hizmeti yapılandırmasıyla ilgilidir, istemci yapılandırması değildir. Çoğu kez, WCF istemci yapılandırması Svcutil. exe gibi bir araçla veya Visual Studio 'dan bir hizmet başvurusu eklenerek oluşturulacaktır. Bir WCF istemcisini el ile yapılandırıyorsanız, yapılandırmaya bir \<client > öğesi eklemeniz ve çağırmak istediğiniz uç noktaları belirtmeniz gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma](configuring-services-using-configuration-files.md)
- [Hizmetler için Bağlamaları Yapılandırma](configuring-bindings-for-wcf-services.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](./feature-details/configuring-system-provided-bindings.md)
- [Hizmetleri Yapılandırma](configuring-services.md)
- [WCF hizmetlerini yapılandırma](configuring-services.md)
- [Code’da WCF Hizmetlerini Yapılandırma](configuring-wcf-services-in-code.md)
