---
title: Windows Communication Foundation Hizmetleri için Bağlamaları Yapılandırma
description: Sistem altındaki öğeleri düzenleyerek bir WCF uygulaması için dağıtım zamanında bağlamaları yapılandırma hakkında bilgi edinin. ServiceModel öğesi.
ms.date: 03/30/2017
helpviewer_keywords:
- binding configuration [WCF]
ms.assetid: 99a85fd8-f7eb-4a84-a93e-7721b37d415c
ms.openlocfilehash: a2bb396e65722726e54cd315e931eea933386659
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247634"
---
# <a name="configuring-bindings-for-windows-communication-foundation-services"></a><span data-ttu-id="3f991-103">Windows Communication Foundation Hizmetleri için Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3f991-103">Configuring Bindings for Windows Communication Foundation Services</span></span>
<span data-ttu-id="3f991-104">Uygulama oluştururken genellikle, uygulamanın dağıtımıyla sonra kararları yöneticiye erteleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f991-104">When creating an application, you often want to defer decisions to the administrator after the deployment of the application.</span></span> <span data-ttu-id="3f991-105">Örneğin, bir hizmet adresinin veya Tekdüzen kaynak tanımlayıcısının (URI) ne kadar ilerlediğinin bilmesinin bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="3f991-105">For example, there is often no way of knowing in advance what a service address, or Uniform Resource Identifier (URI), will be.</span></span> <span data-ttu-id="3f991-106">Bir adresi sabit kodlamak yerine, bir hizmet oluşturduktan sonra yöneticinin bunu yapmasına izin vermek tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="3f991-106">Instead of hard-coding an address, it is preferable to allow an administrator to do so after creating a service.</span></span> <span data-ttu-id="3f991-107">Bu esneklik yapılandırma aracılığıyla gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3f991-107">This flexibility is accomplished through configuration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3f991-108">Yapılandırma dosyalarını hızlı bir şekilde oluşturmak için [ServiceModel meta veri yardımcı programı aracını (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) anahtarla birlikte kullanın `/config` .</span><span class="sxs-lookup"><span data-stu-id="3f991-108">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) with the `/config` switch to quickly create configuration files.</span></span>  
  
## <a name="major-sections"></a><span data-ttu-id="3f991-109">Ana bölümler</span><span class="sxs-lookup"><span data-stu-id="3f991-109">Major Sections</span></span>  
 <span data-ttu-id="3f991-110">Windows Communication Foundation (WCF) yapılandırma şeması, aşağıdaki üç ana bölümü içerir ( `serviceModel` , `bindings` ve `services` ):</span><span class="sxs-lookup"><span data-stu-id="3f991-110">The Windows Communication Foundation (WCF) configuration scheme includes the following three major sections (`serviceModel`, `bindings`, and `services`):</span></span>  
  
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
  
