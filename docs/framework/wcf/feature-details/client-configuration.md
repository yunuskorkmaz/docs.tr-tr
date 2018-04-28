---
title: İstemci Yapılandırması
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5da5bd3b-65d9-43b7-91b9-cc9e989b1350
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 19d1f7630c96f557791f0682fbc0c5d7286c7eb7
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="client-configuration"></a>İstemci Yapılandırması
Kullanabileceğiniz [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] , bağlama davranışı adresi belirtin ve sözleşme istemci yapılandırmasını, hizmet uç noktalarına bağlanmak için istemcileri kullanın istemci uç nokta "ABC" özelliklerini. [ \<İstemci >](../../../../docs/framework/configure-apps/file-schema/wcf/client.md) öğeye sahip bir [ \<uç noktası >](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) öğesi özniteliklerini ABC uç noktası yapılandırmak için kullanılır. Bu öznitelikler, bu konunun "Uç noktaları yapılandırma" bölümünde ele alınmıştır.  
  
 [ \<Uç noktası >](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) öğesi de içerir bir [ \<meta verileri >](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) içeri ve dışarı aktarma meta veriler için ayarları belirtmek için kullanılan öğesi bir [ \<üstbilgiler >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) özel adres üstbilgileri koleksiyonunu içeren öğe ve bir [ \<kimliği >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) bir uç nokta diğer uç noktaları tarafından kimlik doğrulamasına olanak tanıyan öğe iletileri bu adla değişimi. [ \<Üstbilgiler >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) ve [ \<kimliği >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) öğeleri parçası olan <xref:System.ServiceModel.EndpointAddress> ve ele alınmıştır [adresleri](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) konu. Bu konunun yapılandırma meta verilerini alt kısmında meta verileri uzantıları kullanımını açıklayan konulara bağlantılar sağlanmaktadır.  
  
## <a name="configuring-endpoints"></a>Uç noktalarını yapılandırma  
 İstemci yapılandırması bir tane belirtmek istemcinin sağlamak için tasarlanmıştır veya daha fazla uç noktalar, her biri kendi adına sahip adres ve Sözleşme, her başvuran ile [ \<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) ve [ \< davranışları >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) Bu uç yapılandırmak için kullanılan istemci yapılandırma öğeleri. Bu adı olduğundan istemci yapılandırma dosyası "App.config" adlı olmalıdır, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] çalışma zamanı bekliyor. Aşağıdaki örnek, bir istemci yapılandırma dosyası gösterir.  
  
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
  
 İsteğe bağlı `name` özniteliği benzersiz olarak tanımlayan belirli bir sözleşme için bir uç nokta. Tarafından kullanılan <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> veya <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> istemci yapılandırmasında hangi uç noktaya hedeflenen ve hizmet için bir kanal oluşturulduğunda yüklenmesi gereken belirtmek için. Joker karakter uç nokta Yapılandırması adı "*" kullanılabilir ve gösterir <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> sağlanmış tam olarak bir kullanılabilir ve aksi durumda, herhangi bir uç nokta yapılandırma dosyasında yükleyeceğini yöntemi bir özel durum oluşturur. Bu öznitelik atlanırsa, karşılık gelen endpoint belirtilen sözleşme türüyle ilişkili varsayılan uç noktası olarak kullanılır. İçin varsayılan değer `name` gibi diğer adıyla eşleşen boş bir dize bir özniteliktir.  
  
 Tüm uç bulun ve uç noktayı tanımlamak için ilişkili bir adresi olması gerekir. `address` Özniteliği, uç nokta konumunu sağlar URL'yi belirtmek için kullanılabilir. Ancak bir hizmet uç noktası adresi Tekdüzen Kaynak Tanımlayıcısı (URI) oluşturarak kodda de belirtilmesi ve eklenen <xref:System.ServiceModel.ServiceHost> birini kullanarak <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> yöntemleri. Daha fazla bilgi için bkz: [adresleri](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md). Giriş da anlaşılacağı gibi [ \<üstbilgiler >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) ve [ \<kimliği >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) öğeleri parçası olan <xref:System.ServiceModel.EndpointAddress> ve ayrıca ele alınmıştır [ Adresleri](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) konu.  
  
 `binding` Öznitelik, uç nokta bağlama türünü bekliyor bir hizmete bağlanırken kullanılacak gösterir. Başvurulacak yoksa türü kayıtlı yapılandırma bölümü olması gerekir. Önceki örnekte budur [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) uç nokta kullandığını gösterir bölüm bir <xref:System.ServiceModel.WSHttpBinding>. Ancak uç nokta kullanabilirsiniz belirli bir türde birden fazla bağlama olabilir. Bunların her biri kendi sahip [ \<bağlama >](../../../../docs/framework/misc/binding.md) (bağlama) türü öğe içinde. `bindingconfiguration` Özniteliği aynı türde bağlamaları arasında ayrım yapmak için kullanılır. Değeri ile eşleşen `name` özniteliği [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğesi. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] bir istemciyi nasıl yapılandıracağınız yapılandırmayı kullanarak bağlama bkz [nasıl yapılır: yapılandırmada istemci bağlama belirtme](../../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md).  
  
 `behaviorConfiguration` Belirtmek için kullanılan öznitelik [ \<davranışı >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) , [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) uç noktası kullanmanız gerekir. Değeri ile eşleşen `name` özniteliği [ \<davranışı >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) öğesi. İstemci davranışlarını belirtmek için yapılandırma kullanma örneği için bkz: [istemci davranışlarını yapılandırma](../../../../docs/framework/wcf/configuring-client-behaviors.md).  
  
 `contract` Özniteliği uç nokta gösterme hangi sözleşme belirtir. Bu değer eşlendiği <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> , <xref:System.ServiceModel.ServiceContractAttribute>. Hizmet uygulayan sınıfa tam tür adını varsayılan değerdir.  
  
### <a name="configuring-metadata"></a>Meta verileri yapılandırma  
 [ \<Meta verileri >](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) öğe meta verileri kaydetmek için kullanılan ayarları içeri uzantılarını belirtmek için kullanılır. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] meta veri sistemini genişletme bkz[meta veri sistemini genişletme](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uç Noktalar: Adresler, Bağlamalar ve Anlaşmalar](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 [İstemci Davranışlarını Yapılandırma](../../../../docs/framework/wcf/configuring-client-behaviors.md)
