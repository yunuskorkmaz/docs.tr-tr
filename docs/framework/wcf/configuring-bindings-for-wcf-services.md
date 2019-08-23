---
title: Windows Communication Foundation Hizmetleri için Bağlamaları Yapılandırma
ms.date: 03/30/2017
helpviewer_keywords:
- binding configuration [WCF]
ms.assetid: 99a85fd8-f7eb-4a84-a93e-7721b37d415c
ms.openlocfilehash: bfcdcd172d96660c3351926a9c42d298ac3fa654
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928561"
---
# <a name="configuring-bindings-for-windows-communication-foundation-services"></a><span data-ttu-id="76092-102">Windows Communication Foundation Hizmetleri için Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="76092-102">Configuring Bindings for Windows Communication Foundation Services</span></span>
<span data-ttu-id="76092-103">Uygulama oluştururken genellikle, uygulamanın dağıtımıyla sonra kararları yöneticiye erteleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76092-103">When creating an application, you often want to defer decisions to the administrator after the deployment of the application.</span></span> <span data-ttu-id="76092-104">Örneğin, bir hizmet adresinin veya Tekdüzen kaynak tanımlayıcısının (URI) ne kadar ilerlediğinin bilmesinin bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="76092-104">For example, there is often no way of knowing in advance what a service address, or Uniform Resource Identifier (URI), will be.</span></span> <span data-ttu-id="76092-105">Bir adresi sabit kodlamak yerine, bir hizmet oluşturduktan sonra yöneticinin bunu yapmasına izin vermek tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="76092-105">Instead of hard-coding an address, it is preferable to allow an administrator to do so after creating a service.</span></span> <span data-ttu-id="76092-106">Bu esneklik yapılandırma aracılığıyla gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="76092-106">This flexibility is accomplished through configuration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="76092-107">Yapılandırma dosyalarını hızlı bir şekilde oluşturmak için [ServiceModel meta veri yardımcı programı 'nı (Svcutil. exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) `/config` anahtarla birlikte kullanın.</span><span class="sxs-lookup"><span data-stu-id="76092-107">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) with the `/config` switch to quickly create configuration files.</span></span>  
  
## <a name="major-sections"></a><span data-ttu-id="76092-108">Ana bölümler</span><span class="sxs-lookup"><span data-stu-id="76092-108">Major Sections</span></span>  
 <span data-ttu-id="76092-109">Windows Communication Foundation (WCF) yapılandırma şeması, aşağıdaki üç ana bölümü içerir (`serviceModel`, `bindings`ve `services`):</span><span class="sxs-lookup"><span data-stu-id="76092-109">The Windows Communication Foundation (WCF) configuration scheme includes the following three major sections (`serviceModel`, `bindings`, and `services`):</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <bindings>  
        </bindings>  
        <services>  
        </services>  
        <behaviors>  
        </behaviors>  
    </system.serviceModel>  
