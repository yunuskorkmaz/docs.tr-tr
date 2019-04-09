---
title: Basitleştirilmiş Yapılandırma
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: 13cf8bd46ef3aabb011cb2ddd207963235468662
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59184060"
---
# <a name="simplified-configuration"></a>Basitleştirilmiş Yapılandırma
Windows Communication Foundation (WCF) hizmetlerini yapılandırmak, karmaşık bir görev olabilir. Çok sayıda farklı seçeneğiniz vardır ve her zaman gerekli ayarları belirlemek kolay değildir. Yapılandırma dosyalarını WCF hizmetleri esnekliğini artırın, ancak bunlar ayrıca sorunları bulmak sabit bir çoğu için işlemcilerden kaynaklanıyor olabilir. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Bu sorunları giderir ve büyüklüğü ve karmaşıklığı ile hizmet yapılandırmasının azaltmak için bir yol sağlar.  
  
## <a name="simplified-configuration"></a>Basitleştirilmiş Yapılandırma  
 WCF hizmeti yapılandırma dosyalarında <`system.serviceModel`> bölüm içeren bir <`service`> barındırılan her hizmet için öğesi. <`service`> Öğesi içeren bir koleksiyon, <`endpoint`> her hizmet ve isteğe bağlı olarak bir dizi hizmet davranışları için açık Uç noktalara belirten öğeler. <`endpoint`> Elementleri bağlama, adresi ve Sözleşme, uç nokta ve isteğe bağlı olarak bağlama yapılandırması ve uç nokta davranışları ortaya. <`system.serviceModel`> Bölümü içerecek bir <`behaviors`> öğesi hizmet veya uç nokta davranışları belirtmenizi sağlar. Aşağıdaki örnekte gösterildiği <`system.serviceModel`> yapılandırma dosyasının.  
  
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
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] gereksinimini ortadan kaldırarak daha kolay bir WCF hizmeti yapılandırma yapar <`service`> öğesi. Değil eklerseniz bir <`service`> bölümünde veya tüm uç noktaların ekleme bir <`service`> bölüm ve hizmetinizi programlı olarak tanımlamıyor tüm uç noktaları ve hizmetiniz için birer tane olmak üzere otomatik olarak bir varsayılan uç nokta kümesine eklenir Hizmet temel adresi ve hizmetiniz tarafından uygulanan her bir sözleşme için. Her birinde Bu uç noktaları, uç nokta adresini temel adresine karşılık gelen, bağlama temel adres düzeni tarafından belirlenir ve hizmetiniz tarafından uygulanan bir sözleşmedir. Herhangi bir uç noktaları veya hizmet davranışları belirtin veya bağlama ayarı değişiklik gerekmez, hizmet yapılandırma dosyasını belirtmeniz gerekmez. Bir hizmeti iki sözleşmeleri uygular ve ana bilgisayar hem HTTP hem de TCP aktarımlarını etkinleştirir dört varsayılan uç noktalar, her aktarım kullanarak her bir sözleşme için bir hizmet konağı oluşturur. Hizmet ana bilgisayarı varsayılan uç noktalar oluşturmak için kullanılacak hangi bağlamaları bilmeniz gerekir. Bu ayarları belirtilmiş bir <`protocolMappings`> içinde bölümünde <`system.serviceModel`> bölümü. <`protocolMappings`> Bölümü, taşıma protokol şemaları bağlama türleri için eşlenmiş bir listesini içerir. Hizmet ana bilgisayarını kullanmak için hangi bağlama belirlemek için geçirilen temel adresler kullanır. Aşağıdaki örnekte <`protocolMappings`> öğesi.  
  
> [!WARNING]
>  Varsayılan bağlamaları veya davranışlar gibi yapılandırma öğelerini değiştirme, bu varsayılan bağlamaları ve davranışları kullanabilecek beri yapılandırma hiyerarşisinde daha düşük düzeylerde tanımlı hizmetleri etkileyebilir. Bu nedenle, kişi varsayılan bağlamaları ve davranışları değiştirir bu değişiklikleri hiyerarşideki diğer hizmetleri etkileyebilir farkında olması gerekir.  
  
> [!NOTE]
>  Internet Information Services (IIS) veya Windows İşlem Etkinleştirme Hizmeti (WAS) altında barındırılan hizmetler, sanal dizin kendi taban adresi olarak kullanın.  
  
```xml  
<protocolMapping>  
  <add scheme="http"     binding="basicHttpBinding" bindingConfiguration="MyBindingConfiguration"/>  
  <add scheme="net.tcp"  binding="netTcpBinding"/>  
  <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
  <add scheme="net.msmq" binding="netMSMQBinding"/>  
</protocolMapping>  
```  
  
 Önceki örnekte, "http" düzeni ile başlayan bir taban adresi ile bir uç nokta kullanan <xref:System.ServiceModel.BasicHttpBinding>. "Net.tcp" düzeni başlatan temel adresine sahip bir uç nokta kullanan <xref:System.ServiceModel.NetTcpBinding>. Yerel bir App.config veya Web.config dosyasındaki ayarları geçersiz kılabilirsiniz.  
  
 Her öğe içinde <`protocolMappings`> bölümü, bir şema ve bağlama belirtmelisiniz. İsteğe bağlı olarak belirtebilirsiniz bir `bindingConfiguration` içinde bir bağlama yapılandırmasını belirten Öznitelik <`bindings`> yapılandırma dosyası bölümünü. Hayır ise `bindingConfiguration` belirtilirse, uygun bağlama türü anonim bir bağlama yapılandırmasını kullanılır.  
  
 Hizmet davranışları, varsayılan uç noktaları için anonim kullanılarak yapılandırılır <`behavior`> içinde bölümler <`serviceBehaviors`> bölümler. Tüm adlandırılmamış <`behavior`> öğeleri içinde <`serviceBehaviors`> Hizmet davranışları yapılandırmak için kullanılır. Örneğin, aşağıdaki yapılandırma dosyası, konak içindeki tüm hizmetleri için hizmet meta verileri yayımlama sağlar.  
  
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
  
 Uç nokta davranışları, anonim kullanılarak yapılandırılır <`behavior`> içinde bölümler <`serviceBehaviors`> bölümler.  
  
 Aşağıdaki örnek, Basitleştirilmiş yapılandırma modelini kullanan bu konunun başında bir eşdeğer bir yapılandırma dosyasıdır.  
  
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
>  Bu özellik yalnızca WCF Hizmeti Yapılandırması istemci yapılandırmasını ilişkilendirir. Çoğu durumda, WCF istemci yapılandırması svcutil.exe veya Visual Studio'dan bir hizmet başvurusu ekleme gibi bir araç tarafından oluşturulur. Bir WCF istemcisi elle yapılandırıyorsanız eklemeniz gerekecektir bir \<istemci > yapılandırma öğesi ve çağırmak istediğiniz uç nokta belirtin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)
- [Hizmetler için Bağlamaları Yapılandırma](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetleri Yapılandırma](../../../docs/framework/wcf/configuring-services.md)
- [WCF hizmetlerini yapılandırma](configuring-services.md)
- [WCF Hizmetlerini Kodda Yapılandırma](../../../docs/framework/wcf/configuring-wcf-services-in-code.md)
