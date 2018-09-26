---
title: Güvenlik Doğrulaması
ms.date: 03/30/2017
ms.assetid: 48dcd496-0c4f-48ce-8b9b-0e25b77ffa58
author: BrucePerlerMS
ms.openlocfilehash: 4b80457fb551c2ee99f910710c5f30fa59c53a01
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47203430"
---
# <a name="security-validation"></a><span data-ttu-id="b8da9-102">Güvenlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="b8da9-102">Security Validation</span></span>
<span data-ttu-id="b8da9-103">Bu örnek, özel bir davranış Hizmetleri bunlar belirli ölçütlere uyan emin olmak için bir bilgisayar üzerinde doğrulamak için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b8da9-103">This sample demonstrates how to use a custom behavior to validate services on a computer to ensure they meet specific criteria.</span></span> <span data-ttu-id="b8da9-104">Bu örnekte, hizmetleri, hizmette her bir uç noktası aracılığıyla tarama ve güvenli bir bağlama öğeleri içeren denetleniyor özel davranış tarafından doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="b8da9-104">In this sample, services are validated by the custom behavior by scanning through each endpoint on the service and checking to see whether they contain secure binding elements.</span></span> <span data-ttu-id="b8da9-105">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="b8da9-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8da9-106">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="b8da9-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="endpoint-validation-custom-behavior"></a><span data-ttu-id="b8da9-107">Uç nokta doğrulama özel davranışı</span><span class="sxs-lookup"><span data-stu-id="b8da9-107">Endpoint Validation Custom Behavior</span></span>  
 <span data-ttu-id="b8da9-108">Kullanıcı kodu ekleyerek `Validate` bulunan yöntemi <xref:System.ServiceModel.Description.IServiceBehavior> arabirimi, özel davranış verilebilir bir hizmet ya da uç noktası için kullanıcı tanımlı eylemleri gerçekleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="b8da9-108">By adding user code to the `Validate` method contained in the <xref:System.ServiceModel.Description.IServiceBehavior> interface, custom behavior can be given to a service or endpoint to perform user-defined actions.</span></span> <span data-ttu-id="b8da9-109">Aşağıdaki kod, bunların güvenli bağlamaları için bağlama koleksiyonları arar bir hizmette yer alan her bir uç nokta döngü için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b8da9-109">The following code is used to loop through each endpoint contained in a service, which searches through their binding collections for secure bindings.</span></span>  
  
