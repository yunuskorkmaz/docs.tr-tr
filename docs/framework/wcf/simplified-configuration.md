---
title: Basitleştirilmiş Yapılandırma
description: WCF Hizmetleri için Basitleştirilmiş yapılandırma hakkında bilgi edinin. .NET Framework 4.6.1, hizmet yapılandırmasının boyutunu ve karmaşıklığını azaltmak için bir yol sağlar.
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: defaf536d5a5b9f1479271c0976b43e9b1eb5bc4
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246044"
---
# <a name="simplified-configuration"></a>Basitleştirilmiş Yapılandırma
Windows Communication Foundation (WCF) hizmetleri yapılandırmak karmaşık bir görev olabilir. Birçok farklı seçenek vardır ve hangi ayarların gerekli olduğunu belirlemek her zaman kolay değildir. Yapılandırma dosyaları WCF hizmetlerinin esnekliğini artırırken, ayrıca sorunları bulmak için çok zor olan kaynaktır. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]Bu sorunları ele almaktadır ve hizmet yapılandırmasının boyutunu ve karmaşıklığını azaltmak için bir yol sağlar.  
  
## <a name="simplified-configuration"></a>Basitleştirilmiş Yapılandırma  
 WCF hizmeti yapılandırma dosyalarında, <`system.serviceModel`> bölümü `service` barındırılan her hizmet için bir <> öğesi içerir. <`service`> öğesi, `endpoint` her hizmet için sunulan uç noktaları ve isteğe bağlı olarak bir hizmet davranışı kümesini belirten <> öğelerinin bir koleksiyonunu içerir. <`endpoint`> öğeleri, uç nokta tarafından kullanıma sunulan adresi, bağlamayı ve sözleşmeyi belirtir ve isteğe bağlı olarak yapılandırma ve uç nokta davranışları bağlama. <`system.serviceModel`> bölümü ayrıca `behaviors` hizmet veya uç nokta davranışları belirtmenize izin veren bir <> öğesi içerir. Aşağıdaki örnek, `system.serviceModel` bir yapılandırma dosyasının <> bölümünü gösterir.  
  
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
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<> öğesi gereksinimini kaldırarak bir WCF hizmetini yapılandırmayı kolaylaştırır `service` . Bir <`service`> bölümü ekleyemez veya bir <> bölümünde herhangi bir uç nokta ekleyemez `service` ve hizmetiniz program aracılığıyla herhangi bir uç nokta tanımlamıyorsa, her hizmet temel adresi ve hizmetiniz tarafından uygulanan her sözleşme için bir varsayılan uç nokta kümesi otomatik olarak hizmetinize eklenir. Bu uç noktaların her birinde, uç nokta adresi temel adrese karşılık gelir, bağlama ise temel adres düzeni tarafından belirlenir ve sözleşme hizmetiniz tarafından uygulanan bir sözleşmedir. Herhangi bir uç nokta veya hizmet davranışı belirtmeniz veya herhangi bir bağlama ayarı değişikliği yapmanız gerekmiyorsa, bir hizmet yapılandırma dosyası belirtmeniz gerekmez. Bir hizmet iki sözleşme uygularsa ve ana bilgisayar hem HTTP hem de TCP taşımalarını etkinleştirse, hizmet ana bilgisayarı her bir taşıyıcı kullanan her bir sözleşme için dört varsayılan uç nokta oluşturur. Varsayılan uç noktalar oluşturmak için hizmet ana bilgisayarının hangi bağlamaları kullanacağınızı bilmeleri gerekir. Bu ayarlar `protocolMappings` , <> bölümünün içindeki bir <> bölümünde belirtilmiştir `system.serviceModel` . <`protocolMappings`> bölümü, bağlama türlerine eşlenmiş Aktarım Protokolü düzenlerinin bir listesini içerir. Hizmet ana bilgisayarı, hangi bağlamanın kullanılacağını belirleyen, kendisine geçirilen temel adresleri kullanır. Aşağıdaki örnek <`protocolMappings`> öğesini kullanır.  
  
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
  
 Önceki örnekte, "http" düzeniyle başlayan temel adrese sahip bir uç nokta öğesini kullanır <xref:System.ServiceModel.BasicHttpBinding> . Temel adresi "net. TCP" düzeniyle başlayan bir uç nokta, kullanır <xref:System.ServiceModel.NetTcpBinding> . Yerel bir App.config veya Web.config dosyadaki ayarları geçersiz kılabilirsiniz.  
  
 <> bölümündeki her öğe için `protocolMappings` bir şema ve bir bağlama belirtilmelidir. İsteğe bağlı olarak, `bindingConfiguration` yapılandırma dosyasının <> bölümünde bir bağlama yapılandırması belirten bir özniteliği belirtebilir `bindings` . Hayır `bindingConfiguration` belirtilirse, uygun bağlama türünün adsız bağlama yapılandırması kullanılır.  
  
 Hizmet davranışları, `behavior` <> bölümleri içindeki anonim <> bölümleri kullanılarak varsayılan uç noktalar için yapılandırılır `serviceBehaviors` . `behavior`<> içindeki adlandırılmamış <> öğeleri `serviceBehaviors` hizmet davranışlarını yapılandırmak için kullanılır. Örneğin, aşağıdaki yapılandırma dosyası konak içindeki tüm hizmetler için hizmet meta verileri yayımlamayı mümkün bir şekilde sunar.  
  
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
  
 Uç nokta davranışları `behavior` <> bölümleri içindeki anonim <> bölümleri kullanılarak yapılandırılır `serviceBehaviors` .  
  
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
> Bu özellik yalnızca WCF hizmeti yapılandırmasıyla ilgilidir, istemci yapılandırması değildir. WCF istemci yapılandırması, svcutil.exe gibi bir araçla veya Visual Studio 'dan bir hizmet başvurusu ekleyerek oluşturulacaktır. Bir WCF istemcisini el ile yapılandırıyorsanız, \<client> yapılandırmaya bir öğe eklemeniz ve çağırmak istediğiniz uç noktaları belirtmeniz gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma](configuring-services-using-configuration-files.md)
- [Hizmetler için Bağlamaları Yapılandırma](configuring-bindings-for-wcf-services.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](./feature-details/configuring-system-provided-bindings.md)
- [Hizmetleri Yapılandırma](configuring-services.md)
- [WCF hizmetlerini yapılandırma](configuring-services.md)
- [WCF Hizmetlerini Kodda Yapılandırma](configuring-wcf-services-in-code.md)
