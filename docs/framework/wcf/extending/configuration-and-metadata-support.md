---
title: Yapılandırma ve Meta Veri Desteği
ms.date: 03/30/2017
ms.assetid: 27c240cb-8cab-472c-87f8-c864f4978758
ms.openlocfilehash: 0ec8c3286037e7adbe6f5efb73e846a30b9d48d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185661"
---
# <a name="configuration-and-metadata-support"></a><span data-ttu-id="60433-102">Yapılandırma ve Meta Veri Desteği</span><span class="sxs-lookup"><span data-stu-id="60433-102">Configuration and Metadata Support</span></span>
<span data-ttu-id="60433-103">Bu konu, bağlamalar ve bağlama öğeleri için yapılandırma ve meta veri desteğinin nasıl etkinleştirilen açıklanır.</span><span class="sxs-lookup"><span data-stu-id="60433-103">This topic describes how to enable configuration and metadata support for bindings and binding elements.</span></span>  
  
## <a name="overview-of-configuration-and-metadata"></a><span data-ttu-id="60433-104">Yapılandırma ve Meta Verilere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="60433-104">Overview of Configuration and Metadata</span></span>  
 <span data-ttu-id="60433-105">Bu konu, [Gelişmekte Olan Kanallar](developing-channels.md) görev listesinde isteğe bağlı öğeler 1, 2 ve 4 olan aşağıdaki görevleri tartışır.</span><span class="sxs-lookup"><span data-stu-id="60433-105">This topic discusses the following tasks, which are optional items 1, 2, and 4 in the [Developing Channels](developing-channels.md) task list.</span></span>  
  
- <span data-ttu-id="60433-106">Bağlama öğesi için yapılandırma dosyası desteğini etkinleştirme.</span><span class="sxs-lookup"><span data-stu-id="60433-106">Enabling configuration file support for a binding element.</span></span>  
  
- <span data-ttu-id="60433-107">Bağlama için yapılandırma dosyası desteğini etkinleştirme.</span><span class="sxs-lookup"><span data-stu-id="60433-107">Enabling configuration file support for a binding.</span></span>  
  
- <span data-ttu-id="60433-108">Bağlayıcı bir öğe için WSDL ve ilke iddiaları dışa aktarma.</span><span class="sxs-lookup"><span data-stu-id="60433-108">Exporting WSDL and policy assertions for a binding element.</span></span>  
  
