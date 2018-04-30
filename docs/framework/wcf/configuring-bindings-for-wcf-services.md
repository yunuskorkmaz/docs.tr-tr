---
title: Windows Communication Foundation Hizmetleri için Bağlamaları Yapılandırma
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- binding configuration [WCF]
ms.assetid: 99a85fd8-f7eb-4a84-a93e-7721b37d415c
caps.latest.revision: 36
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f98d7c7b7d816687487a652f0527886300f0ee86
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="configuring-bindings-for-windows-communication-foundation-services"></a><span data-ttu-id="7542c-102">Windows Communication Foundation Hizmetleri için Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="7542c-102">Configuring Bindings for Windows Communication Foundation Services</span></span>
<span data-ttu-id="7542c-103">Bir uygulama oluştururken, genellikle uygulama dağıtımdan sonra yönetici kararları erteleneceği istersiniz.</span><span class="sxs-lookup"><span data-stu-id="7542c-103">When creating an application, you often want to defer decisions to the administrator after the deployment of the application.</span></span> <span data-ttu-id="7542c-104">Örneğin, genellikle bir hizmet adresi ya da Tekdüzen Kaynak Tanımlayıcısı (URI) ne olacağını önceden bilmesinin yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="7542c-104">For example, there is often no way of knowing in advance what a service address, or Uniform Resource Identifier (URI), will be.</span></span> <span data-ttu-id="7542c-105">Sabit bir adresi kodlama yerine, bir hizmet oluşturduktan sonra bunu yapmak için yönetici izin vermek için tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="7542c-105">Instead of hard-coding an address, it is preferable to allow an administrator to do so after creating a service.</span></span> <span data-ttu-id="7542c-106">Bu esneklik yapılandırma aracılığıyla gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="7542c-106">This flexibility is accomplished through configuration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7542c-107">Kullanım [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ile `/config` hızlı bir şekilde yapılandırma dosyaları oluşturmak için anahtar.</span><span class="sxs-lookup"><span data-stu-id="7542c-107">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) with the `/config` switch to quickly create configuration files.</span></span>  
  
