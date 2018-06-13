---
title: Güvenlik Doğrulaması
ms.date: 03/30/2017
ms.assetid: 48dcd496-0c4f-48ce-8b9b-0e25b77ffa58
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: f77b01633f214d3a8c4ad8d7226375c3ed2368fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33504390"
---
# <a name="security-validation"></a><span data-ttu-id="cb991-102">Güvenlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="cb991-102">Security Validation</span></span>
<span data-ttu-id="cb991-103">Bu örnek özel bir davranış Hizmetleri belirli ölçütlere uyan emin olmak için bir bilgisayar üzerinde doğrulamak için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cb991-103">This sample demonstrates how to use a custom behavior to validate services on a computer to ensure they meet specific criteria.</span></span> <span data-ttu-id="cb991-104">Bu örnekte, Hizmetleri hizmetinin her uç nokta aracılığıyla tarama ve güvenli bağlama öğelerini içeren denetleniyor özel davranış tarafından doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="cb991-104">In this sample, services are validated by the custom behavior by scanning through each endpoint on the service and checking to see whether they contain secure binding elements.</span></span> <span data-ttu-id="cb991-105">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="cb991-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cb991-106">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="cb991-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="endpoint-validation-custom-behavior"></a><span data-ttu-id="cb991-107">Uç nokta doğrulama özel davranışı</span><span class="sxs-lookup"><span data-stu-id="cb991-107">Endpoint Validation Custom Behavior</span></span>  
 <span data-ttu-id="cb991-108">Kullanıcı kodu ekleyerek `Validate` içinde yer alan yöntemi <xref:System.ServiceModel.Description.IServiceBehavior> arabirimi, özel davranışı verilebilir bir hizmet veya uç nokta için kullanıcı tanımlı eylemleri gerçekleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="cb991-108">By adding user code to the `Validate` method contained in the <xref:System.ServiceModel.Description.IServiceBehavior> interface, custom behavior can be given to a service or endpoint to perform user-defined actions.</span></span> <span data-ttu-id="cb991-109">Aşağıdaki kod, bir hizmeti güvenli bağlamaları için kendi bağlama koleksiyonları arar içinde yer alan her bitiş döngü için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cb991-109">The following code is used to loop through each endpoint contained in a service, which searches through their binding collections for secure bindings.</span></span>  
  
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
  
 <span data-ttu-id="cb991-110">Aşağıdaki kodu Web.config dosyasına ekleyerek ekler `serviceValidate` hizmetinin tanımak davranış uzantısı.</span><span class="sxs-lookup"><span data-stu-id="cb991-110">Adding the following code to Web.config file adds the `serviceValidate` behavior extension for the service to recognize.</span></span>  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="endpointValidate" type="Microsoft.ServiceModel.Samples.EndpointValidateElement, endpointValidate, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
    </extensions>  
