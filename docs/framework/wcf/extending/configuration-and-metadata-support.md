---
title: Yapılandırma ve Meta Veri Desteği
ms.date: 03/30/2017
ms.assetid: 27c240cb-8cab-472c-87f8-c864f4978758
ms.openlocfilehash: 65c826c909496a9efeb99801142eb49e4f92d3bc
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183496"
---
# <a name="configuration-and-metadata-support"></a><span data-ttu-id="d5dff-102">Yapılandırma ve Meta Veri Desteği</span><span class="sxs-lookup"><span data-stu-id="d5dff-102">Configuration and Metadata Support</span></span>
<span data-ttu-id="d5dff-103">Bu konu, bağlamalar ve bağlama öğeleri yapılandırma ve meta veri desteğini etkinleştirmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="d5dff-103">This topic describes how to enable configuration and metadata support for bindings and binding elements.</span></span>  
  
## <a name="overview-of-configuration-and-metadata"></a><span data-ttu-id="d5dff-104">Yapılandırma ve meta veri genel bakış</span><span class="sxs-lookup"><span data-stu-id="d5dff-104">Overview of Configuration and Metadata</span></span>  
 <span data-ttu-id="d5dff-105">İsteğe bağlı öğeler 1, 2 ve 4 aşağıdaki görevleri bu konuda ele alınmıştır, [geliştirme kanalları](../../../../docs/framework/wcf/extending/developing-channels.md) görev listesi.</span><span class="sxs-lookup"><span data-stu-id="d5dff-105">This topic discusses the following tasks, which are optional items 1, 2, and 4 in the [Developing Channels](../../../../docs/framework/wcf/extending/developing-channels.md) task list.</span></span>  
  
-   <span data-ttu-id="d5dff-106">Yapılandırma dosyası bir bağlama öğesi desteğini etkinleştirme.</span><span class="sxs-lookup"><span data-stu-id="d5dff-106">Enabling configuration file support for a binding element.</span></span>  
  
-   <span data-ttu-id="d5dff-107">Yapılandırma dosyası bağlama desteğini etkinleştirme.</span><span class="sxs-lookup"><span data-stu-id="d5dff-107">Enabling configuration file support for a binding.</span></span>  
  
-   <span data-ttu-id="d5dff-108">WSDL ve ilke onaylamaları için bir bağlama öğesi veriliyor.</span><span class="sxs-lookup"><span data-stu-id="d5dff-108">Exporting WSDL and policy assertions for a binding element.</span></span>  
  
-   <span data-ttu-id="d5dff-109">WSDL ve ilke Onaylamalar eklemek ve bağlama veya bağlama öğesi yapılandırmak için tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="d5dff-109">Identifying WSDL and policy assertions to insert and configure your binding or binding element.</span></span>  
  
 <span data-ttu-id="d5dff-110">Kullanıcı tanımlı bağlamalar ve bağlama öğeleri oluşturma hakkında daha fazla bilgi için bkz: [Creating User-Defined bağlamaları](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md) ve [BindingElement oluşturma](../../../../docs/framework/wcf/extending/creating-a-bindingelement.md)sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="d5dff-110">For information about creating user-defined bindings and binding elements, see [Creating User-Defined Bindings](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md) and [Creating a BindingElement](../../../../docs/framework/wcf/extending/creating-a-bindingelement.md), respectively.</span></span>  
  
