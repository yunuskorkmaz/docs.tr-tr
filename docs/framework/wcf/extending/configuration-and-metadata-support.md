---
title: Yapılandırma ve Meta Veri Desteği
ms.date: 03/30/2017
ms.assetid: 27c240cb-8cab-472c-87f8-c864f4978758
ms.openlocfilehash: 4dfeeba6db220e03ad981b13e2bb093bedcd43c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486730"
---
# <a name="configuration-and-metadata-support"></a><span data-ttu-id="26b33-102">Yapılandırma ve Meta Veri Desteği</span><span class="sxs-lookup"><span data-stu-id="26b33-102">Configuration and Metadata Support</span></span>
<span data-ttu-id="26b33-103">Bu konu, bağlamalar ve bağlama öğeleri yapılandırma ve meta veri desteğini etkinleştirmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="26b33-103">This topic describes how to enable configuration and metadata support for bindings and binding elements.</span></span>  
  
## <a name="overview-of-configuration-and-metadata"></a><span data-ttu-id="26b33-104">Yapılandırma ve meta veri genel bakış</span><span class="sxs-lookup"><span data-stu-id="26b33-104">Overview of Configuration and Metadata</span></span>  
 <span data-ttu-id="26b33-105">Bu konuda 1, 2 ve 4 isteğe bağlı öğeleri aşağıdaki görevler ele alınmıştır içinde [geliştirme kanalları](../../../../docs/framework/wcf/extending/developing-channels.md) görev listesi.</span><span class="sxs-lookup"><span data-stu-id="26b33-105">This topic discusses the following tasks, which are optional items 1, 2, and 4 in the [Developing Channels](../../../../docs/framework/wcf/extending/developing-channels.md) task list.</span></span>  
  
-   <span data-ttu-id="26b33-106">Yapılandırma dosyası bir bağlama öğesi desteğini etkinleştirme.</span><span class="sxs-lookup"><span data-stu-id="26b33-106">Enabling configuration file support for a binding element.</span></span>  
  
-   <span data-ttu-id="26b33-107">Yapılandırma dosyası bir bağlama desteğini etkinleştirme.</span><span class="sxs-lookup"><span data-stu-id="26b33-107">Enabling configuration file support for a binding.</span></span>  
  
-   <span data-ttu-id="26b33-108">Bir bağlama öğesi için WSDL ve ilke onaylamalarını dışa aktarma.</span><span class="sxs-lookup"><span data-stu-id="26b33-108">Exporting WSDL and policy assertions for a binding element.</span></span>  
  
-   <span data-ttu-id="26b33-109">WSDL ve ilke onaylamalarını eklemek ve bağlama veya bağlama öğesi yapılandırmak için tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="26b33-109">Identifying WSDL and policy assertions to insert and configure your binding or binding element.</span></span>  
  
 <span data-ttu-id="26b33-110">Kullanıcı tanımlı bağlamalar ve bağlama öğeleri oluşturma hakkında daha fazla bilgi için bkz: [Creating User-Defined bağlamaları](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md) ve [BindingElement oluşturma](../../../../docs/framework/wcf/extending/creating-a-bindingelement.md)sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="26b33-110">For information about creating user-defined bindings and binding elements, see [Creating User-Defined Bindings](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md) and [Creating a BindingElement](../../../../docs/framework/wcf/extending/creating-a-bindingelement.md), respectively.</span></span>  
  
## <a name="adding-configuration-support"></a><span data-ttu-id="26b33-111">Yapılandırma desteği ekleme</span><span class="sxs-lookup"><span data-stu-id="26b33-111">Adding Configuration Support</span></span>  
 <span data-ttu-id="26b33-112">Yapılandırma dosyası bir kanal desteğini etkinleştirmek için iki yapılandırma bölümlerinin uygulamalıdır <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>, bağlama öğeleri, yapılandırma desteği sağlar ve <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> ve <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>, yapılandırma desteğini etkinleştir bağlamaları.</span><span class="sxs-lookup"><span data-stu-id="26b33-112">To enable configuration file support for a channel, you must implement two configuration sections, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>, which enables configuration support for binding elements, and the <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> and <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>, which enable configuration support for bindings.</span></span>  
  
 <span data-ttu-id="26b33-113">Bunu yapmak için daha kolay bir yolu kullanmaktır [ConfigurationCodeGenerator](../../../../docs/framework/wcf/samples/configurationcodegenerator.md) bağlamalar ve bağlama öğeleri yapılandırma kodunu oluşturmak için örnek araç.</span><span class="sxs-lookup"><span data-stu-id="26b33-113">An easier way to do this is to use the [ConfigurationCodeGenerator](../../../../docs/framework/wcf/samples/configurationcodegenerator.md) sample tool to generate configuration code for your bindings and binding elements.</span></span>  
  
