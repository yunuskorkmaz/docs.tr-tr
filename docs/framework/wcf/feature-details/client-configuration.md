---
title: İstemci Yapılandırması
ms.date: 03/30/2017
ms.assetid: 5da5bd3b-65d9-43b7-91b9-cc9e989b1350
ms.openlocfilehash: 2d17438095e65ccf922061c03e406bab35b07c5d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593665"
---
# <a name="client-configuration"></a>İstemci Yapılandırması
İstemcilerin hizmet uç noktalarına bağlanmak için kullanacağı istemci uç noktasının "ABC" özelliklerini, adresi, bağlamayı, davranışı ve sözleşmeyi belirtmek için Windows Communication Foundation (WCF) istemci yapılandırmasını kullanabilirsiniz. [\<client>](../../configure-apps/file-schema/wcf/client.md)Öğesi, [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) özniteliklerini yapılandırmak için öznitelikleri kullanılan bir öğesi içeriyor. Bu öznitelikler, [uç noktaları yapılandırma](#configuring-endpoints) bölümünde ele alınmıştır.  
  
 [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md)Öğesi Ayrıca, [\<metadata>](../../configure-apps/file-schema/wcf/metadata.md) verileri içeri ve dışarı aktarmaya yönelik ayarları belirtmek için kullanılan bir öğesi, [\<headers>](../../configure-apps/file-schema/wcf/headers.md) özel adres üst bilgileri koleksiyonu içeren bir öğesi ve bir [\<identity>](../../configure-apps/file-schema/wcf/identity.md) uç noktanın, ileti alışverişi yapan diğer uç noktalara göre kimlik doğrulamasını sağlayan bir öğesi de içerir. [\<headers>](../../configure-apps/file-schema/wcf/headers.md)Ve [\<identity>](../../configure-apps/file-schema/wcf/identity.md) öğeleri ' ın bir parçasıdır <xref:System.ServiceModel.EndpointAddress> ve [adresler](endpoint-addresses.md) makalesinde ele alınmıştır. Meta veri uzantılarının kullanımını açıklayan konuların bağlantıları, [meta verileri yapılandırma](#configuring-metadata) bölümünde verilmiştir.  
  
## <a name="configuring-endpoints"></a>Uç noktaları yapılandırma  
 İstemci yapılandırması, istemcinin her biri kendi adı, adresi ve sözleşmesine sahip olan bir veya daha fazla uç nokta belirtmesini sağlamak üzere tasarlanmıştır [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) ve [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) Bu uç noktayı yapılandırmak için kullanılacak istemci yapılandırmasındaki ve öğelerine başvurmalıdır. WCF çalışma zamanının beklediği ad olduğundan, istemci yapılandırma dosyası "App. config" olarak adlandırılmalıdır. Aşağıdaki örnekte bir istemci yapılandırma dosyası gösterilmektedir.  
  
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
            <!-- Add another endpoint by adding another <endpoint> element. -->
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
          <!-- Configure this binding here. -->  
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
  
 İsteğe bağlı `name` öznitelik, belirli bir sözleşme için bir uç noktayı benzersiz olarak tanımlar. Bu, <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> veya tarafından, <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> istemci yapılandırmasındaki hangi uç noktanın hedeflenmekte olduğunu ve hizmet için bir kanal oluşturulduğunda yüklenmesi gerektiğini belirtmek için kullanılır. Joker karakterli bir uç nokta yapılandırma adı " \* " mevcuttur ve <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> isteğe tam olarak bir tane varsa ve bir özel durum oluşturursa, dosyanın herhangi bir uç nokta yapılandırmasını yüklemesi gerektiğini gösterir. Bu öznitelik atlanırsa, ilgili uç nokta belirtilen anlaşma türüyle ilişkili varsayılan uç nokta olarak kullanılır. Özniteliğin varsayılan değeri, `name` diğer ad gibi eşleşen boş bir dizedir.  
  
 Uç noktanın yerini bulmak ve tanımlamak için her uç noktanın kendisiyle ilişkili bir adresi olması gerekir. `address`Özniteliği, uç noktanın konumunu sağlayan URL 'yi belirtmek için kullanılabilir. Ancak bir hizmet uç noktasının adresi bir Tekdüzen Kaynak tanımlayıcısı (URI) oluşturularak kodda de belirtilebilir ve <xref:System.ServiceModel.ServiceHost> metotlardan biri kullanılarak eklenir <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> . Daha fazla bilgi için bkz. [adresler](endpoint-addresses.md). Giriş gösterdiği gibi, [\<headers>](../../configure-apps/file-schema/wcf/headers.md) ve öğeleri ' [\<identity>](../../configure-apps/file-schema/wcf/identity.md) ın bir parçasıdır <xref:System.ServiceModel.EndpointAddress> ve de [adresler](endpoint-addresses.md) konusunda ele alınmıştır.  
  
 `binding`Özniteliği, uç noktanın bir hizmete bağlanırken kullanması beklenen bağlama türünü gösterir. Başvuruluyorsa, türün kayıtlı bir yapılandırma bölümü olmalıdır. Önceki örnekte, bu, [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) uç noktanın bir kullandığını gösteren bölümdür <xref:System.ServiceModel.WSHttpBinding> . Ancak, uç noktanın kullanabileceği belirli bir türün birden fazla bağlaması olabilir. Bunların her birinin [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) (Binding) türü öğesinde kendi öğesi vardır. `bindingconfiguration`Özniteliği aynı türden bağlamaları ayırt etmek için kullanılır. Değeri, `name` öğesinin özniteliğiyle eşleştirilir [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) . Yapılandırma kullanarak istemci bağlamasını yapılandırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: yapılandırmada Istemci bağlaması belirtme](../how-to-specify-a-client-binding-in-configuration.md).  
  
 `behaviorConfiguration`Bu öznitelik, [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) uç noktanın ne kadar kullanılacağını belirtmek için kullanılır [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) . Değeri, `name` öğesinin özniteliğiyle eşleştirilir [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) . İstemci davranışlarını belirtmek için yapılandırma kullanmayla ilgili bir örnek için bkz. [Istemci davranışlarını yapılandırma](../configuring-client-behaviors.md).  
  
 `contract`Öznitelik, uç noktanın hangi sözleşmeye sahip olduğunu belirtir. Bu değer ile eşlenir <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> <xref:System.ServiceModel.ServiceContractAttribute> . Varsayılan değer, hizmeti uygulayan sınıfın tam tür adıdır.  
  
### <a name="configuring-metadata"></a>Meta verileri yapılandırma  
 [\<metadata>](../../configure-apps/file-schema/wcf/metadata.md)Öğesi, meta veri içeri aktarma uzantılarını kaydetmek için kullanılan ayarları belirtmek için kullanılır. Meta veri sistemini genişletme hakkında daha fazla bilgi için bkz. [veri sistemini genişletme](../extending/extending-the-metadata-system.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uç Noktalar: Adresler, Bağlamalar ve Anlaşmalar](endpoints-addresses-bindings-and-contracts.md)
- [İstemci Davranışlarını Yapılandırma](../configuring-client-behaviors.md)
