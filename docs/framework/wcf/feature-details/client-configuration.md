---
title: İstemci Yapılandırması
ms.date: 03/30/2017
ms.assetid: 5da5bd3b-65d9-43b7-91b9-cc9e989b1350
ms.openlocfilehash: 6a5cbf5d536af8649b0b8bb93600e94a48c507c1
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141777"
---
# <a name="client-configuration"></a>İstemci Yapılandırması
İstemcilerin hizmet uç noktalarına bağlanmak için kullanacağı istemci uç noktasının "ABC" özelliklerini, adresi, bağlamayı, davranışı ve sözleşmeyi belirtmek için Windows Communication Foundation (WCF) istemci yapılandırmasını kullanabilirsiniz. [\<istemci >](../../configure-apps/file-schema/wcf/client.md) öğesi, özniteliklerini yapılandırmak için öznitelikleri kullanılan bir [\<uç nokta >](../../configure-apps/file-schema/wcf/endpoint-of-client.md) öğesi içerir. Bu öznitelikler, [uç noktaları yapılandırma](#configuring-endpoints) bölümünde ele alınmıştır.  
  
 [\<uç noktası >](../../configure-apps/file-schema/wcf/endpoint-of-client.md) öğesi Ayrıca, verileri içeri ve dışarı aktarmaya yönelik ayarları belirtmek için kullanılan bir [\<meta veri >](../../configure-apps/file-schema/wcf/metadata.md) öğesi içerir, özel adres üst bilgileri koleksiyonu içeren bir [\<üst bilgi >](../../configure-apps/file-schema/wcf/headers.md) öğesi ve bir uç noktanın, ileti alışverişi yapan diğer uç noktalara yönelik kimlik doğrulamasını sağlayan [\<Identity >](../../configure-apps/file-schema/wcf/identity.md) öğesi. [\<üst bilgileri >](../../configure-apps/file-schema/wcf/headers.md) ve [\<kimlik >](../../configure-apps/file-schema/wcf/identity.md) öğeleri <xref:System.ServiceModel.EndpointAddress> parçasıdır ve [adresler](../../wcf/feature-details/endpoint-addresses.md) makalesinde ele alınmıştır. Meta veri uzantılarının kullanımını açıklayan konuların bağlantıları, [meta verileri yapılandırma](#configuring-metadata) bölümünde verilmiştir.  
  
## <a name="configuring-endpoints"></a>Uç noktaları yapılandırma  
 İstemci yapılandırması, her biri bir veya daha fazla uç nokta (her biri kendi adı, adresi ve sözleşmesiyle), her biri [\<bağlamalarına](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) ve bu uç noktayı yapılandırmak için kullanılacak istemci yapılandırmasındaki öğelerin [\<> davranışlarına](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) > başvuran bir veya daha fazla bitiş noktası belirtmesini sağlayacak şekilde tasarlanmıştır. WCF çalışma zamanının beklediği ad olduğundan, istemci yapılandırma dosyası "App. config" olarak adlandırılmalıdır. Aşağıdaki örnekte bir istemci yapılandırma dosyası gösterilmektedir.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
        <client>  
          <endpoint  
            name="endpoint1"  
            address="http://localhost/ServiceModelSamples/service.svc"  
            binding="wsHttpBinding"  
            bindingConfiguration="WSHttpBinding_IHello"  
            behaviorConfiguration="IHello_Behavior"  
            contract="IHello" >  
  
            <metadata>  
              <wsdlImporters>  
                <extension  
                  type="Microsoft.ServiceModel.Samples.WsdlDocumentationImporter, WsdlDocumentation"/>  
              </wsdlImporters>  
            </metadata>  
  
            <identity>  
              <servicePrincipalName value="host/localhost" />  
            </identity>  
          </endpoint>  
// Add another endpoint by adding another <endpoint> element.  
          <endpoint  
            name="endpoint2">  
           //Configure another endpoint here.  
          </endpoint>  
        </client>  
  
//The bindings section references by the bindingConfiguration endpoint attribute.  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_IHello"   
                 bypassProxyOnLocal="false"   
                 hostNameComparisonMode="StrongWildcard">  
          <readerQuotas maxDepth="32"/>  
          <reliableSession ordered="true"   
                           enabled="false" />  
          <security mode="Message">  
           //Security settings go here.  
          </security>  
        </binding>  
        <binding name="Another Binding"  
        //Configure this binding here.  
        </binding>  
          </wsHttpBinding>  
        </bindings>  
  
//The behavior section references by the behaviorConfiguration endpoint attribute.  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name=" IHello_Behavior ">  
                    <clientVia />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
  
    </system.serviceModel>  
</configuration>  
```  
  
 İsteğe bağlı `name` özniteliği belirli bir sözleşme için bir uç noktayı benzersiz olarak tanımlar. Bu, <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> veya <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> tarafından, istemci yapılandırmasındaki hangi uç noktanın hedeflenmekte olduğunu ve hizmet için bir kanal oluşturulduğunda yüklenmesi gerektiğini belirtmek için kullanılır. "\*" joker uç noktası yapılandırma adı kullanılabilir ve <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> yönteminin, dosyanın herhangi bir uç nokta yapılandırmasını yüklemesi gerektiğini, ancak tam olarak kullanılabilir olduğunu ve aksi durumda bir özel durum oluşturacağını belirtir. Bu öznitelik atlanırsa, ilgili uç nokta belirtilen anlaşma türüyle ilişkili varsayılan uç nokta olarak kullanılır. `name` özniteliği için varsayılan değer, diğer ad gibi eşleşen boş bir dizedir.  
  
 Uç noktanın yerini bulmak ve tanımlamak için her uç noktanın kendisiyle ilişkili bir adresi olması gerekir. `address` özniteliği, uç noktanın konumunu sağlayan URL 'YI belirtmek için kullanılabilir. Ancak, bir hizmet uç noktasının adresi bir Tekdüzen Kaynak tanımlayıcısı (URI) oluşturularak kodda de belirtilebilir ve <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> yöntemlerinden biri kullanılarak <xref:System.ServiceModel.ServiceHost> eklenir. Daha fazla bilgi için bkz. [adresler](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md). Giriş gösterdiği gibi, [\<üst bilgileri >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) ve [\<kimlik >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) öğeleri <xref:System.ServiceModel.EndpointAddress> bir parçasıdır ve ayrıca [adresler](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) konusunda da ele alınmıştır.  
  
 `binding` özniteliği, uç noktanın bir hizmete bağlanırken kullanmasını beklediği bağlamanın türünü gösterir. Başvuruluyorsa, türün kayıtlı bir yapılandırma bölümü olmalıdır. Önceki örnekte bu, uç noktanın bir <xref:System.ServiceModel.WSHttpBinding>kullandığını gösteren [\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) bölümüdür. Ancak, uç noktanın kullanabileceği belirli bir türün birden fazla bağlaması olabilir. Bunların her biri, (Binding) türü öğesi içinde [> öğesi\<bağlama](../../configure-apps/file-schema/wcf/bindings.md) . `bindingconfiguration` özniteliği aynı türden bağlamaları ayırt etmek için kullanılır. Değeri, [\<binding >](../../configure-apps/file-schema/wcf/bindings.md) öğesinin `name` özniteliğiyle eşleştirilir. Yapılandırma kullanarak istemci bağlamasını yapılandırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: yapılandırmada Istemci bağlaması belirtme](../../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md).  
  
 `behaviorConfiguration` özniteliği, uç noktanın > [\<EndpointBehavior >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) hangi [\<davranışının](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) kullanılacağını belirtmek için kullanılır. Değeri, [\<behavior >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) öğesinin `name` özniteliğiyle eşleştirilir. İstemci davranışlarını belirtmek için yapılandırma kullanmayla ilgili bir örnek için bkz. [Istemci davranışlarını yapılandırma](../../../../docs/framework/wcf/configuring-client-behaviors.md).  
  
 `contract` özniteliği, uç noktanın hangi sözleşmeyi gösterir belirtir. Bu değer <xref:System.ServiceModel.ServiceContractAttribute><xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> eşlenir. Varsayılan değer, hizmeti uygulayan sınıfın tam tür adıdır.  
  
### <a name="configuring-metadata"></a>Meta verileri yapılandırma  
 Meta veri alma uzantılarını kaydetmek için kullanılan ayarları belirtmek için [\<meta veri >](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) öğesi kullanılır. Meta veri sistemini genişletme hakkında daha fazla bilgi için bkz. [veri sistemini genişletme](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uç Noktalar: Adresler, Bağlamalar ve Anlaşmalar](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [İstemci Davranışlarını Yapılandırma](../../../../docs/framework/wcf/configuring-client-behaviors.md)
