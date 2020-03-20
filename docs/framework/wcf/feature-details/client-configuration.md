---
title: İstemci Yapılandırması
ms.date: 03/30/2017
ms.assetid: 5da5bd3b-65d9-43b7-91b9-cc9e989b1350
ms.openlocfilehash: ff82f56639ec451c04624d22fff0bcb03f46d946
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185372"
---
# <a name="client-configuration"></a>İstemci Yapılandırması
İstemci bitiş noktasının adres, bağlama, davranış ve sözleşme,istemci bitiş noktalarına bağlanmak için kullandıkları "ABC" özelliklerini belirtmek için Windows Communication Foundation (WCF) istemci yapılandırmasını kullanabilirsiniz. [ \<İstemci>](../../configure-apps/file-schema/wcf/client.md) öğesi, uç nokta AbC'lerini yapılandırmak için öznitelikleri kullanılan bir [ \<bitiş noktası>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) öğesine sahiptir. Bu [öznitelikler, Yapılandırılan Uç Noktaları](#configuring-endpoints) bölümünde ele alınmıştır.  
  
 Uç nokta>öğesi, meta veri alma ve dışa aktarma ayarlarını belirtmek için kullanılan bir [ \<meta veri>](../../configure-apps/file-schema/wcf/metadata.md) öğesi, özel adres üstbilgileri>bir koleksiyon içeren bir [ \<](../../configure-apps/file-schema/wcf/endpoint-of-client.md) [ \<üstbilgi>](../../configure-apps/file-schema/wcf/headers.md) öğesi ve iletileri başka uç noktalarla değiş tokuş ederek bitiş noktasının kimlik doğrulamasını sağlayan bir [ \<kimlik>](../../configure-apps/file-schema/wcf/identity.md) öğesi de içerir. [ \<](../../configure-apps/file-schema/wcf/identity.md) <xref:System.ServiceModel.EndpointAddress>>[ \<](../../configure-apps/file-schema/wcf/headers.md) ve kimlik>öğeleri üstbilgiler, [Adresler](../../wcf/feature-details/endpoint-addresses.md) makalesinde ele alınmıştır. Meta veri uzantılarının kullanımını açıklayan konulara [bağlantılar, Yapılandırma Meta verileri](#configuring-metadata) bölümünde sağlanır.  
  
## <a name="configuring-endpoints"></a>Bitiş Noktalarını Yapılandırma  
 İstemci yapılandırması, istemcinin her biri kendi adı, adresi ve sözleşmesi olan bir veya daha fazla uç nokta belirtmesine ve her birinin bu bitiş noktasını yapılandırmak için kullanılacak istemci yapılandırmasındaki [ \<>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) ve [ \<davranışları>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) öğelerine başvurmasına olanak sağlamak üzere tasarlanmıştır. WCF çalışma zamanının beklediği ad bu olduğundan, istemci yapılandırma dosyası "App.config" olarak adlandırılmalıdır. Aşağıdaki örnekte bir istemci yapılandırma dosyası gösterilmektedir.  
  
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
  
 İsteğe `name` bağlı öznitelik benzersiz belirli bir sözleşme için bir bitiş noktası tanımlar. İstemci yapılandırmasında hangi <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> bitiş noktasının hedeflendiğini belirtmek için <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> veya tarafından kullanılır ve hizmet e ki kanal oluşturulduğunda yüklenmesi gerekir. Joker karakter uç noktası\*yapılandırma adı " kullanılabilir <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> ve dosyadaki herhangi bir uç nokta yapılandırmasını yüklemesi gerektiğini gösterir, çünkü tam olarak kullanılabilir bir tane olması ve aksi takdirde bir özel durum attırılır. Bu öznitelik atlanırsa, ilgili uç nokta belirtilen sözleşme türüyle ilişkili varsayılan uç nokta olarak kullanılır. Öznitelik için `name` varsayılan değer, başka bir ad gibi eşleşen boş bir dizedir.  
  
 Uç noktanın bulunması ve tanımlanması için her uç noktanın ilişkili bir adresi olmalıdır. Öznitelik, `address` bitiş noktasının konumunu sağlayan URL'yi belirtmek için kullanılabilir. Ancak, bir hizmet bitiş noktasının adresi, Tek düzen kaynak tanımlayıcısı (URI) oluşturularak kodolarak da <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> belirtilebilir ve <xref:System.ServiceModel.ServiceHost> yöntemlerden birine eklenir. Daha fazla bilgi için [Adresler'e](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)bakın. Girişte de belirtildiği gibi, [ \<temel ler>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) ve <xref:System.ServiceModel.EndpointAddress> [ \<kimlik>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) öğeleri [adresler](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) konusunun bir parçasıdır ve ayrıca Adresler konusunda da tartışılır.  
  
 Öznitelik, `binding` bir hizmete bağlanırken uç noktanın kullanmayı beklediği bağlama türünü gösterir. Başvurulacaksa, türün kayıtlı bir yapılandırma bölümü olmalıdır. Önceki örnekte, bu [ \<ws://Binding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) bölümü, bitiş noktası bir <xref:System.ServiceModel.WSHttpBinding>. Ancak, bitiş noktasının kullanabileceği belirli bir türde birden fazla bağlayıcı olabilir. Bunların her biri [ \<](../../configure-apps/file-schema/wcf/bindings.md) (bağlama) türü öğesi içinde kendi bağlayıcı>öğesi vardır. Öznitelik, `bindingconfiguration` aynı türdeki bağlayıcıları birbirinden ayırmak için kullanılır. Değeri `name` [ \<bağlayıcı>](../../configure-apps/file-schema/wcf/bindings.md) öğesinin özniteliği ile eşleşir. Yapılandırmayı kullanarak istemci bağlamasını yapılandırma hakkında daha fazla bilgi için [bkz.](../../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)  
  
 Öznitelik, `behaviorConfiguration` [ \<bitiş noktası>uç nokta davranışlarının](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) [ \<hangi davranışı>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) kullanması gerektiğini belirtmek için kullanılır. Değeri, [ \<davranış>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) `name` öğesinin özniteliğiyle eşleşir. İstemci davranışlarını belirtmek için yapılandırmayı kullanma örneği [için](../../../../docs/framework/wcf/configuring-client-behaviors.md)bkz.  
  
 Öznitelik, `contract` bitiş noktasının hangi sözleşmeyi ortaya çıkardığını belirtir. Bu değer eşler <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> <xref:System.ServiceModel.ServiceContractAttribute>. Varsayılan değer, hizmeti uygulayan sınıfın tam tür adıdır.  
  
### <a name="configuring-metadata"></a>Meta verileri yapılandırma  
 [ \<Meta veri>](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) öğesi meta veri alma uzantılarını kaydetmek için kullanılan ayarları belirtmek için kullanılır. Meta veri sisteminin genişletilmesi hakkında daha fazla bilgi için [bkz.](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uç Noktalar: Adresler, Bağlamalar ve Anlaşmalar](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [İstemci Davranışlarını Yapılandırma](../../../../docs/framework/wcf/configuring-client-behaviors.md)
