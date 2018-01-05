---
title: "İstemci Yapılandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5da5bd3b-65d9-43b7-91b9-cc9e989b1350
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7ece2585287f6e2767e64c2ec03c75adcfe161c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="client-configuration"></a><span data-ttu-id="47754-102">İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="47754-102">Client Configuration</span></span>
<span data-ttu-id="47754-103">Kullanabileceğiniz [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] , bağlama davranışı adresi belirtin ve sözleşme istemci yapılandırmasını, hizmet uç noktalarına bağlanmak için istemcileri kullanın istemci uç nokta "ABC" özelliklerini.</span><span class="sxs-lookup"><span data-stu-id="47754-103">You can use the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client configuration to specify the address, binding, behavior, and contract, the "ABC" properties of the client endpoint, which clients use to connect to service endpoints.</span></span> <span data-ttu-id="47754-104">[ \<İstemci >](../../../../docs/framework/configure-apps/file-schema/wcf/client.md) öğeye sahip bir [ \<uç noktası >](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) öğesi özniteliklerini ABC uç noktası yapılandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="47754-104">The [\<client>](../../../../docs/framework/configure-apps/file-schema/wcf/client.md) element has an [\<endpoint>](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) element whose attributes are used to configure the endpoint ABCs.</span></span> <span data-ttu-id="47754-105">Bu öznitelikler, bu konunun "Uç noktaları yapılandırma" bölümünde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="47754-105">These attributes are discussed in the "Configuring Endpoints" section of this topic.</span></span>  
  
 <span data-ttu-id="47754-106">[ \<Uç noktası >](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) öğesi de içerir bir [ \<meta verileri >](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) içeri ve dışarı aktarma meta veriler için ayarları belirtmek için kullanılan öğesi bir [ \<üstbilgiler >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) özel adres üstbilgileri koleksiyonunu içeren öğe ve bir [ \<kimliği >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) bir uç nokta diğer uç noktaları tarafından kimlik doğrulamasına olanak tanıyan öğe iletileri bu adla değişimi.</span><span class="sxs-lookup"><span data-stu-id="47754-106">The [\<endpoint>](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) element also contains a [\<metadata>](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) element that is used to specify settings for importing and exporting metadata , a [\<headers>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) element that contains a collection of custom address headers, and an [\<identity>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) element that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span> <span data-ttu-id="47754-107">[ \<Üstbilgiler >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) ve [ \<kimliği >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) öğeleri parçası olan <xref:System.ServiceModel.EndpointAddress> ve ele alınmıştır [adresleri](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) konu.</span><span class="sxs-lookup"><span data-stu-id="47754-107">The [\<headers>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) and [\<identity>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elements are part of the <xref:System.ServiceModel.EndpointAddress> and are discussed in the [Addresses](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) topic.</span></span> <span data-ttu-id="47754-108">Bu konunun yapılandırma meta verilerini alt kısmında meta verileri uzantıları kullanımını açıklayan konulara bağlantılar sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="47754-108">Links to topics that explain the use of metadata extensions are provided in the Configuring Metadata sub-section of this topic.</span></span>  
  
## <a name="configuring-endpoints"></a><span data-ttu-id="47754-109">Uç noktalarını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="47754-109">Configuring Endpoints</span></span>  
 <span data-ttu-id="47754-110">İstemci yapılandırması bir tane belirtmek istemcinin sağlamak için tasarlanmıştır veya daha fazla uç noktalar, her biri kendi adına sahip adres ve Sözleşme, her başvuran ile [ \<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) ve [ \< davranışları >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) Bu uç yapılandırmak için kullanılan istemci yapılandırma öğeleri.</span><span class="sxs-lookup"><span data-stu-id="47754-110">The client configuration is designed to allow the client to specify one or more endpoints, each with its own name, address, and contract, with each referencing the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) and [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elements in the client configuration to be used to configure that endpoint.</span></span> <span data-ttu-id="47754-111">Bu adı olduğundan istemci yapılandırma dosyası "App.config" adlı olmalıdır, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] çalışma zamanı bekliyor.</span><span class="sxs-lookup"><span data-stu-id="47754-111">The client configuration file should be named "App.config" because this is the name that the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime expects.</span></span> <span data-ttu-id="47754-112">Aşağıdaki örnek, bir istemci yapılandırma dosyası gösterir.</span><span class="sxs-lookup"><span data-stu-id="47754-112">The following example shows a client configuration file.</span></span>  
  
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
  
 <span data-ttu-id="47754-113">İsteğe bağlı `name` özniteliği benzersiz olarak tanımlayan belirli bir sözleşme için bir uç nokta.</span><span class="sxs-lookup"><span data-stu-id="47754-113">The optional `name` attribute uniquely identifies an endpoint for a given contract.</span></span> <span data-ttu-id="47754-114">Tarafından kullanılan <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> veya <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> istemci yapılandırmasında hangi uç noktaya hedeflenen ve hizmet için bir kanal oluşturulduğunda yüklenmesi gereken belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="47754-114">It is used by the <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> or by the <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> to specify which endpoint in the client configuration is being targeted and must be loaded when a channel is created to service.</span></span> <span data-ttu-id="47754-115">Joker karakter uç nokta Yapılandırması adı "*" kullanılabilir ve gösterir <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> sağlanmış tam olarak bir kullanılabilir ve aksi durumda, herhangi bir uç nokta yapılandırma dosyasında yükleyeceğini yöntemi bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="47754-115">A wildcard endpoint configuration name "*" is available and indicates to the <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> method that it should load any endpoint configuration in the file, provided there is precisely one available, and otherwise throws an exception.</span></span> <span data-ttu-id="47754-116">Bu öznitelik atlanırsa, karşılık gelen endpoint belirtilen sözleşme türüyle ilişkili varsayılan uç noktası olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="47754-116">If this attribute is omitted, the corresponding endpoint is used as the default endpoint associated with the specified contract type.</span></span> <span data-ttu-id="47754-117">İçin varsayılan değer `name` gibi diğer adıyla eşleşen boş bir dize bir özniteliktir.</span><span class="sxs-lookup"><span data-stu-id="47754-117">The default value for the `name` attribute is an empty string which is matched like any other name.</span></span>  
  
 <span data-ttu-id="47754-118">Tüm uç bulun ve uç noktayı tanımlamak için ilişkili bir adresi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="47754-118">Every endpoint must have an address associated with it to locate and identify the endpoint.</span></span> <span data-ttu-id="47754-119">`address` Özniteliği, uç nokta konumunu sağlar URL'yi belirtmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="47754-119">The `address` attribute can be used to specify the URL that provides the location of the endpoint.</span></span> <span data-ttu-id="47754-120">Ancak bir hizmet uç noktası adresi Tekdüzen Kaynak Tanımlayıcısı (URI) oluşturarak kodda de belirtilmesi ve eklenen <xref:System.ServiceModel.ServiceHost> birini kullanarak <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="47754-120">But the address for a service endpoint can also be specified in code by creating a Uniform Resource Identifier (URI) and is added to the <xref:System.ServiceModel.ServiceHost> using one of the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> methods.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="47754-121">[Adresleri](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md).</span><span class="sxs-lookup"><span data-stu-id="47754-121"> [Addresses](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md).</span></span> <span data-ttu-id="47754-122">Giriş da anlaşılacağı gibi [ \<üstbilgiler >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) ve [ \<kimliği >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) öğeleri parçası olan <xref:System.ServiceModel.EndpointAddress> ve ayrıca ele alınmıştır [ Adresleri](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) konu.</span><span class="sxs-lookup"><span data-stu-id="47754-122">As the introduction indicates, the [\<headers>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) and [\<identity>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elements are part of the <xref:System.ServiceModel.EndpointAddress> and are also discussed in the [Addresses](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) topic.</span></span>  
  
 <span data-ttu-id="47754-123">`binding` Öznitelik, uç nokta bağlama türünü bekliyor bir hizmete bağlanırken kullanılacak gösterir.</span><span class="sxs-lookup"><span data-stu-id="47754-123">The `binding` attribute indicates the type of binding the endpoint expects to use when connecting to a service.</span></span> <span data-ttu-id="47754-124">Başvurulacak yoksa türü kayıtlı yapılandırma bölümü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="47754-124">The type must have a registered configuration section if it is to be referenced.</span></span> <span data-ttu-id="47754-125">Önceki örnekte budur [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) uç nokta kullandığını gösterir bölüm bir <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="47754-125">In the previous example, this is the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) section, which indicates that the endpoint uses a <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="47754-126">Ancak uç nokta kullanabilirsiniz belirli bir türde birden fazla bağlama olabilir.</span><span class="sxs-lookup"><span data-stu-id="47754-126">But there may be more than one binding of a given type that the endpoint can use.</span></span> <span data-ttu-id="47754-127">Bunların her biri kendi sahip [ \<bağlama >](../../../../docs/framework/misc/binding.md) (bağlama) türü öğe içinde.</span><span class="sxs-lookup"><span data-stu-id="47754-127">Each of these has its own [\<binding>](../../../../docs/framework/misc/binding.md) element within the (binding) type element.</span></span> <span data-ttu-id="47754-128">`bindingconfiguration` Özniteliği aynı türde bağlamaları arasında ayrım yapmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="47754-128">The `bindingconfiguration` attribute is used to distinguish between bindings of the same type.</span></span> <span data-ttu-id="47754-129">Değeri ile eşleşen `name` özniteliği [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="47754-129">Its value is matched with the `name` attribute of the [\<binding>](../../../../docs/framework/misc/binding.md) element.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="47754-130">bir istemciyi nasıl yapılandıracağınız yapılandırmayı kullanarak bağlama bkz [nasıl yapılır: yapılandırmada istemci bağlama belirtme](../../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="47754-130"> how to configure a client binding using configuration, see [How to: Specify a Client Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md).</span></span>  
  
 <span data-ttu-id="47754-131">`behaviorConfiguration` Belirtmek için kullanılan öznitelik [ \<davranışı >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) , [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) uç noktası kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="47754-131">The `behaviorConfiguration` attribute is used to specify which [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) of the [\<endpointBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) the endpoint should use.</span></span> <span data-ttu-id="47754-132">Değeri ile eşleşen `name` özniteliği [ \<davranışı >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="47754-132">Its value is matched with the `name` attribute of the [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element.</span></span> <span data-ttu-id="47754-133">İstemci davranışlarını belirtmek için yapılandırma kullanma örneği için bkz: [istemci davranışlarını yapılandırma](../../../../docs/framework/wcf/configuring-client-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="47754-133">For an example of using configuration to specify client behaviors, see [Configuring Client Behaviors](../../../../docs/framework/wcf/configuring-client-behaviors.md).</span></span>  
  
 <span data-ttu-id="47754-134">`contract` Özniteliği uç nokta gösterme hangi sözleşme belirtir.</span><span class="sxs-lookup"><span data-stu-id="47754-134">The `contract` attribute specifies which contract the endpoint is exposing.</span></span> <span data-ttu-id="47754-135">Bu değer eşlendiği <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> , <xref:System.ServiceModel.ServiceContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="47754-135">This value maps to the <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> of the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span> <span data-ttu-id="47754-136">Hizmet uygulayan sınıfa tam tür adını varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="47754-136">The default value is the full type name of the class that implements the service.</span></span>  
  
### <a name="configuring-metadata"></a><span data-ttu-id="47754-137">Meta verileri yapılandırma</span><span class="sxs-lookup"><span data-stu-id="47754-137">Configuring Metadata</span></span>  
 <span data-ttu-id="47754-138">[ \<Meta verileri >](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) öğe meta verileri kaydetmek için kullanılan ayarları içeri uzantılarını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="47754-138">The [\<metadata>](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) element is used to specify settings used to register metadata import extensions.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="47754-139">meta veri sistemini genişletme bkz[meta veri sistemini genişletme](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md).</span><span class="sxs-lookup"><span data-stu-id="47754-139"> extending the metadata system, see[Extending the Metadata System](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47754-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="47754-140">See Also</span></span>  
 [<span data-ttu-id="47754-141">Uç Noktalar: Adresler, Bağlamalar ve Anlaşmalar</span><span class="sxs-lookup"><span data-stu-id="47754-141">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 [<span data-ttu-id="47754-142">İstemci Davranışlarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="47754-142">Configuring Client Behaviors</span></span>](../../../../docs/framework/wcf/configuring-client-behaviors.md)
