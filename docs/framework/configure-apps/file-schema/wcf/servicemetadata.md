---
title: <serviceMetadata>
ms.date: 03/30/2017
ms.assetid: 2b4c3b4c-31d4-4908-a9b7-5bb411c221f2
ms.openlocfilehash: 0b06d61a33cd6a704a5ab0f75d29bde3f72d77fa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59115862"
---
# <a name="servicemetadata"></a>\<serviceMetadata >
Hizmet meta verileri ve ilgili bilgilerin yayınlanmasını belirtir.  
  
\<system.serviceModel>  
\<davranışlar >  
\<serviceBehaviors>  
\<davranışı >  
\<serviceMetadata >  
  
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
|externalMetadataLocation|WSDL ve MEX isteklere otomatik olarak oluşturulan WSDL yerine kullanıcıya döndürülür bir WSDL dosyasının konumunu içeren bir URI. Bu öznitelik ayarlandığında, varsayılan WSDL döndürülür. Varsayılan değer boş bir dizedir.|  
|httpGetBinding|HTTP GET aracılığıyla meta veri alımı için kullanılan bağlama türünü belirten bir dize. Bu ayar isteğe bağlıdır. Belirtilmezse, varsayılan bağlamaları kullanılır.<br /><br /> Destekleyen iç bağlama öğeleri içeren bağlamaları yalnızca <xref:System.ServiceModel.Channels.IReplyChannel> desteklenecektir. Ayrıca, <xref:System.ServiceModel.Channels.MessageVersion> bağlama özelliğini olmalıdır <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.|  
|httpGetBindingConfiguration|İçinde belirtilmiş bağlama adını ayarlayan bir dize `httpGetBinding` bu bağlamanın ek yapılandırma bilgilerinie başvuran öznitelik. Aynı ada tanımlanmalıdır `<bindings>` bölümü.|  
|De|Bir HTTP/Get isteği kullanılarak yapılan alım hizmet için hizmet meta verilerinin belirten bir Boole değeri. Varsayılan, `false` değeridir.<br /><br /> HttpGetUrl özniteliği belirtilmezse, meta veriler yayımlanacağı adresi hizmet adresidir yanı sıra "? wsdl". Örneğin, hizmet adresinin ise "http://localhost:8080/CalculatorService", HTTP/Get meta veri adresi"http://localhost:8080/CalculatorService?wsdl".<br /><br /> Bu özellik ise `false`, HTTP veya HTTPS adresi hizmetinin temel değil veya "? wsdl" göz ardı edilir.|  
|httpGetUrl|Meta veri alma işlemi için bir HTTP/Get isteği kullanılarak yayımlanan adresini belirten bir URI. Göreli bir URI, işleneceğini göre hizmetin taban adresi olarak belirtilir.|  
|httpsGetBinding|HTTPS GET aracılığıyla meta veri alımı için kullanılan bağlama türünü belirten bir dize. Bu ayar isteğe bağlıdır. Belirtilmezse, varsayılan bağlamaları kullanılır.<br /><br /> Destekleyen iç bağlama öğeleri içeren bağlamaları yalnızca <xref:System.ServiceModel.Channels.IReplyChannel> desteklenecektir. Ayrıca, <xref:System.ServiceModel.Channels.MessageVersion> bağlama özelliğini olmalıdır <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.|  
|httpsGetBindingConfiguration|İçinde belirtilmiş bağlama adını ayarlayan bir dize `httpsGetBinding` bu bağlamanın ek yapılandırma bilgilerinie başvuran öznitelik. Aynı ada tanımlanmalıdır `<bindings>` bölümü.|  
|httpsGetEnabled|Bir HTTPS/Get isteği kullanılarak yapılan alım hizmet için hizmet meta verilerinin belirten bir Boole değeri. Varsayılan, `false` değeridir.<br /><br /> HttpGetUrl özniteliği belirtilmezse, meta veriler yayımlanacağı adresi hizmet adresidir yanı sıra "? wsdl". Örneğin, hizmet adresinin ise "https://localhost:8080/CalculatorService", HTTP/Get meta veri adresi"https://localhost:8080/CalculatorService?wsdl".<br /><br /> Bu özellik ise `false`, HTTP veya HTTPS adresi hizmetinin temel değil veya "? wsdl" göz ardı edilir.|  
|httpsGetUrl|Meta veri alma işlemi için bir HTTPS/Get isteği kullanılarak yayımlanan adresini belirten bir URI.|  
|policyVersion|Kullanılan WS-Policy belirtiminin sürümünü belirten bir dize. Bu öznitelik türünde <xref:System.ServiceModel.Description.PolicyVersion>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranışı >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Bir davranış öğesi belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yapılandırma öğesi, bir hizmeti meta veri yayımlama özellikleri denetlemenize olanak tanır. Olası hassas hizmet meta verilerinin yanlışlıkla açığa çıkmasını önlemek için Windows Communication Foundation (WCF) Hizmetleri için varsayılan yapılandırma meta veri yayımlamayı devre dışı bırakır. Bu varsayılan olarak güvenli, davranıştır ancak ayrıca Aracı (Svcutil.exe gibi) yapılandırmasında hizmetin meta veri yayımlama davranışı açıkça etkinleştirilmediği hizmeti çağırmak için gereken istemci kodu oluşturmak için içeri bir meta veri kullanamayacağı anlamına gelir. Bu yapılandırma öğesini kullanarak, bu yayınlama davranışını hizmetiniz için etkinleştirebilirsiniz.  
  
 Bu davranış yapılandırma ayrıntılı örnek için bkz. [meta veri yayımlama davranışı](../../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md).  
  
 İsteğe bağlı `httpGetBinding` ve `httpsGetBinding` öznitelikleri HTTP GET (veya HTTPS GET) aracılığıyla meta veri alımı için kullanılan bağlamaları yapılandırma izin verir. Bunlar belirtilmezse, varsayılan bağlamaları (`HttpTransportBindingElement`, HTTP söz konusu olduğunda ve `HttpsTransportBindingElement`, HTTPS söz konusu olduğunda) uygun şekilde meta veri alımı için kullanılır. Bu öznitelikler yerleşik WCF bağlamaları ile kullanamazsınız dikkat edin. Destekleyen iç bağlama öğeleri içeren bağlamaları yalnızca <xref:System.ServiceModel.Channels.IReplyChannel> desteklenecektir. Ayrıca, <xref:System.ServiceModel.Channels.MessageVersion> bağlama özelliğini olmalıdır <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.  
  
 Kötü amaçlı kullanıcılara bir hizmet riskini azaltmak için Güvenli HTTP (HTTPS) mekanizması üzerinde SSL kullanılarak aktarım mümkündür. Bunu yapmak için önce uygun bir X.509 sertifikası hizmeti barındıran bilgisayardaki belirli bir bağlantı noktası bağlamanız gerekir. (Daha fazla bilgi için [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).) İkinci olarak, hizmet yapılandırması için bu öğe ekleme ve `httpsGetEnabled` özniteliğini `true`. Son olarak, ayarlama `httpsGetUrl` aşağıdaki örnekte gösterildiği gibi hizmet meta veri uç noktası URL'sine özniteliği.  
  
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
 Aşağıdaki örnek yapılandırma kullanarak meta verileri kullanıma sunmak için bir hizmet \<serviceMetadata > öğesi. Ayrıca kullanıma sunmak için bir uç nokta yapılandırır `IMetadataExchange` WS-MetadataExchange (MEX) Protokolü uygulaması olarak sözleşme. Örnekte `mexHttpBinding`, bağlama standart bir kullanışlı olduğu eşdeğer olan `wsHttpBinding` kümesine güvenlik moduyla `None`. Bir "mex" göreli adresini kullanılan uç noktasında olan çözümlenen temel hizmetlerimizi adresi sonuçları bir uç nokta adresi `http://localhost/servicemodelsamples/service.svc/mex`.  
  
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
- [Güvenlik Davranışları](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [Meta Veri Yayımlama Davranışı](../../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)