## <a name="adding-configuration-support"></a><span data-ttu-id="d5dff-111">Yapılandırma desteği ekleme</span><span class="sxs-lookup"><span data-stu-id="d5dff-111">Adding Configuration Support</span></span>  
 <span data-ttu-id="d5dff-112">Yapılandırma dosyası bir kanal desteğini etkinleştirmek için iki yapılandırma bölümlerini uygulamalıdır <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>, bağlama öğeleri, yapılandırma desteği sağlar ve <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> ve <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>, yapılandırma desteğini etkinleştir bağlamalar.</span><span class="sxs-lookup"><span data-stu-id="d5dff-112">To enable configuration file support for a channel, you must implement two configuration sections, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>, which enables configuration support for binding elements, and the <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> and <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>, which enable configuration support for bindings.</span></span>  
  
 <span data-ttu-id="d5dff-113">Bunu yapmak için daha kolay bir yolu kullanmaktır [ConfigurationCodeGenerator](../../../../docs/framework/wcf/samples/configurationcodegenerator.md) bağlamalar ve bağlama öğeleri yapılandırma kodunu oluşturmak için örnek araç.</span><span class="sxs-lookup"><span data-stu-id="d5dff-113">An easier way to do this is to use the [ConfigurationCodeGenerator](../../../../docs/framework/wcf/samples/configurationcodegenerator.md) sample tool to generate configuration code for your bindings and binding elements.</span></span>  
  
