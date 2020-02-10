---
title: Güvenlik Doğrulaması
ms.date: 03/30/2017
ms.assetid: 48dcd496-0c4f-48ce-8b9b-0e25b77ffa58
ms.openlocfilehash: c47f8910076590dae1ee6aabbddcb072d76bfc27
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094936"
---
# <a name="security-validation"></a><span data-ttu-id="c9c2a-102">Güvenlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="c9c2a-102">Security Validation</span></span>
<span data-ttu-id="c9c2a-103">Bu örnek, belirli ölçütlere uyması için bir bilgisayardaki hizmetleri doğrulamak üzere özel bir davranışın nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c9c2a-103">This sample demonstrates how to use a custom behavior to validate services on a computer to ensure they meet specific criteria.</span></span> <span data-ttu-id="c9c2a-104">Bu örnekte, hizmetler, hizmet üzerindeki her bir uç nokta arasında tarama yaparak ve güvenli bağlama öğeleri içerip içermediğini kontrol ederek özel davranış tarafından onaylanır.</span><span class="sxs-lookup"><span data-stu-id="c9c2a-104">In this sample, services are validated by the custom behavior by scanning through each endpoint on the service and checking to see whether they contain secure binding elements.</span></span> <span data-ttu-id="c9c2a-105">Bu örnek, [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)' i temel alır.</span><span class="sxs-lookup"><span data-stu-id="c9c2a-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c9c2a-106">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="c9c2a-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="endpoint-validation-custom-behavior"></a><span data-ttu-id="c9c2a-107">Uç nokta doğrulama özel davranışı</span><span class="sxs-lookup"><span data-stu-id="c9c2a-107">Endpoint Validation Custom Behavior</span></span>  
 <span data-ttu-id="c9c2a-108"><xref:System.ServiceModel.Description.IServiceBehavior> arabirimindeki `Validate` yöntemine Kullanıcı kodu ekleyerek, Kullanıcı tanımlı eylemler gerçekleştirmek için bir hizmete veya uç noktaya özel davranış verilebilir.</span><span class="sxs-lookup"><span data-stu-id="c9c2a-108">By adding user code to the `Validate` method contained in the <xref:System.ServiceModel.Description.IServiceBehavior> interface, custom behavior can be given to a service or endpoint to perform user-defined actions.</span></span> <span data-ttu-id="c9c2a-109">Aşağıdaki kod, bir hizmette yer alan her bir uç noktada, güvenli bağlamalar için bağlama koleksiyonlarında arama yapmak üzere kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c9c2a-109">The following code is used to loop through each endpoint contained in a service, which searches through their binding collections for secure bindings.</span></span>  
  
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
  
 <span data-ttu-id="c9c2a-110">Aşağıdaki kodu Web. config dosyasına eklemek, hizmetin tanıması için `serviceValidate` davranış uzantısını ekler.</span><span class="sxs-lookup"><span data-stu-id="c9c2a-110">Adding the following code to Web.config file adds the `serviceValidate` behavior extension for the service to recognize.</span></span>  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="endpointValidate" type="Microsoft.ServiceModel.Samples.EndpointValidateElement, endpointValidate, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
    </extensions>  