...  
```  
  
 <span data-ttu-id="cb991-111">Davranış uzantısı hizmete eklendikten sonra artık eklemek mümkündür `endpointValidate` davranışı Web.config dosyasında davranışları listesi ve bu nedenle, hizmet.</span><span class="sxs-lookup"><span data-stu-id="cb991-111">Once the behavior extension is added to the service, it is now possible to add the `endpointValidate` behavior to the list of behaviors in the Web.config file and thus, to the service.</span></span>  
  
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
  
 <span data-ttu-id="cb991-112">Davranışları ve Web.config dosyasına eklendi kendi uzantıları tek tek Hizmetleri için davranış uygulamak Machine.config dosyasının eklendiğinde while her hizmetin bilgisayarda etkin davranış uygulanır.</span><span class="sxs-lookup"><span data-stu-id="cb991-112">Behaviors and their extensions that are added to the Web.config file apply behavior to individual services, while when added to the Machine.config file apply behavior to every service active on the computer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cb991-113">Davranış tüm hizmetlere eklerken, herhangi bir değişiklik yapmadan önce Machine.config dosyasının yedeklemek için önerilir.</span><span class="sxs-lookup"><span data-stu-id="cb991-113">When adding behavior to all services, it is suggested to backup the Machine.config file before making any change.</span></span>  
  
 <span data-ttu-id="cb991-114">Şimdi bu örnek client\bin dizininde sağlanan istemci çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cb991-114">Now run the client provided in the client\bin directory of this sample.</span></span> <span data-ttu-id="cb991-115">Bir özel durum olan aşağıdaki iletiyle oluşur: "İstenen hizmet 'http://localhost/servicemodelsamples/service.svc' etkinleştirilemediğini."</span><span class="sxs-lookup"><span data-stu-id="cb991-115">An exception has occurs with the following message: "The requested service, 'http://localhost/servicemodelsamples/service.svc' could not be activated."</span></span> <span data-ttu-id="cb991-116">Bu bir uç nokta davranışını doğrulama uç noktası tarafından güvenli olduğu kabul edildiği için beklenen ve hizmetin başlatılmasını engeller.</span><span class="sxs-lookup"><span data-stu-id="cb991-116">This is expected because an endpoint is considered insecure by the endpoint validating behavior and prevents the service from being started.</span></span> <span data-ttu-id="cb991-117">Davranış Ayrıca hangi uç noktası güvenli olmayan ve "System.ServiceModel 4.0.0.0" kaynak ve "WebHost" kategorisi altında Sistem Olay Görüntüleyicisi'ni bir ileti yazar açıklayan iç özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cb991-117">The behavior also throws an internal exception that describes which endpoint is insecure and writes a message to the system Event Viewer under the "System.ServiceModel 4.0.0.0" source and the "WebHost" category.</span></span> <span data-ttu-id="cb991-118">Bu örnek hizmetinde izlemeyi etkinleştirmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="cb991-118">It is also possible to turn on tracing on the service in this sample.</span></span> <span data-ttu-id="cb991-119">Kullanıcının hizmet izleme Görüntüleyicisi aracı kullanılarak elde edilen hizmet izlemeleri açarak uç nokta doğrulama davranışı tarafından oluşturulan özel durumları görüntülemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="cb991-119">This allows the user to view the exceptions thrown by endpoint validating behavior by opening the resulting service traces using the Service Trace Viewer tool.</span></span>  
  
#### <a name="to-view-failed-endpoint-validation-exception-messages-in-the-event-viewer"></a><span data-ttu-id="cb991-120">Görüntülemek için uç nokta doğrulama özel durum iletilerinin Olay Görüntüleyicisi'nde başarısız oldu</span><span class="sxs-lookup"><span data-stu-id="cb991-120">To view failed endpoint validation exception messages in the Event Viewer</span></span>  
  
1.  <span data-ttu-id="cb991-121">' I tıklatın **Başlat** menü ve select **Çalıştır...** .</span><span class="sxs-lookup"><span data-stu-id="cb991-121">Click the **Start** menu and select **Run…**.</span></span>  
  
2.  <span data-ttu-id="cb991-122">Tür `eventvwr` tıklatıp **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="cb991-122">Type `eventvwr` and click **OK**.</span></span>  
  
3.  <span data-ttu-id="cb991-123">Olay Görüntüleyicisi'ni penceresinde **uygulama**.</span><span class="sxs-lookup"><span data-stu-id="cb991-123">In the Event Viewer window, click **Application**.</span></span>  
  
4.  <span data-ttu-id="cb991-124">"WebHost" kategorisi altında son eklenen "System.ServiceModel 4.0.0.0" olayı çift **uygulama** güvensiz endpoint iletileri görüntülemek için pencere.</span><span class="sxs-lookup"><span data-stu-id="cb991-124">Double-click the recently added "System.ServiceModel 4.0.0.0" event under the "WebHost" category in the **Application** window to view insecure endpoint messages.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="cb991-125">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="cb991-125">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="cb991-126">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cb991-126">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="cb991-127">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cb991-127">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="cb991-128">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cb991-128">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cb991-129">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="cb991-129">The samples may already be installed on your computer.</span></span> <span data-ttu-id="cb991-130">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="cb991-130">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="cb991-131">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="cb991-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cb991-132">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="cb991-132">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ServiceValidation`  
  
## <a name="see-also"></a><span data-ttu-id="cb991-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cb991-133">See Also</span></span>  
 [<span data-ttu-id="cb991-134">AppFabric izleme örnekleri</span><span class="sxs-lookup"><span data-stu-id="cb991-134">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