### <a name="extending-bindingelementextensionelement"></a><span data-ttu-id="d5dff-114">BindingElementExtensionElement genişletme</span><span class="sxs-lookup"><span data-stu-id="d5dff-114">Extending BindingElementExtensionElement</span></span>  
 <span data-ttu-id="d5dff-115">Aşağıdaki kod örneği alınır [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="d5dff-115">The following example code is taken from the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span> <span data-ttu-id="d5dff-116">`UdpTransportElement` Olduğu bir <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> kullanıma sunan `UdpTransportBindingElement` yapılandırma sistemi için.</span><span class="sxs-lookup"><span data-stu-id="d5dff-116">The `UdpTransportElement` is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> that exposes `UdpTransportBindingElement` to the configuration system.</span></span> <span data-ttu-id="d5dff-117">Birkaç temel geçersiz kılmaları ile örnek yapılandırma bölümü adı, bağlama öğesi türü ve bağlama öğesi oluşturulacağını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d5dff-117">With a few basic overrides, the sample defines the configuration section name, the type of the binding element and how to create the binding element.</span></span> <span data-ttu-id="d5dff-118">Kullanıcılar ardından uzantısı bölümüne bir yapılandırma dosyasında şu şekilde kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5dff-118">Users can then register the extension section in a configuration file as follows.</span></span>  
  
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
  
 <span data-ttu-id="d5dff-119">Uzantı UDP taşıma kullanmak için özel bağlamalar başvurulabilir.</span><span class="sxs-lookup"><span data-stu-id="d5dff-119">The extension can be referenced from custom bindings to use UDP as the transport.</span></span>  
  
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
  
### <a name="adding-configuration-for-a-binding"></a><span data-ttu-id="d5dff-120">Bir bağlama için yapılandırması ekleniyor</span><span class="sxs-lookup"><span data-stu-id="d5dff-120">Adding Configuration for a Binding</span></span>  
 <span data-ttu-id="d5dff-121">Bölüm `SampleProfileUdpBindingCollectionElement` olduğu bir <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> kullanıma sunan `SampleProfileUdpBinding` yapılandırma sistemi için.</span><span class="sxs-lookup"><span data-stu-id="d5dff-121">The section `SampleProfileUdpBindingCollectionElement` is a <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> that exposes `SampleProfileUdpBinding` to the configuration system.</span></span> <span data-ttu-id="d5dff-122">Toplu uygulama için temsilci `SampleProfileUdpBindingConfigurationElement`, öğesinden türetildiğini <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="d5dff-122">The bulk of the implementation is delegated to the `SampleProfileUdpBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="d5dff-123">`SampleProfileUdpBindingConfigurationElement` Üzerinde özelliklerine karşılık gelen özelliklerle sahip `SampleProfileUdpBinding`ve eşlenecek işlevleri `ConfigurationElement` bağlama.</span><span class="sxs-lookup"><span data-stu-id="d5dff-123">The `SampleProfileUdpBindingConfigurationElement` has properties that correspond to the properties on `SampleProfileUdpBinding`, and functions to map from the `ConfigurationElement` binding.</span></span> <span data-ttu-id="d5dff-124">Son olarak, `OnApplyConfiguration` yöntemi geçersiz kılınmıştır `SampleProfileUdpBinding`aşağıdaki örnek kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="d5dff-124">Finally, the `OnApplyConfiguration` method is overridden in the `SampleProfileUdpBinding`, as shown in the following sample code.</span></span>  
  
```csharp 
protected override void OnApplyConfiguration(string configurationName)  
{  
            if (binding == null)  
                throw new ArgumentNullException("binding");  
  
            if (binding.GetType() != typeof(SampleProfileUdpBinding))  
            {  
                throw new ArgumentException(string.Format(CultureInfo.CurrentCulture,  
                    "Invalid type for binding. Expected type: {0}. Type passed in: {1}.",  
                    typeof(SampleProfileUdpBinding).AssemblyQualifiedName,  
                    binding.GetType().AssemblyQualifiedName));  
            }  
            SampleProfileUdpBinding udpBinding = (SampleProfileUdpBinding)binding;  
  
            udpBinding.OrderedSession = this.OrderedSession;  
            udpBinding.ReliableSessionEnabled = this.ReliableSessionEnabled;  
            udpBinding.SessionInactivityTimeout = this.SessionInactivityTimeout;  
            if (this.ClientBaseAddress != null)  
                   udpBinding.ClientBaseAddress = ClientBaseAddress;  
}  
```  
  
 <span data-ttu-id="d5dff-125">Bu işleyici yapılandırma sistemi ile kaydetmek için aşağıdaki bölümde ilgili yapılandırma dosyasına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d5dff-125">To register this handler with the configuration system, add the following section to the relevant configuration file.</span></span>  
  
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
  
 <span data-ttu-id="d5dff-126">Öğesinden sonra başvurulabilir [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="d5dff-126">It can then be referenced from the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) configuration section.</span></span>  
  
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
  
## <a name="adding-metadata-support-for-a-binding-element"></a><span data-ttu-id="d5dff-127">Bir bağlama öğesi meta veri desteği eklendi</span><span class="sxs-lookup"><span data-stu-id="d5dff-127">Adding Metadata Support for a Binding Element</span></span>  
 <span data-ttu-id="d5dff-128">Bir kanal meta verileri sisteme tümleştirmek için içeri aktarma ve dışarı aktarma İlkesi desteklemelidir.</span><span class="sxs-lookup"><span data-stu-id="d5dff-128">To integrate a channel into the metadata system, it must support both the import and export of policy.</span></span> <span data-ttu-id="d5dff-129">Bu gibi araçlar sağlayan [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) bağlama öğesi istemcileri oluşturulacak.</span><span class="sxs-lookup"><span data-stu-id="d5dff-129">This allows tools such as [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate clients of the binding element.</span></span>  
  
### <a name="adding-wsdl-support"></a><span data-ttu-id="d5dff-130">WSDL desteği ekleme</span><span class="sxs-lookup"><span data-stu-id="d5dff-130">Adding WSDL Support</span></span>  
 <span data-ttu-id="d5dff-131">Bir bağlamadaki aktarım bağlama öğesinin dışarı ve içeri aktarma adres bilgilerini meta verilerinde sorumludur.</span><span class="sxs-lookup"><span data-stu-id="d5dff-131">The transport binding element in a binding is responsible for exporting and importing addressing information in metadata.</span></span> <span data-ttu-id="d5dff-132">SOAP bağlama kullanırken, aktarım bağlama öğesinin de meta verilerde doğru aktarım URI dışarı aktarmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d5dff-132">When using a SOAP binding, the transport binding element should also export a correct transport URI in metadata.</span></span> <span data-ttu-id="d5dff-133">Aşağıdaki kod örneği alınır [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="d5dff-133">The following example code is taken from the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
#### <a name="wsdl-export"></a><span data-ttu-id="d5dff-134">WSDL dışarı aktarma</span><span class="sxs-lookup"><span data-stu-id="d5dff-134">WSDL Export</span></span>  
 <span data-ttu-id="d5dff-135">Adresleme bilgilerini dışarı aktarmak için `UdpTransportBindingElement` uygulayan <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d5dff-135">To export addressing information, the `UdpTransportBindingElement` implements the <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="d5dff-136"><xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> Yöntemi WSDL bağlantı noktasına doğru adres bilgisi ekler.</span><span class="sxs-lookup"><span data-stu-id="d5dff-136">The <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> method adds the correct addressing information to the WSDL port.</span></span>  
  
```csharp  
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 <span data-ttu-id="d5dff-137">`UdpTransportBindingElement` Uygulaması <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> yöntemi uç nokta bir SOAP bağlama kullandığında bir aktarım URI ayrıca verir:</span><span class="sxs-lookup"><span data-stu-id="d5dff-137">The `UdpTransportBindingElement` implementation of the <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> method also exports a transport URI when the endpoint uses a SOAP binding:</span></span>  
  
```csharp  
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a><span data-ttu-id="d5dff-138">WSDL içeri aktarma</span><span class="sxs-lookup"><span data-stu-id="d5dff-138">WSDL Import</span></span>  
 <span data-ttu-id="d5dff-139">Adresleri içeri aktarma işlemek için WSDL içeri aktarma sistemini genişletmek için aşağıdaki yapılandırma Svcutil.exe.config dosyasında gösterildiği Svcutil.exe için yapılandırma dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d5dff-139">To extend the WSDL import system to handle importing the addresses, add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file:</span></span>  
  
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
  
 <span data-ttu-id="d5dff-140">Svcutil.exe çalıştırırken, WSDL içeri aktarma uzantıları yüklemek için Svcutil.exe alma iki seçenek vardır:</span><span class="sxs-lookup"><span data-stu-id="d5dff-140">When running Svcutil.exe, there are two options for getting Svcutil.exe to load the WSDL import extensions:</span></span>  
  
1.  <span data-ttu-id="d5dff-141">Noktası Svcutil.exe /SvcutilConfig kullanarak yapılandırma dosyasının:\<Dosya >.</span><span class="sxs-lookup"><span data-stu-id="d5dff-141">Point Svcutil.exe to the configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2.  <span data-ttu-id="d5dff-142">Yapılandırma bölümü Svcutil.exe.config için Svcutil.exe ile aynı dizinde ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d5dff-142">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
 <span data-ttu-id="d5dff-143">`UdpBindingElementImporter` Yazın uygular <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d5dff-143">The `UdpBindingElementImporter` type implements the <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="d5dff-144">`ImportEndpoint` Yöntemi WSDL bağlantı noktasından adresini alır:</span><span class="sxs-lookup"><span data-stu-id="d5dff-144">The `ImportEndpoint` method imports the address from the WSDL port:</span></span>  
  
```csharp  
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a><span data-ttu-id="d5dff-145">İlke desteği ekleme</span><span class="sxs-lookup"><span data-stu-id="d5dff-145">Adding Policy Support</span></span>  
 <span data-ttu-id="d5dff-146">Özel bağlama öğesi bağlamasında, bağlama öğesi yeteneklerini ifade etmek için WSDL hizmet uç noktası ilke onaylamalarını dışa aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5dff-146">The custom binding element can export policy assertions in the WSDL binding for a service endpoint to express the capabilities of that binding element.</span></span> <span data-ttu-id="d5dff-147">Aşağıdaki kod örneği alınır [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="d5dff-147">The following example code is taken from the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
#### <a name="policy-export"></a><span data-ttu-id="d5dff-148">İlkeyi dışarı aktarma</span><span class="sxs-lookup"><span data-stu-id="d5dff-148">Policy Export</span></span>  
 <span data-ttu-id="d5dff-149">`UdpTransportBindingElement` Yazın uygular <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> ilke dışarı aktarma için destek eklemek için.</span><span class="sxs-lookup"><span data-stu-id="d5dff-149">The `UdpTransportBindingElement` type implements <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> to add support for exporting policy.</span></span> <span data-ttu-id="d5dff-150">Sonuç olarak, <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> içerir `UdpTransportBindingElement` içerdiği herhangi bir bağlama için ilke oluşturma.</span><span class="sxs-lookup"><span data-stu-id="d5dff-150">As a result, <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> includes `UdpTransportBindingElement` in the generation of policy for any binding that includes it.</span></span>  
  
 <span data-ttu-id="d5dff-151">İçinde <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>, kanal çok noktaya yayın modunda değilse, UDP ve başka bir onaylama için onaylama Ekle.</span><span class="sxs-lookup"><span data-stu-id="d5dff-151">In <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>, add an assertion for UDP and another assertion if the channel is in multicast mode.</span></span> <span data-ttu-id="d5dff-152">Çok noktaya yayın modu etkilediğinden nasıl iletişim yığını oluşturulur ve bu nedenle her iki tarafın arasında koordine edilmelidir budur.</span><span class="sxs-lookup"><span data-stu-id="d5dff-152">This is because multicast mode affects how the communication stack is constructed, and thus must be coordinated between both sides.</span></span>  
  
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
  
 <span data-ttu-id="d5dff-153">Özel Aktarım bağlama öğeleriyle adresleme, işleme için sorumlu olduğundan <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> mantığınız `UdpTransportBindingElement` WS-Addressing sürümü belirtmek için uygun WS-Addressing ilke onaylamalarını dışa aktarma işlemesi gerekir kullanılan.</span><span class="sxs-lookup"><span data-stu-id="d5dff-153">Because custom transport binding elements are responsible for handling addressing, the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> implementation on the `UdpTransportBindingElement` must also handle exporting the appropriate WS-Addressing policy assertions to indicate the version of WS-Addressing being used.</span></span>  
  
```csharp  
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a><span data-ttu-id="d5dff-154">İlke içeri aktarma</span><span class="sxs-lookup"><span data-stu-id="d5dff-154">Policy Import</span></span>  
 <span data-ttu-id="d5dff-155">İlke içeri aktarma sistemini genişletmek için aşağıdaki yapılandırma yapılandırma dosyasına için Svcutil.exe Svcutil.exe.config dosyasında gösterildiği gibi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d5dff-155">To extend the policy import system, add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file:</span></span>  
  
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
  
 <span data-ttu-id="d5dff-156">Biz uygulamak sonra <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> bizim kayıtlı sınıfından (`UdpBindingElementImporter`).</span><span class="sxs-lookup"><span data-stu-id="d5dff-156">Then we implement <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> from our registered class (`UdpBindingElementImporter`).</span></span> <span data-ttu-id="d5dff-157">İçinde <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, uygun ad alanındaki bir onayları incelemek ve işlemek olanları taşıma oluşturma ve çok noktaya yayın olup olmadığı denetleniyor.</span><span class="sxs-lookup"><span data-stu-id="d5dff-157">In <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, examine the assertions in the appropriate namespace and process the ones for generating the transport and checking if it is multicast.</span></span> <span data-ttu-id="d5dff-158">Ayrıca, içeri Aktarıcı işleyen bir onayları onaylar bağlama listeden kaldırın.</span><span class="sxs-lookup"><span data-stu-id="d5dff-158">In addition, remove the assertions that the importer handles from the list of binding assertions.</span></span> <span data-ttu-id="d5dff-159">Yeniden Svcutil.exe çalıştırırken tümleştirme için iki seçenek vardır:</span><span class="sxs-lookup"><span data-stu-id="d5dff-159">Again, when running Svcutil.exe, there are two options for integration:</span></span>  
  
1.  <span data-ttu-id="d5dff-160">Noktası Svcutil.exe /SvcutilConfig kullanarak bizim yapılandırma dosyasına:\<Dosya >.</span><span class="sxs-lookup"><span data-stu-id="d5dff-160">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2.  <span data-ttu-id="d5dff-161">Yapılandırma bölümü Svcutil.exe.config için Svcutil.exe ile aynı dizinde ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d5dff-161">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
### <a name="adding-a-custom-standard-binding-importer"></a><span data-ttu-id="d5dff-162">Özel standart içeri Aktarıcı bağlama ekleme</span><span class="sxs-lookup"><span data-stu-id="d5dff-162">Adding a Custom Standard Binding Importer</span></span>  
 <span data-ttu-id="d5dff-163">Svcutil.exe ve <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> türü varsayılan olarak tanıyacak ve sistem tarafından sağlanan bağlamalar içeri aktarın.</span><span class="sxs-lookup"><span data-stu-id="d5dff-163">Svcutil.exe and the <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> type, by default, recognize and import system-provided bindings.</span></span> <span data-ttu-id="d5dff-164">Aksi takdirde, bağlama olarak içeri aktarılan alır bir <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> örneği.</span><span class="sxs-lookup"><span data-stu-id="d5dff-164">Otherwise, the binding gets imported as a <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="d5dff-165">Svcutil.exe sağlamak ve <xref:System.ServiceModel.Description.WsdlImporter> içeri aktarmak için `SampleProfileUdpBinding` `UdpBindingElementImporter` da bir standart özel bağlama alıcısı davranır.</span><span class="sxs-lookup"><span data-stu-id="d5dff-165">To enable Svcutil.exe and the <xref:System.ServiceModel.Description.WsdlImporter> to import the `SampleProfileUdpBinding` the `UdpBindingElementImporter` also acts as a custom standard binding importer.</span></span>  
  
 <span data-ttu-id="d5dff-166">Standart özel bağlama içeri Aktarıcı uygulayan `ImportEndpoint` yöntemi <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> incelemek için arabirimi <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> , belirli bir standart bağlama tarafından oluşturulmuş, görmek için meta verileri içeri aktarılan örnek.</span><span class="sxs-lookup"><span data-stu-id="d5dff-166">A custom standard binding importer implements the `ImportEndpoint` method on the <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface to examine the <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance imported from metadata to see if it could have been generated by specific standard binding.</span></span>  
  
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
  
 <span data-ttu-id="d5dff-167">Genellikle, bir özel standart bağlama içeri Aktarıcı uygulama standart bağlama tarafından ayarlanmış olabilir yalnızca özellikleri değiştirildi ve diğer tüm özellikler varsayılan olduğunu doğrulamak için içeri aktarılan bağlama öğeleri özelliklerini denetleme içerir.</span><span class="sxs-lookup"><span data-stu-id="d5dff-167">Generally, implementing a custom standard binding importer involves checking the properties of the imported binding elements to verify that only properties that could have been set by the standard binding have changed and all other properties are their defaults.</span></span> <span data-ttu-id="d5dff-168">Standart bağlama içeri Aktarıcı uygulamak için temel bir strateji olan standart bağlama öğesinin bir örneğini oluşturur, standart bağlamayı destekleyen standart bağlama örneği ve karşılaştırma bağlama öğeleri özelliklerinden bağlama yayma içeri aktarılan bağlama öğeleri standart bağlama öğeleri.</span><span class="sxs-lookup"><span data-stu-id="d5dff-168">A basic strategy for implementing a standard binding importer is to create an instance of the standard binding, propagate the properties from the binding elements to the standard binding instance that the standard binding supports, and the compare the binding elements from the standard binding with the imported binding elements.</span></span>