...  
```  
  
 <span data-ttu-id="c9c2a-111">Davranış uzantısı hizmete eklendikten sonra, artık `endpointValidate` davranışını Web. config dosyasındaki davranışlar listesine ve dolayısıyla hizmete eklemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="c9c2a-111">Once the behavior extension is added to the service, it is now possible to add the `endpointValidate` behavior to the list of behaviors in the Web.config file and thus, to the service.</span></span>  
  
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
  
 <span data-ttu-id="c9c2a-112">Web. config dosyasına eklenen davranışlar ve uzantıları, her bir hizmete davranış uygular, ancak Machine. config dosyasına eklendiğinde, bilgisayarda etkin olan her hizmete davranış uygular.</span><span class="sxs-lookup"><span data-stu-id="c9c2a-112">Behaviors and their extensions that are added to the Web.config file apply behavior to individual services, while when added to the Machine.config file apply behavior to every service active on the computer.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c9c2a-113">Tüm hizmetlere davranış eklerken, herhangi bir değişiklik yapmadan önce Machine. config dosyasını yedeklemeniz önerilir.</span><span class="sxs-lookup"><span data-stu-id="c9c2a-113">When adding behavior to all services, it is suggested to backup the Machine.config file before making any change.</span></span>  
  
 <span data-ttu-id="c9c2a-114">Şimdi bu örneğin client\bin dizininde belirtilen istemciyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c9c2a-114">Now run the client provided in the client\bin directory of this sample.</span></span> <span data-ttu-id="c9c2a-115">Şu iletiyle bir özel durum oluştu: "istenen hizmet, 'http://localhost/servicemodelsamples/service.svc' etkinleştirilemedi."</span><span class="sxs-lookup"><span data-stu-id="c9c2a-115">An exception has occurs with the following message: "The requested service, 'http://localhost/servicemodelsamples/service.svc' could not be activated."</span></span> <span data-ttu-id="c9c2a-116">Uç nokta doğrulama davranışının güvenli olmadığı kabul edildiği ve hizmetin başlatılmasını önleyen için bu durum beklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="c9c2a-116">This is expected because an endpoint is considered insecure by the endpoint validating behavior and prevents the service from being started.</span></span> <span data-ttu-id="c9c2a-117">Davranış ayrıca, hangi uç noktanın güvenli olmayan olduğunu ve "System. ServiceModel 4.0.0.0" kaynağı ve "WebHost" kategorisinin altına bir Olay Görüntüleyicisi ileti yazdığını belirten bir iç özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c9c2a-117">The behavior also throws an internal exception that describes which endpoint is insecure and writes a message to the system Event Viewer under the "System.ServiceModel 4.0.0.0" source and the "WebHost" category.</span></span> <span data-ttu-id="c9c2a-118">Bu örnekteki hizmette izlemeyi açmak de mümkündür.</span><span class="sxs-lookup"><span data-stu-id="c9c2a-118">It is also possible to turn on tracing on the service in this sample.</span></span> <span data-ttu-id="c9c2a-119">Bu, kullanıcının Endpoint doğrulama davranışı tarafından oluşturulan özel durumları, hizmet Izleme Görüntüleyicisi aracını kullanarak elde edilen hizmet izlemelerini açarak görüntülemesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="c9c2a-119">This allows the user to view the exceptions thrown by endpoint validating behavior by opening the resulting service traces using the Service Trace Viewer tool.</span></span>  
  
#### <a name="to-view-failed-endpoint-validation-exception-messages-in-the-event-viewer"></a><span data-ttu-id="c9c2a-120">Olay Görüntüleyicisi başarısız uç nokta doğrulama özel durum iletilerini görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="c9c2a-120">To view failed endpoint validation exception messages in the Event Viewer</span></span>  
  
1. <span data-ttu-id="c9c2a-121">**Başlat** menüsüne tıklayın ve **Çalıştır...** seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="c9c2a-121">Click the **Start** menu and select **Run…**.</span></span>  
  
2. <span data-ttu-id="c9c2a-122">`eventvwr` yazın ve **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c9c2a-122">Type `eventvwr` and click **OK**.</span></span>  
  
3. <span data-ttu-id="c9c2a-123">Olay Görüntüleyicisi penceresinde **uygulama**' ya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c9c2a-123">In the Event Viewer window, click **Application**.</span></span>  
  
4. <span data-ttu-id="c9c2a-124">Güvenli olmayan uç nokta iletilerini görüntülemek için **uygulama** penceresindeki "Webhost" kategorisinin altındaki son eklenen "System. ServiceModel 4.0.0.0" olayına çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c9c2a-124">Double-click the recently added "System.ServiceModel 4.0.0.0" event under the "WebHost" category in the **Application** window to view insecure endpoint messages.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c9c2a-125">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="c9c2a-125">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c9c2a-126">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="c9c2a-126">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="c9c2a-127">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="c9c2a-127">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="c9c2a-128">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="c9c2a-128">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c9c2a-129">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="c9c2a-129">The samples may already be installed on your computer.</span></span> <span data-ttu-id="c9c2a-130">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="c9c2a-130">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="c9c2a-131">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="c9c2a-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c9c2a-132">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="c9c2a-132">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ServiceValidation`  
  
## <a name="see-also"></a><span data-ttu-id="c9c2a-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9c2a-133">See also</span></span>

- <span data-ttu-id="c9c2a-134">[AppFabric Izleme örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="c9c2a-134">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
