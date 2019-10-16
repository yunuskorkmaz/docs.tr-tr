---
title: Windows Communication Foundation Hizmetleri için Bağlamaları Yapılandırma
ms.date: 03/30/2017
helpviewer_keywords:
- binding configuration [WCF]
ms.assetid: 99a85fd8-f7eb-4a84-a93e-7721b37d415c
ms.openlocfilehash: 92f9457dd0c118c9a7c578a7088f66cdea1e5ad0
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320663"
---
# <a name="configuring-bindings-for-windows-communication-foundation-services"></a><span data-ttu-id="fe4f0-102">Windows Communication Foundation Hizmetleri için Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="fe4f0-102">Configuring Bindings for Windows Communication Foundation Services</span></span>
<span data-ttu-id="fe4f0-103">Uygulama oluştururken genellikle, uygulamanın dağıtımıyla sonra kararları yöneticiye erteleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-103">When creating an application, you often want to defer decisions to the administrator after the deployment of the application.</span></span> <span data-ttu-id="fe4f0-104">Örneğin, bir hizmet adresinin veya Tekdüzen kaynak tanımlayıcısının (URI) ne kadar ilerlediğinin bilmesinin bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-104">For example, there is often no way of knowing in advance what a service address, or Uniform Resource Identifier (URI), will be.</span></span> <span data-ttu-id="fe4f0-105">Bir adresi sabit kodlamak yerine, bir hizmet oluşturduktan sonra yöneticinin bunu yapmasına izin vermek tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-105">Instead of hard-coding an address, it is preferable to allow an administrator to do so after creating a service.</span></span> <span data-ttu-id="fe4f0-106">Bu esneklik yapılandırma aracılığıyla gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-106">This flexibility is accomplished through configuration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fe4f0-107">Yapılandırma dosyalarını hızlıca oluşturmak için, `/config` anahtarıyla [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-107">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) with the `/config` switch to quickly create configuration files.</span></span>  
  
## <a name="major-sections"></a><span data-ttu-id="fe4f0-108">Ana bölümler</span><span class="sxs-lookup"><span data-stu-id="fe4f0-108">Major Sections</span></span>  
 <span data-ttu-id="fe4f0-109">Windows Communication Foundation (WCF) yapılandırma şeması, aşağıdaki üç ana bölümü içerir (`serviceModel`, `bindings` ve `services`):</span><span class="sxs-lookup"><span data-stu-id="fe4f0-109">The Windows Communication Foundation (WCF) configuration scheme includes the following three major sections (`serviceModel`, `bindings`, and `services`):</span></span>  
  
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
  
