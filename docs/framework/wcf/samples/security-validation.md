---
title: Güvenlik Doğrulaması
ms.date: 03/30/2017
ms.assetid: 48dcd496-0c4f-48ce-8b9b-0e25b77ffa58
ms.openlocfilehash: 17e6e250c6b345477f7c9b377eb8e16ff4331ca7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183376"
---
# <a name="security-validation"></a><span data-ttu-id="b3d8f-102">Güvenlik Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="b3d8f-102">Security Validation</span></span>
<span data-ttu-id="b3d8f-103">Bu örnek, belirli ölçütleri karşıladıklarından emin olmak için bilgisayardaki hizmetleri doğrulamak için özel bir davranışın nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b3d8f-103">This sample demonstrates how to use a custom behavior to validate services on a computer to ensure they meet specific criteria.</span></span> <span data-ttu-id="b3d8f-104">Bu örnekte, hizmetler, hizmetteki her bitiş noktası üzerinden taranarak ve güvenli bağlama öğeleri içerip içermediklerini denetleyerek özel davranış tarafından doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="b3d8f-104">In this sample, services are validated by the custom behavior by scanning through each endpoint on the service and checking to see whether they contain secure binding elements.</span></span> <span data-ttu-id="b3d8f-105">Bu örnek [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b3d8f-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b3d8f-106">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="b3d8f-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="endpoint-validation-custom-behavior"></a><span data-ttu-id="b3d8f-107">Uç Nokta Doğrulama Özel Davranış</span><span class="sxs-lookup"><span data-stu-id="b3d8f-107">Endpoint Validation Custom Behavior</span></span>  
 <span data-ttu-id="b3d8f-108">Arabirimde bulunan `Validate` yönteme kullanıcı kodu eklenerek, kullanıcı tanımlı eylemleri gerçekleştirmek için bir hizmete veya bitiş noktasına özel davranış verilebilir. <xref:System.ServiceModel.Description.IServiceBehavior></span><span class="sxs-lookup"><span data-stu-id="b3d8f-108">By adding user code to the `Validate` method contained in the <xref:System.ServiceModel.Description.IServiceBehavior> interface, custom behavior can be given to a service or endpoint to perform user-defined actions.</span></span> <span data-ttu-id="b3d8f-109">Aşağıdaki kod, güvenli bağlamalar için bağlama koleksiyonları nda arama yapan bir hizmette bulunan her uç noktayı döngüye almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b3d8f-109">The following code is used to loop through each endpoint contained in a service, which searches through their binding collections for secure bindings.</span></span>  
  
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
  
 <span data-ttu-id="b3d8f-110">Web.config dosyasına aşağıdaki kodu `serviceValidate` eklemek, hizmetin tanıyacak davranış uzantısını ekler.</span><span class="sxs-lookup"><span data-stu-id="b3d8f-110">Adding the following code to Web.config file adds the `serviceValidate` behavior extension for the service to recognize.</span></span>  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="endpointValidate" type="Microsoft.ServiceModel.Samples.EndpointValidateElement, endpointValidate, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
    </extensions>  