- <span data-ttu-id="60433-109">Bağlayıcı veya bağlayıcı öğenizi eklemek ve yapılandırmak için WSDL ve ilke iddialarını tanımlama.</span><span class="sxs-lookup"><span data-stu-id="60433-109">Identifying WSDL and policy assertions to insert and configure your binding or binding element.</span></span>  
  
 <span data-ttu-id="60433-110">Kullanıcı tanımlı bağlamalar ve bağlama öğeleri oluşturma hakkında bilgi için sırasıyla [Kullanıcı Tanımlı Bağlamalar Oluşturma](creating-user-defined-bindings.md) ve [Bağlama Öğesi Oluşturma'ya](creating-a-bindingelement.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="60433-110">For information about creating user-defined bindings and binding elements, see [Creating User-Defined Bindings](creating-user-defined-bindings.md) and [Creating a BindingElement](creating-a-bindingelement.md), respectively.</span></span>  
  
## <a name="adding-configuration-support"></a><span data-ttu-id="60433-111">Yapılandırma Desteği Ekleme</span><span class="sxs-lookup"><span data-stu-id="60433-111">Adding Configuration Support</span></span>  
 <span data-ttu-id="60433-112">Bir kanal için yapılandırma dosyası desteğini etkinleştirmek için, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>bağlama öğeleri <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>için yapılandırma desteği sağlayan ve bağlayıcılar için yapılandırma desteğini etkinleştiren iki yapılandırma bölümü uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="60433-112">To enable configuration file support for a channel, you must implement two configuration sections, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>, which enables configuration support for binding elements, and the <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> and <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>, which enable configuration support for bindings.</span></span>  
  
 <span data-ttu-id="60433-113">Bunu yapmanın daha kolay bir yolu, bağlamalarınız ve bağlama öğeleriniz için yapılandırma kodu oluşturmak için [ConfigurationCodeGenerator](../samples/configurationcodegenerator.md) örnek aracını kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="60433-113">An easier way to do this is to use the [ConfigurationCodeGenerator](../samples/configurationcodegenerator.md) sample tool to generate configuration code for your bindings and binding elements.</span></span>  
  
### <a name="extending-bindingelementextensionelement"></a><span data-ttu-id="60433-114">CiltlemeElementExtensionElement</span><span class="sxs-lookup"><span data-stu-id="60433-114">Extending BindingElementExtensionElement</span></span>  
 <span data-ttu-id="60433-115">Aşağıdaki örnek kod [Transport: UDP](../samples/transport-udp.md) örneğinden alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="60433-115">The following example code is taken from the [Transport: UDP](../samples/transport-udp.md) sample.</span></span> <span data-ttu-id="60433-116">Yapılandırma `UdpTransportElement` sistemine <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> maruz `UdpTransportBindingElement` olan bir dir.</span><span class="sxs-lookup"><span data-stu-id="60433-116">The `UdpTransportElement` is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> that exposes `UdpTransportBindingElement` to the configuration system.</span></span> <span data-ttu-id="60433-117">Birkaç temel geçersiz kılmayla, örnek yapılandırma kesit adını, bağlama öğesinin türünü ve bağlama öğesinin nasıl oluşturulmasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="60433-117">With a few basic overrides, the sample defines the configuration section name, the type of the binding element and how to create the binding element.</span></span> <span data-ttu-id="60433-118">Kullanıcılar daha sonra uzantı bölümünü bir yapılandırma dosyasına aşağıdaki gibi kaydedebilirler.</span><span class="sxs-lookup"><span data-stu-id="60433-118">Users can then register the extension section in a configuration file as follows.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <bindingElementExtensions>  
      <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportElement, UdpTransport />  
      </bindingElementExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="60433-119">Uzantı, udp'yi aktarım olarak kullanmak için özel bağlamalardan başvurulabilir.</span><span class="sxs-lookup"><span data-stu-id="60433-119">The extension can be referenced from custom bindings to use UDP as the transport.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <customBinding>  
       <binding configurationName="UdpCustomBinding">  
         <udpTransport/>  
       </binding>  
      </customBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="adding-configuration-for-a-binding"></a><span data-ttu-id="60433-120">Bağlama için Yapılandırma Ekleme</span><span class="sxs-lookup"><span data-stu-id="60433-120">Adding Configuration for a Binding</span></span>  
 <span data-ttu-id="60433-121">Bölüm, `SampleProfileUdpBindingCollectionElement` yapılandırma <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> sistemine `SampleProfileUdpBinding` maruz kalan bir bölümdür.</span><span class="sxs-lookup"><span data-stu-id="60433-121">The section `SampleProfileUdpBindingCollectionElement` is a <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> that exposes `SampleProfileUdpBinding` to the configuration system.</span></span> <span data-ttu-id="60433-122">Uygulamanın büyük bir kısmı `SampleProfileUdpBindingConfigurationElement`, ' den <xref:System.ServiceModel.Configuration.StandardBindingElement>türetilen .</span><span class="sxs-lookup"><span data-stu-id="60433-122">The bulk of the implementation is delegated to the `SampleProfileUdpBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="60433-123">Üzerinde `SampleProfileUdpBindingConfigurationElement` özellikleri `SampleProfileUdpBinding`karşılık gelen özelliklere sahip ve `ConfigurationElement` bağlama eşlenecek işlevleri.</span><span class="sxs-lookup"><span data-stu-id="60433-123">The `SampleProfileUdpBindingConfigurationElement` has properties that correspond to the properties on `SampleProfileUdpBinding`, and functions to map from the `ConfigurationElement` binding.</span></span> <span data-ttu-id="60433-124">Son olarak, `OnApplyConfiguration` `SampleProfileUdpBinding`yöntem, aşağıdaki örnek kodda gösterildiği gibi, geçersiz kılınmış.</span><span class="sxs-lookup"><span data-stu-id="60433-124">Finally, the `OnApplyConfiguration` method is overridden in the `SampleProfileUdpBinding`, as shown in the following sample code.</span></span>  
  
```csharp
protected override void OnApplyConfiguration(string configurationName)  
{  
            if (binding == null)  
                throw new ArgumentNullException("binding");  
  
            if (binding.GetType() != typeof(SampleProfileUdpBinding))  
            {  
                var expectedType = typeof(SampleProfileUdpBinding).AssemblyQualifiedName;
                var typePassedIn = binding.GetType().AssemblyQualifiedName;
                throw new ArgumentException($"Invalid type for binding. Expected type: {expectedType}. Type passed in: {typePassedIn}.");  
            }  
            SampleProfileUdpBinding udpBinding = (SampleProfileUdpBinding)binding;  
  
            udpBinding.OrderedSession = this.OrderedSession;  
            udpBinding.ReliableSessionEnabled = this.ReliableSessionEnabled;  
            udpBinding.SessionInactivityTimeout = this.SessionInactivityTimeout;  
            if (this.ClientBaseAddress != null)  
                   udpBinding.ClientBaseAddress = ClientBaseAddress;  
}  
```  
  
 <span data-ttu-id="60433-125">Bu işleyiciyi yapılandırma sistemine kaydetmek için aşağıdaki bölümü ilgili yapılandırma dosyasına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="60433-125">To register this handler with the configuration system, add the following section to the relevant configuration file.</span></span>  
  
```xml  
<configuration>  
  <configSections>  
     <sectionGroup name="system.serviceModel">  
         <sectionGroup name="bindings">  
                 <section name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport />  
         </sectionGroup>  
     </sectionGroup>  
  </configSections>  
</configuration>  
```  
  
 <span data-ttu-id="60433-126">Daha sonra [ \<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) yapılandırma bölümünden başvurulabilir.</span><span class="sxs-lookup"><span data-stu-id="60433-126">It can then be referenced from the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) configuration section.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint configurationName="calculator"  
                address="soap.udp://localhost:8001/"
                bindingConfiguration="CalculatorServer"  
                binding="sampleProfileUdpBinding"
                contract= "Microsoft.ServiceModel.Samples.ICalculatorContract">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="adding-metadata-support-for-a-binding-element"></a><span data-ttu-id="60433-127">Bağlayıcı Öğe için Meta Veri Desteği Ekleme</span><span class="sxs-lookup"><span data-stu-id="60433-127">Adding Metadata Support for a Binding Element</span></span>  
 <span data-ttu-id="60433-128">Bir kanalı meta veri sistemine entegre etmek için, hem ipolitikasının hem de dışa aktarmanın desteklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="60433-128">To integrate a channel into the metadata system, it must support both the import and export of policy.</span></span> <span data-ttu-id="60433-129">Bu, [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) gibi araçların bağlama öğesinin istemcilerini oluşturmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="60433-129">This allows tools such as [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate clients of the binding element.</span></span>  
  
### <a name="adding-wsdl-support"></a><span data-ttu-id="60433-130">WSDL Desteği Ekleme</span><span class="sxs-lookup"><span data-stu-id="60433-130">Adding WSDL Support</span></span>  
 <span data-ttu-id="60433-131">Bağlayıcıdaki aktarım bağlama öğesi, meta verilerdeki adresleme bilgilerinin dışa aktarılmasından ve aktarılmasından sorumludur.</span><span class="sxs-lookup"><span data-stu-id="60433-131">The transport binding element in a binding is responsible for exporting and importing addressing information in metadata.</span></span> <span data-ttu-id="60433-132">SOAP bağlama kullanırken, taşıma bağlama elemanı da meta verilerde doğru bir aktarım URI dışa aktarmalıdır.</span><span class="sxs-lookup"><span data-stu-id="60433-132">When using a SOAP binding, the transport binding element should also export a correct transport URI in metadata.</span></span> <span data-ttu-id="60433-133">Aşağıdaki örnek kod [Transport: UDP](../samples/transport-udp.md) örneğinden alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="60433-133">The following example code is taken from the [Transport: UDP](../samples/transport-udp.md) sample.</span></span>  
  
#### <a name="wsdl-export"></a><span data-ttu-id="60433-134">WSDL İhracat</span><span class="sxs-lookup"><span data-stu-id="60433-134">WSDL Export</span></span>  
 <span data-ttu-id="60433-135">Adres bilgilerini dışa `UdpTransportBindingElement` aktarmak için <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="60433-135">To export addressing information, the `UdpTransportBindingElement` implements the <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="60433-136">Yöntem, <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> WSDL bağlantı noktasına doğru adresbilgilerini ekler.</span><span class="sxs-lookup"><span data-stu-id="60433-136">The <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> method adds the correct addressing information to the WSDL port.</span></span>  
  
```csharp  
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 <span data-ttu-id="60433-137">Yöntemin `UdpTransportBindingElement` <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> uygulanması, bitiş noktası BIR SOAP bağlama kullandığında bir taşıma URI'si de dışa aktarmaktadır:</span><span class="sxs-lookup"><span data-stu-id="60433-137">The `UdpTransportBindingElement` implementation of the <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> method also exports a transport URI when the endpoint uses a SOAP binding:</span></span>  
  
```csharp  
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a><span data-ttu-id="60433-138">WSDL İthalat</span><span class="sxs-lookup"><span data-stu-id="60433-138">WSDL Import</span></span>  
 <span data-ttu-id="60433-139">WSDL alma sistemini adresleri alma işlemlerini işlemek için genişletmek için, Svcutil.exe.config dosyasında gösterildiği gibi Svcutil.exe yapılandırma dosyasına aşağıdaki yapılandırmayı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="60433-139">To extend the WSDL import system to handle importing the addresses, add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <wsdlImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="60433-140">Svcutil.exe çalıştırırken, WSDL alma uzantıları yüklemek için Svcutil.exe almak için iki seçenek vardır:</span><span class="sxs-lookup"><span data-stu-id="60433-140">When running Svcutil.exe, there are two options for getting Svcutil.exe to load the WSDL import extensions:</span></span>  
  
1. <span data-ttu-id="60433-141">/SvcutilConfig kullanarak yapılandırma dosyasına Point Svcutil.exe:\<dosya>.</span><span class="sxs-lookup"><span data-stu-id="60433-141">Point Svcutil.exe to the configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="60433-142">Yapılandırma bölümünü Svcutil.exe ile aynı dizinde Svcutil.exe.config'e ekleyin.</span><span class="sxs-lookup"><span data-stu-id="60433-142">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
 <span data-ttu-id="60433-143">Tür `UdpBindingElementImporter` <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="60433-143">The `UdpBindingElementImporter` type implements the <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="60433-144">Yöntem `ImportEndpoint` wsdl bağlantı noktasından adresi içeri zabıta:</span><span class="sxs-lookup"><span data-stu-id="60433-144">The `ImportEndpoint` method imports the address from the WSDL port:</span></span>  
  
```csharp  
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a><span data-ttu-id="60433-145">İlke Desteği Ekleme</span><span class="sxs-lookup"><span data-stu-id="60433-145">Adding Policy Support</span></span>  
 <span data-ttu-id="60433-146">Özel bağlama öğesi, bu bağlama öğesinin yeteneklerini ifade etmek için bir hizmet bitiş noktası için WSDL bağlayıcıilki iddialarını dışa aktarabilir.</span><span class="sxs-lookup"><span data-stu-id="60433-146">The custom binding element can export policy assertions in the WSDL binding for a service endpoint to express the capabilities of that binding element.</span></span> <span data-ttu-id="60433-147">Aşağıdaki örnek kod [Transport: UDP](../samples/transport-udp.md) örneğinden alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="60433-147">The following example code is taken from the [Transport: UDP](../samples/transport-udp.md) sample.</span></span>  
  
#### <a name="policy-export"></a><span data-ttu-id="60433-148">İlke İhracatı</span><span class="sxs-lookup"><span data-stu-id="60433-148">Policy Export</span></span>  
 <span data-ttu-id="60433-149">Tür, `UdpTransportBindingElement` dışa aktarma ilkesi için destek eklemek için uygular. <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="60433-149">The `UdpTransportBindingElement` type implements <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> to add support for exporting policy.</span></span> <span data-ttu-id="60433-150">Sonuç olarak, <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> `UdpTransportBindingElement` bunu içeren herhangi bir bağlama için ilke oluşturma içerir.</span><span class="sxs-lookup"><span data-stu-id="60433-150">As a result, <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> includes `UdpTransportBindingElement` in the generation of policy for any binding that includes it.</span></span>  
  
 <span data-ttu-id="60433-151">Kanal <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>çok noktaya yayın modundaysa, UDP için bir iddia ve başka bir iddia ekleyin.</span><span class="sxs-lookup"><span data-stu-id="60433-151">In <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>, add an assertion for UDP and another assertion if the channel is in multicast mode.</span></span> <span data-ttu-id="60433-152">Bunun nedeni, çok noktaya yayın modunun iletişim yığınının nasıl oluşturulduğuna etki etmesi ve bu nedenle her iki taraf arasında koordine edilmesi dir.</span><span class="sxs-lookup"><span data-stu-id="60433-152">This is because multicast mode affects how the communication stack is constructed, and thus must be coordinated between both sides.</span></span>  
  
```csharp  
ICollection<XmlElement> bindingAssertions = context.GetBindingAssertions();  
XmlDocument xmlDocument = new XmlDocument();  
bindingAssertions.Add(xmlDocument.CreateElement(  
UdpPolicyStrings.Prefix, UdpPolicyStrings.TransportAssertion, UdpPolicyStrings.UdpNamespace));  
if (Multicast)  
{  
    bindingAssertions.Add(xmlDocument.CreateElement(  
UdpPolicyStrings.Prefix, UdpPolicyStrings.MulticastAssertion,     UdpPolicyStrings.UdpNamespace));  
}  
```  
  
 <span data-ttu-id="60433-153">Özel aktarım bağlama öğeleri adresleme işlemekten sorumlu olduğundan, <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> ws-addressing sürümünü niçin kullanıldığını göstermek için uygun WS Adresleme ilkesi iddialarını dışa aktarma yı da ele almalıdır. `UdpTransportBindingElement`</span><span class="sxs-lookup"><span data-stu-id="60433-153">Because custom transport binding elements are responsible for handling addressing, the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> implementation on the `UdpTransportBindingElement` must also handle exporting the appropriate WS-Addressing policy assertions to indicate the version of WS-Addressing being used.</span></span>  
  
```csharp  
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a><span data-ttu-id="60433-154">İlke İthalatı</span><span class="sxs-lookup"><span data-stu-id="60433-154">Policy Import</span></span>  
 <span data-ttu-id="60433-155">İlke alma sistemini genişletmek için, Svcutil.exe.config dosyasında gösterildiği gibi Svcutil.exe için yapılandırma dosyasına aşağıdaki yapılandırmayı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="60433-155">To extend the policy import system, add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <policyImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="60433-156">Sonra bizim <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> kayıtlı sınıftan`UdpBindingElementImporter`uygulamak ( ).</span><span class="sxs-lookup"><span data-stu-id="60433-156">Then we implement <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> from our registered class (`UdpBindingElementImporter`).</span></span> <span data-ttu-id="60433-157">In <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, uygun ad alanında iddiaları incelemek ve taşıma oluşturmak ve çok noktaya mı olup olmadığını kontrol etmek için olanları işlemek.</span><span class="sxs-lookup"><span data-stu-id="60433-157">In <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, examine the assertions in the appropriate namespace and process the ones for generating the transport and checking if it is multicast.</span></span> <span data-ttu-id="60433-158">Ayrıca, içe aktarıcının işlediği iddiaları bağlayıcı iddialar listesinden kaldırın.</span><span class="sxs-lookup"><span data-stu-id="60433-158">In addition, remove the assertions that the importer handles from the list of binding assertions.</span></span> <span data-ttu-id="60433-159">Yine, Svcutil.exe çalıştırırken, tümleştirme için iki seçenek vardır:</span><span class="sxs-lookup"><span data-stu-id="60433-159">Again, when running Svcutil.exe, there are two options for integration:</span></span>  
  
1. <span data-ttu-id="60433-160">Svcutil.exe'yi /SvcutilConfig kullanarak yapılandırma\<dosyamıza yönlendirin: dosya>.</span><span class="sxs-lookup"><span data-stu-id="60433-160">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="60433-161">Yapılandırma bölümünü Svcutil.exe ile aynı dizinde Svcutil.exe.config'e ekleyin.</span><span class="sxs-lookup"><span data-stu-id="60433-161">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
### <a name="adding-a-custom-standard-binding-importer"></a><span data-ttu-id="60433-162">Özel Standart Bağlama İthalatçısı Ekleme</span><span class="sxs-lookup"><span data-stu-id="60433-162">Adding a Custom Standard Binding Importer</span></span>  
 <span data-ttu-id="60433-163">Svcutil.exe ve <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> türü, varsayılan olarak, tanımak ve sistem tarafından sağlanan bağlamaları alma.</span><span class="sxs-lookup"><span data-stu-id="60433-163">Svcutil.exe and the <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> type, by default, recognize and import system-provided bindings.</span></span> <span data-ttu-id="60433-164">Aksi takdirde, bağlama bir <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> örnek olarak içe aktarılır.</span><span class="sxs-lookup"><span data-stu-id="60433-164">Otherwise, the binding gets imported as a <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="60433-165">Svcutil.exe ve almak <xref:System.ServiceModel.Description.WsdlImporter> `SampleProfileUdpBinding` için `UdpBindingElementImporter` de özel bir standart bağlayıcı ithalatçı olarak hareket etmesini sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="60433-165">To enable Svcutil.exe and the <xref:System.ServiceModel.Description.WsdlImporter> to import the `SampleProfileUdpBinding` the `UdpBindingElementImporter` also acts as a custom standard binding importer.</span></span>  
  
 <span data-ttu-id="60433-166">Özel bir standart bağlayıcı içe `ImportEndpoint` aktarıcı, meta <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> verilerden alınan örneği incelemek ve belirli bir standart bağlama tarafından oluşturulabilir mi diye görmek için <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> arabirimde yöntem uygular.</span><span class="sxs-lookup"><span data-stu-id="60433-166">A custom standard binding importer implements the `ImportEndpoint` method on the <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface to examine the <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance imported from metadata to see if it could have been generated by specific standard binding.</span></span>  
  
```csharp  
if (context.Endpoint.Binding is CustomBinding)  
{  
    Binding binding;  
    if (transportBindingElement is UdpTransportBindingElement)  
    {  
        //if TryCreate is true, the CustomBinding will be replace by a SampleProfileUdpBinding in the  
        //generated config file for better typed generation.  
        if (SampleProfileUdpBinding.TryCreate(bindingElements, out binding))  
        {  
            binding.Name = context.Endpoint.Binding.Name;  
            binding.Namespace = context.Endpoint.Binding.Namespace;  
            context.Endpoint.Binding = binding;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="60433-167">Genel olarak, özel bir standart bağlama içe aktarma işlemi, yalnızca standart bağlama tarafından ayarlanmış olabilecek özelliklerin değiştiğini ve diğer tüm özelliklerin varsayılanları olduğunu doğrulamak için içe aktarılan bağlama öğelerinin özelliklerini denetlemeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="60433-167">Generally, implementing a custom standard binding importer involves checking the properties of the imported binding elements to verify that only properties that could have been set by the standard binding have changed and all other properties are their defaults.</span></span> <span data-ttu-id="60433-168">Standart bağlayıcı lık uygulamak için temel bir strateji, standart bağlamanın bir örneğini oluşturmak, özellikleri bağlama öğelerinden standart bağlamanın desteklediği standart bağlama örneğine yaymak ve bağlamayı karşılaştırmaktır. alınan bağlama elemanları ile standart bağlama öğeleri.</span><span class="sxs-lookup"><span data-stu-id="60433-168">A basic strategy for implementing a standard binding importer is to create an instance of the standard binding, propagate the properties from the binding elements to the standard binding instance that the standard binding supports, and the compare the binding elements from the standard binding with the imported binding elements.</span></span>
