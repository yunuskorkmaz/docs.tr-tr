---
title: <serviceMetadata>
ms.date: 03/30/2017
ms.assetid: 2b4c3b4c-31d4-4908-a9b7-5bb411c221f2
ms.openlocfilehash: c421273d1d08db047a51f1f1e4f9d6c908f12986
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201780"
---
# \<serviceMetadata>
Hizmet meta verilerinin ve ilgili bilgilerin yayınlanmasını belirtir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceMetadata>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<serviceMetadata externalMetadataLocation="String"
                 httpGetBinding="String"
                 httpGetBindingConfiguration="String"
                 httpGetEnabled="Boolean"
                 httpGetUrl="String"
                 httpsGetBinding="String"
                 httpsGetBindingConfiguration="String"
                 httpsGetEnabled="Boolean"
                 httpsGetUrl="String"
                 policyVersion="Policy12/Policy15" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|externalMetadataLocation|Otomatik olarak oluşturulan WSDL yerine WSDL ve MEX isteklerine yanıt olarak döndürülen WSDL dosyasının konumunu içeren bir URI. Bu öznitelik ayarlanmamışsa varsayılan WSDL döndürülür. Varsayılan değer boş bir dizedir.|  
|Bilgilerinie başvuran HttpGetBinding|HTTP GET aracılığıyla meta veri alımı için kullanılacak bağlama türünü belirten bir dize. Bu ayar isteğe bağlıdır. Belirtilmemişse, varsayılan bağlamalar kullanılacaktır.<br /><br /> Yalnızca destekleyen iç bağlama öğeleri olan bağlamalar <xref:System.ServiceModel.Channels.IReplyChannel> desteklenecektir. Ayrıca, <xref:System.ServiceModel.Channels.MessageVersion> bağlamanın özelliği olmalıdır <xref:System.ServiceModel.Channels.MessageVersion.None%2A> .|  
|httpGetBindingConfiguration|`httpGetBinding`Bu bağlamanın ek yapılandırma bilgilerine başvuran özniteliğinde belirtilen bağlamanın adını ayarlayan bir dize. Bölümünde aynı ad tanımlanmalıdır `<bindings>` .|  
|httpGetEnabled|Bir HTTP/GET isteği kullanılarak alma için hizmet meta verilerinin yayınlanıp yayınlanmayacağını belirten bir Boole değeri. Varsayılan değer: `false`.<br /><br /> HttpGetUrl özniteliği belirtilmemişse, meta verilerin yayımlandığı adres hizmet adresi artı "? wsdl" dir. Örneğin, hizmet adresi ise `http://localhost:8080/CalculatorService` , http/get meta veri adresi olur `http://localhost:8080/CalculatorService?wsdl` .<br /><br /> Bu özellik ise `false` veya hizmetin adresı http veya https tabanlı değilse, "? wsdl" yok sayılır.|  
|httpGetUrl|Bir HTTP/GET isteği kullanılarak alınması için meta verilerin yayımlanacağı adresi belirten bir URI. Göreli bir URI belirtilmişse, hizmetin temel adresine göreli olarak değerlendirilir.|  
|Bilgilerinie başvuran HttpsGetBinding|HTTPS GET aracılığıyla meta veri alımı için kullanılacak bağlama türünü belirten bir dize. Bu ayar isteğe bağlıdır. Belirtilmemişse, varsayılan bağlamalar kullanılacaktır.<br /><br /> Yalnızca destekleyen iç bağlama öğeleri olan bağlamalar <xref:System.ServiceModel.Channels.IReplyChannel> desteklenecektir. Ayrıca, <xref:System.ServiceModel.Channels.MessageVersion> bağlamanın özelliği olmalıdır <xref:System.ServiceModel.Channels.MessageVersion.None%2A> .|  
|httpsGetBindingConfiguration|`httpsGetBinding`Bu bağlamanın ek yapılandırma bilgilerine başvuran özniteliğinde belirtilen bağlamanın adını ayarlayan bir dize. Bölümünde aynı ad tanımlanmalıdır `<bindings>` .|  
|httpsGetEnabled|Bir HTTPS/GET isteği kullanılarak alma için hizmet meta verilerinin yayınlanıp yayınlanmayacağını belirten bir Boole değeri. Varsayılan değer: `false`.<br /><br /> HttpsGetUrl özniteliği belirtilmemişse, meta verilerin yayımlandığı adres, hizmet adresi artı bir "? wsdl" dir. Örneğin, hizmet adresi " https://localhost:8080/CalculatorService " ise, http/get meta veri adresi " https://localhost:8080/CalculatorService?wsdl " olur.<br /><br /> Bu özellik ise `false` veya hizmetin adresı http veya https tabanlı değilse, "? wsdl" yok sayılır.|  
|httpsGetUrl|Bir HTTPS/GET isteği kullanılarak almak için meta verilerin yayımlanacağı adresi belirten bir URI.|  
|policyVersion|Kullanılan WS-Policy belirtiminin sürümünü belirten bir dize. Bu öznitelik türü <xref:System.ServiceModel.Description.PolicyVersion> .|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Hiçbiri  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|Bir davranış öğesi belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yapılandırma öğesi, bir hizmetin meta veri yayımlama özelliklerini denetlemenize olanak tanır. Potansiyel olarak duyarlı hizmet meta verilerinin istenmeden açıklanmasını engellemek için Windows Communication Foundation (WCF) Hizmetleri için varsayılan yapılandırma, meta veri yayımlamayı devre dışı bırakır. Bu davranış, varsayılan olarak güvenlidir, ancak hizmetin meta veri yayımlama davranışı yapılandırmada açıkça etkinleştirilmediği sürece hizmeti çağırmak için gereken istemci kodunu oluşturmak için bir meta veri alma aracı (Svcutil. exe gibi) kullanamazsınız. Bu yapılandırma öğesini kullanarak hizmetiniz için bu yayımlama davranışını etkinleştirebilirsiniz.  
  
 Bu davranışı yapılandırmanın ayrıntılı bir örneği için bkz. [meta veri yayımlama davranışı](../../../wcf/samples/metadata-publishing-behavior.md).  
  
 İsteğe bağlı `httpGetBinding` ve `httpsGetBinding` ÖZNITELIKLERI, http get (veya https Get) aracılığıyla meta veri alımı için kullanılan bağlamaları yapılandırmanıza olanak tanır. Bu değerler belirtilmemişse, varsayılan bağlamalar ( `HttpTransportBindingElement` http durumunda ve `HttpsTransportBindingElement` https durumunda), uygun şekilde meta veri alımı için kullanılır. Bu öznitelikleri yerleşik WCF bağlamaları ile kullanamazsınız. Yalnızca destekleyen iç bağlama öğeleri olan bağlamalar <xref:System.ServiceModel.Channels.IReplyChannel> desteklenecektir. Ayrıca, <xref:System.ServiceModel.Channels.MessageVersion> bağlamanın özelliği olmalıdır <xref:System.ServiceModel.Channels.MessageVersion.None%2A> .  
  
 Bir hizmetin kötü amaçlı kullanıcılara maruz kalmasını azaltmak için, HTTP (HTTPS) üzerinden SSL (HTTPS) mekanizmasını kullanarak aktarımı güvenli hale getirmek mümkündür. Bunu yapmak için, önce uygun bir X. 509.952 sertifikasını hizmeti barındıran bilgisayardaki belirli bir bağlantı noktasına bağlamanız gerekir. (Daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../wcf/feature-details/working-with-certificates.md).) İkinci olarak, bu öğeyi hizmet yapılandırmasına ekleyin ve `httpsGetEnabled` özniteliğini olarak ayarlayın `true` . Son olarak, `httpsGetUrl` Aşağıdaki örnekte gösterildiği gibi, özniteliğini hizmet meta veri uç noktasının URL 'si olarak ayarlayın.  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="NewBehavior">
      <serviceMetadata httpsGetEnabled="true"
                       httpsGetUrl="https://myComputerName/myEndpoint" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, öğesini kullanarak meta verileri açığa çıkarmak için bir hizmet yapılandırır \<serviceMetadata> . Ayrıca, bir uç noktasını bir `IMetadataExchange` WS-MetadataExchange (MEX) protokolünün bir uygulama olarak kullanıma sunmak için yapılandırır. Örnek, `mexHttpBinding` `wsHttpBinding` güvenlik modu olarak ayarlanmış olan öğesine eşdeğer bir standart bağlama olan öğesini kullanır `None` . Uç noktada "mex" göreli adresi kullanılır. bu durum, hizmet tabanı adresine karşı çözümlenirse, bir uç nokta adresinde oluşur `http://localhost/servicemodelsamples/service.svc/mex` .  
  
```xml  
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by the host: http://localhost/servicemodelsamples/service.svc -->
        <endpoint address=""
                  binding="wsHttpBinding"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- The mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex
             To expose the IMetadataExchange contract, you must enable the serviceMetadata behavior as demonstrated below. -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <!-- The serviceMetadata behavior publishes metadata through the IMetadataExchange contract. When this behavior is
               present, you can expose this contract through an endpoint as shown above. Setting httpGetEnabled to true publishes
               the service's WSDL at the <baseaddress>?wsdl eg. http://localhost/servicemodelsamples/service.svc?wsdl -->
          <serviceMetadata httpGetEnabled="True" />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.ServiceMetadataPublishingElement>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- [Güvenlik Davranışları](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Meta Veri Yayımlama Davranışı](../../../wcf/samples/metadata-publishing-behavior.md)