...  
```  
  
 <span data-ttu-id="b3d8f-111">Davranış uzantısı hizmete eklendikten sonra, `endpointValidate` davranışı Web.config dosyasındaki davranışlar listesine ve böylece hizmete eklemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="b3d8f-111">Once the behavior extension is added to the service, it is now possible to add the `endpointValidate` behavior to the list of behaviors in the Web.config file and thus, to the service.</span></span>  
  
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
  
 <span data-ttu-id="b3d8f-112">Web.config dosyasına eklenen davranışlar ve uzantıları, machine.config dosyasına eklendiğinde bilgisayarda etkin olan her hizmete davranış uygularken, davranışı tek tek hizmetlere uygular.</span><span class="sxs-lookup"><span data-stu-id="b3d8f-112">Behaviors and their extensions that are added to the Web.config file apply behavior to individual services, while when added to the Machine.config file apply behavior to every service active on the computer.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b3d8f-113">Tüm hizmetlere davranış eklerken, herhangi bir değişiklik yapmadan önce Machine.config dosyasını yedeklemek önerilir.</span><span class="sxs-lookup"><span data-stu-id="b3d8f-113">When adding behavior to all services, it is suggested to backup the Machine.config file before making any change.</span></span>  
  
 <span data-ttu-id="b3d8f-114">Şimdi bu örnek istemci\bin dizini sağlanan istemci çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b3d8f-114">Now run the client provided in the client\bin directory of this sample.</span></span> <span data-ttu-id="b3d8f-115">Aşağıdaki iletide bir özel durum oluşur: "İstenen hizmet'http://localhost/servicemodelsamples/service.svcetkinleştirilemedi."</span><span class="sxs-lookup"><span data-stu-id="b3d8f-115">An exception has occurs with the following message: "The requested service, 'http://localhost/servicemodelsamples/service.svc' could not be activated."</span></span> <span data-ttu-id="b3d8f-116">Uç nokta doğrulama davranışı tarafından güvenli olarak kabul edilir ve hizmetin başlatılmasını engeller, çünkü bu bekleniyor.</span><span class="sxs-lookup"><span data-stu-id="b3d8f-116">This is expected because an endpoint is considered insecure by the endpoint validating behavior and prevents the service from being started.</span></span> <span data-ttu-id="b3d8f-117">Davranış ayrıca hangi uç noktanın güvenli olmadığını açıklayan bir iç özel durum oluşturur ve "System.ServiceModel 4.0.0.0" kaynağı ve "WebHost" kategorisi altında sistem Olay Görüntüleyicisi'ne bir ileti yazar.</span><span class="sxs-lookup"><span data-stu-id="b3d8f-117">The behavior also throws an internal exception that describes which endpoint is insecure and writes a message to the system Event Viewer under the "System.ServiceModel 4.0.0.0" source and the "WebHost" category.</span></span> <span data-ttu-id="b3d8f-118">Bu örnekteki hizmeti takip etmeyi de açmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="b3d8f-118">It is also possible to turn on tracing on the service in this sample.</span></span> <span data-ttu-id="b3d8f-119">Bu, kullanıcının, Service Trace Viewer aracını kullanarak ortaya çıkan hizmet izleme lerini açarak uç nokta doğrulama davranışıyla atılan özel durumları görüntülemesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b3d8f-119">This allows the user to view the exceptions thrown by endpoint validating behavior by opening the resulting service traces using the Service Trace Viewer tool.</span></span>  
  
#### <a name="to-view-failed-endpoint-validation-exception-messages-in-the-event-viewer"></a><span data-ttu-id="b3d8f-120">Olay Görüntüleyici'nde başarısız uç nokta doğrulama özel durum iletilerini görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="b3d8f-120">To view failed endpoint validation exception messages in the Event Viewer</span></span>  
  
1. <span data-ttu-id="b3d8f-121">**Başlat** menüsüne tıklayın ve **Çalıştır'ı seçin... seçeneğini belirleyin.**</span><span class="sxs-lookup"><span data-stu-id="b3d8f-121">Click the **Start** menu and select **Run…**.</span></span>  
  
2. <span data-ttu-id="b3d8f-122">Yaz `eventvwr` ve **Tamam'ı**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="b3d8f-122">Type `eventvwr` and click **OK**.</span></span>  
  
3. <span data-ttu-id="b3d8f-123">Olay Görüntüleyicisi penceresinde **Uygulama'yı**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="b3d8f-123">In the Event Viewer window, click **Application**.</span></span>  
  
4. <span data-ttu-id="b3d8f-124">Güvenli olmayan uç nokta iletilerini görüntülemek için **Uygulama** penceresinde "WebHost" kategorisi altında yeni eklenen "System.ServiceModel 4.0.0.0" etkinliğini çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="b3d8f-124">Double-click the recently added "System.ServiceModel 4.0.0.0" event under the "WebHost" category in the **Application** window to view insecure endpoint messages.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b3d8f-125">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="b3d8f-125">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b3d8f-126">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="b3d8f-126">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="b3d8f-127">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="b3d8f-127">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="b3d8f-128">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="b3d8f-128">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b3d8f-129">Örnekler bilgisayarınıza zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="b3d8f-129">The samples may already be installed on your computer.</span></span> <span data-ttu-id="b3d8f-130">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b3d8f-130">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="b3d8f-131">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="b3d8f-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b3d8f-132">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="b3d8f-132">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ServiceValidation`  
  
## <a name="see-also"></a><span data-ttu-id="b3d8f-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3d8f-133">See also</span></span>

- <span data-ttu-id="b3d8f-134">[AppFabric İzleme Örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="b3d8f-134">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