### <a name="servicemodel-elements"></a><span data-ttu-id="fe4f0-110">ServiceModel öğeleri</span><span class="sxs-lookup"><span data-stu-id="fe4f0-110">ServiceModel Elements</span></span>  
 <span data-ttu-id="fe4f0-111">Bir hizmet türünü bir veya daha fazla uç nokta ile ve bir hizmetin ayarlarını yapılandırmak için `system.ServiceModel` öğesiyle sınırlanan bölümü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-111">You can use the section bounded by the `system.ServiceModel` element to configure a service type with one or more endpoints, as well as settings for a service.</span></span> <span data-ttu-id="fe4f0-112">Her uç nokta daha sonra bir adresle, sözleşmeyle ve bağlamasıyla yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-112">Each endpoint can then be configured with an address, a contract, and a binding.</span></span> <span data-ttu-id="fe4f0-113">Uç noktalar hakkında daha fazla bilgi için bkz. [Endpoint oluşturmaya genel bakış](endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="fe4f0-113">For more information about endpoints, see [Endpoint Creation Overview](endpoint-creation-overview.md).</span></span> <span data-ttu-id="fe4f0-114">Hiçbir uç nokta belirtilmemişse, çalışma zamanı varsayılan uç noktaları ekler.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-114">If no endpoints are specified, the runtime adds default endpoints.</span></span> <span data-ttu-id="fe4f0-115">Varsayılan uç noktalar, bağlamalar ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](./samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-115">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
 <span data-ttu-id="fe4f0-116">Bir bağlama, aktarımları (HTTP, TCP, kanallar, Message Queuing) ve protokolleri (güvenlik, güvenilirlik, Işlem akışları) belirtir ve her biri bir uç noktanın dünya ile nasıl iletişim kuracağını belirten bağlama öğelerinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-116">A binding specifies transports (HTTP, TCP, pipes, Message Queuing) and protocols (Security, Reliability, Transaction flows) and consists of binding elements, each of which specifies an aspect of how an endpoint communicates with the world.</span></span>  
  
 <span data-ttu-id="fe4f0-117">Örneğin, [\<basicHttpBinding >](../configure-apps/file-schema/wcf/basichttpbinding.md) öğesinin belirtilmesi, bir uç nokta için aktarım olarak http kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-117">For example, specifying the [\<basicHttpBinding>](../configure-apps/file-schema/wcf/basichttpbinding.md) element indicates to use HTTP as the transport for an endpoint.</span></span> <span data-ttu-id="fe4f0-118">Bu uç noktayı kullanan hizmet açıldığında bitiş noktasını çalışma zamanında bağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-118">This is used to wire up the endpoint at run time when the service using this endpoint is opened.</span></span>  
  
 <span data-ttu-id="fe4f0-119">İki tür bağlama vardır: önceden tanımlanmış ve özel.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-119">There are two kinds of bindings: predefined and custom.</span></span> <span data-ttu-id="fe4f0-120">Önceden tanımlanmış bağlamalar, yaygın senaryolarda kullanılan öğelerin yararlı birleşimlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-120">Predefined bindings contain useful combinations of elements that are used in common scenarios.</span></span> <span data-ttu-id="fe4f0-121">WCF 'nin sağladığı önceden tanımlanmış bağlama türlerinin bir listesi için bkz. [sistem tarafından sağlanan bağlamalar](system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="fe4f0-121">For a list of predefined binding types that WCF provides, see [System-Provided Bindings](system-provided-bindings.md).</span></span> <span data-ttu-id="fe4f0-122">Önceden tanımlanmış bağlama koleksiyonu, bir hizmet uygulamasının ihtiyacı olan özelliklerin doğru birleşimine sahip değilse, uygulamanın gereksinimlerini karşılamak için özel bağlamalar oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-122">If no predefined binding collection has the correct combination of features that a service application needs, you can construct custom bindings to meet the application's requirements.</span></span> <span data-ttu-id="fe4f0-123">Özel Bağlamalar hakkında daha fazla bilgi için bkz. [\<customBinding >](../configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="fe4f0-123">For more information about custom bindings, see [\<customBinding>](../configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
 <span data-ttu-id="fe4f0-124">Aşağıdaki dört örnekte, bir WCF hizmeti ayarlamak için kullanılan en yaygın bağlama yapılandırmalarının gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-124">The following four examples illustrate the most common binding configurations used for setting up a WCF service.</span></span>  
  
#### <a name="specifying-an-endpoint-to-use-a-binding-type"></a><span data-ttu-id="fe4f0-125">Bağlama türünü kullanmak için bir uç nokta belirtme</span><span class="sxs-lookup"><span data-stu-id="fe4f0-125">Specifying an Endpoint to Use a Binding Type</span></span>  
 <span data-ttu-id="fe4f0-126">İlk örnek, bir adres, sözleşme ve bağlama ile yapılandırılan bir uç noktanın nasıl belirtildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-126">The first example illustrates how to specify an endpoint configured with an address, a contract, and a binding.</span></span>  
  
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
  
 <span data-ttu-id="fe4f0-127">Bu örnekte, `name` özniteliği, yapılandırmanın hangi hizmet türüyle ilgili olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-127">In this example, the `name` attribute indicates which service type the configuration is for.</span></span> <span data-ttu-id="fe4f0-128">Kodunuzda `HelloWorld` sözleşmesine sahip bir hizmet oluşturduğunuzda, örnek yapılandırmasında tanımlanan tüm uç noktalar ile başlatılır.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-128">When you create a service in your code with the `HelloWorld` contract, it is initialized with all of the endpoints defined in the example configuration.</span></span> <span data-ttu-id="fe4f0-129">Derleme yalnızca bir hizmet sözleşmesi uygularsa, hizmet kullanılabilir tek türü kullandığından `name` özniteliği atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-129">If the assembly implements only one service contract, the `name` attribute can be omitted because the service uses the only available type.</span></span> <span data-ttu-id="fe4f0-130">Öznitelik, @no__t biçiminde olması gereken bir dize alır (0)</span><span class="sxs-lookup"><span data-stu-id="fe4f0-130">The attribute takes a string, which must be in the format `Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`</span></span>  
  
 <span data-ttu-id="fe4f0-131">@No__t-0 özniteliği diğer uç noktaların hizmetle iletişim kurmak için kullandığı URI 'yi belirtir.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-131">The `address` attribute specifies the URI that other endpoints use to communicate to the service.</span></span> <span data-ttu-id="fe4f0-132">URI mutlak ya da göreli yol olabilir.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-132">The URI can be either an absolute or relative path.</span></span> <span data-ttu-id="fe4f0-133">Göreli bir adres sağlanmışsa, konağın bağlamada kullanılan aktarım düzeni için uygun bir temel adres sağlaması beklenir.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-133">If a relative address is provided, the host is expected to provide a base address that is appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="fe4f0-134">Bir adres yapılandırılmamışsa, taban adresin bu uç noktanın adresi olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-134">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span>  
  
 <span data-ttu-id="fe4f0-135">@No__t-0 özniteliği bu uç noktanın sunduğu sözleşmeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-135">The `contract` attribute specifies the contract this endpoint is exposing.</span></span> <span data-ttu-id="fe4f0-136">Hizmet uygulaması türü, anlaşma türünü uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-136">The service implementation type must implement the contract type.</span></span> <span data-ttu-id="fe4f0-137">Bir hizmet uygulamasının tek bir anlaşma türü uygularsa, bu özellik atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-137">If a service implementation implements a single contract type, then this property can be omitted.</span></span>  
  
 <span data-ttu-id="fe4f0-138">@No__t-0 özniteliği, bu belirli uç nokta için kullanılmak üzere önceden tanımlanmış veya özel bir bağlama seçer.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-138">The `binding` attribute selects a predefined or custom binding to use for this specific endpoint.</span></span> <span data-ttu-id="fe4f0-139">Açıkça bir bağlama olmayan bir uç nokta, `BasicHttpBinding` olan varsayılan bağlama seçimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-139">An endpoint that does not explicitly select a binding uses the default binding selection, which is `BasicHttpBinding`.</span></span>  
  
#### <a name="modifying-a-predefined-binding"></a><span data-ttu-id="fe4f0-140">Önceden tanımlanmış bağlamayı değiştirme</span><span class="sxs-lookup"><span data-stu-id="fe4f0-140">Modifying a Predefined Binding</span></span>  
 <span data-ttu-id="fe4f0-141">Aşağıdaki örnekte, önceden tanımlanmış bir bağlama değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-141">In the following example, a predefined binding is modified.</span></span> <span data-ttu-id="fe4f0-142">Daha sonra, hizmette herhangi bir uç noktayı yapılandırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-142">It can then be used to configure any endpoint in the service.</span></span> <span data-ttu-id="fe4f0-143">Bağlama <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> değeri 1 saniyeye ayarlanarak değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-143">The binding is modified by setting the <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> value to 1 second.</span></span> <span data-ttu-id="fe4f0-144">Özelliğin <xref:System.TimeSpan> nesnesi döndürdüğünü unutmayın.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-144">Note that the property returns a <xref:System.TimeSpan> object.</span></span>  
  
 <span data-ttu-id="fe4f0-145">Değiştirilen bağlama bağlamalar bölümünde bulunur.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-145">That altered binding is found in the bindings section.</span></span> <span data-ttu-id="fe4f0-146">Bu değiştirilmiş bağlama artık `endpoint` öğesindeki `binding` özniteliğini ayarlayarak herhangi bir uç nokta oluştururken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-146">This altered binding can now be used when creating any endpoint by setting the `binding` attribute in the `endpoint` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fe4f0-147">Bağlamaya belirli bir ad verirseniz, hizmet uç noktasında belirtilen `bindingConfiguration` ile eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-147">If you give a particular name to the binding, the `bindingConfiguration` specified in the service endpoint must match with it.</span></span>  
  
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
  
## <a name="configuring-a-behavior-to-apply-to-a-service"></a><span data-ttu-id="fe4f0-148">Bir hizmete uygulanacak davranışı yapılandırma</span><span class="sxs-lookup"><span data-stu-id="fe4f0-148">Configuring a Behavior to Apply to a Service</span></span>  
 <span data-ttu-id="fe4f0-149">Aşağıdaki örnekte, hizmet türü için belirli bir davranış yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-149">In the following example, a specific behavior is configured for the service type.</span></span> <span data-ttu-id="fe4f0-150">@No__t-0 öğesi, [ServiceModel meta veri yardımcı programı aracının (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) hizmeti sorgulamasını ve meta verilerden Web Hizmetleri Açıklama DILI (wsdl) belgelerini oluşturmasını sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-150">The `ServiceMetadataBehavior` element is used to enable the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to query the service and generate Web Services Description Language (WSDL) documents from the metadata.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fe4f0-151">Davranışa belirli bir ad verirseniz, hizmet veya uç nokta bölümünde belirtilen `behaviorConfiguration` ile aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-151">If you give a particular name to the behavior, the `behaviorConfiguration` specified in the service or endpoint section must match it.</span></span>  
  
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
  
 <span data-ttu-id="fe4f0-152">Önceki yapılandırma, bir istemcinin "HelloWorld" türü belirlenmiş hizmetin meta verilerini aramasını ve almasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-152">The preceding configuration enables a client to call and get the metadata of the "HelloWorld" typed service.</span></span>  
  
 `svcutil /config:Client.exe.config http://computer:8080/Hello?wsdl`  
  
## <a name="specifying-a-service-with-two-endpoints-using-different-binding-values"></a><span data-ttu-id="fe4f0-153">Farklı bağlama değerleri kullanarak Iki uç nokta içeren bir hizmet belirtme</span><span class="sxs-lookup"><span data-stu-id="fe4f0-153">Specifying a Service with Two Endpoints Using Different Binding Values</span></span>  
 <span data-ttu-id="fe4f0-154">Bu son örnekte, `HelloWorld` hizmet türü için iki uç nokta yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-154">In this last example, two endpoints are configured for the `HelloWorld` service type.</span></span> <span data-ttu-id="fe4f0-155">Her uç nokta, aynı bağlama türünün farklı bir özelleştirilmiş `bindingConfiguration` özniteliğini kullanır (her biri `basicHttpBinding` ' i değiştirir).</span><span class="sxs-lookup"><span data-stu-id="fe4f0-155">Each endpoint uses a different customized  `bindingConfiguration` attribute of the same binding type (each modifies the `basicHttpBinding`).</span></span>  
  
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
  
 <span data-ttu-id="fe4f0-156">@No__t-0 bölümü ekleyerek ve bağlamaları aşağıdaki örnekte gösterildiği gibi yapılandırarak varsayılan yapılandırmayı kullanarak aynı davranışı alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-156">You can get the same behavior using the default configuration by adding a `protocolMapping` section and configuring the bindings as demonstrated in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fe4f0-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe4f0-157">See also</span></span>

- [<span data-ttu-id="fe4f0-158">Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="fe4f0-158">Simplified Configuration</span></span>](simplified-configuration.md)
- [<span data-ttu-id="fe4f0-159">Sistem Tarafından Sağlanan Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="fe4f0-159">System-Provided Bindings</span></span>](system-provided-bindings.md)
- [<span data-ttu-id="fe4f0-160">Uç Nokta Oluşturmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fe4f0-160">Endpoint Creation Overview</span></span>](endpoint-creation-overview.md)
- [<span data-ttu-id="fe4f0-161">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="fe4f0-161">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
