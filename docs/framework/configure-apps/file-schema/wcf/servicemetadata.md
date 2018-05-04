---
title: '&lt;serviceMetadata&gt;'
ms.date: 03/30/2017
ms.assetid: 2b4c3b4c-31d4-4908-a9b7-5bb411c221f2
ms.openlocfilehash: 3c59a47f8a45fbccb05eb1f385215fe2aa739836
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltservicemetadatagt"></a>&lt;serviceMetadata&gt;
Hizmet meta verilerini ve ilişkili bilgileri yayımlanmasını belirtir.  
  
\<system.serviceModel>  
\<davranışları >  
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
|ExternalMetadataLocation|Kullanıcıya otomatik olarak oluşturulan WSDL yerine WSDL ve MEX isteklerine yanıt olarak döndürülen bir WSDL dosya konumunu içeren bir URI. Bu öznitelik ayarlandığında, varsayılan WSDL döndürülür. Varsayılan boş bir dizedir.|  
|httpGetBinding|HTTP GET üzerinden meta veri alma işlemi için kullanılacak bağlama türünü belirten bir dize. Bu ayar isteğe bağlıdır. Belirtilmezse, varsayılan bağlamaları kullanılır.<br /><br /> Destek iç bağlama öğeleri yalnızca bağlamalarla <xref:System.ServiceModel.Channels.IReplyChannel> desteklenecektir. Ayrıca, <xref:System.ServiceModel.Channels.MessageVersion> bağlama özelliğini olmalıdır <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.|  
|httpGetBindingConfiguration|Belirtilen bağlama adını ayarlar bir dize `httpGetBinding` Bu bağlama ek yapılandırma bilgilerinin başvuran özniteliği. Aynı adı tanımlanmalıdır `<bindings>` bölümü.|  
|De|Hizmet meta verileri kullanarak bir HTTP/Get isteği alma için yayımlama belirtir bir Boole değeri. Varsayılan, `false` değeridir.<br /><br /> HttpGetUrl özniteliği belirtilmezse, meta veriler yayımlandığında hizmet adresi adresidir artı bir "? wsdl". Örneğin, hizmet adresi ise "http://localhost:8080/CalculatorService", HTTP/Get meta veri adresi"http://localhost:8080/CalculatorService?wsdl".<br /><br /> Bu özellik ise `false`, veya hizmetinin adresini HTTP veya HTTPS bağlı değil "? wsdl" göz ardı edilir.|  
|HttpGetUrl|Meta verileri kullanarak bir HTTP/Get isteği alma için yayımlanan adresini belirtir URI. Göreli URI onu işleneceğini hizmetin taban adresi gibi göre belirtilir.|  
|httpsGetBinding|HTTPS alma yoluyla meta veri alma işlemi için kullanılacak bağlama türünü belirten bir dize. Bu ayar isteğe bağlıdır. Belirtilmezse, varsayılan bağlamaları kullanılır.<br /><br /> Destek iç bağlama öğeleri yalnızca bağlamalarla <xref:System.ServiceModel.Channels.IReplyChannel> desteklenecektir. Ayrıca, <xref:System.ServiceModel.Channels.MessageVersion> bağlama özelliğini olmalıdır <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.|  
|httpsGetBindingConfiguration|Belirtilen bağlama adını ayarlar bir dize `httpsGetBinding` Bu bağlama ek yapılandırma bilgilerinin başvuran özniteliği. Aynı adı tanımlanmalıdır `<bindings>` bölümü.|  
|De|Hizmet meta verileri kullanarak bir HTTPS/Get isteği alma için yayımlama belirtir bir Boole değeri. Varsayılan, `false` değeridir.<br /><br /> HttpGetUrl özniteliği belirtilmezse, meta veriler yayımlandığında hizmet adresi adresidir artı bir "? wsdl". Örneğin, hizmet adresi ise "https://localhost:8080/CalculatorService", HTTP/Get meta veri adresi"https://localhost:8080/CalculatorService?wsdl".<br /><br /> Bu özellik ise `false`, veya hizmetinin adresini HTTP veya HTTPS bağlı değil "? wsdl" göz ardı edilir.|  
|HttpsGetUrl|Meta verileri kullanarak bir HTTPS/Get isteği alma için yayımlanan adresini belirtir URI.|  
|PolicyVersion|Kullanılan WS-Policy belirtimi sürümünü belirten bir dize. Bu öznitelik türünde <xref:System.ServiceModel.Description.PolicyVersion>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranışı >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Bir davranış öğesi belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yapılandırma öğesi, bir hizmetin meta veri yayımlama özelliklerini denetlemenize olanak sağlar. Olası hassas hizmeti meta verilerin yanlışlıkla açığa çıkmasını önlemek için meta veri yayımlama Windows Communication Foundation (WCF) hizmetlerini için varsayılan yapılandırmayı devre dışı bırakır. Bu davranışı varsayılan olarak güvenlidir, ancak ayrıca bir meta veri kullanamayacağı anlamına gelir (örneğin, Svcutil.exe) aracı hizmetin meta veri yayımlama davranışı açıkça yapılandırmasında etkinleştirilmediği sürece hizmetini çağırmak için gerekli istemci kodu oluşturmak üzere, içe. Bu yapılandırma öğesini kullanarak, bu yayımlama davranışı hizmetiniz için etkinleştirebilirsiniz.  
  
 Bu davranış yapılandırma ayrıntılı örnek için bkz: [meta veri yayımlama davranışı](../../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md).  
  
 İsteğe bağlı `httpGetBinding` ve `httpsGetBinding` öznitelikleri HTTP GET (veya HTTPS Al) aracılığıyla meta veri alma işlemi için kullanılan bağlamaları yapılandırma izin verir. Bunlar belirtilmezse, varsayılan bağlamaları (`HttpTransportBindingElement`, HTTP söz konusu olduğunda ve `HttpsTransportBindingElement`, HTTPS söz konusu olduğunda) uygun şekilde meta veri alma işlemi için kullanılır. Bu öznitelikler yerleşik WCF bağlamalarla kullanamazsınız dikkat edin. Destek iç bağlama öğeleri yalnızca bağlamalarla <xref:System.ServiceModel.Channels.IReplyChannel> desteklenecektir. Ayrıca, <xref:System.ServiceModel.Channels.MessageVersion> bağlama özelliğini olmalıdır <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.  
  
 Kötü niyetli kullanıcılar için bir hizmet riskini azaltmak için Güvenli HTTP (HTTPS) mekanizması üzerinde SSL kullanılarak aktarım mümkündür. Bunu yapmak için önce uygun bir X.509 sertifikası hizmetini barındıran bilgisayarda belirli bir bağlantı noktası bağlamanız gerekir. (Daha fazla bilgi için bkz: [sertifikalarla çalışma](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).) İkinci olarak, hizmet yapılandırması için bu öğe ekleyin ve ayarlayın `httpsGetEnabled` özniteliğini `true`. Son olarak, ayarlamak `httpsGetUrl` aşağıdaki örnekte gösterildiği gibi hizmet meta veri uç noktasının URL'sini özniteliği.  
  
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
 Aşağıdaki örnek yapılandırma meta verileri kullanarak kullanıma sunmak için bir hizmet \<serviceMetadata > öğesi. Kullanıma sunmak için bir uç nokta da yapılandırır `IMetadataExchange` WS-MetadataExchange (MEX) Protokolü uygulaması olarak sözleşme. Örnek kullanır `mexHttpBinding`, kolaylık sağlamak amacıyla bağlaması standart olduğu eşdeğerdir `wsHttpBinding` kümesine güvenlik moduyla `None`. "Mex" göreli adresidir kullanılan uç, hangi olduğunda çözülmüş temel Hizmetleri karşı adresi sonuçları bir uç nokta adresi http://localhost/servicemodelsamples/service.svc/mex.  
  
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
          <!-- The serviceMetadata behavior publishes metadata through   
               the IMetadataExchange contract. When this behavior is   
               present, you can expose this contract through an endpoint   
               as shown above. Setting httpGetEnabled to true publishes   
               the service's WSDL at the <baseaddress>?wsdl  
               eg. http://localhost/servicemodelsamples/service.svc?wsdl -->  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.ServiceMetadataPublishingElement>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
 [Güvenlik Davranışları](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Meta Veri Yayımlama Davranışı](../../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)
