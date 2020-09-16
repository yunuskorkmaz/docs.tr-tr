---
title: Güvenlik Doğrulaması
ms.date: 03/30/2017
ms.assetid: 48dcd496-0c4f-48ce-8b9b-0e25b77ffa58
ms.openlocfilehash: ec7b7f96c1f6489f677970164f74c176b301f55b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557391"
---
# <a name="security-validation"></a><span data-ttu-id="b9741-102">Güvenlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="b9741-102">Security validation</span></span>
<span data-ttu-id="b9741-103">Bu örnek, belirli ölçütlere uyması için bir bilgisayardaki hizmetleri doğrulamak üzere özel bir davranışın nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b9741-103">This sample demonstrates how to use a custom behavior to validate services on a computer to ensure they meet specific criteria.</span></span> <span data-ttu-id="b9741-104">Bu örnekte, hizmetler, hizmet üzerindeki her bir uç nokta arasında tarama yaparak ve güvenli bağlama öğeleri içerip içermediğini kontrol ederek özel davranış tarafından onaylanır.</span><span class="sxs-lookup"><span data-stu-id="b9741-104">In this sample, services are validated by the custom behavior by scanning through each endpoint on the service and checking to see whether they contain secure binding elements.</span></span> <span data-ttu-id="b9741-105">Bu örnek, [Başlarken](getting-started-sample.md)' i temel alır.</span><span class="sxs-lookup"><span data-stu-id="b9741-105">This sample is based on the [Getting Started](getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b9741-106">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="b9741-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="endpoint-validation-custom-behavior"></a><span data-ttu-id="b9741-107">Uç nokta doğrulama özel davranışı</span><span class="sxs-lookup"><span data-stu-id="b9741-107">Endpoint Validation Custom Behavior</span></span>  
 <span data-ttu-id="b9741-108">Arabirimde bulunan yönteme Kullanıcı kodu ekleyerek `Validate` <xref:System.ServiceModel.Description.IServiceBehavior> , Kullanıcı tanımlı eylemler gerçekleştirmek için bir hizmete veya uç noktaya özel davranış verilebilir.</span><span class="sxs-lookup"><span data-stu-id="b9741-108">By adding user code to the `Validate` method contained in the <xref:System.ServiceModel.Description.IServiceBehavior> interface, custom behavior can be given to a service or endpoint to perform user-defined actions.</span></span> <span data-ttu-id="b9741-109">Aşağıdaki kod, bir hizmette yer alan her bir uç noktada, güvenli bağlamalar için bağlama koleksiyonlarında arama yapmak üzere kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b9741-109">The following code is used to loop through each endpoint contained in a service, which searches through their binding collections for secure bindings.</span></span>  
  
```csharp
public void Validate(ServiceDescription serviceDescription,
                                       ServiceHostBase serviceHostBase)  
{  
    // Loop through each endpoint individually, gathering their
    // binding elements.  
    foreach (ServiceEndpoint endpoint in serviceDescription.Endpoints)  
    {  
        secureElementFound = false;  
  
        // Retrieve the endpoint's binding element collection.  
        BindingElementCollection bindingElements =
            endpoint.Binding.CreateBindingElements();  
  
        // Look to see if the binding elements collection contains any
        // secure binding elements. Transport, Asymmetric, and Symmetric
        // binding elements are all derived from SecurityBindingElement.  
        if ((bindingElements.Find<SecurityBindingElement>() != null) || (bindingElements.Find<HttpsTransportBindingElement>() != null) || (bindingElements.Find<WindowsStreamSecurityBindingElement>() != null) || (bindingElements.Find<SslStreamSecurityBindingElement>() != null))  
        {  
            secureElementFound = true;  
        }  
  
    // Send a message to the system event viewer when an endpoint is deemed insecure.  
    if (!secureElementFound)  
        throw new Exception(System.DateTime.Now.ToString() + ": The endpoint \"" + endpoint.Name + "\" has no secure bindings.");  
    }  
}  
```  
  
 <span data-ttu-id="b9741-110">Aşağıdaki kodu Web.config dosyasına eklemek `serviceValidate` , hizmetin, tanıması için davranış uzantısını ekler.</span><span class="sxs-lookup"><span data-stu-id="b9741-110">Adding the following code to Web.config file adds the `serviceValidate` behavior extension for the service to recognize.</span></span>  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="endpointValidate" type="Microsoft.ServiceModel.Samples.EndpointValidateElement, endpointValidate, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
    </extensions>
    ...