## <a name="major-sections"></a><span data-ttu-id="7542c-108">Ana bölümleri</span><span class="sxs-lookup"><span data-stu-id="7542c-108">Major Sections</span></span>  
 <span data-ttu-id="7542c-109">[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Yapılandırma Şeması aşağıdaki üç ana bölümleri içerir (`serviceModel`, `bindings`, ve `services`):</span><span class="sxs-lookup"><span data-stu-id="7542c-109">The [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] configuration scheme includes the following three major sections (`serviceModel`, `bindings`, and `services`):</span></span>  
  
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
  
### <a name="servicemodel-elements"></a><span data-ttu-id="7542c-110">ServiceModel öğeleri</span><span class="sxs-lookup"><span data-stu-id="7542c-110">ServiceModel Elements</span></span>  
 <span data-ttu-id="7542c-111">İlişkisindeki tarafından bölüm kullanabilirsiniz `system.ServiceModel` öğesi bir hizmet türünün bir veya daha fazla uç noktaları gibi bir hizmete yönelik ayarları yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="7542c-111">You can use the section bounded by the `system.ServiceModel` element to configure a service type with one or more endpoints, as well as settings for a service.</span></span> <span data-ttu-id="7542c-112">Her uç nokta bir adresi, bir sözleşme ve bağlama ile yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="7542c-112">Each endpoint can then be configured with an address, a contract, and a binding.</span></span> <span data-ttu-id="7542c-113">Uç noktalar hakkında daha fazla bilgi için bkz: [uç noktası oluşturma genel bakış](../../../docs/framework/wcf/endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="7542c-113">For more information about endpoints, see [Endpoint Creation Overview](../../../docs/framework/wcf/endpoint-creation-overview.md).</span></span> <span data-ttu-id="7542c-114">Uç nokta yok belirtilirse, çalışma zamanı varsayılan uç noktaları ekler.</span><span class="sxs-lookup"><span data-stu-id="7542c-114">If no endpoints are specified, the runtime adds default endpoints.</span></span> <span data-ttu-id="7542c-115">Varsayılan uç noktalar, bağlamaları ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="7542c-115">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
 <span data-ttu-id="7542c-116">Bir bağlama taşımaları (HTTP, TCP, Kanallar, Message Queuing) ve protokolleri (güvenlik, güvenilirlik, işlem akışları) belirtir ve bağlama öğeleri, her biri bir uç nokta nasıl iletişim kurduğu en/boy dünyayla belirtir oluşur.</span><span class="sxs-lookup"><span data-stu-id="7542c-116">A binding specifies transports (HTTP, TCP, pipes, Message Queuing) and protocols (Security, Reliability, Transaction flows) and consists of binding elements, each of which specifies an aspect of how an endpoint communicates with the world.</span></span>  
  
 <span data-ttu-id="7542c-117">Örneğin, belirten [ \<basicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) öğesi belirten HTTP taşıma olarak bir uç noktası için kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="7542c-117">For example, specifying the [\<basicHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element indicates to use HTTP as the transport for an endpoint.</span></span> <span data-ttu-id="7542c-118">Bu kullanılan kablo uç noktası Bu uç nokta kullanarak hizmet açıldığında çalışma zamanında ayarlama için.</span><span class="sxs-lookup"><span data-stu-id="7542c-118">This is used to wire up the endpoint at run time when the service using this endpoint is opened.</span></span>  
  
 <span data-ttu-id="7542c-119">Bağlamalar iki tür vardır: önceden tanımlanmış ve özel.</span><span class="sxs-lookup"><span data-stu-id="7542c-119">There are two kinds of bindings: predefined and custom.</span></span> <span data-ttu-id="7542c-120">Önceden tanımlanmış bağlamaları yararlı birleşimlerini ortak senaryolarda kullanılır öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="7542c-120">Predefined bindings contain useful combinations of elements that are used in common scenarios.</span></span> <span data-ttu-id="7542c-121">Önceden tanımlanmış bağlama listesi türleri için [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] sağlar, bkz: [System-Provided bağlamaları](../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="7542c-121">For a list of predefined binding types that [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] provides, see [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md).</span></span> <span data-ttu-id="7542c-122">Önceden tanımlanmış bağlama koleksiyonu bir hizmet uygulaması gereken özellikleri doğru birleşimini varsa, uygulamanın gereksinimlerini karşılamak için özel bağlamalar oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7542c-122">If no predefined binding collection has the correct combination of features that a service application needs, you can construct custom bindings to meet the application's requirements.</span></span> <span data-ttu-id="7542c-123">Özel bağlama hakkında daha fazla bilgi için bkz: [ \<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="7542c-123">For more information about custom bindings, see [\<customBinding>](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
 <span data-ttu-id="7542c-124">Aşağıdaki dört örnekler ayarlamak için kullanılan en yaygın bağlama yapılandırmaları göstermek bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet.</span><span class="sxs-lookup"><span data-stu-id="7542c-124">The following four examples illustrate the most common binding configurations used for setting up a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service.</span></span>  
  
#### <a name="specifying-an-endpoint-to-use-a-binding-type"></a><span data-ttu-id="7542c-125">Bağlama türü kullanmak için bir uç nokta belirtme</span><span class="sxs-lookup"><span data-stu-id="7542c-125">Specifying an Endpoint to Use a Binding Type</span></span>  
 <span data-ttu-id="7542c-126">İlk örnek bir adresi, bir sözleşme ve bağlama ile yapılandırılan bir uç noktası belirtmek nasıl gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7542c-126">The first example illustrates how to specify an endpoint configured with an address, a contract, and a binding.</span></span>  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
  <!—- This section is optional with the default configuration introduced  
       in .NET Framework 4. -->  
  <endpoint   
      address="/HelloWorld2/"  
      contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
      binding="basicHttpBinding" />
</service>  
```  
  
 <span data-ttu-id="7542c-127">Bu örnekte, `name` özniteliği yapılandırmadır için hangi hizmet türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="7542c-127">In this example, the `name` attribute indicates which service type the configuration is for.</span></span> <span data-ttu-id="7542c-128">Kodunuzu ile bir hizmet oluşturduğunuzda `HelloWorld` sözleşme, örnek yapılandırmada tanımlanan bitiş noktalarının tümü ile başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="7542c-128">When you create a service in your code with the `HelloWorld` contract, it is initialized with all of the endpoints defined in the example configuration.</span></span> <span data-ttu-id="7542c-129">Derleme yalnızca bir hizmet sözleşmesi, uyguluyorsa `name` hizmeti yalnızca kullanılabilir türü kullandığından özniteliği'nin etmeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7542c-129">If the assembly implements only one service contract, the `name` attribute can be omitted because the service uses the only available type.</span></span> <span data-ttu-id="7542c-130">Öznitelik biçiminde olması gereken bir dize alır `Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`</span><span class="sxs-lookup"><span data-stu-id="7542c-130">The attribute takes a string, which must be in the format `Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`</span></span>  
  
 <span data-ttu-id="7542c-131">`address` Özniteliği, diğer uç noktaları için hizmet iletişim kurmak için kullandıkları URI belirtir.</span><span class="sxs-lookup"><span data-stu-id="7542c-131">The `address` attribute specifies the URI that other endpoints use to communicate to the service.</span></span> <span data-ttu-id="7542c-132">URI mutlak veya göreli yol ya da olabilir.</span><span class="sxs-lookup"><span data-stu-id="7542c-132">The URI can be either an absolute or relative path.</span></span> <span data-ttu-id="7542c-133">Göreli bir adresi sağlanırsa, konak bağlama kullanılan aktarma düzeni için uygun bir taban adresi sağlaması beklenir.</span><span class="sxs-lookup"><span data-stu-id="7542c-133">If a relative address is provided, the host is expected to provide a base address that is appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="7542c-134">Bir adresi yapılandırılmamışsa, taban adresi Bu uç nokta adresi olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="7542c-134">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span>  
  
 <span data-ttu-id="7542c-135">`contract` Özniteliği bu bitiş noktasının sunduğu sözleşme belirtir.</span><span class="sxs-lookup"><span data-stu-id="7542c-135">The `contract` attribute specifies the contract this endpoint is exposing.</span></span> <span data-ttu-id="7542c-136">Hizmet uygulama türü sözleşme türü uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="7542c-136">The service implementation type must implement the contract type.</span></span> <span data-ttu-id="7542c-137">Bir hizmet uygulaması tek anlaşma türü uygularsa, bu özellik atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="7542c-137">If a service implementation implements a single contract type, then this property can be omitted.</span></span>  
  
 <span data-ttu-id="7542c-138">`binding` Özniteliği bu belirli uç noktası için kullanılacak önceden tanımlanmış veya özel bir bağlama seçer.</span><span class="sxs-lookup"><span data-stu-id="7542c-138">The `binding` attribute selects a predefined or custom binding to use for this specific endpoint.</span></span> <span data-ttu-id="7542c-139">Açıkça bağlama seçmez bir uç nokta olan varsayılan bağlama seçimi kullanır `BasicHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="7542c-139">An endpoint that does not explicitly select a binding uses the default binding selection, which is `BasicHttpBinding`.</span></span>  
  
#### <a name="modifying-a-predefined-binding"></a><span data-ttu-id="7542c-140">Önceden tanımlanmış bir bağlama değiştirme</span><span class="sxs-lookup"><span data-stu-id="7542c-140">Modifying a Predefined Binding</span></span>  
 <span data-ttu-id="7542c-141">Aşağıdaki örnekte, önceden tanımlanmış bir bağlama değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="7542c-141">In the following example, a predefined binding is modified.</span></span> <span data-ttu-id="7542c-142">Ardından, herhangi bir uç nokta hizmetinde yapılandırmak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7542c-142">It can then be used to configure any endpoint in the service.</span></span> <span data-ttu-id="7542c-143">Bağlama ayarlayarak değiştiren <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> 1 saniye için değer.</span><span class="sxs-lookup"><span data-stu-id="7542c-143">The binding is modified by setting the <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> value to 1 second.</span></span> <span data-ttu-id="7542c-144">Özelliğin döndürdüğü Not bir <xref:System.TimeSpan> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="7542c-144">Note that the property returns a <xref:System.TimeSpan> object.</span></span>  
  
 <span data-ttu-id="7542c-145">Değiştirilmiş bağlama bağlamaları bölümünde bulunur.</span><span class="sxs-lookup"><span data-stu-id="7542c-145">That altered binding is found in the bindings section.</span></span> <span data-ttu-id="7542c-146">Bu değişiklik bağlama artık herhangi bir uç nokta ayarlayarak oluştururken kullanılabilir `binding` özniteliğini `endpoint` öğesi.</span><span class="sxs-lookup"><span data-stu-id="7542c-146">This altered binding can now be used when creating any endpoint by setting the `binding` attribute in the `endpoint` element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7542c-147">Bağlama, belirli bir adı verirseniz `bindingConfiguration` hizmetinde belirtilen bitiş noktası ile eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="7542c-147">If you give a particular name to the binding, the `bindingConfiguration` specified in the service endpoint must match with it.</span></span>  
  
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
  
## <a name="configuring-a-behavior-to-apply-to-a-service"></a><span data-ttu-id="7542c-148">Bir hizmete uygulamak için bir davranışını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="7542c-148">Configuring a Behavior to Apply to a Service</span></span>  
 <span data-ttu-id="7542c-149">Aşağıdaki örnekte, belirli bir davranışı hizmet türü için yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="7542c-149">In the following example, a specific behavior is configured for the service type.</span></span> <span data-ttu-id="7542c-150">`ServiceMetadataBehavior` Öğesi etkinleştirmek için kullanılan [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmet sorgulamak ve Web Hizmetleri Açıklama Dili (WSDL) belgeleri meta verileri oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="7542c-150">The `ServiceMetadataBehavior` element is used to enable the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to query the service and generate Web Services Description Language (WSDL) documents from the metadata.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7542c-151">Davranış için belirli bir adı verirseniz `behaviorConfiguration` hizmet uç noktası belirtilen bölüm onu eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="7542c-151">If you give a particular name to the behavior, the `behaviorConfiguration` specified in the service or endpoint section must match it.</span></span>  
  
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
  
 <span data-ttu-id="7542c-152">Önceki yapılandırma sağlayan bir çağrı ve "HelloWorld" meta verilerini almak için istemci hizmeti belirtilmiş.</span><span class="sxs-lookup"><span data-stu-id="7542c-152">The preceding configuration enables a client to call and get the metadata of the "HelloWorld" typed service.</span></span>  
  
 `svcutil /config:Client.exe.config http://computer:8080/Hello?wsdl`  
  
## <a name="specifying-a-service-with-two-endpoints-using-different-binding-values"></a><span data-ttu-id="7542c-153">Bir hizmet farklı bağlama değerleri kullanarak iki uç nokta ile belirtme</span><span class="sxs-lookup"><span data-stu-id="7542c-153">Specifying a Service with Two Endpoints Using Different Binding Values</span></span>  
 <span data-ttu-id="7542c-154">Son Bu örnekte, iki uç nokta için yapılandırılmış olan `HelloWorld` hizmet türü.</span><span class="sxs-lookup"><span data-stu-id="7542c-154">In this last example, two endpoints are configured for the `HelloWorld` service type.</span></span> <span data-ttu-id="7542c-155">Her uç nokta farklı bir özelleştirilmiş kullanır `bindingConfiguration` öznitelik aynı bağlama türü (her değiştirir `basicHttpBinding`).</span><span class="sxs-lookup"><span data-stu-id="7542c-155">Each endpoint uses a different customized  `bindingConfiguration` attribute of the same binding type (each modifies the `basicHttpBinding`).</span></span>  
  
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
  
 <span data-ttu-id="7542c-156">Ekleyerek varsayılan yapılandırmayı kullanarak aynı davranışı elde edebilirsiniz bir `protocolMapping` bölümü ve aşağıdaki örnekte gösterildiği gibi bağlamaları yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="7542c-156">You can get the same behavior using the default configuration by adding a `protocolMapping` section and configuring the bindings as demonstrated in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7542c-157">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7542c-157">See Also</span></span>  
 [<span data-ttu-id="7542c-158">Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="7542c-158">Simplified Configuration</span></span>](../../../docs/framework/wcf/simplified-configuration.md)  
 [<span data-ttu-id="7542c-159">Sistem Tarafından Sağlanan Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="7542c-159">System-Provided Bindings</span></span>](../../../docs/framework/wcf/system-provided-bindings.md)  
 [<span data-ttu-id="7542c-160">Uç Nokta Oluşturmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7542c-160">Endpoint Creation Overview</span></span>](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [<span data-ttu-id="7542c-161">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="7542c-161">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