### <a name="extending-bindingelementextensionelement"></a><span data-ttu-id="26b33-114">BindingElementExtensionElement genişletme</span><span class="sxs-lookup"><span data-stu-id="26b33-114">Extending BindingElementExtensionElement</span></span>  
 <span data-ttu-id="26b33-115">Aşağıdaki kod örneği alınırlar [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="26b33-115">The following example code is taken from the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span> <span data-ttu-id="26b33-116">`UdpTransportElement` Olan bir <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> kullanıma sunan `UdpTransportBindingElement` yapılandırma sistemi.</span><span class="sxs-lookup"><span data-stu-id="26b33-116">The `UdpTransportElement` is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> that exposes `UdpTransportBindingElement` to the configuration system.</span></span> <span data-ttu-id="26b33-117">Birkaç temel geçersiz kılmalar, örnek yapılandırma bölümü adı, bağlama öğesi türü ve bağlama öğesi oluşturmak nasıl tanımlar.</span><span class="sxs-lookup"><span data-stu-id="26b33-117">With a few basic overrides, the sample defines the configuration section name, the type of the binding element and how to create the binding element.</span></span> <span data-ttu-id="26b33-118">Kullanıcılar daha sonra uzantısı bölümüne bir yapılandırma dosyasında şu şekilde kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26b33-118">Users can then register the extension section in a configuration file as follows.</span></span>  
  
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
  
 <span data-ttu-id="26b33-119">Uzantı UDP taşıma olarak kullanmak için özel bağlamalar başvurulabilir.</span><span class="sxs-lookup"><span data-stu-id="26b33-119">The extension can be referenced from custom bindings to use UDP as the transport.</span></span>  
  
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
  
### <a name="adding-configuration-for-a-binding"></a><span data-ttu-id="26b33-120">Bir bağlama için yapılandırması ekleniyor</span><span class="sxs-lookup"><span data-stu-id="26b33-120">Adding Configuration for a Binding</span></span>  
 <span data-ttu-id="26b33-121">Bölüm `SampleProfileUdpBindingCollectionElement` olan bir <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> kullanıma sunan `SampleProfileUdpBinding` yapılandırma sistemi.</span><span class="sxs-lookup"><span data-stu-id="26b33-121">The section `SampleProfileUdpBindingCollectionElement` is a <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> that exposes `SampleProfileUdpBinding` to the configuration system.</span></span> <span data-ttu-id="26b33-122">Uygulama toplu temsilci için `SampleProfileUdpBindingConfigurationElement`, den türetilen <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="26b33-122">The bulk of the implementation is delegated to the `SampleProfileUdpBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="26b33-123">`SampleProfileUdpBindingConfigurationElement` Özellikler üzerinde karşılık gelen özelliklere sahip `SampleProfileUdpBinding`ve eşlenecek işlevleri `ConfigurationElement` bağlama.</span><span class="sxs-lookup"><span data-stu-id="26b33-123">The `SampleProfileUdpBindingConfigurationElement` has properties that correspond to the properties on `SampleProfileUdpBinding`, and functions to map from the `ConfigurationElement` binding.</span></span> <span data-ttu-id="26b33-124">Son olarak, `OnApplyConfiguration` yöntemi geçersiz kılınmıştır `SampleProfileUdpBinding`, aşağıdaki örnek kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="26b33-124">Finally, the `OnApplyConfiguration` method is overridden in the `SampleProfileUdpBinding`, as shown in the following sample code.</span></span>  
  
```  
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
  
 <span data-ttu-id="26b33-125">Bu işleyici yapılandırma sistemi ile kaydetmek için aşağıdaki bölümde ilgili yapılandırma dosyasına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="26b33-125">To register this handler with the configuration system, add the following section to the relevant configuration file.</span></span>  
  
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
  
 <span data-ttu-id="26b33-126">Öğesinden sonra başvurulabilir [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="26b33-126">It can then be referenced from the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) configuration section.</span></span>  
  
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
  
## <a name="adding-metadata-support-for-a-binding-element"></a><span data-ttu-id="26b33-127">Bir bağlama öğesi için meta verileri desteği ekleme</span><span class="sxs-lookup"><span data-stu-id="26b33-127">Adding Metadata Support for a Binding Element</span></span>  
 <span data-ttu-id="26b33-128">Bir kanal meta verileri sistemle tümleştirmek için içeri ve dışarı aktarma İlkesi desteklemelidir.</span><span class="sxs-lookup"><span data-stu-id="26b33-128">To integrate a channel into the metadata system, it must support both the import and export of policy.</span></span> <span data-ttu-id="26b33-129">Bu gibi araçlar sağlar [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) bağlama öğesi istemcileri oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="26b33-129">This allows tools such as [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate clients of the binding element.</span></span>  
  
### <a name="adding-wsdl-support"></a><span data-ttu-id="26b33-130">WSDL desteği ekleme</span><span class="sxs-lookup"><span data-stu-id="26b33-130">Adding WSDL Support</span></span>  
 <span data-ttu-id="26b33-131">Bir bağlama aktarım bağlama öğe meta verileri adresleme bilgilerini alma ve verme sorumludur.</span><span class="sxs-lookup"><span data-stu-id="26b33-131">The transport binding element in a binding is responsible for exporting and importing addressing information in metadata.</span></span> <span data-ttu-id="26b33-132">SOAP bağlama kullanırken, aktarım bağlama öğesi de meta verilerde doğru taşıma URI dışarı aktarmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="26b33-132">When using a SOAP binding, the transport binding element should also export a correct transport URI in metadata.</span></span> <span data-ttu-id="26b33-133">Aşağıdaki kod örneği alınırlar [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="26b33-133">The following example code is taken from the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
#### <a name="wsdl-export"></a><span data-ttu-id="26b33-134">WSDL dışarı aktarma</span><span class="sxs-lookup"><span data-stu-id="26b33-134">WSDL Export</span></span>  
 <span data-ttu-id="26b33-135">Adresleme bilgilerini dışarı aktarmak için `UdpTransportBindingElement` uygulayan <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="26b33-135">To export addressing information, the `UdpTransportBindingElement` implements the <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="26b33-136"><xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> Yöntemi WSDL bağlantı noktasına doğru adresleme bilgilerini ekler.</span><span class="sxs-lookup"><span data-stu-id="26b33-136">The <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> method adds the correct addressing information to the WSDL port.</span></span>  
  
```  
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 <span data-ttu-id="26b33-137">`UdpTransportBindingElement` Uyarlamasını <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> yöntemi uç nokta bir SOAP bağlama kullandığında taşıma URI ayrıca verir:</span><span class="sxs-lookup"><span data-stu-id="26b33-137">The `UdpTransportBindingElement` implementation of the <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> method also exports a transport URI when the endpoint uses a SOAP binding:</span></span>  
  
```  
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a><span data-ttu-id="26b33-138">WSDL içe aktarma</span><span class="sxs-lookup"><span data-stu-id="26b33-138">WSDL Import</span></span>  
 <span data-ttu-id="26b33-139">Adres alma işlemek için WSDL içe aktarma sistemini genişletmek için aşağıdaki yapılandırma Svcutil.exe.config dosyasında gösterildiği gibi Svcutil.exe için yapılandırma dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="26b33-139">To extend the WSDL import system to handle importing the addresses, add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file:</span></span>  
  
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
  
 <span data-ttu-id="26b33-140">Svcutil.exe çalıştırırken WSDL içe aktarma Uzantıları'nı yüklemek için Svcutil.exe alma için iki seçeneğiniz vardır:</span><span class="sxs-lookup"><span data-stu-id="26b33-140">When running Svcutil.exe, there are two options for getting Svcutil.exe to load the WSDL import extensions:</span></span>  
  
1.  <span data-ttu-id="26b33-141">/SvcutilConfig kullanarak yapılandırma dosyasının noktası Svcutil.exe:\<Dosya >.</span><span class="sxs-lookup"><span data-stu-id="26b33-141">Point Svcutil.exe to the configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2.  <span data-ttu-id="26b33-142">Yapılandırma bölümü için Svcutil.exe.config Svcutil.exe ile aynı dizinde ekleyin.</span><span class="sxs-lookup"><span data-stu-id="26b33-142">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
 <span data-ttu-id="26b33-143">`UdpBindingElementImporter` Yazın uygulayan <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="26b33-143">The `UdpBindingElementImporter` type implements the <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="26b33-144">`ImportEndpoint` Yöntemi WSDL bağlantı noktasından adresi alır:</span><span class="sxs-lookup"><span data-stu-id="26b33-144">The `ImportEndpoint` method imports the address from the WSDL port:</span></span>  
  
```  
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a><span data-ttu-id="26b33-145">İlke desteği ekleme</span><span class="sxs-lookup"><span data-stu-id="26b33-145">Adding Policy Support</span></span>  
 <span data-ttu-id="26b33-146">Özel bağlama öğesi bu bağlama öğesi özelliklerini ifade etmek için bir hizmet uç noktası için WSDL bağlama ilke onaylamalarını dışa aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26b33-146">The custom binding element can export policy assertions in the WSDL binding for a service endpoint to express the capabilities of that binding element.</span></span> <span data-ttu-id="26b33-147">Aşağıdaki kod örneği alınırlar [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="26b33-147">The following example code is taken from the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
#### <a name="policy-export"></a><span data-ttu-id="26b33-148">İlke verme</span><span class="sxs-lookup"><span data-stu-id="26b33-148">Policy Export</span></span>  
 <span data-ttu-id="26b33-149">`UdpTransportBindingElement` Yazın Implements''<xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> İlkesi dışarı aktarma desteği eklemek için.</span><span class="sxs-lookup"><span data-stu-id="26b33-149">The `UdpTransportBindingElement` type implements``<xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> to add support for exporting policy.</span></span> <span data-ttu-id="26b33-150">Sonuç olarak, <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> içeren `UdpTransportBindingElement` içerdiği bağlama için ilke oluşturma.</span><span class="sxs-lookup"><span data-stu-id="26b33-150">As a result, <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> includes `UdpTransportBindingElement` in the generation of policy for any binding that includes it.</span></span>  
  
 <span data-ttu-id="26b33-151">İçinde <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>, kanal çok noktaya yayın modunda ise bir onaylama UDP ve başka bir onaylama için ekleyin.</span><span class="sxs-lookup"><span data-stu-id="26b33-151">In <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>, add an assertion for UDP and another assertion if the channel is in multicast mode.</span></span> <span data-ttu-id="26b33-152">Çok noktaya yayın modu etkilediğinden nasıl iletişim yığını oluşturulur ve böylece her iki yüz arasındaki Eşgüdümlü olmalıdır budur.</span><span class="sxs-lookup"><span data-stu-id="26b33-152">This is because multicast mode affects how the communication stack is constructed, and thus must be coordinated between both sides.</span></span>  
  
```  
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
  
 <span data-ttu-id="26b33-153">Özel Aktarım bağlama öğeleriyle adresleme, işleme için sorumlu olduğu için <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> mantığınız `UdpTransportBindingElement` WS adresleme sürümünü belirtmek için uygun WS adresleme ilke onaylamalarını dışa aktarma işlemesi gerekir kullanılan.</span><span class="sxs-lookup"><span data-stu-id="26b33-153">Because custom transport binding elements are responsible for handling addressing, the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> implementation on the `UdpTransportBindingElement` must also handle exporting the appropriate WS-Addressing policy assertions to indicate the version of WS-Addressing being used.</span></span>  
  
```  
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a><span data-ttu-id="26b33-154">İlke içeri aktarma</span><span class="sxs-lookup"><span data-stu-id="26b33-154">Policy Import</span></span>  
 <span data-ttu-id="26b33-155">İlke içeri aktarma sistemini genişletmek için aşağıdaki yapılandırma yapılandırma dosyasına için Svcutil.exe Svcutil.exe.config dosyasında gösterildiği gibi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="26b33-155">To extend the policy import system, add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file:</span></span>  
  
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
  
 <span data-ttu-id="26b33-156">Biz uygulamak sonra <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> bizim kayıtlı sınıfından (`UdpBindingElementImporter`).</span><span class="sxs-lookup"><span data-stu-id="26b33-156">Then we implement <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> from our registered class (`UdpBindingElementImporter`).</span></span> <span data-ttu-id="26b33-157">İçinde <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, uygun ad alanında onaylar inceleyin ve taşıma oluşturma ve çok noktaya yayın olup olmadığını denetlemek için kullanabileceğiniz olanları işlem.</span><span class="sxs-lookup"><span data-stu-id="26b33-157">In <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, examine the assertions in the appropriate namespace and process the ones for generating the transport and checking if it is multicast.</span></span> <span data-ttu-id="26b33-158">Ayrıca, alıcı işleme onaylar onaylar bağlama listesinden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="26b33-158">In addition, remove the assertions that the importer handles from the list of binding assertions.</span></span> <span data-ttu-id="26b33-159">Yeniden Svcutil.exe çalıştırırken, tümleştirme için iki seçenek vardır:</span><span class="sxs-lookup"><span data-stu-id="26b33-159">Again, when running Svcutil.exe, there are two options for integration:</span></span>  
  
1.  <span data-ttu-id="26b33-160">/SvcutilConfig kullanarak bizim yapılandırma dosyasına noktası Svcutil.exe:\<Dosya >.</span><span class="sxs-lookup"><span data-stu-id="26b33-160">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2.  <span data-ttu-id="26b33-161">Yapılandırma bölümü için Svcutil.exe.config Svcutil.exe ile aynı dizinde ekleyin.</span><span class="sxs-lookup"><span data-stu-id="26b33-161">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
### <a name="adding-a-custom-standard-binding-importer"></a><span data-ttu-id="26b33-162">İçeri Aktarıcı bağlama özel bir standart ekleme</span><span class="sxs-lookup"><span data-stu-id="26b33-162">Adding a Custom Standard Binding Importer</span></span>  
 <span data-ttu-id="26b33-163">Svcutil.exe ve <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> türü, varsayılan olarak algılar ve sistem tarafından sağlanan bağlamalar içeri aktarın.</span><span class="sxs-lookup"><span data-stu-id="26b33-163">Svcutil.exe and the <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> type, by default, recognize and import system-provided bindings.</span></span> <span data-ttu-id="26b33-164">Aksi takdirde, bağlama içeri alır bir <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> örneği.</span><span class="sxs-lookup"><span data-stu-id="26b33-164">Otherwise, the binding gets imported as a <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="26b33-165">Svcutil.exe etkinleştirmek için ve <xref:System.ServiceModel.Description.WsdlImporter> almak için `SampleProfileUdpBinding` `UdpBindingElementImporter` da özel standart bağlama alıcısı davranır.</span><span class="sxs-lookup"><span data-stu-id="26b33-165">To enable Svcutil.exe and the <xref:System.ServiceModel.Description.WsdlImporter> to import the `SampleProfileUdpBinding` the `UdpBindingElementImporter` also acts as a custom standard binding importer.</span></span>  
  
 <span data-ttu-id="26b33-166">Özel standart bağlama alma uygulayan `ImportEndpoint` yöntemi <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> incelemek için arabirimi <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> , belirli standart bağlama tarafından oluşturulmuş, görmek için meta verileri içe örneği.</span><span class="sxs-lookup"><span data-stu-id="26b33-166">A custom standard binding importer implements the `ImportEndpoint` method on the <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface to examine the <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance imported from metadata to see if it could have been generated by specific standard binding.</span></span>  
  
```  
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
  
 <span data-ttu-id="26b33-167">Genellikle, özel standart bağlama alma uygulama standart bağlama tarafından ayarlayabilirsiniz yalnızca özellikleri değişti ve diğer tüm özellikleri varsayılanlarına olduğunu doğrulamak için içe aktarılan bağlama öğeleri özelliklerini denetleme içerir.</span><span class="sxs-lookup"><span data-stu-id="26b33-167">Generally, implementing a custom standard binding importer involves checking the properties of the imported binding elements to verify that only properties that could have been set by the standard binding have changed and all other properties are their defaults.</span></span> <span data-ttu-id="26b33-168">Standart bağlama alma uygulamak için bir temel stratejidir standart bağlama örneği oluşturmak için bağlama öğeleri özelliklerinden standart bağlama destekler standart bağlama örneği ve karşılaştırmak için bağlama yayma içeri aktarılan bağlama öğeleri ile standart bağlama öğeleri.</span><span class="sxs-lookup"><span data-stu-id="26b33-168">A basic strategy for implementing a standard binding importer is to create an instance of the standard binding, propagate the properties from the binding elements to the standard binding instance that the standard binding supports, and the compare the binding elements from the standard binding with the imported binding elements.</span></span>