```  
public void Validate(ServiceDescription serviceDescription,   
                                       ServiceHostBase serviceHostBase)  
{  
    // Loop through each endpoint individually gathering their    
       binding elements.  
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
  
 <span data-ttu-id="b8da9-110">Web.config dosyasına aşağıdaki kodu ekleyerek ekler `serviceValidate` hizmeti tanımak davranış uzantısı.</span><span class="sxs-lookup"><span data-stu-id="b8da9-110">Adding the following code to Web.config file adds the `serviceValidate` behavior extension for the service to recognize.</span></span>  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="endpointValidate" type="Microsoft.ServiceModel.Samples.EndpointValidateElement, endpointValidate, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
    </extensions>  
...  
```  
  
 <span data-ttu-id="b8da9-111">Davranış uzantısı hizmete eklendikten sonra artık eklemek mümkündür `endpointValidate` Web.config dosyasında davranışları listesi ve bu nedenle, hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="b8da9-111">Once the behavior extension is added to the service, it is now possible to add the `endpointValidate` behavior to the list of behaviors in the Web.config file and thus, to the service.</span></span>  
  
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
  
 <span data-ttu-id="b8da9-112">Davranışları ve Web.config dosyasına eklenen uzantılarını ayrı ayrı hizmetlere davranışı uygulamak Machine.config dosyasına eklediğinizde while bilgisayarda etkin olan her bir hizmet davranışı uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b8da9-112">Behaviors and their extensions that are added to the Web.config file apply behavior to individual services, while when added to the Machine.config file apply behavior to every service active on the computer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8da9-113">Davranış tüm hizmetlere eklerken, herhangi bir değişiklik yapmadan önce Machine.config dosyasına yedeklemek için önerilir.</span><span class="sxs-lookup"><span data-stu-id="b8da9-113">When adding behavior to all services, it is suggested to backup the Machine.config file before making any change.</span></span>  
  
 <span data-ttu-id="b8da9-114">Şimdi bu örnek client\bin dizininde sağlanan istemci çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b8da9-114">Now run the client provided in the client\bin directory of this sample.</span></span> <span data-ttu-id="b8da9-115">Bir özel durum olan şu ileti ile oluşur: "istenen hizmeti 'http://localhost/servicemodelsamples/service.svc' etkinleştirilemedi."</span><span class="sxs-lookup"><span data-stu-id="b8da9-115">An exception has occurs with the following message: "The requested service, 'http://localhost/servicemodelsamples/service.svc' could not be activated."</span></span> <span data-ttu-id="b8da9-116">Bu, bir uç nokta davranışı doğrulama uç noktası tarafından güvenli olduğu kabul edildiği için beklenen ve hizmetin başlatılmasını önler.</span><span class="sxs-lookup"><span data-stu-id="b8da9-116">This is expected because an endpoint is considered insecure by the endpoint validating behavior and prevents the service from being started.</span></span> <span data-ttu-id="b8da9-117">Davranışı, ayrıca hangi uç nokta çalınabildiği için güvenli değildir ve "System.ServiceModel 4.0.0.0" kaynağı ve "WebHost" kategorisi altındaki Olay Görüntüleyicisi'ni sistem için bir ileti yazar açıklayan bir iç özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b8da9-117">The behavior also throws an internal exception that describes which endpoint is insecure and writes a message to the system Event Viewer under the "System.ServiceModel 4.0.0.0" source and the "WebHost" category.</span></span> <span data-ttu-id="b8da9-118">Bu örnekte service izlemeyi etkinleştirmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="b8da9-118">It is also possible to turn on tracing on the service in this sample.</span></span> <span data-ttu-id="b8da9-119">Bu hizmet izleme Görüntüleyicisi aracı kullanılarak elde edilen hizmet izlemeleri açarak doğrulama uç nokta davranışı tarafından oluşturulan özel durumları görüntülemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8da9-119">This allows the user to view the exceptions thrown by endpoint validating behavior by opening the resulting service traces using the Service Trace Viewer tool.</span></span>  
  
#### <a name="to-view-failed-endpoint-validation-exception-messages-in-the-event-viewer"></a><span data-ttu-id="b8da9-120">Uç nokta doğrulama özel durum iletilerinin Olay Görüntüleyicisi'nde görüntülemek için başarısız oldu</span><span class="sxs-lookup"><span data-stu-id="b8da9-120">To view failed endpoint validation exception messages in the Event Viewer</span></span>  
  
1.  <span data-ttu-id="b8da9-121">Tıklayın **Başlat** menü ve select **Çalıştır...** .</span><span class="sxs-lookup"><span data-stu-id="b8da9-121">Click the **Start** menu and select **Run…**.</span></span>  
  
2.  <span data-ttu-id="b8da9-122">Tür `eventvwr` tıklatıp **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="b8da9-122">Type `eventvwr` and click **OK**.</span></span>  
  
3.  <span data-ttu-id="b8da9-123">Olay Görüntüleyicisi'ni pencerede **uygulama**.</span><span class="sxs-lookup"><span data-stu-id="b8da9-123">In the Event Viewer window, click **Application**.</span></span>  
  
4.  <span data-ttu-id="b8da9-124">Son eklenen "System.ServiceModel 4.0.0.0" olay "WebHost" kategorisi altında çift **uygulama** güvenli bir uç nokta iletilerini görüntülemek için penceresi.</span><span class="sxs-lookup"><span data-stu-id="b8da9-124">Double-click the recently added "System.ServiceModel 4.0.0.0" event under the "WebHost" category in the **Application** window to view insecure endpoint messages.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b8da9-125">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="b8da9-125">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b8da9-126">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b8da9-126">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="b8da9-127">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b8da9-127">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="b8da9-128">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b8da9-128">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b8da9-129">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="b8da9-129">The samples may already be installed on your computer.</span></span> <span data-ttu-id="b8da9-130">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b8da9-130">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b8da9-131">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="b8da9-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b8da9-132">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="b8da9-132">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ServiceValidation`  
  
## <a name="see-also"></a><span data-ttu-id="b8da9-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b8da9-133">See Also</span></span>  
 [<span data-ttu-id="b8da9-134">AppFabric izleme örnekleri</span><span class="sxs-lookup"><span data-stu-id="b8da9-134">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
