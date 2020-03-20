---
title: Windows Communication Foundation Hizmetleri için Bağlamaları Yapılandırma
ms.date: 03/30/2017
helpviewer_keywords:
- binding configuration [WCF]
ms.assetid: 99a85fd8-f7eb-4a84-a93e-7721b37d415c
ms.openlocfilehash: e7ee1a8ce358c77e46db39af67bd9dc20114fb3b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174829"
---
# <a name="configuring-bindings-for-windows-communication-foundation-services"></a><span data-ttu-id="b5999-102">Windows Communication Foundation Hizmetleri için Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b5999-102">Configuring Bindings for Windows Communication Foundation Services</span></span>
<span data-ttu-id="b5999-103">Bir uygulama oluştururken, genellikle uygulamanın dağıtımından sonra kararları yöneticiye ertelemek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="b5999-103">When creating an application, you often want to defer decisions to the administrator after the deployment of the application.</span></span> <span data-ttu-id="b5999-104">Örneğin, genellikle bir hizmet adresinin veya Tek düzen kaynak tanımlayıcısının (URI) ne olacağını önceden bilmenin bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="b5999-104">For example, there is often no way of knowing in advance what a service address, or Uniform Resource Identifier (URI), will be.</span></span> <span data-ttu-id="b5999-105">Bir adresi zor kodlamak yerine, bir hizmet oluşturduktan sonra yöneticinin bunu yapmasına izin vermek tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="b5999-105">Instead of hard-coding an address, it is preferable to allow an administrator to do so after creating a service.</span></span> <span data-ttu-id="b5999-106">Bu esneklik yapılandırma ile gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b5999-106">This flexibility is accomplished through configuration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b5999-107">Hızlı yapılandırma dosyaları oluşturmak için `/config` geçiş ile [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="b5999-107">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) with the `/config` switch to quickly create configuration files.</span></span>  
  
## <a name="major-sections"></a><span data-ttu-id="b5999-108">Ana Bölümler</span><span class="sxs-lookup"><span data-stu-id="b5999-108">Major Sections</span></span>  
 <span data-ttu-id="b5999-109">Windows Communication Foundation (WCF) yapılandırma şeması aşağıdaki`serviceModel`üç `bindings`ana `services`bölümü içerir ( , , ve):</span><span class="sxs-lookup"><span data-stu-id="b5999-109">The Windows Communication Foundation (WCF) configuration scheme includes the following three major sections (`serviceModel`, `bindings`, and `services`):</span></span>  
  
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
  