### <a name="servicemodel-elements"></a><span data-ttu-id="3f991-111">ServiceModel öğeleri</span><span class="sxs-lookup"><span data-stu-id="3f991-111">ServiceModel Elements</span></span>  
 <span data-ttu-id="3f991-112">Bir hizmet `system.ServiceModel` türünü bir veya daha fazla uç nokta ile ve bir hizmetin ayarlarını yapılandırmak için, öğesiyle sınırlanan bölümü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f991-112">You can use the section bounded by the `system.ServiceModel` element to configure a service type with one or more endpoints, as well as settings for a service.</span></span> <span data-ttu-id="3f991-113">Her uç nokta daha sonra bir adresle, sözleşmeyle ve bağlamasıyla yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="3f991-113">Each endpoint can then be configured with an address, a contract, and a binding.</span></span> <span data-ttu-id="3f991-114">Uç noktalar hakkında daha fazla bilgi için bkz. [Endpoint oluşturmaya genel bakış](endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3f991-114">For more information about endpoints, see [Endpoint Creation Overview](endpoint-creation-overview.md).</span></span> <span data-ttu-id="3f991-115">Hiçbir uç nokta belirtilmemişse, çalışma zamanı varsayılan uç noktaları ekler.</span><span class="sxs-lookup"><span data-stu-id="3f991-115">If no endpoints are specified, the runtime adds default endpoints.</span></span> <span data-ttu-id="3f991-116">Varsayılan uç noktalar, bağlamalar ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](./samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="3f991-116">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
 <span data-ttu-id="3f991-117">Bir bağlama, aktarımları (HTTP, TCP, kanallar, Message Queuing) ve protokolleri (güvenlik, güvenilirlik, Işlem akışları) belirtir ve her biri bir uç noktanın dünya ile nasıl iletişim kuracağını belirten bağlama öğelerinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="3f991-117">A binding specifies transports (HTTP, TCP, pipes, Message Queuing) and protocols (Security, Reliability, Transaction flows) and consists of binding elements, each of which specifies an aspect of how an endpoint communicates with the world.</span></span>  
  
 <span data-ttu-id="3f991-118">Örneğin, öğesinin belirtilmesi, [\<basicHttpBinding>](../configure-apps/file-schema/wcf/basichttpbinding.md) bir uç nokta için taşıma olarak http kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="3f991-118">For example, specifying the [\<basicHttpBinding>](../configure-apps/file-schema/wcf/basichttpbinding.md) element indicates to use HTTP as the transport for an endpoint.</span></span> <span data-ttu-id="3f991-119">Bu uç noktayı kullanan hizmet açıldığında bitiş noktasını çalışma zamanında bağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3f991-119">This is used to wire up the endpoint at run time when the service using this endpoint is opened.</span></span>  
  
 <span data-ttu-id="3f991-120">İki tür bağlama vardır: önceden tanımlanmış ve özel.</span><span class="sxs-lookup"><span data-stu-id="3f991-120">There are two kinds of bindings: predefined and custom.</span></span> <span data-ttu-id="3f991-121">Önceden tanımlanmış bağlamalar, yaygın senaryolarda kullanılan öğelerin yararlı birleşimlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="3f991-121">Predefined bindings contain useful combinations of elements that are used in common scenarios.</span></span> <span data-ttu-id="3f991-122">WCF 'nin sağladığı önceden tanımlanmış bağlama türlerinin bir listesi için bkz. [sistem tarafından sağlanan bağlamalar](system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="3f991-122">For a list of predefined binding types that WCF provides, see [System-Provided Bindings](system-provided-bindings.md).</span></span> <span data-ttu-id="3f991-123">Önceden tanımlanmış bağlama koleksiyonu, bir hizmet uygulamasının ihtiyacı olan özelliklerin doğru birleşimine sahip değilse, uygulamanın gereksinimlerini karşılamak için özel bağlamalar oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f991-123">If no predefined binding collection has the correct combination of features that a service application needs, you can construct custom bindings to meet the application's requirements.</span></span> <span data-ttu-id="3f991-124">Özel Bağlamalar hakkında daha fazla bilgi için bkz [\<customBinding>](../configure-apps/file-schema/wcf/custombinding.md) ..</span><span class="sxs-lookup"><span data-stu-id="3f991-124">For more information about custom bindings, see [\<customBinding>](../configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
 <span data-ttu-id="3f991-125">Aşağıdaki dört örnekte, bir WCF hizmeti ayarlamak için kullanılan en yaygın bağlama yapılandırmalarının gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3f991-125">The following four examples illustrate the most common binding configurations used for setting up a WCF service.</span></span>  
  
#### <a name="specifying-an-endpoint-to-use-a-binding-type"></a><span data-ttu-id="3f991-126">Bağlama türünü kullanmak için bir uç nokta belirtme</span><span class="sxs-lookup"><span data-stu-id="3f991-126">Specifying an Endpoint to Use a Binding Type</span></span>  
 <span data-ttu-id="3f991-127">İlk örnek, bir adres, sözleşme ve bağlama ile yapılandırılan bir uç noktanın nasıl belirtildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3f991-127">The first example illustrates how to specify an endpoint configured with an address, a contract, and a binding.</span></span>  
  
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
  
 <span data-ttu-id="3f991-128">Bu örnekte `name` öznitelik, yapılandırmanın hangi hizmet türüyle ilgili olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3f991-128">In this example, the `name` attribute indicates which service type the configuration is for.</span></span> <span data-ttu-id="3f991-129">Sözleşmeniz ile kodunuzda bir hizmet oluşturduğunuzda `HelloWorld` , örnek yapılandırmasında tanımlanan tüm uç noktalar ile başlatılır.</span><span class="sxs-lookup"><span data-stu-id="3f991-129">When you create a service in your code with the `HelloWorld` contract, it is initialized with all of the endpoints defined in the example configuration.</span></span> <span data-ttu-id="3f991-130">Derleme yalnızca bir hizmet sözleşmesi uygularsa, `name` hizmet kullanılabilir tek türü kullandığından öznitelik atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="3f991-130">If the assembly implements only one service contract, the `name` attribute can be omitted because the service uses the only available type.</span></span> <span data-ttu-id="3f991-131">Öznitelik, biçiminde olması gereken bir dize alır`Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`</span><span class="sxs-lookup"><span data-stu-id="3f991-131">The attribute takes a string, which must be in the format `Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`</span></span>  
  
 <span data-ttu-id="3f991-132">`address`Özniteliği diğer uç noktaların hizmetle iletişim kurmak için KULLANDıĞı URI 'yi belirtir.</span><span class="sxs-lookup"><span data-stu-id="3f991-132">The `address` attribute specifies the URI that other endpoints use to communicate to the service.</span></span> <span data-ttu-id="3f991-133">URI mutlak ya da göreli yol olabilir.</span><span class="sxs-lookup"><span data-stu-id="3f991-133">The URI can be either an absolute or relative path.</span></span> <span data-ttu-id="3f991-134">Göreli bir adres sağlanmışsa, konağın bağlamada kullanılan aktarım düzeni için uygun bir temel adres sağlaması beklenir.</span><span class="sxs-lookup"><span data-stu-id="3f991-134">If a relative address is provided, the host is expected to provide a base address that is appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="3f991-135">Bir adres yapılandırılmamışsa, taban adresin bu uç noktanın adresi olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="3f991-135">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span>  
  
 <span data-ttu-id="3f991-136">`contract`Öznitelik, bu uç noktanın sunduğu sözleşmeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="3f991-136">The `contract` attribute specifies the contract this endpoint is exposing.</span></span> <span data-ttu-id="3f991-137">Hizmet uygulaması türü, anlaşma türünü uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="3f991-137">The service implementation type must implement the contract type.</span></span> <span data-ttu-id="3f991-138">Bir hizmet uygulamasının tek bir anlaşma türü uygularsa, bu özellik atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="3f991-138">If a service implementation implements a single contract type, then this property can be omitted.</span></span>  
  
 <span data-ttu-id="3f991-139">`binding`Öznitelik, bu belirli uç nokta için kullanılmak üzere önceden tanımlanmış veya özel bir bağlama seçer.</span><span class="sxs-lookup"><span data-stu-id="3f991-139">The `binding` attribute selects a predefined or custom binding to use for this specific endpoint.</span></span> <span data-ttu-id="3f991-140">Açıkça bir bağlama olmayan bir uç nokta, varsayılan bağlama seçimini kullanır `BasicHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="3f991-140">An endpoint that does not explicitly select a binding uses the default binding selection, which is `BasicHttpBinding`.</span></span>  
  
#### <a name="modifying-a-predefined-binding"></a><span data-ttu-id="3f991-141">Önceden tanımlanmış bağlamayı değiştirme</span><span class="sxs-lookup"><span data-stu-id="3f991-141">Modifying a Predefined Binding</span></span>  
 <span data-ttu-id="3f991-142">Aşağıdaki örnekte, önceden tanımlanmış bir bağlama değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3f991-142">In the following example, a predefined binding is modified.</span></span> <span data-ttu-id="3f991-143">Daha sonra, hizmette herhangi bir uç noktayı yapılandırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3f991-143">It can then be used to configure any endpoint in the service.</span></span> <span data-ttu-id="3f991-144">Bağlama <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> değeri 1 saniye olarak ayarlanarak değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="3f991-144">The binding is modified by setting the <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> value to 1 second.</span></span> <span data-ttu-id="3f991-145">Özelliğin bir nesne döndürdüğünü unutmayın <xref:System.TimeSpan> .</span><span class="sxs-lookup"><span data-stu-id="3f991-145">Note that the property returns a <xref:System.TimeSpan> object.</span></span>  
  
 <span data-ttu-id="3f991-146">Değiştirilen bağlama bağlamalar bölümünde bulunur.</span><span class="sxs-lookup"><span data-stu-id="3f991-146">That altered binding is found in the bindings section.</span></span> <span data-ttu-id="3f991-147">Bu değiştirilmiş bağlama artık öğedeki özniteliği ayarlanarak herhangi bir uç nokta oluşturulurken kullanılabilir `binding` `endpoint` .</span><span class="sxs-lookup"><span data-stu-id="3f991-147">This altered binding can now be used when creating any endpoint by setting the `binding` attribute in the `endpoint` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3f991-148">Bağlama için belirli bir ad verirseniz, `bindingConfiguration` hizmet uç noktasında belirtilen ' ın onunla eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f991-148">If you give a particular name to the binding, the `bindingConfiguration` specified in the service endpoint must match with it.</span></span>  
  
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
  
## <a name="configuring-a-behavior-to-apply-to-a-service"></a><span data-ttu-id="3f991-149">Bir hizmete uygulanacak davranışı yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3f991-149">Configuring a Behavior to Apply to a Service</span></span>  
 <span data-ttu-id="3f991-150">Aşağıdaki örnekte, hizmet türü için belirli bir davranış yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="3f991-150">In the following example, a specific behavior is configured for the service type.</span></span> <span data-ttu-id="3f991-151">`ServiceMetadataBehavior`Öğesi, [ServiceModel meta veri yardımcı programı aracının (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) hizmeti sorgulamak ve meta verilerden Web Hizmetleri Açıklama Dili (wsdl) belgeleri oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3f991-151">The `ServiceMetadataBehavior` element is used to enable the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to query the service and generate Web Services Description Language (WSDL) documents from the metadata.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3f991-152">Davranışa belirli bir ad verirseniz, `behaviorConfiguration` hizmet veya uç nokta bölümünde belirtilen bir ad ile aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3f991-152">If you give a particular name to the behavior, the `behaviorConfiguration` specified in the service or endpoint section must match it.</span></span>  
  
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
  
 <span data-ttu-id="3f991-153">Önceki yapılandırma, bir istemcinin "HelloWorld" türü belirlenmiş hizmetin meta verilerini aramasını ve almasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="3f991-153">The preceding configuration enables a client to call and get the metadata of the "HelloWorld" typed service.</span></span>  
  
 `svcutil /config:Client.exe.config http://computer:8080/Hello?wsdl`  
  
## <a name="specifying-a-service-with-two-endpoints-using-different-binding-values"></a><span data-ttu-id="3f991-154">Farklı bağlama değerleri kullanarak Iki uç nokta içeren bir hizmet belirtme</span><span class="sxs-lookup"><span data-stu-id="3f991-154">Specifying a Service with Two Endpoints Using Different Binding Values</span></span>  
 <span data-ttu-id="3f991-155">Bu son örnekte, hizmet türü için iki uç nokta yapılandırılır `HelloWorld` .</span><span class="sxs-lookup"><span data-stu-id="3f991-155">In this last example, two endpoints are configured for the `HelloWorld` service type.</span></span> <span data-ttu-id="3f991-156">Her uç nokta `bindingConfiguration` aynı bağlama türünün farklı bir özelleştirilmiş özniteliğini kullanır (her biri ' nı değiştirir `basicHttpBinding` ).</span><span class="sxs-lookup"><span data-stu-id="3f991-156">Each endpoint uses a different customized  `bindingConfiguration` attribute of the same binding type (each modifies the `basicHttpBinding`).</span></span>  
  
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
  
 <span data-ttu-id="3f991-157">`protocolMapping`Aşağıdaki örnekte gösterildiği gibi bir bölüm ekleyerek ve bağlamaları yapılandırarak varsayılan yapılandırmayı kullanarak aynı davranışı sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f991-157">You can get the same behavior using the default configuration by adding a `protocolMapping` section and configuring the bindings as demonstrated in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3f991-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f991-158">See also</span></span>

- [<span data-ttu-id="3f991-159">Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3f991-159">Simplified Configuration</span></span>](simplified-configuration.md)
- [<span data-ttu-id="3f991-160">Sistem tarafından sağlanmış bağlamalar</span><span class="sxs-lookup"><span data-stu-id="3f991-160">System-Provided Bindings</span></span>](system-provided-bindings.md)
- [<span data-ttu-id="3f991-161">Uç Noktası Oluşturma Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3f991-161">Endpoint Creation Overview</span></span>](endpoint-creation-overview.md)
- [<span data-ttu-id="3f991-162">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="3f991-162">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