</configuration>  
```  
  
### <a name="servicemodel-elements"></a><span data-ttu-id="76092-110">ServiceModel öğeleri</span><span class="sxs-lookup"><span data-stu-id="76092-110">ServiceModel Elements</span></span>  
 <span data-ttu-id="76092-111">Bir hizmet türünü bir veya daha fazla uç `system.ServiceModel` nokta ile ve bir hizmetin ayarlarını yapılandırmak için, öğesiyle sınırlanan bölümü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76092-111">You can use the section bounded by the `system.ServiceModel` element to configure a service type with one or more endpoints, as well as settings for a service.</span></span> <span data-ttu-id="76092-112">Her uç nokta daha sonra bir adresle, sözleşmeyle ve bağlamasıyla yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="76092-112">Each endpoint can then be configured with an address, a contract, and a binding.</span></span> <span data-ttu-id="76092-113">Uç noktalar hakkında daha fazla bilgi için bkz. [Endpoint oluşturmaya genel bakış](../../../docs/framework/wcf/endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="76092-113">For more information about endpoints, see [Endpoint Creation Overview](../../../docs/framework/wcf/endpoint-creation-overview.md).</span></span> <span data-ttu-id="76092-114">Hiçbir uç nokta belirtilmemişse, çalışma zamanı varsayılan uç noktaları ekler.</span><span class="sxs-lookup"><span data-stu-id="76092-114">If no endpoints are specified, the runtime adds default endpoints.</span></span> <span data-ttu-id="76092-115">Varsayılan uç noktalar, bağlamalar ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="76092-115">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
 <span data-ttu-id="76092-116">Bir bağlama, aktarımları (HTTP, TCP, kanallar, Message Queuing) ve protokolleri (güvenlik, güvenilirlik, Işlem akışları) belirtir ve her biri bir uç noktanın dünya ile nasıl iletişim kuracağını belirten bağlama öğelerinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="76092-116">A binding specifies transports (HTTP, TCP, pipes, Message Queuing) and protocols (Security, Reliability, Transaction flows) and consists of binding elements, each of which specifies an aspect of how an endpoint communicates with the world.</span></span>  
  
 <span data-ttu-id="76092-117">Örneğin, [ \<BasicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) öğesinin belirtilmesi, bir uç nokta için aktarım olarak http kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="76092-117">For example, specifying the [\<basicHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element indicates to use HTTP as the transport for an endpoint.</span></span> <span data-ttu-id="76092-118">Bu uç noktayı kullanan hizmet açıldığında bitiş noktasını çalışma zamanında bağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="76092-118">This is used to wire up the endpoint at run time when the service using this endpoint is opened.</span></span>  
  
 <span data-ttu-id="76092-119">İki tür bağlama vardır: önceden tanımlanmış ve özel.</span><span class="sxs-lookup"><span data-stu-id="76092-119">There are two kinds of bindings: predefined and custom.</span></span> <span data-ttu-id="76092-120">Önceden tanımlanmış bağlamalar, yaygın senaryolarda kullanılan öğelerin yararlı birleşimlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="76092-120">Predefined bindings contain useful combinations of elements that are used in common scenarios.</span></span> <span data-ttu-id="76092-121">WCF 'nin sağladığı önceden tanımlanmış bağlama türlerinin bir listesi için bkz. [sistem tarafından sağlanan bağlamalar](../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="76092-121">For a list of predefined binding types that WCF provides, see [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md).</span></span> <span data-ttu-id="76092-122">Önceden tanımlanmış bağlama koleksiyonu, bir hizmet uygulamasının ihtiyacı olan özelliklerin doğru birleşimine sahip değilse, uygulamanın gereksinimlerini karşılamak için özel bağlamalar oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76092-122">If no predefined binding collection has the correct combination of features that a service application needs, you can construct custom bindings to meet the application's requirements.</span></span> <span data-ttu-id="76092-123">Özel Bağlamalar hakkında daha fazla bilgi için bkz [ \<. CustomBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="76092-123">For more information about custom bindings, see [\<customBinding>](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
 <span data-ttu-id="76092-124">Aşağıdaki dört örnekte, bir WCF hizmeti ayarlamak için kullanılan en yaygın bağlama yapılandırmalarının gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="76092-124">The following four examples illustrate the most common binding configurations used for setting up a WCF service.</span></span>  
  
#### <a name="specifying-an-endpoint-to-use-a-binding-type"></a><span data-ttu-id="76092-125">Bağlama türünü kullanmak için bir uç nokta belirtme</span><span class="sxs-lookup"><span data-stu-id="76092-125">Specifying an Endpoint to Use a Binding Type</span></span>  
 <span data-ttu-id="76092-126">İlk örnek, bir adres, sözleşme ve bağlama ile yapılandırılan bir uç noktanın nasıl belirtildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="76092-126">The first example illustrates how to specify an endpoint configured with an address, a contract, and a binding.</span></span>  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
  <!-- This section is optional with the default configuration introduced  
       in .NET Framework 4. -->  
  <endpoint   
      address="/HelloWorld2/"  
      contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
      binding="basicHttpBinding" />
</service>  
```  
  
 <span data-ttu-id="76092-127">Bu örnekte `name` öznitelik, yapılandırmanın hangi hizmet türüyle ilgili olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="76092-127">In this example, the `name` attribute indicates which service type the configuration is for.</span></span> <span data-ttu-id="76092-128">`HelloWorld` Sözleşmeniz ile kodunuzda bir hizmet oluşturduğunuzda, örnek yapılandırmasında tanımlanan tüm uç noktalar ile başlatılır.</span><span class="sxs-lookup"><span data-stu-id="76092-128">When you create a service in your code with the `HelloWorld` contract, it is initialized with all of the endpoints defined in the example configuration.</span></span> <span data-ttu-id="76092-129">Derleme yalnızca bir hizmet sözleşmesi uygularsa, `name` hizmet kullanılabilir tek türü kullandığından öznitelik atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="76092-129">If the assembly implements only one service contract, the `name` attribute can be omitted because the service uses the only available type.</span></span> <span data-ttu-id="76092-130">Öznitelik, biçiminde olması gereken bir dize alır`Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`</span><span class="sxs-lookup"><span data-stu-id="76092-130">The attribute takes a string, which must be in the format `Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`</span></span>  
  
 <span data-ttu-id="76092-131">`address` Özniteliği diğer uç noktaların hizmetle iletişim kurmak için kullandığı URI 'yi belirtir.</span><span class="sxs-lookup"><span data-stu-id="76092-131">The `address` attribute specifies the URI that other endpoints use to communicate to the service.</span></span> <span data-ttu-id="76092-132">URI mutlak ya da göreli yol olabilir.</span><span class="sxs-lookup"><span data-stu-id="76092-132">The URI can be either an absolute or relative path.</span></span> <span data-ttu-id="76092-133">Göreli bir adres sağlanmışsa, konağın bağlamada kullanılan aktarım düzeni için uygun bir temel adres sağlaması beklenir.</span><span class="sxs-lookup"><span data-stu-id="76092-133">If a relative address is provided, the host is expected to provide a base address that is appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="76092-134">Bir adres yapılandırılmamışsa, taban adresin bu uç noktanın adresi olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="76092-134">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span>  
  
 <span data-ttu-id="76092-135">`contract` Öznitelik, bu uç noktanın sunduğu sözleşmeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="76092-135">The `contract` attribute specifies the contract this endpoint is exposing.</span></span> <span data-ttu-id="76092-136">Hizmet uygulaması türü, anlaşma türünü uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="76092-136">The service implementation type must implement the contract type.</span></span> <span data-ttu-id="76092-137">Bir hizmet uygulamasının tek bir anlaşma türü uygularsa, bu özellik atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="76092-137">If a service implementation implements a single contract type, then this property can be omitted.</span></span>  
  
 <span data-ttu-id="76092-138">Öznitelik `binding` , bu belirli uç nokta için kullanılmak üzere önceden tanımlanmış veya özel bir bağlama seçer.</span><span class="sxs-lookup"><span data-stu-id="76092-138">The `binding` attribute selects a predefined or custom binding to use for this specific endpoint.</span></span> <span data-ttu-id="76092-139">Açıkça bir bağlama olmayan bir uç nokta, varsayılan bağlama seçimini `BasicHttpBinding`kullanır.</span><span class="sxs-lookup"><span data-stu-id="76092-139">An endpoint that does not explicitly select a binding uses the default binding selection, which is `BasicHttpBinding`.</span></span>  
  