### <a name="servicemodel-elements"></a><span data-ttu-id="b5999-110">ServiceModel Elemanları</span><span class="sxs-lookup"><span data-stu-id="b5999-110">ServiceModel Elements</span></span>  
 <span data-ttu-id="b5999-111">Bir hizmet türünü bir veya `system.ServiceModel` daha fazla uç noktayla ve bir hizmet ayarlarını yapılandırmak için öğeyle sınırlanan bölümü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5999-111">You can use the section bounded by the `system.ServiceModel` element to configure a service type with one or more endpoints, as well as settings for a service.</span></span> <span data-ttu-id="b5999-112">Her bitiş noktası daha sonra bir adres, bir sözleşme ve bir bağlama ile yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="b5999-112">Each endpoint can then be configured with an address, a contract, and a binding.</span></span> <span data-ttu-id="b5999-113">Uç noktalar hakkında daha fazla bilgi için Bkz. [Endpoint Oluşturma Genel Bakışı.](endpoint-creation-overview.md)</span><span class="sxs-lookup"><span data-stu-id="b5999-113">For more information about endpoints, see [Endpoint Creation Overview](endpoint-creation-overview.md).</span></span> <span data-ttu-id="b5999-114">Uç nokta belirtilmemişse, çalışma süresi varsayılan uç noktaları ekler.</span><span class="sxs-lookup"><span data-stu-id="b5999-114">If no endpoints are specified, the runtime adds default endpoints.</span></span> <span data-ttu-id="b5999-115">Varsayılan uç noktalar, bağlamalar ve davranışlar hakkında daha fazla bilgi için wcf hizmetleri için [Basitleştirilmiş Yapılandırma](simplified-configuration.md) ve [Basitleştirilmiş Yapılandırma'ya](./samples/simplified-configuration-for-wcf-services.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="b5999-115">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
 <span data-ttu-id="b5999-116">Bağlayıcı, aktarımları (HTTP, TCP, pipes, Message Queuing) ve protokolleri (Güvenlik, Güvenilirlik, İşlem akışları) belirtir ve her biri bir uç noktanın dünyayla nasıl iletişim kurduğunu gösteren bağlayıcı öğelerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="b5999-116">A binding specifies transports (HTTP, TCP, pipes, Message Queuing) and protocols (Security, Reliability, Transaction flows) and consists of binding elements, each of which specifies an aspect of how an endpoint communicates with the world.</span></span>  
  
 <span data-ttu-id="b5999-117">Örneğin, [ \<temel HttpBinding>](../configure-apps/file-schema/wcf/basichttpbinding.md) öğesini belirterek, bir bitiş noktası için aktarım olarak HTTP'nin kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b5999-117">For example, specifying the [\<basicHttpBinding>](../configure-apps/file-schema/wcf/basichttpbinding.md) element indicates to use HTTP as the transport for an endpoint.</span></span> <span data-ttu-id="b5999-118">Bu, bu bitiş noktasını kullanan hizmet in çalışma zamanında bitiş noktasını kablolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b5999-118">This is used to wire up the endpoint at run time when the service using this endpoint is opened.</span></span>  
  
 <span data-ttu-id="b5999-119">İki tür bağlama vardır: önceden tanımlanmış ve özel.</span><span class="sxs-lookup"><span data-stu-id="b5999-119">There are two kinds of bindings: predefined and custom.</span></span> <span data-ttu-id="b5999-120">Önceden tanımlanmış bağlamalar, ortak senaryolarda kullanılan öğelerin yararlı birleşimlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="b5999-120">Predefined bindings contain useful combinations of elements that are used in common scenarios.</span></span> <span data-ttu-id="b5999-121">WCF'nin sağladığı önceden tanımlanmış bağlama türlerinin listesi için [bkz.](system-provided-bindings.md)</span><span class="sxs-lookup"><span data-stu-id="b5999-121">For a list of predefined binding types that WCF provides, see [System-Provided Bindings](system-provided-bindings.md).</span></span> <span data-ttu-id="b5999-122">Önceden tanımlanmış bağlama koleksiyonu, bir hizmet uygulamasının gereksinim duyduğu özelliklerin doğru birleşimine sahip değilse, uygulamagereksinimlerini karşılamak için özel bağlamalar oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5999-122">If no predefined binding collection has the correct combination of features that a service application needs, you can construct custom bindings to meet the application's requirements.</span></span> <span data-ttu-id="b5999-123">Özel bağlamalar hakkında daha fazla bilgi için [ \<>bkz. ](../configure-apps/file-schema/wcf/custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="b5999-123">For more information about custom bindings, see [\<customBinding>](../configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
 <span data-ttu-id="b5999-124">Aşağıdaki dört örnek, bir WCF hizmeti ayarlamak için kullanılan en yaygın bağlama yapılandırmalarını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="b5999-124">The following four examples illustrate the most common binding configurations used for setting up a WCF service.</span></span>  
  
#### <a name="specifying-an-endpoint-to-use-a-binding-type"></a><span data-ttu-id="b5999-125">Bağlama Türü Kullanmak için Bir Bitiş Noktası Belirtme</span><span class="sxs-lookup"><span data-stu-id="b5999-125">Specifying an Endpoint to Use a Binding Type</span></span>  
 <span data-ttu-id="b5999-126">İlk örnek, adres, sözleşme ve bağlama yla yapılandırılan bir bitiş noktasının nasıl belirtilen şekilde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="b5999-126">The first example illustrates how to specify an endpoint configured with an address, a contract, and a binding.</span></span>  
  
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
  
 <span data-ttu-id="b5999-127">Bu örnekte, `name` öznitelik yapılandırmaiçin hangi hizmet türü için olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b5999-127">In this example, the `name` attribute indicates which service type the configuration is for.</span></span> <span data-ttu-id="b5999-128">Sözleşmeyle birlikte `HelloWorld` kodunuzda bir hizmet oluşturduğunuzda, örnek yapılandırmada tanımlanan tüm uç noktalarıyla baş harfe fişlenir.</span><span class="sxs-lookup"><span data-stu-id="b5999-128">When you create a service in your code with the `HelloWorld` contract, it is initialized with all of the endpoints defined in the example configuration.</span></span> <span data-ttu-id="b5999-129">Derleme yalnızca bir hizmet sözleşmesi uygularsa, `name` hizmet kullanılabilir tek türü kullandığından öznitelik atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="b5999-129">If the assembly implements only one service contract, the `name` attribute can be omitted because the service uses the only available type.</span></span> <span data-ttu-id="b5999-130">Öznitelik biçiminde olması gereken bir dize alır`Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`</span><span class="sxs-lookup"><span data-stu-id="b5999-130">The attribute takes a string, which must be in the format `Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`</span></span>  
  
 <span data-ttu-id="b5999-131">Öznitelik, `address` uri'yi diğer uç noktaların hizmetle iletişim kurmak için kullandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b5999-131">The `address` attribute specifies the URI that other endpoints use to communicate to the service.</span></span> <span data-ttu-id="b5999-132">URI mutlak veya göreceli bir yol olabilir.</span><span class="sxs-lookup"><span data-stu-id="b5999-132">The URI can be either an absolute or relative path.</span></span> <span data-ttu-id="b5999-133">Göreceli bir adres sağlanırsa, ana bilgisayara bağlamada kullanılan aktarım şemasına uygun bir temel adres sağlaması beklenir.</span><span class="sxs-lookup"><span data-stu-id="b5999-133">If a relative address is provided, the host is expected to provide a base address that is appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="b5999-134">Bir adres yapılandırılmamışsa, temel adresin bu bitiş noktasının adresi olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="b5999-134">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span>  
  
 <span data-ttu-id="b5999-135">Öznitelik, `contract` bu bitiş noktasının ortaya çıkardığı sözleşmeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="b5999-135">The `contract` attribute specifies the contract this endpoint is exposing.</span></span> <span data-ttu-id="b5999-136">Hizmet uygulama türü sözleşme türünü uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="b5999-136">The service implementation type must implement the contract type.</span></span> <span data-ttu-id="b5999-137">Bir hizmet uygulaması tek bir sözleşme türü uygularsa, bu özellik atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="b5999-137">If a service implementation implements a single contract type, then this property can be omitted.</span></span>  
  
 <span data-ttu-id="b5999-138">Öznitelik, `binding` bu belirli bitiş noktası için kullanmak üzere önceden tanımlanmış veya özel bir bağlama seçer.</span><span class="sxs-lookup"><span data-stu-id="b5999-138">The `binding` attribute selects a predefined or custom binding to use for this specific endpoint.</span></span> <span data-ttu-id="b5999-139">Bağlayıcıyı açıkça seçmeyen bir bitiş noktası varsayılan bağlama seçimini `BasicHttpBinding`kullanır, yani.</span><span class="sxs-lookup"><span data-stu-id="b5999-139">An endpoint that does not explicitly select a binding uses the default binding selection, which is `BasicHttpBinding`.</span></span>  
  
#### <a name="modifying-a-predefined-binding"></a><span data-ttu-id="b5999-140">Önceden Tanımlanmış Bir Bağlamayı Değiştirme</span><span class="sxs-lookup"><span data-stu-id="b5999-140">Modifying a Predefined Binding</span></span>  
 <span data-ttu-id="b5999-141">Aşağıdaki örnekte, önceden tanımlanmış bir bağlama değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="b5999-141">In the following example, a predefined binding is modified.</span></span> <span data-ttu-id="b5999-142">Daha sonra hizmetteki herhangi bir bitiş noktasını yapılandırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b5999-142">It can then be used to configure any endpoint in the service.</span></span> <span data-ttu-id="b5999-143">Bağlama <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> değeri 1 saniyeye ayarlayarak değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="b5999-143">The binding is modified by setting the <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> value to 1 second.</span></span> <span data-ttu-id="b5999-144">Özelliğin bir <xref:System.TimeSpan> nesneyi döndürtettiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b5999-144">Note that the property returns a <xref:System.TimeSpan> object.</span></span>  
  
 <span data-ttu-id="b5999-145">Bu değiştirilmiş bağlama bağlama bölümünde bulunur.</span><span class="sxs-lookup"><span data-stu-id="b5999-145">That altered binding is found in the bindings section.</span></span> <span data-ttu-id="b5999-146">Bu değiştirilmiş bağlama artık `binding` `endpoint` öğedeki özniteliği ayarlayarak herhangi bir uç nokta oluştururken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b5999-146">This altered binding can now be used when creating any endpoint by setting the `binding` attribute in the `endpoint` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b5999-147">Bağlamaya belirli bir ad verirseniz, hizmet bitiş noktasında `bindingConfiguration` belirtilen adonunla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="b5999-147">If you give a particular name to the binding, the `bindingConfiguration` specified in the service endpoint must match with it.</span></span>  
  
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
  
## <a name="configuring-a-behavior-to-apply-to-a-service"></a><span data-ttu-id="b5999-148">Bir Hizmete Uygulanacak Davranışı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b5999-148">Configuring a Behavior to Apply to a Service</span></span>  
 <span data-ttu-id="b5999-149">Aşağıdaki örnekte, hizmet türü için belirli bir davranış yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="b5999-149">In the following example, a specific behavior is configured for the service type.</span></span> <span data-ttu-id="b5999-150">Öğe, `ServiceMetadataBehavior` [ServiceModel Metadata Utility Tool'un (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) hizmeti sorgulamasını ve meta verilerden Web Hizmetleri Açıklama Dili (WSDL) belgelerini oluşturmasını sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b5999-150">The `ServiceMetadataBehavior` element is used to enable the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to query the service and generate Web Services Description Language (WSDL) documents from the metadata.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b5999-151">Davranışa belirli bir ad verirseniz, hizmet veya bitiş noktası bölümünde `behaviorConfiguration` belirtilen adla eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="b5999-151">If you give a particular name to the behavior, the `behaviorConfiguration` specified in the service or endpoint section must match it.</span></span>  
  
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
  
 <span data-ttu-id="b5999-152">Önceki yapılandırma, istemcinin "HelloWorld" türünde yazılan hizmetin meta verilerini aramasını ve almalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="b5999-152">The preceding configuration enables a client to call and get the metadata of the "HelloWorld" typed service.</span></span>  
  
 `svcutil /config:Client.exe.config http://computer:8080/Hello?wsdl`  
  
## <a name="specifying-a-service-with-two-endpoints-using-different-binding-values"></a><span data-ttu-id="b5999-153">Farklı Bağlama Değerleri Kullanarak İki Uç Noktası Olan Bir Hizmet Belirtme</span><span class="sxs-lookup"><span data-stu-id="b5999-153">Specifying a Service with Two Endpoints Using Different Binding Values</span></span>  
 <span data-ttu-id="b5999-154">Bu son örnekte, `HelloWorld` hizmet türü için iki uç nokta yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="b5999-154">In this last example, two endpoints are configured for the `HelloWorld` service type.</span></span> <span data-ttu-id="b5999-155">Her uç nokta aynı `bindingConfiguration` bağlama türünün farklı bir özelleştirilmiş özniteliği kullanır (her biri `basicHttpBinding`değiştirir).</span><span class="sxs-lookup"><span data-stu-id="b5999-155">Each endpoint uses a different customized  `bindingConfiguration` attribute of the same binding type (each modifies the `basicHttpBinding`).</span></span>  
  
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
  
 <span data-ttu-id="b5999-156">Bir `protocolMapping` bölüm ekleyerek ve aşağıdaki örnekte gösterildiği gibi bağlamaları yapılandırarak varsayılan yapılandırmayı kullanarak aynı davranışı elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5999-156">You can get the same behavior using the default configuration by adding a `protocolMapping` section and configuring the bindings as demonstrated in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b5999-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5999-157">See also</span></span>

- [<span data-ttu-id="b5999-158">Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b5999-158">Simplified Configuration</span></span>](simplified-configuration.md)
- [<span data-ttu-id="b5999-159">Sistem Destekli Ciltler</span><span class="sxs-lookup"><span data-stu-id="b5999-159">System-Provided Bindings</span></span>](system-provided-bindings.md)
- [<span data-ttu-id="b5999-160">Uç Noktası Oluşturma Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b5999-160">Endpoint Creation Overview</span></span>](endpoint-creation-overview.md)
- [<span data-ttu-id="b5999-161">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="b5999-161">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
