---
title: Basitleştirilmiş Yapılandırma
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: 4e316290c045b75896c61e36c1646440c18678e2
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249636"
---
# <a name="simplified-configuration"></a>Basitleştirilmiş Yapılandırma
Windows Communication Foundation (WCF) hizmetlerini yapılandırmak karmaşık bir görev olabilir. Birçok farklı seçenek vardır ve hangi ayarların gerekli olduğunu belirlemek her zaman kolay değildir. Yapılandırma dosyaları WCF hizmetlerinin esnekliğini artırırken, aynı zamanda bulunması zor birçok sorunun kaynağıdır. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]bu sorunları giderir ve hizmet yapılandırmasının boyutunu ve karmaşıklığını azaltmanın bir yolunu sağlar.  
  
## <a name="simplified-configuration"></a>Basitleştirilmiş Yapılandırma  
 WCF hizmet yapılandırma dosyalarında, <`system.serviceModel`> `service` bölümü barındırılan her hizmet için <bir> öğesi içerir. <`service`> öğesi, her `endpoint` hizmet için maruz kalan uç noktaları ve isteğe bağlı olarak bir hizmet davranışı kümesini belirten <> öğeleri koleksiyonu içerir. <`endpoint`> öğeleri, bitiş noktası tarafından maruz kalan adresi, bağlamayı ve sözleşmeyi ve isteğe bağlı olarak bağlama yapılandırması ve uç nokta davranışlarını belirtir. <`system.serviceModel`> bölümü, hizmet `behaviors` veya bitiş noktası davranışlarını belirtmenize olanak tanıyan <bir> öğesi de içerir. Aşağıdaki örnek, yapılandırma `system.serviceModel` dosyasının <> bölümünü gösterir.  
  
```xml  
<system.serviceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="MyServiceBehavior">  
        <serviceMetadata httpGetEnabled="true" />  
        <serviceDebug includeExceptionDetailInFaults="false" />  
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
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<`service`> öğesi gereksinimini kaldırarak bir WCF hizmetini yapılandırmayı kolaylaştırır. <`service`> bölümü eklemezseniz veya <`service`> bölümüne herhangi bir uç nokta eklemezseniz ve hizmetiniz programlı olarak herhangi bir uç nokta tanımlamazsa, her hizmet temel adresi ve hizmetinizin uyguladığı her sözleşme için otomatik olarak bir dizi varsayılan uç nokta hizmetinize eklenir. Bu uç noktaların her birinde, bitiş noktası adresi temel adrese karşılık gelir, bağlama temel adres şeması tarafından belirlenir ve sözleşme hizmetiniz tarafından uygulanan adrestir. Herhangi bir uç nokta veya hizmet davranışı belirtmeniz veya bağlayıcı ayar değişiklikleri yapmanız gerekmiyorsa, bir hizmet yapılandırma dosyası belirtmeniz gerekmez. Bir hizmet iki sözleşme uygularsa ve ana bilgisayar hem HTTP hem de TCP taşımasına olanak tanırsa, hizmet ana bilgisayarı her aktarım ı kullanan her sözleşme için bir tane olmak üzere dört varsayılan uç nokta oluşturur. Varsayılan uç noktaları oluşturmak için hizmet ana bilgisayar hangi bağlamaları kullanacağını bilmelidir. Bu ayarlar, <`protocolMappings` `system.serviceModel`> bölümünde ki <> bölümünde belirtilir. <`protocolMappings`> bölümü, bağlama türlerine eşlenen aktarım protokolü düzenlerinin bir listesini içerir. Hizmet ana bilgisayarı, hangi bağlamanın kullanılacağını belirlemek için ona aktarılan temel adresleri kullanır. Aşağıdaki örnekte <`protocolMappings`> öğesi kullanır.  
  
> [!WARNING]
> Bağlamalar veya davranışlar gibi varsayılan yapılandırma öğelerini değiştirmek, bu varsayılan bağlamaları ve davranışları kullandıklarından, yapılandırma hiyerarşisinin alt düzeylerinde tanımlanan hizmetleri etkileyebilir. Bu nedenle, varsayılan bağlamaları ve davranışları değiştiren kişinin, bu değişikliklerin hiyerarşideki diğer hizmetleri etkileyebileceğinibilmesi gerekir.  
  
> [!NOTE]
> Internet Information Services (IIS) veya Windows Process Activation Service (WAS) kapsamında barındırılan hizmetler, sanal dizini temel adresleri olarak kullanır.  
  
```xml  
<protocolMapping>  
  <add scheme="http"     binding="basicHttpBinding" bindingConfiguration="MyBindingConfiguration"/>  
  <add scheme="net.tcp"  binding="netTcpBinding"/>  
  <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
  <add scheme="net.msmq" binding="netMSMQBinding"/>  
</protocolMapping>  
```  
  
 Önceki örnekte, "http" şeması ile başlayan bir taban adresi <xref:System.ServiceModel.BasicHttpBinding>ile bir bitiş noktası kullanır. "net.tcp" şeması ile başlayan bir taban adresi olan <xref:System.ServiceModel.NetTcpBinding>bir bitiş noktası kullanır. Yerel bir App.config veya Web.config dosyasındaki ayarları geçersiz kılabilirsiniz.  
  
 <`protocolMappings`> bölümündeki her öğe bir şema ve bağlama belirtmelidir. İsteğe bağlı olarak, yapılandırma dosyasının <`bindingConfiguration` `bindings`> bölümünde bağlayıcı yapılandırma belirten bir öznitelik belirtebilir. Hiçbir `bindingConfiguration` belirtilmemişse, uygun bağlama türünün anonim bağlama yapılandırması kullanılır.  
  
 Hizmet davranışları, <`behavior` `serviceBehaviors`> bölümlerdeki anonim <> bölümleri kullanılarak varsayılan uç noktalar için yapılandırılır. > <`behavior` `serviceBehaviors` içindeki adsız <> öğeler, hizmet davranışlarını yapılandırmak için kullanılır. Örneğin, aşağıdaki yapılandırma dosyası ana bilgisayardaki tüm hizmetler için hizmet meta veri yayımlama sağlar.  
  
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
  
 Bitiş noktası davranışları,> `behavior` `serviceBehaviors` <bölümlerdeki anonim <> bölümleri kullanılarak yapılandırılır.  
  
 Aşağıdaki örnek, basitleştirilmiş yapılandırma modelini kullanan bu konunun başındakine eşdeğer bir yapılandırma dosyasıdır.  
  
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
> Bu özellik yalnızca Istemci yapılandırması ile değil, yalnızca WCF hizmet yapılandırması ile ilgilidir. Çoğu zaman, WCF istemci yapılandırmasvcutil.exe veya Visual Studio bir hizmet başvurusu ekleyerek gibi bir araç tarafından oluşturulur. Bir WCF istemcisini el ile yapılandırıyorsanız yapılandırmaya bir \<istemci> öğesi eklemeniz ve aramak istediğiniz uç noktaları belirtmeniz gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma](configuring-services-using-configuration-files.md)
- [Hizmetler için Bağlamaları Yapılandırma](configuring-bindings-for-wcf-services.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](./feature-details/configuring-system-provided-bindings.md)
- [Hizmetleri Yapılandırma](configuring-services.md)
- [WCF hizmetlerinin yapılandırılması](configuring-services.md)
- [WCF Hizmetlerini Kodda Yapılandırma](configuring-wcf-services-in-code.md)
