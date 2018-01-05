---
title: "Basitleştirilmiş Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3ff1dee5a57b0c134c25631ce5c694b1b6b2c006
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="simplified-configuration"></a>Basitleştirilmiş Yapılandırma
Yapılandırma [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Hizmetleri, karmaşık bir görev olabilir. Çok sayıda farklı seçeneğiniz vardır ve her zaman hangi ayarların gerekli olduğunu belirlemek kolay değildir. Yapılandırma dosyaları esnekliğini artırmak sırada [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmetleri de oldukları sorunları bulmak sabit sayıda kaynağı. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]Bu sorunu giderir ve boyutunu ve hizmet yapılandırmasını karmaşıklığını azaltmak için bir yol sağlar.  
  
## <a name="simplified-configuration"></a>Basitleştirilmiş Yapılandırma  
 İçinde [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet yapılandırma dosyaları, <`system.serviceModel`> bölüm içeren bir <`service`> öğesi barındırılan her hizmet için. <`service`> Öğesi içeren bir koleksiyonu <`endpoint`> her hizmet ve isteğe bağlı olarak bir dizi hizmet davranışları için kullanıma sunulan uç noktaları belirtin öğeleri. <`endpoint`> Öğelerini bağlama, adresi belirtin ve Sözleşme, bitiş noktası tarafından ve isteğe bağlı olarak bağlama yapılandırması ve uç nokta davranışları kullanıma. <`system.serviceModel`> Bölümünde de içeren bir <`behaviors`> hizmet veya uç nokta davranışları belirtmenize olanak tanır öğesi. Aşağıdaki örnekte gösterildiği <`system.serviceModel`> bir yapılandırma dosyası bölümünü.  
  
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
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]yapar yapılandırma bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet gereksinimini kaldırarak daha kolay <`service`> öğesi. Değil eklerseniz, bir <`service`> bölümünde veya tüm uç noktalarını eklemek bir <`service`> bölümü ve hizmetinizi değil program aracılığıyla tanımlama uç nokta sonra varsayılan uç noktalar kümesi hizmetiniz için birer tane olmak üzere otomatik olarak eklenir Hizmet taban adresi ve hizmetiniz tarafından uygulanan her bir sözleşme. Her birinde Bu uç noktalar, uç nokta adresi taban adresine karşılık gelen, bağlama temel adres düzeni tarafından belirlenir ve hizmetiniz tarafından uygulanan bir sözleşmedir. Herhangi bir uç noktaları veya hizmet davranışları belirtin veya bağlama ayarı değişiklik gerekmez, hizmet yapılandırma dosyası belirtmeniz gerekmez. Bir hizmet iki sözleşmeleri uygular ve ana bilgisayar hem HTTP hem de TCP aktarımlarını etkinleştirir, hizmet ana bilgisayarı dört varsayılan uç noktalar, her aktarım kullanarak her sözleşme için bir tane oluşturur. Varsayılan uç hizmet ana bilgisayarını oluşturmak için kullanmak üzere hangi bağlamaları bilmeniz gerekir. Bu ayarları belirtilen bir <`protocolMappings`> içinde bölümünde <`system.serviceModel`> bölümü. <`protocolMappings`> Bölümüne Aktarım Protokolü düzenleri türleri bağlama için eşlenmiş bir listesini içerir. Hizmet ana bilgisayarı kendisine geçirilen temel adresler kullanmak için hangi bağlama belirlemek için kullanır. Aşağıdaki örnek kullanır <`protocolMappings`> öğesi.  
  
> [!WARNING]
>  Varsayılan yapılandırma öğelerini bağlamaları veya davranışları gibi değiştirme Hizmetleri bu varsayılan bağlamalar ve davranışları kullanabilecek beri yapılandırma hiyerarşisinin düzeylerinde tanımlı etkileyebilir. Bu nedenle, aktaranın varsayılan bağlamalar ve davranış değişiklikleri bu değişiklikleri hiyerarşideki diğer hizmetler etkileyebilecek farkında olması gerekir.  
  
> [!NOTE]
>  Internet Information Services (IIS) veya Windows İşlem Etkinleştirme Hizmeti (WAS) altında barındırılan hizmetleri sanal dizini kendi taban adresi olarak kullanın.  
  
```xml  
<protocolMapping>  
  <add scheme="http"     binding="basicHttpBinding" bindingConfiguration="MyBindingConfiguration"/>  
  <add scheme="net.tcp"  binding="netTcpBinding"/>  
  <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
  <add scheme="net.msmq" binding="netMSMQBinding"/>  
</protocolMapping>  
```  
  
 Önceki örnekte, "http" düzeni ile başlayan bir taban adresi noktayla kullanır <xref:System.ServiceModel.BasicHttpBinding>. Bir uç nokta "net.tcp" düzeni ile başlayan bir taban adresi kullanan <xref:System.ServiceModel.NetTcpBinding>. Yerel bir App.config veya Web.config dosyasında ayarlarını geçersiz kılabilirsiniz.  
  
 Her öğe içinde <`protocolMappings`> bölümü, bir şema ve bağlama belirtmelisiniz. İsteğe bağlı olarak belirtebilirsiniz bir `bindingConfiguration` içinde bir bağlaması yapılandırma belirten özniteliği <`bindings`> yapılandırma dosyası bölümünü. Öyle değilse `bindingConfiguration` belirtilirse, uygun bağlama türü anonim bağlama yapılandırması kullanılır.  
  
 Hizmet davranışları, varsayılan uç noktaları için anonim kullanılarak yapılandırılır <`behavior`> içindeki bölümler <`serviceBehaviors`> bölümler. Herhangi bir adlandırılmamış <`behavior`> içinde öğelerin <`serviceBehaviors`> Hizmet davranışları yapılandırmak için kullanılır. Örneğin, aşağıdaki yapılandırma dosyası ana bilgisayarı içindeki tüm hizmetler için hizmet meta veri yayımlama sağlar.  
  
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
  
 Uç nokta davranışları anonim kullanılarak yapılandırılır <`behavior`> içindeki bölümler <`serviceBehaviors`> bölümler.  
  
 Aşağıdaki örnek Basitleştirilmiş yapılandırma modelini kullanır, bu konunun başında bir için eşdeğer bir yapılandırma dosyasıdır.  
  
```xml  
<system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="false"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>    <bindings>  
       <basicHttpBinding>  
          <binding maxBufferSize="100"  
                   maxReceiveBufferSize="100" />  
       </basicHttpBinding>  
    </bindings>    <!-- No <service> tag is necessary. Default endpoints will be added to the service -->  
    <!-- The service behavior with name="" will be picked up by the service -->  
    <protocolMapping>  
      <add scheme="http"     binding="basicHttpBinding" / </protocolMapping>  
  </system.serviceModel>  
```  
  
> [!IMPORTANT]
>  Bu özellik yalnızca WCF hizmeti yapılandırmasını istemci yapılandırmasını ilişkilendirir. Çoğu kez, WCF istemci yapılandırması svcutil.exe veya Visual Studio'dan bir hizmet başvurusu ekleme gibi bir araç tarafından oluşturuldu. Bir WCF istemcisi el ile yapılandırıyorsanız eklemeniz gerekir bir \<istemci > yapılandırma öğesine ve istediğiniz çağırmak için uç nokta belirtin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 [Hizmetler için Bağlamaları Yapılandırma](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)  
 [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Hizmetleri Yapılandırma](../../../docs/framework/wcf/configuring-services.md)  
 [Windows Communication Foundation uygulamaları yapılandırma](http://msdn.microsoft.com/en-us/13cb368e-88d4-4c61-8eed-2af0361c6d7a)  
 [Code’da WCF Hizmetlerini Yapılandırma](../../../docs/framework/wcf/configuring-wcf-services-in-code.md)