#### <a name="modifying-a-predefined-binding"></a><span data-ttu-id="76092-140">Önceden tanımlanmış bağlamayı değiştirme</span><span class="sxs-lookup"><span data-stu-id="76092-140">Modifying a Predefined Binding</span></span>  
 <span data-ttu-id="76092-141">Aşağıdaki örnekte, önceden tanımlanmış bir bağlama değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="76092-141">In the following example, a predefined binding is modified.</span></span> <span data-ttu-id="76092-142">Daha sonra, hizmette herhangi bir uç noktayı yapılandırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="76092-142">It can then be used to configure any endpoint in the service.</span></span> <span data-ttu-id="76092-143">Bağlama <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> değeri 1 saniye olarak ayarlanarak değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="76092-143">The binding is modified by setting the <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> value to 1 second.</span></span> <span data-ttu-id="76092-144">Özelliğin bir <xref:System.TimeSpan> nesne döndürdüğünü unutmayın.</span><span class="sxs-lookup"><span data-stu-id="76092-144">Note that the property returns a <xref:System.TimeSpan> object.</span></span>  
  
 <span data-ttu-id="76092-145">Değiştirilen bağlama bağlamalar bölümünde bulunur.</span><span class="sxs-lookup"><span data-stu-id="76092-145">That altered binding is found in the bindings section.</span></span> <span data-ttu-id="76092-146">Bu değiştirilmiş bağlama artık `binding` `endpoint` öğedeki özniteliği ayarlanarak herhangi bir uç nokta oluşturulurken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="76092-146">This altered binding can now be used when creating any endpoint by setting the `binding` attribute in the `endpoint` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="76092-147">Bağlama için belirli bir ad verirseniz, hizmet uç noktasında `bindingConfiguration` belirtilen ' ın onunla eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="76092-147">If you give a particular name to the binding, the `bindingConfiguration` specified in the service endpoint must match with it.</span></span>  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
  <endpoint   
      address="/HelloWorld2/"  
      contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
      binding="basicHttpBinding" />
</service>  
<bindings>  
    <basicHttpBinding   
        receiveTimeout="00:00:01"  
    />  