</system.serviceModel>
```  
  
 <span data-ttu-id="b9741-111">Davranış uzantısı hizmete eklendikten sonra, bu `endpointValidate` davranış, Web.config dosyadaki davranışlar listesine ve bu nedenle hizmete eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="b9741-111">Once the behavior extension is added to the service, it is now possible to add the `endpointValidate` behavior to the list of behaviors in the Web.config file and thus, to the service.</span></span>  
  
```xml  
<behaviors>  
    <serviceBehaviors>  
        <behavior name="CalcServiceSEB1">  
            <serviceMetadata httpGetEnabled="true" />  
            <endpointValidate />  
        </behavior>  
    </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="b9741-112">Web.config dosyasına eklenen davranışlar ve uzantıları, her bir hizmete davranış uygular, Machine.config dosyasına eklendiğinde, bilgisayarda etkin olan her hizmete davranış uygular.</span><span class="sxs-lookup"><span data-stu-id="b9741-112">Behaviors and their extensions that are added to the Web.config file apply behavior to individual services, while when added to the Machine.config file apply behavior to every service active on the computer.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b9741-113">Tüm hizmetlere davranış eklerken, herhangi bir değişiklik yapmadan önce Machine.config dosyasını yedeklemeniz önerilir.</span><span class="sxs-lookup"><span data-stu-id="b9741-113">When adding behavior to all services, it is suggested to backup the Machine.config file before making any change.</span></span>  
  
 <span data-ttu-id="b9741-114">Şimdi bu örneğin client\bin dizininde belirtilen istemciyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b9741-114">Now run the client provided in the client\bin directory of this sample.</span></span> <span data-ttu-id="b9741-115">Şu iletiyle bir özel durum oluşturuldu: "istenen hizmet, ' http://localhost/servicemodelsamples/service.svc ' etkinleştirilemedi."</span><span class="sxs-lookup"><span data-stu-id="b9741-115">An exception is thrown with the following message: "The requested service, 'http://localhost/servicemodelsamples/service.svc' could not be activated."</span></span> <span data-ttu-id="b9741-116">Uç nokta doğrulama davranışının güvenli olmadığı kabul edildiği ve hizmetin başlatılmasını önleyen için bu durum beklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="b9741-116">This is expected because an endpoint is considered insecure by the endpoint validating behavior and prevents the service from being started.</span></span> <span data-ttu-id="b9741-117">Davranış ayrıca, hangi uç noktanın güvenli olmayan olduğunu ve "System. ServiceModel 4.0.0.0" kaynağı ve "WebHost" kategorisinin altına bir Olay Görüntüleyicisi ileti yazdığını belirten bir iç özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b9741-117">The behavior also throws an internal exception that describes which endpoint is insecure and writes a message to the system Event Viewer under the "System.ServiceModel 4.0.0.0" source and the "WebHost" category.</span></span> <span data-ttu-id="b9741-118">Bu örnekteki hizmette izlemeyi açmak de mümkündür.</span><span class="sxs-lookup"><span data-stu-id="b9741-118">It is also possible to turn on tracing on the service in this sample.</span></span> <span data-ttu-id="b9741-119">Bu, kullanıcının Endpoint doğrulama davranışı tarafından oluşturulan özel durumları, hizmet Izleme Görüntüleyicisi aracını kullanarak elde edilen hizmet izlemelerini açarak görüntülemesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b9741-119">This allows the user to view the exceptions thrown by endpoint validating behavior by opening the resulting service traces using the Service Trace Viewer tool.</span></span>  
  
### <a name="view-failed-endpoint-validation-exception-messages-in-the-event-viewer"></a><span data-ttu-id="b9741-120">Olay Görüntüleyicisi başarısız uç nokta doğrulama özel durum iletilerini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="b9741-120">View failed endpoint validation exception messages in the Event Viewer</span></span>  
  
1. <span data-ttu-id="b9741-121">**Başlat** menüsüne tıklayın ve **Çalıştır...** seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="b9741-121">Click the **Start** menu and select **Run…**.</span></span>  
  
2. <span data-ttu-id="b9741-122">Yazın `eventvwr` ve **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b9741-122">Type `eventvwr` and click **OK**.</span></span>  
  
3. <span data-ttu-id="b9741-123">Olay Görüntüleyicisi penceresinde **uygulama**' ya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b9741-123">In the Event Viewer window, click **Application**.</span></span>  
  
4. <span data-ttu-id="b9741-124">Güvenli olmayan uç nokta iletilerini görüntülemek için **uygulama** penceresindeki "Webhost" kategorisinin altındaki son eklenen "System. ServiceModel 4.0.0.0" olayına çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b9741-124">Double-click the recently added "System.ServiceModel 4.0.0.0" event under the "WebHost" category in the **Application** window to view insecure endpoint messages.</span></span>  
  
## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="b9741-125">Örneği kurma, oluşturma ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="b9741-125">Set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b9741-126">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="b9741-126">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="b9741-127">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="b9741-127">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="b9741-128">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="b9741-128">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b9741-129">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="b9741-129">The samples may already be installed on your computer.</span></span> <span data-ttu-id="b9741-130">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b9741-130">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="b9741-131">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b9741-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b9741-132">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="b9741-132">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ServiceValidation`  
  
## <a name="see-also"></a><span data-ttu-id="b9741-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b9741-133">See also</span></span>

- <span data-ttu-id="b9741-134">[AppFabric Izleme örnekleri](/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="b9741-134">[AppFabric Monitoring Samples](/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