</bindings>  
```  
  
## <a name="configuring-a-behavior-to-apply-to-a-service"></a><span data-ttu-id="76092-148">Bir hizmete uygulanacak davranışı yapılandırma</span><span class="sxs-lookup"><span data-stu-id="76092-148">Configuring a Behavior to Apply to a Service</span></span>  
 <span data-ttu-id="76092-149">Aşağıdaki örnekte, hizmet türü için belirli bir davranış yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="76092-149">In the following example, a specific behavior is configured for the service type.</span></span> <span data-ttu-id="76092-150">Öğesi, [ServiceModel meta veri yardımcı programı aracının (Svcutil. exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmeti sorgulamak ve meta verilerden Web Hizmetleri Açıklama Dili (wsdl) belgeleri oluşturmak için kullanılır. `ServiceMetadataBehavior`</span><span class="sxs-lookup"><span data-stu-id="76092-150">The `ServiceMetadataBehavior` element is used to enable the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to query the service and generate Web Services Description Language (WSDL) documents from the metadata.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="76092-151">Davranışa belirli bir ad verirseniz, `behaviorConfiguration` hizmet veya uç nokta bölümünde belirtilen bir ad ile aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="76092-151">If you give a particular name to the behavior, the `behaviorConfiguration` specified in the service or endpoint section must match it.</span></span>  
  
```xml  
<behaviors>  
    <behavior>  
        <ServiceMetadata httpGetEnabled="true" />   
    </behavior>  
</behaviors>  
<services>  
    <service   
       name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">
       <endpoint   
          address="http://computer:8080/Hello"  
          contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
          binding="basicHttpBinding" />
    </service>  
</services>  
```  
  
 <span data-ttu-id="76092-152">Önceki yapılandırma, bir istemcinin "HelloWorld" türü belirlenmiş hizmetin meta verilerini aramasını ve almasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="76092-152">The preceding configuration enables a client to call and get the metadata of the "HelloWorld" typed service.</span></span>  
  
 `svcutil /config:Client.exe.config http://computer:8080/Hello?wsdl`  
  
## <a name="specifying-a-service-with-two-endpoints-using-different-binding-values"></a><span data-ttu-id="76092-153">Farklı bağlama değerleri kullanarak Iki uç nokta içeren bir hizmet belirtme</span><span class="sxs-lookup"><span data-stu-id="76092-153">Specifying a Service with Two Endpoints Using Different Binding Values</span></span>  
 <span data-ttu-id="76092-154">Bu son örnekte, `HelloWorld` hizmet türü için iki uç nokta yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="76092-154">In this last example, two endpoints are configured for the `HelloWorld` service type.</span></span> <span data-ttu-id="76092-155">Her uç nokta aynı bağlama türünün `bindingConfiguration` farklı bir özelleştirilmiş özniteliğini kullanır (her biri ' nı `basicHttpBinding`değiştirir).</span><span class="sxs-lookup"><span data-stu-id="76092-155">Each endpoint uses a different customized  `bindingConfiguration` attribute of the same binding type (each modifies the `basicHttpBinding`).</span></span>  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
    <endpoint  
        address="http://computer:8080/Hello1"  
        contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
        binding="basicHttpBinding"  
        bindingConfiguration="shortTimeout" />
    <endpoint  
        address="http://computer:8080/Hello2"  
        contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
        binding="basicHttpBinding"  
        bindingConfiguration="Secure" />
</service>  
<bindings>  
    <basicHttpBinding   
        name="shortTimeout"  
        timeout="00:00:00:01"   
     />  
     <basicHttpBinding   
        name="Secure">  
        <Security mode="Transport" />  
     </basicHttpBinding>
</bindings>  
```  
  
 <span data-ttu-id="76092-156">Aşağıdaki örnekte gösterildiği gibi bir `protocolMapping` bölüm ekleyerek ve bağlamaları yapılandırarak varsayılan yapılandırmayı kullanarak aynı davranışı sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76092-156">You can get the same behavior using the default configuration by adding a `protocolMapping` section and configuring the bindings as demonstrated in the following example.</span></span>  
  
```xml  
<protocolMapping>  
    <add scheme="http" binding="basicHttpBinding" bindingConfiguration="shortTimeout" />  
    <add scheme="https" binding="basicHttpBinding" bindingConfiguration="Secure" />  
</protocolMapping>  
<bindings>  
    <basicHttpBinding   
        name="shortTimeout"  
        timeout="00:00:00:01"   
     />  
     <basicHttpBinding   
        name="Secure" />  
        <Security mode="Transport" />  
</bindings>  
```  
  
## <a name="see-also"></a><span data-ttu-id="76092-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76092-157">See also</span></span>

- [<span data-ttu-id="76092-158">Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="76092-158">Simplified Configuration</span></span>](../../../docs/framework/wcf/simplified-configuration.md)
- [<span data-ttu-id="76092-159">Sistem Tarafından Sağlanan Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="76092-159">System-Provided Bindings</span></span>](../../../docs/framework/wcf/system-provided-bindings.md)
- [<span data-ttu-id="76092-160">Uç Nokta Oluşturmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="76092-160">Endpoint Creation Overview</span></span>](../../../docs/framework/wcf/endpoint-creation-overview.md)
- [<span data-ttu-id="76092-161">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="76092-161">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
